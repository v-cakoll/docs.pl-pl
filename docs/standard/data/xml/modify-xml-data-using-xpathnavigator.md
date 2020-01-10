---
title: Modyfikowanie danych XML przy użyciu klasy XPathNavigator
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
ms.assetid: 03a7c5a1-b296-4af4-b209-043c958dc0a5
ms.openlocfilehash: 906de1ded4961b7c67d48a010555d139df97cded
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75710638"
---
# <a name="modify-xml-data-using-xpathnavigator"></a>Modyfikowanie danych XML przy użyciu klasy XPathNavigator
Klasa <xref:System.Xml.XPath.XPathNavigator> zawiera zestaw metod służących do modyfikowania węzłów i wartości w dokumencie XML. Aby można było korzystać z tych metod, obiekt <xref:System.Xml.XPath.XPathNavigator> musi być edytowalny, oznacza to, że jego właściwość <xref:System.Xml.XPath.XPathNavigator.CanEdit%2A> musi być `true`.  
  
 <xref:System.Xml.XPath.XPathNavigator> obiektów, które mogą edytować dokument XML, są tworzone przez metodę <xref:System.Xml.XmlDocument.CreateNavigator%2A> klasy <xref:System.Xml.XmlDocument>. <xref:System.Xml.XPath.XPathNavigator> obiektów utworzonych przez klasę <xref:System.Xml.XPath.XPathDocument> są tylko do odczytu, a każda próba użycia metod edycji obiektu <xref:System.Xml.XPath.XPathNavigator> utworzonego przez obiekt <xref:System.Xml.XPath.XPathDocument> powoduje <xref:System.NotSupportedException>.  
  
 Aby uzyskać więcej informacji na temat tworzenia edytowalnych obiektów <xref:System.Xml.XPath.XPathNavigator>, zobacz [odczytywanie danych XML przy użyciu XPathDocument i XmlDocument](../../../../docs/standard/data/xml/reading-xml-data-using-xpathdocument-and-xmldocument.md).  
  
## <a name="modifying-nodes"></a>Modyfikowanie węzłów  
 Prostą techniką zmiany wartości węzła jest użycie <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> i <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> metod klasy <xref:System.Xml.XPath.XPathNavigator>.  
  
 Poniższa tabela zawiera listę efektów tych metod dla różnych typów węzłów.  
  
|<xref:System.Xml.XPath.XPathNodeType>|Zmieniono dane|  
|---------------------------------------------------------------------------------------------------------------------------------------------|------------------|  
|<xref:System.Xml.XPath.XPathNodeType.Root>|Nieobsługiwane.|  
|<xref:System.Xml.XPath.XPathNodeType.Element>|Zawartość elementu.|  
|<xref:System.Xml.XPath.XPathNodeType.Attribute>|Wartość atrybutu.|  
|<xref:System.Xml.XPath.XPathNodeType.Text>|Zawartość tekstowa.|  
|<xref:System.Xml.XPath.XPathNodeType.ProcessingInstruction>|Zawartość, z wyłączeniem celu.|  
|<xref:System.Xml.XPath.XPathNodeType.Comment>|Zawartość komentarza.|  
|<xref:System.Xml.XPath.XPathNodeType.Namespace>|Nieobsługiwane.|  
  
> [!NOTE]
> Edytowanie węzłów <xref:System.Xml.XPath.XPathNodeType.Namespace> lub węzła <xref:System.Xml.XPath.XPathNodeType.Root> nie jest obsługiwane.  
  
 Klasa <xref:System.Xml.XPath.XPathNavigator> udostępnia również zestaw metod służących do wstawiania i usuwania węzłów. Aby uzyskać więcej informacji na temat wstawiania i usuwania węzłów z dokumentu XML, zobacz temat [Wstawianie danych XML przy użyciu klasy XPathNavigator](../../../../docs/standard/data/xml/insert-xml-data-using-xpathnavigator.md) i [usuwanie danych XML przy użyciu klasy XPathNavigator](../../../../docs/standard/data/xml/remove-xml-data-using-xpathnavigator.md) .  
  
