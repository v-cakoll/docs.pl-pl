---
title: Uzyskiwanie dostępu do silnie typizowanych danych XML przy użyciu klasy XPathNavigator
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 898e0f52-8a7c-4d1f-afcd-6ffb28b050b4
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1905e9f1d80931bd15cff5f3d0a92ceee29435ef
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61921241"
---
# <a name="accessing-strongly-typed-xml-data-using-xpathnavigator"></a>Uzyskiwanie dostępu do silnie typizowanych danych XML przy użyciu klasy XPathNavigator
Jako wystąpienia w modelu danych XPath 2.0 <xref:System.Xml.XPath.XPathNavigator> klasy może zawierać silnie typizowane dane, który jest mapowany do typowych języka wspólnego (CLR). Zgodnie z modelu danych XPath 2.0 tylko elementów i atrybutów może zawierać silnie typizowane dane. <xref:System.Xml.XPath.XPathNavigator> Klasa udostępnia mechanizmy do uzyskiwania dostępu do danych w ramach <xref:System.Xml.XPath.XPathDocument> lub <xref:System.Xml.XmlDocument> obiektu jako silnie typizowane dane, a także mechanizmów do konwertowania z jednego typu danych.  
  
## <a name="type-information-exposed-by-xpathnavigator"></a>Informacje o typie udostępnianych przez klasy XPathNavigator  
 Dane XML 1.0 jest technicznie bez typu, chyba że przetworzyć DTD, XML języka (XSD) definicji schematu lub inny mechanizm. Istnieje wiele kategorii informacji o typie, który może być skojarzony z elementu lub atrybutu XML.  
  
- Typy proste CLR: Brak języki schematu XML bezpośrednio obsługują typy środowiska uruchomieniowego języka wspólnego (CLR). Ponieważ jest to przydatne można było wyświetlić prosty element i atrybut zawartość jako najbardziej odpowiednim typem CLR, cała zawartość prostą można wpisać jako <xref:System.String> w przypadku braku informacji o schemacie ze wszystkimi dodano potencjalnie rafinacja tę zawartość do informacji o schemacie Typ, bardziej odpowiednie. Możesz znaleźć najlepiej dopasowaną typ CLR prostej zawartości elementów i atrybutów przy użyciu <xref:System.Xml.XPath.XPathNavigator.ValueType%2A> właściwości. Aby uzyskać więcej informacji o mapowaniu z wbudowanych typów schematu na typy CLR, zobacz [Obsługa typu w ramach klas zestawu System.Xml](../../../../docs/standard/data/xml/type-support-in-the-system-xml-classes.md).  
  
- Wyświetla typy proste (CLR): Element lub atrybut o zawartości prostej mogą zawierać listę wartości oddzielonych biały znak. Wartości są określone przez schemat XML jako "type listy". W przypadku braku schematu XML takie prostej zawartości będzie traktowane jako węzeł tekstowy jednego. Po udostępnieniu schematu XML jako szereg niepodzielnych wartości posiadającymi prosty typ, który jest mapowany do kolekcji obiektów CLR można ujawnić tej prostej zawartości. Aby uzyskać więcej informacji o mapowaniu z wbudowanych typów schematu na typy CLR, zobacz [Obsługa typu w ramach klas zestawu System.Xml](../../../../docs/standard/data/xml/type-support-in-the-system-xml-classes.md).  
  
- Wartość: Sprawdzania poprawności schematu atrybutu lub elementu z typu prostego ma wartość wpisane. Ta wartość jest typu podstawowego, takich jak numeryczne, ciągu lub typu Data. Wszystkie wbudowane typy proste w XSD mogą być mapowane na typy CLR, które zapewniają dostęp do wartości węzła jako typu bardziej odpowiednie, a nie tylko jako <xref:System.String>. Element o atrybuty i elementy podrzędne jest uważana za typ złożony. Wpisane wartości typu złożonego o zawartości prostej (tylko węzły tekstowe jako elementy podrzędne) jest taka sama jak w przypadku typu prostego jego zawartości. Wpisane wartość typ złożony z zawartością złożoną (jeden lub więcej elementów podrzędnych) jest wartość ciągu łączenia wszystkie jego podrzędne węzły tekstowe zwracane jako <xref:System.String>. Aby uzyskać więcej informacji o mapowaniu z wbudowanych typów schematu na typy CLR, zobacz [Obsługa typu w ramach klas zestawu System.Xml](../../../../docs/standard/data/xml/type-support-in-the-system-xml-classes.md).  
  
