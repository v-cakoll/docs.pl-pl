---
ms.openlocfilehash: 4bc060f991501b81db0cb7c521e55996a2b5e91e
ms.sourcegitcommit: 97ce5363efa88179dd76e09de0103a500ca9b659
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/13/2020
ms.locfileid: "86281312"
---
### <a name="behavior-change-for-vector2lerp-and-vector4lerp"></a><span data-ttu-id="03b39-101">Zmiana zachowania dla Vector2. Lerp i Vector4. Lerp</span><span class="sxs-lookup"><span data-stu-id="03b39-101">Behavior change for Vector2.Lerp and Vector4.Lerp</span></span>

<span data-ttu-id="03b39-102">Implementacja <xref:System.Numerics.Vector2.Lerp(System.Numerics.Vector2,System.Numerics.Vector2,System.Single)?displayProperty=nameWithType> i <xref:System.Numerics.Vector4.Lerp(System.Numerics.Vector4,System.Numerics.Vector4,System.Single)?displayProperty=nameWithType> zmiana na prawidłowe konto dla błędu zaokrąglania zmiennoprzecinkowego.</span><span class="sxs-lookup"><span data-stu-id="03b39-102">The implementation of <xref:System.Numerics.Vector2.Lerp(System.Numerics.Vector2,System.Numerics.Vector2,System.Single)?displayProperty=nameWithType> and <xref:System.Numerics.Vector4.Lerp(System.Numerics.Vector4,System.Numerics.Vector4,System.Single)?displayProperty=nameWithType> changed to correctly account for a floating-point rounding error.</span></span>

#### <a name="change-description"></a><span data-ttu-id="03b39-103">Zmień opis</span><span class="sxs-lookup"><span data-stu-id="03b39-103">Change description</span></span>

<span data-ttu-id="03b39-104">Wcześniej <xref:System.Numerics.Vector2.Lerp(System.Numerics.Vector2,System.Numerics.Vector2,System.Single)?displayProperty=nameWithType> i <xref:System.Numerics.Vector4.Lerp(System.Numerics.Vector4,System.Numerics.Vector4,System.Single)?displayProperty=nameWithType> zostały zaimplementowane jako `value1 + (value2 - value1) * amount` .</span><span class="sxs-lookup"><span data-stu-id="03b39-104">Previously, <xref:System.Numerics.Vector2.Lerp(System.Numerics.Vector2,System.Numerics.Vector2,System.Single)?displayProperty=nameWithType> and <xref:System.Numerics.Vector4.Lerp(System.Numerics.Vector4,System.Numerics.Vector4,System.Single)?displayProperty=nameWithType> were implemented as `value1 + (value2 - value1) * amount`.</span></span> <span data-ttu-id="03b39-105">Jednak ze względu na błąd zaokrąglania liczb zmiennoprzecinkowych ten algorytm nie zawsze zwraca `value2` wartość, gdy `amount` jest `1.0f` .</span><span class="sxs-lookup"><span data-stu-id="03b39-105">However, due to a floating-point rounding error, this algorithm doesn't always return `value2` when `amount` is `1.0f`.</span></span>

<span data-ttu-id="03b39-106">W przypadku programu .NET 5,0 lub nowszego implementacja używa tego samego algorytmu co <xref:System.Numerics.Vector3.Lerp(System.Numerics.Vector3,System.Numerics.Vector3,System.Single)?displayProperty=nameWithType> `(value1 * (1.0f - amount)) + (value2 * amount)` .</span><span class="sxs-lookup"><span data-stu-id="03b39-106">In .NET 5.0 and later, the implementation uses the same algorithm as <xref:System.Numerics.Vector3.Lerp(System.Numerics.Vector3,System.Numerics.Vector3,System.Single)?displayProperty=nameWithType>, which is `(value1 * (1.0f - amount)) + (value2 * amount)`.</span></span> <span data-ttu-id="03b39-107">Ten algorytm poprawnie rozliczy dla błędu zaokrąglania.</span><span class="sxs-lookup"><span data-stu-id="03b39-107">This algorithm correctly accounts for the rounding error.</span></span> <span data-ttu-id="03b39-108">Teraz, gdy `amount` jest `1.0f` , wynik jest precyzyjna `value2` .</span><span class="sxs-lookup"><span data-stu-id="03b39-108">Now, when `amount` is `1.0f`, the result is precisely `value2`.</span></span> <span data-ttu-id="03b39-109">Zaktualizowany algorytm umożliwia także swobodne zoptymalizowanie algorytmu przy użyciu, <xref:System.MathF.FusedMultiplyAdd%2A?displayProperty=nameWithType> gdy jest on dostępny.</span><span class="sxs-lookup"><span data-stu-id="03b39-109">The updated algorithm also allows the algorithm to be freely optimized using <xref:System.MathF.FusedMultiplyAdd%2A?displayProperty=nameWithType> when it's available.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="03b39-110">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="03b39-110">Version introduced</span></span>

<span data-ttu-id="03b39-111">5,0 wersja zapoznawcza 7</span><span class="sxs-lookup"><span data-stu-id="03b39-111">5.0 Preview 7</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="03b39-112">Zalecana akcja</span><span class="sxs-lookup"><span data-stu-id="03b39-112">Recommended action</span></span>

<span data-ttu-id="03b39-113">Nie jest wymagane żadne działanie.</span><span class="sxs-lookup"><span data-stu-id="03b39-113">No action is necessary.</span></span> <span data-ttu-id="03b39-114">Jeśli jednak chcesz zachować stare zachowanie, możesz zaimplementować własną `Lerp` funkcję, która używa poprzedniego algorytmu `value1 + (value2 - value1) * amount` .</span><span class="sxs-lookup"><span data-stu-id="03b39-114">However, if you want to maintain the old behavior, you can implement your own `Lerp` function that uses the previous algorithm of `value1 + (value2 - value1) * amount`.</span></span>

#### <a name="category"></a><span data-ttu-id="03b39-115">Kategoria</span><span class="sxs-lookup"><span data-stu-id="03b39-115">Category</span></span>

<span data-ttu-id="03b39-116">Podstawowe biblioteki platformy .NET</span><span class="sxs-lookup"><span data-stu-id="03b39-116">Core .NET libraries</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="03b39-117">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="03b39-117">Affected APIs</span></span>

- <xref:System.Numerics.Vector2.Lerp(System.Numerics.Vector2,System.Numerics.Vector2,System.Single)?displayProperty=fullName>
- <xref:System.Numerics.Vector4.Lerp(System.Numerics.Vector4,System.Numerics.Vector4,System.Single)?displayProperty=fullName>

<!--

#### Affected APIs

- `M:System.Numerics.Vector2.Lerp(System.Numerics.Vector2,System.Numerics.Vector2,System.Single)`
- `M:System.Numerics.Vector4.Lerp(System.Numerics.Vector4,System.Numerics.Vector4,System.Single)`

-->
