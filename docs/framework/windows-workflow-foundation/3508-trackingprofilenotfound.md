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
ms.openlocfilehash: 346cb98b1285883a9a85f2c7abb6147f42734395
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="3508---trackingprofilenotfound"></a><span data-ttu-id="ced97-102">3508 - TrackingProfileNotFound</span><span class="sxs-lookup"><span data-stu-id="ced97-102">3508 - TrackingProfileNotFound</span></span>
## <a name="properties"></a><span data-ttu-id="ced97-103">Właściwości</span><span class="sxs-lookup"><span data-stu-id="ced97-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="ced97-104">ID</span><span class="sxs-lookup"><span data-stu-id="ced97-104">ID</span></span>|<span data-ttu-id="ced97-105">3508</span><span class="sxs-lookup"><span data-stu-id="ced97-105">3508</span></span>|  
|<span data-ttu-id="ced97-106">Słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="ced97-106">Keywords</span></span>|<span data-ttu-id="ced97-107">WFServices</span><span class="sxs-lookup"><span data-stu-id="ced97-107">WFServices</span></span>|  
|<span data-ttu-id="ced97-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="ced97-108">Level</span></span>|<span data-ttu-id="ced97-109">Pełny</span><span class="sxs-lookup"><span data-stu-id="ced97-109">Verbose</span></span>|  
|<span data-ttu-id="ced97-110">Kanał</span><span class="sxs-lookup"><span data-stu-id="ced97-110">Channel</span></span>|<span data-ttu-id="ced97-111">Microsoft-Windows aplikacji Server aplikacje/analityczne</span><span class="sxs-lookup"><span data-stu-id="ced97-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="ced97-112">Opis</span><span class="sxs-lookup"><span data-stu-id="ced97-112">Description</span></span>  
 <span data-ttu-id="ced97-113">Oznacza TrackingProfile nie został znaleziony w pliku konfiguracji lub obiekt ActivityDefinitionId jest niezgodny z profilu.</span><span class="sxs-lookup"><span data-stu-id="ced97-113">Indicates either a TrackingProfile is not found in the config file or the ActivityDefinitionId does not match the profile.</span></span>  
  
## <a name="message"></a><span data-ttu-id="ced97-114">Komunikat</span><span class="sxs-lookup"><span data-stu-id="ced97-114">Message</span></span>  
 <span data-ttu-id="ced97-115">TrackingProfile "%1" dla obiektu ActivityDefinitionId "%2" nie można odnaleźć.</span><span class="sxs-lookup"><span data-stu-id="ced97-115">TrackingProfile '%1' for the ActivityDefinitionId '%2' not found.</span></span> <span data-ttu-id="ced97-116">Nie można odnaleźć TrackingProfile w pliku konfiguracji, albo obiekt ActivityDefinitionId jest niezgodny.</span><span class="sxs-lookup"><span data-stu-id="ced97-116">Either the TrackingProfile is not found in the config file or the ActivityDefinitionId does not match.</span></span>  
  
## <a name="details"></a><span data-ttu-id="ced97-117">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="ced97-117">Details</span></span>  
  
|<span data-ttu-id="ced97-118">Nazwa elementu danych</span><span class="sxs-lookup"><span data-stu-id="ced97-118">Data Item Name</span></span>|<span data-ttu-id="ced97-119">Typ elementu danych</span><span class="sxs-lookup"><span data-stu-id="ced97-119">Data Item Type</span></span>|<span data-ttu-id="ced97-120">Opis</span><span class="sxs-lookup"><span data-stu-id="ced97-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="ced97-121">TrackingProfile</span><span class="sxs-lookup"><span data-stu-id="ced97-121">TrackingProfile</span></span>|<span data-ttu-id="ced97-122">xs:String</span><span class="sxs-lookup"><span data-stu-id="ced97-122">xs:string</span></span>|<span data-ttu-id="ced97-123">Nazwa profilu śledzenia.</span><span class="sxs-lookup"><span data-stu-id="ced97-123">The name of the tracking profile.</span></span>|  
|<span data-ttu-id="ced97-124">Obiekt ActivityDefinitionId</span><span class="sxs-lookup"><span data-stu-id="ced97-124">ActivityDefinitionId</span></span>|<span data-ttu-id="ced97-125">xs:String</span><span class="sxs-lookup"><span data-stu-id="ced97-125">xs:string</span></span>|<span data-ttu-id="ced97-126">Identyfikator definicji działania.</span><span class="sxs-lookup"><span data-stu-id="ced97-126">The activity definition id.</span></span>|  
|<span data-ttu-id="ced97-127">Domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="ced97-127">AppDomain</span></span>|<span data-ttu-id="ced97-128">xs:String</span><span class="sxs-lookup"><span data-stu-id="ced97-128">xs:string</span></span>|<span data-ttu-id="ced97-129">Długość ciągu zwróconego przez AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="ced97-129">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
