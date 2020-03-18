---
ms.openlocfilehash: e609b8006846cd202a6a7eeec2529cf1fbb09e7c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75936983"
---
### <a name="duplicated-apis-removed-from-windows-forms"></a><span data-ttu-id="4f5b7-101">Zduplikowane interfejsy API usunięte z formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="4f5b7-101">Duplicated APIs removed from Windows Forms</span></span>

<span data-ttu-id="4f5b7-102">Liczba interfejsów API przypadkowo zduplikowanych w obszarze <xref:System.Windows.Forms?displayProperty=fullName> nazw, począwszy od .NET Core 3.0 Preview 4, została usunięta w .NET Core 3.0 RC1.</span><span class="sxs-lookup"><span data-stu-id="4f5b7-102">A number of APIs accidentally duplicated in the <xref:System.Windows.Forms?displayProperty=fullName> namespace starting in .NET Core 3.0 Preview 4 have been removed in .NET Core 3.0 RC1.</span></span>

#### <a name="change-description"></a><span data-ttu-id="4f5b7-103">Zmień opis</span><span class="sxs-lookup"><span data-stu-id="4f5b7-103">Change description</span></span>

<span data-ttu-id="4f5b7-104">.NET Core 3.0 Preview 4 przypadkowo zduplikował liczbę typów w obszarze <xref:System.Windows.Forms?displayProperty=fullName> nazw, które już istniały w obszarze <xref:System.ComponentModel.Design?displayProperty=fullName> nazw.</span><span class="sxs-lookup"><span data-stu-id="4f5b7-104">.NET Core 3.0 Preview 4 inadvertently duplicated a number of types in the <xref:System.Windows.Forms?displayProperty=fullName> namespace that already existed in the <xref:System.ComponentModel.Design?displayProperty=fullName> namespace.</span></span> <span data-ttu-id="4f5b7-105">Począwszy od .NET Core 3.0 RC1, te zduplikowane typy nie są już dostępne.</span><span class="sxs-lookup"><span data-stu-id="4f5b7-105">Starting with .NET Core 3.0 RC1, these duplicated types are no longer available.</span></span> <span data-ttu-id="4f5b7-106">W poniższej tabeli przedstawiono oryginalny typ i jego zduplikowany typ:</span><span class="sxs-lookup"><span data-stu-id="4f5b7-106">The following table shows lists the original type and its duplicated type:</span></span>

> [!div class="mx-tdCol2BreakAll"]
> |<span data-ttu-id="4f5b7-107">Typ oryginalny</span><span class="sxs-lookup"><span data-stu-id="4f5b7-107">Original type</span></span>|<span data-ttu-id="4f5b7-108">Zduplikowany typ</span><span class="sxs-lookup"><span data-stu-id="4f5b7-108">Duplicated type</span></span>|
> |---|---|
> |<xref:System.ComponentModel.Design.DesignerActionListsChangedEventArgs?displayProperty=fullName>|`System.Windows.Forms.DesignerActionListsChangedEventArgs`|
> |<xref:System.ComponentModel.Design.DesignerActionListsChangedEventHandler?displayProperty=fullName>|`System.Windows.Forms.DesignerActionListsChangedEventHandler`|
> |<xref:System.ComponentModel.Design.DesignerActionListsChangedType?displayProperty=fullName>|`System.Windows.Forms.DesignerActionListsChangedType`|
> |<xref:System.ComponentModel.Design.DesignerActionUIService?displayProperty=fullName>|`System.Windows.Forms.DesignerActionUIService`|
> |<xref:System.ComponentModel.Design.DesignerCommandSet?displayProperty=fullName>|`System.Windows.Forms.DesignerCommandSet`|

#### <a name="version-introduced"></a><span data-ttu-id="4f5b7-109">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="4f5b7-109">Version introduced</span></span>

<span data-ttu-id="4f5b7-110">3.0 Rc1</span><span class="sxs-lookup"><span data-stu-id="4f5b7-110">3.0 RC1</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="4f5b7-111">Zalecana akcja</span><span class="sxs-lookup"><span data-stu-id="4f5b7-111">Recommended action</span></span>

<span data-ttu-id="4f5b7-112">Zaktualizuj kod, aby odwoływać się do oryginalnego typu, jak pokazano w kolumnie **Typ oryginalny** tabeli.</span><span class="sxs-lookup"><span data-stu-id="4f5b7-112">Update the code to reference the original type, as shown in the **Original type** column of the table.</span></span>

#### <a name="category"></a><span data-ttu-id="4f5b7-113">Kategoria</span><span class="sxs-lookup"><span data-stu-id="4f5b7-113">Category</span></span>

<span data-ttu-id="4f5b7-114">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="4f5b7-114">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="4f5b7-115">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="4f5b7-115">Affected APIs</span></span>

- <span data-ttu-id="4f5b7-116">Nie wykrywalne za pomocą analizy Interfejsu API.</span><span class="sxs-lookup"><span data-stu-id="4f5b7-116">Not detectable via API analysis.</span></span>

<!--

### Affected APIs

- Not detectable via API analysis.

-->
