---
title: Typy — wartości C# odwołania
ms.custom: seodec18
ms.date: 11/26/2018
f1_keywords:
- cs.valuetypes
helpviewer_keywords:
- value types [C#]
- types [C#], value types
- C# language, value types
ms.assetid: 471eb994-2958-49d5-a6be-19b4313f80a3
ms.openlocfilehash: 9907811a43f408020e2ee76621d4975a53945570
ms.sourcegitcommit: 9b1ac36b6c80176fd4e20eb5bfcbd9d56c3264cf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/28/2019
ms.locfileid: "67424030"
---
# <a name="value-types-c-reference"></a><span data-ttu-id="d646f-102">Typy wartości (C# odwołania)</span><span class="sxs-lookup"><span data-stu-id="d646f-102">Value types (C# Reference)</span></span>

<span data-ttu-id="d646f-103">Istnieją dwa rodzaje typów wartości:</span><span class="sxs-lookup"><span data-stu-id="d646f-103">There are two kinds of value types:</span></span>

- [<span data-ttu-id="d646f-104">Struktury</span><span class="sxs-lookup"><span data-stu-id="d646f-104">Structs</span></span>](struct.md)

- [<span data-ttu-id="d646f-105">Wyliczenia</span><span class="sxs-lookup"><span data-stu-id="d646f-105">Enumerations</span></span>](enum.md)

## <a name="main-features-of-value-types"></a><span data-ttu-id="d646f-106">Główne funkcje typów wartości</span><span class="sxs-lookup"><span data-stu-id="d646f-106">Main features of value types</span></span>

<span data-ttu-id="d646f-107">Zmienna typu wartości zawiera wartość typu.</span><span class="sxs-lookup"><span data-stu-id="d646f-107">A variable of a value type contains a value of the type.</span></span> <span data-ttu-id="d646f-108">Na przykład zmiennej `int` typ może zawierać wartość `42`.</span><span class="sxs-lookup"><span data-stu-id="d646f-108">For example, a variable of the `int` type might contain the value `42`.</span></span> <span data-ttu-id="d646f-109">To różni się od zmiennej typu odwołania, który zawiera odwołanie do wystąpienia typu, znany także jako obiekt.</span><span class="sxs-lookup"><span data-stu-id="d646f-109">This differs from a variable of a reference type, which contains a reference to an instance of the type, also known as an object.</span></span> <span data-ttu-id="d646f-110">Po przypisaniu nową wartość do zmiennej typu wartości jest kopiowana.</span><span class="sxs-lookup"><span data-stu-id="d646f-110">When you assign a new value to a variable of a value type, that value is copied.</span></span> <span data-ttu-id="d646f-111">Po przypisaniu nową wartość do zmiennej typu odwołania odwołanie jest kopiowane, nie samego obiektu.</span><span class="sxs-lookup"><span data-stu-id="d646f-111">When you assign a new value to a variable of a reference type, the reference is copied, not the object itself.</span></span>

<span data-ttu-id="d646f-112">Wszystkie typy wartości niejawnie pochodzą od <xref:System.ValueType?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="d646f-112">All value types are derived implicitly from the <xref:System.ValueType?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="d646f-113">Inaczej niż w przypadku typów referencyjnych nie może pochodzić nowy typ z typem wartości.</span><span class="sxs-lookup"><span data-stu-id="d646f-113">Unlike with reference types, you cannot derive a new type from a value type.</span></span> <span data-ttu-id="d646f-114">Jednakże, takie jak typy odwołań struktury mogą implementować interfejsów.</span><span class="sxs-lookup"><span data-stu-id="d646f-114">However, like reference types, structs can implement interfaces.</span></span>

<span data-ttu-id="d646f-115">Zmienne typu wartości nie może być `null` domyślnie.</span><span class="sxs-lookup"><span data-stu-id="d646f-115">Value type variables cannot be `null` by default.</span></span> <span data-ttu-id="d646f-116">Jednakże zmienne odpowiadającego [typów dopuszczających wartości zerowe](../../../csharp/programming-guide/nullable-types/index.md) może być `null`.</span><span class="sxs-lookup"><span data-stu-id="d646f-116">However, variables of the corresponding [nullable types](../../../csharp/programming-guide/nullable-types/index.md) can be `null`.</span></span>

<span data-ttu-id="d646f-117">Każdy typ wartości ma niejawnego konstruktora bez parametrów, która inicjuje wartością domyślną tego typu.</span><span class="sxs-lookup"><span data-stu-id="d646f-117">Each value type has an implicit parameterless constructor that initializes the default value of that type.</span></span> <span data-ttu-id="d646f-118">Aby uzyskać informacje o wartościach domyślnych typów wartości, zobacz [tabela wartości domyślnych](default-values-table.md).</span><span class="sxs-lookup"><span data-stu-id="d646f-118">For information about default values of value types, see [Default values table](default-values-table.md).</span></span>

## <a name="simple-types"></a><span data-ttu-id="d646f-119">Typy proste</span><span class="sxs-lookup"><span data-stu-id="d646f-119">Simple types</span></span>

<span data-ttu-id="d646f-120">*Typów prostych* zestaw wstępnie zdefiniowanych struktura typów dostarczonych przez C# i składają się następujące typy:</span><span class="sxs-lookup"><span data-stu-id="d646f-120">The *simple types* are a set of predefined struct types provided by C# and comprise the following types:</span></span>

- <span data-ttu-id="d646f-121">[Typy całkowite](../builtin-types/integral-numeric-types.md): liczbowych typów całkowitych i [char](char.md) typu</span><span class="sxs-lookup"><span data-stu-id="d646f-121">[Integral types](../builtin-types/integral-numeric-types.md): integer numeric types and the [char](char.md) type</span></span>
- [<span data-ttu-id="d646f-122">Typy zmiennoprzecinkowe</span><span class="sxs-lookup"><span data-stu-id="d646f-122">Floating-point types</span></span>](floating-point-types-table.md)
- [<span data-ttu-id="d646f-123">bool</span><span class="sxs-lookup"><span data-stu-id="d646f-123">bool</span></span>](bool.md)

<span data-ttu-id="d646f-124">Proste typy są identyfikowane za pomocą słów kluczowych, ale te słowa kluczowe są po prostu aliasami dla struktury wstępnie zdefiniowanych typów w pakietach <xref:System> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="d646f-124">The simple types are identified through keywords, but these keywords are simply aliases for predefined struct types in the <xref:System> namespace.</span></span> <span data-ttu-id="d646f-125">Na przykład [int](../builtin-types/integral-numeric-types.md) jest aliasem <xref:System.Int32?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="d646f-125">For example, [int](../builtin-types/integral-numeric-types.md) is an alias of <xref:System.Int32?displayProperty=nameWithType>.</span></span> <span data-ttu-id="d646f-126">Aby uzyskać pełną listę aliasów, zobacz [Tabela typów wbudowanych](built-in-types-table.md).</span><span class="sxs-lookup"><span data-stu-id="d646f-126">For a complete list of aliases, see [Built-in types table](built-in-types-table.md).</span></span>

<span data-ttu-id="d646f-127">Proste typy różnią się od innych typów struktury w sposób, aby umożliwić pewne dodatkowe operacje:</span><span class="sxs-lookup"><span data-stu-id="d646f-127">The simple types differ from other struct types in that they permit certain additional operations:</span></span>

- <span data-ttu-id="d646f-128">Proste typy mogą być inicjowane za pomocą literałów ciągów.</span><span class="sxs-lookup"><span data-stu-id="d646f-128">Simple types can be initialized by using literals.</span></span> <span data-ttu-id="d646f-129">Na przykład `'A'` jest literał o typie `char` i `2001` jest literał o typie `int`.</span><span class="sxs-lookup"><span data-stu-id="d646f-129">For example, `'A'` is a literal of the type `char` and `2001` is a literal of the type `int`.</span></span>

- <span data-ttu-id="d646f-130">Można zadeklarować stałe proste typy z [const](const.md) — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="d646f-130">You can declare constants of the simple types with the [const](const.md) keyword.</span></span> <span data-ttu-id="d646f-131">Nie jest możliwe stałe inne typy struktury.</span><span class="sxs-lookup"><span data-stu-id="d646f-131">It's not possible to have constants of other struct types.</span></span>

- <span data-ttu-id="d646f-132">Wyrażenia stałe, w której argumenty operacji są stałymi typu prostego, są oceniane w czasie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="d646f-132">Constant expressions, whose operands are all simple type constants, are evaluated at compile time.</span></span>

<span data-ttu-id="d646f-133">Aby uzyskać więcej informacji, zobacz [typów prostych](~/_csharplang/spec/types.md#simple-types) części [ C# specyfikacji języka](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="d646f-133">For more information, see the [Simple types](~/_csharplang/spec/types.md#simple-types) section of the [C# language specification](../language-specification/index.md).</span></span>

## <a name="initializing-value-types"></a><span data-ttu-id="d646f-134">Inicjowanie typów wartości</span><span class="sxs-lookup"><span data-stu-id="d646f-134">Initializing value types</span></span>

<span data-ttu-id="d646f-135">Zmienne lokalne w języku C# muszą zostać zainicjowane, przed są one używane.</span><span class="sxs-lookup"><span data-stu-id="d646f-135">Local variables in C# must be initialized before they are used.</span></span> <span data-ttu-id="d646f-136">Na przykład może zadeklarować zmienną lokalną bez inicjowania, jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="d646f-136">For example, you might declare a local variable without initialization as in the following example:</span></span>

```csharp
int myInt;
```

<span data-ttu-id="d646f-137">Nie można użyć go, przed jej inicjalizację.</span><span class="sxs-lookup"><span data-stu-id="d646f-137">You cannot use it before you initialize it.</span></span> <span data-ttu-id="d646f-138">Można zainicjować za pomocą następującej instrukcji:</span><span class="sxs-lookup"><span data-stu-id="d646f-138">You can initialize it using the following statement:</span></span>

```csharp
myInt = new int();  // Invoke parameterless constructor for int type.
```

<span data-ttu-id="d646f-139">Ta instrukcja jest równoważna następującej instrukcji:</span><span class="sxs-lookup"><span data-stu-id="d646f-139">This statement is equivalent to the following statement:</span></span>

```csharp
myInt = 0;         // Assign an initial value, 0 in this example.
```

<span data-ttu-id="d646f-140">Można oczywiście masz deklaracji i inicjowania w tej samej instrukcji, co pokazano w następujących przykładach:</span><span class="sxs-lookup"><span data-stu-id="d646f-140">You can, of course, have the declaration and the initialization in the same statement as in the following examples:</span></span>

```csharp
int myInt = new int();
```

<span data-ttu-id="d646f-141">— lub —</span><span class="sxs-lookup"><span data-stu-id="d646f-141">–or–</span></span>

```csharp
int myInt = 0;
```

<span data-ttu-id="d646f-142">Za pomocą [nowe](../operators/new-operator.md) operator wywołuje konstruktora bez parametrów od określonego typu i przypisuje wartość domyślną do zmiennej.</span><span class="sxs-lookup"><span data-stu-id="d646f-142">Using the [new](../operators/new-operator.md) operator calls the parameterless constructor of the specific type and assigns the default value to the variable.</span></span> <span data-ttu-id="d646f-143">W powyższym przykładzie konstruktora bez parametrów przypisaną wartość `0` do `myInt`.</span><span class="sxs-lookup"><span data-stu-id="d646f-143">In the preceding example, the parameterless constructor assigned the value `0` to `myInt`.</span></span> <span data-ttu-id="d646f-144">Aby uzyskać więcej informacji na temat wartości przypisane przez wywołanie metody konstruktory domyślne zobacz [tabela wartości domyślnych](default-values-table.md).</span><span class="sxs-lookup"><span data-stu-id="d646f-144">For more information about values assigned by calling default constructors, see [Default values table](default-values-table.md).</span></span>

<span data-ttu-id="d646f-145">W przypadku typów zdefiniowanych przez użytkownika, należy użyć [nowe](../operators/new-operator.md) do wywołania konstruktora bez parametrów.</span><span class="sxs-lookup"><span data-stu-id="d646f-145">With user-defined types, use [new](../operators/new-operator.md) to invoke the parameterless constructor.</span></span> <span data-ttu-id="d646f-146">Na przykład następująca instrukcja wywołuje konstruktora bez parametrów z `Point` struktury:</span><span class="sxs-lookup"><span data-stu-id="d646f-146">For example, the following statement invokes the parameterless constructor of the `Point` struct:</span></span>

```csharp
Point p = new Point(); // Invoke parameterless constructor for the struct.
```

<span data-ttu-id="d646f-147">Po tym wywołaniu struktury uznaje się być zdecydowanie przypisywany; oznacza to, że wszystkie jego elementy członkowskie są inicjowane do wartości domyślnych.</span><span class="sxs-lookup"><span data-stu-id="d646f-147">After this call, the struct is considered to be definitely assigned; that is, all its members are initialized to their default values.</span></span>

<span data-ttu-id="d646f-148">Aby uzyskać więcej informacji na temat `new` operatora, zobacz [nowe](../operators/new-operator.md).</span><span class="sxs-lookup"><span data-stu-id="d646f-148">For more information about the `new` operator, see [new](../operators/new-operator.md).</span></span>

<span data-ttu-id="d646f-149">Aby dowiedzieć się, jak formatowanie danych wyjściowych typów liczbowych, zobacz [formatowanie tabeli wyników liczbowych](formatting-numeric-results-table.md).</span><span class="sxs-lookup"><span data-stu-id="d646f-149">For information about formatting the output of numeric types, see [Formatting numeric results table](formatting-numeric-results-table.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="d646f-150">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d646f-150">See also</span></span>

- [<span data-ttu-id="d646f-151">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="d646f-151">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="d646f-152">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="d646f-152">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="d646f-153">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="d646f-153">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="d646f-154">Typy</span><span class="sxs-lookup"><span data-stu-id="d646f-154">Types</span></span>](types.md)
- [<span data-ttu-id="d646f-155">Typy odwołań</span><span class="sxs-lookup"><span data-stu-id="d646f-155">Reference Types</span></span>](reference-types.md)
- [<span data-ttu-id="d646f-156">Typy dopuszczające wartości zerowe</span><span class="sxs-lookup"><span data-stu-id="d646f-156">Nullable types</span></span>](../../programming-guide/nullable-types/index.md)
