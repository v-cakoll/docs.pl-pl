---
title: "Kanał dzielący na fragmenty"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e4d53379-b37c-4b19-8726-9cc914d5d39f
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 2fe0ad62a55c6536b0054aa23ac556b896b02be4
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="chunking-channel"></a>Kanał dzielący na fragmenty
Podczas wysyłania dużych wiadomości przy użyciu [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)], często jest to pożądane, aby ograniczyć ilość pamięci użytej do zbuforowania tych wiadomości. Możliwe rozwiązanie jest strumienia treści wiadomości (przy założeniu, że większość danych znajduje się w treści). Jednak niektóre protokoły wymagają buforowanie cały komunikat. Niezawodna obsługa komunikatów i zabezpieczeń są dwa takie przykłady. Innym rozwiązaniem możliwe jest do dzielenia dużych wiadomość na mniejsze wiadomości nazywanej fragmentów, wysłać jednym fragmencie tych fragmentów w czasie i Przywróć dużych komunikatów po stronie odbierającej. Sama aplikacja może wykonać tego podziału i cofnąć podziału lub można użyć niestandardowego kanału Aby wykonać to zadanie. Segmentu przykład kanału pokazuje, jak protokołu niestandardowego lub warstwowego kanału może służyć do podziału i cofnąć podziału dowolnie dużą wiadomości.  
  
 Podziału powinien zawsze można zastosować tylko wtedy, gdy skonstruowane cały komunikat do wysłania. Segmentu kanału powinna być zawsze warstwie poniżej kanału zabezpieczeń i kanał niezawodnej sesji.  
  
> [!NOTE]
>  Procedury i kompilacji instrukcje dotyczące instalacji dla tego przykładu znajdują się na końcu tego tematu.  
  
> [!IMPORTANT]
>  Próbki mogą być zainstalowane na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Channels\ChunkingChannel`  
  
## <a name="chunking-channel-assumptions-and-limitations"></a>Segmentu założenia kanału i ograniczenia  
  
### <a name="message-structure"></a>Komunikat — struktura  
 Kanał segmentu zakłada następującą strukturę komunikatu dla komunikatów do fragmentarycznego można:  
  
```xml  
<soap:Envelope ...>  
  <!-- headers -->  
  <soap:Body>  
    <operationElement>  
      <paramElement>data to be chunked</paramElement>  
    </operationElement>  
  </soap:Body>  
</soap:Envelope>  
```  
  
 Podczas korzystania z modelu ServiceModel, należy Zwiń operacji, mających 1 parametr wejściowy jest zgodne z tym kształtem komunikatu dla ich komunikatu wejściowego. Podobnie kontrakt operacji, które ma 1 parametr danych wyjściowych ani zwracanej wartości są zgodne z komunikatu dla komunikatów ich dane wyjściowe tego kształtu. Poniżej przedstawiono przykłady takich operacji:  
  
```  
[ServiceContract]  
interface ITestService  
{  
    [OperationContract]  
    Stream EchoStream(Stream stream);  
  
    [OperationContract]  
    Stream DownloadStream();  
  
    [OperationContract(IsOneWay = true)]  
    void UploadStream(Stream stream);  
}  
```  
  
### <a name="sessions"></a>Kategoria Sessions  
 Kanał segmentu wymaga wiadomości dostarczanych tylko raz w uporządkowanego dostarczenia komunikatów (fragmentów). Oznacza to, że źródłowy stosu kanału musi być sesyjnych. Można podać sesji transportu (na przykład transportu TCP) lub przez protokół zamykania kanał (na przykład ReliableSession kanał).  
  
### <a name="asynchronous-send-and-receive"></a>Asynchronicznego wysyłania i odbierania  
 Asynchronous wysyłania i odbierania metod nie są zaimplementowane w tej wersji segmentu przykład kanału.  
  
## <a name="chunking-protocol"></a>Protokół segmentu  
 Kanał segmentu Określa protokół, który wskazuje początek i koniec serii fragmentów, a także numer sekwencyjny każdego fragmentu. Następujące komunikaty przykładzie trzy pokazują start, fragmentów i na końcu wiadomości z komentarzami, które opisują kluczowe aspekty.  
  
### <a name="start-message"></a>Komunikat uruchomienia  
  
```xml  
<s:Envelope xmlns:a="http://www.w3.org/2005/08/addressing"   
            xmlns:s="http://www.w3.org/2003/05/soap-envelope">  
  <s:Header>  
