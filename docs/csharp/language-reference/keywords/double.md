---
title: Double — słowo kluczowe (odwołanie w C#)
ms.date: 07/20/2015
f1_keywords:
- double
- double_CSharpKeyword
helpviewer_keywords:
- double data type [C#]
ms.assetid: 0980e11b-6004-4102-abcf-cfc280fc6991
ms.openlocfilehash: 8e3a94bb79d46f2815e46b86f1aca92acc73e5c2
ms.sourcegitcommit: f9e38d31288fe5962e6be5b0cc286da633482873
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/27/2018
ms.locfileid: "37027853"
---
# <a name="double-c-reference"></a><span data-ttu-id="59c41-102">double (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="59c41-102">double (C# Reference)</span></span>

<span data-ttu-id="59c41-103">`double` — Słowo kluczowe oznacza typu prostego, która przechowuje 64-bitowych wartości zmiennoprzecinkowych.</span><span class="sxs-lookup"><span data-stu-id="59c41-103">The `double` keyword signifies a simple type that stores 64-bit floating-point values.</span></span> <span data-ttu-id="59c41-104">W poniższej tabeli przedstawiono dokładność i zakres przybliżonej `double` typu.</span><span class="sxs-lookup"><span data-stu-id="59c41-104">The following table shows the precision and approximate range for the `double` type.</span></span>

|<span data-ttu-id="59c41-105">Typ</span><span class="sxs-lookup"><span data-stu-id="59c41-105">Type</span></span>|<span data-ttu-id="59c41-106">Zakresie</span><span class="sxs-lookup"><span data-stu-id="59c41-106">Approximate range</span></span>|<span data-ttu-id="59c41-107">Dokładność</span><span class="sxs-lookup"><span data-stu-id="59c41-107">Precision</span></span>|<span data-ttu-id="59c41-108">Typ architektury .NET</span><span class="sxs-lookup"><span data-stu-id="59c41-108">.NET type</span></span>|
|----------|-----------------------|---------------|-------------------------|
|`double`|<span data-ttu-id="59c41-109">±5.0 x 10<sup>−324</sup> do ±1.7 x 10<sup>308</sup></span><span class="sxs-lookup"><span data-stu-id="59c41-109">±5.0 × 10<sup>−324</sup> to ±1.7 × 10<sup>308</sup></span></span>|<span data-ttu-id="59c41-110">15-16 cyfr</span><span class="sxs-lookup"><span data-stu-id="59c41-110">15-16 digits</span></span>|<xref:System.Double?displayProperty=nameWithType>|

## <a name="literals"></a><span data-ttu-id="59c41-111">Literały</span><span class="sxs-lookup"><span data-stu-id="59c41-111">Literals</span></span>

<span data-ttu-id="59c41-112">Domyślnie rzeczywistym literałem po prawej stronie operatora przypisania jest traktowany jako `double`.</span><span class="sxs-lookup"><span data-stu-id="59c41-112">By default, a real numeric literal on the right side of the assignment operator is treated as `double`.</span></span> <span data-ttu-id="59c41-113">Jednak jeśli mają być traktowane jako liczba całkowita z zakresu `double`, należy użyć sufiksu d lub D, na przykład:</span><span class="sxs-lookup"><span data-stu-id="59c41-113">However, if you want an integer number to be treated as `double`, use the suffix d or D, for example:</span></span>

```csharp
double x = 3D;
```

## <a name="conversions"></a><span data-ttu-id="59c41-114">Konwersje</span><span class="sxs-lookup"><span data-stu-id="59c41-114">Conversions</span></span>

<span data-ttu-id="59c41-115">Można mieszać liczbowych typów całkowitych i zmiennoprzecinkowych w wyrażeniu.</span><span class="sxs-lookup"><span data-stu-id="59c41-115">You can mix numeric integral types and floating-point types in an expression.</span></span> <span data-ttu-id="59c41-116">W takim przypadku typów całkowitych są konwertowane na typów zmiennoprzecinkowych.</span><span class="sxs-lookup"><span data-stu-id="59c41-116">In this case, the integral types are converted to floating-point types.</span></span> <span data-ttu-id="59c41-117">Obliczanie wyrażenia odbywa się zgodnie z następującymi zasadami:</span><span class="sxs-lookup"><span data-stu-id="59c41-117">The evaluation of the expression is performed according to the following rules:</span></span>

- <span data-ttu-id="59c41-118">Po spełnieniu jednego z typów zmiennoprzecinkowych `double`, wyrażenie ma `double`, lub [bool](../../../csharp/language-reference/keywords/bool.md) w wyrażeniach relacyjnych lub Boolean.</span><span class="sxs-lookup"><span data-stu-id="59c41-118">If one of the floating-point types is `double`, the expression evaluates to `double`, or [bool](../../../csharp/language-reference/keywords/bool.md) in relational or Boolean expressions.</span></span>

- <span data-ttu-id="59c41-119">W przypadku nie `double` typ w wyrażeniu, ocenia się [float](../../../csharp/language-reference/keywords/float.md), lub [bool](../../../csharp/language-reference/keywords/bool.md) w wyrażeniach relacyjnych lub Boolean.</span><span class="sxs-lookup"><span data-stu-id="59c41-119">If there is no `double` type in the expression, it evaluates to [float](../../../csharp/language-reference/keywords/float.md), or [bool](../../../csharp/language-reference/keywords/bool.md) in relational or Boolean expressions.</span></span>

 <span data-ttu-id="59c41-120">Zmiennoprzecinkowe wyrażenie może zawierać następujące zestawy wartości:</span><span class="sxs-lookup"><span data-stu-id="59c41-120">A floating-point expression can contain the following sets of values:</span></span>

- <span data-ttu-id="59c41-121">Zero dodatnie i ujemne.</span><span class="sxs-lookup"><span data-stu-id="59c41-121">Positive and negative zero.</span></span>

- <span data-ttu-id="59c41-122">Dodatnie i ujemne nieskończoności.</span><span class="sxs-lookup"><span data-stu-id="59c41-122">Positive and negative infinity.</span></span>

- <span data-ttu-id="59c41-123">Wartość nie-liczby (NaN).</span><span class="sxs-lookup"><span data-stu-id="59c41-123">Not-a-Number value (NaN).</span></span>

- <span data-ttu-id="59c41-124">Ograniczone zestaw niezerowe wartości.</span><span class="sxs-lookup"><span data-stu-id="59c41-124">The finite set of nonzero values.</span></span>

<span data-ttu-id="59c41-125">Aby uzyskać więcej informacji na temat tych wartości, zobacz Standard IEEE binarne Floating-Point operacje arytmetyczne, dostępnych na [IEEE](https://www.ieee.org) witryny sieci Web.</span><span class="sxs-lookup"><span data-stu-id="59c41-125">For more information about these values, see IEEE Standard for Binary Floating-Point Arithmetic, available on the [IEEE](https://www.ieee.org) Web site.</span></span>

## <a name="example"></a><span data-ttu-id="59c41-126">Przykład</span><span class="sxs-lookup"><span data-stu-id="59c41-126">Example</span></span>

<span data-ttu-id="59c41-127">W poniższym przykładzie [int](../../../csharp/language-reference/keywords/int.md), [krótki](../../../csharp/language-reference/keywords/short.md), [float](../../../csharp/language-reference/keywords/float.md), a `double` są dodawane, jednocześnie zapewniając `double` wynik.</span><span class="sxs-lookup"><span data-stu-id="59c41-127">In the following example, an [int](../../../csharp/language-reference/keywords/int.md), a [short](../../../csharp/language-reference/keywords/short.md), a [float](../../../csharp/language-reference/keywords/float.md), and a `double` are added together giving a `double` result.</span></span>

[!code-csharp[csrefKeywordsTypes#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#9)]

## <a name="c-language-specification"></a><span data-ttu-id="59c41-128">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="59c41-128">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="59c41-129">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="59c41-129">See Also</span></span>

[<span data-ttu-id="59c41-130">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="59c41-130">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
[<span data-ttu-id="59c41-131">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="59c41-131">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
[<span data-ttu-id="59c41-132">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="59c41-132">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
[<span data-ttu-id="59c41-133">Tabela wartości domyślnych</span><span class="sxs-lookup"><span data-stu-id="59c41-133">Default Values Table</span></span>](../../../csharp/language-reference/keywords/default-values-table.md)  
[<span data-ttu-id="59c41-134">Tabela typów wbudowanych</span><span class="sxs-lookup"><span data-stu-id="59c41-134">Built-In Types Table</span></span>](../../../csharp/language-reference/keywords/built-in-types-table.md)  
[<span data-ttu-id="59c41-135">Tabela typów zmiennoprzecinkowych</span><span class="sxs-lookup"><span data-stu-id="59c41-135">Floating-Point Types Table</span></span>](../../../csharp/language-reference/keywords/floating-point-types-table.md)  
[<span data-ttu-id="59c41-136">Tabela niejawnych konwersji liczbowych</span><span class="sxs-lookup"><span data-stu-id="59c41-136">Implicit Numeric Conversions Table</span></span>](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)  
[<span data-ttu-id="59c41-137">Tabela jawnych konwersji liczbowych</span><span class="sxs-lookup"><span data-stu-id="59c41-137">Explicit Numeric Conversions Table</span></span>](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)  
