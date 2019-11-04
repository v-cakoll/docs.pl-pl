---
title: Formatowanie tabeli wyników liczbowych C# — odwołanie
ms.custom: seodec18
description: Więcej informacji C# na temat standardowych ciągów formatu liczbowego
ms.date: 09/20/2018
helpviewer_keywords:
- formatting [C#]
- numeric formatting [C#]
- String.Format method
ms.assetid: 120ba537-4448-4c62-8676-7a8fdd98f496
ms.openlocfilehash: 2cba5e704787ae6368b2543c985babf2fde3b4dd
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/01/2019
ms.locfileid: "73422754"
---
# <a name="formatting-numeric-results-table-c-reference"></a>Formatowanie tabeli wyników liczbowychC# (odwołanie)

W poniższej tabeli przedstawiono obsługiwane specyfikatory formatu do formatowania wyników liczbowych. Sformatowany wynik w ostatniej kolumnie odpowiada <xref:System.Globalization.CultureInfo>"pl-US".

|Specyfikator formatu|Opis|Przykłady|Wynik|  
|----------------------|-----------------|--------------|------------|  
|C lub c|Waluta|`string s = $"{2.5:C}";`<br /><br /> `string s = $"{-2.5:C}";`|$2,50<br /><br /> ($2,50)|  
|D lub d|Wartość dziesiętna|`string s = $"{25:D5}";`|00025|  
|E lub e|Wykładniczego|`string s = $"{250000:E2}";`|2.50 e + 005|  
|F lub f|Wartość stałoprzecinkowa|`string s = $"{2.5:F2}";`<br /><br /> `string s = $"{2.5:F0}";`|2,50<br /><br /> 3|  
|G lub g|Ogólne|`string s = $"{2.5:G}";`|2,5|  
|N lub n|przypada|`string s = $"{2500000:N}";`|2 500 000,00|  
|P lub p|Wartość procentowa|`string s = $"{0.25:P}";`|25,00%|  
|R lub r|Wartość dwustronna|`string s = $"{2.5:R}";`|2,5|  
|X lub x|Wartość szesnastkowa|`string s = $"{250:X}";`<br /><br /> `string s = $"{0xffff:X}";`|FA<br /><br /> FFFF|  

## <a name="remarks"></a>Uwagi

Użyj specyfikatora formatu, aby utworzyć ciąg formatu. Ciąg formatu ma następującą postać: `Axx`, gdzie

- `A` jest specyfikatorem formatu, który kontroluje typ formatowania zastosowanego do wartości liczbowej.
- `xx` jest specyfikatorem dokładności, który ma wpływ na liczbę cyfr w sformatowanym danych wyjściowych. Wartość specyfikatora dokładności mieści się w zakresie od 0 do 99.

Specyfikatory formatu dziesiętnego ("D" lub "d") i szesnastkowego ("X" lub "x") są obsługiwane tylko dla typów całkowitych. Specyfikator formatu rundy ("R" lub "r") jest obsługiwany tylko w przypadku typów <xref:System.Single>, <xref:System.Double>i <xref:System.Numerics.BigInteger>.

Ciągi standardowego formatu liczbowego są obsługiwane przez:

- Niektóre przeciążenia metody `ToString` wszystkich typów liczbowych. Na przykład można podać ciąg formatu liczbowego dla metod <xref:System.Int32.ToString%28System.String%29?displayProperty=nameWithType> i <xref:System.Int32.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType>.

- [Funkcja formatowania złożonego](../../../standard/base-types/composite-formatting.md)platformy .NET, obsługiwana przez metodę <xref:System.String.Format%2A?displayProperty=nameWithType>, na przykład.

- [Ciągi interpolowane](../tokens/interpolated.md).

Aby uzyskać więcej informacji, zobacz [Standardowe ciągi formatujące](../../../standard/base-types/standard-numeric-format-strings.md)liczby.

## <a name="see-also"></a>Zobacz także

- [C#Odwoła](../index.md)
- [Przewodnik programowania w języku C#](../../programming-guide/index.md)
- [Formatowanie typów](../../../standard/base-types/formatting-types.md)
- [Formatowanie złożone](../../../standard/base-types/composite-formatting.md)
- [Interpolacja ciągów](../tokens/interpolated.md)
- [string](../builtin-types/reference-types.md)
