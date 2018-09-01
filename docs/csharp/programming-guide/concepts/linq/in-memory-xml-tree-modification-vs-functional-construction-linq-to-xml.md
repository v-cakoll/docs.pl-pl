---
title: Modyfikowanie drzewa XML w pamięci programu vs. Konstrukcja funkcjonalna (LINQ to XML) (C#)
ms.date: 07/20/2015
ms.assetid: b5afc31d-a325-4ec6-bf17-0ff90a20ffca
ms.openlocfilehash: 3e6d86ac11f10d7dbb3d270410415fb23acb2e01
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/01/2018
ms.locfileid: "43397802"
---
# <a name="in-memory-xml-tree-modification-vs-functional-construction-linq-to-xml-c"></a><span data-ttu-id="f0b72-102">Modyfikowanie drzewa XML w pamięci programu vs. Konstrukcja funkcjonalna (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="f0b72-102">In-Memory XML Tree Modification vs. Functional Construction (LINQ to XML) (C#)</span></span>
<span data-ttu-id="f0b72-103">Modyfikowanie drzewa XML w miejscu jest tradycyjne podejście na zmieniające się kształt dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="f0b72-103">Modifying an XML tree in place is a traditional approach to changing the shape of an XML document.</span></span> <span data-ttu-id="f0b72-104">Typowa aplikacja ładuje dokumentu do magazynu danych, takich jak modelu DOM lub [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]; używa interfejsu programowania wstawić węzłów, usuń węzły lub zmienić zawartość węzłów; a następnie zapisuje w pliku XML lub przesyła je za pośrednictwem sieci.</span><span class="sxs-lookup"><span data-stu-id="f0b72-104">A typical application loads a document into a data store such as DOM or [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]; uses a programming interface to insert nodes, delete nodes, or change the content of nodes; and then saves the XML to a file or transmits it over a network.</span></span>  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="f0b72-105"> Umożliwia innym rozwiązaniem, które są przydatne w wielu scenariuszach *: konstrukcja funkcjonalna*.</span><span class="sxs-lookup"><span data-stu-id="f0b72-105"> enables another approach that is useful in many scenarios *: functional construction*.</span></span> <span data-ttu-id="f0b72-106">Konstrukcja funkcjonalna modyfikowania dane są traktowane jako problem transformacji, a nie jako szczegółowe manipulowania magazynu danych.</span><span class="sxs-lookup"><span data-stu-id="f0b72-106">Functional construction treats modifying data as a problem of transformation, rather than as detailed manipulation of a data store.</span></span> <span data-ttu-id="f0b72-107">Jeśli możesz wykonać reprezentację danych i przekształcić je wydajnie z jednego formularza do innego, wynik jest taki sam, tak, jakby miały jeden magazyn danych i modyfikować je w jakiś sposób, aby móc innego kształtu.</span><span class="sxs-lookup"><span data-stu-id="f0b72-107">If you can take a representation of data and transform it efficiently from one form to another, the result is the same as if you took one data store and manipulated it in some way to take another shape.</span></span> <span data-ttu-id="f0b72-108">Klucz podejścia konstrukcja funkcjonalna służy do przekazywania wyniki zapytania w celu <xref:System.Xml.Linq.XDocument> i <xref:System.Xml.Linq.XElement> konstruktorów.</span><span class="sxs-lookup"><span data-stu-id="f0b72-108">A key to the functional construction approach is to pass the results of queries to <xref:System.Xml.Linq.XDocument> and <xref:System.Xml.Linq.XElement> constructors.</span></span>  
  
 <span data-ttu-id="f0b72-109">W wielu przypadkach można napisać kod innowacyjne w zaledwie ułamku czasu, który zajmie się do manipulowania magazynu danych, a ten kod jest bardziej niezawodne i łatwiejsze w utrzymaniu.</span><span class="sxs-lookup"><span data-stu-id="f0b72-109">In many cases you can write the transformational code in a fraction of the time that it would take to manipulate the data store, and that code is more robust and easier to maintain.</span></span> <span data-ttu-id="f0b72-110">W takich przypadkach pomimo innowacyjne podejście może zająć więcej mocy obliczeniowej, jest bardziej efektywny sposób modyfikowania danych.</span><span class="sxs-lookup"><span data-stu-id="f0b72-110">In these cases, even though the transformational approach can take more processing power, it is a more effective way to modify data.</span></span> <span data-ttu-id="f0b72-111">Jeśli deweloper jest dobrze znanych funkcjonalności podejście, wynikowy kod w wielu przypadkach jest łatwiejsze do zrozumienia.</span><span class="sxs-lookup"><span data-stu-id="f0b72-111">If a developer is familiar with the functional approach, the resulting code in many cases is easier to understand.</span></span> <span data-ttu-id="f0b72-112">Jest to łatwe do znalezienia kod, który modyfikuje każdej części drzewa.</span><span class="sxs-lookup"><span data-stu-id="f0b72-112">It is easy to find the code that modifies each part of the tree.</span></span>  
  
 <span data-ttu-id="f0b72-113">Podejścia, w którym można zmodyfikować XML drzewa w miejscu jest bardziej znane dużą liczbą programistów modelu DOM, natomiast kod napisany za pomocą funkcjonalne podejście może być nieznane dla deweloperów, którzy jeszcze nie rozpoznaje tego podejścia.</span><span class="sxs-lookup"><span data-stu-id="f0b72-113">The approach where you modify an XML tree in-place is more familiar to many DOM programmers, whereas code written using the functional approach might look unfamiliar to a developer who doesn't yet understand that approach.</span></span> <span data-ttu-id="f0b72-114">Jeśli konieczne będzie jedynie wprowadzenie niewielkiej modyfikacji do dużych drzewa XML, podejście, gdzie można modyfikować drzewa w miejscu, w wielu przypadkach zajmie mniej czasu procesora CPU.</span><span class="sxs-lookup"><span data-stu-id="f0b72-114">If you have to only make a small modification to a large XML tree, the approach where you modify a tree in place in many cases will take less CPU time.</span></span>  
  
 <span data-ttu-id="f0b72-115">Ten temat zawiera przykład, który jest implementowane za pomocą obu metod.</span><span class="sxs-lookup"><span data-stu-id="f0b72-115">This topic provides an example that is implemented with both approaches.</span></span>  
  
## <a name="transforming-attributes-into-elements"></a><span data-ttu-id="f0b72-116">Przekształcanie atrybutów do elementów</span><span class="sxs-lookup"><span data-stu-id="f0b72-116">Transforming Attributes into Elements</span></span>  
 <span data-ttu-id="f0b72-117">Na przykład załóżmy, że chcesz zmodyfikować prostego następujący dokument XML, dzięki czemu atrybuty stają się elementy.</span><span class="sxs-lookup"><span data-stu-id="f0b72-117">For this example, suppose you want to modify the following simple XML document so that the attributes become elements.</span></span> <span data-ttu-id="f0b72-118">W tym temacie przedstawiono pierwsze podejście tradycyjnych modyfikacji w miejscu.</span><span class="sxs-lookup"><span data-stu-id="f0b72-118">This topic first presents the traditional in-place modification approach.</span></span> <span data-ttu-id="f0b72-119">Następnie prezentuje podejście konstrukcja funkcjonalna.</span><span class="sxs-lookup"><span data-stu-id="f0b72-119">It then shows the functional construction approach.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<Root Data1="123" Data2="456">  
  <Child1>Content</Child1>  
</Root>  
```  
  
### <a name="modifying-the-xml-tree"></a><span data-ttu-id="f0b72-120">Modyfikowanie drzewa XML</span><span class="sxs-lookup"><span data-stu-id="f0b72-120">Modifying the XML Tree</span></span>  
 <span data-ttu-id="f0b72-121">Napisanie kodu procedur do tworzenia elementów z atrybutów i następnie usuwanie atrybutów, w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="f0b72-121">You can write some procedural code to create elements from the attributes, and then delete the attributes, as follows:</span></span>  
  
```csharp  
XElement root = XElement.Load("Data.xml");  
foreach (XAttribute att in root.Attributes()) {  
    root.Add(new XElement(att.Name, (string)att));  
}  
root.Attributes().Remove();  
Console.WriteLine(root);  
```  
  
 <span data-ttu-id="f0b72-122">Ten kod generuje następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="f0b72-122">This code produces the following output:</span></span>  
  
```xml  
<Root>  
  <Child1>Content</Child1>  
  <Data1>123</Data1>  
  <Data2>456</Data2>  
</Root>  
```  
  
### <a name="functional-construction-approach"></a><span data-ttu-id="f0b72-123">Konstrukcja funkcjonalna podejście</span><span class="sxs-lookup"><span data-stu-id="f0b72-123">Functional Construction Approach</span></span>  
 <span data-ttu-id="f0b72-124">Z drugiej strony funkcjonalne podejście składa się z kodu w celu utworzenia nowego drzewa, pobierania i wybierania elementów i atrybutów w drzewie źródła i przekształcanie ich odpowiednie zostaną one dodane do nowego drzewa.</span><span class="sxs-lookup"><span data-stu-id="f0b72-124">By contrast, a functional approach consists of code to form a new tree, picking and choosing elements and attributes from the source tree, and transforming them as appropriate as they are added to the new tree.</span></span> <span data-ttu-id="f0b72-125">Funkcjonalne podejście wygląda podobnie do poniższego:</span><span class="sxs-lookup"><span data-stu-id="f0b72-125">The functional approach looks like the following:</span></span>  
  
```csharp  
XElement root = XElement.Load("Data.xml");  
XElement newTree = new XElement("Root",  
    root.Element("Child1"),  
    from att in root.Attributes()  
    select new XElement(att.Name, (string)att)  
);  
Console.WriteLine(newTree);  
```  
  
 <span data-ttu-id="f0b72-126">W tym przykładzie generuje ten sam kod XML jako pierwszy przykład.</span><span class="sxs-lookup"><span data-stu-id="f0b72-126">This example outputs the same XML as the first example.</span></span> <span data-ttu-id="f0b72-127">Jednak należy zauważyć, może faktycznie zobaczysz Wynikowa struktura nowym XML w ujęciu funkcjonalności.</span><span class="sxs-lookup"><span data-stu-id="f0b72-127">However, notice that you can actually see the resulting structure of the new XML in the functional approach.</span></span> <span data-ttu-id="f0b72-128">Możesz zobaczyć tworzenie `Root` element, kod, który ściąga `Child1` elementu w drzewie źródła i kod, który przekształca atrybuty z drzewa źródłowego do elementów w nowym drzewie.</span><span class="sxs-lookup"><span data-stu-id="f0b72-128">You can see the creation of the `Root` element, the code that pulls the `Child1` element from the source tree, and the code that transforms the attributes from the source tree to elements in the new tree.</span></span>  
  
 <span data-ttu-id="f0b72-129">Przykład funkcjonalności w tym przypadku nie jest żadnym krótszy niż pierwszy przykład i nie jest tak naprawdę wszelkie prostsze.</span><span class="sxs-lookup"><span data-stu-id="f0b72-129">The functional example in this case is not any shorter than the first example, and it is not really any simpler.</span></span> <span data-ttu-id="f0b72-130">Jednak w przypadku wielu zmiany do drzewa XML bez funkcjonalne podejście staną się dość skomplikowane i nieco obtuse.</span><span class="sxs-lookup"><span data-stu-id="f0b72-130">However, if you have many changes to make to an XML tree, the non functional approach will become quite complex and somewhat obtuse.</span></span> <span data-ttu-id="f0b72-131">Korzystając z podejścia funkcjonalności, natomiast nadal formularza po prostu żądanego pliku XML osadzania zapytań i wyrażeń, zgodnie z potrzebami pobrać żądaną zawartość.</span><span class="sxs-lookup"><span data-stu-id="f0b72-131">In contrast, when using the functional approach, you still just form the desired XML, embedding queries and expressions as appropriate, to pull in the desired content.</span></span> <span data-ttu-id="f0b72-132">Funkcjonalne podejście dwuoddziałowe zapewnia kod, który jest łatwiejszy w utrzymaniu.</span><span class="sxs-lookup"><span data-stu-id="f0b72-132">The functional approach yields code that is easier to maintain.</span></span>  
  
 <span data-ttu-id="f0b72-133">Należy zauważyć, że w tym przypadku funkcjonalne podejście prawdopodobnie nie wykona dość oraz podejście manipulowania drzewa.</span><span class="sxs-lookup"><span data-stu-id="f0b72-133">Notice that in this case the functional approach probably would not perform quite as well as the tree manipulation approach.</span></span> <span data-ttu-id="f0b72-134">Główny problem polega na tym, że funkcjonalne podejście tworzy więcej krótki czas życia obiektów.</span><span class="sxs-lookup"><span data-stu-id="f0b72-134">The main issue is that the functional approach creates more short lived objects.</span></span> <span data-ttu-id="f0b72-135">Jednak kosztem jest skuteczne Jeśli funkcjonalne podejście pozwala uzyskać większą wydajność pracy programisty.</span><span class="sxs-lookup"><span data-stu-id="f0b72-135">However, the tradeoff is an effective one if using the functional approach allows for greater programmer productivity.</span></span>  
  
 <span data-ttu-id="f0b72-136">Jest to bardzo prosty przykład, ale służy do pokazania różnicy w filozofia dwa podejścia.</span><span class="sxs-lookup"><span data-stu-id="f0b72-136">This is a very simple example, but it serves to show the difference in philosophy between the two approaches.</span></span> <span data-ttu-id="f0b72-137">Funkcjonalne podejście dwuoddziałowe zapewnia większą produktywność w przypadku transformacji dokumentów XML większe.</span><span class="sxs-lookup"><span data-stu-id="f0b72-137">The functional approach yields greater productivity gains for transforming larger XML documents.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f0b72-138">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f0b72-138">See Also</span></span>  
 [<span data-ttu-id="f0b72-139">Modyfikowanie drzew XML (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="f0b72-139">Modifying XML Trees (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/modifying-xml-trees-linq-to-xml.md)
