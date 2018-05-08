---
title: in (modyfikator ogólny) (odwołanie w C#)
ms.date: 07/20/2015
helpviewer_keywords:
- contravariance, in keyword [C#]
- in keyword [C#]
ms.openlocfilehash: 003ce26fe9ba315eefc748a406754026231004b0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="in-generic-modifier-c-reference"></a>in (modyfikator ogólny) (odwołanie w C#)

Parametry typu ogólnego `in` — słowo kluczowe Określa, że parametr typu jest kontrawariantny. Można użyć `in` — słowo kluczowe w interfejsach i delegatów.  
  
 Kontrawariancja pozwala na użycie typu mniej pochodnego od określonej przez parametr ogólny. Dzięki temu niejawna konwersja klas implementujących interfejsów typu variant i niejawna konwersja typów delegatów. Kowariancja i kontrawariancja w ogólnych parametrów typu są obsługiwane dla typów odwołań, ale nie są obsługiwane dla typów wartości.  
  
 Typem może być deklarowana kontrawariantnego w ogólnym interfejsem ani obiektem delegowanym tylko wtedy, gdy definiuje typ parametrów metody, a nie typ zwracany metody. `In`, `ref`, i `out` parametry muszą być niezmienna, co oznacza ich nie należą do żadnej kowariantnego lub kontrawariantnego.
  
 Interfejs, który ma parametr typu kontrawariantnego umożliwia jego metody akceptować argumenty mniej typów pochodnych niż określony przez parametr typu interfejsu. Na przykład w <xref:System.Collections.Generic.IComparer%601> interfejsu, jest typu T kontrawariantny, można przypisać obiektu `IComparer<Person>` typu do obiektu `IComparer<Employee>` typu bez użycia żadnych metod konwersji specjalne `Employee` dziedziczy `Person`.  
  
 Delegat kontrawariantnego można przypisać inną delegata tego samego typu, ale mniej pochodnego parametr typu ogólnego.  
  
 Aby uzyskać więcej informacji, zobacz [Kowariancja i Kontrawariancja](../../programming-guide/concepts/covariance-contravariance/index.md).  
  
## <a name="contravariant-generic-interface"></a>Interfejs ogólny kontrawariantnego   

 Poniższy przykład pokazuje, jak można zadeklarować, rozszerzać i implementować interfejs generyczny kontrawariantnego. Pokazuje też, jak skorzystać z niejawnej konwersji dla klas, które implementują ten interfejs.  
  
 [!code-csharp[csVarianceKeywords#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/in-generic-modifier_1.cs)]  
  
## <a name="contravariant-generic-delegate"></a>Delegat ogólny kontrawariantnego  

 Poniższy przykład pokazuje, jak zadeklarować, wystąpienia i wywoływać kontrawariantnego Delegat ogólny. Pokazuje też, jak można niejawnie przekonwertować typu delegata.  
  
 [!code-csharp[csVarianceKeywords#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/in-generic-modifier_2.cs)]  
  
## <a name="c-language-specification"></a>Specyfikacja języka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [out](../../../csharp/language-reference/keywords/out-generic-modifier.md)  
 [Kowariancja i kontrawariancja](../../programming-guide/concepts/covariance-contravariance/index.md)  
 [Modyfikatory](../../../csharp/language-reference/keywords/modifiers.md)  
