---
ms.openlocfilehash: 87ada29e70a94c39e7ffb74767b99d49c52444af
ms.sourcegitcommit: 348bb052d5cef109a61a3d5253faa5d7167d55ac
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2020
ms.locfileid: "82021642"
---
### <a name="floating-point-parsing-operations-no-longer-fail-or-throw-an-overflowexception"></a><span data-ttu-id="e1af3-101">Operacje analizowania zmiennoprzecinkowego nie są już nieudane lub nie mogą paść za przepełnienie</span><span class="sxs-lookup"><span data-stu-id="e1af3-101">Floating-point parsing operations no longer fail or throw an OverflowException</span></span>

<span data-ttu-id="e1af3-102">Metody analizy zmiennoprzecinowej nie <xref:System.OverflowException> są `false` już rzutować ani zwracać podczas analizowania ciągu, <xref:System.Single> <xref:System.Double> którego wartość liczbowa znajduje się poza zakresem typu zmiennoprzecinkowego lub zmiennoprzecinkowego.</span><span class="sxs-lookup"><span data-stu-id="e1af3-102">The floating-point parsing methods no longer throw an <xref:System.OverflowException> or return `false` when they parse a string whose numeric value is outside the range of the <xref:System.Single> or <xref:System.Double> floating-point type.</span></span>

#### <a name="change-description"></a><span data-ttu-id="e1af3-103">Zmień opis</span><span class="sxs-lookup"><span data-stu-id="e1af3-103">Change description</span></span>

<span data-ttu-id="e1af3-104">W .NET Core 2.2 i <xref:System.Double.Parse%2A?displayProperty=nameWithType> <xref:System.Single.Parse%2A?displayProperty=nameWithType> wcześniejszych wersjach i metody i rzucać <xref:System.OverflowException> dla wartości, które poza zakresem ich odpowiedniego typu.</span><span class="sxs-lookup"><span data-stu-id="e1af3-104">In .NET Core 2.2 and earlier versions, the <xref:System.Double.Parse%2A?displayProperty=nameWithType> and <xref:System.Single.Parse%2A?displayProperty=nameWithType> methods throw an <xref:System.OverflowException> for values that outside the range of their respective type.</span></span> <span data-ttu-id="e1af3-105">I <xref:System.Double.TryParse%2A?displayProperty=nameWithType> <xref:System.Single.TryParse%2A?displayProperty=nameWithType> metody `false` zwracają dla reprezentacji ciągów wartości liczbowych poza zakresem.</span><span class="sxs-lookup"><span data-stu-id="e1af3-105">The <xref:System.Double.TryParse%2A?displayProperty=nameWithType> and <xref:System.Single.TryParse%2A?displayProperty=nameWithType> methods return `false` for the string representations of out-of-range numeric values.</span></span>

