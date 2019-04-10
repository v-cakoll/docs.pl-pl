---
ms.openlocfilehash: efe8a2dd98865f6a24b65ce0f08eb0c574b708f7
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59234440"
---
### <a name="currentculture-and-currentuiculture-flow-across-tasks"></a>CurrentCulture i CurrentUICulture przepływać przez zadania

|   |   |
|---|---|
|Szczegóły|Począwszy od programu .NET Framework 4.6 <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=name> i <xref:System.Globalization.CultureInfo.CurrentUICulture?displayProperty=name> są przechowywane w wątku <xref:System.Threading.ExecutionContext?displayProperty=name>, które odbywa się za pośrednictwem operacji asynchronicznych. Oznacza to, że zmiany <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=name> lub <xref:System.Globalization.CultureInfo.CurrentUICulture?displayProperty=name> zostaną odzwierciedlone w zadaniach, które później są uruchamiane asynchronicznie. To różni się od zachowania poprzedniej wersji programu .NET Framework (która może zresetować <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=name> i <xref:System.Globalization.CultureInfo.CurrentUICulture?displayProperty=name> we wszystkich zadaniach asynchronicznej).|
|Sugestia|Aplikacje, których obejmie ta zmiana może go obejść, jawnie ustawiając żądany <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=name> lub <xref:System.Globalization.CultureInfo.CurrentUICulture?displayProperty=name> jako pierwszej operacji na zadania asynchronicznego. Alternatywnie, stare zachowanie (nie przepływających <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=name> / <xref:System.Globalization.CultureInfo.CurrentUICulture?displayProperty=name>) może być wyrażania zgody na korzystanie przez ustawienie następujących przełącznika zgodności:<pre><code class="lang-csharp">AppContext.SetSwitch(&quot;Switch.System.Globalization.NoAsyncCurrentCulture&quot;, true);&#13;&#10;</code></pre>Ten problem został rozwiązany przez WPF w programie .NET Framework 4.6.2. Również został rozwiązany w platform .NET, 4.6, 4.6.1 za pośrednictwem [KB 3139549](https://support.microsoft.com/kb/3139549). Aplikacje przeznaczone dla .NET Framework 4.6 lub nowszy zostanie automatycznie pobrana właściwe zachowania w aplikacjach WPF — <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=name> / <xref:System.Globalization.CultureInfo.CurrentUICulture?displayProperty=name>) będą zachowywane przez operacje dyspozytora.|
|Zakres|Mały|
|Wersja|4.6|
|Typ|Przekierowanie|
|Dotyczy interfejsów API|<ul><li><xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=nameWithType></li><li><xref:System.Threading.Thread.CurrentCulture?displayProperty=nameWithType></li><li><xref:System.Globalization.CultureInfo.CurrentUICulture?displayProperty=nameWithType></li><li><xref:System.Threading.Thread.CurrentUICulture?displayProperty=nameWithType></li></ul>|
