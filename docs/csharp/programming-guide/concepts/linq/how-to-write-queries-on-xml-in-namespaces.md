---
title: Jak zapisywać zapytania w języku XML w przestrzeniach nazw (C#)
ms.date: 07/20/2015
ms.assetid: 7c54df81-15e4-4091-8c81-a87637029130
ms.openlocfilehash: a8b8d55daaad1ae00e43fed897080ed7a62fafab
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75337373"
---
# <a name="how-to-write-queries-on-xml-in-namespaces-c"></a>Jak zapisywać zapytania w języku XML w przestrzeniach nazw (C#)
Aby napisać kwerendę w xml, który znajduje <xref:System.Xml.Linq.XName> się w obszarze nazw, należy użyć obiektów, które mają poprawny obszar nazw.  
  
 W przypadku języka C#najczęstszym podejściem <xref:System.Xml.Linq.XNamespace> jest zainicjowanie ciągu zawierającego identyfikator URI, a następnie połączenie obszaru nazw z nazwą lokalną za pomocą operatora dodawania.  
  
 Pierwszy zestaw przykładów w tym temacie pokazuje, jak utworzyć drzewo XML w domyślnym obszarze nazw. Drugi zestaw pokazuje, jak utworzyć drzewo XML w przestrzeni nazw z prefiksem.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład tworzy drzewo XML, który znajduje się w domyślnym obszarze nazw. Następnie pobiera kolekcję elementów.  
  
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
  
```output  
1  
2  
3  
```  
  
## <a name="example"></a>Przykład  
 W języku C#, kwerendy są pisane w ten sam sposób, niezależnie od tego, czy piszesz zapytania w drzewie XML, który używa obszaru nazw z prefiksem, czy na drzewie XML z domyślnym obszarem nazw.  
  
 Poniższy przykład tworzy drzewo XML, który znajduje się w przestrzeni nazw z prefiksem. Następnie pobiera kolekcję elementów.  
  
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
  
```output  
1  
2  
3  
```  
  
## <a name="see-also"></a>Zobacz też

- [Omówienie przestrzeni nazw (LINQ do XML) (C#)](namespaces-overview-linq-to-xml.md)
