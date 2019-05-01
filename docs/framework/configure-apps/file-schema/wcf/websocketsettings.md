---
title: <webSocketSettings>
ms.date: 03/30/2017
ms.assetid: bbf97e02-8dd1-4922-acac-3cd33397b249
ms.openlocfilehash: 1101d021f3c7436c4f45a22a48e50f6d1553f753
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61769749"
---
# <a name="websocketsettings"></a>\<webSocketSettings>
Element konfiguracji, służy do określania ustawień gniazda sieci Web.  
  
\<system.ServiceModel>  
\<powiązania >  
\<netHttpBinding>  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<netHttpBinding>
  <binding>
    <webSocketSettings createNotificationOnConnection="Boolean"
                       disablePayloadMasking="Boolean"
                       keepAliveInterval="TimeSpan"
                       maxPendingConnections="Integer"
                       receiveBufferSize="Integer"
                       sendBufferSize="Integer"
                       subProtocol="String"
                       transportUsage="WhenDuplex/Always/Never" />
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
|keepAliveInterval|Określa interwał utrzymywania aktywności Zachowaj.|  
|maxPendingConnections|Określa maksymalną liczbę połączeń, oczekiwanie na wysłanie w usłudze.|  
|receiveBufferSize|Określa rozmiar buforów odbioru.|  
|sendBufferSize|Określa rozmiar buforu wysyłania.|  
|subProtocol|Określa podprotokół gniazda sieci Web.|  
|transportUsage|Określa, kiedy należy używać gniazda sieci Web.|  
  
## <a name="transportusage-attribute"></a>transportUsage atrybutu  
  
|Wartość|Opis|  
|-----------|-----------------|  
|WhenDuplex|Gdy kontrakt jest dupleksowy, należy użyć protokołu gniazda sieci Web.|  
|zawsze|Zawsze używaj protokołu gniazda sieci Web, niezależnie od tego kontraktu.|  
|nigdy nie|Nigdy nie używaj protokołu Websocket.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|\<netHttpBinding>|Określa elementu NetHttpBinding|  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak używać \<webSocketSettings > element.  
  
```xml  
<netHttpBinding>
  <binding>
    <webSocketSettings createNotificationOnConnection="true"
                       disablePayloadMasking="false"
                       keepAliveInterval="00:10:00"
                       maxPendingConnections="100"
                       receiveBufferSize="1000"
                       sendBufferSize="1000"
                       subProtocol="Soap"
                       transportUsage="WhenDuplex/Always/Never" />
  </binding>
</netHttpBinding>
```  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.Channels.Binding>
- <xref:System.ServiceModel.Channels.BindingElement>
- <xref:System.ServiceModel.BasicHttpBinding>
- <xref:System.ServiceModel.Configuration.BasicHttpBindingElement>
- [Powiązania](../../../../../docs/framework/wcf/bindings.md)
- [Konfigurowanie powiązań dostarczanych przez system](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)
- [Konfigurowanie usług i klientów za pomocą powiązań](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [\<Powiązanie >](../../../../../docs/framework/misc/binding.md)
