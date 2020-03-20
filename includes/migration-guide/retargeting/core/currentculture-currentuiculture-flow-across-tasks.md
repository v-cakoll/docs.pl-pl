---
ms.openlocfilehash: efe8a2dd98865f6a24b65ce0f08eb0c574b708f7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "67804597"
---
### <a name="currentculture-and-currentuiculture-flow-across-tasks"></a>CurrentCulture i CurrentUIkultura przepływu między zadaniami

|   |   |
|---|---|
|Szczegóły|Począwszy od .NET Framework 4.6 <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=name> i <xref:System.Globalization.CultureInfo.CurrentUICulture?displayProperty=name> są <xref:System.Threading.ExecutionContext?displayProperty=name>przechowywane w wątku , który przepływa przez operacje asynchroniczne. Oznacza to, <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=name> że <xref:System.Globalization.CultureInfo.CurrentUICulture?displayProperty=name> zmiany lub zostaną odzwierciedlone w zadaniach, które są później uruchamiane asynchronicznie. Różni się to od zachowania poprzednich wersji programu <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=name> .NET Framework (które można zresetować i <xref:System.Globalization.CultureInfo.CurrentUICulture?displayProperty=name> we wszystkich zadaniach asynchronicznych).|
|Sugestia|Aplikacje, których dotyczy ta zmiana, mogą obejść ją, jawnie ustawiając żądaną <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=name> lub <xref:System.Globalization.CultureInfo.CurrentUICulture?displayProperty=name> pierwszą operację w zadaniu asynchronicznego. Alternatywnie, stare zachowanie (nie <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=name> / <xref:System.Globalization.CultureInfo.CurrentUICulture?displayProperty=name>płynące) można wybrać, ustawiając następujący przełącznik zgodności:<pre><code class="lang-csharp">AppContext.SetSwitch(&quot;Switch.System.Globalization.NoAsyncCurrentCulture&quot;, true);&#13;&#10;</code></pre>Ten problem został rozwiązany przez WPF WPF w .NET Framework 4.6.2. Został on również naprawiony w .NET Frameworks 4.6, 4.6.1 do [KB 3139549](https://support.microsoft.com/kb/3139549). Aplikacje przeznaczone dla platformy .NET Framework 4.6 lub nowsze <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=name> / <xref:System.Globalization.CultureInfo.CurrentUICulture?displayProperty=name>automatycznie uzyskają odpowiednie zachowanie w aplikacjach WPF — ) zostaną zachowane w działaniach dyspozytora.|
|Zakres|Mały|
|Wersja|4.6|
|Typ|Przekierowanie|
|Dotyczy interfejsów API|<ul><li><xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=nameWithType></li><li><xref:System.Threading.Thread.CurrentCulture?displayProperty=nameWithType></li><li><xref:System.Globalization.CultureInfo.CurrentUICulture?displayProperty=nameWithType></li><li><xref:System.Threading.Thread.CurrentUICulture?displayProperty=nameWithType></li></ul>|
