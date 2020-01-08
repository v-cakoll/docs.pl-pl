---
title: Jak korzystać ze słowników przy użyciu LINQ to XMLC#()
ms.date: 07/20/2015
ms.assetid: 57bcefe3-8433-4d3b-935a-511c9bcbdfa8
ms.openlocfilehash: 1a98293f208e80e969362fca27014ecd2e5c4183
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/25/2019
ms.locfileid: "75347228"
---
# <a name="how-to-work-with-dictionaries-using-linq-to-xml-c"></a><span data-ttu-id="21471-102">Jak korzystać ze słowników przy użyciu LINQ to XMLC#()</span><span class="sxs-lookup"><span data-stu-id="21471-102">How to work with dictionaries using LINQ to XML (C#)</span></span>
<span data-ttu-id="21471-103">Często wygodnie jest przekonwertować różne struktury danych na XML, a następnie XML z powrotem do innych struktur danych.</span><span class="sxs-lookup"><span data-stu-id="21471-103">It is often convenient to convert varieties of data structures to XML, and XML back to other data structures.</span></span> <span data-ttu-id="21471-104">W tym temacie przedstawiono konkretną implementację tego ogólnego podejścia poprzez konwersję <xref:System.Collections.Generic.Dictionary%602> do formatu XML i z powrotem.</span><span class="sxs-lookup"><span data-stu-id="21471-104">This topic shows a specific implementation of this general approach by converting a <xref:System.Collections.Generic.Dictionary%602> to XML and back.</span></span>  
  
## <a name="example"></a><span data-ttu-id="21471-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="21471-105">Example</span></span>  
 <span data-ttu-id="21471-106">W tym przykładzie stosowana jest forma konstrukcji funkcjonalnej, w której zapytania projektują nowe obiekty <xref:System.Xml.Linq.XElement> i wynikowa kolekcja jest przenoszona jako argument do konstruktora obiektu głównego <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="21471-106">This example uses a form of functional construction in which a query projects new <xref:System.Xml.Linq.XElement> objects, and the resulting collection is passed as an argument to the constructor of the Root <xref:System.Xml.Linq.XElement> object.</span></span>  
  
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
  
 <span data-ttu-id="21471-107">Ten kod generuje następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="21471-107">This code produces the following output:</span></span>  
  
```xml  
<Root>  
  <Child1>Value1</Child1>  
  <Child2>Value2</Child2>  
  <Child3>Value3</Child3>  
  <Child4>Value4</Child4>  
</Root>  
```  
  
## <a name="example"></a><span data-ttu-id="21471-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="21471-108">Example</span></span>  
 <span data-ttu-id="21471-109">Poniższy kod tworzy słownik z pliku XML.</span><span class="sxs-lookup"><span data-stu-id="21471-109">The following code creates a dictionary from XML.</span></span>  
  
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
  
 <span data-ttu-id="21471-110">Ten kod generuje następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="21471-110">This code produces the following output:</span></span>  
  
```output  
Child1:Value1  
Child2:Value2  
Child3:Value3  
Child4:Value4  
```  
