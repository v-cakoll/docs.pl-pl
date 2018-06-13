---
title: Uzyskiwanie dostępu do XML w Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- LINQ to XML [Visual Basic], accessing XML
- Visual Basic code, XML
- accessing XML [Visual Basic], axis properties
- XML [Visual Basic], axis properties
- XML [Visual Basic], accessing
ms.assetid: c47f88b2-3cbc-4bb1-b4b9-be60f71ffc6a
ms.openlocfilehash: b000b3f6846f800b2a96ce10cdd408a355f78a81
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33649597"
---
# <a name="accessing-xml-in-visual-basic"></a>Uzyskiwanie dostępu do XML w Visual Basic
Visual Basic zapewnia właściwości osi XML do uzyskiwania dostępu i nawigacja [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] struktury. Te właściwości Użyj specjalnych składni, aby włączyć dostęp do elementów i atrybutów przez określenie nazw XML.  
  
 W poniższej tabeli wymieniono funkcje językowe, które umożliwiają dostęp do elementów XML oraz atrybuty w języku Visual Basic.  
  
### <a name="xml-axis-properties"></a>Właściwości osi XML  
  
|Opis właściwości|Przykład|Opis|  
|--------------------------|-------------|-----------------|  
|*osi podrzędnej*|`contact.<phone>`|Pobiera wszystkie `phone` elementów, które są elementami podrzędnymi elementu `contact` elementu.|  
|*Atrybut osi*|`phone.@type`|Pobiera wszystkie `type` atrybuty `phone` elementu.|  
|*osi elementu podrzędnego*|`contacts...<name>`|Pobiera wszystkie `name` elementy `contacts` elementu, niezależnie od tego, jak głęboko w hierarchii występowania.|  
|*indeksator rozszerzeń*|`contacts...<name>(0)`|Pobiera pierwszy `name` element z sekwencji.|  
|*value*|`contacts...<name>.Value`|Pobiera pierwszy obiekt reprezentację ciągu w sekwencji, lub `Nothing` Jeśli sekwencja jest pusta.|  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Instrukcje: dostęp do elementów potomnych XML](../../../../visual-basic/programming-guide/language-features/xml/how-to-access-xml-descendant-elements.md)  
 Przedstawia sposób użycia właściwości osi elementu podrzędnego na dostęp do wszystkich elementów XML, które mają określonej nazwy i znajdujących się w obszarze określonego elementu XML.  
  
 [Instrukcje: dostęp do elementów podrzędnych XML](../../../../visual-basic/programming-guide/language-features/xml/how-to-access-xml-child-elements.md)  
 Przedstawia sposób użycia elementem podrzędnym właściwości osi, aby dostęp do wszystkich elementów podrzędnych XML, których nazwa określona w elemencie XML.  
  
 [Instrukcje: dostęp do atrybutów XML](../../../../visual-basic/programming-guide/language-features/xml/how-to-access-xml-attributes.md)  
 Przedstawia sposób użycia właściwości osi atrybutu na dostęp do wszystkich atrybutów XML, których nazwa określona w elemencie XML.  
  
 [Instrukcje: deklarowanie prefiksów przestrzeni nazw XML i korzystanie z nich](../../../../visual-basic/programming-guide/language-features/xml/how-to-declare-and-use-xml-namespace-prefixes.md)  
 Pokazuje, jak deklaruje prefiks przestrzeni nazw XML i użyć go do tworzenia i dostęp do elementów XML.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Właściwości osi XML](../../../../visual-basic/language-reference/xml-axis/xml-axis-properties.md)  
 Zawiera łącza do sekcji opisujące różne właściwości dostępu XML.  
  
 [Przegląd LINQ do XML w Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/overview-of-linq-to-xml.md)  
 Wprowadzenie do przy użyciu [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] w języku Visual Basic.  
  
 [Tworzenie XML w Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)  
 Wprowadzenie do przy użyciu literałów XML w Visual Basic.  
  
 [Manipulowanie XML w Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/manipulating-xml.md)  
 Zawiera łącza do sekcji o ładowania i modyfikowanie kodu XML w Visual Basic.  
  
 [XML](../../../../visual-basic/programming-guide/language-features/xml/index.md)  
 Zawiera łącza do sekcji opisujący sposób użycia [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] w języku Visual Basic.
