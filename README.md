# 🚗 CarBook - .NET 8 Onion Architecture Projesi

![.NET](https://img.shields.io/badge/.NET-8.0-512BD4?style=for-the-badge&logo=dotnet)
![SQL Server](https://img.shields.io/badge/SQL%20Server-CC2927?style=for-the-badge&logo=microsoftsqlserver&logoColor=white)
![JWT](https://img.shields.io/badge/JWT-000000?style=for-the-badge&logo=jsonwebtokens)
![SignalR](https://img.shields.io/badge/SignalR-512BD4?style=for-the-badge&logo=dotnet)
![Swagger](https://img.shields.io/badge/Swagger-85EA2D?style=for-the-badge&logo=swagger&logoColor=black)
![MediatR](https://img.shields.io/badge/MediatR-512BD4?style=for-the-badge)

---

## 📌 Proje Hakkında

CarBook, **ASP.NET Core (.NET 8)** kullanılarak geliştirilmiş modern bir araç kiralama web uygulamasıdır. Proje, sürdürülebilir ve ölçeklenebilir bir yazılım mimarisi oluşturmak amacıyla **Onion Architecture (Soğan Mimarisi)** prensipleri ile tasarlanmıştır. Onion Architecture, uygulamanın iş kurallarını merkezde tutan ve dış katmanların bu çekirdeğe bağımlı olduğu bir yaklaşım sunar. Bu sayede proje **modüler, test edilebilir ve sürdürülebilir** bir yapıya sahip olur.

---

## 🏗️ Mimari Yapı

### 🔵 Core — UdemyCarBook.Application
Application katmanı projenin iş mantığını barındırır. Bu katmanda **DTOs** (TokenResponseDto), **Enums** (RolesType), **Features** klasörü altında CQRS, Mediator ve Repository Pattern yapıları, **Interfaces**, **Services** (ServiceRegistiration), **Tools** (JwtTokenDefaults, JwtTokenGenerator), **Validators** (ReviewValidators) ve **ViewModels** bulunmaktadır.

### 🔵 Core — UdemyCarBook.Domain
Domain katmanı uygulamanın en iç çekirdeğidir. Temel **Entity** sınıfları bu katmanda tanımlanmıştır. **FluentValidation.AspNetCore** paketi ile entity doğrulama kuralları bu katmanda da desteklenmektedir.

### 🟢 Frontends — UdemyCarBook.WebUI
WebUI katmanı kullanıcı arayüzünü oluşturur. **Areas/Admin** ile admin paneli, **Controllers**, **Models**, **ViewComponents**, **Views** ve **wwwroot** klasörlerinden oluşmaktadır. JWT Bearer Authentication bu katmanda da aktif olarak kullanılmaktadır.

### 🟡 Infrastructure — UdemyCarBook.Persistance
Persistence katmanında **CarBookContext** ile veritabanı bağlantısı sağlanmıştır. Repository klasörü altında AppUser, Blog, CarDescription, CarFeature, CarPricing, Car, Comment, RentACar, Review, Statistics ve TagCloud için ayrı repository implementasyonları mevcuttur.

### 🔴 Presentation — UdemyCarBook.WebApi
WebApi katmanında **Controllers**, **Hubs** (CarHub - SignalR) ve gerekli konfigürasyonlar yer almaktadır. API dokümantasyonu **Swashbuckle (Swagger)** ile sağlanmıştır.

---

## 🔐 JWT & Rol Yönetimi

Kimlik doğrulama **JWT Authentication** ile sağlanmıştır. **JwtTokenDefaults** ile token parametreleri merkezi olarak yönetilir, **JwtTokenGenerator** ile her oturum için güvenli token üretilir. **RolesType** enum'u sayesinde kullanıcı rolleri tip güvenli bir şekilde tanımlanmıştır.

---

## 📡 SignalR — CarHub

**CarHub**, SignalR altyapısı kullanılarak gerçek zamanlı veri akışı sağlamak amacıyla geliştirilmiştir. Anlık istatistik ve araç verilerinin sayfayı yenilemeden canlı olarak güncellenmesi bu yapı sayesinde mümkün olmaktadır.

---

## 🛡️ Admin Paneli — Areas/Admin

Admin paneli **Areas** yapısı kullanılarak ana uygulamadan izole edilmiştir. Araç, blog, kullanıcı ve istatistik yönetimi gibi tüm yönetimsel işlemler bu panel üzerinden gerçekleştirilmektedir.

---

## 🧩 ViewComponents

Sayfalar arası tekrar eden UI blokları **ViewComponents** yapısı ile bağımsız ve yeniden kullanılabilir bileşenler olarak geliştirilmiştir.

---

## ⚙️ Kullanılan Teknolojiler

- .NET 8
- ASP.NET Core MVC & Web API
- SQL Server
- Entity Framework Core
- Onion Architecture
- CQRS Pattern
- Mediator Pattern (MediatR)
- Repository Pattern
- JWT Authentication
- SignalR (CarHub)
- FluentValidation
- Swagger (Swashbuckle)
- Postman

---

## 🎯 Proje Amacı

- Katmanlı ve sürdürülebilir bir mimari oluşturmak
- Bağımlılıkları azaltarak modüler bir sistem geliştirmek
- Test edilebilir ve ölçeklenebilir bir web uygulaması oluşturmak
- Gerçek zamanlı iletişim (SignalR) ve güvenli kimlik doğrulama (JWT) altyapısı kurmak

