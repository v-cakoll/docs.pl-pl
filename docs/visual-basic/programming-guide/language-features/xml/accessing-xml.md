---
title: "Uzyskiwanie dostępu do XML w Visual Basic"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- LINQ to XML [Visual Basic], accessing XML
- Visual Basic code, XML
- accessing XML [Visual Basic], axis properties
- XML [Visual Basic], axis properties
- XML [Visual Basic], accessing
ms.assetid: c47f88b2-3cbc-4bb1-b4b9-be60f71ffc6a
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 79c7b8a94731e151a803a041d91dd1e240ddeb97
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="accessing-xml-in-visual-basic"></a>Uzyskiwanie dostępu do XML w Visual Basic
[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]Udostępnia właściwości osi XML do uzyskiwania dostępu i nawigacja [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] struktury. Te właściwości Użyj specjalnych składni, aby włączyć dostęp do elementów i atrybutów przez określenie nazw XML.  
  
 W poniższej tabeli wymieniono funkcje językowe, które umożliwiają dostęp do elementów XML oraz atrybuty w [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)].  
  
### <a name="xml-axis-properties"></a>Właściwości osi XML  
  
|Opis właściwości|Przykład|Opis|  
|--------------------------|-------------|-----------------|  
|*osi podrzędnej*|`contact.<phone>`|Pobiera wszystkie `phone` elementów, które są elementami podrzędnymi elementu `contact` elementu.|  
|*Atrybut osi*|`phone.@type`|Pobiera wszystkie `type` atrybuty `phone` elementu.|  
|*osi elementu podrzędnego*|`contacts...<name>`|Pobiera wszystkie `name` elementy `contacts` elementu, niezależnie od tego, jak głęboko w hierarchii występowania.|  
|*indeksator rozszerzeń*|`contacts...<name>(0)`|Pobiera pierwszy `name` element z sekwencji.|  
|*wartość*|`contacts...<name>.Value`|Pobiera pierwszy obiekt reprezentację ciągu w sekwencji, lub `Nothing` Jeśli sekwencja jest pusta.|  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Porady: dostęp do elementów podrzędnych XML](../../../../visual-basic/programming-guide/language-features/xml/how-to-access-xml-descendant-elements.md)  
 Przedstawia sposób użycia właściwości osi elementu podrzędnego na dostęp do wszystkich elementów XML, które mają określonej nazwy i znajdujących się w obszarze określonego elementu XML.  
  
 [Porady: dostęp do elementów podrzędnych XML](../../../../visual-basic/programming-guide/language-features/xml/how-to-access-xml-child-elements.md)  
 Przedstawia sposób użycia elementem podrzędnym właściwości osi, aby dostęp do wszystkich elementów podrzędnych XML, których nazwa określona w elemencie XML.  
  
 [Porady: dostęp do atrybutów XML](../../../../visual-basic/programming-guide/language-features/xml/how-to-access-xml-attributes.md)  
 Przedstawia sposób użycia właściwości osi atrybutu na dostęp do wszystkich atrybutów XML, których nazwa określona w elemencie XML.  
  
 [Porady: deklarowanie prefiksów Namespace XML i korzystanie](../../../../visual-basic/programming-guide/language-features/xml/how-to-declare-and-use-xml-namespace-prefixes.md)  
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
