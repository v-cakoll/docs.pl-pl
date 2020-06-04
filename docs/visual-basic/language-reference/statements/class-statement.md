---
title: Class, instrukcja
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
ms.openlocfilehash: bdb73772dfe0e6d49d89a4ef006b1bceac14c8ee
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84397158"
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
|`attributelist`|Opcjonalny. Zobacz [listę atrybutów](attribute-list.md).|  
|`accessmodifier`|Opcjonalny. Może być jedną z następujących czynności:<br /><br /> -   [Społeczeństwo](../modifiers/public.md)<br />-   [Chronione](../modifiers/protected.md)<br />-   [Osoby](../modifiers/friend.md)<br />-   [Użytek](../modifiers/private.md)<br />-   [Chroniony znajomy](../modifiers/protected-friend.md)<br />- [Prywatne chronione](../modifiers/private-protected.md)<br/><br/> Zobacz [poziomy dostępu w Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md).|  
|`Shadows`|Opcjonalny. Zobacz [Shadows](../modifiers/shadows.md).|  
|`MustInherit`|Opcjonalny. Zobacz [MustInherit](../modifiers/mustinherit.md).|  
|`NotInheritable`|Opcjonalny. Zobacz [NotInheritable](../modifiers/notinheritable.md).|  
|`Partial`|Opcjonalny. Wskazuje częściową definicję klasy. Zobacz [częściowy](../modifiers/partial.md).|  
|`name`|Wymagany. Nazwa tej klasy. Zobacz [zadeklarowane nazwy elementów](../../programming-guide/language-features/declared-elements/declared-element-names.md).|  
|`Of`|Opcjonalny. Określa, że jest to Klasa generyczna.|  
|`typelist`|Wymagane [w przypadku użycia słowa](of-clause.md) kluczowego. Lista parametrów typu dla tej klasy. Zobacz [Lista typów](type-list.md).|  
|`Inherits`|Opcjonalny. Wskazuje, że ta klasa dziedziczy elementy członkowskie innej klasy. Zobacz [instrukcje Inherits](inherits-statement.md).|  
|`classname`|Wymagane, jeśli używasz `Inherits` instrukcji. Nazwa klasy, z której pochodzi ta klasa.|  
|`Implements`|Opcjonalny. Wskazuje, że ta klasa implementuje elementy członkowskie jednego lub większej liczby interfejsów. Zobacz [instrukcja Implements](implements-statement.md).|  
|`interfacenames`|Wymagane, jeśli używasz `Implements` instrukcji. Nazwy interfejsów implementowanych przez tę klasę.|  
|`statements`|Opcjonalny. Instrukcje definiujące elementy członkowskie tej klasy.|  
|`End Class`|Wymagany. Kończy `Class` definicję.|  
  
## <a name="remarks"></a>Uwagi  
 `Class`Instrukcja definiuje nowy typ danych. *Klasa* jest podstawowym blokiem konstrukcyjnym programowania zorientowanego obiektowo (OOP). Aby uzyskać więcej informacji, zobacz [obiekty i klasy](../../programming-guide/language-features/objects-and-classes/index.md).  
  
 Można używać `Class` tylko na poziomie przestrzeni nazw lub modułu. Oznacza to, że *kontekst deklaracji* klasy musi być plikiem źródłowym, przestrzenią nazw, klasą, strukturą, modułem lub interfejsem i nie może być procedurą ani blokiem. Aby uzyskać więcej informacji, zobacz [konteksty deklaracji i domyślne poziomy dostępu](declaration-contexts-and-default-access-levels.md).  
  
 Każde wystąpienie klasy ma okres istnienia niezależny od wszystkich innych wystąpień. Ten okres istnienia rozpoczyna się, gdy jest tworzony przez nową klauzulę [operatora](../operators/new-operator.md) lub przez funkcję taką jak <xref:Microsoft.VisualBasic.Interaction.CreateObject%2A> . Zostaje ona zakończona, gdy wszystkie zmienne wskazujące na wystąpienie mają wartość [Nothing](../nothing.md) lub do wystąpień innych klas.  
  
 Klasy są domyślne dla [zaprzyjaźnionego](../modifiers/friend.md) dostępu. Możesz dostosować ich poziomy dostępu za pomocą modyfikatorów dostępu. Aby uzyskać więcej informacji, zobacz [poziomy dostępu w Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md).  
  
## <a name="rules"></a>Reguły  
  
- **Zagnieżdżania.** Można zdefiniować jedną klasę w innej. Klasa zewnętrzna jest nazywana *klasą zawierającą*, a Klasa wewnętrzna jest nazywana *klasą zagnieżdżoną*.  
  
