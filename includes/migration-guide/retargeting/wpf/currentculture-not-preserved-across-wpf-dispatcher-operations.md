---
ms.openlocfilehash: bd656478a55856e676853e57f3e7386ea0aa0211
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614824"
---
### <a name="currentculture-is-not-preserved-across-wpf-dispatcher-operations"></a>CurrentCulture nie jest zachowywana w operacjach dyspozytora WPF

#### <a name="details"></a>Szczegóły

Począwszy od .NET Framework 4,6 zmiany <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=fullName> lub <xref:System.Globalization.CultureInfo.CurrentUICulture?displayProperty=fullName> wprowadzone w ramach elementu <xref:System.Windows.Threading.Dispatcher?displayProperty=fullName> zostaną utracone po zakończeniu operacji dyspozytora. Podobnie zmiany <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=fullName> lub <xref:System.Globalization.CultureInfo.CurrentUICulture?displayProperty=fullName> wprowadzone poza operacją dyspozytora mogą nie być odzwierciedlone podczas wykonywania tej operacji. Praktycznie mówiąc, oznacza to, <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=fullName> że <xref:System.Globalization.CultureInfo.CurrentUICulture?displayProperty=fullName> zmiany nie mogą przepływać między wywołaniami ZWROTNYMI interfejsu użytkownika WPF a innym kodem w aplikacji WPF. Jest to spowodowane zmianą w <xref:System.Threading.ExecutionContext?displayProperty=fullName> tej przyczynie <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=fullName> i w <xref:System.Globalization.CultureInfo.CurrentUICulture?displayProperty=fullName> kontekście wykonywania rozpoczynającą się od aplikacji przeznaczonych dla .NET Framework 4,6. Operacje dyspozytora WPF przechowują kontekst wykonywania używany do rozpoczęcia operacji i przywracania poprzedniego kontekstu po zakończeniu operacji. Ponieważ <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=fullName> i <xref:System.Globalization.CultureInfo.CurrentUICulture?displayProperty=fullName> są teraz częścią tego kontekstu, zmiany w nich w ramach operacji dyspozytora nie są utrwalane poza operacją.

#### <a name="suggestion"></a>Sugestia

Aplikacje, których dotyczy ta zmiana, mogą obsłużyć tę zmianę, przechowując odpowiednie <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=fullName> lub <xref:System.Globalization.CultureInfo.CurrentUICulture?displayProperty=fullName> w polu i sprawdzając wszystkie jednostki operacji dyspozytora (w tym programy obsługi wywołania zwrotnego zdarzeń interfejsu użytkownika), które <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=fullName> są poprawne i <xref:System.Globalization.CultureInfo.CurrentUICulture?displayProperty=fullName> są ustawione. Alternatywnie, ze względu na to, że zmiana kontekście wykonywaniaa podstawowa dla tej platformy WPF wpływa tylko na aplikacje przeznaczone dla .NET Framework 4,6 lub nowszej, ten przerwanie można uniknąć, przeznaczenie do .NET Framework 4.5.2. aplikacje, które są przeznaczone dla .NET Framework 4,6 lub nowszego, mogą także obejść ten krok, ustawiając następujący przełącznik zgodności:

<pre><code class="lang-csharp">AppContext.SetSwitch(&quot;Switch.System.Globalization.NoAsyncCurrentCulture&quot;, true);&#13;&#10;</code></pre>

Ten problem został rozwiązany przez WPF w .NET Framework 4.6.2. Został również ustalony w programie .NET Frameworks 4,6, 4.6.1 do [KB 3139549](https://support.microsoft.com/kb/3139549). Aplikacje ukierunkowane na .NET Framework 4,6 lub nowsze automatycznie otrzymają odpowiednie zachowanie w aplikacjach WPF — <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=fullName> / <xref:System.Globalization.CultureInfo.CurrentUICulture?displayProperty=fullName> ) byłyby zachowywane między operacjami dyspozytora.

| Nazwa    | Wartość       |
|:--------|:------------|
| Zakres   | Mały       |
| Wersja | 4.6         |
| Typ    | Przekierowanie |
