---
title: "Zakres domyślne obszary nazw w języku C# 1"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: fe826236-830f-457a-9027-7ad62c909fae
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 95a31f4ffa1b27a8670d9dc979bdceb7f2b8dfdd
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="scope-of-default-namespaces-in-c"></a>Zakres domyślne obszary nazw w języku C#
Domyślne obszary nazw reprezentowany w drzewie XML nie są w zakresie zapytania. Jeśli masz kod XML, który znajduje się w domyślnej przestrzeni nazw, nadal należy zadeklarować <xref:System.Xml.Linq.XNamespace> zmienną i połączyć ją z nazwą lokalną aby kwalifikowana nazwa do użycia w zapytaniu.  
  
 Jest jedną z najczęściej występujących problemów podczas wykonywania zapytania drzewa XML, że jeśli drzewo składni XML ma domyślnej przestrzeni nazw, deweloper czasami zapisuje zapytanie tak, jakby plik XML nie zostały w przestrzeni nazw.  
  
 Pierwszy zestaw przykłady w tym temacie przedstawiono typowy sposób XML w domyślnej przestrzeni nazw jest załadowany, ale jest poddawany kwerendzie nieprawidłowo.  
  
 Drugi zestaw przykładach niezbędnych poprawek, aby wykonać zapytanie XML w przestrzeni nazw.  
  
## <a name="example"></a>Przykład  
 Ten przykład przedstawia tworzenie XML w przestrzeni nazw, a następnie ustaw kwerendę, która zwraca żadnego wyniku.  
  
### <a name="code"></a>Kod  
  
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
 Ten przykład generuje następujące wyniki:  
  
```  
Result set follows:  
End of result set  
```  
  
## <a name="example"></a>Przykład  
 Ten przykład przedstawia tworzenie XML w przestrzeni nazw i zapytanie zakodowanej poprawnie.  
  
 W przeciwieństwie do niepoprawnie zakodowany powyższym przykładzie właściwe podejście przy użyciu języka C# jest zadeklarować i zainicjować <xref:System.Xml.Linq.XNamespace> obiektu i używać go podczas określania <xref:System.Xml.Linq.XName> obiektów. W tym przypadku argument <xref:System.Xml.Linq.XElement.Elements%2A> jest metoda <xref:System.Xml.Linq.XName> obiektu.  
  
### <a name="code"></a>Kod  
  
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
 Ten przykład generuje następujące wyniki:  
  
```  
Result set follows:  
1  
2  
3  
End of result set  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Praca z przestrzeni nazw XML (C#)](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md)
