---
title: Serializacja (C#)
ms.date: 01/02/2020
ms.openlocfilehash: 1d2bda9022b7e43744dd8a0286eff88914cf65a3
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/03/2020
ms.locfileid: "75635733"
---
# <a name="serialization-c"></a>Serializacja (C#)

Serializacja jest procesem konwertowania obiektu do strumienia bajtów w celu przechowywania obiektu lub przesyłania go do pamięci, bazy danych lub pliku. Jego głównym celem jest zapisanie stanu obiektu, aby można było go odtworzyć w razie potrzeby. Proces odwrotny nazywa się deserializacji.

## <a name="how-serialization-works"></a>Jak działa Serializacja

Na tej ilustracji przedstawiono ogólny proces serializacji:

![Grafika serializacji](./media/index/serialization-process.gif)

Obiekt jest serializowany do strumienia, który przenosi dane. Strumień może również zawierać informacje o typie obiektu, takie jak jego wersja, kultura i nazwa zestawu. Z tego strumienia obiekt może być przechowywany w bazie danych, pliku lub pamięci.

### <a name="uses-for-serialization"></a>Używa do serializacji

Serializacja umożliwia deweloperowi zapisanie stanu obiektu i ponowne utworzenie go w razie potrzeby, zapewniając przechowywanie obiektów oraz wymianę danych. Dzięki serializacji programista może wykonywać takie działania, jak:

* Wysyłanie obiektu do aplikacji zdalnej przy użyciu usługi sieci Web
* Przekazywanie obiektu z jednej domeny do innej
* Przekazywanie obiektu przez zaporę jako ciąg JSON lub XML
* Utrzymywanie zabezpieczeń lub informacji specyficznych dla użytkownika w aplikacjach

## <a name="json-serialization"></a>Serializacja JSON

Przestrzeń nazw <xref:System.Text.Json> zawiera klasy dla serializacji JavaScript Object Notation (JSON) i deserializacji. JSON to otwarty standard, który jest często używany do udostępniania danych w sieci Web.

Serializacja JSON serializacji właściwości publicznych obiektu do ciągu, tablicy bajtów lub strumienia zgodnego ze [specyfikacją JSON RFC 8259](https://tools.ietf.org/html/rfc8259). Aby kontrolować sposób <xref:System.Text.Json.JsonSerializer> serializacji lub deserializacji wystąpienia klasy:

* Używanie obiektu <xref:System.Text.Json.JsonSerializerOptions>
* Zastosuj atrybuty z przestrzeni nazw <xref:System.Text.Json.Serialization> do klas lub właściwości
* [Implementowanie konwerterów niestandardowych](../../../../standard/serialization/system-text-json-converters-how-to.md)

## <a name="binary-and-xml-serialization"></a>Serializacja binarna i XML

Przestrzeń nazw <xref:System.Runtime.Serialization> zawiera klasy dla serializacji binarnej i kodu XML oraz deserializacji.

Serializacja binarna korzysta z kodowania binarnego w celu utworzenia kompaktowej serializacji do użycia, takich jak magazyn lub strumienie sieciowe oparte na gnieździe. W serializacji binarnej wszystkie elementy członkowskie, nawet elementy członkowskie, które są tylko do odczytu, są serializowane i zwiększają wydajność. 

Serializacji XML serializować pola publiczne i właściwości obiektu, lub parametry i wartości zwracane metod do strumienia XML, który jest zgodny z konkretnym dokumentem języka definicji schematu XML (XSD). Serializacja XML skutkuje silnie określonymi klasami z właściwościami publicznymi i polami, które są konwertowane na format XML. <xref:System.Xml.Serialization> zawiera klasy do serializacji i deserializacji XML. Należy zastosować atrybuty do klas i elementów członkowskich klasy, aby kontrolować sposób, w jaki <xref:System.Xml.Serialization.XmlSerializer> serializować lub deserializacji wystąpienia klasy.

### <a name="making-an-object-serializable"></a>Tworzenie obiektu jako możliwego do serializacji

W przypadku serializacji binarnej lub XML potrzebne są:

* Obiekt, który ma zostać Zserializowany
* Strumień zawierający serializowany obiekt
* Wystąpienie <xref:System.Runtime.Serialization.Formatter?displayProperty=fullName>

Zastosuj atrybut <xref:System.SerializableAttribute> do typu, aby wskazać, że wystąpienia typu mogą być serializowane. Wyjątek jest zgłaszany w przypadku próby serializacji, ale typ nie ma atrybutu <xref:System.SerializableAttribute>.

Aby zapobiec serializowaniu pola, zastosuj atrybut <xref:System.NonSerializedAttribute>. Jeśli pole o typie możliwym do serializacji zawiera wskaźnik, uchwyt lub inną strukturę danych, która jest specyficzna dla określonego środowiska, a pole nie może być w znaczący sposób odtworzone w innym środowisku, można sprawić, aby nie można było jej serializować.

Jeśli serializowana Klasa zawiera odwołania do obiektów innych klas, które są oznaczone <xref:System.SerializableAttribute>, te obiekty również będą serializowane.

### <a name="basic-and-custom-serialization"></a>Serializacja podstawowa i niestandardowa

Serializacja binarna i XML może być wykonywana na dwa sposoby — podstawowa i niestandardowa.

Serializacja podstawowa używa .NET Framework do automatycznego serializacji obiektu. Jedyny wymóg polega na tym, że Klasa ma zastosowany atrybut <xref:System.SerializableAttribute>. <xref:System.NonSerializedAttribute> może służyć do zachowywania serializacji określonych pól.

W przypadku korzystania z serializacji podstawowej wersja obiektów może tworzyć problemy. Podczas rozwiązywania problemów dotyczących wersji należy użyć serializacji niestandardowej. Serializacja podstawowa jest najprostszym sposobem na wykonywanie serializacji, ale nie zapewnia większej kontroli nad procesem.

W przypadku serializacji niestandardowej można określić, które obiekty będą serializowane i jak będą wykonywane. Klasa musi być oznaczona <xref:System.SerializableAttribute> i implementować interfejs <xref:System.Runtime.Serialization.ISerializable>. Jeśli chcesz, aby obiekt był deserializowany w sposób niestandardowy, użyj konstruktora niestandardowego.

## <a name="designer-serialization"></a>Serializacja projektanta

Serializacja projektanta jest specjalną formą serializacji, która obejmuje rodzaj trwałości obiektu skojarzony z narzędziami programistycznymi. Serializacja projektanta to proces przekonwertowania grafu obiektów na plik źródłowy, który można później użyć do odzyskania grafu obiektów. Plik źródłowy może zawierać kod, znacznik, a nawet informacje tabeli SQL.

## <a name="BKMK_RelatedTopics"></a>Tematy pokrewne i przykłady  

[System. Text. JSON — Omówienie](../../../../standard/serialization/system-text-json-overview.md) Pokazuje, jak uzyskać bibliotekę `System.Text.Json`.

[Jak serializować i deserializować kod JSON w programie .NET](../../../../standard/serialization/system-text-json-how-to.md). Pokazuje, jak odczytywać i zapisywać dane obiektów do i z JSON przy użyciu klasy <xref:System.Text.Json.JsonSerializer>.

[Przewodnik: utrwalanie obiektu w programie Visual Studio (C#)](walkthrough-persisting-an-object-in-visual-studio.md)  
Pokazuje, jak Serializacja może być używana do utrwalania danych obiektu między wystąpieniami, umożliwiając przechowywanie wartości i pobieranie ich przy następnym tworzeniu wystąpienia obiektu.

[Jak odczytać dane obiektu z pliku XML (C#)](how-to-read-object-data-from-an-xml-file.md)  
Pokazuje, jak odczytywać dane obiektów, które zostały wcześniej zapisaną w pliku XML przy użyciu klasy <xref:System.Xml.Serialization.XmlSerializer>.

[Jak napisać dane obiektu do pliku XML (C#)](how-to-write-object-data-to-an-xml-file.md)  
Pokazuje, jak napisać obiekt z klasy do pliku XML przy użyciu klasy <xref:System.Xml.Serialization.XmlSerializer>.
