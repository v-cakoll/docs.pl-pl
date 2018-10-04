---
title: Module — instrukcja (Visual Basic)
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
ms.openlocfilehash: 5628224a08fe5f12cf2a81b179c4998001174354
ms.sourcegitcommit: 69229651598b427c550223d3c58aba82e47b3f82
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/04/2018
ms.locfileid: "48779877"
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
 Opcjonalna. Zobacz temat [Lista atrybutów](../../../visual-basic/language-reference/statements/attribute-list.md).  
  
 `accessmodifier`  
 Opcjonalna. Może to być jeden z następujących elementów:  
  
-   [Public](../../../visual-basic/language-reference/modifiers/public.md)  
  
-   [Friend](../../../visual-basic/language-reference/modifiers/friend.md)  
  
 Zobacz temat [Poziomy dostępu w języku Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
 `name`  
 Wymagana. Nazwa tego modułu. Zobacz temat[Zadeklarowane nazwy elementów](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).  
  
 `statements`  
 Opcjonalna. Instrukcje, które definiują zmienne, właściwości, zdarzenia, procedury i zagnieżdżone typy tego modułu.  
  
 `End Module`  
 Kończy definicję `Module`.  
  
## <a name="remarks"></a>Uwagi  
 Instrukcja `Module` definiuje typ referencyjny dostępny w całej przestrzeni nazw. *Moduł* (nazywany również *modułem standardowym*) przypomina klasę, ale z pewnymi istotnymi różnicami. Każdy moduł ma dokładnie jedno wystąpienie i nie trzeba go tworzyć ani przypisywać do zmiennej. Moduły nie obsługują dziedziczenia ani implementacji interfejsów. Ponadto moduł nie jest *typem* w takim sensie jak klasy czy struktury — nie można zadeklarować elementu programistycznego, którego typem danych będzie moduł.  
  
 Instrukcji `Module` można użyć tylko na poziomie przestrzeni nazw. Oznacza to, że *kontekst deklaracji* modułu musi być plikiem źródłowym lub przestrzenią nazw. Nie może być klasą, strukturą, modułem, interfejsem, procedurą ani blokiem. Nie można zagnieździć modułu w innym module ani żadnym typie. Aby uzyskać więcej informacji, zobacz temat [Konteksty deklaracji i domyślne poziomy dostępu](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).  
  
 Moduł ma ten sam okres istnienia co program. Ponieważ wszystkie jego elementy członkowskie są typu `Shared`, one także mają okresy istnienia takie same jak program.  
  
 Domyślnym typem dostępu modułów jest [Friend](../../../visual-basic/language-reference/modifiers/friend.md). Poziomy dostępu modułów można dostosować za pomocą modyfikatorów dostępu. Aby uzyskać więcej informacji, zobacz temat [Poziomy dostępu w języku Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
 Wszystkie elementy członkowskie modułu są niejawną kolekcją `Shared`.  
  
## <a name="classes-and-modules"></a>Klasy i moduły  
 Te elementy mają wiele wspólnego, ale istnieją pewne ważne różnice.  
  
-   **Terminologia.** Poprzednie wersje języka Visual Basic rozpoznawały dwa typy modułów: *moduły klas* (pliki .cls) i *moduły standardowe* (pliki .bas). W bieżącej wersji są one nazywane odpowiednio *klasami* i *modułami*.  
  
-   **Udostępnione elementy członkowskie.** Można określić, czy udostępniany jest element członkowski klasy czy wystąpienia.  
  
-   **Orientacja obiektowa.** Klasy są zorientowane obiektowo, a moduły nie. Dlatego jako obiekty można tworzyć tylko wystąpienia klas. Aby uzyskać więcej informacji, zobacz temat [Obiekty i klasy](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md).  
  
## <a name="rules"></a>reguły  
  
-   **Modyfikatory.** Wszystkie elementy członkowskie modułu mają niejawnie przypisany modyfikator [Shared](../../../visual-basic/language-reference/modifiers/shared.md). Nie można użyć słowa kluczowego `Shared` podczas deklarowania elementu członkowskiego. Nie można także zmienić stanu udostępnienia żadnego elementu członkowskiego.  
  
-   **Dziedziczenie.** Moduł nie może dziedziczyć z dowolnego typu innego niż <xref:System.Object>, z których wszystkie moduły dziedziczyć. W szczególności jeden moduł nie może dziedziczyć z innej.  
  
     Nie można użyć [dziedziczy instrukcję](../../../visual-basic/language-reference/statements/inherits-statement.md) w definicji modułu, nawet do określenia <xref:System.Object>.  
  
-   **Właściwość domyślna.** Nie można zdefiniować żadnych właściwości domyślne w module. Aby uzyskać więcej informacji, zobacz temat [Default](../../../visual-basic/language-reference/modifiers/default.md).  
  
## <a name="behavior"></a>Zachowanie  
  
-   **Poziom dostępu.** W ramach modułu można zadeklarować każdego członka z poziomu dostępu. Domyślnie członkowie modułu [publicznych](../../../visual-basic/language-reference/modifiers/public.md) dostęp, z wyjątkiem sytuacji zmiennych i stałych, które domyślnie [prywatnej](../../../visual-basic/language-reference/modifiers/private.md) dostępu. Gdy moduł ograniczył dostęp więcej niż jeden z jej członków, pierwszeństwo ma poziom dostępu określonego modułu.  
  
-   **Zakres.** Moduł jest w zakresie jego przestrzeń nazw.  
  
     Zakres każdego członka modułu jest cały moduł. Należy zauważyć, że wszystkie elementy członkowskie poddawane *wpisz podwyższania poziomu*, co powoduje, że ich zakres ma zostać podniesiony do przestrzeni nazw, zawierającej moduł. Aby uzyskać więcej informacji, zobacz [promocja typu](../../../visual-basic/programming-guide/language-features/declared-elements/type-promotion.md).  
  
-   **Kwalifikacja.** Może mieć wiele modułów w projekcie i można zadeklarować składowych o tej samej nazwie w co najmniej dwa moduły. Jednak jeśli odwołanie jest z poza ten moduł musi kwalifikować się wszelkie odwołania do składowej o nazwie odpowiedniego modułu. Aby uzyskać więcej informacji, zobacz [Odwołania do zadeklarowanych elementów](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).  
  
## <a name="example"></a>Przykład  
 [!code-vb[VbVbalrStatements#69](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/module-statement_1.vb)]  
  
## <a name="see-also"></a>Zobacz też  
 [Class, instrukcja](../../../visual-basic/language-reference/statements/class-statement.md)  
 [Namespace, instrukcja](../../../visual-basic/language-reference/statements/namespace-statement.md)  
 [Structure, instrukcja](../../../visual-basic/language-reference/statements/structure-statement.md)  
 [Instrukcja Interface](../../../visual-basic/language-reference/statements/interface-statement.md)  
 [Instrukcja Property](../../../visual-basic/language-reference/statements/property-statement.md)  
 [Promocja typu](../../../visual-basic/programming-guide/language-features/declared-elements/type-promotion.md)
