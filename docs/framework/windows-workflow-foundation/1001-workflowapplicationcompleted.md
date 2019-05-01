---
title: 1001 — WorkflowApplicationCompleted
ms.date: 03/30/2017
ms.assetid: 7a2ab59a-cf66-437a-b01e-f8f7268a3f7a
ms.openlocfilehash: 430174b96a499fff7e0156327bb15e066ce2ca36
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62008645"
---
# <a name="1001---workflowapplicationcompleted"></a><span data-ttu-id="bf734-102">1001 — WorkflowApplicationCompleted</span><span class="sxs-lookup"><span data-stu-id="bf734-102">1001 - WorkflowApplicationCompleted</span></span>
## <a name="properties"></a><span data-ttu-id="bf734-103">Właściwości</span><span class="sxs-lookup"><span data-stu-id="bf734-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="bf734-104">Identyfikator</span><span class="sxs-lookup"><span data-stu-id="bf734-104">ID</span></span>|<span data-ttu-id="bf734-105">1001</span><span class="sxs-lookup"><span data-stu-id="bf734-105">1001</span></span>|  
|<span data-ttu-id="bf734-106">słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="bf734-106">Keywords</span></span>|<span data-ttu-id="bf734-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="bf734-107">WFRuntime</span></span>|  
|<span data-ttu-id="bf734-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="bf734-108">Level</span></span>|<span data-ttu-id="bf734-109">Informacje</span><span class="sxs-lookup"><span data-stu-id="bf734-109">Information</span></span>|  
|<span data-ttu-id="bf734-110">Kanał</span><span class="sxs-lookup"><span data-stu-id="bf734-110">Channel</span></span>|<span data-ttu-id="bf734-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="bf734-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="bf734-112">Opis</span><span class="sxs-lookup"><span data-stu-id="bf734-112">Description</span></span>  
 <span data-ttu-id="bf734-113">Wskazuje, że aplikacja przepływu pracy zostało ukończone w stanie zamkniętym.</span><span class="sxs-lookup"><span data-stu-id="bf734-113">Indicates a workflow application has completed in the Closed state.</span></span>  
  
## <a name="message"></a><span data-ttu-id="bf734-114">Komunikat</span><span class="sxs-lookup"><span data-stu-id="bf734-114">Message</span></span>  
 <span data-ttu-id="bf734-115">WorkflowInstance Id: "%1" została zakończona w stanie zamkniętym.</span><span class="sxs-lookup"><span data-stu-id="bf734-115">WorkflowInstance Id: '%1' has completed in the Closed state.</span></span>  
  
## <a name="details"></a><span data-ttu-id="bf734-116">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="bf734-116">Details</span></span>  
  
|<span data-ttu-id="bf734-117">Nazwa elementu danych</span><span class="sxs-lookup"><span data-stu-id="bf734-117">Data Item Name</span></span>|<span data-ttu-id="bf734-118">Typ elementu danych</span><span class="sxs-lookup"><span data-stu-id="bf734-118">Data Item Type</span></span>|<span data-ttu-id="bf734-119">Opis</span><span class="sxs-lookup"><span data-stu-id="bf734-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="bf734-120">WorkflowInstanceId</span><span class="sxs-lookup"><span data-stu-id="bf734-120">WorkflowInstanceId</span></span>|`xs:string`|<span data-ttu-id="bf734-121">Identyfikator wystąpienia przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="bf734-121">The instance id for the workflow</span></span>|  
|<span data-ttu-id="bf734-122">AppDomain</span><span class="sxs-lookup"><span data-stu-id="bf734-122">AppDomain</span></span>|`xs:string`|<span data-ttu-id="bf734-123">Ciąg zwracany przez AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="bf734-123">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
