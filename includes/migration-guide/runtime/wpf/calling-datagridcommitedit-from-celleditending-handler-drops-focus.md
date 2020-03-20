---
ms.openlocfilehash: e2d63d85adce64db6e00b62ec17f55ae71ce3052
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "67803206"
---
### <a name="calling-datagridcommitedit-from-a-celleditending-handler-drops-focus"></a><span data-ttu-id="ff0cf-101">Wywołanie DataGrid.CommitEdit z programu obsługi CellEditEnding spada fokus</span><span class="sxs-lookup"><span data-stu-id="ff0cf-101">Calling DataGrid.CommitEdit from a CellEditEnding handler drops focus</span></span>

|   |   |
|---|---|
|<span data-ttu-id="ff0cf-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="ff0cf-102">Details</span></span>|<span data-ttu-id="ff0cf-103"><xref:System.Windows.Controls.DataGrid.CommitEdit> Wywołanie z <xref:System.Windows.Controls.DataGrid?displayProperty=name>jednego <xref:System.Windows.Controls.DataGrid.CellEditEnding?displayProperty=name> z programów <xref:System.Windows.Controls.DataGrid?displayProperty=name> obsługi zdarzeń powoduje utratę fokusu.</span><span class="sxs-lookup"><span data-stu-id="ff0cf-103">Calling <xref:System.Windows.Controls.DataGrid.CommitEdit> from one of the <xref:System.Windows.Controls.DataGrid?displayProperty=name>'s <xref:System.Windows.Controls.DataGrid.CellEditEnding?displayProperty=name> event handlers causes the <xref:System.Windows.Controls.DataGrid?displayProperty=name> to lose focus.</span></span>|
|<span data-ttu-id="ff0cf-104">Sugestia</span><span class="sxs-lookup"><span data-stu-id="ff0cf-104">Suggestion</span></span>|<span data-ttu-id="ff0cf-105">Ten błąd został naprawiony w .NET Framework 4.5.2, dzięki czemu można go uniknąć, uaktualniając program .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="ff0cf-105">This bug has been fixed in the .NET Framework 4.5.2, so it can be avoided by upgrading the .NET Framework.</span></span> <span data-ttu-id="ff0cf-106">Alternatywnie można tego uniknąć, wyraźnie wybierając <xref:System.Windows.Controls.DataGrid?displayProperty=name> ponownie po <xref:System.Windows.Controls.DataGrid.CommitEdit?displayProperty=name>wywołaniu .</span><span class="sxs-lookup"><span data-stu-id="ff0cf-106">Alternatively, it can be avoided by explicitly re-selecting the <xref:System.Windows.Controls.DataGrid?displayProperty=name> after calling <xref:System.Windows.Controls.DataGrid.CommitEdit?displayProperty=name>.</span></span>|
|<span data-ttu-id="ff0cf-107">Zakres</span><span class="sxs-lookup"><span data-stu-id="ff0cf-107">Scope</span></span>|<span data-ttu-id="ff0cf-108">Brzeg</span><span class="sxs-lookup"><span data-stu-id="ff0cf-108">Edge</span></span>|
|<span data-ttu-id="ff0cf-109">Wersja</span><span class="sxs-lookup"><span data-stu-id="ff0cf-109">Version</span></span>|<span data-ttu-id="ff0cf-110">4.5</span><span class="sxs-lookup"><span data-stu-id="ff0cf-110">4.5</span></span>|
|<span data-ttu-id="ff0cf-111">Typ</span><span class="sxs-lookup"><span data-stu-id="ff0cf-111">Type</span></span>|<span data-ttu-id="ff0cf-112">Środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="ff0cf-112">Runtime</span></span>|
|<span data-ttu-id="ff0cf-113">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="ff0cf-113">Affected APIs</span></span>|<ul><li><xref:System.Windows.Controls.DataGrid.CommitEdit?displayProperty=nameWithType></li><li><xref:System.Windows.Controls.DataGrid.CommitEdit(System.Windows.Controls.DataGridEditingUnit,System.Boolean)?displayProperty=nameWithType></li></ul>|
