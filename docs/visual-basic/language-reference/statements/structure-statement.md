---
title: Structure — Instrukcja
ms.date: 05/12/2018
f1_keywords:
- vb.Structure
- Structure
helpviewer_keywords:
- user-defined types [Visual Basic], Structure statement
- compound data types [Visual Basic]
- Structure keyword [Visual Basic]
- Structure statement [Visual Basic]
- UDT (user-defined types)
- types [Visual Basic], user-defined
ms.assetid: 9bd1deea-2a89-4cdc-812c-6dcbb947c391
ms.openlocfilehash: 6fdc4f1d2fbd40689c76a15a5a35b25522138be6
ms.sourcegitcommit: 22c3c8f74eaa138dbbbb02eb7d720fce87fc30a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/17/2018
ms.locfileid: "34234468"
---
# <a name="structure-statement"></a>Structure — Instrukcja
Deklaruje nazwę struktury i wprowadza definicje zmiennych, właściwości, zdarzeń i procedur, które obejmuje struktura.

## <a name="syntax"></a>Składnia

```vb
[ <attributelist> ] [ accessmodifier ] [ Shadows ] [ Partial ] _
Structure name [ ( Of typelist ) ]
[ Implements interfacenames ]
[ datamemberdeclarations ]
[ methodmemberdeclarations ]
End Structure
```

## <a name="parts"></a>Części

|Termin|Definicja|
|---|---|
|`attributelist`|Opcjonalne. Zobacz temat [Lista atrybutów](../../../visual-basic/language-reference/statements/attribute-list.md).|
|`accessmodifier`|Opcjonalne. Może to być jeden z następujących elementów:<br /><br /> - [Public](../../../visual-basic/language-reference/modifiers/public.md)<br />- [Protected](../../../visual-basic/language-reference/modifiers/protected.md)<br />- [Friend](../../../visual-basic/language-reference/modifiers/friend.md)<br />- [Private](../../../visual-basic/language-reference/modifiers/private.md)<br />- [Protected Friend](../../language-reference/modifiers/protected-friend.md)<br/>- [Private protected](../../language-reference/modifiers/private-protected.md) <br /><br /> Zobacz temat [Poziomy dostępu w języku Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).|
|`Shadows`|Opcjonalne. Zobacz [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md).|
|`Partial`|Opcjonalne. Wskazuje częściową definicję struktury. Zobacz [Partial](../../../visual-basic/language-reference/modifiers/partial.md).|
|`name`|Wymagane. Nazwa tej struktury. Zobacz temat [Zadeklarowane nazwy elementów](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).|
|`Of`|Opcjonalne. Określa, że jest to struktura generyczna.|
|`typelist`|Wymagane w przypadku użycia słowa kluczowego [Of](../../../visual-basic/language-reference/statements/of-clause.md). Lista parametrów typu dla tej struktury. Zobacz [Lista typów](../../../visual-basic/language-reference/statements/type-list.md).|
|`Implements`|Opcjonalne. Wskazuje, że ta struktura implementuje jeden lub więcej członków interfejsów. Zobacz [Implements (instrukcja)](../../../visual-basic/language-reference/statements/implements-statement.md).|
|`interfacenames`|Wymagane w przypadku użycia instrukcji `Implements`. Nazwy interfejsów, które implementuje ta struktura.|
|`datamemberdeclarations`|Wymagane. Zero lub więcej instrukcji `Const`, `Dim`, `Enum`, lub `Event`, deklarujących *elementy członkowskie* struktury.|
|`methodmemberdeclarations`|Opcjonalne. Zero lub więcej deklaracji `Function`, `Operator`, `Property`, lub procedur `Sub`, które stanowią *metody członkowskie* struktury.|
|`End Structure`|Wymagane. Kończy definicję `Structure`.|

## <a name="remarks"></a>Uwagi

