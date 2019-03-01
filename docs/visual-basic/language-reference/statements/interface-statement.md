---
title: Interface — Instrukcja (Visual Basic)
ms.date: 05/12/2018
f1_keywords:
- vb.Interface
helpviewer_keywords:
- interface statement [Visual Basic]
- interfaces [Visual Basic], interface definition
ms.assetid: 8997af73-bda3-4f79-bd41-ca396b610260
ms.openlocfilehash: f65875caa16bfe00866cc3cd6fd0c0b22b034576
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2019
ms.locfileid: "56970535"
---
# <a name="interface-statement-visual-basic"></a>Interface — Instrukcja (Visual Basic)
Deklaruje nazwę interfejsu i wprowadza definicje elementów członkowskich, które obejmuje interfejs.  
  
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
|`attributelist`|Opcjonalna. Zobacz temat [Lista atrybutów](../../../visual-basic/language-reference/statements/attribute-list.md).|  
|`accessmodifier`|Opcjonalna. Może to być jeden z następujących elementów:<br /><br /> -   [Public](../../../visual-basic/language-reference/modifiers/public.md)<br />-   [Protected](../../../visual-basic/language-reference/modifiers/protected.md)<br />-   [Friend](../../../visual-basic/language-reference/modifiers/friend.md)<br />-   [Private](../../../visual-basic/language-reference/modifiers/private.md)<br />-  [Protected Friend](../../language-reference/modifiers/protected-friend.md)<br/>- [Private protected](../../language-reference/modifiers/private-protected.md)<br /><br /> Zobacz temat [Poziomy dostępu w języku Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).|  
|`Shadows`|Opcjonalna. Zobacz [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md).|  
|`name`|Wymagana. Nazwa tego interfejsu. Zobacz [Zadeklarowane nazwy elementów](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).|  
|`Of`|Opcjonalna. Określa, że jest to interfejs generyczny.|  
|`typelist`|Wymagane w przypadku użycia [z](../../../visual-basic/language-reference/statements/of-clause.md) — słowo kluczowe. Lista parametrów typu dla tego interfejsu. Opcjonalnie, każdy parametr typu mogą być deklarowane wariant przy użyciu `In` i `Out` ogólnego modyfikatorów. Zobacz [Lista typów](../../../visual-basic/language-reference/statements/type-list.md).|  
|`Inherits`|Opcjonalna. Wskazuje, że ten interfejs dziedziczy atrybuty i elementy członkowskie innego interfejsu lub interfejsów. Zobacz [Inherits — instrukcja](../../../visual-basic/language-reference/statements/inherits-statement.md).|  
|`interfacenames`|Wymagane w przypadku użycia instrukcji `Inherits`. Nazwy interfejsów, z których pochodzi ten interfejs.|  
|`modifiers`|Opcjonalna. Odpowiednie modyfikatorów definiowanego członka interfejsu.|  
|`Property`|Opcjonalna. Definiuje właściwości, która jest elementem członkowskim interfejsu.|  
|`Function`|Opcjonalna. Definiuje `Function` procedury, która jest elementem członkowskim interfejsu.|  
|`Sub`|Opcjonalna. Definiuje `Sub` procedury, która jest elementem członkowskim interfejsu.|  
|`Event`|Opcjonalna. Określa zdarzenie, które jest członkiem interfejsu.|  
|`Interface`|Opcjonalna. Definiuje interfejs, który jest zagnieżdżony w ramach tego interfejsu. Definicja interfejsu zagnieżdżonych musi kończyć się `End Interface` instrukcji.|  
|`Class`|Opcjonalna. Definiuje klasę, która jest elementem członkowskim interfejsu. Definicja klasy elementu członkowskiego musi kończyć się `End Class` instrukcji.|  
|`Structure`|Opcjonalna. Definiuje strukturę, która jest elementem członkowskim interfejsu. Definicja struktury elementu członkowskiego musi kończyć się `End Structure` instrukcji.|  
|`membername`|Wymagane dla każdej właściwości, procedury, zdarzenia, interfejsu, klasy lub struktury zdefiniowany jako członka interfejsu. Nazwa elementu członkowskiego.|  
|`End Interface`|Kończy definicję `Interface`.|  
  
