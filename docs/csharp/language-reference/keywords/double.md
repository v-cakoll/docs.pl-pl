---
title: Double — słowo kluczowe (odwołanie w C#)
ms.date: 07/20/2015
f1_keywords:
- double
- double_CSharpKeyword
helpviewer_keywords:
- double data type [C#]
ms.assetid: 0980e11b-6004-4102-abcf-cfc280fc6991
ms.openlocfilehash: 4c11065d9354d44c1da8354c6f7b4f52d7b84c10
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/25/2018
ms.locfileid: "47085271"
---
# <a name="double-c-reference"></a><span data-ttu-id="a1d83-102">double (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="a1d83-102">double (C# Reference)</span></span>

<span data-ttu-id="a1d83-103">`double` — Słowo kluczowe oznacza prosty typ, który przechowuje 64-bitowych wartości zmiennoprzecinkowych.</span><span class="sxs-lookup"><span data-stu-id="a1d83-103">The `double` keyword signifies a simple type that stores 64-bit floating-point values.</span></span> <span data-ttu-id="a1d83-104">W poniższej tabeli przedstawiono dokładności i przybliżony zakres `double` typu.</span><span class="sxs-lookup"><span data-stu-id="a1d83-104">The following table shows the precision and approximate range for the `double` type.</span></span>

|<span data-ttu-id="a1d83-105">Typ</span><span class="sxs-lookup"><span data-stu-id="a1d83-105">Type</span></span>|<span data-ttu-id="a1d83-106">Przybliżony zakres</span><span class="sxs-lookup"><span data-stu-id="a1d83-106">Approximate range</span></span>|<span data-ttu-id="a1d83-107">Dokładność</span><span class="sxs-lookup"><span data-stu-id="a1d83-107">Precision</span></span>|<span data-ttu-id="a1d83-108">Typ architektury .NET</span><span class="sxs-lookup"><span data-stu-id="a1d83-108">.NET type</span></span>|
|----------|-----------------------|---------------|-------------------------|
|`double`|<span data-ttu-id="a1d83-109">±5.0 x 10<sup>−324</sup> do ±1.7 x 10<sup>308</sup></span><span class="sxs-lookup"><span data-stu-id="a1d83-109">±5.0 × 10<sup>−324</sup> to ±1.7 × 10<sup>308</sup></span></span>|<span data-ttu-id="a1d83-110">15-16 cyfr</span><span class="sxs-lookup"><span data-stu-id="a1d83-110">15-16 digits</span></span>|<xref:System.Double?displayProperty=nameWithType>|

## <a name="literals"></a><span data-ttu-id="a1d83-111">Literały</span><span class="sxs-lookup"><span data-stu-id="a1d83-111">Literals</span></span>

<span data-ttu-id="a1d83-112">Domyślnie, literał liczby rzeczywistej liczbowy po prawej stronie operatora przypisania jest traktowany jako `double`.</span><span class="sxs-lookup"><span data-stu-id="a1d83-112">By default, a real numeric literal on the right side of the assignment operator is treated as `double`.</span></span> <span data-ttu-id="a1d83-113">Jednakże jeśli mają być traktowane jako liczba całkowita z zakresu `double`, Użyj sufiksu d lub D, na przykład:</span><span class="sxs-lookup"><span data-stu-id="a1d83-113">However, if you want an integer number to be treated as `double`, use the suffix d or D, for example:</span></span>

```csharp
double x = 3D;
```

## <a name="conversions"></a><span data-ttu-id="a1d83-114">Konwersje</span><span class="sxs-lookup"><span data-stu-id="a1d83-114">Conversions</span></span>

<span data-ttu-id="a1d83-115">Możesz mieszać liczbowych typów całkowitych i zmiennoprzecinkowych w wyrażeniu.</span><span class="sxs-lookup"><span data-stu-id="a1d83-115">You can mix numeric integral types and floating-point types in an expression.</span></span> <span data-ttu-id="a1d83-116">W tym przypadku typów całkowitych są konwertowane do typów zmiennoprzecinkowych.</span><span class="sxs-lookup"><span data-stu-id="a1d83-116">In this case, the integral types are converted to floating-point types.</span></span> <span data-ttu-id="a1d83-117">Obliczania wyrażenia odbywa się zgodnie z następującymi zasadami:</span><span class="sxs-lookup"><span data-stu-id="a1d83-117">The evaluation of the expression is performed according to the following rules:</span></span>

- <span data-ttu-id="a1d83-118">Po spełnieniu jednego z typów zmiennoprzecinkowych `double`, wyrażenie ma `double`, lub [bool](../../../csharp/language-reference/keywords/bool.md) porównania relacyjne i porównania dla równości.</span><span class="sxs-lookup"><span data-stu-id="a1d83-118">If one of the floating-point types is `double`, the expression evaluates to `double`, or to [bool](../../../csharp/language-reference/keywords/bool.md) in relational comparisons and comparisons for equality.</span></span>

- <span data-ttu-id="a1d83-119">W przypadku nie `double` typ w wyrażeniu, był oceniany do [float](../../../csharp/language-reference/keywords/float.md), lub [bool](../../../csharp/language-reference/keywords/bool.md) porównania relacyjne i porównania dla równości.</span><span class="sxs-lookup"><span data-stu-id="a1d83-119">If there is no `double` type in the expression, it evaluates to [float](../../../csharp/language-reference/keywords/float.md), or to [bool](../../../csharp/language-reference/keywords/bool.md) in relational comparisons and comparisons for equality.</span></span>

 <span data-ttu-id="a1d83-120">Wyrażenie typu zmiennoprzecinkowego może zawierać następujące zestawy wartości:</span><span class="sxs-lookup"><span data-stu-id="a1d83-120">A floating-point expression can contain the following sets of values:</span></span>

- <span data-ttu-id="a1d83-121">Zero dodatnie i ujemne.</span><span class="sxs-lookup"><span data-stu-id="a1d83-121">Positive and negative zero.</span></span>

- <span data-ttu-id="a1d83-122">Dodatnie i ujemne nieskończoność.</span><span class="sxs-lookup"><span data-stu-id="a1d83-122">Positive and negative infinity.</span></span>

- <span data-ttu-id="a1d83-123">Wartość nie a liczbą (NaN).</span><span class="sxs-lookup"><span data-stu-id="a1d83-123">Not-a-Number value (NaN).</span></span>

- <span data-ttu-id="a1d83-124">Ograniczone zbiór wartości wartość różną od zera.</span><span class="sxs-lookup"><span data-stu-id="a1d83-124">The finite set of nonzero values.</span></span>

<span data-ttu-id="a1d83-125">Aby uzyskać więcej informacji na temat tych wartości, zobacz Standard IEEE binarne zmiennopozycyjna operacje arytmetyczne, dostępne na [IEEE](https://www.ieee.org) witryny sieci Web.</span><span class="sxs-lookup"><span data-stu-id="a1d83-125">For more information about these values, see IEEE Standard for Binary Floating-Point Arithmetic, available on the [IEEE](https://www.ieee.org) Web site.</span></span>

## <a name="example"></a><span data-ttu-id="a1d83-126">Przykład</span><span class="sxs-lookup"><span data-stu-id="a1d83-126">Example</span></span>

<span data-ttu-id="a1d83-127">W poniższym przykładzie [int](../../../csharp/language-reference/keywords/int.md), [krótki](../../../csharp/language-reference/keywords/short.md), [float](../../../csharp/language-reference/keywords/float.md), a `double` są dodawane, jednocześnie zapewniając `double` wynik.</span><span class="sxs-lookup"><span data-stu-id="a1d83-127">In the following example, an [int](../../../csharp/language-reference/keywords/int.md), a [short](../../../csharp/language-reference/keywords/short.md), a [float](../../../csharp/language-reference/keywords/float.md), and a `double` are added together giving a `double` result.</span></span>

[!code-csharp[csrefKeywordsTypes#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#9)]

## <a name="c-language-specification"></a><span data-ttu-id="a1d83-128">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="a1d83-128">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="a1d83-129">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a1d83-129">See Also</span></span>

- [<span data-ttu-id="a1d83-130">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="a1d83-130">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="a1d83-131">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="a1d83-131">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="a1d83-132">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="a1d83-132">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
- [<span data-ttu-id="a1d83-133">Tabela wartości domyślnych</span><span class="sxs-lookup"><span data-stu-id="a1d83-133">Default Values Table</span></span>](../../../csharp/language-reference/keywords/default-values-table.md)  
- [<span data-ttu-id="a1d83-134">Tabela typów wbudowanych</span><span class="sxs-lookup"><span data-stu-id="a1d83-134">Built-In Types Table</span></span>](../../../csharp/language-reference/keywords/built-in-types-table.md)  
- [<span data-ttu-id="a1d83-135">Tabela typów zmiennoprzecinkowych</span><span class="sxs-lookup"><span data-stu-id="a1d83-135">Floating-Point Types Table</span></span>](../../../csharp/language-reference/keywords/floating-point-types-table.md)  
- [<span data-ttu-id="a1d83-136">Tabela niejawnych konwersji liczbowych</span><span class="sxs-lookup"><span data-stu-id="a1d83-136">Implicit Numeric Conversions Table</span></span>](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)  
- [<span data-ttu-id="a1d83-137">Tabela jawnych konwersji liczbowych</span><span class="sxs-lookup"><span data-stu-id="a1d83-137">Explicit Numeric Conversions Table</span></span>](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)  