Instrukcja `Structure` definiuje złożony typ wartości, który można dostosować. *Struktura* jest generalizacją typu definiowanego przez użytkownika (UDT) z poprzednich wersji programu Visual Basic. Aby uzyskać więcej informacji, zobacz [struktury](../../../visual-basic/programming-guide/language-features/data-types/structures.md).
Struktury obsługują wiele tych samych zadań co klasy. Na przykład struktury mogą mieć właściwości i procedury, mogą implementować interfejsy i mogą mieć sparametryzowane konstruktory. Istnieją jednak istotne różnice między strukturami i klasami, w obszarach takich jak: dziedziczenia, deklaracje i użycie. Dodatkowo klasy to typy referencyjne, a struktury to typy wartościowe. Aby uzyskać więcej informacji, zobacz [struktury i klasy](../../../visual-basic/programming-guide/language-features/data-types/structures-and-classes.md).

`Structure` można użyć tylko na poziomie przestrzeni nazw lub modułu. Oznacza to, że *kontekstem deklaracji* struktury musi być plik źródłowy, przestrzeń nazw, klasa, struktura, moduł lub interfejs i nie może być procedura lub blok. Aby uzyskać więcej informacji, zobacz [Kontekst deklaracji i domyślne poziomy dostępu](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).

Domyślnie struktury posiadają poziom dostępu [Friend](../../../visual-basic/language-reference/modifiers/friend.md). Możesz dostosować ich poziom dostępu za pomocą modyfikatorów dostępu. Aby uzyskać więcej informacji, zobacz temat [Poziomy dostępu w języku Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).

## <a name="rules"></a>Reguły

- **Zagnieżdżanie.** Można zdefiniować jedną strukturę wewnątrz innej. Zewnętrzny element jest nazywany *strukturą zawierającą*, a struktura wewnętrzna nazywana jest *strukturą zagnieżdżoną*. Jednakże nie można uzyskać dostępu do elementów struktury zagnieżdżonej za pośrednictwem struktury zawierającej. Zamiast tego należy zadeklarować zmienną typu zagnieżdżonej struktury danych.

- **Deklaracja elementu członkowskiego.** Musisz zadeklarować każdy element członkowski struktury. Element członkowski struktury nie może być [Protected](../../../visual-basic/language-reference/modifiers/protected.md) lub `Protected Friend` ponieważ nic nie może dziedziczyć z struktury. Sama struktura jednak może być `Protected` lub `Protected Friend`.

Można zadeklarować zero lub więcej nieudostępnionych zmiennych lub nieudostępnionych standardowych zdarzeń w strukturze. Nie możesz mieć tylko stałych, właściwości i procedur, nawet jeśli niektóre z nich są nieudostępnione.

- **Inicjowanie.** Nie można zainicjować wartości któregokolwiek elementu członkowskiego danych nieudostępnionych struktury w części jej deklaracji. Musisz zainicjować element członkowski danych za pomocą sparametryzowanego konstruktora struktury, lub przypisać wartości do elementu członkowskiego po utworzeniu wystąpienia struktury.

- **Dziedziczenie.** Struktura nie może dziedziczyć z dowolnego typu innego niż <xref:System.ValueType>, z którego dziedziczą wszystkie struktury. W szczególności jedna struktura nie może dziedziczyć z innej.

 Nie można użyć [instrukcji Implements](../../../visual-basic/language-reference/statements/inherits-statement.md) w definicji struktury, nawet do określenia <xref:System.ValueType>.

- **Implementacja.** Jeśli struktura używa [instrukcji Implements](../../../visual-basic/language-reference/statements/implements-statement.md), musisz zaimplementować każdy element członkowski zdefiniowany przez każdy interfejs określony w `interfacenames`.

- **Domyślna właściwość.** Struktura może wskazać co najwyżej jedną właściwość jako jego *właściwość domyślną* za pomocą modyfikatora [Default](../../../visual-basic/language-reference/modifiers/default.md). Aby uzyskać więcej informacji, zobacz [Default](../../../visual-basic/language-reference/modifiers/default.md).

## <a name="behavior"></a>Zachowanie

