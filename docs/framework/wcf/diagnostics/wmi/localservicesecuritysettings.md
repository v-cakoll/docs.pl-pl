---
title: LocalServiceSecuritySettings
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 490aa0e5-5242-4f8d-b505-5ec6287633b4
caps.latest.revision: "8"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: 74eff3a6193e6507c1049accf4c43c3ecc8d30a6
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="localservicesecuritysettings"></a><span data-ttu-id="80570-102">LocalServiceSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="80570-102">LocalServiceSecuritySettings</span></span>
<span data-ttu-id="80570-103">LocalServiceSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="80570-103">LocalServiceSecuritySettings</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="80570-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="80570-104">Syntax</span></span>  
  
```  
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
  
## <a name="methods"></a><span data-ttu-id="80570-105">Metody</span><span class="sxs-lookup"><span data-stu-id="80570-105">Methods</span></span>  
 <span data-ttu-id="80570-106">Klasa LocalServiceSecuritySettings nie definiuje żadnych metod.</span><span class="sxs-lookup"><span data-stu-id="80570-106">The LocalServiceSecuritySettings class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="80570-107">Właściwości</span><span class="sxs-lookup"><span data-stu-id="80570-107">Properties</span></span>  
 <span data-ttu-id="80570-108">Klasa LocalServiceSecuritySettings ma następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="80570-108">The LocalServiceSecuritySettings class has the following properties:</span></span>  
  
### <a name="detectreplays"></a><span data-ttu-id="80570-109">DetectReplays</span><span class="sxs-lookup"><span data-stu-id="80570-109">DetectReplays</span></span>  
 <span data-ttu-id="80570-110">Typ danych: wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="80570-110">Data type: boolean</span></span>  
  
 <span data-ttu-id="80570-111">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="80570-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="80570-112">Wartość logiczna określająca, czy ataki metodą kanału wykrytych i zajmuje się automatycznie.</span><span class="sxs-lookup"><span data-stu-id="80570-112">A Boolean value that specifies whether replay attacks against the channel are detected and dealt with automatically.</span></span>  
  
### <a name="inactivitytimeout"></a><span data-ttu-id="80570-113">Limit czasu nieaktywności</span><span class="sxs-lookup"><span data-stu-id="80570-113">InactivityTimeout</span></span>  
 <span data-ttu-id="80570-114">Typ danych: daty i godziny</span><span class="sxs-lookup"><span data-stu-id="80570-114">Data type: datetime</span></span>  
  
 <span data-ttu-id="80570-115">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="80570-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="80570-116">Maksymalna liczba oczekujących sesji bezpieczeństwa obsługiwanych przez usługę.</span><span class="sxs-lookup"><span data-stu-id="80570-116">The maximum number of pending security sessions that the service supports.</span></span>  
  
### <a name="issuedcookielifetime"></a><span data-ttu-id="80570-117">IssuedCookieLifetime</span><span class="sxs-lookup"><span data-stu-id="80570-117">IssuedCookieLifetime</span></span>  
 <span data-ttu-id="80570-118">Typ danych: daty i godziny</span><span class="sxs-lookup"><span data-stu-id="80570-118">Data type: datetime</span></span>  
  
 <span data-ttu-id="80570-119">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="80570-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="80570-120">Obiekt TimeSpan określający okres istnienia wystawionego dla wszystkich nowych plików cookie zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="80570-120">A TimeSpan that specifies the lifetime issued to all new security cookies.</span></span>  
  
### <a name="maxcachedcookies"></a><span data-ttu-id="80570-121">MaxCachedCookies</span><span class="sxs-lookup"><span data-stu-id="80570-121">MaxCachedCookies</span></span>  
 <span data-ttu-id="80570-122">Typ danych: sint32</span><span class="sxs-lookup"><span data-stu-id="80570-122">Data type: sint32</span></span>  
  
 <span data-ttu-id="80570-123">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="80570-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="80570-124">Maksymalna liczba plików cookie, które mogą być buforowane.</span><span class="sxs-lookup"><span data-stu-id="80570-124">The maximum number of cookies that can be cached.</span></span>  
  
### <a name="maxclockskew"></a><span data-ttu-id="80570-125">MaxClockSkew</span><span class="sxs-lookup"><span data-stu-id="80570-125">MaxClockSkew</span></span>  
 <span data-ttu-id="80570-126">Typ danych: daty i godziny</span><span class="sxs-lookup"><span data-stu-id="80570-126">Data type: datetime</span></span>  
  
 <span data-ttu-id="80570-127">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="80570-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="80570-128">Obiekt TimeSpan określający maksymalną różnicę czasu między zegarami systemowymi dwóch uczestników komunikacji.</span><span class="sxs-lookup"><span data-stu-id="80570-128">A TimeSpan that specifies the maximum time difference between the system clocks of the two communicating parties.</span></span>  
  
### <a name="maxpendingsessions"></a><span data-ttu-id="80570-129">MaxPendingSessions</span><span class="sxs-lookup"><span data-stu-id="80570-129">MaxPendingSessions</span></span>  
 <span data-ttu-id="80570-130">Typ danych: sint32</span><span class="sxs-lookup"><span data-stu-id="80570-130">Data type: sint32</span></span>  
  
 <span data-ttu-id="80570-131">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="80570-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="80570-132">Maksymalna liczba oczekujących połączeń przypadających na usługę.</span><span class="sxs-lookup"><span data-stu-id="80570-132">The maximum number of pending connections on the service.</span></span>  
  
### <a name="maxstatefulnegotiations"></a><span data-ttu-id="80570-133">MaxStatefulNegotiations</span><span class="sxs-lookup"><span data-stu-id="80570-133">MaxStatefulNegotiations</span></span>  
 <span data-ttu-id="80570-134">Typ danych: sint32</span><span class="sxs-lookup"><span data-stu-id="80570-134">Data type: sint32</span></span>  
  
 <span data-ttu-id="80570-135">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="80570-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="80570-136">Liczba negocjacji zabezpieczeń, które mogą być jednocześnie aktywne.</span><span class="sxs-lookup"><span data-stu-id="80570-136">The number of security negotiations that can be active concurrently.</span></span>  
  
### <a name="negotiationtimeout"></a><span data-ttu-id="80570-137">NegotiationTimeout</span><span class="sxs-lookup"><span data-stu-id="80570-137">NegotiationTimeout</span></span>  
 <span data-ttu-id="80570-138">Typ danych: daty i godziny</span><span class="sxs-lookup"><span data-stu-id="80570-138">Data type: datetime</span></span>  
  
 <span data-ttu-id="80570-139">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="80570-139">Access type: Read-only</span></span>  
  
 <span data-ttu-id="80570-140">Obiekt TimeSpan określający maksymalny czas trwania fazy negocjacji zabezpieczeń między serwerem a klientem.</span><span class="sxs-lookup"><span data-stu-id="80570-140">A TimeSpan that specifies the maximum duration for the security negotiation phase between server and client.</span></span>  
  
### <a name="reconnecttransportonfailure"></a><span data-ttu-id="80570-141">ReconnectTransportOnFailure</span><span class="sxs-lookup"><span data-stu-id="80570-141">ReconnectTransportOnFailure</span></span>  
 <span data-ttu-id="80570-142">Typ danych: wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="80570-142">Data type: boolean</span></span>  
  
 <span data-ttu-id="80570-143">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="80570-143">Access type: Read-only</span></span>  
  
 <span data-ttu-id="80570-144">Wartość logiczna określająca, czy połączenia używające obsługi wiadomości WS-Reliable podjąć próbę ponownego połączenia po błędach transportu.</span><span class="sxs-lookup"><span data-stu-id="80570-144">A Boolean value that specifies whether connections using WS-Reliable messaging attempt to reconnect after transport failures.</span></span>  
  
### <a name="replaycachesize"></a><span data-ttu-id="80570-145">ReplayCacheSize</span><span class="sxs-lookup"><span data-stu-id="80570-145">ReplayCacheSize</span></span>  
 <span data-ttu-id="80570-146">Typ danych: sint32</span><span class="sxs-lookup"><span data-stu-id="80570-146">Data type: sint32</span></span>  
  
 <span data-ttu-id="80570-147">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="80570-147">Access type: Read-only</span></span>  
  
 <span data-ttu-id="80570-148">Liczba buforowanych identyfikatorów jednorazowych używanych do wykrywania powtórzeń.</span><span class="sxs-lookup"><span data-stu-id="80570-148">The number of cached nonces used for replay detection.</span></span>  
  
### <a name="replaywindow"></a><span data-ttu-id="80570-149">Elementy ReplayWindow</span><span class="sxs-lookup"><span data-stu-id="80570-149">ReplayWindow</span></span>  
 <span data-ttu-id="80570-150">Typ danych: daty i godziny</span><span class="sxs-lookup"><span data-stu-id="80570-150">Data type: datetime</span></span>  
  
 <span data-ttu-id="80570-151">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="80570-151">Access type: Read-only</span></span>  
  
 <span data-ttu-id="80570-152">Obiekt TimeSpan określający okres czasu, w którym identyfikatorów jednorazowych poszczególnych komunikatów są prawidłowe.</span><span class="sxs-lookup"><span data-stu-id="80570-152">A TimeSpan that specifies the duration in which individual message nonces are valid.</span></span>  
  
### <a name="sessionkeyrenewalinterval"></a><span data-ttu-id="80570-153">SessionKeyRenewalInterval</span><span class="sxs-lookup"><span data-stu-id="80570-153">SessionKeyRenewalInterval</span></span>  
 <span data-ttu-id="80570-154">Typ danych: daty i godziny</span><span class="sxs-lookup"><span data-stu-id="80570-154">Data type: datetime</span></span>  
  
 <span data-ttu-id="80570-155">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="80570-155">Access type: Read-only</span></span>  
  
 <span data-ttu-id="80570-156">Obiekt TimeSpan określający okres czasu, po upływie którego inicjator odnawia klucz sesji zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="80570-156">A TimeSpan that specifies the duration after which the initiator renews the key for the security session.</span></span>  
  
### <a name="sessionkeyrolloverinterval"></a><span data-ttu-id="80570-157">SessionKeyRolloverInterval</span><span class="sxs-lookup"><span data-stu-id="80570-157">SessionKeyRolloverInterval</span></span>  
 <span data-ttu-id="80570-158">Typ danych: daty i godziny</span><span class="sxs-lookup"><span data-stu-id="80570-158">Data type: datetime</span></span>  
  
 <span data-ttu-id="80570-159">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="80570-159">Access type: Read-only</span></span>  
  
 <span data-ttu-id="80570-160">Obiekt TimeSpan określający okres poprzedniego klucza sesji jest prawidłowa w komunikatach przychodzących podczas odnawiania klucza.</span><span class="sxs-lookup"><span data-stu-id="80570-160">A TimeSpan that specifies the time interval a previous session key is valid on incoming messages during a key renewal.</span></span>  
  
### <a name="timestampvalidityduration"></a><span data-ttu-id="80570-161">TimestampValidityDuration</span><span class="sxs-lookup"><span data-stu-id="80570-161">TimestampValidityDuration</span></span>  
 <span data-ttu-id="80570-162">Typ danych: daty i godziny</span><span class="sxs-lookup"><span data-stu-id="80570-162">Data type: datetime</span></span>  
  
 <span data-ttu-id="80570-163">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="80570-163">Access type: Read-only</span></span>  
  
 <span data-ttu-id="80570-164">Obiekt TimeSpan określający okres ważności sygnatury czasowej.</span><span class="sxs-lookup"><span data-stu-id="80570-164">A TimeSpan that specifies the duration in which a time stamp is valid.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="80570-165">Wymagania</span><span class="sxs-lookup"><span data-stu-id="80570-165">Requirements</span></span>  
  
|<span data-ttu-id="80570-166">MOF</span><span class="sxs-lookup"><span data-stu-id="80570-166">MOF</span></span>|<span data-ttu-id="80570-167">Zadeklarowany w Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="80570-167">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="80570-168">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="80570-168">Namespace</span></span>|<span data-ttu-id="80570-169">Zdefiniowany w root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="80570-169">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="80570-170">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="80570-170">See Also</span></span>  
 <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings>
