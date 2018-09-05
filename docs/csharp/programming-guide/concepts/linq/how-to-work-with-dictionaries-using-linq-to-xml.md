---
title: 'Porady: Praca ze słownikami przy użyciu LINQ to XML (C#)'
ms.date: 07/20/2015
ms.assetid: 57bcefe3-8433-4d3b-935a-511c9bcbdfa8
ms.openlocfilehash: afe4fafb9963b4fc429f441349f8190c9a1e5bac
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43531984"
---
# <a name="how-to-work-with-dictionaries-using-linq-to-xml-c"></a><span data-ttu-id="d17bd-102">Porady: Praca ze słownikami przy użyciu LINQ to XML (C#)</span><span class="sxs-lookup"><span data-stu-id="d17bd-102">How to: Work with Dictionaries Using LINQ to XML (C#)</span></span>
<span data-ttu-id="d17bd-103">Często jest to wygodne przekonwertować różne typy struktur danych XML i XML do innych struktur danych.</span><span class="sxs-lookup"><span data-stu-id="d17bd-103">It is often convenient to convert varieties of data structures to XML, and XML back to other data structures.</span></span> <span data-ttu-id="d17bd-104">W tym temacie przedstawiono określoną implementację tego podejścia ogólne, konwertując <xref:System.Collections.Generic.Dictionary%602> XML i na odwrót.</span><span class="sxs-lookup"><span data-stu-id="d17bd-104">This topic shows a specific implementation of this general approach by converting a <xref:System.Collections.Generic.Dictionary%602> to XML and back.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d17bd-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="d17bd-105">Example</span></span>  
 <span data-ttu-id="d17bd-106">W tym przykładzie użyto formularza konstrukcja funkcjonalna, w którym zapytanie projektów nowych <xref:System.Xml.Linq.XElement> obiektów i kolekcji wynikowy jest przekazywany jako argument do konstruktora obiektu głównego <xref:System.Xml.Linq.XElement> obiektu.</span><span class="sxs-lookup"><span data-stu-id="d17bd-106">This example uses a form of functional construction in which a query projects new <xref:System.Xml.Linq.XElement> objects, and the resulting collection is passed as an argument to the constructor of the Root <xref:System.Xml.Linq.XElement> object.</span></span>  
  
```csharp  
Dictionary<string, string> dict = new Dictionary<string, string>();  
dict.Add("Child1", "Value1");  
dict.Add("Child2", "Value2");  
dict.Add("Child3", "Value3");  
dict.Add("Child4", "Value4");  
XElement root = new XElement("Root",  
    from keyValue in dict  
    select new XElement(keyValue.Key, keyValue.Value)  
);  
Console.WriteLine(root);  
```  
  
 <span data-ttu-id="d17bd-107">Ten kod generuje następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="d17bd-107">This code produces the following output:</span></span>  
  
```xml  
<Root>  
  <Child1>Value1</Child1>  
  <Child2>Value2</Child2>  
  <Child3>Value3</Child3>  
  <Child4>Value4</Child4>  
</Root>  
```  
  
## <a name="example"></a><span data-ttu-id="d17bd-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="d17bd-108">Example</span></span>  
 <span data-ttu-id="d17bd-109">Poniższy kod tworzy słownik z pliku XML.</span><span class="sxs-lookup"><span data-stu-id="d17bd-109">The following code creates a dictionary from XML.</span></span>  
  
```csharp  
XElement root = new XElement("Root",  
    new XElement("Child1", "Value1"),  
    new XElement("Child2", "Value2"),  
    new XElement("Child3", "Value3"),  
    new XElement("Child4", "Value4")  
);  
  
Dictionary<string, string> dict = new Dictionary<string, string>();  
foreach (XElement el in root.Elements())  
    dict.Add(el.Name.LocalName, el.Value);  
foreach (string str in dict.Keys)  
    Console.WriteLine("{0}:{1}", str, dict[str]);  
```  
  
 <span data-ttu-id="d17bd-110">Ten kod generuje następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="d17bd-110">This code produces the following output:</span></span>  
  
```  
Child1:Value1  
Child2:Value2  
Child3:Value3  
Child4:Value4  
```  
  
## <a name="see-also"></a><span data-ttu-id="d17bd-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d17bd-111">See Also</span></span>

- [<span data-ttu-id="d17bd-112">Projekcje i przekształcenia (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="d17bd-112">Projections and Transformations (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/projections-and-transformations-linq-to-xml.md)
