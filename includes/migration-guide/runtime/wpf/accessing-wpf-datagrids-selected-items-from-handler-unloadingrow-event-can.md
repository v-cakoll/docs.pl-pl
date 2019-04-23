---
ms.openlocfilehash: cda5df4b673412a7c8c59f80f89c19c13dc81dc1
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59804699"
---
### <a name="accessing-a-wpf-datagrids-selected-items-from-a-handler-of-the-datagrids-unloadingrow-event-can-cause-a-nullreferenceexception"></a><span data-ttu-id="99797-101">Uzyskiwanie dostępu do elementu DataGrid WPF wybrane elementy z programu obsługi zdarzeń UnloadingRow w elemencie DataGrid mogą powodować obiektu NullReferenceException</span><span class="sxs-lookup"><span data-stu-id="99797-101">Accessing a WPF DataGrid's selected items from a handler of the DataGrid's UnloadingRow event can cause a NullReferenceException</span></span>

|   |   |
|---|---|
|<span data-ttu-id="99797-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="99797-102">Details</span></span>|<span data-ttu-id="99797-103">Z powodu błędów w programie .NET Framework 4.5, programy obsługi zdarzeń dla <xref:System.Windows.Controls.DataGrid> wydarzenia związane z usunięcie wiersza może spowodować, że <xref:System.NullReferenceException?displayProperty=name> zostanie wygenerowany, jeśli uzyskują oni dostęp do <xref:System.Windows.Controls.DataGrid>firmy <xref:System.Windows.Controls.Primitives.Selector.SelectedItem?displayProperty=name> lub <xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems?displayProperty=name> właściwości.</span><span class="sxs-lookup"><span data-stu-id="99797-103">Due to a bug in the .NET Framework 4.5, event handlers for <xref:System.Windows.Controls.DataGrid> events involving the removal of a row can cause a <xref:System.NullReferenceException?displayProperty=name> to be thrown if they access the <xref:System.Windows.Controls.DataGrid>'s <xref:System.Windows.Controls.Primitives.Selector.SelectedItem?displayProperty=name> or <xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems?displayProperty=name> properties.</span></span>|
|<span data-ttu-id="99797-104">Sugestia</span><span class="sxs-lookup"><span data-stu-id="99797-104">Suggestion</span></span>|<span data-ttu-id="99797-105">Ten problem został rozwiązany w .NET Framework 4.6 i może zostać zlikwidowane przez uaktualnienie do wersji programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="99797-105">This issue has been fixed in the .NET Framework 4.6 and may be addressed by upgrading to that version of the .NET Framework.</span></span>|
|<span data-ttu-id="99797-106">Zakres</span><span class="sxs-lookup"><span data-stu-id="99797-106">Scope</span></span>|<span data-ttu-id="99797-107">Mały</span><span class="sxs-lookup"><span data-stu-id="99797-107">Minor</span></span>|
|<span data-ttu-id="99797-108">Wersja</span><span class="sxs-lookup"><span data-stu-id="99797-108">Version</span></span>|<span data-ttu-id="99797-109">4.5</span><span class="sxs-lookup"><span data-stu-id="99797-109">4.5</span></span>|
|<span data-ttu-id="99797-110">Typ</span><span class="sxs-lookup"><span data-stu-id="99797-110">Type</span></span>|<span data-ttu-id="99797-111">Środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="99797-111">Runtime</span></span>|
|<span data-ttu-id="99797-112">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="99797-112">Affected APIs</span></span>|<ul><li><xref:System.Windows.Controls.DataGrid.UnloadingRow?displayProperty=nameWithType></li><li><xref:System.Windows.Controls.DataGrid.UnloadingRowDetails?displayProperty=nameWithType></li></ul>|
