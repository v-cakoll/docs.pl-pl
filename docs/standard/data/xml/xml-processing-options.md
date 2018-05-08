---
title: Opcje przetwarzania XML
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 33ced8ee-1745-4e71-8dee-ebe70ec067c7
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1b1295185bf0fa06884b1332762d01f86f138a0b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="xml-processing-options"></a>Opcje przetwarzania XML
Zobacz Następująca tabela zawiera listę technologii firmy Microsoft, używanych do przetwarzania danych XML.  
  
## <a name="net-framework-options"></a>.NET framework opcje  
  
|**Opcja**|**Przetwarzania typu**|**Opis**|  
|----------------|-------------------------|---------------------|  
|[LINQ to XML](https://msdn.microsoft.com/library/f0fe21e9-ee43-4a55-b91a-0800e5782c13) <br />(<xref:System.Xml.Linq> przestrzeni nazw)|W pamięci|-Oparte na technologii .NET Framework Language-Integrated zapytania (LINQ).<br />— Zapewnia zapytania podobne do bazy danych SQL dla obiektów, danych relacyjnych i danych XML.<br />— Zapewnia inituive możliwości tworzenia i Przekształcenie dokumentu.<br />— Użyj tej opcji, jeśli piszesz nowy kod.|  
|<xref:System.Xml.XmlReader?displayProperty=nameWithType>|Na podstawie strumienia|— Umożliwia szybkie, niebuforowanym, tylko do przodu do dostępu do danych XML.<br />— Można utworzyć obiektów przy użyciu <xref:System.Xml.XmlReader.Create%2A?displayProperty=nameWithType> metody i określ zestaw funkcji, aby włączyć obiektu przy użyciu <xref:System.Xml.XmlReaderSettings> klasy.|  
|<xref:System.Xml.XmlWriter?displayProperty=nameWithType>|Na podstawie strumienia|— Umożliwia szybkie, niebuforowanym, tylko do przodu do generowania danych XML.<br />— Można utworzyć obiektów przy użyciu <xref:System.Xml.XmlWriter.Create%2A?displayProperty=nameWithType> metody i określ zestaw funkcji, aby włączyć obiektu przy użyciu <xref:System.Xml.XmlWriterSettings> klasy.|  
|<xref:System.Xml.XmlDocument?displayProperty=nameWithType>|W pamięci|-Implementuje [W3C modelu DOM (Document Object) poziom 1 Core](https://www.w3.org/TR/REC-DOM-Level-1/level-one-core.html) i [DOM poziom 2 rdzenie](https://www.w3.org/TR/DOM-Level-2-Core/) zalecenia.<br />— Utwórz, wstawianie, usuwanie i modyfikowanie węzłów przy użyciu metod i właściwości na podstawie znanych modelu DOM.<br />— Użyj tej opcji w przypadku modyfikacji istniejącego kodu korzystającego z modelu DOM. W3C|  
|<xref:System.Xml.XPath.XPathNavigator?displayProperty=nameWithType>|W pamięci|— Zapewnia kilka opcji edycji i możliwości nawigacji przy użyciu modelu kursora.<br />— Dokumenty XML mogą być zawarte w <xref:System.Xml.XPath.XPathDocument> lub <xref:System.Xml.XmlDocument> obiektu.<br />— Zapewnia doskonałą wydajność dla przetwarzania XML tylko do odczytu.<br />— Użyj tej opcji w przypadku modyfikacji istniejącego kodu z kwerendy XPath lub przekształcenia XSLT.|  
|<xref:System.Xml.Xsl.XslCompiledTransform>|W pamięci|— Zapewnia opcje do transformacji danych XML przy użyciu transformacji XSL.<br />- [Kompilatora XSLT (xsltc.exe)](../../../../docs/standard/data/xml/xslt-compiler-xsltc-exe.md) umożliwia możesz odwoływać się do wstępnie skompilowany przekształcenia w aplikacji.|  
  
## <a name="win32-and-com-based-options"></a>Opcje oparte na modelu COM i Win32  
  
|**Opcja**|**Opis**|  
|----------------|---------------------|  
|[XmlLite](https://msdn.microsoft.com/library/ms752872.aspx)|Szybkie, bezpieczne, bez buforowania, tylko do przodu analizatora składni XML ułatwiające tworzenie wysokiej wydajności XML aplikacji.<br />-Współpracuje z dowolnego języka, który może używać biblioteki dołączanej dynamicznie (dll); Firma Microsoft zaleca używanie języka C++.|  
|[PROGRAM MSXML](https://msdn.microsoft.com/library/ms763742.aspx)|COM opartych na technologii przetwarzania kodu XML, który jest dołączony do systemu operacyjnego Windows.<br />— Zapewnia implementacji native modelu DOM obsługę XPath i XSLT.<br />-Zawiera SAX2 analizatora opartego na zdarzeniach.|  
  
## <a name="see-also"></a>Zobacz też  
 [Przetwarzanie danych XML przy użyciu modelu DOM](../../../../docs/standard/data/xml/process-xml-data-using-the-dom-model.md)  
 [Przetwarzanie danych XML przy użyciu modelu danych XPath](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)  
 [Kompilator XSLT (xsltc.exe)](../../../../docs/standard/data/xml/xslt-compiler-xsltc-exe.md)
