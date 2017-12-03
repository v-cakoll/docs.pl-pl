---
title: 4211 - QueuingSqlRetry
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: df569f88-c86b-4503-840d-1399b67f4df7
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 349a91f5b4708d829aee8d7f055871ac7dcc8914
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="4211---queuingsqlretry"></a><span data-ttu-id="f5384-102">4211 - QueuingSqlRetry</span><span class="sxs-lookup"><span data-stu-id="f5384-102">4211 - QueuingSqlRetry</span></span>
## <a name="properties"></a><span data-ttu-id="f5384-103">Właściwości</span><span class="sxs-lookup"><span data-stu-id="f5384-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="f5384-104">ID</span><span class="sxs-lookup"><span data-stu-id="f5384-104">ID</span></span>|<span data-ttu-id="f5384-105">4211</span><span class="sxs-lookup"><span data-stu-id="f5384-105">4211</span></span>|  
|<span data-ttu-id="f5384-106">Słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="f5384-106">Keywords</span></span>|<span data-ttu-id="f5384-107">WFInstanceStore</span><span class="sxs-lookup"><span data-stu-id="f5384-107">WFInstanceStore</span></span>|  
|<span data-ttu-id="f5384-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="f5384-108">Level</span></span>|<span data-ttu-id="f5384-109">Ostrzeżenie</span><span class="sxs-lookup"><span data-stu-id="f5384-109">Warning</span></span>|  
|<span data-ttu-id="f5384-110">Kanał</span><span class="sxs-lookup"><span data-stu-id="f5384-110">Channel</span></span>|<span data-ttu-id="f5384-111">Microsoft-Windows aplikacji debugowania serwera — aplikacje</span><span class="sxs-lookup"><span data-stu-id="f5384-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="f5384-112">Opis</span><span class="sxs-lookup"><span data-stu-id="f5384-112">Description</span></span>  
 <span data-ttu-id="f5384-113">Wskazuje kolejkowania SQL ponów próbę.</span><span class="sxs-lookup"><span data-stu-id="f5384-113">Indicates queuing SQL retry.</span></span>  
  
## <a name="message"></a><span data-ttu-id="f5384-114">Komunikat</span><span class="sxs-lookup"><span data-stu-id="f5384-114">Message</span></span>  
 <span data-ttu-id="f5384-115">Kolejkowanie ponawiania SQL z opóźnieniem %1 MS.</span><span class="sxs-lookup"><span data-stu-id="f5384-115">Queuing SQL retry with delay %1 milliseconds.</span></span>  
  
## <a name="details"></a><span data-ttu-id="f5384-116">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="f5384-116">Details</span></span>  
  
|<span data-ttu-id="f5384-117">Nazwa elementu danych</span><span class="sxs-lookup"><span data-stu-id="f5384-117">Data Item Name</span></span>|<span data-ttu-id="f5384-118">Typ elementu danych</span><span class="sxs-lookup"><span data-stu-id="f5384-118">Data Item Type</span></span>|<span data-ttu-id="f5384-119">Opis</span><span class="sxs-lookup"><span data-stu-id="f5384-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="f5384-120">Opóźnienie</span><span class="sxs-lookup"><span data-stu-id="f5384-120">Delay</span></span>|<span data-ttu-id="f5384-121">xs:String</span><span class="sxs-lookup"><span data-stu-id="f5384-121">xs:string</span></span>|<span data-ttu-id="f5384-122">Opóźnienie między kolejnymi próbami.</span><span class="sxs-lookup"><span data-stu-id="f5384-122">The delay between retries.</span></span>|  
|<span data-ttu-id="f5384-123">Domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="f5384-123">AppDomain</span></span>|<span data-ttu-id="f5384-124">xs:String</span><span class="sxs-lookup"><span data-stu-id="f5384-124">xs:string</span></span>|<span data-ttu-id="f5384-125">Długość ciągu zwróconego przez AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="f5384-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
