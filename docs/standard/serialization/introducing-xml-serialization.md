---
title: Szczegóły serializacji XML
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- XML serialization, about XML serialization
- ICollection interface, serializing
- XmlSerializer class, serializing
- serialization, about serialization
- DataSet class, serializing
- XML Schema, serializing
ms.assetid: 8c63200d-db63-4a03-a93d-21641623df62
ms.openlocfilehash: d644e80cbf5ac17fca4df039d915c847a1936217
ms.sourcegitcommit: 961ec21c22d2f1d55c9cc8a7edf2ade1d1fd92e3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2020
ms.locfileid: "80588454"
---
# <a name="xml-serialization"></a>Serializacja XML

Serializacji to proces konwersji obiektu do formularza, który można łatwo przesłać. Na przykład można serializować obiekt i transportować go przez Internet przy użyciu protokołu HTTP między klientem a serwerem. Z drugiej deserializacji rekonstruuje obiektów ze strumienia.

 Wykonuje serializacji XML serializację tylko publiczny pól i wartości właściwości obiektu do strumienia XML. Serializacji XML nie zawiera informacji o typie. Na przykład jeśli masz **Book** obiektu, który istnieje w obszarze nazw **biblioteki,** nie ma gwarancji, że jest deserializowane do obiektu tego samego typu.

> [!NOTE]
> Serializacji XML nie konwertuje metody, indeksatory, prywatnych pola lub właściwości tylko do odczytu (z wyjątkiem kolekcji tylko do odczytu). Do serializacji obiektu wszystkie pola i właściwości, zarówno publiczne, jak i prywatnych, użyj <xref:System.Runtime.Serialization.DataContractSerializer> zamiast serializacji XML.

 Klasa centralna w serializacji <xref:System.Xml.Serialization.XmlSerializer> XML jest klasą, a najważniejsze metody w tej klasie to **Metody Serialize** i **Deserialize.** <xref:System.Xml.Serialization.XmlSerializer> Tworzy PLiki C# i kompiluje je na PLiki z rozszerzeniem dll do wykonania tej serializacji. W .NET Framework 2.0 [narzędzie generatora serializatora XML (Sgen.exe)](xml-serializer-generator-tool-sgen-exe.md) jest przeznaczone do generowania tych zestawów serializacji z wyprzedzeniem, które mają zostać wdrożone za pomocą aplikacji i zwiększyć wydajność uruchamiania. Strumień XML generowany przez **XmlSerializer** jest zgodny z zaleceniem języka XML 1.0 programu World Wide Web Consortium (W3C) [XML Schema definition language (XSD).](https://www.w3.org/TR/xslt) Ponadto wygenerowane typy danych są zgodne z dokumentem zatytułowanym "XML Schema Część 2: Typy danych".

 Dane w obiektach są opisane przy użyciu konstrukcji języka programowania, takich jak klasy, pola, właściwości, typy pierwotne, tablice, a nawet osadzone XML w postaci **XmlElement** lub **XmlAttribute** obiektów. Istnieje możliwość tworzenia własnych klas oznaczona z atrybutów, lub za pomocą narzędzia definicji schematu XML można wygenerować klas na podstawie istniejącego schematu XML.

 Jeśli masz schematu XML, należy uruchomić narzędzie definicji schematu XML do tworzenia zestaw klasy, które są silnie wpisany schematu i dodawać adnotacje z atrybutami. W przypadku wystąpienia takich klasy jest serializowana, wygenerowany kod XML jest zgodna schematu XML. Zamieszczone w przypadku klasy, można programować względem model obiektów łatwo manipulować spełniającą pewność, że wygenerowany kod XML jest zgodny ze schematem XML. Jest to alternatywa dla korzystania z innych klas w .NET Framework, takich jak **XmlReader** i **XmlWriter** klasy, do analizowania i zapisu strumienia XML. Aby uzyskać więcej informacji, zobacz [Dokumenty i dane XML](../../../docs/standard/data/xml/index.md). Klasy te umożliwiają przeanalizować strumieniem XML. Natomiast należy użyć **XmlSerializer,** gdy oczekuje się, że strumień XML będzie zgodny ze znanym schematem XML.

 Atrybuty kontrolują strumień XML generowany przez klasę **XmlSerializer,** umożliwiając ustawienie obszaru nazw XML, nazwy elementu, nazwy atrybutu i tak dalej strumienia XML. Aby uzyskać więcej informacji na temat tych atrybutów i sposobu kontrolowania serializacji XML, zobacz [Kontrolowanie serializacji XML przy użyciu atrybutów](controlling-xml-serialization-using-attributes.md). Aby uzyskać tabelę tych atrybutów, które są używane do kontrolowania wygenerowanego kodu XML, zobacz [Atrybuty, które kontrolują serializację XML](attributes-that-control-xml-serialization.md).

 Klasa **XmlSerializer** może dodatkowo serializować obiekt i generować zakodowany strumień XML protokołu SOAP. Wygenerowany kod XML jest zgodny z sekcją 5 dokumentu Konsorcjum sieci World Wide Web zatytułowanego "Simple Object Access Protocol (SOAP) 1.1". Aby uzyskać więcej informacji na temat tego procesu, zobacz [Jak: Serializować obiekt jako strumień XML zakodowany w formacie SOAP](how-to-serialize-an-object-as-a-soap-encoded-xml-stream.md). Aby zapoznać się z tabelą atrybutów sterujących wygenerowanym kodem XML, zobacz [Atrybuty sterujące zakodowaną serionizacją protokołu SOAP](attributes-that-control-encoded-soap-serialization.md).

 Klasa **XmlSerializer** generuje komunikaty SOAP utworzone przez i przekazane do usług sieci Web XML. Aby sterować komunikatami PROTOKOŁU SOAP, można zastosować atrybuty do klas, zwracać wartości, parametry i pola znajdujące się w pliku usługi sieci Web XML (asmx). Można użyć atrybuty wymienione w "Serializacji XML atrybuty czy kontroli" i "Atrybuty czy kontroli kodowany protokołu SOAP serializacji", ponieważ usługi XML sieci Web mogą korzystać styl literału lub zakodowanego protokołu SOAP. Aby uzyskać więcej informacji na temat używania atrybutów do kontrolowania kodu XML generowanego przez usługę sieci Web XML, zobacz [Serializacja XML za pomocą usług XML w sieci Web](xml-serialization-with-xml-web-services.md). Aby uzyskać więcej informacji na temat usług sieci Web PROTOKOŁU SOAP i XML, zobacz [Dostosowywanie formatowania wiadomości PROTOKOŁU SOAP](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dkwy2d72(v=vs.100)).

