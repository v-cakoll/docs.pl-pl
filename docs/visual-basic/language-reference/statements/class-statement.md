---
title: Class — Instrukcja (Visual Basic)
ms.date: 05/12/2018
f1_keywords:
- vb.Class
helpviewer_keywords:
- class modules
- Class statement [Visual Basic]
- classes [Visual Basic], fields
- fields [Visual Basic], of classes
- class types [Visual Basic], class statements
- classes [Visual Basic], creating
- classes [Visual Basic], data members
- data members [Visual Basic], of classes
ms.assetid: f2664f38-eb5a-4d4b-a374-1d041521fb6c
ms.openlocfilehash: 1d81ce148e237df6997934f70c294630f6cc7b8d
ms.sourcegitcommit: 22c3c8f74eaa138dbbbb02eb7d720fce87fc30a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/17/2018
ms.locfileid: "34235885"
---
# <a name="class-statement-visual-basic"></a>Class — Instrukcja (Visual Basic)
Deklaruje nazwę klasy i wprowadza definicje zmiennych, właściwości, zdarzeń i procedur, które obejmuje ta klasa.  
  
## <a name="syntax"></a>Składnia  
  
```  
[ <attributelist> ] [ accessmodifier ] [ Shadows ] [ MustInherit | NotInheritable ] [ Partial ] _  
Class name [ ( Of typelist ) ]  
    [ Inherits classname ]  
    [ Implements interfacenames ]  
    [ statements ]  
End Class  
```  
  
## <a name="parts"></a>Części  
  
|Termin|Definicja|  
|---|---|  
|`attributelist`|Opcjonalna. Zobacz temat [Lista atrybutów](../../../visual-basic/language-reference/statements/attribute-list.md).|  
|`accessmodifier`|Opcjonalna. Może to być jeden z następujących elementów:<br /><br /> -   [Publiczna](../../../visual-basic/language-reference/modifiers/public.md)<br />-   [Chronione](../../../visual-basic/language-reference/modifiers/protected.md)<br />-   [Friend](../../../visual-basic/language-reference/modifiers/friend.md)<br />-   [Prywatne](../../../visual-basic/language-reference/modifiers/private.md)<br />-   [Friend chronionych](../../language-reference/modifiers/protected-friend.md)<br />- [Prywatne chronione](../../language-reference/modifiers/private-protected.md)<br/><br/> Zobacz temat [Poziomy dostępu w języku Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).|  
|`Shadows`|Opcjonalna. Zobacz [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md).|  
|`MustInherit`|Opcjonalna. Zobacz [MustInherit](../../../visual-basic/language-reference/modifiers/mustinherit.md).|  
|`NotInheritable`|Opcjonalna. Zobacz [NotInheritable](../../../visual-basic/language-reference/modifiers/notinheritable.md).|  
|`Partial`|Opcjonalna. Wskazuje częściową definicją klasy. Zobacz [częściowe](../../../visual-basic/language-reference/modifiers/partial.md).|  
|`name`|Wymagana. Nazwa tej klasy. Zobacz temat[Zadeklarowane nazwy elementów](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).|  
|`Of`|Opcjonalna. Określa, że jest klasą szablonową.|  
|`typelist`|Wymagane w przypadku użycia [z](../../../visual-basic/language-reference/statements/of-clause.md) — słowo kluczowe. Lista parametrów typu dla tej klasy. Zobacz [typu listy](../../../visual-basic/language-reference/statements/type-list.md).|  
|`Inherits`|Opcjonalna. Wskazuje, że ta klasa dziedziczy elementów członkowskich innej klasy. Zobacz [Inherits — instrukcja](../../../visual-basic/language-reference/statements/inherits-statement.md).|  
|`classname`|Wymagane w przypadku użycia `Inherits` instrukcji. Nazwa klasy, z której pochodzi ta klasa.|  
|`Implements`|Opcjonalna. Wskazuje, że ta klasa implementuje członkami jeden lub więcej interfejsów. Zobacz [implementuje instrukcji](../../../visual-basic/language-reference/statements/implements-statement.md).|  
|`interfacenames`|Wymagane w przypadku użycia `Implements` instrukcji. Nazwy interfejsów, który implementuje ta klasa.|  
|`statements`|Opcjonalna. Instrukcje, które definiują elementy członkowskie tej klasy.|  
|`End Class`|Wymagana. Kończy definicję `Class`.|  
  
