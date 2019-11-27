---
title: Delegate — Instrukcja
ms.date: 07/20/2015
f1_keywords:
- vb.Delegate
helpviewer_keywords:
- delegate keyword [Visual Basic]
- Delegate statement [Visual Basic]
ms.assetid: f799c518-0817-40cc-ad0b-4da846fdba57
ms.openlocfilehash: 662d2c3c0767adfe406e0a6f1b1e6dccd704e795
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74354073"
---
# <a name="delegate-statement"></a>Delegate — Instrukcja
Używane do deklarowania delegata. Delegat jest typem referencyjnym, który odwołuje się do metody `Shared` typu lub do metody wystąpienia obiektu. Każda procedura ze zgodnymi parametrami i zwracanymi typami może służyć do tworzenia wystąpienia tej klasy delegata. Procedurę można później wywołać za pomocą wystąpienia delegata.  
  
## <a name="syntax"></a>Składnia  
  
```vb  
[ <attrlist> ] [ accessmodifier ] _  
[ Shadows ] Delegate [ Sub | Function ] name [( Of typeparamlist )] [([ parameterlist ])] [ As type ]  
```  
  
## <a name="parts"></a>Części  
  
|Termin|Definicja|  
|---|---|  
|`attrlist`|Opcjonalny. Lista atrybutów, które są stosowane do tego delegata. Wiele atrybutów rozdziela się przecinkami. Należy ująć [listę atrybutów](../../../visual-basic/language-reference/statements/attribute-list.md) w nawiasy ostre ("`<`" i "`>`").|  
|`accessmodifier`|Opcjonalny. Określa kod, który może uzyskać dostęp do obiektu delegowanego. Może to być jeden z następujących modyfikatorów dostępu:<br /><br /> - [publiczne](../../../visual-basic/language-reference/modifiers/public.md). Każdy kod, który może uzyskać dostęp do elementu, który deklaruje delegata, może uzyskać do niego dostęp.<br />-   [chroniony](../../../visual-basic/language-reference/modifiers/protected.md). Tylko kod w klasie delegata lub Klasa pochodna mogą uzyskać do niej dostęp.<br />-   [zaprzyjaźniony](../../../visual-basic/language-reference/modifiers/friend.md). Tylko kod w tym samym zestawie może uzyskać dostęp do obiektu delegowanego.<br />- [prywatny](../../../visual-basic/language-reference/modifiers/private.md). Tylko kod w obrębie elementu, który deklaruje delegata, może uzyskać do niego dostęp.<br /><br /> - [chronionego zaprzyjaźnionego](../../language-reference/modifiers/protected-friend.md) kodu tylko w obrębie klasy delegata, klasy pochodnej lub tego samego zestawu mogą uzyskać dostęp do obiektu delegowanego. <br />- [prywatny tylko chroniony](../../language-reference/modifiers/private-protected.md) kod w klasie delegata lub w klasie pochodnej w tym samym zestawie może uzyskać dostęp do delegata. |  
|`Shadows`|Opcjonalny. Wskazuje, że ten delegat ponownie deklaruje i ukrywa element programowania o identycznej nazwie lub zestaw przeciążonych elementów w klasie bazowej. Można obsłużyć dowolny rodzaj zadeklarowanego elementu z dowolnego innego rodzaju.<br /><br /> Element w tle jest niedostępny z klasy pochodnej, która go zasłania, z wyjątkiem tego, że element shadowing jest niedostępny. Na przykład, jeśli element `Private` zasłania element klasy bazowej, kod, który nie ma uprawnień dostępu do elementu `Private`, zamiast tego uzyskuje dostęp do elementu klasy bazowej.|  
|`Sub`|Opcjonalne, ale muszą być wyświetlane `Sub` lub `Function`. Deklaruje tę procedurę jako delegat `Sub` procedury, która nie zwraca wartości.|  
|`Function`|Opcjonalne, ale muszą być wyświetlane `Sub` lub `Function`. Deklaruje tę procedurę jako delegat `Function` procedury, która zwraca wartość.|  
|`name`|Wymagany. Nazwa typu delegata; obowiązują standardowe konwencje nazewnictwa zmiennych.|  
|`typeparamlist`|Opcjonalny. Lista parametrów typu dla tego delegata. Wiele parametrów typu są rozdzielone przecinkami. Opcjonalnie każdy parametr typu może być zadeklarowany jako VARIANT przy użyciu `In` i `Out` Modyfikatory ogólne. Należy ująć [listę typów](../../../visual-basic/language-reference/statements/type-list.md) w nawiasy i wprowadzić ją za pomocą słowa kluczowego `Of`.|  
|`parameterlist`|Opcjonalny. Lista parametrów, które są przesyłane do procedury po jej wywołaniu. Należy ująć [listę parametrów](../../../visual-basic/language-reference/statements/parameter-list.md) w nawiasach.|  
|`type`|Wymagane, jeśli określisz procedurę `Function`. Typ danych wartości zwracanej.|  
  
