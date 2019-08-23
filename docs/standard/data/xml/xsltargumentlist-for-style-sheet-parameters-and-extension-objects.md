---
title: Klasa XsltArgumentList — parametry arkusza stylów i obiekty rozszerzeń
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: de2f0dce-6b98-4908-bba7-ed150cc50355
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 9d08399933f37c4110639bf1f4a81f222dd597b4
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69910323"
---
# <a name="xsltargumentlist-for-style-sheet-parameters-and-extension-objects"></a>Klasa XsltArgumentList — parametry arkusza stylów i obiekty rozszerzeń
<xref:System.Xml.Xsl.XsltArgumentList> Klasa zawiera Extensible Stylesheet Language dla parametrów Transformations (XSLT) i obiektów rozszerzeń XSLT. Po przekazaniu <xref:System.Xml.Xsl.XslTransform.Transform%2A> do metody te parametry i obiekty rozszerzeń mogą być wywoływane z arkuszy stylów.  
  
> [!NOTE]
> Klasy <xref:System.Xml.Xsl.XslTransform> i<xref:System.Xml.Xsl.XsltArgumentList> są przestarzałe w .NET Framework 2,0. Przekształcenia XSLT można wykonywać przy użyciu <xref:System.Xml.Xsl.XslCompiledTransform> klasy. Aby uzyskać więcej informacji, zobacz [Używanie klasy XslCompiledTransform](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) i [Migrowanie z klasy XslTransform](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md) .  
  
 <xref:System.Xml.Xsl.XsltArgumentList> Klasa zawiera parametry XSLT i obiekty rozszerzeń XSLT. Po przekazaniu <xref:System.Xml.Xsl.XslTransform.Transform%2A> do metody te parametry i obiekty rozszerzeń mogą być wywoływane z arkuszy stylów.  
  
 Poniżej przedstawiono zalety przekazywania obiektów zamiast używać osadzonego skryptu:  
  
- Zapewnia lepszą hermetyzację i ponowne użycie klas.  
  
- Zezwala na mniejsze i łatwiejsze w obsłudze arkusze stylów.  
  
- Obsługuje metody wywoływania w klasach należących do przestrzeni nazw innych niż te zdefiniowane w ramach <xref:System> zestawu obsługiwanych przestrzeni nazw.  
  
- Obsługuje przekazywanie fragmentów drzewa wyników do arkusza stylów przy użyciu <xref:System.Xml.XPath.XPathNodeIterator>.  
  
## <a name="xslt-style-sheet-parameters"></a>Parametry arkusza stylów XSLT  
 Parametry XSLT są dodawane do <xref:System.Xml.Xsl.XsltArgumentList> <xref:System.Xml.Xsl.XsltArgumentList.AddParam%2A> metody using. Kwalifikowana nazwa i przestrzeń nazw Uniform Resource Identifier (URI) są skojarzone z obiektem parametru w tym czasie.  
  
 Obiekt parametru powinien odpowiadać typowi organizacja World Wide Web Consortium (W3C). W poniższej tabeli przedstawiono odpowiednie typy W3C, równoważne klasy .NET Framework (typ) i określające, czy typem W3C jest typ języka ścieżki XML (XPath) czy typ XSLT.  
  
|Typ W3C|Równoważna Klasa .NET Framework (typ)|Typ XPath lub typ XSLT|  
|--------------|----------------------------------------------|-----------------------------|  
|String|System.String|XPath|  
|Boolean|System.Boolean|XPath|  
|Wartość liczbowa|System.Double|XPath|  
|Fragment drzewa wyników|System.Xml.XPath.XPathNavigator|XSLT|  
|Zestaw węzłów|System.Xml.XPath.XPathNodeIterator|XPath|  
  
 Jeśli obiekt parametru nie jest jedną z powyższych klas, wymuszony jest podwójny lub ciąg, zgodnie z potrzebami. Wartości Int16, UInt16, Int32, UInt32, Int64, UInt64, Single i Decimal są wymuszane jako Double. Wszystkie inne typy są wymuszane jako ciąg za pomocą `ToString` metody.  
  
#### <a name="to-use-the-xslt-parameter-the-user-needs-to-do-the-following"></a>Aby użyć parametru XSLT, użytkownik musi wykonać następujące czynności:  
  
1. Utwórz i Dodaj obiekty przy użyciu <xref:System.Xml.Xsl.XsltArgumentList.AddParam%2A>. <xref:System.Xml.Xsl.XsltArgumentList>  
  
2. Wywołaj parametry z arkusza stylów.  
  
3. <xref:System.Xml.Xsl.XsltArgumentList> Przekaż<xref:System.Xml.Xsl.XslTransform.Transform%2A> do metody.  
  
### <a name="example"></a>Przykład  
 W poniższym przykładzie zastosowano <xref:System.Xml.Xsl.XsltArgumentList.AddParam%2A> metodę, aby utworzyć parametr do przechowywania obliczonej daty rabatu. Data rabatu jest obliczana na 20 dni od daty zamówienia.  
  
