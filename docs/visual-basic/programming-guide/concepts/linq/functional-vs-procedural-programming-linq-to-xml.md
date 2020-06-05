---
title: Programowanie funkcjonalne a proceduralne (LINQ to XML)
ms.date: 07/20/2015
ms.assetid: ea1015a5-d4c8-4d79-8e1e-ba17a40a4f39
ms.openlocfilehash: 0b525f13298e7402369b890516434cec47e01542
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84398438"
---
# <a name="functional-vs-procedural-programming-linq-to-xml-visual-basic"></a><span data-ttu-id="680e4-102">Programowanie funkcjonalne a proceduralne (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="680e4-102">Functional vs. Procedural Programming (LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="680e4-103">Istnieją różne typy aplikacji XML:</span><span class="sxs-lookup"><span data-stu-id="680e4-103">There are various types of XML applications:</span></span>  
  
- <span data-ttu-id="680e4-104">Niektóre aplikacje pobierają źródłowe dokumenty XML i generują nowe dokumenty XML, które znajdują się w innym kształcie niż dokumenty źródłowe.</span><span class="sxs-lookup"><span data-stu-id="680e4-104">Some applications take source XML documents, and produce new XML documents that are in a different shape than the source documents.</span></span>  
  
- <span data-ttu-id="680e4-105">Niektóre aplikacje pobierają źródłowe dokumenty XML i generują dokumenty z wynikami całkowicie różnymi formularzami, takimi jak pliki tekstowe HTML lub CSV.</span><span class="sxs-lookup"><span data-stu-id="680e4-105">Some applications take source XML documents, and produce result documents in an entirely different form, such as HTML or CSV text files.</span></span>  
  
- <span data-ttu-id="680e4-106">Niektóre aplikacje pobierają źródłowe dokumenty XML i wstawiają rekordy do bazy danych.</span><span class="sxs-lookup"><span data-stu-id="680e4-106">Some applications take source XML documents, and insert records into a database.</span></span>  
  
- <span data-ttu-id="680e4-107">Niektóre aplikacje pobierają dane z innego źródła, takiego jak baza danych, i tworzy z niego dokumenty XML.</span><span class="sxs-lookup"><span data-stu-id="680e4-107">Some applications take data from another source, such as a database, and create XML documents from it.</span></span>  
  
 <span data-ttu-id="680e4-108">Nie są to wszystkie typy aplikacji XML, ale są to reprezentatywny zestaw typów funkcji, które programista XML musi zaimplementować.</span><span class="sxs-lookup"><span data-stu-id="680e4-108">These are not all of the types of XML applications, but these are a representative set of the types of functionality that an XML programmer has to implement.</span></span>  
  
 <span data-ttu-id="680e4-109">W przypadku wszystkich typów aplikacji istnieją dwie podejścia z kontrastem, które może podjąć Deweloper:</span><span class="sxs-lookup"><span data-stu-id="680e4-109">With all of these types of applications, there are two contrasting approaches that a developer can take:</span></span>  
  
- <span data-ttu-id="680e4-110">Funkcjonalne konstruowanie przy użyciu podejścia deklaratywnego.</span><span class="sxs-lookup"><span data-stu-id="680e4-110">Functional construction using a declarative approach.</span></span>  
  
- <span data-ttu-id="680e4-111">Modyfikowanie drzewa XML w pamięci przy użyciu kodu proceduralnego.</span><span class="sxs-lookup"><span data-stu-id="680e4-111">In-memory XML tree modification using procedural code.</span></span>  
  
 <span data-ttu-id="680e4-112">LINQ to XML obsługuje oba podejścia.</span><span class="sxs-lookup"><span data-stu-id="680e4-112">LINQ to XML supports both approaches.</span></span>  
  
 <span data-ttu-id="680e4-113">Korzystając z podejścia funkcjonalnego, należy napisać przekształcenia, które pobierają dokumenty źródłowe i generować zupełnie nowe dokumenty wynikowe z żądanym kształtem.</span><span class="sxs-lookup"><span data-stu-id="680e4-113">When using the functional approach, you write transformations that take the source documents and generate completely new result documents with the desired shape.</span></span>  
  
 <span data-ttu-id="680e4-114">Podczas modyfikowania drzewa XML w miejscu należy napisać kod, który przechodzi przez węzły w drzewie XML w pamięci, wstawiając, usuwając i modyfikując węzły, w razie potrzeby.</span><span class="sxs-lookup"><span data-stu-id="680e4-114">When modifying an XML tree in place, you write code that traverses and navigates through nodes in an in-memory XML tree, inserting, deleting, and modifying nodes as necessary.</span></span>  
  
 <span data-ttu-id="680e4-115">Możesz użyć LINQ to XML z dowolnego podejścia.</span><span class="sxs-lookup"><span data-stu-id="680e4-115">You can use LINQ to XML with either approach.</span></span> <span data-ttu-id="680e4-116">Używasz tych samych klas, a w niektórych przypadkach te same metody.</span><span class="sxs-lookup"><span data-stu-id="680e4-116">You use the same classes, and in some cases the same methods.</span></span> <span data-ttu-id="680e4-117">Jednak struktura i cele dwóch metod są bardzo różne.</span><span class="sxs-lookup"><span data-stu-id="680e4-117">However, the structure and goals of the two approaches are very different.</span></span> <span data-ttu-id="680e4-118">Na przykład w różnych sytuacjach jedno lub inne podejście często ma lepszą wydajność i będzie używać więcej lub mniej pamięci.</span><span class="sxs-lookup"><span data-stu-id="680e4-118">For example, in different situations, one or the other approach will often have better performance, and use more or less memory.</span></span> <span data-ttu-id="680e4-119">Ponadto jedno lub inne podejście będzie łatwiejsze do pisania i uzyskania bardziej możliwego do utrzymania kodu.</span><span class="sxs-lookup"><span data-stu-id="680e4-119">In addition, one or the other approach will be easier to write and yield more maintainable code.</span></span>  
  
 <span data-ttu-id="680e4-120">Aby wyświetlić dwa podejścia z kontrastem, zobacz [Modyfikowanie drzewa XML w pamięci a konstrukcja funkcjonalna (LINQ to XML) (Visual Basic)](in-memory-xml-tree-modification-vs-functional-construction.md).</span><span class="sxs-lookup"><span data-stu-id="680e4-120">To see the two approaches contrasted, see [In-Memory XML Tree Modification vs. Functional Construction (LINQ to XML) (Visual Basic)](in-memory-xml-tree-modification-vs-functional-construction.md).</span></span>  
  
 <span data-ttu-id="680e4-121">Aby zapoznać się z samouczkiem dotyczącym pisania przekształceń funkcjonalnych, zobacz [czyste działania transformacji XML (Visual Basic)](pure-functional-transformations-of-xml.md).</span><span class="sxs-lookup"><span data-stu-id="680e4-121">For a tutorial on writing functional transformations, see [Pure Functional Transformations of XML (Visual Basic)](pure-functional-transformations-of-xml.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="680e4-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="680e4-122">See also</span></span>

- [<span data-ttu-id="680e4-123">Omówienie programowania LINQ to XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="680e4-123">LINQ to XML Programming Overview (Visual Basic)</span></span>](linq-to-xml-programming-overview.md)
