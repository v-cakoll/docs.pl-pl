---
title: Przegląd przestrzeni nazw (LINQ to XML)
ms.date: 07/20/2015
ms.assetid: b8eb31fa-4b26-4acf-8050-6e705687f458
ms.openlocfilehash: bd83a423c8fd19506c5d23ea308bb56cced6ca93
ms.sourcegitcommit: eb9ff6f364cde6f11322e03800d8f5ce302f3c73
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/01/2019
ms.locfileid: "68710550"
---
# <a name="namespaces-overview-linq-to-xml"></a>Przegląd przestrzeni nazw (LINQ to XML)

Ten temat zawiera wprowadzenie do <xref:System.Xml.Linq.XName> przestrzeni nazw, klasy <xref:System.Xml.Linq.XNamespace> i klasy.  
  
## <a name="xml-names"></a>Nazwy XML  

Nazwy XML często są źródłem złożoności w programowaniu XML. Nazwa XML składa się z przestrzeni nazw XML (nazywanej również identyfikatorem URI przestrzeni nazw XML) i nazwy lokalnej. Przestrzeń nazw XML jest podobna do przestrzeni nazw w programie opartym na .NET Framework. Umożliwia ona unikatową kwalifikowanie nazw elementów i atrybutów. Pozwala to uniknąć konfliktów nazw między różnymi częściami dokumentu XML. Po zadeklarowaniu przestrzeni nazw XML można wybrać lokalną nazwę, która musi być unikatowa w obrębie tej przestrzeni nazw.  
  
 Innym aspektem nazw XML są *prefiksy przestrzeni nazw*XML. Prefiksy XML powodują większość złożoności nazw XML. Te prefiksy umożliwiają utworzenie skrótu dla przestrzeni nazw XML, co sprawia, że dokument XML jest bardziej zwięzły i zrozumiały. Jednak prefiksy XML są zależne od ich kontekstu, które mają znaczenie, co zwiększa złożoność. Na przykład prefiks `aw` XML może być skojarzony z jedną przestrzenią nazw XML w jednej części drzewa XML i z inną przestrzenią nazw XML w innej części drzewa XML.  
  
W przypadku [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] używania z Visual Basic i literałów XML należy używać prefiksów przestrzeni nazw podczas pracy z dokumentami w przestrzeni nazw.  
  
W [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]programie Klasa, która reprezentuje nazwy XML, <xref:System.Xml.Linq.XName>to. Nazwy XML często [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] pojawiają się w interfejsie API i wszędzie tam, gdzie jest wymagana nazwa XML, <xref:System.Xml.Linq.XName> parametr zostanie znaleziony. Jednak rzadko pracujemy bezpośrednio z <xref:System.Xml.Linq.XName>. <xref:System.Xml.Linq.XName>zawiera niejawną konwersję z ciągu.  
  
Aby uzyskać więcej informacji, zobacz <xref:System.Xml.Linq.XNamespace> i <xref:System.Xml.Linq.XName>.
