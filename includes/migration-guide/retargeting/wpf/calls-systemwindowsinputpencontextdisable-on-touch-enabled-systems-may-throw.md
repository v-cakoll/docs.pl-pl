---
ms.openlocfilehash: 6bb8c87af66e744514fb43e628c6423487342ac2
ms.sourcegitcommit: 337bdc5a463875daf2cc6883e5a2da97d56f5000
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2019
ms.locfileid: "72887818"
---
### <a name="calls-to-systemwindowsinputpencontextdisable-on-touch-enabled-systems-may-throw-an-argumentexception"></a><span data-ttu-id="bd0fc-101">Wywołania metody System. Windows. Input. PenContext. Disable w systemach z obsługą dotykową mogą zgłosić ArgumentException</span><span class="sxs-lookup"><span data-stu-id="bd0fc-101">Calls to System.Windows.Input.PenContext.Disable on touch-enabled systems may throw an ArgumentException</span></span>

|   |   |
|---|---|
|<span data-ttu-id="bd0fc-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="bd0fc-102">Details</span></span>|<span data-ttu-id="bd0fc-103">W pewnych okolicznościach wywołania wewnętrznej metody **System. Windows. Intput. PenContext. Disable** w systemach z obsługą dotykową mogą zgłosić nieobsłużony <code>T:System.ArgumentException</code> z powodu współużytkowania wątkowości.</span><span class="sxs-lookup"><span data-stu-id="bd0fc-103">Under some circumstances, calls to the internal **System.Windows.Intput.PenContext.Disable** method on touch-enabled systems may throw an unhandled <code>T:System.ArgumentException</code> because of reentrancy.</span></span>|
|<span data-ttu-id="bd0fc-104">Sugestia</span><span class="sxs-lookup"><span data-stu-id="bd0fc-104">Suggestion</span></span>|<span data-ttu-id="bd0fc-105">Ten problem został rozwiązany w .NET Framework 4,7.</span><span class="sxs-lookup"><span data-stu-id="bd0fc-105">This issue has been addressed in the .NET Framework 4.7.</span></span> <span data-ttu-id="bd0fc-106">Aby zapobiec wyjątku, należy przeprowadzić uaktualnienie do wersji .NET Framework począwszy od .NET Framework 4,7.</span><span class="sxs-lookup"><span data-stu-id="bd0fc-106">To prevent the exception, upgrade to a version of the .NET Framework starting with the .NET Framework 4.7.</span></span>|
|<span data-ttu-id="bd0fc-107">Zakres</span><span class="sxs-lookup"><span data-stu-id="bd0fc-107">Scope</span></span>|<span data-ttu-id="bd0fc-108">Krawędź</span><span class="sxs-lookup"><span data-stu-id="bd0fc-108">Edge</span></span>|
|<span data-ttu-id="bd0fc-109">Wersja</span><span class="sxs-lookup"><span data-stu-id="bd0fc-109">Version</span></span>|<span data-ttu-id="bd0fc-110">4.6.1</span><span class="sxs-lookup"><span data-stu-id="bd0fc-110">4.6.1</span></span>|
|<span data-ttu-id="bd0fc-111">Typ</span><span class="sxs-lookup"><span data-stu-id="bd0fc-111">Type</span></span>|<span data-ttu-id="bd0fc-112">Przekierowanie</span><span class="sxs-lookup"><span data-stu-id="bd0fc-112">Retargeting</span></span>|
