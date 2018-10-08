---
title: Ograniczenia (F#)
description: 'Więcej informacji na temat ograniczeń F #, które są stosowane do parametrów typu ogólnego, aby określić wymagania dotyczące argument typu w typie ogólnym lub funkcji.'
ms.date: 05/16/2016
ms.openlocfilehash: 9534db4ffd195022366af8c993658bd94f375f53
ms.sourcegitcommit: 69229651598b427c550223d3c58aba82e47b3f82
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/04/2018
ms.locfileid: "48579873"
---
# <a name="constraints"></a>Ograniczenia

W tym temacie opisano ograniczenia stosowane do ogólnych parametrów, aby określić wymagania dotyczące argument typu w typie ogólnym lub funkcji typu.

## <a name="syntax"></a>Składnia

```fsharp
type-parameter-list when constraint1 [ and constraint2]
```

## <a name="remarks"></a>Uwagi

Istnieje kilka różnych ograniczeń, które można zastosować, aby ograniczyć typy, które mogą być używane w typie podstawowym. Poniższej tabeli wymieniono i opisano te ograniczenia.

|Ograniczenia|Składnia|Opis|
|----------|------|-----------|
|Ograniczenia typu|*Parametr typu* :&gt; *typu*|Podany typ musi być większa lub równa pochodnej z typu określonego lub, jeśli typ jest interfejsem, podany typ musi implementować interfejs.|
|Ograniczenie o wartości null|*Parametr typu* : wartość null|Podany typ musi obsługiwać literałem o wartości null. Obejmuje to wszystkie typy obiektów platformy .NET, ale nie F # listy, spójnej kolekcji, funkcji, klasy, rekord lub typy Unii.|
|Ograniczenie jawnego członka|[(]*parametr typu* [lub... lub *parametr typu*)]: (*sygnatura elementu członkowskiego*)|Co najmniej jeden z podanych argumentów typu musi mieć element członkowski, który ma określony podpis; nie są przeznaczone w typowych zastosowaniach. Elementy członkowskie muszą być albo jawnie zdefiniowane na typ lub część rozszerzenia niejawnego typu jako prawidłowe obiekty docelowe dla jawnego ograniczenia elementu członkowskiego.|
|Ograniczenie konstruktora|*Parametr typu* : (nowe: jednostka -&gt; ")|Podany typ musi mieć domyślnego konstruktora.|
|Ograniczenie typu wartości|: — struktura|Podany typ musi być typem wartości platformy .NET.|
|Ograniczenie typu odwołania|: nie — struktura|Podany typ musi być typem referencyjnym .NET.|
|Ograniczenie typu wyliczenia|: wyliczenia&lt;*typu bazowego*&gt;|Podany typ musi być typu wyliczeniowego, który ma określony typ podstawowy; nie są przeznaczone w typowych zastosowaniach.|
|Ograniczenie delegata|: delegować&lt;*krotki parametr typu*, *zwracanego typu*&gt;|Podany typ musi być typem delegowanym, który ma określone argumenty i zwraca wartości; nie są przeznaczone w typowych zastosowaniach.|
|Ograniczenia porównania|: porównanie|Podany typ musi obsługiwać porównania.|
|Ograniczenie równości|: równości|Podany typ musi obsługiwać równości.|
|Ograniczenie Unmanaged|: niezarządzanych|Podany typ musi być typem niezarządzanym. Typy niezarządzanwe są albo niektóre typy pierwotne (`sbyte`, `byte`, `char`, `nativeint`, `unativeint`, `float32`, `float`, `int16`, `uint16`, `int32`, `uint32`, `int64`, `uint64`, lub `decimal`), Typy wyliczeniowe `nativeptr<_>`, lub struktury nieogólnego, których pola są wszystkie typy niezarządzanych.|
Masz Dodaj ograniczenie, jeśli kod ma można użyć funkcji, która jest ogólnie dostępne na typ ograniczenia, ale nie w typach. Na przykład ograniczenia typu umożliwia określenie typu klasy, można użyć jednej z metod tej klasy, typ lub funkcja ogólna.

Określanie ograniczeń czasami jest wymagana podczas zapisywania parametrów typu w sposób jawny, ponieważ bez ograniczeń, kompilator nie ma możliwości weryfikacji, że funkcje, które są używane będzie dostępna na dowolny typ, który może być dostarczane w czasie wykonywania dla typu parametr.

Najbardziej typowe ograniczenia, używanej w kodzie języka F # to ograniczenia typu, określających klas podstawowych lub interfejsów. Innych ograniczeń albo są używane przez biblioteki języka F # do wykonania niektórych funkcji, takich jak ograniczenie jawny element członkowski, który jest używany do implementowania operatora przeciążania operatorów arytmetycznych lub znajdują się przede wszystkim, ponieważ język F # obsługuje pełne zestaw ograniczeń, który jest obsługiwany przez środowisko uruchomieniowe języka wspólnego.

Podczas procesu wnioskowania typu niektóre ograniczenia są automatycznie wykryta przez kompilator. Na przykład, jeśli używasz `+` operatora w funkcji, kompilator wnioskuje ograniczenie jawnego członka typy zmiennych, które są używane w wyrażeniu.

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

## <a name="see-also"></a>Zobacz także

- [Typy ogólne](index.md)
- [Ograniczenia](constraints.md)
