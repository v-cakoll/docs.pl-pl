---
title: 4212 - LockRetryTimeout
ms.date: 03/30/2017
ms.assetid: d4ad415a-9871-49fc-85b8-8ee2ea149b1d
ms.openlocfilehash: 9b7a463851d380eba1ef7b28fbc6decd0cfc979c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="4212---lockretrytimeout"></a><span data-ttu-id="69475-102">4212 - LockRetryTimeout</span><span class="sxs-lookup"><span data-stu-id="69475-102">4212 - LockRetryTimeout</span></span>
## <a name="properties"></a><span data-ttu-id="69475-103">Właściwości</span><span class="sxs-lookup"><span data-stu-id="69475-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="69475-104">ID</span><span class="sxs-lookup"><span data-stu-id="69475-104">ID</span></span>|<span data-ttu-id="69475-105">4212</span><span class="sxs-lookup"><span data-stu-id="69475-105">4212</span></span>|  
|<span data-ttu-id="69475-106">Słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="69475-106">Keywords</span></span>|<span data-ttu-id="69475-107">WFInstanceStore</span><span class="sxs-lookup"><span data-stu-id="69475-107">WFInstanceStore</span></span>|  
|<span data-ttu-id="69475-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="69475-108">Level</span></span>|<span data-ttu-id="69475-109">Ostrzeżenie</span><span class="sxs-lookup"><span data-stu-id="69475-109">Warning</span></span>|  
|<span data-ttu-id="69475-110">Kanał</span><span class="sxs-lookup"><span data-stu-id="69475-110">Channel</span></span>|<span data-ttu-id="69475-111">Microsoft-Windows aplikacji debugowania serwera — aplikacje</span><span class="sxs-lookup"><span data-stu-id="69475-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="69475-112">Opis</span><span class="sxs-lookup"><span data-stu-id="69475-112">Description</span></span>  
 <span data-ttu-id="69475-113">Dostawca SQL został przekroczony limit czasu próby uzyskania blokady wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="69475-113">SQL provider encountered a timeout trying to acquire the instance lock.</span></span>  
  
## <a name="message"></a><span data-ttu-id="69475-114">Komunikat</span><span class="sxs-lookup"><span data-stu-id="69475-114">Message</span></span>  
 <span data-ttu-id="69475-115">Limit czasu próby uzyskania blokady wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="69475-115">Timeout trying to acquire the instance lock.</span></span>  <span data-ttu-id="69475-116">Operacja nie została ukończona w ciągu przydzielonego limitu czasu równego %1.</span><span class="sxs-lookup"><span data-stu-id="69475-116">The operation did not complete within the allotted timeout of %1.</span></span> <span data-ttu-id="69475-117">Czas przydzielony na tę operację mógł stanowi część większego limitu czasu.</span><span class="sxs-lookup"><span data-stu-id="69475-117">The time allotted to this operation may have been a portion of a longer timeout.</span></span>  
  
## <a name="details"></a><span data-ttu-id="69475-118">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="69475-118">Details</span></span>  
  
|<span data-ttu-id="69475-119">Nazwa elementu danych</span><span class="sxs-lookup"><span data-stu-id="69475-119">Data Item Name</span></span>|<span data-ttu-id="69475-120">Typ elementu danych</span><span class="sxs-lookup"><span data-stu-id="69475-120">Data Item Type</span></span>|<span data-ttu-id="69475-121">Opis</span><span class="sxs-lookup"><span data-stu-id="69475-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="69475-122">Opóźnienie</span><span class="sxs-lookup"><span data-stu-id="69475-122">Delay</span></span>|<span data-ttu-id="69475-123">xs:String</span><span class="sxs-lookup"><span data-stu-id="69475-123">xs:string</span></span>|<span data-ttu-id="69475-124">Opóźnienie między kolejnymi próbami.</span><span class="sxs-lookup"><span data-stu-id="69475-124">The delay between retries.</span></span>|  
|<span data-ttu-id="69475-125">Domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="69475-125">AppDomain</span></span>|<span data-ttu-id="69475-126">xs:String</span><span class="sxs-lookup"><span data-stu-id="69475-126">xs:string</span></span>|<span data-ttu-id="69475-127">Długość ciągu zwróconego przez AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="69475-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
