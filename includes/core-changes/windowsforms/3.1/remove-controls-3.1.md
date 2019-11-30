---
ms.openlocfilehash: 7ff8345fd0a3ca30375cf93d22625f89d5d9a053
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/28/2019
ms.locfileid: "74567346"
---
### <a name="removed-controls"></a><span data-ttu-id="b7bf5-101">Usunięte kontrolki</span><span class="sxs-lookup"><span data-stu-id="b7bf5-101">Removed controls</span></span>

<span data-ttu-id="b7bf5-102">Począwszy od platformy .NET Core 3,1, niektóre kontrolki Windows Forms nie są już dostępne.</span><span class="sxs-lookup"><span data-stu-id="b7bf5-102">Starting in .NET Core 3.1, some Windows Forms controls are no longer available.</span></span>

#### <a name="change-description"></a><span data-ttu-id="b7bf5-103">Zmień opis</span><span class="sxs-lookup"><span data-stu-id="b7bf5-103">Change description</span></span>

<span data-ttu-id="b7bf5-104">Począwszy od platformy .NET Core 3,1, różne kontrolki Windows Forms nie są już dostępne.</span><span class="sxs-lookup"><span data-stu-id="b7bf5-104">Starting with .NET Core 3.1, various Windows Forms controls are no longer available.</span></span> <span data-ttu-id="b7bf5-105">Kontrolki zamiany, które mają lepszy projekt i pomoc techniczną, zostały wprowadzone w .NET Framework 2,0.</span><span class="sxs-lookup"><span data-stu-id="b7bf5-105">Replacement controls that have better design and support were introduced in .NET Framework 2.0.</span></span> <span data-ttu-id="b7bf5-106">Przestarzałe formanty zostały wcześniej usunięte z przyborników projektanta, ale były nadal dostępne do użycia.</span><span class="sxs-lookup"><span data-stu-id="b7bf5-106">The deprecated controls were previously removed from designer toolboxes but were still available to be used.</span></span>

<span data-ttu-id="b7bf5-107">Następujące typy nie są już dostępne:</span><span class="sxs-lookup"><span data-stu-id="b7bf5-107">The following types are no longer available:</span></span>

- <xref:System.Windows.Forms.Menu>
- <xref:System.Windows.Forms.Menu.MenuItemCollection>
- <xref:System.Windows.Forms.MainMenu>
- <xref:System.Windows.Forms.ContextMenu>
- <xref:System.Windows.Forms.MenuItem>
- <xref:System.Windows.Forms.ToolBar>
- <xref:System.Windows.Forms.ToolBarAppearance>
- <xref:System.Windows.Forms.ToolBarButton>
- <xref:System.Windows.Forms.ToolBar.ToolBarButtonCollection>
- <xref:System.Windows.Forms.ToolBarButtonClickEventArgs>
- <xref:System.Windows.Forms.ToolBarButtonStyle>
- <xref:System.Windows.Forms.ToolBarTextAlign>
- <xref:System.Windows.Forms.DataGrid>
- <xref:System.Windows.Forms.DataGridBoolColumn>
- <xref:System.Windows.Forms.DataGridCell>
- <xref:System.Windows.Forms.DataGridColumnStyle>
- <xref:System.Windows.Forms.DataGridLineStyle>
- <xref:System.Windows.Forms.DataGridParentRowsLabelStyle>
- <xref:System.Windows.Forms.DataGridPreferredColumnWidthTypeConverter>
- <xref:System.Windows.Forms.DataGridTableStyle>
- <xref:System.Windows.Forms.DataGridTextBox>
- <xref:System.Windows.Forms.DataGridTextBoxColumn>
- <xref:System.Windows.Forms.GridColumnStylesCollection>
- <xref:System.Windows.Forms.GridTablesFactory>
- <xref:System.Windows.Forms.GridTableStylesCollection>
- <xref:System.Windows.Forms.IDataGridEditingService>
- <xref:System.Windows.Forms.DataGrid.HitTestType>
- <xref:System.Windows.Forms.Design.IMenuEditorService>

#### <a name="version-introduced"></a><span data-ttu-id="b7bf5-108">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="b7bf5-108">Version introduced</span></span>

<span data-ttu-id="b7bf5-109">3,1</span><span class="sxs-lookup"><span data-stu-id="b7bf5-109">3.1</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="b7bf5-110">Zalecane działanie</span><span class="sxs-lookup"><span data-stu-id="b7bf5-110">Recommended action</span></span>