- Nazwa typu określonego schematu języka: W większości przypadków typy CLR, które są ustawione jako efekt uboczny stosowania zewnętrznych schematu, są używane do zapewnienia dostępu do wartości węzła. Jednakże mogą wystąpić sytuacje, w których możesz chcieć sprawdzić typ skojarzony z określonym schematem zastosowane do dokumentu XML. Na przykład możesz przeszukiwać dokumentu XML wyodrębniania wszystkie elementy, które są określane mieć zawartości typu "PurchaseOrder" zgodnie ze schematu. Takie informacje o typie można ustawić tylko w wyniku sprawdzania poprawności schematu i tych informacji jest dostępny za pośrednictwem <xref:System.Xml.XPath.XPathNavigator.XmlType%2A> i <xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A> właściwości <xref:System.Xml.XPath.XPathNavigator> klasy. Aby uzyskać więcej informacji zobacz sekcję wpis zestaw informacji o weryfikacji schematu (PSVI) poniżej.  
  
- Odbicie określonego typu język schematu: W innych przypadkach można uzyskać dodatkowe szczegóły dotyczące określonego schematu zastosowane do dokumentu XML. Na przykład podczas odczytywania pliku XML, które mogą mają zostać wyodrębnione `maxOccurs` atrybutu dla każdej prawidłowym węzłem w dokumencie XML w celu wykonywania niektórych obliczeń niestandardowych. Ponieważ te informacje jest ustawiona tylko za pośrednictwem weryfikacji schematu, jest dostępny za pośrednictwem <xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A> właściwość <xref:System.Xml.XPath.XPathNavigator> klasy. Aby uzyskać więcej informacji zobacz sekcję wpis zestaw informacji o weryfikacji schematu (PSVI) poniżej.  
  
## <a name="xpathnavigator-typed-accessors"></a>Klasy XPathNavigator Typizowane metody dostępu  
 W poniższej tabeli przedstawiono różne właściwości i metod <xref:System.Xml.XPath.XPathNavigator> klasę, która może służyć do dostępu do informacji o typie, informacje o węźle.  
  
|Właściwość|Opis|  
|--------------|-----------------|  
|<xref:System.Xml.XPath.XPathNavigator.XmlType%2A>|Zawiera informacje o typie schematu XML dla węzła, jeśli jest on prawidłowy.|  
|<xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A>|Zawiera zestaw informacji sprawdzania poprawności schematu wpis węzła, który zostanie dodany po weryfikacji. W tym informacje o typie schematu XML, a także informacje o ważności.|  
|<xref:System.Xml.XPath.XPathNavigator.ValueType%2A>|Typ CLR typizowaną wartość węzła.|  
|<xref:System.Xml.XPath.XPathNavigator.TypedValue%2A>|Zawartość węzła CLR jeden lub więcej wartości o typie jest najlepiej dopasowany do typu schematu XML węzła.|  
|<xref:System.Xml.XPath.XPathNavigator.ValueAsBoolean%2A>|<xref:System.String> Rzutować wartości bieżącego węzła <xref:System.Boolean> wartości z regułami rzutowania XPath 2.0 `xs:boolean`.|  
|<xref:System.Xml.XPath.XPathNavigator.ValueAsDateTime%2A>|<xref:System.String> Rzutować wartości bieżącego węzła <xref:System.DateTime> wartości z regułami rzutowania XPath 2.0 `xs:datetime`.|  
|<xref:System.Xml.XPath.XPathNavigator.ValueAsDouble%2A>|<xref:System.String> Rzutować wartości bieżącego węzła <xref:System.Double> wartości z regułami rzutowania XPath 2.0 `xsd:double`.|  
|<xref:System.Xml.XPath.XPathNavigator.ValueAsInt%2A>|<xref:System.String> Rzutować wartości bieżącego węzła <xref:System.Int32> wartości z regułami rzutowania XPath 2.0 `xs:integer`.|  
|<xref:System.Xml.XPath.XPathNavigator.ValueAsLong%2A>|<xref:System.String> Rzutować wartości bieżącego węzła <xref:System.Int64> wartości z regułami rzutowania XPath 2.0 `xs:integer`.|  
|<xref:System.Xml.XPath.XPathNavigator.ValueAs%2A>|Zawartość węzła rzutowany na typ docelowy zgodnie z regułami rzutowania XPath 2.0.|  
  
 Aby uzyskać więcej informacji o mapowaniu z wbudowanych typów schematu na typy CLR, zobacz [Obsługa typu w ramach klas zestawu System.Xml](../../../../docs/standard/data/xml/type-support-in-the-system-xml-classes.md).  
  
## <a name="the-post-schema-validation-infoset-psvi"></a>Zestaw w informacji sprawdzania poprawności schematu Post (PSVI)  
 Procesor schematu XML akceptuje zestaw informacji XML, jako dane wejściowe i konwertuje ją na wpis schematu sprawdzania poprawności zestaw informacji (PSVI). PSVI jest oryginalnym danych wejściowych XML zestaw informacji z nowe elementy informacje dodane i nowy właściwości dodawane do istniejących elementów informacji. Istnieją trzy klasy szerokiego informacji dodawanych do zestaw informacji XML w PSVI, które są udostępniane przez <xref:System.Xml.XPath.XPathNavigator>.  
  
