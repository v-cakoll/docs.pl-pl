---
ms.openlocfilehash: 6bb8c87af66e744514fb43e628c6423487342ac2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "72887818"
---
### <a name="calls-to-systemwindowsinputpencontextdisable-on-touch-enabled-systems-may-throw-an-argumentexception"></a><span data-ttu-id="8ae02-101">Wywołania do System.Windows.Input.PenContext.Wyłącz na dotykowych systemów może rzucać ArgumentException</span><span class="sxs-lookup"><span data-stu-id="8ae02-101">Calls to System.Windows.Input.PenContext.Disable on touch-enabled systems may throw an ArgumentException</span></span>

|   |   |
|---|---|
|<span data-ttu-id="8ae02-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="8ae02-102">Details</span></span>|<span data-ttu-id="8ae02-103">W pewnych okolicznościach wywołania wewnętrznej **system.Windows.Intput.PenContext.Disable** metody w systemach dotykowych może rzucać nieobsługiwał <code>T:System.ArgumentException</code> z powodu ponownego internalrancy.</span><span class="sxs-lookup"><span data-stu-id="8ae02-103">Under some circumstances, calls to the internal **System.Windows.Intput.PenContext.Disable** method on touch-enabled systems may throw an unhandled <code>T:System.ArgumentException</code> because of reentrancy.</span></span>|
|<span data-ttu-id="8ae02-104">Sugestia</span><span class="sxs-lookup"><span data-stu-id="8ae02-104">Suggestion</span></span>|<span data-ttu-id="8ae02-105">Ten problem został rozwiązany w .NET Framework 4.7.</span><span class="sxs-lookup"><span data-stu-id="8ae02-105">This issue has been addressed in the .NET Framework 4.7.</span></span> <span data-ttu-id="8ae02-106">Aby zapobiec wyjątek, uaktualnić do wersji programu .NET Framework, począwszy od .NET Framework 4.7.</span><span class="sxs-lookup"><span data-stu-id="8ae02-106">To prevent the exception, upgrade to a version of the .NET Framework starting with the .NET Framework 4.7.</span></span>|
|<span data-ttu-id="8ae02-107">Zakres</span><span class="sxs-lookup"><span data-stu-id="8ae02-107">Scope</span></span>|<span data-ttu-id="8ae02-108">Brzeg</span><span class="sxs-lookup"><span data-stu-id="8ae02-108">Edge</span></span>|
|<span data-ttu-id="8ae02-109">Wersja</span><span class="sxs-lookup"><span data-stu-id="8ae02-109">Version</span></span>|<span data-ttu-id="8ae02-110">4.6.1</span><span class="sxs-lookup"><span data-stu-id="8ae02-110">4.6.1</span></span>|
|<span data-ttu-id="8ae02-111">Typ</span><span class="sxs-lookup"><span data-stu-id="8ae02-111">Type</span></span>|<span data-ttu-id="8ae02-112">Przekierowanie</span><span class="sxs-lookup"><span data-stu-id="8ae02-112">Retargeting</span></span>|
