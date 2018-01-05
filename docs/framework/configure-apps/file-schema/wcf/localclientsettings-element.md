---
title: '&lt;localClientSettings&gt;, element'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4680ace5-f4e1-4fcb-b9d8-a4a4af5cd7ae
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e906564eb86a2fcd7a82c194bac65416bbeab518
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ltlocalclientsettingsgt-element"></a><span data-ttu-id="c54bd-102">&lt;localClientSettings&gt;, element</span><span class="sxs-lookup"><span data-stu-id="c54bd-102">&lt;localClientSettings&gt; element</span></span>
<span data-ttu-id="c54bd-103">Określa ustawienia zabezpieczenia lokalnego klienta dla tego powiązania.</span><span class="sxs-lookup"><span data-stu-id="c54bd-103">Specifies the security settings of a local client for this binding.</span></span>  
  
 <span data-ttu-id="c54bd-104">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="c54bd-104">\<system.serviceModel></span></span>  
<span data-ttu-id="c54bd-105">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="c54bd-105">\<bindings></span></span>  
<span data-ttu-id="c54bd-106">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="c54bd-106">\<customBinding></span></span>  
<span data-ttu-id="c54bd-107">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="c54bd-107">\<binding></span></span>  
<span data-ttu-id="c54bd-108">\<Zabezpieczenia ></span><span class="sxs-lookup"><span data-stu-id="c54bd-108">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c54bd-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="c54bd-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c54bd-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="c54bd-110">Attributes and Elements</span></span>  
 <span data-ttu-id="c54bd-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="c54bd-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c54bd-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="c54bd-112">Attributes</span></span>  
  
