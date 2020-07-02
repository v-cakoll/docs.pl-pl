---
ms.openlocfilehash: 00ffc782c9a15c0d88f797f52372b4658706b350
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620429"
---
### <a name="glyphruncomputeinkboundingbox-and-formattedtextextent-return-different-values-beginning-in-net-framework-45"></a>GlyphRun. ComputeInkBoundingBox () i FormattedText. zakres zwracają różne wartości zaczynające się na .NET Framework 4,5

#### <a name="details"></a>Szczegóły

Wprowadzono ulepszenia <xref:System.Windows.Media.GlyphRun.ComputeInkBoundingBox> i <xref:System.Windows.Media.FormattedText.Extent> w .NET Framework 4,5 do rozwiązywania problemów, gdy pola są zbyt małe dla zawartych symboli w niektórych przypadkach w .NET Framework 4,0. W wyniku tego niektóre pola ograniczające będą większe od początku .NET Framework 4,5, co spowodowało delikatne różnice w układzie interfejsu użytkownika.

#### <a name="suggestion"></a>Sugestia

Należy pamiętać, że niektóre rozmiary pól ograniczających glify zostały powiększone. Te zmiany zwykle ulepszają testowanie i pole trafień, ale jeśli jest wymagane zachowanie starsze (pre-.NET 4,5), można je dodać, dodając następujący wpis do pliku app.config:<pre><code class="lang-xml">&lt;appsettings&gt;&#13;&#10;&lt;add key=&quot;IncludeAllInkInBoundingBox&quot; value=&quot;false&quot;&gt;&#13;&#10;&lt;/appsettings&gt;&#13;&#10;</code></pre>

| Nazwa    | Wartość       |
|:--------|:------------|
| Zakres   |Brzeg|
|Wersja|4.5|
|Typ|Środowisko uruchomieniowe

#### <a name="affected-apis"></a>Dotyczy interfejsów API

-<xref:System.Windows.Media.GlyphRun.ComputeInkBoundingBox?displayProperty=nameWithType></li><li><xref:System.Windows.Media.FormattedText.Extent?displayProperty=nameWithType></li></ul>|
