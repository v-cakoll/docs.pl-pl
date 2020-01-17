---
title: 'Punkt końcowy: wywołania zabezpieczeń bez autoryzacji na sekundę'
ms.date: 03/30/2017
ms.assetid: c8a1547b-986b-45c1-b302-dea0cd4b516d
ms.openlocfilehash: 8c287ef4c156bb0a76a4b1d08b0d70b40bd76229
ms.sourcegitcommit: 5d769956a04b6d68484dd717077fabc191c21da5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2020
ms.locfileid: "76163179"
---
# <a name="endpoint-security-calls-not-authorized-per-second"></a><span data-ttu-id="0f844-102">Punkt końcowy: wywołania zabezpieczeń bez autoryzacji na sekundę</span><span class="sxs-lookup"><span data-stu-id="0f844-102">Endpoint: Security Calls Not Authorized Per Second</span></span>
<span data-ttu-id="0f844-103">Nazwa licznika: wywołania zabezpieczeń nie są autoryzowane na sekundę.</span><span class="sxs-lookup"><span data-stu-id="0f844-103">Counter Name: Security Calls Not Authorized Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="0f844-104">Opis</span><span class="sxs-lookup"><span data-stu-id="0f844-104">Description</span></span>  
 <span data-ttu-id="0f844-105">Liczba komunikatów przychodzących w drugim, które są prawidłowymi użytkownikami i są chronione prawidłowo, ale użytkownik nie ma uprawnień do wykonywania określonych zadań.</span><span class="sxs-lookup"><span data-stu-id="0f844-105">Number of incoming messages in a second that are from a valid user and protected properly, but the user is not authorized to do specific tasks.</span></span>  
  
 <span data-ttu-id="0f844-106">Licznik jest zwiększany, gdy metoda <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> zwraca `false`.</span><span class="sxs-lookup"><span data-stu-id="0f844-106">This counter is incremented when the <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> method returns `false`.</span></span>  
  
 <span data-ttu-id="0f844-107">Ten licznik jest typem licznika wydajności [PERF_COUNTER_COUNTER](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), którego wartość jest obliczana przy użyciu następującej formuły.</span><span class="sxs-lookup"><span data-stu-id="0f844-107">This counter is of performance counter type [PERF_COUNTER_COUNTER](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="0f844-108">(N 1-N 0)/((D 1-D 0)/F)</span><span class="sxs-lookup"><span data-stu-id="0f844-108">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
