---
ms.openlocfilehash: 3dfacadb5127319d4ce27f367803637cfb1ed00f
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/20/2020
ms.locfileid: "83721519"
---
### <a name="duplicated-apis-removed-from-windows-forms"></a><span data-ttu-id="c2993-101">Zduplikowane interfejsy API zostały usunięte z Windows Forms</span><span class="sxs-lookup"><span data-stu-id="c2993-101">Duplicated APIs removed from Windows Forms</span></span>

<span data-ttu-id="c2993-102">Wiele interfejsów API przypadkowo zduplikowanych w <xref:System.Windows.Forms?displayProperty=fullName> przestrzeni nazw rozpoczynających się w programie .net core 3,0 Preview 4 zostały usunięte w programie .net core 3,0 RC1.</span><span class="sxs-lookup"><span data-stu-id="c2993-102">A number of APIs accidentally duplicated in the <xref:System.Windows.Forms?displayProperty=fullName> namespace starting in .NET Core 3.0 Preview 4 have been removed in .NET Core 3.0 RC1.</span></span>

#### <a name="change-description"></a><span data-ttu-id="c2993-103">Zmień opis</span><span class="sxs-lookup"><span data-stu-id="c2993-103">Change description</span></span>

<span data-ttu-id="c2993-104">Program .NET Core 3,0 w wersji zapoznawczej 4 przypadkowo duplikuje kilka typów w <xref:System.Windows.Forms?displayProperty=fullName> przestrzeni nazw, które już istniały w <xref:System.ComponentModel.Design?displayProperty=fullName> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="c2993-104">.NET Core 3.0 Preview 4 inadvertently duplicated a number of types in the <xref:System.Windows.Forms?displayProperty=fullName> namespace that already existed in the <xref:System.ComponentModel.Design?displayProperty=fullName> namespace.</span></span> <span data-ttu-id="c2993-105">Począwszy od platformy .NET Core 3,0 RC1, te zduplikowane typy nie są już dostępne.</span><span class="sxs-lookup"><span data-stu-id="c2993-105">Starting with .NET Core 3.0 RC1, these duplicated types are no longer available.</span></span> <span data-ttu-id="c2993-106">Poniższa tabela zawiera listę typów pierwotnych i duplikatów typów:</span><span class="sxs-lookup"><span data-stu-id="c2993-106">The following table shows lists the original type and its duplicated type:</span></span>

> [!div class="mx-tdCol2BreakAll"]
> |<span data-ttu-id="c2993-107">Typ oryginalny</span><span class="sxs-lookup"><span data-stu-id="c2993-107">Original type</span></span>|<span data-ttu-id="c2993-108">Zduplikowany typ</span><span class="sxs-lookup"><span data-stu-id="c2993-108">Duplicated type</span></span>|
> |---|---|
> |<xref:System.ComponentModel.Design.DesignerActionListsChangedEventArgs?displayProperty=fullName>|`System.Windows.Forms.DesignerActionListsChangedEventArgs`|
> |<xref:System.ComponentModel.Design.DesignerActionListsChangedEventHandler?displayProperty=fullName>|`System.Windows.Forms.DesignerActionListsChangedEventHandler`|
> |<xref:System.ComponentModel.Design.DesignerActionListsChangedType?displayProperty=fullName>|`System.Windows.Forms.DesignerActionListsChangedType`|
> |<xref:System.ComponentModel.Design.DesignerActionUIService?displayProperty=fullName>|`System.Windows.Forms.DesignerActionUIService`|
> |<xref:System.ComponentModel.Design.DesignerCommandSet?displayProperty=fullName>|`System.Windows.Forms.DesignerCommandSet`|

#### <a name="version-introduced"></a><span data-ttu-id="c2993-109">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="c2993-109">Version introduced</span></span>

<span data-ttu-id="c2993-110">3,0 RC1</span><span class="sxs-lookup"><span data-stu-id="c2993-110">3.0 RC1</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="c2993-111">Zalecana akcja</span><span class="sxs-lookup"><span data-stu-id="c2993-111">Recommended action</span></span>

<span data-ttu-id="c2993-112">Zaktualizuj kod, aby odwołać się do oryginalnego typu, jak pokazano w kolumnie **pierwotnego typu** tabeli.</span><span class="sxs-lookup"><span data-stu-id="c2993-112">Update the code to reference the original type, as shown in the **Original type** column of the table.</span></span>

#### <a name="category"></a><span data-ttu-id="c2993-113">Kategoria</span><span class="sxs-lookup"><span data-stu-id="c2993-113">Category</span></span>

<span data-ttu-id="c2993-114">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="c2993-114">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="c2993-115">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="c2993-115">Affected APIs</span></span>

- <span data-ttu-id="c2993-116">Brak.</span><span class="sxs-lookup"><span data-stu-id="c2993-116">None.</span></span>

<!--

#### Affected APIs

- Not detectable via API analysis.

-->
