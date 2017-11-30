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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 297b3ad9a677d28d12d1b00fdaeec8ec94842263
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="1008---workflowapplicationunloaded"></a><span data-ttu-id="cd23c-102">1008 - WorkflowApplicationUnloaded</span><span class="sxs-lookup"><span data-stu-id="cd23c-102">1008 - WorkflowApplicationUnloaded</span></span>
## <a name="properties"></a><span data-ttu-id="cd23c-103">Właściwości</span><span class="sxs-lookup"><span data-stu-id="cd23c-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="cd23c-104">ID</span><span class="sxs-lookup"><span data-stu-id="cd23c-104">ID</span></span>|<span data-ttu-id="cd23c-105">1008</span><span class="sxs-lookup"><span data-stu-id="cd23c-105">1008</span></span>|  
|<span data-ttu-id="cd23c-106">Słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="cd23c-106">Keywords</span></span>|<span data-ttu-id="cd23c-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="cd23c-107">WFRuntime</span></span>|  
|<span data-ttu-id="cd23c-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="cd23c-108">Level</span></span>|<span data-ttu-id="cd23c-109">Informacje</span><span class="sxs-lookup"><span data-stu-id="cd23c-109">Information</span></span>|  
|<span data-ttu-id="cd23c-110">Kanał</span><span class="sxs-lookup"><span data-stu-id="cd23c-110">Channel</span></span>|<span data-ttu-id="cd23c-111">Microsoft-Windows aplikacji debugowania serwera — aplikacje</span><span class="sxs-lookup"><span data-stu-id="cd23c-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="cd23c-112">Opis</span><span class="sxs-lookup"><span data-stu-id="cd23c-112">Description</span></span>  
 <span data-ttu-id="cd23c-113">Wskazuje, że aplikacja przepływu pracy został zwolniony.</span><span class="sxs-lookup"><span data-stu-id="cd23c-113">Indicates a workflow application has unloaded.</span></span>  
  
## <a name="message"></a><span data-ttu-id="cd23c-114">Komunikat</span><span class="sxs-lookup"><span data-stu-id="cd23c-114">Message</span></span>  
 <span data-ttu-id="cd23c-115">Obiekt WorkflowInstance o identyfikatorze: '%1' został Unloaded.</span><span class="sxs-lookup"><span data-stu-id="cd23c-115">WorkflowInstance Id: '%1' was Unloaded.</span></span>  
  
## <a name="details"></a><span data-ttu-id="cd23c-116">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="cd23c-116">Details</span></span>  
  
|<span data-ttu-id="cd23c-117">Nazwa elementu danych</span><span class="sxs-lookup"><span data-stu-id="cd23c-117">Data Item Name</span></span>|<span data-ttu-id="cd23c-118">Typ elementu danych</span><span class="sxs-lookup"><span data-stu-id="cd23c-118">Data Item Type</span></span>|<span data-ttu-id="cd23c-119">Opis</span><span class="sxs-lookup"><span data-stu-id="cd23c-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="cd23c-120">WorkflowInstanceId</span><span class="sxs-lookup"><span data-stu-id="cd23c-120">WorkflowInstanceId</span></span>|`xs:string`|<span data-ttu-id="cd23c-121">Identyfikator wystąpienia przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="cd23c-121">The instance id for the workflow</span></span>|  
|<span data-ttu-id="cd23c-122">Domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="cd23c-122">AppDomain</span></span>|`xs:string`|<span data-ttu-id="cd23c-123">Długość ciągu zwróconego przez AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="cd23c-123">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
