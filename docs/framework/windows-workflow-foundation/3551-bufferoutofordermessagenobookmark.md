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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 9a380def22c270a3fafe118a426609a93862c447
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="3551---bufferoutofordermessagenobookmark"></a><span data-ttu-id="b84b7-102">3551 - BufferOutOfOrderMessageNoBookmark</span><span class="sxs-lookup"><span data-stu-id="b84b7-102">3551 - BufferOutOfOrderMessageNoBookmark</span></span>
## <a name="properties"></a><span data-ttu-id="b84b7-103">Właściwości</span><span class="sxs-lookup"><span data-stu-id="b84b7-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="b84b7-104">ID</span><span class="sxs-lookup"><span data-stu-id="b84b7-104">ID</span></span>|<span data-ttu-id="b84b7-105">3551</span><span class="sxs-lookup"><span data-stu-id="b84b7-105">3551</span></span>|  
|<span data-ttu-id="b84b7-106">Słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="b84b7-106">Keywords</span></span>|<span data-ttu-id="b84b7-107">WFServices</span><span class="sxs-lookup"><span data-stu-id="b84b7-107">WFServices</span></span>|  
|<span data-ttu-id="b84b7-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="b84b7-108">Level</span></span>|<span data-ttu-id="b84b7-109">Informacje</span><span class="sxs-lookup"><span data-stu-id="b84b7-109">Information</span></span>|  
|<span data-ttu-id="b84b7-110">Kanał</span><span class="sxs-lookup"><span data-stu-id="b84b7-110">Channel</span></span>|<span data-ttu-id="b84b7-111">Microsoft-Windows aplikacji Server aplikacje/analityczne</span><span class="sxs-lookup"><span data-stu-id="b84b7-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="b84b7-112">Opis</span><span class="sxs-lookup"><span data-stu-id="b84b7-112">Description</span></span>  
 <span data-ttu-id="b84b7-113">Wskazuje, że nie powiodło się wznowienie zakładki.</span><span class="sxs-lookup"><span data-stu-id="b84b7-113">Indicates a bookmark resumption has failed.</span></span> <span data-ttu-id="b84b7-114">Buforowany operacji odbierania zostanie podjęta ponownie gdy wystąpienie usługi będzie gotowe do przetworzenia tej operacji.</span><span class="sxs-lookup"><span data-stu-id="b84b7-114">The buffered receive operation will be attempted again when the service instance is ready to process this particular operation.</span></span>  
  
## <a name="message"></a><span data-ttu-id="b84b7-115">Komunikat</span><span class="sxs-lookup"><span data-stu-id="b84b7-115">Message</span></span>  
 <span data-ttu-id="b84b7-116">W tej chwili nie można wykonać operacji "%2" dla wystąpienia usługi "%1".</span><span class="sxs-lookup"><span data-stu-id="b84b7-116">Operation '%2' on service instance '%1' cannot be performed at this time.</span></span> <span data-ttu-id="b84b7-117">Kolejna próba zostanie podjęta, gdy wystąpienie usługi będzie gotowe do przetworzenia tej operacji.</span><span class="sxs-lookup"><span data-stu-id="b84b7-117">Another attempt will be made when the service instance is ready to process this particular operation.</span></span>  
  
## <a name="details"></a><span data-ttu-id="b84b7-118">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="b84b7-118">Details</span></span>  
  
|<span data-ttu-id="b84b7-119">Nazwa elementu danych</span><span class="sxs-lookup"><span data-stu-id="b84b7-119">Data Item Name</span></span>|<span data-ttu-id="b84b7-120">Typ elementu danych</span><span class="sxs-lookup"><span data-stu-id="b84b7-120">Data Item Type</span></span>|<span data-ttu-id="b84b7-121">Opis</span><span class="sxs-lookup"><span data-stu-id="b84b7-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="b84b7-122">OperationName</span><span class="sxs-lookup"><span data-stu-id="b84b7-122">OperationName</span></span>|<span data-ttu-id="b84b7-123">xs:String</span><span class="sxs-lookup"><span data-stu-id="b84b7-123">xs:string</span></span>|<span data-ttu-id="b84b7-124">Nazwa operacji.</span><span class="sxs-lookup"><span data-stu-id="b84b7-124">The name of the operation.</span></span>|  
|<span data-ttu-id="b84b7-125">ServiceInstanceId</span><span class="sxs-lookup"><span data-stu-id="b84b7-125">ServiceInstanceId</span></span>|<span data-ttu-id="b84b7-126">xs:String</span><span class="sxs-lookup"><span data-stu-id="b84b7-126">xs:string</span></span>|<span data-ttu-id="b84b7-127">Identyfikator wystąpienia usługi.</span><span class="sxs-lookup"><span data-stu-id="b84b7-127">The id of the service instance.</span></span>|  
|<span data-ttu-id="b84b7-128">Domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="b84b7-128">AppDomain</span></span>|<span data-ttu-id="b84b7-129">xs:String</span><span class="sxs-lookup"><span data-stu-id="b84b7-129">xs:string</span></span>|<span data-ttu-id="b84b7-130">Długość ciągu zwróconego przez AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="b84b7-130">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
