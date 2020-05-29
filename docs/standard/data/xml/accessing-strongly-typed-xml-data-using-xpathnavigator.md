---
title: Uzyskiwanie dostępu do silnie typizowanych danych XML przy użyciu klasy XPathNavigator
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 898e0f52-8a7c-4d1f-afcd-6ffb28b050b4
ms.openlocfilehash: afbfd516ef25eff94a9eed841f313892007c58a1
ms.sourcegitcommit: 71b8f5a2108a0f1a4ef1d8d75c5b3e129ec5ca1e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2020
ms.locfileid: "84202340"
---
# <a name="accessing-strongly-typed-xml-data-using-xpathnavigator"></a>Uzyskiwanie dostępu do silnie typizowanych danych XML przy użyciu klasy XPathNavigator
Jako wystąpienie modelu danych XPath 2,0, <xref:System.Xml.XPath.XPathNavigator> Klasa może zawierać dane silnie wpisane, które są mapowane na typy środowiska uruchomieniowego języka wspólnego (CLR). Zgodnie z modelem danych XPath 2,0, tylko elementy i atrybuty mogą zawierać dane o jednoznacznie określonym typie. <xref:System.Xml.XPath.XPathNavigator>Klasa udostępnia mechanizmy do uzyskiwania dostępu do danych w <xref:System.Xml.XPath.XPathDocument> <xref:System.Xml.XmlDocument> obiekcie lub jako dane silnie wpisane oraz mechanizmy konwersji z jednego typu danych na inny.  
  
## <a name="type-information-exposed-by-xpathnavigator"></a>Informacje o typie uwidocznione przez element XPathNavigator  
 Dane XML 1,0 są technicznie bez typu, chyba że są przetwarzane ze schematem DTD, językiem definicji schematu XML (XSD) lub innym mechanizmem. Istnieje wiele kategorii informacji o typie, które mogą być skojarzone z elementem lub atrybutem XML.  
  
- Proste typy CLR: żaden z języków schematu XML nie obsługuje bezpośrednio typów środowiska uruchomieniowego języka wspólnego (CLR). Ponieważ warto mieć możliwość wyświetlania prostej zawartości elementu i atrybutu jako najbardziej odpowiedniego typu CLR, cała prosta zawartość może zostać wpisana jako <xref:System.String> nieobecność informacji o schemacie z dowolnymi dodatkowymi informacjami o schemacie, które mogłyby spowodować, że ta zawartość jest bardziej odpowiedni. Najlepiej pasujący typ CLR elementu prostego i zawartości atrybutu można znaleźć za pomocą <xref:System.Xml.XPath.XPathNavigator.ValueType%2A> właściwości. Aby uzyskać więcej informacji na temat mapowania ze schematów wbudowanych typów do typów CLR, zobacz [Obsługa typów w klasach system. XML](../../../../docs/standard/data/xml/type-support-in-the-system-xml-classes.md).  
  
- Listy typów prostych (CLR): element lub atrybut o prostej zawartości może zawierać listę wartości rozdzielonych znakami odstępu. Wartości są określane przez schemat XML jako "typ listy". W przypadku braku schematu XML taka zawartość prosta byłaby traktowana jak pojedynczy węzeł tekstowy. Gdy schemat XML jest dostępny, ta prosta zawartość może być ujawniona jako szereg wartości niepodzielnych, z których każdy ma typ prosty, który jest mapowany do kolekcji obiektów CLR. Aby uzyskać więcej informacji na temat mapowania ze schematów wbudowanych typów do typów CLR, zobacz [Obsługa typów w klasach system. XML](../../../../docs/standard/data/xml/type-support-in-the-system-xml-classes.md).  
  
- Wpisana wartość: atrybut lub element, który został sprawdzony przez schemat z typem prostym, ma wpisaną wartość. Ta wartość to typ pierwotny, taki jak liczbowy, ciąg lub typ daty. Wszystkie wbudowane typy proste w XSD można zamapować na typy CLR, które zapewniają dostęp do wartości węzła jako bardziej odpowiedni typ, a nie tylko jako <xref:System.String> . Element z atrybutami lub elementami podrzędnymi jest traktowany jako typ złożony. Wpisana wartość typu złożonego z prostą zawartością (tylko węzły tekstowe jako elementy podrzędne) jest taka sama jak w przypadku typu prostego jego zawartości. Wpisana wartość typu złożonego z zawartością złożoną (co najmniej jeden element podrzędny) to wartość ciągu łącząca wszystkie podrzędne węzły tekstowe zwracane jako <xref:System.String> . Aby uzyskać więcej informacji na temat mapowania ze schematów wbudowanych typów do typów CLR, zobacz [Obsługa typów w klasach system. XML](../../../../docs/standard/data/xml/type-support-in-the-system-xml-classes.md).  
  
