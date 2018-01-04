---
title: "XsltArgumentList parametry arkusza stylów i rozszerzenia obiektów"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: de2f0dce-6b98-4908-bba7-ed150cc50355
caps.latest.revision: "3"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: b14365266d5a477b32dbbe177d9644596b9e3b38
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="xsltargumentlist-for-style-sheet-parameters-and-extension-objects"></a>XsltArgumentList parametry arkusza stylów i rozszerzenia obiektów
<xref:System.Xml.Xsl.XsltArgumentList> Klasa zawiera Extensible Stylesheet Language parametrów przekształcenia XSLT (), a obiekty rozszerzenia XSLT. Gdy dane są przekazywane do <xref:System.Xml.Xsl.XslTransform.Transform%2A> metody te parametry i rozszerzenia obiekty mogą być wywoływane z arkuszy stylów.  
  
> [!NOTE]
>  <xref:System.Xml.Xsl.XslTransform> i <xref:System.Xml.Xsl.XsltArgumentList> klas są nieaktualne w [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)]. Można wykonać przekształcenia XSLT przy użyciu <xref:System.Xml.Xsl.XslCompiledTransform> klasy. Zobacz [za pomocą klasy XslCompiledTransform](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) i [migracji z klasy XslTransform](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md) Aby uzyskać więcej informacji.  
  
 <xref:System.Xml.Xsl.XsltArgumentList> Klasa zawiera parametry XSLT i obiekty rozszerzenia XSLT. Gdy dane są przekazywane do <xref:System.Xml.Xsl.XslTransform.Transform%2A> metody te parametry i rozszerzenia obiekty mogą być wywoływane z arkuszy stylów.  
  
 Poniżej przedstawiono zalety przekazanie obiektu, a nie za pomocą osadzony skrypt:  
  
-   Zapewnia lepszą hermetyzacji i ponowne użycie klasy.  
  
-   Umożliwia arkusze stylów mniejsze i łatwiejsze do utrzymania.  
  
-   Obsługiwane obsługuje wywoływania metod w klasach należące do przestrzeni nazw innych niż te zdefiniowane w zestawie <xref:System> przestrzeni nazw.  
  
-   Obsługuje przekazywanie wynik fragmenty drzewa do arkusza stylów przy użyciu <xref:System.Xml.XPath.XPathNodeIterator>.  
  
## <a name="xslt-style-sheet-parameters"></a>Parametry arkusz stylów XSLT  
 Parametry XSLT są dodawane do <xref:System.Xml.Xsl.XsltArgumentList> przy użyciu <xref:System.Xml.Xsl.XsltArgumentList.AddParam%2A> metody. Kwalifikowana nazwa i identyfikator URI (Uniform Resource) przestrzeni nazw są skojarzone z obiektem parametru o tej godzinie.  
  
 Obiektu parameter powinna być zgodna z typem sieci World Wide Web konsorcjum W3C. W poniższej tabeli przedstawiono odpowiednie typy W3C odpowiednikiem [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] klasy (typ), oraz czy typ W3C jest typu XML Path Language (XPath) lub XSLT.  
  
|Typ W3C|Równoważne klasy .NET Framework (typ)|Typ wyrażenia XPath lub XSLT|  
|--------------|----------------------------------------------|-----------------------------|  
|String|System.String|XPath|  
|Boolean|System.Boolean|XPath|  
|Wartość liczbowa|System.Double|XPath|  
|Wynikowego fragmentu drzewa|System.Xml.XPath.XPathNavigator|XSLT|  
|Zestaw węzłów|System.Xml.XPath.XPathNodeIterator|XPath|  
  
 Jeśli parametr obiektu nie jest jednym z powyższych klas, jest wymuszone o podwójnej precyzji lub ciąg, zależnie od potrzeb. Typy Int16, UInt16, Int32, UInt32, Int64, UInt64, Single i dziesiętnych będą obowiązkowo przenoszone na wartość o podwójnej precyzji. Wszystkie inne typy będą obowiązkowo przenoszone na ciąg przy użyciu `ToString` metody.  
  
#### <a name="to-use-the-xslt-parameter-the-user-needs-to-do-the-following"></a>Aby użyć parametru XSLT, użytkownik musi wykonać następujące czynności:  
  
1.  Utwórz <xref:System.Xml.Xsl.XsltArgumentList> i dodawanie obiektów przy użyciu <xref:System.Xml.Xsl.XsltArgumentList.AddParam%2A>.  
  
2.  Wywołania parametry z arkusza stylów.  
  
3.  Przekaż <xref:System.Xml.Xsl.XsltArgumentList> do <xref:System.Xml.Xsl.XslTransform.Transform%2A> metody.  
  
### <a name="example"></a>Przykład  
 W poniższym przykładzie użyto <xref:System.Xml.Xsl.XsltArgumentList.AddParam%2A> metodę w celu utworzenia parametru do przechowywania Data obliczony rabat. Data rabatu jest obliczany 20 dni od daty zamówienia.  
  
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
 ORDER.XML  
  
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
  
## <a name="xslt-extension-objects"></a>Obiekty rozszerzenia XSLT  
 Obiekty rozszerzenia XSLT są dodawane do <xref:System.Xml.Xsl.XsltArgumentList> przy użyciu <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> metody. Kwalifikowana nazwa i identyfikator URI przestrzeni nazw są skojarzone z obiektem rozszerzenia o tej godzinie.  
  
 Po dodaniu obiektu, wywołujący <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> musi być w pełni zaufany w zasadach zabezpieczeń. Jeśli element wywołujący jest częściowo zaufany, dodanie zakończy się niepowodzeniem.  
  
 Gdy obiekt zostanie dodany pomyślnie, nie gwarantuje to, że wykonywanie zakończy się pomyślnie. Gdy <xref:System.Xml.Xsl.XslTransform.Transform%2A> metoda jest wywoływana, uprawnienia są obliczane względem dowodów na <xref:System.Xml.Xsl.XslTransform.Load%2A> czasu, oraz że zestaw uprawnień jest przypisane do przekształcania całego procesu. Jeśli obiekt rozszerzeń próbuje zainicjować akcję, która wymaga uprawnień nie znaleziono w zestawie, jest zwracany wyjątek.  
  
 Typy danych zwracane z obiektów rozszerzeń są jednym z czterech podstawowych XPath typy danych numer, string, Boolean i węzła zestawu.  
  
#### <a name="to-use-the-xslt-extension-object-the-user-needs-to-do-the-following"></a>Aby użyć obiektu rozszerzenia XSLT, użytkownik musi wykonać następujące czynności:  
  
1.  Utwórz <xref:System.Xml.Xsl.XsltArgumentList> i dodać za pomocą obiektu rozszerzenia <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A>.  
  
2.  Wywołanie obiektu rozszerzenia z arkusza stylów.  
  
3.  Przekaż <xref:System.Xml.Xsl.XsltArgumentList> do <xref:System.Xml.Xsl.XslTransform.Transform%2A> metody.  
  
### <a name="example"></a>Przykład  
 W poniższym przykładzie oblicza obwód koła podane jego radius.  
  
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
  public class Calculate{  
  
    private double circ = 0;  
  
    public double Circumference(double radius){  
       circ = Math.PI*2*radius;  
       return circ;  
    }  
  }  
}  
```  
  
### <a name="input"></a>Dane wejściowe  
 Number.XML  
  
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
  
## <a name="see-also"></a>Zobacz też  
 [Implementowanie procesora XSLT przy użyciu klasy XslTransform](../../../../docs/standard/data/xml/xsltransform-class-implements-the-xslt-processor.md)
