---
title: 'Instrukcje: Jawne Implementowanie elementów interfejsu - C# przewodnik programowania'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- interfaces [C#], explicitly implementing
ms.assetid: 514cde76-f981-474e-8b40-9493619f899c
ms.openlocfilehash: 019b163a553760ea2868ead0b6af267dfdca278a
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2019
ms.locfileid: "56975540"
---
# <a name="how-to-explicitly-implement-interface-members-c-programming-guide"></a>Instrukcje: Jawne Implementowanie elementów interfejsu (C# Programming Guide)
W tym przykładzie deklaruje [interfejsu](../../../csharp/language-reference/keywords/interface.md), `IDimensions`i klasę, `Box`, który implementuje jawnie składowe interfejsu `getLength` i `getWidth`. Elementy członkowskie są dostępne za pośrednictwem wystąpienia interfejsu `dimensions`.  
  
## <a name="example"></a>Przykład  
 [!code-csharp[csProgGuideInheritance#8](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-explicitly-implement-interface-members_1.cs)]  
  
## <a name="robust-programming"></a>Niezawodne programowanie  
  
-   Należy zauważyć, że następujące wiersze w `Main` metody są oznaczone jako komentarz, ponieważ ich dałby w efekcie błędy kompilacji. Nie można uzyskać dostępu do składowej interfejsu, który jest jawnie implementowane z [klasy](../../../csharp/language-reference/keywords/class.md) wystąpienie:  
  
     [!code-csharp[csProgGuideInheritance#45](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#45)]  
  
-   Zauważ również, że następujące wiersze w `Main` metoda pomyślnie drukowania wymiary pola, ponieważ z wystąpienia interfejsu wywoływane są metody:  
  
     [!code-csharp[csProgGuideInheritance#46](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#46)]  
  
## <a name="see-also"></a>Zobacz także

- [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)
- [Klasy i struktury](../../../csharp/programming-guide/classes-and-structs/index.md)
- [Interfejsy](../../../csharp/programming-guide/interfaces/index.md)
- [Instrukcje: Jawne Implementowanie elementów dwóch interfejsów](../../../csharp/programming-guide/interfaces/how-to-explicitly-implement-members-of-two-interfaces.md)
