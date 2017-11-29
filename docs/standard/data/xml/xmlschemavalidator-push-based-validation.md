---
title: "Sprawdzanie poprawności XmlSchemaValidator wypychania"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 911d4460-dd91-4958-85b2-2ca3299f9ec6
caps.latest.revision: "4"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 5a78321b289dd19c5086223856fd3142f1aef75c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="xmlschemavalidator-push-based-validation"></a>Sprawdzanie poprawności XmlSchemaValidator wypychania
<xref:System.Xml.Schema.XmlSchemaValidator> Klasy udostępnia mechanizm wydajne, wysokiej wydajności, aby sprawdzić poprawność danych XML względem schematów XML w sposób wypychania. Na przykład <xref:System.Xml.Schema.XmlSchemaValidator> klasa umożliwia sprawdzenie poprawności XML typu infoset sprawdzonych w miejscu, bez konieczności serializować go jako dokument XML i ponownej analizy dokumentu za pomocą sprawdzania poprawności modułu odczytującego XML.  
  
 <xref:System.Xml.Schema.XmlSchemaValidator> Klasa może być używana w zaawansowanych scenariuszach, takich jak tworzenie aparaty weryfikacji za pośrednictwem niestandardowych źródeł danych XML lub jako sposobu tworzenia sprawdzania poprawności Edytor XML.  
  
 Poniżej przedstawiono przykład użycia <xref:System.Xml.Schema.XmlSchemaValidator> klasy do sprawdzania poprawności `contosoBooks.xml` pliku przed `contosoBooks.xsd` schematu. W przykładzie użyto <xref:System.Xml.Serialization.XmlSerializer> klasy do deserializacji `contosoBooks.xml` plik i przekazać wartość węzłów do metody <xref:System.Xml.Schema.XmlSchemaValidator> klasy.  
  
