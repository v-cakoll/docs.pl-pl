---
title: '&lt;wsDualHttpBinding&gt;'
ms.date: 03/30/2017
helpviewer_keywords:
- wsDualHttpBinding Element
ms.assetid: fd8ac4e2-5641-473b-9115-73f14ab1c065
ms.openlocfilehash: 8a0dd9dcb7720da7dfd809b09b039819ba2a34ed
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32758974"
---
# <a name="ltwsdualhttpbindinggt"></a>&lt;wsDualHttpBinding&gt;
Definiuje bezpieczne, niezawodne i interoperacyjne powiązanie, które jest odpowiednie dla kontraktów usługi duplex lub komunikacji za pośrednictwem pośredników SOAP.  
  
 \<system.ServiceModel>  
\<powiązania >  
\<wsDualHttpBinding >  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<wsDualHttpBinding>  
        <binding name="string"  
        closeTimeout="TimeSpan"  
        openTimeout="TimeSpan"   
        receiveTimeout="TimeSpan"  
        sendTimeout="TimeSpan"  
        bypassProxyOnLocal="Boolean"  
        clientBaseAddress="URI"  
        transactionFlow="Boolean"   
        hostNameComparisonMode="StrongWildCard/Exact/WeakWildcard"  
        maxBufferPoolSize="integer"  
        maxReceivedMessageSize="Integer"  
        messageEncoding="Text/Mtom"   
        proxyAddress="URI"  
  
textEncoding="Unicode/BigEndianUnicode/UTF8"  
        useDefaultWebProxy="Boolean">  
        <reliableSession ordered="Boolean"  
            inactivityTimeout="TimeSpan" />  
        <security mode="None/Message">  
           <message clientCredentialType="None/Windows/UserName/Certificate/CardSpace"  
                negotiateServiceCredential="Boolean"  
                    algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15" />  
                </security>  
       <readerQuotas             maxArrayLength="Integer"            maxBytesPerRead="Integer"            maxDepth="Integer"             maxNameTableCharCount="Integer"                     maxStringContentLength="Integer" />    </binding>  
