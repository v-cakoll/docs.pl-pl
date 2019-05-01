---
title: LocalServiceSecuritySettings
ms.date: 03/30/2017
ms.assetid: 490aa0e5-5242-4f8d-b505-5ec6287633b4
ms.openlocfilehash: 15304630eb8a14e01d4815ddddc84cd32796fdcf
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61963452"
---
# <a name="localservicesecuritysettings"></a><span data-ttu-id="dcaec-102">LocalServiceSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="dcaec-102">LocalServiceSecuritySettings</span></span>
<span data-ttu-id="dcaec-103">LocalServiceSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="dcaec-103">LocalServiceSecuritySettings</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dcaec-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="dcaec-104">Syntax</span></span>  
  
```csharp
class LocalServiceSecuritySettings  
{  
  boolean DetectReplays;  
  datetime InactivityTimeout;  
  datetime IssuedCookieLifetime;  
  sint32 MaxCachedCookies;  
  datetime MaxClockSkew;  
  sint32 MaxPendingSessions;  
  sint32 MaxStatefulNegotiations;  
  datetime NegotiationTimeout;  
  boolean ReconnectTransportOnFailure;  
  sint32 ReplayCacheSize;  
  datetime ReplayWindow;  
  datetime SessionKeyRenewalInterval;  
  datetime SessionKeyRolloverInterval;  
  datetime TimestampValidityDuration;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="dcaec-105">Metody</span><span class="sxs-lookup"><span data-stu-id="dcaec-105">Methods</span></span>  
 <span data-ttu-id="dcaec-106">Klasa LocalServiceSecuritySettings nie definiuje żadnych metod.</span><span class="sxs-lookup"><span data-stu-id="dcaec-106">The LocalServiceSecuritySettings class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="dcaec-107">Właściwości</span><span class="sxs-lookup"><span data-stu-id="dcaec-107">Properties</span></span>  
 <span data-ttu-id="dcaec-108">Klasa LocalServiceSecuritySettings ma następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="dcaec-108">The LocalServiceSecuritySettings class has the following properties:</span></span>  
  
### <a name="detectreplays"></a><span data-ttu-id="dcaec-109">DetectReplays</span><span class="sxs-lookup"><span data-stu-id="dcaec-109">DetectReplays</span></span>  
 <span data-ttu-id="dcaec-110">Typ danych: wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="dcaec-110">Data type: boolean</span></span>  
  
 <span data-ttu-id="dcaec-111">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="dcaec-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="dcaec-112">Wartość logiczna, która określa, czy ataki metodą kanał są wykrywane i automatycznie uwzględnione.</span><span class="sxs-lookup"><span data-stu-id="dcaec-112">A Boolean value that specifies whether replay attacks against the channel are detected and dealt with automatically.</span></span>  
  
### <a name="inactivitytimeout"></a><span data-ttu-id="dcaec-113">Limit czasu nieaktywności</span><span class="sxs-lookup"><span data-stu-id="dcaec-113">InactivityTimeout</span></span>  
 <span data-ttu-id="dcaec-114">Typ danych: Data i godzina</span><span class="sxs-lookup"><span data-stu-id="dcaec-114">Data type: datetime</span></span>  
  
 <span data-ttu-id="dcaec-115">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="dcaec-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="dcaec-116">Maksymalna liczba oczekujących sesji bezpieczeństwa, obsługiwanych przez usługę.</span><span class="sxs-lookup"><span data-stu-id="dcaec-116">The maximum number of pending security sessions that the service supports.</span></span>  
  
### <a name="issuedcookielifetime"></a><span data-ttu-id="dcaec-117">IssuedCookieLifetime</span><span class="sxs-lookup"><span data-stu-id="dcaec-117">IssuedCookieLifetime</span></span>  
 <span data-ttu-id="dcaec-118">Typ danych: Data i godzina</span><span class="sxs-lookup"><span data-stu-id="dcaec-118">Data type: datetime</span></span>  
  
 <span data-ttu-id="dcaec-119">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="dcaec-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="dcaec-120">Element TimeSpan określający czas istnienia nadawany wszystkie nowe pliki cookie zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="dcaec-120">A TimeSpan that specifies the lifetime issued to all new security cookies.</span></span>  
  
### <a name="maxcachedcookies"></a><span data-ttu-id="dcaec-121">MaxCachedCookies</span><span class="sxs-lookup"><span data-stu-id="dcaec-121">MaxCachedCookies</span></span>  
 <span data-ttu-id="dcaec-122">Typ danych: sint32</span><span class="sxs-lookup"><span data-stu-id="dcaec-122">Data type: sint32</span></span>  
  
 <span data-ttu-id="dcaec-123">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="dcaec-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="dcaec-124">Maksymalna liczba plików cookie, które mogą być buforowane.</span><span class="sxs-lookup"><span data-stu-id="dcaec-124">The maximum number of cookies that can be cached.</span></span>  
  
### <a name="maxclockskew"></a><span data-ttu-id="dcaec-125">MaxClockSkew</span><span class="sxs-lookup"><span data-stu-id="dcaec-125">MaxClockSkew</span></span>  
 <span data-ttu-id="dcaec-126">Typ danych: Data i godzina</span><span class="sxs-lookup"><span data-stu-id="dcaec-126">Data type: datetime</span></span>  
  
 <span data-ttu-id="dcaec-127">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="dcaec-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="dcaec-128">Element TimeSpan określający maksymalną różnicę czasu między zegarami systemowymi dwóch uczestników komunikacji.</span><span class="sxs-lookup"><span data-stu-id="dcaec-128">A TimeSpan that specifies the maximum time difference between the system clocks of the two communicating parties.</span></span>  
  
### <a name="maxpendingsessions"></a><span data-ttu-id="dcaec-129">MaxPendingSessions</span><span class="sxs-lookup"><span data-stu-id="dcaec-129">MaxPendingSessions</span></span>  
 <span data-ttu-id="dcaec-130">Typ danych: sint32</span><span class="sxs-lookup"><span data-stu-id="dcaec-130">Data type: sint32</span></span>  
  
 <span data-ttu-id="dcaec-131">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="dcaec-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="dcaec-132">Maksymalna liczba oczekujących połączeń z usługą.</span><span class="sxs-lookup"><span data-stu-id="dcaec-132">The maximum number of pending connections on the service.</span></span>  
  
### <a name="maxstatefulnegotiations"></a><span data-ttu-id="dcaec-133">MaxStatefulNegotiations</span><span class="sxs-lookup"><span data-stu-id="dcaec-133">MaxStatefulNegotiations</span></span>  
 <span data-ttu-id="dcaec-134">Typ danych: sint32</span><span class="sxs-lookup"><span data-stu-id="dcaec-134">Data type: sint32</span></span>  
  
 <span data-ttu-id="dcaec-135">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="dcaec-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="dcaec-136">Liczba negocjacji zabezpieczeń, które mogą być wykonywane jednocześnie.</span><span class="sxs-lookup"><span data-stu-id="dcaec-136">The number of security negotiations that can be active concurrently.</span></span>  
  
### <a name="negotiationtimeout"></a><span data-ttu-id="dcaec-137">NegotiationTimeout</span><span class="sxs-lookup"><span data-stu-id="dcaec-137">NegotiationTimeout</span></span>  
 <span data-ttu-id="dcaec-138">Typ danych: Data i godzina</span><span class="sxs-lookup"><span data-stu-id="dcaec-138">Data type: datetime</span></span>  
  
 <span data-ttu-id="dcaec-139">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="dcaec-139">Access type: Read-only</span></span>  
  
 <span data-ttu-id="dcaec-140">Element TimeSpan określa maksymalny czas do przeprowadzenia w fazie negocjowanie zabezpieczeń między serwerem a klientem.</span><span class="sxs-lookup"><span data-stu-id="dcaec-140">A TimeSpan that specifies the maximum duration for the security negotiation phase between server and client.</span></span>  
  
### <a name="reconnecttransportonfailure"></a><span data-ttu-id="dcaec-141">ReconnectTransportOnFailure</span><span class="sxs-lookup"><span data-stu-id="dcaec-141">ReconnectTransportOnFailure</span></span>  
 <span data-ttu-id="dcaec-142">Typ danych: wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="dcaec-142">Data type: boolean</span></span>  
  
 <span data-ttu-id="dcaec-143">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="dcaec-143">Access type: Read-only</span></span>  
  
 <span data-ttu-id="dcaec-144">Wartość logiczna określająca, czy połączenia za pomocą usługi WS-Reliable messaging próbę ponownego połączenia po błędach transportu.</span><span class="sxs-lookup"><span data-stu-id="dcaec-144">A Boolean value that specifies whether connections using WS-Reliable messaging attempt to reconnect after transport failures.</span></span>  
  
### <a name="replaycachesize"></a><span data-ttu-id="dcaec-145">ReplayCacheSize</span><span class="sxs-lookup"><span data-stu-id="dcaec-145">ReplayCacheSize</span></span>  
 <span data-ttu-id="dcaec-146">Typ danych: sint32</span><span class="sxs-lookup"><span data-stu-id="dcaec-146">Data type: sint32</span></span>  
  
 <span data-ttu-id="dcaec-147">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="dcaec-147">Access type: Read-only</span></span>  
  
 <span data-ttu-id="dcaec-148">Liczba buforowanych identyfikatorów jednorazowych używanych do wykrywania powtórzeń.</span><span class="sxs-lookup"><span data-stu-id="dcaec-148">The number of cached nonces used for replay detection.</span></span>  
  
### <a name="replaywindow"></a><span data-ttu-id="dcaec-149">Elementy ReplayWindow</span><span class="sxs-lookup"><span data-stu-id="dcaec-149">ReplayWindow</span></span>  
 <span data-ttu-id="dcaec-150">Typ danych: Data i godzina</span><span class="sxs-lookup"><span data-stu-id="dcaec-150">Data type: datetime</span></span>  
  
 <span data-ttu-id="dcaec-151">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="dcaec-151">Access type: Read-only</span></span>  
  
 <span data-ttu-id="dcaec-152">Przedział czasu, który określa czas, w której poszczególne komunikatów są poprawni.</span><span class="sxs-lookup"><span data-stu-id="dcaec-152">A TimeSpan that specifies the duration in which individual message nonces are valid.</span></span>  
  
### <a name="sessionkeyrenewalinterval"></a><span data-ttu-id="dcaec-153">SessionKeyRenewalInterval</span><span class="sxs-lookup"><span data-stu-id="dcaec-153">SessionKeyRenewalInterval</span></span>  
 <span data-ttu-id="dcaec-154">Typ danych: Data i godzina</span><span class="sxs-lookup"><span data-stu-id="dcaec-154">Data type: datetime</span></span>  
  
 <span data-ttu-id="dcaec-155">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="dcaec-155">Access type: Read-only</span></span>  
  
 <span data-ttu-id="dcaec-156">Przedział czasu, który określa czas, po upływie którego inicjator odnawia klucz sesji zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="dcaec-156">A TimeSpan that specifies the duration after which the initiator renews the key for the security session.</span></span>  
  
### <a name="sessionkeyrolloverinterval"></a><span data-ttu-id="dcaec-157">SessionKeyRolloverInterval</span><span class="sxs-lookup"><span data-stu-id="dcaec-157">SessionKeyRolloverInterval</span></span>  
 <span data-ttu-id="dcaec-158">Typ danych: Data i godzina</span><span class="sxs-lookup"><span data-stu-id="dcaec-158">Data type: datetime</span></span>  
  
 <span data-ttu-id="dcaec-159">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="dcaec-159">Access type: Read-only</span></span>  
  
 <span data-ttu-id="dcaec-160">Przedział czasu, który określa przedział czasu poprzedniego klucza sesji jest prawidłowa w wiadomościach przychodzących podczas odnawiania klucza.</span><span class="sxs-lookup"><span data-stu-id="dcaec-160">A TimeSpan that specifies the time interval a previous session key is valid on incoming messages during a key renewal.</span></span>  
  
### <a name="timestampvalidityduration"></a><span data-ttu-id="dcaec-161">TimestampValidityDuration</span><span class="sxs-lookup"><span data-stu-id="dcaec-161">TimestampValidityDuration</span></span>  
 <span data-ttu-id="dcaec-162">Typ danych: Data i godzina</span><span class="sxs-lookup"><span data-stu-id="dcaec-162">Data type: datetime</span></span>  
  
 <span data-ttu-id="dcaec-163">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="dcaec-163">Access type: Read-only</span></span>  
  
 <span data-ttu-id="dcaec-164">Przedział czasu, który określa czas, w którym sygnatura czasowa jest poprawna.</span><span class="sxs-lookup"><span data-stu-id="dcaec-164">A TimeSpan that specifies the duration in which a time stamp is valid.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dcaec-165">Wymagania</span><span class="sxs-lookup"><span data-stu-id="dcaec-165">Requirements</span></span>  
  
|<span data-ttu-id="dcaec-166">MOF</span><span class="sxs-lookup"><span data-stu-id="dcaec-166">MOF</span></span>|<span data-ttu-id="dcaec-167">Zadeklarowana w Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="dcaec-167">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="dcaec-168">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="dcaec-168">Namespace</span></span>|<span data-ttu-id="dcaec-169">Zdefiniowane w root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="dcaec-169">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="dcaec-170">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="dcaec-170">See also</span></span>

- <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings>
