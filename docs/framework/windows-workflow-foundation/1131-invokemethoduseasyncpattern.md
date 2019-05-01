---
title: 1131 — InvokeMethodUseAsyncPattern
ms.date: 03/30/2017
ms.assetid: eca50fa7-5276-4759-ad1c-e490b9bd1f82
ms.openlocfilehash: 150973935d12455aa671043a619fbd6fd7e77425
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62009958"
---
# <a name="1131---invokemethoduseasyncpattern"></a><span data-ttu-id="7920c-102">1131 — InvokeMethodUseAsyncPattern</span><span class="sxs-lookup"><span data-stu-id="7920c-102">1131 - InvokeMethodUseAsyncPattern</span></span>
## <a name="properties"></a><span data-ttu-id="7920c-103">Właściwości</span><span class="sxs-lookup"><span data-stu-id="7920c-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="7920c-104">Identyfikator</span><span class="sxs-lookup"><span data-stu-id="7920c-104">ID</span></span>|<span data-ttu-id="7920c-105">1131</span><span class="sxs-lookup"><span data-stu-id="7920c-105">1131</span></span>|  
|<span data-ttu-id="7920c-106">słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="7920c-106">Keywords</span></span>|<span data-ttu-id="7920c-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="7920c-107">WFRuntime</span></span>|  
|<span data-ttu-id="7920c-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="7920c-108">Level</span></span>|<span data-ttu-id="7920c-109">Informacje</span><span class="sxs-lookup"><span data-stu-id="7920c-109">Information</span></span>|  
|<span data-ttu-id="7920c-110">Kanał</span><span class="sxs-lookup"><span data-stu-id="7920c-110">Channel</span></span>|<span data-ttu-id="7920c-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="7920c-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="7920c-112">Opis</span><span class="sxs-lookup"><span data-stu-id="7920c-112">Description</span></span>  
 <span data-ttu-id="7920c-113">Podczas wykonywania kroku użyciu metody CacheMetadata działania InvokeMethod wskazuje, że korzysta on wzorca asynchronicznego podczas wywoływania metody.</span><span class="sxs-lookup"><span data-stu-id="7920c-113">During CacheMetadata step, InvokeMethod activity indicates that it is using the async pattern when invoking the method.</span></span>  
  
## <a name="message"></a><span data-ttu-id="7920c-114">Komunikat</span><span class="sxs-lookup"><span data-stu-id="7920c-114">Message</span></span>  
 <span data-ttu-id="7920c-115">InvokeMethod "%1" - metoda używa wzorca asynchronicznego "%2" i "%3".</span><span class="sxs-lookup"><span data-stu-id="7920c-115">InvokeMethod '%1' - method uses asynchronous pattern of '%2' and '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="7920c-116">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="7920c-116">Details</span></span>  
  
|<span data-ttu-id="7920c-117">Nazwa elementu danych</span><span class="sxs-lookup"><span data-stu-id="7920c-117">Data Item Name</span></span>|<span data-ttu-id="7920c-118">Typ elementu danych</span><span class="sxs-lookup"><span data-stu-id="7920c-118">Data Item Type</span></span>|<span data-ttu-id="7920c-119">Opis</span><span class="sxs-lookup"><span data-stu-id="7920c-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="7920c-120">InvokeMethod</span><span class="sxs-lookup"><span data-stu-id="7920c-120">InvokeMethod</span></span>|<span data-ttu-id="7920c-121">xs:String</span><span class="sxs-lookup"><span data-stu-id="7920c-121">xs:string</span></span>|<span data-ttu-id="7920c-122">Nazwa wyświetlana działania InvokeMethod.</span><span class="sxs-lookup"><span data-stu-id="7920c-122">The display name of the InvokeMethod activity.</span></span>|  
|<span data-ttu-id="7920c-123">BeginMethod</span><span class="sxs-lookup"><span data-stu-id="7920c-123">BeginMethod</span></span>|<span data-ttu-id="7920c-124">xs:String</span><span class="sxs-lookup"><span data-stu-id="7920c-124">xs:string</span></span>|<span data-ttu-id="7920c-125">Nazwa metody begin.</span><span class="sxs-lookup"><span data-stu-id="7920c-125">The name of the begin method.</span></span>|  
|<span data-ttu-id="7920c-126">EndMethod</span><span class="sxs-lookup"><span data-stu-id="7920c-126">EndMethod</span></span>|<span data-ttu-id="7920c-127">xs:String</span><span class="sxs-lookup"><span data-stu-id="7920c-127">xs:string</span></span>|<span data-ttu-id="7920c-128">Nazwa metody end.</span><span class="sxs-lookup"><span data-stu-id="7920c-128">The name of the end method.</span></span>|  
|<span data-ttu-id="7920c-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="7920c-129">AppDomain</span></span>|<span data-ttu-id="7920c-130">xs:String</span><span class="sxs-lookup"><span data-stu-id="7920c-130">xs:string</span></span>|<span data-ttu-id="7920c-131">Ciąg zwracany przez AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="7920c-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
