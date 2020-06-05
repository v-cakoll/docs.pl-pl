---
title: Interface, instrukcja
ms.date: 05/12/2018
f1_keywords:
- vb.Interface
helpviewer_keywords:
- interface statement [Visual Basic]
- interfaces [Visual Basic], interface definition
ms.assetid: 8997af73-bda3-4f79-bd41-ca396b610260
ms.openlocfilehash: 02d258084aaaa53dcc559cfaa0dec27556351037
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404489"
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
|`attributelist`|Opcjonalny. Zobacz [listę atrybutów](attribute-list.md).|  
|`accessmodifier`|Opcjonalny. Może być jedną z następujących czynności:<br /><br /> -   [Społeczeństwo](../modifiers/public.md)<br />-   [Chronione](../modifiers/protected.md)<br />-   [Osoby](../modifiers/friend.md)<br />-   [Użytek](../modifiers/private.md)<br />-  [Chroniony znajomy](../modifiers/protected-friend.md)<br/>- [Prywatne chronione](../modifiers/private-protected.md)<br /><br /> Zobacz [poziomy dostępu w Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md).|  
|`Shadows`|Opcjonalny. Zobacz [Shadows](../modifiers/shadows.md).|  
|`name`|Wymagany. Nazwa tego interfejsu. Zobacz [zadeklarowane nazwy elementów](../../programming-guide/language-features/declared-elements/declared-element-names.md).|  
|`Of`|Opcjonalny. Określa, że jest to interfejs generyczny.|  
|`typelist`|Wymagane [w przypadku użycia słowa](of-clause.md) kluczowego. Lista parametrów typu dla tego interfejsu. Opcjonalnie każdy parametr typu może być zadeklarowany jako VARIANT przy użyciu `In` i `Out` Modyfikatory ogólne. Zobacz [Lista typów](type-list.md).|  
|`Inherits`|Opcjonalny. Wskazuje, że ten interfejs dziedziczy atrybuty i składowe innego interfejsu lub interfejsów. Zobacz [instrukcje Inherits](inherits-statement.md).|  
|`interfacenames`|Wymagane, jeśli używasz `Inherits` instrukcji. Nazwy interfejsów, z których pochodzi ten interfejs.|  
|`modifiers`|Opcjonalny. Odpowiednie Modyfikatory dla definiowanego elementu członkowskiego interfejsu.|  
|`Property`|Opcjonalny. Definiuje właściwość, która jest elementem członkowskim interfejsu.|  
|`Function`|Opcjonalny. Definiuje `Function` procedurę, która jest elementem członkowskim interfejsu.|  
|`Sub`|Opcjonalny. Definiuje `Sub` procedurę, która jest elementem członkowskim interfejsu.|  
|`Event`|Opcjonalny. Definiuje zdarzenie, które jest elementem członkowskim interfejsu.|  
|`Interface`|Opcjonalny. Definiuje interfejs, który jest zagnieżdżony w tym interfejsie. Zagnieżdżona definicja interfejsu musi kończyć się `End Interface` instrukcją.|  
|`Class`|Opcjonalny. Definiuje klasę, która jest elementem członkowskim interfejsu. Definicja klasy składowej musi kończyć się `End Class` instrukcją.|  
|`Structure`|Opcjonalny. Definiuje strukturę, która jest elementem członkowskim interfejsu. Definicja struktury elementu członkowskiego musi kończyć się `End Structure` instrukcją.|  
|`membername`|Wymagane dla każdej właściwości, procedury, zdarzenia, interfejsu, klasy lub struktury zdefiniowanej jako element członkowski interfejsu. Nazwa elementu członkowskiego.|  
|`End Interface`|Kończy `Interface` definicję.|  
  