|<span data-ttu-id="c54bd-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="c54bd-113">Attribute</span></span>|<span data-ttu-id="c54bd-114">Opis</span><span class="sxs-lookup"><span data-stu-id="c54bd-114">Description</span></span>|  
|---------------|-----------------|  
|`cacheCookies`|<span data-ttu-id="c54bd-115">Wartość logiczna określająca czy włączone jest buforowanie plików cookie.</span><span class="sxs-lookup"><span data-stu-id="c54bd-115">A Boolean value that specifies whether cookie caching is enabled.</span></span> <span data-ttu-id="c54bd-116">Wartość domyślna to `false`.</span><span class="sxs-lookup"><span data-stu-id="c54bd-116">The default is `false`.</span></span>|  
|`cookieRenewalThresholdPercentage`|<span data-ttu-id="c54bd-117">Liczba całkowita określająca maksymalny procent plików cookie, które mogą być odnawiane.</span><span class="sxs-lookup"><span data-stu-id="c54bd-117">An integer that specifies the maximum percentage of cookies that can be renewed.</span></span> <span data-ttu-id="c54bd-118">Wartość ta powinna być pomiędzy 0 a 100 włącznie.</span><span class="sxs-lookup"><span data-stu-id="c54bd-118">This value should be between 0 and 100 inclusively.</span></span> <span data-ttu-id="c54bd-119">Domyślna wartość to 90.</span><span class="sxs-lookup"><span data-stu-id="c54bd-119">The default is 90.</span></span>|  
|`detectReplays`|<span data-ttu-id="c54bd-120">Wartość logiczna określająca, czy ataki metodą kanału wykrytych i zajmuje się automatycznie.</span><span class="sxs-lookup"><span data-stu-id="c54bd-120">A Boolean value that specifies whether replay attacks against the channel are detected and dealt with automatically.</span></span> <span data-ttu-id="c54bd-121">Wartość domyślna to `false`.</span><span class="sxs-lookup"><span data-stu-id="c54bd-121">The default is `false`.</span></span>|  
|`maxClockSkew`|<span data-ttu-id="c54bd-122">A <xref:System.TimeSpan> określający maksymalną różnicę czasu między zegarami systemowymi dwóch uczestników komunikacji.</span><span class="sxs-lookup"><span data-stu-id="c54bd-122">A <xref:System.TimeSpan> that specifies the maximum time difference between the system clocks of the two communicating parties.</span></span> <span data-ttu-id="c54bd-123">Wartość domyślna to "00: 05:00".</span><span class="sxs-lookup"><span data-stu-id="c54bd-123">The default value is "00:05:00".</span></span><br /><br /> <span data-ttu-id="c54bd-124">Gdy ta wartość ma wartość domyślną, odbiorca akceptuje wiadomości wraz z sygnaturą czasową w czasie wysyłania się do 5 minut lub wcześniej niż czas wiadomość została odebrana.</span><span class="sxs-lookup"><span data-stu-id="c54bd-124">When this value is set to the default, the receiver accepts messages with send-time time stamps up to 5 minutes later or earlier than the time the message was received.</span></span> <span data-ttu-id="c54bd-125">Komunikaty, które nie przejdą testów czasie wysyłania są odrzucane.</span><span class="sxs-lookup"><span data-stu-id="c54bd-125">Messages that do not pass the send-time test are rejected.</span></span> <span data-ttu-id="c54bd-126">To ustawienie jest używane w połączeniu z `replayWindow` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="c54bd-126">This setting is used in conjunction with the `replayWindow` attribute.</span></span>|  
|`maxCookieCachingTime`|<span data-ttu-id="c54bd-127">A <xref:System.TimeSpan> , który określa maksymalny okres istnienia plików cookie.</span><span class="sxs-lookup"><span data-stu-id="c54bd-127">A <xref:System.TimeSpan> that specifies the maximum lifetime of cookies.</span></span> <span data-ttu-id="c54bd-128">Wartość domyślna to "10675199.02:48:05.4775807".</span><span class="sxs-lookup"><span data-stu-id="c54bd-128">The default value is "10675199.02:48:05.4775807".</span></span>|  
|`reconnectTransportOnFailure`|<span data-ttu-id="c54bd-129">Wartość logiczna określająca, czy próbować połączenia używające obsługi wiadomości WS-Reliable będą odnawiane po błędach transportu.</span><span class="sxs-lookup"><span data-stu-id="c54bd-129">A Boolean value that specifies whether connections using WS-Reliable messaging will attempt to reconnect after transport failures.</span></span> <span data-ttu-id="c54bd-130">Wartość domyślna to `true`, co oznacza, że są próby nieskończone podejmuje próbę ponownego połączenia.</span><span class="sxs-lookup"><span data-stu-id="c54bd-130">The default is `true`, which means that infinite attempts to reconnect are attempted.</span></span> <span data-ttu-id="c54bd-131">Cykl jest dzielony przez limit czasu bezczynności, co powoduje, że kanał do zgłoszenia wyjątku, gdy nie można go ponownie.</span><span class="sxs-lookup"><span data-stu-id="c54bd-131">The cycle is broken by the inactivity time-out, which causes the channel to throw an exception when it cannot be reconnected.</span></span>|  
|`replayCacheSize`|<span data-ttu-id="c54bd-132">Dodatnia liczba całkowita określająca liczbę buforowanych identyfikatorów jednorazowych używanych do wykrywania powtórzeń.</span><span class="sxs-lookup"><span data-stu-id="c54bd-132">A positive integer that specifies the number of cached nonces used for replay detection.</span></span> <span data-ttu-id="c54bd-133">Po przekroczeniu tego limitu najstarsza identyfikator jednorazowy jest usuwany i nowy identyfikator jednorazowy jest tworzona dla nowej wiadomości.</span><span class="sxs-lookup"><span data-stu-id="c54bd-133">If this limit is exceeded, the oldest nonce is removed and a new nonce is created for the new message.</span></span> <span data-ttu-id="c54bd-134">Wartość domyślna wynosi 500 000.</span><span class="sxs-lookup"><span data-stu-id="c54bd-134">The default value is 500000.</span></span>|  
|`replayWindow`|<span data-ttu-id="c54bd-135">A <xref:System.TimeSpan> , który określa czas, w którym identyfikatorów jednorazowych poszczególnych komunikatów są prawidłowe.</span><span class="sxs-lookup"><span data-stu-id="c54bd-135">A <xref:System.TimeSpan> that specifies the duration in which individual message nonces are valid.</span></span><br /><br /> <span data-ttu-id="c54bd-136">Po tym czasie komunikat wysłany z tego samego identyfikator jednorazowy jak wysyłane przed nie będą akceptowane.</span><span class="sxs-lookup"><span data-stu-id="c54bd-136">After this duration, a message sent with the same nonce as the one sent before will not be accepted.</span></span> <span data-ttu-id="c54bd-137">Ten atrybut jest używany w połączeniu z `maxClockSkew` atrybutu zapobieganie atakom polegającym na odtwarzaniu.</span><span class="sxs-lookup"><span data-stu-id="c54bd-137">This attribute is used in conjunction with the `maxClockSkew` attribute to prevent replay attacks.</span></span> <span data-ttu-id="c54bd-138">Osoba atakująca może powtarzania komunikatu, po wygaśnięciu okna powtarzania.</span><span class="sxs-lookup"><span data-stu-id="c54bd-138">An attacker could replay a message after its replay window has expired.</span></span> <span data-ttu-id="c54bd-139">Ten komunikat, jednak nie powiedzie się `maxClockSkew` testów, które odrzuca wiadomości z sygnaturami czasowymi czasie wysyłania maksymalnie przez określony czas, które są nowsze lub wcześniejszy niż czas wiadomość została odebrana.</span><span class="sxs-lookup"><span data-stu-id="c54bd-139">This message, however, would fail the `maxClockSkew` test which rejects messages with send-time timestamps up to a specified time later or earlier than the time the message was received.</span></span>|  
|`sessionKeyRenewalInterval`|<span data-ttu-id="c54bd-140">A <xref:System.TimeSpan> , który określa czas, po upływie którego inicjator odnowi klucz sesji zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="c54bd-140">A <xref:System.TimeSpan> that specifies the duration after which the initiator will renew the key for the security session.</span></span> <span data-ttu-id="c54bd-141">Wartość domyślna to "10: 00:00".</span><span class="sxs-lookup"><span data-stu-id="c54bd-141">The default is "10:00:00".</span></span>|  
|`sessionKeyRolloverInterval`|<span data-ttu-id="c54bd-142">A <xref:System.TimeSpan> , który określa przedział czasu poprzedniego klucza sesji jest prawidłowa w komunikatach przychodzących podczas odnawiania klucza.</span><span class="sxs-lookup"><span data-stu-id="c54bd-142">A <xref:System.TimeSpan> that specifies the time interval a previous session key is valid on incoming messages during a key renewal.</span></span> <span data-ttu-id="c54bd-143">Wartość domyślna to "00: 05:00".</span><span class="sxs-lookup"><span data-stu-id="c54bd-143">The default is "00:05:00".</span></span><br /><br /> <span data-ttu-id="c54bd-144">Podczas odnawiania klucza klient i serwer muszą zawsze wysyłanie wiadomości przy użyciu najnowszych dostępnych klucza.</span><span class="sxs-lookup"><span data-stu-id="c54bd-144">During key renewal, the client and server must always send messages using the most current available key.</span></span> <span data-ttu-id="c54bd-145">Obie strony będzie akceptować zabezpieczonego za pomocą poprzedni klucz sesji do przerzucania czas wygaśnięcia wiadomości przychodzących.</span><span class="sxs-lookup"><span data-stu-id="c54bd-145">Both parties will accept incoming messages secured with the previous session key until the rollover time expires.</span></span>|  
|`timestampValidityDuration`|<span data-ttu-id="c54bd-146">Dodatnią <xref:System.TimeSpan> określający okres ważności sygnatury czasowej.</span><span class="sxs-lookup"><span data-stu-id="c54bd-146">A positive <xref:System.TimeSpan> that specifies the duration in which a time stamp is valid.</span></span> <span data-ttu-id="c54bd-147">Wartość domyślna to "00: 15:00".</span><span class="sxs-lookup"><span data-stu-id="c54bd-147">The default is "00:15:00".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c54bd-148">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="c54bd-148">Child Elements</span></span>  
 <span data-ttu-id="c54bd-149">Brak</span><span class="sxs-lookup"><span data-stu-id="c54bd-149">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c54bd-150">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="c54bd-150">Parent Elements</span></span>  
  
