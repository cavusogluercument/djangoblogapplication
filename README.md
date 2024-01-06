# djangoblogapplication

EN

This Django blog application provides a basic infrastructure for creating a blog website. Such an application allows users to add, edit, and publish blog posts, which can be viewed by other users or visitors.

Adding and Displaying Blog Posts:

Users can add blog posts with titles, content, and date information. The added posts can later be viewed by users or visitors.

Categorizing Posts:

Categorizing blog posts can help better organize content. For example, there can be blog posts categorized into topics such as technology, sports, fashion, etc.

Monitoring and Managing Comments:

Users or visitors can add comments to blog posts. These comments are usually subject to moderation and management by a moderator.

User Authorization and Security:

Users typically need a user account to add, edit, or delete their own posts. This requires the implementation of user authorization and security measures.

Management with Admin Panel:

Using Django's provided admin panel, it's possible to manage, add, edit, and delete blog posts. This allows the site administrator to have control over the content.

SEO-Friendly URLs:

Providing unique, descriptive, and SEO-friendly URLs for blog posts is important for better rankings on search engines.

RSS Feeds:

Creating RSS feeds from blog posts allows readers to follow updates on your site.

Responsive Design:

A responsive design can be implemented to ensure users can comfortably view the blog on different devices such as computers, tablets, and phones.

These features form the fundamental purposes of a Django blog application. By facilitating the addition, editing, and publishing of content, the application serves as a powerful tool for blog authors and site administrators.

Database Table Designs:

Category Table

name
Blog Table

title (must be unique)
content
image
category (relationship with Category Table - ForeignKey, OneToOne, or ManyToMany)
publish_date
user (relationship with User Table - ForeignKey, OneToOne, or ManyToMany)
status (using choices, e.g., ('d', 'Draft'), ('p', 'Published'))
Comment Table

user (relationship with User Table - ForeignKey, OneToOne, or ManyToMany)
time_stamp
content
blog (relationship with Blog Table - ForeignKey, OneToOne, or ManyToMany)
Likes Table

user (relationship with User Table - ForeignKey, OneToOne, or ManyToMany)
blog (relationship with Blog Table - ForeignKey, OneToOne, or ManyToMany)
likes
PostViews Table

user (relationship with User Table - ForeignKey, OneToOne, or ManyToMany)
post_views
blog (relationship with Blog Table - ForeignKey, OneToOne, or ManyToMany)
time_stamp
Additional Requirements:

Write a method to calculate the total number of comments made.
Calculate the total number of likes.
Calculate the view count of blogs.
User ID in tables with a user field should be automatically obtained from the token information.
Only the get operation should be allowed for category operations for every user. The put, post, and delete operations should be restricted to staff users only.
For blogs, every user can perform the get operation, but only the blog owner and staff users can perform update and delete operations.
If a user is a staff member, they should be able to view and edit their blogs even if the status is 'd'; other users can only view those with status 'p'.
If the user is a staff member, use BlogSerializer; otherwise, use UserBlogSerializer. Therefore, two serializers should be created for blogs, and regular users will not see the status field.
When entering the details page of a blog, create a post view.
Every user can edit their own comments and view comments made by others.





TR

Bu Django blog uygulaması, bir blog sitesi oluşturmak için temel bir altyapı sağlar. Bu tür bir uygulama, kullanıcıların blog yazıları eklemelerine, bu yazıları düzenlemelerine ve yayınlamalarına izin verir. 

Blog Yazıları Eklemek ve Göstermek:

Kullanıcılar, başlık, içerik ve tarih bilgileriyle birlikte blog yazıları ekleyebilir. Eklenen yazılar daha sonra kullanıcılar veya ziyaretçiler tarafından görüntülenebilir.

Yazıları Kategorize Etmek:

Blog yazılarını kategorilere ayırmak, içerikleri daha iyi organize etmeye yardımcı olabilir. Örneğin, teknoloji, spor, moda gibi kategorilere ayrılmış blog yazıları olabilir.

Yorumları İzlemek ve Yönetmek:

Kullanıcılar veya ziyaretçiler, blog yazılarına yorum ekleyebilir. Bu yorumlar genellikle moderatör tarafından kontrol edilebilir ve yönetilebilir.

