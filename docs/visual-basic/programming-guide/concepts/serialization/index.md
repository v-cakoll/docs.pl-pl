---
title: Serializacja (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 67379a76-5465-4af8-a781-0b0b25a62d9a
---
# <a name="serialization-visual-basic"></a>Serializacja (Visual Basic)
Serializacja jest proces konwersji obiektu do strumienia bajtów, aby można było zapisać obiekt lub przekazuje je do pamięci, bazie danych lub pliku. Głównym celem jest zapisanie stanu obiektu, aby można było utworzyć ponownie w razie. Zwrotny proces jest nazywany deserializacji.  
  
## <a name="how-serialization-works"></a>Jak działa serializacji  
 Ta ilustracja przedstawia ogólny proces serializacji.  
  
![Grafika przedstawiająca serializację](./media/index/serialization-process.gif)
  
 Obiekt jest serializowany do strumienia, niesie ze sobą nie tylko dane, ale informacje o typie obiektu, takie jak jego nazwa wersji, kultury i zestawu. W strumieniu mogą być przechowywane w bazie danych, plików lub ilości pamięci.  
  
### <a name="uses-for-serialization"></a>Zastosowań serializacji  
 Serializacja umożliwia deweloperowi zapisany stan obiektu i utwórz go ponownie zgodnie z potrzebami, przeznaczone do przechowywania obiektów, a także wymiany danych. Za pomocą serializacji, deweloper można wykonać akcje, takie jak wysyłanie obiektu do zdalnej aplikacji za pomocą usługi sieci Web, przekazywania obiektu z jednej domeny do innego, przekazywania obiektu przez zaporę jako ciąg znaków XML lub zachowanie bezpieczeństwa lub informacje dotyczące użytkownika w aplikacjach.  
  
### <a name="making-an-object-serializable"></a>Tworzenie możliwych do serializacji obiektu  
 Do serializacji obiektu, należy obiekt do zserializowania, strumień zawiera Zserializowany obiekt oraz a <xref:System.Runtime.Serialization.Formatter>. <xref:System.Runtime.Serialization> zawiera klasy, które są niezbędne do serializacji i deserializacji obiektów.  
  
 Zastosuj <xref:System.SerializableAttribute> atrybutu typu, aby wskazać, że wystąpień tego typu może być serializowany. A <xref:System.Runtime.Serialization.SerializationException> wyjątek jest generowany, jeśli próby serializacji, ale typ <xref:System.SerializableAttribute> atrybutu.  
  
 Jeśli nie mają pola w obrębie swojej klasy jako możliwy do serializacji, zastosuj <xref:System.NonSerializedAttribute> atrybutu. Jeśli pole typu umożliwiającego serializację zawiera wskaźnik, dojście lub niektóre inne struktury danych, które są specyficzne dla określonego środowiska i pola nie może być znacząco odtworzone w innym środowisku, może być zapewnienie nonserializable.  
  
 Jeśli klasa serializacji zawiera odwołania do obiektów innych klas, które są oznaczone <xref:System.SerializableAttribute>, również będą wykonywane szeregowo tych obiektów.  
  
## <a name="binary-and-xml-serialization"></a>Binarne i serializacji XML  
 Dane binarne lub serializacji XML może służyć. Serializacja binarna wszystkich elementów członkowskich, nawet te, które są tylko do odczytu są serializowane i zwiększa wydajność. Serializacji XML zapewnia lepszą czytelność kodu, a także większą elastyczność użycia na współdziałanie i udostępniania obiektów.  
  
### <a name="binary-serialization"></a>Serializacja binarna  
 Serializacja binarna używa kodowania binarnego w celu wygenerowania compact serializacji dla zastosowań, takich jak pamięci masowej lub sieci na podstawie gniazda strumieni.  
  
### <a name="xml-serialization"></a>Serializacji XML  
 Serializacji XML serializuje pola publiczne i właściwości obiektu, lub parametry i wartości zwracane metod do strumień XML, który odpowiada określony dokument języka (XSD) definicji schematu XML. Wyniki serializacji XML w silnie typizowane klasy z właściwości publiczne i pola, które są konwertowane na format XML. <xref:System.Xml.Serialization> zawiera klasy, które są niezbędne do serializacji i deserializacji XML.  
  
 Atrybuty można zastosować do klas i składowych klasy, aby kontrolować sposób <xref:System.Xml.Serialization.XmlSerializer> serializuje i deserializuje wystąpienia klasy.  
  
## <a name="basic-and-custom-serialization"></a>Serializacja podstawowych i niestandardowych  
 Serializacja można wykonać na dwa sposoby podstawowych i niestandardowych. Serializacja podstawowa używa programu .NET Framework, aby automatycznie serializacji obiektu.  
  
### <a name="basic-serialization"></a>Serializacja podstawowa  
 Jedynym wymaganiem podstawowe serializacji jest, że obiekt ma <xref:System.SerializableAttribute> zastosowany. <xref:System.NonSerializedAttribute> Może służyć do uniemożliwić serializowanego określonych pól.  
  
 Gdy używasz podstawowe serializacji, przechowywanie wersji obiektów może spowodować problemy, w którym to przypadku może być korzystniejsze niestandardowej serializacji. Serializacja podstawowa jest najprostszym sposobem wykonania serializacji, ale nie zapewnia poziom kontroli nad procesem.  
  
### <a name="custom-serialization"></a>Niestandardowej serializacji  
 W niestandardowej serializacji można określić dokładnie obiekty, które będą serializowane i jak to robi. Klasa musi być oznaczona <xref:System.SerializableAttribute> i zaimplementować <xref:System.Runtime.Serialization.ISerializable> interfejsu.  
  
 Jeśli chcesz, aby obiekt mógł zostać przeprowadzona w niestandardowy sposób także, należy użyć konstruktora niestandardowego.  
  
## <a name="designer-serialization"></a>Serializacja projektanta  
 Serializacja projektanta jest specjalną forma serializacji, która obejmuje typ trwałości obiektu zwykle skojarzone z narzędziami programistycznymi. Serializacja projektanta jest procesem konwertowania wykresu obiektu do pliku źródłowego, który później może służyć do odzyskania wykresu obiektu. Plik źródłowy może zawierać kod, znaczników lub nawet informacji o tabeli SQL.  
  
## <a name="BKMK_RelatedTopics"></a> Tematy pokrewne i przykłady  
 [Przewodnik: Przechowywanie obiektu w programie Visual Studio (Visual Basic)](../../../../visual-basic/programming-guide/concepts/serialization/walkthrough-persisting-an-object-in-visual-studio.md)  
 Pokazuje, jak serializacji może służyć do utrwalenia danych obiektu między wystąpieniami, co pozwala na przechowywanie wartości i pobierać je podczas następnego, które jest tworzone wystąpienie obiektu.  
  
 [Instrukcje: Odczytywanie danych o obiektach z pliku XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/serialization/how-to-read-object-data-from-an-xml-file.md)  
 Pokazuje, jak odczytywanie danych o obiektach, które zostały wcześniej zapisane do pliku XML przy użyciu <xref:System.Xml.Serialization.XmlSerializer> klasy.  
  
 [Instrukcje: Zapisywania obiektów danych do pliku XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/serialization/how-to-write-object-data-to-an-xml-file.md)  
 Przedstawia sposób zapisania obiektu z klasy do pliku XML przy użyciu <xref:System.Xml.Serialization.XmlSerializer> klasy.
