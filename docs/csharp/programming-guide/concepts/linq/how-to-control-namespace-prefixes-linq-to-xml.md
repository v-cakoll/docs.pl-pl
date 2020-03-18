---
title: Jak kontrolować prefiksy obszaru nazw (C#) (LINQ do XML)
ms.date: 07/20/2015
ms.assetid: 64de5186-b81a-4ddd-8327-8693df59a01b
ms.openlocfilehash: 9f43c0804d8c830fa75f1e1390cb578c5f5d5106
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "74141380"
---
# <a name="how-to-control-namespace-prefixes-c-linq-to-xml"></a>Jak kontrolować prefiksy obszaru nazw (C#) (LINQ do XML)
W tym temacie opisano, jak można kontrolować prefiksy obszaru nazw podczas serializacji drzewa XML.  
  
 W wielu sytuacjach nie jest konieczne kontrolowanie prefiksów obszaru nazw.  
  
 Jednak niektóre narzędzia programowania XML wymagają określonej kontroli prefiksów obszaru nazw. Na przykład może być manipulowanie arkusz emitujący style XSLT lub dokument XAML zawierający osadzone wyrażenia XPath, które odwołują się do prefiksów określonych przestrzeni nazw; w takim przypadku ważne jest, aby dokument był serializowany z tymi określonymi prefiksami.  
  
 Jest to najczęstsza przyczyna kontrolowania prefiksów obszaru nazw.  
  
 Inną częstą przyczyną kontrolowania prefiksów obszaru nazw jest ręczne edytowanie dokumentu XML przez użytkowników i tworzenie prefiksów obszaru nazw, które są wygodne dla użytkownika do wpisania. Na przykład może być generowanie dokumentu XSD. Konwencje dotyczące schematów sugerują, że `xs` `xsd` używasz jednego lub prefiksu obszaru nazw schematu.  
  
 Aby sterować prefiksami obszaru nazw, należy wstawić atrybuty, które deklarują obszary nazw. Jeśli deklarujesz przestrzenie nazw z [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] określonymi prefiksami, spróbuje honorować prefiksy obszaru nazw podczas serializacji.  
  
 Aby utworzyć atrybut, który deklaruje obszar nazw z prefiksem, należy utworzyć atrybut, <xref:System.Xml.Linq.XNamespace.Xmlns%2A>w którym znajduje się obszar nazw atrybutu, a nazwa atrybutu jest prefiksem obszaru nazw. Wartość atrybutu jest identyfikator URI obszaru nazw.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie zadeklarowane są dwie przestrzenie nazw. Określa, że `http://www.adventure-works.com` obszar nazw ma prefiks `aw`, `www.fourthcoffee.com` i że obszar `fc`nazw ma prefiks .  
  
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

- [Omówienie przestrzeni nazw (LINQ do XML) (C#)](namespaces-overview-linq-to-xml.md)
