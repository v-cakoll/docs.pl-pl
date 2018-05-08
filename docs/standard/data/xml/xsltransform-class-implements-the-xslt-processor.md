---
title: Klasa XslTransform implementuje procesorze XSLT
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 88373fe2-4a6b-44f9-8a62-8a3e348e3a46
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5fd0a72ab0274fe6ccc2016d90739a5fda876826
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="xsltransform-class-implements-the-xslt-processor"></a>Klasa XslTransform implementuje procesorze XSLT
> [!NOTE]
>  <xref:System.Xml.Xsl.XslTransform> Klasa jest przestarzała w [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)]. Może wykonywać rozszerzalny język arkusza stylów dla transformacji przekształcenia XSLT () przy użyciu <xref:System.Xml.Xsl.XslCompiledTransform> klasy. Zobacz [za pomocą klasy XslCompiledTransform](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) i [migracji z klasy XslTransform](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md) Aby uzyskać więcej informacji.  
  
 <xref:System.Xml.Xsl.XslTransform> Klasa jest procesorze XSLT Implementowanie zalecenie transformacji XSL (XSLT) w wersji 1.0. <xref:System.Xml.Xsl.XslTransform.Load%2A> Metody lokalizuje i odczytuje arkusze stylów i <xref:System.Xml.Xsl.XslTransform.Transform%2A> metody przekształca dokumentu danego źródła. Dowolnego magazynu, który implementuje <xref:System.Xml.XPath.IXPathNavigable> interfejsu może być używany jako dokument źródłowy dla <xref:System.Xml.Xsl.XslTransform>. [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Implementuje obecnie <xref:System.Xml.XPath.IXPathNavigable> interfejs w <xref:System.Xml.XmlDocument>, <xref:System.Xml.XmlDataDocument>i <xref:System.Xml.XPath.XPathDocument>, więc wszystkie te mogą być używane jako źródło danych wejściowych dokumentu do przekształcenia.  
  
 <xref:System.Xml.Xsl.XslTransform> Obiektu w [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] obsługuje tylko specyfikację XSLT 1.0 zdefiniowane z następujących nazw:  
  
```xml  
<xsl:stylesheet xmlns:xsl="http://www.w3.org/1999/XSL/Transform" version="1.0">    
```  
  
 Arkusz stylów mogą być ładowane, przy użyciu <xref:System.Xml.Xsl.XslTransform.Load%2A> metody z jednego z następujących klas:  
  
-   Element XPathNavigator  
  
-   Element XmlReader  
  
-   Ciąg reprezentujący adres URL  
  
 Istnieje inny <xref:System.Xml.Xsl.XslTransform.Load%2A> metody dla każdego z powyższych klas wejściowego. W przypadku niektórych metod zająć w połączeniu z jednej z tych klas i <xref:System.Xml.XmlResolver> klasy jako argumenty. <xref:System.Xml.XmlResolver> Lokalizuje zasoby odwołuje się `<xsl:import>` lub `<xsl:include>` znaleziono w arkuszu stylów. Następujące metody przyjmują ciąg, <xref:System.Xml.XmlReader>, lub <xref:System.Xml.XPath.XPathNavigator> jako dane wejściowe.  
  
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
  
 Większość <xref:System.Xml.Xsl.XslTransform.Load%2A> metod przedstawionych powyżej podjęcia <xref:System.Xml.XmlResolver> jako parametr. <xref:System.Xml.XmlResolver> Jest używana do ładowania arkusza stylów i wszystkie arkusze stylów w XSL: Import i xsl: obejmują elementy.  
  
 Większość <xref:System.Xml.Xsl.XslTransform.Load%2A> metody również wziąć dowód jako parametr. Parametr dowód jest <xref:System.Security.Policy.Evidence> skojarzonego z arkusza stylów. Poziom zabezpieczeń arkusza stylów wpływa na poziom zabezpieczeń kolejnych odwołuje się on do zasobów, takich jak skrypt w nim żadnego `document()` wykorzystuje funkcje i obiekty rozszerzenia używane przez <xref:System.Xml.Xsl.XsltArgumentList>.  
  
 Jeśli arkusz stylów został załadowany przy użyciu <xref:System.Xml.Xsl.XslTransform.Load%2A> podano metodę, która zawiera parametr adresu URL i oznak, dowód arkusza stylów jest obliczany przez połączenie podany adres URL z lokacji i strefy.  
  
 Jeśli podano Brak identyfikatora URI lub dowód, następnie dowodu zestawu dla arkusza stylów jest w pełni zaufany. Nie załadować arkusze stylów ze źródeł niezaufanych lub dodać rozszerzenie niezaufanych obiektów do <xref:System.Xml.Xsl.XsltArgumentList>.  
  
 Aby uzyskać więcej informacji na temat poziomów zabezpieczeń i dowód i jak wpływa na wykonywanie skryptów, zobacz [XSLT skryptów przy użyciu arkusza stylów \<msxsl:script >](../../../../docs/standard/data/xml/xslt-stylesheet-scripting-using-msxsl-script.md). Aby informacji na temat poziomów zabezpieczeń i dowód i jak wpływa na obiekty rozszerzenia, zobacz [XsltArgumentList parametry arkusza stylów i obiektów rozszerzenia](../../../../docs/standard/data/xml/xsltargumentlist-for-style-sheet-parameters-and-extension-objects.md).  
  
 Informacje dotyczące poziomów zabezpieczeń i dowód i jak wpływa na `document()` funkcji, zobacz [Rozpoznawanie zewnętrznych arkuszy stylów XSLT i dokumentów](../../../../docs/standard/data/xml/resolving-external-xslt-style-sheets-and-documents.md).  
  
 Arkusz stylów można podać z liczbą parametrów wejściowych. Arkusz stylów można również wywołać funkcji rozszerzenia obiektów. Podano zarówno parametrów, jak i obiektów rozszerzeń przy użyciu arkusza stylów <xref:System.Xml.Xsl.XsltArgumentList> klasy. Aby uzyskać więcej informacji na temat <xref:System.Xml.Xsl.XsltArgumentList>, zobacz <xref:System.Xml.Xsl.XsltArgumentList>.  
  
## <a name="recommended-secure-use-of-xsltransform-class"></a>Zalecane użycie bezpiecznego XslTransform klasy  
 Uprawnienia zabezpieczeń arkusza stylów zależą od dowody dostarczone. Poniższa tabela zawiera podsumowanie Lokalizacja arkusza stylów oraz zawiera wyjaśnienie, jakiego rodzaju dowód umożliwiają.  
  
-   Arkusz stylów XSLT nie ma zewnętrznych odwołań lub arkusz stylów, z którym ufasz, że określona ścieżka bazowa kodu.  
  
    -   Podaj dowód z Twojego zestawu:  
  
         `Dim xslt = New XslTransform() xslt.Load(stylesheet, resolver, Me.GetType().Assembly.Evidence)`  
  
         `XsltTransform xslt = new XslTransform();  xslt.Load(stylesheet, resolver, this.GetType().Assembly.Evidence);`  
  
-   Arkusz stylów XSLT pochodzą ze źródła zewnętrznego. Jest on znany pochodzenie źródła i jest możliwe do zweryfikowania identyfikatorem URI.  
  
    -   Utwórz dowód przy użyciu identyfikatora URI.  
  
         `Dim xslt As New XslTransform() Dim ev As Evidence = XmlSecureResolver.CreateEvidenceForUrl(stylesheetUri) xslt.Load(stylesheet, resolver, evidence)`  
  
         `XslTransform xslt = new XslTransform(); Evidence ev = XmlSecureResolver.CreateEvidenceForUrl(stylesheetUri); xslt.Load(stylesheet, resolver, evidence);`  
  
-   Arkusz stylów XSLT pochodzą ze źródła zewnętrznego. Pochodzenie źródła nie jest znany.  
  
    -   Ustaw dowód `null`. Bloki skryptu nie są przetwarzane, XSLT `document()` funkcja nie jest obsługiwana i obiekty uprzywilejowanych rozszerzenia są niedozwolone.  
  
         Ponadto można również ustawić `resolver` parametr `null` gwarantuje to, że `xsl:import` i `xsl:include` elementy nie zostały przetworzone.  
  
-   Arkusz stylów XSLT pochodzą ze źródła zewnętrznego. Pochodzenie źródła nie jest znany, ale wymagają obsługi skryptów.  
  
    -   Żądanie dowodu wywołujący.  
  
## <a name="transformation-of-xml-data"></a>Przekształcenia danych XML  
 Po załadowaniu arkusz stylów transformacja rozpoczyna się przez wywoływanie jednej z <xref:System.Xml.Xsl.XslTransform.Transform%2A> metod i dostarczenie dokument źródło danych wejściowych. <xref:System.Xml.Xsl.XslTransform.Transform%2A> Metody jest przeciążona zapewnienie różnych przekształcania danych wyjściowych. Transformacja może spowodować następujące formaty danych wyjściowych:  
  
-   <xref:System.Xml.XmlReader>  
  
-   <xref:System.Xml.XmlWriter>  
  
-   <xref:System.IO.TextWriter>  
  
-   <xref:System.IO.Stream>  
  
-   Ciąg adres URL pliku  
  
 Udostępnia tego ostatniego formatu ciągu adresu URL, dla scenariusza często używane w Przekształcanie dokument wejściowy znajduje się w adresie URL i zapisywanie dokumentu do adresu URL danych wyjściowych. To <xref:System.Xml.Xsl.XslTransform.Transform%2A> metoda jest metodą wygody do ładowania dokumentu XML z pliku, przekształcenie XSLT i zapisuje dane wyjściowe do pliku. Zapobiega konieczności tworzenia i załadować dokument źródło danych wejściowych, a następnie zapisać do strumienia pliku. Poniższy przykład kodu pokazuje to <xref:System.Xml.Xsl.XslTransform.Transform%2A> metodę przy użyciu adresu URL ciąg jako dane wejściowe i wyjściowe:  
  
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
 Przekształcenia mają zastosowanie do dokumentu jako całość. Innymi słowy w przypadku przekazania w węźle innym niż węzeł główny dokumentu, to nie zapobiega proces przekształcania podczas uzyskiwania dostępu do wszystkich węzłów w załadowanego dokumentu. Aby przekształcić wynikowego fragmentu drzewa, musisz utworzyć <xref:System.Xml.XmlDocument> zawierający tylko drzewa wynik fragmentu i przekazać, który <xref:System.Xml.XmlDocument> do <xref:System.Xml.Xsl.XslTransform.Transform%2A> — metoda. Poniższy przykład wykonuje transformację na wynikowego fragmentu drzewa.  
  
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
  
 W przykładzie użyto library.xml i print_root.xsl pliki jako dane wejściowe i wyświetla następujące polecenie, aby konsoli.  
  
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
  
## <a name="migration-of-xslt-from-net-framework-version-10-to-net-framework-version-11"></a>Migracja pliku XSLT z .NET Framework w wersji 1.0 .NET Framework w wersji 1.1  
 W poniższej tabeli przedstawiono przestarzałe [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] metod w wersji 1.0 i nowych [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] metody wersji 1.1 <xref:System.Xml.Xsl.XslTransform.Load%2A> metody. Nowych metod pozwalają ograniczyć uprawnienia arkusza stylów, określając dowód.  
  
|Przestarzałe metody obciążenia programu .NET Framework w wersji 1.0|Zastąpienie środowiska .NET Framework w wersji 1.1 obciążenia metody|  
|------------------------------------------------------|---------------------------------------------------------|  
|Obciążenia (dane wejściowe Element XPathNavigator);<br /><br /> Obciążenia (Element XPathNavigator wejściowych, element XmlResolver rozpoznawania nazw);|Obciążenia (arkusza stylów Element XPathNavigator, element XmlResolver programu rozpoznawania nazw, dowód dowód);|  
|Obciążenia (arkusza stylów IXPathNavigable);<br /><br /> Obciążenia (IXPathNavigable arkusza stylów, element XmlResolver rozpoznawania);|Obciążenia (IXPathNavigable arkusza stylów, element XmlResolver programu rozpoznawania nazw, dowód dowód);|  
|Obciążenia (arkusza stylów XmlReader);<br /><br /> Obciążenia (XmlReader arkusza stylów, element XmlResolver rozpoznawania);|Obciążenia (XmlReader arkusza stylów, element XmlResolver programu rozpoznawania nazw, dowód dowód);|  
  
 W poniższej tabeli przedstawiono metody przestarzałe i nowych <xref:System.Xml.Xsl.XslTransform.Transform%2A> metody. Nowe metody przyjmują <xref:System.Xml.XmlResolver> obiektu.  
  
|.NET Framework w wersji 1.0 przekształcenie metody przestarzałe|Wersja programu .NET Framework zastąpienie metody przekształcania 1.1|  
|-----------------------------------------------------------|--------------------------------------------------------------|  
|Element XmlReader Transform(XPathNavigator input, XsltArgumentList args)|Element XmlReader Transform(XPathNavigator input, XsltArgumentList args, XmlResolver resolver)|  
|Element XmlReader Transform(IXPathNavigable input, XsltArgumentList args)|Element XmlReader Transform(IXPathNavigable input, XsltArgumentList args, XmlResolver resolver)|  
|Przekształć void (dane wejściowe Element XPathNavigator, XsltArgumentList argumentów, dane wyjściowe XmlWriter)|Przekształć void (wejściowy Element XPathNavigator, XsltArgumentList argumentów, dane wyjściowe XmlWriter, element XmlResolver programu rozpoznawania nazw)|  
|Przekształć void (dane wejściowe IXPathNavigable, XsltArgumentList argumentów, dane wyjściowe XmlWriter)|Przekształć void (IXpathNavigable danych wejściowych, XsltArgumentList argumentów, dane wyjściowe XmlWriter, element XmlResolver programu rozpoznawania nazw)|  
|Przekształć void (dane wejściowe Element XPathNavigator, XsltArgumentList argumentów, dane wyjściowe TextWriter)|Przekształć void (dane wejściowe Element XPathNavigator, XsltArgumentList argumentów, dane wyjściowe TextWriter, element XmlResolver programu rozpoznawania nazw)|  
|Przekształć void (dane wejściowe IXPathNavigable, XsltArgumentList argumentów, dane wyjściowe TextWriter)|Przekształć void (dane wejściowe IXPathNavigable, XsltArgumentList argumentów, dane wyjściowe TextWriter, element XmlResolver programu rozpoznawania nazw)|  
|Przekształć void (dane wejściowe Element XPathNavigator, XsltArgumentList argumentów, strumieni wyjściowych)|Przekształć void (dane wejściowe Element XPathNavigator, XsltArgumentList argumentów, strumieni wyjściowych, element XmlResolver programu rozpoznawania nazw)|  
|Przekształć void (dane wejściowe IXPathNavigable, argumentów XsltArgumentList strumieni wyjściowych)|Przekształć void (dane wejściowe IXPathNavigable, XsltArgumentList argumentów, strumieni wyjściowych, element XmlResolver programu rozpoznawania nazw)|  
|Void przekształcenie (ciągu wejściowego, ciąg dane wyjściowe);|Void przekształcenie (ciągu wejściowego, ciąg dane wyjściowe, element XmlResolver rozpoznawania);|  
  
 <xref:System.Xml.Xsl.XslTransform.XmlResolver%2A?displayProperty=nameWithType> Właściwość jest przestarzała w [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] wersji 1.1. Zamiast tego należy użyć nowego <xref:System.Xml.Xsl.XslTransform.Transform%2A> overloads uwzględniającymi <xref:System.Xml.XmlResolver> obiektu.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Xml.Xsl.XslTransform>  
 [Przekształcenia XSLT przy użyciu klasy XslTransform](../../../../docs/standard/data/xml/xslt-transformations-with-the-xsltransform-class.md)  
 [Klasa XPathNavigator w przekształceniach](../../../../docs/standard/data/xml/xpathnavigator-in-transformations.md)  
 [Klasa XPathNodeIterator w przekształceniach](../../../../docs/standard/data/xml/xpathnodeiterator-in-transformations.md)  
 [Dane wejściowe obiektu XPathDocument klasy XslTransform](../../../../docs/standard/data/xml/xpathdocument-input-to-xsltransform.md)  
 [Dane wejściowe obiektu XmlDataDocument klasy XslTransform](../../../../docs/standard/data/xml/xmldatadocument-input-to-xsltransform.md)  
 [Dane wejściowe obiektu XmlDocument klasy XslTransform](../../../../docs/standard/data/xml/xmldocument-input-to-xsltransform.md)
