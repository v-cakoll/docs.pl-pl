---
title: 'Porady: inkrementacja i dekrementacja wskaźników (Przewodnik programowania w języku C#)'
ms.date: 07/20/2015
helpviewer_keywords:
- pointers [C#], increment and decrement
- pointer expressions [C#], increment and decrement
ms.assetid: 1b8b9281-44ee-485a-9045-3db38a4b4b89
ms.openlocfilehash: 39cefc5dcebf1331a5e0ac0fadb8284e9041eb27
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2018
ms.locfileid: "44062523"
---
# <a name="how-to-increment-and-decrement-pointers-c-programming-guide"></a>Porady: inkrementacja i dekrementacja wskaźników (Przewodnik programowania w języku C#)
Użyj inkrementacji i dekrementacji, `++` i `--`, aby zmienić lokalizację wskaźnika przez [sizeof](../../../csharp/language-reference/keywords/sizeof.md) (`pointer-type`) dla wskaźnika typu wskaźnika — typ *. Inkrementacja i dekrementacja wyrażeń mieć następującą formę:  
  
```  
++p;  
p++;  
--p;  
p--;  
```  
  
 Operatory inkrementacji i dekrementacji może odnosić się do wskaźników dowolnego typu z wyjątkiem typu `void*`.  
  
 Efektem zastosowania operatora inkrementacyjnego do wskaźnika typu `pointer-type` jest dodanie [sizeof](../../../csharp/language-reference/keywords/sizeof.md) (`pointer-type`) adres, który znajduje się w zmiennej wskaźnika.  
  
 Efektem zastosowania operatora dekrementacyjnego do wskaźnika typu `pointer-type` ma Odejmij `sizeof` (`pointer-type`) z adresu, który znajduje się w zmiennej wskaźnika.  
  
 Żadne wyjątki są generowane, gdy domena wskaźnik przepełnienie w operacji, a wynik zależy od implementacji.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie krok po kroku przez tablicę przez zwiększenie wskaźnika przez rozmiar `int`. Z każdego kroku możesz wyświetlić adres i zawartość elementu tablicy.  
  
 [!code-csharp[csProgGuidePointers#3](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-increment-and-decrement-pointers_1.cs)]  
  
 [!code-csharp[csProgGuidePointers#13](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-increment-and-decrement-pointers_2.cs)]  
  
**Wartości: 0 @ adres: 12860272**
**wartości: 1 @ adres: 12860276**
**wartość: 2 @ adres: 12860280**
**wartość: 3 @ adresu : 12860284**
**12860288 @ adres: wartość: 4**

## <a name="see-also"></a>Zobacz też

- [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
- [Wyrażenia wskaźników](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md)  
- [Operatory języka C#](../../../csharp/language-reference/operators/index.md)  
- [Manipulowanie wskaźnikami](../../../csharp/programming-guide/unsafe-code-pointers/manipulating-pointers.md)  
- [Typy wskaźników](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)  
- [Typy](../../../csharp/language-reference/keywords/types.md)  
- [unsafe](../../../csharp/language-reference/keywords/unsafe.md)  
- [fixed, instrukcja](../../../csharp/language-reference/keywords/fixed-statement.md)  
- [stackalloc](../../../csharp/language-reference/keywords/stackalloc.md)
