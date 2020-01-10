---
title: Przetwarzanie danych XML przy użyciu modelu LINQ to XML
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 059d6b9d-63f7-4011-9ba8-8406f0bbae7d
ms.openlocfilehash: f45c5c9dccd2c1e8bdd67000a8b2f22425822ac9
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75710469"
---
# <a name="process-xml-data-using-linq-to-xml"></a><span data-ttu-id="b3712-102">Przetwarzanie danych XML przy użyciu modelu LINQ to XML</span><span class="sxs-lookup"><span data-stu-id="b3712-102">Process XML Data Using LINQ to XML</span></span>
<span data-ttu-id="b3712-103">LINQ to XML jest nowym modelem w .NET Framework w wersji 3,5 na potrzeby przetwarzania danych XML.</span><span class="sxs-lookup"><span data-stu-id="b3712-103">LINQ to XML is the new model in the .NET Framework version 3.5 for processing XML data.</span></span> <span data-ttu-id="b3712-104">LINQ to XML umożliwia deweloperom wykonywanie wszystkich oczekiwań z danymi XML: wykonywanie zapytań, modyfikowanie, tworzenie, zapisywanie i Serializowanie dokumentów XML.</span><span class="sxs-lookup"><span data-stu-id="b3712-104">LINQ to XML allows developers to do everything they would expect with XML data: querying, modifying, creating, saving, and serializing XML documents.</span></span> <span data-ttu-id="b3712-105">Rzeczywiste zalety mieszczą się w funkcji zapytania i tworzenia.</span><span class="sxs-lookup"><span data-stu-id="b3712-105">The real advantages lie in the query and creation capabilities.</span></span>  
  
 <span data-ttu-id="b3712-106">Zapytania w LINQ to XML są zwięzłe i wyraźne, przy użyciu składni bardziej podobnej do SQL niż XPath lub XQuery.</span><span class="sxs-lookup"><span data-stu-id="b3712-106">Queries in LINQ to XML are succinct and expressive, using syntax more similar to SQL than to XPath or XQuery.</span></span> <span data-ttu-id="b3712-107">Ponieważ wyniki zapytania mogą być zwracane jako kolekcje elementów lub atrybutów i mogą być używane jako parametry dla obiektów XElement, drzewa XML mogą być łatwo przekształcone z jednego kształtu na drugi.</span><span class="sxs-lookup"><span data-stu-id="b3712-107">Because query results can be returned as collections of elements or attributes and can be used as parameters for XElement objects, XML trees can be easily transformed from one shape to another.</span></span>  
  
 <span data-ttu-id="b3712-108">LINQ to XML korzysta z technologii LINQ (Language-Integrated Query) w .NET Framework wersji 3,5.</span><span class="sxs-lookup"><span data-stu-id="b3712-108">LINQ to XML leverages the language-integrated query (LINQ) technology in the .NET Framework version 3.5.</span></span> <span data-ttu-id="b3712-109">LINQ rozszerza składnię języka C# i Visual Basic, aby zapewnić zaawansowane możliwości zapytań, które można rozszerzyć do potencjalnie dowolnego magazynu danych.</span><span class="sxs-lookup"><span data-stu-id="b3712-109">LINQ extends the language syntax of C# and Visual Basic to provide powerful query capabilities that can be extended to potentially any data store.</span></span>  
  
 <span data-ttu-id="b3712-110">Aby zapoznać się ze szczegółami dotyczącymi użycia, zobacz [LINQ to XMLC#()](../../../csharp/programming-guide/concepts/linq/linq-to-xml-overview.md) i [LINQ to XML (Visual Basic)](../../../visual-basic/programming-guide/concepts/linq/linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="b3712-110">For a detailed discussion of its use, see [LINQ to XML (C#)](../../../csharp/programming-guide/concepts/linq/linq-to-xml-overview.md) and [LINQ to XML (Visual Basic)](../../../visual-basic/programming-guide/concepts/linq/linq-to-xml.md).</span></span> <span data-ttu-id="b3712-111">Aby zapoznać się z omówieniem programu LINQ Framework, zobacz [Language-Integrated Query (LINQ) C# —](../../../csharp/programming-guide/concepts/linq/index.md) lub [Language-Integrated Query (LINQ) — Visual Basic](../../../visual-basic/programming-guide/concepts/linq/index.md).</span><span class="sxs-lookup"><span data-stu-id="b3712-111">For an overview of the LINQ framework, see [Language-Integrated Query (LINQ) - C#](../../../csharp/programming-guide/concepts/linq/index.md) or [Language-Integrated Query (LINQ) - Visual Basic](../../../visual-basic/programming-guide/concepts/linq/index.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b3712-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b3712-112">See also</span></span>

- <xref:System.Xml.Linq>
- <xref:System.Linq>
- [<span data-ttu-id="b3712-113">LINQ to XML a DOM (C#)</span><span class="sxs-lookup"><span data-stu-id="b3712-113">LINQ to XML vs. DOM (C#)</span></span>](../../../csharp/programming-guide/concepts/linq/linq-to-xml-vs-dom.md)
- [<span data-ttu-id="b3712-114">LINQ to XML a DOM (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b3712-114">LINQ to XML vs. DOM (Visual Basic)</span></span>](../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-vs-dom.md)
- [<span data-ttu-id="b3712-115">LINQ to XML a inne technologie XML (C#)</span><span class="sxs-lookup"><span data-stu-id="b3712-115">LINQ to XML vs. Other XML Technologies (C#)</span></span>](../../../csharp/programming-guide/concepts/linq/linq-to-xml-vs-other-xml-technologies.md)
- [<span data-ttu-id="b3712-116">LINQ to XML a inne technologie XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b3712-116">LINQ to XML vs. Other XML Technologies (Visual Basic)</span></span>](../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-vs-other-xml-technologies.md)
