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
# <a name="authenticate-with-the-azure-libraries-for-net"></a>Uwierzytelnij się za pomocą bibliotek platformy Azure dla platformy .NET

## <a name="connect-to-services-with-connection-strings"></a>Łączenie się z usługami przy użyciu parametrów połączenia

Większość bibliotek usług platformy Azure wymaga ciągu połączenia lub kluczy do uwierzytelniania. Na przykład baza danych SQL używa standardowego ciągu połączenia SQL:

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

Usługa Azure Storage używa klucza magazynu:

```csharp
string storageConnectionString = "DefaultEndpointsProtocol=https;"
        + "AccountName=" + storageName
        + ";AccountKey=" + storageKey
        + ";EndpointSuffix=core.windows.net";

var account = CloudStorageAccount.Parse(storageConnectionString);
// Do things with the account here...
```

Parametry połączenia usługi są używane w innych usługach platformy Azure, takich jak [CosmosDB](https://docs.microsoft.com/azure/cosmos-db/), [Azure Cache for Redis](https://docs.microsoft.com/azure/azure-cache-for-redis/cache-dotnet-how-to-use-azure-redis-cache)i [Service Bus](https://docs.microsoft.com/azure/service-bus-messaging/service-bus-dotnet-get-started-with-queues). Te ciągi można uzyskać przy użyciu witryny Azure portal, interfejsu wiersza polecenia lub programu PowerShell. Można również użyć bibliotek zarządzania platformy Azure dla platformy .NET do wykonywania zapytań o zasoby do tworzenia ciągów połączeń w kodzie.

Ten fragment kodu używa bibliotek zarządzania do utworzenia ciągu połączenia konta magazynu:

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

Inne biblioteki wymagają, aby aplikacja działała z [jednostką usługi](https://docs.microsoft.com/azure/active-directory/develop/active-directory-application-objects), która autoryzuje aplikację do działania z udzielonymi poświadczeniami. Ta konfiguracja jest podobna do kroków uwierzytelniania opartego na obiektach dla wymienionej poniżej biblioteki zarządzania.

## <a name="azure-management-libraries-for-net-authentication"></a><a name="mgmt-auth"></a>Biblioteki zarządzania platformy Azure dla uwierzytelniania .NET

[!include[Create service principal](../includes/create-sp.md)]

Teraz, gdy podmiot zabezpieczeń usługi jest tworzony, dwie opcje są dostępne do uwierzytelniania do jednostki usługi do tworzenia zasobów i zarządzania nimi.

Dla obu opcji należy dodać następujące pakiety NuGet do projektu.

```powershell
Install-Package Microsoft.Azure.Management.Fluent
Install-Package Microsoft.Azure.Management.ResourceManager.Fluent
```

### <a name="authenticate-with-token-credentials"></a>Uwierzytelnij się przy użyciu poświadczeń tokenu

Pierwszą metodą jest tworzenie obiektu poświadczeń tokenu w kodzie. Poświadczenia należy bezpiecznie przechowywać w pliku konfiguracji, rejestrze lub usłudze Azure KeyVault.

```csharp
var credentials = SdkContext.AzureCredentialsFactory
    .FromServicePrincipal(clientId,
    clientSecret,
    tenantId,
    AzureEnvironment.AzureGlobalCloud);
```

Użyj *clientId*, *clientSecret*i *tenantId* wartości z danych wyjściowych JSON podczas tworzenia jednostki usługi.

Następnie utwórz `Azure` obiekt punktu wejścia, aby rozpocząć pracę z interfejsem API:

```csharp
var azure = Microsoft.Azure.Management.Fluent.Azure
    .Configure()
    .Authenticate(credentials)
    .WithDefaultSubscription();
```

### <a name="file-based-authentication"></a><a name="mgmt-file"></a>Uwierzytelnianie oparte na plikach

Uwierzytelnianie oparte na plikach umożliwia umieszczenie poświadczeń jednostki usługi w pliku tekstowym i zabezpieczenie ich w systemie plików.

[!include[File-based authentication](../includes/file-based-auth.md)]

Przeczytaj zawartość pliku i utwórz `Azure` obiekt punktu wejścia, aby rozpocząć pracę z interfejsem API:

```csharp
// pull in the location of the authentication properties file from the environment
var credentials = SdkContext.AzureCredentialsFactory
    .FromFile(Environment.GetEnvironmentVariable("AZURE_AUTH_LOCATION"));

var azure = Microsoft.Azure.Management.Fluent.Azure
    .Configure()
    .Authenticate(credentials)
    .WithDefaultSubscription();
```
