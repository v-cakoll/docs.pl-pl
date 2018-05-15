---
title: 1001 - WorkflowApplicationCompleted
ms.date: 03/30/2017
ms.assetid: 7a2ab59a-cf66-437a-b01e-f8f7268a3f7a
ms.openlocfilehash: 430174b96a499fff7e0156327bb15e066ce2ca36
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="1001---workflowapplicationcompleted"></a><span data-ttu-id="9d617-102">1001 - WorkflowApplicationCompleted</span><span class="sxs-lookup"><span data-stu-id="9d617-102">1001 - WorkflowApplicationCompleted</span></span>
## <a name="properties"></a><span data-ttu-id="9d617-103">Właściwości</span><span class="sxs-lookup"><span data-stu-id="9d617-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="9d617-104">ID</span><span class="sxs-lookup"><span data-stu-id="9d617-104">ID</span></span>|<span data-ttu-id="9d617-105">1001</span><span class="sxs-lookup"><span data-stu-id="9d617-105">1001</span></span>|  
|<span data-ttu-id="9d617-106">Słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="9d617-106">Keywords</span></span>|<span data-ttu-id="9d617-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="9d617-107">WFRuntime</span></span>|  
|<span data-ttu-id="9d617-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="9d617-108">Level</span></span>|<span data-ttu-id="9d617-109">Informacje</span><span class="sxs-lookup"><span data-stu-id="9d617-109">Information</span></span>|  
|<span data-ttu-id="9d617-110">Kanał</span><span class="sxs-lookup"><span data-stu-id="9d617-110">Channel</span></span>|<span data-ttu-id="9d617-111">Microsoft-Windows aplikacji debugowania serwera — aplikacje</span><span class="sxs-lookup"><span data-stu-id="9d617-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="9d617-112">Opis</span><span class="sxs-lookup"><span data-stu-id="9d617-112">Description</span></span>  
 <span data-ttu-id="9d617-113">Wskazuje, że aplikacja przepływu pracy zostało ukończone w stanie zamkniętym.</span><span class="sxs-lookup"><span data-stu-id="9d617-113">Indicates a workflow application has completed in the Closed state.</span></span>  
  
## <a name="message"></a><span data-ttu-id="9d617-114">Komunikat</span><span class="sxs-lookup"><span data-stu-id="9d617-114">Message</span></span>  
 <span data-ttu-id="9d617-115">Obiekt WorkflowInstance o identyfikatorze: "%1" została ukończona w stanie zamkniętym.</span><span class="sxs-lookup"><span data-stu-id="9d617-115">WorkflowInstance Id: '%1' has completed in the Closed state.</span></span>  
  
## <a name="details"></a><span data-ttu-id="9d617-116">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="9d617-116">Details</span></span>  
  
|<span data-ttu-id="9d617-117">Nazwa elementu danych</span><span class="sxs-lookup"><span data-stu-id="9d617-117">Data Item Name</span></span>|<span data-ttu-id="9d617-118">Typ elementu danych</span><span class="sxs-lookup"><span data-stu-id="9d617-118">Data Item Type</span></span>|<span data-ttu-id="9d617-119">Opis</span><span class="sxs-lookup"><span data-stu-id="9d617-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="9d617-120">WorkflowInstanceId</span><span class="sxs-lookup"><span data-stu-id="9d617-120">WorkflowInstanceId</span></span>|`xs:string`|<span data-ttu-id="9d617-121">Identyfikator wystąpienia przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="9d617-121">The instance id for the workflow</span></span>|  
|<span data-ttu-id="9d617-122">Domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="9d617-122">AppDomain</span></span>|`xs:string`|<span data-ttu-id="9d617-123">Długość ciągu zwróconego przez AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="9d617-123">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
