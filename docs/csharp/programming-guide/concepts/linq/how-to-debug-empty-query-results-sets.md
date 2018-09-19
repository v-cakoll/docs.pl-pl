---
title: 'Porady: debugowanie zestawów wyników zapytania (C#)'
ms.date: 07/20/2015
ms.assetid: b569f0dc-425e-45a6-acbf-770fb761c981
ms.openlocfilehash: 4760b1e5274634954bd5fe4b3880fd4415af2510
ms.sourcegitcommit: f513a91160b3fec289dd06646d0d6f81f8fcf910
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46007155"
---
# <a name="how-to-debug-empty-query-results-sets-c"></a>Porady: debugowanie zestawów wyników zapytania (C#)
Jedną z najbardziej typowych problemów podczas wykonywania zapytań dotyczących drzew XML jest, że jeśli drzewa XML ma domyślny obszar nazw, deweloper czasami zapisuje zapytanie tak, jakby plik XML nie znajdowały się w przestrzeni nazw.  
  
 Pierwszy zestaw przykładów w tym temacie przedstawiono typowy sposób XML w domyślnej przestrzeni nazw jest ładowany i jest wykonywane zapytanie nieprawidłowo.  
  
 Drugi zestaw przykładach pokazano niezbędnych poprawek, dzięki czemu można tworzyć zapytania XML w przestrzeni nazw.  
  
 Aby uzyskać więcej informacji, zobacz [Praca z przestrzeniami nazw XML (C#)](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md).  
  
## <a name="example"></a>Przykład  
 Ten przykład przedstawia tworzenie XML w przestrzeni nazw i ustaw zapytania, które zwraca żadnego wyniku.  
  
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
  
 Ten przykład generuje następujące wyniki:  
  
```  
Result set follows:  
End of result set  
```  
  
## <a name="example"></a>Przykład  
 Ten przykład przedstawia tworzenie XML w przestrzeni nazw i zapytanie, które są poprawnie kodowane.  
  
 Rozwiązanie jest do zadeklarowania i zainicjowania <xref:System.Xml.Linq.XNamespace> obiektu i z niej korzystać, podczas określania <xref:System.Xml.Linq.XName> obiektów. W tym przypadku argument <xref:System.Xml.Linq.XElement.Elements%2A> metodą jest <xref:System.Xml.Linq.XName> obiektu.  
  
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
  
 Ten przykład generuje następujące wyniki:  
  
```  
Result set follows:  
1  
2  
3  
End of result set  
```  
  
## <a name="see-also"></a>Zobacz też

- [Podstawowe zapytania (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/basic-queries-linq-to-xml.md)
