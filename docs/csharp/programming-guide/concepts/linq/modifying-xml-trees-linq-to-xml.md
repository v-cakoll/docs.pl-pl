---
title: Modyfikowanie drzew XML (LINQ do XML) (C#)
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 8ec47e6d-2363-4694-be46-8d5ca4d15fc9
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 8cf3ffabeb7c3caa5f0e3e38fb6f69551ce791b3
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="modifying-xml-trees-linq-to-xml-c"></a><span data-ttu-id="bc0cc-102">Modyfikowanie drzew XML (LINQ do XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="bc0cc-102">Modifying XML Trees (LINQ to XML) (C#)</span></span>
[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="bc0cc-103">jest magazynu w pamięci dla drzewa XML.</span><span class="sxs-lookup"><span data-stu-id="bc0cc-103"> is an in-memory store for an XML tree.</span></span> <span data-ttu-id="bc0cc-104">Po załadować lub przeanalizować drzewo XML ze źródła, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] umożliwia modyfikowanie tego drzewa w miejscu, a następnie serializować drzewa, być może zapisać go do pliku lub wysłanie ich do serwera zdalnego.</span><span class="sxs-lookup"><span data-stu-id="bc0cc-104">After you load or parse an XML tree from a source, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] lets you modify that tree in place, and then serialize the tree, perhaps saving it to a file or sending it to a remote server.</span></span>  
  
 <span data-ttu-id="bc0cc-105">Po zmodyfikowaniu drzewa w miejscu niektórych metod, takich jak używać <xref:System.Xml.Linq.XContainer.Add%2A>.</span><span class="sxs-lookup"><span data-stu-id="bc0cc-105">When you modify a tree in place, you use certain methods, such as <xref:System.Xml.Linq.XContainer.Add%2A>.</span></span>  
  
 <span data-ttu-id="bc0cc-106">Istnieje jednak innym rozwiązaniem, który jest używany konstrukcji funkcjonalności do generowania nowego drzewa z innego kształtu.</span><span class="sxs-lookup"><span data-stu-id="bc0cc-106">However, there is another approach, which is to use functional construction to generate a new tree with a different shape.</span></span> <span data-ttu-id="bc0cc-107">W zależności od typów zmian, które należy wprowadzić swoje drzewo XML, a w zależności od wielkości drzewa ta metoda może być bardziej niezawodne i łatwiejsze do opracowywania.</span><span class="sxs-lookup"><span data-stu-id="bc0cc-107">Depending on the types of changes that you need to make to your XML tree, and depending on the size of the tree, this approach can be more robust and easier to develop.</span></span> <span data-ttu-id="bc0cc-108">Pierwszym temacie w tej sekcji porównanie tych dwóch metod.</span><span class="sxs-lookup"><span data-stu-id="bc0cc-108">The first topic in this section compares these two approaches.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="bc0cc-109">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="bc0cc-109">In This Section</span></span>  
  
|<span data-ttu-id="bc0cc-110">Temat</span><span class="sxs-lookup"><span data-stu-id="bc0cc-110">Topic</span></span>|<span data-ttu-id="bc0cc-111">Opis</span><span class="sxs-lookup"><span data-stu-id="bc0cc-111">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="bc0cc-112">Vs modyfikacji drzewa XML w pamięci. Konstrukcja funkcjonalności (LINQ do XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="bc0cc-112">In-Memory XML Tree Modification vs. Functional Construction (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/in-memory-xml-tree-modification-vs-functional-construction-linq-to-xml.md)|<span data-ttu-id="bc0cc-113">Porównuje modyfikowanie drzewo XML w pamięci do budowy funkcjonalności.</span><span class="sxs-lookup"><span data-stu-id="bc0cc-113">Compares modifying an XML tree in memory to functional construction.</span></span>|  
|[<span data-ttu-id="bc0cc-114">Dodawanie elementy, atrybuty i węzłów do drzewa XML (C#)</span><span class="sxs-lookup"><span data-stu-id="bc0cc-114">Adding Elements, Attributes, and Nodes to an XML Tree (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/adding-elements-attributes-and-nodes-to-an-xml-tree.md)|<span data-ttu-id="bc0cc-115">Zawiera informacje o dodawaniu elementy, atrybuty lub węzłów do drzewa XML.</span><span class="sxs-lookup"><span data-stu-id="bc0cc-115">Provides information about adding elements, attributes, or nodes to an XML tree.</span></span>|  
|[<span data-ttu-id="bc0cc-116">Modyfikowanie elementy, atrybuty i węzłów w drzewie XML</span><span class="sxs-lookup"><span data-stu-id="bc0cc-116">Modifying Elements, Attributes, and Nodes in an XML Tree</span></span>](../../../../csharp/programming-guide/concepts/linq/modifying-elements-attributes-and-nodes-in-an-xml-tree.md)|<span data-ttu-id="bc0cc-117">Zawiera informacje dotyczące modyfikowania istniejące elementy, atrybuty lub węzłów.</span><span class="sxs-lookup"><span data-stu-id="bc0cc-117">Provides information about modifying existing elements, attributes, or nodes.</span></span>|  
|[<span data-ttu-id="bc0cc-118">Usuwanie elementy, atrybuty i węzły z drzewa XML (C#)</span><span class="sxs-lookup"><span data-stu-id="bc0cc-118">Removing Elements, Attributes, and Nodes from an XML Tree (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/removing-elements-attributes-and-nodes-from-an-xml-tree.md)|<span data-ttu-id="bc0cc-119">Zawiera informacje o usuwaniu elementy, atrybuty lub węzłów w drzewie XML.</span><span class="sxs-lookup"><span data-stu-id="bc0cc-119">Provides information about removing elements, attributes, or nodes from the XML tree.</span></span>|  
|[<span data-ttu-id="bc0cc-120">Obsługa pary nazwa/wartość (C#)</span><span class="sxs-lookup"><span data-stu-id="bc0cc-120">Maintaining Name/Value Pairs (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/maintaining-name-value-pairs.md)|<span data-ttu-id="bc0cc-121">Zawiera opis sposobu obsługi informacji o aplikacji, która najlepiej jest przechowywane jako pary nazwa/wartość, takie jak informacje o konfiguracji lub ustawień globalnych.</span><span class="sxs-lookup"><span data-stu-id="bc0cc-121">Describes how to maintain application information that is best kept as name/value pairs, such as configuration information or global settings.</span></span>|  
|[<span data-ttu-id="bc0cc-122">Porady: Zmienianie Namespace drzewo całego XML (C#)</span><span class="sxs-lookup"><span data-stu-id="bc0cc-122">How to: Change the Namespace for an Entire XML Tree (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-change-the-namespace-for-an-entire-xml-tree.md)|<span data-ttu-id="bc0cc-123">Przedstawia sposób przenoszenia drzewa XML z jednej przestrzeni nazw do innego.</span><span class="sxs-lookup"><span data-stu-id="bc0cc-123">Shows how to move an XML tree from one namespace into another.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="bc0cc-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="bc0cc-124">See Also</span></span>  
 [<span data-ttu-id="bc0cc-125">Przewodnik programowania w języku (LINQ do XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="bc0cc-125">Programming Guide (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/programming-guide-linq-to-xml.md)
