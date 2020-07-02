---
ms.openlocfilehash: d78d083b16ac034c6c393dbc0f6094ee4c6c63c0
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85622377"
---
### <a name="datagridcellspanelbringindexintoview-throws-argumentoutofrangeexception"></a><span data-ttu-id="bc3a6-101">DataGridCellsPanel. BringIndexIntoView zgłasza wyjątku ArgumentOutOfRangeException</span><span class="sxs-lookup"><span data-stu-id="bc3a6-101">DataGridCellsPanel.BringIndexIntoView throws ArgumentOutOfRangeException</span></span>

#### <a name="details"></a><span data-ttu-id="bc3a6-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="bc3a6-102">Details</span></span>

<span data-ttu-id="bc3a6-103"><xref:System.Windows.Controls.DataGrid.ScrollIntoView(System.Object)>działa asynchronicznie, gdy Wirtualizacja kolumny jest włączona, ale szerokość kolumn nie została jeszcze ustalona.</span><span class="sxs-lookup"><span data-stu-id="bc3a6-103"><xref:System.Windows.Controls.DataGrid.ScrollIntoView(System.Object)> will work asynchronously when column virtualization is enabled but the column widths have not yet been determined.</span></span>  <span data-ttu-id="bc3a6-104">Jeśli kolumny zostaną usunięte przed wykonaniem asynchronicznej pracy, <xref:System.ArgumentOutOfRangeException?displayProperty=fullName> może wystąpić.</span><span class="sxs-lookup"><span data-stu-id="bc3a6-104">If columns are removed before the asynchronous work happens, an <xref:System.ArgumentOutOfRangeException?displayProperty=fullName> can occur.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="bc3a6-105">Sugestia</span><span class="sxs-lookup"><span data-stu-id="bc3a6-105">Suggestion</span></span>

<span data-ttu-id="bc3a6-106">Jeden z następujących elementów:</span><span class="sxs-lookup"><span data-stu-id="bc3a6-106">Any one of the following:</span></span><ol><li><span data-ttu-id="bc3a6-107">Uaktualnij do .NET Framework 4,7.</span><span class="sxs-lookup"><span data-stu-id="bc3a6-107">Upgrade to .NET Framework 4.7.</span></span></li><li><span data-ttu-id="bc3a6-108">Zainstaluj najnowszą poprawkę obsługi dla .NET Framework 4.6.2.</span><span class="sxs-lookup"><span data-stu-id="bc3a6-108">Install the latest servicing patch for .NET Framework 4.6.2.</span></span></li><li><span data-ttu-id="bc3a6-109">Należy unikać usuwania kolumn do momentu ukończenia asynchronicznej odpowiedzi <xref:System.Windows.Controls.DataGrid.ScrollIntoView(System.Object)> .</span><span class="sxs-lookup"><span data-stu-id="bc3a6-109">Avoid removing columns until the asynchronous response to <xref:System.Windows.Controls.DataGrid.ScrollIntoView(System.Object)> has completed.</span></span></li></ol>

| <span data-ttu-id="bc3a6-110">Nazwa</span><span class="sxs-lookup"><span data-stu-id="bc3a6-110">Name</span></span>    | <span data-ttu-id="bc3a6-111">Wartość</span><span class="sxs-lookup"><span data-stu-id="bc3a6-111">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="bc3a6-112">Zakres</span><span class="sxs-lookup"><span data-stu-id="bc3a6-112">Scope</span></span>   |<span data-ttu-id="bc3a6-113">Brzeg</span><span class="sxs-lookup"><span data-stu-id="bc3a6-113">Edge</span></span>|
|<span data-ttu-id="bc3a6-114">Wersja</span><span class="sxs-lookup"><span data-stu-id="bc3a6-114">Version</span></span>|<span data-ttu-id="bc3a6-115">4.6.2</span><span class="sxs-lookup"><span data-stu-id="bc3a6-115">4.6.2</span></span>|
|<span data-ttu-id="bc3a6-116">Typ</span><span class="sxs-lookup"><span data-stu-id="bc3a6-116">Type</span></span>|<span data-ttu-id="bc3a6-117">Środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="bc3a6-117">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="bc3a6-118">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="bc3a6-118">Affected APIs</span></span>

-<xref:System.Windows.Controls.DataGrid.ScrollIntoView(System.Object)?displayProperty=nameWithType></li><li><xref:System.Windows.Controls.DataGrid.ScrollIntoView(System.Object,System.Windows.Controls.DataGridColumn)?displayProperty=nameWithType></li></ul>|
