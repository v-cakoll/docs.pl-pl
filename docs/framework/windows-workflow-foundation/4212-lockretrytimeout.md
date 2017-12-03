---
title: 4212 - LockRetryTimeout
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d4ad415a-9871-49fc-85b8-8ee2ea149b1d
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: abe1f560cc984551f069a75873a7e5545aec03cf
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="4212---lockretrytimeout"></a><span data-ttu-id="83b1c-102">4212 - LockRetryTimeout</span><span class="sxs-lookup"><span data-stu-id="83b1c-102">4212 - LockRetryTimeout</span></span>
## <a name="properties"></a><span data-ttu-id="83b1c-103">Właściwości</span><span class="sxs-lookup"><span data-stu-id="83b1c-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="83b1c-104">ID</span><span class="sxs-lookup"><span data-stu-id="83b1c-104">ID</span></span>|<span data-ttu-id="83b1c-105">4212</span><span class="sxs-lookup"><span data-stu-id="83b1c-105">4212</span></span>|  
|<span data-ttu-id="83b1c-106">Słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="83b1c-106">Keywords</span></span>|<span data-ttu-id="83b1c-107">WFInstanceStore</span><span class="sxs-lookup"><span data-stu-id="83b1c-107">WFInstanceStore</span></span>|  
|<span data-ttu-id="83b1c-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="83b1c-108">Level</span></span>|<span data-ttu-id="83b1c-109">Ostrzeżenie</span><span class="sxs-lookup"><span data-stu-id="83b1c-109">Warning</span></span>|  
|<span data-ttu-id="83b1c-110">Kanał</span><span class="sxs-lookup"><span data-stu-id="83b1c-110">Channel</span></span>|<span data-ttu-id="83b1c-111">Microsoft-Windows aplikacji debugowania serwera — aplikacje</span><span class="sxs-lookup"><span data-stu-id="83b1c-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="83b1c-112">Opis</span><span class="sxs-lookup"><span data-stu-id="83b1c-112">Description</span></span>  
 <span data-ttu-id="83b1c-113">Dostawca SQL został przekroczony limit czasu próby uzyskania blokady wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="83b1c-113">SQL provider encountered a timeout trying to acquire the instance lock.</span></span>  
  
## <a name="message"></a><span data-ttu-id="83b1c-114">Komunikat</span><span class="sxs-lookup"><span data-stu-id="83b1c-114">Message</span></span>  
 <span data-ttu-id="83b1c-115">Limit czasu próby uzyskania blokady wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="83b1c-115">Timeout trying to acquire the instance lock.</span></span>  <span data-ttu-id="83b1c-116">Operacja nie została ukończona w ciągu przydzielonego limitu czasu równego %1.</span><span class="sxs-lookup"><span data-stu-id="83b1c-116">The operation did not complete within the allotted timeout of %1.</span></span> <span data-ttu-id="83b1c-117">Czas przydzielony na tę operację mógł stanowi część większego limitu czasu.</span><span class="sxs-lookup"><span data-stu-id="83b1c-117">The time allotted to this operation may have been a portion of a longer timeout.</span></span>  
  
## <a name="details"></a><span data-ttu-id="83b1c-118">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="83b1c-118">Details</span></span>  
  
|<span data-ttu-id="83b1c-119">Nazwa elementu danych</span><span class="sxs-lookup"><span data-stu-id="83b1c-119">Data Item Name</span></span>|<span data-ttu-id="83b1c-120">Typ elementu danych</span><span class="sxs-lookup"><span data-stu-id="83b1c-120">Data Item Type</span></span>|<span data-ttu-id="83b1c-121">Opis</span><span class="sxs-lookup"><span data-stu-id="83b1c-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="83b1c-122">Opóźnienie</span><span class="sxs-lookup"><span data-stu-id="83b1c-122">Delay</span></span>|<span data-ttu-id="83b1c-123">xs:String</span><span class="sxs-lookup"><span data-stu-id="83b1c-123">xs:string</span></span>|<span data-ttu-id="83b1c-124">Opóźnienie między kolejnymi próbami.</span><span class="sxs-lookup"><span data-stu-id="83b1c-124">The delay between retries.</span></span>|  
|<span data-ttu-id="83b1c-125">Domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="83b1c-125">AppDomain</span></span>|<span data-ttu-id="83b1c-126">xs:String</span><span class="sxs-lookup"><span data-stu-id="83b1c-126">xs:string</span></span>|<span data-ttu-id="83b1c-127">Długość ciągu zwróconego przez AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="83b1c-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
