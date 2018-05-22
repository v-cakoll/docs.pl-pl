---
title: Friend (Visual Basic)
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
ms.openlocfilehash: d906fc8ada19f22059da44acbd76dd07dacd4801
ms.sourcegitcommit: 22c3c8f74eaa138dbbbb02eb7d720fce87fc30a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/17/2018
---
# <a name="friend-visual-basic"></a>Friend (Visual Basic)
Określa, że co najmniej jeden zadeklarowany element programistyczny jest dostępny tylko w obrębie zestawu, który zawiera jego deklarację.  
  
## <a name="remarks"></a>Uwagi  
 W wielu przypadkach ma elementów, takich jak klasy i struktury, który będzie używany przez cały zestaw nie tylko przez składnik, który je deklaruje programowania. Jednak nie można ich jako dostępny przez kod poza zestaw (na przykład jeśli aplikacja jest zastrzeżone). Jeśli chcesz ograniczyć dostęp do elementu w ten sposób można Zadeklaruj ją przy użyciu `Friend` modyfikator.  
  
 Kod w innych klas, struktur i modułów, które są kompilowane do tego samego zestawu można uzyskać dostęp do wszystkich `Friend` elementów w tym zestawie.  
  
 `Friend` dostęp jest często poziomu preferowany elementom programowania aplikacji i `Friend` jest dostęp domyślny poziom interfejsu, modułu, klasy lub struktury.  
  
 Można użyć `Friend` tylko na poziomie modułu, interfejsem lub przestrzeni nazw. W związku z tym kontekście deklaracji dla `Friend` elementu musi być plikiem źródłowym, przestrzeni nazw, interfejs, modułu, klasy lub struktury; nie może być procedury.  

> [!NOTE]
> Można również użyć [Protected Friend](protected-friend.md) modyfikator dostępu, co sprawia, że element członkowski klasy jest dostępny w obrębie klasy, z klasy pochodnej i z tego samego zestawu, w którym klasa jest zdefiniowana. Aby ograniczyć dostęp do elementu członkowskiego z w swojej klasie i klasach pochodnych w tym samym zestawie, należy użyć [prywatne chronione](private-protected.md) modyfikator dostępu.

 Porównanie `Friend` i innych modyfikatorów dostępu, zobacz [poziomy w języku Visual Basic dostępu](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
> [!NOTE]
>  Można określić, że inny zestaw jest przyjaznego zestawu, co umożliwia dostęp do wszystkich typów i elementów członkowskich, które są oznaczone jako `Friend`. Aby uzyskać więcej informacji, zobacz [przyjazne zestawy](../../programming-guide/concepts/assemblies-gac/friend-assemblies.md).  
  
## <a name="example"></a>Przykład  
 Następujące klasy używa `Friend` modyfikator zezwalająca na inne elementy programowania, w tym samym zestawie, aby dostęp do niektórych elementów członkowskich.  
  
 [!code-vb[VbVbalrAccessModifiers#1](../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/friend_1.vb)]  
  
## <a name="usage"></a>Użycie  
 Można użyć `Friend` modyfikator w tych sytuacjach:  
  
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
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>  
 [Public](../../../visual-basic/language-reference/modifiers/public.md)  
 [Protected](../../../visual-basic/language-reference/modifiers/protected.md)  
 [Private](../../../visual-basic/language-reference/modifiers/private.md)  
 [Prywatne chronione](./private-protected.md)   
 [Friend chronionych](./protected-friend.md)   
 [Poziomy dostępu w Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)  
 [Procedury](../../../visual-basic/programming-guide/language-features/procedures/index.md)  
 [Struktury](../../../visual-basic/programming-guide/language-features/data-types/structures.md)  
 [Obiekty i klasy](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
