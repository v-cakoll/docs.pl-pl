---
title: Programowanie funkcjonalne a Proceduralne (LINQ to XML) (C#)
ms.date: 07/20/2015
ms.assetid: fc64e39c-a487-4882-9169-da4de97917d9
ms.openlocfilehash: 888c360e1b868c79d378f2fc46a26c152121300f
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2018
ms.locfileid: "44071768"
---
# <a name="functional-vs-procedural-programming-linq-to-xml-c"></a><span data-ttu-id="cd4ff-102">Programowanie funkcjonalne a Proceduralne (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="cd4ff-102">Functional vs. Procedural Programming (LINQ to XML) (C#)</span></span>
<span data-ttu-id="cd4ff-103">Istnieją różne rodzaje aplikacji XML:</span><span class="sxs-lookup"><span data-stu-id="cd4ff-103">There are various types of XML applications:</span></span>  
  
-   <span data-ttu-id="cd4ff-104">Niektóre aplikacje źródła dokumentów XML i tworzące nowe dokumenty XML znajdujących się w innym kształcie niż dokumentów źródłowych.</span><span class="sxs-lookup"><span data-stu-id="cd4ff-104">Some applications take source XML documents, and produce new XML documents that are in a different shape than the source documents.</span></span>  
  
-   <span data-ttu-id="cd4ff-105">Niektóre aplikacje źródła dokumentów XML i tworzące dokumenty wynik w postaci zupełnie innego, takich jak pliki tekst HTML lub CSV.</span><span class="sxs-lookup"><span data-stu-id="cd4ff-105">Some applications take source XML documents, and produce result documents in an entirely different form, such as HTML or CSV text files.</span></span>  
  
-   <span data-ttu-id="cd4ff-106">Niektóre aplikacje zająć dokumentów XML źródła i wstawiania rekordów do bazy danych.</span><span class="sxs-lookup"><span data-stu-id="cd4ff-106">Some applications take source XML documents, and insert records into a database.</span></span>  
  
-   <span data-ttu-id="cd4ff-107">Niektóre aplikacje pobierają dane z innego źródła, takich jak bazy danych i tworzenie dokumentów XML z niego.</span><span class="sxs-lookup"><span data-stu-id="cd4ff-107">Some applications take data from another source, such as a database, and create XML documents from it.</span></span>  
  
 <span data-ttu-id="cd4ff-108">Nie są to wszystkie typy aplikacji XML, ale są to reprezentatywny zestaw typów, funkcji, który musi zaimplementować programista XML.</span><span class="sxs-lookup"><span data-stu-id="cd4ff-108">These are not all of the types of XML applications, but these are a representative set of the types of functionality that an XML programmer has to implement.</span></span>  
  
 <span data-ttu-id="cd4ff-109">W przypadku wszystkich tych rodzajów aplikacji istnieją dwie metody kontrastujące deweloper może potrwać:</span><span class="sxs-lookup"><span data-stu-id="cd4ff-109">With all of these types of applications, there are two contrasting approaches that a developer can take:</span></span>  
  
-   <span data-ttu-id="cd4ff-110">Konstrukcja funkcjonalna przy użyciu podejścia deklaratywnego.</span><span class="sxs-lookup"><span data-stu-id="cd4ff-110">Functional construction using a declarative approach.</span></span>  
  
-   <span data-ttu-id="cd4ff-111">Za pomocą kod proceduralny modyfikowanie drzewa XML w pamięci.</span><span class="sxs-lookup"><span data-stu-id="cd4ff-111">In-memory XML tree modification using procedural code.</span></span>  
  
 <span data-ttu-id="cd4ff-112">LINQ to XML obsługuje oba podejścia.</span><span class="sxs-lookup"><span data-stu-id="cd4ff-112">LINQ to XML supports both approaches.</span></span>  
  
 <span data-ttu-id="cd4ff-113">Korzystając z podejścia funkcjonalności, można napisać przekształcenia używające dokumentów źródłowych i generować zupełnie nowe dokumenty wyniku żądanego kształtu.</span><span class="sxs-lookup"><span data-stu-id="cd4ff-113">When using the functional approach, you write transformations that take the source documents and generate completely new result documents with the desired shape.</span></span>  
  
 <span data-ttu-id="cd4ff-114">Podczas modyfikowania drzewa XML w miejscu, pisania kodu, który przechodzi przez i przechodzi przez węzły w drzewie XML w pamięci, wstawianie, usuwanie i modyfikowanie węzłów, zgodnie z potrzebami.</span><span class="sxs-lookup"><span data-stu-id="cd4ff-114">When modifying an XML tree in place, you write code that traverses and navigates through nodes in an in-memory XML tree, inserting, deleting, and modifying nodes as necessary.</span></span>  
  
 <span data-ttu-id="cd4ff-115">Za pomocą LINQ to XML każda z tych metod.</span><span class="sxs-lookup"><span data-stu-id="cd4ff-115">You can use LINQ to XML with either approach.</span></span> <span data-ttu-id="cd4ff-116">Użyj tych samych klas, a w niektórych przypadkach te same metody.</span><span class="sxs-lookup"><span data-stu-id="cd4ff-116">You use the same classes, and in some cases the same methods.</span></span> <span data-ttu-id="cd4ff-117">Struktury i celów dwie metody są jednak bardzo różnią się.</span><span class="sxs-lookup"><span data-stu-id="cd4ff-117">However, the structure and goals of the two approaches are very different.</span></span> <span data-ttu-id="cd4ff-118">Na przykład w różnych sytuacjach co najmniej inne podejście będzie często mają lepszą wydajność i używać więcej lub mniej pamięci.</span><span class="sxs-lookup"><span data-stu-id="cd4ff-118">For example, in different situations, one or the other approach will often have better performance, and use more or less memory.</span></span> <span data-ttu-id="cd4ff-119">Ponadto co najmniej inne podejście będzie można łatwiej napisać i uzyskanie więcej kodu łatwego w utrzymaniu.</span><span class="sxs-lookup"><span data-stu-id="cd4ff-119">In addition, one or the other approach will be easier to write and yield more maintainable code.</span></span>  
  
 <span data-ttu-id="cd4ff-120">Aby wyświetlić dwa podejścia porównanie, zobacz [vs modyfikowanie drzewa XML w pamięci. Konstrukcja funkcjonalna (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/in-memory-xml-tree-modification-vs-functional-construction-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="cd4ff-120">To see the two approaches contrasted, see [In-Memory XML Tree Modification vs. Functional Construction (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/in-memory-xml-tree-modification-vs-functional-construction-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="cd4ff-121">Samouczek na temat pisania przekształceń funkcjonalnych, zobacz [czystego funkcjonalności przekształcenia XML (C#)](../../../../csharp/programming-guide/concepts/linq/pure-functional-transformations-of-xml.md).</span><span class="sxs-lookup"><span data-stu-id="cd4ff-121">For a tutorial on writing functional transformations, see [Pure Functional Transformations of XML (C#)](../../../../csharp/programming-guide/concepts/linq/pure-functional-transformations-of-xml.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cd4ff-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="cd4ff-122">See Also</span></span>

- [<span data-ttu-id="cd4ff-123">LINQ to XML — przegląd programowania (C#)</span><span class="sxs-lookup"><span data-stu-id="cd4ff-123">LINQ to XML Programming Overview (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-programming-overview.md)
