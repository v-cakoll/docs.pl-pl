---
title: Wykonywanie skryptów arkusza stylów XSLT przy użyciu elementu <msxsl:script>
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 60e2541b-0cea-4b2e-a4fa-85f4c50f1bef
ms.openlocfilehash: 9bf57e0f74a353fb6512a24214e9479c1d813aab
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2020
ms.locfileid: "78160212"
---
# <a name="xslt-stylesheet-scripting-using-msxslscript"></a>Obsługa skryptów arkusza stylów \<XSLT przy użyciu msxsl:> skryptu
<xref:System.Xml.Xsl.XslTransform> Klasa obsługuje osadzone skrypty przy użyciu `script` elementu.  
  
> [!NOTE]
> <xref:System.Xml.Xsl.XslTransform> Klasa jest przestarzała w .NET Framework 2,0. Można wykonać przekształcenia Extensible Stylesheet Language for Transformations (XSLT) przy użyciu <xref:System.Xml.Xsl.XslCompiledTransform> klasy. Aby uzyskać więcej informacji, zobacz [Używanie klasy XslCompiledTransform](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) i [Migrowanie z klasy XslTransform](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md) .  
  
 <xref:System.Xml.Xsl.XslTransform> Klasa obsługuje osadzone skrypty przy użyciu `script` elementu. Po załadowaniu arkusza stylów wszystkie zdefiniowane funkcje są kompilowane do języka pośredniego firmy Microsoft (MSIL) przez zawinięte w definicji klasy i nie mają utraty wydajności w wyniku.  
  
 `<msxsl:script>` Element jest zdefiniowany poniżej:  
  
```xml  
<msxsl:script language = "language-name" implements-prefix = "prefix of user namespace"> </msxsl:script>  
```  
  
 gdzie `msxsl` jest prefiksem powiązanym z `urn:schemas-microsoft-com:xslt`przestrzenią nazw.  
  
 `language` Atrybut nie jest obowiązkowy, ale jeśli jest określony, jego wartość musi być jedną `C#`z następujących:, `VB`, `JScript` `JavaScript` `VisualBasic`,, lub. `CSharp` Jeśli nie zostanie określony, język jest wartością domyślną języka JScript. Nie `language-name` jest rozróżniana wielkość liter, dlatego "JavaScript" i "JavaScript" są równoważne.  
  
 Ten `implements-prefix` atrybut jest obowiązkowy. Ten atrybut służy do deklarowania przestrzeni nazw i kojarzenia jej z blokiem skryptu. Wartość tego atrybutu jest prefiks, który reprezentuje obszar nazw. Ta przestrzeń nazw może być zdefiniowana gdzieś w arkuszu stylów.  
  
 Ponieważ `msxsl:script` element należy do przestrzeni nazw `urn:schemas-microsoft-com:xslt`, arkusz stylów musi zawierać deklarację `xmlns:msxsl=urn:schemas-microsoft-com:xslt`przestrzeni nazw.  
  
 Jeśli obiekt wywołujący skrypt nie ma <xref:System.Security.Permissions.SecurityPermissionFlag> uprawnień dostępu, wówczas skrypt w arkuszu stylów nigdy nie zostanie skompilowany i wywołanie do <xref:System.Xml.Xsl.XslTransform.Load%2A> nie powiedzie się.  
  
 Jeśli obiekt wywołujący `UnmanagedCode` ma uprawnienie, skrypt kompiluje, ale dozwolone operacje są zależne od dowodów dostarczonych w czasie ładowania.  
  
 Jeśli <xref:System.Xml.Xsl.XslTransform.Load%2A> używasz jednej z metod, które pobierają <xref:System.Xml.XmlReader> lub <xref:System.Xml.XPath.XPathNavigator> ładują arkusz stylów, musisz użyć <xref:System.Xml.Xsl.XslTransform.Load%2A> przeciążenia, które przyjmuje <xref:System.Security.Policy.Evidence> parametr jako jeden z argumentów. Aby zapewnić dowód, obiekt wywołujący musi <xref:System.Security.Permissions.SecurityPermissionFlag> mieć uprawnienia do `Evidence` dostawy zestawu skryptu. Jeśli obiekt wywołujący nie ma tego uprawnienia, można ustawić `Evidence` parametr na. `null` Powoduje to, <xref:System.Xml.Xsl.XslTransform.Load%2A> że funkcja kończy się niepowodzeniem, jeśli znajdzie skrypt. `ControlEvidence` Uprawnienie jest uznawane za bardzo zaawansowane uprawnienia, które powinny być przyznawane tylko do wysoce zaufanego kodu.  
  
 Aby uzyskać dowody z Twojego zestawu, użyj `this.GetType().Assembly.Evidence`. Aby uzyskać dowód z Uniform Resource Identifier (URI), użyj `Evidence e = XmlSecureResolver.CreateEvidenceForUrl(stylesheetURI)`.  
  
 W przypadku korzystania <xref:System.Xml.Xsl.XslTransform.Load%2A> z metod, które <xref:System.Xml.XmlResolver> pobierają `Evidence`, ale nie, Strefa zabezpieczeń dla zestawu domyślnie ma wartość pełne zaufanie. Aby uzyskać więcej informacji, <xref:System.Security.SecurityZone> Zobacz i [nazwane zestawy uprawnień](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/4652tyx7(v=vs.100)).  
  
 Funkcje mogą być deklarowane w `msxsl:script` obrębie elementu. W poniższej tabeli przedstawiono przestrzenie nazw, które są obsługiwane domyślnie. Można używać klas poza wymienionymi obszarami nazw. Jednak te klasy muszą być w pełni kwalifikowane.  
  
