---
title: <localClientSettings>, element
ms.date: 03/30/2017
ms.assetid: 4680ace5-f4e1-4fcb-b9d8-a4a4af5cd7ae
ms.openlocfilehash: e7331105582a4a48b7edd8cd4f6a691771b0b8ff
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69930799"
---
# <a name="localclientsettings-element"></a>\<localClientSettings> element
Określa ustawienia zabezpieczeń lokalnego klienta dla tego powiązania.  
  
 \<system.serviceModel>  
\<> powiązań  
\<customBinding>  
\<> powiązania  
\<> zabezpieczeń  
  
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
|`cookieRenewalThresholdPercentage`|Liczba całkowita określająca maksymalny procent plików cookie, które mogą być odnawiane. Ta wartość powinna należeć do zakresu od 0 do 100 włącznie. Wartość domyślna to 90.|  
|`detectReplays`|Wartość logiczna określająca, czy ataki powtarzające się na kanał są wykrywane i rozwiązywane automatycznie. Wartość domyślna to `false`.|  
|`maxClockSkew`|A <xref:System.TimeSpan> , która określa maksymalną różnicę czasu między zegarami systemowymi dwóch osób komunikujących się. Wartość domyślna to "00:05:00".<br /><br /> Gdy ta wartość jest ustawiona domyślnie, odbiorca akceptuje komunikaty o sygnaturach czasowych czasu wysłania do 5 minut później lub wcześniej od momentu odebrania komunikatu. Komunikaty, które nie przeszły testu czasu wysłania, są odrzucane. To ustawienie jest używane w połączeniu z `replayWindow` atrybutem.|  
|`maxCookieCachingTime`|A <xref:System.TimeSpan> określa maksymalny okres istnienia plików cookie. Wartość domyślna to "10675199.02:48:05.4775807".|  
|`reconnectTransportOnFailure`|Wartość logiczna określająca, czy połączenia korzystające z protokołu WS-niezawodny będą podejmować próby ponownego nawiązania połączenia po awariach transportu. Wartość domyślna to `true`, co oznacza, że podjęto próbę nieograniczonej próby ponownego nawiązania połączenia. Cykl jest przerwany przez limit czasu braku aktywności, który powoduje, że kanał zgłasza wyjątek, gdy nie można ponownie nawiązać połączenia.|  
|`replayCacheSize`|Dodatnia liczba całkowita określająca liczbę buforowanych identyfikatorów jednorazowych używanych do wykrywania powtórzeń. W przypadku przekroczenia tego limitu najstarszy identyfikator jednorazowy zostanie usunięty i dla nowej wiadomości zostanie utworzony nowy identyfikator jednorazowy. Wartość domyślna to 500000.|  
|`replayWindow`|A <xref:System.TimeSpan> , który określa czas, w którym poszczególne wiadomości identyfikatorów jednorazowych są prawidłowe.<br /><br /> Po tym czasie zostanie wysłany komunikat z tym samym identyfikatorem jednorazowym, który został wysłany wcześniej, nie zostanie zaakceptowany. Ten atrybut jest używany w połączeniu z `maxClockSkew` atrybutem w celu zapobiegania atakom metodą powtórzeń. Osoba atakująca może odtworzyć komunikat po wygaśnięciu okna powtarzania. Jednak ten komunikat `maxClockSkew` przetestuje niepowodzenie testu, który odrzuca komunikaty z sygnaturami czasowymi czasu wysłania do określonego czasu później lub wcześniej od momentu odebrania komunikatu.|  
|`sessionKeyRenewalInterval`|A <xref:System.TimeSpan> , który określa czas, po którym inicjator odnowi klucz dla sesji zabezpieczeń. Wartość domyślna to "10:00:00".|  
|`sessionKeyRolloverInterval`|A <xref:System.TimeSpan> określa przedział czasu, w którym poprzedni klucz sesji jest ważny w przypadku komunikatów przychodzących podczas odnawiania klucza. Wartość domyślna to "00:05:00".<br /><br /> Podczas odnawiania klucza klient i serwer muszą zawsze wysyłać komunikaty przy użyciu najbardziej aktualnego dostępnego klucza. Obie strony będą akceptować wiadomości przychodzące zabezpieczone przy użyciu poprzedniego klucza sesji do momentu wygaśnięcia czasu przerzucania.|  
|`timestampValidityDuration`|Wartość dodatnia <xref:System.TimeSpan> określająca czas ważności sygnatury czasowej. Wartość domyślna to "00:15:00".|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<> zabezpieczeń](security-of-custombinding.md)|Określa opcje zabezpieczeń dla niestandardowego powiązania.|  
|[\<secureConversationBootstrap>](secureconversationbootstrap.md)|Określa wartości domyślne używane do inicjowania usługi bezpiecznej konwersacji.|  
  
## <a name="remarks"></a>Uwagi  
 Ustawienia są lokalne w sensie, że nie są ustawieniami pochodzącymi z zasad zabezpieczeń usługi.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.Configuration.LocalClientSecuritySettingsElement>
- <xref:System.ServiceModel.Configuration.SecurityElementBase.LocalClientSettings%2A>
- <xref:System.ServiceModel.Channels.SecurityBindingElement.LocalClientSettings%2A>
- <xref:System.ServiceModel.Channels.LocalClientSecuritySettings>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [Powiązania](../../../wcf/bindings.md)
- [Rozszerzanie powiązań](../../../wcf/extending/extending-bindings.md)
- [Powiązania niestandardowe](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
- [Instrukcje: Tworzenie niestandardowego powiązania przy użyciu elementu SecurityBindingElement](../../../wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
- [Zabezpieczenia powiązania niestandardowego](../../../wcf/samples/custom-binding-security.md)
