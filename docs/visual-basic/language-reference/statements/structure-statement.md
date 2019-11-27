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
ms.openlocfilehash: 120f836b9d49c00e9c53af0d1fc832e22c8cbbb8
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346456"
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
|`attributelist`|Opcjonalny. Zobacz [listę atrybutów](attribute-list.md).|
|`accessmodifier`|Opcjonalny. Może to być jeden z następujących modyfikatorów dostępu:<br /><br /> -   [publiczny](../modifiers/public.md)<br />-   [chronione](../modifiers/protected.md)<br />-   [znajomy](../modifiers/friend.md)<br />-   [prywatny](../modifiers/private.md)<br />- [chronionego przyjaciela](../modifiers/protected-friend.md)<br/>- [prywatnej ochrony](../modifiers/private-protected.md) <br /><br /> Zobacz [poziomy dostępu w Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md).|
|`Shadows`|Opcjonalny. Zobacz [Shadows](../modifiers/shadows.md).|
|`Partial`|Opcjonalny. Wskazuje częściową definicję struktury. Zobacz [częściowy](../modifiers/partial.md).|
|`name`|Wymagany. Nazwa tej struktury. Zobacz [zadeklarowane nazwy elementów](../../programming-guide/language-features/declared-elements/declared-element-names.md).|
|`Of`|Opcjonalny. Określa, że jest to struktura generyczna.|
|`typelist`|Wymagane [w przypadku użycia słowa](of-clause.md) kluczowego. Lista parametrów typu dla tej struktury. Zobacz [Lista typów](type-list.md).|
|`Implements`|Opcjonalny. Wskazuje, że ta struktura implementuje składowe jednego lub więcej interfejsów. Zobacz [instrukcja Implements](implements-statement.md).|
|`interfacenames`|Wymagane, jeśli używasz instrukcji `Implements`. Nazwy interfejsów, które implementuje ta struktura.|
|`datamemberdeclarations`|Wymagany. Zero lub więcej instrukcji `Const`, `Dim`, `Enum`lub `Event` deklarujących *składowe danych* struktury.|
|`methodmemberdeclarations`|Opcjonalny. Zero lub więcej deklaracji procedur `Function`, `Operator`, `Property`lub `Sub`, które służą jako *elementy składowe metody* struktury.|
|`End Structure`|Wymagany. Kończy definicję `Structure`.|

## <a name="remarks"></a>Uwagi

Instrukcja `Structure` definiuje złożony typ wartości, który można dostosować. *Struktura* jest generalizacją typu zdefiniowanego przez użytkownika (UDT) poprzednich wersji Visual Basic. Aby uzyskać więcej informacji, zobacz [struktury](../../programming-guide/language-features/data-types/structures.md).

Struktury obsługują wiele tych samych funkcji co klasy. Na przykład struktury mogą mieć właściwości i procedury, mogą implementować interfejsy i mogą mieć sparametryzowane konstruktory. Istnieją jednak istotne różnice między strukturami i klasami w obszarach takich jak: dziedziczenia, deklaracje i użycie. Ponadto klasy to typy referencyjne, a struktury to typy wartościowe. Aby uzyskać więcej informacji, zobacz [struktury i klasy](../../programming-guide/language-features/data-types/structures-and-classes.md).

`Structure` można używać tylko na poziomie przestrzeni nazw lub modułu. Oznacza to, że *kontekst deklaracji* dla struktury musi być plikiem źródłowym, przestrzenią nazw, klasą, strukturą, modułem lub interfejsem i nie może być procedurą ani blokiem. Aby uzyskać więcej informacji, zobacz [konteksty deklaracji i domyślne poziomy dostępu](declaration-contexts-and-default-access-levels.md).

Struktury są domyślne dla [zaprzyjaźnionego](../modifiers/friend.md) dostępu. Poziomy dostępu modułów można dostosować za pomocą modyfikatorów dostępu. Aby uzyskać więcej informacji, zobacz [poziomy dostępu w Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md).

## <a name="rules"></a>Reguły

- **Zagnieżdżania.** Można zdefiniować jedną strukturę wewnątrz innej. Struktura zewnętrzna jest nazywana *strukturą zawierającą*, a wewnętrzną strukturę nazywa się *zagnieżdżoną strukturą*. Jednak nie można uzyskać dostępu do składowych struktury zagnieżdżonej za pośrednictwem struktury zawierającej. Zamiast tego należy zadeklarować zmienną typu danych struktury zagnieżdżonej.

- **Deklaracja elementu członkowskiego.** Musisz zadeklarować każdą składową struktury. Składowa struktury nie może być [chroniona](../modifiers/protected.md) ani `Protected Friend`, ponieważ żadne elementy nie mogą dziedziczyć ze struktury. Sama struktura może być jednak `Protected` lub `Protected Friend`.
  
     Można zadeklarować nieudostępnione zmienne lub nieudostępnione niestandardowe zdarzenia w strukturze lub nie deklarować ich wcale. Nie mogą istnieć tylko stałe, właściwości i procedury, nawet jeśli niektóre z nich są nieudostępnione.

