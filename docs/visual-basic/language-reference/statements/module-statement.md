---
title: "Module — Instrukcja"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
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
caps.latest.revision: "24"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 92cdcd1919f21243118108da3bc382ea5d954130
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="module-statement"></a>Module — Instrukcja

Deklaruje nazwę modułu i wprowadza definicje zmiennych, właściwości, zdarzeń i procedur, z których składa się moduł.

## <a name="syntax"></a>Składnia

```vb
[ <listaatrybutów> ] [ modyfikatordostępu ]  Module nazwa
    [ instrukcje ]
End Module
```

## <a name="parts"></a>Części

 `listaatrybutów`
 Opcjonalna. Zobacz [listę atrybutów](../../../visual-basic/language-reference/statements/attribute-list.md).

 `modyfikatordostępu`
Opcjonalny. Może to być jeden z następujących:

- [Public](../../../visual-basic/language-reference/modifiers/public.md)

- [Friend](../../../visual-basic/language-reference/modifiers/friend.md)

 Zobacz [poziomy dostępu w Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).

 `nazwa`
 Wymagana. Nazwa tego modułu. Zobacz [zadeklarowane nazwy elementów](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).

 `instrukcje`
 Opcjonalny. Instrukcje, które definiują zmienne, właściwości, zdarzenia, procedury i zagnieżdżone typy tego modułu.

 `End Module`
 Kończy definicję `Module`.

## <a name="remarks"></a>Uwagi

 Instrukcja `Module` definiuje typ referencyjny, dostępny w całej przestrzeni nazw. *Moduł* (nazywany również *modułem standardowym*) jest podobny do klasy, ale z pewnymi istotnymi różnicami. Każdy moduł ma dokładnie jedno wystąpienie i nie trzeba go tworzyć ani przypisywać do zmiennej. Moduły nie obsługują dziedziczenia lub implementacji interfejsów. Należy zauważyć, że moduł nie jest *typem* w sensie, w jakim są klasy lub struktury — nie można zadeklarować elementu programowania, który będzie miał typ danych modułu.

 Można użyć `Module` tylko na poziomie przestrzeni nazw. Oznacza to, że *kontekst deklaracji* modułu musi być plikiem źródłowym lub przestrzenią nazw i nie może być klasą, strukturą, modułem, interfejsem, procedurą lub blokiem. Nie można zagnieździć modułu w innym module lub jakimkolwiek typie. Aby uzyskać więcej informacji, zobacz [Kontekst deklaracji i domyślne poziomy dostępu](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).

 Moduł ma ten sam czas istnienia co Twój program. Ponieważ wszystkie jego elementy członkowskie są typu `Shared`, one także mają okresy istnienia takie same jak program.

 Domyślnie moduły mają typ dostępu [Friend](../../../visual-basic/language-reference/modifiers/friend.md). Można dostosować ich poziomy dostępu za pomocą modyfikatorów dostępu. Aby uzyskać więcej informacji, zobacz [Poziomy dostępu w Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).

 Wszystkie elementy członkowskie modułu są niejawnie `Shared`.

## <a name="classes-and-modules"></a>Klasy i moduły

 Te elementy mają wiele podobieństw, ale istnieje kilka istotnych różnic.

- **Terminologia.** Poprzednie wersje programu Visual Basic rozpoznają dwa typy modułów: *moduły klas* (pliki .cls) i *standardowe moduły* (pliki .bas). Bieżąca wersja wywołuje odpowiednio *klasy* i *moduły*.

- **Udostępniane elementy członkowskie.** Można kontrolować, czy udostępniony jest element członkowski klasy, czy wystąpienie elementu członkowskiego.

- **Orientacja obiektowa.** Klasy są zorientowane obiektowo, ale moduły nie są. Więc tylko klasy mogą być tworzone jako obiekty. Aby uzyskać więcej informacji, zobacz [Obiekty i klasy](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md).

## <a name="rules"></a>Reguły

- **Modyfikatory.** Wszyscy członkowie modułu są niejawnie [Shared](../../../visual-basic/language-reference/modifiers/shared.md). Nie można użyć `Shared` — słowo kluczowe podczas deklarowania elementem członkowskim i nie można zmienić udostępniony stan dowolnego elementu członkowskiego.  

- **Dziedziczenie.** Moduł nie może dziedziczyć z dowolnego typu innego niż <xref:System.Object>, z których wszystkie moduły dziedziczyć. W szczególności jeden moduł nie może dziedziczyć z innego.

Nie można użyć [dziedziczy instrukcję](../../../visual-basic/language-reference/statements/inherits-statement.md) w definicji modułu, nawet do określenia <xref:System.Object>.

-   **Domyślna właściwość.** Nie można zdefiniować żadnych właściwości domyślne w module. Aby uzyskać więcej informacji, zobacz [domyślne](../../../visual-basic/language-reference/modifiers/default.md).  

## <a name="behavior"></a>Zachowanie

-   **Poziom dostępu.** W module mogą zadeklarować każdy element członkowski z poziomu dostępu. Domyślnie moduł członków [publicznego](../../../visual-basic/language-reference/modifiers/public.md) uzyskać dostęp, z wyjątkiem zmienne i stałe, które domyślnie [prywatnej](../../../visual-basic/language-reference/modifiers/private.md) dostępu. Gdy moduł ograniczył dostęp więcej niż jeden z jego elementów członkowskich, pierwszeństwo ma poziom dostępu do określonego modułu.  

- **Zakres.** Moduł jest w zakresie w całym ich nazw.

     Zakres każdego elementu modułu jest cały moduł. Należy zauważyć, że wszystkie elementy członkowskie przejście *wpisz podwyższania poziomu*, co powoduje, że ich zakres się dopiero przestrzeni nazw zawierającej modułu. Aby uzyskać więcej informacji, zobacz [promocja typu](../../../visual-basic/programming-guide/language-features/declared-elements/type-promotion.md).

- **Kwalifikacji.** Może mieć wiele modułów w projekcie i można zadeklarować elementów członkowskich o tej samej nazwie w co najmniej dwa moduły. Jednak jeśli odwołanie jest z poza ten moduł muszą kwalifikować się wszystkich odwołań do takiego elementu członkowskiego o nazwie odpowiedniego modułu. Aby uzyskać więcej informacji, zobacz [odwołania do elementów zadeklarowany](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).
  
## <a name="example"></a>Przykład

 [!code-vb[VbVbalrStatements#69](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/module-statement_1.vb)]
  
## <a name="see-also"></a>Zobacz też

 [Class — instrukcja](../../../visual-basic/language-reference/statements/class-statement.md)
 [Namespace — instrukcja](../../../visual-basic/language-reference/statements/namespace-statement.md)
 [Structure — instrukcja](../../../visual-basic/language-reference/statements/structure-statement.md)
 [Interface — instrukcja](../../../visual-basic/language-reference/statements/interface-statement.md)
 [Property — instrukcja](../../../visual-basic/language-reference/statements/property-statement.md)
 [Promocja typu](../../../visual-basic/programming-guide/language-features/declared-elements/type-promotion.md)
