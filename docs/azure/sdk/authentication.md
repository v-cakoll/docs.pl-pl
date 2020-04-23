---
title: Uwierzytelnij się za pomocą bibliotek platformy Azure dla platformy .NET
description: Uwierzytelnij się w bibliotekach platformy Azure dla platformy .NET
ms.date: 08/22/2018
ms.custom: azure-sdk-dotnet
ms.openlocfilehash: f6af813cd1423be8784b769b272756b2c8258392
ms.sourcegitcommit: d9470d8b2278b33108332c05224d86049cb9484b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/17/2020
ms.locfileid: "82072152"
---
# <a name="authenticate-with-the-azure-libraries-for-net"></a><span data-ttu-id="0c055-103">Uwierzytelnij się za pomocą bibliotek platformy Azure dla platformy .NET</span><span class="sxs-lookup"><span data-stu-id="0c055-103">Authenticate with the Azure Libraries for .NET</span></span>

## <a name="connect-to-services-with-connection-strings"></a><span data-ttu-id="0c055-104">Łączenie się z usługami przy użyciu parametrów połączenia</span><span class="sxs-lookup"><span data-stu-id="0c055-104">Connect to services with connection strings</span></span>

<span data-ttu-id="0c055-105">Większość bibliotek usług platformy Azure wymaga ciągu połączenia lub kluczy do uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="0c055-105">Most Azure service libraries require a connection string or keys for authentication.</span></span> <span data-ttu-id="0c055-106">Na przykład baza danych SQL używa standardowego ciągu połączenia SQL:</span><span class="sxs-lookup"><span data-stu-id="0c055-106">For example, SQL Database uses a standard SQL connection string:</span></span>

```csharp
var builder = new SqlConnectionStringBuilder();
builder.DataSource = "example.database.windows.net";
builder.InitialCatalog = "MyDatabase";
builder.UserID = "sampleuser@example"; // Format user ID as "user@server"
builder.Password = password;
builder.Encrypt = true;
builder.TrustServerCertificate = true;

using (var conn = new SqlConnection(builder.ConnectionString))
{
    conn.Open();
    // Do things with the connection...
    // ...
}
```

<span data-ttu-id="0c055-107">Usługa Azure Storage używa klucza magazynu:</span><span class="sxs-lookup"><span data-stu-id="0c055-107">Azure Storage uses a storage key:</span></span>

```csharp
string storageConnectionString = "DefaultEndpointsProtocol=https;"
        + "AccountName=" + storageName
        + ";AccountKey=" + storageKey
        + ";EndpointSuffix=core.windows.net";

var account = CloudStorageAccount.Parse(storageConnectionString);
// Do things with the account here...
```

