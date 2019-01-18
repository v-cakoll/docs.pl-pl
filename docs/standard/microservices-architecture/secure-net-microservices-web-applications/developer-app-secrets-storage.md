---
title: Bezpieczne przechowywanie wpisów tajnych aplikacji podczas programowania
description: Zabezpieczenia w Mikrousługach .NET i aplikacji sieci Web - odradzamy przechowywanie wpisów tajnych aplikacji, takie jak hasła, parametry połączenia lub klucze interfejsu API w kontroli źródła, informacje o opcjach, używane w programie ASP.NET Core, w szczególności należy zrozumieć, jak obsługiwać " wpisy tajne".
author: mjrousos
ms.author: wiwagn
ms.date: 10/19/2018
ms.openlocfilehash: fe8e7fa11c9a4f4cae133c2e09f9e4b4dd40a546
ms.sourcegitcommit: 542aa405b295955eb055765f33723cb8b588d0d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2019
ms.locfileid: "54361992"
---
# <a name="store-application-secrets-safely-during-development"></a><span data-ttu-id="406cb-103">Bezpiecznie Store wpisów tajnych aplikacji podczas programowania</span><span class="sxs-lookup"><span data-stu-id="406cb-103">Store application secrets safely during development</span></span>

<span data-ttu-id="406cb-104">Aby połączyć się z chronionych zasobów i inne usługi, aplikacje platformy ASP.NET Core zazwyczaj należy użyć parametrów połączenia, hasła lub inne poświadczenia, które zawierają poufne informacje.</span><span class="sxs-lookup"><span data-stu-id="406cb-104">To connect with protected resources and other services, ASP.NET Core applications typically need to use connection strings, passwords, or other credentials that contain sensitive information.</span></span> <span data-ttu-id="406cb-105">Te elementy poufnych informacji są nazywane *wpisów tajnych*.</span><span class="sxs-lookup"><span data-stu-id="406cb-105">These sensitive pieces of information are called *secrets*.</span></span> <span data-ttu-id="406cb-106">Jest najlepszym rozwiązaniem, aby nie zawierać wpisy tajne w kodzie źródłowym i upewniając się, nie będą przechowywane klucze tajne w kontroli źródła.</span><span class="sxs-lookup"><span data-stu-id="406cb-106">It's a best practice to not include secrets in source code and making sure not to store secrets in source control.</span></span> <span data-ttu-id="406cb-107">Zamiast tego należy użyć modelu konfiguracji platformy ASP.NET Core na odczyt kluczy tajnych z bardziej bezpiecznych lokalizacjach.</span><span class="sxs-lookup"><span data-stu-id="406cb-107">Instead, you should use the ASP.NET Core configuration model to read the secrets from more secure locations.</span></span>

<span data-ttu-id="406cb-108">Muszą być rozdzielone wpisów tajnych dla uzyskiwanie dostępu do programowania i przemieszczania zasobów z nich używane do uzyskiwania dostępu do zasobów w środowisku produkcyjnym, ponieważ inne osoby będą potrzebowali dostępu do tych różnych zestawów wpisów tajnych.</span><span class="sxs-lookup"><span data-stu-id="406cb-108">You must separate the secrets for accessing development and staging resources from the ones used for accessing production resources, because different individuals will need access to those different sets of secrets.</span></span> <span data-ttu-id="406cb-109">Do przechowywania wpisów tajnych używanych podczas tworzenia, wspólnego podejścia są przechowywanie wpisów tajnych w zmiennych środowiskowych lub za pomocą narzędzia ASP.NET Core klucz tajny menedżera.</span><span class="sxs-lookup"><span data-stu-id="406cb-109">To store secrets used during development, common approaches are to either store secrets in environment variables or by using the ASP.NET Core Secret Manager tool.</span></span> <span data-ttu-id="406cb-110">Dla bardziej bezpieczne przechowywanie w środowiskach produkcyjnych mikrousługi można przechowywać wpisy tajne w usłudze Azure Key Vault.</span><span class="sxs-lookup"><span data-stu-id="406cb-110">For more secure storage in production environments, microservices can store secrets in an Azure Key Vault.</span></span>

