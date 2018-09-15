---
title: Tworzenie dokumentu XML
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 877e9c62-b082-4bfb-bc5b-f47297eb30ef
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b76140fb7d79b1e191c0451cd7556963130d224a
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/15/2018
ms.locfileid: "45646184"
---
# <a name="xml-document-creation"></a><span data-ttu-id="b832e-102">Tworzenie dokumentu XML</span><span class="sxs-lookup"><span data-stu-id="b832e-102">XML Document Creation</span></span>
<span data-ttu-id="b832e-103">Istnieją dwa sposoby tworzenia dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="b832e-103">There are two ways to create an XML document.</span></span> <span data-ttu-id="b832e-104">Jednym ze sposobów jest utworzenie **XmlDocument** bez parametrów.</span><span class="sxs-lookup"><span data-stu-id="b832e-104">One way is to create an **XmlDocument** with no parameters.</span></span> <span data-ttu-id="b832e-105">Innym sposobem jest utworzenie **XmlDocument** i przekazać go tabeli XmlNameTable jako parametr.</span><span class="sxs-lookup"><span data-stu-id="b832e-105">The other way is to create an **XmlDocument** and pass it an XmlNameTable as a parameter.</span></span> <span data-ttu-id="b832e-106">Poniższy przykład pokazuje, jak utworzyć nowy, pusty **XmlDocument** przy użyciu bez parametrów.</span><span class="sxs-lookup"><span data-stu-id="b832e-106">The following example shows how to create a new, empty **XmlDocument** using no parameters.</span></span>  
  
```vb  
Dim doc As New XmlDocument()  
```  
  
```csharp  
XmlDocument doc = new XmlDocument();  
```  
  
 <span data-ttu-id="b832e-107">Po utworzeniu dokumentu, będzie można go załadować z danymi z ciągu, przesyłać strumieniowo, adres URL, czytnika tekstu lub **XmlReader** pochodne klasy przy użyciu **obciążenia** metody.</span><span class="sxs-lookup"><span data-stu-id="b832e-107">Once a document is created, you can load it with data from a string, stream, URL, text reader, or an **XmlReader** derived class using the **Load** method.</span></span> <span data-ttu-id="b832e-108">Istnieje również innej metody load, **działanie metody LoadXML** metody, która odczytuje XML z ciągu.</span><span class="sxs-lookup"><span data-stu-id="b832e-108">There is also another load method, the **LoadXML** method, which reads XML from a string.</span></span> <span data-ttu-id="b832e-109">Aby uzyskać więcej informacji na temat różnych **obciążenia** metod, zobacz [wczytywanie dokumentu XML do modelu DOM](../../../../docs/standard/data/xml/reading-an-xml-document-into-the-dom.md).</span><span class="sxs-lookup"><span data-stu-id="b832e-109">For more information on the various **Load** methods, see [Reading an XML Document into the DOM](../../../../docs/standard/data/xml/reading-an-xml-document-into-the-dom.md).</span></span>  
  
 <span data-ttu-id="b832e-110">Brak klasy o nazwie **tabeli XmlNameTable**.</span><span class="sxs-lookup"><span data-stu-id="b832e-110">There is a class called the **XmlNameTable**.</span></span> <span data-ttu-id="b832e-111">Ta klasa znajduje się tabela obiektów string rozproszone obiekty.</span><span class="sxs-lookup"><span data-stu-id="b832e-111">This class is a table of atomized string objects.</span></span> <span data-ttu-id="b832e-112">Ta tabela zawiera skuteczne dla analizatora XML do użycia tego samego obiektu ciągu dla elementu wszystkie powtórzone i nazw atrybutów w dokumencie XML.</span><span class="sxs-lookup"><span data-stu-id="b832e-112">This table provides an efficient means for the XML parser to use the same string object for all repeated element and attribute names in an XML document.</span></span> <span data-ttu-id="b832e-113">**Tabeli XmlNameTable** zostało automatycznie utworzone po dokumentu jest tworzony, jak pokazano powyżej i jest ładowany z nazwy atrybutu i elementu podczas ładowania dokumentu.</span><span class="sxs-lookup"><span data-stu-id="b832e-113">An **XmlNameTable** is automatically created when a document is created as shown above and is loaded with attribute and element names when the document is loaded.</span></span> <span data-ttu-id="b832e-114">Jeśli masz już dokumentu za pomocą nazwy tabeli, a te nazwy może przydać się w innym dokumencie, można utworzyć nowego dokumentu przy użyciu **obciążenia** metody, która przyjmuje **tabeli XmlNameTable** jako parametr.</span><span class="sxs-lookup"><span data-stu-id="b832e-114">If you already have a document with a name table, and those names would be useful in another document, you can create a new document using the **Load** method that takes an **XmlNameTable** as a parameter.</span></span> <span data-ttu-id="b832e-115">Gdy dokument zostanie utworzony przy użyciu tej metody, wykorzystuje istniejące **tabeli XmlNameTable** ze wszystkimi atrybuty i elementy już załadowane do niego z innych dokumentów.</span><span class="sxs-lookup"><span data-stu-id="b832e-115">When the document is created with this method, it uses the existing **XmlNameTable** with all the attributes and elements already loaded into it from the other document.</span></span> <span data-ttu-id="b832e-116">Umożliwia ono wydajnie porównywania nazw elementów i atrybutów.</span><span class="sxs-lookup"><span data-stu-id="b832e-116">It can be used for efficiently comparing element and attribute names.</span></span> <span data-ttu-id="b832e-117">Aby uzyskać więcej informacji na temat **tabeli XmlNameTable**, zobacz [obiektu porównanie przy użyciu tabeli XmlNameTable](../../../../docs/standard/data/xml/object-comparison-using-xmlnametable.md).</span><span class="sxs-lookup"><span data-stu-id="b832e-117">For more information on the **XmlNameTable**, see [Object Comparison Using XmlNameTable](../../../../docs/standard/data/xml/object-comparison-using-xmlnametable.md).</span></span> <span data-ttu-id="b832e-118">Aby informacje, zobacz <xref:System.Xml.XmlNameTable>.</span><span class="sxs-lookup"><span data-stu-id="b832e-118">For reference, see <xref:System.Xml.XmlNameTable>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b832e-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b832e-119">See also</span></span>

- [<span data-ttu-id="b832e-120">Model DOM (XML Document Object Model)</span><span class="sxs-lookup"><span data-stu-id="b832e-120">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
