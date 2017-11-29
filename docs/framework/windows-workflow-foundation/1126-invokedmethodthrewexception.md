---
title: 1126 - InvokedMethodThrewException
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0d3cff1a-97e6-4b6c-be18-108c6881bfc0
caps.latest.revision: "2"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: b11c2f167ce7afce992cddb2f32f840212d4ac8d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="1126---invokedmethodthrewexception"></a><span data-ttu-id="b5cc8-102">1126 - InvokedMethodThrewException</span><span class="sxs-lookup"><span data-stu-id="b5cc8-102">1126 - InvokedMethodThrewException</span></span>
## <a name="properties"></a><span data-ttu-id="b5cc8-103">Właściwości</span><span class="sxs-lookup"><span data-stu-id="b5cc8-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="b5cc8-104">ID</span><span class="sxs-lookup"><span data-stu-id="b5cc8-104">ID</span></span>|<span data-ttu-id="b5cc8-105">1126</span><span class="sxs-lookup"><span data-stu-id="b5cc8-105">1126</span></span>|  
|<span data-ttu-id="b5cc8-106">Słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="b5cc8-106">Keywords</span></span>|<span data-ttu-id="b5cc8-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="b5cc8-107">WFRuntime</span></span>|  
|<span data-ttu-id="b5cc8-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="b5cc8-108">Level</span></span>|<span data-ttu-id="b5cc8-109">Informacje</span><span class="sxs-lookup"><span data-stu-id="b5cc8-109">Information</span></span>|  
|<span data-ttu-id="b5cc8-110">Kanał</span><span class="sxs-lookup"><span data-stu-id="b5cc8-110">Channel</span></span>|<span data-ttu-id="b5cc8-111">Microsoft-Windows aplikacji debugowania serwera — aplikacje</span><span class="sxs-lookup"><span data-stu-id="b5cc8-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="b5cc8-112">Opis</span><span class="sxs-lookup"><span data-stu-id="b5cc8-112">Description</span></span>  
 <span data-ttu-id="b5cc8-113">Wskazuje, że wystąpił wyjątek w metodzie wywołanej przez działanie InvokeMethod.</span><span class="sxs-lookup"><span data-stu-id="b5cc8-113">Indicates an exception was thrown by the method called by the InvokeMethod activity.</span></span>  
  
## <a name="message"></a><span data-ttu-id="b5cc8-114">Komunikat</span><span class="sxs-lookup"><span data-stu-id="b5cc8-114">Message</span></span>  
 <span data-ttu-id="b5cc8-115">Wystąpił wyjątek w metodzie wywołanej przez działanie "%1".</span><span class="sxs-lookup"><span data-stu-id="b5cc8-115">An exception was thrown in the method called by the activity '%1'.</span></span> <span data-ttu-id="b5cc8-116">%2</span><span class="sxs-lookup"><span data-stu-id="b5cc8-116">%2</span></span>  
  
## <a name="details"></a><span data-ttu-id="b5cc8-117">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="b5cc8-117">Details</span></span>  
  
|<span data-ttu-id="b5cc8-118">Nazwa elementu danych</span><span class="sxs-lookup"><span data-stu-id="b5cc8-118">Data Item Name</span></span>|<span data-ttu-id="b5cc8-119">Typ elementu danych</span><span class="sxs-lookup"><span data-stu-id="b5cc8-119">Data Item Type</span></span>|<span data-ttu-id="b5cc8-120">Opis</span><span class="sxs-lookup"><span data-stu-id="b5cc8-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="b5cc8-121">InvokeMethod</span><span class="sxs-lookup"><span data-stu-id="b5cc8-121">InvokeMethod</span></span>|<span data-ttu-id="b5cc8-122">xs:String</span><span class="sxs-lookup"><span data-stu-id="b5cc8-122">xs:string</span></span>|<span data-ttu-id="b5cc8-123">Nazwa wyświetlana InvokeMethod działania.</span><span class="sxs-lookup"><span data-stu-id="b5cc8-123">The display name of the InvokeMethod activity.</span></span>|  
|<span data-ttu-id="b5cc8-124">Wyjątek</span><span class="sxs-lookup"><span data-stu-id="b5cc8-124">Exception</span></span>|<span data-ttu-id="b5cc8-125">xs:String</span><span class="sxs-lookup"><span data-stu-id="b5cc8-125">xs:string</span></span>|<span data-ttu-id="b5cc8-126">Szczegóły wyjątku dla wyjątku</span><span class="sxs-lookup"><span data-stu-id="b5cc8-126">The exception details for the exception</span></span>|  
|<span data-ttu-id="b5cc8-127">Domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="b5cc8-127">AppDomain</span></span>|<span data-ttu-id="b5cc8-128">xs:String</span><span class="sxs-lookup"><span data-stu-id="b5cc8-128">xs:string</span></span>|<span data-ttu-id="b5cc8-129">Długość ciągu zwróconego przez AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="b5cc8-129">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
