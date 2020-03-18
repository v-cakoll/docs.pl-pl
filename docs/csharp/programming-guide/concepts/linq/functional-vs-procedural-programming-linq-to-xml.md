---
title: Programowanie funkcjonalne a programowanie proceduralne (LINQ do XML) (C#)
ms.date: 07/20/2015
ms.assetid: fc64e39c-a487-4882-9169-da4de97917d9
ms.openlocfilehash: e87114d2edcda4b2df14eb2d84f62ebe9638b5eb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "69594248"
---
# <a name="functional-vs-procedural-programming-linq-to-xml-c"></a><span data-ttu-id="2f916-102">Programowanie funkcjonalne a programowanie proceduralne (LINQ do XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="2f916-102">Functional vs. Procedural Programming (LINQ to XML) (C#)</span></span>
<span data-ttu-id="2f916-103">Istnieją różne rodzaje aplikacji XML:</span><span class="sxs-lookup"><span data-stu-id="2f916-103">There are various types of XML applications:</span></span>  
  
- <span data-ttu-id="2f916-104">Niektóre aplikacje przyjmują źródłowe dokumenty XML i tworzą nowe dokumenty XML, które mają inny kształt niż dokumenty źródłowe.</span><span class="sxs-lookup"><span data-stu-id="2f916-104">Some applications take source XML documents, and produce new XML documents that are in a different shape than the source documents.</span></span>  
  
- <span data-ttu-id="2f916-105">Niektóre aplikacje przyjmują źródłowe dokumenty XML i tworzą dokumenty wyników w zupełnie innej formie, takiej jak pliki tekstowe HTML lub CSV.</span><span class="sxs-lookup"><span data-stu-id="2f916-105">Some applications take source XML documents, and produce result documents in an entirely different form, such as HTML or CSV text files.</span></span>  
  
- <span data-ttu-id="2f916-106">Niektóre aplikacje przyjmują źródłowe dokumenty XML i wstawiają rekordy do bazy danych.</span><span class="sxs-lookup"><span data-stu-id="2f916-106">Some applications take source XML documents, and insert records into a database.</span></span>  
  
- <span data-ttu-id="2f916-107">Niektóre aplikacje przyjmują dane z innego źródła, takiego jak baza danych, i tworzą z niej dokumenty XML.</span><span class="sxs-lookup"><span data-stu-id="2f916-107">Some applications take data from another source, such as a database, and create XML documents from it.</span></span>  
  
 <span data-ttu-id="2f916-108">Nie są to wszystkie typy aplikacji XML, ale są to reprezentatywny zestaw typów funkcji, które programista XML musi zaimplementować.</span><span class="sxs-lookup"><span data-stu-id="2f916-108">These are not all of the types of XML applications, but these are a representative set of the types of functionality that an XML programmer has to implement.</span></span>  
  
 <span data-ttu-id="2f916-109">W przypadku wszystkich tych typów aplikacji istnieją dwa kontrastujące podejścia, które deweloper może podjąć:</span><span class="sxs-lookup"><span data-stu-id="2f916-109">With all of these types of applications, there are two contrasting approaches that a developer can take:</span></span>  
  
- <span data-ttu-id="2f916-110">Funkcjonalna konstrukcja przy użyciu podejścia deklaratywnego.</span><span class="sxs-lookup"><span data-stu-id="2f916-110">Functional construction using a declarative approach.</span></span>  
  
- <span data-ttu-id="2f916-111">Modyfikacja drzewa XML w pamięci przy użyciu kodu proceduralnego.</span><span class="sxs-lookup"><span data-stu-id="2f916-111">In-memory XML tree modification using procedural code.</span></span>  
  
 <span data-ttu-id="2f916-112">LINQ do XML obsługuje oba podejścia.</span><span class="sxs-lookup"><span data-stu-id="2f916-112">LINQ to XML supports both approaches.</span></span>  
  
 <span data-ttu-id="2f916-113">Korzystając z podejścia funkcjonalnego, piszesz przekształcenia, które przyjmują dokumenty źródłowe i generują całkowicie nowe dokumenty wynikowe o pożądanym kształcie.</span><span class="sxs-lookup"><span data-stu-id="2f916-113">When using the functional approach, you write transformations that take the source documents and generate completely new result documents with the desired shape.</span></span>  
  
 <span data-ttu-id="2f916-114">Podczas modyfikowania drzewa XML w miejscu, należy napisać kod, który przechodzi i porusza się po węzłach w drzewie XML w pamięci, wstawianie, usuwanie i modyfikowanie węzłów w razie potrzeby.</span><span class="sxs-lookup"><span data-stu-id="2f916-114">When modifying an XML tree in place, you write code that traverses and navigates through nodes in an in-memory XML tree, inserting, deleting, and modifying nodes as necessary.</span></span>  
  
 <span data-ttu-id="2f916-115">Linq można użyć do XML z obu podejść.</span><span class="sxs-lookup"><span data-stu-id="2f916-115">You can use LINQ to XML with either approach.</span></span> <span data-ttu-id="2f916-116">Używasz tych samych klas, a w niektórych przypadkach te same metody.</span><span class="sxs-lookup"><span data-stu-id="2f916-116">You use the same classes, and in some cases the same methods.</span></span> <span data-ttu-id="2f916-117">Jednak struktura i cele obu podejść są bardzo różne.</span><span class="sxs-lookup"><span data-stu-id="2f916-117">However, the structure and goals of the two approaches are very different.</span></span> <span data-ttu-id="2f916-118">Na przykład w różnych sytuacjach jedno lub drugie podejście często mają lepszą wydajność i używać więcej lub mniej pamięci.</span><span class="sxs-lookup"><span data-stu-id="2f916-118">For example, in different situations, one or the other approach will often have better performance, and use more or less memory.</span></span> <span data-ttu-id="2f916-119">Ponadto jedno lub drugie podejście będzie łatwiejsze do napisania i przynieść więcej kodu do konserwacji.</span><span class="sxs-lookup"><span data-stu-id="2f916-119">In addition, one or the other approach will be easier to write and yield more maintainable code.</span></span>  
  
 <span data-ttu-id="2f916-120">Aby zobaczyć dwa podejścia skontrastowane, zobacz [Modyfikacja drzewa XML w pamięci vs. Konstrukcja funkcjonalna (LINQ do XML) (C#)](./in-memory-xml-tree-modification-vs-functional-construction-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="2f916-120">To see the two approaches contrasted, see [In-Memory XML Tree Modification vs. Functional Construction (LINQ to XML) (C#)](./in-memory-xml-tree-modification-vs-functional-construction-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="2f916-121">Aby zapoznać się z samouczkiem na temat pisania przekształceń funkcjonalnych, zobacz [Czyste transformacje funkcjonalne języka XML (C#).](./introduction-to-pure-functional-transformations.md)</span><span class="sxs-lookup"><span data-stu-id="2f916-121">For a tutorial on writing functional transformations, see [Pure Functional Transformations of XML (C#)](./introduction-to-pure-functional-transformations.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2f916-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2f916-122">See also</span></span>

- [<span data-ttu-id="2f916-123">Omówienie programowania LINQ do XML (C#)</span><span class="sxs-lookup"><span data-stu-id="2f916-123">LINQ to XML Programming Overview (C#)</span></span>](./linq-to-xml-overview.md)
