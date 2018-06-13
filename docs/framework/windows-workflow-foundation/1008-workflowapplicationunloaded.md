---
title: 1008 - WorkflowApplicationUnloaded
ms.date: 03/30/2017
ms.assetid: a605b780-4a7e-43ab-92e7-0a3b01d053b0
ms.openlocfilehash: c7c22e6e4270a3fc3e91e1711db5da9bd5a378b9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33509564"
---
# <a name="1008---workflowapplicationunloaded"></a><span data-ttu-id="ffb4f-102">1008 - WorkflowApplicationUnloaded</span><span class="sxs-lookup"><span data-stu-id="ffb4f-102">1008 - WorkflowApplicationUnloaded</span></span>
## <a name="properties"></a><span data-ttu-id="ffb4f-103">Właściwości</span><span class="sxs-lookup"><span data-stu-id="ffb4f-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="ffb4f-104">ID</span><span class="sxs-lookup"><span data-stu-id="ffb4f-104">ID</span></span>|<span data-ttu-id="ffb4f-105">1008</span><span class="sxs-lookup"><span data-stu-id="ffb4f-105">1008</span></span>|  
|<span data-ttu-id="ffb4f-106">Słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="ffb4f-106">Keywords</span></span>|<span data-ttu-id="ffb4f-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="ffb4f-107">WFRuntime</span></span>|  
|<span data-ttu-id="ffb4f-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="ffb4f-108">Level</span></span>|<span data-ttu-id="ffb4f-109">Informacje</span><span class="sxs-lookup"><span data-stu-id="ffb4f-109">Information</span></span>|  
|<span data-ttu-id="ffb4f-110">Kanał</span><span class="sxs-lookup"><span data-stu-id="ffb4f-110">Channel</span></span>|<span data-ttu-id="ffb4f-111">Microsoft-Windows aplikacji debugowania serwera — aplikacje</span><span class="sxs-lookup"><span data-stu-id="ffb4f-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="ffb4f-112">Opis</span><span class="sxs-lookup"><span data-stu-id="ffb4f-112">Description</span></span>  
 <span data-ttu-id="ffb4f-113">Wskazuje, że aplikacja przepływu pracy został zwolniony.</span><span class="sxs-lookup"><span data-stu-id="ffb4f-113">Indicates a workflow application has unloaded.</span></span>  
  
## <a name="message"></a><span data-ttu-id="ffb4f-114">Komunikat</span><span class="sxs-lookup"><span data-stu-id="ffb4f-114">Message</span></span>  
 <span data-ttu-id="ffb4f-115">Obiekt WorkflowInstance o identyfikatorze: '%1' został Unloaded.</span><span class="sxs-lookup"><span data-stu-id="ffb4f-115">WorkflowInstance Id: '%1' was Unloaded.</span></span>  
  
## <a name="details"></a><span data-ttu-id="ffb4f-116">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="ffb4f-116">Details</span></span>  
  
|<span data-ttu-id="ffb4f-117">Nazwa elementu danych</span><span class="sxs-lookup"><span data-stu-id="ffb4f-117">Data Item Name</span></span>|<span data-ttu-id="ffb4f-118">Typ elementu danych</span><span class="sxs-lookup"><span data-stu-id="ffb4f-118">Data Item Type</span></span>|<span data-ttu-id="ffb4f-119">Opis</span><span class="sxs-lookup"><span data-stu-id="ffb4f-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="ffb4f-120">WorkflowInstanceId</span><span class="sxs-lookup"><span data-stu-id="ffb4f-120">WorkflowInstanceId</span></span>|`xs:string`|<span data-ttu-id="ffb4f-121">Identyfikator wystąpienia przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="ffb4f-121">The instance id for the workflow</span></span>|  
|<span data-ttu-id="ffb4f-122">Domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="ffb4f-122">AppDomain</span></span>|`xs:string`|<span data-ttu-id="ffb4f-123">Długość ciągu zwróconego przez AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="ffb4f-123">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
