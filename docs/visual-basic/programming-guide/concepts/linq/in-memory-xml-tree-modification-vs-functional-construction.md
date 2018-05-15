---
title: Vs modyfikacji drzewa XML w pamięci. Konstrukcja funkcjonalności (LINQ do XML) (Visual Basic)
ms.date: 07/20/2015
ms.assetid: d91c4ebf-6549-43cc-9961-26d4a82f722b
ms.openlocfilehash: 71b8799d4da2f8f4fb10bdec6ca7cfcec76e036a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="in-memory-xml-tree-modification-vs-functional-construction-linq-to-xml-visual-basic"></a><span data-ttu-id="08d1f-102">Vs modyfikacji drzewa XML w pamięci. Konstrukcja funkcjonalności (LINQ do XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="08d1f-102">In-Memory XML Tree Modification vs. Functional Construction (LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="08d1f-103">Modyfikowanie drzewo XML w miejscu jest to tradycyjne podejście, aby zmiana kształtu dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="08d1f-103">Modifying an XML tree in place is a traditional approach to changing the shape of an XML document.</span></span> <span data-ttu-id="08d1f-104">Typowa aplikacja ładuje dokumentu do magazynu danych, takich jak modelu DOM lub [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]; używa interfejsu programowania do wstawiania węzłów, usuń węzły lub zmienić zawartości węzłów; a następnie zapisuje w pliku XML lub przesyła go za pośrednictwem sieci.</span><span class="sxs-lookup"><span data-stu-id="08d1f-104">A typical application loads a document into a data store such as DOM or [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]; uses a programming interface to insert nodes, delete nodes, or change the content of nodes; and then saves the XML to a file or transmits it over a network.</span></span>  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="08d1f-105"> Umożliwia innym rozwiązaniem, które są przydatne w wielu scenariuszach *: budowa funkcjonalności*.</span><span class="sxs-lookup"><span data-stu-id="08d1f-105"> enables another approach that is useful in many scenarios *: functional construction*.</span></span> <span data-ttu-id="08d1f-106">Funkcjonalności konstrukcji modyfikowanie dane są traktowane jako problem transformacji, a nie jako szczegółowe modyfikowanie magazynu danych.</span><span class="sxs-lookup"><span data-stu-id="08d1f-106">Functional construction treats modifying data as a problem of transformation, rather than as detailed manipulation of a data store.</span></span> <span data-ttu-id="08d1f-107">Jeśli możesz pobrać reprezentację dane i przetransformować je wydajnie z jednego formularza do innego, wynik jest taki sam, jakby miał jeden magazyn danych i manipulowanie go w celu podjęcia innego kształtu.</span><span class="sxs-lookup"><span data-stu-id="08d1f-107">If you can take a representation of data and transform it efficiently from one form to another, the result is the same as if you took one data store and manipulated it in some way to take another shape.</span></span> <span data-ttu-id="08d1f-108">Klucz do metody konstruowania funkcjonalności jest do przekazania wyników zapytania, aby <xref:System.Xml.Linq.XDocument> i <xref:System.Xml.Linq.XElement> konstruktorów.</span><span class="sxs-lookup"><span data-stu-id="08d1f-108">A key to the functional construction approach is to pass the results of queries to <xref:System.Xml.Linq.XDocument> and <xref:System.Xml.Linq.XElement> constructors.</span></span>  
  
 <span data-ttu-id="08d1f-109">W wielu przypadkach można napisać transformational kod w ułamku czasu, który zajmie się do manipulowania magazynu danych, a ten kod jest bardziej niezawodny i łatwiejsze w obsłudze.</span><span class="sxs-lookup"><span data-stu-id="08d1f-109">In many cases you can write the transformational code in a fraction of the time that it would take to manipulate the data store, and that code is more robust and easier to maintain.</span></span> <span data-ttu-id="08d1f-110">W takich przypadkach mimo że transformational podejście może zająć więcej mocy obliczeniowej jest bardziej efektywny sposób modyfikowania danych.</span><span class="sxs-lookup"><span data-stu-id="08d1f-110">In these cases, even though the transformational approach can take more processing power, it is a more effective way to modify data.</span></span> <span data-ttu-id="08d1f-111">W przypadku zapoznać się z funkcjonalności podejście dewelopera, wynikowy kod w wielu przypadkach jest łatwiejsze do zrozumienia.</span><span class="sxs-lookup"><span data-stu-id="08d1f-111">If a developer is familiar with the functional approach, the resulting code in many cases is easier to understand.</span></span> <span data-ttu-id="08d1f-112">Jest łatwe do odnalezienia kod, który modyfikuje każdej części drzewa.</span><span class="sxs-lookup"><span data-stu-id="08d1f-112">It is easy to find the code that modifies each part of the tree.</span></span>  
  
 <span data-ttu-id="08d1f-113">Podejście, w którym można zmodyfikować XML drzewa w miejscu jest lepiej znana wielu programistów modelu DOM, podczas gdy kod napisany za pomocą funkcjonalności podejście może wyglądać doświadczenia w pracy dla deweloperów, którzy jeszcze nie rozpoznaje tego podejścia.</span><span class="sxs-lookup"><span data-stu-id="08d1f-113">The approach where you modify an XML tree in-place is more familiar to many DOM programmers, whereas code written using the functional approach might look unfamiliar to a developer who doesn't yet understand that approach.</span></span> <span data-ttu-id="08d1f-114">Jeśli konieczne będzie jedynie wprowadzenie małych modyfikację dużych drzewa XML, podejście, w którym można zmodyfikować w drzewie miejsce w wielu przypadkach będzie zająć mniej czasu Procesora.</span><span class="sxs-lookup"><span data-stu-id="08d1f-114">If you have to only make a small modification to a large XML tree, the approach where you modify a tree in place in many cases will take less CPU time.</span></span>  
  
 <span data-ttu-id="08d1f-115">Ten temat zawiera przykładowy jest realizowana za pomocą obu podejść.</span><span class="sxs-lookup"><span data-stu-id="08d1f-115">This topic provides an example that is implemented with both approaches.</span></span>  
  
## <a name="transforming-attributes-into-elements"></a><span data-ttu-id="08d1f-116">Przekształcanie atrybutów do elementów</span><span class="sxs-lookup"><span data-stu-id="08d1f-116">Transforming Attributes into Elements</span></span>  
 <span data-ttu-id="08d1f-117">Na przykład załóżmy, że chcesz zmodyfikować następujące prostego dokumentu XML, aby atrybuty stają się elementów.</span><span class="sxs-lookup"><span data-stu-id="08d1f-117">For this example, suppose you want to modify the following simple XML document so that the attributes become elements.</span></span> <span data-ttu-id="08d1f-118">W tym temacie przedstawiono najpierw podejście tradycyjnych modyfikacji w miejscu.</span><span class="sxs-lookup"><span data-stu-id="08d1f-118">This topic first presents the traditional in-place modification approach.</span></span> <span data-ttu-id="08d1f-119">Następnie pokaże podejście konstrukcji funkcjonalności.</span><span class="sxs-lookup"><span data-stu-id="08d1f-119">It then shows the functional construction approach.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<Root Data1="123" Data2="456">  
  <Child1>Content</Child1>  
</Root>  
```  
  
### <a name="modifying-the-xml-tree"></a><span data-ttu-id="08d1f-120">Modyfikowanie drzewa XML</span><span class="sxs-lookup"><span data-stu-id="08d1f-120">Modifying the XML Tree</span></span>  
 <span data-ttu-id="08d1f-121">Napisanie kodu procedur tworzenia elementów z atrybutów i Usuń atrybutów, w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="08d1f-121">You can write some procedural code to create elements from the attributes, and then delete the attributes, as follows:</span></span>  
  
```vb  
Dim root As XElement = XElement.Load("Data.xml")  
For Each att As XAttribute In root.Attributes()  
    root.Add(New XElement(att.Name, att.Value))  
Next  
root.Attributes().Remove()  
Console.WriteLine(root)  
```  
  
 <span data-ttu-id="08d1f-122">Ten kod generuje następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="08d1f-122">This code produces the following output:</span></span>  
  
```xml  
<Root>  
  <Child1>Content</Child1>  
  <Data1>123</Data1>  
  <Data2>456</Data2>  
</Root>  
```  
  
### <a name="functional-construction-approach"></a><span data-ttu-id="08d1f-123">Podejście funkcjonalności konstrukcji</span><span class="sxs-lookup"><span data-stu-id="08d1f-123">Functional Construction Approach</span></span>  
 <span data-ttu-id="08d1f-124">Z kolei funkcjonalności podejście składa się z kodu w celu utworzenia nowego drzewa, pobierania i Wybieranie elementów i atrybutów z drzewa źródła i przekształcanie je jako odpowiednie, gdy są one dodawane do nowego drzewa.</span><span class="sxs-lookup"><span data-stu-id="08d1f-124">By contrast, a functional approach consists of code to form a new tree, picking and choosing elements and attributes from the source tree, and transforming them as appropriate as they are added to the new tree.</span></span> <span data-ttu-id="08d1f-125">Podejście funkcjonalności wygląda następująco:</span><span class="sxs-lookup"><span data-stu-id="08d1f-125">The functional approach looks like the following:</span></span>  
  
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
  
 <span data-ttu-id="08d1f-126">W tym przykładzie danych wyjściowych tego samego pliku XML, co w pierwszym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="08d1f-126">This example outputs the same XML as the first example.</span></span> <span data-ttu-id="08d1f-127">Jednak zauważyć faktycznie widać Wynikowa struktura nowy kod XML w ujęciu funkcjonalności.</span><span class="sxs-lookup"><span data-stu-id="08d1f-127">However, notice that you can actually see the resulting structure of the new XML in the functional approach.</span></span> <span data-ttu-id="08d1f-128">Zostanie wyświetlony tworzenie `Root` element, kod, który pobiera `Child1` element z drzewa źródło i kod, który przekształca atrybutów z drzewa źródła do elementów w nowym drzewie.</span><span class="sxs-lookup"><span data-stu-id="08d1f-128">You can see the creation of the `Root` element, the code that pulls the `Child1` element from the source tree, and the code that transforms the attributes from the source tree to elements in the new tree.</span></span>  
  
 <span data-ttu-id="08d1f-129">Przykład funkcjonalności w takim przypadku nie jest żadnym krótszy niż pierwszym przykładzie, a nie jest to naprawdę any prostsze.</span><span class="sxs-lookup"><span data-stu-id="08d1f-129">The functional example in this case is not any shorter than the first example, and it is not really any simpler.</span></span> <span data-ttu-id="08d1f-130">Jednak jeśli masz wiele zmian, aby upewnić się na drzewo XML z systemem innym niż funkcjonalności podejście staną się dość złożone i nieco obtuse.</span><span class="sxs-lookup"><span data-stu-id="08d1f-130">However, if you have many changes to make to an XML tree, the non functional approach will become quite complex and somewhat obtuse.</span></span> <span data-ttu-id="08d1f-131">Z kolei korzystając z funkcjonalności podejście, nadal właśnie formularz żądanego pliku XML osadzanie zapytania i wyrażenia, w celu ściągania w żądanej zawartości.</span><span class="sxs-lookup"><span data-stu-id="08d1f-131">In contrast, when using the functional approach, you still just form the desired XML, embedding queries and expressions as appropriate, to pull in the desired content.</span></span> <span data-ttu-id="08d1f-132">Podejście funkcjonalności implikuje kod, który jest łatwiejsze w obsłudze.</span><span class="sxs-lookup"><span data-stu-id="08d1f-132">The functional approach yields code that is easier to maintain.</span></span>  
  
 <span data-ttu-id="08d1f-133">Należy zauważyć, że w takim przypadku funkcjonalności podejście prawdopodobnie nie przeprowadza się bardzo, a także metoda manipulowania drzewa.</span><span class="sxs-lookup"><span data-stu-id="08d1f-133">Notice that in this case the functional approach probably would not perform quite as well as the tree manipulation approach.</span></span> <span data-ttu-id="08d1f-134">Główny problem jest utworzoną za pomocą funkcjonalności podejście więcej krótkich okresów ważności obiektów.</span><span class="sxs-lookup"><span data-stu-id="08d1f-134">The main issue is that the functional approach creates more short lived objects.</span></span> <span data-ttu-id="08d1f-135">Jednak zależności jest skuteczne Jeśli funkcjonalności podejście pozwala na zwiększenie wydajności programisty.</span><span class="sxs-lookup"><span data-stu-id="08d1f-135">However, the tradeoff is an effective one if using the functional approach allows for greater programmer productivity.</span></span>  
  
 <span data-ttu-id="08d1f-136">To jest bardzo prosty przykład, ale służy do wyświetlenia różnicy w zasady klas dwa podejścia.</span><span class="sxs-lookup"><span data-stu-id="08d1f-136">This is a very simple example, but it serves to show the difference in philosophy between the two approaches.</span></span> <span data-ttu-id="08d1f-137">Podejście funkcjonalności daje większą produktywność do transformacji dokumentów XML większy.</span><span class="sxs-lookup"><span data-stu-id="08d1f-137">The functional approach yields greater productivity gains for transforming larger XML documents.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="08d1f-138">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="08d1f-138">See Also</span></span>  
 [<span data-ttu-id="08d1f-139">Modyfikowanie drzew XML (LINQ do XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="08d1f-139">Modifying XML Trees (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/modifying-xml-trees-linq-to-xml.md)
