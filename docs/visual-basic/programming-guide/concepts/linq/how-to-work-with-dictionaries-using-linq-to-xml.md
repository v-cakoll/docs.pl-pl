---
title: "Porady: Praca z słowniki za pomocą LINQ do XML (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6cb3f969-1986-414a-b850-87418712edea
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: dc7290a3afca22ffc92914efacdb768a72e2aef7
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-work-with-dictionaries-using-linq-to-xml-visual-basic"></a><span data-ttu-id="0d6af-102">Porady: Praca z słowniki za pomocą LINQ do XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0d6af-102">How to: Work with Dictionaries Using LINQ to XML (Visual Basic)</span></span>
<span data-ttu-id="0d6af-103">Często jest to wygodny do przekonwertowania odmian struktur danych XML i XML inne struktury danych.</span><span class="sxs-lookup"><span data-stu-id="0d6af-103">It is often convenient to convert varieties of data structures to XML, and XML back to other data structures.</span></span> <span data-ttu-id="0d6af-104">W tym temacie przedstawiono konkretnej implementacji tego podejścia ogólne konwertując <xref:System.Collections.Generic.Dictionary%602> XML i na odwrót.</span><span class="sxs-lookup"><span data-stu-id="0d6af-104">This topic shows a specific implementation of this general approach by converting a <xref:System.Collections.Generic.Dictionary%602> to XML and back.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0d6af-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="0d6af-105">Example</span></span>  
 <span data-ttu-id="0d6af-106">W tym przykładzie używane literały XML i zapytanie w wyrażenia osadzonego.</span><span class="sxs-lookup"><span data-stu-id="0d6af-106">This example uses XML literals and a query in an embedded expression.</span></span> <span data-ttu-id="0d6af-107">Nowe projekty zapytania <xref:System.Xml.Linq.XElement> obiekty, które następnie stają się nowa zawartość `Root` <xref:System.Xml.Linq.XElement> obiektu.</span><span class="sxs-lookup"><span data-stu-id="0d6af-107">The query projects new <xref:System.Xml.Linq.XElement> objects, which then become the new content for the `Root` <xref:System.Xml.Linq.XElement> object.</span></span>  
  
```vb  
Dim dict As Dictionary(Of String, String) = New Dictionary(Of String, String)()  
dict.Add("Child1", "Value1")  
dict.Add("Child2", "Value2")  
dict.Add("Child3", "Value3")  
dict.Add("Child4", "Value4")  
Dim root As XElement = _  
    <Root>  
        <%= From keyValue In dict _  
            Select New XElement(keyValue.Key, keyValue.Value) %>  
    </Root>  
Console.WriteLine(root)  
```  
  
 <span data-ttu-id="0d6af-108">Ten kod generuje następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="0d6af-108">This code produces the following output:</span></span>  
  
```xml  
          <Root>  
  <Child1>Value1</Child1>  
  <Child2>Value2</Child2>  
  <Child3>Value3</Child3>  
  <Child4>Value4</Child4>  
</Root>  
```  
  
## <a name="example"></a><span data-ttu-id="0d6af-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="0d6af-109">Example</span></span>  
 <span data-ttu-id="0d6af-110">Poniższy kod tworzy słownik z pliku XML.</span><span class="sxs-lookup"><span data-stu-id="0d6af-110">The following code creates a dictionary from XML.</span></span>  
  
```vb  
Dim root As XElement = _  
        <Root>  
            <Child1>Value1</Child1>  
            <Child2>Value2</Child2>  
            <Child3>Value3</Child3>  
            <Child4>Value4</Child4>  
        </Root>  
  
Dim dict As Dictionary(Of String, String) = New Dictionary(Of String, String)  
For Each el As XElement In root.Elements  
    dict.Add(el.Name.LocalName, el.Value)  
Next  
For Each str As String In dict.Keys  
    Console.WriteLine("{0}:{1}", str, dict(str))  
Next  
```  
  
 <span data-ttu-id="0d6af-111">Ten kod generuje następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="0d6af-111">This code produces the following output:</span></span>  
  
```  
Child1:Value1  
Child2:Value2  
Child3:Value3  
Child4:Value4  
```  
  
## <a name="see-also"></a><span data-ttu-id="0d6af-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0d6af-112">See Also</span></span>  
 [<span data-ttu-id="0d6af-113">Projekcje i przekształcenia (LINQ do XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0d6af-113">Projections and Transformations (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/projections-and-transformations-linq-to-xml.md)
