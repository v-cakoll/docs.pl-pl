---
title: <localServiceSettings>, element
ms.date: 03/30/2017
ms.assetid: 0658549c-3f65-46dd-8c5c-9895441ed734
ms.openlocfilehash: 36fcc9454a5762a4a375cc7f6eaee1c4cf0580e2
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69931729"
---
# <a name="localservicesettings-element"></a>\<localServiceSettings, element >
Określa ustawienia zabezpieczeń usługi lokalnej dla tego powiązania.  
  
 \<system.serviceModel>  
\<> powiązań  
\<customBinding>  
\<> powiązania  
\<> zabezpieczeń  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<security>
  <localServiceSettings detectReplays="Boolean"
                        inactivityTimeout="TimeSpan"
                        issuedCookieLifeTime="TimeSpan"
                        maxCachedCookies="Integer"
                        maxClockSkew="TimeSpan"
                        maxPendingSessions="Integer"
                        maxStatefulNegotiations="Integer"
                        negotiationTimeout="TimeSpan"
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
|`detectReplays`|Wartość logiczna określająca, czy ataki powtarzające się na kanał są wykrywane i rozwiązywane automatycznie. Wartość domyślna to `false`.|  
|`inactivityTimeout`|Wartość dodatnia <xref:System.TimeSpan> , która określa czas braku aktywności kanału przed upływem limitu czasu. Wartość domyślna to "01:00:00".|  
|`issuedCookieLifeTime`|A <xref:System.TimeSpan> określa okres istnienia wystawiony dla wszystkich nowych plików cookie zabezpieczeń. Pliki cookie, które przekraczają ich okres istnienia, są odtwarzane i muszą zostać ponownie wynegocjowane. Wartość domyślna to "10:00:00".|  
|`maxCachedCookies`|Dodatnia liczba całkowita, która określa maksymalną liczbę plików cookie, które mogą być buforowane. Wartość domyślna to 1000.|  
|`maxClockSkew`|A <xref:System.TimeSpan> , która określa maksymalną różnicę czasu między zegarami systemowymi dwóch osób komunikujących się. Wartość domyślna to "00:05:00".<br /><br /> Gdy ta wartość jest ustawiona domyślnie, odbiorca akceptuje komunikaty o sygnaturach czasowych czasu wysłania do 5 minut później lub wcześniej od momentu odebrania komunikatu. Komunikaty, które nie przeszły testu czasu wysłania, są odrzucane. To ustawienie jest używane w połączeniu z `replayWindow` atrybutem.|  
|`maxPendingSessions`|Dodatnia liczba całkowita, która określa maksymalną liczbę oczekujących sesji bezpieczeństwa obsługiwanych przez usługę. Po osiągnięciu tego limitu Wszyscy nowi klienci odbierają błędy protokołu SOAP. Wartość domyślna to 1000.|  
|`maxStatefulNegotiations`|Dodatnia liczba całkowita, która określa liczbę negocjacji zabezpieczeń, które mogą być jednocześnie aktywne. Sesje negocjacji przekraczające limit są umieszczane w kolejce i można je wykonać tylko wtedy, gdy będzie dostępna spacja poniżej limitu. Wartość domyślna to 1024.|  
|`negotiationTimeout`|A <xref:System.TimeSpan> określa okres istnienia zasad zabezpieczeń używanych przez kanał. Po upływie tego czasu kanał jest negocjowany ponownie z klientem w celu uzyskania nowych zasad zabezpieczeń. Wartość domyślna to "00:02:00".|  
|`reconnectTransportOnFailure`|Wartość logiczna określająca, czy połączenia korzystające z protokołu WS-niezawodny będą podejmować próby ponownego nawiązania połączenia po awariach transportu. Wartość domyślna to `true`, co oznacza, że podjęto próbę nieograniczonej próby ponownego nawiązania połączenia. Cykl jest przerwany przez limit czasu braku aktywności, który powoduje, że kanał zgłasza wyjątek, gdy nie można ponownie nawiązać połączenia.|  
|`replayCacheSize`|Dodatnia liczba całkowita określająca liczbę buforowanych identyfikatorów jednorazowych używanych do wykrywania powtórzeń. W przypadku przekroczenia tego limitu najstarszy identyfikator jednorazowy zostanie usunięty i dla nowej wiadomości zostanie utworzony nowy identyfikator jednorazowy. Wartość domyślna to 500000.|  
|`replayWindow`|A <xref:System.TimeSpan> , który określa czas, w którym poszczególne wiadomości identyfikatorów jednorazowych są prawidłowe.<br /><br /> Po tym czasie zostanie wysłany komunikat z tym samym identyfikatorem jednorazowym, który został wysłany wcześniej, nie zostanie zaakceptowany. Ten atrybut jest używany w połączeniu z `maxClockSkew` atrybutem w celu zapobiegania atakom metodą powtórzeń. Osoba atakująca może odtworzyć komunikat po wygaśnięciu okna powtarzania. Jednak ten komunikat `maxClockSkew` przetestuje niepowodzenie testu, który odrzuca komunikaty z sygnaturami czasowymi czasu wysłania do określonego czasu później lub wcześniej od momentu odebrania komunikatu.|  
|`sessionKeyRenewalInterval`|A <xref:System.TimeSpan> , który określa czas, po którym inicjator odnowi klucz dla sesji zabezpieczeń. Wartość domyślna to "10:00:00".|  
|`sessionKeyRolloverInterval`|A <xref:System.TimeSpan> określa przedział czasu, w którym poprzedni klucz sesji jest ważny w przypadku komunikatów przychodzących podczas odnawiania klucza. Wartość domyślna to "00:05:00".<br /><br /> Podczas odnawiania klucza klient i serwer muszą zawsze wysyłać komunikaty przy użyciu najbardziej aktualnego dostępnego klucza. Obie strony będą akceptować wiadomości przychodzące zabezpieczone przy użyciu poprzedniego klucza sesji do momentu wygaśnięcia czasu przerzucania.|  
|`timestampValidityDuration`|Wartość dodatnia <xref:System.TimeSpan> określająca czas ważności sygnatury czasowej. Wartość domyślna to "00:15:00".|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<> zabezpieczeń](security-of-custombinding.md)|Określa opcje zabezpieczeń dla niestandardowego powiązania.|  
|[\<secureConversationBootstrap>](secureconversationbootstrap.md)|Określa wartości domyślne używane do inicjowania usługi bezpiecznej konwersacji.|  
  