<span data-ttu-id="e1af3-106">Począwszy od .NET Core <xref:System.Double.Parse%2A?displayProperty=nameWithType>3.0, <xref:System.Double.TryParse%2A?displayProperty=nameWithType>, , <xref:System.Single.Parse%2A?displayProperty=nameWithType>i <xref:System.Single.TryParse%2A?displayProperty=nameWithType> metody nie są już zawodzą podczas analizowania ciągów liczbowych poza zakresem.</span><span class="sxs-lookup"><span data-stu-id="e1af3-106">Starting with .NET Core 3.0, the <xref:System.Double.Parse%2A?displayProperty=nameWithType>, <xref:System.Double.TryParse%2A?displayProperty=nameWithType>, <xref:System.Single.Parse%2A?displayProperty=nameWithType>, and <xref:System.Single.TryParse%2A?displayProperty=nameWithType> methods no longer fail when parsing out-of-range numeric strings.</span></span> <span data-ttu-id="e1af3-107">Zamiast tego <xref:System.Double> metody analizy zwracają <xref:System.Double.PositiveInfinity?displayProperty=nameWithType> wartości, <xref:System.Double.MaxValue?displayProperty=nameWithType>które przekraczają <xref:System.Double.NegativeInfinity?displayProperty=nameWithType> , i zwracają <xref:System.Double.MinValue?displayProperty=nameWithType>dla wartości, które są mniejsze niż .</span><span class="sxs-lookup"><span data-stu-id="e1af3-107">Instead, the <xref:System.Double> parsing methods return <xref:System.Double.PositiveInfinity?displayProperty=nameWithType> for values that exceed <xref:System.Double.MaxValue?displayProperty=nameWithType>, and they return <xref:System.Double.NegativeInfinity?displayProperty=nameWithType> for values that are less than <xref:System.Double.MinValue?displayProperty=nameWithType>.</span></span> <span data-ttu-id="e1af3-108">Podobnie metody <xref:System.Single> analizy <xref:System.Single.PositiveInfinity?displayProperty=nameWithType> zwracają wartości, które <xref:System.Single.MaxValue?displayProperty=nameWithType>przekraczają i <xref:System.Single.NegativeInfinity?displayProperty=nameWithType> zwracają wartości, które <xref:System.Single.MinValue?displayProperty=nameWithType>są mniejsze niż .</span><span class="sxs-lookup"><span data-stu-id="e1af3-108">Similarly, the <xref:System.Single> parsing methods return <xref:System.Single.PositiveInfinity?displayProperty=nameWithType> for values that exceed <xref:System.Single.MaxValue?displayProperty=nameWithType>, and they return <xref:System.Single.NegativeInfinity?displayProperty=nameWithType> for values that are less than <xref:System.Single.MinValue?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="e1af3-109">Ta zmiana została wywłyszona w celu poprawy zgodności z IEEE 754:2008.</span><span class="sxs-lookup"><span data-stu-id="e1af3-109">This change was made for improved IEEE 754:2008 compliance.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="e1af3-110">Wprowadzono wersję</span><span class="sxs-lookup"><span data-stu-id="e1af3-110">Version introduced</span></span>

<span data-ttu-id="e1af3-111">3.0</span><span class="sxs-lookup"><span data-stu-id="e1af3-111">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="e1af3-112">Zalecana akcja</span><span class="sxs-lookup"><span data-stu-id="e1af3-112">Recommended action</span></span>

<span data-ttu-id="e1af3-113">Ta zmiana może mieć wpływ na kod na jeden z dwóch sposobów:</span><span class="sxs-lookup"><span data-stu-id="e1af3-113">This change can affect your code in either of two ways:</span></span>

- <span data-ttu-id="e1af3-114">Kod zależy od programu <xref:System.OverflowException> obsługi do wykonania, gdy wystąpi przepełnienie.</span><span class="sxs-lookup"><span data-stu-id="e1af3-114">Your code depends on the handler for the <xref:System.OverflowException> to execute when an overflow occurs.</span></span> <span data-ttu-id="e1af3-115">W takim przypadku należy `catch` usunąć instrukcję i umieścić `If` niezbędny <xref:System.Double.IsInfinity%2A?displayProperty=nameWithType> kod <xref:System.Single.IsInfinity%2A?displayProperty=nameWithType> `true`w instrukcji, która sprawdza, czy jest .</span><span class="sxs-lookup"><span data-stu-id="e1af3-115">In this case, you should remove the `catch` statement and place any necessary code in an `If` statement that tests whether <xref:System.Double.IsInfinity%2A?displayProperty=nameWithType> or <xref:System.Single.IsInfinity%2A?displayProperty=nameWithType> is `true`.</span></span>

- <span data-ttu-id="e1af3-116">Kod zakłada, że wartości zmiennoprzecinkowe nie `Infinity`są .</span><span class="sxs-lookup"><span data-stu-id="e1af3-116">Your code assumes that floating-point values are not `Infinity`.</span></span> <span data-ttu-id="e1af3-117">W takim przypadku należy dodać kod niezbędny do sprawdzenia `PositiveInfinity` `NegativeInfinity`wartości zmiennoprzecinkowych i .</span><span class="sxs-lookup"><span data-stu-id="e1af3-117">In this case, you should add the necessary code to check for floating-point values of `PositiveInfinity` and `NegativeInfinity`.</span></span>

#### <a name="category"></a><span data-ttu-id="e1af3-118">Kategoria</span><span class="sxs-lookup"><span data-stu-id="e1af3-118">Category</span></span>

<span data-ttu-id="e1af3-119">Podstawowe biblioteki .NET</span><span class="sxs-lookup"><span data-stu-id="e1af3-119">Core .NET libraries</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="e1af3-120">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="e1af3-120">Affected APIs</span></span>

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
