---
title: "Nieautoryzowane wywołania zabezpieczeń na sekundę"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0f189767-8c05-478a-8f0b-9228e5d351e5
caps.latest.revision: "9"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: f52236bb69b1e393179e0a4a8af2e141c173d47d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="security-calls-not-authorized-per-second"></a><span data-ttu-id="8dcda-102">Nieautoryzowane wywołania zabezpieczeń na sekundę</span><span class="sxs-lookup"><span data-stu-id="8dcda-102">Security Calls Not Authorized Per Second</span></span>
<span data-ttu-id="8dcda-103">Nazwa licznika: Wywołania zabezpieczeń bez autoryzacji na sekundę.</span><span class="sxs-lookup"><span data-stu-id="8dcda-103">Counter Name: Security Calls Not Authorized Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="8dcda-104">Opis</span><span class="sxs-lookup"><span data-stu-id="8dcda-104">Description</span></span>  
 <span data-ttu-id="8dcda-105">Liczba wywołań z nieudaną autoryzacją w tej operacji na sekundę.</span><span class="sxs-lookup"><span data-stu-id="8dcda-105">Number of calls that failed authorization in this operation in a second.</span></span>  
  
 <span data-ttu-id="8dcda-106">Ten licznik jest zwiększany po <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> metoda zwraca `false`.</span><span class="sxs-lookup"><span data-stu-id="8dcda-106">This counter is incremented when the <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> method returns `false`.</span></span> <span data-ttu-id="8dcda-107">Wskazuje on, że przychodzący komunikat pochodzi z prawidłowego użytkownika i odpowiednio chroniona, ale użytkownik nie ma uprawnień do wykonywania określonych zadań.</span><span class="sxs-lookup"><span data-stu-id="8dcda-107">It indicates that the incoming message is from a valid user and protected properly, but the user is not authorized to do specific tasks.</span></span>  
  
 <span data-ttu-id="8dcda-108">Ten licznik jest typu licznika wydajności [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), którego wartość jest obliczana przy użyciu następującej formuły.</span><span class="sxs-lookup"><span data-stu-id="8dcda-108">This counter is of performance counter type [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="8dcda-109">(N 1 - N 0) / ((D 1 - D 0) / F)</span><span class="sxs-lookup"><span data-stu-id="8dcda-109">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
