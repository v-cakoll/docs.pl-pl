---
title: "Punkt końcowy: Wywołania zabezpieczeń bez autoryzacji"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d25095ff-9ff0-4c69-a674-4e6a9fe3f4dc
caps.latest.revision: "4"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 39c6b3fe9ef527b276a0dc4f6dc9e11b6125c609
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="endpoint-security-calls-not-authorized"></a><span data-ttu-id="af379-102">Punkt końcowy: Wywołania zabezpieczeń bez autoryzacji</span><span class="sxs-lookup"><span data-stu-id="af379-102">Endpoint: Security Calls Not Authorized</span></span>
<span data-ttu-id="af379-103">Nazwa licznika: Wywołania zabezpieczeń bez autoryzacji.</span><span class="sxs-lookup"><span data-stu-id="af379-103">Counter Name: Security Calls Not Authorized.</span></span>  
  
## <a name="description"></a><span data-ttu-id="af379-104">Opis</span><span class="sxs-lookup"><span data-stu-id="af379-104">Description</span></span>  
 <span data-ttu-id="af379-105">Ten licznik jest zwiększany po <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> metoda zwraca `false`.</span><span class="sxs-lookup"><span data-stu-id="af379-105">This counter is incremented when the <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> method returns `false`.</span></span> <span data-ttu-id="af379-106">Wskazuje on, że przychodzący komunikat pochodzi z prawidłowego użytkownika i odpowiednio chroniona, ale użytkownik nie ma uprawnień do wykonywania określonych zadań.</span><span class="sxs-lookup"><span data-stu-id="af379-106">It indicates that the incoming message is from a valid user and protected properly, but the user is not authorized to do specific tasks.</span></span>
