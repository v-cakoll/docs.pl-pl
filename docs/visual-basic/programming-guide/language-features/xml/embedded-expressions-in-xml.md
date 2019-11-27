---
title: Wyrażenia osadzone w XML
ms.date: 07/20/2015
f1_keywords:
- vb.XmlEmbeddedExpression
helpviewer_keywords:
- embedded expressions [Visual Basic]
- LINQ to XML [Visual Basic], embedded expressions
- XML literals [Visual Basic], embedded expressions
ms.assetid: bf2eb779-b751-4b7c-854f-9f2161482352
ms.openlocfilehash: 0cdb960160457108ddf18c554dae5f5993269833
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74332355"
---
# <a name="embedded-expressions-in-xml-visual-basic"></a>Wyrażenia osadzone w XML (Visual Basic)
Wyrażenia osadzone umożliwiają tworzenie literałów XML zawierających wyrażenia, które są oceniane w czasie wykonywania. Składnia wyrażenia osadzonego jest `<%=` `expression` `%>`, która jest taka sama jak składnia używana w ASP.NET.  
  
 Na przykład można utworzyć literał elementu XML, łącząc osadzone wyrażenia z zawartością tekstu literalnego.  
  
 [!code-vb[VbXMLSamples#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#27)]  
  
 Jeśli `isbnNumber` zawiera liczbę całkowitą 12345 i `modifiedDate` zawiera datę 3/5/2006, gdy ten kod jest wykonywany, wartością `book` jest:  
  
```xml  
<book category="fiction" isbn="12345">  
  <modifiedDate>3/5/2006</modifiedDate>  
</book>  
```  
  
## <a name="embedded-expression-location-and-validation"></a>Lokalizacja i walidacja wyrażenia osadzonego  
 Wyrażenia osadzone mogą występować tylko w określonych lokalizacjach w wyrażeniach literałów XML. Lokalizacja wyrażenia określa typy, które mogą być zwracane przez wyrażenie, oraz sposób obsługi `Nothing`. W poniższej tabeli opisano dozwolone lokalizacje i typy osadzonych wyrażeń.  
  
|Lokalizacja w literale|Typ wyrażenia|Obsługa `Nothing`|  
|---|---|---|  
|Nazwa elementu XML|<xref:System.Xml.Linq.XName>|Błąd|  
|Zawartość elementu XML|`Object` lub tablica `Object`|Ignorowane|  
|Nazwa atrybutu elementu XML|<xref:System.Xml.Linq.XName>|Błąd, chyba że wartość atrybutu jest również `Nothing`|  
|Wartość atrybutu elementu XML|`Object`|Zignorowano deklarację atrybutu|  
|Atrybut elementu XML|<xref:System.Xml.Linq.XAttribute> lub kolekcja <xref:System.Xml.Linq.XAttribute>|Ignorowane|  
|Element główny dokumentu XML|<xref:System.Xml.Linq.XElement> lub kolekcja jednego obiektu <xref:System.Xml.Linq.XElement> i dowolną liczbę obiektów <xref:System.Xml.Linq.XProcessingInstruction> i <xref:System.Xml.Linq.XComment>|Ignorowane|  
  
- Przykład wyrażenia osadzonego w nazwie elementu XML:  
  
     [!code-vb[VbXMLSamples#32](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#32)]  
  
- Przykład wyrażenia osadzonego w zawartości elementu XML:  
  
     [!code-vb[VbXMLSamples#33](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#33)]  
  
- Przykład wyrażenia osadzonego w nazwie atrybutu XML elementu:  
  
     [!code-vb[VbXMLSamples#34](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#34)]  
  
- Przykład wyrażenia osadzonego w wartości atrybutu elementu XML:  
  
     [!code-vb[VbXMLSamples#35](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#35)]  
  
- Przykład wyrażenia osadzonego w atrybucie elementu XML:  
  
     [!code-vb[VbXMLSamples#36](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#36)]  
  
- Przykład wyrażenia osadzonego w elemencie głównym dokumentu XML:  
  
     [!code-vb[VbXMLSamples#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#37)]  
  
 Jeśli włączysz `Option Strict`, kompilator sprawdzi, czy typ poszczególnych wyrażeń osadzonych poszerza do wymaganego typu. Jedynym wyjątkiem jest element główny dokumentu XML, który jest sprawdzany, gdy kod jest uruchomiony. Jeśli kompilujesz bez `Option Strict`, możesz osadzić wyrażenia typu `Object` i ich typ jest weryfikowany w czasie wykonywania.  
  
 W lokalizacjach, w których zawartość jest opcjonalna, osadzone wyrażenia zawierające `Nothing` są ignorowane. Oznacza to, że nie trzeba sprawdzać zawartości elementu, wartości atrybutów ani elementów tablicy nie `Nothing` przed użyciem literału XML. Nie można `Nothing`wymaganych wartości, takich jak nazwy elementów i atrybutów.  
  
 Aby uzyskać więcej informacji o używaniu wyrażenia osadzonego w określonym typie literału, zobacz [literał dokumentu XML](../../../../visual-basic/language-reference/xml-literals/xml-document-literal.md), [literał elementu XML](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md).  
  
## <a name="scoping-rules"></a>Reguły określania zakresu  
 Kompilator konwertuje każdy literał XML na wywołanie konstruktora dla odpowiedniego typu literału. Zawartość literału i osadzone wyrażenia w literale XML są przekazane jako argumenty do konstruktora. Oznacza to, że wszystkie Visual Basic elementy programistyczne dostępne dla literału XML są również dostępne dla jego osadzonych wyrażeń.  
  
 W literale XML można uzyskać dostęp do prefiksów przestrzeni nazw XML zadeklarowanych za pomocą instrukcji `Imports`. Można zadeklarować nowy prefiks przestrzeni nazw XML lub zaobserwować istniejący prefiks przestrzeni nazw XML w elemencie przy użyciu atrybutu `xmlns`. Nowa przestrzeń nazw jest dostępna dla węzłów podrzędnych tego elementu, ale nie do literałów XML w wyrażeniach osadzonych.  
  
> [!NOTE]
> W przypadku deklarowania prefiksu przestrzeni nazw XML przy użyciu atrybutu przestrzeni nazw `xmlns`, wartość atrybutu musi być ciągiem stałym. W tym względzie użycie atrybutu `xmlns` jest podobne do deklarowania przestrzeni nazw XML przy użyciu instrukcji `Imports`. Nie można użyć wyrażenia osadzonego do określenia wartości przestrzeni nazw XML.  
  
## <a name="see-also"></a>Zobacz także

- [Tworzenie kodu XML w Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
- [Literał dokumentu XML](../../../../visual-basic/language-reference/xml-literals/xml-document-literal.md)
- [Literał elementu XML](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)
- [Option Strict, instrukcja](../../../../visual-basic/language-reference/statements/option-strict-statement.md)
- [Imports, instrukcja (przestrzeń nazw i typ .NET)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)
- [Literały XML — przegląd](../../../../visual-basic/programming-guide/language-features/xml/xml-literals-overview.md)
