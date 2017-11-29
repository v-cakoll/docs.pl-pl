---
title: "Omówienie przestrzenie nazw (LINQ do XML)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 16283322-8238-4918-ab11-802ac6748eb7
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: d2aa60f10e9d4cf1b1db4d2e81d94e5ea8e1302a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="namespaces-overview-linq-to-xml"></a>Omówienie przestrzenie nazw (LINQ do XML)
W tym temacie przedstawiono obszary nazw, <xref:System.Xml.Linq.XName> klasy, a <xref:System.Xml.Linq.XNamespace> klasy.  
  
## <a name="xml-names"></a>Nazwy XML  
 Nazwy XML często są źródłem złożoności programowania w języku XML. Nazwa XML składa się z przestrzeni nazw XML (nazywanych również identyfikator URI przestrzeni nazw XML) i nazwa lokalna. Obszar nazw XML jest podobny do przestrzeni nazw w [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]-programu. Umożliwia ona zakwalifikować unikatowej nazwy elementów i atrybutów. Dzięki temu można uniknąć konfliktów nazw między różnymi składnikami dokumentu XML. Po zadeklarowaniu przestrzeni nazw XML, można wybrać nazwę lokalną o tylko musi być unikatowa w obrębie tej przestrzeni nazw.  
  
 Innym aspektem nazw XML jest XML *prefiksy przestrzeni nazw*. Prefiksy XML, że większość złożoność nazwy XML. Tymi prefiksami umożliwiają tworzenie skrótu dla przestrzeni nazw XML, co sprawia, że dokument XML bardziej zwięzłe i zrozumienia. Jednak prefiksy XML w zależności od kontekstu ma znaczenie, który dodaje złożoności. Na przykład prefiks XML `aw` może być skojarzony z jedną przestrzeń nazw XML w jednej części drzewa XML oraz z różnych przestrzeni nazw XML w innej części drzewa XML.  
  
 Jedną z zalet funkcji [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] języku C# jest, że nie trzeba używać prefiksów XML. Gdy [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] ładuje lub analizuje dokument XML prefiksami XML nie zostanie rozwiązany do jego odpowiedniej przestrzeni nazw XML. Po wykonaniu tej podczas pracy z dokumentu, który używa przestrzeni nazw, możesz prawie zawsze dostęp do przestrzeni nazw przez identyfikator URI przestrzeni nazw, a nie przez prefiks przestrzeni nazw. Podczas pracy deweloperów z nazw XML w [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] zawsze pracują z nazwą XML pełną (to, że przestrzeń nazw XML i nazwa lokalna). Jednakże, gdy jest to konieczne, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] służy do pracy z i kontrolować prefiksy przestrzeni nazw.  
  
 W [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], jest klasa, która reprezentuje nazw XML <xref:System.Xml.Linq.XName>. Nazwy XML często są wyświetlane w całym [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] interfejsu API, i wszędzie tam, gdzie nazwa XML jest wymagana, można znaleźć <xref:System.Xml.Linq.XName> parametru. Jednak rzadko pracę bezpośrednio z <xref:System.Xml.Linq.XName>. <xref:System.Xml.Linq.XName>zawiera niejawna konwersja z ciągu.  
  
 Aby uzyskać więcej informacji, zobacz <xref:System.Xml.Linq.XNamespace> i <xref:System.Xml.Linq.XName>.  
  
## <a name="see-also"></a>Zobacz też  
 [Praca z przestrzeni nazw XML (C#)](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md)
