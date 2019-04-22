---
title: Konstrukcja funkcjonalna (LINQ to XML) (Visual Basic)
ms.date: 07/20/2015
ms.assetid: feac4273-39ab-43ae-bab7-4059c807a785
ms.openlocfilehash: f677c0d0e204b5d12718701ab70b8a3c1bd3530c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "58816554"
---
# <a name="functional-construction-linq-to-xml-visual-basic"></a><span data-ttu-id="9862d-102">Konstrukcja funkcjonalna (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9862d-102">Functional Construction (LINQ to XML) (Visual Basic)</span></span>
[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <span data-ttu-id="9862d-103">zapewnia zaawansowany sposób tworzyć elementy XML o nazwie *konstrukcja funkcjonalna*.</span><span class="sxs-lookup"><span data-stu-id="9862d-103">provides a powerful way to create XML elements called *functional construction*.</span></span> <span data-ttu-id="9862d-104">Konstrukcja funkcjonalna jest możliwość tworzenia drzewa XML w pojedynczej instrukcji.</span><span class="sxs-lookup"><span data-stu-id="9862d-104">Functional construction is the ability to create an XML tree in a single statement.</span></span>  
  
 <span data-ttu-id="9862d-105">Istnieje kilka kluczowych funkcji [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] interfejs programowania, które umożliwiają konstrukcja funkcjonalna:</span><span class="sxs-lookup"><span data-stu-id="9862d-105">There are several key features of the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] programming interface that enable functional construction:</span></span>  
  
-   <span data-ttu-id="9862d-106"><xref:System.Xml.Linq.XElement> Konstruktor przyjmuje różne typy argumentów dla zawartości.</span><span class="sxs-lookup"><span data-stu-id="9862d-106">The <xref:System.Xml.Linq.XElement> constructor takes various types of arguments for content.</span></span> <span data-ttu-id="9862d-107">Na przykład, można przekazać inny <xref:System.Xml.Linq.XElement> obiektu, który staje się nie zawiera elementu podrzędnego.</span><span class="sxs-lookup"><span data-stu-id="9862d-107">For example, you can pass another <xref:System.Xml.Linq.XElement> object, which becomes a child element.</span></span> <span data-ttu-id="9862d-108">Możesz przekazać <xref:System.Xml.Linq.XAttribute> obiektu, który staje się atrybut elementu.</span><span class="sxs-lookup"><span data-stu-id="9862d-108">You can pass an <xref:System.Xml.Linq.XAttribute> object, which becomes an attribute of the element.</span></span> <span data-ttu-id="9862d-109">Lub możesz przekazać inny rodzaj obiektu, który jest konwertowany na ciąg i staje się zawartością tekstową elementu.</span><span class="sxs-lookup"><span data-stu-id="9862d-109">Or you can pass any other type of object, which is converted to a string and becomes the text content of the element.</span></span>  
  
-   <span data-ttu-id="9862d-110"><xref:System.Xml.Linq.XElement> Konstruktor przyjmuje `params` tablicy typu <xref:System.Object>, dzięki czemu można przekazać dowolną liczbę obiektów do konstruktora.</span><span class="sxs-lookup"><span data-stu-id="9862d-110">The <xref:System.Xml.Linq.XElement> constructor takes a `params` array of type <xref:System.Object>, so that you can pass any number of objects to the constructor.</span></span> <span data-ttu-id="9862d-111">Dzięki temu można utworzyć elementu, który ma zawartość złożoną.</span><span class="sxs-lookup"><span data-stu-id="9862d-111">This enables you to create an element that has complex content.</span></span>  
  
-   <span data-ttu-id="9862d-112">Jeśli obiekt implementuje interfejs <xref:System.Collections.Generic.IEnumerable%601>, są wyliczane kolekcji w obiekcie, a wszystkie elementy w kolekcji są dodawane.</span><span class="sxs-lookup"><span data-stu-id="9862d-112">If an object implements <xref:System.Collections.Generic.IEnumerable%601>, the collection in the object is enumerated, and all items in the collection are added.</span></span> <span data-ttu-id="9862d-113">Jeśli kolekcja zawiera <xref:System.Xml.Linq.XElement> lub <xref:System.Xml.Linq.XAttribute> obiektów, każdy element w kolekcji zostanie dodany osobno.</span><span class="sxs-lookup"><span data-stu-id="9862d-113">If the collection contains <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XAttribute> objects, each item in the collection is added separately.</span></span> <span data-ttu-id="9862d-114">Jest to ważne, ponieważ dzięki temu można przekazać wyników [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] zapytania do konstruktora.</span><span class="sxs-lookup"><span data-stu-id="9862d-114">This is important because it lets you pass the results of a [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query to the constructor.</span></span>  
  
 <span data-ttu-id="9862d-115">Oto przykład:</span><span class="sxs-lookup"><span data-stu-id="9862d-115">The following is an example:</span></span>  
  
 <span data-ttu-id="9862d-116">Te funkcje umożliwiają pisanie kodu przy użyciu literałów XML, tworzenie drzewa XML, a także napisać kod, który używa wyników [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] zapytania podczas tworzenia drzewa XML:</span><span class="sxs-lookup"><span data-stu-id="9862d-116">These features enable you to write code using XML literals to create an XML tree, and also to write code that uses the results of [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] queries when you create an XML tree:</span></span>  
  
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
  
 <span data-ttu-id="9862d-117">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="9862d-117">This example produces the following output:</span></span>  
  
```xml  
<Root>  
  <Child>1</Child>  
  <Child>2</Child>  
  <Element>3</Element>  
  <Element>4</Element>  
  <Element>5</Element>  
</Root>  
```  
  
## <a name="see-also"></a><span data-ttu-id="9862d-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9862d-118">See also</span></span>

- [<span data-ttu-id="9862d-119">Tworzenie drzew XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9862d-119">Creating XML Trees (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/creating-xml-trees.md)
