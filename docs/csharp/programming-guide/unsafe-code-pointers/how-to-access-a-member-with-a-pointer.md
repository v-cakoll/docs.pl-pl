---
title: 'Porady: uzyskiwanie dostępu do członka za pomocą wskaźnika - C# Programming Guide'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- pointers [C#], member access
ms.assetid: 1e998498-8c85-4a78-8ce2-4d8c20f08342
ms.openlocfilehash: 5b2658611be559240c0cce5b30c35c015ff37d7a
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2019
ms.locfileid: "56978790"
---
# <a name="how-to-access-a-member-with-a-pointer-c-programming-guide"></a>Porady: uzyskiwanie dostępu do członka za pomocą wskaźnika (C# Programming Guide)
Do uzyskania dostępu do członka struktury, która jest zadeklarowana w niebezpiecznym kontekście, można używać operatora dostępu do elementu członkowskiego, jak pokazano w poniższym przykładzie, w którym `p` jest wskaźnikiem do [struktury](../../../csharp/language-reference/keywords/struct.md) zawierający element członkowski `x`.  
  
```  
CoOrds* p = &home;  
p -> x = 25; //member access operator ->  
```  
  
## <a name="example"></a>Przykład  
 W tym przykładzie [struktury](../../../csharp/language-reference/keywords/struct.md), `CoOrds`, zawierający dwie współrzędne `x` i `y` jest zadeklarowana i uruchomiony. Za pomocą operatora dostępu do elementu członkowskiego `->` i wskaźnik do wystąpienia `home`, `x` i `y` mają przypisane wartości.  
  
> [!NOTE]
>  Należy zauważyć, że wyrażenie `p->x` jest równoważne wyrażeniu `(*p).x`, i ten sam efekt można uzyskać przy użyciu jednej z dwóch wyrażeń.  
  
 [!code-csharp[csProgGuidePointers#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuidePointers/CS/Pointers2.cs#9)]  
  
 [!code-csharp[csProgGuidePointers#10](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-access-a-member-with-a-pointer_2.cs)]  
  
## <a name="see-also"></a>Zobacz także

- [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)
- [Wyrażenia wskaźników](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md)
- [Typy wskaźników](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)
- [Typy](../../../csharp/language-reference/keywords/types.md)
- [unsafe](../../../csharp/language-reference/keywords/unsafe.md)
- [fixed, instrukcja](../../../csharp/language-reference/keywords/fixed-statement.md)
- [stackalloc](../../../csharp/language-reference/keywords/stackalloc.md)
