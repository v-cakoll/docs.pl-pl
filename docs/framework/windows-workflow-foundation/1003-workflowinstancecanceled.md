---
title: 1003 — WorkflowInstanceCanceled
ms.date: 03/30/2017
ms.assetid: 64754dc2-c160-4bf3-869a-13d56694e2dc
ms.openlocfilehash: c76a2dab6a95bda7f3969af07f814aba30071c7f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62008632"
---
# <a name="1003---workflowinstancecanceled"></a><span data-ttu-id="4af10-102">1003 — WorkflowInstanceCanceled</span><span class="sxs-lookup"><span data-stu-id="4af10-102">1003 - WorkflowInstanceCanceled</span></span>
## <a name="properties"></a><span data-ttu-id="4af10-103">Właściwości</span><span class="sxs-lookup"><span data-stu-id="4af10-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="4af10-104">Identyfikator</span><span class="sxs-lookup"><span data-stu-id="4af10-104">ID</span></span>|<span data-ttu-id="4af10-105">1003</span><span class="sxs-lookup"><span data-stu-id="4af10-105">1003</span></span>|  
|<span data-ttu-id="4af10-106">słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="4af10-106">Keywords</span></span>|<span data-ttu-id="4af10-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="4af10-107">WFRuntime</span></span>|  
|<span data-ttu-id="4af10-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="4af10-108">Level</span></span>|<span data-ttu-id="4af10-109">Informacje</span><span class="sxs-lookup"><span data-stu-id="4af10-109">Information</span></span>|  
|<span data-ttu-id="4af10-110">Kanał</span><span class="sxs-lookup"><span data-stu-id="4af10-110">Channel</span></span>|<span data-ttu-id="4af10-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="4af10-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="4af10-112">Opis</span><span class="sxs-lookup"><span data-stu-id="4af10-112">Description</span></span>  
 <span data-ttu-id="4af10-113">Wskazuje, że wystąpienie przepływu pracy zostało ukończone w stanu Canceled.</span><span class="sxs-lookup"><span data-stu-id="4af10-113">Indicates a workflow instance has completed in the Canceled state.</span></span>  
  
## <a name="message"></a><span data-ttu-id="4af10-114">Komunikat</span><span class="sxs-lookup"><span data-stu-id="4af10-114">Message</span></span>  
 <span data-ttu-id="4af10-115">WorkflowInstance Id: "%1" została ukończona w stanu Canceled.</span><span class="sxs-lookup"><span data-stu-id="4af10-115">WorkflowInstance Id: '%1' has completed in the Canceled state.</span></span>  
  
## <a name="details"></a><span data-ttu-id="4af10-116">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="4af10-116">Details</span></span>  
  
|<span data-ttu-id="4af10-117">Nazwa elementu danych</span><span class="sxs-lookup"><span data-stu-id="4af10-117">Data Item Name</span></span>|<span data-ttu-id="4af10-118">Typ elementu danych</span><span class="sxs-lookup"><span data-stu-id="4af10-118">Data Item Type</span></span>|<span data-ttu-id="4af10-119">Opis</span><span class="sxs-lookup"><span data-stu-id="4af10-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="4af10-120">WorkflowInstanceId</span><span class="sxs-lookup"><span data-stu-id="4af10-120">WorkflowInstanceId</span></span>|`xs:string`|<span data-ttu-id="4af10-121">Identyfikator wystąpienia przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="4af10-121">The instance id for the workflow</span></span>|  
|<span data-ttu-id="4af10-122">AppDomain</span><span class="sxs-lookup"><span data-stu-id="4af10-122">AppDomain</span></span>|`xs:string`|<span data-ttu-id="4af10-123">Ciąg zwracany przez AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="4af10-123">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
