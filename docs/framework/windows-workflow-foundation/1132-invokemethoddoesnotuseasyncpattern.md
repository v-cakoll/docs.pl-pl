---
title: 1132 - InvokeMethodDoesNotUseAsyncPattern
ms.date: 03/30/2017
ms.assetid: 436b3767-4460-46b0-9ea3-fc2963260c11
ms.openlocfilehash: 64701d4c38c042e8273129be19f9caeb2c442abf
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="1132---invokemethoddoesnotuseasyncpattern"></a><span data-ttu-id="97cab-102">1132 - InvokeMethodDoesNotUseAsyncPattern</span><span class="sxs-lookup"><span data-stu-id="97cab-102">1132 - InvokeMethodDoesNotUseAsyncPattern</span></span>
## <a name="properties"></a><span data-ttu-id="97cab-103">Właściwości</span><span class="sxs-lookup"><span data-stu-id="97cab-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="97cab-104">ID</span><span class="sxs-lookup"><span data-stu-id="97cab-104">ID</span></span>|<span data-ttu-id="97cab-105">1132</span><span class="sxs-lookup"><span data-stu-id="97cab-105">1132</span></span>|  
|<span data-ttu-id="97cab-106">Słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="97cab-106">Keywords</span></span>|<span data-ttu-id="97cab-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="97cab-107">WFRuntime</span></span>|  
|<span data-ttu-id="97cab-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="97cab-108">Level</span></span>|<span data-ttu-id="97cab-109">Informacje</span><span class="sxs-lookup"><span data-stu-id="97cab-109">Information</span></span>|  
|<span data-ttu-id="97cab-110">Kanał</span><span class="sxs-lookup"><span data-stu-id="97cab-110">Channel</span></span>|<span data-ttu-id="97cab-111">Microsoft-Windows aplikacji debugowania serwera — aplikacje</span><span class="sxs-lookup"><span data-stu-id="97cab-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="97cab-112">Opis</span><span class="sxs-lookup"><span data-stu-id="97cab-112">Description</span></span>  
 <span data-ttu-id="97cab-113">Podczas wykonywania kroku CacheMetadata działania InvokeMethod wskazuje, czy nie używa wzorca asynchronicznego podczas wywoływania metody.</span><span class="sxs-lookup"><span data-stu-id="97cab-113">During CacheMetadata step, InvokeMethod activity indicates that it is not using the async pattern when invoking the method.</span></span>  
  
## <a name="message"></a><span data-ttu-id="97cab-114">Komunikat</span><span class="sxs-lookup"><span data-stu-id="97cab-114">Message</span></span>  
 <span data-ttu-id="97cab-115">InvokeMethod "%1" — metoda nie korzysta ze wzorca asynchronicznego.</span><span class="sxs-lookup"><span data-stu-id="97cab-115">InvokeMethod '%1' - method does not use asynchronous pattern.</span></span>  
  
## <a name="details"></a><span data-ttu-id="97cab-116">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="97cab-116">Details</span></span>  
  
|<span data-ttu-id="97cab-117">Nazwa elementu danych</span><span class="sxs-lookup"><span data-stu-id="97cab-117">Data Item Name</span></span>|<span data-ttu-id="97cab-118">Typ elementu danych</span><span class="sxs-lookup"><span data-stu-id="97cab-118">Data Item Type</span></span>|<span data-ttu-id="97cab-119">Opis</span><span class="sxs-lookup"><span data-stu-id="97cab-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="97cab-120">InvokeMethod</span><span class="sxs-lookup"><span data-stu-id="97cab-120">InvokeMethod</span></span>|<span data-ttu-id="97cab-121">xs:String</span><span class="sxs-lookup"><span data-stu-id="97cab-121">xs:string</span></span>|<span data-ttu-id="97cab-122">Nazwa wyświetlana InvokeMethod działania.</span><span class="sxs-lookup"><span data-stu-id="97cab-122">The display name of the InvokeMethod activity.</span></span>|  
|<span data-ttu-id="97cab-123">Domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="97cab-123">AppDomain</span></span>|<span data-ttu-id="97cab-124">xs:String</span><span class="sxs-lookup"><span data-stu-id="97cab-124">xs:string</span></span>|<span data-ttu-id="97cab-125">Długość ciągu zwróconego przez AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="97cab-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
