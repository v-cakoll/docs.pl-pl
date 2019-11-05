---
title: Ograniczenia
description: Dowiedz F# się więcej o ograniczeniach, które mają zastosowanie do parametrów typu ogólnego, aby określić wymagania dla argumentu typu w ogólnym typie lub funkcji.
ms.date: 05/16/2016
ms.openlocfilehash: 70a8bec1ad67d7e814cb7a96b1876bb22399c5e7
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/01/2019
ms.locfileid: "73425018"
---
# <a name="constraints"></a>Ograniczenia

W tym temacie opisano ograniczenia, które można zastosować do parametrów typu ogólnego, aby określić wymagania dla argumentu typu w ogólnym typie lub funkcji.

## <a name="syntax"></a>Składnia

```fsharp
type-parameter-list when constraint1 [ and constraint2]
```

## <a name="remarks"></a>Uwagi

Istnieje kilka różnych ograniczeń, które można zastosować, aby ograniczyć typy, które mogą być używane w typie ogólnym. W poniższej tabeli wymieniono i opisano te ograniczenia.

|Typu|Składnia|Opis|
|----------|------|-----------|
|Ograniczenie typu|*Typ parametru* : *Typ*&gt;|Dostarczony typ musi być równy lub pochodny od określonego typu lub, jeśli typ jest interfejsem, udostępniony typ musi implementować interfejs.|
|Ograniczenie null|*typ — parametr* : null|Dostarczony typ musi obsługiwać literał o wartości null. Obejmuje to wszystkie typy obiektów .NET, ale F# nie listy, krotki, funkcje, klasy, rekordu lub Unii.|
|Jawne ograniczenie elementu członkowskiego|[(]*typ — parametr* [lub... lub *parametru typu*)]: (*sygnatura elementu członkowskiego*)|Co najmniej jeden z podanych argumentów typu musi mieć element członkowski o określonej sygnaturze; nie przeznaczony do wspólnego użycia. Elementy członkowskie muszą być jawnie zdefiniowane w typie lub części niejawnego rozszerzenia typu, aby były prawidłowymi obiektami docelowymi dla jawnego ograniczenia elementu członkowskiego.|
|Ograniczenie konstruktora|*parametr typu* : (New: unit-&gt; "a)|Dostarczony typ musi mieć konstruktora bez parametrów.|
|Ograniczenie typu wartości|: Struktura|Udostępniony typ musi być typem wartości platformy .NET.|
|Ograniczenie typu odwołania|: nie struktura|Podany typ musi być typem referencyjnym platformy .NET.|
|Ograniczenie typu wyliczenia|: Wyliczenie&lt;*Typ podstawowy*&gt;|Dostarczony typ musi być typem wyliczanym, który ma określony typ podstawowy; nie przeznaczony do wspólnego użycia.|
|Delegowanie ograniczenia|: delegowanie&lt;*krotki — typ parametru*, *Typ zwracany*&gt;|Dostarczony typ musi być typem delegata, który ma określone argumenty i wartość zwracaną; nie przeznaczony do wspólnego użycia.|
|Ograniczenie porównania|: porównanie|Udostępniony typ musi obsługiwać porównanie.|
|Ograniczenie równości|: równość|Dostarczony typ musi obsługiwać równość.|
|Niezarządzany warunek ograniczający|: niezarządzane|Podany typ musi być typem niezarządzanym. Typy niezarządzane to pewne typy pierwotne (`sbyte`, `byte`, `char`, `nativeint`, `unativeint`, `float32`, `float`, `int16`, `uint16`, `int32`, `uint32`, `int64`, `uint64`, lub `decimal`), typy wyliczeniowe, `nativeptr<_>`lub nieogólne struktury, których pola są wszystkie typy niezarządzane.|

Musisz dodać ograniczenie, gdy kod musi używać funkcji, która jest dostępna w typie ograniczenia, ale nie dla typów ogólnie. Na przykład, jeśli używasz ograniczenia typu do określenia typu klasy, możesz użyć dowolnej z metod tej klasy w funkcji ogólnej lub w typie.

Określanie ograniczeń jest czasami wymagane w przypadku jawnego pisania parametrów typu, ponieważ bez ograniczenia kompilator nie ma możliwości sprawdzenia, czy używane funkcje będą dostępne dla dowolnego typu, który może być dostarczony w czasie wykonywania dla typu konstruktora.

Najbardziej typowe ograniczenia, które są używane F# w kodzie, to ograniczenia typu, które określają klasy bazowe lub interfejsy. Inne ograniczenia są używane przez F# bibliotekę do implementowania pewnych funkcji, takich jak jawne ograniczenie elementu członkowskiego, który jest używany do implementowania przeciążania operatora dla operatorów arytmetycznych lub są świadczone głównie z F# powodu obsługuje pełny zestaw ograniczeń, które są obsługiwane przez środowisko uruchomieniowe języka wspólnego.

W procesie wnioskowania o typie niektóre ograniczenia są wywnioskowane automatycznie przez kompilator. Na przykład jeśli używasz operatora `+` w funkcji, kompilator wnioskuje jawne ograniczenie elementu członkowskiego dla typów zmiennych, które są używane w wyrażeniu.

Poniższy kod ilustruje niektóre deklaracje ograniczeń:

```fsharp
// Base Type Constraint
type Class1<'T when 'T :> System.Exception> =
class end

// Interface Type Constraint
type Class2<'T when 'T :> System.IComparable> =
class end

// Null constraint
type Class3<'T when 'T : null> =
class end

// Member constraint with instance member
type Class5<'T when 'T : (member Method1 : 'T -> int)> =
class end

// Member constraint with property
type Class6<'T when 'T : (member Property1 : int)> =
class end

// Constructor constraint
type Class7<'T when 'T : (new : unit -> 'T)>() =
member val Field = new 'T()

// Reference type constraint
type Class8<'T when 'T : not struct> =
class end

// Enumeration constraint with underlying value specified
type Class9<'T when 'T : enum<uint32>> =
class end

// 'T must implement IComparable, or be an array type with comparable
// elements, or be System.IntPtr or System.UIntPtr. Also, 'T must not have
// the NoComparison attribute.
type Class10<'T when 'T : comparison> =
class end

// 'T must support equality. This is true for any type that does not
// have the NoEquality attribute.
type Class11<'T when 'T : equality> =
class end

type Class12<'T when 'T : delegate<obj * System.EventArgs, unit>> =
class end

type Class13<'T when 'T : unmanaged> =
class end

// Member constraints with two type parameters
// Most often used with static type parameters in inline functions
let inline add(value1 : ^T when ^T : (static member (+) : ^T * ^T -> ^T), value2: ^T) =
value1 + value2

// ^T and ^U must support operator +
let inline heterogenousAdd(value1 : ^T when (^T or ^U) : (static member (+) : ^T * ^U -> ^T), value2 : ^U) =
value1 + value2

// If there are multiple constraints, use the and keyword to separate them.
type Class14<'T,'U when 'T : equality and 'U : equality> =
class end
```

## <a name="see-also"></a>Zobacz także

- [Typy ogólne](index.md)
- [Ograniczenia](constraints.md)
