---
title: Kompilacja schematu kolekcji XmlSchemaCollection
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 76f28770-7126-428f-9ed5-7b5ae8bad5ee
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d64443f213603b1f5db9c256acc88e998e3f009a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33571488"
---
# <a name="xmlschemacollection-schema-compilation"></a><span data-ttu-id="1d4f9-102">Kompilacja schematu kolekcji XmlSchemaCollection</span><span class="sxs-lookup"><span data-stu-id="1d4f9-102">XmlSchemaCollection Schema Compilation</span></span>
<span data-ttu-id="1d4f9-103">**Kolekcji XmlSchemaCollection** pamięci podręcznej lub biblioteki, gdzie schematy języka (XSD) definicji XML danych (XDR) i schemat XML może być przechowywane i sprawdzania poprawności.</span><span class="sxs-lookup"><span data-stu-id="1d4f9-103">The **XmlSchemaCollection** is a cache or library where XML-Data Reduced (XDR) and XML Schema definition language (XSD) schemas can be stored and validated.</span></span> <span data-ttu-id="1d4f9-104">**Kolekcji XmlSchemaCollection** zwiększa wydajność, buforując schematów w pamięci zamiast dostępu do nich z pliku lub adres URL.</span><span class="sxs-lookup"><span data-stu-id="1d4f9-104">**XmlSchemaCollection** improves performance by caching schemas in memory instead of accessing them from a file or URL.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1d4f9-105">Mimo że **kolekcji XmlSchemaCollection** klasy przechowuje zarówno schematy XDR i schematów XML, wszystkie metody i właściwości, która przyjmuje lub zwraca **schematu XML** obiekt obsługuje tylko schematy XML.</span><span class="sxs-lookup"><span data-stu-id="1d4f9-105">Although the **XmlSchemaCollection** class stores both XDR schemas and XML Schemas, any method and property that takes or returns an **XmlSchema** object supports XML Schemas only.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="1d4f9-106"><xref:System.Xml.Schema.XmlSchemaCollection> Klasy jest teraz przestarzałe i zostało zastąpione <xref:System.Xml.Schema.XmlSchemaSet> klasy.</span><span class="sxs-lookup"><span data-stu-id="1d4f9-106">The <xref:System.Xml.Schema.XmlSchemaCollection> class is now obsolete and has been replaced with the <xref:System.Xml.Schema.XmlSchemaSet> class.</span></span> <span data-ttu-id="1d4f9-107">Aby uzyskać więcej informacji na temat <xref:System.Xml.Schema.XmlSchemaSet> , zobacz klasy [XmlSchemaSet kompilowania schematu](../../../../docs/standard/data/xml/xmlschemaset-for-schema-compilation.md).</span><span class="sxs-lookup"><span data-stu-id="1d4f9-107">For more information about the <xref:System.Xml.Schema.XmlSchemaSet> class see, [XmlSchemaSet for Schema Compilation](../../../../docs/standard/data/xml/xmlschemaset-for-schema-compilation.md).</span></span>  
  
## <a name="add-schemas-to-the-collection"></a><span data-ttu-id="1d4f9-108">Dodaj schematy do kolekcji</span><span class="sxs-lookup"><span data-stu-id="1d4f9-108">Add Schemas to the Collection</span></span>  
 <span data-ttu-id="1d4f9-109">Schematy są załadowane do kolekcji przy użyciu **Dodaj** metody **kolekcji XmlSchemaCollection**, które jest skojarzony z identyfikatorem URI przestrzeni nazw schematu.</span><span class="sxs-lookup"><span data-stu-id="1d4f9-109">Schemas are loaded to the collection using the **Add** method of **XmlSchemaCollection**, at which time the schema is associated with a namespace URI.</span></span> <span data-ttu-id="1d4f9-110">Dla schematów XML identyfikator URI przestrzeni nazw będzie zazwyczaj docelowego obszaru nazw dla schematu.</span><span class="sxs-lookup"><span data-stu-id="1d4f9-110">For XML Schemas, the namespace URI will typically be the target namespace for the schema.</span></span> <span data-ttu-id="1d4f9-111">Schematy XDR, aby uzyskać identyfikator URI przestrzeni nazw jest przestrzeń nazw określona, jeśli schemat został dodany do kolekcji.</span><span class="sxs-lookup"><span data-stu-id="1d4f9-111">For XDR schemas, the namespace URI is the namespace specified when the schema was added to the collection.</span></span>  
  
## <a name="check-for-a-schema-in-the-collection"></a><span data-ttu-id="1d4f9-112">Sprawdź, czy schemat w kolekcji</span><span class="sxs-lookup"><span data-stu-id="1d4f9-112">Check for a Schema in the Collection</span></span>  
 <span data-ttu-id="1d4f9-113">Można sprawdzić, czy schemat jest w kolekcji przy użyciu **zawiera** metody.</span><span class="sxs-lookup"><span data-stu-id="1d4f9-113">You can check to see if a schema is in the collection by using the **Contains** method.</span></span> <span data-ttu-id="1d4f9-114">**Zawiera** metoda przyjmuje albo **schematu XML** obiektu (na potrzeby tylko schematy XML) lub ciąg reprezentujący identyfikator URI przestrzeni nazw skojarzone ze schematem (dla schematów schematów XML i XDR).</span><span class="sxs-lookup"><span data-stu-id="1d4f9-114">The **Contains** method takes either an **XmlSchema** object (for XML Schemas only) or a string representing the namespace URI associated with the schema (for XML Schemas and XDR schemas).</span></span>  
  
