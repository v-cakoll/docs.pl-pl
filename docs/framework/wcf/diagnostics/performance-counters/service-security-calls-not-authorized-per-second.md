---
title: 'Usługa: Nieautoryzowane wywołania zabezpieczeń na sekundę'
ms.date: 03/30/2017
ms.assetid: 1eeade5a-ea62-4757-b1f9-1b1b1746abd1
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: f2c921991f059d7dfe5661dfe688ec9675d0d5fe
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/08/2018
ms.locfileid: "44210643"
---
# <a name="service-security-calls-not-authorized-per-second"></a><span data-ttu-id="2a2fa-102">Usługa: Nieautoryzowane wywołania zabezpieczeń na sekundę</span><span class="sxs-lookup"><span data-stu-id="2a2fa-102">Service: Security Calls Not Authorized Per Second</span></span>
<span data-ttu-id="2a2fa-103">Nazwa licznika: zabezpieczeń wywołania nie autoryzacji na sekundę</span><span class="sxs-lookup"><span data-stu-id="2a2fa-103">Counter name: Security Calls Not Authorized Per Second</span></span>  
  
## <a name="description"></a><span data-ttu-id="2a2fa-104">Opis</span><span class="sxs-lookup"><span data-stu-id="2a2fa-104">Description</span></span>  
 <span data-ttu-id="2a2fa-105">Liczba komunikatów przychodzących w jednej sekundy, które pochodzą z prawidłowego użytkownika i odpowiednio chroniona, ale użytkownik nie ma uprawnień do wykonywania określonych zadań.</span><span class="sxs-lookup"><span data-stu-id="2a2fa-105">Number of incoming messages in one second, which are from a valid user and protected properly, but the user is not authorized to do specific tasks.</span></span>  
  
 <span data-ttu-id="2a2fa-106">Ten licznik jest zwiększany po <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> metoda zwraca `false`.</span><span class="sxs-lookup"><span data-stu-id="2a2fa-106">This counter is incremented when the <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> method returns `false`.</span></span>  
  
 <span data-ttu-id="2a2fa-107">Ten licznik jest typ licznika wydajności [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkId=94649), którego wartość jest obliczana przy użyciu następującej formuły.</span><span class="sxs-lookup"><span data-stu-id="2a2fa-107">This counter is of performance counter type [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkId=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="2a2fa-108">(N: 1 - N 0) / ((D 1 - D 0) / F)</span><span class="sxs-lookup"><span data-stu-id="2a2fa-108">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
