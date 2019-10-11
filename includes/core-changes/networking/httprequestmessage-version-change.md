---
ms.openlocfilehash: b50a108d2efbfd3da0d690cb02537a12f766b26b
ms.sourcegitcommit: dfd612ba454ce775a766bcc6fe93bc1d43dfda47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/09/2019
ms.locfileid: "72237426"
---
### <a name="default-value-of-httprequestmessageversion-changed-to-11"></a>Wartość domyślna HttpRequestMessage. Version została zmieniona na 1,1 

Wartość domyślna właściwości <xref:System.Net.Http.HttpRequestMessage.Version?displayProperty=fullName> zmieniła się z od 2,0 do 1,1.

#### <a name="version-introduced"></a>Wprowadzona wersja

.NET Core 3,0

#### <a name="change-description"></a>Zmień opis

W przypadku platformy .NET Core 1,0 do 2,0 wartość domyślna właściwości <xref:System.Net.Http.HttpRequestMessage.Version?displayProperty=fullName> to 1,1. Począwszy od platformy .NET Core 2,1, zmieniono ją na 2,1. 

Począwszy od platformy .NET Core 3,0, domyślny numer wersji zwrócony przez właściwość <xref:System.Net.Http.HttpRequestMessage.Version?displayProperty=fullName> jest ponownie 1,1.
 
#### <a name="recommended-action"></a>Zalecana akcja

Zaktualizuj swój kod, jeśli zależy od właściwości <xref:System.Net.Http.HttpRequestMessage.Version?displayProperty=fullName> zwracającej wartość domyślną 2,0.

#### <a name="category"></a>Kategoria

Networking

#### <a name="affected-apis"></a>Narażone interfejsy API

- <xref:System.Net.Http.HttpRequestMessage.Version?displayProperty=fullName>

<!--
a def
### Affected APIs

- `P:System.Net.Http.HttpRequestMessage.Version`

-- >

