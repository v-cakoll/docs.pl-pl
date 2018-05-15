---
title: AppDomainInfo
ms.date: 03/30/2017
ms.assetid: 6610b7d8-81eb-4bec-a543-9b72ad7b6f73
ms.openlocfilehash: 7189448a930298837089cf3ac2743cb7e073ae02
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="appdomaininfo"></a><span data-ttu-id="18890-102">AppDomainInfo</span><span class="sxs-lookup"><span data-stu-id="18890-102">AppDomainInfo</span></span>
<span data-ttu-id="18890-103">Informacje o domenie aplikacji</span><span class="sxs-lookup"><span data-stu-id="18890-103">Application domain information</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="18890-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="18890-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="18890-105">Metody</span><span class="sxs-lookup"><span data-stu-id="18890-105">Methods</span></span>  
 <span data-ttu-id="18890-106">Klasa AppDomainInfo nie definiuje żadnych metod.</span><span class="sxs-lookup"><span data-stu-id="18890-106">The AppDomainInfo class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="18890-107">Właściwości</span><span class="sxs-lookup"><span data-stu-id="18890-107">Properties</span></span>  
 <span data-ttu-id="18890-108">Klasa AppDomainInfo ma następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="18890-108">The AppDomainInfo class has the following properties:</span></span>  
  
### <a name="appdomainid"></a><span data-ttu-id="18890-109">AppDomainId</span><span class="sxs-lookup"><span data-stu-id="18890-109">AppDomainId</span></span>  
 <span data-ttu-id="18890-110">Typ danych: sint32</span><span class="sxs-lookup"><span data-stu-id="18890-110">Data type: sint32</span></span>  
  
 <span data-ttu-id="18890-111">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="18890-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="18890-112">Identyfikator domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="18890-112">The Id of the appdomain.</span></span>  
  
### <a name="isdefault"></a><span data-ttu-id="18890-113">Wartość</span><span class="sxs-lookup"><span data-stu-id="18890-113">IsDefault</span></span>  
 <span data-ttu-id="18890-114">Typ danych: wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="18890-114">Data type: boolean</span></span>  
  
 <span data-ttu-id="18890-115">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="18890-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="18890-116">Wskazuje, czy domena aplikacji jest domyślną domeną.</span><span class="sxs-lookup"><span data-stu-id="18890-116">Indicates whether the appdomain is the default appdomain.</span></span>  
  
### <a name="logmalformedmessages"></a><span data-ttu-id="18890-117">LogMalformedMessages</span><span class="sxs-lookup"><span data-stu-id="18890-117">LogMalformedMessages</span></span>  
 <span data-ttu-id="18890-118">Typ danych: wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="18890-118">Data type: boolean</span></span>  
  
 <span data-ttu-id="18890-119">Dostęp typu: odczytu/zapisu</span><span class="sxs-lookup"><span data-stu-id="18890-119">Access type: Read/Write</span></span>  
  
 <span data-ttu-id="18890-120">Wartość określająca, czy wadliwe komunikaty są rejestrowane.</span><span class="sxs-lookup"><span data-stu-id="18890-120">A value that specifies whether malformed messages are logged.</span></span>  
  
### <a name="logmessagesatservicelevel"></a><span data-ttu-id="18890-121">LogMessagesAtServiceLevel</span><span class="sxs-lookup"><span data-stu-id="18890-121">LogMessagesAtServiceLevel</span></span>  
 <span data-ttu-id="18890-122">Typ danych: wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="18890-122">Data type: boolean</span></span>  
  
 <span data-ttu-id="18890-123">Dostęp typu: odczytu/zapisu</span><span class="sxs-lookup"><span data-stu-id="18890-123">Access type: Read/Write</span></span>  
  
 <span data-ttu-id="18890-124">Wartość, która określa, czy komunikaty są śledzone na poziomie usługi (przed zaszyfrowaniem i transformacjami związanymi z transportem).</span><span class="sxs-lookup"><span data-stu-id="18890-124">A value that specifies whether messages are traced at the service level (before encryption and transport-related transforms).</span></span>  
  
### <a name="logmessagesattransportlevel"></a><span data-ttu-id="18890-125">LogMessagesAtTransportLevel</span><span class="sxs-lookup"><span data-stu-id="18890-125">LogMessagesAtTransportLevel</span></span>  
 <span data-ttu-id="18890-126">Typ danych: wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="18890-126">Data type: boolean</span></span>  
  
 <span data-ttu-id="18890-127">Dostęp typu: odczytu/zapisu</span><span class="sxs-lookup"><span data-stu-id="18890-127">Access type: Read/Write</span></span>  
  
 <span data-ttu-id="18890-128">Wartość, która określa, czy komunikaty są śledzone na poziomie transportu.</span><span class="sxs-lookup"><span data-stu-id="18890-128">A value that specifies whether messages are traced at the transport level.</span></span>  
  
