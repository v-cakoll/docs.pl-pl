---
title: Ograniczenia (F#)
description: 'Więcej informacji na temat języka F # ograniczenia dotyczące parametrów typu ogólnego, aby określić wymagania dotyczące argument typu w typie ogólnym lub funkcji.'
ms.date: 05/16/2016
ms.openlocfilehash: f0722cafe27a4e2c38dfbf091973edb136cf5228
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33562313"
---
# <a name="constraints"></a>Ograniczenia

W tym temacie opisano ograniczenia, które można zastosować do ogólnego typu w celu określenia wymagań dotyczących argument typu w typie ogólnym lub funkcji.


## <a name="syntax"></a>Składnia

```fsharp
type-parameter-list when constraint1 [ and constraint2]
```

## <a name="remarks"></a>Uwagi
Istnieje kilka różnych ograniczeń, które można zastosować do ograniczania typów, których można użyć w typie ogólnym. Poniższa tabela zawiera listę oraz opis tych warunków ograniczających.

|Ograniczenia|Składnia|Opis|
|----------|------|-----------|
|Ograniczenie typu|*Parametr typu* :&gt; *typu*|Podany typ musi być równa lub pochodnych z typem określonym lub, jeśli typ jest interfejsem, podany typ musi implementować interfejs.|
|Ograniczenie wartości null|*Parametr typu* : wartość null|Podany typ musi obsługiwać literał wartości null. Dotyczy to również wszystkich typów obiektów platformy .NET, ale nie F # listy, spójnej kolekcji, funkcji, klasy, rekordu lub Unii.|
|Ograniczenie jawnego członka|[()]*parametr typu* [lub lub *parametr typu*)]: (* sygnaturę elementu członkowskiego *)|Co najmniej jedna z podanych argumentów typu musi mieć element członkowski, który ma określony podpis; nie jest przeznaczone do użycia. Elementy członkowskie muszą być albo jawnie zdefiniowane na typ lub część rozszerzenia typu niejawnego jako prawidłowe elementy docelowe dla jawnego ograniczenia elementu członkowskiego.|
|Ograniczenie konstruktora|*Parametr typu* : (new: jednostka -&gt; ")|Podany typ musi mieć konstruktora domyślnego.|
|Ograniczenie typu wartości|: struktury|Podany typ musi być typem wartości .NET.|
|Ograniczenie typu odwołania|: nie — struktura|Podany typ musi być typem referencyjnym .NET.|
|Ograniczenie typu wyliczenia|: wyliczenia&lt;*typu podstawowego*&gt;|Podany typ musi być Typ wyliczany określonego typu źródłowego; nie jest przeznaczone do użycia.|
|Ograniczenie delegata|: delegować&lt;*krotki parametru typu*, *zwracanego typu*&gt;|Podany typ musi być typem delegata, który ma określone argumenty i zwracać wartość; nie jest przeznaczone do użycia.|
|Ograniczenia porównania|: porównania|Podany typ musi obsługiwać porównania.|
|Ograniczenie równości|: równości|Podany typ musi obsługiwać równości.|
|Ograniczenie niezarządzane|: niezarządzane|Podany typ musi być typem niezarządzanym. Typy niezarządzanwe są albo niektórych typów pierwotnych (`sbyte`, `byte`, `char`, `nativeint`, `unativeint`, `float32`, `float`, `int16`, `uint16`, `int32`, `uint32`, `int64`, `uint64`, lub `decimal`), Typy wyliczeniowe `nativeptr&lt;_&gt;`, lub struktury nieogólnego, których pola są wszystkie typy niezarządzane.|
Należy dodać ograniczenie po kodzie można użyć funkcji, która jest dostępna na typ ograniczenia, ale nie w typach ogólnie. Na przykład jeśli ograniczenia typu należy użyć do określenia typu klasy, używając jednej z metod klas w ogólnym funkcja lub typ.

Określenie ograniczenia jest czasami wymagane podczas zapisywania parametrów typu jawnie, ponieważ bez ograniczenia, kompilator nie ma możliwości sprawdzenia, czy funkcje, które są używane będzie dostępny dla dowolnego typu, który może być dostarczony w czasie wykonywania dla typu parametr.

Ograniczenia najczęściej używanych w kodzie języka F # są ograniczenia typu, których określić klasy podstawowej lub do interfejsów. Innych ograniczeń albo są używane przez biblioteki języka F # do wykonania niektórych funkcji, takich jak ograniczenia jawnego członka, które jest używane do implementowania przeładowanie operatorów arytmetycznych operatora lub znajdują się głównie, ponieważ język F # obsługuje pełną zestaw warunków ograniczających obsługiwaną przez środowisko uruchomieniowe języka wspólnego.

W trakcie wnioskowania typu niektóre ograniczenia są automatycznie wykryta przez kompilator. Na przykład, jeśli używasz `+` operatora w funkcji, kompilator wnioskuje ograniczenie jawnego członka typy zmiennych, które są używane w wyrażeniu.

Poniższy kod ilustruje deklaracje pewne ograniczenia.

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

// Member constraint with static member
type Class4<'T when 'T : (static member staticMethod1 : unit -> 'T) > =
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

## <a name="see-also"></a>Zobacz też
[Typy ogólne](index.md)

[Ograniczenia](constraints.md)
