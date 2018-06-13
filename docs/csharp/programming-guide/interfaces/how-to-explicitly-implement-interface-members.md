---
title: 'Porady: jawne implementowanie elementów interfejsu (Przewodnik programowania w języku C#)'
ms.date: 07/20/2015
helpviewer_keywords:
- interfaces [C#], explicitly implementing
ms.assetid: 514cde76-f981-474e-8b40-9493619f899c
ms.openlocfilehash: 5f7ae6bae46cdf6596b206abbdeeb94b5c21a13f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33332189"
---
# <a name="how-to-explicitly-implement-interface-members-c-programming-guide"></a>Porady: jawne implementowanie elementów interfejsu (Przewodnik programowania w języku C#)
W tym przykładzie deklaruje [interfejsu](../../../csharp/language-reference/keywords/interface.md), `IDimensions`i klasę, `Box`, który implementuje jawnie elementy członkowskie interfejsu `getLength` i `getWidth`. Elementy członkowskie są dostępne za pośrednictwem wystąpienie interfejsu `dimensions`.  
  
## <a name="example"></a>Przykład  
 [!code-csharp[csProgGuideInheritance#8](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-explicitly-implement-interface-members_1.cs)]  
  
## <a name="robust-programming"></a>Niezawodne programowanie  
  
-   Należy zauważyć, że następujące wiersze w `Main` metoda są oznaczone jako komentarz, ponieważ będą one powodować błędy kompilacji. Nie można uzyskać dostępu do elementu członkowskiego interfejsu, który jest jawnie implementowane z [klasy](../../../csharp/language-reference/keywords/class.md) wystąpienie:  
  
     [!code-csharp[csProgGuideInheritance#45](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-explicitly-implement-interface-members_2.cs)]  
  
-   Też zwrócić uwagę, że następujące wiersze w `Main` metody pomyślnie wydruku wymiary pola, ponieważ te metody są wywoływane z wystąpienia interfejsu:  
  
     [!code-csharp[csProgGuideInheritance#46](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-explicitly-implement-interface-members_3.cs)]  
  
## <a name="see-also"></a>Zobacz też  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Klasy i struktury](../../../csharp/programming-guide/classes-and-structs/index.md)  
 [Interfejsy](../../../csharp/programming-guide/interfaces/index.md)  
 [Instrukcje: jawne implementowanie elementów dwóch interfejsów](../../../csharp/programming-guide/interfaces/how-to-explicitly-implement-members-of-two-interfaces.md)
