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
# <a name="authenticate-with-the-azure-sdk-for-net"></a>Uwierzytelnianie za pomocą zestawu Azure SDK dla platformy .NET

## <a name="recommended-azureidentity"></a>Zalecane: Azure. Identity

Najnowsze pakiety w zestawie Azure SDK dla platformy .NET używają wspólnego pakietu uwierzytelniania do uwierzytelniania `Azure.Identity` . Użycie `Azure.Identity` jest zalecane w porównaniu z innymi mechanizmami uwierzytelniania opisanymi w dalszej części tego dokumentu. Pakiety obsługujące poświadczenia dostarczone przez `Azure.Identity` program mają identyfikatory pakietów rozpoczynające się od *platformy Azure.* [Aby uzyskać więcej informacji, zobacz najnowsze wersje zestawu Azure SDK dla platformy .NET](https://azure.github.io/azure-sdk/releases/latest/index.html#net).

Aby uzyskać pełne instrukcje dotyczące korzystania `Azure.Identity` z programu w projekcie, zapoznaj się z dokumentacją [klienta tożsamości platformy Azure dla platformy .NET](/dotnet/api/overview/azure/identity-readme).

> [!TIP]
> Przykłady dotyczące korzystania z usługi Azure Identity do zarządzania zasobami platformy Azure i uzyskiwania do nich dostępu można znaleźć w temacie [tożsamość platformy Azure, zarządzanie zasobami i przykład magazynu](/samples/dotnet/samples/azure-identity-resource-management-storage/) .

Aby uwierzytelnić się w bibliotekach, które nie obsługują platformy Azure. tożsamość, zobacz pozostała część tego tematu.

## <a name="access-azure-resources"></a>Dostęp do zasobów platformy Azure

Aby można było korzystać z zasobów platformy Azure, takich jak pobieranie klucza tajnego z Key Vault lub przechowywanie obiektu BLOB w magazynie, wiele bibliotek usług platformy Azure wymaga parametrów połączenia lub kluczy do uwierzytelnienia. Na przykład SQL Database używa [standardowych parametrów połączenia SQL](https://docs.microsoft.com/azure/azure-sql/database/connect-query-dotnet-core). Parametry połączenia usługi są używane w innych usługach platformy Azure, takich jak [CosmosDB](/azure/cosmos-db/), [pamięć podręczna platformy Azure dla Redis](/azure/azure-cache-for-redis/cache-dotnet-how-to-use-azure-redis-cache)i [Service Bus](/azure/service-bus-messaging/service-bus-dotnet-get-started-with-queues). Te ciągi można pobrać przy użyciu Azure Portal, interfejsu wiersza polecenia lub programu PowerShell. Za pomocą bibliotek zarządzania platformy Azure dla platformy .NET można także wysyłać zapytania do zasobów w celu tworzenia parametrów połączenia w kodzie.

Metody używania parametrów połączenia różnią się w zależności od produktu. [Zapoznaj się z dokumentacją dotyczącą produktu platformy Azure](/azure/?product=featured).

## <a name="manage-azure-resources"></a>Zarządzanie zasobami platformy Azure

[!include[Create service principal](includes/create-sp.md)]

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

Następnie Utwórz obiekt punktu wejścia, `Azure` Aby rozpocząć pracę z interfejsem API:

```csharp
var azure = Microsoft.Azure.Management.Fluent.Azure
    .Configure()
    .Authenticate(credentials)
    .WithDefaultSubscription();
```

### <a name="file-based-authentication"></a><a name="mgmt-file"></a>Uwierzytelnianie oparte na plikach

Uwierzytelnianie oparte na plikach umożliwia umieszczenie poświadczeń jednostki usługi w zwykłym pliku tekstowym i zabezpieczenie go w systemie plików.

[!include[File-based authentication](includes/file-based-auth.md)]

Odczytaj zawartość pliku i Utwórz obiekt punktu wejścia, `Azure` Aby rozpocząć pracę z interfejsem API:

```csharp
// pull in the location of the authentication properties file from the environment
var credentials = SdkContext.AzureCredentialsFactory
    .FromFile(Environment.GetEnvironmentVariable("AZURE_AUTH_LOCATION"));

var azure = Microsoft.Azure.Management.Fluent.Azure
    .Configure()
    .Authenticate(credentials)
    .WithDefaultSubscription();
```
