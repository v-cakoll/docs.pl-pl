---
title: Long — C# odwołania
ms.custom: seodec18
ms.date: 03/14/2017
f1_keywords:
- long_CSharpKeyword
- long
helpviewer_keywords:
- long keyword [C#]
ms.assetid: f9b24319-1f39-48be-a42b-d528ee28a7fd
ms.openlocfilehash: 997ce7399dc9742076932b213811abd1f847e60b
ms.sourcegitcommit: 438919211260bb415fc8f96ca3eabc33cf2d681d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2019
ms.locfileid: "59613294"
---
# <a name="long-c-reference"></a><span data-ttu-id="dc338-102">long (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="dc338-102">long (C# Reference)</span></span>

<span data-ttu-id="dc338-103">`long` Wskazuje, że integralny typ, który przechowuje wartości w zależności od rozmiaru i zakres pokazano w poniższej tabeli.</span><span class="sxs-lookup"><span data-stu-id="dc338-103">`long` denotes an integral type that stores values according to the size and range shown in the following table.</span></span>

|<span data-ttu-id="dc338-104">Typ</span><span class="sxs-lookup"><span data-stu-id="dc338-104">Type</span></span>|<span data-ttu-id="dc338-105">Zakres</span><span class="sxs-lookup"><span data-stu-id="dc338-105">Range</span></span>|<span data-ttu-id="dc338-106">Rozmiar</span><span class="sxs-lookup"><span data-stu-id="dc338-106">Size</span></span>|<span data-ttu-id="dc338-107">Typ architektury .NET</span><span class="sxs-lookup"><span data-stu-id="dc338-107">.NET type</span></span>|
|----------|-----------|----------|-------------------------|
|`long`|<span data-ttu-id="dc338-108">-9,223,372,036,854,775,808 do 9,223,372,036,854,775,807</span><span class="sxs-lookup"><span data-stu-id="dc338-108">-9,223,372,036,854,775,808 to 9,223,372,036,854,775,807</span></span>|<span data-ttu-id="dc338-109">64-bitowa liczba całkowita ze znakiem</span><span class="sxs-lookup"><span data-stu-id="dc338-109">Signed 64-bit integer</span></span>|<xref:System.Int64?displayProperty=nameWithType>|

## <a name="literals"></a><span data-ttu-id="dc338-110">Literały</span><span class="sxs-lookup"><span data-stu-id="dc338-110">Literals</span></span>

<span data-ttu-id="dc338-111">Można zadeklarować i zainicjować `long` zmiennej przypisując literał dziesiętny szesnastkowy literał lub (rozpoczynający się znakami języka C# 7.0) literału do niego dane binarne.</span><span class="sxs-lookup"><span data-stu-id="dc338-111">You can declare and initialize a `long` variable by assigning a decimal literal, a hexadecimal literal, or (starting with C# 7.0) a binary literal to it.</span></span>

<span data-ttu-id="dc338-112">W poniższym przykładzie liczb całkowitych równa 4 294 967 296, które są reprezentowane jako dziesiętne, szesnastkową, i literały binarne są przypisane do `long` wartości.</span><span class="sxs-lookup"><span data-stu-id="dc338-112">In the following example, integers equal to 4,294,967,296 that are represented as decimal, hexadecimal, and binary literals are assigned to `long` values.</span></span>

[!code-csharp[long](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#Long)]

> [!NOTE]
> <span data-ttu-id="dc338-113">Użyj prefiksu `0x` lub `0X` do oznaczania szesnastkowy literał i prefiksem `0b` lub `0B` do oznaczania literału binarnego.</span><span class="sxs-lookup"><span data-stu-id="dc338-113">You use the prefix `0x` or `0X` to denote a hexadecimal literal and the prefix `0b` or `0B` to denote a binary literal.</span></span> <span data-ttu-id="dc338-114">Literały dziesiętna mieć żadnego prefiksu.</span><span class="sxs-lookup"><span data-stu-id="dc338-114">Decimal literals have no prefix.</span></span>

<span data-ttu-id="dc338-115">Uruchamianie przy użyciu języka C# 7.0, dodano kilka funkcji zwiększyć czytelność.</span><span class="sxs-lookup"><span data-stu-id="dc338-115">Starting with C# 7.0, a couple of features have been added to enhance readability.</span></span>
- <span data-ttu-id="dc338-116">C# 7.0 umożliwia użycie znaku podkreślenia `_`, jako separator cyfr.</span><span class="sxs-lookup"><span data-stu-id="dc338-116">C# 7.0 allows the usage of the underscore character, `_`, as a digit separator.</span></span>
- <span data-ttu-id="dc338-117">Umożliwia w języku C# 7.2 `_` ma być używany jako separator cyfr dla literału binarnego lub szesnastkowego po prefiksie.</span><span class="sxs-lookup"><span data-stu-id="dc338-117">C# 7.2 allows `_` to be used as a digit separator for a binary or hexadecimal literal, after the prefix.</span></span> <span data-ttu-id="dc338-118">Literał dziesiętny nie mogą mieć wiodącego podkreślenia.</span><span class="sxs-lookup"><span data-stu-id="dc338-118">A decimal literal isn't permitted to have a leading underscore.</span></span>

<span data-ttu-id="dc338-119">Poniżej przedstawiono kilka przykładów.</span><span class="sxs-lookup"><span data-stu-id="dc338-119">Some examples are shown below.</span></span>

[!code-csharp[long](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#LongS)]

<span data-ttu-id="dc338-120">Literały całkowite mogą również zawierać sufiks, który oznacza typ.</span><span class="sxs-lookup"><span data-stu-id="dc338-120">Integer literals can also include a suffix that denotes the type.</span></span> <span data-ttu-id="dc338-121">Sufiks `L` oznacza `long`.</span><span class="sxs-lookup"><span data-stu-id="dc338-121">The suffix `L` denotes a `long`.</span></span> <span data-ttu-id="dc338-122">W poniższym przykładzie użyto `L` sufiks do oznaczania długich liczb całkowitych:</span><span class="sxs-lookup"><span data-stu-id="dc338-122">The following example uses the `L` suffix to denote a long integer:</span></span>

```csharp
long value = 4294967296L;
```

> [!NOTE]
> <span data-ttu-id="dc338-123">Mała litera "l" można również użyć jako sufiks.</span><span class="sxs-lookup"><span data-stu-id="dc338-123">You can also use the lowercase letter "l" as a suffix.</span></span> <span data-ttu-id="dc338-124">Jednakże spowoduje to wygenerowanie ostrzeżenia kompilatora ponieważ litera "l" można łatwo pomylić z cyfrą "1".</span><span class="sxs-lookup"><span data-stu-id="dc338-124">However, this generates a compiler warning because the letter "l" is easily confused with the digit "1."</span></span> <span data-ttu-id="dc338-125">Użyj "L" w celu uściślenia.</span><span class="sxs-lookup"><span data-stu-id="dc338-125">Use "L" for clarity.</span></span>

<span data-ttu-id="dc338-126">Kiedy używasz sufiks `L`, typu literał liczby całkowitej zostanie uznane albo `long` lub [ulong](../../../csharp/language-reference/keywords/ulong.md), w zależności od rozmiaru.</span><span class="sxs-lookup"><span data-stu-id="dc338-126">When you use the suffix `L`, the type of the literal integer is determined to be either `long` or [ulong](../../../csharp/language-reference/keywords/ulong.md), depending on its size.</span></span> <span data-ttu-id="dc338-127">W tym przypadku jest to `long` ponieważ ona mniejsza niż zakres [ulong](../../../csharp/language-reference/keywords/ulong.md).</span><span class="sxs-lookup"><span data-stu-id="dc338-127">In this case, it is `long` because it less than the range of [ulong](../../../csharp/language-reference/keywords/ulong.md).</span></span>

<span data-ttu-id="dc338-128">Zazwyczaj sufiksu jest używane do wywołania przeciążonych metod.</span><span class="sxs-lookup"><span data-stu-id="dc338-128">A common use of the suffix is to call overloaded methods.</span></span> <span data-ttu-id="dc338-129">Na przykład mieć parametrów typu w następujących przeciążonych metod `long` i [int](../../../csharp/language-reference/keywords/int.md):</span><span class="sxs-lookup"><span data-stu-id="dc338-129">For example, the following overloaded methods have parameters of type `long` and [int](../../../csharp/language-reference/keywords/int.md):</span></span>

```csharp
public static void SampleMethod(int i) {}
public static void SampleMethod(long l) {}
```

<span data-ttu-id="dc338-130">`L` Sufiks gwarantuje, że poprawne przeciążenie jest wywoływana:</span><span class="sxs-lookup"><span data-stu-id="dc338-130">The `L` suffix guarantees that the correct overload is called:</span></span>

```csharp
SampleMethod(5);    // Calls the method with the int parameter
SampleMethod(5L);   // Calls the method with the long parameter
```

<span data-ttu-id="dc338-131">Jeśli literał liczby całkowitej nie sufiksu, jego typ jest pierwszym następujące typy, w których jej wartość może być reprezentowana:</span><span class="sxs-lookup"><span data-stu-id="dc338-131">If an integer literal has no suffix, its type is the first of the following types in which its value can be represented:</span></span>

1. [<span data-ttu-id="dc338-132">int</span><span class="sxs-lookup"><span data-stu-id="dc338-132">int</span></span>](int.md)
2. [<span data-ttu-id="dc338-133">uint</span><span class="sxs-lookup"><span data-stu-id="dc338-133">uint</span></span>](../../../csharp/language-reference/keywords/uint.md)
3. `long`
4. [<span data-ttu-id="dc338-134">ulong</span><span class="sxs-lookup"><span data-stu-id="dc338-134">ulong</span></span>](../../../csharp/language-reference/keywords/ulong.md)

<span data-ttu-id="dc338-135">Typem jest literał 4294967296 w poprzednich przykładach `long`, ponieważ spowodowałoby to przekroczenie zakresu [uint](../../../csharp/language-reference/keywords/uint.md) (zobacz [Tabela typów całkowitych](../../../csharp/language-reference/keywords/integral-types-table.md) dla rozmiaru magazynu typów całkowitych).</span><span class="sxs-lookup"><span data-stu-id="dc338-135">The literal 4294967296 in the previous examples is of type `long`, because it exceeds the range of [uint](../../../csharp/language-reference/keywords/uint.md) (see [Integral Types Table](../../../csharp/language-reference/keywords/integral-types-table.md) for the storage sizes of integral types).</span></span>

<span data-ttu-id="dc338-136">Jeśli używasz `long` typu o inne typy całkowitoliczbowe w jednym wyrażeniu, wyrażenie jest oceniane jako `long` (lub [bool](../../../csharp/language-reference/keywords/bool.md) w przypadku wyrażeń relacyjnych lub logiczną).</span><span class="sxs-lookup"><span data-stu-id="dc338-136">If you use the `long` type with other integral types in the same expression, the expression is evaluated as `long` (or [bool](../../../csharp/language-reference/keywords/bool.md) in the case of relational or Boolean expressions).</span></span> <span data-ttu-id="dc338-137">Na przykład poniższe wyrażenie obliczane jako `long`:</span><span class="sxs-lookup"><span data-stu-id="dc338-137">For example, the following expression evaluates as `long`:</span></span>

```csharp
898L + 88
```

<span data-ttu-id="dc338-138">Instrukcje dotyczące wyrażeniach arytmetycznych mieszane typy zmiennoprzecinkowe i całkowite typy, zobacz [float](../../../csharp/language-reference/keywords/float.md) i [double](../../../csharp/language-reference/keywords/double.md).</span><span class="sxs-lookup"><span data-stu-id="dc338-138">For information on arithmetic expressions with mixed floating-point types and integral types, see [float](../../../csharp/language-reference/keywords/float.md) and [double](../../../csharp/language-reference/keywords/double.md).</span></span>

## <a name="conversions"></a><span data-ttu-id="dc338-139">Konwersje</span><span class="sxs-lookup"><span data-stu-id="dc338-139">Conversions</span></span>

<span data-ttu-id="dc338-140">Jest wstępnie zdefiniowanych niejawna konwersja z `long` do [float](../../../csharp/language-reference/keywords/float.md), [double](../../../csharp/language-reference/keywords/double.md), lub [dziesiętna](../../../csharp/language-reference/keywords/decimal.md).</span><span class="sxs-lookup"><span data-stu-id="dc338-140">There is a predefined implicit conversion from `long` to [float](../../../csharp/language-reference/keywords/float.md), [double](../../../csharp/language-reference/keywords/double.md), or [decimal](../../../csharp/language-reference/keywords/decimal.md).</span></span> <span data-ttu-id="dc338-141">W przeciwnym razie należy użyć rzutowania.</span><span class="sxs-lookup"><span data-stu-id="dc338-141">Otherwise a cast must be used.</span></span> <span data-ttu-id="dc338-142">Na przykład następująca instrukcja generuje błąd kompilacji bez jawnego rzutowania:</span><span class="sxs-lookup"><span data-stu-id="dc338-142">For example, the following statement will produce a compilation error without an explicit cast:</span></span>

```csharp
int x = 8L;        // Error: no implicit conversion from long to int
int y = (int)8L;   // OK: explicit conversion to int
```

<span data-ttu-id="dc338-143">Jest wstępnie zdefiniowanych niejawna konwersja z [sbyte](../../../csharp/language-reference/keywords/sbyte.md), [bajtów](../../../csharp/language-reference/keywords/byte.md), [krótki](../../../csharp/language-reference/keywords/short.md), [ushort](../../../csharp/language-reference/keywords/ushort.md), [int](../../../csharp/language-reference/keywords/int.md), [uint](../../../csharp/language-reference/keywords/uint.md), lub [char](../../../csharp/language-reference/keywords/char.md) do `long`.</span><span class="sxs-lookup"><span data-stu-id="dc338-143">There is a predefined implicit conversion from [sbyte](../../../csharp/language-reference/keywords/sbyte.md), [byte](../../../csharp/language-reference/keywords/byte.md), [short](../../../csharp/language-reference/keywords/short.md), [ushort](../../../csharp/language-reference/keywords/ushort.md), [int](../../../csharp/language-reference/keywords/int.md), [uint](../../../csharp/language-reference/keywords/uint.md), or [char](../../../csharp/language-reference/keywords/char.md) to `long`.</span></span>

<span data-ttu-id="dc338-144">Zwróć uwagę, że nie istnieje niejawna konwersja z typów zmiennoprzecinkowych `long`.</span><span class="sxs-lookup"><span data-stu-id="dc338-144">Notice also that there is no implicit conversion from floating-point types to `long`.</span></span> <span data-ttu-id="dc338-145">Na przykład następująca instrukcja generuje błąd kompilatora, chyba że używana jest jawnego rzutowania:</span><span class="sxs-lookup"><span data-stu-id="dc338-145">For example, the following statement generates a compiler error unless an explicit cast is used:</span></span>

```csharp
long x = 3.0;         // Error: no implicit conversion from double
long y = (long)3.0;   // OK: explicit conversion
```

## <a name="c-language-specification"></a><span data-ttu-id="dc338-146">Specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="dc338-146">C# Language Specification</span></span>

<span data-ttu-id="dc338-147">Aby uzyskać więcej informacji, zobacz [typów całkowitych](~/_csharplang/spec/types.md#integral-types) w [ C# specyfikacji języka](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="dc338-147">For more information, see [Integral types](~/_csharplang/spec/types.md#integral-types) in the [C# Language Specification](../language-specification/index.md).</span></span> <span data-ttu-id="dc338-148">Specyfikacja języka jest ostatecznym źródłem informacji o składni i użyciu języka C#.</span><span class="sxs-lookup"><span data-stu-id="dc338-148">The language specification is the definitive source for C# syntax and usage.</span></span>

## <a name="see-also"></a><span data-ttu-id="dc338-149">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="dc338-149">See also</span></span>

- <xref:System.Int64>
- [<span data-ttu-id="dc338-150">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="dc338-150">C# Reference</span></span>](../../../csharp/language-reference/index.md)
- [<span data-ttu-id="dc338-151">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="dc338-151">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="dc338-152">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="dc338-152">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)
- [<span data-ttu-id="dc338-153">Tabela typów całkowitych</span><span class="sxs-lookup"><span data-stu-id="dc338-153">Integral Types Table</span></span>](../../../csharp/language-reference/keywords/integral-types-table.md)
- [<span data-ttu-id="dc338-154">Tabela typów wbudowanych</span><span class="sxs-lookup"><span data-stu-id="dc338-154">Built-In Types Table</span></span>](../../../csharp/language-reference/keywords/built-in-types-table.md)
- [<span data-ttu-id="dc338-155">Tabela niejawnych konwersji liczbowych</span><span class="sxs-lookup"><span data-stu-id="dc338-155">Implicit Numeric Conversions Table</span></span>](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)
- [<span data-ttu-id="dc338-156">Tabela jawnych konwersji liczbowych</span><span class="sxs-lookup"><span data-stu-id="dc338-156">Explicit Numeric Conversions Table</span></span>](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)
