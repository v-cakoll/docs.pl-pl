---
title: Przegląd przestrzeni nazw (LINQ to XML)
ms.date: 07/20/2015
ms.assetid: b8eb31fa-4b26-4acf-8050-6e705687f458
ms.openlocfilehash: b2ea4c28fe14e57d3f72bb29d4960f436bbd9bb9
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54603710"
---
# <a name="namespaces-overview-linq-to-xml"></a>Przegląd przestrzeni nazw (LINQ to XML)
W tym temacie przedstawiono przestrzeni nazw, <xref:System.Xml.Linq.XName> klasy, a <xref:System.Xml.Linq.XNamespace> klasy.  
  
## <a name="xml-names"></a>Nazwy XML  
 Nazwy XML są często źródłem złożoności w programowaniu XML. Nazwa XML składa się z przestrzeni nazw XML (nazywane również identyfikator URI przestrzeni nazw XML) i lokalna nazwa. Przestrzeń nazw XML jest podobny do przestrzeni nazw w [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]— na podstawie programu. Pozwala ona jednoznacznie kwalifikowania nazwy elementów i atrybutów. Pomaga to uniknąć konfliktów nazw między różne części dokumentu XML. Jeśli zadeklarowano nazw XML, można wybrać nazwę lokalną o tylko musi być unikatowa w obrębie tej przestrzeni nazw.  
  
 Innym aspektem nazw XML jest XML *prefiksy przestrzeni nazw*. Prefiksy XML spowodować, że większość złożoność nazwy XML. Prefiksy te umożliwiają tworzenie skrótów dla przestrzeni nazw XML, co sprawia, że dokument XML bardziej zwięzłe i zrozumiałe. Jednak prefiksy XML w zależności od kontekstu ma znaczenie, które zwiększa złożoność. Na przykład prefiks XML `aw` może być skojarzony z jedną przestrzeń nazw XML w jednej części drzewa XML oraz z innej przestrzeni nazw XML w innej części drzewa XML.  
  
 Korzystając z [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] z literałami Visual Basic i XML, należy użyć prefiksy przestrzeni nazw, podczas pracy z dokumentami w przestrzeniach nazw.  
  
 W [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], klasa, która reprezentuje nazwy XML jest <xref:System.Xml.Linq.XName>. Nazwy XML są często widoczne w całym [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] interfejsu API i wszędzie tam, gdzie nazwa XML jest wymagana, można znaleźć <xref:System.Xml.Linq.XName> parametru. Jednak rzadko pracę bezpośrednio z <xref:System.Xml.Linq.XName>. <xref:System.Xml.Linq.XName> zawiera niejawną konwersję z ciągu.  
  
 Aby uzyskać więcej informacji, zobacz <xref:System.Xml.Linq.XNamespace> i <xref:System.Xml.Linq.XName>.  
  
## <a name="see-also"></a>Zobacz także
- [Praca z przestrzeniami nazw XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md)
