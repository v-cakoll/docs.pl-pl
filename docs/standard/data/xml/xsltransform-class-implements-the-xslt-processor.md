---
title: Implementowanie procesora XSLT przy użyciu klasy XslTransform
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 88373fe2-4a6b-44f9-8a62-8a3e348e3a46
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7c36ff35622ae5c9cddf4ffd1ebd0a60feb348a8
ms.sourcegitcommit: a8d3504f0eae1a40bda2b06bd441ba01f1631ef0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/18/2019
ms.locfileid: "67170893"
---
# <a name="xsltransform-class-implements-the-xslt-processor"></a>Implementowanie procesora XSLT przy użyciu klasy XslTransform

> [!NOTE]
> <xref:System.Xml.Xsl.XslTransform> Klasa jest przestarzała w programie .NET Framework 2.0. Można przeprowadzić rozszerzalny język arkusza stylów dla przekształceń przekształcenia (XSLT) przy użyciu <xref:System.Xml.Xsl.XslCompiledTransform> klasy. Zobacz [używanie klasy XslCompiledTransform](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) i [Migrowanie z klasy XslTransform](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md) Aby uzyskać więcej informacji.

<xref:System.Xml.Xsl.XslTransform> Klasa jest procesora XSLT implementacji przekształcenia XSL (XSLT) w wersji 1.0 zalecenia. <xref:System.Xml.Xsl.XslTransform.Load%2A> Metoda lokalizuje i odczytuje arkusze stylów i <xref:System.Xml.Xsl.XslTransform.Transform%2A> metoda przekształca dokumentu danego źródła. Dowolnego magazynu, który implementuje <xref:System.Xml.XPath.IXPathNavigable> interfejsu może być używany jako dokument źródłowy dla <xref:System.Xml.Xsl.XslTransform>. .NET Framework implementuje obecnie <xref:System.Xml.XPath.IXPathNavigable> interfejsu na <xref:System.Xml.XmlDocument>, <xref:System.Xml.XmlDataDocument>i <xref:System.Xml.XPath.XPathDocument>, więc wszystkie te mogą być używane jako dokument źródła danych wejściowych do przekształcenia.

<xref:System.Xml.Xsl.XslTransform> Obiektu w programie .NET Framework obsługuje tylko specyfikacji XSLT 1.0, zdefiniowana za pomocą następujących przestrzeni nazw:

```xml
<xsl:stylesheet xmlns:xsl="http://www.w3.org/1999/XSL/Transform" version="1.0">
```

Arkusz stylów może być załadowany, za pomocą <xref:System.Xml.Xsl.XslTransform.Load%2A> metody, z jedną z następujących klas:

- Klasy XPathNavigator

- XmlReader

- Ciąg reprezentujący adres URL

Istnieje inny <xref:System.Xml.Xsl.XslTransform.Load%2A> metody dla każdego z powyższych klas danych wejściowych. Niektóre metody przyjmują w połączeniu z jednej z tych klas i <xref:System.Xml.XmlResolver> klasy jako argumenty. <xref:System.Xml.XmlResolver> Lokalizuje zasobów przywoływanych przez `<xsl:import>` lub `<xsl:include>` znalezione w arkuszu stylów. Następujące metody przyjmują ciąg <xref:System.Xml.XmlReader>, lub <xref:System.Xml.XPath.XPathNavigator> jako dane wejściowe.

```vb
Overloads Public Sub Load(String)
```

```csharp
public void Load(string);
```

```vb
Overloads Public Sub Load(String, XmlResolver)
```

```csharp
public void Load(string, XmlResolver);
```

```vb
Overloads Public Sub Load(XmlReader, XmlResolver, Evidence)
```

```csharp
public void Load(XmlReader, XmlResolver, Evidence);
```

```vb
Overloads Public Sub Load(XPathNavigator, XmlResolver, Evidence)
```

```csharp
public void Load(XPathNavigator, XmlResolver, Evidence);
```

