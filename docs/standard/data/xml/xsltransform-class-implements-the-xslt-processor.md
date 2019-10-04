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
ms.openlocfilehash: 8cc3eb3e3f147d8ed15587946af743c96739a9b1
ms.sourcegitcommit: 7bfe1682d9368cf88d43e895d1e80ba2d88c3a99
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/04/2019
ms.locfileid: "71956863"
---
# <a name="xsltransform-class-implements-the-xslt-processor"></a>Implementowanie procesora XSLT przy użyciu klasy XslTransform

> [!NOTE]
> Klasa <xref:System.Xml.Xsl.XslTransform> jest przestarzała w .NET Framework 2,0. Można wykonywać przekształcenia Extensible Stylesheet Language for Transformations (XSLT) przy użyciu klasy <xref:System.Xml.Xsl.XslCompiledTransform>. Aby uzyskać więcej informacji, zobacz [Używanie klasy XslCompiledTransform](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) i [Migrowanie z klasy XslTransform](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md) .

Klasa <xref:System.Xml.Xsl.XslTransform> to procesor XSLT implementujący zalecenia dotyczące wersji 1,0 języka XSL (XSLT). Metoda <xref:System.Xml.Xsl.XslTransform.Load%2A> lokalizuje i odczytuje arkusze stylów, a metoda <xref:System.Xml.Xsl.XslTransform.Transform%2A> przekształca dany dokument źródłowy. Dowolny magazyn, który implementuje interfejs <xref:System.Xml.XPath.IXPathNavigable>, może być używany jako dokument źródłowy dla <xref:System.Xml.Xsl.XslTransform>. .NET Framework obecnie implementuje interfejs <xref:System.Xml.XPath.IXPathNavigable> na <xref:System.Xml.XmlDocument>, <xref:System.Xml.XmlDataDocument> i <xref:System.Xml.XPath.XPathDocument>, dlatego wszystkie te wartości mogą być używane jako wejściowy dokument źródłowy do przekształcenia.

Obiekt <xref:System.Xml.Xsl.XslTransform> w .NET Framework obsługuje specyfikację XSLT 1,0, zdefiniowaną za pomocą następującej przestrzeni nazw:

```xml
<xsl:stylesheet xmlns:xsl="http://www.w3.org/1999/XSL/Transform" version="1.0">
```

Arkusz stylów można załadować przy użyciu metody <xref:System.Xml.Xsl.XslTransform.Load%2A> z jednej z następujących klas:

- Pustym XPathNavigator

- Elementu

- Ciąg reprezentujący adres URL

Istnieje inna metoda <xref:System.Xml.Xsl.XslTransform.Load%2A> dla każdej z powyższych klas wejściowych. Niektóre metody przyjmują kombinację jednej z tych klas i klasy <xref:System.Xml.XmlResolver> jako argumenty. @No__t-0 lokalizuje zasoby, do których odwołuje się `<xsl:import>` lub `<xsl:include>` Znalezione w arkuszu stylów. Następujące metody przyjmują ciąg, <xref:System.Xml.XmlReader> lub <xref:System.Xml.XPath.XPathNavigator> jako dane wejściowe.

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

Większość metod <xref:System.Xml.Xsl.XslTransform.Load%2A> pokazanych powyżej przyjmuje <xref:System.Xml.XmlResolver> jako parametr. @No__t-0 służy do ładowania arkusza stylów i wszystkich arkuszy stylów, do których odwołuje się element xsl: import i xsl: include.

Większość metod <xref:System.Xml.Xsl.XslTransform.Load%2A> przyjmuje również dowody jako parametr. Parametr zeznania jest <xref:System.Security.Policy.Evidence>, który jest skojarzony z arkuszem stylów. Poziom zabezpieczeń arkusza stylów ma wpływ na poziom zabezpieczeń wszelkich kolejnych zasobów, do których się odwołuje, takich jak skrypt, który zawiera, do wszystkich funkcji `document()` i wszystkich obiektów rozszerzeń używanych przez <xref:System.Xml.Xsl.XsltArgumentList>.

Jeśli arkusz stylów jest ładowany przy użyciu metody <xref:System.Xml.Xsl.XslTransform.Load%2A>, która zawiera parametr adresu URL, a żadne dowody nie są dostarczane, dowód arkusza stylów jest obliczany przez połączenie podanego adresu URL ze swoją lokacją i strefą.