```vb  
Imports System  
Imports System.IO  
Imports System.Xml  
Imports System.Xml.XPath  
Imports System.Xml.Xsl  
  
Public class Sample  
  
   Private Const filename As String = "order.xml"  
   Private Const stylesheet As String = "discount.xsl"  
  
   Public Shared Sub Main()  
  
    'Create the XslTransform and load the style sheet.  
    Dim xslt As XslTransform = New XslTransform  
    xslt.Load(stylesheet)  
  
    'Load the XML data file.  
    Dim doc As XPathDocument = New XPathDocument(filename)  
  
    'Create an XsltArgumentList.  
    Dim xslArg As XsltArgumentList = New XsltArgumentList  
  
    'Calculate the discount date.  
    Dim today As DateTime = DateTime.Now  
    Dim d As DateTime = today.AddDays(20)  
    xslArg.AddParam("discount", "", d.ToString())  
  
    'Create an XmlTextWriter to handle the output.  
    Dim writer As XmlTextWriter = New XmlTextWriter("orderout.xml", Nothing)  
  
    'Transform the file.  
    xslt.Transform(doc, xslArg, writer, Nothing)  
  
    writer.Close()  
  
  End Sub  
End Class  
```  
  
```csharp  
using System;  
using System.IO;  
using System.Xml;  
using System.Xml.XPath;  
using System.Xml.Xsl;  
  
public class Sample  
{  
   private const String filename = "order.xml";  
   private const String stylesheet = "discount.xsl";  
  
   public static void Main() {  
  
    //Create the XslTransform and load the style sheet.  
    XslTransform xslt = new XslTransform();  
    xslt.Load(stylesheet);  
  
    //Load the XML data file.  
    XPathDocument doc = new XPathDocument(filename);  
  
    //Create an XsltArgumentList.  
    XsltArgumentList xslArg = new XsltArgumentList();  
  
    //Calculate the discount date.  
    DateTime today = DateTime.Now;  
    DateTime d = today.AddDays(20);  
    xslArg.AddParam("discount", "", d.ToString());  
  
    //Create an XmlTextWriter to handle the output.  
    XmlTextWriter writer = new XmlTextWriter("orderout.xml", null);  
  
    //Transform the file.  
    xslt.Transform(doc, xslArg, writer, null);  
    writer.Close();  
  }  
}  
```  
  
### <a name="input"></a>Dane wejściowe  
 order.xml  
  
```xml  
<!--Represents a customer order-->  
<order>  
  <book ISBN='10-861003-324'>  
    <title>The Handmaid's Tale</title>  
    <price>19.95</price>  
  </book>  
  <cd ISBN='2-3631-4'>  
    <title>Americana</title>  
    <price>16.95</price>  
  </cd>  
</order>  
```  
  
 Discount. xsl  
  
```xml  
<xsl:stylesheet version="1.0" xmlns:xsl="http://www.w3.org/1999/XSL/Transform">  
  <xsl:param name="discount"/>  
  <xsl:template match="/">  
    <order>  
      <xsl:variable name="sub-total" select="sum(//price)"/>  
      <total><xsl:value-of select="$sub-total"/></total>  
      15% discount if paid by: <xsl:value-of select="$discount"/>  
    </order>  
  </xsl:template>  
</xsl:stylesheet>  
```  
  
### <a name="output"></a>Dane wyjściowe  
  
```xml  
<order>  
   <total>36.9</total>   
   15% discount if paid by: 5/6/2001 5:01:15 PM   
</order>  
```  
  
## <a name="xslt-extension-objects"></a>Obiekty rozszerzeń XSLT  
 Obiekty rozszerzeń XSLT są dodawane do <xref:System.Xml.Xsl.XsltArgumentList> <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> metody using. Kwalifikowana nazwa i identyfikator URI przestrzeni nazw są skojarzone z obiektem rozszerzenia w tym czasie.  
  
 Po dodaniu obiektu obiekt wywołujący <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> musi być w pełni zaufany w zasadach zabezpieczeń. Jeśli obiekt wywołujący jest częściowo zaufany, dodanie nie powiedzie się.  
  
 Mimo że obiekt został pomyślnie dodany, nie gwarantuje to, że wykonywanie zakończy się pomyślnie. Gdy metoda jest wywoływana, uprawnienia są obliczane na podstawie dowodów dostarczonych w <xref:System.Xml.Xsl.XslTransform.Load%2A> czasie, a zestaw uprawnień jest przypisany do całego procesu transformacji. <xref:System.Xml.Xsl.XslTransform.Transform%2A> Jeśli obiekt rozszerzenia próbuje zainicjować akcję, która wymaga uprawnień nieznalezionych w zestawie, zgłaszany jest wyjątek.  
  
 Typy danych zwracane z obiektów rozszerzeń to jeden z czterech podstawowych typów danych XPath o liczbie, ciągu, wartości logicznej i zestawie węzłów.  
  
#### <a name="to-use-the-xslt-extension-object-the-user-needs-to-do-the-following"></a>Aby użyć obiektu rozszerzenia XSLT, użytkownik musi wykonać następujące czynności:  
  
