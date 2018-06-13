---
title: Przekształcenia XSLT przy użyciu klasy XslTransform
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 500335af-f9b5-413b-968a-e6d9a824478c
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ece159b35cfbc83e05432b93ce7df06a5ca9fcac
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33576171"
---
# <a name="xslt-transformations-with-the-xsltransform-class"></a>Przekształcenia XSLT przy użyciu klasy XslTransform
> [!NOTE]
>  <xref:System.Xml.Xsl.XslTransform> Klasa jest przestarzała w [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)]. Może wykonywać rozszerzalny język arkusza stylów dla transformacji przekształcenia XSLT () przy użyciu <xref:System.Xml.Xsl.XslCompiledTransform> klasy. Zobacz [za pomocą klasy XslCompiledTransform](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) i [migracji z klasy XslTransform](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md) Aby uzyskać więcej informacji.  
  
 Celem XSLT jest przekształcenie zawartości dokumentu XML źródła do innego dokumentu, która różni się w formacie lub struktury (na przykład: Przekształcanie XML w kodzie HTML do użytku w witrynie sieci Web lub przekształcać je do dokumentu, który zawiera tylko b wymagane pola Aplikacja y). Ten proces transformacji jest określona przez znajdujący się w www.w3.org/TR/xslt zalecenia w wersji 1.0 XSLT sieci World Wide Web konsorcjum W3C. W [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)], <xref:System.Xml.Xsl.XslTransform> znaleziono w klasy <xref:System.Xml.Xsl> przestrzeni nazw jest procesorze XSLT, która implementuje funkcje w tej specyfikacji. Mała liczba funkcji, które nie zostały wdrożone z zalecenia W3C XSLT 1.0, na liście [dane wyjściowe z XslTransform](../../../../docs/standard/data/xml/outputs-from-an-xsltransform.md). Na poniższej ilustracji przedstawiono architekturę przekształcania [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)].  
  
## <a name="overview"></a>Omówienie  
 ![Architektura przekształcenia XSLT](../../../../docs/standard/data/xml/media/xslttransformationswithxsltransformclass.gif "xsltTransformationsWithXslTransformClass")  
Architektura przekształcenia  
  
 Zalecenie XSLT używa XML Path Language (XPath), aby wybrać części dokumentu XML, gdy wyrażenie XPath jest język kwerendy służące do nawigacji węzłów w drzewie dokumentu. Jak pokazano na diagramie [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] implementacji XPath jest używana do wybierania części XML przechowywane w kilka klas, takich jak <xref:System.Xml.XmlDocument>, <xref:System.Xml.XmlDataDocument>i <xref:System.Xml.XPath.XPathDocument>. <xref:System.Xml.XPath.XPathDocument> Jest zoptymalizowany XSLT magazynu danych, a w przypadku użycia z <xref:System.Xml.Xsl.XslTransform>, zapewnia przekształceń XSLT z dobrą wydajność.  
  
 Podczas pracy z poniższej listy tabeli często używa klas <xref:System.Xml.Xsl.XslTransform> i XPath i ich funkcji.  
  
|Klasy lub interfejsu|Funkcja|  
|------------------------|--------------|  
|<xref:System.Xml.XPath.XPathNavigator>|To interfejs API, który udostępnia model styl kursora nawigacji w sklepie, wraz z możliwością kwerendy XPath. Nie zapewnia edytowanie odpowiedni magazyn. Do edycji, użyj <xref:System.Xml.XmlDocument> klasy.|  
|<xref:System.Xml.XPath.IXPathNavigable>|Jest to interfejs zapewniający `CreateNavigator` metody <xref:System.Xml.XPath.XPathNavigator> magazynu.|  
|<xref:System.Xml.XmlDocument>|Umożliwia edytowanie tego dokumentu. Implementuje <xref:System.Xml.XPath.IXPathNavigable>, umożliwiając scenariusze edycji dokumentu, gdzie są następnie wymagane przekształcenia XSLT. Aby uzyskać więcej informacji, zobacz [dane wejściowe XmlDocument XslTransform](../../../../docs/standard/data/xml/xmldocument-input-to-xsltransform.md).|  
|<xref:System.Xml.XmlDataDocument>|Jest pochodną <xref:System.Xml.XmlDocument>. Tworzy ono relacyjnych i względem XML przy użyciu <xref:System.Data.DataSet> w celu zoptymalizowania magazynu danych strukturalnych w dokumencie XML zgodnie z określonym mapowania na <xref:System.Data.DataSet>. Implementuje <xref:System.Xml.XPath.IXPathNavigable>, dzięki czemu scenariuszy, w którym przekształcenia XSLT mogą być wykonywane za pośrednictwem relacyjne dane pobrane z bazy danych. Aby uzyskać więcej informacji, zobacz [XML integracji z danych relacyjnych i ADO.NET](../../../../docs/standard/data/xml/xml-integration-with-relational-data-and-adonet.md).|  
|<xref:System.Xml.XPath.XPathDocument>|Ta klasa jest zoptymalizowana pod kątem <xref:System.Xml.Xsl.XslTransform> przetwarzania i kwerendy XPath i udostępnia pamięć podręczną tylko do odczytu o wysokiej wydajności. Implementuje <xref:System.Xml.XPath.IXPathNavigable> i preferowany magazynu do użycia na potrzeby przekształcenia XSLT.|  
|<xref:System.Xml.XPath.XPathNodeIterator>|Zapewnia on nawigacji przez zestaw węzłów XPath. Wszystkie metody wyboru XPath na <xref:System.Xml.XPath.XPathNavigator> zwracać <xref:System.Xml.XPath.XPathNodeIterator>. Wiele <xref:System.Xml.XPath.XPathNodeIterator> obiekty mogą być tworzone w tym samym magazynie reprezentujący wybranego zestawu węzłów.|  
  
