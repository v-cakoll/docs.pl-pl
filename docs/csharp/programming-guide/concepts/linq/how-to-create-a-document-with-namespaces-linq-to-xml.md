---
title: 'Porady: Tworzenie dokumentu z przestrzeni nazw (C#) (LINQ do XML)'
ms.date: 07/20/2015
ms.assetid: 37e63c57-f86d-47ac-88a7-2c2d107def30
ms.openlocfilehash: ab572e0af79d51205167ad60b1b80e8ba6b43707
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-create-a-document-with-namespaces-c-linq-to-xml"></a>Porady: Tworzenie dokumentu z przestrzeni nazw (C#) (LINQ do XML)
W tym temacie przedstawiono sposób tworzenia dokumentów z przestrzeni nazw.  
  
## <a name="example"></a>Przykład  
 Aby utworzyć element lub atrybut, który znajduje się w przestrzeni nazw, należy najpierw zadeklarować i zainicjuj <xref:System.Xml.Linq.XNamespace> obiektu. Następnie należy dodanie przeciążenia operatora połączyć przestrzeni nazw z nazwą lokalną, wyrażone jako ciąg.  
  
 Poniższy przykład powoduje utworzenie dokumentu o jednej przestrzeni nazw. Domyślnie [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] serializuje ten dokument z domyślnej przestrzeni nazw.  
  
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
 Poniższy przykład powoduje utworzenie dokumentu o jednej przestrzeni nazw. Tworzy również atrybut, który deklaruje przestrzeni nazw z prefiksem przestrzeni nazw. Aby utworzyć atrybutu, który deklaruje przestrzeni nazw z prefiksem, należy utworzyć atrybutu, gdzie nazwa atrybutu jest prefiks przestrzeni nazw, a ta nazwa jest <xref:System.Xml.Linq.XNamespace.Xmlns%2A> przestrzeni nazw. Wartość tego atrybutu jest identyfikatorem URI przestrzeni nazw.  
  
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
 Poniższy przykład przedstawia tworzenie dokumentu, który zawiera dwie przestrzenie nazw. Jedna jest domyślnej przestrzeni nazw. Inny jest przestrzenią nazw z prefiksem.  
  
 W tym przestrzeń nazw atrybutów w elemencie głównym, przestrzenie nazw są serializowane, aby http://www.adventure-works.com jest domyślna przestrzeń nazw i www.fourthcoffee.com jest serializowany z prefiksem "fc". Aby utworzyć atrybutu, który deklaruje domyślnej przestrzeni nazw, należy utworzyć atrybut o nazwie "xmlns", bez przestrzeni nazw. Wartość atrybutu jest domyślny identyfikator URI przestrzeni nazw.  
  
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
 Poniższy przykład tworzy dokument, który zawiera dwie przestrzenie nazw, zarówno z prefiksy przestrzeni nazw.  
  
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
 Innym sposobem wykonania takiego samego wyniku jest używanie rozszerzonych nazw zamiast deklarowanie i tworzenie <xref:System.Xml.Linq.XNamespace> obiektu.  
  
 Takie podejście ma wpływ na wydajność. Zawsze przekazać ciąg, który zawiera rozwiniętą nazwą do [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] należy przeanalizować nazwy, znajdowanie atomized przestrzeni nazw i znaleźć atomized nazwy. Ten proces trwa czas procesora CPU. Wydajności odgrywa ważną rolę, możesz chcieć deklarowanie i użycie <xref:System.Xml.Linq.XNamespace> jawnie obiektu.  
  
 Jeśli wydajność jest ważne problemu, zobacz [wstępne Atomizacja obiektów XName (LINQ do XML) (C#)](../../../../csharp/programming-guide/concepts/linq/pre-atomization-of-xname-objects-linq-to-xml.md) Aby uzyskać więcej informacji  
  
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
 [Praca z przestrzeni nazw XML (C#)](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md)
