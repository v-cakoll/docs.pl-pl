---
ms.openlocfilehash: b5f12e648a82ebaba7d09b546e8aa2fc7cd82a37
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/11/2019
ms.locfileid: "67803206"
---
### <a name="calling-datagridcommitedit-from-a-celleditending-handler-drops-focus"></a><span data-ttu-id="1bd65-101">Wywoływanie DataGrid.CommitEdit z obsługi CellEditEnding spada koncentracji uwagi</span><span class="sxs-lookup"><span data-stu-id="1bd65-101">Calling DataGrid.CommitEdit from a CellEditEnding handler drops focus</span></span>

|   |   |
|---|---|
|<span data-ttu-id="1bd65-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="1bd65-102">Details</span></span>|<span data-ttu-id="1bd65-103">Wywoływanie <xref:System.Windows.Controls.DataGrid.CommitEdit> z jednego z <xref:System.Windows.Controls.DataGrid?displayProperty=name>firmy <xref:System.Windows.Controls.DataGrid.CellEditEnding?displayProperty=name> powoduje, że procedury obsługi zdarzeń <xref:System.Windows.Controls.DataGrid?displayProperty=name> utratę fokus.</span><span class="sxs-lookup"><span data-stu-id="1bd65-103">Calling <xref:System.Windows.Controls.DataGrid.CommitEdit> from one of the <xref:System.Windows.Controls.DataGrid?displayProperty=name>'s <xref:System.Windows.Controls.DataGrid.CellEditEnding?displayProperty=name> event handlers causes the <xref:System.Windows.Controls.DataGrid?displayProperty=name> to lose focus.</span></span>|
|<span data-ttu-id="1bd65-104">Sugestia</span><span class="sxs-lookup"><span data-stu-id="1bd65-104">Suggestion</span></span>|<span data-ttu-id="1bd65-105">Ten błąd został naprawiony w programie .NET Framework 4.5.2, dzięki czemu można uniknąć przez uaktualnienie programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="1bd65-105">This bug has been fixed in the .NET Framework 4.5.2, so it can be avoided by upgrading the .NET Framework.</span></span> <span data-ttu-id="1bd65-106">Alternatywnie można należy unikać ponownie, wybierając jawnie <xref:System.Windows.Controls.DataGrid?displayProperty=name> po wywołaniu <xref:System.Windows.Controls.DataGrid.CommitEdit?displayProperty=name>.</span><span class="sxs-lookup"><span data-stu-id="1bd65-106">Alternatively, it can be avoided by explicitly re-selecting the <xref:System.Windows.Controls.DataGrid?displayProperty=name> after calling <xref:System.Windows.Controls.DataGrid.CommitEdit?displayProperty=name>.</span></span>|
|<span data-ttu-id="1bd65-107">Scope</span><span class="sxs-lookup"><span data-stu-id="1bd65-107">Scope</span></span>|<span data-ttu-id="1bd65-108">Krawędź</span><span class="sxs-lookup"><span data-stu-id="1bd65-108">Edge</span></span>|
|<span data-ttu-id="1bd65-109">Wersja</span><span class="sxs-lookup"><span data-stu-id="1bd65-109">Version</span></span>|<span data-ttu-id="1bd65-110">4.5</span><span class="sxs-lookup"><span data-stu-id="1bd65-110">4.5</span></span>|
|<span data-ttu-id="1bd65-111">Typ</span><span class="sxs-lookup"><span data-stu-id="1bd65-111">Type</span></span>|<span data-ttu-id="1bd65-112">Środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="1bd65-112">Runtime</span></span>|
|<span data-ttu-id="1bd65-113">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="1bd65-113">Affected APIs</span></span>|<ul><li><xref:System.Windows.Controls.DataGrid.CommitEdit?displayProperty=nameWithType></li><li><xref:System.Windows.Controls.DataGrid.CommitEdit(System.Windows.Controls.DataGridEditingUnit,System.Boolean)?displayProperty=nameWithType></li></ul>|

