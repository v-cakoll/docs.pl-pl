---
title: Serializacja (C#)
ms.date: 04/26/2018
ms.openlocfilehash: 03a7cd2d48b79d94674e64e96130e20a86051fb2
ms.sourcegitcommit: 88f251b08bf0718ce119f3d7302f514b74895038
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/10/2018
---
# <a name="serialization-c"></a>Serializacja (C#)

Serializacja jest proces konwersji obiektu do strumienia bajtów do przechowywania obiektu lub przekazuje je do pamięci, bazą danych lub pliku. Głównym celem jest zapisanie stanu obiektu, aby można było utworzyć ją w razie potrzeby ponownie. Odwrotnej proces jest nazywany deserializacji.

## <a name="how-serialization-works"></a>Jak działa serializacji

Ta ilustracja przedstawia proces serializacji.

![Grafika przedstawiająca serializację](./media/serialization.gif "szeregowanie")

Strumień, który niesie nie tylko dane, ale informacje o typie obiektu, takie jak jego nazwa wersji, kultury i zestawu serializowany jest obiekt. W strumieniu mogą być przechowywane w bazie danych, plik lub pamięci.

### <a name="uses-for-serialization"></a>Używa do serializacji

Serializacja umożliwia deweloperowi zapisanie stanu obiektu i utwórz go ponownie zgodnie z potrzebami, przeznaczone do przechowywania obiektów, jak również wymiany danych. Za pomocą serializacji, deweloper można wykonać akcji, takich jak wysyłanie obiektu do aplikacji zdalnej przy użyciu usługi sieci Web, przekazanie obiektu z jednej domeny do innej, przekazywanie przez zaporę obiektu jako ciąg XML lub zabezpieczenie lub informacje specyficzne dla użytkownika w aplikacjach.

### <a name="making-an-object-serializable"></a>Wprowadzenie do serializacji obiektu

Szeregowania obiektu, należy na można zserializować obiektu strumienia zawiera Zserializowany obiekt oraz a <xref:System.Runtime.Serialization.Formatter>. <xref:System.Runtime.Serialization> zawiera klasy, które są niezbędne do serializacji i deserializacji obiektów.

Zastosuj <xref:System.SerializableAttribute> atrybut do typu, aby wskazać, że wystąpień tego typu może być Zserializowany. Jest zwracany wyjątek, jeśli próba serializować, ale nie ma typu <xref:System.SerializableAttribute> atrybutu.

Jeśli nie chcesz pole w klasie jako możliwy do serializacji, zastosuj <xref:System.NonSerializedAttribute> atrybutu. Jeśli pole typu umożliwiającego serializację zawiera wskaźnik, dojście lub niektóre inne struktura danych, która jest specyficzna dla danego środowiska, a pole nie może uzyskać wiarygodny odtworzenia w innym środowisku, może być dokonanie nonserializable.

Jeśli serializacji klasa zawiera odwołania do obiektów na innych klas, które są oznaczone jako <xref:System.SerializableAttribute>, również będą wykonywane szeregowo tych obiektów.

## <a name="binary-and-xml-serialization"></a>Dane binarne i serializacja XML

Można użyć pliku binarnego lub serializacji XML. W serializacji binarnej, wszystkie elementy członkowskie, nawet elementów członkowskich, które są tylko do odczytu są serializowane i zwiększa wydajność. Serializacja XML zawiera czytelność kodu i większą elastyczność użycia na współdziałanie i udostępniania obiektów.

### <a name="binary-serialization"></a>Serializacja binarna

Serializacja binarna używa kodowania binarnego do generowania compact serializacji dla zastosowań, takich jak pamięci masowej lub sieci opartych na gniazda strumieni.

### <a name="xml-serialization"></a>Serializacja XML

Serializacja XML serializuje publiczne pola i właściwości obiektu lub parametrów i zwracanych wartościach metod, w strumieniu XML, które odpowiada określonego dokumentu schematu XML definition language (XSD). Wyniki serializacji XML w silnie typizowane klas z właściwości publiczne i pola, które są konwertowane na XML. <xref:System.Xml.Serialization> zawiera klasy, które są niezbędne do serializacji i deserializacji XML.

Stosowanie atrybutów do klas i elementów członkowskich klasy, aby kontrolować sposób <xref:System.Xml.Serialization.XmlSerializer> serializuje i deserializuje wystąpienia klasy.

## <a name="basic-and-custom-serialization"></a>Serializacja podstawowych i niestandardowych

Serializacja można przeprowadzić na dwa sposoby podstawowych i niestandardowych. Podstawowe serializacji używa programu .NET Framework, aby automatycznie serializacji obiektu.

### <a name="basic-serialization"></a>Podstawowe serializacji

Jedynym wymaganiem w serializacji podstawowa jest, że obiekt ma <xref:System.SerializableAttribute> atrybut zastosowany. <xref:System.NonSerializedAttribute> Można zapobiec serializowana określonych pól.

Korzystając z podstawowych serializacji, przechowywanie wersji obiektów może spowodować problemy. Można użyć niestandardowej serializacji, gdy problemy z wersjonowaniem są ważne. Serializacja podstawowa jest najprostszym sposobem wykonania serializacji, ale nie zapewnia poziom kontroli nad procesem.

### <a name="custom-serialization"></a>Niestandardowej serializacji

W niestandardowej serializacji można określić dokładnie obiekty, które będą serializowane i jak będą wykonywane. Klasy muszą być oznaczone jako <xref:System.SerializableAttribute> i wdrożenie <xref:System.Runtime.Serialization.ISerializable> interfejsu.

Obiektu do zdeserializowania w niestandardowy sposób również, należy użyć niestandardowego konstruktora.

## <a name="designer-serialization"></a>Serializacja projektanta

Serializacja projektanta jest specjalna forma serializacji, która obejmuje rodzaj trwałość obiektów skojarzonych z narzędziami programistycznymi. Projektanta serializacji to proces konwertowania z wykresu obiektu na plik źródłowy, który później mogą być używane do odzyskania wykres obiektu. Plik źródłowy może zawierać kod, znaczników lub nawet informacji o tabeli SQL.

##  <a name="BKMK_RelatedTopics"></a> Tematy pokrewne i przykłady  
[Wskazówki: Przechowywanie obiektu w programie Visual Studio (C#)](walkthrough-persisting-an-object-in-visual-studio.md)  
Pokazuje, jak serializacji może służyć do utrwalenia danych obiektu między wystąpieniami, co umożliwia przechowywanie wartości i pobrać je przy następnym utworzeniu wystąpienia obiektu.

[Porady: odczytywanie danych o obiektach z pliku XML (C#)](how-to-read-object-data-from-an-xml-file.md)  
 Pokazuje, jak można odczytać danych obiektów, które zostały wcześniej zapisane do pliku XML przy użyciu <xref:System.Xml.Serialization.XmlSerializer> klasy.

[Porady: wpisywanie danych o obiektach do pliku XML (C#)](how-to-write-object-data-to-an-xml-file.md)  
Przedstawia sposób zapisania obiektu z klasy do pliku XML przy użyciu <xref:System.Xml.Serialization.XmlSerializer> klasy.
