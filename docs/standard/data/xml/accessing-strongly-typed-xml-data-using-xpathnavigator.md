---
title: Uzyskiwanie dostępu do silnie typu danych XML przy użyciu parametrem XPathNavigator
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 898e0f52-8a7c-4d1f-afcd-6ffb28b050b4
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 040a137f9b7c26c4484a69313e1f405699a19b64
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="accessing-strongly-typed-xml-data-using-xpathnavigator"></a>Uzyskiwanie dostępu do silnie typu danych XML przy użyciu parametrem XPathNavigator
Jako wystąpienie modelu danych XPath 2.0 <xref:System.Xml.XPath.XPathNavigator> klasy może zawierać jednoznacznie danych, który jest mapowany na typowych języka wspólnego (CLR). Zgodnie z modelem danych XPath 2.0 tylko elementy i atrybuty mogą zawierać silnie typizowane dane. <xref:System.Xml.XPath.XPathNavigator> Klasy zawiera mechanizmy do uzyskiwania dostępu do danych w ramach <xref:System.Xml.XPath.XPathDocument> lub <xref:System.Xml.XmlDocument> obiektu jako silnie typizowane dane, a także mechanizmy do konwertowania z jednego typu danych.  
  
## <a name="type-information-exposed-by-xpathnavigator"></a>Informacje o typie udostępnione przez element XPathNavigator  
 Dane XML 1.0 jest technicznie bez typu, chyba że przetworzyć DTD XML schematu (XSD) języka definicji schematu lub inny mechanizm. Istnieje wiele kategorii informacji o typie, który może być skojarzony z elementu lub atrybutu XML.  
  
-   Proste typy CLR: Brak schematu XML języków obsługuje typy środowiska uruchomieniowego języka wspólnego (CLR) bezpośrednio. Ponieważ warto mieć możliwość wyświetlania elementu proste i zawartość atrybutów jako najbardziej odpowiedni typ CLR, wszystkie prostej zawartości można wpisać jako <xref:System.String> w przypadku braku informacji o schemacie ze wszystkimi dodać informacji o schemacie potencjalnie uściślenie tę zawartość więcej odpowiedniego typu. Można znaleźć najlepiej dopasowaną CLR typu prostego elementów i atrybutów zawartości przy użyciu <xref:System.Xml.XPath.XPathNavigator.ValueType%2A> właściwości. Aby uzyskać więcej informacji na temat mapowanie schematu typy wbudowane typy CLR, zobacz [typu obsługi w klasach System.Xml](../../../../docs/standard/data/xml/type-support-in-the-system-xml-classes.md).  
  
-   Lista typów prostych (CLR): element lub atrybut o zawartości prostej mogą zawierać listę wartości oddzielonych biały znak. Wartości są określone przez schemat XML na "typ listy". W przypadku braku schematu XML takie prostej zawartości będzie traktowane jako jeden tekst węzła. Po udostępnieniu schematu XML to prosta zawartość można udostępnić jak szereg atomic wartości każde posiada typu prostego, który jest mapowany na kolekcję obiektów CLR. Aby uzyskać więcej informacji na temat mapowanie schematu typy wbudowane typy CLR, zobacz [typu obsługi w klasach System.Xml](../../../../docs/standard/data/xml/type-support-in-the-system-xml-classes.md).  
  
-   Wartość: Sprawdzania poprawności schematu atrybutu lub elementu z typu prostego ma wartość typu. Ta wartość jest typu pierwotnego, takie jak liczbowe, ciągu lub typu date. Wszystkie typy proste wbudowane w XSD mogą być mapowane na typy CLR, które zapewniają dostęp do wartości węzła jako typu bardziej odpowiednie, a nie tylko jako <xref:System.String>. Element z atrybutów lub elementów podrzędnych jest uważany za typ złożony. Typu wartości typu złożonego o zawartości prostej (tylko węzły tekstowe jako elementy podrzędne) jest taka sama jak typu prostego jego zawartości. Wartość typu Typ złożony z zawartością złożoną (jeden lub więcej elementów podrzędnych) to wartość ciągu łączenia wszystkich tekst węzły podrzędne zwracane jako <xref:System.String>. Aby uzyskać więcej informacji na temat mapowanie schematu typy wbudowane typy CLR, zobacz [typu obsługi w klasach System.Xml](../../../../docs/standard/data/xml/type-support-in-the-system-xml-classes.md).  
  
-   Nazwa typu z określonego języka schematu: W większości przypadków typy CLR, które są skonfigurowane jako efekt uboczny stosowania zewnętrzny schemat, są używane do zapewniają dostęp do wartości węzła. Jednak może być sytuacje, w którym można zbadać typ skojarzony z określonym schematem zastosowane do dokumentu XML. Na przykład możesz przeszukiwać dokument XML wyodrębniania wszystkie elementy, które są określane mieć zawartości typu "PurchaseOrder" w zależności od schematu. Takie informacje o typie można ustawić tylko w wyniku sprawdzania poprawności schematu i te informacje jest dostępny za pośrednictwem <xref:System.Xml.XPath.XPathNavigator.XmlType%2A> i <xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A> właściwości <xref:System.Xml.XPath.XPathNavigator> klasy. Aby uzyskać więcej informacji zobacz sekcję Post schemat sprawdzania poprawności typu infoset sprawdzonych (PSVI) poniżej.  
  
