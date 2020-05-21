---
ms.openlocfilehash: a35de09b9a7bb9686433205359c3cc55954c29c3
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/20/2020
ms.locfileid: "83721318"
---
### <a name="types-in-microsoftvisualbasicdevices-namespace-not-available"></a><span data-ttu-id="8654e-101">Typy w przestrzeni nazw Microsoft. VisualBasic. Devices są niedostępne</span><span class="sxs-lookup"><span data-stu-id="8654e-101">Types in Microsoft.VisualBasic.Devices namespace not available</span></span>

<span data-ttu-id="8654e-102">Typy w <xref:Microsoft.VisualBasic.Devices?displayProperty=fullName> przestrzeni nazw są niedostępne.</span><span class="sxs-lookup"><span data-stu-id="8654e-102">The types in the <xref:Microsoft.VisualBasic.Devices?displayProperty=fullName> namespace are not available.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="8654e-103">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="8654e-103">Version introduced</span></span>

<span data-ttu-id="8654e-104">.NET Core 3,0 (wersja zapoznawcza 8)</span><span class="sxs-lookup"><span data-stu-id="8654e-104">.NET Core 3.0 Preview 8</span></span>

#### <a name="change-description"></a><span data-ttu-id="8654e-105">Zmień opis</span><span class="sxs-lookup"><span data-stu-id="8654e-105">Change description</span></span>

<span data-ttu-id="8654e-106">Typy w <xref:Microsoft.VisualBasic.Devices?displayProperty=fullName> przestrzeni nazw były dostępne w niektórych wersjach programu .NET Core 3,0 w wersji zapoznawczej.</span><span class="sxs-lookup"><span data-stu-id="8654e-106">The types in the <xref:Microsoft.VisualBasic.Devices?displayProperty=fullName> namespace were available in some .NET Core 3.0 Preview releases,.</span></span> <span data-ttu-id="8654e-107">Nie są już dostępne począwszy od programu .NET Core 3,0 w wersji zapoznawczej 9.</span><span class="sxs-lookup"><span data-stu-id="8654e-107">They are no longer available starting with .NET Core 3.0 Preview 9.</span></span>

<span data-ttu-id="8654e-108">Typy zostały usunięte, aby uniknąć niepotrzebnych zależności zestawów lub istotne zmiany w kolejnych wersjach.</span><span class="sxs-lookup"><span data-stu-id="8654e-108">The types were removed to avoid unnecessary assembly dependencies or breaking changes in subsequent releases.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="8654e-109">Zalecana akcja</span><span class="sxs-lookup"><span data-stu-id="8654e-109">Recommended action</span></span>

<span data-ttu-id="8654e-110">Jeśli kod zależy od użycia <xref:Microsoft.VisualBasic.Devices> typów i ich członków, może być możliwe użycie odpowiedniego typu lub elementu członkowskiego w bibliotece klas .NET.</span><span class="sxs-lookup"><span data-stu-id="8654e-110">If your code depends on the use of <xref:Microsoft.VisualBasic.Devices> types and their members, you may be able to use a corresponding type or member in the .NET class library.</span></span> <span data-ttu-id="8654e-111">Na przykład równoważne funkcje <xref:Microsoft.VisualBasic.Devices.Clock?displayProperty=nameWithType> klasy są dostarczane przez <xref:System.DateTime?displayProperty=nameWithType> typy i i <xref:System.Environment?displayProperty=nameWithType> równoważne funkcje <xref:Microsoft.VisualBasic.Devices.Ports?displayProperty=nameWithType> klasy są udostępniane przez typy w <xref:System.IO.Ports?displayProperty=nameWithType> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="8654e-111">For example, equivalent functionality to the <xref:Microsoft.VisualBasic.Devices.Clock?displayProperty=nameWithType> class is provided by the <xref:System.DateTime?displayProperty=nameWithType> and <xref:System.Environment?displayProperty=nameWithType> types, and equivalent functionality to the <xref:Microsoft.VisualBasic.Devices.Ports?displayProperty=nameWithType> class is provided by types in the <xref:System.IO.Ports?displayProperty=nameWithType> namespace.</span></span>

#### <a name="category"></a><span data-ttu-id="8654e-112">Kategoria</span><span class="sxs-lookup"><span data-stu-id="8654e-112">Category</span></span>

<span data-ttu-id="8654e-113">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="8654e-113">Visual Basic</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="8654e-114">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="8654e-114">Affected APIs</span></span>

- <xref:Microsoft.VisualBasic.Devices?displayProperty=fullName>

<!--

#### Affected APIs

- `N:Microsoft.VisualBasic.Devices`

-->
