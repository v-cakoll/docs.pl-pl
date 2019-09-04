---
title: 'Instrukcje: Pracuj ze słownikami przy użyciuC#LINQ to XML ()'
ms.date: 07/20/2015
ms.assetid: 57bcefe3-8433-4d3b-935a-511c9bcbdfa8
ms.openlocfilehash: 55512e6039010d74d390c805c119935c436f9834
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70253242"
---
# <a name="how-to-work-with-dictionaries-using-linq-to-xml-c"></a>Instrukcje: Pracuj ze słownikami przy użyciuC#LINQ to XML ()
Często wygodnie jest przekonwertować różne struktury danych na XML, a następnie XML z powrotem do innych struktur danych. W tym temacie przedstawiono określoną implementację ogólnego podejścia poprzez konwersję <xref:System.Collections.Generic.Dictionary%602> do formatu XML i z powrotem.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie stosowana jest forma konstrukcji funkcjonalnej, w której zapytania projektują nowe <xref:System.Xml.Linq.XElement> obiekty, a wynikowa kolekcja jest przenoszona jako argument do konstruktora obiektu głównego. <xref:System.Xml.Linq.XElement>  
  
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
  
 Ten kod generuje następujące dane wyjściowe:  
  
```xml  
<Root>  
  <Child1>Value1</Child1>  
  <Child2>Value2</Child2>  
  <Child3>Value3</Child3>  
  <Child4>Value4</Child4>  
</Root>  
```  
  
## <a name="example"></a>Przykład  
 Poniższy kod tworzy słownik z pliku XML.  
  
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
  
 Ten kod generuje następujące dane wyjściowe:  
  
```output  
Child1:Value1  
Child2:Value2  
Child3:Value3  
Child4:Value4  
```  
