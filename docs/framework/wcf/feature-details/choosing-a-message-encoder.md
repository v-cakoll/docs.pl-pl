---
title: Wybieranie kodera komunikatów
ms.date: 03/30/2017
ms.assetid: 2204d82d-d962-4922-a79e-c9a231604f19
ms.openlocfilehash: a306896af7a73d43956638981908c12d86126a9f
ms.sourcegitcommit: 59e36e65ac81cdd094a5a84617625b2a0ff3506e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/27/2020
ms.locfileid: "80345256"
---
# <a name="choosing-a-message-encoder"></a>Wybieranie kodera komunikatów
W tym temacie omówiono kryteria wyboru spośród koderów wiadomości, które są zawarte w Programie Windows Communication Foundation (WCF): mechanizm binarny, tekst i mechanizm optymalizacji transmisji wiadomości (MTOM).  
  
 W WCF można określić sposób przesyłania danych przez sieć między punktami końcowymi za pomocą *powiązania,* które składa się z sekwencji *elementów wiązania.* Koder wiadomości jest reprezentowany przez element wiązania kodowania wiadomości w stosie wiązania. Powiązanie zawiera opcjonalne elementy wiązania protokołu, takie jak element wiązania zabezpieczeń lub element wiązania niezawodnej obsługi wiadomości, wymagany element wiązania kodowania komunikatów i wymagany element wiązania transportu.  
  
 Element wiązania kodowania komunikatów znajduje się poniżej elementów wiązania protokołu opcjonalnego i powyżej wymaganego elementu wiązania transportu. Po stronie wychodzącej koder wiadomości serializuje <xref:System.ServiceModel.Channels.Message> wychodzących i przekazuje go do transportu. Po stronie przychodzącej koder wiadomości odbiera serializowany formularz a <xref:System.ServiceModel.Channels.Message> z transportu i przekazuje go do wyższej warstwy protokołu, jeśli jest obecny, lub do aplikacji, jeśli nie.  
  
 Podczas łączenia się z istniejącym klientem lub serwerem może nie mieć wyboru dotyczące używania kodowania określonej wiadomości, ponieważ należy zakodować wiadomości w sposób oczekiwany przez drugą stronę. Jednak jeśli piszesz usługę WCF, można udostępnić usługi za pośrednictwem wielu punktów końcowych, każdy przy użyciu innego kodowania wiadomości. Dzięki temu klienci mogą wybrać najlepsze kodowanie do rozmowy z usługą za pomocą punktu końcowego, który jest dla nich najlepszy, a także daje klientom elastyczność wyboru kodowania, które jest dla nich najlepsze. Za pomocą wielu punktów końcowych umożliwia również łączenie zalet kodowania różnych komunikatów z innymi elementami wiązania.  
  
## <a name="system-provided-encoders"></a>Enkodery dostarczane przez system  
 WCF zawiera trzy kodery komunikatów, które są reprezentowane przez następujące trzy klasy:  
  
- <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>, koder wiadomości tekstowych obsługuje zarówno zwykłe kodowanie XML, jak i kodowanie protokołu SOAP. Zwykły tryb kodowania XML kodera wiadomości tekstowych jest nazywany "zwykłym starym XML" (POX), aby odróżnić go od kodowania protokołu SOAP opartego na tekście. Aby włączyć pox, <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement.MessageVersion%2A> ustaw <xref:System.ServiceModel.Channels.MessageVersion.None%2A>właściwość na . Użyj kodera wiadomości tekstowych, aby współpracować z punktami końcowymi innych niż WCF.  
  
- <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>, koder wiadomości binarnych, używa kompaktowego formatu binarnego i jest zoptymalizowany pod kątem komunikacji WCF do WCF, a zatem nie jest interoperacyjny. Jest to również najbardziej wydajny koder wszystkich koderów WCF zapewnia.  
  
