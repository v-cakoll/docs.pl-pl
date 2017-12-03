---
title: 114 - WorkflowInstanceRecordWithId
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2bd8b4a1-b210-4c07-8156-f19392318c08
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: c7f6324d6d563ca19b16a76cff809649ad90e3dd
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="114---workflowinstancerecordwithid"></a><span data-ttu-id="8bcf3-102">114 - WorkflowInstanceRecordWithId</span><span class="sxs-lookup"><span data-stu-id="8bcf3-102">114 - WorkflowInstanceRecordWithId</span></span>
## <a name="properties"></a><span data-ttu-id="8bcf3-103">Właściwości</span><span class="sxs-lookup"><span data-stu-id="8bcf3-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="8bcf3-104">ID</span><span class="sxs-lookup"><span data-stu-id="8bcf3-104">ID</span></span>|<span data-ttu-id="8bcf3-105">114</span><span class="sxs-lookup"><span data-stu-id="8bcf3-105">114</span></span>|  
|<span data-ttu-id="8bcf3-106">Słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="8bcf3-106">Keywords</span></span>|<span data-ttu-id="8bcf3-107">HealthMonitoring, WFTracking</span><span class="sxs-lookup"><span data-stu-id="8bcf3-107">HealthMonitoring, WFTracking</span></span>|  
|<span data-ttu-id="8bcf3-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="8bcf3-108">Level</span></span>|<span data-ttu-id="8bcf3-109">Informacje</span><span class="sxs-lookup"><span data-stu-id="8bcf3-109">Information</span></span>|  
|<span data-ttu-id="8bcf3-110">Kanał</span><span class="sxs-lookup"><span data-stu-id="8bcf3-110">Channel</span></span>|<span data-ttu-id="8bcf3-111">Microsoft-Windows aplikacji Server aplikacje/analityczne</span><span class="sxs-lookup"><span data-stu-id="8bcf3-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="8bcf3-112">Opis</span><span class="sxs-lookup"><span data-stu-id="8bcf3-112">Description</span></span>  
 <span data-ttu-id="8bcf3-113">To zdarzenie jest emitowane przez uczestnika śledzenia zdarzeń systemu Windows, gdy wystąpienia przepływu pracy emituje WorkflowInstanceRecord dla stanów przepływu pracy: rozpoczęto wznowione, utrwalone, w stanie bezczynności, usunięty, zakończona, anulowana, zwalnianie, Anulowano.</span><span class="sxs-lookup"><span data-stu-id="8bcf3-113">This event is emitted by the ETW tracking participant when a workflow instance emits WorkflowInstanceRecord for workflow states : Started, Resumed, Persisted, Idle, Deleted, Completed, Canceled, Unloaded, Unsuspended.</span></span>  
  
## <a name="message"></a><span data-ttu-id="8bcf3-114">Komunikat</span><span class="sxs-lookup"><span data-stu-id="8bcf3-114">Message</span></span>  
 <span data-ttu-id="8bcf3-115">TrackRecord = WorkflowInstanceRecord, identyfikator wystąpienia = %1, RecordNumber = %2, EventTime = %3, obiekt ActivityDefinitionId = %4, stan = %5, adnotacje = %6, ProfileName = %7 WorkflowDefinitionIdentity = %8</span><span class="sxs-lookup"><span data-stu-id="8bcf3-115">TrackRecord= WorkflowInstanceRecord, InstanceID = %1, RecordNumber = %2, EventTime = %3, ActivityDefinitionId = %4, State = %5, Annotations = %6, ProfileName = %7, WorkflowDefinitionIdentity = %8</span></span>  
  
## <a name="details"></a><span data-ttu-id="8bcf3-116">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="8bcf3-116">Details</span></span>  
  
