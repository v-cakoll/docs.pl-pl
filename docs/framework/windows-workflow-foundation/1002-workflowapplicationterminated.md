---
title: 1002 — WorkflowApplicationTerminated
ms.date: 03/30/2017
ms.assetid: 4e8b111f-79dc-4898-bb4a-e9b36f69420f
ms.openlocfilehash: 01c9aba6e863e07a1a999a28fccefbab95a34d5b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62008658"
---
# <a name="1002---workflowapplicationterminated"></a><span data-ttu-id="e6695-102">1002 — WorkflowApplicationTerminated</span><span class="sxs-lookup"><span data-stu-id="e6695-102">1002 - WorkflowApplicationTerminated</span></span>
## <a name="properties"></a><span data-ttu-id="e6695-103">Właściwości</span><span class="sxs-lookup"><span data-stu-id="e6695-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="e6695-104">Identyfikator</span><span class="sxs-lookup"><span data-stu-id="e6695-104">ID</span></span>|<span data-ttu-id="e6695-105">1002</span><span class="sxs-lookup"><span data-stu-id="e6695-105">1002</span></span>|  
|<span data-ttu-id="e6695-106">słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="e6695-106">Keywords</span></span>|<span data-ttu-id="e6695-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="e6695-107">WFRuntime</span></span>|  
|<span data-ttu-id="e6695-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="e6695-108">Level</span></span>|<span data-ttu-id="e6695-109">Informacje</span><span class="sxs-lookup"><span data-stu-id="e6695-109">Information</span></span>|  
|<span data-ttu-id="e6695-110">Kanał</span><span class="sxs-lookup"><span data-stu-id="e6695-110">Channel</span></span>|<span data-ttu-id="e6695-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="e6695-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="e6695-112">Opis</span><span class="sxs-lookup"><span data-stu-id="e6695-112">Description</span></span>  
 <span data-ttu-id="e6695-113">Wskazuje, że aplikacja przepływu pracy został zakończony w stanie Faulted z powodu wyjątku.</span><span class="sxs-lookup"><span data-stu-id="e6695-113">Indicates a workflow application has terminated in the Faulted state with an exception.</span></span>  
  
## <a name="message"></a><span data-ttu-id="e6695-114">Komunikat</span><span class="sxs-lookup"><span data-stu-id="e6695-114">Message</span></span>  
 <span data-ttu-id="e6695-115">Identyfikator WorkflowApplication: "%1" została zakończona.</span><span class="sxs-lookup"><span data-stu-id="e6695-115">WorkflowApplication Id: '%1' was terminated.</span></span> <span data-ttu-id="e6695-116">Ukończono się w stanie Faulted z powodu wyjątku.</span><span class="sxs-lookup"><span data-stu-id="e6695-116">It has completed in the Faulted state with an exception.</span></span>  
  
## <a name="details"></a><span data-ttu-id="e6695-117">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="e6695-117">Details</span></span>  
  
|<span data-ttu-id="e6695-118">Nazwa elementu danych</span><span class="sxs-lookup"><span data-stu-id="e6695-118">Data Item Name</span></span>|<span data-ttu-id="e6695-119">Typ elementu danych</span><span class="sxs-lookup"><span data-stu-id="e6695-119">Data Item Type</span></span>|<span data-ttu-id="e6695-120">Opis</span><span class="sxs-lookup"><span data-stu-id="e6695-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="e6695-121">WorkflowApplicationId</span><span class="sxs-lookup"><span data-stu-id="e6695-121">WorkflowApplicationId</span></span>|`xs:string`|<span data-ttu-id="e6695-122">Identyfikator aplikacji przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="e6695-122">The workflow application id</span></span>|  
|<span data-ttu-id="e6695-123">Wyjątek</span><span class="sxs-lookup"><span data-stu-id="e6695-123">Exception</span></span>|`xs:string`|<span data-ttu-id="e6695-124">Szczegóły wyjątku, dla wyjątku</span><span class="sxs-lookup"><span data-stu-id="e6695-124">The exception details for the exception</span></span>|  
|<span data-ttu-id="e6695-125">AppDomain</span><span class="sxs-lookup"><span data-stu-id="e6695-125">AppDomain</span></span>|`xs:string`|<span data-ttu-id="e6695-126">Ciąg zwracany przez AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="e6695-126">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
