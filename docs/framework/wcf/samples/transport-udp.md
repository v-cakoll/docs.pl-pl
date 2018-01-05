---
title: 'Transport: UDP'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 738705de-ad3e-40e0-b363-90305bddb140
caps.latest.revision: "48"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1933d216f991b78e21a56ec67826dce0b4a7b24a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="transport-udp"></a>Transport: UDP
Przykładowe transportu UDP pokazano, jak wdrażanie UDP emisji pojedynczej i multiemisji jako niestandardowego [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] transportu. Próbka opisuje zalecaną procedurą tworzenia niestandardowych transportu w [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], przy użyciu platformy kanału i wykonując [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] najlepsze rozwiązania. Kroki, aby utworzyć niestandardowe transportu są następujące:  
  
1.  Decyzji, które kanału [wzorce wymiany wiadomości](#MessageExchangePatterns) (IOutputChannel IInputChannel, IDuplexChannel, IRequestChannel albo IReplyChannel) z elementu ChannelFactory i ChannelListener będzie obsługiwać. Następnie zdecydować, czy będzie obsługiwać zamykania zmian tych interfejsów.  
  
2.  Tworzenie fabryki kanałów i odbiornik, który obsługuje Twojej wymiany komunikatów.  
  
3.  Upewnij się, że wszelkie wyjątki dotyczące sieci są znormalizowane do odpowiedniej klasy pochodnej z <xref:System.ServiceModel.CommunicationException>.  
  
4.  Dodaj [ \<powiązania >](../../../../docs/framework/misc/binding.md) element, który dodaje niestandardowy transportu do stosu kanału. Aby uzyskać więcej informacji, zobacz [Dodawanie elementu powiązania](#AddingABindingElement).  
  
5.  Dodaj sekcję rozszerzenia elementu powiązania do udostępnienia element powiązania do konfiguracji systemu.  
  
6.  Dodawanie rozszerzeń metadanych do komunikowania się funkcji do innych punktów końcowych.  
  
7.  Dodaj powiązanie, które wstępnie konfiguruje stos elementy wiązania zgodnie z dobrze zdefiniowanego profilu. Aby uzyskać więcej informacji, zobacz [Dodawanie Powiązanie standardowe](#AddingAStandardBinding).  
  
8.  Dodaj powiązanie sekcji i elementu konfiguracji powiązania do udostępnienia powiązania system konfiguracji. Aby uzyskać więcej informacji, zobacz [dodanie obsługi konfiguracji](#AddingConfigurationSupport).  
  
<a name="MessageExchangePatterns"></a>   
## <a name="message-exchange-patterns"></a>Wzorce wymiany komunikatów  
 Pierwszy krok Pisanie niestandardowych transportu jest podjęcie decyzji, które wzorce wymiany wiadomości (MEPs) są wymagane dla transportu. Istnieją trzy MEPs do wyboru:  
  
-   Datagramów (IInputChannel/IOutputChannel)  
  
     Korzystając z datagram MEP, klient wysyła wiadomości przy użyciu "wyzwalać i zapomnij" programu exchange. Uruchomienie a zapomnieć exchange to taki, który wymaga potwierdzenia poza pasmem pomyślnie dostawy. Komunikat mogą zostać utracone podczas przesyłania i nigdy nie dotarcia do usługi. Jeśli operacja wysyłania zakończy się pomyślnie po stronie klienta, nie gwarantuje to, że zdalny punkt końcowy odebrał komunikat. Datagram jest bloku konstrukcyjnego podstawowych do obsługi wiadomości, ponieważ można tworzyć własne protokoły na nim — łącznie z protokołów bezpieczne i niezawodne protokoły. Wdrożenie klienta datagram kanałów <xref:System.ServiceModel.Channels.IOutputChannel> implementuje interfejs i Usługa datagramów kanałów <xref:System.ServiceModel.Channels.IInputChannel> interfejsu.  
  
-   Żądanie odpowiedź (IRequestChannel/IReplyChannel)  
  
     W tym MEP jest wysyłany komunikat i odpowiedzi. Wzorzec składa się z pary żądanie / odpowiedź. Przykłady wywołań żądań i odpowiedzi są zdalnych wywołań procedur (RPC) i przeglądarka pobiera. Ten wzorzec jest nazywany również półdupleks. W tym MEP wdrożenia klienta kanałów <xref:System.ServiceModel.Channels.IRequestChannel> i wdrożenie usługi kanałów <xref:System.ServiceModel.Channels.IReplyChannel>.  
  
-   Dupleks (IDuplexChannel)  
  
     Dupleks MEP umożliwia dowolnej liczby wiadomości wysłane przez klienta i odbieranie w dowolnej kolejności. Dupleks MEP przypomina rozmowy telefonicznej każdego wyrazu jest używany w przypadku komunikatu. Ponieważ obie strony może wysyłać i odbierać w tym MEP, interfejs implementowany przez kanały klient i usługa jest <xref:System.ServiceModel.Channels.IDuplexChannel>.  
  
 Każdy z tych MEPs również obsługuje sesji. Dodano funkcje udostępniane przez kanał obsługujący sesji jest ona są powiązane wszystkich wiadomości wysłanych i odebranych na kanale. Wzorzec żądań i odpowiedzi się sesję komunikat dwa autonomiczne skorelowanych żądania i odpowiedzi. Z kolei wzorzec żądań i odpowiedzi, który obsługuje sesji oznacza skorelowanych wszystkie pary żądanie/odpowiedź w tym kanale ze sobą. Daje łączną liczbę sześć MEPs — dupleks Datagram, żądanie-odpowiedź, Datagram z sesji i żądań i odpowiedzi z sesji i z sesji dupleksowej — do wyboru.  
  
> [!NOTE]
>  Dla transportu UDP Datagram, jest tylko MEP, która jest obsługiwana, ponieważ protokół UDP jest z założenia protokołem "wyzwalać i zapomnij".  
  
### <a name="the-icommunicationobject-and-the-wcf-object-lifecycle"></a>Interfejs ICommunicationObject i cyklem życia obiektów WCF  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]Typowe maszyna stanu, używany do zarządzania cyklem życia obiektów, takich jak <xref:System.ServiceModel.Channels.IChannel>, <xref:System.ServiceModel.Channels.IChannelFactory>, i <xref:System.ServiceModel.Channels.IChannelListener> używanych do komunikacji. Brak pięć Państwa, w których te obiekty komunikacji może istnieć. Te stany są reprezentowane przez <xref:System.ServiceModel.CommunicationState> wyliczenie i są w następujący sposób:  
  
-   Utworzona: Jest to stan <xref:System.ServiceModel.ICommunicationObject> po raz pierwszy zostanie uruchomiony. Nie wejścia/wyjścia (We/Wy) występuje w tym stanie.  
  
-   Otwieranie: Obiektów przejścia do tego stanu, kiedy <xref:System.ServiceModel.ICommunicationObject.Open%2A> jest wywoływana. W tym momencie właściwości są wprowadzane niezmienne i można rozpocząć operacji wejścia/wyjścia. Ten proces przejścia jest prawidłowy tylko w stanie Created.  
  
-   Otwarta: Przejście obiekty do tego stanu po zakończeniu procesu otwierania. Ten proces przejścia jest prawidłowy tylko w stanie otwarcia. W tym momencie obiekt jest w pełni gotowa do przeniesienia.  
  
-   Zamknięcia: Obiekty przejścia do tego stanu, kiedy <xref:System.ServiceModel.ICommunicationObject.Close%2A> jest wywoływana dla łagodne zamykanie. Ten proces przejścia jest prawidłowy tylko w stanie otwartym.  
  
-   Zamknięte: W polu Zamknięto obiekty stanu nie są już używać. Ogólnie rzecz biorąc większość konfiguracji jest nadal dostępne dla kontroli, ale nie można komunikować. Ten stan jest odpowiednikiem zostanie usunięty.  
  
-   Faulted: W stanie Faulted obiekty są dostępne do wglądu, ale można już używać. W przypadku nieodwracalny błąd przejścia obiektu, w tym stanie. To jedyne prawidłowe przejścia z tego stanu do `Closed` stanu.  
  
 Brak zdarzeń, które dla każdej zmiany stanu. <xref:System.ServiceModel.ICommunicationObject.Abort%2A> Metody można wywołać w dowolnej chwili i spowoduje, że obiekt przejście bezpośrednio z bieżącego stanu w stanie zamkniętym. Wywoływanie <xref:System.ServiceModel.ICommunicationObject.Abort%2A> kończy pracę niedokończone.  
  
<a name="ChannelAndChannelListener"></a>   
## <a name="channel-factory-and-channel-listener"></a>Fabryka kanałów i odbiornika kanałów  
 Następny krok w Pisanie niestandardowych transportu jest utworzenie implementacja <xref:System.ServiceModel.Channels.IChannelFactory> dla kanałów klienta oraz <xref:System.ServiceModel.Channels.IChannelListener> kanałów usługi. Warstwie kanału korzysta ze wzorca fabrykę do tworzenia kanałów. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]udostępnia pomocników klasę podstawową dla tego procesu.  
  
-   <xref:System.ServiceModel.Channels.CommunicationObject> Klasa implementuje <xref:System.ServiceModel.ICommunicationObject> i wymusza automatu stanów opisany w kroku 2. 

-   "<xref:System.ServiceModel.Channels.ChannelManagerBase> Klasa implementuje <xref:System.ServiceModel.Channels.CommunicationObject> i zapewnia ujednolicone klasa podstawowa dla <xref:System.ServiceModel.Channels.ChannelFactoryBase> i <xref:System.ServiceModel.Channels.ChannelListenerBase>. <xref:System.ServiceModel.Channels.ChannelManagerBase> Klasa działa w połączeniu z <xref:System.ServiceModel.Channels.ChannelBase>, która jest klasy podstawowej, która implementuje <xref:System.ServiceModel.Channels.IChannel>.  
  
-   "<xref:System.ServiceModel.Channels.ChannelFactoryBase> Klasa implementuje <xref:System.ServiceModel.Channels.ChannelManagerBase> i <xref:System.ServiceModel.Channels.IChannelFactory> i konsoliduje `CreateChannel` overloads do jednego `OnCreateChannel` metody abstrakcyjnej.  
  
-   <xref:System.ServiceModel.Channels.ChannelListenerBase> Klasa implementuje <xref:System.ServiceModel.Channels.IChannelListener>. Odpowiada on za podstawowy zarządzania.  
  
 W tym przykładzie wdrożenie fabryki znajduje się w UdpChannelFactory.cs i implementacji odbiornika znajduje się w UdpChannelListener.cs. <xref:System.ServiceModel.Channels.IChannel> Implementacje znajdują się w UdpOutputChannel.cs i UdpInputChannel.cs.  
  
### <a name="the-udp-channel-factory"></a>Fabryka kanałów UDP  
 `UdpChannelFactory` Pochodną <xref:System.ServiceModel.Channels.ChannelFactoryBase>. Zastępuje próbki <xref:System.ServiceModel.Channels.ChannelFactoryBase.GetProperty%2A> zapewniające dostęp do wersji kodera wiadomości wiadomości. Zastępuje również próbki <xref:System.ServiceModel.Channels.ChannelFactoryBase.OnClose%2A> tak, aby firma Microsoft zerwanie naszych wystąpienie <xref:System.ServiceModel.Channels.BufferManager> podczas przejścia komputera stanu.  
  
#### <a name="the-udp-output-channel"></a>Kanał wyjściowy UDP  
 `UdpOutputChannel` Implementuje <xref:System.ServiceModel.Channels.IOutputChannel>. Konstruktor sprawdza poprawność argumentów i tworzy miejsce docelowe <xref:System.Net.EndPoint> na podstawie obiektu <xref:System.ServiceModel.EndpointAddress> przekazanego pakietu.  
  
```csharp
this.socket = new Socket(this.remoteEndPoint.AddressFamily, SocketType.Dgram, ProtocolType.Udp);  
```  
  
 Kanał może zostać zamknięty, bezpiecznie lub ungracefully. Jeśli bezpiecznie zamknięcie kanału gniazda zostanie zamknięte, a połączenie jest nawiązywane w klasie podstawowej `OnClose` metody. Jeśli to zgłasza wyjątek, wywołuje metodę infrastruktury `Abort` zapewnienie kanał jest wyczyszczone.  
  
```csharp
this.socket.Close(0);  
```  
  
 Następnie wdrożymy `Send()` i `BeginSend()` / `EndSend()`. To dzieli się na dwóch głównych sekcji. Najpierw możemy serializować komunikat do tablicy typu byte.  
  
```csharp
ArraySegment<byte> messageBuffer = EncodeMessage(message);  
```  
  
 Firma Microsoft wyśle danych w sieci.  
  
```csharp
this.socket.SendTo(messageBuffer.Array, messageBuffer.Offset, messageBuffer.Count, SocketFlags.None, this.remoteEndPoint);  
```  
  
### <a name="the-udpchannellistener"></a>UdpChannelListener  
 "UdpChannelListener implementujący próbki jest pochodną <xref:System.ServiceModel.Channels.ChannelListenerBase> klasy. Użyto jednego gniazda UDP do odbierania datagramów. `OnOpen` Metody odbiera dane przy użyciu gniazda UDP w pętli asynchronicznego. Dane są następnie konwertowane na wiadomości przy użyciu platformy Kodowanie komunikatu.  
  
```csharp
message = MessageEncoderFactory.Encoder.ReadMessage(new ArraySegment<byte>(buffer, 0, count), bufferManager);  
```  
  
 Ponieważ ten sam kanał datagram reprezentuje komunikaty przychodzące z różnych źródeł, `UdpChannelListener` odbiornik singleton. Na większości, jeden aktywny <xref:System.ServiceModel.Channels.IChannel>'' skojarzone z tym odbiorniku naraz. Przykład generuje kolejnego tylko wtedy, gdy kanału, który jest zwracany przez `AcceptChannel` metody później został usunięty. Po otrzymaniu komunikatu jest dodawanych do kolejki w tym kanale singleton.  
  
#### <a name="udpinputchannel"></a>UdpInputChannel  
 `UdpInputChannel` Klasa implementuje `IInputChannel`. Składa się z kolejki wiadomości przychodzących, które jest wypełniana `UdpChannelListener`do gniazda. Komunikaty te są usuniętej przez `IInputChannel.Receive` metody.  
  
<a name="AddingABindingElement"></a>   
## <a name="adding-a-binding-element"></a>Dodawanie elementu powiązania  
 Teraz, kiedy są tworzone i fabryki kanałów, firma Microsoft musi ujawniać je do środowiska wykonawczego ServiceModel za pośrednictwem powiązania. Powiązanie to kolekcja elementów powiązań reprezentujący stosu komunikacji skojarzony z adresem usługi. Każdy element na stosie jest reprezentowana przez [ \<powiązania >](../../../../docs/framework/misc/binding.md) elementu.  
  
 W przykładzie jest element powiązania `UdpTransportBindingElement`, która jest pochodną <xref:System.ServiceModel.Channels.TransportBindingElement>. Zastępuje on następujące metody umożliwiające tworzenie fabryki skojarzony z powiązaniem naszych.  
  
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
  
 Zawiera także członków do klonowania `BindingElement` i zwracanie naszych schematu (soap.udp).  
  
## <a name="adding-metadata-support-for-a-transport-binding-element"></a>Dodawanie obsługi metadanych elementu powiązania transportu  
 Integrowanie naszych transportu w metadanych systemu, firma Microsoft obsługuje importu i eksportu zasad. Pozwala to Generowanie klientów naszych powiązania za pośrednictwem [narzędzie narzędzia metadanych elementu ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).  
  
### <a name="adding-wsdl-support"></a>Dodawanie obsługi WSDL  
 Element powiązania transportu w powiązaniu jest odpowiedzialny za eksportowanie i importowanie informacji o adresach w metadanych. Korzystając z powiązaniem SOAP, element powiązania transportu należy również eksportować poprawne transportu identyfikatora URI w metadanych.  
  
#### <a name="wsdl-export"></a>Eksportu WSDL  
 Aby wyeksportować informacje adresowania `UdpTransportBindingElement` implementuje `IWsdlExportExtension` interfejsu. `ExportEndpoint` Metoda dodaje poprawne informacje adresowania do portu WSDL.  
  
```csharp
if (context.WsdlPort != null)  
{  
    AddAddressToWsdlPort(context.WsdlPort, context.Endpoint.Address, encodingBindingElement.MessageVersion.Addressing);  
}  
```  
  
 `UdpTransportBindingElement` Implementacja `ExportEndpoint` metody Eksportuje również transportu identyfikatora URI gdy punkt końcowy korzysta z powiązaniem SOAP.  
  
```csharp
WsdlNS.SoapBinding soapBinding = GetSoapBinding(context, exporter);  
if (soapBinding != null)  
{  
    soapBinding.Transport = UdpPolicyStrings.UdpNamespace;  
}  
```  
  
#### <a name="wsdl-import"></a>Importu WSDL  
 Rozszerzenie importu WSDL systemu do obsługi importowanie adresów, możemy dodać następującą konfigurację do pliku konfiguracji dla Svcutil.exe jak pokazano w pliku Svcutil.exe.config.  
  
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
  
 Podczas uruchamiania Svcutil.exe, istnieją dwa sposoby uzyskania Svcutil.exe można załadować rozszerzenia importu WSDL:  
  
1.  Punkt Svcutil.exe naszych pliku konfiguracji za pomocą /SvcutilConfig:\<pliku >.  
  
2.  Dodaj sekcję konfiguracyjną do Svcutil.exe.config w tym samym katalogu co Svcutil.exe.  
  
 `UdpBindingElementImporter` Typ implementuje `IWsdlImportExtension` interfejsu. `ImportEndpoint` Metoda importuje adres z portu WSDL.  
  
```csharp
BindingElementCollection bindingElements = context.Endpoint.Binding.CreateBindingElements();  
TransportBindingElement transportBindingElement = bindingElements.Find<TransportBindingElement>();  
if (transportBindingElement is UdpTransportBindingElement)  
{  
    ImportAddress(context);  
}  
```  
  
### <a name="adding-policy-support"></a>Dodawanie obsługi zasad  
 Element powiązania niestandardowego można wyeksportować potwierdzenia zasad w powiązaniu WSDL dla punktu końcowego usługi Express możliwości tego elementu powiązania.  
  
#### <a name="policy-export"></a>Eksportowanie zasad  
 `UdpTransportBindingElement` Typ implementuje `IPolicyExportExtension` Aby dodać obsługę eksportowania zasady. W związku z tym `System.ServiceModel.MetadataExporter` obejmuje `UdpTransportBindingElement` generacji zasady dla żadnego powiązania, która go zawiera.  
  
 W `IPolicyExportExtension.ExportPolicy`, możemy Dodawanie potwierdzenie dla protokołów UDP i potwierdzenia innego Jeśli firma Microsoft pracuje w trybie multiemisji. Wynika to tryb multiemisji ma wpływ na sposób stosu komunikacji jest tworzony i w związku z tym musi być między obie strony.  
  
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
  
 Ponieważ elementy powiązania transportu niestandardowy jest odpowiedzialny za obsługę adresowania, `IPolicyExportExtension` implementacji na `UdpTransportBindingElement` również musi obsługiwać eksportowanie zasad potwierdzenia WS-Addressing odpowiednie wskazująca wersji WS-Addressing używana.  
  
```csharp
AddWSAddressingAssertion(context, encodingBindingElement.MessageVersion.Addressing);  
```  
  
#### <a name="policy-import"></a>Importowanie zasad  
 Rozszerzenie systemu zaimportować zasad, możemy Dodaj następującą konfigurację do pliku konfiguracji dla Svcutil.exe jak pokazano w pliku Svcutil.exe.config.  
  
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
  
 Następnie wdrożymy `IPolicyImporterExtension` z naszych zarejestrowanych klasy (`UdpBindingElementImporter`). W `ImportPolicy()`, firma Microsoft za pośrednictwem potwierdzenia w naszym przestrzeni nazw i przetworzyć te generowania transportu i sprawdź, czy multiemisji. Możemy również usunąć potwierdzenia, które chronimy z listy powiązania potwierdzenia. Ponownie uruchamiając Svcutil.exe, dostępne są dwie opcje do integracji:  
  
1.  Punkt Svcutil.exe naszych pliku konfiguracji za pomocą /SvcutilConfig:\<pliku >.  
  
2.  Dodaj sekcję konfiguracyjną do Svcutil.exe.config w tym samym katalogu co Svcutil.exe.  
  
<a name="AddingAStandardBinding"></a>   
## <a name="adding-a-standard-binding"></a>Dodawanie Powiązanie standardowe  
 Nasze element powiązania mogą być używane na dwa sposoby:  
  
-   Za pomocą niestandardowego powiązania: niestandardowego powiązania umożliwia użytkownikom tworzenie własnych powiązania na podstawie dowolnego zestawu elementów wiązania.  
  
-   Za pomocą powiązania dostarczane przez system, która zawiera naszych elementu powiązania. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]udostępnia wiele tych powiązań zdefiniowanych przez system, taką jak `BasicHttpBinding`, `NetTcpBinding`, i `WsHttpBinding`. Każdy z tych powiązań jest skojarzona z profilem dobrze zdefiniowany.  
  
 Przykład implementuje powiązanie profilu w `SampleProfileUdpBinding`, która jest pochodną <xref:System.ServiceModel.Channels.Binding>. `SampleProfileUdpBinding` Zawiera maksymalnie cztery elementy powiązania w nim: `UdpTransportBindingElement`, `TextMessageEncodingBindingElement CompositeDuplexBindingElement`, i `ReliableSessionBindingElement`.  
  
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
  
### <a name="adding-a-custom-standard-binding-importer"></a>Dodawanie niestandardowego powiązania importera Standard  
 Svcutil.exe i `WsdlImporter` typu domyślnie rozpoznaje i importuje powiązań zdefiniowanych przez system. W przeciwnym razie zaimportowany, ponieważ pobiera powiązania `CustomBinding` wystąpienia. Aby włączyć Svcutil.exe i `WsdlImporter` do zaimportowania `SampleProfileUdpBinding` `UdpBindingElementImporter` działa również jako importer niestandardowe Powiązanie standardowe.  
  
 Implementuje importera niestandardowe Powiązanie standardowe `ImportEndpoint` metoda `IWsdlImportExtension` interfejs do sprawdzenia `CustomBinding` wystąpienia zaimportowane z metadanych, aby zobaczyć, czy może on zostać wygenerowane przez określone powiązanie standardowe.  
  
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
  
 Ogólnie rzecz biorąc importera niestandardowego powiązania standardowa implementacja polega na sprawdzanie właściwości elementów importowanych powiązanie, aby sprawdzić, czy zostały zmienione tylko właściwości, które można ustawić przez powiązanie standardowe i inne właściwości są ich wartości domyślne. Podstawowe strategię implementowania importera Powiązanie standardowe jest do utworzenia wystąpienia Powiązanie standardowe, propagowanie powiązania właściwości z elementów wiążących wystąpienie Powiązanie standardowe obsługującej Powiązanie standardowe i porównania elementy z Powiązanie standardowe elementami importowanych powiązania.  
  
<a name="AddingConfigurationSupport"></a>   
## <a name="adding-configuration-support"></a>Dodawanie obsługi konfiguracji  
 Do udostępnienia naszych transportu za pomocą konfiguracji, musimy zaimplementować dwie sekcje konfiguracji. Pierwsza to `BindingElementExtensionElement` dla `UdpTransportBindingElement`. Jest to, aby `CustomBinding` implementacje może odwoływać się naszego elementu powiązania. Druga `Configuration` dla naszych `SampleProfileUdpBinding`.  
  
### <a name="binding-element-extension-element"></a>Element rozszerzenia elementu powiązania  
 Sekcja `UdpTransportElement` jest `BindingElementExtensionElement` który uwidacznia `UdpTransportBindingElement` do konfiguracji systemu. Z kilku podstawowych zastąpień definiujemy naszych nazwę sekcji konfiguracji, naszych elementu powiązania oraz sposobu tworzenia naszych elementu powiązania. Firma Microsoft można zarejestrować naszej sekcji rozszerzeń w pliku konfiguracji, jak pokazano w poniższym kodzie.  
  
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
  
 Rozszerzenia mogą być przywoływane z niestandardowego powiązania do użycia jako transportu UDP.  
  
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
 Sekcja `SampleProfileUdpBindingCollectionElement` jest `StandardBindingCollectionElement` który uwidacznia `SampleProfileUdpBinding` do konfiguracji systemu. Delegowane do zbiorczego wdrożenia `SampleProfileUdpBindingConfigurationElement`, która jest pochodną `StandardBindingElement`. `SampleProfileUdpBindingConfigurationElement` Ma właściwości, które odpowiadają właściwościom na `SampleProfileUdpBinding`i funkcji do mapowania z `ConfigurationElement` powiązania. Ponadto Zastąp `OnApplyConfiguration` metody w naszym `SampleProfileUdpBinding`, jak pokazano w poniższym kodzie próbki.  
  
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
  
 Aby zarejestrować ten program obsługi przy użyciu systemu konfiguracji, dodania do pliku konfiguracji związanych z poniższej sekcji.  
  
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
  
 Można go następnie odwoływać z sekcji konfiguracji serviceModel.  
  
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
  
## <a name="the-udp-test-service-and-client"></a>Usługa badania UDP i klienta  
 Za pomocą tego transportu przykładowy kod testu jest dostępny w katalogach UdpTestService i UdpTestClient. Kod usługi składa się z dwóch testów — jeden test ustawia punktów końcowych i powiązania z kodu i innych zrobi to za pomocą konfiguracji. Zarówno testy Użyj dwa punkty końcowe. Jeden punkt końcowy używa `SampleUdpProfileBinding` z [ \<reliableSession >](http://msdn.microsoft.com/en-us/9c93818a-7dfa-43d5-b3a1-1aafccf3a00b) ustawioną `true`. Innych punktów końcowych używa niestandardowego powiązania z `UdpTransportBindingElement`. Jest to równoważne przy użyciu `SampleUdpProfileBinding` z [ \<reliableSession >](http://msdn.microsoft.com/en-us/9c93818a-7dfa-43d5-b3a1-1aafccf3a00b) ustawioną `false`. Zarówno testy Tworzenie usługi, dodawanie punktu końcowego dla każdego powiązania, otwórz usługę i poczekaj, aż użytkownik trafienie ENTER przed zamknięciem usługi.  
  
 Podczas uruchamiania aplikacji testu usługi powinny być widoczne następujące dane wyjściowe.  
  
```console
Testing Udp From Code.  
Service is started from code...  
Press <ENTER> to terminate the service and start service from config...  
```  
  
 Następnie można uruchomić aplikacji klienckiej testu dla opublikowanych punktów końcowych. Aplikacja testowa klienta tworzy klienta dla każdego punktu końcowego i wysyła komunikaty pięciu do każdego punktu końcowego. Następujące dane wyjściowe znajduje się na kliencie.  
  
```console
Testing Udp From Imported Files Generated By SvcUtil.  
0  
3  
6  
9  
12  
Press <ENTER> to complete test.  
```  
  
 Poniżej znajduje się pełne dane wyjściowe w usłudze.  
  
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
  
 Aby uruchomić aplikację klienta przed opublikowane za pomocą konfiguracji punktów końcowych, kliknij przycisk ENTER w usłudze, a następnie ponownie uruchom klienta testowego. Następujące dane wyjściowe powinny być widoczne w usłudze.  
  
```console
Testing Udp From Config.  
Service is started from config...  
Press <ENTER> to terminate the service and exit...  
```  
  
 Ponowne uruchomienie klienta daje takie same jak w poprzednim.  
  
 Można ponownie wygenerować kod klienta i konfiguracji przy użyciu Svcutil.exe, uruchom aplikację usługi, a następnie uruchom następujące Svcutil.exe z katalogu głównego próbki.  
  
```console
svcutil http://localhost:8000/udpsample/ /reference:UdpTranport\bin\UdpTransport.dll /svcutilConfig:svcutil.exe.config  
```  
  
 Należy pamiętać, że Svcutil.exe nie generuje konfiguracji rozszerzenia powiązania dla `SampleProfileUdpBinding`, więc należy ją dodać ręcznie.  
  
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
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, kompilacji, a następnie uruchom próbki  
  
1.  Postępuj zgodnie z instrukcjami w celu skompilowania rozwiązania, [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
2.  Aby uruchomić przykładowy w konfiguracji pojedynczej lub między komputerami, postępuj zgodnie z instrukcjami w [uruchamiania przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
3.  Zapoznaj się z poprzedniej sekcji "UDP testu i klient usługi".  
  
> [!IMPORTANT]
>  Próbki mogą być zainstalowane na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Transport\Udp`
