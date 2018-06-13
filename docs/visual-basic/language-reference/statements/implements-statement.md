---
title: Implements — Instrukcja
ms.date: 07/20/2015
f1_keywords:
- vb.Implements
- Implements
helpviewer_keywords:
- Implements statement [Visual Basic], syntax
- Implements statement [Visual Basic]
- interface implementation [Visual Basic], Implements statement
ms.assetid: 1fafb83f-f55a-4215-8ea9-681e8622613d
ms.openlocfilehash: 5afc7e4e3a03dfab1288e50e65e5076bdd438f7a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33604214"
---
# <a name="implements-statement"></a>Implements — Instrukcja
Określa jeden lub więcej interfejsów lub członków interfejsu, które muszą zostać zaimplementowane w klasie lub definicji struktury, w której znajduje się.  
  
## <a name="syntax"></a>Składnia  
  
```  
Implements interfacename [, ...]  
-or-  
Implements interfacename.interfacemember [, ...]  
```  
  
## <a name="parts"></a>Części  
 `interfacename`  
 Wymagana. Interfejs, którego właściwości, procedur i zdarzenia są wdrażane przez odpowiednie elementy członkowskie w klasie lub strukturze.  
  
 `interfacemember`  
 Wymagana. Element członkowski interfejsu, który zostanie wdrożony.  
  
## <a name="remarks"></a>Uwagi  
 Interfejs jest kolekcją prototypów reprezentujący członków (właściwości, procedur i zdarzeń) hermetyzuje interfejsu. Interfejsy zawierać tylko deklaracje elementów członkowskich; klasy i struktury implementuje tych elementów członkowskich. Aby uzyskać więcej informacji, zobacz [interfejsów](../../../visual-basic/programming-guide/language-features/interfaces/index.md).  
  
 `Implements` Instrukcji musi występować zaraz po `Class` lub `Structure` instrukcji.  
  
 Po zaimplementowaniu interfejsu należy zaimplementować wszystkich elementów członkowskich zadeklarowanych w interfejsie. Pominięcie dowolnego elementu członkowskiego jest uważany za błąd składni. Aby zaimplementować poszczególnych elementów członkowskich, należy określić [implementuje](../../../visual-basic/language-reference/statements/implements-clause.md) — słowo kluczowe (które są oddzielne od `Implements` instrukcji) po deklaruje element członkowski klasy lub struktury. Aby uzyskać więcej informacji, zobacz [interfejsów](../../../visual-basic/programming-guide/language-features/interfaces/index.md).  
  
 Można użyć klasy [prywatnej](../../../visual-basic/language-reference/modifiers/private.md) implementacje właściwości i procedury, ale elementy te są dostępne tylko rzutowanie zadeklarowany wystąpienia klasy implementującej do zmiennej typu interfejsu.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia użycie `Implements` instrukcji można implementować członków interfejsu. Definiuje interfejs o nazwie `ICustomerInfo` zdarzenia, właściwości i procedury. Klasa `customerInfo` implementuje wszystkich elementów członkowskich zdefiniowanych w interfejsie.  
  
 [!code-vb[VbVbalrStatements#33](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/implements-statement_1.vb)]  
  
 Należy pamiętać, że klasa `customerInfo` używa `Implements` instrukcji w wierszu kodu oddzielne źródło, aby wskazać, że klasa implementuje wszyscy członkowie `ICustomerInfo` interfejsu. Następnie używa każdy element członkowski w klasie `Implements` słowa kluczowego jako części swojej deklaracji elementu członkowskiego, aby wskazać, że implementuje ten element członkowski interfejsu.  
  
## <a name="example"></a>Przykład  
 Poniższe dwie procedury pokazują, jak można za pomocą interfejsu zaimplementowana w poprzednim przykładzie. Próba wykonania tych procedur projektu i dodawać wywołania `testImplements` procedury.  
  
 [!code-vb[VbVbalrStatements#34](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/implements-statement_2.vb)]  
  
## <a name="see-also"></a>Zobacz też  
 [Implements](../../../visual-basic/language-reference/statements/implements-clause.md)  
 [Interface, instrukcja](../../../visual-basic/language-reference/statements/interface-statement.md)  
 [Interfejsy](../../../visual-basic/programming-guide/language-features/interfaces/index.md)
