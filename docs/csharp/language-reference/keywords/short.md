---
title: krótki - C# odwołania
ms.custom: seodec18
ms.date: 03/14/2017
f1_keywords:
- short
- short_CSharpKeyword
helpviewer_keywords:
- short keyword [C#]
ms.assetid: 04c10688-e51a-4a87-bfec-83f7fb42ff11
ms.openlocfilehash: 0b02e72e0588f1c1a0343a391430b5878b96b5f5
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65633988"
---
# <a name="short-c-reference"></a><span data-ttu-id="282ff-102">short (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="282ff-102">short (C# Reference)</span></span>

<span data-ttu-id="282ff-103">`short` Wskazuje, że typ liczby całkowitej danych, który przechowuje wartości w zależności od rozmiaru i zakres pokazano w poniższej tabeli.</span><span class="sxs-lookup"><span data-stu-id="282ff-103">`short` denotes an integral data type that stores values according to the size and range shown in the following table.</span></span>

|<span data-ttu-id="282ff-104">Typ</span><span class="sxs-lookup"><span data-stu-id="282ff-104">Type</span></span>|<span data-ttu-id="282ff-105">Zakres</span><span class="sxs-lookup"><span data-stu-id="282ff-105">Range</span></span>|<span data-ttu-id="282ff-106">Rozmiar</span><span class="sxs-lookup"><span data-stu-id="282ff-106">Size</span></span>|<span data-ttu-id="282ff-107">Typ architektury .NET</span><span class="sxs-lookup"><span data-stu-id="282ff-107">.NET type</span></span>|
|----------|-----------|----------|-------------------------|
|`short`|<span data-ttu-id="282ff-108">-32768 do 32767.</span><span class="sxs-lookup"><span data-stu-id="282ff-108">-32,768 to 32,767</span></span>|<span data-ttu-id="282ff-109">16-bitową liczbę całkowitą ze znakiem</span><span class="sxs-lookup"><span data-stu-id="282ff-109">Signed 16-bit integer</span></span>|<xref:System.Int16?displayProperty=nameWithType>|

## <a name="literals"></a><span data-ttu-id="282ff-110">Literały</span><span class="sxs-lookup"><span data-stu-id="282ff-110">Literals</span></span>

<span data-ttu-id="282ff-111">Można zadeklarować i zainicjować `short` zmiennej przypisując literał dziesiętny szesnastkowy literał lub (rozpoczynający się znakami języka C# 7.0) literału do niego dane binarne.</span><span class="sxs-lookup"><span data-stu-id="282ff-111">You can declare and initialize a `short` variable by assigning a decimal literal, a hexadecimal literal, or (starting with C# 7.0) a binary literal to it.</span></span>  <span data-ttu-id="282ff-112">Jeśli literał liczby całkowitej jest poza zakresem `short` (to znaczy, jeśli jest mniejszy niż <xref:System.Int16.MinValue?displayProperty=nameWithType> lub większa niż <xref:System.Int16.MaxValue?displayProperty=nameWithType>), wystąpi błąd kompilacji.</span><span class="sxs-lookup"><span data-stu-id="282ff-112">If the integer literal is outside the range of `short` (that is, if it is less than <xref:System.Int16.MinValue?displayProperty=nameWithType> or greater than <xref:System.Int16.MaxValue?displayProperty=nameWithType>), a compilation error occurs.</span></span>

<span data-ttu-id="282ff-113">W poniższym przykładzie liczb całkowitych równa 1,034, które są reprezentowane jako dziesiętne, szesnastkową, i literały binarne są niejawnie konwertowane z [int](int.md) do `short` wartości.</span><span class="sxs-lookup"><span data-stu-id="282ff-113">In the following example, integers equal to 1,034 that are represented as decimal, hexadecimal, and binary literals are implicitly converted from [int](int.md) to `short` values.</span></span>

[!code-csharp[Short](~/samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#Short)]

> [!NOTE]
> <span data-ttu-id="282ff-114">Użyj prefiksu `0x` lub `0X` do oznaczania szesnastkowy literał i prefiksem `0b` lub `0B` do oznaczania literału binarnego.</span><span class="sxs-lookup"><span data-stu-id="282ff-114">You use the prefix `0x` or `0X` to denote a hexadecimal literal and the prefix `0b` or `0B` to denote a binary literal.</span></span> <span data-ttu-id="282ff-115">Literały dziesiętna mieć żadnego prefiksu.</span><span class="sxs-lookup"><span data-stu-id="282ff-115">Decimal literals have no prefix.</span></span>

<span data-ttu-id="282ff-116">Uruchamianie przy użyciu języka C# 7.0, dodano kilka funkcji zwiększyć czytelność.</span><span class="sxs-lookup"><span data-stu-id="282ff-116">Starting with C# 7.0, a couple of features have been added to enhance readability.</span></span>

- <span data-ttu-id="282ff-117">C# 7.0 umożliwia użycie znaku podkreślenia `_`, jako separator cyfr.</span><span class="sxs-lookup"><span data-stu-id="282ff-117">C# 7.0 allows the usage of the underscore character, `_`, as a digit separator.</span></span>
- <span data-ttu-id="282ff-118">Umożliwia w języku C# 7.2 `_` ma być używany jako separator cyfr dla literału binarnego lub szesnastkowego po prefiksie.</span><span class="sxs-lookup"><span data-stu-id="282ff-118">C# 7.2 allows `_` to be used as a digit separator for a binary or hexadecimal literal, after the prefix.</span></span> <span data-ttu-id="282ff-119">Literał dziesiętny nie mogą mieć wiodącego podkreślenia.</span><span class="sxs-lookup"><span data-stu-id="282ff-119">A decimal literal isn't permitted to have a leading underscore.</span></span>

<span data-ttu-id="282ff-120">Poniżej przedstawiono kilka przykładów.</span><span class="sxs-lookup"><span data-stu-id="282ff-120">Some examples are shown below.</span></span>

[!code-csharp[Short](~/samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#ShortS)]

## <a name="compiler-overload-resolution"></a><span data-ttu-id="282ff-121">Przeciążeń z późnym</span><span class="sxs-lookup"><span data-stu-id="282ff-121">Compiler overload resolution</span></span>

<span data-ttu-id="282ff-122">Podczas wywoływania przeciążone metody, należy użyć rzutowania.</span><span class="sxs-lookup"><span data-stu-id="282ff-122">A cast must be used when calling overloaded methods.</span></span> <span data-ttu-id="282ff-123">Należy wziąć pod uwagę, na przykład, następujące przeciążone metody, które używają `short` i [int](int.md) parametry:</span><span class="sxs-lookup"><span data-stu-id="282ff-123">Consider, for example, the following overloaded methods that use `short` and [int](int.md) parameters:</span></span>

```csharp
public static void SampleMethod(int i) {}
public static void SampleMethod(short s) {}
```

<span data-ttu-id="282ff-124">Za pomocą `short` rzutowania gwarantuje, że poprawnego typu ma nazwę, na przykład:</span><span class="sxs-lookup"><span data-stu-id="282ff-124">Using the `short` cast guarantees that the correct type is called, for example:</span></span>

```csharp
SampleMethod(5);         // Calling the method with the int parameter
SampleMethod((short)5);  // Calling the method with the short parameter
```

## <a name="conversions"></a><span data-ttu-id="282ff-125">Konwersje</span><span class="sxs-lookup"><span data-stu-id="282ff-125">Conversions</span></span>

<span data-ttu-id="282ff-126">Jest wstępnie zdefiniowanych niejawna konwersja z `short` do [int](int.md), [długie](long.md), [float](float.md), [double](double.md), lub [ dziesiętna](decimal.md).</span><span class="sxs-lookup"><span data-stu-id="282ff-126">There is a predefined implicit conversion from `short` to [int](int.md), [long](long.md), [float](float.md), [double](double.md), or [decimal](decimal.md).</span></span>

<span data-ttu-id="282ff-127">Nie można niejawnie przekonwertować nieliteralnego typy liczbowe większy rozmiar magazynu na `short` (zobacz [Tabela typów całkowitych](integral-types-table.md) dla rozmiaru magazynu typów całkowitych).</span><span class="sxs-lookup"><span data-stu-id="282ff-127">You cannot implicitly convert nonliteral numeric types of larger storage size to `short` (see [Integral Types Table](integral-types-table.md) for the storage sizes of integral types).</span></span> <span data-ttu-id="282ff-128">Należy wziąć pod uwagę, na przykład, następujące dwa `short` zmienne `x` i `y`:</span><span class="sxs-lookup"><span data-stu-id="282ff-128">Consider, for example, the following two `short` variables `x` and `y`:</span></span>

```csharp
short x = 5, y = 12;
```

<span data-ttu-id="282ff-129">Poniższa instrukcja przypisania powoduje błąd kompilacji, ponieważ daje w wyniku wyrażenia arytmetycznego po prawej stronie operatora przypisania [int](int.md) domyślnie.</span><span class="sxs-lookup"><span data-stu-id="282ff-129">The following assignment statement produces a compilation error because the arithmetic expression on the right-hand side of the assignment operator evaluates to [int](int.md) by default.</span></span>

```csharp
short z  = x + y;        // Compiler error CS0266: no conversion from int to short
```

<span data-ttu-id="282ff-130">Aby rozwiązać ten problem, należy użyć rzutowania:</span><span class="sxs-lookup"><span data-stu-id="282ff-130">To fix this problem, use a cast:</span></span>

```csharp
short z  = (short)(x + y);   // Explicit conversion
```

<span data-ttu-id="282ff-131">Istnieje również możliwość użycia poniższe instrukcje, gdzie zmienna docelowa ma taki sam rozmiar magazynu lub większy rozmiar magazynu:</span><span class="sxs-lookup"><span data-stu-id="282ff-131">It is also possible to use the following statements, where the destination variable has the same storage size or a larger storage size:</span></span>

```csharp
int m = x + y;
long n = x + y;
```

<span data-ttu-id="282ff-132">Istnieje niejawna konwersja z typów zmiennoprzecinkowych `short`.</span><span class="sxs-lookup"><span data-stu-id="282ff-132">There is no implicit conversion from floating-point types to `short`.</span></span> <span data-ttu-id="282ff-133">Na przykład następująca instrukcja generuje błąd kompilatora, chyba że używana jest jawnego rzutowania:</span><span class="sxs-lookup"><span data-stu-id="282ff-133">For example, the following statement generates a compiler error unless an explicit cast is used:</span></span>

```csharp
short x = 3.0;          // Error: no implicit conversion from double
short y = (short)3.0;   // OK: explicit conversion
```

<span data-ttu-id="282ff-134">Instrukcje dotyczące wyrażeniach arytmetycznych mieszane typy zmiennoprzecinkowe i całkowite typy, zobacz [float](float.md) i [double](double.md).</span><span class="sxs-lookup"><span data-stu-id="282ff-134">For information on arithmetic expressions with mixed floating-point types and integral types, see [float](float.md) and [double](double.md).</span></span>

<span data-ttu-id="282ff-135">Aby uzyskać więcej informacji na temat reguł niejawnych konwersji liczbowych, zobacz [Implicit Numeric Conversions Table](implicit-numeric-conversions-table.md).</span><span class="sxs-lookup"><span data-stu-id="282ff-135">For more information on implicit numeric conversion rules, see the [Implicit Numeric Conversions Table](implicit-numeric-conversions-table.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="282ff-136">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="282ff-136">C# language specification</span></span>

<span data-ttu-id="282ff-137">Aby uzyskać więcej informacji, zobacz [typów całkowitych](~/_csharplang/spec/types.md#integral-types) w [ C# specyfikacji języka](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="282ff-137">For more information, see [Integral types](~/_csharplang/spec/types.md#integral-types) in the [C# Language Specification](../language-specification/index.md).</span></span> <span data-ttu-id="282ff-138">Specyfikacja języka jest ostatecznym źródłem informacji o składni i użyciu języka C#.</span><span class="sxs-lookup"><span data-stu-id="282ff-138">The language specification is the definitive source for C# syntax and usage.</span></span>

## <a name="see-also"></a><span data-ttu-id="282ff-139">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="282ff-139">See also</span></span>

- <xref:System.Int16>
- [<span data-ttu-id="282ff-140">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="282ff-140">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="282ff-141">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="282ff-141">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="282ff-142">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="282ff-142">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="282ff-143">Tabela typów całkowitych</span><span class="sxs-lookup"><span data-stu-id="282ff-143">Integral Types Table</span></span>](integral-types-table.md)
- [<span data-ttu-id="282ff-144">Tabela typów wbudowanych</span><span class="sxs-lookup"><span data-stu-id="282ff-144">Built-In Types Table</span></span>](built-in-types-table.md)
- [<span data-ttu-id="282ff-145">Tabela niejawnych konwersji liczbowych</span><span class="sxs-lookup"><span data-stu-id="282ff-145">Implicit Numeric Conversions Table</span></span>](implicit-numeric-conversions-table.md)
- [<span data-ttu-id="282ff-146">Tabela jawnych konwersji liczbowych</span><span class="sxs-lookup"><span data-stu-id="282ff-146">Explicit Numeric Conversions Table</span></span>](explicit-numeric-conversions-table.md)
