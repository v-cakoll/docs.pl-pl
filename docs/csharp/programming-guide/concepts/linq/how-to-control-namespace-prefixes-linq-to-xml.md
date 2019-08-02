---
title: 'Instrukcje: Przekontrolowanie prefiksówC#przestrzeni nazw () (LINQ to XML)'
ms.date: 07/20/2015
ms.assetid: 64de5186-b81a-4ddd-8327-8693df59a01b
ms.openlocfilehash: 5b836be46001b660547532311b1b507ff234975f
ms.sourcegitcommit: eb9ff6f364cde6f11322e03800d8f5ce302f3c73
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/01/2019
ms.locfileid: "68710162"
---
# <a name="how-to-control-namespace-prefixes-c-linq-to-xml"></a>Instrukcje: Przekontrolowanie prefiksówC#przestrzeni nazw () (LINQ to XML)
W tym temacie opisano, jak można kontrolować prefiksy przestrzeni nazw podczas serializacji drzewa XML.  
  
 W wielu sytuacjach nie trzeba kontrolować prefiksów przestrzeni nazw.  
  
 Jednak niektóre narzędzia programowania XML wymagają określonej kontroli prefiksów przestrzeni nazw. Na przykład może to być manipulowanie arkuszem stylów XSLT lub dokumentem XAML zawierającym osadzone wyrażenia XPath odwołujące się do określonych prefiksów przestrzeni nazw; w takim przypadku ważne jest, aby dokument był serializowany z tymi określonymi prefiksami.  
  
 Jest to najbardziej typowy powód kontrolowania prefiksów przestrzeni nazw.  
  
 Kolejną częstą przyczyną kontrolowania prefiksów przestrzeni nazw jest to, że użytkownicy będą mogli ręcznie edytować dokument XML i utworzyć prefiksy przestrzeni nazw, które są wygodne dla użytkownika. Na przykład może być generowany dokument XSD. Konwencje dla schematów sugerują użycie albo `xs` `xsd` jako prefiksu przestrzeni nazw schematu.  
  
 Aby kontrolować prefiksy przestrzeni nazw, należy wstawić atrybuty, które deklarują przestrzenie nazw. W przypadku deklarowania przestrzeni nazw z określonymi prefiksami [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] program podejmie próbę zahonorowania prefiksów przestrzeni nazw podczas serializacji.  
  
 Aby utworzyć atrybut, który deklaruje przestrzeń nazw z prefiksem, utworzysz atrybut, w którym przestrzeń nazw atrybutu jest <xref:System.Xml.Linq.XNamespace.Xmlns%2A>, a nazwa atrybutu jest prefiksem przestrzeni nazw. Wartość atrybutu jest identyfikatorem URI przestrzeni nazw.  
  
## <a name="example"></a>Przykład  
 Ten przykład deklaruje dwie przestrzenie nazw. Określa, że `http://www.adventure-works.com` przestrzeń nazw ma `aw`prefiks i że `www.fourthcoffee.com` przestrzeń nazw ma prefiks `fc`.  
  
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
  
## <a name="see-also"></a>Zobacz także

- [Przegląd przestrzeni nazw (LINQ to XML)C#()](namespaces-overview-linq-to-xml.md)
