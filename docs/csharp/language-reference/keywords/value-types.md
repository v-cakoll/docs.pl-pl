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
ms.openlocfilehash: 49043a9fe9eabbb54176a0106007ef0d26ed795f
ms.sourcegitcommit: 89c93d05c2281b4c834f48f6c8df1047e1410980
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2018
ms.locfileid: "34172215"
---
# <a name="value-types-c-reference"></a><span data-ttu-id="84354-102">Typy wartości (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="84354-102">Value Types (C# Reference)</span></span>
<span data-ttu-id="84354-103">Typy wartości obejmują dwie główne kategorie:</span><span class="sxs-lookup"><span data-stu-id="84354-103">The value types consist of two main categories:</span></span>  
  
-   [<span data-ttu-id="84354-104">Struktury</span><span class="sxs-lookup"><span data-stu-id="84354-104">Structs</span></span>](../../../csharp/language-reference/keywords/struct.md)  
  
-   [<span data-ttu-id="84354-105">Wyliczenia</span><span class="sxs-lookup"><span data-stu-id="84354-105">Enumerations</span></span>](../../../csharp/language-reference/keywords/enum.md)  
  
 <span data-ttu-id="84354-106">Struktury można podzielić na następujące kategorie:</span><span class="sxs-lookup"><span data-stu-id="84354-106">Structs fall into these categories:</span></span>  
  
-   <span data-ttu-id="84354-107">Typy liczbowe</span><span class="sxs-lookup"><span data-stu-id="84354-107">Numeric types</span></span>  
  
    -   [<span data-ttu-id="84354-108">Typy całkowite</span><span class="sxs-lookup"><span data-stu-id="84354-108">Integral types</span></span>](../../../csharp/language-reference/keywords/integral-types-table.md)  
  
    -   [<span data-ttu-id="84354-109">Typy zmiennoprzecinkowe</span><span class="sxs-lookup"><span data-stu-id="84354-109">Floating-point types</span></span>](../../../csharp/language-reference/keywords/floating-point-types-table.md)  
  
    -   [<span data-ttu-id="84354-110">decimal</span><span class="sxs-lookup"><span data-stu-id="84354-110">decimal</span></span>](../../../csharp/language-reference/keywords/decimal.md)  
  
-   [<span data-ttu-id="84354-111">bool</span><span class="sxs-lookup"><span data-stu-id="84354-111">bool</span></span>](../../../csharp/language-reference/keywords/bool.md)  
  
-   <span data-ttu-id="84354-112">Struktury zdefiniowane przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="84354-112">User defined structs.</span></span>  
  
## <a name="main-features-of-value-types"></a><span data-ttu-id="84354-113">Główne funkcje typów wartości</span><span class="sxs-lookup"><span data-stu-id="84354-113">Main Features of Value Types</span></span>  
 <span data-ttu-id="84354-114">Zmienne, które są oparte na typy wartości bezpośrednio zawierać wartości.</span><span class="sxs-lookup"><span data-stu-id="84354-114">Variables that are based on value types directly contain values.</span></span> <span data-ttu-id="84354-115">Przypisywanie jedną wartość typu zmienną do innej kopii zawartych w niej wartości.</span><span class="sxs-lookup"><span data-stu-id="84354-115">Assigning one value type variable to another copies the contained value.</span></span> <span data-ttu-id="84354-116">To różni się od przypisywanie zmienne odwołujące się do typu, który kopiuje odwołanie do obiektu, ale nie samego obiektu.</span><span class="sxs-lookup"><span data-stu-id="84354-116">This differs from the assignment of reference type variables, which copies a reference to the object but not the object itself.</span></span>  
  
 <span data-ttu-id="84354-117">Wszystkie typy wartości są pochodnymi niejawnie <xref:System.ValueType?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="84354-117">All value types are derived implicitly from the <xref:System.ValueType?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="84354-118">W odróżnieniu od z typami odwołanie, nie może pochodzić nowy typ z typem wartości.</span><span class="sxs-lookup"><span data-stu-id="84354-118">Unlike with reference types, you cannot derive a new type from a value type.</span></span> <span data-ttu-id="84354-119">Jednakże, takich jak typy referencyjne struktury mogą implementować interfejsów.</span><span class="sxs-lookup"><span data-stu-id="84354-119">However, like reference types, structs can implement interfaces.</span></span>  
  
 <span data-ttu-id="84354-120">W przeciwieństwie do typów referencyjnych, typ wartości nie może zawierać `null` wartość.</span><span class="sxs-lookup"><span data-stu-id="84354-120">Unlike reference types, a value type cannot contain the `null` value.</span></span> <span data-ttu-id="84354-121">Jednak [typy dopuszczające wartości zerowe](../../../csharp/programming-guide/nullable-types/index.md) funkcji Zezwalaj dla typów wartości do przypisania do `null`.</span><span class="sxs-lookup"><span data-stu-id="84354-121">However, the [nullable types](../../../csharp/programming-guide/nullable-types/index.md) feature does allow for value types to be assigned to `null`.</span></span>  
  
 <span data-ttu-id="84354-122">Każdy typ wartości ma niejawne domyślnego konstruktora, który inicjuje wartością domyślną tego typu.</span><span class="sxs-lookup"><span data-stu-id="84354-122">Each value type has an implicit default constructor that initializes the default value of that type.</span></span> <span data-ttu-id="84354-123">Aby uzyskać informacje o wartościach domyślnych typów wartości, zobacz [tabela wartości domyślnych](../../../csharp/language-reference/keywords/default-values-table.md).</span><span class="sxs-lookup"><span data-stu-id="84354-123">For information about default values of value types, see [Default Values Table](../../../csharp/language-reference/keywords/default-values-table.md).</span></span>  
  
