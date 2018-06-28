---
title: float — słowo kluczowe (odwołanie w C#)
ms.date: 07/20/2015
f1_keywords:
- float
- float_CSharpKeyword
helpviewer_keywords:
- float keyword [C#]
- floating-point numbers [C#], float keyword
ms.assetid: 1e77db7b-dedb-48b7-8dd1-b055e96a9258
ms.openlocfilehash: 9500aceed62904e68d6b7ee8bec569d12103bb18
ms.sourcegitcommit: f9e38d31288fe5962e6be5b0cc286da633482873
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/27/2018
ms.locfileid: "37028243"
---
# <a name="float-c-reference"></a><span data-ttu-id="9059a-102">float (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="9059a-102">float (C# Reference)</span></span>

<span data-ttu-id="9059a-103">`float` — Słowo kluczowe oznacza typu prostego, która przechowuje 32-bitowych wartości zmiennoprzecinkowych.</span><span class="sxs-lookup"><span data-stu-id="9059a-103">The `float` keyword signifies a simple type that stores 32-bit floating-point values.</span></span> <span data-ttu-id="9059a-104">W poniższej tabeli przedstawiono dokładność i zakres przybliżonej `float` typu.</span><span class="sxs-lookup"><span data-stu-id="9059a-104">The following table shows the precision and approximate range for the `float` type.</span></span>

|<span data-ttu-id="9059a-105">Typ</span><span class="sxs-lookup"><span data-stu-id="9059a-105">Type</span></span>|<span data-ttu-id="9059a-106">Zakresie</span><span class="sxs-lookup"><span data-stu-id="9059a-106">Approximate range</span></span>|<span data-ttu-id="9059a-107">Dokładność</span><span class="sxs-lookup"><span data-stu-id="9059a-107">Precision</span></span>|<span data-ttu-id="9059a-108">Typ architektury .NET</span><span class="sxs-lookup"><span data-stu-id="9059a-108">.NET type</span></span>|  
|----------|-----------------------|---------------|-------------------------|  
|`float`|<span data-ttu-id="9059a-109">-3,4 x 10<sup>38</sup> do + 3,4 x 10<sup>38</sup></span><span class="sxs-lookup"><span data-stu-id="9059a-109">-3.4 × 10<sup>38</sup> to +3.4 × 10<sup>38</sup></span></span>|<span data-ttu-id="9059a-110">7 cyfr</span><span class="sxs-lookup"><span data-stu-id="9059a-110">7 digits</span></span>|<xref:System.Single?displayProperty=nameWithType>|  

## <a name="literals"></a><span data-ttu-id="9059a-111">Literały</span><span class="sxs-lookup"><span data-stu-id="9059a-111">Literals</span></span>

<span data-ttu-id="9059a-112">Domyślnie rzeczywistym literałem po prawej stronie operatora przypisania jest traktowany jako [podwójne](double.md).</span><span class="sxs-lookup"><span data-stu-id="9059a-112">By default, a real numeric literal on the right side of the assignment operator is treated as [double](double.md).</span></span> <span data-ttu-id="9059a-113">W związku z tym można zainicjować zmiennej typu float, używają sufiksu `f` lub `F`, jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="9059a-113">Therefore, to initialize a float variable, use the suffix `f` or `F`, as in the following example:</span></span>

```csharp
float x = 3.5F;
```

<span data-ttu-id="9059a-114">Jeśli nie używasz sufiks w poprzedniej deklaracji, otrzymasz błąd kompilacji, ponieważ chcesz przechowywać [podwójne](double.md) wartości do `float` zmiennej.</span><span class="sxs-lookup"><span data-stu-id="9059a-114">If you do not use the suffix in the previous declaration, you will get a compilation error because you are trying to store a [double](double.md) value into a `float` variable.</span></span>

## <a name="conversions"></a><span data-ttu-id="9059a-115">Konwersje</span><span class="sxs-lookup"><span data-stu-id="9059a-115">Conversions</span></span>

<span data-ttu-id="9059a-116">Można mieszać liczbowych typów całkowitych i zmiennoprzecinkowych w wyrażeniu.</span><span class="sxs-lookup"><span data-stu-id="9059a-116">You can mix numeric integral types and floating-point types in an expression.</span></span> <span data-ttu-id="9059a-117">W takim przypadku typów całkowitych są konwertowane na typów zmiennoprzecinkowych.</span><span class="sxs-lookup"><span data-stu-id="9059a-117">In this case, the integral types are converted to floating-point types.</span></span> <span data-ttu-id="9059a-118">Obliczanie wyrażenia odbywa się zgodnie z następującymi zasadami:</span><span class="sxs-lookup"><span data-stu-id="9059a-118">The evaluation of the expression is performed according to the following rules:</span></span>

- <span data-ttu-id="9059a-119">Po spełnieniu jednego z typów zmiennoprzecinkowych [podwójne](double.md), wyrażenie ma [podwójne](double.md) lub [bool](bool.md) w wyrażeniach relacyjnych lub Boolean.</span><span class="sxs-lookup"><span data-stu-id="9059a-119">If one of the floating-point types is [double](double.md), the expression evaluates to [double](double.md) or [bool](bool.md) in relational or Boolean expressions.</span></span>

- <span data-ttu-id="9059a-120">W przypadku nie [podwójne](double.md) typ w wyrażeniu wyrażenie daje w wyniku `float` lub [bool](bool.md) w wyrażeniach relacyjnych lub Boolean.</span><span class="sxs-lookup"><span data-stu-id="9059a-120">If there is no [double](double.md) type in the expression, the expression evaluates to `float` or [bool](bool.md) in relational or Boolean expressions.</span></span>

<span data-ttu-id="9059a-121">Zmiennoprzecinkowe wyrażenie może zawierać następujące zestawy wartości:</span><span class="sxs-lookup"><span data-stu-id="9059a-121">A floating-point expression can contain the following sets of values:</span></span>

- <span data-ttu-id="9059a-122">Zero dodatnie i ujemne</span><span class="sxs-lookup"><span data-stu-id="9059a-122">Positive and negative zero</span></span>

- <span data-ttu-id="9059a-123">Dodatnie i ujemne infinity</span><span class="sxs-lookup"><span data-stu-id="9059a-123">Positive and negative infinity</span></span>

- <span data-ttu-id="9059a-124">Wartość nie-liczby (NaN)</span><span class="sxs-lookup"><span data-stu-id="9059a-124">Not-a-Number value (NaN)</span></span>

- <span data-ttu-id="9059a-125">Ograniczone zbiór niezerowe wartości</span><span class="sxs-lookup"><span data-stu-id="9059a-125">The finite set of nonzero values</span></span>

<span data-ttu-id="9059a-126">Aby uzyskać więcej informacji na temat tych wartości, zobacz Standard IEEE binarne Floating-Point operacje arytmetyczne, dostępnych na [IEEE](http://www.ieee.org) witryny sieci Web.</span><span class="sxs-lookup"><span data-stu-id="9059a-126">For more information about these values, see IEEE Standard for Binary Floating-Point Arithmetic, available on the [IEEE](http://www.ieee.org) website.</span></span>

## <a name="example"></a><span data-ttu-id="9059a-127">Przykład</span><span class="sxs-lookup"><span data-stu-id="9059a-127">Example</span></span>

<span data-ttu-id="9059a-128">W poniższym przykładzie [int](int.md), [krótki](short.md), a `float` są uwzględnione w wyrażeniu matematycznym nadanie `float` wynik.</span><span class="sxs-lookup"><span data-stu-id="9059a-128">In the following example, an [int](int.md), a [short](short.md), and a `float` are included in a mathematical expression giving a `float` result.</span></span> <span data-ttu-id="9059a-129">(Należy pamiętać, że `float` jest aliasem <xref:System.Single?displayProperty=nameWithType> typu.) Należy zauważyć, że istnieje nie [podwójne](double.md) w wyrażeniu.</span><span class="sxs-lookup"><span data-stu-id="9059a-129">(Remember that `float` is an alias for the <xref:System.Single?displayProperty=nameWithType> type.) Notice that there is no [double](double.md) in the expression.</span></span>

[!code-csharp[csrefKeywordsTypes#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#13)]

## <a name="c-language-specification"></a><span data-ttu-id="9059a-130">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="9059a-130">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="9059a-131">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9059a-131">See also</span></span>

<xref:System.Single>  
[<span data-ttu-id="9059a-132">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="9059a-132">C# Reference</span></span>](../index.md)  
[<span data-ttu-id="9059a-133">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="9059a-133">C# Programming Guide</span></span>](../../programming-guide/index.md)  
[<span data-ttu-id="9059a-134">Rzutowanie i konwersje typów</span><span class="sxs-lookup"><span data-stu-id="9059a-134">Casting and Type Conversions</span></span>](../../programming-guide/types/casting-and-type-conversions.md)  
[<span data-ttu-id="9059a-135">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="9059a-135">C# Keywords</span></span>](index.md)  
[<span data-ttu-id="9059a-136">Tabela typów całkowitych</span><span class="sxs-lookup"><span data-stu-id="9059a-136">Integral Types Table</span></span>](integral-types-table.md)  
[<span data-ttu-id="9059a-137">Tabela typów wbudowanych</span><span class="sxs-lookup"><span data-stu-id="9059a-137">Built-In Types Table</span></span>](built-in-types-table.md)  
[<span data-ttu-id="9059a-138">Tabela niejawnych konwersji liczbowych</span><span class="sxs-lookup"><span data-stu-id="9059a-138">Implicit Numeric Conversions Table</span></span>](implicit-numeric-conversions-table.md)  
[<span data-ttu-id="9059a-139">Tabela jawnych konwersji liczbowych</span><span class="sxs-lookup"><span data-stu-id="9059a-139">Explicit Numeric Conversions Table</span></span>](explicit-numeric-conversions-table.md)  