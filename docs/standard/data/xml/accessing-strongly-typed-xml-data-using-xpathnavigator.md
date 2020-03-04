---
title: Uzyskiwanie dostępu do silnie typizowanych danych XML przy użyciu klasy XPathNavigator
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 898e0f52-8a7c-4d1f-afcd-6ffb28b050b4
ms.openlocfilehash: e6ec30e3c7c2318b199122cd63c7f56584707a98
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2020
ms.locfileid: "78158054"
---
# <a name="accessing-strongly-typed-xml-data-using-xpathnavigator"></a>Uzyskiwanie dostępu do silnie typizowanych danych XML przy użyciu klasy XPathNavigator
Jako wystąpienie modelu danych XPath 2,0, Klasa <xref:System.Xml.XPath.XPathNavigator> może zawierać dane z jednoznacznie określonym typem, które są mapowane na typy środowiska uruchomieniowego języka wspólnego (CLR). Zgodnie z modelem danych XPath 2,0, tylko elementy i atrybuty mogą zawierać dane o jednoznacznie określonym typie. Klasa <xref:System.Xml.XPath.XPathNavigator> udostępnia mechanizmy do uzyskiwania dostępu do danych w <xref:System.Xml.XPath.XPathDocument> lub <xref:System.Xml.XmlDocument> obiekt jako dane z jednoznacznie określonym typem oraz mechanizmy konwersji z jednego typu danych na inny.  
  
## <a name="type-information-exposed-by-xpathnavigator"></a>Informacje o typie uwidocznione przez element XPathNavigator  
 Dane XML 1,0 są technicznie bez typu, chyba że są przetwarzane ze schematem DTD, językiem definicji schematu XML (XSD) lub innym mechanizmem. Istnieje wiele kategorii informacji o typie, które mogą być skojarzone z elementem lub atrybutem XML.  
  
- Proste typy CLR: żaden z języków schematu XML nie obsługuje bezpośrednio typów środowiska uruchomieniowego języka wspólnego (CLR). Ponieważ przydatne jest, aby można było wyświetlać proste zawartości elementów i atrybutów jako najbardziej odpowiedni typ CLR, cała zawartość prosta może być wpisywany jako <xref:System.String> w przypadku braku informacji o schemacie z dowolnymi dodatkowymi informacjami o schemacie, aby potencjalnie udoskonalić tę zawartość do bardziej odpowiedniego typu. Najlepiej pasujący typ CLR elementu prostego i zawartości atrybutu można znaleźć za pomocą właściwości <xref:System.Xml.XPath.XPathNavigator.ValueType%2A>. Aby uzyskać więcej informacji na temat mapowania ze schematów wbudowanych typów do typów CLR, zobacz [Obsługa typów w klasach system. XML](../../../../docs/standard/data/xml/type-support-in-the-system-xml-classes.md).  
  
- Listy typów prostych (CLR): element lub atrybut o prostej zawartości może zawierać listę wartości rozdzielonych znakami odstępu. Wartości są określane przez schemat XML jako "typ listy". W przypadku braku schematu XML taka zawartość prosta byłaby traktowana jak pojedynczy węzeł tekstowy. Gdy schemat XML jest dostępny, ta prosta zawartość może być ujawniona jako szereg wartości niepodzielnych, z których każdy ma typ prosty, który jest mapowany do kolekcji obiektów CLR. Aby uzyskać więcej informacji na temat mapowania ze schematów wbudowanych typów do typów CLR, zobacz [Obsługa typów w klasach system. XML](../../../../docs/standard/data/xml/type-support-in-the-system-xml-classes.md).  
  
- Wpisana wartość: atrybut lub element, który został sprawdzony przez schemat z typem prostym, ma wpisaną wartość. Ta wartość to typ pierwotny, taki jak liczbowy, ciąg lub typ daty. Wszystkie wbudowane typy proste w XSD można zamapować na typy CLR, które zapewniają dostęp do wartości węzła jako bardziej odpowiedni typ, a nie tylko jako <xref:System.String>. Element z atrybutami lub elementami podrzędnymi jest traktowany jako typ złożony. Wpisana wartość typu złożonego z prostą zawartością (tylko węzły tekstowe jako elementy podrzędne) jest taka sama jak w przypadku typu prostego jego zawartości. Wpisana wartość typu złożonego z zawartością złożoną (co najmniej jeden element podrzędny) to wartość ciągu łącząca wszystkie podrzędne węzły tekstowe zwracane jako <xref:System.String>. Aby uzyskać więcej informacji na temat mapowania ze schematów wbudowanych typów do typów CLR, zobacz [Obsługa typów w klasach system. XML](../../../../docs/standard/data/xml/type-support-in-the-system-xml-classes.md).  
  
