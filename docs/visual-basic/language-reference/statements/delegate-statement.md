---
title: Delegate — Instrukcja
ms.date: 07/20/2015
f1_keywords:
- vb.Delegate
helpviewer_keywords:
- delegate keyword [Visual Basic]
- Delegate statement [Visual Basic]
ms.assetid: f799c518-0817-40cc-ad0b-4da846fdba57
ms.openlocfilehash: fb9d8b2c2647ba8fd3b7cee4781f1574b6679b0f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="delegate-statement"></a>Delegate — Instrukcja
Można zadeklarować obiektu delegowanego. Delegat jest typem referencyjnym, który odwołuje się do `Shared` metody typu lub metod wystąpień obiektu. Postępowanie z pasujących typów parametru i wróć może służyć do tworzenia wystąpienia tej klasy delegatu. Następnie procedurę później można wywołać za pomocą wystąpienia obiektu delegowanego.  
  
## <a name="syntax"></a>Składnia  
  
```  
[ <attrlist> ] [ accessmodifier ] _  
[ Shadows ] Delegate [ Sub | Function ] name [( Of typeparamlist )] [([ parameterlist ])] [ As type ]  
```  
  
## <a name="parts"></a>Części  
  
|Termin|Definicja|  
|---|---|  
|`attrlist`|Opcjonalna. Lista atrybutów, które są stosowane do tego obiektu delegowanego. Wiele atrybutów są rozdzielane przecinkami. Musisz ją ująć [lista atrybutów](../../../visual-basic/language-reference/statements/attribute-list.md) w nawiasy ("`<`"i"`>`").|  
|`accessmodifier`|Opcjonalna. Określa, jaki kod mogą uzyskiwać dostęp do obiektu delegowanego. Może to być jeden z następujących elementów:<br /><br /> -   [Publiczny](../../../visual-basic/language-reference/modifiers/public.md). Wszelki kod, który można uzyskać dostępu do elementu, który deklaruje delegata do niego dostęp.<br />-   [Chronione](../../../visual-basic/language-reference/modifiers/protected.md). Tylko kod w klasie obiektów delegowanych lub klasy pochodnej do niego dostęp.<br />-   [Friend](../../../visual-basic/language-reference/modifiers/friend.md). Tylko kod w tym samym zestawie mogą uzyskiwać dostęp do obiektu delegowanego.<br />-   [Prywatne](../../../visual-basic/language-reference/modifiers/private.md). Tylko kodu w elemencie, który deklaruje delegata do niego dostęp.<br /><br /> Można określić `Protected Friend` Aby włączyć dostęp z kodu w klasie obiektów delegowanych, klasa pochodna lub tego samego zestawu.|  
|`Shadows`|Opcjonalna. Wskazuje, że ten delegat programistyczny ponownie deklaruje i ukrywa element programowania o identycznej nazwie lub zbiór elementów przeciążona w klasie podstawowej. Można obserwować dowolny rodzaj elementu zadeklarowany z innego typu.<br /><br /> Element zasłonięty z są niedostępne w klasie pochodnej, któremu, z wyjątkiem z którym przesłaniania element jest niedostępny. Na przykład jeśli `Private` element zasłania element klasy podstawowej, kod, który nie ma uprawnień dostępu do `Private` element uzyskuje dostęp do elementu klasy podstawowej zamiast tego.|  
|`Sub`|Opcjonalne, ale albo `Sub` lub `Function` musi występować. Deklaruje tej procedury jako pełnomocnik `Sub` procedury, która nie zwraca wartości.|  
|`Function`|Opcjonalne, ale albo `Sub` lub `Function` musi występować. Deklaruje tej procedury jako pełnomocnik `Function` procedury, która nie zwraca wartości.|  
|`name`|Wymagana. Nazwa typu delegata; następuje standardowej konwencji nazewnictwa zmiennej.|  
|`typeparamlist`|Opcjonalna. Lista parametrów typu dla tego obiektu delegowanego. Wiele parametrów typu są oddzielone przecinkami. Opcjonalnie, każdy parametr typu mogą być deklarowane variant przy użyciu `In` i `Out` ogólnego modyfikatorów. Musisz ją ująć [lista typów](../../../visual-basic/language-reference/statements/type-list.md) w nawiasach i wprowadzić go przy użyciu `Of` — słowo kluczowe.|  
|`parameterlist`|Opcjonalna. Lista parametrów, które są przekazywane do procedury, gdy jest wywoływana. Musisz ją ująć [listy parametrów](../../../visual-basic/language-reference/statements/parameter-list.md) w nawiasach.|  
|`type`|Wymagane, jeśli można określić `Function` procedury. Typ danych wartości zwracanej.|  
  
## <a name="remarks"></a>Uwagi  
 `Delegate` Instrukcji definiuje parametr i zwracane typy klasa delegata. Postępowanie z pasującymi parametrów i zwracanych typów może służyć do tworzenia wystąpienia tej klasy delegatu. Procedura może następnie później można wywołać za pomocą wystąpienia delegata przez wywołanie metody delegata `Invoke` metody.  
  
 Delegaty mogą być deklarowane w przestrzeni nazw, modułu, klasy lub struktury poziomu, ale nie w procedurze.  
  
 Każda klasa delegata definiuje konstruktora, który jest przekazywany specyfikację metody obiektu. Argument do konstruktora delegata musi być odwołaniem do metody lub wyrażenia lambda.  
  
 Aby określić odwołań do metody, należy użyć następującej składni:  
  
 `AddressOf` [`expression`.]`methodname`  
  
 Typ kompilacji `expression` musi być nazwą klasy lub interfejsu, który zawiera metodę o określonej nazwie, w których Podpis pasuje do podpisu klasie obiektów delegowanych. `methodname` Może być udostępnionej metody lub metodą wystąpienia. `methodname` Nie jest opcjonalny, nawet w przypadku utworzenia delegata dla metody domyślnej klasy.  
  
 Aby określić wyrażenie lambda, użyj następującej składni:  
  
 `Function` ([`parm` Jako `type`, `parm2` jako `type2`,...]) `expression`  
  
 Podpis funkcji musi być zgodny z typem obiektu delegowanego. Aby uzyskać więcej informacji na temat wyrażeń lambda, zobacz [wyrażenia Lambda](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).  
  
 Aby uzyskać więcej informacji na temat delegatów, zobacz [delegatów](../../../visual-basic/programming-guide/language-features/delegates/index.md).  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto `Delegate` instrukcji, aby zadeklarować delegata działających na dwie liczby i zwraca liczbę. `DelegateTest` Metoda pobiera wystąpienie tego typu delegata i używa go do działania na pary numerów.  
  
 [!code-vb[VbVbalrDelegates#14](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/delegate-statement_1.vb)]  
  
## <a name="see-also"></a>Zobacz też  
 [AddressOf, operator](../../../visual-basic/language-reference/operators/addressof-operator.md)  
 [z](../../../visual-basic/language-reference/statements/of-clause.md)  
 [Delegaci](../../../visual-basic/programming-guide/language-features/delegates/index.md)  
 [Instrukcje: używanie klasy ogólnej](../../../visual-basic/programming-guide/language-features/data-types/how-to-use-a-generic-class.md)  
 [Typy ogólne w Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)  
 [Kowariancja i kontrawariancja](../../programming-guide/concepts/covariance-contravariance/index.md)  
 [In](../../../visual-basic/language-reference/modifiers/in-generic-modifier.md)  
 [limit](../../../visual-basic/language-reference/modifiers/out-generic-modifier.md)
