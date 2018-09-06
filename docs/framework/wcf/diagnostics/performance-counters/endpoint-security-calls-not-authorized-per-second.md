---
title: 'Punkt końcowy: Wywołania zabezpieczeń bez autoryzacji na sekundę'
ms.date: 03/30/2017
ms.assetid: c8a1547b-986b-45c1-b302-dea0cd4b516d
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 4cefdd7480c7d0e9475b1883e603d9db1f287d4a
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2018
ms.locfileid: "44035632"
---
# <a name="endpoint-security-calls-not-authorized-per-second"></a><span data-ttu-id="068e4-102">Punkt końcowy: Wywołania zabezpieczeń bez autoryzacji na sekundę</span><span class="sxs-lookup"><span data-stu-id="068e4-102">Endpoint: Security Calls Not Authorized Per Second</span></span>
<span data-ttu-id="068e4-103">Nazwa licznika: Wywołania zabezpieczeń bez autoryzacji na sekundę.</span><span class="sxs-lookup"><span data-stu-id="068e4-103">Counter Name: Security Calls Not Authorized Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="068e4-104">Opis</span><span class="sxs-lookup"><span data-stu-id="068e4-104">Description</span></span>  
 <span data-ttu-id="068e4-105">Liczba komunikatów przychodzących na sekundę, które pochodzą z prawidłowego użytkownika i odpowiednio chroniona, ale użytkownik nie ma uprawnień do wykonywania określonych zadań.</span><span class="sxs-lookup"><span data-stu-id="068e4-105">Number of incoming messages in a second that are from a valid user and protected properly, but the user is not authorized to do specific tasks.</span></span>  
  
 <span data-ttu-id="068e4-106">Ten licznik jest zwiększany po <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> metoda zwraca `false`.</span><span class="sxs-lookup"><span data-stu-id="068e4-106">This counter is incremented when the <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> method returns `false`.</span></span>  
  
 <span data-ttu-id="068e4-107">Ten licznik jest typ licznika wydajności [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), którego wartość jest obliczana przy użyciu następującej formuły.</span><span class="sxs-lookup"><span data-stu-id="068e4-107">This counter is of performance counter type [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="068e4-108">(N: 1 - N 0) / ((D 1 - D 0) / F)</span><span class="sxs-lookup"><span data-stu-id="068e4-108">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
