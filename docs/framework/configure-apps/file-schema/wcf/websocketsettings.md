---
title: '&lt;webSocketSettings&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bbf97e02-8dd1-4922-acac-3cd33397b249
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7ee0f555fc1e3412032e0a7dda3a747bbfef6f4d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ltwebsocketsettingsgt"></a>&lt;webSocketSettings&gt;
Element konfiguracji, służy do określania ustawień gniazda sieci Web.  
  
\<System. ServiceModel >  
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
|Podprotokół|Określa podprotokołu gniazda sieci Web.|  
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
 [Konfigurowanie usług Windows Communication Foundation i klientów za pomocą powiązań](http://msdn.microsoft.com/en-us/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [\<Powiązanie >](../../../../../docs/framework/misc/binding.md)
