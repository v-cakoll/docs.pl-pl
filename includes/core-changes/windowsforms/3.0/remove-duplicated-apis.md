---
ms.openlocfilehash: 3d0a90a57c2b1c2759b8420e74c284668d54e9cb
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/28/2019
ms.locfileid: "74644041"
---
### <a name="duplicated-apis-removed-from-windows-forms"></a><span data-ttu-id="cf897-101">Zduplikowane interfejsy API zostały usunięte z Windows Forms</span><span class="sxs-lookup"><span data-stu-id="cf897-101">Duplicated APIs removed from Windows Forms</span></span>

<span data-ttu-id="cf897-102">Wiele interfejsów API przypadkowo zduplikowanych w przestrzeni nazw <xref:System.Windows.Forms?displayProperty=fullName>, począwszy od platformy .NET Core 3,0 w wersji zapoznawczej 4, zostało usuniętych w programie .NET Core 3,0 RC1.</span><span class="sxs-lookup"><span data-stu-id="cf897-102">A number of APIs accidentally duplicated in the <xref:System.Windows.Forms?displayProperty=fullName> namespace starting in .NET Core 3.0 Preview 4 have been removed in .NET Core 3.0 RC1.</span></span>

#### <a name="change-description"></a><span data-ttu-id="cf897-103">Zmień opis</span><span class="sxs-lookup"><span data-stu-id="cf897-103">Change description</span></span>

<span data-ttu-id="cf897-104">Program .NET Core 3,0 w wersji zapoznawczej 4 przypadkowo duplikuje kilka typów w przestrzeni nazw <xref:System.Windows.Forms?displayProperty=fullName>, które już istniały w przestrzeni nazw <xref:System.ComponentModel.Design?displayProperty=fullName>.</span><span class="sxs-lookup"><span data-stu-id="cf897-104">.NET Core 3.0 Preview 4 inadvertently duplicated a number of types in the <xref:System.Windows.Forms?displayProperty=fullName> namespace that already existed in the <xref:System.ComponentModel.Design?displayProperty=fullName> namespace.</span></span> <span data-ttu-id="cf897-105">Począwszy od platformy .NET Core 3,0 RC1, te zduplikowane typy nie są już dostępne.</span><span class="sxs-lookup"><span data-stu-id="cf897-105">Starting with .NET Core 3.0 RC1, these duplicated types are no longer available.</span></span> <span data-ttu-id="cf897-106">Poniższa tabela zawiera listę typów pierwotnych i duplikatów typów:</span><span class="sxs-lookup"><span data-stu-id="cf897-106">The following table shows lists the original type and its duplicated type:</span></span>

|<span data-ttu-id="cf897-107">Typ oryginalny</span><span class="sxs-lookup"><span data-stu-id="cf897-107">Original type</span></span>|<span data-ttu-id="cf897-108">Zduplikowany typ</span><span class="sxs-lookup"><span data-stu-id="cf897-108">Duplicated type</span></span>|
|---|---|
|<xref:System.ComponentModel.Design.DesignerActionListsChangedEventArgs?displayProperty=fullName>|`System.Windows.Forms.DesignerActionListsChangedEventArgs`|
|<xref:System.ComponentModel.Design.DesignerActionListsChangedEventHandler?displayProperty=fullName>|`System.Windows.Forms.DesignerActionListsChangedEventHandler`|
|<xref:System.ComponentModel.Design.DesignerActionListsChangedType?displayProperty=fullName>|`System.Windows.Forms.DesignerActionListsChangedType`|
|<xref:System.ComponentModel.Design.DesignerActionUIService?displayProperty=fullName>|`System.Windows.Forms.DesignerActionUIService`|
|<xref:System.ComponentModel.Design.DesignerCommandSet?displayProperty=fullName>|`System.Windows.Forms.DesignerCommandSet`|

#### <a name="version-introduced"></a><span data-ttu-id="cf897-109">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="cf897-109">Version introduced</span></span>

<span data-ttu-id="cf897-110">3,0 RC1</span><span class="sxs-lookup"><span data-stu-id="cf897-110">3.0 RC1</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="cf897-111">Zalecane działanie</span><span class="sxs-lookup"><span data-stu-id="cf897-111">Recommended action</span></span>

<span data-ttu-id="cf897-112">Zaktualizuj kod, aby odwołać się do oryginalnego typu, jak pokazano w kolumnie **pierwotnego typu** tabeli.</span><span class="sxs-lookup"><span data-stu-id="cf897-112">Update the code to reference the original type, as shown in the **Original type** column of the table.</span></span>

#### <a name="category"></a><span data-ttu-id="cf897-113">Kategoria</span><span class="sxs-lookup"><span data-stu-id="cf897-113">Category</span></span>

<span data-ttu-id="cf897-114">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="cf897-114">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="cf897-115">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="cf897-115">Affected APIs</span></span>

- <span data-ttu-id="cf897-116">Nie wykrywalne za pośrednictwem analizy interfejsu API.</span><span class="sxs-lookup"><span data-stu-id="cf897-116">Not detectable via API analysis.</span></span>

<!--

### Affected APIs

- Not detectable via API analysis.

-->
