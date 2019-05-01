---
title: Weryfikacja schematu przy użyciu klasy XPathNavigator
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 81fa0e41-d9c9-46f0-b22b-50da839c77f5
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 335e6578767c130760f322aa2b015ea7b0f317f9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62026994"
---
# <a name="schema-validation-using-xpathnavigator"></a><span data-ttu-id="0b164-102">Weryfikacja schematu przy użyciu klasy XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="0b164-102">Schema Validation using XPathNavigator</span></span>
<span data-ttu-id="0b164-103">Za pomocą <xref:System.Xml.XmlDocument> klasy, można sprawdzić poprawność zawartości XML zawartych w <xref:System.Xml.XmlDocument> obiektu na dwa sposoby.</span><span class="sxs-lookup"><span data-stu-id="0b164-103">Using the <xref:System.Xml.XmlDocument> class, you can validate the XML content contained in an <xref:System.Xml.XmlDocument> object in two ways.</span></span> <span data-ttu-id="0b164-104">Pierwszym sposobem jest do weryfikowania zawartości XML przy użyciu sprawdzania poprawności <xref:System.Xml.XmlReader> obiektu i drugim sposobem jest użycie <xref:System.Xml.XmlDocument.Validate%2A> metody <xref:System.Xml.XmlDocument> klasy.</span><span class="sxs-lookup"><span data-stu-id="0b164-104">The first way is to validate the XML content using a validating <xref:System.Xml.XmlReader> object and the second way is to use the <xref:System.Xml.XmlDocument.Validate%2A> method of the <xref:System.Xml.XmlDocument> class.</span></span> <span data-ttu-id="0b164-105">Można również wykonać walidacji tylko do odczytu zawartości przy użyciu XML <xref:System.Xml.XPath.XPathDocument> klasy.</span><span class="sxs-lookup"><span data-stu-id="0b164-105">You can also perform read-only validation of XML content using the <xref:System.Xml.XPath.XPathDocument> class.</span></span>  
  
## <a name="validating-xml-data"></a><span data-ttu-id="0b164-106">Sprawdzanie poprawności danych XML</span><span class="sxs-lookup"><span data-stu-id="0b164-106">Validating XML Data</span></span>  
 <span data-ttu-id="0b164-107"><xref:System.Xml.XmlDocument> Klasy nie można zweryfikować za pomocą definicji DTD lub XML schematu definicji języka (XSD) sprawdzanie poprawności schematu domyślnie dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="0b164-107">The <xref:System.Xml.XmlDocument> class does not validate an XML document using either DTD or XML schema definition language (XSD) schema validation by default.</span></span> <span data-ttu-id="0b164-108">Sprawdza tylko, że jest poprawnie sformułowany dokument XML.</span><span class="sxs-lookup"><span data-stu-id="0b164-108">It only verifies that the XML document is well formed.</span></span>  
  
 <span data-ttu-id="0b164-109">Pierwszym sposobem Sprawdź poprawność dokumentu XML jest do walidacji dokumentu, ponieważ jest ładowany do <xref:System.Xml.XmlDocument> przy użyciu sprawdzania poprawności <xref:System.Xml.XmlReader> obiektu.</span><span class="sxs-lookup"><span data-stu-id="0b164-109">The first way to validate an XML document is to validate the document as it is loaded into an <xref:System.Xml.XmlDocument> object using a validating <xref:System.Xml.XmlReader> object.</span></span> <span data-ttu-id="0b164-110">Drugi sposób polega na weryfikowanie wcześniej bez typu dokumentu XML, przy użyciu <xref:System.Xml.XmlDocument.Validate%2A> metody <xref:System.Xml.XmlDocument> klasy.</span><span class="sxs-lookup"><span data-stu-id="0b164-110">The second way is to validate a previously untyped XML document using the <xref:System.Xml.XmlDocument.Validate%2A> method of the <xref:System.Xml.XmlDocument> class.</span></span> <span data-ttu-id="0b164-111">W obu przypadkach zmiany zweryfikowanych dokumentu XML może być sprawdzony ponownie przy użyciu <xref:System.Xml.XmlDocument.Validate%2A> metody <xref:System.Xml.XmlDocument> klasy.</span><span class="sxs-lookup"><span data-stu-id="0b164-111">In both cases, changes to the validated XML document can be revalidated using the <xref:System.Xml.XmlDocument.Validate%2A> method of the <xref:System.Xml.XmlDocument> class.</span></span>  
  
