---
title: "1036 — RuntimeTransactionCompletionRequested"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d36b9f44-7c0f-4083-9d3a-9034dd2b98de
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 91fcac0bdfe885051941d100f1a2c131c547f19e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="1036---runtimetransactioncompletionrequested"></a><span data-ttu-id="fafe7-102">1036 — RuntimeTransactionCompletionRequested</span><span class="sxs-lookup"><span data-stu-id="fafe7-102">1036 - RuntimeTransactionCompletionRequested</span></span>
## <a name="properties"></a><span data-ttu-id="fafe7-103">Właściwości</span><span class="sxs-lookup"><span data-stu-id="fafe7-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="fafe7-104">ID</span><span class="sxs-lookup"><span data-stu-id="fafe7-104">ID</span></span>|<span data-ttu-id="fafe7-105">1036</span><span class="sxs-lookup"><span data-stu-id="fafe7-105">1036</span></span>|  
|<span data-ttu-id="fafe7-106">Słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="fafe7-106">Keywords</span></span>|<span data-ttu-id="fafe7-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="fafe7-107">WFRuntime</span></span>|  
|<span data-ttu-id="fafe7-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="fafe7-108">Level</span></span>|<span data-ttu-id="fafe7-109">Pełny</span><span class="sxs-lookup"><span data-stu-id="fafe7-109">Verbose</span></span>|  
|<span data-ttu-id="fafe7-110">Kanał</span><span class="sxs-lookup"><span data-stu-id="fafe7-110">Channel</span></span>|<span data-ttu-id="fafe7-111">Microsoft-Windows aplikacji debugowania serwera — aplikacje</span><span class="sxs-lookup"><span data-stu-id="fafe7-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="fafe7-112">Opis</span><span class="sxs-lookup"><span data-stu-id="fafe7-112">Description</span></span>  
 <span data-ttu-id="fafe7-113">Wskazuje, że działanie zaplanowało wykonanie transakcji czasu wykonywania.</span><span class="sxs-lookup"><span data-stu-id="fafe7-113">Indicates an activity has scheduled the completion of the runtime transaction.</span></span>  
  
## <a name="message"></a><span data-ttu-id="fafe7-114">Komunikat</span><span class="sxs-lookup"><span data-stu-id="fafe7-114">Message</span></span>  
 <span data-ttu-id="fafe7-115">Działanie "%1", nazwa wyświetlana: %2, identyfikator wystąpienia: '%3', zaplanowało wykonanie transakcji czasu wykonywania.</span><span class="sxs-lookup"><span data-stu-id="fafe7-115">Activity '%1', DisplayName: '%2', InstanceId: '%3' has scheduled completion of the runtime transaction.</span></span>  
  
## <a name="details"></a><span data-ttu-id="fafe7-116">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="fafe7-116">Details</span></span>  
  
|<span data-ttu-id="fafe7-117">Nazwa elementu danych</span><span class="sxs-lookup"><span data-stu-id="fafe7-117">Data Item Name</span></span>|<span data-ttu-id="fafe7-118">Typ elementu danych</span><span class="sxs-lookup"><span data-stu-id="fafe7-118">Data Item Type</span></span>|<span data-ttu-id="fafe7-119">Opis</span><span class="sxs-lookup"><span data-stu-id="fafe7-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="fafe7-120">Działanie</span><span class="sxs-lookup"><span data-stu-id="fafe7-120">Activity</span></span>|<span data-ttu-id="fafe7-121">xs:String</span><span class="sxs-lookup"><span data-stu-id="fafe7-121">xs:string</span></span>|<span data-ttu-id="fafe7-122">Nazwa typu działania.</span><span class="sxs-lookup"><span data-stu-id="fafe7-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="fafe7-123">Nazwa wyświetlana</span><span class="sxs-lookup"><span data-stu-id="fafe7-123">DisplayName</span></span>|<span data-ttu-id="fafe7-124">xs:String</span><span class="sxs-lookup"><span data-stu-id="fafe7-124">xs:string</span></span>|<span data-ttu-id="fafe7-125">Nazwa wyświetlana działania.</span><span class="sxs-lookup"><span data-stu-id="fafe7-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="fafe7-126">Identyfikator wystąpienia</span><span class="sxs-lookup"><span data-stu-id="fafe7-126">InstanceId</span></span>|<span data-ttu-id="fafe7-127">xs:String</span><span class="sxs-lookup"><span data-stu-id="fafe7-127">xs:string</span></span>|<span data-ttu-id="fafe7-128">Identyfikator wystąpienia działania.</span><span class="sxs-lookup"><span data-stu-id="fafe7-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="fafe7-129">Domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="fafe7-129">AppDomain</span></span>|<span data-ttu-id="fafe7-130">xs:String</span><span class="sxs-lookup"><span data-stu-id="fafe7-130">xs:string</span></span>|<span data-ttu-id="fafe7-131">Długość ciągu zwróconego przez AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="fafe7-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