## <a name="security-considerations-for-xmlserializer-applications"></a>Zagadnienia dotyczące zabezpieczeń dla aplikacji XmlSerializer

Podczas tworzenia aplikacji, która używa **XmlSerializer**, należy pamiętać o następujących elementów i ich implikacje:

- **XmlSerializer** tworzy pliki C# (cs) i kompiluje je do plików dll w katalogu nazwanym przez zmienną środowiska TEMP; serializacji występuje z tymi bibliotekami DLL.

  > [!NOTE]
  > Te zestawy serializacji można wygenerowane z góry i podpisane za pomocą narzędzia SGen.exe. Nie działa serwer usług sieci Web. Innymi słowy jest tylko do użytku klienta i ręczne serializacji.

  Kod i biblioteki DLL są podatne na złośliwego procesu w czasie tworzenia i kompilacji. Podczas używania na komputerze z systemem Microsoft Windows NT 4.0 lub nowszy, może być możliwe dla co najmniej dwa użytkownikom udostępnianie katalogu TEMP. Udostępnianie katalogu TEMP jest niebezpieczne, jeśli dwa konta mają różne uprawnienia zabezpieczeń, a konto o wyższych uprawnieniach uruchamia aplikację za pomocą **XmlSerializer**. W takim przypadku jeden użytkownik może naruszyć bezpieczeństwo komputera, zastępując skompilowany plik cs lub .dll. Aby usunąć ten problem, zawsze upewnij się, że każde konto na komputerze ma własny profil. Domyślnie zmienna środowiskowa TEMP wskazuje inny folder dla każdego konta.

- Jeśli złośliwy użytkownik wysyła ciągły strumień danych XML do serwera sieci Web (atak typu "odmowa usługi"), **xmlSerializer** kontynuuje przetwarzanie danych, dopóki na komputerze nie zabraknie zasobów.

  Ten rodzaj ataku jest eliminowany, jeśli używasz komputera z uruchomionymi internetowymi usługami informacyjnymi (IIS), a aplikacja jest uruchomiona w usługach IIS. Program IIS zawiera bramę, która nie może przetwarzać strumieni dłużej niż pewną liczbę (wartość domyślna to 4 KB). Jeśli tworzysz aplikację, która nie używa usług IIS i deserializes z **XmlSerializer**, należy zaimplementować podobną bramę, która zapobiega atak typu "odmowa usługi".

