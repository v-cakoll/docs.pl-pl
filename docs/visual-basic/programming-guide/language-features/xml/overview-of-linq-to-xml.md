---
title: Przegląd LINQ to XML w Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- LINQ to XML [Visual Basic], about LINQ to XML
- LINQ [Visual Basic], LINQ to XML
ms.assetid: 01c62a79-6d58-468e-84fb-039c05947701
ms.openlocfilehash: 91f622b9eecdd1aec8b9361493095e92a851988e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61761841"
---
# <a name="overview-of-linq-to-xml-in-visual-basic"></a>Przegląd LINQ to XML w Visual Basic
Visual Basic zapewnia obsługę [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] przy użyciu literałów XML i właściwości osi XML. Dzięki temu można używać składni znana i wygodna do pracy z danymi XML w kodzie języka Visual Basic. *Literały XML* umożliwiają objęcie XML bezpośrednio w kodzie. *Właściwości osi XML* umożliwiają dostęp do węzłów podrzędnych, węzły podrzędne i atrybuty literał XML. Aby uzyskać więcej informacji, zobacz [literały XML-Przegląd](../../../../visual-basic/programming-guide/language-features/xml/xml-literals-overview.md) i [uzyskiwania dostępu do XML w Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/accessing-xml.md).  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] jest programowania XML w pamięci zaprojektowane specjalnie, aby móc korzystać z interfejsu API [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)]. Mimo że można wywołać [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] API bezpośrednio, tylko Visual Basic umożliwia deklarowanie literałów XML i uzyskać bezpośredni dostęp do właściwości osi XML.  
  
> [!NOTE]
>  Literały XML i właściwości osi XML nie są obsługiwane w kodzie deklaratywne na stronie ASP.NET. Aby korzystać z funkcji XML w Visual Basic, umieść kod w osobna strona kodu w aplikacji programu ASP.NET.  
  
 ![Link do wideo](../../../../visual-basic/programming-guide/language-features/xml/media/playvideo.gif "PlayVideo") uzyskać pokrewne pokazy wideo, zobacz [jak zacząć korzystać z LINQ to XML?](/aspnet/web-forms/videos/data-access/linq-videos-from-the-vb-team/how-do-i-get-started-with-linq-to-xml) i [jak mogę utworzyć arkusze kalkulacyjne programu Excel za pomocą LINQ to XML?](/aspnet/web-forms/videos/data-access/linq-videos-from-the-vb-team/how-do-i-create-excel-spreadsheets-using-linq-to-xml).  
  
## <a name="creating-xml"></a>Tworzenie kodu XML  
 Istnieją dwa sposoby tworzenia drzew XML w Visual Basic. Można zadeklarować literału bezpośrednio w kodzie XML lub użyć [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] interfejsów API, aby utworzyć drzewo. Oba procesy Włącz kod w celu odzwierciedlenia końcowego struktury drzewa XML. Na przykład poniższy kod tworzy XML element:  
  
 [!code-vb[VbXmlSamples#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples2.vb#5)]  
  
 Aby uzyskać więcej informacji, zobacz [tworzenie XML w Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md).  
  
## <a name="accessing-and-navigating-xml"></a>Uzyskiwanie dostępu do ani nawigować XML  
 Zapewnia właściwości osi XML do uzyskiwania dostępu i przechodząc struktury XML w Visual Basic. Te właściwości zostanie umożliwiony dostęp do elementów XML oraz atrybuty przez określenie nazwy elementów podrzędnych XML. Alternatywnie, możesz jawnie wywołać [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] metody nawigacji i lokalizowania elementów i atrybutów. Na przykład poniższy kod używa właściwości osi XML do odwoływania się do atrybuty i elementy podrzędne elementu XML. Przykład kodu wykorzystuje [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] zapytanie w celu pobierania elementów podrzędnych i zwracania je jako elementy XML, efektywnie wykonywanie transformacji.  
  
 [!code-vb[VbXmlSamples#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples3.vb#8)]  
  
 Aby uzyskać więcej informacji, zobacz [uzyskiwania dostępu do XML w Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/accessing-xml.md).  
  
## <a name="xml-namespaces"></a>Obszary nazw XML  
 Visual Basic można określić alias dla globalnej przestrzeni nazw XML przy użyciu `Imports` instrukcji. Poniższy przykład pokazuje, jak używać `Imports` instrukcję, aby zaimportować obszar nazw XML:  
  
 [!code-vb[VbXMLSamples#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples1.vb#1)]  
  
 Gdy dostęp do właściwości osi XML i deklarowanie literałów XML do dokumentów XML i elementy, można użyć aliasu przestrzeni nazw XML.  
  
 Możesz pobrać <xref:System.Xml.Linq.XNamespace> obiekt dla prefiksu określonego obszaru nazw, przy użyciu [getxmlnamespace — Operator](../../../../visual-basic/language-reference/operators/getxmlnamespace-operator.md).  
  
 Aby uzyskać więcej informacji, zobacz [Importy — instrukcja (XML Namespace)](../../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md).  
  
### <a name="using-xml-namespaces-in-xml-literals"></a>Używanie przestrzeni nazw XML w literałach XML  
 Poniższy przykład pokazuje, jak utworzyć <xref:System.Xml.Linq.XElement> obiekt, który korzysta z globalnej przestrzeni nazw `ns`:  
  
 [!code-vb[VbXMLSamples#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples1.vb#2)]  
  
 Kompilator języka Visual Basic tłumaczy literały XML, które zawiera aliasy obszaru nazw XML na równoważne kod, który używa notacji XML przy użyciu przestrzeni nazw XML, za pomocą `xmlns` atrybutu. Po skompilowaniu kodu w poprzedniej sekcji przykład generuje zasadniczo tego samego pliku wykonywalnego kodu w poniższym przykładzie:  
  
 [!code-vb[VbXMLSamples#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples1.vb#3)]  
  
### <a name="using-xml-namespaces-in-xml-axis-properties"></a>Właściwości osi XML przy użyciu przestrzeni nazw XML  
 Zadeklarowane w literałach XML obszary nazw XML nie są dostępne do użycia w właściwości osi XML. Jednak globalnej przestrzeni nazw może być używany z właściwości osi XML. Użyj dwukropka do oddzielenia prefiks przestrzeni nazw XML na podstawie nazwy elementu lokalnego. Poniżej znajduje się przykład:  
  
 [!code-vb[VbXMLSamples#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples1.vb#4)]  
  
## <a name="see-also"></a>Zobacz także

- [XML](../../../../visual-basic/programming-guide/language-features/xml/index.md)
- [Tworzenie XML w Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
- [Uzyskiwanie dostępu do XML w Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/accessing-xml.md)
- [Manipulowanie XML w Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/manipulating-xml.md)
