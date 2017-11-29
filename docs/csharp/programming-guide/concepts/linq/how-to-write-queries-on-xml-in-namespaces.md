---
title: "Porady: Pisanie zapytań na kod XML w przestrzeni nazw (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 7c54df81-15e4-4091-8c81-a87637029130
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 194e12f88f7c22c365a18bc2dd42a3dd26b5c569
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-write-queries-on-xml-in-namespaces-c"></a>Porady: Pisanie zapytań na kod XML w przestrzeni nazw (C#)
Aby napisać zapytanie na języku XML, który znajduje się w przestrzeni nazw, należy użyć <xref:System.Xml.Linq.XName> obiektów, które mają poprawną przestrzeń nazw.  
  
 Język C#, najbardziej typowym podejściem jest zainicjowanie <xref:System.Xml.Linq.XNamespace> przy użyciu ciągu, który zawiera identyfikator URI, następnie za pomocą dodanie przeciążenia operatora łączenia przestrzeni nazw z nazwą lokalną.  
  
 Pierwszy zestaw przykłady w tym temacie przedstawiono sposób tworzenia drzewo XML w domyślnej przestrzeni nazw. Drugi zestaw pokazano, jak utworzyć drzewo XML w przestrzeni nazw z prefiksem.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład tworzy drzewo XML, który znajduje się w domyślnej przestrzeni nazw. Następnie pobierania kolekcję elementów.  
  
```csharp  
XNamespace aw = "http://www.adventure-works.com";  
XElement root = XElement.Parse(  
@"<Root xmlns='http://www.adventure-works.com'>  
    <Child>1</Child>  
    <Child>2</Child>  
    <Child>3</Child>  
    <AnotherChild>4</AnotherChild>  
    <AnotherChild>5</AnotherChild>  
    <AnotherChild>6</AnotherChild>  
</Root>");  
IEnumerable<XElement> c1 =  
    from el in root.Elements(aw + "Child")  
    select el;  
foreach (XElement el in c1)  
    Console.WriteLine((int)el);  
```  
  
 Ten przykład generuje następujące wyniki:  
  
```  
1  
2  
3  
```  
  
## <a name="example"></a>Przykład  
 W języku C# możesz pisać zapytania w taki sam sposób, niezależnie od tego, czy pisania zapytania na drzewo XML, który używa przestrzeni nazw z prefiksem lub drzewo XML z domyślnej przestrzeni nazw.  
  
 Poniższy przykład tworzy drzewo XML, który znajduje się w przestrzeni nazw z prefiksem. Następnie pobierania kolekcję elementów.  
  
```csharp  
XNamespace aw = "http://www.adventure-works.com";  
XElement root = XElement.Parse(  
@"<aw:Root xmlns:aw='http://www.adventure-works.com'>  
    <aw:Child>1</aw:Child>  
    <aw:Child>2</aw:Child>  
    <aw:Child>3</aw:Child>  
    <aw:AnotherChild>4</aw:AnotherChild>  
    <aw:AnotherChild>5</aw:AnotherChild>  
    <aw:AnotherChild>6</aw:AnotherChild>  
</aw:Root>");  
IEnumerable<XElement> c1 =  
    from el in root.Elements(aw + "Child")  
    select el;  
foreach (XElement el in c1)  
    Console.WriteLine((int)el);  
```  
  
 Ten przykład generuje następujące wyniki:  
  
```  
1  
2  
3  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Praca z przestrzeni nazw XML (C#)](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md)
