---
title: 'Porady: inkrementacja i dekrementacja wskaźników (Przewodnik programowania w języku C#)'
ms.date: 07/20/2015
helpviewer_keywords:
- pointers [C#], increment and decrement
- pointer expressions [C#], increment and decrement
ms.assetid: 1b8b9281-44ee-485a-9045-3db38a4b4b89
ms.openlocfilehash: e1c3ac12a126450781d0ce78e788f39c740b5279
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-increment-and-decrement-pointers-c-programming-guide"></a>Porady: inkrementacja i dekrementacja wskaźników (Przewodnik programowania w języku C#)
Użyj inkrementacji i dekrementacji, `++` i `--`, aby zmienić lokalizację wskaźnika przez [sizeof](../../../csharp/language-reference/keywords/sizeof.md) (`pointer-type`) dla wskaźnika typu wskaźnika — typ *. Inkrementacja i dekrementacja wyrażeń mieć następującą formę:  
  
```  
++p;  
p++;  
--p;  
p--;  
```  
  
 Operatory inkrementacji i dekrementacji można zastosować do wskaźników dowolnego typu, z wyjątkiem typu `void*`.  
  
 Efekt zastosowania operatora inkrementacji do wskaźnika typu `pointer-type` jest dodanie [sizeof](../../../csharp/language-reference/keywords/sizeof.md) (`pointer-type`) adres, który jest zawarty w zmiennej wskaźnikowej.  
  
 Skutek stosowania operator dekrementacji do wskaźnika typu `pointer-type` jest do odjęcia `sizeof` (`pointer-type`) z adresu, który jest zawarty w zmiennej wskaźnikowej.  
  
 Żadne wyjątki są generowane, gdy domeny wskaźnika przepełnienie w operacji, a wynik zależy od implementacji.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie można wykonywać krokowo tablicy przez zwiększanie wskaźnika przez rozmiar `int`. Z każdym kroku możesz wyświetlić adres i zawartość elementu tablicy.  
  
 [!code-csharp[csProgGuidePointers#3](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-increment-and-decrement-pointers_1.cs)]  
  
 [!code-csharp[csProgGuidePointers#13](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-increment-and-decrement-pointers_2.cs)]  
  
 **Wartości: 0 @ adres: 12860272**  
**Wartości: 1 @ adres: 12860276**  
**Wartość: 2 @ adres: 12860280**  
**Wartość: 3 @ adres: 12860284**  
**Wartość: 4 @ adres: 12860288**   
## <a name="see-also"></a>Zobacz też  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Wyrażenia wskaźników](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md)  
 [Operatory języka C#](../../../csharp/language-reference/operators/index.md)  
 [Manipulowanie wskaźnikami](../../../csharp/programming-guide/unsafe-code-pointers/manipulating-pointers.md)  
 [Typy wskaźników](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)  
 [Typy](../../../csharp/language-reference/keywords/types.md)  
 [unsafe](../../../csharp/language-reference/keywords/unsafe.md)  
 [fixed, instrukcja](../../../csharp/language-reference/keywords/fixed-statement.md)  
 [stackalloc](../../../csharp/language-reference/keywords/stackalloc.md)
