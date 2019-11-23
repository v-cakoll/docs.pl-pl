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
ms.openlocfilehash: a420a134eda6c62758b0d218e3c0a4a4922b048c
ms.sourcegitcommit: d7c298f6c2e3aab0c7498bfafc0a0a94ea1fe23e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/10/2019
ms.locfileid: "72250042"
---
# <a name="xmlschemavalidator-push-based-validation"></a>Weryfikacja oparta na wypchnięciach przy użyciu klasy XmlSchemaValidator

Klasa <xref:System.Xml.Schema.XmlSchemaValidator> zapewnia wydajny mechanizm o wysokiej wydajności służący do sprawdzania poprawności danych XML w schematach XML w sposób oparty na wypychaniu. Na przykład Klasa <xref:System.Xml.Schema.XmlSchemaValidator> umożliwia weryfikowanie w miejscu XML sprawdzonych, bez konieczności serializacji go jako dokumentu XML, a następnie ponowne analizowanie dokumentu przy użyciu walidacji czytnika XML.

Klasy <xref:System.Xml.Schema.XmlSchemaValidator> można używać w zaawansowanych scenariuszach, takich jak tworzenie aparatów walidacji w niestandardowych źródłach danych XML lub sposób tworzenia walidacji składnika zapisywania XML.

Poniżej znajduje się przykład użycia klasy <xref:System.Xml.Schema.XmlSchemaValidator> do walidacji pliku `contosoBooks.xml` w schemacie `contosoBooks.xsd`. W przykładzie zastosowano klasę <xref:System.Xml.Serialization.XmlSerializer>, aby deserializować plik `contosoBooks.xml` i przekazać wartości węzłów do metod klasy <xref:System.Xml.Schema.XmlSchemaValidator>.

> [!NOTE]
> Ten przykład jest używany w części tego tematu.

