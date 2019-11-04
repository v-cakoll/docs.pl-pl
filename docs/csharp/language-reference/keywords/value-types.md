---
title: Typy wartości — C# odwołanie
ms.custom: seodec18
ms.date: 11/26/2018
f1_keywords:
- cs.valuetypes
helpviewer_keywords:
- value types [C#]
- types [C#], value types
- C# language, value types
ms.assetid: 471eb994-2958-49d5-a6be-19b4313f80a3
ms.openlocfilehash: 940d21bdd90d4594a39edc20283ca6a45ccf81fe
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/01/2019
ms.locfileid: "73422202"
---
# <a name="value-types-c-reference"></a><span data-ttu-id="13507-102">Typy wartości (C# odwołanie)</span><span class="sxs-lookup"><span data-stu-id="13507-102">Value types (C# Reference)</span></span>

<span data-ttu-id="13507-103">Istnieją dwa rodzaje typów wartości:</span><span class="sxs-lookup"><span data-stu-id="13507-103">There are two kinds of value types:</span></span>

- [<span data-ttu-id="13507-104">Struktury</span><span class="sxs-lookup"><span data-stu-id="13507-104">Structs</span></span>](struct.md)

- [<span data-ttu-id="13507-105">Wyliczenia</span><span class="sxs-lookup"><span data-stu-id="13507-105">Enumerations</span></span>](enum.md)

## <a name="main-features-of-value-types"></a><span data-ttu-id="13507-106">Główne funkcje typów wartości</span><span class="sxs-lookup"><span data-stu-id="13507-106">Main features of value types</span></span>

<span data-ttu-id="13507-107">Zmienna typu wartości zawiera wartość typu.</span><span class="sxs-lookup"><span data-stu-id="13507-107">A variable of a value type contains a value of the type.</span></span> <span data-ttu-id="13507-108">Na przykład zmienna typu `int` może zawierać wartość `42`.</span><span class="sxs-lookup"><span data-stu-id="13507-108">For example, a variable of the `int` type might contain the value `42`.</span></span> <span data-ttu-id="13507-109">Różni się to od zmiennej typu referencyjnego, która zawiera odwołanie do wystąpienia typu, znanego również jako obiekt.</span><span class="sxs-lookup"><span data-stu-id="13507-109">This differs from a variable of a reference type, which contains a reference to an instance of the type, also known as an object.</span></span> <span data-ttu-id="13507-110">Gdy przypiszesz nową wartość do zmiennej typu wartości, ta wartość jest kopiowana.</span><span class="sxs-lookup"><span data-stu-id="13507-110">When you assign a new value to a variable of a value type, that value is copied.</span></span> <span data-ttu-id="13507-111">Gdy przypiszesz nową wartość do zmiennej typu referencyjnego, odwołanie jest kopiowane, a nie samego obiektu.</span><span class="sxs-lookup"><span data-stu-id="13507-111">When you assign a new value to a variable of a reference type, the reference is copied, not the object itself.</span></span>

<span data-ttu-id="13507-112">Wszystkie typy wartości są wyprowadzane niejawnie z <xref:System.ValueType?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="13507-112">All value types are derived implicitly from the <xref:System.ValueType?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="13507-113">W przeciwieństwie do typów referencyjnych nie można utworzyć nowego typu z typu wartości.</span><span class="sxs-lookup"><span data-stu-id="13507-113">Unlike with reference types, you cannot derive a new type from a value type.</span></span> <span data-ttu-id="13507-114">Jednak takie jak typy odwołań, struktury mogą implementować interfejsy.</span><span class="sxs-lookup"><span data-stu-id="13507-114">However, like reference types, structs can implement interfaces.</span></span>

<span data-ttu-id="13507-115">Zmienne typu wartości domyślnie nie mogą być `null`.</span><span class="sxs-lookup"><span data-stu-id="13507-115">Value type variables cannot be `null` by default.</span></span> <span data-ttu-id="13507-116">Jednak zmienne odpowiednich [typów wartości dopuszczających wartość null](../../programming-guide/nullable-types/index.md) mogą być `null`.</span><span class="sxs-lookup"><span data-stu-id="13507-116">However, variables of the corresponding [nullable value types](../../programming-guide/nullable-types/index.md) can be `null`.</span></span>

<span data-ttu-id="13507-117">Każdy typ wartości ma niejawny Konstruktor bez parametrów, który inicjuje wartość domyślną tego typu.</span><span class="sxs-lookup"><span data-stu-id="13507-117">Each value type has an implicit parameterless constructor that initializes the default value of that type.</span></span> <span data-ttu-id="13507-118">Aby uzyskać informacje o domyślnych wartościach typów wartości, zobacz [tabela wartości domyślnych](default-values-table.md).</span><span class="sxs-lookup"><span data-stu-id="13507-118">For information about default values of value types, see [Default values table](default-values-table.md).</span></span>

## <a name="simple-types"></a><span data-ttu-id="13507-119">Typy proste</span><span class="sxs-lookup"><span data-stu-id="13507-119">Simple types</span></span>

<span data-ttu-id="13507-120">*Typy proste* są zestawem wstępnie zdefiniowanych typów struktur udostępnianych przez C# i składają się z następujących typów:</span><span class="sxs-lookup"><span data-stu-id="13507-120">The *simple types* are a set of predefined struct types provided by C# and comprise the following types:</span></span>

- <span data-ttu-id="13507-121">[Typy całkowite](../builtin-types/integral-numeric-types.md): typy liczbowe liczb całkowitych i typ [char](char.md)</span><span class="sxs-lookup"><span data-stu-id="13507-121">[Integral types](../builtin-types/integral-numeric-types.md): integer numeric types and the [char](char.md) type</span></span>
- [<span data-ttu-id="13507-122">Typy zmiennoprzecinkowe</span><span class="sxs-lookup"><span data-stu-id="13507-122">Floating-point types</span></span>](../builtin-types/floating-point-numeric-types.md)
- [<span data-ttu-id="13507-123">bool</span><span class="sxs-lookup"><span data-stu-id="13507-123">bool</span></span>](bool.md)

<span data-ttu-id="13507-124">Typy proste są identyfikowane za pomocą słów kluczowych, ale te słowa kluczowe są po prostu aliasami dla wstępnie zdefiniowanych typów struktur w przestrzeni nazw <xref:System>.</span><span class="sxs-lookup"><span data-stu-id="13507-124">The simple types are identified through keywords, but these keywords are simply aliases for predefined struct types in the <xref:System> namespace.</span></span> <span data-ttu-id="13507-125">Na przykład [int](../builtin-types/integral-numeric-types.md) jest aliasem <xref:System.Int32?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="13507-125">For example, [int](../builtin-types/integral-numeric-types.md) is an alias of <xref:System.Int32?displayProperty=nameWithType>.</span></span> <span data-ttu-id="13507-126">Aby uzyskać pełną listę aliasów, zobacz [Tabela typów wbudowanych](built-in-types-table.md).</span><span class="sxs-lookup"><span data-stu-id="13507-126">For a complete list of aliases, see [Built-in types table](built-in-types-table.md).</span></span>

<span data-ttu-id="13507-127">Proste typy różnią się od innych typów struktur w tym, że dopuszczają pewne dodatkowe operacje:</span><span class="sxs-lookup"><span data-stu-id="13507-127">The simple types differ from other struct types in that they permit certain additional operations:</span></span>

- <span data-ttu-id="13507-128">Typy proste można inicjować przy użyciu literałów.</span><span class="sxs-lookup"><span data-stu-id="13507-128">Simple types can be initialized by using literals.</span></span> <span data-ttu-id="13507-129">Na przykład `'A'` jest literałem typu `char`, a `2001` jest literałem typu `int`.</span><span class="sxs-lookup"><span data-stu-id="13507-129">For example, `'A'` is a literal of the type `char` and `2001` is a literal of the type `int`.</span></span>

- <span data-ttu-id="13507-130">Stałe typów prostych można zadeklarować za pomocą słowa kluczowego [const](const.md) .</span><span class="sxs-lookup"><span data-stu-id="13507-130">You can declare constants of the simple types with the [const](const.md) keyword.</span></span> <span data-ttu-id="13507-131">Nie jest możliwe posiadanie stałych z innych typów struktur.</span><span class="sxs-lookup"><span data-stu-id="13507-131">It's not possible to have constants of other struct types.</span></span>

- <span data-ttu-id="13507-132">Wyrażenia stałe, których operandy to wszystkie proste typy stałe, są oceniane w czasie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="13507-132">Constant expressions, whose operands are all simple type constants, are evaluated at compile time.</span></span>

<span data-ttu-id="13507-133">Aby uzyskać więcej informacji, zobacz sekcję [typy proste](~/_csharplang/spec/types.md#simple-types) [ C# specyfikacji języka](/dotnet/csharp/language-reference/language-specification/introduction).</span><span class="sxs-lookup"><span data-stu-id="13507-133">For more information, see the [Simple types](~/_csharplang/spec/types.md#simple-types) section of the [C# language specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span>

## <a name="initializing-value-types"></a><span data-ttu-id="13507-134">Inicjowanie typów wartości</span><span class="sxs-lookup"><span data-stu-id="13507-134">Initializing value types</span></span>

<span data-ttu-id="13507-135">Zmienne lokalne w C# programie muszą zostać zainicjowane przed ich użyciem.</span><span class="sxs-lookup"><span data-stu-id="13507-135">Local variables in C# must be initialized before they are used.</span></span> <span data-ttu-id="13507-136">Na przykład można zadeklarować zmienną lokalną bez inicjalizacji, jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="13507-136">For example, you might declare a local variable without initialization as in the following example:</span></span>

```csharp
int myInt;
```

<span data-ttu-id="13507-137">Nie można jej użyć przed zainicjowaniem.</span><span class="sxs-lookup"><span data-stu-id="13507-137">You cannot use it before you initialize it.</span></span> <span data-ttu-id="13507-138">Można go zainicjować przy użyciu następującej instrukcji:</span><span class="sxs-lookup"><span data-stu-id="13507-138">You can initialize it using the following statement:</span></span>

```csharp
myInt = new int();  // Invoke parameterless constructor for int type.
```

<span data-ttu-id="13507-139">Ta instrukcja jest równoznaczna z następującą instrukcją:</span><span class="sxs-lookup"><span data-stu-id="13507-139">This statement is equivalent to the following statement:</span></span>

```csharp
myInt = 0;         // Assign an initial value, 0 in this example.
```

<span data-ttu-id="13507-140">Można oczywiście mieć deklarację i inicjalizację w tej samej instrukcji, jak w następujących przykładach:</span><span class="sxs-lookup"><span data-stu-id="13507-140">You can, of course, have the declaration and the initialization in the same statement as in the following examples:</span></span>

```csharp
int myInt = new int();
```

<span data-ttu-id="13507-141">oraz</span><span class="sxs-lookup"><span data-stu-id="13507-141">–or–</span></span>

```csharp
int myInt = 0;
```

<span data-ttu-id="13507-142">Użycie operatora [New](../operators/new-operator.md) wywołuje konstruktora bez parametrów określonego typu i przypisuje wartość domyślną zmiennej.</span><span class="sxs-lookup"><span data-stu-id="13507-142">Using the [new](../operators/new-operator.md) operator calls the parameterless constructor of the specific type and assigns the default value to the variable.</span></span> <span data-ttu-id="13507-143">W poprzednim przykładzie Konstruktor bez parametrów przypisał wartość `0`, aby `myInt`.</span><span class="sxs-lookup"><span data-stu-id="13507-143">In the preceding example, the parameterless constructor assigned the value `0` to `myInt`.</span></span> <span data-ttu-id="13507-144">Aby uzyskać więcej informacji na temat wartości przypisanych przez wywoływanie konstruktorów bez parametrów, zobacz [tabela wartości domyślnych](default-values-table.md).</span><span class="sxs-lookup"><span data-stu-id="13507-144">For more information about values assigned by calling parameterless constructors, see [Default values table](default-values-table.md).</span></span>

<span data-ttu-id="13507-145">W przypadku typów zdefiniowanych przez użytkownika Użyj metody [New](../operators/new-operator.md) , aby wywołać Konstruktor bez parametrów.</span><span class="sxs-lookup"><span data-stu-id="13507-145">With user-defined types, use [new](../operators/new-operator.md) to invoke the parameterless constructor.</span></span> <span data-ttu-id="13507-146">Na przykład poniższa instrukcja wywołuje konstruktora bez parametrów `Point` struct:</span><span class="sxs-lookup"><span data-stu-id="13507-146">For example, the following statement invokes the parameterless constructor of the `Point` struct:</span></span>

```csharp
var p = new Point(); // Invoke parameterless constructor for the struct.
```

<span data-ttu-id="13507-147">Po tym wywołaniu struktura jest uznawana za ostatecznie przypisaną; oznacza to, że wszystkie jego elementy członkowskie są inicjowane do ich wartości domyślnych.</span><span class="sxs-lookup"><span data-stu-id="13507-147">After this call, the struct is considered to be definitely assigned; that is, all its members are initialized to their default values.</span></span>

<span data-ttu-id="13507-148">Aby uzyskać więcej informacji na temat operatora `new`, zobacz [New](../operators/new-operator.md).</span><span class="sxs-lookup"><span data-stu-id="13507-148">For more information about the `new` operator, see [new](../operators/new-operator.md).</span></span>

<span data-ttu-id="13507-149">Informacje o formatowaniu danych wyjściowych typów liczbowych znajdują się w temacie [formatowanie tabeli wyników liczbowych](formatting-numeric-results-table.md).</span><span class="sxs-lookup"><span data-stu-id="13507-149">For information about formatting the output of numeric types, see [Formatting numeric results table](formatting-numeric-results-table.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="13507-150">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="13507-150">See also</span></span>

- [<span data-ttu-id="13507-151">C#Odwoła</span><span class="sxs-lookup"><span data-stu-id="13507-151">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="13507-152">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="13507-152">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="13507-153">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="13507-153">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="13507-154">Typy</span><span class="sxs-lookup"><span data-stu-id="13507-154">Types</span></span>](/dotnet/csharp/language-reference/keywords)
- [<span data-ttu-id="13507-155">Typy odwołań</span><span class="sxs-lookup"><span data-stu-id="13507-155">Reference types</span></span>](reference-types.md)
- [<span data-ttu-id="13507-156">Typy wartości null</span><span class="sxs-lookup"><span data-stu-id="13507-156">Nullable value types</span></span>](../../programming-guide/nullable-types/index.md)
