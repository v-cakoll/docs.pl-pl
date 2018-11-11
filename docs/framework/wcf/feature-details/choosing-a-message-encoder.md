---
title: Wybieranie kodera komunikatów
ms.date: 03/30/2017
ms.assetid: 2204d82d-d962-4922-a79e-c9a231604f19
ms.openlocfilehash: 061869704674206739d81be24e105fc87ce0f129
ms.sourcegitcommit: b5cd9d5d3b75a5537fc9ad8a3f085f0bb1845ee0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/07/2018
ms.locfileid: "44248933"
---
# <a name="choosing-a-message-encoder"></a>Wybieranie kodera komunikatów
W tym temacie omówiono kryteria wybierania koderów wiadomości, które znajdują się w Windows Communication Foundation (WCF): plik binarny, tekst i komunikat transmisji optymalizacji mechanizm (MTOM).  
  
 W programie WCF, możesz określić sposób transferu danych za pośrednictwem sieci między punktami końcowymi przez *powiązania*, która składa się z sekwencji *elementów wiązania*. Koder komunikatów jest reprezentowany przez element powiązania w stosie powiązania kodowania komunikatu. Powiązanie zawiera elementy powiązania protokołu opcjonalne, przykład elementu powiązania zabezpieczeń lub niezawodnej obsługi komunikatów elementu powiązania, wiadomość wymagane kodowanie elementu powiązania, a element powiązania transportu wymagane.  
  
 Element powiązania z kodowania komunikatu znajduje się poniżej elementy powiązania protokołu opcjonalne i powyżej elementu powiązania transportu wymagane. Po stronie wychodzących kodera komunikatów serializuje wychodzącej <xref:System.ServiceModel.Channels.Message> i przekazuje je do transportu. Po stronie przychodzących kodera komunikatów odbiera serializowane postaci <xref:System.ServiceModel.Channels.Message> z transportu i przekazuje go do protokół wyższej warstwy, jeśli jest obecny, lub do aplikacji, w przeciwnym razie.  
  
 Podczas łączenia z istniejącego klienta lub serwera, możesz nie mieć wyboru — informacje przy użyciu kodowania określoną wiadomość, ponieważ należy do zakodowania wiadomości w taki sposób, że oczekiwana druga strona. Jednak jeśli piszesz usługi WCF można ujawnić usługi za pomocą wielu punktów końcowych, każdy przy użyciu kodowania inny komunikat. Dzięki temu klienci wybrać optymalne kodowanie dla komunikować się z usługą za pośrednictwem punktu końcowego, który sprawdza się najlepiej w ich, zapewniając klientom swobodę wybierz metodę kodowania, która sprawdza się najlepiej w nich. Za pomocą wielu punktów końcowych również pozwala połączyć zalety kodowania inny komunikat z innymi elementami powiązania.  
  
## <a name="system-provided-encoders"></a>Kodery dostarczane przez system  
 Usługi WCF zawiera trzy koderów wiadomości, które są reprezentowane przez następujące trzy klasy:  
  
-   <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>, tekst koder komunikatów, obsługuje zarówno zwykłe Kodowanie XML i kodowaniem SOAP. Zwykły tryb kodowania XML koder komunikatu tekstowego nosi nazwę "zwykłe stare XML" (POX), w odróżnieniu od kodowania SOAP opartego na tekst. Aby włączyć POX, ustaw <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement.MessageVersion%2A> właściwość <xref:System.ServiceModel.Channels.MessageVersion.None%2A>. Użyj koder komunikatów tekstu pod kątem współdziałania z punktami końcowymi WCF nie.  
  
-   <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>, koder komunikatu binarnego używa compact format binarny jest zoptymalizowany pod kątem usługi WCF do komunikacji WCF i dlatego nie jest międzyoperacyjnych. Dotyczy to również większość kodera wydajne wszystkich koderów udostępnia usługi WCF.  
  
