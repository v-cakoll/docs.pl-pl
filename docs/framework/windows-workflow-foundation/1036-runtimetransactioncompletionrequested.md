---
title: 1036 — RuntimeTransactionCompletionRequested
ms.date: 03/30/2017
ms.assetid: d36b9f44-7c0f-4083-9d3a-9034dd2b98de
ms.openlocfilehash: 649ba542a9ed2f330ac71e447602d637530dc601
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33510396"
---
# <a name="1036---runtimetransactioncompletionrequested"></a><span data-ttu-id="a303c-102">1036 — RuntimeTransactionCompletionRequested</span><span class="sxs-lookup"><span data-stu-id="a303c-102">1036 - RuntimeTransactionCompletionRequested</span></span>
## <a name="properties"></a><span data-ttu-id="a303c-103">Właściwości</span><span class="sxs-lookup"><span data-stu-id="a303c-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="a303c-104">ID</span><span class="sxs-lookup"><span data-stu-id="a303c-104">ID</span></span>|<span data-ttu-id="a303c-105">1036</span><span class="sxs-lookup"><span data-stu-id="a303c-105">1036</span></span>|  
|<span data-ttu-id="a303c-106">Słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="a303c-106">Keywords</span></span>|<span data-ttu-id="a303c-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="a303c-107">WFRuntime</span></span>|  
|<span data-ttu-id="a303c-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="a303c-108">Level</span></span>|<span data-ttu-id="a303c-109">Pełny</span><span class="sxs-lookup"><span data-stu-id="a303c-109">Verbose</span></span>|  
|<span data-ttu-id="a303c-110">Kanał</span><span class="sxs-lookup"><span data-stu-id="a303c-110">Channel</span></span>|<span data-ttu-id="a303c-111">Microsoft-Windows aplikacji debugowania serwera — aplikacje</span><span class="sxs-lookup"><span data-stu-id="a303c-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="a303c-112">Opis</span><span class="sxs-lookup"><span data-stu-id="a303c-112">Description</span></span>  
 <span data-ttu-id="a303c-113">Wskazuje, że działanie zaplanowało wykonanie transakcji czasu wykonywania.</span><span class="sxs-lookup"><span data-stu-id="a303c-113">Indicates an activity has scheduled the completion of the runtime transaction.</span></span>  
  
## <a name="message"></a><span data-ttu-id="a303c-114">Komunikat</span><span class="sxs-lookup"><span data-stu-id="a303c-114">Message</span></span>  
 <span data-ttu-id="a303c-115">Działanie "%1", nazwa wyświetlana: %2, identyfikator wystąpienia: '%3', zaplanowało wykonanie transakcji czasu wykonywania.</span><span class="sxs-lookup"><span data-stu-id="a303c-115">Activity '%1', DisplayName: '%2', InstanceId: '%3' has scheduled completion of the runtime transaction.</span></span>  
  
## <a name="details"></a><span data-ttu-id="a303c-116">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="a303c-116">Details</span></span>  
  
|<span data-ttu-id="a303c-117">Nazwa elementu danych</span><span class="sxs-lookup"><span data-stu-id="a303c-117">Data Item Name</span></span>|<span data-ttu-id="a303c-118">Typ elementu danych</span><span class="sxs-lookup"><span data-stu-id="a303c-118">Data Item Type</span></span>|<span data-ttu-id="a303c-119">Opis</span><span class="sxs-lookup"><span data-stu-id="a303c-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="a303c-120">Działanie</span><span class="sxs-lookup"><span data-stu-id="a303c-120">Activity</span></span>|<span data-ttu-id="a303c-121">xs:String</span><span class="sxs-lookup"><span data-stu-id="a303c-121">xs:string</span></span>|<span data-ttu-id="a303c-122">Nazwa typu działania.</span><span class="sxs-lookup"><span data-stu-id="a303c-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="a303c-123">Nazwa wyświetlana</span><span class="sxs-lookup"><span data-stu-id="a303c-123">DisplayName</span></span>|<span data-ttu-id="a303c-124">xs:String</span><span class="sxs-lookup"><span data-stu-id="a303c-124">xs:string</span></span>|<span data-ttu-id="a303c-125">Nazwa wyświetlana działania.</span><span class="sxs-lookup"><span data-stu-id="a303c-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="a303c-126">Identyfikator wystąpienia</span><span class="sxs-lookup"><span data-stu-id="a303c-126">InstanceId</span></span>|<span data-ttu-id="a303c-127">xs:String</span><span class="sxs-lookup"><span data-stu-id="a303c-127">xs:string</span></span>|<span data-ttu-id="a303c-128">Identyfikator wystąpienia działania.</span><span class="sxs-lookup"><span data-stu-id="a303c-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="a303c-129">Domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="a303c-129">AppDomain</span></span>|<span data-ttu-id="a303c-130">xs:String</span><span class="sxs-lookup"><span data-stu-id="a303c-130">xs:string</span></span>|<span data-ttu-id="a303c-131">Długość ciągu zwróconego przez AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="a303c-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
