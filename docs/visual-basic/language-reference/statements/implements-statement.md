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
ms.openlocfilehash: e2e279b2c935dd082cbf832265a8ad09e6dffe9e
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351153"
---
# <a name="implements-statement"></a>Implements — Instrukcja
Określa jeden lub więcej interfejsów lub składowych interfejsu, które muszą zostać zaimplementowane w definicji klasy lub struktury, w której występuje.  
  
## <a name="syntax"></a>Składnia  
  
```vb  
Implements interfacename [, ...]  
' -or-  
Implements interfacename.interfacemember [, ...]  
```  
  
## <a name="parts"></a>Części  
 `interfacename`  
 Wymagana. Interfejs, którego właściwości, procedury i zdarzenia mają być implementowane przez odpowiadające im elementy członkowskie klasy lub struktury.  
  
 `interfacemember`  
 Wymagana. Element członkowski interfejsu, który jest implementowany.  
  
## <a name="remarks"></a>Uwagi  
 Interfejs jest kolekcją prototypów reprezentujących elementy członkowskie (właściwości, procedury i zdarzenia), które są hermetyzowane w interfejsie. Interfejsy zawierają tylko deklaracje elementów członkowskich; klasy i struktury implementują te składowe. Aby uzyskać więcej informacji, zobacz [interfejsy](../../../visual-basic/programming-guide/language-features/interfaces/index.md).  
  
 Instrukcja `Implements` musi być od razu zgodna z instrukcją `Class` lub `Structure`.  
  
 Podczas implementowania interfejsu, należy zaimplementować wszystkie elementy członkowskie zadeklarowane w interfejsie. Pominięcie żadnego elementu członkowskiego jest uznawane za błąd składniowy. Aby zaimplementować pojedynczy element członkowski, należy określić słowo kluczowe [Implements](../../../visual-basic/language-reference/statements/implements-clause.md) (które jest oddzielone od instrukcji `Implements`) podczas deklarowania elementu członkowskiego w klasie lub strukturze. Aby uzyskać więcej informacji, zobacz [interfejsy](../../../visual-basic/programming-guide/language-features/interfaces/index.md).  
  
 Klasy mogą używać [prywatnych](../../../visual-basic/language-reference/modifiers/private.md) implementacji właściwości i procedur, ale te elementy członkowskie są dostępne tylko przez rzutowanie wystąpienia klasy implementującej na zmienną zadeklarowaną jako typ interfejsu.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak używać instrukcji `Implements` do implementowania elementów członkowskich interfejsu. Definiuje interfejs o nazwie `ICustomerInfo` ze zdarzeniem, właściwością i procedurą. Klasa `customerInfo` implementuje wszystkie elementy członkowskie zdefiniowane w interfejsie.  
  
 [!code-vb[VbVbalrStatements#33](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#33)]  
  
 Należy zauważyć, że Klasa `customerInfo` używa instrukcji `Implements` w oddzielnym wierszu kodu źródłowego, aby wskazać, że klasa implementuje wszystkie elementy członkowskie interfejsu `ICustomerInfo`. Następnie każdy element członkowski w klasie używa słowa kluczowego `Implements` jako części deklaracji elementu członkowskiego, aby wskazać, że implementuje ten element członkowski interfejsu.  
  
## <a name="example"></a>Przykład  
 W poniższych dwóch procedurach pokazano, jak można użyć interfejsu zaimplementowanego w poprzednim przykładzie. Aby przetestować implementację, należy dodać te procedury do projektu i wywołać procedurę `testImplements`.  
  
 [!code-vb[VbVbalrStatements#34](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#34)]  
  
## <a name="see-also"></a>Zobacz także

- [Wprowadza](../../../visual-basic/language-reference/statements/implements-clause.md)
- [Interface, instrukcja](../../../visual-basic/language-reference/statements/interface-statement.md)
- [Interfejsy](../../../visual-basic/programming-guide/language-features/interfaces/index.md)
