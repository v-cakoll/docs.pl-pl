---
title: 1008 - WorkflowApplicationUnloaded
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a605b780-4a7e-43ab-92e7-0a3b01d053b0
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: dedb1dd389e2308ea8f70d71f057d17a45172517
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="1008---workflowapplicationunloaded"></a><span data-ttu-id="2a723-102">1008 - WorkflowApplicationUnloaded</span><span class="sxs-lookup"><span data-stu-id="2a723-102">1008 - WorkflowApplicationUnloaded</span></span>
## <a name="properties"></a><span data-ttu-id="2a723-103">Właściwości</span><span class="sxs-lookup"><span data-stu-id="2a723-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="2a723-104">ID</span><span class="sxs-lookup"><span data-stu-id="2a723-104">ID</span></span>|<span data-ttu-id="2a723-105">1008</span><span class="sxs-lookup"><span data-stu-id="2a723-105">1008</span></span>|  
|<span data-ttu-id="2a723-106">Słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="2a723-106">Keywords</span></span>|<span data-ttu-id="2a723-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="2a723-107">WFRuntime</span></span>|  
|<span data-ttu-id="2a723-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="2a723-108">Level</span></span>|<span data-ttu-id="2a723-109">Informacje</span><span class="sxs-lookup"><span data-stu-id="2a723-109">Information</span></span>|  
|<span data-ttu-id="2a723-110">Kanał</span><span class="sxs-lookup"><span data-stu-id="2a723-110">Channel</span></span>|<span data-ttu-id="2a723-111">Microsoft-Windows aplikacji debugowania serwera — aplikacje</span><span class="sxs-lookup"><span data-stu-id="2a723-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="2a723-112">Opis</span><span class="sxs-lookup"><span data-stu-id="2a723-112">Description</span></span>  
 <span data-ttu-id="2a723-113">Wskazuje, że aplikacja przepływu pracy został zwolniony.</span><span class="sxs-lookup"><span data-stu-id="2a723-113">Indicates a workflow application has unloaded.</span></span>  
  
## <a name="message"></a><span data-ttu-id="2a723-114">Komunikat</span><span class="sxs-lookup"><span data-stu-id="2a723-114">Message</span></span>  
 <span data-ttu-id="2a723-115">Obiekt WorkflowInstance o identyfikatorze: '%1' został Unloaded.</span><span class="sxs-lookup"><span data-stu-id="2a723-115">WorkflowInstance Id: '%1' was Unloaded.</span></span>  
  
## <a name="details"></a><span data-ttu-id="2a723-116">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="2a723-116">Details</span></span>  
  
|<span data-ttu-id="2a723-117">Nazwa elementu danych</span><span class="sxs-lookup"><span data-stu-id="2a723-117">Data Item Name</span></span>|<span data-ttu-id="2a723-118">Typ elementu danych</span><span class="sxs-lookup"><span data-stu-id="2a723-118">Data Item Type</span></span>|<span data-ttu-id="2a723-119">Opis</span><span class="sxs-lookup"><span data-stu-id="2a723-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="2a723-120">WorkflowInstanceId</span><span class="sxs-lookup"><span data-stu-id="2a723-120">WorkflowInstanceId</span></span>|`xs:string`|<span data-ttu-id="2a723-121">Identyfikator wystąpienia przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="2a723-121">The instance id for the workflow</span></span>|  
|<span data-ttu-id="2a723-122">Domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="2a723-122">AppDomain</span></span>|`xs:string`|<span data-ttu-id="2a723-123">Długość ciągu zwróconego przez AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="2a723-123">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
