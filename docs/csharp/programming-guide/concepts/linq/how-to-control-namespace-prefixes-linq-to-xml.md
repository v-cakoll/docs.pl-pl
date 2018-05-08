---
title: 'Porady: kontrolowanie prefiksy Namespace (C#) (LINQ do XML)'
ms.date: 07/20/2015
ms.assetid: 64de5186-b81a-4ddd-8327-8693df59a01b
ms.openlocfilehash: af864139d56bd3ebb22cca6369b82539b9d007da
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-control-namespace-prefixes-c-linq-to-xml"></a>Porady: kontrolowanie prefiksy Namespace (C#) (LINQ do XML)
W tym temacie opisano, jak podczas serializowania drzewo XML można kontrolować prefiksy przestrzeni nazw.  
  
 W wielu sytuacjach nie jest potrzebne do sterowania prefiksy przestrzeni nazw.  
  
 Jednak niektóre narzędzia do programowania XML wymagają określonego formantu prefiksy przestrzeni nazw. Na przykład użytkownik może być manipulowanie arkusz stylów XSLT lub dokumentu XAML, który zawiera osadzony wyrażenia XPath, które odwołują się do określonego obszaru nazw prefiksów; w tym przypadku jest ważne, że dokument być serializowany z tych prefiksów.  
  
 Jest to najbardziej typowe przyczyny kontrolowanie prefiksy przestrzeni nazw.  
  
 Kontrolowanie prefiksy przestrzeni nazw innej typową przyczyną jest użytkownicy mają ręcznie edytować dokument XML, czy chcesz utworzyć prefiksy przestrzeni nazw, które są wygodne dla użytkownika na typ. Na przykład użytkownik może generować dokumentu XSD. Konwencje dla schematów sugerują, użyj jednej `xs` lub `xsd` jako prefiksu dla przestrzeni nazw schematu.  
  
 Aby kontrolować prefiksy przestrzeni nazw, należy wstawić atrybutów, które zadeklarować przestrzeni nazw. Deklarowanie przestrzeni nazw z prefiksów, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] podejmie próbę honorować prefiksy przestrzeni nazw podczas serializacji.  
  
 Aby utworzyć atrybutu, który deklaruje przestrzeni nazw z prefiksem, należy utworzyć gdzie przestrzeni nazw nazwa atrybutu jest atrybut <xref:System.Xml.Linq.XNamespace.Xmlns%2A>, a nazwa atrybutu to prefiks przestrzeni nazw. Wartość atrybutu jest identyfikatorem URI przestrzeni nazw.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie deklaruje dwie przestrzenie nazw. Określa, że `http://www.adventure-works.com` przestrzeń nazw ma prefiks `aw`oraz że `www.fourthcoffee.com` przestrzeń nazw ma prefiks `fc`.  
  
```csharp  
XNamespace aw = "http://www.adventure-works.com";  
XNamespace fc = "www.fourthcoffee.com";  
XElement root = new XElement(aw + "Root",  
    new XAttribute(XNamespace.Xmlns + "aw", "http://www.adventure-works.com"),  
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
<aw:Root xmlns:aw="http://www.adventure-works.com" xmlns:fc="www.fourthcoffee.com">  
  <fc:Child>  
    <aw:DifferentChild>other content</aw:DifferentChild>  
  </fc:Child>  
  <aw:Child2>c2 content</aw:Child2>  
  <fc:Child3>c3 content</fc:Child3>  
</aw:Root>  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Praca z przestrzeni nazw XML (C#)](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md)