### <a name="validating-a-document-as-it-is-loaded"></a><span data-ttu-id="0b164-112">Sprawdzanie poprawności dokumentu w postaci, w jakiej jest ładowany.</span><span class="sxs-lookup"><span data-stu-id="0b164-112">Validating a Document as it is Loaded</span></span>  
 <span data-ttu-id="0b164-113">Sprawdzanie poprawności <xref:System.Xml.XmlReader> obiekt jest tworzony przez przekazanie <xref:System.Xml.XmlReaderSettings> obiekt <xref:System.Xml.XmlReader.Create%2A> metody <xref:System.Xml.XmlReader> klasy, która przyjmuje <xref:System.Xml.XmlReaderSettings> obiektu jako parametr.</span><span class="sxs-lookup"><span data-stu-id="0b164-113">A validating <xref:System.Xml.XmlReader> object is created by passing an <xref:System.Xml.XmlReaderSettings> object to the <xref:System.Xml.XmlReader.Create%2A> method of the <xref:System.Xml.XmlReader> class that takes an <xref:System.Xml.XmlReaderSettings> object as a parameter.</span></span> <span data-ttu-id="0b164-114"><xref:System.Xml.XmlReaderSettings> Przekazano obiekt jako parametr ma <xref:System.Xml.XmlReaderSettings.ValidationType%2A> właściwością `Schema` a schematu XML w dokumencie XML zawartych w <xref:System.Xml.XmlDocument> obiekt dodany do jego <xref:System.Xml.XmlReaderSettings.Schemas%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="0b164-114">The <xref:System.Xml.XmlReaderSettings> object passed as a parameter has a <xref:System.Xml.XmlReaderSettings.ValidationType%2A> property set to `Schema` and an XML Schema for the XML document contained in the <xref:System.Xml.XmlDocument> object added to its <xref:System.Xml.XmlReaderSettings.Schemas%2A> property.</span></span> <span data-ttu-id="0b164-115">Sprawdzanie poprawności <xref:System.Xml.XmlReader> obiekt jest następnie używany do tworzenia <xref:System.Xml.XmlDocument> obiektu.</span><span class="sxs-lookup"><span data-stu-id="0b164-115">The validating <xref:System.Xml.XmlReader> object is then used to create the <xref:System.Xml.XmlDocument> object.</span></span>  
  
 <span data-ttu-id="0b164-116">Poniższy przykład sprawdza `contosoBooks.xml` plików jest ładowany do <xref:System.Xml.XmlDocument> obiektu, tworząc <xref:System.Xml.XmlDocument> przy użyciu sprawdzania poprawności <xref:System.Xml.XmlReader> obiektu.</span><span class="sxs-lookup"><span data-stu-id="0b164-116">The following example validates the `contosoBooks.xml` file as it is loaded into the <xref:System.Xml.XmlDocument> object by creating the <xref:System.Xml.XmlDocument> object using a validating <xref:System.Xml.XmlReader> object.</span></span> <span data-ttu-id="0b164-117">Ponieważ dokument XML jest nieprawidłowa zgodnie z jego schematu, są generowane, nie ostrzeżeń ani błędów sprawdzania poprawności schematu.</span><span class="sxs-lookup"><span data-stu-id="0b164-117">Because the XML document is valid according to its schema, no schema validation errors or warnings are generated.</span></span>  
  
```vb  
Imports System  
Imports System.Xml  
Imports System.Xml.Schema  
Imports System.Xml.XPath  
  
Class ValidatingReaderExample  
  
    Shared Sub Main(ByVal args() As String)  
  
        Try  
            Dim settings As XmlReaderSettings = New XmlReaderSettings()  
            settings.Schemas.Add("http://www.contoso.com/books", "contosoBooks.xsd")  
            settings.ValidationType = ValidationType.Schema  
  
            Dim reader As XmlReader = XmlReader.Create("contosoBooks.xml", settings)  
  
            Dim document As XmlDocument = New XmlDocument()  
            document.Load(reader)  
            Dim navigator As XPathNavigator = document.CreateNavigator()  
  
        Catch e As Exception  
            Console.WriteLine("ValidatingReaderExample.Exception: {0}", e.Message)  
        End Try  
  
    End Sub  
  
    Shared Sub SchemaValidationHandler(ByVal sender As Object, ByVal e As ValidationEventArgs)  
  
        Select Case e.Severity  
            Case XmlSeverityType.Error  
                Console.WriteLine("Schema Validation Error: {0}", e.Message)  
                Exit Sub  
            Case XmlSeverityType.Warning  
                Console.WriteLine("Schema Validation Warning: {0}", e.Message)  
                Exit Sub  
        End Select  
  
    End Sub  
  
End Class  
```  
  
