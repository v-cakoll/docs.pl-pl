---
title: Kompilacja schematu a klasa XmlSchemaCollection
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 76f28770-7126-428f-9ed5-7b5ae8bad5ee
ms.openlocfilehash: 3d517652665d6d0693e141d623483ff8946bbbf4
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84290243"
---
# <a name="xmlschemacollection-schema-compilation"></a><span data-ttu-id="61a3d-102">Kompilacja schematu a klasa XmlSchemaCollection</span><span class="sxs-lookup"><span data-stu-id="61a3d-102">XmlSchemaCollection Schema Compilation</span></span>
<span data-ttu-id="61a3d-103">**XmlSchemaCollection** jest pamięcią podręczną lub biblioteką, w której można przechowywać i sprawdzać dane XML (XDR) oraz schematy języka definicji schematu XML (XSD).</span><span class="sxs-lookup"><span data-stu-id="61a3d-103">The **XmlSchemaCollection** is a cache or library where XML-Data Reduced (XDR) and XML Schema definition language (XSD) schemas can be stored and validated.</span></span> <span data-ttu-id="61a3d-104">Obiekt **XmlSchemaCollection** zwiększa wydajność przez buforowanie schematów w pamięci zamiast uzyskiwania do nich dostępu z pliku lub adresu URL.</span><span class="sxs-lookup"><span data-stu-id="61a3d-104">**XmlSchemaCollection** improves performance by caching schemas in memory instead of accessing them from a file or URL.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="61a3d-105">Chociaż Klasa **XmlSchemaCollection** przechowuje zarówno schematy XDR, jak i schematy XML, każda metoda i właściwość, która pobiera lub zwraca obiekt **XmlSchema** , obsługuje tylko schematy XML.</span><span class="sxs-lookup"><span data-stu-id="61a3d-105">Although the **XmlSchemaCollection** class stores both XDR schemas and XML Schemas, any method and property that takes or returns an **XmlSchema** object supports XML Schemas only.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="61a3d-106"><xref:System.Xml.Schema.XmlSchemaCollection>Klasa jest obecnie przestarzała i została zastąpiona <xref:System.Xml.Schema.XmlSchemaSet> klasą.</span><span class="sxs-lookup"><span data-stu-id="61a3d-106">The <xref:System.Xml.Schema.XmlSchemaCollection> class is now obsolete and has been replaced with the <xref:System.Xml.Schema.XmlSchemaSet> class.</span></span> <span data-ttu-id="61a3d-107">Aby uzyskać więcej informacji na temat <xref:System.Xml.Schema.XmlSchemaSet> klasy, zobacz zestaw [XmlSchemaSet dla kompilacji schematu](xmlschemaset-for-schema-compilation.md).</span><span class="sxs-lookup"><span data-stu-id="61a3d-107">For more information about the <xref:System.Xml.Schema.XmlSchemaSet> class see, [XmlSchemaSet for Schema Compilation](xmlschemaset-for-schema-compilation.md).</span></span>  
  
## <a name="add-schemas-to-the-collection"></a><span data-ttu-id="61a3d-108">Dodaj schematy do kolekcji</span><span class="sxs-lookup"><span data-stu-id="61a3d-108">Add Schemas to the Collection</span></span>  
 <span data-ttu-id="61a3d-109">Schematy są ładowane do kolekcji za pomocą metody **Add** klasy **XmlSchemaCollection**, w której schemat jest skojarzony z identyfikatorem URI przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="61a3d-109">Schemas are loaded to the collection using the **Add** method of **XmlSchemaCollection**, at which time the schema is associated with a namespace URI.</span></span> <span data-ttu-id="61a3d-110">W przypadku schematów XML identyfikator URI przestrzeni nazw będzie zazwyczaj docelowym obszarem nazw dla schematu.</span><span class="sxs-lookup"><span data-stu-id="61a3d-110">For XML Schemas, the namespace URI will typically be the target namespace for the schema.</span></span> <span data-ttu-id="61a3d-111">W przypadku schematów XDR identyfikator URI przestrzeni nazw jest przestrzenią nazw określoną, gdy schemat został dodany do kolekcji.</span><span class="sxs-lookup"><span data-stu-id="61a3d-111">For XDR schemas, the namespace URI is the namespace specified when the schema was added to the collection.</span></span>  
  
## <a name="check-for-a-schema-in-the-collection"></a><span data-ttu-id="61a3d-112">Wyszukaj schemat w kolekcji</span><span class="sxs-lookup"><span data-stu-id="61a3d-112">Check for a Schema in the Collection</span></span>  
 <span data-ttu-id="61a3d-113">Możesz sprawdzić, czy schemat znajduje się w kolekcji przy użyciu metody **Contains** .</span><span class="sxs-lookup"><span data-stu-id="61a3d-113">You can check to see if a schema is in the collection by using the **Contains** method.</span></span> <span data-ttu-id="61a3d-114">Metoda **Contains** pobiera obiekt **XML** (tylko schematy XML) lub ciąg reprezentujący identyfikator URI przestrzeni nazw skojarzony ze schematem (dla schematów XML i schematów XDR).</span><span class="sxs-lookup"><span data-stu-id="61a3d-114">The **Contains** method takes either an **XmlSchema** object (for XML Schemas only) or a string representing the namespace URI associated with the schema (for XML Schemas and XDR schemas).</span></span>  
  