</wsDualHttpBinding>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty i elementy podrzędne, elementy nadrzędne  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|bypassProxyOnLocal|Wartość logiczna, która wskazuje, czy pominąć serwer proxy dla adresów lokalnych. Wartość domyślna to `false`.|  
|clientBaseAddress|Identyfikator URI, który ustawia adres podstawowy nasłuchujący klienta dla wiadomości odpowiedzi z usługi. Jeśli jest określony, ten adres (oraz na channelGUID) jest używany do nasłuchiwania. Jeśli nie określono wartości, adres podstawowy klienta jest generowane w sposób specyficznych dla transportu. Wartość domyślna to `null`.|  
|closeTimeout|A <xref:System.TimeSpan> wartość, która określa interwał przeznaczony na zakończenie operacji zamknięcia. Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>. Wartość domyślna to 00:01:00.|  
|hostnameComparisonMode|Określa tryb porównania nazw hostów HTTP używany do przeprowadzenia analizy identyfikatorów URI. Ten atrybut jest typu <xref:System.ServiceModel.HostNameComparisonMode>, która wskazuje, czy nazwa hosta jest używana w celu dotarcia do usługi podczas dopasowywania identyfikatora URI. Wartość domyślna to <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, który ignoruje nazwy hosta w dopasowania.|  
|MaxBufferPoolSize|Liczba całkowita określająca maksymalny rozmiar puli buforów dla tego powiązania. Wartość domyślna to 524,288 bajtów (512 * 1024). Bufory za pomocą wielu części programu Windows Communication Foundation (WCF). Tworzenie i niszczenie buforów za każdym razem, gdy są one używane jest kosztowne i odzyskiwanie pamięci dla buforów również jest kosztowna. Używając puli buforów można podjąć buforu z puli, ten jest używany i zwracać do puli, gdy wszystko będzie gotowe. W związku z tym jest unikać obciążenie związane z tworzeniem i niszczenie buforów.|  
|maxReceivedMessageSize|Dodatnia liczba całkowita, która określa maksymalny rozmiar wiadomości, w bajtach, włącznie z nagłówkami, odebranych z kanału skonfigurowane dla tego wiązania. Nadawcy wiadomości przekracza ten limit, zostanie wyświetlony błąd protokołu SOAP. Odbiornik porzuca wiadomości i tworzy wpis zdarzenia w dzienniku śledzenia. Wartość domyślna to 65536.|  
|messageEncoding|Definiuje koder używany do kodowania komunikatu. Prawidłowe wartości są następujące:<br /><br /> -Tekst: Użyj kodera wiadomości tekstowych.<br />-Mtom: Za pomocą kodera wiadomości transmisji organizacji mechanizmu 1.0 (MTOM).<br />— Wartość domyślna to tekst.<br /><br /> Ten atrybut jest typu <xref:System.ServiceModel.WSMessageEncoding>.|  
|nazwa|Ciąg zawierający nazwę konfiguracji powiązania. Wartość ta powinna być unikatowa, ponieważ jest używany jako identyfikator dla tego powiązania. Począwszy od [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], powiązania i zachowania nie muszą mieć nazwę. Aby uzyskać więcej informacji o konfiguracji domyślnej i bez powiązania i zachowania, zobacz [uproszczony konfiguracji](../../../../../docs/framework/wcf/simplified-configuration.md) i [uproszczona konfiguracja usług WCF](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).|  
|openTimeout|A <xref:System.TimeSpan> wartość, która określa interwał przeznaczony na zakończenie operacji otwarcia. Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>. Wartość domyślna to 00:01:00.|  
|proxyAddress|Identyfikator URI, który określa adres serwera proxy HTTP. Jeśli `useDefaultWebProxy` jest `true`, to ustawienie musi być `null`. Wartość domyślna to `null`.|  
|receiveTimeout|A <xref:System.TimeSpan> wartość, która określa interwał przeznaczony na zakończenie operacji odbioru. Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>. Wartość domyślna to 00:01:00.|  
|sendTimeout|A <xref:System.TimeSpan> wartość, która określa interwał przeznaczony na zakończenie operacji wysyłania. Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>. Wartość domyślna to 00:01:00.|  
|textEncoding|Ustawia kodowanie do użycia w celu emisji komunikatów w powiązaniu zestawu znaków. Prawidłowe wartości są następujące:<br /><br /> -BigEndianUnicode: Unicode BigEndian kodowanie.<br />-Unicode: 16-bitowego kodowania.<br />-UTF8: 8-bitowego kodowania o<br /><br /> Wartość domyślna to UTF8. Ten atrybut jest typu <xref:System.Text.Encoding>.|  
|transactionFlow|Wartość logiczna określająca, czy wiązanie obsługuje przechodzenia WS-transakcji. Wartość domyślna to `false`.|  
|useDefaultWebProxy|Wartość logiczna wskazująca, czy jest używany serwer proxy HTTP systemu skonfigurowany automatycznie. Adres serwera proxy musi być `null` (to znaczy, że nie ustawiono) Jeśli ten atrybut jest `true`. Wartość domyślna to `true`.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<Zabezpieczenia >](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wsdualhttpbinding.md)|Definiuje ustawienia zabezpieczeń dla powiązania. Ten element jest typu <xref:System.ServiceModel.Configuration.WSDualHttpSecurityElement>.|  
|[\<readerQuotas>](http://msdn.microsoft.com/library/3e5e42ff-cef8-478f-bf14-034449239bfd)|Definiuje ograniczenia złożoności wiadomości SOAP, które mogą być przetwarzane przez punkty końcowe skonfigurowane dla tego wiązania. Ten element jest typu <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.|  
|[reliableSession](http://msdn.microsoft.com/library/9c93818a-7dfa-43d5-b3a1-1aafccf3a00b)|Określa, czy niezawodnej sesji są połączenia między punktami końcowymi kanału.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<powiązania >](../../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)|Ten element przetrzymuje kolekcję powiązań standardowych i niestandardowych.|  
  
## <a name="remarks"></a>Uwagi  
 `WSDualHttpBinding` Udostępnia możliwość obsługi tego samego protokoły usług sieci Web jako `WSHttpBinding`, ale do użycia z kontraktów dupleksowych. `WSDualHttpBinding` obsługuje zabezpieczenia protokołu SOAP i tylko wymaga niezawodnej obsługi komunikatów. To powiązanie wymaga, że klient ma publiczny identyfikator URI, który zawiera punkt końcowy wywołania zwrotnego dla usługi. Jest to obsługiwane przez `clientBaseAddress` atrybutu. Dwa powiązania udostępnia adres IP klienta do usługi. Klienta należy użyć zabezpieczeń, aby upewnić się, że go tylko łączy się z usługami go relacji zaufania.  
  
 To powiązanie może służyć do niezawodnego komunikacji za pośrednictwem pośredników SOAP co najmniej jeden.  
  
 Domyślnie to powiązanie generuje stosu środowiska wykonawczego o WS-ReliableMessaging niezawodności, WS-Security komunikat zabezpieczeń i uwierzytelniania HTTP w celu dostarczania komunikatów i kodowanie wiadomości tekstowe i XML.  
  
## <a name="example"></a>Przykład  
  
```xml  
<configuration>  
<system.ServiceModel>  
<bindings>  
<wsDualHttpBinding>  
    <binding   
        closeTimeout="00:00:10"  
        openTimeout="00:00:20"   
        receiveTimeout="00:00:30"  
        sendTimeout="00:00:40"  
        bypassProxyOnLocal="false"   
        clientBaseAddress="http://localhost:8001/client/"  
        transactionFlow="true"   
        hostNameComparisonMode="WeakWildcard"  
        maxReceivedMessageSize="1000"  
        messageEncoding="Mtom"   
        proxyAddress="http://foo/bar"   
        textEncoding="utf-16"  
        useDefaultWebProxy="false">  
        <reliableSession ordered="false"  
            inactivityTimeout="00:02:00" />  
        <security mode="None">  
            <message clientCredentialType="None"  
                negotiateServiceCredential="false"  
                algorithmSuite="Aes128" />  
        </security>  
    </binding>  
</wsDualHttpBinding>  
</bindings>  
</system.ServiceModel>  
</configuration>  
```  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.WSDualHttpBinding>  
 <xref:System.ServiceModel.Configuration.WSDualHttpBindingElement>  
 [Powiązania](../../../../../docs/framework/wcf/bindings.md)  
 [Konfigurowanie powiązań dostarczanych przez system](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [Konfigurowanie usług Windows Communication Foundation i klientów za pomocą powiązań](http://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [\<Powiązanie >](../../../../../docs/framework/misc/binding.md)
