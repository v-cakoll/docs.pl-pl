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
ms.openlocfilehash: 1d2bc07cff75fce7ddb50da9f54d161d7f235cab
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="39458---trackingrecordtruncated"></a><span data-ttu-id="ba274-102">39458 - TrackingRecordTruncated</span><span class="sxs-lookup"><span data-stu-id="ba274-102">39458 - TrackingRecordTruncated</span></span>
## <a name="properties"></a><span data-ttu-id="ba274-103">Właściwości</span><span class="sxs-lookup"><span data-stu-id="ba274-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="ba274-104">ID</span><span class="sxs-lookup"><span data-stu-id="ba274-104">ID</span></span>|<span data-ttu-id="ba274-105">39458</span><span class="sxs-lookup"><span data-stu-id="ba274-105">39458</span></span>|  
|<span data-ttu-id="ba274-106">Słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="ba274-106">Keywords</span></span>|<span data-ttu-id="ba274-107">WFTracking</span><span class="sxs-lookup"><span data-stu-id="ba274-107">WFTracking</span></span>|  
|<span data-ttu-id="ba274-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="ba274-108">Level</span></span>|<span data-ttu-id="ba274-109">Ostrzeżenie</span><span class="sxs-lookup"><span data-stu-id="ba274-109">Warning</span></span>|  
|<span data-ttu-id="ba274-110">Kanał</span><span class="sxs-lookup"><span data-stu-id="ba274-110">Channel</span></span>|<span data-ttu-id="ba274-111">Microsoft-Windows aplikacji debugowania serwera — aplikacje</span><span class="sxs-lookup"><span data-stu-id="ba274-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="ba274-112">Opis</span><span class="sxs-lookup"><span data-stu-id="ba274-112">Description</span></span>  
 <span data-ttu-id="ba274-113">Wskazuje, że został obcięty rekord śledzenia.</span><span class="sxs-lookup"><span data-stu-id="ba274-113">Indicates a tracking record has been truncated.</span></span> <span data-ttu-id="ba274-114">Zmienne/adnotacje/dane użytkownika zostały usunięte.</span><span class="sxs-lookup"><span data-stu-id="ba274-114">Variables/annotations/user data have been removed.</span></span>  
  
## <a name="message"></a><span data-ttu-id="ba274-115">Komunikat</span><span class="sxs-lookup"><span data-stu-id="ba274-115">Message</span></span>  
 <span data-ttu-id="ba274-116">Obcięty rekord śledzenia %1 został zapisany w sesji usługi ETW za pomocą dostawcy %2.</span><span class="sxs-lookup"><span data-stu-id="ba274-116">Truncated tracking record %1 written to ETW session with provider %2.</span></span> <span data-ttu-id="ba274-117">Zmienne/adnotacje/dane użytkownika zostały usunięte</span><span class="sxs-lookup"><span data-stu-id="ba274-117">Variables/annotations/user data have been removed</span></span>  
  
## <a name="details"></a><span data-ttu-id="ba274-118">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="ba274-118">Details</span></span>  
  
|<span data-ttu-id="ba274-119">Nazwa elementu danych</span><span class="sxs-lookup"><span data-stu-id="ba274-119">Data Item Name</span></span>|<span data-ttu-id="ba274-120">Typ elementu danych</span><span class="sxs-lookup"><span data-stu-id="ba274-120">Data Item Type</span></span>|<span data-ttu-id="ba274-121">Opis</span><span class="sxs-lookup"><span data-stu-id="ba274-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="ba274-122">RecordNumber</span><span class="sxs-lookup"><span data-stu-id="ba274-122">RecordNumber</span></span>|<span data-ttu-id="ba274-123">xs:String</span><span class="sxs-lookup"><span data-stu-id="ba274-123">xs:string</span></span>|<span data-ttu-id="ba274-124">Liczba rekordów śledzenia.</span><span class="sxs-lookup"><span data-stu-id="ba274-124">The tracking record number.</span></span>|  
|<span data-ttu-id="ba274-125">Identyfikator dostawcy</span><span class="sxs-lookup"><span data-stu-id="ba274-125">ProviderId</span></span>|<span data-ttu-id="ba274-126">xs:String</span><span class="sxs-lookup"><span data-stu-id="ba274-126">xs:string</span></span>|<span data-ttu-id="ba274-127">Identyfikator dostawcy ETW.</span><span class="sxs-lookup"><span data-stu-id="ba274-127">The ETW provider id.</span></span>|  
|<span data-ttu-id="ba274-128">Domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="ba274-128">AppDomain</span></span>|<span data-ttu-id="ba274-129">xs:String</span><span class="sxs-lookup"><span data-stu-id="ba274-129">xs:string</span></span>|<span data-ttu-id="ba274-130">Długość ciągu zwróconego przez AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="ba274-130">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