|<span data-ttu-id="8bcf3-117">Nazwa elementu danych</span><span class="sxs-lookup"><span data-stu-id="8bcf3-117">Data Item Name</span></span>|<span data-ttu-id="8bcf3-118">Typ elementu danych</span><span class="sxs-lookup"><span data-stu-id="8bcf3-118">Data Item Type</span></span>|<span data-ttu-id="8bcf3-119">Opis</span><span class="sxs-lookup"><span data-stu-id="8bcf3-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="8bcf3-120">Identyfikator wystąpienia</span><span class="sxs-lookup"><span data-stu-id="8bcf3-120">InstanceId</span></span>|<span data-ttu-id="8bcf3-121">xs:GUID</span><span class="sxs-lookup"><span data-stu-id="8bcf3-121">xs:GUID</span></span>|<span data-ttu-id="8bcf3-122">Identyfikator wystąpienia przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="8bcf3-122">The instance id for the workflow</span></span>|  
|<span data-ttu-id="8bcf3-123">RecordNumber</span><span class="sxs-lookup"><span data-stu-id="8bcf3-123">RecordNumber</span></span>|<span data-ttu-id="8bcf3-124">xs:Long</span><span class="sxs-lookup"><span data-stu-id="8bcf3-124">xs:long</span></span>|<span data-ttu-id="8bcf3-125">Numer sekwencyjny emitowany rekordu</span><span class="sxs-lookup"><span data-stu-id="8bcf3-125">The sequence number of the emitted record</span></span>|  
|<span data-ttu-id="8bcf3-126">eventTime</span><span class="sxs-lookup"><span data-stu-id="8bcf3-126">EventTime</span></span>|<span data-ttu-id="8bcf3-127">xs: DateTime</span><span class="sxs-lookup"><span data-stu-id="8bcf3-127">xs:dateTime</span></span>|<span data-ttu-id="8bcf3-128">Godzina w formacie UTC podczas zdarzenia zostały wyemitowane</span><span class="sxs-lookup"><span data-stu-id="8bcf3-128">The time in UTC when the event was emitted</span></span>|  
|<span data-ttu-id="8bcf3-129">Obiekt ActivityDefinitionId</span><span class="sxs-lookup"><span data-stu-id="8bcf3-129">ActivityDefinitionId</span></span>|<span data-ttu-id="8bcf3-130">xs:String</span><span class="sxs-lookup"><span data-stu-id="8bcf3-130">xs:string</span></span>|<span data-ttu-id="8bcf3-131">Nazwa działania głównego w przepływie pracy</span><span class="sxs-lookup"><span data-stu-id="8bcf3-131">The name of the root activity in the workflow</span></span>|  
|<span data-ttu-id="8bcf3-132">Stan</span><span class="sxs-lookup"><span data-stu-id="8bcf3-132">State</span></span>|<span data-ttu-id="8bcf3-133">xs:String</span><span class="sxs-lookup"><span data-stu-id="8bcf3-133">xs:string</span></span>|<span data-ttu-id="8bcf3-134">Bieżący stan przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="8bcf3-134">The current state of the Workflow.</span></span>|  
|<span data-ttu-id="8bcf3-135">Adnotacje</span><span class="sxs-lookup"><span data-stu-id="8bcf3-135">Annotations</span></span>|<span data-ttu-id="8bcf3-136">xs:String</span><span class="sxs-lookup"><span data-stu-id="8bcf3-136">xs:string</span></span>|<span data-ttu-id="8bcf3-137">Adnotacje, które zostały dodane do tego zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="8bcf3-137">The annotations that were added to this event.</span></span> <span data-ttu-id="8bcf3-138">Wartości są przechowywane w elemencie xml w formacie \<elementy >\< nazwa elementu = "annotationName" type="System.String" > annotationValue\</elementu > \< /elementy >.</span><span class="sxs-lookup"><span data-stu-id="8bcf3-138">The values are stored in an xml element in the format \<items>\< item name = "annotationName" type="System.String">annotationValue\</item>\</items>.</span></span> <span data-ttu-id="8bcf3-139">Jeśli nie określono bez adnotacji, a następnie ciąg zawiera \<elementów / >.</span><span class="sxs-lookup"><span data-stu-id="8bcf3-139">If no annotations are specified then the string contains \<items/>.</span></span> <span data-ttu-id="8bcf3-140">Rozmiar zdarzenia ETW jest ograniczona przez rozmiar bufora ETW lub max ładunku zdarzenia ETW.</span><span class="sxs-lookup"><span data-stu-id="8bcf3-140">The ETW event size is limited by the ETW buffer size or the max payload for an ETW event.</span></span> <span data-ttu-id="8bcf3-141">Jeśli limity ETW przekracza rozmiar zdarzenia, a następnie zdarzenia został obcięty przez usunięcie adnotacje i zastąpienie wartości adnotacji z \<elementy >...  \< /elementy >.</span><span class="sxs-lookup"><span data-stu-id="8bcf3-141">If the size of the event exceeds the ETW limits, then the event is truncated by dropping the annotations and replacing the annotation value with \<items>...\</items>.</span></span>|  
|<span data-ttu-id="8bcf3-142">ProfileName</span><span class="sxs-lookup"><span data-stu-id="8bcf3-142">ProfileName</span></span>|<span data-ttu-id="8bcf3-143">xs:String</span><span class="sxs-lookup"><span data-stu-id="8bcf3-143">xs:string</span></span>|<span data-ttu-id="8bcf3-144">Nazwa lub profilu śledzenia, które spowodowały to zdarzenie jest emitowany</span><span class="sxs-lookup"><span data-stu-id="8bcf3-144">The name or the tracking profile that resulted in this event being emitted</span></span>|  
|<span data-ttu-id="8bcf3-145">WorkflowDefinitionIdentity</span><span class="sxs-lookup"><span data-stu-id="8bcf3-145">WorkflowDefinitionIdentity</span></span>|<span data-ttu-id="8bcf3-146">xs:String</span><span class="sxs-lookup"><span data-stu-id="8bcf3-146">xs:string</span></span>|<span data-ttu-id="8bcf3-147">Identyfikator definicji przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="8bcf3-147">The workflow definition id</span></span>|  
|<span data-ttu-id="8bcf3-148">Domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="8bcf3-148">AppDomain</span></span>|<span data-ttu-id="8bcf3-149">xs:String</span><span class="sxs-lookup"><span data-stu-id="8bcf3-149">xs:string</span></span>|<span data-ttu-id="8bcf3-150">Długość ciągu zwróconego przez AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="8bcf3-150">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