-   Odbicie typu określonego języka schematu: W innych przypadkach można uzyskać dodatkowe szczegóły typu określonego schematu zastosowane do dokumentu XML. Na przykład podczas odczytywania pliku XML, można wyodrębnić `maxOccurs` atrybutu dla każdego węzła nieprawidłowy dokument XML w celu wykonywania pewnych obliczeń niestandardowych. Ponieważ te informacje jest ustawiona tylko przez schemat weryfikacji, jest dostępny za pośrednictwem <xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A> właściwość <xref:System.Xml.XPath.XPathNavigator> klasy. Aby uzyskać więcej informacji zobacz sekcję Post schemat sprawdzania poprawności typu infoset sprawdzonych (PSVI) poniżej.  
  
## <a name="xpathnavigator-typed-accessors"></a>Element XPathNavigator typu metody dostępu  
 W poniższej tabeli przedstawiono różne właściwości i metody <xref:System.Xml.XPath.XPathNavigator> klasy, która umożliwia dostęp do informacji o typie o węzła.  
  
|Właściwość|Opis|  
|--------------|-----------------|  
|<xref:System.Xml.XPath.XPathNavigator.XmlType%2A>|Zawiera informacje o typie schematu XML dla węzła, jeśli jest ona prawidłowa.|  
|<xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A>|Zawiera Infoset sprawdzania poprawności schematu Post węzła, który jest dodawany po weryfikacji. W tym informacje o typie schematu XML, a także informacje o ważności.|  
|<xref:System.Xml.XPath.XPathNavigator.ValueType%2A>|Typ CLR typu wartość węzła.|  
|<xref:System.Xml.XPath.XPathNavigator.TypedValue%2A>|Zawartość węzła CLR jeden lub więcej wartości o typie jest najlepiej pasuje do typu schematu XML węzła.|  
|<xref:System.Xml.XPath.XPathNavigator.ValueAsBoolean%2A>|<xref:System.String> Rzutować wartości z bieżącego węzła <xref:System.Boolean> wartości zgodnie z regułami rzutowanie XPath 2.0 dla `xs:boolean`.|  
|<xref:System.Xml.XPath.XPathNavigator.ValueAsDateTime%2A>|<xref:System.String> Rzutować wartości z bieżącego węzła <xref:System.DateTime> wartości zgodnie z regułami rzutowanie XPath 2.0 dla `xs:datetime`.|  
|<xref:System.Xml.XPath.XPathNavigator.ValueAsDouble%2A>|<xref:System.String> Rzutować wartości z bieżącego węzła <xref:System.Double> wartości zgodnie z regułami rzutowanie XPath 2.0 dla `xsd:double`.|  
|<xref:System.Xml.XPath.XPathNavigator.ValueAsInt%2A>|<xref:System.String> Rzutować wartości z bieżącego węzła <xref:System.Int32> wartości zgodnie z regułami rzutowanie XPath 2.0 dla `xs:integer`.|  
|<xref:System.Xml.XPath.XPathNavigator.ValueAsLong%2A>|<xref:System.String> Rzutować wartości z bieżącego węzła <xref:System.Int64> wartości zgodnie z regułami rzutowanie XPath 2.0 dla `xs:integer`.|  
|<xref:System.Xml.XPath.XPathNavigator.ValueAs%2A>|Zawartość węzła Rzutowanie na typ docelowy zgodnie z regułami rzutowanie XPath 2.0.|  
  
 Aby uzyskać więcej informacji na temat mapowanie schematu typy wbudowane typy CLR, zobacz [typu obsługi w klasach System.Xml](../../../../docs/standard/data/xml/type-support-in-the-system-xml-classes.md).  
  
## <a name="the-post-schema-validation-infoset-psvi"></a>Post schemat sprawdzania poprawności typu infoset sprawdzonych (PSVI)  
 Procesor schematu XML akceptuje obiektu XML typu Infoset jako dane wejściowe i konwertuje ją na Post schemat sprawdzania poprawności typu Infoset (PSVI). PSVI jest oryginalny wejściowego XML typu infoset nowych elementów informacji dodany i nowych właściwości dodane do istniejących elementów informacji. Istnieją trzy klasy szerokie informacji dodawanych do typu Infoset XML w PSVI, które są udostępniane przez <xref:System.Xml.XPath.XPathNavigator>.  
  
1.  Wyniki sprawdzania poprawności: Informacje dotyczące tego, czy element lub atrybut pomyślnie zweryfikowano lub nie. To jest udostępniany przez <xref:System.Xml.Schema.IXmlSchemaInfo.Validity%2A> właściwość <xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A> właściwość <xref:System.Xml.XPath.XPathNavigator> klasy.  
  
