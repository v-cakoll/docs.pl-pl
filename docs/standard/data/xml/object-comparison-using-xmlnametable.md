---
title: XmlNameTable przy użyciu porównanie obiektów
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 8d94e041-d340-4ddf-9a2c-d7319e3f4f86
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 09f717cb4c09c1e35b9472b7b549f1d3edf0dd15
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="object-comparison-using-xmlnametable"></a><span data-ttu-id="364fb-102">XmlNameTable przy użyciu porównanie obiektów</span><span class="sxs-lookup"><span data-stu-id="364fb-102">Object Comparison Using XmlNameTable</span></span>
<span data-ttu-id="364fb-103">**XmlDocuments**, podczas tworzenia tabeli nazwy specjalnie do tego dokumentu.</span><span class="sxs-lookup"><span data-stu-id="364fb-103">**XmlDocuments**, when created, have a name table created specifically for that document.</span></span> <span data-ttu-id="364fb-104">Gdy XML jest ładowany do dokumentu lub nowych elementów lub atrybutów są tworzone, nazwy atrybutu i elementu są umieszczane w **XmlNameTable**.</span><span class="sxs-lookup"><span data-stu-id="364fb-104">When XML is loaded into the document, or new elements or attributes are created, the attribute and element names are put into the **XmlNameTable**.</span></span> <span data-ttu-id="364fb-105">Można również utworzyć **XmlDocument** przy użyciu istniejącego **niepowtarzającymi** z innego dokumentu.</span><span class="sxs-lookup"><span data-stu-id="364fb-105">You can also create an **XmlDocument** using an existing **NameTable** from another document.</span></span> <span data-ttu-id="364fb-106">Gdy **XmlDocuments** są tworzone za pomocą konstruktora, który przyjmuje **XmlNameTable** parametru dokument ma dostęp do nazwy węzła, obszary nazw i prefiksy już zapisana w  **XmlNameTable**.</span><span class="sxs-lookup"><span data-stu-id="364fb-106">When **XmlDocuments** are created with the constructor that takes an **XmlNameTable** parameter, the document has access to the node names, namespaces, and prefixes already stored in the **XmlNameTable**.</span></span> <span data-ttu-id="364fb-107">Niezależnie od tego, jak nazwa tabeli jest ładowany z nazwami po nazwy są przechowywane w tabeli nazw można porównywać szybko przy użyciu obiektu porównania zamiast porównania ciągu.</span><span class="sxs-lookup"><span data-stu-id="364fb-107">Regardless of how the name table is loaded with names, once the names are stored in the table, names can be compared quickly using object comparison instead of string comparison.</span></span> <span data-ttu-id="364fb-108">Ciągi można również dodać do tabeli nazwy przy użyciu <xref:System.Xml.NameTable.Add%2A>.</span><span class="sxs-lookup"><span data-stu-id="364fb-108">Strings can also be added to the name table using the <xref:System.Xml.NameTable.Add%2A>.</span></span> <span data-ttu-id="364fb-109">Poniższy przykładowy kod przedstawia tabeli nazw, tworzenia i ciąg **mójCiąg** dodawanych do tabeli.</span><span class="sxs-lookup"><span data-stu-id="364fb-109">The following code sample shows a name table being created and the string **MyString** being added to the table.</span></span> <span data-ttu-id="364fb-110">Po wykonaniu tej **XmlDocument** jest tworzony przy użyciu tej tabeli, a nazwy elementów i atrybutów w **Myfile.xml** są dodawane do istniejącej tabeli nazw.</span><span class="sxs-lookup"><span data-stu-id="364fb-110">After that, an **XmlDocument** is created using that table, and the element and attribute names in **Myfile.xml** are added to the existing name table.</span></span>  
  
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
  
 <span data-ttu-id="364fb-111">W poniższym przykładzie kodu pokazano tworzenie dokumentu, dwa nowe elementy dodawany do dokumentu, który dodaje je do tabeli nazwy dokumentu, a obiekt porównania nazw.</span><span class="sxs-lookup"><span data-stu-id="364fb-111">The following code example shows the creation of a document, two new elements being added to the document, which also adds them to the document name table, and the object comparison on the names.</span></span>  
  
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
  
 <span data-ttu-id="364fb-112">Powyższym scenariuszu tabeli nazwy przekazywane między dwa dokumenty jest typowe w przypadku, gdy ten sam typ dokumentu jest przetwarzana, takich jak dokumenty kolejności w witrynie handlu elektronicznego, które odpowiadają typ schematu XML definition language (XSD) schemat lub dokument są powtarzane definicji (DTD) i tej samej ciągów.</span><span class="sxs-lookup"><span data-stu-id="364fb-112">The above scenario of a name table passed between two documents is typical when the same type of document is being processed repeatedly, such as order documents at an ecommerce site, which conform to an XML Schema definition language (XSD) schema or document type definition (DTD) and the same strings are repeated.</span></span> <span data-ttu-id="364fb-113">Przy użyciu tej samej tabeli nazw zapewnia lepszą wydajność, zgodnie z takiej samej nazwie elementu występuje w wielu dokumentów.</span><span class="sxs-lookup"><span data-stu-id="364fb-113">Using the same name table gives a performance improvement, as the same element name occurs in multiple documents.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="364fb-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="364fb-114">See Also</span></span>  
 [<span data-ttu-id="364fb-115">Model DOM (XML Document Object Model)</span><span class="sxs-lookup"><span data-stu-id="364fb-115">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