<!—Original message action is replaced with a chunking-specific action. -->  
    <a:Action s:mustUnderstand="1">http://samples.microsoft.com/chunkingAction</a:Action>  
<!--  
Original message is assigned a unique id that is transmitted   
in a MessageId header. Note that this is different from the WS-Addressing MessageId header.  
-->  
    <MessageId s:mustUnderstand="1" xmlns="http://samples.microsoft.com/chunking">  
53f183ee-04aa-44a0-b8d3-e45224563109  
</MessageId>  
<!--  
ChunkingStart header signals the start of a chunked message.  
-->  
    <ChunkingStart s:mustUnderstand="1" i:nil="true" xmlns:i="http://www.w3.org/2001/XMLSchema-instance" xmlns="http://samples.microsoft.com/chunking" />  
<!--  
Original message action is transmitted in OriginalAction.  
This is required to re-create the original message on the other side.  
-->  
    <OriginalAction xmlns="http://samples.microsoft.com/chunking">  
http://tempuri.org/ITestService/EchoStream  
    </OriginalAction>  
   <!--  
    All original message headers are included here.  
   -->  
  </s:Header>  
  <s:Body>  
<!--  
Chunking assumes this structure of Body content:  
<element>  
  <childelement>large data to be chunked<childelement>  
</element>  
The start message contains just <element> and <childelement> without  
the data to be chunked.  
-->  
    <EchoStream xmlns="http://tempuri.org/">  
      <stream />  
    </EchoStream>  
  </s:Body>  
</s:Envelope>  
```  
  
### <a name="chunk-message"></a>Komunikat fragmentu  
  
```xml  
<s:Envelope   
  xmlns:a="http://www.w3.org/2005/08/addressing"   
  xmlns:s="http://www.w3.org/2003/05/soap-envelope">  
  <s:Header>  
   <!--  
    All chunking protocol messages have this action.  
   -->  
    <a:Action s:mustUnderstand="1">  
      http://samples.microsoft.com/chunkingAction  
    </a:Action>  
<!--  
Same as MessageId in the start message. The GUID indicates which original message this chunk belongs to.  
-->  
    <MessageId s:mustUnderstand="1"   
               xmlns="http://samples.microsoft.com/chunking">  
      53f183ee-04aa-44a0-b8d3-e45224563109  
    </MessageId>  
<!--  
The sequence number of the chunk.  
This number restarts at 1 with each new sequence of chunks.  
-->  
    <ChunkNumber s:mustUnderstand="1"   
                 xmlns="http://samples.microsoft.com/chunking">  
      1096  
    </ChunkNumber>  
  </s:Header>  
  <s:Body>  
<!--  
The chunked data is wrapped in a chunk element.  
The encoding of this data (and the entire message)   
depends on the encoder used. The chunking channel does not mandate an encoding.  
-->  
    <chunk xmlns="http://samples.microsoft.com/chunking">  
kfSr2QcBlkHTvQ==  
    </chunk>  
  </s:Body>  
</s:Envelope>  
```  
  
### <a name="end-message"></a>Komunikat  
  
```xml  
<s:Envelope xmlns:a="http://www.w3.org/2005/08/addressing"   
            xmlns:s="http://www.w3.org/2003/05/soap-envelope">  
  <s:Header>  
    <a:Action s:mustUnderstand="1">  
      http://samples.microsoft.com/chunkingAction  
    </a:Action>  
