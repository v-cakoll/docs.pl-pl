---
title: Wstępne rozproszenie obiektów XName (LINQ to XML) (C#)
ms.date: 07/20/2015
ms.assetid: e84fbbe7-f072-4771-bfbb-059d18e1ad15
ms.openlocfilehash: 6a1f3ea5e0b53fe488c13ebd273cce436d7c685b
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43516219"
---
# <a name="pre-atomization-of-xname-objects-linq-to-xml-c"></a>Wstępne rozproszenie obiektów XName (LINQ to XML) (C#)
Jednym ze sposobów, aby zwiększyć wydajność w składniku LINQ to XML jest wstępnie wyodrębnić <xref:System.Xml.Linq.XName> obiektów. Wstępne rozproszenie oznacza, że możesz przypisać ciąg <xref:System.Xml.Linq.XName> obiekt przed przystąpieniem do tworzenia drzewa XML za pomocą konstruktorów z <xref:System.Xml.Linq.XElement> i <xref:System.Xml.Linq.XAttribute> klasy. Następnie, zamiast przekazywać ciąg do konstruktora, który użyć niejawna konwersja ciągu na <xref:System.Xml.Linq.XName>, należy przekazać zainicjowanej <xref:System.Xml.Linq.XName> obiektu.  
  
 Poprawia to wydajność, podczas tworzenia dużych drzewa XML, w którym są powtarzane określonej nazwy. Aby to zrobić, możesz zadeklarować i zainicjować <xref:System.Xml.Linq.XName> obiektów przed konstruowania drzewa XML, a następnie użyj <xref:System.Xml.Linq.XName> obiektów zamiast określania ciągów nazw elementów i atrybutów. Ta technika może przynieść znaczący wzrost wydajności w przypadku tworzenia dużej liczby elementów (lub atrybutów) o takiej samej nazwie.  
  
 Wstępne rozproszenie należy przetestować przy użyciu danego scenariusza, aby zdecydować, czy należy jej używać.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia to.  
  
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
  
 Poniższy przykład pokazuje tę samą technikę, w którym dokument XML jest w przestrzeni nazw:  
  
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
  
 Poniższy przykład jest bardziej przypominające, co prawdopodobnie wystąpi w świecie rzeczywistym. W tym przykładzie zawartość elementu jest dostarczana przez kwerendę:  
  
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
  
 Poprzedni przykład działa lepiej niż poniższy przykład, w których nazwy są nie wstępnie rozproszone obiekty:  
  
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

- [Wydajność (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/performance-linq-to-xml.md)  
- [Rozproszone obiekty XName i Xnamespace (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/atomized-xname-and-xnamespace-objects-linq-to-xml.md)
