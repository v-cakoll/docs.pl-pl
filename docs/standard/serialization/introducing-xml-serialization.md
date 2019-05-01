---
title: Wprowadzenie do serializacji XML
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
ms.openlocfilehash: 491819c52c5bb1e7767e41fce7e56d8f95d10286
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61933695"
---
# <a name="introducing-xml-serialization"></a>Wprowadzenie do serializacji XML

Serializacji to proces konwersji obiektu do formularza, który można łatwo przesłać. Na przykład możesz wykonać serializację obiektu i transport go w Internecie między klientem a serwerem przy użyciu protokołu HTTP. Z drugiej deserializacji rekonstruuje obiektów ze strumienia.

 Wykonuje serializacji XML serializację tylko publiczny pól i wartości właściwości obiektu do strumienia XML. Serializacji XML nie zawiera informacji o typie. Na przykład, jeśli masz **książki** obiektu, który znajduje się w **biblioteki** przestrzeni nazw, nie ma żadnej gwarancji, że jest ona przeprowadzona deserializacja obiektu tego samego typu.

> [!NOTE]
> Serializacji XML nie konwertuje metody, indeksatory, prywatnych pola lub właściwości tylko do odczytu (z wyjątkiem kolekcji tylko do odczytu). Do serializacji obiektu wszystkie pola i właściwości, zarówno publiczne, jak i prywatnych, użyj <xref:System.Runtime.Serialization.DataContractSerializer> zamiast serializacji XML.

 Klasa centralnej w serializacji XML jest <xref:System.Xml.Serialization.XmlSerializer> klasy i najważniejszych metod w tej klasie są **Serialize** i **Deserialize** metody. <xref:System.Xml.Serialization.XmlSerializer> Tworzy PLiki C# i kompiluje je na PLiki z rozszerzeniem dll do wykonania tej serializacji. W programie .NET Framework 2.0 [narzędzie generatora serializatora XML (Sgen.exe)](xml-serializer-generator-tool-sgen-exe.md) jest przeznaczona do generowania te zestawy serializacji z góry na wdrożony z aplikacją i zwiększeniu wydajności uruchamiania. Strumień XML generowanych przez **XmlSerializer** jest zgodne z konsorcjum World Wide Web (W3C) [język definicji schematu XML (XSD) 1.0 zalecenia](https://www.w3.org/TR/xslt). Ponadto generowane typy danych są zgodne z dokumentu zatytułowanej "XML schematu część 2: Typy danych."

 Dane w obiekty opisano przy użyciu narzędzi programistycznych języka, takich jak klasy, pola, właściwości, typy pierwotne, tablice i XML nawet osadzone w formie **XmlElement** lub **XmlAttribute**obiektów. Istnieje możliwość tworzenia własnych klas oznaczona z atrybutów, lub za pomocą narzędzia definicji schematu XML można wygenerować klas na podstawie istniejącego schematu XML.

 Jeśli masz schematu XML, należy uruchomić narzędzie definicji schematu XML do tworzenia zestaw klasy, które są silnie wpisany schematu i dodawać adnotacje z atrybutami. W przypadku wystąpienia takich klasy jest serializowana, wygenerowany kod XML jest zgodna schematu XML. Zamieszczone w przypadku klasy, można programować względem model obiektów łatwo manipulować spełniającą pewność, że wygenerowany kod XML jest zgodny ze schematem XML. Jest to alternatywa dla użycia innych klas .NET Framework, takich jak **XmlReader** i **XmlWriter** klasy do analizy i zapisać strumień XML. Aby uzyskać więcej informacji, zobacz [dokumenty i dane XML](../../../docs/standard/data/xml/index.md). Klasy te umożliwiają przeanalizować strumieniem XML. Z kolei użyj **XmlSerializer** gdy oczekuje strumień XML zgodny ze znanych schematem XML.

 Atrybuty kontrolować strumień XML generowanych przez **XmlSerializer** klasy, co pozwala ustawić przestrzeni nazw XML, nazwa elementu, nazwa atrybutu i tak dalej strumienia XML. Aby uzyskać więcej informacji o tych atrybutów i sposobie ich kontrolować serializacji XML, zobacz [kontrolowanie atrybutów za pomocą serializacji XML](controlling-xml-serialization-using-attributes.md). Dla tabeli te atrybuty, które są używane do kontrolowania wygenerowany kod XML, zobacz [atrybutów, sterowania serializacji XML](attributes-that-control-xml-serialization.md).

 **XmlSerializer** klasy dalsze można serializować obiektu i generowanie zakodowany strumień XML protokołu SOAP. Wygenerowany kod XML jest zgodna z części 5 dokumentu World Wide Web Consortium "Simple Object Access Protocol (SOAP) 1.1." Aby uzyskać więcej informacji na temat tego procesu, zobacz [jak: Serializacja obiektu jako Stream XML kodowany w formacie protokołu SOAP](how-to-serialize-an-object-as-a-soap-encoded-xml-stream.md). Dla tabeli atrybutów kontrolujących wygenerowany kod XML, zobacz [atrybuty, kontroli kodowany protokołu SOAP serializacji](attributes-that-control-encoded-soap-serialization.md).

 **XmlSerializer** generuje komunikaty protokołu SOAP utworzone przez i przekazanych do usług XML sieci Web. Aby kontrolować komunikaty protokołu SOAP, można zastosować atrybutów do klasy, zwracanej wartości, parametry i pola znaleziony w pliku usługi sieci Web XML (.asmx). Można użyć atrybuty wymienione w "Serializacji XML atrybuty czy kontroli" i "Atrybuty czy kontroli kodowany protokołu SOAP serializacji", ponieważ usługi XML sieci Web mogą korzystać styl literału lub zakodowanego protokołu SOAP. Aby uzyskać więcej informacji o korzystaniu z atrybutów w celu sterowania XML generowanych przez usługi sieci Web XML, zobacz [serializacji XML przy użyciu usług XML sieci Web](xml-serialization-with-xml-web-services.md). Aby uzyskać więcej informacji o usługach sieci Web XML i protokołu SOAP, zobacz [Dostosowywanie formatowania komunikatu protokołu SOAP](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dkwy2d72(v=vs.100)).

