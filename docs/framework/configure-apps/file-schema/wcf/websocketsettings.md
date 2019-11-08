---
title: <webSocketSettings>
ms.date: 03/30/2017
ms.assetid: bbf97e02-8dd1-4922-acac-3cd33397b249
ms.openlocfilehash: fa87a1b0961425d6a9bc84769bef6e87cbc2ce96
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/07/2019
ms.locfileid: "73732552"
---
# <a name="websocketsettings"></a>\<webSocketSettings >
Element konfiguracji służący do określania ustawień gniazda sieci Web.  
  
[ **\<configuration >** ](../configuration-element.md) \
&nbsp; &nbsp;[ **\<system. serviceModel >** ](system-servicemodel.md) \
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<powiązań**](bindings.md) >\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<protokół HttpBinding**](nethttpbinding.md) >\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<powiązania >** \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<webSocketSettings >**  
  
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
|disablePayloadMasking|Określa, czy maskowanie gniazda sieci Web jest wyłączone.|  
|keepAliveInterval|Określa interwał utrzymywania aktywności.|  
|maxPendingConnections|Określa maksymalną liczbę połączeń oczekujących na wysłanie usługi.|  
|receiveBufferSize|Określa rozmiar buforu odbioru.|  
|sendBufferSize|Określa rozmiar buforu wysyłania.|  
|Podprotokół|Określa podprotokół gniazda sieci Web.|  
|transportUsage|Określa, kiedy należy używać gniazd sieci Web.|  
  
## <a name="transportusage-attribute"></a>transportUsage — atrybut  
  
|Wartość|Opis|  
|-----------|-----------------|  
|WhenDuplex|Użyj protokołu gniazda sieci Web, gdy kontrakt jest w trybie dupleksu.|  
|stałego|Zawsze używaj protokołu gniazda internetowego niezależnie od kontraktu.|  
|Ustawione|Nigdy nie używaj protokołu gniazda sieci Web.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|\<> protokołu HttpBinding|Określa protokół HttpBinding|  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak używać elementu \<webSocketSettings >.  
  
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
- [Powiązania](../../../wcf/bindings.md)
- [Konfigurowanie powiązań dostarczanych przez system](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [Konfigurowanie usług i klientów za pomocą powiązań](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [> powiązań \<](bindings.md)
