---
title: Implements — instrukcja (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Implements
- Implements
helpviewer_keywords:
- Implements statement [Visual Basic], syntax
- Implements statement [Visual Basic]
- interface implementation [Visual Basic], Implements statement
ms.assetid: 1fafb83f-f55a-4215-8ea9-681e8622613d
ms.openlocfilehash: 1f0c6b052ead303e0b43465dac2067422abc4ef8
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "58818875"
---
# <a name="implements-statement"></a>Implements — Instrukcja
Określa jedną lub więcej interfejsów lub składowych interfejsu, które muszą zostać zaimplementowane w klasie lub definicji struktury, w której występuje.  
  
## <a name="syntax"></a>Składnia  
  
```  
Implements interfacename [, ...]  
-or-  
Implements interfacename.interfacemember [, ...]  
```  
  
## <a name="parts"></a>Części  
 `interfacename`  
 Wymagana. Interfejs, którego właściwości, procedur i zdarzeń mają być wykonywane przez odpowiednie elementy członkowskie w klasie lub strukturze.  
  
 `interfacemember`  
 Wymagana. Element członkowski interfejs, który zostanie wdrożony.  
  
## <a name="remarks"></a>Uwagi  
 Interfejs jest kolekcją prototypów reprezentujących elementy członkowskie (właściwości, procedur i zdarzeń) hermetyzuje interfejs. Interfejsy zawierać deklaracje dla elementów członkowskich; klasy i struktury zaimplementować te składowe. Więcej informacji znajdziesz w artykule [Interfejsy](../../../visual-basic/programming-guide/language-features/interfaces/index.md).  
  
 `Implements` Natychmiast wykonaj instrukcję `Class` lub `Structure` instrukcji.  
  
 Podczas implementowania interfejsu musi implementować wszystkich elementów członkowskich zadeklarowanych w interfejsie. Pominięcie dowolnego elementu członkowskiego jest uważany za błąd składni. Aby zaimplementować poszczególnych elementów członkowskich, należy określić [implementuje](../../../visual-basic/language-reference/statements/implements-clause.md) — słowo kluczowe (który jest oddzielony od `Implements` instrukcji) kiedy Deklarujesz element członkowski w klasie lub strukturze. Więcej informacji znajdziesz w artykule [Interfejsy](../../../visual-basic/programming-guide/language-features/interfaces/index.md).  
  
 Można użyć klasy [prywatnej](../../../visual-basic/language-reference/modifiers/private.md) implementacji właściwości i procedury, ale te składowe są dostępne tylko rzutowania wystąpienia klasy implementującej do zmiennej zadeklarowany typ interfejsu.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak używać `Implements` instrukcję, aby implementować członków interfejsu. Definiuje interfejs o nazwie `ICustomerInfo` zdarzenie, właściwości i procedury. Klasa `customerInfo` implementuje wszystkie elementy członkowskie zdefiniowane w interfejsie.  
  
 [!code-vb[VbVbalrStatements#33](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#33)]  
  
 Należy pamiętać, że klasa `customerInfo` używa `Implements` instrukcji na oddzielne źródło wiersza kodu, aby wskazać, że klasa implementuje wszystkie elementy członkowskie `ICustomerInfo` interfejsu. Następnie używa każdego elementu członkowskiego w klasie `Implements` słowa kluczowego jako części swojej deklaracji elementu członkowskiego, aby wskazać implementuje tej składowej interfejsu.  
  
## <a name="example"></a>Przykład  
 Poniższe dwie procedury pokazują, jak można użyć interfejsu implementowany w poprzednim przykładzie. Aby przetestować wdrożenia, należy dodać te procedury do projektu i wywołania `testImplements` procedury.  
  
 [!code-vb[VbVbalrStatements#34](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#34)]  
  
## <a name="see-also"></a>Zobacz także

- [Implements](../../../visual-basic/language-reference/statements/implements-clause.md)
- [Instrukcja Interface](../../../visual-basic/language-reference/statements/interface-statement.md)
- [Interfejsy](../../../visual-basic/programming-guide/language-features/interfaces/index.md)
