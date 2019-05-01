---
title: 1008 — WorkflowApplicationUnloaded
ms.date: 03/30/2017
ms.assetid: a605b780-4a7e-43ab-92e7-0a3b01d053b0
ms.openlocfilehash: c7c22e6e4270a3fc3e91e1711db5da9bd5a378b9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61925232"
---
# <a name="1008---workflowapplicationunloaded"></a><span data-ttu-id="092f3-102">1008 — WorkflowApplicationUnloaded</span><span class="sxs-lookup"><span data-stu-id="092f3-102">1008 - WorkflowApplicationUnloaded</span></span>
## <a name="properties"></a><span data-ttu-id="092f3-103">Właściwości</span><span class="sxs-lookup"><span data-stu-id="092f3-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="092f3-104">Identyfikator</span><span class="sxs-lookup"><span data-stu-id="092f3-104">ID</span></span>|<span data-ttu-id="092f3-105">1008</span><span class="sxs-lookup"><span data-stu-id="092f3-105">1008</span></span>|  
|<span data-ttu-id="092f3-106">słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="092f3-106">Keywords</span></span>|<span data-ttu-id="092f3-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="092f3-107">WFRuntime</span></span>|  
|<span data-ttu-id="092f3-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="092f3-108">Level</span></span>|<span data-ttu-id="092f3-109">Informacje</span><span class="sxs-lookup"><span data-stu-id="092f3-109">Information</span></span>|  
|<span data-ttu-id="092f3-110">Kanał</span><span class="sxs-lookup"><span data-stu-id="092f3-110">Channel</span></span>|<span data-ttu-id="092f3-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="092f3-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="092f3-112">Opis</span><span class="sxs-lookup"><span data-stu-id="092f3-112">Description</span></span>  
 <span data-ttu-id="092f3-113">Wskazuje, że aplikacja przepływu pracy został zwolniony.</span><span class="sxs-lookup"><span data-stu-id="092f3-113">Indicates a workflow application has unloaded.</span></span>  
  
## <a name="message"></a><span data-ttu-id="092f3-114">Komunikat</span><span class="sxs-lookup"><span data-stu-id="092f3-114">Message</span></span>  
 <span data-ttu-id="092f3-115">WorkflowInstance Id: "%1" został Unloaded.</span><span class="sxs-lookup"><span data-stu-id="092f3-115">WorkflowInstance Id: '%1' was Unloaded.</span></span>  
  
## <a name="details"></a><span data-ttu-id="092f3-116">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="092f3-116">Details</span></span>  
  
|<span data-ttu-id="092f3-117">Nazwa elementu danych</span><span class="sxs-lookup"><span data-stu-id="092f3-117">Data Item Name</span></span>|<span data-ttu-id="092f3-118">Typ elementu danych</span><span class="sxs-lookup"><span data-stu-id="092f3-118">Data Item Type</span></span>|<span data-ttu-id="092f3-119">Opis</span><span class="sxs-lookup"><span data-stu-id="092f3-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="092f3-120">WorkflowInstanceId</span><span class="sxs-lookup"><span data-stu-id="092f3-120">WorkflowInstanceId</span></span>|`xs:string`|<span data-ttu-id="092f3-121">Identyfikator wystąpienia przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="092f3-121">The instance id for the workflow</span></span>|  
|<span data-ttu-id="092f3-122">AppDomain</span><span class="sxs-lookup"><span data-stu-id="092f3-122">AppDomain</span></span>|`xs:string`|<span data-ttu-id="092f3-123">Ciąg zwracany przez AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="092f3-123">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
