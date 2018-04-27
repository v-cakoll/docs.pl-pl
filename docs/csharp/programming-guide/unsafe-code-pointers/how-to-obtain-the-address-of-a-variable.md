---
title: 'Porady: uzyskiwanie adresu zmiennej (Przewodnik programowania w języku C#)'
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- variables [C#], address of
- pointers [C#], & operator
- pointer expressions [C#], address-of operator
ms.assetid: 44fe2cd9-a64f-4ef5-be2a-09ce807c0182
caps.latest.revision: 19
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 63a49490effb8b7d365492e8518b7558ec03a705
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-obtain-the-address-of-a-variable-c-programming-guide"></a>Porady: uzyskiwanie adresu zmiennej (Przewodnik programowania w języku C#)
Aby uzyskać adres wyrażenie jednoargumentowe, który ocenia do zmiennej stałej, użyj operator address-of `&`:  
  
```csharp  
int number;  
int* p = &number; //address-of operator &  
```  
  
 Operator address-of można zastosować tylko do zmiennej. Jeśli zmienna jest zmienną ruchome, możesz użyć [stałej instrukcji](../../../csharp/language-reference/keywords/fixed-statement.md) tymczasowo naprawić przed uzyskiwanie adresu zmiennej.  
  
 Jest obowiązek upewnij się, że zmienna jest zainicjowana. Kompilator nie wygeneruje komunikat o błędzie, jeśli zmienna nie jest zainicjowany.  
  
 Nie można pobrać adres stała lub wartość.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie wskaźnik do `int`, `p`i przypisanie adresu zmiennej całkowitą `number`. Zmienna `number` zainicjowano wyniku przypisanie do `*p`. Jeśli możesz przekształcić w komentarz tej instrukcji przypisania, inicjowanie zmiennej `number` zostanie usunięty, ale błąd kompilacji nie jest wystawiany.  

> [!NOTE]
> W tym przykładzie z kompilacji [ `-unsafe` ](../../language-reference/compiler-options/unsafe-compiler-option.md) — opcja kompilatora.
  
 [!code-csharp[address-of-a-variable](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuidePointers/CS/Pointers.cs#8)]  
  
## <a name="see-also"></a>Zobacz też  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Wyrażenia wskaźników](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md)  
 [Typy wskaźników](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)  
 [Typy](../../../csharp/language-reference/keywords/types.md)  
 [unsafe](../../../csharp/language-reference/keywords/unsafe.md)  
 [fixed, instrukcja](../../../csharp/language-reference/keywords/fixed-statement.md)  
 [stackalloc](../../../csharp/language-reference/keywords/stackalloc.md)
