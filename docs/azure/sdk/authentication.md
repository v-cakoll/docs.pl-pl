---
title: Uwierzytelnianie za pomocą bibliotek platformy Azure dla platformy .NET
description: Uwierzytelnianie w bibliotekach platformy Azure dla platformy .NET
ms.date: 08/22/2018
ms.custom: azure-sdk-dotnet
ms.openlocfilehash: f6af813cd1423be8784b769b272756b2c8258392
ms.sourcegitcommit: d9470d8b2278b33108332c05224d86049cb9484b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/17/2020
ms.locfileid: "82072152"
---
# <a name="authenticate-with-the-azure-libraries-for-net"></a>Uwierzytelnianie za pomocą bibliotek platformy Azure dla platformy .NET

## <a name="connect-to-services-with-connection-strings"></a>Łączenie się z usługami przy użyciu parametrów połączenia

Większość bibliotek usługi platformy Azure wymaga parametrów połączenia lub kluczy do uwierzytelnienia. Na przykład SQL Database używa standardowych parametrów połączenia SQL:

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

Parametry połączenia usługi są używane w innych usługach platformy Azure, takich jak [CosmosDB](https://docs.microsoft.com/azure/cosmos-db/), [pamięć podręczna platformy Azure dla Redis](https://docs.microsoft.com/azure/azure-cache-for-redis/cache-dotnet-how-to-use-azure-redis-cache)i [Service Bus](https://docs.microsoft.com/azure/service-bus-messaging/service-bus-dotnet-get-started-with-queues). Te ciągi można pobrać przy użyciu Azure Portal, interfejsu wiersza polecenia lub programu PowerShell. Za pomocą bibliotek zarządzania platformy Azure dla platformy .NET można także wysyłać zapytania do zasobów w celu tworzenia parametrów połączenia w kodzie.

Ten fragment kodu używa bibliotek zarządzania do tworzenia parametrów połączenia konta magazynu:

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

## <a name="azure-management-libraries-for-net-authentication"></a><a name="mgmt-auth"></a>Biblioteki zarządzania platformy Azure dla uwierzytelniania platformy .NET

[!include[Create service principal](../includes/create-sp.md)]

Po utworzeniu jednostki usługi dostępne są dwie opcje uwierzytelniania dla jednostki usługi w celu utworzenia zasobów i zarządzania nimi.

W przypadku obu opcji należy dodać następujące pakiety NuGet do projektu.

```powershell
Install-Package Microsoft.Azure.Management.Fluent
Install-Package Microsoft.Azure.Management.ResourceManager.Fluent
```

### <a name="authenticate-with-token-credentials"></a>Uwierzytelnianie przy użyciu poświadczeń tokenu

Pierwsza metoda polega na utworzeniu obiektu poświadczeń tokenu w kodzie. Poświadczenia powinny być bezpiecznie przechowywane w pliku konfiguracyjnym, rejestrze lub w magazynie kluczy platformy Azure.

```csharp
var credentials = SdkContext.AzureCredentialsFactory
    .FromServicePrincipal(clientId,
    clientSecret,
    tenantId,
    AzureEnvironment.AzureGlobalCloud);
```

Podczas tworzenia nazwy głównej usługi Użyj wartości *clientId*, *clientSecret*i *TENANTID* z danych wyjściowych JSON.

Następnie Utwórz obiekt punktu `Azure` wejścia, aby rozpocząć pracę z interfejsem API:

```csharp
var azure = Microsoft.Azure.Management.Fluent.Azure
    .Configure()
    .Authenticate(credentials)
    .WithDefaultSubscription();
```

### <a name="file-based-authentication"></a><a name="mgmt-file"></a>Uwierzytelnianie oparte na plikach

Uwierzytelnianie oparte na plikach umożliwia umieszczenie poświadczeń jednostki usługi w zwykłym pliku tekstowym i zabezpieczenie go w systemie plików.

[!include[File-based authentication](../includes/file-based-auth.md)]

Odczytaj zawartość pliku i Utwórz obiekt punktu `Azure` wejścia, aby rozpocząć pracę z interfejsem API:

```csharp
// pull in the location of the authentication properties file from the environment
var credentials = SdkContext.AzureCredentialsFactory
    .FromFile(Environment.GetEnvironmentVariable("AZURE_AUTH_LOCATION"));

var azure = Microsoft.Azure.Management.Fluent.Azure
    .Configure()
    .Authenticate(credentials)
    .WithDefaultSubscription();
```
