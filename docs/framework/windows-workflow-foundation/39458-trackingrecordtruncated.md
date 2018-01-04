---
title: 39458 - TrackingRecordTruncated
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5352f0eb-d571-454a-bab5-e2162888b218
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4d12549d201ac621361bd6a517df6c6b53ab7aec
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="39458---trackingrecordtruncated"></a><span data-ttu-id="74a18-102">39458 - TrackingRecordTruncated</span><span class="sxs-lookup"><span data-stu-id="74a18-102">39458 - TrackingRecordTruncated</span></span>
## <a name="properties"></a><span data-ttu-id="74a18-103">Właściwości</span><span class="sxs-lookup"><span data-stu-id="74a18-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="74a18-104">ID</span><span class="sxs-lookup"><span data-stu-id="74a18-104">ID</span></span>|<span data-ttu-id="74a18-105">39458</span><span class="sxs-lookup"><span data-stu-id="74a18-105">39458</span></span>|  
|<span data-ttu-id="74a18-106">Słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="74a18-106">Keywords</span></span>|<span data-ttu-id="74a18-107">WFTracking</span><span class="sxs-lookup"><span data-stu-id="74a18-107">WFTracking</span></span>|  
|<span data-ttu-id="74a18-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="74a18-108">Level</span></span>|<span data-ttu-id="74a18-109">Ostrzeżenie</span><span class="sxs-lookup"><span data-stu-id="74a18-109">Warning</span></span>|  
|<span data-ttu-id="74a18-110">Kanał</span><span class="sxs-lookup"><span data-stu-id="74a18-110">Channel</span></span>|<span data-ttu-id="74a18-111">Microsoft-Windows aplikacji debugowania serwera — aplikacje</span><span class="sxs-lookup"><span data-stu-id="74a18-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="74a18-112">Opis</span><span class="sxs-lookup"><span data-stu-id="74a18-112">Description</span></span>  
 <span data-ttu-id="74a18-113">Wskazuje, że został obcięty rekord śledzenia.</span><span class="sxs-lookup"><span data-stu-id="74a18-113">Indicates a tracking record has been truncated.</span></span> <span data-ttu-id="74a18-114">Zmienne/adnotacje/dane użytkownika zostały usunięte.</span><span class="sxs-lookup"><span data-stu-id="74a18-114">Variables/annotations/user data have been removed.</span></span>  
  
## <a name="message"></a><span data-ttu-id="74a18-115">Komunikat</span><span class="sxs-lookup"><span data-stu-id="74a18-115">Message</span></span>  
 <span data-ttu-id="74a18-116">Obcięty rekord śledzenia %1 został zapisany w sesji usługi ETW za pomocą dostawcy %2.</span><span class="sxs-lookup"><span data-stu-id="74a18-116">Truncated tracking record %1 written to ETW session with provider %2.</span></span> <span data-ttu-id="74a18-117">Zmienne/adnotacje/dane użytkownika zostały usunięte</span><span class="sxs-lookup"><span data-stu-id="74a18-117">Variables/annotations/user data have been removed</span></span>  
  
## <a name="details"></a><span data-ttu-id="74a18-118">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="74a18-118">Details</span></span>  
  
|<span data-ttu-id="74a18-119">Nazwa elementu danych</span><span class="sxs-lookup"><span data-stu-id="74a18-119">Data Item Name</span></span>|<span data-ttu-id="74a18-120">Typ elementu danych</span><span class="sxs-lookup"><span data-stu-id="74a18-120">Data Item Type</span></span>|<span data-ttu-id="74a18-121">Opis</span><span class="sxs-lookup"><span data-stu-id="74a18-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="74a18-122">RecordNumber</span><span class="sxs-lookup"><span data-stu-id="74a18-122">RecordNumber</span></span>|<span data-ttu-id="74a18-123">xs:String</span><span class="sxs-lookup"><span data-stu-id="74a18-123">xs:string</span></span>|<span data-ttu-id="74a18-124">Liczba rekordów śledzenia.</span><span class="sxs-lookup"><span data-stu-id="74a18-124">The tracking record number.</span></span>|  
|<span data-ttu-id="74a18-125">Identyfikator dostawcy</span><span class="sxs-lookup"><span data-stu-id="74a18-125">ProviderId</span></span>|<span data-ttu-id="74a18-126">xs:String</span><span class="sxs-lookup"><span data-stu-id="74a18-126">xs:string</span></span>|<span data-ttu-id="74a18-127">Identyfikator dostawcy ETW.</span><span class="sxs-lookup"><span data-stu-id="74a18-127">The ETW provider id.</span></span>|  
|<span data-ttu-id="74a18-128">Domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="74a18-128">AppDomain</span></span>|<span data-ttu-id="74a18-129">xs:String</span><span class="sxs-lookup"><span data-stu-id="74a18-129">xs:string</span></span>|<span data-ttu-id="74a18-130">Długość ciągu zwróconego przez AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="74a18-130">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