Większość <xref:System.Xml.Xsl.XslTransform.Load%2A> metod przedstawionych powyżej take <xref:System.Xml.XmlResolver> jako parametr. <xref:System.Xml.XmlResolver> Jest używana do ładowania arkusza stylów i wszelkie arkusze stylów w elementu xsl: Import i xsl: obejmują elementy.

Większość <xref:System.Xml.Xsl.XslTransform.Load%2A> metody przyjmują również dowody jako parametr. Parametr dowód <xref:System.Security.Policy.Evidence> skojarzonego z arkusza stylów. Poziom zabezpieczeń arkusza stylów wpływa na poziom zabezpieczeń wszystkie kolejne zasoby, które odwołuje się do, takich jak skryptu w nim dowolne `document()` wykorzystuje funkcje i obiekty rozszerzeń używane przez <xref:System.Xml.Xsl.XsltArgumentList>.

Jeśli arkusz stylów jest ładowany za pomocą <xref:System.Xml.Xsl.XslTransform.Load%2A> metodę, która zawiera parametr adresu URL i oznak jest dostarczany, dowód arkusza stylów jest obliczana przez połączenie danego adresu URL z jej witryny i strefy.

Jeśli nie podano żadnych identyfikatora URI lub dowód, dowodów dla arkusza stylów jest w pełni zaufany. Nie załadować arkusze stylów ze źródeł niezaufanych lub dodać obiekty niezaufane rozszerzenia do <xref:System.Xml.Xsl.XsltArgumentList>.

Aby uzyskać więcej informacji na temat poziomów zabezpieczeń i dowody i jak wpływa on na wykonywanie skryptów, zobacz [XSLT skryptów przy użyciu arkusza stylów \<msxsl: script >](../../../../docs/standard/data/xml/xslt-stylesheet-scripting-using-msxsl-script.md). Aby uzyskać informacje na temat poziomów zabezpieczeń i dowody i jak wpływa na obiekty rozszerzeń, zobacz [XsltArgumentList — parametry arkusza stylów i obiekty rozszerzeń](../../../../docs/standard/data/xml/xsltargumentlist-for-style-sheet-parameters-and-extension-objects.md).

Aby uzyskać informacji na temat poziomów zabezpieczeń i dowody i jak wpływa na `document()` funkcji, zobacz [Rozpoznawanie zewnętrznych arkuszy stylów XSLT i dokumenty](../../../../docs/standard/data/xml/resolving-external-xslt-style-sheets-and-documents.md).

Arkusz stylów można podać z liczbą parametrów wejściowych. Arkusz stylów można również wywołać funkcje na obiekty rozszerzeń. Parametry i obiekty rozszerzeń, które są dostarczane do przy użyciu arkusza stylów <xref:System.Xml.Xsl.XsltArgumentList> klasy. Aby uzyskać więcej informacji na temat <xref:System.Xml.Xsl.XsltArgumentList>, zobacz <xref:System.Xml.Xsl.XsltArgumentList>.

## <a name="recommended-secure-use-of-xsltransform-class"></a>Zalecane bezpieczne użycie klasy XslTransform

Uprawnienia zabezpieczeń w arkuszu stylów są zależne od dowody dostarczone. Poniższa tabela zawiera podsumowanie Lokalizacja arkusza stylów i zawiera wyjaśnienie, jakiego rodzaju dowody, aby nadać.

- Arkusz stylów XSLT nie ma zewnętrznych odwołań, lub arkusz stylów pochodzi z bazy kodu, którym ufasz.

  - Podaj dowód z zestawu:

    ```vb
    Dim xslt = New XslTransform() xslt.Load(stylesheet, resolver, Me.GetType().Assembly.Evidence)

    XsltTransform xslt = new XslTransform();  xslt.Load(stylesheet, resolver, this.GetType().Assembly.Evidence);
    ```

