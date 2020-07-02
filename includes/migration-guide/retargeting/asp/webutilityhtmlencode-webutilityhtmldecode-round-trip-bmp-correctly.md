---
ms.openlocfilehash: acb5b467fc8f0692d8fa1b3b8263fd27308cc124
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617168"
---
### <a name="webutilityhtmlencode-and-webutilityhtmldecode-round-trip-bmp-correctly"></a>Metody WebUtility.HtmlEncode i WebUtility.HtmlDecode wykonują rundę BMP poprawnie

#### <a name="details"></a>Szczegóły

W przypadku aplikacji, których platformą docelową jest program .NET Framework 4.5, znaki znajdujące się poza płaszczyzną Basic Multilingual Plane (BMP) wykonują rundę poprawnie, gdy są przekazywane do metod <xref:System.Net.WebUtility.HtmlDecode(System.String)>.

#### <a name="suggestion"></a>Sugestia

Ta zmiana nie powinna mieć żadnego wpływu na bieżące aplikacje, ale aby przywrócić oryginalne zachowanie, ustaw `targetFramework` atrybut `<httpRuntime>` elementu na ciąg inny niż "4,5". Można również ustawić atrybuty `unicodeEncodingConformance` i `unicodeDecodingConformance` elementu konfiguracji `<webUtility>`, aby sterować tym zachowaniem niezależnie od wersji docelowej programu .NET Framework.

| Nazwa    | Wartość       |
|:--------|:------------|
| Zakres   | Brzeg        |
| Wersja | 4.5         |
| Typ    | Przekierowanie |

#### <a name="affected-apis"></a>Dotyczy interfejsów API

- <xref:System.Net.WebUtility.HtmlEncode(System.String)?displayProperty=nameWithType>
- <xref:System.Net.WebUtility.HtmlEncode(System.String,System.IO.TextWriter)?displayProperty=nameWithType>
