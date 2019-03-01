---
title: Porównanie wskaźników - C# przewodnik programowania
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- pointers [C#], comparison
ms.assetid: fcafd514-7405-4deb-8490-cc58efda5495
ms.openlocfilehash: 5185bd5e1686858452efcc7c89e2c1977e094386
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2019
ms.locfileid: "56969209"
---
# <a name="pointer-comparison-c-programming-guide"></a>Porównanie wskaźników (Przewodnik programowania w języku C#)
Można zastosować następujących operatorów porównywanie wskaźników dowolnego typu:  
  
 **==   !=   \<   >   \<=   >=**  
  
 Operatory porównania Porównaj adresy dwóch argumentów operacji, jak gdyby były liczb całkowitych bez znaku.  
  
## <a name="example"></a>Przykład  
 [!code-csharp[csProgGuidePointers#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuidePointers/CS/Pointers2.cs#16)]  
  
 [!code-csharp[csProgGuidePointers#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuidePointers/CS/Pointers.cs#17)]  
  
## <a name="sample-output"></a>Przykładowe dane wyjściowe  
 `True`  
  
 `False`  
  
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
