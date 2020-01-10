---
title: Przekształcenia XSLT w różnych magazynach
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 369850e9-004a-45d2-b5c3-5060d9135adb
ms.openlocfilehash: 490ac30a3e4f0c50cb5d011f1d583c6e5ce9e672
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709663"
---
# <a name="xslt-transformations-over-different-stores"></a>Przekształcenia XSLT w różnych magazynach
> [!NOTE]
> Klasa <xref:System.Xml.Xsl.XslTransform> jest przestarzała w .NET Framework 2,0. Można wykonywać przekształcenia Extensible Stylesheet Language for Transformations (XSLT) przy użyciu klasy <xref:System.Xml.Xsl.XslCompiledTransform>. Aby uzyskać więcej informacji, zobacz [Używanie klasy XslCompiledTransform](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) i [Migrowanie z klasy XslTransform](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md) .  
  
 Klasy ADO.NET i XML w .NET Framework zapewniają ujednolicony model programowania do uzyskiwania dostępu do danych. Te dane są reprezentowane jako dane XML, które są tekstem rozdzielanym przez Tagi i dane relacyjne, które są tabelami zawierającymi wiersze i kolumny. KOD XML w .NET Framework odczytuje dane XML z dowolnego strumienia danych do drzew węzłów XML Document Object Model (DOM), w których dane mogą być programistycznie dostępne, podczas gdy ADO.NET zapewnia dostęp do danych relacyjnych w obiekcie <xref:System.Data.DataSet> i manipulowanie nimi.  
  
 DOM XML zapewnia dostęp do danych w dokumentach XML i dodatkowych klasach do odczytu, zapisu i nawigowania w dokumentach XML. Te klasy są obsługiwane w przestrzeni nazw <xref:System.Xml>, która również łączy XML DOM z usługami dostępu do danych udostępnionymi przez ADO.NET. <xref:System.Xml.XmlDataDocument> zapewnia dostęp relacyjny do danych. <xref:System.Xml.XmlDataDocument> mapuje XML na dane relacyjne w <xref:System.Data.DataSet>ADO.NET. Wszystkie aplikacje oparte na .NET Framework mogą używać klas w przestrzeni nazw <xref:System.Xml> do uzyskiwania dostępu do dokumentów XML i danych relacyjnych w <xref:System.Xml.XmlDataDocument>i manipulowania nimi. Ta implementacja obsługuje architektury n-warstwowe na potrzeby zbierania i dystrybuowania danych. Aby uzyskać więcej informacji, zobacz temat [Integracja XML z danymi relacyjnymi i ADO.NET](../../../../docs/standard/data/xml/xml-integration-with-relational-data-and-adonet.md).  
  
## <a name="see-also"></a>Zobacz także

- [Implementowanie procesora XSLT przy użyciu klasy XslTransform](../../../../docs/standard/data/xml/xsltransform-class-implements-the-xslt-processor.md)
