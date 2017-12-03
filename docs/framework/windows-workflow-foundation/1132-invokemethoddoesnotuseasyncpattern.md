---
title: 1132 - InvokeMethodDoesNotUseAsyncPattern
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 436b3767-4460-46b0-9ea3-fc2963260c11
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 321d8c6185c8d24b7a3b6e255e235c36c119ff21
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="1132---invokemethoddoesnotuseasyncpattern"></a><span data-ttu-id="3d512-102">1132 - InvokeMethodDoesNotUseAsyncPattern</span><span class="sxs-lookup"><span data-stu-id="3d512-102">1132 - InvokeMethodDoesNotUseAsyncPattern</span></span>
## <a name="properties"></a><span data-ttu-id="3d512-103">Właściwości</span><span class="sxs-lookup"><span data-stu-id="3d512-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="3d512-104">ID</span><span class="sxs-lookup"><span data-stu-id="3d512-104">ID</span></span>|<span data-ttu-id="3d512-105">1132</span><span class="sxs-lookup"><span data-stu-id="3d512-105">1132</span></span>|  
|<span data-ttu-id="3d512-106">Słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="3d512-106">Keywords</span></span>|<span data-ttu-id="3d512-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="3d512-107">WFRuntime</span></span>|  
|<span data-ttu-id="3d512-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="3d512-108">Level</span></span>|<span data-ttu-id="3d512-109">Informacje</span><span class="sxs-lookup"><span data-stu-id="3d512-109">Information</span></span>|  
|<span data-ttu-id="3d512-110">Kanał</span><span class="sxs-lookup"><span data-stu-id="3d512-110">Channel</span></span>|<span data-ttu-id="3d512-111">Microsoft-Windows aplikacji debugowania serwera — aplikacje</span><span class="sxs-lookup"><span data-stu-id="3d512-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="3d512-112">Opis</span><span class="sxs-lookup"><span data-stu-id="3d512-112">Description</span></span>  
 <span data-ttu-id="3d512-113">Podczas wykonywania kroku CacheMetadata działania InvokeMethod wskazuje, czy nie używa wzorca asynchronicznego podczas wywoływania metody.</span><span class="sxs-lookup"><span data-stu-id="3d512-113">During CacheMetadata step, InvokeMethod activity indicates that it is not using the async pattern when invoking the method.</span></span>  
  
## <a name="message"></a><span data-ttu-id="3d512-114">Komunikat</span><span class="sxs-lookup"><span data-stu-id="3d512-114">Message</span></span>  
 <span data-ttu-id="3d512-115">InvokeMethod "%1" — metoda nie korzysta ze wzorca asynchronicznego.</span><span class="sxs-lookup"><span data-stu-id="3d512-115">InvokeMethod '%1' - method does not use asynchronous pattern.</span></span>  
  
## <a name="details"></a><span data-ttu-id="3d512-116">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="3d512-116">Details</span></span>  
  
|<span data-ttu-id="3d512-117">Nazwa elementu danych</span><span class="sxs-lookup"><span data-stu-id="3d512-117">Data Item Name</span></span>|<span data-ttu-id="3d512-118">Typ elementu danych</span><span class="sxs-lookup"><span data-stu-id="3d512-118">Data Item Type</span></span>|<span data-ttu-id="3d512-119">Opis</span><span class="sxs-lookup"><span data-stu-id="3d512-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="3d512-120">InvokeMethod</span><span class="sxs-lookup"><span data-stu-id="3d512-120">InvokeMethod</span></span>|<span data-ttu-id="3d512-121">xs:String</span><span class="sxs-lookup"><span data-stu-id="3d512-121">xs:string</span></span>|<span data-ttu-id="3d512-122">Nazwa wyświetlana InvokeMethod działania.</span><span class="sxs-lookup"><span data-stu-id="3d512-122">The display name of the InvokeMethod activity.</span></span>|  
|<span data-ttu-id="3d512-123">Domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="3d512-123">AppDomain</span></span>|<span data-ttu-id="3d512-124">xs:String</span><span class="sxs-lookup"><span data-stu-id="3d512-124">xs:string</span></span>|<span data-ttu-id="3d512-125">Długość ciągu zwróconego przez AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="3d512-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
