---
ms.openlocfilehash: 719f336e1b38597674d6ee8f0c5429dd965054b1
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/20/2020
ms.locfileid: "83721050"
---
### <a name="floating-point-formatting-and-parsing-behavior-changed"></a>Zmieniono formatowanie zmiennoprzecinkowe i zachowanie analizy

Sposób analizowania i formatowania liczby zmiennoprzecinkowej (według <xref:System.Double> <xref:System.Single> typów i) są teraz zgodne ze standardem IEEE.

#### <a name="change-description"></a>Zmień opis

W programie .NET Core 2,2 i starszych wersjach formatowanie z <xref:System.Double.ToString%2A?displayProperty=nameWithType> i i <xref:System.Single.ToString%2A?displayProperty=nameWithType> Analizowanie za pomocą <xref:System.Double.Parse%2A?displayProperty=nameWithType> ,, i <xref:System.Double.TryParse%2A?displayProperty=nameWithType> <xref:System.Single.Parse%2A?displayProperty=nameWithType> <xref:System.Single.TryParse%2A?displayProperty=nameWithType> nie jest zgodne ze standardem IEEE. W związku z tym nie jest możliwe zagwarantowanie, że wartość będzie w sposób roundtrip obsługiwany przy użyciu dowolnego obsługiwanego ciągu formatu standardowego lub niestandardowego. W przypadku niektórych danych wejściowych próba przeanalizowania sformatowanej wartości może zakończyć się niepowodzeniem, a dla innych, przeanalizowana wartość nie jest równa oryginalnej wartości.

Począwszy od platformy .NET Core 3,0, operacje analizowania i formatowania są zgodne ze standardem IEEE 754. Dzięki temu zachowanie typów zmiennoprzecinkowych w programie .NET pasuje do języków zgodnych ze standardem IEEE, takich jak C#. Aby uzyskać więcej informacji, zobacz Wprowadzenie do [analizy zmiennoprzecinkowej i ulepszenia formatowania w blogu platformy .NET Core 3,0](https://devblogs.microsoft.com/dotnet/floating-point-parsing-and-formatting-improvements-in-net-core-3-0/) .

#### <a name="version-introduced"></a>Wprowadzona wersja

3.0

#### <a name="recommended-action"></a>Zalecana akcja

Sekcja "potencjalny wpływ na istniejący kod" [w temacie analiza zmiennoprzecinkowa i ulepszenia formatowania w blogu programu .net core 3,0](https://devblogs.microsoft.com/dotnet/floating-point-parsing-and-formatting-improvements-in-net-core-3-0/) sugeruje zmiany w kodzie w przypadku zmiany zachowania w porównaniu do aplikacji platformy .net Core 2,2. obejmuje to użycie innego standardowego lub niestandardowego ciągu formatu w celu wymuszenia żądanego zachowania. Niektóre wyniki mogą nie mieć obejścia, jeśli były wcześniej nieprawidłowe.

#### <a name="category"></a>Kategoria

Podstawowe biblioteki platformy .NET

#### <a name="affected-apis"></a>Dotyczy interfejsów API

- <xref:System.Double.ToString%2A?displayProperty=nameWithType>
- <xref:System.Single.ToString%2A?displayProperty=nameWithType>
- <xref:System.Double.Parse%2A?displayProperty=nameWithType>
- <xref:System.Double.TryParse%2A?displayProperty=nameWithType>
- <xref:System.Single.Parse%2A?displayProperty=nameWithType>
- <xref:System.Single.TryParse%2A?displayProperty=nameWithType>

<!-- 

#### Affected APIs

- `Overload:System.Double.ToString`
- `Overload:System.Single.ToString`
- `Overload:System.Double.Parse`
- `Overload:System.Double.TryParse`
- `Overload:System.Single.Parse`
- `Overload:System.Single.TryParse`

-->
