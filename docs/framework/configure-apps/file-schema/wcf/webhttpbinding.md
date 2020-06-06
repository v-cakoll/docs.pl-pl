---
title: <webHttpBinding>
ms.date: 03/30/2017
ms.assetid: 84179d77-825d-44b9-895a-ab08e7aa044d
ms.openlocfilehash: 0bb6d1f40fe38cb13ed8ab07957de5db22d48fcc
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "74140500"
---
# \<webHttpBinding>
Definiuje element powiązania, który jest używany do konfigurowania punktów końcowych dla usług sieci Web Windows Communication Foundation (WCF), które odpowiadają na żądania HTTP zamiast komunikatów protokołu SOAP.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<webHttpBinding>**  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<webHttpBinding>
  <binding allowCookies="Boolean"
           bypassProxyOnLocal="Boolean"
           closeTimeout="TimeSpan"
           hostNameComparisonMode="StrongWildCard/Exact/WeakWildcard"
           maxBufferPoolSize="integer"
           maxBufferSize="integer"
           maxReceivedMessageSize="Integer"
           name="string"
           openTimeout="TimeSpan"
           proxyAddress="URI"
           receiveTimeout="TimeSpan"
           sendTimeout="TimeSpan"
           transferMode="Buffered/Streamed/StreamedRequest/StreamedResponse"
           useDefaultWebProxy="Boolean"
           writeEncoding="UnicodeFffeTextEncoding/Utf16TextEncoding/Utf8TextEncoding">
    <security mode="None/Transport/TransportCredentialOnly">
      <transport clientCredentialType="Basic/Certificate/Digest/None/Ntlm/Windows"
                 proxyCredentialType="Basic/Digest/None/Ntlm/Windows"
                 realm="string" />
    </security>
    <readerQuotas maxArrayLength="Integer"
                  maxBytesPerRead="Integer"
                  maxDepth="Integer"
                  maxNameTableCharCount="Integer"
                  maxStringContentLength="Integer" />
  </binding>
