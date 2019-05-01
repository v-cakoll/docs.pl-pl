---
title: XAttribute klasa — Przegląd (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 7781580a-9583-4a1b-ae1e-91c5936eb0b1
ms.openlocfilehash: 6b24f429a69067f6af1a61efe4102a5638db3031
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61907455"
---
# <a name="xattribute-class-overview-visual-basic"></a>XAttribute klasa — Przegląd (Visual Basic)
Atrybuty są pary nazwa/wartość, które są skojarzone z elementem. <xref:System.Xml.Linq.XAttribute> Klasa reprezentuje atrybutów XML.  
  
## <a name="overview"></a>Omówienie  
 Praca z atrybutów w [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] jest podobna do pracy z elementami. Ich konstruktory są podobne. Metody używane do pobierania kolekcji z nich są podobne. A [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] wyrażenia zapytania dla kolekcji atrybutów wygląda bardzo podobnie do [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] wyrażeniu kolekcji elementy zapytania.  
  
 Kolejność, w którym atrybuty zostały dodane do elementu są zachowywane. Oznacza to, że podczas iteracji atrybuty zobaczysz je w tej samej kolejności, czy zostały dodane.  
  
## <a name="the-xattribute-constructor"></a>Konstruktor XAttribute  
 Następujący Konstruktor <xref:System.Xml.Linq.XAttribute> klasy jest tą, która będzie najczęściej używać:  
  
|Konstruktor|Opis|  
|-----------------|-----------------|  
|`XAttribute(XName name, object content)`|Tworzy <xref:System.Xml.Linq.XAttribute> obiektu. `name` Argument określa nazwę atrybutu; `content` określa wartość tego atrybutu.|  
  
### <a name="creating-an-element-with-an-attribute"></a>Tworzenie elementu za pomocą atrybutu  
 Poniższy kod pokazuje element zawierający atrybut przy użyciu literałów XML w Visual Basic:  
  
```vb  
Dim phone As XElement = <Phone Type="Home">555-555-5555</Phone>  
Console.WriteLine(phone)  
```  
  
 Ten przykład generuje następujące wyniki:  
  
```xml  
<Phone Type="Home">555-555-5555</Phone>  
```  
  
### <a name="functional-construction-of-attributes"></a>Konstrukcja funkcjonalna atrybutów  
 Można skonstruować <xref:System.Xml.Linq.XAttribute> obiektów w tekście za pomocą konstrukcji <xref:System.Xml.Linq.XElement> obiektów w następujący sposób:  
  
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
 Istnieją pewne różnice między atrybuty i elementy. <xref:System.Xml.Linq.XAttribute> obiekty nie są węzłów w drzewie XML. Są one pary nazwa/wartość skojarzona z elementem XML. W przeciwieństwie do modelu DOM (Document Object), to lepiej odzwierciedla struktury XML. Mimo że <xref:System.Xml.Linq.XAttribute> obiekty nie są faktycznie węzłów w drzewie XML, Praca z <xref:System.Xml.Linq.XAttribute> obiektów jest bardzo podobny do pracy z <xref:System.Xml.Linq.XElement> obiektów.  
  
 Wykonywania tego rozróżnienia jest szczególnie ważne tylko dla deweloperów, którzy są pisanie kodu, który współdziała z drzew XML na poziomie węzła. Nie są związani z wykonywania tego rozróżnienia wielu deweloperów.  
  
## <a name="see-also"></a>Zobacz także

- [LINQ to XML — przegląd programowania (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-programming-overview.md)
