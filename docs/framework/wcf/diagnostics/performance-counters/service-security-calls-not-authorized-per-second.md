---
title: 'Usługa: Nieautoryzowane wywołania zabezpieczeń na sekundę'
ms.date: 03/30/2017
ms.assetid: 1eeade5a-ea62-4757-b1f9-1b1b1746abd1
ms.openlocfilehash: 964eff97a58ab7d5a68dbc1891473ae8d04a50ad
ms.sourcegitcommit: 5d769956a04b6d68484dd717077fabc191c21da5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2020
ms.locfileid: "76163881"
---
# <a name="service-security-calls-not-authorized-per-second"></a><span data-ttu-id="b060c-102">Usługa: Nieautoryzowane wywołania zabezpieczeń na sekundę</span><span class="sxs-lookup"><span data-stu-id="b060c-102">Service: Security Calls Not Authorized Per Second</span></span>
<span data-ttu-id="b060c-103">Nazwa licznika: wywołania zabezpieczeń bez autoryzacji na sekundę</span><span class="sxs-lookup"><span data-stu-id="b060c-103">Counter name: Security Calls Not Authorized Per Second</span></span>  
  
## <a name="description"></a><span data-ttu-id="b060c-104">Opis</span><span class="sxs-lookup"><span data-stu-id="b060c-104">Description</span></span>  
 <span data-ttu-id="b060c-105">Liczba wiadomości przychodzących w jednej sekund, które są od prawidłowego użytkownika i są chronione prawidłowo, ale użytkownik nie ma uprawnień do wykonywania określonych zadań.</span><span class="sxs-lookup"><span data-stu-id="b060c-105">Number of incoming messages in one second, which are from a valid user and protected properly, but the user is not authorized to do specific tasks.</span></span>  
  
 <span data-ttu-id="b060c-106">Licznik jest zwiększany, gdy metoda <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> zwraca `false`.</span><span class="sxs-lookup"><span data-stu-id="b060c-106">This counter is incremented when the <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> method returns `false`.</span></span>  
  
 <span data-ttu-id="b060c-107">Ten licznik jest typem licznika wydajności [PERF_COUNTER_COUNTER](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), którego wartość jest obliczana przy użyciu następującej formuły.</span><span class="sxs-lookup"><span data-stu-id="b060c-107">This counter is of performance counter type [PERF_COUNTER_COUNTER](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="b060c-108">(N 1-N 0)/((D 1-D 0)/F)</span><span class="sxs-lookup"><span data-stu-id="b060c-108">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
