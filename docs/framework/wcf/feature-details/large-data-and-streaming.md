---
title: "Duże ilości danych i przesyłanie strumieniowe"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ab2851f5-966b-4549-80ab-c94c5c0502d2
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: e9551fcf4f302be899dcee8737b3bcfad15f1210
ms.sourcegitcommit: cf22b29db780e532e1090c6e755aa52d28273fa6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/01/2018
---
# <a name="large-data-and-streaming"></a>Duże ilości danych i przesyłanie strumieniowe
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] to infrastruktura komunikacji opartych na języku XML. Ponieważ dane XML często jest zakodowany w formacie tekstu standardowego, zdefiniowane w [Specyfikacja XML 1.0](http://go.microsoft.com/fwlink/?LinkId=94838), połączonych projektanci systemów i architektów zwykle niepokoi rozmiaru danych przesyłanych w sieci (lub rozmiar) komunikaty wysyłane między sieci i kodowanie tekstowy XML stanowi wyzwanie specjalne wydajność transferu danych binarnych.  
  
## <a name="basic-considerations"></a>Podstawowe zagadnienia  
 Aby podać ogólne informacje o następujące informacje dotyczące [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], w tej sekcji opisano niektóre problemy ogólne i zagadnienia dotyczące kodowania, dane binarne i przesyłania strumieniowego które zwykle dotyczą połączonych systemów infrastruktury.  
  
### <a name="encoding-data-text-vs-binary"></a>Dane kodowania: Vs tekstu. plików binarnych  
 Często wyrażane developer problemy obejmują wrażenie, że XML ma znaczne obciążenie w porównaniu do formatów binarnych z powodu powtarzających się charakter początkowe tagi i tagami końcowymi, czy kodowanie wartości liczbowe uważa się znacznie większe ponieważ są one wyrażone w wartości tekstowe i danych binarnych nie można wyrazić wydajne, ponieważ musi być specjalnie zakodowany na osadzanie w formacie tekstowym.  
  
 Wiele z tych i podobne dotyczy są prawidłowe, rzeczywista różnica między wiadomości tekstu XML zakodowane w środowisku usług XML sieci Web i binarnie wiadomości w starszej wersji zdalne wywołanie procedury (RPC) środowiska jest często znacznie mniej znaczących niż może sugerować początkowej brany pod uwagę.  
  
 Podczas tekstu XML zakodowanego wiadomości są niewidoczne i "do odczytu", binary wiadomości są często dość zasłoniętej porównania i trudne do zdekodowania bez narzędzia. Różnica w czytelności prowadzi do przeoczenia czy binarny wiadomości również często przenoszenia metadanych wbudowany w ładunku, który dodaje nakładów pracy, tak jak w przypadku wiadomości tekstowe XML. Ta zasada dotyczy w szczególności dla danych binarnych formatów, które mają na celu dostarczenie luźno sprzężenia i dynamicznych wywołania funkcji.  
  
 Formacie binarnym często zawierają takie informacje opisowe metadanych w "Nagłówek z" deklaruje również układ danych dla następujących rekordów danych. Ładunek następnie następuje tej deklaracji wspólnej bloku metadanych przy minimalnym obciążeniu dalsze. Z kolei XML umieszcza każdego elementu danych w element lub atrybut tak, aby otaczającego metadanych kilkukrotnie uwzględniane dla poszczególnych obiektów serializowanych ładunku. W związku z tym rozmiar obiektu w jednym ładunku serializacji przypomina podczas porównywania tekst reprezentacje binarne jako niektóre metadane opisowe muszą być wyrażone zarówno, ale korzyści format binarny z opisu udostępnionych metadanych z każdym dodatkowe Obiekt ładunku jest przenoszona z powodu mniejszy narzut ogólnej.  
  
 Nadal, dla niektórych typów danych, takich jak numery, może być wadą przy użyciu stałym rozmiarze, binary reprezentacje numeryczne, 128-bitowego typu decimal zamiast zwykłego tekstu, np. jako zwykły tekst reprezentacja może być kilka mniejszych bajtów. Dane tekstowe może być również rozmiar korzyści z zazwyczaj bardziej elastyczne tekstu XML, kodowania opcji, gdy niektóre formaty binarne mogą domyślnie Unicode 16-bitowego lub nawet 32-bitowe, które nie ma zastosowania do formatu XML binarnego .NET.  
  
 W związku z tym podjęciem decyzji o tekst lub binarny nie jest dość tak proste, jak przy założeniu binarne komunikaty są zawsze mniejszy niż wiadomości tekstowe XML.  
  
 Wyczyść zaletą wiadomości tekstowe XML jest są oparte na standardach i oferują najszerszych wybór opcji współdziałanie i Obsługa platform. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]w sekcji "Kodowania" w dalszej części tego tematu.  
  
