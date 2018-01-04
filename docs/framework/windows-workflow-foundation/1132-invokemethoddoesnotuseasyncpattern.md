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
ms.workload: dotnet
ms.openlocfilehash: 75386b56f7926b9ddb883e0ca212d795898fe6f8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="1132---invokemethoddoesnotuseasyncpattern"></a><span data-ttu-id="256bd-102">1132 - InvokeMethodDoesNotUseAsyncPattern</span><span class="sxs-lookup"><span data-stu-id="256bd-102">1132 - InvokeMethodDoesNotUseAsyncPattern</span></span>
## <a name="properties"></a><span data-ttu-id="256bd-103">Właściwości</span><span class="sxs-lookup"><span data-stu-id="256bd-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="256bd-104">ID</span><span class="sxs-lookup"><span data-stu-id="256bd-104">ID</span></span>|<span data-ttu-id="256bd-105">1132</span><span class="sxs-lookup"><span data-stu-id="256bd-105">1132</span></span>|  
|<span data-ttu-id="256bd-106">Słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="256bd-106">Keywords</span></span>|<span data-ttu-id="256bd-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="256bd-107">WFRuntime</span></span>|  
|<span data-ttu-id="256bd-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="256bd-108">Level</span></span>|<span data-ttu-id="256bd-109">Informacje</span><span class="sxs-lookup"><span data-stu-id="256bd-109">Information</span></span>|  
|<span data-ttu-id="256bd-110">Kanał</span><span class="sxs-lookup"><span data-stu-id="256bd-110">Channel</span></span>|<span data-ttu-id="256bd-111">Microsoft-Windows aplikacji debugowania serwera — aplikacje</span><span class="sxs-lookup"><span data-stu-id="256bd-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="256bd-112">Opis</span><span class="sxs-lookup"><span data-stu-id="256bd-112">Description</span></span>  
 <span data-ttu-id="256bd-113">Podczas wykonywania kroku CacheMetadata działania InvokeMethod wskazuje, czy nie używa wzorca asynchronicznego podczas wywoływania metody.</span><span class="sxs-lookup"><span data-stu-id="256bd-113">During CacheMetadata step, InvokeMethod activity indicates that it is not using the async pattern when invoking the method.</span></span>  
  
## <a name="message"></a><span data-ttu-id="256bd-114">Komunikat</span><span class="sxs-lookup"><span data-stu-id="256bd-114">Message</span></span>  
 <span data-ttu-id="256bd-115">InvokeMethod "%1" — metoda nie korzysta ze wzorca asynchronicznego.</span><span class="sxs-lookup"><span data-stu-id="256bd-115">InvokeMethod '%1' - method does not use asynchronous pattern.</span></span>  
  
## <a name="details"></a><span data-ttu-id="256bd-116">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="256bd-116">Details</span></span>  
  
|<span data-ttu-id="256bd-117">Nazwa elementu danych</span><span class="sxs-lookup"><span data-stu-id="256bd-117">Data Item Name</span></span>|<span data-ttu-id="256bd-118">Typ elementu danych</span><span class="sxs-lookup"><span data-stu-id="256bd-118">Data Item Type</span></span>|<span data-ttu-id="256bd-119">Opis</span><span class="sxs-lookup"><span data-stu-id="256bd-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="256bd-120">InvokeMethod</span><span class="sxs-lookup"><span data-stu-id="256bd-120">InvokeMethod</span></span>|<span data-ttu-id="256bd-121">xs:String</span><span class="sxs-lookup"><span data-stu-id="256bd-121">xs:string</span></span>|<span data-ttu-id="256bd-122">Nazwa wyświetlana InvokeMethod działania.</span><span class="sxs-lookup"><span data-stu-id="256bd-122">The display name of the InvokeMethod activity.</span></span>|  
|<span data-ttu-id="256bd-123">Domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="256bd-123">AppDomain</span></span>|<span data-ttu-id="256bd-124">xs:String</span><span class="sxs-lookup"><span data-stu-id="256bd-124">xs:string</span></span>|<span data-ttu-id="256bd-125">Długość ciągu zwróconego przez AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="256bd-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
