---
title: Kanał dzielący na fragmenty
ms.date: 03/30/2017
ms.assetid: e4d53379-b37c-4b19-8726-9cc914d5d39f
ms.openlocfilehash: 9572ad6f88786af34252cea1f3c62d5067257b8b
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43661194"
---
# <a name="chunking-channel"></a>Kanał dzielący na fragmenty
Podczas wysyłania dużych komunikatów za pomocą usługi Windows Communication Foundation (WCF), często jest pożądane, aby ograniczyć ilość pamięci używana do buforowania te komunikaty. Jedno z możliwych rozwiązań jest przesyłanie strumieniowe treść wiadomości (przy założeniu, że duża część danych znajduje się w treści). Jednak niektóre protokoły wymagają buforowanie cały komunikat. Niezawodna obsługa komunikatów i zabezpieczenia są dwa takie przykłady. Inne możliwe rozwiązanie jest dzielenia dużych wiadomość na mniejsze wiadomości o nazwie fragmentów, Wyślij jednym fragmencie tych fragmentów w danym momencie i odtworzenia dużych komunikatów po stronie odbierającej. Sama aplikacja może wykonać tego segmentu i cofnąć segmentu lub użyć niestandardowy kanał to zrobić. Segmentu przykład kanału pokazuje, jak niestandardowego protokołu lub warstwowej kanału może służyć do segmentu i cofnąć segmentu arbitralnie dużych komunikatów.  
  
 Dzielący na fragmenty należy zawsze można zastosować tylko wtedy, gdy został skonstruowany cały komunikat do wysłania. Kanał segmentu powinien zawsze warstwowe w poniżej kanału zabezpieczeń i kanał niezawodnej sesji.  
  
> [!NOTE]
>  Procedury i kompilacja instrukcje dotyczące instalacji w tym przykładzie znajdują się na końcu tego tematu.  
  
