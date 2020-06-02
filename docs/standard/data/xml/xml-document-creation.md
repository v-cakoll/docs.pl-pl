---
title: Tworzenie dokumentu XML
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 877e9c62-b082-4bfb-bc5b-f47297eb30ef
ms.openlocfilehash: 577d353a30c986d198140b4596ae1a7e199ddd6e
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84291984"
---
# <a name="xml-document-creation"></a><span data-ttu-id="12f1d-102">Tworzenie dokumentu XML</span><span class="sxs-lookup"><span data-stu-id="12f1d-102">XML Document Creation</span></span>
<span data-ttu-id="12f1d-103">Istnieją dwa sposoby tworzenia dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="12f1d-103">There are two ways to create an XML document.</span></span> <span data-ttu-id="12f1d-104">Jednym ze sposobów jest utworzenie **dokumentu XmlDocument** bez parametrów.</span><span class="sxs-lookup"><span data-stu-id="12f1d-104">One way is to create an **XmlDocument** with no parameters.</span></span> <span data-ttu-id="12f1d-105">Innym sposobem jest utworzenie **dokumentu XmlDocument** i przekazanie go do XmlNameTable jako parametru.</span><span class="sxs-lookup"><span data-stu-id="12f1d-105">The other way is to create an **XmlDocument** and pass it an XmlNameTable as a parameter.</span></span> <span data-ttu-id="12f1d-106">Poniższy przykład pokazuje, jak utworzyć nowy pusty **dokument XmlDocument** bez parametrów.</span><span class="sxs-lookup"><span data-stu-id="12f1d-106">The following example shows how to create a new, empty **XmlDocument** using no parameters.</span></span>  
  
```vb  
Dim doc As New XmlDocument()  
```  
  
```csharp  
XmlDocument doc = new XmlDocument();  
```  
  
 <span data-ttu-id="12f1d-107">Po utworzeniu dokumentu można załadować go przy użyciu danych z ciągu, strumienia, adresu URL, czytnika tekstu lub klasy pochodnej **XmlReader** przy użyciu metody **Load** .</span><span class="sxs-lookup"><span data-stu-id="12f1d-107">Once a document is created, you can load it with data from a string, stream, URL, text reader, or an **XmlReader** derived class using the **Load** method.</span></span> <span data-ttu-id="12f1d-108">Istnieje również inna metoda ładowania, Metoda **LoadXml** , która odczytuje dane XML z ciągu.</span><span class="sxs-lookup"><span data-stu-id="12f1d-108">There is also another load method, the **LoadXML** method, which reads XML from a string.</span></span> <span data-ttu-id="12f1d-109">Aby uzyskać więcej informacji na temat różnych metod **ładowania** , zobacz [odczytywanie dokumentu XML w modelu dom](reading-an-xml-document-into-the-dom.md).</span><span class="sxs-lookup"><span data-stu-id="12f1d-109">For more information on the various **Load** methods, see [Reading an XML Document into the DOM](reading-an-xml-document-into-the-dom.md).</span></span>  
  
 <span data-ttu-id="12f1d-110">Istnieje Klasa o nazwie **XmlNameTable**.</span><span class="sxs-lookup"><span data-stu-id="12f1d-110">There is a class called the **XmlNameTable**.</span></span> <span data-ttu-id="12f1d-111">Ta klasa jest tabelą obiektów ciągów atomowych.</span><span class="sxs-lookup"><span data-stu-id="12f1d-111">This class is a table of atomized string objects.</span></span> <span data-ttu-id="12f1d-112">Ta tabela zawiera wydajny środek dla analizatora XML, aby używać tego samego obiektu ciągu dla wszystkich powtórzonych nazw elementów i atrybutów w dokumencie XML.</span><span class="sxs-lookup"><span data-stu-id="12f1d-112">This table provides an efficient means for the XML parser to use the same string object for all repeated element and attribute names in an XML document.</span></span> <span data-ttu-id="12f1d-113">**XmlNameTable** jest tworzony automatycznie podczas tworzenia dokumentu, jak pokazano powyżej, i jest ładowany z atrybutami i nazwami elementów podczas ładowania dokumentu.</span><span class="sxs-lookup"><span data-stu-id="12f1d-113">An **XmlNameTable** is automatically created when a document is created as shown above and is loaded with attribute and element names when the document is loaded.</span></span> <span data-ttu-id="12f1d-114">Jeśli masz już dokument z tabelą nazw, a te nazwy byłyby przydatne w innym dokumencie, możesz utworzyć nowy dokument przy użyciu metody **Load** , która przyjmuje **XmlNameTable** jako parametr.</span><span class="sxs-lookup"><span data-stu-id="12f1d-114">If you already have a document with a name table, and those names would be useful in another document, you can create a new document using the **Load** method that takes an **XmlNameTable** as a parameter.</span></span> <span data-ttu-id="12f1d-115">Gdy dokument zostanie utworzony przy użyciu tej metody, używa istniejącej **XmlNameTable** ze wszystkimi atrybutami i elementami już załadowanymi do niego z innego dokumentu.</span><span class="sxs-lookup"><span data-stu-id="12f1d-115">When the document is created with this method, it uses the existing **XmlNameTable** with all the attributes and elements already loaded into it from the other document.</span></span> <span data-ttu-id="12f1d-116">Może służyć do wydajnego porównywania nazw elementów i atrybutów.</span><span class="sxs-lookup"><span data-stu-id="12f1d-116">It can be used for efficiently comparing element and attribute names.</span></span> <span data-ttu-id="12f1d-117">Aby uzyskać więcej informacji na temat **XmlNameTable**, zobacz [porównanie obiektów przy użyciu XmlNameTable](object-comparison-using-xmlnametable.md).</span><span class="sxs-lookup"><span data-stu-id="12f1d-117">For more information on the **XmlNameTable**, see [Object Comparison Using XmlNameTable](object-comparison-using-xmlnametable.md).</span></span> <span data-ttu-id="12f1d-118">Aby uzyskać informacje, zobacz <xref:System.Xml.XmlNameTable> .</span><span class="sxs-lookup"><span data-stu-id="12f1d-118">For reference, see <xref:System.Xml.XmlNameTable>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="12f1d-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="12f1d-119">See also</span></span>

- [<span data-ttu-id="12f1d-120">XML Document Object Model (DOM)</span><span class="sxs-lookup"><span data-stu-id="12f1d-120">XML Document Object Model (DOM)</span></span>](xml-document-object-model-dom.md)
