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
ms.openlocfilehash: 282b7d91ec7cfe2f587c67bc9a982f0da22ad925
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410312"
---
# <a name="accessing-xml-in-visual-basic"></a>Uzyskiwanie dostępu do XML w Visual Basic
Visual Basic udostępnia właściwości osi XML na potrzeby uzyskiwania dostępu do struktur i nawigowania w nich [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] . Te właściwości używają specjalnej składni, aby umożliwić dostęp do elementów i atrybutów przez określenie nazw XML.  
  
 Poniższa tabela zawiera listę funkcji języka, które umożliwiają dostęp do elementów i atrybutów XML w Visual Basic.  
  
### <a name="xml-axis-properties"></a>Właściwości osi XML  
  
|Opis właściwości|Przykład|Opis|  
|--------------------------|-------------|-----------------|  
|*oś podrzędna*|`contact.<phone>`|Pobiera wszystkie `phone` elementy, które są elementami podrzędnymi `contact` elementu.|  
|*oś atrybutów*|`phone.@type`|Pobiera wszystkie `type` atrybuty `phone` elementu.|  
|*oś elementu podrzędnego*|`contacts...<name>`|Pobiera wszystkie `name` elementy `contacts` elementu, niezależnie od tego, jak głęboko występują w hierarchii.|  
|*Indeksator rozszerzeń*|`contacts...<name>(0)`|Pobiera pierwszy `name` element z sekwencji.|  
|*wartościami*|`contacts...<name>.Value`|Pobiera ciąg reprezentujący pierwszy obiekt w sekwencji lub, `Nothing` Jeśli sekwencja jest pusta.|  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Instrukcje: dostęp do elementów potomnych XML](how-to-access-xml-descendant-elements.md)  
 Pokazuje, jak używać właściwości osi elementu podrzędnego w celu uzyskania dostępu do wszystkich elementów XML, które mają określoną nazwę i które są zawarte w określonym elemencie XML.  
  
 [Instrukcje: dostęp do elementów podrzędnych XML](how-to-access-xml-child-elements.md)  
 Pokazuje, jak używać właściwości osi podrzędnej w celu uzyskania dostępu do wszystkich elementów podrzędnych XML, które mają określoną nazwę w elemencie XML.  
  
 [Instrukcje: dostęp do atrybutów XML](how-to-access-xml-attributes.md)  
 Pokazuje, jak używać właściwości osi atrybutu w celu uzyskania dostępu do wszystkich atrybutów XML o określonej nazwie w elemencie XML.  
  
 [Porady: deklarowanie prefiksów przestrzeni nazw XML i korzystanie z nich](how-to-declare-and-use-xml-namespace-prefixes.md)  
 Pokazuje, jak zadeklarować prefiks przestrzeni nazw XML i używać go do tworzenia elementów XML i uzyskiwania do nich dostępu.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Właściwości osi XML](../../../language-reference/xml-axis/index.md)  
 Zawiera łącza do sekcji opisujących różne właściwości dostępu XML.  
  
 [Przegląd LINQ to XML w Visual Basic](overview-of-linq-to-xml.md)  
 Zawiera wprowadzenie do korzystania [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] z programu w Visual Basic.  
  
 [Tworzenie XML w Visual Basic](creating-xml.md)  
 Zawiera wprowadzenie do korzystania z literałów XML w Visual Basic.  
  
 [Manipulowanie XML w Visual Basic](manipulating-xml.md)  
 Zawiera łącza do sekcji dotyczące ładowania i modyfikowania kodu XML w Visual Basic.  
  
 [XML](index.md)  
 Zawiera łącza do sekcji opisujących sposób korzystania [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] z programu w programie Visual Basic.
