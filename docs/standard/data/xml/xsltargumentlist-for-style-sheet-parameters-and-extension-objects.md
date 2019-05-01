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
ms.openlocfilehash: e6209df7d226d7e3acb938801d1fb77afbe1249b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62026612"
---
# <a name="xsltargumentlist-for-style-sheet-parameters-and-extension-objects"></a>Klasa XsltArgumentList — parametry arkusza stylów i obiekty rozszerzeń
<xref:System.Xml.Xsl.XsltArgumentList> Klasa zawiera rozszerzalny język arkusza stylów dla parametrów przekształcenia (XSLT) i obiekty rozszerzeń XSLT. Przy przekazywaniu do <xref:System.Xml.Xsl.XslTransform.Transform%2A> metody te parametry i rozszerzenie obiekty mogą być wywoływane z arkuszy stylów.  
  
> [!NOTE]
>  <xref:System.Xml.Xsl.XslTransform> i <xref:System.Xml.Xsl.XsltArgumentList> klasy są przestarzałe w programie [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)]. Można wykonywać przekształcenia XSLT przy użyciu <xref:System.Xml.Xsl.XslCompiledTransform> klasy. Zobacz [używanie klasy XslCompiledTransform](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) i [Migrowanie z klasy XslTransform](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md) Aby uzyskać więcej informacji.  
  
 <xref:System.Xml.Xsl.XsltArgumentList> Klasa zawiera parametry XSLT i obiekty rozszerzeń XSLT. Przy przekazywaniu do <xref:System.Xml.Xsl.XslTransform.Transform%2A> metody te parametry i rozszerzenie obiekty mogą być wywoływane z arkuszy stylów.  
  
 Poniżej przedstawiono zalety przekazywania obiektu, a nie przy użyciu osadzonych skryptów:  
  
- Zapewnia lepszą hermetyzacji i ponowne użycie klas.  
  
- Umożliwia arkusze stylów była mniejsza i będzie łatwiejszy w utrzymaniu.  
  
- Program obsługuje wywoływania metod w klasach należące do przestrzeni nazw, innym niż te zdefiniowane w zestawie obsługiwanych <xref:System> przestrzeni nazw.  
  
- Obsługuje przekazywanie fragmenty drzewa wynik do arkusza stylów z użyciem <xref:System.Xml.XPath.XPathNodeIterator>.  
  
## <a name="xslt-style-sheet-parameters"></a>Parametry arkusza stylów XSLT  
 Parametry XSLT są dodawane do <xref:System.Xml.Xsl.XsltArgumentList> przy użyciu <xref:System.Xml.Xsl.XsltArgumentList.AddParam%2A> metody. Kwalifikowana nazwa i identyfikator (URI nazw) są skojarzone z obiektem parametrów w tym czasie.  
  
 Obiekt parametr powinien odpowiadać typowi World Wide Web Consortium (W3C). W poniższej tabeli przedstawiono odpowiednie typy W3C odpowiednik [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] klasy (typ), oraz czy typ W3C jest typu XML Path Language (XPath) lub XSLT.  
  
|Typ W3C|Odpowiednik klasy .NET Framework (typ)|Wyrażenie XPath typu lub XSLT|  
|--------------|----------------------------------------------|-----------------------------|  
|String|System.String|XPath|  
|Boolean|System.Boolean|XPath|  
|Wartość liczbowa|System.Double|XPath|  
|Wynikowego fragmentu drzewa|System.Xml.XPath.XPathNavigator|XSLT|  
|Zestaw węzłów|System.Xml.XPath.XPathNodeIterator|XPath|  
  
 Jeśli obiekt parametr nie jest jedną z powyższych klas, jest zmuszony do Double lub ciąg, zgodnie z potrzebami. Typy Int16, UInt16, Int32, UInt32, Int64, UInt64, pojedynczego i dziesiętnych będą obowiązkowo przenoszone na wartość o podwójnej precyzji. Wszystkie pozostałe typy będą obowiązkowo przenoszone na ciąg przy użyciu `ToString` metody.  
  
#### <a name="to-use-the-xslt-parameter-the-user-needs-to-do-the-following"></a>Aby użyć parametru XSLT, użytkownik musi wykonać następujące czynności:  
  
1. Tworzenie <xref:System.Xml.Xsl.XsltArgumentList> i dodawanie obiektów przy użyciu <xref:System.Xml.Xsl.XsltArgumentList.AddParam%2A>.  
  
2. Parametry wywołań z arkusza stylów.  
  
3. Przekaż <xref:System.Xml.Xsl.XsltArgumentList> do <xref:System.Xml.Xsl.XslTransform.Transform%2A> metody.  
  
### <a name="example"></a>Przykład  
 W poniższym przykładzie użyto <xref:System.Xml.Xsl.XsltArgumentList.AddParam%2A> metodę, aby utworzyć parametr do przechowywania daty obliczony rabat. Data rabatu jest obliczana za 20 dni od daty zamówienia.  
  
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
  
 discount.xsl  
  
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
 Obiekty rozszerzeń XSLT są dodawane do <xref:System.Xml.Xsl.XsltArgumentList> przy użyciu <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> metody. Kwalifikowana nazwa i identyfikator URI przestrzeni nazw są skojarzone z obiektu rozszerzenia, w tym czasie.  
  
 Po dodaniu obiektu, obiekt wywołujący <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> musi być w pełni zaufany w zasadach zabezpieczeń. Obiekt wywołujący jest częściowo zaufany, dodanie zakończy się niepowodzeniem.  
  
 Chociaż obiekt zostanie dodany pomyślnie, nie gwarantuje to, że wykonanie zakończą się pomyślnie. Gdy <xref:System.Xml.Xsl.XslTransform.Transform%2A> metoda jest wywoływana, uprawnienia są obliczane względem dowodów przy zachowaniu <xref:System.Xml.Xsl.XslTransform.Load%2A> czasu i że zestaw uprawnień jest przypisany do procesu cały przekształcenia. Jeśli rozszerzenie obiektu próbuje zainicjować akcję, która wymaga uprawnień nie można odnaleźć w zestawie, jest zgłaszany wyjątek.  
  
 Typy danych zwróciło obiekty rozszerzeń są zestawu obejmującego cztery typy danych podstawowych XPath w numer, ciąg, wartość logiczna i węzła zestawu.  
  
#### <a name="to-use-the-xslt-extension-object-the-user-needs-to-do-the-following"></a>Aby użyć obiektu rozszerzenia XSLT, użytkownik musi wykonać następujące czynności:  
  
1. Tworzenie <xref:System.Xml.Xsl.XsltArgumentList> i dodać za pomocą obiektu rozszerzenia <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A>.  
  
2. Wywołanie obiektu rozszerzenia z arkusza stylów.  
  
3. Przekaż <xref:System.Xml.Xsl.XsltArgumentList> do <xref:System.Xml.Xsl.XslTransform.Transform%2A> metody.  
  
### <a name="example"></a>Przykład  
 W poniższym przykładzie obliczany obwód koła, biorąc pod uwagę jego usługi radius.  
  
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
  
 Circle.xsl  
  
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