## <a name="remarks"></a>Uwagi  
 *Interfejs* definiuje zestaw elementów członkowskich, takich jak właściwości i procedury, które mogą implementować klasy i struktury. Interfejs definiuje tylko sygnatury elementów członkowskich, a nie ich wewnętrzne działania.  
  
 Klasa lub struktura implementuje interfejs, dostarczając kod dla każdego elementu członkowskiego zdefiniowanego przez interfejs. Na koniec, gdy aplikacja tworzy wystąpienie z tej klasy lub struktury, obiekt istnieje i jest uruchamiany w pamięci. Aby uzyskać więcej informacji, zobacz [obiekty i klasy](../../programming-guide/language-features/objects-and-classes/index.md) i [interfejsy](../../programming-guide/language-features/interfaces/index.md).  
  
 Można używać `Interface` tylko na poziomie przestrzeni nazw lub modułu. Oznacza to, że *kontekst deklaracji* dla interfejsu musi być plikiem źródłowym, przestrzenią nazw, klasą, strukturą, modułem lub interfejsem i nie może być procedurą ani blokiem. Aby uzyskać więcej informacji, zobacz [konteksty deklaracji i domyślne poziomy dostępu](declaration-contexts-and-default-access-levels.md).  
  
 Interfejsy domyślnie mają dostęp do [przyjaciela](../modifiers/friend.md) . Możesz dostosować ich poziomy dostępu za pomocą modyfikatorów dostępu. Aby uzyskać więcej informacji, zobacz [poziomy dostępu w Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md).  
  
## <a name="rules"></a>Reguły  
  
- **Zagnieżdżanie interfejsów.** Można zdefiniować jeden interfejs w innym. Interfejs zewnętrzny jest nazywany interfejsem *zawierającym*, a interfejs wewnętrzny jest nazywany *interfejsem zagnieżdżonym*.  
  
- **Deklaracja elementu członkowskiego.** Gdy deklarujesz właściwość lub procedurę jako element członkowski interfejsu, definiujesz tylko *podpis* tej właściwości lub tej procedury. Obejmuje to typ elementu (właściwość lub procedura), jego parametry i typy parametrów oraz typ zwracany. W związku z tym definicja elementu członkowskiego używa tylko jednej linii kodu, a instrukcje kończące, takie jak `End Function` lub, `End Property` nie są prawidłowe w interfejsie.  
  
     W przeciwieństwie do definiowania wyliczenia lub struktury albo zagnieżdżonej klasy lub interfejsu, konieczne jest uwzględnienie ich składowych danych.  
  
- **Modyfikatory elementów członkowskich.** Nie można używać żadnych modyfikatorów dostępu podczas definiowania elementów członkowskich modułu, ani nie można określać modyfikatora [Shared](../modifiers/shared.md) ani any z wyjątkiem [przeciążenia](../modifiers/overloads.md). Można zadeklarować dowolny element członkowski z [cieniami](../modifiers/shadows.md)i użyć [domyślnego](../modifiers/default.md) podczas definiowania właściwości, a także [tylko do odczytu](../modifiers/readonly.md) lub [zapisu](../modifiers/writeonly.md).  
  
- **Strukturze.** Jeśli interfejs używa [instrukcji Inherits](inherits-statement.md), można określić jeden lub więcej interfejsów podstawowych. Można dziedziczyć z dwóch interfejsów, nawet jeśli każda z nich definiuje element członkowski o tej samej nazwie. W takim przypadku kod implementujący musi używać kwalifikacji nazw, aby określić, który element członkowski jest wdrażany.  
  
     Interfejs nie może dziedziczyć z innego interfejsu z bardziej restrykcyjnym poziomem dostępu. Na przykład `Public` interfejs nie może dziedziczyć z `Friend` interfejsu.  
  
     Interfejs nie może dziedziczyć z interfejsu zagnieżdżonego w nim.  
  
