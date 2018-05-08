---
title: Literały XML - Przegląd (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- XML literals [Visual Basic], about XML literals
- declaring XML literals [Visual Basic]
- LINQ to XML [Visual Basic], XML literals
- literals [Visual Basic], XML
ms.assetid: 37987c15-4ab8-471b-bd45-399816bfb57f
ms.openlocfilehash: 03fc8c11b5553c9c3a63bdcb69bf6135050e2c89
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="xml-literals-overview-visual-basic"></a>Literały XML - Przegląd (Visual Basic)
*Literał XML* umożliwia dołączenie XML bezpośrednio w kodzie języka Visual Basic. Reprezentuje składni literału XML [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] obiektów który jest podobny do składni XML 1.0. Ułatwia to programowo utworzyć elementów XML oraz dokumentów, ponieważ używany kod ma taką samą strukturę jak końcowego XML.  
  
 Literały XML do kompiluje Visual Basic [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] obiektów. [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] udostępnia prosty model obiektów do tworzenia i manipulowanie XML, a ten model integruje się również z [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)]. Aby uzyskać więcej informacji, zobacz <xref:System.Xml.Linq.XElement>.  
  
 Wyrażenie języka Visual Basic można osadzić w postaci literału ciągu XML. W czasie wykonywania, aplikacja tworzy [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] obiekt dla każdego literal, zawierające wartości wyrażenia osadzone. Dzięki temu można określić zawartości dynamicznej wewnątrz literału XML. Aby uzyskać więcej informacji, zobacz [wyrażenia osadzone w XML](../../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md).  
  
 Aby uzyskać więcej informacji na temat różnic między składni literału XML i składni XML 1.0, zobacz [literały XML i specyfikacja XML 1.0](../../../../visual-basic/programming-guide/language-features/xml/xml-literals-and-the-xml-1-0-specification.md).  
  
## <a name="simple-literals"></a>Literały proste  
 Można utworzyć [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] obiekt kodu języka Visual Basic, wpisując lub wklejając w prawidłowym kodem XML. Literał elementu XML zwraca <xref:System.Xml.Linq.XElement> obiektu. Aby uzyskać więcej informacji, zobacz [literał elementu XML](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md) i [literały XML i specyfikacja XML 1.0](../../../../visual-basic/programming-guide/language-features/xml/xml-literals-and-the-xml-1-0-specification.md). Poniższy przykład tworzy element XML, który ma kilka elementów podrzędnych.  
  
 [!code-vb[VbXMLSamples#5](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-literals-overview_1.vb)]  
  
 Można utworzyć dokumentu XML, uruchamiając literału z XML `<?xml version="1.0"?>`, jak pokazano w poniższym przykładzie. Literał dokumentu XML zwraca <xref:System.Xml.Linq.XDocument> obiektu. Aby uzyskać więcej informacji, zobacz [literał dokumentu XML](../../../../visual-basic/language-reference/xml-literals/xml-document-literal.md).  
  
 [!code-vb[VbXMLSamples#6](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-literals-overview_2.vb)]  
  
> [!NOTE]
>  Składnia literału XML w Visual Basic nie jest taka sama jak składni w specyfikacji XML 1.0. Aby uzyskać więcej informacji, zobacz [literały XML i specyfikacja XML 1.0](../../../../visual-basic/programming-guide/language-features/xml/xml-literals-and-the-xml-1-0-specification.md).  
  
## <a name="line-continuation"></a>Kontynuacja wiersza  
 Literał XML może obejmować wiele wierszy bez użycia znaki kontynuacji wiersza (wprowadź podkreślenia miejsca sekwencji). Ułatwia to porównać literałów XML w kodzie z dokumentów XML.  
  
 Kompilator traktuje znaki kontynuacji wiersza jako część literału XML. W związku z tym należy używać sekwencji wprowadź podkreślenia miejsca tylko wtedy, gdy jego [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] obiektu.  
  
 Jednak potrzebne znaki kontynuacji wiersza, jeśli masz wielowierszowych wyrażeń w wyrażenia osadzonego. Aby uzyskać więcej informacji, zobacz [wyrażenia osadzone w XML](../../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md).  
  
## <a name="embedding-queries-in-xml-literals"></a>Osadzanie zapytań w literałach XML  
 Zapytania można użyć w wyrażeniu osadzonych. Po wykonaniu tej czynności elementów zwróconych przez zapytanie są dodawane do elementu XML. Dzięki temu można dodać zawartość dynamiczna, takich jak wynik kwerendy użytkownika do literału XML.  
  
 Na przykład w poniższym kodzie użyto osadzonego zapytania do tworzenia elementów XML z elementów członkowskich `phoneNumbers2` tablicy, a następnie dodać tych elementów jako elementy podrzędne `contact2`.  
  
 [!code-vb[VbXMLSamples#7](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-literals-overview_3.vb)]  
  
## <a name="how-the-compiler-creates-objects-from-xml-literals"></a>Jak kompilator tworzy obiekty na podstawie literałów XML  
 Kompilator Visual Basic tłumaczy literałów XML na wywołania odpowiednikiem [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] konstruktorów w celu zbudowania [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] obiektu. Na przykład kompilator Visual Basic przekształci Poniższy przykładowy kod do wywołania <xref:System.Xml.Linq.XProcessingInstruction> konstruktora dla instrukcji wersji XML, wywołań <xref:System.Xml.Linq.XElement> Konstruktor `<contact>`, `<name>`, i `<phone>` elementy i wywołania <xref:System.Xml.Linq.XAttribute> Konstruktor `type` atrybutu. W szczególności podane atrybuty w następującym przykładzie, kompilator Visual Basic wywoła <xref:System.Xml.Linq.XAttribute.%23ctor%28System.Xml.Linq.XName%2CSystem.Object%29> Konstruktor dwa razy. Pierwszy będzie przekazać wartość `type` dla `name` parametr i wartość `home` dla `value` parametru. Drugi będzie również przekazać wartość `type` dla `name` parametru, ale wartość `work` dla `value` parametru.  
  
 [!code-vb[VbXMLSamples#6](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-literals-overview_2.vb)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Xml.Linq.XElement>  
 [Tworzenie XML w Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)  
 [Wyrażenia osadzone w XML](../../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md)  
 [Literał dokumentu XML](../../../../visual-basic/language-reference/xml-literals/xml-document-literal.md)  
 [Literał elementu XML](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)  
 [Literały XML](../../../../visual-basic/language-reference/xml-literals/index.md)
