---
title: In (modyfikator ogólny) (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.VarianceIn
helpviewer_keywords:
- contravariance, In keyword [Visual Basic]
- In keyword [Visual Basic]
ms.assetid: 59bb13c5-fe96-42b8-8286-86293d1661c5
ms.openlocfilehash: d1d9209cd583ac96ece59660ad29c76a66d3395a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="in-generic-modifier-visual-basic"></a>In (modyfikator ogólny) (Visual Basic)
Parametry typu ogólnego `In` — słowo kluczowe Określa, że parametr typu jest kontrawariantny.  
  
## <a name="remarks"></a>Uwagi  
 Kontrawariancja pozwala na użycie typu mniej pochodnego od określonej przez parametr ogólny. Dzięki temu niejawna konwersja klas implementujących interfejsów typu variant i niejawna konwersja typów delegatów.  
  
 Aby uzyskać więcej informacji, zobacz [Kowariancja i Kontrawariancja](../../programming-guide/concepts/covariance-contravariance/index.md).  
  
## <a name="rules"></a>Reguły  
 Można użyć `In` — słowo kluczowe w interfejsach i delegatów.  
  
 Parametr typu mogą być deklarowane kontrawariantnego w ogólny interfejs lub delegat, jeśli jest używany tylko jako typ argumentów metody i nie jest używany jako typ zwracany metody. `ByRef` Parametry nie mogą być kowariantnego lub kontrawariantnego.  
  
 Kowariancja i kontrawariancja są obsługiwane dla typów referencyjnych i nie jest obsługiwane dla typów wartości.  
  
 W języku Visual Basic nie można zadeklarować zdarzenia w interfejsach kontrawariantnego bez określania typu delegowanego. Ponadto kontrawariantnego interfejsów nie mogą mieć zagnieżdżonych klas, wyliczeń lub struktury, ale można mieć zagnieżdżonych interfejsów.  
  
## <a name="behavior"></a>Zachowanie  
 Interfejs, który ma parametr typu kontrawariantnego umożliwia jego metody akceptować argumenty mniej typów pochodnych niż określony przez parametr typu interfejsu. Na przykład ponieważ w .NET Framework 4 w <xref:System.Collections.Generic.IComparer%601> interfejsu, jest typu T kontrawariantny, można przypisać obiektu `IComparer(Of Person)` typu do obiektu `IComparer(Of Employee)` typu bez użycia żadnych metod konwersji specjalne `Person` dziedziczy `Employee`.  
  
 Delegat kontrawariantnego można przypisać inną delegata tego samego typu, ale mniej pochodnego parametr typu ogólnego.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak można zadeklarować, rozszerzać i implementować interfejs generyczny kontrawariantnego. Pokazuje też, jak skorzystać z niejawnej konwersji dla klas, które implementują ten interfejs.  
  
 [!code-vb[vbVarianceKeywords#1](../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/in-generic-modifier_1.vb)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak zadeklarować, wystąpienia i wywoływać kontrawariantnego Delegat ogólny. Pokazuje też, jak można niejawnie przekonwertować typu delegata.  
  
 [!code-vb[vbVarianceKeywords#2](../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/in-generic-modifier_2.vb)]  
  
## <a name="see-also"></a>Zobacz też  
 [Wariancje w interfejsach ogólnych](../../programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md)  
 [limit](../../../visual-basic/language-reference/modifiers/out-generic-modifier.md)