- **Zainicjować.** Nie można zainicjować wartości żadnej składowej danych nieudostępnionych struktury w części jej deklaracji. Musisz zainicjować składową danych za pomocą konstruktora sparametryzowanego struktury lub przypisać wartość do składowej po utworzeniu wystąpienia struktury.

- **Strukturze.** Struktura nie może dziedziczyć z żadnego typu innego niż <xref:System.ValueType>, z którego dziedziczą wszystkie struktury. W szczególności jedna struktura nie może dziedziczyć z innej.

     Nie można użyć [instrukcji Inherits](inherits-statement.md) w definicji struktury, nawet w celu określenia <xref:System.ValueType>.

- **Realizacji.** Jeśli struktura używa [instrukcji Implements](implements-statement.md), należy zaimplementować każdy element członkowski zdefiniowany przez każdy interfejs określony w `interfacenames`.

- **Właściwość domyślna.** Struktura może określać najwyżej jedną właściwość jako *Właściwość domyślną*, używając modyfikatora [domyślnego](../modifiers/default.md) . Aby uzyskać więcej informacji, zobacz [domyślne](../modifiers/default.md).

## <a name="behavior"></a>Zachowanie

- **Poziom dostępu.** W ramach struktury można zadeklarować każdą składową z własnym poziomem dostępu. Wszyscy członkowie struktury domyślnie mają dostęp [publiczny](../modifiers/public.md) . Należy pamiętać, że jeśli struktura ma bardziej ograniczony poziom dostępu, automatycznie ogranicza to dostęp do jej składowych, nawet jeśli dostosujesz ich poziomy dostępu za pomocą modyfikatorów dostępu.

- **Scope.** Struktura jest w zakresie zawierającej ją przestrzeni nazw, klasy, struktury lub modułu.

     Zakresem każdej składowej struktury jest cała struktura.

- **Okres istnienia.** Sama struktura nie ma okresu istnienia. Ale każde wystąpienie struktury ma okres istnienia niezależny od innych wystąpień.

     Okres istnienia wystąpienia rozpoczyna się, gdy jest on tworzony przez [nową](../operators/new-operator.md) klauzulę operatora. Kończy się po zakończeniu okresu istnienia zmiennej, która odpowiada za zakończenie.

     Nie można wydłużyć okresu istnienia instancji struktury. Funkcjonalność zbliżona do struktury statycznej jest udostępniania przez moduł. Aby uzyskać więcej informacji, zobacz [moduł instrukcja](module-statement.md).

     Składowe struktury mają okresy istnienia zależne od tego, jak i gdzie są zadeklarowane. Aby uzyskać więcej informacji, zobacz "okres istnienia" w [instrukcji klasy](class-statement.md).

- **Branego.** Kod spoza struktury musi kwalifikować nazwę składowej z nazwą tej struktury.

     Jeśli kod wewnątrz struktury zagnieżdżonej wykonuje niekwalifikowane odwołanie do elementu programistycznego, program Visual Basic wyszukuje element najpierw w strukturze zagnieżdżonej, następnie w strukturze zawierającej i tak dalej do najbardziej zewnętrznego elementu zawierającego. Aby uzyskać więcej informacji, zobacz [odwołania do zadeklarowanych elementów](../../programming-guide/language-features/declared-elements/references-to-declared-elements.md).

- **Użycie pamięci.** Podobnie jak w przypadku wszystkich złożonych typów danych, nie można bezpiecznie obliczyć łącznego zużycia pamięci przez strukturę, dodając do siebie nominalne alokacje magazynu jej składowych. Ponadto nie można bezpiecznie założyć, że kolejność magazynowania w pamięci jest taka sama jak kolejność deklaracji. Jeśli konieczne jest kontrolowanie układu pamięci masowej struktury, można zastosować atrybut <xref:System.Runtime.InteropServices.StructLayoutAttribute> do instrukcji `Structure`.

## <a name="example"></a>Przykład

Poniższy przykład używa instrukcji `Structure`, aby zdefiniować zestaw powiązanych danych dla pracownika. Przedstawia on użycie `Public`, `Friend`i `Private` elementów członkowskich, aby odzwierciedlić czułość elementów danych. Przedstawione są także składowe procedury, właściwości i zdarzenia.

[!code-vb[VbVbalrStatements#57](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#57)]

Aby uzyskać więcej informacji na temat używania `Structure`s, zobacz [Zmienna struktury](../../programming-guide/language-features/data-types/structure-variables.md).

## <a name="see-also"></a>Zobacz także

- [Class, instrukcja](class-statement.md)
- [Interface, instrukcja](interface-statement.md)
- [Module, instrukcja](module-statement.md)
- [Dim, instrukcja](dim-statement.md)
- [Const, instrukcja](const-statement.md)
- [Enum, instrukcja](enum-statement.md)
- [Event, instrukcja](event-statement.md)
- [Operator, instrukcja](operator-statement.md)
- [Property, instrukcja](property-statement.md)
- [Struktury i klasy](../../programming-guide/language-features/data-types/structures-and-classes.md)
