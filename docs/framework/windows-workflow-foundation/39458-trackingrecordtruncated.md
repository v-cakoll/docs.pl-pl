---
title: 39458 — TrackingRecordTruncated
ms.date: 03/30/2017
ms.assetid: 5352f0eb-d571-454a-bab5-e2162888b218
ms.openlocfilehash: 416feb4073b31178b016ae72c9cd85e15c4a68c3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61774416"
---
# <a name="39458---trackingrecordtruncated"></a><span data-ttu-id="0723a-102">39458 — TrackingRecordTruncated</span><span class="sxs-lookup"><span data-stu-id="0723a-102">39458 - TrackingRecordTruncated</span></span>
## <a name="properties"></a><span data-ttu-id="0723a-103">Właściwości</span><span class="sxs-lookup"><span data-stu-id="0723a-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="0723a-104">Identyfikator</span><span class="sxs-lookup"><span data-stu-id="0723a-104">ID</span></span>|<span data-ttu-id="0723a-105">39458</span><span class="sxs-lookup"><span data-stu-id="0723a-105">39458</span></span>|  
|<span data-ttu-id="0723a-106">słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="0723a-106">Keywords</span></span>|<span data-ttu-id="0723a-107">WFTracking</span><span class="sxs-lookup"><span data-stu-id="0723a-107">WFTracking</span></span>|  
|<span data-ttu-id="0723a-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="0723a-108">Level</span></span>|<span data-ttu-id="0723a-109">Ostrzeżenie</span><span class="sxs-lookup"><span data-stu-id="0723a-109">Warning</span></span>|  
|<span data-ttu-id="0723a-110">Kanał</span><span class="sxs-lookup"><span data-stu-id="0723a-110">Channel</span></span>|<span data-ttu-id="0723a-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="0723a-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="0723a-112">Opis</span><span class="sxs-lookup"><span data-stu-id="0723a-112">Description</span></span>  
 <span data-ttu-id="0723a-113">Wskazuje, że rekord śledzenia zostały obcięte.</span><span class="sxs-lookup"><span data-stu-id="0723a-113">Indicates a tracking record has been truncated.</span></span> <span data-ttu-id="0723a-114">Dane adnotacje/zmienne/użytkownika zostały usunięte.</span><span class="sxs-lookup"><span data-stu-id="0723a-114">Variables/annotations/user data have been removed.</span></span>  
  
## <a name="message"></a><span data-ttu-id="0723a-115">Komunikat</span><span class="sxs-lookup"><span data-stu-id="0723a-115">Message</span></span>  
 <span data-ttu-id="0723a-116">Obcięte śledzenia rekord %1 zapisywane do sesji ETW za pomocą dostawcy %2.</span><span class="sxs-lookup"><span data-stu-id="0723a-116">Truncated tracking record %1 written to ETW session with provider %2.</span></span> <span data-ttu-id="0723a-117">Usunięto użytkownika/zmienne/adnotacji danych</span><span class="sxs-lookup"><span data-stu-id="0723a-117">Variables/annotations/user data have been removed</span></span>  
  
## <a name="details"></a><span data-ttu-id="0723a-118">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="0723a-118">Details</span></span>  
  
|<span data-ttu-id="0723a-119">Nazwa elementu danych</span><span class="sxs-lookup"><span data-stu-id="0723a-119">Data Item Name</span></span>|<span data-ttu-id="0723a-120">Typ elementu danych</span><span class="sxs-lookup"><span data-stu-id="0723a-120">Data Item Type</span></span>|<span data-ttu-id="0723a-121">Opis</span><span class="sxs-lookup"><span data-stu-id="0723a-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="0723a-122">RecordNumber</span><span class="sxs-lookup"><span data-stu-id="0723a-122">RecordNumber</span></span>|<span data-ttu-id="0723a-123">xs:String</span><span class="sxs-lookup"><span data-stu-id="0723a-123">xs:string</span></span>|<span data-ttu-id="0723a-124">Liczba rekordów śledzenia.</span><span class="sxs-lookup"><span data-stu-id="0723a-124">The tracking record number.</span></span>|  
|<span data-ttu-id="0723a-125">ProviderId</span><span class="sxs-lookup"><span data-stu-id="0723a-125">ProviderId</span></span>|<span data-ttu-id="0723a-126">xs:String</span><span class="sxs-lookup"><span data-stu-id="0723a-126">xs:string</span></span>|<span data-ttu-id="0723a-127">Identyfikator dostawcy funkcji ETW.</span><span class="sxs-lookup"><span data-stu-id="0723a-127">The ETW provider id.</span></span>|  
|<span data-ttu-id="0723a-128">AppDomain</span><span class="sxs-lookup"><span data-stu-id="0723a-128">AppDomain</span></span>|<span data-ttu-id="0723a-129">xs:String</span><span class="sxs-lookup"><span data-stu-id="0723a-129">xs:string</span></span>|<span data-ttu-id="0723a-130">Ciąg zwracany przez AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="0723a-130">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
