---
ms.openlocfilehash: a44458484ea09c566defeabc9b604bd55d994e93
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617545"
---
### <a name="calls-to-systemwindowsinputpencontextdisable-on-touch-enabled-systems-may-throw-an-argumentexception"></a><span data-ttu-id="7382b-101">Wywołania metody System. Windows. Input. PenContext. Disable w systemach z obsługą dotykową mogą zgłosić ArgumentException</span><span class="sxs-lookup"><span data-stu-id="7382b-101">Calls to System.Windows.Input.PenContext.Disable on touch-enabled systems may throw an ArgumentException</span></span>

#### <a name="details"></a><span data-ttu-id="7382b-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="7382b-102">Details</span></span>

<span data-ttu-id="7382b-103">W pewnych okolicznościach wywołania wewnętrznej metody **System. Windows. Intput. PenContext. Disable** w systemach z obsługą dotykową mogą zgłosić nieobsłużony `T:System.ArgumentException` skutek z powodu współużytkowania wątkowości.</span><span class="sxs-lookup"><span data-stu-id="7382b-103">Under some circumstances, calls to the internal **System.Windows.Intput.PenContext.Disable** method on touch-enabled systems may throw an unhandled `T:System.ArgumentException` because of reentrancy.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="7382b-104">Sugestia</span><span class="sxs-lookup"><span data-stu-id="7382b-104">Suggestion</span></span>

<span data-ttu-id="7382b-105">Ten problem został rozwiązany w .NET Framework 4,7.</span><span class="sxs-lookup"><span data-stu-id="7382b-105">This issue has been addressed in the .NET Framework 4.7.</span></span> <span data-ttu-id="7382b-106">Aby zapobiec wyjątku, należy przeprowadzić uaktualnienie do wersji .NET Framework począwszy od .NET Framework 4,7.</span><span class="sxs-lookup"><span data-stu-id="7382b-106">To prevent the exception, upgrade to a version of the .NET Framework starting with the .NET Framework 4.7.</span></span>

| <span data-ttu-id="7382b-107">Nazwa</span><span class="sxs-lookup"><span data-stu-id="7382b-107">Name</span></span>    | <span data-ttu-id="7382b-108">Wartość</span><span class="sxs-lookup"><span data-stu-id="7382b-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="7382b-109">Zakres</span><span class="sxs-lookup"><span data-stu-id="7382b-109">Scope</span></span>   | <span data-ttu-id="7382b-110">Brzeg</span><span class="sxs-lookup"><span data-stu-id="7382b-110">Edge</span></span>        |
| <span data-ttu-id="7382b-111">Wersja</span><span class="sxs-lookup"><span data-stu-id="7382b-111">Version</span></span> | <span data-ttu-id="7382b-112">4.6.1</span><span class="sxs-lookup"><span data-stu-id="7382b-112">4.6.1</span></span>       |
| <span data-ttu-id="7382b-113">Typ</span><span class="sxs-lookup"><span data-stu-id="7382b-113">Type</span></span>    | <span data-ttu-id="7382b-114">Przekierowanie</span><span class="sxs-lookup"><span data-stu-id="7382b-114">Retargeting</span></span> |
