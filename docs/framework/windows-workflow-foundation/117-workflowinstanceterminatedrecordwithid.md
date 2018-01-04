---
title: 117 - WorkflowInstanceTerminatedRecordWithId
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e68539d0-5338-468a-9f75-7e5b09d39a3c
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3fd8ece3245b99a5d976058135492e8503dd1c8b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="117---workflowinstanceterminatedrecordwithid"></a><span data-ttu-id="f4750-102">117 - WorkflowInstanceTerminatedRecordWithId</span><span class="sxs-lookup"><span data-stu-id="f4750-102">117 - WorkflowInstanceTerminatedRecordWithId</span></span>
## <a name="properties"></a><span data-ttu-id="f4750-103">Właściwości</span><span class="sxs-lookup"><span data-stu-id="f4750-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="f4750-104">ID</span><span class="sxs-lookup"><span data-stu-id="f4750-104">ID</span></span>|<span data-ttu-id="f4750-105">117</span><span class="sxs-lookup"><span data-stu-id="f4750-105">117</span></span>|  
|<span data-ttu-id="f4750-106">Słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="f4750-106">Keywords</span></span>|<span data-ttu-id="f4750-107">HealthMonitoring, WFTracking</span><span class="sxs-lookup"><span data-stu-id="f4750-107">HealthMonitoring, WFTracking</span></span>|  
|<span data-ttu-id="f4750-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="f4750-108">Level</span></span>|<span data-ttu-id="f4750-109">Błąd</span><span class="sxs-lookup"><span data-stu-id="f4750-109">Error</span></span>|  
|<span data-ttu-id="f4750-110">Kanał</span><span class="sxs-lookup"><span data-stu-id="f4750-110">Channel</span></span>|<span data-ttu-id="f4750-111">Microsoft-Windows aplikacji Server aplikacje/analityczne</span><span class="sxs-lookup"><span data-stu-id="f4750-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="f4750-112">Opis</span><span class="sxs-lookup"><span data-stu-id="f4750-112">Description</span></span>  
 <span data-ttu-id="f4750-113">To zdarzenie jest emitowane przez uczestnika śledzenia zdarzeń systemu Windows, gdy WorkflowInstanceTerminatedRecord emituje wystąpienia przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="f4750-113">This event is emitted by the ETW tracking participant when a workflow instance emits WorkflowInstanceTerminatedRecord.</span></span>  
  
## <a name="message"></a><span data-ttu-id="f4750-114">Komunikat</span><span class="sxs-lookup"><span data-stu-id="f4750-114">Message</span></span>  
 <span data-ttu-id="f4750-115">TrackRecord = WorkflowInstanceTerminatedRecord, identyfikator wystąpienia = %1, RecordNumber = %2, EventTime = %3, obiekt ActivityDefinitionId = %4, przyczyna = %5, adnotacje = %6, ProfileName = %7 WorkflowDefinitionIdentity = %8</span><span class="sxs-lookup"><span data-stu-id="f4750-115">TrackRecord = WorkflowInstanceTerminatedRecord, InstanceID = %1, RecordNumber = %2, EventTime = %3, ActivityDefinitionId = %4, Reason = %5,  Annotations = %6, ProfileName = %7, WorkflowDefinitionIdentity = %8</span></span>  
  
## <a name="details"></a><span data-ttu-id="f4750-116">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="f4750-116">Details</span></span>  
  