### <a name="binary-content"></a>Zawartość binarna  
 Jeden obszar, w których kodowania binarnego są nadrzędne w stosunku do tekstowych kodowania pod względem wynikowy rozmiar wiadomości są dużych danych binarnych elementy, takie jak zdjęcia, wideo, dźwięki lub jakąkolwiek inną formę nieprzezroczyste, binarne dane, które muszą być wymieniane między usługami i ich konsumentów. Aby dopasować te typy danych do tekstu XML, typowym podejściem jest kodować je przy użyciu kodowania Base64.  
  
 W ciągu zakodowanego algorytmem Base64 każdego znaku reprezentuje 6-bitowej oryginalnych danych 8-bitową, co powoduje stosunek kodowanie koszty 4:3 dla Base64, nie licząc bardzo formatowanie znaków (CR/LF), które są często dodane przez Konwencję. Gdy znaczenie różnice między XML i kodowanie binarne zwykle zależy od scenariusza, przyrost rozmiaru więcej niż % 33 przy przekazywaniu ładunku 500 MB zazwyczaj nie jest akceptowane.  
  
 Aby uniknąć tego kodowania nakład pracy mechanizmu optymalizacji transmisji wiadomości (MTOM) standard umożliwia jego oddzielenie elementy dużej ilości danych, które są zawarte w wiadomości i wykonywanie ich z komunikatem jako dane binarne bez żadnych kodowania. Z MTOM komunikaty są wymieniane w sposób podobny do transferu protokołu SMTP (Simple Mail) wiadomości e-mail z załącznikami lub osadzonej zawartości (obrazów i innej zawartości embedded); Komunikaty mechanizmu MTOM są dostarczane w sekwencji MIME multipart/związane z częścią głównego jest rzeczywista komunikatu protokołu SOAP.  
  
 Komunikat mechanizmu MTOM SOAP są modyfikowane z jego wersja nie jest zakodowany tak, aby tagi specjalne elementów, które odwołują się do odpowiednich części MIME miejsce elementów oryginalnej wiadomości, która zawiera dane binarne. W związku z tym komunikatu protokołu SOAP odwołuje się do zawartości binarnej poprzez wskazanie części MIME wysyłane z nim, ale w przeciwnym razie po prostu przenosi dane tekstowe XML. Ten model jest ściśle wyrównany z ustalonymi modelu SMTP, nie istnieje szerokie narzędzia pomocy technicznej do kodowania i dekodowania komunikaty mechanizmu MTOM na wielu platformach, co czyni go bardzo interoperacyjne wybór.  
  
 Nadal podobnie jak w przypadku Base64, MTOM również zawiera pewne koszty niezbędne w formacie MIME tak, aby korzyści wynikające z używania MTOM są tylko widoczne, gdy rozmiar elementu danych binarnych przekracza około 1 KB. Ze względu na obciążenie wiadomości w formacie MTOM może być większa niż wiadomości, korzystających z kodowania Base64 dla danych binarnych, jeśli ładunek danych binarnych pozostaje poniżej tej wartości progowej. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]w sekcji "Kodowania" w dalszej części tego tematu.  
  
### <a name="large-data-content"></a>Zawartość dużej ilości danych  
 Przewodowy poziomu Odłóż, opisane powyżej ładunku 500 MB również stanowi doskonałe wyzwanie lokalnego na usługę i klienta. Domyślnie [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] przetwarza wiadomości w *tryb buforowany*. Oznacza to, że cała zawartość komunikatu jest dostępny w pamięci przed wysłaniem lub po odebraniu. Gdy to dobre rozwiązanie dla większości scenariuszy i niezbędne do obsługi funkcji, takich jak podpisów cyfrowych i niezawodne dostarczanie dużych wiadomości może wyczerpać zasobów systemowych.  
  
 Strategii postępowania w przypadku dużych ładunków jest przesyłania strumieniowego. Podczas wiadomości często zwłaszcza tych, które wyrażoną w kodzie XML, są uważane jako względnie compact danych, komunikat może mieć rozmiar wielu gigabajtów i podobne strumień danych ciągłego ponad pakietu danych. Gdy dane są przesyłane w trybie przesyłania strumieniowego zamiast tryb buforowany, nadawca udostępnia zawartość treści wiadomości do adresata w formie strumienia i infrastruktury komunikatów stale przekazuje dane od nadawcy do odbiornika jako staje się dostępne.  
  
 Najbardziej typowym scenariuszem takiej zawartości dużej ilości danych, będą wykonywane transferów są transferów danych binarnych obiekty, które:  
  
