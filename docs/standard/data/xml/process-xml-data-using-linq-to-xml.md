---
title: Przetwarzanie danych XML przy użyciu LINQ to XML
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 059d6b9d-63f7-4011-9ba8-8406f0bbae7d
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 8d24f379bcfdb494369b84173cad4daa800fb7a9
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2018
ms.locfileid: "43862679"
---
# <a name="process-xml-data-using-linq-to-xml"></a><span data-ttu-id="484a0-102">Przetwarzanie danych XML przy użyciu LINQ to XML</span><span class="sxs-lookup"><span data-stu-id="484a0-102">Process XML Data Using LINQ to XML</span></span>
<span data-ttu-id="484a0-103">LINQ to XML jest nowy model w .NET Framework w wersji 3.5 do przetwarzania danych XML.</span><span class="sxs-lookup"><span data-stu-id="484a0-103">LINQ to XML is the new model in the .NET Framework version 3.5 for processing XML data.</span></span> <span data-ttu-id="484a0-104">LINQ to XML umożliwia deweloperom robić wszystko, czego mogą oczekiwać z danymi XML: wykonywanie zapytań, modyfikowanie, tworzenia, zapisywania i serializacja dokumentów XML.</span><span class="sxs-lookup"><span data-stu-id="484a0-104">LINQ to XML allows developers to do everything they would expect with XML data: querying, modifying, creating, saving, and serializing XML documents.</span></span> <span data-ttu-id="484a0-105">Istotne zalety znajdują się w funkcje zapytań i tworzenia.</span><span class="sxs-lookup"><span data-stu-id="484a0-105">The real advantages lie in the query and creation capabilities.</span></span>  
  
 <span data-ttu-id="484a0-106">Zapytania w LINQ to XML są zwięzły i obszerne strategie, przy użyciu składni więcej podobnej do bazy danych SQL niż XPath lub wyrażenie XQuery.</span><span class="sxs-lookup"><span data-stu-id="484a0-106">Queries in LINQ to XML are succinct and expressive, using syntax more similar to SQL than to XPath or XQuery.</span></span> <span data-ttu-id="484a0-107">Ponieważ wyniki zapytania mogą być zwracane jako kolekcje elementów lub atrybutów i mogą być używane jako parametry dla obiektów klasy XElement, drzew XML można je łatwo przekształcać z jednego kształtu do innego.</span><span class="sxs-lookup"><span data-stu-id="484a0-107">Because query results can be returned as collections of elements or attributes and can be used as parameters for XElement objects, XML trees can be easily transformed from one shape to another.</span></span>  
  
 <span data-ttu-id="484a0-108">LINQ to XML korzysta z technologii zapytanie o języku zintegrowanym (LINQ) w programie .NET Framework w wersji 3.5.</span><span class="sxs-lookup"><span data-stu-id="484a0-108">LINQ to XML leverages the language-integrated query (LINQ) technology in the .NET Framework version 3.5.</span></span> <span data-ttu-id="484a0-109">LINQ rozszerza składni języka C# i Visual Basic oraz możliwości kwerend, które można rozszerzyć na potencjalnie dowolnego magazynu danych.</span><span class="sxs-lookup"><span data-stu-id="484a0-109">LINQ extends the language syntax of C# and Visual Basic to provide powerful query capabilities that can be extended to potentially any data store.</span></span>  
  
 <span data-ttu-id="484a0-110">Zobacz [LINQ to XML](https://msdn.microsoft.com/library/f0fe21e9-ee43-4a55-b91a-0800e5782c13) szczegółowe omówienie użytkowania i zobacz [LINQ (Language-Integrated Query)](https://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d) omówienie LINQ framework.</span><span class="sxs-lookup"><span data-stu-id="484a0-110">See [LINQ to XML](https://msdn.microsoft.com/library/f0fe21e9-ee43-4a55-b91a-0800e5782c13) for a detailed discussion of its use, and see [LINQ (Language-Integrated Query)](https://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d) for an overview of the LINQ framework.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="484a0-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="484a0-111">See also</span></span>

- <xref:System.Xml.Linq>  
- <xref:System.Linq>  
- [<span data-ttu-id="484a0-112">LINQ to XML a DOM</span><span class="sxs-lookup"><span data-stu-id="484a0-112">LINQ to XML vs. DOM</span></span>](https://msdn.microsoft.com/library/19b5ed02-feb2-455a-8897-f7f0fd76aca3)  
- [<span data-ttu-id="484a0-113">LINQ to XML a inne technologie XML</span><span class="sxs-lookup"><span data-stu-id="484a0-113">LINQ to XML vs. Other XML Technologies</span></span>](https://msdn.microsoft.com/library/7ba1eecf-f09a-42de-bc80-22ca5b2e42d3)
