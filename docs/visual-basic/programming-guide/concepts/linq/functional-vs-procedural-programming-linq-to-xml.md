---
title: Programowanie funkcjonalne a Proceduralne (LINQ to XML) (Visual Basic)
ms.date: 07/20/2015
ms.assetid: ea1015a5-d4c8-4d79-8e1e-ba17a40a4f39
ms.openlocfilehash: f7e57ab2db5fa20a3a8414058573ca96e30e80d7
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64618255"
---
# <a name="functional-vs-procedural-programming-linq-to-xml-visual-basic"></a><span data-ttu-id="20fe5-102">Programowanie funkcjonalne a Proceduralne (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="20fe5-102">Functional vs. Procedural Programming (LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="20fe5-103">Istnieją różne rodzaje aplikacji XML:</span><span class="sxs-lookup"><span data-stu-id="20fe5-103">There are various types of XML applications:</span></span>  
  
- <span data-ttu-id="20fe5-104">Niektóre aplikacje źródła dokumentów XML i tworzące nowe dokumenty XML znajdujących się w innym kształcie niż dokumentów źródłowych.</span><span class="sxs-lookup"><span data-stu-id="20fe5-104">Some applications take source XML documents, and produce new XML documents that are in a different shape than the source documents.</span></span>  
  
- <span data-ttu-id="20fe5-105">Niektóre aplikacje źródła dokumentów XML i tworzące dokumenty wynik w postaci zupełnie innego, takich jak pliki tekst HTML lub CSV.</span><span class="sxs-lookup"><span data-stu-id="20fe5-105">Some applications take source XML documents, and produce result documents in an entirely different form, such as HTML or CSV text files.</span></span>  
  
- <span data-ttu-id="20fe5-106">Niektóre aplikacje zająć dokumentów XML źródła i wstawiania rekordów do bazy danych.</span><span class="sxs-lookup"><span data-stu-id="20fe5-106">Some applications take source XML documents, and insert records into a database.</span></span>  
  
- <span data-ttu-id="20fe5-107">Niektóre aplikacje pobierają dane z innego źródła, takich jak bazy danych i tworzenie dokumentów XML z niego.</span><span class="sxs-lookup"><span data-stu-id="20fe5-107">Some applications take data from another source, such as a database, and create XML documents from it.</span></span>  
  
 <span data-ttu-id="20fe5-108">Nie są to wszystkie typy aplikacji XML, ale są to reprezentatywny zestaw typów, funkcji, który musi zaimplementować programista XML.</span><span class="sxs-lookup"><span data-stu-id="20fe5-108">These are not all of the types of XML applications, but these are a representative set of the types of functionality that an XML programmer has to implement.</span></span>  
  
 <span data-ttu-id="20fe5-109">W przypadku wszystkich tych rodzajów aplikacji istnieją dwie metody kontrastujące deweloper może potrwać:</span><span class="sxs-lookup"><span data-stu-id="20fe5-109">With all of these types of applications, there are two contrasting approaches that a developer can take:</span></span>  
  
- <span data-ttu-id="20fe5-110">Konstrukcja funkcjonalna przy użyciu podejścia deklaratywnego.</span><span class="sxs-lookup"><span data-stu-id="20fe5-110">Functional construction using a declarative approach.</span></span>  
  
- <span data-ttu-id="20fe5-111">Za pomocą kod proceduralny modyfikowanie drzewa XML w pamięci.</span><span class="sxs-lookup"><span data-stu-id="20fe5-111">In-memory XML tree modification using procedural code.</span></span>  
  
 <span data-ttu-id="20fe5-112">LINQ to XML obsługuje oba podejścia.</span><span class="sxs-lookup"><span data-stu-id="20fe5-112">LINQ to XML supports both approaches.</span></span>  
  
 <span data-ttu-id="20fe5-113">Korzystając z podejścia funkcjonalności, można napisać przekształcenia używające dokumentów źródłowych i generować zupełnie nowe dokumenty wyniku żądanego kształtu.</span><span class="sxs-lookup"><span data-stu-id="20fe5-113">When using the functional approach, you write transformations that take the source documents and generate completely new result documents with the desired shape.</span></span>  
  
 <span data-ttu-id="20fe5-114">Podczas modyfikowania drzewa XML w miejscu, pisania kodu, który przechodzi przez i przechodzi przez węzły w drzewie XML w pamięci, wstawianie, usuwanie i modyfikowanie węzłów, zgodnie z potrzebami.</span><span class="sxs-lookup"><span data-stu-id="20fe5-114">When modifying an XML tree in place, you write code that traverses and navigates through nodes in an in-memory XML tree, inserting, deleting, and modifying nodes as necessary.</span></span>  
  
 <span data-ttu-id="20fe5-115">Za pomocą LINQ to XML każda z tych metod.</span><span class="sxs-lookup"><span data-stu-id="20fe5-115">You can use LINQ to XML with either approach.</span></span> <span data-ttu-id="20fe5-116">Użyj tych samych klas, a w niektórych przypadkach te same metody.</span><span class="sxs-lookup"><span data-stu-id="20fe5-116">You use the same classes, and in some cases the same methods.</span></span> <span data-ttu-id="20fe5-117">Struktury i celów dwie metody są jednak bardzo różnią się.</span><span class="sxs-lookup"><span data-stu-id="20fe5-117">However, the structure and goals of the two approaches are very different.</span></span> <span data-ttu-id="20fe5-118">Na przykład w różnych sytuacjach co najmniej inne podejście będzie często mają lepszą wydajność i używać więcej lub mniej pamięci.</span><span class="sxs-lookup"><span data-stu-id="20fe5-118">For example, in different situations, one or the other approach will often have better performance, and use more or less memory.</span></span> <span data-ttu-id="20fe5-119">Ponadto co najmniej inne podejście będzie można łatwiej napisać i uzyskanie więcej kodu łatwego w utrzymaniu.</span><span class="sxs-lookup"><span data-stu-id="20fe5-119">In addition, one or the other approach will be easier to write and yield more maintainable code.</span></span>  
  
 <span data-ttu-id="20fe5-120">Aby wyświetlić dwa podejścia porównanie, zobacz [vs modyfikowanie drzewa XML w pamięci. Konstrukcja funkcjonalna (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/in-memory-xml-tree-modification-vs-functional-construction.md).</span><span class="sxs-lookup"><span data-stu-id="20fe5-120">To see the two approaches contrasted, see [In-Memory XML Tree Modification vs. Functional Construction (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/in-memory-xml-tree-modification-vs-functional-construction.md).</span></span>  
  
 <span data-ttu-id="20fe5-121">Samouczek na temat pisania przekształceń funkcjonalnych, zobacz [czystego funkcjonalności przekształcenia XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/pure-functional-transformations-of-xml.md).</span><span class="sxs-lookup"><span data-stu-id="20fe5-121">For a tutorial on writing functional transformations, see [Pure Functional Transformations of XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/pure-functional-transformations-of-xml.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="20fe5-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="20fe5-122">See also</span></span>

- [<span data-ttu-id="20fe5-123">LINQ to XML — przegląd programowania (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="20fe5-123">LINQ to XML Programming Overview (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-programming-overview.md)
