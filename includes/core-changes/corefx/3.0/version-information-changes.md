---
ms.openlocfilehash: 2a751acc129ebd1c917b87f8083ffef72c7d8c17
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/28/2019
ms.locfileid: "74568202"
---
### <a name="apis-that-report-version-now-report-product-and-not-file-version"></a><span data-ttu-id="d6dae-101">Interfejsy API służące do raportowania wersji teraz produktu i nie wersji</span><span class="sxs-lookup"><span data-stu-id="d6dae-101">APIs that report version now report product and not file version</span></span>

<span data-ttu-id="d6dae-102">Wiele interfejsów API, które zwracają wersje w oprogramowaniu .NET Core, teraz zwróciło wersję produktu, a nie wersję pliku.</span><span class="sxs-lookup"><span data-stu-id="d6dae-102">Many of the APIs that return versions in .NET Core now returned the product version rather than the file version.</span></span>

#### <a name="change-description"></a><span data-ttu-id="d6dae-103">Zmień opis</span><span class="sxs-lookup"><span data-stu-id="d6dae-103">Change description</span></span>

<span data-ttu-id="d6dae-104">W programie .NET Core 2,2 i poprzednich wersjach metody, takie jak <xref:System.Environment.Version?displayProperty=nameWithType>, <xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription?displayProperty=nameWithType>i okno dialogowe właściwości pliku dla zestawów .NET Core odzwierciedlają wersję pliku.</span><span class="sxs-lookup"><span data-stu-id="d6dae-104">In .NET Core 2.2 and previous versions, methods such as <xref:System.Environment.Version?displayProperty=nameWithType>, <xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription?displayProperty=nameWithType>, and the file properties dialog for .NET Core assemblies reflect the file version.</span></span> <span data-ttu-id="d6dae-105">Począwszy od platformy .NET Core 3,0, odzwierciedlają one wersję produktu.</span><span class="sxs-lookup"><span data-stu-id="d6dae-105">Starting with .NET Core 3.0, they reflect the product version.</span></span>

<span data-ttu-id="d6dae-106">Na poniższej ilustracji przedstawiono różnice w informacjach o wersji zestawu *System. Runtime. dll* dla programu .net Core 2,2 (po lewej stronie) i .net Core 3,0 (po prawej), jak pokazano w oknie dialogowym właściwości pliku **Eksploratora Windows** .</span><span class="sxs-lookup"><span data-stu-id="d6dae-106">The following figure illustrates the difference in version information for the *System.Runtime.dll* assembly for .NET Core 2.2 (on the left) and .NET Core 3.0 (on the right) as displayed by the **Windows Explorer** file properties dialog.</span></span>

![Różnica w informacjach o wersji produktu](~/docs/images/core-changes/corefx/version-information-changes/file-details.png)

#### <a name="version-introduced"></a><span data-ttu-id="d6dae-108">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="d6dae-108">Version introduced</span></span>

<span data-ttu-id="d6dae-109">3.0</span><span class="sxs-lookup"><span data-stu-id="d6dae-109">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="d6dae-110">Zalecane działanie</span><span class="sxs-lookup"><span data-stu-id="d6dae-110">Recommended action</span></span>

<span data-ttu-id="d6dae-111">Brak.</span><span class="sxs-lookup"><span data-stu-id="d6dae-111">None.</span></span> <span data-ttu-id="d6dae-112">Ta zmiana powinna sprawiać, że wykrywanie wersji jest intuicyjne, a nie obtuse.</span><span class="sxs-lookup"><span data-stu-id="d6dae-112">This change should make version detection intuitive rather than obtuse.</span></span>

#### <a name="category"></a><span data-ttu-id="d6dae-113">Kategoria</span><span class="sxs-lookup"><span data-stu-id="d6dae-113">Category</span></span>

<span data-ttu-id="d6dae-114">CoreFx</span><span class="sxs-lookup"><span data-stu-id="d6dae-114">CoreFx</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="d6dae-115">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="d6dae-115">Affected APIs</span></span>

- <xref:System.Environment.Version?displayProperty=nameWithType>
- <xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription?displayProperty=nameWithType>

<!--

### Affected APIs

- `P:System.Environment.Version`
- `P:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription`

-->
