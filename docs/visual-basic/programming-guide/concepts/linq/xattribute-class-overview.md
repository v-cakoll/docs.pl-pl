---
title: XAttribute, klasa — przegląd
ms.date: 07/20/2015
ms.assetid: 7781580a-9583-4a1b-ae1e-91c5936eb0b1
ms.openlocfilehash: ceafe5478e41fb4c2038fd9300ef7b1ee6cb8411
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/03/2020
ms.locfileid: "75636656"
---
# <a name="xattribute-class-overview-visual-basic"></a>Przegląd klasy XAttribute (Visual Basic)
Atrybuty są parami nazw/wartości, które są skojarzone z elementem. Klasa <xref:System.Xml.Linq.XAttribute> reprezentuje atrybuty XML.  
  
## <a name="overview"></a>Omówienie  
 Praca z atrybutami w [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] jest podobna do pracy z elementami. Ich konstruktory są podobne. Metody używane do pobierania kolekcji są podobne. Wyrażenie zapytania LINQ dla kolekcji atrybutów wygląda bardzo podobnie do wyrażenia zapytania LINQ dla kolekcji elementów.  
  
 Kolejność, w jakiej atrybuty zostały dodane do elementu, jest zachowywana. Oznacza to, że podczas iteracji przez atrybuty są one widoczne w takiej samej kolejności, w jakiej zostały dodane.  
  
## <a name="the-xattribute-constructor"></a>Konstruktor XAttribute  
 Następujący Konstruktor klasy <xref:System.Xml.Linq.XAttribute> jest najczęściej używanym:  
  
|Konstruktor|Opis|  
|-----------------|-----------------|  
|`XAttribute(XName name, object content)`|Tworzy <xref:System.Xml.Linq.XAttribute> obiektu. `name` argument określa nazwę atrybutu; `content` określa zawartość atrybutu.|  
  
### <a name="creating-an-element-with-an-attribute"></a>Tworzenie elementu z atrybutem  
 Poniższy kod przedstawia element, który zawiera atrybut używając literałów XML w Visual Basic:  
  
```vb  
Dim phone As XElement = <Phone Type="Home">555-555-5555</Phone>  
Console.WriteLine(phone)  
```  
  
 Ten przykład generuje następujące wyniki:  
  
```xml  
<Phone Type="Home">555-555-5555</Phone>  
```  
  
### <a name="functional-construction-of-attributes"></a>Funkcjonalne konstruowanie atrybutów  
 Można konstruować <xref:System.Xml.Linq.XAttribute> obiektów w wierszu z konstrukcją obiektów <xref:System.Xml.Linq.XElement> w następujący sposób:  
  
```vb  
Dim c As XElement = _  
    <Customers>  
        <Customer>  
            <Name>John Doe</Name>  
            <PhoneNumbers>  
                <Phone type="home">555-555-5555</Phone>  
                <Phone type="work">666-666-6666</Phone>  
            </PhoneNumbers>  
        </Customer>  
    </Customers>  
Console.WriteLine(c)  
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
 Istnieją pewne różnice między atrybutami i elementami. obiekty <xref:System.Xml.Linq.XAttribute> nie są węzłami w drzewie XML. Są to pary nazw/wartości skojarzone z elementem XML. W przeciwieństwie do Document Object Model (DOM), to dokładniej odzwierciedla strukturę XML. Chociaż obiekty <xref:System.Xml.Linq.XAttribute> nie są w rzeczywistości węzłami w drzewie XML, praca z obiektami <xref:System.Xml.Linq.XAttribute> jest bardzo podobna do pracy z obiektami <xref:System.Xml.Linq.XElement>.  
  
 Ta różnica jest głównie ważna tylko dla deweloperów, którzy piszą kod, który współpracuje z drzewami XML na poziomie węzła. Wielu deweloperów nie będą zainteresowani tym rozróżnieniem.  
  
## <a name="see-also"></a>Zobacz także

- [Omówienie programowania LINQ to XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-programming-overview.md)
