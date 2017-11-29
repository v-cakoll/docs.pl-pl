---
title: 3552 - MaxPendingMessagesPerChannelExceeded
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fc8309d9-eb3a-4636-a6f0-dd0018c1361d
caps.latest.revision: "3"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 5ba5e4aa8e1338321838e40db7d976107315ef64
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="3552---maxpendingmessagesperchannelexceeded"></a><span data-ttu-id="1fffa-102">3552 - MaxPendingMessagesPerChannelExceeded</span><span class="sxs-lookup"><span data-stu-id="1fffa-102">3552 - MaxPendingMessagesPerChannelExceeded</span></span>
## <a name="properties"></a><span data-ttu-id="1fffa-103">Właściwości</span><span class="sxs-lookup"><span data-stu-id="1fffa-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="1fffa-104">ID</span><span class="sxs-lookup"><span data-stu-id="1fffa-104">ID</span></span>|<span data-ttu-id="1fffa-105">3552</span><span class="sxs-lookup"><span data-stu-id="1fffa-105">3552</span></span>|  
|<span data-ttu-id="1fffa-106">Słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="1fffa-106">Keywords</span></span>|<span data-ttu-id="1fffa-107">Limit przydziału, WFServices</span><span class="sxs-lookup"><span data-stu-id="1fffa-107">Quota, WFServices</span></span>|  
|<span data-ttu-id="1fffa-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="1fffa-108">Level</span></span>|<span data-ttu-id="1fffa-109">Ostrzeżenie</span><span class="sxs-lookup"><span data-stu-id="1fffa-109">Warning</span></span>|  
|<span data-ttu-id="1fffa-110">Kanał</span><span class="sxs-lookup"><span data-stu-id="1fffa-110">Channel</span></span>|<span data-ttu-id="1fffa-111">Microsoft-Windows aplikacji Server aplikacje/analityczne</span><span class="sxs-lookup"><span data-stu-id="1fffa-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="1fffa-112">Opis</span><span class="sxs-lookup"><span data-stu-id="1fffa-112">Description</span></span>  
 <span data-ttu-id="1fffa-113">Wskazuje "MaxPendingMessagesPerChannel" Osiągnięto limit przepustnicy.</span><span class="sxs-lookup"><span data-stu-id="1fffa-113">Indicates the throttle 'MaxPendingMessagesPerChannel' limit was hit.</span></span>  
  
## <a name="message"></a><span data-ttu-id="1fffa-114">Komunikat</span><span class="sxs-lookup"><span data-stu-id="1fffa-114">Message</span></span>  
 <span data-ttu-id="1fffa-115">Osiągnięto przepustnicy "MaxPendingMessagesPerChannel" limit równy "%1".</span><span class="sxs-lookup"><span data-stu-id="1fffa-115">The throttle 'MaxPendingMessagesPerChannel' limit of  '%1' was hit.</span></span> <span data-ttu-id="1fffa-116">Aby zwiększyć ten limit, zmień właściwość MaxPendingMessagesPerChannel obiektu bufferedreceiveservicebehavior.</span><span class="sxs-lookup"><span data-stu-id="1fffa-116">To increase this limit, adjust the MaxPendingMessagesPerChannel property on BufferedReceiveServiceBehavior.</span></span>  
  
## <a name="details"></a><span data-ttu-id="1fffa-117">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="1fffa-117">Details</span></span>  
  
|<span data-ttu-id="1fffa-118">Nazwa elementu danych</span><span class="sxs-lookup"><span data-stu-id="1fffa-118">Data Item Name</span></span>|<span data-ttu-id="1fffa-119">Typ elementu danych</span><span class="sxs-lookup"><span data-stu-id="1fffa-119">Data Item Type</span></span>|<span data-ttu-id="1fffa-120">Opis</span><span class="sxs-lookup"><span data-stu-id="1fffa-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="1fffa-121">Limit</span><span class="sxs-lookup"><span data-stu-id="1fffa-121">Limit</span></span>|<span data-ttu-id="1fffa-122">xs:String</span><span class="sxs-lookup"><span data-stu-id="1fffa-122">xs:string</span></span>|<span data-ttu-id="1fffa-123">Limit przepustnicy MaxPendingMessagesPerChannel.</span><span class="sxs-lookup"><span data-stu-id="1fffa-123">The limit of the MaxPendingMessagesPerChannel throttle.</span></span>|  
|<span data-ttu-id="1fffa-124">Domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="1fffa-124">AppDomain</span></span>|<span data-ttu-id="1fffa-125">xs:String</span><span class="sxs-lookup"><span data-stu-id="1fffa-125">xs:string</span></span>|<span data-ttu-id="1fffa-126">Długość ciągu zwróconego przez AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="1fffa-126">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
