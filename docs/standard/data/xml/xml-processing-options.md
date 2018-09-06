---
title: Opcje przetwarzania XML
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 33ced8ee-1745-4e71-8dee-ebe70ec067c7
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 4e0d0a2a8d8c7fd75da7f2109619d588eac7b4a6
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2018
ms.locfileid: "43863023"
---
# <a name="xml-processing-options"></a>Opcje przetwarzania XML
Zobacz następujące tabele, aby uzyskać listę technologie firmy Microsoft, które służy do przetwarzania danych XML.  
  
## <a name="net-framework-options"></a>Opcje struktury platformy .NET  
  
|**Option**|**Typ przetwarzania**|**Opis**|  
|----------------|-------------------------|---------------------|  
|[LINQ to XML](https://msdn.microsoft.com/library/f0fe21e9-ee43-4a55-b91a-0800e5782c13) <br />(<xref:System.Xml.Linq> przestrzeni nazw)|W pamięci|-Oparte na technologii .NET Framework Language-Integrated Query (LINQ).<br />— Zapewnia zapytania podobne do bazy danych SQL dla obiektów, opartego na danych relacyjnych i danych XML.<br />— Zapewnia możliwości tworzenia i transformacji intuicyjne dokumentu.<br />— Użyj tej opcji, jeśli piszesz nowy kod.|  
|<xref:System.Xml.XmlReader?displayProperty=nameWithType>|Na podstawie Stream|— Zapewnia szybkie niebuforowanym, tylko do przodu sposób dostępu do danych XML.<br />— Możesz tworzyć obiekty używając <xref:System.Xml.XmlReader.Create%2A?displayProperty=nameWithType> metodę i określić zestaw funkcji, aby włączyć obiekt za pomocą <xref:System.Xml.XmlReaderSettings> klasy.|  
|<xref:System.Xml.XmlWriter?displayProperty=nameWithType>|Na podstawie Stream|— Umożliwia szybkie niebuforowanym, tylko do przodu do generowania danych XML.<br />— Możesz tworzyć obiekty używając <xref:System.Xml.XmlWriter.Create%2A?displayProperty=nameWithType> metodę i określić zestaw funkcji, aby włączyć obiekt za pomocą <xref:System.Xml.XmlWriterSettings> klasy.|  
|<xref:System.Xml.XmlDocument?displayProperty=nameWithType>|W pamięci|-Implementuje [W3C Document Object Model (DOM) poziom 1 Core](https://www.w3.org/TR/REC-DOM-Level-1/level-one-core.html) i [Core 2 na poziomie modelu DOM](https://www.w3.org/TR/DOM-Level-2-Core/) zalecenia.<br />— Tworzenie, wstawianie, usuwanie i modyfikowanie węzłów przy użyciu metod i właściwości, w oparciu o znanego modelu DOM.<br />— Użyj tej opcji w przypadku modyfikacji istniejącego kodu, który korzysta z modelu DOM. W3C|  
|<xref:System.Xml.XPath.XPathNavigator?displayProperty=nameWithType>|W pamięci|-Oferuje kilka opcji edycji i możliwości nawigacji przy użyciu modelu kursora.<br />— Dokumenty XML mogą być zawarte w <xref:System.Xml.XPath.XPathDocument> lub <xref:System.Xml.XmlDocument> obiektu.<br />— Zapewnia doskonałą wydajność dla przetwarzania XML tylko do odczytu.<br />— Użyj tej opcji, w przypadku modyfikacji istniejącego kodu za pomocą kwerendy XPath lub przekształcenia XSLT.|  
|<xref:System.Xml.Xsl.XslCompiledTransform>|W pamięci|-Dostarcza opcje do przekształcania danych XML przy użyciu transformacji XSL.<br />[Kompilator XSLT (xsltc.exe)](../../../../docs/standard/data/xml/xslt-compiler-xsltc-exe.md) umożliwia odwołanie wstępnie skompilowany przekształcenia w swojej aplikacji.|  
  
## <a name="win32-and-com-based-options"></a>Win32 i opcje oparte na modelu COM  
  
|**Option**|**Opis**|  
|----------------|---------------------|  
|[XmlLite](https://msdn.microsoft.com/library/ms752872.aspx)|Szybkie i bezpieczne, bez buforowania, tylko do przodu analizatora XML, który pomoże Ci tworzenie wysokiej wydajności XML aplikacji.<br />— Działa z dowolnym językiem, który można użyć biblioteki dołączanej dynamicznie (dll); Zaleca się przy użyciu języka C++.|  
|[MSXML](https://msdn.microsoft.com/library/ms763742.aspx)|COM opartych na technologii przetwarzania XML, który jest dołączony do systemu operacyjnego Windows.<br />— Zapewnia natywnych implementacji modelu DOM o obsługę języka XPath i XSLT.<br />-Zawiera SAX2 analizatora opartego na zdarzeniach.|  
  
## <a name="see-also"></a>Zobacz także

- [Przetwarzanie danych XML przy użyciu modelu DOM](../../../../docs/standard/data/xml/process-xml-data-using-the-dom-model.md)  
- [Przetwarzanie danych XML przy użyciu modelu danych XPath](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)  
- [Kompilator XSLT (xsltc.exe)](../../../../docs/standard/data/xml/xslt-compiler-xsltc-exe.md)
