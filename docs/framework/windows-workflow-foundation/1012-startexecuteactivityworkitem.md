---
title: 1012 — StartExecuteActivityWorkItem
ms.date: 03/30/2017
ms.assetid: 29e9b1c6-c5d7-4b58-b59d-a06a923d3c80
ms.openlocfilehash: d6b330bc454c39584e5027f757fd9d9d3434d941
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61924582"
---
# <a name="1012---startexecuteactivityworkitem"></a><span data-ttu-id="da960-102">1012 — StartExecuteActivityWorkItem</span><span class="sxs-lookup"><span data-stu-id="da960-102">1012 - StartExecuteActivityWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="da960-103">Właściwości</span><span class="sxs-lookup"><span data-stu-id="da960-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="da960-104">Identyfikator</span><span class="sxs-lookup"><span data-stu-id="da960-104">ID</span></span>|<span data-ttu-id="da960-105">1012</span><span class="sxs-lookup"><span data-stu-id="da960-105">1012</span></span>|  
|<span data-ttu-id="da960-106">słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="da960-106">Keywords</span></span>|<span data-ttu-id="da960-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="da960-107">WFRuntime</span></span>|  
|<span data-ttu-id="da960-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="da960-108">Level</span></span>|<span data-ttu-id="da960-109">Pełny</span><span class="sxs-lookup"><span data-stu-id="da960-109">Verbose</span></span>|  
|<span data-ttu-id="da960-110">Kanał</span><span class="sxs-lookup"><span data-stu-id="da960-110">Channel</span></span>|<span data-ttu-id="da960-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="da960-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="da960-112">Opis</span><span class="sxs-lookup"><span data-stu-id="da960-112">Description</span></span>  
 <span data-ttu-id="da960-113">Wskazuje, że ExecuteActivityWorkItem Trwa uruchamianie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="da960-113">Indicates an ExecuteActivityWorkItem is starting execution.</span></span>  
  
## <a name="message"></a><span data-ttu-id="da960-114">Komunikat</span><span class="sxs-lookup"><span data-stu-id="da960-114">Message</span></span>  
 <span data-ttu-id="da960-115">Rozpoczynanie wykonywania ExecuteActivityWorkItem dla działania "%1", DisplayName: "%2", InstanceId: "%3".</span><span class="sxs-lookup"><span data-stu-id="da960-115">Starting execution of an ExecuteActivityWorkItem for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="da960-116">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="da960-116">Details</span></span>  
  
|<span data-ttu-id="da960-117">Nazwa elementu danych</span><span class="sxs-lookup"><span data-stu-id="da960-117">Data Item Name</span></span>|<span data-ttu-id="da960-118">Typ elementu danych</span><span class="sxs-lookup"><span data-stu-id="da960-118">Data Item Type</span></span>|<span data-ttu-id="da960-119">Opis</span><span class="sxs-lookup"><span data-stu-id="da960-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="da960-120">Działanie</span><span class="sxs-lookup"><span data-stu-id="da960-120">Activity</span></span>|<span data-ttu-id="da960-121">xs:String</span><span class="sxs-lookup"><span data-stu-id="da960-121">xs:string</span></span>|<span data-ttu-id="da960-122">Nazwa typu działania.</span><span class="sxs-lookup"><span data-stu-id="da960-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="da960-123">Nazwa wyświetlana</span><span class="sxs-lookup"><span data-stu-id="da960-123">DisplayName</span></span>|<span data-ttu-id="da960-124">xs:String</span><span class="sxs-lookup"><span data-stu-id="da960-124">xs:string</span></span>|<span data-ttu-id="da960-125">Nazwa wyświetlana działania.</span><span class="sxs-lookup"><span data-stu-id="da960-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="da960-126">InstanceId</span><span class="sxs-lookup"><span data-stu-id="da960-126">InstanceId</span></span>|<span data-ttu-id="da960-127">xs:String</span><span class="sxs-lookup"><span data-stu-id="da960-127">xs:string</span></span>|<span data-ttu-id="da960-128">Identyfikator wystąpienia działania.</span><span class="sxs-lookup"><span data-stu-id="da960-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="da960-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="da960-129">AppDomain</span></span>|<span data-ttu-id="da960-130">xs:String</span><span class="sxs-lookup"><span data-stu-id="da960-130">xs:string</span></span>|<span data-ttu-id="da960-131">Ciąg zwracany przez AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="da960-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
