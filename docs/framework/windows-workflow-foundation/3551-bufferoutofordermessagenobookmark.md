---
title: 3551 - BufferOutOfOrderMessageNoBookmark
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7930d6c4-c843-4a83-933a-cecd71b80d1e
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 6dc505a4e0e79b37f9adff41b80dcba55215576f
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="3551---bufferoutofordermessagenobookmark"></a><span data-ttu-id="f52cc-102">3551 - BufferOutOfOrderMessageNoBookmark</span><span class="sxs-lookup"><span data-stu-id="f52cc-102">3551 - BufferOutOfOrderMessageNoBookmark</span></span>
## <a name="properties"></a><span data-ttu-id="f52cc-103">Właściwości</span><span class="sxs-lookup"><span data-stu-id="f52cc-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="f52cc-104">ID</span><span class="sxs-lookup"><span data-stu-id="f52cc-104">ID</span></span>|<span data-ttu-id="f52cc-105">3551</span><span class="sxs-lookup"><span data-stu-id="f52cc-105">3551</span></span>|  
|<span data-ttu-id="f52cc-106">Słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="f52cc-106">Keywords</span></span>|<span data-ttu-id="f52cc-107">WFServices</span><span class="sxs-lookup"><span data-stu-id="f52cc-107">WFServices</span></span>|  
|<span data-ttu-id="f52cc-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="f52cc-108">Level</span></span>|<span data-ttu-id="f52cc-109">Informacje</span><span class="sxs-lookup"><span data-stu-id="f52cc-109">Information</span></span>|  
|<span data-ttu-id="f52cc-110">Kanał</span><span class="sxs-lookup"><span data-stu-id="f52cc-110">Channel</span></span>|<span data-ttu-id="f52cc-111">Microsoft-Windows aplikacji Server aplikacje/analityczne</span><span class="sxs-lookup"><span data-stu-id="f52cc-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="f52cc-112">Opis</span><span class="sxs-lookup"><span data-stu-id="f52cc-112">Description</span></span>  
 <span data-ttu-id="f52cc-113">Wskazuje, że nie powiodło się wznowienie zakładki.</span><span class="sxs-lookup"><span data-stu-id="f52cc-113">Indicates a bookmark resumption has failed.</span></span> <span data-ttu-id="f52cc-114">Buforowany operacji odbierania zostanie podjęta ponownie gdy wystąpienie usługi będzie gotowe do przetworzenia tej operacji.</span><span class="sxs-lookup"><span data-stu-id="f52cc-114">The buffered receive operation will be attempted again when the service instance is ready to process this particular operation.</span></span>  
  
## <a name="message"></a><span data-ttu-id="f52cc-115">Komunikat</span><span class="sxs-lookup"><span data-stu-id="f52cc-115">Message</span></span>  
 <span data-ttu-id="f52cc-116">W tej chwili nie można wykonać operacji "%2" dla wystąpienia usługi "%1".</span><span class="sxs-lookup"><span data-stu-id="f52cc-116">Operation '%2' on service instance '%1' cannot be performed at this time.</span></span> <span data-ttu-id="f52cc-117">Kolejna próba zostanie podjęta, gdy wystąpienie usługi będzie gotowe do przetworzenia tej operacji.</span><span class="sxs-lookup"><span data-stu-id="f52cc-117">Another attempt will be made when the service instance is ready to process this particular operation.</span></span>  
  
## <a name="details"></a><span data-ttu-id="f52cc-118">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="f52cc-118">Details</span></span>  
  
|<span data-ttu-id="f52cc-119">Nazwa elementu danych</span><span class="sxs-lookup"><span data-stu-id="f52cc-119">Data Item Name</span></span>|<span data-ttu-id="f52cc-120">Typ elementu danych</span><span class="sxs-lookup"><span data-stu-id="f52cc-120">Data Item Type</span></span>|<span data-ttu-id="f52cc-121">Opis</span><span class="sxs-lookup"><span data-stu-id="f52cc-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="f52cc-122">OperationName</span><span class="sxs-lookup"><span data-stu-id="f52cc-122">OperationName</span></span>|<span data-ttu-id="f52cc-123">xs:String</span><span class="sxs-lookup"><span data-stu-id="f52cc-123">xs:string</span></span>|<span data-ttu-id="f52cc-124">Nazwa operacji.</span><span class="sxs-lookup"><span data-stu-id="f52cc-124">The name of the operation.</span></span>|  
|<span data-ttu-id="f52cc-125">ServiceInstanceId</span><span class="sxs-lookup"><span data-stu-id="f52cc-125">ServiceInstanceId</span></span>|<span data-ttu-id="f52cc-126">xs:String</span><span class="sxs-lookup"><span data-stu-id="f52cc-126">xs:string</span></span>|<span data-ttu-id="f52cc-127">Identyfikator wystąpienia usługi.</span><span class="sxs-lookup"><span data-stu-id="f52cc-127">The id of the service instance.</span></span>|  
|<span data-ttu-id="f52cc-128">Domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="f52cc-128">AppDomain</span></span>|<span data-ttu-id="f52cc-129">xs:String</span><span class="sxs-lookup"><span data-stu-id="f52cc-129">xs:string</span></span>|<span data-ttu-id="f52cc-130">Długość ciągu zwróconego przez AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="f52cc-130">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
