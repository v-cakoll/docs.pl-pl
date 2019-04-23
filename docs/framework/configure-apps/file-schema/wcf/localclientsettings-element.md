---
title: <localClientSettings>, element
ms.date: 03/30/2017
ms.assetid: 4680ace5-f4e1-4fcb-b9d8-a4a4af5cd7ae
ms.openlocfilehash: c5caf183e37edda6efc79ec81f1628180379fd46
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59163101"
---
# <a name="localclientsettings-element"></a>\<localClientSettings> element
Określa ustawienia zabezpieczenia lokalnego klienta dla tego powiązania.  
  
 \<system.serviceModel>  
\<powiązania >  
\<customBinding>  
\<Powiązanie >  
\<security>  
  
## <a name="syntax"></a>Składnia  
  
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
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`cacheCookies`|Wartość logiczna określająca, czy włączone jest buforowanie plików cookie. Wartość domyślna to `false`.|  
|`cookieRenewalThresholdPercentage`|Liczba całkowita określająca maksymalny procent plików cookie, które mogą być odnawiane. Wartość ta powinna być się w zakresie od 0 do 100 włącznie. Domyślna wartość to 90.|  
|`detectReplays`|Wartość logiczna, która określa, czy ataki metodą kanał są wykrywane i automatycznie uwzględnione. Wartość domyślna to `false`.|  
|`maxClockSkew`|A <xref:System.TimeSpan> określający maksymalną różnicę czasu między zegarami systemowymi dwóch uczestników komunikacji. Wartość domyślna to "00: 05:00".<br /><br /> W przypadku tę wartość ustawiono domyślną, odbiornik akceptuje komunikaty, w których sygnatury czasowe w czasie wysyłania się do 5 minut później, lub wcześniej niż czas wiadomość została odebrana. Wiadomości, które nie są przekazywane do testu czas wysłania są odrzucane. To ustawienie jest używane w połączeniu z `replayWindow` atrybutu.|  
|`maxCookieCachingTime`|Element <xref:System.TimeSpan> , który określa maksymalny czas istnienia plików cookie. Wartość domyślna to "10675199.02:48:05.4775807".|  
|`reconnectTransportOnFailure`|Wartość logiczna określająca, czy połączenia za pomocą usługi WS-Reliable messaging podejmie próbę ponownego połączenia po błędów transportu. Wartość domyślna to `true`, co oznacza, że nieskończonej prób ponownego połączenia są próby. Cykl jest dzielony przez limit czasu braku aktywności, co powoduje zgłoszenie wyjątku, gdy nie można ich połączyć kanału.|  
|`replayCacheSize`|Dodatnia liczba całkowita określająca liczbę buforowanych identyfikatorów jednorazowych używanych do wykrywania powtórzeń. W przypadku przekroczenia tego limitu najstarsza identyfikator jednorazowy jest usuwany, a nowy identyfikator jednorazowy jest tworzona dla nowej wiadomości. Wartość domyślna wynosi 500 000.|  
|`replayWindow`|Element <xref:System.TimeSpan> , który określa czas, w której poszczególne komunikatów są poprawni.<br /><br /> Po tym czasie nie będą akceptowane wiadomością wysłaną za pomocą tego samego identyfikatora jednorazowego, wysyłane przed. Ten atrybut jest używany w połączeniu z `maxClockSkew` atrybutu, aby zapobiec włamania. Osoba atakująca może oparte na metodzie powtórzeń komunikat po wygaśnięciu okna powtarzania. Ten komunikat, jednak będą się kończyć niepowodzeniem `maxClockSkew` testu, która odrzuca wiadomości z sygnaturami czasowymi czas wysłania, aż określony czas później lub wcześniejszy niż czas wiadomość została odebrana.|  
|`sessionKeyRenewalInterval`|Element <xref:System.TimeSpan> , który określa czas, po upływie którego inicjator odnowi klucz sesji zabezpieczeń. Wartość domyślna to "10: 00:00".|  
|`sessionKeyRolloverInterval`|A <xref:System.TimeSpan> określający przedział czasu poprzedniego klucza sesji obowiązuje w wiadomościach przychodzących podczas odnawiania klucza. Wartość domyślna to "00: 05:00".<br /><br /> Podczas odnawiania klucza klient i serwer muszą zawsze wysyłania komunikatów przy użyciu najnowszych dostępnych klucza. Obie strony będzie akceptować komunikaty przychodzące zabezpieczony za pomocą klucza poprzedniej sesji, do momentu wygaśnięcia podczas przerzucania.|  
|`timestampValidityDuration`|Dodatnią <xref:System.TimeSpan> , który określa czas, w którym sygnatura czasowa jest poprawna. Wartość domyślna to "00: 15:00".|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<Zabezpieczenia >](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md)|Określa opcje zabezpieczeń dla niestandardowego powiązania.|  
|[\<secureConversationBootstrap>](../../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md)|Określa wartości domyślne używane do inicjowania usługi bezpiecznej konwersacji.|  
  
## <a name="remarks"></a>Uwagi  
 Ustawienia są lokalne w tym sensie, że nie są one ustawienia pochodzące z zasad zabezpieczeń usługi.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.Configuration.LocalClientSecuritySettingsElement>
- <xref:System.ServiceModel.Configuration.SecurityElementBase.LocalClientSettings%2A>
- <xref:System.ServiceModel.Channels.SecurityBindingElement.LocalClientSettings%2A>
- <xref:System.ServiceModel.Channels.LocalClientSecuritySettings>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [Powiązania](../../../../../docs/framework/wcf/bindings.md)
- [Rozszerzanie powiązań](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [Powiązania niestandardowe](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [\<customBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
- [Instrukcje: Tworzenie niestandardowego powiązania za pomocą elementu SecurityBindingElement](../../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
- [Zabezpieczenia powiązania niestandardowego](../../../../../docs/framework/wcf/samples/custom-binding-security.md)