```csharp  
using System;  
using System.Xml;  
using System.Xml.Schema;  
using System.Xml.XPath;  
  
class ValidatingReaderExample  
{  
    static void Main(string[] args)  
    {  
        try  
        {  
            XmlReaderSettings settings = new XmlReaderSettings();  
            settings.Schemas.Add("http://www.contoso.com/books", "contosoBooks.xsd");  
            settings.ValidationType = ValidationType.Schema;  
  
            XmlReader reader = XmlReader.Create("contosoBooks.xml", settings);  
  
            XmlDocument document = new XmlDocument();  
            document.Load(reader);  
            XPathNavigator navigator = document.CreateNavigator();  
        }  
        catch (Exception e)  
        {  
            Console.WriteLine("ValidatingReaderExample.Exception: {0}", e.Message);  
        }  
    }  
  
    static void SchemaValidationHandler(object sender, ValidationEventArgs e)  
    {  
        switch (e.Severity)  
        {  
            case XmlSeverityType.Error:  
                Console.WriteLine("Schema Validation Error: {0}", e.Message);  
                break;  
            case XmlSeverityType.Warning:  
                Console.WriteLine("Schema Validation Warning: {0}", e.Message);  
                break;  
        }  
    }  
}  
```  
  
 <span data-ttu-id="0b164-118">Przykład przyjmuje `contosoBooks.xml` pliku jako dane wejściowe.</span><span class="sxs-lookup"><span data-stu-id="0b164-118">The example takes the `contosoBooks.xml` file as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
 <span data-ttu-id="0b164-119">Przykład pobiera również `contosoBooks.xsd` jako dane wejściowe.</span><span class="sxs-lookup"><span data-stu-id="0b164-119">The example also takes the `contosoBooks.xsd` as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#3](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xsd#3)]  
  
 <span data-ttu-id="0b164-120">W powyższym przykładzie <xref:System.Xml.Schema.XmlSchemaValidationException> zostanie zgłoszony, gdy <xref:System.Xml.XmlDocument.Load%2A> jest wywoływana, jeśli dowolny typ atrybutu lub elementu nie jest zgodny z odpowiedniego typu, określona w schemacie sprawdzania poprawności.</span><span class="sxs-lookup"><span data-stu-id="0b164-120">In the above example, an <xref:System.Xml.Schema.XmlSchemaValidationException> will be thrown when <xref:System.Xml.XmlDocument.Load%2A> is called if any attribute or element type does not match the corresponding type specified in the validating schema.</span></span> <span data-ttu-id="0b164-121">Jeśli <xref:System.Xml.XmlReaderSettings.ValidationEventHandler> jest ustawiona na sprawdzanie poprawności <xref:System.Xml.XmlReader>, <xref:System.Xml.XmlReaderSettings.ValidationEventHandler> będzie wywoływana zawsze wtedy, gdy zostanie osiągnięty nieprawidłowego typu.</span><span class="sxs-lookup"><span data-stu-id="0b164-121">If a <xref:System.Xml.XmlReaderSettings.ValidationEventHandler> is set on the validating <xref:System.Xml.XmlReader>, the <xref:System.Xml.XmlReaderSettings.ValidationEventHandler> will get called whenever an invalid type is encountered.</span></span>  
  
 <span data-ttu-id="0b164-122"><xref:System.Xml.Schema.XmlSchemaException> Zgłaszany w sytuacji, gdy atrybut lub element z <xref:System.Xml.XPath.XPathNavigator.TypedValue%2A> równa `invalid` odbywa się przez <xref:System.Xml.XPath.XPathNavigator>.</span><span class="sxs-lookup"><span data-stu-id="0b164-122">An <xref:System.Xml.Schema.XmlSchemaException> will be thrown when an attribute or element with <xref:System.Xml.XPath.XPathNavigator.TypedValue%2A> set to `invalid` is accessed by the <xref:System.Xml.XPath.XPathNavigator>.</span></span>  
  
 <span data-ttu-id="0b164-123"><xref:System.Xml.Schema.XmlSchemaInfo.Validity%2A> Właściwość może służyć do określenia czy poszczególne atrybut lub element obowiązuje podczas uzyskiwania dostępu do atrybutów lub elementów z <xref:System.Xml.XPath.XPathNavigator>.</span><span class="sxs-lookup"><span data-stu-id="0b164-123">The <xref:System.Xml.Schema.XmlSchemaInfo.Validity%2A> property can be used to determine whether or not an individual attribute or element is valid when accessing attributes or elements with the <xref:System.Xml.XPath.XPathNavigator>.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0b164-124">Podczas ładowania dokumentu XML do <xref:System.Xml.XmlDocument> obiektu za pomocą skojarzonego schematu, który definiuje wartości domyślne <xref:System.Xml.XmlDocument> obiektu traktuje te ustawienia domyślne tak, jakby były one wyświetlane w dokumencie XML.</span><span class="sxs-lookup"><span data-stu-id="0b164-124">When an XML document is loaded into an <xref:System.Xml.XmlDocument> object with an associated schema that defines default values, the <xref:System.Xml.XmlDocument> object treats these defaults as if they appeared in the XML document.</span></span> <span data-ttu-id="0b164-125">Oznacza to, że <xref:System.Xml.XPath.XPathNavigator.IsEmptyElement%2A> właściwość zawsze zwraca `false` element, który został przyjmujące wartości domyślne ze schematu, nawet jeśli w dokumencie XML został zapisany jako pusty element.</span><span class="sxs-lookup"><span data-stu-id="0b164-125">This means that the <xref:System.Xml.XPath.XPathNavigator.IsEmptyElement%2A> property  always returns `false` for an element that was defaulted from the schema, even if in the XML document it was written as an empty element.</span></span>  
  
