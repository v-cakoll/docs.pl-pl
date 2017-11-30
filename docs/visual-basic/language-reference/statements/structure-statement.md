---
title: "Structure — Instrukcja"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
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
caps.latest.revision: "28"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 43211bb10793acf3bfe0c1d7a35791114170ee7d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="structure-statement"></a>Structure — Instrukcja
Deklaruje nazwę struktury i wprowadza definicje zmiennych, właściwości, zdarzeń i procedur, które obejmuje struktury.  
  
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
|`attributelist`|Opcjonalny. Zobacz [listę atrybutów](../../../visual-basic/language-reference/statements/attribute-list.md).|  
|`accessmodifier`|Opcjonalny. Może to być jedna z następujących czynności:<br /><br /> -   [Publiczna](../../../visual-basic/language-reference/modifiers/public.md)<br />-   [Chronione](../../../visual-basic/language-reference/modifiers/protected.md)<br />-   [Friend](../../../visual-basic/language-reference/modifiers/friend.md)<br />-   [Prywatne](../../../visual-basic/language-reference/modifiers/private.md)<br />-   `Protected Friend`<br /><br /> Zobacz [poziomy w języku Visual Basic dostępu](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).|  
|`Shadows`|Opcjonalny. Zobacz [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md).|  
|`Partial`|Opcjonalny. Wskazuje definicji częściowej struktury. Zobacz [częściowe](../../../visual-basic/language-reference/modifiers/partial.md).|  
|`name`|Wymagany. Nazwa tej struktury. Zobacz [zadeklarowane nazwy elementów](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).|  
|`Of`|Opcjonalny. Określa, że jest to struktura generyczna.|  
|`typelist`|Wymagane w przypadku użycia [z](../../../visual-basic/language-reference/statements/of-clause.md) — słowo kluczowe. Lista parametrów typu dla tej struktury. Zobacz [typu listy](../../../visual-basic/language-reference/statements/type-list.md).|  
|`Implements`|Opcjonalny. Wskazuje, że ta struktura implementuje członkami jeden lub więcej interfejsów. Zobacz [implementuje instrukcji](../../../visual-basic/language-reference/statements/implements-statement.md).|  
|`interfacenames`|Wymagane w przypadku użycia `Implements` instrukcji. Nazwy interfejsów, które implementuje tej struktury.|  
|`datamemberdeclarations`|Wymagany. Zero lub więcej `Const`, `Dim`, `Enum`, lub `Event` instrukcje deklarowanie *elementy członkowskie danych* struktury.|  
|`methodmemberdeclarations`|Opcjonalny. Deklaracje zero lub więcej `Function`, `Operator`, `Property`, lub `Sub` procedur, które stanowią *członków metody* struktury.|  
|`End Structure`|Wymagany. Kończy `Structure` definicji.|  
  
