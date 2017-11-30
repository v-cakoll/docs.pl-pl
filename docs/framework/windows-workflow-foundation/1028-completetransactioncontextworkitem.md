---
title: 1028 - CompleteTransactionContextWorkItem
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 95423f9d-d29a-460e-bcd8-096e80af5bd0
caps.latest.revision: "3"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 77ef22bd29c167b5be26ceb5360397d38c547c22
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="1028---completetransactioncontextworkitem"></a><span data-ttu-id="709ec-102">1028 - CompleteTransactionContextWorkItem</span><span class="sxs-lookup"><span data-stu-id="709ec-102">1028 - CompleteTransactionContextWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="709ec-103">Właściwości</span><span class="sxs-lookup"><span data-stu-id="709ec-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="709ec-104">ID</span><span class="sxs-lookup"><span data-stu-id="709ec-104">ID</span></span>|<span data-ttu-id="709ec-105">1028</span><span class="sxs-lookup"><span data-stu-id="709ec-105">1028</span></span>|  
|<span data-ttu-id="709ec-106">Słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="709ec-106">Keywords</span></span>|<span data-ttu-id="709ec-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="709ec-107">WFRuntime</span></span>|  
|<span data-ttu-id="709ec-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="709ec-108">Level</span></span>|<span data-ttu-id="709ec-109">Pełny</span><span class="sxs-lookup"><span data-stu-id="709ec-109">Verbose</span></span>|  
|<span data-ttu-id="709ec-110">Kanał</span><span class="sxs-lookup"><span data-stu-id="709ec-110">Channel</span></span>|<span data-ttu-id="709ec-111">Microsoft-Windows aplikacji debugowania serwera — aplikacje</span><span class="sxs-lookup"><span data-stu-id="709ec-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="709ec-112">Opis</span><span class="sxs-lookup"><span data-stu-id="709ec-112">Description</span></span>  
 <span data-ttu-id="709ec-113">Wskazuje, że Ukończono element roboczy TransactionContextWorkItem.</span><span class="sxs-lookup"><span data-stu-id="709ec-113">Indicates a TransactionContextWorkItem has completed.</span></span>  
  
## <a name="message"></a><span data-ttu-id="709ec-114">Komunikat</span><span class="sxs-lookup"><span data-stu-id="709ec-114">Message</span></span>  
 <span data-ttu-id="709ec-115">Ukończono element roboczy TransactionContextWorkItem dla działania %1, nazwa wyświetlana: %2, identyfikator wystąpienia: '%3'.</span><span class="sxs-lookup"><span data-stu-id="709ec-115">A TransactionContextWorkItem has completed for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="709ec-116">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="709ec-116">Details</span></span>  
  
|<span data-ttu-id="709ec-117">Nazwa elementu danych</span><span class="sxs-lookup"><span data-stu-id="709ec-117">Data Item Name</span></span>|<span data-ttu-id="709ec-118">Typ elementu danych</span><span class="sxs-lookup"><span data-stu-id="709ec-118">Data Item Type</span></span>|<span data-ttu-id="709ec-119">Opis</span><span class="sxs-lookup"><span data-stu-id="709ec-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="709ec-120">Działanie</span><span class="sxs-lookup"><span data-stu-id="709ec-120">Activity</span></span>|<span data-ttu-id="709ec-121">xs:String</span><span class="sxs-lookup"><span data-stu-id="709ec-121">xs:string</span></span>|<span data-ttu-id="709ec-122">Nazwa typu działania.</span><span class="sxs-lookup"><span data-stu-id="709ec-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="709ec-123">Nazwa wyświetlana</span><span class="sxs-lookup"><span data-stu-id="709ec-123">DisplayName</span></span>|<span data-ttu-id="709ec-124">xs:String</span><span class="sxs-lookup"><span data-stu-id="709ec-124">xs:string</span></span>|<span data-ttu-id="709ec-125">Nazwa wyświetlana działania.</span><span class="sxs-lookup"><span data-stu-id="709ec-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="709ec-126">Identyfikator wystąpienia</span><span class="sxs-lookup"><span data-stu-id="709ec-126">InstanceId</span></span>|<span data-ttu-id="709ec-127">xs:String</span><span class="sxs-lookup"><span data-stu-id="709ec-127">xs:string</span></span>|<span data-ttu-id="709ec-128">Identyfikator wystąpienia działania.</span><span class="sxs-lookup"><span data-stu-id="709ec-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="709ec-129">Domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="709ec-129">AppDomain</span></span>|<span data-ttu-id="709ec-130">xs:String</span><span class="sxs-lookup"><span data-stu-id="709ec-130">xs:string</span></span>|<span data-ttu-id="709ec-131">Długość ciągu zwróconego przez AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="709ec-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
