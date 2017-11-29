---
title: Ograniczenia (F#)
description: "Więcej informacji na temat języka F # ograniczenia dotyczące parametrów typu ogólnego, aby określić wymagania dotyczące argument typu w typie ogólnym lub funkcji."
keywords: "Visual f #, f #, funkcjonalności programowania"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 2f232a3a-9486-48fb-9759-f23404ed4b52
ms.openlocfilehash: 91854fd2f692688e0f1c27aba1422eff64156048
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="constraints"></a><span data-ttu-id="7bcb5-104">Ograniczenia</span><span class="sxs-lookup"><span data-stu-id="7bcb5-104">Constraints</span></span>

<span data-ttu-id="7bcb5-105">W tym temacie opisano ograniczenia, które można zastosować do ogólnego typu w celu określenia wymagań dotyczących argument typu w typie ogólnym lub funkcji.</span><span class="sxs-lookup"><span data-stu-id="7bcb5-105">This topic describes constraints that you can apply to generic type parameters to specify the requirements for a type argument in a generic type or function.</span></span>


## <a name="syntax"></a><span data-ttu-id="7bcb5-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="7bcb5-106">Syntax</span></span>

```fsharp
type-parameter-list when constraint1 [ and constraint2]
```

## <a name="remarks"></a><span data-ttu-id="7bcb5-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="7bcb5-107">Remarks</span></span>
<span data-ttu-id="7bcb5-108">Istnieje kilka różnych ograniczeń, które można zastosować do ograniczania typów, których można użyć w typie ogólnym.</span><span class="sxs-lookup"><span data-stu-id="7bcb5-108">There are several different constraints you can apply to limit the types that can be used in a generic type.</span></span> <span data-ttu-id="7bcb5-109">Poniższa tabela zawiera listę oraz opis tych warunków ograniczających.</span><span class="sxs-lookup"><span data-stu-id="7bcb5-109">The following table lists and describes these constraints.</span></span>

|<span data-ttu-id="7bcb5-110">Ograniczenia</span><span class="sxs-lookup"><span data-stu-id="7bcb5-110">Constraint</span></span>|<span data-ttu-id="7bcb5-111">Składnia</span><span class="sxs-lookup"><span data-stu-id="7bcb5-111">Syntax</span></span>|<span data-ttu-id="7bcb5-112">Opis</span><span class="sxs-lookup"><span data-stu-id="7bcb5-112">Description</span></span>|
|----------|------|-----------|
|<span data-ttu-id="7bcb5-113">Ograniczenie typu</span><span class="sxs-lookup"><span data-stu-id="7bcb5-113">Type Constraint</span></span>|<span data-ttu-id="7bcb5-114">*Parametr typu* :&gt; *typu*</span><span class="sxs-lookup"><span data-stu-id="7bcb5-114">*type-parameter* :&gt; *type*</span></span>|<span data-ttu-id="7bcb5-115">Podany typ musi być równa lub pochodnych z typem określonym lub, jeśli typ jest interfejsem, podany typ musi implementować interfejs.</span><span class="sxs-lookup"><span data-stu-id="7bcb5-115">The provided type must be equal to or derived from the type specified, or, if the type is an interface, the provided type must implement the interface.</span></span>|
|<span data-ttu-id="7bcb5-116">Ograniczenie wartości null</span><span class="sxs-lookup"><span data-stu-id="7bcb5-116">Null Constraint</span></span>|<span data-ttu-id="7bcb5-117">*Parametr typu* : wartość null</span><span class="sxs-lookup"><span data-stu-id="7bcb5-117">*type-parameter* : null</span></span>|<span data-ttu-id="7bcb5-118">Podany typ musi obsługiwać literał wartości null.</span><span class="sxs-lookup"><span data-stu-id="7bcb5-118">The provided type must support the null literal.</span></span> <span data-ttu-id="7bcb5-119">Dotyczy to również wszystkich typów obiektów platformy .NET, ale nie F # listy, spójnej kolekcji, funkcji, klasy, rekordu lub Unii.</span><span class="sxs-lookup"><span data-stu-id="7bcb5-119">This includes all .NET object types but not F# list, tuple, function, class, record, or union types.</span></span>|
|<span data-ttu-id="7bcb5-120">Ograniczenie jawnego członka</span><span class="sxs-lookup"><span data-stu-id="7bcb5-120">Explicit Member Constraint</span></span>|<span data-ttu-id="7bcb5-121">[()]*parametr typu* [lub lub *parametr typu*)]: (* sygnaturę elementu członkowskiego *)</span><span class="sxs-lookup"><span data-stu-id="7bcb5-121">[(]*type-parameter* [or ... or *type-parameter*)] : (*member-signature *)</span></span>|<span data-ttu-id="7bcb5-122">Co najmniej jedna z podanych argumentów typu musi mieć element członkowski, który ma określony podpis; nie jest przeznaczone do użycia.</span><span class="sxs-lookup"><span data-stu-id="7bcb5-122">At least one of the type arguments provided must have a member that has the specified signature; not intended for common use.</span></span> <span data-ttu-id="7bcb5-123">Elementy członkowskie muszą być albo jawnie zdefiniowane na typ lub część rozszerzenia typu niejawnego jako prawidłowe elementy docelowe dla jawnego ograniczenia elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="7bcb5-123">Members must be either explicitly defined on the type or part of an implicit type extension to be valid targets for an Explicit Member Constraint.</span></span>|
|<span data-ttu-id="7bcb5-124">Ograniczenie konstruktora</span><span class="sxs-lookup"><span data-stu-id="7bcb5-124">Constructor Constraint</span></span>|<span data-ttu-id="7bcb5-125">*Parametr typu* : (new: jednostka -&gt; ")</span><span class="sxs-lookup"><span data-stu-id="7bcb5-125">*type-parameter* : ( new : unit -&gt; 'a )</span></span>|<span data-ttu-id="7bcb5-126">Podany typ musi mieć konstruktora domyślnego.</span><span class="sxs-lookup"><span data-stu-id="7bcb5-126">The provided type must have a default constructor.</span></span>|
|<span data-ttu-id="7bcb5-127">Ograniczenie typu wartości</span><span class="sxs-lookup"><span data-stu-id="7bcb5-127">Value Type Constraint</span></span>|<span data-ttu-id="7bcb5-128">: struktury</span><span class="sxs-lookup"><span data-stu-id="7bcb5-128">: struct</span></span>|<span data-ttu-id="7bcb5-129">Podany typ musi być typem wartości .NET.</span><span class="sxs-lookup"><span data-stu-id="7bcb5-129">The provided type must be a .NET value type.</span></span>|
|<span data-ttu-id="7bcb5-130">Ograniczenie typu odwołania</span><span class="sxs-lookup"><span data-stu-id="7bcb5-130">Reference Type Constraint</span></span>|<span data-ttu-id="7bcb5-131">: nie — struktura</span><span class="sxs-lookup"><span data-stu-id="7bcb5-131">: not struct</span></span>|<span data-ttu-id="7bcb5-132">Podany typ musi być typem referencyjnym .NET.</span><span class="sxs-lookup"><span data-stu-id="7bcb5-132">The provided type must be a .NET reference type.</span></span>|
|<span data-ttu-id="7bcb5-133">Ograniczenie typu wyliczenia</span><span class="sxs-lookup"><span data-stu-id="7bcb5-133">Enumeration Type Constraint</span></span>|<span data-ttu-id="7bcb5-134">: wyliczenia&lt;*typu podstawowego*&gt;</span><span class="sxs-lookup"><span data-stu-id="7bcb5-134">: enum&lt;*underlying-type*&gt;</span></span>|<span data-ttu-id="7bcb5-135">Podany typ musi być Typ wyliczany określonego typu źródłowego; nie jest przeznaczone do użycia.</span><span class="sxs-lookup"><span data-stu-id="7bcb5-135">The provided type must be an enumerated type that has the specified underlying type; not intended for common use.</span></span>|
|<span data-ttu-id="7bcb5-136">Ograniczenie delegata</span><span class="sxs-lookup"><span data-stu-id="7bcb5-136">Delegate Constraint</span></span>|<span data-ttu-id="7bcb5-137">: delegować&lt;*krotki parametru typu*, *zwracanego typu*&gt;</span><span class="sxs-lookup"><span data-stu-id="7bcb5-137">: delegate&lt;*tuple-parameter-type*, *return-type*&gt;</span></span>|<span data-ttu-id="7bcb5-138">Podany typ musi być typem delegata, który ma określone argumenty i zwracać wartość; nie jest przeznaczone do użycia.</span><span class="sxs-lookup"><span data-stu-id="7bcb5-138">The provided type must be a delegate type that has the specified arguments and return value; not intended for common use.</span></span>|
|<span data-ttu-id="7bcb5-139">Ograniczenia porównania</span><span class="sxs-lookup"><span data-stu-id="7bcb5-139">Comparison Constraint</span></span>|<span data-ttu-id="7bcb5-140">: porównania</span><span class="sxs-lookup"><span data-stu-id="7bcb5-140">: comparison</span></span>|<span data-ttu-id="7bcb5-141">Podany typ musi obsługiwać porównania.</span><span class="sxs-lookup"><span data-stu-id="7bcb5-141">The provided type must support comparison.</span></span>|
|<span data-ttu-id="7bcb5-142">Ograniczenie równości</span><span class="sxs-lookup"><span data-stu-id="7bcb5-142">Equality Constraint</span></span>|<span data-ttu-id="7bcb5-143">: równości</span><span class="sxs-lookup"><span data-stu-id="7bcb5-143">: equality</span></span>|<span data-ttu-id="7bcb5-144">Podany typ musi obsługiwać równości.</span><span class="sxs-lookup"><span data-stu-id="7bcb5-144">The provided type must support equality.</span></span>|
|<span data-ttu-id="7bcb5-145">Ograniczenie niezarządzane</span><span class="sxs-lookup"><span data-stu-id="7bcb5-145">Unmanaged Constraint</span></span>|<span data-ttu-id="7bcb5-146">: niezarządzane</span><span class="sxs-lookup"><span data-stu-id="7bcb5-146">: unmanaged</span></span>|<span data-ttu-id="7bcb5-147">Podany typ musi być typem niezarządzanym.</span><span class="sxs-lookup"><span data-stu-id="7bcb5-147">The provided type must be an unmanaged type.</span></span> <span data-ttu-id="7bcb5-148">Typy niezarządzanwe są albo niektórych typów pierwotnych (`sbyte`, `byte`, `char`, `nativeint`, `unativeint`, `float32`, `float`, `int16`, `uint16`, `int32`, `uint32`, `int64`, `uint64`, lub `decimal`), Typy wyliczeniowe `nativeptr&lt;_&gt;`, lub struktury nieogólnego, których pola są wszystkie typy niezarządzane.</span><span class="sxs-lookup"><span data-stu-id="7bcb5-148">Unmanaged types are either certain primitive types (`sbyte`, `byte`, `char`, `nativeint`, `unativeint`, `float32`, `float`, `int16`, `uint16`, `int32`, `uint32`, `int64`, `uint64`, or `decimal`), enumeration types, `nativeptr&lt;_&gt;`, or a non-generic structure whose fields are all unmanaged types.</span></span>|
<span data-ttu-id="7bcb5-149">Należy dodać ograniczenie po kodzie można użyć funkcji, która jest dostępna na typ ograniczenia, ale nie w typach ogólnie.</span><span class="sxs-lookup"><span data-stu-id="7bcb5-149">You have to add a constraint when your code has to use a feature that is available on the constraint type but not on types in general.</span></span> <span data-ttu-id="7bcb5-150">Na przykład jeśli ograniczenia typu należy użyć do określenia typu klasy, używając jednej z metod klas w ogólnym funkcja lub typ.</span><span class="sxs-lookup"><span data-stu-id="7bcb5-150">For example, if you use the type constraint to specify a class type, you can use any one of the methods of that class in the generic function or type.</span></span>

<span data-ttu-id="7bcb5-151">Określenie ograniczenia jest czasami wymagane podczas zapisywania parametrów typu jawnie, ponieważ bez ograniczenia, kompilator nie ma możliwości sprawdzenia, czy funkcje, które są używane będzie dostępny dla dowolnego typu, który może być dostarczony w czasie wykonywania dla typu parametr.</span><span class="sxs-lookup"><span data-stu-id="7bcb5-151">Specifying constraints is sometimes required when writing type parameters explicitly, because without a constraint, the compiler has no way of verifying that the features that you are using will be available on any type that might be supplied at run time for the type parameter.</span></span>

<span data-ttu-id="7bcb5-152">Ograniczenia najczęściej używanych w kodzie języka F # są ograniczenia typu, których określić klasy podstawowej lub do interfejsów.</span><span class="sxs-lookup"><span data-stu-id="7bcb5-152">The most common constraints you use in F# code are type constraints that specify base classes or interfaces.</span></span> <span data-ttu-id="7bcb5-153">Innych ograniczeń albo są używane przez biblioteki języka F # do wykonania niektórych funkcji, takich jak ograniczenia jawnego członka, które jest używane do implementowania przeładowanie operatorów arytmetycznych operatora lub znajdują się głównie, ponieważ język F # obsługuje pełną zestaw warunków ograniczających obsługiwaną przez środowisko uruchomieniowe języka wspólnego.</span><span class="sxs-lookup"><span data-stu-id="7bcb5-153">The other constraints are either used by the F# library to implement certain functionality, such as the explicit member constraint, which is used to implement operator overloading for arithmetic operators, or are provided mainly because F# supports the complete set of constraints that is supported by the common language runtime.</span></span>

<span data-ttu-id="7bcb5-154">W trakcie wnioskowania typu niektóre ograniczenia są automatycznie wykryta przez kompilator.</span><span class="sxs-lookup"><span data-stu-id="7bcb5-154">During the type inference process, some constraints are inferred automatically by the compiler.</span></span> <span data-ttu-id="7bcb5-155">Na przykład, jeśli używasz `+` operatora w funkcji, kompilator wnioskuje ograniczenie jawnego członka typy zmiennych, które są używane w wyrażeniu.</span><span class="sxs-lookup"><span data-stu-id="7bcb5-155">For example, if you use the `+` operator in a function, the compiler infers an explicit member constraint on variable types that are used in the expression.</span></span>

<span data-ttu-id="7bcb5-156">Poniższy kod ilustruje deklaracje pewne ograniczenia.</span><span class="sxs-lookup"><span data-stu-id="7bcb5-156">The following code illustrates some constraint declarations.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="7bcb5-157">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7bcb5-157">See Also</span></span>
[<span data-ttu-id="7bcb5-158">Typy ogólne</span><span class="sxs-lookup"><span data-stu-id="7bcb5-158">Generics</span></span>](index.md)

[<span data-ttu-id="7bcb5-159">Ograniczenia</span><span class="sxs-lookup"><span data-stu-id="7bcb5-159">Constraints</span></span>](constraints.md)
