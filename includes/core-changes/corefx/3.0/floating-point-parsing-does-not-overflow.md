---
ms.openlocfilehash: 30580b3fde5b8a99862896bb7d31c6c4024f97e8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "74568097"
---
### <a name="floating-point-parsing-operations-no-longer-fail-or-throw-an-overflowexception"></a><span data-ttu-id="4c8c4-101">Operacje analizy zmiennoprzecinkowych nie są już inwakczliwe ani nie mogą być powodem do przepełnieniaWyjątek</span><span class="sxs-lookup"><span data-stu-id="4c8c4-101">Floating-point parsing operations no longer fail or throw an OverflowException</span></span>

<span data-ttu-id="4c8c4-102">Metody analizy zmiennoprzecinkowej nie <xref:System.OverflowException> są `false` już rzuty lub zwracane podczas analizowania ciągu, którego wartość liczbowa znajduje się poza zakresem <xref:System.Single> typu zmiennoprzecinkowego. <xref:System.Double></span><span class="sxs-lookup"><span data-stu-id="4c8c4-102">The floating-point parsing methods no longer throw an <xref:System.OverflowException> or return `false` when they parse a string whose numeric value is outside the range of the <xref:System.Single> or <xref:System.Double> floating-point type.</span></span>

#### <a name="change-description"></a><span data-ttu-id="4c8c4-103">Zmień opis</span><span class="sxs-lookup"><span data-stu-id="4c8c4-103">Change description</span></span>

<span data-ttu-id="4c8c4-104">W .NET Core 2.2 i <xref:System.Double.Parse%2A?displayProperty=nameWithType> wcześniejszych wersjach i <xref:System.Single.Parse%2A?displayProperty=nameWithType> metody wyrzucając <xref:System.OverflowException> dla wartości, które wykraczają poza zakres ich odpowiedniego typu.</span><span class="sxs-lookup"><span data-stu-id="4c8c4-104">In .NET Core 2.2 and earlier versions, the <xref:System.Double.Parse%2A?displayProperty=nameWithType> and <xref:System.Single.Parse%2A?displayProperty=nameWithType> methods throw an <xref:System.OverflowException> for values that outside the range of their respective type.</span></span> <span data-ttu-id="4c8c4-105">I <xref:System.Double.TryParse%2A?displayProperty=nameWithType> <xref:System.Single.TryParse%2A?displayProperty=nameWithType> metody zwracają `false` dla reprezentacji ciągów wartości liczbowych poza zakresem.</span><span class="sxs-lookup"><span data-stu-id="4c8c4-105">The <xref:System.Double.TryParse%2A?displayProperty=nameWithType> and <xref:System.Single.TryParse%2A?displayProperty=nameWithType> methods return `false` for the string representations of out-of-range numeric values.</span></span>

<span data-ttu-id="4c8c4-106">Począwszy od .NET Core <xref:System.Double.Parse%2A?displayProperty=nameWithType>3.0, , <xref:System.Double.TryParse%2A?displayProperty=nameWithType>, , <xref:System.Single.Parse%2A?displayProperty=nameWithType>i <xref:System.Single.TryParse%2A?displayProperty=nameWithType> metody nie zawiodą już podczas analizowania ciągów liczbowych poza zakresem.</span><span class="sxs-lookup"><span data-stu-id="4c8c4-106">Starting with .NET Core 3.0, the <xref:System.Double.Parse%2A?displayProperty=nameWithType>, <xref:System.Double.TryParse%2A?displayProperty=nameWithType>, <xref:System.Single.Parse%2A?displayProperty=nameWithType>, and <xref:System.Single.TryParse%2A?displayProperty=nameWithType> methods no longer fail when parsing out-of-range numeric strings.</span></span> <span data-ttu-id="4c8c4-107">Zamiast tego <xref:System.Double> metody analizy zwracają <xref:System.Double.PositiveInfinity?displayProperty=nameWithType> wartości, <xref:System.Double.MaxValue?displayProperty=nameWithType>które przekraczają <xref:System.Double.NegativeInfinity?displayProperty=nameWithType> , i zwracają <xref:System.Double.MinValue?displayProperty=nameWithType>dla wartości, które są mniejsze niż .</span><span class="sxs-lookup"><span data-stu-id="4c8c4-107">Instead, the <xref:System.Double> parsing methods return <xref:System.Double.PositiveInfinity?displayProperty=nameWithType> for values that exceed <xref:System.Double.MaxValue?displayProperty=nameWithType>, and they return <xref:System.Double.NegativeInfinity?displayProperty=nameWithType> for values that are less than <xref:System.Double.MinValue?displayProperty=nameWithType>.</span></span> <span data-ttu-id="4c8c4-108">Podobnie metody <xref:System.Single> analizy zwracają <xref:System.Single.PositiveInfinity?displayProperty=nameWithType> wartości, które przekraczają <xref:System.Single.MaxValue?displayProperty=nameWithType>, i <xref:System.Single.NegativeInfinity?displayProperty=nameWithType> zwracają dla wartości, które są mniejsze niż <xref:System.Single.MinValue?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="4c8c4-108">Similarly, the <xref:System.Single> parsing methods return <xref:System.Single.PositiveInfinity?displayProperty=nameWithType> for values that exceed <xref:System.Single.MaxValue?displayProperty=nameWithType>, and they return <xref:System.Single.NegativeInfinity?displayProperty=nameWithType> for values that are less than <xref:System.Single.MinValue?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="4c8c4-109">Zmiana ta została wmazana w celu poprawy zgodności ieee 754:2008.</span><span class="sxs-lookup"><span data-stu-id="4c8c4-109">This change was made for improved IEEE 754:2008 compliance.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="4c8c4-110">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="4c8c4-110">Version introduced</span></span>

