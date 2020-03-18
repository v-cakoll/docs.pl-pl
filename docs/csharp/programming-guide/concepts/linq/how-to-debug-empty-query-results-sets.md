---
title: Jak debugować puste zestawy wyników kwerendy (C#)
ms.date: 07/20/2015
ms.assetid: b569f0dc-425e-45a6-acbf-770fb761c981
ms.openlocfilehash: 2716f7c525ac6bee8d2fb374e4ecc4c975d852a0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "74141293"
---
# <a name="how-to-debug-empty-query-results-sets-c"></a>Jak debugować puste zestawy wyników kwerendy (C#)
Jednym z najczęstszych problemów podczas wykonywania zapytań drzew XML jest to, że jeśli drzewo XML ma domyślny obszar nazw, deweloper czasami zapisuje kwerendę tak, jakby XML nie znajdował się w przestrzeni nazw.  
  
 Pierwszy zestaw przykładów w tym temacie pokazuje typowy sposób, że XML w domyślnym obszarze nazw jest ładowany i jest przeszukiwany nieprawidłowo.  
  
 Drugi zestaw przykładów pokazuje niezbędne poprawki, dzięki czemu można wysyłać zapytania do języka XML w obszarze nazw.  
  
 Aby uzyskać więcej informacji, zobacz [Omówienie przestrzeni nazw (LINQ do XML) (C#)](namespaces-overview-linq-to-xml.md).  
  
## <a name="example"></a>Przykład  
 W tym przykładzie przedstawiono tworzenie języka XML w obszarze nazw i kwerendę, która zwraca pusty zestaw wyników.  
  
```csharp  
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
    from el in root.Elements("Child")  
    select el;  
Console.WriteLine("Result set follows:");  
foreach (XElement el in c1)  
    Console.WriteLine((int)el);  
Console.WriteLine("End of result set");  
```  
  
 W tym przykładzie daje następujący wynik:  
  
```output  
Result set follows:  
End of result set  
```  
  
## <a name="example"></a>Przykład  
 W tym przykładzie przedstawiono tworzenie języka XML w obszarze nazw i kwerendę, która jest poprawnie zakodowana.  
  
 Rozwiązaniem jest zadeklarowanie i zainicjowanie <xref:System.Xml.Linq.XNamespace> obiektu oraz użycie go <xref:System.Xml.Linq.XName> podczas określania obiektów. W takim przypadku argument <xref:System.Xml.Linq.XContainer.Elements%2A> metody jest <xref:System.Xml.Linq.XName> obiektem.  
  
```csharp  
XElement root = XElement.Parse(  
@"<Root xmlns='http://www.adventure-works.com'>  
    <Child>1</Child>  
    <Child>2</Child>  
    <Child>3</Child>  
    <AnotherChild>4</AnotherChild>  
    <AnotherChild>5</AnotherChild>  
    <AnotherChild>6</AnotherChild>  
</Root>");  
XNamespace aw = "http://www.adventure-works.com";  
IEnumerable<XElement> c1 =  
    from el in root.Elements(aw + "Child")  
    select el;  
Console.WriteLine("Result set follows:");  
foreach (XElement el in c1)  
    Console.WriteLine((int)el);  
Console.WriteLine("End of result set");  
```  
  
 W tym przykładzie daje następujący wynik:  
  
```output  
Result set follows:  
1  
2  
3  
End of result set  
```  
