---
ms.openlocfilehash: 78d2ec6fb505573ad36d55a9ca0a20452b7fa244
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/07/2019
ms.locfileid: "72002851"
---
### <a name="default-value-of-httprequestmessageversion-changed-to-11"></a>Wartość domyślna HttpRequestMessage. Version została zmieniona na 1,1 

Wartość domyślna właściwości <xref:System.Net.Http.HttpRequestMessage.Version?displayProperty=fullName> zmieniła się z od 2,0 do 1,1.

#### <a name="version-introduced"></a>Wprowadzona wersja

.NET Core 3.0

#### <a name="details"></a>Szczegóły

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

