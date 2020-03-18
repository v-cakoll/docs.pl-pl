---
ms.openlocfilehash: 7f528510e4158dad71280a7b1f269a231b8c60f2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "76116343"
---
### <a name="types-in-microsoftvisualbasicdevices-namespace-not-available"></a><span data-ttu-id="17274-101">Typy w obszarze nazw Microsoft.VisualBasic.Devices niedostępne</span><span class="sxs-lookup"><span data-stu-id="17274-101">Types in Microsoft.VisualBasic.Devices namespace not available</span></span>

<span data-ttu-id="17274-102">Typy w <xref:Microsoft.VisualBasic.Devices?displayProperty=fullName> obszarze nazw nie są dostępne.</span><span class="sxs-lookup"><span data-stu-id="17274-102">The types in the <xref:Microsoft.VisualBasic.Devices?displayProperty=fullName> namespace are not available.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="17274-103">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="17274-103">Version introduced</span></span>

<span data-ttu-id="17274-104">Podgląd .NET Core 3.0 8</span><span class="sxs-lookup"><span data-stu-id="17274-104">.NET Core 3.0 Preview 8</span></span>

#### <a name="change-description"></a><span data-ttu-id="17274-105">Zmień opis</span><span class="sxs-lookup"><span data-stu-id="17274-105">Change description</span></span>

<span data-ttu-id="17274-106">Typy w <xref:Microsoft.VisualBasic.Devices?displayProperty=fullName> obszarze nazw były dostępne w niektórych wersjach podglądu programu .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="17274-106">The types in the <xref:Microsoft.VisualBasic.Devices?displayProperty=fullName> namespace were available in some .NET Core 3.0 Preview releases,.</span></span> <span data-ttu-id="17274-107">Nie są już dostępne od wersji .NET Core 3.0 Preview 9.</span><span class="sxs-lookup"><span data-stu-id="17274-107">They are no longer available starting with .NET Core 3.0 Preview 9.</span></span>

<span data-ttu-id="17274-108">Typy zostały usunięte, aby uniknąć niepotrzebnych zależności zestawu lub zerwania zmian w kolejnych wersjach.</span><span class="sxs-lookup"><span data-stu-id="17274-108">The types were removed to avoid unnecessary assembly dependencies or breaking changes in subsequent releases.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="17274-109">Zalecana akcja</span><span class="sxs-lookup"><span data-stu-id="17274-109">Recommended action</span></span>

<span data-ttu-id="17274-110">Jeśli kod zależy od <xref:Microsoft.VisualBasic.Devices> użycia typów i ich elementów członkowskich, można użyć odpowiedniego typu lub elementu członkowskiego w bibliotece klas .NET.</span><span class="sxs-lookup"><span data-stu-id="17274-110">If your code depends on the use of <xref:Microsoft.VisualBasic.Devices> types and their members, you may be able to use a corresponding type or member in the .NET class library.</span></span> <span data-ttu-id="17274-111">Na przykład równoważne funkcje <xref:Microsoft.VisualBasic.Devices.Clock?displayProperty=nameWithType> do klasy <xref:System.DateTime?displayProperty=nameWithType> jest <xref:System.Environment?displayProperty=nameWithType> dostarczany przez i typów <xref:Microsoft.VisualBasic.Devices.Ports?displayProperty=nameWithType> i równoważne funkcje <xref:System.IO.Ports?displayProperty=nameWithType> do klasy jest dostarczany przez typy w przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="17274-111">For example, equivalent functionality to the <xref:Microsoft.VisualBasic.Devices.Clock?displayProperty=nameWithType> class is provided by the <xref:System.DateTime?displayProperty=nameWithType> and <xref:System.Environment?displayProperty=nameWithType> types, and equivalent functionality to the <xref:Microsoft.VisualBasic.Devices.Ports?displayProperty=nameWithType> class is provided by types in the <xref:System.IO.Ports?displayProperty=nameWithType> namespace.</span></span>

#### <a name="category"></a><span data-ttu-id="17274-112">Kategoria</span><span class="sxs-lookup"><span data-stu-id="17274-112">Category</span></span>

<span data-ttu-id="17274-113">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="17274-113">Visual Basic</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="17274-114">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="17274-114">Affected APIs</span></span>

- <xref:Microsoft.VisualBasic.Devices?displayProperty=fullName>

<!--

### Affected APIs

- `N:Microsoft.VisualBasic.Devices`

-->
