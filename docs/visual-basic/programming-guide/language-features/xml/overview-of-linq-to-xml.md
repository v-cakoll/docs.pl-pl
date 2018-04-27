---
title: Przegląd LINQ to XML w Visual Basic
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- LINQ to XML [Visual Basic], about LINQ to XML
- LINQ [Visual Basic], LINQ to XML
ms.assetid: 01c62a79-6d58-468e-84fb-039c05947701
caps.latest.revision: 17
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: be9038fb194c0e4890593b4b80751a477def20a7
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="overview-of-linq-to-xml-in-visual-basic"></a>Przegląd LINQ to XML w Visual Basic
Visual Basic zapewnia obsługę [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] przy użyciu literałów XML i właściwości osi XML. Dzięki temu można używać składni znanych i wygodny do pracy z XML w kodzie języka Visual Basic. *Literały XML* umożliwiają dodawanie bezpośrednio w kodzie XML. *Właściwości osi XML* umożliwiają dostęp do węzłów podrzędnych węzłów elementów podrzędnych i atrybuty literał XML. Aby uzyskać więcej informacji, zobacz [literały XML-Przegląd](../../../../visual-basic/programming-guide/language-features/xml/xml-literals-overview.md) i [podczas uzyskiwania dostępu do XML w Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/accessing-xml.md).  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] jest XML w pamięci programowania zaprojektowane specjalnie, aby móc korzystać z interfejsu API [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)]. Mimo że można wywołać [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] API bezpośrednio, tylko Visual Basic umożliwia deklarowanie literałów XML i bezpośredni dostęp do właściwości osi XML.  
  
> [!NOTE]
>  Literały XML i właściwości osi XML nie są obsługiwane w kodzie deklaratywne strony ASP.NET. Aby używać funkcji XML w Visual Basic, umieść swój kod na stronie związane z kodem w aplikacji ASP.NET.  
  
 ![łącze do wideo](../../../../visual-basic/programming-guide/language-features/xml/media/playvideo.gif "PlayVideo") dla powiązanych pokazów wideo, zobacz [jak rozpocząć pracę z LINQ do XML?](http://go.microsoft.com/fwlink/?LinkId=143034) i [jak utworzyć arkusze programu Excel za pomocą LINQ do XML?](http://go.microsoft.com/fwlink/?LinkId=143536).  
  
## <a name="creating-xml"></a>Tworzenie XML  
 Istnieją dwa sposoby tworzenia drzewa XML w Visual Basic. Można zadeklarować literału bezpośrednio w kodzie XML, albo użyć [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] interfejsów API, aby utworzyć drzewo. Oba procesy Włącz kod w celu odzwierciedlenia końcowego struktury drzewa XML. Na przykład poniższy przykład kodu tworzy XML element:  
  
 [!code-vb[VbXmlSamples#5](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/overview-of-linq-to-xml_1.vb)]  
  
 Aby uzyskać więcej informacji, zobacz [tworzenie XML w Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md).  
  
## <a name="accessing-and-navigating-xml"></a>Uzyskiwanie dostępu i przechodząc XML  
 Visual Basic zawiera właściwości osi XML do uzyskiwania dostępu i nawigacja struktury XML. Te właściwości umożliwia dostęp do elementów XML oraz atrybuty przez określenie nazw elementów podrzędnych XML. Alternatywnie można jawnie wywołać [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] metody do nawigowania i znajdowanie elementów i atrybutów. Na przykład poniższy przykładowy kod używa właściwości osi XML do odwoływania się do atrybuty i elementy podrzędne elementu XML. Przykład kodu wykorzystuje [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] zapytania w celu pobierania elementów podrzędnych i zwracania je jako elementy XML, efektywnie wykonywania transformacji.  
  
 [!code-vb[VbXmlSamples#8](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/overview-of-linq-to-xml_2.vb)]  
  
 Aby uzyskać więcej informacji, zobacz [podczas uzyskiwania dostępu do XML w Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/accessing-xml.md).  
  
## <a name="xml-namespaces"></a>Przestrzenie nazw XML  
 Visual Basic umożliwia określenie aliasu globalnej przestrzeni nazw XML przy użyciu `Imports` instrukcji. Poniższy przykład przedstawia użycie `Imports` instrukcji do zaimportowania do przestrzeni nazw XML:  
  
 [!code-vb[VbXMLSamples#1](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/overview-of-linq-to-xml_3.vb)]  
  
 Podczas dostępu do właściwości osi XML i deklarowanie literałów XML do dokumentów XML i elementy, można użyć aliasu przestrzeni nazw XML.  
  
 Możesz pobrać <xref:System.Xml.Linq.XNamespace> obiektu dla prefiksu przestrzeni nazw określonej za pomocą [operatora GetXmlNamespace](../../../../visual-basic/language-reference/operators/getxmlnamespace-operator.md).  
  
 Aby uzyskać więcej informacji, zobacz [Importy — instrukcja (XML Namespace)](../../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md).  
  
### <a name="using-xml-namespaces-in-xml-literals"></a>Używanie przestrzeni nazw XML w literałach XML  
 Poniższy przykład przedstawia sposób tworzenia <xref:System.Xml.Linq.XElement> obiekt, który korzysta z globalnej przestrzeni nazw `ns`:  
  
 [!code-vb[VbXMLSamples#2](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/overview-of-linq-to-xml_4.vb)]  
  
 Kompilator Visual Basic tłumaczy literałów XML, zawierające aliasów przestrzeni nazw XML na równoważne kod, który używa notacji XML przy użyciu przestrzeni nazw XML, z `xmlns` atrybutu. Podczas kompilacji, kod w przykładzie w poprzedniej sekcji tworzy zasadniczo tego samego kodu wykonywalnego jak w poniższym przykładzie:  
  
 [!code-vb[VbXMLSamples#3](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/overview-of-linq-to-xml_5.vb)]  
  
### <a name="using-xml-namespaces-in-xml-axis-properties"></a>Właściwości osi XML przy użyciu przestrzeni nazw XML  
 Przestrzenie nazw XML zadeklarowany w literałach XML nie są dostępne do użycia w właściwości osi XML. Jednak globalnej przestrzeni nazw może służyć z właściwości osi XML. Użyj dwukropka do oddzielania prefiks przestrzeni nazw XML na podstawie nazwy elementu lokalnego. Poniżej przedstawiono przykładowy:  
  
 [!code-vb[VbXMLSamples#4](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/overview-of-linq-to-xml_6.vb)]  
  
## <a name="see-also"></a>Zobacz też  
 [XML](../../../../visual-basic/programming-guide/language-features/xml/index.md)  
 [Tworzenie XML w Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)  
 [Uzyskiwanie dostępu do XML w Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/accessing-xml.md)  
 [Manipulowanie XML w Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/manipulating-xml.md)
