---
ms.openlocfilehash: 1d01de4b978309e05a6036953f2a6909628a2480
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/28/2019
ms.locfileid: "74643999"
---
### <a name="switchsystemwindowsformsallowupdatechildcontrolindexfortabcontrols-compatibility-switch-not-supported"></a><span data-ttu-id="49e04-101">Przełącznik. System. Windows. Forms. AllowUpdateChildControlIndexForTabControls nie jest obsługiwany.</span><span class="sxs-lookup"><span data-stu-id="49e04-101">Switch.System.Windows.Forms.AllowUpdateChildControlIndexForTabControls compatibility switch not supported</span></span>

<span data-ttu-id="49e04-102">Przełącznik zgodności `Switch.System.Windows.Forms.AllowUpdateChildControlIndexForTabControls` jest obsługiwany w Windows Forms w .NET Framework 4,6 i nowszych wersjach, ale nie jest obsługiwany w Windows Forms począwszy od platformy .NET Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="49e04-102">The `Switch.System.Windows.Forms.AllowUpdateChildControlIndexForTabControls` compatibility switch is supported in Windows Forms on .NET Framework 4.6 and later versions but is not supported in Windows Forms starting with .NET Core 3.0.</span></span>

#### <a name="change-description"></a><span data-ttu-id="49e04-103">Zmień opis</span><span class="sxs-lookup"><span data-stu-id="49e04-103">Change description</span></span>

<span data-ttu-id="49e04-104">W .NET Framework 4,6 i nowszych wersjach, wybranie karty zmienia kolejność kolekcji kontrolek.</span><span class="sxs-lookup"><span data-stu-id="49e04-104">In .NET Framework 4.6 and later versions, selecting a tab reorders its control collection.</span></span> <span data-ttu-id="49e04-105">Przełącznik zgodności `Switch.System.Windows.Forms.AllowUpdateChildControlIndexForTabControls` pozwala aplikacji pominąć tę zmianę kolejności, jeśli to zachowanie jest niepożądane.</span><span class="sxs-lookup"><span data-stu-id="49e04-105">The `Switch.System.Windows.Forms.AllowUpdateChildControlIndexForTabControls` compatibility switch allows an application to skip this reordering when this behavior is undesirable.</span></span>

<span data-ttu-id="49e04-106">W programie .NET Core przełącznik `Switch.System.Windows.Forms.AllowUpdateChildControlIndexForTabControls` nie jest obsługiwany.</span><span class="sxs-lookup"><span data-stu-id="49e04-106">In .NET Core, the `Switch.System.Windows.Forms.AllowUpdateChildControlIndexForTabControls` switch is not supported.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="49e04-107">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="49e04-107">Version introduced</span></span>

<span data-ttu-id="49e04-108">3,0 wersja zapoznawcza 9</span><span class="sxs-lookup"><span data-stu-id="49e04-108">3.0 Preview 9</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="49e04-109">Zalecane działanie</span><span class="sxs-lookup"><span data-stu-id="49e04-109">Recommended action</span></span>

<span data-ttu-id="49e04-110">Usuń przełącznik.</span><span class="sxs-lookup"><span data-stu-id="49e04-110">Remove the switch.</span></span> <span data-ttu-id="49e04-111">Przełącznik nie jest obsługiwany i żadna alternatywna funkcja nie jest dostępna.</span><span class="sxs-lookup"><span data-stu-id="49e04-111">The switch is not supported, and no alternative functionality is available.</span></span>

#### <a name="category"></a><span data-ttu-id="49e04-112">Kategoria</span><span class="sxs-lookup"><span data-stu-id="49e04-112">Category</span></span>

<span data-ttu-id="49e04-113">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="49e04-113">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="49e04-114">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="49e04-114">Affected APIs</span></span>

- <span data-ttu-id="49e04-115">Brak</span><span class="sxs-lookup"><span data-stu-id="49e04-115">None</span></span>

<!-- 

### Affected APIs

- Not detectable via API analysis

-->
