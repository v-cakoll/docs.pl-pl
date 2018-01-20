---
title: '&lt;webHttpBinding&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 84179d77-825d-44b9-895a-ab08e7aa044d
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0eb39fe234664b5ef5ffb604090191db14e8d751
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2018
---
# <a name="ltwebhttpbindinggt"></a>&lt;webHttpBinding&gt;
Definiuje element powiązania, który jest używany do konfigurowania punktów końcowych dla [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] tego odpowiada na żądania HTTP zamiast na wiadomości SOAP usług sieci Web.  
  
\<system.ServiceModel>  
\<powiązania >  
\<webHttpBinding>  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<webHttpBinding>  
  <binding   
    allowCookies="Boolean"  
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
 W poniższych sekcjach opisano atrybuty i elementy podrzędne, elementy nadrzędne  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|allowCookies|Wartość logiczna wskazująca, czy klient akceptuje pliki cookie i propaguje je do przyszłych żądań. Wartością domyślną jest false.<br /><br /> Tej właściwości można użyć w przypadku interakcji z usługami sieci Web ASMX, które używają plików cookie. W ten sposób można się upewnić, że pliki cookie zwrócony z serwera, automatycznie są kopiowane do wszystkich przyszłych żądań dla tej usługi.|  
|bypassProxyOnLocal|Wartość logiczna, która wskazuje, czy pominąć serwer proxy dla adresów lokalnych. Wartość domyślna to `false`.|  
|closeTimeout|A <xref:System.TimeSpan> wartość, która określa interwał przeznaczony na zakończenie operacji zamknięcia. Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>. Wartość domyślna to 00:01:00.|  
|hostnameComparisonMode|Określa tryb porównania nazw hostów HTTP używany do przeprowadzenia analizy identyfikatorów URI. Ten atrybut jest typu <xref:System.ServiceModel.HostNameComparisonMode>, która wskazuje, czy nazwa hosta jest używana w celu dotarcia do usługi podczas dopasowywania identyfikatora URI. Wartość domyślna to <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, który ignoruje nazwy hosta w dopasowania.|  
|maxBufferPoolSize|Liczba całkowita określająca maksymalny rozmiar puli buforów dla tego powiązania. Wartość domyślna to 524,288 bajtów (512 * 1024). Bufory za pomocą wielu części programu Windows Communication Foundation (WCF). Tworzenie i niszczenie buforów za każdym razem, gdy są one używane jest kosztowne i odzyskiwanie pamięci dla buforów również jest kosztowna. Używając puli buforów można podjąć buforu z puli, ten jest używany i zwracać do puli, gdy wszystko będzie gotowe. W związku z tym jest unikać obciążenie związane z tworzeniem i niszczenie buforów.|  
|wartość maxBufferSize|Liczba całkowita, która określa maksymalną ilość pamięci przydzielonej do użycia przez menedżera buforów komunikatów, który odbiera komunikaty z kanału. Wartość domyślna to 524,288 (0x80000) bajtów.|  
|maxReceivedMessageSize|Dodatnia liczba całkowita, która określa maksymalny rozmiar wiadomości, w bajtach, włącznie z nagłówkami, odebranych z kanału skonfigurowane dla tego wiązania. Nadawcy wiadomości przekracza ten limit, zostanie wyświetlony błąd. Odbiornik porzuca wiadomości i tworzy wpis zdarzenia w dzienniku śledzenia. Wartość domyślna to 65536. **Uwaga:** zwiększenie tej samej wartości nie są wystarczające w zgodnym trybie ASP.NET. Należy również zwiększyć wartość `httpRuntime` (zobacz [httpRuntime — Element (schemat ustawień programu ASP.NET)](http://msdn.microsoft.com/library/e9b81350-8aaf-47cc-9843-5f7d0c59f369)).|  
|nazwa|Ciąg zawierający nazwę konfiguracji powiązania. Wartość ta powinna być unikatowa, ponieważ jest używany jako identyfikator dla tego powiązania. Począwszy od [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], powiązania i zachowania nie muszą mieć nazwę. Aby uzyskać więcej informacji o konfiguracji domyślnej i bez powiązania i zachowania, zobacz [uproszczony konfiguracji](../../../../../docs/framework/wcf/simplified-configuration.md) i [uproszczona konfiguracja usług WCF](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).|  
|openTimeout|A <xref:System.TimeSpan> wartość, która określa interwał przeznaczony na zakończenie operacji otwarcia. Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>. Wartość domyślna to 00:01:00.|  
|proxyAddress|Identyfikator URI, który określa adres serwera proxy HTTP. Jeśli `useSystemWebProxy` jest `true`, to ustawienie musi być `null`. Wartość domyślna to `null`.|  
|receiveTimeout|A <xref:System.TimeSpan> wartość, która określa interwał przeznaczony na zakończenie operacji odbioru. Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>. Wartość domyślna to 00:01:00.|  
|sendTimeout|A <xref:System.TimeSpan> wartość, która określa interwał przeznaczony na zakończenie operacji wysyłania. Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>. Wartość domyślna to 00:01:00.|  
|Tryb transferu.|A <xref:System.ServiceModel.TransferMode> wartość, która wskazuje, czy Usługa skonfigurowana dla tego wiązania używa trybu strumieniowego, czy buforowanego (lub obie) tryby transferu komunikatów. Wartość domyślna to `Buffered`.|  
|useDefaultWebProxy|Wartość logiczna określająca, czy jest używany serwer proxy HTTP systemu skonfigurowany automatycznie. Wartość domyślna to `true`.|  
|writeEncoding|Określa, że kodowania znaków, która jest używana dla treści wiadomości. Prawidłowe wartości są następujące:<br /><br /> UnicodeFffeTextEncoding: Unicode BigEndian kodowanie.<br /><br /> Utf16TextEncoding: 16-bitowego kodowania.<br /><br /> Utf8TextEncoding: 8-bitowego kodowania.<br /><br /> Wartość domyślna to Utf8TextEncoding.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<readerQuotas>](http://msdn.microsoft.com/library/3e5e42ff-cef8-478f-bf14-034449239bfd)|Definiuje ograniczenia złożoności wiadomości POX, które mogą być przetwarzane przez punkty końcowe skonfigurowane dla tego wiązania. Ten element jest typu <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.|  
|[\<security>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-webhttpbinding.md)|Definiuje ustawienia zabezpieczeń dla powiązania. Ten element jest typu <xref:System.ServiceModel.Configuration.WebHttpSecurityElement>.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<powiązania >](../../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)|Ten element przetrzymuje kolekcję powiązań standardowych i niestandardowych.|  
  
## <a name="remarks"></a>Uwagi  
 [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] Modelu programowania sieci Web umożliwia deweloperom ujawnia [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] sieci Web usług za pomocą żądania HTTP, które używają "zwykły starego XML" styl (POX) zamiast opartego na protokole SOAP komunikatów do obsługi komunikatów. Aby klienci mogli komunikować się z usługą za pomocą żądania HTTP, punkt końcowy usługi musi być skonfigurowany z [ \<webHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md) mający \<WebHttpBehavior > dołączone do niego.  
  
 Obsługa w [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] zespolonego i ASP. Zarówno integracji AJAX jest oparty na modelu programowania sieci Web. Aby uzyskać więcej informacji o modelu, zobacz [modelu programowania protokołu HTTP sieci Web WCF](../../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.WebHttpBinding>  
 <xref:System.ServiceModel.Configuration.WebHttpBindingElement>  
 [Model programowania protokołu HTTP sieci Web w programie WCF](../../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)  
 [Powiązania](../../../../../docs/framework/wcf/bindings.md)  
 [Konfigurowanie powiązań dostarczanych przez system](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [Konfigurowanie usług Windows Communication Foundation i klientów za pomocą powiązań](http://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [\<Powiązanie >](../../../../../docs/framework/misc/binding.md)
