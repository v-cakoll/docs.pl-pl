---
title: 'Porady: Tworzenie dokumentu z przestrzeniami nazw (C#) (LINQ to XML)'
ms.date: 07/20/2015
ms.assetid: 37e63c57-f86d-47ac-88a7-2c2d107def30
ms.openlocfilehash: 0fa19af47847b0d6b804528af3f766c9775e74f3
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2018
ms.locfileid: "43863690"
---
# <a name="how-to-create-a-document-with-namespaces-c-linq-to-xml"></a>Porady: Tworzenie dokumentu z przestrzeniami nazw (C#) (LINQ to XML)
W tym temacie przedstawiono sposób tworzenia dokumentów z przestrzeni nazw.  
  
## <a name="example"></a>Przykład  
 Aby utworzyć element lub atrybut, który znajduje się w przestrzeni nazw, najpierw do deklarowania i inicjowania <xref:System.Xml.Linq.XNamespace> obiektu. Następnie należy użyć Przeciążony operator dodawania połączyć przestrzeni nazw o nazwie lokalnej, wyrażone jako ciąg.  
  
 Poniższy przykład tworzy dokument o jedną przestrzeń nazw. Domyślnie [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] serializuje tego dokumentu przy użyciu domyślnej przestrzeni nazw.  
  
```csharp  
// Create an XML tree in a namespace.  
XNamespace aw = "http://www.adventure-works.com";  
XElement root = new XElement(aw + "Root",  
    new XElement(aw + "Child", "child content")  
);  
Console.WriteLine(root);  
```  
  
 Ten przykład generuje następujące wyniki:  
  
```xml  
<Root xmlns="http://www.adventure-works.com">  
  <Child>child content</Child>  
</Root>  
```  
  
## <a name="example"></a>Przykład  
 Poniższy przykład tworzy dokument o jedną przestrzeń nazw. Tworzy również atrybut, który deklaruje przestrzeni nazw z prefiksem nazw. Aby utworzyć atrybut, który deklaruje przestrzeni nazw z prefiksem, należy utworzyć atrybut, gdzie nazwa atrybutu jest prefiks przestrzeni nazw, a ta nazwa jest <xref:System.Xml.Linq.XNamespace.Xmlns%2A> przestrzeni nazw. Wartość tego atrybutu jest identyfikatorem URI przestrzeni nazw.  
  
```csharp  
// Create an XML tree in a namespace, with a specified prefix  
XNamespace aw = "http://www.adventure-works.com";  
XElement root = new XElement(aw + "Root",  
    new XAttribute(XNamespace.Xmlns + "aw", "http://www.adventure-works.com"),  
    new XElement(aw + "Child", "child content")  
);  
Console.WriteLine(root);  
```  
  
 Ten przykład generuje następujące wyniki:  
  
```xml  
<aw:Root xmlns:aw="http://www.adventure-works.com">  
  <aw:Child>child content</aw:Child>  
</aw:Root>  
```  
  
## <a name="example"></a>Przykład  
 Tworzenie dokumentu, który zawiera dwie przestrzeni nazw można znaleźć w poniższym przykładzie. Jeden jest domyślny obszar nazw. Innym jest przestrzeń nazw z prefiksem.  
  
 Umieszczając przestrzeni nazw atrybutów w elemencie głównym, przestrzenie nazw są serializowane, aby `http://www.adventure-works.com` jest domyślny obszar nazw i `www.fourthcoffee.com` jest serializowana z prefiksem "fc". Aby utworzyć atrybut, który deklaruje domyślny obszar nazw, należy utworzyć atrybut o nazwie "xmlns", bez przestrzeni nazw. Wartość atrybutu jest domyślny obszar nazw identyfikatora URI.  
  