<span data-ttu-id="4c8c4-111">3.0</span><span class="sxs-lookup"><span data-stu-id="4c8c4-111">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="4c8c4-112">Zalecana akcja</span><span class="sxs-lookup"><span data-stu-id="4c8c4-112">Recommended action</span></span>

<span data-ttu-id="4c8c4-113">Ta zmiana może mieć wpływ na kod na dwa sposoby:</span><span class="sxs-lookup"><span data-stu-id="4c8c4-113">This change can affect your code in either of two ways:</span></span>

- <span data-ttu-id="4c8c4-114">Kod zależy od programu <xref:System.OverflowException> obsługi do wykonania po wystąpieniu przepełnienia.</span><span class="sxs-lookup"><span data-stu-id="4c8c4-114">Your code depends on the handler for the <xref:System.OverflowException> to execute when an overflow occurs.</span></span> <span data-ttu-id="4c8c4-115">W takim przypadku należy `catch` usunąć instrukcję i umieścić `If` niezbędny <xref:System.Double.IsInfinity%2A?displayProperty=nameWithType> kod <xref:System.Single.IsInfinity%2A?displayProperty=nameWithType> `true`w instrukcji, która sprawdza, czy jest .</span><span class="sxs-lookup"><span data-stu-id="4c8c4-115">In this case, you should remove the `catch` statement and place any necessary code in an `If` statement that tests whether <xref:System.Double.IsInfinity%2A?displayProperty=nameWithType> or <xref:System.Single.IsInfinity%2A?displayProperty=nameWithType> is `true`.</span></span>

- <span data-ttu-id="4c8c4-116">Kod zakłada, że wartości zmiennoprzecinkowe nie `Infinity`są .</span><span class="sxs-lookup"><span data-stu-id="4c8c4-116">Your code assumes that floating-point values are not `Infinity`.</span></span> <span data-ttu-id="4c8c4-117">W takim przypadku należy dodać kod niezbędny do sprawdzenia `PositiveInfinity` `NegativeInfinity`wartości zmiennoprzecinkowych i .</span><span class="sxs-lookup"><span data-stu-id="4c8c4-117">In this case, you should add the necessary code to check for floating-point values of `PositiveInfinity` and `NegativeInfinity`.</span></span>

#### <a name="category"></a><span data-ttu-id="4c8c4-118">Kategoria</span><span class="sxs-lookup"><span data-stu-id="4c8c4-118">Category</span></span>

<span data-ttu-id="4c8c4-119">CoreFx</span><span class="sxs-lookup"><span data-stu-id="4c8c4-119">CoreFx</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="4c8c4-120">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="4c8c4-120">Affected APIs</span></span>

- <xref:System.Double.Parse%2A?displayProperty=nameWithType>
- <xref:System.Double.TryParse%2A?displayProperty=nameWithType>
- <xref:System.Single.Parse%2A?displayProperty=nameWithType>
- <xref:System.Single.TryParse%2A?displayProperty=nameWithType>

<!--

### Affected APIs

- `Overload:System.Double.Parse`
- `Overload:System.Double.TryParse`
- `Overload:System.Single.Parse`
- `Overload:System.Single.TryParse`

-->
