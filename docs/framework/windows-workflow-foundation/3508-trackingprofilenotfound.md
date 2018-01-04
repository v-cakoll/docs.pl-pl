---
title: 3508 - TrackingProfileNotFound
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4cee3c4a-0490-4c94-aa19-ef7ce7287c02
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 34812b6ddefb69c053cfefa91d7227a7bf15f42e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="3508---trackingprofilenotfound"></a><span data-ttu-id="e5311-102">3508 - TrackingProfileNotFound</span><span class="sxs-lookup"><span data-stu-id="e5311-102">3508 - TrackingProfileNotFound</span></span>
## <a name="properties"></a><span data-ttu-id="e5311-103">Właściwości</span><span class="sxs-lookup"><span data-stu-id="e5311-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="e5311-104">ID</span><span class="sxs-lookup"><span data-stu-id="e5311-104">ID</span></span>|<span data-ttu-id="e5311-105">3508</span><span class="sxs-lookup"><span data-stu-id="e5311-105">3508</span></span>|  
|<span data-ttu-id="e5311-106">Słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="e5311-106">Keywords</span></span>|<span data-ttu-id="e5311-107">WFServices</span><span class="sxs-lookup"><span data-stu-id="e5311-107">WFServices</span></span>|  
|<span data-ttu-id="e5311-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="e5311-108">Level</span></span>|<span data-ttu-id="e5311-109">Pełny</span><span class="sxs-lookup"><span data-stu-id="e5311-109">Verbose</span></span>|  
|<span data-ttu-id="e5311-110">Kanał</span><span class="sxs-lookup"><span data-stu-id="e5311-110">Channel</span></span>|<span data-ttu-id="e5311-111">Microsoft-Windows aplikacji Server aplikacje/analityczne</span><span class="sxs-lookup"><span data-stu-id="e5311-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="e5311-112">Opis</span><span class="sxs-lookup"><span data-stu-id="e5311-112">Description</span></span>  
 <span data-ttu-id="e5311-113">Oznacza TrackingProfile nie został znaleziony w pliku konfiguracji lub obiekt ActivityDefinitionId jest niezgodny z profilu.</span><span class="sxs-lookup"><span data-stu-id="e5311-113">Indicates either a TrackingProfile is not found in the config file or the ActivityDefinitionId does not match the profile.</span></span>  
  
## <a name="message"></a><span data-ttu-id="e5311-114">Komunikat</span><span class="sxs-lookup"><span data-stu-id="e5311-114">Message</span></span>  
 <span data-ttu-id="e5311-115">TrackingProfile "%1" dla obiektu ActivityDefinitionId "%2" nie można odnaleźć.</span><span class="sxs-lookup"><span data-stu-id="e5311-115">TrackingProfile '%1' for the ActivityDefinitionId '%2' not found.</span></span> <span data-ttu-id="e5311-116">Nie można odnaleźć TrackingProfile w pliku konfiguracji, albo obiekt ActivityDefinitionId jest niezgodny.</span><span class="sxs-lookup"><span data-stu-id="e5311-116">Either the TrackingProfile is not found in the config file or the ActivityDefinitionId does not match.</span></span>  
  
## <a name="details"></a><span data-ttu-id="e5311-117">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="e5311-117">Details</span></span>  
  
|<span data-ttu-id="e5311-118">Nazwa elementu danych</span><span class="sxs-lookup"><span data-stu-id="e5311-118">Data Item Name</span></span>|<span data-ttu-id="e5311-119">Typ elementu danych</span><span class="sxs-lookup"><span data-stu-id="e5311-119">Data Item Type</span></span>|<span data-ttu-id="e5311-120">Opis</span><span class="sxs-lookup"><span data-stu-id="e5311-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="e5311-121">TrackingProfile</span><span class="sxs-lookup"><span data-stu-id="e5311-121">TrackingProfile</span></span>|<span data-ttu-id="e5311-122">xs:String</span><span class="sxs-lookup"><span data-stu-id="e5311-122">xs:string</span></span>|<span data-ttu-id="e5311-123">Nazwa profilu śledzenia.</span><span class="sxs-lookup"><span data-stu-id="e5311-123">The name of the tracking profile.</span></span>|  
|<span data-ttu-id="e5311-124">Obiekt ActivityDefinitionId</span><span class="sxs-lookup"><span data-stu-id="e5311-124">ActivityDefinitionId</span></span>|<span data-ttu-id="e5311-125">xs:String</span><span class="sxs-lookup"><span data-stu-id="e5311-125">xs:string</span></span>|<span data-ttu-id="e5311-126">Identyfikator definicji działania.</span><span class="sxs-lookup"><span data-stu-id="e5311-126">The activity definition id.</span></span>|  
|<span data-ttu-id="e5311-127">Domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="e5311-127">AppDomain</span></span>|<span data-ttu-id="e5311-128">xs:String</span><span class="sxs-lookup"><span data-stu-id="e5311-128">xs:string</span></span>|<span data-ttu-id="e5311-129">Długość ciągu zwróconego przez AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="e5311-129">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