- Nazwa typu określonego dla języka: w większości przypadków typy CLR, które są ustawiane jako efekt uboczny zastosowania schematu zewnętrznego, są używane w celu zapewnienia dostępu do wartości węzła. Mogą jednak wystąpić sytuacje, w których można ocenić typ skojarzony z określonym schematem zastosowanym do dokumentu XML. Na przykład możesz chcieć przeszukać dokument XML, wyodrębniając wszystkie elementy, które są określone jako mają zawartość typu "PurchaseOrder" zgodnie z dołączonym schematem. Takie informacje o typie można ustawić tylko w wyniku walidacji schematu i dostęp do tych informacji za pomocą właściwości <xref:System.Xml.XPath.XPathNavigator.XmlType%2A> i <xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A> klasy <xref:System.Xml.XPath.XPathNavigator>. Aby uzyskać więcej informacji, zobacz poniższą sekcję po sprawdzeniu poprawności schematu sprawdzonych (PSVI).  
  
- Odbicie typu specyficznego dla języka schematu: w innych przypadkach może być konieczne uzyskanie dalszych szczegółowych informacji o typie specyficznym dla schematu zastosowanym w dokumencie XML. Na przykład podczas odczytywania pliku XML można wyodrębnić atrybut `maxOccurs` dla każdego prawidłowego węzła w dokumencie XML, aby wykonać niestandardowe obliczenia. Ponieważ te informacje są ustawiane tylko za pomocą walidacji schematu, można uzyskać do niej dostęp za pomocą właściwości <xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A> klasy <xref:System.Xml.XPath.XPathNavigator>. Aby uzyskać więcej informacji, zobacz poniższą sekcję po sprawdzeniu poprawności schematu sprawdzonych (PSVI).  
  
## <a name="xpathnavigator-typed-accessors"></a>Metody dostępu typu XPathNavigator  
 W poniższej tabeli przedstawiono różne właściwości i metody klasy <xref:System.Xml.XPath.XPathNavigator>, których można użyć w celu uzyskania dostępu do informacji o typie węzła.  
  
|Właściwość|Opis|  
|--------------|-----------------|  
|<xref:System.Xml.XPath.XPathNavigator.XmlType%2A>|Zawiera informacje o typie schematu XML dla węzła, jeśli jest on prawidłowy.|  
|<xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A>|Zawiera sprawdzonych walidacji schematu w węźle, który jest dodawany po walidacji. Obejmuje to informacje o typie schematu XML, a także informacje o ważności.|  
|<xref:System.Xml.XPath.XPathNavigator.ValueType%2A>|Typ CLR wartości w węźle.|  
|<xref:System.Xml.XPath.XPathNavigator.TypedValue%2A>|Zawartość węzła jako co najmniej jedna wartość CLR, której typem jest najbliższe dopasowanie do typu schematu XML węzła.|  
|<xref:System.Xml.XPath.XPathNavigator.ValueAsBoolean%2A>|Wartość <xref:System.String> bieżącego węzła jest rzutowana na wartość <xref:System.Boolean>, zgodnie z regułami rzutowania XPath 2,0 dla `xs:boolean`.|  
|<xref:System.Xml.XPath.XPathNavigator.ValueAsDateTime%2A>|Wartość <xref:System.String> bieżącego węzła jest rzutowana na wartość <xref:System.DateTime>, zgodnie z regułami rzutowania XPath 2,0 dla `xs:datetime`.|  
|<xref:System.Xml.XPath.XPathNavigator.ValueAsDouble%2A>|Wartość <xref:System.String> bieżącego węzła jest rzutowana na wartość <xref:System.Double>, zgodnie z regułami rzutowania XPath 2,0 dla `xsd:double`.|  
|<xref:System.Xml.XPath.XPathNavigator.ValueAsInt%2A>|Wartość <xref:System.String> bieżącego węzła jest rzutowana na wartość <xref:System.Int32>, zgodnie z regułami rzutowania XPath 2,0 dla `xs:integer`.|  
|<xref:System.Xml.XPath.XPathNavigator.ValueAsLong%2A>|Wartość <xref:System.String> bieżącego węzła jest rzutowana na wartość <xref:System.Int64>, zgodnie z regułami rzutowania XPath 2,0 dla `xs:integer`.|  
|<xref:System.Xml.XPath.XPathNavigator.ValueAs%2A>|Zawartość węzła jest rzutowana na typ docelowy zgodnie z regułami rzutowania XPath 2,0.|  
  
 Aby uzyskać więcej informacji na temat mapowania ze schematów wbudowanych typów do typów CLR, zobacz [Obsługa typów w klasach system. XML](../../../../docs/standard/data/xml/type-support-in-the-system-xml-classes.md).  
  
