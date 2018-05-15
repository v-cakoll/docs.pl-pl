---
title: 1028 - CompleteTransactionContextWorkItem
ms.date: 03/30/2017
ms.assetid: 95423f9d-d29a-460e-bcd8-096e80af5bd0
ms.openlocfilehash: 806a437822cef8802a2bef6a54f924f84c88ef60
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="1028---completetransactioncontextworkitem"></a><span data-ttu-id="3d111-102">1028 - CompleteTransactionContextWorkItem</span><span class="sxs-lookup"><span data-stu-id="3d111-102">1028 - CompleteTransactionContextWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="3d111-103">Właściwości</span><span class="sxs-lookup"><span data-stu-id="3d111-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="3d111-104">ID</span><span class="sxs-lookup"><span data-stu-id="3d111-104">ID</span></span>|<span data-ttu-id="3d111-105">1028</span><span class="sxs-lookup"><span data-stu-id="3d111-105">1028</span></span>|  
|<span data-ttu-id="3d111-106">Słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="3d111-106">Keywords</span></span>|<span data-ttu-id="3d111-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="3d111-107">WFRuntime</span></span>|  
|<span data-ttu-id="3d111-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="3d111-108">Level</span></span>|<span data-ttu-id="3d111-109">Pełny</span><span class="sxs-lookup"><span data-stu-id="3d111-109">Verbose</span></span>|  
|<span data-ttu-id="3d111-110">Kanał</span><span class="sxs-lookup"><span data-stu-id="3d111-110">Channel</span></span>|<span data-ttu-id="3d111-111">Microsoft-Windows aplikacji debugowania serwera — aplikacje</span><span class="sxs-lookup"><span data-stu-id="3d111-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="3d111-112">Opis</span><span class="sxs-lookup"><span data-stu-id="3d111-112">Description</span></span>  
 <span data-ttu-id="3d111-113">Wskazuje, że Ukończono element roboczy TransactionContextWorkItem.</span><span class="sxs-lookup"><span data-stu-id="3d111-113">Indicates a TransactionContextWorkItem has completed.</span></span>  
  
## <a name="message"></a><span data-ttu-id="3d111-114">Komunikat</span><span class="sxs-lookup"><span data-stu-id="3d111-114">Message</span></span>  
 <span data-ttu-id="3d111-115">Ukończono element roboczy TransactionContextWorkItem dla działania %1, nazwa wyświetlana: %2, identyfikator wystąpienia: '%3'.</span><span class="sxs-lookup"><span data-stu-id="3d111-115">A TransactionContextWorkItem has completed for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="3d111-116">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="3d111-116">Details</span></span>  
  
|<span data-ttu-id="3d111-117">Nazwa elementu danych</span><span class="sxs-lookup"><span data-stu-id="3d111-117">Data Item Name</span></span>|<span data-ttu-id="3d111-118">Typ elementu danych</span><span class="sxs-lookup"><span data-stu-id="3d111-118">Data Item Type</span></span>|<span data-ttu-id="3d111-119">Opis</span><span class="sxs-lookup"><span data-stu-id="3d111-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="3d111-120">Działanie</span><span class="sxs-lookup"><span data-stu-id="3d111-120">Activity</span></span>|<span data-ttu-id="3d111-121">xs:String</span><span class="sxs-lookup"><span data-stu-id="3d111-121">xs:string</span></span>|<span data-ttu-id="3d111-122">Nazwa typu działania.</span><span class="sxs-lookup"><span data-stu-id="3d111-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="3d111-123">Nazwa wyświetlana</span><span class="sxs-lookup"><span data-stu-id="3d111-123">DisplayName</span></span>|<span data-ttu-id="3d111-124">xs:String</span><span class="sxs-lookup"><span data-stu-id="3d111-124">xs:string</span></span>|<span data-ttu-id="3d111-125">Nazwa wyświetlana działania.</span><span class="sxs-lookup"><span data-stu-id="3d111-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="3d111-126">Identyfikator wystąpienia</span><span class="sxs-lookup"><span data-stu-id="3d111-126">InstanceId</span></span>|<span data-ttu-id="3d111-127">xs:String</span><span class="sxs-lookup"><span data-stu-id="3d111-127">xs:string</span></span>|<span data-ttu-id="3d111-128">Identyfikator wystąpienia działania.</span><span class="sxs-lookup"><span data-stu-id="3d111-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="3d111-129">Domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="3d111-129">AppDomain</span></span>|<span data-ttu-id="3d111-130">xs:String</span><span class="sxs-lookup"><span data-stu-id="3d111-130">xs:string</span></span>|<span data-ttu-id="3d111-131">Długość ciągu zwróconego przez AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="3d111-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
