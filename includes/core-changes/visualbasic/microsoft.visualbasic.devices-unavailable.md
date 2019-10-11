---
ms.openlocfilehash: dae4afa92b8833f326b4eacd00b36bb3e1199cc1
ms.sourcegitcommit: dfd612ba454ce775a766bcc6fe93bc1d43dfda47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/09/2019
ms.locfileid: "72237425"
---
### <a name="types-in-microsoftvisualbasicdevices-namespace-not-available"></a><span data-ttu-id="9dd54-101">Typy w przestrzeni nazw Microsoft. VisualBasic. Devices są niedostępne</span><span class="sxs-lookup"><span data-stu-id="9dd54-101">Types in Microsoft.VisualBasic.Devices namespace not available</span></span>

<span data-ttu-id="9dd54-102">Typy w przestrzeni nazw <xref:Microsoft.VisualBasic.Devices?displayProperty=fullName> są niedostępne.</span><span class="sxs-lookup"><span data-stu-id="9dd54-102">The types in the <xref:Microsoft.VisualBasic.Devices?displayProperty=fullName> namespace are not available.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="9dd54-103">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="9dd54-103">Version introduced</span></span>

<span data-ttu-id="9dd54-104">.NET Core 3,0 (wersja zapoznawcza 8)</span><span class="sxs-lookup"><span data-stu-id="9dd54-104">.NET Core 3.0 Preview 8</span></span>

#### <a name="change-description"></a><span data-ttu-id="9dd54-105">Zmień opis</span><span class="sxs-lookup"><span data-stu-id="9dd54-105">Change description</span></span>

<span data-ttu-id="9dd54-106">Typy w przestrzeni nazw <xref:Microsoft.VisualBasic.Devices?displayProperty=fullName> były dostępne w niektórych wersjach programu .NET Core 3,0 w wersji zapoznawczej.</span><span class="sxs-lookup"><span data-stu-id="9dd54-106">The types in the <xref:Microsoft.VisualBasic.Devices?displayProperty=fullName> namespace were available in some .NET Core 3.0 Preview releases,.</span></span> <span data-ttu-id="9dd54-107">Nie są już dostępne począwszy od programu .NET Core 3,0 w wersji zapoznawczej 9.</span><span class="sxs-lookup"><span data-stu-id="9dd54-107">They are no longer available starting with .NET Core 3.0 Preview 9.</span></span>

<span data-ttu-id="9dd54-108">Typy zostały usunięte, aby uniknąć niepotrzebnych zależności zestawów lub istotne zmiany w kolejnych wersjach.</span><span class="sxs-lookup"><span data-stu-id="9dd54-108">The types were removed to avoid unnecessary assembly dependencies or breaking changes in subsequent releases.</span></span>
 
#### <a name="recommended-action"></a><span data-ttu-id="9dd54-109">Zalecana akcja</span><span class="sxs-lookup"><span data-stu-id="9dd54-109">Recommended action</span></span>

<span data-ttu-id="9dd54-110">Jeśli kod zależy od użycia typów <xref:Microsoft.VisualBasic.Devices> i ich elementów członkowskich, można użyć odpowiedniego typu lub elementu członkowskiego w bibliotece klas .NET.</span><span class="sxs-lookup"><span data-stu-id="9dd54-110">If your code depends on the use of <xref:Microsoft.VisualBasic.Devices> types and their members, you may be able to use a corresponding type or member in the .NET class library.</span></span> <span data-ttu-id="9dd54-111">Na przykład równoważne funkcje klasy <xref:Microsoft.VisualBasic.Devices.Clock?displayProperty=nameWithType> są dostarczane przez typy <xref:System.DateTime?displayProperty=nameWithType> i <xref:System.Environment?displayProperty=nameWithType>, a równoważne funkcje klasy <xref:Microsoft.VisualBasic.Devices.Ports?displayProperty=nameWithType> są udostępniane przez typy w przestrzeni nazw <xref:System.IO.Ports?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="9dd54-111">For example, equivalent functionality to the <xref:Microsoft.VisualBasic.Devices.Clock?displayProperty=nameWithType> class is provided by the <xref:System.DateTime?displayProperty=nameWithType> and <xref:System.Environment?displayProperty=nameWithType> types, and equivalent functionality to the <xref:Microsoft.VisualBasic.Devices.Ports?displayProperty=nameWithType> class is provided by types in the <xref:System.IO.Ports?displayProperty=nameWithType> namespace.</span></span>

#### <a name="category"></a><span data-ttu-id="9dd54-112">Kategoria</span><span class="sxs-lookup"><span data-stu-id="9dd54-112">Category</span></span>

<span data-ttu-id="9dd54-113">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="9dd54-113">Visual Basic</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="9dd54-114">Narażone interfejsy API</span><span class="sxs-lookup"><span data-stu-id="9dd54-114">Affected APIs</span></span>

- <xref:Microsoft.VisualBasic.Devices?displayProperty=fullName>

<!--

### Affected APIs

- `N:Microsoft.VisualBasic.Devices`

-- >

