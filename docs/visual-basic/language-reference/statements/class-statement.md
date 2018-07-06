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
|`attributelist`|Opcjonalne. Zobacz temat [Lista atrybutów](../../../visual-basic/language-reference/statements/attribute-list.md).|  
|`accessmodifier`|Opcjonalne. Może to być jeden z następujących parametrów:<br />
<br />-   [Public](../../../visual-basic/language-reference/modifiers/public.md)
<br />-   [Protected](../../../visual-basic/language-reference/modifiers/protected.md)
<br />-   [Friend](../../../visual-basic/language-reference/modifiers/friend.md)
<br />-   [Private](../../../visual-basic/language-reference/modifiers/private.md)
<br />-   [Protected Friend](../../language-reference/modifiers/protected-friend.md)
<br />-   [Private Protected](../../language-reference/modifiers/private-protected.md)
<br/><br/> Zobacz temat [Poziomy dostępu w języku Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).|  
|`Shadows`|Opcjonalne. Zobacz [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md).|  
|`MustInherit`|Opcjonalne. Zobacz [MustInherit](../../../visual-basic/language-reference/modifiers/mustinherit.md).|  
|`NotInheritable`|Opcjonalne. Zobacz [NotInheritable](../../../visual-basic/language-reference/modifiers/notinheritable.md).|  
|`Partial`|Opcjonalne. Wskazuje częściową definicję klasy. Zobacz [Partial](../../../visual-basic/language-reference/modifiers/partial.md).|  
|`name`|Wymagane. Nazwa tej klasy. Zobacz temat [Zadeklarowane nazwy elementów](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).|  
|`Of`|Opcjonalne. Określa, że jest klasą ogólną.|  
|`typelist`|Wymagane w przypadku użycia słowa kluczowego [Of](../../../visual-basic/language-reference/statements/of-clause.md). Lista parametrów typu dla tej klasy. Zobacz [Lista typów](../../../visual-basic/language-reference/statements/type-list.md).|  
|`Inherits`|Opcjonalne. Wskazuje, że ta klasa dziedziczy elementy członkowskie innej klasy. Zobacz [instrukcja Inherits](../../../visual-basic/language-reference/statements/inherits-statement.md).|  
|`classname`|Wymagane w przypadku użycia instrukcji `Inherits`. Nazwa klasy, z której pochodzi ta klasa.|  
|`Implements`|Opcjonalne. Wskazuje, że ta klasa implementuje elementy członkowskie jednego lub więcej interfejsów. Zobacz [instrukcja Implements](../../../visual-basic/language-reference/statements/implements-statement.md).|  
|`interfacenames`|Wymagane w przypadku użycia instrukcji `Implements`. Nazwy interfejsów, które implementuje ta klasa.|  
|`statements`|Opcjonalne. Instrukcje, które definiują elementy członkowskie tej klasy.|  
|`End Class`|Wymagane. Kończy definicję `Class`.|  
  