- Arkusz stylów XSLT jest dostarczany ze źródła zewnętrznego. Pochodzenie źródła jest znane, i jest możliwe do zweryfikowania identyfikatorem URI.

  - Tworzenie dokumentów, używając identyfikatora URI.

    ```vb
    Dim xslt As New XslTransform() Dim ev As Evidence = XmlSecureResolver.CreateEvidenceForUrl(stylesheetUri) xslt.Load(stylesheet, resolver, evidence)

    XslTransform xslt = new XslTransform(); Evidence ev = XmlSecureResolver.CreateEvidenceForUrl(stylesheetUri); xslt.Load(stylesheet, resolver, evidence);
    ```

- Arkusz stylów XSLT jest dostarczany ze źródła zewnętrznego. Pochodzenie źródła nie jest znany.

  - Ustaw dowód `null`. Bloki skryptu nie są przetwarzane, XSLT `document()` funkcja nie jest obsługiwana i obiekty rozszerzeń uprzywilejowanych są niedozwolone.

    Ponadto można również ustawić `resolver` parametr `null` gwarantuje to, że `xsl:import` i `xsl:include` elementy nie zostały przetworzone.

- Arkusz stylów XSLT jest dostarczany ze źródła zewnętrznego. Pochodzenie źródła nie jest znany, ale wymagają obsługi skryptów.

  - Żądanie dowód od elementu wywołującego.

## <a name="transformation-of-xml-data"></a>Przekształcania danych XML

Po załadowaniu arkusza stylów transformacja rozpoczyna się przez wywołanie jednej z <xref:System.Xml.Xsl.XslTransform.Transform%2A> metod i dostarczenie dokument źródła danych wejściowych. <xref:System.Xml.Xsl.XslTransform.Transform%2A> Metody jest przeciążona, aby zapewnić różne przekształcenia danych wyjściowych. Transformacja może spowodować następujące formaty danych wyjściowych:

- <xref:System.Xml.XmlReader>

- <xref:System.Xml.XmlWriter>

- <xref:System.IO.TextWriter>

- <xref:System.IO.Stream>

- Ciąg adresu URL w pliku

Ten ostatni format ciągu adresu URL, zawiera często używane scenariusza w przekształcaniu dokument wejściowy znajduje się w adresie URL i zapisywania dokumentu do adresu URL danych wyjściowych. To <xref:System.Xml.Xsl.XslTransform.Transform%2A> metody jest to wygodna metoda można załadować dokumentu XML z pliku, wykonywanie transformacji XSLT i zapisać dane wyjściowe do pliku. Zapobiega konieczności utworzyć i załadować dokument źródła danych wejściowych, a następnie zapisać do strumienia pliku. Poniższy przykładowy kod pokazuje zastosowanie <xref:System.Xml.Xsl.XslTransform.Transform%2A> metody przy użyciu adresu URL ciąg jako dane wejściowe i wyjściowe:

```vb
Dim xsltransform As XslTransform = New XslTransform()
xsltransform.Load("favorite.xsl")
xsltransform.Transform("MyDocument.Xml", "TransformResult.xml", Nothing)
```

```csharp
XslTransform xsltransform = new XslTransform();
xsltransform.Load("favorite.xsl");
xsltransform.Transform("MyDocument.xml", "TransformResult.xml", null);
```

## <a name="transforming-a-section-of-an-xml-document"></a>Przekształcanie części dokumentu XML

Przekształcenia mają zastosowanie do dokumentu jako całości. Innymi słowy Jeśli przekażesz w węźle innym niż węzeł główny dokument, to nie uniemożliwia proces przekształcania uzyskiwania dostępu do wszystkich węzłów w dokumencie załadowane. Aby przekształcić wynikowego fragmentu drzewa, musisz utworzyć <xref:System.Xml.XmlDocument> zawierający tylko drzewa wynik fragmentu i przekazać go <xref:System.Xml.XmlDocument> do <xref:System.Xml.Xsl.XslTransform.Transform%2A> metody. Poniższy przykład wykonuje przekształcenie na wynikowego fragmentu drzewa.

