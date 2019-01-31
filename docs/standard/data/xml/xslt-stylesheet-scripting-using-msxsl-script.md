---
title: 'XSLT arkusza stylów skryptów przy użyciu < msxsl: script >'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 60e2541b-0cea-4b2e-a4fa-85f4c50f1bef
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f3abaa8115d2e52a98f0b42588860dece6361df5
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55267303"
---
# <a name="xslt-stylesheet-scripting-using-msxslscript"></a>XSLT skryptów przy użyciu arkusza stylów \<msxsl: script >
<xref:System.Xml.Xsl.XslTransform> Klasa obsługuje osadzonych skryptów przy użyciu `script` elementu.  
  
> [!NOTE]
>  <xref:System.Xml.Xsl.XslTransform> Klasy jest przestarzała w [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)]. Można przeprowadzić rozszerzalny język arkusza stylów dla przekształceń przekształcenia (XSLT) przy użyciu <xref:System.Xml.Xsl.XslCompiledTransform> klasy. Zobacz [używanie klasy XslCompiledTransform](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) i [Migrowanie z klasy XslTransform](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md) Aby uzyskać więcej informacji.  
  
 <xref:System.Xml.Xsl.XslTransform> Klasa obsługuje osadzonych skryptów przy użyciu `script` elementu. Po załadowaniu arkusza stylów, wszystkie funkcje zdefiniowane są kompilowane do języka Microsoft intermediate language (MSIL), są opakowane w definicji klasy i w wyniku mają bez utraty wydajności.  
  
 `<msxsl:script>` Jest zdefiniowany element poniżej:  
  
