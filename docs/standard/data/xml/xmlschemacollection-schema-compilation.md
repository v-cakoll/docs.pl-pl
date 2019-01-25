---
title: XmlSchemaCollection Schema Compilation
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 76f28770-7126-428f-9ed5-7b5ae8bad5ee
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3d47fa4d4ef7a55182dd27aa6f64542fec1fa99c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54704319"
---
# <a name="xmlschemacollection-schema-compilation"></a><span data-ttu-id="bb013-102">XmlSchemaCollection Schema Compilation</span><span class="sxs-lookup"><span data-stu-id="bb013-102">XmlSchemaCollection Schema Compilation</span></span>
<span data-ttu-id="bb013-103">**Użyciu klasy XmlSchemaCollection** pamięci podręcznej lub biblioteki, gdzie danych XML (XDR) i schematu XML schematów języka (XSD) definicji mogą być przechowywane i zweryfikowane.</span><span class="sxs-lookup"><span data-stu-id="bb013-103">The **XmlSchemaCollection** is a cache or library where XML-Data Reduced (XDR) and XML Schema definition language (XSD) schemas can be stored and validated.</span></span> <span data-ttu-id="bb013-104">**Użyciu klasy XmlSchemaCollection** zwiększa wydajność, buforowanie schematów w pamięci, a nie dostępu do nich z pliku lub adres URL.</span><span class="sxs-lookup"><span data-stu-id="bb013-104">**XmlSchemaCollection** improves performance by caching schemas in memory instead of accessing them from a file or URL.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="bb013-105">Mimo że **użyciu klasy XmlSchemaCollection** klasa przechowuje schematy XDR i schematów XML, wszystkie metody i właściwości, która przyjmuje i zwraca **XmlSchema** obiekt obsługuje tylko schematów XML.</span><span class="sxs-lookup"><span data-stu-id="bb013-105">Although the **XmlSchemaCollection** class stores both XDR schemas and XML Schemas, any method and property that takes or returns an **XmlSchema** object supports XML Schemas only.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="bb013-106"><xref:System.Xml.Schema.XmlSchemaCollection> Klasa jest obecnie przestarzały i został zastąpiony <xref:System.Xml.Schema.XmlSchemaSet> klasy.</span><span class="sxs-lookup"><span data-stu-id="bb013-106">The <xref:System.Xml.Schema.XmlSchemaCollection> class is now obsolete and has been replaced with the <xref:System.Xml.Schema.XmlSchemaSet> class.</span></span> <span data-ttu-id="bb013-107">Aby uzyskać więcej informacji na temat <xref:System.Xml.Schema.XmlSchemaSet> , zobacz klasę [klasa XmlSchemaSet na potrzeby kompilacji schematu](../../../../docs/standard/data/xml/xmlschemaset-for-schema-compilation.md).</span><span class="sxs-lookup"><span data-stu-id="bb013-107">For more information about the <xref:System.Xml.Schema.XmlSchemaSet> class see, [XmlSchemaSet for Schema Compilation](../../../../docs/standard/data/xml/xmlschemaset-for-schema-compilation.md).</span></span>  
  
## <a name="add-schemas-to-the-collection"></a><span data-ttu-id="bb013-108">Dodaj schematy do kolekcji</span><span class="sxs-lookup"><span data-stu-id="bb013-108">Add Schemas to the Collection</span></span>  
 <span data-ttu-id="bb013-109">Schematy są załadowane do kolekcji przy użyciu **Dodaj** metody **użyciu klasy XmlSchemaCollection**, co jest skojarzony z identyfikatora URI obszaru nazw schematu.</span><span class="sxs-lookup"><span data-stu-id="bb013-109">Schemas are loaded to the collection using the **Add** method of **XmlSchemaCollection**, at which time the schema is associated with a namespace URI.</span></span> <span data-ttu-id="bb013-110">Dla schematów XML identyfikator URI przestrzeni nazw będzie zazwyczaj docelowego obszaru nazw dla schematu.</span><span class="sxs-lookup"><span data-stu-id="bb013-110">For XML Schemas, the namespace URI will typically be the target namespace for the schema.</span></span> <span data-ttu-id="bb013-111">Schematy XDR, aby uzyskać identyfikator URI przestrzeni nazw jest przestrzeń nazw określona, jeśli schemat został dodany do kolekcji.</span><span class="sxs-lookup"><span data-stu-id="bb013-111">For XDR schemas, the namespace URI is the namespace specified when the schema was added to the collection.</span></span>  
  
## <a name="check-for-a-schema-in-the-collection"></a><span data-ttu-id="bb013-112">Sprawdź, czy schemat w kolekcji</span><span class="sxs-lookup"><span data-stu-id="bb013-112">Check for a Schema in the Collection</span></span>  
 <span data-ttu-id="bb013-113">Można sprawdzić, czy schemat jest w kolekcji przy użyciu **zawiera** metody.</span><span class="sxs-lookup"><span data-stu-id="bb013-113">You can check to see if a schema is in the collection by using the **Contains** method.</span></span> <span data-ttu-id="bb013-114">**Zawiera** metoda przyjmuje albo **XmlSchema** obiektu (dla tylko schematy XML) lub ciąg reprezentujący identyfikator URI przestrzeni nazw skojarzone ze schematem (dla schematów XML, schematy i XDR).</span><span class="sxs-lookup"><span data-stu-id="bb013-114">The **Contains** method takes either an **XmlSchema** object (for XML Schemas only) or a string representing the namespace URI associated with the schema (for XML Schemas and XDR schemas).</span></span>  
  