### <a name="validating-a-document-using-the-validate-method"></a><span data-ttu-id="0b164-126">Sprawdzanie poprawności dokumentu przy użyciu metody sprawdzania poprawności</span><span class="sxs-lookup"><span data-stu-id="0b164-126">Validating a Document using the Validate Method</span></span>  
 <span data-ttu-id="0b164-127"><xref:System.Xml.XmlDocument.Validate%2A> Metody <xref:System.Xml.XmlDocument> klasy weryfikuje zawarte w dokumencie XML <xref:System.Xml.XmlDocument> obiektu względem schematów określone w <xref:System.Xml.XmlDocument> obiektu <xref:System.Xml.XmlDocument.Schemas%2A> właściwości i wykonuje rozszerzeniu zestaw informacji.</span><span class="sxs-lookup"><span data-stu-id="0b164-127">The <xref:System.Xml.XmlDocument.Validate%2A> method of the <xref:System.Xml.XmlDocument> class validates the XML document contained in an <xref:System.Xml.XmlDocument> object against the schemas specified in the <xref:System.Xml.XmlDocument> object's <xref:System.Xml.XmlDocument.Schemas%2A> property and performs infoset augmentation.</span></span> <span data-ttu-id="0b164-128">Wynik jest wcześniej bez typu dokumentu XML w <xref:System.Xml.XmlDocument> obiektu zastąpione wpisane dokumentu.</span><span class="sxs-lookup"><span data-stu-id="0b164-128">The result is a previously untyped XML document in the <xref:System.Xml.XmlDocument> object replaced with a typed document.</span></span>  
  
 <span data-ttu-id="0b164-129"><xref:System.Xml.XmlDocument> Obiektu raporty schematu błędy i ostrzeżenia walidacji za pomocą <xref:System.Xml.Schema.ValidationEventHandler> delegowany przekazany jako parametr do <xref:System.Xml.XmlDocument.Validate%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="0b164-129">The <xref:System.Xml.XmlDocument> object reports schema validation errors and warnings using the <xref:System.Xml.Schema.ValidationEventHandler> delegate passed as a parameter to the <xref:System.Xml.XmlDocument.Validate%2A> method.</span></span>  
  
 <span data-ttu-id="0b164-130">Poniższy przykład sprawdza `contosoBooks.xml` zawarte w pliku <xref:System.Xml.XmlDocument> obiektu względem `contosoBooks.xsd` zawartych w schemacie <xref:System.Xml.XmlDocument> obiektu <xref:System.Xml.XmlDocument.Schemas%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="0b164-130">The following example validates the `contosoBooks.xml` file contained in the <xref:System.Xml.XmlDocument> object against the `contosoBooks.xsd` schema contained in the <xref:System.Xml.XmlDocument> object's <xref:System.Xml.XmlDocument.Schemas%2A> property.</span></span>  
  
