---
title: "in (modyfikator ogólny) (odwołanie w C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- contravariance, in keyword [C#]
- in keyword [C#]
ms.assetid: 3a778c36-8aed-4ebe-aa8b-39f4057215b1
caps.latest.revision: "17"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 84773fca826b5a25679f1385a11c51b590ea20f2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="in-generic-modifier-c-reference"></a>in (modyfikator ogólny) (odwołanie w C#)
Parametry typu ogólnego `in` — słowo kluczowe Określa, że parametr typu jest kontrawariantny. Można użyć `in` — słowo kluczowe w interfejsach i delegatów.  
  
 Kontrawariancja pozwala na użycie typu mniej pochodnego od określonej przez parametr ogólny. Dzięki temu niejawna konwersja klas implementujących interfejsów typu variant i niejawna konwersja typów delegatów. Kowariancja i kontrawariancja w ogólnych parametrów typu są obsługiwane dla typów odwołań, ale nie są obsługiwane dla typów wartości.  
  
 Typem może być deklarowana kontrawariantnego w ogólnym interfejsem ani obiektem delegowanym, jeśli jest używany tylko jako typ argumentów metody i nie jest używany jako typ zwracany metody. `Ref`i `out` parametrów nie może być wariantem.  
  
 Interfejs, który ma parametr typu kontrawariantnego umożliwia jego metody akceptować argumenty mniej typów pochodnych niż określony przez parametr typu interfejsu. Na przykład ponieważ w .NET Framework 4 w <xref:System.Collections.Generic.IComparer%601> interfejsu, jest typu T kontrawariantny, można przypisać obiektu `IComparer(Of Person)` typu do obiektu `IComparer(Of Employee)` typu bez użycia żadnych metod konwersji specjalne `Employee` dziedziczy `Person`.  
  
 Delegat kontrawariantnego można przypisać inną delegata tego samego typu, ale mniej pochodnego parametr typu ogólnego.  
  
 Aby uzyskać więcej informacji, zobacz [Kowariancja i Kontrawariancja](../../programming-guide/concepts/covariance-contravariance/index.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak można zadeklarować, rozszerzać i implementować interfejs generyczny kontrawariantnego. Pokazuje też, jak skorzystać z niejawnej konwersji dla klas, które implementują ten interfejs.  
  
 [!code-csharp[csVarianceKeywords#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/in-generic-modifier_1.cs)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak zadeklarować, wystąpienia i wywoływać kontrawariantnego Delegat ogólny. Pokazuje też, jak można niejawnie przekonwertować typu delegata.  
  
 [!code-csharp[csVarianceKeywords#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/in-generic-modifier_2.cs)]  
  
## <a name="c-language-specification"></a>Specyfikacja języka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [limit](../../../csharp/language-reference/keywords/out-generic-modifier.md)  
 [Kowariancja i Kontrawariancja](../../programming-guide/concepts/covariance-contravariance/index.md)  
 [Modyfikatory](../../../csharp/language-reference/keywords/modifiers.md)
