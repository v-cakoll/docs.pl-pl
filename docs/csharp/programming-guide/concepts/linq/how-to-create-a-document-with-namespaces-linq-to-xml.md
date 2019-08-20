---
title: 'Instrukcje: Tworzenie dokumentu z przestrzeniami nazwC#() (LINQ to XML)'
ms.date: 07/20/2015
ms.assetid: 37e63c57-f86d-47ac-88a7-2c2d107def30
ms.openlocfilehash: 180dc5138f8f21b3e52e4a8b3cee4748cafdd0f5
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69593885"
---
# <a name="how-to-create-a-document-with-namespaces-c-linq-to-xml"></a>Instrukcje: Tworzenie dokumentu z przestrzeniami nazwC#() (LINQ to XML)
W tym temacie pokazano, jak tworzyć dokumenty z przestrzeniami nazw.  
  
## <a name="example"></a>Przykład  
 Aby utworzyć element lub atrybut, który znajduje się w przestrzeni nazw, należy najpierw zadeklarować i zainicjować <xref:System.Xml.Linq.XNamespace> obiekt. Następnie należy użyć przeciążenia operatora dodawania, aby połączyć przestrzeń nazw z nazwą lokalną wyrażoną jako ciąg.  
  
 Poniższy przykład tworzy dokument z jedną przestrzenią nazw. Domyślnie program [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] serializować ten dokument przy użyciu domyślnej przestrzeni nazw.  
  
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
 Poniższy przykład tworzy dokument z jedną przestrzenią nazw. Tworzy również atrybut, który deklaruje przestrzeń nazw z prefiksem przestrzeni nazw. Aby utworzyć atrybut, który deklaruje przestrzeń nazw z prefiksem, utworzysz atrybut, w którym nazwa atrybutu jest prefiksem przestrzeni nazw, a ta nazwa znajduje się w <xref:System.Xml.Linq.XNamespace.Xmlns%2A> przestrzeni nazw. Wartość tego atrybutu jest identyfikatorem URI przestrzeni nazw.  
  
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
 Poniższy przykład pokazuje, jak utworzyć dokument zawierający dwie przestrzenie nazw. Jest to domyślna przestrzeń nazw. Innym jest przestrzenią nazw z prefiksem.  
  
 Uwzględniając atrybuty przestrzeni nazw w elemencie głównym, przestrzenie nazw są serializowane, `http://www.adventure-works.com` więc jest to domyślna przestrzeń nazw `www.fourthcoffee.com` i jest serializowany z prefiksem "FC". Aby utworzyć atrybut, który deklaruje domyślną przestrzeń nazw, należy utworzyć atrybut o nazwie "xmlns" bez przestrzeni nazw. Wartość atrybutu jest domyślnym identyfikatorem URI przestrzeni nazw.  
  
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
 Poniższy przykład tworzy dokument zawierający dwie przestrzenie nazw, zarówno z prefiksami przestrzeni nazw.  
  
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
 Innym sposobem osiągnięcia tego samego wyniku jest użycie rozwiniętych nazw zamiast deklarowania i tworzenia <xref:System.Xml.Linq.XNamespace> obiektu.  
  
 Takie podejście ma wpływ na wydajność. Za każdym razem, gdy przekazujesz ciąg, który zawiera rozwiniętą [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] nazwę [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], należy przeanalizować nazwę, znaleźć wykorzystaną przestrzeń nazw i znaleźć nazwę atomową. Ten proces pobiera czas procesora CPU. Jeśli wydajność jest ważna, warto zadeklarować obiekt i używać go <xref:System.Xml.Linq.XNamespace> jawnie.  
  
 Jeśli wydajność jest ważnym problemem, zobacz [pre-rozproszenie of XName Objects (LINQ to XML)C#(),](./pre-atomization-of-xname-objects-linq-to-xml.md) Aby uzyskać więcej informacji  
  
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
  
## <a name="see-also"></a>Zobacz także

- [Przegląd przestrzeni nazw (LINQ to XML)C#()](namespaces-overview-linq-to-xml.md)
