---
title: Serializacja
ms.date: 07/20/2015
ms.assetid: 67379a76-5465-4af8-a781-0b0b25a62d9a
ms.openlocfilehash: db14147a23940fa2403613036750be1bca566e8e
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84413144"
---
# <a name="serialization-visual-basic"></a>Serializacja (Visual Basic)
Serializacja to proces konwersji obiektu do strumienia bajtów w celu przechowywania obiektu lub przesyłania go do pamięci, bazy danych lub pliku. Jego głównym celem jest zapisanie stanu obiektu, aby można było go odtworzyć w razie potrzeby. Proces odwrotny nazywa się deserializacji.  
  
## <a name="how-serialization-works"></a>Jak działa Serializacja  
 Na tej ilustracji przedstawiono ogólny proces serializacji.  
  
![Grafika serializacji](./media/index/serialization-process.gif)
  
 Obiekt jest serializowany do strumienia, który przeprowadzi nie tylko dane, ale informacje o typie obiektu, takie jak jego wersja, kultura i nazwa zestawu. Ze strumienia można go przechowywać w bazie danych, pliku lub pamięci.  
  
### <a name="uses-for-serialization"></a>Używa do serializacji  
 Serializacja umożliwia deweloperowi zapisanie stanu obiektu i ponowne utworzenie go w razie potrzeby, zapewniając przechowywanie obiektów oraz wymianę danych. Dzięki serializacji programista może wykonywać takie działania, jak wysyłanie obiektu do aplikacji zdalnej za pomocą usługi sieci Web, przekazywanie obiektu z jednej domeny do drugiego, przekazywanie obiektu przez zaporę jako ciąg XML lub utrzymywanie zabezpieczeń lub informacji specyficznych dla użytkownika w aplikacjach.  
  
### <a name="making-an-object-serializable"></a>Tworzenie obiektu jako możliwego do serializacji  
 Aby serializować obiekt, wymagany jest obiekt, który ma być serializowany, strumień zawierający serializowany obiekt i <xref:System.Runtime.Serialization.Formatter> . <xref:System.Runtime.Serialization>zawiera klasy niezbędne do serializacji i deserializacji obiektów.  
  
 Zastosuj <xref:System.SerializableAttribute> atrybut do typu, aby wskazać, że wystąpienia tego typu mogą być serializowane. <xref:System.Runtime.Serialization.SerializationException>Wyjątek jest zgłaszany w przypadku próby serializacji, ale typ nie ma <xref:System.SerializableAttribute> atrybutu.  
  
 Jeśli nie chcesz, aby w klasie nie można było serializować pola, Zastosuj <xref:System.NonSerializedAttribute> atrybut. Jeśli pole o typie możliwym do serializacji zawiera wskaźnik, uchwyt lub inną strukturę danych, która jest specyficzna dla określonego środowiska, a pole nie może być w znaczący sposób odtworzone w innym środowisku, można sprawić, aby nie można było jej serializować.  
  
 Jeśli Serializacja klasy zawiera odwołania do obiektów innych klas, które są oznaczone <xref:System.SerializableAttribute> , te obiekty również będą serializowane.  
  
## <a name="binary-and-xml-serialization"></a>Serializacja binarna i XML  
 Można użyć serializacji binarnej lub XML. W serializacji binarnej wszystkie elementy członkowskie, nawet te, które są tylko do odczytu, są serializowane i zwiększają wydajność. Serializacja XML zapewnia bardziej czytelny kod, a także większą elastyczność udostępniania obiektów i użycia na potrzeby współdziałania.  
  
### <a name="binary-serialization"></a>Serializacja binarna  
 Serializacja binarna korzysta z kodowania binarnego w celu utworzenia kompaktowej serializacji do użycia, takich jak magazyn lub strumienie sieciowe oparte na gnieździe.  
  
### <a name="xml-serialization"></a>Serializacji XML  
 Serializacji XML serializować pola publiczne i właściwości obiektu, lub parametry i wartości zwracane metod do strumienia XML, który jest zgodny z konkretnym dokumentem języka definicji schematu XML (XSD). Serializacja XML skutkuje silnie określonymi klasami z właściwościami publicznymi i polami, które są konwertowane na format XML. <xref:System.Xml.Serialization>zawiera klasy niezbędne do serializacji i deserializacji XML.  
  
 Można zastosować atrybuty do klas i elementów członkowskich klasy w celu kontrolowania sposobu <xref:System.Xml.Serialization.XmlSerializer> serializacji lub deserializacji wystąpienia klasy.  
  
## <a name="basic-and-custom-serialization"></a>Serializacja podstawowa i niestandardowa  
 Serializacja można wykonać na dwa sposoby — podstawowa i niestandardowa. Serializacja podstawowa używa .NET Framework do automatycznego serializacji obiektu.  
  
### <a name="basic-serialization"></a>Serializacja podstawowa  
 Jedynym wymaganiem w serializacji podstawowej jest to, że obiekt ma <xref:System.SerializableAttribute> zastosowany atrybut. <xref:System.NonSerializedAttribute>Może służyć do zachowywania serializacji określonych pól.  
  
 W przypadku korzystania z serializacji podstawowej wersja obiektów może tworzyć problemy, w których może być preferowana Serializacja niestandardowa. Serializacja podstawowa jest najprostszym sposobem na wykonywanie serializacji, ale nie zapewnia większej kontroli nad procesem.  
  
### <a name="custom-serialization"></a>Serializacja niestandardowa  
 W przypadku serializacji niestandardowej można określić, które obiekty będą serializowane i jak będą wykonywane. Klasa musi być oznaczona <xref:System.SerializableAttribute> i implementować <xref:System.Runtime.Serialization.ISerializable> interfejs.  
  
 Jeśli chcesz, aby obiekt był deserializowany w sposób niestandardowy, musisz użyć konstruktora niestandardowego.  
  
## <a name="designer-serialization"></a>Serializacja projektanta  
 Serializacja projektanta jest specjalną formą serializacji, która obejmuje rodzaj trwałości obiektu zazwyczaj skojarzony z narzędziami programistycznymi. Serializacja projektanta to proces przekonwertowania grafu obiektów na plik źródłowy, który można później użyć do odzyskania grafu obiektów. Plik źródłowy może zawierać kod, znacznik, a nawet informacje tabeli SQL.  
  
## <a name="related-topics-and-examples"></a><a name="BKMK_RelatedTopics"></a>Tematy pokrewne i przykłady  
 [Przewodnik: utrwalanie obiektu w programie Visual Studio (Visual Basic)](walkthrough-persisting-an-object-in-visual-studio.md)  
 Pokazuje, jak Serializacja może być używana do utrwalania danych obiektu między wystąpieniami, umożliwiając przechowywanie wartości i pobieranie ich przy następnym tworzeniu wystąpienia obiektu.  
  
 [Instrukcje: odczytywanie danych obiektu z pliku XML (Visual Basic)](how-to-read-object-data-from-an-xml-file.md)  
 Pokazuje, jak odczytywać dane obiektów, które zostały wcześniej zapisaną w pliku XML przy użyciu <xref:System.Xml.Serialization.XmlSerializer> klasy.  
  
 [Instrukcje: zapisywanie danych obiektu w pliku XML (Visual Basic)](how-to-write-object-data-to-an-xml-file.md)  
 Pokazuje, jak napisać obiekt z klasy do pliku XML przy użyciu <xref:System.Xml.Serialization.XmlSerializer> klasy.
