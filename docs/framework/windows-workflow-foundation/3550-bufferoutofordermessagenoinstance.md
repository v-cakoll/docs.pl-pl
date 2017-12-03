---
title: 3550 - BufferOutOfOrderMessageNoInstance
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1299d294-99b8-430e-98b1-55f5f17002f3
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: eabc6a6915560d8c49e695d5d681f1544689cb07
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="3550---bufferoutofordermessagenoinstance"></a><span data-ttu-id="c201f-102">3550 - BufferOutOfOrderMessageNoInstance</span><span class="sxs-lookup"><span data-stu-id="c201f-102">3550 - BufferOutOfOrderMessageNoInstance</span></span>
## <a name="properties"></a><span data-ttu-id="c201f-103">Właściwości</span><span class="sxs-lookup"><span data-stu-id="c201f-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="c201f-104">ID</span><span class="sxs-lookup"><span data-stu-id="c201f-104">ID</span></span>|<span data-ttu-id="c201f-105">3550</span><span class="sxs-lookup"><span data-stu-id="c201f-105">3550</span></span>|  
|<span data-ttu-id="c201f-106">Słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="c201f-106">Keywords</span></span>|<span data-ttu-id="c201f-107">WFServices</span><span class="sxs-lookup"><span data-stu-id="c201f-107">WFServices</span></span>|  
|<span data-ttu-id="c201f-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="c201f-108">Level</span></span>|<span data-ttu-id="c201f-109">Informacje</span><span class="sxs-lookup"><span data-stu-id="c201f-109">Information</span></span>|  
|<span data-ttu-id="c201f-110">Kanał</span><span class="sxs-lookup"><span data-stu-id="c201f-110">Channel</span></span>|<span data-ttu-id="c201f-111">Microsoft-Windows aplikacji Server aplikacje/analityczne</span><span class="sxs-lookup"><span data-stu-id="c201f-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="c201f-112">Opis</span><span class="sxs-lookup"><span data-stu-id="c201f-112">Description</span></span>  
 <span data-ttu-id="c201f-113">Wskazuje, że buforowanego receive nie powiodło się.</span><span class="sxs-lookup"><span data-stu-id="c201f-113">Indicates a buffered receive has failed.</span></span> <span data-ttu-id="c201f-114">Operacja zostanie podjęta ponownie, gdy wystąpienie usługi będzie gotowe do przetworzenia tej operacji.</span><span class="sxs-lookup"><span data-stu-id="c201f-114">The operation will be attempted again when the service instance is ready to process this particular operation.</span></span>  
  
## <a name="message"></a><span data-ttu-id="c201f-115">Komunikat</span><span class="sxs-lookup"><span data-stu-id="c201f-115">Message</span></span>  
 <span data-ttu-id="c201f-116">W tej chwili nie można wykonać operacji "%1".</span><span class="sxs-lookup"><span data-stu-id="c201f-116">Operation '%1' cannot be performed at this time.</span></span> <span data-ttu-id="c201f-117">Kolejna próba zostanie podjęta, gdy wystąpienie usługi będzie gotowe do przetworzenia tej operacji.</span><span class="sxs-lookup"><span data-stu-id="c201f-117">Another attempt will be made when the service instance is ready to process this particular operation.</span></span>  
  
## <a name="details"></a><span data-ttu-id="c201f-118">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="c201f-118">Details</span></span>  
  
|<span data-ttu-id="c201f-119">Nazwa elementu danych</span><span class="sxs-lookup"><span data-stu-id="c201f-119">Data Item Name</span></span>|<span data-ttu-id="c201f-120">Typ elementu danych</span><span class="sxs-lookup"><span data-stu-id="c201f-120">Data Item Type</span></span>|<span data-ttu-id="c201f-121">Opis</span><span class="sxs-lookup"><span data-stu-id="c201f-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="c201f-122">OperationName</span><span class="sxs-lookup"><span data-stu-id="c201f-122">OperationName</span></span>|<span data-ttu-id="c201f-123">xs:String</span><span class="sxs-lookup"><span data-stu-id="c201f-123">xs:string</span></span>|<span data-ttu-id="c201f-124">Nazwa operacji.</span><span class="sxs-lookup"><span data-stu-id="c201f-124">The name of the operation.</span></span>|  
|<span data-ttu-id="c201f-125">Domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="c201f-125">AppDomain</span></span>|<span data-ttu-id="c201f-126">xs:String</span><span class="sxs-lookup"><span data-stu-id="c201f-126">xs:string</span></span>|<span data-ttu-id="c201f-127">Długość ciągu zwróconego przez AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="c201f-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
