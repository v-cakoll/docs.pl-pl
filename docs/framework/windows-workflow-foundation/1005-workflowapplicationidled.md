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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 42d22a7187adc712c0f236111cecac89dd59e2f4
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="1005---workflowapplicationidled"></a><span data-ttu-id="e3e2a-102">1005 - WorkflowApplicationIdled</span><span class="sxs-lookup"><span data-stu-id="e3e2a-102">1005 - WorkflowApplicationIdled</span></span>
## <a name="properties"></a><span data-ttu-id="e3e2a-103">Właściwości</span><span class="sxs-lookup"><span data-stu-id="e3e2a-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="e3e2a-104">ID</span><span class="sxs-lookup"><span data-stu-id="e3e2a-104">ID</span></span>|<span data-ttu-id="e3e2a-105">1005</span><span class="sxs-lookup"><span data-stu-id="e3e2a-105">1005</span></span>|  
|<span data-ttu-id="e3e2a-106">Słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="e3e2a-106">Keywords</span></span>|<span data-ttu-id="e3e2a-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="e3e2a-107">WFRuntime</span></span>|  
|<span data-ttu-id="e3e2a-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="e3e2a-108">Level</span></span>|<span data-ttu-id="e3e2a-109">Informacje</span><span class="sxs-lookup"><span data-stu-id="e3e2a-109">Information</span></span>|  
|<span data-ttu-id="e3e2a-110">Kanał</span><span class="sxs-lookup"><span data-stu-id="e3e2a-110">Channel</span></span>|<span data-ttu-id="e3e2a-111">Microsoft-Windows aplikacji debugowania serwera — aplikacje</span><span class="sxs-lookup"><span data-stu-id="e3e2a-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="e3e2a-112">Opis</span><span class="sxs-lookup"><span data-stu-id="e3e2a-112">Description</span></span>  
 <span data-ttu-id="e3e2a-113">Wskazuje, że ma idled aplikacji przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="e3e2a-113">Indicates a workflow application has idled.</span></span>  
  
## <a name="message"></a><span data-ttu-id="e3e2a-114">Komunikat</span><span class="sxs-lookup"><span data-stu-id="e3e2a-114">Message</span></span>  
 <span data-ttu-id="e3e2a-115">Obiekt WorkflowApplication o identyfikatorze: "%1" zakończył bezczynności.</span><span class="sxs-lookup"><span data-stu-id="e3e2a-115">WorkflowApplication Id: '%1' went idle.</span></span>  
  
## <a name="details"></a><span data-ttu-id="e3e2a-116">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="e3e2a-116">Details</span></span>  
  
|<span data-ttu-id="e3e2a-117">Nazwa elementu danych</span><span class="sxs-lookup"><span data-stu-id="e3e2a-117">Data Item Name</span></span>|<span data-ttu-id="e3e2a-118">Typ elementu danych</span><span class="sxs-lookup"><span data-stu-id="e3e2a-118">Data Item Type</span></span>|<span data-ttu-id="e3e2a-119">Opis</span><span class="sxs-lookup"><span data-stu-id="e3e2a-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="e3e2a-120">WorkflowInstanceId</span><span class="sxs-lookup"><span data-stu-id="e3e2a-120">WorkflowInstanceId</span></span>|`xs:string`|<span data-ttu-id="e3e2a-121">Identyfikator aplikacji przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="e3e2a-121">The workflow application id</span></span>|  
|<span data-ttu-id="e3e2a-122">Domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="e3e2a-122">AppDomain</span></span>|`xs:string`|<span data-ttu-id="e3e2a-123">Długość ciągu zwróconego przez AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="e3e2a-123">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
