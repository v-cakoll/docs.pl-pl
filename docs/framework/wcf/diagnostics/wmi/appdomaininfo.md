---
title: AppDomainInfo
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6610b7d8-81eb-4bec-a543-9b72ad7b6f73
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ed5053dd69628a9f5ff7318ce7fe772f42de6e24
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="appdomaininfo"></a><span data-ttu-id="0969d-102">AppDomainInfo</span><span class="sxs-lookup"><span data-stu-id="0969d-102">AppDomainInfo</span></span>
<span data-ttu-id="0969d-103">Informacje o domenie aplikacji</span><span class="sxs-lookup"><span data-stu-id="0969d-103">Application domain information</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0969d-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="0969d-104">Syntax</span></span>  
  
```  
class AppDomainInfo  
{  
  sint32 AppDomainId;  
  boolean IsDefault;  
  boolean LogMalformedMessages;  
  boolean LogMessagesAtServiceLevel;  
  boolean LogMessagesAtTransportLevel;  
  TraceListener MessageLoggingTraceListeners[];  
  string Name;  
  string PerformanceCounters;  
  sint32 ProcessId;  
  string ServiceConfigPath;  
  string TraceLevel;  
  TraceListener wmiTraceListeners[];  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="0969d-105">Metody</span><span class="sxs-lookup"><span data-stu-id="0969d-105">Methods</span></span>  
 <span data-ttu-id="0969d-106">Klasa AppDomainInfo nie definiuje żadnych metod.</span><span class="sxs-lookup"><span data-stu-id="0969d-106">The AppDomainInfo class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="0969d-107">Właściwości</span><span class="sxs-lookup"><span data-stu-id="0969d-107">Properties</span></span>  
 <span data-ttu-id="0969d-108">Klasa AppDomainInfo ma następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="0969d-108">The AppDomainInfo class has the following properties:</span></span>  
  
### <a name="appdomainid"></a><span data-ttu-id="0969d-109">AppDomainId</span><span class="sxs-lookup"><span data-stu-id="0969d-109">AppDomainId</span></span>  
 <span data-ttu-id="0969d-110">Typ danych: sint32</span><span class="sxs-lookup"><span data-stu-id="0969d-110">Data type: sint32</span></span>  
  
 <span data-ttu-id="0969d-111">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="0969d-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="0969d-112">Identyfikator domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="0969d-112">The Id of the appdomain.</span></span>  
  
### <a name="isdefault"></a><span data-ttu-id="0969d-113">Wartość</span><span class="sxs-lookup"><span data-stu-id="0969d-113">IsDefault</span></span>  
 <span data-ttu-id="0969d-114">Typ danych: wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="0969d-114">Data type: boolean</span></span>  
  
 <span data-ttu-id="0969d-115">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="0969d-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="0969d-116">Wskazuje, czy domena aplikacji jest domyślną domeną.</span><span class="sxs-lookup"><span data-stu-id="0969d-116">Indicates whether the appdomain is the default appdomain.</span></span>  
  
### <a name="logmalformedmessages"></a><span data-ttu-id="0969d-117">LogMalformedMessages</span><span class="sxs-lookup"><span data-stu-id="0969d-117">LogMalformedMessages</span></span>  
 <span data-ttu-id="0969d-118">Typ danych: wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="0969d-118">Data type: boolean</span></span>  
  
 <span data-ttu-id="0969d-119">Dostęp typu: odczytu/zapisu</span><span class="sxs-lookup"><span data-stu-id="0969d-119">Access type: Read/Write</span></span>  
  
 <span data-ttu-id="0969d-120">Wartość określająca, czy wadliwe komunikaty są rejestrowane.</span><span class="sxs-lookup"><span data-stu-id="0969d-120">A value that specifies whether malformed messages are logged.</span></span>  
  
### <a name="logmessagesatservicelevel"></a><span data-ttu-id="0969d-121">LogMessagesAtServiceLevel</span><span class="sxs-lookup"><span data-stu-id="0969d-121">LogMessagesAtServiceLevel</span></span>  
 <span data-ttu-id="0969d-122">Typ danych: wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="0969d-122">Data type: boolean</span></span>  
  
 <span data-ttu-id="0969d-123">Dostęp typu: odczytu/zapisu</span><span class="sxs-lookup"><span data-stu-id="0969d-123">Access type: Read/Write</span></span>  
  
 <span data-ttu-id="0969d-124">Wartość, która określa, czy komunikaty są śledzone na poziomie usługi (przed zaszyfrowaniem i transformacjami związanymi z transportem).</span><span class="sxs-lookup"><span data-stu-id="0969d-124">A value that specifies whether messages are traced at the service level (before encryption and transport-related transforms).</span></span>  
  
### <a name="logmessagesattransportlevel"></a><span data-ttu-id="0969d-125">LogMessagesAtTransportLevel</span><span class="sxs-lookup"><span data-stu-id="0969d-125">LogMessagesAtTransportLevel</span></span>  
 <span data-ttu-id="0969d-126">Typ danych: wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="0969d-126">Data type: boolean</span></span>  
  
 <span data-ttu-id="0969d-127">Dostęp typu: odczytu/zapisu</span><span class="sxs-lookup"><span data-stu-id="0969d-127">Access type: Read/Write</span></span>  
  
 <span data-ttu-id="0969d-128">Wartość, która określa, czy komunikaty są śledzone na poziomie transportu.</span><span class="sxs-lookup"><span data-stu-id="0969d-128">A value that specifies whether messages are traced at the transport level.</span></span>  
  
### <a name="messageloggingtracelisteners"></a><span data-ttu-id="0969d-129">MessageLoggingTraceListeners</span><span class="sxs-lookup"><span data-stu-id="0969d-129">MessageLoggingTraceListeners</span></span>  
 <span data-ttu-id="0969d-130">Typ danych: TraceListener tablicy</span><span class="sxs-lookup"><span data-stu-id="0969d-130">Data type: TraceListener array</span></span>  
  
 <span data-ttu-id="0969d-131">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="0969d-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="0969d-132">Kolekcja obiektów nasłuchujących śledzenia System.Wmi.MessageLogging źródła śledzenia.</span><span class="sxs-lookup"><span data-stu-id="0969d-132">The collection trace listeners that listen to the System.Wmi.MessageLogging trace source.</span></span>  
  
### <a name="name"></a><span data-ttu-id="0969d-133">Nazwa</span><span class="sxs-lookup"><span data-stu-id="0969d-133">Name</span></span>  
 <span data-ttu-id="0969d-134">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="0969d-134">Data type: string</span></span>  
  
 <span data-ttu-id="0969d-135">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="0969d-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="0969d-136">Nazwa elementu appdomain.</span><span class="sxs-lookup"><span data-stu-id="0969d-136">The name of the appdomain.</span></span>  
  
### <a name="performancecounters"></a><span data-ttu-id="0969d-137">liczniki wydajności</span><span class="sxs-lookup"><span data-stu-id="0969d-137">PerformanceCounters</span></span>  
 <span data-ttu-id="0969d-138">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="0969d-138">Data type: string</span></span>  
  
 <span data-ttu-id="0969d-139">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="0969d-139">Access type: Read-only</span></span>  
  
 <span data-ttu-id="0969d-140">Zakres aktywnych liczników wydajności w domenie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="0969d-140">The scope of active performance counters in the appdomain.</span></span>  
  
### <a name="processid"></a><span data-ttu-id="0969d-141">Identyfikator procesu</span><span class="sxs-lookup"><span data-stu-id="0969d-141">ProcessId</span></span>  
 <span data-ttu-id="0969d-142">Typ danych: sint32</span><span class="sxs-lookup"><span data-stu-id="0969d-142">Data type: sint32</span></span>  
  
 <span data-ttu-id="0969d-143">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="0969d-143">Access type: Read-only</span></span>  
  
 <span data-ttu-id="0969d-144">Identyfikator procesu.</span><span class="sxs-lookup"><span data-stu-id="0969d-144">The process Id.</span></span>  
  
### <a name="serviceconfigpath"></a><span data-ttu-id="0969d-145">ServiceConfigPath</span><span class="sxs-lookup"><span data-stu-id="0969d-145">ServiceConfigPath</span></span>  
 <span data-ttu-id="0969d-146">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="0969d-146">Data type: string</span></span>  
  
 <span data-ttu-id="0969d-147">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="0969d-147">Access type: Read-only</span></span>  
  
 <span data-ttu-id="0969d-148">Ścieżka do konfiguracji usługi.</span><span class="sxs-lookup"><span data-stu-id="0969d-148">The path to the configuration of the service.</span></span>  
  
### <a name="tracelevel"></a><span data-ttu-id="0969d-149">TraceLevel</span><span class="sxs-lookup"><span data-stu-id="0969d-149">TraceLevel</span></span>  
 <span data-ttu-id="0969d-150">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="0969d-150">Data type: string</span></span>  
  
 <span data-ttu-id="0969d-151">Dostęp typu: odczytu/zapisu</span><span class="sxs-lookup"><span data-stu-id="0969d-151">Access type: Read/Write</span></span>  
  
 <span data-ttu-id="0969d-152">Poziom śledzenia źródła śledzenia System.Wmi.</span><span class="sxs-lookup"><span data-stu-id="0969d-152">The trace level of the System.Wmi trace source.</span></span>  
  
### <a name="servicemodeltracelisteners"></a><span data-ttu-id="0969d-153">ServiceModelTraceListeners</span><span class="sxs-lookup"><span data-stu-id="0969d-153">ServiceModelTraceListeners</span></span>  
 <span data-ttu-id="0969d-154">Typ danych: TraceListener tablicy</span><span class="sxs-lookup"><span data-stu-id="0969d-154">Data type: TraceListener array</span></span>  
  
 <span data-ttu-id="0969d-155">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="0969d-155">Access type: Read-only</span></span>  
  
 <span data-ttu-id="0969d-156">Kolekcja obiektów nasłuchujących ze źródła System.ServiceModel.</span><span class="sxs-lookup"><span data-stu-id="0969d-156">A collection of listeners from the System.ServiceModel trace source.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0969d-157">Wymagania</span><span class="sxs-lookup"><span data-stu-id="0969d-157">Requirements</span></span>  
  
|<span data-ttu-id="0969d-158">MOF</span><span class="sxs-lookup"><span data-stu-id="0969d-158">MOF</span></span>|<span data-ttu-id="0969d-159">Zadeklarowany w Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="0969d-159">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="0969d-160">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="0969d-160">Namespace</span></span>|<span data-ttu-id="0969d-161">Zdefiniowany w root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="0969d-161">Defined in root\ServiceModel</span></span>|
