---
title: '&lt;webSocketSettings&gt;'
ms.date: 03/30/2017
ms.assetid: bbf97e02-8dd1-4922-acac-3cd33397b249
ms.openlocfilehash: 84aee31b6c15beb32732f89eae7c3d176f57971d
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32754840"
---
# <a name="ltwebsocketsettingsgt"></a>&lt;webSocketSettings&gt;
Element konfiguracji, służy do określania ustawień gniazda sieci Web.  
  
\<system.ServiceModel>  
\<powiązania >  
\<netHttpBinding >  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<netHttpBinding>  
  <binding>   
    <webSocketSettings createNotificationOnConnection="boolean" 
                       disablePayloadMasking="boolean" 
                       keepAliveInterval="TimeSpan" 
                       maxPendingConnections="Integer" 
                       receiveBufferSize="Integer" 
                       sendBufferSize="Integer" 
                       subProtocol="String" 
                       transportUsage="WhenDuplex/Always/Never"/>
  </binding>  
</netHttpBinding>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|createNotificationOnConnection|Określa, czy powiadomienie jest wysyłane po nawiązaniu połączenia.|  
|disablePayloadMasking|Określa, czy maskowania gniazda sieci Web jest wyłączona.|  
|keepAliveInterval|Określa interwał keep alive.|  
|maxPendingConnections|Określa maksymalną liczbę połączeń oczekujących na wysyłania w usłudze.|  
|receiveBufferSize|Określa rozmiar buforu odbioru.|  
|sendBufferSize|Określa rozmiar buforów wysyłania.|  
|subProtocol|Określa podprotokołu gniazda sieci Web.|  
|transportUsage|Określa, kiedy należy używać gniazda sieci Web.|  
  
## <a name="transportusage-attribute"></a>transportUsage atrybutu  
  
|Wartość|Opis|  
|-----------|-----------------|  
|WhenDuplex|Gdy kontrakt jest dupleksowy, należy użyć protokołu gniazda sieci Web.|  
|Zawsze|Zawsze używaj protokołu gniazda sieci Web, niezależnie od tego kontraktu.|  
|Nigdy nie|Nigdy nie używaj protokołu gniazda sieci Web.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|\<netHttpBinding >|Określa elementu NetHttpBinding|  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia użycie \<webSocketSettings > elementu.  
  
```xml  
<netHttpBinding>  
        <binding>  
          <webSocketSettings createNotificationOnConnection="true"  
                              disablePayloadMasking="false  
                              keepAliveInterval="00:10:00"  
                              maxPendingConnections="100"  
                              receiveBufferSize="1000"  
                              sendBufferSize="1000"  
                              subProtocol="Soap"  
                              transportUsage="WhenDuplex/Always/Never"/>  
  
        </binding>  
      </netHttpBinding>  
```  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.Channels.Binding>  
 <xref:System.ServiceModel.Channels.BindingElement>  
 <xref:System.ServiceModel.BasicHttpBinding>  
 <xref:System.ServiceModel.Configuration.BasicHttpBindingElement>  
 [Powiązania](../../../../../docs/framework/wcf/bindings.md)  
 [Konfigurowanie powiązań dostarczanych przez system](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [Konfigurowanie usług Windows Communication Foundation i klientów za pomocą powiązań](http://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [\<Powiązanie >](../../../../../docs/framework/misc/binding.md)
