---
title: Porównanie obiektów przy użyciu tabeli XmlNameTable
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 8d94e041-d340-4ddf-9a2c-d7319e3f4f86
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 814f5434dd0473b3b1dd613a2eba14a828c464d9
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2018
ms.locfileid: "43862785"
---
# <a name="object-comparison-using-xmlnametable"></a><span data-ttu-id="040cf-102">Porównanie obiektów przy użyciu tabeli XmlNameTable</span><span class="sxs-lookup"><span data-stu-id="040cf-102">Object Comparison Using XmlNameTable</span></span>
<span data-ttu-id="040cf-103">**XmlDocuments**, podczas tworzenia tabeli nazwę specjalnie do tego dokumentu.</span><span class="sxs-lookup"><span data-stu-id="040cf-103">**XmlDocuments**, when created, have a name table created specifically for that document.</span></span> <span data-ttu-id="040cf-104">Gdy XML jest ładowany do dokumentu lub są tworzone nowe elementy lub atrybuty, nazwy atrybutu i elementu są umieszczane w **tabeli XmlNameTable**.</span><span class="sxs-lookup"><span data-stu-id="040cf-104">When XML is loaded into the document, or new elements or attributes are created, the attribute and element names are put into the **XmlNameTable**.</span></span> <span data-ttu-id="040cf-105">Można również utworzyć **XmlDocument** korzystania z istniejącej **niepowtarzającymi** z innego dokumentu.</span><span class="sxs-lookup"><span data-stu-id="040cf-105">You can also create an **XmlDocument** using an existing **NameTable** from another document.</span></span> <span data-ttu-id="040cf-106">Gdy **XmlDocuments** są tworzone przy użyciu konstruktora, który przyjmuje **tabeli XmlNameTable** parametru dokument ma dostęp do nazwy węzłów, przestrzenie nazw i prefiksy, które już są przechowywane w  **Tabeli XmlNameTable**.</span><span class="sxs-lookup"><span data-stu-id="040cf-106">When **XmlDocuments** are created with the constructor that takes an **XmlNameTable** parameter, the document has access to the node names, namespaces, and prefixes already stored in the **XmlNameTable**.</span></span> <span data-ttu-id="040cf-107">Niezależnie od tego, jak tabela nazw jest ładowany z nazwami, gdy nazwy są przechowywane w tabeli, nazwy można porównać szybko za pomocą obiektu porównania, zamiast porównywania ciągów.</span><span class="sxs-lookup"><span data-stu-id="040cf-107">Regardless of how the name table is loaded with names, once the names are stored in the table, names can be compared quickly using object comparison instead of string comparison.</span></span> <span data-ttu-id="040cf-108">Ciągi mogą być również dodawane do tabeli nazwy przy użyciu <xref:System.Xml.NameTable.Add%2A>.</span><span class="sxs-lookup"><span data-stu-id="040cf-108">Strings can also be added to the name table using the <xref:System.Xml.NameTable.Add%2A>.</span></span> <span data-ttu-id="040cf-109">Poniższy przykładowy kod przedstawia tabelę nazw, tworzonych i ciąg **mójCiąg** dodawane do tabeli.</span><span class="sxs-lookup"><span data-stu-id="040cf-109">The following code sample shows a name table being created and the string **MyString** being added to the table.</span></span> <span data-ttu-id="040cf-110">Po tym **XmlDocument** jest tworzony przy użyciu tej tabeli, a także nazw elementów i atrybutów w **Myfile.xml** są dodawane do istniejącej tabeli nazwy.</span><span class="sxs-lookup"><span data-stu-id="040cf-110">After that, an **XmlDocument** is created using that table, and the element and attribute names in **Myfile.xml** are added to the existing name table.</span></span>  
  
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
  
 <span data-ttu-id="040cf-111">W poniższym przykładzie kodu pokazano tworzenie obiektu dokumentu, dwa nowe elementy są dodawane do dokumentu, który dodaje je do tabeli nazwę dokumentu i porównanie obiektu na nazwach.</span><span class="sxs-lookup"><span data-stu-id="040cf-111">The following code example shows the creation of a document, two new elements being added to the document, which also adds them to the document name table, and the object comparison on the names.</span></span>  
  
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
  
 <span data-ttu-id="040cf-112">Powyższym scenariuszu tabeli nazwy przekazywane między dwoma dokumentami jest typowe w przypadku, gdy ten sam typ dokumentu jest przetwarzany wielokrotnie, takich jak dokumenty w witrynie handlu elektronicznego, które są zgodne z typ schematu XML definicji język (XSD) schematu lub dokumentu Definition (DTD) i tej samej ciągi są powtarzane.</span><span class="sxs-lookup"><span data-stu-id="040cf-112">The above scenario of a name table passed between two documents is typical when the same type of document is being processed repeatedly, such as order documents at an ecommerce site, which conform to an XML Schema definition language (XSD) schema or document type definition (DTD) and the same strings are repeated.</span></span> <span data-ttu-id="040cf-113">Używanie taką samą tabelą nazw zapewnia zwiększenie wydajności, zgodnie z takiej samej nazwie elementu odbywa się w wielu dokumentów.</span><span class="sxs-lookup"><span data-stu-id="040cf-113">Using the same name table gives a performance improvement, as the same element name occurs in multiple documents.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="040cf-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="040cf-114">See also</span></span>

- [<span data-ttu-id="040cf-115">Model DOM (XML Document Object Model)</span><span class="sxs-lookup"><span data-stu-id="040cf-115">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