- **Strukturze.** Jeśli Klasa używa [instrukcji Inherits](inherits-statement.md), można określić tylko jedną klasę bazową lub interfejs. Klasa nie może dziedziczyć z więcej niż jednego elementu.  
  
     Klasa nie może dziedziczyć z innej klasy z bardziej restrykcyjnym poziomem dostępu. Na przykład `Public` Klasa nie może dziedziczyć z `Friend` klasy.  
  
     Klasa nie może dziedziczyć z klasy zagnieżdżonej w tym elemencie.  
  
- **Realizacji.** Jeśli Klasa używa [instrukcji Implements](implements-statement.md), należy zaimplementować każdy element członkowski zdefiniowany przez każdy interfejs określony w `interfacenames` . Wyjątkiem jest zmiana implementacji składowej klasy bazowej. Aby uzyskać więcej informacji, zobacz "Reimplementacja" w temacie [Implements](implements-clause.md).  
  
- **Właściwość domyślna.** Klasa może określać co najwyżej jedną właściwość jako *Właściwość domyślną*. Aby uzyskać więcej informacji, zobacz [domyślne](../modifiers/default.md).  
  
## <a name="behavior"></a>Zachowanie  
  
- **Poziom dostępu.** W obrębie klasy można zadeklarować każdego członka z własnym poziomem dostępu. Członkowie klasy są domyślnie dostępem [publicznym](../modifiers/public.md) , z wyjątkiem zmiennych i stałych, które domyślnie są dostępem [prywatnym](../modifiers/private.md) . Gdy Klasa ma więcej ograniczony dostęp niż jeden z jej członków, poziom dostępu do klasy ma pierwszeństwo.  
  
- **Scope.** Klasa znajduje się w zakresie, w której znajduje się przestrzeń nazw, Klasa, struktura lub moduł.  
  
     Zakres każdego elementu członkowskiego klasy jest całą klasą.  
  
     **Okres istnienia.** Visual Basic nie obsługuje klas statycznych. Funkcjonalny odpowiednik klasy statycznej jest dostarczany przez moduł. Aby uzyskać więcej informacji, zobacz [moduł instrukcja](module-statement.md).  
  
     Elementy członkowskie klasy mają okresy istnienia, w zależności od tego, jak i gdzie są one zadeklarowane. Aby uzyskać więcej informacji, zobacz [okres istnienia w Visual Basic](../../programming-guide/language-features/declared-elements/lifetime.md).  
  
- **Branego.** Kod poza klasą musi kwalifikować nazwę elementu członkowskiego o nazwie tej klasy.  
  
     Jeśli kod wewnątrz klasy zagnieżdżonej tworzy niekwalifikowane odwołanie do elementu programistycznego, Visual Basic wyszukuje element jako pierwszy w klasie zagnieżdżonej, a następnie w klasie zawierającej i tak dalej, jak najbardziej zewnętrzny element zawierający.  
  
## <a name="classes-and-modules"></a>Klasy i moduły  
 Te elementy mają wiele podobieństw, ale istnieją pewne istotne różnice.  
  
- **Terminologia.** Poprzednie wersje Visual Basic rozpoznają dwa typy modułów: *moduły klasy* (pliki. CLS) i *moduły standardowe* (pliki. bas). Bieżąca wersja wywołuje odpowiednio te *klasy* i *moduły*.  
  
- **Udostępnione elementy członkowskie.** Można kontrolować, czy element członkowski klasy jest członkiem współdzielonym, czy wystąpieniem.  
  
- **Orientacja obiektu.** Klasy są zorientowane obiektowo, ale moduły nie są. Można utworzyć co najmniej jedno wystąpienie klasy. Aby uzyskać więcej informacji, zobacz [obiekty i klasy](../../programming-guide/language-features/objects-and-classes/index.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład używa instrukcji, `Class` Aby zdefiniować klasę i kilku członków.  
  
 [!code-vb[VbVbalrStatements#62](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#62)]  
  
## <a name="see-also"></a>Zobacz też

- [Obiekty i klasy](../../programming-guide/language-features/objects-and-classes/index.md)
- [Struktury i klasy](../../programming-guide/language-features/data-types/structures-and-classes.md)
- [Interface, instrukcja](interface-statement.md)
- [Module — Instrukcja](module-statement.md)
- [Property — Instrukcja](property-statement.md)
- [Okres istnienia obiektów: w jaki sposób obiekty są tworzone i niszczone](../../programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)
- [Typy ogólne w Visual Basic](../../programming-guide/language-features/data-types/generic-types.md)
- [Instrukcje: Używanie klasy ogólnej](../../programming-guide/language-features/data-types/how-to-use-a-generic-class.md)
