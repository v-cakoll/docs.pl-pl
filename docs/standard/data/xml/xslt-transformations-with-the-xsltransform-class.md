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
ms.openlocfilehash: ee35ce1016d9e0a825254fad4b08d4b94da16943
ms.sourcegitcommit: a8d3504f0eae1a40bda2b06bd441ba01f1631ef0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/18/2019
ms.locfileid: "67170953"
---
# <a name="xslt-transformations-with-the-xsltransform-class"></a>Przekształcenia XSLT przy użyciu klasy XslTransform

> [!NOTE]
> <xref:System.Xml.Xsl.XslTransform> Klasa jest przestarzała w programie .NET Framework 2.0. Można przeprowadzić rozszerzalny język arkusza stylów dla przekształceń przekształcenia (XSLT) przy użyciu <xref:System.Xml.Xsl.XslCompiledTransform> klasy. Zobacz [używanie klasy XslCompiledTransform](using-the-xslcompiledtransform-class.md) i [Migrowanie z klasy XslTransform](migrating-from-the-xsltransform-class.md) Aby uzyskać więcej informacji.

Celem XSLT jest do przekształcania zawartości w dokumencie źródłowym XML do innego dokumentu, która różni się w formacie lub struktury (na przykład Przekształcanie kodu XML w kodzie HTML do użycia w witrynie sieci Web lub Przekształcanie dokumentu, który zawiera tylko b wymagane pola y aplikacji). Ten proces przekształcania określono przez konsorcjum World Wide Web (W3C)[XSLT w wersji 1.0 zalecenie](https://www.w3.org/TR/1999/REC-xslt-19991116). W .NET Framework <xref:System.Xml.Xsl.XslTransform> znaleziono w klasy <xref:System.Xml.Xsl> przestrzeni nazw jest procesora XSLT, który implementuje funkcje tej specyfikacji. Istnieje kilka małych funkcji, które nie zostały wdrożone z zaleceniem W3C specyfikacji XSLT 1.0, na liście [dane wyjściowe z klasy XslTransform](outputs-from-an-xsltransform.md). Na poniższej ilustracji przedstawiono architekturę przekształcania programu .NET Framework.

## <a name="overview"></a>Omówienie

![Diagram przedstawiający architekturę transformację XSLT.](./media/xslt-transformations-with-the-xsltransform-class/xslt-transformation-architecture.gif) 

Zalecenie XSLT używa XML Path Language (XPath), aby wybrać części dokumentu XML, gdy wyrażenie XPath jest język zapytań, używany do przechodzenia węzłów w drzewie dokumentu. Jak pokazano na diagramie, wdrożenia programu .NET Framework, XPath jest używany do wybierania części XML przechowywane w kilka klas, takie jak <xref:System.Xml.XmlDocument>, <xref:System.Xml.XmlDataDocument>i <xref:System.Xml.XPath.XPathDocument>. <xref:System.Xml.XPath.XPathDocument> Jest magazynem danych zoptymalizowanych XSLT i gdy jest używane z <xref:System.Xml.Xsl.XslTransform>, zapewnia przekształcenia XSLT przy użyciu dobrą wydajność.

Podczas pracy z poniższej listy tabel często używa klas <xref:System.Xml.Xsl.XslTransform> i XPath i ich funkcji.

|Klasy lub interfejsu|Funkcja|
|------------------------|--------------|
|<xref:System.Xml.XPath.XPathNavigator>|To interfejs API, który udostępnia model styl kursor do nawigowania w sklepie, wraz z pomocy technicznej kwerendy XPath. Nie zapewnia edytowanie podstawowego magazynu. W przypadku edytowania, użyj <xref:System.Xml.XmlDocument> klasy.|
|<xref:System.Xml.XPath.IXPathNavigable>|To interfejs, który udostępnia `CreateNavigator` metody <xref:System.Xml.XPath.XPathNavigator> dla magazynu.|
|<xref:System.Xml.XmlDocument>|Umożliwia edytowanie tego dokumentu. Implementuje <xref:System.Xml.XPath.IXPathNavigable>, dzięki czemu scenariuszy edytowanie dokumentów, których następnie wymagane są przekształcenia XSLT. Aby uzyskać więcej informacji, zobacz [dane wejściowe obiektu XmlDocument klasy xsltransform](xmldocument-input-to-xsltransform.md).|
|<xref:System.Xml.XmlDataDocument>|Jest pochodną <xref:System.Xml.XmlDocument>. Tworzy ono relacyjnej i cech XML przy użyciu <xref:System.Data.DataSet> do optymalizacji magazynowania ustrukturyzowanych danych w dokumencie XML, zgodnie z określonym mapowania na <xref:System.Data.DataSet>. Implementuje <xref:System.Xml.XPath.IXPathNavigable>, dzięki czemu scenariuszy, w którym przekształcenia XSLT mogą być wykonywane na danych relacyjnych, pobierane z bazy danych. Aby uzyskać więcej informacji, zobacz [Integracja XML z danymi relacyjnymi i ADO.NET](xml-integration-with-relational-data-and-adonet.md).|
|<xref:System.Xml.XPath.XPathDocument>|Ta klasa jest zoptymalizowana pod kątem <xref:System.Xml.Xsl.XslTransform> przetwarzania i zapytań XPath i oferuje pamięć podręczną tylko do odczytu o wysokiej wydajności. Implementuje <xref:System.Xml.XPath.IXPathNavigable> i jest to preferowany magazyn na potrzeby przekształceń XSLT.|
|<xref:System.Xml.XPath.XPathNodeIterator>|Zapewnia on nawigacji przez zestawy węzła XPath. Wszystkie metody wyboru XPath w <xref:System.Xml.XPath.XPathNavigator> zwracają <xref:System.Xml.XPath.XPathNodeIterator>. Wiele <xref:System.Xml.XPath.XPathNodeIterator> obiekty mogą być tworzone za pośrednictwem tego samego magazynu, reprezentujący wybrany zestaw węzłów.|

## <a name="msxml-xslt-extensions"></a>Rozszerzenia programu MSXML XSLT

`msxsl:script` i `msxsl:node-set` funkcje są tylko rozszerzenia XSLT Microsoft XML Core Services (MSXML), obsługiwane przez <xref:System.Xml.Xsl.XslTransform> klasy.

## <a name="example"></a>Przykład

Poniższy przykład kodu ładuje arkusz stylów XSLT odczytuje plik o nazwie mojedane.XML do <xref:System.Xml.XPath.XPathDocument>i wykonuje przekształcenie danych na fikcyjnej plik o nazwie myStyleSheet.xsl, wysyłając sformatowane dane wyjściowe do konsoli.

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
        XPathDocument xpathdocument = new XPathDocument(filename);
        XmlTextWriter writer = new XmlTextWriter(Console.Out);
        writer.Formatting = Formatting.Indented;

        xslt.Transform(xpathdocument, null, writer, null);
    }
}
```

## <a name="see-also"></a>Zobacz także

- <xref:System.Xml.Xsl.XslTransform>
- [Implementowanie procesora XSLT przy użyciu klasy XslTransform](xsltransform-class-implements-the-xslt-processor.md)
- [Implementowanie zachowań uznaniowych w klasie XslTransform](implementation-of-discretionary-behaviors-in-the-xsltransform-class.md)
- [Klasa XPathNavigator w przekształceniach](xpathnavigator-in-transformations.md)
- [Klasa XPathNodeIterator w przekształceniach](xpathnodeiterator-in-transformations.md)
- [Dane wejściowe obiektu XPathDocument klasy XslTransform](xpathdocument-input-to-xsltransform.md)
- [Dane wejściowe obiektu XmlDataDocument klasy XslTransform](xmldatadocument-input-to-xsltransform.md)
- [Dane wejściowe obiektu XmlDocument klasy XslTransform](xmldocument-input-to-xsltransform.md)
