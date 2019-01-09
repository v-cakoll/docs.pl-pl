---
title: '&lt;localServiceSettings&gt;, element'
ms.date: 03/30/2017
ms.assetid: 0658549c-3f65-46dd-8c5c-9895441ed734
ms.openlocfilehash: 5d5150590bc0a8a0d21662eadc7dda67aad872ef
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/09/2019
ms.locfileid: "54150282"
---
# <a name="ltlocalservicesettingsgt-element"></a>&lt;localServiceSettings&gt;, element
Określa ustawienia zabezpieczenia lokalnej usługi dla tego powiązania.  
  
 \<system.serviceModel>  
\<powiązania >  
\<customBinding>  
\<Powiązanie >  
\<Zabezpieczenia >  
  
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
|`detectReplays`|Wartość logiczna, która określa, czy ataki metodą kanał są wykrywane i automatycznie uwzględnione. Wartość domyślna to `false`.|  
|`inactivityTimeout`|Dodatnią <xref:System.TimeSpan> , który określa czas nieaktywności, po którym kanał czeka przed upływem limitu czasu. Wartość domyślna to "01: 00:00".|  
|`issuedCookieLifeTime`|A <xref:System.TimeSpan> określający czas istnienia nadawany wszystkie nowe pliki cookie zabezpieczeń. Pliki cookie, które wykraczają poza ich okres istnienia z kopiami przyrostowymi i muszą być ponownie negocjowane. Wartość domyślna to "10: 00:00".|  
|`maxCachedCookies`|Dodatnia liczba całkowita, określająca maksymalną liczbę plików cookie, które mogą być buforowane. Wartość domyślna to 1000.|  
|`maxClockSkew`|A <xref:System.TimeSpan> określający maksymalną różnicę czasu między zegarami systemowymi dwóch uczestników komunikacji. Wartość domyślna to "00: 05:00".<br /><br /> W przypadku tę wartość ustawiono domyślną, odbiornik akceptuje komunikaty, w których sygnatury czasowe w czasie wysyłania się do 5 minut później, lub wcześniej niż czas wiadomość została odebrana. Wiadomości, które nie są przekazywane do testu czas wysłania są odrzucane. To ustawienie jest używane w połączeniu z `replayWindow` atrybutu.|  
|`maxPendingSessions`|Dodatnia liczba całkowita, określająca maksymalną liczbę oczekujących sesji bezpieczeństwa, obsługiwanych przez usługę. Po osiągnięciu tego limitu, wszyscy nowi klienci otrzymują błędach SOAP. Wartość domyślna to 1000.|  
|`maxStatefulNegotiations`|Dodatnia liczba całkowita, która określa liczbę negocjacji zabezpieczeń, które mogą być wykonywane jednocześnie. Sesje negocjacji poza limitem zostaną umieszczone w kolejce i może zostać zrealizowane wyłącznie po udostępnieniu przestrzeni poniżej limitu. Wartość domyślna to 1024.|  
|`negotiationTimeout`|A <xref:System.TimeSpan> określający czas istnienia zasad bezpieczeństwa używanego przez kanał. Po upływie czasu, kanał podejmuje negocjacje z klientem dla nowych zasad zabezpieczeń. Wartość domyślna to "00: 02:00".|  
|`reconnectTransportOnFailure`|Wartość logiczna określająca, czy połączenia za pomocą usługi WS-Reliable messaging podejmie próbę ponownego połączenia po błędów transportu. Wartość domyślna to `true`, co oznacza, że nieskończonej prób ponownego połączenia są próby. Cykl jest dzielony przez limit czasu braku aktywności, co powoduje zgłoszenie wyjątku, gdy nie można ich połączyć kanału.|  
|`replayCacheSize`|Dodatnia liczba całkowita określająca liczbę buforowanych identyfikatorów jednorazowych używanych do wykrywania powtórzeń. W przypadku przekroczenia tego limitu najstarsza identyfikator jednorazowy jest usuwany, a nowy identyfikator jednorazowy jest tworzona dla nowej wiadomości. Wartość domyślna wynosi 500 000.|  
|`replayWindow`|Element <xref:System.TimeSpan> , który określa czas, w której poszczególne komunikatów są poprawni.<br /><br /> Po tym czasie nie będą akceptowane wiadomością wysłaną za pomocą tego samego identyfikatora jednorazowego, wysyłane przed. Ten atrybut jest używany w połączeniu z `maxClockSkew` atrybutu, aby zapobiec włamania. Osoba atakująca może oparte na metodzie powtórzeń komunikat po wygaśnięciu okna powtarzania. Ten komunikat, jednak będą się kończyć niepowodzeniem `maxClockSkew` testu, która odrzuca wiadomości z sygnaturami czasowymi czas wysłania, aż określony czas później lub wcześniejszy niż czas wiadomość została odebrana.|  
|`sessionKeyRenewalInterval`|Element <xref:System.TimeSpan> , który określa czas, po upływie którego inicjator odnowi klucz sesji zabezpieczeń. Wartość domyślna to "10: 00:00".|  
|`sessionKeyRolloverInterval`|A <xref:System.TimeSpan> określający przedział czasu poprzedniego klucza sesji obowiązuje w wiadomościach przychodzących podczas odnawiania klucza. Wartość domyślna to "00: 05:00".<br /><br /> Podczas odnawiania klucza klient i serwer muszą zawsze wysyłania komunikatów przy użyciu najnowszych dostępnych klucza. Obie strony będzie akceptować komunikaty przychodzące zabezpieczony za pomocą klucza poprzedniej sesji, do momentu wygaśnięcia podczas przerzucania.|  
|`timestampValidityDuration`|Dodatnią <xref:System.TimeSpan> , który określa czas, w którym sygnatura czasowa jest poprawna. Wartość domyślna to "00: 15:00".|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<Zabezpieczenia >](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md)|Określa opcje zabezpieczeń dla niestandardowego powiązania.|  
|[\<secureConversationBootstrap >](../../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md)|Określa wartości domyślne używane do inicjowania usługi bezpiecznej konwersacji.|  
  