- **XmlSerializer** serializuje dane i uruchamia dowolny kod przy użyciu dowolnego typu podane do niego.

  Istnieją dwie metody, w których obiekt złośliwego przedstawia zagrożenia. Może uruchomić złośliwy kod lub może wstrzyknąć złośliwy kod do pliku C# utworzonego przez **XmlSerializer**. W przypadku pierwszego Jeśli obiekt złośliwego próbuje uruchomić destrukcyjne procedurę, zabezpieczenia dostępu do kodu uniemożliwia szkody wykonywana. W drugim przypadku istnieje teoretyczna możliwość, że złośliwy obiekt może w jakiś sposób wstrzyknąć kod do pliku C# utworzonego przez **XmlSerializer**. Mimo że ten problem zbadaniu dokładnie i takiego ataku jest uznawany za mało prawdopodobne, należy podjąć środki ostrożności nigdy nie szeregowania danych o typie nieznany i niezaufane.

- Zserializowany poufnych danych może być narażony.

  Po **XmlSerializer** ma szeregowane dane, mogą być przechowywane jako plik XML lub innego magazynu danych. Sklepu danych jest dostępna dla innych procesów, czy jest widoczny w intranecie lub w Internecie, dane mogą skradziony i użyty w sposób złośliwy. Na przykład jeśli utworzysz aplikację, która serializuje zamówienia, które zawierają numery kart kredytowych, dane są bardzo poufne. Aby zapobiec, zawsze ochrony magazynu danych i wykonać kroki, aby utrzymać ją prywatnych.

## <a name="serialization-of-a-simple-class"></a>Serializacja klasy prostej

Poniższy przykład kodu przedstawia klasę podstawową z polem publicznym.

```vb
Public Class OrderForm
    Public OrderDate As DateTime
End Class
```

```csharp
public class OrderForm
{
    public DateTime OrderDate;
}
```

W przypadku wystąpienia tej klasy jest serializowana, jego może wyglądać w następujący sposób.

```xml
<OrderForm>
    <OrderDate>12/12/01</OrderDate>
</OrderForm>
```

Aby uzyskać więcej przykładów serializacji, zobacz [Przykłady serializacji XML](examples-of-xml-serialization.md).

## <a name="items-that-can-be-serialized"></a>Elementy, które można wykonywać serializację

Następujące elementy mogą być serializowane przy użyciu **XmLSerializer** klasy:

- Właściwości publiczne odczytu/zapisu i pola publiczne klas.

- Klasy, które implementują **ICollection** lub **IEnumerable**.

  > [!NOTE]
  > Tylko kolekcje są serializacji, nie publiczny właściwości.

- **XmlElement** obiektów.

- **XmlNode** obiektów.

- **Obiekty Zestawu danych.**

 Aby uzyskać więcej informacji na temat serializacji lub deserializacji obiektów, zobacz [Jak: Serialize obiektu](how-to-serialize-an-object.md) i [jak: Deserialize obiektu](how-to-deserialize-an-object.md).

## <a name="advantages-of-using-xml-serialization"></a>Korzyści wynikające z używania serializacji XML

Klasa **XmlSerializer** zapewnia pełną i elastyczną kontrolę podczas serializacji obiektu jako XML. W przypadku tworzenia usługi sieci Web XML można zastosować atrybuty sterujące serializacją klas i elementów członkowskich, aby upewnić się, że dane wyjściowe XML są zgodne z określonym schematem.

Na przykład **XmlSerializer** umożliwia:

- Określ, czy pole lub właściwość powinien być kodowany jako atrybut lub element.

- Określ przestrzeni nazw XML do użycia.

- Określ nazwę elementu lub atrybutu, jeśli nazwa pola lub właściwości jest nieodpowiedni.

Inną zaletą serializacji XML jest to, że nie masz żadnych ograniczeń w aplikacji, które opracowywać, tak długo, jak strumień XML, który jest generowany jest zgodny z danym schematem. Wyobraź sobie schematu, używany do opisania książki. Zawiera funkcje tytuł, autor, Wydawca i ISBN numer elementu. Można opracować aplikację, która przetwarza dane XML w dowolny sposób, na przykład jako zamówienie księgowe lub jako spis książek. W obu przypadkach jedynym wymaganiem jest, czy strumień XML jest zgodny ze schematem określonego języka (XSD) definicji schematu XML.

## <a name="xml-serialization-considerations"></a>Uwagi dotyczące serializacji XML

Podczas korzystania z klasy **XmlSerializer** należy wziąć pod uwagę następujące kwestie:

- Narzędzie Sgen.exe wyraźnie jest przeznaczona do generowania zestawów serializacji w celu uzyskania optymalnej wydajności.

- Serializowane dane zawiera tylko danych i struktury klas. Informacje o tożsamości i zestawu typu nie są uwzględniane.

