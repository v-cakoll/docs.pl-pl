---
title: 3503 — DuplicateCorrelationQuery
ms.date: 03/30/2017
ms.assetid: b857f8e6-ce4d-4da4-bc9d-6cd63fa558a4
ms.openlocfilehash: 37a689b30b0bcab9124472deb98627afbe30dfee
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61755600"
---
# <a name="3503---duplicatecorrelationquery"></a><span data-ttu-id="f2e53-102">3503 — DuplicateCorrelationQuery</span><span class="sxs-lookup"><span data-stu-id="f2e53-102">3503 - DuplicateCorrelationQuery</span></span>
## <a name="properties"></a><span data-ttu-id="f2e53-103">Właściwości</span><span class="sxs-lookup"><span data-stu-id="f2e53-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="f2e53-104">Identyfikator</span><span class="sxs-lookup"><span data-stu-id="f2e53-104">ID</span></span>|<span data-ttu-id="f2e53-105">3503</span><span class="sxs-lookup"><span data-stu-id="f2e53-105">3503</span></span>|  
|<span data-ttu-id="f2e53-106">słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="f2e53-106">Keywords</span></span>|<span data-ttu-id="f2e53-107">WFServices</span><span class="sxs-lookup"><span data-stu-id="f2e53-107">WFServices</span></span>|  
|<span data-ttu-id="f2e53-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="f2e53-108">Level</span></span>|<span data-ttu-id="f2e53-109">Ostrzeżenie</span><span class="sxs-lookup"><span data-stu-id="f2e53-109">Warning</span></span>|  
|<span data-ttu-id="f2e53-110">Kanał</span><span class="sxs-lookup"><span data-stu-id="f2e53-110">Channel</span></span>|<span data-ttu-id="f2e53-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="f2e53-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="f2e53-112">Opis</span><span class="sxs-lookup"><span data-stu-id="f2e53-112">Description</span></span>  
 <span data-ttu-id="f2e53-113">Wskazuje, że znaleziono zduplikowane CorrelationQuery.</span><span class="sxs-lookup"><span data-stu-id="f2e53-113">Indicates a duplicate CorrelationQuery was found.</span></span> <span data-ttu-id="f2e53-114">Zduplikowane zapytania nie będą używane, podczas obliczania korelacji.</span><span class="sxs-lookup"><span data-stu-id="f2e53-114">The duplicate query will not be used when calculating correlation.</span></span>  
  
## <a name="message"></a><span data-ttu-id="f2e53-115">Komunikat</span><span class="sxs-lookup"><span data-stu-id="f2e53-115">Message</span></span>  
 <span data-ttu-id="f2e53-116">Znaleziono zduplikowane CorrelationQuery, w której = "%1".</span><span class="sxs-lookup"><span data-stu-id="f2e53-116">A duplicate CorrelationQuery was found with Where='%1'.</span></span> <span data-ttu-id="f2e53-117">To zapytanie zduplikowane nie będzie używane, podczas obliczania korelacji.</span><span class="sxs-lookup"><span data-stu-id="f2e53-117">This duplicate query will not be used when calculating correlation.</span></span>  
  
## <a name="details"></a><span data-ttu-id="f2e53-118">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="f2e53-118">Details</span></span>  
  
|<span data-ttu-id="f2e53-119">Nazwa elementu danych</span><span class="sxs-lookup"><span data-stu-id="f2e53-119">Data Item Name</span></span>|<span data-ttu-id="f2e53-120">Typ elementu danych</span><span class="sxs-lookup"><span data-stu-id="f2e53-120">Data Item Type</span></span>|<span data-ttu-id="f2e53-121">Opis</span><span class="sxs-lookup"><span data-stu-id="f2e53-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="f2e53-122">Gdzie</span><span class="sxs-lookup"><span data-stu-id="f2e53-122">Where</span></span>|<span data-ttu-id="f2e53-123">xs:String</span><span class="sxs-lookup"><span data-stu-id="f2e53-123">xs:string</span></span>|<span data-ttu-id="f2e53-124">Gdzie części zapytania korelacji.</span><span class="sxs-lookup"><span data-stu-id="f2e53-124">The Where portion of the correlation query.</span></span>|  
|<span data-ttu-id="f2e53-125">AppDomain</span><span class="sxs-lookup"><span data-stu-id="f2e53-125">AppDomain</span></span>|<span data-ttu-id="f2e53-126">xs:String</span><span class="sxs-lookup"><span data-stu-id="f2e53-126">xs:string</span></span>|<span data-ttu-id="f2e53-127">Ciąg zwracany przez AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="f2e53-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
