---
title: 1027 — StartTransactionContextWorkItem
ms.date: 03/30/2017
ms.assetid: 116ae5ec-b9d5-4231-824e-270d00eea7b8
ms.openlocfilehash: 231a7607f2ce9a38e8dd6c1486a68bc9eb459e5e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62008827"
---
# <a name="1027---starttransactioncontextworkitem"></a><span data-ttu-id="5fcc4-102">1027 — StartTransactionContextWorkItem</span><span class="sxs-lookup"><span data-stu-id="5fcc4-102">1027 - StartTransactionContextWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="5fcc4-103">Właściwości</span><span class="sxs-lookup"><span data-stu-id="5fcc4-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="5fcc4-104">Identyfikator</span><span class="sxs-lookup"><span data-stu-id="5fcc4-104">ID</span></span>|<span data-ttu-id="5fcc4-105">1027</span><span class="sxs-lookup"><span data-stu-id="5fcc4-105">1027</span></span>|  
|<span data-ttu-id="5fcc4-106">słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="5fcc4-106">Keywords</span></span>|<span data-ttu-id="5fcc4-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="5fcc4-107">WFRuntime</span></span>|  
|<span data-ttu-id="5fcc4-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="5fcc4-108">Level</span></span>|<span data-ttu-id="5fcc4-109">Pełny</span><span class="sxs-lookup"><span data-stu-id="5fcc4-109">Verbose</span></span>|  
|<span data-ttu-id="5fcc4-110">Kanał</span><span class="sxs-lookup"><span data-stu-id="5fcc4-110">Channel</span></span>|<span data-ttu-id="5fcc4-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="5fcc4-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="5fcc4-112">Opis</span><span class="sxs-lookup"><span data-stu-id="5fcc4-112">Description</span></span>  
 <span data-ttu-id="5fcc4-113">Wskazuje, że TransactionContextWorkItem Trwa uruchamianie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="5fcc4-113">Indicates a TransactionContextWorkItem is starting execution.</span></span>  
  
## <a name="message"></a><span data-ttu-id="5fcc4-114">Komunikat</span><span class="sxs-lookup"><span data-stu-id="5fcc4-114">Message</span></span>  
 <span data-ttu-id="5fcc4-115">Rozpoczynanie wykonywania TransactionContextWorkItem dla działania "%1", DisplayName: "%2", InstanceId: "%3".</span><span class="sxs-lookup"><span data-stu-id="5fcc4-115">Starting execution of a TransactionContextWorkItem for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="5fcc4-116">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="5fcc4-116">Details</span></span>  
  
|<span data-ttu-id="5fcc4-117">Nazwa elementu danych</span><span class="sxs-lookup"><span data-stu-id="5fcc4-117">Data Item Name</span></span>|<span data-ttu-id="5fcc4-118">Typ elementu danych</span><span class="sxs-lookup"><span data-stu-id="5fcc4-118">Data Item Type</span></span>|<span data-ttu-id="5fcc4-119">Opis</span><span class="sxs-lookup"><span data-stu-id="5fcc4-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="5fcc4-120">Działanie</span><span class="sxs-lookup"><span data-stu-id="5fcc4-120">Activity</span></span>|<span data-ttu-id="5fcc4-121">xs:String</span><span class="sxs-lookup"><span data-stu-id="5fcc4-121">xs:string</span></span>|<span data-ttu-id="5fcc4-122">Nazwa typu działania.</span><span class="sxs-lookup"><span data-stu-id="5fcc4-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="5fcc4-123">Nazwa wyświetlana</span><span class="sxs-lookup"><span data-stu-id="5fcc4-123">DisplayName</span></span>|<span data-ttu-id="5fcc4-124">xs:String</span><span class="sxs-lookup"><span data-stu-id="5fcc4-124">xs:string</span></span>|<span data-ttu-id="5fcc4-125">Nazwa wyświetlana działania.</span><span class="sxs-lookup"><span data-stu-id="5fcc4-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="5fcc4-126">InstanceId</span><span class="sxs-lookup"><span data-stu-id="5fcc4-126">InstanceId</span></span>|<span data-ttu-id="5fcc4-127">xs:String</span><span class="sxs-lookup"><span data-stu-id="5fcc4-127">xs:string</span></span>|<span data-ttu-id="5fcc4-128">Identyfikator wystąpienia działania.</span><span class="sxs-lookup"><span data-stu-id="5fcc4-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="5fcc4-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="5fcc4-129">AppDomain</span></span>|<span data-ttu-id="5fcc4-130">xs:String</span><span class="sxs-lookup"><span data-stu-id="5fcc4-130">xs:string</span></span>|<span data-ttu-id="5fcc4-131">Ciąg zwracany przez AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="5fcc4-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