```vb
Dim xslt As New XslTransform()
xslt.Load("print_root.xsl")
Dim doc As New XmlDocument()
doc.Load("library.xml")
' Create a new document containing just the result tree fragment.
Dim testNode As XmlNode = doc.DocumentElement.FirstChild
Dim tmpDoc As New XmlDocument()
tmpDoc.LoadXml(testNode.OuterXml)
' Pass the document containing the result tree fragment
' to the Transform method.
Console.WriteLine(("Passing " + tmpDoc.OuterXml + " to print_root.xsl"))
xslt.Transform(tmpDoc, Nothing, Console.Out, Nothing)
```

```csharp
XslTransform xslt = new XslTransform();
xslt.Load("print_root.xsl");
XmlDocument doc = new XmlDocument();
doc.Load("library.xml");
// Create a new document containing just the result tree fragment.
XmlNode testNode = doc.DocumentElement.FirstChild;
XmlDocument tmpDoc = new XmlDocument();
tmpDoc.LoadXml(testNode.OuterXml);
// Pass the document containing the result tree fragment
// to the Transform method.
Console.WriteLine("Passing " + tmpDoc.OuterXml + " to print_root.xsl");
xslt.Transform(tmpDoc, null, Console.Out, null);
```

W przykładzie użyto library.xml i print_root.xsl pliki jako dane wejściowe i dane wyjściowe konsoli następującą zawartość.

```
Passing <book genre="novel" ISBN="1-861001-57-5"><title>Pride And Prejudice</title></book> to print_root.xsl
Root node is book.
```

Library.XML

```xml
<library>
  <book genre='novel' ISBN='1-861001-57-5'>
     <title>Pride And Prejudice</title>
  </book>
  <book genre='novel' ISBN='1-81920-21-2'>
     <title>Hook</title>
  </book>
</library>
```

print_root.xsl

```xml
<stylesheet version="1.0" xmlns="http://www.w3.org/1999/XSL/Transform" >
  <output method="text" />
  <template match="/">
     Root node is  <value-of select="local-name(//*[position() = 1])" />
  </template>
</stylesheet>
```

## <a name="migration-of-xslt-from-net-framework-version-10-to-net-framework-version-11"></a>Migracja XSLT z .NET Framework w wersji 1.0 do .NET Framework w wersji 1.1

W poniższej tabeli przedstawiono metody .NET Framework przestarzałe w wersji 1.0 i nowa wersja .NET Framework 1.1 metody <xref:System.Xml.Xsl.XslTransform.Load%2A> metody. Nowe metody umożliwiają ograniczenie uprawnień arkusza stylów, określając dowodów.

|.NET Framework w wersji 1.0 obciążenia metody przestarzałe|Zastąpienie .NET Framework w wersji 1.1 obciążenia metody|
|------------------------------------------------------|---------------------------------------------------------|
|Załaduj (dane wejściowe klasy XPathNavigator);<br /><br /> Obciążenia (klasy XPathNavigator danych wejściowych, element XmlResolver rozpoznawania nazw);|Obciążenia (klasy XPathNavigator arkusza stylów, element XmlResolver programu rozpoznawania nazw, dowód dowód);|
|Załaduj (arkusza stylów IXPathNavigable);<br /><br /> Obciążenia (IXPathNavigable arkusza stylów, rozpoznawania element XmlResolver);|Obciążenia (IXPathNavigable arkusza stylów, element XmlResolver programu rozpoznawania nazw, dowód dowód);|
|Załaduj (arkusza stylów XmlReader);<br /><br /> Obciążenia (element XmlReader arkusza stylów, rozpoznawania element XmlResolver);|Obciążenia (element XmlReader arkusza stylów, element XmlResolver programu rozpoznawania nazw, dowód dowód);|

W poniższej tabeli przedstawiono metody przestarzałe i nowe <xref:System.Xml.Xsl.XslTransform.Transform%2A> metody. Nowe metody przyjmują <xref:System.Xml.XmlResolver> obiektu.