- <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement>, element wiązania, określa kodowanie znaków i przechowywanie wersji wiadomości dla wiadomości przy użyciu kodowania MTOM. MTOM to wydajna technologia przesyłania danych binarnych w wiadomościach WCF. Koder MTOM próbuje stworzyć równowagę między wydajnością a interoperacyjnością. Kodowanie MTOM przesyła większość XML w formie tekstowej, ale optymalizuje duże bloki danych binarnych, przesyłając je w stanie, w jakim są, bez konwersji na tekst. Pod względem wydajności, wśród koderów WCF zapewnia, MTOM jest pomiędzy tekstem (najwolniejszy) i binarny (najszybszy).  
  
## <a name="how-to-choose-a-message-encoder"></a>Jak wybrać koder wiadomości  
 W poniższej tabeli opisano typowe czynniki używane do wybierania kodera wiadomości. Ustalanie priorytetów czynników, które są ważne dla aplikacji, a następnie wybierz kodery komunikatów, które najlepiej współpracują z tymi czynnikami. Należy wziąć pod uwagę wszelkie dodatkowe czynniki niewymienione w tej tabeli i wszelkie niestandardowe kodery komunikatów, które mogą być wymagane w aplikacji.  
  
|Czynnikiem|Opis|Kodery obsługujące ten czynnik|  
|------------|-----------------|---------------------------------------|  
|Obsługiwane zestawy znaków|<xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>i <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement> obsługuje tylko kodowania UTF8 i UTF16 Unicode *(big-endian* i *little-endian).* Jeśli wymagane są inne kodowania, takie jak UTF7 lub ASCII, należy użyć niestandardowego kodera. Aby uzyskać przykładowy koder niestandardowy, zobacz [Koder wiadomości niestandardowych](https://docs.microsoft.com/dotnet/framework/wcf/samples/custom-message-encoder-custom-text-encoder).|Tekst|  
|Kontroli|Inspekcja to możliwość sprawdzania wiadomości podczas transmisji. Kodowanie tekstu, z lub bez użycia protokołu SOAP, umożliwiają sprawdzanie i analizowanie wiadomości przez wiele aplikacji bez użycia specjalistycznych narzędzi. Należy zauważyć, że użycie zabezpieczeń transferu, na poziomie wiadomości lub transportu, wpływa na możliwość sprawdzania wiadomości. Poufność chroni wiadomość przed badaniem, a integralność chroni wiadomość przed modyfikacją.|Tekst|  
|Niezawodność|Niezawodność to odporność kodera na błędy transmisji. Niezawodność można również zapewnić w warstwie wiadomości, transportu lub aplikacji. Wszystkie standardowe kodery WCF zakładają, że inna warstwa zapewnia niezawodność. Koder ma niewielką możliwość odzyskania po błędzie transmisji.|Brak|  
|Prostota|Prostota reprezentuje łatwość, z jaką można tworzyć kodery i dekodery dla specyfikacji kodowania. Kodowanie tekstu są szczególnie korzystne dla prostoty, a kodowanie tekstu POX ma dodatkową zaletę, że nie wymaga obsługi przetwarzania protokołu SOAP.|Tekst (POX)|  
|Rozmiar|Kodowanie określa ilość narzutów nałożonych na zawartość. Rozmiar zakodowanych komunikatów jest bezpośrednio związany z maksymalną przepływnością operacji serwisowych. Kodowania binarne są na ogół bardziej kompaktowe niż kodowania tekstu. Gdy rozmiar wiadomości jest na premię, należy również rozważyć kompresji zawartości wiadomości podczas kodowania. Jednak kompresja dodaje koszty przetwarzania zarówno dla nadawcy wiadomości, jak i odbiorcy.|plików binarnych|  
|Przesyłanie strumieniowe|Przesyłanie strumieniowe umożliwia aplikacjom rozpoczęcie przetwarzania wiadomości przed nadejdą całej wiadomości. Skutecznie przy użyciu przesyłania strumieniowego wymaga, aby ważne dane dla wiadomości być dostępne na początku wiadomości, tak aby aplikacja odbierająca nie jest wymagane czekać na jej przybycie. Ponadto aplikacje korzystające z przesyłania strumieniowego muszą organizować dane w wiadomości przyrostowo, aby zawartość nie miała zależności do przodu. W wielu przypadkach należy naruszyć problem między zawartością przesyłania strumieniowego a posiadaniem najmniejszego możliwego rozmiaru transferu dla tej zawartości.|Brak|  
|Obsługa narzędzi innych firm|Obszary pomocy technicznej dotyczące kodowania obejmują rozwój i diagnostykę. Deweloperzy innych firm poczynili duże inwestycje w biblioteki i zestawy narzędzi do obsługi wiadomości zakodowanych w formacie POX.|Tekst (POX)|  
|Współdziałanie|Ten czynnik odnosi się do zdolności kodera WCF do współpracy z usługami innych niż WCF.|Tekst<br /><br /> MTOM (częściowy)|  
  
Uwaga: Podczas korzystania z binarnego kodera, przy użyciu IgnoreWhitespace ustawienie podczas tworzenia XMLReader nie będzie miało wpływu.  Na przykład, jeśli wykonasz następujące czynności wewnątrz operacji usługi:  

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
  
Ustawienie IgnoreWhitespace jest ignorowane.  
  
## <a name="compression-and-the-binary-encoder"></a>Kompresja i koder binarny

Począwszy od WCF 4.5 koder binarny WCF dodaje obsługę kompresji. Dzięki temu można używać algorytmu gzip/deflate do wysyłania skompresowanych wiadomości z klienta WCF, a także odpowiadać za pomocą skompresowanych wiadomości z usługi WCF hostowanej samodzielnie. Ta funkcja umożliwia kompresję zarówno na transportach HTTP i TCP. Usługę WCF hostowanych usług usług IIS zawsze można włączyć do wysyłania skompresowanych odpowiedzi, konfigurując serwer hosta usług IIS. Typ kompresji jest skonfigurowany <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement.CompressionFormat%2A?displayProperty=nameWithType> z właściwością. Ta właściwość jest ustawiona na jedną z wartości wyliczenia: <xref:System.ServiceModel.Channels.CompressionFormat?displayProperty=nameWithType>

- <xref:System.ServiceModel.Channels.CompressionFormat.Deflate>
- <xref:System.ServiceModel.Channels.CompressionFormat.GZip>
- <xref:System.ServiceModel.Channels.CompressionFormat.None>
  
Ponieważ ta właściwość jest dostępna tylko na binaryMessageEncodingBindingElement, należy utworzyć niestandardowe powiązanie, takie jak następujące, aby użyć tej funkcji:

 ```xml
 <customBinding>
   <binding name="BinaryCompressionBinding">
     <binaryMessageEncoding compressionFormat ="GZip" />
     <httpTransport />
  </binding>
</customBinding>
 ```

Zarówno klient, jak i usługa muszą wyrazić zgodę na wysyłanie i odbieranie skompresowanych komunikatów i dlatego właściwość compressionFormat musi być skonfigurowana na elemencie binaryMessageEncoding na kliencie i usłudze. A ProtocolException jest zgłaszany, jeśli usługa lub klient nie jest skonfigurowany do kompresji, ale druga strona jest. Włączenie kompresji należy dokładnie rozważyć. Kompresja jest najczęściej przydatna, jeśli przepustowość sieci jest wąskim gardłem. W przypadku, gdy procesor jest wąskim gardłem, kompresja zmniejszy przepustowość. Należy przeprowadzić odpowiednie badania w symulowanym środowisku, aby dowiedzieć się, czy jest to korzystne dla aplikacji  
  
## <a name="see-also"></a>Zobacz też

- [Powiązania](../../../../docs/framework/wcf/feature-details/bindings.md)
