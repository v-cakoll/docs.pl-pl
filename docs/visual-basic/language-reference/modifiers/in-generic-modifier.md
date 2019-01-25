---
title: In (modyfikator ogólny) (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.VarianceIn
helpviewer_keywords:
- contravariance, In keyword [Visual Basic]
- In keyword [Visual Basic]
ms.assetid: 59bb13c5-fe96-42b8-8286-86293d1661c5
ms.openlocfilehash: 4d5909e6ee7436b7e4f7baa30bfe81eb8ba5441e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54625756"
---
# <a name="in-generic-modifier-visual-basic"></a>In (modyfikator ogólny) (Visual Basic)
Dla parametrów typu genetycznego `In` — słowo kluczowe Określa, że parametr typu jest kontrawariantny.  
  
## <a name="remarks"></a>Uwagi  
 Kontrawariancja umożliwia używania typu mniej pochodnego niż określona przez parametr ogólny. Umożliwia to niejawna konwersja klasy, które implementują interfejsów typu variant i niejawnej konwersji typów obiektów delegowanych.  
  
 Aby uzyskać więcej informacji, zobacz [kowariancji i kontrawariancji](../../programming-guide/concepts/covariance-contravariance/index.md).  
  
## <a name="rules"></a>reguły  
 Możesz użyć `In` — słowo kluczowe w interfejsach ogólnych i delegatach.  
  
 Parametr typu mogą być deklarowane kontrawariantnego w ogólny interfejs lub delegat, jeśli jest używany tylko jako typ argumentów metody i nie jest używana jako zwracany typ metody. `ByRef` Parametry nie mogą być kowariantny lub kontrawariantny.  
  
 Kowariancja i kontrawariancja są obsługiwane dla typów odwołań i nie jest obsługiwane dla typów wartości.  
  
 W języku Visual Basic nie można zadeklarować zdarzenia w interfejsach kontrawariantnego bez określania typu delegata. Ponadto kontrawariantnego interfejsy nie mogą zagnieżdżać klas, wyliczeń lub struktur, ale mogą być zagnieżdżone interfejsów.  
  
## <a name="behavior"></a>Zachowanie  
 Interfejs, który ma kontrawariantnego parametru typu umożliwia jego metod przyjmowały argumenty mniej pochodne typy niż określony przez parametr typu interfejsu. Na przykład ponieważ w programie .NET Framework 4 w <xref:System.Collections.Generic.IComparer%601> interfejsu typu T jest kontrawariantny, można przypisać obiektu `IComparer(Of Person)` typ obiektu `IComparer(Of Employee)` typu bez przy użyciu dowolnej metody konwersji specjalne, jeśli `Person` dziedziczy `Employee`.  
  
 Kontrawariantnego delegata można przypisać inną delegata tego samego typu, ale mniej pochodnego parametr typu ogólnego.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak deklarować, rozszerzanie i implementować interfejs ogólny kontrawariantny. Pokazuje również, jak można użyć niejawna konwersja dla klas, które implementują ten interfejs.  
  
 [!code-vb[vbVarianceKeywords#1](../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/in-generic-modifier_1.vb)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak deklarować, Utwórz wystąpienie i wywołania to delegat generyczny kontrawariantny. Pokazuje również, jak można niejawnie przekonwertować typu delegata.  
  
 [!code-vb[vbVarianceKeywords#2](../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/in-generic-modifier_2.vb)]  
  
## <a name="see-also"></a>Zobacz także
- [Wariancje w interfejsach ogólnych](../../programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md)
- [limit](../../../visual-basic/language-reference/modifiers/out-generic-modifier.md)
