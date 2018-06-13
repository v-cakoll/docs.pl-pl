---
title: XSLT skryptów przy użyciu arkusza stylów &lt;msxsl:script&gt;
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 60e2541b-0cea-4b2e-a4fa-85f4c50f1bef
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5b1fb13e33f759c44e090a9294548c224e10344e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33577179"
---
# <a name="xslt-stylesheet-scripting-using-ltmsxslscriptgt"></a>XSLT skryptów przy użyciu arkusza stylów &lt;msxsl:script&gt;
<xref:System.Xml.Xsl.XslTransform> Klasa obsługuje osadzonych skryptów przy użyciu `script` elementu.  
  
> [!NOTE]
>  <xref:System.Xml.Xsl.XslTransform> Klasa jest przestarzała w [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)]. Może wykonywać rozszerzalny język arkusza stylów dla transformacji przekształcenia XSLT () przy użyciu <xref:System.Xml.Xsl.XslCompiledTransform> klasy. Zobacz [za pomocą klasy XslCompiledTransform](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) i [migracji z klasy XslTransform](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md) Aby uzyskać więcej informacji.  
  
 <xref:System.Xml.Xsl.XslTransform> Klasa obsługuje osadzonych skryptów przy użyciu `script` elementu. Po załadowaniu arkusza stylów żadnych określonych funkcji są kompilowane na język pośredni firmy Microsoft (MSIL) przez są ujęte w definicji klasy i w związku z tym mieć bez utraty wydajności.  
  
 `<msxsl:script>` Jest zdefiniowany element poniżej:  
  
