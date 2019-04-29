---
title: Formatowanie tabeli wyników liczbowych - C# odwołania
ms.custom: seodec18
description: Dowiedz się więcej o języku C# standardowe ciągi formatujące liczby
ms.date: 09/20/2018
helpviewer_keywords:
- formatting [C#]
- numeric formatting [C#]
- String.Format method
ms.assetid: 120ba537-4448-4c62-8676-7a8fdd98f496
ms.openlocfilehash: 12fe89e3aa63e9d3d8c3f102fe5a01a5f2225375
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61661558"
---
# <a name="formatting-numeric-results-table-c-reference"></a>Formatowanie tabeli wyników liczbowych (odwołanie w C#)

W poniższej tabeli przedstawiono specyfikatory formatu obsługiwanych formatowania wyników liczbowych. Sformatowany wynik w ostatniej kolumnie odnosi się do "en US" <xref:System.Globalization.CultureInfo>.

|Specyfikator formatu|Opis|Przykłady|Wynik|  
|----------------------|-----------------|--------------|------------|  
|C lub c|Waluta|`string s = $"{2.5:C}";`<br /><br /> `string s = $"{-2.5:C}";`|$2.50<br /><br /> ($2.50)|  
|D lub d|Wartość dziesiętna|`string s = $"{25:D5}";`|00025|  
|E lub e|Wykładnicza|`string s = $"{250000:E2}";`|2.50E + 005|  
|F lub f|Wartość stałoprzecinkowa|`string s = $"{2.5:F2}";`<br /><br /> `string s = $"{2.5:F0}";`|2.50<br /><br /> 3|  
|G lub g|Ogólne|`string s = $"{2.5:G}";`|2.5|  
|N lub n|Numeric|`string s = $"{2500000:N}";`|2,500,000.00|  
|P lub p|Wartość procentowa|`string s = $"{0.25:P}";`|25.00%|  
|R lub r|Wartość dwustronna|`string s = $"{2.5:R}";`|2.5|  
|X lub x|Wartość szesnastkowa|`string s = $"{250:X}";`<br /><br /> `string s = $"{0xffff:X}";`|FA<br /><br /> FFFF|  

## <a name="remarks"></a>Uwagi

Specyfikator formatu umożliwia tworzenie ciągu formatu. Ciąg formatu ma następującą postać: `Axx`, gdzie

- `A` to specyfikator formatu, który określa typ sformatowane na wartość liczbową.
- `xx` jest Specyfikator dokładności, który wpływa na liczbę cyfr w sformatowane wyniki. Wartość zakresu Specyfikator dokładności, od 0 do 99.

Dziesiętnego ("D" lub "d") i formatu szesnastkowego ("X" lub "x") specyfikatory są obsługiwane tylko w przypadku typów całkowitych. Obustronne specyfikator formatu ("R" lub "r") jest obsługiwana tylko w przypadku <xref:System.Single>, <xref:System.Double>, i <xref:System.Numerics.BigInteger> typów.

Ciągi standardowego formatu liczb są obsługiwane przez:

- Niektóre przeciążenia `ToString` metoda wszystkich typów liczbowych. Na przykład można podać ciąg w formacie liczbowym do <xref:System.Int32.ToString%28System.String%29?displayProperty=nameWithType> i <xref:System.Int32.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType> metody.

- .NET [funkcję formatowania złożonego](../../../standard/base-types/composite-formatting.md), które są obsługiwane przez <xref:System.String.Format%2A?displayProperty=nameWithType> metody, na przykład.

- [Ciągi interpolowane](../tokens/interpolated.md).

Aby uzyskać więcej informacji, zobacz [Standard Numeric Format Strings](../../../standard/base-types/standard-numeric-format-strings.md).

## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka C#](../index.md)
- [Przewodnik programowania w języku C#](../../programming-guide/index.md)
- [Tabele odwołań dla typów](reference-tables-for-types.md)
- [Formatowanie tekstu](../../../standard/base-types/formatting-types.md)
- [Złożone formatowanie](../../../standard/base-types/composite-formatting.md)
- [Interpolacja ciągów](../tokens/interpolated.md)
- [string](string.md)
