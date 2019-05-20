---
title: Wyrażenia osadzone w XML (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.XmlEmbeddedExpression
helpviewer_keywords:
- embedded expressions [Visual Basic]
- LINQ to XML [Visual Basic], embedded expressions
- XML literals [Visual Basic], embedded expressions
ms.assetid: bf2eb779-b751-4b7c-854f-9f2161482352
ms.openlocfilehash: ef8ac62d9d969ce4463931d69b0302376ca0ccc4
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/19/2019
ms.locfileid: "65881553"
---
# <a name="embedded-expressions-in-xml-visual-basic"></a>Wyrażenia osadzone w XML (Visual Basic)
Wyrażenia osadzone umożliwiają tworzenie literałów XML, które zawierają wyrażenia, które są oceniane w czasie wykonywania. Składnia wyrażenia osadzone jest `<%=` `expression` `%>`, która jest taka sama jak składnią używaną w programie ASP.NET.  
  
 Na przykład można utworzysz XML element literału, łącząc osadzone wyrażenia zawierające tekst dosłowny zawartości.  
  
 [!code-vb[VbXMLSamples#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#27)]  
  
 Jeśli `isbnNumber` zawiera całkowitą 12345 i `modifiedDate` zawiera datę 3/5/2006, kiedy ten kod jest wykonywany, wartość `book` jest:  
  
```xml  
<book category="fiction" isbn="12345">  
  <modifiedDate>3/5/2006</modifiedDate>  
</book>  
```  
  
## <a name="embedded-expression-location-and-validation"></a>Wyrażenia osadzone lokalizacji i sprawdzania poprawności  
 Wyrażenia osadzone może znajdować się tylko w określonych lokalizacjach w ramach wyrażeń literałów XML. Formanty lokalizacji wyrażenie, które typy wyrażenie może zwrócić i w jaki sposób `Nothing` jest obsługiwane. W poniższej tabeli opisano dozwolone lokalizacje i typy wyrażenia osadzone.  
  
|Lokalizacja w literału|Typ wyrażenia|Obsługa `Nothing`|  
|---|---|---|  
|Nazwa elementu XML|<xref:System.Xml.Linq.XName>|Błąd|  
|Treść elementu XML.|`Object` tablica lub `Object`|Ignorowane|  
|Nazwa atrybutu — element XML|<xref:System.Xml.Linq.XName>|Błąd, chyba że wartość atrybutu jest również `Nothing`|  
|Wartość atrybutu — element XML|`Object`|Atrybut deklaracja ignorowana|  
|Atrybut — element XML|<xref:System.Xml.Linq.XAttribute> lub kolekcji <xref:System.Xml.Linq.XAttribute>|Ignorowane|  
|Element główny dokumentu XML|<xref:System.Xml.Linq.XElement> lub kolekcji jednego <xref:System.Xml.Linq.XElement> obiektu i dowolną liczbę <xref:System.Xml.Linq.XProcessingInstruction> i <xref:System.Xml.Linq.XComment> obiektów|Ignorowane|  
  
- Przykład wyrażenia osadzone w nazwa elementu XML:  
  
     [!code-vb[VbXMLSamples#32](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#32)]  
  
- Przykład wyrażenia osadzone w zawartości elementu XML:  
  
     [!code-vb[VbXMLSamples#33](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#33)]  
  
- Przykład wyrażenia osadzone w nazwie atrybutu elementu XML:  
  
     [!code-vb[VbXMLSamples#34](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#34)]  
  
- Przykład wyrażenia osadzone w wartości atrybutu elementu XML:  
  
     [!code-vb[VbXMLSamples#35](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#35)]  
  
- Przykład wyrażenia osadzone w atrybucie — element XML:  
  
     [!code-vb[VbXMLSamples#36](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#36)]  
  
- Przykład wyrażenia osadzone w głównym elementem dokumentu XML:  
  
     [!code-vb[VbXMLSamples#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#37)]  
  
 Po włączeniu `Option Strict`, kompilator sprawdza, czy typ każdego osadzone wyrażenia rozszerza się na wymagany typ. Jedynym wyjątkiem jest, aby uzyskać element główny dokumentu XML, który jest weryfikowany, gdy kod działa. Jeśli kompilujesz bez `Option Strict`, możesz osadzić wyrażeń o typie `Object` i ich typ jest weryfikowana w czasie wykonywania.  
  
 W lokalizacji, w którym zawartość jest opcjonalne osadzone wyrażenia, które zawierają `Nothing` są ignorowane. Oznacza to, nie trzeba sprawdzić zawartość elementu, wartości atrybutów i elementów tablicy nie są `Nothing` przed użyciem literał XML. Wymagane wartości, takich jak nazwy elementów i atrybutów, nie może być `Nothing`.  
  
 Aby uzyskać więcej informacji na temat za pomocą wyrażenia osadzone w określonym typie literału, zobacz [literał dokumentu XML](../../../../visual-basic/language-reference/xml-literals/xml-document-literal.md), [literał elementu XML](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md).  
  
## <a name="scoping-rules"></a>Wyznaczanie zakresu reguły  
 Kompilator konwertuje literał XML wywołanie konstruktora dla odpowiedniego typu literału. Zawartość literałową i wyrażenia osadzone w literał XML są przekazywane jako argumenty do konstruktora. Oznacza to, że wszystkie dostępne literał XML elementy programowania Visual Basic są również dostępne dla jego wyrażenia osadzone.  
  
 W literał XML, można uzyskać dostęp do przestrzeni nazw XML prefiksy zadeklarowanych za pomocą `Imports` instrukcji. Zadeklaruj nowy prefiks przestrzeni nazw XML lub w tle XML prefiks obszaru nazw, w elemencie przy użyciu `xmlns` atrybutu. Nowy obszar nazw jest dostępna, do węzłów podrzędnych tego elementu, ale nie do literałów XML w wyrażenia osadzone.  
  
> [!NOTE]
>  Kiedy Deklarujesz prefiks przestrzeni nazw XML przy użyciu `xmlns` atrybut przestrzeni nazw, wartość atrybutu musi być ciągiem stałym. W tym zakresie za pomocą `xmlns` przypomina za pomocą atrybutu `Imports` instrukcję, aby zadeklarować przestrzeni nazw XML. Wyrażenia osadzone nie można użyć do określenia wartości przestrzeni nazw XML.  
  
## <a name="see-also"></a>Zobacz także

- [Tworzenie XML w Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
- [Literał dokumentu XML](../../../../visual-basic/language-reference/xml-literals/xml-document-literal.md)
- [Literał elementu XML](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)
- [Option Strict, instrukcja](../../../../visual-basic/language-reference/statements/option-strict-statement.md)
- [Imports, instrukcja (przestrzeń nazw i typ .NET)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)
- [Literały XML — przegląd](../../../../visual-basic/programming-guide/language-features/xml/xml-literals-overview.md)
