---
title: <localClientSettings>, element
ms.date: 03/30/2017
ms.assetid: 4680ace5-f4e1-4fcb-b9d8-a4a4af5cd7ae
ms.openlocfilehash: 3ec0394943c030a8866087c98a912682a2a2112e
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "70400319"
---
# <a name="localclientsettings-element"></a><span data-ttu-id="f96fd-102">\<localClientSettings>, element</span><span class="sxs-lookup"><span data-stu-id="f96fd-102">\<localClientSettings> element</span></span>
<span data-ttu-id="f96fd-103">Określa ustawienia zabezpieczeń lokalnego klienta dla tego powiązania.</span><span class="sxs-lookup"><span data-stu-id="f96fd-103">Specifies the security settings of a local client for this binding.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<localClientSettings>**  
  
## <a name="syntax"></a><span data-ttu-id="f96fd-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="f96fd-104">Syntax</span></span>  
  
```xml  
<security>
   <localClientSettings cacheCookies="Boolean"
                        cookieRenewalThresholdPercentage="Integer"
                        detectReplays="Boolean"
                        maxClockSkew="TimeSpan"
                        maxCookieCachingTime="TimeSpan"
                        reconnectTransportOnFailure="Boolean"
                        replayCacheSize="Integer"
                        replayWindow="TimeSpan"
                        sessionKeyRenewalInterval="TimeSpan"
                        sessionKeyRolloverInterval="TimeSpan"
                        timestampValidityDuration="TimeSpan" />
</security>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f96fd-105">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="f96fd-105">Attributes and Elements</span></span>  
 <span data-ttu-id="f96fd-106">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="f96fd-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f96fd-107">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="f96fd-107">Attributes</span></span>  
  
|<span data-ttu-id="f96fd-108">Atrybut</span><span class="sxs-lookup"><span data-stu-id="f96fd-108">Attribute</span></span>|<span data-ttu-id="f96fd-109">Opis</span><span class="sxs-lookup"><span data-stu-id="f96fd-109">Description</span></span>|  
|---------------|-----------------|  
|`cacheCookies`|<span data-ttu-id="f96fd-110">Wartość logiczna określająca, czy włączone jest buforowanie plików cookie.</span><span class="sxs-lookup"><span data-stu-id="f96fd-110">A Boolean value that specifies whether cookie caching is enabled.</span></span> <span data-ttu-id="f96fd-111">Wartość domyślna to `false`.</span><span class="sxs-lookup"><span data-stu-id="f96fd-111">The default is `false`.</span></span>|  
|`cookieRenewalThresholdPercentage`|<span data-ttu-id="f96fd-112">Liczba całkowita określająca maksymalny procent plików cookie, które mogą być odnawiane.</span><span class="sxs-lookup"><span data-stu-id="f96fd-112">An integer that specifies the maximum percentage of cookies that can be renewed.</span></span> <span data-ttu-id="f96fd-113">Ta wartość powinna należeć do zakresu od 0 do 100 włącznie.</span><span class="sxs-lookup"><span data-stu-id="f96fd-113">This value should be between 0 and 100 inclusively.</span></span> <span data-ttu-id="f96fd-114">Wartość domyślna to 90.</span><span class="sxs-lookup"><span data-stu-id="f96fd-114">The default is 90.</span></span>|  
|`detectReplays`|<span data-ttu-id="f96fd-115">Wartość logiczna określająca, czy ataki powtarzające się na kanał są wykrywane i rozwiązywane automatycznie.</span><span class="sxs-lookup"><span data-stu-id="f96fd-115">A Boolean value that specifies whether replay attacks against the channel are detected and dealt with automatically.</span></span> <span data-ttu-id="f96fd-116">Wartość domyślna to `false`.</span><span class="sxs-lookup"><span data-stu-id="f96fd-116">The default is `false`.</span></span>|  
|`maxClockSkew`|<span data-ttu-id="f96fd-117">A <xref:System.TimeSpan> , która określa maksymalną różnicę czasu między zegarami systemowymi dwóch osób komunikujących się.</span><span class="sxs-lookup"><span data-stu-id="f96fd-117">A <xref:System.TimeSpan> that specifies the maximum time difference between the system clocks of the two communicating parties.</span></span> <span data-ttu-id="f96fd-118">Wartość domyślna to "00:05:00".</span><span class="sxs-lookup"><span data-stu-id="f96fd-118">The default value is "00:05:00".</span></span><br /><br /> <span data-ttu-id="f96fd-119">Gdy ta wartość jest ustawiona domyślnie, odbiorca akceptuje komunikaty o sygnaturach czasowych czasu wysłania do 5 minut później lub wcześniej od momentu odebrania komunikatu.</span><span class="sxs-lookup"><span data-stu-id="f96fd-119">When this value is set to the default, the receiver accepts messages with send-time time stamps up to 5 minutes later or earlier than the time the message was received.</span></span> <span data-ttu-id="f96fd-120">Komunikaty, które nie przeszły testu czasu wysłania, są odrzucane.</span><span class="sxs-lookup"><span data-stu-id="f96fd-120">Messages that do not pass the send-time test are rejected.</span></span> <span data-ttu-id="f96fd-121">To ustawienie jest używane w połączeniu z `replayWindow` atrybutem.</span><span class="sxs-lookup"><span data-stu-id="f96fd-121">This setting is used in conjunction with the `replayWindow` attribute.</span></span>|  
|`maxCookieCachingTime`|<span data-ttu-id="f96fd-122">A <xref:System.TimeSpan> określa maksymalny okres istnienia plików cookie.</span><span class="sxs-lookup"><span data-stu-id="f96fd-122">A <xref:System.TimeSpan> that specifies the maximum lifetime of cookies.</span></span> <span data-ttu-id="f96fd-123">Wartość domyślna to "10675199.02:48:05.4775807".</span><span class="sxs-lookup"><span data-stu-id="f96fd-123">The default value is "10675199.02:48:05.4775807".</span></span>|  
|`reconnectTransportOnFailure`|<span data-ttu-id="f96fd-124">Wartość logiczna określająca, czy połączenia korzystające z protokołu WS-niezawodny będą podejmować próby ponownego nawiązania połączenia po awariach transportu.</span><span class="sxs-lookup"><span data-stu-id="f96fd-124">A Boolean value that specifies whether connections using WS-Reliable messaging will attempt to reconnect after transport failures.</span></span> <span data-ttu-id="f96fd-125">Wartość domyślna to `true` , co oznacza, że podjęto próbę nieograniczonej próby ponownego nawiązania połączenia.</span><span class="sxs-lookup"><span data-stu-id="f96fd-125">The default is `true`, which means that infinite attempts to reconnect are attempted.</span></span> <span data-ttu-id="f96fd-126">Cykl jest przerwany przez limit czasu braku aktywności, który powoduje, że kanał zgłasza wyjątek, gdy nie można ponownie nawiązać połączenia.</span><span class="sxs-lookup"><span data-stu-id="f96fd-126">The cycle is broken by the inactivity time-out, which causes the channel to throw an exception when it cannot be reconnected.</span></span>|  
|`replayCacheSize`|<span data-ttu-id="f96fd-127">Dodatnia liczba całkowita określająca liczbę buforowanych identyfikatorów jednorazowych używanych do wykrywania powtórzeń.</span><span class="sxs-lookup"><span data-stu-id="f96fd-127">A positive integer that specifies the number of cached nonces used for replay detection.</span></span> <span data-ttu-id="f96fd-128">W przypadku przekroczenia tego limitu najstarszy identyfikator jednorazowy zostanie usunięty i dla nowej wiadomości zostanie utworzony nowy identyfikator jednorazowy.</span><span class="sxs-lookup"><span data-stu-id="f96fd-128">If this limit is exceeded, the oldest nonce is removed and a new nonce is created for the new message.</span></span> <span data-ttu-id="f96fd-129">Wartość domyślna to 500000.</span><span class="sxs-lookup"><span data-stu-id="f96fd-129">The default value is 500000.</span></span>|  
|`replayWindow`|<span data-ttu-id="f96fd-130">A <xref:System.TimeSpan> , który określa czas, w którym poszczególne wiadomości identyfikatorów jednorazowych są prawidłowe.</span><span class="sxs-lookup"><span data-stu-id="f96fd-130">A <xref:System.TimeSpan> that specifies the duration in which individual message nonces are valid.</span></span><br /><br /> <span data-ttu-id="f96fd-131">Po tym czasie zostanie wysłany komunikat z tym samym identyfikatorem jednorazowym, który został wysłany wcześniej, nie zostanie zaakceptowany.</span><span class="sxs-lookup"><span data-stu-id="f96fd-131">After this duration, a message sent with the same nonce as the one sent before will not be accepted.</span></span> <span data-ttu-id="f96fd-132">Ten atrybut jest używany w połączeniu z `maxClockSkew` atrybutem w celu zapobiegania atakom metodą powtórzeń.</span><span class="sxs-lookup"><span data-stu-id="f96fd-132">This attribute is used in conjunction with the `maxClockSkew` attribute to prevent replay attacks.</span></span> <span data-ttu-id="f96fd-133">Osoba atakująca może odtworzyć komunikat po wygaśnięciu okna powtarzania.</span><span class="sxs-lookup"><span data-stu-id="f96fd-133">An attacker could replay a message after its replay window has expired.</span></span> <span data-ttu-id="f96fd-134">Jednak ten komunikat `maxClockSkew` przetestuje niepowodzenie testu, który odrzuca komunikaty z sygnaturami czasowymi czasu wysłania do określonego czasu później lub wcześniej od momentu odebrania komunikatu.</span><span class="sxs-lookup"><span data-stu-id="f96fd-134">This message, however, would fail the `maxClockSkew` test which rejects messages with send-time timestamps up to a specified time later or earlier than the time the message was received.</span></span>|  
|`sessionKeyRenewalInterval`|<span data-ttu-id="f96fd-135">A <xref:System.TimeSpan> , który określa czas, po którym inicjator odnowi klucz dla sesji zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="f96fd-135">A <xref:System.TimeSpan> that specifies the duration after which the initiator will renew the key for the security session.</span></span> <span data-ttu-id="f96fd-136">Wartość domyślna to "10:00:00".</span><span class="sxs-lookup"><span data-stu-id="f96fd-136">The default is "10:00:00".</span></span>|  
|`sessionKeyRolloverInterval`|<span data-ttu-id="f96fd-137">A <xref:System.TimeSpan> określa przedział czasu, w którym poprzedni klucz sesji jest ważny w przypadku komunikatów przychodzących podczas odnawiania klucza.</span><span class="sxs-lookup"><span data-stu-id="f96fd-137">A <xref:System.TimeSpan> that specifies the time interval a previous session key is valid on incoming messages during a key renewal.</span></span> <span data-ttu-id="f96fd-138">Wartość domyślna to "00:05:00".</span><span class="sxs-lookup"><span data-stu-id="f96fd-138">The default is "00:05:00".</span></span><br /><br /> <span data-ttu-id="f96fd-139">Podczas odnawiania klucza klient i serwer muszą zawsze wysyłać komunikaty przy użyciu najbardziej aktualnego dostępnego klucza.</span><span class="sxs-lookup"><span data-stu-id="f96fd-139">During key renewal, the client and server must always send messages using the most current available key.</span></span> <span data-ttu-id="f96fd-140">Obie strony będą akceptować wiadomości przychodzące zabezpieczone przy użyciu poprzedniego klucza sesji do momentu wygaśnięcia czasu przerzucania.</span><span class="sxs-lookup"><span data-stu-id="f96fd-140">Both parties will accept incoming messages secured with the previous session key until the rollover time expires.</span></span>|  
|`timestampValidityDuration`|<span data-ttu-id="f96fd-141">Wartość dodatnia określająca <xref:System.TimeSpan> czas ważności sygnatury czasowej.</span><span class="sxs-lookup"><span data-stu-id="f96fd-141">A positive <xref:System.TimeSpan> that specifies the duration in which a time stamp is valid.</span></span> <span data-ttu-id="f96fd-142">Wartość domyślna to "00:15:00".</span><span class="sxs-lookup"><span data-stu-id="f96fd-142">The default is "00:15:00".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f96fd-143">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="f96fd-143">Child Elements</span></span>  
 <span data-ttu-id="f96fd-144">Brak</span><span class="sxs-lookup"><span data-stu-id="f96fd-144">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f96fd-145">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="f96fd-145">Parent Elements</span></span>  
  
|<span data-ttu-id="f96fd-146">Element</span><span class="sxs-lookup"><span data-stu-id="f96fd-146">Element</span></span>|<span data-ttu-id="f96fd-147">Opis</span><span class="sxs-lookup"><span data-stu-id="f96fd-147">Description</span></span>|  
|-------------|-----------------|  
|[\<security>](security-of-custombinding.md)|<span data-ttu-id="f96fd-148">Określa opcje zabezpieczeń dla niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="f96fd-148">Specifies the security options for a custom binding.</span></span>|  
|[\<secureConversationBootstrap>](secureconversationbootstrap.md)|<span data-ttu-id="f96fd-149">Określa wartości domyślne używane do inicjowania usługi bezpiecznej konwersacji.</span><span class="sxs-lookup"><span data-stu-id="f96fd-149">Specifies the default values used for initiating a secure conversation service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f96fd-150">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f96fd-150">Remarks</span></span>  
 <span data-ttu-id="f96fd-151">Ustawienia są lokalne w sensie, że nie są ustawieniami pochodzącymi z zasad zabezpieczeń usługi.</span><span class="sxs-lookup"><span data-stu-id="f96fd-151">The settings are local in the sense that they are not settings derived from the security policy of the service.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f96fd-152">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f96fd-152">See also</span></span>

- <xref:System.ServiceModel.Configuration.LocalClientSecuritySettingsElement>
- <xref:System.ServiceModel.Configuration.SecurityElementBase.LocalClientSettings%2A>
- <xref:System.ServiceModel.Channels.SecurityBindingElement.LocalClientSettings%2A>
- <xref:System.ServiceModel.Channels.LocalClientSecuritySettings>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="f96fd-153">Powiązania</span><span class="sxs-lookup"><span data-stu-id="f96fd-153">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="f96fd-154">Rozszerzanie powiązań</span><span class="sxs-lookup"><span data-stu-id="f96fd-154">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="f96fd-155">Powiązania niestandardowe</span><span class="sxs-lookup"><span data-stu-id="f96fd-155">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
- [<span data-ttu-id="f96fd-156">Instrukcje: tworzenie niestandardowego powiązania za pomocą elementu SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="f96fd-156">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
- [<span data-ttu-id="f96fd-157">Zabezpieczenia wiązania niestandardowego</span><span class="sxs-lookup"><span data-stu-id="f96fd-157">Custom Binding Security</span></span>](../../../wcf/samples/custom-binding-security.md)