## <a name="remarks"></a>Uwagi  
 Instrukcja `Delegate` definiuje parametry i zwracane typy klasy delegatów. Każda procedura z pasującymi parametrami i zwracanymi typami może służyć do tworzenia wystąpienia tej klasy delegata. Procedurę można później wywołać za pomocą wystąpienia delegata, wywołując metodę `Invoke` delegata.  
  
 Delegaty mogą być zadeklarowane na poziomie przestrzeni nazw, modułu, klasy lub struktury, ale nie w ramach procedury.  
  
 Każda Klasa delegatów definiuje konstruktora, który przekazał specyfikację metody obiektu. Argument konstruktora delegata musi być odwołaniem do metody lub wyrażeniem lambda.  
  
 Aby określić odwołanie do metody, należy użyć następującej składni:  
  
 `AddressOf` [`expression`.]`methodname`  
  
 Typ czasu kompilacji `expression` musi być nazwą klasy lub interfejsem, który zawiera metodę o określonej nazwie, której sygnatura pasuje do sygnatury klasy delegata. `methodname` może być metodą udostępnioną lub metodą wystąpienia. `methodname` nie jest opcjonalna, nawet jeśli utworzysz delegata dla metody domyślnej klasy.  
  
 Aby określić wyrażenie lambda, należy użyć następującej składni:  
  
 `Function` ([`parm` jako `type``parm2` jako `type2`,...]) `expression`  
  
 Sygnatura funkcji musi być zgodna z typem delegata. Aby uzyskać więcej informacji na temat wyrażeń lambda, zobacz [lambda Expressions](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).  
  
 Aby uzyskać więcej informacji na temat delegatów, zobacz [delegats](../../../visual-basic/programming-guide/language-features/delegates/index.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład używa instrukcji `Delegate`, aby zadeklarować delegata na potrzeby obsługi dwóch liczb i zwracać liczbę. Metoda `DelegateTest` przyjmuje wystąpienie delegata tego typu i używa go do obsługi par liczb.  
  
 [!code-vb[VbVbalrDelegates#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDelegates/VB/Class1.vb#14)]  
  
## <a name="see-also"></a>Zobacz także

- [AddressOf, operator](../../../visual-basic/language-reference/operators/addressof-operator.md)
- [Z](../../../visual-basic/language-reference/statements/of-clause.md)
- [Delegaci](../../../visual-basic/programming-guide/language-features/delegates/index.md)
- [Instrukcje: używanie klasy ogólnej](../../../visual-basic/programming-guide/language-features/data-types/how-to-use-a-generic-class.md)
- [Typy ogólne w Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [Kowariancja i kontrawariancja](../../programming-guide/concepts/covariance-contravariance/index.md)
- [Podczas](../../../visual-basic/language-reference/modifiers/in-generic-modifier.md)
- [Określoną](../../../visual-basic/language-reference/modifiers/out-generic-modifier.md)
