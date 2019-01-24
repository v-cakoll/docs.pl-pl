---
title: Duże ilości danych i przesyłanie strumieniowe
ms.date: 03/30/2017
ms.assetid: ab2851f5-966b-4549-80ab-c94c5c0502d2
ms.openlocfilehash: c6514903294147671804b5b8de47fddc764b0547
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54674118"
---
# <a name="large-data-and-streaming"></a>Duże ilości danych i przesyłanie strumieniowe
Windows Communication Foundation (WCF) to infrastruktura komunikacji opartych na języku XML. Ponieważ dane XML zwykle jest zakodowane w formacie tekstu standardowego, zdefiniowane w [Specyfikacja XML 1.0](https://go.microsoft.com/fwlink/?LinkId=94838), połączone systemy, deweloperów i architektów są zazwyczaj zajmującym się ochroną zużycie o komunikacji sieciowej (lub rozmiar) komunikaty wysyłane między sieć i kodowanie oparte na tekście XML stanowi szczególne wyzwanie wydajny transfer danych binarnych.  
  
## <a name="basic-considerations"></a>Podstawowe zagadnienia  
 Aby podać ogólne informacje o następujące informacje dotyczące usługi WCF, w tej sekcji opisano niektóre ogólne problemy i zagadnienia dotyczące kodowania i danych binarnych i przesyłania strumieniowego, zazwyczaj dotyczą połączonych systemów infrastruktury.  
  
### <a name="encoding-data-text-vs-binary"></a>Kodowanie danych: Vs tekstu. plików binarnych  
 Problemy najczęściej zaakceptowania developer obejmują wrażenie, że plik XML zawiera znaczne obciążenie w porównaniu do formaty binarne ze względu na charakter powtarzające się znaczniki start i znacznikami końcowymi, czy kodowanie wartości liczbowych jest uważany za znacznie większą ponieważ są wyrażone w wartości tekstowe i danych binarnych nie można wyrazić efektywne, ponieważ muszą być specjalnie kodowane dla osadzania w formacie tekstowym.  
  
 Chociaż wiele z nich i podobnych zastosowaniach dotyczy są prawidłowe, rzeczywiste różnica między wiadomości tekstu XML kodowane w środowisku usług XML sieci Web i wiadomości w formacie pliku binarnego w starszej wersji zdalnego wywołania procedury (RPC) środowiska często jest znacznie mniej istotne niż może sugerować początkowej brany pod uwagę.  
  
 Podczas tekstu XML zakodowany komunikaty są niewidoczne a "do odczytu", komunikatów binarnych często są dość zasłoniętej porównania i trudne do zdekodowania bez narzędzi. Różnica w uzyskać jego lepszą czytelność prowadzi do przeoczyć, że komunikatów binarnych przenoszenia często wbudowanych metadanych ładunek, który dodaje obciążenie, podobnie jak w przypadku wiadomości tekstowe XML. Ta zasada obowiązuje specjalnie dla danych binarnych formaty, w których mają na celu dostarczenie luźno sprzężenia i dynamiczne wywołania funkcji.  
  
 Formaty binarne często zawierają takie informacje opisowe metadanych w "Nagłówek" deklaruje również układ danych dla następujących rekordów danych. Ładunek następnie następuje po tej deklaracji wspólnego blok metadanych z minimalnym dodatkowe obciążenie. Z kolei XML otacza każdy element danych elementu lub atrybutu tak, aby otaczającej metadanych kilkukrotnie uwzględniane dla poszczególnych obiektów w ładunku serializowanych. W rezultacie, rozmiar obiektu jednym ładunku serializowanych przypomina podczas porównywania tekst do reprezentacji binarnych, ponieważ niektóre metadane opisowe muszą być wyrażone w obu przypadkach jednak korzyści format binarny z opisu udostępnionych metadanych z każdym dodatkowe Obiekt ładunku, który jest przekazywany z powodu mniejszy narzut ogólną.  
  
 Jednak dla niektórych typów danych, takich jak numery, może być niedogodność za pomocą stałym rozmiarze, binarne reprezentacje wartości liczbowych, 128-bitowego typu dziesiętnego zamiast zwykłego tekstu, np. jako zwykły tekst reprezentacji może być kilka mniejszych w bajtach. Dane tekstowe również może korzystnie wpływać na rozmiar z zazwyczaj bardziej elastyczne tekstu XML, kodowania opcji, podczas gdy niektóre formaty binarne mogą domyślnie 16-bitowych lub nawet 32-bitowy Unicode, które nie ma zastosowania do formatu XML binarne .NET.  
  
 W rezultacie podjęciem decyzji o tekstowych lub binarnych nie jest dość łatwe jak zakładając, że komunikatów binarnych zawsze są mniejsze niż wiadomości tekstowe XML.  
  
 Wyczyść zalet wiadomości tekstowe XML jest są oparte na standardach i oferują największą wybór opcji współpracy i pomoc techniczna platformy. Aby uzyskać więcej informacji zobacz sekcję "Kodowania" w dalszej części tego tematu.  
  
### <a name="binary-content"></a>Zawartość binarna  
 Jeden obszar, w których są oparte na tekście kodowania pod względem wynikowy rozmiar komunikatu przekracza kodami binarnymi są elementy dużych danych binarnych, takich jak obrazy, wideo, klipów dźwiękowych lub jakąkolwiek inną formę nieprzejrzystych, binarne dane, które muszą być wymieniane między usługami i ich odbiorcy. Aby dopasować te typy danych do tekstu XML, typowym podejściem jest kodować je przy użyciu kodowania Base64.  
  
 W ciągu zakodowanego algorytmem Base64 każdy znak reprezentuje 6 bitów oryginalnych danych 8-bitową, co skutkuje 4:3 kodowanie obciążenie współczynnik Base64, nie licząc zamykającego dodatkowego formatowania znaków (CR/LF), które są często dodane przez Konwencję. Gdy znaczenie różnice między XML i kodami binarnymi zwykle zależy od scenariusza, przyrost rozmiaru ponad 33% podczas przesyłania ładunku 500 MB zazwyczaj nie jest dopuszczalne.  
  
 Aby uniknąć tego kodowania obciążenie, mechanizmu optymalizacji transmisji wiadomości (MTOM) standard umożliwia oddzielenie elementy dużych ilości danych, które są zawarte w wiadomości i znajdują się komunikatem jako dane binarne bez żadnych kodowania. Za pomocą MTOM komunikaty są wymieniane w sposób podobny do transferu protokołu SMTP (Simple Mail) wiadomości e-mail z załącznikami lub osadzonej zawartości (obrazy i inną zawartość osadzoną); Komunikaty MTOM są spakowane jako sekwencje MIME multipart/związane z części głównej jest rzeczywista komunikatu protokołu SOAP.  
  
 Komunikat protokołu SOAP MTOM jest modyfikowana z jego usunięcie zakodowanym wersji, tak, aby znaczniki specjalne elementów, które odwołują się do odpowiedniej części MIME odbywać elementów oryginalnej wiadomości, która zawiera dane binarne. W rezultacie komunikatu protokołu SOAP odwołuje się do zawartości binarnej, wskazując części MIME wysyłane z niego, ale w przeciwnym razie po prostu niesie ze sobą dane tekstowe XML. Ten model jest ściśle powiązana z dobrze udokumentowana modelu SMTP, nie istnieje szerokie, narzędzia do obsługi do kodowania i dekodowania MTOM wiadomości na wielu platformach, co czyni go bardzo interoperacyjne wybór.  
  
 Nadal podobnie jak w formacie Base64, MTOM również jest dostarczany z pewien narzut niezbędne w formacie MIME, aby korzyści wynikające z używania MTOM są tylko widoczne, gdy rozmiar elementu danych binarnych przekracza rozmiar około 1 KB. Ze względu na obciążenie wiadomości w formacie MTOM może być większa niż wiadomości, które używają kodowania Base64 dla danych binarnych, jeśli ładunek danych binarnych pozostaje poniżej tej wartości progowej. Aby uzyskać więcej informacji zobacz sekcję "Kodowania" w dalszej części tego tematu.  
  
### <a name="large-data-content"></a>Zawartość dużych ilości danych  
 O komunikacji sieciowej — zużycie specjalnie, wymienionych wcześniej ładunku 500 MB stanowi również wspaniałe wyzwanie lokalnych, na dla usługi i klienta. Domyślnie program WCF przetwarza wiadomości w *tryb buforowany*. Oznacza to, że całą zawartość komunikatu jest obecne w pamięci, przed wysłaniem lub po ich odebraniu. Gdy to dobry strategii w przypadku większości scenariuszy i niezbędny do obsługi komunikatów funkcje, takie jak podpisów cyfrowych i niezawodne dostarczanie dużych komunikatów może wyczerpać zasobów systemowych.  
  
 Strategia radzenia sobie z dużych ładunków jest przesyłanie strumieniowe. Podczas wiadomości zwłaszcza tych, które wyrażone w formacie XML, są często traktowane jako pakiety danych stosunkowo compact, komunikat może mieć rozmiar wielu gigabajtów i przypominają strumienia ciągłego danych, więcej niż pakiet danych. Gdy dane są przesyłane w trybie przesyłania strumieniowego zamiast tryb buforowany, nadawca udostępnia zawartość treści wiadomości do odbiorcy w formie strumienia i infrastruktury komunikatów stale przekazuje dane od nadawcy do odbiorcy, ponieważ jest dostępna.  
  
 Najbardziej typowym scenariuszem, w którym takiej zawartości dużych ilości danych, które Transfer odbywa się czy opłata za transfery danych binarnych obiekty, które:  
  
-   Nie można łatwo podzielić na sekwencję wiadomości.  
  
-   Musi być dostarczane w sposób terminowy.  
  
-   Nie są dostępne w całości po zainicjowaniu transferu.  
  
 W przypadku danych, który nie ma tych warunków ograniczających zazwyczaj lepiej jest wysyłać sekwencje komunikaty w zakresie sesji niż jeden dużych bloków komunikatów. Aby uzyskać więcej informacji zobacz sekcję "Przesyłanie strumieniowe danych" w dalszej części tego tematu.  
  
 Podczas wysyłania dużych ilości danych należy ustawić `maxAllowedContentLength` ustawienie programu IIS (Aby uzyskać więcej informacji, zobacz [Konfigurowanie limity żądań usług IIS](https://go.microsoft.com/fwlink/?LinkId=253165)) i `maxReceivedMessageSize` powiązanie ustawienia (na przykład [ System.ServiceModel.BasicHttpBinding.MaxReceivedMessageSize](xref:System.ServiceModel.HttpBindingBase.MaxReceivedMessageSize%2A) lub <xref:System.ServiceModel.NetTcpBinding.MaxReceivedMessageSize%2A>). `maxAllowedContentLength` Właściwości wartość domyślna to 28.6 M i `maxReceivedMessageSize` właściwości wartość domyślna to 64 KB.  
  
## <a name="encodings"></a>Encodings  
 *Kodowanie* definiuje zestaw reguł o tym, jak prezentować wiadomości na łączu. *Kodera* implementuje takich kodowania i jest odpowiedzialny za, na stronie nadawcy włączenie w pamięci <xref:System.ServiceModel.Channels.Message> do strumienia bajtów lub buforem bajtów, które mogą być wysyłane przez sieć. Po stronie odbiorcy kodera włącza sekwencję bajtów do wiadomości w pamięci.  
  
 WCF zawiera trzy koderów i pozwala na zapis i dołączyć własnego kodery w razie potrzeby.  
  
 Każda standardowa powiązania obejmuje wstępnie skonfigurowane kodera, według której powiązania z prefiksem Net * Użyj kodera binarnego (umieszczając <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement> klasy) podczas <xref:System.ServiceModel.BasicHttpBinding> i <xref:System.ServiceModel.WSHttpBinding> klasy korzystać koder tekstu komunikatu (przez klasy <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement> klasy) domyślnie.  
  
|Koder elementu powiązania|Opis|  
|-----------------------------|-----------------|  
|<xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>|Koder komunikatów tekstu jest kodera domyślnego dla wszystkich opartych na protokole HTTP powiązań i odpowiednim wyborem dla wszystkich powiązań niestandardowych, gdzie współdziałanie jest kwestią najwyższy. Ten koder odczytuje i zapisuje standardowego protokołu SOAP 1.1 SOAP 1.2 wiadomości SMS za pomocą nie specjalnej obsługi dla danych binarnych. Jeśli <xref:System.ServiceModel.Channels.MessageVersion> wiadomości jest równa `None`otoki koperty protokołu SOAP jest pomijane w danych wyjściowych i zawartość treści komunikatu jest serializowana.|  
|<xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement>|Koder komunikatów MTOM jest koder tekstu, który implementuje specjalnej obsługi dla danych binarnych i nie jest używany domyślnie we wszystkich standardowych powiązania, ponieważ jest on ściśle narzędzie optymalizacji w każdym przypadku. Jeśli komunikat zawiera dane binarne, która przekracza próg, w którym kodowanie MTOM stopa, dane są zewnętrznych do części MIME, zgodnie z koperty wiadomości. Zobacz Włączanie MTOM w dalszej części tej sekcji.|  
|<xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>|Koder komunikatu binarnego jest kodera domyślnego dla Net * powiązań i odpowiednim wyborem zawsze wtedy, gdy obie strony komunikujące się opierają się na WCF. Koder komunikatu binarnego w formacie .NET binarne XML, reprezentacja binarna specyficzne dla firmy Microsoft, dla zestawów informacji XML (Infosets), która jest ogólnie daje mniejszy wyświetlacz niż równoważnych reprezentacji XML 1.0 koduje dane binarne w postaci bajtów strumień.|  
  
 Kodowanie wiadomości tekstowe jest zwykle najlepszym wyborem dla dowolnej ścieżki komunikacji, wymagającego współdziałania, w trakcie kodowania komunikatu binarnego jest najlepszym wyborem dla dowolnej innej ścieżki komunikacji. Zazwyczaj kodowania komunikatu binarnego daje wiadomości mniejszych rozmiarów w porównaniu do tekstu dla pojedynczego stopniowo mniejszych komunikat i rozmiary w czasie trwania sesji komunikacji. W przeciwieństwie do kodowania tekstu, kodowanie binarne nie trzeba używać specjalnej obsługi dla danych binarnych, takich jak przy użyciu Base64, ale reprezentuje bajtów jako bajtów.  
  
 Jeśli rozwiązanie nie wymaga współdziałania, ale nadal chcesz używać transportu HTTP, można utworzyć <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement> do niestandardowego powiązania, który używa <xref:System.ServiceModel.Channels.HttpTransportBindingElement> klasy dla transportu. Jeśli wielu klientów w usłudze wymagają współdziałania, zaleca się udostępnieniem równoległe punktów końcowych, że każdy ma odpowiednie transportu i opcji kodowania dla odpowiednich klientów włączone.  
  
### <a name="enabling-mtom"></a>Włączanie MTOM  
 Gdy wymagane jest współdziałanie i muszą być wysyłane duże ilości danych binarnych, a następnie Kodowanie komunikatu MTOM jest alternatywą kodowanie strategii, która pozwala na standardzie <xref:System.ServiceModel.BasicHttpBinding> lub <xref:System.ServiceModel.WSHttpBinding> powiązania, ustawiając do odpowiednich `MessageEncoding` Właściwość <xref:System.ServiceModel.WSMessageEncoding.Mtom> lub za pośrednictwem <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement> do <xref:System.ServiceModel.Channels.CustomBinding>. Poniższy przykład kodu, wyodrębnione z [kodowanie MTOM](../../../../docs/framework/wcf/samples/mtom-encoding.md) przykład pokazuje, jak włączyć MTOM w konfiguracji.  
  
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
  
 Jak wspomniano wcześniej, decyzji o użyciu, kodowanie MTOM zależy od ilości danych, które wysyłasz. Ponadto ponieważ MTOM jest włączana na poziomie powiązania, włączanie MTOM ma wpływ na wszystkie operacje w danym punkcie końcowym.  
  
 Koder MTOM zawsze emituje MTOM zakodowane w formacie MIME/wielu-niepełnym komunikat niezależnie od tego, czy dane binarne kończy się on zewnętrznych, więc należy zwykle tylko włączyć MTOM dla punktów końcowych, które wymiana komunikatów z więcej niż 1 KB danych binarnych. Również kontraktów usług przeznaczone do użytku z włączoną obsługą MTOM punktami końcowymi Jeśli to możliwe, można ograniczyć do określenia takich operacji transferu danych. Funkcje pokrewnej kontrolki powinien znajdować się w osobnej umowy. "Tylko MTOM" stosowana ta reguła tylko komunikaty wysyłane za pośrednictwem punktu końcowego dla komputerów z obsługą MTOM; koder MTOM można dekodować i analizowanie przychodzących wiadomości oraz innych MTOM.  
  
 Za pomocą koder MTOM jest zgodny z innymi funkcjami programu WCF. Należy pamiętać, że może nie być możliwe obserwowania tej reguły we wszystkich przypadkach, takich jak podczas sesji pomocy technicznej jest wymagany.  
  
### <a name="programming-model"></a>Model programowania  
 Niezależnie od tego, którego trzy wbudowane koderów, możesz użyć w aplikacji środowiska programowania jest identyczny w odniesieniu do transferowania danych binarnych. Różnica polega na w sposób WCF służy do obsługi danych na podstawie ich typów danych.  
  
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
  
 Korzystając z MTOM, poprzedni kontraktu danych jest serializowana zgodnie z następującymi zasadami:  
  
-   Jeśli `binaryBuffer` nie `null` i indywidualnie zawiera wystarczającej ilości danych, aby uzasadniać obciążenie o eksternalizację MTOM (nagłówków MIME i tak dalej) w porównaniu do formatu Base64 kodowania, dane są zewnętrznych i przenoszone z komunikatem w ramach MIME binarne. Jeśli próg nie zostanie przekroczony, dane są zakodowane jako Base64.  
  
-   Ciąg (i wszystkich innych typów, które nie są binarne) zawsze jest przedstawiana jako ciąg w treści wiadomości, bez względu na rozmiar.  
  
 Wpływ na kodowanie MTOM jest taka sama niezależnie od użycia kontrakt danych jawne, jak pokazano w powyższym przykładzie użyj listę parametrów w operacji, mają kontraktów danych zagnieżdżonych lub przeniesienia obiektu kontraktu danych wewnątrz kolekcji. Tablice typu byte nadają się zawsze do optymalizacji i są zoptymalizowane pod kątem, jeśli spełnione są progi optymalizacji.  
  
> [!NOTE]
>  Nie powinien być używany <xref:System.IO.Stream?displayProperty=nameWithType> pochodne typy wewnątrz kontraktów danych. Stream data powinien być przekazywany przy użyciu modelu przesyłania strumieniowego, szczegółowo opisane w poniższej sekcji "Dane przesyłane strumieniowo".  
  
## <a name="streaming-data"></a>Dane przesyłane strumieniowo  
 W przypadku dużych ilości danych do przesłania strumieniowego tryb transferu programu WCF jest możliwe alternatywa domyślne zachowanie buforowania i przetwarzanie komunikatów w pamięci w całości.  
  
 Jak wspomniano wcześniej, należy włączyć przesyłania strumieniowego tylko w przypadku dużych komunikatów (z zawartością tekstowych lub binarnych), czy dane nie można podzielić, jeśli wiadomość musi zostać dostarczony w odpowiednim czasie, czy dane nie jest jeszcze w pełni dostępna po rozpoczęciu transferu.  
  
### <a name="restrictions"></a>Ograniczenia  
 Szereg istotnych funkcji WCF nie można użyć podczas przesyłania strumieniowego jest włączona:  
  
-   Nie można wykonać podpisów cyfrowych dla treści wiadomości, ponieważ wymagają one, obliczanie skrótu za pośrednictwem zawartość cały komunikat. W przypadku przesyłania strumieniowego zawartość nie jest w pełni dostępne, gdy nagłówki wiadomości są zbudowane i wysyłane i dlatego nie można obliczyć podpisu cyfrowego.  
  
-   Szyfrowanie jest zależna od podpisów cyfrowych, aby sprawdzić, czy dane zostały odtworzone poprawnie.  
  
-   Niezawodne sesje musi buforu wysłanych komunikatów na kliencie ponowne dostarczenie pobiera utracony komunikat w przeniesieniu i muszą przechowywać wiadomości w usłudze przed przekazaniem ich do implementacji usługi, aby zachować kolejność komunikatów, w przypadku, gdy komunikaty są odbierane poza sekwencji.  
  
 Ze względu na te ograniczenia funkcjonalności można użyć tylko transportu zabezpieczeń opcje przesyłania strumieniowego i nie można włączyć w sesjach niezawodnych. Przesyłanie strumieniowe jest dostępna tylko w następujących powiązań zdefiniowanych przez system:  
  
-   <xref:System.ServiceModel.BasicHttpBinding>  
  
-   <xref:System.ServiceModel.NetTcpBinding>  
  
-   <xref:System.ServiceModel.NetNamedPipeBinding>  
  
-   <xref:System.ServiceModel.WebHttpBinding>  
  
 Ponieważ podstawowy transport <xref:System.ServiceModel.NetTcpBinding> i <xref:System.ServiceModel.NetNamedPipeBinding> nieprzerwaną pracę niezawodne dostarczanie i opartego na połączeniach sesji pomocy technicznej, w odróżnieniu od protokołu HTTP, te dwa powiązania tylko minimalny zestaw dotyczy tych warunków ograniczających w praktyce.  
  
 Przesyłanie strumieniowe nie jest dostępna za pomocą transportu usługi kolejkowania komunikatów (MSMQ) i dlatego nie może być używany z <xref:System.ServiceModel.NetMsmqBinding> lub <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> klasy. Transportu MSMQ tylko obsługuje transfery buforowane dane o rozmiarze ograniczone wiadomości, a wszystkie inne transportu nie mają żadnych limit rozmiaru komunikatu praktyczne większość scenariuszy.  
  
 Przesyłanie strumieniowe również nie jest dostępna podczas za pomocą transportu kanał elementu równorzędnego, więc nie jest dostępna z <xref:System.ServiceModel.NetPeerTcpBinding>.  
  
#### <a name="streaming-and-sessions"></a>Przesyłanie strumieniowe i sesji  
 Podczas przesyłania strumieniowego wywołania z powiązaniem oparte na sesji, może wystąpić nieoczekiwane zachowanie. Wszystkie wywołania przesyłania strumieniowego są nawiązywane przy użyciu jednego kanału (kanał datagram), który nie obsługuje sesji, nawet jeśli powiązania, używany jest skonfigurowany do używania sesji. Jeśli wielu klientów wywołań przesyłania strumieniowego do tego samego obiektu usługi za pośrednictwem powiązania oparte na sesji i tryb współbieżności obiekt usługi jest ustawiony na jednym i jego wystąpienie kontekstu tryb ustawiono PerSession, wywołania musi przechodzić przez kanał datagram i dlatego tylko jeden wywołania są przetwarzane w danym momencie. Co najmniej jeden klient może następnie limit czasu. Ten problem można obejść przez ustawienie Tryb kontekstu wystąpienia obiektu usługi PerCall lub współbieżności do wielu.  
  
> [!NOTE]
>  MaxConcurrentSessions nie ma znaczenia w tym przypadku, ponieważ istnieje tylko jeden "sesja".  
  
### <a name="enabling-streaming"></a>Włączanie przesyłania strumieniowego  
 Aby umożliwić przesyłanie strumieniowe w następujący sposób:  
  
-   Wysyłanie i umożliwienia akceptowania żądań aplikacji w trybie przesyłania strumieniowego i zaakceptuj i zwracania odpowiedzi w tryb buforowany (<xref:System.ServiceModel.TransferMode.StreamedRequest>).  
  
-   Wysyłanie i umożliwienia akceptowania żądań aplikacji w tryb buforowany i zaakceptuj i zwracania odpowiedzi w trybie przesyłane strumieniowo (<xref:System.ServiceModel.TransferMode.StreamedResponse>).  
  
-   Wysyłanie i odbieranie żądań i odpowiedzi w trybie przesyłanej strumieniowo w obu kierunkach. (<xref:System.ServiceModel.TransferMode.Streamed>).  
  
 Można wyłączyć, przesyłanie strumieniowe, ustawiając tryb transferu <xref:System.ServiceModel.TransferMode.Buffered>, co jest ustawieniem domyślnym na wszystkie powiązania. Poniższy kod pokazuje, jak ustawić tryb transferu w konfiguracji.  
  
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
  
 Podczas tworzenia wystąpienia usługi powiązania w kodzie, należy ustawić odpowiednie `TransferMode` właściwości powiązania (lub elementu powiązania transportu, jeśli redagowania niestandardowego powiązania) na jedną z wartości wymienionych wcześniej.  
  
 Można włączyć strumieniowe przesyłanie żądań i odpowiedzi lub w obu kierunkach niezależnie po obu stronach strony komunikujące się bez wywierania wpływu na funkcjonalność. Jednak należy zawsze zakładać, że rozmiar przeniesionych danych jest tyle znaczące, że włączenie przesyłania strumieniowego jest uzasadnione dla obu punktów końcowych łącza komunikacyjnego. Do komunikacji dla wielu platform, gdzie jeden z punktów końcowych, które nie jest zaimplementowana przy użyciu usługi WCF możliwość używania przesyłania strumieniowego zależy od możliwości przesyłania strumieniowego platformy. Kolejny wyjątek rzadkich może być oparte na scenariuszu, gdzie klienta lub usługę, należy zminimalizować jej zestawu roboczego i może pozwolić rozmiary małych buforów zużycie pamięci.  
  
### <a name="enabling-asynchronous-streaming"></a>Włączanie asynchronicznego przesyłania strumieniowego  
 Aby włączyć, asynchronicznego przesyłania strumieniowego, Dodaj <xref:System.ServiceModel.Description.DispatcherSynchronizationBehavior> zachowanie punktu końcowego usługi hosta i ustaw jego <xref:System.ServiceModel.Description.DispatcherSynchronizationBehavior.AsynchronousSendEnabled%2A> właściwość `true`. Dodaliśmy również możliwości true asynchronicznego przesyłania strumieniowego po stronie wysyłania. To zwiększa skalowalność usługi w scenariuszach, gdzie jest strumienia komunikatów do wielu klientów, niektóre z nich są powolne podczas odczytu, prawdopodobnie z powodu przeciążenia sieci lub w ogóle nie czytają. W tych scenariuszach możemy teraz nie blokują jednym z wątków w usłudze na klienta. Zapewnia to, że usługa jest w stanie do przetworzenia wiele większej liczby klientów, zwiększając w ten sposób skalowalność usługi.  
  
### <a name="programming-model-for-streamed-transfers"></a>Model programowania transferów przesyłane strumieniowo  
 Model programowania do przesyłania strumieniowego jest bardzo proste. Odbiera dane przesyłane strumieniowo, określ kontrakt operacji, która ma jeden <xref:System.IO.Stream> wpisany parametr wejściowy. W przypadku zwracający dane przesyłane strumieniowo, zwracają <xref:System.IO.Stream> odwołania.  
  
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
  
 Operacja `Echo` w poprzednim przykładzie odbiera i zwraca strumienia i powinna być używana w powiązaniu z <xref:System.ServiceModel.TransferMode.Streamed>. Dla operacji `RequestInfo`, <xref:System.ServiceModel.TransferMode.StreamedResponse> najlepiej nadaje się, ponieważ zwraca ono tylko wartość <xref:System.IO.Stream>. Operacja jednokierunkowa najlepiej nadaje się dla <xref:System.ServiceModel.TransferMode.StreamedRequest>.  
  
 Należy pamiętać, ten drugi parametr dodawanie do następujących `Echo` lub `ProvideInfo` operacje powoduje, że model usług powrócić do buforowanego strategii i używania czasu wykonywania serializacji reprezentacja strumienia. Tylko operacje z parametrem jednym strumień wejściowy są zgodne z żądaniem end-to-end przesyłania strumieniowego.  
  
 Ta zasada dotyczy podobnie kontrakty komunikatów. Jak pokazano na poniższym kontraktu komunikatu, może mieć tylko członek jednej jednostki w swojej kontraktu komunikatu, który jest strumień. Jeśli chcesz przekazać dodatkowe informacje o strumieniu, te informacje muszą być przeprowadzane w nagłówkach wiadomości. Treść komunikatu jest zastrzeżone wyłącznie dla zawartości strumienia.  
  
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
  
 Końcowy transfery przesyłane strumieniowo i komunikat o jest zamknięty, gdy strumień osiągnie koniec pliku (EOF). Podczas wysyłania komunikatu (zwracanie wartości lub wywołanie operacji), możesz przekazać <xref:System.IO.FileStream> i infrastruktura WCF później ściąga wszystkie dane z tej usługi stream, dopóki strumień całkowicie odczytane i osiągnięcia końca pliku. Transfer danych przesyłane strumieniowo dla źródła, nie takie wstępnie skompilowanych <xref:System.IO.Stream> istnieje w klasie pochodnej, konstruowania taka klasa, nakładki tej klasy, za pośrednictwem źródła strumienia i używać go jako argument lub wartości zwracanej.  
  
 Podczas odbierania komunikatu, WCF, tworzy strumień przez treść komunikatu algorytmem Base64 (lub odpowiedniego części MIME, jeśli za pomocą MTOM), a strumień osiągnie EOF, gdy zawartość została przeczytana.  
  
 Również poziomu transportu przesyłania strumieniowego współdziała z żadnych innych typ kontraktu komunikatu (listy parametrów, argumenty kontraktu danych i kontraktu komunikatu jawne), ale ponieważ serializacji i deserializacji takich typ wiadomości, wymagane jest buforowanie przez serializator , przy użyciu takich wariantów umowy nie jest zalecane.  
  
### <a name="special-security-considerations-for-large-data"></a>Zagadnienia dotyczące zabezpieczeń specjalne dla dużych ilości danych  
 Wszystkie powiązania umożliwiają ograniczenie rozmiaru wiadomości przychodzących, aby zapobiec atakom typu "odmowa usługi". <xref:System.ServiceModel.BasicHttpBinding>, Na przykład udostępnia [System.ServiceModel.BasicHttpBinding.MaxReceivedMessageSize](xref:System.ServiceModel.HttpBindingBase.MaxReceivedMessageSize%2A) właściwość, która jest zakresem rozmiaru komunikatu przychodzącego, a więc również granic maksymalną ilość pamięci, która jest dostępna podczas przetwarzania komunikatu. Ta jednostka jest ustawiana w bajtach z wartością domyślną 65 536 bajtów.  
  
 Zagrożenie bezpieczeństwa, które są specyficzne dla scenariusz transmisji strumieniowej w dużych ilości danych wywołuje typu "odmowa usługi", powodując dane buforowane, gdy odbiornika oczekuje przesyłane strumieniowo. Na przykład WCF zawsze buforuje nagłówków protokołu SOAP wiadomości, a więc osoba atakująca może konstruować tak dużych niebezpieczną wiadomość, która zawiera tylko nagłówki, aby wymusić dane, które mają być buforowane. Po włączeniu przesyłania strumieniowego `MaxReceivedMessageSize` może być ustawiona na bardzo dużą wartość, ponieważ odbiornika oczekuje nigdy nie cały komunikat do buforowanych w pamięci na raz. Jeśli WCF jest zmuszony do buforu komunikatu, wystąpi przepełnienie pamięci.  
  
 W związku z tym ograniczanie maksymalny rozmiar wiadomości przychodzącej nie wystarcza w tym przypadku. `MaxBufferSize` Ograniczenie pamięci, który zapewnia buforowanie WCF jest wymagana właściwość. Ważne jest, aby Ustaw tę opcję na wartość bezpiecznych (lub zachować wartość domyślną) podczas przesyłania strumieniowego. Załóżmy, że usługa musi otrzymać bit pliki rozmiarze maksymalnie 4 GB i przechowywać je na dysku lokalnym. Załóżmy również, że pamięć jest ograniczona w taki sposób, można tylko buforu 64 KB danych w danym momencie. Następnie należy ustawić `MaxReceivedMessageSize` do 4 GB i `MaxBufferSize` 64 KB. Ponadto w danej implementacji usługi upewnij się jedynie odczytywać strumień przychodzących we fragmentach o rozmiarze 64 KB, a następnie odczytu nie dalej fragmentów przed poprzedniej została zapisane na dysku i usuwane z pamięci.  
  
 Jest również pamiętać, że ten limit przydziału tylko ogranicza ich buforowanie wykonywane przez architekturę WCF i nie można chronić się przed dowolnego buforowania, możesz zrobić w Twojej własnej implementacji usługi lub klienta. Aby uzyskać więcej informacji dotyczących zabezpieczeń, zobacz [zagadnienia dotyczące zabezpieczeń dla danych](../../../../docs/framework/wcf/feature-details/security-considerations-for-data.md).  
  
> [!NOTE]
>  Decyzja dotycząca użycia buforowanego lub przesyłane strumieniowo transferu jest decyzja lokalnego punktu końcowego. Dla transportu HTTP tryb transferu nie propagować przez połączenie lub serwery proxy i innych pośredników. Ustawianie trybu transferu nie zostaną uwzględnione w opisie interfejsu usługi. Po wygenerowaniu klienta programu WCF do usługi, możesz edytować plik konfiguracji usługi przeznaczone do użycia w przypadku transferów przesyłane strumieniowo można ustawić trybu. Dla protokołu TCP i rodzajów transportu nazwanego potoku tryb transferu jest propagowany jako potwierdzenie zasad.  
  
## <a name="see-also"></a>Zobacz także
- [Instrukcje: Włączanie przesyłania strumieniowego](../../../../docs/framework/wcf/feature-details/how-to-enable-streaming.md)
