---
title: 'Porady: inkrementacja i dekrementacja wskaźników - C# Programming Guide'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- pointers [C#], increment and decrement
- pointer expressions [C#], increment and decrement
ms.assetid: 1b8b9281-44ee-485a-9045-3db38a4b4b89
ms.openlocfilehash: 040437bc8cbab4ba12f243434bdea7798711ce8a
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65635160"
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
  
 [!code-csharp[csProgGuidePointers#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuidePointers/CS/Pointers2.cs#3)]  
  
 [!code-csharp[csProgGuidePointers#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuidePointers/CS/Pointers.cs#13)]  
  
**Wartości: 0 @ adres: 12860272**
**wartości: 1 @ adres: 12860276**
**wartość: 2 @ adres: 12860280**
**wartość: 3 @ adresu : 12860284**
**12860288 @ adres: wartość: 4**

## <a name="see-also"></a>Zobacz także

- [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)
- [Operatory języka C#](../../../csharp/language-reference/operators/index.md)
- [Manipulowanie wskaźnikami](../../../csharp/programming-guide/unsafe-code-pointers/how-to-increment-and-decrement-pointers.md)
- [Typy wskaźników](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)
- [Typy](../../../csharp/language-reference/keywords/types.md)
- [unsafe](../../../csharp/language-reference/keywords/unsafe.md)
- [fixed, instrukcja](../../../csharp/language-reference/keywords/fixed-statement.md)
- [stackalloc](../../../csharp/language-reference/keywords/stackalloc.md)
- [sizeof](../../../csharp/language-reference/keywords/sizeof.md)
