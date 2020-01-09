---
title: Konstrukcja funkcjonalna (LINQ to XML)
ms.date: 07/20/2015
ms.assetid: feac4273-39ab-43ae-bab7-4059c807a785
ms.openlocfilehash: a51360d6c8d44770c462afb728a1fb78d3e2cd42
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/03/2020
ms.locfileid: "75636851"
---
# <a name="functional-construction-linq-to-xml-visual-basic"></a><span data-ttu-id="77e04-102">Konstrukcja funkcjonalna (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="77e04-102">Functional Construction (LINQ to XML) (Visual Basic)</span></span>
[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <span data-ttu-id="77e04-103">zapewnia zaawansowany sposób tworzenia elementów XML o nazwie *konstrukcja funkcjonalna*.</span><span class="sxs-lookup"><span data-stu-id="77e04-103">provides a powerful way to create XML elements called *functional construction*.</span></span> <span data-ttu-id="77e04-104">Konstrukcja funkcjonalna to możliwość tworzenia drzewa XML w pojedynczej instrukcji.</span><span class="sxs-lookup"><span data-stu-id="77e04-104">Functional construction is the ability to create an XML tree in a single statement.</span></span>  
  
 <span data-ttu-id="77e04-105">Istnieje kilka najważniejszych funkcji interfejsu programowania [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], które umożliwiają konstruowanie funkcjonalne:</span><span class="sxs-lookup"><span data-stu-id="77e04-105">There are several key features of the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] programming interface that enable functional construction:</span></span>  
  
- <span data-ttu-id="77e04-106">Konstruktor <xref:System.Xml.Linq.XElement> ma różne typy argumentów dla zawartości.</span><span class="sxs-lookup"><span data-stu-id="77e04-106">The <xref:System.Xml.Linq.XElement> constructor takes various types of arguments for content.</span></span> <span data-ttu-id="77e04-107">Na przykład można przekazać inny obiekt <xref:System.Xml.Linq.XElement>, który stanie się elementem podrzędnym.</span><span class="sxs-lookup"><span data-stu-id="77e04-107">For example, you can pass another <xref:System.Xml.Linq.XElement> object, which becomes a child element.</span></span> <span data-ttu-id="77e04-108">Można przekazać obiekt <xref:System.Xml.Linq.XAttribute>, który stanie się atrybutem elementu.</span><span class="sxs-lookup"><span data-stu-id="77e04-108">You can pass an <xref:System.Xml.Linq.XAttribute> object, which becomes an attribute of the element.</span></span> <span data-ttu-id="77e04-109">Lub można przekazać każdy inny typ obiektu, który jest konwertowany na ciąg i stanie się zawartością tekstową elementu.</span><span class="sxs-lookup"><span data-stu-id="77e04-109">Or you can pass any other type of object, which is converted to a string and becomes the text content of the element.</span></span>  
  
- <span data-ttu-id="77e04-110">Konstruktor <xref:System.Xml.Linq.XElement> pobiera tablicę `params` typu <xref:System.Object>, dzięki czemu można przekazać dowolną liczbę obiektów do konstruktora.</span><span class="sxs-lookup"><span data-stu-id="77e04-110">The <xref:System.Xml.Linq.XElement> constructor takes a `params` array of type <xref:System.Object>, so that you can pass any number of objects to the constructor.</span></span> <span data-ttu-id="77e04-111">Dzięki temu można utworzyć element, który ma złożoną zawartość.</span><span class="sxs-lookup"><span data-stu-id="77e04-111">This enables you to create an element that has complex content.</span></span>  
  
- <span data-ttu-id="77e04-112">Jeśli obiekt implementuje <xref:System.Collections.Generic.IEnumerable%601>, kolekcja w obiekcie zostanie wyliczona i wszystkie elementy w kolekcji zostaną dodane.</span><span class="sxs-lookup"><span data-stu-id="77e04-112">If an object implements <xref:System.Collections.Generic.IEnumerable%601>, the collection in the object is enumerated, and all items in the collection are added.</span></span> <span data-ttu-id="77e04-113">Jeśli kolekcja zawiera obiekty <xref:System.Xml.Linq.XElement> lub <xref:System.Xml.Linq.XAttribute>, każdy element w kolekcji zostanie dodany osobno.</span><span class="sxs-lookup"><span data-stu-id="77e04-113">If the collection contains <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XAttribute> objects, each item in the collection is added separately.</span></span> <span data-ttu-id="77e04-114">Jest to ważne, ponieważ umożliwia przekazywanie wyników zapytania LINQ do konstruktora.</span><span class="sxs-lookup"><span data-stu-id="77e04-114">This is important because it lets you pass the results of a LINQ query to the constructor.</span></span>  
  
 <span data-ttu-id="77e04-115">Poniżej przedstawiono przykład:</span><span class="sxs-lookup"><span data-stu-id="77e04-115">The following is an example:</span></span>  
  
 <span data-ttu-id="77e04-116">Te funkcje umożliwiają pisanie kodu przy użyciu literałów XML w celu utworzenia drzewa XML, a także do pisania kodu, który używa wyników zapytań LINQ podczas tworzenia drzewa XML:</span><span class="sxs-lookup"><span data-stu-id="77e04-116">These features enable you to write code using XML literals to create an XML tree, and also to write code that uses the results of LINQ queries when you create an XML tree:</span></span>  
  
```vb  
Dim srcTree As XElement = _  
    <Root>  
        <Element>1</Element>  
        <Element>2</Element>  
        <Element>3</Element>  
        <Element>4</Element>  
        <Element>5</Element>  
    </Root>  
Dim xmlTree As XElement = _  
    <Root>  
        <Child>1</Child>  
        <Child>2</Child>  
        <%= From el In srcTree.Elements() _  
            Where CInt(el) > 2 _  
            Select el %>  
    </Root>  
Console.WriteLine(xmlTree)  
```  
  
 <span data-ttu-id="77e04-117">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="77e04-117">This example produces the following output:</span></span>  
  
```xml  
<Root>  
  <Child>1</Child>  
  <Child>2</Child>  
  <Element>3</Element>  
  <Element>4</Element>  
  <Element>5</Element>  
</Root>  
```  
  
## <a name="see-also"></a><span data-ttu-id="77e04-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="77e04-118">See also</span></span>

- [<span data-ttu-id="77e04-119">Tworzenie drzew XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="77e04-119">Creating XML Trees (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/creating-xml-trees.md)