Jeśli nie podano żadnego identyfikatora URI lub dowodu, oznacza to, że dowody ustawione dla arkusza stylów są w pełni zaufane. Nie Ładuj arkuszy stylów z niezaufanych źródeł ani nie dodawaj niezaufanych obiektów rozszerzeń do <xref:System.Xml.Xsl.XsltArgumentList>.

Aby uzyskać więcej informacji na temat poziomów zabezpieczeń i dowodów, jak ma to wpływ na skrypty, zobacz [XSLT stylesheet Scripting Using \<msxsl: script >](../../../../docs/standard/data/xml/xslt-stylesheet-scripting-using-msxsl-script.md). Aby uzyskać informacje na temat poziomów zabezpieczeń i dowodów, jak ma to wpływ na obiekty rozszerzeń, zobacz [XsltArgumentList for Style Sheet Parameters and Extension Objects](../../../../docs/standard/data/xml/xsltargumentlist-for-style-sheet-parameters-and-extension-objects.md).

Aby uzyskać informacje na temat poziomów zabezpieczeń i dowodów, jak ma to wpływ na funkcję `document()`, zobacz [rozpoznawanie zewnętrznych arkuszy stylów XSLT i dokumentów](../../../../docs/standard/data/xml/resolving-external-xslt-style-sheets-and-documents.md).

Arkusz stylów może być dostarczony z liczbą parametrów wejściowych. Arkusz stylów może również wywoływać funkcje dla obiektów rozszerzeń. Parametry i obiekty rozszerzeń są dostarczane do arkusza stylów przy użyciu klasy <xref:System.Xml.Xsl.XsltArgumentList>. Aby uzyskać więcej informacji na temat <xref:System.Xml.Xsl.XsltArgumentList>, zobacz <xref:System.Xml.Xsl.XsltArgumentList>.

## <a name="recommended-secure-use-of-xsltransform-class"></a>Zalecane bezpieczne użycie klasy XslTransform

Uprawnienia zabezpieczeń arkusza stylów zależą od dostarczonych dowodów. Poniższa tabela zawiera podsumowanie lokalizacji arkusza stylów i zawiera objaśnienie typu dowodu do przekazania.

- Arkusz stylów XSLT nie ma odwołań zewnętrznych lub arkusz stylów pochodzi z zaufanej podstawy kodu.

  - Podaj dowody z Twojego zestawu:

    ```vb
    Dim xslt = New XslTransform() xslt.Load(stylesheet, resolver, Me.GetType().Assembly.Evidence)

    XsltTransform xslt = new XslTransform();  xslt.Load(stylesheet, resolver, this.GetType().Assembly.Evidence);
    ```

- Arkusz stylów XSLT pochodzi ze źródła zewnętrznego. Źródło źródła jest znane i istnieje zweryfikowany identyfikator URI.

  - Utwórz dowód przy użyciu identyfikatora URI.

    ```vb
    Dim xslt As New XslTransform() Dim ev As Evidence = XmlSecureResolver.CreateEvidenceForUrl(stylesheetUri) xslt.Load(stylesheet, resolver, evidence)

    XslTransform xslt = new XslTransform(); Evidence ev = XmlSecureResolver.CreateEvidenceForUrl(stylesheetUri); xslt.Load(stylesheet, resolver, evidence);
    ```

- Arkusz stylów XSLT pochodzi ze źródła zewnętrznego. Źródło źródła jest nieznane.

  - Ustaw dowód na `null`. Bloki skryptów nie są przetwarzane, funkcja XSLT `document()` nie jest obsługiwana, a uprzywilejowane obiekty rozszerzeń są niedozwolone.

    Ponadto można również ustawić parametr `resolver` na `null`, co gwarantuje, że elementy `xsl:import` i `xsl:include` nie są przetwarzane.

- Arkusz stylów XSLT pochodzi ze źródła zewnętrznego. Źródło źródła jest nieznane, ale wymagana jest obsługa skryptów.

  - Zażądaj dowodu od wywołującego.

## <a name="transformation-of-xml-data"></a>Przekształcanie danych XML