<span data-ttu-id="b7bf5-111">Każda z usuniętych kontrolek ma zalecaną kontrolę zamiany.</span><span class="sxs-lookup"><span data-stu-id="b7bf5-111">Each removed control has a recommended replacement control.</span></span> <span data-ttu-id="b7bf5-112">Zapoznaj się z poniższą tabelą:</span><span class="sxs-lookup"><span data-stu-id="b7bf5-112">Refer to the following table:</span></span>

| <span data-ttu-id="b7bf5-113">Usunięty formant (API)</span><span class="sxs-lookup"><span data-stu-id="b7bf5-113">Removed control (API)</span></span> | <span data-ttu-id="b7bf5-114">Zalecane zastąpienie</span><span class="sxs-lookup"><span data-stu-id="b7bf5-114">Recommended replacement</span></span> | <span data-ttu-id="b7bf5-115">Skojarzone interfejsy API, które zostały usunięte</span><span class="sxs-lookup"><span data-stu-id="b7bf5-115">Associated APIs that are removed</span></span> |
|-|-|-|
| <span data-ttu-id="b7bf5-116">DataGrid</span><span class="sxs-lookup"><span data-stu-id="b7bf5-116">DataGrid</span></span> | <span data-ttu-id="b7bf5-117">DataGridView</span><span class="sxs-lookup"><span data-stu-id="b7bf5-117">DataGridView</span></span> | <span data-ttu-id="b7bf5-118">DataGridCell, DataGridRow, DataGridTableCollection, DataGridColumnCollection, Element DataGridTableStyle, DataGridColumnStyle, datalinii siatki, DataGridParentRowsLabel, DataGridParentRowsLabelStyle, DataGridBoolColumn, DataGridTextBox, GridColumnStylesCollection, GridTableStylesCollection, HitTestType</span><span class="sxs-lookup"><span data-stu-id="b7bf5-118">DataGridCell, DataGridRow, DataGridTableCollection, DataGridColumnCollection, DataGridTableStyle, DataGridColumnStyle, DataGridLineStyle, DataGridParentRowsLabel, DataGridParentRowsLabelStyle, DataGridBoolColumn, DataGridTextBox, GridColumnStylesCollection, GridTableStylesCollection, HitTestType</span></span> |
| <span data-ttu-id="b7bf5-119">ToolBar</span><span class="sxs-lookup"><span data-stu-id="b7bf5-119">ToolBar</span></span> | <span data-ttu-id="b7bf5-120">ToolStrip</span><span class="sxs-lookup"><span data-stu-id="b7bf5-120">ToolStrip</span></span> | <span data-ttu-id="b7bf5-121">ToolBarAppearance</span><span class="sxs-lookup"><span data-stu-id="b7bf5-121">ToolBarAppearance</span></span> |
| <span data-ttu-id="b7bf5-122">ToolBarButton</span><span class="sxs-lookup"><span data-stu-id="b7bf5-122">ToolBarButton</span></span> | <span data-ttu-id="b7bf5-123">Element ToolStripButton</span><span class="sxs-lookup"><span data-stu-id="b7bf5-123">ToolStripButton</span></span> | <span data-ttu-id="b7bf5-124">ToolBarButtonClickEventArgs, ToolBarButtonClickEventHandler, ToolBarButton, ToolBarTextAlign</span><span class="sxs-lookup"><span data-stu-id="b7bf5-124">ToolBarButtonClickEventArgs, ToolBarButtonClickEventHandler, ToolBarButtonStyle, ToolBarTextAlign</span></span>|
| <span data-ttu-id="b7bf5-125">ContextMenu</span><span class="sxs-lookup"><span data-stu-id="b7bf5-125">ContextMenu</span></span> | <span data-ttu-id="b7bf5-126">ContextMenuStrip</span><span class="sxs-lookup"><span data-stu-id="b7bf5-126">ContextMenuStrip</span></span> | |
| <span data-ttu-id="b7bf5-127">Menu</span><span class="sxs-lookup"><span data-stu-id="b7bf5-127">Menu</span></span> | <span data-ttu-id="b7bf5-128">ToolStripDropDown, ToolstripDropDownMenu</span><span class="sxs-lookup"><span data-stu-id="b7bf5-128">ToolStripDropDown, ToolstripDropDownMenu</span></span> | <span data-ttu-id="b7bf5-129">MenuItemCollection</span><span class="sxs-lookup"><span data-stu-id="b7bf5-129">MenuItemCollection</span></span> |
| <span data-ttu-id="b7bf5-130">MainMenu</span><span class="sxs-lookup"><span data-stu-id="b7bf5-130">MainMenu</span></span> | <span data-ttu-id="b7bf5-131">MenuStrip</span><span class="sxs-lookup"><span data-stu-id="b7bf5-131">MenuStrip</span></span> | |
| <span data-ttu-id="b7bf5-132">MenuItem</span><span class="sxs-lookup"><span data-stu-id="b7bf5-132">MenuItem</span></span> | <span data-ttu-id="b7bf5-133">ToolstripMenuItem</span><span class="sxs-lookup"><span data-stu-id="b7bf5-133">ToolstripMenuItem</span></span> | |

