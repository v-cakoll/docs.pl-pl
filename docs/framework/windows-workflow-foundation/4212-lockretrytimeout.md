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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 897e6ef8b739654a61058106966c870c47f8129a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="4212---lockretrytimeout"></a><span data-ttu-id="c2d11-102">4212 - LockRetryTimeout</span><span class="sxs-lookup"><span data-stu-id="c2d11-102">4212 - LockRetryTimeout</span></span>
## <a name="properties"></a><span data-ttu-id="c2d11-103">Właściwości</span><span class="sxs-lookup"><span data-stu-id="c2d11-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="c2d11-104">ID</span><span class="sxs-lookup"><span data-stu-id="c2d11-104">ID</span></span>|<span data-ttu-id="c2d11-105">4212</span><span class="sxs-lookup"><span data-stu-id="c2d11-105">4212</span></span>|  
|<span data-ttu-id="c2d11-106">Słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="c2d11-106">Keywords</span></span>|<span data-ttu-id="c2d11-107">WFInstanceStore</span><span class="sxs-lookup"><span data-stu-id="c2d11-107">WFInstanceStore</span></span>|  
|<span data-ttu-id="c2d11-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="c2d11-108">Level</span></span>|<span data-ttu-id="c2d11-109">Ostrzeżenie</span><span class="sxs-lookup"><span data-stu-id="c2d11-109">Warning</span></span>|  
|<span data-ttu-id="c2d11-110">Kanał</span><span class="sxs-lookup"><span data-stu-id="c2d11-110">Channel</span></span>|<span data-ttu-id="c2d11-111">Microsoft-Windows aplikacji debugowania serwera — aplikacje</span><span class="sxs-lookup"><span data-stu-id="c2d11-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="c2d11-112">Opis</span><span class="sxs-lookup"><span data-stu-id="c2d11-112">Description</span></span>  
 <span data-ttu-id="c2d11-113">Dostawca SQL został przekroczony limit czasu próby uzyskania blokady wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="c2d11-113">SQL provider encountered a timeout trying to acquire the instance lock.</span></span>  
  
## <a name="message"></a><span data-ttu-id="c2d11-114">Komunikat</span><span class="sxs-lookup"><span data-stu-id="c2d11-114">Message</span></span>  
 <span data-ttu-id="c2d11-115">Limit czasu próby uzyskania blokady wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="c2d11-115">Timeout trying to acquire the instance lock.</span></span>  <span data-ttu-id="c2d11-116">Operacja nie została ukończona w ciągu przydzielonego limitu czasu równego %1.</span><span class="sxs-lookup"><span data-stu-id="c2d11-116">The operation did not complete within the allotted timeout of %1.</span></span> <span data-ttu-id="c2d11-117">Czas przydzielony na tę operację mógł stanowi część większego limitu czasu.</span><span class="sxs-lookup"><span data-stu-id="c2d11-117">The time allotted to this operation may have been a portion of a longer timeout.</span></span>  
  
## <a name="details"></a><span data-ttu-id="c2d11-118">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="c2d11-118">Details</span></span>  
  
|<span data-ttu-id="c2d11-119">Nazwa elementu danych</span><span class="sxs-lookup"><span data-stu-id="c2d11-119">Data Item Name</span></span>|<span data-ttu-id="c2d11-120">Typ elementu danych</span><span class="sxs-lookup"><span data-stu-id="c2d11-120">Data Item Type</span></span>|<span data-ttu-id="c2d11-121">Opis</span><span class="sxs-lookup"><span data-stu-id="c2d11-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="c2d11-122">Opóźnienie</span><span class="sxs-lookup"><span data-stu-id="c2d11-122">Delay</span></span>|<span data-ttu-id="c2d11-123">xs:String</span><span class="sxs-lookup"><span data-stu-id="c2d11-123">xs:string</span></span>|<span data-ttu-id="c2d11-124">Opóźnienie między kolejnymi próbami.</span><span class="sxs-lookup"><span data-stu-id="c2d11-124">The delay between retries.</span></span>|  
|<span data-ttu-id="c2d11-125">Domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="c2d11-125">AppDomain</span></span>|<span data-ttu-id="c2d11-126">xs:String</span><span class="sxs-lookup"><span data-stu-id="c2d11-126">xs:string</span></span>|<span data-ttu-id="c2d11-127">Długość ciągu zwróconego przez AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="c2d11-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
