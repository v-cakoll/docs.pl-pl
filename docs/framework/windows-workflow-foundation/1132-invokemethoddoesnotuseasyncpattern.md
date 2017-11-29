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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 300e843529bfc76df4193b46cd713ce0bd9cdbfd
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="1132---invokemethoddoesnotuseasyncpattern"></a><span data-ttu-id="b61af-102">1132 - InvokeMethodDoesNotUseAsyncPattern</span><span class="sxs-lookup"><span data-stu-id="b61af-102">1132 - InvokeMethodDoesNotUseAsyncPattern</span></span>
## <a name="properties"></a><span data-ttu-id="b61af-103">Właściwości</span><span class="sxs-lookup"><span data-stu-id="b61af-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="b61af-104">ID</span><span class="sxs-lookup"><span data-stu-id="b61af-104">ID</span></span>|<span data-ttu-id="b61af-105">1132</span><span class="sxs-lookup"><span data-stu-id="b61af-105">1132</span></span>|  
|<span data-ttu-id="b61af-106">Słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="b61af-106">Keywords</span></span>|<span data-ttu-id="b61af-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="b61af-107">WFRuntime</span></span>|  
|<span data-ttu-id="b61af-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="b61af-108">Level</span></span>|<span data-ttu-id="b61af-109">Informacje</span><span class="sxs-lookup"><span data-stu-id="b61af-109">Information</span></span>|  
|<span data-ttu-id="b61af-110">Kanał</span><span class="sxs-lookup"><span data-stu-id="b61af-110">Channel</span></span>|<span data-ttu-id="b61af-111">Microsoft-Windows aplikacji debugowania serwera — aplikacje</span><span class="sxs-lookup"><span data-stu-id="b61af-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="b61af-112">Opis</span><span class="sxs-lookup"><span data-stu-id="b61af-112">Description</span></span>  
 <span data-ttu-id="b61af-113">Podczas wykonywania kroku CacheMetadata działania InvokeMethod wskazuje, czy nie używa wzorca asynchronicznego podczas wywoływania metody.</span><span class="sxs-lookup"><span data-stu-id="b61af-113">During CacheMetadata step, InvokeMethod activity indicates that it is not using the async pattern when invoking the method.</span></span>  
  
## <a name="message"></a><span data-ttu-id="b61af-114">Komunikat</span><span class="sxs-lookup"><span data-stu-id="b61af-114">Message</span></span>  
 <span data-ttu-id="b61af-115">InvokeMethod "%1" — metoda nie korzysta ze wzorca asynchronicznego.</span><span class="sxs-lookup"><span data-stu-id="b61af-115">InvokeMethod '%1' - method does not use asynchronous pattern.</span></span>  
  
## <a name="details"></a><span data-ttu-id="b61af-116">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="b61af-116">Details</span></span>  
  
|<span data-ttu-id="b61af-117">Nazwa elementu danych</span><span class="sxs-lookup"><span data-stu-id="b61af-117">Data Item Name</span></span>|<span data-ttu-id="b61af-118">Typ elementu danych</span><span class="sxs-lookup"><span data-stu-id="b61af-118">Data Item Type</span></span>|<span data-ttu-id="b61af-119">Opis</span><span class="sxs-lookup"><span data-stu-id="b61af-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="b61af-120">InvokeMethod</span><span class="sxs-lookup"><span data-stu-id="b61af-120">InvokeMethod</span></span>|<span data-ttu-id="b61af-121">xs:String</span><span class="sxs-lookup"><span data-stu-id="b61af-121">xs:string</span></span>|<span data-ttu-id="b61af-122">Nazwa wyświetlana InvokeMethod działania.</span><span class="sxs-lookup"><span data-stu-id="b61af-122">The display name of the InvokeMethod activity.</span></span>|  
|<span data-ttu-id="b61af-123">Domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="b61af-123">AppDomain</span></span>|<span data-ttu-id="b61af-124">xs:String</span><span class="sxs-lookup"><span data-stu-id="b61af-124">xs:string</span></span>|<span data-ttu-id="b61af-125">Długość ciągu zwróconego przez AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="b61af-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
