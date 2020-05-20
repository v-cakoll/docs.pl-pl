---
title: Weryfikacja oparta na wypchnięciach przy użyciu klasy XmlSchemaValidator
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 911d4460-dd91-4958-85b2-2ca3299f9ec6
ms.openlocfilehash: d5b2fe4325000023acc98580a2a6d014f56fecbd
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2020
ms.locfileid: "83419112"
---
# <a name="xmlschemavalidator-push-based-validation"></a>Weryfikacja oparta na wypchnięciach przy użyciu klasy XmlSchemaValidator

<xref:System.Xml.Schema.XmlSchemaValidator>Klasa zapewnia wydajny mechanizm o wysokiej wydajności służący do sprawdzania poprawności danych XML w schematach XML w sposób oparty na wypychaniu. Na przykład <xref:System.Xml.Schema.XmlSchemaValidator> Klasa pozwala na sprawdzenie poprawności sprawdzonych XML, bez konieczności serializacji go jako dokumentu XML, a następnie ponowne przeanalizowanie dokumentu przy użyciu walidacji kodu XML.

<xref:System.Xml.Schema.XmlSchemaValidator>Klasa może być używana w zaawansowanych scenariuszach, takich jak tworzenie aparatów walidacji w niestandardowych źródłach danych XML lub sposób tworzenia walidacji składnika zapisywania XML.

Poniżej przedstawiono przykład użycia <xref:System.Xml.Schema.XmlSchemaValidator> klasy do walidacji `contosoBooks.xml` pliku względem `contosoBooks.xsd` schematu. W przykładzie używa <xref:System.Xml.Serialization.XmlSerializer> klasy do deserializacji `contosoBooks.xml` pliku i przekazywania wartości węzłów do metod <xref:System.Xml.Schema.XmlSchemaValidator> klasy.

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

Aby rozpocząć walidację sprawdzonych XML, należy najpierw zainicjować nowe wystąpienie <xref:System.Xml.Schema.XmlSchemaValidator> klasy przy użyciu <xref:System.Xml.Schema.XmlSchemaValidator.%23ctor%2A> konstruktora.

<xref:System.Xml.Schema.XmlSchemaValidator.%23ctor%2A>Konstruktor przyjmuje <xref:System.Xml.XmlNameTable> , <xref:System.Xml.Schema.XmlSchemaSet> , i <xref:System.Xml.XmlNamespaceManager> obiekty jako parametry, a także <xref:System.Xml.Schema.XmlSchemaValidationFlags> wartość jako parametr. <xref:System.Xml.XmlNameTable>Obiekt jest używany do wyodrębnić dobrze znanych ciągów przestrzeni nazw, takich jak przestrzeń nazw schematu, przestrzeń nazw XML i tak dalej, i jest przenoszona do <xref:System.Xml.Schema.XmlSchemaDatatype.ParseValue%2A> metody podczas walidacji zawartości prostej. <xref:System.Xml.Schema.XmlSchemaSet>Obiekt zawiera schematy XML używane do sprawdzania poprawności sprawdzonych XML. <xref:System.Xml.XmlNamespaceManager>Obiekt jest używany do rozpoznawania przestrzeni nazw napotkanych podczas walidacji. Ta <xref:System.Xml.Schema.XmlSchemaValidationFlags> wartość służy do wyłączania niektórych funkcji weryfikacji.

Aby uzyskać więcej informacji na temat <xref:System.Xml.Schema.XmlSchemaValidator.%23ctor%2A> konstruktora, zobacz <xref:System.Xml.Schema.XmlSchemaValidator> dokumentację referencyjną klasy.

### <a name="initializing-validation"></a>Inicjowanie walidacji

Po <xref:System.Xml.Schema.XmlSchemaValidator> skonstruowaniu obiektu istnieją dwie przeciążone <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> metody służące do zainicjowania stanu <xref:System.Xml.Schema.XmlSchemaValidator> obiektu. Poniżej przedstawiono dwie <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> metody.

- <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType>

- <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType>

