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
ms.openlocfilehash: 0540c52cf3e4cd7594f051c10832ea99cf58a34e
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/01/2018
ms.locfileid: "43386463"
---
# <a name="accessing-xml-in-visual-basic"></a>Uzyskiwanie dostępu do XML w Visual Basic
Zapewnia właściwości osi XML do uzyskiwania dostępu i nawigacja w Visual Basic [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] struktury. Te właściwości użyj specjalnej składni, aby włączyć dostęp do elementów i atrybutów, określając nazwy XML.  
  
 W poniższej tabeli wymieniono funkcje językowe, które umożliwiają użytkownikowi dostęp do elementów XML oraz atrybuty w języku Visual Basic.  
  
### <a name="xml-axis-properties"></a>Właściwości osi XML  
  
|Opis właściwości|Przykład|Opis|  
|--------------------------|-------------|-----------------|  
|*osi podrzędnej*|`contact.<phone>`|Pobiera wszystkie `phone` elementy, które są elementami podrzędnymi `contact` elementu.|  
|*osi atrybutu*|`phone.@type`|Pobiera wszystkie `type` atrybuty `phone` elementu.|  
|*osi elementu podrzędnego*|`contacts...<name>`|Pobiera wszystkie `name` elementy `contacts` elementu, niezależnie od tego, jak głęboko w hierarchii, ich wystąpienia.|  
|*indeksator rozszerzeń*|`contacts...<name>(0)`|Pobiera pierwszy `name` elementu z sekwencji.|  
|*value*|`contacts...<name>.Value`|Pobiera ciąg reprezentujący pierwszy obiekt w sekwencji, lub `Nothing` Jeśli sekwencji jest pusta.|  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Instrukcje: dostęp do elementów potomnych XML](../../../../visual-basic/programming-guide/language-features/xml/how-to-access-xml-descendant-elements.md)  
 Pokazuje, jak dostęp do wszystkich elementów XML, które mają określoną nazwą i znajdujących się w określonym elemencie XML za pomocą właściwości osi elementu podrzędnego.  
  
 [Instrukcje: dostęp do elementów podrzędnych XML](../../../../visual-basic/programming-guide/language-features/xml/how-to-access-xml-child-elements.md)  
 Pokazuje, jak korzystać z elementem podrzędnym właściwości osi, aby dostęp do wszystkich elementów podrzędnych XML, które mają określoną nazwą w elemencie XML.  
  
 [Instrukcje: dostęp do atrybutów XML](../../../../visual-basic/programming-guide/language-features/xml/how-to-access-xml-attributes.md)  
 Pokazuje, jak dostęp do wszystkich atrybutów XML, które mają określoną nazwą w elemencie XML za pomocą właściwości osi atrybutu.  
  
 [Instrukcje: deklarowanie prefiksów przestrzeni nazw XML i korzystanie z nich](../../../../visual-basic/programming-guide/language-features/xml/how-to-declare-and-use-xml-namespace-prefixes.md)  
 Pokazuje sposób deklarowania prefiks przestrzeni nazw XML i użyć jej do tworzenia i dostęp do elementów XML.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Właściwości osi XML](../../../../visual-basic/language-reference/xml-axis/index.md)  
 Zawiera łącza do sekcji opisujących różne właściwości dostępu do XML.  
  
 [Przegląd interfejsu LINQ to XML w Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/overview-of-linq-to-xml.md)  
 Zawiera wprowadzenie do korzystania z [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] w języku Visual Basic.  
  
 [Tworzenie XML w Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)  
 Wprowadzenie do korzystania z literałów XML w Visual Basic.  
  
 [Manipulowanie XML w Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/manipulating-xml.md)  
 Zawiera łącza do sekcje dotyczące ładowania i modyfikowania XML w Visual Basic.  
  
 [XML](../../../../visual-basic/programming-guide/language-features/xml/index.md)  
 Zawiera łącza do sekcji opisujący sposób użycia [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] w języku Visual Basic.
