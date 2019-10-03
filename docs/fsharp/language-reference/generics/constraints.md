---
title: Ograniczenia
description: Dowiedz F# się więcej o ograniczeniach, które mają zastosowanie do parametrów typu ogólnego, aby określić wymagania dla argumentu typu w ogólnym typie lub funkcji.
ms.date: 05/16/2016
ms.openlocfilehash: 9912ba63138d893a7c616661dd2b1cbdbe51916c
ms.sourcegitcommit: 878ca7550b653114c3968ef8906da2b3e60e3c7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/02/2019
ms.locfileid: "71736795"
---
# <a name="constraints"></a><span data-ttu-id="ae0c6-103">Ograniczenia</span><span class="sxs-lookup"><span data-stu-id="ae0c6-103">Constraints</span></span>

<span data-ttu-id="ae0c6-104">W tym temacie opisano ograniczenia, które można zastosować do parametrów typu ogólnego, aby określić wymagania dla argumentu typu w ogólnym typie lub funkcji.</span><span class="sxs-lookup"><span data-stu-id="ae0c6-104">This topic describes constraints that you can apply to generic type parameters to specify the requirements for a type argument in a generic type or function.</span></span>

## <a name="syntax"></a><span data-ttu-id="ae0c6-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="ae0c6-105">Syntax</span></span>

```fsharp
type-parameter-list when constraint1 [ and constraint2]
```

## <a name="remarks"></a><span data-ttu-id="ae0c6-106">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ae0c6-106">Remarks</span></span>

<span data-ttu-id="ae0c6-107">Istnieje kilka różnych ograniczeń, które można zastosować, aby ograniczyć typy, które mogą być używane w typie ogólnym.</span><span class="sxs-lookup"><span data-stu-id="ae0c6-107">There are several different constraints you can apply to limit the types that can be used in a generic type.</span></span> <span data-ttu-id="ae0c6-108">W poniższej tabeli wymieniono i opisano te ograniczenia.</span><span class="sxs-lookup"><span data-stu-id="ae0c6-108">The following table lists and describes these constraints.</span></span>

