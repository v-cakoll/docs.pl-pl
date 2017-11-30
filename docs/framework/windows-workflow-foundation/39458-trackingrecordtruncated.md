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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: ecf18d6d751edd47dbeca7d2e5f4491892e41e6d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="39458---trackingrecordtruncated"></a><span data-ttu-id="ddd66-102">39458 - TrackingRecordTruncated</span><span class="sxs-lookup"><span data-stu-id="ddd66-102">39458 - TrackingRecordTruncated</span></span>
## <a name="properties"></a><span data-ttu-id="ddd66-103">Właściwości</span><span class="sxs-lookup"><span data-stu-id="ddd66-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="ddd66-104">ID</span><span class="sxs-lookup"><span data-stu-id="ddd66-104">ID</span></span>|<span data-ttu-id="ddd66-105">39458</span><span class="sxs-lookup"><span data-stu-id="ddd66-105">39458</span></span>|  
|<span data-ttu-id="ddd66-106">Słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="ddd66-106">Keywords</span></span>|<span data-ttu-id="ddd66-107">WFTracking</span><span class="sxs-lookup"><span data-stu-id="ddd66-107">WFTracking</span></span>|  
|<span data-ttu-id="ddd66-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="ddd66-108">Level</span></span>|<span data-ttu-id="ddd66-109">Ostrzeżenie</span><span class="sxs-lookup"><span data-stu-id="ddd66-109">Warning</span></span>|  
|<span data-ttu-id="ddd66-110">Kanał</span><span class="sxs-lookup"><span data-stu-id="ddd66-110">Channel</span></span>|<span data-ttu-id="ddd66-111">Microsoft-Windows aplikacji debugowania serwera — aplikacje</span><span class="sxs-lookup"><span data-stu-id="ddd66-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="ddd66-112">Opis</span><span class="sxs-lookup"><span data-stu-id="ddd66-112">Description</span></span>  
 <span data-ttu-id="ddd66-113">Wskazuje, że został obcięty rekord śledzenia.</span><span class="sxs-lookup"><span data-stu-id="ddd66-113">Indicates a tracking record has been truncated.</span></span> <span data-ttu-id="ddd66-114">Zmienne/adnotacje/dane użytkownika zostały usunięte.</span><span class="sxs-lookup"><span data-stu-id="ddd66-114">Variables/annotations/user data have been removed.</span></span>  
  
## <a name="message"></a><span data-ttu-id="ddd66-115">Komunikat</span><span class="sxs-lookup"><span data-stu-id="ddd66-115">Message</span></span>  
 <span data-ttu-id="ddd66-116">Obcięty rekord śledzenia %1 został zapisany w sesji usługi ETW za pomocą dostawcy %2.</span><span class="sxs-lookup"><span data-stu-id="ddd66-116">Truncated tracking record %1 written to ETW session with provider %2.</span></span> <span data-ttu-id="ddd66-117">Zmienne/adnotacje/dane użytkownika zostały usunięte</span><span class="sxs-lookup"><span data-stu-id="ddd66-117">Variables/annotations/user data have been removed</span></span>  
  
## <a name="details"></a><span data-ttu-id="ddd66-118">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="ddd66-118">Details</span></span>  
  
|<span data-ttu-id="ddd66-119">Nazwa elementu danych</span><span class="sxs-lookup"><span data-stu-id="ddd66-119">Data Item Name</span></span>|<span data-ttu-id="ddd66-120">Typ elementu danych</span><span class="sxs-lookup"><span data-stu-id="ddd66-120">Data Item Type</span></span>|<span data-ttu-id="ddd66-121">Opis</span><span class="sxs-lookup"><span data-stu-id="ddd66-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="ddd66-122">RecordNumber</span><span class="sxs-lookup"><span data-stu-id="ddd66-122">RecordNumber</span></span>|<span data-ttu-id="ddd66-123">xs:String</span><span class="sxs-lookup"><span data-stu-id="ddd66-123">xs:string</span></span>|<span data-ttu-id="ddd66-124">Liczba rekordów śledzenia.</span><span class="sxs-lookup"><span data-stu-id="ddd66-124">The tracking record number.</span></span>|  
|<span data-ttu-id="ddd66-125">Identyfikator dostawcy</span><span class="sxs-lookup"><span data-stu-id="ddd66-125">ProviderId</span></span>|<span data-ttu-id="ddd66-126">xs:String</span><span class="sxs-lookup"><span data-stu-id="ddd66-126">xs:string</span></span>|<span data-ttu-id="ddd66-127">Identyfikator dostawcy ETW.</span><span class="sxs-lookup"><span data-stu-id="ddd66-127">The ETW provider id.</span></span>|  
|<span data-ttu-id="ddd66-128">Domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="ddd66-128">AppDomain</span></span>|<span data-ttu-id="ddd66-129">xs:String</span><span class="sxs-lookup"><span data-stu-id="ddd66-129">xs:string</span></span>|<span data-ttu-id="ddd66-130">Długość ciągu zwróconego przez AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="ddd66-130">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
