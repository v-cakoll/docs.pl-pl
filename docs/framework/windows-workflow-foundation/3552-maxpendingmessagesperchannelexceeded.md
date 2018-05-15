---
title: 3552 - MaxPendingMessagesPerChannelExceeded
ms.date: 03/30/2017
ms.assetid: fc8309d9-eb3a-4636-a6f0-dd0018c1361d
ms.openlocfilehash: a163ed216cbdfbf2b9d77d25979733d6bdb121d3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="3552---maxpendingmessagesperchannelexceeded"></a><span data-ttu-id="43e56-102">3552 - MaxPendingMessagesPerChannelExceeded</span><span class="sxs-lookup"><span data-stu-id="43e56-102">3552 - MaxPendingMessagesPerChannelExceeded</span></span>
## <a name="properties"></a><span data-ttu-id="43e56-103">Właściwości</span><span class="sxs-lookup"><span data-stu-id="43e56-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="43e56-104">ID</span><span class="sxs-lookup"><span data-stu-id="43e56-104">ID</span></span>|<span data-ttu-id="43e56-105">3552</span><span class="sxs-lookup"><span data-stu-id="43e56-105">3552</span></span>|  
|<span data-ttu-id="43e56-106">Słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="43e56-106">Keywords</span></span>|<span data-ttu-id="43e56-107">Limit przydziału, WFServices</span><span class="sxs-lookup"><span data-stu-id="43e56-107">Quota, WFServices</span></span>|  
|<span data-ttu-id="43e56-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="43e56-108">Level</span></span>|<span data-ttu-id="43e56-109">Ostrzeżenie</span><span class="sxs-lookup"><span data-stu-id="43e56-109">Warning</span></span>|  
|<span data-ttu-id="43e56-110">Kanał</span><span class="sxs-lookup"><span data-stu-id="43e56-110">Channel</span></span>|<span data-ttu-id="43e56-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="43e56-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="43e56-112">Opis</span><span class="sxs-lookup"><span data-stu-id="43e56-112">Description</span></span>  
 <span data-ttu-id="43e56-113">Wskazuje "MaxPendingMessagesPerChannel" Osiągnięto limit przepustnicy.</span><span class="sxs-lookup"><span data-stu-id="43e56-113">Indicates the throttle 'MaxPendingMessagesPerChannel' limit was hit.</span></span>  
  
## <a name="message"></a><span data-ttu-id="43e56-114">Komunikat</span><span class="sxs-lookup"><span data-stu-id="43e56-114">Message</span></span>  
 <span data-ttu-id="43e56-115">Osiągnięto przepustnicy "MaxPendingMessagesPerChannel" limit równy "%1".</span><span class="sxs-lookup"><span data-stu-id="43e56-115">The throttle 'MaxPendingMessagesPerChannel' limit of  '%1' was hit.</span></span> <span data-ttu-id="43e56-116">Aby zwiększyć ten limit, zmień właściwość MaxPendingMessagesPerChannel obiektu bufferedreceiveservicebehavior.</span><span class="sxs-lookup"><span data-stu-id="43e56-116">To increase this limit, adjust the MaxPendingMessagesPerChannel property on BufferedReceiveServiceBehavior.</span></span>  
  
## <a name="details"></a><span data-ttu-id="43e56-117">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="43e56-117">Details</span></span>  
  
|<span data-ttu-id="43e56-118">Nazwa elementu danych</span><span class="sxs-lookup"><span data-stu-id="43e56-118">Data Item Name</span></span>|<span data-ttu-id="43e56-119">Typ elementu danych</span><span class="sxs-lookup"><span data-stu-id="43e56-119">Data Item Type</span></span>|<span data-ttu-id="43e56-120">Opis</span><span class="sxs-lookup"><span data-stu-id="43e56-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="43e56-121">Limit</span><span class="sxs-lookup"><span data-stu-id="43e56-121">Limit</span></span>|<span data-ttu-id="43e56-122">xs:String</span><span class="sxs-lookup"><span data-stu-id="43e56-122">xs:string</span></span>|<span data-ttu-id="43e56-123">Limit przepustnicy MaxPendingMessagesPerChannel.</span><span class="sxs-lookup"><span data-stu-id="43e56-123">The limit of the MaxPendingMessagesPerChannel throttle.</span></span>|  
|<span data-ttu-id="43e56-124">Domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="43e56-124">AppDomain</span></span>|<span data-ttu-id="43e56-125">xs:String</span><span class="sxs-lookup"><span data-stu-id="43e56-125">xs:string</span></span>|<span data-ttu-id="43e56-126">Długość ciągu zwróconego przez AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="43e56-126">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