## <a name="retrieve-a-schema-from-the-collection"></a><span data-ttu-id="1d4f9-115">Pobieranie schematu z kolekcji</span><span class="sxs-lookup"><span data-stu-id="1d4f9-115">Retrieve a Schema from the Collection</span></span>  
 <span data-ttu-id="1d4f9-116">Można pobrać schematu z kolekcji za pomocą **elementu** właściwości.</span><span class="sxs-lookup"><span data-stu-id="1d4f9-116">You can retrieve a schema from the collection by using the **Item** property.</span></span> <span data-ttu-id="1d4f9-117">**Elementu** właściwość przyjmuje ciąg reprezentujący przestrzeń nazw identyfikator URI skojarzony ze schematem, zwykle jego docelowy obszar nazw i zwraca **schematu XML** obiektu.</span><span class="sxs-lookup"><span data-stu-id="1d4f9-117">The **Item** property takes a string representing the namespace URI associated with the schema, typically its target namespace, and returns an **XmlSchema** object.</span></span> <span data-ttu-id="1d4f9-118">**Elementu** właściwość dotyczy tylko schematy XML.</span><span class="sxs-lookup"><span data-stu-id="1d4f9-118">The **Item** property applies to XML Schemas only.</span></span> <span data-ttu-id="1d4f9-119">Zwracana wartość jest zawsze odwołanie o wartości null dla schematy XDR, ponieważ nie mają model obiektów, które jest dostępne.</span><span class="sxs-lookup"><span data-stu-id="1d4f9-119">The return value is always a null reference for XDR schemas because they do not have an object model available.</span></span>  
  
## <a name="validate-xml-documents-using-xmlschemacollection"></a><span data-ttu-id="1d4f9-120">Sprawdzanie poprawności dokumentów XML za pomocą kolekcji XmlSchemaCollection</span><span class="sxs-lookup"><span data-stu-id="1d4f9-120">Validate XML Documents Using XmlSchemaCollection</span></span>  
 <span data-ttu-id="1d4f9-121">Sprawdzanie poprawności XML wystąpienia dokumentu za pomocą **kolekcji XmlSchemaCollection** tworząc **kolekcji XmlSchemaCollection** obiektu, Dodawanie użytkownika schematy do kolekcji, a ustawienie **schematów**  właściwość **elementu XmlValidatingReader** można przypisać utworzony **kolekcji XmlSchemaCollection** do **elementu XmlValidatingReader**.</span><span class="sxs-lookup"><span data-stu-id="1d4f9-121">You can validate an XML instance document using an **XmlSchemaCollection** by creating the **XmlSchemaCollection** object, adding your schemas to the collection, and setting the **Schemas** property on the **XmlValidatingReader** to assign the created **XmlSchemaCollection** to the **XmlValidatingReader**.</span></span>  
  
### <a name="improved-performance"></a><span data-ttu-id="1d4f9-122">Większa wydajność</span><span class="sxs-lookup"><span data-stu-id="1d4f9-122">Improved Performance</span></span>  
 <span data-ttu-id="1d4f9-123">Jest to zalecane, jeśli jest sprawdzana poprawność więcej niż jeden dokument względem tego samego schematu, możesz użyć **kolekcji XmlSchemaCollection** ponieważ zapewnia lepszą wydajność, buforując schematów w pamięci.</span><span class="sxs-lookup"><span data-stu-id="1d4f9-123">It is recommended, if you are validating more than one document against the same schema, that you use the **XmlSchemaCollection** because it provides better performance by caching schemas in memory.</span></span>  
  
 <span data-ttu-id="1d4f9-124">Poniższy przykład kodu tworzy **kolekcji XmlSchemaCollection** obiektu, dodaje do kolekcji schematów i ustawia **schematy** właściwości.</span><span class="sxs-lookup"><span data-stu-id="1d4f9-124">The following code example creates the **XmlSchemaCollection** object, adds schemas to the collection, and sets the **Schemas** property.</span></span>  
  
```vb  
Dim tr as XmlTextReader = new XmlTextReader("Books.xml")  
Dim vr as XmlValidatingReader = new XmlValidatingReader(tr)  
Dim xsc as XmlSchemaCollection = new XmlSchemaCollection  
xsc.Add("urn:bookstore-schema", "Books.xsd")  
vr.Schemas.Add(xsc)  
```  
  
```csharp  
XmlTextReader tr = new XmlTextReader("Books.xml");  
XmlValidatingReader vr = new XmlValidatingReader(tr);  
XmlSchemaCollection xsc = new XmlSchemaCollection();  
xsc.Add("urn:bookstore-schema", "Books.xsd");    
vr.Schemas.Add(xsc);  
```  
  
## <a name="see-also"></a><span data-ttu-id="1d4f9-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1d4f9-125">See Also</span></span>  
 [<span data-ttu-id="1d4f9-126">Weryfikacja XDR przy użyciu klasy XmlSchemaCollection</span><span class="sxs-lookup"><span data-stu-id="1d4f9-126">XDR Validation with XmlSchemaCollection</span></span>](../../../../docs/standard/data/xml/xdr-validation-with-xmlschemacollection.md)  
 [<span data-ttu-id="1d4f9-127">Weryfikacja schematu XML (XSD) przy użyciu klasy XmlSchemaCollection</span><span class="sxs-lookup"><span data-stu-id="1d4f9-127">XML Schema (XSD) Validation with XmlSchemaCollection</span></span>](../../../../docs/standard/data/xml/xml-schema-xsd-validation-with-xmlschemacollection.md)
