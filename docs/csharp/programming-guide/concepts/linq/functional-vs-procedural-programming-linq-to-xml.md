---
title: Vs funkcjonalności. Programowanie procedurach (LINQ do XML) (C#)
ms.date: 07/20/2015
ms.assetid: fc64e39c-a487-4882-9169-da4de97917d9
ms.openlocfilehash: 16d78e967fd5379940ac93c82e3bb59c60941e58
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33328217"
---
# <a name="functional-vs-procedural-programming-linq-to-xml-c"></a><span data-ttu-id="fae38-102">Vs funkcjonalności. Programowanie procedurach (LINQ do XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="fae38-102">Functional vs. Procedural Programming (LINQ to XML) (C#)</span></span>
<span data-ttu-id="fae38-103">Istnieją różne typy aplikacji XML:</span><span class="sxs-lookup"><span data-stu-id="fae38-103">There are various types of XML applications:</span></span>  
  
-   <span data-ttu-id="fae38-104">Niektóre aplikacje zająć dokumentów XML źródła i utworzyć nowe dokumenty XML, znajdujących się w kształcie innego niż dokumenty źródła.</span><span class="sxs-lookup"><span data-stu-id="fae38-104">Some applications take source XML documents, and produce new XML documents that are in a different shape than the source documents.</span></span>  
  
-   <span data-ttu-id="fae38-105">Niektóre aplikacje zająć dokumentów XML źródła i tworzenie dokumentów wynik w postaci zupełnie innego, takich jak pliki tekstowe HTML lub CSV.</span><span class="sxs-lookup"><span data-stu-id="fae38-105">Some applications take source XML documents, and produce result documents in an entirely different form, such as HTML or CSV text files.</span></span>  
  
-   <span data-ttu-id="fae38-106">Niektóre aplikacje zająć dokumentów XML źródła i Wstaw rekordy w bazie danych.</span><span class="sxs-lookup"><span data-stu-id="fae38-106">Some applications take source XML documents, and insert records into a database.</span></span>  
  
-   <span data-ttu-id="fae38-107">Niektóre aplikacje pobierają dane z innego źródła, na przykład w bazie danych i tworzenie dokumentów XML z niego.</span><span class="sxs-lookup"><span data-stu-id="fae38-107">Some applications take data from another source, such as a database, and create XML documents from it.</span></span>  
  
 <span data-ttu-id="fae38-108">Nie są one wszystkich typów aplikacji XML, ale są one reprezentatywny zestaw typów funkcji, aby zaimplementować programisty XML.</span><span class="sxs-lookup"><span data-stu-id="fae38-108">These are not all of the types of XML applications, but these are a representative set of the types of functionality that an XML programmer has to implement.</span></span>  
  
 <span data-ttu-id="fae38-109">Wszystkie aplikacje tego typu istnieją dwie metody kontrastujące deweloper może zająć:</span><span class="sxs-lookup"><span data-stu-id="fae38-109">With all of these types of applications, there are two contrasting approaches that a developer can take:</span></span>  
  
-   <span data-ttu-id="fae38-110">Budowa funkcjonalności deklaratywne podejście.</span><span class="sxs-lookup"><span data-stu-id="fae38-110">Functional construction using a declarative approach.</span></span>  
  
-   <span data-ttu-id="fae38-111">Przy użyciu kodu procedurach modyfikacji drzewa XML w pamięci.</span><span class="sxs-lookup"><span data-stu-id="fae38-111">In-memory XML tree modification using procedural code.</span></span>  
  
 <span data-ttu-id="fae38-112">LINQ do XML obsługuje obu podejść.</span><span class="sxs-lookup"><span data-stu-id="fae38-112">LINQ to XML supports both approaches.</span></span>  
  
 <span data-ttu-id="fae38-113">Korzystając z funkcjonalności podejście, należy napisać przekształcenia, które podejmują dokumentów źródłowych i generowanie całkowicie nowych dokumentów wynik żądanego kształtu.</span><span class="sxs-lookup"><span data-stu-id="fae38-113">When using the functional approach, you write transformations that take the source documents and generate completely new result documents with the desired shape.</span></span>  
  
 <span data-ttu-id="fae38-114">Podczas modyfikowania drzewo XML w miejscu, pisania kodu, który jest przesyłany i nawiguje węzłów w drzewie XML w pamięci, wstawianie, usuwanie i modyfikowanie węzłów w razie potrzeby.</span><span class="sxs-lookup"><span data-stu-id="fae38-114">When modifying an XML tree in place, you write code that traverses and navigates through nodes in an in-memory XML tree, inserting, deleting, and modifying nodes as necessary.</span></span>  
  
 <span data-ttu-id="fae38-115">LINQ do XML można użyć obu metod.</span><span class="sxs-lookup"><span data-stu-id="fae38-115">You can use LINQ to XML with either approach.</span></span> <span data-ttu-id="fae38-116">Użyj tej samej klasy, a w niektórych przypadkach te same metody.</span><span class="sxs-lookup"><span data-stu-id="fae38-116">You use the same classes, and in some cases the same methods.</span></span> <span data-ttu-id="fae38-117">Jednak struktury i celów dwa podejścia są bardzo różnią się.</span><span class="sxs-lookup"><span data-stu-id="fae38-117">However, the structure and goals of the two approaches are very different.</span></span> <span data-ttu-id="fae38-118">Na przykład w różnych sytuacjach co najmniej inne podejścia będzie często mają lepszą wydajność i użyj bardziej lub mniej pamięci.</span><span class="sxs-lookup"><span data-stu-id="fae38-118">For example, in different situations, one or the other approach will often have better performance, and use more or less memory.</span></span> <span data-ttu-id="fae38-119">Ponadto jedna lub innej metody będzie łatwiejszy do zapisu i uzyskanie kodu za więcej.</span><span class="sxs-lookup"><span data-stu-id="fae38-119">In addition, one or the other approach will be easier to write and yield more maintainable code.</span></span>  
  
 <span data-ttu-id="fae38-120">Aby wyświetlić dwa podejścia odróżniające, zobacz [vs modyfikacji drzewa XML w pamięci. Konstrukcja funkcjonalności (LINQ do XML) (C#)](../../../../csharp/programming-guide/concepts/linq/in-memory-xml-tree-modification-vs-functional-construction-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="fae38-120">To see the two approaches contrasted, see [In-Memory XML Tree Modification vs. Functional Construction (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/in-memory-xml-tree-modification-vs-functional-construction-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="fae38-121">Samouczek dotyczący zapisywania przekształcenia funkcjonalności, zobacz [czysty funkcjonalności transformacji XML (C#)](../../../../csharp/programming-guide/concepts/linq/pure-functional-transformations-of-xml.md).</span><span class="sxs-lookup"><span data-stu-id="fae38-121">For a tutorial on writing functional transformations, see [Pure Functional Transformations of XML (C#)](../../../../csharp/programming-guide/concepts/linq/pure-functional-transformations-of-xml.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fae38-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="fae38-122">See Also</span></span>  
 [<span data-ttu-id="fae38-123">LINQ do XML-przegląd programowania w języku (C#)</span><span class="sxs-lookup"><span data-stu-id="fae38-123">LINQ to XML Programming Overview (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-programming-overview.md)
