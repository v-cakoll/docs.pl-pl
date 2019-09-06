---
title: Bezpieczne przechowywanie kluczy tajnych aplikacji podczas jej tworzenia
description: Zabezpieczenia w mikrousługach .NET i aplikacjach sieci Web — nie przechowuj wpisów tajnych aplikacji, takich jak hasła, parametry połączenia lub klucze interfejsu API w kontroli źródła, Poznaj opcje, których można użyć w ASP.NET Core, w szczególności musisz zrozumieć, jak obsługiwać "użytkownika wpisy tajne ".
author: mjrousos
ms.author: wiwagn
ms.date: 10/19/2018
ms.openlocfilehash: fe8e7fa11c9a4f4cae133c2e09f9e4b4dd40a546
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/30/2019
ms.locfileid: "70296485"
---
# <a name="store-application-secrets-safely-during-development"></a><span data-ttu-id="cd5a5-103">Bezpieczne przechowywanie wpisów tajnych aplikacji podczas opracowywania</span><span class="sxs-lookup"><span data-stu-id="cd5a5-103">Store application secrets safely during development</span></span>

<span data-ttu-id="cd5a5-104">Aby nawiązać połączenie z chronionymi zasobami i innymi usługami, ASP.NET Core aplikacje zwykle muszą używać parametrów połączenia, haseł lub innych poświadczeń, które zawierają informacje poufne.</span><span class="sxs-lookup"><span data-stu-id="cd5a5-104">To connect with protected resources and other services, ASP.NET Core applications typically need to use connection strings, passwords, or other credentials that contain sensitive information.</span></span> <span data-ttu-id="cd5a5-105">Te poufne informacje są nazywane *tajemnicami*.</span><span class="sxs-lookup"><span data-stu-id="cd5a5-105">These sensitive pieces of information are called *secrets*.</span></span> <span data-ttu-id="cd5a5-106">Najlepszym rozwiązaniem jest, aby nie uwzględnić wpisów tajnych w kodzie źródłowym i upewnić się, że wpisy tajne nie są przechowywane w kontroli źródła.</span><span class="sxs-lookup"><span data-stu-id="cd5a5-106">It's a best practice to not include secrets in source code and making sure not to store secrets in source control.</span></span> <span data-ttu-id="cd5a5-107">Zamiast tego należy użyć modelu konfiguracji ASP.NET Core, aby odczytać wpisy tajne z bardziej bezpiecznych lokalizacji.</span><span class="sxs-lookup"><span data-stu-id="cd5a5-107">Instead, you should use the ASP.NET Core configuration model to read the secrets from more secure locations.</span></span>

<span data-ttu-id="cd5a5-108">Należy oddzielić wpisy tajne, aby uzyskać dostęp do zasobów deweloperskich i przejściowych z tych, które są używane do uzyskiwania dostępu do zasobów produkcyjnych, ponieważ różne osoby będą potrzebować dostępu do tych różnych zestawów kluczy tajnych.</span><span class="sxs-lookup"><span data-stu-id="cd5a5-108">You must separate the secrets for accessing development and staging resources from the ones used for accessing production resources, because different individuals will need access to those different sets of secrets.</span></span> <span data-ttu-id="cd5a5-109">Aby przechowywać wpisy tajne używane podczas opracowywania, typowe podejścia do przechowywania wpisów tajnych w zmiennych środowiskowych lub za pomocą narzędzia ASP.NET Core Secret Manager.</span><span class="sxs-lookup"><span data-stu-id="cd5a5-109">To store secrets used during development, common approaches are to either store secrets in environment variables or by using the ASP.NET Core Secret Manager tool.</span></span> <span data-ttu-id="cd5a5-110">Aby zapewnić większy bezpieczny magazyn w środowiskach produkcyjnych, mikrousługi mogą przechowywać wpisy tajne w Azure Key Vault.</span><span class="sxs-lookup"><span data-stu-id="cd5a5-110">For more secure storage in production environments, microservices can store secrets in an Azure Key Vault.</span></span>

