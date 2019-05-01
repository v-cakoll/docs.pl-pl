---
title: 1013 — CompleteExecuteActivityWorkItem
ms.date: 03/30/2017
ms.assetid: 31fc57b3-ef2f-48f0-a5de-b4e2c5c9ded7
ms.openlocfilehash: c1ff62bb4143bb798ea7adb7c3fee539ef68bc37
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61925193"
---
# <a name="1013---completeexecuteactivityworkitem"></a><span data-ttu-id="4a751-102">1013 — CompleteExecuteActivityWorkItem</span><span class="sxs-lookup"><span data-stu-id="4a751-102">1013 - CompleteExecuteActivityWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="4a751-103">Właściwości</span><span class="sxs-lookup"><span data-stu-id="4a751-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="4a751-104">Identyfikator</span><span class="sxs-lookup"><span data-stu-id="4a751-104">ID</span></span>|<span data-ttu-id="4a751-105">1013</span><span class="sxs-lookup"><span data-stu-id="4a751-105">1013</span></span>|  
|<span data-ttu-id="4a751-106">słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="4a751-106">Keywords</span></span>|<span data-ttu-id="4a751-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="4a751-107">WFRuntime</span></span>|  
|<span data-ttu-id="4a751-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="4a751-108">Level</span></span>|<span data-ttu-id="4a751-109">Pełny</span><span class="sxs-lookup"><span data-stu-id="4a751-109">Verbose</span></span>|  
|<span data-ttu-id="4a751-110">Kanał</span><span class="sxs-lookup"><span data-stu-id="4a751-110">Channel</span></span>|<span data-ttu-id="4a751-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="4a751-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="4a751-112">Opis</span><span class="sxs-lookup"><span data-stu-id="4a751-112">Description</span></span>  
 <span data-ttu-id="4a751-113">Wskazuje, że ExecuteActivityWorkItem zostało zakończone.</span><span class="sxs-lookup"><span data-stu-id="4a751-113">Indicates an ExecuteActivityWorkItem has completed</span></span>  
  
## <a name="message"></a><span data-ttu-id="4a751-114">Komunikat</span><span class="sxs-lookup"><span data-stu-id="4a751-114">Message</span></span>  
 <span data-ttu-id="4a751-115">ExecuteActivityWorkItem zostało ukończone dla działania "%1", DisplayName: "%2", InstanceId: "%3".</span><span class="sxs-lookup"><span data-stu-id="4a751-115">An ExecuteActivityWorkItem has completed for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="4a751-116">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="4a751-116">Details</span></span>  
  
|<span data-ttu-id="4a751-117">Nazwa elementu danych</span><span class="sxs-lookup"><span data-stu-id="4a751-117">Data Item Name</span></span>|<span data-ttu-id="4a751-118">Typ elementu danych</span><span class="sxs-lookup"><span data-stu-id="4a751-118">Data Item Type</span></span>|<span data-ttu-id="4a751-119">Opis</span><span class="sxs-lookup"><span data-stu-id="4a751-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="4a751-120">Działanie</span><span class="sxs-lookup"><span data-stu-id="4a751-120">Activity</span></span>|<span data-ttu-id="4a751-121">xs:String</span><span class="sxs-lookup"><span data-stu-id="4a751-121">xs:string</span></span>|<span data-ttu-id="4a751-122">Nazwa typu działania.</span><span class="sxs-lookup"><span data-stu-id="4a751-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="4a751-123">Nazwa wyświetlana</span><span class="sxs-lookup"><span data-stu-id="4a751-123">DisplayName</span></span>|<span data-ttu-id="4a751-124">xs:String</span><span class="sxs-lookup"><span data-stu-id="4a751-124">xs:string</span></span>|<span data-ttu-id="4a751-125">Nazwa wyświetlana działania.</span><span class="sxs-lookup"><span data-stu-id="4a751-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="4a751-126">InstanceId</span><span class="sxs-lookup"><span data-stu-id="4a751-126">InstanceId</span></span>|<span data-ttu-id="4a751-127">xs:String</span><span class="sxs-lookup"><span data-stu-id="4a751-127">xs:string</span></span>|<span data-ttu-id="4a751-128">Identyfikator wystąpienia działania.</span><span class="sxs-lookup"><span data-stu-id="4a751-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="4a751-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="4a751-129">AppDomain</span></span>|<span data-ttu-id="4a751-130">xs:String</span><span class="sxs-lookup"><span data-stu-id="4a751-130">xs:string</span></span>|<span data-ttu-id="4a751-131">Ciąg zwracany przez AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="4a751-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
