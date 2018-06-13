---
title: float (odwołanie w C#)
ms.date: 07/20/2015
f1_keywords:
- float
- float_CSharpKeyword
helpviewer_keywords:
- float keyword [C#]
- floating-point numbers [C#], float keyword
ms.assetid: 1e77db7b-dedb-48b7-8dd1-b055e96a9258
ms.openlocfilehash: edeed59da26c7007b23e1eec8c05fbd2e6d34d36
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33219248"
---
# <a name="float-c-reference"></a><span data-ttu-id="8a985-102">float (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="8a985-102">float (C# Reference)</span></span>
<span data-ttu-id="8a985-103">`float` — Słowo kluczowe oznacza typu prostego, która przechowuje 32-bitowych wartości zmiennoprzecinkowych.</span><span class="sxs-lookup"><span data-stu-id="8a985-103">The `float` keyword signifies a simple type that stores 32-bit floating-point values.</span></span> <span data-ttu-id="8a985-104">W poniższej tabeli przedstawiono dokładność i zakres przybliżonej `float` typu.</span><span class="sxs-lookup"><span data-stu-id="8a985-104">The following table shows the precision and approximate range for the `float` type.</span></span>  
  
|<span data-ttu-id="8a985-105">Typ</span><span class="sxs-lookup"><span data-stu-id="8a985-105">Type</span></span>|<span data-ttu-id="8a985-106">Zakresie</span><span class="sxs-lookup"><span data-stu-id="8a985-106">Approximate range</span></span>|<span data-ttu-id="8a985-107">Dokładność</span><span class="sxs-lookup"><span data-stu-id="8a985-107">Precision</span></span>|<span data-ttu-id="8a985-108">Typ programu .NET Framework</span><span class="sxs-lookup"><span data-stu-id="8a985-108">.NET Framework type</span></span>|  
|----------|-----------------------|---------------|-------------------------|  
|`float`|<span data-ttu-id="8a985-109">-3,4 x 10<sup>38</sup>do + 3,4 x 10<sup>38</sup></span><span class="sxs-lookup"><span data-stu-id="8a985-109">-3.4 × 10<sup>38</sup>to +3.4 × 10<sup>38</sup></span></span>|<span data-ttu-id="8a985-110">7 cyfr</span><span class="sxs-lookup"><span data-stu-id="8a985-110">7 digits</span></span>|<xref:System.Single?displayProperty=nameWithType>|  
  
## <a name="literals"></a><span data-ttu-id="8a985-111">Literały</span><span class="sxs-lookup"><span data-stu-id="8a985-111">Literals</span></span>  
 <span data-ttu-id="8a985-112">Domyślnie rzeczywistym literałem po prawej stronie operatora przypisania jest traktowany jako [podwójne](double.md).</span><span class="sxs-lookup"><span data-stu-id="8a985-112">By default, a real numeric literal on the right side of the assignment operator is treated as [double](double.md).</span></span> <span data-ttu-id="8a985-113">W związku z tym można zainicjować zmiennej typu float, używają sufiksu `f` lub `F`, jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="8a985-113">Therefore, to initialize a float variable, use the suffix `f` or `F`, as in the following example:</span></span>  
  
```csharp
float x = 3.5F;  
```
  
 <span data-ttu-id="8a985-114">Jeśli nie używasz sufiks w poprzedniej deklaracji, otrzymasz błąd kompilacji, ponieważ chcesz przechowywać [podwójne](double.md) wartości do `float` zmiennej.</span><span class="sxs-lookup"><span data-stu-id="8a985-114">If you do not use the suffix in the previous declaration, you will get a compilation error because you are trying to store a [double](double.md) value into a `float` variable.</span></span>  
  
## <a name="conversions"></a><span data-ttu-id="8a985-115">Konwersje</span><span class="sxs-lookup"><span data-stu-id="8a985-115">Conversions</span></span>  
 <span data-ttu-id="8a985-116">Można mieszać liczbowych typów całkowitych i zmiennoprzecinkowych w wyrażeniu.</span><span class="sxs-lookup"><span data-stu-id="8a985-116">You can mix numeric integral types and floating-point types in an expression.</span></span> <span data-ttu-id="8a985-117">W takim przypadku typów całkowitych są konwertowane na typów zmiennoprzecinkowych.</span><span class="sxs-lookup"><span data-stu-id="8a985-117">In this case, the integral types are converted to floating-point types.</span></span> <span data-ttu-id="8a985-118">Obliczanie wyrażenia odbywa się zgodnie z następującymi zasadami:</span><span class="sxs-lookup"><span data-stu-id="8a985-118">The evaluation of the expression is performed according to the following rules:</span></span>  
  
-   <span data-ttu-id="8a985-119">Po spełnieniu jednego z typów zmiennoprzecinkowych [podwójne](double.md), wyrażenie ma [podwójne](double.md) lub [bool](bool.md) w wyrażeniach relacyjnych lub Boolean.</span><span class="sxs-lookup"><span data-stu-id="8a985-119">If one of the floating-point types is [double](double.md), the expression evaluates to [double](double.md) or [bool](bool.md) in relational or Boolean expressions.</span></span>  
  
-   <span data-ttu-id="8a985-120">W przypadku nie [podwójne](double.md) typ w wyrażeniu wyrażenie daje w wyniku `float` lub [bool](bool.md) w wyrażeniach relacyjnych lub Boolean.</span><span class="sxs-lookup"><span data-stu-id="8a985-120">If there is no [double](double.md) type in the expression, the expression evaluates to `float` or [bool](bool.md) in relational or Boolean expressions.</span></span>  
  
 <span data-ttu-id="8a985-121">Zmiennoprzecinkowe wyrażenie może zawierać następujące zestawy wartości:</span><span class="sxs-lookup"><span data-stu-id="8a985-121">A floating-point expression can contain the following sets of values:</span></span>  
  
-   <span data-ttu-id="8a985-122">Zero dodatnie i ujemne</span><span class="sxs-lookup"><span data-stu-id="8a985-122">Positive and negative zero</span></span>  
  
-   <span data-ttu-id="8a985-123">Dodatnie i ujemne infinity</span><span class="sxs-lookup"><span data-stu-id="8a985-123">Positive and negative infinity</span></span>  
  
-   <span data-ttu-id="8a985-124">Wartość nie-liczby (NaN)</span><span class="sxs-lookup"><span data-stu-id="8a985-124">Not-a-Number value (NaN)</span></span>  
  
-   <span data-ttu-id="8a985-125">Ograniczone zbiór niezerowe wartości</span><span class="sxs-lookup"><span data-stu-id="8a985-125">The finite set of nonzero values</span></span>  
  
 <span data-ttu-id="8a985-126">Aby uzyskać więcej informacji na temat tych wartości, zobacz Standard IEEE binarne Floating-Point operacje arytmetyczne, dostępnych na [IEEE](http://www.ieee.org) witryny sieci Web.</span><span class="sxs-lookup"><span data-stu-id="8a985-126">For more information about these values, see IEEE Standard for Binary Floating-Point Arithmetic, available on the [IEEE](http://www.ieee.org) Web site.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8a985-127">Przykład</span><span class="sxs-lookup"><span data-stu-id="8a985-127">Example</span></span>  
 <span data-ttu-id="8a985-128">W poniższym przykładzie [int](int.md), [krótki](short.md), a `float` są uwzględnione w wyrażeniu matematycznym nadanie `float` wynik.</span><span class="sxs-lookup"><span data-stu-id="8a985-128">In the following example, an [int](int.md), a [short](short.md), and a `float` are included in a mathematical expression giving a `float` result.</span></span> <span data-ttu-id="8a985-129">(Należy pamiętać, że `float` jest aliasem <xref:System.Single?displayProperty=nameWithType> typu.) Należy zauważyć, że istnieje nie [podwójne](double.md) w wyrażeniu.</span><span class="sxs-lookup"><span data-stu-id="8a985-129">(Remember that `float` is an alias for the <xref:System.Single?displayProperty=nameWithType> type.) Notice that there is no [double](double.md) in the expression.</span></span>  
  
 [!code-csharp[csrefKeywordsTypes#13](../../../csharp/language-reference/keywords/codesnippet/CSharp/float_1.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="8a985-130">Specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="8a985-130">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="8a985-131">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8a985-131">See Also</span></span>  
 <xref:System.Single>  
 [<span data-ttu-id="8a985-132">Odwołanie w C#</span><span class="sxs-lookup"><span data-stu-id="8a985-132">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="8a985-133">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="8a985-133">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="8a985-134">Rzutowanie i konwersje typów</span><span class="sxs-lookup"><span data-stu-id="8a985-134">Casting and Type Conversions</span></span>](../../../csharp/programming-guide/types/casting-and-type-conversions.md)  
 [<span data-ttu-id="8a985-135">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="8a985-135">C# Keywords</span></span>](index.md)  
 [<span data-ttu-id="8a985-136">Tabela typów całkowitych</span><span class="sxs-lookup"><span data-stu-id="8a985-136">Integral Types Table</span></span>](integral-types-table.md)  
 [<span data-ttu-id="8a985-137">Tabela typów wbudowanych</span><span class="sxs-lookup"><span data-stu-id="8a985-137">Built-In Types Table</span></span>](built-in-types-table.md)  
 [<span data-ttu-id="8a985-138">Tabela niejawnych konwersji liczbowych</span><span class="sxs-lookup"><span data-stu-id="8a985-138">Implicit Numeric Conversions Table</span></span>](implicit-numeric-conversions-table.md)  
 [<span data-ttu-id="8a985-139">Tabela jawnych konwersji liczbowych</span><span class="sxs-lookup"><span data-stu-id="8a985-139">Explicit Numeric Conversions Table</span></span>](explicit-numeric-conversions-table.md)