Metoda Domyślna <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType> inicjuje <xref:System.Xml.Schema.XmlSchemaValidator> obiekt do jego stanu początkowego, a przeciążona <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType> Metoda, która przyjmuje <xref:System.Xml.Schema.XmlSchemaObject> jako parametr inicjuje <xref:System.Xml.Schema.XmlSchemaValidator> obiekt do stanu początkowego dla częściowej walidacji.

Obie <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> metody można wywołać tylko natychmiast po <xref:System.Xml.Schema.XmlSchemaValidator> skonstruowaniu obiektu lub po wywołaniu metody <xref:System.Xml.Schema.XmlSchemaValidator.EndValidation%2A> .

Aby zapoznać się z przykładem <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType> metody, zobacz przykład we wprowadzeniu. Aby uzyskać więcej informacji na temat <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> metody, zobacz <xref:System.Xml.Schema.XmlSchemaValidator> dokumentację dotyczącą klasy.

#### <a name="partial-validation"></a>Częściowe sprawdzanie poprawności

<xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType>Metoda, która przyjmuje <xref:System.Xml.Schema.XmlSchemaObject> jako parametr inicjuje <xref:System.Xml.Schema.XmlSchemaValidator> obiekt do stanu początkowego dla częściowej walidacji.

W poniższym przykładzie <xref:System.Xml.Schema.XmlSchemaObject> jest inicjowane dla częściowej walidacji przy użyciu <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType> metody. `orderNumber`Element schematu jest przesyłany przez wybranie elementu schematu <xref:System.Xml.XmlQualifiedName> w <xref:System.Xml.Schema.XmlSchemaObjectTable> kolekcji zwróconej przez <xref:System.Xml.Schema.XmlSchemaSet.GlobalElements%2A> Właściwość <xref:System.Xml.Schema.XmlSchemaSet> obiektu. <xref:System.Xml.Schema.XmlSchemaValidator>Następnie obiekt sprawdza poprawność tego określonego elementu.

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

Aby uzyskać więcej informacji na temat <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> metody, zobacz <xref:System.Xml.Schema.XmlSchemaValidator> dokumentację dotyczącą klasy.

### <a name="adding-additional-schemas"></a>Dodawanie dodatkowych schematów

<xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A>Metoda <xref:System.Xml.Schema.XmlSchemaValidator> klasy służy do dodawania schematu XML do zestawu schematów używanych podczas walidacji. <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A>Metoda może służyć do symulowania efektu napotkania wbudowanego schematu XML w sprawdzonych XML.

> [!NOTE]
> Docelowa przestrzeń nazw <xref:System.Xml.Schema.XmlSchema> parametru nie może być zgodna z elementem lub atrybutem już napotkanym przez <xref:System.Xml.Schema.XmlSchemaValidator> obiekt.
>
> Jeśli <xref:System.Xml.Schema.XmlSchemaValidationFlags.ProcessInlineSchema?displayProperty=nameWithType> wartość nie została przeniesiona jako parametr do <xref:System.Xml.Schema.XmlSchemaValidator.%23ctor%2A> konstruktora, <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> Metoda nie wykonuje żadnych operacji.

Wynik <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> metody jest zależny od bieżącego kontekstu węzła XML, który jest sprawdzany. Aby uzyskać więcej informacji na temat kontekstów walidacji, zobacz sekcję "kontekst walidacji" w tym temacie.

Aby uzyskać więcej informacji na temat <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> metody, zobacz <xref:System.Xml.Schema.XmlSchemaValidator> dokumentację dotyczącą klasy.

### <a name="validating-elements-attributes-and-content"></a>Walidacja elementów, atrybutów i zawartości

<xref:System.Xml.Schema.XmlSchemaValidator>Klasa zawiera kilka metod służących do sprawdzania poprawności elementów, atrybutów i zawartości w sprawdzonych XML w schematach XML. W poniższej tabeli opisano każdą z tych metod.

