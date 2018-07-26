---
title: Ograniczenia (F#)
description: 'Więcej informacji na temat ograniczeń F #, które są stosowane do parametrów typu ogólnego, aby określić wymagania dotyczące argument typu w typie ogólnym lub funkcji.'
ms.date: 05/16/2016
ms.openlocfilehash: 7af064159d2722256f0db8286a99fc02435a99cd
ms.sourcegitcommit: 60645077dc4b62178403145f8ef691b13ffec28e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2018
ms.locfileid: "37936868"
---
# <a name="constraints"></a><span data-ttu-id="d7433-103">Ograniczenia</span><span class="sxs-lookup"><span data-stu-id="d7433-103">Constraints</span></span>

<span data-ttu-id="d7433-104">W tym temacie opisano ograniczenia stosowane do ogólnych parametrów, aby określić wymagania dotyczące argument typu w typie ogólnym lub funkcji typu.</span><span class="sxs-lookup"><span data-stu-id="d7433-104">This topic describes constraints that you can apply to generic type parameters to specify the requirements for a type argument in a generic type or function.</span></span>


## <a name="syntax"></a><span data-ttu-id="d7433-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="d7433-105">Syntax</span></span>

```fsharp
type-parameter-list when constraint1 [ and constraint2]
```

## <a name="remarks"></a><span data-ttu-id="d7433-106">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d7433-106">Remarks</span></span>
<span data-ttu-id="d7433-107">Istnieje kilka różnych ograniczeń, które można zastosować, aby ograniczyć typy, które mogą być używane w typie podstawowym.</span><span class="sxs-lookup"><span data-stu-id="d7433-107">There are several different constraints you can apply to limit the types that can be used in a generic type.</span></span> <span data-ttu-id="d7433-108">Poniższej tabeli wymieniono i opisano te ograniczenia.</span><span class="sxs-lookup"><span data-stu-id="d7433-108">The following table lists and describes these constraints.</span></span>

|<span data-ttu-id="d7433-109">Ograniczenia</span><span class="sxs-lookup"><span data-stu-id="d7433-109">Constraint</span></span>|<span data-ttu-id="d7433-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="d7433-110">Syntax</span></span>|<span data-ttu-id="d7433-111">Opis</span><span class="sxs-lookup"><span data-stu-id="d7433-111">Description</span></span>|
|----------|------|-----------|
|<span data-ttu-id="d7433-112">Ograniczenia typu</span><span class="sxs-lookup"><span data-stu-id="d7433-112">Type Constraint</span></span>|<span data-ttu-id="d7433-113">*Parametr typu* :&gt; *typu*</span><span class="sxs-lookup"><span data-stu-id="d7433-113">*type-parameter* :&gt; *type*</span></span>|<span data-ttu-id="d7433-114">Podany typ musi być większa lub równa pochodnej z typu określonego lub, jeśli typ jest interfejsem, podany typ musi implementować interfejs.</span><span class="sxs-lookup"><span data-stu-id="d7433-114">The provided type must be equal to or derived from the type specified, or, if the type is an interface, the provided type must implement the interface.</span></span>|
|<span data-ttu-id="d7433-115">Ograniczenie o wartości null</span><span class="sxs-lookup"><span data-stu-id="d7433-115">Null Constraint</span></span>|<span data-ttu-id="d7433-116">*Parametr typu* : wartość null</span><span class="sxs-lookup"><span data-stu-id="d7433-116">*type-parameter* : null</span></span>|<span data-ttu-id="d7433-117">Podany typ musi obsługiwać literałem o wartości null.</span><span class="sxs-lookup"><span data-stu-id="d7433-117">The provided type must support the null literal.</span></span> <span data-ttu-id="d7433-118">Obejmuje to wszystkie typy obiektów platformy .NET, ale nie F # listy, spójnej kolekcji, funkcji, klasy, rekord lub typy Unii.</span><span class="sxs-lookup"><span data-stu-id="d7433-118">This includes all .NET object types but not F# list, tuple, function, class, record, or union types.</span></span>|
|<span data-ttu-id="d7433-119">Ograniczenie jawnego członka</span><span class="sxs-lookup"><span data-stu-id="d7433-119">Explicit Member Constraint</span></span>|<span data-ttu-id="d7433-120">[()]*parametr typu* [lub... lub *parametr typu*)]: (*sygnatura elementu członkowskiego*)</span><span class="sxs-lookup"><span data-stu-id="d7433-120">[(]*type-parameter* [or ... or *type-parameter*)] : (*member-signature*)</span></span>|<span data-ttu-id="d7433-121">Co najmniej jeden z podanych argumentów typu musi mieć element członkowski, który ma określony podpis; nie są przeznaczone w typowych zastosowaniach.</span><span class="sxs-lookup"><span data-stu-id="d7433-121">At least one of the type arguments provided must have a member that has the specified signature; not intended for common use.</span></span> <span data-ttu-id="d7433-122">Elementy członkowskie muszą być albo jawnie zdefiniowane na typ lub część rozszerzenia niejawnego typu jako prawidłowe obiekty docelowe dla jawnego ograniczenia elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="d7433-122">Members must be either explicitly defined on the type or part of an implicit type extension to be valid targets for an Explicit Member Constraint.</span></span>|
|<span data-ttu-id="d7433-123">Ograniczenie konstruktora</span><span class="sxs-lookup"><span data-stu-id="d7433-123">Constructor Constraint</span></span>|<span data-ttu-id="d7433-124">*Parametr typu* : (nowe: jednostka -&gt; ")</span><span class="sxs-lookup"><span data-stu-id="d7433-124">*type-parameter* : ( new : unit -&gt; 'a )</span></span>|<span data-ttu-id="d7433-125">Podany typ musi mieć domyślnego konstruktora.</span><span class="sxs-lookup"><span data-stu-id="d7433-125">The provided type must have a default constructor.</span></span>|
|<span data-ttu-id="d7433-126">Ograniczenie typu wartości</span><span class="sxs-lookup"><span data-stu-id="d7433-126">Value Type Constraint</span></span>|<span data-ttu-id="d7433-127">: — struktura</span><span class="sxs-lookup"><span data-stu-id="d7433-127">: struct</span></span>|<span data-ttu-id="d7433-128">Podany typ musi być typem wartości platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="d7433-128">The provided type must be a .NET value type.</span></span>|
|<span data-ttu-id="d7433-129">Ograniczenie typu odwołania</span><span class="sxs-lookup"><span data-stu-id="d7433-129">Reference Type Constraint</span></span>|<span data-ttu-id="d7433-130">: nie — struktura</span><span class="sxs-lookup"><span data-stu-id="d7433-130">: not struct</span></span>|<span data-ttu-id="d7433-131">Podany typ musi być typem referencyjnym .NET.</span><span class="sxs-lookup"><span data-stu-id="d7433-131">The provided type must be a .NET reference type.</span></span>|
|<span data-ttu-id="d7433-132">Ograniczenie typu wyliczenia</span><span class="sxs-lookup"><span data-stu-id="d7433-132">Enumeration Type Constraint</span></span>|<span data-ttu-id="d7433-133">: wyliczenia&lt;*typu bazowego*&gt;</span><span class="sxs-lookup"><span data-stu-id="d7433-133">: enum&lt;*underlying-type*&gt;</span></span>|<span data-ttu-id="d7433-134">Podany typ musi być typu wyliczeniowego, który ma określony typ podstawowy; nie są przeznaczone w typowych zastosowaniach.</span><span class="sxs-lookup"><span data-stu-id="d7433-134">The provided type must be an enumerated type that has the specified underlying type; not intended for common use.</span></span>|
|<span data-ttu-id="d7433-135">Ograniczenie delegata</span><span class="sxs-lookup"><span data-stu-id="d7433-135">Delegate Constraint</span></span>|<span data-ttu-id="d7433-136">: delegować&lt;*krotki parametr typu*, *zwracanego typu*&gt;</span><span class="sxs-lookup"><span data-stu-id="d7433-136">: delegate&lt;*tuple-parameter-type*, *return-type*&gt;</span></span>|<span data-ttu-id="d7433-137">Podany typ musi być typem delegowanym, który ma określone argumenty i zwraca wartości; nie są przeznaczone w typowych zastosowaniach.</span><span class="sxs-lookup"><span data-stu-id="d7433-137">The provided type must be a delegate type that has the specified arguments and return value; not intended for common use.</span></span>|
|<span data-ttu-id="d7433-138">Ograniczenia porównania</span><span class="sxs-lookup"><span data-stu-id="d7433-138">Comparison Constraint</span></span>|<span data-ttu-id="d7433-139">: porównanie</span><span class="sxs-lookup"><span data-stu-id="d7433-139">: comparison</span></span>|<span data-ttu-id="d7433-140">Podany typ musi obsługiwać porównania.</span><span class="sxs-lookup"><span data-stu-id="d7433-140">The provided type must support comparison.</span></span>|
|<span data-ttu-id="d7433-141">Ograniczenie równości</span><span class="sxs-lookup"><span data-stu-id="d7433-141">Equality Constraint</span></span>|<span data-ttu-id="d7433-142">: równości</span><span class="sxs-lookup"><span data-stu-id="d7433-142">: equality</span></span>|<span data-ttu-id="d7433-143">Podany typ musi obsługiwać równości.</span><span class="sxs-lookup"><span data-stu-id="d7433-143">The provided type must support equality.</span></span>|
|<span data-ttu-id="d7433-144">Ograniczenie Unmanaged</span><span class="sxs-lookup"><span data-stu-id="d7433-144">Unmanaged Constraint</span></span>|<span data-ttu-id="d7433-145">: niezarządzanych</span><span class="sxs-lookup"><span data-stu-id="d7433-145">: unmanaged</span></span>|<span data-ttu-id="d7433-146">Podany typ musi być typem niezarządzanym.</span><span class="sxs-lookup"><span data-stu-id="d7433-146">The provided type must be an unmanaged type.</span></span> <span data-ttu-id="d7433-147">Typy niezarządzanwe są albo niektóre typy pierwotne (`sbyte`, `byte`, `char`, `nativeint`, `unativeint`, `float32`, `float`, `int16`, `uint16`, `int32`, `uint32`, `int64`, `uint64`, lub `decimal`), Typy wyliczeniowe `nativeptr&lt;_&gt;`, lub struktury nieogólnego, których pola są wszystkie typy niezarządzanych.</span><span class="sxs-lookup"><span data-stu-id="d7433-147">Unmanaged types are either certain primitive types (`sbyte`, `byte`, `char`, `nativeint`, `unativeint`, `float32`, `float`, `int16`, `uint16`, `int32`, `uint32`, `int64`, `uint64`, or `decimal`), enumeration types, `nativeptr&lt;_&gt;`, or a non-generic structure whose fields are all unmanaged types.</span></span>|
<span data-ttu-id="d7433-148">Masz Dodaj ograniczenie, jeśli kod ma można użyć funkcji, która jest ogólnie dostępne na typ ograniczenia, ale nie w typach.</span><span class="sxs-lookup"><span data-stu-id="d7433-148">You have to add a constraint when your code has to use a feature that is available on the constraint type but not on types in general.</span></span> <span data-ttu-id="d7433-149">Na przykład ograniczenia typu umożliwia określenie typu klasy, można użyć jednej z metod tej klasy, typ lub funkcja ogólna.</span><span class="sxs-lookup"><span data-stu-id="d7433-149">For example, if you use the type constraint to specify a class type, you can use any one of the methods of that class in the generic function or type.</span></span>

<span data-ttu-id="d7433-150">Określanie ograniczeń czasami jest wymagana podczas zapisywania parametrów typu w sposób jawny, ponieważ bez ograniczeń, kompilator nie ma możliwości weryfikacji, że funkcje, które są używane będzie dostępna na dowolny typ, który może być dostarczane w czasie wykonywania dla typu parametr.</span><span class="sxs-lookup"><span data-stu-id="d7433-150">Specifying constraints is sometimes required when writing type parameters explicitly, because without a constraint, the compiler has no way of verifying that the features that you are using will be available on any type that might be supplied at run time for the type parameter.</span></span>

<span data-ttu-id="d7433-151">Najbardziej typowe ograniczenia, używanej w kodzie języka F # to ograniczenia typu, określających klas podstawowych lub interfejsów.</span><span class="sxs-lookup"><span data-stu-id="d7433-151">The most common constraints you use in F# code are type constraints that specify base classes or interfaces.</span></span> <span data-ttu-id="d7433-152">Innych ograniczeń albo są używane przez biblioteki języka F # do wykonania niektórych funkcji, takich jak ograniczenie jawny element członkowski, który jest używany do implementowania operatora przeciążania operatorów arytmetycznych lub znajdują się przede wszystkim, ponieważ język F # obsługuje pełne zestaw ograniczeń, który jest obsługiwany przez środowisko uruchomieniowe języka wspólnego.</span><span class="sxs-lookup"><span data-stu-id="d7433-152">The other constraints are either used by the F# library to implement certain functionality, such as the explicit member constraint, which is used to implement operator overloading for arithmetic operators, or are provided mainly because F# supports the complete set of constraints that is supported by the common language runtime.</span></span>

<span data-ttu-id="d7433-153">Podczas procesu wnioskowania typu niektóre ograniczenia są automatycznie wykryta przez kompilator.</span><span class="sxs-lookup"><span data-stu-id="d7433-153">During the type inference process, some constraints are inferred automatically by the compiler.</span></span> <span data-ttu-id="d7433-154">Na przykład, jeśli używasz `+` operatora w funkcji, kompilator wnioskuje ograniczenie jawnego członka typy zmiennych, które są używane w wyrażeniu.</span><span class="sxs-lookup"><span data-stu-id="d7433-154">For example, if you use the `+` operator in a function, the compiler infers an explicit member constraint on variable types that are used in the expression.</span></span>

<span data-ttu-id="d7433-155">Poniższy kod ilustruje deklaracje pewne ograniczenia.</span><span class="sxs-lookup"><span data-stu-id="d7433-155">The following code illustrates some constraint declarations.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="d7433-156">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d7433-156">See Also</span></span>
[<span data-ttu-id="d7433-157">Typy ogólne</span><span class="sxs-lookup"><span data-stu-id="d7433-157">Generics</span></span>](index.md)

[<span data-ttu-id="d7433-158">Ograniczenia</span><span class="sxs-lookup"><span data-stu-id="d7433-158">Constraints</span></span>](constraints.md)
