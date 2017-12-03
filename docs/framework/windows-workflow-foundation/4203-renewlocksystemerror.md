---
title: 4203 - RenewLockSystemError
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6ec9ec6f-4ae2-45cf-b99b-02cdb9dc9ec9
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 9c2214ec48f0c1cba1e3aacad0eaa5a29625f9c4
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="4203---renewlocksystemerror"></a><span data-ttu-id="b48f5-102">4203 - RenewLockSystemError</span><span class="sxs-lookup"><span data-stu-id="b48f5-102">4203 - RenewLockSystemError</span></span>
## <a name="properties"></a><span data-ttu-id="b48f5-103">Właściwości</span><span class="sxs-lookup"><span data-stu-id="b48f5-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="b48f5-104">ID</span><span class="sxs-lookup"><span data-stu-id="b48f5-104">ID</span></span>|<span data-ttu-id="b48f5-105">4203</span><span class="sxs-lookup"><span data-stu-id="b48f5-105">4203</span></span>|  
|<span data-ttu-id="b48f5-106">Słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="b48f5-106">Keywords</span></span>|<span data-ttu-id="b48f5-107">WFInstanceStore</span><span class="sxs-lookup"><span data-stu-id="b48f5-107">WFInstanceStore</span></span>|  
|<span data-ttu-id="b48f5-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="b48f5-108">Level</span></span>|<span data-ttu-id="b48f5-109">Błąd</span><span class="sxs-lookup"><span data-stu-id="b48f5-109">Error</span></span>|  
|<span data-ttu-id="b48f5-110">Kanał</span><span class="sxs-lookup"><span data-stu-id="b48f5-110">Channel</span></span>|<span data-ttu-id="b48f5-111">Microsoft-Windows aplikacji debugowania serwera — aplikacje</span><span class="sxs-lookup"><span data-stu-id="b48f5-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="b48f5-112">Opis</span><span class="sxs-lookup"><span data-stu-id="b48f5-112">Description</span></span>  
 <span data-ttu-id="b48f5-113">Wskazuje dostawcy SQL można przedłużyć okresu ważności blokady z powodu albo okresu ważności blokady już minęła lub właściciel blokady został usunięty.</span><span class="sxs-lookup"><span data-stu-id="b48f5-113">Indicates SQL provider has failed to extend lock expiration due to either lock expiration already passed or the lock owner was deleted.</span></span> <span data-ttu-id="b48f5-114">Obiekt SqlWorkflowInstanceStore zostanie przerwane.</span><span class="sxs-lookup"><span data-stu-id="b48f5-114">The SqlWorkflowInstanceStore will be aborted.</span></span>  
  
## <a name="message"></a><span data-ttu-id="b48f5-115">Komunikat</span><span class="sxs-lookup"><span data-stu-id="b48f5-115">Message</span></span>  
 <span data-ttu-id="b48f5-116">Nie można przedłużyć okresu ważności blokady, blokada już wygasła lub właściciel blokady został usunięty.</span><span class="sxs-lookup"><span data-stu-id="b48f5-116">Failed to extend lock expiration, lock expiration already passed or the lock owner was deleted.</span></span> <span data-ttu-id="b48f5-117">Trwa przerywanie SqlWorkflowInstanceStore.</span><span class="sxs-lookup"><span data-stu-id="b48f5-117">Aborting SqlWorkflowInstanceStore.</span></span>  
  
## <a name="details"></a><span data-ttu-id="b48f5-118">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="b48f5-118">Details</span></span>  
  
|<span data-ttu-id="b48f5-119">Nazwa elementu danych</span><span class="sxs-lookup"><span data-stu-id="b48f5-119">Data Item Name</span></span>|<span data-ttu-id="b48f5-120">Typ elementu danych</span><span class="sxs-lookup"><span data-stu-id="b48f5-120">Data Item Type</span></span>|<span data-ttu-id="b48f5-121">Opis</span><span class="sxs-lookup"><span data-stu-id="b48f5-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="b48f5-122">Domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="b48f5-122">AppDomain</span></span>|<span data-ttu-id="b48f5-123">xs:String</span><span class="sxs-lookup"><span data-stu-id="b48f5-123">xs:string</span></span>|<span data-ttu-id="b48f5-124">Długość ciągu zwróconego przez AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="b48f5-124">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
