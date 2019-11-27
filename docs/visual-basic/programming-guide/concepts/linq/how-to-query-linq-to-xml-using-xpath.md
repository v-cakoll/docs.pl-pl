---
title: 'Instrukcje: zapytanie LINQ to XML przy użyciu XPath'
ms.date: 07/20/2015
ms.assetid: e1f69a20-1efa-452d-9089-c472fa84b3d5
ms.openlocfilehash: 563756c019ddd458d46f47c843e32ddc7bbaacd1
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74347657"
---
# <a name="how-to-query-linq-to-xml-using-xpath-visual-basic"></a><span data-ttu-id="6ab45-102">Instrukcje: zapytanie LINQ to XML przy użyciu XPath (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6ab45-102">How to: Query LINQ to XML Using XPath (Visual Basic)</span></span>
<span data-ttu-id="6ab45-103">W tym temacie przedstawiono metody rozszerzające, które umożliwiają badanie drzewa XML przy użyciu XPath.</span><span class="sxs-lookup"><span data-stu-id="6ab45-103">This topic introduces the extension methods that enable you to query an XML tree by using XPath.</span></span> <span data-ttu-id="6ab45-104">Aby uzyskać szczegółowe informacje na temat korzystania z tych metod rozszerzających, zobacz <xref:System.Xml.XPath.Extensions?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="6ab45-104">For detailed information about using these extension methods, see <xref:System.Xml.XPath.Extensions?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="6ab45-105">Chyba że masz bardzo konkretny powód wykonywania zapytań przy użyciu XPath, na przykład w przypadku korzystania z starszego kodu, używanie XPath z LINQ to XML nie jest zalecane.</span><span class="sxs-lookup"><span data-stu-id="6ab45-105">Unless you have a very specific reason for querying using XPath, such as extensive use of legacy code, using XPath with LINQ to XML is not recommended.</span></span> <span data-ttu-id="6ab45-106">Zapytania XPath nie będą wykonywane, a także [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] zapytań.</span><span class="sxs-lookup"><span data-stu-id="6ab45-106">XPath queries will not perform as well as [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] queries.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6ab45-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="6ab45-107">Example</span></span>  
 <span data-ttu-id="6ab45-108">Poniższy przykład tworzy małe drzewo XML i używa <xref:System.Xml.XPath.Extensions.XPathSelectElements%2A> do wybierania zestawu elementów.</span><span class="sxs-lookup"><span data-stu-id="6ab45-108">The following example creates a small XML tree and uses <xref:System.Xml.XPath.Extensions.XPathSelectElements%2A> to select a set of elements.</span></span>  
  
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
  
 <span data-ttu-id="6ab45-109">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="6ab45-109">This example produces the following output:</span></span>  
  
```xml  
<Child2>4</Child2>  
<Child2>5</Child2>  
<Child2>6</Child2>  
```  
  
## <a name="see-also"></a><span data-ttu-id="6ab45-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6ab45-110">See also</span></span>

- [<span data-ttu-id="6ab45-111">Zaawansowane techniki zapytań (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6ab45-111">Advanced Query Techniques (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/advanced-query-techniques-linq-to-xml.md)
