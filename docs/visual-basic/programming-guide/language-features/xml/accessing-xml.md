---
title: Uzyskiwanie dostępu do kodu XML
ms.date: 07/20/2015
helpviewer_keywords:
- LINQ to XML [Visual Basic], accessing XML
- Visual Basic code, XML
- accessing XML [Visual Basic], axis properties
- XML [Visual Basic], axis properties
- XML [Visual Basic], accessing
ms.assetid: c47f88b2-3cbc-4bb1-b4b9-be60f71ffc6a
ms.openlocfilehash: 1fa1d94fc710272ac0ba9ea7167989da42a51fcd
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351748"
---
# <a name="accessing-xml-in-visual-basic"></a>Uzyskiwanie dostępu do XML w Visual Basic
Visual Basic udostępnia właściwości osi XML na potrzeby uzyskiwania dostępu do struktur [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] i nawigowania w nich. Te właściwości używają specjalnej składni, aby umożliwić dostęp do elementów i atrybutów przez określenie nazw XML.  
  
 Poniższa tabela zawiera listę funkcji języka, które umożliwiają dostęp do elementów i atrybutów XML w Visual Basic.  
  
### <a name="xml-axis-properties"></a>Właściwości osi XML  
  
|Opis właściwości|Przykład|Opis|  
|--------------------------|-------------|-----------------|  
|*oś podrzędna*|`contact.<phone>`|Pobiera wszystkie elementy `phone`, które są elementami podrzędnymi elementu `contact`.|  
|*oś atrybutów*|`phone.@type`|Pobiera wszystkie `type` atrybuty elementu `phone`.|  
|*oś elementu podrzędnego*|`contacts...<name>`|Pobiera wszystkie elementy `name` elementu `contacts`, niezależnie od ich występowania w hierarchii.|  
|*Indeksator rozszerzeń*|`contacts...<name>(0)`|Pobiera pierwszy `name` elementu z sekwencji.|  
|*value*|`contacts...<name>.Value`|Pobiera ciąg reprezentujący pierwszy obiekt w sekwencji lub `Nothing`, jeśli sekwencja jest pusta.|  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Instrukcje: dostęp do elementów potomnych XML](../../../../visual-basic/programming-guide/language-features/xml/how-to-access-xml-descendant-elements.md)  
 Pokazuje, jak używać właściwości osi elementu podrzędnego w celu uzyskania dostępu do wszystkich elementów XML, które mają określoną nazwę i które są zawarte w określonym elemencie XML.  
  
 [Instrukcje: dostęp do elementów podrzędnych XML](../../../../visual-basic/programming-guide/language-features/xml/how-to-access-xml-child-elements.md)  
 Pokazuje, jak używać właściwości osi podrzędnej w celu uzyskania dostępu do wszystkich elementów podrzędnych XML, które mają określoną nazwę w elemencie XML.  
  
 [Instrukcje: dostęp do atrybutów XML](../../../../visual-basic/programming-guide/language-features/xml/how-to-access-xml-attributes.md)  
 Pokazuje, jak używać właściwości osi atrybutu w celu uzyskania dostępu do wszystkich atrybutów XML o określonej nazwie w elemencie XML.  
  
 [Instrukcje: deklarowanie prefiksów przestrzeni nazw XML i korzystanie z nich](../../../../visual-basic/programming-guide/language-features/xml/how-to-declare-and-use-xml-namespace-prefixes.md)  
 Pokazuje, jak zadeklarować prefiks przestrzeni nazw XML i używać go do tworzenia elementów XML i uzyskiwania do nich dostępu.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Właściwości osi XML](../../../../visual-basic/language-reference/xml-axis/index.md)  
 Zawiera łącza do sekcji opisujących różne właściwości dostępu XML.  
  
 [Omówienie LINQ to XML w Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/overview-of-linq-to-xml.md)  
 Zawiera wprowadzenie do korzystania z [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] w Visual Basic.  
  
 [Tworzenie kodu XML w Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)  
 Zawiera wprowadzenie do korzystania z literałów XML w Visual Basic.  
  
 [Manipulowanie XML w Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/manipulating-xml.md)  
 Zawiera łącza do sekcji dotyczące ładowania i modyfikowania kodu XML w Visual Basic.  
  
 [XML](../../../../visual-basic/programming-guide/language-features/xml/index.md)  
 Zawiera łącza do sekcji opisujących sposób używania [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] w Visual Basic.
