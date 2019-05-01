---
title: 39456 — TrackingRecordDropped
ms.date: 03/30/2017
ms.assetid: da13d5bc-1736-47a4-b3fd-064ca8040326
ms.openlocfilehash: f117c7759bab1759a7d614db275de88f8b37c331
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61774429"
---
# <a name="39456---trackingrecorddropped"></a><span data-ttu-id="ce0f8-102">39456 — TrackingRecordDropped</span><span class="sxs-lookup"><span data-stu-id="ce0f8-102">39456 - TrackingRecordDropped</span></span>
## <a name="properties"></a><span data-ttu-id="ce0f8-103">Właściwości</span><span class="sxs-lookup"><span data-stu-id="ce0f8-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="ce0f8-104">Identyfikator</span><span class="sxs-lookup"><span data-stu-id="ce0f8-104">ID</span></span>|<span data-ttu-id="ce0f8-105">39456</span><span class="sxs-lookup"><span data-stu-id="ce0f8-105">39456</span></span>|  
|<span data-ttu-id="ce0f8-106">słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="ce0f8-106">Keywords</span></span>|<span data-ttu-id="ce0f8-107">WFTracking</span><span class="sxs-lookup"><span data-stu-id="ce0f8-107">WFTracking</span></span>|  
|<span data-ttu-id="ce0f8-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="ce0f8-108">Level</span></span>|<span data-ttu-id="ce0f8-109">Ostrzeżenie</span><span class="sxs-lookup"><span data-stu-id="ce0f8-109">Warning</span></span>|  
|<span data-ttu-id="ce0f8-110">Kanał</span><span class="sxs-lookup"><span data-stu-id="ce0f8-110">Channel</span></span>|<span data-ttu-id="ce0f8-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="ce0f8-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="ce0f8-112">Opis</span><span class="sxs-lookup"><span data-stu-id="ce0f8-112">Description</span></span>  
 <span data-ttu-id="ce0f8-113">Wskazuje, że rekord śledzenia został porzucony, ponieważ jego rozmiar przekracza maksymalną dozwoloną przez dostawcę sesji funkcji ETW.</span><span class="sxs-lookup"><span data-stu-id="ce0f8-113">Indicates a tracking record has been dropped because its size exceeds maximum allowed by the ETW session provider.</span></span>  
  
## <a name="message"></a><span data-ttu-id="ce0f8-114">Komunikat</span><span class="sxs-lookup"><span data-stu-id="ce0f8-114">Message</span></span>  
 <span data-ttu-id="ce0f8-115">Rozmiar śledzenia rekord %1 przekracza maksymalną dozwoloną przez sesję funkcji ETW dla dostawcy %2</span><span class="sxs-lookup"><span data-stu-id="ce0f8-115">Size of tracking record %1 exceeds maximum allowed by the ETW session for provider %2</span></span>  
  
## <a name="details"></a><span data-ttu-id="ce0f8-116">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="ce0f8-116">Details</span></span>  
  
|<span data-ttu-id="ce0f8-117">Nazwa elementu danych</span><span class="sxs-lookup"><span data-stu-id="ce0f8-117">Data Item Name</span></span>|<span data-ttu-id="ce0f8-118">Typ elementu danych</span><span class="sxs-lookup"><span data-stu-id="ce0f8-118">Data Item Type</span></span>|<span data-ttu-id="ce0f8-119">Opis</span><span class="sxs-lookup"><span data-stu-id="ce0f8-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="ce0f8-120">Wyjątek</span><span class="sxs-lookup"><span data-stu-id="ce0f8-120">Exception</span></span>|<span data-ttu-id="ce0f8-121">xs:String</span><span class="sxs-lookup"><span data-stu-id="ce0f8-121">xs:string</span></span>|<span data-ttu-id="ce0f8-122">Szczegóły wyjątku, dla wyjątku</span><span class="sxs-lookup"><span data-stu-id="ce0f8-122">The exception details for the exception</span></span>|  
|<span data-ttu-id="ce0f8-123">AppDomain</span><span class="sxs-lookup"><span data-stu-id="ce0f8-123">AppDomain</span></span>|<span data-ttu-id="ce0f8-124">xs:String</span><span class="sxs-lookup"><span data-stu-id="ce0f8-124">xs:string</span></span>|<span data-ttu-id="ce0f8-125">Ciąg zwracany przez AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="ce0f8-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
