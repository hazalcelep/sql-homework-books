[library_books.sql](https://github.com/user-attachments/files/22316108/library_books.sql)
create table dbo.books (
book_id int identity (1,1) primary key,
tittle nvarchar(200) not null,
author nvarchar(150) not null,
genre nvarchar(50),
price decimal(5,2) CHECK (price >= 0),
stock int CHECK (stock >= 0),
published_year int CHECK (published_year BETWEEN 1900 AND 2025),
added_at date NOT NULL DEFAULT GETDATE())

insert into books ([tittle], [author], [genre], [price], [stock], [published_year], [added_at] ) 
values (N'Kay�p Zaman�n �zinde',N'M. Proust',N'roman',129.90,25,1913,'2025-08-20'),
(N'Simyac�',N'P. Coelho',N'roman',89.50,40,1988,'2025-08-21'),
(N'Sapiens',N'Y. N. Harari',N'Tarih',159.00,18,2011,'2025-08-25'),
(N'�nce Memed',N'Y. Kemal',N'roman',99.90,12,1955,'2025-08-22'),
(N'K�rl�k',N'J. Saramago',N'roman',119.00,7,1995,'2025-08-28'),
(N'Dune',N'F. Herbert',N'bilim',149.00,30,1965,'2025-09-01'),
(N'Hayvan �iftli�i', N'G. Orwell', N'roman', 79.90, 55, 1945, '2025-08-23'),
(N'1984', N'G. Orwell', N'roman', 99.00, 35, 1949, '2025-08-24'),
(N'Nutuk', N'M. K. Atat�rk', N'tarih', 139.00, 20, 1927, '2025-08-27'),
(N'K���k Prens', N'A. de Saint-Exup�ry', N'�ocuk', 69.90, 80, 1943, '2025-08-26'),
(N'Ba�lang��', N'D. Brown', N'roman', 109.00, 22, 2017, '2025-09-02'),
(N'Atomik Al��kanl�klar', N'J. Clear', N'ki�isel geli�im', 129.00, 28, 2018, '2025-09-03'),
(N'Zaman�n K�sa Tarihi', N'S. Hawking', N'bilim', 119.50, 16, 1988, '2025-08-29'),
(N'�eker Portakal�', N'J. M. de Vasconcelos', N'roman', 84.90, 45, 1968, '2025-08-30'),
(N'Bir �dam Mahk�munun Son G�n�', N'V. Hugo', N'roman', 74.90, 26, 1900, '2025-08-31');

select tittle as [Kitap Ad�],author as Yazari,price as fiyat
FROM books
order by price ASC;

select tittle as [Kitap Ad�], genre as T�r
from books
where genre=N'roman'
order by tittle ASC;

select tittle as [Kitap Ad�], price as Fiyat�
from books
where price between 80 and 120 

select tittle as [Kitap Ad�], stock as Adeti
from books
where stock <20

select tittle as [Kitap Ad�]
from books
where tittle like  N'%zaman%';

select tittle as [Kitap Ad�], genre [t�r�]
from books 
where genre IN (N'Roman' ,N'Bilim') 

select tittle as [Kitap Ad�], published_year as [Yay�nland��� Y�l]
from books 
where published_year>=2000
ORDER BY published_year DESC;

select tittle as [Kitap Ad�], added_at as [Eklendi�i Tarih]
from books
WHERE added_at >=DATEADD(DAY, -10, CAST(GETDATE() AS DATE))
ORDER BY added_at DESC;

SELECT TOP 5 tittle AS [Kitap Ad�], price AS [Fiyat]
FROM books
ORDER BY price DESC;

select tittle as [Kitap Ad�], stock [Adeti],price [fiyat�]
from books
where stock between 30 and 60
ORDER BY price ASC;
