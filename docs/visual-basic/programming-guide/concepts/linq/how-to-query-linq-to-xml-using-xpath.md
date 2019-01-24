---
title: 'Instrukcje: Zapytania LINQ to XML przy użyciu składni XPath (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: e1f69a20-1efa-452d-9089-c472fa84b3d5
ms.openlocfilehash: 754b3c4d1f14f2f78b5688f13ab679bc01798a6c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54615993"
---
# <a name="how-to-query-linq-to-xml-using-xpath-visual-basic"></a>Instrukcje: Zapytania LINQ to XML przy użyciu składni XPath (Visual Basic)
W tym temacie przedstawiono metody rozszerzenia, które pozwalają na wykonywanie zapytań drzewa XML przy użyciu wyrażenie XPath. Aby uzyskać szczegółowe informacje o używaniu tych metod rozszerzenia, zobacz <xref:System.Xml.XPath.Extensions?displayProperty=nameWithType>.  
  
 Jeśli nie masz bardzo powód do wykonywania zapytań przy użyciu XPath, takie jak zwiększone użycie starszego kodu, za pomocą LINQ to XML przy użyciu XPath nie jest zalecane. Zapytania XPath nie będzie wykonywać także [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] zapytania.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład tworzy mały drzewa XML i używa <xref:System.Xml.XPath.Extensions.XPathSelectElements%2A> wybrać zestaw elementów.  
  
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
  
 Ten przykład generuje następujące wyniki:  
  
```xml  
<Child2>4</Child2>  
<Child2>5</Child2>  
<Child2>6</Child2>  
```  
  
## <a name="see-also"></a>Zobacz także
- [Zaawansowane techniki zapytań (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/advanced-query-techniques-linq-to-xml.md)
