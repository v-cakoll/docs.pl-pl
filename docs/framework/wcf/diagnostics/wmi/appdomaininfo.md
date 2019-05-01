---
title: AppDomainInfo
ms.date: 03/30/2017
ms.assetid: 6610b7d8-81eb-4bec-a543-9b72ad7b6f73
ms.openlocfilehash: 0b7f8aadbd9a9dfcdd33fc65be3a5a41ea95f5be
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61964258"
---
# <a name="appdomaininfo"></a><span data-ttu-id="4913e-102">AppDomainInfo</span><span class="sxs-lookup"><span data-stu-id="4913e-102">AppDomainInfo</span></span>
<span data-ttu-id="4913e-103">Informacje o domenie aplikacji</span><span class="sxs-lookup"><span data-stu-id="4913e-103">Application domain information</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4913e-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="4913e-104">Syntax</span></span>  
  
```csharp
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
  
## <a name="methods"></a><span data-ttu-id="4913e-105">Metody</span><span class="sxs-lookup"><span data-stu-id="4913e-105">Methods</span></span>  
 <span data-ttu-id="4913e-106">Klasa AppDomainInfo nie definiuje żadnych metod.</span><span class="sxs-lookup"><span data-stu-id="4913e-106">The AppDomainInfo class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="4913e-107">Właściwości</span><span class="sxs-lookup"><span data-stu-id="4913e-107">Properties</span></span>  
 <span data-ttu-id="4913e-108">Klasa AppDomainInfo ma następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="4913e-108">The AppDomainInfo class has the following properties:</span></span>  
  
### <a name="appdomainid"></a><span data-ttu-id="4913e-109">AppDomainId</span><span class="sxs-lookup"><span data-stu-id="4913e-109">AppDomainId</span></span>  
 <span data-ttu-id="4913e-110">Typ danych: sint32</span><span class="sxs-lookup"><span data-stu-id="4913e-110">Data type: sint32</span></span>  
  
 <span data-ttu-id="4913e-111">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="4913e-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="4913e-112">Identyfikator elementu appdomain.</span><span class="sxs-lookup"><span data-stu-id="4913e-112">The Id of the appdomain.</span></span>  
  
### <a name="isdefault"></a><span data-ttu-id="4913e-113">IsDefault</span><span class="sxs-lookup"><span data-stu-id="4913e-113">IsDefault</span></span>  
 <span data-ttu-id="4913e-114">Typ danych: wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="4913e-114">Data type: boolean</span></span>  
  
 <span data-ttu-id="4913e-115">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="4913e-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="4913e-116">Wskazuje, czy element appdomain jest domyślnej domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="4913e-116">Indicates whether the appdomain is the default appdomain.</span></span>  
  
### <a name="logmalformedmessages"></a><span data-ttu-id="4913e-117">LogMalformedMessages</span><span class="sxs-lookup"><span data-stu-id="4913e-117">LogMalformedMessages</span></span>  
 <span data-ttu-id="4913e-118">Typ danych: wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="4913e-118">Data type: boolean</span></span>  
  
 <span data-ttu-id="4913e-119">Typ dostępu: Odczyt/zapis</span><span class="sxs-lookup"><span data-stu-id="4913e-119">Access type: Read/Write</span></span>  
  
 <span data-ttu-id="4913e-120">Wartość, która określa, czy wadliwe komunikaty są rejestrowane.</span><span class="sxs-lookup"><span data-stu-id="4913e-120">A value that specifies whether malformed messages are logged.</span></span>  
  
### <a name="logmessagesatservicelevel"></a><span data-ttu-id="4913e-121">LogMessagesAtServiceLevel</span><span class="sxs-lookup"><span data-stu-id="4913e-121">LogMessagesAtServiceLevel</span></span>  
 <span data-ttu-id="4913e-122">Typ danych: wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="4913e-122">Data type: boolean</span></span>  
  
 <span data-ttu-id="4913e-123">Typ dostępu: Odczyt/zapis</span><span class="sxs-lookup"><span data-stu-id="4913e-123">Access type: Read/Write</span></span>  
  
 <span data-ttu-id="4913e-124">Wartość, która określa, czy komunikaty są śledzone na poziomie usługi (przed zaszyfrowaniem i transformacjami związanymi z transportem).</span><span class="sxs-lookup"><span data-stu-id="4913e-124">A value that specifies whether messages are traced at the service level (before encryption and transport-related transforms).</span></span>  
  
### <a name="logmessagesattransportlevel"></a><span data-ttu-id="4913e-125">LogMessagesAtTransportLevel</span><span class="sxs-lookup"><span data-stu-id="4913e-125">LogMessagesAtTransportLevel</span></span>  
 <span data-ttu-id="4913e-126">Typ danych: wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="4913e-126">Data type: boolean</span></span>  
  
 <span data-ttu-id="4913e-127">Typ dostępu: Odczyt/zapis</span><span class="sxs-lookup"><span data-stu-id="4913e-127">Access type: Read/Write</span></span>  
  
 <span data-ttu-id="4913e-128">Wartość, która określa, czy komunikaty są śledzone na poziomie transportu.</span><span class="sxs-lookup"><span data-stu-id="4913e-128">A value that specifies whether messages are traced at the transport level.</span></span>  
  
### <a name="messageloggingtracelisteners"></a><span data-ttu-id="4913e-129">MessageLoggingTraceListeners</span><span class="sxs-lookup"><span data-stu-id="4913e-129">MessageLoggingTraceListeners</span></span>  
 <span data-ttu-id="4913e-130">Typ danych: Tablica zdarzeń TraceListener</span><span class="sxs-lookup"><span data-stu-id="4913e-130">Data type: TraceListener array</span></span>  
  
 <span data-ttu-id="4913e-131">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="4913e-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="4913e-132">Kolekcja obiektów nasłuchujących śledzenia System.Wmi.MessageLogging źródła śledzenia.</span><span class="sxs-lookup"><span data-stu-id="4913e-132">The collection trace listeners that listen to the System.Wmi.MessageLogging trace source.</span></span>  
  
### <a name="name"></a><span data-ttu-id="4913e-133">Nazwa</span><span class="sxs-lookup"><span data-stu-id="4913e-133">Name</span></span>  
 <span data-ttu-id="4913e-134">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="4913e-134">Data type: string</span></span>  
  
 <span data-ttu-id="4913e-135">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="4913e-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="4913e-136">Nazwa domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="4913e-136">The name of the appdomain.</span></span>  
  
### <a name="performancecounters"></a><span data-ttu-id="4913e-137">Liczniki wydajności</span><span class="sxs-lookup"><span data-stu-id="4913e-137">PerformanceCounters</span></span>  
 <span data-ttu-id="4913e-138">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="4913e-138">Data type: string</span></span>  
  
 <span data-ttu-id="4913e-139">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="4913e-139">Access type: Read-only</span></span>  
  
 <span data-ttu-id="4913e-140">Zakres aktywnych liczników wydajności w domenie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="4913e-140">The scope of active performance counters in the appdomain.</span></span>  
  
### <a name="processid"></a><span data-ttu-id="4913e-141">Identyfikator procesu</span><span class="sxs-lookup"><span data-stu-id="4913e-141">ProcessId</span></span>  
 <span data-ttu-id="4913e-142">Typ danych: sint32</span><span class="sxs-lookup"><span data-stu-id="4913e-142">Data type: sint32</span></span>  
  
 <span data-ttu-id="4913e-143">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="4913e-143">Access type: Read-only</span></span>  
  
 <span data-ttu-id="4913e-144">Identyfikator procesu.</span><span class="sxs-lookup"><span data-stu-id="4913e-144">The process Id.</span></span>  
  
### <a name="serviceconfigpath"></a><span data-ttu-id="4913e-145">ServiceConfigPath</span><span class="sxs-lookup"><span data-stu-id="4913e-145">ServiceConfigPath</span></span>  
 <span data-ttu-id="4913e-146">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="4913e-146">Data type: string</span></span>  
  
 <span data-ttu-id="4913e-147">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="4913e-147">Access type: Read-only</span></span>  
  
 <span data-ttu-id="4913e-148">Ścieżka do konfiguracji usługi.</span><span class="sxs-lookup"><span data-stu-id="4913e-148">The path to the configuration of the service.</span></span>  
  
### <a name="tracelevel"></a><span data-ttu-id="4913e-149">TraceLevel</span><span class="sxs-lookup"><span data-stu-id="4913e-149">TraceLevel</span></span>  
 <span data-ttu-id="4913e-150">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="4913e-150">Data type: string</span></span>  
  
 <span data-ttu-id="4913e-151">Typ dostępu: Odczyt/zapis</span><span class="sxs-lookup"><span data-stu-id="4913e-151">Access type: Read/Write</span></span>  
  
 <span data-ttu-id="4913e-152">Poziom śledzenia System.Wmi źródła śledzenia.</span><span class="sxs-lookup"><span data-stu-id="4913e-152">The trace level of the System.Wmi trace source.</span></span>  
  
### <a name="servicemodeltracelisteners"></a><span data-ttu-id="4913e-153">ServiceModelTraceListeners</span><span class="sxs-lookup"><span data-stu-id="4913e-153">ServiceModelTraceListeners</span></span>  
 <span data-ttu-id="4913e-154">Typ danych: Tablica zdarzeń TraceListener</span><span class="sxs-lookup"><span data-stu-id="4913e-154">Data type: TraceListener array</span></span>  
  
 <span data-ttu-id="4913e-155">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="4913e-155">Access type: Read-only</span></span>  
  
 <span data-ttu-id="4913e-156">Kolekcja obiektów nasłuchujących ze źródła śledzenia System.ServiceModel.</span><span class="sxs-lookup"><span data-stu-id="4913e-156">A collection of listeners from the System.ServiceModel trace source.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4913e-157">Wymagania</span><span class="sxs-lookup"><span data-stu-id="4913e-157">Requirements</span></span>  
  
|<span data-ttu-id="4913e-158">MOF</span><span class="sxs-lookup"><span data-stu-id="4913e-158">MOF</span></span>|<span data-ttu-id="4913e-159">Zadeklarowana w Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="4913e-159">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="4913e-160">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="4913e-160">Namespace</span></span>|<span data-ttu-id="4913e-161">Zdefiniowane w root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="4913e-161">Defined in root\ServiceModel</span></span>|