## <a name="main-features-of-simple-types"></a><span data-ttu-id="84354-124">Główne funkcje typy proste</span><span class="sxs-lookup"><span data-stu-id="84354-124">Main Features of Simple Types</span></span>  
 <span data-ttu-id="84354-125">Wszystkie typy proste — te typy całkowite języka C# — są aliasów typów .NET Framework systemu.</span><span class="sxs-lookup"><span data-stu-id="84354-125">All of the simple types -- those integral to the C# language -- are aliases of the .NET Framework System types.</span></span> <span data-ttu-id="84354-126">Na przykład [int](../../../csharp/language-reference/keywords/int.md) jest aliasem <xref:System.Int32?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="84354-126">For example, [int](../../../csharp/language-reference/keywords/int.md) is an alias of <xref:System.Int32?displayProperty=nameWithType>.</span></span> <span data-ttu-id="84354-127">Aby uzyskać pełną listę aliasów, zobacz [Tabela typów wbudowanych](../../../csharp/language-reference/keywords/built-in-types-table.md).</span><span class="sxs-lookup"><span data-stu-id="84354-127">For a complete list of aliases, see [Built-In Types Table](../../../csharp/language-reference/keywords/built-in-types-table.md).</span></span>  
  
 <span data-ttu-id="84354-128">Wyrażenia stałe, którego argumenty operacji są wszystkich stałych typu prostego, są oceniane w czasie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="84354-128">Constant expressions, whose operands are all simple type constants, are evaluated at compilation time.</span></span>  
  
 <span data-ttu-id="84354-129">Proste typy mogą być inicjowane przy użyciu literałów.</span><span class="sxs-lookup"><span data-stu-id="84354-129">Simple types can be initialized by using literals.</span></span> <span data-ttu-id="84354-130">Na przykład, "A" jest literałem typu `char` i 2001 jest literałem typu `int`.</span><span class="sxs-lookup"><span data-stu-id="84354-130">For example, 'A' is a literal of the type `char` and 2001 is a literal of the type `int`.</span></span>  
  
## <a name="initializing-value-types"></a><span data-ttu-id="84354-131">Inicjowanie typów wartości</span><span class="sxs-lookup"><span data-stu-id="84354-131">Initializing Value Types</span></span>  
 <span data-ttu-id="84354-132">Zmienne lokalne w języku C# muszą zostać zainicjowane, przed są one używane.</span><span class="sxs-lookup"><span data-stu-id="84354-132">Local variables in C# must be initialized before they are used.</span></span> <span data-ttu-id="84354-133">Na przykład może zadeklarować zmiennej lokalnej bez inicjowania jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="84354-133">For example, you might declare a local variable without initialization as in the following example:</span></span>  
  
```csharp  
int myInt;  
```  
  
 <span data-ttu-id="84354-134">Nie można używać go, zanim można go zainicjować.</span><span class="sxs-lookup"><span data-stu-id="84354-134">You cannot use it before you initialize it.</span></span> <span data-ttu-id="84354-135">Można zainicjować za pomocą następujących instrukcji:</span><span class="sxs-lookup"><span data-stu-id="84354-135">You can initialize it using the following statement:</span></span>  
  
```csharp  
myInt = new int();  // Invoke default constructor for int type.  
```  
  
 <span data-ttu-id="84354-136">Ta instrukcja jest odpowiednikiem następująca instrukcja:</span><span class="sxs-lookup"><span data-stu-id="84354-136">This statement is equivalent to the following statement:</span></span>  
  
