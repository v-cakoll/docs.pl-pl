---
title: Literały XML — przegląd
ms.date: 07/20/2015
helpviewer_keywords:
- XML literals [Visual Basic], about XML literals
- declaring XML literals [Visual Basic]
- LINQ to XML [Visual Basic], XML literals
- literals [Visual Basic], XML
ms.assetid: 37987c15-4ab8-471b-bd45-399816bfb57f
ms.openlocfilehash: e5d2465d145f4059600121c6cef30bb2c74a8c1c
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346201"
---
# <a name="xml-literals-overview-visual-basic"></a>Literały XML - Przegląd (Visual Basic)
*Literał XML* umożliwia dołączenie kodu XML bezpośrednio do kodu Visual Basic. Składnia literału XML reprezentuje [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] obiektów i jest podobna do składni XML 1,0. Ułatwia to tworzenie elementów i dokumentów XML, ponieważ kod ma taką samą strukturę jak końcowy kod XML.  
  
 Visual Basic kompiluje literały XML do obiektów [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]. [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] udostępnia prosty model obiektów do tworzenia i manipulowania XML, a ten model integruje się dobrze z [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)]. Aby uzyskać więcej informacji, zobacz <xref:System.Xml.Linq.XElement>.  
  
 Można osadzić wyrażenie Visual Basic w literale XML. W czasie wykonywania aplikacja tworzy obiekt [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] dla każdego literału, włączając wartości osadzonych wyrażeń. Pozwala to określić zawartość dynamiczną wewnątrz literału XML. Aby uzyskać więcej informacji, zobacz [Embedded Expressions in XML](../../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md).  
  
 Aby uzyskać więcej informacji o różnicach między składnią literału XML i składnią XML 1,0, zobacz [literały XML i Specyfikacja xml 1,0](../../../../visual-basic/programming-guide/language-features/xml/xml-literals-and-the-xml-1-0-specification.md).  
  
## <a name="simple-literals"></a>Literały proste  
 Można utworzyć obiekt [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] w kodzie Visual Basic, wpisując lub wklejając w prawidłowym formacie XML. Literał elementu XML zwraca obiekt <xref:System.Xml.Linq.XElement>. Aby uzyskać więcej informacji, zobacz [literał elementu XML](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md) i [literały XML i specyfikacja XML 1,0](../../../../visual-basic/programming-guide/language-features/xml/xml-literals-and-the-xml-1-0-specification.md). Poniższy przykład tworzy element XML, który ma kilka elementów podrzędnych.  
  
 [!code-vb[VbXMLSamples#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples2.vb#5)]  
  
 Można utworzyć dokument XML, uruchamiając literał XML z `<?xml version="1.0"?>`, jak pokazano w poniższym przykładzie. Literał dokumentu XML zwraca obiekt <xref:System.Xml.Linq.XDocument>. Aby uzyskać więcej informacji, zobacz [literał dokumentu XML](../../../../visual-basic/language-reference/xml-literals/xml-document-literal.md).  
  
 [!code-vb[VbXMLSamples#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples2.vb#6)]  
  
> [!NOTE]
> Składnia literału XML w Visual Basic nie jest taka sama jak składnia w specyfikacji XML 1,0. Aby uzyskać więcej informacji, zobacz [literały XML i Specyfikacja xml 1,0](../../../../visual-basic/programming-guide/language-features/xml/xml-literals-and-the-xml-1-0-specification.md).  
  
## <a name="line-continuation"></a>Kontynuacja wiersza  
 Literał XML może rozdzielić wiele wierszy bez używania znaków kontynuacji wiersza (znak podkreślenia w znakach-ENTER). Ułatwia to porównywanie literałów XML w kodzie z dokumentami XML.  
  
 Kompilator traktuje znaki kontynuacji wierszy jako część literału XML. W związku z tym należy używać znaku podkreślenia spacji — należy wprowadzać sekwencję tylko wtedy, gdy należy do obiektu [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].  
  
 Jednak jeśli w wyrażeniu osadzonym jest wyrażenie wielowierszowe, muszą być wymagane znaki kontynuacji wiersza. Aby uzyskać więcej informacji, zobacz [Embedded Expressions in XML](../../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md).  
  
## <a name="embedding-queries-in-xml-literals"></a>Osadzanie zapytań w literałach XML  
 Możesz użyć zapytania w wyrażeniu osadzonym. Po wykonaniu tej czynności elementy zwrócone przez zapytanie są dodawane do elementu XML. Pozwala to dodać zawartość dynamiczną, na przykład wynik zapytania użytkownika do literału XML.  
  
 Na przykład poniższy kod używa osadzonego zapytania, aby utworzyć elementy XML z elementów członkowskich tablicy `phoneNumbers2`, a następnie dodać te elementy jako elementy podrzędne `contact2`.  
  
 [!code-vb[VbXMLSamples#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples2.vb#7)]  
  
## <a name="how-the-compiler-creates-objects-from-xml-literals"></a>Jak kompilator tworzy obiekty z literałów XML  
 Kompilator Visual Basic tłumaczy literały XML na wywołania odpowiednich konstruktorów [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] w celu utworzenia obiektu [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]. Na przykład kompilator Visual Basic przetłumaczy Poniższy przykład kodu na wywołanie konstruktora <xref:System.Xml.Linq.XProcessingInstruction> dla instrukcji wersji XML, wywołuje konstruktora <xref:System.Xml.Linq.XElement> dla elementów `<contact>`, `<name>`i `<phone>`, a następnie wywołuje Konstruktor <xref:System.Xml.Linq.XAttribute> dla atrybutu `type`. W odniesieniu do atrybutów w poniższym przykładzie kompilator Visual Basic wywoła <xref:System.Xml.Linq.XAttribute.%23ctor%28System.Xml.Linq.XName%2CSystem.Object%29> konstruktora dwa razy. Pierwszy przekaże wartość `type` parametru `name` i `home` wartość dla parametru `value`. Druga również przekaże wartość `type` parametru `name`, ale wartość `work` dla parametru `value`.  
  
 [!code-vb[VbXMLSamples#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples2.vb#6)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Xml.Linq.XElement>
- [Tworzenie kodu XML w Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
- [Wyrażenia osadzone w XML](../../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md)
- [Literał dokumentu XML](../../../../visual-basic/language-reference/xml-literals/xml-document-literal.md)
- [Literał elementu XML](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)
- [Literały XML](../../../../visual-basic/language-reference/xml-literals/index.md)