1. Wyniki sprawdzania poprawności: Informacje dotyczące tego, czy element lub atrybut został pomyślnie zweryfikowany czy nie. To jest uwidaczniany przez <xref:System.Xml.Schema.IXmlSchemaInfo.Validity%2A> właściwość <xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A> właściwość <xref:System.Xml.XPath.XPathNavigator> klasy.  
  
2. Domyślne informacje: Wskazanie, czy wartość elementu lub atrybutu uzyskano przy użyciu wartości domyślnych, określona w schemacie, czy nie. To jest uwidaczniany przez <xref:System.Xml.Schema.IXmlSchemaInfo.IsDefault%2A> właściwość <xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A> właściwość <xref:System.Xml.XPath.XPathNavigator> klasy.  
  
3. Deklaracje typów: Odwołania do składników schematu, które mogą być definicje typów lub elementów i atrybutów deklaracji. <xref:System.Xml.XPath.XPathNavigator.XmlType%2A> Właściwość <xref:System.Xml.XPath.XPathNavigator> zawiera informacje o określonym typie węzła, jeśli jest on prawidłowy. W przypadku ważności węzeł jest nieznany, takie jak kiedy została zweryfikowana następnie później edytować. a następnie <xref:System.Xml.XPath.XPathNavigator.XmlType%2A> właściwość jest ustawiona na `null` , ale informacje o typie jest nadal dostępne z poziomu różnych właściwości obiektu <xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A> właściwość <xref:System.Xml.XPath.XPathNavigator> klasy.  
  
 W poniższym przykładzie pokazano, korzystając z informacji udostępnianych przez zestaw wpis schematu sprawdzania poprawności informacji <xref:System.Xml.XPath.XPathNavigator>.  
  
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
  
 Przykład pobiera również `books.xsd` schematu jako dane wejściowe.  
  
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
  
## <a name="obtain-typed-values-using-valueas-properties"></a>Uzyskiwanie wartości Typizowane, za pomocą właściwości ValueAs  
 Wpisane wartości węzła mogą być pobierane, uzyskując dostęp do <xref:System.Xml.XPath.XPathNavigator.TypedValue%2A> właściwość <xref:System.Xml.XPath.XPathNavigator>. W niektórych przypadkach można przekonwertować wartości typizowane węzła do innego typu. Typowym przykładem jest można uzyskać wartość liczbową z węzła XML. Na przykład rozważmy następujący dokument XML niezweryfikowanych i bez typu.  
  
```xml  
<books>  
    <book>  
        <title>Title</title>  
        <price>10.00</price>  
        <published>2003-12-31</published>  
    </book>  
</books>  
```  
  
 Jeśli <xref:System.Xml.XPath.XPathNavigator> jest ustawiony na `price` elementu <xref:System.Xml.XPath.XPathNavigator.XmlType%2A> będzie właściwość `null`, <xref:System.Xml.XPath.XPathNavigator.ValueType%2A> będzie właściwość <xref:System.String>i <xref:System.Xml.XPath.XPathNavigator.TypedValue%2A> właściwość może być ciągiem `10.00`.  
  
 Będzie jednak nadal możliwe do wyodrębnienia wartości jako wartość liczbową przy użyciu <xref:System.Xml.XPath.XPathItem.ValueAs%2A>, <xref:System.Xml.XPath.XPathNavigator.ValueAsDouble%2A>, <xref:System.Xml.XPath.XPathNavigator.ValueAsInt%2A>, lub <xref:System.Xml.XPath.XPathNavigator.ValueAsLong%2A> metody i właściwości. W poniższym przykładzie pokazano wykonywania takich rzutowanie za pomocą <xref:System.Xml.XPath.XPathItem.ValueAs%2A> metody.  
  
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
  
 Aby uzyskać więcej informacji o mapowaniu z wbudowanych typów schematu na typy CLR, zobacz [Obsługa typu w ramach klas zestawu System.Xml](../../../../docs/standard/data/xml/type-support-in-the-system-xml-classes.md).  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- [Obsługa typu w ramach klas zestawu System.Xml](../../../../docs/standard/data/xml/type-support-in-the-system-xml-classes.md)
- [Przetwarzanie danych XML przy użyciu modelu danych XPath](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)
- [Nawigacja po zestawie węzłów przy użyciu klasy XPathNavigator](../../../../docs/standard/data/xml/node-set-navigation-using-xpathnavigator.md)
- [Nawigacja po atrybutach i przestrzeni nazw węzła przy użyciu klasy XPathNavigator](../../../../docs/standard/data/xml/attribute-and-namespace-node-navigation-using-xpathnavigator.md)
- [Wyodrębnianie danych XML przy użyciu klasy XPathNavigator](../../../../docs/standard/data/xml/extract-xml-data-using-xpathnavigator.md)
