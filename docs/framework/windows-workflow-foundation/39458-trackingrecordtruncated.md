---
title: 39458 - TrackingRecordTruncated
ms.date: 03/30/2017
ms.assetid: 5352f0eb-d571-454a-bab5-e2162888b218
ms.openlocfilehash: 416feb4073b31178b016ae72c9cd85e15c4a68c3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33514485"
---
# <a name="39458---trackingrecordtruncated"></a><span data-ttu-id="01665-102">39458 - TrackingRecordTruncated</span><span class="sxs-lookup"><span data-stu-id="01665-102">39458 - TrackingRecordTruncated</span></span>
## <a name="properties"></a><span data-ttu-id="01665-103">Właściwości</span><span class="sxs-lookup"><span data-stu-id="01665-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="01665-104">ID</span><span class="sxs-lookup"><span data-stu-id="01665-104">ID</span></span>|<span data-ttu-id="01665-105">39458</span><span class="sxs-lookup"><span data-stu-id="01665-105">39458</span></span>|  
|<span data-ttu-id="01665-106">Słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="01665-106">Keywords</span></span>|<span data-ttu-id="01665-107">WFTracking</span><span class="sxs-lookup"><span data-stu-id="01665-107">WFTracking</span></span>|  
|<span data-ttu-id="01665-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="01665-108">Level</span></span>|<span data-ttu-id="01665-109">Ostrzeżenie</span><span class="sxs-lookup"><span data-stu-id="01665-109">Warning</span></span>|  
|<span data-ttu-id="01665-110">Kanał</span><span class="sxs-lookup"><span data-stu-id="01665-110">Channel</span></span>|<span data-ttu-id="01665-111">Microsoft-Windows aplikacji debugowania serwera — aplikacje</span><span class="sxs-lookup"><span data-stu-id="01665-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="01665-112">Opis</span><span class="sxs-lookup"><span data-stu-id="01665-112">Description</span></span>  
 <span data-ttu-id="01665-113">Wskazuje, że został obcięty rekord śledzenia.</span><span class="sxs-lookup"><span data-stu-id="01665-113">Indicates a tracking record has been truncated.</span></span> <span data-ttu-id="01665-114">Zmienne/adnotacje/dane użytkownika zostały usunięte.</span><span class="sxs-lookup"><span data-stu-id="01665-114">Variables/annotations/user data have been removed.</span></span>  
  
## <a name="message"></a><span data-ttu-id="01665-115">Komunikat</span><span class="sxs-lookup"><span data-stu-id="01665-115">Message</span></span>  
 <span data-ttu-id="01665-116">Obcięty rekord śledzenia %1 został zapisany w sesji usługi ETW za pomocą dostawcy %2.</span><span class="sxs-lookup"><span data-stu-id="01665-116">Truncated tracking record %1 written to ETW session with provider %2.</span></span> <span data-ttu-id="01665-117">Zmienne/adnotacje/dane użytkownika zostały usunięte</span><span class="sxs-lookup"><span data-stu-id="01665-117">Variables/annotations/user data have been removed</span></span>  
  
## <a name="details"></a><span data-ttu-id="01665-118">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="01665-118">Details</span></span>  
  
|<span data-ttu-id="01665-119">Nazwa elementu danych</span><span class="sxs-lookup"><span data-stu-id="01665-119">Data Item Name</span></span>|<span data-ttu-id="01665-120">Typ elementu danych</span><span class="sxs-lookup"><span data-stu-id="01665-120">Data Item Type</span></span>|<span data-ttu-id="01665-121">Opis</span><span class="sxs-lookup"><span data-stu-id="01665-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="01665-122">RecordNumber</span><span class="sxs-lookup"><span data-stu-id="01665-122">RecordNumber</span></span>|<span data-ttu-id="01665-123">xs:String</span><span class="sxs-lookup"><span data-stu-id="01665-123">xs:string</span></span>|<span data-ttu-id="01665-124">Liczba rekordów śledzenia.</span><span class="sxs-lookup"><span data-stu-id="01665-124">The tracking record number.</span></span>|  
|<span data-ttu-id="01665-125">Identyfikator dostawcy</span><span class="sxs-lookup"><span data-stu-id="01665-125">ProviderId</span></span>|<span data-ttu-id="01665-126">xs:String</span><span class="sxs-lookup"><span data-stu-id="01665-126">xs:string</span></span>|<span data-ttu-id="01665-127">Identyfikator dostawcy ETW.</span><span class="sxs-lookup"><span data-stu-id="01665-127">The ETW provider id.</span></span>|  
|<span data-ttu-id="01665-128">Domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="01665-128">AppDomain</span></span>|<span data-ttu-id="01665-129">xs:String</span><span class="sxs-lookup"><span data-stu-id="01665-129">xs:string</span></span>|<span data-ttu-id="01665-130">Długość ciągu zwróconego przez AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="01665-130">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
