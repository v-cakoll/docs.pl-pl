---
ms.openlocfilehash: 5612ebce67946e22aaeeba861115ce4f8967e1f5
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/25/2019
ms.locfileid: "75344456"
---
### <a name="apis-that-report-version-now-report-product-and-not-file-version"></a><span data-ttu-id="0164f-101">Interfejsy API służące do raportowania wersji teraz produktu i nie wersji</span><span class="sxs-lookup"><span data-stu-id="0164f-101">APIs that report version now report product and not file version</span></span>

<span data-ttu-id="0164f-102">Wiele interfejsów API, które zwracają wersje w oprogramowaniu .NET Core, teraz zwracają wersję produktu, a nie wersję pliku.</span><span class="sxs-lookup"><span data-stu-id="0164f-102">Many of the APIs that return versions in .NET Core now return the product version rather than the file version.</span></span>

#### <a name="change-description"></a><span data-ttu-id="0164f-103">Opis zmiany</span><span class="sxs-lookup"><span data-stu-id="0164f-103">Change description</span></span>

<span data-ttu-id="0164f-104">W programie .NET Core 2,2 i poprzednich wersjach metody, takie jak <xref:System.Environment.Version?displayProperty=nameWithType>, <xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription?displayProperty=nameWithType>i okno dialogowe właściwości pliku dla zestawów .NET Core odzwierciedlają wersję pliku.</span><span class="sxs-lookup"><span data-stu-id="0164f-104">In .NET Core 2.2 and previous versions, methods such as <xref:System.Environment.Version?displayProperty=nameWithType>, <xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription?displayProperty=nameWithType>, and the file properties dialog for .NET Core assemblies reflect the file version.</span></span> <span data-ttu-id="0164f-105">Począwszy od platformy .NET Core 3,0, odzwierciedlają one wersję produktu.</span><span class="sxs-lookup"><span data-stu-id="0164f-105">Starting with .NET Core 3.0, they reflect the product version.</span></span>

<span data-ttu-id="0164f-106">Na poniższej ilustracji przedstawiono różnice w informacjach o wersji zestawu *System. Runtime. dll* dla programu .net Core 2,2 (po lewej stronie) i .net Core 3,0 (po prawej), jak pokazano w oknie dialogowym właściwości pliku **Eksploratora Windows** .</span><span class="sxs-lookup"><span data-stu-id="0164f-106">The following figure illustrates the difference in version information for the *System.Runtime.dll* assembly for .NET Core 2.2 (on the left) and .NET Core 3.0 (on the right) as displayed by the **Windows Explorer** file properties dialog.</span></span>

![Różnica w informacjach o wersji produktu](~/docs/images/core-changes/corefx/version-information-changes/file-details.png)

#### <a name="version-introduced"></a><span data-ttu-id="0164f-108">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="0164f-108">Version introduced</span></span>

<span data-ttu-id="0164f-109">3.0</span><span class="sxs-lookup"><span data-stu-id="0164f-109">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="0164f-110">Zalecane działanie</span><span class="sxs-lookup"><span data-stu-id="0164f-110">Recommended action</span></span>

<span data-ttu-id="0164f-111">Brak.</span><span class="sxs-lookup"><span data-stu-id="0164f-111">None.</span></span> <span data-ttu-id="0164f-112">Ta zmiana powinna sprawiać, że wykrywanie wersji jest intuicyjne, a nie obtuse.</span><span class="sxs-lookup"><span data-stu-id="0164f-112">This change should make version detection intuitive rather than obtuse.</span></span>

#### <a name="category"></a><span data-ttu-id="0164f-113">Kategoria</span><span class="sxs-lookup"><span data-stu-id="0164f-113">Category</span></span>

<span data-ttu-id="0164f-114">CoreFx</span><span class="sxs-lookup"><span data-stu-id="0164f-114">CoreFx</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="0164f-115">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="0164f-115">Affected APIs</span></span>

- <xref:System.Environment.Version?displayProperty=nameWithType>
- <xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription?displayProperty=nameWithType>

<!--

### Affected APIs

- `P:System.Environment.Version`
- `P:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription`

-->
