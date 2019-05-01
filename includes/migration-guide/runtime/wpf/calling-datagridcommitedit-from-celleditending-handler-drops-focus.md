---
ms.openlocfilehash: e2d63d85adce64db6e00b62ec17f55ae71ce3052
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61649341"
---
### <a name="calling-datagridcommitedit-from-a-celleditending-handler-drops-focus"></a><span data-ttu-id="a325a-101">Wywoływanie DataGrid.CommitEdit z obsługi CellEditEnding spada koncentracji uwagi</span><span class="sxs-lookup"><span data-stu-id="a325a-101">Calling DataGrid.CommitEdit from a CellEditEnding handler drops focus</span></span>

|   |   |
|---|---|
|<span data-ttu-id="a325a-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="a325a-102">Details</span></span>|<span data-ttu-id="a325a-103">Wywoływanie <xref:System.Windows.Controls.DataGrid.CommitEdit> z jednego z <xref:System.Windows.Controls.DataGrid?displayProperty=name>firmy <xref:System.Windows.Controls.DataGrid.CellEditEnding?displayProperty=name> powoduje, że procedury obsługi zdarzeń <xref:System.Windows.Controls.DataGrid?displayProperty=name> utratę fokus.</span><span class="sxs-lookup"><span data-stu-id="a325a-103">Calling <xref:System.Windows.Controls.DataGrid.CommitEdit> from one of the <xref:System.Windows.Controls.DataGrid?displayProperty=name>'s <xref:System.Windows.Controls.DataGrid.CellEditEnding?displayProperty=name> event handlers causes the <xref:System.Windows.Controls.DataGrid?displayProperty=name> to lose focus.</span></span>|
|<span data-ttu-id="a325a-104">Sugestia</span><span class="sxs-lookup"><span data-stu-id="a325a-104">Suggestion</span></span>|<span data-ttu-id="a325a-105">Ten błąd został naprawiony w programie .NET Framework 4.5.2, dzięki czemu można uniknąć przez uaktualnienie programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="a325a-105">This bug has been fixed in the .NET Framework 4.5.2, so it can be avoided by upgrading the .NET Framework.</span></span> <span data-ttu-id="a325a-106">Alternatywnie można należy unikać ponownie, wybierając jawnie <xref:System.Windows.Controls.DataGrid?displayProperty=name> po wywołaniu <xref:System.Windows.Controls.DataGrid.CommitEdit?displayProperty=name>.</span><span class="sxs-lookup"><span data-stu-id="a325a-106">Alternatively, it can be avoided by explicitly re-selecting the <xref:System.Windows.Controls.DataGrid?displayProperty=name> after calling <xref:System.Windows.Controls.DataGrid.CommitEdit?displayProperty=name>.</span></span>|
|<span data-ttu-id="a325a-107">Zakres</span><span class="sxs-lookup"><span data-stu-id="a325a-107">Scope</span></span>|<span data-ttu-id="a325a-108">Krawędź</span><span class="sxs-lookup"><span data-stu-id="a325a-108">Edge</span></span>|
|<span data-ttu-id="a325a-109">Wersja</span><span class="sxs-lookup"><span data-stu-id="a325a-109">Version</span></span>|<span data-ttu-id="a325a-110">4.5</span><span class="sxs-lookup"><span data-stu-id="a325a-110">4.5</span></span>|
|<span data-ttu-id="a325a-111">Typ</span><span class="sxs-lookup"><span data-stu-id="a325a-111">Type</span></span>|<span data-ttu-id="a325a-112">Środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="a325a-112">Runtime</span></span>|
|<span data-ttu-id="a325a-113">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="a325a-113">Affected APIs</span></span>|<ul><li><xref:System.Windows.Controls.DataGrid.CommitEdit?displayProperty=nameWithType></li><li><xref:System.Windows.Controls.DataGrid.CommitEdit(System.Windows.Controls.DataGridEditingUnit,System.Boolean)?displayProperty=nameWithType></li></ul>|