#### <a name="category"></a><span data-ttu-id="b7bf5-134">Kategoria</span><span class="sxs-lookup"><span data-stu-id="b7bf5-134">Category</span></span>

<span data-ttu-id="b7bf5-135">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b7bf5-135">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="b7bf5-136">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="b7bf5-136">Affected APIs</span></span>

- <xref:System.Windows.Forms.Menu?displayProperty=nameWithType>
- <xref:System.Windows.Forms.Menu.MenuItemCollection?displayProperty=nameWithType>
- <xref:System.Windows.Forms.MainMenu?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ContextMenu?displayProperty=nameWithType>
- <xref:System.Windows.Forms.MenuItem?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ToolBar?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ToolBarAppearance?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ToolBarButton?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ToolBar.ToolBarButtonCollection?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ToolBarButtonClickEventArgs?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ToolBarButtonStyle?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ToolBarTextAlign?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGrid?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridBoolColumn?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridCell?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridColumnStyle?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridLineStyle?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridParentRowsLabelStyle?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridPreferredColumnWidthTypeConverter?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridTableStyle?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridTextBox?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridTextBoxColumn?displayProperty=nameWithType>
- <xref:System.Windows.Forms.GridColumnStylesCollection?displayProperty=nameWithType>
- <xref:System.Windows.Forms.GridTablesFactory?displayProperty=nameWithType>
- <xref:System.Windows.Forms.GridTableStylesCollection?displayProperty=nameWithType>
- <xref:System.Windows.Forms.IDataGridEditingService?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGrid.HitTestType?displayProperty=nameWithType>
- <xref:System.Windows.Forms.Design.IMenuEditorService?displayProperty=nameWithType>

<!-- 

### Affected APIs

- `T:System.Windows.Forms.Menu`
- `T:System.Windows.Forms.Menu.MenuItemCollection`
- `T:System.Windows.Forms.MainMenu`
- `T:System.Windows.Forms.ContextMenu`
- `T:System.Windows.Forms.MenuItem`
- `T:System.Windows.Forms.ToolBar`
- `T:System.Windows.Forms.ToolBarAppearance`
- `T:System.Windows.Forms.ToolBarButton`
- `T:System.Windows.Forms.ToolBar.ToolBarButtonCollection`
- `T:System.Windows.Forms.ToolBarButtonClickEventArgs`
- `T:System.Windows.Forms.ToolBarButtonStyle`
- `T:System.Windows.Forms.ToolBarTextAlign`
- `T:System.Windows.Forms.DataGrid`
- `T:System.Windows.Forms.DataGridBoolColumn`
- `T:System.Windows.Forms.DataGridCell`
- `T:System.Windows.Forms.DataGridColumnStyle`
- `T:System.Windows.Forms.DataGridLineStyle`
- `T:System.Windows.Forms.DataGridParentRowsLabelStyle`
- `T:System.Windows.Forms.DataGridPreferredColumnWidthTypeConverter`
- `T:System.Windows.Forms.DataGridTableStyle`
- `T:System.Windows.Forms.DataGridTextBox`
- `T:System.Windows.Forms.DataGridTextBoxColumn`
- `T:System.Windows.Forms.GridColumnStylesCollection`
- `T:System.Windows.Forms.GridTablesFactory`
- `T:System.Windows.Forms.GridTableStylesCollection`
- `T:System.Windows.Forms.IDataGridEditingService`
- `T:System.Windows.Forms.DataGrid.HitTestType`
- `T:System.Windows.Forms.Design.IMenuEditorService`

-->
