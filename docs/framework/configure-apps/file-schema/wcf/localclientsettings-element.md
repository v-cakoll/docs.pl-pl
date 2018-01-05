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
# <a name="ltlocalclientsettingsgt-element"></a>&lt;localClientSettings&gt;, element
Określa ustawienia zabezpieczenia lokalnego klienta dla tego powiązania.  
  
 \<system.serviceModel >  
\<powiązania >  
\<customBinding >  
\<Powiązanie >  
\<Zabezpieczenia >  
  
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
|`cacheCookies`|Wartość logiczna określająca czy włączone jest buforowanie plików cookie. Wartość domyślna to `false`.|  
|`cookieRenewalThresholdPercentage`|Liczba całkowita określająca maksymalny procent plików cookie, które mogą być odnawiane. Wartość ta powinna być pomiędzy 0 a 100 włącznie. Domyślna wartość to 90.|  
|`detectReplays`|Wartość logiczna określająca, czy ataki metodą kanału wykrytych i zajmuje się automatycznie. Wartość domyślna to `false`.|  
|`maxClockSkew`|A <xref:System.TimeSpan> określający maksymalną różnicę czasu między zegarami systemowymi dwóch uczestników komunikacji. Wartość domyślna to "00: 05:00".<br /><br /> Gdy ta wartość ma wartość domyślną, odbiorca akceptuje wiadomości wraz z sygnaturą czasową w czasie wysyłania się do 5 minut lub wcześniej niż czas wiadomość została odebrana. Komunikaty, które nie przejdą testów czasie wysyłania są odrzucane. To ustawienie jest używane w połączeniu z `replayWindow` atrybutu.|  
|`maxCookieCachingTime`|A <xref:System.TimeSpan> , który określa maksymalny okres istnienia plików cookie. Wartość domyślna to "10675199.02:48:05.4775807".|  
|`reconnectTransportOnFailure`|Wartość logiczna określająca, czy próbować połączenia używające obsługi wiadomości WS-Reliable będą odnawiane po błędach transportu. Wartość domyślna to `true`, co oznacza, że są próby nieskończone podejmuje próbę ponownego połączenia. Cykl jest dzielony przez limit czasu bezczynności, co powoduje, że kanał do zgłoszenia wyjątku, gdy nie można go ponownie.|  
|`replayCacheSize`|Dodatnia liczba całkowita określająca liczbę buforowanych identyfikatorów jednorazowych używanych do wykrywania powtórzeń. Po przekroczeniu tego limitu najstarsza identyfikator jednorazowy jest usuwany i nowy identyfikator jednorazowy jest tworzona dla nowej wiadomości. Wartość domyślna wynosi 500 000.|  
|`replayWindow`|A <xref:System.TimeSpan> , który określa czas, w którym identyfikatorów jednorazowych poszczególnych komunikatów są prawidłowe.<br /><br /> Po tym czasie komunikat wysłany z tego samego identyfikator jednorazowy jak wysyłane przed nie będą akceptowane. Ten atrybut jest używany w połączeniu z `maxClockSkew` atrybutu zapobieganie atakom polegającym na odtwarzaniu. Osoba atakująca może powtarzania komunikatu, po wygaśnięciu okna powtarzania. Ten komunikat, jednak nie powiedzie się `maxClockSkew` testów, które odrzuca wiadomości z sygnaturami czasowymi czasie wysyłania maksymalnie przez określony czas, które są nowsze lub wcześniejszy niż czas wiadomość została odebrana.|  
|`sessionKeyRenewalInterval`|A <xref:System.TimeSpan> , który określa czas, po upływie którego inicjator odnowi klucz sesji zabezpieczeń. Wartość domyślna to "10: 00:00".|  
|`sessionKeyRolloverInterval`|A <xref:System.TimeSpan> , który określa przedział czasu poprzedniego klucza sesji jest prawidłowa w komunikatach przychodzących podczas odnawiania klucza. Wartość domyślna to "00: 05:00".<br /><br /> Podczas odnawiania klucza klient i serwer muszą zawsze wysyłanie wiadomości przy użyciu najnowszych dostępnych klucza. Obie strony będzie akceptować zabezpieczonego za pomocą poprzedni klucz sesji do przerzucania czas wygaśnięcia wiadomości przychodzących.|  
|`timestampValidityDuration`|Dodatnią <xref:System.TimeSpan> określający okres ważności sygnatury czasowej. Wartość domyślna to "00: 15:00".|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<Zabezpieczenia >](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md)|Określa opcje zabezpieczeń dla niestandardowego powiązania.|  
|[\<secureConversationBootstrap >](../../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md)|Określa wartości domyślne używane do inicjowania usługi bezpiecznej konwersacji.|  
  
## <a name="remarks"></a>Uwagi  
 Ustawienia są lokalne w tym sensie, że nie są one ustawienia pochodzące z zasad zabezpieczeń usługi.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.Configuration.LocalClientSecuritySettingsElement>  
 <xref:System.ServiceModel.Configuration.SecurityElementBase.LocalClientSettings%2A>  
 <xref:System.ServiceModel.Channels.SecurityBindingElement.LocalClientSettings%2A>  
 <xref:System.ServiceModel.Channels.LocalClientSecuritySettings>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [Powiązania](../../../../../docs/framework/wcf/bindings.md)  
 [Rozszerzanie powiązań](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [Powiązania niestandardowe](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [\<customBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)  
 [Instrukcje: tworzenie niestandardowego powiązania za pomocą elementu SecurityBindingElement](../../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)  
 [Zabezpieczenia powiązania niestandardowego](../../../../../docs/framework/wcf/samples/custom-binding-security.md)