```csharp  
// The http://www.adventure-works.com namespace is forced to be the default namespace.  
XNamespace aw = "http://www.adventure-works.com";  
XNamespace fc = "www.fourthcoffee.com";  
XElement root = new XElement(aw + "Root",  
    new XAttribute("xmlns", "http://www.adventure-works.com"),  
    new XAttribute(XNamespace.Xmlns + "fc", "www.fourthcoffee.com"),  
    new XElement(fc + "Child",  
        new XElement(aw + "DifferentChild", "other content")  
    ),  
    new XElement(aw + "Child2", "c2 content"),  
    new XElement(fc + "Child3", "c3 content")  
);  
Console.WriteLine(root);  
```  
  
 Ten przykład generuje następujące wyniki:  
  
```xml  
<Root xmlns="http://www.adventure-works.com" xmlns:fc="www.fourthcoffee.com">  
  <fc:Child>  
    <DifferentChild>other content</DifferentChild>  
  </fc:Child>  
  <Child2>c2 content</Child2>  
  <fc:Child3>c3 content</fc:Child3>  
</Root>  
```  
  
## <a name="example"></a>Przykład  
 Poniższy przykład tworzy dokument, który zawiera dwie przestrzenie nazw, obie z prefiksy przestrzeni nazw.  
  
```csharp  
XNamespace aw = "http://www.adventure-works.com";  
XNamespace fc = "www.fourthcoffee.com";  
XElement root = new XElement(aw + "Root",  
    new XAttribute(XNamespace.Xmlns + "aw", aw.NamespaceName),  
    new XAttribute(XNamespace.Xmlns + "fc", fc.NamespaceName),  
    new XElement(fc + "Child",  
        new XElement(aw + "DifferentChild", "other content")  
    ),  
    new XElement(aw + "Child2", "c2 content"),  
    new XElement(fc + "Child3", "c3 content")  
);  
Console.WriteLine(root);  
```  
  
 Ten przykład generuje następujące wyniki:  
  
```xml  
<aw:Root xmlns:aw="http://www.adventure-works.com" xmlns:fc="www.fourthcoffee.com">  
  <fc:Child>  
    <aw:DifferentChild>other content</aw:DifferentChild>  
  </fc:Child>  
  <aw:Child2>c2 content</aw:Child2>  
  <fc:Child3>c3 content</fc:Child3>  
</aw:Root>  
```  
  
## <a name="example"></a>Przykład  
 Innym sposobem, aby osiągnąć ten sam wynik jest użycie rozwiniętej nazwy zamiast deklarowania i tworzenie <xref:System.Xml.Linq.XNamespace> obiektu.  
  
 Takie podejście ma wpływ na wydajność. Każdorazowo przekazania ciągu, który zawiera rozwiniętej nazwy, aby [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] musi przeanalizować nazwy, Znajdź rozproszone obiekty przestrzeni nazw i Znajdź nazwę rozproszone obiekty. Ten proces trwa czasu procesora CPU. Ważne jest, wydajności, możesz chcieć deklarowanie i użycie <xref:System.Xml.Linq.XNamespace> jawnie obiektu.  
  
 Jeśli wydajność jest ważnym zagadnieniem, zobacz [wstępne rozproszenie obiektów XName (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/pre-atomization-of-xname-objects-linq-to-xml.md) Aby uzyskać więcej informacji  
  
```csharp  
// Create an XML tree in a namespace, with a specified prefix  
XElement root = new XElement("{http://www.adventure-works.com}Root",  
    new XAttribute(XNamespace.Xmlns + "aw", "http://www.adventure-works.com"),  
    new XElement("{http://www.adventure-works.com}Child", "child content")  
);  
Console.WriteLine(root);  
```  
  
 Ten przykład generuje następujące wyniki:  
  
```xml  
<aw:Root xmlns:aw="http://www.adventure-works.com">  
  <aw:Child>child content</aw:Child>  
</aw:Root>  
```  
  
## <a name="see-also"></a>Zobacz też

- [Praca z przestrzeniami nazw XML (C#)](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md)
