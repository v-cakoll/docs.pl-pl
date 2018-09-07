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
ms.openlocfilehash: 805813506b957afb326c71ee4bbb15837726e4e5
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2018
ms.locfileid: "44076322"
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
 Wymagane. Interfejs, którego właściwości, procedur i zdarzeń mają być wykonywane przez odpowiednie elementy członkowskie w klasie lub strukturze.  
  
 `interfacemember`  
 Wymagane. Element członkowski interfejs, który zostanie wdrożony.  
  
## <a name="remarks"></a>Uwagi  
 Interfejs jest kolekcją prototypów reprezentujących elementy członkowskie (właściwości, procedur i zdarzeń) hermetyzuje interfejs. Interfejsy zawierać deklaracje dla elementów członkowskich; klasy i struktury zaimplementować te składowe. Więcej informacji znajdziesz w artykule [Interfejsy](../../../visual-basic/programming-guide/language-features/interfaces/index.md).  
  
 `Implements` Natychmiast wykonaj instrukcję `Class` lub `Structure` instrukcji.  
  
 Podczas implementowania interfejsu musi implementować wszystkich elementów członkowskich zadeklarowanych w interfejsie. Pominięcie dowolnego elementu członkowskiego jest uważany za błąd składni. Aby zaimplementować poszczególnych elementów członkowskich, należy określić [implementuje](../../../visual-basic/language-reference/statements/implements-clause.md) — słowo kluczowe (który jest oddzielony od `Implements` instrukcji) kiedy Deklarujesz element członkowski w klasie lub strukturze. Więcej informacji znajdziesz w artykule [Interfejsy](../../../visual-basic/programming-guide/language-features/interfaces/index.md).  
  
 Można użyć klasy [prywatnej](../../../visual-basic/language-reference/modifiers/private.md) implementacji właściwości i procedury, ale te składowe są dostępne tylko rzutowania wystąpienia klasy implementującej do zmiennej zadeklarowany typ interfejsu.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak używać `Implements` instrukcję, aby implementować członków interfejsu. Definiuje interfejs o nazwie `ICustomerInfo` zdarzenie, właściwości i procedury. Klasa `customerInfo` implementuje wszystkie elementy członkowskie zdefiniowane w interfejsie.  
  
 [!code-vb[VbVbalrStatements#33](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/implements-statement_1.vb)]  
  
 Należy pamiętać, że klasa `customerInfo` używa `Implements` instrukcji na oddzielne źródło wiersza kodu, aby wskazać, że klasa implementuje wszystkie elementy członkowskie `ICustomerInfo` interfejsu. Następnie używa każdego elementu członkowskiego w klasie `Implements` słowa kluczowego jako części swojej deklaracji elementu członkowskiego, aby wskazać implementuje tej składowej interfejsu.  
  
## <a name="example"></a>Przykład  
 Poniższe dwie procedury pokazują, jak można użyć interfejsu implementowany w poprzednim przykładzie. Aby przetestować wdrożenia, należy dodać te procedury do projektu i wywołania `testImplements` procedury.  
  
 [!code-vb[VbVbalrStatements#34](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/implements-statement_2.vb)]  
  
## <a name="see-also"></a>Zobacz też  
 [Implements](../../../visual-basic/language-reference/statements/implements-clause.md)  
 [Instrukcja Interface](../../../visual-basic/language-reference/statements/interface-statement.md)  
 [Interfejsy](../../../visual-basic/programming-guide/language-features/interfaces/index.md)
