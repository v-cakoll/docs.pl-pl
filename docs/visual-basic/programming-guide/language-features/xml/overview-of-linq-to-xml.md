---
title: Przegląd interfejsu LINQ to XML
ms.date: 07/20/2015
helpviewer_keywords:
- LINQ to XML [Visual Basic], about LINQ to XML
- LINQ [Visual Basic], LINQ to XML
ms.assetid: 01c62a79-6d58-468e-84fb-039c05947701
ms.openlocfilehash: 0481a140541a7f45c682c5150bc1c3d647de90bd
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2020
ms.locfileid: "78266901"
---
# <a name="overview-of-linq-to-xml-in-visual-basic"></a>Przegląd LINQ to XML w Visual Basic
Visual Basic zapewnia [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] obsługę za pomocą literałów XML i właściwości osi XML. Dzięki temu można użyć znanej, wygodnej składni do pracy z xml w kodzie języka Visual Basic. *Literały XML* umożliwiają dołączanie kodu XML bezpośrednio do kodu. *Właściwości osi XML* umożliwiają dostęp do węzłów podrzędnych, węzłów podrzędnych i atrybutów literału XML. Aby uzyskać więcej informacji, zobacz [Omówienie literałów XML](../../../../visual-basic/programming-guide/language-features/xml/xml-literals-overview.md) i [uzyskiwanie dostępu do pliku XML w języku Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/accessing-xml.md).  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]to interfejs API programowania XML w pamięci zaprojektowany specjalnie w celu skorzystania z zapytania zintegrowanego z językiem (LINQ). Chociaż można wywołać interfejsy API LINQ bezpośrednio, tylko visual basic umożliwia deklarowanie literałów XML i bezpośredni dostęp do właściwości osi XML.  
  
> [!NOTE]
> Literały XML i właściwości osi XML nie są obsługiwane w kodzie deklaratywnym na stronie ASP.NET. Aby korzystać z funkcji XML języka Visual Basic, umieść kod na stronie związanej z kodem w aplikacji ASP.NET.  
  
 [Przycisk Odtwórz](./media/overview-of-linq-to-xml/play-video-icon-example.gif) Aby zapoznać się z powiązanymi prezentacjami wideo, zobacz [How Do I Create Excel Spreadsheets using LINQ to XML?](/aspnet/web-forms/videos/data-access/linq-videos-from-the-vb-team/how-do-i-create-excel-spreadsheets-using-linq-to-xml) [Jak rozpocząć pracę z LINQ do XML?](/aspnet/web-forms/videos/data-access/linq-videos-from-the-vb-team/how-do-i-get-started-with-linq-to-xml)
  
## <a name="creating-xml"></a>Tworzenie kodu XML  
 Istnieją dwa sposoby tworzenia drzew XML w języku Visual Basic. Można zadeklarować literał XML bezpośrednio w kodzie lub można użyć interfejsów API LINQ do utworzenia drzewa. Oba procesy umożliwiają kod odzwierciedlać ostateczną strukturę drzewa XML. Na przykład poniższy przykład kodu tworzy element XML:  
  
 [!code-vb[VbXmlSamples#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples2.vb#5)]  
  
 Aby uzyskać więcej informacji, zobacz [Tworzenie pliku XML w języku Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md).  
  
## <a name="accessing-and-navigating-xml"></a>Uzyskiwanie dostępu do xml i nawigowanie  
 Visual Basic zapewnia właściwości osi XML do uzyskiwania dostępu do struktur XML i nawigacji. Właściwości te umożliwiają dostęp do elementów XML i atrybutów, określając nazwy elementów podrzędnych XML. Alternatywnie można jawnie wywołać metody LINQ do nawigacji i lokalizowania elementów i atrybutów. Na przykład w poniższym przykładzie kodu użyto właściwości osi XML, aby odwołać się do atrybutów i elementów podrzędnych elementu XML. Przykładowy kod używa kwerendy LINQ do pobierania elementów podrzędnych i wyprowadzania ich jako elementów XML, skutecznie wykonując transformację.  
  
 [!code-vb[VbXmlSamples#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples3.vb#8)]  
  
 Aby uzyskać więcej informacji, zobacz [Uzyskiwanie dostępu do pliku XML w języku Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/accessing-xml.md).  
  
## <a name="xml-namespaces"></a>Przestrzenie nazw XML  
 Visual Basic umożliwia określenie aliasu do globalnego obszaru nazw `Imports` XML przy użyciu instrukcji. W poniższym przykładzie `Imports` pokazano, jak za pomocą instrukcji zaimportować obszar nazw XML:  
  
 [!code-vb[VbXMLSamples#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples1.vb#1)]  
  
 Alias obszaru nazw XML można używać podczas uzyskiwania dostępu do właściwości osi XML i deklarowania literałów XML dla dokumentów i elementów XML.  
  
 <xref:System.Xml.Linq.XNamespace> Obiekt dla określonego prefiksu obszaru nazw można pobrać za pomocą operatora [GetXmlNamespace](../../../../visual-basic/language-reference/operators/getxmlnamespace-operator.md).  
  
 Aby uzyskać więcej informacji, zobacz [Oświadczenie o imporcie (obszar nazw XML)](../../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md).  
  
### <a name="using-xml-namespaces-in-xml-literals"></a>Korzystanie z obszarów nazw XML w literałach XML  
 W poniższym przykładzie <xref:System.Xml.Linq.XElement> pokazano, jak utworzyć obiekt, który używa globalnego obszaru `ns`nazw:  
  
 [!code-vb[VbXMLSamples#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples1.vb#2)]  
  
 Kompilator języka Visual Basic tłumaczy literały XML zawierające aliasy obszaru nazw XML na równoważny kod, który `xmlns` używa notacji XML do używania obszarów nazw XML z atrybutem. Po skompilowaniu kod w przykładzie poprzedniej sekcji tworzy zasadniczo ten sam kod wykonywalny, co w poniższym przykładzie:  
  
 [!code-vb[VbXMLSamples#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples1.vb#3)]  
  
### <a name="using-xml-namespaces-in-xml-axis-properties"></a>Używanie obszarów nazw XML we właściwościach osi XML  
 Obszary nazw XML zadeklarowane w literałach XML nie są dostępne do użycia we właściwościach osi XML. Jednak globalne przestrzenie nazw mogą być używane z właściwościami osi XML. Użyj dwukropka, aby oddzielić prefiks obszaru nazw XML od nazwy elementu lokalnego. Oto przykład:  
  
 [!code-vb[VbXMLSamples#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples1.vb#4)]  
  
## <a name="see-also"></a>Zobacz też

- [Xml](../../../../visual-basic/programming-guide/language-features/xml/index.md)
- [Tworzenie XML w Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
- [Uzyskiwanie dostępu do XML w Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/accessing-xml.md)
- [Manipulowanie XML w Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/manipulating-xml.md)
