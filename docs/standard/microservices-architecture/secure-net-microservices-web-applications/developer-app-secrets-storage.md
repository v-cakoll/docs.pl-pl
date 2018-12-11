---
title: Bezpieczne przechowywanie wpisów tajnych aplikacji podczas programowania
description: Architektura Mikrousług .NET konteneryzowanych aplikacji .NET | Bezpieczne przechowywanie wpisów tajnych aplikacji podczas programowania
author: mjrousos
ms.author: wiwagn
ms.date: 05/26/2017
ms.openlocfilehash: 6f5dfbb53b99fec4d7cc66c528fe866c71c2172f
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2018
ms.locfileid: "53143873"
---
# <a name="storing-application-secrets-safely-during-development"></a><span data-ttu-id="e740d-103">Bezpieczne przechowywanie wpisów tajnych aplikacji podczas programowania</span><span class="sxs-lookup"><span data-stu-id="e740d-103">Storing application secrets safely during development</span></span>

<span data-ttu-id="e740d-104">Aby połączyć się z chronionych zasobów i inne usługi, aplikacje platformy ASP.NET Core zazwyczaj należy użyć parametrów połączenia, hasła lub inne poświadczenia, które zawierają poufne informacje.</span><span class="sxs-lookup"><span data-stu-id="e740d-104">To connect with protected resources and other services, ASP.NET Core applications typically need to use connection strings, passwords, or other credentials that contain sensitive information.</span></span> <span data-ttu-id="e740d-105">Te elementy poufnych informacji są nazywane *wpisów tajnych*.</span><span class="sxs-lookup"><span data-stu-id="e740d-105">These sensitive pieces of information are called *secrets*.</span></span> <span data-ttu-id="e740d-106">Jest najlepszym rozwiązaniem jest wykluczającą wpisów tajnych w kodzie źródłowym i na pewno nie do przechowywania wpisów tajnych w kontroli źródła.</span><span class="sxs-lookup"><span data-stu-id="e740d-106">It is a best practice to not include secrets in source code and certainly not to store secrets in source control.</span></span> <span data-ttu-id="e740d-107">Zamiast tego należy użyć modelu konfiguracji platformy ASP.NET Core na odczyt kluczy tajnych z bardziej bezpiecznych lokalizacjach.</span><span class="sxs-lookup"><span data-stu-id="e740d-107">Instead, you should use the ASP.NET Core configuration model to read the secrets from more secure locations.</span></span>

<span data-ttu-id="e740d-108">Należy oddzielić wpisów tajnych dla uzyskiwanie dostępu do programowania i przemieszczania zasobów używanych do uzyskiwania dostępu do zasobów w środowisku produkcyjnym, ponieważ inne osoby będą potrzebowali dostępu do tych różnych zestawów wpisów tajnych.</span><span class="sxs-lookup"><span data-stu-id="e740d-108">You should separate the secrets for accessing development and staging resources from those used for accessing production resources, because different individuals will need access to those different sets of secrets.</span></span> <span data-ttu-id="e740d-109">Do przechowywania wpisów tajnych używanych podczas tworzenia, wspólnego podejścia są przechowywanie wpisów tajnych w zmiennych środowiskowych lub za pomocą narzędzia ASP.NET Core klucz tajny menedżera.</span><span class="sxs-lookup"><span data-stu-id="e740d-109">To store secrets used during development, common approaches are to either store secrets in environment variables or by using the ASP.NET Core Secret Manager tool.</span></span> <span data-ttu-id="e740d-110">Dla bardziej bezpieczne przechowywanie w środowiskach produkcyjnych mikrousługi można przechowywać wpisy tajne w usłudze Azure Key Vault.</span><span class="sxs-lookup"><span data-stu-id="e740d-110">For more secure storage in production environments, microservices can store secrets in an Azure Key Vault.</span></span>

## <a name="storing-secrets-in-environment-variables"></a><span data-ttu-id="e740d-111">Przechowywanie kluczy tajnych w zmiennych środowiskowych</span><span class="sxs-lookup"><span data-stu-id="e740d-111">Storing secrets in environment variables</span></span>

