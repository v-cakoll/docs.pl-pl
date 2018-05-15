---
title: Konstrukcja funkcjonalności (LINQ do XML) (Visual Basic)
ms.date: 07/20/2015
ms.assetid: feac4273-39ab-43ae-bab7-4059c807a785
ms.openlocfilehash: 360c321f993c8adb17767987060a0edcccad082a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="functional-construction-linq-to-xml-visual-basic"></a><span data-ttu-id="649a2-102">Konstrukcja funkcjonalności (LINQ do XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="649a2-102">Functional Construction (LINQ to XML) (Visual Basic)</span></span>
[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="649a2-103"> udostępnia zaawansowane metody do tworzenia elementów XML o nazwie *funkcjonalności konstrukcji*.</span><span class="sxs-lookup"><span data-stu-id="649a2-103"> provides a powerful way to create XML elements called *functional construction*.</span></span> <span data-ttu-id="649a2-104">Konstrukcja funkcjonalności jest możliwość tworzenia drzewo XML w jednej instrukcji.</span><span class="sxs-lookup"><span data-stu-id="649a2-104">Functional construction is the ability to create an XML tree in a single statement.</span></span>  
  
 <span data-ttu-id="649a2-105">Istnieje kilka kluczowych funkcji [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] interfejsu programowania, umożliwiające konstrukcji funkcjonalności:</span><span class="sxs-lookup"><span data-stu-id="649a2-105">There are several key features of the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] programming interface that enable functional construction:</span></span>  
  
-   <span data-ttu-id="649a2-106"><xref:System.Xml.Linq.XElement> Konstruktor ma różne typy argumentów dla zawartości.</span><span class="sxs-lookup"><span data-stu-id="649a2-106">The <xref:System.Xml.Linq.XElement> constructor takes various types of arguments for content.</span></span> <span data-ttu-id="649a2-107">Na przykład można przekazać inny <xref:System.Xml.Linq.XElement> obiektu, który staje się elementu podrzędnego.</span><span class="sxs-lookup"><span data-stu-id="649a2-107">For example, you can pass another <xref:System.Xml.Linq.XElement> object, which becomes a child element.</span></span> <span data-ttu-id="649a2-108">Można przekazać <xref:System.Xml.Linq.XAttribute> obiektu, który staje się atrybutem elementu.</span><span class="sxs-lookup"><span data-stu-id="649a2-108">You can pass an <xref:System.Xml.Linq.XAttribute> object, which becomes an attribute of the element.</span></span> <span data-ttu-id="649a2-109">Lub może przekazać inny rodzaj obiektu, który jest konwertowana na ciąg i staje się zawartości tekstowej elementu.</span><span class="sxs-lookup"><span data-stu-id="649a2-109">Or you can pass any other type of object, which is converted to a string and becomes the text content of the element.</span></span>  
  
-   <span data-ttu-id="649a2-110"><xref:System.Xml.Linq.XElement> Konstruktor pobiera `params` tablicy typu <xref:System.Object>, dzięki czemu można przekazać dowolną liczbę obiektów do konstruktora.</span><span class="sxs-lookup"><span data-stu-id="649a2-110">The <xref:System.Xml.Linq.XElement> constructor takes a `params` array of type <xref:System.Object>, so that you can pass any number of objects to the constructor.</span></span> <span data-ttu-id="649a2-111">Dzięki temu można utworzyć element, który ma zawartość złożoną.</span><span class="sxs-lookup"><span data-stu-id="649a2-111">This enables you to create an element that has complex content.</span></span>  
  
-   <span data-ttu-id="649a2-112">Jeśli obiekt implementuje <xref:System.Collections.Generic.IEnumerable%601>wyliczeniu kolekcji w obiekcie i zostaną dodane wszystkie elementy w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="649a2-112">If an object implements <xref:System.Collections.Generic.IEnumerable%601>, the collection in the object is enumerated, and all items in the collection are added.</span></span> <span data-ttu-id="649a2-113">Jeśli kolekcja zawiera <xref:System.Xml.Linq.XElement> lub <xref:System.Xml.Linq.XAttribute> obiekty oddzielnie dodaniu każdego elementu w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="649a2-113">If the collection contains <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XAttribute> objects, each item in the collection is added separately.</span></span> <span data-ttu-id="649a2-114">Jest to ważne, ponieważ dzięki temu można przekazać wyników [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] zapytania do konstruktora.</span><span class="sxs-lookup"><span data-stu-id="649a2-114">This is important because it lets you pass the results of a [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query to the constructor.</span></span>  
  
 <span data-ttu-id="649a2-115">Oto przykład:</span><span class="sxs-lookup"><span data-stu-id="649a2-115">The following is an example:</span></span>  
  
 <span data-ttu-id="649a2-116">Te funkcje umożliwiają napisać kod przy użyciu literałów XML, aby utworzyć drzewo XML, a także do pisania kodu, który używa wyników [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] zapytania po utworzeniu drzewo XML:</span><span class="sxs-lookup"><span data-stu-id="649a2-116">These features enable you to write code using XML literals to create an XML tree, and also to write code that uses the results of [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] queries when you create an XML tree:</span></span>  
  
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
  
 <span data-ttu-id="649a2-117">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="649a2-117">This example produces the following output:</span></span>  
  
```xml  
<Root>  
  <Child>1</Child>  
  <Child>2</Child>  
  <Element>3</Element>  
  <Element>4</Element>  
  <Element>5</Element>  
</Root>  
```  
  
## <a name="see-also"></a><span data-ttu-id="649a2-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="649a2-118">See Also</span></span>  
 [<span data-ttu-id="649a2-119">Tworzenie drzewa XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="649a2-119">Creating XML Trees (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/creating-xml-trees.md)