[!code-csharp[XmlSchemaValidatorExamples#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaValidatorExamples/CS/XmlSchemaValidatorExamples.cs#1)]
[!code-vb[XmlSchemaValidatorExamples#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaValidatorExamples/VB/XmlSchemaValidatorExamples.vb#1)]

Przykład pobiera `contosoBooks.xml` plik jako dane wejściowe.

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

Aby rozpocząć walidację sprawdzonych XML, należy najpierw zainicjować nowe wystąpienie klasy <xref:System.Xml.Schema.XmlSchemaValidator> przy użyciu konstruktora <xref:System.Xml.Schema.XmlSchemaValidator.%23ctor%2A>.

Konstruktor <xref:System.Xml.Schema.XmlSchemaValidator.%23ctor%2A> przyjmuje obiekty <xref:System.Xml.XmlNameTable>, <xref:System.Xml.Schema.XmlSchemaSet>i <xref:System.Xml.XmlNamespaceManager> jako parametry, a także wartość <xref:System.Xml.Schema.XmlSchemaValidationFlags> jako parametr. Obiekt <xref:System.Xml.XmlNameTable> jest używany do wyodrębnić dobrze znanych ciągów przestrzeni nazw, takich jak przestrzeń nazw schematu, przestrzeń nazw XML i tak dalej, i jest przenoszona do metody <xref:System.Xml.Schema.XmlSchemaDatatype.ParseValue%2A> podczas weryfikacji prostej zawartości. Obiekt <xref:System.Xml.Schema.XmlSchemaSet> zawiera schematy XML używane do sprawdzania poprawności sprawdzonych XML. Obiekt <xref:System.Xml.XmlNamespaceManager> jest używany do rozpoznawania przestrzeni nazw napotkanych podczas walidacji. Wartość <xref:System.Xml.Schema.XmlSchemaValidationFlags> służy do wyłączania niektórych funkcji weryfikacji.

Więcej informacji na temat konstruktora <xref:System.Xml.Schema.XmlSchemaValidator.%23ctor%2A> można znaleźć w dokumentacji dotyczącej klasy <xref:System.Xml.Schema.XmlSchemaValidator>.

### <a name="initializing-validation"></a>Inicjowanie walidacji

Po skonstruowaniu obiektu <xref:System.Xml.Schema.XmlSchemaValidator> są dwie przeciążone metody <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> użyte do zainicjowania stanu obiektu <xref:System.Xml.Schema.XmlSchemaValidator>. Poniżej przedstawiono dwie metody <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A>.

- <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType>

- <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType>

Domyślna metoda <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType> inicjuje obiekt <xref:System.Xml.Schema.XmlSchemaValidator> do jego stanu początkowego, a przeciążona metoda <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType>, która przyjmuje <xref:System.Xml.Schema.XmlSchemaObject> jako parametr inicjuje obiekt <xref:System.Xml.Schema.XmlSchemaValidator> do stanu początkowego dla częściowej walidacji.

Obie metody <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> mogą być wywoływane tylko natychmiast po skonstruowaniu obiektu <xref:System.Xml.Schema.XmlSchemaValidator> lub po wywołaniu <xref:System.Xml.Schema.XmlSchemaValidator.EndValidation%2A>.

Przykład metody <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType> zapoznaj się z przykładem we wprowadzeniu. Więcej informacji o metodzie <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> można znaleźć w dokumentacji dotyczącej klasy <xref:System.Xml.Schema.XmlSchemaValidator>.

#### <a name="partial-validation"></a>Częściowe sprawdzanie poprawności

Metoda <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType>, która przyjmuje <xref:System.Xml.Schema.XmlSchemaObject> jako parametr inicjuje obiekt <xref:System.Xml.Schema.XmlSchemaValidator> do stanu początkowego dla częściowej walidacji.

W poniższym przykładzie <xref:System.Xml.Schema.XmlSchemaObject> jest inicjowana do walidacji częściowej przy użyciu metody <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType>. Element schematu `orderNumber` jest przenoszona przez wybranie elementu schematu <xref:System.Xml.XmlQualifiedName> w kolekcji <xref:System.Xml.Schema.XmlSchemaObjectTable> zwróconej przez właściwość <xref:System.Xml.Schema.XmlSchemaSet.GlobalElements%2A> obiektu <xref:System.Xml.Schema.XmlSchemaSet>. Obiekt <xref:System.Xml.Schema.XmlSchemaValidator> następnie sprawdza poprawność tego określonego elementu.

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

Przykład pobiera Poniższy schemat XML jako dane wejściowe.

```xml
<xs:schema xmlns:xs="http://www.w3.org/2001/XMLSchema">
  <xs:element name="orderNumber" type="xs:int" />
</xs:schema>
```

Więcej informacji o metodzie <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> można znaleźć w dokumentacji dotyczącej klasy <xref:System.Xml.Schema.XmlSchemaValidator>.

### <a name="adding-additional-schemas"></a>Dodawanie dodatkowych schematów

Metoda <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> klasy <xref:System.Xml.Schema.XmlSchemaValidator> służy do dodawania schematu XML do zestawu schematów używanych podczas walidacji. Metoda <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> może służyć do symulowania efektu napotkania wbudowanego schematu XML w języku XML sprawdzonych.

> [!NOTE]
> Docelowa przestrzeń nazw parametru <xref:System.Xml.Schema.XmlSchema> nie może być zgodna z elementem lub atrybutem już napotkanym przez obiekt <xref:System.Xml.Schema.XmlSchemaValidator>.
>
> Jeśli wartość <xref:System.Xml.Schema.XmlSchemaValidationFlags.ProcessInlineSchema?displayProperty=nameWithType> nie została przeniesiona jako parametr do konstruktora <xref:System.Xml.Schema.XmlSchemaValidator.%23ctor%2A>, Metoda <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> nie wykonuje żadnych operacji.

Wynik metody <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> jest zależny od bieżącego kontekstu węzła XML, który jest sprawdzany. Aby uzyskać więcej informacji na temat kontekstów walidacji, zobacz sekcję "kontekst walidacji" w tym temacie.

Więcej informacji o metodzie <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> można znaleźć w dokumentacji dotyczącej klasy <xref:System.Xml.Schema.XmlSchemaValidator>.

### <a name="validating-elements-attributes-and-content"></a>Walidacja elementów, atrybutów i zawartości

Klasa <xref:System.Xml.Schema.XmlSchemaValidator> udostępnia kilka metod służących do sprawdzania poprawności elementów, atrybutów i zawartości w sprawdzonych XML w schematach XML. W poniższej tabeli opisano każdą z tych metod.

|Metoda|Opis|
|------------|-----------------|
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A>|Sprawdza poprawność nazwy elementu w bieżącym kontekście.|
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>|Sprawdza poprawność atrybutu w kontekście bieżącego elementu lub względem obiektu <xref:System.Xml.Schema.XmlSchemaAttribute> przekazaną jako parametr do metody <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A>.|
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndOfAttributes%2A>|Sprawdza, czy wszystkie wymagane atrybuty w kontekście elementu są obecne i przygotowuje obiekt <xref:System.Xml.Schema.XmlSchemaValidator>, aby sprawdzić poprawność zawartości podrzędnej elementu.|
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A>|Sprawdza, czy tekst jest dozwolony w kontekście bieżącego elementu i gromadzi tekst do walidacji, jeśli bieżący element ma prostą zawartość.|
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateWhitespace%2A>|Sprawdza, czy w bieżącym kontekście elementu jest dozwolone białe miejsce, i gromadzi białe miejsce do walidacji, czy bieżący element ma prostą zawartość.|
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A>|Sprawdza, czy zawartość tekstowa elementu jest prawidłowa przy uwzględnieniu jego typu danych dla elementów z prostą zawartością i sprawdza, czy zawartość bieżącego elementu jest kompletna dla elementów z zawartością złożoną.|
|<xref:System.Xml.Schema.XmlSchemaValidator.SkipToEndElement%2A>|Pomija sprawdzanie poprawności zawartości bieżącego elementu i przygotowuje obiekt <xref:System.Xml.Schema.XmlSchemaValidator> do walidacji zawartości w kontekście elementu nadrzędnego.|
|<xref:System.Xml.Schema.XmlSchemaValidator.EndValidation%2A>|Wykonuje walidację i sprawdza ograniczenia tożsamości dla całego dokumentu XML, jeśli ustawiono opcję walidacji <xref:System.Xml.Schema.XmlSchemaValidationFlags.ProcessIdentityConstraints>.|

> [!NOTE]
> Klasa <xref:System.Xml.Schema.XmlSchemaValidator> ma zdefiniowane przejście stanu, które wymusza sekwencję i wystąpienia wywołań wykonanych dla każdej z metod opisanych w poprzedniej tabeli. Przejście określonego stanu klasy <xref:System.Xml.Schema.XmlSchemaValidator> zostało opisane w sekcji "przechodzenie stanu XmlSchemaValidator" w tym temacie.

Przykład metod używanych do sprawdzania poprawności elementów, atrybutów i zawartości w sprawdzonych XML zawiera przykład w poprzedniej sekcji. Więcej informacji o tych metodach znajduje się w dokumentacji dotyczącej klas <xref:System.Xml.Schema.XmlSchemaValidator>.

#### <a name="validating-content-using-an-xmlvaluegetter"></a>Sprawdzanie poprawności zawartości przy użyciu XmlValueGetter

`delegate` <xref:System.Xml.Schema.XmlValueGetter>może służyć do przekazywania wartości węzłów atrybutów, tekstu lub białych miejsc jako typów środowiska uruchomieniowego języka wspólnego (CLR) zgodnych z typem języka definicji schematu XML (XSD) atrybutu, tekstu lub odstępu. <xref:System.Xml.Schema.XmlValueGetter>`delegate` jest przydatne, jeśli wartość CLR węzła atrybutu, tekstu lub białego miejsca jest już dostępna, i unika kosztu konwersji na `string`, a następnie ponowne przeanalizowanie go w celu sprawdzenia poprawności.

Metody <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>, <xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A>i <xref:System.Xml.Schema.XmlSchemaValidator.ValidateWhitespace%2A> są przeciążone i akceptują wartości węzłów atrybutów, tekstu lub białych miejsc jako `string` lub <xref:System.Xml.Schema.XmlValueGetter>`delegate`.

Następujące metody klasy <xref:System.Xml.Schema.XmlSchemaValidator> akceptują <xref:System.Xml.Schema.XmlValueGetter>`delegate` jako parametr.

- <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>

- <xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A>

- <xref:System.Xml.Schema.XmlSchemaValidator.ValidateWhitespace%2A>

Poniżej przedstawiono przykład <xref:System.Xml.Schema.XmlValueGetter>`delegate` pobrany z przykładu klasy <xref:System.Xml.Schema.XmlSchemaValidator> we wprowadzeniu. `delegate` <xref:System.Xml.Schema.XmlValueGetter>zwraca wartość atrybutu jako obiekt <xref:System.DateTime>. Aby sprawdzić poprawność tego obiektu <xref:System.DateTime> zwróconego przez <xref:System.Xml.Schema.XmlValueGetter>, obiekt <xref:System.Xml.Schema.XmlSchemaValidator> najpierw konwertuje go na element ValueType (ValueType jest domyślnym mapowaniem CLR dla typu XSD) dla typu danych atrybutu, a następnie sprawdza aspekty w skonwertowanej wartości.

```vb
Shared dateTimeGetterContent As Object

Shared Function DateTimeGetterHandle() As Object
    Return dateTimeGetterContent
End Function

Shared Function DateTimeGetter(dateTime As DateTime) As XmlValueGetter
    dateTimeGetterContent = dateTime
    Return New XmlValueGetter(AddressOf DateTimeGetterHandle)
End Function
```

```csharp
static object dateTimeGetterContent;

static object DateTimeGetterHandle()
{
    return dateTimeGetterContent;
}

static XmlValueGetter DateTimeGetter(DateTime dateTime)
{
    dateTimeGetterContent = dateTime;
    return new XmlValueGetter(dateTimeGetterHandle);
}
```

Aby zapoznać się z kompletnym przykładem `delegate`<xref:System.Xml.Schema.XmlValueGetter>, zobacz przykład we wprowadzeniu. Więcej informacji na temat `delegate`<xref:System.Xml.Schema.XmlValueGetter>można znaleźć w dokumentacji dotyczącej klas <xref:System.Xml.Schema.XmlValueGetter>i <xref:System.Xml.Schema.XmlSchemaValidator>.

#### <a name="post-schema-validation-information"></a>Post-Schema-Validation-Information

Klasa <xref:System.Xml.Schema.XmlSchemaInfo> reprezentuje niektóre z podanych po schemacie walidacji węzła XML zweryfikowanego przez klasę <xref:System.Xml.Schema.XmlSchemaValidator>. Różne metody klasy <xref:System.Xml.Schema.XmlSchemaValidator> akceptują obiekt <xref:System.Xml.Schema.XmlSchemaInfo> jako opcjonalny parametr `out` (`null`).

Po pomyślnej weryfikacji właściwości obiektu <xref:System.Xml.Schema.XmlSchemaInfo> są ustawiane z wynikami walidacji. Na przykład po pomyślnym sprawdzeniu atrybutu przy użyciu metody <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> obiekt <xref:System.Xml.Schema.XmlSchemaInfo> (jeśli określony) <xref:System.Xml.Schema.XmlSchemaInfo.SchemaAttribute%2A>, <xref:System.Xml.Schema.XmlSchemaInfo.SchemaType%2A>, <xref:System.Xml.Schema.XmlSchemaInfo.MemberType%2A>i <xref:System.Xml.Schema.XmlSchemaInfo.Validity%2A> właściwości są ustawione z wynikami walidacji.

Następujące metody klasy <xref:System.Xml.Schema.XmlSchemaValidator> akceptują obiekt <xref:System.Xml.Schema.XmlSchemaInfo> jako parametr out.

- <xref:System.Xml.Schema.XmlSchemaValidator.SkipToEndElement%2A>

- <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>

- <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>

- <xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A>

- <xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A>

- <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A>

- <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A>

- <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndOfAttributes%2A>

Aby zapoznać się z kompletnym przykładem klasy <xref:System.Xml.Schema.XmlSchemaInfo>, zobacz przykład we wprowadzeniu. Więcej informacji na temat klasy <xref:System.Xml.Schema.XmlSchemaInfo> można znaleźć w dokumentacji dotyczącej klasy <xref:System.Xml.Schema.XmlSchemaInfo>.

### <a name="retrieving-expected-particles-attributes-and-unspecified-default-attributes"></a>Pobieranie oczekiwanych cząsteczek, atrybutów i nieokreślonych atrybutów domyślnych

Klasa <xref:System.Xml.Schema.XmlSchemaValidator> dostarcza metody <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A>, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A>i <xref:System.Xml.Schema.XmlSchemaValidator.GetUnspecifiedDefaultAttributes%2A>, aby pobrać oczekiwane cząstki, atrybuty i nieokreślone atrybuty domyślne w bieżącym kontekście walidacji.

#### <a name="retrieving-expected-particles"></a>Pobieranie oczekiwanych cząsteczek

Metoda <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> zwraca tablicę obiektów <xref:System.Xml.Schema.XmlSchemaParticle> zawierających oczekiwane cząstki w bieżącym kontekście elementu. Prawidłowe cząstki, które mogą być zwracane przez metodę <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A>, są wystąpieniami klas <xref:System.Xml.Schema.XmlSchemaElement> i <xref:System.Xml.Schema.XmlSchemaAny>.

Gdy compositor dla modelu zawartości jest `xs:sequence`, zwracana jest tylko Następna cząstka w sekwencji. Jeśli compositor dla modelu zawartości to `xs:all` lub `xs:choice`, zwracane są wszystkie prawidłowe cząstki, które mogą się pojawić w kontekście bieżącego elementu.

> [!NOTE]
> Jeśli metoda <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> jest wywoływana natychmiast po wywołaniu metody <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A>, Metoda <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> zwróci wszystkie elementy globalne.

Na przykład, w schemacie języka definicji schematu XML (XSD) i w poniższym dokumencie XML, po walidacji elementu `book`, element `book` jest bieżącym kontekstem elementu. Metoda <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> zwraca tablicę zawierającą pojedynczy obiekt <xref:System.Xml.Schema.XmlSchemaElement> reprezentujący element `title`. Gdy kontekst walidacji jest elementem `title`, Metoda <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> zwraca pustą tablicę. Jeśli metoda <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> jest wywoływana po zweryfikowaniu elementu `title`, ale przed zweryfikowaniem elementu `description`, zwraca tablicę zawierającą pojedynczy obiekt <xref:System.Xml.Schema.XmlSchemaElement> reprezentujący element `description`. Jeśli metoda <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> jest wywoływana po zweryfikowaniu elementu `description`, zwraca tablicę zawierającą pojedynczy obiekt <xref:System.Xml.Schema.XmlSchemaAny> reprezentujący symbol wieloznaczny.

```vb
Dim reader As XmlReader =  XmlReader.Create("input.xml")

Dim schemaSet As New XmlSchemaSet()
schemaSet.Add(Nothing, "schema.xsd")
Dim manager As New XmlNamespaceManager(reader.NameTable)

Dim validator As New XmlSchemaValidator(reader.NameTable,schemaSet,manager,XmlSchemaValidationFlags.None)
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

var schemaSet = new XmlSchemaSet();
schemaSet.Add(null, "schema.xsd");
var manager = new XmlNamespaceManager(reader.NameTable);

var validator = new XmlSchemaValidator(reader.NameTable, schemaSet, manager, XmlSchemaValidationFlags.None);
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

 Przykład pobiera następujący kod XML jako dane wejściowe:

```xml
<xs:schema xmlns:xs="http://www.w3c.org/2001/XMLSchema">
  <xs:element name="book">
    <xs:sequence>
      <xs:element name="title" type="xs:string" />
      <xs:element name="description" type="xs:string" />
      <xs:any processContent="lax" maxOccurs="unbounded" />
    </xs:sequence>
  </xs:element>
</xs:schema>
```

Przykład pobiera następujący schemat XSD jako dane wejściowe:

```xml
<book>
  <title>My Book</title>
  <description>My Book's Description</description>
  <namespace>System.Xml.Schema</namespace>
</book>
```

> [!NOTE]
> Wyniki <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A>, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A>i <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> metody klasy <xref:System.Xml.Schema.XmlSchemaValidator> są zależne od bieżącego kontekstu, który jest sprawdzany. Aby uzyskać więcej informacji, zobacz sekcję "kontekst walidacji" w tym temacie.

Przykład metody <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> zapoznaj się z przykładem we wprowadzeniu. Więcej informacji o metodzie <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> można znaleźć w dokumentacji dotyczącej klasy <xref:System.Xml.Schema.XmlSchemaValidator>.

#### <a name="retrieving-expected-attributes"></a>Pobieranie oczekiwanych atrybutów

Metoda <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> zwraca tablicę obiektów <xref:System.Xml.Schema.XmlSchemaAttribute> zawierających oczekiwane atrybuty w bieżącym kontekście elementu.

Na przykład w przykładzie we wprowadzeniu Metoda <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> jest używana do pobierania wszystkich atrybutów elementu `book`.

Jeśli wywołasz metodę <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> bezpośrednio po metodzie <xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A>, zwracane są wszystkie atrybuty, które mogą pojawić się w dokumencie XML. Jeśli jednak wywołasz metodę <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> po jednym lub kilku wywołaniach metody <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>, zwracane są atrybuty, które nie zostały jeszcze zweryfikowane dla bieżącego elementu.

> [!NOTE]
> Wyniki <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A>, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A>i <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> metody klasy <xref:System.Xml.Schema.XmlSchemaValidator> są zależne od bieżącego kontekstu, który jest sprawdzany. Aby uzyskać więcej informacji, zobacz sekcję "kontekst walidacji" w tym temacie.

Przykład metody <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> zapoznaj się z przykładem we wprowadzeniu. Więcej informacji o metodzie <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> można znaleźć w dokumentacji dotyczącej klasy <xref:System.Xml.Schema.XmlSchemaValidator>.

#### <a name="retrieving-unspecified-default-attributes"></a>Pobieranie nieokreślonych atrybutów domyślnych

Metoda <xref:System.Xml.Schema.XmlSchemaValidator.GetUnspecifiedDefaultAttributes%2A> wypełnia <xref:System.Collections.ArrayList> określone za pomocą obiektów <xref:System.Xml.Schema.XmlSchemaAttribute> dla wszystkich atrybutów z wartościami domyślnymi, które nie zostały wcześniej zweryfikowane przy użyciu metody <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> w kontekście elementu. Metoda <xref:System.Xml.Schema.XmlSchemaValidator.GetUnspecifiedDefaultAttributes%2A> powinna być wywoływana po wywołaniu metody <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> dla każdego atrybutu w kontekście elementu. Metoda <xref:System.Xml.Schema.XmlSchemaValidator.GetUnspecifiedDefaultAttributes%2A> powinna służyć do określenia, jakie atrybuty domyślne mają być wstawiane do zweryfikowanego dokumentu XML.

Więcej informacji o metodzie <xref:System.Xml.Schema.XmlSchemaValidator.GetUnspecifiedDefaultAttributes%2A> można znaleźć w dokumentacji dotyczącej klasy <xref:System.Xml.Schema.XmlSchemaValidator>.

### <a name="handling-schema-validation-events"></a>Obsługa zdarzeń walidacji schematu

Ostrzeżenia i błędy walidacji schematu napotkane podczas walidacji są obsługiwane przez zdarzenie <xref:System.Xml.Schema.XmlSchemaValidator.ValidationEventHandler> klasy <xref:System.Xml.Schema.XmlSchemaValidator>.

Ostrzeżenia dotyczące walidacji schematu mają <xref:System.Xml.Schema.XmlSeverityType> wartość <xref:System.Xml.Schema.XmlSeverityType.Warning> i błędy walidacji schematu mają <xref:System.Xml.Schema.XmlSeverityType> wartość <xref:System.Xml.Schema.XmlSeverityType.Error>. Jeśli nie przypisano <xref:System.Xml.Schema.XmlSchemaValidator.ValidationEventHandler>, zostanie zgłoszony <xref:System.Xml.Schema.XmlSchemaValidationException> dla wszystkich błędów walidacji schematu z wartością <xref:System.Xml.Schema.XmlSeverityType> <xref:System.Xml.Schema.XmlSeverityType.Error>. Niemniej jednak <xref:System.Xml.Schema.XmlSchemaValidationException> nie jest generowany w przypadku ostrzeżeń dotyczących sprawdzania poprawności schematu z wartością <xref:System.Xml.Schema.XmlSeverityType> <xref:System.Xml.Schema.XmlSeverityType.Warning>.

Poniżej znajduje się przykład <xref:System.Xml.Schema.ValidationEventHandler>, który odbiera ostrzeżenia i błędy walidacji schematu napotkane podczas walidacji schematu wykonane z przykładu we wprowadzeniu.

```vb
Shared Sub SchemaValidationEventHandler(sender As Object, e As ValidationEventArgs)

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

Aby zapoznać się z kompletnym przykładem <xref:System.Xml.Schema.ValidationEventHandler>, zobacz przykład we wprowadzeniu. Więcej informacji można znaleźć w dokumentacji dotyczącej klas <xref:System.Xml.Schema.XmlSchemaInfo>.

## <a name="xmlschemavalidator-state-transition"></a>XmlSchemaValidator stanu przejścia

Klasa <xref:System.Xml.Schema.XmlSchemaValidator> ma zdefiniowane przejście stanu, które wymusza sekwencję i wystąpienia wywołań wykonanych dla każdej metody używanej do sprawdzania poprawności elementów, atrybutów i zawartości w sprawdzonych XML.

W poniższej tabeli opisano przechodzenie stanu klasy <xref:System.Xml.Schema.XmlSchemaValidator> oraz sekwencję i wystąpienia wywołań metod, które można wykonać w każdym stanie.

|Stan|Transition|
|-----------|----------------|
|legalizacj|<xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> (<xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> &#124; TopLevel *) <xref:System.Xml.Schema.XmlSchemaValidator.EndValidation%2A>|
|TopLevel|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateWhitespace%2A> &#124; <xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A> &#124; Element|
|Element|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A> <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>* (<xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndOfAttributes%2A> zawartości\*)? <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A> &#124;<br /><br /> <xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A> <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>\* <xref:System.Xml.Schema.XmlSchemaValidator.SkipToEndElement%2A> &#124;<br /><br /> <xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A> <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>\* <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndOfAttributes%2A> zawartości\* <xref:System.Xml.Schema.XmlSchemaValidator.SkipToEndElement%2A>&#124;|
|Zawartość|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateWhitespace%2A> &#124; <xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A> &#124; Element|

> [!NOTE]
> <xref:System.InvalidOperationException> jest generowany przez każdą z metod w powyższej tabeli, gdy wywołanie metody jest wykonywane w niepoprawnej sekwencji, zgodnie z bieżącym stanem <xref:System.Xml.Schema.XmlSchemaValidator> obiektu.

W powyższej tabeli przechodzenia stanu są używane symbole interpunkcyjne do opisywania metod i innych stanów, które mogą być wywoływane dla każdego stanu przejścia stanu klasy <xref:System.Xml.Schema.XmlSchemaValidator>. Używane symbole są tymi samymi symbolami, które znajdują się w dokumentacji XML Standards dla definicji typu dokumentu (DTD).

W poniższej tabeli opisano, jak symbole interpunkcji Znalezione w powyższej tabeli przejścia stanu mają wpływ na metody i inne Stany, które mogą być wywoływane dla każdego stanu w ramach przejścia stanu klasy <xref:System.Xml.Schema.XmlSchemaValidator>.

|Symbol|Opis|
|------------|-----------------|
|&#124;|Można wywołać metodę lub stan (jeden przed paskiem lub po nim).|
|?|Metoda lub stan, który poprzedza znak zapytania, jest opcjonalne, ale jeśli jest wywoływana, może być wywoływana tylko raz.|
|*|Metoda lub stan poprzedzający symbol * jest opcjonalny i może być wywoływana więcej niż raz.|

## <a name="validation-context"></a>Kontekst walidacji

Metody klasy <xref:System.Xml.Schema.XmlSchemaValidator> używane do sprawdzania poprawności elementów, atrybutów i zawartości w sprawdzonych XML, zmiany kontekstu walidacji obiektu <xref:System.Xml.Schema.XmlSchemaValidator>. Na przykład Metoda <xref:System.Xml.Schema.XmlSchemaValidator.SkipToEndElement%2A> pomija walidację zawartości bieżącego elementu i przygotowuje obiekt <xref:System.Xml.Schema.XmlSchemaValidator> do walidacji zawartości w kontekście elementu nadrzędnego; jest równoważne pominięciu weryfikacji dla wszystkich elementów podrzędnych bieżącego elementu, a następnie wywołania metody <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A>.

Wyniki <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A>, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A>i <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> metody klasy <xref:System.Xml.Schema.XmlSchemaValidator> są zależne od bieżącego kontekstu, który jest sprawdzany.

W poniższej tabeli opisano wyniki wywoływania tych metod po wywołaniu jednej z metod klasy <xref:System.Xml.Schema.XmlSchemaValidator> używanej do walidacji elementów, atrybutów i zawartości w sprawdzonych XML.

|Metoda|GetExpectedParticles|GetExpectedAttributes|AddSchema|
|------------|--------------------------|---------------------------|---------------|
|<xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A>|Jeśli domyślna metoda <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> jest wywoływana, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> zwraca tablicę zawierającą wszystkie elementy globalne.<br /><br /> Jeśli przeciążona metoda <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A>, która przyjmuje <xref:System.Xml.Schema.XmlSchemaObject> jako parametr jest wywoływana w celu zainicjowania częściowej walidacji elementu, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> zwraca tylko element, do którego zainicjowano obiekt <xref:System.Xml.Schema.XmlSchemaValidator>.|Jeśli domyślna metoda <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> jest wywoływana, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> zwraca pustą tablicę.<br /><br /> Jeśli przeciążanie metody <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A>, która przyjmuje <xref:System.Xml.Schema.XmlSchemaObject> jako parametr jest wywoływana w celu zainicjowania częściowej walidacji atrybutu, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> zwróci tylko atrybut, do którego zainicjowano obiekt <xref:System.Xml.Schema.XmlSchemaValidator>.|Dodaje schemat do <xref:System.Xml.Schema.XmlSchemaSet> obiektu <xref:System.Xml.Schema.XmlSchemaValidator>, jeśli nie ma żadnych błędów przetwarzania wstępnego.|
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A>|Jeśli element context jest prawidłowy, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> zwraca sekwencję elementów oczekiwanych jako elementy podrzędne elementu Context.<br /><br /> Jeśli element context jest nieprawidłowy, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> zwraca pustą tablicę.|Jeśli element context jest prawidłowy i jeśli żadne wywołanie do <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> nie zostało wcześniej wykonane, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> zwraca listę wszystkich atrybutów zdefiniowanych w elemencie Context.<br /><br /> Jeśli niektóre atrybuty zostały już sprawdzone, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> zwraca listę pozostałych atrybutów do zweryfikowania.<br /><br /> Jeśli element context jest nieprawidłowy, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> zwraca pustą tablicę.|Tak samo jak powyżej.|
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>|Jeśli atrybut kontekstu jest atrybutem najwyższego poziomu, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> zwraca pustą tablicę.<br /><br /> W przeciwnym razie <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> zwraca sekwencję elementów oczekiwaną jako pierwszy element podrzędny elementu kontekstu.|Jeśli atrybut kontekstu jest atrybutem najwyższego poziomu, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> zwraca pustą tablicę.<br /><br /> W przeciwnym razie <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> zwraca listę pozostałych atrybutów do zweryfikowania.|Tak samo jak powyżej.|
|<xref:System.Xml.Schema.XmlSchemaValidator.GetUnspecifiedDefaultAttributes%2A>|<xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> zwraca sekwencję elementów oczekiwaną jako pierwszy element podrzędny elementu kontekstu.|<xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> zwraca listę wymaganych i opcjonalnych atrybutów, które nie zostały jeszcze zweryfikowane dla elementu kontekstu.|Tak samo jak powyżej.|
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndOfAttributes%2A>|<xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> zwraca sekwencję elementów oczekiwaną jako pierwszy element podrzędny elementu kontekstu.|<xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> zwraca pustą tablicę.|Tak samo jak powyżej.|
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A>|Jeśli element ContentType elementu context jest mieszany, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> zwraca sekwencję elementów oczekiwanych w następnym położeniu.<br /><br /> Jeśli element ContentType elementu ContextType ma wartość textOnly lub Empty, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> zwraca pustą tablicę.<br /><br /> Jeśli element ContentType elementu ContextType to ElementOnly, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> zwraca sekwencję elementów oczekiwanych w następnym miejscu, ale wystąpił błąd sprawdzania poprawności.|<xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> zwraca listę atrybutów elementu kontekstu, które nie zostały zweryfikowane.|Tak samo jak powyżej.|
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateWhitespace%2A>|Jeśli odstępy między kontekstami jest odstępem najwyższego poziomu, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> zwraca pustą tablicę.<br /><br /> W przeciwnym razie zachowanie metody <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> jest takie samo jak w <xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A>.|Jeśli odstępy między kontekstami jest odstępem najwyższego poziomu, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> zwraca pustą tablicę.<br /><br /> W przeciwnym razie zachowanie metody <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> jest takie samo jak w <xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A>.|Tak samo jak powyżej.|
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A>|<xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> zwraca sekwencję elementów oczekiwanych po elemencie kontekstu (możliwe elementy równorzędne).|<xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> zwraca listę atrybutów elementu kontekstu, które nie zostały zweryfikowane.<br /><br /> Jeśli element kontekstu nie ma elementu nadrzędnego, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> zwraca pustą listę (element context jest elementem nadrzędnym bieżącego elementu, w którym <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A> został wywołany).|Tak samo jak powyżej.|
|<xref:System.Xml.Schema.XmlSchemaValidator.SkipToEndElement%2A>|Taki sam jak <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A>.|Taki sam jak <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A>.|Tak samo jak powyżej.|
|<xref:System.Xml.Schema.XmlSchemaValidator.EndValidation%2A>|Zwraca pustą tablicę.|Zwraca pustą tablicę.|Tak samo jak powyżej.|

> [!NOTE]
> Wartości zwracane przez różne właściwości klasy <xref:System.Xml.Schema.XmlSchemaValidator> nie są zmieniane przez wywołanie dowolnej metody z powyższej tabeli.

## <a name="see-also"></a>Zobacz także

- <xref:System.Xml.Schema.XmlSchemaValidator>
