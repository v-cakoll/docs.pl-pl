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
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 997bdf4423364e9b5361635820849a6bde9e8960
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="3503---duplicatecorrelationquery"></a><span data-ttu-id="3eb28-102">3503 - DuplicateCorrelationQuery</span><span class="sxs-lookup"><span data-stu-id="3eb28-102">3503 - DuplicateCorrelationQuery</span></span>
## <a name="properties"></a><span data-ttu-id="3eb28-103">Właściwości</span><span class="sxs-lookup"><span data-stu-id="3eb28-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="3eb28-104">ID</span><span class="sxs-lookup"><span data-stu-id="3eb28-104">ID</span></span>|<span data-ttu-id="3eb28-105">3503</span><span class="sxs-lookup"><span data-stu-id="3eb28-105">3503</span></span>|  
|<span data-ttu-id="3eb28-106">Słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="3eb28-106">Keywords</span></span>|<span data-ttu-id="3eb28-107">WFServices</span><span class="sxs-lookup"><span data-stu-id="3eb28-107">WFServices</span></span>|  
|<span data-ttu-id="3eb28-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="3eb28-108">Level</span></span>|<span data-ttu-id="3eb28-109">Ostrzeżenie</span><span class="sxs-lookup"><span data-stu-id="3eb28-109">Warning</span></span>|  
|<span data-ttu-id="3eb28-110">Kanał</span><span class="sxs-lookup"><span data-stu-id="3eb28-110">Channel</span></span>|<span data-ttu-id="3eb28-111">Microsoft-Windows aplikacji Server aplikacje/analityczne</span><span class="sxs-lookup"><span data-stu-id="3eb28-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="3eb28-112">Opis</span><span class="sxs-lookup"><span data-stu-id="3eb28-112">Description</span></span>  
 <span data-ttu-id="3eb28-113">Wskazuje, że znaleziono zduplikowane CorrelationQuery.</span><span class="sxs-lookup"><span data-stu-id="3eb28-113">Indicates a duplicate CorrelationQuery was found.</span></span> <span data-ttu-id="3eb28-114">Zduplikowane zapytanie nie zostanie użyte, podczas obliczania korelacji.</span><span class="sxs-lookup"><span data-stu-id="3eb28-114">The duplicate query will not be used when calculating correlation.</span></span>  
  
## <a name="message"></a><span data-ttu-id="3eb28-115">Komunikat</span><span class="sxs-lookup"><span data-stu-id="3eb28-115">Message</span></span>  
 <span data-ttu-id="3eb28-116">Znaleziono zduplikowane CorrelationQuery o Where = '%1'.</span><span class="sxs-lookup"><span data-stu-id="3eb28-116">A duplicate CorrelationQuery was found with Where='%1'.</span></span> <span data-ttu-id="3eb28-117">To zduplikowane zapytanie nie zostanie użyte podczas obliczania korelacji.</span><span class="sxs-lookup"><span data-stu-id="3eb28-117">This duplicate query will not be used when calculating correlation.</span></span>  
  
## <a name="details"></a><span data-ttu-id="3eb28-118">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="3eb28-118">Details</span></span>  
  
|<span data-ttu-id="3eb28-119">Nazwa elementu danych</span><span class="sxs-lookup"><span data-stu-id="3eb28-119">Data Item Name</span></span>|<span data-ttu-id="3eb28-120">Typ elementu danych</span><span class="sxs-lookup"><span data-stu-id="3eb28-120">Data Item Type</span></span>|<span data-ttu-id="3eb28-121">Opis</span><span class="sxs-lookup"><span data-stu-id="3eb28-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="3eb28-122">Gdzie</span><span class="sxs-lookup"><span data-stu-id="3eb28-122">Where</span></span>|<span data-ttu-id="3eb28-123">xs:String</span><span class="sxs-lookup"><span data-stu-id="3eb28-123">xs:string</span></span>|<span data-ttu-id="3eb28-124">Gdzie część zapytania korelacji.</span><span class="sxs-lookup"><span data-stu-id="3eb28-124">The Where portion of the correlation query.</span></span>|  
|<span data-ttu-id="3eb28-125">Domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="3eb28-125">AppDomain</span></span>|<span data-ttu-id="3eb28-126">xs:String</span><span class="sxs-lookup"><span data-stu-id="3eb28-126">xs:string</span></span>|<span data-ttu-id="3eb28-127">Długość ciągu zwróconego przez AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="3eb28-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
