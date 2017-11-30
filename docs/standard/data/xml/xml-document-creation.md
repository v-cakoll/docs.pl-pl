---
title: Tworzenie dokumentu XML
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 877e9c62-b082-4bfb-bc5b-f47297eb30ef
caps.latest.revision: "4"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 5a0806e34cfbf7c8e0b5ba995ca4876b8d10405e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="xml-document-creation"></a><span data-ttu-id="89880-102">Tworzenie dokumentu XML</span><span class="sxs-lookup"><span data-stu-id="89880-102">XML Document Creation</span></span>
<span data-ttu-id="89880-103">Istnieją dwa sposoby tworzenia dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="89880-103">There are two ways to create an XML document.</span></span> <span data-ttu-id="89880-104">Jednym ze sposobów jest utworzenie **XmlDocument** bez parametrów.</span><span class="sxs-lookup"><span data-stu-id="89880-104">One way is to create an **XmlDocument** with no parameters.</span></span> <span data-ttu-id="89880-105">Innym sposobem jest utworzenie **XmlDocument** i przekaż go XmlNameTable jako parametr.</span><span class="sxs-lookup"><span data-stu-id="89880-105">The other way is to create an **XmlDocument** and pass it an XmlNameTable as a parameter.</span></span> <span data-ttu-id="89880-106">Poniższy przykład pokazuje, jak utworzyć nowy, pusty **XmlDocument** przy użyciu bez parametrów.</span><span class="sxs-lookup"><span data-stu-id="89880-106">The following example shows how to create a new, empty **XmlDocument** using no parameters.</span></span>  
  
```vb  
Dim doc As New XmlDocument()  
```  
  
```csharp  
XmlDocument doc = new XmlDocument();  
```  
  
 <span data-ttu-id="89880-107">Po utworzeniu dokumentu, będzie można go załadować z danymi z ciągu, strumienia, adres URL, czytnika tekstu lub **XmlReader** pochodzi z klasy przy użyciu **załadować** — metoda.</span><span class="sxs-lookup"><span data-stu-id="89880-107">Once a document is created, you can load it with data from a string, stream, URL, text reader, or an **XmlReader** derived class using the **Load** method.</span></span> <span data-ttu-id="89880-108">Istnieje również innej metody load, **działanie metody LoadXML** metodę, która odczytuje z ciągu XML.</span><span class="sxs-lookup"><span data-stu-id="89880-108">There is also another load method, the **LoadXML** method, which reads XML from a string.</span></span> <span data-ttu-id="89880-109">Aby uzyskać więcej informacji na temat różnych **obciążenia** metod, zobacz [odczytywanie dokumentu XML do modelu DOM](../../../../docs/standard/data/xml/reading-an-xml-document-into-the-dom.md).</span><span class="sxs-lookup"><span data-stu-id="89880-109">For more information on the various **Load** methods, see [Reading an XML Document into the DOM](../../../../docs/standard/data/xml/reading-an-xml-document-into-the-dom.md).</span></span>  
  
 <span data-ttu-id="89880-110">Brak klasy o nazwie **XmlNameTable**.</span><span class="sxs-lookup"><span data-stu-id="89880-110">There is a class called the **XmlNameTable**.</span></span> <span data-ttu-id="89880-111">Ta klasa jest tabeli obiektów atomized ciągu.</span><span class="sxs-lookup"><span data-stu-id="89880-111">This class is a table of atomized string objects.</span></span> <span data-ttu-id="89880-112">Ta tabela zawiera skuteczne dla analizatora składni XML do użycia z tym samym obiektem ciąg wszystkie powtórzone elementu i nazwach atrybutów w dokumencie XML.</span><span class="sxs-lookup"><span data-stu-id="89880-112">This table provides an efficient means for the XML parser to use the same string object for all repeated element and attribute names in an XML document.</span></span> <span data-ttu-id="89880-113">**XmlNameTable** jest tworzony automatycznie podczas dokumentu jest tworzony, jak pokazano powyżej i został załadowany z nazwami atrybutów i elementów, podczas ładowania dokumentu.</span><span class="sxs-lookup"><span data-stu-id="89880-113">An **XmlNameTable** is automatically created when a document is created as shown above and is loaded with attribute and element names when the document is loaded.</span></span> <span data-ttu-id="89880-114">Jeśli masz już dokument z tabeli nazw i nazwy, które będą przydatne w innym dokumencie, można utworzyć nowego dokumentu przy użyciu **obciążenia** metody pobierającej **XmlNameTable** jako parametr.</span><span class="sxs-lookup"><span data-stu-id="89880-114">If you already have a document with a name table, and those names would be useful in another document, you can create a new document using the **Load** method that takes an **XmlNameTable** as a parameter.</span></span> <span data-ttu-id="89880-115">Po utworzeniu dokumentu przy użyciu tej metody wykorzystuje istniejące **XmlNameTable** ze wszystkimi atrybuty i elementy już załadowany do niego z innego dokumentu.</span><span class="sxs-lookup"><span data-stu-id="89880-115">When the document is created with this method, it uses the existing **XmlNameTable** with all the attributes and elements already loaded into it from the other document.</span></span> <span data-ttu-id="89880-116">Może służyć do porównywania wydajnie nazw elementów i atrybutów.</span><span class="sxs-lookup"><span data-stu-id="89880-116">It can be used for efficiently comparing element and attribute names.</span></span> <span data-ttu-id="89880-117">Aby uzyskać więcej informacji na temat **XmlNameTable**, zobacz [XmlNameTable przy użyciu porównania obiektu](../../../../docs/standard/data/xml/object-comparison-using-xmlnametable.md).</span><span class="sxs-lookup"><span data-stu-id="89880-117">For more information on the **XmlNameTable**, see [Object Comparison Using XmlNameTable](../../../../docs/standard/data/xml/object-comparison-using-xmlnametable.md).</span></span> <span data-ttu-id="89880-118">Aby informacje, zobacz <xref:System.Xml.XmlNameTable>.</span><span class="sxs-lookup"><span data-stu-id="89880-118">For reference, see <xref:System.Xml.XmlNameTable>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="89880-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="89880-119">See Also</span></span>  
 [<span data-ttu-id="89880-120">Modelu obiektu dokumentu XML modelu DOM)</span><span class="sxs-lookup"><span data-stu-id="89880-120">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
