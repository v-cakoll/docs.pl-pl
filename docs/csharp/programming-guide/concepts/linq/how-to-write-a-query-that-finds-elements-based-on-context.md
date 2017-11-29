---
title: "Porady: Napisz zapytanie, które wyszukuje elementy na podstawie kontekstu (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 3ff79ef0-fc8b-42fe-8cc0-10dc32b06b4e
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: a9e818c5e0967a6d146cd48b81aebcba4bbdde3f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-write-a-query-that-finds-elements-based-on-context-c"></a>Porady: Napisz zapytanie, które wyszukuje elementy na podstawie kontekstu (C#)
Czasami może być konieczne Napisz zapytanie, które wybiera elementy na podstawie ich kontekstu. Można filtrować na podstawie poprzedzające lub następujące elementów równorzędnych. Można filtrować na podstawie podrzędnej lub elementy nadrzędne.  
  
 Aby to zrobić, zapisywanie zapytania i przy użyciu wyników kwerendy w `where` klauzuli. Jeśli trzeba najpierw przetestować wartości null, a następnie sprawdź wartość jest wygodniejsze w zapytaniu w `let` klauzuli, a następnie użyj wyniki w `where` klauzuli.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład wybranie wszystkich `p` elementów, które są od razu następuje `ul` elementu.  
  
```csharp  
XElement doc = XElement.Parse(@"<Root>  
    <p id=""1""/>  
    <ul>abc</ul>  
    <Child>  
        <p id=""2""/>  
        <notul/>  
        <p id=""3""/>  
        <ul>def</ul>  
        <p id=""4""/>  
    </Child>  
    <Child>  
        <p id=""5""/>  
        <notul/>  
        <p id=""6""/>  
        <ul>abc</ul>  
        <p id=""7""/>  
    </Child>  
</Root>");  
  
IEnumerable<XElement> items =  
    from e in doc.Descendants("p")  
    let z = e.ElementsAfterSelf().FirstOrDefault()  
    where z != null && z.Name.LocalName == "ul"  
    select e;  
  
foreach (XElement e in items)  
    Console.WriteLine("id = {0}", (string)e.Attribute("id"));  
```  
  
 Ten kod generuje następujące dane wyjściowe:  
  
```  
id = 1  
id = 3  
id = 6  
```  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano tego samego zapytania w formacie XML, który znajduje się w przestrzeni nazw. Aby uzyskać więcej informacji, zobacz [Praca z przestrzeni nazw XML (C#)](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md).  
  
```csharp  
XElement doc = XElement.Parse(@"<Root xmlns='http://www.adatum.com'>  
    <p id=""1""/>  
    <ul>abc</ul>  
    <Child>  
        <p id=""2""/>  
        <notul/>  
        <p id=""3""/>  
        <ul>def</ul>  
        <p id=""4""/>  
    </Child>  
    <Child>  
        <p id=""5""/>  
        <notul/>  
        <p id=""6""/>  
        <ul>abc</ul>  
        <p id=""7""/>  
    </Child>  
</Root>");  
  
XNamespace ad = "http://www.adatum.com";  
  
IEnumerable<XElement> items =  
    from e in doc.Descendants(ad + "p")  
    let z = e.ElementsAfterSelf().FirstOrDefault()  
    where z != null && z.Name == ad.GetName("ul")  
    select e;  
  
foreach (XElement e in items)  
    Console.WriteLine("id = {0}", (string)e.Attribute("id"));  
```  
  
 Ten kod generuje następujące dane wyjściowe:  
  
```  
id = 1  
id = 3  
id = 6  
```  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Xml.Linq.XElement.Parse%2A>  
 <xref:System.Xml.Linq.XContainer.Descendants%2A>  
 <xref:System.Xml.Linq.XNode.ElementsAfterSelf%2A>  
 <xref:System.Linq.Enumerable.FirstOrDefault%2A>  
 [Podstawowe zapytania (LINQ do XML) (C#)](../../../../csharp/programming-guide/concepts/linq/basic-queries-linq-to-xml.md)
