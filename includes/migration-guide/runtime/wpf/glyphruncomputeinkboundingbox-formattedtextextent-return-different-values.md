---
ms.openlocfilehash: 059aa6f5885634b22b64d594563973f17fd2c4e7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61977365"
---
### <a name="glyphruncomputeinkboundingbox-and-formattedtextextent-return-different-values-beginning-in-net-framework-45"></a>GlyphRun.ComputeInkBoundingBox() i FormattedText.Extent zwracać różne wartości, począwszy od programu .NET Framework 4.5

|   |   |
|---|---|
|Szczegóły|Wprowadzono ulepszenia <xref:System.Windows.Media.GlyphRun.ComputeInkBoundingBox> i <xref:System.Windows.Media.FormattedText.Extent> w .NET Framework 4.5, aby rozwiązać problemy z, w których polach były zbyt mały dla zawartych symbole w niektórych przypadkach w .NET Framework 4.0. W wyniku tego niektóre obwiedni będzie większy począwszy od wersji programu .NET Framework 4.5, wynikiem drobne różnice w układzie interfejsu użytkownika.|
|Sugestia|Należy pamiętać, wzrósł przykładowe rozmiary symbol otaczający pole. Te zmiany zwykle zwiększa prezentacji i testowania trafień pola, ale w razie potrzeby starsze zachowanie (wstępne .NET 4.5) go może być wyrażania zgody na, dodając następujący wpis do pliku app.config:<pre><code class="lang-xml">&lt;appsettings&gt;&#13;&#10;&lt;add key=&quot;IncludeAllInkInBoundingBox&quot; value=&quot;false&quot;&gt;&#13;&#10;&lt;/appsettings&gt;&#13;&#10;</code></pre>|
|Zakres|Krawędź|
|Wersja|4.5|
|Typ|Środowisko uruchomieniowe|
|Dotyczy interfejsów API|<ul><li><xref:System.Windows.Media.GlyphRun.ComputeInkBoundingBox?displayProperty=nameWithType></li><li><xref:System.Windows.Media.FormattedText.Extent?displayProperty=nameWithType></li></ul>|