```vb  
Imports System  
Imports System.Xml  
Imports System.Xml.Schema  
Imports System.Xml.XPath  
  
Class ValidateExample  
  
    Shared Sub Main(ByVal args() As String)  
  
        Dim document As XmlDocument = New XmlDocument()  
        document.Load("contosoBooks.xml")  
        Dim navigator As XPathNavigator = document.CreateNavigator()  
  
        document.Schemas.Add("http://www.contoso.com/books", "contosoBooks.xsd")  
        Dim validation As ValidationEventHandler = New ValidationEventHandler(AddressOf SchemaValidationHandler)  
  
        document.Validate(validation)  
  
    End Sub  
  
    Shared Sub SchemaValidationHandler(ByVal sender As Object, ByVal e As ValidationEventArgs)  
  
        Select Case e.Severity  
            Case XmlSeverityType.Error  
                Console.WriteLine("Schema Validation Error: {0}", e.Message)  
                Exit Sub  
            Case XmlSeverityType.Warning  
                Console.WriteLine("Schema Validation Warning: {0}", e.Message)  
                Exit Sub  
        End Select  
  
    End Sub  
  
End Class  
```  
  
```csharp  
using System;  
using System.Xml;  
using System.Xml.Schema;  
using System.Xml.XPath;  
  
class ValidateExample  
{  
    static void Main(string[] args)  
    {  
        XmlDocument document = new XmlDocument();  
        document.Load("contosoBooks.xml");  
        XPathNavigator navigator = document.CreateNavigator();  
  
        document.Schemas.Add("http://www.contoso.com/books", "contosoBooks.xsd");  
        ValidationEventHandler validation = new ValidationEventHandler(SchemaValidationHandler);  
  
        document.Validate(validation);  
    }  
  
    static void SchemaValidationHandler(object sender, ValidationEventArgs e)  
    {  
        switch (e.Severity)  
        {  
            case XmlSeverityType.Error:  
                Console.WriteLine("Schema Validation Error: {0}", e.Message);  
                break;  
            case XmlSeverityType.Warning:  
                Console.WriteLine("Schema Validation Warning: {0}", e.Message);  
                break;  
        }  
    }  
}  
```  
  
 <span data-ttu-id="0b164-131">Przykład przyjmuje `contosoBooks.xml` pliku jako dane wejściowe.</span><span class="sxs-lookup"><span data-stu-id="0b164-131">The example takes the `contosoBooks.xml` file as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
 <span data-ttu-id="0b164-132">Przykład pobiera również `contosoBooks.xsd` jako dane wejściowe.</span><span class="sxs-lookup"><span data-stu-id="0b164-132">The example also takes the `contosoBooks.xsd` as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#3](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xsd#3)]  
  
### <a name="validating-modifications"></a><span data-ttu-id="0b164-133">Sprawdzanie poprawności zmian</span><span class="sxs-lookup"><span data-stu-id="0b164-133">Validating Modifications</span></span>  
 <span data-ttu-id="0b164-134">Po dokonaniu modyfikacji dokumentu XML, można sprawdzić poprawność modyfikacji względem schematu dla dokumentów XML za pomocą <xref:System.Xml.XmlDocument.Validate%2A> metody <xref:System.Xml.XmlDocument> klasy.</span><span class="sxs-lookup"><span data-stu-id="0b164-134">After modifications are made to an XML document, you can validate the modifications against the schema for the XML document using the <xref:System.Xml.XmlDocument.Validate%2A> method of the <xref:System.Xml.XmlDocument> class.</span></span>  
  
 <span data-ttu-id="0b164-135">Poniższy przykład sprawdza `contosoBooks.xml` plików jest ładowany do <xref:System.Xml.XmlDocument> obiektu, tworząc <xref:System.Xml.XmlDocument> przy użyciu sprawdzania poprawności <xref:System.Xml.XmlReader> obiektu.</span><span class="sxs-lookup"><span data-stu-id="0b164-135">The following example validates the `contosoBooks.xml` file as it is loaded into the <xref:System.Xml.XmlDocument> object by creating the <xref:System.Xml.XmlDocument> object using a validating <xref:System.Xml.XmlReader> object.</span></span> <span data-ttu-id="0b164-136">Dokument XML jest pomyślnie zweryfikowane, ponieważ został załadowany bez generowania żadnych ostrzeżeń ani błędów sprawdzania poprawności schematu.</span><span class="sxs-lookup"><span data-stu-id="0b164-136">The XML document is validated successfully as it is loaded without generating any schema validation errors or warnings.</span></span> <span data-ttu-id="0b164-137">Przykład następnie udostępnia dwie zmiany w dokumencie XML, które są nieprawidłowe, zgodnie z opisem w `contosoBooks.xsd` schematu.</span><span class="sxs-lookup"><span data-stu-id="0b164-137">The example then makes two modifications to the XML document that are invalid according to the `contosoBooks.xsd` schema.</span></span> <span data-ttu-id="0b164-138">Pierwszy modyfikacji wstawia nieprawidłowy element podrzędny spowodowało błąd walidacji schematu, a drugi modyfikacji ustawia wartość węzła typu wartości, która jest nieprawidłowa przy uwzględnieniu typu węzła spowodowało wyjątek.</span><span class="sxs-lookup"><span data-stu-id="0b164-138">The first modification inserts an invalid child element resulting in a schema validation error, and the second modification sets the value of a typed node to a value that is invalid according to the type of the node resulting in an exception.</span></span>  
  