- Nazwa typu określonego dla języka: w większości przypadków typy CLR, które są ustawiane jako efekt uboczny zastosowania schematu zewnętrznego, są używane w celu zapewnienia dostępu do wartości węzła. Mogą jednak wystąpić sytuacje, w których można ocenić typ skojarzony z określonym schematem zastosowanym do dokumentu XML. Na przykład możesz chcieć przeszukać dokument XML, wyodrębniając wszystkie elementy, które są określone jako mają zawartość typu "PurchaseOrder" zgodnie z dołączonym schematem. Takie informacje o typie można ustawić tylko w wyniku walidacji schematu i dostęp do tych informacji za pomocą <xref:System.Xml.XPath.XPathNavigator.XmlType%2A> właściwości i <xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A> <xref:System.Xml.XPath.XPathNavigator> klasy. Aby uzyskać więcej informacji, zobacz poniższą sekcję po sprawdzeniu poprawności schematu sprawdzonych (PSVI).  
  
- Odbicie typu specyficznego dla języka schematu: w innych przypadkach może być konieczne uzyskanie dalszych szczegółowych informacji o typie specyficznym dla schematu zastosowanym w dokumencie XML. Na przykład podczas odczytywania pliku XML może być konieczne wyodrębnienie `maxOccurs` atrybutu dla każdego prawidłowego węzła w dokumencie XML w celu wykonania niektórych obliczeń niestandardowych. Ponieważ te informacje są ustawiane tylko za pomocą walidacji schematu, są dostępne za pomocą <xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A> właściwości <xref:System.Xml.XPath.XPathNavigator> klasy. Aby uzyskać więcej informacji, zobacz poniższą sekcję po sprawdzeniu poprawności schematu sprawdzonych (PSVI).  
  
## <a name="xpathnavigator-typed-accessors"></a>Metody dostępu typu XPathNavigator  
 W poniższej tabeli przedstawiono różne właściwości i metody <xref:System.Xml.XPath.XPathNavigator> klasy, których można użyć w celu uzyskania dostępu do informacji o typie węzła.  
  
|Właściwość|Opis|  
|--------------|-----------------|  
|<xref:System.Xml.XPath.XPathNavigator.XmlType%2A>|Zawiera informacje o typie schematu XML dla węzła, jeśli jest on prawidłowy.|  
|<xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A>|Zawiera sprawdzonych walidacji schematu w węźle, który jest dodawany po walidacji. Obejmuje to informacje o typie schematu XML, a także informacje o ważności.|  
|<xref:System.Xml.XPath.XPathNavigator.ValueType%2A>|Typ CLR wartości w węźle.|  
|<xref:System.Xml.XPath.XPathNavigator.TypedValue%2A>|Zawartość węzła jako co najmniej jedna wartość CLR, której typem jest najbliższe dopasowanie do typu schematu XML węzła.|  
|<xref:System.Xml.XPath.XPathNavigator.ValueAsBoolean%2A>|<xref:System.String>Wartość bieżącego węzła rzutowana na <xref:System.Boolean> wartość, zgodnie z regułami rzutowania XPath 2,0 dla `xs:boolean` .|  
|<xref:System.Xml.XPath.XPathNavigator.ValueAsDateTime%2A>|<xref:System.String>Wartość bieżącego węzła rzutowana na <xref:System.DateTime> wartość, zgodnie z regułami rzutowania XPath 2,0 dla `xs:datetime` .|  
|<xref:System.Xml.XPath.XPathNavigator.ValueAsDouble%2A>|<xref:System.String>Wartość bieżącego węzła rzutowana na <xref:System.Double> wartość, zgodnie z regułami rzutowania XPath 2,0 dla `xsd:double` .|  
|<xref:System.Xml.XPath.XPathNavigator.ValueAsInt%2A>|<xref:System.String>Wartość bieżącego węzła rzutowana na <xref:System.Int32> wartość, zgodnie z regułami rzutowania XPath 2,0 dla `xs:integer` .|  
|<xref:System.Xml.XPath.XPathNavigator.ValueAsLong%2A>|<xref:System.String>Wartość bieżącego węzła rzutowana na <xref:System.Int64> wartość, zgodnie z regułami rzutowania XPath 2,0 dla `xs:integer` .|  
|<xref:System.Xml.XPath.XPathNavigator.ValueAs%2A>|Zawartość węzła jest rzutowana na typ docelowy zgodnie z regułami rzutowania XPath 2,0.|  
  
 Aby uzyskać więcej informacji na temat mapowania ze schematów wbudowanych typów do typów CLR, zobacz [Obsługa typów w klasach system. XML](../../../../docs/standard/data/xml/type-support-in-the-system-xml-classes.md).  
  
