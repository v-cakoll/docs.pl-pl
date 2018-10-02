---
title: Współdziałanie z aplikacjami POX
ms.date: 03/30/2017
ms.assetid: 449276b8-4633-46f0-85c9-81f01d127636
ms.openlocfilehash: b7fdb4e16bce52025515ced065d0f48cffb7fa3f
ms.sourcegitcommit: ea00c05e0995dae928d48ead99ddab6296097b4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/02/2018
ms.locfileid: "48035035"
---
# <a name="interoperability-with-pox-applications"></a>Współdziałanie z aplikacjami POX

"Zwykłe stare XML" aplikacji (POX) komunikują się przez wymianę nieprzetworzone komunikaty HTTP, które zawierają tylko dane aplikacji XML, który nie jest ujęty w kopercie SOAP. Windows Communication Foundation (WCF) może zapewnić zarówno w przypadku usług, jak i klientów, którzy używają POX wiadomości. W usłudze WCF może służyć do implementowania usług, które uwidaczniają punkty końcowe do klientów, takich jak przeglądarki sieci Web i języków skryptów, które wysyłania i odbierania komunikatów POX. Na komputerze klienckim model programowania WCF może służyć do wdrożenia klientów komunikujących się za pomocą usług opartych na POX.  
  
> [!NOTE]
> W tym dokumencie pierwotnie został napisany dla [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 3.0.  [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 3.5 ma wbudowaną obsługę pracy z aplikacjami POX. Aby uzyskać więcej informacji na temat, zobacz [modelu programowania protokołu HTTP sieci Web programu WCF](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md).
  
## <a name="pox-programming-with-wcf"></a>POX programowania przy użyciu programu WCF

Usługi WCF, które komunikują się za pośrednictwem protokołu HTTP przy użyciu wiadomości POX [ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md).

```xml
<customBinding>
   <binding name="poxServerBinding">
       <textMessageEncoding messageVersion="None" />
       <httpTransport />
   </binding>
</customBinding>
```

To niestandardowe powiązanie zawiera dwa elementy:

- [\<httpTransport >](../../../../docs/framework/configure-apps/file-schema/wcf/httptransport.md)

- [\<textMessageEncoding >](../../../../docs/framework/configure-apps/file-schema/wcf/textmessageencoding.md)

Standardowa koder komunikatu tekstowego WCF specjalnie jest skonfigurowany do używania <xref:System.ServiceModel.Channels.MessageVersion.None%2A> wartość, która pozwala na przetwarzanie XML komunikat ładunków pojawiające się nie opakowane w kopercie SOAP.

Klienci WCF, które komunikują się za pośrednictwem protokołu HTTP przy użyciu komunikatów o POX użyć podobnych powiązania (pokazano w poniższym kodzie imperatywne).

```csharp
private static Binding CreatePoxBinding()
{
    TextMessageEncodingBindingElement encoder =
        new TextMessageEncodingBindingElement( MessageVersion.None, Encoding.UTF8 );
    HttpTransportBindingElement transport = new HttpTransportBindingElement();
    transport.ManualAddressing = true;
    return new CustomBinding( new BindingElement[] { encoder, transport } );
}
```

Ponieważ klienci POX należy jawnie określić identyfikatory URI, do którego wysyłają komunikaty, są zazwyczaj należy skonfigurować <xref:System.ServiceModel.Channels.HttpTransportBindingElement> trybu ręcznego adresowania, ustawiając <xref:System.ServiceModel.Channels.TransportBindingElement.ManualAddressing%2A> właściwości `true` w elemencie. Dzięki temu wiadomości należy się zająć jawnie przez kod aplikacji i nie jest konieczne utworzyć nowy <xref:System.ServiceModel.ChannelFactory> za każdym razem, gdy aplikacja wysyła komunikat do inny identyfikator URI protokołu HTTP.

Ponieważ w celu przekazania informacji o protokole ważne wiadomości POX nie używają nagłówków protokołu SOAP, POX klientów i usług w często muszą manipulować rodzajów podstawowego żądania HTTP używany do wysyłania i odbierania wiadomości. Informacje protokołu specyficzne dla protokołu HTTP, takie jak nagłówki HTTP i kodów stanu są udostępniane w modelu programowania usług WCF za pomocą dwóch klas:

- <xref:System.ServiceModel.Channels.HttpRequestMessageProperty>, który zawiera informacje o żądaniu HTTP, takich jak nagłówki metodę i żądania HTTP.

- <xref:System.ServiceModel.Channels.HttpResponseMessageProperty>, który zawiera informacje o odpowiedzi HTTP, takich jak opis kodu i stan stanu HTTP, a także wszystkie nagłówki odpowiedzi HTTP.
  
Poniższy przykład kodu pokazuje sposób tworzenia komunikatu żądania HTTP GET, które są skierowane do `http://localhost:8100/customers`.

```csharp
Message request = Message.CreateMessage( MessageVersion.None, String.Empty );
request.Headers.To = "http://localhost:8100/customers";

HttpRequestMessageProperty property = new HttpRequestMessageProperty();
property.Method = "GET";
property.SuppressEntityBody = true;
request.Properties.Add( HttpRequestMessageProperty.Name, property );
```

Po pierwsze, puste żądanie <xref:System.ServiceModel.Channels.Message> jest tworzony przez wywołanie <xref:System.ServiceModel.Channels.Message.CreateMessage%28System.ServiceModel.Channels.MessageVersion%2CSystem.String%29>. <xref:System.ServiceModel.Channels.MessageVersion.None%2A> Parametr jest używany do wskazania, że koperty protokołu SOAP nie jest wymagany i <xref:System.String.Empty> parametr jest przekazywany jako akcję. Komunikat żądania jest następnie rozwiązane przez ustawienie <xref:System.ServiceModel.Channels.MessageHeaders.To%2A> nagłówka do żądanego identyfikatora URI. Następnie <xref:System.ServiceModel.Channels.HttpRequestMessageProperty> jest tworzony i <xref:System.ServiceModel.Channels.HttpRequestMessageProperty.Method%2A> jest ustawiona na zlecenie HTTP metody GET i <xref:System.ServiceModel.Channels.HttpRequestMessageProperty.SuppressEntityBody%2A> jest ustawiona na `true` do wskazania, że żadne dane nie powinny być wysyłane w treści wychodzący komunikat żądania HTTP. Na koniec właściwości żądania zostanie dodany do <xref:System.ServiceModel.Channels.Message.Properties%2A> zbiór komunikat żądania, aby go mogą mieć wpływ na sposób transportu HTTP wysyła żądanie. Komunikat jest gotowy do wysłania przez odpowiednie wystąpienie <xref:System.ServiceModel.Channels.IRequestChannel>.

Podobne techniki może służyć w usłudze można wyodrębnić <xref:System.ServiceModel.Channels.HttpRequestMessageProperty> z przychodzących wiadomości i konstrukcji odpowiedzi.