|<span data-ttu-id="c54bd-151">Element</span><span class="sxs-lookup"><span data-stu-id="c54bd-151">Element</span></span>|<span data-ttu-id="c54bd-152">Opis</span><span class="sxs-lookup"><span data-stu-id="c54bd-152">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c54bd-153">\<Zabezpieczenia ></span><span class="sxs-lookup"><span data-stu-id="c54bd-153">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md)|<span data-ttu-id="c54bd-154">Określa opcje zabezpieczeń dla niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="c54bd-154">Specifies the security options for a custom binding.</span></span>|  
|[<span data-ttu-id="c54bd-155">\<secureConversationBootstrap ></span><span class="sxs-lookup"><span data-stu-id="c54bd-155">\<secureConversationBootstrap></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md)|<span data-ttu-id="c54bd-156">Określa wartości domyślne używane do inicjowania usługi bezpiecznej konwersacji.</span><span class="sxs-lookup"><span data-stu-id="c54bd-156">Specifies the default values used for initiating a secure conversation service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c54bd-157">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c54bd-157">Remarks</span></span>  
 <span data-ttu-id="c54bd-158">Ustawienia są lokalne w tym sensie, że nie są one ustawienia pochodzące z zasad zabezpieczeń usługi.</span><span class="sxs-lookup"><span data-stu-id="c54bd-158">The settings are local in the sense that they are not settings derived from the security policy of the service.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c54bd-159">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c54bd-159">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.LocalClientSecuritySettingsElement>  
 <xref:System.ServiceModel.Configuration.SecurityElementBase.LocalClientSettings%2A>  
 <xref:System.ServiceModel.Channels.SecurityBindingElement.LocalClientSettings%2A>  
 <xref:System.ServiceModel.Channels.LocalClientSecuritySettings>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [<span data-ttu-id="c54bd-160">Powiązania</span><span class="sxs-lookup"><span data-stu-id="c54bd-160">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="c54bd-161">Rozszerzanie powiązań</span><span class="sxs-lookup"><span data-stu-id="c54bd-161">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="c54bd-162">Powiązania niestandardowe</span><span class="sxs-lookup"><span data-stu-id="c54bd-162">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="c54bd-163">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="c54bd-163">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)  
 [<span data-ttu-id="c54bd-164">Instrukcje: tworzenie niestandardowego powiązania za pomocą elementu SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="c54bd-164">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)  
 [<span data-ttu-id="c54bd-165">Zabezpieczenia powiązania niestandardowego</span><span class="sxs-lookup"><span data-stu-id="c54bd-165">Custom Binding Security</span></span>](../../../../../docs/framework/wcf/samples/custom-binding-security.md)