### <a name="messageloggingtracelisteners"></a><span data-ttu-id="18890-129">MessageLoggingTraceListeners</span><span class="sxs-lookup"><span data-stu-id="18890-129">MessageLoggingTraceListeners</span></span>  
 <span data-ttu-id="18890-130">Typ danych: TraceListener tablicy</span><span class="sxs-lookup"><span data-stu-id="18890-130">Data type: TraceListener array</span></span>  
  
 <span data-ttu-id="18890-131">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="18890-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="18890-132">Kolekcja obiektów nasłuchujących śledzenia System.Wmi.MessageLogging źródła śledzenia.</span><span class="sxs-lookup"><span data-stu-id="18890-132">The collection trace listeners that listen to the System.Wmi.MessageLogging trace source.</span></span>  
  
### <a name="name"></a><span data-ttu-id="18890-133">Nazwa</span><span class="sxs-lookup"><span data-stu-id="18890-133">Name</span></span>  
 <span data-ttu-id="18890-134">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="18890-134">Data type: string</span></span>  
  
 <span data-ttu-id="18890-135">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="18890-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="18890-136">Nazwa elementu appdomain.</span><span class="sxs-lookup"><span data-stu-id="18890-136">The name of the appdomain.</span></span>  
  
### <a name="performancecounters"></a><span data-ttu-id="18890-137">liczniki wydajności</span><span class="sxs-lookup"><span data-stu-id="18890-137">PerformanceCounters</span></span>  
 <span data-ttu-id="18890-138">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="18890-138">Data type: string</span></span>  
  
 <span data-ttu-id="18890-139">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="18890-139">Access type: Read-only</span></span>  
  
 <span data-ttu-id="18890-140">Zakres aktywnych liczników wydajności w domenie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="18890-140">The scope of active performance counters in the appdomain.</span></span>  
  
### <a name="processid"></a><span data-ttu-id="18890-141">Identyfikator procesu</span><span class="sxs-lookup"><span data-stu-id="18890-141">ProcessId</span></span>  
 <span data-ttu-id="18890-142">Typ danych: sint32</span><span class="sxs-lookup"><span data-stu-id="18890-142">Data type: sint32</span></span>  
  
 <span data-ttu-id="18890-143">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="18890-143">Access type: Read-only</span></span>  
  
 <span data-ttu-id="18890-144">Identyfikator procesu.</span><span class="sxs-lookup"><span data-stu-id="18890-144">The process Id.</span></span>  
  
### <a name="serviceconfigpath"></a><span data-ttu-id="18890-145">ServiceConfigPath</span><span class="sxs-lookup"><span data-stu-id="18890-145">ServiceConfigPath</span></span>  
 <span data-ttu-id="18890-146">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="18890-146">Data type: string</span></span>  
  
 <span data-ttu-id="18890-147">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="18890-147">Access type: Read-only</span></span>  
  
 <span data-ttu-id="18890-148">Ścieżka do konfiguracji usługi.</span><span class="sxs-lookup"><span data-stu-id="18890-148">The path to the configuration of the service.</span></span>  
  
### <a name="tracelevel"></a><span data-ttu-id="18890-149">TraceLevel</span><span class="sxs-lookup"><span data-stu-id="18890-149">TraceLevel</span></span>  
 <span data-ttu-id="18890-150">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="18890-150">Data type: string</span></span>  
  
 <span data-ttu-id="18890-151">Dostęp typu: odczytu/zapisu</span><span class="sxs-lookup"><span data-stu-id="18890-151">Access type: Read/Write</span></span>  
  
 <span data-ttu-id="18890-152">Poziom śledzenia źródła śledzenia System.Wmi.</span><span class="sxs-lookup"><span data-stu-id="18890-152">The trace level of the System.Wmi trace source.</span></span>  
  
### <a name="servicemodeltracelisteners"></a><span data-ttu-id="18890-153">ServiceModelTraceListeners</span><span class="sxs-lookup"><span data-stu-id="18890-153">ServiceModelTraceListeners</span></span>  
 <span data-ttu-id="18890-154">Typ danych: TraceListener tablicy</span><span class="sxs-lookup"><span data-stu-id="18890-154">Data type: TraceListener array</span></span>  
  
 <span data-ttu-id="18890-155">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="18890-155">Access type: Read-only</span></span>  
  
 <span data-ttu-id="18890-156">Kolekcja obiektów nasłuchujących ze źródła System.ServiceModel.</span><span class="sxs-lookup"><span data-stu-id="18890-156">A collection of listeners from the System.ServiceModel trace source.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="18890-157">Wymagania</span><span class="sxs-lookup"><span data-stu-id="18890-157">Requirements</span></span>  
  
|<span data-ttu-id="18890-158">MOF</span><span class="sxs-lookup"><span data-stu-id="18890-158">MOF</span></span>|<span data-ttu-id="18890-159">Zadeklarowany w Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="18890-159">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="18890-160">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="18890-160">Namespace</span></span>|<span data-ttu-id="18890-161">Zdefiniowany w root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="18890-161">Defined in root\ServiceModel</span></span>|