|Metoda|Opis|
|------------|-----------------|
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A>|Sprawdza poprawność nazwy elementu w bieżącym kontekście.|
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>|Sprawdza poprawność atrybutu w bieżącym kontekście elementu lub względem obiektu, który <xref:System.Xml.Schema.XmlSchemaAttribute> przeszedł jako parametr do <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> metody.|
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndOfAttributes%2A>|Sprawdza, czy wszystkie wymagane atrybuty w kontekście elementu są obecne i przygotowuje <xref:System.Xml.Schema.XmlSchemaValidator> obiekt do zweryfikowania zawartości podrzędnej elementu.|
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A>|Sprawdza, czy tekst jest dozwolony w kontekście bieżącego elementu i gromadzi tekst do walidacji, jeśli bieżący element ma prostą zawartość.|
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateWhitespace%2A>|Sprawdza, czy w bieżącym kontekście elementu jest dozwolone białe miejsce, i gromadzi białe miejsce do walidacji, czy bieżący element ma prostą zawartość.|
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A>|Sprawdza, czy zawartość tekstowa elementu jest prawidłowa przy uwzględnieniu jego typu danych dla elementów z prostą zawartością i sprawdza, czy zawartość bieżącego elementu jest kompletna dla elementów z zawartością złożoną.|
|<xref:System.Xml.Schema.XmlSchemaValidator.SkipToEndElement%2A>|Pomija sprawdzanie poprawności zawartości bieżącego elementu i przygotowuje <xref:System.Xml.Schema.XmlSchemaValidator> obiekt do walidacji zawartości w kontekście elementu nadrzędnego.|
|<xref:System.Xml.Schema.XmlSchemaValidator.EndValidation%2A>|Zakończenie sprawdzania poprawności i sprawdza ograniczenia tożsamości dla całego dokumentu XML, jeśli <xref:System.Xml.Schema.XmlSchemaValidationFlags.ProcessIdentityConstraints> opcja walidacji jest ustawiona.|

> [!NOTE]
> <xref:System.Xml.Schema.XmlSchemaValidator>Klasa ma zdefiniowane przejście stanu, które wymusza sekwencję i wystąpienia wywołań wykonanych dla każdej z metod opisanych w poprzedniej tabeli. Przejście określonego stanu <xref:System.Xml.Schema.XmlSchemaValidator> klasy jest opisane w sekcji "przechodzenie stanu XmlSchemaValidator" w tym temacie.

Przykład metod używanych do sprawdzania poprawności elementów, atrybutów i zawartości w sprawdzonych XML zawiera przykład w poprzedniej sekcji. Więcej informacji o tych metodach znajduje się w <xref:System.Xml.Schema.XmlSchemaValidator> dokumentacji dotyczącej klas.

#### <a name="validating-content-using-an-xmlvaluegetter"></a>Sprawdzanie poprawności zawartości przy użyciu XmlValueGetter

<xref:System.Xml.Schema.XmlValueGetter> `delegate` Może służyć do przekazywania wartości węzłów atrybutów, tekstu lub białych miejsc jako typów środowiska uruchomieniowego języka wspólnego (CLR) zgodnych z typem języka definicji schematu XML (XSD) atrybutu, tekstu lub odstępu. <xref:System.Xml.Schema.XmlValueGetter> `delegate` Jest przydatny, jeśli wartość CLR atrybutu, tekstu lub pustego węzła jest już dostępna, i unika kosztu konwertowania go na `string` a następnie ponowne przeanalizowanie w celu weryfikacji.

<xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>Metody, <xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A> , i <xref:System.Xml.Schema.XmlSchemaValidator.ValidateWhitespace%2A> są przeciążone i akceptują wartość atrybutu, tekst lub węzły białych miejsc jako `string` lub <xref:System.Xml.Schema.XmlValueGetter> `delegate` .

Następujące metody <xref:System.Xml.Schema.XmlSchemaValidator> klasy akceptują <xref:System.Xml.Schema.XmlValueGetter> `delegate` jako parametr.

- <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>

- <xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A>

- <xref:System.Xml.Schema.XmlSchemaValidator.ValidateWhitespace%2A>

