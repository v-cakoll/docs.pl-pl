---
title: "Interface — Instrukcja (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.Interface
helpviewer_keywords:
- interface statement [Visual Basic]
- interfaces [Visual Basic], interface definition
ms.assetid: 8997af73-bda3-4f79-bd41-ca396b610260
caps.latest.revision: "26"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 9418dc86ac6947ae951cb8fb757aed6e092a6668
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="interface-statement-visual-basic"></a>Interface — Instrukcja (Visual Basic)
Deklaruje nazwę interfejsu i wprowadza definicje elementów członkowskich, które obejmuje interfejsu.  
  
## <a name="syntax"></a>Składnia  
  
```  
[ <attributelist> ] [ accessmodifier ] [ Shadows ] _  
Interface name [ ( Of typelist ) ]  
    [ Inherits interfacenames ]  
    [ [ modifiers ] Property membername ]  
    [ [ modifiers ] Function membername ]  
    [ [ modifiers ] Sub membername ]  
    [ [ modifiers ] Event membername ]  
    [ [ modifiers ] Interface membername ]  
    [ [ modifiers ] Class membername ]  
    [ [ modifiers ] Structure membername ]  
End Interface  
```  
  
## <a name="parts"></a>Części  
  
|Termin|Definicja|  
|---|---|  
|`attributelist`|Opcjonalny. Zobacz [listę atrybutów](../../../visual-basic/language-reference/statements/attribute-list.md).|  
|`accessmodifier`|Opcjonalny. Może to być jedna z następujących czynności:<br /><br /> -   [Publiczna](../../../visual-basic/language-reference/modifiers/public.md)<br />-   [Chronione](../../../visual-basic/language-reference/modifiers/protected.md)<br />-   [Friend](../../../visual-basic/language-reference/modifiers/friend.md)<br />-   [Prywatne](../../../visual-basic/language-reference/modifiers/private.md)<br />-   `Protected Friend`<br /><br /> Zobacz [poziomy w języku Visual Basic dostępu](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).|  
|`Shadows`|Opcjonalny. Zobacz [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md).|  
|`name`|Wymagany. Nazwa tego interfejsu. Zobacz [zadeklarowane nazwy elementów](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).|  
|`Of`|Opcjonalny. Określa, że jest to interfejs generyczny.|  
|`typelist`|Wymagane w przypadku użycia [z](../../../visual-basic/language-reference/statements/of-clause.md) — słowo kluczowe. Lista parametrów typu dla tego interfejsu. Opcjonalnie, każdy parametr typu mogą być deklarowane variant przy użyciu `In` i `Out` ogólnego modyfikatorów. Zobacz [typu listy](../../../visual-basic/language-reference/statements/type-list.md).|  
|`Inherits`|Opcjonalny. Wskazuje, że ten interfejs dziedziczy atrybuty i elementy członkowskie innego interfejsu lub interfejsów. Zobacz [Inherits — instrukcja](../../../visual-basic/language-reference/statements/inherits-statement.md).|  
|`interfacenames`|Wymagane w przypadku użycia `Inherits` instrukcji. Nazwy interfejsów, spośród których pochodzi ten interfejs.|  
|`modifiers`|Opcjonalny. Modyfikatory odpowiednie dla elementu członkowskiego interfejsu, jest zdefiniowany.|  
|`Property`|Opcjonalny. Definiuje właściwości, która jest elementem członkowskim interfejsu.|  
|`Function`|Opcjonalny. Definiuje `Function` procedury, która jest elementem członkowskim interfejsu.|  
|`Sub`|Opcjonalny. Definiuje `Sub` procedury, która jest elementem członkowskim interfejsu.|  
|`Event`|Opcjonalny. Definiuje zdarzenia, które jest elementem członkowskim interfejsu.|  
|`Interface`|Opcjonalny. Definiuje interfejs, który jest zagnieżdżony w obrębie tego interfejsu. Definicja interfejsu zagnieżdżonych musi kończyć się `End Interface` instrukcji.|  
|`Class`|Opcjonalny. Definiuje klasę, która jest elementem członkowskim interfejsu. Definicji elementu członkowskiego klasy musi kończyć się `End Class` instrukcji.|  
|`Structure`|Opcjonalny. Definiuje strukturę, która jest elementem członkowskim interfejsu. Definicji elementu członkowskiego struktury musi kończyć się `End Structure` instrukcji.|  
|`membername`|Wymagany dla każdej właściwości, procedury, zdarzenia, interfejsu, klasy lub struktury zdefiniowany jako element członkowski interfejsu. Nazwa elementu członkowskiego.|  
|`End Interface`|Kończy `Interface` definicji.|  
  
