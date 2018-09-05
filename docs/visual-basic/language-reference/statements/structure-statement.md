---
title: Structure — instrukcja (Visual Basic)
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
ms.openlocfilehash: 9377d889f56049720ab10439582300913f5cbb37
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/01/2018
ms.locfileid: "43416444"
---
# <a name="structure-statement"></a>Structure — Instrukcja
Deklaruje nazwę struktury i wprowadza definicje zmiennych, właściwości, zdarzeń i procedur, które obejmuje struktura.  
  
## <a name="syntax"></a>Składnia  
  
```  
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
|`attributelist`|Opcjonalna. Zobacz temat [Lista atrybutów](../../../visual-basic/language-reference/statements/attribute-list.md).|  
|`accessmodifier`|Opcjonalna. Może to być jeden z następujących elementów:<br /><br /> -   [Public](../../../visual-basic/language-reference/modifiers/public.md)<br />-   [Protected](../../../visual-basic/language-reference/modifiers/protected.md)<br />-   [Friend](../../../visual-basic/language-reference/modifiers/friend.md)<br />-   [Private](../../../visual-basic/language-reference/modifiers/private.md)<br />- [Protected Friend](../../language-reference/modifiers/protected-friend.md)<br/>- [Private protected](../../language-reference/modifiers/private-protected.md) <br /><br /> Zobacz temat [Poziomy dostępu w języku Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).|  
|`Shadows`|Opcjonalna. Zobacz [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md).|  
|`Partial`|Opcjonalne. Wskazuje częściową definicję struktury. Zobacz [Partial](../../../visual-basic/language-reference/modifiers/partial.md).|  
|`name`|Wymagane. Nazwa tej struktury. Zobacz [Nazwy zadeklarowanych elementów](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).|  
|`Of`|Opcjonalne. Określa, że jest to struktura generyczna.|  
|`typelist`|Wymagane w przypadku użycia [z](../../../visual-basic/language-reference/statements/of-clause.md) — słowo kluczowe. Lista parametrów typu dla tej struktury. Zobacz [Lista typów](../../../visual-basic/language-reference/statements/type-list.md).|  
|`Implements`|Opcjonalne. Wskazuje, że ta struktura implementuje składowe jednego lub więcej interfejsów. Zobacz [Implements, instrukcja](../../../visual-basic/language-reference/statements/implements-statement.md).|  
|`interfacenames`|Wymagane w przypadku użycia instrukcji `Implements`. Nazwy interfejsów, które implementuje ta struktura.|  
|`datamemberdeclarations`|Wymagane. Zero lub dowolna liczba instrukcji `Const`, `Dim`, `Enum`, lub `Event` deklarujących *składowe danych* struktury.|  
|`methodmemberdeclarations`|Opcjonalna. Zero lub dowolna liczba deklaracji procedur  `Function`, `Operator`, `Property`, lub `Sub`, które są *składowymi metod* struktury.|  
|`End Structure`|Wymagane. Kończy definicję instrukcji `Structure`.|  
  
## <a name="remarks"></a>Uwagi  
 Instrukcja `Structure` definiuje złożony typ wartości, który można dostosować. *Struktura* jest generalizacją typu definiowanego przez użytkownika (UDT) z poprzednich wersji programu Visual Basic. Aby uzyskać więcej informacji, zobacz [struktury](../../../visual-basic/programming-guide/language-features/data-types/structures.md).  
  
 Struktury obsługują wiele tych samych funkcji co klasy. Na przykład struktury mogą mieć właściwości i procedury, mogą implementować interfejsy i mogą mieć sparametryzowane konstruktory. Istnieją jednak istotne różnice między strukturami i klasami w obszarach takich jak: dziedziczenia, deklaracje i użycie. Ponadto klasy to typy referencyjne, a struktury to typy wartościowe. Aby uzyskać więcej informacji, zobacz [Struktury i klasy](../../../visual-basic/programming-guide/language-features/data-types/structures-and-classes.md).  
  
 Instrukcji `Structure` można użyć tylko na poziomie przestrzeni nazw lub modułu. Oznacza to, że *kontekstem deklaracji* struktury musi być plik źródłowy, przestrzeń nazw, klasa, struktura, moduł lub interfejs, ale nie może być procedura ani blok.  Aby uzyskać więcej informacji, zobacz [Konteksty deklaracji i domyślne poziomy dostępu](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md)  
  
 Domyślnie struktury mają poziom dostępu [Friend](../../../visual-basic/language-reference/modifiers/friend.md) Możesz dostosować ich poziom dostępu za pomocą modyfikatorów dostępu. Aby uzyskać więcej informacji, zobacz temat [Poziomy dostępu w języku Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
## <a name="rules"></a>reguły  
  
-   **Zagnieżdżanie.** Można zdefiniować jedną strukturę wewnątrz innej. Struktura zewnętrzna jest nazywana *strukturą zawierającą*, a struktura wewnętrzna — *strukturą zagnieżdżoną*. Jednak nie można uzyskać dostępu do składowych struktury zagnieżdżonej za pośrednictwem struktury zawierającej. Zamiast tego należy zadeklarować zmienną typu danych struktury zagnieżdżonej.  
  
-   **Deklaracja składowej.** Musisz zadeklarować każdą składową struktury. Składowa struktury nie może być typu [Protected](../../../visual-basic/language-reference/modifiers/protected.md) ani `Protected Friend`, ponieważ nic nie może dziedziczyć ze struktury. Sama struktura może być jednak typu `Protected` lub `Protected Friend`.  
  
     Można zadeklarować nieudostępnione zmienne lub nieudostępnione niestandardowe zdarzenia w strukturze lub nie deklarować ich wcale. Nie mogą istnieć tylko stałe, właściwości i procedury, nawet jeśli niektóre z nich są nieudostępnione.  
  
-   **Inicjowanie.** Nie można zainicjować wartości żadnej składowej danych nieudostępnionych struktury w części jej deklaracji. Musisz zainicjować składową danych za pomocą konstruktora sparametryzowanego struktury lub przypisać wartość do składowej po utworzeniu wystąpienia struktury.  
  
-   **Dziedziczenie.** Struktura nie może dziedziczyć z typu innego niż <xref:System.ValueType>, z którego dziedziczą wszystkie struktury. W szczególności jedna struktura nie może dziedziczyć z innej.  
  
     Nie można użyć [instrukcji Inherits ](../../../visual-basic/language-reference/statements/inherits-statement.md) w definicji struktury, nawet do określenia typu <xref:System.ValueType>.  
  
-   **Implementacja.** Jeśli struktura używa [instrukcji Implements](../../../visual-basic/language-reference/statements/implements-statement.md), musisz zaimplementować każdą składową zdefiniowaną przez każdy interfejs określony w elemencie `interfacenames`.  
  
-   **Właściwość domyślna.** Struktura może wskazać co najwyżej jedną właściwość jako jego *właściwość domyślną* za pomocą modyfikatora [Default](../../../visual-basic/language-reference/modifiers/default.md). Aby uzyskać więcej informacji, zobacz [Default](../../../visual-basic/language-reference/modifiers/default.md).  
  
## <a name="behavior"></a>Zachowanie  
  
-   **Poziom dostępu.** W ramach struktury można zadeklarować każdą składową z własnym poziomem dostępu. Domyślnie wszystkie składowe struktury mają dostęp typu [Public](../../../visual-basic/language-reference/modifiers/public.md). Należy pamiętać, że jeśli struktura ma bardziej ograniczony poziom dostępu, automatycznie ogranicza to dostęp do jej składowych, nawet jeśli dostosujesz ich poziomy dostępu za pomocą modyfikatorów dostępu.
  
  
-   **Zakres.** Struktura jest w zakresie zawierającej ją przestrzeni nazw, klasy, struktury lub modułu.  
  
     Zakresem każdej składowej struktury jest cała struktura.  
  
-   **Okres istnienia.** Sama struktura nie ma okresu istnienia. Ale każde wystąpienie struktury ma okres istnienia niezależny od innych wystąpień.  
  
     Okres istnienia wystąpienia rozpoczyna się w momencie jej utworzenia przez klauzulę [operatora New](../../../visual-basic/language-reference/operators/new-operator.md). Kończy się po zakończeniu okresu istnienia zmiennej, która odpowiada za zakończenie.
  
  
     Nie można wydłużyć okresu istnienia instancji struktury. Funkcjonalność zbliżona do struktury statycznej jest udostępniania przez moduł. Aby uzyskać więcej informacji, zobacz [Module, instrukcja](../../../visual-basic/language-reference/statements/module-statement.md).  
  
     Składowe struktury mają okresy istnienia zależne od tego, jak i gdzie są zadeklarowane. Aby uzyskać więcej informacji, zobacz "Okres istnienia" w artykule [Class, instrukcja](../../../visual-basic/language-reference/statements/class-statement.md).  
  
-   **Kwalifikacja.** Kod spoza struktury musi kwalifikować nazwę składowej z nazwą tej struktury.  
  
     Jeśli kod wewnątrz struktury zagnieżdżonej wykonuje niekwalifikowane odwołanie do elementu programistycznego, program Visual Basic wyszukuje element najpierw w strukturze zagnieżdżonej, następnie w strukturze zawierającej i tak dalej do najbardziej zewnętrznego elementu zawierającego. Aby uzyskać więcej informacji, zobacz [Odwołania do zadeklarowanych elementów](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).  
  
-   **Zużycie pamięci.** Podobnie jak w przypadku wszystkich złożonych typów danych, nie można bezpiecznie obliczyć łącznego zużycia pamięci przez strukturę, dodając do siebie nominalne alokacje magazynu jej składowych. Ponadto nie można bezpiecznie założyć, że kolejność magazynowania w pamięci jest taka sama jak kolejność deklaracji. Jeśli musisz kontrolować układ magazynu struktury, możesz zastosować atrybut <xref:System.Runtime.InteropServices.StructLayoutAttribute> w instrukcji `Structure`.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto instrukcji `Structure` do zdefiniowania zestawu powiązanych danych dla pracownika. Widoczne jest użycie składowych `Public`, `Friend` i `Private` w celu odzwierciedlenia charakteru elementów danych. Przedstawione są także składowe procedury, właściwości i zdarzenia.  
  
 [!code-vb[VbVbalrStatements#57](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/structure-statement_1.vb)]  
  
## <a name="see-also"></a>Zobacz też  
 [Class, instrukcja](../../../visual-basic/language-reference/statements/class-statement.md)  
 [Instrukcja Interface](../../../visual-basic/language-reference/statements/interface-statement.md)  
 [Instrukcja Module](../../../visual-basic/language-reference/statements/module-statement.md)  
 [Dim, instrukcja](../../../visual-basic/language-reference/statements/dim-statement.md)  
 [Const, instrukcja](../../../visual-basic/language-reference/statements/const-statement.md)  
 [Enum, instrukcja](../../../visual-basic/language-reference/statements/enum-statement.md)  
 [Event, instrukcja](../../../visual-basic/language-reference/statements/event-statement.md)  
 [Operator, instrukcja](../../../visual-basic/language-reference/statements/operator-statement.md)  
 [Instrukcja Property](../../../visual-basic/language-reference/statements/property-statement.md)  
 [Struktury i klasy](../../../visual-basic/programming-guide/language-features/data-types/structures-and-classes.md)