```xml  
<msxsl:script language = "language-name" implements-prefix = "prefix of user namespace"> </msxsl:script>  
```  
  
 gdzie `msxsl` jest powiązany z przestrzenią nazw prefiks `urn:schemas-microsoft-com:xslt`.  
  
 `language` Atrybut nie jest to konieczne, ale jeśli jest określony, jego wartość musi być jedną z następujących: C#, VB, JScript, JavaScript, VisualBasic lub CSharp. Jeśli nie określono język domyślnie JScript. `language-name` Nie jest rozróżniana wielkość liter, więc "JavaScript" i "javascript" są równoważne.  
  
 `implements-prefix` Atrybut jest obowiązkowy. Ten atrybut służy do zadeklarować przestrzeni nazw i powiązać ją z bloku skryptu. Wartość tego atrybutu jest prefiks, który reprezentuje obszar nazw. Ta przestrzeń nazw można zdefiniować gdzieś w arkuszu stylów.  
  
 Ponieważ `msxsl:script` element należy do przestrzeni nazw `urn:schemas-microsoft-com:xslt`, arkusz stylów musi zawierać deklaracji przestrzeni nazw `xmlns:msxsl=urn:schemas-microsoft-com:xslt`.  
  
 Jeśli element wywołujący skryptu nie ma <xref:System.Security.Permissions.SecurityPermissionFlag> uprawnienie, dostępu, a następnie skryptu w arkuszu stylów nigdy nie zostanie skompilowany i wywołania w celu <xref:System.Xml.Xsl.XslTransform.Load%2A> zakończy się niepowodzeniem.  
  
 Jeśli element wywołujący ma `UnmanagedCode` kompiluje skrypt uprawnień, ale operacje, które są dozwolone są zależne od dowód, że podano w czasie ładowania.  
  
 Jeśli używasz jednego z <xref:System.Xml.Xsl.XslTransform.Load%2A> metod, które przyjmują <xref:System.Xml.XmlReader> lub <xref:System.Xml.XPath.XPathNavigator> załadować arkusza stylów, należy użyć <xref:System.Xml.Xsl.XslTransform.Load%2A> przeciążenia, które przyjmuje <xref:System.Security.Policy.Evidence> parametru jako jeden z jego argumentów. Aby udowodnić, wywołujący musi mieć <xref:System.Security.Permissions.SecurityPermissionFlag> uprawnienia do dostarczania `Evidence` dla zestawu skryptu. Jeśli element wywołujący nie ma to uprawnienie, a następnie ich można ustawić `Evidence` parametr `null`. Powoduje to <xref:System.Xml.Xsl.XslTransform.Load%2A> funkcji, aby zakończyć się niepowodzeniem w przypadku odnalezienia skryptu. `ControlEvidence` Uprawnienie jest uznawany za bardzo zaawansowane uprawnienia, które powinno być przyznane wyłącznie do kodu wysoce zaufanych.  
  
 Aby uzyskać dowody z tym zestawem, należy użyć `this.GetType().Assembly.Evidence`. Aby uzyskać dowody z zasobów identyfikator URI (Uniform), należy użyć `Evidence e = XmlSecureResolver.CreateEvidenceForUrl(stylesheetURI)`.  
  
 Jeśli używasz <xref:System.Xml.Xsl.XslTransform.Load%2A> metod, które przyjmują <xref:System.Xml.XmlResolver> , lecz nie `Evidence`, wartością domyślną pełnego zaufania strefy zabezpieczeń dla zestawu. Aby uzyskać więcej informacji, zobacz <xref:System.Security.SecurityZone> i [nazwane zestawy uprawnień](https://msdn.microsoft.com/library/08250d67-c99d-4ab0-8d2b-b0e12019f6e3).  
  
 Funkcje mogą być deklarowane w `msxsl:script` elementu. W poniższej tabeli przedstawiono przestrzenie nazw, które są obsługiwane domyślnie. Można użyć klasy spoza listy przestrzeni nazw. Jednak te klasy musi być w pełni kwalifikowana.  
  
|Domyślne obszary nazw|Opis|  
|------------------------|-----------------|  
|System|Klasa systemu.|  
|System.Collection|Klasy kolekcji.|  
|System.Text|Klasy tekstu.|  
|System.Text.RegularExpressions|Klasy wyrażeń regularnych.|  
|System.Xml|Podstawowe klasy XML.|  
|System.Xml.Xsl|Klasy XSLT.|  
|System.Xml.XPath|Klasy XML Path Language (XPath).|  
|Microsoft.VisualBasic|Klasy dla skryptów Microsoft Visual Basic.|  
  
 Funkcja została zadeklarowana, jest zawarty w bloku skryptu. Arkusze stylów może zawierać wiele bloków skryptu, każdy działające niezależnie od innych. Oznacza to, że jeśli wykonujesz kompilację w bloku skryptu nie można wywołać funkcję zdefiniowaną w innego bloku skryptu, chyba że jest on zadeklarowany jako do tego samego obszaru nazw i tego samego języka skryptów. Ponieważ każdy blok skryptu może znajdować się w jego własnej języka i blok jest analizowana zgodnie z regułami gramatyki tego analizatora składni języka, należy użyć składni poprawne dla języka w użyciu. Na przykład, jeśli w bloku skryptu C#, następnie jest błędem węzłem komentarza XML `<!-- an XML comment -->` w bloku.  
  
 Podanych argumentów i zwracanych wartości zdefiniowane przez funkcje skryptu musi być jednego z typów XPath w sieci World Wide Web konsorcjum W3C lub XSLT. W poniższej tabeli przedstawiono odpowiednie typy W3C równoważne .NET Framework klas (typ) i czy W3C typem jest typ XPath lub XSLT.  
  
|Typ|Odpowiednik .NET Framework klasy (typ)|Typ wyrażenia XPath lub XSLT|  
|----------|----------------------------------------------|-----------------------------|  
|String|System.String|XPath|  
|Boolean|System.Boolean|XPath|  
|Wartość liczbowa|System.Double|XPath|  
|Wynikowego fragmentu drzewa|System.Xml.XPath.XPathNavigator|XSLT|  
|Zestaw węzłów|System.Xml.XPath.XPathNodeIterator|XPath|  
  
 Jeśli funkcja skryptu korzysta z jednego z następujących typów numerycznych: Int16, UInt16, Int32, UInt32, Int64, UInt64, jednym lub Decimal, są one wymuszono dwukrotnie, która mapuje numer typu W3C XPath. Wszystkie inne typy będą obowiązkowo przenoszone na ciąg przez wywołanie metody `ToString` metody.  
  
 Jeśli funkcja skryptu wykorzystuje ona typu innego niż wymienione powyżej, lub jeśli funkcja nie kompiluje się po arkusza stylów jest ładowany do <xref:System.Xml.Xsl.XslTransform> obiektu, jest zgłaszany wyjątek.  
  
 Korzystając z `msxsl:script` elementu, zdecydowanie zaleca się umieszczanie skryptu, niezależnie od języka, wewnątrz sekcji CDATA. Na przykład następujący kod XML zawiera szablon sekcji CDATA, w którym znajduje się kod.  
  
```xml  
<msxsl:script implements-prefix='yourprefix' language='CSharp'>  
    <![CDATA[  
    ... your code here ...  
    ]]>  
</msxsl:script>  
```  
  
 Zdecydowanie zaleca się umieszczanie całą zawartość skryptu w sekcji CDATA, ponieważ operatorów, identyfikatory lub ograniczniki dla danego języka mogą potencjalnie jest błędnie zinterpretowane w formacie XML. Poniższy przykład przedstawia użycie operatora logicznego AND w skrypcie.  
  
```xml  
<msxsl:script implements-prefix='yourprefix' language='CSharp>  
    public string book(string abc, string xyz)  
    {  if ((abc== abc)&&(abc== xyz)) return bar+xyz;  
        else return null;  
    }  
</msxsl:script>  
```  
  
 Zgłasza wyjątek, ponieważ takie znaki nie będą miały zmienione znaczenie. Dokument jest ładowany w formacie XML, a nie szczególnego traktowania jest stosowany do tekstu między `msxsl:script` znaczniki elementów.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto osadzony skrypt, aby obliczyć obwód koła podane jego radius.  
  
```vb  
Imports System  
Imports System.IO  
Imports System.Xml  
Imports System.Xml.XPath  
Imports System.Xml.Xsl  
  
Public Class Sample  
  
   Private Const filename As String = "number.xml"  
   Private Const stylesheet As String = "calc.xsl"  
  
   Public Shared Sub Main()  
  
    'Create the XslTransform and load the style sheet.  
    Dim xslt As XslTransform = New XslTransform  
    xslt.Load(stylesheet)  
  
    'Load the XML data file.  
    Dim doc As XPathDocument = New XPathDocument(filename)  
  
    'Create an XmlTextWriter to output to the console.               
    Dim writer As XmlTextWriter = New XmlTextWriter(Console.Out)  
    writer.Formatting = Formatting.Indented  
  
    'Transform the file.  
    xslt.Transform(doc, Nothing, writer, Nothing)  
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
   private const String filename = "number.xml";  
   private const String stylesheet = "calc.xsl";  
  
   public static void Main() {  
  
    //Create the XslTransform and load the style sheet.  
    XslTransform xslt = new XslTransform();  
    xslt.Load(stylesheet);  
  
    //Load the XML data file.  
    XPathDocument doc = new XPathDocument(filename);  
  
    //Create an XmlTextWriter to output to the console.               
    XmlTextWriter writer = new XmlTextWriter(Console.Out);  
    writer.Formatting = Formatting.Indented;  
  
    //Transform the file.  
    xslt.Transform(doc, null, writer, null);  
    writer.Close();  
  }   
}  
```  
  
## <a name="input"></a>Dane wejściowe  
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
  
 calc.xsl  
  
```xml  
<xsl:stylesheet version="1.0" xmlns:xsl="http://www.w3.org/1999/XSL/Transform"  
    xmlns:msxsl="urn:schemas-microsoft-com:xslt"  
    xmlns:user="urn:my-scripts">  
  
  <msxsl:script language="C#" implements-prefix="user">  
     <![CDATA[  
     public double circumference(double radius){  
       double pi = 3.14;  
       double circ = pi*radius*2;  
       return circ;  
     }  
      ]]>  
   </msxsl:script>  
  
  <xsl:template match="data">    
  <circles>  
  
  <xsl:for-each select="circle">  
    <circle>  
    <xsl:copy-of select="node()"/>  
       <circumference>  
          <xsl:value-of select="user:circumference(radius)"/>   
       </circumference>  
    </circle>  
  </xsl:for-each>  
  </circles>  
  </xsl:template>  
</xsl:stylesheet>  
```  
  
## <a name="output"></a>Dane wyjściowe  
  
```xml  
<circles xmlns:msxsl="urn:schemas-microsoft-com:xslt" xmlns:user="urn:my-scripts">  
  <circle>  
    <radius>12</radius>  
    <circumference>75.36</circumference>  
  </circle>  
  <circle>  
    <radius>37.5</radius>  
    <circumference>235.5</circumference>  
  </circle>  
</circles>    
```  
  
## <a name="see-also"></a>Zobacz też  
 [Implementowanie procesora XSLT przy użyciu klasy XslTransform](../../../../docs/standard/data/xml/xsltransform-class-implements-the-xslt-processor.md)