## <a name="remarks"></a>Uwagi  
 *Interfejsu* definiuje zestaw elementów członkowskich, takie jak właściwości i procedury, które klasy i struktury można zaimplementować. Interfejs definiuje tylko podpisów elementów członkowskich, a nie ich wewnętrzne działanie.  
  
 Klasa lub struktura implementuje interfejs poprzez dostarczanie kodu dla każdego elementu członkowskiego zdefiniowane przez interfejs. Na koniec gdy aplikacja tworzy wystąpienie z tej klasy lub struktury, obiekt istnieje i jest uruchamiany w pamięci. Aby uzyskać więcej informacji, zobacz [obiekty i klasy](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md) i [interfejsów](../../../visual-basic/programming-guide/language-features/interfaces/index.md).  
  
 Instrukcji `Interface` można użyć tylko na poziomie przestrzeni nazw lub modułu. Oznacza to, że *kontekst deklaracji* interfejs musi być plikiem źródłowym, przestrzeń nazw, klasy, struktury, modułu lub interfejsu i nie może być procedurą lub blokiem. Aby uzyskać więcej informacji, zobacz [Kontekst deklaracji i domyślne poziomy dostępu](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).  
  
 Interfejsy domyślnie [Friend](../../../visual-basic/language-reference/modifiers/friend.md) dostępu. Poziomy dostępu można zmienić za pomocą modyfikatorów dostępu. Aby uzyskać więcej informacji, zobacz temat [Poziomy dostępu w języku Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
## <a name="rules"></a>reguły  
  
-   **Zagnieżdżanie interfejsów.** Można zdefiniować jeden interfejs w innym. Wywoływany jest interfejs zewnętrzny *zawierający interfejs*, i wywoływany jest interfejs wewnętrzny *zagnieżdżonego interfejsu*.  
  
-   **Deklaracja składowej.** Kiedy Deklarujesz właściwość lub procedura jako składową interfejsu, jest definiowana tylko *podpisu* właściwość lub procedurę. Obejmuje to typ elementu (właściwość lub procedura), jego parametry i typy parametrów i jego typem zwracanym. W związku z tym definicji elementu członkowskiego wykorzystuje tylko jeden wiersz kodu i kończący oświadczeń `End Function` lub `End Property` nie są prawidłowe w interfejsie.  
  
     Natomiast gdy zdefiniujesz wyliczenie lub struktury, lub zagnieżdżona klasa lub interfejs jest konieczne uwzględnienie ich składowych danych.  
  
-   **Element członkowski modyfikatorów.** Nie można użyć dowolnego modyfikatorów dostępu podczas definiowania elementów członkowskich w module nie można określić [Shared](../../../visual-basic/language-reference/modifiers/shared.md) lub dowolnym modyfikator procedury, z wyjątkiem [przeciążenia](../../../visual-basic/language-reference/modifiers/overloads.md). Można zadeklarować dowolnego elementu członkowskiego z [cieni](../../../visual-basic/language-reference/modifiers/shadows.md), można użyć [domyślne](../../../visual-basic/language-reference/modifiers/default.md) podczas definiowania właściwość także [tylko do odczytu](../../../visual-basic/language-reference/modifiers/readonly.md) lub [WriteOnly](../../../visual-basic/language-reference/modifiers/writeonly.md).  
  
-   **Dziedziczenie.** Jeśli korzysta z interfejsu [dziedziczy instrukcję](../../../visual-basic/language-reference/statements/inherits-statement.md), można określić jeden lub więcej podstawowych interfejsów. Dwa interfejsy mogą dziedziczyć, nawet wtedy, gdy każda definiują element członkowski o takiej samej nazwie. Jeśli to zrobisz, więc w kodzie implementującym musi być określona elementu członkowskiego, który implementuje kwantyfikacja nazwy.  
  
     Interfejs nie może dziedziczyć z innego interfejsu z bardziej restrykcyjny poziom dostępu. Na przykład `Public` interfejs nie może dziedziczyć `Friend` interfejsu.  
  
     Interfejs nie może dziedziczyć z interfejsu w nim zagnieżdżony.  
  
-   **Implementacja.** Gdy klasa używa [implementuje](../../../visual-basic/language-reference/statements/implements-clause.md) instrukcję, aby zaimplementować ten interfejs musi implementować, każdy element członkowski zdefiniowany w interfejsie. Ponadto każdy podpis w kodzie implementującym musi dokładnie odpowiadać odpowiedni podpis, które są zdefiniowane w tym interfejsie. Nazwa elementu członkowskiego w kodzie implementującym nie ma jednak jest zgodna z nazwą elementu członkowskiego, zgodnie z definicją w interfejsie.  
  
     Gdy klasa implementuje procedurę, nie może go wyznaczyć procedurze jako `Shared`.  
  
-   **Właściwość domyślna.** Interfejs można określić co najwyżej jedną właściwość jako jego *właściwość domyślna*, mogą być przywoływane bez użycia nazwy właściwości. Określ taką właściwość deklarując ją za pomocą [domyślne](../../../visual-basic/language-reference/modifiers/default.md) modyfikator.  
  
     Należy zauważyć, że oznacza to, że interfejs można zdefiniować właściwość domyślną tylko wtedy, gdy brak dziedziczy.  
  
## <a name="behavior"></a>Zachowanie  
  
-   **Poziom dostępu.** Wszyscy członkowie interfejsu niejawnie ma [publicznych](../../../visual-basic/language-reference/modifiers/public.md) dostępu. Nie można użyć dowolnego modyfikator dostępu, podczas definiowania członka. Jednak klasy implementującej interfejs może zadeklarować poziom dostępu dla każdego członka zaimplementowane.  
  
     Jeśli wystąpienie klasy jest przypisany do zmiennej, poziom dostępu członków może zależeć od tego, czy typ danych zmiennej jest podstawowym interfejsu lub klasy implementującej. Ilustruje to poniższy przykład.  
  
     [!code-vb[VbVbalrStatements#39](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#39)]  
  
     Jeśli uzyskujesz dostęp do członków klasy za pomocą `varAsInterface`, wszystkie one mają dostęp publiczny. Jednak jeśli uzyskujesz dostęp do członków przy użyciu `varAsClass`, `Sub` procedury `doSomething` ma dostęp prywatny.  
  
-   **Zakres.** Interfejs jest w zakresie przestrzeni nazw, klasy, struktury lub modułu.  
  
     Zakres każdego członka interfejsu jest cały interfejs.  
  
-   **Okres istnienia.** Interfejs nie ma własnego okresu istnienia, podobnie jak jego członków. Gdy klasa implementuje interfejs i obiekt jest tworzona jako wystąpienie że klasy, obiekt ma okres istnienia aplikacji, w którym jest uruchomiony. Aby uzyskać więcej informacji, zobacz "Okres istnienia" w artykule [Class, instrukcja](../../../visual-basic/language-reference/statements/class-statement.md).  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto `Interface` instrukcji, aby zdefiniować interfejs o nazwie `thisInterface`, muszą być zaimplementowane przy użyciu `Property` instrukcji i `Function` instrukcji.  
  
 [!code-vb[VbVbalrStatements#40](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#40)]  
  
 Należy pamiętać, że `Property` i `Function` instrukcje nie wprowadzają bloków, kończąc `End Property` i `End Function` w interfejsie. Interfejs definiuje tylko podpisy składowych. Pełny `Property` i `Function` bloki są wyświetlane w klasie, która implementuje `thisInterface`.  
  
## <a name="see-also"></a>Zobacz także
- [Interfejsy](../../../visual-basic/programming-guide/language-features/interfaces/index.md)
- [Class, instrukcja](../../../visual-basic/language-reference/statements/class-statement.md)
- [Instrukcja Module](../../../visual-basic/language-reference/statements/module-statement.md)
- [Structure, instrukcja](../../../visual-basic/language-reference/statements/structure-statement.md)
- [Instrukcja Property](../../../visual-basic/language-reference/statements/property-statement.md)
- [Function, instrukcja](../../../visual-basic/language-reference/statements/function-statement.md)
- [Sub, instrukcja](../../../visual-basic/language-reference/statements/sub-statement.md)
- [Typy ogólne w Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [Wariancje w interfejsach ogólnych](../../programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md)
- [W](../../../visual-basic/language-reference/modifiers/in-generic-modifier.md)
- [limit](../../../visual-basic/language-reference/modifiers/out-generic-modifier.md)
