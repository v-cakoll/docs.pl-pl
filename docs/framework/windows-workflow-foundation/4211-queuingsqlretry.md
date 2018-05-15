---
title: 4211 - QueuingSqlRetry
ms.date: 03/30/2017
ms.assetid: df569f88-c86b-4503-840d-1399b67f4df7
ms.openlocfilehash: ede74eb642c5c2c79b90cf1458db424d9f83b087
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="4211---queuingsqlretry"></a><span data-ttu-id="507b7-102">4211 - QueuingSqlRetry</span><span class="sxs-lookup"><span data-stu-id="507b7-102">4211 - QueuingSqlRetry</span></span>
## <a name="properties"></a><span data-ttu-id="507b7-103">Właściwości</span><span class="sxs-lookup"><span data-stu-id="507b7-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="507b7-104">ID</span><span class="sxs-lookup"><span data-stu-id="507b7-104">ID</span></span>|<span data-ttu-id="507b7-105">4211</span><span class="sxs-lookup"><span data-stu-id="507b7-105">4211</span></span>|  
|<span data-ttu-id="507b7-106">Słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="507b7-106">Keywords</span></span>|<span data-ttu-id="507b7-107">WFInstanceStore</span><span class="sxs-lookup"><span data-stu-id="507b7-107">WFInstanceStore</span></span>|  
|<span data-ttu-id="507b7-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="507b7-108">Level</span></span>|<span data-ttu-id="507b7-109">Ostrzeżenie</span><span class="sxs-lookup"><span data-stu-id="507b7-109">Warning</span></span>|  
|<span data-ttu-id="507b7-110">Kanał</span><span class="sxs-lookup"><span data-stu-id="507b7-110">Channel</span></span>|<span data-ttu-id="507b7-111">Microsoft-Windows aplikacji debugowania serwera — aplikacje</span><span class="sxs-lookup"><span data-stu-id="507b7-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="507b7-112">Opis</span><span class="sxs-lookup"><span data-stu-id="507b7-112">Description</span></span>  
 <span data-ttu-id="507b7-113">Wskazuje kolejkowania SQL ponów próbę.</span><span class="sxs-lookup"><span data-stu-id="507b7-113">Indicates queuing SQL retry.</span></span>  
  
## <a name="message"></a><span data-ttu-id="507b7-114">Komunikat</span><span class="sxs-lookup"><span data-stu-id="507b7-114">Message</span></span>  
 <span data-ttu-id="507b7-115">Kolejkowanie ponawiania SQL z opóźnieniem %1 MS.</span><span class="sxs-lookup"><span data-stu-id="507b7-115">Queuing SQL retry with delay %1 milliseconds.</span></span>  
  
## <a name="details"></a><span data-ttu-id="507b7-116">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="507b7-116">Details</span></span>  
  
|<span data-ttu-id="507b7-117">Nazwa elementu danych</span><span class="sxs-lookup"><span data-stu-id="507b7-117">Data Item Name</span></span>|<span data-ttu-id="507b7-118">Typ elementu danych</span><span class="sxs-lookup"><span data-stu-id="507b7-118">Data Item Type</span></span>|<span data-ttu-id="507b7-119">Opis</span><span class="sxs-lookup"><span data-stu-id="507b7-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="507b7-120">Opóźnienie</span><span class="sxs-lookup"><span data-stu-id="507b7-120">Delay</span></span>|<span data-ttu-id="507b7-121">xs:String</span><span class="sxs-lookup"><span data-stu-id="507b7-121">xs:string</span></span>|<span data-ttu-id="507b7-122">Opóźnienie między kolejnymi próbami.</span><span class="sxs-lookup"><span data-stu-id="507b7-122">The delay between retries.</span></span>|  
|<span data-ttu-id="507b7-123">Domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="507b7-123">AppDomain</span></span>|<span data-ttu-id="507b7-124">xs:String</span><span class="sxs-lookup"><span data-stu-id="507b7-124">xs:string</span></span>|<span data-ttu-id="507b7-125">Długość ciągu zwróconego przez AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="507b7-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
