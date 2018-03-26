---
title: 'Porady: inkrementacja i dekrementacja wskaźników (Przewodnik programowania w języku C#)'
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- pointers [C#], increment and decrement
- pointer expressions [C#], increment and decrement
ms.assetid: 1b8b9281-44ee-485a-9045-3db38a4b4b89
caps.latest.revision: ''
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 2c8efc6d0844d867ad6eebccf3bb22c03e6d5020
ms.sourcegitcommit: c883637b41ee028786edceece4fa872939d2e64c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/26/2018
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
