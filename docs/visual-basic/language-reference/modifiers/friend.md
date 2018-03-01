---
title: Friend (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Friend
helpviewer_keywords:
- Friend keyword [Visual Basic]
- Friend access modifier
- Friend keyword [Visual Basic], syntax
- Protected Friend keyword combination
- Friend keyword [Visual Basic], and Protected
ms.assetid: b664605e-1c79-4728-b996-aa59c50846bc
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: df0e8ad1990fe7a1aa495e1794c942813cffb5bc
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="friend-visual-basic"></a>Friend (Visual Basic)
Określa, że co najmniej jeden zadeklarowany element programistyczny jest dostępny tylko w obrębie zestawu, który zawiera jego deklarację.  
  
## <a name="remarks"></a>Uwagi  
 W wielu przypadkach ma elementów, takich jak klasy i struktury, który będzie używany przez cały zestaw nie tylko przez składnik, który je deklaruje programowania. Jednak nie można ich jako dostępny przez kod poza zestaw (na przykład jeśli aplikacja jest zastrzeżone). Jeśli chcesz ograniczyć dostęp do elementu w ten sposób można Zadeklaruj ją przy użyciu `Friend` modyfikator.  
  
 Kod w innych klas, struktur i modułów, które są kompilowane do tego samego zestawu można uzyskać dostęp do wszystkich `Friend` elementów w tym zestawie.  
  
 `Friend`dostęp jest często poziomu preferowany elementom programowania aplikacji i `Friend` jest dostęp domyślny poziom interfejsu, modułu, klasy lub struktury.  
  
 Można użyć `Friend` tylko na poziomie modułu, interfejsem lub przestrzeni nazw. W związku z tym kontekście deklaracji dla `Friend` elementu musi być plikiem źródłowym, przestrzeni nazw, interfejs, modułu, klasy lub struktury; nie może być procedury.  
  
 Można użyć `Friend` modyfikator w połączeniu z [chronione](../../../visual-basic/language-reference/modifiers/protected.md) modyfikator w tej samej deklaracji. Ta kombinacja przyznaje zarówno `Friend` dostępu i chronionego dostępu na zadeklarowane elementy, dzięki czemu są one dostępne z dowolnej lokalizacji w tym samym zestawie, swojej klasy oraz klas pochodnych. Można określić `Protected Friend` tylko w elementach członkowskich klas.  
  
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
 [Poziomy dostępu w Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)  
 [Procedury](../../../visual-basic/programming-guide/language-features/procedures/index.md)  
 [Struktury](../../../visual-basic/programming-guide/language-features/data-types/structures.md)  
 [Obiekty i klasy](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
