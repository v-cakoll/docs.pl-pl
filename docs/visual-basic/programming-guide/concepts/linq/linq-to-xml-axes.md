---
title: Osie LINQ to XML
ms.date: 07/20/2015
ms.assetid: ecd3bd00-28e5-4517-a59f-53bff39fd478
ms.openlocfilehash: 73c5325c23c4724a28a123af5c2f8c25b2fd02de
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352021"
---
# <a name="linq-to-xml-axes-visual-basic"></a>Osie LINQ to XML (Visual Basic)
Po utworzeniu drzewa XML lub załadowaniu dokumentu XML do drzewa XML można wykonać zapytania do niego, aby znaleźć elementy i atrybuty i pobrać ich wartości.  
  
 Przed zapisaniem jakichkolwiek zapytań należy zrozumieć [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] osi. Istnieją dwa rodzaje metod osi: najpierw istnieją metody, które są wywoływane na pojedynczym obiekcie <xref:System.Xml.Linq.XElement>, <xref:System.Xml.Linq.XDocument> obiektu lub <xref:System.Xml.Linq.XNode> obiektu. Metody te działają na pojedynczym obiekcie i zwracają kolekcję obiektów <xref:System.Xml.Linq.XElement>, <xref:System.Xml.Linq.XAttribute>lub <xref:System.Xml.Linq.XNode>. Następnie istnieją metody rozszerzające, które działają na kolekcjach i kolekcjach zwracanych. Metody rozszerzające wyliczają kolekcję źródłową, wywołują odpowiednią metodę osi dla każdego elementu w kolekcji i łączą wyniki.  
  
## <a name="in-this-section"></a>W tej sekcji  
  
|Temat|Opis|  
|-----------|-----------------|  
|[Przegląd osi LINQ to XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-axes-overview.md)|Definiuje osie i wyjaśnia, jak są używane w kontekście zapytań [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].|  
|[Instrukcje: pobieranie kolekcji elementów (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-retrieve-a-collection-of-elements-linq-to-xml.md)|Wprowadza metodę <xref:System.Xml.Linq.XContainer.Elements%2A>. Ta metoda pobiera kolekcję elementów podrzędnych elementu.|  
|[Instrukcje: pobieranie wartości elementu (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-retrieve-the-value-of-an-element-linq-to-xml.md)|Pokazuje, jak pobrać wartości elementów.|  
|[Instrukcje: filtrowanie nazw elementów (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-filter-on-element-names-linq-to-xml.md)|Pokazuje, jak filtrować nazwy elementów przy użyciu osi.|  
|[Instrukcje: wywołania metody osi łańcuchowej (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-chain-axis-method-calls-linq-to-xml.md)|Pokazuje sposób łańcucha wywołań metod osi.|  
|[Instrukcje: Pobieranie pojedynczego elementu podrzędnego (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-retrieve-a-single-child-element-linq-to-xml.md)|Pokazuje, jak pobrać pojedynczy element podrzędny elementu, pod nazwą tagu elementu podrzędnego.|  
|[Instrukcje: pobieranie kolekcji atrybutów (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-retrieve-a-collection-of-attributes-linq-to-xml.md)|Wprowadza metodę <xref:System.Xml.Linq.XElement.Attributes%2A>. Ta metoda pobiera atrybuty elementu.|  
|[Instrukcje: Pobieranie pojedynczego atrybutu (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-retrieve-a-single-attribute-linq-to-xml.md)|Pokazuje, jak pobrać pojedynczy atrybut elementu, pod nazwą atrybutu.|  
|[Instrukcje: pobieranie wartości atrybutu (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-retrieve-the-value-of-an-attribute-linq-to-xml.md)|Pokazuje, jak pobrać wartości atrybutów.|  
|[Instrukcje: pobieranie płytki wartości elementu (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-retrieve-the-shallow-value-of-an-element.md)|Pokazuje, jak pobrać skróconą wartość elementu.|  
|[Osie zintegrowane z językiem w Visual Basic (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/language-integrated-axes.md)|Podsumowuje Visual Basic osi zintegrowanych.|  
  
## <a name="see-also"></a>Zobacz także

- [Przewodnik programowania (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/programming-guide-linq-to-xml.md)
