---
title: Interface — Instrukcja (Visual Basic)
ms.date: 05/12/2018
f1_keywords:
- vb.Interface
helpviewer_keywords:
- interface statement [Visual Basic]
- interfaces [Visual Basic], interface definition
ms.assetid: 8997af73-bda3-4f79-bd41-ca396b610260
ms.openlocfilehash: 68590702835e47e5f0f2e0380bc0fe4017d5eb15
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72582668"
---
# <a name="interface-statement-visual-basic"></a>Interface — Instrukcja (Visual Basic)
Deklaruje nazwę interfejsu i wprowadza definicje elementów członkowskich, które zawiera interfejs.  
  
## <a name="syntax"></a>Składnia  
  
```vb  
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
|`accessmodifier`|Opcjonalny. Może być jedną z następujących czynności:<br /><br /> -   [Public](../../../visual-basic/language-reference/modifiers/public.md)<br />-   [Ochrona](../../../visual-basic/language-reference/modifiers/protected.md)<br />-   [Friend](../../../visual-basic/language-reference/modifiers/friend.md)<br />-   [Private](../../../visual-basic/language-reference/modifiers/private.md)<br />-  [chronionego przyjaciela](../../language-reference/modifiers/protected-friend.md)<br/>- [Private Protected](../../language-reference/modifiers/private-protected.md)<br /><br /> Zobacz [poziomy dostępu w Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).|  
|`Shadows`|Opcjonalny. Zobacz [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md).|  
|`name`|Wymagany. Nazwa tego interfejsu. Zobacz [zadeklarowane nazwy elementów](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).|  
|`Of`|Opcjonalny. Określa, że jest to interfejs generyczny.|  
|`typelist`|Wymagane [w przypadku użycia słowa](../../../visual-basic/language-reference/statements/of-clause.md) kluczowego. Lista parametrów typu dla tego interfejsu. Opcjonalnie każdy parametr typu może być zadeklarowany jako VARIANT przy użyciu `In` i `Out` Modyfikatory ogólne. Zobacz [Lista typów](../../../visual-basic/language-reference/statements/type-list.md).|  
|`Inherits`|Opcjonalny. Wskazuje, że ten interfejs dziedziczy atrybuty i składowe innego interfejsu lub interfejsów. Zobacz [instrukcje Inherits](../../../visual-basic/language-reference/statements/inherits-statement.md).|  
|`interfacenames`|Wymagane, jeśli używasz instrukcji `Inherits`. Nazwy interfejsów, z których pochodzi ten interfejs.|  
|`modifiers`|Opcjonalny. Odpowiednie Modyfikatory dla definiowanego elementu członkowskiego interfejsu.|  
|`Property`|Opcjonalny. Definiuje właściwość, która jest elementem członkowskim interfejsu.|  
|`Function`|Opcjonalny. Definiuje procedurę `Function`, która jest elementem członkowskim interfejsu.|  
|`Sub`|Opcjonalny. Definiuje procedurę `Sub`, która jest elementem członkowskim interfejsu.|  
|`Event`|Opcjonalny. Definiuje zdarzenie, które jest elementem członkowskim interfejsu.|  
|`Interface`|Opcjonalny. Definiuje interfejs, który jest zagnieżdżony w tym interfejsie. Zagnieżdżona definicja interfejsu musi kończyć się instrukcją `End Interface`.|  
|`Class`|Opcjonalny. Definiuje klasę, która jest elementem członkowskim interfejsu. Definicja klasy składowej musi kończyć się instrukcją `End Class`.|  
|`Structure`|Opcjonalny. Definiuje strukturę, która jest elementem członkowskim interfejsu. Definicja struktury elementu członkowskiego musi kończyć się instrukcją `End Structure`.|  
|`membername`|Wymagane dla każdej właściwości, procedury, zdarzenia, interfejsu, klasy lub struktury zdefiniowanej jako element członkowski interfejsu. Nazwa elementu członkowskiego.|  
|`End Interface`|Kończy definicję `Interface`.|  
  
## <a name="remarks"></a>Uwagi  
 *Interfejs* definiuje zestaw elementów członkowskich, takich jak właściwości i procedury, które mogą implementować klasy i struktury. Interfejs definiuje tylko sygnatury elementów członkowskich, a nie ich wewnętrzne działania.  
  
 Klasa lub struktura implementuje interfejs, dostarczając kod dla każdego elementu członkowskiego zdefiniowanego przez interfejs. Na koniec, gdy aplikacja tworzy wystąpienie z tej klasy lub struktury, obiekt istnieje i jest uruchamiany w pamięci. Aby uzyskać więcej informacji, zobacz [obiekty i klasy](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md) i [interfejsy](../../../visual-basic/programming-guide/language-features/interfaces/index.md).  
  
 @No__t_0 można używać tylko na poziomie przestrzeni nazw lub modułu. Oznacza to, że *kontekst deklaracji* dla interfejsu musi być plikiem źródłowym, przestrzenią nazw, klasą, strukturą, modułem lub interfejsem i nie może być procedurą ani blokiem. Aby uzyskać więcej informacji, zobacz [konteksty deklaracji i domyślne poziomy dostępu](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).  
  
 Interfejsy domyślnie mają dostęp do [przyjaciela](../../../visual-basic/language-reference/modifiers/friend.md) . Możesz dostosować ich poziomy dostępu za pomocą modyfikatorów dostępu. Aby uzyskać więcej informacji, zobacz [poziomy dostępu w Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
## <a name="rules"></a>Przepisy  
  
- **Zagnieżdżanie interfejsów.** Można zdefiniować jeden interfejs w innym. Interfejs zewnętrzny jest nazywany interfejsem *zawierającym*, a interfejs wewnętrzny jest nazywany *interfejsem zagnieżdżonym*.  
  
- **Deklaracja elementu członkowskiego.** Gdy deklarujesz właściwość lub procedurę jako element członkowski interfejsu, definiujesz tylko *podpis* tej właściwości lub tej procedury. Obejmuje to typ elementu (właściwość lub procedura), jego parametry i typy parametrów oraz typ zwracany. W związku z tym definicja elementu członkowskiego używa tylko jednej linii kodu, a instrukcje kończące, takie jak `End Function` lub `End Property`, nie są prawidłowe w interfejsie.  
  
     W przeciwieństwie do definiowania wyliczenia lub struktury albo zagnieżdżonej klasy lub interfejsu, konieczne jest uwzględnienie ich składowych danych.  
  
- **Modyfikatory elementów członkowskich.** Nie można używać żadnych modyfikatorów dostępu podczas definiowania elementów członkowskich modułu, ani nie można określać modyfikatora [Shared](../../../visual-basic/language-reference/modifiers/shared.md) ani any z wyjątkiem [przeciążenia](../../../visual-basic/language-reference/modifiers/overloads.md). Można zadeklarować dowolny element członkowski z [cieniami](../../../visual-basic/language-reference/modifiers/shadows.md)i użyć [domyślnego](../../../visual-basic/language-reference/modifiers/default.md) podczas definiowania właściwości, a także [tylko do odczytu](../../../visual-basic/language-reference/modifiers/readonly.md) lub [zapisu](../../../visual-basic/language-reference/modifiers/writeonly.md).  
  
- **Strukturze.** Jeśli interfejs używa [instrukcji Inherits](../../../visual-basic/language-reference/statements/inherits-statement.md), można określić jeden lub więcej interfejsów podstawowych. Można dziedziczyć z dwóch interfejsów, nawet jeśli każda z nich definiuje element członkowski o tej samej nazwie. W takim przypadku kod implementujący musi używać kwalifikacji nazw, aby określić, który element członkowski jest wdrażany.  
  
     Interfejs nie może dziedziczyć z innego interfejsu z bardziej restrykcyjnym poziomem dostępu. Na przykład interfejs `Public` nie może dziedziczyć po interfejsie `Friend`.  
  
     Interfejs nie może dziedziczyć z interfejsu zagnieżdżonego w nim.  
  
- **Realizacji.** Gdy Klasa używa instrukcji [Implements](../../../visual-basic/language-reference/statements/implements-clause.md) w celu zaimplementowania tego interfejsu, musi zaimplementować każdy element członkowski zdefiniowany w interfejsie. Ponadto każdy podpis w kodzie implementującym musi dokładnie pasować do odpowiadającego mu podpisu zdefiniowanego w tym interfejsie. Jednak nazwa elementu członkowskiego w kodzie implementującym nie musi odpowiadać nazwie elementu członkowskiego zdefiniowanego w interfejsie.  
  
     Gdy klasa implementuje procedurę, nie może wyznaczyć procedury jako `Shared`.  
  
- **Właściwość domyślna.** Interfejs może określać co najwyżej jedną właściwość jako *domyślną właściwość*, do której można się odwoływać bez użycia nazwy właściwości. Należy określić taką właściwość, deklarując ją z modyfikatorem [domyślnym](../../../visual-basic/language-reference/modifiers/default.md) .  
  
     Zauważ, że interfejs może definiować właściwość domyślną tylko wtedy, gdy dziedziczy brak.  
  
## <a name="behavior"></a>Zachowanie  
  
- **Poziom dostępu.** Wszyscy członkowie interfejsu mają niejawnie dostęp [publiczny](../../../visual-basic/language-reference/modifiers/public.md) . Nie można użyć żadnego modyfikatora dostępu podczas definiowania elementu członkowskiego. Jednak Klasa implementująca interfejs może zadeklarować poziom dostępu dla każdego zaimplementowanego elementu członkowskiego.  
  
     Jeśli przypiszesz wystąpienie klasy do zmiennej, poziom dostępu jego elementów członkowskich może zależeć od tego, czy typ danych zmiennej jest interfejsem podstawowym, czy klasą implementującą. Ilustruje to poniższy przykład.  
  
     [!code-vb[VbVbalrStatements#39](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#39)]  
  
     Jeśli uzyskujesz dostęp do członków klasy za `varAsInterface`, wszyscy mają dostęp publiczny. Jeśli jednak dostęp do członków odbywa się za pomocą `varAsClass`, procedura `Sub` `doSomething` ma dostęp prywatny.  
  
- **Scope.** Interfejs jest w zakresie w całej jego przestrzeni nazw, klasy, struktury lub modułu.  
  
     Zakres każdego elementu członkowskiego interfejsu jest całym interfejsem.  
  
- **Okres istnienia.** Interfejs nie ma samego okresu istnienia ani nie należy do jego składowych. Gdy klasa implementuje interfejs, a obiekt jest tworzony jako wystąpienie tej klasy, obiekt ma okres istnienia w aplikacji, w której jest uruchomiony. Aby uzyskać więcej informacji, zobacz "okres istnienia" w [instrukcji klasy](../../../visual-basic/language-reference/statements/class-statement.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład używa instrukcji `Interface`, aby zdefiniować interfejs o nazwie `thisInterface`, który musi być zaimplementowany przy użyciu instrukcji `Property` i instrukcji `Function`.  
  
 [!code-vb[VbVbalrStatements#40](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#40)]  
  
 Należy zauważyć, że instrukcje `Property` i `Function` nie wprowadzają bloków kończących się na `End Property` i `End Function` w interfejsie. Interfejs definiuje tylko sygnatury swoich elementów członkowskich. Pełne bloki `Property` i `Function` pojawiają się w klasie, która implementuje `thisInterface`.  
  
## <a name="see-also"></a>Zobacz także

- [Interfejsy](../../../visual-basic/programming-guide/language-features/interfaces/index.md)
- [Class, instrukcja](../../../visual-basic/language-reference/statements/class-statement.md)
- [Module, instrukcja](../../../visual-basic/language-reference/statements/module-statement.md)
- [Structure, instrukcja](../../../visual-basic/language-reference/statements/structure-statement.md)
- [Property, instrukcja](../../../visual-basic/language-reference/statements/property-statement.md)
- [Function, instrukcja](../../../visual-basic/language-reference/statements/function-statement.md)
- [Sub, instrukcja](../../../visual-basic/language-reference/statements/sub-statement.md)
- [Typy ogólne w Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [Wariancje w interfejsach ogólnych](../../programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md)
- [Podczas](../../../visual-basic/language-reference/modifiers/in-generic-modifier.md)
- [Określoną](../../../visual-basic/language-reference/modifiers/out-generic-modifier.md)
