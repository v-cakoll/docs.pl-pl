---
title: 4209 - TimeoutOpeningSqlConnection
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f0e56518-9758-41dc-a760-50d1a10fba6e
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 86d971a2e5f1257281c453e7eb0c2dc1755098d8
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="4209---timeoutopeningsqlconnection"></a><span data-ttu-id="dfd0a-102">4209 - TimeoutOpeningSqlConnection</span><span class="sxs-lookup"><span data-stu-id="dfd0a-102">4209 - TimeoutOpeningSqlConnection</span></span>
## <a name="properties"></a><span data-ttu-id="dfd0a-103">Właściwości</span><span class="sxs-lookup"><span data-stu-id="dfd0a-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="dfd0a-104">ID</span><span class="sxs-lookup"><span data-stu-id="dfd0a-104">ID</span></span>|<span data-ttu-id="dfd0a-105">4209</span><span class="sxs-lookup"><span data-stu-id="dfd0a-105">4209</span></span>|  
|<span data-ttu-id="dfd0a-106">Słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="dfd0a-106">Keywords</span></span>|<span data-ttu-id="dfd0a-107">WFInstanceStore</span><span class="sxs-lookup"><span data-stu-id="dfd0a-107">WFInstanceStore</span></span>|  
|<span data-ttu-id="dfd0a-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="dfd0a-108">Level</span></span>|<span data-ttu-id="dfd0a-109">Błąd</span><span class="sxs-lookup"><span data-stu-id="dfd0a-109">Error</span></span>|  
|<span data-ttu-id="dfd0a-110">Kanał</span><span class="sxs-lookup"><span data-stu-id="dfd0a-110">Channel</span></span>|<span data-ttu-id="dfd0a-111">Microsoft-Windows aplikacji debugowania serwera — aplikacje</span><span class="sxs-lookup"><span data-stu-id="dfd0a-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="dfd0a-112">Opis</span><span class="sxs-lookup"><span data-stu-id="dfd0a-112">Description</span></span>  
 <span data-ttu-id="dfd0a-113">Wskazuje, że limit czasu podczas próby otwarcia połączenia SQL.</span><span class="sxs-lookup"><span data-stu-id="dfd0a-113">Indicates a timeout was encountered when trying to open a SQL connection.</span></span>  
  
## <a name="message"></a><span data-ttu-id="dfd0a-114">Komunikat</span><span class="sxs-lookup"><span data-stu-id="dfd0a-114">Message</span></span>  
 <span data-ttu-id="dfd0a-115">Upłynął limit czasu próby otwarcia połączenia SQL.</span><span class="sxs-lookup"><span data-stu-id="dfd0a-115">Timeout trying to open a SQL connection.</span></span> <span data-ttu-id="dfd0a-116">Operacja nie została ukończona w ciągu przydzielonego limitu czasu równego %1.</span><span class="sxs-lookup"><span data-stu-id="dfd0a-116">The operation did not complete within the allotted timeout of %1.</span></span> <span data-ttu-id="dfd0a-117">Czas przydzielony na tę operację mógł stanowi część większego limitu czasu.</span><span class="sxs-lookup"><span data-stu-id="dfd0a-117">The time allotted to this operation may have been a portion of a longer timeout.</span></span>  
  
## <a name="details"></a><span data-ttu-id="dfd0a-118">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="dfd0a-118">Details</span></span>  
  
|<span data-ttu-id="dfd0a-119">Nazwa elementu danych</span><span class="sxs-lookup"><span data-stu-id="dfd0a-119">Data Item Name</span></span>|<span data-ttu-id="dfd0a-120">Typ elementu danych</span><span class="sxs-lookup"><span data-stu-id="dfd0a-120">Data Item Type</span></span>|<span data-ttu-id="dfd0a-121">Opis</span><span class="sxs-lookup"><span data-stu-id="dfd0a-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="dfd0a-122">Limit czasu</span><span class="sxs-lookup"><span data-stu-id="dfd0a-122">Timeout</span></span>|<span data-ttu-id="dfd0a-123">xs:String</span><span class="sxs-lookup"><span data-stu-id="dfd0a-123">xs:string</span></span>|<span data-ttu-id="dfd0a-124">Limit czasu otwarcia połączenia SQL.</span><span class="sxs-lookup"><span data-stu-id="dfd0a-124">The timeout value for opening the SQL connection.</span></span>|  
|<span data-ttu-id="dfd0a-125">Domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="dfd0a-125">AppDomain</span></span>|<span data-ttu-id="dfd0a-126">xs:String</span><span class="sxs-lookup"><span data-stu-id="dfd0a-126">xs:string</span></span>|<span data-ttu-id="dfd0a-127">Długość ciągu zwróconego przez AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="dfd0a-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
