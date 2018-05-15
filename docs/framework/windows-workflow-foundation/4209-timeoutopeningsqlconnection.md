---
title: 4209 - TimeoutOpeningSqlConnection
ms.date: 03/30/2017
ms.assetid: f0e56518-9758-41dc-a760-50d1a10fba6e
ms.openlocfilehash: d61d710959f99dbc8a91441766a690eb7e9a365c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="4209---timeoutopeningsqlconnection"></a><span data-ttu-id="7aecc-102">4209 - TimeoutOpeningSqlConnection</span><span class="sxs-lookup"><span data-stu-id="7aecc-102">4209 - TimeoutOpeningSqlConnection</span></span>
## <a name="properties"></a><span data-ttu-id="7aecc-103">Właściwości</span><span class="sxs-lookup"><span data-stu-id="7aecc-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="7aecc-104">ID</span><span class="sxs-lookup"><span data-stu-id="7aecc-104">ID</span></span>|<span data-ttu-id="7aecc-105">4209</span><span class="sxs-lookup"><span data-stu-id="7aecc-105">4209</span></span>|  
|<span data-ttu-id="7aecc-106">Słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="7aecc-106">Keywords</span></span>|<span data-ttu-id="7aecc-107">WFInstanceStore</span><span class="sxs-lookup"><span data-stu-id="7aecc-107">WFInstanceStore</span></span>|  
|<span data-ttu-id="7aecc-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="7aecc-108">Level</span></span>|<span data-ttu-id="7aecc-109">Błąd</span><span class="sxs-lookup"><span data-stu-id="7aecc-109">Error</span></span>|  
|<span data-ttu-id="7aecc-110">Kanał</span><span class="sxs-lookup"><span data-stu-id="7aecc-110">Channel</span></span>|<span data-ttu-id="7aecc-111">Microsoft-Windows aplikacji debugowania serwera — aplikacje</span><span class="sxs-lookup"><span data-stu-id="7aecc-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="7aecc-112">Opis</span><span class="sxs-lookup"><span data-stu-id="7aecc-112">Description</span></span>  
 <span data-ttu-id="7aecc-113">Wskazuje, że limit czasu podczas próby otwarcia połączenia SQL.</span><span class="sxs-lookup"><span data-stu-id="7aecc-113">Indicates a timeout was encountered when trying to open a SQL connection.</span></span>  
  
## <a name="message"></a><span data-ttu-id="7aecc-114">Komunikat</span><span class="sxs-lookup"><span data-stu-id="7aecc-114">Message</span></span>  
 <span data-ttu-id="7aecc-115">Upłynął limit czasu próby otwarcia połączenia SQL.</span><span class="sxs-lookup"><span data-stu-id="7aecc-115">Timeout trying to open a SQL connection.</span></span> <span data-ttu-id="7aecc-116">Operacja nie została ukończona w ciągu przydzielonego limitu czasu równego %1.</span><span class="sxs-lookup"><span data-stu-id="7aecc-116">The operation did not complete within the allotted timeout of %1.</span></span> <span data-ttu-id="7aecc-117">Czas przydzielony na tę operację mógł stanowi część większego limitu czasu.</span><span class="sxs-lookup"><span data-stu-id="7aecc-117">The time allotted to this operation may have been a portion of a longer timeout.</span></span>  
  
## <a name="details"></a><span data-ttu-id="7aecc-118">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="7aecc-118">Details</span></span>  
  
|<span data-ttu-id="7aecc-119">Nazwa elementu danych</span><span class="sxs-lookup"><span data-stu-id="7aecc-119">Data Item Name</span></span>|<span data-ttu-id="7aecc-120">Typ elementu danych</span><span class="sxs-lookup"><span data-stu-id="7aecc-120">Data Item Type</span></span>|<span data-ttu-id="7aecc-121">Opis</span><span class="sxs-lookup"><span data-stu-id="7aecc-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="7aecc-122">Limit czasu</span><span class="sxs-lookup"><span data-stu-id="7aecc-122">Timeout</span></span>|<span data-ttu-id="7aecc-123">xs:String</span><span class="sxs-lookup"><span data-stu-id="7aecc-123">xs:string</span></span>|<span data-ttu-id="7aecc-124">Limit czasu otwarcia połączenia SQL.</span><span class="sxs-lookup"><span data-stu-id="7aecc-124">The timeout value for opening the SQL connection.</span></span>|  
|<span data-ttu-id="7aecc-125">Domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="7aecc-125">AppDomain</span></span>|<span data-ttu-id="7aecc-126">xs:String</span><span class="sxs-lookup"><span data-stu-id="7aecc-126">xs:string</span></span>|<span data-ttu-id="7aecc-127">Długość ciągu zwróconego przez AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="7aecc-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