Po załadowaniu arkusza stylów przekształcenie rozpocznie się, wywołując jedną z metod <xref:System.Xml.Xsl.XslTransform.Transform%2A> i dostarczając dokument źródła danych wejściowych. Metoda <xref:System.Xml.Xsl.XslTransform.Transform%2A> jest przeciążona, aby zapewnić różne wyjścia transformacji. Transformacja może spowodować następujące formaty wyjściowe:

- <xref:System.Xml.XmlReader>

- <xref:System.Xml.XmlWriter>

- <xref:System.IO.TextWriter>

- <xref:System.IO.Stream>

- Adres URL ciągu pliku

Ten ostatni format, adres URL ciągu, zapewnia często używany scenariusz do przekształcania dokumentu wejściowego znajdującego się w adresie URL i zapisywania dokumentu w wyjściowym adresie URL. Ta metoda <xref:System.Xml.Xsl.XslTransform.Transform%2A> jest wygodną metodą ładowania dokumentu XML z pliku, wykonywania transformacji XSLT i zapisywania danych wyjściowych do pliku. Uniemożliwia to utworzenie i załadowanie wejściowego dokumentu źródłowego, a następnie zapisanie go w strumieniu pliku. Poniższy przykład kodu pokazuje użycie metody <xref:System.Xml.Xsl.XslTransform.Transform%2A> przy użyciu ciągu adresu URL jako danych wejściowych i wyjściowych:

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

## <a name="transforming-a-section-of-an-xml-document"></a>Przekształcanie sekcji dokumentu XML

Przekształcenia są stosowane do dokumentu jako całości. Innymi słowy, jeśli przejdziesz do węzła innego niż węzeł główny dokumentu, nie uniemożliwi to proces przekształcania uzyskuje dostęp do wszystkich węzłów w załadowanym dokumencie. Aby przekształcić fragment drzewa wyników, należy utworzyć <xref:System.Xml.XmlDocument> zawierający tylko fragment drzewa wynik i przekazać go <xref:System.Xml.XmlDocument> do metody <xref:System.Xml.Xsl.XslTransform.Transform%2A>. Poniższy przykład wykonuje transformację fragmentu drzewa wynik.

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

W przykładzie są stosowane pliki Library. XML i print_root. xsl jako dane wejściowe i wyprowadzane przez konsolę następujące elementy:

```console
Passing <book genre="novel" ISBN="1-861001-57-5"><title>Pride And Prejudice</title></book> to print_root.xsl
Root node is book.
```

Library. XML

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

print_root. xsl

```xml
<stylesheet version="1.0" xmlns="http://www.w3.org/1999/XSL/Transform" >
  <output method="text" />
  <template match="/">
     Root node is  <value-of select="local-name(//*[position() = 1])" />
  </template>
</stylesheet>
```

## <a name="migration-of-xslt-from-net-framework-version-10-to-net-framework-version-11"></a>Migracja XSLT z .NET Framework wersja 1,0 do .NET Framework wersja 1,1

W poniższej tabeli przedstawiono przestarzałe metody .NET Framework w wersji 1,0 oraz nowe metody .NET Framework w wersji 1,1 dla metody <xref:System.Xml.Xsl.XslTransform.Load%2A>. Nowe metody umożliwiają ograniczenie uprawnień arkusza stylów przez określenie dowodu.

