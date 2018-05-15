---
title: 1004 - WorkflowInstanceAborted
ms.date: 03/30/2017
ms.assetid: edb9ab8c-0b9a-488d-aa96-9c8c7984b53c
ms.openlocfilehash: d1eaf3cf107a6b5e244cc2d9372ee68d387ef6c3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="1004---workflowinstanceaborted"></a><span data-ttu-id="ff7d5-102">1004 - WorkflowInstanceAborted</span><span class="sxs-lookup"><span data-stu-id="ff7d5-102">1004 - WorkflowInstanceAborted</span></span>
## <a name="properties"></a><span data-ttu-id="ff7d5-103">Właściwości</span><span class="sxs-lookup"><span data-stu-id="ff7d5-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="ff7d5-104">ID</span><span class="sxs-lookup"><span data-stu-id="ff7d5-104">ID</span></span>|<span data-ttu-id="ff7d5-105">1004</span><span class="sxs-lookup"><span data-stu-id="ff7d5-105">1004</span></span>|  
|<span data-ttu-id="ff7d5-106">Słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="ff7d5-106">Keywords</span></span>|<span data-ttu-id="ff7d5-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="ff7d5-107">WFRuntime</span></span>|  
|<span data-ttu-id="ff7d5-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="ff7d5-108">Level</span></span>|<span data-ttu-id="ff7d5-109">Informacje</span><span class="sxs-lookup"><span data-stu-id="ff7d5-109">Information</span></span>|  
|<span data-ttu-id="ff7d5-110">Kanał</span><span class="sxs-lookup"><span data-stu-id="ff7d5-110">Channel</span></span>|<span data-ttu-id="ff7d5-111">Microsoft-Windows aplikacji debugowania serwera — aplikacje</span><span class="sxs-lookup"><span data-stu-id="ff7d5-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="ff7d5-112">Opis</span><span class="sxs-lookup"><span data-stu-id="ff7d5-112">Description</span></span>  
 <span data-ttu-id="ff7d5-113">Wskazuje, że wystąpienie worfklow została przerwana z powodu wyjątku.</span><span class="sxs-lookup"><span data-stu-id="ff7d5-113">Indicates a worfklow instance has aborted with an exception.</span></span>  
  
## <a name="message"></a><span data-ttu-id="ff7d5-114">Komunikat</span><span class="sxs-lookup"><span data-stu-id="ff7d5-114">Message</span></span>  
 <span data-ttu-id="ff7d5-115">Obiekt WorkflowInstance o identyfikatorze: "%1" zostało przerwane z powodu wyjątku.</span><span class="sxs-lookup"><span data-stu-id="ff7d5-115">WorkflowInstance Id: '%1' was aborted with an exception.</span></span>  
  
## <a name="details"></a><span data-ttu-id="ff7d5-116">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="ff7d5-116">Details</span></span>  
  
|<span data-ttu-id="ff7d5-117">Nazwa elementu danych</span><span class="sxs-lookup"><span data-stu-id="ff7d5-117">Data Item Name</span></span>|<span data-ttu-id="ff7d5-118">Typ elementu danych</span><span class="sxs-lookup"><span data-stu-id="ff7d5-118">Data Item Type</span></span>|<span data-ttu-id="ff7d5-119">Opis</span><span class="sxs-lookup"><span data-stu-id="ff7d5-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="ff7d5-120">WorkflowInstanceId</span><span class="sxs-lookup"><span data-stu-id="ff7d5-120">WorkflowInstanceId</span></span>|`xs:string`|<span data-ttu-id="ff7d5-121">Identyfikator wystąpienia przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="ff7d5-121">The instance id for the workflow</span></span>|  
|<span data-ttu-id="ff7d5-122">Wyjątek</span><span class="sxs-lookup"><span data-stu-id="ff7d5-122">Exception</span></span>|`xs:string`|<span data-ttu-id="ff7d5-123">Szczegóły wyjątku dla wyjątku</span><span class="sxs-lookup"><span data-stu-id="ff7d5-123">The exception details for the exception</span></span>|  
|<span data-ttu-id="ff7d5-124">Domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="ff7d5-124">AppDomain</span></span>|`xs:string`|<span data-ttu-id="ff7d5-125">Długość ciągu zwróconego przez AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="ff7d5-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