```vb  
Imports System  
Imports System.Xml  
Imports System.Xml.Schema  
Imports System.Xml.XPath  
  
Class ValidatingReaderExample  
  
    Shared Sub Main(ByVal args() As String)  
  
        Try  
            Dim settings As XmlReaderSettings = New XmlReaderSettings()  
            settings.Schemas.Add("http://www.contoso.com/books", "contosoBooks.xsd")  
            settings.ValidationType = ValidationType.Schema  
  
            Dim reader As XmlReader = XmlReader.Create("contosoBooks.xml", settings)  
  
            Dim document As XmlDocument = New XmlDocument()  
            document.Load(reader)  
            Dim navigator As XPathNavigator = document.CreateNavigator()  
  
            Dim validation As ValidationEventHandler = New ValidationEventHandler(AddressOf SchemaValidationHandler)  
  
            navigator.MoveToChild("bookstore", "http://www.contoso.com/books")  
            navigator.MoveToChild("book", "http://www.contoso.com/books")  
            navigator.MoveToChild("author", "http://www.contoso.com/books")  
  
            navigator.AppendChild("<title>Book Title</title>")  
  
            document.Validate(validation)  
  
            navigator.MoveToParent()  
            navigator.MoveToChild("price", "http://www.contoso.com/books")  
            navigator.SetTypedValue(DateTime.Now)  
        Catch e As Exception  
            Console.WriteLine("ValidatingReaderExample.Exception: {0}", e.Message)  
        End Try  
  
    End Sub  
  
    Shared Sub SchemaValidationHandler(ByVal sender As Object, ByVal e As ValidationEventArgs)  
  
        Select Case e.Severity  
            Case XmlSeverityType.Error  
                Console.WriteLine("Schema Validation Error: {0}", e.Message)  
                Exit Sub  
            Case XmlSeverityType.Warning  
                Console.WriteLine("Schema Validation Warning: {0}", e.Message)  
                Exit Sub  
        End Select  
  
    End Sub  
  
End Class  
```  
  
