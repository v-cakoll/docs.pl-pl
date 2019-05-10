---
title: Weryfikacja oparta na wypchnięciach przy użyciu klasy XmlSchemaValidator
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 911d4460-dd91-4958-85b2-2ca3299f9ec6
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 8e2b6ca8ef04ad6ff637a59f03f3b4cf04cb06ad
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64615364"
---
# <a name="xmlschemavalidator-push-based-validation"></a>Weryfikacja oparta na wypchnięciach przy użyciu klasy XmlSchemaValidator
<xref:System.Xml.Schema.XmlSchemaValidator> Klasa udostępnia efektywny, wydajny mechanizm weryfikacji danych XML względem schematów XML w sposób, na podstawie wypychania. Na przykład <xref:System.Xml.Schema.XmlSchemaValidator> klasy umożliwia sprawdzenie poprawności XML zestaw informacji w miejscu, bez konieczności serializować go jako dokument XML, a następnie ponownej analizy dokumentu przy użyciu sprawdzania poprawności odczytującego XML.  
  
 <xref:System.Xml.Schema.XmlSchemaValidator> Klasy mogą być używane w zaawansowanych scenariuszach, takich jak tworzenie aparatów sprawdzania poprawności dla niestandardowych źródeł danych XML lub umożliwia tworzenie sprawdzania poprawności edytora XML.  
  
 Oto przykład użycia <xref:System.Xml.Schema.XmlSchemaValidator> klasy, aby sprawdzić poprawność `contosoBooks.xml` pliku względem `contosoBooks.xsd` schematu. W przykładzie użyto <xref:System.Xml.Serialization.XmlSerializer> klasy do deserializacji `contosoBooks.xml` pliku i przekazać wartość węzłów do metody <xref:System.Xml.Schema.XmlSchemaValidator> klasy.  
  
