---
title: Porównywanie obiektów przy użyciu tabeli XmlNameTable
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 8d94e041-d340-4ddf-9a2c-d7319e3f4f86
ms.openlocfilehash: 0dd68e8c9beadf26f858a4a5100e2824bbbd4a19
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84292036"
---
# <a name="object-comparison-using-xmlnametable"></a><span data-ttu-id="cba4b-102">Porównywanie obiektów przy użyciu tabeli XmlNameTable</span><span class="sxs-lookup"><span data-stu-id="cba4b-102">Object Comparison Using XmlNameTable</span></span>
<span data-ttu-id="cba4b-103">Element **XmlDocuments**, po utworzeniu, ma tabelę nazw utworzoną dla tego dokumentu.</span><span class="sxs-lookup"><span data-stu-id="cba4b-103">**XmlDocuments**, when created, have a name table created specifically for that document.</span></span> <span data-ttu-id="cba4b-104">Gdy XML jest ładowany do dokumentu lub są tworzone nowe elementy lub atrybuty, nazwy atrybutów i elementów są umieszczane w **XmlNameTable**.</span><span class="sxs-lookup"><span data-stu-id="cba4b-104">When XML is loaded into the document, or new elements or attributes are created, the attribute and element names are put into the **XmlNameTable**.</span></span> <span data-ttu-id="cba4b-105">Można również utworzyć **XmlDocument** przy użyciu istniejącego **NameTable** z innego dokumentu.</span><span class="sxs-lookup"><span data-stu-id="cba4b-105">You can also create an **XmlDocument** using an existing **NameTable** from another document.</span></span> <span data-ttu-id="cba4b-106">Gdy **dokumenty XmlDocument** są tworzone za pomocą konstruktora, który przyjmuje parametr **XmlNameTable** , dokument ma dostęp do nazw węzłów, przestrzeni nazw i prefiksów już przechowywanych w **XmlNameTable**.</span><span class="sxs-lookup"><span data-stu-id="cba4b-106">When **XmlDocuments** are created with the constructor that takes an **XmlNameTable** parameter, the document has access to the node names, namespaces, and prefixes already stored in the **XmlNameTable**.</span></span> <span data-ttu-id="cba4b-107">Niezależnie od sposobu ładowania tabeli nazw do nazw, gdy nazwy są przechowywane w tabeli, nazwy można porównać szybko przy użyciu porównania obiektów zamiast porównywania ciągów.</span><span class="sxs-lookup"><span data-stu-id="cba4b-107">Regardless of how the name table is loaded with names, once the names are stored in the table, names can be compared quickly using object comparison instead of string comparison.</span></span> <span data-ttu-id="cba4b-108">Ciągi można także dodawać do tabeli nazw przy użyciu <xref:System.Xml.NameTable.Add%2A> .</span><span class="sxs-lookup"><span data-stu-id="cba4b-108">Strings can also be added to the name table using the <xref:System.Xml.NameTable.Add%2A>.</span></span> <span data-ttu-id="cba4b-109">Poniższy przykład kodu przedstawia utworzoną tabelę nazw **i ciąg ciągu, który jest** dodawany do tabeli.</span><span class="sxs-lookup"><span data-stu-id="cba4b-109">The following code sample shows a name table being created and the string **MyString** being added to the table.</span></span> <span data-ttu-id="cba4b-110">Po tym elemencie **XmlDocument** zostanie utworzony przy użyciu tej tabeli, a nazwy elementów i atrybutów w **pliku. XML** są dodawane do istniejącej tabeli nazw.</span><span class="sxs-lookup"><span data-stu-id="cba4b-110">After that, an **XmlDocument** is created using that table, and the element and attribute names in **Myfile.xml** are added to the existing name table.</span></span>  
  
```vb  
Dim nt As New NameTable()  
nt.Add("MyString")  
Dim doc As New XmlDocument(nt)  
doc.Load("Myfile.xml")  
```  
  
```csharp  
NameTable nt = new NameTable();  
nt.Add("MyString");  
XmlDocument doc = new XmlDocument(nt);  
doc.Load("Myfile.xml");  
```  
  
 <span data-ttu-id="cba4b-111">Poniższy przykład kodu pokazuje Tworzenie dokumentu, dwa nowe elementy dodawane do dokumentu, które również dodaje je do tabeli nazw dokumentów i porównanie obiektów dla nazw.</span><span class="sxs-lookup"><span data-stu-id="cba4b-111">The following code example shows the creation of a document, two new elements being added to the document, which also adds them to the document name table, and the object comparison on the names.</span></span>  
  
```vb  
Dim doc1 As XmlDocument = imp.CreateDocument()  
Dim node1 As XmlElement = doc.CreateElement("node1")  
Dim doc2 As XmlDocument = imp.CreateDocument()  
Dim node2 As XmlElement = doc.CreateElement("node2")  
if (CType(node1.Name, object) = CType(node2.Name, object))  
```  
  
```csharp  
XmlDocument doc1 = imp.CreateDocument();  
node1 = doc1.CreateElement ("node1");  
XmlDocument doc2 = imp.CreateDocument();  
node2 = doc2.CreateElement ("node1");  
if (((object)node1.Name) == ((object)node2.Name))  
{ ...  
```  
  
 <span data-ttu-id="cba4b-112">Powyższy scenariusz tabeli nazw przekazaną między dwoma dokumentami jest typowy, gdy ten sam typ dokumentu jest przetwarzany wielokrotnie, na przykład w kolejności dokumentów w witrynie handlu elektronicznego, który jest zgodny ze schematem języka definicji schematu XML (XSD) lub definicją typu dokumentu (DTD), a te same ciągi są powtórzone.</span><span class="sxs-lookup"><span data-stu-id="cba4b-112">The above scenario of a name table passed between two documents is typical when the same type of document is being processed repeatedly, such as order documents at an ecommerce site, which conform to an XML Schema definition language (XSD) schema or document type definition (DTD) and the same strings are repeated.</span></span> <span data-ttu-id="cba4b-113">Korzystanie z tej samej tabeli nazw zapewnia poprawę wydajności, ponieważ ta sama nazwa elementu występuje w wielu dokumentach.</span><span class="sxs-lookup"><span data-stu-id="cba4b-113">Using the same name table gives a performance improvement, as the same element name occurs in multiple documents.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cba4b-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="cba4b-114">See also</span></span>

- [<span data-ttu-id="cba4b-115">XML Document Object Model (DOM)</span><span class="sxs-lookup"><span data-stu-id="cba4b-115">XML Document Object Model (DOM)</span></span>](xml-document-object-model-dom.md)
