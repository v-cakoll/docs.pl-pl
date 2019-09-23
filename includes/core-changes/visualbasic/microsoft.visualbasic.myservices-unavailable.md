---
ms.openlocfilehash: ba543414d4f84362c9b9b876395815e837efbd3f
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/23/2019
ms.locfileid: "71181851"
---
### <a name="types-in-microsoftvisualbasicmyservices-namespace-not-available"></a><span data-ttu-id="9bf42-101">Typy w przestrzeni nazw Microsoft. VisualBasic. WebServices są niedostępne</span><span class="sxs-lookup"><span data-stu-id="9bf42-101">Types in Microsoft.VisualBasic.MyServices namespace not available</span></span>

<span data-ttu-id="9bf42-102">Typy w <xref:Microsoft.VisualBasic.MyServices?displayProperty=fullName> przestrzeni nazw są niedostępne.</span><span class="sxs-lookup"><span data-stu-id="9bf42-102">The types in the <xref:Microsoft.VisualBasic.MyServices?displayProperty=fullName> namespace are not available.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="9bf42-103">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="9bf42-103">Version introduced</span></span>

<span data-ttu-id="9bf42-104">.NET Core 3,0 (wersja zapoznawcza 8)</span><span class="sxs-lookup"><span data-stu-id="9bf42-104">.NET Core 3.0 Preview 8</span></span>

#### <a name="details"></a><span data-ttu-id="9bf42-105">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="9bf42-105">Details</span></span>

<span data-ttu-id="9bf42-106">Typy w <xref:Microsoft.VisualBasic.MyServices?displayProperty=fullName> przestrzeni nazw były dostępne w niektórych wersjach programu .NET Core 3,0 w wersji zapoznawczej.</span><span class="sxs-lookup"><span data-stu-id="9bf42-106">The types in the <xref:Microsoft.VisualBasic.MyServices?displayProperty=fullName> namespace were available in some .NET Core 3.0 Preview releases,.</span></span> <span data-ttu-id="9bf42-107">Nie są już dostępne począwszy od programu .NET Core 3,0 w wersji zapoznawczej 9.</span><span class="sxs-lookup"><span data-stu-id="9bf42-107">They are no longer available starting with .NET Core 3.0 Preview 9.</span></span>

<span data-ttu-id="9bf42-108">Typy zostały usunięte, aby uniknąć niepotrzebnych zależności zestawów lub istotne zmiany w kolejnych wersjach.</span><span class="sxs-lookup"><span data-stu-id="9bf42-108">The types were removed to avoid unnecessary assembly dependencies or breaking changes in subsequent releases.</span></span>
 
#### <a name="recommended-action"></a><span data-ttu-id="9bf42-109">Zalecana akcja</span><span class="sxs-lookup"><span data-stu-id="9bf42-109">Recommended action</span></span>

<span data-ttu-id="9bf42-110">Jeśli kod zależy od użycia typów **Microsoft. VisualBasic. WebServices** i ich członków, istnieją odpowiednie typy i elementy członkowskie w bibliotece klas .NET.</span><span class="sxs-lookup"><span data-stu-id="9bf42-110">If your code depends on the use of **Microsoft.VisualBasic.MyServices** types and their members, there are corresponding types and members in the .NET class library.</span></span> <span data-ttu-id="9bf42-111">Poniżej znajduje się mapowanie typów **Microsoft. VisualBasic. WebServices** na ich równoważne typy biblioteki klas .NET:</span><span class="sxs-lookup"><span data-stu-id="9bf42-111">The following is a mapping of  **Microsoft.VisualBasic.MyServices** types to their equivalent .NET class library types:</span></span>

|<span data-ttu-id="9bf42-112">Typ Microsoft. VisualBasic. WebServices</span><span class="sxs-lookup"><span data-stu-id="9bf42-112">Microsoft.VisualBasic.MyServices type</span></span>|<span data-ttu-id="9bf42-113">Typ biblioteki klas .NET</span><span class="sxs-lookup"><span data-stu-id="9bf42-113">.NET class library type</span></span>|
|--|--|
|<xref:Microsoft.VisualBasic.MyServices.ClipboardProxy>|<span data-ttu-id="9bf42-114"><xref:System.Windows.Clipboard?displayProperty=nameWithType>dla aplikacji <xref:System.Windows.Forms.Clipboard?displayProperty=nameWithType> WPF dla aplikacji Windows Forms</span><span class="sxs-lookup"><span data-stu-id="9bf42-114"><xref:System.Windows.Clipboard?displayProperty=nameWithType> for WPF applications, <xref:System.Windows.Forms.Clipboard?displayProperty=nameWithType> for Windows Forms applications</span></span>| 
|<xref:Microsoft.VisualBasic.MyServices.FileSystemProxy>|<span data-ttu-id="9bf42-115">Typy w <xref:System.IO> przestrzeni nazw</span><span class="sxs-lookup"><span data-stu-id="9bf42-115">Types in the <xref:System.IO> namespace</span></span>|
|<xref:Microsoft.VisualBasic.MyServices.RegistryProxy>|<span data-ttu-id="9bf42-116">Typy związane z rejestrem w <xref:Microsoft.Win32> przestrzeni nazw</span><span class="sxs-lookup"><span data-stu-id="9bf42-116">Registry-related types in the <xref:Microsoft.Win32> namespace</span></span>|
|<xref:Microsoft.VisualBasic.MyServices.SpecialDirectoriesProxy>|<xref:System.Environment.GetFolderPath%2A?displayProperty=nameWithType>|

#### <a name="category"></a><span data-ttu-id="9bf42-117">Kategoria</span><span class="sxs-lookup"><span data-stu-id="9bf42-117">Category</span></span>

<span data-ttu-id="9bf42-118">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="9bf42-118">Visual Basic</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="9bf42-119">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="9bf42-119">Affected APIs</span></span>

- <xref:Microsoft.VisualBasic.MyServices?displayProperty=fullName>

<!--

### Affected APIs

- `N:Microsoft.VisualBasic.MyServices`

-- >