1. Utwórz i Dodaj obiekt rozszerzenia przy użyciu <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A>. <xref:System.Xml.Xsl.XsltArgumentList>  
  
2. Wywołaj obiekt rozszerzenia z arkusza stylów.  
  
3. <xref:System.Xml.Xsl.XsltArgumentList> Przekaż<xref:System.Xml.Xsl.XslTransform.Transform%2A> do metody.  
  
### <a name="example"></a>Przykład  
 Poniższy przykład oblicza obwód okręgu, w którym znajduje się jego promień.  
  
```vb  
Imports System  
Imports System.IO  
Imports System.Xml  
Imports System.Xml.XPath  
Imports System.Xml.Xsl  
  
Public Class Sample  
   Private Const filename As String = "number.xml"  
   Private Const stylesheet As String = "circle.xsl"  
  
   Public Shared Sub Main()  
        Dim test As Sample = New Sample  
   End Sub  
  
  Public Sub New()  
    'Create the XslTransform and load the style sheet.  
    Dim xslt As XslTransform = New XslTransform  
    xslt.Load(stylesheet)  
  
    'Load the XML data file.  
    Dim doc As XPathDocument = New XPathDocument(filename)  
  
    'Create an XsltArgumentList.  
    Dim xslArg As XsltArgumentList = New XsltArgumentList  
  
    'Add an object to calculate the circumference of the circle.  
    Dim obj As Calculate = New Calculate  
    xslArg.AddExtensionObject("urn:myObj", obj)  
  
    'Create an XmlTextWriter to output to the console.  
    Dim writer As XmlTextWriter = New XmlTextWriter(Console.Out)  
  
    'Transform the file.  
    xslt.Transform(doc, xslArg, writer, Nothing)  
    writer.Close()  
  
  End Sub  
  
  'Calculates the circumference of a circle given the radius.  
  Public Class Calculate  
  
    Private circ As double = 0  
  
    Public Function Circumference(radius As Double) As Double  
       circ = Math.PI*2*radius  
       Return circ  
    End Function  
  End Class  
End Class  
```  
  
```csharp  
using System;  
using System.IO;  
using System.Xml;  
using System.Xml.XPath;  
using System.Xml.Xsl;  
  
public class Sample  
{  
   private const String filename = "number.xml";  
   private const String stylesheet = "circle.xsl";  
  
   public static void Main() {  
  
        Sample test = new Sample();  
    }  
  
  public Sample() {  
  
    //Create the XslTransform and load the style sheet.  
    XslTransform xslt = new XslTransform();  
    xslt.Load(stylesheet);  
  
    //Load the XML data file.  
    XPathDocument doc = new XPathDocument(filename);  
  
    //Create an XsltArgumentList.  
    XsltArgumentList xslArg = new XsltArgumentList();  
  
    //Add an object to calculate the circumference of the circle.  
    Calculate obj = new Calculate();  
    xslArg.AddExtensionObject("urn:myObj", obj);  
  
    //Create an XmlTextWriter to output to the console.  
    XmlTextWriter writer = new XmlTextWriter(Console.Out);  
  
    //Transform the file.  
    xslt.Transform(doc, xslArg, writer, null);  
    writer.Close();  
  
  }  
  
  //Calculates the circumference of a circle given the radius.  
  public class Calculate {  
  
    private double circ = 0;  
  
    public double Circumference(double radius){  
       circ = Math.PI*2*radius;  
       return circ;  
    }  
  }  
}  
```  
  
### <a name="input"></a>Dane wejściowe  
 number.xml  
  
```xml  
<?xml version='1.0'?>  
<data>  
  <circle>  
    <radius>12</radius>  
  </circle>  
  <circle>  
    <radius>37.5</radius>  
  </circle>  
</data>    
```  
  
 Circle. xsl  
  
```xml  
<xsl:stylesheet version="1.0" xmlns:xsl="http://www.w3.org/1999/XSL/Transform"  
    xmlns:myObj="urn:myObj">  
  
  <xsl:template match="data">  
  <circles>  
  <xsl:for-each select="circle">  
    <circle>  
    <xsl:copy-of select="node()"/>  
       <circumference>  
          <xsl:value-of select="myObj:Circumference(radius)"/>          
       </circumference>  
    </circle>  
  </xsl:for-each>  
  </circles>  
  </xsl:template>  
</xsl:stylesheet>  
```  
  
### <a name="output"></a>Dane wyjściowe  
 `<circles xmlns:myObj="urn:myObj">`  
  
 `<circle>`  
  
 `<radius>12</radius>`  
  
 `<circumference>75.398223686155</circumference>`  
  
 `</circle>`  
  
 `<circle>`  
  
 `<radius>37.5</radius>`  
  
 `<circumference>235.61944901923448</circumference>`  
  
 `</circle>`  
  
 `</circles>`  
  
## <a name="see-also"></a>Zobacz także

- [Implementowanie procesora XSLT przy użyciu klasy XslTransform](../../../../docs/standard/data/xml/xsltransform-class-implements-the-xslt-processor.md)