## <a name="store-secrets-in-environment-variables"></a><span data-ttu-id="cd5a5-111">Przechowuj wpisy tajne w zmiennych środowiskowych</span><span class="sxs-lookup"><span data-stu-id="cd5a5-111">Store secrets in environment variables</span></span>

<span data-ttu-id="cd5a5-112">Jednym ze sposobów utrzymywania tajemnicy kodu źródłowego jest to, aby deweloperzy mogli ustawiać klucze tajne na podstawie ciągów jako [zmienne środowiskowe](/aspnet/core/security/app-secrets#environment-variables) na swoich maszynach deweloperskich.</span><span class="sxs-lookup"><span data-stu-id="cd5a5-112">One way to keep secrets out of source code is for developers to set string-based secrets as [environment variables](/aspnet/core/security/app-secrets#environment-variables) on their development machines.</span></span> <span data-ttu-id="cd5a5-113">W przypadku używania zmiennych środowiskowych do przechowywania wpisów tajnych z nazwami hierarchicznymi, takimi jak zagnieżdżone w sekcjach konfiguracji, należy nazwać zmienne, aby uwzględnić pełną hierarchię jej sekcji, rozdzielaną średnikami (:).</span><span class="sxs-lookup"><span data-stu-id="cd5a5-113">When you use environment variables to store secrets with hierarchical names, such as the ones nested in configuration sections, you must name the variables to include the complete hierarchy of its sections, delimited with colons (:).</span></span>

<span data-ttu-id="cd5a5-114">Na przykład ustawienie zmiennej `Logging:LogLevel:Default` środowiskowej na `Debug` wartość będzie równoważne wartości konfiguracji z następującego pliku JSON:</span><span class="sxs-lookup"><span data-stu-id="cd5a5-114">For example, setting an environment variable `Logging:LogLevel:Default` to `Debug` value would be equivalent to a configuration value from the following JSON file:</span></span>

```json
{
    "Logging": {
        "LogLevel": {
            "Default": "Debug"
        }
    }
}
```

<span data-ttu-id="cd5a5-115">Aby uzyskać dostęp do tych wartości ze zmiennych środowiskowych, aplikacja po prostu musi wywołać AddEnvironmentVariables na ConfigurationBuilder podczas konstruowania obiektu IConfigurationRoot.</span><span class="sxs-lookup"><span data-stu-id="cd5a5-115">To access these values from environment variables, the application just needs to call AddEnvironmentVariables on its ConfigurationBuilder when constructing an IConfigurationRoot object.</span></span>

<span data-ttu-id="cd5a5-116">Należy pamiętać, że zmienne środowiskowe są zwykle przechowywane jako zwykły tekst, więc jeśli komputer lub proces ze zmiennymi środowiskowymi zostanie naruszony, wartości zmiennych środowiskowych będą widoczne.</span><span class="sxs-lookup"><span data-stu-id="cd5a5-116">Note that environment variables are commonly stored as plain text, so if the machine or process with the environment variables is compromised, the environment variable values will be visible.</span></span>

## <a name="store-secrets-with-the-aspnet-core-secret-manager"></a><span data-ttu-id="cd5a5-117">Przechowywanie wpisów tajnych za pomocą programu ASP.NET Core Secret Manager</span><span class="sxs-lookup"><span data-stu-id="cd5a5-117">Store secrets with the ASP.NET Core Secret Manager</span></span>

<span data-ttu-id="cd5a5-118">Narzędzie ASP.NET Core [Secret Manager](/aspnet/core/security/app-secrets#secret-manager) zapewnia kolejną metodę utrzymywania wpisów tajnych z kodu źródłowego.</span><span class="sxs-lookup"><span data-stu-id="cd5a5-118">The ASP.NET Core [Secret Manager](/aspnet/core/security/app-secrets#secret-manager) tool provides another method of keeping secrets out of source code.</span></span> <span data-ttu-id="cd5a5-119">Aby użyć narzędzia Secret Manager, zainstaluj pakiet **Microsoft. Extensions. Configuration. SecretManager** w pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="cd5a5-119">To use the Secret Manager tool, install the package **Microsoft.Extensions.Configuration.SecretManager** in your project file.</span></span> <span data-ttu-id="cd5a5-120">Gdy ta zależność jest obecna i przywrócona, `dotnet user-secrets` polecenie może służyć do ustawiania wartości wpisów tajnych z wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="cd5a5-120">Once that dependency is present and has been restored, the `dotnet user-secrets` command can be used to set the value of secrets from the command line.</span></span> <span data-ttu-id="cd5a5-121">Te wpisy tajne będą przechowywane w pliku JSON w katalogu profilu użytkownika (szczegóły różnią się w zależności od systemu operacyjnego), a nie od kodu źródłowego.</span><span class="sxs-lookup"><span data-stu-id="cd5a5-121">These secrets will be stored in a JSON file in the user’s profile directory (details vary by OS), away from source code.</span></span>

<span data-ttu-id="cd5a5-122">Wpisy tajne ustawiane przez narzędzie tajnego Menedżera są `UserSecretsId` zorganizowane według właściwości projektu, który używa wpisów tajnych.</span><span class="sxs-lookup"><span data-stu-id="cd5a5-122">Secrets set by the Secret Manager tool are organized by the `UserSecretsId` property of the project that's using the secrets.</span></span> <span data-ttu-id="cd5a5-123">W związku z tym należy ustawić właściwość UserSecretsId w pliku projektu, jak pokazano w poniższym fragmencie kodu.</span><span class="sxs-lookup"><span data-stu-id="cd5a5-123">Therefore, you must be sure to set the UserSecretsId property in your project file, as shown in the snippet below.</span></span> <span data-ttu-id="cd5a5-124">Wartość domyślna to identyfikator GUID przypisany przez program Visual Studio, ale rzeczywisty ciąg nie jest ważny, o ile jest unikatowy na komputerze.</span><span class="sxs-lookup"><span data-stu-id="cd5a5-124">The default value is a GUID assigned by Visual Studio, but the actual string is not important as long as it's unique in your computer.</span></span>

```xml
<PropertyGroup>
    <UserSecretsId>UniqueIdentifyingString</UserSecretsId>
</PropertyGroup>
```

<span data-ttu-id="cd5a5-125">Korzystanie z wpisów tajnych przechowywanych w ramach Menedżera wpisów tajnych w aplikacji `AddUserSecrets<T>` jest realizowane przez wywołanie wystąpienia ConfigurationBuilder w celu uwzględnienia wpisów tajnych aplikacji w konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="cd5a5-125">Using secrets stored with Secret Manager in an application is accomplished by calling `AddUserSecrets<T>` on the ConfigurationBuilder instance to include secrets for the application in its configuration.</span></span> <span data-ttu-id="cd5a5-126">Parametr generyczny T powinien być typem z zestawu, do którego zastosowano UserSecretId.</span><span class="sxs-lookup"><span data-stu-id="cd5a5-126">The generic parameter T should be a type from the assembly that the UserSecretId was applied to.</span></span> <span data-ttu-id="cd5a5-127">Zwykle korzystanie `AddUserSecrets<Startup>` z programu jest bardzo precyzyjne.</span><span class="sxs-lookup"><span data-stu-id="cd5a5-127">Usually using `AddUserSecrets<Startup>` is fine.</span></span>

<span data-ttu-id="cd5a5-128">Program jest zawarty w domyślnych opcjach środowiska programistycznego, gdy jest `CreateDefaultBuilder` używana metoda w *program.cs*. `AddUserSecrets<Startup>()`</span><span class="sxs-lookup"><span data-stu-id="cd5a5-128">The `AddUserSecrets<Startup>()` is included in the default options for the Development environment when using the `CreateDefaultBuilder` method in *Program.cs*.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="cd5a5-129">[Poprzedni](authorization-net-microservices-web-applications.md)Następny
>[](azure-key-vault-protects-secrets.md)</span><span class="sxs-lookup"><span data-stu-id="cd5a5-129">[Previous](authorization-net-microservices-web-applications.md)
[Next](azure-key-vault-protects-secrets.md)</span></span>
