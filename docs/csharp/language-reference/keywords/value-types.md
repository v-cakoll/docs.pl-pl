---
title: Typy wartości (odwołanie w C#)
ms.date: 07/20/2015
f1_keywords:
- cs.valuetypes
helpviewer_keywords:
- value types [C#]
- types [C#], value types
- C# language, value types
ms.assetid: 471eb994-2958-49d5-a6be-19b4313f80a3
ms.openlocfilehash: 3bbaea9247d975c27ed6f49dedb749312f675296
ms.sourcegitcommit: a368166a51e5204c0224fbf5e46476e3ed122817
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/31/2018
ms.locfileid: "43331853"
---
# <a name="value-types-c-reference"></a><span data-ttu-id="9bfe8-102">Typy wartości (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="9bfe8-102">Value Types (C# Reference)</span></span>
<span data-ttu-id="9bfe8-103">Typy wartości obejmują dwie główne kategorie:</span><span class="sxs-lookup"><span data-stu-id="9bfe8-103">The value types consist of two main categories:</span></span>  
  
-   [<span data-ttu-id="9bfe8-104">Struktury</span><span class="sxs-lookup"><span data-stu-id="9bfe8-104">Structs</span></span>](../../../csharp/language-reference/keywords/struct.md)  
  
-   [<span data-ttu-id="9bfe8-105">Wyliczenia</span><span class="sxs-lookup"><span data-stu-id="9bfe8-105">Enumerations</span></span>](../../../csharp/language-reference/keywords/enum.md)  
  
 <span data-ttu-id="9bfe8-106">Struktury można podzielić na następujące kategorie:</span><span class="sxs-lookup"><span data-stu-id="9bfe8-106">Structs fall into these categories:</span></span>  
  
-   <span data-ttu-id="9bfe8-107">Typy liczbowe</span><span class="sxs-lookup"><span data-stu-id="9bfe8-107">Numeric types</span></span>  
  
    -   [<span data-ttu-id="9bfe8-108">Typy całkowite</span><span class="sxs-lookup"><span data-stu-id="9bfe8-108">Integral types</span></span>](../../../csharp/language-reference/keywords/integral-types-table.md)  
  
    -   [<span data-ttu-id="9bfe8-109">Typy zmiennoprzecinkowe</span><span class="sxs-lookup"><span data-stu-id="9bfe8-109">Floating-point types</span></span>](../../../csharp/language-reference/keywords/floating-point-types-table.md)  
  
-   [<span data-ttu-id="9bfe8-110">bool</span><span class="sxs-lookup"><span data-stu-id="9bfe8-110">bool</span></span>](../../../csharp/language-reference/keywords/bool.md)  
  
-   <span data-ttu-id="9bfe8-111">Struktury zdefiniowany przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="9bfe8-111">User defined structs.</span></span>  
  
## <a name="main-features-of-value-types"></a><span data-ttu-id="9bfe8-112">Główne funkcje typów wartości</span><span class="sxs-lookup"><span data-stu-id="9bfe8-112">Main Features of Value Types</span></span>  
 <span data-ttu-id="9bfe8-113">Zmienne, które są oparte na typach wartości bezpośrednio zawierają wartości.</span><span class="sxs-lookup"><span data-stu-id="9bfe8-113">Variables that are based on value types directly contain values.</span></span> <span data-ttu-id="9bfe8-114">Przypisanie jednej zmiennej typu wartości do innej kopii zawarte wartości.</span><span class="sxs-lookup"><span data-stu-id="9bfe8-114">Assigning one value type variable to another copies the contained value.</span></span> <span data-ttu-id="9bfe8-115">To różni się od przypisania zmiennych typu odwołania, która kopiuje odwołanie do obiektu, ale nie samego obiektu.</span><span class="sxs-lookup"><span data-stu-id="9bfe8-115">This differs from the assignment of reference type variables, which copies a reference to the object but not the object itself.</span></span>  
  
 <span data-ttu-id="9bfe8-116">Wszystkie typy wartości niejawnie pochodzą od <xref:System.ValueType?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="9bfe8-116">All value types are derived implicitly from the <xref:System.ValueType?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="9bfe8-117">Inaczej niż w przypadku typów referencyjnych nie może pochodzić nowy typ z typem wartości.</span><span class="sxs-lookup"><span data-stu-id="9bfe8-117">Unlike with reference types, you cannot derive a new type from a value type.</span></span> <span data-ttu-id="9bfe8-118">Jednakże, takie jak typy odwołań struktury mogą implementować interfejsów.</span><span class="sxs-lookup"><span data-stu-id="9bfe8-118">However, like reference types, structs can implement interfaces.</span></span>  
  
 <span data-ttu-id="9bfe8-119">W przeciwieństwie do typów referencyjnych, typ wartości nie może zawierać `null` wartość.</span><span class="sxs-lookup"><span data-stu-id="9bfe8-119">Unlike reference types, a value type cannot contain the `null` value.</span></span> <span data-ttu-id="9bfe8-120">Jednak [typów dopuszczających wartości zerowe](../../../csharp/programming-guide/nullable-types/index.md) funkcja pozwala dla typów wartości, które ma być przypisane do `null`.</span><span class="sxs-lookup"><span data-stu-id="9bfe8-120">However, the [nullable types](../../../csharp/programming-guide/nullable-types/index.md) feature does allow for value types to be assigned to `null`.</span></span>  
  
 <span data-ttu-id="9bfe8-121">Różne wartości mają niejawnego domyślnego konstruktora, który jest inicjowana wartością domyślną tego typu.</span><span class="sxs-lookup"><span data-stu-id="9bfe8-121">Each value type has an implicit default constructor that initializes the default value of that type.</span></span> <span data-ttu-id="9bfe8-122">Aby uzyskać informacje o wartościach domyślnych typów wartości, zobacz [tabela wartości domyślnych](../../../csharp/language-reference/keywords/default-values-table.md).</span><span class="sxs-lookup"><span data-stu-id="9bfe8-122">For information about default values of value types, see [Default Values Table](../../../csharp/language-reference/keywords/default-values-table.md).</span></span>  
  
## <a name="main-features-of-simple-types"></a><span data-ttu-id="9bfe8-123">Najważniejsze typy proste</span><span class="sxs-lookup"><span data-stu-id="9bfe8-123">Main Features of Simple Types</span></span>  
 <span data-ttu-id="9bfe8-124">Wszystkie typy proste — te całkowite języka C# — są aliasy typów programu .NET Framework System.</span><span class="sxs-lookup"><span data-stu-id="9bfe8-124">All of the simple types -- those integral to the C# language -- are aliases of the .NET Framework System types.</span></span> <span data-ttu-id="9bfe8-125">Na przykład [int](../../../csharp/language-reference/keywords/int.md) jest aliasem <xref:System.Int32?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="9bfe8-125">For example, [int](../../../csharp/language-reference/keywords/int.md) is an alias of <xref:System.Int32?displayProperty=nameWithType>.</span></span> <span data-ttu-id="9bfe8-126">Aby uzyskać pełną listę aliasów, zobacz [Tabela typów wbudowanych](../../../csharp/language-reference/keywords/built-in-types-table.md).</span><span class="sxs-lookup"><span data-stu-id="9bfe8-126">For a complete list of aliases, see [Built-In Types Table](../../../csharp/language-reference/keywords/built-in-types-table.md).</span></span>  
  
 <span data-ttu-id="9bfe8-127">Wyrażenia stałe, w której argumenty operacji są stałymi typu prostego, są obliczane w czasie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="9bfe8-127">Constant expressions, whose operands are all simple type constants, are evaluated at compilation time.</span></span>  
  
 <span data-ttu-id="9bfe8-128">Proste typy mogą być inicjowane za pomocą literałów ciągów.</span><span class="sxs-lookup"><span data-stu-id="9bfe8-128">Simple types can be initialized by using literals.</span></span> <span data-ttu-id="9bfe8-129">Na przykład, "A" jest literał o typie `char` i 2001 jest literał o typie `int`.</span><span class="sxs-lookup"><span data-stu-id="9bfe8-129">For example, 'A' is a literal of the type `char` and 2001 is a literal of the type `int`.</span></span>  
  
## <a name="initializing-value-types"></a><span data-ttu-id="9bfe8-130">Inicjowanie typów wartości</span><span class="sxs-lookup"><span data-stu-id="9bfe8-130">Initializing Value Types</span></span>  
 <span data-ttu-id="9bfe8-131">Zmienne lokalne w języku C# muszą zostać zainicjowane, przed są one używane.</span><span class="sxs-lookup"><span data-stu-id="9bfe8-131">Local variables in C# must be initialized before they are used.</span></span> <span data-ttu-id="9bfe8-132">Na przykład może zadeklarować zmienną lokalną bez inicjowania, jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="9bfe8-132">For example, you might declare a local variable without initialization as in the following example:</span></span>  
  
```csharp  
int myInt;  
```  
  
 <span data-ttu-id="9bfe8-133">Nie można użyć go, przed jej inicjalizację.</span><span class="sxs-lookup"><span data-stu-id="9bfe8-133">You cannot use it before you initialize it.</span></span> <span data-ttu-id="9bfe8-134">Można zainicjować za pomocą następującej instrukcji:</span><span class="sxs-lookup"><span data-stu-id="9bfe8-134">You can initialize it using the following statement:</span></span>  
  
```csharp  
myInt = new int();  // Invoke default constructor for int type.  
```  
  
 <span data-ttu-id="9bfe8-135">Ta instrukcja jest równoważna następującej instrukcji:</span><span class="sxs-lookup"><span data-stu-id="9bfe8-135">This statement is equivalent to the following statement:</span></span>  
  
```csharp  
myInt = 0;         // Assign an initial value, 0 in this example.  
```  
  
 <span data-ttu-id="9bfe8-136">Można oczywiście masz deklaracji i inicjowania w tej samej instrukcji, co pokazano w następujących przykładach:</span><span class="sxs-lookup"><span data-stu-id="9bfe8-136">You can, of course, have the declaration and the initialization in the same statement as in the following examples:</span></span>  
  
```csharp  
int myInt = new int();  
```  
  
 <span data-ttu-id="9bfe8-137">— lub —</span><span class="sxs-lookup"><span data-stu-id="9bfe8-137">–or–</span></span>  
  
```csharp  
int myInt = 0;  
```  
  
 <span data-ttu-id="9bfe8-138">Za pomocą [nowe](../../../csharp/language-reference/keywords/new.md) operator wywołuje domyślnego konstruktora określonego typu i przypisuje wartość domyślną do zmiennej.</span><span class="sxs-lookup"><span data-stu-id="9bfe8-138">Using the [new](../../../csharp/language-reference/keywords/new.md) operator calls the default constructor of the specific type and assigns the default value to the variable.</span></span> <span data-ttu-id="9bfe8-139">W powyższym przykładzie konstruktora domyślnego przypisaną wartość `0` do `myInt`.</span><span class="sxs-lookup"><span data-stu-id="9bfe8-139">In the preceding example, the default constructor assigned the value `0` to `myInt`.</span></span> <span data-ttu-id="9bfe8-140">Aby uzyskać więcej informacji na temat wartości przypisane przez wywołanie metody konstruktory domyślne zobacz [tabela wartości domyślnych](../../../csharp/language-reference/keywords/default-values-table.md).</span><span class="sxs-lookup"><span data-stu-id="9bfe8-140">For more information about values assigned by calling default constructors, see [Default Values Table](../../../csharp/language-reference/keywords/default-values-table.md).</span></span>  
  
 <span data-ttu-id="9bfe8-141">W przypadku typów zdefiniowanych przez użytkownika, należy użyć [nowe](../../../csharp/language-reference/keywords/new.md) do wywołania konstruktora domyślnego.</span><span class="sxs-lookup"><span data-stu-id="9bfe8-141">With user-defined types, use [new](../../../csharp/language-reference/keywords/new.md) to invoke the default constructor.</span></span> <span data-ttu-id="9bfe8-142">Na przykład następująca instrukcja wywołuje domyślny konstruktor obiektu `Point` struktury:</span><span class="sxs-lookup"><span data-stu-id="9bfe8-142">For example, the following statement invokes the default constructor of the `Point` struct:</span></span>  
  
```csharp  
Point p = new Point(); // Invoke default constructor for the struct.  
```  
  
 <span data-ttu-id="9bfe8-143">Po tym wywołaniu struktury uznaje się być zdecydowanie przypisywany; oznacza to, że wszystkie jego elementy członkowskie są inicjowane do wartości domyślnych.</span><span class="sxs-lookup"><span data-stu-id="9bfe8-143">After this call, the struct is considered to be definitely assigned; that is, all its members are initialized to their default values.</span></span>  
  
 <span data-ttu-id="9bfe8-144">Aby uzyskać więcej informacji na temat operatora new zobacz [nowe](../../../csharp/language-reference/keywords/new.md).</span><span class="sxs-lookup"><span data-stu-id="9bfe8-144">For more information about the new operator, see [new](../../../csharp/language-reference/keywords/new.md).</span></span>  
  
 <span data-ttu-id="9bfe8-145">Aby dowiedzieć się, jak formatowanie danych wyjściowych typów liczbowych, zobacz [formatowanie tabeli wyników liczbowych](../../../csharp/language-reference/keywords/formatting-numeric-results-table.md).</span><span class="sxs-lookup"><span data-stu-id="9bfe8-145">For information about formatting the output of numeric types, see [Formatting Numeric Results Table](../../../csharp/language-reference/keywords/formatting-numeric-results-table.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9bfe8-146">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9bfe8-146">See Also</span></span>

- [<span data-ttu-id="9bfe8-147">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="9bfe8-147">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="9bfe8-148">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="9bfe8-148">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="9bfe8-149">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="9bfe8-149">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
- [<span data-ttu-id="9bfe8-150">Typy</span><span class="sxs-lookup"><span data-stu-id="9bfe8-150">Types</span></span>](../../../csharp/language-reference/keywords/types.md)  
- [<span data-ttu-id="9bfe8-151">Tabele odwołań dla typów</span><span class="sxs-lookup"><span data-stu-id="9bfe8-151">Reference Tables for Types</span></span>](../../../csharp/language-reference/keywords/reference-tables-for-types.md)  
- [<span data-ttu-id="9bfe8-152">Typy odwołań</span><span class="sxs-lookup"><span data-stu-id="9bfe8-152">Reference Types</span></span>](../../../csharp/language-reference/keywords/reference-types.md)  
- [<span data-ttu-id="9bfe8-153">Typy dopuszczające wartości zerowe</span><span class="sxs-lookup"><span data-stu-id="9bfe8-153">Nullable types</span></span>](../../programming-guide/nullable-types/index.md)  