## <a name="remarks"></a>Uwagi  
 Ustawienia są lokalne, ponieważ nie są publikowane jako część zasad zabezpieczeń usługi i nie ma wpływu na powiązań klienta.  
  
 Następujące atrybuty `localServiceSecuritySettings` element mogą pomóc ograniczyć atak typu "odmowa usługi" (DOS) zabezpieczeń:  
  
-   `maxCachedCookies`: Określa maksymalną liczbę SecurityContextTokens ograniczone czasowo, które są buforowane przez serwer po wykonaniu tej negocjacji SPNEGO lub SSL.  
  
-   `issuedCookieLifetime`: Określa okres istnienia SecurityContextTokens, które są wydawane przez serwer po negocjacji SPNEGO lub SSL. Serwer buforuje SecurityContextTokens przez ten czas.  
  
-   `maxPendingSessions`: Określa maksymalną liczbę bezpiecznych konwersacji, które są ustalane na serwerze, ale żadne komunikaty aplikacji przetworzonych. Ten limit przydziału uniemożliwia klientom po ustanawianie bezpiecznej konwersacji na usługę, co powoduje usługi do zarządzania stanem dla każdego klienta, ale nigdy z nich korzystać.  
  
-   `inactivityTimeout`: Określa maksymalny czas, usługa utrzymuje bezpiecznej konwersacji aktywność bez otrzymania kiedykolwiek komunikatu aplikacji na nim. Ten limit przydziału uniemożliwia klientom po ustanawianie bezpiecznej konwersacji na usługę, co powoduje usługi do zarządzania stanem dla każdego klienta, ale nigdy z nich korzystać.  
  
 W sesji bezpiecznej konwersacji, należy pamiętać, że oba `inactivityTimeout` i `receiveTimeout` atrybutów w powiązaniu wpływa na limit czasu sesji. Im krótsze dwa Określa, kiedy występują przekroczenia limitu czasu.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.Configuration.LocalServiceSecuritySettingsElement>  
 <xref:System.ServiceModel.Configuration.SecurityElementBase.LocalServiceSettings%2A>  
 <xref:System.ServiceModel.Channels.SecurityBindingElement.LocalServiceSettings%2A>  
 <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [Powiązania](../../../../../docs/framework/wcf/bindings.md)  
 [Rozszerzanie powiązań](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [Powiązania niestandardowe](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [\<customBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)  
 [Instrukcje: Tworzenie niestandardowego powiązania za pomocą elementu SecurityBindingElement](../../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)  
 [Zabezpieczenia powiązania niestandardowego](../../../../../docs/framework/wcf/samples/custom-binding-security.md)
