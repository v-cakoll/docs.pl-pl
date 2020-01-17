---
ms.openlocfilehash: 9aff20e35469f9e786f0f790fda4ffaa04e76e64
ms.sourcegitcommit: ed3f926b6cdd372037bbcc214dc8f08a70366390
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/16/2020
ms.locfileid: "76116415"
---
### <a name="default-value-of-httprequestmessageversion-changed-to-11"></a>Wartość domyślna HttpRequestMessage. Version została zmieniona na 1,1

Wartość domyślna właściwości <xref:System.Net.Http.HttpRequestMessage.Version?displayProperty=fullName> została zmieniona z 2,0 na 1,1.

#### <a name="version-introduced"></a>Wprowadzona wersja

.NET Core 3.0

#### <a name="change-description"></a>Opis zmiany

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

-->
