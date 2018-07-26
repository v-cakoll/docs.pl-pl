---
title: 'Porady: tworzenie zapytań dotyczących LINQ to XML przy użyciu XPath (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: e1f69a20-1efa-452d-9089-c472fa84b3d5
ms.openlocfilehash: d8f23bd8417c3f59377e5e677b08e403ecc1122d
ms.sourcegitcommit: 70c76a12449439bac0f7a359866be5a0311ce960
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/25/2018
ms.locfileid: "39244351"
---
# <a name="how-to-query-linq-to-xml-using-xpath-visual-basic"></a><span data-ttu-id="efd95-102">Porady: tworzenie zapytań dotyczących LINQ to XML przy użyciu XPath (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="efd95-102">How to: Query LINQ to XML Using XPath (Visual Basic)</span></span>
<span data-ttu-id="efd95-103">W tym temacie przedstawiono metody rozszerzenia, które pozwalają na wykonywanie zapytań drzewa XML przy użyciu wyrażenie XPath.</span><span class="sxs-lookup"><span data-stu-id="efd95-103">This topic introduces the extension methods that enable you to query an XML tree by using XPath.</span></span> <span data-ttu-id="efd95-104">Aby uzyskać szczegółowe informacje o używaniu tych metod rozszerzenia, zobacz <xref:System.Xml.XPath.Extensions?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="efd95-104">For detailed information about using these extension methods, see <xref:System.Xml.XPath.Extensions?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="efd95-105">Jeśli nie masz bardzo powód do wykonywania zapytań przy użyciu XPath, takie jak zwiększone użycie starszego kodu, za pomocą LINQ to XML przy użyciu XPath nie jest zalecane.</span><span class="sxs-lookup"><span data-stu-id="efd95-105">Unless you have a very specific reason for querying using XPath, such as extensive use of legacy code, using XPath with LINQ to XML is not recommended.</span></span> <span data-ttu-id="efd95-106">Zapytania XPath nie będzie wykonywać także [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] zapytania.</span><span class="sxs-lookup"><span data-stu-id="efd95-106">XPath queries will not perform as well as [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] queries.</span></span>  
  
## <a name="example"></a><span data-ttu-id="efd95-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="efd95-107">Example</span></span>  
 <span data-ttu-id="efd95-108">Poniższy przykład tworzy mały drzewa XML i używa <xref:System.Xml.XPath.Extensions.XPathSelectElements%2A> wybrać zestaw elementów.</span><span class="sxs-lookup"><span data-stu-id="efd95-108">The following example creates a small XML tree and uses <xref:System.Xml.XPath.Extensions.XPathSelectElements%2A> to select a set of elements.</span></span>  
  
```vb  
Dim root As XElement = _  
    <Root>  
        <Child1>1</Child1>  
        <Child1>2</Child1>  
        <Child1>3</Child1>  
        <Child2>4</Child2>  
        <Child2>5</Child2>  
        <Child2>6</Child2>  
    </Root>  
  
Dim list As IEnumerable(Of XElement) = root.XPathSelectElements("./Child2")  
For Each el As XElement In list  
    Console.WriteLine(el)  
Next  
```  
  
 <span data-ttu-id="efd95-109">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="efd95-109">This example produces the following output:</span></span>  
  
```xml  
<Child2>4</Child2>  
<Child2>5</Child2>  
<Child2>6</Child2>  
```  
  
## <a name="see-also"></a><span data-ttu-id="efd95-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="efd95-110">See Also</span></span>  
 [<span data-ttu-id="efd95-111">Zaawansowane techniki zapytań (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="efd95-111">Advanced Query Techniques (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/advanced-query-techniques-linq-to-xml.md)
