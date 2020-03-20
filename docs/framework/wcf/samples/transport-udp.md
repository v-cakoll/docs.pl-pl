---
title: 'Transport: UDP'
ms.date: 03/30/2017
ms.assetid: 738705de-ad3e-40e0-b363-90305bddb140
ms.openlocfilehash: 3fd16ccd634b6875eae1e87547c35c6cba79c857
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79143775"
---
# <a name="transport-udp"></a>Transport: UDP
Przykład transportu UDP pokazuje, jak zaimplementować emisję pojedynczą udp i multiemisji jako niestandardowy transport fundacji komunikacji systemu Windows (WCF). W przykładzie opisano zalecaną procedurę tworzenia transportu niestandardowego w WCF, przy użyciu struktury kanału i po WCF najlepszych rozwiązań. Kroki tworzenia transportu niestandardowego są następujące:  
  
1. Zdecyduj, który z wzorców [wymiany wiadomości](#MessageExchangePatterns) kanału (IOutputChannel, IInputChannel, IDuplexChannel, IRequestChannel lub IReplyChannel) będzie obsługiwać channelfactory i ChannelListener. Następnie zdecyduj, czy będzie obsługiwać sesyjne odmiany tych interfejsów.  
  
2. Utwórz fabrykę kanałów i odbiornika, które obsługują wzorzec wymiany wiadomości.  
  
3. Upewnij się, że wszelkie wyjątki specyficzne dla sieci <xref:System.ServiceModel.CommunicationException>są znormalizowane do odpowiedniej klasy pochodnej .  
  
4. Dodaj element [ \<>powiązania,](../../configure-apps/file-schema/wcf/bindings.md) który dodaje niestandardowy transport do stosu kanałów. Aby uzyskać więcej informacji, zobacz [Dodawanie elementu wiązania](#AddingABindingElement).  
  
5. Dodaj sekcję rozszerzenia elementu wiązania, aby udostępnić nowy element wiązania do systemu konfiguracji.  
  
6. Dodaj rozszerzenia metadanych, aby komunikować możliwości do innych punktów końcowych.  
  
7. Dodaj powiązanie, które wstępnie konfiguruje stos elementów wiązania zgodnie z dobrze zdefiniowanym profilem. Aby uzyskać więcej informacji, zobacz [Dodawanie powiązania standardowego](#AddingAStandardBinding).  
  
8. Dodaj sekcję powiązania i element konfiguracji powiązania, aby udostępnić powiązanie do systemu konfiguracji. Aby uzyskać więcej informacji, zobacz [Dodawanie obsługi konfiguracji](#AddingConfigurationSupport).  
  
<a name="MessageExchangePatterns"></a>
## <a name="message-exchange-patterns"></a>Wzorce wymiany wiadomości  
 Pierwszym krokiem w pisaniu transportu niestandardowego jest podjęcie decyzji, które wzorce wymiany komunikatów (MEP) są wymagane dla transportu. Do wyboru jest trzech posłów do PE:  
  
- Datagram (IInputChannel/IOutputChannel)  
  
     Podczas korzystania z datagramu PO, klient wysyła wiadomość za pomocą "ogień i zapomnij" wymiany. Wymiana ognia i zapomnij jest taki, który wymaga out-of-band potwierdzenie pomyślnej dostawy. Wiadomość może zostać utracona podczas przesyłania i nigdy nie dotrze do usługi. Jeśli operacja wysyłania zakończy się pomyślnie na końcu klienta, nie gwarantuje, że zdalny punkt końcowy odebrał wiadomość. Datagram jest podstawowym elementem konstrukcyjnym dla wiadomości, ponieważ można tworzyć własne protokoły na nim , w tym niezawodne protokoły i bezpieczne protokoły. Kanały datagramu <xref:System.ServiceModel.Channels.IOutputChannel> klienta implementują interfejs <xref:System.ServiceModel.Channels.IInputChannel> i kanały datagramu usługi implementują interfejs.  
  
- Odpowiedź na żądanie (IRequestChannel/IReplyChannel)  
  
     W tym posłie do PE wysyłana jest wiadomość i odbierana jest odpowiedź. Wzorzec składa się z par żądanie odpowiedź. Przykładami wywołań żądanie-odpowiedź są zdalne wywołania procedury (RPC) i kontrolery WIRT przeglądarki. Ten wzorzec jest również znany jako Półdupleks. W tym mep, <xref:System.ServiceModel.Channels.IRequestChannel> kanały klienta <xref:System.ServiceModel.Channels.IReplyChannel>implementowania i kanały usług implementować .  
  
- Dupleks (IDuplexChannel)  
  
     Dupleksowy poseł do PE umożliwia dowolną liczbę wiadomości, które mają być wysyłane przez klienta i odbierane w dowolnej kolejności. Dupleksowy poseł do PE jest jak rozmowa telefoniczna, gdzie każde wypowiadane słowo jest wiadomością. Ponieważ obie strony mogą wysyłać i odbierać w tym mep, <xref:System.ServiceModel.Channels.IDuplexChannel>interfejs zaimplementowany przez kanały klienta i usługi jest .  
  
 Każdy z tych posłów do PE może również poprzeć sesje. Dodatkową funkcją zapewnianą przez kanał obsługujący sesję jest to, że koreluje wszystkie wiadomości wysyłane i odbierane na kanale. Wzorzec request-response jest autonomiczną sesją dwóch wiadomości, ponieważ żądanie i odpowiedź są skorelowane. Z drugiej strony wzorzec request-response, który obsługuje sesje oznacza, że wszystkie pary żądania/odpowiedzi na tym kanale są ze sobą skorelowane. Daje to łącznie sześciu posłów do PE — Datagram, Żądanie odpowiedzi, Dupleks, Datagram z sesjami, Żądanie-Odpowiedź z sesjami i Dupleks z sesjami — do wyboru.  
  
> [!NOTE]
> W przypadku transportu UDP jedynym posłem do PE, który jest obsługiwany, jest Datagram, ponieważ UDP jest z natury protokołem "ogień i zapomnij".  
  
### <a name="the-icommunicationobject-and-the-wcf-object-lifecycle"></a>ICommunicationObject i cykl życia obiektu WCF  
 WCF ma wspólną maszynę stanu, która jest używana <xref:System.ServiceModel.Channels.IChannel> <xref:System.ServiceModel.Channels.IChannelFactory>do <xref:System.ServiceModel.Channels.IChannelListener> zarządzania cyklem życia obiektów, takich jak , i które są używane do komunikacji. Istnieje pięć stanów, w których te obiekty komunikacji mogą istnieć. Te stany są reprezentowane przez wyliczenie <xref:System.ServiceModel.CommunicationState> i są następujące:  
  
- Utworzone: Jest to <xref:System.ServiceModel.ICommunicationObject> stan, kiedy jest po raz pierwszy wystąpienia. W tym stanie nie występuje wejście/wyjście (We/Wy).  
  
- Otwieranie: Obiekty przejście <xref:System.ServiceModel.ICommunicationObject.Open%2A> do tego stanu, gdy jest wywoływana. W tym momencie właściwości są niezmienne i można rozpocząć wejście/wyjście. To przejście jest prawidłowe tylko ze stanu Utworzone.  
  
- Otwarte: Obiekty przejście do tego stanu po zakończeniu otwartego procesu. To przejście jest prawidłowe tylko ze stanu Otwieranie. W tym momencie obiekt jest w pełni użyteczny do transferu.  
  
- Zamknięcie: Obiekty przejścia do <xref:System.ServiceModel.ICommunicationObject.Close%2A> tego stanu, gdy jest wywoływana dla bezpiecznego zamknięcia. To przejście jest prawidłowe tylko ze stanu Otwarty.  
  
- Zamknięte: W stanie zamknięte obiekty nie nadają się już do użytku. Ogólnie rzecz biorąc większość konfiguracji jest nadal dostępna do inspekcji, ale nie może nastąpić żadna komunikacja. Ten stan jest odpowiednikiem unieszkodliwiwania.  
  
- Uszkodzony: W stanie Faulted obiekty są dostępne do inspekcji, ale nie są już użyteczne. Po wystąpieniu nieodwracalnego błędu obiekt przechodzi do tego stanu. Jedynym prawidłowym przejściem z `Closed` tego stanu jest do stanu.  
  
 Istnieją zdarzenia, które uruchamiają dla każdego przejścia stanu. Metoda <xref:System.ServiceModel.ICommunicationObject.Abort%2A> może być wywoływana w dowolnym momencie i powoduje, że obiekt do przejścia natychmiast z jego bieżącego stanu do zamkniętego stanu. Wywołanie <xref:System.ServiceModel.ICommunicationObject.Abort%2A> kończy niedokończoną pracę.  
  
<a name="ChannelAndChannelListener"></a>
## <a name="channel-factory-and-channel-listener"></a>Fabryka kanałów i odbiornik kanałów  
 Następnym krokiem w pisaniu transportu niestandardowego <xref:System.ServiceModel.Channels.IChannelFactory> jest utworzenie <xref:System.ServiceModel.Channels.IChannelListener> implementacji dla kanałów klienta i dla kanałów usług. Warstwa kanału używa wzorca fabrycznego do konstruowania kanałów. WCF zapewnia pomocników klasy podstawowej dla tego procesu.  
  
- Klasa <xref:System.ServiceModel.Channels.CommunicationObject> implementuje <xref:System.ServiceModel.ICommunicationObject> i wymusza maszynę stanu wcześniej opisane w kroku 2.

- Klasa <xref:System.ServiceModel.Channels.ChannelManagerBase> implementuje <xref:System.ServiceModel.Channels.CommunicationObject> i zapewnia ujednoliconą klasę podstawową dla <xref:System.ServiceModel.Channels.ChannelFactoryBase> i <xref:System.ServiceModel.Channels.ChannelListenerBase>. Klasa <xref:System.ServiceModel.Channels.ChannelManagerBase> działa w <xref:System.ServiceModel.Channels.ChannelBase>połączeniu z , który jest <xref:System.ServiceModel.Channels.IChannel>klasą podstawową, która implementuje .  
  
- Klasa <xref:System.ServiceModel.Channels.ChannelFactoryBase> implementuje <xref:System.ServiceModel.Channels.ChannelManagerBase> <xref:System.ServiceModel.Channels.IChannelFactory> i konsoliduje `CreateChannel` przeciążenia `OnCreateChannel` w jedną metodę abstrakcyjną.  
  
- Klasa <xref:System.ServiceModel.Channels.ChannelListenerBase> implementuje <xref:System.ServiceModel.Channels.IChannelListener>. Zajmuje się podstawowym zarządzaniem państwem.  
  
 W tym przykładzie implementacji fabryki znajduje się w UdpChannelFactory.cs i implementacji odbiornika jest zawarty w UdpChannelListener.cs. Implementacje <xref:System.ServiceModel.Channels.IChannel> są w UdpOutputChannel.cs i UdpInputChannel.cs.  
  
### <a name="the-udp-channel-factory"></a>Fabryka kanałów UDP  
 Pochodzi `UdpChannelFactory` z <xref:System.ServiceModel.Channels.ChannelFactoryBase>. Przykładowe <xref:System.ServiceModel.Channels.ChannelFactoryBase.GetProperty%2A> zastąpienia, aby zapewnić dostęp do wersji wiadomości kodera wiadomości. Przykład również <xref:System.ServiceModel.Channels.ChannelFactoryBase.OnClose%2A> zastępuje, dzięki czemu możemy zniszczyć <xref:System.ServiceModel.Channels.BufferManager> nasze wystąpienie, gdy przechodzi maszyny stanu.  
  
#### <a name="the-udp-output-channel"></a>Kanał wyjściowy UDP  
 Implements `UdpOutputChannel` <xref:System.ServiceModel.Channels.IOutputChannel>. Konstruktor sprawdza poprawność argumentów <xref:System.Net.EndPoint> i konstruuje obiekt docelowy na podstawie <xref:System.ServiceModel.EndpointAddress> tego, który jest przekazywany w.  
  
```csharp
this.socket = new Socket(this.remoteEndPoint.AddressFamily, SocketType.Dgram, ProtocolType.Udp);  
```  
  
 Kanał można zamknąć z gracją lub bezgrawych. Jeśli kanał jest zamknięty bezpiecznie gniazdo jest zamknięty i wywołanie `OnClose` metody klasy podstawowej. Jeśli to zgłasza wyjątek, `Abort` infrastruktury wywołuje, aby upewnić się, że kanał jest czyszczone.  
  
```csharp
this.socket.Close(0);  
```  
  
 Następnie `Send()` wdrażamy `BeginSend()` / `EndSend()`i . To dzieli się na dwie główne sekcje. Najpierw serializujemy wiadomość do tablicy bajtów.  
  
```csharp
ArraySegment<byte> messageBuffer = EncodeMessage(message);  
```  
  
 Następnie wysyłamy uzyskane dane na drucie.  
  
```csharp
this.socket.SendTo(messageBuffer.Array, messageBuffer.Offset, messageBuffer.Count, SocketFlags.None, this.remoteEndPoint);  
```  
  
### <a name="the-udpchannellistener"></a>The UdpChannelListener  
 Implementuje `UdpChannelListener` próbki pochodzi z <xref:System.ServiceModel.Channels.ChannelListenerBase> klasy. Używa jednego gniazda UDP do odbierania datagramów. Metoda `OnOpen` odbiera dane przy użyciu gniazda UDP w pętli asynchroniczne. Dane są następnie konwertowane na wiadomości przy użyciu struktury kodowania wiadomości.  
  
```csharp
message = MessageEncoderFactory.Encoder.ReadMessage(new ArraySegment<byte>(buffer, 0, count), bufferManager);  
```  
  
 Ponieważ ten sam kanał datagramu reprezentuje komunikaty, `UdpChannelListener` które pochodzą z wielu źródeł, jest detektor singleton. Jest co najwyżej jeden <xref:System.ServiceModel.Channels.IChannel> aktywny związany z tym odbiornikiem naraz. Próbka generuje inny tylko wtedy, gdy kanał, który jest zwracany przez `AcceptChannel` metodę jest następnie usuwane. Po odebraniu wiadomości jest ona likżdowana w tej pojedynczej wiadomości.  
  
#### <a name="udpinputchannel"></a>UdpInputChannel  
 Klasa `UdpInputChannel` implementuje `IInputChannel`. Składa się z kolejki wiadomości przychodzących, `UdpChannelListener`który jest wypełniany przez gniazdo 's. Te komunikaty są usuwane `IInputChannel.Receive` w kolejce przez metodę.  
  
<a name="AddingABindingElement"></a>
## <a name="adding-a-binding-element"></a>Dodawanie elementu wiązania  
 Teraz, gdy fabryki i kanały są budowane, musimy udostępnić je do środowiska uruchomieniowego ServiceModel za pośrednictwem powiązania. Powiązanie jest kolekcją elementów wiązania, który reprezentuje stos komunikacji skojarzony z adresem usługi. Każdy element w stosie jest reprezentowany przez [ \<element wiązania>.](../../configure-apps/file-schema/wcf/bindings.md)  
  
 W próbce element wiązania `UdpTransportBindingElement`jest , <xref:System.ServiceModel.Channels.TransportBindingElement>który pochodzi z . Zastępuje następujące metody tworzenia fabryk skojarzonych z naszym powiązaniem.  
  
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
  
 Zawiera również członków do `BindingElement` klonowania i powrotu naszego programu (soap.udp).  
  
## <a name="adding-metadata-support-for-a-transport-binding-element"></a>Dodawanie obsługi metadanych dla elementu wiązania transportu  
 Aby zintegrować nasz transport z systemem metadanych, musimy wspierać zarówno import, jak i eksport polityki. Pozwala nam to na generowanie klientów naszego powiązania za pośrednictwem [narzędzia ServiceModel Metadata Utility Tool (Svcutil.exe).](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)  
  
### <a name="adding-wsdl-support"></a>Dodawanie obsługi WSDL  
 Element wiązania transportu w powiązaniu jest odpowiedzialny za eksportowanie i importowanie informacji adresowych w metadanych. Podczas korzystania z powiązania SOAP element wiązania transportu należy również wyeksportować poprawny identyfikator URI transportu w metadanych.  
  
#### <a name="wsdl-export"></a>Eksport WSDL  
 Aby wyeksportować informacje adresowe implementuje `UdpTransportBindingElement` `IWsdlExportExtension` interfejs. Metoda `ExportEndpoint` dodaje poprawne informacje adresowe do portu WSDL.  
  
```csharp
if (context.WsdlPort != null)  
{  
    AddAddressToWsdlPort(context.WsdlPort, context.Endpoint.Address, encodingBindingElement.MessageVersion.Addressing);  
}  
```  
  
 Implementacja `UdpTransportBindingElement` `ExportEndpoint` metody eksportuje również transportowy identyfikator URI, gdy punkt końcowy używa powiązania SOAP.  
  
```csharp
WsdlNS.SoapBinding soapBinding = GetSoapBinding(context, exporter);  
if (soapBinding != null)  
{  
    soapBinding.Transport = UdpPolicyStrings.UdpNamespace;  
}  
```  
  
#### <a name="wsdl-import"></a>WSDL Import  
 Aby rozszerzyć system importowania WSDL do obsługi importowania adresów, musimy dodać następującą konfigurację do pliku konfiguracyjnego dla pliku Svcutil.exe, jak pokazano w pliku Svcutil.exe.config.  
  
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
  
 Podczas uruchamiania programu Svcutil.exe dostępne są dwie opcje ładowania rozszerzenia importu WSDL przez program Svcutil.exe:  
  
1. Punkt Svcutil.exe do naszego pliku konfiguracyjnego za\<pomocą pliku /SvcutilConfig:>.  
  
2. Dodaj sekcję konfiguracji do pliku Svcutil.exe.config w tym samym katalogu co program Svcutil.exe.  
  
 Typ `UdpBindingElementImporter` implementuje `IWsdlImportExtension` interfejs. Metoda `ImportEndpoint` importuje adres z portu WSDL.  
  
```csharp
BindingElementCollection bindingElements = context.Endpoint.Binding.CreateBindingElements();  
TransportBindingElement transportBindingElement = bindingElements.Find<TransportBindingElement>();  
if (transportBindingElement is UdpTransportBindingElement)  
{  
    ImportAddress(context);  
}  
```  
  
### <a name="adding-policy-support"></a>Dodawanie obsługi zasad  
 Element wiązania niestandardowego można eksportować potwierdzeń zasad w powiązanie WSDL dla punktu końcowego usługi do wyrażania możliwości tego elementu wiązania.  
  
#### <a name="policy-export"></a>Eksport zasad  
 Typ `UdpTransportBindingElement` implementuje, `IPolicyExportExtension` aby dodać obsługę zasad eksportowania. W rezultacie `System.ServiceModel.MetadataExporter` obejmuje `UdpTransportBindingElement` w generowaniu zasad dla dowolnego powiązania, które go zawiera.  
  
 W `IPolicyExportExtension.ExportPolicy`, dodajemy potwierdzenia dla UDP i innego potwierdzenia, jeśli jesteśmy w trybie multiemisji. Jest tak, ponieważ tryb multiemisji wpływa na sposób konstruowania stosu komunikacji, a zatem musi być skoordynowane między obiema stronami.  
  
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
  
 Ponieważ niestandardowe elementy wiązania transportu są `IPolicyExportExtension` odpowiedzialne za `UdpTransportBindingElement` obsługę adresowania, implementacja na musi również obsługiwać eksportowanie odpowiednich potwierdzeń zasad adresowania WS, aby wskazać wersję używanego adresowania WS.  
  
```csharp
AddWSAddressingAssertion(context, encodingBindingElement.MessageVersion.Addressing);  
```  
  
#### <a name="policy-import"></a>Import zasad  
 Aby rozszerzyć system importu zasad, musimy dodać następującą konfigurację do pliku konfiguracyjnego dla pliku Svcutil.exe, jak pokazano w pliku Svcutil.exe.config.  
  
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
  
 Następnie wdrażamy `IPolicyImporterExtension` z naszej`UdpBindingElementImporter`zarejestrowanej klasy ( ). W `ImportPolicy()`, możemy przeglądać potwierdzenia w naszej przestrzeni nazw i przetwarzać te do generowania transportu i sprawdzić, czy jest multiemisji. Musimy również usunąć potwierdzenia, które obsługujemy z listy potwierdzeń wiązania. Ponownie, podczas uruchamiania programu Svcutil.exe dostępne są dwie opcje integracji:  
  
1. Punkt Svcutil.exe do naszego pliku konfiguracyjnego za\<pomocą pliku /SvcutilConfig:>.  
  
2. Dodaj sekcję konfiguracji do pliku Svcutil.exe.config w tym samym katalogu co program Svcutil.exe.  
  
<a name="AddingAStandardBinding"></a>
## <a name="adding-a-standard-binding"></a>Dodawanie standardowego powiązania  
 Nasz element wiązania może być używany na dwa sposoby:  
  
- Za pośrednictwem niestandardowego powiązania: Niestandardowe powiązanie umożliwia użytkownikowi tworzenie własnego powiązania na podstawie dowolnego zestawu elementów wiązania.  
  
- Za pomocą powiązania dostarczonego przez system, który zawiera nasz element wiązania. WCF udostępnia szereg tych powiązań zdefiniowanych `BasicHttpBinding`przez `NetTcpBinding`system, takich jak , i `WsHttpBinding`. Każde z tych powiązań jest skojarzone z dobrze zdefiniowanym profilem.  
  
 Przykład implementuje powiązanie `SampleProfileUdpBinding`profilu w <xref:System.ServiceModel.Channels.Binding>, który pochodzi od . Zawiera `SampleProfileUdpBinding` do czterech elementów wiązania `UdpTransportBindingElement` `TextMessageEncodingBindingElement CompositeDuplexBindingElement`w `ReliableSessionBindingElement`nim: , , i .  
  
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
  
### <a name="adding-a-custom-standard-binding-importer"></a>Dodawanie niestandardowego importera wiązania standardowego  
 Program Svcutil.exe `WsdlImporter` i typ domyślnie rozpoznają i importują powiązania zdefiniowane przez system. W przeciwnym razie powiązanie `CustomBinding` zostanie zaimportowane jako wystąpienie. Aby włączyć Svcutil.exe `WsdlImporter` i `SampleProfileUdpBinding` importować `UdpBindingElementImporter` również działa jako importer wiązania standard niestandardowy.  
  
 Importer wiązania niestandardowego standard `ImportEndpoint` implementuje `IWsdlImportExtension` metodę w `CustomBinding` interfejsie, aby sprawdzić wystąpienie importowane z metadanych, aby zobaczyć, czy mogło zostać wygenerowane przez określone powiązanie standardowe.  
  
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
  
 Ogólnie rzecz biorąc implementowanie importera wiązania niestandardowego standard polega na sprawdzeniu właściwości importowanych elementów wiązania, aby sprawdzić, czy tylko właściwości, które mogły zostać ustawione przez standardowe powiązanie zostały zmienione i wszystkie inne właściwości są ich wartościami domyślnymi. Podstawową strategią wdrażania standardowego importera wiązania jest utworzenie wystąpienia standardowego powiązania, propagowanie właściwości z elementów wiązania do standardowego wystąpienia wiązania, które obsługuje standardowe powiązanie, oraz porównywanie powiązania elementy ze standardowego powiązania z importowanymi elementami wiązania.  
  
<a name="AddingConfigurationSupport"></a>
## <a name="adding-configuration-support"></a>Dodawanie obsługi konfiguracji  
 Aby udostępnić nasz transport za pomocą konfiguracji, musimy wdrożyć dwie sekcje konfiguracji. Pierwszy to `BindingElementExtensionElement` dla `UdpTransportBindingElement`. Jest to `CustomBinding` tak, że implementacje można odwołać się do naszego elementu wiązania. Drugi jest `Configuration` dla `SampleProfileUdpBinding`naszych .  
  
### <a name="binding-element-extension-element"></a>Element rozszerzenia elementu wiązania  
 Sekcja `UdpTransportElement` `BindingElementExtensionElement` jest, która `UdpTransportBindingElement` udostępnia do systemu konfiguracji. Za pomocą kilku podstawowych przesłomów definiujemy naszą nazwę sekcji konfiguracji, typ naszego elementu wiązania i sposób tworzenia naszego elementu wiązania. Następnie możemy zarejestrować naszą sekcję rozszerzenia w pliku konfiguracyjnym, jak pokazano w poniższym kodzie.  
  
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
  
 Rozszerzenie można odwoływać się od niestandardowych powiązań do korzystania z protokołu UDP jako transportu.  
  
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
  
### <a name="binding-section"></a>Sekcja wiązania  
 Sekcja `SampleProfileUdpBindingCollectionElement` `StandardBindingCollectionElement` jest, która `SampleProfileUdpBinding` udostępnia do systemu konfiguracji. Większość implementacji jest delegowana `SampleProfileUdpBindingConfigurationElement`do , który `StandardBindingElement`pochodzi z . Ma `SampleProfileUdpBindingConfigurationElement` właściwości, które odpowiadają właściwości `SampleProfileUdpBinding`na , i funkcje do mapowania z `ConfigurationElement` powiązania. Na koniec należy zastąpić `OnApplyConfiguration` metodę `SampleProfileUdpBinding`w naszym , jak pokazano w poniższym przykładowym kodzie.  
  
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
  
 Aby zarejestrować ten program obsługi w systemie konfiguracji, dodajemy następującą sekcję do odpowiedniego pliku konfiguracyjnego.  
  
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
  
 Następnie można odwoływać się z serviceModel sekcji konfiguracji.  
  
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
  
## <a name="the-udp-test-service-and-client"></a>Usługa testowa UDP i klient  
 Kod testowy do korzystania z tego przykładowego transportu jest dostępny w katalogach UdpTestService i UdpTestClient. Kod usługi składa się z dwóch testów — jeden test konfiguruje powiązania i punkty końcowe z kodu, a drugi robi to za pośrednictwem konfiguracji. Oba testy używają dwóch punktów końcowych. Jeden punkt końcowy `SampleUdpProfileBinding` używa [ \<z reliableSession>](https://docs.microsoft.com/previous-versions/ms731375(v=vs.90)) `true`ustawiona na . Drugi punkt końcowy używa niestandardowego `UdpTransportBindingElement`powiązania z programem . Jest to równoważne użyciu `SampleUdpProfileBinding` z `false` [ \<reliableSession>](https://docs.microsoft.com/previous-versions/ms731375(v=vs.90)) ustawiona na . Oba testy tworzą usługę, dodają punkt końcowy dla każdego powiązania, otwierają usługę, a następnie czekają, aż użytkownik trafi enter przed zamknięciem usługi.  
  
 Po uruchomieniu aplikacji testowej usługi powinny zostać wyświetlenia następujących danych wyjściowych.  
  
```console
Testing Udp From Code.  
Service is started from code...  
Press <ENTER> to terminate the service and start service from config...  
```  
  
 Następnie można uruchomić aplikację klienta testowego względem opublikowanych punktów końcowych. Aplikacja testowa klienta tworzy klienta dla każdego punktu końcowego i wysyła pięć komunikatów do każdego punktu końcowego. Następujące dane wyjściowe znajduje się na kliencie.  
  
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
  
 Aby uruchomić aplikację kliencką względem punktów końcowych opublikowanych przy użyciu konfiguracji, naciśnij enter w usłudze, a następnie uruchom ponownie klienta testowego. W usłudze powinny zostać wyświetlenia następujące dane wyjściowe.  
  
```console
Testing Udp From Config.  
Service is started from config...  
Press <ENTER> to terminate the service and exit...  
```  
  
 Uruchamianie klienta ponownie daje takie same jak poprzednie wyniki.  
  
 Aby ponownie wygenerować kod klienta i konfigurację przy użyciu pliku Svcutil.exe, uruchom aplikację usługi, a następnie uruchom następujący program Svcutil.exe z katalogu głównego próbki.  
  
```console
svcutil http://localhost:8000/udpsample/ /reference:UdpTransport\bin\UdpTransport.dll /svcutilConfig:svcutil.exe.config  
```  
  
 Należy zauważyć, że program Svcutil.exe nie `SampleProfileUdpBinding`generuje konfiguracji rozszerzenia powiązania dla programu , dlatego należy dodać ją ręcznie.  
  
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
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, skompilować i uruchomić próbkę  
  
1. Aby utworzyć rozwiązanie, postępuj zgodnie z instrukcjami w [tworzeniu przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
2. Aby uruchomić próbkę w konfiguracji z jednym lub krzyżowym komputerem, postępuj zgodnie z instrukcjami w [programie Uruchamianie przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
3. Zapoznaj się z poprzednią sekcją "Usługa testowa I klient UDP".  
  
> [!IMPORTANT]
> Próbki mogą być już zainstalowane na komputerze. Przed kontynuowaniem sprawdź następujący (domyślny) katalog.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) Przykłady dla platformy .NET Framework 4,](https://www.microsoft.com/download/details.aspx?id=21459) aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady. Ten przykład znajduje się w następującym katalogu.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Transport\Udp`
