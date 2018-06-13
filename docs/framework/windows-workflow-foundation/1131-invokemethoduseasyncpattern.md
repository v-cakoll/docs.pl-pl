---
title: 1131 - InvokeMethodUseAsyncPattern
ms.date: 03/30/2017
ms.assetid: eca50fa7-5276-4759-ad1c-e490b9bd1f82
ms.openlocfilehash: 150973935d12455aa671043a619fbd6fd7e77425
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33512669"
---
# <a name="1131---invokemethoduseasyncpattern"></a><span data-ttu-id="21556-102">1131 - InvokeMethodUseAsyncPattern</span><span class="sxs-lookup"><span data-stu-id="21556-102">1131 - InvokeMethodUseAsyncPattern</span></span>
## <a name="properties"></a><span data-ttu-id="21556-103">Właściwości</span><span class="sxs-lookup"><span data-stu-id="21556-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="21556-104">ID</span><span class="sxs-lookup"><span data-stu-id="21556-104">ID</span></span>|<span data-ttu-id="21556-105">1131</span><span class="sxs-lookup"><span data-stu-id="21556-105">1131</span></span>|  
|<span data-ttu-id="21556-106">Słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="21556-106">Keywords</span></span>|<span data-ttu-id="21556-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="21556-107">WFRuntime</span></span>|  
|<span data-ttu-id="21556-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="21556-108">Level</span></span>|<span data-ttu-id="21556-109">Informacje</span><span class="sxs-lookup"><span data-stu-id="21556-109">Information</span></span>|  
|<span data-ttu-id="21556-110">Kanał</span><span class="sxs-lookup"><span data-stu-id="21556-110">Channel</span></span>|<span data-ttu-id="21556-111">Microsoft-Windows aplikacji debugowania serwera — aplikacje</span><span class="sxs-lookup"><span data-stu-id="21556-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="21556-112">Opis</span><span class="sxs-lookup"><span data-stu-id="21556-112">Description</span></span>  
 <span data-ttu-id="21556-113">Podczas wykonywania kroku CacheMetadata działanie InvokeMethod wskazuje, że jest on używa wzorca asynchronicznego podczas wywoływania metody.</span><span class="sxs-lookup"><span data-stu-id="21556-113">During CacheMetadata step, InvokeMethod activity indicates that it is using the async pattern when invoking the method.</span></span>  
  
## <a name="message"></a><span data-ttu-id="21556-114">Komunikat</span><span class="sxs-lookup"><span data-stu-id="21556-114">Message</span></span>  
 <span data-ttu-id="21556-115">InvokeMethod "%1" — metoda korzysta ze wzorca asynchronicznego "%2" i "%3".</span><span class="sxs-lookup"><span data-stu-id="21556-115">InvokeMethod '%1' - method uses asynchronous pattern of '%2' and '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="21556-116">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="21556-116">Details</span></span>  
  
|<span data-ttu-id="21556-117">Nazwa elementu danych</span><span class="sxs-lookup"><span data-stu-id="21556-117">Data Item Name</span></span>|<span data-ttu-id="21556-118">Typ elementu danych</span><span class="sxs-lookup"><span data-stu-id="21556-118">Data Item Type</span></span>|<span data-ttu-id="21556-119">Opis</span><span class="sxs-lookup"><span data-stu-id="21556-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="21556-120">InvokeMethod</span><span class="sxs-lookup"><span data-stu-id="21556-120">InvokeMethod</span></span>|<span data-ttu-id="21556-121">xs:String</span><span class="sxs-lookup"><span data-stu-id="21556-121">xs:string</span></span>|<span data-ttu-id="21556-122">Nazwa wyświetlana InvokeMethod działania.</span><span class="sxs-lookup"><span data-stu-id="21556-122">The display name of the InvokeMethod activity.</span></span>|  
|<span data-ttu-id="21556-123">BeginMethod</span><span class="sxs-lookup"><span data-stu-id="21556-123">BeginMethod</span></span>|<span data-ttu-id="21556-124">xs:String</span><span class="sxs-lookup"><span data-stu-id="21556-124">xs:string</span></span>|<span data-ttu-id="21556-125">Nazwa metody begin.</span><span class="sxs-lookup"><span data-stu-id="21556-125">The name of the begin method.</span></span>|  
|<span data-ttu-id="21556-126">EndMethod</span><span class="sxs-lookup"><span data-stu-id="21556-126">EndMethod</span></span>|<span data-ttu-id="21556-127">xs:String</span><span class="sxs-lookup"><span data-stu-id="21556-127">xs:string</span></span>|<span data-ttu-id="21556-128">Nazwa metody end.</span><span class="sxs-lookup"><span data-stu-id="21556-128">The name of the end method.</span></span>|  
|<span data-ttu-id="21556-129">Domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="21556-129">AppDomain</span></span>|<span data-ttu-id="21556-130">xs:String</span><span class="sxs-lookup"><span data-stu-id="21556-130">xs:string</span></span>|<span data-ttu-id="21556-131">Długość ciągu zwróconego przez AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="21556-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
