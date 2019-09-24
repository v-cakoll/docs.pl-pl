---
ms.openlocfilehash: 2a751acc129ebd1c917b87f8083ffef72c7d8c17
ms.sourcegitcommit: 56f1d1203d0075a461a10a301459d3aa452f4f47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/24/2019
ms.locfileid: "71216369"
---
### <a name="apis-that-report-version-now-report-product-and-not-file-version"></a><span data-ttu-id="cae10-101">Interfejsy API służące do raportowania wersji teraz produktu i nie wersji</span><span class="sxs-lookup"><span data-stu-id="cae10-101">APIs that report version now report product and not file version</span></span>

<span data-ttu-id="cae10-102">Wiele interfejsów API, które zwracają wersje w oprogramowaniu .NET Core, teraz zwróciło wersję produktu, a nie wersję pliku.</span><span class="sxs-lookup"><span data-stu-id="cae10-102">Many of the APIs that return versions in .NET Core now returned the product version rather than the file version.</span></span>

#### <a name="change-description"></a><span data-ttu-id="cae10-103">Zmień opis</span><span class="sxs-lookup"><span data-stu-id="cae10-103">Change description</span></span>

<span data-ttu-id="cae10-104">W programie .NET Core 2,2 i poprzednich wersjach metody, takie <xref:System.Environment.Version?displayProperty=nameWithType>jak <xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription?displayProperty=nameWithType>, i okno dialogowe właściwości pliku dla zestawów .NET Core odzwierciedlają wersję pliku.</span><span class="sxs-lookup"><span data-stu-id="cae10-104">In .NET Core 2.2 and previous versions, methods such as <xref:System.Environment.Version?displayProperty=nameWithType>, <xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription?displayProperty=nameWithType>, and the file properties dialog for .NET Core assemblies reflect the file version.</span></span> <span data-ttu-id="cae10-105">Począwszy od platformy .NET Core 3,0, odzwierciedlają one wersję produktu.</span><span class="sxs-lookup"><span data-stu-id="cae10-105">Starting with .NET Core 3.0, they reflect the product version.</span></span>

<span data-ttu-id="cae10-106">Na poniższej ilustracji przedstawiono różnice w informacjach o wersji zestawu *System. Runtime. dll* dla programu .net Core 2,2 (po lewej stronie) i .net Core 3,0 (po prawej), jak pokazano w oknie dialogowym właściwości pliku **Eksploratora Windows** .</span><span class="sxs-lookup"><span data-stu-id="cae10-106">The following figure illustrates the difference in version information for the *System.Runtime.dll* assembly for .NET Core 2.2 (on the left) and .NET Core 3.0 (on the right) as displayed by the **Windows Explorer** file properties dialog.</span></span>

![Różnica w informacjach o wersji produktu](~/docs/images/core-changes/corefx/version-information-changes/file-details.png)

#### <a name="version-introduced"></a><span data-ttu-id="cae10-108">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="cae10-108">Version introduced</span></span>

<span data-ttu-id="cae10-109">3.0</span><span class="sxs-lookup"><span data-stu-id="cae10-109">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="cae10-110">Zalecana akcja</span><span class="sxs-lookup"><span data-stu-id="cae10-110">Recommended action</span></span>

<span data-ttu-id="cae10-111">Brak.</span><span class="sxs-lookup"><span data-stu-id="cae10-111">None.</span></span> <span data-ttu-id="cae10-112">Ta zmiana powinna sprawiać, że wykrywanie wersji jest intuicyjne, a nie obtuse.</span><span class="sxs-lookup"><span data-stu-id="cae10-112">This change should make version detection intuitive rather than obtuse.</span></span>

#### <a name="category"></a><span data-ttu-id="cae10-113">Kategoria</span><span class="sxs-lookup"><span data-stu-id="cae10-113">Category</span></span>

<span data-ttu-id="cae10-114">CoreFx</span><span class="sxs-lookup"><span data-stu-id="cae10-114">CoreFx</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="cae10-115">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="cae10-115">Affected APIs</span></span>

- <xref:System.Environment.Version?displayProperty=nameWithType>
- <xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription?displayProperty=nameWithType>

<!--

### Affected APIs

- `P:System.Environment.Version`
- `P:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription`

-->
