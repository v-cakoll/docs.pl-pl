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
ms.openlocfilehash: d534553fcc6ee63d560e731a535d44c3acd1a214
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74347898"
---
# <a name="xslt-transformations-with-the-xsltransform-class"></a>Przekształcenia XSLT przy użyciu klasy XslTransform

> [!NOTE]
> Klasa <xref:System.Xml.Xsl.XslTransform> jest przestarzała w .NET Framework 2,0. Można wykonywać przekształcenia Extensible Stylesheet Language for Transformations (XSLT) przy użyciu klasy <xref:System.Xml.Xsl.XslCompiledTransform>. Aby uzyskać więcej informacji, zobacz [Używanie klasy XslCompiledTransform](using-the-xslcompiledtransform-class.md) i [Migrowanie z klasy XslTransform](migrating-from-the-xsltransform-class.md) .

Celem XSLT jest przekształcenie zawartości źródłowego dokumentu XML do innego dokumentu, który jest inny w formacie lub strukturze (na przykład w celu przekształcenia XML w HTML do użycia w witrynie sieci Web lub przekształcenia go w dokument zawierający tylko pola wymagane b). t aplikacji). Ten proces transformacji jest określany przez organizacja World Wide Web Consortium (W3C) w[wersji 1,0 zalecenia](https://www.w3.org/TR/1999/REC-xslt-19991116). W .NET Framework Klasa <xref:System.Xml.Xsl.XslTransform>, która znajduje się w przestrzeni nazw <xref:System.Xml.Xsl>, to procesor XSLT, który implementuje funkcje tej specyfikacji. Istnieje niewielka liczba funkcji, które nie zostały zaimplementowane z rekomendacji W3C XSLT 1,0, wymienione w danych [wyjściowych z XslTransform](outputs-from-an-xsltransform.md). Na poniższej ilustracji przedstawiono architekturę transformacji .NET Framework.

## <a name="overview"></a>Przegląd

![Diagram przedstawiający architekturę transformacji XSLT.](./media/xslt-transformations-with-the-xsltransform-class/xslt-transformation-architecture.gif) 

Zalecenie XSLT używa języka ścieżki XML (XPath) do wybierania części dokumentu XML, gdzie XPath jest językiem zapytań używanym do nawigowania po węzłach drzewa dokumentu. Jak pokazano na diagramie, .NET Framework implementacja XPath służy do wybierania części XML przechowywanych w kilku klasach, takich jak <xref:System.Xml.XmlDocument>, <xref:System.Xml.XmlDataDocument>i <xref:System.Xml.XPath.XPathDocument>. <xref:System.Xml.XPath.XPathDocument> jest zoptymalizowanym magazynem danych XSLT i w przypadku korzystania z <xref:System.Xml.Xsl.XslTransform>, zapewnia przekształcenia XSLT z dobrą wydajnością.

W poniższej tabeli wymieniono typowe zastosowania klas podczas pracy z <xref:System.Xml.Xsl.XslTransform> i XPath oraz ich funkcją.

|Klasa lub interfejs|Funkcja|
|------------------------|--------------|
|<xref:System.Xml.XPath.XPathNavigator>|Jest to interfejs API, który udostępnia model stylu kursora na potrzeby nawigowania po sklepie oraz obsługę zapytań XPath. Nie zapewnia on edycji bazowego magazynu. Aby edytować, użyj klasy <xref:System.Xml.XmlDocument>.|
|<xref:System.Xml.XPath.IXPathNavigable>|Jest to interfejs, który udostępnia metodę `CreateNavigator` do <xref:System.Xml.XPath.XPathNavigator> magazynu.|
|<xref:System.Xml.XmlDocument>|Umożliwia edytowanie tego dokumentu. Implementuje <xref:System.Xml.XPath.IXPathNavigable>, co umożliwia scenariusze edycji dokumentów, w których przekształcenia XSLT są wymagane. Aby uzyskać więcej informacji, zobacz [XmlDocument input to XslTransform](xmldocument-input-to-xsltransform.md).|
|<xref:System.Xml.XmlDataDocument>|Pochodzi ona od <xref:System.Xml.XmlDocument>. Mostkuje środowiska relacyjne i XML przy użyciu <xref:System.Data.DataSet> do optymalizowania magazynu danych strukturalnych w dokumencie XML zgodnie z określonymi mapowaniami w <xref:System.Data.DataSet>. Implementuje <xref:System.Xml.XPath.IXPathNavigable>, umożliwiając scenariusze, w których można wykonywać przekształcenia XSLT w danych relacyjnych pobieranych z bazy danych. Aby uzyskać więcej informacji, zobacz temat [Integracja XML z danymi relacyjnymi i ADO.NET](xml-integration-with-relational-data-and-adonet.md).|
|<xref:System.Xml.XPath.XPathDocument>|Ta klasa jest zoptymalizowana pod kątem <xref:System.Xml.Xsl.XslTransform> przetwarzania i zapytań XPath i udostępnia pamięć podręczną o wysokiej wydajności tylko do odczytu. Implementuje <xref:System.Xml.XPath.IXPathNavigable> i jest preferowanym magazynem do użycia na potrzeby transformacji XSLT.|
|<xref:System.Xml.XPath.XPathNodeIterator>|Zapewnia nawigację nad zestawami węzłów XPath. Wszystkie metody wyboru XPath na <xref:System.Xml.XPath.XPathNavigator> zwracają <xref:System.Xml.XPath.XPathNodeIterator>. Wiele obiektów <xref:System.Xml.XPath.XPathNodeIterator> można utworzyć w tym samym magazynie, z których każdy reprezentuje wybrany zestaw węzłów.|

## <a name="msxml-xslt-extensions"></a>Rozszerzenia XSLT języka MSXML

`msxsl:script` i `msxsl:node-set` funkcje są jedynymi rozszerzeniami XSLT programu Microsoft XML Core Services (MSXML) obsługiwanymi przez klasę <xref:System.Xml.Xsl.XslTransform>.

## <a name="example"></a>Przykład

Poniższy przykład kodu ładuje arkusz stylów XSLT, odczytuje plik o nazwie moje dane. XML do <xref:System.Xml.XPath.XPathDocument>i wykonuje przekształcenie danych w fikcyjnym pliku o nazwie plik. xsl, wysyłając sformatowane dane wyjściowe do konsoli.

```vb
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