Poniżej przedstawiono przykład pochodzący <xref:System.Xml.Schema.XmlValueGetter> `delegate` z <xref:System.Xml.Schema.XmlSchemaValidator> przykładu klasy we wprowadzeniu. <xref:System.Xml.Schema.XmlValueGetter> `delegate` Zwraca wartość atrybutu jako <xref:System.DateTime> obiekt. Aby sprawdzić poprawność tego <xref:System.DateTime> obiektu zwróconego przez <xref:System.Xml.Schema.XmlValueGetter> , <xref:System.Xml.Schema.XmlSchemaValidator> obiekt najpierw konwertuje go na element ValueType (ValueType jest domyślnym mapowaniem CLR dla typu XSD) dla typu danych atrybutu, a następnie sprawdza aspekty w skonwertowanej wartości.

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

Pełny przykład można <xref:System.Xml.Schema.XmlValueGetter> `delegate` znaleźć w przykładowym wprowadzeniu. Aby uzyskać więcej informacji na temat <xref:System.Xml.Schema.XmlValueGetter> `delegate` , zobacz <xref:System.Xml.Schema.XmlValueGetter> <xref:System.Xml.Schema.XmlSchemaValidator> dokumentację dotyczącą i dokumentacja klasy.

#### <a name="post-schema-validation-information"></a>Po zaweryfikacji schematu — informacje

<xref:System.Xml.Schema.XmlSchemaInfo>Klasa reprezentuje niektóre z podanych po schemacie walidacji węzła XML zweryfikowanego przez <xref:System.Xml.Schema.XmlSchemaValidator> klasę. Różne metody <xref:System.Xml.Schema.XmlSchemaValidator> klasy akceptują <xref:System.Xml.Schema.XmlSchemaInfo> obiekt jako opcjonalny `null` parametr () `out` .

Po pomyślnej weryfikacji właściwości <xref:System.Xml.Schema.XmlSchemaInfo> obiektu są ustawiane z wynikami walidacji. Na przykład po pomyślnej weryfikacji atrybutu przy użyciu <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> metody <xref:System.Xml.Schema.XmlSchemaInfo> obiekt (jeśli określony) <xref:System.Xml.Schema.XmlSchemaInfo.SchemaAttribute%2A> , <xref:System.Xml.Schema.XmlSchemaInfo.SchemaType%2A> ,, <xref:System.Xml.Schema.XmlSchemaInfo.MemberType%2A> i <xref:System.Xml.Schema.XmlSchemaInfo.Validity%2A> właściwości są ustawiane z wynikami walidacji.

Poniższe <xref:System.Xml.Schema.XmlSchemaValidator> metody klasy akceptują <xref:System.Xml.Schema.XmlSchemaInfo> obiekt jako parametr out.

- <xref:System.Xml.Schema.XmlSchemaValidator.SkipToEndElement%2A>

- <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>

- <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>

- <xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A>

- <xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A>

- <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A>

- <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A>

- <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndOfAttributes%2A>

Aby zapoznać się z kompletnym przykładem <xref:System.Xml.Schema.XmlSchemaInfo> klasy, zobacz przykład we wprowadzeniu. Więcej informacji o klasie można <xref:System.Xml.Schema.XmlSchemaInfo> znaleźć w dokumentacji dotyczącej <xref:System.Xml.Schema.XmlSchemaInfo> klas.

### <a name="retrieving-expected-particles-attributes-and-unspecified-default-attributes"></a>Pobieranie oczekiwanych cząsteczek, atrybutów i nieokreślonych atrybutów domyślnych

<xref:System.Xml.Schema.XmlSchemaValidator>Klasa zawiera <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> metody, i, <xref:System.Xml.Schema.XmlSchemaValidator.GetUnspecifiedDefaultAttributes%2A> Aby pobrać oczekiwane cząstki, atrybuty i nieokreślone atrybuty domyślne w bieżącym kontekście walidacji.

#### <a name="retrieving-expected-particles"></a>Pobieranie oczekiwanych cząsteczek

<xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A>Metoda zwraca tablicę <xref:System.Xml.Schema.XmlSchemaParticle> obiektów zawierających oczekiwane cząstki w bieżącym kontekście elementu. Prawidłowe cząstki, które mogą być zwracane przez <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> metodę, są wystąpieniami <xref:System.Xml.Schema.XmlSchemaElement> <xref:System.Xml.Schema.XmlSchemaAny> klas i.

