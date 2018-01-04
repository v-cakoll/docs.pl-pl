---
title: "Współdziałanie z aplikacjami POX"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 449276b8-4633-46f0-85c9-81f01d127636
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8cb7e209397e593ae1fd81c2bc2552e54a32adf0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="interoperability-with-pox-applications"></a>Współdziałanie z aplikacjami POX
"Zwykły starego XML" (POX) aplikacji komunikacji przez wymianę raw komunikaty HTTP, które zawierają tylko dane aplikacji XML, który nie jest umieszczone wewnątrz koperty protokołu SOAP. [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]może zapewnić zarówno usług i klientów, którzy używają POX wiadomości. W usłudze [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] może służyć do wdrożenia usług, które udostępniają punktów końcowych do klientów, takich jak przeglądarki sieci Web i języki skryptów, które wysyłania i odbierania wiadomości POX. Na komputerze klienckim [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] model programowania może służyć do wdrożenia klientów, które komunikują się z usługami opartymi na POX.  
  
> [!NOTE]
>  Ten dokument został pierwotnie napisane dla [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 3.0.  [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]3.5 ma wbudowaną obsługę pracy z aplikacjami POX. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]zobacz [modelu programowania protokołu HTTP sieci Web WCF](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)  
  
## <a name="pox-programming-with-wcf"></a>POX programowania przy użyciu programu WCF  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]usługi, które komunikują się za pośrednictwem protokołu HTTP przy użyciu wiadomości POX [ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md).  
  
```xml  
<customBinding>  
   <binding name="poxServerBinding">  
       <textMessageEncoding messageVersion="None" />  
       <httpTransport />  
   </binding>  
</customBinding>  
```  
  
 To niestandardowe powiązanie zawiera dwa elementy:  
  
-   [ \<HttpTransport >](../../../../docs/framework/configure-apps/file-schema/wcf/httptransport.md) i  
  
-   [ \<TextMessageEncoding >](../../../../docs/framework/configure-apps/file-schema/wcf/textmessageencoding.md).  
  
 Standardowe [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] kodera wiadomości tekstowych specjalnie jest skonfigurowana do używania <xref:System.ServiceModel.Channels.MessageVersion.None%2A> wartość, która pozwala na przetwarzanie XML wiadomości ładunków nie przychodzące otoczona koperty protokołu SOAP.  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]klientów, które komunikują się za pośrednictwem protokołu HTTP przy użyciu wiadomości POX Użyj podobne wiązanie (pokazano w poniższym kodzie konieczne).  
  
```  
private static Binding CreatePoxBinding()  
{  
    TextMessageEncodingBindingElement encoder =   
    new TextMessageEncodingBindingElement( MessageVersion.None, Encoding.UTF8 );  
    HttpTransportBindingElement transport = new HttpTransportBindingElement();  
    transport.ManualAddressing = true;  
    return new CustomBinding( new BindingElement[] { encoder, transport } );  
}   
```  
  
 Ponieważ POX klientów należy jawnie określić identyfikatory URI, do którego wysyłania wiadomości, one zazwyczaj należy skonfigurować <xref:System.ServiceModel.Channels.HttpTransportBindingElement> na ręczny tryb adresowania przez ustawienie <xref:System.ServiceModel.Channels.TransportBindingElement.ManualAddressing%2A> właściwości `true` w elemencie. Dzięki temu wiadomości mogą być adresowane jawnie przez kod aplikacji i nie jest konieczne utworzyć nową <xref:System.ServiceModel.ChannelFactory> za każdym razem, gdy aplikacja wysyła komunikat do inny identyfikator URI protokołu HTTP.  
  
 Ponieważ POX wiadomości nie należy używać nagłówków SOAP w celu przedstawienia informacji o protokole ważne, POX klientów i usług często muszą manipulować części realizacji źródłowego żądania HTTP, które są używane do wysyłania i odbierania wiadomości. Informacje protokołu specyficzne dla protokołu HTTP, takie jak nagłówków HTTP i kodów stanu są udostępniane w [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] model programowania za pomocą dwóch klas:  
  
-   <xref:System.ServiceModel.Channels.HttpRequestMessageProperty>, który zawiera informacje o żądaniu HTTP, takich jak nagłówki metoda i żądania HTTP.  
  
-   <xref:System.ServiceModel.Channels.HttpResponseMessageProperty>, który zawiera informacje o odpowiedzi HTTP, takie jak stan HTTP opis kodu i stan, a także żadnych nagłówków odpowiedzi HTTP.  
  
 Poniższy przykładowy kod przedstawia sposób tworzenia HTTP GET komunikat żądania opisanej http://localhost:8100/klientom.  
  
```  
Message request = Message.CreateMessage( MessageVersion.None, String.Empty );  
request.Headers.To = "http://localhost:8100/customers";  
  
HttpRequestMessageProperty property = new HttpRequestMessageProperty();  
property.Method = "GET";  
property.SuppressEntityBody = true;  
request.Properties.Add( HttpRequestMessageProperty.Name, property );  
```  
  
 Po pierwsze, puste żądanie <xref:System.ServiceModel.Channels.Message> jest tworzony przez wywołanie metody <xref:System.ServiceModel.Channels.Message.CreateMessage%28System.ServiceModel.Channels.MessageVersion%2CSystem.String%29>. <xref:System.ServiceModel.Channels.MessageVersion.None%2A> Parametr jest używany, aby wskazać, że koperty protokołu SOAP nie jest wymagany i <xref:System.String.Empty> parametr jest przekazywany jako działania. Komunikat żądania jest następnie adresowane przez ustawienie <xref:System.ServiceModel.Channels.MessageHeaders.To%2A> nagłówka do żądanego identyfikatora URI. Następnie <xref:System.ServiceModel.Channels.HttpRequestMessageProperty> jest tworzony i <xref:System.ServiceModel.Channels.HttpRequestMessageProperty.Method%2A> ustawiono zlecenie HTTP GET, metoda i <xref:System.ServiceModel.Channels.HttpRequestMessageProperty.SuppressEntityBody%2A> ma ustawioną wartość `true` wskazująca, że żadne dane mają być wysyłane w treści komunikatu wychodzącego żądania HTTP. Na koniec właściwości żądania jest dodawany do <xref:System.ServiceModel.Channels.Message.Properties%2A> kolekcji, więc ona mieć wpływ jak transportu HTTP wysyła żądanie komunikatu żądania. Komunikat jest gotowa do wysłania przez odpowiednie wystąpienie <xref:System.ServiceModel.Channels.IRequestChannel>.  
  
 Podobne techniki umożliwiają w usłudze wyodrębnić <xref:System.ServiceModel.Channels.HttpRequestMessageProperty> z komunikatu przychodzącego i konstrukcja odpowiedzi.