## <a name="the-post-schema-validation-infoset-psvi"></a>Sprawdzanie poprawności po stronie sprawdzonych (PSVI)  
 Procesor schematu XML akceptuje sprawdzonych XML jako dane wejściowe i konwertuje ją na wpis weryfikacji schematu sprawdzonych (PSVI). PSVI to oryginalny wejściowy kod XML sprawdzonych z nowymi dodawanymi elementami informacji i nowymi właściwościami dodawanymi do istniejących elementów informacji. Istnieją trzy szerokie klasy informacji dodanych do sprawdzonych XML w PSVI, które są udostępniane przez <xref:System.Xml.XPath.XPathNavigator> .  
  
1. Wyniki walidacji: informacje o tym, czy element lub atrybut został pomyślnie zweryfikowany. Jest to uwidaczniane przez <xref:System.Xml.Schema.IXmlSchemaInfo.Validity%2A> Właściwość <xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A> właściwości <xref:System.Xml.XPath.XPathNavigator> klasy.  
  
2. Informacje domyślne: wskazanie, czy wartość elementu lub atrybutu została uzyskana za pośrednictwem wartości domyślnych określonych w schemacie, czy nie. Jest to uwidaczniane przez <xref:System.Xml.Schema.IXmlSchemaInfo.IsDefault%2A> Właściwość <xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A> właściwości <xref:System.Xml.XPath.XPathNavigator> klasy.  
  
3. Adnotacje typu: odwołania do składników schematu, które mogą być definicjami typów lub deklaracji elementów i atrybutów. <xref:System.Xml.XPath.XPathNavigator.XmlType%2A>Właściwość <xref:System.Xml.XPath.XPathNavigator> zawiera informacje o określonym typie węzła, jeśli jest on prawidłowy. Jeśli ważność węzła jest nieznana, na przykład gdy została zweryfikowana, a następnie edytowana. następnie <xref:System.Xml.XPath.XPathNavigator.XmlType%2A> Właściwość jest ustawiona na, `null` ale informacje o typie są nadal dostępne z różnych właściwości <xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A> właściwości <xref:System.Xml.XPath.XPathNavigator> klasy.  
  
 Poniższy przykład ilustruje użycie informacji w sprawdzonych walidacji schematu uwidocznionych przez <xref:System.Xml.XPath.XPathNavigator> .  
  
```vb  
Dim settings As XmlReaderSettings = New XmlReaderSettings()  
settings.Schemas.Add("http://www.contoso.com/books", "books.xsd")  
settings.ValidationType = ValidationType.Schema  
  
Dim reader As XmlReader = XmlReader.Create("books.xml", settings)  
  
Dim document As XmlDocument = New XmlDocument()  
document.Load(reader)  
Dim navigator As XPathNavigator = document.CreateNavigator()  
navigator.MoveToChild("books", "http://www.contoso.com/books")  
navigator.MoveToChild("book", "http://www.contoso.com/books")  
navigator.MoveToChild("published", "http://www.contoso.com/books")  
  
Console.WriteLine(navigator.SchemaInfo.SchemaType.Name)  
Console.WriteLine(navigator.SchemaInfo.Validity)  
Console.WriteLine(navigator.SchemaInfo.SchemaElement.MinOccurs)  
```  
  
```csharp  
XmlReaderSettings settings = new XmlReaderSettings();  
settings.Schemas.Add("http://www.contoso.com/books", "books.xsd");  
settings.ValidationType = ValidationType.Schema;  
  
XmlReader reader = XmlReader.Create("books.xml", settings);  
  
XmlDocument document = new XmlDocument();  
document.Load(reader);  
XPathNavigator navigator = document.CreateNavigator();  
navigator.MoveToChild("books", "http://www.contoso.com/books");  
navigator.MoveToChild("book", "http://www.contoso.com/books");  
navigator.MoveToChild("published", "http://www.contoso.com/books");  
  
Console.WriteLine(navigator.SchemaInfo.SchemaType.Name);  
Console.WriteLine(navigator.SchemaInfo.Validity);  
Console.WriteLine(navigator.SchemaInfo.SchemaElement.MinOccurs);  
```  
  
 Przykład pobiera `books.xml` plik jako dane wejściowe.  
  
```xml  
<books xmlns="http://www.contoso.com/books">  
    <book>  
        <title>Title</title>  
        <price>10.00</price>  
        <published>2003-12-31</published>  
    </book>  
</books>  
```  
  
 Przykład pobiera również `books.xsd` schemat jako dane wejściowe.  
  