> [!IMPORTANT]
>  Przykłady może już być zainstalowany na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Channels\ChunkingChannel`  
  
## <a name="chunking-channel-assumptions-and-limitations"></a>Segmentu kanału założenia i ograniczenia  
  
### <a name="message-structure"></a>Struktura wiadomości  
 Kanał segmentu zakłada następującą strukturę komunikatu dla komunikatów jest podzielony:  
  
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
  
 Korzystając z modelu ServiceModel, kontrakt operacji, które mają 1 parametr wejściowy jest zgodne z tym kształtem komunikatu dla ich komunikat wejściowy. Podobnie operacji kontraktu, które mają 1 parametru wyjściowego lub wartości zwracanej zgodne z tym kształtem komunikatu dla ich komunikatu wyjściowego. Poniżej przedstawiono przykłady takich operacji:  
  
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
 Kanał segmentu wymaga wiadomości dostarczanych tylko raz w uporządkowanej dostarczania wiadomości (fragmentów). Oznacza to, że podstawowy stos kanału musi być sesji. Sesje mogą otrzymywać przez transportu (na przykład warstwy transportowej TCP) lub kanału sesji protokołu (na przykład, ReliableSession kanał).  
  
### <a name="asynchronous-send-and-receive"></a>Asynchroniczne wysyłanie i odbieranie  
 Asynchroniczne wysyłanie i odbieranie metod nie są implementowane przez tę wersję segmentu przykład kanału.  
  
## <a name="chunking-protocol"></a>Protokół segmentu  
 Kanał segmentu Określa protokół, który wskazuje początek i koniec szereg fragmenty, a także numer sekwencyjny każdego fragmentu. Następujące komunikaty trzy przykładowe pokazują, uruchamianie i fragmentów i na końcu komunikatów za pomocą komentarzy opisujących kluczowych aspektów każdej.  
  
### <a name="start-message"></a>Komunikat rozpoczęcia  
  
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
  
### <a name="chunk-message"></a>Komunikat fragmentów  
  
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
  
### <a name="end-message"></a>Komunikat zakończenia  
  
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
  
## <a name="chunking-channel-architecture"></a>Architektura kanał dzielący na fragmenty  
 Kanał segmentu jest `IDuplexSessionChannel` , na wysokim poziomie następujący architektury typowego kanału. Brak `ChunkingBindingElement` , można tworzyć `ChunkingChannelFactory` i `ChunkingChannelListener`. `ChunkingChannelFactory` Tworzy wystąpienia `ChunkingChannel` gdy otrzyma monit. `ChunkingChannelListener` Tworzy wystąpienia `ChunkingChannel` po zaakceptowaniu nowy kanał wewnętrznego. `ChunkingChannel` Jest odpowiedzialny za wysyłanie i odbieranie komunikatów.  
  
 Na następnym poziomie, `ChunkingChannel` opiera się na kilka składników, aby zaimplementować protokół segmentu. Na stronie wysyłania kanał używa niestandardowego `XmlDictionaryWriter` o nazwie `ChunkingWriter` wykonujący rzeczywiste segmentu. `ChunkingWriter` używa wewnętrznego kanału bezpośrednio, aby wysłać fragmenty. Za pomocą niestandardowego `XmlDictionaryWriter` pozwala nam wysyłanie fragmentów podczas zapisywania dużą porcję oryginalnej wiadomości. Oznacza to, że firma Microsoft nie Buforuj całego oryginalnej wiadomości.  
  
 ![Kanał dzielący na fragmenty](../../../../docs/framework/wcf/samples/media/chunkingchannel1.gif "ChunkingChannel1")  
  
 Po stronie odbierającej `ChunkingChannel` baza danych ściąga wiadomości z kanału wewnętrzny i przekazuje je do niestandardowego `XmlDictionaryReader` o nazwie `ChunkingReader`, który reconstitutes oryginalnego komunikatu z przychodzącego fragmentów. `ChunkingChannel` to opakowuje `ChunkingReader` w niestandardowym `Message` wdrożenia o nazwie `ChunkingMessage` i zwraca ten komunikat do wyższej warstwie. Ta kombinacja `ChunkingReader` i `ChunkingMessage` pozwala nam cofnąć Podziel oryginalnego treści wiadomości, jak jest odczytywany przez warstwę powyżej, nie trzeba buforować całej treści oryginalnej wiadomości. `ChunkingReader` ma kolejki, gdzie buforuje przychodzących fragmentów maksymalnie można skonfigurować maksymalną liczbę buforowanych fragmentów. Po osiągnięciu tego limitu maksymalnej czytnik czeka na komunikaty, aby być opróżniane z kolejki przez w wyższej warstwie (oznacza to, odczytując tylko z oryginalnego treść wiadomości) lub dopóki nie otrzymywać maksymalną osiągnięciu limitu czasu.  
  
 ![Kanał dzielący na fragmenty](../../../../docs/framework/wcf/samples/media/chunkingchannel2.gif "ChunkingChannel2")  
  
## <a name="chunking-programming-model"></a>Model programowania dzielący na fragmenty  
 Deweloperzy usług można określić wiadomości, które mają być podzielony przez zastosowanie `ChunkingBehavior` atrybutu do operacji w ramach umowy. Udostępnia atrybut `AppliesTo` właściwość, która umożliwia deweloperom określić, czy segmentu stosuje się do komunikatu wejściowego, komunikatu wyjściowego lub obu. W poniższym przykładzie pokazano użycie `ChunkingBehavior` atrybutu:  
  
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
  
 W tym modelu programowania `ChunkingBindingElement` kompiluje listę akcji elementy URI identyfikujące komunikaty, aby być fragmentaryczne. Akcja każdej wiadomości wychodzących jest porównywana z tej listy w celu ustalenia, czy fragmentaryczne lub wysyłane bezpośrednio wiadomość.  
  
## <a name="implementing-the-send-operation"></a>Implementowanie operacji wysyłania  
 Na wysokim poziomie operacji wysyłania najpierw sprawdza, czy wychodzącej wiadomości musi być podzielony, a jeśli nie, wysyła komunikat bezpośrednio przy użyciu wewnętrznego kanału.  
  
 Jeśli komunikat należy fragmentaryczne, Wyślij tworzy nową `ChunkingWriter` i wywołania `WriteBodyContents` wiadomości wychodzących przekazanie do niej to `ChunkingWriter`. `ChunkingWriter` , A następnie jest segmentu komunikatu (w tym kopiowanie oryginalne nagłówki wiadomości na komunikat fragmentów uruchomienia), a następnie wysyła fragmentów przy użyciu wewnętrznego kanału.  
  
 Kilka szczegóły warte odnotowania:  
  
-   Wyślij pierwszego wywołania `ThrowIfDisposedOrNotOpened` zapewnienie `CommunicationState` jest otwarty.  
  
-   Wysyłanie są synchronizowane, dzięki czemu mogą być wysyłane tylko jedna wiadomość na raz dla każdej sesji. Brak `ManualResetEvent` o nazwie `sendingDone` , jest resetowany po wysłaniu fragmentaryczne wiadomości. Wysłany komunikat fragmentów zakończenia tego zdarzenia jest ustawiona. Metoda wysyłania czeka dla tego zdarzenia, należy ustawić przed ponowną próbą wysłania wychodzących wiadomości.  
  
-   Wyślij blokad `CommunicationObject.ThisLock` zapobiegające synchronizacji zmian stanu podczas wysyłania. Zobacz <xref:System.ServiceModel.Channels.CommunicationObject> dokumentacji, aby uzyskać więcej informacji na temat <xref:System.ServiceModel.Channels.CommunicationObject> stanów i stan maszyny.  
  
-   Limit czasu, przekazana do wysyłania służy jako limit czasu operacji wysyłania całego, która obejmuje rozsyłanie wszystkich fragmentów.  
  
-   Niestandardowy `XmlDictionaryWriter` projekt został wybrany w celu uniknięcia buforowanie całej treści oryginalnej wiadomości. Gdybyśmy wybrali, aby uzyskać `XmlDictionaryReader` w treści przy użyciu `message.GetReaderAtBodyContents` całej treści będą buforowane. Zamiast tego oferujemy niestandardowego `XmlDictionaryWriter` przekazana do `message.WriteBodyContents`. Jak wiadomość wywołania WriteBase64 w edytorze, moduł zapisujący pakietów się fragmentów do wiadomości i wysyła je za pomocą wewnętrznego kanału. Bloki WriteBase64 do momentu wysłania jest fragmentów.  
  
## <a name="implementing-the-receive-operation"></a>Implementowanie operacji odbioru  
 Na wysokim poziomie operacji odbierania najpierw sprawdza, czy przychodzące wiadomości nie jest `null` oraz że jej działaniem jest `ChunkingAction`. Jeśli nie spełnia kryteriów obu, zwracany jest komunikat niezmienione Receive. W przeciwnym razie Receive tworzy nową `ChunkingReader` i nowy `ChunkingMessage` otaczający go (przez wywołanie metody `GetNewChunkingMessage`). Przed zwróceniem przez nowych `ChunkingMessage`, Receive korzysta z puli wątków do wykonywania `ReceiveChunkLoop`, która wywołuje metodę `innerChannel.Receive` w pętli i zdejmowania rąk fragmentach, aby `ChunkingReader` aż do zakończenia fragmentów wiadomość zostaje odebrana lub zostanie osiągnięty limit czasu odbioru.  
  
 Kilka szczegóły warte odnotowania:  
  
-   Takie jak wysyłanie, odbieranie połączeń pierwszy `ThrowIfDisposedOrNotOepned` zapewnienie `CommunicationState` jest otwarty.  
  
-   Wyświetlany jest również synchronizowane, tak że tylko jeden komunikat może zostać odebrany w czasie z sesji. Jest to szczególnie ważne, ponieważ po otrzymaniu komunikatu fragmentów start wszystkie kolejne Odebrane komunikaty powinny być fragmentów w ramach tej nowej sekwencji fragmentów, do momentu zakończenia fragmentów wiadomość zostaje odebrana. Odbieranie nie ściągają komunikaty z kanału wewnętrzny, otrzymanie wszystkich fragmentów, do których należą do wiadomości, obecnie cofnąć jest podzielony. W tym celu odbierania używa `ManualResetEvent` o nazwie `currentMessageCompleted`, która ma wartość, gdy komunikat fragmentów zakończenia jest odbierany i zresetować po odebraniu nowej wiadomości fragmentów rozpoczęcia.  
  
-   W przeciwieństwie do wysłania Receive nie uniemożliwia zsynchronizowane stanami podczas odbierania. Na przykład Zamknij można wywołać podczas odbierania i czeka, aż do ukończenia oczekujących odbieranie oryginalnego komunikatu lub określona wartość limitu czasu zostanie osiągnięty.  
  
-   Limit czasu, przekazana do odbierania jest używany, podobnie jak limit czasu dla całego otrzymują operacji, która obejmuje dostęp do wszystkich fragmentów.  
  
-   Jeśli warstwy, która zużywa komunikat zużywa treść komunikatu z szybkością niższa niż stopa wiadomości przychodzących fragmentów, `ChunkingReader` buforuje te fragmenty przychodzących do limitu określonego przez `ChunkingBindingElement.MaxBufferedChunks`. Po osiągnięciu tego limitu nie ma więcej fragmentów są pobierane z niższej warstwie, aż do buforowanego fragmentów jest używany lub zostanie osiągnięty limit czasu odbioru.  
  
## <a name="communicationobject-overrides"></a>CommunicationObject zastąpień  
  
### <a name="onopen"></a>Zdarzenia  
 `OnOpen` wywołania `innerChannel.Open` do otwierania kanału wewnętrznego.  
  
### <a name="onclose"></a>OnClose  
 `OnClose` najpierw ustawia `stopReceive` do `true` celu sygnalizowania, że oczekujące `ReceiveChunkLoop` zatrzymania. Następnie czeka na zatwierdzenie `receiveStopped``ManualResetEvent`, która jest ustawiona, gdy `ReceiveChunkLoop` zatrzymuje. Zakładając, że `ReceiveChunkLoop` zatrzymuje się przed upływem określonego limitu czasu, `OnClose` wywołania `innerChannel.Close` z pozostałych przekroczeniem limitu czasu.  
  
### <a name="onabort"></a>OnAbort  
 `OnAbort` wywołania `innerChannel.Abort` przerwania wewnętrzny kanału. Jeśli istnieje oczekujące `ReceiveChunkLoop` otrzymuje wyjątku z Oczekujące `innerChannel.Receive` wywołania.  
  
### <a name="onfaulted"></a>OnFaulted  
 `ChunkingChannel` Nie wymaga specjalnego zachowania, gdy kanał komunikacji niezawodnej, więc `OnFaulted` nie zostanie zastąpione.  
  
## <a name="implementing-channel-factory"></a>Implementowanie fabryki kanałów  
 `ChunkingChannelFactory` Jest odpowiedzialny za tworzenie wystąpień `ChunkingDuplexSessionChannel` i kaskadowych stanów przejść do wewnętrzna fabryka kanałów.  
  
 `OnCreateChannel` używa wewnętrzna fabryka kanałów w celu utworzenia `IDuplexSessionChannel` wewnętrzny kanału. Następnie tworzy nową `ChunkingDuplexSessionChannel` przekazanie jej w tym kanale wewnętrzny wraz z listą działań komunikat na być podzielony i maksymalną liczbę fragmentów do zbuforowania podczas odbierania. Lista wiadomości działania, aby być podzielony i maksymalną liczbę fragmentów do buforowania są dwa parametry przekazywane do `ChunkingChannelFactory` w jego konstruktorze. W sekcji na `ChunkingBindingElement` opisuje pochodzenie tych wartości.  
  
 `OnOpen`, `OnClose`, `OnAbort` i ich odpowiedniki asynchroniczne wywoływanie odpowiednia metoda przejścia stanu na wewnętrzna fabryka kanałów.  
  
## <a name="implementing-channel-listener"></a>Implementowanie odbiornika kanałów  
 `ChunkingChannelListener` Tworzy otokę wokół odbiornika kanału wewnętrznego. Jego funkcję main, oprócz delegata wywołania tego odbiornika kanału wewnętrzny jest opakowanie nowe `ChunkingDuplexSessionChannels` wokół kanały akceptowana od odbiornika kanałów wewnętrznego. Jest to realizowane w `OnAcceptChannel` i `OnEndAcceptChannel`. Nowo utworzony `ChunkingDuplexSessionChannel` jest przekazywany wewnętrzny kanał wraz z innymi parametrami, które opisano wcześniej.  
  
## <a name="implementing-binding-element-and-binding"></a>Implementowanie elementu powiązania i powiązania  
 `ChunkingBindingElement` jest odpowiedzialny za tworzenie `ChunkingChannelFactory` i `ChunkingChannelListener`. `ChunkingBindingElement` Sprawdza, czy T w `CanBuildChannelFactory` \<T > i `CanBuildChannelListener` \<T > typu `IDuplexSessionChannel` (tylko kanał obsługiwane segmentu kanał) i inne elementy powiązania powiązanie obsługuje to Typ kanału.  
  
 `BuildChannelFactory`\<T > najpierw sprawdza, czy typ żądanego kanału mogą być wbudowane, a następnie pobiera listę akcji komunikat na być podzielony. Aby uzyskać więcej informacji zobacz następującą sekcję. Następnie tworzy nową `ChunkingChannelFactory` przekazanie do niej wewnętrzna fabryka kanałów (postaci zwracanej przez `context.BuildInnerChannelFactory<IDuplexSessionChannel>`), lista akcji wiadomości i maksymalną liczbę fragmentów do buforowania. Maksymalna liczba fragmentów pochodzi z właściwością o nazwie `MaxBufferedChunks` udostępnianych przez `ChunkingBindingElement`.  
  
 `BuildChannelListener<T>` zawiera podobne implementację tworzenia `ChunkingChannelListener` i przekazanie do niej odbiornik kanału wewnętrznego.  
  
 Brak powiązanie przykład zawarty w tym przykładzie o nazwie `TcpChunkingBinding`. To powiązanie zawiera dwa elementy wiązania: `TcpTransportBindingElement` i `ChunkingBindingElement`. Oprócz udostępnianie `MaxBufferedChunks` właściwości powiązania ustawia również niektóre `TcpTransportBindingElement` właściwości, takie jak `MaxReceivedMessageSize` (ustawia ją na `ChunkingUtils.ChunkSize` + 100 KB bajtów dla nagłówków).  
  
 `TcpChunkingBinding` implementuje również `IBindingRuntimePreferences` i zwraca wartość true z `ReceiveSynchronously` metoda wskazujący, że są wykonywane tylko synchroniczne wywołania Receive.  
  
### <a name="determining-which-messages-to-chunk"></a>Określanie, które komunikaty dotyczące fragmentów  
 Kanał segmentu chunks tylko komunikaty, które są identyfikowane za pomocą `ChunkingBehavior` atrybutu. `ChunkingBehavior` Klasy implementuje `IOperationBehavior` i jest implementowany przez wywołanie metody `AddBindingParameter` metody. W przypadku tej metody `ChunkingBehavior` sprawdza, czy wartość jego `AppliesTo` właściwości (`InMessage`, `OutMessage` i / lub) do określenia wiadomości, które powinny być fragmentaryczne. Następnie pobiera akcji każdego z tych komunikatów (z kolekcji wiadomości na `OperationDescription`) i dodaje go do kolekcji ciągów, zawartych w instancji `ChunkingBindingParameter`. Następnie dodaje to `ChunkingBindingParameter` podanego `BindingParameterCollection`.  
  
 To `BindingParameterCollection` są przekazywane wewnątrz `BindingContext` do każdego elementu powiązania w powiązaniu w przypadku tego elementu powiązania kompilacji fabryki kanału lub odbiornika kanałów. `ChunkingBindingElement`Przez implementację `BuildChannelFactory<T>` i `BuildChannelListener<T>` tego `ChunkingBindingParameter` poza `BindingContext’`s `BindingParameterCollection`. Zbiór działań zawartych w `ChunkingBindingParameter` jest następnie przekazywany do `ChunkingChannelFactory` lub `ChunkingChannelListener`, który z kolei przekazuje go do `ChunkingDuplexSessionChannel`.  
  
## <a name="running-the-sample"></a>Działa aplikacja przykładowa  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, tworzenie i uruchamianie aplikacji przykładowej  
  
1.  Zainstaluj [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 4.0, używając następującego polecenia.  
  
    ```  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2.  Upewnij się, że wykonano [procedura konfiguracji jednorazowe dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
3.  Aby skompilować rozwiązanie, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
4.  Do uruchomienia przykładu w konfiguracji o jednym lub wielu maszyny, postępuj zgodnie z instrukcjami [uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
5.  Uruchom najpierw Service.exe, a następnie uruchom Client.exe i obejrzyj oba okna konsoli danych wyjściowych.  
  
 Podczas uruchamiania przykładu, należy się następujące dane wyjściowe.  
  
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
