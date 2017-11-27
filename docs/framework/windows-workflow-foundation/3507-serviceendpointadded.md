---
title: 3507 - ServiceEndpointAdded
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c068fc0e-07ee-4551-9824-ea7216e1fe37
caps.latest.revision: "2"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 463482bbcc659c6dba15b854ff06f41754f63ccc
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="3507---serviceendpointadded"></a><span data-ttu-id="c25cd-102">3507 - ServiceEndpointAdded</span><span class="sxs-lookup"><span data-stu-id="c25cd-102">3507 - ServiceEndpointAdded</span></span>
## <a name="properties"></a><span data-ttu-id="c25cd-103">Właściwości</span><span class="sxs-lookup"><span data-stu-id="c25cd-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="c25cd-104">ID</span><span class="sxs-lookup"><span data-stu-id="c25cd-104">ID</span></span>|<span data-ttu-id="c25cd-105">3507</span><span class="sxs-lookup"><span data-stu-id="c25cd-105">3507</span></span>|  
|<span data-ttu-id="c25cd-106">Słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="c25cd-106">Keywords</span></span>|<span data-ttu-id="c25cd-107">WFServices</span><span class="sxs-lookup"><span data-stu-id="c25cd-107">WFServices</span></span>|  
|<span data-ttu-id="c25cd-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="c25cd-108">Level</span></span>|<span data-ttu-id="c25cd-109">Informacje</span><span class="sxs-lookup"><span data-stu-id="c25cd-109">Information</span></span>|  
|<span data-ttu-id="c25cd-110">Kanał</span><span class="sxs-lookup"><span data-stu-id="c25cd-110">Channel</span></span>|<span data-ttu-id="c25cd-111">Microsoft-Windows aplikacji Server aplikacje/analityczne</span><span class="sxs-lookup"><span data-stu-id="c25cd-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="c25cd-112">Opis</span><span class="sxs-lookup"><span data-stu-id="c25cd-112">Description</span></span>  
 <span data-ttu-id="c25cd-113">Wskazuje, że dodano punkt końcowy usługi.</span><span class="sxs-lookup"><span data-stu-id="c25cd-113">Indicates a service endpoint has been added.</span></span>  
  
## <a name="message"></a><span data-ttu-id="c25cd-114">Komunikat</span><span class="sxs-lookup"><span data-stu-id="c25cd-114">Message</span></span>  
 <span data-ttu-id="c25cd-115">Punkt końcowy usługi został dodany dla adresu "%1", powiązania "%2" i kontraktu "%3".</span><span class="sxs-lookup"><span data-stu-id="c25cd-115">A service endpoint has been added for address '%1', binding '%2', and contract '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="c25cd-116">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="c25cd-116">Details</span></span>  
  
|<span data-ttu-id="c25cd-117">Nazwa elementu danych</span><span class="sxs-lookup"><span data-stu-id="c25cd-117">Data Item Name</span></span>|<span data-ttu-id="c25cd-118">Typ elementu danych</span><span class="sxs-lookup"><span data-stu-id="c25cd-118">Data Item Type</span></span>|<span data-ttu-id="c25cd-119">Opis</span><span class="sxs-lookup"><span data-stu-id="c25cd-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="c25cd-120">Adres</span><span class="sxs-lookup"><span data-stu-id="c25cd-120">Address</span></span>|<span data-ttu-id="c25cd-121">xs:String</span><span class="sxs-lookup"><span data-stu-id="c25cd-121">xs:string</span></span>|<span data-ttu-id="c25cd-122">Adres punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="c25cd-122">The address of the endpoint.</span></span>|  
|<span data-ttu-id="c25cd-123">Powiązanie</span><span class="sxs-lookup"><span data-stu-id="c25cd-123">Binding</span></span>|<span data-ttu-id="c25cd-124">xs:String</span><span class="sxs-lookup"><span data-stu-id="c25cd-124">xs:string</span></span>|<span data-ttu-id="c25cd-125">Powiązanie punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="c25cd-125">The binding of the endpoint.</span></span>|  
|<span data-ttu-id="c25cd-126">Kontrakt</span><span class="sxs-lookup"><span data-stu-id="c25cd-126">Contract</span></span>|<span data-ttu-id="c25cd-127">xs:String</span><span class="sxs-lookup"><span data-stu-id="c25cd-127">xs:string</span></span>|<span data-ttu-id="c25cd-128">Kontrakt punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="c25cd-128">The contract of the endpoint.</span></span>|  
|<span data-ttu-id="c25cd-129">Domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="c25cd-129">AppDomain</span></span>|<span data-ttu-id="c25cd-130">xs:String</span><span class="sxs-lookup"><span data-stu-id="c25cd-130">xs:string</span></span>|<span data-ttu-id="c25cd-131">Długość ciągu zwróconego przez AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="c25cd-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