-   Nie można łatwo podzielić w sekwencji komunikatów.  
  
-   Musi zostać dostarczony w odpowiednim czasie.  
  
-   Nie są dostępne w całości po zainicjowaniu transferu.  
  
 Dla danych, który nie ma tych ograniczeń, zazwyczaj lepiej jest wysyłanie sekwencji komunikatów w zakresie sesji niż jeden komunikat duże. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]sekcja "Dane przesyłania strumieniowego" w dalszej części tego tematu.  
  
 Podczas wysyłania dużych ilości danych należy ustawić `maxAllowedContentLength` ustawienie programu IIS (Aby uzyskać więcej informacji, zobacz [Konfigurowanie limity żądań usług IIS](http://go.microsoft.com/fwlink/?LinkId=253165)) i `maxReceivedMessageSize` powiązanie ustawienie (na przykład [ System.ServiceModel.BasicHttpBinding.MaxReceivedMessageSize](xref:System.ServiceModel.HttpBindingBase.MaxReceivedMessageSize%2A) lub <xref:System.ServiceModel.NetTcpBinding.MaxReceivedMessageSize%2A>). `maxAllowedContentLength` Wartości domyślne właściwości 28.6 m i `maxReceivedMessageSize` właściwość domyślnie 64 KB.  
  
## <a name="encodings"></a>Kodowanie  
 *Kodowanie* definiuje zestaw reguł temat do prezentowania wiadomości w sieci. *Koder* implementuje takie kodowania i odpowiada na stronie nadawcy Włączanie <xref:System.ServiceModel.Channels.Message> w pamięci komunikatu jako strumień bajtów lub Bufor bajtów, które mogą być wysyłane przez sieć. Na stronie odbiorcy koder włącza sekwencję bajtów do wiadomości w pamięci.  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] obejmuje trzy koderów i pozwala wpisać i dołączyć własnego koderów w razie potrzeby.  
  
 Każdy powiązań standardowych obejmuje wstępnie skonfigurowane kodera, zgodnie z którymi powiązania z prefiksem Net * Użyj kodera binarnego (umieszczając <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement> klasy) podczas <xref:System.ServiceModel.BasicHttpBinding> i <xref:System.ServiceModel.WSHttpBinding> klasy używać kodera wiadomości tekstowych (za pomocą klasy <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement> klasy) domyślnie.  
  
|Element powiązania kodera|Opis|  
|-----------------------------|-----------------|  
|<xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>|Kodera wiadomości tekstowych jest kodera domyślnego dla wszystkich powiązań oparte na protokole HTTP i wybór odpowiedniego dla wszystkich powiązań niestandardowych, gdzie współdziałanie jest najwyższym problemu. Ten koder odczytuje i zapisuje standardowego protokołu SOAP 1.1 SOAP 1.2 wiadomości SMS z nie specjalnej obsługi dla danych binarnych. Jeśli <xref:System.ServiceModel.Channels.MessageVersion> wiadomości ma ustawioną wartość `None`, pominięcia otoki koperty protokołu SOAP z danych wyjściowych i jest serializowany zawartość treści komunikatu.|  
|<xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement>|Koder komunikatu MTOM jest koder tekstu, który implementuje specjalnej obsługi dla danych binarnych i nie jest używany domyślnie w jednym z powiązań standardowych, ponieważ ściśle to narzędzie optymalizacji w każdym przypadku. Jeśli komunikat zawiera dane binarne, która przekracza próg, gdzie kodowanie MTOM daje korzyści, danych jest externalized do części MIME po koperty wiadomości. Zobacz Włączanie MTOM w dalszej części tej sekcji.|  
|<xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>|Koder komunikatu binarnego jest kodera domyślnego dla powiązania Net * i odpowiednie polecenie zawsze, gdy oba komunikującymi się Stronami są oparte na [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]. Koder komunikatów binarnych używa .NET XML formatu binarnego, to binarna reprezentacja specyficzne dla firmy Microsoft dla zestawów informacji XML (Infosets), który zazwyczaj daje mniejsze zużycie niż równoważne reprezentacji XML 1.0 koduje dane binarne jako typu byte strumień.|  
  
 Kodowanie komunikatu tekst jest zwykle najlepszym wyborem umożliwiającym dowolną ścieżkę komunikacji, który wymaga współdziałanie, podczas gdy Kodowanie komunikatu binarnego jest najlepszym rozwiązaniem dla dowolnej innej ścieżki komunikacji. Kodowanie komunikatu binarnego daje zwykle mniejsze rozmiary i tekst w pojedynczym komunikacie i stopniowo mniejszy komunikat rozmiary w czasie trwania sesji komunikacji wiadomości. W przeciwieństwie do kodowania tekstu, kodowanie binarne nie trzeba używać specjalnej obsługi dla danych binarnych, takich jak przy użyciu Base64, ale reprezentuje bajtów bajtów.  
  
 Jeśli rozwiązanie nie wymaga współdziałanie, ale nadal chcesz używać transportu HTTP, można utworzyć <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement> do niestandardowego powiązania, który używa <xref:System.ServiceModel.Channels.HttpTransportBindingElement> klasy dla transportu. Jeśli wielu klientów w usłudze wymagają współdziałania, zaleca się, że uwidaczniać równoległych punktów końcowych, że każdy ma odpowiednie transportu i opcje kodowania dla odpowiednich klientów włączone.  
  
### <a name="enabling-mtom"></a>Włączanie mechanizmu MTOM  
 Gdy wymagane jest współdziałanie i należy wysłać dużych danych binarnych, a następnie Kodowanie komunikatu MTOM jest alternatywnej kodowanie strategii, które można włączyć na standardzie <xref:System.ServiceModel.BasicHttpBinding> lub <xref:System.ServiceModel.WSHttpBinding> powiązania przez ustawienie odpowiednio `MessageEncoding` dla właściwości <xref:System.ServiceModel.WSMessageEncoding.Mtom> lub przez tworzenie <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement> do <xref:System.ServiceModel.Channels.CustomBinding>. Poniższy przykładowy kod, wyodrębniony z [kodowanie MTOM](../../../../docs/framework/wcf/samples/mtom-encoding.md) przykładowych pokazano, jak włączyć MTOM w konfiguracji.  
  
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
  
 Jak wspomniano wcześniej, decyzji o użyciu kodowanie MTOM zależy od ilość danych, z którego są wysyłane. Ponadto MTOM jest włączony na poziomie powiązanie, włączenie MTOM ma wpływ na wszystkie operacje w danym punkcie końcowym.  
  
 Ponieważ koder MTOM zawsze emituje MTOM zakodowane w formacie MIME/kilku-niepełnym komunikat niezależnie od tego, czy dane binarne kończy się on externalized, należy zwykle tylko włączać MTOM dla punktów końcowych, które wymiany wiadomości z więcej niż 1 KB danych binarnych. Ponadto kontraktów usług przeznaczony do użytku z włączoną MTOM punktami końcowymi Jeśli to możliwe, można ograniczyć do określenie takie operacje transferu danych. Funkcji pokrewnej kontrolki powinny znajdować się w oddzielnych kontraktu. To "Tylko MTOM" reguła dotyczy tylko wiadomości wysyłane za pośrednictwem punktu końcowego dla komputerów z obsługą MTOM; koder MTOM można zdekodować i przeanalizować również przychodzących wiadomości z systemem innym niż MTOM.  
  
 Przy użyciu koder MTOM jest zgodny z wszystkich innych [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] funkcji. Należy pamiętać, że może nie być możliwe obserwować tej reguły we wszystkich przypadkach, takich jak gdy wymagana jest obsługa sesji.  
  
### <a name="programming-model"></a>Model programowania  
 Niezależnie od tego, który trzy koderów wbudowanych użycia we własnej aplikacji środowisko programowania jest identyczna w odniesieniu do transferowania danych binarnych. Jest to różnica w sposób [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] obsługi danych na podstawie ich typów danych.  
  
```  
[DataContract]  
class MyData  
{  
    [DataMember]  
    byte[] binaryBuffer;  
    [DataMember]  
    string someStringData;  
}   
```  
  
 Używając MTOM poprzedniego kontrakt danych jest serializowany zgodnie z następującymi zasadami:  
  
-   Jeśli `binaryBuffer` nie jest `null` i indywidualnie zawiera za mało danych do justify obciążenie externalization MTOM (nagłówków MIME itd.) w porównaniu do formatu Base64 kodowania, dane są externalized i przenoszona z komunikatu jako binarne części MIME. Jeśli nie przekroczono progu, dane są kodowane jako Base64.  
  
-   Ciąg (i innych typów, które nie są binarne) zawsze jest reprezentowany jako ciąg wewnątrz treści wiadomości, niezależnie od rozmiaru.  
  
 Wpływa na kodowanie MTOM jest takie samo czy używać kontraktu danych jawne, jak pokazano w poprzednim przykładzie, użyj listę parametrów w operacji, mają kontraktów danych zagnieżdżonych lub przenieść obiekt kontraktu danych wewnątrz kolekcji. Tablice typu byte nadają się zawsze do optymalizacji i są zoptymalizowane, jeśli spełnione są progi optymalizacji.  
  
> [!NOTE]
>  Nie powinien być używany <xref:System.IO.Stream?displayProperty=nameWithType> pochodnych typów wewnątrz kontraktów danych. Strumień danych powinny być przekazywane przy użyciu modelu przesyłania strumieniowego, wyjaśniono w poniższej sekcji "Dane przesyłane strumieniowo".  
  
## <a name="streaming-data"></a>Dane przesyłane strumieniowo  
 Jeśli masz dużą ilość danych do przesłania tryb strumieniowy transfer w [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] jest możliwe alternatywą do domyślne zachowanie buforowania i przetwarzanie komunikatów w pamięci w całości.  
  
 Jak wspomniano wcześniej, należy włączyć strumienia tylko w przypadku dużych wiadomości (z zawartością tekst lub binarny), jeśli dane nie segmentem, jeśli wiadomość musi zostać dostarczona w odpowiednim czasie lub danych nie jest jeszcze całkowicie dostępna po zainicjowaniu transferu.  
  
### <a name="restrictions"></a>Ograniczenia  
 Nie można użyć znaczących [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] funkcji po włączeniu przesyłania strumieniowego:  
  
-   Nie można wykonać podpisów cyfrowych dla treści wiadomości, ponieważ wymagają one obliczania skrótu za pośrednictwem zawartość cały komunikat. W przypadku przesyłania strumieniowego zawartości nie jest całkowicie dostępne, gdy nagłówki komunikatów są konstruowane i wysyłane i dlatego nie można obliczyć podpisu cyfrowego.  
  
-   Szyfrowanie jest zależna od podpisów cyfrowych, aby sprawdzić, czy dane zostały odtworzone poprawnie.  
  
-   Niezawodne sesje musi buforu wysłanych komunikatów na kliencie ponowne dostarczenie wiadomości pobiera zgubiony transferu i musi posiadać komunikatów w usłudze przed przekazaniem ich do implementacji usługi w celu zachowania kolejności wiadomości, w przypadku, gdy są odbierane wiadomości poza sekwencji.  
  
 Ze względu na te ograniczenia funkcjonalności można użyć opcji przesyłania strumieniowego i użytkownik nie może włączyć niezawodnej sesji zabezpieczeń tylko poziomu transportu. Przesyłanie strumieniowe jest dostępna tylko w następujących powiązań zdefiniowanych w systemie:  
  
-   <xref:System.ServiceModel.BasicHttpBinding>  
  
-   <xref:System.ServiceModel.NetTcpBinding>  
  
-   <xref:System.ServiceModel.NetNamedPipeBinding>  
  
-   <xref:System.ServiceModel.WebHttpBinding>  
  
 Ponieważ podstawowej transport <xref:System.ServiceModel.NetTcpBinding> i <xref:System.ServiceModel.NetNamedPipeBinding> związanego z używaniem niezawodnego dostarczania i opartego na połączeniach sesji pomocy technicznej, w odróżnieniu od protokołu HTTP, te dwa powiązania tylko minimalny zestaw dotyczy tych warunków ograniczających w praktyce.  
  
 Przesyłanie strumieniowe jest niedostępna, gdy transport usługi kolejkowania komunikatów (MSMQ) i dlatego nie można używać z <xref:System.ServiceModel.NetMsmqBinding> lub <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> klasy. Transportu MSMQ tylko obsługuje transferów buforowane dane o rozmiarze ograniczonego komunikat, a wszystkie inne transportów nie ma żadnych limit rozmiaru wiadomości praktyczne większość scenariuszy.  
  
 Przesyłanie strumieniowe jest również niedostępna, gdy przy użyciu kanału równorzędnego transportu, dlatego nie jest dostępna z <xref:System.ServiceModel.NetPeerTcpBinding>.  
  
#### <a name="streaming-and-sessions"></a>Przesyłania strumieniowego i sesji  
 Mogą wystąpić nieoczekiwane zachowanie podczas przesyłania strumieniowego wywołania z powiązaniem opartymi na sesji. Wszystkie wywołania przesyłania strumieniowego są nawiązywane przy użyciu jednego kanału (kanale datagramowym), który nie obsługuje sesji, nawet jeśli powiązania, używany jest skonfigurowana do używania sesji. Jeśli wielu klientów wywołań przesyłania strumieniowego do tego samego obiektu usługi za pośrednictwem powiązania opartymi na sesji i tryb współbieżności obiekt usługi jest ustawiony na jednym i jej wystąpienia kontekstu tryb ma ustawioną wartość PerSession, wywołania musi przechodzić przez kanał datagram i dlatego tylko jeden wywołania są przetwarzane pojedynczo. Co najmniej jeden klient następnie może upłynął limit czasu. Ten problem można obejść przez ustawienie Tryb kontekstu wystąpienia obiektu usługi PerCall lub współbieżności do wielu.  
  
> [!NOTE]
>  MaxConcurrentSessions w tym przypadku jest nieskuteczne, ponieważ jest dostępna tylko jedna "sesja".  
  
### <a name="enabling-streaming"></a>Włączanie przesyłania strumieniowego  
 Można włączyć przesyłania strumieniowego w następujący sposób:  
  
-   Wysyłanie i akceptowania żądań w trybie przesyłania strumieniowego i zaakceptować i zwracanie odpowiedzi w tryb buforowany (<xref:System.ServiceModel.TransferMode.StreamedRequest>).  
  
-   Wysyłanie i akceptowania żądań w tryb buforowany i zaakceptować i zwracać odpowiedzi w trybie przesyłanej strumieniowo (<xref:System.ServiceModel.TransferMode.StreamedResponse>).  
  
-   Wysyłanie i odbieranie żądań i odpowiedzi w trybie przesyłanej strumieniowo w obu kierunkach. (<xref:System.ServiceModel.TransferMode.Streamed>).  
  
 Możesz wyłączyć przesyłania strumieniowego przez ustawienie Tryb transferu <xref:System.ServiceModel.TransferMode.Buffered>, co jest ustawieniem domyślnym na wszystkie powiązania. Poniższy kod przedstawia sposób ustawiania tryb transferu w konfiguracji.  
  
```xml  
<system.serviceModel>  
     …  
    <bindings>  
      <basicHttpBinding>  
        <binding name="ExampleBinding" transferMode="Streaming"/>  
      </basicHttpBinding>  
    </bindings>  
     …  
<system.serviceModel>  
```  
  
 Podczas wystąpienia wiązania w kodzie, należy ustawić odpowiednie `TransferMode` właściwości powiązania (lub jeśli redagowania niestandardowego powiązania elementu powiązania transportu) na jedną z wymienionych wcześniej wartości.  
  
 Można włączyć przesyłania strumieniowego dla żądań i odpowiedzi lub dla obu kierunków niezależnie na każdej stronie komunikującymi się Stronami bez wpływu na funkcjonalność. Jednak należy zawsze przyjęto, że rozmiar przekazywanych danych zostało tak istotne jest, że włączenie przesyłania strumieniowego jest uzasadnione na oba punkty końcowe łącza komunikacyjnego. Do komunikacji między platformami, gdy jeden z punktów końcowych nie został zaimplementowany w [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], możliwość używania przesyłania strumieniowego zależy od możliwości przesyłania strumieniowego platformy. Kolejny wyjątek rzadkich może być obsługiwanego scenariusza, w którym klienta lub usługę należy zminimalizować jej zestawu roboczego i może pozwolić buforu małych rozmiarów zużycie pamięci.  
  
### <a name="enabling-asynchronous-streaming"></a>Włączanie asynchronicznego przesyłania strumieniowego  
 Aby włączyć, asynchronicznego przesyłania strumieniowego, Dodaj <xref:System.ServiceModel.Description.DispatcherSynchronizationBehavior> zachowania punktu końcowego usługi hosta i ustaw jej <xref:System.ServiceModel.Description.DispatcherSynchronizationBehavior.AsynchronousSendEnabled%2A> właściwości `true`. Dodaliśmy również możliwości wartość true, asynchronicznego przesyłania strumieniowego po stronie wysyłającej. Zwiększa to skalowalność usługi w scenariuszach, w którym jest strumienia komunikatów do wielu klientów, niektóre z nich są przetwarzane wolno podczas odczytywania prawdopodobnie z powodu przeciążenia sieci lub nie są w ogóle odczytywania. W tych scenariuszach mamy teraz nie blokują poszczególnych wątków w usłudze na klienta. Dzięki temu, że usługa jest w stanie przetwarzać wiele większej liczby klientów w celu poprawy skalowalności usługi.  
  
### <a name="programming-model-for-streamed-transfers"></a>Model programowania transferów przesyłanej strumieniowo  
 Model programowania do przesyłania strumieniowego jest prosta. Odbieranie danych przesyłany strumieniowo, określ kontrakt operacji, który ma jeden <xref:System.IO.Stream> wpisane parametru wejściowego. Do zwracania danych przesyłany strumieniowo, zwróć <xref:System.IO.Stream> odwołania.  
  
```  
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
  
 Operacja `Echo` w poprzednim przykładzie odbiera i zwraca strumienia i dlatego powinien być używany w powiązaniu z <xref:System.ServiceModel.TransferMode.Streamed>. Dla operacji `RequestInfo`, <xref:System.ServiceModel.TransferMode.StreamedResponse> najlepiej nadaje się, ponieważ tylko zwraca <xref:System.IO.Stream>. Operacja jednokierunkowa najlepiej nadaje się do <xref:System.ServiceModel.TransferMode.StreamedRequest>.  
  
 Należy pamiętać, że dodanie drugi parametr dla następujących `Echo` lub `ProvideInfo` operacji powoduje modelu usługi powrócić do buforowanego strategii i użyj środowiska wykonawczego serializacji reprezentację strumienia. Tylko operacje z parametrem jednego strumienia wejściowego są zgodne z żądaniem end-to-end przesyłania strumieniowego.  
  
 Ta zasada dotyczy podobnie kontraktów komunikatu. Jak pokazano na poniższej kontraktu komunikatu, mogą mieć tylko członek jednej jednostki w sieci kontraktu komunikatu, który jest typu stream. Jeśli chcesz przekazać dodatkowe informacje o strumieniu, te informacje musi być wykonana w nagłówkach wiadomości. Treść komunikatu jest zastrzeżone wyłącznie dla zawartości strumienia.  
  
```  
[MessageContract]  
public class UploadStreamMessage  
{  
   [MessageHeader]  
   public string appRef;  
   [MessageBodyMember]  
   public Stream data;  
}   
```  
  
 Zakończenia transferu przesyłanej strumieniowo i komunikat jest zamknięty, gdy strumień osiągnie koniec pliku (EOF). Podczas wysyłania komunikatu (zwracanie wartości lub wywołaniem operacji), można przekazać <xref:System.IO.FileStream> i [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] infrastruktury następnie pobiera wszystkie dane tego strumienia, dopóki strumień całkowicie odczytane i osiągnięto koniec pliku. Na przesyłanie danych przesyłany strumieniowo źródła który nie takich wbudowanych <xref:System.IO.Stream> istnieje w klasie pochodnej, utworzyć taka klasa nakładki tej klasy w źródle strumienia i używać go jako wartość argumentu lub return.  
  
 Podczas odbierania komunikatu, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] konstruuje strumienia za pośrednictwem wiadomości algorytmem Base64 body zawartości (lub odpowiednich części MIME, jeśli przy użyciu mechanizmu MTOM), a strumień osiągnie EOF przeczytaniu zawartości.  
  
 Również poziomu transportu strumieniowego działa z żadnych innych typ kontraktu komunikatu (listy parametrów, argumentów kontraktu danych i kontraktu komunikatu jawne), ale ponieważ serializacji i deserializacji takich wpisane wiadomości, wymagane jest buforowanie przez serializator , za pomocą takich wariantów kontrakt nie jest zalecane.  
  
### <a name="special-security-considerations-for-large-data"></a>Zagadnienia dotyczące zabezpieczeń specjalne dla dużej ilości danych  
 Wszystkie powiązania pozwalają ograniczyć rozmiar wiadomości przychodzących, aby zapobiec atakom typu "odmowa usługi". <xref:System.ServiceModel.BasicHttpBinding>, Na przykład przedstawia [System.ServiceModel.BasicHttpBinding.MaxReceivedMessageSize](xref:System.ServiceModel.HttpBindingBase.MaxReceivedMessageSize%2A) właściwości zakresem rozmiar wiadomości przychodzącej, a więc także zakresem maksymalną ilość pamięci, który jest dostępny podczas przetwarzania wiadomości. Ta jednostka ma wartość w bajtach z wartością domyślną 65 536 bajtów.  
  
 Na zagrożenia bezpieczeństwa, które są specyficzne dla scenariusza przesyłania strumieniowego dużej ilości danych provokes typu "odmowa usługi", powodując dane buforowane podczas odbiornika oczekuje przesyłane strumieniowo. Na przykład [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] zawsze buforuje nagłówków protokołu SOAP wiadomości, i dlatego osoba atakująca może konstruować dużych niebezpieczną wiadomość, która składa się wyłącznie z nagłówków, aby wymusić dane buforowane. Po włączeniu przesyłania strumieniowego `MaxReceivedMessageSize` może być ustawiony na bardzo dużą wartość, ponieważ odbiornika oczekuje nigdy nie cały komunikat, aby jednocześnie buforowane w pamięci. Jeśli [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] wymuszono buforu komunikat występuje przepełnienie pamięci.  
  
 W związku z tym ograniczenie maksymalny rozmiar wiadomości przychodzącej nie jest wystarczająco w takim przypadku. `MaxBufferSize` Jest wymagana właściwość, aby ograniczyć ilość pamięci który [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] buforów. Ważne jest, aby to ustawienie na wartość bezpieczne (lub zachowania jej wartość domyślną) podczas przesyłania strumieniowego. Załóżmy na przykład, usługa musi otrzymać pliki o rozmiarze do 4 GB i przechowywać je na dysku lokalnym. Załóżmy również, że pamięć jest ograniczona w taki sposób, można tylko buforu 64 KB danych w czasie. Następnie należy ustawić `MaxReceivedMessageSize` do 4 GB i `MaxBufferSize` 64 KB. Ponadto w implementacji usługi, należy tylko odczytywać przychodzący strumień w fragmentów 64 KB, a nie odczytuj dalej fragmentu przed poprzedniego został zapisany na dysku i usuwane z pamięci.  
  
 Jest również wziąć pod uwagę, że przydział ogranicza tylko buforowania programach [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] i nie można chronić przed żadnych buforowania, należy wykonać w celu wykonania własne usługi lub klienta. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]zagadnienia dotyczące zabezpieczeń, zobacz [zagadnienia dotyczące zabezpieczeń dla danych](../../../../docs/framework/wcf/feature-details/security-considerations-for-data.md).  
  
> [!NOTE]
>  Decyzja o wykorzystaniu buforowane lub przesyłany strumieniowo transferu jest decyzji lokalnego punktu końcowego. Dla transportu HTTP tryb transferu nie propaguje przez połączenie lub serwerów proxy i innych pośredników. Ustawianie trybu transferu nie zostaną uwzględnione w opisie interfejsu usługi. Po wygenerowaniu [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] klienta do usługi, należy edytować pliku konfiguracji dla usług przeznaczony do użycia w przypadku transferów przesyłanej strumieniowo można ustawić trybu. Dla transportu nazwanego potoku i TCP tryb transferu jest propagowana jako potwierdzenia zasad.  
  
## <a name="see-also"></a>Zobacz też  
 [Instrukcje: włączanie przesyłania strumieniowego](../../../../docs/framework/wcf/feature-details/how-to-enable-streaming.md)
