---
title: Programowanie funkcjonalne a Programowanie proceduralne (LINQ to XML)C#()
ms.date: 07/20/2015
ms.assetid: fc64e39c-a487-4882-9169-da4de97917d9
ms.openlocfilehash: e87114d2edcda4b2df14eb2d84f62ebe9638b5eb
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69594248"
---
# <a name="functional-vs-procedural-programming-linq-to-xml-c"></a><span data-ttu-id="f4080-102">Programowanie funkcjonalne a Programowanie proceduralne (LINQ to XML)C#()</span><span class="sxs-lookup"><span data-stu-id="f4080-102">Functional vs. Procedural Programming (LINQ to XML) (C#)</span></span>
<span data-ttu-id="f4080-103">Istnieją różne typy aplikacji XML:</span><span class="sxs-lookup"><span data-stu-id="f4080-103">There are various types of XML applications:</span></span>  
  
- <span data-ttu-id="f4080-104">Niektóre aplikacje pobierają źródłowe dokumenty XML i generują nowe dokumenty XML, które znajdują się w innym kształcie niż dokumenty źródłowe.</span><span class="sxs-lookup"><span data-stu-id="f4080-104">Some applications take source XML documents, and produce new XML documents that are in a different shape than the source documents.</span></span>  
  
- <span data-ttu-id="f4080-105">Niektóre aplikacje pobierają źródłowe dokumenty XML i generują dokumenty z wynikami całkowicie różnymi formularzami, takimi jak pliki tekstowe HTML lub CSV.</span><span class="sxs-lookup"><span data-stu-id="f4080-105">Some applications take source XML documents, and produce result documents in an entirely different form, such as HTML or CSV text files.</span></span>  
  
- <span data-ttu-id="f4080-106">Niektóre aplikacje pobierają źródłowe dokumenty XML i wstawiają rekordy do bazy danych.</span><span class="sxs-lookup"><span data-stu-id="f4080-106">Some applications take source XML documents, and insert records into a database.</span></span>  
  
- <span data-ttu-id="f4080-107">Niektóre aplikacje pobierają dane z innego źródła, takiego jak baza danych, i tworzy z niego dokumenty XML.</span><span class="sxs-lookup"><span data-stu-id="f4080-107">Some applications take data from another source, such as a database, and create XML documents from it.</span></span>  
  
 <span data-ttu-id="f4080-108">Nie są to wszystkie typy aplikacji XML, ale są to reprezentatywny zestaw typów funkcji, które programista XML musi zaimplementować.</span><span class="sxs-lookup"><span data-stu-id="f4080-108">These are not all of the types of XML applications, but these are a representative set of the types of functionality that an XML programmer has to implement.</span></span>  
  
 <span data-ttu-id="f4080-109">W przypadku wszystkich typów aplikacji istnieją dwie podejścia z kontrastem, które może podjąć Deweloper:</span><span class="sxs-lookup"><span data-stu-id="f4080-109">With all of these types of applications, there are two contrasting approaches that a developer can take:</span></span>  
  
- <span data-ttu-id="f4080-110">Funkcjonalne konstruowanie przy użyciu podejścia deklaratywnego.</span><span class="sxs-lookup"><span data-stu-id="f4080-110">Functional construction using a declarative approach.</span></span>  
  
- <span data-ttu-id="f4080-111">Modyfikowanie drzewa XML w pamięci przy użyciu kodu proceduralnego.</span><span class="sxs-lookup"><span data-stu-id="f4080-111">In-memory XML tree modification using procedural code.</span></span>  
  
 <span data-ttu-id="f4080-112">LINQ to XML obsługuje oba podejścia.</span><span class="sxs-lookup"><span data-stu-id="f4080-112">LINQ to XML supports both approaches.</span></span>  
  
 <span data-ttu-id="f4080-113">Korzystając z podejścia funkcjonalnego, należy napisać przekształcenia, które pobierają dokumenty źródłowe i generować zupełnie nowe dokumenty wynikowe z żądanym kształtem.</span><span class="sxs-lookup"><span data-stu-id="f4080-113">When using the functional approach, you write transformations that take the source documents and generate completely new result documents with the desired shape.</span></span>  
  
 <span data-ttu-id="f4080-114">Podczas modyfikowania drzewa XML w miejscu należy napisać kod, który przechodzi przez węzły w drzewie XML w pamięci, wstawiając, usuwając i modyfikując węzły, w razie potrzeby.</span><span class="sxs-lookup"><span data-stu-id="f4080-114">When modifying an XML tree in place, you write code that traverses and navigates through nodes in an in-memory XML tree, inserting, deleting, and modifying nodes as necessary.</span></span>  
  
 <span data-ttu-id="f4080-115">Możesz użyć LINQ to XML z dowolnego podejścia.</span><span class="sxs-lookup"><span data-stu-id="f4080-115">You can use LINQ to XML with either approach.</span></span> <span data-ttu-id="f4080-116">Używasz tych samych klas, a w niektórych przypadkach te same metody.</span><span class="sxs-lookup"><span data-stu-id="f4080-116">You use the same classes, and in some cases the same methods.</span></span> <span data-ttu-id="f4080-117">Jednak struktura i cele dwóch metod są bardzo różne.</span><span class="sxs-lookup"><span data-stu-id="f4080-117">However, the structure and goals of the two approaches are very different.</span></span> <span data-ttu-id="f4080-118">Na przykład w różnych sytuacjach jedno lub inne podejście często ma lepszą wydajność i będzie używać więcej lub mniej pamięci.</span><span class="sxs-lookup"><span data-stu-id="f4080-118">For example, in different situations, one or the other approach will often have better performance, and use more or less memory.</span></span> <span data-ttu-id="f4080-119">Ponadto jedno lub inne podejście będzie łatwiejsze do pisania i uzyskania bardziej możliwego do utrzymania kodu.</span><span class="sxs-lookup"><span data-stu-id="f4080-119">In addition, one or the other approach will be easier to write and yield more maintainable code.</span></span>  
  
 <span data-ttu-id="f4080-120">Aby wyświetlić dwa podejścia z kontrastem, zobacz [modyfikowanie drzewa XML w pamięci a Konstrukcja funkcjonalna (LINQ to XML)C#(](./in-memory-xml-tree-modification-vs-functional-construction-linq-to-xml.md)).</span><span class="sxs-lookup"><span data-stu-id="f4080-120">To see the two approaches contrasted, see [In-Memory XML Tree Modification vs. Functional Construction (LINQ to XML) (C#)](./in-memory-xml-tree-modification-vs-functional-construction-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="f4080-121">Aby zapoznać się z samouczkiem dotyczącym pisania przekształceń funkcjonalnych, zobacz [czyste działania transformacji XMLC#()](./introduction-to-pure-functional-transformations.md).</span><span class="sxs-lookup"><span data-stu-id="f4080-121">For a tutorial on writing functional transformations, see [Pure Functional Transformations of XML (C#)](./introduction-to-pure-functional-transformations.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f4080-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f4080-122">See also</span></span>

- [<span data-ttu-id="f4080-123">Omówienie programowania LINQ to XML (C#)</span><span class="sxs-lookup"><span data-stu-id="f4080-123">LINQ to XML Programming Overview (C#)</span></span>](./linq-to-xml-overview.md)