```csharp  
myInt = 0;         // Assign an initial value, 0 in this example.  
```  
  
 <span data-ttu-id="84354-137">Deklaracji i inicjowania mogą oczywiście ma w tej samej instrukcji, na przykład:</span><span class="sxs-lookup"><span data-stu-id="84354-137">You can, of course, have the declaration and the initialization in the same statement as in the following examples:</span></span>  
  
```csharp  
int myInt = new int();  
```  
  
 <span data-ttu-id="84354-138">— lub —</span><span class="sxs-lookup"><span data-stu-id="84354-138">–or–</span></span>  
  
```csharp  
int myInt = 0;  
```  
  
 <span data-ttu-id="84354-139">Przy użyciu [nowe](../../../csharp/language-reference/keywords/new.md) operator wywołuje domyślny konstruktor obiektu określonego typu i przypisuje wartość domyślną do zmiennej.</span><span class="sxs-lookup"><span data-stu-id="84354-139">Using the [new](../../../csharp/language-reference/keywords/new.md) operator calls the default constructor of the specific type and assigns the default value to the variable.</span></span> <span data-ttu-id="84354-140">W powyższym przykładzie konstruktora domyślnego przypisaną wartość `0` do `myInt`.</span><span class="sxs-lookup"><span data-stu-id="84354-140">In the preceding example, the default constructor assigned the value `0` to `myInt`.</span></span> <span data-ttu-id="84354-141">Aby uzyskać więcej informacji na temat przypisanych przez wywołanie metody konstruktory domyślne wartości, zobacz [tabela wartości domyślnych](../../../csharp/language-reference/keywords/default-values-table.md).</span><span class="sxs-lookup"><span data-stu-id="84354-141">For more information about values assigned by calling default constructors, see [Default Values Table](../../../csharp/language-reference/keywords/default-values-table.md).</span></span>  
  
 <span data-ttu-id="84354-142">Typy danych zdefiniowane przez użytkownika, za pomocą [nowe](../../../csharp/language-reference/keywords/new.md) do wywołania konstruktora domyślnego.</span><span class="sxs-lookup"><span data-stu-id="84354-142">With user-defined types, use [new](../../../csharp/language-reference/keywords/new.md) to invoke the default constructor.</span></span> <span data-ttu-id="84354-143">Na przykład następująca instrukcja wywołuje domyślny konstruktor obiektu `Point` struktury:</span><span class="sxs-lookup"><span data-stu-id="84354-143">For example, the following statement invokes the default constructor of the `Point` struct:</span></span>  
  
```csharp  
Point p = new Point(); // Invoke default constructor for the struct.  
```  
  
 <span data-ttu-id="84354-144">Po tym wywołaniu struktury jest uznawany za można zdecydowanie przypisać; oznacza to, że wszyscy jej członkowie są inicjowane z wartościami domyślnymi.</span><span class="sxs-lookup"><span data-stu-id="84354-144">After this call, the struct is considered to be definitely assigned; that is, all its members are initialized to their default values.</span></span>  
  
 <span data-ttu-id="84354-145">Aby uzyskać więcej informacji na temat operatora new, zobacz [nowe](../../../csharp/language-reference/keywords/new.md).</span><span class="sxs-lookup"><span data-stu-id="84354-145">For more information about the new operator, see [new](../../../csharp/language-reference/keywords/new.md).</span></span>  
  
 <span data-ttu-id="84354-146">Aby dowiedzieć się, jak formatowanie danych wyjściowych typy liczbowe, zobacz [formatowanie tabeli wyników liczbowych](../../../csharp/language-reference/keywords/formatting-numeric-results-table.md).</span><span class="sxs-lookup"><span data-stu-id="84354-146">For information about formatting the output of numeric types, see [Formatting Numeric Results Table](../../../csharp/language-reference/keywords/formatting-numeric-results-table.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="84354-147">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="84354-147">See Also</span></span>  
 [<span data-ttu-id="84354-148">Odwołanie w C#</span><span class="sxs-lookup"><span data-stu-id="84354-148">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="84354-149">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="84354-149">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="84354-150">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="84354-150">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="84354-151">Typy</span><span class="sxs-lookup"><span data-stu-id="84354-151">Types</span></span>](../../../csharp/language-reference/keywords/types.md)  
 [<span data-ttu-id="84354-152">Tabele odwołań dla typów</span><span class="sxs-lookup"><span data-stu-id="84354-152">Reference Tables for Types</span></span>](../../../csharp/language-reference/keywords/reference-tables-for-types.md)  
 [<span data-ttu-id="84354-153">Typy odwołań</span><span class="sxs-lookup"><span data-stu-id="84354-153">Reference Types</span></span>](../../../csharp/language-reference/keywords/reference-types.md)
