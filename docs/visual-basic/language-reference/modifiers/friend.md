---
title: Friend
ms.date: 07/20/2015
f1_keywords:
- vb.Friend
helpviewer_keywords:
- Friend keyword [Visual Basic]
- Friend access modifier
- Friend keyword [Visual Basic], syntax
- Protected Friend keyword combination
- Friend keyword [Visual Basic], and Protected
ms.assetid: b664605e-1c79-4728-b996-aa59c50846bc
ms.openlocfilehash: 98f8ed947c9f4376c5778011a3a91ca8b094f9ec
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351561"
---
# <a name="friend-visual-basic"></a>Friend (Visual Basic)
Określa, że co najmniej jeden zadeklarowany element programistyczny jest dostępny tylko w obrębie zestawu, który zawiera jego deklarację.  
  
## <a name="remarks"></a>Uwagi  
 W wielu przypadkach elementy programowania, takie jak klasy i struktury, mają być używane przez cały zestaw, nie tylko przez składnik, który deklaruje je. Jednak użytkownik może nie chcieć uzyskiwać dostępu przez kod poza zestawem (na przykład jeśli aplikacja jest zastrzeżona). Jeśli chcesz ograniczyć dostęp do elementu w ten sposób, możesz go zadeklarować za pomocą modyfikatora `Friend`.  
  
 Kod w innych klasach, strukturach i modułach, które są kompilowane do tego samego zestawu, mogą uzyskać dostęp do wszystkich elementów `Friend` w tym zestawie.  
  
 `Friend` dostęp jest często preferowanym poziomem dla elementów programistycznych aplikacji, a `Friend` jest domyślnym poziomem dostępu do interfejsu, modułu, klasy lub struktury.  
  
 `Friend` można używać tylko na poziomie modułu, interfejsu lub przestrzeni nazw. W związku z tym kontekst deklaracji dla elementu `Friend` musi być plikiem źródłowym, przestrzenią nazw, interfejsem, modułem, klasą lub strukturą; nie może to być procedura.  

> [!NOTE]
> Można również użyć modyfikatora [Protected Friend](protected-friend.md) Access, który sprawia, że element członkowski klasy jest dostępny z tej klasy, z klas pochodnych i z tego samego zestawu, w którym jest zdefiniowana Klasa. Aby ograniczyć dostęp do elementu członkowskiego z poziomu jego klasy i z klas pochodnych w tym samym zestawie, należy użyć modyfikatora [Private Protected](private-protected.md) Access.

 Aby porównać `Friend` i inne Modyfikatory dostępu, zobacz [poziomy dostępu w Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
> [!NOTE]
> Można określić, że inny zestaw jest zestawem zaprzyjaźnionym, który umożliwia mu dostęp do wszystkich typów i elementów członkowskich, które są oznaczone jako `Friend`. Aby uzyskać więcej informacji, zobacz [zaprzyjaźnione zestawy](../../../standard/assembly/friend.md).

## <a name="example"></a>Przykład  
 Poniższa klasa używa modyfikatora `Friend`, aby zezwolić innym elementom programistycznym w tym samym zestawie na dostęp do niektórych elementów członkowskich.  
  
 [!code-vb[VbVbalrAccessModifiers#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalraccessmodifiers/vb/class1.vb#1)]  
  
## <a name="usage"></a>Sposób użycia  
 W tych kontekstach można użyć modyfikatora `Friend`:  
  
 [Class, instrukcja](../../../visual-basic/language-reference/statements/class-statement.md)  
  
 [Const, instrukcja](../../../visual-basic/language-reference/statements/const-statement.md)  
  
 [Declare, instrukcja](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 [Delegate, instrukcja](../../../visual-basic/language-reference/statements/delegate-statement.md)  
  
 [Dim, instrukcja](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [Enum, instrukcja](../../../visual-basic/language-reference/statements/enum-statement.md)  
  
 [Event, instrukcja](../../../visual-basic/language-reference/statements/event-statement.md)  
  
 [Function, instrukcja](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [Interface, instrukcja](../../../visual-basic/language-reference/statements/interface-statement.md)  
  
 [Module, instrukcja](../../../visual-basic/language-reference/statements/module-statement.md)  
  
 [Property, instrukcja](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [Structure, instrukcja](../../../visual-basic/language-reference/statements/structure-statement.md)  
  
 [Sub, instrukcja](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>
- [Public](../../../visual-basic/language-reference/modifiers/public.md)
- [Protected](../../../visual-basic/language-reference/modifiers/protected.md)
- [Private](../../../visual-basic/language-reference/modifiers/private.md)
- [Private Protected](./private-protected.md)
- [Protected Friend](./protected-friend.md)
- [Poziomy dostępu w Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
- [Procedury](../../../visual-basic/programming-guide/language-features/procedures/index.md)
- [Struktury](../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [Obiekty i klasy](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
