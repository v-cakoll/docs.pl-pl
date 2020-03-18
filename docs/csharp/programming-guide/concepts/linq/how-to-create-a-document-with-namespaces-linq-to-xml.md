---
title: Jak utworzyć dokument z obszarami nazw (C#) (LINQ do XML)
ms.date: 07/20/2015
ms.assetid: 37e63c57-f86d-47ac-88a7-2c2d107def30
ms.openlocfilehash: 429b0b0b41f2201b983f931e469b25ff406b91ac
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "74141323"
---
# <a name="how-to-create-a-document-with-namespaces-c-linq-to-xml"></a>Jak utworzyć dokument z obszarami nazw (C#) (LINQ do XML)
W tym temacie pokazano, jak tworzyć dokumenty z obszarami nazw.  
  
## <a name="example"></a>Przykład  
 Aby utworzyć element lub atrybut, który znajduje się w przestrzeni nazw, należy najpierw zadeklarować i zainicjować <xref:System.Xml.Linq.XNamespace> obiekt. Następnie należy użyć przeciążenia operatora dodawania, aby połączyć obszar nazw z nazwą lokalną, wyrażoną jako ciąg.  
  
 Poniższy przykład tworzy dokument z jednym obszarem nazw. Domyślnie [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] serializuje ten dokument z domyślnym obszarem nazw.  
  
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
 Poniższy przykład tworzy dokument z jednym obszarem nazw. Tworzy również atrybut, który deklaruje obszar nazw z prefiksem obszaru nazw. Aby utworzyć atrybut, który deklaruje obszar nazw z prefiksem, należy utworzyć atrybut, w którym nazwa atrybutu <xref:System.Xml.Linq.XNamespace.Xmlns%2A> jest prefiksem obszaru nazw, a ta nazwa znajduje się w obszarze nazw. Wartość tego atrybutu jest identyfikator URI obszaru nazw.  
  
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
 W poniższym przykładzie przedstawiono utworzenie dokumentu, który zawiera dwie przestrzenie nazw. Jednym z nich jest domyślna przestrzeń nazw. Innym jest obszar nazw z prefiksem.  
  
 Dołączając atrybuty obszaru nazw do elementu głównego, przestrzenie nazw są serializowane tak, że `http://www.adventure-works.com` jest to domyślny obszar nazw i `www.fourthcoffee.com` jest serializowany z prefiksem "fc". Aby utworzyć atrybut, który deklaruje domyślny obszar nazw, należy utworzyć atrybut o nazwie "xmlns", bez obszaru nazw. Wartość atrybutu jest domyślnym identyfikatorem URI obszaru nazw.  
  
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
 Poniższy przykład tworzy dokument, który zawiera dwie przestrzenie nazw, zarówno z prefiksami obszaru nazw.  
  
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
 Innym sposobem osiągnięcia tego samego wyniku jest użycie rozwiniętych <xref:System.Xml.Linq.XNamespace> nazw zamiast deklarowania i tworzenia obiektu.  
  
 Takie podejście ma wpływ na wydajność. Za każdym razem, gdy przekażesz [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] ciąg zawierający rozwiniętą nazwę, musi przeanalizować nazwę, znaleźć roztomięty obszar nazw i znaleźć roztomiętą nazwę. Ten proces zajmuje czas procesora CPU. Jeśli wydajność jest ważna, można zadeklarować <xref:System.Xml.Linq.XNamespace> i używać obiektu jawnie.  
  
 Jeśli wydajność jest ważnym problemem, zobacz [Wstępne atomizacja obiektów XName (LINQ do XML) (C#),](./pre-atomization-of-xname-objects-linq-to-xml.md) aby uzyskać więcej informacji  
  
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

- [Omówienie przestrzeni nazw (LINQ do XML) (C#)](namespaces-overview-linq-to-xml.md)