|<span data-ttu-id="f4750-117">Nazwa elementu danych</span><span class="sxs-lookup"><span data-stu-id="f4750-117">Data Item Name</span></span>|<span data-ttu-id="f4750-118">Typ elementu danych</span><span class="sxs-lookup"><span data-stu-id="f4750-118">Data Item Type</span></span>|<span data-ttu-id="f4750-119">Opis</span><span class="sxs-lookup"><span data-stu-id="f4750-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="f4750-120">Identyfikator wystąpienia</span><span class="sxs-lookup"><span data-stu-id="f4750-120">InstanceId</span></span>|<span data-ttu-id="f4750-121">xs:GUID</span><span class="sxs-lookup"><span data-stu-id="f4750-121">xs:GUID</span></span>|<span data-ttu-id="f4750-122">Identyfikator wystąpienia przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="f4750-122">The instance id for the workflow</span></span>|  
|<span data-ttu-id="f4750-123">RecordNumber</span><span class="sxs-lookup"><span data-stu-id="f4750-123">RecordNumber</span></span>|<span data-ttu-id="f4750-124">xs:Long</span><span class="sxs-lookup"><span data-stu-id="f4750-124">xs:long</span></span>|<span data-ttu-id="f4750-125">Numer sekwencyjny emitowany rekordu</span><span class="sxs-lookup"><span data-stu-id="f4750-125">The sequence number of the emitted record</span></span>|  
|<span data-ttu-id="f4750-126">eventTime</span><span class="sxs-lookup"><span data-stu-id="f4750-126">EventTime</span></span>|<span data-ttu-id="f4750-127">xs: DateTime</span><span class="sxs-lookup"><span data-stu-id="f4750-127">xs:dateTime</span></span>|<span data-ttu-id="f4750-128">Godzina w formacie UTC podczas zdarzenia zostały wyemitowane</span><span class="sxs-lookup"><span data-stu-id="f4750-128">The time in UTC when the event was emitted</span></span>|  
|<span data-ttu-id="f4750-129">Obiekt ActivityDefinitionId</span><span class="sxs-lookup"><span data-stu-id="f4750-129">ActivityDefinitionId</span></span>|<span data-ttu-id="f4750-130">xs:String</span><span class="sxs-lookup"><span data-stu-id="f4750-130">xs:string</span></span>|<span data-ttu-id="f4750-131">Nazwa działania głównego w przepływie pracy</span><span class="sxs-lookup"><span data-stu-id="f4750-131">The name of the root activity in the workflow</span></span>|  
|<span data-ttu-id="f4750-132">Stan</span><span class="sxs-lookup"><span data-stu-id="f4750-132">State</span></span>|<span data-ttu-id="f4750-133">xs:String</span><span class="sxs-lookup"><span data-stu-id="f4750-133">xs:string</span></span>|<span data-ttu-id="f4750-134">Bieżący stan przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="f4750-134">The current state of the Workflow.</span></span>|  
|<span data-ttu-id="f4750-135">Adnotacje</span><span class="sxs-lookup"><span data-stu-id="f4750-135">Annotations</span></span>|<span data-ttu-id="f4750-136">xs:String</span><span class="sxs-lookup"><span data-stu-id="f4750-136">xs:string</span></span>|<span data-ttu-id="f4750-137">Adnotacje, które zostały dodane do tego zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="f4750-137">The annotations that were added to this event.</span></span> <span data-ttu-id="f4750-138">Wartości są przechowywane w elemencie xml w formacie \<elementy >\< nazwa elementu = "annotationName" type="System.String" > annotationValue\</elementu > \< /elementy >.</span><span class="sxs-lookup"><span data-stu-id="f4750-138">The values are stored in an xml element in the format \<items>\< item name = "annotationName" type="System.String">annotationValue\</item>\</items>.</span></span> <span data-ttu-id="f4750-139">Jeśli nie określono bez adnotacji, a następnie ciąg zawiera \<elementów / >.</span><span class="sxs-lookup"><span data-stu-id="f4750-139">If no annotations are specified then the string contains \<items/>.</span></span> <span data-ttu-id="f4750-140">Rozmiar zdarzenia ETW jest ograniczona przez rozmiar bufora ETW lub max ładunku zdarzenia ETW.</span><span class="sxs-lookup"><span data-stu-id="f4750-140">The ETW event size is limited by the ETW buffer size or the max payload for an ETW event.</span></span> <span data-ttu-id="f4750-141">Jeśli limity ETW przekracza rozmiar zdarzenia, a następnie zdarzenia został obcięty przez usunięcie adnotacje i zastąpienie wartości adnotacji z \<elementy >...  \< /elementy >.</span><span class="sxs-lookup"><span data-stu-id="f4750-141">If the size of the event exceeds the ETW limits, then the event is truncated by dropping the annotations and replacing the annotation value with \<items>...\</items>.</span></span>|  
|<span data-ttu-id="f4750-142">ProfileName</span><span class="sxs-lookup"><span data-stu-id="f4750-142">ProfileName</span></span>|<span data-ttu-id="f4750-143">xs:String</span><span class="sxs-lookup"><span data-stu-id="f4750-143">xs:string</span></span>|<span data-ttu-id="f4750-144">Nazwa lub profilu śledzenia, które spowodowały to zdarzenie jest emitowany</span><span class="sxs-lookup"><span data-stu-id="f4750-144">The name or the tracking profile that resulted in this event being emitted</span></span>|  
|<span data-ttu-id="f4750-145">WorkflowDefinitionIdentity</span><span class="sxs-lookup"><span data-stu-id="f4750-145">WorkflowDefinitionIdentity</span></span>|<span data-ttu-id="f4750-146">xs:String</span><span class="sxs-lookup"><span data-stu-id="f4750-146">xs:string</span></span>|<span data-ttu-id="f4750-147">Identyfikator definicji przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="f4750-147">The workflow definition id</span></span>|  
|<span data-ttu-id="f4750-148">Domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="f4750-148">AppDomain</span></span>|<span data-ttu-id="f4750-149">xs:String</span><span class="sxs-lookup"><span data-stu-id="f4750-149">xs:string</span></span>|<span data-ttu-id="f4750-150">Długość ciągu zwróconego przez AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="f4750-150">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
