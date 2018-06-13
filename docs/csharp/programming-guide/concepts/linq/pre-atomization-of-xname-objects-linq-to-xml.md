---
title: Wstępne Atomizacja XName obiektów (LINQ do XML) (C#)
ms.date: 07/20/2015
ms.assetid: e84fbbe7-f072-4771-bfbb-059d18e1ad15
ms.openlocfilehash: 8d793dcdfd2669fa96c92be0e0e3c3ebb8f38d0e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33329306"
---
# <a name="pre-atomization-of-xname-objects-linq-to-xml-c"></a>Wstępne Atomizacja XName obiektów (LINQ do XML) (C#)
Jednym ze sposobów poprawy wydajności w składniku LINQ to XML ma wstępnie rozproszyć <xref:System.Xml.Linq.XName> obiektów. Wstępne Atomizacja oznacza, że można przypisać ciąg <xref:System.Xml.Linq.XName> obiekt przed utworzeniem drzewa XML za pomocą konstruktorów <xref:System.Xml.Linq.XElement> i <xref:System.Xml.Linq.XAttribute> klasy. Następnie, zamiast przekazywanie ciąg konstruktora, który użyć niejawna konwersja z ciągu na <xref:System.Xml.Linq.XName>, należy przekazać zainicjowane <xref:System.Xml.Linq.XName> obiektu.  
  
 Poprawia to wydajność, podczas tworzenia dużych drzewa XML, w którym są powtarzane konkretne nazwy. W tym celu należy zadeklarować i zainicjuj <xref:System.Xml.Linq.XName> obiekty przed skonstruuj drzewo XML, a następnie użyć <xref:System.Xml.Linq.XName> obiektów zamiast określania ciągów dla nazw elementów i atrybutów. Ta technika może spowodować znaczący wzrost wydajności w przypadku tworzenia dużą liczbę elementów (lub atrybutów) o takiej samej nazwie.  
  
 Należy przetestować przed Atomizacja z danego scenariusza zdecydować, czy należy z niej korzystać.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano to.  
  
```csharp  
XName Root = "Root";  
XName Data = "Data";  
XName ID = "ID";  
  
XElement root = new XElement(Root,  
    new XElement(Data,  
        new XAttribute(ID, "1"),  
        "4,100,000"),  
    new XElement(Data,  
        new XAttribute(ID, "2"),  
        "3,700,000"),  
    new XElement(Data,  
        new XAttribute(ID, "3"),  
        "1,150,000")  
);  
  
Console.WriteLine(root);  
```  
  
 Ten przykład generuje następujące wyniki:  
  
```xml  
<Root>  
  <Data ID="1">4,100,000</Data>  
  <Data ID="2">3,700,000</Data>  
  <Data ID="3">1,150,000</Data>  
</Root>  
```  
  
 W poniższym przykładzie przedstawiono tę samą metodę, gdy dokument XML jest w przestrzeni nazw:  
  
```csharp  
XNamespace aw = "http://www.adventure-works.com";  
XName Root = aw + "Root";  
XName Data = aw + "Data";  
XName ID = "ID";  
  
XElement root = new XElement(Root,  
    new XAttribute(XNamespace.Xmlns + "aw", aw),  
    new XElement(Data,  
        new XAttribute(ID, "1"),  
        "4,100,000"),  
    new XElement(Data,  
        new XAttribute(ID, "2"),  
        "3,700,000"),  
    new XElement(Data,  
        new XAttribute(ID, "3"),  
        "1,150,000")  
);  
  
Console.WriteLine(root);  
```  
  
 Ten przykład generuje następujące wyniki:  
  
```xml  
<aw:Root xmlns:aw="http://www.adventure-works.com">  
  <aw:Data ID="1">4,100,000</aw:Data>  
  <aw:Data ID="2">3,700,000</aw:Data>  
  <aw:Data ID="3">1,150,000</aw:Data>  
</aw:Root>  
```  
  
 Poniższy przykład przypomina więcej co prawdopodobnie wystąpią w świecie rzeczywistym. W tym przykładzie zawartość elementu jest dostarczana przez kwerendę:  
  
```csharp  
XName Root = "Root";  
XName Data = "Data";  
XName ID = "ID";  
  
DateTime t1 = DateTime.Now;  
XElement root = new XElement(Root,  
    from i in System.Linq.Enumerable.Range(1, 100000)  
    select new XElement(Data,  
        new XAttribute(ID, i),  
        i * 5)  
);  
DateTime t2 = DateTime.Now;  
  
Console.WriteLine("Time to construct:{0}", t2 - t1);  
```  
  
 Poprzedni przykład wykonuje lepszą wydajność niż poniższy przykład, w którym nazwy nie są wstępnie atomized:  
  
```csharp  
DateTime t1 = DateTime.Now;  
XElement root = new XElement("Root",  
    from i in System.Linq.Enumerable.Range(1, 100000)  
    select new XElement("Data",  
        new XAttribute("ID", i),  
        i * 5)  
);  
DateTime t2 = DateTime.Now;  
  
Console.WriteLine("Time to construct:{0}", t2 - t1);  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Wydajność (LINQ do XML) (C#)](../../../../csharp/programming-guide/concepts/linq/performance-linq-to-xml.md)  
 [Atomized XName i XNamespace obiektów (LINQ do XML) (C#)](../../../../csharp/programming-guide/concepts/linq/atomized-xname-and-xnamespace-objects-linq-to-xml.md)
