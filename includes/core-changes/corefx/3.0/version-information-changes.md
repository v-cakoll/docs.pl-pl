---
ms.openlocfilehash: 1580c8c8b7bdad91656f494537230293dbaaf93b
ms.sourcegitcommit: 348bb052d5cef109a61a3d5253faa5d7167d55ac
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2020
ms.locfileid: "82021574"
---
### <a name="apis-that-report-version-now-report-product-and-not-file-version"></a><span data-ttu-id="32ae4-101">Interfejsy API, które zgłaszają wersję raportu, teraz zgłaszają produkt, a nie wersję pliku</span><span class="sxs-lookup"><span data-stu-id="32ae4-101">APIs that report version now report product and not file version</span></span>

<span data-ttu-id="32ae4-102">Wiele interfejsów API, które zwracają wersje w .NET Core teraz zwraca wersję produktu, a nie wersji pliku.</span><span class="sxs-lookup"><span data-stu-id="32ae4-102">Many of the APIs that return versions in .NET Core now return the product version rather than the file version.</span></span>

#### <a name="change-description"></a><span data-ttu-id="32ae4-103">Zmień opis</span><span class="sxs-lookup"><span data-stu-id="32ae4-103">Change description</span></span>

<span data-ttu-id="32ae4-104">W .NET Core 2.2 i poprzednich <xref:System.Environment.Version?displayProperty=nameWithType> <xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription?displayProperty=nameWithType>wersjach metody takie jak , i okno dialogowe właściwości pliku dla zestawów .NET Core odzwierciedlają wersję pliku.</span><span class="sxs-lookup"><span data-stu-id="32ae4-104">In .NET Core 2.2 and previous versions, methods such as <xref:System.Environment.Version?displayProperty=nameWithType>, <xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription?displayProperty=nameWithType>, and the file properties dialog for .NET Core assemblies reflect the file version.</span></span> <span data-ttu-id="32ae4-105">Począwszy od .NET Core 3.0, odzwierciedlają one wersję produktu.</span><span class="sxs-lookup"><span data-stu-id="32ae4-105">Starting with .NET Core 3.0, they reflect the product version.</span></span>

<span data-ttu-id="32ae4-106">Na poniższym rysunku przedstawiono różnicę w informacjach o wersji dla zestawu *System.Runtime.dll* dla .NET Core 2.2 (po lewej) i .NET Core 3.0 (po prawej) wyświetlanych w oknie dialogowym Właściwości pliku **Eksploratora Windows.**</span><span class="sxs-lookup"><span data-stu-id="32ae4-106">The following figure illustrates the difference in version information for the *System.Runtime.dll* assembly for .NET Core 2.2 (on the left) and .NET Core 3.0 (on the right) as displayed by the **Windows Explorer** file properties dialog.</span></span>

![Różnica w informacjach o wersji produktu](~/docs/images/core-changes/corefx/version-information-changes/file-details.png)

#### <a name="version-introduced"></a><span data-ttu-id="32ae4-108">Wprowadzono wersję</span><span class="sxs-lookup"><span data-stu-id="32ae4-108">Version introduced</span></span>

<span data-ttu-id="32ae4-109">3.0</span><span class="sxs-lookup"><span data-stu-id="32ae4-109">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="32ae4-110">Zalecana akcja</span><span class="sxs-lookup"><span data-stu-id="32ae4-110">Recommended action</span></span>

<span data-ttu-id="32ae4-111">Brak.</span><span class="sxs-lookup"><span data-stu-id="32ae4-111">None.</span></span> <span data-ttu-id="32ae4-112">Ta zmiana powinna sprawić, że wykrywanie wersji będzie intuicyjne, a nie rozwarte.</span><span class="sxs-lookup"><span data-stu-id="32ae4-112">This change should make version detection intuitive rather than obtuse.</span></span>

#### <a name="category"></a><span data-ttu-id="32ae4-113">Kategoria</span><span class="sxs-lookup"><span data-stu-id="32ae4-113">Category</span></span>

<span data-ttu-id="32ae4-114">Podstawowe biblioteki .NET</span><span class="sxs-lookup"><span data-stu-id="32ae4-114">Core .NET libraries</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="32ae4-115">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="32ae4-115">Affected APIs</span></span>

- <xref:System.Environment.Version?displayProperty=nameWithType>
- <xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription?displayProperty=nameWithType>

<!--

### Affected APIs

- `P:System.Environment.Version`
- `P:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription`

-->
