---
title: 3503 - DuplicateCorrelationQuery
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b857f8e6-ce4d-4da4-bc9d-6cd63fa558a4
caps.latest.revision: "2"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 60367b33e1e57cce8646b4fcde79c7d4fd20a4cc
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="3503---duplicatecorrelationquery"></a><span data-ttu-id="febb2-102">3503 - DuplicateCorrelationQuery</span><span class="sxs-lookup"><span data-stu-id="febb2-102">3503 - DuplicateCorrelationQuery</span></span>
## <a name="properties"></a><span data-ttu-id="febb2-103">Właściwości</span><span class="sxs-lookup"><span data-stu-id="febb2-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="febb2-104">ID</span><span class="sxs-lookup"><span data-stu-id="febb2-104">ID</span></span>|<span data-ttu-id="febb2-105">3503</span><span class="sxs-lookup"><span data-stu-id="febb2-105">3503</span></span>|  
|<span data-ttu-id="febb2-106">Słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="febb2-106">Keywords</span></span>|<span data-ttu-id="febb2-107">WFServices</span><span class="sxs-lookup"><span data-stu-id="febb2-107">WFServices</span></span>|  
|<span data-ttu-id="febb2-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="febb2-108">Level</span></span>|<span data-ttu-id="febb2-109">Ostrzeżenie</span><span class="sxs-lookup"><span data-stu-id="febb2-109">Warning</span></span>|  
|<span data-ttu-id="febb2-110">Kanał</span><span class="sxs-lookup"><span data-stu-id="febb2-110">Channel</span></span>|<span data-ttu-id="febb2-111">Microsoft-Windows aplikacji Server aplikacje/analityczne</span><span class="sxs-lookup"><span data-stu-id="febb2-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="febb2-112">Opis</span><span class="sxs-lookup"><span data-stu-id="febb2-112">Description</span></span>  
 <span data-ttu-id="febb2-113">Wskazuje, że znaleziono zduplikowane CorrelationQuery.</span><span class="sxs-lookup"><span data-stu-id="febb2-113">Indicates a duplicate CorrelationQuery was found.</span></span> <span data-ttu-id="febb2-114">Zduplikowane zapytanie nie zostanie użyte, podczas obliczania korelacji.</span><span class="sxs-lookup"><span data-stu-id="febb2-114">The duplicate query will not be used when calculating correlation.</span></span>  
  
## <a name="message"></a><span data-ttu-id="febb2-115">Komunikat</span><span class="sxs-lookup"><span data-stu-id="febb2-115">Message</span></span>  
 <span data-ttu-id="febb2-116">Znaleziono zduplikowane CorrelationQuery o Where = '%1'.</span><span class="sxs-lookup"><span data-stu-id="febb2-116">A duplicate CorrelationQuery was found with Where='%1'.</span></span> <span data-ttu-id="febb2-117">To zduplikowane zapytanie nie zostanie użyte podczas obliczania korelacji.</span><span class="sxs-lookup"><span data-stu-id="febb2-117">This duplicate query will not be used when calculating correlation.</span></span>  
  
## <a name="details"></a><span data-ttu-id="febb2-118">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="febb2-118">Details</span></span>  
  
|<span data-ttu-id="febb2-119">Nazwa elementu danych</span><span class="sxs-lookup"><span data-stu-id="febb2-119">Data Item Name</span></span>|<span data-ttu-id="febb2-120">Typ elementu danych</span><span class="sxs-lookup"><span data-stu-id="febb2-120">Data Item Type</span></span>|<span data-ttu-id="febb2-121">Opis</span><span class="sxs-lookup"><span data-stu-id="febb2-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="febb2-122">Gdzie</span><span class="sxs-lookup"><span data-stu-id="febb2-122">Where</span></span>|<span data-ttu-id="febb2-123">xs:String</span><span class="sxs-lookup"><span data-stu-id="febb2-123">xs:string</span></span>|<span data-ttu-id="febb2-124">Gdzie część zapytania korelacji.</span><span class="sxs-lookup"><span data-stu-id="febb2-124">The Where portion of the correlation query.</span></span>|  
|<span data-ttu-id="febb2-125">Domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="febb2-125">AppDomain</span></span>|<span data-ttu-id="febb2-126">xs:String</span><span class="sxs-lookup"><span data-stu-id="febb2-126">xs:string</span></span>|<span data-ttu-id="febb2-127">Długość ciągu zwróconego przez AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="febb2-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
