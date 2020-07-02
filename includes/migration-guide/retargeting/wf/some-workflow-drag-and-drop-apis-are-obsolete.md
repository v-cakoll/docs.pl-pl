---
ms.openlocfilehash: b6cb7edcd6bed50efdf59f3321320ac8cd1b1ab8
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617289"
---
### <a name="some-workflow-drag-and-drop-apis-are-obsolete"></a><span data-ttu-id="1bdc9-101">Niektóre interfejsy API przeciągania i upuszczania przepływu pracy są przestarzałe</span><span class="sxs-lookup"><span data-stu-id="1bdc9-101">Some WorkFlow drag-and-drop APIs are obsolete</span></span>

#### <a name="details"></a><span data-ttu-id="1bdc9-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="1bdc9-102">Details</span></span>

<span data-ttu-id="1bdc9-103">Ten interfejs API przeciągania i upuszczania tego przepływu pracy jest przestarzały i spowoduje ostrzeżenia kompilatora, jeśli aplikacja zostanie odbudowana na 4,5.</span><span class="sxs-lookup"><span data-stu-id="1bdc9-103">This WorkFlow drag-and-drop API is obsolete and will cause compiler warnings if the app is rebuilt against 4.5.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="1bdc9-104">Sugestia</span><span class="sxs-lookup"><span data-stu-id="1bdc9-104">Suggestion</span></span>

<span data-ttu-id="1bdc9-105"><xref:System.Activities.Presentation.DragDropHelper?displayProperty=fullName>Zamiast tego należy użyć nowych interfejsów API, które obsługują operacje z wieloma obiektami.</span><span class="sxs-lookup"><span data-stu-id="1bdc9-105">New <xref:System.Activities.Presentation.DragDropHelper?displayProperty=fullName> APIs that support operations with multiple objects should be used instead.</span></span> <span data-ttu-id="1bdc9-106">Alternatywnie można pominąć ostrzeżenia kompilacji lub można je uniknąć przy użyciu starszego kompilatora.</span><span class="sxs-lookup"><span data-stu-id="1bdc9-106">Alternatively, the build warnings can be suppressed or they can be avoided by using an older compiler.</span></span> <span data-ttu-id="1bdc9-107">Interfejsy API są nadal obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="1bdc9-107">The APIs are still supported.</span></span>

| <span data-ttu-id="1bdc9-108">Nazwa</span><span class="sxs-lookup"><span data-stu-id="1bdc9-108">Name</span></span>    | <span data-ttu-id="1bdc9-109">Wartość</span><span class="sxs-lookup"><span data-stu-id="1bdc9-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="1bdc9-110">Zakres</span><span class="sxs-lookup"><span data-stu-id="1bdc9-110">Scope</span></span>   | <span data-ttu-id="1bdc9-111">Mały</span><span class="sxs-lookup"><span data-stu-id="1bdc9-111">Minor</span></span>       |
| <span data-ttu-id="1bdc9-112">Wersja</span><span class="sxs-lookup"><span data-stu-id="1bdc9-112">Version</span></span> | <span data-ttu-id="1bdc9-113">4.5</span><span class="sxs-lookup"><span data-stu-id="1bdc9-113">4.5</span></span>         |
| <span data-ttu-id="1bdc9-114">Typ</span><span class="sxs-lookup"><span data-stu-id="1bdc9-114">Type</span></span>    | <span data-ttu-id="1bdc9-115">Przekierowanie</span><span class="sxs-lookup"><span data-stu-id="1bdc9-115">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="1bdc9-116">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="1bdc9-116">Affected APIs</span></span>

- <xref:System.Activities.Presentation.DragDropHelper.DoDragMove(System.Activities.Presentation.WorkflowViewElement,System.Windows.Point)?displayProperty=nameWithType>
- <xref:System.Activities.Presentation.DragDropHelper.GetCompositeView(System.Windows.DragEventArgs)?displayProperty=nameWithType>
- <xref:System.Activities.Presentation.DragDropHelper.GetDraggedModelItem(System.Windows.DragEventArgs)?displayProperty=nameWithType>
- <xref:System.Activities.Presentation.DragDropHelper.GetDroppedObject(System.Windows.DependencyObject,System.Windows.DragEventArgs,System.Activities.Presentation.EditingContext)?displayProperty=nameWithType>