Gdy compositor dla modelu zawartości to `xs:sequence` , zwracana jest tylko Następna cząstka w sekwencji. Jeśli compositor dla modelu zawartości to `xs:all` lub `xs:choice` a, zwracane są wszystkie prawidłowe cząstki, które mogą się pojawić w kontekście bieżącego elementu.

> [!NOTE]
> Jeśli <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> Metoda jest wywoływana natychmiast po wywołaniu <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> metody, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> Metoda zwraca wszystkie elementy globalne.

Na przykład, w schemacie języka definicji schematu XML (XSD) i w poniższym dokumencie XML po walidacji `book` elementu `book` element jest bieżącym kontekstem elementu. <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A>Metoda zwraca tablicę zawierającą pojedynczy <xref:System.Xml.Schema.XmlSchemaElement> obiekt reprezentujący `title` element. Gdy kontekst walidacji jest `title` elementem, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> Metoda zwraca pustą tablicę. Jeśli <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> Metoda jest wywoływana po `title` sprawdzeniu elementu, ale przed `description` zweryfikowaniem elementu, zwraca tablicę zawierającą pojedynczy <xref:System.Xml.Schema.XmlSchemaElement> obiekt reprezentujący `description` element. Jeśli <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> Metoda jest wywoływana po `description` sprawdzeniu elementu, zwraca tablicę zawierającą pojedynczy <xref:System.Xml.Schema.XmlSchemaAny> obiekt reprezentujący symbol wieloznaczny.

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
> Wyniki <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> metod, i <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> <xref:System.Xml.Schema.XmlSchemaValidator> klasy są zależne od bieżącego kontekstu, który jest sprawdzany. Aby uzyskać więcej informacji, zobacz sekcję "kontekst walidacji" w tym temacie.

Aby zapoznać się z przykładem <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> metody, zobacz przykład we wprowadzeniu. Aby uzyskać więcej informacji na temat <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> metody, zobacz <xref:System.Xml.Schema.XmlSchemaValidator> dokumentację dotyczącą klasy.

#### <a name="retrieving-expected-attributes"></a>Pobieranie oczekiwanych atrybutów

<xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A>Metoda zwraca tablicę <xref:System.Xml.Schema.XmlSchemaAttribute> obiektów zawierających oczekiwane atrybuty w bieżącym kontekście elementu.

Na przykład w przykładzie we wprowadzeniu <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> Metoda jest używana do pobierania wszystkich atrybutów `book` elementu.

Jeśli wywołasz <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> metodę natychmiast po <xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A> metodzie, zwracane są wszystkie atrybuty, które mogą pojawić się w dokumencie XML. Jednak w przypadku wywołania <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> metody po jednym lub większej liczbie wywołań do <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> metody zwracane są atrybuty, które nie zostały jeszcze zweryfikowane dla bieżącego elementu.

> [!NOTE]
> Wyniki <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> metod, i <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> <xref:System.Xml.Schema.XmlSchemaValidator> klasy są zależne od bieżącego kontekstu, który jest sprawdzany. Aby uzyskać więcej informacji, zobacz sekcję "kontekst walidacji" w tym temacie.

Aby zapoznać się z przykładem <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> metody, zobacz przykład we wprowadzeniu. Aby uzyskać więcej informacji na temat <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> metody, zobacz <xref:System.Xml.Schema.XmlSchemaValidator> dokumentację dotyczącą klasy.

#### <a name="retrieving-unspecified-default-attributes"></a>Pobieranie nieokreślonych atrybutów domyślnych

<xref:System.Xml.Schema.XmlSchemaValidator.GetUnspecifiedDefaultAttributes%2A>Metoda wypełnia <xref:System.Collections.ArrayList> określone z <xref:System.Xml.Schema.XmlSchemaAttribute> obiektami dla wszystkich atrybutów wartościami domyślnymi, które nie zostały wcześniej zweryfikowane przy użyciu <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> metody w kontekście elementu. <xref:System.Xml.Schema.XmlSchemaValidator.GetUnspecifiedDefaultAttributes%2A>Metoda powinna być wywoływana po wywołaniu <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> metody dla każdego atrybutu w kontekście elementu. <xref:System.Xml.Schema.XmlSchemaValidator.GetUnspecifiedDefaultAttributes%2A>Metoda powinna służyć do określenia, jakie atrybuty domyślne mają zostać wstawione do zweryfikowanego dokumentu XML.