## <a name="the-post-schema-validation-infoset-psvi"></a>Sprawdzanie poprawności po stronie sprawdzonych (PSVI)  
 Procesor schematu XML akceptuje sprawdzonych XML jako dane wejściowe i konwertuje ją na wpis weryfikacji schematu sprawdzonych (PSVI). PSVI to oryginalny wejściowy kod XML sprawdzonych z nowymi dodawanymi elementami informacji i nowymi właściwościami dodawanymi do istniejących elementów informacji. Istnieją trzy szerokie klasy informacji dodanych do sprawdzonych XML w PSVI, które są udostępniane przez <xref:System.Xml.XPath.XPathNavigator>.  
  
1. Wyniki walidacji: informacje o tym, czy element lub atrybut został pomyślnie zweryfikowany. Jest to uwidaczniane przez właściwość <xref:System.Xml.Schema.IXmlSchemaInfo.Validity%2A> właściwości <xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A> klasy <xref:System.Xml.XPath.XPathNavigator>.  
  
2. Informacje domyślne: wskazanie, czy wartość elementu lub atrybutu została uzyskana za pośrednictwem wartości domyślnych określonych w schemacie, czy nie. Jest to uwidaczniane przez właściwość <xref:System.Xml.Schema.IXmlSchemaInfo.IsDefault%2A> właściwości <xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A> klasy <xref:System.Xml.XPath.XPathNavigator>.  
  
3. Adnotacje typu: odwołania do składników schematu, które mogą być definicjami typów lub deklaracji elementów i atrybutów. Właściwość <xref:System.Xml.XPath.XPathNavigator.XmlType%2A> <xref:System.Xml.XPath.XPathNavigator> zawiera informacje o określonym typie węzła, jeśli jest on prawidłowy. Jeśli ważność węzła jest nieznana, na przykład gdy została zweryfikowana, a następnie edytowana. następnie właściwość <xref:System.Xml.XPath.XPathNavigator.XmlType%2A> jest ustawiona na `null`, ale informacje o typie są nadal dostępne z różnych właściwości właściwości <xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A> klasy <xref:System.Xml.XPath.XPathNavigator>.  
  
 Poniższy przykład ilustruje użycie informacji w sprawdzonych walidacji schematu uwidocznionych przez <xref:System.Xml.XPath.XPathNavigator>.  
  
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
  
 Przykład pobiera również schemat `books.xsd` jako dane wejściowe.  
  
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
 Wartość wpisana w węźle można pobrać, uzyskując dostęp do właściwości <xref:System.Xml.XPath.XPathNavigator.TypedValue%2A> <xref:System.Xml.XPath.XPathNavigator>. W niektórych przypadkach możesz chcieć przekonwertować wpisaną wartość węzła na inny typ. Typowym przykładem jest uzyskanie wartości liczbowej z węzła XML. Rozważmy na przykład następujący niesprawdzony i niewpisany dokument XML.  
  
```xml  
<books>  
    <book>  
        <title>Title</title>  
        <price>10.00</price>  
        <published>2003-12-31</published>  
    </book>  
</books>  
```  
  
 Jeśli <xref:System.Xml.XPath.XPathNavigator> jest umieszczona w `price` elemencie, właściwość <xref:System.Xml.XPath.XPathNavigator.XmlType%2A> byłaby `null`, <xref:System.Xml.XPath.XPathNavigator.ValueType%2A> właściwość będzie <xref:System.String>, a właściwość <xref:System.Xml.XPath.XPathNavigator.TypedValue%2A> będzie ciąg `10.00`.  
  
 Jednak nadal jest możliwe wyodrębnienie wartości jako wartości liczbowej przy użyciu metody <xref:System.Xml.XPath.XPathItem.ValueAs%2A>, <xref:System.Xml.XPath.XPathNavigator.ValueAsDouble%2A>, <xref:System.Xml.XPath.XPathNavigator.ValueAsInt%2A>lub <xref:System.Xml.XPath.XPathNavigator.ValueAsLong%2A>. Poniższy przykład ilustruje wykonywanie takich rzutowania przy użyciu metody <xref:System.Xml.XPath.XPathItem.ValueAs%2A>.  
  
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
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- [Obsługa typu w ramach klas zestawu System.Xml](../../../../docs/standard/data/xml/type-support-in-the-system-xml-classes.md)
- [Przetwarzanie danych XML przy użyciu modelu danych XPath](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)
- [Nawigacja po zestawie węzłów przy użyciu klasy XPathNavigator](../../../../docs/standard/data/xml/node-set-navigation-using-xpathnavigator.md)
- [Nawigacja po atrybutach i przestrzeni nazw węzła przy użyciu klasy XPathNavigator](../../../../docs/standard/data/xml/attribute-and-namespace-node-navigation-using-xpathnavigator.md)
- [Wyodrębnianie danych XML przy użyciu klasy XPathNavigator](../../../../docs/standard/data/xml/extract-xml-data-using-xpathnavigator.md)
