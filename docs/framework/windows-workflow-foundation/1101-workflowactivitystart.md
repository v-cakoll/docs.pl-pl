---
title: 1101 — WorkflowActivityStart
ms.date: 03/30/2017
ms.assetid: 831cd386-b9b5-47a9-9690-aff6292ff348
ms.openlocfilehash: 1e6db97284b7ca83d532166d96d7a42df0a51091
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61924153"
---
# <a name="1101---workflowactivitystart"></a><span data-ttu-id="2a921-102">1101 — WorkflowActivityStart</span><span class="sxs-lookup"><span data-stu-id="2a921-102">1101 - WorkflowActivityStart</span></span>
## <a name="properties"></a><span data-ttu-id="2a921-103">Właściwości</span><span class="sxs-lookup"><span data-stu-id="2a921-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="2a921-104">Identyfikator</span><span class="sxs-lookup"><span data-stu-id="2a921-104">ID</span></span>|<span data-ttu-id="2a921-105">1101</span><span class="sxs-lookup"><span data-stu-id="2a921-105">1101</span></span>|  
|<span data-ttu-id="2a921-106">słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="2a921-106">Keywords</span></span>|<span data-ttu-id="2a921-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="2a921-107">WFRuntime</span></span>|  
|<span data-ttu-id="2a921-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="2a921-108">Level</span></span>|<span data-ttu-id="2a921-109">Informacje</span><span class="sxs-lookup"><span data-stu-id="2a921-109">Information</span></span>|  
|<span data-ttu-id="2a921-110">Kanał</span><span class="sxs-lookup"><span data-stu-id="2a921-110">Channel</span></span>|<span data-ttu-id="2a921-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="2a921-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="2a921-112">Opis</span><span class="sxs-lookup"><span data-stu-id="2a921-112">Description</span></span>  
 <span data-ttu-id="2a921-113">Wskazuje, że działanie przepływu pracy została uruchomiona.</span><span class="sxs-lookup"><span data-stu-id="2a921-113">Indicates a workflow activity has started.</span></span>  
  
## <a name="message"></a><span data-ttu-id="2a921-114">Komunikat</span><span class="sxs-lookup"><span data-stu-id="2a921-114">Message</span></span>  
 <span data-ttu-id="2a921-115">WorkflowInstance Id: Aktivita E2E "%1"</span><span class="sxs-lookup"><span data-stu-id="2a921-115">WorkflowInstance Id: '%1' E2E Activity</span></span>  
  
## <a name="details"></a><span data-ttu-id="2a921-116">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="2a921-116">Details</span></span>  
  
|<span data-ttu-id="2a921-117">Nazwa elementu danych</span><span class="sxs-lookup"><span data-stu-id="2a921-117">Data Item Name</span></span>|<span data-ttu-id="2a921-118">Typ elementu danych</span><span class="sxs-lookup"><span data-stu-id="2a921-118">Data Item Type</span></span>|<span data-ttu-id="2a921-119">Opis</span><span class="sxs-lookup"><span data-stu-id="2a921-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="2a921-120">WorkflowInstanceId</span><span class="sxs-lookup"><span data-stu-id="2a921-120">WorkflowInstanceId</span></span>|<span data-ttu-id="2a921-121">xs:String</span><span class="sxs-lookup"><span data-stu-id="2a921-121">xs:string</span></span>|<span data-ttu-id="2a921-122">Identyfikator wystąpienia przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="2a921-122">The workflow instance id.</span></span>|  
|<span data-ttu-id="2a921-123">AppDomain</span><span class="sxs-lookup"><span data-stu-id="2a921-123">AppDomain</span></span>|<span data-ttu-id="2a921-124">xs:String</span><span class="sxs-lookup"><span data-stu-id="2a921-124">xs:string</span></span>|<span data-ttu-id="2a921-125">Ciąg zwracany przez AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="2a921-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
