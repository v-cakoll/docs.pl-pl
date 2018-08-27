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
ms.openlocfilehash: 98f89ba3d79f7679b69ce10fd875b3caf69c5257
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/26/2018
ms.locfileid: "42932913"
---
# <a name="float-c-reference"></a><span data-ttu-id="f0707-102">float (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="f0707-102">float (C# Reference)</span></span>

<span data-ttu-id="f0707-103">`float` — Słowo kluczowe oznacza prosty typ, który przechowuje 32-bitowych wartości zmiennoprzecinkowych.</span><span class="sxs-lookup"><span data-stu-id="f0707-103">The `float` keyword signifies a simple type that stores 32-bit floating-point values.</span></span> <span data-ttu-id="f0707-104">W poniższej tabeli przedstawiono dokładności i przybliżony zakres `float` typu.</span><span class="sxs-lookup"><span data-stu-id="f0707-104">The following table shows the precision and approximate range for the `float` type.</span></span>

|<span data-ttu-id="f0707-105">Typ</span><span class="sxs-lookup"><span data-stu-id="f0707-105">Type</span></span>|<span data-ttu-id="f0707-106">Przybliżony zakres</span><span class="sxs-lookup"><span data-stu-id="f0707-106">Approximate range</span></span>|<span data-ttu-id="f0707-107">Dokładność</span><span class="sxs-lookup"><span data-stu-id="f0707-107">Precision</span></span>|<span data-ttu-id="f0707-108">Typ architektury .NET</span><span class="sxs-lookup"><span data-stu-id="f0707-108">.NET type</span></span>|  
|----------|-----------------------|---------------|-------------------------|  
|`float`|<span data-ttu-id="f0707-109">±1.5 x 10<sup>−45</sup> do ±3.4 x 10<sup>38</sup></span><span class="sxs-lookup"><span data-stu-id="f0707-109">±1.5 x 10<sup>−45</sup> to ±3.4 x 10<sup>38</sup></span></span>|<span data-ttu-id="f0707-110">7 cyfr</span><span class="sxs-lookup"><span data-stu-id="f0707-110">7 digits</span></span>|<xref:System.Single?displayProperty=nameWithType>|  

## <a name="literals"></a><span data-ttu-id="f0707-111">Literały</span><span class="sxs-lookup"><span data-stu-id="f0707-111">Literals</span></span>

<span data-ttu-id="f0707-112">Domyślnie, literał liczby rzeczywistej liczbowy po prawej stronie operatora przypisania jest traktowany jako [double](double.md).</span><span class="sxs-lookup"><span data-stu-id="f0707-112">By default, a real numeric literal on the right side of the assignment operator is treated as [double](double.md).</span></span> <span data-ttu-id="f0707-113">W związku z tym, aby zainicjalizować zmienną float, należy użyć sufiksu `f` lub `F`, jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="f0707-113">Therefore, to initialize a float variable, use the suffix `f` or `F`, as in the following example:</span></span>

```csharp
float x = 3.5F;
```

<span data-ttu-id="f0707-114">Jeśli nie używasz sufiks w poprzedniej deklaracji, otrzymasz błąd kompilacji, ponieważ użytkownik próbuje zapisać [double](double.md) wartością do `float` zmiennej.</span><span class="sxs-lookup"><span data-stu-id="f0707-114">If you do not use the suffix in the previous declaration, you will get a compilation error because you are trying to store a [double](double.md) value into a `float` variable.</span></span>

## <a name="conversions"></a><span data-ttu-id="f0707-115">Konwersje</span><span class="sxs-lookup"><span data-stu-id="f0707-115">Conversions</span></span>

<span data-ttu-id="f0707-116">Możesz mieszać liczbowych typów całkowitych i zmiennoprzecinkowych w wyrażeniu.</span><span class="sxs-lookup"><span data-stu-id="f0707-116">You can mix numeric integral types and floating-point types in an expression.</span></span> <span data-ttu-id="f0707-117">W tym przypadku typów całkowitych są konwertowane do typów zmiennoprzecinkowych.</span><span class="sxs-lookup"><span data-stu-id="f0707-117">In this case, the integral types are converted to floating-point types.</span></span> <span data-ttu-id="f0707-118">Obliczania wyrażenia odbywa się zgodnie z następującymi zasadami:</span><span class="sxs-lookup"><span data-stu-id="f0707-118">The evaluation of the expression is performed according to the following rules:</span></span>

- <span data-ttu-id="f0707-119">Po spełnieniu jednego z typów zmiennoprzecinkowych [double](double.md), wyrażenie ma [double](double.md), lub [bool](bool.md) w porównania relacyjne i porównania dla równości.</span><span class="sxs-lookup"><span data-stu-id="f0707-119">If one of the floating-point types is [double](double.md), the expression evaluates to [double](double.md), or to [bool](bool.md) in relational comparisons or comparisons for equality.</span></span>

