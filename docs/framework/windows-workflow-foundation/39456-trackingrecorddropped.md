---
title: 39456 - TrackingRecordDropped
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: da13d5bc-1736-47a4-b3fd-064ca8040326
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 592d7c0a3725dcb50f7911a198c9dc9b7199a0a8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="39456---trackingrecorddropped"></a><span data-ttu-id="86e4a-102">39456 - TrackingRecordDropped</span><span class="sxs-lookup"><span data-stu-id="86e4a-102">39456 - TrackingRecordDropped</span></span>
## <a name="properties"></a><span data-ttu-id="86e4a-103">Właściwości</span><span class="sxs-lookup"><span data-stu-id="86e4a-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="86e4a-104">ID</span><span class="sxs-lookup"><span data-stu-id="86e4a-104">ID</span></span>|<span data-ttu-id="86e4a-105">39456</span><span class="sxs-lookup"><span data-stu-id="86e4a-105">39456</span></span>|  
|<span data-ttu-id="86e4a-106">Słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="86e4a-106">Keywords</span></span>|<span data-ttu-id="86e4a-107">WFTracking</span><span class="sxs-lookup"><span data-stu-id="86e4a-107">WFTracking</span></span>|  
|<span data-ttu-id="86e4a-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="86e4a-108">Level</span></span>|<span data-ttu-id="86e4a-109">Ostrzeżenie</span><span class="sxs-lookup"><span data-stu-id="86e4a-109">Warning</span></span>|  
|<span data-ttu-id="86e4a-110">Kanał</span><span class="sxs-lookup"><span data-stu-id="86e4a-110">Channel</span></span>|<span data-ttu-id="86e4a-111">Microsoft-Windows aplikacji debugowania serwera — aplikacje</span><span class="sxs-lookup"><span data-stu-id="86e4a-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="86e4a-112">Opis</span><span class="sxs-lookup"><span data-stu-id="86e4a-112">Description</span></span>  
 <span data-ttu-id="86e4a-113">Wskazuje, że rekord śledzenia został porzucony, ponieważ jej rozmiar przekracza maksymalną dozwoloną przez dostawcę sesji funkcji ETW.</span><span class="sxs-lookup"><span data-stu-id="86e4a-113">Indicates a tracking record has been dropped because its size exceeds maximum allowed by the ETW session provider.</span></span>  
  
## <a name="message"></a><span data-ttu-id="86e4a-114">Komunikat</span><span class="sxs-lookup"><span data-stu-id="86e4a-114">Message</span></span>  
 <span data-ttu-id="86e4a-115">Rozmiar rekordu śledzenia %1 przekracza maksymalny dozwolony przez sesję usługi ETW dla dostawcy %2</span><span class="sxs-lookup"><span data-stu-id="86e4a-115">Size of tracking record %1 exceeds maximum allowed by the ETW session for provider %2</span></span>  
  
## <a name="details"></a><span data-ttu-id="86e4a-116">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="86e4a-116">Details</span></span>  
  
|<span data-ttu-id="86e4a-117">Nazwa elementu danych</span><span class="sxs-lookup"><span data-stu-id="86e4a-117">Data Item Name</span></span>|<span data-ttu-id="86e4a-118">Typ elementu danych</span><span class="sxs-lookup"><span data-stu-id="86e4a-118">Data Item Type</span></span>|<span data-ttu-id="86e4a-119">Opis</span><span class="sxs-lookup"><span data-stu-id="86e4a-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="86e4a-120">Wyjątek</span><span class="sxs-lookup"><span data-stu-id="86e4a-120">Exception</span></span>|<span data-ttu-id="86e4a-121">xs:String</span><span class="sxs-lookup"><span data-stu-id="86e4a-121">xs:string</span></span>|<span data-ttu-id="86e4a-122">Szczegóły wyjątku dla wyjątku</span><span class="sxs-lookup"><span data-stu-id="86e4a-122">The exception details for the exception</span></span>|  
|<span data-ttu-id="86e4a-123">Domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="86e4a-123">AppDomain</span></span>|<span data-ttu-id="86e4a-124">xs:String</span><span class="sxs-lookup"><span data-stu-id="86e4a-124">xs:string</span></span>|<span data-ttu-id="86e4a-125">Długość ciągu zwróconego przez AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="86e4a-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