```xml  
<msxsl:script language = "language-name" implements-prefix = "prefix of user namespace"> </msxsl:script>  
```  
  
 gdzie `msxsl` jest prefiks, który jest powiązany z przestrzeni nazw `urn:schemas-microsoft-com:xslt`.  
  
 `language` Atrybut nie jest wymagany, ale jeśli zostanie określony, jego wartość musi być jedną z następujących czynności: C#, VB, JScript, JavaScript, VisualBasic, or CSharp. Jeśli nie zostanie określona, język domyślnie JScript. `language-name` Nie jest rozróżniana wielkość liter, więc "JavaScript" i "javascript" są równoważne.  
  
 `implements-prefix` Atrybut jest wymagany. Ten atrybut służy do deklarację przestrzeni nazw i skojarzyć go z bloku skryptu. Wartość tego atrybutu jest prefiks, który reprezentuje obszar nazw. Ta przestrzeń nazw można zdefiniować gdzieś w arkuszu stylów.  
  
 Ponieważ `msxsl:script` element należy do przestrzeni nazw `urn:schemas-microsoft-com:xslt`, arkusz stylów może zawierać deklaracji przestrzeni nazw `xmlns:msxsl=urn:schemas-microsoft-com:xslt`.  
  
 Jeśli obiekt wywołujący skryptu nie ma <xref:System.Security.Permissions.SecurityPermissionFlag> uprawnienie, dostępu, a następnie skrypt w arkuszu stylów nigdy nie zostanie skompilowany i wywołania <xref:System.Xml.Xsl.XslTransform.Load%2A> zakończy się niepowodzeniem.  
  
 Jeśli obiekt wywołujący ma `UnmanagedCode` kompiluje skrypt uprawnienia, ale operacje, które są dozwolone są zależne od dowodów, która jest dostarczana w czasie ładowania.  
  
 Jeśli używasz jednego z <xref:System.Xml.Xsl.XslTransform.Load%2A> metod, które przyjmują <xref:System.Xml.XmlReader> lub <xref:System.Xml.XPath.XPathNavigator> można załadować arkusza stylów, należy użyć <xref:System.Xml.Xsl.XslTransform.Load%2A> przeciążenia przyjmującego <xref:System.Security.Policy.Evidence> parametru jako jeden z argumentów. Aby przedstawić dowód na to, wywołujący musi mieć <xref:System.Security.Permissions.SecurityPermissionFlag> uprawnień, aby dostarczyć `Evidence` dla zestawu skryptów. Jeśli obiekt wywołujący nie ma tego uprawnienia, a następnie mogą oni ustawić `Evidence` parametr `null`. Powoduje to, że <xref:System.Xml.Xsl.XslTransform.Load%2A> funkcję, aby zakończyć się niepowodzeniem, jeśli znajdzie skryptu. `ControlEvidence` Uprawnienie jest uznawany za bardzo zaawansowane uprawnienia, które powinny być przyznawane tylko do wysoce zaufanym kodem.  
  
 Aby uzyskać dowód z zestawu, należy użyć `this.GetType().Assembly.Evidence`. Aby uzyskać dowód z jednolite zasobów identyfikator (URI), użyj `Evidence e = XmlSecureResolver.CreateEvidenceForUrl(stylesheetURI)`.  
  
 Jeśli używasz <xref:System.Xml.Xsl.XslTransform.Load%2A> metod, które przyjmują <xref:System.Xml.XmlResolver> , ale nie `Evidence`, wartością domyślną pełnego zaufania strefie zabezpieczeń dla zestawu. Aby uzyskać więcej informacji, zobacz <xref:System.Security.SecurityZone> i [nazwanych zestawów uprawnień](https://msdn.microsoft.com/library/08250d67-c99d-4ab0-8d2b-b0e12019f6e3).  
  
 Funkcje mogą być zadeklarowane w obrębie `msxsl:script` elementu. W poniższej tabeli przedstawiono przestrzenie nazw, które są obsługiwane przez domyślny. Można użyć klas spoza listy obszarów nazw. Jednak te klasy musi być w pełni kwalifikowana.  
  
|Domyślne obszary nazw|Opis|  
|------------------------|-----------------|  
|System|Klasa systemu.|  
|System.Collection|Klasy kolekcji.|  
|System.Text|Klasy tekstu.|  
|System.Text.RegularExpressions|Klasy wyrażeń regularnych.|  
|System.Xml|Podstawowe klasy XML.|  
|System.Xml.Xsl|Klasy XSLT.|  
|System.Xml.XPath|Klasy XML Path Language (XPath).|  
|Microsoft.VisualBasic|Klasy dla skryptów programu Microsoft Visual Basic.|  
  
 Gdy funkcja jest zadeklarowana, znajduje się w bloku skryptu. Arkusze stylów może zawierać wiele Bloki skryptu, każdy niezależnego innych. Oznacza to, że jeśli wykonujesz wewnątrz bloku skryptu, nie można wywołać funkcję zdefiniowaną w innego bloku skryptu, o ile nie jest zadeklarowany ma ten sam język skryptów i tej samej przestrzeni nazw. Ponieważ każdy blok skryptu może znajdować się w jego własnej języka i bloku jest analizowany zgodnie z regułami gramatyki tego analizatora języka, należy użyć składni poprawne dla języka w użyciu. Na przykład, jeśli jesteś w bloku skryptu C#, wówczas jest błąd za pomocą węzła komentarz XML `<!-- an XML comment -->` w bloku.  
  
 Podanych argumentów i wartości zwracane definicją funkcji skryptu musi być jednym z typów XPath World Wide Web Consortium (W3C) lub XSLT. W poniższej tabeli przedstawiono odpowiednie typy W3C równoważne .NET Framework klas (typ) i czy W3C, wpisz to wyrażenie XPath typu lub XSLT.  
  
|Typ|Równoważne .NET Framework klasy (typ)|Wyrażenie XPath typu lub XSLT|  
|----------|----------------------------------------------|-----------------------------|  
|String|System.String|XPath|  
|Boolean|System.Boolean|XPath|  
|Wartość liczbowa|System.Double|XPath|  
|Wynikowego fragmentu drzewa|System.Xml.XPath.XPathNavigator|XSLT|  
|Zestaw węzłów|System.Xml.XPath.XPathNodeIterator|XPath|  
  
 Jeśli funkcja skryptu korzysta z jednego z następujących typów liczbowych: Int16, UInt16, Int32, UInt32, Int64, UInt64, jednego lub dziesiętnej, jest zmuszony do dwukrotnie, która mapuje do typu number W3C XPath. Wszystkie pozostałe typy będą obowiązkowo przenoszone na ciąg przez wywołanie metody `ToString` metody.  
  
 Jeśli funkcja skryptu korzysta z typu innego niż wymienione powyżej lub jeśli funkcja nie kompiluje się kiedy arkusza stylów jest ładowany do <xref:System.Xml.Xsl.XslTransform> obiektu, jest zgłaszany wyjątek.  
  
 Korzystając z `msxsl:script` elementu, zdecydowanie zaleca się że skryptu, niezależnie od języka, można umieścić w sekcji CDATA. Na przykład następujący kody XML pokazuje szablonu sekcji CDATA, w którym znajduje się kod.  
  
```xml  
<msxsl:script implements-prefix='yourprefix' language='CSharp'>  
    <![CDATA[  
    ... your code here ...  
    ]]>  
</msxsl:script>  
```  
  
 Wysoce zalecane jest aby cała zawartość skryptu były umieszczane w sekcji CDATA, ponieważ operatory, identyfikatory lub ograniczniki dla danego języka ma potencjał jest błędnie zinterpretowana jako XML. Poniższy przykład pokazuje użycie operatora logicznego AND w skrypcie.  
  
```xml  
<msxsl:script implements-prefix='yourprefix' language='CSharp'>  
    public string book(string abc, string xyz)  
    {  
        if ((abc == bar) && (abc == xyz)) return bar + xyz;  
        else return null;  
    }  
</msxsl:script>  
```  
  
 Zgłasza wyjątek, ponieważ takie znaki nie będą miały zmienione znaczenie. Dokument jest ładowany w formacie XML, a nie szczególne traktowanie jest stosowany do tekstu między `msxsl:script` tagi elementów.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto osadzonych skryptów do obliczania obwód koła, biorąc pod uwagę jego usługi radius.  
  
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
  
   public static void Main()  
   {  
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
     public double circumference(double radius)  
     {  
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
  
## <a name="see-also"></a>Zobacz także

- [Implementowanie procesora XSLT przy użyciu klasy XslTransform](../../../../docs/standard/data/xml/xsltransform-class-implements-the-xslt-processor.md)
