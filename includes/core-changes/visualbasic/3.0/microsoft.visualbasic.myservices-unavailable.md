---
ms.openlocfilehash: d207a937917da78f6b902ad8ca4f02fa9a46c2e1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "76116371"
---
### <a name="types-in-microsoftvisualbasicmyservices-namespace-not-available"></a><span data-ttu-id="2f853-101">Typy w przestrzeni nazw Microsoft. VisualBasic. WebServices są niedostępne</span><span class="sxs-lookup"><span data-stu-id="2f853-101">Types in Microsoft.VisualBasic.MyServices namespace not available</span></span>

<span data-ttu-id="2f853-102">Typy w <xref:Microsoft.VisualBasic.MyServices?displayProperty=fullName> przestrzeni nazw są niedostępne.</span><span class="sxs-lookup"><span data-stu-id="2f853-102">The types in the <xref:Microsoft.VisualBasic.MyServices?displayProperty=fullName> namespace are not available.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="2f853-103">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="2f853-103">Version introduced</span></span>

<span data-ttu-id="2f853-104">.NET Core 3,0 (wersja zapoznawcza 8)</span><span class="sxs-lookup"><span data-stu-id="2f853-104">.NET Core 3.0 Preview 8</span></span>

#### <a name="change-description"></a><span data-ttu-id="2f853-105">Zmień opis</span><span class="sxs-lookup"><span data-stu-id="2f853-105">Change description</span></span>

<span data-ttu-id="2f853-106">Typy w <xref:Microsoft.VisualBasic.MyServices?displayProperty=fullName> przestrzeni nazw były dostępne w niektórych wersjach programu .net Core 3,0 Preview.</span><span class="sxs-lookup"><span data-stu-id="2f853-106">The types in the <xref:Microsoft.VisualBasic.MyServices?displayProperty=fullName> namespace were available in some .NET Core 3.0 Preview releases.</span></span> <span data-ttu-id="2f853-107">Nie są już dostępne począwszy od programu .NET Core 3,0 w wersji zapoznawczej 9.</span><span class="sxs-lookup"><span data-stu-id="2f853-107">They are no longer available starting with .NET Core 3.0 Preview 9.</span></span>

<span data-ttu-id="2f853-108">Typy zostały usunięte, aby uniknąć niepotrzebnych zależności zestawów lub istotne zmiany w kolejnych wersjach.</span><span class="sxs-lookup"><span data-stu-id="2f853-108">The types were removed to avoid unnecessary assembly dependencies or breaking changes in subsequent releases.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="2f853-109">Zalecana akcja</span><span class="sxs-lookup"><span data-stu-id="2f853-109">Recommended action</span></span>

<span data-ttu-id="2f853-110">Jeśli kod zależy od użycia typów **Microsoft. VisualBasic. WebServices** i ich członków, istnieją odpowiednie typy i elementy członkowskie w bibliotece klas .NET.</span><span class="sxs-lookup"><span data-stu-id="2f853-110">If your code depends on the use of **Microsoft.VisualBasic.MyServices** types and their members, there are corresponding types and members in the .NET class library.</span></span> <span data-ttu-id="2f853-111">Poniżej znajduje się mapowanie typów **Microsoft. VisualBasic. WebServices** na ich równoważne typy biblioteki klas .NET:</span><span class="sxs-lookup"><span data-stu-id="2f853-111">The following is a mapping of  **Microsoft.VisualBasic.MyServices** types to their equivalent .NET class library types:</span></span>

|<span data-ttu-id="2f853-112">Typ Microsoft. VisualBasic. WebServices</span><span class="sxs-lookup"><span data-stu-id="2f853-112">Microsoft.VisualBasic.MyServices type</span></span>|<span data-ttu-id="2f853-113">Typ biblioteki klas .NET</span><span class="sxs-lookup"><span data-stu-id="2f853-113">.NET class library type</span></span>|
|--|--|
|<xref:Microsoft.VisualBasic.MyServices.ClipboardProxy>|<span data-ttu-id="2f853-114"><xref:System.Windows.Clipboard?displayProperty=nameWithType>dla aplikacji <xref:System.Windows.Forms.Clipboard?displayProperty=nameWithType> WPF dla aplikacji Windows Forms</span><span class="sxs-lookup"><span data-stu-id="2f853-114"><xref:System.Windows.Clipboard?displayProperty=nameWithType> for WPF applications, <xref:System.Windows.Forms.Clipboard?displayProperty=nameWithType> for Windows Forms applications</span></span>|
|<xref:Microsoft.VisualBasic.MyServices.FileSystemProxy>|<span data-ttu-id="2f853-115">Typy w <xref:System.IO> przestrzeni nazw</span><span class="sxs-lookup"><span data-stu-id="2f853-115">Types in the <xref:System.IO> namespace</span></span>|
|<xref:Microsoft.VisualBasic.MyServices.RegistryProxy>|<span data-ttu-id="2f853-116">Typy związane z rejestrem w <xref:Microsoft.Win32> przestrzeni nazw</span><span class="sxs-lookup"><span data-stu-id="2f853-116">Registry-related types in the <xref:Microsoft.Win32> namespace</span></span>|
|<xref:Microsoft.VisualBasic.MyServices.SpecialDirectoriesProxy>|<xref:System.Environment.GetFolderPath%2A?displayProperty=nameWithType>|

#### <a name="category"></a><span data-ttu-id="2f853-117">Kategoria</span><span class="sxs-lookup"><span data-stu-id="2f853-117">Category</span></span>

<span data-ttu-id="2f853-118">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="2f853-118">Visual Basic</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="2f853-119">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="2f853-119">Affected APIs</span></span>

- <xref:Microsoft.VisualBasic.MyServices?displayProperty=fullName>

<!--

### Affected APIs

- `N:Microsoft.VisualBasic.MyServices`

-->
