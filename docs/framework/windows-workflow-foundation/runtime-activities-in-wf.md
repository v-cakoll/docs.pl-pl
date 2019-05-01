---
title: Działania środowiska uruchomieniowego w WF
ms.date: 03/30/2017
ms.assetid: e5ae8c31-19bc-4655-88b3-6b75cd6a1bd5
ms.openlocfilehash: 7981d3f75c8fd2d0ddd2ae0233f425c2907c270c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61938102"
---
# <a name="runtime-activities-in-wf"></a><span data-ttu-id="ca13d-102">Działania środowiska uruchomieniowego w WF</span><span class="sxs-lookup"><span data-stu-id="ca13d-102">Runtime Activities in WF</span></span>
[!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] <span data-ttu-id="ca13d-103">zawiera kilka działań dostarczane przez system do uzyskiwania dostępu do funkcji środowiska uruchomieniowego przepływu pracy, takich jak trwałości i kończenie działania.</span><span class="sxs-lookup"><span data-stu-id="ca13d-103">provides several system-provided activities for accessing the features of the workflow runtime, such as persistence and termination.</span></span>  
  
|<span data-ttu-id="ca13d-104">Działanie</span><span class="sxs-lookup"><span data-stu-id="ca13d-104">Activity</span></span>|<span data-ttu-id="ca13d-105">Opis</span><span class="sxs-lookup"><span data-stu-id="ca13d-105">Description</span></span>|  
|--------------|-----------------|  
|<xref:System.Activities.Statements.Persist>|<span data-ttu-id="ca13d-106">Wyraźnie zażąda, że przepływ pracy utrwalanie stanu.</span><span class="sxs-lookup"><span data-stu-id="ca13d-106">Explicitly requests that the workflow persist its state.</span></span>|  
|<xref:System.Activities.Statements.TerminateWorkflow>|<span data-ttu-id="ca13d-107">Kończy się na uruchomione wystąpienie przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="ca13d-107">Terminates the running workflow instance.</span></span>|  
|<xref:System.Activities.Statements.NoPersistScope>|<span data-ttu-id="ca13d-108">Działanie kontenera, który uniemożliwia utrwalaniu działań podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="ca13d-108">A container activity that prevents child activities from persisting.</span></span>|
