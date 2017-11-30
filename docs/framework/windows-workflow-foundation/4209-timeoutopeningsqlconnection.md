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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: f87e99585ccbdf3b89653f026860e7b66dc6c9b6
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="4209---timeoutopeningsqlconnection"></a><span data-ttu-id="d87d2-102">4209 - TimeoutOpeningSqlConnection</span><span class="sxs-lookup"><span data-stu-id="d87d2-102">4209 - TimeoutOpeningSqlConnection</span></span>
## <a name="properties"></a><span data-ttu-id="d87d2-103">Właściwości</span><span class="sxs-lookup"><span data-stu-id="d87d2-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="d87d2-104">ID</span><span class="sxs-lookup"><span data-stu-id="d87d2-104">ID</span></span>|<span data-ttu-id="d87d2-105">4209</span><span class="sxs-lookup"><span data-stu-id="d87d2-105">4209</span></span>|  
|<span data-ttu-id="d87d2-106">Słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="d87d2-106">Keywords</span></span>|<span data-ttu-id="d87d2-107">WFInstanceStore</span><span class="sxs-lookup"><span data-stu-id="d87d2-107">WFInstanceStore</span></span>|  
|<span data-ttu-id="d87d2-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="d87d2-108">Level</span></span>|<span data-ttu-id="d87d2-109">Błąd</span><span class="sxs-lookup"><span data-stu-id="d87d2-109">Error</span></span>|  
|<span data-ttu-id="d87d2-110">Kanał</span><span class="sxs-lookup"><span data-stu-id="d87d2-110">Channel</span></span>|<span data-ttu-id="d87d2-111">Microsoft-Windows aplikacji debugowania serwera — aplikacje</span><span class="sxs-lookup"><span data-stu-id="d87d2-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="d87d2-112">Opis</span><span class="sxs-lookup"><span data-stu-id="d87d2-112">Description</span></span>  
 <span data-ttu-id="d87d2-113">Wskazuje, że limit czasu podczas próby otwarcia połączenia SQL.</span><span class="sxs-lookup"><span data-stu-id="d87d2-113">Indicates a timeout was encountered when trying to open a SQL connection.</span></span>  
  
## <a name="message"></a><span data-ttu-id="d87d2-114">Komunikat</span><span class="sxs-lookup"><span data-stu-id="d87d2-114">Message</span></span>  
 <span data-ttu-id="d87d2-115">Upłynął limit czasu próby otwarcia połączenia SQL.</span><span class="sxs-lookup"><span data-stu-id="d87d2-115">Timeout trying to open a SQL connection.</span></span> <span data-ttu-id="d87d2-116">Operacja nie została ukończona w ciągu przydzielonego limitu czasu równego %1.</span><span class="sxs-lookup"><span data-stu-id="d87d2-116">The operation did not complete within the allotted timeout of %1.</span></span> <span data-ttu-id="d87d2-117">Czas przydzielony na tę operację mógł stanowi część większego limitu czasu.</span><span class="sxs-lookup"><span data-stu-id="d87d2-117">The time allotted to this operation may have been a portion of a longer timeout.</span></span>  
  
## <a name="details"></a><span data-ttu-id="d87d2-118">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="d87d2-118">Details</span></span>  
  
|<span data-ttu-id="d87d2-119">Nazwa elementu danych</span><span class="sxs-lookup"><span data-stu-id="d87d2-119">Data Item Name</span></span>|<span data-ttu-id="d87d2-120">Typ elementu danych</span><span class="sxs-lookup"><span data-stu-id="d87d2-120">Data Item Type</span></span>|<span data-ttu-id="d87d2-121">Opis</span><span class="sxs-lookup"><span data-stu-id="d87d2-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="d87d2-122">Limit czasu</span><span class="sxs-lookup"><span data-stu-id="d87d2-122">Timeout</span></span>|<span data-ttu-id="d87d2-123">xs:String</span><span class="sxs-lookup"><span data-stu-id="d87d2-123">xs:string</span></span>|<span data-ttu-id="d87d2-124">Limit czasu otwarcia połączenia SQL.</span><span class="sxs-lookup"><span data-stu-id="d87d2-124">The timeout value for opening the SQL connection.</span></span>|  
|<span data-ttu-id="d87d2-125">Domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="d87d2-125">AppDomain</span></span>|<span data-ttu-id="d87d2-126">xs:String</span><span class="sxs-lookup"><span data-stu-id="d87d2-126">xs:string</span></span>|<span data-ttu-id="d87d2-127">Długość ciągu zwróconego przez AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="d87d2-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
