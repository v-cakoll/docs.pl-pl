---
title: Structure — Instrukcja (Visual Basic)
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
ms.openlocfilehash: ac128e257269ca301400bd8b294539d1ec836cab
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/29/2019
ms.locfileid: "73038617"
---
# <a name="structure-statement"></a>Structure — Instrukcja

Deklaruje nazwę struktury i wprowadza definicje zmiennych, właściwości, zdarzeń i procedur, które składają się na strukturę.

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
|`accessmodifier`|Opcjonalny. Może być jedną z następujących czynności:<br /><br /> -   [Public](../modifiers/public.md)<br />-   [Ochrona](../modifiers/protected.md)<br />-   [Friend](../modifiers/friend.md)<br />-   [Private](../modifiers/private.md)<br />- [chroniony znajomy](../modifiers/protected-friend.md)<br/>- [Private Protected](../modifiers/private-protected.md) <br /><br /> Zobacz [poziomy dostępu w Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md).|
|`Shadows`|Opcjonalny. Zobacz [Shadows](../modifiers/shadows.md).|
|`Partial`|Opcjonalny. Wskazuje częściową definicję struktury. Zobacz [częściowy](../modifiers/partial.md).|
|`name`|Wymagany. Nazwa tej struktury. Zobacz [zadeklarowane nazwy elementów](../../programming-guide/language-features/declared-elements/declared-element-names.md).|
|`Of`|Opcjonalny. Określa, że jest to struktura generyczna.|
|`typelist`|Wymagane [w przypadku użycia słowa](of-clause.md) kluczowego. Lista parametrów typu dla tej struktury. Zobacz [Lista typów](type-list.md).|
|`Implements`|Opcjonalny. Wskazuje, że ta struktura implementuje elementy członkowskie jednego lub większej liczby interfejsów. Zobacz [instrukcja Implements](implements-statement.md).|
|`interfacenames`|Wymagane, jeśli używasz instrukcji `Implements`. Nazwy interfejsów implementowanych przez tę strukturę.|
|`datamemberdeclarations`|Wymagany. Zero lub więcej instrukcji `Const`, `Dim`, `Enum` lub `Event` deklarujących *składowe danych* struktury.|
|`methodmemberdeclarations`|Opcjonalny. Zero lub więcej deklaracji procedur `Function`, `Operator`, `Property` lub `Sub`, które służą jako *elementy składowe metody* struktury.|
|`End Structure`|Wymagany. Kończy definicję `Structure`.|

## <a name="remarks"></a>Uwagi

Instrukcja `Structure` definiuje złożony typ wartości, który można dostosować. *Struktura* jest generalizacją typu zdefiniowanego przez użytkownika (UDT) poprzednich wersji Visual Basic. Aby uzyskać więcej informacji, zobacz [struktury](../../programming-guide/language-features/data-types/structures.md).

Struktury obsługują wiele z tych samych funkcji co klasy. Na przykład struktury mogą mieć właściwości i procedury, które mogą implementować interfejsy i mogą mieć sparametryzowane konstruktory. Istnieją jednak znaczące różnice między strukturami i klasami w obszarach takich jak dziedziczenie, deklaracje i użycie. Ponadto klasy są typami odwołań, a struktury są typami wartości. Aby uzyskać więcej informacji, zobacz [struktury i klasy](../../programming-guide/language-features/data-types/structures-and-classes.md).

`Structure` można używać tylko na poziomie przestrzeni nazw lub modułu. Oznacza to, że *kontekst deklaracji* dla struktury musi być plikiem źródłowym, przestrzenią nazw, klasą, strukturą, modułem lub interfejsem i nie może być procedurą ani blokiem. Aby uzyskać więcej informacji, zobacz [konteksty deklaracji i domyślne poziomy dostępu](declaration-contexts-and-default-access-levels.md).

Struktury są domyślne dla [zaprzyjaźnionego](../modifiers/friend.md) dostępu. Możesz dostosować ich poziomy dostępu za pomocą modyfikatorów dostępu. Aby uzyskać więcej informacji, zobacz [poziomy dostępu w Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md).

## <a name="rules"></a>Przepisy

- **Zagnieżdżania.** Można zdefiniować jedną strukturę w innej. Struktura zewnętrzna jest nazywana *strukturą zawierającą*, a wewnętrzną strukturę nazywa się *zagnieżdżoną strukturą*. Nie można jednak uzyskać dostępu do elementów członkowskich struktury zagnieżdżonej za pomocą struktury zawierającej. Zamiast tego należy zadeklarować zmienną typu danych struktury zagnieżdżonej.

