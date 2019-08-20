---
title: XAttribute — Omówienie klasyC#()
ms.date: 07/20/2015
ms.assetid: 5a630f24-f9ad-400e-831e-c14ebfc9e142
ms.openlocfilehash: 79ef00aa79be0c743423cfba1a911b238ff9a7ca
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69590928"
---
# <a name="xattribute-class-overview-c"></a>XAttribute — Omówienie klasyC#()
Atrybuty są parami nazw/wartości, które są skojarzone z elementem. <xref:System.Xml.Linq.XAttribute> Klasa reprezentuje atrybuty XML.  
  
## <a name="overview"></a>Omówienie  
 Praca z atrybutami [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] w jest podobna do pracy z elementami. Ich konstruktory są podobne. Metody używane do pobierania kolekcji są podobne. Wyrażenie zapytania dla kolekcji atrybutów wygląda bardzo podobnie [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] do wyrażenia zapytania dla kolekcji elementów. [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]  
  
 Kolejność, w jakiej atrybuty zostały dodane do elementu, jest zachowywana. Oznacza to, że podczas iteracji przez atrybuty są one widoczne w takiej samej kolejności, w jakiej zostały dodane.  
  
## <a name="the-xattribute-constructor"></a>Konstruktor XAttribute  
 Następujący Konstruktor <xref:System.Xml.Linq.XAttribute> klasy jest najczęściej używanym:  
  
|Konstruktor|Opis|  
|-----------------|-----------------|  
|`XAttribute(XName name, object content)`|Tworzy <xref:System.Xml.Linq.XAttribute> obiektu. `name` Argument określa nazwę atrybutu; `content` określa zawartość atrybutu.|  
  
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
  
### <a name="functional-construction-of-attributes"></a>Funkcjonalne konstruowanie atrybutów  
 Można tworzyć <xref:System.Xml.Linq.XAttribute> obiekty w wierszu z <xref:System.Xml.Linq.XElement> konstrukcją obiektów w następujący sposób:  
  
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
 Istnieją pewne różnice między atrybutami i elementami. <xref:System.Xml.Linq.XAttribute>obiekty nie są węzłami w drzewie XML. Są to pary nazw/wartości skojarzone z elementem XML. W przeciwieństwie do Document Object Model (DOM), to dokładniej odzwierciedla strukturę XML. Chociaż <xref:System.Xml.Linq.XAttribute> obiekty nie są w rzeczywistości węzłami w drzewie XML, praca <xref:System.Xml.Linq.XAttribute> z obiektami jest bardzo podobna do pracy <xref:System.Xml.Linq.XElement> z obiektami.  
  
 Ta różnica jest głównie ważna tylko dla deweloperów, którzy piszą kod, który współpracuje z drzewami XML na poziomie węzła. Wielu deweloperów nie będą zainteresowani tym rozróżnieniem.  
  
## <a name="see-also"></a>Zobacz także

- [Omówienie programowania LINQ to XML (C#)](./linq-to-xml-overview.md)
