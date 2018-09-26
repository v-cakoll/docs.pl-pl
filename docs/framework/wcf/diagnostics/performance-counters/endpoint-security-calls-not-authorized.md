---
title: 'Punkt końcowy: Wywołania zabezpieczeń bez autoryzacji'
ms.date: 03/30/2017
ms.assetid: d25095ff-9ff0-4c69-a674-4e6a9fe3f4dc
author: BrucePerlerMS
ms.openlocfilehash: 2d2f114d45675ece23f818d4d56bcc40684f9dbf
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/26/2018
ms.locfileid: "47194084"
---
# <a name="endpoint-security-calls-not-authorized"></a><span data-ttu-id="92ed7-102">Punkt końcowy: Wywołania zabezpieczeń bez autoryzacji</span><span class="sxs-lookup"><span data-stu-id="92ed7-102">Endpoint: Security Calls Not Authorized</span></span>
<span data-ttu-id="92ed7-103">Nazwa licznika: Wywołania zabezpieczeń bez autoryzacji.</span><span class="sxs-lookup"><span data-stu-id="92ed7-103">Counter Name: Security Calls Not Authorized.</span></span>  
  
## <a name="description"></a><span data-ttu-id="92ed7-104">Opis</span><span class="sxs-lookup"><span data-stu-id="92ed7-104">Description</span></span>  
 <span data-ttu-id="92ed7-105">Ten licznik jest zwiększany po <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> metoda zwraca `false`.</span><span class="sxs-lookup"><span data-stu-id="92ed7-105">This counter is incremented when the <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> method returns `false`.</span></span> <span data-ttu-id="92ed7-106">Wskazuje on, przychodząca wiadomość pochodzi z prawidłowego użytkownika i odpowiednio chroniona, ale użytkownik nie ma uprawnień do wykonywania określonych zadań.</span><span class="sxs-lookup"><span data-stu-id="92ed7-106">It indicates that the incoming message is from a valid user and protected properly, but the user is not authorized to do specific tasks.</span></span>
