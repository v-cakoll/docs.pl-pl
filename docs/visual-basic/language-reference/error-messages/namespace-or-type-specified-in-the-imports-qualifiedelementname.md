---
title: Przestrzeń nazw lub typ określone w elemencie Imports „<qualifiedelementname>” nie zawierają żadnego członka publicznego lub nie można go odnaleźć
ms.date: 07/20/2015
f1_keywords:
- bc40056
- vbc40056
helpviewer_keywords:
- BC40056
ms.assetid: b59f5754-444f-4378-9272-9678b437e84a
ms.openlocfilehash: 8675d9c3b202200c89e12e7a5f51a19d9e3e0e64
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409468"
---
# <a name="namespace-or-type-specified-in-the-imports-qualifiedelementname-doesnt-contain-any-public-member-or-cannot-be-found"></a>Przestrzeń nazw lub typ określone w elemencie Imports „\<qualifiedelementname>” nie zawierają żadnego członka publicznego lub nie można go odnaleźć

Przestrzeń nazw lub typ określony w elemencie Imports " \<qualifiedelementname> " nie zawiera żadnej publicznej składowej lub nie można jej znaleźć. Upewnij się, że przestrzeń nazw lub typ jest zdefiniowany i zawiera co najmniej jedną publiczną składową. Upewnij się, że Nazwa aliasu nie zawiera innych aliasów.

`Imports`Instrukcja określa element zawierający, którego nie można odnaleźć lub nie definiuje żadnych `Public` elementów członkowskich.

*Element zawierający* może być przestrzenią nazw, klasą, strukturą, modułem, interfejsem lub wyliczeniem. Element zawierający zawiera elementy członkowskie, takie jak zmienne, procedury lub inne elementy zawierające.

Celem importowania jest umożliwienie kodowi dostępu do przestrzeni nazw lub typów elementów członkowskich bez konieczności kwalifikowania się do nich. W projekcie może być również konieczne dodanie odwołania do przestrzeni nazw lub typu. Aby uzyskać więcej informacji, zobacz "Importowanie zawierających elementy" w [odniesieniu do zadeklarowanych elementów](../../programming-guide/language-features/declared-elements/references-to-declared-elements.md).

Jeśli kompilator nie może znaleźć określonego elementu zawierającego, wówczas nie może rozpoznać odwołań, które go używają. Jeśli odnajdzie element, ale element nie ujawnia żadnych `Public` elementów członkowskich, odwołanie nie może się powieść. W obu przypadkach nie ma znaczenia, aby zaimportować element.

Należy pamiętać, że w przypadku zaimportowania elementu zawierającego i przypisania do niego aliasu importu nie można użyć tego aliasu importu do zaimportowania innego elementu. Poniższy kod generuje błąd kompilatora.

```vb
Imports winfrm = System.Windows.Forms

' The following statement is INVALID  because it reuses an import alias.

Imports behave = winfrm.Design.Behavior`
```

**Identyfikator błędu:** BC40056

## <a name="to-correct-this-error"></a>Aby poprawić ten błąd

1. Sprawdź, czy element zawierający jest dostępny z projektu.

2. Sprawdź, czy Specyfikacja elementu zawierającego nie zawiera żadnego aliasu importu z innego importu.

3. Sprawdź, czy zawierający element uwidacznia co najmniej jeden `Public` element członkowski.

## <a name="see-also"></a>Zobacz też

- [Imports — Instrukcja (.NET Namespace i Type)](../statements/imports-statement-net-namespace-and-type.md)
- [Namespace — Instrukcja](../statements/namespace-statement.md)
- [Społeczeństwo](../modifiers/public.md)
- [Przestrzenie nazw w Visual Basic](../../programming-guide/program-structure/namespaces.md)
- [Odwołania do elementów zadeklarowanych](../../programming-guide/language-features/declared-elements/references-to-declared-elements.md)
