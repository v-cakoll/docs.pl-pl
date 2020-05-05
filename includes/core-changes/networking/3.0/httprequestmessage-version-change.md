---
ms.openlocfilehash: 5ad9c494fd02059e05cc744aad3b06cfc9399995
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "77451897"
---
### <a name="default-value-of-httprequestmessageversion-changed-to-11"></a>Wartość domyślna HttpRequestMessage. Version została zmieniona na 1,1

Wartość domyślna <xref:System.Net.Http.HttpRequestMessage.Version?displayProperty=fullName> właściwości została zmieniona z 2,0 na 1,1.

#### <a name="version-introduced"></a>Wprowadzona wersja

3.0

#### <a name="change-description"></a>Zmień opis

W przypadku platformy .NET Core 1,0 do 2,0 wartość domyślna <xref:System.Net.Http.HttpRequestMessage.Version?displayProperty=fullName> właściwości to 1,1. Począwszy od platformy .NET Core 2,1, zmieniono ją na 2,1.

Począwszy od platformy .NET Core 3,0, domyślny numer wersji zwracany przez <xref:System.Net.Http.HttpRequestMessage.Version?displayProperty=fullName> właściwość jest ponownie 1,1.

#### <a name="recommended-action"></a>Zalecana akcja

Zaktualizuj swój kod, jeśli zależy od <xref:System.Net.Http.HttpRequestMessage.Version?displayProperty=fullName> właściwości zwracającej wartość domyślną 2,0.

#### <a name="category"></a>Kategoria

Networking

#### <a name="affected-apis"></a>Dotyczy interfejsów API

- <xref:System.Net.Http.HttpRequestMessage.Version?displayProperty=fullName>

<!--

#### Affected APIs

- `P:System.Net.Http.HttpRequestMessage.Version`

-->
