---
title: Omówienie klasy XAttribute (C#)
ms.date: 07/20/2015
ms.assetid: 5a630f24-f9ad-400e-831e-c14ebfc9e142
ms.openlocfilehash: 7a806314664c6319fc45cff0dddedbe38027059d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75635668"
---
# <a name="xattribute-class-overview-c"></a>Omówienie klasy XAttribute (C#)
Atrybuty są pary nazwa/wartość, które są skojarzone z elementem. Klasa <xref:System.Xml.Linq.XAttribute> reprezentuje atrybuty XML.  
  
## <a name="overview"></a>Omówienie  
 Praca z atrybutami jest [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] podobna do pracy z elementami. Ich konstruktory są podobne. Metody, które są używane do pobierania kolekcji z nich są podobne. Wyrażenie kwerendy LINQ dla kolekcji atrybutów wygląda bardzo podobnie do wyrażenia kwerendy LINQ dla kolekcji elementów.  
  
 Kolejność, w jakiej atrybuty zostały dodane do elementu jest zachowywana. Oznacza to, że podczas itetensji przez atrybuty, widać je w tej samej kolejności, że zostały one dodane.  
  
## <a name="the-xattribute-constructor"></a>Konstruktor XAttribute  
 Następujący konstruktor <xref:System.Xml.Linq.XAttribute> klasy jest najczęściej używany:  
  
|Konstruktor|Opis|  
|-----------------|-----------------|  
|`XAttribute(XName name, object content)`|Tworzy obiekt <xref:System.Xml.Linq.XAttribute>. Argument `name` określa nazwę atrybutu; `content` określa zawartość atrybutu.|  
  
### <a name="creating-an-element-with-an-attribute"></a>Tworzenie elementu z atrybutem  
 Poniższy kod przedstawia typowe zadanie tworzenia elementu, który zawiera atrybut:  
  
```csharp  
XElement phone = new XElement("Phone",  
    new XAttribute("Type", "Home"),  
    "555-555-5555");  
Console.WriteLine(phone);  
```  
  
 Ten przykład generuje następujące wyniki:  
  
```xml  
<Phone Type="Home">555-555-5555</Phone>  
```  
  
### <a name="functional-construction-of-attributes"></a>Funkcjonalna konstrukcja atrybutów  
 Obiekty można <xref:System.Xml.Linq.XAttribute> konstruować zgodnie z <xref:System.Xml.Linq.XElement> konstrukcją obiektów w następujący sposób:  
  
```csharp  
XElement c = new XElement("Customers",  
    new XElement("Customer",  
        new XElement("Name", "John Doe"),  
        new XElement("PhoneNumbers",  
            new XElement("Phone",  
                new XAttribute("type", "home"),  
                "555-555-5555"),  
            new XElement("Phone",  
                new XAttribute("type", "work"),  
                "666-666-6666")  
        )  
    )  
);  
Console.WriteLine(c);  
```  
  
 Ten przykład generuje następujące wyniki:  
  
```xml  
<Customers>  
  <Customer>  
    <Name>John Doe</Name>  
    <PhoneNumbers>  
      <Phone type="home">555-555-5555</Phone>  
      <Phone type="work">666-666-6666</Phone>  
    </PhoneNumbers>  
  </Customer>  
</Customers>  
```  
  
### <a name="attributes-are-not-nodes"></a>Atrybuty nie są węzłami  
 Istnieją pewne różnice między atrybutami i elementami. <xref:System.Xml.Linq.XAttribute>obiekty nie są węzłami w drzewie XML. Są to pary nazw/wartości skojarzone z elementem XML. W przeciwieństwie do modelu obiektu dokumentu (DOM), odzwierciedla to bardziej odzwierciedla strukturę XML. Mimo <xref:System.Xml.Linq.XAttribute> że obiekty nie są w rzeczywistości węzłów w drzewie XML, praca z <xref:System.Xml.Linq.XAttribute> obiektami jest bardzo podobny do pracy z <xref:System.Xml.Linq.XElement> obiektami.  
  
 To rozróżnienie jest przede wszystkim ważne tylko dla deweloperów, którzy piszą kod, który działa z drzewami XML na poziomie węzła. Wielu deweloperów nie będzie się tym przejmować.  
  
## <a name="see-also"></a>Zobacz też

- [Omówienie programowania LINQ do XML (C#)](./linq-to-xml-overview.md)
