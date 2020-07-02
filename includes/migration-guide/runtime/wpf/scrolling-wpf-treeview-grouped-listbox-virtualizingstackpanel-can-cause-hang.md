---
ms.openlocfilehash: 1be68c2968d0eaa9024007bcf37abf9e44c36f1c
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85622149"
---
### <a name="scrolling-a-wpf-treeview-or-grouped-listbox-in-a-virtualizingstackpanel-can-cause-a-hang"></a><span data-ttu-id="d5e21-101">Przewijanie drzewa WPF lub zgrupowane pole listy w VirtualizingStackPanel może spowodować zawieszenie</span><span class="sxs-lookup"><span data-stu-id="d5e21-101">Scrolling a WPF TreeView or grouped ListBox in a VirtualizingStackPanel can cause a hang</span></span>

#### <a name="details"></a><span data-ttu-id="d5e21-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="d5e21-102">Details</span></span>

<span data-ttu-id="d5e21-103">W .NET Framework v 4.5, przewinięcie WPF <xref:System.Windows.Controls.TreeView?displayProperty=fullName> w zwirtualizowanym panelu stosu może spowodować zawieszenie, jeśli w okienku ekranu pojawią się marginesy (między elementami na <xref:System.Windows.Controls.TreeView?displayProperty=fullName> przykład lub w elemencie ItemsPresenter).</span><span class="sxs-lookup"><span data-stu-id="d5e21-103">In the .NET Framework v4.5, scrolling a WPF <xref:System.Windows.Controls.TreeView?displayProperty=fullName> in a virtualized stack panel can cause hangs if there are margins in the viewport (between the items in the <xref:System.Windows.Controls.TreeView?displayProperty=fullName>, for example, or on an ItemsPresenter element).</span></span> <span data-ttu-id="d5e21-104">Ponadto w niektórych przypadkach różne elementy w widoku mogą spowodować niestabilność nawet wtedy, gdy nie ma marginesów.</span><span class="sxs-lookup"><span data-stu-id="d5e21-104">Additionally, in some cases, different sized items in the view can cause instability even if there are no margins.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="d5e21-105">Sugestia</span><span class="sxs-lookup"><span data-stu-id="d5e21-105">Suggestion</span></span>

<span data-ttu-id="d5e21-106">Tę usterkę można uniknąć przez uaktualnienie do .NET Framework 4.5.1.</span><span class="sxs-lookup"><span data-stu-id="d5e21-106">This bug can be avoided by upgrading to .NET Framework 4.5.1.</span></span> <span data-ttu-id="d5e21-107">Alternatywnie marginesy mogą być usuwane z kolekcji widoku (na przykład <xref:System.Windows.Controls.TreeView?displayProperty=fullName> s) w zwirtualizowanych panelach stosu, jeśli wszystkie zawarte elementy mają ten sam rozmiar.</span><span class="sxs-lookup"><span data-stu-id="d5e21-107">Alternatively, margins can be removed from view collections (like <xref:System.Windows.Controls.TreeView?displayProperty=fullName>s) within virtualized stack panels if all contained items are the same size.</span></span>

| <span data-ttu-id="d5e21-108">Nazwa</span><span class="sxs-lookup"><span data-stu-id="d5e21-108">Name</span></span>    | <span data-ttu-id="d5e21-109">Wartość</span><span class="sxs-lookup"><span data-stu-id="d5e21-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="d5e21-110">Zakres</span><span class="sxs-lookup"><span data-stu-id="d5e21-110">Scope</span></span>   |<span data-ttu-id="d5e21-111">Duży</span><span class="sxs-lookup"><span data-stu-id="d5e21-111">Major</span></span>|
|<span data-ttu-id="d5e21-112">Wersja</span><span class="sxs-lookup"><span data-stu-id="d5e21-112">Version</span></span>|<span data-ttu-id="d5e21-113">4.5</span><span class="sxs-lookup"><span data-stu-id="d5e21-113">4.5</span></span>|
|<span data-ttu-id="d5e21-114">Typ</span><span class="sxs-lookup"><span data-stu-id="d5e21-114">Type</span></span>|<span data-ttu-id="d5e21-115">Środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="d5e21-115">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="d5e21-116">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="d5e21-116">Affected APIs</span></span>

-<xref:System.Windows.Controls.VirtualizingStackPanel.SetIsVirtualizing(System.Windows.DependencyObject,System.Boolean)?displayProperty=nameWithType></li></ul>|
