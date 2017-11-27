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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 06d4695eb125475f41a94c7f2266df6d2c3f400d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="4203---renewlocksystemerror"></a><span data-ttu-id="8a8a7-102">4203 - RenewLockSystemError</span><span class="sxs-lookup"><span data-stu-id="8a8a7-102">4203 - RenewLockSystemError</span></span>
## <a name="properties"></a><span data-ttu-id="8a8a7-103">Właściwości</span><span class="sxs-lookup"><span data-stu-id="8a8a7-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="8a8a7-104">ID</span><span class="sxs-lookup"><span data-stu-id="8a8a7-104">ID</span></span>|<span data-ttu-id="8a8a7-105">4203</span><span class="sxs-lookup"><span data-stu-id="8a8a7-105">4203</span></span>|  
|<span data-ttu-id="8a8a7-106">Słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="8a8a7-106">Keywords</span></span>|<span data-ttu-id="8a8a7-107">WFInstanceStore</span><span class="sxs-lookup"><span data-stu-id="8a8a7-107">WFInstanceStore</span></span>|  
|<span data-ttu-id="8a8a7-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="8a8a7-108">Level</span></span>|<span data-ttu-id="8a8a7-109">Błąd</span><span class="sxs-lookup"><span data-stu-id="8a8a7-109">Error</span></span>|  
|<span data-ttu-id="8a8a7-110">Kanał</span><span class="sxs-lookup"><span data-stu-id="8a8a7-110">Channel</span></span>|<span data-ttu-id="8a8a7-111">Microsoft-Windows aplikacji debugowania serwera — aplikacje</span><span class="sxs-lookup"><span data-stu-id="8a8a7-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="8a8a7-112">Opis</span><span class="sxs-lookup"><span data-stu-id="8a8a7-112">Description</span></span>  
 <span data-ttu-id="8a8a7-113">Wskazuje dostawcy SQL można przedłużyć okresu ważności blokady z powodu albo okresu ważności blokady już minęła lub właściciel blokady został usunięty.</span><span class="sxs-lookup"><span data-stu-id="8a8a7-113">Indicates SQL provider has failed to extend lock expiration due to either lock expiration already passed or the lock owner was deleted.</span></span> <span data-ttu-id="8a8a7-114">Obiekt SqlWorkflowInstanceStore zostanie przerwane.</span><span class="sxs-lookup"><span data-stu-id="8a8a7-114">The SqlWorkflowInstanceStore will be aborted.</span></span>  
  
## <a name="message"></a><span data-ttu-id="8a8a7-115">Komunikat</span><span class="sxs-lookup"><span data-stu-id="8a8a7-115">Message</span></span>  
 <span data-ttu-id="8a8a7-116">Nie można przedłużyć okresu ważności blokady, blokada już wygasła lub właściciel blokady został usunięty.</span><span class="sxs-lookup"><span data-stu-id="8a8a7-116">Failed to extend lock expiration, lock expiration already passed or the lock owner was deleted.</span></span> <span data-ttu-id="8a8a7-117">Trwa przerywanie SqlWorkflowInstanceStore.</span><span class="sxs-lookup"><span data-stu-id="8a8a7-117">Aborting SqlWorkflowInstanceStore.</span></span>  
  
## <a name="details"></a><span data-ttu-id="8a8a7-118">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="8a8a7-118">Details</span></span>  
  
|<span data-ttu-id="8a8a7-119">Nazwa elementu danych</span><span class="sxs-lookup"><span data-stu-id="8a8a7-119">Data Item Name</span></span>|<span data-ttu-id="8a8a7-120">Typ elementu danych</span><span class="sxs-lookup"><span data-stu-id="8a8a7-120">Data Item Type</span></span>|<span data-ttu-id="8a8a7-121">Opis</span><span class="sxs-lookup"><span data-stu-id="8a8a7-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="8a8a7-122">Domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="8a8a7-122">AppDomain</span></span>|<span data-ttu-id="8a8a7-123">xs:String</span><span class="sxs-lookup"><span data-stu-id="8a8a7-123">xs:string</span></span>|<span data-ttu-id="8a8a7-124">Długość ciągu zwróconego przez AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="8a8a7-124">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
