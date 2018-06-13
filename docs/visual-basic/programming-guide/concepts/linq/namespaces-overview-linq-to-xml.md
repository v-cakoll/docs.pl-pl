---
title: Omówienie przestrzenie nazw (LINQ do XML)
ms.date: 07/20/2015
ms.assetid: b8eb31fa-4b26-4acf-8050-6e705687f458
ms.openlocfilehash: 0e8a3313a41338f28a225a6d94fe5a4eb5210b8a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33645892"
---
# <a name="namespaces-overview-linq-to-xml"></a>Omówienie przestrzenie nazw (LINQ do XML)
W tym temacie przedstawiono obszary nazw, <xref:System.Xml.Linq.XName> klasy, a <xref:System.Xml.Linq.XNamespace> klasy.  
  
## <a name="xml-names"></a>Nazwy XML  
 Nazwy XML często są źródłem złożoności programowania w języku XML. Nazwa XML składa się z przestrzeni nazw XML (nazywanych również identyfikator URI przestrzeni nazw XML) i nazwa lokalna. Obszar nazw XML jest podobny do przestrzeni nazw w [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]-programu. Umożliwia ona zakwalifikować unikatowej nazwy elementów i atrybutów. Dzięki temu można uniknąć konfliktów nazw między różnymi składnikami dokumentu XML. Po zadeklarowaniu przestrzeni nazw XML, można wybrać nazwę lokalną o tylko musi być unikatowa w obrębie tej przestrzeni nazw.  
  
 Innym aspektem nazw XML jest XML *prefiksy przestrzeni nazw*. Prefiksy XML, że większość złożoność nazwy XML. Tymi prefiksami umożliwiają tworzenie skrótu dla przestrzeni nazw XML, co sprawia, że dokument XML bardziej zwięzłe i zrozumienia. Jednak prefiksy XML w zależności od kontekstu ma znaczenie, który dodaje złożoności. Na przykład prefiks XML `aw` może być skojarzony z jedną przestrzeń nazw XML w jednej części drzewa XML oraz z różnych przestrzeni nazw XML w innej części drzewa XML.  
  
 Korzystając z [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] z literały Visual Basic i XML, należy użyć prefiksy przestrzeni nazw podczas pracy z dokumentami w przestrzeniach nazw.  
  
 W [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], jest klasa, która reprezentuje nazw XML <xref:System.Xml.Linq.XName>. Nazwy XML często są wyświetlane w całym [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] interfejsu API, i wszędzie tam, gdzie nazwa XML jest wymagana, można znaleźć <xref:System.Xml.Linq.XName> parametru. Jednak rzadko pracę bezpośrednio z <xref:System.Xml.Linq.XName>. <xref:System.Xml.Linq.XName> zawiera niejawna konwersja z ciągu.  
  
 Aby uzyskać więcej informacji, zobacz <xref:System.Xml.Linq.XNamespace> i <xref:System.Xml.Linq.XName>.  
  
## <a name="see-also"></a>Zobacz też  
 [Praca z przestrzeni nazw XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md)
