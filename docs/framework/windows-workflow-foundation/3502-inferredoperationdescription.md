---
title: 3502 - InferredOperationDescription
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6aebb614-3c72-4537-ba11-3cc7200ef1f1
caps.latest.revision: "2"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 044d67bc2b721451ade04947484899266d288d8c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="3502---inferredoperationdescription"></a><span data-ttu-id="e99dd-102">3502 - InferredOperationDescription</span><span class="sxs-lookup"><span data-stu-id="e99dd-102">3502 - InferredOperationDescription</span></span>
## <a name="properties"></a><span data-ttu-id="e99dd-103">Właściwości</span><span class="sxs-lookup"><span data-stu-id="e99dd-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="e99dd-104">ID</span><span class="sxs-lookup"><span data-stu-id="e99dd-104">ID</span></span>|<span data-ttu-id="e99dd-105">3502</span><span class="sxs-lookup"><span data-stu-id="e99dd-105">3502</span></span>|  
|<span data-ttu-id="e99dd-106">Słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="e99dd-106">Keywords</span></span>|<span data-ttu-id="e99dd-107">WFServices</span><span class="sxs-lookup"><span data-stu-id="e99dd-107">WFServices</span></span>|  
|<span data-ttu-id="e99dd-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="e99dd-108">Level</span></span>|<span data-ttu-id="e99dd-109">Informacje</span><span class="sxs-lookup"><span data-stu-id="e99dd-109">Information</span></span>|  
|<span data-ttu-id="e99dd-110">Kanał</span><span class="sxs-lookup"><span data-stu-id="e99dd-110">Channel</span></span>|<span data-ttu-id="e99dd-111">Microsoft-Windows aplikacji Server aplikacje/analityczne</span><span class="sxs-lookup"><span data-stu-id="e99dd-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="e99dd-112">Opis</span><span class="sxs-lookup"><span data-stu-id="e99dd-112">Description</span></span>  
 <span data-ttu-id="e99dd-113">Wskazuje, że OperationDescription został wywnioskowany na podstawie obiektu WorkflowService.</span><span class="sxs-lookup"><span data-stu-id="e99dd-113">Indicates an OperationDescription has been inferred from WorkflowService.</span></span>  
  
## <a name="message"></a><span data-ttu-id="e99dd-114">Komunikat</span><span class="sxs-lookup"><span data-stu-id="e99dd-114">Message</span></span>  
 <span data-ttu-id="e99dd-115">OperationDescription o nazwie "% 1" w kontrakcie "%2" został wywnioskowany na podstawie obiektu WorkflowService.</span><span class="sxs-lookup"><span data-stu-id="e99dd-115">OperationDescription with Name='%1' in contract '%2' has been inferred from WorkflowService.</span></span> <span data-ttu-id="e99dd-116">Ustawienie właściwości IsOneWay = %3.</span><span class="sxs-lookup"><span data-stu-id="e99dd-116">IsOneWay=%3.</span></span>  
  
## <a name="details"></a><span data-ttu-id="e99dd-117">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="e99dd-117">Details</span></span>  
  
|<span data-ttu-id="e99dd-118">Nazwa elementu danych</span><span class="sxs-lookup"><span data-stu-id="e99dd-118">Data Item Name</span></span>|<span data-ttu-id="e99dd-119">Typ elementu danych</span><span class="sxs-lookup"><span data-stu-id="e99dd-119">Data Item Type</span></span>|<span data-ttu-id="e99dd-120">Opis</span><span class="sxs-lookup"><span data-stu-id="e99dd-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="e99dd-121">OperationName</span><span class="sxs-lookup"><span data-stu-id="e99dd-121">OperationName</span></span>|<span data-ttu-id="e99dd-122">xs:String</span><span class="sxs-lookup"><span data-stu-id="e99dd-122">xs:string</span></span>|<span data-ttu-id="e99dd-123">Nazwa operacji.</span><span class="sxs-lookup"><span data-stu-id="e99dd-123">The name of the operation.</span></span>|  
|<span data-ttu-id="e99dd-124">ContractName</span><span class="sxs-lookup"><span data-stu-id="e99dd-124">ContractName</span></span>|<span data-ttu-id="e99dd-125">xs:String</span><span class="sxs-lookup"><span data-stu-id="e99dd-125">xs:string</span></span>|<span data-ttu-id="e99dd-126">Nazwa kontraktu.</span><span class="sxs-lookup"><span data-stu-id="e99dd-126">The name of the contract.</span></span>|  
|<span data-ttu-id="e99dd-127">Ustawienie właściwości IsOneWay</span><span class="sxs-lookup"><span data-stu-id="e99dd-127">IsOneWay</span></span>|<span data-ttu-id="e99dd-128">xs:String</span><span class="sxs-lookup"><span data-stu-id="e99dd-128">xs:string</span></span>|<span data-ttu-id="e99dd-129">Wartość PRAWDA lub Fałsz wskazująca, czy kontrakt jest jednokierunkowa.</span><span class="sxs-lookup"><span data-stu-id="e99dd-129">True or False indicating if the contract is one-way.</span></span>|  
|<span data-ttu-id="e99dd-130">Domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="e99dd-130">AppDomain</span></span>|<span data-ttu-id="e99dd-131">xs:String</span><span class="sxs-lookup"><span data-stu-id="e99dd-131">xs:string</span></span>|<span data-ttu-id="e99dd-132">Długość ciągu zwróconego przez AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="e99dd-132">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