```csharp  
using System;  
using System.Xml;  
using System.Xml.Schema;  
using System.Xml.XPath;  
  
class ValidatingReaderExample  
{  
    static void Main(string[] args)  
    {  
        try  
        {  
            XmlReaderSettings settings = new XmlReaderSettings();  
            settings.Schemas.Add("http://www.contoso.com/books", "contosoBooks.xsd");  
            settings.ValidationType = ValidationType.Schema;  
  
            XmlReader reader = XmlReader.Create("contosoBooks.xml", settings);  
  
            XmlDocument document = new XmlDocument();  
            document.Load(reader);  
            XPathNavigator navigator = document.CreateNavigator();  
  
            ValidationEventHandler validation = new ValidationEventHandler(SchemaValidationHandler);  
  
            navigator.MoveToChild("bookstore", "http://www.contoso.com/books");  
            navigator.MoveToChild("book", "http://www.contoso.com/books");  
            navigator.MoveToChild("author", "http://www.contoso.com/books");  
  
            navigator.AppendChild("<title>Book Title</title>");  
  
            document.Validate(validation);  
  
            navigator.MoveToParent();  
            navigator.MoveToChild("price", "http://www.contoso.com/books");  
            navigator.SetTypedValue(DateTime.Now);  
        }  
        catch (Exception e)  
        {  
            Console.WriteLine("ValidatingReaderExample.Exception: {0}", e.Message);  
        }  
    }  
  
    static void SchemaValidationHandler(object sender, ValidationEventArgs e)  
    {  
        switch (e.Severity)  
        {  
            case XmlSeverityType.Error:  
                Console.WriteLine("Schema Validation Error: {0}", e.Message);  
                break;  
            case XmlSeverityType.Warning:  
                Console.WriteLine("Schema Validation Warning: {0}", e.Message);  
                break;  
        }  
    }  
}  
```  
  
 <span data-ttu-id="0b164-139">Przykład przyjmuje `contosoBooks.xml` pliku jako dane wejściowe.</span><span class="sxs-lookup"><span data-stu-id="0b164-139">The example takes the `contosoBooks.xml` file as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
 <span data-ttu-id="0b164-140">Przykład pobiera również `contosoBooks.xsd` jako dane wejściowe.</span><span class="sxs-lookup"><span data-stu-id="0b164-140">The example also takes the `contosoBooks.xsd` as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#3](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xsd#3)]  
  
 <span data-ttu-id="0b164-141">W powyższym przykładzie dwie zmiany zostaną wprowadzone do dokumentu XML zawartych w <xref:System.Xml.XmlDocument> obiektu.</span><span class="sxs-lookup"><span data-stu-id="0b164-141">In the example above, two modifications are made to the XML document contained in the <xref:System.Xml.XmlDocument> object.</span></span> <span data-ttu-id="0b164-142">Zgodnie z dokumentu XML została załadowana, wszelkie błędy sprawdzania poprawności schematu, napotkano będzie zostały obsłużone przez metodę programu obsługi zdarzeń sprawdzania poprawności i wyświetlony w konsoli.</span><span class="sxs-lookup"><span data-stu-id="0b164-142">As the XML document was loaded, any schema validation errors encountered would have been handled by the validation event handler method and written to the console.</span></span>  
  
 <span data-ttu-id="0b164-143">W tym przykładzie błędy sprawdzania poprawności zostały wprowadzone po dokumentu XML została załadowana, a znaleziono za pomocą <xref:System.Xml.XmlDocument.Validate%2A> metody <xref:System.Xml.XmlDocument> klasy.</span><span class="sxs-lookup"><span data-stu-id="0b164-143">In this example, the validation errors were introduced after the XML document was loaded and were found using the <xref:System.Xml.XmlDocument.Validate%2A> method of the <xref:System.Xml.XmlDocument> class.</span></span>  
  
 <span data-ttu-id="0b164-144">Zmiany dokonane za pomocą <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> metody <xref:System.Xml.XPath.XPathNavigator> klasy spowodowało <xref:System.InvalidCastException> ponieważ nowa wartość jest nieprawidłowa przy uwzględnieniu typu schematu węzła.</span><span class="sxs-lookup"><span data-stu-id="0b164-144">Modifications made using the <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> method of the <xref:System.Xml.XPath.XPathNavigator> class resulted in an <xref:System.InvalidCastException> because the new value was invalid according to the schema type of the node.</span></span>  
  
 <span data-ttu-id="0b164-145">Aby uzyskać więcej informacji o modyfikowaniu wartości za pomocą <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> metody, zobacz [modyfikowanie danych XML przy użyciu klasy XPathNavigator](../../../../docs/standard/data/xml/modify-xml-data-using-xpathnavigator.md) tematu.</span><span class="sxs-lookup"><span data-stu-id="0b164-145">For more information about modifying values using the <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> method, see the [Modify XML Data using XPathNavigator](../../../../docs/standard/data/xml/modify-xml-data-using-xpathnavigator.md) topic.</span></span>  
  