<!--  
Same as MessageId in the start message. The GUID indicates which original message this chunk belongs to.  
-->  
    <MessageId s:mustUnderstand="1"   
               xmlns="http://samples.microsoft.com/chunking">  
      53f183ee-04aa-44a0-b8d3-e45224563109  
    </MessageId>  
<!--  
ChunkingEnd header signals the end of a chunk sequence.  
-->  
    <ChunkingEnd s:mustUnderstand="1" i:nil="true"   
                 xmlns:i="http://www.w3.org/2001/XMLSchema-instance"   
                 xmlns="http://samples.microsoft.com/chunking" />  
<!--  
ChunkingEnd messages have a sequence number.  
-->  
    <ChunkNumber s:mustUnderstand="1"   
                 xmlns="http://samples.microsoft.com/chunking">  
      79  
    </ChunkNumber>  
  </s:Header>  
  <s:Body>  
<!--  
The ChunkingEnd message has the same <element><childelement> structure  
as the ChunkingStart message.  
-->  
    <EchoStream xmlns="http://tempuri.org/">  
      <stream />  
    </EchoStream>  
  </s:Body>  
</s:Envelope>  
```  
  
## <a name="chunking-channel-architecture"></a>Architektura kanału segmentu  
 Kanał segmentu jest `IDuplexSessionChannel` , na wysokim poziomie następujący architektura typowe kanału. Brak `ChunkingBindingElement` który można tworzyć `ChunkingChannelFactory` i `ChunkingChannelListener`. `ChunkingChannelFactory` Tworzy wystąpienia `ChunkingChannel` gdy otrzyma monit. `ChunkingChannelListener` Tworzy wystąpienia `ChunkingChannel` po zaakceptowaniu nowy kanał wewnętrzny. `ChunkingChannel` Jest odpowiedzialny za wysyłanie i odbieranie wiadomości.  
  
 Na następny poziom w dół `ChunkingChannel` opiera się na kilka składników do implementowania protokołu segmentu. Po stronie wysyłającej kanału używa niestandardowego `XmlDictionaryWriter` o nazwie `ChunkingWriter` wykonuje rzeczywiste podziału. `ChunkingWriter`wysyła przy użyciu kanału wewnętrzny bezpośrednio fragmentów. Przy użyciu niestandardowego `XmlDictionaryWriter` umożliwia firmie Microsoft w celu wysłania fragmentów, jak jest zapisywana duża treści oryginalnej wiadomości. Oznacza to, że firma Microsoft nie buforowania całego oryginalnej wiadomości.  
  
 ![Kanał dzielący na fragmenty](../../../../docs/framework/wcf/samples/media/chunkingchannel1.gif "ChunkingChannel1")  
  
 Po stronie odbierania `ChunkingChannel` pobiera komunikaty z kanału wewnętrzny i przekazuje je do niestandardowego `XmlDictionaryReader` o nazwie `ChunkingReader`, który reconstitutes z przychodzącego fragmentów oryginalnej wiadomości. `ChunkingChannel`opakowuje to `ChunkingReader` w niestandardowej `Message` wdrożenia o nazwie `ChunkingMessage` i zwraca ten komunikat do warstwy powyżej. Ta kombinacja `ChunkingReader` i `ChunkingMessage` pozwala cofnąć bryłkach oryginalnego treść komunikatu zgodnie z są odczytywane przez warstwę powyżej zamiast buforu całej treści oryginalnej wiadomości. `ChunkingReader`ma kolejkę, gdzie buforuje przychodzące fragmentów maksymalnie można skonfigurować maksymalną liczbę buforowanych fragmentów. Po osiągnięciu tego limitu maksymalnej czytnik czeka na komunikaty, aby być opróżnione z kolejki przez warstwę powyżej (oznacza to, odczytując tylko z treści oryginalnej wiadomości) lub do momentu odbierania maksymalną osiągnięciu limitu czasu.  
  
 ![Kanał dzielący na fragmenty](../../../../docs/framework/wcf/samples/media/chunkingchannel2.gif "ChunkingChannel2")  
  
## <a name="chunking-programming-model"></a>Model programowania podziału  
 Deweloperzy usług można określić wiadomości, które mają być fragmentaryczne stosując `ChunkingBehavior` atrybutu z operacjami w ramach umowy. Udostępnia atrybut `AppliesTo` właściwość, która umożliwia deweloperowi określić, czy podziału stosuje się do komunikatu wejściowego, komunikatu wyjściowego lub obu. W poniższym przykładzie przedstawiono użycie `ChunkingBehavior` atrybutu:  
  
```  
[ServiceContract]  
interface ITestService  
{  
    [OperationContract]  
    [ChunkingBehavior(ChunkingAppliesTo.Both)]  
    Stream EchoStream(Stream stream);  
  
