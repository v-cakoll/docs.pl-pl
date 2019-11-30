---
ms.openlocfilehash: ff156afb3da4b921517fd841c5de2295265a8d7b
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/28/2019
ms.locfileid: "74567752"
---
### <a name="default-value-of-httprequestmessageversion-changed-to-11"></a>Wartość domyślna HttpRequestMessage. Version została zmieniona na 1,1

Wartość domyślna właściwości <xref:System.Net.Http.HttpRequestMessage.Version?displayProperty=fullName> została zmieniona z 2,0 na 1,1.

#### <a name="version-introduced"></a>Wprowadzona wersja

.NET Core 3.0

#### <a name="change-description"></a>Zmień opis

W przypadku platformy .NET Core 1,0 do 2,0 wartość domyślna właściwości <xref:System.Net.Http.HttpRequestMessage.Version?displayProperty=fullName> to 1,1. Począwszy od platformy .NET Core 2,1, zmieniono ją na 2,1.

Począwszy od platformy .NET Core 3,0, domyślny numer wersji zwracany przez właściwość <xref:System.Net.Http.HttpRequestMessage.Version?displayProperty=fullName> jest ponownie 1,1.

#### <a name="recommended-action"></a>Zalecane działanie

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

