---
title: 'Porady: inkrementacja i dekrementacja wskaźników (C# Programming Guide)'
ms.date: 07/20/2015
helpviewer_keywords:
- pointers [C#], increment and decrement
- pointer expressions [C#], increment and decrement
ms.assetid: 1b8b9281-44ee-485a-9045-3db38a4b4b89
ms.openlocfilehash: c75432d88a1e96742573a6e69a4e035066a387c4
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2018
ms.locfileid: "53128339"
---
# <a name="how-to-increment-and-decrement-pointers-c-programming-guide"></a>Porady: inkrementacja i dekrementacja wskaźników (C# Programming Guide)

Użyj inkrementacji i dekrementacji, `++` i `--`, aby zmienić lokalizację wskaźnika przez `sizeof(pointer-type)` wskaźnika typu `pointer-type*`. Inkrementacja i dekrementacja wyrażeń mieć następującą formę:  
  
```csharp
++p;  
p++;  
--p;  
p--;  
```  
  
 Operatory inkrementacji i dekrementacji może odnosić się do wskaźników dowolnego typu z wyjątkiem typu `void*`.  
  
 Efektem zastosowania operatora inkrementacyjnego do wskaźnika typu `pointer-type*` jest dodanie `sizeof(pointer-type)` adres, który znajduje się w zmiennej wskaźnika.  
  
 Efektem zastosowania operatora dekrementacyjnego do wskaźnika typu `pointer-type*` ma Odejmij `sizeof(pointer-type)` z adresu, który znajduje się w zmiennej wskaźnika.  
  
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

## <a name="see-also"></a>Zobacz także

- [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
- [Wyrażenia wskaźników](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md)  
- [Operatory języka C#](../../../csharp/language-reference/operators/index.md)  
- [Manipulowanie wskaźnikami](../../../csharp/programming-guide/unsafe-code-pointers/manipulating-pointers.md)  
- [Typy wskaźników](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)  
- [Typy](../../../csharp/language-reference/keywords/types.md)  
- [unsafe](../../../csharp/language-reference/keywords/unsafe.md)  
- [fixed, instrukcja](../../../csharp/language-reference/keywords/fixed-statement.md)  
- [stackalloc](../../../csharp/language-reference/keywords/stackalloc.md)
- [sizeof](../../../csharp/language-reference/keywords/sizeof.md)
