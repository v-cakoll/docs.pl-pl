---
title: Wybieranie kodera komunikatów
ms.date: 03/30/2017
ms.assetid: 2204d82d-d962-4922-a79e-c9a231604f19
ms.openlocfilehash: dbc5981013fe5e023f1d6d9eaf64b2e1fa18e2df
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84587342"
---
# <a name="choose-a-message-encoder"></a>Wybierz koder komunikatów

W tym artykule omówiono kryteria umożliwiające wybór między koderami komunikatów zawartymi w Windows Communication Foundation (WCF): mechanizm optymalizacji komunikacji binarnej, tekstu i przesyłania komunikatów (MTOM).  
  
 W programie WCF należy określić sposób transferu danych między punktami końcowymi przy użyciu *powiązania*, które składa się z sekwencji *elementów powiązania*. Koder komunikatów jest reprezentowany przez element powiązania kodowania komunikatu w stosie powiązań. Powiązanie obejmuje opcjonalne elementy powiązania protokołów, takie jak element powiązania zabezpieczeń lub element powiązania niezawodnej obsługi komunikatów, wymagany element powiązania kodowania komunikatów i wymagany element powiązania transportu.  
  
 Element powiązania kodowania komunikatu znajduje się poniżej opcjonalne elementy powiązania protokołu i powyżej wymaganego elementu powiązania transportu. Po stronie wychodzącej koder komunikatów serializować wychodzące <xref:System.ServiceModel.Channels.Message> i przekazuje je do transportu. Po stronie przychodzącej koder komunikatów otrzymuje zserializowaną formę z <xref:System.ServiceModel.Channels.Message> transportu i przekazuje go do warstwy wyższej protokołu, jeśli jest obecny lub do aplikacji, jeśli nie.  
  
 Podczas nawiązywania połączenia z istniejącym klientem lub serwerem nie można wybrać, jak używać określonego kodowania komunikatów, ponieważ należy zakodować komunikaty w taki sposób, że jest to oczekiwane. Jednak w przypadku pisania usługi WCF można uwidocznić usługę za pomocą wielu punktów końcowych, z których każdy korzysta z innego kodowania komunikatów. Dzięki temu klienci mogą wybrać najlepsze kodowanie do rozmowy z usługą za pośrednictwem punktu końcowego, który jest najlepszy dla nich, a także zapewnić klientom elastyczność wybierania najlepszego dla nich kodowania. Używanie wielu punktów końcowych umożliwia również łączenie zalet różnych kodowań komunikatów z innymi elementami powiązania.  
  
## <a name="system-provided-encoders"></a>Kodery dostarczone przez system  
 Program WCF zawiera trzy kodery komunikatów, które są reprezentowane przez następujące trzy klasy:  
  
- <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>koder wiadomości SMS obsługuje zarówno zwykłe Kodowanie XML, jak i kodowanie protokołu SOAP. Tryb zwykłego kodowania XML kodera wiadomości tekstowych jest nazywany "zwykłym starym plikiem XML" (POX) w celu odróżnienia go od kodowania SOAP opartego na tekście. Aby włączyć POX, ustaw <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement.MessageVersion%2A> Właściwość na <xref:System.ServiceModel.Channels.MessageVersion.None%2A> . Użyj kodera wiadomości tekstowych do współpracy z punktami końcowymi spoza usługi WCF.  
  
- <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>kodera komunikatów binarnych używa kompaktowego formatu binarnego, który jest zoptymalizowany pod kątem komunikacji WCF z usługą WCF i w związku z tym nie jest obsługiwany. Jest to również najbardziej wydajny koder wszystkich koderów udostępnianych przez funkcję WCF.  
  
- <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement>, element Binding, określa kodowanie znaków i przechowywanie wersji komunikatów dla komunikatów przy użyciu kodowania MTOM. MTOM to wydajna technologia przesyłania danych binarnych w komunikatach programu WCF. Koder MTOM próbuje utworzyć balans między wydajnością i współdziałaniem. Kodowanie MTOM przesyła większość XML w postaci tekstowej, ale optymalizuje duże bloki danych binarnych przez przesłanie ich bez konwersji do tekstu. W zakresie wydajności, wśród koderów WCF zapewnia, MTOM jest między tekstem (najwolniejszym) i binarnym (najszybszy).  
  
## <a name="how-to-choose-a-message-encoder"></a>Jak wybrać koder komunikatów  
 W poniższej tabeli opisano typowe czynniki używane do wybierania kodera komunikatów. Określ priorytety czynników, które są ważne dla aplikacji, a następnie wybierz kodery komunikatów, które najlepiej współpracują z tymi czynnikami. Należy wziąć pod uwagę wszelkie dodatkowe czynniki, które nie są wymienione w tej tabeli oraz wszystkie niestandardowe kodery komunikatów, które mogą być wymagane w aplikacji.  
  
