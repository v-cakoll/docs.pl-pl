---
ms.openlocfilehash: ca662b57fae9b1d0d41290f3052f71bca66e9bf3
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59774469"
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
