---
title: 'Instrukcje: Pisanie zapytań dotyczących kodu XML w przestrzeniach nazw (C#)'
ms.date: 07/20/2015
ms.assetid: 7c54df81-15e4-4091-8c81-a87637029130
ms.openlocfilehash: e6b966e90d1f7fc86efaa422ecd8afb030d97163
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54722105"
---
# <a name="how-to-write-queries-on-xml-in-namespaces-c"></a>Instrukcje: Pisanie zapytań dotyczących kodu XML w przestrzeniach nazw (C#)
Aby napisać zapytanie na języku XML, który znajduje się w przestrzeni nazw, należy użyć <xref:System.Xml.Linq.XName> obiektów, które mają poprawną przestrzeń nazw.  
  
 Dla języka C#, najbardziej typowym podejściem jest do zainicjowania <xref:System.Xml.Linq.XNamespace> ciąg, który zawiera identyfikator URI, następnie użycie Przeciążony operator dodawania połączyć przestrzeni nazw o nazwie lokalnej.  
  
 Pierwszy zestaw przykładów w tym temacie przedstawiono sposób tworzenia drzewa XML w domyślnej przestrzeni nazw. Drugi zestaw przedstawia sposób tworzenia drzewa XML w przestrzeni nazw z prefiksem.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład tworzy drzewa XML, który znajduje się w domyślnej przestrzeni nazw. Pobiera kolekcję elementów.  
  
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
 W języku C# możesz pisać zapytania w taki sam sposób niezależnie od tego, czy piszesz zapytania na drzewo składni XML, który używa przestrzeni nazw z prefiksem lub drzewa XML przy użyciu domyślnej przestrzeni nazw.  
  
 Poniższy przykład tworzy drzewa XML, który znajduje się w przestrzeni nazw z prefiksem. Pobiera kolekcję elementów.  
  
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
  
## <a name="see-also"></a>Zobacz także

- [Praca z przestrzeniami nazw XML (C#)](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md)
