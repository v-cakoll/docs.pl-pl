---
title: Opcje przetwarzania XML
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 33ced8ee-1745-4e71-8dee-ebe70ec067c7
caps.latest.revision: "5"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 2619842bedef2c28e792969dfbd5c724375122bf
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="xml-processing-options"></a>Opcje przetwarzania XML
Zobacz Następująca tabela zawiera listę technologii firmy Microsoft, używanych do przetwarzania danych XML.  
  
## <a name="net-framework-options"></a>.NET framework opcje  
  
|**Opcja**|**Przetwarzania typu**|**Opis**|  
|----------------|-------------------------|---------------------|  
|[LINQ to XML](http://msdn.microsoft.com/library/f0fe21e9-ee43-4a55-b91a-0800e5782c13) <br />(<xref:System.Xml.Linq> przestrzeni nazw)|W pamięci|-Oparte na technologii .NET Framework Language-Integrated zapytania (LINQ).<br />— Zapewnia zapytania podobne do bazy danych SQL dla obiektów, danych relacyjnych i danych XML.<br />— Zapewnia inituive możliwości tworzenia i Przekształcenie dokumentu.<br />— Użyj tej opcji, jeśli piszesz nowy kod.|  
|<xref:System.Xml.XmlReader?displayProperty=nameWithType>|Na podstawie strumienia|— Umożliwia szybkie, niebuforowanym, tylko do przodu do dostępu do danych XML.<br />— Można utworzyć obiektów przy użyciu <xref:System.Xml.XmlReader.Create%2A?displayProperty=nameWithType> metody i określ zestaw funkcji, aby włączyć obiektu przy użyciu <xref:System.Xml.XmlReaderSettings> klasy.|  
|<xref:System.Xml.XmlWriter?displayProperty=nameWithType>|Na podstawie strumienia|— Umożliwia szybkie, niebuforowanym, tylko do przodu do generowania danych XML.<br />— Można utworzyć obiektów przy użyciu <xref:System.Xml.XmlWriter.Create%2A?displayProperty=nameWithType> metody i określ zestaw funkcji, aby włączyć obiektu przy użyciu <xref:System.Xml.XmlWriterSettings> klasy.|  
|<xref:System.Xml.XmlDocument?displayProperty=nameWithType>|W pamięci|-Implementuje [W3C modelu DOM (Document Object) poziom 1 Core](http://www.w3.org/TR/REC-DOM-Level-1/level-one-core.html) i [DOM poziom 2 rdzenie](http://www.w3.org/TR/DOM-Level-2-Core/) zalecenia.<br />— Utwórz, wstawianie, usuwanie i modyfikowanie węzłów przy użyciu metod i właściwości na podstawie znanych modelu DOM.<br />— Użyj tej opcji w przypadku modyfikacji istniejącego kodu korzystającego z modelu DOM. W3C|  
|<xref:System.Xml.XPath.XPathNavigator?displayProperty=nameWithType>|W pamięci|— Zapewnia kilka opcji edycji i możliwości nawigacji przy użyciu modelu kursora.<br />— Dokumenty XML mogą być zawarte w <xref:System.Xml.XPath.XPathDocument> lub <xref:System.Xml.XmlDocument> obiektu.<br />— Zapewnia doskonałą wydajność dla przetwarzania XML tylko do odczytu.<br />— Użyj tej opcji w przypadku modyfikacji istniejącego kodu z kwerendy XPath lub przekształcenia XSLT.|  
|<xref:System.Xml.Xsl.XslCompiledTransform>|W pamięci|— Zapewnia opcje do transformacji danych XML przy użyciu transformacji XSL.<br />- [Kompilatora XSLT (xsltc.exe)](../../../../docs/standard/data/xml/xslt-compiler-xsltc-exe.md) umożliwia możesz odwoływać się do wstępnie skompilowany przekształcenia w aplikacji.|  
  
## <a name="win32-and-com-based-options"></a>Opcje oparte na modelu COM i Win32  
  
|**Opcja**|**Opis**|  
|----------------|---------------------|  
|[XmlLite](http://go.microsoft.com/fwlink/?LinkId=93723)|Szybkie, bezpieczne, bez buforowania, tylko do przodu analizatora składni XML ułatwiające tworzenie wysokiej wydajności XML aplikacji.<br />-Współpracuje z dowolnego języka, który może używać biblioteki dołączanej dynamicznie (dll); Firma Microsoft zaleca używanie języka C++.|  
|[PROGRAM MSXML](http://go.microsoft.com/fwlink/?LinkId=93722)|COM opartych na technologii przetwarzania kodu XML, który jest dołączony do systemu operacyjnego Windows.<br />— Zapewnia implementacji native modelu DOM obsługę XPath i XSLT.<br />-Zawiera SAX2 analizatora opartego na zdarzeniach.|  
  
## <a name="see-also"></a>Zobacz też  
 [Przetwarzanie danych XML przy użyciu modelu DOM](../../../../docs/standard/data/xml/process-xml-data-using-the-dom-model.md)  
 [Przetwarzanie danych XML przy użyciu modelu danych XPath](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)  
 [Kompilator XSLT (xsltc.exe)](../../../../docs/standard/data/xml/xslt-compiler-xsltc-exe.md)
