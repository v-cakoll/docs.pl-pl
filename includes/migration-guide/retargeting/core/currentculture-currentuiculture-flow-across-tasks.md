---
ms.openlocfilehash: 78faa5f4008b41bac75c94ce09a58c8227e5b485
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614670"
---
### <a name="currentculture-and-currentuiculture-flow-across-tasks"></a>Przepływy CurrentCulture i CurrentUICulture między zadaniami

#### <a name="details"></a>Szczegóły

Począwszy od .NET Framework 4,6 <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=fullName> i <xref:System.Globalization.CultureInfo.CurrentUICulture?displayProperty=fullName> są przechowywane w wątku <xref:System.Threading.ExecutionContext?displayProperty=fullName> , który przepływa przez operacje asynchroniczne. Oznacza to, że zmiany w <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=fullName> lub <xref:System.Globalization.CultureInfo.CurrentUICulture?displayProperty=fullName> zostaną odzwierciedlone w zadaniach, które są później uruchamiane asynchronicznie. Różni się to od zachowania poprzednich wersji .NET Framework (które zostałyby zresetowane <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=fullName> i <xref:System.Globalization.CultureInfo.CurrentUICulture?displayProperty=fullName> we wszystkich zadaniach asynchronicznych).

#### <a name="suggestion"></a>Sugestia

Aplikacje, których dotyczy ta zmiana, mogą obejść je przez jawne ustawienie żądanej <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=fullName> lub <xref:System.Globalization.CultureInfo.CurrentUICulture?displayProperty=fullName> pierwszej operacji w zadaniu asynchronicznym. Alternatywnie, stare zachowanie (nieprzepływności <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=fullName> / <xref:System.Globalization.CultureInfo.CurrentUICulture?displayProperty=fullName> ) może być włączane przez ustawienie następującego przełącznika zgodności:

```csharp
AppContext.SetSwitch("Switch.System.Globalization.NoAsyncCurrentCulture", true);
```

Ten problem został rozwiązany przez WPF w .NET Framework 4.6.2. Został również ustalony w programie .NET Frameworks 4,6, 4.6.1 do [KB 3139549](https://support.microsoft.com/kb/3139549). Aplikacje ukierunkowane na .NET Framework 4,6 lub nowsze automatycznie otrzymają odpowiednie zachowanie w aplikacjach WPF — <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=fullName> / <xref:System.Globalization.CultureInfo.CurrentUICulture?displayProperty=fullName> ) byłyby zachowywane między operacjami dyspozytora.

| Nazwa    | Wartość       |
|:--------|:------------|
| Zakres   | Mały       |
| Wersja | 4.6         |
| Typ    | Przekierowanie |

#### <a name="affected-apis"></a>Dotyczy interfejsów API

- <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=nameWithType>
- <xref:System.Threading.Thread.CurrentCulture?displayProperty=nameWithType>
- <xref:System.Globalization.CultureInfo.CurrentUICulture?displayProperty=nameWithType>
- <xref:System.Threading.Thread.CurrentUICulture?displayProperty=nameWithType>
