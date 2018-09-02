---
title: Formatowanie tabeli wyników liczbowych (odwołanie w C#)
ms.date: 07/20/2015
helpviewer_keywords:
- formatting [C#]
- numeric formatting [C#]
- String.Format method
- Console.Write method
ms.assetid: 120ba537-4448-4c62-8676-7a8fdd98f496
ms.openlocfilehash: 8d034955d5d5d31788eafc0c21246451d7fd1f35
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2018
ms.locfileid: "43474297"
---
# <a name="formatting-numeric-results-table-c-reference"></a>Formatowanie tabeli wyników liczbowych (odwołanie w C#)
Wyników liczbowych można sformatować za pomocą <xref:System.String.Format%2A?displayProperty=nameWithType> metoda, za pomocą <xref:System.Console.Write%2A?displayProperty=nameWithType> lub <xref:System.Console.WriteLine%2A?displayProperty=nameWithType> metod, które wymagają `String.Format`, lub za pomocą [Interpolacja ciągów](../tokens/interpolated.md). Format jest określony za pomocą ciągów formatu. Poniższa tabela zawiera ciągi obsługiwany formatu standardowego. Ciąg formatu ma następującą postać: `Axx`, gdzie `A` jest specyfikatorem formatu i `xx` jest Specyfikator dokładności. Specyfikator formatu określa typ sformatowane wartości liczbowej, a Specyfikator dokładności określa liczbę cyfr znaczących lub miejsc dziesiętnych sformatowanych danych wyjściowych. Wartość zakresu Specyfikator dokładności, od 0 do 99.  
  
 Aby uzyskać więcej informacji na temat standardowych i niestandardowych ciągów formatowania, zobacz [typy formatowania](../../../standard/base-types/formatting-types.md).
  
|Specyfikator formatu|Opis|Przykłady|Dane wyjściowe|  
|----------------------|-----------------|--------------|------------|  
|C lub c|Waluta|Console.Write — ("{0:C}", 2.5);<br /><br /> Console.Write — ("{0:C}", -2,5);|$2.50<br /><br /> ($2.50)|  
|D lub d|Wartość dziesiętna|Console.Write — ("{0:D5}", 25);|00025|  
|E lub e|naukowe|Console.Write — ("{0:E}", rozmiar 250 000);|2.500000E+005|  
|F lub f|Wartość stałoprzecinkowa|Console.Write — ("{0:F2}", 25);<br /><br /> Console.Write — ("{0:F0}", 25);|25.00<br /><br /> 25|  
|G lub g|Ogólne|Console.Write — ("{0:G}", 2.5);|2.5|  
|N lub n|Wartość liczbowa|Console.Write — ("{0:N}", 2500000);|2,500,000.00|  
|X lub x|Wartość szesnastkowa|Console.Write — ("{0:X}", 250);<br /><br /> Console.Write — ("{0:X}", 0xffff);|FA<br /><br /> FFFF|  
  
## <a name="see-also"></a>Zobacz też

- [Dokumentacja języka C#](../../../csharp/language-reference/index.md)  
- [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
- [Standardowe ciągi formatujące liczby](../../../standard/base-types/standard-numeric-format-strings.md)  
- [Tabele odwołań dla typów](../../../csharp/language-reference/keywords/reference-tables-for-types.md)  
- [string](../../../csharp/language-reference/keywords/string.md)
