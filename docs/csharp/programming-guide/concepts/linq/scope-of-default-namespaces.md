---
title: Zakres domyślnych przestrzeni nazw w języku C#
ms.date: 07/20/2015
ms.assetid: fe826236-830f-457a-9027-7ad62c909fae
ms.openlocfilehash: 7615351f6e5f8b18bd6466a83d54aa65a6c99b50
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "70253041"
---
# <a name="scope-of-default-namespaces-in-c"></a>Zakres domyślnych obszarów nazw w języku C\#
Domyślne obszary nazw reprezentowane w drzewie XML nie znajdują się w zakresie kwerend. Jeśli masz XML, który znajduje się w domyślnym <xref:System.Xml.Linq.XNamespace> obszarze nazw, nadal należy zadeklarować zmienną i połączyć ją z nazwą lokalną, aby kwalifikowana nazwa była używana w kwerendzie.  
  
 Jednym z najczęstszych problemów podczas wykonywania zapytań drzew XML jest to, że jeśli drzewo XML ma domyślny obszar nazw, deweloper czasami zapisuje kwerendę tak, jakby XML nie znajdował się w przestrzeni nazw.  
  
 Pierwszy zestaw przykładów w tym temacie pokazuje typowy sposób, że XML w domyślnym obszarze nazw jest ładowany, ale jest przeszukiwany nieprawidłowo.  
  
 Drugi zestaw przykładów pokazuje niezbędne poprawki, dzięki czemu można wysyłać zapytania do języka XML w obszarze nazw.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie przedstawiono utworzenie języka XML w obszarze nazw i kwerendę, która zwraca pusty zestaw wyników.  
  
### <a name="code"></a>Code  
  
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
  
### <a name="comments"></a>Komentarze  
 W tym przykładzie daje następujący wynik:  
  
```output  
Result set follows:  
End of result set  
```  
  
## <a name="example"></a>Przykład  
 W tym przykładzie przedstawiono tworzenie języka XML w obszarze nazw i kwerendę, która jest poprawnie zakodowana.  
  
 W przeciwieństwie do niepoprawnie zakodowane powyżej, poprawne podejście podczas korzystania z <xref:System.Xml.Linq.XNamespace> Języka C# jest zadeklarować <xref:System.Xml.Linq.XName> i zainicjować obiekt i używać go podczas określania obiektów. W takim przypadku argument <xref:System.Xml.Linq.XContainer.Elements%2A> metody jest <xref:System.Xml.Linq.XName> obiektem.  
  
### <a name="code"></a>Code  
  
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
  
### <a name="comments"></a>Komentarze  
 W tym przykładzie daje następujący wynik:  
  
```output  
Result set follows:  
1  
2  
3  
End of result set  
```  
  
## <a name="see-also"></a>Zobacz też

- [Omówienie przestrzeni nazw (LINQ do XML) (C#)](namespaces-overview-linq-to-xml.md)
