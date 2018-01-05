---
title: 115 - WorkflowInstanceAbortedRecordWithId
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0293dd4e-e6ae-473a-b3d6-c2d38f9bd875
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 314f880f1fc2d78efc59f73f37122d03ae30cf72
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="115---workflowinstanceabortedrecordwithid"></a><span data-ttu-id="bef7f-102">115 - WorkflowInstanceAbortedRecordWithId</span><span class="sxs-lookup"><span data-stu-id="bef7f-102">115 - WorkflowInstanceAbortedRecordWithId</span></span>
## <a name="properties"></a><span data-ttu-id="bef7f-103">Właściwości</span><span class="sxs-lookup"><span data-stu-id="bef7f-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="bef7f-104">ID</span><span class="sxs-lookup"><span data-stu-id="bef7f-104">ID</span></span>|<span data-ttu-id="bef7f-105">115</span><span class="sxs-lookup"><span data-stu-id="bef7f-105">115</span></span>|  
|<span data-ttu-id="bef7f-106">Słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="bef7f-106">Keywords</span></span>|<span data-ttu-id="bef7f-107">HealthMonitoring, WFTracking</span><span class="sxs-lookup"><span data-stu-id="bef7f-107">HealthMonitoring, WFTracking</span></span>|  
|<span data-ttu-id="bef7f-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="bef7f-108">Level</span></span>|<span data-ttu-id="bef7f-109">Ostrzeżenie</span><span class="sxs-lookup"><span data-stu-id="bef7f-109">Warning</span></span>|  
|<span data-ttu-id="bef7f-110">Kanał</span><span class="sxs-lookup"><span data-stu-id="bef7f-110">Channel</span></span>|<span data-ttu-id="bef7f-111">Microsoft-Windows aplikacji Server aplikacje/analityczne</span><span class="sxs-lookup"><span data-stu-id="bef7f-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="bef7f-112">Opis</span><span class="sxs-lookup"><span data-stu-id="bef7f-112">Description</span></span>  
 <span data-ttu-id="bef7f-113">To zdarzenie jest emitowane przez uczestnika śledzenia zdarzeń systemu Windows, gdy WorkflowInstanceAbortedRecord emituje wystąpienia przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="bef7f-113">This event is emitted by the ETW tracking participant when a workflow instance emits WorkflowInstanceAbortedRecord.</span></span>  
  
## <a name="message"></a><span data-ttu-id="bef7f-114">Komunikat</span><span class="sxs-lookup"><span data-stu-id="bef7f-114">Message</span></span>  
 <span data-ttu-id="bef7f-115">TrackRecord = WorkflowInstanceAbortedRecord, identyfikator wystąpienia = %1, RecordNumber = %2, EventTime = %3, obiekt ActivityDefinitionId = %4, przyczyna = %5, adnotacje = %6, ProfileName = %7 WorkflowDefinitionIdentity = %8</span><span class="sxs-lookup"><span data-stu-id="bef7f-115">TrackRecord = WorkflowInstanceAbortedRecord, InstanceID = %1, RecordNumber = %2, EventTime = %3, ActivityDefinitionId = %4, Reason = %5,  Annotations = %6, ProfileName = %7, WorkflowDefinitionIdentity = %8</span></span>  
  
## <a name="details"></a><span data-ttu-id="bef7f-116">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="bef7f-116">Details</span></span>  
  