## <a name="security-considerations-for-xmlserializer-applications"></a>Zagadnienia dotyczące aplikacji XmlSerializer zabezpieczeń

Podczas tworzenia aplikacji, która używa **XmlSerializer**, należy pamiętać o następujących elementów i ich skutki:

- **XmlSerializer** tworzy C# (CS), pliki i kompiluje je na pliki .dll w katalogu o nazwie określonej przez zmienną środowiskową TEMP; serializacja występuje z tych bibliotek DLL.

  > [!NOTE]
  > Te zestawy serializacji można wygenerowane z góry i podpisane za pomocą narzędzia SGen.exe. Nie działa serwer usług sieci Web. Innymi słowy jest tylko do użytku klienta i ręczne serializacji.

  Kod i biblioteki DLL są podatne na złośliwego procesu w czasie tworzenia i kompilacji. Podczas używania na komputerze z systemem Microsoft Windows NT 4.0 lub nowszy, może być możliwe dla co najmniej dwa użytkownikom udostępnianie katalogu TEMP. Udostępnianie katalogu TEMP jest niebezpieczne, jeśli dwa konta z uprawnieniami zabezpieczeń, a konto wyższych uprawnień uruchamia aplikacji za pomocą **XmlSerializer**. W tym przypadku jeden użytkownik może naruszenia zabezpieczeń komputera za pomocą zastąpienia pliku CS lub .dll, który jest kompilowany. Aby usunąć ten problem, zawsze upewnij się, że każde konto na komputerze ma własny profil. Domyślnie zmienna środowiskowa TEMP wskazuje inny folder dla każdego konta.

- Jeśli złośliwy użytkownik wysyła ciągłego strumienia danych XML do serwera sieci Web ("odmowa usługi"), a następnie **XmlSerializer** kontynuuje przetwarzanie danych, dopóki komputer jest za mało zasobów.

  Ten rodzaj ataku jest usunięte, jeśli używasz komputera z systemem Internet Information Services (IIS), a aplikacja jest uruchomiona w ramach usług IIS. Program IIS zawiera bramę, która nie może przetwarzać strumieni dłużej niż pewną liczbę (wartość domyślna to 4 KB). Jeśli utworzysz aplikację, która korzysta z usług IIS i deserializuje z **XmlSerializer**, należy zaimplementować podobne bramę, która blokuje typu "odmowa usługi".