```xml  
<xs:schema xmlns="http://www.contoso.com/books"
attributeFormDefault="unqualified" elementFormDefault="qualified"
targetNamespace="http://www.contoso.com/books"
xmlns:xs="http://www.w3.org/2001/XMLSchema">  
    <xs:simpleType name="publishedType">  
        <xs:restriction base="xs:date">  
            <xs:minInclusive value="2003-01-01" />  
            <xs:maxInclusive value="2003-12-31" />  
        </xs:restriction>  
    </xs:simpleType>  
    <xs:complexType name="bookType">  
        <xs:sequence>  
            <xs:element name="title" type="xs:string"/>  
            <xs:element name="price" type="xs:decimal"/>  
            <xs:element name="published" type="publishedType"/>  
        </xs:sequence>  
    </xs:complexType>  
    <xs:complexType name="booksType">  
        <xs:sequence>  
            <xs:element name="book" type="bookType" />  
        </xs:sequence>  
    </xs:complexType>  
    <xs:element name="books" type="booksType" />  
</xs:schema>  
```  
  
## <a name="obtain-typed-values-using-valueas-properties"></a>Uzyskiwanie wpisanych wartości przy użyciu właściwości ValueAs  
 Wartość wpisana w węźle można pobrać, uzyskując dostęp do <xref:System.Xml.XPath.XPathNavigator.TypedValue%2A> właściwości <xref:System.Xml.XPath.XPathNavigator> . W niektórych przypadkach możesz chcieć przekonwertować wpisaną wartość węzła na inny typ. Typowym przykładem jest uzyskanie wartości liczbowej z węzła XML. Rozważmy na przykład następujący niesprawdzony i niewpisany dokument XML.  
  
```xml  
<books>  
    <book>  
        <title>Title</title>  
        <price>10.00</price>  
        <published>2003-12-31</published>  
    </book>  
</books>  
```  
  
 Jeśli pozycja <xref:System.Xml.XPath.XPathNavigator> jest ustawiona w elemencie, właściwość powinna być, `price` <xref:System.Xml.XPath.XPathNavigator.XmlType%2A> `null` <xref:System.Xml.XPath.XPathNavigator.ValueType%2A> <xref:System.String> a <xref:System.Xml.XPath.XPathNavigator.TypedValue%2A> Właściwość byłaby ciągiem `10.00` .  
  
 Jednak nadal jest możliwe wyodrębnienie wartości jako wartości liczbowej przy użyciu <xref:System.Xml.XPath.XPathItem.ValueAs%2A> <xref:System.Xml.XPath.XPathNavigator.ValueAsDouble%2A> metody,, <xref:System.Xml.XPath.XPathNavigator.ValueAsInt%2A> lub <xref:System.Xml.XPath.XPathNavigator.ValueAsLong%2A> i właściwości. Poniższy przykład ilustruje wykonywanie takich rzutowania przy użyciu <xref:System.Xml.XPath.XPathItem.ValueAs%2A> metody.  
  
```vb  
Dim document As New XmlDocument()  
document.Load("books.xml")  
Dim navigator As XPathNavigator = document.CreateNavigator()  
navigator.MoveToChild("books", "")  
navigator.MoveToChild("book", "")  
navigator.MoveToChild("price", "")  
  
Dim price = navigator.ValueAs(GetType(Decimal))  
Dim discount As Decimal = 0.2  
  
Console.WriteLine("The price of the book has been dropped 20% from {0:C} to {1:C}", navigator.Value, (price - price * discount))  
```  
  
```csharp  
XmlDocument document = new XmlDocument();  
document.Load("books.xml");  
XPathNavigator navigator = document.CreateNavigator();  
navigator.MoveToChild("books", "");  
navigator.MoveToChild("book", "");  
navigator.MoveToChild("price", "");  
  
Decimal price = (decimal)navigator.ValueAs(typeof(decimal));  
  
Console.WriteLine("The price of the book has been dropped 20% from {0:C} to {1:C}", navigator.Value, (price - price * (decimal)0.20));  
```  
  
 Aby uzyskać więcej informacji na temat mapowania ze schematów wbudowanych typów do typów CLR, zobacz [Obsługa typów w klasach system. XML](../../../../docs/standard/data/xml/type-support-in-the-system-xml-classes.md).  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- [Obsługa typu w ramach klas zestawu System.Xml](../../../../docs/standard/data/xml/type-support-in-the-system-xml-classes.md)
- [Przetwarzanie danych XML przy użyciu modelu danych XPath](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)
- [Nawigacja po zestawie węzłów przy użyciu klasy XPathNavigator](../../../../docs/standard/data/xml/node-set-navigation-using-xpathnavigator.md)
- [Nawigacja po atrybutach i przestrzeni nazw węzła przy użyciu klasy XPathNavigator](../../../../docs/standard/data/xml/attribute-and-namespace-node-navigation-using-xpathnavigator.md)
- [Wyodrębnianie danych XML przy użyciu klasy XPathNavigator](../../../../docs/standard/data/xml/extract-xml-data-using-xpathnavigator.md)