## <a name="store-secrets-in-environment-variables"></a><span data-ttu-id="406cb-111">Store wpisów tajnych w zmiennych środowiskowych</span><span class="sxs-lookup"><span data-stu-id="406cb-111">Store secrets in environment variables</span></span>

<span data-ttu-id="406cb-112">Jest jednym ze sposobów odróżnienia wpisy tajne z kodu źródłowego, deweloperzy mogą ustawić oparte na ciągach wpisów tajnych jako [zmienne środowiskowe](/aspnet/core/security/app-secrets#environment-variables) na swoich komputerach deweloperskich.</span><span class="sxs-lookup"><span data-stu-id="406cb-112">One way to keep secrets out of source code is for developers to set string-based secrets as [environment variables](/aspnet/core/security/app-secrets#environment-variables) on their development machines.</span></span> <span data-ttu-id="406cb-113">Gdy zmienne środowiskowe są używane do przechowywania wpisów tajnych za pomocą nazw hierarchicznych, takich jak te zagnieżdżonego w sekcji konfiguracji nazwę zmienne, aby uwzględnić hierarchię pełną sekcjach rozdzielonych z dwukropkiem (:).</span><span class="sxs-lookup"><span data-stu-id="406cb-113">When you use environment variables to store secrets with hierarchical names, such as the ones nested in configuration sections, you must name the variables to include the complete hierarchy of its sections, delimited with colons (:).</span></span>

<span data-ttu-id="406cb-114">Na przykład ustawienie zmiennej środowiskowej `Logging:LogLevel:Default` do `Debug` wartość byłaby równoważna wartości konfiguracji z następującego pliku JSON:</span><span class="sxs-lookup"><span data-stu-id="406cb-114">For example, setting an environment variable `Logging:LogLevel:Default` to `Debug` value would be equivalent to a configuration value from the following JSON file:</span></span>

```json
{
    "Logging": {
        "LogLevel": {
            "Default": "Debug"
        }
    }
}
```

<span data-ttu-id="406cb-115">Dostępu do tych wartości w zmiennych środowiskowych, aplikacja musi jedynie może wywołać jej ConfigurationBuilder AddEnvironmentVariables przy konstruowaniu obiektu IConfigurationRoot.</span><span class="sxs-lookup"><span data-stu-id="406cb-115">To access these values from environment variables, the application just needs to call AddEnvironmentVariables on its ConfigurationBuilder when constructing an IConfigurationRoot object.</span></span>

<span data-ttu-id="406cb-116">Należy pamiętać, że zmienne środowiskowe są często przechowywane jako zwykły tekst, więc w przypadku naruszenia zabezpieczeń komputera lub proces, za pomocą zmiennych środowiskowych, wartości zmiennych środowiskowych będą widoczne.</span><span class="sxs-lookup"><span data-stu-id="406cb-116">Note that environment variables are commonly stored as plain text, so if the machine or process with the environment variables is compromised, the environment variable values will be visible.</span></span>

## <a name="store-secrets-with-the-aspnet-core-secret-manager"></a><span data-ttu-id="406cb-117">Wpisy tajne Store Menedżera wpisu tajnego za pomocą platformy ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="406cb-117">Store secrets with the ASP.NET Core Secret Manager</span></span>

<span data-ttu-id="406cb-118">ASP.NET Core [Menedżera klucz tajny](/aspnet/core/security/app-secrets#secret-manager) narzędzie udostępnia inną metodą przechowywanie wpisów tajnych z kodu źródłowego.</span><span class="sxs-lookup"><span data-stu-id="406cb-118">The ASP.NET Core [Secret Manager](/aspnet/core/security/app-secrets#secret-manager) tool provides another method of keeping secrets out of source code.</span></span> <span data-ttu-id="406cb-119">Aby użyć narzędzia Menedżer klucz tajny, należy zainstalować pakiet **Microsoft.Extensions.Configuration.SecretManager** w pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="406cb-119">To use the Secret Manager tool, install the package **Microsoft.Extensions.Configuration.SecretManager** in your project file.</span></span> <span data-ttu-id="406cb-120">Po tej zależności jest obecny i zostało przywrócone, `dotnet user-secrets` polecenia można ustawić wartości kluczy tajnych z wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="406cb-120">Once that dependency is present and has been restored, the `dotnet user-secrets` command can be used to set the value of secrets from the command line.</span></span> <span data-ttu-id="406cb-121">Tych kluczy tajnych będą przechowywane w pliku JSON w katalogu profilu użytkownika (Szczegóły różnią się zależnie od systemu operacyjnego), od kodu źródłowego.</span><span class="sxs-lookup"><span data-stu-id="406cb-121">These secrets will be stored in a JSON file in the user’s profile directory (details vary by OS), away from source code.</span></span>

<span data-ttu-id="406cb-122">Wpisy tajne ustawione przez narzędzie Menedżer klucz tajny są uporządkowane według `UserSecretsId` właściwości projektu, który jest używany wpisy tajne.</span><span class="sxs-lookup"><span data-stu-id="406cb-122">Secrets set by the Secret Manager tool are organized by the `UserSecretsId` property of the project that's using the secrets.</span></span> <span data-ttu-id="406cb-123">W związku z tym należy ustawić właściwość UserSecretsId w pliku projektu, jak pokazano w poniższym fragmencie kodu.</span><span class="sxs-lookup"><span data-stu-id="406cb-123">Therefore, you must be sure to set the UserSecretsId property in your project file, as shown in the snippet below.</span></span> <span data-ttu-id="406cb-124">Wartość domyślna to identyfikator GUID przypisany przez program Visual Studio, ale rzeczywistego ciągu nie jest ważna, tak długo, jak jest unikatowa w komputerze.</span><span class="sxs-lookup"><span data-stu-id="406cb-124">The default value is a GUID assigned by Visual Studio, but the actual string is not important as long as it's unique in your computer.</span></span>

```xml
<PropertyGroup>
    <UserSecretsId>UniqueIdentifyingString</UserSecretsId>
</PropertyGroup>
```

<span data-ttu-id="406cb-125">Przy użyciu kluczy tajnych przechowywanych przy użyciu Menedżera klucz tajny aplikacji odbywa się przez wywołanie metody `AddUserSecrets<T>` wystąpieniu ConfigurationBuilder obejmujący wpisów tajnych aplikacji w konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="406cb-125">Using secrets stored with Secret Manager in an application is accomplished by calling `AddUserSecrets<T>` on the ConfigurationBuilder instance to include secrets for the application in its configuration.</span></span> <span data-ttu-id="406cb-126">Parametr ogólny T powinien być typem z zestawu, która UserSecretId została zastosowana do.</span><span class="sxs-lookup"><span data-stu-id="406cb-126">The generic parameter T should be a type from the assembly that the UserSecretId was applied to.</span></span> <span data-ttu-id="406cb-127">Zazwyczaj przy użyciu `AddUserSecrets<Startup>` jest w dobrym stanie.</span><span class="sxs-lookup"><span data-stu-id="406cb-127">Usually using `AddUserSecrets<Startup>` is fine.</span></span>

<span data-ttu-id="406cb-128">`AddUserSecrets<Startup>()` Są objęte domyślne opcje dotyczące środowiska programistycznego, korzystając z `CreateDefaultBuilder` method in Class metoda *Program.cs*.</span><span class="sxs-lookup"><span data-stu-id="406cb-128">The `AddUserSecrets<Startup>()` is included in the default options for the Development environment when using the `CreateDefaultBuilder` method in *Program.cs*.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="406cb-129">[Poprzednie](authorization-net-microservices-web-applications.md)
>[dalej](azure-key-vault-protects-secrets.md)</span><span class="sxs-lookup"><span data-stu-id="406cb-129">[Previous](authorization-net-microservices-web-applications.md)
[Next](azure-key-vault-protects-secrets.md)</span></span>
