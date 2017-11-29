---
title: "Przegląd klasy XAttribute (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 5a630f24-f9ad-400e-831e-c14ebfc9e142
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: e9cfedb476f44ef8c3eaeb45bac571d17802d525
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="xattribute-class-overview-c"></a>Przegląd klasy XAttribute (C#)
Atrybuty są pary nazwa/wartość, które są skojarzone z elementem. <xref:System.Xml.Linq.XAttribute> Klasa reprezentuje atrybuty XML.  
  
## <a name="overview"></a>Omówienie  
 Praca z atrybutów w [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] jest podobna do pracy z elementami. Ich konstruktory są podobne. Metody używane do pobierania kolekcji z nich są podobne. A [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] wygląda bardzo podobnie do wyrażenia zapytania dla kolekcji atrybutów [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] zapytania wyrażenie nie zawiera kolekcję elementów.  
  
 Kolejność, w którym atrybuty zostały dodane do elementu są zachowywane. Oznacza to, że podczas iteracji atrybuty wyświetlanych w tej samej kolejności, że zostały one dodane.  
  
## <a name="the-xattribute-constructor"></a>Konstruktor XAttribute  
 Następujące konstruktora <xref:System.Xml.Linq.XAttribute> klasy jest najczęściej używaną:  
  
|Konstruktor|Opis|  
|-----------------|-----------------|  
|`XAttribute(XName name, object content)`|Tworzy <xref:System.Xml.Linq.XAttribute> obiektu. `name` Argument określa nazwę atrybutu; `content` określa zawartości atrybutu.|  
  
### <a name="creating-an-element-with-an-attribute"></a>Tworzenie elementu za pomocą atrybutu  
 Poniższy kod przedstawia typowych zadań tworzenia elementu zawierającego atrybut:  
  
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
  
### <a name="functional-construction-of-attributes"></a>Konstrukcja funkcjonalności atrybutów  
 Można utworzyć <xref:System.Xml.Linq.XAttribute> wiersza z konstrukcji obiektów <xref:System.Xml.Linq.XElement> obiekty w następujący sposób:  
  
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
 Istnieją pewne różnice między atrybuty i elementy. <xref:System.Xml.Linq.XAttribute>obiekty nie są węzłów w drzewie XML. Są one pary nazwa/wartość skojarzona z elementem XML. W przeciwieństwie do modelu DOM (Document Object), to lepiej odzwierciedla struktury XML. Mimo że <xref:System.Xml.Linq.XAttribute> obiekty nie są faktycznie węzłów w drzewie XML, Praca z <xref:System.Xml.Linq.XAttribute> obiektów jest bardzo podobny do pracy z <xref:System.Xml.Linq.XElement> obiektów.  
  
 Ta różnica jest głównie istotne tylko dla deweloperów, którzy pisania kodu, który działa z drzewa XML na poziomie węzła. Nie są związane z tym rozróżnienia wielu deweloperów.  
  
## <a name="see-also"></a>Zobacz też  
 [LINQ do XML-przegląd programowania w języku (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-programming-overview.md)
