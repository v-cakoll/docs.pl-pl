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
ms.openlocfilehash: 76fee9673514287dd120a215fc843e4d995e68c0
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="appdomaininfo"></a><span data-ttu-id="aabae-102">AppDomainInfo</span><span class="sxs-lookup"><span data-stu-id="aabae-102">AppDomainInfo</span></span>
<span data-ttu-id="aabae-103">Informacje o domenie aplikacji</span><span class="sxs-lookup"><span data-stu-id="aabae-103">Application domain information</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aabae-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="aabae-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="aabae-105">Metody</span><span class="sxs-lookup"><span data-stu-id="aabae-105">Methods</span></span>  
 <span data-ttu-id="aabae-106">Klasa AppDomainInfo nie definiuje żadnych metod.</span><span class="sxs-lookup"><span data-stu-id="aabae-106">The AppDomainInfo class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="aabae-107">Właściwości</span><span class="sxs-lookup"><span data-stu-id="aabae-107">Properties</span></span>  
 <span data-ttu-id="aabae-108">Klasa AppDomainInfo ma następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="aabae-108">The AppDomainInfo class has the following properties:</span></span>  
  
### <a name="appdomainid"></a><span data-ttu-id="aabae-109">AppDomainId</span><span class="sxs-lookup"><span data-stu-id="aabae-109">AppDomainId</span></span>  
 <span data-ttu-id="aabae-110">Typ danych: sint32</span><span class="sxs-lookup"><span data-stu-id="aabae-110">Data type: sint32</span></span>  
  
 <span data-ttu-id="aabae-111">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="aabae-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="aabae-112">Identyfikator domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="aabae-112">The Id of the appdomain.</span></span>  
  
### <a name="isdefault"></a><span data-ttu-id="aabae-113">Wartość</span><span class="sxs-lookup"><span data-stu-id="aabae-113">IsDefault</span></span>  
 <span data-ttu-id="aabae-114">Typ danych: wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="aabae-114">Data type: boolean</span></span>  
  
 <span data-ttu-id="aabae-115">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="aabae-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="aabae-116">Wskazuje, czy domena aplikacji jest domyślną domeną.</span><span class="sxs-lookup"><span data-stu-id="aabae-116">Indicates whether the appdomain is the default appdomain.</span></span>  
  
### <a name="logmalformedmessages"></a><span data-ttu-id="aabae-117">LogMalformedMessages</span><span class="sxs-lookup"><span data-stu-id="aabae-117">LogMalformedMessages</span></span>  
 <span data-ttu-id="aabae-118">Typ danych: wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="aabae-118">Data type: boolean</span></span>  
  
 <span data-ttu-id="aabae-119">Dostęp typu: odczytu/zapisu</span><span class="sxs-lookup"><span data-stu-id="aabae-119">Access type: Read/Write</span></span>  
  
 <span data-ttu-id="aabae-120">Wartość określająca, czy wadliwe komunikaty są rejestrowane.</span><span class="sxs-lookup"><span data-stu-id="aabae-120">A value that specifies whether malformed messages are logged.</span></span>  
  
### <a name="logmessagesatservicelevel"></a><span data-ttu-id="aabae-121">LogMessagesAtServiceLevel</span><span class="sxs-lookup"><span data-stu-id="aabae-121">LogMessagesAtServiceLevel</span></span>  
 <span data-ttu-id="aabae-122">Typ danych: wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="aabae-122">Data type: boolean</span></span>  
  
 <span data-ttu-id="aabae-123">Dostęp typu: odczytu/zapisu</span><span class="sxs-lookup"><span data-stu-id="aabae-123">Access type: Read/Write</span></span>  
  
 <span data-ttu-id="aabae-124">Wartość, która określa, czy komunikaty są śledzone na poziomie usługi (przed zaszyfrowaniem i transformacjami związanymi z transportem).</span><span class="sxs-lookup"><span data-stu-id="aabae-124">A value that specifies whether messages are traced at the service level (before encryption and transport-related transforms).</span></span>  
  
### <a name="logmessagesattransportlevel"></a><span data-ttu-id="aabae-125">LogMessagesAtTransportLevel</span><span class="sxs-lookup"><span data-stu-id="aabae-125">LogMessagesAtTransportLevel</span></span>  
 <span data-ttu-id="aabae-126">Typ danych: wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="aabae-126">Data type: boolean</span></span>  
  
 <span data-ttu-id="aabae-127">Dostęp typu: odczytu/zapisu</span><span class="sxs-lookup"><span data-stu-id="aabae-127">Access type: Read/Write</span></span>  
  
 <span data-ttu-id="aabae-128">Wartość, która określa, czy komunikaty są śledzone na poziomie transportu.</span><span class="sxs-lookup"><span data-stu-id="aabae-128">A value that specifies whether messages are traced at the transport level.</span></span>  
  