|1U|Opis|Kodery obsługujące ten czynnik|  
|------------|-----------------|---------------------------------------|  
|Obsługiwane zestawy znaków|<xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>i <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement> obsługują tylko kodowania w formacie Unicode i UTF16 (*big-endian* i *little-endian*). Jeśli wymagane są inne kodowania, takie jak UTF7 lub ASCII, należy użyć kodera niestandardowego. Aby zapoznać się z przykładowym koderem niestandardowym, zobacz [niestandardowy koder komunikatów](https://docs.microsoft.com/dotnet/framework/wcf/samples/custom-message-encoder-custom-text-encoder).|Tekst|  
|Przedubojowego|Inspekcja umożliwia badanie komunikatów podczas przesyłania. Kodowanie tekstu, z lub bez użycia protokołu SOAP, pozwala na inspekcję i analizowanie komunikatów przez wiele aplikacji bez używania wyspecjalizowanych narzędzi. Korzystanie z zabezpieczeń transferu, na poziomie wiadomości lub transportu, wpływa na możliwość inspekcji komunikatów. Poufność chroni komunikat przed badaniem i zapewnia integralność chroniącą wiadomość przed modyfikacją.|Tekst|  
|Niezawodność|Niezawodność to odporność kodera na błędy transmisji. Niezawodność można także zapewnić przy użyciu komunikatów, transportu lub warstwy aplikacji. W przypadku wszystkich standardowych koderów WCF przyjęto założenie, że inna warstwa zapewnia niezawodność. Koder ma mało możliwości odzyskania sprawności po błędzie transmisji.|Brak|  
|Zapewni|Prostota przedstawia łatwość, za pomocą których można tworzyć kodery i dekodery dla specyfikacji kodowania. Kodowanie tekstu jest szczególnie korzystne dla uproszczenia, a kodowanie tekstu POX ma dodatkową zaletę, która nie wymaga obsługi przetwarzania protokołu SOAP.|Tekst (POX)|  
|Rozmiar|Kodowanie określa wielkość narzutu nałożoną na zawartość. Rozmiar zakodowanych komunikatów jest bezpośrednio związany z maksymalną przepływność operacji usługi. Kodowanie binarne są zwykle bardziej kompaktowe niż kodowania tekstu. Gdy rozmiar wiadomości jest w wersji Premium, należy rozważyć również kompresję zawartości komunikatu podczas kodowania. Jednak kompresja dodaje koszty przetwarzania zarówno dla nadawcy wiadomości, jak i odbiorcy.|Binarne|  
|Przesyłanie strumieniowe|Przesyłanie strumieniowe umożliwia aplikacjom rozpoczęcie przetwarzania komunikatów przed odebraniem całego komunikatu. Efektywne korzystanie z przesyłania strumieniowego wymaga, aby ważne dane dla wiadomości były dostępne na początku wiadomości, dzięki czemu aplikacja do odbierania nie musi czekać na jej dostarczenie. Ponadto aplikacje korzystające z transferu przesyłanego strumieniowo muszą organizować dane w wiadomości przyrostowo, dzięki czemu zawartość nie ma zależności do przesyłania dalej. W wielu przypadkach należy wymusić kompromis między zawartością przesyłania strumieniowego i rozmiarem najmniejszego możliwego rozmiaru transferu dla tej zawartości.|Brak|  
|Obsługa narzędzi innych firm|Obszary obsługi kodowania obejmują programowanie i diagnostykę. Deweloperzy innych firm zapełnili duże inwestycje w biblioteki i zestawy narzędzi do obsługi wiadomości zakodowanych w formacie POX.|Tekst (POX)|  
|Współdziałanie|Ten czynnik oznacza możliwość współdziałania kodera WCF z usługami nieopartymi na usłudze WCF.|Tekst<br /><br /> MTOM (częściowa)|  
  
Uwaga: w przypadku używania kodera binarnego użycie ustawienia IgnoreWhitespace podczas tworzenia elementu XMLReader nie będzie miało żadnego efektu.  Na przykład, jeśli wykonasz następujące czynności w ramach operacji usługi:  

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

Począwszy od programu WCF 4,5 koder binarny WCF dodaje obsługę kompresji. Dzięki temu można używać algorytmu GZip/Wklęśnięcie do wysyłania skompresowanych komunikatów z klienta programu WCF, a także odpowiedzi na skompresowane komunikaty z własnej hostowanej usługi WCF. Ta funkcja umożliwia kompresję zarówno transportów HTTP, jak i TCP. Usługi WCF hostowanej przez usługi IIS zawsze można włączyć do wysyłania skompresowanych odpowiedzi przez skonfigurowanie serwera hosta usług IIS. Typ kompresji jest konfigurowany z <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement.CompressionFormat%2A?displayProperty=nameWithType> właściwością. Ta właściwość jest ustawiona na jedną z <xref:System.ServiceModel.Channels.CompressionFormat?displayProperty=nameWithType> wartości wyliczenia:

- <xref:System.ServiceModel.Channels.CompressionFormat.Deflate>
- <xref:System.ServiceModel.Channels.CompressionFormat.GZip>
- <xref:System.ServiceModel.Channels.CompressionFormat.None>
  
Ponieważ ta właściwość jest uwidaczniana tylko w binaryMessageEncodingBindingElement, konieczne będzie utworzenie niestandardowego powiązania, takiego jak następujące, aby użyć tej funkcji:

 ```xml
 <customBinding>
   <binding name="BinaryCompressionBinding">
     <binaryMessageEncoding compressionFormat ="GZip" />
     <httpTransport />
  </binding>
</customBinding>
 ```

Zarówno klient, jak i usługa muszą wyrazić zgodę na wysyłanie i odbieranie skompresowanych komunikatów, w związku z czym Właściwość compressionFormat musi być skonfigurowana dla elementu binaryMessageEncoding zarówno na kliencie, jak i w usłudze. Zostanie zgłoszony wyjątek ProtocolException, jeśli usługa lub klient nie jest skonfigurowany do kompresji, ale druga strona to. Należy uważnie rozważyć włączenie kompresji. Kompresja jest przede wszystkim przydatna, jeśli przepustowość sieci jest wąskim gardłem. W przypadku, gdy procesor CPU jest wąskim gardłem, kompresja obniży przepływność. Należy wykonać odpowiednie testy w symulowanym środowisku, aby dowiedzieć się, czy ta korzyść ma zastosowanie do aplikacji  
  
## <a name="see-also"></a>Zobacz też

- [Powiązania](bindings.md)