- <span data-ttu-id="f0707-120">W przypadku nie [double](double.md) wpisz wyrażenie wyrażenie daje w wyniku `float`, lub [bool](bool.md) w porównania relacyjne i porównania dla równości.</span><span class="sxs-lookup"><span data-stu-id="f0707-120">If there is no [double](double.md) type in the expression, the expression evaluates to `float`, or to [bool](bool.md) in relational comparisons or comparisons for equality.</span></span>

<span data-ttu-id="f0707-121">Wyrażenie typu zmiennoprzecinkowego może zawierać następujące zestawy wartości:</span><span class="sxs-lookup"><span data-stu-id="f0707-121">A floating-point expression can contain the following sets of values:</span></span>

- <span data-ttu-id="f0707-122">Zero dodatnie i ujemne</span><span class="sxs-lookup"><span data-stu-id="f0707-122">Positive and negative zero</span></span>

- <span data-ttu-id="f0707-123">Dodatnie i ujemne nieskończoność.</span><span class="sxs-lookup"><span data-stu-id="f0707-123">Positive and negative infinity</span></span>

- <span data-ttu-id="f0707-124">Wartość nie a liczbą (NaN)</span><span class="sxs-lookup"><span data-stu-id="f0707-124">Not-a-Number value (NaN)</span></span>

- <span data-ttu-id="f0707-125">Ograniczone zbiór wartości wartość różną od zera</span><span class="sxs-lookup"><span data-stu-id="f0707-125">The finite set of nonzero values</span></span>

<span data-ttu-id="f0707-126">Aby uzyskać więcej informacji na temat tych wartości, zobacz Standard IEEE binarne zmiennopozycyjna operacje arytmetyczne, dostępne na [IEEE](http://www.ieee.org) witryny sieci Web.</span><span class="sxs-lookup"><span data-stu-id="f0707-126">For more information about these values, see IEEE Standard for Binary Floating-Point Arithmetic, available on the [IEEE](http://www.ieee.org) website.</span></span>

## <a name="example"></a><span data-ttu-id="f0707-127">Przykład</span><span class="sxs-lookup"><span data-stu-id="f0707-127">Example</span></span>

<span data-ttu-id="f0707-128">W poniższym przykładzie [int](int.md), [krótki](short.md), a `float` są zawarte w wyrażeniu matematycznym, zapewniając `float` wynik.</span><span class="sxs-lookup"><span data-stu-id="f0707-128">In the following example, an [int](int.md), a [short](short.md), and a `float` are included in a mathematical expression giving a `float` result.</span></span> <span data-ttu-id="f0707-129">(Należy pamiętać, że `float` jest aliasem dla <xref:System.Single?displayProperty=nameWithType> typu.) Zwróć uwagę, że ma nie [double](double.md) w wyrażeniu.</span><span class="sxs-lookup"><span data-stu-id="f0707-129">(Remember that `float` is an alias for the <xref:System.Single?displayProperty=nameWithType> type.) Notice that there is no [double](double.md) in the expression.</span></span>

[!code-csharp[csrefKeywordsTypes#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#13)]

## <a name="c-language-specification"></a><span data-ttu-id="f0707-130">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="f0707-130">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="f0707-131">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f0707-131">See also</span></span>

- <xref:System.Single>  
- [<span data-ttu-id="f0707-132">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="f0707-132">C# Reference</span></span>](../index.md)  
- [<span data-ttu-id="f0707-133">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="f0707-133">C# Programming Guide</span></span>](../../programming-guide/index.md)  
- [<span data-ttu-id="f0707-134">Rzutowanie i konwersje typów</span><span class="sxs-lookup"><span data-stu-id="f0707-134">Casting and Type Conversions</span></span>](../../programming-guide/types/casting-and-type-conversions.md)  
- [<span data-ttu-id="f0707-135">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="f0707-135">C# Keywords</span></span>](index.md)  
- [<span data-ttu-id="f0707-136">Tabela typów całkowitych</span><span class="sxs-lookup"><span data-stu-id="f0707-136">Integral Types Table</span></span>](integral-types-table.md)  
- [<span data-ttu-id="f0707-137">Tabela typów wbudowanych</span><span class="sxs-lookup"><span data-stu-id="f0707-137">Built-In Types Table</span></span>](built-in-types-table.md)  
- [<span data-ttu-id="f0707-138">Tabela niejawnych konwersji liczbowych</span><span class="sxs-lookup"><span data-stu-id="f0707-138">Implicit Numeric Conversions Table</span></span>](implicit-numeric-conversions-table.md)  
- [<span data-ttu-id="f0707-139">Tabela jawnych konwersji liczbowych</span><span class="sxs-lookup"><span data-stu-id="f0707-139">Explicit Numeric Conversions Table</span></span>](explicit-numeric-conversions-table.md)  