---
title: "Formatowanie tabeli wyników liczbowych (odwołanie w C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- formatting [C#]
- numeric formatting [C#]
- String.Format method
- Console.Write method
ms.assetid: 120ba537-4448-4c62-8676-7a8fdd98f496
caps.latest.revision: "14"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: cce14d5124ffdf030701ae0fc769278da51f86cc
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="formatting-numeric-results-table-c-reference"></a>Formatowanie tabeli wyników liczbowych (odwołanie w C#)
Można też wyników liczbowych za pomocą <xref:System.String.Format%2A?displayProperty=nameWithType> metody, lub za pomocą <xref:System.Console.Write%2A?displayProperty=nameWithType> lub <xref:System.Console.WriteLine%2A?displayProperty=nameWithType> metodę, która wywołuje `String.Format`. Format jest określona za pomocą ciągi formatów. Poniższa tabela zawiera obsługiwane standardowe ciągi formatujące. Ciąg formatu, który ma następującą postać: `Axx`, gdzie `A` jest specyfikator formatu i `xx` jest Specyfikator dokładności. Specyfikator formatu określa typ formatowanie zastosowane do wartości liczbowej i Specyfikator dokładności określa liczbę cyfr znaczących lub miejsc dziesiętnych sformatowanych danych wyjściowych. Wartość precyzji specyfikator w zakresie od 0 do 99.  
  
 Aby uzyskać więcej informacji na temat standardowe i niestandardowe ciągi formatowania, zobacz [typy formatowania](../../../standard/base-types/formatting-types.md). Aby uzyskać więcej informacji na temat `String.Format` metody, zobacz <xref:System.String.Format%2A?displayProperty=nameWithType>.  
  
|Specyfikator formatu|Opis|Przykłady|Dane wyjściowe|  
|----------------------|-----------------|--------------|------------|  
|C lub c|Waluta|Console.Write ("{0: c}", 2.5);<br /><br /> Console.Write ("{0: c}", -2,5);|$2.50<br /><br /> ($2.50)|  
|D lub d|Wartość dziesiętna|Console.Write ("{0:D5}", 25);|00025|  
|E lub e|Naukowe|Console.Write ("{0:E}", 250000);|2.500000E + 005|  
|F lub f|Wartość stałoprzecinkowa|Console.Write ("{0:F2}", 25);<br /><br /> Console.Write ("{0:F0}", 25);|25.00<br /><br /> 25|  
|G lub g|Ogólne|Console.Write ("{0: g}", 2.5);|2.5|  
|N lub n|Wartość liczbowa|Console.Write ("{0: n}", 2500000);|2,500,000.00|  
|X lub x|Wartość szesnastkowa|Console.Write ("{0: x}", 250);<br /><br /> Console.Write ("{0: x}", 0xffff);|FA<br /><br /> FFFF|  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie w C#](../../../csharp/language-reference/index.md)  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Standardowe ciągi formatujące liczby](../../../standard/base-types/standard-numeric-format-strings.md)  
 [Tabele odwołań dla typów](../../../csharp/language-reference/keywords/reference-tables-for-types.md)  
 [ciąg](../../../csharp/language-reference/keywords/string.md)