|.NET Framework w wersji 1.0 Przekształcanie metody przestarzałe|Wersja programu .NET Framework zastąpienie Przekształcanie metody 1.1|
|-----------------------------------------------------------|--------------------------------------------------------------|
|Element XmlReader Transform(XPathNavigator input, XsltArgumentList args)|Element XmlReader Transform(XPathNavigator input, XsltArgumentList args, XmlResolver resolver)|
|Element XmlReader Transform(IXPathNavigable input, XsltArgumentList args)|Element XmlReader Transform(IXPathNavigable input, XsltArgumentList args, XmlResolver resolver)|
|Void Przekształcanie (dane wejściowe klasy XPathNavigator, argumenty XsltArgumentList, dane wyjściowe XmlWriter)|Void Przekształcanie (dane wejściowe klasy XPathNavigator XsltArgumentList argumenty, dane wyjściowe XmlWriter, element XmlResolver programu rozpoznawania nazw)|
|Void Przekształcanie (dane wejściowe IXPathNavigable, argumenty XsltArgumentList, XmlWriter dane wyjściowe)|Void Przekształcanie (dane wejściowe IXpathNavigable XsltArgumentList argumenty, XmlWriter dane wyjściowe, element XmlResolver programu rozpoznawania nazw)|
|Void Przekształcanie (dane wejściowe klasy XPathNavigator, argumenty XsltArgumentList, dane wyjściowe TextWriter)|Void Przekształcanie (dane wejściowe klasy XPathNavigator XsltArgumentList argumenty, dane wyjściowe TextWriter, element XmlResolver programu rozpoznawania nazw)|
|Void Przekształcanie (IXPathNavigable danych wejściowych, argumenty XsltArgumentList, dane wyjściowe TextWriter)|Void Przekształcanie (IXPathNavigable danych wejściowych, argumenty XsltArgumentList, dane wyjściowe TextWriter, element XmlResolver programu rozpoznawania nazw)|
|Void Przekształcanie (dane wejściowe klasy XPathNavigator, argumenty XsltArgumentList, dane wyjściowe Stream)|Void Przekształcanie (dane wejściowe klasy XPathNavigator XsltArgumentList argumenty, dane wyjściowe Stream, element XmlResolver programu rozpoznawania nazw)|
|Void Przekształcanie (IXPathNavigable danych wejściowych, argumenty XsltArgumentList, dane wyjściowe Stream)|Void Przekształcanie (dane wejściowe IXPathNavigable XsltArgumentList argumenty, Stream dane wyjściowe, element XmlResolver programu rozpoznawania nazw)|
|Void Przekształcanie (ciąg wejściowy, ciąg dane wyjściowe);|Void Przekształcanie (ciąg wejściowy, ciąg danych wyjściowych element XmlResolver programu rozpoznawania nazw);|

<xref:System.Xml.Xsl.XslTransform.XmlResolver%2A?displayProperty=nameWithType> Właściwość jest przestarzała w programie .NET Framework w wersji 1.1. Zamiast tego należy użyć nowego <xref:System.Xml.Xsl.XslTransform.Transform%2A> przeciążeń przybierają które <xref:System.Xml.XmlResolver> obiektu.

## <a name="see-also"></a>Zobacz także

- <xref:System.Xml.Xsl.XslTransform>
- [Przekształcenia XSLT przy użyciu klasy XslTransform](../../../../docs/standard/data/xml/xslt-transformations-with-the-xsltransform-class.md)
- [Klasa XPathNavigator w przekształceniach](../../../../docs/standard/data/xml/xpathnavigator-in-transformations.md)
- [Klasa XPathNodeIterator w przekształceniach](../../../../docs/standard/data/xml/xpathnodeiterator-in-transformations.md)
- [Dane wejściowe obiektu XPathDocument klasy XslTransform](../../../../docs/standard/data/xml/xpathdocument-input-to-xsltransform.md)
- [Dane wejściowe obiektu XmlDataDocument klasy XslTransform](../../../../docs/standard/data/xml/xmldatadocument-input-to-xsltransform.md)
- [Dane wejściowe obiektu XmlDocument klasy XslTransform](../../../../docs/standard/data/xml/xmldocument-input-to-xsltransform.md)
