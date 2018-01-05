---
title: "Działania środowiska uruchomieniowego w WF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e5ae8c31-19bc-4655-88b3-6b75cd6a1bd5
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3386138f01d4865b02ca821a30da68e5d73b64e0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="runtime-activities-in-wf"></a><span data-ttu-id="99dfc-102">Działania środowiska uruchomieniowego w WF</span><span class="sxs-lookup"><span data-stu-id="99dfc-102">Runtime Activities in WF</span></span>
[!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)]<span data-ttu-id="99dfc-103">zawiera kilka działań dostarczane przez system do uzyskiwania dostępu do funkcji środowiska uruchomieniowego przepływu pracy, takich jak trwałości i kończenie działania.</span><span class="sxs-lookup"><span data-stu-id="99dfc-103"> provides several system-provided activities for accessing the features of the workflow runtime, such as persistence and termination.</span></span>  
  
|<span data-ttu-id="99dfc-104">Działanie</span><span class="sxs-lookup"><span data-stu-id="99dfc-104">Activity</span></span>|<span data-ttu-id="99dfc-105">Opis</span><span class="sxs-lookup"><span data-stu-id="99dfc-105">Description</span></span>|  
|--------------|-----------------|  
|<xref:System.Activities.Statements.Persist>|<span data-ttu-id="99dfc-106">Wyraźnie zażąda, że przepływ pracy utrwalić stanu.</span><span class="sxs-lookup"><span data-stu-id="99dfc-106">Explicitly requests that the workflow persist its state.</span></span>|  
|<xref:System.Activities.Statements.TerminateWorkflow>|<span data-ttu-id="99dfc-107">Kończy uruchomione wystąpienie przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="99dfc-107">Terminates the running workflow instance.</span></span>|  
|<xref:System.Activities.Statements.NoPersistScope>|<span data-ttu-id="99dfc-108">Działanie kontenera, który uniemożliwia utrwalanie działań podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="99dfc-108">A container activity that prevents child activities from persisting.</span></span>|