- **Realizacji.** Gdy Klasa używa instrukcji [Implements](implements-clause.md) w celu zaimplementowania tego interfejsu, musi zaimplementować każdy element członkowski zdefiniowany w interfejsie. Ponadto każdy podpis w kodzie implementującym musi dokładnie pasować do odpowiadającego mu podpisu zdefiniowanego w tym interfejsie. Jednak nazwa elementu członkowskiego w kodzie implementującym nie musi odpowiadać nazwie elementu członkowskiego zdefiniowanego w interfejsie.  
  
     Gdy klasa implementuje procedurę, nie może wyznaczyć procedury jako `Shared` .  
  
- **Właściwość domyślna.** Interfejs może określać co najwyżej jedną właściwość jako *domyślną właściwość*, do której można się odwoływać bez użycia nazwy właściwości. Należy określić taką właściwość, deklarując ją z modyfikatorem [domyślnym](../modifiers/default.md) .  
  
     Zauważ, że interfejs może definiować właściwość domyślną tylko wtedy, gdy dziedziczy brak.  
  
## <a name="behavior"></a>Zachowanie  
  
- **Poziom dostępu.** Wszyscy członkowie interfejsu mają niejawnie dostęp [publiczny](../modifiers/public.md) . Nie można użyć żadnego modyfikatora dostępu podczas definiowania elementu członkowskiego. Jednak Klasa implementująca interfejs może zadeklarować poziom dostępu dla każdego zaimplementowanego elementu członkowskiego.  
  
     Jeśli przypiszesz wystąpienie klasy do zmiennej, poziom dostępu jego elementów członkowskich może zależeć od tego, czy typ danych zmiennej jest interfejsem podstawowym, czy klasą implementującą. Ilustruje to poniższy przykład.  
  
     [!code-vb[VbVbalrStatements#39](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#39)]  
  
     Jeśli uzyskujesz dostęp do członków klasy za poorednictwem `varAsInterface` , wszyscy mają dostęp publiczny. Jeśli jednak dostęp do członków odbywa się za pomocą programu `varAsClass` , `Sub` procedura `doSomething` ma dostęp prywatny.  
  
- **Scope.** Interfejs jest w zakresie w całej jego przestrzeni nazw, klasy, struktury lub modułu.  
  
     Zakres każdego elementu członkowskiego interfejsu jest całym interfejsem.  
  
- **Okres istnienia.** Interfejs nie ma samego okresu istnienia ani nie należy do jego składowych. Gdy klasa implementuje interfejs, a obiekt jest tworzony jako wystąpienie tej klasy, obiekt ma okres istnienia w aplikacji, w której jest uruchomiony. Aby uzyskać więcej informacji, zobacz "okres istnienia" w [instrukcji klasy](class-statement.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład używa `Interface` instrukcji, aby zdefiniować interfejs o nazwie `thisInterface` , który musi być zaimplementowany przy użyciu `Property` instrukcji i `Function` instrukcji.  
  
 [!code-vb[VbVbalrStatements#40](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#40)]  
  
 Należy zauważyć, `Property` że `Function` instrukcje i nie wprowadzają bloków kończących się na `End Property` i `End Function` w interfejsie. Interfejs definiuje tylko sygnatury swoich elementów członkowskich. Pełne `Property` i `Function` bloki pojawiają się w klasie implementującej `thisInterface` .  
  
## <a name="see-also"></a>Zobacz też

- [Interfejsy](../../programming-guide/language-features/interfaces/index.md)
- [Class, instrukcja](class-statement.md)
- [Module — Instrukcja](module-statement.md)
- [Structure — Instrukcja](structure-statement.md)
- [Property — Instrukcja](property-statement.md)
- [Function, instrukcja](function-statement.md)
- [Sub, instrukcja](sub-statement.md)
- [Typy ogólne w Visual Basic](../../programming-guide/language-features/data-types/generic-types.md)
- [Wariancje w interfejsach](../../programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md)
- [W](../modifiers/in-generic-modifier.md)
- [Określoną](../modifiers/out-generic-modifier.md)
