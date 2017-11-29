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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: c318ee6509ce8b96a1e7e78a13f4aeb7c76dde6a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="4211---queuingsqlretry"></a><span data-ttu-id="63856-102">4211 - QueuingSqlRetry</span><span class="sxs-lookup"><span data-stu-id="63856-102">4211 - QueuingSqlRetry</span></span>
## <a name="properties"></a><span data-ttu-id="63856-103">Właściwości</span><span class="sxs-lookup"><span data-stu-id="63856-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="63856-104">ID</span><span class="sxs-lookup"><span data-stu-id="63856-104">ID</span></span>|<span data-ttu-id="63856-105">4211</span><span class="sxs-lookup"><span data-stu-id="63856-105">4211</span></span>|  
|<span data-ttu-id="63856-106">Słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="63856-106">Keywords</span></span>|<span data-ttu-id="63856-107">WFInstanceStore</span><span class="sxs-lookup"><span data-stu-id="63856-107">WFInstanceStore</span></span>|  
|<span data-ttu-id="63856-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="63856-108">Level</span></span>|<span data-ttu-id="63856-109">Ostrzeżenie</span><span class="sxs-lookup"><span data-stu-id="63856-109">Warning</span></span>|  
|<span data-ttu-id="63856-110">Kanał</span><span class="sxs-lookup"><span data-stu-id="63856-110">Channel</span></span>|<span data-ttu-id="63856-111">Microsoft-Windows aplikacji debugowania serwera — aplikacje</span><span class="sxs-lookup"><span data-stu-id="63856-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="63856-112">Opis</span><span class="sxs-lookup"><span data-stu-id="63856-112">Description</span></span>  
 <span data-ttu-id="63856-113">Wskazuje kolejkowania SQL ponów próbę.</span><span class="sxs-lookup"><span data-stu-id="63856-113">Indicates queuing SQL retry.</span></span>  
  
## <a name="message"></a><span data-ttu-id="63856-114">Komunikat</span><span class="sxs-lookup"><span data-stu-id="63856-114">Message</span></span>  
 <span data-ttu-id="63856-115">Kolejkowanie ponawiania SQL z opóźnieniem %1 MS.</span><span class="sxs-lookup"><span data-stu-id="63856-115">Queuing SQL retry with delay %1 milliseconds.</span></span>  
  
## <a name="details"></a><span data-ttu-id="63856-116">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="63856-116">Details</span></span>  
  
|<span data-ttu-id="63856-117">Nazwa elementu danych</span><span class="sxs-lookup"><span data-stu-id="63856-117">Data Item Name</span></span>|<span data-ttu-id="63856-118">Typ elementu danych</span><span class="sxs-lookup"><span data-stu-id="63856-118">Data Item Type</span></span>|<span data-ttu-id="63856-119">Opis</span><span class="sxs-lookup"><span data-stu-id="63856-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="63856-120">Opóźnienie</span><span class="sxs-lookup"><span data-stu-id="63856-120">Delay</span></span>|<span data-ttu-id="63856-121">xs:String</span><span class="sxs-lookup"><span data-stu-id="63856-121">xs:string</span></span>|<span data-ttu-id="63856-122">Opóźnienie między kolejnymi próbami.</span><span class="sxs-lookup"><span data-stu-id="63856-122">The delay between retries.</span></span>|  
|<span data-ttu-id="63856-123">Domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="63856-123">AppDomain</span></span>|<span data-ttu-id="63856-124">xs:String</span><span class="sxs-lookup"><span data-stu-id="63856-124">xs:string</span></span>|<span data-ttu-id="63856-125">Długość ciągu zwróconego przez AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="63856-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
