---
title: Duże ilości danych i przesyłanie strumieniowe
ms.date: 03/30/2017
ms.assetid: ab2851f5-966b-4549-80ab-c94c5c0502d2
ms.openlocfilehash: 70e43eaf4dc77e07af8ec65faf9cf0fa9a7a0fe4
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/14/2019
ms.locfileid: "70991517"
---
# <a name="large-data-and-streaming"></a>Duże ilości danych i przesyłanie strumieniowe
Windows Communication Foundation (WCF) to infrastruktura komunikacji oparta na języku XML. Ponieważ dane XML są powszechnie zakodowane w standardowym formacie tekstowym zdefiniowanym w [specyfikacji XML 1,0](https://go.microsoft.com/fwlink/?LinkId=94838), połączone systemy deweloperzy i architektów zwykle są zaangażowane w informacje o sieci (lub rozmiarze) komunikatów wysyłanych przez sieć i Kodowanie za pomocą tekstu XML stanowi specjalne wyzwania dotyczące wydajnego transferu danych binarnych.  
  
## <a name="basic-considerations"></a>Podstawowe zagadnienia  
 Aby podać informacje w tle dotyczące następujących informacji dotyczących programu WCF, w tej sekcji przedstawiono niektóre ogólne zagadnienia i zagadnienia dotyczące kodowania, danych binarnych i przesyłania strumieniowego, które są ogólnie stosowane do infrastruktury podłączonych systemów.  
  
### <a name="encoding-data-text-vs-binary"></a>Dane kodowania: Tekst a plików binarnych  
 Często wyrażane problemy dla deweloperów obejmują postrzeganie, że kod XML ma znaczne obciążenie w porównaniu z formatami binarnymi ze względu na powtarzalny charakter tagów początkowych i tagów końcowych, że kodowanie wartości liczbowych jest uznawane za znacznie większe ponieważ są one wyrażone w wartościach tekstowych, a dane binarne nie mogą być wyrażone efektywnie, ponieważ muszą być specjalnie zakodowane w formacie tekstowym.  
  
 Chociaż wiele z tych i podobnych problemów jest prawidłowych, rzeczywista różnica między komunikatami szyfrowanymi w formacie XML w środowisku usług sieci Web XML i kodowanymi binarnie komunikatami w starszym środowisku zdalnego wywołania procedury (RPC) jest często znacznie mniej znacząca niż możliwe jest zaproponowanie pierwszego zagadnienia.  
  
 Komunikaty zakodowane w formacie XML są przezroczyste i "czytelne", wiadomości binarne są często stosunkowo odczuwalne w porównaniu i trudne do zdekodowania bez narzędzi. Ta różnica w czytelności prowadzi do zapomina, że wiadomości binarne często zawierają wbudowane metadane w ładunku, co zwiększa obciążenie tak jak w przypadku wiadomości tekstowych XML. Jest to szczególnie prawdziwe w przypadku formatów binarnych, które mają na celu zapewnienie swobodnego sprzężenia i możliwości dynamicznego wywoływania.  
  
 Jednak formaty binarne zwykle zawierają takie opisowe informacje metadanych w "nagłówku", który również deklaruje układ danych dla następujących rekordów danych. Ładunek następuje po tej wspólnej deklaracji bloku metadanych z minimalnym dodatkowym obciążeniem. W przeciwieństwie, kod XML ujmuje każdy element danych w elemencie lub atrybucie, tak aby otaczające metadane były powtarzane dla każdego serializowanego obiektu ładunku. W związku z tym rozmiar pojedynczego serializowanego obiektu ładunku jest podobny w przypadku porównywania tekstu z reprezentacją binarną, ponieważ niektóre metadane opisowe muszą być wyrażone w obu przypadkach, ale format binarny korzysta z opisu udostępnionej metadanych z każdą dodatkową Obiekt ładunku, który jest przenoszony z powodu dolnego ogólnego obciążenia.  
  
 W przypadku niektórych typów danych, takich jak liczby, może być niekorzystne użycie stałych, binarnych reprezentacji liczbowych, takich jak 128-bitowy typ dziesiętny zamiast zwykłego tekstu, ponieważ reprezentacja zwykłego tekstu może być mniejsza. W przypadku danych tekstowych mogą być również dostępne różne rozmiary z zwykle bardziej elastycznych opcji kodowania tekstu XML, podczas gdy niektóre formaty binarne mogą domyślnie mieć 16-bitową lub nawet 32-bitową wersję Unicode, która nie ma zastosowania do binarnego formatu XML programu .NET.  
  
 W związku z tym wybranie między tekstem a plikiem binarnym nie jest bardzo proste, ponieważ przy założeniu, że komunikaty binarne są zawsze mniejsze niż wiadomości tekstowe XML.  
  
 Oczywistą zaletą komunikatów tekstowych XML jest to, że są one oparte na standardach i oferują najszerszy wybór opcji współdziałania i obsługi platformy. Aby uzyskać więcej informacji, zobacz sekcję "kodowania" w dalszej części tego tematu.  
  
### <a name="binary-content"></a>Zawartość binarna  
 Jeden obszar, w którym kodowania binarne są przeznaczone do kodowania na podstawie tekstu, pod warunkiem, że rozmiary komunikatów są dużymi elementami danych binarnych, takimi jak obrazy, wideo, klipy dźwiękowe lub jakakolwiek inna forma nieprzezroczystych danych binarnych, które muszą być wymieniane między usługami i ich odbiorcy. Aby dopasować te typy danych do tekstu XML, typowe podejście polega na zakodowaniu ich przy użyciu kodowania base64.  
  
 W ciągu zakodowanym algorytmem Base64 każdy znak reprezentuje 6-bitów oryginalnych danych 8-bitowych, co skutkuje wskaźnikiem narzutowania kodowania 4:3 dla Base64, a nie zliczaniem dodatkowych znaków formatowania (znak powrotu karetki/wysuwu wiersza), które są powszechnie dodawane przez Konwencję. Chociaż istotność różnic między kodowaniem XML i binarnym zwykle zależy od scenariusza, wzrost rozmiaru większy niż 33% podczas przekazywania ładunku 500-MB nie jest zazwyczaj akceptowalny.  
  
 Aby uniknąć tego obciążenia kodowania, w standardzie mechanizm optymalizacji transmisji wiadomości (MTOM) można eksternalizacji duże elementy danych, które znajdują się w komunikacie i przenosząc je do wiadomości jako dane binarne bez żadnego specjalnego kodowania. Przy użyciu mechanizmu MTOM komunikaty są wymieniane w podobny sposób do Simple Mail Transfer Protocol (SMTP) wiadomości e-mail z załącznikami lub osadzoną zawartością (obrazy i inne osadzone elementy); Komunikaty mechanizmu MTOM są pakowane jako wieloczęściowe/powiązane sekwencje MIME z główną częścią rzeczywistego komunikatu protokołu SOAP.  
  
 Komunikat protokołu SOAP MTOM jest modyfikowany z jego niekodowanej wersji tak, aby Tagi elementów specjalnych odwołujące się do odpowiednich części MIME miały miejsce oryginalne elementy w komunikacie zawierającym dane binarne. W związku z tym komunikat protokołu SOAP odwołuje się do zawartości binarnej, wskazując do wysłanej z nią części MIME, ale w przeciwnym razie tylko przenosi dane tekstowe XML. Ponieważ ten model jest ściśle wyrównany przy użyciu dobrze ustanowionego modelu SMTP, dostępne są szeroką gamę narzędzi do kodowania i dekodowania komunikatów MTOM na wielu platformach, co sprawia, że jest to niezwykle interoperacyjne rozwiązanie.  
  
 Nadal, podobnie jak w przypadku protokołu Base64, MTOM jest również niezbędny do użycia w formacie MIME, dzięki czemu zalety używania MTOM są widoczne tylko wtedy, gdy rozmiar elementu danych binarnych przekroczy około 1 KB. Ze względu na obciążenie, komunikaty kodowane algorytmem MTOM mogą być większe niż komunikaty, które używają kodowania base64 dla danych binarnych, jeśli ładunek binarny pozostaje poniżej tego progu. Aby uzyskać więcej informacji, zobacz sekcję "kodowania" w dalszej części tego tematu.  
  
### <a name="large-data-content"></a>Duża zawartość danych  
 Poza tym, wspomniany wcześniej ładunek 500-MB stanowi również wspaniałe lokalne wyzwanie na potrzeby usługi i klienta. Domyślnie program WCF przetwarza komunikaty w *trybie buforowanym*. Oznacza to, że cała zawartość komunikatu jest obecna w pamięci przed wysłaniem lub po odebraniu. Chociaż jest to dobrą strategią dla większości scenariuszy i są niezbędne do obsługi komunikatów, takich jak podpisy cyfrowe i niezawodne dostarczanie, duże wiadomości mogą wyczerpać zasoby systemu.  
  
 Strategia postępowania z dużymi ładunkiem polega na przesyłaniu strumieniowym. Komunikaty, szczególnie te wyrażone w formacie XML, są powszechnie uważane za stosunkowo kompaktowe pakiety danych, a komunikat może mieć rozmiar wiele gigabajtów i przypominać strumień danych ciągłych więcej niż pakiet danych. Gdy dane są przesyłane w trybie przesyłania strumieniowego, a nie w trybie buforowanym, nadawca wysyła zawartość treści wiadomości do adresata w postaci strumienia, a infrastruktura komunikatów stale przekazuje dane od nadawcy do odbiorcy w miarę rozwoju udostępnione.  
  
 Najbardziej typowym scenariuszem, w którym występują takie transfery dużej ilości danych, są transfery obiektów danych binarnych, które:  
  
- Nie można łatwo rozbić do sekwencji komunikatów.  
  
- Muszą być dostarczone w odpowiednim czasie.  
  
- Nie są dostępne w całości po zainicjowaniu transferu.  
  
 W przypadku danych, które nie mają tych ograniczeń, zazwyczaj lepiej jest wysyłać sekwencje komunikatów w zakresie sesji niż w przypadku jednej dużej wiadomości. Aby uzyskać więcej informacji, zobacz sekcję "dane przesyłane strumieniowo" w dalszej części tego tematu.  
  
 Podczas wysyłania dużych ilości danych należy ustawić `maxAllowedContentLength` ustawienie usług IIS (Aby uzyskać więcej informacji, zobacz [Konfigurowanie limitów żądań usług IIS](https://go.microsoft.com/fwlink/?LinkId=253165)) i `maxReceivedMessageSize` ustawienie powiązania (na przykład [ System. ServiceModel. BasicHttpBinding. MaxReceivedMessageSize](xref:System.ServiceModel.HttpBindingBase.MaxReceivedMessageSize%2A) lub <xref:System.ServiceModel.NetTcpBinding.MaxReceivedMessageSize%2A>). Właściwość domyślna to 28,6 M `maxReceivedMessageSize` , a właściwość domyślna to 64 KB. `maxAllowedContentLength`  
  
## <a name="encodings"></a>Kodowanie  
 *Kodowanie* definiuje zestaw reguł dotyczących sposobu prezentowania wiadomości w sieci przewodowej. *Koder* implementuje takie kodowanie i jest odpowiedzialny na stronie nadawcy w celu wyłączania pamięci <xref:System.ServiceModel.Channels.Message> do strumienia bajtów lub buforu bajtów, który można wysłać w sieci. Po stronie odbiornika koder zamienia sekwencję bajtów na komunikat w pamięci.  
  
 Program WCF zawiera trzy kodery i umożliwia pisanie i podłączenie własnych koderów, w razie potrzeby.  
  
 Każde ze standardowych powiązań zawiera wstępnie skonfigurowany koder, według którego powiązania z prefiksem Net * używają kodera binarnego (poprzez dołączenie <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement> klasy), <xref:System.ServiceModel.BasicHttpBinding> podczas gdy klasy <xref:System.ServiceModel.WSHttpBinding> i używają kodera wiadomości tekstowych (za pomocą Domyślnie <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement> Klasa).  
  
|Element powiązania kodera|Opis|  
|-----------------------------|-----------------|  
|<xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>|Koder wiadomości tekstowych to domyślny koder dla wszystkich powiązań opartych na protokole HTTP i odpowiedni wybór dla wszystkich powiązań niestandardowych, w których współdziałanie jest najwyższej istotności. Ten koder odczytuje i zapisuje standardowe komunikaty tekstowe SOAP 1.1/SOAP 1,2 bez specjalnej obsługi danych binarnych. Jeśli właściwość komunikatu jest ustawiona na <xref:System.ServiceModel.Channels.MessageVersion.None?displayProperty=nameWithType>, otoka koperty protokołu SOAP zostanie pominięta z danych wyjściowych i tylko zawartość treści komunikatu jest serializowana. <xref:System.ServiceModel.Channels.MessageVersion?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement>|Koder komunikatów MTOM jest koderem tekstowym, który implementuje specjalną obsługę danych binarnych i nie jest domyślnie używany w żadnym ze standardowych powiązań, ponieważ jest to wyłącznie narzędzie do optymalizacji wielkości liter. Jeśli komunikat zawiera dane binarne, które przekraczają próg, w którym Kodowanie MTOM zwraca korzyść, dane są zewnętrzne do części MIME po kopercie komunikatu. Zobacz Włączanie mechanizmu MTOM w dalszej części tej sekcji.|  
|<xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>|Koder komunikatów binarnych to domyślny koder powiązań NET * i odpowiedni wybór, gdy obie strony komunikują się na podstawie WCF. Koder komunikatów binarnych używa formatu binarny programu .NET, czyli reprezentacji binarnych dla określonych firmy Microsoft dla zestawów informacyjnych XML (Infosets), która zazwyczaj daje mniejszy wpływ niż odpowiednik reprezentacji XML 1,0 i koduje dane binarne jako bajt produkcyjne.|  
  
 Kodowanie wiadomości tekstowych jest zazwyczaj najlepszym wyborem dla każdej ścieżki komunikacji wymagającej współdziałania, podczas gdy kodowanie komunikatów binarnych jest najlepszym wyborem dla każdej innej ścieżki komunikacyjnej. Kodowanie wiadomości binarnych zazwyczaj daje mniejsze rozmiary komunikatów w porównaniu do tekstu w przypadku pojedynczego komunikatu i stopniowo zmniejsza mniejsze rozmiary komunikatów w czasie trwania sesji komunikacji. W przeciwieństwie do kodowania tekstu, kodowanie binarne nie musi używać specjalnej obsługi danych binarnych, takich jak użycie Base64, ale reprezentuje bajty jako bajty.  
  
 Jeśli rozwiązanie nie wymaga współdziałania, ale nadal chcesz używać transportu HTTP, możesz złożyć <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement> do niestandardowego powiązania, które <xref:System.ServiceModel.Channels.HttpTransportBindingElement> używa klasy do transportu. Jeśli liczba klientów w usłudze wymaga współdziałania, zaleca się uwidocznienie równoległych punktów końcowych, z których każdy ma odpowiednie opcje transportu i kodowania dla odpowiednich klientów.  
  
### <a name="enabling-mtom"></a>Włączanie mechanizmu MTOM  
 Gdy współdziałanie jest wymaganiem i należy wysłać duże dane binarne, kodowanie komunikatów mechanizmu MTOM jest alternatywną strategią kodowania, którą można włączyć na <xref:System.ServiceModel.BasicHttpBinding> podstawie <xref:System.ServiceModel.WSHttpBinding> standardu lub powiązań przez `MessageEncoding` ustawienie odpowiednich Właściwość do <xref:System.ServiceModel.WSMessageEncoding.Mtom> lub przez złożenie <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement> <xref:System.ServiceModel.Channels.CustomBinding>do. W poniższym przykładowym kodzie wyodrębnionym z przykładu [kodowania MTOM](../../../../docs/framework/wcf/samples/mtom-encoding.md) pokazano, jak włączyć MTOM w konfiguracji.  
  
```xml  
<system.serviceModel>  
     …  
    <bindings>  
      <wsHttpBinding>  
        <binding name="ExampleBinding" messageEncoding="Mtom"/>  
      </wsHttpBinding>  
    </bindings>  
     …  
<system.serviceModel>  
```  
  
 Jak wspomniano wcześniej, decyzja o użyciu kodowania MTOM zależy od wysyłanego woluminu danych. Ponadto, ponieważ MTOM jest włączony na poziomie powiązania, włączenie mechanizmu MTOM wpływa na wszystkie operacje w danym punkcie końcowym.  
  
 Ponieważ koder MTOM zawsze emituje komunikat MIME/wieloczęściowy zakodowany przez MTOM, bez względu na to, czy dane binarne kończą się zewnętrznie, należy ogólnie włączyć MTOM dla punktów końcowych, które wymieniają komunikaty zawierające więcej niż 1 KB danych binarnych. Ponadto kontrakty usługi przeznaczone do użycia z punktami końcowymi z obsługą mechanizmu MTOM powinny być w miarę możliwości ograniczone do określania takich operacji transferu danych. Powiązane funkcje kontroli powinny znajdować się w osobnym kontrakcie. Ta reguła "MTOM-Only" dotyczy tylko komunikatów wysyłanych za poorednictwem punktu końcowego z obsługą mechanizmu MTOM; MTOM-koder może również zdekodować i analizować przychodzące komunikaty inne niż MTOM.  
  
 Używanie kodera MTOM jest zgodne ze wszystkimi innymi funkcjami WCF. Należy zauważyć, że może nie być możliwe przestrzeganie tej reguły we wszystkich przypadkach, na przykład gdy wymagana jest obsługa sesji.  
  
### <a name="programming-model"></a>Model programowania  
 Niezależnie od tego, które z trzech wbudowanych koderów używanych w aplikacji, środowisko programistyczne jest identyczne z uwzględnieniem transferu danych binarnych. Różnica polega na tym, jak WCF obsługuje dane na podstawie ich typów danych.  
  
```csharp
[DataContract]  
class MyData  
{  
    [DataMember]  
    byte[] binaryBuffer;  
    [DataMember]  
    string someStringData;  
}   
```  
  
 W przypadku korzystania z mechanizmu MTOM poprzedni kontrakt danych jest serializowany zgodnie z następującymi regułami:  
  
- Jeśli `binaryBuffer` nie`null` jest i pojedynczo zawiera wystarczającą ilość danych, aby uzasadnić obciążenie externalization MTOM (nagłówki MIME itd.) w porównaniu z kodowaniem Base64, dane są zewnętrzne i przenoszone wraz z komunikatem jako binarną część MIME. Jeśli próg nie zostanie przekroczony, dane są kodowane jako Base64.  
  
- Ciąg (i wszystkie inne typy, które nie są binarne) są zawsze reprezentowane jako ciąg wewnątrz treści komunikatu, bez względu na rozmiar.  
  
 Wpływ na Kodowanie MTOM jest taki sam, niezależnie od tego, czy jest używany jawny kontrakt danych, jak pokazano w poprzednim przykładzie, należy użyć listy parametrów w operacji, mieć zagnieżdżone Kontrakty danych lub przenieść obiekt kontraktu danych wewnątrz kolekcji. Tablice bajtowe są zawsze kandydatami do optymalizacji i są optymalizowane, jeśli są spełnione progi optymalizacji.  
  
> [!NOTE]
> Nie należy używać <xref:System.IO.Stream?displayProperty=nameWithType> typów pochodnych wewnątrz kontraktów danych. Dane przesyłane strumieniowo powinny być przekazywane przy użyciu modelu przesyłania strumieniowego, wyjaśnione w poniższych sekcjach "dane przesyłane strumieniowo".  
  
## <a name="streaming-data"></a>Przesyłanie strumieniowe danych  
 W przypadku transferu dużej ilości danych, tryb transferu przesyłania strumieniowego w programie WCF jest możliwym rozwiązaniem alternatywnym dla domyślnego zachowania buforowania i przetwarzania komunikatów w pamięci.  
  
 Jak wspomniano wcześniej, Włącz przesyłanie strumieniowe tylko dla dużych komunikatów (z zawartością tekstową lub binarną), jeśli nie można podzielić danych na segmenty, jeśli wiadomość musi zostać dostarczona w odpowiednim czasie lub jeśli dane nie są jeszcze w pełni dostępne podczas inicjowania transferu.  
  
### <a name="restrictions"></a>Ograniczenia  
 W przypadku włączenia przesyłania strumieniowego nie można użyć dużej liczby funkcji WCF:  
  
- Podpisy cyfrowe dla treści wiadomości nie mogą zostać wykonane, ponieważ wymagają przetwarzania skrótu przez całą zawartość wiadomości. W przypadku przesyłania strumieniowego zawartość nie jest w pełni dostępna, gdy nagłówki wiadomości są konstruowane i wysyłane i w związku z tym nie można obliczyć podpisu cyfrowego.  
  
- Szyfrowanie zależy od podpisów cyfrowych, aby sprawdzić, czy dane zostały poprawnie skonstruowane.  
  
- Niezawodne sesje muszą buforować wysyłane komunikaty na kliencie w celu ponownego dostarczenia, jeśli komunikat zostanie utracony w ramach transferu i musi przechowywać komunikaty w usłudze przed przekazaniem ich do implementacji usługi w celu zachowania kolejności komunikatów w przypadku otrzymania komunikatów o wypadekch poza kolejnością.  
  
 Ze względu na te ograniczenia funkcjonalne można używać tylko opcji zabezpieczeń na poziomie transportu do przesyłania strumieniowego i nie można włączać niezawodnych sesji. Przesyłanie strumieniowe jest dostępne tylko w przypadku następujących powiązań zdefiniowanych przez system:  
  
- <xref:System.ServiceModel.BasicHttpBinding>  
  
- <xref:System.ServiceModel.NetTcpBinding>  
  
- <xref:System.ServiceModel.NetNamedPipeBinding>  
  
- <xref:System.ServiceModel.WebHttpBinding>  
  
 Ze względu na to, że <xref:System.ServiceModel.NetTcpBinding> podstawowe <xref:System.ServiceModel.NetNamedPipeBinding> transporty i obsługują niezawodne dostarczanie i sesję opartą na połączeniach, w przeciwieństwie do protokołu HTTP, te dwa powiązania mają minimalny wpływ na te ograniczenia.  
  
 Transmisja strumieniowa nie jest dostępna w przypadku transportu usługi kolejkowania komunikatów (MSMQ) i dlatego nie można jej używać <xref:System.ServiceModel.NetMsmqBinding> z <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> ani klasą. Transport kolejkowania komunikatów obsługuje tylko buforowane transfery danych z ograniczonym rozmiarem komunikatu, podczas gdy wszystkie inne transporty nie mają praktycznego limitu rozmiaru komunikatów dla większości scenariuszy.  
  
 Przesyłanie strumieniowe jest również niedostępne w przypadku korzystania z transportu kanału równorzędnego, więc nie jest <xref:System.ServiceModel.NetPeerTcpBinding>dostępne w programie.  
  
#### <a name="streaming-and-sessions"></a>Przesyłanie strumieniowe i sesje  
 Podczas przesyłania strumieniowego do wywołań opartych na sesji może wystąpić nieoczekiwane zachowanie. Wszystkie wywołania przesyłania strumieniowego są realizowane za pośrednictwem pojedynczego kanału (kanału datagramu), który nie obsługuje sesji, nawet jeśli używane powiązanie jest skonfigurowane do korzystania z sesji. Jeśli wielu klientów przesyła strumieniowo wywołania do tego samego obiektu usługi za pośrednictwem powiązań opartych na sesji, a tryb współbieżności obiektu usługi jest ustawiony na wartość Single, a jego tryb kontekstu wystąpienia jest ustawiony na PerSession, wszystkie wywołania muszą przechodzić przez kanał datagramu i tylko jeden wywołanie jest przetwarzane w czasie. Co najmniej jeden klient może przekroczyć limit czasu. Ten problem można obejść, konfigurując tryb kontekstu wystąpienia obiektu usługi do PerCall lub współbieżności do wielu.  
  
> [!NOTE]
> MaxConcurrentSessions nie ma wpływu w tym przypadku, ponieważ jest dostępna tylko jedna "sesja".  
  
### <a name="enabling-streaming"></a>Włączanie przesyłania strumieniowego  
 Przesyłanie strumieniowe można włączyć w następujący sposób:  
  
- Wysyłanie i akceptowanie żądań w trybie przesyłania strumieniowego oraz akceptowanie i zwracanie odpowiedzi w<xref:System.ServiceModel.TransferMode.StreamedRequest>trybie buforowanym ().  
  
- Wysyłanie i akceptowanie żądań w trybie buforowanym oraz akceptowanie i zwracanie odpowiedzi w trybie przesyłania<xref:System.ServiceModel.TransferMode.StreamedResponse>strumieniowego ().  
  
- Wysyłanie i odbieranie żądań i odpowiedzi w trybie przesyłania strumieniowego w obu kierunkach. (<xref:System.ServiceModel.TransferMode.Streamed>).  
  
 Przesyłanie strumieniowe można wyłączyć, ustawiając tryb transferu na <xref:System.ServiceModel.TransferMode.Buffered>, który jest ustawieniem domyślnym dla wszystkich powiązań. Poniższy kod pokazuje, jak ustawić tryb transferu w konfiguracji.  
  
```xml  
<system.serviceModel>  
     …  
    <bindings>  
      <basicHttpBinding>  
        <binding name="ExampleBinding" transferMode="Streamed"/>  
      </basicHttpBinding>  
    </bindings>  
     …  
<system.serviceModel>  
```  
  
 Podczas tworzenia wystąpienia powiązania w kodzie, należy ustawić odpowiednią `TransferMode` właściwość powiązania (lub element powiązania transportu, jeśli tworzysz niestandardowe powiązanie) do jednej z wcześniej wymienionych wartości.  
  
 Można włączyć przesyłanie strumieniowe żądań i odpowiedzi albo w obu kierunkach, niezależnie od ich strony, bez wywierania wpływu na funkcjonalność. Należy jednak zawsze założyć, że transferowany rozmiar danych jest tak duży, że włączenie przesyłania strumieniowego jest uzasadnione na obu punktach końcowych łącza komunikacyjnego. W przypadku komunikacji między platformami, w której jeden z punktów końcowych nie jest zaimplementowany przy użyciu programu WCF, możliwość korzystania z przesyłania strumieniowego zależy od możliwości przesyłania strumieniowego na platformie. Innym rzadkim wyjątkiem może być Scenariusz oparty na zużyciu pamięci, w którym klient lub usługa musi zminimalizować swój zestaw roboczy i może zapewnić tylko małe rozmiary buforów.  
  
### <a name="enabling-asynchronous-streaming"></a>Włączanie przesyłania strumieniowego asynchronicznego  
 Aby włączyć asynchroniczne przesyłanie strumieniowe, <xref:System.ServiceModel.Description.DispatcherSynchronizationBehavior> Dodaj zachowanie punktu końcowego do hosta usługi i ustaw <xref:System.ServiceModel.Description.DispatcherSynchronizationBehavior.AsynchronousSendEnabled%2A> jego właściwość `true`na. Dodaliśmy także możliwość wysyłania strumieniowo asynchronicznych danych przesyłanych po stronie wysyłającej. Poprawia to skalowalność usługi w scenariuszach, w których przesyła strumieniowo komunikaty do wielu klientów, z których może się zająć wolne odczytywanie z powodu przeciążenia sieci lub nie są w ogóle odczytywane. W tych scenariuszach nie blokujemy poszczególnych wątków w usłudze na klienta. Dzięki temu usługa może przetwarzać wielu kolejnych klientów w taki sposób, aby zwiększyć skalowalność usługi.  
  
### <a name="programming-model-for-streamed-transfers"></a>Model programowania dla transferów przesyłanych strumieniowo  
 Model programowania dla przesyłania strumieniowego jest prosty. W przypadku otrzymywania przesyłanych strumieniowo danych należy określić kontrakt operacji, <xref:System.IO.Stream> który ma parametr wejściowy z jednym typem. Aby można było zwracać dane przesyłane strumieniowo <xref:System.IO.Stream> , zwróć odwołanie.  
  
```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface IStreamedService  
{  
    [OperationContract]  
    Stream Echo(Stream data);  
    [OperationContract]  
    Stream RequestInfo(string query);  
    [OperationContract(OneWay=true)]  
    void ProvideInfo(Stream data);  
}  
```  
  
 Operacja `Echo` w powyższym przykładzie odbiera i zwraca strumień i dlatego powinna być używana w powiązaniu z <xref:System.ServiceModel.TransferMode.Streamed>. Dla operacji `RequestInfo` <xref:System.ServiceModel.TransferMode.StreamedResponse> jest najlepiej dopasowany, <xref:System.IO.Stream>ponieważ zwraca tylko wartość. Operacja jednokierunkowa najlepiej nadaje się do <xref:System.ServiceModel.TransferMode.StreamedRequest>.  
  
 Należy zauważyć, że dodanie drugiego parametru do poniższych `Echo` lub `ProvideInfo` operacji powoduje, że model usługi przywraca z powrotem do buforowanej strategii i używa reprezentacji serializacji w czasie wykonywania strumienia. Tylko operacje z pojedynczym parametrem strumienia wejściowego są zgodne z żądaniami kompleksowego przesyłania strumieniowego.  
  
 Ta reguła w podobny sposób dotyczy kontraktów komunikatów. Zgodnie z poniższą umową dotyczącą komunikatu można mieć tylko jeden element członkowski treści w ramach kontraktu, który jest strumieniem. Jeśli chcesz przekazać dodatkowe informacje ze strumieniem, te informacje muszą być przenoszone w nagłówkach wiadomości. Treść komunikatu jest zarezerwowana wyłącznie dla zawartości strumienia.  
  
```csharp
[MessageContract]  
public class UploadStreamMessage  
{  
   [MessageHeader]  
   public string appRef;  
   [MessageBodyMember]  
   public Stream data;  
}   
```  
  
 Transfer przesyłanych strumieniowo kończy się, a komunikat jest zamykany, gdy strumień osiągnie koniec pliku (EOF). W przypadku wysyłania komunikatu (zwracającego wartość lub wywołania operacji) można przekazać <xref:System.IO.FileStream> infrastrukturę usługi WCF, a następnie pobrać wszystkie dane z tego strumienia do momentu całkowitego odczytania strumienia i osiągnięcia EOF. Aby przesłać dane przesyłane strumieniowo dla źródła, które nie istnieje wcześniej utworzona <xref:System.IO.Stream> Klasa pochodna, konstrukcja takiej klasy, nałóż ją na źródło strumienia i Użyj tego jako argumentu lub wartości zwracanej.  
  
 W przypadku otrzymania komunikatu Funkcja WCF konstruuje strumień za pośrednictwem zawartości treści komunikatu kodowanej algorytmem Base64 (lub odpowiedniej części MIME, jeśli jest używany), a strumień osiągnie wartość EOF, gdy zawartość została odczytana.  
  
 Przesyłanie strumieniowe na poziomie transportu działa również z dowolnym innym typem kontraktu komunikatu (listami parametrów, argumentami kontraktu danych i umową z jawnym komunikatem), ale ponieważ Serializacja i deserializacja takich komunikatów o określonym typie wymaga buforowania przez serializator nie zaleca się używania takich wariantów kontraktu.  
  
### <a name="special-security-considerations-for-large-data"></a>Specjalne zagadnienia dotyczące zabezpieczeń w przypadku dużych ilości danych  
 Wszystkie powiązania umożliwiają ograniczenie rozmiaru komunikatów przychodzących, aby zapobiec atakom typu "odmowa usługi". Na przykład uwidacznia Właściwość [System. ServiceModel. BasicHttpBinding. MaxReceivedMessageSize](xref:System.ServiceModel.HttpBindingBase.MaxReceivedMessageSize%2A) , która wiąże się z rozmiarem komunikatu przychodzącego, a także wiąże się z maksymalną ilością pamięci, do której uzyskuje się dostęp podczas przetwarzania <xref:System.ServiceModel.BasicHttpBinding> Komunikat. Ta jednostka jest ustawiona w bajtach z wartością domyślną 65 536 bajtów.  
  
 Zagrożenie bezpieczeństwa specyficzne dla scenariusza dużego przesyłania strumieniowego danych wywołuje odmowę usługi, powodując, że dane są buforowane, gdy odbiornik oczekuje na przesłanie strumieniowo. Na przykład usługa WCF zawsze buforuje nagłówki protokołu SOAP, a więc osoba atakująca może utworzyć dużą złośliwą wiadomość, która składa się w całości z nagłówków, aby wymusić, że dane mają być buforowane. Gdy funkcja przesyłania strumieniowego jest `MaxReceivedMessageSize` włączona, można ustawić niezwykle dużą wartość, ponieważ odbiornik nigdy nie oczekuje, że cały komunikat jest buforowany w pamięci jednocześnie. Jeśli funkcja WCF jest zmuszona do buforowania komunikatu, wystąpi przepełnienie pamięci.  
  
 W związku z tym ograniczenie maksymalnego rozmiaru komunikatu przychodzącego nie jest wystarczające w tym przypadku. `MaxBufferSize` Właściwość jest wymagana, aby ograniczyć ilość pamięci buforów WCF. Należy pamiętać, aby ustawić wartość bezpieczną (lub zachować wartość domyślną) podczas przesyłania strumieniowego. Załóżmy na przykład, że usługa musi odbierać pliki o rozmiarze do 4 GB i przechowywać je na dysku lokalnym. Załóżmy również, że pamięć jest ograniczona w taki sposób, że w danym momencie można buforować tylko 64 KB danych. Następnie ustaw `MaxReceivedMessageSize` wartość 4 GB i `MaxBufferSize` na 64 KB. Ponadto w implementacji usługi należy upewnić się, że użytkownik ma uprawnienia tylko do odczytu ze strumienia przychodzącego w fragmentach 64-KB i nie odczytuje następnego fragmentu, zanim poprzedni zostanie zapisany na dysku i odrzucony z pamięci.  
  
 Ważne jest również, aby zrozumieć, że ten limit przydziału ogranicza buforowanie wykonywane przez WCF i nie może chronić użytkownika przed żadnym buforowaniem wykonywanym we własnej implementacji usługi lub klienta. Aby uzyskać więcej informacji o dodatkowych kwestiach dotyczących zabezpieczeń, zobacz [zagadnienia dotyczące zabezpieczeń danych](../../../../docs/framework/wcf/feature-details/security-considerations-for-data.md).  
  
> [!NOTE]
> Decyzja o użyciu buforowanych lub przesyłanych strumieniowo jest lokalną decyzją punktu końcowego. W przypadku transportów HTTP tryb transferu nie jest propagowany przez połączenie lub serwery proxy i innych pośredników. Ustawienie trybu transferu nie jest odzwierciedlone w opisie interfejsu usługi. Po wygenerowaniu klienta programu WCF do usługi należy edytować plik konfiguracji usług przeznaczonych do użycia z transferem strumieniowym w celu ustawienia trybu. W przypadku transportów TCP i nazwanych potoków tryb transferu jest propagowany jako potwierdzenie zasad.  
  
## <a name="see-also"></a>Zobacz także

- [Instrukcje: Włącz przesyłanie strumieniowe](../../../../docs/framework/wcf/feature-details/how-to-enable-streaming.md)