## <a name="retrieve-a-schema-from-the-collection"></a><span data-ttu-id="bb013-115">Pobieranie schematu z kolekcji</span><span class="sxs-lookup"><span data-stu-id="bb013-115">Retrieve a Schema from the Collection</span></span>  
 <span data-ttu-id="bb013-116">Można pobrać schematu z kolekcji za pomocą **elementu** właściwości.</span><span class="sxs-lookup"><span data-stu-id="bb013-116">You can retrieve a schema from the collection by using the **Item** property.</span></span> <span data-ttu-id="bb013-117">**Elementu** właściwość przyjmuje ciąg reprezentujący przestrzeń nazw identyfikator URI skojarzony ze schematem, zwykle jego docelowego obszaru nazw i zwraca **XmlSchema** obiektu.</span><span class="sxs-lookup"><span data-stu-id="bb013-117">The **Item** property takes a string representing the namespace URI associated with the schema, typically its target namespace, and returns an **XmlSchema** object.</span></span> <span data-ttu-id="bb013-118">**Elementu** właściwość dotyczy tylko schematów XML.</span><span class="sxs-lookup"><span data-stu-id="bb013-118">The **Item** property applies to XML Schemas only.</span></span> <span data-ttu-id="bb013-119">Wartość zwracana jest zawsze odwołanie o wartości null dla schematów XDR, ponieważ nie mają model obiektów, które jest dostępne.</span><span class="sxs-lookup"><span data-stu-id="bb013-119">The return value is always a null reference for XDR schemas because they do not have an object model available.</span></span>  
  
## <a name="validate-xml-documents-using-xmlschemacollection"></a><span data-ttu-id="bb013-120">Sprawdź poprawność dokumentów XML za pomocą użyciu klasy XmlSchemaCollection</span><span class="sxs-lookup"><span data-stu-id="bb013-120">Validate XML Documents Using XmlSchemaCollection</span></span>  
 <span data-ttu-id="bb013-121">Sprawdzanie poprawności XML wystąpienie dokumentu za pomocą **użyciu klasy XmlSchemaCollection** , tworząc **użyciu klasy XmlSchemaCollection** obiektu, dodając swoje schematy do kolekcji i ustawienie **schematów**  właściwość **elementu XmlValidatingReader** można przypisać utworzony **użyciu klasy XmlSchemaCollection** do **elementu XmlValidatingReader**.</span><span class="sxs-lookup"><span data-stu-id="bb013-121">You can validate an XML instance document using an **XmlSchemaCollection** by creating the **XmlSchemaCollection** object, adding your schemas to the collection, and setting the **Schemas** property on the **XmlValidatingReader** to assign the created **XmlSchemaCollection** to the **XmlValidatingReader**.</span></span>  
  
### <a name="improved-performance"></a><span data-ttu-id="bb013-122">Lepsza wydajność</span><span class="sxs-lookup"><span data-stu-id="bb013-122">Improved Performance</span></span>  
 <span data-ttu-id="bb013-123">Jest to zalecane, Jeśli zatwierdzasz więcej niż jeden dokument względem tego samego schematu, że używasz **użyciu klasy XmlSchemaCollection** ponieważ zapewnia lepszą wydajność, buforując schematów w pamięci.</span><span class="sxs-lookup"><span data-stu-id="bb013-123">It is recommended, if you are validating more than one document against the same schema, that you use the **XmlSchemaCollection** because it provides better performance by caching schemas in memory.</span></span>  
  
 <span data-ttu-id="bb013-124">Poniższy przykład kodu tworzy **użyciu klasy XmlSchemaCollection** obiektu, schematy są dodawane do kolekcji i ustawia **schematów** właściwości.</span><span class="sxs-lookup"><span data-stu-id="bb013-124">The following code example creates the **XmlSchemaCollection** object, adds schemas to the collection, and sets the **Schemas** property.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="bb013-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="bb013-125">See also</span></span>

- [<span data-ttu-id="bb013-126">Weryfikacja XDR przy użyciu klasy XmlSchemaCollection</span><span class="sxs-lookup"><span data-stu-id="bb013-126">XDR Validation with XmlSchemaCollection</span></span>](../../../../docs/standard/data/xml/xdr-validation-with-xmlschemacollection.md)
- [<span data-ttu-id="bb013-127">Weryfikacja schematu XML (XSD) przy użyciu klasy XmlSchemaCollection</span><span class="sxs-lookup"><span data-stu-id="bb013-127">XML Schema (XSD) Validation with XmlSchemaCollection</span></span>](../../../../docs/standard/data/xml/xml-schema-xsd-validation-with-xmlschemacollection.md)