## <a name="msxml-xslt-extensions"></a>Rozszerzenia programu MSXML XSLT  
 `msxsl:script` i `msxsl:node-set` funkcje są tylko rozszerzenia XSLT Microsoft XML Core Services (MSXML) obsługiwany przez <xref:System.Xml.Xsl.XslTransform> klasy.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu ładuje arkusz stylów XSLT odczytuje plik o nazwie mojedane.XML do <xref:System.Xml.XPath.XPathDocument>i wykonuje transformację danych w fikcyjnej plik o nazwie myStyleSheet.xsl wysyłania sformatowane dane wyjściowe do konsoli.  
  
```vb  
Imports System  
Imports System.IO  
Imports System.Xml  
Imports System.Xml.XPath  
Imports System.Xml.Xsl  
  
Public Class Sample  
    Private filename As [String] = "mydata.xml"  
    Private stylesheet As [String] = "myStyleSheet.xsl"  
  
    Public Shared Sub Main()  
        Dim xslt As New XslTransform()  
        xslt.Load(stylesheet)  
        Dim xpathdocument As New XPathDocument(filename)  
        Dim writer As New XmlTextWriter(Console.Out)  
        writer.Formatting = Formatting.Indented  
  
        xslt.Transform(xpathdocument, Nothing, writer, Nothing)  
    End Sub 'Main  
End Class 'Sample  
```  
  
```csharp  
using System;  
using System.IO;  
using System.Xml;  
using System.Xml.XPath;  
using System.Xml.Xsl;  
  
public class Sample   
{  
    private const String filename = "mydata.xml";  
    private const String stylesheet = "myStyleSheet.xsl";  
  
    public static void Main()   
    {  
    XslTransform xslt = new XslTransform();  
    xslt.Load(stylesheet);  
    XPathDocument xpathdocument = new  
    XPathDocument(filename);  
    XmlTextWriter writer = new XmlTextWriter(Console.Out);  
    writer.Formatting=Formatting.Indented;  
  
    xslt.Transform(xpathdocument, null, writer, null);      
    }  
}  
```  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Xml.Xsl.XslTransform>  
 [Implementowanie procesora XSLT przy użyciu klasy XslTransform](../../../../docs/standard/data/xml/xsltransform-class-implements-the-xslt-processor.md)  
 [Implementowanie zachowań uznaniowych w klasie XslTransform](../../../../docs/standard/data/xml/implementation-of-discretionary-behaviors-in-the-xsltransform-class.md)  
 [Klasa XPathNavigator w przekształceniach](../../../../docs/standard/data/xml/xpathnavigator-in-transformations.md)  
 [Klasa XPathNodeIterator w przekształceniach](../../../../docs/standard/data/xml/xpathnodeiterator-in-transformations.md)  
 [Dane wejściowe obiektu XPathDocument klasy XslTransform](../../../../docs/standard/data/xml/xpathdocument-input-to-xsltransform.md)  
 [Dane wejściowe obiektu XmlDataDocument klasy XslTransform](../../../../docs/standard/data/xml/xmldatadocument-input-to-xsltransform.md)  
 [Dane wejściowe obiektu XmlDocument klasy XslTransform](../../../../docs/standard/data/xml/xmldocument-input-to-xsltransform.md)
