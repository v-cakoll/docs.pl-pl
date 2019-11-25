---
title: 'Transport: UDP'
ms.date: 03/30/2017
ms.assetid: 738705de-ad3e-40e0-b363-90305bddb140
ms.openlocfilehash: fab15b1d4dab61de37f4b609a6e43c5f4a32fb75
ms.sourcegitcommit: fbb8a593a511ce667992502a3ce6d8f65c594edf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2019
ms.locfileid: "74138688"
---
# <a name="transport-udp"></a>Transport: UDP
Przykład transportu UDP ilustruje sposób implementacji protokołu UDP emisji pojedynczej i multiemisji jako niestandardowego transportu Windows Communication Foundation (WCF). W przykładzie opisano zalecaną procedurę tworzenia niestandardowego transportu w programie WCF przy użyciu struktury kanału i poniższych najlepszych rozwiązań w zakresie usług WCF. Poniżej przedstawiono procedurę tworzenia transportu niestandardowego:  
  
1. Podjęcie decyzji o tym, które z [komunikatów](#MessageExchangePatterns) kanału (IOutputChannel, IInputChannel, IDuplexChannel, IRequestChannel lub IReplyChannel) będą obsługiwane przez obiekt ChannelFactory i ChannelListener. Następnie zdecyduj, czy będą obsługiwane zmiany w sesji dla tych interfejsów.  
  
2. Utwórz fabrykę kanałów i odbiornik obsługujący wzorzec wymiany komunikatów.  
  
3. Upewnij się, że wszystkie wyjątki specyficzne dla sieci są znormalizowane do odpowiedniej klasy pochodnej <xref:System.ServiceModel.CommunicationException>.  
  
4. Dodaj element [> powiązania\<](../../configure-apps/file-schema/wcf/bindings.md) , który dodaje niestandardowy transport do stosu kanału. Aby uzyskać więcej informacji, zobacz [Dodawanie elementu powiązania](#AddingABindingElement).  
  
5. Dodaj sekcję rozszerzenie elementu powiązania, aby udostępnić nowy element powiązania do systemu konfiguracji.  
  
6. Dodaj rozszerzenia metadanych, aby komunikować możliwości z innymi punktami końcowymi.  
  
7. Dodaj powiązanie, które wstępnie konfiguruje stos elementów powiązania zgodnie z dobrze zdefiniowanym profilem. Aby uzyskać więcej informacji, zobacz [Dodawanie standardowego powiązania](#AddingAStandardBinding).  
  
8. Dodaj sekcję powiązania i element konfiguracji powiązania, aby uwidocznić powiązanie z systemem konfiguracji. Aby uzyskać więcej informacji, zobacz [Dodawanie obsługi konfiguracji](#AddingConfigurationSupport).  
  
<a name="MessageExchangePatterns"></a>   
## <a name="message-exchange-patterns"></a>Wzorce wymiany komunikatów  
 Pierwszym krokiem w przypadku pisania niestandardowego transportu jest podjęcie decyzji, które wzorce wymiany komunikatów (MEPs) są wymagane do transportu. Istnieją trzy MEPs do wyboru:  
  
- Datagram (IInputChannel/IOutputChannel)  
  
     W przypadku korzystania z unikatowy MEP datagramu klient wysyła komunikat przy użyciu wymiany "pożar i zapomnij". Usługa Fire i zapomnij wymiany jest taka, która wymaga potwierdzenia pomyślnego dostarczenia poza pasmem. Komunikat może zostać utracony podczas przesyłania i nigdy nie docierał do usługi. Jeśli operacja wysyłania zostanie zakończona pomyślnie na końcu klienta, nie gwarantuje to, że zdalny punkt końcowy odebrał komunikat. Datagram jest podstawowym blokiem konstrukcyjnym do obsługi komunikatów, ponieważ można tworzyć własne protokoły na jego podstawie — w tym niezawodne protokoły i bezpieczne protokoły. Kanały datagramów klienta implementują interfejsy <xref:System.ServiceModel.Channels.IOutputChannel> interfejs i datagram usługi implementują interfejs <xref:System.ServiceModel.Channels.IInputChannel>.  
  
- Żądanie-odpowiedź (IRequestChannel/IReplyChannel)  
  
     W tym unikatowy MEP komunikat jest wysyłany, a odpowiedź zostanie odebrana. Wzorzec składa się z par żądanie-odpowiedź. Przykłady wywołań żądania-odpowiedź to zdalne wywołania procedur (RPC) i przeglądarka. Ten wzorzec jest również znany jako półdupleks. W tym unikatowy MEP kanały klienta implementują <xref:System.ServiceModel.Channels.IRequestChannel> i kanały usługi implementują <xref:System.ServiceModel.Channels.IReplyChannel>.  
  
- Dupleks (IDuplexChannel)  
  
     UNIKATOWY MEP dupleks umożliwia wysyłanie dowolnej liczby komunikatów przez klienta i odbieranie ich w dowolnej kolejności. UNIKATOWY MEP dupleks jest taka sama jak rozmowa telefoniczna, gdzie każdy wypowiadany wyraz jest komunikatem. Ponieważ obie strony mogą wysyłać i odbierać dane w tym unikatowy MEP, interfejs zaimplementowany przez klienta i kanały usługi jest <xref:System.ServiceModel.Channels.IDuplexChannel>.  
  
 Każdy z tych MEPs może również obsługiwać sesje. Dodatkowe funkcje udostępniane przez kanał obsługujący sesje polegają na tym, że są skorelowane wszystkie komunikaty wysyłane i odbierane w kanale. Wzorzec żądanie-odpowiedź jest autonomiczną sesją dwustronicową, ponieważ żądanie i odpowiedź są skorelowane. Z kolei wzorzec żądanie-odpowiedź, który obsługuje sesje, oznacza, że wszystkie pary żądanie/odpowiedź w tym kanale są skorelowane ze sobą. Dzięki temu można uzyskać łącznie sześć MEPs — datagram, żądanie-odpowiedź, dupleks, datagram z sesjami, żądanie-odpowiedź z sesjami i dupleks z sesjami — do wyboru.  
  
> [!NOTE]
> W przypadku transportu UDP jedyną obsługiwaną unikatowy MEPą jest datagram, ponieważ protokół UDP jest z natury "pożar i zapomnij".  
  
### <a name="the-icommunicationobject-and-the-wcf-object-lifecycle"></a>Interfejs ICommunicationObject i cykl życia obiektów WCF  
 Program WCF ma wspólny komputer stanu używany do zarządzania cyklem życia obiektów, takimi jak <xref:System.ServiceModel.Channels.IChannel>, <xref:System.ServiceModel.Channels.IChannelFactory>i <xref:System.ServiceModel.Channels.IChannelListener>, które są używane do komunikacji. Istnieje pięć Stanów, w których te obiekty komunikacyjne mogą istnieć. Te Stany są reprezentowane przez Wyliczenie <xref:System.ServiceModel.CommunicationState> i są następujące:  
  
- Utworzone: jest to stan <xref:System.ServiceModel.ICommunicationObject> podczas pierwszego wystąpienia. W tym stanie nie ma danych wejściowych/wyjściowych (we/wy).  
  
- Otwieranie: obiekty są przenoszone do tego stanu po wywołaniu <xref:System.ServiceModel.ICommunicationObject.Open%2A>. W tym punkcie właściwości są niezmienne, a wejście/wyjście może zacząć. To przejście jest prawidłowe tylko ze stanu utworzonego.  
  
- Otwarte: obiekty są przenoszone do tego stanu po zakończeniu procesu otwierania. To przejście jest prawidłowe tylko w stanie otwarcia. W tym momencie obiekt jest w pełni przydatny do przeniesienia.  
  
- Zamykanie: obiekty są przenoszone do tego stanu, gdy <xref:System.ServiceModel.ICommunicationObject.Close%2A> jest wywoływana w celu bezpiecznego zamknięcia. To przejście jest prawidłowe tylko w stanie otwartym.  
  
- Zamknięte: w obiektach stanu zamkniętego nie można już używać. Ogólnie rzecz biorąc, większość konfiguracji jest nadal dostępna do inspekcji, ale nie można przeprowadzić komunikacji. Ten stan jest równoważny do usunięcia.  
  
- Błąd: w stanie błędu, obiekty są dostępne do inspekcji, ale nie są już użyteczne. Gdy wystąpi błąd nieodwracalny, obiekt przechodzi do tego stanu. Jedyne prawidłowe przejście z tego stanu jest w stanie `Closed`.  
  
 Istnieją zdarzenia wyzwalane dla każdego przejścia stanu. Metodę <xref:System.ServiceModel.ICommunicationObject.Abort%2A> można wywołać w dowolnym momencie i powoduje, że obiekt natychmiast przechodzi od bieżącego stanu do stanu zamkniętego. Wywołanie <xref:System.ServiceModel.ICommunicationObject.Abort%2A> kończy wszystkie nieukończone zadania.  
  
<a name="ChannelAndChannelListener"></a>   
## <a name="channel-factory-and-channel-listener"></a>Odbiornik kanałów i kanałów  
 Następnym krokiem podczas pisania niestandardowego transportu jest utworzenie implementacji <xref:System.ServiceModel.Channels.IChannelFactory> dla kanałów klienta i <xref:System.ServiceModel.Channels.IChannelListener> dla kanałów usługi. Warstwa kanału używa wzorca fabryki do konstruowania kanałów. Funkcja WCF udostępnia pomocników klasy bazowej dla tego procesu.  
  
- Klasa <xref:System.ServiceModel.Channels.CommunicationObject> implementuje <xref:System.ServiceModel.ICommunicationObject> i wymusza komputer stanu wcześniej opisany w kroku 2. 

- Klasa <xref:System.ServiceModel.Channels.ChannelManagerBase> implementuje <xref:System.ServiceModel.Channels.CommunicationObject> i zapewnia ujednoliconą klasę bazową dla <xref:System.ServiceModel.Channels.ChannelFactoryBase> i <xref:System.ServiceModel.Channels.ChannelListenerBase>. Klasa <xref:System.ServiceModel.Channels.ChannelManagerBase> działa w połączeniu z <xref:System.ServiceModel.Channels.ChannelBase>, która jest klasą bazową implementującą <xref:System.ServiceModel.Channels.IChannel>.  
  
- Klasa <xref:System.ServiceModel.Channels.ChannelFactoryBase> implementuje <xref:System.ServiceModel.Channels.ChannelManagerBase> i <xref:System.ServiceModel.Channels.IChannelFactory> i konsoliduje przeciążenia `CreateChannel` do jednej `OnCreateChannel` metody abstrakcyjnej.  
  
- Klasa <xref:System.ServiceModel.Channels.ChannelListenerBase> implementuje <xref:System.ServiceModel.Channels.IChannelListener>. Dział IT zajmuje się podstawowym zarządzaniem stanem.  
  
 W tym przykładzie implementacja fabryki jest zawarta w UdpChannelFactory.cs, a implementacja odbiornika jest zawarta w UdpChannelListener.cs. Implementacje <xref:System.ServiceModel.Channels.IChannel> są w UdpOutputChannel.cs i UdpInputChannel.cs.  
  
### <a name="the-udp-channel-factory"></a>Fabryka kanałów UDP  
 `UdpChannelFactory` pochodzi od <xref:System.ServiceModel.Channels.ChannelFactoryBase>. Przykład przesłania <xref:System.ServiceModel.Channels.ChannelFactoryBase.GetProperty%2A>, aby zapewnić dostęp do wersji komunikatu kodera wiadomości. W przykładzie zastąpił również <xref:System.ServiceModel.Channels.ChannelFactoryBase.OnClose%2A>, aby można było rozdzielić nasze wystąpienie <xref:System.ServiceModel.Channels.BufferManager> po przeniesieniu automatu Stanów.  
  
#### <a name="the-udp-output-channel"></a>Kanał wyjściowy UDP  
 `UdpOutputChannel` implementuje <xref:System.ServiceModel.Channels.IOutputChannel>. Konstruktor sprawdza poprawność argumentów i konstruuje obiekt docelowy <xref:System.Net.EndPoint> na podstawie przekazanego <xref:System.ServiceModel.EndpointAddress>.  
  
```csharp
this.socket = new Socket(this.remoteEndPoint.AddressFamily, SocketType.Dgram, ProtocolType.Udp);  
```  
  
 Kanał może być zamknięty bezpiecznie lub bezproblemowo. Jeśli kanał zostanie zamknięty bezpiecznie, gniazdo jest zamknięte, a wywołanie jest nawiązywane z klasą bazową `OnClose` metodzie. Jeśli zgłasza wyjątek, infrastruktura wywoła `Abort`, aby upewnić się, że kanał jest czyszczony.  
  
```csharp
this.socket.Close(0);  
```  
  
 Następnie implementujemy `Send()` i `BeginSend()`/`EndSend()`. Ten podział jest podzielony na dwie główne sekcje. Najpierw serializowaćmy komunikat do tablicy bajtów.  
  
```csharp
ArraySegment<byte> messageBuffer = EncodeMessage(message);  
```  
  
 Następnie wysyłamy dane uzyskane w sieci.  
  
```csharp
this.socket.SendTo(messageBuffer.Array, messageBuffer.Offset, messageBuffer.Count, SocketFlags.None, this.remoteEndPoint);  
```  
  
### <a name="the-udpchannellistener"></a>UdpChannelListener  
 `UdpChannelListener`, które implementuje przykład dziedziczy z klasy <xref:System.ServiceModel.Channels.ChannelListenerBase>. Do odbierania datagramów jest stosowane pojedyncze gniazdo UDP. Metoda `OnOpen` odbiera dane przy użyciu gniazda UDP w pętli asynchronicznej. Dane są następnie konwertowane na komunikaty przy użyciu struktury kodowania komunikatów.  
  
```csharp
message = MessageEncoderFactory.Encoder.ReadMessage(new ArraySegment<byte>(buffer, 0, count), bufferManager);  
```  
  
 Ponieważ ten sam kanał datagramu reprezentuje komunikat, który dociera z kilku źródeł, `UdpChannelListener` jest pojedynczym odbiornikiem. Istnieje najwyżej jedna aktywna <xref:System.ServiceModel.Channels.IChannel> skojarzona z tym odbiornikiem. Przykład generuje inny, tylko wtedy, gdy kanał, który jest zwracany przez metodę `AcceptChannel` jest następnie usuwany. Po odebraniu komunikatu jest on dodawany do kolejki pojedynczego tego kanału.  
  
#### <a name="udpinputchannel"></a>UdpInputChannel  
 Klasa `UdpInputChannel` implementuje `IInputChannel`. Składa się z kolejki komunikatów przychodzących wypełnianych przez gniazdo `UdpChannelListener`. Te komunikaty są dekolejkowane przez metodę `IInputChannel.Receive`.  
  
<a name="AddingABindingElement"></a>   
## <a name="adding-a-binding-element"></a>Dodawanie elementu powiązania  
 Teraz, gdy fabryki i kanały są kompilowane, muszą uwidocznić je w środowisku uruchomieniowym ServiceModel za pomocą powiązania. Powiązanie to kolekcja elementów powiązania, które reprezentują stos komunikacji skojarzony z adresem usługi. Każdy element w stosie jest reprezentowany przez [\<powiązanie >](../../configure-apps/file-schema/wcf/bindings.md) elementu.  
  
 W przykładzie element Binding jest `UdpTransportBindingElement`, który pochodzi z <xref:System.ServiceModel.Channels.TransportBindingElement>. Zastępuje on następujące metody tworzenia fabryk skojarzonych z naszymi powiązaniami.  
  
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
  
 Zawiera również elementy członkowskie do klonowania `BindingElement` i zwracają nasz schemat (SOAP. UDP).  
  
## <a name="adding-metadata-support-for-a-transport-binding-element"></a>Dodawanie obsługi metadanych dla elementu powiązania transportowego  
 Aby zintegrować transport w systemie metadanych, musimy obsługiwać import i eksport zasad. Dzięki temu można generować klientów naszego powiązania za pomocą [narzędzia Svcutil. exe (narzędzie do przesyłania metadanych)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).  
  
### <a name="adding-wsdl-support"></a>Dodawanie obsługi WSDL  
 Element powiązania transportu w powiązaniu jest odpowiedzialny za eksportowanie i importowanie informacji dotyczących adresowania w metadanych. W przypadku korzystania z powiązania SOAP element powiązania transportu powinien również eksportować prawidłowy identyfikator URI transportu w metadanych.  
  
#### <a name="wsdl-export"></a>Eksport WSDL  
 Aby wyeksportować informacje dotyczące adresowania, `UdpTransportBindingElement` implementuje interfejs `IWsdlExportExtension`. Metoda `ExportEndpoint` dodaje do portu WSDL prawidłowe informacje dotyczące adresowania.  
  
```csharp
if (context.WsdlPort != null)  
{  
    AddAddressToWsdlPort(context.WsdlPort, context.Endpoint.Address, encodingBindingElement.MessageVersion.Addressing);  
}  
```  
  
 `UdpTransportBindingElement` implementacja metody `ExportEndpoint` również eksportuje identyfikator URI transportu, gdy punkt końcowy używa powiązania protokołu SOAP.  
  
```csharp
WsdlNS.SoapBinding soapBinding = GetSoapBinding(context, exporter);  
if (soapBinding != null)  
{  
    soapBinding.Transport = UdpPolicyStrings.UdpNamespace;  
}  
```  
  
#### <a name="wsdl-import"></a>Import WSDL  
 Aby zwiększyć system importowania WSDL do obsługi importowania adresów, należy dodać następującą konfigurację do pliku konfiguracji programu Svcutil. exe, jak pokazano w pliku Svcutil. exe. config.  
  
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
  
 Podczas uruchamiania programu Svcutil. exe dostępne są dwie opcje pobrania pliku Svcutil. exe w celu załadowania rozszerzeń WSDL:  
  
1. Wskaż plik konfiguracyjny Svcutil. exe przy użyciu > pliku/SvcutilConfig:\<.  
  
2. Dodaj sekcję konfiguracji do pliku Svcutil. exe. config w tym samym katalogu, w którym znajduje się Svcutil. exe.  
  
 Typ `UdpBindingElementImporter` implementuje interfejs `IWsdlImportExtension`. Metoda `ImportEndpoint` importuje adres z portu WSDL.  
  
```csharp
BindingElementCollection bindingElements = context.Endpoint.Binding.CreateBindingElements();  
TransportBindingElement transportBindingElement = bindingElements.Find<TransportBindingElement>();  
if (transportBindingElement is UdpTransportBindingElement)  
{  
    ImportAddress(context);  
}  
```  
  
### <a name="adding-policy-support"></a>Dodawanie obsługi zasad  
 Niestandardowy element powiązania może eksportować potwierdzenia zasad w powiązaniu WSDL dla punktu końcowego usługi, aby przedstawić możliwości tego elementu powiązania.  
  
#### <a name="policy-export"></a>Eksport zasad  
 Typ `UdpTransportBindingElement` implementuje `IPolicyExportExtension`, aby dodać obsługę eksportowania zasad. W związku z tym `System.ServiceModel.MetadataExporter` zawiera `UdpTransportBindingElement` w generacji zasad dla dowolnego powiązania, które zawiera.  
  
 W `IPolicyExportExtension.ExportPolicy`dodamy potwierdzenie protokołu UDP i inne potwierdzenie w przypadku trybu multiemisji. Jest to spowodowane tym, że tryb multiemisji wpływa na sposób konstruowania stosu komunikacji i w związku z tym musi być koordynowany między stronami.  
  
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
  
 Ponieważ niestandardowe elementy powiązania transportu są odpowiedzialne za obsługę adresowania, implementacja `IPolicyExportExtension` na `UdpTransportBindingElement` musi również obsługiwać eksportowanie odpowiednich zatwierdzeń zasad WS-Addressing w celu wskazania używanej wersji WS-Addressing.  
  
```csharp
AddWSAddressingAssertion(context, encodingBindingElement.MessageVersion.Addressing);  
```  
  
#### <a name="policy-import"></a>Importowanie zasad  
 Aby można było zwiększyć system importowania zasad, należy dodać następującą konfigurację do pliku konfiguracji programu Svcutil. exe, jak pokazano w pliku Svcutil. exe. config.  
  
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
  
 Następnie implementujemy `IPolicyImporterExtension` z naszej zarejestrowanej klasy (`UdpBindingElementImporter`). W `ImportPolicy()`przeszukiwania potwierdzeń w naszym obszarze nazw i przetwarzania tych elementów w celu wygenerowania transportu i sprawdzenia, czy jest to multiemisja. Należy również usunąć z listy potwierdzeń powiązań. Po uruchomieniu programu Svcutil. exe dostępne są dwie opcje integracji:  
  
1. Wskaż plik konfiguracyjny Svcutil. exe przy użyciu > pliku/SvcutilConfig:\<.  
  
2. Dodaj sekcję konfiguracji do pliku Svcutil. exe. config w tym samym katalogu, w którym znajduje się Svcutil. exe.  
  
<a name="AddingAStandardBinding"></a>   
## <a name="adding-a-standard-binding"></a>Dodawanie powiązania standardowego  
 Nasz element powiązania może być używany na dwa sposoby:  
  
- Za pośrednictwem niestandardowego powiązania: niestandardowe powiązanie umożliwia użytkownikowi tworzenie własnych powiązań na podstawie dowolnego zestawu elementów powiązania.  
  
- Za pomocą podanego w systemie powiązania, które zawiera nasz element powiązania. Funkcja WCF udostępnia wiele takich powiązań zdefiniowanych przez system, takich jak `BasicHttpBinding`, `NetTcpBinding`i `WsHttpBinding`. Wszystkie te powiązania są skojarzone ze zdefiniowanym profilem.  
  
 Przykład implementuje powiązanie profilu w `SampleProfileUdpBinding`, które wynika z <xref:System.ServiceModel.Channels.Binding>. `SampleProfileUdpBinding` zawiera maksymalnie cztery elementy powiązania w ramach tej grupy: `UdpTransportBindingElement`, `TextMessageEncodingBindingElement CompositeDuplexBindingElement`i `ReliableSessionBindingElement`.  
  
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
  
### <a name="adding-a-custom-standard-binding-importer"></a>Dodawanie niestandardowego importera powiązań standardowych  
 Svcutil. exe i typ `WsdlImporter` domyślnie rozpoznaje i importuje powiązania zdefiniowane przez system. W przeciwnym razie powiązanie zostanie zaimportowane jako wystąpienie `CustomBinding`. Aby umożliwić programowi Svcutil. exe i `WsdlImporter` Importowanie `SampleProfileUdpBinding` `UdpBindingElementImporter` również działa jako niestandardowy importer powiązań standardowych.  
  
 Niestandardowy importer powiązań standardowych implementuje metodę `ImportEndpoint` w interfejsie `IWsdlImportExtension`, aby sprawdzić wystąpienie `CustomBinding` zaimportowane z metadanych, aby sprawdzić, czy mogło zostać wygenerowane przez określone powiązanie standardowe.  
  
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
  
 Ogólnie rzecz biorąc, implementacja niestandardowego importera powiązań standardowych polega na sprawdzeniu właściwości zaimportowanych elementów powiązania, aby sprawdzić, czy zmieniono tylko właściwości, które mogły zostać ustawione przez powiązanie standardowe, a wszystkie inne właściwości są ich domyślnymi. Podstawową strategią wdrażania importera powiązań standardowych jest utworzenie wystąpienia standardowego powiązania, propagowanie właściwości z elementów powiązania do standardowego wystąpienia powiązania, które obsługuje powiązanie standardowe, oraz porównanie powiązania elementy ze standardowego powiązania z zaimportowanymi elementami powiązania.  
  
<a name="AddingConfigurationSupport"></a>   
## <a name="adding-configuration-support"></a>Dodawanie obsługi konfiguracji  
 Aby udostępnić nasze transporty w konfiguracji, należy zaimplementować dwie sekcje konfiguracyjne. Pierwszy to `BindingElementExtensionElement` `UdpTransportBindingElement`. Jest tak dlatego, że implementacje `CustomBinding` mogą odwoływać się do naszego elementu powiązania. Drugim jest `Configuration` dla naszych `SampleProfileUdpBinding`.  
  
### <a name="binding-element-extension-element"></a>Element rozszerzenia elementu powiązania  
 Sekcja `UdpTransportElement` jest `BindingElementExtensionElement`, który uwidacznia `UdpTransportBindingElement` do systemu konfiguracji. Za pomocą kilku podstawowych zastąpień definiujemy nazwę sekcji konfiguracji, typ naszego elementu powiązania oraz sposób tworzenia naszego elementu powiązania. Następnie możemy zarejestrować naszą sekcję rozszerzenia w pliku konfiguracji, jak pokazano w poniższym kodzie.  
  
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
  
 Do rozszerzenia można odwoływać się z niestandardowych powiązań, aby użyć protokołu UDP jako transportu.  
  
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
 Sekcja `SampleProfileUdpBindingCollectionElement` jest `StandardBindingCollectionElement`, który uwidacznia `SampleProfileUdpBinding` do systemu konfiguracji. Zbiorcza implementacja jest delegowana do `SampleProfileUdpBindingConfigurationElement`, który pochodzi z `StandardBindingElement`. `SampleProfileUdpBindingConfigurationElement` ma właściwości, które odpowiadają właściwościom `SampleProfileUdpBinding`i funkcje do mapowania na podstawie powiązania `ConfigurationElement`. Na koniec Zastąp metodę `OnApplyConfiguration` w naszym `SampleProfileUdpBinding`, jak pokazano w poniższym przykładowym kodzie.  
  
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
  
 Aby zarejestrować ten program obsługi przy użyciu systemu konfiguracji, należy dodać następującą sekcję do odpowiedniego pliku konfiguracji.  
  
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
  
 Następnie można się do niego odwoływać z sekcji konfiguracji serviceModel.  
  
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
  
## <a name="the-udp-test-service-and-client"></a>Usługa i klient testowy UDP  
 Kod testowy służący do korzystania z tego przykładowego transportu jest dostępny w katalogach UdpTestService i UdpTestClient. Kod usługi składa się z dwóch testów — jeden test konfiguruje powiązania i punkty końcowe z kodu, a drugi robi to za pośrednictwem konfiguracji. Oba testy używają dwóch punktów końcowych. Jeden punkt końcowy używa `SampleUdpProfileBinding` z [\<reliableSession >](https://docs.microsoft.com/previous-versions/ms731375(v=vs.90)) ustawiony na `true`. Drugi punkt końcowy używa niestandardowego powiązania z `UdpTransportBindingElement`. Jest to równoznaczne z użyciem `SampleUdpProfileBinding` z [\<reliableSession >](https://docs.microsoft.com/previous-versions/ms731375(v=vs.90)) ustawionym na `false`. Oba testy umożliwiają utworzenie usługi, dodanie punktu końcowego dla każdego powiązania, otwarcie usługi i oczekiwanie na naciśnięcie klawisza ENTER przed zamknięciem usługi.  
  
 Po uruchomieniu aplikacji testowej usługi powinny zostać wyświetlone następujące dane wyjściowe.  
  
```console
Testing Udp From Code.  
Service is started from code...  
Press <ENTER> to terminate the service and start service from config...  
```  
  
 Następnie możesz uruchomić testową aplikację kliencką dla opublikowanych punktów końcowych. Aplikacja testowa klienta tworzy klienta dla każdego punktu końcowego i wysyła pięć komunikatów do każdego punktu końcowego. Następujące dane wyjściowe są na komputerze klienckim.  
  
```console
Testing Udp From Imported Files Generated By SvcUtil.  
0  
3  
6  
9  
12  
Press <ENTER> to complete test.  
```  
  
 Poniżej przedstawiono pełne dane wyjściowe usługi.  
  
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
  
 Aby uruchomić aplikację kliencką dla punktów końcowych publikowanych za pomocą konfiguracji, naciśnij klawisz ENTER w usłudze, a następnie ponownie uruchom klienta testowego. W usłudze powinny zostać wyświetlone następujące dane wyjściowe.  
  
```console
Testing Udp From Config.  
Service is started from config...  
Press <ENTER> to terminate the service and exit...  
```  
  
 Uruchomienie klienta ponownie daje takie samo, jak poprzednie wyniki.  
  
 Aby ponownie wygenerować kod i konfigurację klienta przy użyciu programu Svcutil. exe, uruchom aplikację usługi, a następnie uruchom następujący plik Svcutil. exe z katalogu głównego przykładu.  
  
```console
svcutil http://localhost:8000/udpsample/ /reference:UdpTransport\bin\UdpTransport.dll /svcutilConfig:svcutil.exe.config  
```  
  
 Należy pamiętać, że Svcutil. exe nie generuje konfiguracji rozszerzenia powiązania dla `SampleProfileUdpBinding`, więc należy dodać ją ręcznie.  
  
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
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, skompilować i uruchomić przykład  
  
1. Aby skompilować rozwiązanie, postępuj zgodnie z instrukcjami w temacie [Tworzenie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
2. Aby uruchomić przykład w konfiguracji na jednym lub wielu komputerach, postępuj zgodnie z instrukcjami w temacie [Uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
3. Zapoznaj się z poprzednią sekcją "usługa testowa i klient usługi UDP".  
  
> [!IMPORTANT]
> Przykłady mogą być już zainstalowane na komputerze. Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) , aby pobrać wszystkie próbki Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)]. Ten przykład znajduje się w następującym katalogu.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Transport\Udp`
