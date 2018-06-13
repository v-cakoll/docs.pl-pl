---
title: LINQ do osi XML (C#)
ms.date: 07/20/2015
ms.assetid: 3f7d54ff-b608-43a1-9e2d-e70668b72df8
ms.openlocfilehash: d12d35a6f9b02056946ba201a7bd5a961f64ba36
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33331493"
---
# <a name="linq-to-xml-axes-c"></a>LINQ do osi XML (C#)
Po drzewo XML utworzony lub załadowany dokumentu XML na drzewo XML można wykonać zapytanie, aby znaleźć elementy i atrybuty lub pobrać wartości.  
  
 Aby można było tworzyć kwerendy, należy zrozumieć [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] osi. Istnieją dwa rodzaje metody osi: najpierw istnieją metody, które wywołują w ramach jednej <xref:System.Xml.Linq.XElement> obiektu <xref:System.Xml.Linq.XDocument> obiekt, lub <xref:System.Xml.Linq.XNode> obiektu. Te metody działają na pojedynczy obiekt a zwracać kolekcji <xref:System.Xml.Linq.XElement>, <xref:System.Xml.Linq.XAttribute>, lub <xref:System.Xml.Linq.XNode> obiektów. Po drugie są metody rozszerzenia, które działają w kolekcjach i zwracać kolekcji. Metody rozszerzenia wyliczyć kolekcji źródłowej wywołać metodę odpowiednich osi dla każdego elementu w kolekcji i łączenie wyniki.  
  
## <a name="in-this-section"></a>W tej sekcji  
  
|Temat|Opis|  
|-----------|-----------------|  
|[LINQ do XML-Przegląd osie (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-axes-overview.md)|Definiuje osie oraz wyjaśniono, jak są używane w kontekście [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] zapytania.|  
|[Porady: pobierania kolekcję elementów (LINQ do XML) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-retrieve-a-collection-of-elements-linq-to-xml.md)|Wprowadza <xref:System.Xml.Linq.XContainer.Elements%2A> metody. Ta metoda pobiera kolekcję elementów podrzędnych danego elementu.|  
|[Porady: pobieranie wartości elementu (LINQ do XML) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-retrieve-the-value-of-an-element-linq-to-xml.md)|Pokazuje, jak można pobrać wartości elementów.|  
|[Porady: Filtr na nazwy elementów (LINQ do XML) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-filter-on-element-names-linq-to-xml.md)|Pokazuje, jak można filtrować według nazwy elementów przy użyciu osi.|  
|[Porady: łańcucha wywołań metody osi (LINQ do XML) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-chain-axis-method-calls-linq-to-xml.md)|Pokazuje, jak tworzyć łańcuchy wywołania metod osi.|  
|[Porady: Pobieranie elementu podrzędnego pojedynczego (LINQ do XML) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-retrieve-a-single-child-element-linq-to-xml.md)|Pokazuje, jak można pobrać elementu podrzędnego pojedynczego elementu, nazwę tagu elementu podrzędnego.|  
|[Porady: pobierania kolekcję atrybutów (LINQ do XML) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-retrieve-a-collection-of-attributes-linq-to-xml.md)|Wprowadza <xref:System.Xml.Linq.XElement.Attributes%2A> metody. Ta metoda pobiera atrybuty elementu.|  
|[Porady: pobieranie jeden atrybut (LINQ do XML) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-retrieve-a-single-attribute-linq-to-xml.md)|Pokazuje, jak pobrać jeden atrybut elementu jest podana nazwa atrybutu.|  
|[Porady: pobieranie wartości atrybutu (LINQ do XML) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-retrieve-the-value-of-an-attribute-linq-to-xml.md)|Pokazuje, jak można pobrać wartości atrybutów.|  
|[Porady: pobieranie skrócona wartość elementu (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-retrieve-the-shallow-value-of-an-element.md)|Pokazuje, jak pobrać pobieżną wartości elementu.|  
  
## <a name="see-also"></a>Zobacz też  
 [Metody rozszerzeń](../../../../csharp/programming-guide/classes-and-structs/extension-methods.md)  
 [Przewodnik programowania w języku (LINQ do XML) (C#)](../../../../csharp/programming-guide/concepts/linq/programming-guide-linq-to-xml.md)
