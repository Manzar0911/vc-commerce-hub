# 🛍️ VC Commerce Hub

[![.NET 8](https://img.shields.io/badge/.NET-8.0-512BD4?logo=dotnet&logoColor=white)](https://dotnet.microsoft.com/)
[![C#](https://img.shields.io/badge/C%23-12.0-239120?logo=csharp&logoColor=white)](https://docs.microsoft.com/en-us/dotnet/csharp/)
[![ASP.NET Core](https://img.shields.io/badge/ASP.NET%20Core-8.0-blue?logo=dotnet)](https://dotnet.microsoft.com/apps/aspnet)
[![Architecture](https://img.shields.io/badge/Architecture-Headless%20%7C%20Modular-orange)](#system-architecture)
[![License](https://img.shields.io/badge/License-Virto%20Commerce%20OSL-green.svg)](LICENSE)

**VC Commerce Hub** is a modular enterprise e-commerce storefront engine built with **ASP.NET 8** and **.NET Core**. Designed for high-performance B2B and B2C commerce, it functions as a decoupled, headless storefront that communicates seamlessly with commerce backend services via robust GraphQL and REST APIs.

---

## 🌟 Key Highlights

- **Multi-Store & Multi-Tenant**: Host multiple storefronts with customized layouts and regional catalogs from a single codebase.
- **Dynamic Liquid Theme Engine**: Flexible Scriban & Liquid-based template rendering supporting custom layouts, snippets, and Sass/SCSS runtime compilation.
- **Headless API Integration**: Unified communication with commerce platforms using both GraphQL and RESTful endpoints.
- **High-Performance Caching**: Layered caching system featuring in-memory cache and distributed **Redis** support with auto-invalidation.
- **Omnichannel & Extensible**: Seamless customer experience across web, mobile, and third-party touchpoints.
- **Enterprise Security**: Built-in authentication supporting OAuth2, OpenID Connect (OIDC), Google, Facebook, GitHub, and ASP.NET Identity Core.
- **Resilient Operations**: Integrated with **Polly** for retry policies, circuit breakers, and fault-tolerant network operations.

---

## 🏗️ System Architecture

The solution is divided into modular, decoupled layers:

```
vc-commerce-hub/
├── VirtoCommerce.Storefront/         # Main ASP.NET 8 Web App (Routing, Controllers, Middleware, Auth)
├── VirtoCommerce.LiquidThemeEngine/  # Templating Engine (Liquid/Scriban renderer, SCSS compiler)
├── VirtoCommerce.Storefront.Model/   # Core Domain Models, DTOs, Catalog, Cart & Order abstractions
└── VirtoCommerce.Storefront.Tests/   # Unit, Functional & Integration Test Suite
```

---

## 🛠️ Technology Stack

| Layer | Technologies |
|---|---|
| **Framework** | .NET 8.0, ASP.NET Core MVC |
| **Language** | C# 12 |
| **Templating** | Liquid, Scriban Engine, LibSassHost (SCSS) |
| **APIs & Protocols** | GraphQL (GraphQL.Client), RESTful APIs, Swagger/OpenAPI |
| **Caching & Messaging** | StackExchange.Redis, MemoryCache, Polly Resilience Engine |
| **Identity & Security** | ASP.NET Identity Core, IdentityModel, OAuth (GitHub, Google, Facebook) |
| **Validation & Utilities** | FluentValidation, Markdig (Markdown), Newtonsoft.Json |
| **Deployment** | Docker, Azure App Service (ARM Template Included) |

---

## 🚀 Getting Started

### Prerequisites
- [.NET 8.0 SDK](https://dotnet.microsoft.com/download/dotnet/8.0) or higher
- [Visual Studio 2022](https://visualstudio.microsoft.com/) / [VS Code](https://code.visualstudio.com/) / [Rider](https://www.jetbrains.com/rider/)
- Redis *(optional, for distributed caching)*

### Installation & Local Setup

1. **Clone the repository:**
   ```bash
   git clone https://github.com/Manzar0911/vc-commerce-hub.git
   cd vc-commerce-hub
   ```

2. **Restore dependencies:**
   ```bash
   dotnet restore
   ```

3. **Configure Environment:**
   Update your endpoint credentials in `VirtoCommerce.Storefront/appsettings.json` or `appsettings.Development.json`:
   ```json
   {
     "VirtoCommerce": {
       "Endpoint": {
         "Url": "https://your-commerce-backend-url.com",
         "ApiSecret": "YOUR_API_SECRET"
       }
     }
   }
   ```

4. **Build the Solution:**
   ```bash
   dotnet build
   ```

5. **Run the Storefront:**
   ```bash
   cd VirtoCommerce.Storefront
   dotnet run --urls=https://localhost:5001
   ```
   Open `https://localhost:5001` in your browser.

---

## 🧪 Running Tests

To run the automated test suite across all test projects:

```bash
dotnet test --logger "console;verbosity=detailed"
```

---

## ⚙️ Configuration & Deployment

### HTTPS Certificate Trust
Trust the local .NET development certificate before launching:
```bash
dotnet dev-certs https --trust
```

### Azure Deployment
The repository includes an Azure Resource Manager template (`azuredeploy.json`) for automated one-click provisioning to Azure App Service.

[![Deploy to Azure](https://aka.ms/deploytoazurebutton)](https://portal.azure.com/#create/Microsoft.Template/uri/https%3A%2F%2Fraw.githubusercontent.com%2FManzar0911%2Fvc-commerce-hub%2Fmain%2Fazuredeploy.json)

---

## 👤 Author & Maintainer

* **Manzar** - [@Manzar0911](https://github.com/Manzar0911)

---

## 📄 License

This project is licensed under the [Virto Commerce Open Software License](LICENSE). Based on Virto Commerce Storefront architecture.
