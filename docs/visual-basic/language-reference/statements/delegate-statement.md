---
title: Delegate — instrukcja (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Delegate
helpviewer_keywords:
- delegate keyword [Visual Basic]
- Delegate statement [Visual Basic]
ms.assetid: f799c518-0817-40cc-ad0b-4da846fdba57
ms.openlocfilehash: 4718c0a6e332d644a7f54c79246df95f841058d0
ms.sourcegitcommit: 8c28ab17c26bf08abbd004cc37651985c68841b8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2018
ms.locfileid: "48845394"
---
# <a name="delegate-statement"></a>Delegate — Instrukcja
Używane do deklarowania delegata. Delegat jest typem referencyjnym, który odwołuje się do `Shared` metody typu lub metod wystąpień obiektu. Każda procedura ze zgodnymi typy parametrów i zwrotu może służyć do utworzenia wystąpienia tej klasy delegatu. Procedurę można następnie później wywołać za pośrednictwem wystąpienia delegata.  
  
## <a name="syntax"></a>Składnia  
  
```  
[ <attrlist> ] [ accessmodifier ] _  
[ Shadows ] Delegate [ Sub | Function ] name [( Of typeparamlist )] [([ parameterlist ])] [ As type ]  
```  
  
## <a name="parts"></a>Części  
  
|Termin|Definicja|  
|---|---|  
|`attrlist`|Opcjonalna. Lista atrybutów, które są stosowane do tego delegata. Wiele atrybutów rozdziela się przecinkami. Należy ująć [listę atrybutów](../../../visual-basic/language-reference/statements/attribute-list.md) w nawiasy ("`<`"i"`>`").|  
|`accessmodifier`|Opcjonalna. Określa, jaki kod może uzyskać dostęp do obiektu delegowanego. Może to być jeden z następujących elementów:<br /><br /> - [Publiczne](../../../visual-basic/language-reference/modifiers/public.md). Wszelki kod, który mogą uzyskiwać dostęp do elementu, który deklaruje delegata do niego dostęp.<br />-   [Chronione](../../../visual-basic/language-reference/modifiers/protected.md). Tylko kod w obrębie klasy delegatu lub klasy pochodnej do niego dostęp.<br />-   [Friend](../../../visual-basic/language-reference/modifiers/friend.md). Tylko kodu w ramach tego samego zestawu można uzyskać dostęp do delegata.<br />- [Prywatne](../../../visual-basic/language-reference/modifiers/private.md). Tylko kod wewnątrz elementu, który deklaruje delegata do niego dostęp.<br /><br /> - [Protected Friend](../../language-reference/modifiers/protected-friend.md) tylko do kodu w ramach klasy delegata, klasę pochodną lub tego samego zestawu mogą uzyskiwać dostęp do obiektu delegowanego. <br />- [Prywatny chroniony](../../language-reference/modifiers/private-protected.md) tylko kod wewnątrz klasy delegatu lub w klasie pochodnej z tego samego zestawu mogą uzyskiwać dostęp do obiektu delegowanego. |  
|`Shadows`|Opcjonalna. Wskazuje, że ten delegat programistyczny ponownie deklaruje i ukrywa o identycznej nazwie elementu programistycznego lub zestaw przeciążonych elementów w klasie bazowej. Można w tle dowolnego typu element zadeklarowany za pomocą dowolnego typu.<br /><br /> Zasłonięte element jest niedostępny z w klasie pochodnej, która zasłania, z wyjątkiem sytuacji, z którym przesłaniania elementu jest niedostępny. Na przykład jeśli `Private` element zasłania elementu klasy podstawowej, kod, który nie ma uprawnień dostępu do `Private` element uzyskuje dostęp do elementu klasy podstawowej zamiast tego.|  
|`Sub`|Opcjonalne, ale albo `Sub` lub `Function` musi znajdować się. Deklaruje tej procedury jako pełnomocnik `Sub` procedury, która nie zwraca wartości.|  
|`Function`|Opcjonalne, ale albo `Sub` lub `Function` musi znajdować się. Deklaruje tej procedury jako pełnomocnik `Function` procedury, która nie zwraca wartości.|  
|`name`|Wymagane. Nazwa typu delegata; następuje standardową konwencją nazw zmiennych.|  
|`typeparamlist`|Opcjonalna. Lista parametrów typu dla tego delegata. Wiele parametrów typu są oddzielone przecinkami. Opcjonalnie, każdy parametr typu mogą być deklarowane wariant przy użyciu `In` i `Out` ogólnego modyfikatorów. Należy ująć [lista typów](../../../visual-basic/language-reference/statements/type-list.md) w nawiasach i wprowadzić ją za pomocą `Of` — słowo kluczowe.|  
|`parameterlist`|Opcjonalna. Lista parametrów, które są przekazywane do procedury, gdy jest wywoływana. Należy ująć [listy parametrów](../../../visual-basic/language-reference/statements/parameter-list.md) w nawiasach.|  
|`type`|Wymagane, jeśli określisz `Function` procedury. Typ danych wartości zwracanej.|  
  
## <a name="remarks"></a>Uwagi  
 `Delegate` Instrukcja definiuje typy parametrów i zwrotu klasy delegata. Każda procedura ze zgodnymi parametry i zwracane typy może służyć do utworzenia wystąpienia tej klasy delegatu. Procedurę można następnie później wywołać za pośrednictwem wystąpienia delegata przez wywołanie metody delegata `Invoke` metody.  
  
 Delegaty mogą być deklarowane w przestrzeni nazw, modułu, klasy lub struktury poziomu, ale nie w obrębie procedury.  
  
 Każda klasa obiektu delegowanego definiuje konstruktora, który jest przekazywany do specyfikacji metody obiektu. Argument do konstruktora obiektu delegowanego musi być odwołanie do metody lub wyrażenia lambda.  
  
 Aby określić odwołanie do metody, użyj następującej składni:  
  
 `AddressOf` [`expression`.]`methodname`  
  
 Typ kompilacji `expression` musi być nazwą klasy lub interfejsu, który zawiera metodę o określonej nazwie, którego podpis pasuje do podpisu klasa obiektu delegowanego. `methodname` Może być udostępnionej metody lub metodą wystąpienia. `methodname` Nie jest opcjonalny, nawet wtedy, gdy utworzenia delegata dla metody domyślnej klasy.  
  
 Aby określić wyrażenie lambda, użyj następującej składni:  
  
 `Function` ([`parm` Jako `type`, `parm2` jako `type2`,...]) `expression`  
  
 Podpis funkcji musi być zgodny z typem delegata. Aby uzyskać więcej informacji na temat wyrażeń lambda, zobacz [wyrażeń Lambda](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).  
  
 Aby uzyskać więcej informacji na temat obiektów delegowanych, zobacz [delegatów](../../../visual-basic/programming-guide/language-features/delegates/index.md).  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto `Delegate` instrukcję, aby zadeklarować delegata na potrzeby świadczenia na dwie liczby i zwraca liczbę. `DelegateTest` Metoda przyjmuje wystąpienie delegata tego typu i używa go do wykonywania operacji pary numerów.  
  
 [!code-vb[VbVbalrDelegates#14](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/delegate-statement_1.vb)]  
  
## <a name="see-also"></a>Zobacz też  
 [AddressOf, operator](../../../visual-basic/language-reference/operators/addressof-operator.md)  
 [z](../../../visual-basic/language-reference/statements/of-clause.md)  
 [Delegaci](../../../visual-basic/programming-guide/language-features/delegates/index.md)  
 [Instrukcje: używanie klasy ogólnej](../../../visual-basic/programming-guide/language-features/data-types/how-to-use-a-generic-class.md)  
 [Typy ogólne w Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)  
 [Kowariancja i kontrawariancja](../../programming-guide/concepts/covariance-contravariance/index.md)  
 [W](../../../visual-basic/language-reference/modifiers/in-generic-modifier.md)  
 [limit](../../../visual-basic/language-reference/modifiers/out-generic-modifier.md)