## <a name="remarks"></a>Uwagi  
 `Structure` Instrukcji definiuje typ wartości złożonego, który można dostosować. A *struktury* jest generalizacji typu zdefiniowanego przez użytkownika (UDT) poprzednich wersji programu Visual Basic. Aby uzyskać więcej informacji, zobacz [struktury](../../../visual-basic/programming-guide/language-features/data-types/structures.md).  
  
 Struktury obsługuje wiele te same funkcje co klasy. Na przykład struktury mogą mieć właściwości i procedury, miały zaimplementowane interfejsy i może mieć sparametryzowanych konstruktorów. Istnieją jednak istotne różnice między struktury i klasy w obszarach, takich jak dziedziczenia, deklaracje i użycia. Również typy referencyjne występują następujące klasy i struktury są typów wartości. Aby uzyskać więcej informacji, zobacz [struktury i klasy](../../../visual-basic/programming-guide/language-features/data-types/structures-and-classes.md).  
  
 Można użyć `Structure` tylko na poziomie przestrzeni nazw lub modułu. Oznacza to, że *kontekście deklaracji* przez strukturę musi zawierać plik źródłowy, przestrzeni nazw, klasy, struktury, modułu lub interfejsu i nie może być procedurę lub blok. Aby uzyskać więcej informacji, zobacz [kontekst deklaracji i domyślne poziomy dostępu](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).  
  
 Domyślnie struktury [Friend](../../../visual-basic/language-reference/modifiers/friend.md) dostępu. Można dostosować ich poziomy dostępu z modyfikatorów dostępu. Aby uzyskać więcej informacji, zobacz [poziomy w języku Visual Basic dostępu](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
## <a name="rules"></a>Reguły  
  
-   **Zagnieżdżania.** Można określić jedną struktury w innym. Zewnętrzny element jest nazywany *strukturze*, i struktura wewnętrznej nazywana jest *zagnieżdżone struktury*. Jednak nie masz dostępu do elementów zagnieżdżonej konstrukcji za pośrednictwem struktury zawierającego. Zamiast tego należy zadeklarować zmiennej typu zagnieżdżonego struktury danych.  
  
-   **Deklaracja elementu członkowskiego.** Musisz zadeklarować każdy element członkowski struktury. Nie może być elementem członkowskim struktury [chronione](../../../visual-basic/language-reference/modifiers/protected.md) lub `Protected Friend` ponieważ nic nie może dziedziczyć z strukturze. Struktury, jednak może być `Protected` lub `Protected Friend`.  
  
     Można zadeklarować zero lub więcej zmiennych udostępniana lub udostępniana, standardowych zdarzeń w strukturze. Nawet jeśli niektóre z nich jest udostępniana nie może mieć tylko stałe, właściwości i procedur.  
  
-   **Inicjowanie.** Nie można zainicjować wartość dowolnego elementu członkowskiego danych udostępniana struktury jako części swojej deklaracji. Musisz zainicjować element członkowski danych za pomocą sparametryzowanym konstruktorze struktury lub przypisać wartości do elementu członkowskiego, po utworzeniu wystąpienia struktury.  
  
-   **Dziedziczenie.** Struktura nie może dziedziczyć z dowolnego typu innego niż <xref:System.ValueType>, z której dziedziczy wszystkie struktury. W szczególności co struktura nie może dziedziczyć z innego.  
  
     Nie można użyć [dziedziczy instrukcję](../../../visual-basic/language-reference/statements/inherits-statement.md) w definicji struktury, nawet do określenia <xref:System.ValueType>.  
  
-   **Implementacja.** Jeśli używa struktury [Implements — instrukcja](../../../visual-basic/language-reference/statements/implements-statement.md), musisz zaimplementować każdego elementu członkowskiego zdefiniowane przez każdego interfejsu należy określić w `interfacenames`.  
  
-   **Domyślna właściwość.** Struktura można określić co najwyżej jedną właściwość jako jego *domyślna właściwość*za pomocą [domyślne](../../../visual-basic/language-reference/modifiers/default.md) modyfikator. Aby uzyskać więcej informacji, zobacz [domyślne](../../../visual-basic/language-reference/modifiers/default.md).  
  
## <a name="behavior"></a>Zachowanie  
  
-   **Poziom dostępu.** W ramach struktury mogą zadeklarować każdy element członkowski z poziomu dostępu. Domyślnie wszystkie elementy członkowskie struktury [publicznego](../../../visual-basic/language-reference/modifiers/public.md) dostępu. Należy pamiętać, że jeśli struktura się bardziej ograniczony poziom dostępu, to automatycznie ogranicza dostęp do jej elementów członkowskich, nawet jeśli dopasowywanie ich poziomy dostępu z modyfikatorów dostępu.  
  
-   **Zakres.** Struktura jest w zakresie w całym jej zawierającego przestrzeni nazw, klasy, struktury lub modułu.  
  
     Zakres każdy element członkowski struktury jest cała struktura.  
  
-   **Okres istnienia.** Struktura nie może mieć okres istnienia. Zamiast każde wystąpienie tej struktury ma okres istnienia niezależnie od innych wystąpień.  
  
     Okres istnienia wystąpienia uruchamia się, gdy jest tworzony przez [operatora New](../../../visual-basic/language-reference/operators/new-operator.md) klauzuli. Go kończy się po zakończeniu okresu istnienia zmiennej, która przechowuje.  
  
     Nie można rozszerzyć okres istnienia wystąpienia struktury. Zbliżenie do struktury statycznej funkcji jest udostępniana przez moduł. Aby uzyskać więcej informacji, zobacz [Module — instrukcja](../../../visual-basic/language-reference/statements/module-statement.md).  
  
     Elementy członkowskie struktury okresy istnienia w zależności od tego, jak i gdzie są zadeklarowane. Aby uzyskać więcej informacji, zobacz "Istnienia" w [Class — instrukcja](../../../visual-basic/language-reference/statements/class-statement.md).  
  
-   **Kwalifikacji.** Kod poza strukturą musi nazwy członka o nazwie tej struktury.  
  
     Kod wewnątrz struktury zagnieżdżone wykonuje niekwalifikowane odwołanie do elementu programistycznego, Visual Basic wyszukuje element najpierw w strukturze zagnieżdżonych, następnie w jej zawierającego struktury i tak dalej do najbardziej zewnętrznego elementu zawierającego. Aby uzyskać więcej informacji, zobacz [odwołania do elementów zadeklarowany](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).  
  
-   **Zużycie pamięci.** Podobnie jak w przypadku wszystkich złożone typy danych, nie można bezpiecznie obliczania zużycia całkowitej ilości pamięci struktury przez dodanie alokacji magazynu nominalnego jego elementów członkowskich. Ponadto nie można bezpiecznie zakładać, że kolejność magazynu w pamięci jest taka sama jak zamówienia deklaracji. Jeśli potrzebujesz do sterowania układem magazynu struktury, możesz zastosować <xref:System.Runtime.InteropServices.StructLayoutAttribute> atrybutu `Structure` instrukcji.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto `Structure` instrukcji do zdefiniowania zestawu powiązanych danych do pracownika. Widoczny jest użycie `Public`, `Friend`, i `Private` elementy członkowskie, aby odzwierciedlić charakter elementów danych. Przedstawia on także procedury, właściwości i zdarzenia elementów członkowskich.  
  
 [!code-vb[VbVbalrStatements#57](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/structure-statement_1.vb)]  
  
## <a name="see-also"></a>Zobacz też  
 [Class — instrukcja](../../../visual-basic/language-reference/statements/class-statement.md)  
 [Interface — instrukcja](../../../visual-basic/language-reference/statements/interface-statement.md)  
 [Module — instrukcja](../../../visual-basic/language-reference/statements/module-statement.md)  
 [Dim — instrukcja](../../../visual-basic/language-reference/statements/dim-statement.md)  
 [Const — instrukcja](../../../visual-basic/language-reference/statements/const-statement.md)  
 [Enum — instrukcja](../../../visual-basic/language-reference/statements/enum-statement.md)  
 [Event — instrukcja](../../../visual-basic/language-reference/statements/event-statement.md)  
 [Operator — instrukcja](../../../visual-basic/language-reference/statements/operator-statement.md)  
 [Property — instrukcja](../../../visual-basic/language-reference/statements/property-statement.md)  
 [Struktury i klasy](../../../visual-basic/programming-guide/language-features/data-types/structures-and-classes.md)
