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
ms.openlocfilehash: 2603621eb23747275e6db22a1743c5260967c6a3
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="1005---workflowapplicationidled"></a><span data-ttu-id="0a9f9-102">1005 - WorkflowApplicationIdled</span><span class="sxs-lookup"><span data-stu-id="0a9f9-102">1005 - WorkflowApplicationIdled</span></span>
## <a name="properties"></a><span data-ttu-id="0a9f9-103">Właściwości</span><span class="sxs-lookup"><span data-stu-id="0a9f9-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="0a9f9-104">ID</span><span class="sxs-lookup"><span data-stu-id="0a9f9-104">ID</span></span>|<span data-ttu-id="0a9f9-105">1005</span><span class="sxs-lookup"><span data-stu-id="0a9f9-105">1005</span></span>|  
|<span data-ttu-id="0a9f9-106">Słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="0a9f9-106">Keywords</span></span>|<span data-ttu-id="0a9f9-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="0a9f9-107">WFRuntime</span></span>|  
|<span data-ttu-id="0a9f9-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="0a9f9-108">Level</span></span>|<span data-ttu-id="0a9f9-109">Informacje</span><span class="sxs-lookup"><span data-stu-id="0a9f9-109">Information</span></span>|  
|<span data-ttu-id="0a9f9-110">Kanał</span><span class="sxs-lookup"><span data-stu-id="0a9f9-110">Channel</span></span>|<span data-ttu-id="0a9f9-111">Microsoft-Windows aplikacji debugowania serwera — aplikacje</span><span class="sxs-lookup"><span data-stu-id="0a9f9-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="0a9f9-112">Opis</span><span class="sxs-lookup"><span data-stu-id="0a9f9-112">Description</span></span>  
 <span data-ttu-id="0a9f9-113">Wskazuje, że ma idled aplikacji przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="0a9f9-113">Indicates a workflow application has idled.</span></span>  
  
## <a name="message"></a><span data-ttu-id="0a9f9-114">Komunikat</span><span class="sxs-lookup"><span data-stu-id="0a9f9-114">Message</span></span>  
 <span data-ttu-id="0a9f9-115">Obiekt WorkflowApplication o identyfikatorze: "%1" zakończył bezczynności.</span><span class="sxs-lookup"><span data-stu-id="0a9f9-115">WorkflowApplication Id: '%1' went idle.</span></span>  
  
## <a name="details"></a><span data-ttu-id="0a9f9-116">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="0a9f9-116">Details</span></span>  
  
|<span data-ttu-id="0a9f9-117">Nazwa elementu danych</span><span class="sxs-lookup"><span data-stu-id="0a9f9-117">Data Item Name</span></span>|<span data-ttu-id="0a9f9-118">Typ elementu danych</span><span class="sxs-lookup"><span data-stu-id="0a9f9-118">Data Item Type</span></span>|<span data-ttu-id="0a9f9-119">Opis</span><span class="sxs-lookup"><span data-stu-id="0a9f9-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="0a9f9-120">WorkflowInstanceId</span><span class="sxs-lookup"><span data-stu-id="0a9f9-120">WorkflowInstanceId</span></span>|`xs:string`|<span data-ttu-id="0a9f9-121">Identyfikator aplikacji przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="0a9f9-121">The workflow application id</span></span>|  
|<span data-ttu-id="0a9f9-122">Domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="0a9f9-122">AppDomain</span></span>|`xs:string`|<span data-ttu-id="0a9f9-123">Długość ciągu zwróconego przez AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="0a9f9-123">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
