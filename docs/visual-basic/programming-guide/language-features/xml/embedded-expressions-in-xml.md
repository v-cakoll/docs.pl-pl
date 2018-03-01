---
title: "Wyrażenia osadzone w XML (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vb.XmlEmbeddedExpression
helpviewer_keywords:
- embedded expressions [Visual Basic]
- LINQ to XML [Visual Basic], embedded expressions
- XML literals [Visual Basic], embedded expressions
ms.assetid: bf2eb779-b751-4b7c-854f-9f2161482352
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: b1cdba0a39a932f143ac98c2514240e1696a8fe0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="embedded-expressions-in-xml-visual-basic"></a>Wyrażenia osadzone w XML (Visual Basic)
Wyrażenia osadzone umożliwiają tworzenie literałów XML, które zawierają wyrażenia, które są oceniane w czasie wykonywania. Składnia wyrażenia osadzonego jest `<%=` `expression` `%>`, który jest taki sam jak używać składni w [!INCLUDE[vstecasp](~/includes/vstecasp-md.md)].  
  
 Na przykład utworzeniem — element XML literału, łączenia wyrażenia osadzone pomocą zawartości tekstowej literału.  
  
 [!code-vb[VbXMLSamples#27](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/embedded-expressions-in-xml_1.vb)]  
  
 Jeśli `isbnNumber` zawiera całkowitą 12345 i `modifiedDate` zawiera datę 3/5/2006, gdy ten kod jest wykonywana, wartość `book` jest:  
  
```xml  
<book category="fiction" isbn="12345">  
  <modifiedDate>3/5/2006</modifiedDate>  
</book>  
```  
  
## <a name="embedded-expression-location-and-validation"></a>Wyrażenia osadzonego lokalizacji i sprawdzania poprawności  
 Wyrażenia osadzone może występować tylko w określonych lokalizacjach w wyrażeniach literału XML. Rozwiązania lokalizacji wyrażenie, które typy wyrażenie, które może zwracać i w jaki sposób `Nothing` jest obsługiwane. W poniższej tabeli opisano dozwolonych lokalizacji i typy osadzone wyrażenia.  
  
|Lokalizacja w literale|Typ wyrażenia|Obsługa`Nothing`|  
|---|---|---|  
|Nazwa elementu XML|<xref:System.Xml.Linq.XName>|Błąd|  
|Treść elementu XML.|`Object`tablica lub`Object`|Ignorowane|  
|Nazwa atrybutu element XML|<xref:System.Xml.Linq.XName>|Błąd, chyba że wartość atrybutu jest również`Nothing`|  
|Wartość atrybutu element XML|`Object`|Atrybut deklaracja ignorowana|  
|Atrybut — element XML|<xref:System.Xml.Linq.XAttribute>lub kolekcji<xref:System.Xml.Linq.XAttribute>|Ignorowane|  
|Element główny dokumentu XML|<xref:System.Xml.Linq.XElement>lub Kolekcja jednej <xref:System.Xml.Linq.XElement> obiekt i dowolnej liczby <xref:System.Xml.Linq.XProcessingInstruction> i <xref:System.Xml.Linq.XComment> obiektów|Ignorowane|  
  
-   Przykład wyrażenia osadzonego w nazwie elementu XML:  
  
     [!code-vb[VbXMLSamples#32](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/embedded-expressions-in-xml_2.vb)]  
  
-   Przykład wyrażenia osadzonego w zawartości elementu XML:  
  
     [!code-vb[VbXMLSamples#33](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/embedded-expressions-in-xml_3.vb)]  
  
-   Przykład wyrażenia osadzonego w nazwie atrybutu elementu XML:  
  
     [!code-vb[VbXMLSamples#34](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/embedded-expressions-in-xml_4.vb)]  
  
-   Przykład wyrażenia osadzonego w wartości atrybutu XML elementu:  
  
     [!code-vb[VbXMLSamples#35](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/embedded-expressions-in-xml_5.vb)]  
  
-   Przykład wyrażenia osadzonego w atrybucie elementu XML:  
  
     [!code-vb[VbXMLSamples#36](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/embedded-expressions-in-xml_6.vb)]  
  
-   Przykład wyrażenia osadzonego w głównym elementem dokumentu XML:  
  
     [!code-vb[VbXMLSamples#37](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/embedded-expressions-in-xml_7.vb)]  
  
 Po włączeniu `Option Strict`, kompilator sprawdza, czy typ każdego wyrażenia osadzonego rozszerzenie na wymagany typ. Jedynym wyjątkiem jest dla elementu głównego dokumentu XML, która została zweryfikowana, gdy kod działa. Jeśli kompilacja bez `Option Strict`, można osadzić wyrażeń typu `Object` i typem jest weryfikowana w czasie wykonywania.  
  
 W lokalizacji, której zawartość jest opcjonalne osadzone wyrażenia, które zawierają `Nothing` są ignorowane. Oznacza to, nie trzeba sprawdzić tej zawartości elementu wartości atrybutów i elementów tablicy nie są `Nothing` przed użyciem literał XML. Wymagane wartości, takich jak nazwy elementów i atrybutów, nie mogą być `Nothing`.  
  
 Aby uzyskać więcej informacji o używaniu wyrażenia osadzonego w określonego typu literal, zobacz [literał dokumentu XML](../../../../visual-basic/language-reference/xml-literals/xml-document-literal.md), [literał elementu XML](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md).  
  
## <a name="scoping-rules"></a>Zakres reguły  
 Kompilator konwertuje literał XML na wywołanie konstruktora dla odpowiedniego typu literału. Zawartość literalna i wyrażenia osadzone w literał XML są przekazywane jako argumenty konstruktora. Oznacza to, że wszystkie [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] programistyczny literał XML dostępne są również dostępne dla jego wyrażenia osadzonego.  
  
 Wewnątrz literału XML, można uzyskać dostępu do przestrzeni nazw XML prefiksy zadeklarowana z `Imports` instrukcji. Zadeklaruj nowy prefiks przestrzeni nazw XML lub w tle XML prefiks obszaru nazw, w elemencie przy użyciu `xmlns` atrybutu. Nowa przestrzeń nazw jest dostępna, do węzłów podrzędnych tego elementu, ale nie do literałów XML w wyrażeniach osadzonych.  
  
> [!NOTE]
>  Gdy deklaruje prefiks przestrzeni nazw XML przy użyciu `xmlns` atrybutu przestrzeni nazw, wartość atrybutu musi być ciągiem stałym. W tym zakresie przy użyciu `xmlns` przypomina przy użyciu atrybutu `Imports` instrukcji, aby zadeklarować przestrzeni nazw XML. Aby określić wartość przestrzeni nazw XML, nie można użyć wyrażenia osadzonego.  
  
## <a name="see-also"></a>Zobacz też  
 [Tworzenie XML w Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)  
 [Literał dokumentu XML](../../../../visual-basic/language-reference/xml-literals/xml-document-literal.md)  
 [Literał elementu XML](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)  
 [Option Strict — instrukcja](../../../../visual-basic/language-reference/statements/option-strict-statement.md)  
 [Imports — instrukcja (.NET Namespace i Type)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)  
 [Literały XML-Przegląd](../../../../visual-basic/programming-guide/language-features/xml/xml-literals-overview.md)
