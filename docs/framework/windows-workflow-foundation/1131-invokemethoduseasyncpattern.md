---
title: 1131 - InvokeMethodUseAsyncPattern
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: eca50fa7-5276-4759-ad1c-e490b9bd1f82
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: db529ed413d70165c7813e23ce8f164262c8e16b
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="1131---invokemethoduseasyncpattern"></a><span data-ttu-id="f847a-102">1131 - InvokeMethodUseAsyncPattern</span><span class="sxs-lookup"><span data-stu-id="f847a-102">1131 - InvokeMethodUseAsyncPattern</span></span>
## <a name="properties"></a><span data-ttu-id="f847a-103">Właściwości</span><span class="sxs-lookup"><span data-stu-id="f847a-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="f847a-104">ID</span><span class="sxs-lookup"><span data-stu-id="f847a-104">ID</span></span>|<span data-ttu-id="f847a-105">1131</span><span class="sxs-lookup"><span data-stu-id="f847a-105">1131</span></span>|  
|<span data-ttu-id="f847a-106">Słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="f847a-106">Keywords</span></span>|<span data-ttu-id="f847a-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="f847a-107">WFRuntime</span></span>|  
|<span data-ttu-id="f847a-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="f847a-108">Level</span></span>|<span data-ttu-id="f847a-109">Informacje</span><span class="sxs-lookup"><span data-stu-id="f847a-109">Information</span></span>|  
|<span data-ttu-id="f847a-110">Kanał</span><span class="sxs-lookup"><span data-stu-id="f847a-110">Channel</span></span>|<span data-ttu-id="f847a-111">Microsoft-Windows aplikacji debugowania serwera — aplikacje</span><span class="sxs-lookup"><span data-stu-id="f847a-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="f847a-112">Opis</span><span class="sxs-lookup"><span data-stu-id="f847a-112">Description</span></span>  
 <span data-ttu-id="f847a-113">Podczas wykonywania kroku CacheMetadata działanie InvokeMethod wskazuje, że jest on używa wzorca asynchronicznego podczas wywoływania metody.</span><span class="sxs-lookup"><span data-stu-id="f847a-113">During CacheMetadata step, InvokeMethod activity indicates that it is using the async pattern when invoking the method.</span></span>  
  
## <a name="message"></a><span data-ttu-id="f847a-114">Komunikat</span><span class="sxs-lookup"><span data-stu-id="f847a-114">Message</span></span>  
 <span data-ttu-id="f847a-115">InvokeMethod "%1" — metoda korzysta ze wzorca asynchronicznego "%2" i "%3".</span><span class="sxs-lookup"><span data-stu-id="f847a-115">InvokeMethod '%1' - method uses asynchronous pattern of '%2' and '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="f847a-116">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="f847a-116">Details</span></span>  
  
|<span data-ttu-id="f847a-117">Nazwa elementu danych</span><span class="sxs-lookup"><span data-stu-id="f847a-117">Data Item Name</span></span>|<span data-ttu-id="f847a-118">Typ elementu danych</span><span class="sxs-lookup"><span data-stu-id="f847a-118">Data Item Type</span></span>|<span data-ttu-id="f847a-119">Opis</span><span class="sxs-lookup"><span data-stu-id="f847a-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="f847a-120">InvokeMethod</span><span class="sxs-lookup"><span data-stu-id="f847a-120">InvokeMethod</span></span>|<span data-ttu-id="f847a-121">xs:String</span><span class="sxs-lookup"><span data-stu-id="f847a-121">xs:string</span></span>|<span data-ttu-id="f847a-122">Nazwa wyświetlana InvokeMethod działania.</span><span class="sxs-lookup"><span data-stu-id="f847a-122">The display name of the InvokeMethod activity.</span></span>|  
|<span data-ttu-id="f847a-123">BeginMethod</span><span class="sxs-lookup"><span data-stu-id="f847a-123">BeginMethod</span></span>|<span data-ttu-id="f847a-124">xs:String</span><span class="sxs-lookup"><span data-stu-id="f847a-124">xs:string</span></span>|<span data-ttu-id="f847a-125">Nazwa metody begin.</span><span class="sxs-lookup"><span data-stu-id="f847a-125">The name of the begin method.</span></span>|  
|<span data-ttu-id="f847a-126">EndMethod</span><span class="sxs-lookup"><span data-stu-id="f847a-126">EndMethod</span></span>|<span data-ttu-id="f847a-127">xs:String</span><span class="sxs-lookup"><span data-stu-id="f847a-127">xs:string</span></span>|<span data-ttu-id="f847a-128">Nazwa metody end.</span><span class="sxs-lookup"><span data-stu-id="f847a-128">The name of the end method.</span></span>|  
|<span data-ttu-id="f847a-129">Domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="f847a-129">AppDomain</span></span>|<span data-ttu-id="f847a-130">xs:String</span><span class="sxs-lookup"><span data-stu-id="f847a-130">xs:string</span></span>|<span data-ttu-id="f847a-131">Długość ciągu zwróconego przez AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="f847a-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
