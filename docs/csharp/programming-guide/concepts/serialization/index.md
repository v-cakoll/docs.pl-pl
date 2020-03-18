---
title: Serializacja (C#)
ms.date: 01/02/2020
ms.openlocfilehash: d914298a370b09307e84c88959542b4823cf37ce
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "79167598"
---
# <a name="serialization-c"></a>Serializacja (C#)

Serializacja to proces konwertowania obiektu na strumień bajtów w celu przechowywania obiektu lub przesyłania go do pamięci, bazy danych lub pliku. Jego głównym celem jest zapisanie stanu obiektu, aby móc go odtworzyć w razie potrzeby. Proces odwrotny nazywa się deserializacją.

## <a name="how-serialization-works"></a>Jak działa serializacja

Na tej ilustracji przedstawiono ogólny proces serializacji:

![Grafika serializacji](./media/index/serialization-process.gif)

Obiekt jest serializowany do strumienia, który przenosi dane. Strumień może również mieć informacje o typie obiektu, takie jak jego wersja, kultura i nazwa zestawu. Z tego strumienia obiekt może być przechowywany w bazie danych, pliku lub pamięci.

### <a name="uses-for-serialization"></a>Zastosowania serializacji

Serializacja umożliwia deweloperowi zapisanie stanu obiektu i ponowne utworzenie go w razie potrzeby, zapewniając przechowywanie obiektów, a także wymianę danych. Dzięki serializacji deweloper może wykonywać akcje, takie jak:

* Wysyłanie obiektu do aplikacji zdalnej przy użyciu usługi sieci web
* Przekazywanie obiektu z jednej domeny do drugiej
* Przekazywanie obiektu przez zaporę jako ciąg JSON lub XML
* Obsługa zabezpieczeń lub informacji specyficznych dla użytkownika w aplikacjach

## <a name="json-serialization"></a>Serializacja JSON

Obszar <xref:System.Text.Json> nazw zawiera klasy serializacji i deserializacji notacji obiektów JavaScript (JSON). JSON to otwarty standard, który jest powszechnie używany do udostępniania danych w internecie.

Serializacja JSON serializuje właściwości publiczne obiektu w ciągu, tablicy bajtów lub strumienia, który jest zgodny ze [specyfikacją RFC 8259 JSON](https://tools.ietf.org/html/rfc8259). Aby kontrolować <xref:System.Text.Json.JsonSerializer> sposób serializacji lub deserializacji wystąpienia klasy:

* Używanie <xref:System.Text.Json.JsonSerializerOptions> obiektu
* Stosowanie atrybutów <xref:System.Text.Json.Serialization> z obszaru nazw do klas lub właściwości
* [Implementowanie konwerterów niestandardowych](../../../../standard/serialization/system-text-json-converters-how-to.md)

## <a name="binary-and-xml-serialization"></a>Serializacja binarna i XML

Obszar <xref:System.Runtime.Serialization> nazw zawiera klasy serializacji binarnej i XML oraz deserializacji.

Serializacja binarna używa kodowania binarnego do tworzenia kompaktowej serializacji dla zastosowań, takich jak strumienie sieciowe oparte na pamięci masowej lub gniazdach. W serializacji binarnej wszystkie elementy członkowskie, nawet elementy członkowskie, które są tylko do odczytu, są serializowane, a wydajność jest zwiększona.

Serializacja XML serializuje pola publiczne i właściwości obiektu lub parametry i zwracane wartości metod w strumieniu XML zgodnym z dokumentem języka xsd (określonego języka definicji schematu XML). Serializacja XML powoduje, że klasy silnie typizowane z właściwościami publicznymi i polami są konwertowane na XML. <xref:System.Xml.Serialization>zawiera klasy serializacji i deserializacji XML. Atrybuty stosuje się do klas i członków <xref:System.Xml.Serialization.XmlSerializer> klasy, aby kontrolować sposób serializacji lub deserializacji wystąpienia klasy.

### <a name="making-an-object-serializable"></a>Możliwość serializacji obiektu

Do serializacji binarnej lub XML potrzebne są:

* Obiekt, który ma być serializowany
* Strumień zawierający obiekt serializowany
* Wystąpienie <xref:System.Runtime.Serialization.Formatter?displayProperty=fullName>

Zastosuj <xref:System.SerializableAttribute> atrybut do typu, aby wskazać, że wystąpienia typu mogą być serializowane. Wyjątek jest generowany, jeśli spróbujesz serializować, ale <xref:System.SerializableAttribute> typ nie ma atrybutu.

Aby zapobiec serializacji pola, <xref:System.NonSerializedAttribute> należy zastosować ten atrybut. Jeśli pole typu serializable zawiera wskaźnik, dojście lub inną strukturę danych, która jest specyficzna dla określonego środowiska, a pole nie może być sensownie odtworzone w innym środowisku, można go uczynić nieserializable.

Jeśli serializowana klasa zawiera odwołania do <xref:System.SerializableAttribute>obiektów innych klas, które są oznaczone, obiekty te będą również serializowane.

### <a name="basic-and-custom-serialization"></a>Serializacja podstawowa i dostosowana do indywidualnych potrzeb

Serializacja binarna i XML może być wykonywana na dwa sposoby, podstawowe i niestandardowe.

Serializacja podstawowa używa programu .NET Framework do automatycznego serializacji obiektu. Jedynym wymaganiem jest, <xref:System.SerializableAttribute> że klasa ma zastosowany atrybut. Może <xref:System.NonSerializedAttribute> służyć do zachowania określonych pól z serializacji.

Korzystając z seryjnej podstawowej, przechowywanie wersji obiektów może powodować problemy. Serializacji niestandardowej można użyć, gdy ważne są problemy z przechowywaniem wersji. Serializacja podstawowa jest najprostszym sposobem wykonywania serializacji, ale nie zapewnia dużej kontroli nad procesem.

W serializacji niestandardowej można dokładnie określić, które obiekty będą serializowane i jak to będzie zrobione. Klasa musi być <xref:System.SerializableAttribute> oznaczona i zaimplementować <xref:System.Runtime.Serialization.ISerializable> interfejs. Jeśli chcesz, aby obiekt został deserializowany w niestandardowy sposób, należy użyć niestandardowego konstruktora.

## <a name="designer-serialization"></a>Serializacja projektanta

Serializacja projektanta jest specjalną formą serializacji, która obejmuje rodzaj trwałości obiektu skojarzonego z narzędziami programistycznymi. Serializacja projektanta to proces konwertowania wykresu obiektu na plik źródłowy, który może później służyć do odzyskiwania wykresu obiektu. Plik źródłowy może zawierać informacje o kodzie, znacznikach, a nawet tabeli SQL.

## <a name="BKMK_RelatedTopics"></a>Pokrewne tematy i przykłady  

[Przegląd System.Text.Json](../../../../standard/serialization/system-text-json-overview.md) Pokazuje, jak `System.Text.Json` uzyskać biblioteki.

[Jak serializować i deserializować JSON w .NET](../../../../standard/serialization/system-text-json-how-to.md).
Pokazuje, jak odczytywać i zapisywać dane obiektów <xref:System.Text.Json.JsonSerializer> do i z JSON przy użyciu klasy.

[Instruktaż: Utrwalanie obiektu w programie Visual Studio (C#)](walkthrough-persisting-an-object-in-visual-studio.md)  
Pokazuje, jak serializacji może służyć do utrwalania danych obiektu między wystąpieniami, co pozwala na przechowywanie wartości i pobrać je przy następnym wystąpieniu obiektu.

[Jak odczytywać dane obiektu z pliku XML (C#)](how-to-read-object-data-from-an-xml-file.md)  
Pokazuje, jak odczytywać dane obiektów, które zostały <xref:System.Xml.Serialization.XmlSerializer> wcześniej zapisane w pliku XML przy użyciu klasy.

[Jak zapisywać dane obiektu do pliku XML (C#)](how-to-write-object-data-to-an-xml-file.md)  
Pokazuje, jak zapisać obiekt z klasy do pliku <xref:System.Xml.Serialization.XmlSerializer> XML przy użyciu klasy.
