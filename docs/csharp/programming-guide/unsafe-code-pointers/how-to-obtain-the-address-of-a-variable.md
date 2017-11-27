---
title: "Porady: uzyskiwanie adresu zmiennej (Przewodnik programowania w języku C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- variables [C#], address of
- pointers [C#], & operator
- pointer expressions [C#], address-of operator
ms.assetid: 44fe2cd9-a64f-4ef5-be2a-09ce807c0182
caps.latest.revision: "19"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 3d0969f7e62864c682660f08cd4198aa4032e0e2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-obtain-the-address-of-a-variable-c-programming-guide"></a>Porady: uzyskiwanie adresu zmiennej (Przewodnik programowania w języku C#)
Aby uzyskać adres wyrażenie jednoargumentowe, który ocenia do zmiennej stałej, użyj operator address-of:  
  
```  
int number;  
int* p = &number; //address-of operator &  
```  
  
 Operator address-of można zastosować tylko do zmiennej. Jeśli zmienna jest zmienną ruchome, możesz użyć [stałej instrukcji](../../../csharp/language-reference/keywords/fixed-statement.md) tymczasowo naprawić przed uzyskiwanie adresu zmiennej.  
  
 Jest obowiązek upewnij się, że zmienna jest zainicjowana. Kompilator nie będzie wystawiać komunikat o błędzie, jeśli zmienna nie jest zainicjowany.  
  
 Nie można pobrać adres stała lub wartość.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie wskaźnik do `int`, `p`i przypisanie adresu zmiennej całkowitą `number`. Zmienna `number` zainicjowano wyniku przypisanie do * p. Jeśli wprowadzeniu tej instrukcji przypisania komentarz, inicjowanie zmiennej `number` zostaną usunięte, ale błąd kompilacji nie jest wystawiany. Zwróć uwagę na [dostęp do elementu członkowskiego](../../../csharp/programming-guide/unsafe-code-pointers/how-to-access-a-member-with-a-pointer.md) operator `->` do wyświetlenia adres przechowywanych we wskaźniku.  
  
 [!code-csharp[csProgGuidePointers#7](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-obtain-the-address-of-a-variable_1.cs)]  
  
 [!code-csharp[csProgGuidePointers#8](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-obtain-the-address-of-a-variable_2.cs)]  
  
## <a name="see-also"></a>Zobacz też  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Wyrażenia wskaźników](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md)  
 [Typy wskaźnika](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)  
 [Typy](../../../csharp/language-reference/keywords/types.md)  
 [unsafe](../../../csharp/language-reference/keywords/unsafe.md)  
 [Fixed — instrukcja](../../../csharp/language-reference/keywords/fixed-statement.md)  
 [stackalloc](../../../csharp/language-reference/keywords/stackalloc.md)
