---
ms.openlocfilehash: 0778285ef1b5702bd79743038a1bd21ba04612d6
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/11/2019
ms.locfileid: "67804322"
---
### <a name="calls-to-systemwindowsinputpencontextdisable-on-touch-enabled-systems-may-throw-an-argumentexception"></a><span data-ttu-id="02b2f-101">Wywołania System.Windows.Input.PenContext.Disable w systemach z obsługą dotykową może zgłaszać ArgumentException</span><span class="sxs-lookup"><span data-stu-id="02b2f-101">Calls to System.Windows.Input.PenContext.Disable on touch-enabled systems may throw an ArgumentException</span></span>

|   |   |
|---|---|
|<span data-ttu-id="02b2f-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="02b2f-102">Details</span></span>|<span data-ttu-id="02b2f-103">W niektórych okolicznościach wywołania wewnętrznego <strong>System.Windows.Intput.PenContext.Disable</strong> metody w systemach z obsługą dotykową może zgłaszać nieobsługiwany <code>T:System.ArgumentException</code> ze względu na współużytkowania wątkowości.</span><span class="sxs-lookup"><span data-stu-id="02b2f-103">Under some circumstances, calls to the internal <strong>System.Windows.Intput.PenContext.Disable</strong> method on touch-enabled systems may throw an unhandled <code>T:System.ArgumentException</code> because of reentrancy.</span></span>|
|<span data-ttu-id="02b2f-104">Sugestia</span><span class="sxs-lookup"><span data-stu-id="02b2f-104">Suggestion</span></span>|<span data-ttu-id="02b2f-105">Ten problem został rozwiązany w programie .NET Framework 4.7.</span><span class="sxs-lookup"><span data-stu-id="02b2f-105">This issue has been addressed in the .NET Framework 4.7.</span></span> <span data-ttu-id="02b2f-106">Aby zapobiec wyjątek, uaktualnienie do wersji programu .NET Framework, począwszy od programu .NET Framework 4.7.</span><span class="sxs-lookup"><span data-stu-id="02b2f-106">To prevent the exception, upgrade to a version of the .NET Framework starting with the .NET Framework 4.7.</span></span>|
|<span data-ttu-id="02b2f-107">Scope</span><span class="sxs-lookup"><span data-stu-id="02b2f-107">Scope</span></span>|<span data-ttu-id="02b2f-108">Krawędź</span><span class="sxs-lookup"><span data-stu-id="02b2f-108">Edge</span></span>|
|<span data-ttu-id="02b2f-109">Wersja</span><span class="sxs-lookup"><span data-stu-id="02b2f-109">Version</span></span>|<span data-ttu-id="02b2f-110">4.6.1</span><span class="sxs-lookup"><span data-stu-id="02b2f-110">4.6.1</span></span>|
|<span data-ttu-id="02b2f-111">Typ</span><span class="sxs-lookup"><span data-stu-id="02b2f-111">Type</span></span>|<span data-ttu-id="02b2f-112">Przekierowanie</span><span class="sxs-lookup"><span data-stu-id="02b2f-112">Retargeting</span></span>|