Aby uzyskać więcej informacji na temat <xref:System.Xml.Schema.XmlSchemaValidator.GetUnspecifiedDefaultAttributes%2A> metody, zobacz <xref:System.Xml.Schema.XmlSchemaValidator> dokumentację dotyczącą klasy.

### <a name="handling-schema-validation-events"></a>Obsługa zdarzeń walidacji schematu

Ostrzeżenia i błędy walidacji schematu napotkane podczas walidacji są obsługiwane przez <xref:System.Xml.Schema.XmlSchemaValidator.ValidationEventHandler> zdarzenie <xref:System.Xml.Schema.XmlSchemaValidator> klasy.

Ostrzeżenia dotyczące walidacji schematu mają <xref:System.Xml.Schema.XmlSeverityType> wartość <xref:System.Xml.Schema.XmlSeverityType.Warning> i błędy walidacji schematu mają <xref:System.Xml.Schema.XmlSeverityType> wartość <xref:System.Xml.Schema.XmlSeverityType.Error> . Jeśli nie <xref:System.Xml.Schema.XmlSchemaValidator.ValidationEventHandler> został przypisany, <xref:System.Xml.Schema.XmlSchemaValidationException> jest zgłaszany dla wszystkich błędów walidacji schematu z <xref:System.Xml.Schema.XmlSeverityType> wartością <xref:System.Xml.Schema.XmlSeverityType.Error> . <xref:System.Xml.Schema.XmlSchemaValidationException>Nie jest jednak zgłaszany dla ostrzeżeń dotyczących sprawdzania poprawności schematu z <xref:System.Xml.Schema.XmlSeverityType> wartością <xref:System.Xml.Schema.XmlSeverityType.Warning> .

Poniżej znajduje się przykład <xref:System.Xml.Schema.ValidationEventHandler> , który odbiera ostrzeżenia i błędy walidacji schematu, które zostały wykryte podczas walidacji schematu z przykładu we wprowadzeniu.

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

Pełny przykład można <xref:System.Xml.Schema.ValidationEventHandler> znaleźć w przykładowym wprowadzeniu. Więcej informacji można znaleźć w <xref:System.Xml.Schema.XmlSchemaInfo> dokumentacji dotyczącej klas.

## <a name="xmlschemavalidator-state-transition"></a>XmlSchemaValidator stanu przejścia

<xref:System.Xml.Schema.XmlSchemaValidator>Klasa ma zdefiniowane przejście stanu, które wymusza sekwencję i wystąpienia wywołań wykonanych do każdej metody używanej do sprawdzania poprawności elementów, atrybutów i zawartości w sprawdzonych XML.

W poniższej tabeli opisano przechodzenie stanu <xref:System.Xml.Schema.XmlSchemaValidator> klasy oraz sekwencję i wystąpienia wywołań metod, które można wykonać w każdym stanie.