## <a name="remarks"></a>Uwagi  
 Ustawienia są lokalne, ponieważ nie są publikowane w ramach zasad zabezpieczeń usługi i nie mają wpływu na powiązanie klienta.  
  
 Następujące atrybuty `localServiceSecuritySettings` elementu mogą pomóc w ograniczeniu ataku typu "odmowa usługi" (DOS):  
  
- `maxCachedCookies`: określa maksymalną liczbę SecurityContextTokens związanych z limitem czasu, które są buforowane przez serwer po wykonaniu negocjacji SPNEGO lub SSL.  
  
- `issuedCookieLifetime`: steruje okresem istnienia SecurityContextTokens wystawionego przez serwer po negocjacji SPNEGO lub SSL. Serwer buforuje SecurityContextTokens w tym okresie czasu.  
  
- `maxPendingSessions`: określa maksymalną liczbę bezpiecznych konwersacji, które są ustanowione na serwerze, ale dla których nie przetworzono komunikatów aplikacji. Ten limit przydziału uniemożliwia klientom ustanawianie bezpiecznych konwersacji w usłudze, co powoduje, że usługa zachowuje stan dla każdego klienta, ale nigdy nie korzysta z nich.  
  
- `inactivityTimeout`: określa maksymalny czas, przez który usługa utrzymuje bezpieczną konwersację, bez odebrania na niej komunikatu aplikacji. Ten limit przydziału uniemożliwia klientom ustanawianie bezpiecznych konwersacji w usłudze, co powoduje, że usługa zachowuje stan dla każdego klienta, ale nigdy nie korzysta z nich.  
  
 W sesji bezpiecznej konwersacji należy zauważyć, że zarówno `inactivityTimeout` , `receiveTimeout` jak i atrybuty dotyczące powiązań wpływają na limit czasu sesji. Krótszy z dwóch określa czas wystąpienia przekroczeń limitu czasu.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.Configuration.LocalServiceSecuritySettingsElement>
- <xref:System.ServiceModel.Configuration.SecurityElementBase.LocalServiceSettings%2A>
- <xref:System.ServiceModel.Channels.SecurityBindingElement.LocalServiceSettings%2A>
- <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [Powiązania](../../../wcf/bindings.md)
- [Rozszerzanie powiązań](../../../wcf/extending/extending-bindings.md)
- [Powiązania niestandardowe](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
- [Instrukcje: Tworzenie niestandardowego powiązania przy użyciu elementu SecurityBindingElement](../../../wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
- [Zabezpieczenia powiązania niestandardowego](../../../wcf/samples/custom-binding-security.md)
