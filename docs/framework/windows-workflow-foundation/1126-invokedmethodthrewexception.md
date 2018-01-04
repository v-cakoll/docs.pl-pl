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
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5dc752a5c9d5bebe39a4d4be2c3642333aa041de
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="1126---invokedmethodthrewexception"></a><span data-ttu-id="7d7cc-102">1126 - InvokedMethodThrewException</span><span class="sxs-lookup"><span data-stu-id="7d7cc-102">1126 - InvokedMethodThrewException</span></span>
## <a name="properties"></a><span data-ttu-id="7d7cc-103">Właściwości</span><span class="sxs-lookup"><span data-stu-id="7d7cc-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="7d7cc-104">ID</span><span class="sxs-lookup"><span data-stu-id="7d7cc-104">ID</span></span>|<span data-ttu-id="7d7cc-105">1126</span><span class="sxs-lookup"><span data-stu-id="7d7cc-105">1126</span></span>|  
|<span data-ttu-id="7d7cc-106">Słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="7d7cc-106">Keywords</span></span>|<span data-ttu-id="7d7cc-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="7d7cc-107">WFRuntime</span></span>|  
|<span data-ttu-id="7d7cc-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="7d7cc-108">Level</span></span>|<span data-ttu-id="7d7cc-109">Informacje</span><span class="sxs-lookup"><span data-stu-id="7d7cc-109">Information</span></span>|  
|<span data-ttu-id="7d7cc-110">Kanał</span><span class="sxs-lookup"><span data-stu-id="7d7cc-110">Channel</span></span>|<span data-ttu-id="7d7cc-111">Microsoft-Windows aplikacji debugowania serwera — aplikacje</span><span class="sxs-lookup"><span data-stu-id="7d7cc-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="7d7cc-112">Opis</span><span class="sxs-lookup"><span data-stu-id="7d7cc-112">Description</span></span>  
 <span data-ttu-id="7d7cc-113">Wskazuje, że wystąpił wyjątek w metodzie wywołanej przez działanie InvokeMethod.</span><span class="sxs-lookup"><span data-stu-id="7d7cc-113">Indicates an exception was thrown by the method called by the InvokeMethod activity.</span></span>  
  
## <a name="message"></a><span data-ttu-id="7d7cc-114">Komunikat</span><span class="sxs-lookup"><span data-stu-id="7d7cc-114">Message</span></span>  
 <span data-ttu-id="7d7cc-115">Wystąpił wyjątek w metodzie wywołanej przez działanie "%1".</span><span class="sxs-lookup"><span data-stu-id="7d7cc-115">An exception was thrown in the method called by the activity '%1'.</span></span> <span data-ttu-id="7d7cc-116">%2</span><span class="sxs-lookup"><span data-stu-id="7d7cc-116">%2</span></span>  
  
## <a name="details"></a><span data-ttu-id="7d7cc-117">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="7d7cc-117">Details</span></span>  
  
|<span data-ttu-id="7d7cc-118">Nazwa elementu danych</span><span class="sxs-lookup"><span data-stu-id="7d7cc-118">Data Item Name</span></span>|<span data-ttu-id="7d7cc-119">Typ elementu danych</span><span class="sxs-lookup"><span data-stu-id="7d7cc-119">Data Item Type</span></span>|<span data-ttu-id="7d7cc-120">Opis</span><span class="sxs-lookup"><span data-stu-id="7d7cc-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="7d7cc-121">InvokeMethod</span><span class="sxs-lookup"><span data-stu-id="7d7cc-121">InvokeMethod</span></span>|<span data-ttu-id="7d7cc-122">xs:String</span><span class="sxs-lookup"><span data-stu-id="7d7cc-122">xs:string</span></span>|<span data-ttu-id="7d7cc-123">Nazwa wyświetlana InvokeMethod działania.</span><span class="sxs-lookup"><span data-stu-id="7d7cc-123">The display name of the InvokeMethod activity.</span></span>|  
|<span data-ttu-id="7d7cc-124">Wyjątek</span><span class="sxs-lookup"><span data-stu-id="7d7cc-124">Exception</span></span>|<span data-ttu-id="7d7cc-125">xs:String</span><span class="sxs-lookup"><span data-stu-id="7d7cc-125">xs:string</span></span>|<span data-ttu-id="7d7cc-126">Szczegóły wyjątku dla wyjątku</span><span class="sxs-lookup"><span data-stu-id="7d7cc-126">The exception details for the exception</span></span>|  
|<span data-ttu-id="7d7cc-127">Domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="7d7cc-127">AppDomain</span></span>|<span data-ttu-id="7d7cc-128">xs:String</span><span class="sxs-lookup"><span data-stu-id="7d7cc-128">xs:string</span></span>|<span data-ttu-id="7d7cc-129">Długość ciągu zwróconego przez AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="7d7cc-129">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
