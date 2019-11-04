---
title: Opcje przetwarzania XML
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 33ced8ee-1745-4e71-8dee-ebe70ec067c7
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3fc7def48bff71935fce7c6ed914ad20c66e5182
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/01/2019
ms.locfileid: "73425176"
---
# <a name="xml-processing-options"></a>Opcje przetwarzania XML
Zapoznaj się z poniższymi tabelami, aby zapoznać się z listą technologii firmy Microsoft, których można użyć do przetwarzania danych XML.  
  
## <a name="net-framework-options"></a>Opcje .NET Framework  
  
|**Zaznaczyć**|**Typ przetwarzania**|**Opis**|  
|----------------|-------------------------|---------------------|  
|[LINQ to XML (C#)](../../../csharp/programming-guide/concepts/linq/linq-to-xml-overview.md) <br/> [LINQ to XML (Visual Basic)](../../../visual-basic/programming-guide/concepts/linq/linq-to-xml.md) <br />(<xref:System.Xml.Linq> przestrzeń nazw)|W pamięci|— Oparta na technologii .NET Framework Language-Integrated Query (LINQ).<br />— Zapewnia środowisko zapytań podobne do SQL dla obiektów, danych relacyjnych i danych XML.<br />— Oferuje intuicyjne możliwości tworzenia i przekształcania dokumentów.<br />— Użyj tej opcji, jeśli piszesz nowy kod.|  
|<xref:System.Xml.XmlReader?displayProperty=nameWithType>|Oparte na strumieniu|— Zapewnia szybki, niebuforowany, w sposób umożliwiający dostęp do danych XML.<br />— Można tworzyć obiekty za pomocą metody <xref:System.Xml.XmlReader.Create%2A?displayProperty=nameWithType> i określać zestaw funkcji do włączenia na obiekcie przy użyciu klasy <xref:System.Xml.XmlReaderSettings>.|  
|<xref:System.Xml.XmlWriter?displayProperty=nameWithType>|Oparte na strumieniu|— Zapewnia szybki, niebuforowany, tylko do przodu sposób generowania danych XML.<br />— Można tworzyć obiekty za pomocą metody <xref:System.Xml.XmlWriter.Create%2A?displayProperty=nameWithType> i określać zestaw funkcji do włączenia na obiekcie przy użyciu klasy <xref:System.Xml.XmlWriterSettings>.|  
|<xref:System.Xml.XmlDocument?displayProperty=nameWithType>|W pamięci|-Implementuje zalecenia dotyczące poziomu 1 podstawowego i [modelu dom](https://www.w3.org/TR/DOM-Level-2-Core/) w [formacie W3C Document Object Model (dom)](https://www.w3.org/TR/REC-DOM-Level-1/level-one-core.html) .<br />— Można tworzyć, wstawiać, usuwać i modyfikować węzły przy użyciu metod i właściwości w oparciu o znany model DOM.<br />— Użyj tej opcji, jeśli modyfikujesz istniejący kod korzystający z W3C DOM.|  
|<xref:System.Xml.XPath.XPathNavigator?displayProperty=nameWithType>|W pamięci|— Oferuje kilka opcji edycji i możliwości nawigacji przy użyciu modelu kursorów.<br />-Dokumenty XML mogą być zawarte w obiekcie <xref:System.Xml.XPath.XPathDocument> lub <xref:System.Xml.XmlDocument>.<br />— Zapewnia doskonałą wydajność przetwarzania plików XML w trybie tylko do odczytu.<br />— Użyj tej opcji, jeśli modyfikujesz istniejący kod przy użyciu zapytań XPath lub transformacji XSLT.|  
|<xref:System.Xml.Xsl.XslCompiledTransform>|W pamięci|— Oferuje opcje przekształcania danych XML przy użyciu transformacji XSL.<br />- [Kompilator XSLT (xsltc. exe)](../../../../docs/standard/data/xml/xslt-compiler-xsltc-exe.md) umożliwia odwoływanie się do wstępnie skompilowanych transformacji w aplikacji.|  
  
## <a name="win32-and-com-based-options"></a>Opcje oparte na systemie Win32 i modelu COM  
  
|**Zaznaczyć**|**Opis**|  
|----------------|---------------------|  
|[XmlLite](https://docs.microsoft.com/previous-versions/windows/desktop/ms752872(v=vs.85))|-Szybki, bezpieczny, nieobsługujący buforowanie parser XML, który ułatwia tworzenie aplikacji XML o wysokiej wydajności.<br />-Działa z dowolnym językiem, który może korzystać z bibliotek dołączanych dynamicznie (dll); Zalecamy korzystanie z C++programu.|  
|[PROGRAMU](https://docs.microsoft.com/previous-versions/windows/desktop/ms763742(v=vs.85))|— Technologia oparta na modelu COM służąca do przetwarzania kodu XML, który jest dołączony do systemu operacyjnego Windows.<br />— Zapewnia natywną implementację modelu DOM z obsługą języka XPath i XSLT.<br />-Zawiera parser oparty na zdarzeniach SAX2.|  
  
## <a name="see-also"></a>Zobacz także

- [Przetwarzanie danych XML przy użyciu modelu DOM](../../../../docs/standard/data/xml/process-xml-data-using-the-dom-model.md)
- [Przetwarzanie danych XML przy użyciu modelu danych XPath](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)
- [Kompilator XSLT (xsltc.exe)](../../../../docs/standard/data/xml/xslt-compiler-xsltc-exe.md)