-   <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement>, element powiązania określa znak kodowanie i wersjonowanie wiadomości dla wiadomości przy użyciu kodowanie MTOM. MTOM to technologia wydajne przekazywania danych binarnych w wiadomościach WCF. Koder MTOM podejmuje próbę utworzenia równowagi między współdziałania i wydajność. Kodowanie MTOM przesyła większość kodu XML w postaci tekstowej, ale optymalizuje dużych bloków danych binarnych, przekazywania ich jako — jest bez konwersji na tekst. Pod względem wydajności między koderów, który udostępnia usługi WCF MTOM jest wewnętrzne tekstu (najwolniejsze) i plik binarny (najszybciej).  
  
## <a name="how-to-choose-a-message-encoder"></a>Wybieranie kodera komunikatów  
 W poniższej tabeli opisano typowe czynniki, które umożliwiają wybieranie kodera komunikatów. Ustaw priorytet czynników, które są ważne w przypadku aplikacji, a następnie najlepiej wybierz koderów komunikat współpracujące z tych czynników. Należy wziąć pod uwagę czynników dodatkowe niewymienionych w tej tabeli oraz wszelkie koderów niestandardowy komunikat, które mogą być wymagane w aplikacji.  
  
|współczynnik|Opis|Kodery, które obsługują ten współczynnik|  
|------------|-----------------|---------------------------------------|  
|Obsługiwanych zestawów znaków|<xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement> i <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement> obsługuje tylko UTF8 i UTF16 Unicode (*big-endian* i *little-endian*) kodowania. Jeśli inne kodowanie są wymagane, na przykład UTF7 lub ASCII, należy użyć niestandardowego kodera. Aby uzyskać przykład niestandardowego kodera, zobacz [niestandardowy koder komunikatów](https://go.microsoft.com/fwlink/?LinkId=119857).|Tekst|  
|Inspekcja|Inspekcja jest możliwość zbadania komunikatów podczas transmisji. Kodowania tekstu, z lub bez użycia protokołu SOAP, zezwalania na komunikaty inspekcji i analizowane przez wiele aplikacji bez użycia specjalistycznych narzędzi. Należy pamiętać, że użycie bezpieczeństwie transferu, na poziomie komunikatu lub transportu, ma wpływ na możliwość kontroli wiadomości. Poufność ochronę komunikat sprawdzane i integralność chroni komunikatu przed modyfikacją.|Tekst|  
|Niezawodność|Niezawodność jest odporność koder błędy transmisji. Niezawodność, może być również dostarczona w wiadomości, transportu lub warstwie aplikacji. Wszystkie standardowe koderów WCF przyjęto założenie, że kolejna warstwa jest zapewnienie niezawodności. Koder zdolność nieco odzyskać sprawność po błędzie transmisji.|Brak|  
|Prostota|Prostota reprezentuje łatwe za pomocą którego można utworzyć kodeków dla specyfikację kodowania. Kodowania tekstu jest szczególnie korzystne dla uproszczenia i kodowanie tekstu POX ma dodatkową zaletą nie wymagających obsługi przetwarzania protokołu SOAP.|Tekst (POX)|  
|Rozmiar|Kodowanie określa Obciążenie nałożone na zawartość. Rozmiar zakodowany wiadomości jest bezpośrednio związana maksymalną przepływność operacji usługi. Kody binarne są zazwyczaj mniejszych niż kodowania tekstu. Jeśli rozmiar komunikatu wynosi premium, należy wziąć pod uwagę także kompresja treści komunikatu podczas kodowania. Jednak kompresji zwiększa koszty przetwarzania dla odbiorcy i nadawcy wiadomości.|plików binarnych|  
|Przesyłanie strumieniowe|Przesyłanie strumieniowe umożliwia aplikacjom rozpoczęcie przetwarzania komunikatu, zanim dotarła cały komunikat. Skutecznie przy użyciu przesyłania strumieniowego wymaga ważnych danych komunikatu dostępną na początku komunikatu tak, aby aplikacja odbierająca nie jest wymagane poczekaj na jego dostarczenie. Ponadto aplikacje, które używają przesyłane strumieniowo transferu musi organizowania danych w komunikacie przyrostowo tak, aby zawartość nie ma zależności skierowane w przód. W wielu przypadkach można naruszyć bezpieczeństwo między przesyłanie strumieniowe zawartości oraz o najmniejszego możliwego rozmiaru możliwe transferu tej zawartości.|Brak|  
|3 Obsługa narzędzia innych firm|Obszary pomocy technicznej w zakresie kodowania obejmują rozwoju i diagnostyki. Deweloperzy innych firm wprowadzono dużych inwestycji w bibliotekach i narzędziach programistycznych obsługi wiadomości zakodowane w formacie POX.|Tekst (POX)|  
|Współdziałanie|Ten współczynnik odnosi się do możliwości kodera WCF do współdziałania z usługami innych WCF.|Tekst<br /><br /> MTOM (częściowa Obsługa)|  
  
Uwaga: Korzystając z kodera binarnego, przy użyciu ustawienia IgnoreWhitespace, tworząc element XMLReader odniesie żadnego skutku.  Na przykład, jeśli wykonasz następujące czynności w operacji usługi:  

```csharp
public void OperationContract(XElement input)
{
    Console.WriteLine("{0}", input.Value);
    int counter = 0;
    var xreader = input.CreateReader();
    var reader = XmlReader.Create(xreader, new XmlReaderSettings() { IgnoreWhitespace = true });
    while (reader.Read())
    {
        counter++;
    }

    Console.WriteLine("Read {0} lines with reader", counter);
}
```  
  
Ustawienie IgnoreWhitespace zostanie zignorowane.  
  
## <a name="compression-and-the-binary-encoder"></a>Kompresja i kodera binarnego

Począwszy od programu WCF 4.5 kodera binarnego WCF dodaje obsługę kompresji. To pozwala na użycie algorytmu gzip nebo deflate do wysyłania wiadomości skompresowany z klienta programu WCF i odpowiada także skompresowane komunikaty o z obsługiwanej samodzielnie usługi WCF. Ta funkcja umożliwia kompresję transportu HTTP i TCP. Usługi WCF hostowanej w programie IIS zawsze być włączona usługa wysyłania skompresowane odpowiedzi, konfigurując serwer hosta usług IIS. Typ kompresji jest skonfigurowany przy użyciu <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement.CompressionFormat%2A?displayProperty=nameWithType> właściwości. Ta właściwość jest ustawiona na jedną z <xref:System.ServiceModel.Channels.CompressionFormat?displayProperty=nameWithType> wartości wyliczenia:

* `CompressionFormat.Deflate`
* `CompressionFormat.GZip`
* `CompressionFormat.None`
  
Ponieważ ta właściwość jest dostępne tylko BinaryMessageEncodingBindingElement, należy utworzyć niestandardowego powiązania podobnie do poniższego, aby użyć tej funkcji:

 ```xml
 <customBinding>
   <binding name="BinaryCompressionBinding">
     <binaryMessageEncoding compressionFormat ="GZip" />
     <httpTransport />
  </binding>
</customBinding>
 ```

Zarówno klient, jak i usługi muszą wyrazić zgodę na wysyłanie i odbieranie komunikatów skompresowane i w związku z tym należy skonfigurować właściwości compressionFormat w elemencie binaryMessageEncoding zarówno klient, jak i usługi. Protocolexception — jest generowany, jeśli usługi lub klienta nie jest skonfigurowany dla kompresji, ale jest drugiej strony. Włączanie kompresji powinien zostać starannie przemyślany. Kompresja przede wszystkim jest przydatne, jeśli przepustowość sieci jest "wąskie gardło". W przypadku, gdy Procesor jest wąskie gardło Kompresja zmniejsza się przepływności. Odpowiednie testy musi odbywać się w środowisku symulowanym, aby dowiedzieć się, jeśli jest to korzystne dla aplikacji  
  
## <a name="see-also"></a>Zobacz też

[Powiązania](../../../../docs/framework/wcf/feature-details/bindings.md)
