---
ms.openlocfilehash: ff156afb3da4b921517fd841c5de2295265a8d7b
ms.sourcegitcommit: 5a28f8eb071fcc09b045b0c4ae4b96898673192e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2019
ms.locfileid: "73198518"
---
### <a name="default-value-of-httprequestmessageversion-changed-to-11"></a>Wartość domyślna HttpRequestMessage. Version została zmieniona na 1,1

Wartość domyślna właściwości <xref:System.Net.Http.HttpRequestMessage.Version?displayProperty=fullName> zmieniła się z od 2,0 do 1,1.

#### <a name="version-introduced"></a>Wprowadzona wersja

.NET Core 3.0

#### <a name="change-description"></a>Zmień opis

W przypadku platformy .NET Core 1,0 do 2,0 wartość domyślna właściwości <xref:System.Net.Http.HttpRequestMessage.Version?displayProperty=fullName> to 1,1. Począwszy od platformy .NET Core 2,1, zmieniono ją na 2,1.

Począwszy od platformy .NET Core 3,0, domyślny numer wersji zwrócony przez właściwość <xref:System.Net.Http.HttpRequestMessage.Version?displayProperty=fullName> jest ponownie 1,1.

#### <a name="recommended-action"></a>Zalecana akcja

Zaktualizuj swój kod, jeśli zależy od właściwości <xref:System.Net.Http.HttpRequestMessage.Version?displayProperty=fullName> zwracającej wartość domyślną 2,0.

#### <a name="category"></a>Kategoria

Obsługa sieci

#### <a name="affected-apis"></a>Dotyczy interfejsów API

- <xref:System.Net.Http.HttpRequestMessage.Version?displayProperty=fullName>

<!--
a def
### Affected APIs

- `P:System.Net.Http.HttpRequestMessage.Version`

-- >

