---
ms.openlocfilehash: ce4f09908b1025e8e5a0380c9bf035c6b0db479a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "74568166"
---
### <a name="floating-point-formatting-and-parsing-behavior-changed"></a>Zmieniono zachowanie formatowania i analizowania zmiennoprzecinkowego

Przeanalizowanie i formatowanie zmiennoprzecinkowych (według <xref:System.Double> typów) <xref:System.Single> są teraz zgodne ze standardem IEEE.

#### <a name="change-description"></a>Zmień opis

W .NET Core 2.2 i wcześniejszych <xref:System.Double.ToString%2A?displayProperty=nameWithType> wersjach formatowanie <xref:System.Single.ToString%2A?displayProperty=nameWithType>i <xref:System.Double.Parse%2A?displayProperty=nameWithType> <xref:System.Double.TryParse%2A?displayProperty=nameWithType>analizowanie z , , , <xref:System.Single.Parse%2A?displayProperty=nameWithType>i <xref:System.Single.TryParse%2A?displayProperty=nameWithType> nie są zgodne ze specyfikacją IEEE. W rezultacie nie można zagwarantować, że wartość będzie roundtrip z dowolnego obsługiwanego standardowego lub niestandardowego ciągu formatu. W przypadku niektórych danych wejściowych próba przeanalizowania sformatowanej wartości może zakończyć się niepowodzeniem, a dla innych wartość przeanalizowana nie jest równa wartości oryginalnej.

Począwszy od .NET Core 3.0, operacje analizy i formatowania są zgodne ze standardem IEEE 754. Gwarantuje to, że zachowanie typów zmiennoprzecinkowych w .NET jest zgodne z zachowaniem języków zgodnych ze specyfikacją IEEE, takich jak C#. Aby uzyskać więcej informacji, zobacz [ulepszenia analizy i formatowania zmiennoprzecinkowych w blogu .NET Core 3.0.](https://devblogs.microsoft.com/dotnet/floating-point-parsing-and-formatting-improvements-in-net-core-3-0/)

#### <a name="version-introduced"></a>Wprowadzona wersja

3.0

#### <a name="recommended-action"></a>Zalecana akcja

Sekcja "Potencjalny wpływ na istniejący kod" [ulepszeń analizy i formatowania zmiennoprzecinkowego w blogu .NET Core 3.0](https://devblogs.microsoft.com/dotnet/floating-point-parsing-and-formatting-improvements-in-net-core-3-0/) sugeruje zmiany w kodzie, jeśli obserwujesz zmianę zachowania w porównaniu z aplikacjami .NET Core 2.2 Ogólnie, wiąże się to z użyciem innego standardowego lub niestandardowego ciągu formatu w celu wymuszenia żądanego zachowania. Niektóre wyniki mogą nie mieć obejścia, jeśli były wcześniej niepoprawne.

#### <a name="category"></a>Kategoria

CoreFx

#### <a name="affected-apis"></a>Dotyczy interfejsów API

- <xref:System.Double.ToString%2A?displayProperty=nameWithType>
- <xref:System.Single.ToString%2A?displayProperty=nameWithType>
- <xref:System.Double.Parse%2A?displayProperty=nameWithType>
- <xref:System.Double.TryParse%2A?displayProperty=nameWithType>
- <xref:System.Single.Parse%2A?displayProperty=nameWithType>
- <xref:System.Single.TryParse%2A?displayProperty=nameWithType>

<!-- 

### Affected APIs

- `Overload:System.Double.ToString`
- `Overload:System.Single.ToString`
- `Overload:System.Double.Parse`
- `Overload:System.Double.TryParse`
- `Overload:System.Single.Parse`
- `Overload:System.Single.TryParse`

-->
