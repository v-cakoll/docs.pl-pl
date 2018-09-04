---
title: '&lt;wsHttpContextBinding&gt;'
ms.date: 03/30/2017
ms.assetid: 1e40b5c9-0df2-4d66-afc5-a99d0e4ae7a4
ms.openlocfilehash: 59322cfd260aada0a13a8215946914ef21c182c7
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43505476"
---
# <a name="ltwshttpcontextbindinggt"></a>&lt;wsHttpContextBinding&gt;
Dostarcza kontekst dla <xref:System.ServiceModel.WSHttpBinding> wymaga, aby poziom ochrony były podpisane.  
  
\<system.serviceModel>  
\<powiązania >  
\<wsHttpContextBinding>  
  
## <a name="syntax"></a>Składnia  
  
```xml
<wsHttpContextBinding>  
  <binding allowCookies="Boolean" 
           bypassProxyOnLocal="Boolean"  
           closeTimeout="TimeSpan" 
           contextProtectionLevel="EncryptAndSign/None/Sign" 
           hostNameComparisonMode="StrongWildCard/Exact/WeakWildcard" 
           maxBufferPoolSize="integer" 
           maxReceivedMessageSize="Integer" 
           messageEncoding="Text/Mtom" 
           name="string" 
           openTimeout="TimeSpan" 
           proxyAddress="URI" 
           receiveTimeout="TimeSpan" 
           sendTimeout="TimeSpan" 
           textEncoding="UnicodeFffeTextEncoding/Utf16TextEncoding/Utf8TextEncoding"  
           transactionFlow="Boolean"  
           useDefaultWebProxy="Boolean">  
    <reliableSession ordered="Boolean"  
                     inactivityTimeout="TimeSpan"  
                     enabled="Boolean" />  
    <security mode="Message/None/Transport/TransportWithCredential">  
      <transport clientCredentialType="Basic/Certificate/Digest/None/Ntlm/Windows"  
                 proxyCredentialType="Basic/Digest/None/Ntlm/Windows"  
                 realm="string"   
                 defaultClientCredentialType="Basic/Certificate/Digest/None/Ntlm/Windows"  
                 defaultProxyCredentialType="Basic/Digest/None/Ntlm/Windows"  
                 defaultRealm="string" />  
      <message clientCredentialType="Certificate/IssuedToken/None/UserName/Windows"  
               algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"  
               establishSecurityContext="Boolean"   
               negotiateServiceCredential="Boolean" />  
    </security>  
    <readerQuotas maxArrayLength="Integer" 
                  maxBytesPerRead="Integer" 
                  maxDepth="Integer" 
                  maxNameTableCharCount="Integer" 
                  maxStringContentLength="Integer" />
  </binding>  
</wsHttpContextBinding>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|allowCookies|Wartość logiczna, która wskazuje, czy klient akceptuje pliki cookie i propaguje je do przyszłych żądań. Wartość domyślna to `false`.<br /><br /> Gdy `allowCookies` ustawiono `true`, obiekt contextChannel użyje httpCookies jako tryb wymiany kontekstu. Jeśli ten atrybut jest równa `false`, kontekst są wymieniane jako nagłówków protokołu soap.<br /><br /> Wartość domyślna to `false`.<br /><br /> Podczas interakcji z usługami sieci Web ASMX, które używają plików cookie, można użyć tej właściwości. W ten sposób można się upewnić, że pliki cookie, zwrócona z serwera są automatycznie kopiowane do wszystkich przyszłych żądań za daną usługę.|  
|bypassProxyOnLocal|Wartość logiczna, która wskazuje, czy pominąć serwer proxy dla adresów lokalnych. Wartość domyślna to `false`.|  
|closeTimeout|A <xref:System.TimeSpan> wartość, która określa przedział czasu przewidzianego na zakończenie operacji zamknięcia. Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>. Wartość domyślna to 00:01:00.|  
|contextProtectionLevel|Nieprawidłowy <xref:System.Net.Security.ProtectionLevel> wartość, która określa poziom ochrony żądany nagłówek SOAP, wykorzystywany do propagowania informacje o kontekście.  Wartość domyślna to `Sign`.|  
|hostnameComparisonMode|Określa tryb porównywania nazwy hosta HTTP używany do analizowania identyfikatorów URI. Ten atrybut jest typu <xref:System.ServiceModel.HostNameComparisonMode>, która wskazuje, czy nazwa hosta jest używana w celu dotarcia do usługi podczas dopasowywania identyfikatora URI. Wartość domyślna to <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, który ignoruje hostname dopasowania.|  
|maxBufferPoolSize|Liczba całkowita określająca maksymalny rozmiar puli buforów dla tego powiązania. Wartość domyślna to 524,288 bajtów (512 * 1024). Wiele części programu Windows Communication Foundation (WCF) za pomocą buforów. Tworzenie i niszczenie buforów za każdym razem, gdy są one używane jest kosztowne, a także jest kosztowne wyrzucania elementów bezużytecznych dla buforów. Dzięki pulom buforu zająć buforu z puli, go używać i przywrócić go do puli, gdy wszystko będzie gotowe. Ten sposób unika się obciążenie tworzeniem i likwidowaniem buforów.|  
|maxReceivedMessageSize|Dodatnia liczba całkowita, która określa maksymalny rozmiar komunikatu, w bajtach, włącznie z nagłówkami, które może zostać odebrany w kanale skonfigurowany tym wiązaniem. Nadawca wiadomości przekroczenie tego limitu zostanie wyświetlony błąd protokołu SOAP. Należy określić odbiorcę porzuca wiadomość i tworzy wpis zdarzenia w dzienniku śledzenia. Wartość domyślna to 65536.|  
|messageEncoding|Definiuje encoder umożliwia kodowanie wiadomości. Prawidłowe wartości są następujące:<br /><br /> -Text: Użyj koder komunikatu tekstowego.<br />-Mtom: Za pomocą kodera komunikatów transmisji organizacji mechanizm 1.0 (MTOM).<br />— Wartość domyślna to Text.<br /><br /> Ten atrybut jest typu <xref:System.ServiceModel.WSMessageEncoding>.|  
|nazwa|Ciąg, który zawiera nazwę konfiguracji powiązania. Wartość ta powinna być unikatowy, ponieważ jest używany jako identyfikator dla wiązania. Począwszy od [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], powiązania i zachowania nie muszą mieć nazwę. Aby uzyskać więcej informacji o domyślnej konfiguracji i powiązania pustego oraz zachowań, zobacz [uproszczona konfiguracja](../../../../../docs/framework/wcf/simplified-configuration.md) i [uproszczona konfiguracja usług WCF](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).|  
|openTimeout|A <xref:System.TimeSpan> wartość, która określa przedział czasu przewidzianego na zakończenie operacji Otwórz. Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>. Wartość domyślna to 00:01:00.|  
|proxyAddress|Identyfikator URI, który określa adres serwera proxy HTTP. Jeśli `useSystemWebProxy` jest `true`, to ustawienie musi być `null`. Wartość domyślna to `null`.|  
|receiveTimeout|A <xref:System.TimeSpan> wartość, która określa przedział czasu przewidzianego na ukończenie operacji odbierania. Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>. Wartość domyślna to 00:01:00.|  
|sendTimeout|A <xref:System.TimeSpan> wartość, która określa przedział czasu przewidzianego na ukończenie operacji wysyłania. Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>. Wartość domyślna to 00:01:00.|  
|textEncoding|Określa kodowanie do użycia w celu emisji komunikatów w powiązaniu zestawu znaków. Prawidłowe wartości są następujące:<br /><br /> -UnicodeFffeTextEncoding: Unicode BigEndian kodowanie.<br />-Utf16TextEncoding: 16-bitowego kodowania.<br />-Utf8TextEncoding: 8-bitowego kodowania.<br /><br /> Wartość domyślna to Utf8TextEncoding.<br /><br /> Ten atrybut jest typu <xref:System.Text.Encoding>.|  
|transactionFlow|Wartość logiczna określająca, czy powiązanie obsługuje płynące WS-transakcji. Wartość domyślna to `false`.|  
|useDefaultWebProxy|Wartość logiczna określająca, czy jest używany serwer proxy HTTP systemu skonfigurowany automatycznie. Wartość domyślna to `true`.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<Zabezpieczenia >](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md)|Definiuje ustawienia zabezpieczeń dla wiązania. Ten element jest typu <xref:System.ServiceModel.Configuration.WSHttpSecurityElement>.|  
|[\<readerQuotas>](https://msdn.microsoft.com/library/3e5e42ff-cef8-478f-bf14-034449239bfd)|Definiuje ograniczenia złożoności wiadomości SOAP, które mogą być przetwarzane przez punkty końcowe skonfigurowane dla tego wiązania. Ten element jest typu <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.|  
|[reliableSession](https://msdn.microsoft.com/library/9c93818a-7dfa-43d5-b3a1-1aafccf3a00b)|Określa, jeśli niezawodnej sesji są ustanawiane między punktami końcowymi kanału.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<powiązania >](../../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)|Ten element przetrzymuje kolekcję powiązań standardowych i niestandardowych.|  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.WSHttpBinding>  
 <xref:System.ServiceModel.WSHttpContextBinding>  
 <xref:System.ServiceModel.Configuration.WSHttpContextBindingElement>  
 <xref:System.ServiceModel.Channels.ContextBindingElement>  
 [Powiązania](../../../../../docs/framework/wcf/bindings.md)  
 [Konfigurowanie powiązań dostarczanych przez system](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [Konfigurowanie Windows Communication Foundation i klientów za pomocą powiązań](https://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [\<Powiązanie >](../../../../../docs/framework/misc/binding.md)  
 [\<wsHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)
