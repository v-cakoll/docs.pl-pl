---
ms.openlocfilehash: 935d9b2368ea4a0eeca7943dcbd584d24d2a6633
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/20/2020
ms.locfileid: "83721320"
---
### <a name="floating-point-parsing-operations-no-longer-fail-or-throw-an-overflowexception"></a><span data-ttu-id="04a72-101">Operacje analizowania zmiennoprzecinkowe nie będą już kończyć się niepowodzeniem lub nie generują wyjątku overflow</span><span class="sxs-lookup"><span data-stu-id="04a72-101">Floating-point parsing operations no longer fail or throw an OverflowException</span></span>

<span data-ttu-id="04a72-102">Metody analizy zmiennoprzecinkowej nie generują już ani nie <xref:System.OverflowException> zwracają `false` podczas analizowania ciągu, którego wartość liczbowa jest spoza zakresu <xref:System.Single> lub <xref:System.Double> typu zmiennoprzecinkowego.</span><span class="sxs-lookup"><span data-stu-id="04a72-102">The floating-point parsing methods no longer throw an <xref:System.OverflowException> or return `false` when they parse a string whose numeric value is outside the range of the <xref:System.Single> or <xref:System.Double> floating-point type.</span></span>

#### <a name="change-description"></a><span data-ttu-id="04a72-103">Zmień opis</span><span class="sxs-lookup"><span data-stu-id="04a72-103">Change description</span></span>

<span data-ttu-id="04a72-104">W programie .NET Core 2,2 i starszych wersjach <xref:System.Double.Parse%2A?displayProperty=nameWithType> metody i <xref:System.Single.Parse%2A?displayProperty=nameWithType> generują <xref:System.OverflowException> dla wartości, które wykraczają poza zakres odpowiedniego typu.</span><span class="sxs-lookup"><span data-stu-id="04a72-104">In .NET Core 2.2 and earlier versions, the <xref:System.Double.Parse%2A?displayProperty=nameWithType> and <xref:System.Single.Parse%2A?displayProperty=nameWithType> methods throw an <xref:System.OverflowException> for values that outside the range of their respective type.</span></span> <span data-ttu-id="04a72-105"><xref:System.Double.TryParse%2A?displayProperty=nameWithType>Metody i <xref:System.Single.TryParse%2A?displayProperty=nameWithType> zwracają `false` dla reprezentacji ciągów wartości liczbowych poza zakresem.</span><span class="sxs-lookup"><span data-stu-id="04a72-105">The <xref:System.Double.TryParse%2A?displayProperty=nameWithType> and <xref:System.Single.TryParse%2A?displayProperty=nameWithType> methods return `false` for the string representations of out-of-range numeric values.</span></span>

<span data-ttu-id="04a72-106">Począwszy od platformy .NET Core 3,0, <xref:System.Double.Parse%2A?displayProperty=nameWithType> <xref:System.Double.TryParse%2A?displayProperty=nameWithType> metody,, <xref:System.Single.Parse%2A?displayProperty=nameWithType> i <xref:System.Single.TryParse%2A?displayProperty=nameWithType> nie kończą się niepowodzeniem podczas analizowania ciągów liczbowych poza zakresem.</span><span class="sxs-lookup"><span data-stu-id="04a72-106">Starting with .NET Core 3.0, the <xref:System.Double.Parse%2A?displayProperty=nameWithType>, <xref:System.Double.TryParse%2A?displayProperty=nameWithType>, <xref:System.Single.Parse%2A?displayProperty=nameWithType>, and <xref:System.Single.TryParse%2A?displayProperty=nameWithType> methods no longer fail when parsing out-of-range numeric strings.</span></span> <span data-ttu-id="04a72-107">Zamiast tego <xref:System.Double> metody analizy zwracają <xref:System.Double.PositiveInfinity?displayProperty=nameWithType> wartości, które przekraczają <xref:System.Double.MaxValue?displayProperty=nameWithType> , i zwracają <xref:System.Double.NegativeInfinity?displayProperty=nameWithType> dla wartości, które są mniejsze niż <xref:System.Double.MinValue?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="04a72-107">Instead, the <xref:System.Double> parsing methods return <xref:System.Double.PositiveInfinity?displayProperty=nameWithType> for values that exceed <xref:System.Double.MaxValue?displayProperty=nameWithType>, and they return <xref:System.Double.NegativeInfinity?displayProperty=nameWithType> for values that are less than <xref:System.Double.MinValue?displayProperty=nameWithType>.</span></span> <span data-ttu-id="04a72-108">Podobnie <xref:System.Single> metody analizy zwracają wartości, <xref:System.Single.PositiveInfinity?displayProperty=nameWithType> które przekraczają <xref:System.Single.MaxValue?displayProperty=nameWithType> , i zwracają <xref:System.Single.NegativeInfinity?displayProperty=nameWithType> dla wartości, które są mniejsze niż <xref:System.Single.MinValue?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="04a72-108">Similarly, the <xref:System.Single> parsing methods return <xref:System.Single.PositiveInfinity?displayProperty=nameWithType> for values that exceed <xref:System.Single.MaxValue?displayProperty=nameWithType>, and they return <xref:System.Single.NegativeInfinity?displayProperty=nameWithType> for values that are less than <xref:System.Single.MinValue?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="04a72-109">Ta zmiana została wprowadzona w celu uzyskania ulepszonej zgodności ze standardem IEEE 754:2008.</span><span class="sxs-lookup"><span data-stu-id="04a72-109">This change was made for improved IEEE 754:2008 compliance.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="04a72-110">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="04a72-110">Version introduced</span></span>

