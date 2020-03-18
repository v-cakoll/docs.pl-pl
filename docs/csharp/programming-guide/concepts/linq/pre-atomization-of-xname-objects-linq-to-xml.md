---
title: Wstępne atomizacja obiektów XName (LINQ do XML) (C#)
ms.date: 07/20/2015
ms.assetid: e84fbbe7-f072-4771-bfbb-059d18e1ad15
ms.openlocfilehash: 2fd754a352bd2988e52ec9c67a9915a8e587b107
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "69591493"
---
# <a name="pre-atomization-of-xname-objects-linq-to-xml-c"></a>Wstępne atomizacja obiektów XName (LINQ do XML) (C#)
Jednym ze sposobów poprawy wydajności w LINQ do XML <xref:System.Xml.Linq.XName> jest wstępnie atomize obiektów. Wstępnej atomizacji oznacza, że można <xref:System.Xml.Linq.XName> przypisać ciąg do obiektu przed utworzeniem drzewa XML przy użyciu konstruktorów <xref:System.Xml.Linq.XElement> i <xref:System.Xml.Linq.XAttribute> klas. Następnie zamiast przekazywania ciągu do konstruktora, który będzie używać <xref:System.Xml.Linq.XName>niejawnej konwersji <xref:System.Xml.Linq.XName> z ciągu do , przekazać zainicjowany obiekt.  
  
 Zwiększa to wydajność podczas tworzenia dużego drzewa XML, w którym są powtarzane określone nazwy. Aby to zrobić, należy zadeklarować i zainicjować <xref:System.Xml.Linq.XName> obiekty przed skonstruowaniem drzewa XML, a następnie użyć <xref:System.Xml.Linq.XName> obiektów zamiast określania ciągów dla nazwy elementu i atrybutów. Ta technika może przynieść znaczny wzrost wydajności, jeśli tworzysz dużą liczbę elementów (lub atrybutów) o tej samej nazwie.  
  
 Należy przetestować wstępnej atomizacji ze scenariuszem, aby zdecydować, czy należy go używać.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje to.  
  
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
  
 W poniższym przykładzie przedstawiono tę samą technikę, w której dokument XML znajduje się w przestrzeni nazw:  
  
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
  
 Poniższy przykład jest bardziej podobny do tego, co prawdopodobnie napotkasz w prawdziwym świecie. W tym przykładzie zawartość elementu jest dostarczana przez kwerendę:  
  
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
  
 Poprzedni przykład działa lepiej niż w poniższym przykładzie, w którym nazwy nie są wstępnie atomized:  
  
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

- [Atomizowane obiekty XName i XNamespace (LINQ do XML) (C#)](./atomized-xname-and-xnamespace-objects-linq-to-xml.md)
