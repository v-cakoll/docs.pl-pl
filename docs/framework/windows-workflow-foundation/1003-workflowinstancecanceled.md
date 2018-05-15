---
title: 1003 - WorkflowInstanceCanceled
ms.date: 03/30/2017
ms.assetid: 64754dc2-c160-4bf3-869a-13d56694e2dc
ms.openlocfilehash: c76a2dab6a95bda7f3969af07f814aba30071c7f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="1003---workflowinstancecanceled"></a><span data-ttu-id="b9a77-102">1003 - WorkflowInstanceCanceled</span><span class="sxs-lookup"><span data-stu-id="b9a77-102">1003 - WorkflowInstanceCanceled</span></span>
## <a name="properties"></a><span data-ttu-id="b9a77-103">Właściwości</span><span class="sxs-lookup"><span data-stu-id="b9a77-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="b9a77-104">ID</span><span class="sxs-lookup"><span data-stu-id="b9a77-104">ID</span></span>|<span data-ttu-id="b9a77-105">1003</span><span class="sxs-lookup"><span data-stu-id="b9a77-105">1003</span></span>|  
|<span data-ttu-id="b9a77-106">Słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="b9a77-106">Keywords</span></span>|<span data-ttu-id="b9a77-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="b9a77-107">WFRuntime</span></span>|  
|<span data-ttu-id="b9a77-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="b9a77-108">Level</span></span>|<span data-ttu-id="b9a77-109">Informacje</span><span class="sxs-lookup"><span data-stu-id="b9a77-109">Information</span></span>|  
|<span data-ttu-id="b9a77-110">Kanał</span><span class="sxs-lookup"><span data-stu-id="b9a77-110">Channel</span></span>|<span data-ttu-id="b9a77-111">Microsoft-Windows aplikacji debugowania serwera — aplikacje</span><span class="sxs-lookup"><span data-stu-id="b9a77-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="b9a77-112">Opis</span><span class="sxs-lookup"><span data-stu-id="b9a77-112">Description</span></span>  
 <span data-ttu-id="b9a77-113">Wskazuje, że wystąpienie przepływu pracy zostało zakończone; stan anulowane.</span><span class="sxs-lookup"><span data-stu-id="b9a77-113">Indicates a workflow instance has completed in the Canceled state.</span></span>  
  
## <a name="message"></a><span data-ttu-id="b9a77-114">Komunikat</span><span class="sxs-lookup"><span data-stu-id="b9a77-114">Message</span></span>  
 <span data-ttu-id="b9a77-115">Obiekt WorkflowInstance o identyfikatorze: "%1" została ukończona w stan anulowane.</span><span class="sxs-lookup"><span data-stu-id="b9a77-115">WorkflowInstance Id: '%1' has completed in the Canceled state.</span></span>  
  
## <a name="details"></a><span data-ttu-id="b9a77-116">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="b9a77-116">Details</span></span>  
  
|<span data-ttu-id="b9a77-117">Nazwa elementu danych</span><span class="sxs-lookup"><span data-stu-id="b9a77-117">Data Item Name</span></span>|<span data-ttu-id="b9a77-118">Typ elementu danych</span><span class="sxs-lookup"><span data-stu-id="b9a77-118">Data Item Type</span></span>|<span data-ttu-id="b9a77-119">Opis</span><span class="sxs-lookup"><span data-stu-id="b9a77-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="b9a77-120">WorkflowInstanceId</span><span class="sxs-lookup"><span data-stu-id="b9a77-120">WorkflowInstanceId</span></span>|`xs:string`|<span data-ttu-id="b9a77-121">Identyfikator wystąpienia przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="b9a77-121">The instance id for the workflow</span></span>|  
|<span data-ttu-id="b9a77-122">Domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="b9a77-122">AppDomain</span></span>|`xs:string`|<span data-ttu-id="b9a77-123">Długość ciągu zwróconego przez AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="b9a77-123">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
