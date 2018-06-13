---
title: Out (modyfikator ogólny) (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.VarianceOut
helpviewer_keywords:
- Out keyword [Visual Basic]
- covariance, Out keyword [Visual Basic]
ms.assetid: c4418369-1518-4a46-9a1e-054c61038eca
ms.openlocfilehash: 7ba774bfcd629a7518602d4b971e86a690b2dd83
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33598156"
---
# <a name="out-generic-modifier-visual-basic"></a>Out (modyfikator ogólny) (Visual Basic)
Parametry typu ogólnego `Out` — słowo kluczowe Określa, że typ jest kowariantny.  
  
## <a name="remarks"></a>Uwagi  
 Kowariancja pozwala na użycie typu bardziej pochodnego od określonej przez parametr ogólny. Dzięki temu niejawna konwersja klas implementujących interfejsów typu variant i niejawna konwersja typów delegatów.  
  
 Aby uzyskać więcej informacji, zobacz [Kowariancja i Kontrawariancja](../../programming-guide/concepts/covariance-contravariance/index.md).  
  
## <a name="rules"></a>Reguły  
 Można użyć `Out` — słowo kluczowe w interfejsach i delegatów.  
  
 W interfejsie ogólny parametru typu mogą być deklarowane jako kowariantnego, spełnia następujące warunki:  
  
-   Parametr typu jest używany tylko jako typ zwracany metody interfejsu i nie jest używany jako typ argumentów metody.  
  
    > [!NOTE]
    >  Istnieje jeden wyjątek od tej reguły. Jeśli w interfejsie kowariantnego to delegat generyczny kontrawariantnego jako parametr metody, można użyć typu kowariantnego jako parametr typu ogólnego dla tego obiektu delegowanego. Aby uzyskać więcej informacji na temat kowariantnego i kontrawariantnego delegatów, zobacz [wariancji w Delegatach](../../programming-guide/concepts/covariance-contravariance/variance-in-delegates.md) i [przy użyciu wariancję Func i delegatów akcji](../../programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md).  
  
-   Parametr typu nie jest używany jako ogólne ograniczenia dla metod interfejsu.  
  
 Delegat ogólny parametru typu mogą być deklarowane kowariantnego Jeśli jest używany tylko jako typ zwracany metody i nie są używane dla argumentów metody.  
  
 Kowariancja i kontrawariancja są obsługiwane dla typów odwołań, ale nie są obsługiwane dla typów wartości.  
  
 W języku Visual Basic nie można zadeklarować zdarzenia w interfejsach kowariantnego bez określania typu delegowanego. Ponadto kowariantnego interfejsów nie mogą mieć zagnieżdżonych klas, wyliczeń lub struktury, ale można mieć zagnieżdżonych interfejsów.  
  
## <a name="behavior"></a>Zachowanie  
 Interfejs, który ma parametr typu kowariantnego umożliwia sposobów niż określony przez parametr typu bardziej pochodnego typy zwracane. Na przykład ponieważ w .NET Framework 4 w <xref:System.Collections.Generic.IEnumerable%601>typu T jest kowariantny, można przypisać obiektu `IEnumerabe(Of String)` typu do obiektu `IEnumerable(Of Object)` typu bez korzystania z żadnych metod konwersji specjalnych.  
  
 Kowariantnego delegata można przypisać inną delegata tego samego typu, ale także z bardziej pochodny parametr typu ogólnego.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak zadeklarować, rozszerzać i implementacji kowariantnego interfejs generyczny. On również przedstawia użycie niejawna konwersja dla klas implementujących interfejs kowariantny.  
  
 [!code-vb[vbVarianceKeywords#3](../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/out-generic-modifier_1.vb)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak zadeklarować, wystąpienia i wywoływać kowariantnego Delegat ogólny. Pokazuje też, używania niejawna konwersja typów delegata.  
  
 [!code-vb[vbVarianceKeywords#4](../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/out-generic-modifier_2.vb)]  
  
## <a name="see-also"></a>Zobacz też  
 [Wariancje w interfejsach ogólnych](../../programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md)  
 [In](../../../visual-basic/language-reference/modifiers/in-generic-modifier.md)
