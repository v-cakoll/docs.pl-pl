---
title: 1005 - WorkflowApplicationIdled
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 74d77dfa-f20d-4fe9-a6ae-e6d1b5fe4182
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: dc9f8f72000fe283baa5bb2814e41051c1424983
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="1005---workflowapplicationidled"></a><span data-ttu-id="cd87a-102">1005 - WorkflowApplicationIdled</span><span class="sxs-lookup"><span data-stu-id="cd87a-102">1005 - WorkflowApplicationIdled</span></span>
## <a name="properties"></a><span data-ttu-id="cd87a-103">Właściwości</span><span class="sxs-lookup"><span data-stu-id="cd87a-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="cd87a-104">ID</span><span class="sxs-lookup"><span data-stu-id="cd87a-104">ID</span></span>|<span data-ttu-id="cd87a-105">1005</span><span class="sxs-lookup"><span data-stu-id="cd87a-105">1005</span></span>|  
|<span data-ttu-id="cd87a-106">Słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="cd87a-106">Keywords</span></span>|<span data-ttu-id="cd87a-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="cd87a-107">WFRuntime</span></span>|  
|<span data-ttu-id="cd87a-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="cd87a-108">Level</span></span>|<span data-ttu-id="cd87a-109">Informacje</span><span class="sxs-lookup"><span data-stu-id="cd87a-109">Information</span></span>|  
|<span data-ttu-id="cd87a-110">Kanał</span><span class="sxs-lookup"><span data-stu-id="cd87a-110">Channel</span></span>|<span data-ttu-id="cd87a-111">Microsoft-Windows aplikacji debugowania serwera — aplikacje</span><span class="sxs-lookup"><span data-stu-id="cd87a-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="cd87a-112">Opis</span><span class="sxs-lookup"><span data-stu-id="cd87a-112">Description</span></span>  
 <span data-ttu-id="cd87a-113">Wskazuje, że ma idled aplikacji przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="cd87a-113">Indicates a workflow application has idled.</span></span>  
  
## <a name="message"></a><span data-ttu-id="cd87a-114">Komunikat</span><span class="sxs-lookup"><span data-stu-id="cd87a-114">Message</span></span>  
 <span data-ttu-id="cd87a-115">Obiekt WorkflowApplication o identyfikatorze: "%1" zakończył bezczynności.</span><span class="sxs-lookup"><span data-stu-id="cd87a-115">WorkflowApplication Id: '%1' went idle.</span></span>  
  
## <a name="details"></a><span data-ttu-id="cd87a-116">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="cd87a-116">Details</span></span>  
  
|<span data-ttu-id="cd87a-117">Nazwa elementu danych</span><span class="sxs-lookup"><span data-stu-id="cd87a-117">Data Item Name</span></span>|<span data-ttu-id="cd87a-118">Typ elementu danych</span><span class="sxs-lookup"><span data-stu-id="cd87a-118">Data Item Type</span></span>|<span data-ttu-id="cd87a-119">Opis</span><span class="sxs-lookup"><span data-stu-id="cd87a-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="cd87a-120">WorkflowInstanceId</span><span class="sxs-lookup"><span data-stu-id="cd87a-120">WorkflowInstanceId</span></span>|`xs:string`|<span data-ttu-id="cd87a-121">Identyfikator aplikacji przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="cd87a-121">The workflow application id</span></span>|  
|<span data-ttu-id="cd87a-122">Domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="cd87a-122">AppDomain</span></span>|`xs:string`|<span data-ttu-id="cd87a-123">Długość ciągu zwróconego przez AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="cd87a-123">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
