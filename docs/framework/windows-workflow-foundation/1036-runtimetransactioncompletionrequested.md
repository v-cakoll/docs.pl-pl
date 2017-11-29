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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 4f497d777221a98b38603b2ced29342651b1020b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="1036---runtimetransactioncompletionrequested"></a><span data-ttu-id="be02e-102">1036 — RuntimeTransactionCompletionRequested</span><span class="sxs-lookup"><span data-stu-id="be02e-102">1036 - RuntimeTransactionCompletionRequested</span></span>
## <a name="properties"></a><span data-ttu-id="be02e-103">Właściwości</span><span class="sxs-lookup"><span data-stu-id="be02e-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="be02e-104">ID</span><span class="sxs-lookup"><span data-stu-id="be02e-104">ID</span></span>|<span data-ttu-id="be02e-105">1036</span><span class="sxs-lookup"><span data-stu-id="be02e-105">1036</span></span>|  
|<span data-ttu-id="be02e-106">Słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="be02e-106">Keywords</span></span>|<span data-ttu-id="be02e-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="be02e-107">WFRuntime</span></span>|  
|<span data-ttu-id="be02e-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="be02e-108">Level</span></span>|<span data-ttu-id="be02e-109">Pełny</span><span class="sxs-lookup"><span data-stu-id="be02e-109">Verbose</span></span>|  
|<span data-ttu-id="be02e-110">Kanał</span><span class="sxs-lookup"><span data-stu-id="be02e-110">Channel</span></span>|<span data-ttu-id="be02e-111">Microsoft-Windows aplikacji debugowania serwera — aplikacje</span><span class="sxs-lookup"><span data-stu-id="be02e-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="be02e-112">Opis</span><span class="sxs-lookup"><span data-stu-id="be02e-112">Description</span></span>  
 <span data-ttu-id="be02e-113">Wskazuje, że działanie zaplanowało wykonanie transakcji czasu wykonywania.</span><span class="sxs-lookup"><span data-stu-id="be02e-113">Indicates an activity has scheduled the completion of the runtime transaction.</span></span>  
  
## <a name="message"></a><span data-ttu-id="be02e-114">Komunikat</span><span class="sxs-lookup"><span data-stu-id="be02e-114">Message</span></span>  
 <span data-ttu-id="be02e-115">Działanie "%1", nazwa wyświetlana: %2, identyfikator wystąpienia: '%3', zaplanowało wykonanie transakcji czasu wykonywania.</span><span class="sxs-lookup"><span data-stu-id="be02e-115">Activity '%1', DisplayName: '%2', InstanceId: '%3' has scheduled completion of the runtime transaction.</span></span>  
  
## <a name="details"></a><span data-ttu-id="be02e-116">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="be02e-116">Details</span></span>  
  
|<span data-ttu-id="be02e-117">Nazwa elementu danych</span><span class="sxs-lookup"><span data-stu-id="be02e-117">Data Item Name</span></span>|<span data-ttu-id="be02e-118">Typ elementu danych</span><span class="sxs-lookup"><span data-stu-id="be02e-118">Data Item Type</span></span>|<span data-ttu-id="be02e-119">Opis</span><span class="sxs-lookup"><span data-stu-id="be02e-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="be02e-120">Działanie</span><span class="sxs-lookup"><span data-stu-id="be02e-120">Activity</span></span>|<span data-ttu-id="be02e-121">xs:String</span><span class="sxs-lookup"><span data-stu-id="be02e-121">xs:string</span></span>|<span data-ttu-id="be02e-122">Nazwa typu działania.</span><span class="sxs-lookup"><span data-stu-id="be02e-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="be02e-123">Nazwa wyświetlana</span><span class="sxs-lookup"><span data-stu-id="be02e-123">DisplayName</span></span>|<span data-ttu-id="be02e-124">xs:String</span><span class="sxs-lookup"><span data-stu-id="be02e-124">xs:string</span></span>|<span data-ttu-id="be02e-125">Nazwa wyświetlana działania.</span><span class="sxs-lookup"><span data-stu-id="be02e-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="be02e-126">Identyfikator wystąpienia</span><span class="sxs-lookup"><span data-stu-id="be02e-126">InstanceId</span></span>|<span data-ttu-id="be02e-127">xs:String</span><span class="sxs-lookup"><span data-stu-id="be02e-127">xs:string</span></span>|<span data-ttu-id="be02e-128">Identyfikator wystąpienia działania.</span><span class="sxs-lookup"><span data-stu-id="be02e-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="be02e-129">Domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="be02e-129">AppDomain</span></span>|<span data-ttu-id="be02e-130">xs:String</span><span class="sxs-lookup"><span data-stu-id="be02e-130">xs:string</span></span>|<span data-ttu-id="be02e-131">Długość ciągu zwróconego przez AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="be02e-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
