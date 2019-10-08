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
ms.openlocfilehash: 2e4514686afcbbe0e9ff0b3326c1be212db4f9f8
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005149"
---
# <a name="class-statement-visual-basic"></a>Class — Instrukcja (Visual Basic)
Deklaruje nazwę klasy i wprowadza definicje zmiennych, właściwości, zdarzeń i procedur, które obejmuje Klasa.  
  
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
|`attributelist`|Opcjonalny. Zobacz [listę atrybutów](../../../visual-basic/language-reference/statements/attribute-list.md).|  
|`accessmodifier`|Opcjonalny. Może być jedną z następujących czynności:<br /><br /> -   [Public](../../../visual-basic/language-reference/modifiers/public.md)<br />-   [Ochrona](../../../visual-basic/language-reference/modifiers/protected.md)<br />-   [Friend](../../../visual-basic/language-reference/modifiers/friend.md)<br />-   [Private](../../../visual-basic/language-reference/modifiers/private.md)<br />-   [chroniony znajomy](../../language-reference/modifiers/protected-friend.md)<br />- [Private Protected](../../language-reference/modifiers/private-protected.md)<br/><br/> Zobacz [poziomy dostępu w Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).|  
|`Shadows`|Opcjonalny. Zobacz [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md).|  
|`MustInherit`|Opcjonalny. Zobacz [MustInherit](../../../visual-basic/language-reference/modifiers/mustinherit.md).|  
|`NotInheritable`|Opcjonalny. Zobacz [NotInheritable](../../../visual-basic/language-reference/modifiers/notinheritable.md).|  
|`Partial`|Opcjonalny. Wskazuje częściową definicję klasy. Zobacz [częściowy](../../../visual-basic/language-reference/modifiers/partial.md).|  
|`name`|Wymagany. Nazwa tej klasy. Zobacz [zadeklarowane nazwy elementów](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).|  
|`Of`|Opcjonalny. Określa, że jest to Klasa generyczna.|  
|`typelist`|Wymagane [w przypadku użycia słowa](../../../visual-basic/language-reference/statements/of-clause.md) kluczowego. Lista parametrów typu dla tej klasy. Zobacz [Lista typów](../../../visual-basic/language-reference/statements/type-list.md).|  
|`Inherits`|Opcjonalny. Wskazuje, że ta klasa dziedziczy elementy członkowskie innej klasy. Zobacz [instrukcje Inherits](../../../visual-basic/language-reference/statements/inherits-statement.md).|  
|`classname`|Wymagane, jeśli używasz instrukcji `Inherits`. Nazwa klasy, z której pochodzi ta klasa.|  
|`Implements`|Opcjonalny. Wskazuje, że ta klasa implementuje elementy członkowskie jednego lub większej liczby interfejsów. Zobacz [instrukcja Implements](../../../visual-basic/language-reference/statements/implements-statement.md).|  
|`interfacenames`|Wymagane, jeśli używasz instrukcji `Implements`. Nazwy interfejsów implementowanych przez tę klasę.|  
|`statements`|Opcjonalny. Instrukcje definiujące elementy członkowskie tej klasy.|  
|`End Class`|Wymagany. Kończy definicję `Class`.|  
  