|<span data-ttu-id="bef7f-117">Nazwa elementu danych</span><span class="sxs-lookup"><span data-stu-id="bef7f-117">Data Item Name</span></span>|<span data-ttu-id="bef7f-118">Typ elementu danych</span><span class="sxs-lookup"><span data-stu-id="bef7f-118">Data Item Type</span></span>|<span data-ttu-id="bef7f-119">Opis</span><span class="sxs-lookup"><span data-stu-id="bef7f-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="bef7f-120">Identyfikator wystąpienia</span><span class="sxs-lookup"><span data-stu-id="bef7f-120">InstanceId</span></span>|<span data-ttu-id="bef7f-121">xs:GUID</span><span class="sxs-lookup"><span data-stu-id="bef7f-121">xs:GUID</span></span>|<span data-ttu-id="bef7f-122">Identyfikator wystąpienia przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="bef7f-122">The instance id for the workflow</span></span>|  
|<span data-ttu-id="bef7f-123">RecordNumber</span><span class="sxs-lookup"><span data-stu-id="bef7f-123">RecordNumber</span></span>|<span data-ttu-id="bef7f-124">xs:Long</span><span class="sxs-lookup"><span data-stu-id="bef7f-124">xs:long</span></span>|<span data-ttu-id="bef7f-125">Numer sekwencyjny emitowany rekordu</span><span class="sxs-lookup"><span data-stu-id="bef7f-125">The sequence number of the emitted record</span></span>|  
|<span data-ttu-id="bef7f-126">eventTime</span><span class="sxs-lookup"><span data-stu-id="bef7f-126">EventTime</span></span>|<span data-ttu-id="bef7f-127">xs: DateTime</span><span class="sxs-lookup"><span data-stu-id="bef7f-127">xs:dateTime</span></span>|<span data-ttu-id="bef7f-128">Godzina w formacie UTC podczas zdarzenia zostały wyemitowane</span><span class="sxs-lookup"><span data-stu-id="bef7f-128">The time in UTC when the event was emitted</span></span>|  
|<span data-ttu-id="bef7f-129">Obiekt ActivityDefinitionId</span><span class="sxs-lookup"><span data-stu-id="bef7f-129">ActivityDefinitionId</span></span>|<span data-ttu-id="bef7f-130">xs:String</span><span class="sxs-lookup"><span data-stu-id="bef7f-130">xs:string</span></span>|<span data-ttu-id="bef7f-131">Nazwa działania głównego w przepływie pracy</span><span class="sxs-lookup"><span data-stu-id="bef7f-131">The name of the root activity in the workflow</span></span>|  
|<span data-ttu-id="bef7f-132">Stan</span><span class="sxs-lookup"><span data-stu-id="bef7f-132">State</span></span>|<span data-ttu-id="bef7f-133">xs:String</span><span class="sxs-lookup"><span data-stu-id="bef7f-133">xs:string</span></span>|<span data-ttu-id="bef7f-134">Bieżący stan przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="bef7f-134">The current state of the Workflow.</span></span>|  
|<span data-ttu-id="bef7f-135">Adnotacje</span><span class="sxs-lookup"><span data-stu-id="bef7f-135">Annotations</span></span>|<span data-ttu-id="bef7f-136">xs:String</span><span class="sxs-lookup"><span data-stu-id="bef7f-136">xs:string</span></span>|<span data-ttu-id="bef7f-137">Adnotacje, które zostały dodane do tego zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="bef7f-137">The annotations that were added to this event.</span></span> <span data-ttu-id="bef7f-138">Wartości są przechowywane w elemencie xml w formacie \<elementy >\< nazwa elementu = "annotationName" type="System.String" > annotationValue\</elementu > \< /elementy >.</span><span class="sxs-lookup"><span data-stu-id="bef7f-138">The values are stored in an xml element in the format \<items>\< item name = "annotationName" type="System.String">annotationValue\</item>\</items>.</span></span> <span data-ttu-id="bef7f-139">Jeśli nie określono bez adnotacji, a następnie ciąg zawiera \<elementów / >.</span><span class="sxs-lookup"><span data-stu-id="bef7f-139">If no annotations are specified then the string contains \<items/>.</span></span> <span data-ttu-id="bef7f-140">Rozmiar zdarzenia ETW jest ograniczona przez rozmiar bufora ETW lub max ładunku zdarzenia ETW.</span><span class="sxs-lookup"><span data-stu-id="bef7f-140">The ETW event size is limited by the ETW buffer size or the max payload for an ETW event.</span></span> <span data-ttu-id="bef7f-141">Jeśli limity ETW przekracza rozmiar zdarzenia, a następnie zdarzenia został obcięty przez usunięcie adnotacje i zastąpienie wartości adnotacji z \<elementy >...  \< /elementy >.</span><span class="sxs-lookup"><span data-stu-id="bef7f-141">If the size of the event exceeds the ETW limits, then the event is truncated by dropping the annotations and replacing the annotation value with \<items>...\</items>.</span></span>|  
|<span data-ttu-id="bef7f-142">ProfileName</span><span class="sxs-lookup"><span data-stu-id="bef7f-142">ProfileName</span></span>|<span data-ttu-id="bef7f-143">xs:String</span><span class="sxs-lookup"><span data-stu-id="bef7f-143">xs:string</span></span>|<span data-ttu-id="bef7f-144">Nazwa lub profilu śledzenia, które spowodowały to zdarzenie jest emitowany</span><span class="sxs-lookup"><span data-stu-id="bef7f-144">The name or the tracking profile that resulted in this event being emitted</span></span>|  
|<span data-ttu-id="bef7f-145">WorkflowDefinitionIdentity</span><span class="sxs-lookup"><span data-stu-id="bef7f-145">WorkflowDefinitionIdentity</span></span>|<span data-ttu-id="bef7f-146">xs:String</span><span class="sxs-lookup"><span data-stu-id="bef7f-146">xs:string</span></span>|<span data-ttu-id="bef7f-147">Identyfikator definicji przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="bef7f-147">The workflow definition id</span></span>|  
|<span data-ttu-id="bef7f-148">Domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="bef7f-148">AppDomain</span></span>|<span data-ttu-id="bef7f-149">xs:String</span><span class="sxs-lookup"><span data-stu-id="bef7f-149">xs:string</span></span>|<span data-ttu-id="bef7f-150">Długość ciągu zwróconego przez AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="bef7f-150">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