- **XmlSerializer** serializuje dane i uruchamia żadnego kodu przy użyciu dowolnego typu do niego.

  Istnieją dwie metody, w których obiekt złośliwego przedstawia zagrożenia. Można go uruchomić złośliwego kodu lub jego można wstawić złośliwego kodu do pliku języka C# utworzone przez **XmlSerializer**. W przypadku pierwszego Jeśli obiekt złośliwego próbuje uruchomić destrukcyjne procedurę, zabezpieczenia dostępu do kodu uniemożliwia szkody wykonywana. W drugim przypadku jest teoretyczna możliwość, że obiekt złośliwego jakiś sposób może wstawić kod do pliku języka C# utworzone przez **XmlSerializer**. Mimo że ten problem zbadaniu dokładnie i takiego ataku jest uznawany za mało prawdopodobne, należy podjąć środki ostrożności nigdy nie szeregowania danych o typie nieznany i niezaufane.

- Zserializowany poufnych danych może być narażony.

  Po **XmlSerializer** ma danych serializowanych na fragmenty, mogą być przechowywane jako plik XML lub w innym magazynie danych. Sklepu danych jest dostępna dla innych procesów, czy jest widoczny w intranecie lub w Internecie, dane mogą skradziony i użyty w sposób złośliwy. Na przykład, jeśli tworzysz aplikację serializujący zamówienia zawierające numerów kart kredytowych, dane są bardzo ważne. Aby zapobiec, zawsze ochrony magazynu danych i wykonać kroki, aby utrzymać ją prywatnych.

## <a name="serialization-of-a-simple-class"></a>Serializacja prostą klasę

Poniższy przykład kodu pokazuje podstawowe klasy z polem publiczne.

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

Aby uzyskać więcej przykładów serializacji, zobacz [przykłady serializacji XML](examples-of-xml-serialization.md).

## <a name="items-that-can-be-serialized"></a>Elementy, które można wykonywać serializację

Następujące elementy mogą być Zserializowany za pomocą **XmLSerializer** klasy:

- Właściwości publiczne odczytu/zapisu i pola publiczne klas.

- Klasy, które implementują **ICollection** lub **IEnumerable**.

  > [!NOTE]
  > Tylko kolekcje są serializacji, nie publiczny właściwości.

- **XmlElement** obiektów.

- **Element XmlNode** obiektów.

- **Zestaw danych** obiektów.

 Aby uzyskać więcej informacji na temat serializacji lub deserializacji obiektów, zobacz [jak: Serializacja obiektu](how-to-serialize-an-object.md) i [jak: Deserializacji obiektu](how-to-deserialize-an-object.md).

## <a name="advantages-of-using-xml-serialization"></a>Korzyści wynikające z używania serializacji XML

**XmlSerializer** klasy daje pełny i elastyczną kontrolę podczas serializacji obiektu jako XML. W przypadku tworzenia usługi XML sieci Web, można zastosować atrybuty sterujące serializacji do klas i składowych, aby upewnić się, że dane wyjściowe XML jest zgodny z określonego schematu.

Na przykład **XmlSerializer** umożliwia:

- Określ, czy pole lub właściwość powinien być kodowany jako atrybut lub element.

- Określ przestrzeni nazw XML do użycia.

- Określ nazwę elementu lub atrybutu, jeśli nazwa pola lub właściwości jest nieodpowiedni.

Inną zaletą serializacji XML jest, że masz nie ograniczenia dla aplikacji, które tworzysz, tak długo, jak strumień XML, który jest generowany jest zgodny ze schematem danego. Wyobraź sobie schematu, używany do opisania książki. Zawiera funkcje tytuł, autor, Wydawca i ISBN numer elementu. Można opracować aplikację, która przetwarza dane XML w dowolny sposób, który ma, na przykład kolejność książki lub jako spis książki. W obu przypadkach jedynym wymaganiem jest, czy strumień XML jest zgodny ze schematem określonego języka (XSD) definicji schematu XML.

## <a name="xml-serialization-considerations"></a>Uwagi dotyczące serializacji XML

Następujące należy uwzględnić podczas przy użyciu **XmlSerializer** klasy:

- Narzędzie Sgen.exe wyraźnie jest przeznaczona do generowania zestawów serializacji w celu uzyskania optymalnej wydajności.

- Serializowane dane zawiera tylko danych i struktury klas. Informacje o tożsamości i zestawu typu nie są uwzględniane.

- Może być Zserializowany tylko właściwości publiczne i pola. Właściwości muszą mieć publiczne metody dostępu (Pobieranie i ustawianie metody). Jeśli muszą serializację danych bez publicznego, użyj <xref:System.Runtime.Serialization.DataContractSerializer> klasy zamiast serializacji XML.

