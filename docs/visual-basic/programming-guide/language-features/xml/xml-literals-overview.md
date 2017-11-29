---
title: "Literały XML - Przegląd (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- XML literals [Visual Basic], about XML literals
- declaring XML literals [Visual Basic]
- LINQ to XML [Visual Basic], XML literals
- literals [Visual Basic], XML
ms.assetid: 37987c15-4ab8-471b-bd45-399816bfb57f
caps.latest.revision: "27"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 59ce79995025692428263120f9c21c7baf5cf231
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="xml-literals-overview-visual-basic"></a>Literały XML - Przegląd (Visual Basic)
*Literał XML* umożliwia dołączenie XML bezpośrednio do użytkownika [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] kodu. Reprezentuje składni literału XML [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] obiektów który jest podobny do składni XML 1.0. Ułatwia to programowo utworzyć elementów XML oraz dokumentów, ponieważ używany kod ma taką samą strukturę jak końcowego XML.  
  
 [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]kompiluje literałów XML do [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] obiektów. [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]udostępnia prosty model obiektów do tworzenia i manipulowanie XML, a ten model integruje się również z [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)]. Aby uzyskać więcej informacji, zobacz <xref:System.Xml.Linq.XElement>.  
  
 Można osadzić [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] wyrażenie w literał XML. W czasie wykonywania, aplikacja tworzy [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] obiekt dla każdego literal, zawierające wartości wyrażenia osadzone. Dzięki temu można określić zawartości dynamicznej wewnątrz literału XML. Aby uzyskać więcej informacji, zobacz [wyrażenia osadzone w XML](../../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md).  
  
 Aby uzyskać więcej informacji na temat różnic między składni literału XML i składni XML 1.0, zobacz [literały XML i specyfikacja XML 1.0](../../../../visual-basic/programming-guide/language-features/xml/xml-literals-and-the-xml-1-0-specification.md).  
  
## <a name="simple-literals"></a>Literały proste  
 Można utworzyć [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] obiektu w Twojej [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] kodu, wpisując lub wklejając w prawidłowym kodem XML. Literał elementu XML zwraca <xref:System.Xml.Linq.XElement> obiektu. Aby uzyskać więcej informacji, zobacz [literał elementu XML](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md) i [literały XML i specyfikacja XML 1.0](../../../../visual-basic/programming-guide/language-features/xml/xml-literals-and-the-xml-1-0-specification.md). Poniższy przykład tworzy element XML, który ma kilka elementów podrzędnych.  
  
 [!code-vb[VbXMLSamples#5](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-literals-overview_1.vb)]  
  
 Można utworzyć dokumentu XML, uruchamiając literału z XML `<?xml version="1.0"?>`, jak pokazano w poniższym przykładzie. Literał dokumentu XML zwraca <xref:System.Xml.Linq.XDocument> obiektu. Aby uzyskać więcej informacji, zobacz [literał dokumentu XML](../../../../visual-basic/language-reference/xml-literals/xml-document-literal.md).  
  
 [!code-vb[VbXMLSamples#6](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-literals-overview_2.vb)]  
  
> [!NOTE]
>  Składnia literału XML w [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] nie jest taka sama jak składni w specyfikacji XML 1.0. Aby uzyskać więcej informacji, zobacz [literały XML i specyfikacja XML 1.0](../../../../visual-basic/programming-guide/language-features/xml/xml-literals-and-the-xml-1-0-specification.md).  
  
## <a name="line-continuation"></a>Kontynuacja wiersza  
 Literał XML może obejmować wiele wierszy bez użycia znaki kontynuacji wiersza (wprowadź podkreślenia miejsca sekwencji). Ułatwia to porównać literałów XML w kodzie z dokumentów XML.  
  
 Kompilator traktuje znaki kontynuacji wiersza jako część literału XML. W związku z tym należy używać sekwencji wprowadź podkreślenia miejsca tylko wtedy, gdy jego [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] obiektu.  
  
 Jednak potrzebne znaki kontynuacji wiersza, jeśli masz wielowierszowych wyrażeń w wyrażenia osadzonego. Aby uzyskać więcej informacji, zobacz [wyrażenia osadzone w XML](../../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md).  
  
## <a name="embedding-queries-in-xml-literals"></a>Osadzanie zapytań w literałach XML  
 Zapytania można użyć w wyrażeniu osadzonych. Po wykonaniu tej czynności elementów zwróconych przez zapytanie są dodawane do elementu XML. Dzięki temu można dodać zawartość dynamiczna, takich jak wynik kwerendy użytkownika do literału XML.  
  
 Na przykład w poniższym kodzie użyto osadzonego zapytania do tworzenia elementów XML z elementów członkowskich `phoneNumbers2` tablicy, a następnie dodać tych elementów jako elementy podrzędne `contact2`.  
  
 [!code-vb[VbXMLSamples#7](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-literals-overview_3.vb)]  
  
## <a name="how-the-compiler-creates-objects-from-xml-literals"></a>Jak kompilator tworzy obiekty na podstawie literałów XML  
 [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] Kompilatora tłumaczy literałów XML na wywołania odpowiednikiem [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] konstruktorów w celu zbudowania [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] obiektu. Na przykład [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] kompilatora przekształci Poniższy przykładowy kod do wywołania <xref:System.Xml.Linq.XProcessingInstruction> konstruktora dla instrukcji wersji XML, wywołań <xref:System.Xml.Linq.XElement> Konstruktor `<contact>`, `<name>`i `<phone>`elementów i wywołania <xref:System.Xml.Linq.XAttribute> Konstruktor `type` atrybutu. W szczególności podane atrybuty w następującym przykładowym [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] wywoła kompilatora <xref:System.Xml.Linq.XAttribute.%23ctor%28System.Xml.Linq.XName%2CSystem.Object%29> Konstruktor dwa razy. Pierwszy będzie przekazać wartość `type` dla `name` parametr i wartość `home` dla `value` parametru. Drugi będzie również przekazać wartość `type` dla `name` parametru, ale wartość `work` dla `value` parametru.  
  
 [!code-vb[VbXMLSamples#6](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-literals-overview_2.vb)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Xml.Linq.XElement>  
 [Tworzenie XML w Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)  
 [Wyrażenia osadzone w XML](../../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md)  
 [Literał dokumentu XML](../../../../visual-basic/language-reference/xml-literals/xml-document-literal.md)  
 [Literał elementu XML](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)  
 [Literały XML](../../../../visual-basic/language-reference/xml-literals/index.md)
