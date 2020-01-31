---
title: Dim — Instrukcja
ms.date: 05/12/2018
f1_keywords:
- vb.Dim
- Dim
helpviewer_keywords:
- Public keyword [Visual Basic], in Dim statement
- Dim statement [Visual Basic]
- fixed-length strings [Visual Basic], declaring
- variables [Visual Basic], declaring
- WithEvents keyword [Visual Basic], Dim statement
- dynamic arrays [Visual Basic], Dim statement
- variables [Visual Basic], initializing
- '{} braces'
- fields [Visual Basic], as member variables
- declarations [Visual Basic], dynamic arrays
- member variables [Visual Basic]
- default values [Visual Basic]
- data types [Visual Basic], assigning
- braces {}
- As keyword [Visual Basic], in Dim statement
- arrays [Visual Basic], declaring
- New keyword [Visual Basic], Dim statement
- To keyword [Visual Basic], in Dim statement
- storage [Visual Basic], allocating
- local variables [Visual Basic]
- declaration statements [Visual Basic]
- Dim statement [Visual Basic], syntax
- variables [Visual Basic], member and local
ms.assetid: fae3eca1-f0b2-4400-994b-7aa58a848448
ms.openlocfilehash: 1b0c3089c366c417af926c8c0703cea021674432
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744724"
---
# <a name="dim-statement-visual-basic"></a><span data-ttu-id="9c19b-102">Dim — Instrukcja (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9c19b-102">Dim statement (Visual Basic)</span></span>

<span data-ttu-id="9c19b-103">Deklaruje i przydziela miejsce do magazynowania dla co najmniej jednej zmiennej.</span><span class="sxs-lookup"><span data-stu-id="9c19b-103">Declares and allocates storage space for one or more variables.</span></span>

## <a name="syntax"></a><span data-ttu-id="9c19b-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="9c19b-104">Syntax</span></span>

```vb
[ <attributelist> ] [ accessmodifier ] [[ Shared ] [ Shadows ] | [ Static ]] [ ReadOnly ]
Dim [ WithEvents ] variablelist
```

## <a name="parts"></a><span data-ttu-id="9c19b-105">Części</span><span class="sxs-lookup"><span data-stu-id="9c19b-105">Parts</span></span>

- `attributelist`

  <span data-ttu-id="9c19b-106">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="9c19b-106">Optional.</span></span> <span data-ttu-id="9c19b-107">Zobacz [Lista atrybutów](attribute-list.md).</span><span class="sxs-lookup"><span data-stu-id="9c19b-107">See [Attribute List](attribute-list.md).</span></span>

