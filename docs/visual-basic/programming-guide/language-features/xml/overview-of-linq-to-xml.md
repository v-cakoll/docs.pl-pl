---
title: Przegląd LINQ to XML w Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- LINQ to XML [Visual Basic], about LINQ to XML
- LINQ [Visual Basic], LINQ to XML
ms.assetid: 01c62a79-6d58-468e-84fb-039c05947701
ms.openlocfilehash: 5080efdf10a8e3b1f6815e836f9fffe968a8e4e0
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69939247"
---
# <a name="overview-of-linq-to-xml-in-visual-basic"></a>Przegląd LINQ to XML w Visual Basic
Visual Basic zapewnia obsługę [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] za pomocą literałów XML i właściwości osi XML. Dzięki temu można używać znanej, wygodnej składni do pracy z danymi XML w kodzie Visual Basic. *Literały XML* umożliwiają dołączenie kodu XML bezpośrednio w kodzie. *Właściwości osi XML* umożliwiają dostęp do węzłów podrzędnych, węzłów podrzędnych i atrybutów literału XML. Aby uzyskać więcej informacji, zobacz [Omówienie literałów XML](../../../../visual-basic/programming-guide/language-features/xml/xml-literals-overview.md) i [Uzyskiwanie dostępu do kodu XML w Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/accessing-xml.md).  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]to interfejs API programowania w pamięci, zaprojektowany specjalnie z myślą o korzystaniu z programu [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)]. Chociaż można wywołać [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] interfejsy API bezpośrednio, tylko Visual Basic umożliwiają deklarowanie literałów XML i bezpośredni dostęp do właściwości osi XML.  
  
> [!NOTE]
> Literały XML i właściwości osi XML nie są obsługiwane w kodzie deklaratywnym na stronie ASP.NET. Aby korzystać z funkcji Visual Basic XML, należy umieścić kod na stronie powiązanej z kodem w aplikacji ASP.NET.  
  
 [Przycisk odtwarzania](./media/overview-of-linq-to-xml/play-video-icon-example.gif) Aby zapoznać się z pokrewnymi pokazami wideo, zobacz [jak rozpocząć pracę z LINQ to XML?](/aspnet/web-forms/videos/data-access/linq-videos-from-the-vb-team/how-do-i-get-started-with-linq-to-xml) i [jak utworzyć arkusze kalkulacyjne programu Excel przy użyciu LINQ to XML?](/aspnet/web-forms/videos/data-access/linq-videos-from-the-vb-team/how-do-i-create-excel-spreadsheets-using-linq-to-xml).   
  
## <a name="creating-xml"></a>Tworzenie kodu XML  
 Istnieją dwa sposoby tworzenia drzew XML w Visual Basic. Można zadeklarować literał XML bezpośrednio w kodzie lub użyć [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] interfejsów API do utworzenia drzewa. Oba procesy umożliwiają kod odzwierciedlający końcową strukturę drzewa XML. Na przykład poniższy kod ilustruje tworzenie elementu XML:  
  
 [!code-vb[VbXmlSamples#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples2.vb#5)]  
  
 Aby uzyskać więcej informacji, zobacz [Tworzenie kodu XML w Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md).  
  
## <a name="accessing-and-navigating-xml"></a>Uzyskiwanie dostępu do pliku XML i nawigowanie po nim  
 Visual Basic udostępnia właściwości osi XML na potrzeby uzyskiwania dostępu do struktur XML i nawigowania w nich. Te właściwości umożliwiają dostęp do elementów i atrybutów XML przez określenie nazw elementów podrzędnych XML. Alternatywnie można jawnie wywołać [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] metody nawigowania i lokalizowania elementów i atrybutów. Na przykład poniższy przykład kodu używa właściwości osi XML do odwoływania się do atrybutów i elementów podrzędnych elementu XML. W przykładzie kodu jest [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] wykorzystywane zapytanie do pobierania elementów podrzędnych i wyprowadzania ich jako elementów XML, co efektywnie wykonuje przekształcenie.  
  
 [!code-vb[VbXmlSamples#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples3.vb#8)]  
  
 Aby uzyskać więcej informacji, zobacz [Uzyskiwanie dostępu do kodu XML w Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/accessing-xml.md).  
  
## <a name="xml-namespaces"></a>Przestrzenie nazw XML  
 Visual Basic umożliwia określenie aliasu globalnej przestrzeni nazw XML przy użyciu `Imports` instrukcji. Poniższy przykład pokazuje, `Imports` jak używać instrukcji do importowania przestrzeni nazw XML:  
  
 [!code-vb[VbXMLSamples#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples1.vb#1)]  
  
 Można użyć aliasu przestrzeni nazw XML podczas uzyskiwania dostępu do właściwości osi XML i deklarowania literałów XML dla dokumentów i elementów XML.  
  
 Można pobrać <xref:System.Xml.Linq.XNamespace> obiekt dla określonego prefiksu przestrzeni nazw za pomocą [operatora GetXmlNamespace](../../../../visual-basic/language-reference/operators/getxmlnamespace-operator.md).  
  
 Aby uzyskać więcej informacji, zobacz Imports — [instrukcja (przestrzeń nazw XML)](../../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md).  
  
### <a name="using-xml-namespaces-in-xml-literals"></a>Używanie przestrzeni nazw XML w literałach XML  
 Poniższy przykład pokazuje, jak utworzyć <xref:System.Xml.Linq.XElement> obiekt, który używa globalnej przestrzeni nazw: `ns`  
  
 [!code-vb[VbXMLSamples#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples1.vb#2)]  
  
 Kompilator Visual Basic tłumaczy literały XML zawierające aliasy przestrzeni nazw XML na równoważny kod, który używa notacji XML do używania przestrzeni nazw XML, `xmlns` z atrybutem. Po skompilowaniu kod w powyższej sekcji jest w rzeczywistości tworzony jako ten sam kod wykonywalny, co Poniższy przykład:  
  
 [!code-vb[VbXMLSamples#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples1.vb#3)]  
  
### <a name="using-xml-namespaces-in-xml-axis-properties"></a>Używanie przestrzeni nazw XML we właściwościach osi XML  
 Przestrzenie nazw XML zadeklarowane w literałach XML nie są dostępne do użycia we właściwościach osi XML. Jednak globalne przestrzenie nazw mogą być używane z właściwościami osi XML. Użyj dwukropka, aby oddzielić prefiks przestrzeni nazw XML od nazwy elementu lokalnego. Oto przykład:  
  
 [!code-vb[VbXMLSamples#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples1.vb#4)]  
  
## <a name="see-also"></a>Zobacz także

- [XML](../../../../visual-basic/programming-guide/language-features/xml/index.md)
- [Tworzenie kodu XML w Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
- [Uzyskiwanie dostępu do pliku XML w Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/accessing-xml.md)
- [Manipulowanie XML w Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/manipulating-xml.md)