- **Poziom dostępu.** W ramach struktury można zadeklarować każdy element członkowski z własnym poziomem dostępu. Domyślnie wszystkie elementy członkowskie struktury mają dostęp [Public](../../../visual-basic/language-reference/modifiers/public.md). Należy pamiętać, że jeśli struktura ma bardziej ograniczony poziom dostępu, to automatycznie ogranicza to dostęp do jej elementów członkowskich, nawet jeśli dostosujesz ich poziomy dostępu za pomocą modyfikatorów dostępu.

- **Zakres.** Struktura jest w zakresie zawierającej ją przestrzeni nazw, klasy, struktury lub modułu.

 Zakresem każdego elementu członkowskiego struktury jest cała struktura.

- **Okres istnienia.** Sama struktura nie może mieć okresu istnienia. Zamiast tego każde wystąpienie struktury ma okres istnienia niezależny od innych wystąpień.

 Okres istnienia wystąpienia rozpoczyna się, gdy jest tworzona przez [operator New](../../../visual-basic/language-reference/operators/new-operator.md). Kończy się po zakończeniu okresu istnienia zmiennej, która ją przechowuje.

 Nie można rozszerzyć okresu istnienia instancji struktury. Zbliżone do funkcjonalności struktury statycznej jest realizowane przez moduł. Aby uzyskać więcej informacji, zobacz [Module — instrukcja](../../../visual-basic/language-reference/statements/module-statement.md).

 Elementy członkowskie struktury posiadają okresy istnienia zależne od tego, jak i gdzie są zadeklarowane. Aby uzyskać więcej informacji, zobacz "Okres istnienia" w [Class — instrukcja](../../../visual-basic/language-reference/statements/class-statement.md).

- **Kwalifikacja.** Kod spoza struktury musi kwalifikować nazwę członka z nazwą tej struktury.

 Jeśli kod wewnątrz struktury zagnieżdżonej wykonuje niekwalifikowane odwołanie do elementu programistycznego, Visual Basic wyszukuje element najpierw w strukturze zagnieżdżonej, następnie w strukturze zawierającej i tak dalej do najbardziej zewnętrznego elementu zawierającego. Aby uzyskać więcej informacji, zobacz [odwołania do elementów zadeklarowanych](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).

- **Zużycie pamięci.** Podobnie jak w przypadku wszystkich złożonych typów danych, nie można bezpiecznie obliczyć wykorzystania pamięci przez strukturę poprzez dodanie nominalnej alokacji przestrzeni jej elementów członkowskich. Ponadto nie można bezpiecznie założyć, że kolejność przestrzeni w pamięci jest taka sama jak kolejność deklaracji. Jeśli potrzebujesz sterować układem przechowywania struktury, możesz zastosować atrybut <xref:System.Runtime.InteropServices.StructLayoutAttribute> w instrukcji `Structure`.

## <a name="example"></a>Przykład
 W poniższym przykładzie użyto instrukcji `Structure` do zdefiniowania zestawu powiązanych danych do pracownika. Widoczne jest użycie elementów członkowskich `Public`, `Friend` i `Private`, aby odzwierciedlić charakter elementów danych. Przedstawia on także procedury, właściwości i zdarzenia elementów członkowskich.

 [!code-vb[VbVbalrStatements#57](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/structure-statement_1.vb)]

## <a name="see-also"></a>Zobacz też
 [Class, instrukcja](../../../visual-basic/language-reference/statements/class-statement.md)
 [Interface, instrukcja](../../../visual-basic/language-reference/statements/interface-statement.md)
 [Module, instrukcja](../../../visual-basic/language-reference/statements/module-statement.md)
 [Dim, instrukcja](../../../visual-basic/language-reference/statements/dim-statement.md)
 [Const, instrukcja](../../../visual-basic/language-reference/statements/const-statement.md)
 [Enum, instrukcja](../../../visual-basic/language-reference/statements/enum-statement.md)
 [Event, instrukcja](../../../visual-basic/language-reference/statements/event-statement.md)
 [Operator, instrukcja](../../../visual-basic/language-reference/statements/operator-statement.md)
 [Property, instrukcja](../../../visual-basic/language-reference/statements/property-statement.md)
 [Struktury i klasy](../../../visual-basic/programming-guide/language-features/data-types/structures-and-classes.md)
