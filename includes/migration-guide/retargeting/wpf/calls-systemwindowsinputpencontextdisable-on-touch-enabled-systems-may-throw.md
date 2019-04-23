---
ms.openlocfilehash: 3cd5052dffcb059c240a310e0b89384f28409264
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "59982154"
---
### <a name="calls-to-systemwindowsinputpencontextdisable-on-touch-enabled-systems-may-throw-an-argumentexception"></a><span data-ttu-id="15b6e-101">Wywołania System.Windows.Input.PenContext.Disable w systemach z obsługą dotykową może zgłaszać ArgumentException</span><span class="sxs-lookup"><span data-stu-id="15b6e-101">Calls to System.Windows.Input.PenContext.Disable on touch-enabled systems may throw an ArgumentException</span></span>

|   |   |
|---|---|
|<span data-ttu-id="15b6e-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="15b6e-102">Details</span></span>|<span data-ttu-id="15b6e-103">W niektórych okolicznościach wywołania wewnętrznego <strong>System.Windows.Intput.PenContext.Disable</strong> metody w systemach z obsługą dotykową może zgłaszać nieobsługiwany <code>T:System.ArgumentException</code> ze względu na współużytkowania wątkowości.</span><span class="sxs-lookup"><span data-stu-id="15b6e-103">Under some circumstances, calls to the internal <strong>System.Windows.Intput.PenContext.Disable</strong> method on touch-enabled systems may throw an unhandled <code>T:System.ArgumentException</code> because of reentrancy.</span></span>|
|<span data-ttu-id="15b6e-104">Sugestia</span><span class="sxs-lookup"><span data-stu-id="15b6e-104">Suggestion</span></span>|<span data-ttu-id="15b6e-105">Ten problem został rozwiązany w programie .NET Framework 4.7.</span><span class="sxs-lookup"><span data-stu-id="15b6e-105">This issue has been addressed in the .NET Framework 4.7.</span></span> <span data-ttu-id="15b6e-106">Aby zapobiec wyjątek, uaktualnienie do wersji programu .NET Framework, począwszy od programu .NET Framework 4.7.</span><span class="sxs-lookup"><span data-stu-id="15b6e-106">To prevent the exception, upgrade to a version of the .NET Framework starting with the .NET Framework 4.7.</span></span>|
|<span data-ttu-id="15b6e-107">Zakres</span><span class="sxs-lookup"><span data-stu-id="15b6e-107">Scope</span></span>|<span data-ttu-id="15b6e-108">Krawędź</span><span class="sxs-lookup"><span data-stu-id="15b6e-108">Edge</span></span>|
|<span data-ttu-id="15b6e-109">Wersja</span><span class="sxs-lookup"><span data-stu-id="15b6e-109">Version</span></span>|<span data-ttu-id="15b6e-110">4.6.1</span><span class="sxs-lookup"><span data-stu-id="15b6e-110">4.6.1</span></span>|
|<span data-ttu-id="15b6e-111">Typ</span><span class="sxs-lookup"><span data-stu-id="15b6e-111">Type</span></span>|<span data-ttu-id="15b6e-112">Przekierowanie</span><span class="sxs-lookup"><span data-stu-id="15b6e-112">Retargeting</span></span>|
