---
title: "stackalloc (odwołanie w C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- stackalloc_CSharpKeyword
- stackalloc
helpviewer_keywords:
- stackalloc keyword [C#]
ms.assetid: adc04c28-3ed2-4326-807a-7545df92b852
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: ad4453f889a344fcd44dfad44a30fef07380b6a3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="stackalloc-c-reference"></a>stackalloc (odwołanie w C#)
`stackalloc` — Słowo kluczowe jest używane w kontekście niebezpieczny kod można przydzielić bloku pamięci na stosie.  
  
```  
int* block = stackalloc int[100];  
```  
  
## <a name="remarks"></a>Uwagi  
 Słowo kluczowe jest prawidłowy tylko w lokalnej zmiennej inicjatory. Poniższy kod powoduje, że błędy kompilatora.  
  
```  
int* block;  
// The following assignment statement causes compiler errors. You  
// can use stackalloc only when declaring and initializing a local   
// variable.  
block = stackalloc int[100];  
```  
  
 Ponieważ są związane z typów wskaźnika, `stackalloc` wymaga [niebezpieczne](../../../csharp/language-reference/keywords/unsafe.md) kontekstu. Aby uzyskać więcej informacji, zobacz [niebezpieczny kod i wskaźniki](../../../csharp/programming-guide/unsafe-code-pointers/index.md).  
  
 `stackalloc`przypomina [_alloca](/cpp/c-runtime-library/reference/alloca) biblioteki wykonawcze języka C.  
  
 Poniższy przykład oblicza i wyświetla najpierw 20 cyfr w sekwencji Fibonacci. Każdą liczbę to suma poprzednich dwóch liczb. W kodzie bloku pamięci wystarczający rozmiar ma 20 elementów typu `int` został przydzielony na stosie nie stosu. Adres bloku są przechowywane we wskaźniku `fib`. Ta pamięć nie podlega wyrzucanie elementów bezużytecznych i dlatego nie trzeba przypięty (przy użyciu [stałej](../../../csharp/language-reference/keywords/fixed-statement.md)). Okres istnienia blok pamięci jest ograniczona do istnienia metody, która definiuje ją. Nie można zwolnić pamięć, przed metoda zwraca.  
  
## <a name="example"></a>Przykład  
 [!code-csharp[csrefKeywordsOperator#15](../../../csharp/language-reference/keywords/codesnippet/CSharp/stackalloc_1.cs)]  
  
## <a name="security"></a>Zabezpieczenia  
 Niebezpieczny kod jest mniej bezpieczna niż bezpiecznych metod. Jednak użycie `stackalloc` automatycznie włączone funkcje wykrywania przepełnienie buforu w środowisku uruchomieniowym języka (wspólnego CLR). W przypadku wykrycia przepełnienie buforu, proces jest zakończony tak szybko jak to możliwe, aby zminimalizować ryzyko, że złośliwy kod jest wykonywany.  
  
## <a name="c-language-specification"></a>Specyfikacja języka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie w C#](../../../csharp/language-reference/index.md)  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Słowa kluczowe języka C#](../../../csharp/language-reference/keywords/index.md)  
 [Słowa kluczowe operatora](../../../csharp/language-reference/keywords/operator-keywords.md)  
 [Niebezpieczny kod i wskaźniki](../../../csharp/programming-guide/unsafe-code-pointers/index.md)