Kullanıcı Yetkilendirmesi ve Güvenlik:

Kullanıcılar genellikle kendi yazılarını ekleyebilmek, düzenleyebilmek veya silebilmek için bir kullanıcı hesabına sahip olmalıdır. Bu, kullanıcı yetkilendirmesi ve güvenlik önlemlerinin uygulanmasını gerektirir.

Admin Paneli İle Yönetim:

Django'nun sağladığı admin paneli üzerinden blog yazılarını yönetmek, eklemek, düzenlemek ve silmek mümkündür. Bu, site yöneticisinin içerik üzerinde kontrol sahibi olmasını sağlar.

SEO Dostu URL'ler:

Blog yazılarına benzersiz, açıklayıcı ve SEO dostu URL'ler sağlamak, arama motorlarında daha iyi sıralama almak için önemlidir.

RSS Beslemeleri:

Blog yazılarından oluşturulan RSS beslemeleri, okuyucuların sitenizdeki güncellemeleri takip etmelerini sağlar.

Responsive Tasarım:

Kullanıcıların farklı cihazlarda (bilgisayarlar, tabletler, telefonlar) blogu rahatça görüntüleyebilmeleri için responsive bir tasarım sağlanabilir.

Bu gibi özellikler, bir Django blog uygulamasının temel amaçlarını oluşturur. Uygulama, kullanıcıların içerik eklemesini, düzenlemesini ve yayınlamasını kolaylaştırarak blog yazarlarına ve site yöneticilerine güçlü bir araç sunar.

1- Category Table
name

2- Blog Table
title: her title farklı olmak zorunda

content

image

category : Category Tablosu ile uygun olan ilişki kurulmalıdır. ForeigneKey - OneToOne veya ManyToMany

publish_date

user : User Tablosu  ile uygun olan ilişki kurulmalıdır. ForeigneKey - OneToOne veya ManyToMany

status : choices kullanmanızı istiyorum ('d', 'Draft'), ('p', 'Published') şeklinde oluşturabilirsiniz.

3- Comment Table

user:

User Tablosu  ile uygun olan ilişki kurulmalıdır. ForeigneKey - OneToOne veya ManyToMany
time_stamp

content

blog : Blog Tablosu  ile uygun olan ilişki kurulmalıdır. ForeigneKey - OneToOne veya ManyToMany

4- Likes Table

user: User Tablosu  ile uygun olan ilişki kurulmalıdır. ForeigneKey - OneToOne veya ManyToMany

blog: Blog Tablosu  ile uygun olan ilişki kurulmalıdır. ForeigneKey - OneToOne veya ManyToMany
likes

5- PostViews Table
user: User Tablosu  ile uygun olan ilişki kurulmalıdır. ForeigneKey - OneToOne veya ManyToMany
post_views

blog: Blog Tablosu  ile uygun olan ilişki kurulmalıdır. ForeigneKey - OneToOne veya ManyToMany
time_stamp

6- Toplam kaç yorum yapıldığını hesaplayan bir method yazılmalı

7- Toplam kaç tane like atıldığını hesaplayın

8- Blogların görüntüleme sayısını hesaplayın

9- User field olan tablolarda user id otomatik olarak token bilgisinden alınmalıdır

10- category işlemlerinde sadece get işlemini her kullanıcı yapabilir, put post delete işlemlerini sadece staff user yapabilir:

11- Bloglarda get işlemini her kullanıcı yapabilecek update ve delete işlemlerini yalnızca blog sahibi ve staff user yapabilecek:

12-  Kullanıcı eğer blog sahibi ya da staff ise bloglarının status'u 'd' olsa bile görüntüleyip düzenleyebilecek: diğer kullanıcılar sadece status ‘p’ olanları görüntüleyebilecek

13- Kullanı staff ise BlogSerializer kullansın değil ise UserBlogSerializer'ı kullansın: bu sebeple Blog için 2 tane serializer oluşturulmalı normal kullanıcılar status field’ını görmeyecek.

14- Blog sayfasının detayına girdiğimizde post_view create edilecek

15- Her kullanıcı kendi yorumunu düzenleyebilecek herkesin yorumunu görüntüleyebilecek



