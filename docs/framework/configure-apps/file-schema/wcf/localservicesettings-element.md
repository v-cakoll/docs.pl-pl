---
title: '&lt;localServiceSettings&gt;, element'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0658549c-3f65-46dd-8c5c-9895441ed734
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 08a03a614439a642bd3e9741cd25eca312008c87
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="ltlocalservicesettingsgt-element"></a>&lt;localServiceSettings&gt;, element
Określa ustawienia zabezpieczenia lokalnej usługi dla tego powiązania.  
  
 \<system.serviceModel >  
\<powiązania >  
\<customBinding >  
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
|`detectReplays`|Wartość logiczna określająca, czy ataki metodą kanału wykrytych i zajmuje się automatycznie. Wartość domyślna to `false`.|  
|`inactivityTimeout`|Dodatnią <xref:System.TimeSpan> , który określa okres bezczynności kanału czeka zanim upłynie limit czasu. Wartość domyślna to "01: 00:00".|  
|`issuedCookieLifeTime`|A <xref:System.TimeSpan> określający czas istnienia nadawany wszystkich nowych plików cookie zabezpieczeń. Pliki cookie, które wykraczają poza ich istnienia są odzyskiwane i musi być negocjowane ponownie. Wartość domyślna to "10: 00:00".|  
|`maxCachedCookies`|Dodatnia liczba całkowita, która określa maksymalną liczbę plików cookie, które mogą być buforowane. Wartość domyślna to 1000.|  
|`maxClockSkew`|A <xref:System.TimeSpan> określający maksymalną różnicę czasu między zegarami systemowymi dwóch uczestników komunikacji. Wartość domyślna to "00: 05:00".<br /><br /> Gdy ta wartość ma wartość domyślną, odbiorca akceptuje wiadomości wraz z sygnaturą czasową w czasie wysyłania się do 5 minut lub wcześniej niż czas wiadomość została odebrana. Komunikaty, które nie przejdą testów czasie wysyłania są odrzucane. To ustawienie jest używane w połączeniu z `replayWindow` atrybutu.|  
|`maxPendingSessions`|Dodatnia liczba całkowita, która określa maksymalną liczbę oczekujących sesji bezpieczeństwa obsługiwanych przez usługę. Po osiągnięciu tego limitu, wszyscy nowi klienci odbierać błędach SOAP. Wartość domyślna to 1000.|  
|`maxStatefulNegotiations`|Dodatnia liczba całkowita określająca liczbę negocjacji zabezpieczeń, które mogą być jednocześnie aktywne. Sesje negocjacji poza limitem są umieszczane w kolejce i może zostać zrealizowane wyłącznie po udostępnieniu przestrzeni poniżej limitu. Wartość domyślna to 1024.|  
|`negotiationTimeout`|A <xref:System.TimeSpan> określający czas istnienia zasad bezpieczeństwa używanego przez kanał. Po upływie czasu, podejmuje negocjacje kanału z klientem dla nowych zasad zabezpieczeń. Wartość domyślna to "00: 02:00".|  
|`reconnectTransportOnFailure`|Wartość logiczna określająca, czy próbować połączenia używające obsługi wiadomości WS-Reliable będą odnawiane po błędach transportu. Wartość domyślna to `true`, co oznacza, że są próby nieskończone podejmuje próbę ponownego połączenia. Cykl jest dzielony przez limit czasu bezczynności, co powoduje, że kanał do zgłoszenia wyjątku, gdy nie można go ponownie.|  
|`replayCacheSize`|Dodatnia liczba całkowita określająca liczbę buforowanych identyfikatorów jednorazowych używanych do wykrywania powtórzeń. Po przekroczeniu tego limitu najstarsza identyfikator jednorazowy jest usuwany i nowy identyfikator jednorazowy jest tworzona dla nowej wiadomości. Wartość domyślna wynosi 500 000.|  
|`replayWindow`|A <xref:System.TimeSpan> , który określa czas, w którym identyfikatorów jednorazowych poszczególnych komunikatów są prawidłowe.<br /><br /> Po tym czasie komunikat wysłany z tego samego identyfikator jednorazowy jak wysyłane przed nie będą akceptowane. Ten atrybut jest używany w połączeniu z `maxClockSkew` atrybutu zapobieganie atakom polegającym na odtwarzaniu. Osoba atakująca może powtarzania komunikatu, po wygaśnięciu okna powtarzania. Ten komunikat, jednak nie powiedzie się `maxClockSkew` testów, które odrzuca wiadomości z sygnaturami czasowymi czasie wysyłania maksymalnie przez określony czas, które są nowsze lub wcześniejszy niż czas wiadomość została odebrana.|  
|`sessionKeyRenewalInterval`|A <xref:System.TimeSpan> , który określa czas, po upływie którego inicjator odnowi klucz sesji zabezpieczeń. Wartość domyślna to "10: 00:00".|  
|`sessionKeyRolloverInterval`|A <xref:System.TimeSpan> , który określa przedział czasu poprzedniego klucza sesji jest prawidłowa w komunikatach przychodzących podczas odnawiania klucza. Wartość domyślna to "00: 05:00".<br /><br /> Podczas odnawiania klucza klient i serwer muszą zawsze wysyłanie wiadomości przy użyciu najnowszych dostępnych klucza. Obie strony będzie akceptować zabezpieczonego za pomocą poprzedni klucz sesji do przerzucania czas wygaśnięcia wiadomości przychodzących.|  
|`timestampValidityDuration`|Dodatnią <xref:System.TimeSpan> określający okres ważności sygnatury czasowej. Wartość domyślna to "00: 15:00".|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<Zabezpieczenia >](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md)|Określa opcje zabezpieczeń dla niestandardowego powiązania.|  
|[\<secureConversationBootstrap >](../../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md)|Określa wartości domyślne używane do inicjowania usługi bezpiecznej konwersacji.|  
  
