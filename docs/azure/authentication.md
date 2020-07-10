---
title: Informacje o uwierzytelnianiu w bibliotekach platformy Azure dla platformy .NET
description: Wyjaśnia różne sposoby uwierzytelniania przy użyciu zestawu Azure SDK dla platformy .NET.
ms.date: 06/19/2020
ms.custom: azure-sdk-dotnet
ms.openlocfilehash: 5ed29d5485dc7f59bcc757c8903116edf6bd5d7d
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/09/2020
ms.locfileid: "86174969"
---
# <a name="authenticate-with-the-azure-sdk-for-net"></a><span data-ttu-id="66901-103">Uwierzytelnianie za pomocą zestawu Azure SDK dla platformy .NET</span><span class="sxs-lookup"><span data-stu-id="66901-103">Authenticate with the Azure SDK for .NET</span></span>

## <a name="recommended-azureidentity"></a><span data-ttu-id="66901-104">Zalecane: Azure. Identity</span><span class="sxs-lookup"><span data-stu-id="66901-104">Recommended: Azure.Identity</span></span>

<span data-ttu-id="66901-105">Najnowsze pakiety w zestawie Azure SDK dla platformy .NET używają wspólnego pakietu uwierzytelniania do uwierzytelniania `Azure.Identity` .</span><span class="sxs-lookup"><span data-stu-id="66901-105">The latest packages in the Azure SDK for .NET use a common authentication package to authenticate, `Azure.Identity`.</span></span> <span data-ttu-id="66901-106">Użycie `Azure.Identity` jest zalecane w porównaniu z innymi mechanizmami uwierzytelniania opisanymi w dalszej części tego dokumentu.</span><span class="sxs-lookup"><span data-stu-id="66901-106">Using `Azure.Identity` is recommended over other authentication mechanisms described later in this document.</span></span> <span data-ttu-id="66901-107">Pakiety obsługujące poświadczenia dostarczone przez `Azure.Identity` program mają identyfikatory pakietów rozpoczynające się od *platformy Azure.*</span><span class="sxs-lookup"><span data-stu-id="66901-107">Packages supporting the credentials provided by `Azure.Identity` have package identifiers starting with *Azure.*</span></span> <span data-ttu-id="66901-108">[Aby uzyskać więcej informacji, zobacz najnowsze wersje zestawu Azure SDK dla platformy .NET](https://azure.github.io/azure-sdk/releases/latest/index.html#net).</span><span class="sxs-lookup"><span data-stu-id="66901-108">[For more information, see the latest releases in the Azure SDK for .NET](https://azure.github.io/azure-sdk/releases/latest/index.html#net).</span></span>

<span data-ttu-id="66901-109">Aby uzyskać pełne instrukcje dotyczące korzystania `Azure.Identity` z programu w projekcie, zapoznaj się z dokumentacją [klienta tożsamości platformy Azure dla platformy .NET](/dotnet/api/overview/azure/identity-readme).</span><span class="sxs-lookup"><span data-stu-id="66901-109">For complete instructions on using `Azure.Identity` in your project, see the documentation for [Azure Identity client for .NET](/dotnet/api/overview/azure/identity-readme).</span></span>

> [!TIP]
> <span data-ttu-id="66901-110">Przykłady dotyczące korzystania z usługi Azure Identity do zarządzania zasobami platformy Azure i uzyskiwania do nich dostępu można znaleźć w temacie [tożsamość platformy Azure, zarządzanie zasobami i przykład magazynu](/samples/dotnet/samples/azure-identity-resource-management-storage/) .</span><span class="sxs-lookup"><span data-stu-id="66901-110">See the [Azure Identity, Resource Management, and Storage sample](/samples/dotnet/samples/azure-identity-resource-management-storage/) for examples of using Azure Identity to manage and access Azure resources.</span></span>

<span data-ttu-id="66901-111">Aby uwierzytelnić się w bibliotekach, które nie obsługują platformy Azure. tożsamość, zobacz pozostała część tego tematu.</span><span class="sxs-lookup"><span data-stu-id="66901-111">To authenticate with libraries that don't support Azure.Identity, see the rest of this topic.</span></span>

## <a name="access-azure-resources"></a><span data-ttu-id="66901-112">Dostęp do zasobów platformy Azure</span><span class="sxs-lookup"><span data-stu-id="66901-112">Access Azure resources</span></span>

<span data-ttu-id="66901-113">Aby można było korzystać z zasobów platformy Azure, takich jak pobieranie klucza tajnego z Key Vault lub przechowywanie obiektu BLOB w magazynie, wiele bibliotek usług platformy Azure wymaga parametrów połączenia lub kluczy do uwierzytelnienia.</span><span class="sxs-lookup"><span data-stu-id="66901-113">To interact with Azure resources, such as retrieving a secret from Key Vault or storing a blob in Storage, many Azure service libraries require a connection string or keys for authentication.</span></span> <span data-ttu-id="66901-114">Na przykład SQL Database używa [standardowych parametrów połączenia SQL](https://docs.microsoft.com/azure/azure-sql/database/connect-query-dotnet-core).</span><span class="sxs-lookup"><span data-stu-id="66901-114">For example, SQL Database uses a [standard SQL connection string](https://docs.microsoft.com/azure/azure-sql/database/connect-query-dotnet-core).</span></span> <span data-ttu-id="66901-115">Parametry połączenia usługi są używane w innych usługach platformy Azure, takich jak [CosmosDB](/azure/cosmos-db/), [pamięć podręczna platformy Azure dla Redis](/azure/azure-cache-for-redis/cache-dotnet-how-to-use-azure-redis-cache)i [Service Bus](/azure/service-bus-messaging/service-bus-dotnet-get-started-with-queues).</span><span class="sxs-lookup"><span data-stu-id="66901-115">Service connection strings are used in other Azure services like [CosmosDB](/azure/cosmos-db/), [Azure Cache for Redis](/azure/azure-cache-for-redis/cache-dotnet-how-to-use-azure-redis-cache), and [Service Bus](/azure/service-bus-messaging/service-bus-dotnet-get-started-with-queues).</span></span> <span data-ttu-id="66901-116">Te ciągi można pobrać przy użyciu Azure Portal, interfejsu wiersza polecenia lub programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="66901-116">You can get those strings using the Azure portal, CLI, or PowerShell.</span></span> <span data-ttu-id="66901-117">Za pomocą bibliotek zarządzania platformy Azure dla platformy .NET można także wysyłać zapytania do zasobów w celu tworzenia parametrów połączenia w kodzie.</span><span class="sxs-lookup"><span data-stu-id="66901-117">You can also use the Azure management libraries for .NET to query resources to build connection strings in your code.</span></span>

<span data-ttu-id="66901-118">Metody używania parametrów połączenia różnią się w zależności od produktu.</span><span class="sxs-lookup"><span data-stu-id="66901-118">The methods for using a connection string vary by product.</span></span> <span data-ttu-id="66901-119">[Zapoznaj się z dokumentacją dotyczącą produktu platformy Azure](/azure/?product=featured).</span><span class="sxs-lookup"><span data-stu-id="66901-119">[Refer to the documentation for your Azure product](/azure/?product=featured).</span></span>

## <a name="manage-azure-resources"></a><span data-ttu-id="66901-120">Zarządzanie zasobami platformy Azure</span><span class="sxs-lookup"><span data-stu-id="66901-120">Manage Azure resources</span></span>

[!include[Create service principal](includes/create-sp.md)]

<span data-ttu-id="66901-121">Po utworzeniu jednostki usługi dostępne są dwie opcje uwierzytelniania dla jednostki usługi w celu utworzenia zasobów i zarządzania nimi.</span><span class="sxs-lookup"><span data-stu-id="66901-121">Now that the service principal is created, two options are available to authenticate to the service principal to create and manage resources.</span></span>

<span data-ttu-id="66901-122">W przypadku obu opcji należy dodać następujące pakiety NuGet do projektu.</span><span class="sxs-lookup"><span data-stu-id="66901-122">For both options you will need to add the following NuGet packages to your project.</span></span>

```powershell
Install-Package Microsoft.Azure.Management.Fluent
Install-Package Microsoft.Azure.Management.ResourceManager.Fluent
```

### <a name="authenticate-with-token-credentials"></a><span data-ttu-id="66901-123">Uwierzytelnianie przy użyciu poświadczeń tokenu</span><span class="sxs-lookup"><span data-stu-id="66901-123">Authenticate with token credentials</span></span>

<span data-ttu-id="66901-124">Pierwsza metoda polega na utworzeniu obiektu poświadczeń tokenu w kodzie.</span><span class="sxs-lookup"><span data-stu-id="66901-124">The first method is to build the token credential object in code.</span></span> <span data-ttu-id="66901-125">Poświadczenia powinny być bezpiecznie przechowywane w pliku konfiguracyjnym, rejestrze lub w magazynie kluczy platformy Azure.</span><span class="sxs-lookup"><span data-stu-id="66901-125">You should store the credentials securely in a configuration file, the registry, or Azure KeyVault.</span></span>

```csharp
var credentials = SdkContext.AzureCredentialsFactory
    .FromServicePrincipal(clientId,
        clientSecret,
        tenantId,
        AzureEnvironment.AzureGlobalCloud);
```

<span data-ttu-id="66901-126">Podczas tworzenia nazwy głównej usługi Użyj wartości *clientId*, *clientSecret*i *TENANTID* z danych wyjściowych JSON.</span><span class="sxs-lookup"><span data-stu-id="66901-126">Use the *clientId*, *clientSecret*, and *tenantId* values from the JSON output when you created the service principal.</span></span>

<span data-ttu-id="66901-127">Następnie Utwórz obiekt punktu wejścia, `Azure` Aby rozpocząć pracę z interfejsem API:</span><span class="sxs-lookup"><span data-stu-id="66901-127">Then create the entry point `Azure` object to start working with the API:</span></span>

```csharp
var azure = Microsoft.Azure.Management.Fluent.Azure
    .Configure()
    .Authenticate(credentials)
    .WithDefaultSubscription();
```

### <a name="file-based-authentication"></a><a name="mgmt-file"></a><span data-ttu-id="66901-128">Uwierzytelnianie oparte na plikach</span><span class="sxs-lookup"><span data-stu-id="66901-128">File-based authentication</span></span>

<span data-ttu-id="66901-129">Uwierzytelnianie oparte na plikach umożliwia umieszczenie poświadczeń jednostki usługi w zwykłym pliku tekstowym i zabezpieczenie go w systemie plików.</span><span class="sxs-lookup"><span data-stu-id="66901-129">File-based authentication allows you to put the service principal credentials in a plain text file and secure it within the file system.</span></span>

[!include[File-based authentication](includes/file-based-auth.md)]

<span data-ttu-id="66901-130">Odczytaj zawartość pliku i Utwórz obiekt punktu wejścia, `Azure` Aby rozpocząć pracę z interfejsem API:</span><span class="sxs-lookup"><span data-stu-id="66901-130">Read the contents of the file and create the entry point `Azure` object to start working with the API:</span></span>

```csharp
// pull in the location of the authentication properties file from the environment
var credentials = SdkContext.AzureCredentialsFactory
    .FromFile(Environment.GetEnvironmentVariable("AZURE_AUTH_LOCATION"));

var azure = Microsoft.Azure.Management.Fluent.Azure
    .Configure()
    .Authenticate(credentials)
    .WithDefaultSubscription();
```
