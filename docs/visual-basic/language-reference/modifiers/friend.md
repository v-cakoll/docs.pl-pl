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
ms.openlocfilehash: 9be3200300de308a70559536905d1e118a4a5fe4
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54616202"
---
# <a name="friend-visual-basic"></a>Friend (Visual Basic)
Określa, że co najmniej jeden zadeklarowany element programistyczny jest dostępny tylko w obrębie zestawu, który zawiera jego deklarację.  
  
## <a name="remarks"></a>Uwagi  
 W wielu przypadkach chcesz elementów, takich jak klasy i struktury, który będzie używany przez cały zespół nie tylko przez składnik, który je deklaruje programowania. Jednak nie można ich udostępnienie przez kod poza zestaw (na przykład, jeśli aplikacja jest zastrzeżone). Jeśli chcesz ograniczyć dostęp do elementu w ten sposób, trzeba je zadeklarować, za pomocą `Friend` modyfikator.  
  
 Kod w innych klas, struktur i modułów, które są kompilowane do tej samej zestawu można uzyskać dostęp do wszystkich `Friend` elementów w tym zestawie.  
  
 `Friend` dostęp do często jest preferowany poziom dla elementów programowania aplikacji, a `Friend` jest dostęp do domyślnej na poziomie interfejsu, modułu, klasy lub struktury.  
  
 Możesz użyć `Friend` tylko na poziomie modułu, interfejsu lub przestrzeni nazw. W związku z tym, kontekst deklaracji dla `Friend` element musi być plikiem źródłowym, przestrzeni nazw, interfejs, modułu, klasy lub struktury; nie może być procedurą.  

> [!NOTE]
> Można również użyć [Protected Friend](protected-friend.md) modyfikator dostępu, co sprawia, że element członkowski klasy jest dostępny w obrębie tej klasy z klas pochodnych i z tego samego zestawu, w którym klasa jest zdefiniowana. Aby ograniczyć dostęp do elementu członkowskiego w w swojej klasie i klasach pochodnych tego samego zestawu, należy użyć [Private Protected](private-protected.md) modyfikator dostępu.

 Porównanie `Friend` , a druga modyfikatorach dostępu, zobacz [poziomy w języku Visual Basic dostępu](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
> [!NOTE]
>  Można określić, czy innego zestawu jest zestawu friend, co pozwala na dostęp do wszystkich typów i elementów członkowskich, które są oznaczone jako `Friend`. Aby uzyskać więcej informacji, zobacz [przyjaznych zestawów](../../programming-guide/concepts/assemblies-gac/friend-assemblies.md).  
  
## <a name="example"></a>Przykład  
 Następujące klasy używa `Friend` modyfikator, aby zezwolić na inne elementy programowania, w ramach tego samego zestawu dostęp do niektórych elementów członkowskich.  
  
 [!code-vb[VbVbalrAccessModifiers#1](../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/friend_1.vb)]  
  
## <a name="usage"></a>Użycie  
 Możesz użyć `Friend` modyfikator w tych kontekstach:  
  
 [Class, instrukcja](../../../visual-basic/language-reference/statements/class-statement.md)  
  
 [Const, instrukcja](../../../visual-basic/language-reference/statements/const-statement.md)  
  
 [Declare, instrukcja](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 [Delegate, instrukcja](../../../visual-basic/language-reference/statements/delegate-statement.md)  
  
 [Dim, instrukcja](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [Enum, instrukcja](../../../visual-basic/language-reference/statements/enum-statement.md)  
  
 [Event, instrukcja](../../../visual-basic/language-reference/statements/event-statement.md)  
  
 [Function, instrukcja](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [Instrukcja Interface](../../../visual-basic/language-reference/statements/interface-statement.md)  
  
 [Instrukcja Module](../../../visual-basic/language-reference/statements/module-statement.md)  
  
 [Instrukcja Property](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [Structure, instrukcja](../../../visual-basic/language-reference/statements/structure-statement.md)  
  
 [Sub, instrukcja](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>
- [Public](../../../visual-basic/language-reference/modifiers/public.md)
- [Protected](../../../visual-basic/language-reference/modifiers/protected.md)
- [Private](../../../visual-basic/language-reference/modifiers/private.md)
- [Private Protected](./private-protected.md)
- [Protected Friend](./protected-friend.md)
- [Poziomy dostępu w języku Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
- [Procedury](../../../visual-basic/programming-guide/language-features/procedures/index.md)
- [Struktury](../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [Obiekty i klasy](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
