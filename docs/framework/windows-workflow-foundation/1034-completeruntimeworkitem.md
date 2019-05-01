---
title: 1034 — CompleteRuntimeWorkItem
ms.date: 03/30/2017
ms.assetid: 45620011-8b04-4f87-ab5a-65b24145e17d
ms.openlocfilehash: bd49c608a8f6a6caab6975850507a00a2c0edb03
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61924556"
---
# <a name="1034---completeruntimeworkitem"></a><span data-ttu-id="7fd0f-102">1034 — CompleteRuntimeWorkItem</span><span class="sxs-lookup"><span data-stu-id="7fd0f-102">1034 - CompleteRuntimeWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="7fd0f-103">Właściwości</span><span class="sxs-lookup"><span data-stu-id="7fd0f-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="7fd0f-104">Identyfikator</span><span class="sxs-lookup"><span data-stu-id="7fd0f-104">ID</span></span>|<span data-ttu-id="7fd0f-105">1034</span><span class="sxs-lookup"><span data-stu-id="7fd0f-105">1034</span></span>|  
|<span data-ttu-id="7fd0f-106">słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="7fd0f-106">Keywords</span></span>|<span data-ttu-id="7fd0f-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="7fd0f-107">WFRuntime</span></span>|  
|<span data-ttu-id="7fd0f-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="7fd0f-108">Level</span></span>|<span data-ttu-id="7fd0f-109">Pełny</span><span class="sxs-lookup"><span data-stu-id="7fd0f-109">Verbose</span></span>|  
|<span data-ttu-id="7fd0f-110">Kanał</span><span class="sxs-lookup"><span data-stu-id="7fd0f-110">Channel</span></span>|<span data-ttu-id="7fd0f-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="7fd0f-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="7fd0f-112">Opis</span><span class="sxs-lookup"><span data-stu-id="7fd0f-112">Description</span></span>  
 <span data-ttu-id="7fd0f-113">Wskazuje, że RuntimeWorkItem zostało zakończone.</span><span class="sxs-lookup"><span data-stu-id="7fd0f-113">Indicates a RuntimeWorkItem has completed.</span></span>  
  
## <a name="message"></a><span data-ttu-id="7fd0f-114">Komunikat</span><span class="sxs-lookup"><span data-stu-id="7fd0f-114">Message</span></span>  
 <span data-ttu-id="7fd0f-115">Element roboczy środowisko uruchomieniowe zostało ukończone dla działania "%1", DisplayName: "%2", InstanceId: "%3".</span><span class="sxs-lookup"><span data-stu-id="7fd0f-115">A runtime work item has completed for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="7fd0f-116">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="7fd0f-116">Details</span></span>  
  
|<span data-ttu-id="7fd0f-117">Nazwa elementu danych</span><span class="sxs-lookup"><span data-stu-id="7fd0f-117">Data Item Name</span></span>|<span data-ttu-id="7fd0f-118">Typ elementu danych</span><span class="sxs-lookup"><span data-stu-id="7fd0f-118">Data Item Type</span></span>|<span data-ttu-id="7fd0f-119">Opis</span><span class="sxs-lookup"><span data-stu-id="7fd0f-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="7fd0f-120">Działanie</span><span class="sxs-lookup"><span data-stu-id="7fd0f-120">Activity</span></span>|<span data-ttu-id="7fd0f-121">xs:String</span><span class="sxs-lookup"><span data-stu-id="7fd0f-121">xs:string</span></span>|<span data-ttu-id="7fd0f-122">Nazwa typu działania.</span><span class="sxs-lookup"><span data-stu-id="7fd0f-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="7fd0f-123">Nazwa wyświetlana</span><span class="sxs-lookup"><span data-stu-id="7fd0f-123">DisplayName</span></span>|<span data-ttu-id="7fd0f-124">xs:String</span><span class="sxs-lookup"><span data-stu-id="7fd0f-124">xs:string</span></span>|<span data-ttu-id="7fd0f-125">Nazwa wyświetlana działania.</span><span class="sxs-lookup"><span data-stu-id="7fd0f-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="7fd0f-126">InstanceId</span><span class="sxs-lookup"><span data-stu-id="7fd0f-126">InstanceId</span></span>|<span data-ttu-id="7fd0f-127">xs:String</span><span class="sxs-lookup"><span data-stu-id="7fd0f-127">xs:string</span></span>|<span data-ttu-id="7fd0f-128">Identyfikator wystąpienia działania.</span><span class="sxs-lookup"><span data-stu-id="7fd0f-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="7fd0f-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="7fd0f-129">AppDomain</span></span>|<span data-ttu-id="7fd0f-130">xs:String</span><span class="sxs-lookup"><span data-stu-id="7fd0f-130">xs:string</span></span>|<span data-ttu-id="7fd0f-131">Ciąg zwracany przez AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="7fd0f-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
