---
ms.openlocfilehash: db70596552ffd699156e1b7a55cb1e944596f077
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75902001"
---
### <a name="data-protection-dataprotectionazurestorage-uses-new-azure-storage-apis"></a>Ochrona danych: DataProtection.AzureStorage korzysta z nowych interfejsów API usługi Azure Storage

<xref:Microsoft.AspNetCore.DataProtection.AzureStorage?displayProperty=fullName>zależy od [bibliotek usługi Azure Storage](https://github.com/Azure/azure-storage-net). Te biblioteki zmienili nazwy swoich zestawów, pakietów i przestrzeni nazw. Począwszy od ASP.NET Core `Microsoft.AspNetCore.DataProtection.AzureStorage` 3.0, używa nowych `Microsoft.Azure.Storage.`interfejsów API i pakietów z prefiksem.

W przypadku pytań dotyczących interfejsów <https://github.com/Azure/azure-storage-net>API usługi Azure Storage użyj . Aby uzyskać dyskusję na ten temat, zobacz [dotnet/aspnetcore#8472](https://github.com/dotnet/aspnetcore/issues/8472).

#### <a name="version-introduced"></a>Wprowadzona wersja

3.0

#### <a name="old-behavior"></a>Stare zachowanie

Pakiet odwołuje się `WindowsAzure.Storage` do pakietu NuGet.

#### <a name="new-behavior"></a>Nowe zachowanie

Pakiet odwołuje `Microsoft.Azure.Storage.Blob` się do pakietu NuGet.

#### <a name="reason-for-change"></a>Przyczyna zmiany

Ta zmiana `Microsoft.AspNetCore.DataProtection.AzureStorage` umożliwia migrację do zalecanych pakietów usługi Azure Storage.

#### <a name="recommended-action"></a>Zalecana akcja

Jeśli nadal musisz używać starszych interfejsów API usługi Azure Storage z ASP.NET Core 3.0, dodaj bezpośrednią zależność do pakietu [WindowsAzure.Storage.](https://www.nuget.org/packages/WindowsAzure.Storage/) Ten pakiet można zainstalować `Microsoft.Azure.Storage` obok nowych interfejsów API.

W wielu przypadkach uaktualnienie `using` polega tylko na zmianie instrukcji, aby użyć nowych obszarów nazw:

```diff
- using Microsoft.WindowsAzure.Storage;
- using Microsoft.WindowsAzure.Storage.Blob;
+ using Microsoft.Azure.Storage;
+ using Microsoft.Azure.Storage.Blob;
```

#### <a name="category"></a>Kategoria

ASP.NET Core

#### <a name="affected-apis"></a>Dotyczy interfejsów API

Brak

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
