---
title: decimal — słowo kluczowe - C# odwołania
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- decimal_CSharpKeyword
- decimal
helpviewer_keywords:
- decimal keyword [C#]
ms.assetid: b6522132-b5ee-4be3-ad13-3adfdb7de7a1
ms.openlocfilehash: 7ad01f9e4f5a8b1a153b1ef306e9d6168335eb3d
ms.sourcegitcommit: 9b1ac36b6c80176fd4e20eb5bfcbd9d56c3264cf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/28/2019
ms.locfileid: "67424308"
---
# <a name="decimal-c-reference"></a><span data-ttu-id="c2722-102">decimal (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="c2722-102">decimal (C# Reference)</span></span>

<span data-ttu-id="c2722-103">`decimal` — Słowo kluczowe wskazuje typ danych 128-bitowych.</span><span class="sxs-lookup"><span data-stu-id="c2722-103">The `decimal` keyword indicates a 128-bit data type.</span></span> <span data-ttu-id="c2722-104">W porównaniu do innych typów zmiennoprzecinkowych `decimal` typ ma większą dokładność i mniejszy zakres, który sprawia, że odpowiedni do obliczeń finansowych i walutowych.</span><span class="sxs-lookup"><span data-stu-id="c2722-104">Compared to other floating-point types, the `decimal` type has more precision and a smaller range, which makes it appropriate for financial and monetary calculations.</span></span> <span data-ttu-id="c2722-105">Przybliżony zakres i dokładność `decimal` typu są wyświetlane w poniższej tabeli.</span><span class="sxs-lookup"><span data-stu-id="c2722-105">The approximate range and precision for the `decimal` type are shown in the following table.</span></span>

|<span data-ttu-id="c2722-106">Typ</span><span class="sxs-lookup"><span data-stu-id="c2722-106">Type</span></span>|<span data-ttu-id="c2722-107">Przybliżony zakres</span><span class="sxs-lookup"><span data-stu-id="c2722-107">Approximate Range</span></span>|<span data-ttu-id="c2722-108">Dokładność</span><span class="sxs-lookup"><span data-stu-id="c2722-108">Precision</span></span>|<span data-ttu-id="c2722-109">Typ architektury .NET</span><span class="sxs-lookup"><span data-stu-id="c2722-109">.NET type</span></span>|
|----------|-----------------------|---------------|-------------------------|
|`decimal`|<span data-ttu-id="c2722-110">±1.0 x 10<sup>-28</sup> do ±7.9228 x 10<sup>28</sup></span><span class="sxs-lookup"><span data-stu-id="c2722-110">±1.0 x 10<sup>-28</sup> to ±7.9228 x 10<sup>28</sup></span></span>|<span data-ttu-id="c2722-111">28–29 cyfr znaczących</span><span class="sxs-lookup"><span data-stu-id="c2722-111">28-29 significant digits</span></span>|<xref:System.Decimal?displayProperty=nameWithType>|

<span data-ttu-id="c2722-112">Wartość domyślna `decimal` wynosi 0, m.</span><span class="sxs-lookup"><span data-stu-id="c2722-112">The default value of a `decimal` is 0m.</span></span>

## <a name="literals"></a><span data-ttu-id="c2722-113">Literały</span><span class="sxs-lookup"><span data-stu-id="c2722-113">Literals</span></span>

<span data-ttu-id="c2722-114">Jeśli chcesz, aby rzeczywistych literał liczbowy powinien być traktowany jako `decimal`, należy użyć sufiksu m lub M, na przykład:</span><span class="sxs-lookup"><span data-stu-id="c2722-114">If you want a numeric real literal to be treated as `decimal`, use the suffix m or M, for example:</span></span>

```csharp
decimal myMoney = 300.5m;
```

<span data-ttu-id="c2722-115">Bez sufiksu m liczba jest traktowana [double](../../../csharp/language-reference/keywords/double.md) i generuje błąd kompilatora.</span><span class="sxs-lookup"><span data-stu-id="c2722-115">Without the suffix m, the number is treated as a [double](../../../csharp/language-reference/keywords/double.md) and generates a compiler error.</span></span>

## <a name="conversions"></a><span data-ttu-id="c2722-116">Konwersje</span><span class="sxs-lookup"><span data-stu-id="c2722-116">Conversions</span></span>

<span data-ttu-id="c2722-117">Typy całkowite są niejawnie konwertowane na `decimal` i wynik daje w wyniku `decimal`.</span><span class="sxs-lookup"><span data-stu-id="c2722-117">The integral types are implicitly converted to `decimal` and the result evaluates to `decimal`.</span></span> <span data-ttu-id="c2722-118">Dlatego można zainicjować zmienną typu decimal, używając literału typu integer, bez konieczności użycia sufiksu, tak jak pokazano poniżej:</span><span class="sxs-lookup"><span data-stu-id="c2722-118">Therefore you can initialize a decimal variable using an integer literal, without the suffix, as follows:</span></span>

```csharp
decimal myMoney = 300;
```

<span data-ttu-id="c2722-119">Istnieje niejawna konwersja między innymi typami zmiennoprzecinkowymi a `decimal` typu; w związku z tym, należy użyć rzutowania, aby przekonwertować między tymi dwoma typami.</span><span class="sxs-lookup"><span data-stu-id="c2722-119">There is no implicit conversion between other floating-point types and the `decimal` type; therefore, a cast must be used to convert between these two types.</span></span> <span data-ttu-id="c2722-120">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="c2722-120">For example:</span></span>

```csharp
decimal myMoney = 99.9m;
double x = (double)myMoney;
myMoney = (decimal)x;
```

<span data-ttu-id="c2722-121">Można także łączyć `decimal` całkowite typy liczbowe w jednym wyrażeniu.</span><span class="sxs-lookup"><span data-stu-id="c2722-121">You can also mix `decimal` and numeric integral types in the same expression.</span></span> <span data-ttu-id="c2722-122">Jednak jednoczesne użycie typu `decimal` i innych typów zmiennoprzecinkowych bez rzutowania spowoduje błąd kompilacji.</span><span class="sxs-lookup"><span data-stu-id="c2722-122">However, mixing `decimal` and other floating-point types without a cast causes a compilation error.</span></span>

<span data-ttu-id="c2722-123">Aby uzyskać więcej informacji dotyczących niejawnych konwersji liczbowych, zobacz [Implicit Numeric Conversions Table](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md).</span><span class="sxs-lookup"><span data-stu-id="c2722-123">For more information about implicit numeric conversions, see [Implicit Numeric Conversions Table](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md).</span></span>

<span data-ttu-id="c2722-124">Aby uzyskać więcej informacji dotyczących jawnych konwersji liczbowych, zobacz [Explicit Numeric Conversions Table](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md).</span><span class="sxs-lookup"><span data-stu-id="c2722-124">For more information about explicit numeric conversions, see [Explicit Numeric Conversions Table](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md).</span></span>

## <a name="formatting-decimal-output"></a><span data-ttu-id="c2722-125">Formatowanie danych wyjściowych typu decimal</span><span class="sxs-lookup"><span data-stu-id="c2722-125">Formatting decimal output</span></span>

<span data-ttu-id="c2722-126">Wyniki można formatować, przy użyciu `String.Format` metodę, lub za pomocą <xref:System.Console.Write%2A?displayProperty=nameWithType> metody, która wywołuje `String.Format()`.</span><span class="sxs-lookup"><span data-stu-id="c2722-126">You can format the results by using the `String.Format` method, or through the <xref:System.Console.Write%2A?displayProperty=nameWithType> method, which calls `String.Format()`.</span></span> <span data-ttu-id="c2722-127">Format waluty jest określany przy użyciu standardowego ciągu formatu walutowego (C lub c), tak jak pokazano w drugim przykładzie w dalszej części tego artykułu.</span><span class="sxs-lookup"><span data-stu-id="c2722-127">The currency format is specified by using the standard currency format string "C" or "c," as shown in the second example later in this article.</span></span> <span data-ttu-id="c2722-128">Aby uzyskać więcej informacji na temat `String.Format` metody, zobacz <xref:System.String.Format%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="c2722-128">For more information about the `String.Format` method, see <xref:System.String.Format%2A?displayProperty=nameWithType>.</span></span>

## <a name="example"></a><span data-ttu-id="c2722-129">Przykład</span><span class="sxs-lookup"><span data-stu-id="c2722-129">Example</span></span>

<span data-ttu-id="c2722-130">Poniższy przykład powoduje błąd kompilatora spowodowany próbą dodania [double](../../../csharp/language-reference/keywords/double.md) i `decimal` zmiennych.</span><span class="sxs-lookup"><span data-stu-id="c2722-130">The following example causes a compiler error by trying to add [double](../../../csharp/language-reference/keywords/double.md) and `decimal` variables.</span></span>

```csharp
decimal dec = 0m;
double dub = 9;
// The following line causes an error that reads "Operator '+' cannot be applied to
// operands of type 'double' and 'decimal'"
Console.WriteLine(dec + dub);

// You can fix the error by using explicit casting of either operand.
Console.WriteLine(dec + (decimal)dub);
Console.WriteLine((double)dec + dub);
```

<span data-ttu-id="c2722-131">Wynikiem jest następujący błąd:</span><span class="sxs-lookup"><span data-stu-id="c2722-131">The result is the following error:</span></span>

`Operator '+' cannot be applied to operands of type 'double' and 'decimal'`

<span data-ttu-id="c2722-132">W tym przykładzie `decimal` i [int](../../../csharp/language-reference/builtin-types/integral-numeric-types.md) są używane razem w jednym wyrażeniu.</span><span class="sxs-lookup"><span data-stu-id="c2722-132">In this example, a `decimal` and an [int](../../../csharp/language-reference/builtin-types/integral-numeric-types.md) are mixed in the same expression.</span></span> <span data-ttu-id="c2722-133">Wynik daje w wyniku `decimal` typu.</span><span class="sxs-lookup"><span data-stu-id="c2722-133">The result evaluates to the `decimal` type.</span></span>

[!code-csharp[csrefKeywordsTypes#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#6)]

## <a name="example"></a><span data-ttu-id="c2722-134">Przykład</span><span class="sxs-lookup"><span data-stu-id="c2722-134">Example</span></span>

<span data-ttu-id="c2722-135">W tym przykładzie dane wyjściowe są formatowane przy użyciu ciągu formatu walutowego.</span><span class="sxs-lookup"><span data-stu-id="c2722-135">In this example, the output is formatted by using the currency format string.</span></span> <span data-ttu-id="c2722-136">Należy zauważyć, że `x` jest zaokrąglana, ponieważ liczba miejsc dziesiętnych przekracza wartość 0,99.</span><span class="sxs-lookup"><span data-stu-id="c2722-136">Notice that `x` is rounded because the decimal places exceed $0.99.</span></span> <span data-ttu-id="c2722-137">Zmienna `y`, która przedstawia maksymalną dokładną liczbę cyfr, jest wyświetlana dokładnie w poprawnym formacie.</span><span class="sxs-lookup"><span data-stu-id="c2722-137">The variable `y`, which represents the maximum exact digits, is displayed exactly in the correct format.</span></span>

[!code-csharp[csrefKeywordsTypes#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#7)]

## <a name="c-language-specification"></a><span data-ttu-id="c2722-138">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="c2722-138">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="c2722-139">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c2722-139">See also</span></span>

- <xref:System.Decimal>
- [<span data-ttu-id="c2722-140">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="c2722-140">C# Reference</span></span>](../../../csharp/language-reference/index.md)
- [<span data-ttu-id="c2722-141">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="c2722-141">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="c2722-142">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="c2722-142">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)
- [<span data-ttu-id="c2722-143">Typy całkowite</span><span class="sxs-lookup"><span data-stu-id="c2722-143">Integral types</span></span>](../../../csharp/language-reference/builtin-types/integral-numeric-types.md)
- [<span data-ttu-id="c2722-144">Tabela typów wbudowanych</span><span class="sxs-lookup"><span data-stu-id="c2722-144">Built-In Types Table</span></span>](../../../csharp/language-reference/keywords/built-in-types-table.md)
- [<span data-ttu-id="c2722-145">Tabela niejawnych konwersji liczbowych</span><span class="sxs-lookup"><span data-stu-id="c2722-145">Implicit Numeric Conversions Table</span></span>](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)
- [<span data-ttu-id="c2722-146">Tabela jawnych konwersji liczbowych</span><span class="sxs-lookup"><span data-stu-id="c2722-146">Explicit Numeric Conversions Table</span></span>](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)
- [<span data-ttu-id="c2722-147">Standardowe ciągi formatujące liczby</span><span class="sxs-lookup"><span data-stu-id="c2722-147">Standard Numeric Format Strings</span></span>](../../../standard/base-types/standard-numeric-format-strings.md)
