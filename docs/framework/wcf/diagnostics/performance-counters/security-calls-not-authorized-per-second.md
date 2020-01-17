---
title: Nieautoryzowane wywołania zabezpieczeń na sekundę
ms.date: 03/30/2017
ms.assetid: 0f189767-8c05-478a-8f0b-9228e5d351e5
ms.openlocfilehash: 2986ba241ef9b6c110a4742f77320469cdf5f07a
ms.sourcegitcommit: 5d769956a04b6d68484dd717077fabc191c21da5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2020
ms.locfileid: "76163933"
---
# <a name="security-calls-not-authorized-per-second"></a><span data-ttu-id="92da2-102">Nieautoryzowane wywołania zabezpieczeń na sekundę</span><span class="sxs-lookup"><span data-stu-id="92da2-102">Security Calls Not Authorized Per Second</span></span>
<span data-ttu-id="92da2-103">Nazwa licznika: wywołania zabezpieczeń nie są autoryzowane na sekundę.</span><span class="sxs-lookup"><span data-stu-id="92da2-103">Counter Name: Security Calls Not Authorized Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="92da2-104">Opis</span><span class="sxs-lookup"><span data-stu-id="92da2-104">Description</span></span>  
 <span data-ttu-id="92da2-105">Liczba wywołań, których autoryzacja zakończyła się niepowodzeniem w ramach tej operacji w drugim.</span><span class="sxs-lookup"><span data-stu-id="92da2-105">Number of calls that failed authorization in this operation in a second.</span></span>  
  
 <span data-ttu-id="92da2-106">Licznik jest zwiększany, gdy metoda <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> zwraca `false`.</span><span class="sxs-lookup"><span data-stu-id="92da2-106">This counter is incremented when the <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> method returns `false`.</span></span> <span data-ttu-id="92da2-107">Wskazuje on, że komunikat przychodzący jest prawidłowym użytkownikiem i chroniony prawidłowo, ale użytkownik nie ma uprawnień do wykonywania określonych zadań.</span><span class="sxs-lookup"><span data-stu-id="92da2-107">It indicates that the incoming message is from a valid user and protected properly, but the user is not authorized to do specific tasks.</span></span>  
  
 <span data-ttu-id="92da2-108">Ten licznik jest typem licznika wydajności [PERF_COUNTER_COUNTER](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), którego wartość jest obliczana przy użyciu następującej formuły.</span><span class="sxs-lookup"><span data-stu-id="92da2-108">This counter is of performance counter type [PERF_COUNTER_COUNTER](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="92da2-109">(N 1-N 0)/((D 1-D 0)/F)</span><span class="sxs-lookup"><span data-stu-id="92da2-109">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
