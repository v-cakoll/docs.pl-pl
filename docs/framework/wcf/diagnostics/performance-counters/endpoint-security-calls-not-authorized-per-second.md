---
title: 'Punkt końcowy: Wywołania zabezpieczeń bez autoryzacji na sekundę'
ms.date: 03/30/2017
ms.assetid: c8a1547b-986b-45c1-b302-dea0cd4b516d
author: BrucePerlerMS
ms.openlocfilehash: 4abea795eb196d339beec17fa7a171927aa85324
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/25/2018
ms.locfileid: "47078373"
---
# <a name="endpoint-security-calls-not-authorized-per-second"></a><span data-ttu-id="833b1-102">Punkt końcowy: Wywołania zabezpieczeń bez autoryzacji na sekundę</span><span class="sxs-lookup"><span data-stu-id="833b1-102">Endpoint: Security Calls Not Authorized Per Second</span></span>
<span data-ttu-id="833b1-103">Nazwa licznika: Wywołania zabezpieczeń bez autoryzacji na sekundę.</span><span class="sxs-lookup"><span data-stu-id="833b1-103">Counter Name: Security Calls Not Authorized Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="833b1-104">Opis</span><span class="sxs-lookup"><span data-stu-id="833b1-104">Description</span></span>  
 <span data-ttu-id="833b1-105">Liczba komunikatów przychodzących na sekundę, które pochodzą z prawidłowego użytkownika i odpowiednio chroniona, ale użytkownik nie ma uprawnień do wykonywania określonych zadań.</span><span class="sxs-lookup"><span data-stu-id="833b1-105">Number of incoming messages in a second that are from a valid user and protected properly, but the user is not authorized to do specific tasks.</span></span>  
  
 <span data-ttu-id="833b1-106">Ten licznik jest zwiększany po <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> metoda zwraca `false`.</span><span class="sxs-lookup"><span data-stu-id="833b1-106">This counter is incremented when the <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> method returns `false`.</span></span>  
  
 <span data-ttu-id="833b1-107">Ten licznik jest typ licznika wydajności [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), którego wartość jest obliczana przy użyciu następującej formuły.</span><span class="sxs-lookup"><span data-stu-id="833b1-107">This counter is of performance counter type [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="833b1-108">(N: 1 - N 0) / ((D 1 - D 0) / F)</span><span class="sxs-lookup"><span data-stu-id="833b1-108">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
