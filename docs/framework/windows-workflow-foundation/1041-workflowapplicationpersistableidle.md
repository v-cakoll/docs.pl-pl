---
title: 1041 - WorkflowApplicationPersistableIdle
ms.date: 03/30/2017
ms.assetid: 966adf2f-e21d-44df-a3ec-a8e285e0a316
ms.openlocfilehash: 07be0ae603443a1ef06cb539bba7b227d7b3e325
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="1041---workflowapplicationpersistableidle"></a><span data-ttu-id="370ed-102">1041 - WorkflowApplicationPersistableIdle</span><span class="sxs-lookup"><span data-stu-id="370ed-102">1041 - WorkflowApplicationPersistableIdle</span></span>
## <a name="properties"></a><span data-ttu-id="370ed-103">Właściwości</span><span class="sxs-lookup"><span data-stu-id="370ed-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="370ed-104">ID</span><span class="sxs-lookup"><span data-stu-id="370ed-104">ID</span></span>|<span data-ttu-id="370ed-105">1041</span><span class="sxs-lookup"><span data-stu-id="370ed-105">1041</span></span>|  
|<span data-ttu-id="370ed-106">Słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="370ed-106">Keywords</span></span>|<span data-ttu-id="370ed-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="370ed-107">WFRuntime</span></span>|  
|<span data-ttu-id="370ed-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="370ed-108">Level</span></span>|<span data-ttu-id="370ed-109">Informacje</span><span class="sxs-lookup"><span data-stu-id="370ed-109">Information</span></span>|  
|<span data-ttu-id="370ed-110">Kanał</span><span class="sxs-lookup"><span data-stu-id="370ed-110">Channel</span></span>|<span data-ttu-id="370ed-111">Microsoft-Windows aplikacji debugowania serwera — aplikacje</span><span class="sxs-lookup"><span data-stu-id="370ed-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="370ed-112">Opis</span><span class="sxs-lookup"><span data-stu-id="370ed-112">Description</span></span>  
 <span data-ttu-id="370ed-113">Wskazuje, że aplikacja przepływu pracy jest bezczynny i możliwy do utrwalenia.</span><span class="sxs-lookup"><span data-stu-id="370ed-113">Indicates that a workflow application is idle and persistable.</span></span> <span data-ttu-id="370ed-114">Aplikacja przepływu pracy będą idled lub utrwalone.</span><span class="sxs-lookup"><span data-stu-id="370ed-114">The workflow application will be idled or persisted.</span></span>  
  
## <a name="message"></a><span data-ttu-id="370ed-115">Komunikat</span><span class="sxs-lookup"><span data-stu-id="370ed-115">Message</span></span>  
 <span data-ttu-id="370ed-116">Obiekt WorkflowApplication o identyfikatorze: "%1" jest bezczynny i możliwy do utrwalenia.</span><span class="sxs-lookup"><span data-stu-id="370ed-116">WorkflowApplication Id: '%1' is idle and persistable.</span></span>  <span data-ttu-id="370ed-117">Zostanie podjęta następująca Akcja: %2.</span><span class="sxs-lookup"><span data-stu-id="370ed-117">The following action will be taken: %2.</span></span>  
  
## <a name="details"></a><span data-ttu-id="370ed-118">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="370ed-118">Details</span></span>  
  
|<span data-ttu-id="370ed-119">Nazwa elementu danych</span><span class="sxs-lookup"><span data-stu-id="370ed-119">Data Item Name</span></span>|<span data-ttu-id="370ed-120">Typ elementu danych</span><span class="sxs-lookup"><span data-stu-id="370ed-120">Data Item Type</span></span>|<span data-ttu-id="370ed-121">Opis</span><span class="sxs-lookup"><span data-stu-id="370ed-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="370ed-122">WorkflowApplicationId</span><span class="sxs-lookup"><span data-stu-id="370ed-122">WorkflowApplicationId</span></span>|<span data-ttu-id="370ed-123">xs:String</span><span class="sxs-lookup"><span data-stu-id="370ed-123">xs:string</span></span>|<span data-ttu-id="370ed-124">Identyfikator aplikacji przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="370ed-124">The workflow application id</span></span>|  
|<span data-ttu-id="370ed-125">ActionTaken</span><span class="sxs-lookup"><span data-stu-id="370ed-125">ActionTaken</span></span>|<span data-ttu-id="370ed-126">xs:String</span><span class="sxs-lookup"><span data-stu-id="370ed-126">xs:string</span></span>|<span data-ttu-id="370ed-127">Akcja, która wpłynie na aplikacji przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="370ed-127">The action that will be taken on the workflow application.</span></span>|  
|<span data-ttu-id="370ed-128">Domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="370ed-128">AppDomain</span></span>|<span data-ttu-id="370ed-129">xs:String</span><span class="sxs-lookup"><span data-stu-id="370ed-129">xs:string</span></span>|<span data-ttu-id="370ed-130">Długość ciągu zwróconego przez AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="370ed-130">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
