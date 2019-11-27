---
title: Class — Instrukcja
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
ms.openlocfilehash: 3cb276f134e90ce3b3009234eb980d89477e0d09
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74354147"
---
# <a name="class-statement-visual-basic"></a>Class — Instrukcja (Visual Basic)
Deklaruje nazwę klasy i wprowadza definicje zmiennych, właściwości, zdarzeń i procedur, które obejmuje ta klasa.  
  
## <a name="syntax"></a>Składnia  
  
```vb  
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
|`attributelist`|Opcjonalna. Zobacz [listę atrybutów](../../../visual-basic/language-reference/statements/attribute-list.md).|  
|`accessmodifier`|Opcjonalna. Może to być jeden z następujących modyfikatorów dostępu:<br /><br /> -   [publiczny](../../../visual-basic/language-reference/modifiers/public.md)<br />-   [chronione](../../../visual-basic/language-reference/modifiers/protected.md)<br />-   [znajomy](../../../visual-basic/language-reference/modifiers/friend.md)<br />-   [prywatny](../../../visual-basic/language-reference/modifiers/private.md)<br />-   [chronionego przyjaciela](../../language-reference/modifiers/protected-friend.md)<br />- [prywatnej ochrony](../../language-reference/modifiers/private-protected.md)<br/><br/> Zobacz [poziomy dostępu w Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).|  
|`Shadows`|Opcjonalna. Zobacz [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md).|  
|`MustInherit`|Opcjonalna. Zobacz [MustInherit](../../../visual-basic/language-reference/modifiers/mustinherit.md).|  
|`NotInheritable`|Opcjonalna. Zobacz [NotInheritable](../../../visual-basic/language-reference/modifiers/notinheritable.md).|  
|`Partial`|Opcjonalna. Wskazuje częściową definicję klasy. Zobacz [częściowy](../../../visual-basic/language-reference/modifiers/partial.md).|  
|`name`|Wymagana. Nazwa tej klasy. Zobacz [zadeklarowane nazwy elementów](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).|  
|`Of`|Opcjonalna. Określa, że jest to Klasa generyczna.|  
|`typelist`|Wymagane [w przypadku użycia słowa](../../../visual-basic/language-reference/statements/of-clause.md) kluczowego. Lista parametrów typu dla tej klasy. Zobacz [Lista typów](../../../visual-basic/language-reference/statements/type-list.md).|  
|`Inherits`|Opcjonalna. Wskazuje, że ta klasa dziedziczy elementy członkowskie innej klasy. Zobacz [instrukcje Inherits](../../../visual-basic/language-reference/statements/inherits-statement.md).|  
|`classname`|Wymagane, jeśli używasz instrukcji `Inherits`. Nazwa klasy, z której pochodzi ta klasa.|  
|`Implements`|Opcjonalna. Wskazuje, że ta klasa implementuje elementy członkowskie jednego lub większej liczby interfejsów. Zobacz [instrukcja Implements](../../../visual-basic/language-reference/statements/implements-statement.md).|  
|`interfacenames`|Wymagane, jeśli używasz instrukcji `Implements`. Nazwy interfejsów implementowanych przez tę klasę.|  
|`statements`|Opcjonalna. Instrukcje definiujące elementy członkowskie tej klasy.|  
|`End Class`|Wymagana. Kończy definicję `Class`.|  
  
## <a name="remarks"></a>Uwagi  
 Instrukcja `Class` definiuje nowy typ danych. *Klasa* jest podstawowym blokiem konstrukcyjnym programowania zorientowanego obiektowo (OOP). Aby uzyskać więcej informacji, zobacz [obiekty i klasy](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md).  
  
 `Class` można używać tylko na poziomie przestrzeni nazw lub modułu. Oznacza to, że *kontekst deklaracji* klasy musi być plikiem źródłowym, przestrzenią nazw, klasą, strukturą, modułem lub interfejsem i nie może być procedurą ani blokiem. Aby uzyskać więcej informacji, zobacz [konteksty deklaracji i domyślne poziomy dostępu](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).  
  
 Każde wystąpienie klasy ma okres istnienia niezależny od innych wystąpień. Ten okres istnienia rozpoczyna się, gdy jest tworzony przez nową klauzulę [operatora](../../../visual-basic/language-reference/operators/new-operator.md) lub przez funkcję, taką jak <xref:Microsoft.VisualBasic.Interaction.CreateObject%2A>. Zostaje ona zakończona, gdy wszystkie zmienne wskazujące na wystąpienie mają wartość [Nothing](../../../visual-basic/language-reference/nothing.md) lub do wystąpień innych klas.  
  
 Klasy są domyślne dla [zaprzyjaźnionego](../../../visual-basic/language-reference/modifiers/friend.md) dostępu. Poziomy dostępu modułów można dostosować za pomocą modyfikatorów dostępu. Aby uzyskać więcej informacji, zobacz [poziomy dostępu w Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
## <a name="rules"></a>Reguły  
  
- **Zagnieżdżania.** Jedną klasę można zdefiniować w obrębie innej. Klasa zewnętrzna jest nazywana *klasą zawierającą*, a Klasa wewnętrzna jest nazywana *klasą zagnieżdżoną*.  
  
- **Strukturze.** Jeśli Klasa używa [instrukcji Inherits](../../../visual-basic/language-reference/statements/inherits-statement.md), można określić tylko jedną klasę bazową lub interfejs. Klasa nie może dziedziczyć z więcej niż jednego elementu.  
  
     Klasa nie może dziedziczyć z innej klasy o bardziej restrykcyjnym poziomie dostępu. Na przykład Klasa `Public` nie może dziedziczyć z klasy `Friend`.  
  
     Klasa nie może też dziedziczyć z klasy w niej zagnieżdżonej.  
  
- **Realizacji.** Jeśli Klasa używa [instrukcji Implements](../../../visual-basic/language-reference/statements/implements-statement.md), należy zaimplementować każdy element członkowski zdefiniowany przez każdy interfejs określony w `interfacenames`. Wyjątkiem jest ponowna implementacja elementu członkowskiego klasy podstawowej. Aby uzyskać więcej informacji, zobacz "Reimplementacja" w temacie [Implements](../../../visual-basic/language-reference/statements/implements-clause.md).  
  
- **Właściwość domyślna.** Klasa może określać co najwyżej jedną właściwość jako *Właściwość domyślną*. Aby uzyskać więcej informacji, zobacz [domyślne](../../../visual-basic/language-reference/modifiers/default.md).  
  
## <a name="behavior"></a>Zachowanie  
  
- **Poziom dostępu.** W obrębie klasy można zadeklarować każdy element członkowski z własnym poziomem dostępu. Członkowie klasy są domyślnie dostępem [publicznym](../../../visual-basic/language-reference/modifiers/public.md) , z wyjątkiem zmiennych i stałych, które domyślnie są dostępem [prywatnym](../../../visual-basic/language-reference/modifiers/private.md) . Gdy klasa ma poziom dostępu bardziej restrykcyjny niż jeden z jej elementów członkowskich, pierwszeństwo ma poziom dostępu klasy.  
  
- **Scope.** Zakresem klasy jest cała zawierająca ją przestrzeń nazw, klasa, struktura lub moduł.  
  
     Zakresem każdego elementu członkowskiego klasy jest cała klasa.  
  
     **Okres istnienia.** Visual Basic nie obsługuje klas statycznych. Funkcjonalność odpowiadająca klasie statycznej jest realizowana przez moduł. Aby uzyskać więcej informacji, zobacz [moduł instrukcja](../../../visual-basic/language-reference/statements/module-statement.md).  
  
     Elementy członkowskie klasy mają swoje okresy istnienia zależne od tego, jak i gdzie są zadeklarowane. Aby uzyskać więcej informacji, zobacz [okres istnienia w Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md).  
  
- **Branego.** Kod poza klasą musi określać nazwę elementu członkowskiego z nazwą tej klasy.  
  
     Jeśli kod wewnątrz klasy zagnieżdżonej wykonuje niekwalifikowane odwołanie do elementu programistycznego, Visual Basic wyszukuje ten element najpierw w klasie zagnieżdżonej, a następnie w klasie zawierającej — i tak dalej aż do najbardziej zewnętrznego elementu zawierającego.  
  
## <a name="classes-and-modules"></a>Klasy i moduły  
 Te elementy mają wiele podobieństw, ale istnieją pewne istotne różnice.  
  
- **Terminologia.** Poprzednie wersje Visual Basic rozpoznają dwa typy modułów: *moduły klasy* (pliki. CLS) i *moduły standardowe* (pliki. bas). Bieżąca wersja wywołuje odpowiednio te *klasy* i *moduły*.  
  
- **Udostępnione elementy członkowskie.** Można określić, czy udostępniany jest element członkowski klasy czy wystąpienia.  
  
- **Orientacja obiektu.** Klasy są zorientowane obiektowo, a moduły nie. Można utworzyć co najmniej jedno wystąpienie klasy. Aby uzyskać więcej informacji, zobacz [obiekty i klasy](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład używa instrukcji `Class`, aby zdefiniować klasę i kilku członków.  
  
 [!code-vb[VbVbalrStatements#62](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#62)]  
  
## <a name="see-also"></a>Zobacz także

- [Obiekty i klasy](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
- [Struktury i klasy](../../../visual-basic/programming-guide/language-features/data-types/structures-and-classes.md)
- [Interface, instrukcja](../../../visual-basic/language-reference/statements/interface-statement.md)
- [Module, instrukcja](../../../visual-basic/language-reference/statements/module-statement.md)
- [Property, instrukcja](../../../visual-basic/language-reference/statements/property-statement.md)
- [Okres istnienia obiektów: w jaki sposób obiekty są tworzone i niszczone](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)
- [Typy ogólne w Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [Instrukcje: używanie klasy ogólnej](../../../visual-basic/programming-guide/language-features/data-types/how-to-use-a-generic-class.md)