### <a name="messageloggingtracelisteners"></a><span data-ttu-id="aabae-129">MessageLoggingTraceListeners</span><span class="sxs-lookup"><span data-stu-id="aabae-129">MessageLoggingTraceListeners</span></span>  
 <span data-ttu-id="aabae-130">Typ danych: TraceListener tablicy</span><span class="sxs-lookup"><span data-stu-id="aabae-130">Data type: TraceListener array</span></span>  
  
 <span data-ttu-id="aabae-131">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="aabae-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="aabae-132">Kolekcja obiektów nasłuchujących śledzenia System.Wmi.MessageLogging źródła śledzenia.</span><span class="sxs-lookup"><span data-stu-id="aabae-132">The collection trace listeners that listen to the System.Wmi.MessageLogging trace source.</span></span>  
  
### <a name="name"></a><span data-ttu-id="aabae-133">Nazwa</span><span class="sxs-lookup"><span data-stu-id="aabae-133">Name</span></span>  
 <span data-ttu-id="aabae-134">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="aabae-134">Data type: string</span></span>  
  
 <span data-ttu-id="aabae-135">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="aabae-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="aabae-136">Nazwa elementu appdomain.</span><span class="sxs-lookup"><span data-stu-id="aabae-136">The name of the appdomain.</span></span>  
  
### <a name="performancecounters"></a><span data-ttu-id="aabae-137">liczniki wydajności</span><span class="sxs-lookup"><span data-stu-id="aabae-137">PerformanceCounters</span></span>  
 <span data-ttu-id="aabae-138">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="aabae-138">Data type: string</span></span>  
  
 <span data-ttu-id="aabae-139">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="aabae-139">Access type: Read-only</span></span>  
  
 <span data-ttu-id="aabae-140">Zakres aktywnych liczników wydajności w domenie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="aabae-140">The scope of active performance counters in the appdomain.</span></span>  
  
### <a name="processid"></a><span data-ttu-id="aabae-141">Identyfikator procesu</span><span class="sxs-lookup"><span data-stu-id="aabae-141">ProcessId</span></span>  
 <span data-ttu-id="aabae-142">Typ danych: sint32</span><span class="sxs-lookup"><span data-stu-id="aabae-142">Data type: sint32</span></span>  
  
 <span data-ttu-id="aabae-143">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="aabae-143">Access type: Read-only</span></span>  
  
 <span data-ttu-id="aabae-144">Identyfikator procesu.</span><span class="sxs-lookup"><span data-stu-id="aabae-144">The process Id.</span></span>  
  
### <a name="serviceconfigpath"></a><span data-ttu-id="aabae-145">ServiceConfigPath</span><span class="sxs-lookup"><span data-stu-id="aabae-145">ServiceConfigPath</span></span>  
 <span data-ttu-id="aabae-146">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="aabae-146">Data type: string</span></span>  
  
 <span data-ttu-id="aabae-147">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="aabae-147">Access type: Read-only</span></span>  
  
 <span data-ttu-id="aabae-148">Ścieżka do konfiguracji usługi.</span><span class="sxs-lookup"><span data-stu-id="aabae-148">The path to the configuration of the service.</span></span>  
  
### <a name="tracelevel"></a><span data-ttu-id="aabae-149">TraceLevel</span><span class="sxs-lookup"><span data-stu-id="aabae-149">TraceLevel</span></span>  
 <span data-ttu-id="aabae-150">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="aabae-150">Data type: string</span></span>  
  
 <span data-ttu-id="aabae-151">Dostęp typu: odczytu/zapisu</span><span class="sxs-lookup"><span data-stu-id="aabae-151">Access type: Read/Write</span></span>  
  
 <span data-ttu-id="aabae-152">Poziom śledzenia źródła śledzenia System.Wmi.</span><span class="sxs-lookup"><span data-stu-id="aabae-152">The trace level of the System.Wmi trace source.</span></span>  
  
### <a name="servicemodeltracelisteners"></a><span data-ttu-id="aabae-153">ServiceModelTraceListeners</span><span class="sxs-lookup"><span data-stu-id="aabae-153">ServiceModelTraceListeners</span></span>  
 <span data-ttu-id="aabae-154">Typ danych: TraceListener tablicy</span><span class="sxs-lookup"><span data-stu-id="aabae-154">Data type: TraceListener array</span></span>  
  
 <span data-ttu-id="aabae-155">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="aabae-155">Access type: Read-only</span></span>  
  
 <span data-ttu-id="aabae-156">Kolekcja obiektów nasłuchujących ze źródła System.ServiceModel.</span><span class="sxs-lookup"><span data-stu-id="aabae-156">A collection of listeners from the System.ServiceModel trace source.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="aabae-157">Wymagania</span><span class="sxs-lookup"><span data-stu-id="aabae-157">Requirements</span></span>  
  
|<span data-ttu-id="aabae-158">MOF</span><span class="sxs-lookup"><span data-stu-id="aabae-158">MOF</span></span>|<span data-ttu-id="aabae-159">Zadeklarowany w Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="aabae-159">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="aabae-160">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="aabae-160">Namespace</span></span>|<span data-ttu-id="aabae-161">Zdefiniowany w root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="aabae-161">Defined in root\ServiceModel</span></span>|