</webHttpBinding>
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|allowCookies|Wartość logiczna wskazująca, czy klient akceptuje pliki cookie i propaguje je do przyszłych żądań. Wartością domyślną jest false.<br /><br /> Tej właściwości można użyć podczas współpracy z usługami sieci Web ASMX, które korzystają z plików cookie. W ten sposób można mieć pewność, że pliki cookie zwrócone z serwera są automatycznie kopiowane do wszystkich przyszłych żądań klientów dla tej usługi.|  
|bypassProxyOnLocal|Wartość logiczna wskazująca, czy pominąć serwer proxy dla adresów lokalnych. Wartość domyślna to `false`.|  
|closeTimeout|<xref:System.TimeSpan>Wartość określająca interwał czasu podanego do ukończenia operacji zamknięcia. Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero> . Wartość domyślna to 00:01:00.|  
|hostnameComparisonMode|Określa tryb porównania nazw hostów HTTP używany do analizowania identyfikatorów URI. Ten atrybut jest typu <xref:System.ServiceModel.HostNameComparisonMode> , który wskazuje, czy nazwa hosta jest używana do uzyskiwania dostępu do usługi podczas dopasowywania identyfikatora URI. Wartość domyślna to <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard> , co powoduje ignorowanie nazwy hosta w dopasowaniu.|  
|maxBufferPoolSize|Liczba całkowita określająca maksymalny rozmiar puli buforów dla tego powiązania. Wartość domyślna to 524 288 bajtów (512 * 1024). Wiele części Windows Communication Foundation (WCF) używa buforów. Tworzenie i niszczenie buforów za każdym razem, gdy są używane, jest kosztowne i wyrzucanie elementów bezużytecznych dla buforów jest również kosztowne. W przypadku pul buforów można pobrać bufor z puli, użyć go i zwrócić do puli po zakończeniu. W ten sposób nie ma konieczności narzutu na tworzenie i niszczenie buforów.|  
|maxBufferSize|Liczba całkowita określająca maksymalną ilość pamięci przydzieloną do użytku przez Menedżera buforów komunikatów, które odbierają komunikaty z kanału. Wartość domyślna to 524 288 (0x80000) b.|  
|maxReceivedMessageSize|Dodatnia liczba całkowita, która określa maksymalny rozmiar wiadomości (w bajtach), w tym nagłówki, które można odbierać w kanale skonfigurowanym dla tego powiązania. Nadawca wiadomości przekraczającej ten limit spowoduje zwrócenie błędu. Odbiorca odrzuca komunikat i tworzy wpis zdarzenia w dzienniku śledzenia. Wartość domyślna to 65536. **Uwaga:**  Zwiększenie tej samej wartości nie jest wystarczające w trybie zgodności ASP.NET. Należy również zwiększyć wartość `httpRuntime` (zobacz [element httpRuntime (schemat ustawień ASP.NET)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/e1f13641(v=vs.100))).|  
|name|Ciąg zawierający nazwę konfiguracji powiązania. Ta wartość powinna być unikatowa, ponieważ jest używana jako identyfikacja dla powiązania. Począwszy od .NET Framework 4, powiązania i zachowania nie muszą mieć nazwy. Aby uzyskać więcej informacji na temat konfiguracji domyślnej i powiązań pustego i zachowań, zobacz [Uproszczona konfiguracja](../../../wcf/simplified-configuration.md) i [Uproszczona konfiguracja dla usług WCF](../../../wcf/samples/simplified-configuration-for-wcf-services.md).|  
|openTimeout|<xref:System.TimeSpan>Wartość, która określa przedział czasu podanego na zakończenie operacji otwarcia. Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero> . Wartość domyślna to 00:01:00.|  
|proxyAddress|Identyfikator URI, który określa adres serwera proxy HTTP. Jeśli `useSystemWebProxy` jest `true` , to ustawienie musi być `null` . Wartość domyślna to `null`.|  
|receiveTimeout|Wartość określająca <xref:System.TimeSpan> interwał czasu podanego do ukończenia operacji odbioru. Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero> . Wartość domyślna to 00:01:00.|  
|Właściwości SendTimeout|<xref:System.TimeSpan>Wartość określająca interwał czasu podanego do ukończenia operacji wysyłania. Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero> . Wartość domyślna to 00:01:00.|  
|elementy TransferMode.|<xref:System.ServiceModel.TransferMode>Wartość wskazująca, czy Usługa skonfigurowana za pomocą powiązania korzysta z przenoszonych lub buforowanych trybów przesyłania komunikatów. Wartość domyślna to `Buffered`.|  
|useDefaultWebProxy|Wartość logiczna określająca, czy jest używany konfigurowany przez system serwer proxy HTTP. Wartość domyślna to `true`.|  
|writeEncoding|Określa kodowanie znaków, które jest używane dla tekstu komunikatu. Prawidłowe wartości to:<br /><br /> UnicodeFffeTextEncoding: kodowanie Unicode BigEndian.<br /><br /> Utf16TextEncoding: kodowanie 16-bitowe.<br /><br /> Utf8TextEncoding: kodowanie 8-bitowe.<br /><br /> Wartość domyślna to Utf8TextEncoding.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))|Definiuje ograniczenia złożoności komunikatów POX, które mogą być przetwarzane przez punkty końcowe skonfigurowane za pomocą tego powiązania. Ten element jest typu <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement> .|  
|[\<security>](security-of-webhttpbinding.md)|Definiuje ustawienia zabezpieczeń dla powiązania. Ten element jest typu <xref:System.ServiceModel.Configuration.WebHttpSecurityElement> .|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<bindings>](bindings.md)|Ten element zawiera kolekcję powiązań standardowych i niestandardowych.|  
  
## <a name="remarks"></a>Uwagi  
 Model programowania w sieci Web WCF umożliwia deweloperom udostępnianie usług sieci Web WCF za pośrednictwem żądań HTTP, które używają komunikatów o formacie "zwykły stary kod XML" (POX) zamiast komunikatów opartych na protokole SOAP. Aby klienci mogli komunikować się z usługą przy użyciu żądań HTTP, należy skonfigurować punkt końcowy usługi z [\<webHttpBinding>](webhttpbinding.md) \<WebHttpBehavior> dołączonym do niej elementem.  
  
 Obsługa funkcji WCF dla zespalania i ASP. Integracja AJAX jest oparta na modelu programowania sieci Web. Aby uzyskać więcej informacji na temat modelu, zobacz [model programowania HTTP sieci Web](../../../wcf/feature-details/wcf-web-http-programming-model.md)w programie WCF.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.WebHttpBinding>
- <xref:System.ServiceModel.Configuration.WebHttpBindingElement>
- [Model programowania protokołu HTTP sieci Web w programie WCF](../../../wcf/feature-details/wcf-web-http-programming-model.md)
- [Powiązania](../../../wcf/bindings.md)
- [Konfigurowanie powiązań dostarczanych przez system](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [Konfigurowanie usług i klientów za pomocą powiązań](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
