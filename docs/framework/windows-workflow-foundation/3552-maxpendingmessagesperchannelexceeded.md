---
title: 3552 — MaxPendingMessagesPerChannelExceeded
ms.date: 03/30/2017
ms.assetid: fc8309d9-eb3a-4636-a6f0-dd0018c1361d
ms.openlocfilehash: a163ed216cbdfbf2b9d77d25979733d6bdb121d3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61945941"
---
# <a name="3552---maxpendingmessagesperchannelexceeded"></a><span data-ttu-id="4894c-102">3552 — MaxPendingMessagesPerChannelExceeded</span><span class="sxs-lookup"><span data-stu-id="4894c-102">3552 - MaxPendingMessagesPerChannelExceeded</span></span>
## <a name="properties"></a><span data-ttu-id="4894c-103">Właściwości</span><span class="sxs-lookup"><span data-stu-id="4894c-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="4894c-104">Identyfikator</span><span class="sxs-lookup"><span data-stu-id="4894c-104">ID</span></span>|<span data-ttu-id="4894c-105">3552</span><span class="sxs-lookup"><span data-stu-id="4894c-105">3552</span></span>|  
|<span data-ttu-id="4894c-106">słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="4894c-106">Keywords</span></span>|<span data-ttu-id="4894c-107">Limit przydziału, WFServices</span><span class="sxs-lookup"><span data-stu-id="4894c-107">Quota, WFServices</span></span>|  
|<span data-ttu-id="4894c-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="4894c-108">Level</span></span>|<span data-ttu-id="4894c-109">Ostrzeżenie</span><span class="sxs-lookup"><span data-stu-id="4894c-109">Warning</span></span>|  
|<span data-ttu-id="4894c-110">Kanał</span><span class="sxs-lookup"><span data-stu-id="4894c-110">Channel</span></span>|<span data-ttu-id="4894c-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="4894c-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="4894c-112">Opis</span><span class="sxs-lookup"><span data-stu-id="4894c-112">Description</span></span>  
 <span data-ttu-id="4894c-113">Wskazuje ograniczania "MaxPendingMessagesPerChannel" Osiągnięto limit.</span><span class="sxs-lookup"><span data-stu-id="4894c-113">Indicates the throttle 'MaxPendingMessagesPerChannel' limit was hit.</span></span>  
  
## <a name="message"></a><span data-ttu-id="4894c-114">Komunikat</span><span class="sxs-lookup"><span data-stu-id="4894c-114">Message</span></span>  
 <span data-ttu-id="4894c-115">Ograniczenie "MaxPendingMessagesPerChannel" limit "%1" został trafiony.</span><span class="sxs-lookup"><span data-stu-id="4894c-115">The throttle 'MaxPendingMessagesPerChannel' limit of  '%1' was hit.</span></span> <span data-ttu-id="4894c-116">Aby zwiększyć ten limit, Dopasuj właściwość MaxPendingMessagesPerChannel BufferedReceiveServiceBehavior.</span><span class="sxs-lookup"><span data-stu-id="4894c-116">To increase this limit, adjust the MaxPendingMessagesPerChannel property on BufferedReceiveServiceBehavior.</span></span>  
  
## <a name="details"></a><span data-ttu-id="4894c-117">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="4894c-117">Details</span></span>  
  
|<span data-ttu-id="4894c-118">Nazwa elementu danych</span><span class="sxs-lookup"><span data-stu-id="4894c-118">Data Item Name</span></span>|<span data-ttu-id="4894c-119">Typ elementu danych</span><span class="sxs-lookup"><span data-stu-id="4894c-119">Data Item Type</span></span>|<span data-ttu-id="4894c-120">Opis</span><span class="sxs-lookup"><span data-stu-id="4894c-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="4894c-121">Limit</span><span class="sxs-lookup"><span data-stu-id="4894c-121">Limit</span></span>|<span data-ttu-id="4894c-122">xs:String</span><span class="sxs-lookup"><span data-stu-id="4894c-122">xs:string</span></span>|<span data-ttu-id="4894c-123">Limit przepustowości MaxPendingMessagesPerChannel.</span><span class="sxs-lookup"><span data-stu-id="4894c-123">The limit of the MaxPendingMessagesPerChannel throttle.</span></span>|  
|<span data-ttu-id="4894c-124">AppDomain</span><span class="sxs-lookup"><span data-stu-id="4894c-124">AppDomain</span></span>|<span data-ttu-id="4894c-125">xs:String</span><span class="sxs-lookup"><span data-stu-id="4894c-125">xs:string</span></span>|<span data-ttu-id="4894c-126">Ciąg zwracany przez AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="4894c-126">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
