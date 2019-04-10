---
ms.openlocfilehash: ca662b57fae9b1d0d41290f3052f71bca66e9bf3
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59234842"
---
### <a name="webutilityhtmlencode-and-webutilityhtmldecode-round-trip-bmp-correctly"></a>Metody WebUtility.HtmlEncode i WebUtility.HtmlDecode wykonują rundę BMP poprawnie

|   |   |
|---|---|
|Szczegóły|W przypadku aplikacji, których platformą docelową jest program .NET Framework 4.5, znaki znajdujące się poza płaszczyzną Basic Multilingual Plane (BMP) wykonują rundę poprawnie, gdy są przekazywane do metod <xref:System.Net.WebUtility.HtmlDecode(System.String)>.|
|Sugestia|Ta zmiana nie powinna mieć żadnego wpływu na bieżące aplikacje, ale aby przywrócić oryginalne zachowanie, ustaw atrybut <code>targetFramework</code> elementu <code>&lt;httpRuntime&gt;</code> na ciąg znaków inny niż &quot;4.5&quot;. Można również ustawić atrybuty <code>unicodeEncodingConformance</code> i <code>unicodeDecodingConformance</code> elementu konfiguracji <code>&lt;webUtility&gt;</code>, aby sterować tym zachowaniem niezależnie od wersji docelowej programu .NET Framework.|
|Zakres|Krawędź|
|Wersja|4.5|
|Typ|Przekierowanie|
|Dotyczy interfejsów API|<ul><li><xref:System.Net.WebUtility.HtmlEncode(System.String)?displayProperty=nameWithType></li><li><xref:System.Net.WebUtility.HtmlEncode(System.String,System.IO.TextWriter)?displayProperty=nameWithType></li></ul>|
