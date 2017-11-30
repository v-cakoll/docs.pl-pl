---
title: "Vs funkcjonalności. Programowanie procedurach (LINQ do XML) (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: fc64e39c-a487-4882-9169-da4de97917d9
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: b6aa8ce45afdb68f7ff544b8c8f2f5e1e4a79533
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="functional-vs-procedural-programming-linq-to-xml-c"></a><span data-ttu-id="0472d-102">Vs funkcjonalności. Programowanie procedurach (LINQ do XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="0472d-102">Functional vs. Procedural Programming (LINQ to XML) (C#)</span></span>
<span data-ttu-id="0472d-103">Istnieją różne typy aplikacji XML:</span><span class="sxs-lookup"><span data-stu-id="0472d-103">There are various types of XML applications:</span></span>  
  
-   <span data-ttu-id="0472d-104">Niektóre aplikacje zająć dokumentów XML źródła i utworzyć nowe dokumenty XML, znajdujących się w kształcie innego niż dokumenty źródła.</span><span class="sxs-lookup"><span data-stu-id="0472d-104">Some applications take source XML documents, and produce new XML documents that are in a different shape than the source documents.</span></span>  
  
-   <span data-ttu-id="0472d-105">Niektóre aplikacje zająć dokumentów XML źródła i tworzenie dokumentów wynik w postaci zupełnie innego, takich jak pliki tekstowe HTML lub CSV.</span><span class="sxs-lookup"><span data-stu-id="0472d-105">Some applications take source XML documents, and produce result documents in an entirely different form, such as HTML or CSV text files.</span></span>  
  
-   <span data-ttu-id="0472d-106">Niektóre aplikacje zająć dokumentów XML źródła i Wstaw rekordy w bazie danych.</span><span class="sxs-lookup"><span data-stu-id="0472d-106">Some applications take source XML documents, and insert records into a database.</span></span>  
  
-   <span data-ttu-id="0472d-107">Niektóre aplikacje pobierają dane z innego źródła, na przykład w bazie danych i tworzenie dokumentów XML z niego.</span><span class="sxs-lookup"><span data-stu-id="0472d-107">Some applications take data from another source, such as a database, and create XML documents from it.</span></span>  
  
 <span data-ttu-id="0472d-108">Nie są one wszystkich typów aplikacji XML, ale są one reprezentatywny zestaw typów funkcji, aby zaimplementować programisty XML.</span><span class="sxs-lookup"><span data-stu-id="0472d-108">These are not all of the types of XML applications, but these are a representative set of the types of functionality that an XML programmer has to implement.</span></span>  
  
 <span data-ttu-id="0472d-109">Wszystkie aplikacje tego typu istnieją dwie metody kontrastujące deweloper może zająć:</span><span class="sxs-lookup"><span data-stu-id="0472d-109">With all of these types of applications, there are two contrasting approaches that a developer can take:</span></span>  
  
-   <span data-ttu-id="0472d-110">Budowa funkcjonalności deklaratywne podejście.</span><span class="sxs-lookup"><span data-stu-id="0472d-110">Functional construction using a declarative approach.</span></span>  
  
-   <span data-ttu-id="0472d-111">Przy użyciu kodu procedurach modyfikacji drzewa XML w pamięci.</span><span class="sxs-lookup"><span data-stu-id="0472d-111">In-memory XML tree modification using procedural code.</span></span>  
  
 <span data-ttu-id="0472d-112">LINQ do XML obsługuje obu podejść.</span><span class="sxs-lookup"><span data-stu-id="0472d-112">LINQ to XML supports both approaches.</span></span>  
  
 <span data-ttu-id="0472d-113">Korzystając z funkcjonalności podejście, należy napisać przekształcenia, które podejmują dokumentów źródłowych i generowanie całkowicie nowych dokumentów wynik żądanego kształtu.</span><span class="sxs-lookup"><span data-stu-id="0472d-113">When using the functional approach, you write transformations that take the source documents and generate completely new result documents with the desired shape.</span></span>  
  
 <span data-ttu-id="0472d-114">Podczas modyfikowania drzewo XML w miejscu, pisania kodu, który jest przesyłany i nawiguje węzłów w drzewie XML w pamięci, wstawianie, usuwanie i modyfikowanie węzłów w razie potrzeby.</span><span class="sxs-lookup"><span data-stu-id="0472d-114">When modifying an XML tree in place, you write code that traverses and navigates through nodes in an in-memory XML tree, inserting, deleting, and modifying nodes as necessary.</span></span>  
  
 <span data-ttu-id="0472d-115">LINQ do XML można użyć obu metod.</span><span class="sxs-lookup"><span data-stu-id="0472d-115">You can use LINQ to XML with either approach.</span></span> <span data-ttu-id="0472d-116">Użyj tej samej klasy, a w niektórych przypadkach te same metody.</span><span class="sxs-lookup"><span data-stu-id="0472d-116">You use the same classes, and in some cases the same methods.</span></span> <span data-ttu-id="0472d-117">Jednak struktury i celów dwa podejścia są bardzo różnią się.</span><span class="sxs-lookup"><span data-stu-id="0472d-117">However, the structure and goals of the two approaches are very different.</span></span> <span data-ttu-id="0472d-118">Na przykład w różnych sytuacjach co najmniej inne podejścia będzie często mają lepszą wydajność i użyj bardziej lub mniej pamięci.</span><span class="sxs-lookup"><span data-stu-id="0472d-118">For example, in different situations, one or the other approach will often have better performance, and use more or less memory.</span></span> <span data-ttu-id="0472d-119">Ponadto jedna lub innej metody będzie łatwiejszy do zapisu i uzyskanie kodu za więcej.</span><span class="sxs-lookup"><span data-stu-id="0472d-119">In addition, one or the other approach will be easier to write and yield more maintainable code.</span></span>  
  
 <span data-ttu-id="0472d-120">Aby wyświetlić dwa podejścia odróżniające, zobacz [vs modyfikacji drzewa XML w pamięci. Konstrukcja funkcjonalności (LINQ do XML) (C#)](../../../../csharp/programming-guide/concepts/linq/in-memory-xml-tree-modification-vs-functional-construction-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="0472d-120">To see the two approaches contrasted, see [In-Memory XML Tree Modification vs. Functional Construction (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/in-memory-xml-tree-modification-vs-functional-construction-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="0472d-121">Samouczek dotyczący zapisywania przekształcenia funkcjonalności, zobacz [czysty funkcjonalności transformacji XML (C#)](../../../../csharp/programming-guide/concepts/linq/pure-functional-transformations-of-xml.md).</span><span class="sxs-lookup"><span data-stu-id="0472d-121">For a tutorial on writing functional transformations, see [Pure Functional Transformations of XML (C#)](../../../../csharp/programming-guide/concepts/linq/pure-functional-transformations-of-xml.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0472d-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0472d-122">See Also</span></span>  
 [<span data-ttu-id="0472d-123">LINQ do XML-przegląd programowania w języku (C#)</span><span class="sxs-lookup"><span data-stu-id="0472d-123">LINQ to XML Programming Overview (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-programming-overview.md)
