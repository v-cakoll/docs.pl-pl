---
title: Duże ilości danych i przesyłanie strumieniowe
ms.date: 03/30/2017
ms.assetid: ab2851f5-966b-4549-80ab-c94c5c0502d2
ms.openlocfilehash: 91e53f66fb0f2f94a315c318eb0b203d78427bae
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184678"
---
# <a name="large-data-and-streaming"></a>Duże ilości danych i przesyłanie strumieniowe

Windows Communication Foundation (WCF) to infrastruktura komunikacyjna oparta na języku XML. Ponieważ dane XML są powszechnie kodowane w standardowym formacie tekstowym zdefiniowanym w [specyfikacji XML 1.0,](https://www.w3.org/TR/REC-xml/)deweloperzy i architekci połączonych systemów są zazwyczaj zaniepokojeni śladem (lub rozmiarem) komunikatów wysyłanych przez sieć, a kodowanie tekstowe XML stanowi szczególne wyzwanie dla wydajnego transferu danych binarnych.  
  
## <a name="basic-considerations"></a>Zagadnienia podstawowe  
 Aby podać podstawowe informacje na temat następujących informacji dla WCF, w tej sekcji przedstawiono pewne ogólne problemy i zagadnienia dotyczące kodowania, danych binarnych i przesyłania strumieniowego, które zazwyczaj mają zastosowanie do infrastruktury połączonych systemów.  
  
### <a name="encoding-data-text-vs-binary"></a>Kodowanie danych: tekst a binarny  
 Powszechnie wyrażane obawy deweloperów obejmują przekonanie, że XML ma znaczne obciążenie w porównaniu do formatów binarnych ze względu na powtarzalny charakter tagów początkowych i końcowych, że kodowanie wartości liczbowych jest uważane za znacznie większe ponieważ są one wyrażone w wartościach tekstowych i że dane binarne nie mogą być wyrażone skutecznie, ponieważ muszą być specjalnie zakodowane do osadzania w formacie tekstowym.  
  
 Chociaż wiele z tych i podobnych problemów jest prawidłowych, rzeczywista różnica między wiadomościami zakodowanymi w tekście XML w środowisku usług sieci Web XML a wiadomościami zakodowanymi w formacie binarnym w środowisku starszego zdalnego wywołania procedury (RPC) jest często znacznie mniej istotna niż wstępnej analizy może sugerować.  
  
 Podczas gdy wiadomości zakodowane w tekście XML są przezroczyste i "czytelne dla człowieka", wiadomości binarne są często dość niejasne w porównaniu i trudne do dekodowania bez narzędzi. Ta różnica w czytelności prowadzi do przeoczenia, że wiadomości binarne często zawierają wbudowane metadane w ładunku, co zwiększa obciążenie, podobnie jak w przypadku wiadomości tekstowych XML. Jest to szczególnie prawdziwe dla formatów binarnych, które mają na celu zapewnienie możliwości luźnego sprzężenia i wywołania dynamicznego.  
  
 Jednak formaty binarne często zawierają takie opisowe informacje o metadanych w "nagłówku", który również deklaruje układ danych dla następujących rekordów danych. Ładunek następnie następuje tej deklaracji bloku metadanych wspólne przy minimalnym dalsze obciążenie. Z drugiej strony XML zawiera każdy element danych w elemencie lub atrybucie, dzięki czemu otaczające metadane są powtarzalnie uwzględniane dla każdego szeregowanego obiektu ładunku. W rezultacie rozmiar pojedynczego seryjnego obiektu ładunku jest podobny podczas porównywania tekstu z reprezentacjami binarnymi, ponieważ niektóre metadane opisowe muszą być wyrażone dla obu, ale format binarny korzysta z udostępnionego opisu metadanych z każdym dodatkowym obiekt ładunku, który jest przesyłany z powodu niższego ogólnego narzutu.  
  
 Mimo to dla niektórych typów danych, takich jak liczby, może być wadą przy użyciu stałego rozmiaru, binarne reprezentacje liczbowe, takie jak 128-bitowy typ dziesiętny zamiast zwykłego tekstu, jak zwykły tekst reprezentacji może być kilka bajtów mniejszych. Dane tekstowe mogą również mieć korzyści z rozmiaru z zazwyczaj bardziej elastycznych opcji kodowania tekstu XML, podczas gdy niektóre formaty binarne mogą domyślnie 16-bitowe lub nawet 32-bitowe Unicode, które nie ma zastosowania do formatu .NET Binary XML.  
  
 W rezultacie podejmowanie decyzji między tekstem lub binarnym nie jest tak proste, jak przy założeniu, że wiadomości binarne są zawsze mniejsze niż wiadomości tekstowe XML.  
  
 Wyraźną zaletą wiadomości tekstowych XML jest to, że są one oparte na standardach i oferują najszerszy wybór opcji interoperacyjności i obsługi platformy. Aby uzyskać więcej informacji, zobacz sekcję "Kodowanie" w dalszej części tego tematu.  
  
### <a name="binary-content"></a>Zawartość binarna  
 Jednym z obszarów, w którym kodowanie binarne jest lepsze od kodowania tekstowego pod względem rozmiaru wiadomości, są duże elementy danych binarnych, takie jak obrazy, filmy, klipy dźwiękowe lub jakakolwiek inna forma nieprzezroczystych, binarnych danych, które muszą być wymieniane między usługami i ich Konsumentów. Aby dopasować te typy danych do tekstu XML, typowym podejściem jest zakodowanie ich przy użyciu kodowania Base64.  
  
 W ciągu zakodowanym w zasadach Base64 każdy znak reprezentuje 6 bitów oryginalnych danych 8-bitowych, co powoduje stosunek kodowania 4:3 dla Base64, nie licząc dodatkowych znaków formatowania (powrotu karetki/kanału informacyjnego wiersza), które są powszechnie dodawane przez konwencję. Podczas gdy znaczenie różnic między kodowaniem XML i binarnych zazwyczaj zależy od scenariusza, przyrost rozmiaru o więcej niż 33% podczas przesyłania ładunku 500 MB jest zwykle nie do przyjęcia.  
  
 Aby uniknąć tego obciążenia kodowania, standard Mechanizm optymalizacji transmisji wiadomości (MTOM) umożliwia eksternalizację dużych elementów danych, które są zawarte w wiadomości i przenoszenie ich z wiadomością jako dane binarne bez specjalnego kodowania. Z MTOM wiadomości są wymieniane w podobny sposób do wiadomości e-mail Simple Mail Transfer Protocol (SMTP) z załącznikami lub zawartością osadzoną (zdjęcia i inne osadzone treści); Komunikaty MTOM są pakowane jako wieloczęściowe/powiązane sekwencje MIME, a część główna jest rzeczywistym komunikatem SOAP.  
  
 Komunikat MTOM SOAP jest modyfikowany z jego wersji niekodowanej, tak aby specjalne znaczniki elementów, które odwołują się do odpowiednich części MIME, umieszczały oryginalne elementy w komunikacie zawierającym dane binarne. W rezultacie komunikat SOAP odnosi się do zawartości binarnej, wskazując części MIME wysłane z nim, ale w przeciwnym razie po prostu przenosi dane tekstowe XML. Ponieważ ten model jest ściśle zgodny z ugruntowanym modelem SMTP, istnieje szeroka obsługa narzędzi do kodowania i dekodowania komunikatów MTOM na wielu platformach, co czyni go niezwykle interoperacyjnym wyborem.  
  
 Mimo to, podobnie jak w przypadku Base64, MTOM jest również wyposażony w pewne niezbędne obciążenie dla formatu MIME, dzięki czemu zalety korzystania z MTOM są widoczne tylko wtedy, gdy rozmiar elementu danych binarnych przekracza około 1 KB. Ze względu na obciążenie, wiadomości zakodowane w MTOM mogą być większe niż komunikaty, które używają kodowania Base64 dla danych binarnych, jeśli ładunek binarny pozostaje poniżej tego progu. Aby uzyskać więcej informacji, zobacz sekcję "Kodowanie" w dalszej części tego tematu.  
  
### <a name="large-data-content"></a>Duża zawartość danych  
 Wire-footprint na bok, wcześniej wspomniano 500-MB ładowność również stanowi wielkie lokalne wyzwanie dla usługi i klienta. Domyślnie WCF przetwarza wiadomości w *trybie buforowanym*. Oznacza to, że cała zawartość wiadomości jest obecna w pamięci przed wysłaniem lub po jej odebraniu. Chociaż jest to dobra strategia dla większości scenariuszy i niezbędna dla funkcji obsługi wiadomości, takich jak podpisy cyfrowe i niezawodne dostarczanie, duże komunikaty mogą wyczerpać zasoby systemu.  
  
 Strategia radzenia sobie z dużymi ładunkami jest streaming. Podczas gdy wiadomości, zwłaszcza te wyrażone w języku XML, są powszechnie uważane za stosunkowo kompaktowe pakiety danych, wiadomość może mieć rozmiar wielu gigabajtów i przypominać ciągły strumień danych bardziej niż pakiet danych. Gdy dane są przesyłane w trybie przesyłania strumieniowego zamiast w trybie buforowanym, nadawca udostępnia adresatowi zawartość treści wiadomości w postaci strumienia, a infrastruktura wiadomości stale przesyła dane z nadawcy do odbiorcy, gdy się pojawią. Dostępne.  
  
 Najczęstszym scenariuszem, w którym takie transfery zawartości dużych danych występują są transfery obiektów danych binarnych, które:  
  
- Nie można łatwo podzielić na sekwencję wiadomości.  
  
- Musi być dostarczony w odpowiednim czasie.  
  
- Nie są dostępne w całości po zainicjowaniu transferu.  
  
 W przypadku danych, które nie mają tych ograniczeń, zazwyczaj lepiej jest wysyłać sekwencje wiadomości w zakresie sesji niż jeden duży komunikat. Aby uzyskać więcej informacji, zobacz sekcję "Dane przesyłania strumieniowego" w dalszej części tego tematu.  
  
 Podczas wysyłania dużych ilości danych należy `maxAllowedContentLength` ustawić ustawienie usług IIS (aby uzyskać więcej informacji, `maxReceivedMessageSize` zobacz [Konfigurowanie limitów żądań usług IIS)](https://docs.microsoft.com/iis/configuration/system.webServer/security/requestFiltering/requestLimits/)i ustawienie powiązania (na przykład <xref:System.ServiceModel.NetTcpBinding.MaxReceivedMessageSize%2A> [System.ServiceModel.BasicHttpBinding.MaxReceivedMessageSize](xref:System.ServiceModel.HttpBindingBase.MaxReceivedMessageSize%2A) lub ). Właściwość domyślnie `maxAllowedContentLength` 28.6 MB `maxReceivedMessageSize` i właściwość domyślnie 64KB.  
  
## <a name="encodings"></a>Kodowanie  
 *Kodowanie* definiuje zestaw reguł dotyczących sposobu prezentowania wiadomości w sieci. *Koder* implementuje takie kodowanie i jest odpowiedzialny, po stronie nadawcy, <xref:System.ServiceModel.Channels.Message> za przekształcenie w pamięci w strumień bajtów lub bufor bajtów, które mogą być wysyłane przez sieć. Po stronie odbiornika koder zamienia sekwencję bajtów w komunikat w pamięci.  
  
 WCF zawiera trzy kodery i pozwala na pisanie i podłączanie własnych koderów, jeśli to konieczne.  
  
 Każde z powiązań standardowych zawiera wstępnie skonfigurowany koder, przy czym powiązania z prefiksem Net* używają <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement> kodera <xref:System.ServiceModel.BasicHttpBinding> binarnego (przez włączenie klasy), podczas gdy klasy i <xref:System.ServiceModel.WSHttpBinding> używają kodera wiadomości tekstowych (za pomocą <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement> klasy) domyślnie.  
  
|Element wiązania kodera|Opis|  
|-----------------------------|-----------------|  
|<xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>|Koder wiadomości tekstowych jest domyślnym koderem dla wszystkich powiązań opartych na protoko> HTTP i odpowiednim wyborem dla wszystkich niestandardowych powiązań, w których współdziałanie jest największym problemem. Ten koder odczytuje i zapisuje standardowe wiadomości tekstowe SOAP 1.1/SOAP 1.2 bez specjalnej obsługi danych binarnych. Jeśli <xref:System.ServiceModel.Channels.MessageVersion?displayProperty=nameWithType> właściwość wiadomości jest <xref:System.ServiceModel.Channels.MessageVersion.None?displayProperty=nameWithType>ustawiona na , otoka koperty SOAP jest pomijana z danych wyjściowych i tylko zawartość treści wiadomości jest serializowana.|  
|<xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement>|Koder komunikatów MTOM jest koderem tekstu, który implementuje specjalną obsługę danych binarnych i nie jest domyślnie używany w żadnym ze standardowych powiązań, ponieważ jest to narzędzie do optymalizacji dla każdego przypadku. Jeśli komunikat zawiera dane binarne, który przekracza próg, w którym kodowanie MTOM daje korzyści, dane są zewnętrznie do części MIME po obwiedni wiadomości. Zobacz Włączanie MTOM w dalszej części tej sekcji.|  
|<xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>|Koder wiadomości binarnych jest domyślnym koderem dla powiązań Net* i odpowiednim wyborem, gdy obie strony komunikacji są oparte na WCF. Koder wiadomości binarnych używa formatu .NET Binary XML Format, specyficznego dla firmy Microsoft reprezentacji binarnej dla zestawów informacji XML (Zestawy informacji), która zazwyczaj daje mniejszy ślad niż odpowiednik reprezentacji XML 1.0 i koduje dane binarne jako bajt Strumienia.|  
  
 Kodowanie wiadomości tekstowych jest zazwyczaj najlepszym wyborem dla każdej ścieżki komunikacji, która wymaga współdziałania, podczas gdy kodowanie wiadomości binarnych jest najlepszym wyborem dla każdej innej ścieżki komunikacji. Kodowanie wiadomości binarnych zazwyczaj daje mniejsze rozmiary wiadomości w porównaniu do tekstu dla pojedynczej wiadomości i stopniowo nawet mniejsze rozmiary wiadomości w czasie trwania sesji komunikacyjnej. W przeciwieństwie do kodowania tekstu kodowanie binarne nie musi używać specjalnej obsługi danych binarnych, takich jak base64, ale reprezentuje bajty jako bajty.  
  
 Jeśli rozwiązanie nie wymaga współdziałania, ale nadal chcesz używać transportu HTTP, <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement> można skomponować <xref:System.ServiceModel.Channels.HttpTransportBindingElement> do niestandardowego powiązania, które używa klasy do transportu. Jeśli liczba klientów w usłudze wymaga współdziałania, zaleca się uwidacznianie równoległych punktów końcowych, z których każdy ma odpowiednie opcje transportu i kodowania dla odpowiednich klientów włączone.  
  
### <a name="enabling-mtom"></a>Włączanie mtom  
 Gdy interoperacyjność jest wymaganiem i muszą być wysyłane duże dane binarne, kodowanie wiadomości MTOM <xref:System.ServiceModel.WSHttpBinding> jest alternatywną `MessageEncoding` strategią <xref:System.ServiceModel.WSMessageEncoding.Mtom> kodowania, którą <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement> można <xref:System.ServiceModel.Channels.CustomBinding>włączyć w standardzie <xref:System.ServiceModel.BasicHttpBinding> lub powiązaniach, ustawiając odpowiednią właściwość na lub przez redagowanie do . Poniższy przykładowy kod wyodrębniony z przykładowego [kodowania MTOM](../../../../docs/framework/wcf/samples/mtom-encoding.md) pokazuje, jak włączyć MTOM w konfiguracji.  
  
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
  
 Jak wspomniano wcześniej, decyzja o użyciu kodowania MTOM zależy od wysyłanego woluminu danych. Ponadto ponieważ MTOM jest włączona na poziomie powiązania, włączenie MTOM wpływa na wszystkie operacje w danym punkcie końcowym.  
  
 Ponieważ koder MTOM zawsze emituje komunikat MIME/wieloczęściowy zakodowany w formacie MTOM, niezależnie od tego, czy dane binarne kończą się zewnętrznie, zazwyczaj należy włączyć mtom tylko dla punktów końcowych, które wymieniają wiadomości z więcej niż 1 KB danych binarnych. Ponadto umowy serwisowe przeznaczone do użytku z punktami końcowymi obsługującymi protokół MTOM powinny, w miarę możliwości, być ograniczone do określania takich operacji transferu danych. Funkcja kontroli pokrewne powinny znajdować się na oddzielnym kontrakcie. Ta reguła "tylko MTOM" ma zastosowanie tylko do wiadomości wysyłanych za pośrednictwem punktu końcowego obsługującego protokół MTOM; Koder MTOM może dekodować i analizować przychodzące komunikaty inne niż MTOM.  
  
 Korzystanie z kodera MTOM jest zgodne ze wszystkimi innymi funkcjami WCF. Należy zauważyć, że może nie być możliwe przestrzeganie tej reguły we wszystkich przypadkach, takich jak gdy wymagana jest obsługa sesji.  
  
### <a name="programming-model"></a>Model programowania  
 Niezależnie od tego, które z trzech wbudowanych koderów, których używasz w aplikacji, środowisko programowania jest identyczne w odniesieniu do przesyłania danych binarnych. Różnica polega na tym, jak WCF obsługuje dane na podstawie ich typów danych.  
  
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
  
 W przypadku korzystania z programu MTOM poprzedni kontrakt danych jest serializowany zgodnie z następującymi regułami:  
  
- Jeśli `binaryBuffer` nie `null` jest i indywidualnie zawiera wystarczającą ilość danych, aby uzasadnić obciążenie eksternalizacji MTOM (nagłówki MIME i tak dalej) w porównaniu do kodowania Base64, dane są eksternalizowane i przenoszone z wiadomością jako binarną część MIME. Jeśli próg nie zostanie przekroczony, dane są kodowane jako Base64.  
  
- Ciąg (i wszystkie inne typy, które nie są binarne) jest zawsze reprezentowana jako ciąg wewnątrz treści wiadomości, niezależnie od rozmiaru.  
  
 Wpływ na kodowanie MTOM jest taki sam, czy używasz jawnego kontraktu danych, jak pokazano w poprzednim przykładzie, użyj listy parametrów w operacji, mają zagnieżdżone kontrakty danych lub przenieś obiekt kontraktu danych wewnątrz kolekcji. Tablice bajtów są zawsze kandydatami do optymalizacji i są optymalizowane, jeśli progi optymalizacji są spełnione.  
  
> [!NOTE]
> Nie należy używać <xref:System.IO.Stream?displayProperty=nameWithType> typów pochodnych wewnątrz kontraktów danych. Dane strumienia powinny być przekazywane przy użyciu modelu przesyłania strumieniowego, wyjaśniono w poniższej sekcji "Dane przesyłania strumieniowego".  
  
## <a name="streaming-data"></a>Przesyłanie strumieniowe danych  
 Gdy masz dużą ilość danych do transferu, tryb przesyłania strumieniowego w WCF jest wykonalną alternatywą dla domyślnego zachowania buforowania i przetwarzania wiadomości w pamięci w całości.  
  
 Jak wspomniano wcześniej, włącz przesyłanie strumieniowe tylko dla dużych wiadomości (z tekstem lub zawartością binarną), jeśli dane nie mogą być segmentowane, jeśli wiadomość musi być dostarczona w odpowiednim czasie lub jeśli dane nie są jeszcze w pełni dostępne po zainicjowaniu transferu.  
  
### <a name="restrictions"></a>Ograniczenia  
 Nie można używać znacznej liczby funkcji WCF, gdy przesyłanie strumieniowe jest włączone:  
  
- Nie można wykonać podpisów cyfrowych dla treści wiadomości, ponieważ wymagają one obliczenia skrótu dla całej zawartości wiadomości. W przypadku przesyłania strumieniowego zawartość nie jest w pełni dostępna, gdy nagłówki wiadomości są konstruowane i wysyłane i w związku z tym nie można obliczyć podpisu cyfrowego.  
  
- Szyfrowanie zależy od podpisów cyfrowych, aby sprawdzić, czy dane zostały poprawnie zrekonstruowane.  
  
- Niezawodne sesje muszą buforować wysłane wiadomości na kliencie w celu ponownego dostarczenia, jeśli wiadomość zostanie utracona podczas transferu i musi zawierać wiadomości w usłudze przed przekazaniem ich do implementacji usługi, aby zachować kolejność wiadomości w przypadku odebrania wiadomości poza kolejnością.  
  
 Ze względu na te ograniczenia funkcjonalne można używać tylko opcji zabezpieczeń na poziomie transportu do przesyłania strumieniowego i nie można włączyć niezawodnych sesji. Przesyłanie strumieniowe jest dostępne tylko z następującymi powiązaniami zdefiniowanymi przez system:  
  
- <xref:System.ServiceModel.BasicHttpBinding>  
  
- <xref:System.ServiceModel.NetTcpBinding>  
  
- <xref:System.ServiceModel.NetNamedPipeBinding>  
  
- <xref:System.ServiceModel.WebHttpBinding>  
  
 Ponieważ podstawowe transporty <xref:System.ServiceModel.NetTcpBinding> <xref:System.ServiceModel.NetNamedPipeBinding> i mają nieodłączne niezawodne dostarczanie i obsługi sesji oparte na połączeniu, w przeciwieństwie do PROTOKOŁU HTTP, te dwa powiązania są tylko minimalnie wpływa na te ograniczenia, w praktyce.  
  
 Przesyłanie strumieniowe nie jest dostępne z transportem usługi kolejkowania <xref:System.ServiceModel.NetMsmqBinding> wiadomości <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> (MSMQ) i dlatego nie można ich używać z klasą lub klasą. Transport Usługi kolejkowania wiadomości obsługuje tylko buforowane transfery danych o ograniczonym rozmiarze wiadomości, podczas gdy wszystkie inne transporty nie mają żadnego praktycznego limitu rozmiaru wiadomości dla większości scenariuszy.  
  
 Przesyłanie strumieniowe jest również niedostępne podczas korzystania z <xref:System.ServiceModel.NetPeerTcpBinding>transportu kanału równorzędnego, więc nie jest dostępne z .  
  
#### <a name="streaming-and-sessions"></a>Przesyłanie strumieniowe i sesje  
 Może wystąpić nieoczekiwane zachowanie podczas przesyłania strumieniowego wywołań z powiązaniem opartym na sesji. Wszystkie wywołania przesyłania strumieniowego są dokonywane za pośrednictwem jednego kanału (kanału datagram), który nie obsługuje sesji, nawet jeśli używane powiązanie jest skonfigurowane do używania sesji. Jeśli wielu klientów wywołuje przesyłanie strumieniowe do tego samego obiektu usługi za pośrednictwem powiązania opartego na sesji, a tryb współbieżności obiektu usługi jest ustawiony na pojedynczy, a jego tryb kontekstowy wystąpienia jest ustawiony na PerSession, wszystkie wywołania muszą przejść przez kanał datagramu, a więc tylko jeden połączenie jest przetwarzane w czasie. Jeden lub więcej klientów może następnie limit czasu. Można obejść ten problem, ustawiając tryb kontekstowy wystąpienia obiektu usługi na PerCall lub Współbieżność na wiele.  
  
> [!NOTE]
> MaxConcurrentSessions nie ma wpływu w tym przypadku, ponieważ istnieje tylko jedna "sesja" dostępne.  
  
### <a name="enabling-streaming"></a>Włączanie przesyłania strumieniowego  
 Przesyłanie strumieniowe można włączyć w następujący sposób:  
  
- Wysyłaj i akceptuj żądania w trybie przesyłania strumieniowego<xref:System.ServiceModel.TransferMode.StreamedRequest>oraz akceptuj i zwracaj odpowiedzi w trybie buforowanym ( ).  
  
- Wysyłanie i akceptowanie żądań w trybie buforowanym oraz<xref:System.ServiceModel.TransferMode.StreamedResponse>akceptowanie i zwracanie odpowiedzi w trybie strumieniowym ( ).  
  
- Wysyłaj i odbieraj żądania i odpowiedzi w trybie przesyłania strumieniowego w obu kierunkach. (<xref:System.ServiceModel.TransferMode.Streamed>).  
  
 Można wyłączyć przesyłanie strumieniowe, <xref:System.ServiceModel.TransferMode.Buffered>ustawiając tryb transferu na , który jest ustawieniem domyślnym dla wszystkich powiązań. Poniższy kod pokazuje, jak ustawić tryb transferu w konfiguracji.  
  
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
  
 Podczas tworzenia wystąpienia powiązania w kodzie, należy `TransferMode` ustawić odpowiednią właściwość powiązania (lub elementu wiązania transportu, jeśli są redagowanie powiązania niestandardowego) do jednej z wcześniej wymienionych wartości.  
  
 Można włączyć przesyłanie strumieniowe dla żądań i odpowiedzi lub dla obu kierunków niezależnie po obu stronach strony komunikujących się bez wpływu na funkcjonalność. Należy jednak zawsze zakładać, że rozmiar przesyłanych danych jest tak istotny, że włączanie przesyłania strumieniowego jest uzasadnione dla obu punktów końcowych łącza komunikacyjnego. W przypadku komunikacji między platformami, w której jeden z punktów końcowych nie jest implementowany za pomocą WCF, możliwość korzystania z przesyłania strumieniowego zależy od możliwości przesyłania strumieniowego platformy. Innym rzadkim wyjątkiem może być scenariusz oparty na zużyciu pamięci, w którym klient lub usługa musi zminimalizować jego zestaw roboczy i może pozwolić sobie tylko na małe rozmiary buforu.  
  
### <a name="enabling-asynchronous-streaming"></a>Włączanie przesyłania strumieniowego asynchronii  
 Aby włączyć przesyłanie strumieniowe asynchroniczne, dodaj zachowanie punktu końcowego <xref:System.ServiceModel.Description.DispatcherSynchronizationBehavior> do hosta usługi i ustaw jego <xref:System.ServiceModel.Description.DispatcherSynchronizationBehavior.AsynchronousSendEnabled%2A> właściwość na `true`. Dodaliśmy również możliwość prawdziwego asynchronicznego przesyłania strumieniowego po stronie wysyłania. Zwiększa to skalowalność usługi w scenariuszach, w których jest przesyłania strumieniowego wiadomości do wielu klientów, z których niektóre są powolne w czytaniu prawdopodobnie z powodu przeciążenia sieci lub nie są odczytywanie w ogóle. W tych scenariuszach nie blokujemy teraz poszczególnych wątków w usłudze na klienta. Dzięki temu usługa jest w stanie przetworzyć o wiele więcej klientów, poprawiając w ten sposób skalowalność usługi.  
  
### <a name="programming-model-for-streamed-transfers"></a>Model programowania dla transferów przesyłanych strumieniowo  
 Model programowania do przesyłania strumieniowego jest prosty. W przypadku odbierania przesyłanych strumieniowo danych <xref:System.IO.Stream> należy określić kontrakt operacyjny, który ma jeden typowany parametr wejściowy. W przypadku zwracania przesyłanych <xref:System.IO.Stream> strumieniowo danych należy zwrócić odwołanie.  
  
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
  
 Operacja `Echo` w poprzednim przykładzie odbiera i zwraca strumień i dlatego powinny <xref:System.ServiceModel.TransferMode.Streamed>być używane na powiązanie z . Dla operacji `RequestInfo` <xref:System.ServiceModel.TransferMode.StreamedResponse> najlepiej nadaje się, ponieważ zwraca <xref:System.IO.Stream>tylko . Operacja jednokierunkowa jest najlepiej <xref:System.ServiceModel.TransferMode.StreamedRequest>dopasowana do .  
  
 Należy zauważyć, że dodanie `Echo` drugiego `ProvideInfo` parametru do następujących lub operacji powoduje, że model usługi, aby powrócić do strategii buforowane i użyć reprezentacji serializacji w czasie wykonywania strumienia. Tylko operacje z jednym parametrem strumienia wejściowego są zgodne z przesyłania strumieniowego żądania end-to-end.  
  
 Ta reguła ma zastosowanie podobnie do kontraktów wiadomości. Jak pokazano w następującej umowy wiadomości, można mieć tylko jeden element członkowski w umowie wiadomości, który jest strumień. Jeśli chcesz przekazać dodatkowe informacje ze strumieniem, te informacje muszą być przenoszone w nagłówkach wiadomości. Treść wiadomości jest zarezerwowana wyłącznie dla zawartości strumienia.  
  
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
  
 Transfery przesyłane strumieniowo kończą się, a wiadomość jest zamykana, gdy strumień osiągnie koniec pliku (EOF). Podczas wysyłania wiadomości (zwracanie wartości lub wywoływanie operacji), można przekazać <xref:System.IO.FileStream> i WCF infrastruktury następnie pobiera wszystkie dane z tego strumienia, aż strumień został całkowicie odczytany i osiągnął EOF. Aby przenieść przesyłane strumieniowo dane dla <xref:System.IO.Stream> źródła, że nie istnieje taka wstępnie zbudowana klasa pochodna, skonstruuj taką klasę, nakładaj tę klasę za pomocą źródła strumienia i użyj jej jako argumentu lub wartości zwracanej.  
  
 Podczas odbierania wiadomości WCF tworzy strumień za pośrednictwem zawartości treści wiadomości zakodowanej w systemie Base64 (lub odpowiedniej części MIME, jeśli używa mtom) i strumień osiągnie EOF po odczytaniu zawartości.  
  
 Przesyłanie strumieniowe na poziomie transportu działa również z dowolnym innym typem kontraktu wiadomości (listy parametrów, argumenty kontraktu danych i jawny kontrakt wiadomości), ale ponieważ serializacji i deserializacji takich wpisanych wiadomości wymaga buforowania przez serializatora , stosowanie takich wariantów umowy nie jest wskazane.  
  
### <a name="special-security-considerations-for-large-data"></a>Specjalne zagadnienia dotyczące zabezpieczeń dla dużych danych  
 Wszystkie powiązania umożliwiają ograniczenie rozmiaru wiadomości przychodzących, aby zapobiec atakom typu "odmowa usługi". Na <xref:System.ServiceModel.BasicHttpBinding>przykład udostępnia [System.ServiceModel.BasicHttpBinding.MaxReceivedMessageSize](xref:System.ServiceModel.HttpBindingBase.MaxReceivedMessageSize%2A) właściwość, która ogranicza rozmiar wiadomości przychodzącej, a więc również ogranicza maksymalną ilość pamięci, która jest dostępna podczas przetwarzania wiadomości. Ta jednostka jest ustawiona w bajtach o domyślnej wartości 65 536 bajtów.  
  
 Zagrożenie bezpieczeństwa, które jest specyficzne dla scenariusza przesyłania strumieniowego dużych danych powoduje atak typu "odmowa usługi", powodując buforowanie danych, gdy odbiorca oczekuje, że mają być przesyłane strumieniowo. Na przykład WCF zawsze buforuje nagłówki SOAP wiadomości, a więc osoba atakująca może skonstruować dużą złośliwą wiadomość, która składa się w całości z nagłówków, aby wymusić buforowanie danych. Gdy przesyłanie strumieniowe `MaxReceivedMessageSize` jest włączone, może być ustawiona na bardzo dużą wartość, ponieważ odbiorca nigdy nie oczekuje, że cała wiadomość ma być buforowana w pamięci naraz. Jeśli WCF jest zmuszony do buforowania wiadomości, występuje przepełnienie pamięci.  
  
 W związku z tym ograniczenie maksymalnego rozmiaru wiadomości przychodzącej nie wystarczy w tym przypadku. Właściwość `MaxBufferSize` jest wymagana do ograniczenia pamięci, która buforuje WCF. Ważne jest, aby ustawić to na bezpieczną wartość (lub zachować ją na wartości domyślnej) podczas przesyłania strumieniowego. Załóżmy na przykład, że usługa musi odbierać pliki o rozmiarze do 4 GB i przechowywać je na dysku lokalnym. Załóżmy również, że pamięć jest ograniczona w taki sposób, że można buforować tylko 64 KB danych w danym momencie. Następnie można ustawić `MaxReceivedMessageSize` na 4 `MaxBufferSize` GB i 64 KB. Ponadto w implementacji usługi należy upewnić się, że odczytywanie tylko ze strumienia przychodzącego we fragmentach 64 KB i nie odczytuje następnego fragmentu, zanim poprzedni został zapisany na dysku i odrzucony z pamięci.  
  
 Jest również ważne, aby zrozumieć, że ten przydział ogranicza tylko buforowanie wykonywane przez WCF i nie można chronić przed buforowanie, które można zrobić w implementacji własnej usługi lub klienta. Aby uzyskać więcej informacji na temat dodatkowych zagadnień dotyczących zabezpieczeń, zobacz [Zagadnienia dotyczące zabezpieczeń dotyczące danych](../../../../docs/framework/wcf/feature-details/security-considerations-for-data.md).  
  
> [!NOTE]
> Decyzja o użyciu buforowanych lub przesyłanych strumieniowo transferów jest decyzją lokalną punktu końcowego. W przypadku transportów HTTP tryb transferu nie jest propagowane przez połączenie lub serwery proxy i innych pośredników. Ustawienie trybu transferu nie jest odzwierciedlone w opisie interfejsu usługi. Po wygenerowaniu klienta WCF do usługi, należy edytować plik konfiguracji dla usług przeznaczonych do użycia z transferów strumieniowych, aby ustawić tryb. W przypadku transportu TCP i nazwanego potoku tryb transferu jest propagowany jako asercja zasad.  
  
## <a name="see-also"></a>Zobacz też

- [Instrukcje: włączanie przesyłania strumieniowego](../../../../docs/framework/wcf/feature-details/how-to-enable-streaming.md)