### <a name="modifying-untyped-values"></a>Modyfikowanie wartości niewpisanych  
 Metoda <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> po prostu wstawia wartość nietypu `string` przekazaną jako parametr jako wartość węzła, w którym obiekt <xref:System.Xml.XPath.XPathNavigator> jest obecnie umieszczony. Wartość jest wstawiana bez żadnego typu lub bez weryfikowania, czy nowa wartość jest prawidłowa zgodnie z typem węzła, jeśli dostępne są informacje o schemacie.  
  
 W poniższym przykładzie metoda <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> służy do aktualizowania wszystkich elementów `price` w pliku `contosoBooks.xml`.  
  
 [!code-cpp[XPathNavigatorMethods#47](../../../../samples/snippets/cpp/VS_Snippets_Data/XPathNavigatorMethods/CPP/xpathnavigatormethods.cpp#47)]
 [!code-csharp[XPathNavigatorMethods#47](../../../../samples/snippets/csharp/VS_Snippets_Data/XPathNavigatorMethods/CS/xpathnavigatormethods.cs#47)]
 [!code-vb[XPathNavigatorMethods#47](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XPathNavigatorMethods/VB/xpathnavigatormethods.vb#47)]  
  
 Przykład pobiera `contosoBooks.xml` plik jako dane wejściowe.  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
### <a name="modifying-typed-values"></a>Modyfikowanie wpisanych wartości  
 Gdy typ węzła jest typem prostym schematu XML W3C, Nowa wartość wstawiona przez metodę <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> jest sprawdzana względem aspektów typu prostego przed ustawieniem wartości. Jeśli nowa wartość jest nieprawidłowa w zależności od typu węzła (na przykład ustawienie wartości `-1` dla elementu, którego typem jest `xs:positiveInteger`), powoduje wyjątek.  
  
 Poniższy przykład próbuje zmienić wartość elementu `price` pierwszego elementu `book` w pliku `contosoBooks.xml` na wartość <xref:System.DateTime>. Ponieważ typ schematu XML elementu `price` jest zdefiniowany jako `xs:decimal` w plikach `contosoBooks.xsd`, spowoduje to wyjątek.  
  
```vb  
Dim settings As XmlReaderSettings = New XmlReaderSettings()  
settings.Schemas.Add("http://www.contoso.com/books", "contosoBooks.xsd")  
settings.ValidationType = ValidationType.Schema  
  
Dim reader As XmlReader = XmlReader.Create("contosoBooks.xml", settings)  
  
Dim document As XmlDocument = New XmlDocument()  
document.Load(reader)  
Dim navigator As XPathNavigator = document.CreateNavigator()  
  
navigator.MoveToChild("bookstore", "http://www.contoso.com/books")  
navigator.MoveToChild("book", "http://www.contoso.com/books")  
navigator.MoveToChild("price", "http://www.contoso.com/books")  
  
navigator.SetTypedValue(DateTime.Now)  
```  
  
```csharp  
XmlReaderSettings settings = new XmlReaderSettings();  
settings.Schemas.Add("http://www.contoso.com/books", "contosoBooks.xsd");  
settings.ValidationType = ValidationType.Schema;  
  
XmlReader reader = XmlReader.Create("contosoBooks.xml", settings);  
  
XmlDocument document = new XmlDocument();  
document.Load(reader);  
XPathNavigator navigator = document.CreateNavigator();  
  
navigator.MoveToChild("bookstore", "http://www.contoso.com/books");  
navigator.MoveToChild("book", "http://www.contoso.com/books");  
navigator.MoveToChild("price", "http://www.contoso.com/books");  
  
navigator.SetTypedValue(DateTime.Now);  
```  
  
 Przykład pobiera `contosoBooks.xml` plik jako dane wejściowe.  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
 Przykład pobiera również `contosoBooks.xsd` jako dane wejściowe.  
  
 [!code-xml[XPathXMLExamples#3](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xsd#3)]  
  
#### <a name="the-effects-of-editing-strongly-typed-xml-data"></a>Efekty edytowania danych XML o jednoznacznie określonym typie  
 Klasa <xref:System.Xml.XPath.XPathNavigator> używa schematu W3C XML jako podstawy do opisywania XML o jednoznacznie określonym typie. Elementy i atrybuty mogą być opatrzone adnotacją z informacjami o typie na podstawie walidacji dokumentu XML schematu W3C. Elementy, które mogą zawierać inne elementy lub atrybuty, są nazywane typami złożonymi, natomiast te, które mogą zawierać tylko tekstową zawartość, są nazywane typami prostymi.  
  
> [!NOTE]
> Atrybuty mogą mieć tylko typy proste.  
  
 Element lub atrybut może być uznawany za schemat-prawidłowy, jeśli jest zgodny ze wszystkimi regułami specyficznymi dla definicji typu. Element, który ma `xs:int` typu prostego, musi zawierać wartość liczbową z przedziału od-2147483648 do 2147483647, aby była prawidłowa dla schematu. W przypadku typów złożonych, walidacja schematu elementu jest zależna od poprawności schematu, jego elementów podrzędnych i atrybutów. W tym przypadku, jeśli element jest prawidłowy względem definicji typu złożonego, wszystkie jego elementy podrzędne i atrybuty są prawidłowe względem ich definicji typów. Podobnie, jeśli nawet jeden z elementów podrzędnych lub atrybutów elementu jest nieprawidłowy względem definicji typu lub ma nieznane ważność, element jest również nieprawidłowy lub nieznanej ważności.  
  
 Uwzględniając, że ważność elementu jest zależna od ważności jego elementów podrzędnych i atrybutów, modyfikacje w wyniku zmiany ważności elementu, jeśli były wcześniej ważne. W przypadku, gdy elementy podrzędne lub atrybuty elementu są wstawiane, aktualizowane lub usuwane, ważność elementu jest nieznana. Jest to reprezentowane przez właściwość <xref:System.Xml.Schema.IXmlSchemaInfo.Validity%2A> elementu właściwości <xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A>, która jest ustawiana na <xref:System.Xml.Schema.XmlSchemaValidity.NotKnown>. Co więcej, ten efekt kaskadowo umieszcza w całym dokumencie XML, ponieważ ważność elementu nadrzędnego elementu (i jego elementu nadrzędnego itd.) również będzie nieznana.  
  
 Aby uzyskać więcej informacji na temat walidacji schematu i klasy <xref:System.Xml.XPath.XPathNavigator>, zobacz [Walidacja schematu przy użyciu elementu XPathNavigator](../../../../docs/standard/data/xml/schema-validation-using-xpathnavigator.md).  
  
### <a name="modifying-attributes"></a>Modyfikowanie atrybutów  
 Metody <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> i <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> mogą służyć do modyfikowania węzłów atrybutów nietypowych i typów, jak również inne typy węzłów wymienione w sekcji "Modyfikowanie węzłów".  
  
 Poniższy przykład zmienia wartość atrybutu `genre` pierwszego elementu `book` w pliku `books.xml`.  
  
```vb  
Dim document As XmlDocument = New XmlDocument()  
document.Load("books.xml")  
Dim navigator As XPathNavigator = document.CreateNavigator()  
  
navigator.MoveToChild("bookstore", String.Empty)  
navigator.MoveToChild("book", String.Empty)  
navigator.MoveToAttribute("genre", String.Empty)  
  
navigator.SetValue("non-fiction")  
  
navigator.MoveToRoot()  
Console.WriteLine(navigator.OuterXml)  
```  
  
```csharp  
XmlDocument document = new XmlDocument();  
document.Load("books.xml");  
XPathNavigator navigator = document.CreateNavigator();  
  
navigator.MoveToChild("bookstore", String.Empty);  
navigator.MoveToChild("book", String.Empty);  
navigator.MoveToAttribute("genre", String.Empty);  
  
navigator.SetValue("non-fiction");  
  
navigator.MoveToRoot();  
Console.WriteLine(navigator.OuterXml);  
```  
  
 Aby uzyskać więcej informacji na temat metod <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> i <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A>, zobacz sekcję "Modyfikowanie wartości niewpisanych" i "Modyfikowanie wartości wpisanych".  
  
## <a name="innerxml-and-outerxml-properties"></a>Właściwości InnerXml i OuterXml  
 Właściwości <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> i <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> klasy <xref:System.Xml.XPath.XPathNavigator> zmieniają znaczniki XML dla węzłów, w których jest obecnie umieszczony obiekt <xref:System.Xml.XPath.XPathNavigator>.  
  
 Właściwość <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> zmienia znaczniki XML węzłów podrzędnych, a obiekt <xref:System.Xml.XPath.XPathNavigator> jest obecnie umieszczony w przeanalizowanej zawartości danego `string`XML. Podobnie Właściwość <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> zmienia znaczniki XML węzłów podrzędnych, a obiekt <xref:System.Xml.XPath.XPathNavigator> jest obecnie umieszczony, a także bieżący węzeł.  
  
 W poniższym przykładzie zastosowano Właściwość <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A>, aby zmodyfikować wartość elementu `price` i wstawić nowy atrybut `discount` dla pierwszego elementu `book` w pliku `contosoBooks.xml`.  
  
```vb  
Dim document As XmlDocument = New XmlDocument()  
document.Load("contosoBooks.xml");  
Dim navigator As XPathNavigator = document.CreateNavigator()  
  
navigator.MoveToChild("bookstore", "http://www.contoso.com/books")  
navigator.MoveToChild("book", "http://www.contoso.com/books")  
navigator.MoveToChild("price", "http://www.contoso.com/books")  
  
navigator.OuterXml = "<price discount=\"0\">10.99</price>"  
  
navigator.MoveToRoot()  
Console.WriteLine(navigator.OuterXml)  
```  
  
```csharp  
XmlDocument document = new XmlDocument();  
document.Load("contosoBooks.xml");  
XPathNavigator navigator = document.CreateNavigator();  
  
navigator.MoveToChild("bookstore", "http://www.contoso.com/books");  
navigator.MoveToChild("book", "http://www.contoso.com/books");  
navigator.MoveToChild("price", "http://www.contoso.com/books");  
  
navigator.OuterXml = "<price discount=\"0\">10.99</price>";  
  
navigator.MoveToRoot();  
Console.WriteLine(navigator.OuterXml);  
```  
  
 Przykład pobiera `contosoBooks.xml` plik jako dane wejściowe.  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
## <a name="modifying-namespace-nodes"></a>Modyfikowanie węzłów przestrzeni nazw  
 W Document Object Model (DOM) deklaracje przestrzeni nazw są traktowane tak, jakby były zwykłymi atrybutami, które można wstawiać, aktualizować i usuwać. Klasa <xref:System.Xml.XPath.XPathNavigator> nie zezwala na wykonywanie takich operacji w węzłach przestrzeni nazw, ponieważ zmiana wartości węzła przestrzeni nazw może zmienić tożsamość elementów i atrybutów w zakresie węzła przestrzeni nazw, jak pokazano w poniższym przykładzie.  
  
```xml  
<root xmlns="http://www.contoso.com">  
    <child />  
</root>  
```  
  
 Jeśli powyższy przykład XML zostanie zmieniony w następujący sposób, to efektywnie zmienia nazwę każdego elementu w dokumencie, ponieważ wartość identyfikatora URI każdego elementu jest zmieniana.  
  
```xml  
<root xmlns="urn:contoso.com">  
    <child />  
</root>  
```  
  
 Wstawianie węzłów przestrzeni nazw, które nie powodują konfliktu z deklaracjami przestrzeni nazw w zakresie, w którym są wstawiane, jest dozwolone przez klasę <xref:System.Xml.XPath.XPathNavigator>. W takim przypadku deklaracje przestrzeni nazw nie są deklarowane w niższych zakresach dokumentu XML i nie powoduje zmiany nazwy, jak pokazano w poniższym przykładzie.  
  
```xml  
<root xmlns:a="http://www.contoso.com">  
    <parent>  
        <a:child />  
    </parent>  
</root>  
```  
  
 Jeśli przykładowy kod XML został zmieniony w następujący sposób, deklaracje przestrzeni nazw są poprawnie propagowane w dokumencie XML poniżej zakresu innej deklaracji przestrzeni nazw.  
  
```xml  
<root xmlns:a="http://www.contoso.com">  
    <parent a:parent-id="1234" xmlns:a="http://www.contoso.com/parent-id">  
        <a:child xmlns:a="http://www.contoso.com/">  
    </parent>  
</root>  
```  
  
 W powyższym przykładzie XML atrybut `a:parent-id` jest wstawiany dla elementu `parent` w przestrzeni nazw `http://www.contoso.com/parent-id`. Metoda <xref:System.Xml.XPath.XPathNavigator.CreateAttribute%2A> jest używana do wstawiania atrybutu podczas umieszczania w elemencie `parent`. Deklaracja przestrzeni nazw `http://www.contoso.com` jest automatycznie wstawiana przez klasę <xref:System.Xml.XPath.XPathNavigator>, aby zachować spójność reszty dokumentu XML.  
  
## <a name="modifying-entity-reference-nodes"></a>Modyfikowanie węzłów odwołań do jednostek  
 Węzły odwołania jednostki w obiekcie <xref:System.Xml.XmlDocument> są tylko do odczytu i nie można ich edytować przy użyciu klas <xref:System.Xml.XPath.XPathNavigator> lub <xref:System.Xml.XmlNode>. Każda próba zmodyfikowania węzła odwołania do jednostki powoduje wystąpienie <xref:System.InvalidOperationException>.  
  
## <a name="modifying-xsinil-nodes"></a>Modyfikowanie węzłów xsi: nil  
 Zalecenie dotyczące schematu W3C XML wprowadza koncepcję elementu, który jest nillable. Gdy element jest nillable, możliwe jest, aby element nie miał zawartości i nadal był prawidłowy. Koncepcja elementu nillable jest podobna do koncepcji obiektu, który jest `null`. Główną różnicą jest to, że nie można uzyskać dostępu do obiektu `null` w jakikolwiek sposób, podczas gdy element `xsi:nil` nadal ma właściwości, takie jak atrybuty, do których można uzyskać dostęp, ale nie ma zawartości (elementów podrzędnych lub tekstu). Istnienie atrybutu `xsi:nil` z wartością `true` dla elementu w dokumencie XML jest używane do wskazywania, że element nie ma zawartości.  
  
 Jeśli obiekt <xref:System.Xml.XPath.XPathNavigator> jest używany do dodawania zawartości do prawidłowego elementu z atrybutem `xsi:nil` o wartości `true`, wartość atrybutu `xsi:nil` jest ustawiona na `false`.  
  
> [!NOTE]
> Jeśli zawartość elementu z atrybutem `xsi:nil` ustawionym na `false` jest usuwana, wartość atrybutu nie zostanie zmieniona na `true`.  
  
## <a name="saving-an-xml-document"></a>Zapisywanie dokumentu XML  
 Zapisywanie zmian wprowadzonych w obiekcie <xref:System.Xml.XmlDocument> w wyniku metod edycji opisanych w tym temacie jest wykonywane przy użyciu metod klasy <xref:System.Xml.XmlDocument>. Aby uzyskać więcej informacji na temat zapisywania zmian wprowadzonych w obiekcie <xref:System.Xml.XmlDocument>, zobacz [Zapisywanie i pisanie dokumentu](../../../../docs/standard/data/xml/saving-and-writing-a-document.md).  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- [Przetwarzanie danych XML przy użyciu modelu danych XPath](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)
- [Wstawianie danych XML przy użyciu klasy XPathNavigator](../../../../docs/standard/data/xml/insert-xml-data-using-xpathnavigator.md)
- [Usuwanie danych XML przy użyciu klasy XPathNavigator](../../../../docs/standard/data/xml/remove-xml-data-using-xpathnavigator.md)
