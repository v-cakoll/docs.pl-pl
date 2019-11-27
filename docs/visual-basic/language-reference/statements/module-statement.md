---
title: Module — Instrukcja
ms.date: 07/20/2015
f1_keywords:
- Module
- vb.Module
helpviewer_keywords:
- modules, classes
- modules
- Module statement [Visual Basic]
- modules, declaring
- standard modules
- classes [Visual Basic], vs. modules
- declarations [Visual Basic], modules
ms.assetid: a1243afc-14a5-45df-95d5-51118aeac362
ms.openlocfilehash: 56fc4f9383f1fc4779358ef18a4e5c611d897eda
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348018"
---
# <a name="module-statement"></a>Module — Instrukcja

Deklaruje nazwę modułu i wprowadza definicje zmiennych, właściwości, zdarzeń i procedur, z których składa się moduł.

## <a name="syntax"></a>Składnia

```vb
[ <attributelist> ] [ accessmodifier ]  Module name
    [ statements ]
End Module
```

## <a name="parts"></a>Części

`attributelist`  
Opcjonalna. Zobacz [listę atrybutów](../../../visual-basic/language-reference/statements/attribute-list.md).

`accessmodifier`  
Opcjonalna. Może to być jeden z następujących modyfikatorów dostępu:

- [Public](../../../visual-basic/language-reference/modifiers/public.md)

- [Friend](../../../visual-basic/language-reference/modifiers/friend.md)

Zobacz [poziomy dostępu w Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).

`name`  
Wymagana. Nazwa tego modułu. Zobacz [zadeklarowane nazwy elementów](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).

`statements`  
Opcjonalna. Instrukcje, które definiują zmienne, właściwości, zdarzenia, procedury i zagnieżdżone typy tego modułu.

`End Module`  
Kończy definicję `Module`.

## <a name="remarks"></a>Uwagi

Instrukcja `Module` definiuje typ referencyjny, który jest dostępny w całej przestrzeni nazw. *Moduł* (czasami nazywany *modułem standardowym*) jest podobny do klasy, ale z istotnymi różnicami. Każdy moduł ma dokładnie jedno wystąpienie i nie trzeba go tworzyć ani przypisywać do zmiennej. Moduły nie obsługują dziedziczenia ani implementacji interfejsów. Należy zauważyć, że moduł nie jest *typem* w sensie, że Klasa lub struktura to — nie można zadeklarować elementu programistycznego w taki sposób, aby miał typ danych modułu.

`Module` można używać tylko na poziomie przestrzeni nazw. Oznacza to, że *kontekst deklaracji* dla modułu musi być plikiem źródłowym lub przestrzenią nazw i nie może być klasą, strukturą, modułem, interfejsem, procedurą lub blokiem. Nie można zagnieździć modułu w innym module ani żadnym typie. Aby uzyskać więcej informacji, zobacz [konteksty deklaracji i domyślne poziomy dostępu](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).

Moduł ma ten sam okres istnienia co program. Ponieważ wszyscy członkowie są `Shared`, mają także okresy istnienia równe tym programowi.

Moduły domyślnie mają dostęp do [znajomych](../../../visual-basic/language-reference/modifiers/friend.md) . Poziomy dostępu modułów można dostosować za pomocą modyfikatorów dostępu. Aby uzyskać więcej informacji, zobacz [poziomy dostępu w Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).

Wszystkie elementy członkowskie modułu są niejawnie `Shared`.

## <a name="classes-and-modules"></a>Klasy i moduły

Te elementy mają wiele podobieństw, ale istnieją pewne istotne różnice.

- **Terminologia.** Poprzednie wersje Visual Basic rozpoznają dwa typy modułów: *moduły klasy* (pliki. CLS) i *moduły standardowe* (pliki. bas). Bieżąca wersja wywołuje odpowiednio te *klasy* i *moduły*.

- **Udostępnione elementy członkowskie.** Można określić, czy udostępniany jest element członkowski klasy czy wystąpienia.

- **Orientacja obiektu.** Klasy są zorientowane obiektowo, a moduły nie. Dlatego jako obiekty można tworzyć tylko wystąpienia klas. Aby uzyskać więcej informacji, zobacz [obiekty i klasy](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md).

## <a name="rules"></a>Reguły

- **Modyfikatory.** Wszystkie elementy członkowskie modułu są niejawnie [udostępniane](../../../visual-basic/language-reference/modifiers/shared.md). Nie można użyć słowa kluczowego `Shared` podczas deklarowania elementu członkowskiego i nie można zmienić stanu udostępnionego żadnego elementu członkowskiego.

- **Strukturze.** Moduł nie może dziedziczyć po żadnym typie innym niż <xref:System.Object>, z którego dziedziczy wszystkie moduły. W szczególności jeden moduł nie może dziedziczyć z innego.

  Nie można użyć [instrukcji Inherits](../../../visual-basic/language-reference/statements/inherits-statement.md) w definicji modułu, nawet w celu określenia <xref:System.Object>.

- **Właściwość domyślna.** Nie można definiować żadnych właściwości domyślnych w module. Aby uzyskać więcej informacji, zobacz [domyślne](../../../visual-basic/language-reference/modifiers/default.md).

## <a name="behavior"></a>Zachowanie

- **Poziom dostępu.** W module można zadeklarować każdego członka z własnym poziomem dostępu. Członkowie modułów domyślnie mają dostęp [publiczny](../../../visual-basic/language-reference/modifiers/public.md) , z wyjątkiem zmiennych i stałych, które domyślnie są dostępem [prywatnym](../../../visual-basic/language-reference/modifiers/private.md) . Gdy moduł ma więcej ograniczony dostęp niż jeden z jego składowych, pierwszeństwo ma określony poziom dostępu do modułu.

- **Scope.** Moduł znajduje się w zakresie w całej przestrzeni nazw.

  Każdy element członkowski modułu jest zakresem całego modułu. Zwróć uwagę, że wszyscy członkowie przechodzą *promocję typu*, co powoduje, że ich zakres zostanie podwyższony do przestrzeni nazw zawierającej moduł. Aby uzyskać więcej informacji, zobacz [Promocja typu](../../../visual-basic/programming-guide/language-features/declared-elements/type-promotion.md).

- **Branego.** W projekcie może istnieć wiele modułów i można zadeklarować składowe o tej samej nazwie w co najmniej dwóch modułach. Należy jednak zakwalifikować każde odwołanie do takiego elementu członkowskiego z odpowiednią nazwą modułu, jeśli odwołanie pochodzi spoza tego modułu. Aby uzyskać więcej informacji, zobacz [odwołania do zadeklarowanych elementów](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).

## <a name="example"></a>Przykład

[!code-vb[VbVbalrStatements#69](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#69)]

## <a name="see-also"></a>Zobacz także

- [Class, instrukcja](../../../visual-basic/language-reference/statements/class-statement.md)
- [Namespace, instrukcja](../../../visual-basic/language-reference/statements/namespace-statement.md)
- [Structure, instrukcja](../../../visual-basic/language-reference/statements/structure-statement.md)
- [Interface, instrukcja](../../../visual-basic/language-reference/statements/interface-statement.md)
- [Property, instrukcja](../../../visual-basic/language-reference/statements/property-statement.md)
- [Promocja typu](../../../visual-basic/programming-guide/language-features/declared-elements/type-promotion.md)
