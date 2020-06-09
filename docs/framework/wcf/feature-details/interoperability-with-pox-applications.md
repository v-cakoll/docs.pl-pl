---
title: Współdziałanie z aplikacjami POX
ms.date: 03/30/2017
ms.assetid: 449276b8-4633-46f0-85c9-81f01d127636
ms.openlocfilehash: 64a6d850a32b14bc60cd43466e04b53a7a39be81
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84579270"
---
# <a name="interoperability-with-pox-applications"></a>Współdziałanie z aplikacjami POX

"Zwykłe stare aplikacje XML" (POX) komunikują się przez wymianę nieprzetworzonych komunikatów HTTP, które zawierają tylko dane aplikacji XML, które nie są ujęte w kopercie protokołu SOAP. Windows Communication Foundation (WCF) może zapewnić zarówno usługi, jak i klientów korzystających z komunikatów POX. Usługa WCF może służyć do implementowania usług, które ujawniają punkty końcowe klientom, takim jak przeglądarki sieci Web i języki skryptów, które wysyłają i odbierają wiadomości POX. Na kliencie model programowania WCF może służyć do implementowania klientów komunikujących się z usługami opartymi na POX.  
  
> [!NOTE]
> Ten dokument został pierwotnie zapisany dla .NET Framework 3,0.  .NET Framework 3,5 ma wbudowaną obsługę pracy z aplikacjami POX. Aby uzyskać więcej informacji, zobacz [model programowania HTTP sieci Web](wcf-web-http-programming-model.md)w programie WCF.
  
## <a name="pox-programming-with-wcf"></a>Programowanie POX przy użyciu programu WCF

Usługi WCF, które komunikują się za pośrednictwem protokołu HTTP przy użyciu komunikatów POX używają usługi [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md) .

```xml
<customBinding>
   <binding name="poxServerBinding">
       <textMessageEncoding messageVersion="None" />
       <httpTransport />
   </binding>
</customBinding>
```

To powiązanie niestandardowe zawiera dwa elementy:

- [\<httpTransport>](../../configure-apps/file-schema/wcf/httptransport.md)

- [\<textMessageEncoding>](../../configure-apps/file-schema/wcf/textmessageencoding.md)

Standardowy koder wiadomości tekstowych WCF jest specjalnie skonfigurowany do korzystania z <xref:System.ServiceModel.Channels.MessageVersion.None%2A> wartości, co pozwala na przetwarzanie ładunków komunikatów XML, które nie są umieszczane w kopercie protokołu SOAP.

Klienci programu WCF komunikują się za pośrednictwem protokołu HTTP przy użyciu komunikatów POX używają podobnego powiązania (pokazanego w poniższym kodzie).

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

Ponieważ klienci POX muszą jawnie określić identyfikatory URI, do których są wysyłane wiadomości, zazwyczaj muszą skonfigurować <xref:System.ServiceModel.Channels.HttpTransportBindingElement> do trybu ręcznego adresowania, ustawiając właściwość na <xref:System.ServiceModel.Channels.TransportBindingElement.ManualAddressing%2A> `true` na element. Dzięki temu komunikaty mają być jawnie rozkierowane przez kod aplikacji i nie trzeba tworzyć nowych za <xref:System.ServiceModel.ChannelFactory> każdym razem, gdy aplikacja wysyła komunikat do innego identyfikatora URI protokołu HTTP.

Ponieważ komunikaty POX nie używają nagłówków protokołu SOAP do przekazywania ważnych informacji o protokole, POX klienci i usługi często muszą manipulować fragmentami podstawowego żądania HTTP, które są używane do wysyłania lub odbierania wiadomości. Informacje o protokole protokołu HTTP, takie jak nagłówki HTTP i kody stanu, są rozmieszczone w modelu programowania WCF przez dwie klasy:

- <xref:System.ServiceModel.Channels.HttpRequestMessageProperty>, który zawiera informacje na temat żądania HTTP, takie jak metoda HTTP i nagłówki żądania.

- <xref:System.ServiceModel.Channels.HttpResponseMessageProperty>, który zawiera informacje o odpowiedzi HTTP, takie jak kod stanu HTTP i opis stanu, a także wszystkie nagłówki odpowiedzi HTTP.
  
Poniższy przykład kodu pokazuje, jak utworzyć komunikat żądania HTTP GET, który jest rozkierowany `http://localhost:8100/customers` .

```csharp
Message request = Message.CreateMessage( MessageVersion.None, String.Empty );
request.Headers.To = "http://localhost:8100/customers";

HttpRequestMessageProperty property = new HttpRequestMessageProperty();
property.Method = "GET";
property.SuppressEntityBody = true;
request.Properties.Add( HttpRequestMessageProperty.Name, property );
```

Najpierw jest tworzone puste żądanie <xref:System.ServiceModel.Channels.Message> przez wywołanie <xref:System.ServiceModel.Channels.Message.CreateMessage%28System.ServiceModel.Channels.MessageVersion%2CSystem.String%29> . <xref:System.ServiceModel.Channels.MessageVersion.None%2A>Parametr jest używany do wskazania, że koperta protokołu SOAP nie jest wymagana, a <xref:System.String.Empty> parametr jest przenoszona jako akcja. Następnie komunikat żądania jest rozkierowany przez ustawienie <xref:System.ServiceModel.Channels.MessageHeaders.To%2A> nagłówka do żądanego identyfikatora URI. Następnie <xref:System.ServiceModel.Channels.HttpRequestMessageProperty> jest tworzony i <xref:System.ServiceModel.Channels.HttpRequestMessageProperty.Method%2A> ma ustawioną metodę get zlecenia HTTP i <xref:System.ServiceModel.Channels.HttpRequestMessageProperty.SuppressEntityBody%2A> jest ustawiony na wartość, aby `true` wskazać, że żadne dane nie powinny być wysyłane w treści komunikatu żądania wychodzącego http. Na koniec Właściwość żądania jest dodawana do <xref:System.ServiceModel.Channels.Message.Properties%2A> kolekcji komunikatów żądania, co może mieć wpływ na sposób wysyłania żądania przez transport HTTP. Wiadomość jest następnie gotowa do wysłania w odpowiednim wystąpieniu <xref:System.ServiceModel.Channels.IRequestChannel> .

Podobne techniki mogą być używane w usłudze w celu wyodrębnienia <xref:System.ServiceModel.Channels.HttpRequestMessageProperty> z komunikatu przychodzącego i skonstruowania odpowiedzi.