|Domyślne przestrzenie nazw|Opis|  
|------------------------|-----------------|  
|System|Klasy systemowej.|  
|System.Collection|Klasy kolekcji.|  
|System.Text|Klasy tekstowe.|  
|System.Text.RegularExpressions|Klasy wyrażeń regularnych.|  
|System.Xml|Podstawowe klasy XML.|  
|System. XML. xsl|Klasy XSLT.|  
|System.Xml.XPath|Klasy języka XML Path Language (XPath).|  
|Microsoft. VisualBasic|Klasy dla skryptów Visual Basic firmy Microsoft.|  
  
 Gdy funkcja jest zadeklarowana, jest zawarta w bloku skryptu. Arkusze stylów mogą zawierać wiele bloków skryptu, z których każda działa niezależnie od siebie. Oznacza to, że jeśli wykonujesz wewnątrz bloku skryptu, nie można wywołać funkcji, która została zdefiniowana w innym bloku skryptu, chyba że jest zadeklarowana jako ma tę samą przestrzeń nazw i ten sam język skryptowy. Ponieważ każdy blok skryptu może znajdować się w własnym języku, a blok jest analizowany zgodnie z regułami gramatyki tego parsera języka, należy użyć poprawnej składni dla używanego języka. Na przykład, jeśli jesteś w bloku skryptu języka C#, jest to błąd, aby użyć węzła `<!-- an XML comment -->` komentarza XML w bloku.  
  
 Podane argumenty i zwracane wartości zdefiniowane przez funkcje skryptów muszą być jednym z typów XPath lub XSLT organizacja World Wide Web Consortium (W3C). W poniższej tabeli przedstawiono odpowiednie typy W3C, równoważne klasy .NET Framework (typ) i określające, czy typ W3C jest typem XPath czy XSLT.  
  
|Typ|Równoważna Klasa .NET Framework (typ)|Typ XPath lub typ XSLT|  
|----------|----------------------------------------------|-----------------------------|  
|Ciąg|System. String|XPath|  
|Wartość logiczna|System. Boolean|XPath|  
|Liczba|System. Double|XPath|  
|Fragment drzewa wyników|System. XML. XPath. XPathNavigator|XSL|  
|Zestaw węzłów|System. XML. XPath. XPathNodeIterator|XPath|  
  
 Jeśli funkcja skryptu używa jednego z następujących typów liczbowych: Int16, UInt16, Int32, UInt32, Int64, UInt64, Single lub decimal, są one wymuszane jako podwójne, które mapuje do typu W3C XPath. Wszystkie inne typy są wymuszane jako ciąg przez wywołanie `ToString` metody.  
  
 Jeśli funkcja skryptu używa typu innego niż wymienione powyżej, lub jeśli funkcja nie kompiluje się, gdy arkusz stylów jest ładowany do <xref:System.Xml.Xsl.XslTransform> obiektu, zgłaszany jest wyjątek.  
  
 W przypadku korzystania `msxsl:script` z elementu zdecydowanie zaleca się, aby skrypt niezależnie od języka został umieszczony wewnątrz sekcji CDATA. Na przykład, poniższy kod XML pokazuje szablon sekcji CDATA, w której umieszczony jest swój plik.  
  
```xml  
<msxsl:script implements-prefix='yourprefix' language='CSharp'>  
    <![CDATA[  
    ... your code here ...  
    ]]>  
</msxsl:script>  
```  
  
 Zdecydowanie zaleca się, aby cała zawartość skryptu była umieszczana w sekcji CDATA, ponieważ operatory, identyfikatory lub ograniczniki danego języka mają potencjalną interpretację jako XML. W poniższym przykładzie pokazano użycie operatora logicznego AND w skrypcie.  
  
```xml  
<msxsl:script implements-prefix='yourprefix' language='CSharp'>  
    public string book(string abc, string xyz)  
    {  
        if ((abc == bar) && (abc == xyz)) return bar + xyz;  
        else return null;  
    }  
</msxsl:script>  
```  
  
 Zgłasza wyjątek, ponieważ znaki handlowe nie są wyprowadzane. Dokument jest ładowany jako XML i nie jest stosowane żadne specjalne traktowanie do tekstu między tagami `msxsl:script` elementów.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie zastosowano osadzony skrypt do obliczenia obwodu okręgu, który ma swój promień.  
  
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
 Number. XML  
  
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
  
 calc. xsl  
  
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
  
## <a name="see-also"></a>Zobacz też

- [Implementowanie procesora XSLT przy użyciu klasy XslTransform](../../../../docs/standard/data/xml/xsltransform-class-implements-the-xslt-processor.md)
