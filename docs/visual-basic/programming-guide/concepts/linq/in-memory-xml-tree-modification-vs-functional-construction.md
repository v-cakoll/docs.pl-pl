---
title: Modyfikowanie drzewa XML w pamięci a konstrukcja funkcjonalna (LINQ to XML)
ms.date: 07/20/2015
ms.assetid: d91c4ebf-6549-43cc-9961-26d4a82f722b
ms.openlocfilehash: efdbf51efa0f502ac9991d520defe45bb95678b7
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84397612"
---
# <a name="in-memory-xml-tree-modification-vs-functional-construction-linq-to-xml-visual-basic"></a><span data-ttu-id="29b08-102">Modyfikowanie drzewa XML w pamięci a konstrukcja funkcjonalna (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="29b08-102">In-Memory XML Tree Modification vs. Functional Construction (LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="29b08-103">Modyfikowanie drzewa XML jest tradycyjnym podejściem do zmiany kształtu dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="29b08-103">Modifying an XML tree in place is a traditional approach to changing the shape of an XML document.</span></span> <span data-ttu-id="29b08-104">Typowa aplikacja ładuje dokument do magazynu danych, takiego jak DOM lub [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] ; używa interfejsu programowania, aby wstawiać węzły, usuwać węzły lub zmieniać zawartość węzłów, a następnie zapisuje dane XML do pliku lub przesyła je za pośrednictwem sieci.</span><span class="sxs-lookup"><span data-stu-id="29b08-104">A typical application loads a document into a data store such as DOM or [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]; uses a programming interface to insert nodes, delete nodes, or change the content of nodes; and then saves the XML to a file or transmits it over a network.</span></span>  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="29b08-105">umożliwia kolejną metodę, która jest przydatna w wielu scenariuszach *: konstrukcja funkcjonalna*.</span><span class="sxs-lookup"><span data-stu-id="29b08-105">enables another approach that is useful in many scenarios *: functional construction*.</span></span> <span data-ttu-id="29b08-106">Konstrukcja funkcjonalna traktuje modyfikowanie danych jako problem transformacji, a nie jako szczegółowe manipulowanie magazynem danych.</span><span class="sxs-lookup"><span data-stu-id="29b08-106">Functional construction treats modifying data as a problem of transformation, rather than as detailed manipulation of a data store.</span></span> <span data-ttu-id="29b08-107">Jeśli możesz wykonać reprezentację danych i Przekształć ją efektywnie z jednego formularza na inny, wynik jest taki sam jak w przypadku, gdy został przestawiony jeden magazyn danych i manipulowanie nim w jakiś sposób, aby zastosować inny kształt.</span><span class="sxs-lookup"><span data-stu-id="29b08-107">If you can take a representation of data and transform it efficiently from one form to another, the result is the same as if you took one data store and manipulated it in some way to take another shape.</span></span> <span data-ttu-id="29b08-108">Najważniejszym podejściem do konstrukcji funkcjonalnej jest przekazanie wyników zapytań do <xref:System.Xml.Linq.XDocument> i <xref:System.Xml.Linq.XElement> konstruktorów.</span><span class="sxs-lookup"><span data-stu-id="29b08-108">A key to the functional construction approach is to pass the results of queries to <xref:System.Xml.Linq.XDocument> and <xref:System.Xml.Linq.XElement> constructors.</span></span>  
  
 <span data-ttu-id="29b08-109">W wielu przypadkach można napisać przekształcenie kod w ułamku czasu, jaki mógłby wykonać w celu manipulowania magazynem danych, a ten kod jest bardziej niezawodny i łatwiejszy w obsłudze.</span><span class="sxs-lookup"><span data-stu-id="29b08-109">In many cases you can write the transformational code in a fraction of the time that it would take to manipulate the data store, and that code is more robust and easier to maintain.</span></span> <span data-ttu-id="29b08-110">W takich przypadkach, mimo że podejście przekształcenie może mieć większą moc obliczeniową, jest to bardziej efektywny sposób modyfikacji danych.</span><span class="sxs-lookup"><span data-stu-id="29b08-110">In these cases, even though the transformational approach can take more processing power, it is a more effective way to modify data.</span></span> <span data-ttu-id="29b08-111">Jeśli programista zna podejście funkcjonalne, kod wynikający z wielu przypadków jest łatwiejszy do zrozumienia.</span><span class="sxs-lookup"><span data-stu-id="29b08-111">If a developer is familiar with the functional approach, the resulting code in many cases is easier to understand.</span></span> <span data-ttu-id="29b08-112">Można łatwo znaleźć kod modyfikujący poszczególne części drzewa.</span><span class="sxs-lookup"><span data-stu-id="29b08-112">It is easy to find the code that modifies each part of the tree.</span></span>  
  
 <span data-ttu-id="29b08-113">Podejście, w którym modyfikujesz drzewo XML w miejscu, jest bardziej znane dla wielu programistów modelu DOM, natomiast kod zapisany przy użyciu podejścia funkcjonalnego może wyglądać nieznajomo dla deweloperów, który nie rozumie tego podejścia.</span><span class="sxs-lookup"><span data-stu-id="29b08-113">The approach where you modify an XML tree in-place is more familiar to many DOM programmers, whereas code written using the functional approach might look unfamiliar to a developer who doesn't yet understand that approach.</span></span> <span data-ttu-id="29b08-114">Jeśli konieczne jest tylko małe modyfikacje w dużym drzewie XML, podejście, w którym można modyfikować drzewo w wielu przypadkach, zajmie mniej czasu procesora.</span><span class="sxs-lookup"><span data-stu-id="29b08-114">If you have to only make a small modification to a large XML tree, the approach where you modify a tree in place in many cases will take less CPU time.</span></span>  
  
 <span data-ttu-id="29b08-115">Ten temat zawiera przykład, który jest implementowany przy obu podejściach.</span><span class="sxs-lookup"><span data-stu-id="29b08-115">This topic provides an example that is implemented with both approaches.</span></span>  
  