## <a name="retrieve-a-schema-from-the-collection"></a><span data-ttu-id="61a3d-115">Pobierz schemat z kolekcji</span><span class="sxs-lookup"><span data-stu-id="61a3d-115">Retrieve a Schema from the Collection</span></span>  
 <span data-ttu-id="61a3d-116">Schemat z kolekcji można pobrać przy użyciu właściwości **Item** .</span><span class="sxs-lookup"><span data-stu-id="61a3d-116">You can retrieve a schema from the collection by using the **Item** property.</span></span> <span data-ttu-id="61a3d-117">Właściwość **Item** przyjmuje ciąg reprezentujący identyfikator URI przestrzeni nazw skojarzony ze schematem, zazwyczaj jego przestrzeń nazw Target i zwraca obiekt **XmlSchema** .</span><span class="sxs-lookup"><span data-stu-id="61a3d-117">The **Item** property takes a string representing the namespace URI associated with the schema, typically its target namespace, and returns an **XmlSchema** object.</span></span> <span data-ttu-id="61a3d-118">Właściwość **Item** ma zastosowanie tylko do schematów XML.</span><span class="sxs-lookup"><span data-stu-id="61a3d-118">The **Item** property applies to XML Schemas only.</span></span> <span data-ttu-id="61a3d-119">Wartość zwracana jest zawsze odwołaniem null dla schematów XDR, ponieważ nie ma dostępnego modelu obiektów.</span><span class="sxs-lookup"><span data-stu-id="61a3d-119">The return value is always a null reference for XDR schemas because they do not have an object model available.</span></span>  
  
## <a name="validate-xml-documents-using-xmlschemacollection"></a><span data-ttu-id="61a3d-120">Sprawdzanie poprawności dokumentów XML przy użyciu elementu XmlSchemaCollection</span><span class="sxs-lookup"><span data-stu-id="61a3d-120">Validate XML Documents Using XmlSchemaCollection</span></span>  
 <span data-ttu-id="61a3d-121">Można sprawdzić poprawność dokumentu wystąpienia XML za **pomocą XmlSchemaCollection** , tworząc **obiekt XmlSchemaCollection** , dodając schematy do kolekcji i ustawiając właściwość **schematy** w **XmlValidatingReader** , aby przypisać utworzony element **XmlSchemaCollection** do **XmlValidatingReader**.</span><span class="sxs-lookup"><span data-stu-id="61a3d-121">You can validate an XML instance document using an **XmlSchemaCollection** by creating the **XmlSchemaCollection** object, adding your schemas to the collection, and setting the **Schemas** property on the **XmlValidatingReader** to assign the created **XmlSchemaCollection** to the **XmlValidatingReader**.</span></span>  
  
### <a name="improved-performance"></a><span data-ttu-id="61a3d-122">Zwiększona wydajność</span><span class="sxs-lookup"><span data-stu-id="61a3d-122">Improved Performance</span></span>  
 <span data-ttu-id="61a3d-123">Zaleca się, aby w przypadku sprawdzania poprawności więcej niż jednego dokumentu w tym samym schemacie używać elementu **XmlSchemaCollection** , ponieważ zapewnia lepszą wydajność przez buforowanie schematów w pamięci.</span><span class="sxs-lookup"><span data-stu-id="61a3d-123">It is recommended, if you are validating more than one document against the same schema, that you use the **XmlSchemaCollection** because it provides better performance by caching schemas in memory.</span></span>  
  
 <span data-ttu-id="61a3d-124">Poniższy przykład kodu tworzy obiekt **XmlSchemaCollection** , dodaje schematy do kolekcji i ustawia właściwość **schematy** .</span><span class="sxs-lookup"><span data-stu-id="61a3d-124">The following code example creates the **XmlSchemaCollection** object, adds schemas to the collection, and sets the **Schemas** property.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="61a3d-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="61a3d-125">See also</span></span>

- [<span data-ttu-id="61a3d-126">Weryfikacja XDR przy użyciu klasy XmlSchemaCollection</span><span class="sxs-lookup"><span data-stu-id="61a3d-126">XDR Validation with XmlSchemaCollection</span></span>](xdr-validation-with-xmlschemacollection.md)
- [<span data-ttu-id="61a3d-127">Weryfikacja schematu XML (XSD) przy użyciu klasy XmlSchemaCollection</span><span class="sxs-lookup"><span data-stu-id="61a3d-127">XML Schema (XSD) Validation with XmlSchemaCollection</span></span>](xml-schema-xsd-validation-with-xmlschemacollection.md)
