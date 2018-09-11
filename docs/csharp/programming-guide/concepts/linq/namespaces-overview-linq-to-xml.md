---
title: Przegląd przestrzeni nazw (LINQ to XML)
ms.date: 07/20/2015
ms.assetid: 16283322-8238-4918-ab11-802ac6748eb7
ms.openlocfilehash: 4d422d9f72eb3297cffda72c441d6370d519f450
ms.sourcegitcommit: 4b6490b2529707627ad77c3a43fbe64120397175
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2018
ms.locfileid: "44266657"
---
# <a name="namespaces-overview-linq-to-xml"></a>Przegląd przestrzeni nazw (LINQ to XML)
W tym temacie przedstawiono przestrzeni nazw, <xref:System.Xml.Linq.XName> klasy, a <xref:System.Xml.Linq.XNamespace> klasy.  
  
## <a name="xml-names"></a>Nazwy XML  
 Nazwy XML są często źródłem złożoności w programowaniu XML. Nazwa XML składa się z przestrzeni nazw XML (nazywane również identyfikator URI przestrzeni nazw XML) i lokalna nazwa. Przestrzeń nazw XML jest podobny do przestrzeni nazw w [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]— na podstawie programu. Pozwala ona jednoznacznie kwalifikowania nazwy elementów i atrybutów. Pomaga to uniknąć konfliktów nazw między różne części dokumentu XML. Jeśli zadeklarowano nazw XML, można wybrać nazwę lokalną o tylko musi być unikatowa w obrębie tej przestrzeni nazw.  
  
 Innym aspektem nazw XML jest XML *prefiksy przestrzeni nazw*. Prefiksy XML spowodować, że większość złożoność nazwy XML. Prefiksy te umożliwiają tworzenie skrótów dla przestrzeni nazw XML, co sprawia, że dokument XML bardziej zwięzłe i zrozumiałe. Jednak prefiksy XML w zależności od kontekstu ma znaczenie, które zwiększa złożoność. Na przykład prefiks XML `aw` może być skojarzony z jedną przestrzeń nazw XML w jednej części drzewa XML oraz z innej przestrzeni nazw XML w innej części drzewa XML.  
  
 Jedną z zalet funkcji [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] przy użyciu języka C# jest, że nie trzeba używać prefiksów XML. Gdy [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] ładuje lub analizuje dokument XML prefiksu dla każdego XML nie zostanie rozwiązany do jego odpowiedniej przestrzeni nazw XML. Po tym podczas pracy z dokumentu, który używa przestrzeni nazw, należy prawie zawsze dostęp do przestrzeni nazw za pomocą identyfikatora URI obszaru nazw, a nie przy użyciu prefiksu przestrzeni nazw. Gdy deweloperzy pracują z nazwami XML w [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] zawsze pracują z w pełni kwalifikowana nazwa XML (czyli przestrzeni nazw XML i lokalna nazwa). Jednakże, gdy jest to konieczne, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] umożliwia pracę i kontrolowanie prefiksów przestrzeni nazw.  
  
 W [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], klasa, która reprezentuje nazwy XML jest <xref:System.Xml.Linq.XName>. Nazwy XML są często widoczne w całym [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] interfejsu API i wszędzie tam, gdzie nazwa XML jest wymagana, można znaleźć <xref:System.Xml.Linq.XName> parametru. Jednak rzadko pracę bezpośrednio z <xref:System.Xml.Linq.XName>. <xref:System.Xml.Linq.XName> zawiera niejawną konwersję z ciągu.  
  
 Aby uzyskać więcej informacji, zobacz <xref:System.Xml.Linq.XNamespace> i <xref:System.Xml.Linq.XName>.  
  
## <a name="see-also"></a>Zobacz też

- [Praca z przestrzeniami nazw XML (C#)](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md)
