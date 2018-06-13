---
title: 1033 - StartRuntimeWorkItem
ms.date: 03/30/2017
ms.assetid: 172b5346-9f3b-46ae-bc06-39872022376a
ms.openlocfilehash: c7192ed7c5fb43fe6f65b47b8cebde3cf4aed32c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33510069"
---
# <a name="1033---startruntimeworkitem"></a><span data-ttu-id="48d0f-102">1033 - StartRuntimeWorkItem</span><span class="sxs-lookup"><span data-stu-id="48d0f-102">1033 - StartRuntimeWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="48d0f-103">Właściwości</span><span class="sxs-lookup"><span data-stu-id="48d0f-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="48d0f-104">ID</span><span class="sxs-lookup"><span data-stu-id="48d0f-104">ID</span></span>|<span data-ttu-id="48d0f-105">1033</span><span class="sxs-lookup"><span data-stu-id="48d0f-105">1033</span></span>|  
|<span data-ttu-id="48d0f-106">Słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="48d0f-106">Keywords</span></span>|<span data-ttu-id="48d0f-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="48d0f-107">WFRuntime</span></span>|  
|<span data-ttu-id="48d0f-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="48d0f-108">Level</span></span>|<span data-ttu-id="48d0f-109">Pełny</span><span class="sxs-lookup"><span data-stu-id="48d0f-109">Verbose</span></span>|  
|<span data-ttu-id="48d0f-110">Kanał</span><span class="sxs-lookup"><span data-stu-id="48d0f-110">Channel</span></span>|<span data-ttu-id="48d0f-111">Microsoft-Windows aplikacji debugowania serwera — aplikacje</span><span class="sxs-lookup"><span data-stu-id="48d0f-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="48d0f-112">Opis</span><span class="sxs-lookup"><span data-stu-id="48d0f-112">Description</span></span>  
 <span data-ttu-id="48d0f-113">Wskazuje, że RuntimeWorkItem jest rozpoczęcie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="48d0f-113">Indicates a RuntimeWorkItem is starting execution.</span></span>  
  
## <a name="message"></a><span data-ttu-id="48d0f-114">Komunikat</span><span class="sxs-lookup"><span data-stu-id="48d0f-114">Message</span></span>  
 <span data-ttu-id="48d0f-115">Rozpoczęcie wykonywania elementu roboczego środowiska wykonawczego dla działania %1, nazwa wyświetlana: %2, identyfikator wystąpienia: '%3'.</span><span class="sxs-lookup"><span data-stu-id="48d0f-115">Starting execution of a runtime work item for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="48d0f-116">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="48d0f-116">Details</span></span>  
  
|<span data-ttu-id="48d0f-117">Nazwa elementu danych</span><span class="sxs-lookup"><span data-stu-id="48d0f-117">Data Item Name</span></span>|<span data-ttu-id="48d0f-118">Typ elementu danych</span><span class="sxs-lookup"><span data-stu-id="48d0f-118">Data Item Type</span></span>|<span data-ttu-id="48d0f-119">Opis</span><span class="sxs-lookup"><span data-stu-id="48d0f-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="48d0f-120">Działanie</span><span class="sxs-lookup"><span data-stu-id="48d0f-120">Activity</span></span>|<span data-ttu-id="48d0f-121">xs:String</span><span class="sxs-lookup"><span data-stu-id="48d0f-121">xs:string</span></span>|<span data-ttu-id="48d0f-122">Nazwa typu działania.</span><span class="sxs-lookup"><span data-stu-id="48d0f-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="48d0f-123">Nazwa wyświetlana</span><span class="sxs-lookup"><span data-stu-id="48d0f-123">DisplayName</span></span>|<span data-ttu-id="48d0f-124">xs:String</span><span class="sxs-lookup"><span data-stu-id="48d0f-124">xs:string</span></span>|<span data-ttu-id="48d0f-125">Nazwa wyświetlana działania.</span><span class="sxs-lookup"><span data-stu-id="48d0f-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="48d0f-126">Identyfikator wystąpienia</span><span class="sxs-lookup"><span data-stu-id="48d0f-126">InstanceId</span></span>|<span data-ttu-id="48d0f-127">xs:String</span><span class="sxs-lookup"><span data-stu-id="48d0f-127">xs:string</span></span>|<span data-ttu-id="48d0f-128">Identyfikator wystąpienia działania.</span><span class="sxs-lookup"><span data-stu-id="48d0f-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="48d0f-129">Domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="48d0f-129">AppDomain</span></span>|<span data-ttu-id="48d0f-130">xs:String</span><span class="sxs-lookup"><span data-stu-id="48d0f-130">xs:string</span></span>|<span data-ttu-id="48d0f-131">Długość ciągu zwróconego przez AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="48d0f-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
