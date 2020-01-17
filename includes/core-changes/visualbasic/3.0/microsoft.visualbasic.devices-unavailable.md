---
ms.openlocfilehash: 7f528510e4158dad71280a7b1f269a231b8c60f2
ms.sourcegitcommit: ed3f926b6cdd372037bbcc214dc8f08a70366390
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/16/2020
ms.locfileid: "76116343"
---
### <a name="types-in-microsoftvisualbasicdevices-namespace-not-available"></a><span data-ttu-id="598a7-101">Typy w przestrzeni nazw Microsoft. VisualBasic. Devices są niedostępne</span><span class="sxs-lookup"><span data-stu-id="598a7-101">Types in Microsoft.VisualBasic.Devices namespace not available</span></span>

<span data-ttu-id="598a7-102">Typy w przestrzeni nazw <xref:Microsoft.VisualBasic.Devices?displayProperty=fullName> są niedostępne.</span><span class="sxs-lookup"><span data-stu-id="598a7-102">The types in the <xref:Microsoft.VisualBasic.Devices?displayProperty=fullName> namespace are not available.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="598a7-103">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="598a7-103">Version introduced</span></span>

<span data-ttu-id="598a7-104">.NET Core 3,0 (wersja zapoznawcza 8)</span><span class="sxs-lookup"><span data-stu-id="598a7-104">.NET Core 3.0 Preview 8</span></span>

#### <a name="change-description"></a><span data-ttu-id="598a7-105">Opis zmiany</span><span class="sxs-lookup"><span data-stu-id="598a7-105">Change description</span></span>

<span data-ttu-id="598a7-106">Typy w przestrzeni nazw <xref:Microsoft.VisualBasic.Devices?displayProperty=fullName> były dostępne w niektórych wersjach programu .NET Core 3,0 w wersji zapoznawczej.</span><span class="sxs-lookup"><span data-stu-id="598a7-106">The types in the <xref:Microsoft.VisualBasic.Devices?displayProperty=fullName> namespace were available in some .NET Core 3.0 Preview releases,.</span></span> <span data-ttu-id="598a7-107">Nie są już dostępne począwszy od programu .NET Core 3,0 w wersji zapoznawczej 9.</span><span class="sxs-lookup"><span data-stu-id="598a7-107">They are no longer available starting with .NET Core 3.0 Preview 9.</span></span>

<span data-ttu-id="598a7-108">Typy zostały usunięte, aby uniknąć niepotrzebnych zależności zestawów lub istotne zmiany w kolejnych wersjach.</span><span class="sxs-lookup"><span data-stu-id="598a7-108">The types were removed to avoid unnecessary assembly dependencies or breaking changes in subsequent releases.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="598a7-109">Zalecane działanie</span><span class="sxs-lookup"><span data-stu-id="598a7-109">Recommended action</span></span>

<span data-ttu-id="598a7-110">Jeśli kod zależy od użycia typów <xref:Microsoft.VisualBasic.Devices> i ich członków, można użyć odpowiedniego typu lub składowej w bibliotece klas .NET.</span><span class="sxs-lookup"><span data-stu-id="598a7-110">If your code depends on the use of <xref:Microsoft.VisualBasic.Devices> types and their members, you may be able to use a corresponding type or member in the .NET class library.</span></span> <span data-ttu-id="598a7-111">Na przykład równoważne funkcje klasy <xref:Microsoft.VisualBasic.Devices.Clock?displayProperty=nameWithType> są dostarczane przez typy <xref:System.DateTime?displayProperty=nameWithType> i <xref:System.Environment?displayProperty=nameWithType> i równoważne funkcje klasy <xref:Microsoft.VisualBasic.Devices.Ports?displayProperty=nameWithType> są udostępniane przez typy w przestrzeni nazw <xref:System.IO.Ports?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="598a7-111">For example, equivalent functionality to the <xref:Microsoft.VisualBasic.Devices.Clock?displayProperty=nameWithType> class is provided by the <xref:System.DateTime?displayProperty=nameWithType> and <xref:System.Environment?displayProperty=nameWithType> types, and equivalent functionality to the <xref:Microsoft.VisualBasic.Devices.Ports?displayProperty=nameWithType> class is provided by types in the <xref:System.IO.Ports?displayProperty=nameWithType> namespace.</span></span>

#### <a name="category"></a><span data-ttu-id="598a7-112">Kategoria</span><span class="sxs-lookup"><span data-stu-id="598a7-112">Category</span></span>

<span data-ttu-id="598a7-113">Język Visual Basic</span><span class="sxs-lookup"><span data-stu-id="598a7-113">Visual Basic</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="598a7-114">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="598a7-114">Affected APIs</span></span>

- <xref:Microsoft.VisualBasic.Devices?displayProperty=fullName>

<!--

### Affected APIs

- `N:Microsoft.VisualBasic.Devices`

-->