> [!NOTE]
>  W tym przykładzie jest używane w sekcjach tego tematu.  
  
 [!code-csharp[XmlSchemaValidatorExamples#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaValidatorExamples/CS/XmlSchemaValidatorExamples.cs#1)]
 [!code-vb[XmlSchemaValidatorExamples#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaValidatorExamples/VB/XmlSchemaValidatorExamples.vb#1)]  
  
 Przykład przyjmuje `contosoBooks.xml` pliku jako dane wejściowe.  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
 Przykład pobiera również `contosoBooks.xsd` jako dane wejściowe.  
  
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
  
## <a name="validating-xml-data-using-xmlschemavalidator"></a>Walidacja danych XML przy użyciu XmlSchemaValidator  
 Aby rozpocząć sprawdzanie poprawności zestaw informacji XML, najpierw należy zainicjować nowe wystąpienie klasy <xref:System.Xml.Schema.XmlSchemaValidator> przy użyciu <xref:System.Xml.Schema.XmlSchemaValidator.%23ctor%2A> konstruktora.  
  
 <xref:System.Xml.Schema.XmlSchemaValidator.%23ctor%2A> Konstruktor przyjmuje <xref:System.Xml.XmlNameTable>, <xref:System.Xml.Schema.XmlSchemaSet>, i <xref:System.Xml.XmlNamespaceManager> obiektów jako parametrów, a także <xref:System.Xml.Schema.XmlSchemaValidationFlags> wartość jako parametr. <xref:System.Xml.XmlNameTable> Obiekt jest używany do wyodrębnić dobrze znanych nazw ciągi, takie jak przestrzeń nazw schematu, przestrzeń nazw XML i tak dalej i jest przekazywany do <xref:System.Xml.Schema.XmlSchemaDatatype.ParseValue%2A> metody podczas sprawdzania poprawności prostej zawartości. <xref:System.Xml.Schema.XmlSchemaSet> Obiekt zawiera schematów XML, używany do sprawdzania poprawności zestaw informacji XML. <xref:System.Xml.XmlNamespaceManager> Obiekt jest używany do rozpoznawania nazw podczas sprawdzania poprawności. <xref:System.Xml.Schema.XmlSchemaValidationFlags> Wartość jest używana do wyłączenia niektórych funkcji sprawdzania poprawności.  
  
 Aby uzyskać więcej informacji na temat <xref:System.Xml.Schema.XmlSchemaValidator.%23ctor%2A> konstruktora, zobacz <xref:System.Xml.Schema.XmlSchemaValidator> klasy dokumentację referencyjną.  
  
### <a name="initializing-validation"></a>Inicjowanie weryfikacji  
 Po <xref:System.Xml.Schema.XmlSchemaValidator> obiekt został skonstruowany, istnieją dwie przeciążone <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> metody używane do zainicjowania stan <xref:System.Xml.Schema.XmlSchemaValidator> obiektu. Poniżej przedstawiono dwa <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> metody.  
  
- <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType>  
  
- <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType>  
  
 Wartość domyślna <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType> inicjuje metodę <xref:System.Xml.Schema.XmlSchemaValidator> obiekt do stanu początkowego i przeciążone <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType> metody, która przyjmuje <xref:System.Xml.Schema.XmlSchemaObject> jako parametr inicjuje <xref:System.Xml.Schema.XmlSchemaValidator> obiekt początkowy stan dla częściowego Sprawdzanie poprawności.  
  
 Zarówno <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> metody można wywołać tylko natychmiast po <xref:System.Xml.Schema.XmlSchemaValidator> został skonstruowany obiekt lub po wywołaniu <xref:System.Xml.Schema.XmlSchemaValidator.EndValidation%2A>.  
  
 Na przykład <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType> metody, zobacz przykład we wstępie. Aby uzyskać więcej informacji na temat <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> metody, zobacz <xref:System.Xml.Schema.XmlSchemaValidator> klasy dokumentację referencyjną.  
  
#### <a name="partial-validation"></a>Częściowej weryfikacji  
 <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType> Metody, która przyjmuje <xref:System.Xml.Schema.XmlSchemaObject> jako parametr inicjuje <xref:System.Xml.Schema.XmlSchemaValidator> obiekt początkowy stan dla częściowej weryfikacji.  
  
 W poniższym przykładzie <xref:System.Xml.Schema.XmlSchemaObject> inicjowane dla częściowej weryfikacji za pomocą <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType> metody. `orderNumber` Elementu schematu jest przekazywany przez wybranie elementu schematu za <xref:System.Xml.XmlQualifiedName> w <xref:System.Xml.Schema.XmlSchemaObjectTable> kolekcji zwróconej przez <xref:System.Xml.Schema.XmlSchemaSet.GlobalElements%2A> właściwość <xref:System.Xml.Schema.XmlSchemaSet> obiektu. <xref:System.Xml.Schema.XmlSchemaValidator> Obiektu następnie weryfikuje ten określony element.  
  
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
  
 Aby uzyskać więcej informacji na temat <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> metody, zobacz <xref:System.Xml.Schema.XmlSchemaValidator> klasy dokumentację referencyjną.  
  
### <a name="adding-additional-schemas"></a>Dodawanie schematów dodatkowych  
 <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> Metody <xref:System.Xml.Schema.XmlSchemaValidator> klasa jest używana do dodawania schematu XML do zestawu schematów używany podczas sprawdzania poprawności. <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> Metoda można symulować efekt napotkania wbudowanego schematu XML w zestaw informacji XML, sprawdzania poprawności.  
  
> [!NOTE]
>  Docelowy obszar nazw <xref:System.Xml.Schema.XmlSchema> parametru nie może być zgodna z nazwą dowolny element lub atrybut już napotykanych przez <xref:System.Xml.Schema.XmlSchemaValidator> obiektu.  
>   
>  Jeśli <xref:System.Xml.Schema.XmlSchemaValidationFlags.ProcessInlineSchema?displayProperty=nameWithType> wartość nie została przekazana jako parametr do <xref:System.Xml.Schema.XmlSchemaValidator.%23ctor%2A> konstruktora, <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> metoda nic nie robi.  
  
 Wynik <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> metoda zależy od bieżącego kontekstu węzła XML weryfikowana. Aby uzyskać więcej informacji o kontekstach sprawdzania poprawności zobacz sekcję "Kontekst weryfikacji" w tym temacie.  
  
 Aby uzyskać więcej informacji na temat <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> metody, zobacz <xref:System.Xml.Schema.XmlSchemaValidator> klasy dokumentację referencyjną.  
  
### <a name="validating-elements-attributes-and-content"></a>Sprawdzanie poprawności, elementy, atrybuty i zawartości  
 <xref:System.Xml.Schema.XmlSchemaValidator> Klasa udostępnia kilka metod sprawdzania poprawności, elementy, atrybuty i zawartości w zestaw informacji XML, względem schematów XML. W poniższej tabeli opisano każdy z tych metod.  
  
|Metoda|Opis|  
|------------|-----------------|  
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A>|Sprawdza poprawność nazwy elementu w bieżącym kontekście.|  
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>|Sprawdza poprawność atrybutu kontekst bieżącego elementu lub względem <xref:System.Xml.Schema.XmlSchemaAttribute> przekazano obiekt jako parametr do <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> metody.|  
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndOfAttributes%2A>|Sprawdza, czy wszystkie wymagane atrybuty w kontekście elementu są obecne i przygotowuje <xref:System.Xml.Schema.XmlSchemaValidator> obiektu do weryfikacji zawartość elementu podrzędnego elementu.|  
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A>|Sprawdza, czy tekst jest dozwolona w bieżącym kontekście elementu i gromadzi tekstu do sprawdzania poprawności, jeśli bieżący element ma zawartość, proste.|  
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateWhitespace%2A>|Sprawdza, czy odstępu, jest dozwolona w bieżącym kontekście elementu i gromadzi biały do weryfikacji, czy bieżący element posiada prostej zawartości.|  
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A>|Sprawdza, czy zawartości tekstowej elementu jest nieprawidłowa w kontekście jego typu danych dla elementów z zawartością prostą i sprawdza, czy zawartość bieżącego elementu jest ukończony dla elementów z zawartością złożoną.|  
|<xref:System.Xml.Schema.XmlSchemaValidator.SkipToEndElement%2A>|Pomija weryfikację bieżącej zawartości elementu i przygotowuje <xref:System.Xml.Schema.XmlSchemaValidator> obiektu, aby walidować zawartość w kontekście elementu nadrzędnego.|  
|<xref:System.Xml.Schema.XmlSchemaValidator.EndValidation%2A>|Kończy się sprawdzanie poprawności i sprawdza ograniczenia tożsamości na całego dokumentu XML, czy <xref:System.Xml.Schema.XmlSchemaValidationFlags.ProcessIdentityConstraints> ustawiono opcję sprawdzania poprawności.|  
  
> [!NOTE]
>  <xref:System.Xml.Schema.XmlSchemaValidator> Klasa ma zmianę stanu zdefiniowany, który wymusza kolejność i wystąpienie wywołania do każdej z metod opisanych w poprzedniej tabeli. Przejście stanu z określonego <xref:System.Xml.Schema.XmlSchemaValidator> klasy jest opisane w sekcji "XmlSchemaValidator przejście stanu" w tym temacie.  
  
 Na przykład metody używane do sprawdzania poprawności, elementy, atrybuty i zawartości w zestaw informacji XML Zobacz przykład w poprzedniej sekcji. Aby uzyskać więcej informacji o tych metodach, zobacz <xref:System.Xml.Schema.XmlSchemaValidator> klasy dokumentację referencyjną.  
  
#### <a name="validating-content-using-an-xmlvaluegetter"></a>Sprawdzanie poprawności zawartości przy użyciu XmlValueGetter  
 <xref:System.Xml.Schema.XmlValueGetter> `delegate` Może służyć do przekazywania wartości atrybutu, tekst lub węzły odstępu jako typy środowiska uruchomieniowego języka wspólnego (CLR) zgodny z typem języka definicji schematu XML (XSD) atrybutu, tekst lub węzeł odstępu. <xref:System.Xml.Schema.XmlValueGetter> `delegate` Jest przydatne, jeśli wartość CLR atrybut, tekst lub odstępu węzeł jest już dostępny i pozwala uniknąć kosztów podczas konwertowania go do `string` i następnie ponownej analizy go ponownie do sprawdzania poprawności.  
  
 <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>, <xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A>, I <xref:System.Xml.Schema.XmlSchemaValidator.ValidateWhitespace%2A> metody są przeciążone i zaakceptuj wartość atrybutu, tekst lub węzły odstępu jako `string` lub <xref:System.Xml.Schema.XmlValueGetter> `delegate`.  
  
 Następujące metody <xref:System.Xml.Schema.XmlSchemaValidator> zaakceptować klasy <xref:System.Xml.Schema.XmlValueGetter> `delegate` jako parametr.  
  
- <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>  
  
- <xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A>  
  
- <xref:System.Xml.Schema.XmlSchemaValidator.ValidateWhitespace%2A>  
  
 Poniżej przedstawiono przykład <xref:System.Xml.Schema.XmlValueGetter> `delegate` pobranych z <xref:System.Xml.Schema.XmlSchemaValidator> klasy przykładu we wprowadzeniu. <xref:System.Xml.Schema.XmlValueGetter> `delegate` Zwraca wartość atrybutu jako <xref:System.DateTime> obiektu. Aby to sprawdzić <xref:System.DateTime> obiektu zwróconego przez <xref:System.Xml.Schema.XmlValueGetter>, <xref:System.Xml.Schema.XmlSchemaValidator> obiektu najpierw konwertuje ją na właściwość ValueType (ValueType jest domyślne mapowanie środowiska CLR dla typu XSD) dla typu danych atrybutu, a następnie aspektami kontroli na przekonwertowany wartość.  
  
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
  
 Aby uzyskać pełny przykład <xref:System.Xml.Schema.XmlValueGetter> `delegate`, zobacz przykład we wstępie. Aby uzyskać więcej informacji na temat <xref:System.Xml.Schema.XmlValueGetter> `delegate`, zobacz <xref:System.Xml.Schema.XmlValueGetter>, i <xref:System.Xml.Schema.XmlSchemaValidator> klasy dokumentację referencyjną.  
  
#### <a name="post-schema-validation-information"></a>Post-Schema-Validation-Information  
 <xref:System.Xml.Schema.XmlSchemaInfo> Klasa reprezentuje niektóre odniesienie-Schema-weryfikacji — informacje o węzła XML zweryfikowany przez <xref:System.Xml.Schema.XmlSchemaValidator> klasy. Różnych metod <xref:System.Xml.Schema.XmlSchemaValidator> zaakceptować klasy <xref:System.Xml.Schema.XmlSchemaInfo> obiektu jako opcjonalny (`null`) `out` parametru.  
  
 Po pomyślnej weryfikacji, właściwości <xref:System.Xml.Schema.XmlSchemaInfo> obiektu są konfigurowane przy użyciu wyników weryfikacji. Na przykład po pomyślnej weryfikacji przy użyciu atrybutu <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> metody <xref:System.Xml.Schema.XmlSchemaInfo> obiekt użytkownika (Jeśli określono) <xref:System.Xml.Schema.XmlSchemaInfo.SchemaAttribute%2A>, <xref:System.Xml.Schema.XmlSchemaInfo.SchemaType%2A>, <xref:System.Xml.Schema.XmlSchemaInfo.MemberType%2A>, i <xref:System.Xml.Schema.XmlSchemaInfo.Validity%2A> właściwości są ustawiane przy użyciu wyników weryfikacji .  
  
 Następujące <xref:System.Xml.Schema.XmlSchemaValidator> akceptować metod klasy <xref:System.Xml.Schema.XmlSchemaInfo> obiektu jako parametru wyjściowego.  
  
- <xref:System.Xml.Schema.XmlSchemaValidator.SkipToEndElement%2A>  
  
- <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>  
  
- <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>  
  
- <xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A>  
  
- <xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A>  
  
- <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A>  
  
- <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A>  
  
- <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndOfAttributes%2A>  
  
 Aby uzyskać pełny przykład <xref:System.Xml.Schema.XmlSchemaInfo> klasy, zobacz przykładu we wprowadzeniu. Aby uzyskać więcej informacji na temat <xref:System.Xml.Schema.XmlSchemaInfo> klasy, zobacz <xref:System.Xml.Schema.XmlSchemaInfo> klasy dokumentację referencyjną.  
  
### <a name="retrieving-expected-particles-attributes-and-unspecified-default-attributes"></a>Trwa pobieranie oczekiwanego cząstek, atrybuty i atrybuty domyślne nieokreślony  
 <xref:System.Xml.Schema.XmlSchemaValidator> Klasa udostępnia <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A>, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A>, i <xref:System.Xml.Schema.XmlSchemaValidator.GetUnspecifiedDefaultAttributes%2A> metod, które można pobrać oczekiwanego cząstek, atrybuty i atrybuty domyślne nieokreślony w bieżącym kontekście sprawdzania poprawności.  
  
#### <a name="retrieving-expected-particles"></a>Trwa pobieranie cząstki oczekiwane  
 <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> Metoda zwraca tablicę <xref:System.Xml.Schema.XmlSchemaParticle> obiektów zawierających oczekiwanego cząstek w kontekst bieżącego elementu. Nieprawidłowa cząstek, które mogą być zwrócone przez <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> metody są wystąpieniami <xref:System.Xml.Schema.XmlSchemaElement> i <xref:System.Xml.Schema.XmlSchemaAny> klasy.  
  
 Gdy compositor dla modelu zawartości jest `xs:sequence`, zwracany jest tylko dalej cząstka w sekwencji. Jeśli compositor dla modelu zawartości jest `xs:all` lub `xs:choice`, a następnie zwracane są wszystkie cząstki prawidłowe, które można wykonać w bieżącym kontekście elementu.  
  
> [!NOTE]
>  Jeśli <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> metoda jest wywoływana natychmiast po wywołaniu <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> metody <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> metoda zwraca wszystkie elementy globalne.  
  
 Na przykład w języku definicji schematu XML (XSD) schematu i XML dokumentu poniżej, po upewnieniu się, `book` elementu `book` element jest kontekst bieżącego elementu. <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> Metoda zwraca tablicę zawierającą jeden <xref:System.Xml.Schema.XmlSchemaElement> obiekt reprezentujący `title` elementu. Gdy jest kontekst weryfikacji `title` elementu <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> metoda zwraca pustą tablicę. Jeśli <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> metoda jest wywoływana po `title` element został zweryfikowany, lecz przed `description` zweryfikowany element, zwraca tablicę zawierającą jeden <xref:System.Xml.Schema.XmlSchemaElement> obiekt reprezentujący `description` elementu. Jeśli <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> metoda jest wywoływana po `description` element został zweryfikowany, a następnie zwraca tablicę zawierającą pojedynczy <xref:System.Xml.Schema.XmlSchemaAny> obiekt reprezentujący symbol wieloznaczny.  
  
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
  
 Przykład przyjmuje następujący kod XML jako dane wejściowe.  
  
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
>  Wyniki <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A>, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A>, i <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> metody <xref:System.Xml.Schema.XmlSchemaValidator> klasy są uzależnione od bieżącego kontekstu sprawdzania poprawności. Aby uzyskać więcej informacji zobacz sekcję "Kontekst weryfikacji" tego tematu.  
  
 Na przykład <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> metody, zobacz przykład we wstępie. Aby uzyskać więcej informacji na temat <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> metody, zobacz <xref:System.Xml.Schema.XmlSchemaValidator> klasy dokumentację referencyjną.  
  
#### <a name="retrieving-expected-attributes"></a>Pobieranie atrybutów oczekiwane  
 <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> Metoda zwraca tablicę <xref:System.Xml.Schema.XmlSchemaAttribute> obiektów zawierających oczekiwanego atrybuty kontekst bieżącego elementu.  
  
 Na przykład w przypadku przykładu we wprowadzeniu <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> metoda służy do pobierania wszystkich atrybutów `book` elementu.  
  
 Jeśli wywołasz <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> metoda natychmiast po <xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A> metody, zwracane są wszystkie atrybuty, które może się pojawić w dokumencie XML. Jednak jeśli wywołasz <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> metody jedno lub więcej wywołań <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> metody, zwracane są atrybuty, które nie zostały jeszcze zweryfikowane dla bieżącego elementu.  
  
> [!NOTE]
>  Wyniki <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A>, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A>, i <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> metody <xref:System.Xml.Schema.XmlSchemaValidator> klasy są uzależnione od bieżącego kontekstu sprawdzania poprawności. Aby uzyskać więcej informacji zobacz sekcję "Kontekst weryfikacji" tego tematu.  
  
 Na przykład <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> metody, zobacz przykład we wstępie. Aby uzyskać więcej informacji na temat <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> metody, zobacz <xref:System.Xml.Schema.XmlSchemaValidator> klasy dokumentację referencyjną.  
  
#### <a name="retrieving-unspecified-default-attributes"></a>Podczas pobierania atrybutów nieokreślonych domyślnych  
 <xref:System.Xml.Schema.XmlSchemaValidator.GetUnspecifiedDefaultAttributes%2A> Metoda wypełni <xref:System.Collections.ArrayList> określenia <xref:System.Xml.Schema.XmlSchemaAttribute> obiektów wszystkich atrybutów z wartościami domyślnymi, które mają nie zostało wcześniej poddane walidacji za pomocą <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> metodę w kontekście elementu. <xref:System.Xml.Schema.XmlSchemaValidator.GetUnspecifiedDefaultAttributes%2A> Metoda powinna być wywoływana po wywołaniu <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> metody dla każdego atrybutu w kontekście elementu. <xref:System.Xml.Schema.XmlSchemaValidator.GetUnspecifiedDefaultAttributes%2A> Metoda powinna służyć, aby określić atrybuty domyślnych ma zostać wstawiony w dokumencie XML, w trakcie sprawdzania poprawności.  
  
 Aby uzyskać więcej informacji na temat <xref:System.Xml.Schema.XmlSchemaValidator.GetUnspecifiedDefaultAttributes%2A> metody, zobacz <xref:System.Xml.Schema.XmlSchemaValidator> klasy dokumentację referencyjną.  
  
### <a name="handling-schema-validation-events"></a>Obsługa zdarzeń sprawdzania poprawności schematu  
 Schemat Walidacja ostrzeżeń i błędów napotkanych podczas sprawdzania poprawności, które są obsługiwane przez <xref:System.Xml.Schema.XmlSchemaValidator.ValidationEventHandler> zdarzenia <xref:System.Xml.Schema.XmlSchemaValidator> klasy.  
  
 Ostrzeżenia sprawdzania poprawności schematu mają <xref:System.Xml.Schema.XmlSeverityType> wartość <xref:System.Xml.Schema.XmlSeverityType.Warning> i błędy sprawdzania poprawności schematu <xref:System.Xml.Schema.XmlSeverityType> wartość <xref:System.Xml.Schema.XmlSeverityType.Error>. Jeśli nie <xref:System.Xml.Schema.XmlSchemaValidator.ValidationEventHandler> został przypisany, <xref:System.Xml.Schema.XmlSchemaValidationException> jest generowany dla wszystkich błędów sprawdzania poprawności schematu za pomocą <xref:System.Xml.Schema.XmlSeverityType> wartość <xref:System.Xml.Schema.XmlSeverityType.Error>. Jednak <xref:System.Xml.Schema.XmlSchemaValidationException> nie jest generowany dla ostrzeżenia sprawdzania poprawności schematu za pomocą <xref:System.Xml.Schema.XmlSeverityType> wartość <xref:System.Xml.Schema.XmlSeverityType.Warning>.  
  
 Oto przykład <xref:System.Xml.Schema.ValidationEventHandler> odbierająca schematu Walidacja ostrzeżeń i błędów napotkanych podczas sprawdzania poprawności schematu z przykładu we wprowadzeniu.  
  
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
  
 Aby uzyskać pełny przykład <xref:System.Xml.Schema.ValidationEventHandler>, zobacz przykład we wstępie. Aby uzyskać więcej informacji, zobacz <xref:System.Xml.Schema.XmlSchemaInfo> klasy dokumentację referencyjną.  
  
## <a name="xmlschemavalidator-state-transition"></a>Przejście stanu XmlSchemaValidator  
 <xref:System.Xml.Schema.XmlSchemaValidator> Klasa ma zmianę stanu zdefiniowany, który wymusza kolejność i wystąpienie wywołania do każdej metody sprawdzania poprawności, elementy, atrybuty i zawartości w zestaw informacji XML.  
  
 W poniższej tabeli opisano przejście stanu z <xref:System.Xml.Schema.XmlSchemaValidator> klasy, a sekwencji i wystąpienie wywołania metody, które mogą być wykonane w każdym stanie.  
  
|Stan|przejścia|  
|-----------|----------------|  
|Sprawdzanie poprawności|<xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> (<xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> &#124; TopLevel *) <xref:System.Xml.Schema.XmlSchemaValidator.EndValidation%2A>|  
|TopLevel|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateWhitespace%2A> &#124; <xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A> &#124; Element|  
|Element|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A> <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>* (<xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndOfAttributes%2A> Zawartości\*)? <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A> &#124;<br /><br /> <xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A> <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>\* <xref:System.Xml.Schema.XmlSchemaValidator.SkipToEndElement%2A> &#124;<br /><br /> <xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A> <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>\* <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndOfAttributes%2A> Zawartość\* <xref:System.Xml.Schema.XmlSchemaValidator.SkipToEndElement%2A>&#124;|  
|Zawartość|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateWhitespace%2A> &#124; <xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A> &#124; Element|  
  
> [!NOTE]
>  <xref:System.InvalidOperationException> Jest zgłaszany przez każdą z metod w powyższej tabeli, gdy wywołanie metody składa się nieprawidłowe sekwencji zgodnie z bieżącym stanem <xref:System.Xml.Schema.XmlSchemaValidator> obiektu.  
  
 Powyższej tabeli przejścia stanu używa symbole znaków interpunkcyjnych, aby opisać metody i innych stanów, którą można wywołać dla każdego stanu przejście stanu <xref:System.Xml.Schema.XmlSchemaValidator> klasy. Symbole używane są te same symbole w odwołanie do standardów XML znaleziono dokumentu Type Definition (DTD).  
  
 W poniższej tabeli opisano wpływ symbole znaków interpunkcyjnych, znaleziono w powyższej tabeli przejścia stanu na metody i innych państw, może być wywoływana dla każdego stanu w okresie przejściowym stanu z <xref:System.Xml.Schema.XmlSchemaValidator> klasy.  
  
|Symbol|Opis|  
|------------|-----------------|  
|&#124;|Można wywołać metody lub stan (jeden przed pasku) lub obiektowi po nim.|  
|?|Ta metoda lub stan, który poprzedza znak zapytania jest opcjonalne, ale jeśli jest on nazywany go może lze volat pouze jednou.|  
|*|Ta metoda lub stan, który poprzedza * symboli jest opcjonalna i może być wywoływana więcej niż jeden raz.|  
  
## <a name="validation-context"></a>Kontekst weryfikacji  
 Metody <xref:System.Xml.Schema.XmlSchemaValidator> klasa służy do sprawdzania poprawności, elementy, atrybuty i zawartości w zestaw informacji XML, Zmień kontekst weryfikacji <xref:System.Xml.Schema.XmlSchemaValidator> obiektu. Na przykład <xref:System.Xml.Schema.XmlSchemaValidator.SkipToEndElement%2A> metoda Pomija weryfikację bieżącej zawartości elementu i przygotowuje <xref:System.Xml.Schema.XmlSchemaValidator> obiektu aby walidować zawartość w kontekście elementu nadrzędnego; jest to równoważne do pomijania sprawdzania poprawności na wszystkie obiekty podrzędne bieżącego elementu a następnie wywołując <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A> metody.  
  
 Wyniki <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A>, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A>, i <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> metody <xref:System.Xml.Schema.XmlSchemaValidator> klasy są uzależnione od bieżącego kontekstu sprawdzania poprawności.  
  
 W poniższej tabeli opisano wyniki wywoływanie tych metod po wywołaniu jednej z metod <xref:System.Xml.Schema.XmlSchemaValidator> klasa służy do sprawdzania poprawności, elementy, atrybuty i zawartości w zestaw informacji XML.  
  
|Metoda|GetExpectedParticles|GetExpectedAttributes|AddSchema|  
|------------|--------------------------|---------------------------|---------------|  
|<xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A>|Jeśli wartość domyślna <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> metoda jest wywoływana, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> zwraca tablicę zawierającą wszystkie elementy globalne.<br /><br /> Jeśli przeciążone <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> metody, która przyjmuje <xref:System.Xml.Schema.XmlSchemaObject> jako parametru jest wywoływana, aby zainicjować częściowej weryfikacji elementu <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> zwraca tylko element, do którego <xref:System.Xml.Schema.XmlSchemaValidator> obiekt został zainicjowany.|Jeśli wartość domyślna <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> metoda jest wywoływana, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> zwraca pustą tablicę.<br /><br /> Jeśli przeciążenia <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> metody, która przyjmuje <xref:System.Xml.Schema.XmlSchemaObject> jako parametru jest wywoływana, aby zainicjować częściowej weryfikacji atrybutu <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> zwraca tylko atrybut, do którego <xref:System.Xml.Schema.XmlSchemaValidator> obiekt został zainicjowany.|Dodaje schematu do <xref:System.Xml.Schema.XmlSchemaSet> z <xref:System.Xml.Schema.XmlSchemaValidator> obiektu, jeśli nie ma żadnych błędów przetwarzania wstępnego.|  
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A>|Jeśli element kontekstu jest prawidłowy, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> zwraca sekwencję elementów oczekiwanych jako elementy podrzędne elementu kontekstu.<br /><br /> Jeśli element kontekstu jest nieprawidłowy, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> zwraca pustą tablicę.|Jeśli element kontekstu jest prawidłowy, a nie wywołanie <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> zostało wcześniej ustanowione, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> zwraca listę wszystkich atrybutów, które są zdefiniowane w elemencie kontekstu.<br /><br /> Jeśli niektóre atrybuty zostały już zweryfikowane, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> zwraca listę pozostałe atrybuty, które ma zostać zweryfikowana.<br /><br /> Jeśli element kontekstu jest nieprawidłowy, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> zwraca pustą tablicę.|Wartość taka sama jak powyżej.|  
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>|Jeśli atrybut kontekstu jest atrybutem najwyższego poziomu <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> zwraca pustą tablicę.<br /><br /> W przeciwnym razie <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> zwraca sekwencję elementów oczekiwano jako pierwszy element podrzędny elementu kontekstu.|Jeśli atrybut kontekstu jest atrybutem najwyższego poziomu <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> zwraca pustą tablicę.<br /><br /> W przeciwnym razie <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> zwraca listę wszystkich pozostałych atrybutów, które mają być weryfikowane.|Wartość taka sama jak powyżej.|  
|<xref:System.Xml.Schema.XmlSchemaValidator.GetUnspecifiedDefaultAttributes%2A>|<xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> Zwraca sekwencję elementów oczekiwano jako pierwszy element podrzędny elementu kontekstu.|<xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> Zwraca listę wymaganych i opcjonalnych atrybutów, które są jeszcze zostanie wykonane sprawdzanie poprawności elementu kontekstu.|Wartość taka sama jak powyżej.|  
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndOfAttributes%2A>|<xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> Zwraca sekwencję elementów oczekiwano jako pierwszy element podrzędny elementu kontekstu.|<xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> Zwraca pustą tablicę.|Wartość taka sama jak powyżej.|  
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A>|Jeśli typ zawartości elementu kontekstu jest mieszany, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> zwraca sekwencję elementów oczekiwanych pozycji dalej.<br /><br /> Jeśli typ zawartości elementu kontekstu jest TextOnly lub jest pusta, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> zwraca pustą tablicę.<br /><br /> Jeśli typ zawartości elementu kontekstu jest ElementOnly, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> zwraca sekwencję elementów w pozycji dalej, ale błąd sprawdzania poprawności już wystąpił.|<xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> Zwraca listę atrybutów, które nie są weryfikowane elementu kontekstu.|Wartość taka sama jak powyżej.|  
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateWhitespace%2A>|Jeśli kontekst-biały znak jest najwyższego poziomu odstępu <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> zwraca pustą tablicę.<br /><br /> W przeciwnym razie <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> zachowanie metody jest taka sama, jak w <xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A>.|Jeśli kontekst-biały znak jest najwyższego poziomu odstępu <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> zwraca pustą tablicę.<br /><br /> W przeciwnym razie <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> zachowanie metody jest taka sama, jak w <xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A>.|Wartość taka sama jak powyżej.|  
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A>|<xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> Zwraca sekwencję elementów oczekiwanych po elemencie kontekstu (możliwe elementów równorzędnych).|<xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> Zwraca listę atrybutów, które nie są weryfikowane elementu kontekstu.<br /><br /> Jeśli element kontekstu nie ma elementu nadrzędnego następnie <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> zwraca pustą listę (element kontekstu jest elementem nadrzędnym bieżącego elementu, na którym <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A> wywołano).|Wartość taka sama jak powyżej.|  
|<xref:System.Xml.Schema.XmlSchemaValidator.SkipToEndElement%2A>|Taki sam jak <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A>.|Taki sam jak <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A>.|Wartość taka sama jak powyżej.|  
|<xref:System.Xml.Schema.XmlSchemaValidator.EndValidation%2A>|Zwraca pustą tablicę.|Zwraca pustą tablicę.|Wartość taka sama jak powyżej.|  
  
> [!NOTE]
>  Wartości zwracane przez różne właściwości <xref:System.Xml.Schema.XmlSchemaValidator> klasy nie są modyfikowane przez wywołanie jednej z metod w powyższej tabeli.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Xml.Schema.XmlSchemaValidator>