## <a name="transforming-attributes-into-elements"></a><span data-ttu-id="29b08-116">Transformowanie atrybutów do elementów</span><span class="sxs-lookup"><span data-stu-id="29b08-116">Transforming Attributes into Elements</span></span>  
 <span data-ttu-id="29b08-117">Na potrzeby tego przykładu Załóżmy, że chcesz zmodyfikować następujący prosty dokument XML, aby atrybuty staną się elementami.</span><span class="sxs-lookup"><span data-stu-id="29b08-117">For this example, suppose you want to modify the following simple XML document so that the attributes become elements.</span></span> <span data-ttu-id="29b08-118">Ten temat najpierw przedstawia tradycyjne podejście do modyfikacji w miejscu.</span><span class="sxs-lookup"><span data-stu-id="29b08-118">This topic first presents the traditional in-place modification approach.</span></span> <span data-ttu-id="29b08-119">Następnie zostanie wyświetlone podejście konstrukcja funkcjonalna.</span><span class="sxs-lookup"><span data-stu-id="29b08-119">It then shows the functional construction approach.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<Root Data1="123" Data2="456">  
  <Child1>Content</Child1>  
</Root>  
```  
  
### <a name="modifying-the-xml-tree"></a><span data-ttu-id="29b08-120">Modyfikowanie drzewa XML</span><span class="sxs-lookup"><span data-stu-id="29b08-120">Modifying the XML Tree</span></span>  
 <span data-ttu-id="29b08-121">Można napisać kod proceduralny, aby utworzyć elementy z atrybutów, a następnie usunąć atrybuty w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="29b08-121">You can write some procedural code to create elements from the attributes, and then delete the attributes, as follows:</span></span>  
  
```vb  
Dim root As XElement = XElement.Load("Data.xml")  
For Each att As XAttribute In root.Attributes()  
    root.Add(New XElement(att.Name, att.Value))  
Next  
root.Attributes().Remove()  
Console.WriteLine(root)  
```  
  
 <span data-ttu-id="29b08-122">Ten kod generuje następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="29b08-122">This code produces the following output:</span></span>  
  
```xml  
<Root>  
  <Child1>Content</Child1>  
  <Data1>123</Data1>  
  <Data2>456</Data2>  
</Root>  
```  
  
### <a name="functional-construction-approach"></a><span data-ttu-id="29b08-123">Podejście funkcjonalne</span><span class="sxs-lookup"><span data-stu-id="29b08-123">Functional Construction Approach</span></span>  
 <span data-ttu-id="29b08-124">Z kolei podejście funkcjonalne obejmuje kod służący do tworzenia nowego drzewa, wybierania i wybierania elementów i atrybutów z drzewa źródłowego i przekształcania ich zgodnie z potrzebami, gdy są dodawane do nowego drzewa.</span><span class="sxs-lookup"><span data-stu-id="29b08-124">By contrast, a functional approach consists of code to form a new tree, picking and choosing elements and attributes from the source tree, and transforming them as appropriate as they are added to the new tree.</span></span> <span data-ttu-id="29b08-125">Podejście funkcjonalne wygląda następująco:</span><span class="sxs-lookup"><span data-stu-id="29b08-125">The functional approach looks like the following:</span></span>  
  
```vb  
Dim root As XElement = XElement.Load("Data.xml")  
Dim newTree As XElement = _  
    <Root>  
        <%= root.<Child1> %>  
        <%= From att In root.Attributes() _  
            Select New XElement(att.Name, att.Value) %>  
    </Root>  
