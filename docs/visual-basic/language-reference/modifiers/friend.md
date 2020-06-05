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
ms.openlocfilehash: 4ac8e5942cf6097642ec111992ebfcdb91e8d7c1
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84392174"
---
# <a name="friend-visual-basic"></a>Friend (Visual Basic)
Określa, że co najmniej jeden zadeklarowany element programistyczny jest dostępny tylko w obrębie zestawu, który zawiera jego deklarację.  
  
## <a name="remarks"></a>Uwagi  
 W wielu przypadkach elementy programowania, takie jak klasy i struktury, mają być używane przez cały zestaw, nie tylko przez składnik, który deklaruje je. Jednak użytkownik może nie chcieć uzyskiwać dostępu przez kod poza zestawem (na przykład jeśli aplikacja jest zastrzeżona). Jeśli chcesz ograniczyć dostęp do elementu w ten sposób, możesz go zadeklarować za pomocą `Friend` modyfikatora.  
  
 Kod w innych klasach, strukturach i modułach, które są kompilowane do tego samego zestawu, mogą uzyskać dostęp do wszystkich `Friend` elementów w tym zestawie.  
  
 `Friend`dostęp jest często preferowanym poziomem dla elementów programistycznych aplikacji i `Friend` jest domyślnym poziomem dostępu do interfejsu, modułu, klasy lub struktury.  
  
 Można używać `Friend` tylko na poziomie modułu, interfejsu lub przestrzeni nazw. W związku z tym kontekst deklaracji dla `Friend` elementu musi być plikiem źródłowym, przestrzenią nazw, interfejsem, modułem, klasą lub strukturą. nie może to być procedura.  

> [!NOTE]
> Można również użyć modyfikatora [Protected Friend](protected-friend.md) Access, który sprawia, że element członkowski klasy jest dostępny z tej klasy, z klas pochodnych i z tego samego zestawu, w którym jest zdefiniowana Klasa. Aby ograniczyć dostęp do elementu członkowskiego z poziomu jego klasy i z klas pochodnych w tym samym zestawie, należy użyć modyfikatora [Private Protected](private-protected.md) Access.

 Aby uzyskać porównanie `Friend` i inne Modyfikatory dostępu, zobacz [poziomy dostępu w Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md).  
  
> [!NOTE]
> Można określić, że inny zestaw jest zestawem zaprzyjaźnionym, który umożliwia mu dostęp do wszystkich typów i elementów członkowskich, które są oznaczone jako `Friend` . Aby uzyskać więcej informacji, zobacz [zaprzyjaźnione zestawy](../../../standard/assembly/friend.md).

## <a name="example"></a>Przykład  
 Poniższa klasa używa `Friend` modyfikatora, aby zezwolić innym elementom programistycznym w tym samym zestawie na dostęp do niektórych elementów członkowskich.  
  
 [!code-vb[VbVbalrAccessModifiers#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalraccessmodifiers/vb/class1.vb#1)]  
  
## <a name="usage"></a>Użycie  
 Modyfikatora można użyć `Friend` w tych kontekstach:  
  
 [Class, instrukcja](../statements/class-statement.md)  
  
 [Const, instrukcja](../statements/const-statement.md)  
  
 [Declare — Instrukcja](../statements/declare-statement.md)  
  
 [Delegate — Instrukcja](../statements/delegate-statement.md)  
  
 [Dim, instrukcja](../statements/dim-statement.md)  
  
 [Enum, instrukcja](../statements/enum-statement.md)  
  
 [Event — Instrukcja](../statements/event-statement.md)  
  
 [Function, instrukcja](../statements/function-statement.md)  
  
 [Interface, instrukcja](../statements/interface-statement.md)  
  
 [Module — Instrukcja](../statements/module-statement.md)  
  
 [Property — Instrukcja](../statements/property-statement.md)  
  
 [Structure — Instrukcja](../statements/structure-statement.md)  
  
 [Sub, instrukcja](../statements/sub-statement.md)  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>
- [Społeczeństwo](public.md)
- [Chronione](protected.md)
- [Użytek](private.md)
- [Prywatne chronione](./private-protected.md)
- [Protected Friend](./protected-friend.md)
- [Poziomy dostępu w Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md)
- [Procedury](../../programming-guide/language-features/procedures/index.md)
- [Struktury](../../programming-guide/language-features/data-types/structures.md)
- [Obiekty i klasy](../../programming-guide/language-features/objects-and-classes/index.md)