- `accessmodifier`

  <span data-ttu-id="9c19b-108">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="9c19b-108">Optional.</span></span> <span data-ttu-id="9c19b-109">Może to być jeden z następujących elementów:</span><span class="sxs-lookup"><span data-stu-id="9c19b-109">Can be one of the following:</span></span>

  - [<span data-ttu-id="9c19b-110">Public</span><span class="sxs-lookup"><span data-stu-id="9c19b-110">Public</span></span>](../modifiers/public.md)

  - [<span data-ttu-id="9c19b-111">Protected</span><span class="sxs-lookup"><span data-stu-id="9c19b-111">Protected</span></span>](../modifiers/protected.md)

  - [<span data-ttu-id="9c19b-112">Friend</span><span class="sxs-lookup"><span data-stu-id="9c19b-112">Friend</span></span>](../modifiers/friend.md)

  - [<span data-ttu-id="9c19b-113">Private</span><span class="sxs-lookup"><span data-stu-id="9c19b-113">Private</span></span>](../modifiers/private.md)

  - [<span data-ttu-id="9c19b-114">Protected Friend</span><span class="sxs-lookup"><span data-stu-id="9c19b-114">Protected Friend</span></span>](../modifiers/protected-friend.md)

  - [<span data-ttu-id="9c19b-115">Private Protected</span><span class="sxs-lookup"><span data-stu-id="9c19b-115">Private Protected</span></span>](../modifiers/private-protected.md)

  <span data-ttu-id="9c19b-116">Zobacz [Poziomy dostępu w języku Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="9c19b-116">See [Access levels in Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md).</span></span>

- `Shared`

  <span data-ttu-id="9c19b-117">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="9c19b-117">Optional.</span></span> <span data-ttu-id="9c19b-118">Zobacz [udostępnianie](../modifiers/shared.md).</span><span class="sxs-lookup"><span data-stu-id="9c19b-118">See [Shared](../modifiers/shared.md).</span></span>

- `Shadows`

  <span data-ttu-id="9c19b-119">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="9c19b-119">Optional.</span></span> <span data-ttu-id="9c19b-120">Zobacz [Shadows](../modifiers/shadows.md).</span><span class="sxs-lookup"><span data-stu-id="9c19b-120">See [Shadows](../modifiers/shadows.md).</span></span>

- `Static`

  <span data-ttu-id="9c19b-121">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="9c19b-121">Optional.</span></span> <span data-ttu-id="9c19b-122">Zobacz [static](../modifiers/static.md).</span><span class="sxs-lookup"><span data-stu-id="9c19b-122">See [Static](../modifiers/static.md).</span></span>

- `ReadOnly`

  <span data-ttu-id="9c19b-123">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="9c19b-123">Optional.</span></span> <span data-ttu-id="9c19b-124">Zobacz [tylko do odczytu](../modifiers/readonly.md).</span><span class="sxs-lookup"><span data-stu-id="9c19b-124">See [ReadOnly](../modifiers/readonly.md).</span></span>

- `WithEvents`

  <span data-ttu-id="9c19b-125">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="9c19b-125">Optional.</span></span> <span data-ttu-id="9c19b-126">Określa, że są to zmienne obiektów odwołujące się do wystąpień klasy, które mogą zgłaszać zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="9c19b-126">Specifies that these are object variables that refer to instances of a class that can raise events.</span></span> <span data-ttu-id="9c19b-127">Zobacz [WithEvents](../modifiers/withevents.md).</span><span class="sxs-lookup"><span data-stu-id="9c19b-127">See [WithEvents](../modifiers/withevents.md).</span></span>

- `variablelist`

  <span data-ttu-id="9c19b-128">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="9c19b-128">Required.</span></span> <span data-ttu-id="9c19b-129">Lista zmiennych, które są zadeklarowane w tej instrukcji.</span><span class="sxs-lookup"><span data-stu-id="9c19b-129">List of variables being declared in this statement.</span></span>

  `variable [ , variable ... ]`

  <span data-ttu-id="9c19b-130">Każda `variable` ma następującą składnię i części:</span><span class="sxs-lookup"><span data-stu-id="9c19b-130">Each `variable` has the following syntax and parts:</span></span>

  <span data-ttu-id="9c19b-131">`variablename [ ( [ boundslist ] ) ] [ As [ New ] datatype [ With`{`[ .propertyname = propinitializer [ , ... ] ] } ] ] [ = initializer ]`</span><span class="sxs-lookup"><span data-stu-id="9c19b-131">`variablename [ ( [ boundslist ] ) ] [ As [ New ] datatype [ With`{`[ .propertyname = propinitializer [ , ... ] ] } ] ] [ = initializer ]`</span></span>

  |<span data-ttu-id="9c19b-132">Części</span><span class="sxs-lookup"><span data-stu-id="9c19b-132">Part</span></span>|<span data-ttu-id="9c19b-133">Opis</span><span class="sxs-lookup"><span data-stu-id="9c19b-133">Description</span></span>|
  |---|---|
  |`variablename`|<span data-ttu-id="9c19b-134">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="9c19b-134">Required.</span></span> <span data-ttu-id="9c19b-135">Nazwa zmiennej.</span><span class="sxs-lookup"><span data-stu-id="9c19b-135">Name of the variable.</span></span> <span data-ttu-id="9c19b-136">Zobacz [Zadeklarowane nazwy elementów](../../programming-guide/language-features/declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="9c19b-136">See [Declared Element Names](../../programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>|
  |`boundslist`|<span data-ttu-id="9c19b-137">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="9c19b-137">Optional.</span></span> <span data-ttu-id="9c19b-138">Lista granic każdego wymiaru zmiennej tablicowej.</span><span class="sxs-lookup"><span data-stu-id="9c19b-138">List of bounds of each dimension of an array variable.</span></span>|
  |`New`|<span data-ttu-id="9c19b-139">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="9c19b-139">Optional.</span></span> <span data-ttu-id="9c19b-140">Tworzy nowe wystąpienie klasy podczas uruchamiania instrukcji `Dim`.</span><span class="sxs-lookup"><span data-stu-id="9c19b-140">Creates a new instance of the class when the `Dim` statement runs.</span></span>|
  |`datatype`|<span data-ttu-id="9c19b-141">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="9c19b-141">Optional.</span></span> <span data-ttu-id="9c19b-142">Typ danych zmiennej.</span><span class="sxs-lookup"><span data-stu-id="9c19b-142">Data type of the variable.</span></span>|
  |`With`|<span data-ttu-id="9c19b-143">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="9c19b-143">Optional.</span></span> <span data-ttu-id="9c19b-144">Wprowadza listę inicjatora obiektów.</span><span class="sxs-lookup"><span data-stu-id="9c19b-144">Introduces the object initializer list.</span></span>|
  |`propertyname`|<span data-ttu-id="9c19b-145">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="9c19b-145">Optional.</span></span> <span data-ttu-id="9c19b-146">Nazwa właściwości w klasie, dla której tworzysz wystąpienie.</span><span class="sxs-lookup"><span data-stu-id="9c19b-146">The name of a property in the class you are making an instance of.</span></span>|
  |`propinitializer`|<span data-ttu-id="9c19b-147">Wymagane po `propertyname` =.</span><span class="sxs-lookup"><span data-stu-id="9c19b-147">Required after `propertyname` =.</span></span> <span data-ttu-id="9c19b-148">Wyrażenie, które jest oceniane i przypisywane do nazwy właściwości.</span><span class="sxs-lookup"><span data-stu-id="9c19b-148">The expression that is evaluated and assigned to the property name.</span></span>|
  |`initializer`|<span data-ttu-id="9c19b-149">Opcjonalne, jeśli nie określono `New`.</span><span class="sxs-lookup"><span data-stu-id="9c19b-149">Optional if `New` is not specified.</span></span> <span data-ttu-id="9c19b-150">Wyrażenie, które jest oceniane i przypisywane do zmiennej podczas jej tworzenia.</span><span class="sxs-lookup"><span data-stu-id="9c19b-150">Expression that is evaluated and assigned to the variable when it is created.</span></span>|

## <a name="remarks"></a><span data-ttu-id="9c19b-151">Uwagi</span><span class="sxs-lookup"><span data-stu-id="9c19b-151">Remarks</span></span>

<span data-ttu-id="9c19b-152">Kompilator Visual Basic używa instrukcji `Dim` do określenia typu danych zmiennej i innych informacji, takich jak kod, który może uzyskać dostęp do zmiennej.</span><span class="sxs-lookup"><span data-stu-id="9c19b-152">The Visual Basic compiler uses the `Dim` statement to determine the variable's data type and other information, such as what code can access the variable.</span></span> <span data-ttu-id="9c19b-153">Poniższy przykład deklaruje zmienną do przechowywania wartości `Integer`.</span><span class="sxs-lookup"><span data-stu-id="9c19b-153">The following example declares a variable to hold an `Integer` value.</span></span>

```vb
Dim numberOfStudents As Integer
```

<span data-ttu-id="9c19b-154">Można określić dowolny typ danych lub nazwę wyliczenia, struktury, klasy lub interfejsu.</span><span class="sxs-lookup"><span data-stu-id="9c19b-154">You can specify any data type or the name of an enumeration, structure, class, or interface.</span></span>

```vb
Dim finished As Boolean
Dim monitorBox As System.Windows.Forms.Form
```

<span data-ttu-id="9c19b-155">Dla typu referencyjnego za pomocą słowa kluczowego `New` można utworzyć nowe wystąpienie klasy lub struktury, która jest określona przez typ danych.</span><span class="sxs-lookup"><span data-stu-id="9c19b-155">For a reference type, you use the `New` keyword to create a new instance of the class or structure that is specified by the data type.</span></span> <span data-ttu-id="9c19b-156">Jeśli używasz `New`, nie używasz wyrażenia inicjatora.</span><span class="sxs-lookup"><span data-stu-id="9c19b-156">If you use `New`, you do not use an initializer expression.</span></span> <span data-ttu-id="9c19b-157">Zamiast tego należy podać argumenty, jeśli są wymagane, do konstruktora klasy, z której tworzysz zmienną.</span><span class="sxs-lookup"><span data-stu-id="9c19b-157">Instead, you supply arguments, if they are required, to the constructor of the class from which you are creating the variable.</span></span>

```vb
Dim bottomLabel As New System.Windows.Forms.Label
```

<span data-ttu-id="9c19b-158">Można zadeklarować zmienną w procedurze, bloku, klasie, strukturze lub module.</span><span class="sxs-lookup"><span data-stu-id="9c19b-158">You can declare a variable in a procedure, block, class, structure, or module.</span></span> <span data-ttu-id="9c19b-159">Nie można zadeklarować zmiennej w pliku źródłowym, przestrzeni nazw lub interfejsie.</span><span class="sxs-lookup"><span data-stu-id="9c19b-159">You cannot declare a variable in a source file, namespace, or interface.</span></span> <span data-ttu-id="9c19b-160">Aby uzyskać więcej informacji, zobacz [Konteksty deklaracji i domyślne poziomy dostępu](declaration-contexts-and-default-access-levels.md)</span><span class="sxs-lookup"><span data-stu-id="9c19b-160">For more information, see [Declaration Contexts and Default Access Levels](declaration-contexts-and-default-access-levels.md).</span></span>

<span data-ttu-id="9c19b-161">Zmienna zadeklarowana na poziomie modułu, poza żadną procedurą, to zmienna lub *pole* *Członkowskie* .</span><span class="sxs-lookup"><span data-stu-id="9c19b-161">A variable that is declared at module level, outside any procedure, is a *member variable* or *field*.</span></span> <span data-ttu-id="9c19b-162">Zmienne składowe znajdują się w zakresie w całej klasy, strukturze lub module.</span><span class="sxs-lookup"><span data-stu-id="9c19b-162">Member variables are in scope throughout their class, structure, or module.</span></span> <span data-ttu-id="9c19b-163">Zmienna zadeklarowana na poziomie procedury jest *zmienną lokalną*.</span><span class="sxs-lookup"><span data-stu-id="9c19b-163">A variable that is declared at procedure level is a *local variable*.</span></span> <span data-ttu-id="9c19b-164">Zmienne lokalne znajdują się w zakresie tylko w obrębie procedury lub bloku.</span><span class="sxs-lookup"><span data-stu-id="9c19b-164">Local variables are in scope only within their procedure or block.</span></span>

<span data-ttu-id="9c19b-165">Poniższe Modyfikatory dostępu są używane do deklarowania zmiennych poza procedurą: `Public`, `Protected`, `Friend`, `Protected Friend`i `Private`.</span><span class="sxs-lookup"><span data-stu-id="9c19b-165">The following access modifiers are used to declare variables outside a procedure: `Public`, `Protected`, `Friend`, `Protected Friend`, and `Private`.</span></span> <span data-ttu-id="9c19b-166">Aby uzyskać więcej informacji, zobacz temat [Poziomy dostępu w języku Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="9c19b-166">For more information, see [Access levels in Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md).</span></span>

<span data-ttu-id="9c19b-167">Słowo kluczowe `Dim` jest opcjonalne i zwykle pomijane, jeśli określisz dowolny z następujących modyfikatorów: `Public`, `Protected`, `Friend`, `Protected Friend`, `Private`, `Shared`, `Shadows`, `Static`, `ReadOnly`lub `WithEvents`.</span><span class="sxs-lookup"><span data-stu-id="9c19b-167">The `Dim` keyword is optional and usually omitted if you specify any of the following modifiers: `Public`, `Protected`, `Friend`, `Protected Friend`, `Private`, `Shared`, `Shadows`, `Static`, `ReadOnly`, or `WithEvents`.</span></span>

```vb
Public maximumAllowed As Double
Protected Friend currentUserName As String
Private salary As Decimal
Static runningTotal As Integer
```

<span data-ttu-id="9c19b-168">Jeśli `Option Explicit` jest włączone (wartość domyślna), kompilator wymaga deklaracji dla każdej używanej zmiennej.</span><span class="sxs-lookup"><span data-stu-id="9c19b-168">If `Option Explicit` is on (the default), the compiler requires a declaration for every variable you use.</span></span> <span data-ttu-id="9c19b-169">Aby uzyskać więcej informacji, zobacz [Option Explicit](option-explicit-statement.md).</span><span class="sxs-lookup"><span data-stu-id="9c19b-169">For more information, see [Option Explicit Statement](option-explicit-statement.md).</span></span>

## <a name="specifying-an-initial-value"></a><span data-ttu-id="9c19b-170">Określanie wartości początkowej</span><span class="sxs-lookup"><span data-stu-id="9c19b-170">Specifying an initial value</span></span>

<span data-ttu-id="9c19b-171">Podczas tworzenia można przypisać wartość do zmiennej.</span><span class="sxs-lookup"><span data-stu-id="9c19b-171">You can assign a value to a variable when it is created.</span></span> <span data-ttu-id="9c19b-172">Dla typu wartości należy użyć *inicjatora* , aby podać wyrażenie, które ma zostać przypisane do zmiennej.</span><span class="sxs-lookup"><span data-stu-id="9c19b-172">For a value type, you use an *initializer* to supply an expression to be assigned to the variable.</span></span> <span data-ttu-id="9c19b-173">Wyrażenie musi obliczyć stałą, którą można obliczyć w czasie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="9c19b-173">The expression must evaluate to a constant that can be calculated at compile time.</span></span>

```vb
Dim quantity As Integer = 10
Dim message As String = "Just started"
```

<span data-ttu-id="9c19b-174">Jeśli inicjator jest określony i typ danych nie jest określony w klauzuli `As`, *wnioskowanie typu* jest używane do wywnioskowania typu danych z inicjatora.</span><span class="sxs-lookup"><span data-stu-id="9c19b-174">If an initializer is specified and a data type is not specified in an `As` clause, *type inference* is used to infer the data type from the initializer.</span></span> <span data-ttu-id="9c19b-175">W poniższym przykładzie zarówno `num1`, jak i `num2` są silnie wpisane jako liczby całkowite.</span><span class="sxs-lookup"><span data-stu-id="9c19b-175">In the following example, both `num1` and `num2` are strongly typed as integers.</span></span> <span data-ttu-id="9c19b-176">W drugiej deklaracji typ wnioskowania wnioskuje typ z wartości 3.</span><span class="sxs-lookup"><span data-stu-id="9c19b-176">In the second declaration, type inference infers the type from the value 3.</span></span>

```vb
' Use explicit typing.
Dim num1 As Integer = 3

' Use local type inference.
Dim num2 = 3
```

<span data-ttu-id="9c19b-177">Wnioskowanie o typie ma zastosowanie na poziomie procedury.</span><span class="sxs-lookup"><span data-stu-id="9c19b-177">Type inference applies at the procedure level.</span></span> <span data-ttu-id="9c19b-178">Nie ma zastosowania poza procedurą w klasie, strukturze, module lub interfejsie.</span><span class="sxs-lookup"><span data-stu-id="9c19b-178">It does not apply outside a procedure in a class, structure, module, or interface.</span></span> <span data-ttu-id="9c19b-179">Aby uzyskać więcej informacji na temat wnioskowania o typie, zobacz [instrukcja wnioskowania](option-infer-statement.md) i [wnioskowanie o typie lokalnym](../../programming-guide/language-features/variables/local-type-inference.md).</span><span class="sxs-lookup"><span data-stu-id="9c19b-179">For more information about type inference, see [Option Infer Statement](option-infer-statement.md) and [Local Type Inference](../../programming-guide/language-features/variables/local-type-inference.md).</span></span>

<span data-ttu-id="9c19b-180">Aby uzyskać informacje o tym, co się stanie, gdy nie określono typu danych lub inicjatora, zobacz [domyślne typy danych i wartości](dim-statement.md#default) w dalszej części tego tematu.</span><span class="sxs-lookup"><span data-stu-id="9c19b-180">For information about what happens when a data type or initializer is not specified, see [Default Data Types and Values](dim-statement.md#default) later in this topic.</span></span>

<span data-ttu-id="9c19b-181">*Inicjatora obiektów* można użyć do deklarowania wystąpień typów nazwanych i anonimowych.</span><span class="sxs-lookup"><span data-stu-id="9c19b-181">You can use an *object initializer* to declare instances of named and anonymous types.</span></span> <span data-ttu-id="9c19b-182">Poniższy kod tworzy wystąpienie klasy `Student` i używa inicjatora obiektów do inicjowania właściwości.</span><span class="sxs-lookup"><span data-stu-id="9c19b-182">The following code creates an instance of a `Student` class and uses an object initializer to initialize properties.</span></span>

```vb
Dim student1 As New Student With {.First = "Michael",
                                  .Last = "Tucker"}
```

<span data-ttu-id="9c19b-183">Aby uzyskać więcej informacji na temat inicjatorów obiektów, zobacz [How to: DECLARE a Object przy użyciu inicjatora obiektów](../../programming-guide/language-features/objects-and-classes/how-to-declare-an-object-by-using-an-object-initializer.md) [: typy nazwane i anonimowe](../../programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)oraz [Typy anonimowe](../../programming-guide/language-features/objects-and-classes/anonymous-types.md).</span><span class="sxs-lookup"><span data-stu-id="9c19b-183">For more information about object initializers, see [How to: Declare an Object by Using an Object Initializer](../../programming-guide/language-features/objects-and-classes/how-to-declare-an-object-by-using-an-object-initializer.md), [Object Initializers: Named and Anonymous Types](../../programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md), and [Anonymous Types](../../programming-guide/language-features/objects-and-classes/anonymous-types.md).</span></span>

## <a name="declaring-multiple-variables"></a><span data-ttu-id="9c19b-184">Deklarowanie wielu zmiennych</span><span class="sxs-lookup"><span data-stu-id="9c19b-184">Declaring multiple variables</span></span>

<span data-ttu-id="9c19b-185">Można zadeklarować kilka zmiennych w jednej instrukcji deklaracji, określając nazwę zmiennej dla każdej z nich i po każdej nazwie tablicy z nawiasami.</span><span class="sxs-lookup"><span data-stu-id="9c19b-185">You can declare several variables in one declaration statement, specifying the variable name for each one, and following each array name with parentheses.</span></span> <span data-ttu-id="9c19b-186">W przypadku wielu zmiennych są one oddzielane przecinkami.</span><span class="sxs-lookup"><span data-stu-id="9c19b-186">Multiple variables are separated by commas.</span></span>

```vb
Dim lastTime, nextTime, allTimes() As Date
```

<span data-ttu-id="9c19b-187">W przypadku deklarowania więcej niż jednej zmiennej z jedną klauzulą `As` nie można dostarczyć inicjatora dla tej grupy zmiennych.</span><span class="sxs-lookup"><span data-stu-id="9c19b-187">If you declare more than one variable with one `As` clause, you cannot supply an initializer for that group of variables.</span></span>

<span data-ttu-id="9c19b-188">Można określić różne typy danych dla różnych zmiennych przy użyciu oddzielnej klauzuli `As` dla każdej zadeklarowanej zmiennej.</span><span class="sxs-lookup"><span data-stu-id="9c19b-188">You can specify different data types for different variables by using a separate `As` clause for each variable you declare.</span></span> <span data-ttu-id="9c19b-189">Każda zmienna przyjmuje typ danych określony w pierwszej klauzuli `As` napotkanej po jego części `variablename`.</span><span class="sxs-lookup"><span data-stu-id="9c19b-189">Each variable takes the data type specified in the first `As` clause encountered after its `variablename` part.</span></span>

```vb
Dim a, b, c As Single, x, y As Double, i As Integer
' a, b, and c are all Single; x and y are both Double
```

## <a name="arrays"></a><span data-ttu-id="9c19b-190">Tablice</span><span class="sxs-lookup"><span data-stu-id="9c19b-190">Arrays</span></span>

<span data-ttu-id="9c19b-191">Można zadeklarować zmienną do przechowywania *tablicy*, która może zawierać wiele wartości.</span><span class="sxs-lookup"><span data-stu-id="9c19b-191">You can declare a variable to hold an *array*, which can hold multiple values.</span></span> <span data-ttu-id="9c19b-192">Aby określić, że zmienna przechowuje tablicę, obserwuj jej `variablename` bezpośrednio z nawiasami.</span><span class="sxs-lookup"><span data-stu-id="9c19b-192">To specify that a variable holds an array, follow its `variablename` immediately with parentheses.</span></span> <span data-ttu-id="9c19b-193">Aby uzyskać więcej informacji na temat tablic, zobacz [tablice](../../programming-guide/language-features/arrays/index.md).</span><span class="sxs-lookup"><span data-stu-id="9c19b-193">For more information about arrays, see [Arrays](../../programming-guide/language-features/arrays/index.md).</span></span>

<span data-ttu-id="9c19b-194">Można określić dolną i górną granicę każdego wymiaru tablicy.</span><span class="sxs-lookup"><span data-stu-id="9c19b-194">You can specify the lower and upper bound of each dimension of an array.</span></span> <span data-ttu-id="9c19b-195">W tym celu należy uwzględnić `boundslist` wewnątrz nawiasów.</span><span class="sxs-lookup"><span data-stu-id="9c19b-195">To do this, include a `boundslist` inside the parentheses.</span></span> <span data-ttu-id="9c19b-196">Dla każdego wymiaru `boundslist` określa górną granicę i opcjonalnie dolną granicę.</span><span class="sxs-lookup"><span data-stu-id="9c19b-196">For each dimension, the `boundslist` specifies the upper bound and optionally the lower bound.</span></span> <span data-ttu-id="9c19b-197">Dolna granica jest zawsze równa zero, niezależnie od tego, czy została określona, czy nie.</span><span class="sxs-lookup"><span data-stu-id="9c19b-197">The lower bound is always zero, whether you specify it or not.</span></span> <span data-ttu-id="9c19b-198">Każdy indeks może się różnić od zera za pośrednictwem jego górnej wartości powiązanej.</span><span class="sxs-lookup"><span data-stu-id="9c19b-198">Each index can vary from zero through its upper bound value.</span></span>

<span data-ttu-id="9c19b-199">Poniższe dwie instrukcje są równoważne.</span><span class="sxs-lookup"><span data-stu-id="9c19b-199">The following two statements are equivalent.</span></span> <span data-ttu-id="9c19b-200">Każda instrukcja deklaruje tablicę z 21 `Integer` elementów.</span><span class="sxs-lookup"><span data-stu-id="9c19b-200">Each statement declares an array of 21 `Integer` elements.</span></span> <span data-ttu-id="9c19b-201">Gdy uzyskujesz dostęp do tablicy, indeks może się różnić od 0 do 20.</span><span class="sxs-lookup"><span data-stu-id="9c19b-201">When you access the array, the index can vary from 0 through 20.</span></span>

```vb
Dim totals(20) As Integer
Dim totals(0 To 20) As Integer
```

<span data-ttu-id="9c19b-202">Poniższa instrukcja deklaruje dwuwymiarową tablicę typu `Double`.</span><span class="sxs-lookup"><span data-stu-id="9c19b-202">The following statement declares a two-dimensional array of type `Double`.</span></span> <span data-ttu-id="9c19b-203">Tablica zawiera 4 wiersze (3 + 1) z 6 kolumn (5 + 1) każdy.</span><span class="sxs-lookup"><span data-stu-id="9c19b-203">The array has 4 rows (3 + 1) of 6 columns (5 + 1) each.</span></span> <span data-ttu-id="9c19b-204">Należy zauważyć, że górna granica reprezentuje najwyższe możliwe wartości dla indeksu, a nie długość wymiaru.</span><span class="sxs-lookup"><span data-stu-id="9c19b-204">Note that an upper bound represents the highest possible value for the index, not the length of the dimension.</span></span> <span data-ttu-id="9c19b-205">Wymiar jest długością górnej granicy powiększonej o jeden.</span><span class="sxs-lookup"><span data-stu-id="9c19b-205">The length of the dimension is the upper bound plus one.</span></span>

```vb
Dim matrix2(3, 5) As Double
```

<span data-ttu-id="9c19b-206">Tablica może mieć od 1 do 32 wymiarów.</span><span class="sxs-lookup"><span data-stu-id="9c19b-206">An array can have from 1 to 32 dimensions.</span></span>

<span data-ttu-id="9c19b-207">Wszystkie granice można pozostawić puste w deklaracji tablicy.</span><span class="sxs-lookup"><span data-stu-id="9c19b-207">You can leave all the bounds blank in an array declaration.</span></span> <span data-ttu-id="9c19b-208">W takim przypadku tablica ma określoną liczbę wymiarów, ale nie została zainicjowana.</span><span class="sxs-lookup"><span data-stu-id="9c19b-208">If you do this, the array has the number of dimensions you specify, but it is uninitialized.</span></span> <span data-ttu-id="9c19b-209">Ma wartość `Nothing`, dopóki nie zostanie zainicjowana co najmniej część jej elementów.</span><span class="sxs-lookup"><span data-stu-id="9c19b-209">It has a value of `Nothing` until you initialize at least some of its elements.</span></span> <span data-ttu-id="9c19b-210">Instrukcja `Dim` musi określać granice dla wszystkich wymiarów lub dla żadnych wymiarów.</span><span class="sxs-lookup"><span data-stu-id="9c19b-210">The `Dim` statement must specify bounds either for all dimensions or for no dimensions.</span></span>

```vb
' Declare an array with blank array bounds.
Dim messages() As String
' Initialize the array.
ReDim messages(4)
```

<span data-ttu-id="9c19b-211">Jeśli tablica ma więcej niż jeden wymiar, musisz uwzględnić przecinki między nawiasami, aby wskazać liczbę wymiarów.</span><span class="sxs-lookup"><span data-stu-id="9c19b-211">If the array has more than one dimension, you must include commas between the parentheses to indicate the number of dimensions.</span></span>

```vb
Dim oneDimension(), twoDimensions(,), threeDimensions(,,) As Byte
```

<span data-ttu-id="9c19b-212">*Tablicę o zerowej długości* można zadeklarować przez zadeklarowanie jednego z wymiarów tablicy jako-1.</span><span class="sxs-lookup"><span data-stu-id="9c19b-212">You can declare a *zero-length array* by declaring one of the array's dimensions to be -1.</span></span> <span data-ttu-id="9c19b-213">Zmienna, która przechowuje tablicę o zerowej długości, nie ma wartości `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="9c19b-213">A variable that holds a zero-length array does not have the value `Nothing`.</span></span> <span data-ttu-id="9c19b-214">Tablice o zerowej długości są wymagane przez niektóre funkcje środowiska uruchomieniowego języka wspólnego.</span><span class="sxs-lookup"><span data-stu-id="9c19b-214">Zero-length arrays are required by certain common language runtime functions.</span></span> <span data-ttu-id="9c19b-215">Jeśli spróbujesz uzyskać dostęp do takiej tablicy, wystąpi wyjątek w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="9c19b-215">If you try to access such an array, a runtime exception occurs.</span></span> <span data-ttu-id="9c19b-216">Aby uzyskać więcej informacji, zobacz [tablice](../../programming-guide/language-features/arrays/index.md).</span><span class="sxs-lookup"><span data-stu-id="9c19b-216">For more information, see [Arrays](../../programming-guide/language-features/arrays/index.md).</span></span>

<span data-ttu-id="9c19b-217">Można zainicjować wartości tablicy przy użyciu literału tablicy.</span><span class="sxs-lookup"><span data-stu-id="9c19b-217">You can initialize the values of an array by using an array literal.</span></span> <span data-ttu-id="9c19b-218">W tym celu należy ująć wartości inicjujące za pomocą nawiasów klamrowych (`{}`).</span><span class="sxs-lookup"><span data-stu-id="9c19b-218">To do this, surround the initialization values with braces (`{}`).</span></span>

```vb
Dim longArray() As Long = {0, 1, 2, 3}
```

<span data-ttu-id="9c19b-219">W przypadku tablic wielowymiarowych Inicjalizacja dla każdego oddzielnego wymiaru jest ujęta w nawiasy klamrowe w zewnętrznym wymiarze.</span><span class="sxs-lookup"><span data-stu-id="9c19b-219">For multidimensional arrays, the initialization for each separate dimension is enclosed in braces in the outer dimension.</span></span> <span data-ttu-id="9c19b-220">Elementy są określone w kolejności wierszy — główne.</span><span class="sxs-lookup"><span data-stu-id="9c19b-220">The elements are specified in row-major order.</span></span>

```vb
Dim twoDimensions(,) As Integer = {{0, 1, 2}, {10, 11, 12}}
```

<span data-ttu-id="9c19b-221">Aby uzyskać więcej informacji na temat literałów tablicowych, zobacz [tablice](../../programming-guide/language-features/arrays/index.md).</span><span class="sxs-lookup"><span data-stu-id="9c19b-221">For more information about array literals, see [Arrays](../../programming-guide/language-features/arrays/index.md).</span></span>

## <a name="default"></a><span data-ttu-id="9c19b-222">Domyślne typy danych i wartości</span><span class="sxs-lookup"><span data-stu-id="9c19b-222">Default data types and values</span></span>

<span data-ttu-id="9c19b-223">W poniższej tabeli opisano wyniki różnych kombinacji określania typu danych i inicjatora w instrukcji `Dim`.</span><span class="sxs-lookup"><span data-stu-id="9c19b-223">The following table describes the results of various combinations of specifying the data type and initializer in a `Dim` statement.</span></span>

|<span data-ttu-id="9c19b-224">Określono typ danych?</span><span class="sxs-lookup"><span data-stu-id="9c19b-224">Data type specified?</span></span>|<span data-ttu-id="9c19b-225">Określono inicjator?</span><span class="sxs-lookup"><span data-stu-id="9c19b-225">Initializer specified?</span></span>|<span data-ttu-id="9c19b-226">Przykład</span><span class="sxs-lookup"><span data-stu-id="9c19b-226">Example</span></span>|<span data-ttu-id="9c19b-227">Wynik</span><span class="sxs-lookup"><span data-stu-id="9c19b-227">Result</span></span>|
|---|---|---|---|
|<span data-ttu-id="9c19b-228">Nie</span><span class="sxs-lookup"><span data-stu-id="9c19b-228">No</span></span>|<span data-ttu-id="9c19b-229">Nie</span><span class="sxs-lookup"><span data-stu-id="9c19b-229">No</span></span>|`Dim qty`|<span data-ttu-id="9c19b-230">Jeśli [opcja Strict](option-strict-statement.md) jest wyłączona (wartość domyślna), zmienna jest ustawiona na `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="9c19b-230">If [Option Strict](option-strict-statement.md) is off (the default), the variable is set to `Nothing`.</span></span><br /><br /> <span data-ttu-id="9c19b-231">Jeśli `Option Strict` jest włączona, wystąpi błąd w czasie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="9c19b-231">If `Option Strict` is on, a compile-time error occurs.</span></span>|
|<span data-ttu-id="9c19b-232">Nie</span><span class="sxs-lookup"><span data-stu-id="9c19b-232">No</span></span>|<span data-ttu-id="9c19b-233">Tak</span><span class="sxs-lookup"><span data-stu-id="9c19b-233">Yes</span></span>|`Dim qty = 5`|<span data-ttu-id="9c19b-234">Jeśli [opcja wnioskowanie](option-infer-statement.md) jest włączona (wartość domyślna), zmienna Pobiera typ danych inicjatora.</span><span class="sxs-lookup"><span data-stu-id="9c19b-234">If [Option Infer](option-infer-statement.md) is on (the default), the variable takes the data type of the initializer.</span></span> <span data-ttu-id="9c19b-235">Zobacz [wnioskowanie o typie lokalnym](../../programming-guide/language-features/variables/local-type-inference.md).</span><span class="sxs-lookup"><span data-stu-id="9c19b-235">See [Local Type Inference](../../programming-guide/language-features/variables/local-type-inference.md).</span></span><br /><br /> <span data-ttu-id="9c19b-236">Jeśli `Option Infer` jest wyłączone i `Option Strict` jest wyłączone, zmienna Pobiera typ danych `Object`.</span><span class="sxs-lookup"><span data-stu-id="9c19b-236">If `Option Infer` is off and `Option Strict` is off, the variable takes the data type of `Object`.</span></span><br /><br /> <span data-ttu-id="9c19b-237">Jeśli `Option Infer` jest wyłączona i `Option Strict` jest włączona, wystąpi błąd w czasie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="9c19b-237">If `Option Infer` is off and `Option Strict` is on, a compile-time error occurs.</span></span>|
|<span data-ttu-id="9c19b-238">Tak</span><span class="sxs-lookup"><span data-stu-id="9c19b-238">Yes</span></span>|<span data-ttu-id="9c19b-239">Nie</span><span class="sxs-lookup"><span data-stu-id="9c19b-239">No</span></span>|`Dim qty As Integer`|<span data-ttu-id="9c19b-240">Zmienna jest inicjowana do wartości domyślnej dla typu danych.</span><span class="sxs-lookup"><span data-stu-id="9c19b-240">The variable is initialized to the default value for the data type.</span></span> <span data-ttu-id="9c19b-241">Zapoznaj się z tabelą w dalszej części tej sekcji.</span><span class="sxs-lookup"><span data-stu-id="9c19b-241">See the table later in this section.</span></span>|
|<span data-ttu-id="9c19b-242">Tak</span><span class="sxs-lookup"><span data-stu-id="9c19b-242">Yes</span></span>|<span data-ttu-id="9c19b-243">Tak</span><span class="sxs-lookup"><span data-stu-id="9c19b-243">Yes</span></span>|`Dim qty  As Integer = 5`|<span data-ttu-id="9c19b-244">Jeśli typ danych inicjatora nie zostanie przekonwertowany na określony typ danych, wystąpi błąd w czasie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="9c19b-244">If the data type of the initializer is not convertible to the specified data type, a compile-time error occurs.</span></span>|

<span data-ttu-id="9c19b-245">Jeśli określisz typ danych, ale nie określisz inicjatora, Visual Basic inicjuje zmienną do wartości domyślnej dla tego typu danych.</span><span class="sxs-lookup"><span data-stu-id="9c19b-245">If you specify a data type but do not specify an initializer, Visual Basic initializes the variable to the default value for its data type.</span></span> <span data-ttu-id="9c19b-246">W poniższej tabeli przedstawiono domyślne wartości inicjujące.</span><span class="sxs-lookup"><span data-stu-id="9c19b-246">The following table shows the default initialization values.</span></span>

|<span data-ttu-id="9c19b-247">Typ danych</span><span class="sxs-lookup"><span data-stu-id="9c19b-247">Data type</span></span>|<span data-ttu-id="9c19b-248">Wartość domyślna</span><span class="sxs-lookup"><span data-stu-id="9c19b-248">Default value</span></span>|
|---|---|
|<span data-ttu-id="9c19b-249">Wszystkie typy liczbowe (w tym `Byte` i `SByte`)</span><span class="sxs-lookup"><span data-stu-id="9c19b-249">All numeric types (including `Byte` and `SByte`)</span></span>|<span data-ttu-id="9c19b-250">0</span><span class="sxs-lookup"><span data-stu-id="9c19b-250">0</span></span>|
|`Char`|<span data-ttu-id="9c19b-251">Plik binarny 0</span><span class="sxs-lookup"><span data-stu-id="9c19b-251">Binary 0</span></span>|
|<span data-ttu-id="9c19b-252">Wszystkie typy odwołań (w tym `Object`, `String`i wszystkie tablice)</span><span class="sxs-lookup"><span data-stu-id="9c19b-252">All reference types (including `Object`, `String`, and all arrays)</span></span>|`Nothing`|
|`Boolean`|`False`|
|`Date`|<span data-ttu-id="9c19b-253">12:00 AM 1 stycznia roku 1 (01/01/0001 12:00:00 AM)</span><span class="sxs-lookup"><span data-stu-id="9c19b-253">12:00 AM of January 1 of the year 1 (01/01/0001 12:00:00 AM)</span></span>|

<span data-ttu-id="9c19b-254">Każdy element struktury jest inicjowany tak, jakby była to odrębna zmienna.</span><span class="sxs-lookup"><span data-stu-id="9c19b-254">Each element of a structure is initialized as if it were a separate variable.</span></span> <span data-ttu-id="9c19b-255">Jeśli deklarujesz długość tablicy, ale nie zainicjujesz jej elementów, każdy element jest inicjowany tak, jakby był oddzielną zmienną.</span><span class="sxs-lookup"><span data-stu-id="9c19b-255">If you declare the length of an array but do not initialize its elements, each element is initialized as if it were a separate variable.</span></span>

## <a name="static-local-variable-lifetime"></a><span data-ttu-id="9c19b-256">Okres istnienia statycznej zmiennej lokalnej</span><span class="sxs-lookup"><span data-stu-id="9c19b-256">Static local variable lifetime</span></span>

<span data-ttu-id="9c19b-257">`Static` zmienna lokalna ma dłuższy okres istnienia niż procedura, w której jest zadeklarowana.</span><span class="sxs-lookup"><span data-stu-id="9c19b-257">A `Static` local variable has a longer lifetime than that of the procedure in which it is declared.</span></span> <span data-ttu-id="9c19b-258">Granice okresu istnienia zmiennej zależą od tego, gdzie procedura została zadeklarowana, oraz od tego, czy jest ona `Shared`.</span><span class="sxs-lookup"><span data-stu-id="9c19b-258">The boundaries of the variable's lifetime depend on where the procedure is declared and whether it is `Shared`.</span></span>

|<span data-ttu-id="9c19b-259">Deklaracja procedury</span><span class="sxs-lookup"><span data-stu-id="9c19b-259">Procedure declaration</span></span>|<span data-ttu-id="9c19b-260">Zmienna została zainicjowana</span><span class="sxs-lookup"><span data-stu-id="9c19b-260">Variable initialized</span></span>|<span data-ttu-id="9c19b-261">Zmienna przerywa istniejące</span><span class="sxs-lookup"><span data-stu-id="9c19b-261">Variable stops existing</span></span>|
|---|---|---|
|<span data-ttu-id="9c19b-262">W module</span><span class="sxs-lookup"><span data-stu-id="9c19b-262">In a module</span></span>|<span data-ttu-id="9c19b-263">Przy pierwszym wywołaniu procedury</span><span class="sxs-lookup"><span data-stu-id="9c19b-263">The first time the procedure is called</span></span>|<span data-ttu-id="9c19b-264">Gdy program zatrzyma wykonywanie</span><span class="sxs-lookup"><span data-stu-id="9c19b-264">When your program stops execution</span></span>|
|<span data-ttu-id="9c19b-265">W klasie lub strukturze, procedura jest `Shared`</span><span class="sxs-lookup"><span data-stu-id="9c19b-265">In a class or structure, procedure is `Shared`</span></span>|<span data-ttu-id="9c19b-266">Przy pierwszym wywołaniu procedury w konkretnym wystąpieniu lub w samej klasie lub strukturze</span><span class="sxs-lookup"><span data-stu-id="9c19b-266">The first time the procedure is called either on a specific instance or on the class or structure itself</span></span>|<span data-ttu-id="9c19b-267">Gdy program zatrzyma wykonywanie</span><span class="sxs-lookup"><span data-stu-id="9c19b-267">When your program stops execution</span></span>|
|<span data-ttu-id="9c19b-268">W klasie lub strukturze procedura nie jest `Shared`</span><span class="sxs-lookup"><span data-stu-id="9c19b-268">In a class or structure, procedure isn't `Shared`</span></span>|<span data-ttu-id="9c19b-269">Przy pierwszym wywołaniu procedury w określonym wystąpieniu</span><span class="sxs-lookup"><span data-stu-id="9c19b-269">The first time the procedure is called on a specific instance</span></span>|<span data-ttu-id="9c19b-270">Gdy wystąpienie zostanie wydane na potrzeby wyrzucania elementów bezużytecznych (GC)</span><span class="sxs-lookup"><span data-stu-id="9c19b-270">When the instance is released for garbage collection (GC)</span></span>|

## <a name="attributes-and-modifiers"></a><span data-ttu-id="9c19b-271">Atrybuty i Modyfikatory</span><span class="sxs-lookup"><span data-stu-id="9c19b-271">Attributes and modifiers</span></span>

<span data-ttu-id="9c19b-272">Atrybuty można stosować tylko do zmiennych składowych, nie do zmiennych lokalnych.</span><span class="sxs-lookup"><span data-stu-id="9c19b-272">You can apply attributes only to member variables, not to local variables.</span></span> <span data-ttu-id="9c19b-273">Atrybut zawiera informacje dotyczące metadanych zestawu, który nie ma znaczenia dla magazynu tymczasowego, takiego jak zmienne lokalne.</span><span class="sxs-lookup"><span data-stu-id="9c19b-273">An attribute contributes information to the assembly's metadata, which is not meaningful for temporary storage such as local variables.</span></span>

<span data-ttu-id="9c19b-274">Na poziomie modułu nie można użyć modyfikatora `Static`, aby zadeklarować zmienne składowe.</span><span class="sxs-lookup"><span data-stu-id="9c19b-274">At module level, you cannot use the `Static` modifier to declare member variables.</span></span> <span data-ttu-id="9c19b-275">Na poziomie procedury nie można używać `Shared`, `Shadows`, `ReadOnly`, `WithEvents`ani modyfikatorów dostępu do deklarowania zmiennych lokalnych.</span><span class="sxs-lookup"><span data-stu-id="9c19b-275">At procedure level, you cannot use `Shared`, `Shadows`, `ReadOnly`, `WithEvents`, or any access modifiers to declare local variables.</span></span>

<span data-ttu-id="9c19b-276">Możesz określić, jaki kod może uzyskać dostęp do zmiennej, dostarczając `accessmodifier`.</span><span class="sxs-lookup"><span data-stu-id="9c19b-276">You can specify what code can access a variable by supplying an `accessmodifier`.</span></span> <span data-ttu-id="9c19b-277">Zmienne składowe klasy i modułu (poza jakąkolwiek procedurą) domyślnie są dostępem prywatnym, a zmienne składowe struktury domyślnie mają dostęp publiczny.</span><span class="sxs-lookup"><span data-stu-id="9c19b-277">Class and module member variables (outside any procedure) default to private access, and structure member variables default to public access.</span></span> <span data-ttu-id="9c19b-278">Możesz dostosować ich poziom dostępu za pomocą modyfikatorów dostępu.</span><span class="sxs-lookup"><span data-stu-id="9c19b-278">You can adjust their access levels with the access modifiers.</span></span> <span data-ttu-id="9c19b-279">Nie można używać modyfikatorów dostępu dla zmiennych lokalnych (wewnątrz procedury).</span><span class="sxs-lookup"><span data-stu-id="9c19b-279">You cannot use access modifiers on local variables (inside a procedure).</span></span>

<span data-ttu-id="9c19b-280">Można określić `WithEvents` tylko w zmiennych składowych, a nie na zmiennych lokalnych wewnątrz procedury.</span><span class="sxs-lookup"><span data-stu-id="9c19b-280">You can specify `WithEvents` only on member variables, not on local variables inside a procedure.</span></span> <span data-ttu-id="9c19b-281">Jeśli określisz `WithEvents`, typem danych zmiennej musi być określony typ klasy, a nie `Object`.</span><span class="sxs-lookup"><span data-stu-id="9c19b-281">If you specify `WithEvents`, the data type of the variable must be a specific class type, not `Object`.</span></span> <span data-ttu-id="9c19b-282">Nie można zadeklarować tablicy przy użyciu `WithEvents`.</span><span class="sxs-lookup"><span data-stu-id="9c19b-282">You cannot declare an array with `WithEvents`.</span></span> <span data-ttu-id="9c19b-283">Aby uzyskać więcej informacji na temat zdarzeń, zobacz [zdarzenia](../../programming-guide/language-features/events/index.md).</span><span class="sxs-lookup"><span data-stu-id="9c19b-283">For more information about events, see [Events](../../programming-guide/language-features/events/index.md).</span></span>

> [!NOTE]
> <span data-ttu-id="9c19b-284">Kod poza klasą, strukturą lub modułem musi kwalifikować nazwę zmiennej składowej o nazwie tej klasy, struktury lub modułu.</span><span class="sxs-lookup"><span data-stu-id="9c19b-284">Code outside a class, structure, or module must qualify a member variable's name with the name of that class, structure, or module.</span></span> <span data-ttu-id="9c19b-285">Kod poza procedurą lub blok nie może odwoływać się do żadnych zmiennych lokalnych w ramach tej procedury lub bloku.</span><span class="sxs-lookup"><span data-stu-id="9c19b-285">Code outside a procedure or block cannot refer to any local variables within that procedure or block.</span></span>

## <a name="releasing-managed-resources"></a><span data-ttu-id="9c19b-286">Zwalnianie zasobów zarządzanych</span><span class="sxs-lookup"><span data-stu-id="9c19b-286">Releasing managed resources</span></span>

<span data-ttu-id="9c19b-287">.NET Framework Moduł wyrzucania elementów bezużytecznych usuwa zarządzane zasoby bez żadnego dodatkowego kodowania w Twojej części.</span><span class="sxs-lookup"><span data-stu-id="9c19b-287">The .NET Framework garbage collector disposes of managed resources without any extra coding on your part.</span></span> <span data-ttu-id="9c19b-288">Można jednak wymusić usunięcie zarządzanego zasobu, zamiast czekać na Moduł wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="9c19b-288">However, you can force the disposal of a managed resource instead of waiting for the garbage collector.</span></span>

<span data-ttu-id="9c19b-289">Jeśli klasa jest zastosowana do szczególnie cennych i niedozwolonych zasobów (takich jak połączenie z bazą danych lub dojście do pliku), możesz nie czekać, aż następne odzyskiwanie pamięci zostanie oczyszczone wystąpienie klasy, które nie jest już używane.</span><span class="sxs-lookup"><span data-stu-id="9c19b-289">If a class holds onto a particularly valuable and scarce resource (such as a database connection or file handle), you might not want to wait until the next garbage collection to clean up a class instance that's no longer in use.</span></span> <span data-ttu-id="9c19b-290">Klasa może zaimplementować interfejs <xref:System.IDisposable>, aby zapewnić możliwość zwolnienia zasobów przed wyrzucaniem elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="9c19b-290">A class may implement the <xref:System.IDisposable> interface to provide a way to release resources before a garbage collection.</span></span> <span data-ttu-id="9c19b-291">Klasa implementująca ten interfejs uwidacznia metodę `Dispose`, która może zostać wywołana, aby wymusić natychmiastowe wydanie cennych zasobów.</span><span class="sxs-lookup"><span data-stu-id="9c19b-291">A class that implements that interface exposes a `Dispose` method that can be called to force valuable resources to be released immediately.</span></span>

<span data-ttu-id="9c19b-292">Instrukcja `Using` automatyzuje proces pozyskiwania zasobu, wykonywania zestawu instrukcji, a następnie usuwania zasobu.</span><span class="sxs-lookup"><span data-stu-id="9c19b-292">The `Using` statement automates the process of acquiring a resource, executing a set of statements, and then disposing of the resource.</span></span> <span data-ttu-id="9c19b-293">Jednak zasób musi implementować interfejs <xref:System.IDisposable>.</span><span class="sxs-lookup"><span data-stu-id="9c19b-293">However, the resource must implement the <xref:System.IDisposable> interface.</span></span> <span data-ttu-id="9c19b-294">Aby uzyskać więcej informacji, zobacz [using instrukcji](using-statement.md).</span><span class="sxs-lookup"><span data-stu-id="9c19b-294">For more information, see [Using Statement](using-statement.md).</span></span>

## <a name="example"></a><span data-ttu-id="9c19b-295">Przykład</span><span class="sxs-lookup"><span data-stu-id="9c19b-295">Example</span></span>

<span data-ttu-id="9c19b-296">Poniższy przykład deklaruje zmienne przy użyciu instrukcji `Dim` z różnymi opcjami.</span><span class="sxs-lookup"><span data-stu-id="9c19b-296">The following example declares variables by using the `Dim` statement with various options.</span></span>

[!code-vb[VbVbalrStatements#141](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class11.vb#141)]

## <a name="example"></a><span data-ttu-id="9c19b-297">Przykład</span><span class="sxs-lookup"><span data-stu-id="9c19b-297">Example</span></span>

<span data-ttu-id="9c19b-298">Poniższy przykład zawiera listę numerów pierwszych z zakresu od 1 do 30.</span><span class="sxs-lookup"><span data-stu-id="9c19b-298">The following example lists the prime numbers between 1 and 30.</span></span> <span data-ttu-id="9c19b-299">Zakres zmiennych lokalnych został opisany w komentarzach do kodu.</span><span class="sxs-lookup"><span data-stu-id="9c19b-299">The scope of local variables is described in code comments.</span></span>

[!code-vb[VbVbalrStatements#142](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class11.vb#142)]

## <a name="example"></a><span data-ttu-id="9c19b-300">Przykład</span><span class="sxs-lookup"><span data-stu-id="9c19b-300">Example</span></span>

<span data-ttu-id="9c19b-301">W poniższym przykładzie zmienna `speedValue` jest zadeklarowana na poziomie klasy.</span><span class="sxs-lookup"><span data-stu-id="9c19b-301">In the following example, the `speedValue` variable is declared at the class level.</span></span> <span data-ttu-id="9c19b-302">Słowo kluczowe `Private` jest używane do deklarowania zmiennej.</span><span class="sxs-lookup"><span data-stu-id="9c19b-302">The `Private` keyword is used to declare the variable.</span></span> <span data-ttu-id="9c19b-303">Do zmiennej można uzyskać dostęp za pomocą procedury w klasie `Car`.</span><span class="sxs-lookup"><span data-stu-id="9c19b-303">The variable can be accessed by any procedure in the `Car` class.</span></span>

[!code-vb[VbVbalrStatements#144](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class11.vb#144)]

[!code-vb[VbVbalrStatements#145](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class11.vb#145)]

## <a name="see-also"></a><span data-ttu-id="9c19b-304">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9c19b-304">See also</span></span>

- [<span data-ttu-id="9c19b-305">Const, instrukcja</span><span class="sxs-lookup"><span data-stu-id="9c19b-305">Const Statement</span></span>](const-statement.md)
- [<span data-ttu-id="9c19b-306">ReDim, instrukcja</span><span class="sxs-lookup"><span data-stu-id="9c19b-306">ReDim Statement</span></span>](redim-statement.md)
- [<span data-ttu-id="9c19b-307">Option Explicit, instrukcja</span><span class="sxs-lookup"><span data-stu-id="9c19b-307">Option Explicit Statement</span></span>](option-explicit-statement.md)
- [<span data-ttu-id="9c19b-308">Option Infer, instrukcja</span><span class="sxs-lookup"><span data-stu-id="9c19b-308">Option Infer Statement</span></span>](option-infer-statement.md)
- [<span data-ttu-id="9c19b-309">Option Strict, instrukcja</span><span class="sxs-lookup"><span data-stu-id="9c19b-309">Option Strict Statement</span></span>](option-strict-statement.md)
- [<span data-ttu-id="9c19b-310">Strona kompilowania, Projektant projektu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9c19b-310">Compile Page, Project Designer (Visual Basic)</span></span>](/visualstudio/ide/reference/compile-page-project-designer-visual-basic)
- [<span data-ttu-id="9c19b-311">Deklaracja zmiennej</span><span class="sxs-lookup"><span data-stu-id="9c19b-311">Variable Declaration</span></span>](../../programming-guide/language-features/variables/variable-declaration.md)
- [<span data-ttu-id="9c19b-312">Tablice</span><span class="sxs-lookup"><span data-stu-id="9c19b-312">Arrays</span></span>](../../programming-guide/language-features/arrays/index.md)
- [<span data-ttu-id="9c19b-313">Inicjatory obiektów: typy nazwane i anonimowe</span><span class="sxs-lookup"><span data-stu-id="9c19b-313">Object Initializers: Named and Anonymous Types</span></span>](../../programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)
- [<span data-ttu-id="9c19b-314">Typy anonimowe</span><span class="sxs-lookup"><span data-stu-id="9c19b-314">Anonymous Types</span></span>](../../programming-guide/language-features/objects-and-classes/anonymous-types.md)
- [<span data-ttu-id="9c19b-315">Inicjatory obiektów: typy nazwane i anonimowe</span><span class="sxs-lookup"><span data-stu-id="9c19b-315">Object Initializers: Named and Anonymous Types</span></span>](../../programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)
- [<span data-ttu-id="9c19b-316">Instrukcje: deklarowanie obiektu za pomocą inicjatora obiektów</span><span class="sxs-lookup"><span data-stu-id="9c19b-316">How to: Declare an Object by Using an Object Initializer</span></span>](../../programming-guide/language-features/objects-and-classes/how-to-declare-an-object-by-using-an-object-initializer.md)
- [<span data-ttu-id="9c19b-317">Wnioskowanie o typie lokalnym</span><span class="sxs-lookup"><span data-stu-id="9c19b-317">Local Type Inference</span></span>](../../programming-guide/language-features/variables/local-type-inference.md)
