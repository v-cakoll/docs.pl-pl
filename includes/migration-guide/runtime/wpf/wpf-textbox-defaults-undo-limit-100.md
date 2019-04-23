---
ms.openlocfilehash: de79182e326082786c1e0691f8888e30cd410f5d
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59235419"
---
### <a name="wpf-textbox-defaults-to-undo-limit-of-100"></a><span data-ttu-id="f3b84-101">Domyślnie pole tekstowe WPF Cofnij granicę równą 100</span><span class="sxs-lookup"><span data-stu-id="f3b84-101">WPF TextBox defaults to undo limit of 100</span></span>

|   |   |
|---|---|
|<span data-ttu-id="f3b84-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="f3b84-102">Details</span></span>|<span data-ttu-id="f3b84-103">W programie .NET Framework 4.5 domyślny limit cofania WPF textbox wynosi 100 (w przeciwieństwie do zwrócenia w .NET Framework 4.0)</span><span class="sxs-lookup"><span data-stu-id="f3b84-103">In .NET Framework 4.5, the default undo limit for a WPF textbox is 100 (as opposed to being unlimited in .NET Framework 4.0)</span></span>|
|<span data-ttu-id="f3b84-104">Sugestia</span><span class="sxs-lookup"><span data-stu-id="f3b84-104">Suggestion</span></span>|<span data-ttu-id="f3b84-105">Jeśli limit 100 cofania jest zbyt niska, limit można jawnie ustawić za pomocą <xref:System.Windows.Controls.Primitives.TextBoxBase.UndoLimit></span><span class="sxs-lookup"><span data-stu-id="f3b84-105">If an undo limit of 100 is too low, the limit can be set explicitly with <xref:System.Windows.Controls.Primitives.TextBoxBase.UndoLimit></span></span>|
|<span data-ttu-id="f3b84-106">Zakres</span><span class="sxs-lookup"><span data-stu-id="f3b84-106">Scope</span></span>|<span data-ttu-id="f3b84-107">Krawędź</span><span class="sxs-lookup"><span data-stu-id="f3b84-107">Edge</span></span>|
|<span data-ttu-id="f3b84-108">Wersja</span><span class="sxs-lookup"><span data-stu-id="f3b84-108">Version</span></span>|<span data-ttu-id="f3b84-109">4.5</span><span class="sxs-lookup"><span data-stu-id="f3b84-109">4.5</span></span>|
|<span data-ttu-id="f3b84-110">Typ</span><span class="sxs-lookup"><span data-stu-id="f3b84-110">Type</span></span>|<span data-ttu-id="f3b84-111">Środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="f3b84-111">Runtime</span></span>|
|<span data-ttu-id="f3b84-112">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="f3b84-112">Affected APIs</span></span>|<ul><li><xref:System.Windows.Controls.TextBox?displayProperty=nameWithType></li></ul>|
