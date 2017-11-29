---
title: 1002 - WorkflowApplicationTerminated
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4e8b111f-79dc-4898-bb4a-e9b36f69420f
caps.latest.revision: "4"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 54ef06c3aded628e18325b78f55e80e4470ecd01
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="1002---workflowapplicationterminated"></a><span data-ttu-id="73890-102">1002 - WorkflowApplicationTerminated</span><span class="sxs-lookup"><span data-stu-id="73890-102">1002 - WorkflowApplicationTerminated</span></span>
## <a name="properties"></a><span data-ttu-id="73890-103">Właściwości</span><span class="sxs-lookup"><span data-stu-id="73890-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="73890-104">ID</span><span class="sxs-lookup"><span data-stu-id="73890-104">ID</span></span>|<span data-ttu-id="73890-105">1002</span><span class="sxs-lookup"><span data-stu-id="73890-105">1002</span></span>|  
|<span data-ttu-id="73890-106">Słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="73890-106">Keywords</span></span>|<span data-ttu-id="73890-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="73890-107">WFRuntime</span></span>|  
|<span data-ttu-id="73890-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="73890-108">Level</span></span>|<span data-ttu-id="73890-109">Informacje</span><span class="sxs-lookup"><span data-stu-id="73890-109">Information</span></span>|  
|<span data-ttu-id="73890-110">Kanał</span><span class="sxs-lookup"><span data-stu-id="73890-110">Channel</span></span>|<span data-ttu-id="73890-111">Microsoft-Windows aplikacji debugowania serwera — aplikacje</span><span class="sxs-lookup"><span data-stu-id="73890-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="73890-112">Opis</span><span class="sxs-lookup"><span data-stu-id="73890-112">Description</span></span>  
 <span data-ttu-id="73890-113">Wskazuje, że aplikacja przepływu pracy zostało przerwane w stanie Faulted z wyjątkiem.</span><span class="sxs-lookup"><span data-stu-id="73890-113">Indicates a workflow application has terminated in the Faulted state with an exception.</span></span>  
  
## <a name="message"></a><span data-ttu-id="73890-114">Komunikat</span><span class="sxs-lookup"><span data-stu-id="73890-114">Message</span></span>  
 <span data-ttu-id="73890-115">Obiekt WorkflowApplication o identyfikatorze: '%1' została zakończona.</span><span class="sxs-lookup"><span data-stu-id="73890-115">WorkflowApplication Id: '%1' was terminated.</span></span> <span data-ttu-id="73890-116">Została ukończona w stan końcowy: Faulted z wyjątkiem.</span><span class="sxs-lookup"><span data-stu-id="73890-116">It has completed in the Faulted state with an exception.</span></span>  
  
## <a name="details"></a><span data-ttu-id="73890-117">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="73890-117">Details</span></span>  
  
|<span data-ttu-id="73890-118">Nazwa elementu danych</span><span class="sxs-lookup"><span data-stu-id="73890-118">Data Item Name</span></span>|<span data-ttu-id="73890-119">Typ elementu danych</span><span class="sxs-lookup"><span data-stu-id="73890-119">Data Item Type</span></span>|<span data-ttu-id="73890-120">Opis</span><span class="sxs-lookup"><span data-stu-id="73890-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="73890-121">WorkflowApplicationId</span><span class="sxs-lookup"><span data-stu-id="73890-121">WorkflowApplicationId</span></span>|`xs:string`|<span data-ttu-id="73890-122">Identyfikator aplikacji przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="73890-122">The workflow application id</span></span>|  
|<span data-ttu-id="73890-123">Wyjątek</span><span class="sxs-lookup"><span data-stu-id="73890-123">Exception</span></span>|`xs:string`|<span data-ttu-id="73890-124">Szczegóły wyjątku dla wyjątku</span><span class="sxs-lookup"><span data-stu-id="73890-124">The exception details for the exception</span></span>|  
|<span data-ttu-id="73890-125">Domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="73890-125">AppDomain</span></span>|`xs:string`|<span data-ttu-id="73890-126">Długość ciągu zwróconego przez AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="73890-126">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
