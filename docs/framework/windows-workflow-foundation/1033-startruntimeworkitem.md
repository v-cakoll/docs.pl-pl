---
title: 1033 — StartRuntimeWorkItem
ms.date: 03/30/2017
ms.assetid: 172b5346-9f3b-46ae-bc06-39872022376a
ms.openlocfilehash: c7192ed7c5fb43fe6f65b47b8cebde3cf4aed32c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61924244"
---
# <a name="1033---startruntimeworkitem"></a><span data-ttu-id="e62ee-102">1033 — StartRuntimeWorkItem</span><span class="sxs-lookup"><span data-stu-id="e62ee-102">1033 - StartRuntimeWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="e62ee-103">Właściwości</span><span class="sxs-lookup"><span data-stu-id="e62ee-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="e62ee-104">Identyfikator</span><span class="sxs-lookup"><span data-stu-id="e62ee-104">ID</span></span>|<span data-ttu-id="e62ee-105">1033</span><span class="sxs-lookup"><span data-stu-id="e62ee-105">1033</span></span>|  
|<span data-ttu-id="e62ee-106">słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="e62ee-106">Keywords</span></span>|<span data-ttu-id="e62ee-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="e62ee-107">WFRuntime</span></span>|  
|<span data-ttu-id="e62ee-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="e62ee-108">Level</span></span>|<span data-ttu-id="e62ee-109">Pełny</span><span class="sxs-lookup"><span data-stu-id="e62ee-109">Verbose</span></span>|  
|<span data-ttu-id="e62ee-110">Kanał</span><span class="sxs-lookup"><span data-stu-id="e62ee-110">Channel</span></span>|<span data-ttu-id="e62ee-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="e62ee-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="e62ee-112">Opis</span><span class="sxs-lookup"><span data-stu-id="e62ee-112">Description</span></span>  
 <span data-ttu-id="e62ee-113">Wskazuje, że RuntimeWorkItem Trwa uruchamianie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="e62ee-113">Indicates a RuntimeWorkItem is starting execution.</span></span>  
  
## <a name="message"></a><span data-ttu-id="e62ee-114">Komunikat</span><span class="sxs-lookup"><span data-stu-id="e62ee-114">Message</span></span>  
 <span data-ttu-id="e62ee-115">Rozpoczynanie wykonywania elementu roboczego środowiska uruchomieniowego dla działania "%1", DisplayName: "%2", InstanceId: "%3".</span><span class="sxs-lookup"><span data-stu-id="e62ee-115">Starting execution of a runtime work item for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="e62ee-116">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="e62ee-116">Details</span></span>  
  
|<span data-ttu-id="e62ee-117">Nazwa elementu danych</span><span class="sxs-lookup"><span data-stu-id="e62ee-117">Data Item Name</span></span>|<span data-ttu-id="e62ee-118">Typ elementu danych</span><span class="sxs-lookup"><span data-stu-id="e62ee-118">Data Item Type</span></span>|<span data-ttu-id="e62ee-119">Opis</span><span class="sxs-lookup"><span data-stu-id="e62ee-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="e62ee-120">Działanie</span><span class="sxs-lookup"><span data-stu-id="e62ee-120">Activity</span></span>|<span data-ttu-id="e62ee-121">xs:String</span><span class="sxs-lookup"><span data-stu-id="e62ee-121">xs:string</span></span>|<span data-ttu-id="e62ee-122">Nazwa typu działania.</span><span class="sxs-lookup"><span data-stu-id="e62ee-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="e62ee-123">Nazwa wyświetlana</span><span class="sxs-lookup"><span data-stu-id="e62ee-123">DisplayName</span></span>|<span data-ttu-id="e62ee-124">xs:String</span><span class="sxs-lookup"><span data-stu-id="e62ee-124">xs:string</span></span>|<span data-ttu-id="e62ee-125">Nazwa wyświetlana działania.</span><span class="sxs-lookup"><span data-stu-id="e62ee-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="e62ee-126">InstanceId</span><span class="sxs-lookup"><span data-stu-id="e62ee-126">InstanceId</span></span>|<span data-ttu-id="e62ee-127">xs:String</span><span class="sxs-lookup"><span data-stu-id="e62ee-127">xs:string</span></span>|<span data-ttu-id="e62ee-128">Identyfikator wystąpienia działania.</span><span class="sxs-lookup"><span data-stu-id="e62ee-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="e62ee-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="e62ee-129">AppDomain</span></span>|<span data-ttu-id="e62ee-130">xs:String</span><span class="sxs-lookup"><span data-stu-id="e62ee-130">xs:string</span></span>|<span data-ttu-id="e62ee-131">Ciąg zwracany przez AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="e62ee-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