<span data-ttu-id="e740d-112">Jest jednym ze sposobów odróżnienia wpisy tajne z kodu źródłowego, deweloperzy mogą ustawić oparte na ciągach wpisów tajnych jako [zmienne środowiskowe](https://docs.microsoft.com/aspnet/core/security/app-secrets#environment-variables) na swoich komputerach deweloperskich.</span><span class="sxs-lookup"><span data-stu-id="e740d-112">One way to keep secrets out of source code is for developers to set string-based secrets as [environment variables](https://docs.microsoft.com/aspnet/core/security/app-secrets#environment-variables) on their development machines.</span></span> <span data-ttu-id="e740d-113">Użycie zmiennych środowiskowych do przechowywania wpisów tajnych za pomocą nazwy hierarchiczne, (te zagnieżdżonego w sekcji konfiguracji), Utwórz nazwę zmiennych środowiskowych, która zawiera pełnej hierarchii o nazwie klucza tajnego, lista z dwukropkiem (:).</span><span class="sxs-lookup"><span data-stu-id="e740d-113">When you use environment variables to store secrets with hierarchical names (those nested in configuration sections), create a name for the environment variables that includes the full hierarchy of the secret’s name, delimited with colons (:).</span></span>

<span data-ttu-id="e740d-114">Na przykład ustawienie zmiennej środowiskowej rejestrowania: LogLevel:Default debugowania byłaby równoważna wartości konfiguracji z następującego pliku JSON:</span><span class="sxs-lookup"><span data-stu-id="e740d-114">For example, setting an environment variable Logging:LogLevel:Default to Debug would be equivalent to a configuration value from the following JSON file:</span></span>

```json
{
    "Logging": {
        "LogLevel": {
            "Default": "Debug"
        }
    }
}
```

<span data-ttu-id="e740d-115">Dostępu do tych wartości w zmiennych środowiskowych, aplikacja musi jedynie może wywołać jej ConfigurationBuilder AddEnvironmentVariables przy konstruowaniu obiektu IConfigurationRoot.</span><span class="sxs-lookup"><span data-stu-id="e740d-115">To access these values from environment variables, the application just needs to call AddEnvironmentVariables on its ConfigurationBuilder when constructing an IConfigurationRoot object.</span></span>

<span data-ttu-id="e740d-116">Należy pamiętać, że zmienne środowiskowe zazwyczaj są przechowywane jako zwykły tekst, więc w przypadku naruszenia zabezpieczeń komputera lub proces, za pomocą zmiennych środowiskowych, wartości zmiennych środowiskowych będą widoczne.</span><span class="sxs-lookup"><span data-stu-id="e740d-116">Note that environment variables are generally stored as plain text, so if the machine or process with the environment variables is compromised, the environment variable values will be visible.</span></span>

## <a name="storing-secrets-using-the-aspnet-core-secret-manager"></a><span data-ttu-id="e740d-117">Przechowywanie wpisów tajnych przy użyciu Menedżera klucz tajny platformy ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="e740d-117">Storing secrets using the ASP.NET Core Secret Manager</span></span>

<span data-ttu-id="e740d-118">ASP.NET Core [Menedżera klucz tajny](https://docs.microsoft.com/aspnet/core/security/app-secrets#secret-manager) narzędzie udostępnia inną metodą przechowywanie wpisów tajnych z kodu źródłowego.</span><span class="sxs-lookup"><span data-stu-id="e740d-118">The ASP.NET Core [Secret Manager](https://docs.microsoft.com/aspnet/core/security/app-secrets#secret-manager) tool provides another method of keeping secrets out of source code.</span></span> <span data-ttu-id="e740d-119">Aby użyć narzędzia menedżera klucz tajny, należy dołączyć odwołanie narzędzia (DotNetCliToolReference) do pakietu Microsoft.Extensions.SecretManager.Tools w pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="e740d-119">To use the Secret Manager tool, include a tools reference (DotNetCliToolReference) to the Microsoft.Extensions.SecretManager.Tools package in your project file.</span></span> <span data-ttu-id="e740d-120">Po tej zależności i zostało przywrócone, polecenia dotnet wpisami tajnymi użytkowników może służyć do ustawiania wartości kluczy tajnych z wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="e740d-120">Once that dependency is present and has been restored, the dotnet user-secrets command can be used to set the value of secrets from the command line.</span></span> <span data-ttu-id="e740d-121">Tych kluczy tajnych będą przechowywane w pliku JSON w katalogu profilu użytkownika (Szczegóły różnią się zależnie od systemu operacyjnego), od kodu źródłowego.</span><span class="sxs-lookup"><span data-stu-id="e740d-121">These secrets will be stored in a JSON file in the user’s profile directory (details vary by OS), away from source code.</span></span>

<span data-ttu-id="e740d-122">Wpisy tajne ustawione przez narzędzie Menedżer klucz tajny są uporządkowane według właściwości UserSecretsId projektu, który jest używany wpisy tajne.</span><span class="sxs-lookup"><span data-stu-id="e740d-122">Secrets set by the Secret Manager tool are organized by the UserSecretsId property of the project that is using the secrets.</span></span> <span data-ttu-id="e740d-123">W związku z tym należy ustawić właściwość UserSecretsId w pliku projektu (jak pokazano w poniższym fragmencie kodu).</span><span class="sxs-lookup"><span data-stu-id="e740d-123">Therefore, you must be sure to set the UserSecretsId property in your project file (as shown in the snippet below).</span></span> <span data-ttu-id="e740d-124">Rzeczywisty ciąg używany jako identyfikator nie jest ważna, tak długo, jak jest unikatowa w projekcie.</span><span class="sxs-lookup"><span data-stu-id="e740d-124">The actual string used as the ID is not important as long as it is unique in the project.</span></span>

```xml
<PropertyGroup>
    <UserSecretsId>UniqueIdentifyingString</UserSecretsId>
</PropertyGroup>
```

<span data-ttu-id="e740d-125">Przy użyciu kluczy tajnych przechowywanych przy użyciu Menedżera klucz tajny aplikacji odbywa się przez wywołanie metody AddUserSecrets&lt;T&gt; wystąpieniu ConfigurationBuilder obejmujący wpisów tajnych aplikacji w konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="e740d-125">Using secrets stored with Secret Manager in an application is accomplished by calling AddUserSecrets&lt;T&gt; on the ConfigurationBuilder instance to include secrets for the application in its configuration.</span></span> <span data-ttu-id="e740d-126">Parametr ogólny T powinien być typem z zestawu, która UserSecretId została zastosowana do.</span><span class="sxs-lookup"><span data-stu-id="e740d-126">The generic parameter T should be a type from the assembly that the UserSecretId was applied to.</span></span> <span data-ttu-id="e740d-127">Zazwyczaj przy użyciu AddUserSecrets&lt;uruchamiania&gt; jest w dobrym stanie.</span><span class="sxs-lookup"><span data-stu-id="e740d-127">Usually using AddUserSecrets&lt;Startup&gt; is fine.</span></span>


>[!div class="step-by-step"]
><span data-ttu-id="e740d-128">[Poprzednie](authorization-net-microservices-web-applications.md)
>[dalej](azure-key-vault-protects-secrets.md)</span><span class="sxs-lookup"><span data-stu-id="e740d-128">[Previous](authorization-net-microservices-web-applications.md)
[Next](azure-key-vault-protects-secrets.md)</span></span>