## <a name="remarks"></a>Uwagi  
 Ustawienia są lokalne, ponieważ nie są publikowane jako część zasad zabezpieczeń usługi i nie ma wpływu na powiązań klienta.  
  
 Następujące atrybuty `localServiceSecuritySettings` elementu mogą pomóc ograniczyć przypadki atak typu "odmowa usługi" (DOS) zabezpieczeń:  
  
-   `maxCachedCookies`: steruje maksymalną liczbą SecurityContextTokens ograniczony czas, które są buforowane na serwerze po wykonaniu negocjacji SPNEGO lub SSL.  
  
-   `issuedCookieLifetime`: Określa okres istnienia SecurityContextTokens, które są wydawane przez serwer po negocjacji SPNEGO lub SSL. Serwer buforuje SecurityContextTokens w tym okresie czasu.  
  
-   `maxPendingSessions`: steruje maksymalną liczbą bezpiecznych konwersacji, które są ustalane na serwerze, ale które zostały przetworzone żadnych komunikatów aplikacji. Ten limit przydziału uniemożliwia klientom ustanawiania bezpiecznych konwersacji w usłudze, co powoduje Usługa do przechowywania stanu dla każdego klienta, ale nigdy nie za ich pomocą.  
  
-   `inactivityTimeout`: Określa maksymalny czas czy usługa przechowuje bezpiecznej konwersacji aktywności bez kiedykolwiek odbierania komunikatu aplikacji na nim. Ten limit przydziału uniemożliwia klientom ustanawiania bezpiecznych konwersacji w usłudze, co powoduje Usługa do przechowywania stanu dla każdego klienta, ale nigdy nie za ich pomocą.  
  
 W sesji bezpiecznej konwersacji, należy pamiętać, że oba `inactivityTimeout` i `receiveTimeout` atrybutów w powiązaniu mają wpływ na limit czasu sesji. Krótszą dwóch Określa, kiedy występują przekroczenia limitu czasu.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.Configuration.LocalServiceSecuritySettingsElement>  
 <xref:System.ServiceModel.Configuration.SecurityElementBase.LocalServiceSettings%2A>  
 <xref:System.ServiceModel.Channels.SecurityBindingElement.LocalServiceSettings%2A>  
 <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [Powiązania](../../../../../docs/framework/wcf/bindings.md)  
 [Rozszerzanie powiązań](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [Powiązania niestandardowe](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [\<customBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)  
 [Porady: Tworzenie niestandardowego wiązania za pomocą elementu SecurityBindingElement](../../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)  
 [Zabezpieczenia powiązania niestandardowego](../../../../../docs/framework/wcf/samples/custom-binding-security.md)