2.  Domyślne informacje: Wskazać, czy wartość elementu lub atrybutu uzyskano przy użyciu wartości domyślnych określonej w schemacie, czy nie. To jest udostępniany przez <xref:System.Xml.Schema.IXmlSchemaInfo.IsDefault%2A> właściwość <xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A> właściwość <xref:System.Xml.XPath.XPathNavigator> klasy.  
  
3.  Adnotacje typu: Odwołania do składników schematu, które mogą być definicji typu lub deklaracje elementów i atrybutów. <xref:System.Xml.XPath.XPathNavigator.XmlType%2A> Właściwość <xref:System.Xml.XPath.XPathNavigator> zawiera informacje określonego typu węzła, jeśli jest ona prawidłowa. Jeśli ważność węzeł jest nieznany, takie jak kiedy został zweryfikowany następnie później edytować. następnie przy użyciu <xref:System.Xml.XPath.XPathNavigator.XmlType%2A> właściwość jest ustawiona na `null` , ale jest nadal dostępne z różne właściwości informacji o typie <xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A> właściwość <xref:System.Xml.XPath.XPathNavigator> klasy.  
  
 Poniższy przykład przedstawia, korzystając z informacji Infoset sprawdzania poprawności schematu Post udostępnianych przez <xref:System.Xml.XPath.XPathNavigator>.  
  
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
  
 Przykład przyjmuje `books.xml` pliku jako dane wejściowe.  
  
```xml  
<books xmlns="http://www.contoso.com/books">  
    <book>  
        <title>Title</title>  
        <price>10.00</price>  
        <published>2003-12-31</published>  
    </book>  
</books>  
```  
  
 Przykład również przyjmuje `books.xsd` schematu jako dane wejściowe.  
  
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
  
## <a name="obtain-typed-values-using-valueas-properties"></a>Uzyskanie typu wartości za pomocą właściwości ValueAs  
 Można pobrać typu wartości węzła po zalogowaniu się do <xref:System.Xml.XPath.XPathNavigator.TypedValue%2A> właściwość <xref:System.Xml.XPath.XPathNavigator>. W niektórych przypadkach można przekonwertować wartości typu węzła do innego typu. Typowym przykładem jest uzyskanie wartość liczbową z węzła XML. Rozważmy na przykład następujący dokument XML niezweryfikowanych i bez typu.  
  
```xml  
<books>  
    <book>  
        <title>Title</title>  
        <price>10.00</price>  
        <published>2003-12-31</published>  
    </book>  
</books>  
```  
  
 Jeśli <xref:System.Xml.XPath.XPathNavigator> jest ustawiony na `price` elementu <xref:System.Xml.XPath.XPathNavigator.XmlType%2A> byłoby właściwości `null`, <xref:System.Xml.XPath.XPathNavigator.ValueType%2A> byłoby właściwości <xref:System.String>i <xref:System.Xml.XPath.XPathNavigator.TypedValue%2A> właściwość może być ciągiem `10.00`.  
  
 Jednak jest nadal możliwe wyodrębnić wartość jako wartość liczbowa przy użyciu <xref:System.Xml.XPath.XPathItem.ValueAs%2A>, <xref:System.Xml.XPath.XPathNavigator.ValueAsDouble%2A>, <xref:System.Xml.XPath.XPathNavigator.ValueAsInt%2A>, lub <xref:System.Xml.XPath.XPathNavigator.ValueAsLong%2A> metody i właściwości. Poniższy przykład przedstawia wykonywania takich rzutowania using <xref:System.Xml.XPath.XPathItem.ValueAs%2A> metody.  
  
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
  
 Aby uzyskać więcej informacji na temat mapowanie schematu typy wbudowane typy CLR, zobacz [typu obsługi w klasach System.Xml](../../../../docs/standard/data/xml/type-support-in-the-system-xml-classes.md).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Xml.XmlDocument>  
 <xref:System.Xml.XPath.XPathDocument>  
 <xref:System.Xml.XPath.XPathNavigator>  
 [Obsługa typu w ramach klas zestawu System.Xml](../../../../docs/standard/data/xml/type-support-in-the-system-xml-classes.md)  
 [Przetwarzanie danych XML przy użyciu modelu danych XPath](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)  
 [Nawigacja po zestawie węzłów przy użyciu klasy XPathNavigator](../../../../docs/standard/data/xml/node-set-navigation-using-xpathnavigator.md)  
 [Nawigacja po atrybutach i przestrzeni nazw węzła przy użyciu klasy XPathNavigator](../../../../docs/standard/data/xml/attribute-and-namespace-node-navigation-using-xpathnavigator.md)  
 [Wyodrębnianie danych XML przy użyciu klasy XPathNavigator](../../../../docs/standard/data/xml/extract-xml-data-using-xpathnavigator.md)