> [!NOTE]
>  W tym przykładzie jest używane w sekcjach tego tematu.  
  
 [!code-csharp[XmlSchemaValidatorExamples#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaValidatorExamples/CS/XmlSchemaValidatorExamples.cs#1)]
 [!code-vb[XmlSchemaValidatorExamples#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaValidatorExamples/VB/XmlSchemaValidatorExamples.vb#1)]  
  
 Przykład przyjmuje `contosoBooks.xml` pliku jako dane wejściowe.  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
 Przykład również przyjmuje `contosoBooks.xsd` jako danych wejściowych.  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<xs:schema attributeFormDefault="unqualified" elementFormDefault="qualified" targetNamespace="http://www.contoso.com/books" xmlns:xs="http://www.w3.org/2001/XMLSchema">  
    <xs:element name="bookstore">  
        <xs:complexType>  
            <xs:sequence>  
                <xs:element maxOccurs="unbounded" name="book">  
                    <xs:complexType>  
                        <xs:sequence>  
                            <xs:element name="title" type="xs:string" />  
                            <xs:element name="author">  
                                <xs:complexType>  
                                    <xs:sequence>  
                                        <xs:element minOccurs="0" name="name" type="xs:string" />  
                                        <xs:element minOccurs="0" name="first-name" type="xs:string" />  
                                        <xs:element minOccurs="0" name="last-name" type="xs:string" />  
                                    </xs:sequence>  
                                </xs:complexType>  
                            </xs:element>  
                            <xs:element name="price" type="xs:decimal" />  
                        </xs:sequence>  
                        <xs:attribute name="genre" type="xs:string" use="required" />  
                        <xs:attribute name="publicationdate" type="xs:date" use="required" />  
                        <xs:attribute name="ISBN" type="xs:string" use="required" />  
                    </xs:complexType>  
                </xs:element>  
            </xs:sequence>  
        </xs:complexType>  
    </xs:element>  
</xs:schema>  
```  
  
## <a name="validating-xml-data-using-xmlschemavalidator"></a>Sprawdzanie poprawności danych XML przy użyciu XmlSchemaValidator  
 Aby rozpocząć sprawdzanie poprawności XML typu infoset, należy najpierw zainicjować nowe wystąpienie klasy <xref:System.Xml.Schema.XmlSchemaValidator> przy użyciu <xref:System.Xml.Schema.XmlSchemaValidator.%23ctor%2A> konstruktora.  
  
 <xref:System.Xml.Schema.XmlSchemaValidator.%23ctor%2A> Konstruktor pobiera <xref:System.Xml.XmlNameTable>, <xref:System.Xml.Schema.XmlSchemaSet>, i <xref:System.Xml.XmlNamespaceManager> obiektów jako parametry, a także <xref:System.Xml.Schema.XmlSchemaValidationFlags> wartość jako parametr. <xref:System.Xml.XmlNameTable> Obiektu służy do rozproszyć ciągi dobrze znanych przestrzeni nazw jak przestrzeń nazw schematu, przestrzeni nazw XML i tak dalej i jest przekazywana do <xref:System.Xml.Schema.XmlSchemaDatatype.ParseValue%2A> metody podczas sprawdzania poprawności prostej zawartości. <xref:System.Xml.Schema.XmlSchemaSet> Obiekt zawiera schematów XML, używany do sprawdzania poprawności XML typu infoset sprawdzonych. <xref:System.Xml.XmlNamespaceManager> Obiekt jest używany do rozpoznawania nazw podczas sprawdzania poprawności. <xref:System.Xml.Schema.XmlSchemaValidationFlags> Wartość jest używana do wyłączenia niektórych funkcji sprawdzania poprawności.  
  
 Aby uzyskać więcej informacji na temat <xref:System.Xml.Schema.XmlSchemaValidator.%23ctor%2A> konstruktora, zobacz <xref:System.Xml.Schema.XmlSchemaValidator> klasy dokumentacji.  
  
### <a name="initializing-validation"></a>Inicjowanie weryfikacji  
 Po <xref:System.Xml.Schema.XmlSchemaValidator> obiekt został skonstruowany, istnieją dwie przeciążony <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> metody używane do zainicjowania stan <xref:System.Xml.Schema.XmlSchemaValidator> obiektu. Poniżej przedstawiono dwa <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> metody.  
  
-   <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType>  
  
-   <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType>  
  
 Wartość domyślna <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType> inicjuje — metoda <xref:System.Xml.Schema.XmlSchemaValidator> obiektu do jego początkowy stan i przeciążone <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType> metody pobierającej <xref:System.Xml.Schema.XmlSchemaObject> jako parametr inicjuje <xref:System.Xml.Schema.XmlSchemaValidator> obiekt początkowy stan dla częściowego Sprawdzanie poprawności.  
  
 Zarówno <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> metody może zostać wywołany tylko natychmiast po <xref:System.Xml.Schema.XmlSchemaValidator> obiekt został skonstruowany lub po wywołaniu <xref:System.Xml.Schema.XmlSchemaValidator.EndValidation%2A>.  
  
 Przykład <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType> metody, zapoznaj się z przykładem w wprowadzenie. Aby uzyskać więcej informacji na temat <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> metody, zobacz <xref:System.Xml.Schema.XmlSchemaValidator> klasy dokumentacji.  
  
#### <a name="partial-validation"></a>Częściowego sprawdzania poprawności  
 <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType> Metody pobierającej <xref:System.Xml.Schema.XmlSchemaObject> jako parametr inicjuje <xref:System.Xml.Schema.XmlSchemaValidator> obiekt początkowy stan dla częściowego sprawdzania poprawności.  
  
 W poniższym przykładzie <xref:System.Xml.Schema.XmlSchemaObject> inicjowane dla przy użyciu częściowego sprawdzania poprawności <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType> metody. `orderNumber` Elementu schematu jest przekazywana przez wybranie elementu schematu przez <xref:System.Xml.XmlQualifiedName> w <xref:System.Xml.Schema.XmlSchemaObjectTable> kolekcji zwróconej przez <xref:System.Xml.Schema.XmlSchemaSet.GlobalElements%2A> właściwość <xref:System.Xml.Schema.XmlSchemaSet> obiektu. <xref:System.Xml.Schema.XmlSchemaValidator> Obiektu następnie weryfikuje ten konkretny element.  
  
```vb  
Dim schemaSet As XmlSchemaSet = New XmlSchemaSet()  
schemaSet.Add(Nothing, "schema.xsd")  
schemaSet.Compile()  
Dim nameTable As NameTable = New NameTable()  
Dim manager As XmlNamespaceManager = New XmlNamespaceManager(nameTable)  
  
Dim validator As XmlSchemaValidator = New XmlSchemaValidator(nameTable, schemaSet, manager, XmlSchemaValidationFlags.None)  
validator.Initialize(schemaSet.GlobalElements.Item(New XmlQualifiedName("orderNumber")))  
  
validator.ValidateElement("orderNumber", "", Nothing)  
validator.ValidateEndOfAttributes(Nothing)  
validator.ValidateText("123")  
validator.ValidateEndElement(Nothing)  
```  
  
```csharp  
XmlSchemaSet schemaSet = new XmlSchemaSet();  
schemaSet.Add(null, "schema.xsd");  
schemaSet.Compile();  
NameTable nameTable = new NameTable();  
XmlNamespaceManager manager = new XmlNamespaceManager(nameTable);  
  
XmlSchemaValidator validator = new XmlSchemaValidator(nameTable, schemaSet, manager, XmlSchemaValidationFlags.None);  
validator.Initialize(schemaSet.GlobalElements[new XmlQualifiedName("orderNumber")]);  
  
validator.ValidateElement("orderNumber", "", null);  
validator.ValidateEndOfAttributes(null);  
validator.ValidateText("123");  
validator.ValidateEndElement(null);  
```  
  
 Przykład przyjmuje następujące schematu XML jako dane wejściowe.  
  
 `<xs:schema xmlns:xs="http://www.w3.org/2001/XMLSchema">`  
  
 `<xs:element name="orderNumber" type="xs:int" />`  
  
 `</xs:schema>`  
  
 Aby uzyskać więcej informacji na temat <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> metody, zobacz <xref:System.Xml.Schema.XmlSchemaValidator> klasy dokumentacji.  
  
### <a name="adding-additional-schemas"></a>Dodawanie dodatkowych schematów  
 <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> Metody <xref:System.Xml.Schema.XmlSchemaValidator> klasa jest używana do dodawania schematu XML do zestawu używany podczas weryfikacji schematów. <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> — Metoda można symulować efekt napotkania wbudowanego schematu XML w XML typu infoset sprawdzonych sprawdzania poprawności.  
  
> [!NOTE]
>  Docelowa przestrzeń nazw <xref:System.Xml.Schema.XmlSchema> parametru nie może być zgodna z dowolny element lub atrybut już występujących <xref:System.Xml.Schema.XmlSchemaValidator> obiektu.  
>   
>  Jeśli <xref:System.Xml.Schema.XmlSchemaValidationFlags.ProcessInlineSchema?displayProperty=nameWithType> wartość nie została przekazana jako parametr <xref:System.Xml.Schema.XmlSchemaValidator.%23ctor%2A> konstruktora, <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> — metoda nie działa.  
  
 Wynik <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> metoda zależy od bieżącego kontekstu węzła XML sprawdzania poprawności. Aby uzyskać więcej informacji o kontekstach weryfikacji zobacz sekcję "Kontekst weryfikacji" tego tematu.  
  
 Aby uzyskać więcej informacji na temat <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> metody, zobacz <xref:System.Xml.Schema.XmlSchemaValidator> klasy dokumentacji.  
  
### <a name="validating-elements-attributes-and-content"></a>Sprawdzanie poprawności elementy, atrybuty i zawartości  
 <xref:System.Xml.Schema.XmlSchemaValidator> Klasa udostępnia kilka metod używany do sprawdzania poprawności elementy, atrybuty i zawartość obiektu XML typu infoset względem schematów XML. W poniższej tabeli opisano każdy z tych metod.  
  
|Metoda|Opis|  
|------------|-----------------|  
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A>|Weryfikuje nazwy elementu w bieżącym kontekście.|  
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>|Sprawdza poprawność atrybutu w bieżącym kontekście element lub <xref:System.Xml.Schema.XmlSchemaAttribute> przekazano obiekt jako parametr <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> metody.|  
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndOfAttributes%2A>|Sprawdza, czy wszystkie wymagane atrybuty w kontekście elementu są przedstawić i przygotowuje <xref:System.Xml.Schema.XmlSchemaValidator> obiektu do weryfikacji zawartość elementu podrzędnego elementu.|  
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A>|Sprawdza, czy tekst jest dozwolona w bieżącym kontekście elementu i akumuluje tekst sprawdzania poprawności, jeśli bieżący element ma prostą zawartością.|  
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateWhitespace%2A>|Sprawdza, czy biały znak jest dozwolona w bieżącym kontekście elementu i akumuluje biały znak do weryfikacji, czy bieżący element ma prostą zawartością.|  
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A>|Sprawdza, czy zawartości tekstowej elementu jest prawidłowa zgodnie z jego typu danych dla elementów z zawartością proste i weryfikuje, czy zawartość bieżącego elementu jest pełny dla elementów z zawartością złożoną.|  
|<xref:System.Xml.Schema.XmlSchemaValidator.SkipToEndElement%2A>|Pomija weryfikację bieżącego elementu zawartości i przygotowuje <xref:System.Xml.Schema.XmlSchemaValidator> obiektu do weryfikacji zawartości w kontekście elementu nadrzędnego.|  
|<xref:System.Xml.Schema.XmlSchemaValidator.EndValidation%2A>|Kończy się sprawdzanie poprawności i ograniczenia tożsamości w całym dokumencie XML sprawdza, czy <xref:System.Xml.Schema.XmlSchemaValidationFlags.ProcessIdentityConstraints> ustawiono opcję sprawdzania poprawności.|  
  
> [!NOTE]
>  <xref:System.Xml.Schema.XmlSchemaValidator> Klasa ma zdefiniowany przejście wymusza sekwencji i wystąpienie wywołań do każdej z metod opisanych w poprzedniej tabeli. Przejście stanu określonego <xref:System.Xml.Schema.XmlSchemaValidator> klasy jest opisany w sekcji "Przejście stanu XmlSchemaValidator" tego tematu.  
  
 Na przykład metody używane do sprawdzania poprawności elementy, atrybuty i zawartość XML typu infoset Zobacz przykład w poprzedniej sekcji. Aby uzyskać więcej informacji na temat tych metod, zobacz <xref:System.Xml.Schema.XmlSchemaValidator> klasy dokumentacji.  
  
#### <a name="validating-content-using-an-xmlvaluegetter"></a>Sprawdzanie poprawności zawartości przy użyciu XmlValueGetter  
 <xref:System.Xml.Schema.XmlValueGetter> `delegate` Może służyć do przekazywania wartości atrybutu, tekst lub białe węzły jako typy środowiska uruchomieniowego języka wspólnego (CLR) zgodny z typem języka definicji schematu XML (XSD) atrybutów, tekst lub węzeł biały znak. <xref:System.Xml.Schema.XmlValueGetter> `delegate` Jest przydatna, jeśli wartość CLR atrybut, tekst lub węzeł biały znak jest już dostępny i pozwala uniknąć kosztów konwersja na `string` , a następnie ponownej analizy go ponownie do weryfikacji.  
  
 <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>, <xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A>, I <xref:System.Xml.Schema.XmlSchemaValidator.ValidateWhitespace%2A> metody jest przeciążona i zaakceptuj wartość atrybutu, tekst lub białe węzły `string` lub <xref:System.Xml.Schema.XmlValueGetter> `delegate`.  
  
 Następujące metody <xref:System.Xml.Schema.XmlSchemaValidator> zaakceptować klasy <xref:System.Xml.Schema.XmlValueGetter> `delegate` jako parametr.  
  
-   <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>  
  
-   <xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A>  
  
-   <xref:System.Xml.Schema.XmlSchemaValidator.ValidateWhitespace%2A>  
  
 Poniżej przedstawiono przykład <xref:System.Xml.Schema.XmlValueGetter> `delegate` pobranych z <xref:System.Xml.Schema.XmlSchemaValidator> przykład klasy w wprowadzenie. <xref:System.Xml.Schema.XmlValueGetter> `delegate` Zwraca wartość atrybutu jako <xref:System.DateTime> obiektu. Aby to sprawdzić <xref:System.DateTime> obiektu zwróconego przez <xref:System.Xml.Schema.XmlValueGetter>, <xref:System.Xml.Schema.XmlSchemaValidator> obiektu najpierw konwertuje ją na właściwość ValueType (ValueType jest domyślne mapowanie CLR dla typu XSD) dla typu danych atrybutu, a następnie kontroli zestawów reguł skonwertowany wartość.  
  
```vb  
Shared dateTimeGetterContent As Object  
  
Shared Function dateTimeGetterHandle() As Object  
    Return dateTimeGetterContent  
End Function  
  
Shared Function dateTimeGetter(ByVal dateTime As DateTime) As XmlValueGetter  
    dateTimeGetterContent = dateTime  
    Return New XmlValueGetter(AddressOf dateTimeGetterHandle)  
End Function  
```  
  
```csharp  
static object dateTimeGetterContent;  
  
static object dateTimeGetterHandle()  
{  
    return dateTimeGetterContent;  
}  
  
static XmlValueGetter dateTimeGetter(DateTime dateTime)  
{  
    dateTimeGetterContent = dateTime;  
    return new XmlValueGetter(dateTimeGetterHandle);  
}  
```  
  
 Aby uzyskać pełny przykład <xref:System.Xml.Schema.XmlValueGetter> `delegate`, zapoznaj się z przykładem w wprowadzenie. Aby uzyskać więcej informacji na temat <xref:System.Xml.Schema.XmlValueGetter> `delegate`, zobacz <xref:System.Xml.Schema.XmlValueGetter>, i <xref:System.Xml.Schema.XmlSchemaValidator> klasy dokumentacji.  
  
#### <a name="post-schema-validation-information"></a>Po-Schema-sprawdzania poprawności — informacje  
 <xref:System.Xml.Schema.XmlSchemaInfo> Klasa reprezentuje część po-Schema-— informacje o weryfikacji węzła XML zweryfikowany przez <xref:System.Xml.Schema.XmlSchemaValidator> klasy. Różnych metod <xref:System.Xml.Schema.XmlSchemaValidator> zaakceptować klasy <xref:System.Xml.Schema.XmlSchemaInfo> obiektu jako opcjonalny (`null`) `out` parametru.  
  
 Po pomyślnym zweryfikowaniem, właściwości <xref:System.Xml.Schema.XmlSchemaInfo> obiektu są konfigurowane przy użyciu wyniki weryfikacji. Na przykład po pomyślnym zweryfikowaniem przy użyciu atrybutu <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> metody <xref:System.Xml.Schema.XmlSchemaInfo> obiektu użytkownika (Jeśli określono) <xref:System.Xml.Schema.XmlSchemaInfo.SchemaAttribute%2A>, <xref:System.Xml.Schema.XmlSchemaInfo.SchemaType%2A>, <xref:System.Xml.Schema.XmlSchemaInfo.MemberType%2A>, i <xref:System.Xml.Schema.XmlSchemaInfo.Validity%2A> właściwości są ustawione z wynikami weryfikacji .  
  
 Następujące <xref:System.Xml.Schema.XmlSchemaValidator> metody klasy <xref:System.Xml.Schema.XmlSchemaInfo> obiektu jako parametr wyjściowy.  
  
-   <xref:System.Xml.Schema.XmlSchemaValidator.SkipToEndElement%2A>  
  
-   <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>  
  
-   <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>  
  
-   <xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A>  
  
-   <xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A>  
  
-   <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A>  
  
-   <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A>  
  
-   <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndOfAttributes%2A>  
  
 Aby uzyskać pełny przykład <xref:System.Xml.Schema.XmlSchemaInfo> klasy, zapoznaj się z przykładem w wprowadzenie. Aby uzyskać więcej informacji na temat <xref:System.Xml.Schema.XmlSchemaInfo> , zobacz <xref:System.Xml.Schema.XmlSchemaInfo> klasy dokumentacji.  
  
### <a name="retrieving-expected-particles-attributes-and-unspecified-default-attributes"></a>Trwa pobieranie oczekiwanego cząstki, atrybuty i nieokreślony domyślne atrybuty  
 <xref:System.Xml.Schema.XmlSchemaValidator> Klasa udostępnia <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A>, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A>, i <xref:System.Xml.Schema.XmlSchemaValidator.GetUnspecifiedDefaultAttributes%2A> metod można pobrać oczekiwanego cząstki, atrybuty i nieokreślony domyślne atrybuty w bieżącym kontekście sprawdzania poprawności.  
  
#### <a name="retrieving-expected-particles"></a>Trwa pobieranie cząstki oczekiwany  
 <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> Metoda zwraca tablicę <xref:System.Xml.Schema.XmlSchemaParticle> obiektów zawierających oczekiwanego cząstek w bieżącym kontekście elementu. Nieprawidłowa cząstki, które mogą być zwrócone przez <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> metody są wystąpieniami klasy <xref:System.Xml.Schema.XmlSchemaElement> i <xref:System.Xml.Schema.XmlSchemaAny> klasy.  
  
 Gdy compositor dla modelu zawartości jest `xs:sequence`, jest zwracana tylko dalej cząstki w sekwencji. Jeśli compositor dla modelu zawartości jest `xs:all` lub `xs:choice`, a następnie zwracane są wszystkie prawidłowe cząstki, które można wykonać w bieżącym kontekście elementu.  
  
> [!NOTE]
>  Jeśli <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> metoda jest wywoływana natychmiast po wywołaniu <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> metody <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> metoda zwraca wszystkie elementy globalne.  
  
 Na przykład w języku definicji schematu XML (XSD) schematu i XML dokumentu poniżej, po weryfikacji `book` elementu `book` element jest bieżącym kontekście elementu. <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> Metoda zwraca tablicę zawierającą pojedynczy <xref:System.Xml.Schema.XmlSchemaElement> reprezentujący obiekt `title` elementu. Gdy jest kontekst weryfikacji `title` elementu <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> metoda zwraca pustą tablicę. Jeśli <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> metoda jest wywoływana po wykonaniu `title` element została zweryfikowana, ale przed wysłaniem `description` został zweryfikowany element, zwraca tablicę zawierającą pojedynczy <xref:System.Xml.Schema.XmlSchemaElement> reprezentujący obiekt `description` elementu. Jeśli <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> metoda jest wywoływana po wykonaniu `description` element został zweryfikowany, a następnie zwraca tablicę zawierającą pojedynczy <xref:System.Xml.Schema.XmlSchemaAny> obiekt reprezentujący symbol wieloznaczny.  
  
```vb  
Dim reader As XmlReader =  XmlReader.Create("input.xml")   
  
Dim schemaSet As XmlSchemaSet =  New XmlSchemaSet()   
schemaSet.Add(Nothing, "schema.xsd")  
Dim manager As XmlNamespaceManager =  New XmlNamespaceManager(reader.NameTable)   
  
Dim validator As XmlSchemaValidator =  New XmlSchemaValidator(reader.NameTable,schemaSet,manager,XmlSchemaValidationFlags.None)  
validator.Initialize()  
  
validator.ValidateElement("book", "", Nothing)  
  
validator.ValidateEndOfAttributes(Nothing)  
For Each element As XmlSchemaElement In validator.GetExpectedParticles()  
    Console.WriteLine(element.Name)  
Next  
  
validator.ValidateElement("title", "", Nothing)  
validator.ValidateEndOfAttributes(Nothing)  
For Each element As XmlSchemaElement In validator.GetExpectedParticles()  
    Console.WriteLine(element.Name)  
Next  
validator.ValidateEndElement(Nothing)  
  
For Each element As XmlSchemaElement In validator.GetExpectedParticles()  
    Console.WriteLine(element.Name)  
Next  
  
validator.ValidateElement("description", "", Nothing)  
validator.ValidateEndOfAttributes(Nothing)  
validator.ValidateEndElement(Nothing)  
  
For Each particle As XmlSchemaParticle In validator.GetExpectedParticles()  
    Console.WriteLine(particle.GetType())  
Next  
  
validator.ValidateElement("namespace", "", Nothing)  
validator.ValidateEndOfAttributes(Nothing)  
validator.ValidateEndElement(Nothing)  
  
validator.ValidateEndElement(Nothing)  
```  
  
```csharp  
XmlReader reader = XmlReader.Create("input.xml");  
  
XmlSchemaSet schemaSet = new XmlSchemaSet();  
schemaSet.Add(null, "schema.xsd");  
XmlNamespaceManager manager = new XmlNamespaceManager(reader.NameTable);  
  
XmlSchemaValidator validator = new XmlSchemaValidator(reader.NameTable, schemaSet, manager, XmlSchemaValidationFlags.None);  
validator.Initialize();  
  
validator.ValidateElement("book", "", null);  
  
validator.ValidateEndOfAttributes(null);  
foreach (XmlSchemaElement element in validator.GetExpectedParticles())  
{  
    Console.WriteLine(element.Name);  
}  
  
validator.ValidateElement("title", "", null);  
validator.ValidateEndOfAttributes(null);  
foreach (XmlSchemaElement element in validator.GetExpectedParticles())  
{  
    Console.WriteLine(element.Name);  
}  
validator.ValidateEndElement(null);  
  
foreach (XmlSchemaElement element in validator.GetExpectedParticles())  
{  
    Console.WriteLine(element.Name);  
}  
  
validator.ValidateElement("description", "", null);  
validator.ValidateEndOfAttributes(null);  
validator.ValidateEndElement(null);  
  
foreach (XmlSchemaParticle particle in validator.GetExpectedParticles())  
{  
    Console.WriteLine(particle.GetType());  
}  
  
validator.ValidateElement("namespace", "", null);  
validator.ValidateEndOfAttributes(null);  
validator.ValidateEndElement(null);  
  
validator.ValidateEndElement(null);  
```  
  
 Przykład przyjmuje następujące XML jako dane wejściowe.  
  
 `<xs:schema xmlns:xs="http://www.w3c.org/2001/XMLSchema">`  
  
 `<xs:element name="book">`  
  
 `<xs:sequence>`  
  
 `<xs:element name="title" type="xs:string" />`  
  
 `<xs:element name="description" type="xs:string" />`  
  
 `<xs:any processContent="lax" maxOccurs="unbounded" />`  
  
 `</xs:sequence>`  
  
 `</xs:element>`  
  
 `</xs:schema>`  
  
 Przykład przyjmuje następujące schematu XSD jako dane wejściowe.  
  
 `<book>`  
  
 `<title>My Book</title>`  
  
 `<description>My Book's Description</description>`  
  
 `<namespace>System.Xml.Schema</namespace>`  
  
 `</book>`  
  
> [!NOTE]
>  Wyniki <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A>, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A>, i <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> metody <xref:System.Xml.Schema.XmlSchemaValidator> klasy są zależne od bieżącego kontekstu sprawdzania poprawności. Aby uzyskać więcej informacji zobacz sekcję "Kontekst weryfikacji" tego tematu.  
  
 Przykład <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> metody, zapoznaj się z przykładem w wprowadzenie. Aby uzyskać więcej informacji na temat <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> metody, zobacz <xref:System.Xml.Schema.XmlSchemaValidator> klasy dokumentacji.  
  
#### <a name="retrieving-expected-attributes"></a>Pobieranie oczekiwanych atrybutów  
 <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> Metoda zwraca tablicę <xref:System.Xml.Schema.XmlSchemaAttribute> obiektów zawierających oczekiwane atrybuty w bieżącym kontekście elementu.  
  
 Na przykład w przykładzie wprowadzenie <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> metoda służy do pobierania wszystkich atrybutów `book` elementu.  
  
 Jeśli należy wywołać <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> metody natychmiast po <xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A> metody, zwracane są wszystkie atrybuty, które mogą występować w dokumencie XML. Jednak jeśli wywołujesz <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> metody po co najmniej jednego wywołania <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> metody, zwracane są atrybuty, które nie została sprawdzona dla bieżącego elementu.  
  
> [!NOTE]
>  Wyniki <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A>, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A>, i <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> metody <xref:System.Xml.Schema.XmlSchemaValidator> klasy są zależne od bieżącego kontekstu sprawdzania poprawności. Aby uzyskać więcej informacji zobacz sekcję "Kontekst weryfikacji" tego tematu.  
  
 Przykład <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> metody, zapoznaj się z przykładem w wprowadzenie. Aby uzyskać więcej informacji na temat <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> metody, zobacz <xref:System.Xml.Schema.XmlSchemaValidator> klasy dokumentacji.  
  
#### <a name="retrieving-unspecified-default-attributes"></a>Podczas pobierania atrybutów nieokreślonych domyślnych  
 <xref:System.Xml.Schema.XmlSchemaValidator.GetUnspecifiedDefaultAttributes%2A> Metoda wypełnia <xref:System.Collections.ArrayList> określenia <xref:System.Xml.Schema.XmlSchemaAttribute> obiektów wszystkich atrybutów z wartościami domyślnymi, które nie zostały wcześniej zatwierdzone przy użyciu <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> metody w kontekście elementu. <xref:System.Xml.Schema.XmlSchemaValidator.GetUnspecifiedDefaultAttributes%2A> Metoda powinna być wywoływana po wywołaniu <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> metody dla każdego atrybutu w kontekście elementu. <xref:System.Xml.Schema.XmlSchemaValidator.GetUnspecifiedDefaultAttributes%2A> Metodę do określenia atrybutów domyślnych ma zostać wstawiony do sprawdzania poprawności dokumentu XML.  
  
 Aby uzyskać więcej informacji na temat <xref:System.Xml.Schema.XmlSchemaValidator.GetUnspecifiedDefaultAttributes%2A> metody, zobacz <xref:System.Xml.Schema.XmlSchemaValidator> klasy dokumentacji.  
  
### <a name="handling-schema-validation-events"></a>Obsługa zdarzeń sprawdzania poprawności schematu  
 Schemat sprawdzania poprawności ostrzeżeń i błędów napotkanych podczas sprawdzania poprawności, które są obsługiwane przez <xref:System.Xml.Schema.XmlSchemaValidator.ValidationEventHandler> zdarzenie <xref:System.Xml.Schema.XmlSchemaValidator> klasy.  
  
 Ostrzeżenia dotyczące sprawdzania poprawności schematu mają <xref:System.Xml.Schema.XmlSeverityType> wartość <xref:System.Xml.Schema.XmlSeverityType.Warning> i błędy sprawdzania poprawności schematu <xref:System.Xml.Schema.XmlSeverityType> wartość <xref:System.Xml.Schema.XmlSeverityType.Error>. Jeśli nie <xref:System.Xml.Schema.XmlSchemaValidator.ValidationEventHandler> został przypisany, <xref:System.Xml.Schema.XmlSchemaValidationException> jest generowany dla wszystkich błędów sprawdzania poprawności schematu z <xref:System.Xml.Schema.XmlSeverityType> wartość <xref:System.Xml.Schema.XmlSeverityType.Error>. Jednak <xref:System.Xml.Schema.XmlSchemaValidationException> nie zgłoszono ostrzeżeń sprawdzania poprawności schematu z <xref:System.Xml.Schema.XmlSeverityType> wartość <xref:System.Xml.Schema.XmlSeverityType.Warning>.  
  
 Poniżej przedstawiono przykład <xref:System.Xml.Schema.ValidationEventHandler> odbierająca schemat sprawdzania poprawności ostrzeżeń i błędów napotkanych podczas sprawdzania poprawności schematu z przykład wprowadzenia.  
  
```vb  
Shared Sub SchemaValidationEventHandler(ByVal sender As Object, ByVal e As ValidationEventArgs)  
  
    Select Case e.Severity  
        Case XmlSeverityType.Error  
            Console.WriteLine(vbCrLf & "Error: {0}", e.Message)  
            Exit Sub  
        Case XmlSeverityType.Warning  
            Console.WriteLine(vbCrLf & "Warning: {0}", e.Message)  
            Exit Sub  
    End Select  
End Sub  
```  
  
```csharp  
static void SchemaValidationEventHandler(object sender, ValidationEventArgs e)  
{  
    switch (e.Severity)  
    {  
        case XmlSeverityType.Error:  
            Console.WriteLine("\nError: {0}", e.Message);  
            break;  
        case XmlSeverityType.Warning:  
            Console.WriteLine("\nWarning: {0}", e.Message);  
            break;  
    }  
}  
```  
  
 Aby uzyskać pełny przykład <xref:System.Xml.Schema.ValidationEventHandler>, zapoznaj się z przykładem w wprowadzenie. Aby uzyskać więcej informacji, zobacz <xref:System.Xml.Schema.XmlSchemaInfo> klasy dokumentacji.  
  
## <a name="xmlschemavalidator-state-transition"></a>Przejście stanu XmlSchemaValidator  
 <xref:System.Xml.Schema.XmlSchemaValidator> Klasa ma zdefiniowany przejście wymusza sekwencji i wystąpienie wywołań wykonanych dla każdej z metod używany do sprawdzania poprawności elementy, atrybuty i zawartość XML typu infoset.  
  
 W poniższej tabeli opisano zmiany stanu z <xref:System.Xml.Schema.XmlSchemaValidator> klasy, a sekwencji i wystąpieniem wywołania metody, które można podjąć w każdym stanie.  
  
|Stan|przejścia|  
|-----------|----------------|  
|Sprawdzanie poprawności|<xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A>(<xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> &#124; TopLevel*)<xref:System.Xml.Schema.XmlSchemaValidator.EndValidation%2A>|  
|TopLevel|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateWhitespace%2A>&#124; <xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A> &#124; Element|  
|Element|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A><xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>* (<xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndOfAttributes%2A> Zawartości\*)? <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A> &#124;<br /><br /> <xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A> <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>\* <xref:System.Xml.Schema.XmlSchemaValidator.SkipToEndElement%2A> &#124;<br /><br /> <xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A><xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> \* <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndOfAttributes%2A> Zawartości\* <xref:System.Xml.Schema.XmlSchemaValidator.SkipToEndElement%2A> &#124;|  
|Zawartość|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateWhitespace%2A>&#124; <xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A> &#124; Element|  
  
> [!NOTE]
>  <xref:System.InvalidOperationException> Jest generowany przez każdą z metod w powyższej tabeli, gdy wywołanie do metody jest przeprowadzane w Nieprawidłowa sekwencja zgodnie z bieżącym stanem <xref:System.Xml.Schema.XmlSchemaValidator> obiektu.  
  
 Powyższej tabeli przejścia stanu używa znaki interpunkcyjne, aby opisać metody i inne stany, które można wywołać dla każdego stanu przejście stanu <xref:System.Xml.Schema.XmlSchemaValidator> klasy. Symbole używane są tego samego symbole znaleziono w odwołaniu standardów XML definicji typu dla dokumentu (DTD).  
  
 W poniższej tabeli opisano wpływ metody interpunkcyjnych w powyższej tabeli przejścia stanu i innych stany, które można wywołać dla każdego stanu w przejście stanu <xref:System.Xml.Schema.XmlSchemaValidator> klasy.  
  
|Symbol|Opis|  
|------------|-----------------|  
|&#124;|Można wywołać metody lub stan (jeden przed pasku) lub jeden po nim.|  
|?|Stan, poprzedzający znak zapytania lub metoda jest opcjonalne, ale jeśli jest to go można wywołać tylko raz.|  
|*|Metoda lub stan poprzedzający * symbol jest opcjonalna i może zostać wywołany więcej niż raz.|  
  
## <a name="validation-context"></a>Kontekst weryfikacji  
 Metody <xref:System.Xml.Schema.XmlSchemaValidator> klasa służy do sprawdzania poprawności elementy, atrybuty i zawartość XML typu infoset, Zmień kontekst weryfikacji <xref:System.Xml.Schema.XmlSchemaValidator> obiektu. Na przykład <xref:System.Xml.Schema.XmlSchemaValidator.SkipToEndElement%2A> metody Pomija weryfikację bieżącego elementu zawartości i przygotowuje <xref:System.Xml.Schema.XmlSchemaValidator> obiektu sprawdzanie zawartości w kontekście elementu nadrzędnego; jest odpowiednikiem pomijanie sprawdzania poprawności dla wszystkie elementy podrzędne bieżącego elementu a następnie podczas wywoływania <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A> metody.  
  
 Wyniki <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A>, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A>, i <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> metody <xref:System.Xml.Schema.XmlSchemaValidator> klasy są zależne od bieżącego kontekstu sprawdzania poprawności.  
  
 W poniższej tabeli opisano wyników wywołania tych metod po wywołaniu metody jednej z metod <xref:System.Xml.Schema.XmlSchemaValidator> klasy używany do sprawdzania poprawności elementy, atrybuty i zawartość XML typu infoset.  
  
|Metoda|GetExpectedParticles|GetExpectedAttributes|AddSchema|  
|------------|--------------------------|---------------------------|---------------|  
|<xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A>|Jeśli domyślna <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> metoda jest wywoływana, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> zwraca tablicę zawierającą wszystkie elementy globalne.<br /><br /> Jeśli przeciążone <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> metody pobierającej <xref:System.Xml.Schema.XmlSchemaObject> jako parametr nosi nazwę zainicjować częściowego sprawdzania poprawności elementu <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> zwraca tylko element, do którego <xref:System.Xml.Schema.XmlSchemaValidator> obiekt został zainicjowany.|Jeśli domyślna <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> metoda jest wywoływana, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> zwraca pustą tablicę.<br /><br /> Jeśli przeciążenia <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> metody pobierającej <xref:System.Xml.Schema.XmlSchemaObject> jako parametr nosi nazwę zainicjować częściowej walidacji atrybutu <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> zwraca tylko atrybut, do którego <xref:System.Xml.Schema.XmlSchemaValidator> obiekt został zainicjowany.|Dodaje schemat <xref:System.Xml.Schema.XmlSchemaSet> z <xref:System.Xml.Schema.XmlSchemaValidator> obiektu, jeśli nie ma ono żadnych błędów przetwarzania wstępnego.|  
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A>|Jeśli element kontekstu jest prawidłowy, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> zwraca sekwencję elementów oczekiwanych jako elementy podrzędne elementu kontekstu.<br /><br /> Jeśli element kontekstu jest nieprawidłowy, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> zwraca pustą tablicę.|Jeśli element kontekstu jest prawidłowy, a nie wywołanie <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> zostało wcześniej ustanowione, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> zwraca listę wszystkich atrybutów zdefiniowanych w elemencie kontekstu.<br /><br /> Jeśli niektóre atrybuty zostały zatwierdzone, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> zwraca listę pozostałe atrybuty do sprawdzenia poprawności.<br /><br /> Jeśli element kontekstu jest nieprawidłowy, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> zwraca pustą tablicę.|Taka sama jak powyżej.|  
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>|Jeśli atrybut kontekstu nie jest atrybutem najwyższego poziomu, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> zwraca pustą tablicę.<br /><br /> W przeciwnym razie <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> zwraca sekwencję elementów oczekiwanych jako pierwszy element podrzędny elementu kontekstu.|Jeśli atrybut kontekstu nie jest atrybutem najwyższego poziomu, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> zwraca pustą tablicę.<br /><br /> W przeciwnym razie <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> zwraca listę pozostałych atrybutów, które mają być weryfikowane.|Taka sama jak powyżej.|  
|<xref:System.Xml.Schema.XmlSchemaValidator.GetUnspecifiedDefaultAttributes%2A>|<xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A>Zwraca sekwencję elementów oczekiwanych jako pierwszy element podrzędny elementu kontekstu.|<xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A>Zwraca listę atrybutów wymaganych i opcjonalnych, które mają jeszcze można sprawdzić poprawności elementu kontekstu.|Taka sama jak powyżej.|  
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndOfAttributes%2A>|<xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A>Zwraca sekwencję elementów oczekiwanych jako pierwszy element podrzędny elementu kontekstu.|<xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A>Zwraca pustą tablicę.|Taka sama jak powyżej.|  
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A>|Jeśli typ zawartości elementu kontekstu jest mieszany, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> zwraca sekwencję elementów w pozycji dalej.<br /><br /> Jeśli typ zawartości elementu kontekstu jest TextOnly lub jest pusta, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> zwraca pustą tablicę.<br /><br /> Jeśli typ zawartości elementu kontekstu jest ElementOnly, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> zwraca już wystąpił sekwencja elementy w pozycji dalej, ale błąd sprawdzania poprawności.|<xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A>Zwraca listę atrybutów niezweryfikowany elementu kontekstu.|Taka sama jak powyżej.|  
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateWhitespace%2A>|Jeśli odstępu kontekstu jest najwyższego poziomu odstępu <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> zwraca pustą tablicę.<br /><br /> W przeciwnym razie <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> metody zachowanie jest takie samo, jak w <xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A>.|Jeśli odstępu kontekstu jest najwyższego poziomu odstępu <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> zwraca pustą tablicę.<br /><br /> W przeciwnym razie <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> metody zachowanie jest takie samo, jak w <xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A>.|Taka sama jak powyżej.|  
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A>|<xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A>Zwraca sekwencję elementów oczekiwanych po elemencie kontekstu (możliwe elementów równorzędnych).|<xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A>Zwraca listę atrybutów niezweryfikowany elementu kontekstu.<br /><br /> Jeśli element kontekstu nie ma nadrzędnego następnie <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> zwraca pustą listę (element kontekstu jest elementem nadrzędnym bieżącego elementu, na którym <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A> została wywołana).|Taka sama jak powyżej.|  
|<xref:System.Xml.Schema.XmlSchemaValidator.SkipToEndElement%2A>|Taki sam jak <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A>.|Taki sam jak <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A>.|Taka sama jak powyżej.|  
|<xref:System.Xml.Schema.XmlSchemaValidator.EndValidation%2A>|Zwraca pustą tablicę.|Zwraca pustą tablicę.|Taka sama jak powyżej.|  
  
> [!NOTE]
>  Wartości zwracane przez różne właściwości <xref:System.Xml.Schema.XmlSchemaValidator> klasy nie zostały zmienione przez wywołanie metody, w powyższej tabeli.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Xml.Schema.XmlSchemaValidator>