## <a name="remarks"></a>Uwagi  
 *Interfejsu* definiuje zestaw elementów członkowskich, takich jak zaimplementować procedur, które klasy i struktury i właściwości. Interfejs definiuje tylko podpisy elementów członkowskich, a nie ich wewnętrzne działanie.  
  
 Klasy lub struktury implementuje interfejs, podając kod dla każdego elementu członkowskiego zdefiniowany przez interfejs. Na koniec gdy aplikacja tworzy wystąpienie z tej klasy lub struktury, obiekt istnieje i jest uruchamiany w pamięci. Aby uzyskać więcej informacji, zobacz [obiekty i klasy](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md) i [interfejsów](../../../visual-basic/programming-guide/language-features/interfaces/index.md).  
  
 Można użyć `Interface` tylko na poziomie przestrzeni nazw lub modułu. Oznacza to, że *kontekście deklaracji* przez interfejs musi zawierać plik źródłowy, przestrzeni nazw, klasy, struktury, modułu lub interfejsu i nie może być procedurę lub blok. Aby uzyskać więcej informacji, zobacz [kontekst deklaracji i domyślne poziomy dostępu](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).  
  
 Interfejsy domyślną [Friend](../../../visual-basic/language-reference/modifiers/friend.md) dostępu. Można dostosować ich poziomy dostępu z modyfikatorów dostępu. Aby uzyskać więcej informacji, zobacz [poziomy w języku Visual Basic dostępu](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
## <a name="rules"></a>Reguły  
  
-   **Zagnieżdżania interfejsów.** Można określić jeden interfejs w innym. Wywoływany jest interfejs zewnętrzne *interfejsem*, i jest nazywany wewnętrzny interfejs *zagnieżdżonego interfejsu*.  
  
-   **Deklaracja elementu członkowskiego.** Przy deklarowaniu właściwość lub procedura jako element członkowski interfejsu są definiowane tylko *podpisu* właściwość lub procedura. W tym typ elementu (właściwość lub procedura), jego parametrów i typy parametrów i jej typu zwracanego. W związku z tym definicji elementu członkowskiego używa tylko jeden wiersz kodu i zakończenia oświadczeń `End Function` lub `End Property` nie są prawidłowe w interfejsie.  
  
     Z kolei definiując wyliczenie lub struktury, lub zagnieżdżone klasy lub interfejsu, jest konieczne jest stosowanie ich elementy członkowskie danych.  
  
-   **Modyfikatory elementu członkowskiego.** Nie można użyć dowolnego modyfikatorów dostępu podczas definiowania modułu elementów członkowskich nie można określić [Shared](../../../visual-basic/language-reference/modifiers/shared.md) lub dowolnego modyfikator procedury, z wyjątkiem [Overloads](../../../visual-basic/language-reference/modifiers/overloads.md). Można zadeklarować członków z [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md), można użyć [domyślne](../../../visual-basic/language-reference/modifiers/default.md) podczas definiowania właściwości, a także [tylko do odczytu](../../../visual-basic/language-reference/modifiers/readonly.md) lub [WriteOnly](../../../visual-basic/language-reference/modifiers/writeonly.md).  
  
-   **Dziedziczenie.** Jeśli w interfejsie są używane [dziedziczy instrukcję](../../../visual-basic/language-reference/statements/inherits-statement.md), można określić co najmniej jeden interfejsach podstawowych. Może dziedziczyć z dwóch interfejsów, nawet jeśli ich zdefiniować element członkowski o takiej samej nazwie. Jeśli to zrobisz, więc implementującej kodu musi umożliwia określenie, który element członkowski implementuje kwantyfikacja nazwy.  
  
     Interfejs nie może dziedziczyć z innego interfejsu z bardziej restrykcyjne poziom dostępu. Na przykład `Public` interfejsu nie może dziedziczyć z `Friend` interfejsu.  
  
     Interfejs nie może dziedziczyć z interfejsu w nim zagnieżdżony.  
  
-   **Implementacja.** Gdy używa klasy [implementuje](../../../visual-basic/language-reference/statements/implements-clause.md) instrukcji, aby zaimplementować ten interfejs musi implementować każdego elementu członkowskiego zdefiniowanego w interfejsie. Ponadto sygnatur w kodzie implementującej musi dokładnie odpowiadać odpowiedni podpis zdefiniowane w tym interfejsie. Nazwa elementu członkowskiego w kodzie implementujący nie ma jednak jest zgodna z nazwą elementu członkowskiego, zgodnie z definicją w interfejsie.  
  
     Gdy klasa implementuje procedurę, nie można wyznaczyć procedury jako `Shared`.  
  
-   **Domyślna właściwość.** Interfejs można określić co najwyżej jedną właściwość jako jego *domyślna właściwość*, którego można odwoływać się bez użycia nazwy właściwości. Określ takich właściwości ona z [domyślne](../../../visual-basic/language-reference/modifiers/default.md) modyfikator.  
  
     Zwróć uwagę, że oznacza to, że interfejs można zdefiniować właściwości domyślnej tylko wtedy, gdy żaden dziedziczy.  
  
## <a name="behavior"></a>Zachowanie  
  
-   **Poziom dostępu.** Wszystkie elementy członkowskie interfejsu niejawnie ma [publicznego](../../../visual-basic/language-reference/modifiers/public.md) dostępu. Nie można użyć dowolnego modyfikator dostępu podczas definiowania elementu członkowskiego. Jednak klasy implementującej interfejs można zadeklarować poziom dostępu dla każdego członka zaimplementowany.  
  
     Jeśli wystąpienie klasy jest przypisany do zmiennej, poziom dostępu do jego elementów członkowskich może zależeć od tego, czy typ danych zmiennej jest powiązanego interfejsu lub klasy implementującej. Ilustruje to poniższy przykład.  
  
     [!code-vb[VbVbalrStatements#39](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/interface-statement_1.vb)]  
  
     Jeśli dostęp do elementów członkowskich klasy za pomocą `varAsInterface`, wszystkie mają dostęp publiczny. Jednak jeśli dostęp do elementów członkowskich za pomocą `varAsClass`, `Sub` procedury `doSomething` ma dostęp do prywatnego.  
  
-   **Zakres.** Interfejs jest w zakresie w całej przestrzeni nazw, klasy, struktury lub modułu.  
  
     Zakres każdego członka interfejsu jest cały interfejs.  
  
-   **Okres istnienia.** Interfejs nie może mieć okres istnienia, podobnie jak jego elementów członkowskich. Gdy klasa implementuje interfejs i obiekt jest tworzony jako wystąpienie że klasy, obiekt ma istnienia aplikacji, w którym jest uruchomiony. Aby uzyskać więcej informacji, zobacz "Istnienia" w [Class — instrukcja](../../../visual-basic/language-reference/statements/class-statement.md).  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto `Interface` instrukcji, aby zdefiniować interfejsu o nazwie `thisInterface`, musi zostać wdrożone z `Property` instrukcji i `Function` instrukcji.  
  
 [!code-vb[VbVbalrStatements#40](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/interface-statement_2.vb)]  
  
 Należy pamiętać, że `Property` i `Function` instrukcje nie znajdą się bloki kończąc `End Property` i `End Function` w interfejsie. Interfejs definiuje sygnatur jej elementów członkowskich. Pełny `Property` i `Function` bloki są wyświetlane w klasie, który implementuje `thisInterface`.  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy](../../../visual-basic/programming-guide/language-features/interfaces/index.md)  
 [Class — instrukcja](../../../visual-basic/language-reference/statements/class-statement.md)  
 [Module — instrukcja](../../../visual-basic/language-reference/statements/module-statement.md)  
 [Structure — instrukcja](../../../visual-basic/language-reference/statements/structure-statement.md)  
 [Property — instrukcja](../../../visual-basic/language-reference/statements/property-statement.md)  
 [Function — instrukcja](../../../visual-basic/language-reference/statements/function-statement.md)  
 [Sub — instrukcja](../../../visual-basic/language-reference/statements/sub-statement.md)  
 [Typy ogólne w Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)  
 [Wariancje w interfejsach](../../programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md)  
 [W](../../../visual-basic/language-reference/modifiers/in-generic-modifier.md)  
 [Limit](../../../visual-basic/language-reference/modifiers/out-generic-modifier.md)