<span data-ttu-id="04a72-111">3.0</span><span class="sxs-lookup"><span data-stu-id="04a72-111">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="04a72-112">Zalecana akcja</span><span class="sxs-lookup"><span data-stu-id="04a72-112">Recommended action</span></span>

<span data-ttu-id="04a72-113">Ta zmiana może mieć wpływ na kod na jeden z dwóch sposobów:</span><span class="sxs-lookup"><span data-stu-id="04a72-113">This change can affect your code in either of two ways:</span></span>

- <span data-ttu-id="04a72-114">Kod zależy od programu obsługi <xref:System.OverflowException> do wykonania, gdy występuje przepełnienie.</span><span class="sxs-lookup"><span data-stu-id="04a72-114">Your code depends on the handler for the <xref:System.OverflowException> to execute when an overflow occurs.</span></span> <span data-ttu-id="04a72-115">W takim przypadku należy usunąć `catch` instrukcję i umieścić dowolny kod w `If` instrukcji, która sprawdza, czy <xref:System.Double.IsInfinity%2A?displayProperty=nameWithType> lub <xref:System.Single.IsInfinity%2A?displayProperty=nameWithType> jest `true` .</span><span class="sxs-lookup"><span data-stu-id="04a72-115">In this case, you should remove the `catch` statement and place any necessary code in an `If` statement that tests whether <xref:System.Double.IsInfinity%2A?displayProperty=nameWithType> or <xref:System.Single.IsInfinity%2A?displayProperty=nameWithType> is `true`.</span></span>

- <span data-ttu-id="04a72-116">W kodzie założono, że wartości zmiennoprzecinkowe nie są `Infinity` .</span><span class="sxs-lookup"><span data-stu-id="04a72-116">Your code assumes that floating-point values are not `Infinity`.</span></span> <span data-ttu-id="04a72-117">W takim przypadku należy dodać wymagany kod w celu sprawdzenia wartości zmiennoprzecinkowych `PositiveInfinity` i `NegativeInfinity` .</span><span class="sxs-lookup"><span data-stu-id="04a72-117">In this case, you should add the necessary code to check for floating-point values of `PositiveInfinity` and `NegativeInfinity`.</span></span>

#### <a name="category"></a><span data-ttu-id="04a72-118">Kategoria</span><span class="sxs-lookup"><span data-stu-id="04a72-118">Category</span></span>

<span data-ttu-id="04a72-119">Podstawowe biblioteki platformy .NET</span><span class="sxs-lookup"><span data-stu-id="04a72-119">Core .NET libraries</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="04a72-120">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="04a72-120">Affected APIs</span></span>

- <xref:System.Double.Parse%2A?displayProperty=nameWithType>
- <xref:System.Double.TryParse%2A?displayProperty=nameWithType>
- <xref:System.Single.Parse%2A?displayProperty=nameWithType>
- <xref:System.Single.TryParse%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

- `Overload:System.Double.Parse`
- `Overload:System.Double.TryParse`
- `Overload:System.Single.Parse`
- `Overload:System.Single.TryParse`

-->
