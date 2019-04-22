---
title: Literały XML - Przegląd (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- XML literals [Visual Basic], about XML literals
- declaring XML literals [Visual Basic]
- LINQ to XML [Visual Basic], XML literals
- literals [Visual Basic], XML
ms.assetid: 37987c15-4ab8-471b-bd45-399816bfb57f
ms.openlocfilehash: a7b70669131ae35135088418e4b33b3ae289d322
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "58839889"
---
# <a name="xml-literals-overview-visual-basic"></a>Literały XML - Przegląd (Visual Basic)
*Literał XML* umożliwia włączenie XML bezpośrednio w kodzie języka Visual Basic. Literał składnia XML przedstawia [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] obiektów który jest podobny do składni XML 1.0. Ta funkcja ułatwia programistycznym tworzeniu elementów XML i dokumentów, ponieważ kod ma tę samą strukturę jako ostatecznego XML.  
  
 Visual Basic kompiluje literałów XML do [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] obiektów. [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] udostępnia prosty model obiektu do tworzenia i manipulowania XML i ten model dobrze integruje się z [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)]. Aby uzyskać więcej informacji, zobacz <xref:System.Xml.Linq.XElement>.  
  
 Wyrażenie języka Visual Basic można osadzić w literał XML. W czasie wykonywania, aplikacja tworzy [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] obiekt dla każdego literału, zawierające wartości wyrażenia osadzone. Dzięki temu można określić zawartość dynamiczna wewnątrz literał XML. Aby uzyskać więcej informacji, zobacz [wyrażenia osadzone w XML](../../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md).  
  
 Aby uzyskać więcej informacji na temat różnic między składni literał XML i składni XML 1.0, zobacz [literały XML i specyfikacja XML 1.0](../../../../visual-basic/programming-guide/language-features/xml/xml-literals-and-the-xml-1-0-specification.md).  
  
## <a name="simple-literals"></a>Literały prosty  
 Możesz utworzyć [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] obiektu w kodzie języka Visual Basic, wpisując lub wklejając w prawidłowym kodem XML. Literał elementu XML zwraca <xref:System.Xml.Linq.XElement> obiektu. Aby uzyskać więcej informacji, zobacz [literał elementu XML](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md) i [literały XML i specyfikacja XML 1.0](../../../../visual-basic/programming-guide/language-features/xml/xml-literals-and-the-xml-1-0-specification.md). Poniższy przykład tworzy element XML, który ma kilka elementów podrzędnych.  
  
 [!code-vb[VbXMLSamples#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples2.vb#5)]  
  
 Można utworzyć dokumentu XML, uruchamiając literał za pomocą XML `<?xml version="1.0"?>`, jak pokazano w poniższym przykładzie. Literał dokumentu XML zwraca <xref:System.Xml.Linq.XDocument> obiektu. Aby uzyskać więcej informacji, zobacz [literał dokumentu XML](../../../../visual-basic/language-reference/xml-literals/xml-document-literal.md).  
  
 [!code-vb[VbXMLSamples#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples2.vb#6)]  
  
> [!NOTE]
>  Składnia literał XML w Visual Basic nie jest taka sama jak w składni Specyfikacja XML 1.0. Aby uzyskać więcej informacji, zobacz [literały XML i specyfikacja XML 1.0](../../../../visual-basic/programming-guide/language-features/xml/xml-literals-and-the-xml-1-0-specification.md).  
  
## <a name="line-continuation"></a>Kontynuacja wiersza  
 Literał XML może obejmować wiele wierszy, bez używania znaków kontynuacji wiersza (wprowadź podkreślenia miejsca na kolejny). Ta funkcja ułatwia porównanie literałów XML w kodzie za pomocą dokumentów XML.  
  
 Kompilator traktuje znaki kontynuacji wiersza, jako część literał XML. Dlatego należy używać sekwencji wprowadź podkreślenia miejsce tylko wtedy, gdy należy ono do [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] obiektu.  
  
 Należy jednak znaki kontynuacji wiersza w przypadku wielowierszowe wyrażenia w wyrażeniu osadzonych. Aby uzyskać więcej informacji, zobacz [wyrażenia osadzone w XML](../../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md).  
  
## <a name="embedding-queries-in-xml-literals"></a>Osadzanie zapytania w literałach XML  
 Zapytania można użyć w wyrażeniu osadzonych. Gdy to zrobisz, elementów zwróconych przez zapytanie są dodawane do elementu XML. Dzięki temu można dodać zawartość dynamiczną, takich jak wynik zapytania użytkownika do literał XML.  
  
 Na przykład w poniższym kodzie użyto osadzonego zapytania do tworzenia elementów XML z elementów członkowskich `phoneNumbers2` macierz, a następnie dodaj te elementy jako elementy podrzędne `contact2`.  
  
 [!code-vb[VbXMLSamples#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples2.vb#7)]  
  
## <a name="how-the-compiler-creates-objects-from-xml-literals"></a>Jak kompilator tworzy obiekty z literałów XML  
 Kompilator Visual Basic tłumaczy literałów XML na wywołania do równowartości [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] konstruktorów w celu zbudowania [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] obiektu. Na przykład, kompilator Visual Basic tłumaczenia w poniższym przykładzie kodu na wywołanie <xref:System.Xml.Linq.XProcessingInstruction> wywołania konstruktora dla instrukcji wersji XML, <xref:System.Xml.Linq.XElement> Konstruktor `<contact>`, `<name>`, i `<phone>` elementy i wywołania <xref:System.Xml.Linq.XAttribute> Konstruktor `type` atrybutu. W szczególności podane atrybuty w następującym przykładzie, kompilator Visual Basic wywoła <xref:System.Xml.Linq.XAttribute.%23ctor%28System.Xml.Linq.XName%2CSystem.Object%29> Konstruktor dwa razy. Pierwszy przekazują wartość `type` dla `name` parametr i wartość `home` dla `value` parametru. Drugi będzie również przekazać wartość `type` dla `name` parametru, ale wartość `work` dla `value` parametru.  
  
 [!code-vb[VbXMLSamples#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples2.vb#6)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Xml.Linq.XElement>
- [Tworzenie XML w Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
- [Wyrażenia osadzone w XML](../../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md)
- [Literał dokumentu XML](../../../../visual-basic/language-reference/xml-literals/xml-document-literal.md)
- [Literał elementu XML](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)
- [Literały XML](../../../../visual-basic/language-reference/xml-literals/index.md)