### <a name="read-only-validation"></a><span data-ttu-id="0b164-146">Sprawdzanie poprawności tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="0b164-146">Read-Only Validation</span></span>  
 <span data-ttu-id="0b164-147"><xref:System.Xml.XPath.XPathDocument> Klasy jest tylko do odczytu, w pamięci reprezentacją dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="0b164-147">The <xref:System.Xml.XPath.XPathDocument> class is a read-only, in-memory representation of an XML document.</span></span> <span data-ttu-id="0b164-148">Zarówno <xref:System.Xml.XPath.XPathDocument> klasy i <xref:System.Xml.XmlDocument> tworzenia klasy <xref:System.Xml.XPath.XPathNavigator> obiekty do nawigowania i edycji dokumentów XML.</span><span class="sxs-lookup"><span data-stu-id="0b164-148">Both the <xref:System.Xml.XPath.XPathDocument> class and the <xref:System.Xml.XmlDocument> class create <xref:System.Xml.XPath.XPathNavigator> objects to navigate and edit XML documents.</span></span> <span data-ttu-id="0b164-149">Ponieważ <xref:System.Xml.XPath.XPathDocument> klasa jest klasą tylko do odczytu <xref:System.Xml.XPath.XPathNavigator> użytkownika zwróciła obiekt <xref:System.Xml.XPath.XPathDocument> obiektów nie można edytować dokumentu XML zawartych w <xref:System.Xml.XPath.XPathDocument> obiektu.</span><span class="sxs-lookup"><span data-stu-id="0b164-149">Because the <xref:System.Xml.XPath.XPathDocument> class is a read-only class, <xref:System.Xml.XPath.XPathNavigator> object's returned from <xref:System.Xml.XPath.XPathDocument> objects cannot edit the XML document contained in the <xref:System.Xml.XPath.XPathDocument> object.</span></span>  
  
 <span data-ttu-id="0b164-150">W przypadku sprawdzania poprawności, można utworzyć <xref:System.Xml.XPath.XPathDocument> obiektu tak samo, jak tworzysz <xref:System.Xml.XmlDocument> przy użyciu sprawdzania poprawności <xref:System.Xml.XmlReader> obiektu zgodnie z opisem we wcześniejszej części tego tematu.</span><span class="sxs-lookup"><span data-stu-id="0b164-150">In the case of validation, you can create an <xref:System.Xml.XPath.XPathDocument> object just like you create an <xref:System.Xml.XmlDocument> object using a validating <xref:System.Xml.XmlReader> object as described earlier in this topic.</span></span> <span data-ttu-id="0b164-151"><xref:System.Xml.XPath.XPathDocument> Obiektu sprawdza poprawność dokumentu XML jest ładowany, ale ponieważ nie można edytować danych XML w <xref:System.Xml.XPath.XPathDocument> obiektu, nie można ponownie sprawdź poprawność dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="0b164-151">The <xref:System.Xml.XPath.XPathDocument> object validates the XML document as it is loaded, but because you cannot edit the XML data in the <xref:System.Xml.XPath.XPathDocument> object, you cannot revalidate the XML document.</span></span>  
  
 <span data-ttu-id="0b164-152">Aby uzyskać więcej informacji na temat tylko do odczytu i edycji <xref:System.Xml.XPath.XPathNavigator> obiekty, zobacz [odczytywania danych XML przy użyciu klas XPathDocument i XmlDocument](../../../../docs/standard/data/xml/reading-xml-data-using-xpathdocument-and-xmldocument.md) tematu.</span><span class="sxs-lookup"><span data-stu-id="0b164-152">For more information about read-only and editable <xref:System.Xml.XPath.XPathNavigator> objects, see the [Reading XML Data using XPathDocument and XmlDocument](../../../../docs/standard/data/xml/reading-xml-data-using-xpathdocument-and-xmldocument.md) topic.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0b164-153">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0b164-153">See also</span></span>

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- [<span data-ttu-id="0b164-154">Przetwarzanie danych XML przy użyciu modelu danych XPath</span><span class="sxs-lookup"><span data-stu-id="0b164-154">Process XML Data Using the XPath Data Model</span></span>](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)
- [<span data-ttu-id="0b164-155">Wczytywanie danych XML przy użyciu klas XPathDocument i XmlDocument</span><span class="sxs-lookup"><span data-stu-id="0b164-155">Reading XML Data using XPathDocument and XmlDocument</span></span>](../../../../docs/standard/data/xml/reading-xml-data-using-xpathdocument-and-xmldocument.md)
- [<span data-ttu-id="0b164-156">Wybieranie, obliczanie i dopasowywanie danych XML przy użyciu klasy XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="0b164-156">Selecting, Evaluating and Matching XML Data using XPathNavigator</span></span>](../../../../docs/standard/data/xml/selecting-evaluating-and-matching-xml-data-using-xpathnavigator.md)
- [<span data-ttu-id="0b164-157">Uzyskiwanie dostępu do danych XML przy użyciu klasy XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="0b164-157">Accessing XML Data using XPathNavigator</span></span>](../../../../docs/standard/data/xml/accessing-xml-data-using-xpathnavigator.md)
- [<span data-ttu-id="0b164-158">Edytowanie danych XML przy użyciu klasy XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="0b164-158">Editing XML Data using XPathNavigator</span></span>](../../../../docs/standard/data/xml/editing-xml-data-using-xpathnavigator.md)
