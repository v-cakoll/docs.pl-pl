---
title: LINQ do osi XML (Visual Basic)
ms.date: 07/20/2015
ms.assetid: ecd3bd00-28e5-4517-a59f-53bff39fd478
ms.openlocfilehash: 23feaf0aee66002a59279a49192ad459afc682aa
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/26/2018
ms.locfileid: "42930135"
---
# <a name="linq-to-xml-axes-visual-basic"></a>LINQ do osi XML (Visual Basic)
Po drzewa XML utworzone lub ładowany dokument XML do drzewa XML można tworzyć zapytania, do znajdowania elementów i atrybutów i pobierania ich wartości.  
  
 Aby można było tworzyć żadnych zapytań, należy zrozumieć [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] osi. Istnieją dwa rodzaje metod osi: po pierwsze, istnieją metody, które wywołują na pojedynczym <xref:System.Xml.Linq.XElement> obiektu, <xref:System.Xml.Linq.XDocument> obiektu lub <xref:System.Xml.Linq.XNode> obiektu. Te metody działają na pojedynczy obiekt i zwracają zbiór <xref:System.Xml.Linq.XElement>, <xref:System.Xml.Linq.XAttribute>, lub <xref:System.Xml.Linq.XNode> obiektów. Po drugie są metody rozszerzenia, które działają na kolekcji i zwracają kolekcje. Metody rozszerzenia wyliczania kolekcji źródłowej, wywołać metodę odpowiednich osi dla każdego elementu w kolekcji, a następnie łączenie wyników.  
  
## <a name="in-this-section"></a>W tej sekcji  
  
|Temat|Opis|  
|-----------|-----------------|  
|[LINQ to XML — Przegląd osi (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-axes-overview.md)|Definiuje osi i wyjaśniono, jak są używane w kontekście [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] zapytania.|  
|[Porady: pobieranie kolekcji elementów (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-retrieve-a-collection-of-elements-linq-to-xml.md)|Wprowadza <xref:System.Xml.Linq.XContainer.Elements%2A> metody. Ta metoda pobiera kolekcję elementów podrzędnych elementu.|  
|[Porady: pobieranie wartości elementu (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-retrieve-the-value-of-an-element-linq-to-xml.md)|Pokazuje, jak można pobrać wartości elementów.|  
|[Porady: filtrowanie nazw elementów (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-filter-on-element-names-linq-to-xml.md)|Pokazuje, jak filtrowanie nazw elementów, gdy za pomocą osi.|  
|[Jak: utworzyć łańcuch wywołań metody osi (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-chain-axis-method-calls-linq-to-xml.md)|Pokazuje, jak połączyć w łańcuch wywołań metody osi.|  
|[Porady: pobieranie jeden typ elementów podrzędnych (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-retrieve-a-single-child-element-linq-to-xml.md)|Pokazuje, jak pobrać jeden typ elementów podrzędnych elementu, otrzymuje nazwę tagu elementu podrzędnego.|  
|[Porady: pobieranie kolekcji atrybutów (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-retrieve-a-collection-of-attributes-linq-to-xml.md)|Wprowadza <xref:System.Xml.Linq.XElement.Attributes%2A> metody. Ta metoda pobiera atrybuty elementu.|  
|[Porady: pobieranie pojedynczego atrybutu (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-retrieve-a-single-attribute-linq-to-xml.md)|Pokazuje, jak pobieranie pojedynczego atrybutu elementu, otrzymuje nazwę atrybutu.|  
|[Porady: pobieranie wartości atrybutu (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-retrieve-the-value-of-an-attribute-linq-to-xml.md)|Pokazuje, jak można pobrać wartości atrybutów.|  
|[Porady: pobieranie płytkiej wartości elementu (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-retrieve-the-shallow-value-of-an-element.md)|Pokazuje, jak pobieranie płytkiej wartości elementu.|  
|[Osie o języku zintegrowanym w języku Visual Basic (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/language-integrated-axes.md)|Zawiera podsumowanie osi zintegrowane w języku Visual Basic.|  
  
## <a name="see-also"></a>Zobacz też  
 [Przewodnik programowania (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/programming-guide-linq-to-xml.md)
