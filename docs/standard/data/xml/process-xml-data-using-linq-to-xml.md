---
title: Przetwarzanie danych XML przy użyciu modelu LINQ to XML
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 059d6b9d-63f7-4011-9ba8-8406f0bbae7d
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1554c3e2b13dd0ea0d64ccd7e7caee0a1e0dd3f9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61949685"
---
# <a name="process-xml-data-using-linq-to-xml"></a><span data-ttu-id="158ab-102">Przetwarzanie danych XML przy użyciu modelu LINQ to XML</span><span class="sxs-lookup"><span data-stu-id="158ab-102">Process XML Data Using LINQ to XML</span></span>
<span data-ttu-id="158ab-103">LINQ to XML jest nowy model w .NET Framework w wersji 3.5 do przetwarzania danych XML.</span><span class="sxs-lookup"><span data-stu-id="158ab-103">LINQ to XML is the new model in the .NET Framework version 3.5 for processing XML data.</span></span> <span data-ttu-id="158ab-104">LINQ to XML umożliwia deweloperom robić wszystko, czego mogą oczekiwać z danymi XML: wykonywanie zapytań, modyfikowanie, tworzenia, zapisywania i serializacja dokumentów XML.</span><span class="sxs-lookup"><span data-stu-id="158ab-104">LINQ to XML allows developers to do everything they would expect with XML data: querying, modifying, creating, saving, and serializing XML documents.</span></span> <span data-ttu-id="158ab-105">Istotne zalety znajdują się w funkcje zapytań i tworzenia.</span><span class="sxs-lookup"><span data-stu-id="158ab-105">The real advantages lie in the query and creation capabilities.</span></span>  
  
 <span data-ttu-id="158ab-106">Zapytania w LINQ to XML są zwięzły i obszerne strategie, przy użyciu składni więcej podobnej do bazy danych SQL niż XPath lub wyrażenie XQuery.</span><span class="sxs-lookup"><span data-stu-id="158ab-106">Queries in LINQ to XML are succinct and expressive, using syntax more similar to SQL than to XPath or XQuery.</span></span> <span data-ttu-id="158ab-107">Ponieważ wyniki zapytania mogą być zwracane jako kolekcje elementów lub atrybutów i mogą być używane jako parametry dla obiektów klasy XElement, drzew XML można je łatwo przekształcać z jednego kształtu do innego.</span><span class="sxs-lookup"><span data-stu-id="158ab-107">Because query results can be returned as collections of elements or attributes and can be used as parameters for XElement objects, XML trees can be easily transformed from one shape to another.</span></span>  
  
 <span data-ttu-id="158ab-108">LINQ to XML korzysta z technologii zapytanie o języku zintegrowanym (LINQ) w programie .NET Framework w wersji 3.5.</span><span class="sxs-lookup"><span data-stu-id="158ab-108">LINQ to XML leverages the language-integrated query (LINQ) technology in the .NET Framework version 3.5.</span></span> <span data-ttu-id="158ab-109">LINQ rozszerza składni języka C# i Visual Basic oraz możliwości kwerend, które można rozszerzyć na potencjalnie dowolnego magazynu danych.</span><span class="sxs-lookup"><span data-stu-id="158ab-109">LINQ extends the language syntax of C# and Visual Basic to provide powerful query capabilities that can be extended to potentially any data store.</span></span>  
  
 <span data-ttu-id="158ab-110">Aby uzyskać szczegółowe omówienie jego użycia, zobacz [LINQ to XML (C#)](../../../csharp/programming-guide/concepts/linq/linq-to-xml.md) i [LINQ to XML (Visual Basic)](../../../visual-basic/programming-guide/concepts/linq/linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="158ab-110">For a detailed discussion of its use, see [LINQ to XML (C#)](../../../csharp/programming-guide/concepts/linq/linq-to-xml.md) and [LINQ to XML (Visual Basic)](../../../visual-basic/programming-guide/concepts/linq/linq-to-xml.md).</span></span> <span data-ttu-id="158ab-111">Aby uzyskać omówienie LINQ framework, zobacz [Language-Integrated Query (LINQ) - C# ](../../../csharp/programming-guide/concepts/linq/index.md) lub [Language-Integrated Query (LINQ) - Visual Basic](../../../visual-basic/programming-guide/concepts/linq/index.md).</span><span class="sxs-lookup"><span data-stu-id="158ab-111">For an overview of the LINQ framework, see [Language-Integrated Query (LINQ) - C#](../../../csharp/programming-guide/concepts/linq/index.md) or [Language-Integrated Query (LINQ) - Visual Basic](../../../visual-basic/programming-guide/concepts/linq/index.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="158ab-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="158ab-112">See also</span></span>

- <xref:System.Xml.Linq>
- <xref:System.Linq>
- [<span data-ttu-id="158ab-113">LINQ to XML a MODELU DOM (C#)</span><span class="sxs-lookup"><span data-stu-id="158ab-113">LINQ to XML vs. DOM (C#)</span></span>](../../../csharp/programming-guide/concepts/linq/linq-to-xml-vs-dom.md)
- [<span data-ttu-id="158ab-114">LINQ to XML a Modelu DOM (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="158ab-114">LINQ to XML vs. DOM (Visual Basic)</span></span>](../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-vs-dom.md)
- [<span data-ttu-id="158ab-115">LINQ to XML a Inne technologie XML (C#)</span><span class="sxs-lookup"><span data-stu-id="158ab-115">LINQ to XML vs. Other XML Technologies (C#)</span></span>](../../../csharp/programming-guide/concepts/linq/linq-to-xml-vs-other-xml-technologies.md)
- [<span data-ttu-id="158ab-116">LINQ to XML a Inne technologie XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="158ab-116">LINQ to XML vs. Other XML Technologies (Visual Basic)</span></span>](../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-vs-other-xml-technologies.md)