|Stan|Transition|
|-----------|----------------|
|Walidacja|<xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A>( <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> &#124; TopLevel *)<xref:System.Xml.Schema.XmlSchemaValidator.EndValidation%2A>|
|TopLevel|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateWhitespace%2A><xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A>Element &#124; &#124;|
|Element|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A><xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>* ( <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndOfAttributes%2A> Zawartość \* )? <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A>&#124;<br /><br /> <xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A><xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>\* <xref:System.Xml.Schema.XmlSchemaValidator.SkipToEndElement%2A> &#124;<br /><br /> <xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A><xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>\* <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndOfAttributes%2A> \* <xref:System.Xml.Schema.XmlSchemaValidator.SkipToEndElement%2A> &#124; zawartości|
|Zawartość|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateWhitespace%2A><xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A>Element &#124; &#124;|

> [!NOTE]
> <xref:System.InvalidOperationException>Jest generowany przez każdą z metod w powyższej tabeli, gdy wywołanie metody jest wykonywane w niepoprawnej sekwencji zgodnie z bieżącym stanem <xref:System.Xml.Schema.XmlSchemaValidator> obiektu.

W powyższej tabeli przechodzenia stanu są używane symbole interpunkcyjne do opisywania metod i innych stanów, które mogą być wywoływane dla każdego stanu przejścia stanu <xref:System.Xml.Schema.XmlSchemaValidator> klasy. Używane symbole są tymi samymi symbolami, które znajdują się w dokumentacji XML Standards dla definicji typu dokumentu (DTD).

W poniższej tabeli opisano, jak symbole interpunkcji Znalezione w powyższej tabeli przejścia stanu mają wpływ na metody i inne Stany, które mogą być wywoływane dla każdego stanu w fazie przejścia stanu <xref:System.Xml.Schema.XmlSchemaValidator> klasy.

|Symbol|Opis|
|------------|-----------------|
|&#124;|Można wywołać metodę lub stan (jeden przed paskiem lub po nim).|
|?|Metoda lub stan, który poprzedza znak zapytania, jest opcjonalne, ale jeśli jest wywoływana, może być wywoływana tylko raz.|
|\*|Metoda lub stan poprzedzający \* symbol jest opcjonalny i może być wywoływana więcej niż raz.|

## <a name="validation-context"></a>Kontekst walidacji

Metody <xref:System.Xml.Schema.XmlSchemaValidator> klasy używane do sprawdzania poprawności elementów, atrybutów i zawartości w sprawdzonych XML, zmiana kontekstu walidacji <xref:System.Xml.Schema.XmlSchemaValidator> obiektu. Na przykład <xref:System.Xml.Schema.XmlSchemaValidator.SkipToEndElement%2A> Metoda pomija sprawdzanie poprawności zawartości bieżącego elementu i przygotowuje <xref:System.Xml.Schema.XmlSchemaValidator> obiekt do walidacji zawartości w kontekście elementu nadrzędnego; jest to równoznaczne z pominięciem walidacji dla wszystkich elementów podrzędnych bieżącego elementu, a następnie wywołania <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A> metody.

Wyniki <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> metod, i <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> <xref:System.Xml.Schema.XmlSchemaValidator> klasy są zależne od bieżącego kontekstu, który jest sprawdzany.

W poniższej tabeli opisano wyniki wywołania tych metod po wywołaniu jednej z metod <xref:System.Xml.Schema.XmlSchemaValidator> klasy używanej do walidacji elementów, atrybutów i zawartości w sprawdzonych XML.

|Metoda|GetExpectedParticles|GetExpectedAttributes|AddSchema|
|------------|--------------------------|---------------------------|---------------|
|<xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A>|Jeśli <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> wywoływana jest metoda domyślna, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> zwraca tablicę zawierającą wszystkie elementy globalne.<br /><br /> Jeśli przeciążona <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> Metoda, która przyjmuje <xref:System.Xml.Schema.XmlSchemaObject> jako parametr, jest wywoływana w celu zainicjowania częściowej walidacji elementu, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> zwraca tylko element, do którego <xref:System.Xml.Schema.XmlSchemaValidator> obiekt został zainicjowany.|Jeśli <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> wywoływana jest metoda domyślna, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> zwraca pustą tablicę.<br /><br /> Jeśli Przeciążenie <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> metody, która przyjmuje <xref:System.Xml.Schema.XmlSchemaObject> jako parametr jest wywoływana w celu zainicjowania częściowej walidacji atrybutu, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> zwraca tylko atrybut, do którego <xref:System.Xml.Schema.XmlSchemaValidator> obiekt został zainicjowany.|Dodaje schemat do obiektu, <xref:System.Xml.Schema.XmlSchemaSet> Jeśli nie <xref:System.Xml.Schema.XmlSchemaValidator> ma żadnych błędów przetwarzania wstępnego.|
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A>|Jeśli element context jest prawidłowy, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> zwraca sekwencję elementów oczekiwaną jako elementy podrzędne elementu Context.<br /><br /> Jeśli element context jest nieprawidłowy, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> zwraca pustą tablicę.|Jeśli element kontekstu jest prawidłowy i jeśli żadne wywołanie do nie <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> zostało wcześniej wykonane, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> zwraca listę wszystkich atrybutów zdefiniowanych w elemencie kontekstu.<br /><br /> Jeśli niektóre atrybuty zostały już zweryfikowane, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> zwraca listę pozostałych atrybutów do zweryfikowania.<br /><br /> Jeśli element context jest nieprawidłowy, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> zwraca pustą tablicę.|Tak samo jak powyżej.|
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>|Jeśli atrybut kontekstu jest atrybutem najwyższego poziomu, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> zwraca pustą tablicę.<br /><br /> W przeciwnym razie <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> zwraca sekwencję elementów oczekiwaną jako pierwszy element podrzędny elementu kontekstu.|Jeśli atrybut kontekstu jest atrybutem najwyższego poziomu, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> zwraca pustą tablicę.<br /><br /> W przeciwnym razie <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> zwraca listę pozostałych atrybutów do zweryfikowania.|Tak samo jak powyżej.|
|<xref:System.Xml.Schema.XmlSchemaValidator.GetUnspecifiedDefaultAttributes%2A>|<xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A>zwraca sekwencję elementów oczekiwaną jako pierwszy element podrzędny elementu kontekstu.|<xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A>zwraca listę wymaganych i opcjonalnych atrybutów, które nie zostały jeszcze zweryfikowane dla elementu kontekstu.|Tak samo jak powyżej.|
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndOfAttributes%2A>|<xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A>zwraca sekwencję elementów oczekiwaną jako pierwszy element podrzędny elementu kontekstu.|<xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A>zwraca pustą tablicę.|Tak samo jak powyżej.|
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A>|Jeśli element ContentType elementu context jest mieszany, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> zwraca sekwencję elementów oczekiwaną w następnym położeniu.<br /><br /> Jeśli element ContentType elementu ContextType ma wartość textOnly lub Empty, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> zwraca pustą tablicę.<br /><br /> Jeśli element ContentType elementu ContextType ma wartość ElementOnly, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> zwraca sekwencję elementów oczekiwaną w następnym miejscu, ale wystąpił błąd sprawdzania poprawności.|<xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A>zwraca listę atrybutów elementu kontekstu, które nie zostały zweryfikowane.|Tak samo jak powyżej.|
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateWhitespace%2A>|Jeśli odstępy między kontekstami jest odstępem najwyższego poziomu, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> zwraca pustą tablicę.<br /><br /> W przeciwnym razie <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> zachowanie metody jest takie samo jak w <xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A> .|Jeśli odstępy między kontekstami jest odstępem najwyższego poziomu, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> zwraca pustą tablicę.<br /><br /> W przeciwnym razie <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> zachowanie metody jest takie samo jak w <xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A> .|Tak samo jak powyżej.|
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A>|<xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A>zwraca sekwencję elementów oczekiwaną po elemencie kontekstu (możliwe elementy równorzędne).|<xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A>zwraca listę atrybutów elementu kontekstu, które nie zostały zweryfikowane.<br /><br /> Jeśli element kontekstu nie ma elementu nadrzędnego <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> , funkcja zwróci pustą listę (element context jest obiektem nadrzędnym bieżącego elementu, w którym <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A> został wywołany).|Tak samo jak powyżej.|
|<xref:System.Xml.Schema.XmlSchemaValidator.SkipToEndElement%2A>|Analogicznie jak <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A> .|Analogicznie jak <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A> .|Tak samo jak powyżej.|
|<xref:System.Xml.Schema.XmlSchemaValidator.EndValidation%2A>|Zwraca pustą tablicę.|Zwraca pustą tablicę.|Tak samo jak powyżej.|

> [!NOTE]
> Wartości zwracane przez różne właściwości <xref:System.Xml.Schema.XmlSchemaValidator> klasy nie są zmieniane przez wywołanie dowolnej metody z powyższej tabeli.

## <a name="see-also"></a>Zobacz także

- <xref:System.Xml.Schema.XmlSchemaValidator>
