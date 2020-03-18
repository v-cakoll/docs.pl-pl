---
ms.openlocfilehash: 5612ebce67946e22aaeeba861115ce4f8967e1f5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75344456"
---
### <a name="apis-that-report-version-now-report-product-and-not-file-version"></a><span data-ttu-id="23d31-101">Interfejsy API, które zgłaszają wersję raportu teraz zgłosić produkt, a nie wersji pliku</span><span class="sxs-lookup"><span data-stu-id="23d31-101">APIs that report version now report product and not file version</span></span>

<span data-ttu-id="23d31-102">Wiele interfejsów API, które zwracają wersje w .NET Core teraz zwrócić wersję produktu, a nie wersji pliku.</span><span class="sxs-lookup"><span data-stu-id="23d31-102">Many of the APIs that return versions in .NET Core now return the product version rather than the file version.</span></span>

#### <a name="change-description"></a><span data-ttu-id="23d31-103">Zmień opis</span><span class="sxs-lookup"><span data-stu-id="23d31-103">Change description</span></span>

<span data-ttu-id="23d31-104">W .NET Core 2.2 i poprzednich <xref:System.Environment.Version?displayProperty=nameWithType> <xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription?displayProperty=nameWithType>wersjach metody, takie jak , , i okno dialogowe właściwości pliku dla zestawów .NET Core odzwierciedlają wersję pliku.</span><span class="sxs-lookup"><span data-stu-id="23d31-104">In .NET Core 2.2 and previous versions, methods such as <xref:System.Environment.Version?displayProperty=nameWithType>, <xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription?displayProperty=nameWithType>, and the file properties dialog for .NET Core assemblies reflect the file version.</span></span> <span data-ttu-id="23d31-105">Począwszy od .NET Core 3.0, odzwierciedlają one wersję produktu.</span><span class="sxs-lookup"><span data-stu-id="23d31-105">Starting with .NET Core 3.0, they reflect the product version.</span></span>

<span data-ttu-id="23d31-106">Na poniższej ilustracji przedstawiono różnicę w informacjach o wersji dla zestawu *System.Runtime.dll* dla .NET Core 2.2 (po lewej) i .NET Core 3.0 (po prawej) wyświetlanych w oknie dialogowym właściwości pliku **Eksploratora Windows.**</span><span class="sxs-lookup"><span data-stu-id="23d31-106">The following figure illustrates the difference in version information for the *System.Runtime.dll* assembly for .NET Core 2.2 (on the left) and .NET Core 3.0 (on the right) as displayed by the **Windows Explorer** file properties dialog.</span></span>

![Różnica w informacjach o wersji produktu](~/docs/images/core-changes/corefx/version-information-changes/file-details.png)

#### <a name="version-introduced"></a><span data-ttu-id="23d31-108">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="23d31-108">Version introduced</span></span>

<span data-ttu-id="23d31-109">3.0</span><span class="sxs-lookup"><span data-stu-id="23d31-109">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="23d31-110">Zalecana akcja</span><span class="sxs-lookup"><span data-stu-id="23d31-110">Recommended action</span></span>

<span data-ttu-id="23d31-111">Brak.</span><span class="sxs-lookup"><span data-stu-id="23d31-111">None.</span></span> <span data-ttu-id="23d31-112">Ta zmiana powinna sprawić, że wykrywanie wersji będzie intuicyjne, a nie rozwrzęce.</span><span class="sxs-lookup"><span data-stu-id="23d31-112">This change should make version detection intuitive rather than obtuse.</span></span>

#### <a name="category"></a><span data-ttu-id="23d31-113">Kategoria</span><span class="sxs-lookup"><span data-stu-id="23d31-113">Category</span></span>

<span data-ttu-id="23d31-114">CoreFx</span><span class="sxs-lookup"><span data-stu-id="23d31-114">CoreFx</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="23d31-115">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="23d31-115">Affected APIs</span></span>

- <xref:System.Environment.Version?displayProperty=nameWithType>
- <xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription?displayProperty=nameWithType>

<!--

### Affected APIs

- `P:System.Environment.Version`
- `P:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription`

-->
