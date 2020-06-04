---
title: Delegate — Instrukcja
ms.date: 07/20/2015
f1_keywords:
- vb.Delegate
helpviewer_keywords:
- delegate keyword [Visual Basic]
- Delegate statement [Visual Basic]
ms.assetid: f799c518-0817-40cc-ad0b-4da846fdba57
ms.openlocfilehash: 8dec28620b0409f05007b2c0b1c1fd4494c2d7c8
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404761"
---
# <a name="delegate-statement"></a>Delegate — Instrukcja
Używane do deklarowania delegata. Delegat jest typem referencyjnym, który odwołuje się do `Shared` metody typu lub do metody wystąpienia obiektu. Każda procedura ze zgodnymi parametrami i zwracanymi typami może służyć do tworzenia wystąpienia tej klasy delegata. Procedurę można później wywołać za pomocą wystąpienia delegata.  
  
## <a name="syntax"></a>Składnia  
  
```vb  
[ <attrlist> ] [ accessmodifier ] _  
[ Shadows ] Delegate [ Sub | Function ] name [( Of typeparamlist )] [([ parameterlist ])] [ As type ]  
```  
  
## <a name="parts"></a>Części  
  
|Termin|Definicja|  
|---|---|  
|`attrlist`|Opcjonalny. Lista atrybutów, które są stosowane do tego delegata. Wiele atrybutów jest oddzielonych przecinkami. Należy ująć [listę atrybutów](attribute-list.md) w nawiasy kątowe (" `<` " i " `>` ").|  
|`accessmodifier`|Opcjonalny. Określa kod, który może uzyskać dostęp do obiektu delegowanego. Może być jedną z następujących czynności:<br /><br /> - [Publiczne](../modifiers/public.md). Każdy kod, który może uzyskać dostęp do elementu, który deklaruje delegata, może uzyskać do niego dostęp.<br />-   [Ochrona](../modifiers/protected.md). Tylko kod w klasie delegata lub Klasa pochodna mogą uzyskać do niej dostęp.<br />-   [Zaprzyjaźniony](../modifiers/friend.md). Tylko kod w tym samym zestawie może uzyskać dostęp do obiektu delegowanego.<br />- [Prywatny](../modifiers/private.md). Tylko kod w obrębie elementu, który deklaruje delegata, może uzyskać do niego dostęp.<br /><br /> - [Chroniony znajomy](../modifiers/protected-friend.md) Tylko kod w obrębie klasy delegata, klasy pochodnej lub tego samego zestawu mogą uzyskać dostęp do obiektu delegowanego. <br />- [Prywatne chronione](../modifiers/private-protected.md) Tylko kod znajdujący się w klasie delegata lub w klasie pochodnej w tym samym zestawie mogą uzyskać dostęp do obiektu delegowanego. |  
|`Shadows`|Opcjonalny. Wskazuje, że ten delegat ponownie deklaruje i ukrywa element programowania o identycznej nazwie lub zestaw przeciążonych elementów w klasie bazowej. Można obsłużyć dowolny rodzaj zadeklarowanego elementu z dowolnego innego rodzaju.<br /><br /> Element w tle jest niedostępny z klasy pochodnej, która go zasłania, z wyjątkiem tego, że element shadowing jest niedostępny. Na przykład, jeśli `Private` element zasłania element klasy bazowej, kod, który nie ma uprawnień dostępu do `Private` elementu uzyskuje dostęp do elementu klasy bazowej.|  
|`Sub`|Opcjonalne, ale `Sub` lub `Function` muszą pojawić się. Deklaruje tę procedurę jako procedurę delegata `Sub` , która nie zwraca wartości.|  
|`Function`|Opcjonalne, ale `Sub` lub `Function` muszą pojawić się. Deklaruje tę procedurę jako procedurę delegata `Function` zwracającą wartość.|  
|`name`|Wymagany. Nazwa typu delegata; obowiązują standardowe konwencje nazewnictwa zmiennych.|  
|`typeparamlist`|Opcjonalny. Lista parametrów typu dla tego delegata. Wiele parametrów typu są rozdzielone przecinkami. Opcjonalnie każdy parametr typu może być zadeklarowany jako VARIANT przy użyciu `In` i `Out` Modyfikatory ogólne. Należy ująć [listę typów](type-list.md) w nawiasy i wprowadzić ją ze `Of` słowem kluczowym.|  
|`parameterlist`|Opcjonalny. Lista parametrów, które są przesyłane do procedury po jej wywołaniu. Należy ująć [listę parametrów](parameter-list.md) w nawiasach.|  
|`type`|Wymagane, jeśli określisz `Function` procedurę. Typ danych wartości zwracanej.|  
  
## <a name="remarks"></a>Uwagi  
 `Delegate`Instrukcja definiuje parametry i zwracane typy klasy delegata. Każda procedura z pasującymi parametrami i zwracanymi typami może służyć do tworzenia wystąpienia tej klasy delegata. Procedurę można później wywołać za pomocą wystąpienia delegata, wywołując metodę delegata `Invoke` .  
  
 Delegaty mogą być zadeklarowane na poziomie przestrzeni nazw, modułu, klasy lub struktury, ale nie w ramach procedury.  
  
 Każda Klasa delegatów definiuje konstruktora, który przekazał specyfikację metody obiektu. Argument konstruktora delegata musi być odwołaniem do metody lub wyrażeniem lambda.  
  
 Aby określić odwołanie do metody, należy użyć następującej składni:  
  
 `AddressOf` [`expression`.]`methodname`  
  
 Typ czasu kompilacji `expression` musi być nazwą klasy lub interfejsem zawierającym metodę o określonej nazwie, której sygnatura pasuje do sygnatury klasy delegata. `methodname`Może to być Metoda wspólna lub metoda wystąpienia. `methodname`Nie jest opcjonalna, nawet jeśli utworzysz delegata dla metody domyślnej klasy.  
  
 Aby określić wyrażenie lambda, należy użyć następującej składni:  
  
 `Function`([ `parm` AS `type` , `parm2` AS, `type2` ...])`expression`  
  
 Sygnatura funkcji musi być zgodna z typem delegata. Aby uzyskać więcej informacji na temat wyrażeń lambda, zobacz [lambda Expressions](../../programming-guide/language-features/procedures/lambda-expressions.md).  
  
 Aby uzyskać więcej informacji na temat delegatów, zobacz [delegats](../../programming-guide/language-features/delegates/index.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład używa instrukcji, `Delegate` Aby zadeklarować delegata na potrzeby obsługi dwóch liczb i zwracać liczbę. `DelegateTest`Metoda przyjmuje wystąpienie delegata tego typu i używa go do obsługi par liczb.  
  
 [!code-vb[VbVbalrDelegates#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDelegates/VB/Class1.vb#14)]  
  
## <a name="see-also"></a>Zobacz też

- [AddressOf, operator](../operators/addressof-operator.md)
- [Z](of-clause.md)
- [Delegaci](../../programming-guide/language-features/delegates/index.md)
- [Instrukcje: Używanie klasy ogólnej](../../programming-guide/language-features/data-types/how-to-use-a-generic-class.md)
- [Typy ogólne w Visual Basic](../../programming-guide/language-features/data-types/generic-types.md)
- [Kowariancja i kontrawariancja](../../programming-guide/concepts/covariance-contravariance/index.md)
- [W](../modifiers/in-generic-modifier.md)
- [Określoną](../modifiers/out-generic-modifier.md)
