---
title: 'Transport: UDP'
ms.date: 03/30/2017
ms.assetid: 738705de-ad3e-40e0-b363-90305bddb140
ms.openlocfilehash: 12981e970706c5fc1d954c237309f12c85320c75
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64617372"
---
# <a name="transport-udp"></a>Transport: UDP
Przykładowe transportu UDP demonstruje sposób implementacji UDP emisji pojedynczej i multiemisji jako niestandardowy transportu Windows Communication Foundation (WCF). Przykład w tym artykule opisano zalecane procedury tworzenia niestandardowych transportu programu WCF, za pomocą struktura kanału i zgodnie z najlepszymi rozwiązaniami WCF. Kroki umożliwiające utworzenie niestandardowego transportu są następujące:  
  
1. Zdecyduj, które kanał [wiadomości programu Exchange wzorców](#MessageExchangePatterns) (IOutputChannel, IInputChannel, IDuplexChannel, IRequestChannel lub IReplyChannel) będzie obsługiwać Twoja elementu ChannelFactory i ChannelListener. Następnie zdecyduj, czy będzie obsługiwać sesji odchylenia tych interfejsów.  
  
2. Tworzenie fabryki kanałów i odbiornik, który obsługuje usługi wymiany komunikatów.  
  
3. Upewnij się, że wszystkie wyjątki dotyczące sieci są znormalizowane zgodnie z odpowiedniej klasy pochodnej z <xref:System.ServiceModel.CommunicationException>.  
  
4. Dodaj [ \<powiązania >](../../../../docs/framework/misc/binding.md) element, który dodaje niestandardowy transportu do stosu kanału. Aby uzyskać więcej informacji, zobacz [Dodawanie elementu powiązania](#AddingABindingElement).  
  
5. Dodaj sekcję rozszerzenia elementu powiązania do udostępnienia nowego elementu powiązania do konfiguracji systemu.  
  
6. Dodaj rozszerzenia metadanych do komunikowania się funkcji innych punktów końcowych.  
  
7. Dodaj powiązanie, które są wstępnie konfiguruje stosie elementów wiązania zgodnie z profilem dobrze zdefiniowane. Aby uzyskać więcej informacji, zobacz [dodając powiązanie standardowe](#AddingAStandardBinding).  
  
8. Dodaj sekcję wiązania i element konfiguracji powiązania aby uwidocznić powiązania do systemu konfiguracji. Aby uzyskać więcej informacji, zobacz [dodanie obsługi konfiguracji](#AddingConfigurationSupport).  
  
<a name="MessageExchangePatterns"></a>   
## <a name="message-exchange-patterns"></a>Wzorce wymiany komunikatów  
 Pierwszym krokiem Pisanie niestandardowych transportu jest podjęcie decyzji, które wzorców wymiany komunikatów (MEPs) są wymagane dla transportu. Istnieją trzy MEPs do wyboru:  
  
- Datagramów (IInputChannel/IOutputChannel)  
  
     Korzystając z datagram MEP, klient wysyła komunikat "fire and forget" program exchange jest używany. Element zostanie wyzwolony i zapomnij programu exchange to taki, który wymaga potwierdzenia out-of-band skutecznej. Komunikat może zostać utracone podczas przesyłania i nigdy nie dotrzeć do usługi. Jeśli operacja wysyłania zakończy się pomyślnie po stronie klienta, nie gwarantuje to, że zdalny punkt końcowy otrzymał komunikat. Datagram jest elementem konstrukcyjnym podstawowych do obsługi komunikatów, możesz tworzyć własne protokołów na jego podstawie — w tym protokoły niezawodne i bezpieczne protokoły. Implementowanie kanały datagram klientów <xref:System.ServiceModel.Channels.IOutputChannel> implementuje interfejs i usługi kanały datagram <xref:System.ServiceModel.Channels.IInputChannel> interfejsu.  
  
- Request-Response (IRequestChannel/IReplyChannel)  
  
     W tym MEP wiadomość jest wysyłana i odpowiedzi. Wzorzec składa się z pary odpowiedź na żądanie. Odpowiedź na żądanie wywołania przykłady zdalnych wywołań procedur (RPC) i przeglądarka pobiera. Ten wzorzec jest nazywany również półdupleks. W tym MEP zaimplementuj kanały klientów <xref:System.ServiceModel.Channels.IRequestChannel> i zaimplementować usługi kanały <xref:System.ServiceModel.Channels.IReplyChannel>.  
  
- Duplex (IDuplexChannel)  
  
     Dwukierunkowe MEP umożliwia dowolną liczbę wiadomości wysłane przez klienta i odbieranie w dowolnej kolejności. Dwukierunkowego MEP przypomina rozmowy telefonicznej, gdzie każdy wyraz mowy jest komunikat. Obie strony może wysyłać i odbierać w tym MEP, interfejs implementowany przez kanały klient internetowy i usługa jest <xref:System.ServiceModel.Channels.IDuplexChannel>.  
  
 Każda z tych MEPs również obsługuje sesji. Dodano funkcje udostępniane przez kanał sesji aware jest, czy jest skorelowane wszystkie komunikaty wysłane i odebrane w kanale. Wzorzec odpowiedź na żądanie jest sesję komunikat dwóch autonomicznych, jak żądania i odpowiedzi są powiązane. Z kolei wzorzec odpowiedź na żądanie, który obsługuje sesji oznacza, że wszystkie pary żądanie/odpowiedź, w tym kanale są powiązane ze sobą. Daje w sumie sześć MEPs — Datagram, odpowiedź na żądanie, dupleks, Datagram z sesjami, odpowiedź na żądanie z sesji i dwukierunkowe z sesjami — do wyboru.  
  
> [!NOTE]
>  Dla transportu UDP Datagram, jest tylko MEP, która jest obsługiwana, ponieważ UDP jest protokołem "fire and forget".  
  
### <a name="the-icommunicationobject-and-the-wcf-object-lifecycle"></a>ICommunicationObject i cyklem życia obiektu programu WCF  
 Usługi WCF ma typowe automatu stanów, który służy do zarządzania cyklem życia obiektów, takich jak <xref:System.ServiceModel.Channels.IChannel>, <xref:System.ServiceModel.Channels.IChannelFactory>, i <xref:System.ServiceModel.Channels.IChannelListener> służące do komunikacji. Istnieje pięć państw, w których może istnieć tych obiektów komunikacyjnych. Te stany są reprezentowane przez <xref:System.ServiceModel.CommunicationState> wyliczenie i są w następujący sposób:  
  
- Utworzone: Jest to stan <xref:System.ServiceModel.ICommunicationObject> po raz pierwszy zostanie uruchomiony. Nie wejścia/wyjścia (We/Wy) występuje w tym stanie.  
  
- Otwieranie: Stan przejścia obiektów do tego, kiedy <xref:System.ServiceModel.ICommunicationObject.Open%2A> jest wywoływana. W tym momencie są wprowadzane niezmienialnych właściwości i rozpocząć wejścia/wyjścia. Ten proces przejścia jest prawidłowy tylko w stanie Created.  
  
- Otwarta: Obiekty przejście do tego stanu po zakończeniu procesu otwierania. Ten proces przejścia jest prawidłowy tylko w stanie otwarcia. W tym momencie obiekt jest w pełni użyteczne do przeniesienia.  
  
- Zamknięcie: Stan przejścia obiektów do tego, kiedy <xref:System.ServiceModel.ICommunicationObject.Close%2A> jest wywoływana dla łagodne zamykanie. Ten proces przejścia jest prawidłowy tylko w stanie otwartym.  
  
- Zamknięte: W polu Zamknięto obiekty stanu nie są już można używać. Ogólnie rzecz biorąc większość konfiguracji jest nadal dostępne dla kontroli, ale nie można komunikować się. Ten stan jest odpowiednikiem zostanie usunięty.  
  
- Wystąpił błąd: W stanie Faulted obiekty są dostępne do wglądu, ale można już używać. Gdy wystąpi błąd nieodwracalny, obiekt przechodzi w ten stan. Jedyne prawidłowe przejścia z tego stanu jest do `Closed` stanu.  
  
 Występują zdarzenia, które są aktywowane, dla każdego przejścia stanu. <xref:System.ServiceModel.ICommunicationObject.Abort%2A> Metodę można wywołać w dowolnym momencie i sprawia, że obiekt do którego nastąpi przejście od razu od bieżącego stanu w stanie zamkniętym. Wywoływanie <xref:System.ServiceModel.ICommunicationObject.Abort%2A> kończy się dowolnym niedokończona praca.  
  
<a name="ChannelAndChannelListener"></a>   
## <a name="channel-factory-and-channel-listener"></a>Fabryka kanałów i odbiornika kanałów  
 Następnym krokiem w pisaniu niestandardowe transportu jest utworzenie implementacji klasy <xref:System.ServiceModel.Channels.IChannelFactory> kanały klientów i z <xref:System.ServiceModel.Channels.IChannelListener> kanałach usługi. Warstwy kanału korzysta ze wzorca fabryki tworzenia kanałów. Usługi WCF zapewnia pomocnicy klasy bazowej dla tego procesu.  
  
- <xref:System.ServiceModel.Channels.CommunicationObject> Klasy implementuje <xref:System.ServiceModel.ICommunicationObject> oraz wymusza automatu stanów opisany wcześniej w kroku 2. 

- <xref:System.ServiceModel.Channels.ChannelManagerBase> Klasy implementuje <xref:System.ServiceModel.Channels.CommunicationObject> i zapewnia ujednolicone klasa bazowa dla <xref:System.ServiceModel.Channels.ChannelFactoryBase> i <xref:System.ServiceModel.Channels.ChannelListenerBase>. <xref:System.ServiceModel.Channels.ChannelManagerBase> Klasy działa w połączeniu z <xref:System.ServiceModel.Channels.ChannelBase>, która jest klasą bazową, która implementuje <xref:System.ServiceModel.Channels.IChannel>.  
  
- <xref:System.ServiceModel.Channels.ChannelFactoryBase> Klasy implementuje <xref:System.ServiceModel.Channels.ChannelManagerBase> i <xref:System.ServiceModel.Channels.IChannelFactory> i konsoliduje `CreateChannel` przeciążeń w jednym `OnCreateChannel` metody abstrakcyjnej.  
  
- <xref:System.ServiceModel.Channels.ChannelListenerBase> Klasy implementuje <xref:System.ServiceModel.Channels.IChannelListener>. Ta odpowiada za zarządzanie stanem podstawowe.  
  
 W tym przykładzie wdrożenie fabryki znajduje się w UdpChannelFactory.cs i implementacji odbiornik znajduje się w UdpChannelListener.cs. <xref:System.ServiceModel.Channels.IChannel> Implementacje są UdpOutputChannel.cs i UdpInputChannel.cs.  
  
### <a name="the-udp-channel-factory"></a>Fabryka kanałów UDP  
 `UdpChannelFactory` Pochodzi od klasy <xref:System.ServiceModel.Channels.ChannelFactoryBase>. Przykład zastępuje <xref:System.ServiceModel.Channels.ChannelFactoryBase.GetProperty%2A> zapewnienie dostępu do wersji wiadomości koder komunikatów. Zastępuje również próbki <xref:System.ServiceModel.Channels.ChannelFactoryBase.OnClose%2A> , dzięki czemu możemy zatrzymywania naszych wystąpienie <xref:System.ServiceModel.Channels.BufferManager> podczas przejścia automatu stanów.  
  
#### <a name="the-udp-output-channel"></a>Kanał danych wyjściowych UDP  
 `UdpOutputChannel` Implementuje <xref:System.ServiceModel.Channels.IOutputChannel>. Konstruktor weryfikuje argumentów i tworzy miejsce docelowe <xref:System.Net.EndPoint> na podstawie obiektu <xref:System.ServiceModel.EndpointAddress> który jest przekazywany w.  
  
```csharp
this.socket = new Socket(this.remoteEndPoint.AddressFamily, SocketType.Dgram, ProtocolType.Udp);  
```  
  
 Kanał może zostać zamknięty, bez problemu zmieniała lub ungracefully. Jeśli kanał jest zamknięta bez problemu zmieniała gniazda zostanie zamknięte, a wywołanie klasy bazowej `OnClose` metody. Jeśli to zgłasza wyjątek, wywołuje metodę infrastruktury `Abort` zapewnienie kanał jest czyszczony.  
  
```csharp
this.socket.Close(0);  
```  
  
 Następnie wdrożymy `Send()` i `BeginSend()` / `EndSend()`. To dzieli się na dwóch głównych sekcji. Najpierw możemy serializować komunikatu do tablicy typu byte.  
  
```csharp
ArraySegment<byte> messageBuffer = EncodeMessage(message);  
```  
  
 Firma Microsoft wyśle dane wynikowe w sieci.  
  
```csharp
this.socket.SendTo(messageBuffer.Array, messageBuffer.Offset, messageBuffer.Count, SocketFlags.None, this.remoteEndPoint);  
```  
  
### <a name="the-udpchannellistener"></a>The UdpChannelListener  
 `UdpChannelListener` Że próbki implementuje pochodzi od klasy <xref:System.ServiceModel.Channels.ChannelListenerBase> klasy. Aby otrzymać datagramy używa jedno gniazdo UDP. `OnOpen` Metoda otrzymuje dane przy użyciu gniazda UDP pętlę asynchronicznego. Dane są następnie przekształcana w wiadomości przy użyciu Framework Kodowanie komunikatu.  
  
```csharp
message = MessageEncoderFactory.Encoder.ReadMessage(new ArraySegment<byte>(buffer, 0, count), bufferManager);  
```  
  
 Ponieważ ten sam kanał datagram reprezentuje komunikaty przychodzące z różnych źródeł, `UdpChannelListener` jest odbiornika pojedynczego wystąpienia. Na większości, jednym aktywnym <xref:System.ServiceModel.Channels.IChannel> skojarzony z tym odbiornik naraz. Przykład generuje inny tylko wtedy, gdy kanał, który jest zwracany przez `AcceptChannel` metoda później zostanie usunięty. Gdy wiadomość zostaje odebrana, to umieszczonych w kolejce do tego kanału pojedynczego wystąpienia.  
  
#### <a name="udpinputchannel"></a>UdpInputChannel  
 `UdpInputChannel` Klasy implementuje `IInputChannel`. Składa się z kolejki wiadomości przychodzących, które jest wypełniana przez `UdpChannelListener`w gniazda. Te komunikaty są usuwane z kolejki przez `IInputChannel.Receive` metody.  
  
<a name="AddingABindingElement"></a>   
## <a name="adding-a-binding-element"></a>Dodawanie elementu powiązania  
 Teraz, gdy są kompilowane fabryk i kanałów, firma Microsoft musi narażają je do środowiska uruchomieniowego ServiceModel za pośrednictwem powiązania. Powiązanie to kolekcja elementów wiązania, który reprezentuje stos komunikacji skojarzone z adresem usługi. Każdy element w stosie jest reprezentowany przez [ \<powiązania >](../../../../docs/framework/misc/binding.md) elementu.  
  
 W tym przykładzie jest element powiązania `UdpTransportBindingElement`, która jest pochodną <xref:System.ServiceModel.Channels.TransportBindingElement>. Zastępuje ona poniższych metod, aby tworzyć fabryki skojarzone z naszych powiązania.  
  
```csharp
public IChannelFactory<TChannel> BuildChannelFactory<TChannel>(BindingContext context)  
{  
    return (IChannelFactory<TChannel>)(object)new UdpChannelFactory(this, context);  
}  
  
public IChannelListener<TChannel> BuildChannelListener<TChannel>(BindingContext context)  
{  
    return (IChannelListener<TChannel>)(object)new UdpChannelListener(this, context);  
}  
```  
  
 Zawiera również członków do klonowania `BindingElement` i zwracanie tym schemacie (soap.udp).  
  
## <a name="adding-metadata-support-for-a-transport-binding-element"></a>Dodanie obsługi metadanych elementu powiązania transportu  
 Do integracji naszego transportu w systemie metadanych, firma Microsoft obsługuje import i Eksport zasad. Dzięki temu można wygenerować klientów naszych powiązania za pomocą [narzędzia narzędzie metadanych elementu ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).  
  
### <a name="adding-wsdl-support"></a>Dodawanie pomocy technicznej WSDL  
 Element powiązania transportu powiązanie jest odpowiedzialny za eksportowanie i importowanie informacji o adresach w metadanych. Korzystając z powiązania protokołu SOAP, element powiązania transportu powinien również wyeksportować poprawne transportu identyfikatora URI w metadanych.  
  
#### <a name="wsdl-export"></a>WSDL Export  
 Aby wyeksportować informacje dotyczące adresowania `UdpTransportBindingElement` implementuje `IWsdlExportExtension` interfejsu. `ExportEndpoint` Metoda dodaje poprawnych informacji adresowania do portu WSDL.  
  
```csharp
if (context.WsdlPort != null)  
{  
    AddAddressToWsdlPort(context.WsdlPort, context.Endpoint.Address, encodingBindingElement.MessageVersion.Addressing);  
}  
```  
  
 `UdpTransportBindingElement` Implementacji `ExportEndpoint` metoda również eksportuje transportu identyfikatora URI, gdy punkt końcowy korzysta z powiązania protokołu SOAP.  
  
```csharp
WsdlNS.SoapBinding soapBinding = GetSoapBinding(context, exporter);  
if (soapBinding != null)  
{  
    soapBinding.Transport = UdpPolicyStrings.UdpNamespace;  
}  
```  
  
#### <a name="wsdl-import"></a>WSDL Import  
 Aby rozszerzyć system importu WSDL do obsługi adresów importowania, firma Microsoft należy dodać następującą konfigurację do pliku konfiguracji dla Svcutil.exe jak pokazano w pliku Svcutil.exe.config.  
  
```xml
<configuration>  
  <system.serviceModel>  
    <client>  
      <metadata>  
        <wsdlImporters>  
          <extension type=" Microsoft.ServiceModel.Samples.UdpBindingElementImporter, UdpTransport" />  
        </policyImporters>  
      </metadata>  
    </client>  
  </system.serviceModel>  
</configuration>  
```  
  
 Podczas uruchamiania Svcutil.exe, istnieją dwie opcje w celu uzyskania Svcutil.exe można załadować rozszerzenia importu WSDL:  
  
1. Punkt Svcutil.exe do naszego pliku konfiguracji, za pomocą /SvcutilConfig:\<pliku >.  
  
2. Dodaj sekcję konfiguracji do Svcutil.exe.config, w tym samym katalogu co Svcutil.exe.  
  
 `UdpBindingElementImporter` Typ implementuje `IWsdlImportExtension` interfejsu. `ImportEndpoint` Metoda importuje adres z portu WSDL.  
  
```csharp
BindingElementCollection bindingElements = context.Endpoint.Binding.CreateBindingElements();  
TransportBindingElement transportBindingElement = bindingElements.Find<TransportBindingElement>();  
if (transportBindingElement is UdpTransportBindingElement)  
{  
    ImportAddress(context);  
}  
```  
  
### <a name="adding-policy-support"></a>Dodanie obsługi zasad  
 Element niestandardowego powiązania, można wyeksportować asercji zasad Powiązanie WSDL dla punktu końcowego usługi do wyrażenia możliwości tego elementu powiązania.  
  
#### <a name="policy-export"></a>Eksportowanie zasad  
 `UdpTransportBindingElement` Typ implementuje `IPolicyExportExtension` się Dodaj pomoc techniczna dotycząca eksportowania zasad. W rezultacie `System.ServiceModel.MetadataExporter` obejmuje `UdpTransportBindingElement` podczas generowania zasady dla powiązania zawierający go.  
  
 W `IPolicyExportExtension.ExportPolicy`, możemy dodać potwierdzenia dla protokołów UDP i innym potwierdzenie, jeśli firma Microsoft w trybie multiemisji. Jest to spowodowane ma wpływ tryb multiemisji jak stos komunikacji jest tworzony i dlatego musi być koordynowane między obie strony.  
  
```csharp
ICollection<XmlElement> bindingAssertions = context.GetBindingAssertions();  
XmlDocument xmlDocument = new XmlDocument();  
bindingAssertions.Add(xmlDocument.CreateElement(  
UdpPolicyStrings.Prefix, UdpPolicyStrings.TransportAssertion, UdpPolicyStrings.UdpNamespace));  
if (Multicast)  
{  
    bindingAssertions.Add(xmlDocument.CreateElement(
        UdpPolicyStrings.Prefix, 
        UdpPolicyStrings.MulticastAssertion, 
        UdpPolicyStrings.UdpNamespace));  
}  
```  
  
 Ponieważ elementy powiązania transportu niestandardowego jest odpowiedzialny za obsługę adresowania, `IPolicyExportExtension` implementacji na `UdpTransportBindingElement` muszą również obsługiwać eksportowania odpowiednie WS-Addressing asercji zasad do wskazania wersji WS-Addressing jest używane.  
  
```csharp
AddWSAddressingAssertion(context, encodingBindingElement.MessageVersion.Addressing);  
```  
  
#### <a name="policy-import"></a>Importuj zasady  
 Aby rozszerzyć system zaimportować zasad, firma Microsoft Dodaj następującą konfigurację do pliku konfiguracji dla Svcutil.exe jak pokazano w pliku Svcutil.exe.config.  
  
```xml
<configuration>  
  <system.serviceModel>  
    <client>  
      <metadata>  
        <policyImporters>  
          <extension type=" Microsoft.ServiceModel.Samples.UdpBindingElementImporter, UdpTransport" />  
        </policyImporters>  
      </metadata>  
    </client>  
  </system.serviceModel>  
</configuration>  
```  
  
 Następnie wdrożymy `IPolicyImporterExtension` z naszych zarejestrowanych klasy (`UdpBindingElementImporter`). W `ImportPolicy()`, firma Microsoft za pośrednictwem potwierdzenia w naszych przestrzeni nazw i przetwarzać te generowania transportu i sprawdź, czy jest multiemisji. Możemy również usunąć potwierdzenia, które będziemy obsługiwać z listy powiązania potwierdzenia. Ponownie uruchamiając Svcutil.exe, dostępne są dwie opcje integracji:  
  
1. Punkt Svcutil.exe do naszego pliku konfiguracji, za pomocą /SvcutilConfig:\<pliku >.  
  
2. Dodaj sekcję konfiguracji do Svcutil.exe.config, w tym samym katalogu co Svcutil.exe.  
  
<a name="AddingAStandardBinding"></a>   
## <a name="adding-a-standard-binding"></a>Dodawanie standardowych powiązania  
 Nasz element powiązania może służyć w następujących dwóch sposobów:  
  
- Za pośrednictwem powiązania niestandardowego: Powiązanie niestandardowe umożliwia użytkownikowi tworzenie własnych powiązania na podstawie dowolnego zestawu elementów wiązania.  
  
- Za pomocą powiązania dostarczane przez system obejmuje to nasz element powiązania. WCF udostępnia wiele z tych powiązań zdefiniowanych przez system, takie jak `BasicHttpBinding`, `NetTcpBinding`, i `WsHttpBinding`. Każda z tych powiązań jest skojarzona z profilem dobrze zdefiniowane.  
  
 Przykład implementuje powiązanie profilu w `SampleProfileUdpBinding`, która jest pochodną <xref:System.ServiceModel.Channels.Binding>. `SampleProfileUdpBinding` Zawiera maksymalnie cztery elementy powiązania w niej: `UdpTransportBindingElement`, `TextMessageEncodingBindingElement CompositeDuplexBindingElement`, i `ReliableSessionBindingElement`.  
  
```csharp
public override BindingElementCollection CreateBindingElements()  
{     
    BindingElementCollection bindingElements = new BindingElementCollection();  
    if (ReliableSessionEnabled)  
    {  
        bindingElements.Add(session);  
        bindingElements.Add(compositeDuplex);  
    }  
    bindingElements.Add(encoding);  
    bindingElements.Add(transport);  
    return bindingElements.Clone();  
}  
```  
  
### <a name="adding-a-custom-standard-binding-importer"></a>Dodawanie niestandardowych standardowego powiązanie importera  
 Svcutil.exe i `WsdlImporter` typu domyślnie, rozpoznaje i importuje powiązań zdefiniowanych przez system. W przeciwnym razie powiązanie pobiera importowane jako `CustomBinding` wystąpienia. Aby włączyć Svcutil.exe i `WsdlImporter` do zaimportowania `SampleProfileUdpBinding` `UdpBindingElementImporter` działa również jako importera niestandardowego powiązania standardowych.  
  
 Implementuje importera niestandardowego powiązania standardowa `ImportEndpoint` metody `IWsdlImportExtension` interfejsu do sprawdzenia `CustomBinding` wystąpienia zaimportowane z metadanych, aby zobaczyć, czy może on zostać wygenerowane przez określone powiązanie standardowe.  
  
```csharp
if (context.Endpoint.Binding is CustomBinding)  
{  
    Binding binding;  
    if (transportBindingElement is UdpTransportBindingElement)  
    {  
        //if TryCreate is true, the CustomBinding will be replace by a SampleProfileUdpBinding in the  
        //generated config file for better typed generation.  
        if (SampleProfileUdpBinding.TryCreate(bindingElements, out binding))  
        {  
            binding.Name = context.Endpoint.Binding.Name;  
            binding.Namespace = context.Endpoint.Binding.Namespace;  
            context.Endpoint.Binding = binding;  
        }  
    }  
}  
```  
  
 Ogólnie rzecz biorąc Implementowanie importera niestandardowego powiązania standardowa polega na sprawdzeniu właściwości elementów wiązania zaimportowanych, aby sprawdzić, czy tylko właściwości, które można ustawić przez powiązanie standardowe zostały zmienione, a wszystkie pozostałe właściwości są ich wartości domyślne. Podstawowe strategii wykonywania importera Powiązanie standardowe jest utworzenie wystąpienia standard powiązania Propagacja powiązania właściwości z elementy powiązania wystąpienie Powiązanie standardowe, które obsługuje standardowe powiązania w celu porównania elementy wiązania standardowa elementami importowanych powiązania.  
  
<a name="AddingConfigurationSupport"></a>   
## <a name="adding-configuration-support"></a>Dodanie obsługi konfiguracji  
 Aby udostępnić naszym transportu za pomocą konfiguracji, musimy zaimplementować dwie sekcje konfiguracji. Pierwsza to `BindingElementExtensionElement` dla `UdpTransportBindingElement`. Jest to tak, aby `CustomBinding` implementacji może odwoływać się do naszych element powiązania. Drugi to `Configuration` dla naszych `SampleProfileUdpBinding`.  
  
### <a name="binding-element-extension-element"></a>Element rozszerzenia elementu powiązania  
 Sekcja `UdpTransportElement` jest `BindingElementExtensionElement` który uwidacznia `UdpTransportBindingElement` systemu konfiguracji. Za pomocą kilku podstawowych zastąpień definiujemy naszych nazwa sekcji konfiguracji, typ nasz element powiązania oraz sposób tworzenia nasz element powiązania. Firma Microsoft można zarejestrować naszej sekcji rozszerzeń w pliku konfiguracji, jak pokazano w poniższym kodzie.  
  
```xml
<configuration>  
  <system.serviceModel>  
    <extensions>  
      <bindingElementExtensions>  
        <add name="udpTransport" type="Microsoft.ServiceModel.Samples.UdpTransportElement, UdpTransport />  
      </bindingElementExtensions>  
    </extensions>  
  </system.serviceModel>  
</configuration>  
```  
  
 Rozszerzenia mogą być przywoływane z powiązań niestandardowych, aby używać protokołu UDP transportu.  
  
```xml
<configuration>  
  <system.serviceModel>  
    <bindings>  
      <customBinding>  
       <binding configurationName="UdpCustomBinding">  
         <udpTransport/>  
       </binding>  
      </customBinding>  
    </bindings>  
  </system.serviceModel>  
</configuration>  
```  
  
### <a name="binding-section"></a>Sekcja powiązania  
 Sekcja `SampleProfileUdpBindingCollectionElement` jest `StandardBindingCollectionElement` który uwidacznia `SampleProfileUdpBinding` systemu konfiguracji. Duża część wykonania jest delegowane do `SampleProfileUdpBindingConfigurationElement`, która jest pochodną `StandardBindingElement`. `SampleProfileUdpBindingConfigurationElement` Ma właściwości, które odnoszą się do właściwości `SampleProfileUdpBinding`i funkcji do mapowania z `ConfigurationElement` powiązania. Na koniec Zastąp `OnApplyConfiguration` method in Class metoda naszych `SampleProfileUdpBinding`, jak pokazano w poniższym przykładowym kodzie.  
  
```csharp
protected override void OnApplyConfiguration(string configurationName)  
{  
    if (binding == null)
        throw new ArgumentNullException("binding");

    if (binding.GetType() != typeof(SampleProfileUdpBinding))
    {
        throw new ArgumentException(string.Format(CultureInfo.CurrentCulture,
            "Invalid type for binding. Expected type: {0}. Type passed in: {1}.",
            typeof(SampleProfileUdpBinding).AssemblyQualifiedName,
            binding.GetType().AssemblyQualifiedName));
    }
    SampleProfileUdpBinding udpBinding = (SampleProfileUdpBinding)binding;

    udpBinding.OrderedSession = this.OrderedSession;
    udpBinding.ReliableSessionEnabled = this.ReliableSessionEnabled;
    udpBinding.SessionInactivityTimeout = this.SessionInactivityTimeout;
    if (this.ClientBaseAddress != null)
        udpBinding.ClientBaseAddress = ClientBaseAddress;
}
```  
  
 Aby zarejestrować ten program obsługi przy użyciu systemu konfiguracji, można dodać następującą sekcję do pliku konfiguracji związanych z.  
  
```xml
<configuration>  
  <configSections>  
     <sectionGroup name="system.serviceModel">  
        <sectionGroup name="bindings">  
          <section name="sampleProfileUdpBinding" type="Microsoft.ServiceModel.Samples.SampleProfileUdpBindingCollectionElement, UdpTransport />  
        </sectionGroup>  
     </sectionGroup>  
  </configSections>  
</configuration>  
```  
  
 Go mogą następnie odwoływać się w sekcji Konfiguracja modelu serviceModel.  
  
```xml
<configuration>  
  <system.serviceModel>  
    <client>  
      <endpoint configurationName="calculator"  
                address="soap.udp://localhost:8001/"   
                bindingConfiguration="CalculatorServer"  
                binding="sampleProfileUdpBinding"   
                contract= "Microsoft.ServiceModel.Samples.ICalculatorContract">  
      </endpoint>  
    </client>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="the-udp-test-service-and-client"></a>Usługa Test UDP i klienta  
 Za pomocą transportu ten przykładowy kod testu jest dostępna w katalogach UdpTestService i UdpTestClient. Kod usługi składa się z dwóch testów — jeden test ustawia powiązania i punktów końcowych z kodu i innych zrobi to za pośrednictwem konfiguracji. Oba testy używają dwa punkty końcowe. Jeden punkt końcowy korzysta z `SampleUdpProfileBinding` z [ \<reliableSession >](https://docs.microsoft.com/previous-versions/ms731375(v=vs.90)) równa `true`. Inny punkt końcowy korzysta z niestandardowego powiązania za pomocą `UdpTransportBindingElement`. Jest to równoważne użyciu `SampleUdpProfileBinding` z [ \<reliableSession >](https://docs.microsoft.com/previous-versions/ms731375(v=vs.90)) równa `false`. Oba testy utworzyć usługę, Dodaj punkt końcowy dla każdego powiązania, otwórz usługę i zaczekaj, aż użytkownikowi przed zamknięciem usługi naciśnij klawisz ENTER.  
  
 Po uruchomieniu aplikacji testowej usługi powinny pojawić się następujące dane wyjściowe.  
  
```console
Testing Udp From Code.  
Service is started from code...  
Press <ENTER> to terminate the service and start service from config...  
```  
  
 Następnie można uruchomić aplikacji klienckiej testu względem opublikowanych punktów końcowych. Aplikacja testowa klienta tworzy klienta dla każdego punktu końcowego i wysyła pięć wiadomości do każdego punktu końcowego. Następujące dane wyjściowe to na kliencie.  
  
```console
Testing Udp From Imported Files Generated By SvcUtil.  
0  
3  
6  
9  
12  
Press <ENTER> to complete test.  
```  
  
 Poniżej przedstawiono pełne dane wyjściowe w usłudze.  
  
```console
Service is started from code...  
Press <ENTER> to terminate the service and start service from config...  
Hello, world!  
Hello, world!  
Hello, world!  
Hello, world!  
Hello, world!  
   adding 0 + 0  
   adding 1 + 2  
   adding 2 + 4  
   adding 3 + 6  
   adding 4 + 8  
```  
  
 Aby uruchomić aplikacji klienckiej względem punktów końcowych opublikowanych przy użyciu konfiguracji, naciśnij klawisz ENTER w usłudze, a następnie ponownie uruchom klienta testowego. Następujące dane wyjściowe powinny być widoczne w usłudze.  
  
```console
Testing Udp From Config.  
Service is started from config...  
Press <ENTER> to terminate the service and exit...  
```  
  
 Ponowne uruchomienie klienta daje takie same jak w poprzednim.  
  
 Aby ponownie wygenerować kod klienta i konfiguracji za pomocą Svcutil.exe, uruchamiania aplikacji usługi, a następnie uruchom następujące Svcutil.exe z katalogu głównego przykładowego.  
  
```console
svcutil http://localhost:8000/udpsample/ /reference:UdpTranport\bin\UdpTransport.dll /svcutilConfig:svcutil.exe.config  
```  
  
 Należy pamiętać, Svcutil.exe nie generuje konfigurację rozszerzenia powiązania `SampleProfileUdpBinding`, dlatego należy je dodać ręcznie.  
  
```xml
<configuration>  
  <system.serviceModel>      
    <extensions>  
      <!-- This was added manually because svcutil.exe does not add this extension to the file -->  
      <bindingExtensions>  
        <add name="sampleProfileUdpBinding" type="Microsoft.ServiceModel.Samples.SampleProfileUdpBindingCollectionElement, UdpTransport" />  
      </bindingExtensions>  
    </extensions>  
  </system.serviceModel>  
</configuration>  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, tworzenie i uruchamianie aplikacji przykładowej  
  
1. Aby skompilować rozwiązanie, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
2. Do uruchomienia przykładu w konfiguracji o jednym lub wielu maszyny, postępuj zgodnie z instrukcjami [uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
3. Zapoznaj się z poprzedniej sekcji "UDP testu i klienta usługi".  
  
> [!IMPORTANT]
>  Przykłady może już być zainstalowany na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Transport\Udp`
