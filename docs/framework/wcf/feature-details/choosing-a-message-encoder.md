---
title: "Wybieranie kodera komunikatów"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2204d82d-d962-4922-a79e-c9a231604f19
caps.latest.revision: "19"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 1d19a4e925fef7fa904b6f866719d593b93db6fa
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="choosing-a-message-encoder"></a>Wybieranie kodera komunikatów
W tym temacie omówiono kryteria wybierania koderów wiadomości, które znajdują się w [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]: binary, tekst i mechanizmu optymalizacji transmisji wiadomości (MTOM).  
  
 W [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], określ sposób transferu danych za pośrednictwem sieci między punktami końcowymi za pomocą klasy *powiązania*, która składa się z sekwencji *elementów wiązania*. Koder komunikatów jest reprezentowany przez element powiązania w stosie powiązanie kodowania komunikatu. Powiązanie zawiera elementów powiązania protokołu opcjonalnych, takich jak elementu powiązania zabezpieczeń lub niezawodnej obsługi komunikatów element powiązania, wiadomości wymagane kodowanie elementu powiązania, a element powiązania transportu wymagane.  
  
 Element powiązania kodowania komunikatu znajduje się poniżej elementy powiązania protokołu opcjonalne i powyżej elementu powiązania transportu wymagane. Na stronie wychodzących kodera wiadomości serializuje wychodzącej <xref:System.ServiceModel.Channels.Message> i przekazuje je do transportu. Na stronie przychodzące kodera wiadomości odbiera serializacji formę <xref:System.ServiceModel.Channels.Message> z transportu i przekazuje go do protokołu wyższej warstwy, jeśli istnieje, lub do aplikacji, jeśli nie.  
  
 Podczas łączenia z istniejącego klienta lub serwera, możesz nie mieć wybór o przy użyciu kodowania danego komunikatu, ponieważ należy do kodowania wiadomości w taki sposób, który jest oczekiwany po drugiej stronie. Jednak jeśli piszesz [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usługi z usługą za pomocą wiele punktów końcowych, mogą uwidaczniać każdego przy użyciu kodowania inny komunikat. Pozwala to klientom wybrać optymalne kodowanie na potrzeby komunikuje się z usługą za pośrednictwem punktu końcowego, który jest najbardziej przydatna w przypadku ich, zapewniając elastyczność wybierz metodę kodowania, która jest najlepsze dla nich klientów. Przy użyciu wielu punktów końcowych umożliwia również łączyć z innymi elementami powiązanie korzyści wynikające z kodowania innego wiadomości.  
  
## <a name="system-provided-encoders"></a>Kodery dostarczane przez system  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]obejmuje trzy koderów wiadomości, które są reprezentowane przez następujących trzech klas:  
  
-   <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>, kodera wiadomości tekstowych, obsługuje zarówno zwykły Kodowanie XML i kodowania protokołu SOAP. Zwykły tryb kodowania XML kodera wiadomości tekstowych nazywa się "zwykły starego XML" (POX) do odróżnienia tekstowych kodowania protokołu SOAP. Aby włączyć POX, ustaw <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement.MessageVersion%2A> właściwości <xref:System.ServiceModel.Channels.MessageVersion.None%2A>. Użyj kodera wiadomości tekstowe na potrzeby współdziałania z inną niż[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] punktów końcowych.  
  
-   <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>, binarnego kodera wiadomości, w formacie kompaktowym binarne i jest zoptymalizowany pod kątem [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] do [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] komunikację i dlatego nie współpracuje. Dotyczy to również największą wydajność kodera wszystkich koderów [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] udostępnia.  
  
-   <<!--zz xref:System.ServiceModel.Channels.MTOMMessageEncodingBindingElement -->`System.ServiceModel.Channels.MTOMMessageEncodingBindingElement`>, element powiązania Określa kodowanie znaków i wersji komunikatu dla komunikatów przy użyciu kodowania MTOM. MTOM jest technologią wydajne przekazywania danych binarnych w [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] wiadomości. Koder MTOM podejmuje próbę utworzenia równowagi między wydajności i współdziałanie. Kodowanie MTOM przesyła większości XML w postaci tekstowej, ale optymalizuje dużych bloków danych binarnych, przekazując je jako — Brak konwersji na tekst. Pod względem wydajności między koderów [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] zapewnia MTOM jest tekst między nimi (najwolniejsze) i pliku binarnego (najszybciej).  
  
## <a name="how-to-choose-a-message-encoder"></a>Wybieranie kodera komunikatów  
 W poniższej tabeli opisano typowych czynników, które umożliwiają wybieranie kodera wiadomości. Priorytet czynników, które są ważne w przypadku aplikacji, a następnie wybierz pozycję koderów komunikat pracy najlepiej z tych czynników. Należy wziąć pod uwagę żadnych dodatkowych czynników, które nie są wymienione w tej tabeli i wszelkie koderów niestandardowy komunikat, które mogą być wymagane w aplikacji.  
  
|Współczynnik|Opis|Kodery obsługujące ten współczynnik|  
|------------|-----------------|---------------------------------------|  
|Obsługiwanych zestawów znaków|<xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>i <<!--zz xref:System.ServiceModel.Channels.MTOMMessageEncodingBindingElement --> `System.ServiceModel.Channels.MTOMMessageEncodingBindingElement`> obsługuje tylko UTF8 i UTF16 Unicode (*big-endian* i *little endian*) kodowania. Jeśli inne kodowanie są wymagane, takie jak UTF7 lub ASCII, należy użyć niestandardowego kodera. Na przykład niestandardowego kodera, zobacz [niestandardowy koder komunikatów](http://go.microsoft.com/fwlink/?LinkId=119857).|Tekst|  
|Inspekcji|Inspekcja jest możliwość Sprawdź komunikaty podczas przesyłania. Kodowania tekstu, z lub bez użycia protokołu SOAP, zezwolić na komunikaty inspekcji i analizowane przez wiele aplikacji bez użycia narzędzia specjalne. Należy pamiętać, że użycie transfer zabezpieczenia na poziomie komunikatu lub transportu, wpływa na możliwość Sprawdź komunikaty. Poufność uniemożliwia badane wiadomości i integralności chroni komunikat przed modyfikacją.|Tekst|  
|Niezawodność|Niezawodność jest odporność kodera błędy transmisji. Można również podać niezawodność w wiadomości, transportu lub warstwy aplikacji. Wszystkie standardowe [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] koderów założono, że kolejną warstwę zapewnia niezawodność. Koder ma mało możliwość odzyskania po błędzie podczas transmisji.|Brak|  
|Prostota|Prostota reprezentuje łatwość, z którym można utworzyć kodeków dotyczyło kodowania. Kodowania tekstu są szczególnie korzystne dla uproszczenia i kodowanie tekstu POX ma dodatkowe zaletą nie wymaga obsługi przetwarzania protokołu SOAP.|Tekst (POX)|  
|Rozmiar|Kodowanie określa narzut na zawartość. Rozmiar zakodowanej wiadomości jest bezpośrednio powiązana maksymalnej przepływności operacji usługi. Kodowanie binarne są zazwyczaj mniejszych niż kodowania tekstu. Jeśli rozmiar wiadomości jest, należy wziąć pod uwagę także kompresja treść komunikatu podczas kodowania. Jednak kompresji dodaje koszty przetwarzania nadawca i odbiorca.|plików binarnych|  
|przesyłanie strumieniowe|Przesyłanie strumieniowe umożliwia aplikacjom rozpoczęcie przetwarzania komunikatu, zanim dotarła cały komunikat. Efektywnie przy użyciu przesyłania strumieniowego wymaga ważnych danych dla wiadomości dostępną na początku wiadomości, aby aplikacja odbierająca nie jest wymagane o jego odebranie. Ponadto aplikacje używające przesyłanej strumieniowo transfer musi organizowania danych w komunikacie przyrostowo tak, aby zawartość nie ma zależności skierowane w przód. W wielu przypadkach można znaleźć kompromis między przesyłanie strumieniowe zawartości oraz posiadające najmniejsze możliwe transferu tej zawartości.|Brak|  
|Obsługa narzędzia firm 3|Obszary pomocy technicznej dla kodowania to programowanie i diagnostyki. Inne firmy zostały wprowadzone dużych inwestycji w bibliotekach i narzędzi obsługi wiadomości zakodowane w formacie POX.|Tekst (POX)|  
|Współdziałanie|Współczynnik ten odnosi się do funkcji [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] koder na potrzeby współdziałania z inną niż[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usług.|Tekst<br /><br /> MTOM (częściowe)|  
  
Uwaga: Przy użyciu kodera binarnego, przy użyciu ustawienia IgnoreWhitespace, tworząc element XMLReader nie odniesie żadnego skutku.  Na przykład, jeśli wykonaj następujące czynności wewnątrz operacji usługi:  

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

Począwszy od WCF 4.5 kodera binarnego WCF dodaje obsługę kompresji. To pozwala na użycie algorytm gzip/deflate do wysyłania wiadomości skompresowany z klienta programu WCF i również odpowiadać, podając skompresowany wiadomości z własnym hostowanej usługi WCF. Ta funkcja umożliwia kompresji HTTP i TCP transportów. Usługi WCF hostowanej w programie IIS zawsze być włączona usługa wysyłania skompresowane odpowiedzi przez skonfigurowanie serwera hosta usług IIS. Typ kompresji jest konfigurowana <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement.CompressionFormat%2A?displayProperty=nameWithType> właściwości. Ta właściwość jest ustawiona na jeden z <xref:System.ServiceModel.Channels.CompressionFormat?displayProperty=nameWithType> wartości wyliczeniowych:

* `CompressionFormat.Deflate`
* `CompressionFormat.GZip`
* `CompressionFormat.None`
  
Ponieważ ta właściwość jest dostępne tylko BinaryMessageEncodingBindingElement, należy utworzyć niestandardowego powiązania podobnie do następującej, aby użyć tej funkcji:

 ```xml
 <customBinding>
   <binding name="BinaryCompressionBinding">
     <binaryMessageEncoding compressionFormat ="GZip" />
     <httpTransport />
  </binding>
</customBinding>
 ```

Klient i usługa muszą zgodę na wysyłanie i odbieranie wiadomości skompresowany, a w związku z tym należy skonfigurować właściwości compressionFormat w elemencie binaryMessageEncoding zarówno klient, jak i usługi. Jeśli usługi lub klienta nie jest skonfigurowany do kompresji, ale jest druga Strona, zostanie zgłoszony wyjątek. Włączanie kompresji należy starannie rozważyć. Kompresja przede wszystkim jest przydatne, jeśli przepustowość sieci jest wąskiego gardła. W przypadku, gdy procesor CPU stanowi wąskie gardło Kompresja zmniejsza się przepływności. Testowanie odpowiednie musi zostać wykonane w środowisku symulowanym, aby dowiedzieć się, jeśli jest to korzystne dla aplikacji  
  
## <a name="see-also"></a>Zobacz też

[Powiązania](../../../../docs/framework/wcf/feature-details/bindings.md)
