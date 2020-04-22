---
ms.openlocfilehash: 22dbb1e982f83687a9e0eb288ed72c78c676db77
ms.sourcegitcommit: 348bb052d5cef109a61a3d5253faa5d7167d55ac
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2020
ms.locfileid: "82021592"
---
### <a name="floating-point-formatting-and-parsing-behavior-changed"></a>Zmieniono formatowanie zmiennoprzecinowe i analizowanie

Zmiennoprzecinające się parsowanie <xref:System.Double> i <xref:System.Single> formatowanie zachowanie (przez i typów) są teraz zgodne ze standardem IEEE.

#### <a name="change-description"></a>Zmień opis

W .NET Core 2.2 i wcześniejszych <xref:System.Double.ToString%2A?displayProperty=nameWithType> <xref:System.Single.ToString%2A?displayProperty=nameWithType>wersjach formatowanie <xref:System.Double.Parse%2A?displayProperty=nameWithType>z <xref:System.Double.TryParse%2A?displayProperty=nameWithType> <xref:System.Single.Parse%2A?displayProperty=nameWithType>i <xref:System.Single.TryParse%2A?displayProperty=nameWithType> , i analizowanie z , , i nie są zgodne ze standardem IEEE. W rezultacie nie można zagwarantować, że wartość będzie w obie strony z dowolnym obsługiwanym ciągiem w formacie standardowym lub niestandardowym. W przypadku niektórych danych wejściowych próba przeanalizowania sformatowanej wartości może zakończyć się niepowodzeniem, a w przypadku innych wartość analizowana nie jest równa wartości oryginalnej.

Począwszy od platformy .NET Core 3.0, operacje analizowania i formatowania są zgodne ze standardem IEEE 754. Gwarantuje to, że zachowanie typów zmiennoprzecinkowych w .NET odpowiada językom zgodnym z IEEE, takim jak C#. Aby uzyskać więcej informacji, zobacz [zmiennoprzecinające analizy i formatowanie ulepszenia w programie .NET Core 3.0](https://devblogs.microsoft.com/dotnet/floating-point-parsing-and-formatting-improvements-in-net-core-3-0/) wpis w blogu.

#### <a name="version-introduced"></a>Wprowadzono wersję

3.0

#### <a name="recommended-action"></a>Zalecana akcja

Sekcja "Potencjalny wpływ na istniejący kod" w sekcji [Analizowanie zmiennoprzecinkowe i formatowanie ulepszeń w blogu .NET Core 3.0](https://devblogs.microsoft.com/dotnet/floating-point-parsing-and-formatting-improvements-in-net-core-3-0/) sugeruje zmiany w kodzie, jeśli zauważysz zmianę zachowania w porównaniu do aplikacji .NET Core 2.2 Ogólnie rzecz biorąc, wiąże się to z użyciem innego ciągu standardowego lub niestandardowego formatu w celu wymuszenia żądanego zachowania. Niektóre wyniki mogą nie mieć obejścia, jeśli były wcześniej niepoprawne.

#### <a name="category"></a>Kategoria

Podstawowe biblioteki .NET

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