## <a name="remarks"></a>Uwagi  
 A `Class` instrukcji definiuje nowy typ danych. A *klasy* jest podstawowym blokiem konstrukcyjnym programowanie zorientowane obiektowo (Obiektowo). Aby uzyskać więcej informacji, zobacz temat [Obiekty i klasy](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md).  
  
 Można użyć `Class` tylko na poziomie przestrzeni nazw lub modułu. Oznacza to, że *kontekście deklaracji* dla klasy musi być pliku źródłowego, przestrzeni nazw, klasy, struktury, modułu lub interfejsu i nie może być procedurę lub blok. Aby uzyskać więcej informacji, zobacz [Declaration Contexts and Default Access Level](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md) (Kontekst deklaracji i domyślne poziomy dostępu).  
  
 Każde wystąpienie klasy ma czas istnienia, niezależnie od innych wystąpień. Ten cykl życia uruchamia się, gdy jest tworzony przez [operatora New](../../../visual-basic/language-reference/operators/new-operator.md) klauzuli lub funkcji, takich jak <xref:Microsoft.VisualBasic.Interaction.CreateObject%2A>. Go kończy się, gdy wszystkie zmienne wskazujące wystąpienie zostały ustawione na [nic](../../../visual-basic/language-reference/nothing.md) lub wystąpienia innych klas.  
  
 Domyślnie klasy [Friend](../../../visual-basic/language-reference/modifiers/friend.md) dostępu. Poziomy dostępu modułów można dostosować za pomocą modyfikatorów dostępu. Aby uzyskać więcej informacji, zobacz temat [Poziomy dostępu w języku Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
## <a name="rules"></a>Reguły  
  
-   **Zagnieżdżania.** Można określić jedną klasę w innym. Klasa zewnętrzne jest nazywana *klasą*, i nosi nazwę klasy wewnętrznej *zagnieżdżone klasy*.  
  
-   **Dziedziczenie.** Jeśli używa klasy [dziedziczy instrukcję](../../../visual-basic/language-reference/statements/inherits-statement.md), można określić tylko jeden klasy podstawowej lub interfejsu. Klasa nie może dziedziczyć z więcej niż jeden element.  
  
     Klasa nie może dziedziczyć z innej klasy z bardziej restrykcyjne poziom dostępu. Na przykład `Public` nie może dziedziczyć po klasie `Friend` klasy.  
  
     Klasa nie może też dziedziczyć z klasy w niej zagnieżdżonej.  
  
-   **Implementacja.** Jeśli używa klasy [Implements — instrukcja](../../../visual-basic/language-reference/statements/implements-statement.md), musisz zaimplementować każdego elementu członkowskiego zdefiniowane przez każdego interfejsu należy określić w `interfacenames`. Wyjątkiem jest ponowna implementacja elementu członkowskiego klasy podstawowej. Aby uzyskać więcej informacji, zobacz "Ponowna implementacja" w [implementuje](../../../visual-basic/language-reference/statements/implements-clause.md).  
  
-   **Domyślna właściwość.** Klasę można określić co najwyżej jedną właściwość jako jego *domyślna właściwość*. Aby uzyskać więcej informacji, zobacz [domyślne](../../../visual-basic/language-reference/modifiers/default.md).  
  
## <a name="behavior"></a>Zachowanie  
  
-   **Poziom dostępu.** W klasie mogą zadeklarować każdy element członkowski z poziomu dostępu. Domyślne elementy członkowskie klasy [publicznego](../../../visual-basic/language-reference/modifiers/public.md) uzyskać dostęp, z wyjątkiem zmienne i stałe, które domyślnie [prywatnej](../../../visual-basic/language-reference/modifiers/private.md) dostępu. Gdy klasa ograniczył dostęp więcej niż jeden z jego elementów członkowskich, pierwszeństwo ma poziom dostępu do klasy.  
  
-   **Zakres.** Klasa jest w zakresie w całym jej zawierającego przestrzeni nazw, klasy, struktury lub modułu.  
  
     Zakres każdy element członkowski klasy jest całej klasy.  
  
     **Okres istnienia.** Język Visual Basic nie obsługuje klasy statyczne. Odpowiednik funkcjonalności w klasie statycznej jest udostępniana przez moduł. Aby uzyskać więcej informacji, zobacz [Module — instrukcja](../../../visual-basic/language-reference/statements/module-statement.md).  
  
     Elementy członkowskie klasy okresy istnienia w zależności od tego, jak i gdzie są zadeklarowane. Aby uzyskać więcej informacji, zobacz [okres istnienia w Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md).  
  
-   **Kwalifikacji.** Kod poza klasą musi nazwy członka o nazwie tej klasy.  
  
     Kod wewnątrz klasy zagnieżdżonej wykonuje niekwalifikowane odwołanie do elementu programistycznego, Visual Basic wyszukuje element najpierw w klasie zagnieżdżonych, następnie w zawierająca go klasa, i tak dalej do najbardziej zewnętrznego elementu zawierającego.  
  
## <a name="classes-and-modules"></a>Klasy i moduły  
 Te elementy mają wiele podobieństw, ale istnieje kilka istotnych różnic.  
  
-   **Terminologia.** Poprzednie wersje języka Visual Basic rozpoznawały dwa typy modułów: *moduły klas* (pliki .cls) i *moduły standardowe* (pliki .bas). W bieżącej wersji są one nazywane odpowiednio *klasami* i *modułami*.  
  
-   **Udostępnione elementy członkowskie.** Można określić, czy udostępniany jest element członkowski klasy czy wystąpienia.  
  
-   **Orientacja obiektowa.** Klasy są zorientowane obiektowo, a moduły nie. Można utworzyć co najmniej jedno wystąpienie klasy. Aby uzyskać więcej informacji, zobacz temat [Obiekty i klasy](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md).  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto `Class` instrukcji, aby zdefiniować klasę i kilka elementów członkowskich.  
  
 [!code-vb[VbVbalrStatements#62](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/class-statement_1.vb)]  
  
## <a name="see-also"></a>Zobacz też  
 [Obiekty i klasy](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)  
 [Struktury i klasy](../../../visual-basic/programming-guide/language-features/data-types/structures-and-classes.md)  
 [Instrukcja Interface](../../../visual-basic/language-reference/statements/interface-statement.md)  
 [Module, instrukcja](../../../visual-basic/language-reference/statements/module-statement.md)  
 [Instrukcja Property](../../../visual-basic/language-reference/statements/property-statement.md)  
 [Okres istnienia obiektów: w jaki sposób obiekty są tworzone i niszczone](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)  
 [Typy ogólne w Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)  
 [Instrukcje: używanie klasy ogólnej](../../../visual-basic/programming-guide/language-features/data-types/how-to-use-a-generic-class.md)