## <a name="remarks"></a>Uwagi  
 Instrukcja `Class` definiuje nowy typ danych. *Klasa* jest podstawowym blokiem konstrukcyjnym programowania zorientowanego obiektowo (OOP). Aby uzyskać więcej informacji, zobacz [obiekty i klasy](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md).  
  
 @No__t-0 można użyć tylko w przestrzeni nazw lub na poziomie modułu. Oznacza to, że *kontekst deklaracji* klasy musi być plikiem źródłowym, przestrzenią nazw, klasą, strukturą, modułem lub interfejsem i nie może być procedurą ani blokiem. Aby uzyskać więcej informacji, zobacz [konteksty deklaracji i domyślne poziomy dostępu](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).  
  
 Każde wystąpienie klasy ma okres istnienia niezależny od wszystkich innych wystąpień. Ten okres istnienia rozpoczyna się, gdy jest tworzony przez nową klauzulę [operatora](../../../visual-basic/language-reference/operators/new-operator.md) lub przez funkcję, taką jak <xref:Microsoft.VisualBasic.Interaction.CreateObject%2A>. Zostaje ona zakończona, gdy wszystkie zmienne wskazujące na wystąpienie mają wartość [Nothing](../../../visual-basic/language-reference/nothing.md) lub do wystąpień innych klas.  
  
 Klasy są domyślne dla [zaprzyjaźnionego](../../../visual-basic/language-reference/modifiers/friend.md) dostępu. Możesz dostosować ich poziomy dostępu za pomocą modyfikatorów dostępu. Aby uzyskać więcej informacji, zobacz [poziomy dostępu w Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
## <a name="rules"></a>Przepisy  
  
- **Zagnieżdżania.** Można zdefiniować jedną klasę w innej. Klasa zewnętrzna jest nazywana *klasą zawierającą*, a Klasa wewnętrzna jest nazywana *klasą zagnieżdżoną*.  
  
- **Strukturze.** Jeśli Klasa używa [instrukcji Inherits](../../../visual-basic/language-reference/statements/inherits-statement.md), można określić tylko jedną klasę bazową lub interfejs. Klasa nie może dziedziczyć z więcej niż jednego elementu.  
  
     Klasa nie może dziedziczyć z innej klasy z bardziej restrykcyjnym poziomem dostępu. Na przykład Klasa `Public` nie może dziedziczyć z klasy `Friend`.  
  
     Klasa nie może dziedziczyć z klasy zagnieżdżonej w tym elemencie.  
  
- **Realizacji.** Jeśli Klasa używa [instrukcji Implements](../../../visual-basic/language-reference/statements/implements-statement.md), należy zaimplementować każdy element członkowski zdefiniowany przez każdy interfejs określony w `interfacenames`. Wyjątkiem jest zmiana implementacji składowej klasy bazowej. Aby uzyskać więcej informacji, zobacz "Reimplementacja" w temacie [Implements](../../../visual-basic/language-reference/statements/implements-clause.md).  
  
- **Właściwość domyślna.** Klasa może określać co najwyżej jedną właściwość jako *Właściwość domyślną*. Aby uzyskać więcej informacji, zobacz [domyślne](../../../visual-basic/language-reference/modifiers/default.md).  
  
## <a name="behavior"></a>Zachowanie  
  
- **Poziom dostępu.** W obrębie klasy można zadeklarować każdego członka z własnym poziomem dostępu. Członkowie klasy są domyślnie dostępem [publicznym](../../../visual-basic/language-reference/modifiers/public.md) , z wyjątkiem zmiennych i stałych, które domyślnie są dostępem [prywatnym](../../../visual-basic/language-reference/modifiers/private.md) . Gdy Klasa ma więcej ograniczony dostęp niż jeden z jej członków, poziom dostępu do klasy ma pierwszeństwo.  
  
- **Scope.** Klasa znajduje się w zakresie, w której znajduje się przestrzeń nazw, Klasa, struktura lub moduł.  
  
     Zakres każdego elementu członkowskiego klasy jest całą klasą.  
  
     **Okres istnienia.** Visual Basic nie obsługuje klas statycznych. Funkcjonalny odpowiednik klasy statycznej jest dostarczany przez moduł. Aby uzyskać więcej informacji, zobacz [moduł instrukcja](../../../visual-basic/language-reference/statements/module-statement.md).  
  
     Elementy członkowskie klasy mają okresy istnienia, w zależności od tego, jak i gdzie są one zadeklarowane. Aby uzyskać więcej informacji, zobacz [okres istnienia w Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md).  
  
- **Branego.** Kod poza klasą musi kwalifikować nazwę elementu członkowskiego o nazwie tej klasy.  
  
     Jeśli kod wewnątrz klasy zagnieżdżonej tworzy niekwalifikowane odwołanie do elementu programistycznego, Visual Basic wyszukuje element jako pierwszy w klasie zagnieżdżonej, a następnie w klasie zawierającej i tak dalej, jak najbardziej zewnętrzny element zawierający.  
  
## <a name="classes-and-modules"></a>Klasy i moduły  
 Te elementy mają wiele podobieństw, ale istnieją pewne istotne różnice.  
  
- **Terminologia.** Poprzednie wersje Visual Basic rozpoznają dwa typy modułów: *moduły klasy* (pliki. CLS) i *moduły standardowe* (pliki. bas). Bieżąca wersja wywołuje odpowiednio te *klasy* i *moduły*.  
  
- **Udostępnione elementy członkowskie.** Można kontrolować, czy element członkowski klasy jest członkiem współdzielonym, czy wystąpieniem.  
  
- **Orientacja obiektu.** Klasy są zorientowane obiektowo, ale moduły nie są. Można utworzyć co najmniej jedno wystąpienie klasy. Aby uzyskać więcej informacji, zobacz [obiekty i klasy](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład używa instrukcji `Class` w celu zdefiniowania klasy i kilku członków.  
  
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
