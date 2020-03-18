---
title: Modyfikacja drzewa XML w pamięci a konstrukcja funkcjonalna (LINQ do XML) (C#)
ms.date: 07/20/2015
ms.assetid: b5afc31d-a325-4ec6-bf17-0ff90a20ffca
ms.openlocfilehash: 55eb95585bdd5d2c52175cacae2e6d049bd06f69
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "66484556"
---
# <a name="in-memory-xml-tree-modification-vs-functional-construction-linq-to-xml-c"></a><span data-ttu-id="89247-102">Modyfikacja drzewa XML w pamięci a konstrukcja funkcjonalna (LINQ do XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="89247-102">In-Memory XML Tree Modification vs. Functional Construction (LINQ to XML) (C#)</span></span>
<span data-ttu-id="89247-103">Modyfikowanie drzewa XML w miejscu jest tradycyjnym podejściem do zmiany kształtu dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="89247-103">Modifying an XML tree in place is a traditional approach to changing the shape of an XML document.</span></span> <span data-ttu-id="89247-104">Typowa aplikacja ładuje dokument do magazynu [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]danych, takiego jak DOM lub ; używa interfejsu programowania do wstawiania węzłów, usuwania węzłów lub zmiany zawartości węzłów; a następnie zapisuje kod XML w pliku lub przesyła go przez sieć.</span><span class="sxs-lookup"><span data-stu-id="89247-104">A typical application loads a document into a data store such as DOM or [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]; uses a programming interface to insert nodes, delete nodes, or change the content of nodes; and then saves the XML to a file or transmits it over a network.</span></span>  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="89247-105">umożliwia inne podejście, które jest przydatne w wielu scenariuszach: *konstrukcja funkcjonalna*.</span><span class="sxs-lookup"><span data-stu-id="89247-105">enables another approach that is useful in many scenarios: *functional construction*.</span></span> <span data-ttu-id="89247-106">Funkcjonalna konstrukcja traktuje modyfikowanie danych jako problem transformacji, a nie jako szczegółową manipulację magazynem danych.</span><span class="sxs-lookup"><span data-stu-id="89247-106">Functional construction treats modifying data as a problem of transformation, rather than as detailed manipulation of a data store.</span></span> <span data-ttu-id="89247-107">Jeśli można wziąć reprezentację danych i przekształcić je wydajnie z jednego formularza do drugiego, wynik jest taki sam, jak w przypadku, gdy byś wziął jeden magazyn danych i manipulował nim w jakiś sposób, aby nabrać innego kształtu.</span><span class="sxs-lookup"><span data-stu-id="89247-107">If you can take a representation of data and transform it efficiently from one form to another, the result is the same as if you took one data store and manipulated it in some way to take another shape.</span></span> <span data-ttu-id="89247-108">Kluczem do podejścia konstrukcji funkcjonalnych jest przekazywanie <xref:System.Xml.Linq.XDocument> <xref:System.Xml.Linq.XElement> wyników zapytań do i konstruktorów.</span><span class="sxs-lookup"><span data-stu-id="89247-108">A key to the functional construction approach is to pass the results of queries to <xref:System.Xml.Linq.XDocument> and <xref:System.Xml.Linq.XElement> constructors.</span></span>  
  
 <span data-ttu-id="89247-109">W wielu przypadkach można napisać kod transformacji w ułamku czasu, który zajmie manipulowanie magazyn danych, a ten kod jest bardziej niezawodne i łatwiejsze w utrzymaniu.</span><span class="sxs-lookup"><span data-stu-id="89247-109">In many cases you can write the transformational code in a fraction of the time that it would take to manipulate the data store, and that code is more robust and easier to maintain.</span></span> <span data-ttu-id="89247-110">W takich przypadkach, mimo że podejście transformacyjne może zająć więcej mocy obliczeniowej, jest to bardziej skuteczny sposób modyfikowania danych.</span><span class="sxs-lookup"><span data-stu-id="89247-110">In these cases, even though the transformational approach can take more processing power, it is a more effective way to modify data.</span></span> <span data-ttu-id="89247-111">Jeśli deweloper jest zaznajomiony z podejściem funkcjonalnym, wynikowy kod w wielu przypadkach jest łatwiejsze do zrozumienia.</span><span class="sxs-lookup"><span data-stu-id="89247-111">If a developer is familiar with the functional approach, the resulting code in many cases is easier to understand.</span></span> <span data-ttu-id="89247-112">Łatwo jest znaleźć kod, który modyfikuje każdą część drzewa.</span><span class="sxs-lookup"><span data-stu-id="89247-112">It is easy to find the code that modifies each part of the tree.</span></span>  
  
 <span data-ttu-id="89247-113">Podejście, w którym można zmodyfikować drzewo XML w miejscu jest bardziej znane wielu programistów DOM, podczas gdy kod napisany przy użyciu podejścia funkcjonalnego może wyglądać nieznane deweloperowi, który jeszcze nie rozumie tego podejścia.</span><span class="sxs-lookup"><span data-stu-id="89247-113">The approach where you modify an XML tree in-place is more familiar to many DOM programmers, whereas code written using the functional approach might look unfamiliar to a developer who doesn't yet understand that approach.</span></span> <span data-ttu-id="89247-114">Jeśli trzeba tylko dokonać małej modyfikacji do dużego drzewa XML, podejście, w którym można zmodyfikować drzewo w miejscu w wielu przypadkach zajmie mniej czasu procesora CPU.</span><span class="sxs-lookup"><span data-stu-id="89247-114">If you have to only make a small modification to a large XML tree, the approach where you modify a tree in place in many cases will take less CPU time.</span></span>  
  
 <span data-ttu-id="89247-115">W tym temacie przedstawiono przykład, który jest implementowany z obu podejść.</span><span class="sxs-lookup"><span data-stu-id="89247-115">This topic provides an example that is implemented with both approaches.</span></span>  
  
## <a name="transforming-attributes-into-elements"></a><span data-ttu-id="89247-116">Przekształcanie atrybutów w elementy</span><span class="sxs-lookup"><span data-stu-id="89247-116">Transforming Attributes into Elements</span></span>  
 <span data-ttu-id="89247-117">W tym przykładzie załóżmy, że chcesz zmodyfikować następujący prosty dokument XML, aby atrybuty stały się elementami.</span><span class="sxs-lookup"><span data-stu-id="89247-117">For this example, suppose you want to modify the following simple XML document so that the attributes become elements.</span></span> <span data-ttu-id="89247-118">W tym temacie najpierw przedstawiono tradycyjne podejście modyfikacji w miejscu.</span><span class="sxs-lookup"><span data-stu-id="89247-118">This topic first presents the traditional in-place modification approach.</span></span> <span data-ttu-id="89247-119">Następnie pokazuje funkcjonalne podejście budowlane.</span><span class="sxs-lookup"><span data-stu-id="89247-119">It then shows the functional construction approach.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<Root Data1="123" Data2="456">  
  <Child1>Content</Child1>  
</Root>  
```  
  
### <a name="modifying-the-xml-tree"></a><span data-ttu-id="89247-120">Modyfikowanie drzewa XML</span><span class="sxs-lookup"><span data-stu-id="89247-120">Modifying the XML Tree</span></span>  
 <span data-ttu-id="89247-121">Można napisać kod proceduralny, aby utworzyć elementy z atrybutów, a następnie usunąć atrybuty, w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="89247-121">You can write some procedural code to create elements from the attributes, and then delete the attributes, as follows:</span></span>  
  
```csharp  
XElement root = XElement.Load("Data.xml");  
foreach (XAttribute att in root.Attributes()) {  
    root.Add(new XElement(att.Name, (string)att));  
}  
root.Attributes().Remove();  
Console.WriteLine(root);  
```  
  
 <span data-ttu-id="89247-122">Ten kod generuje następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="89247-122">This code produces the following output:</span></span>  
  
```xml  
<Root>  
  <Child1>Content</Child1>  
  <Data1>123</Data1>  
  <Data2>456</Data2>  
</Root>  
```  
  
### <a name="functional-construction-approach"></a><span data-ttu-id="89247-123">Funkcjonalne podejście budowlane</span><span class="sxs-lookup"><span data-stu-id="89247-123">Functional Construction Approach</span></span>  
 <span data-ttu-id="89247-124">Natomiast podejście funkcjonalne składa się z kodu do tworzenia nowego drzewa, zbieranie i wybieranie elementów i atrybutów z drzewa źródłowego i przekształcanie ich odpowiednio, ponieważ są one dodawane do nowego drzewa.</span><span class="sxs-lookup"><span data-stu-id="89247-124">By contrast, a functional approach consists of code to form a new tree, picking and choosing elements and attributes from the source tree, and transforming them as appropriate as they are added to the new tree.</span></span> <span data-ttu-id="89247-125">Podejście funkcjonalne wygląda następująco:</span><span class="sxs-lookup"><span data-stu-id="89247-125">The functional approach looks like the following:</span></span>  
  
```csharp  
XElement root = XElement.Load("Data.xml");  
XElement newTree = new XElement("Root",  
    root.Element("Child1"),  
    from att in root.Attributes()  
    select new XElement(att.Name, (string)att)  
);  
Console.WriteLine(newTree);  
```  
  
 <span data-ttu-id="89247-126">W tym przykładzie wyprowadza ten sam kod XML, co pierwszy przykład.</span><span class="sxs-lookup"><span data-stu-id="89247-126">This example outputs the same XML as the first example.</span></span> <span data-ttu-id="89247-127">Należy jednak zauważyć, że faktycznie można zobaczyć wynikową strukturę nowego kodu XML w podejściu funkcjonalnym.</span><span class="sxs-lookup"><span data-stu-id="89247-127">However, notice that you can actually see the resulting structure of the new XML in the functional approach.</span></span> <span data-ttu-id="89247-128">Możesz zobaczyć tworzenie `Root` elementu, kod, który pobiera `Child1` element z drzewa źródłowego i kod, który przekształca atrybuty z drzewa źródłowego do elementów w nowym drzewie.</span><span class="sxs-lookup"><span data-stu-id="89247-128">You can see the creation of the `Root` element, the code that pulls the `Child1` element from the source tree, and the code that transforms the attributes from the source tree to elements in the new tree.</span></span>  
  
 <span data-ttu-id="89247-129">Funkcjonalny przykład w tym przypadku nie jest krótszy niż w pierwszym przykładzie i tak naprawdę nie jest prostszy.</span><span class="sxs-lookup"><span data-stu-id="89247-129">The functional example in this case is not any shorter than the first example, and it is not really any simpler.</span></span> <span data-ttu-id="89247-130">Jeśli jednak masz wiele zmian do drzewa XML, niefunkcjonalne podejście stanie się dość skomplikowane i nieco rozwlekłe.</span><span class="sxs-lookup"><span data-stu-id="89247-130">However, if you have many changes to make to an XML tree, the non functional approach will become quite complex and somewhat obtuse.</span></span> <span data-ttu-id="89247-131">Z drugiej strony, korzystając z podejścia funkcjonalnego, nadal po prostu tworzą żądane XML, osadzanie zapytań i wyrażeń, w stosownych przypadkach, aby wyciągnąć żądaną zawartość.</span><span class="sxs-lookup"><span data-stu-id="89247-131">In contrast, when using the functional approach, you still just form the desired XML, embedding queries and expressions as appropriate, to pull in the desired content.</span></span> <span data-ttu-id="89247-132">Podejście funkcjonalne daje kod, który jest łatwiejszy w utrzymaniu.</span><span class="sxs-lookup"><span data-stu-id="89247-132">The functional approach yields code that is easier to maintain.</span></span>  
  
 <span data-ttu-id="89247-133">Należy zauważyć, że w tym przypadku podejście funkcjonalne prawdopodobnie nie będzie działać tak dobrze, jak podejście manipulacji drzewa.</span><span class="sxs-lookup"><span data-stu-id="89247-133">Notice that in this case the functional approach probably would not perform quite as well as the tree manipulation approach.</span></span> <span data-ttu-id="89247-134">Głównym problemem jest to, że podejście funkcjonalne tworzy bardziej krótkotrwałe obiekty.</span><span class="sxs-lookup"><span data-stu-id="89247-134">The main issue is that the functional approach creates more short lived objects.</span></span> <span data-ttu-id="89247-135">Jednak kompromis jest skuteczny, jeśli zastosowanie podejścia funkcjonalnego pozwala na większą wydajność programisty.</span><span class="sxs-lookup"><span data-stu-id="89247-135">However, the tradeoff is an effective one if using the functional approach allows for greater programmer productivity.</span></span>  
  
 <span data-ttu-id="89247-136">Jest to bardzo prosty przykład, ale służy do pokazania różnicy w filozofii między tymi dwoma podejściami.</span><span class="sxs-lookup"><span data-stu-id="89247-136">This is a very simple example, but it serves to show the difference in philosophy between the two approaches.</span></span> <span data-ttu-id="89247-137">Podejście funkcjonalne zapewnia większy wzrost wydajności w przypadku przekształcania większych dokumentów XML.</span><span class="sxs-lookup"><span data-stu-id="89247-137">The functional approach yields greater productivity gains for transforming larger XML documents.</span></span>  
  