- Może być Zserializowany tylko właściwości publiczne i pola. Właściwości muszą mieć publiczne metody dostępu (Pobieranie i ustawianie metody). Jeśli muszą serializację danych bez publicznego, użyj <xref:System.Runtime.Serialization.DataContractSerializer> klasy zamiast serializacji XML.

- Klasa musi mieć konstruktora bez parametrów, który ma być serializowany przez **XmlSerializer**.

- Nie można serializować metody.

- **XmlSerializer** może przetwarzać klasy, które implementują **IEnumerable** lub **ICollection** inaczej, jeśli spełniają pewne wymagania, w następujący sposób.

  Klasa, która implementuje **IEnumerable** należy zaimplementować public **Add** metody, która przyjmuje pojedynczy parametr. Parametr **Add** metody musi być spójny (polimorficzny) z typem zwróconym z **właściwości IEnumerator.Current** zwróconej z metody **GetEnumerator.**

  Klasa, która implementuje **ICollection** oprócz **IEnumerable** (takich jak **CollectionBase)** musi mieć publiczną **właściwość** indeksowane element (indeksator w języku C#), która przyjmuje liczbę całkowitą i musi mieć publiczną **właściwość Count** typu **integer**. Parametr przekazany do **Add** metody musi być tego samego typu, który zwrócił z **Item** właściwości lub jednej z podstaw tego typu.

  Dla klas, które implementują **ICollection**, wartości, które mają być serializowane są pobierane z indeksowanej właściwości **Item,** a nie przez wywołanie **GetEnumerator**. Ponadto pola publiczne i właściwości nie są serializowane, z wyjątkiem pól publicznych zwracających inną klasę kolekcji (która implementuje **ICollection**). Na przykład zobacz [Przykłady serializacji XML](examples-of-xml-serialization.md).

## <a name="xsd-data-type-mapping"></a>Mapowania typów danych XSD

Dokument W3C zatytułowany [Schemat XML Część 2: Typy danych](https://www.w3.org/TR/xmlschema-2/) określa proste typy danych, które są dozwolone w schemacie języka XM (XSD) języka schematu schematu schematu xsd. Dla wielu z nich (na przykład **int** i **decimal),** istnieje odpowiedni typ danych w .NET Framework. Jednak niektóre typy danych XML nie mają odpowiedniego typu danych w .NET Framework (na przykład typ danych **NMTOKEN).** W takich przypadkach, jeśli do generowania klas ze schematu używasz narzędzia XML Schema Definition[(XML Schema Definition Tool (Xsd.exe)](xml-schema-definition-tool-xsd-exe.md)) odpowiedni atrybut jest stosowany do elementu członkowskiego ciągu typu, a jego właściwość **DataType** jest ustawiona na nazwę typu danych XML. Na przykład jeśli schemat zawiera element o nazwie "MyToken" z typem danych XML **NMTOKEN,** wygenerowana klasa może zawierać element członkowski, jak pokazano w poniższym przykładzie.

```vb
<XmlElement(DataType:="NMTOKEN")> _
Public MyToken As String
```

```csharp
[XmlElement(DataType = "NMTOKEN")]
public string MyToken;
```

Podobnie w przypadku tworzenia klasy, która musi być zgodna z określonym schematem XML (XSD), należy zastosować odpowiedni atrybut i ustawić jego właściwość **DataType** na żądaną nazwę typu danych XML.

Aby uzyskać pełną listę mapowań typów, zobacz **Właściwość DataType** dla dowolnej z następujących klas atrybutów:

- <xref:System.Xml.Serialization.SoapAttributeAttribute>

- <xref:System.Xml.Serialization.SoapElementAttribute>

- <xref:System.Xml.Serialization.XmlArrayItemAttribute>

- <xref:System.Xml.Serialization.XmlAttributeAttribute>

- <xref:System.Xml.Serialization.XmlElementAttribute>

- <xref:System.Xml.Serialization.XmlRootAttribute>

## <a name="see-also"></a>Zobacz też

- <xref:System.Xml.Serialization.XmlSerializer>
- <xref:System.Runtime.Serialization.DataContractSerializer>
- <xref:System.IO.FileStream>
- [Serializacja XML i SOAP](xml-and-soap-serialization.md)
- [Serializacja binarna](binary-serialization.md)
- [Serializacja](index.md)
- <xref:System.Xml.Serialization.XmlSerializer>
- [Przykłady serializacji XML](examples-of-xml-serialization.md)
- [Instrukcje: Serializacja obiektu](how-to-serialize-an-object.md)
- [Instrukcje: Deserializacja obiektu](how-to-deserialize-an-object.md)