- Klasa musi mieć konstruktora domyślnego przez **XmlSerializer**.

- Nie można serializować metody.

- **Element XmlSerializer** może przetwarzać klasy, które implementują **IEnumerable** lub **ICollection** inaczej, jeśli spełniają określone wymagania w następujący sposób.

  Klasa, która implementuje **IEnumerable** musi implementować publicznego **Dodaj** metodę, która przyjmuje jeden parametr. **Dodaj** parametru metody muszą być zgodne (polimorficzny) z typem zwracanym z **IEnumerator.Current** zwrócone przez właściwość **GetEnumerator** Metoda.

  Klasa, która implementuje **ICollection** oprócz **IEnumerable** (takie jak **CollectionBase**) musi mieć publiczny **elementu** indeksowane właściwości (indeksatora w języku C#), która przyjmuje całkowitą, a musi mieć publiczny **liczba** właściwości typu **całkowitą**. Parametr przekazany do **Dodaj** metoda musi być tego samego typu, jaka jest zwracana z **elementu** właściwości lub jeden z tego typu zasad.

  Dla klas które implementują **ICollection**, wartości serializacji są pobierane z indeksowanej **elementu** właściwości, a nie przez wywołanie metody **GetEnumerator**. Ponadto pola publiczne i właściwości są nie seryjny, z wyjątkiem publicznych pola, które zwracają innej kolekcji klasy (taki, który implementuje **ICollection**). Aby uzyskać przykład, zobacz [przykłady serializacji XML](examples-of-xml-serialization.md).

## <a name="xsd-data-type-mapping"></a>Mapowania typów danych XSD

W3C dokumentu zatytułowanej [XML schematu część 2: Typy danych](https://www.w3.org/TR/xmlschema-2/) Określa typy proste dane, które są dozwolone w schemacie języka (XSD) definicji schematu XML. Dla wielu z tych (na przykład **int** i **dziesiętna**), ma odpowiedni typ danych w programie .NET Framework. Jednak niektóre typy danych XML ma odpowiedni typ danych w programie .NET Framework (na przykład **NMTOKEN** — typ danych). W takich przypadkach Jeśli za pomocą narzędzia definicji schematu XML ([narzędzie definicji schematu XML (Xsd.exe)](xml-schema-definition-tool-xsd-exe.md)) do generowania klasy w schemacie, odpowiedni atrybut jest stosowany do składowej typu ciąg i jego **typudanych** właściwość jest ustawiona na nazwę typu danych XML. Na przykład, jeśli schemat zawiera element o nazwie "MyToken" z typem danych XML **NMTOKEN**, wygenerowana klasa może zawierać składową, jak pokazano w poniższym przykładzie.

```vb
<XmlElement(DataType:="NMTOKEN")> _
Public MyToken As String
```

```csharp
[XmlElement(DataType = "NMTOKEN")]
public string MyToken;
```

Podobnie, jeśli tworzysz klasę, która musi być zgodna do określonego schematu XML (XSD), należy zastosować odpowiedni atrybut i ustawić jej **DataType** właściwość do żądanej dane XML, wpisz nazwę.

Aby uzyskać pełną listę mapowań typu, zobacz **DataType** właściwości dla każdej z następujących klas atrybutów:

- <xref:System.Xml.Serialization.SoapAttributeAttribute>

- <xref:System.Xml.Serialization.SoapElementAttribute>

- <xref:System.Xml.Serialization.XmlArrayItemAttribute>

- <xref:System.Xml.Serialization.XmlAttributeAttribute>

- <xref:System.Xml.Serialization.XmlElementAttribute>

- <xref:System.Xml.Serialization.XmlRootAttribute>

## <a name="see-also"></a>Zobacz także

- <xref:System.Xml.Serialization.XmlSerializer>
- <xref:System.Runtime.Serialization.DataContractSerializer>
- <xref:System.IO.FileStream>
- [Serializacja XML i SOAP](xml-and-soap-serialization.md)
- [Serializacja binarna](binary-serialization.md)
- [Serializacja](index.md)
- <xref:System.Xml.Serialization.XmlSerializer>
- [Przykłady serializacji XML](examples-of-xml-serialization.md)
- [Instrukcje: Serializacja obiektu](how-to-serialize-an-object.md)
- [Instrukcje: Deserializacji obiektu](how-to-deserialize-an-object.md)
