---
title: LINQ do osi XML (Visual Basic)
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ecd3bd00-28e5-4517-a59f-53bff39fd478
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 404ddcc89e6549d7575761e10c23413d9688a38f
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="linq-to-xml-axes-visual-basic"></a>LINQ do osi XML (Visual Basic)
Po drzewo XML utworzony lub załadowany dokumentu XML na drzewo XML można wykonać zapytanie, aby znaleźć elementy i atrybuty lub pobrać wartości.  
  
 Aby można było tworzyć kwerendy, należy zrozumieć [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] osi. Istnieją dwa rodzaje metody osi: najpierw istnieją metody, które wywołują w ramach jednej <xref:System.Xml.Linq.XElement> obiektu <xref:System.Xml.Linq.XDocument> obiekt, lub <xref:System.Xml.Linq.XNode> obiektu. Te metody działają na pojedynczy obiekt a zwracać kolekcji <xref:System.Xml.Linq.XElement>, <xref:System.Xml.Linq.XAttribute>, lub <xref:System.Xml.Linq.XNode> obiektów. Po drugie są metody rozszerzenia, które działają w kolekcjach i zwracać kolekcji. Metody rozszerzenia wyliczyć kolekcji źródłowej wywołać metodę odpowiednich osi dla każdego elementu w kolekcji i łączenie wyniki.  
  
## <a name="in-this-section"></a>W tej sekcji  
  
|Temat|Opis|  
|-----------|-----------------|  
|[LINQ do XML-Przegląd osie (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-axes-overview.md)|Definiuje osie oraz wyjaśniono, jak są używane w kontekście [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] zapytania.|  
|[Porady: pobierania kolekcję elementów (LINQ do XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-retrieve-a-collection-of-elements-linq-to-xml.md)|Wprowadza <xref:System.Xml.Linq.XContainer.Elements%2A> metody. Ta metoda pobiera kolekcję elementów podrzędnych danego elementu.|  
|[Porady: pobieranie wartości elementu (LINQ do XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-retrieve-the-value-of-an-element-linq-to-xml.md)|Pokazuje, jak można pobrać wartości elementów.|  
|[Porady: Filtr na nazwy elementów (LINQ do XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-filter-on-element-names-linq-to-xml.md)|Pokazuje, jak można filtrować według nazwy elementów przy użyciu osi.|  
|[Porady: łańcucha wywołań metody osi (LINQ do XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-chain-axis-method-calls-linq-to-xml.md)|Pokazuje, jak tworzyć łańcuchy wywołania metod osi.|  
|[Porady: Pobieranie elementu podrzędnego pojedynczego (LINQ do XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-retrieve-a-single-child-element-linq-to-xml.md)|Pokazuje, jak można pobrać elementu podrzędnego pojedynczego elementu, nazwę tagu elementu podrzędnego.|  
|[Porady: pobierania kolekcję atrybutów (LINQ do XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-retrieve-a-collection-of-attributes-linq-to-xml.md)|Wprowadza <xref:System.Xml.Linq.XElement.Attributes%2A> metody. Ta metoda pobiera atrybuty elementu.|  
|[Porady: pobieranie jeden atrybut (LINQ do XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-retrieve-a-single-attribute-linq-to-xml.md)|Pokazuje, jak pobrać jeden atrybut elementu jest podana nazwa atrybutu.|  
|[Porady: pobieranie wartości atrybutu (LINQ do XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-retrieve-the-value-of-an-attribute-linq-to-xml.md)|Pokazuje, jak można pobrać wartości atrybutów.|  
|[Porady: pobieranie skrócona wartość elementu (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-retrieve-the-shallow-value-of-an-element.md)|Pokazuje, jak pobrać pobieżną wartości elementu.|  
|[Języku zintegrowanym osi w języku Visual Basic (LINQ do XML)](../../../../visual-basic/programming-guide/concepts/linq/language-integrated-axes.md)|Zawiera podsumowanie osie zintegrowane w języku Visual Basic.|  
  
## <a name="see-also"></a>Zobacz też  
 [Przewodnik programowania w języku (LINQ do XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/programming-guide-linq-to-xml.md)