- **Deklaracja elementu członkowskiego.** Należy zadeklarować każdy element członkowski struktury. Składowa struktury nie może być [chroniona](../modifiers/protected.md) ani `Protected Friend`, ponieważ żadne elementy nie mogą dziedziczyć ze struktury. Sama struktura może być jednak `Protected` lub `Protected Friend`.
  
     Można zadeklarować zero lub więcej zmiennych nieudostępnionych lub nieudostępnianych, niestandardowych zdarzeń w strukturze. Nie mogą istnieć tylko stałe, właściwości i procedury, nawet jeśli niektóre z nich są nieudostępnione.

- **Zainicjować.** Nie można zainicjować wartości dowolnego elementu członkowskiego danych nieudostępnionej struktury w ramach swojej deklaracji. Konieczne jest zainicjowanie takiego elementu członkowskiego danych za pomocą konstruktora sparametryzowanego dla struktury lub przypisanie wartości do elementu członkowskiego po utworzeniu wystąpienia struktury.

- **Strukturze.** Struktura nie może dziedziczyć z żadnego typu innego niż <xref:System.ValueType>, z którego dziedziczą wszystkie struktury. W szczególności jedna struktura nie może dziedziczyć z innego.

     Nie można użyć [instrukcji Inherits](inherits-statement.md) w definicji struktury, nawet w celu określenia <xref:System.ValueType>.

- **Realizacji.** Jeśli struktura używa [instrukcji Implements](implements-statement.md), należy zaimplementować każdy element członkowski zdefiniowany przez każdy interfejs określony w `interfacenames`.

- **Właściwość domyślna.** Struktura może określać najwyżej jedną właściwość jako *Właściwość domyślną*, używając modyfikatora [domyślnego](../modifiers/default.md) . Aby uzyskać więcej informacji, zobacz [domyślne](../modifiers/default.md).

## <a name="behavior"></a>Zachowanie

- **Poziom dostępu.** W ramach struktury można zadeklarować każdego członka z własnym poziomem dostępu. Wszyscy członkowie struktury domyślnie mają dostęp [publiczny](../modifiers/public.md) . Należy pamiętać, że jeśli sama struktura ma bardziej ograniczony poziom dostępu, to automatycznie ogranicza dostęp do jej elementów członkowskich, nawet jeśli dostosowujesz ich poziomy dostępu za pomocą modyfikatorów dostępu.

- **Scope.** Struktura znajduje się w zakresie, w której znajduje się przestrzeń nazw, Klasa, struktura lub moduł.

     Zakres każdego elementu członkowskiego struktury to cała struktura.

- **Okres istnienia.** Struktura nie jest sama przez okres istnienia. Zamiast tego każde wystąpienie tej struktury ma okres istnienia niezależny od wszystkich innych wystąpień.

     Okres istnienia wystąpienia rozpoczyna się, gdy jest on tworzony przez [nową](../operators/new-operator.md) klauzulę operatora. Koniec okresu istnienia zmiennej, która go skończy.

     Nie można zwiększyć okresu istnienia wystąpienia struktury. Przeprzybliżanie do funkcji struktury statycznej jest zapewniane przez moduł. Aby uzyskać więcej informacji, zobacz [moduł instrukcja](module-statement.md).

     Elementy członkowskie struktury mają okresy istnienia, w zależności od tego, jak i gdzie są zgłaszane. Aby uzyskać więcej informacji, zobacz "okres istnienia" w [instrukcji klasy](class-statement.md).

- **Branego.** Kod poza strukturą musi kwalifikować się do nazwy składowej o nazwie tej struktury.

     Jeśli kod wewnątrz struktury zagnieżdżonej sprawia, że niekwalifikowane odwołanie do elementu programistycznego, Visual Basic wyszukuje element jako pierwszy w strukturze zagnieżdżonej, a następnie w strukturze zawierającej i tak dalej, jak najbardziej zewnętrzny element zawierający. Aby uzyskać więcej informacji, zobacz [odwołania do zadeklarowanych elementów](../../programming-guide/language-features/declared-elements/references-to-declared-elements.md).

- **Użycie pamięci.** Podobnie jak w przypadku wszystkich złożonych typów danych, nie można bezpiecznie obliczyć całkowitego zużycia pamięci przez dodanie do nich nominalnych przydziałów pamięci masowej. Ponadto nie można bezpiecznie założyć, że kolejność przechowywania w pamięci jest taka sama jak w przypadku kolejności deklaracji. Jeśli konieczne jest kontrolowanie układu pamięci masowej struktury, można zastosować atrybut <xref:System.Runtime.InteropServices.StructLayoutAttribute> do instrukcji `Structure`.

## <a name="example"></a>Przykład

Poniższy przykład używa instrukcji `Structure`, aby zdefiniować zestaw powiązanych danych dla pracownika. Przedstawia on użycie `Public`, `Friend` i `Private` elementów członkowskich, aby odzwierciedlić czułość elementów danych. Pokazuje również procedury, właściwości i składowe zdarzeń.

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