|Przestarzałe metody ładowania .NET Framework w wersji 1,0|Zastępowanie metod ładowania .NET Framework w wersji 1,1|
|------------------------------------------------------|---------------------------------------------------------|
|Załaduj (dane wejściowe XPathNavigator);<br /><br /> Załaduj (dane wejściowe.|Załaduj (XPathNavigator StyleSheet, sqlresolverer, dowód potwierdzający);|
|Ładowanie (arkusz stylów IXPathNavigable);<br /><br /> Załaduj (IXPathNavigable StyleSheet, sqlresolverer);|Load (IXPathNavigable StyleSheet, procedura rozpoznawania nazw XmlResolver, dowód dowodu);|
|Ładowanie (arkusz stylów XmlReader);<br /><br /> Załaduj (XmlReader StyleSheet, xmlresolverer);|Załaduj (XmlReader StyleSheet, XmlResolver, resolver, dowód potwierdzający);|

W poniższej tabeli przedstawiono przestarzałe i nowe metody dla metody <xref:System.Xml.Xsl.XslTransform.Transform%2A>. Nowe metody przyjmują obiekt <xref:System.Xml.XmlResolver>.

|Przestarzałe metody transformacji .NET Framework w wersji 1,0|Zastępowanie metod 1,1 .NET Framework wersja przekształcenia|
|-----------------------------------------------------------|--------------------------------------------------------------|
|Transformacja XmlReader (dane wejściowe XPathNavigator, XsltArgumentList args)|Przekształcanie XmlReader (dane wejściowe XPathNavigator, XsltArgumentList args, mechanizm rozwiązywania konfliktów XmlResolver)|
|XmlReader Transform (IXPathNavigable Input, XsltArgumentList args)|XmlReader Transform (IXPathNavigable Input, XsltArgumentList args, xmlresolverer)|
|Unieważnij transformację (dane wejściowe XPathNavigator, XsltArgumentList args, wynik XmlWriter)|Unieważnij transformację (dane wejściowe XPathNavigator, XsltArgumentList args, dane wyjściowe XmlWriter, mechanizm rozwiązywania konfliktów XmlResolver)|
|Void Transform (dane wejściowe IXPathNavigable, XsltArgumentList args, dane wyjściowe XmlWriter)|Unieważnij transformację (dane wejściowe IXpathNavigable, XsltArgumentList args, dane wyjściowe XmlWriter, mechanizm rozwiązywania konfliktów XmlResolver)|
|Void Transform (dane wejściowe XPathNavigator, XsltArgumentList argumentów, wynik TextWriter)|Unieważnij transformację (dane wejściowe XPathNavigator, XsltArgumentList args, dane wyjściowe TextWriter, mechanizm rozwiązywania konfliktów XmlResolver)|
|Void Transform (IXPathNavigable Input, XsltArgumentList args, TextWriter Output)|Void Transform (dane wejściowe IXPathNavigable, XsltArgumentList args, TextWriter Output, resolver XmlResolver)|
|Void Transform (dane wejściowe XPathNavigator, XsltArgumentList args, wyjście strumienia)|Void Transform (dane wejściowe XPathNavigator, XsltArgumentList args, dane wyjściowe strumienia, mechanizm rozwiązywania konfliktów XmlResolver)|
|Void Transform (IXPathNavigable Input, XsltArgumentList args, strumień wyjściowy)|Void Transform (dane wejściowe IXPathNavigable, XsltArgumentList args, dane wyjściowe strumienia, mechanizm rozwiązywania konfliktów XmlResolver)|
|Void Transform (ciąg wejściowy, ciąg wyjściowy);|Unieważnij transformację (dane wejściowe ciągów, ciągi danych wyjściowych, mechanizm rozwiązywania konfliktów XmlResolver);|

Właściwość <xref:System.Xml.Xsl.XslTransform.XmlResolver%2A?displayProperty=nameWithType> jest przestarzała w .NET Framework wersji 1,1. Zamiast tego należy użyć nowych przeciążeń <xref:System.Xml.Xsl.XslTransform.Transform%2A>, które pobierają obiekt <xref:System.Xml.XmlResolver>.

## <a name="see-also"></a>Zobacz także

- <xref:System.Xml.Xsl.XslTransform>
- [Przekształcenia XSLT przy użyciu klasy XslTransform](../../../../docs/standard/data/xml/xslt-transformations-with-the-xsltransform-class.md)
- [Klasa XPathNavigator w przekształceniach](../../../../docs/standard/data/xml/xpathnavigator-in-transformations.md)
- [Klasa XPathNodeIterator w przekształceniach](../../../../docs/standard/data/xml/xpathnodeiterator-in-transformations.md)
- [Dane wejściowe obiektu XPathDocument klasy XslTransform](../../../../docs/standard/data/xml/xpathdocument-input-to-xsltransform.md)
- [Dane wejściowe obiektu XmlDataDocument klasy XslTransform](../../../../docs/standard/data/xml/xmldatadocument-input-to-xsltransform.md)
- [Dane wejściowe obiektu XmlDocument klasy XslTransform](../../../../docs/standard/data/xml/xmldocument-input-to-xsltransform.md)
