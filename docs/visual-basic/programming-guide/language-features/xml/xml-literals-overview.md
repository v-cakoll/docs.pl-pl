---
title: Literały XML - Przegląd
ms.date: 07/20/2015
helpviewer_keywords:
- XML literals [Visual Basic], about XML literals
- declaring XML literals [Visual Basic]
- LINQ to XML [Visual Basic], XML literals
- literals [Visual Basic], XML
ms.assetid: 37987c15-4ab8-471b-bd45-399816bfb57f
ms.openlocfilehash: e889de4eefae6a943c70735f8a16474cb76d1149
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84403294"
---
# <a name="xml-literals-overview-visual-basic"></a>Literały XML - Przegląd (Visual Basic)
*Literał XML* umożliwia dołączenie kodu XML bezpośrednio do kodu Visual Basic. Składnia literału XML reprezentuje [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] obiekty i jest podobna do SKŁADNI xml 1,0. Ułatwia to tworzenie elementów i dokumentów XML, ponieważ kod ma taką samą strukturę jak końcowy kod XML.  
  
 Visual Basic kompiluje literały XML do [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] obiektów. [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]udostępnia prosty model obiektów do tworzenia i manipulowania XML, a ten model integruje się dobrze ze standardem Language-Integrated Query (LINQ). Aby uzyskać więcej informacji, zobacz <xref:System.Xml.Linq.XElement>.  
  
 Można osadzić wyrażenie Visual Basic w literale XML. W czasie wykonywania aplikacja tworzy [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] obiekt dla każdego literału, włączając wartości osadzonych wyrażeń. Pozwala to określić zawartość dynamiczną wewnątrz literału XML. Aby uzyskać więcej informacji, zobacz [Embedded Expressions in XML](embedded-expressions-in-xml.md).  
  
 Aby uzyskać więcej informacji o różnicach między składnią literału XML i składnią XML 1,0, zobacz [literały XML i Specyfikacja xml 1,0](xml-literals-and-the-xml-1-0-specification.md).  
  
## <a name="simple-literals"></a>Literały proste  
 Można utworzyć [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] obiekt w kodzie Visual Basic, wpisując lub wklejając w prawidłowym formacie XML. Literał elementu XML zwraca <xref:System.Xml.Linq.XElement> obiekt. Aby uzyskać więcej informacji, zobacz [literał elementu XML](../../../language-reference/xml-literals/xml-element-literal.md) i [literały XML i specyfikacja XML 1,0](xml-literals-and-the-xml-1-0-specification.md). Poniższy przykład tworzy element XML, który ma kilka elementów podrzędnych.  
  
 [!code-vb[VbXMLSamples#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples2.vb#5)]  
  
 Można utworzyć dokument XML, uruchamiając literał XML z `<?xml version="1.0"?>` , jak pokazano w poniższym przykładzie. Literał dokumentu XML zwraca <xref:System.Xml.Linq.XDocument> obiekt. Aby uzyskać więcej informacji, zobacz [literał dokumentu XML](../../../language-reference/xml-literals/xml-document-literal.md).  
  
 [!code-vb[VbXMLSamples#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples2.vb#6)]  
  
> [!NOTE]
> Składnia literału XML w Visual Basic nie jest taka sama jak składnia w specyfikacji XML 1,0. Aby uzyskać więcej informacji, zobacz [literały XML i Specyfikacja xml 1,0](xml-literals-and-the-xml-1-0-specification.md).  
  
## <a name="line-continuation"></a>Kontynuacja wiersza  
 Literał XML może rozdzielić wiele wierszy bez używania znaków kontynuacji wiersza (znak podkreślenia w znakach-ENTER). Ułatwia to porównywanie literałów XML w kodzie z dokumentami XML.  
  
 Kompilator traktuje znaki kontynuacji wierszy jako część literału XML. W związku z tym należy używać znaku podkreślenia spacji — należy wprowadzać sekwencję tylko wtedy, gdy należy do [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] obiektu.  
  
 Jednak jeśli w wyrażeniu osadzonym jest wyrażenie wielowierszowe, muszą być wymagane znaki kontynuacji wiersza. Aby uzyskać więcej informacji, zobacz [Embedded Expressions in XML](embedded-expressions-in-xml.md).  
  
## <a name="embedding-queries-in-xml-literals"></a>Osadzanie zapytań w literałach XML  
 Możesz użyć zapytania w wyrażeniu osadzonym. Po wykonaniu tej czynności elementy zwrócone przez zapytanie są dodawane do elementu XML. Pozwala to dodać zawartość dynamiczną, na przykład wynik zapytania użytkownika do literału XML.  
  
 Na przykład poniższy kod używa osadzonego zapytania, aby utworzyć elementy XML z elementów członkowskich `phoneNumbers2` tablicy, a następnie dodać te elementy jako elementy podrzędne `contact2` .  
  
 [!code-vb[VbXMLSamples#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples2.vb#7)]  
  
## <a name="how-the-compiler-creates-objects-from-xml-literals"></a>Jak kompilator tworzy obiekty z literałów XML  
 Kompilator Visual Basic tłumaczy literały XML na wywołania równoważnych [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] konstruktorów w celu utworzenia [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] obiektu. Na przykład kompilator Visual Basic przetłumaczy Poniższy przykład kodu na wywołanie <xref:System.Xml.Linq.XProcessingInstruction> konstruktora dla instrukcji wersji języka XML, wywołania do <xref:System.Xml.Linq.XElement> konstruktora dla `<contact>` elementów, `<name>` i `<phone>` i wywołań do <xref:System.Xml.Linq.XAttribute> konstruktora dla `type` atrybutu. W odniesieniu do atrybutów w poniższym przykładzie, kompilator Visual Basic wywoła <xref:System.Xml.Linq.XAttribute.%23ctor%28System.Xml.Linq.XName%2CSystem.Object%29> Konstruktor dwa razy. Pierwsze przekaże wartość `type` `name` parametru i wartość `home` `value` parametru. Druga również przekaże wartość `type` `name` parametru, ale wartość `work` `value` parametru.  
  
 [!code-vb[VbXMLSamples#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples2.vb#6)]  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Xml.Linq.XElement>
- [Tworzenie XML w Visual Basic](creating-xml.md)
- [Wyrażenia osadzone w XML](embedded-expressions-in-xml.md)
- [Literał dokumentu XML](../../../language-reference/xml-literals/xml-document-literal.md)
- [Literał elementu XML](../../../language-reference/xml-literals/xml-element-literal.md)
- [Literały XML](../../../language-reference/xml-literals/index.md)