## <a name="remarks"></a>Uwagi  
 Instrukcja `Class` definiuje nowy typ danych. *Klasa* jest podstawowym blokiem konstrukcyjnym programowania zorientowanego obiektowo (object-oriented programming - OOP). Aby uzyskać więcej informacji, zobacz temat [Obiekty i klasy](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md).  
  
 `Class` można użyć tylko na poziomie przestrzeni nazw lub modułu. Oznacza to, że *kontekstem deklaracji* klasy musi być plik źródłowy, przestrzeń nazw, klasa, struktura, moduł lub interfejs i nie może być procedura lub blok. Aby uzyskać więcej informacji, zobacz [Kontekst deklaracji i domyślne poziomy dostępu](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).  
  
 Każde wystąpienie klasy ma czas istnienia niezależny od innych wystąpień. Czas istnienia rozpoczyna się, gdy klasa jest tworzona przez [operator New](../../../visual-basic/language-reference/operators/new-operator.md), klauzulę lub funkcję, taką jak <xref:Microsoft.VisualBasic.Interaction.CreateObject%2A>. Czas istnienia kończy się, gdy wszystkie zmienne wskazujące na wystąpienie zostaną ustawione na [Nothing](../../../visual-basic/language-reference/nothing.md) lub wystąpienia innych klas.  
  
 Domyślnie klasy posiadają poziom dostępu typu [Friend](../../../visual-basic/language-reference/modifiers/friend.md). Poziomy dostępu można dostosować za pomocą modyfikatorów dostępu. Aby uzyskać więcej informacji, zobacz temat [Poziomy dostępu w języku Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
## <a name="rules"></a>Reguły  
  
-   **Zagnieżdżanie.** Można zdefiniować jedną klasę w innej. Klasa zewnętrzna jest nazywana *klasą zawierającą*, a klasa wewnętrzna *klasą zagnieżdżoną*.  
  
-   **Dziedziczenie.** Jeśli klasa używa [instrukcji Inherits](../../../visual-basic/language-reference/statements/inherits-statement.md), można określić tylko jedną klasę podstawową lub interfejs. Klasa nie może dziedziczyć z więcej niż jednego elementu.  
  
     Klasa nie może dziedziczyć z innej klasy o bardziej restrykcyjnym poziomie dostępu. Na przykład klasa `Public` nie może dziedziczyć po klasie `Friend`.  
  
     Klasa nie może dziedziczyć z klasy w niej zagnieżdżonej.  
  
-   **Implementacja.** Jeśli klasa używa [instrukcji Implements](../../../visual-basic/language-reference/statements/implements-statement.md), musisz zaimplementować każdy element członkowski zdefiniowany przez każdy interfejs określony w `interfacenames`. Wyjątkiem jest ponowna implementacja elementu członkowskiego klasy podstawowej. Aby uzyskać więcej informacji, zobacz rozdział "Ponowna implementacja" w temacie [klauzula Implements](../../../visual-basic/language-reference/statements/implements-clause.md).  
  
-   **Domyślna właściwość.** Klasa może określić co najwyżej jedną właściwość jako jej *właściwość domyślną*. Aby uzyskać więcej informacji, zobacz temat [Default](../../../visual-basic/language-reference/modifiers/default.md).  
  
## <a name="behavior"></a>Zachowanie  
  
-   **Poziom dostępu.** Wewnątrz klasy można zadeklarować każdy element członkowski z własnym poziomem dostępu. Domyślne elementy członkowskie klasy mają poziom dostępu typu [Public](../../../visual-basic/language-reference/modifiers/public.md), z wyjątkiem zmiennych i stałych, których domyślny poziom jest typu [Private](../../../visual-basic/language-reference/modifiers/private.md). Gdy klasa posiada poziom dostępu bardziej restrykcyjny niż jeden z jej elementów członkowskich, pierwszeństwo ma poziom dostępu do klasy.  
  
-   **Zakres.** Zasięgiem klasy jest cała zawierająca ją przestrzeń nazw, klasa, struktura lub moduł.  
  
     Zakresem każdego elementu członkowskiego klasy jest cała klasa.  
  
-   **Okres istnienia.** Język Visual Basic nie obsługuje klas statycznych. Funkcjonalność odpowiadająca klasie statycznej jest realizowana przez moduł. Aby uzyskać więcej informacji, zobacz [instrukcja Module](../../../visual-basic/language-reference/statements/module-statement.md).  
  
     Elementy członkowskie klasy posiadają okresy istnienia zależne od tego, jak i gdzie są zadeklarowane. Aby uzyskać więcej informacji, zobacz [okres istnienia w Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md).  
  
-   **Kwalifikacji.** Kod poza klasą musi określać nazwę elementu członkowskiego z nazwą tej klasy.  
  
     Jeśli kod wewnątrz klasy zagnieżdżonej wykonuje niekwalifikowane odwołanie do elementu programistycznego, Visual Basic wyszukuje ten element najpierw w klasie zagnieżdżonej, następnie w klasie zawierającej, i tak dalej do najbardziej zewnętrznego elementu zawierającego.  
  
## <a name="classes-and-modules"></a>Klasy i moduły  
 Elementy te mają wiele podobieństw, ale istnieje kilka istotnych różnic.  
  
-   **Terminologia.** Poprzednie wersje języka Visual Basic rozpoznawały dwa typy modułów: *moduły klas* (pliki .cls) i *moduły standardowe* (pliki .bas). W bieżącej wersji są one nazywane odpowiednio *klasami* i *modułami*.  
  
-   **Udostępnione elementy członkowskie.** Można określić, czy udostępniany jest element członkowski klasy czy wystąpienia.  
  
-   **Orientacja obiektowa.** Klasy są zorientowane obiektowo, a moduły nie. Można utworzyć co najmniej jedno wystąpienie klasy. Aby uzyskać więcej informacji, zobacz temat [Obiekty i klasy](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md).  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto instrukcji `Class`, aby zdefiniować klasę i kilka elementów członkowskich.  
  
 [!code-vb[VbVbalrStatements#62](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/class-statement_1.vb)]  
  
## <a name="see-also"></a>Zobacz też  
 [Obiekty i klasy](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)  
 [Struktury i klasy](../../../visual-basic/programming-guide/language-features/data-types/structures-and-classes.md)  
 [Instrukcja Interface](../../../visual-basic/language-reference/statements/interface-statement.md)  
 [Instrukcja Module](../../../visual-basic/language-reference/statements/module-statement.md)  
 [Instrukcja Property](../../../visual-basic/language-reference/statements/property-statement.md)  
 [Okres istnienia obiektów: w jaki sposób obiekty są tworzone i niszczone](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)  
 [Typy ogólne w Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)  
 [Instrukcje: używanie klasy ogólnej](../../../visual-basic/programming-guide/language-features/data-types/how-to-use-a-generic-class.md)