Console.WriteLine(newTree)  
```  
  
 <span data-ttu-id="29b08-126">Ten przykład wyprowadza ten sam kod XML jako pierwszy przykład.</span><span class="sxs-lookup"><span data-stu-id="29b08-126">This example outputs the same XML as the first example.</span></span> <span data-ttu-id="29b08-127">Należy jednak zauważyć, że w metodzie funkcjonalnej można zobaczyć uzyskaną strukturę nowego kodu XML.</span><span class="sxs-lookup"><span data-stu-id="29b08-127">However, notice that you can actually see the resulting structure of the new XML in the functional approach.</span></span> <span data-ttu-id="29b08-128">Można zobaczyć `Root` , jak utworzyć element, kod, który ściąga `Child1` element z drzewa źródłowego, oraz kod, który przekształca atrybuty z drzewa źródłowego do elementów w nowym drzewie.</span><span class="sxs-lookup"><span data-stu-id="29b08-128">You can see the creation of the `Root` element, the code that pulls the `Child1` element from the source tree, and the code that transforms the attributes from the source tree to elements in the new tree.</span></span>  
  
 <span data-ttu-id="29b08-129">Przykład funkcjonalny w tym przypadku nie jest krótszy niż pierwszy przykład. nie jest to naprawdę prostsze.</span><span class="sxs-lookup"><span data-stu-id="29b08-129">The functional example in this case is not any shorter than the first example, and it is not really any simpler.</span></span> <span data-ttu-id="29b08-130">Jeśli jednak w drzewie XML wprowadzono wiele zmian, podejście niefunkcjonalne stanie się dość skomplikowane i dość obtuse.</span><span class="sxs-lookup"><span data-stu-id="29b08-130">However, if you have many changes to make to an XML tree, the non functional approach will become quite complex and somewhat obtuse.</span></span> <span data-ttu-id="29b08-131">Natomiast w przypadku korzystania z podejścia funkcjonalnego nadal wystarczy utworzyć żądany kod XML, a następnie osadzić zapytania i wyrażenia, aby ściągnąć odpowiednią zawartość.</span><span class="sxs-lookup"><span data-stu-id="29b08-131">In contrast, when using the functional approach, you still just form the desired XML, embedding queries and expressions as appropriate, to pull in the desired content.</span></span> <span data-ttu-id="29b08-132">Podejście funkcjonalne daje kod, który jest łatwiejszy w obsłudze.</span><span class="sxs-lookup"><span data-stu-id="29b08-132">The functional approach yields code that is easier to maintain.</span></span>  
  
 <span data-ttu-id="29b08-133">Należy zauważyć, że w tym przypadku podejście funkcjonalne prawdopodobnie nie będzie działać w sposób niewidoczny, a także podejście do manipulowania drzewem.</span><span class="sxs-lookup"><span data-stu-id="29b08-133">Notice that in this case the functional approach probably would not perform quite as well as the tree manipulation approach.</span></span> <span data-ttu-id="29b08-134">Główny problem polega na tym, że podejście funkcjonalne tworzy więcej obiektów krótkotrwałych.</span><span class="sxs-lookup"><span data-stu-id="29b08-134">The main issue is that the functional approach creates more short lived objects.</span></span> <span data-ttu-id="29b08-135">Jednak kompromis jest skuteczny, jeśli użycie podejścia funkcjonalnego pozwala zwiększyć produktywność programistyczną.</span><span class="sxs-lookup"><span data-stu-id="29b08-135">However, the tradeoff is an effective one if using the functional approach allows for greater programmer productivity.</span></span>  
  
 <span data-ttu-id="29b08-136">Jest to bardzo prosty przykład, ale służy do wyświetlania różnicy między dwoma podejściami.</span><span class="sxs-lookup"><span data-stu-id="29b08-136">This is a very simple example, but it serves to show the difference in philosophy between the two approaches.</span></span> <span data-ttu-id="29b08-137">Podejście funkcjonalne daje większe korzyści produktywności związane z transformą większych dokumentów XML.</span><span class="sxs-lookup"><span data-stu-id="29b08-137">The functional approach yields greater productivity gains for transforming larger XML documents.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="29b08-138">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="29b08-138">See also</span></span>

- [<span data-ttu-id="29b08-139">Modyfikowanie drzew XML (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="29b08-139">Modifying XML Trees (LINQ to XML) (Visual Basic)</span></span>](modifying-xml-trees-linq-to-xml.md)