<span data-ttu-id="0c055-108">Parametry połączenia usługi są używane w innych usługach platformy Azure, takich jak [CosmosDB](https://docs.microsoft.com/azure/cosmos-db/), [Azure Cache for Redis](https://docs.microsoft.com/azure/azure-cache-for-redis/cache-dotnet-how-to-use-azure-redis-cache)i [Service Bus](https://docs.microsoft.com/azure/service-bus-messaging/service-bus-dotnet-get-started-with-queues).</span><span class="sxs-lookup"><span data-stu-id="0c055-108">Service connection strings are used in other Azure services like [CosmosDB](https://docs.microsoft.com/azure/cosmos-db/), [Azure Cache for Redis](https://docs.microsoft.com/azure/azure-cache-for-redis/cache-dotnet-how-to-use-azure-redis-cache), and [Service Bus](https://docs.microsoft.com/azure/service-bus-messaging/service-bus-dotnet-get-started-with-queues).</span></span> <span data-ttu-id="0c055-109">Te ciągi można uzyskać przy użyciu witryny Azure portal, interfejsu wiersza polecenia lub programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="0c055-109">You can get those strings using the Azure portal, CLI, or PowerShell.</span></span> <span data-ttu-id="0c055-110">Można również użyć bibliotek zarządzania platformy Azure dla platformy .NET do wykonywania zapytań o zasoby do tworzenia ciągów połączeń w kodzie.</span><span class="sxs-lookup"><span data-stu-id="0c055-110">You can also use the Azure management libraries for .NET to query resources to build connection strings in your code.</span></span>

<span data-ttu-id="0c055-111">Ten fragment kodu używa bibliotek zarządzania do utworzenia ciągu połączenia konta magazynu:</span><span class="sxs-lookup"><span data-stu-id="0c055-111">This snippet uses the management libraries to create a storage account connection string:</span></span>

```csharp
// Get a storage account
var storage = azure.StorageAccounts.GetByResourceGroup("myResourceGroup", "myStorageAccount");

// Extract the keys
var storageKeys = storage.GetKeys();

// Build the connection string
string storageConnectionString = "DefaultEndpointsProtocol=https;"
        + "AccountName=" + storage.Name
        + ";AccountKey=" + storageKeys[0].Value
        + ";EndpointSuffix=core.windows.net";

// Connect
var account = CloudStorageAccount.Parse(storageConnectionString);

// Do things with the account here...
```

<span data-ttu-id="0c055-112">Inne biblioteki wymagają, aby aplikacja działała z [jednostką usługi](https://docs.microsoft.com/azure/active-directory/develop/active-directory-application-objects), która autoryzuje aplikację do działania z udzielonymi poświadczeniami.</span><span class="sxs-lookup"><span data-stu-id="0c055-112">Other libraries require your application to run with a [service principal](https://docs.microsoft.com/azure/active-directory/develop/active-directory-application-objects) authorizing the application to run with granted credentials.</span></span> <span data-ttu-id="0c055-113">Ta konfiguracja jest podobna do kroków uwierzytelniania opartego na obiektach dla wymienionej poniżej biblioteki zarządzania.</span><span class="sxs-lookup"><span data-stu-id="0c055-113">This configuration is similar to the object-based authentication steps for the management library listed below.</span></span>

## <a name="azure-management-libraries-for-net-authentication"></a><a name="mgmt-auth"></a><span data-ttu-id="0c055-114">Biblioteki zarządzania platformy Azure dla uwierzytelniania .NET</span><span class="sxs-lookup"><span data-stu-id="0c055-114">Azure management libraries for .NET authentication</span></span>

[!include[Create service principal](../includes/create-sp.md)]

<span data-ttu-id="0c055-115">Teraz, gdy podmiot zabezpieczeń usługi jest tworzony, dwie opcje są dostępne do uwierzytelniania do jednostki usługi do tworzenia zasobów i zarządzania nimi.</span><span class="sxs-lookup"><span data-stu-id="0c055-115">Now that the service principal is created, two options are available to authenticate to the service principal to create and manage resources.</span></span>

<span data-ttu-id="0c055-116">Dla obu opcji należy dodać następujące pakiety NuGet do projektu.</span><span class="sxs-lookup"><span data-stu-id="0c055-116">For both options you will need to add the following NuGet packages to your project.</span></span>

```powershell
Install-Package Microsoft.Azure.Management.Fluent
Install-Package Microsoft.Azure.Management.ResourceManager.Fluent
```

### <a name="authenticate-with-token-credentials"></a><span data-ttu-id="0c055-117">Uwierzytelnij się przy użyciu poświadczeń tokenu</span><span class="sxs-lookup"><span data-stu-id="0c055-117">Authenticate with token credentials</span></span>

<span data-ttu-id="0c055-118">Pierwszą metodą jest tworzenie obiektu poświadczeń tokenu w kodzie.</span><span class="sxs-lookup"><span data-stu-id="0c055-118">The first method is to build the token credential object in code.</span></span> <span data-ttu-id="0c055-119">Poświadczenia należy bezpiecznie przechowywać w pliku konfiguracji, rejestrze lub usłudze Azure KeyVault.</span><span class="sxs-lookup"><span data-stu-id="0c055-119">You should store the credentials securely in a configuration file, the registry, or Azure KeyVault.</span></span>

```csharp
var credentials = SdkContext.AzureCredentialsFactory
    .FromServicePrincipal(clientId,
    clientSecret,
    tenantId,
    AzureEnvironment.AzureGlobalCloud);
```

<span data-ttu-id="0c055-120">Użyj *clientId*, *clientSecret*i *tenantId* wartości z danych wyjściowych JSON podczas tworzenia jednostki usługi.</span><span class="sxs-lookup"><span data-stu-id="0c055-120">Use the *clientId*, *clientSecret*, and *tenantId* values from the JSON output when you created the service principal.</span></span>

<span data-ttu-id="0c055-121">Następnie utwórz `Azure` obiekt punktu wejścia, aby rozpocząć pracę z interfejsem API:</span><span class="sxs-lookup"><span data-stu-id="0c055-121">Then create the entry point `Azure` object to start working with the API:</span></span>

```csharp
var azure = Microsoft.Azure.Management.Fluent.Azure
    .Configure()
    .Authenticate(credentials)
    .WithDefaultSubscription();
```

### <a name="file-based-authentication"></a><a name="mgmt-file"></a><span data-ttu-id="0c055-122">Uwierzytelnianie oparte na plikach</span><span class="sxs-lookup"><span data-stu-id="0c055-122">File-based authentication</span></span>

<span data-ttu-id="0c055-123">Uwierzytelnianie oparte na plikach umożliwia umieszczenie poświadczeń jednostki usługi w pliku tekstowym i zabezpieczenie ich w systemie plików.</span><span class="sxs-lookup"><span data-stu-id="0c055-123">File-based authentication allows you to put the service principal credentials in a plain text file and secure it within the file system.</span></span>

[!include[File-based authentication](../includes/file-based-auth.md)]

<span data-ttu-id="0c055-124">Przeczytaj zawartość pliku i utwórz `Azure` obiekt punktu wejścia, aby rozpocząć pracę z interfejsem API:</span><span class="sxs-lookup"><span data-stu-id="0c055-124">Read the contents of the file and create the entry point `Azure` object to start working with the API:</span></span>

```csharp
// pull in the location of the authentication properties file from the environment
var credentials = SdkContext.AzureCredentialsFactory
    .FromFile(Environment.GetEnvironmentVariable("AZURE_AUTH_LOCATION"));

var azure = Microsoft.Azure.Management.Fluent.Azure
    .Configure()
    .Authenticate(credentials)
    .WithDefaultSubscription();
```
