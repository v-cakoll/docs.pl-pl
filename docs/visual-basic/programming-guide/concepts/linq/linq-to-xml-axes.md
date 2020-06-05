---
title: Osie LINQ to XML
ms.date: 07/20/2015
ms.assetid: ecd3bd00-28e5-4517-a59f-53bff39fd478
ms.openlocfilehash: 757c765062b1d1ca1cddb0c559fa46ef6a0fe796
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84368988"
---
# <a name="linq-to-xml-axes-visual-basic"></a>Osie LINQ to XML (Visual Basic)
Po utworzeniu drzewa XML lub załadowaniu dokumentu XML do drzewa XML można wykonać zapytania do niego, aby znaleźć elementy i atrybuty i pobrać ich wartości.  
  
 Przed zapisaniem jakichkolwiek zapytań należy zrozumieć [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] osie. Istnieją dwa rodzaje metod osi: najpierw istnieją metody, które są wywoływane dla pojedynczego <xref:System.Xml.Linq.XElement> obiektu, <xref:System.Xml.Linq.XDocument> obiektu lub <xref:System.Xml.Linq.XNode> obiektu. Metody te działają na pojedynczym obiekcie i zwracają kolekcję <xref:System.Xml.Linq.XElement> <xref:System.Xml.Linq.XAttribute> obiektów, lub <xref:System.Xml.Linq.XNode> . Następnie istnieją metody rozszerzające, które działają na kolekcjach i kolekcjach zwracanych. Metody rozszerzające wyliczają kolekcję źródłową, wywołują odpowiednią metodę osi dla każdego elementu w kolekcji i łączą wyniki.  
  
## <a name="in-this-section"></a>W tej sekcji  
  
|Temat|Opis|  
|-----------|-----------------|  
|[Przegląd osi LINQ to XML (Visual Basic)](linq-to-xml-axes-overview.md)|Definiuje osie i wyjaśnia, jak są używane w kontekście [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] zapytań.|  
|[Instrukcje: pobieranie kolekcji elementów (LINQ to XML) (Visual Basic)](how-to-retrieve-a-collection-of-elements-linq-to-xml.md)|Wprowadza <xref:System.Xml.Linq.XContainer.Elements%2A> metodę. Ta metoda pobiera kolekcję elementów podrzędnych elementu.|  
|[Instrukcje: pobieranie wartości elementu (LINQ to XML) (Visual Basic)](how-to-retrieve-the-value-of-an-element-linq-to-xml.md)|Pokazuje, jak pobrać wartości elementów.|  
|[Instrukcje: filtrowanie nazw elementów (LINQ to XML) (Visual Basic)](how-to-filter-on-element-names-linq-to-xml.md)|Pokazuje, jak filtrować nazwy elementów przy użyciu osi.|  
|[Instrukcje: wywołania metody osi łańcuchowej (LINQ to XML) (Visual Basic)](how-to-chain-axis-method-calls-linq-to-xml.md)|Pokazuje sposób łańcucha wywołań metod osi.|  
|[Instrukcje: Pobieranie pojedynczego elementu podrzędnego (LINQ to XML) (Visual Basic)](how-to-retrieve-a-single-child-element-linq-to-xml.md)|Pokazuje, jak pobrać pojedynczy element podrzędny elementu, pod nazwą tagu elementu podrzędnego.|  
|[Instrukcje: pobieranie kolekcji atrybutów (LINQ to XML) (Visual Basic)](how-to-retrieve-a-collection-of-attributes-linq-to-xml.md)|Wprowadza <xref:System.Xml.Linq.XElement.Attributes%2A> metodę. Ta metoda pobiera atrybuty elementu.|  
|[Instrukcje: Pobieranie pojedynczego atrybutu (LINQ to XML) (Visual Basic)](how-to-retrieve-a-single-attribute-linq-to-xml.md)|Pokazuje, jak pobrać pojedynczy atrybut elementu, pod nazwą atrybutu.|  
|[Instrukcje: pobieranie wartości atrybutu (LINQ to XML) (Visual Basic)](how-to-retrieve-the-value-of-an-attribute-linq-to-xml.md)|Pokazuje, jak pobrać wartości atrybutów.|  
|[Instrukcje: pobieranie płytki wartości elementu (Visual Basic)](how-to-retrieve-the-shallow-value-of-an-element.md)|Pokazuje, jak pobrać skróconą wartość elementu.|  
|[Osie zintegrowane z językiem w Visual Basic (LINQ to XML)](language-integrated-axes.md)|Podsumowuje Visual Basic osi zintegrowanych.|  
  
## <a name="see-also"></a>Zobacz też

- [Przewodnik programowania (LINQ to XML) (Visual Basic)](programming-guide-linq-to-xml.md)
