---
title: Przekształcenia XSLT w różnych magazynach
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 369850e9-004a-45d2-b5c3-5060d9135adb
ms.openlocfilehash: 0eb98aad00227688df3e097ad674b44a29e5cb1a
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84281716"
---
# <a name="xslt-transformations-over-different-stores"></a>Przekształcenia XSLT w różnych magazynach
> [!NOTE]
> <xref:System.Xml.Xsl.XslTransform>Klasa jest przestarzała w .NET Framework 2,0. Można wykonać przekształcenia Extensible Stylesheet Language for Transformations (XSLT) przy użyciu <xref:System.Xml.Xsl.XslCompiledTransform> klasy. Aby uzyskać więcej informacji, zobacz [Używanie klasy XslCompiledTransform](using-the-xslcompiledtransform-class.md) i [Migrowanie z klasy XslTransform](migrating-from-the-xsltransform-class.md) .  
  
 Klasy ADO.NET i XML w .NET Framework zapewniają ujednolicony model programowania do uzyskiwania dostępu do danych. Te dane są reprezentowane jako dane XML, które są tekstem rozdzielanym przez Tagi i dane relacyjne, które są tabelami zawierającymi wiersze i kolumny. KOD XML w .NET Framework odczytuje dane XML z dowolnego strumienia danych do drzew drzewa XML Document Object Model (DOM), w których dane mogą być programistycznie dostępne, podczas gdy ADO.NET zapewnia metodę dostępu i manipulowania danymi relacyjnymi w <xref:System.Data.DataSet> obiekcie.  
  
 DOM XML zapewnia dostęp do danych w dokumentach XML i dodatkowych klasach do odczytu, zapisu i nawigowania w dokumentach XML. Te klasy są obsługiwane w <xref:System.Xml> przestrzeni nazw, co również łączy XML dom z usługami dostępu do danych udostępnionymi przez ADO.NET. <xref:System.Xml.XmlDataDocument>Zapewnia dostęp relacyjny do danych. <xref:System.Xml.XmlDataDocument>Mapowanie XML na dane relacyjne w ADO.NET <xref:System.Data.DataSet> . Wszystkie aplikacje oparte na .NET Framework mogą używać klas w <xref:System.Xml> przestrzeni nazw do uzyskiwania dostępu do dokumentów XML i danych relacyjnych w programie oraz manipulowania nimi <xref:System.Xml.XmlDataDocument> . Ta implementacja obsługuje architektury n-warstwowe na potrzeby zbierania i dystrybuowania danych. Aby uzyskać więcej informacji, zobacz temat [Integracja XML z danymi relacyjnymi i ADO.NET](xml-integration-with-relational-data-and-adonet.md).  
  
## <a name="see-also"></a>Zobacz także

- [Implementowanie procesora XSLT przy użyciu klasy XslTransform](xsltransform-class-implements-the-xslt-processor.md)
