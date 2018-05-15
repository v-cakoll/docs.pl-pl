---
title: Działania środowiska uruchomieniowego w WF
ms.date: 03/30/2017
ms.assetid: e5ae8c31-19bc-4655-88b3-6b75cd6a1bd5
ms.openlocfilehash: 7981d3f75c8fd2d0ddd2ae0233f425c2907c270c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="runtime-activities-in-wf"></a><span data-ttu-id="463bf-102">Działania środowiska uruchomieniowego w WF</span><span class="sxs-lookup"><span data-stu-id="463bf-102">Runtime Activities in WF</span></span>
[!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)]<span data-ttu-id="463bf-103"> zawiera kilka działań dostarczane przez system do uzyskiwania dostępu do funkcji środowiska uruchomieniowego przepływu pracy, takich jak trwałości i kończenie działania.</span><span class="sxs-lookup"><span data-stu-id="463bf-103"> provides several system-provided activities for accessing the features of the workflow runtime, such as persistence and termination.</span></span>  
  
|<span data-ttu-id="463bf-104">Działanie</span><span class="sxs-lookup"><span data-stu-id="463bf-104">Activity</span></span>|<span data-ttu-id="463bf-105">Opis</span><span class="sxs-lookup"><span data-stu-id="463bf-105">Description</span></span>|  
|--------------|-----------------|  
|<xref:System.Activities.Statements.Persist>|<span data-ttu-id="463bf-106">Wyraźnie zażąda, że przepływ pracy utrwalić stanu.</span><span class="sxs-lookup"><span data-stu-id="463bf-106">Explicitly requests that the workflow persist its state.</span></span>|  
|<xref:System.Activities.Statements.TerminateWorkflow>|<span data-ttu-id="463bf-107">Kończy uruchomione wystąpienie przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="463bf-107">Terminates the running workflow instance.</span></span>|  
|<xref:System.Activities.Statements.NoPersistScope>|<span data-ttu-id="463bf-108">Działanie kontenera, który uniemożliwia utrwalanie działań podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="463bf-108">A container activity that prevents child activities from persisting.</span></span>|