    [OperationContract]  
    [ChunkingBehavior(ChunkingAppliesTo.OutMessage)]  
    Stream DownloadStream();  
  
    [OperationContract(IsOneWay=true)]  
    [ChunkingBehavior(ChunkingAppliesTo.InMessage)]  
    void UploadStream(Stream stream);  
  
}  
```  
  
 Z tego modelu programowania `ChunkingBindingElement` kompiluje listę akcji zidentyfikować komunikaty, aby być fragmentaryczne identyfikatorów URI. Akcja każdego komunikatu wychodzącego jest porównywana z tej listy, aby określić, czy fragmentaryczne też wysyłane bezpośrednio wiadomości.  
  
## <a name="implementing-the-send-operation"></a>Implementowanie operacji wysyłania  
 Na wysokim poziomie operacji wysyłania najpierw sprawdza, czy wiadomości wychodzącej musi być fragmentaryczne i, jeśli nie, wysyła wiadomość bezpośrednio za pomocą kanału wewnętrzny.  
  
 Jeśli wiadomość musi fragmentaryczne, Wyślij tworzy nowy `ChunkingWriter` i wywołania `WriteBodyContents` komunikatu wychodzącego przekazanie jej przez to `ChunkingWriter`. `ChunkingWriter` , A następnie jest podziału komunikatów (w tym kopiowanie oryginalne nagłówki wiadomości na komunikat uruchomienia fragmentu) i wysyła fragmentów za pomocą kanału wewnętrzny.  
  
 Kilka szczegóły warto zauważyć:  
  
-   Wyślij pierwsze wywołania `ThrowIfDisposedOrNotOpened` zapewnienie `CommunicationState` jest otwarty.  
  
-   Wysyłanie są synchronizowane, mogą być wysyłane tylko jeden wiadomości w czasie dla każdej sesji. Brak `ManualResetEvent` o nazwie `sendingDone` zresetowania po wysłaniu wiadomości podzielony. Wysłany komunikat fragmentu zakończenia tego zdarzenia jest ustawiona. Metody Send oczekuje dla tego zdarzenia, należy ustawić przed ponowną próbą wysłania wychodzących.  
  
-   Wyślij blokad `CommunicationObject.ThisLock` zapobiegające synchronizacji zmian stanu podczas wysyłania. Zobacz <xref:System.ServiceModel.Channels.CommunicationObject> dokumentację, aby uzyskać więcej informacji na temat <xref:System.ServiceModel.Channels.CommunicationObject> stanów i komputera stanu.  
  
-   Limit czasu przekazany do wysyłania jest używany jako limit czasu dla operacji wysyłania całego, która obejmuje wszystkie fragmenty wysyłanie.  
  
-   Niestandardowa `XmlDictionaryWriter` projektu została wybrana, aby uniknąć buforowanie całej treści oryginalnej wiadomości. Czy możemy uzyskać `XmlDictionaryReader` przy użyciu treści `message.GetReaderAtBodyContents` cały będą buforowane. Zamiast tego mamy niestandardowego `XmlDictionaryWriter` przekazywany do `message.WriteBodyContents`. Jako wiadomości wywołania WriteBase64 na składnik zapisywania, moduł zapisujący pakietów się fragmentów w komunikatach i wysyła je przy użyciu kanału wewnętrzny. Bloki WriteBase64 momentu wysłania fragmentów.  
  
## <a name="implementing-the-receive-operation"></a>Implementowanie operacji odbierania  
 Na wysokim poziomie operacji odbierania najpierw sprawdza, czy komunikat przychodzący nie jest `null` i że jego działanie jest `ChunkingAction`. Jeśli nie spełnia kryteriów zarówno, zwracany jest komunikat niezmienione Receive. W przeciwnym razie Receive tworzy nowy `ChunkingReader` i nowy `ChunkingMessage` otaczający go (wywołując `GetNewChunkingMessage`). Przed powrotem przez nowych `ChunkingMessage`, Receive korzysta z puli wątków do wykonania `ReceiveChunkLoop`, które wywołuje `innerChannel.Receive` w pętli i ręce poza fragmentów do `ChunkingReader` aż do zakończenia fragmentu komunikat jest odbierany lub jest osiągnęła limit czasu odbioru.  
  
 Kilka szczegóły warto zauważyć:  
  
-   Jak wysyłania, odbierania połączeń pierwszy `ThrowIfDisposedOrNotOepned` zapewnienie `CommunicationState` jest otwarty.  
  
-   Wyświetlany jest synchronizowane, tak że tylko jeden komunikat może zostać odebrany w czasie z sesji. Jest to szczególnie ważne, ponieważ po odebraniu komunikatu fragmentu start, wszystkie kolejne odebrane wiadomości powinny być fragmentów w ramach nowej sekwencji fragmentu do momentu otrzymania wiadomości końcowego fragmentu. Odbieranie nie może pobierać komunikaty z kanału wewnętrzny, dopóki wszystkie fragmenty należące do komunikatu obecnie cofnąć trwa fragmentaryczne są odbierane. W tym celu odbierania używa `ManualResetEvent` o nazwie `currentMessageCompleted`, która ma wartość, gdy komunikat fragmentu zakończenia jest odbierany i zresetować po odebraniu nowego komunikatu fragmentu rozpoczęcia.  
  
-   W przeciwieństwie do wysyłania Receive nie zapobiega przejścia zsynchronizowanie podczas odbierania. Na przykład Zamknij można wywołać podczas odbierania i czeka, aż do ukończenia oczekującej receive oryginalnej wiadomości lub osiągnięto wartość określonego limitu czasu.  
  
-   Limit czasu przekazany do odbierania jest używany jako limitu czasu dla całego odbierania operacja, która obejmuje wszystkie fragmenty odbierania.  
  
-   Jeśli warstwy, który wykorzystuje komunikat zajmuje treść komunikatu z szybkością mniejszy niż liczba komunikatów przychodzących fragmentu, `ChunkingReader` buforuje tych fragmentów przychodzące do limitu określonego przez `ChunkingBindingElement.MaxBufferedChunks`. Po osiągnięciu tego limitu już fragmentów są pobierane z dolnej warstwy, aż do buforowanego fragmentu jest używany lub osiągnięto limit czasu odbioru.  
  
## <a name="communicationobject-overrides"></a>Zastąpienia CommunicationObject  
  
### <a name="onopen"></a>Zdarzenia  
 `OnOpen`wywołania `innerChannel.Open` otworzyć kanału wewnętrzny.  
  
### <a name="onclose"></a>OnClose  
 `OnClose`najpierw ustawia `stopReceive` do `true` sygnalizują oczekujące `ReceiveChunkLoop` zatrzymania. Następnie czeka na `receiveStopped``ManualResetEvent`, która jest ustawiana w przypadku `ReceiveChunkLoop` zatrzymuje. Zakładając, że `ReceiveChunkLoop` zatrzymuje się przed upływem określonego limitu czasu `OnClose` wywołania `innerChannel.Close` pozostałych limitu czasu.  
  
### <a name="onabort"></a>OnAbort  
 `OnAbort`wywołania `innerChannel.Abort` przerwania wewnętrzny kanału. Jeśli istnieje oczekujące `ReceiveChunkLoop` pobiera wyjątku z oczekujących `innerChannel.Receive` wywołania.  
  
### <a name="onfaulted"></a>OnFaulted  
 `ChunkingChannel` Nie wymaga specjalnego zachowania, gdy kanał komunikacji niezawodnej to `OnFaulted` nie zostanie zastąpiona.  
  
## <a name="implementing-channel-factory"></a>Implementowanie fabryki kanałów  
 `ChunkingChannelFactory` Odpowiedzialną za tworzenie wystąpień `ChunkingDuplexSessionChannel` i kaskadowych zmian stanu do wewnętrzna fabryka kanałów.  
  
 `OnCreateChannel`używa wewnętrzna fabryka kanałów w celu utworzenia `IDuplexSessionChannel` wewnętrzny kanału. Następnie tworzy nowy `ChunkingDuplexSessionChannel` przekazanie jej przez ten kanał wewnętrzny wraz z listy można fragmentaryczne akcje wiadomości i maksymalną liczbę fragmentów do zbuforowania podczas odbierania. Listę można fragmentaryczne akcje wiadomości i maksymalną liczbę fragmentów, aby buforować są dwa parametry przekazywane do `ChunkingChannelFactory` w jego konstruktora. Sekcję `ChunkingBindingElement` w tym artykule opisano, skąd pochodzą te wartości.  
  
 `OnOpen`, `OnClose`, `OnAbort` i ich odpowiedniki asynchroniczne wywołanie odpowiedniej metody przejścia stanu na wewnętrzna fabryka kanałów.  
  
## <a name="implementing-channel-listener"></a>Implementowanie odbiornika kanałów  
 `ChunkingChannelListener` Jest otokę odbiornika kanałów wewnętrzny. Jej główną funkcją, oprócz delegata wywołania tego odbiornika kanału wewnętrzny jest opakowywać nowych `ChunkingDuplexSessionChannels` wokół kanały akceptowane z odbiornika kanałów wewnętrzny. Jest to wykonywane w `OnAcceptChannel` i `OnEndAcceptChannel`. Nowo utworzony `ChunkingDuplexSessionChannel` jest przekazywany wewnętrzny kanału oraz inne parametry opisane wcześniej.  
  
## <a name="implementing-binding-element-and-binding"></a>Wdrażanie elementu powiązania i powiązania  
 `ChunkingBindingElement`jest odpowiedzialny za tworzenie `ChunkingChannelFactory` i `ChunkingChannelListener`. `ChunkingBindingElement` Sprawdza, czy T w `CanBuildChannelFactory` \<T > i `CanBuildChannelListener` \<T > jest typu `IDuplexSessionChannel` (tylko kanał obsługiwane przez kanał segmentu) i inne elementy powiązania powiązanie obsługuje to Typ kanału.  
  
 `BuildChannelFactory`\<T > najpierw sprawdza, czy typ kanału żądanej mogą być wbudowane, a następnie pobiera listę komunikatów akcje fragmentarycznego można. Aby uzyskać więcej informacji zobacz sekcję poniżej. Następnie tworzy nowy `ChunkingChannelFactory` przekazanie jej wewnętrzna fabryka kanałów (zwrócony z `context.BuildInnerChannelFactory<IDuplexSessionChannel>`), listy Akcje wiadomości i maksymalną liczbę fragmentów do buforowania. Maksymalna liczba fragmentów pochodzi z właściwość o nazwie `MaxBufferedChunks` udostępnianych przez `ChunkingBindingElement`.  
  
 `BuildChannelListener<T>`implementacją podobne do tworzenia `ChunkingChannelListener` i przekazanie jej przez odbiornik kanału wewnętrzny.  
  
 Brak powiązania przykład zawarty w tym przykładzie o nazwie `TcpChunkingBinding`. To powiązanie składa się z dwóch elementów powiązania: `TcpTransportBindingElement` i `ChunkingBindingElement`. Oprócz udostępnianie `MaxBufferedChunks` właściwość powiązania także ustawia niektóre `TcpTransportBindingElement` właściwości, takie jak `MaxReceivedMessageSize` (ustawia ją na `ChunkingUtils.ChunkSize` + 100 KB bajtów dla nagłówków).  
  
 `TcpChunkingBinding`implementuje również `IBindingRuntimePreferences` i zwraca wartość true z `ReceiveSynchronously` metody wskazujący, że są wykonywane tylko synchroniczne wywołania Receive.  
  
### <a name="determining-which-messages-to-chunk"></a>Określanie, które wiadomości do fragmentu  
 Kanał segmentu chunks tylko komunikaty identyfikowane za pomocą `ChunkingBehavior` atrybutu. `ChunkingBehavior` Klasa implementuje `IOperationBehavior` i jest implementowane przez wywołanie metody `AddBindingParameter` metody. W przypadku tej metody `ChunkingBehavior` sprawdza, czy wartość jego `AppliesTo` właściwości (`InMessage`, `OutMessage` lub obie) do określenia wiadomości, które powinny być fragmentaryczne. Następnie pobiera działania każdego z tych wiadomości (z kolekcji wiadomości na `OperationDescription`) i dodaje go do kolekcji ciągów, zawartych w wystąpienia `ChunkingBindingParameter`. Dodaje następnie to `ChunkingBindingParameter` w udostępnionej klasie `BindingParameterCollection`.  
  
 To `BindingParameterCollection` jest przekazywany wewnątrz `BindingContext` do każdego elementu powiązania w powiązaniu podczas tworzenia elementu powiązania fabryki kanału lub odbiornika kanałów. `ChunkingBindingElement`w implementacji `BuildChannelFactory<T>` i `BuildChannelListener<T>` ściągnięcia to `ChunkingBindingParameter` z `BindingContext’`s `BindingParameterCollection`. Zbiór działań zawartych w `ChunkingBindingParameter` są następnie przekazywane do `ChunkingChannelFactory` lub `ChunkingChannelListener`, który z kolei przekazuje go do `ChunkingDuplexSessionChannel`.  
  
## <a name="running-the-sample"></a>Uruchomiona próbki  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, kompilacji, a następnie uruchom próbki  
  
1.  Zainstaluj [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 4.0 za pomocą następującego polecenia.  
  
    ```  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2.  Upewnij się, że wykonano procedurę [jednorazowego procedurę instalacji dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
3.  Postępuj zgodnie z instrukcjami w celu skompilowania rozwiązania, [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
4.  Aby uruchomić przykładowy w konfiguracji pojedynczej lub między komputerami, postępuj zgodnie z instrukcjami w [uruchamiania przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
5.  Uruchom najpierw Service.exe, uruchom Client.exe i obejrzyj oba okna konsoli dla danych wyjściowych.  
  
 Podczas uruchamiania próbki, oczekiwano następujących danych wyjściowych.  
  
 Klient:  
  
```  
Press enter when service is available  
  
 > Sent chunk 1 of message 867c1fd1-d39e-4be1-bc7b-32066d7ced10  
 > Sent chunk 2 of message 867c1fd1-d39e-4be1-bc7b-32066d7ced10  
 > Sent chunk 3 of message 867c1fd1-d39e-4be1-bc7b-32066d7ced10  
 > Sent chunk 4 of message 867c1fd1-d39e-4be1-bc7b-32066d7ced10  
 > Sent chunk 5 of message 867c1fd1-d39e-4be1-bc7b-32066d7ced10  
 > Sent chunk 6 of message 867c1fd1-d39e-4be1-bc7b-32066d7ced10  
 > Sent chunk 7 of message 867c1fd1-d39e-4be1-bc7b-32066d7ced10  
 > Sent chunk 8 of message 867c1fd1-d39e-4be1-bc7b-32066d7ced10  
 > Sent chunk 9 of message 867c1fd1-d39e-4be1-bc7b-32066d7ced10  
 > Sent chunk 10 of message 867c1fd1-d39e-4be1-bc7b-32066d7ced10  
 < Received chunk 1 of message 5b226ad5-c088-4988-b737-6a565e0563dd  
 < Received chunk 2 of message 5b226ad5-c088-4988-b737-6a565e0563dd  
 < Received chunk 3 of message 5b226ad5-c088-4988-b737-6a565e0563dd  
 < Received chunk 4 of message 5b226ad5-c088-4988-b737-6a565e0563dd  
 < Received chunk 5 of message 5b226ad5-c088-4988-b737-6a565e0563dd  
 < Received chunk 6 of message 5b226ad5-c088-4988-b737-6a565e0563dd  
 < Received chunk 7 of message 5b226ad5-c088-4988-b737-6a565e0563dd  
 < Received chunk 8 of message 5b226ad5-c088-4988-b737-6a565e0563dd  
 < Received chunk 9 of message 5b226ad5-c088-4988-b737-6a565e0563dd  
 < Received chunk 10 of message 5b226ad5-c088-4988-b737-6a565e0563dd  
```  
  
 Serwer:  
  
```  
Service started, press enter to exit  
 < Received chunk 1 of message 867c1fd1-d39e-4be1-bc7b-32066d7ced10  
 < Received chunk 2 of message 867c1fd1-d39e-4be1-bc7b-32066d7ced10  
 < Received chunk 3 of message 867c1fd1-d39e-4be1-bc7b-32066d7ced10  
 < Received chunk 4 of message 867c1fd1-d39e-4be1-bc7b-32066d7ced10  
 < Received chunk 5 of message 867c1fd1-d39e-4be1-bc7b-32066d7ced10  
 < Received chunk 6 of message 867c1fd1-d39e-4be1-bc7b-32066d7ced10  
 < Received chunk 7 of message 867c1fd1-d39e-4be1-bc7b-32066d7ced10  
 < Received chunk 8 of message 867c1fd1-d39e-4be1-bc7b-32066d7ced10  
 < Received chunk 9 of message 867c1fd1-d39e-4be1-bc7b-32066d7ced10  
 < Received chunk 10 of message 867c1fd1-d39e-4be1-bc7b-32066d7ced10  
 > Sent chunk 1 of message 5b226ad5-c088-4988-b737-6a565e0563dd  
 > Sent chunk 2 of message 5b226ad5-c088-4988-b737-6a565e0563dd  
 > Sent chunk 3 of message 5b226ad5-c088-4988-b737-6a565e0563dd  
 > Sent chunk 4 of message 5b226ad5-c088-4988-b737-6a565e0563dd  
 > Sent chunk 5 of message 5b226ad5-c088-4988-b737-6a565e0563dd  
 > Sent chunk 6 of message 5b226ad5-c088-4988-b737-6a565e0563dd  
 > Sent chunk 7 of message 5b226ad5-c088-4988-b737-6a565e0563dd  
 > Sent chunk 8 of message 5b226ad5-c088-4988-b737-6a565e0563dd  
 > Sent chunk 9 of message 5b226ad5-c088-4988-b737-6a565e0563dd  
 > Sent chunk 10 of message 5b226ad5-c088-4988-b737-6a565e0563dd  
```  
  
## <a name="see-also"></a>Zobacz też
