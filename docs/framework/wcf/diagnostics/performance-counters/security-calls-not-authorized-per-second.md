---
title: Nieautoryzowane wywołania zabezpieczeń na sekundę
ms.date: 03/30/2017
ms.assetid: 0f189767-8c05-478a-8f0b-9228e5d351e5
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 4d4970c6f6552163114b33a34ae87c6ed56b5e13
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/03/2018
ms.locfileid: "43484849"
---
# <a name="security-calls-not-authorized-per-second"></a><span data-ttu-id="6faf4-102">Nieautoryzowane wywołania zabezpieczeń na sekundę</span><span class="sxs-lookup"><span data-stu-id="6faf4-102">Security Calls Not Authorized Per Second</span></span>
<span data-ttu-id="6faf4-103">Nazwa licznika: Wywołania zabezpieczeń bez autoryzacji na sekundę.</span><span class="sxs-lookup"><span data-stu-id="6faf4-103">Counter Name: Security Calls Not Authorized Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="6faf4-104">Opis</span><span class="sxs-lookup"><span data-stu-id="6faf4-104">Description</span></span>  
 <span data-ttu-id="6faf4-105">Liczba wywołań, których nie powiodła się autoryzacja w tę operację za chwilę.</span><span class="sxs-lookup"><span data-stu-id="6faf4-105">Number of calls that failed authorization in this operation in a second.</span></span>  
  
 <span data-ttu-id="6faf4-106">Ten licznik jest zwiększany po <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> metoda zwraca `false`.</span><span class="sxs-lookup"><span data-stu-id="6faf4-106">This counter is incremented when the <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> method returns `false`.</span></span> <span data-ttu-id="6faf4-107">Wskazuje on, przychodząca wiadomość pochodzi z prawidłowego użytkownika i odpowiednio chroniona, ale użytkownik nie ma uprawnień do wykonywania określonych zadań.</span><span class="sxs-lookup"><span data-stu-id="6faf4-107">It indicates that the incoming message is from a valid user and protected properly, but the user is not authorized to do specific tasks.</span></span>  
  
 <span data-ttu-id="6faf4-108">Ten licznik jest typ licznika wydajności [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), którego wartość jest obliczana przy użyciu następującej formuły.</span><span class="sxs-lookup"><span data-stu-id="6faf4-108">This counter is of performance counter type [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="6faf4-109">(N: 1 - N 0) / ((D 1 - D 0) / F)</span><span class="sxs-lookup"><span data-stu-id="6faf4-109">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