|<span data-ttu-id="ae0c6-109">Typu</span><span class="sxs-lookup"><span data-stu-id="ae0c6-109">Constraint</span></span>|<span data-ttu-id="ae0c6-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="ae0c6-110">Syntax</span></span>|<span data-ttu-id="ae0c6-111">Opis</span><span class="sxs-lookup"><span data-stu-id="ae0c6-111">Description</span></span>|
|----------|------|-----------|
|<span data-ttu-id="ae0c6-112">Ograniczenie typu</span><span class="sxs-lookup"><span data-stu-id="ae0c6-112">Type Constraint</span></span>|<span data-ttu-id="ae0c6-113">Typ *-parametr* : &gt; *Typ*</span><span class="sxs-lookup"><span data-stu-id="ae0c6-113">*type-parameter* :&gt; *type*</span></span>|<span data-ttu-id="ae0c6-114">Dostarczony typ musi być równy lub pochodny od określonego typu lub, jeśli typ jest interfejsem, udostępniony typ musi implementować interfejs.</span><span class="sxs-lookup"><span data-stu-id="ae0c6-114">The provided type must be equal to or derived from the type specified, or, if the type is an interface, the provided type must implement the interface.</span></span>|
|<span data-ttu-id="ae0c6-115">Ograniczenie null</span><span class="sxs-lookup"><span data-stu-id="ae0c6-115">Null Constraint</span></span>|<span data-ttu-id="ae0c6-116">*typ — parametr* : null</span><span class="sxs-lookup"><span data-stu-id="ae0c6-116">*type-parameter* : null</span></span>|<span data-ttu-id="ae0c6-117">Dostarczony typ musi obsługiwać literał o wartości null.</span><span class="sxs-lookup"><span data-stu-id="ae0c6-117">The provided type must support the null literal.</span></span> <span data-ttu-id="ae0c6-118">Obejmuje to wszystkie typy obiektów .NET, ale F# nie listy, krotki, funkcje, klasy, rekordu lub Unii.</span><span class="sxs-lookup"><span data-stu-id="ae0c6-118">This includes all .NET object types but not F# list, tuple, function, class, record, or union types.</span></span>|
|<span data-ttu-id="ae0c6-119">Jawne ograniczenie elementu członkowskiego</span><span class="sxs-lookup"><span data-stu-id="ae0c6-119">Explicit Member Constraint</span></span>|<span data-ttu-id="ae0c6-120">[(]*typ — parametr* [lub... lub *parametru typu*)]: (*sygnatura elementu członkowskiego*)</span><span class="sxs-lookup"><span data-stu-id="ae0c6-120">[(]*type-parameter* [or ... or *type-parameter*)] : (*member-signature*)</span></span>|<span data-ttu-id="ae0c6-121">Co najmniej jeden z podanych argumentów typu musi mieć element członkowski o określonej sygnaturze; nie przeznaczony do wspólnego użycia.</span><span class="sxs-lookup"><span data-stu-id="ae0c6-121">At least one of the type arguments provided must have a member that has the specified signature; not intended for common use.</span></span> <span data-ttu-id="ae0c6-122">Elementy członkowskie muszą być jawnie zdefiniowane w typie lub części niejawnego rozszerzenia typu, aby były prawidłowymi obiektami docelowymi dla jawnego ograniczenia elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="ae0c6-122">Members must be either explicitly defined on the type or part of an implicit type extension to be valid targets for an Explicit Member Constraint.</span></span>|
|<span data-ttu-id="ae0c6-123">Ograniczenie konstruktora</span><span class="sxs-lookup"><span data-stu-id="ae0c6-123">Constructor Constraint</span></span>|<span data-ttu-id="ae0c6-124">*parametr typu* : (New: unit-&gt; "a)</span><span class="sxs-lookup"><span data-stu-id="ae0c6-124">*type-parameter* : ( new : unit -&gt; 'a )</span></span>|<span data-ttu-id="ae0c6-125">Dostarczony typ musi mieć konstruktora bez parametrów.</span><span class="sxs-lookup"><span data-stu-id="ae0c6-125">The provided type must have a parameterless constructor.</span></span>|
|<span data-ttu-id="ae0c6-126">Ograniczenie typu wartości</span><span class="sxs-lookup"><span data-stu-id="ae0c6-126">Value Type Constraint</span></span>|<span data-ttu-id="ae0c6-127">: Struktura</span><span class="sxs-lookup"><span data-stu-id="ae0c6-127">: struct</span></span>|<span data-ttu-id="ae0c6-128">Udostępniony typ musi być typem wartości platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="ae0c6-128">The provided type must be a .NET value type.</span></span>|
|<span data-ttu-id="ae0c6-129">Ograniczenie typu odwołania</span><span class="sxs-lookup"><span data-stu-id="ae0c6-129">Reference Type Constraint</span></span>|<span data-ttu-id="ae0c6-130">: nie struktura</span><span class="sxs-lookup"><span data-stu-id="ae0c6-130">: not struct</span></span>|<span data-ttu-id="ae0c6-131">Podany typ musi być typem referencyjnym platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="ae0c6-131">The provided type must be a .NET reference type.</span></span>|
|<span data-ttu-id="ae0c6-132">Ograniczenie typu wyliczenia</span><span class="sxs-lookup"><span data-stu-id="ae0c6-132">Enumeration Type Constraint</span></span>|<span data-ttu-id="ae0c6-133">: Wyliczenie @ no__t-0*bazowe-type*&gt;</span><span class="sxs-lookup"><span data-stu-id="ae0c6-133">: enum&lt;*underlying-type*&gt;</span></span>|<span data-ttu-id="ae0c6-134">Dostarczony typ musi być typem wyliczanym, który ma określony typ podstawowy; nie przeznaczony do wspólnego użycia.</span><span class="sxs-lookup"><span data-stu-id="ae0c6-134">The provided type must be an enumerated type that has the specified underlying type; not intended for common use.</span></span>|
|<span data-ttu-id="ae0c6-135">Delegowanie ograniczenia</span><span class="sxs-lookup"><span data-stu-id="ae0c6-135">Delegate Constraint</span></span>|<span data-ttu-id="ae0c6-136">: delegowanie @ no__t-0*krotka-typ parametru*, *zwracany typ*&gt;</span><span class="sxs-lookup"><span data-stu-id="ae0c6-136">: delegate&lt;*tuple-parameter-type*, *return-type*&gt;</span></span>|<span data-ttu-id="ae0c6-137">Dostarczony typ musi być typem delegata, który ma określone argumenty i wartość zwracaną; nie przeznaczony do wspólnego użycia.</span><span class="sxs-lookup"><span data-stu-id="ae0c6-137">The provided type must be a delegate type that has the specified arguments and return value; not intended for common use.</span></span>|
|<span data-ttu-id="ae0c6-138">Ograniczenie porównania</span><span class="sxs-lookup"><span data-stu-id="ae0c6-138">Comparison Constraint</span></span>|<span data-ttu-id="ae0c6-139">: porównanie</span><span class="sxs-lookup"><span data-stu-id="ae0c6-139">: comparison</span></span>|<span data-ttu-id="ae0c6-140">Udostępniony typ musi obsługiwać porównanie.</span><span class="sxs-lookup"><span data-stu-id="ae0c6-140">The provided type must support comparison.</span></span>|
|<span data-ttu-id="ae0c6-141">Ograniczenie równości</span><span class="sxs-lookup"><span data-stu-id="ae0c6-141">Equality Constraint</span></span>|<span data-ttu-id="ae0c6-142">: równość</span><span class="sxs-lookup"><span data-stu-id="ae0c6-142">: equality</span></span>|<span data-ttu-id="ae0c6-143">Dostarczony typ musi obsługiwać równość.</span><span class="sxs-lookup"><span data-stu-id="ae0c6-143">The provided type must support equality.</span></span>|
|<span data-ttu-id="ae0c6-144">Niezarządzany warunek ograniczający</span><span class="sxs-lookup"><span data-stu-id="ae0c6-144">Unmanaged Constraint</span></span>|<span data-ttu-id="ae0c6-145">: niezarządzane</span><span class="sxs-lookup"><span data-stu-id="ae0c6-145">: unmanaged</span></span>|<span data-ttu-id="ae0c6-146">Podany typ musi być typem niezarządzanym.</span><span class="sxs-lookup"><span data-stu-id="ae0c6-146">The provided type must be an unmanaged type.</span></span> <span data-ttu-id="ae0c6-147">Typy niezarządzane to pewne typy pierwotne (`sbyte`, `byte`, `char`, `nativeint`, `unativeint`, `float32`, `float`, `int16`, `uint16`, `int32`, 0, 1, 2 lub 3), typy wyliczeniowe, 4 lub nieogólne Struktura, której wszystkie pola są typami niezarządzanymi.</span><span class="sxs-lookup"><span data-stu-id="ae0c6-147">Unmanaged types are either certain primitive types (`sbyte`, `byte`, `char`, `nativeint`, `unativeint`, `float32`, `float`, `int16`, `uint16`, `int32`, `uint32`, `int64`, `uint64`, or `decimal`), enumeration types, `nativeptr<_>`, or a non-generic structure whose fields are all unmanaged types.</span></span>|

<span data-ttu-id="ae0c6-148">Musisz dodać ograniczenie, gdy kod musi używać funkcji, która jest dostępna w typie ograniczenia, ale nie dla typów ogólnie.</span><span class="sxs-lookup"><span data-stu-id="ae0c6-148">You have to add a constraint when your code has to use a feature that is available on the constraint type but not on types in general.</span></span> <span data-ttu-id="ae0c6-149">Na przykład, jeśli używasz ograniczenia typu do określenia typu klasy, możesz użyć dowolnej z metod tej klasy w funkcji ogólnej lub w typie.</span><span class="sxs-lookup"><span data-stu-id="ae0c6-149">For example, if you use the type constraint to specify a class type, you can use any one of the methods of that class in the generic function or type.</span></span>

<span data-ttu-id="ae0c6-150">Określanie ograniczeń jest czasami wymagane w przypadku jawnego pisania parametrów typu, ponieważ bez ograniczenia kompilator nie ma możliwości sprawdzenia, czy używane funkcje będą dostępne dla dowolnego typu, który może być dostarczony w czasie wykonywania dla typu konstruktora.</span><span class="sxs-lookup"><span data-stu-id="ae0c6-150">Specifying constraints is sometimes required when writing type parameters explicitly, because without a constraint, the compiler has no way of verifying that the features that you are using will be available on any type that might be supplied at run time for the type parameter.</span></span>

<span data-ttu-id="ae0c6-151">Najbardziej typowe ograniczenia, które są używane F# w kodzie, to ograniczenia typu, które określają klasy bazowe lub interfejsy.</span><span class="sxs-lookup"><span data-stu-id="ae0c6-151">The most common constraints you use in F# code are type constraints that specify base classes or interfaces.</span></span> <span data-ttu-id="ae0c6-152">Inne ograniczenia są używane przez F# bibliotekę do implementowania pewnych funkcji, takich jak jawne ograniczenie elementu członkowskiego, który jest używany do implementowania przeciążania operatora dla operatorów arytmetycznych lub są świadczone głównie z F# powodu obsługuje pełny zestaw ograniczeń, które są obsługiwane przez środowisko uruchomieniowe języka wspólnego.</span><span class="sxs-lookup"><span data-stu-id="ae0c6-152">The other constraints are either used by the F# library to implement certain functionality, such as the explicit member constraint, which is used to implement operator overloading for arithmetic operators, or are provided mainly because F# supports the complete set of constraints that is supported by the common language runtime.</span></span>

<span data-ttu-id="ae0c6-153">W procesie wnioskowania o typie niektóre ograniczenia są wywnioskowane automatycznie przez kompilator.</span><span class="sxs-lookup"><span data-stu-id="ae0c6-153">During the type inference process, some constraints are inferred automatically by the compiler.</span></span> <span data-ttu-id="ae0c6-154">Na przykład jeśli używasz operatora `+` w funkcji, kompilator wnioskuje jawne ograniczenie elementu członkowskiego dla typów zmiennych, które są używane w wyrażeniu.</span><span class="sxs-lookup"><span data-stu-id="ae0c6-154">For example, if you use the `+` operator in a function, the compiler infers an explicit member constraint on variable types that are used in the expression.</span></span>

<span data-ttu-id="ae0c6-155">Poniższy kod ilustruje niektóre deklaracje ograniczeń:</span><span class="sxs-lookup"><span data-stu-id="ae0c6-155">The following code illustrates some constraint declarations:</span></span>

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

## <a name="see-also"></a><span data-ttu-id="ae0c6-156">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ae0c6-156">See also</span></span>

- [<span data-ttu-id="ae0c6-157">Typy ogólne</span><span class="sxs-lookup"><span data-stu-id="ae0c6-157">Generics</span></span>](index.md)
- [<span data-ttu-id="ae0c6-158">Ograniczenia</span><span class="sxs-lookup"><span data-stu-id="ae0c6-158">Constraints</span></span>](constraints.md)
