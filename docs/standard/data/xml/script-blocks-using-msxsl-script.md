---
title: Msxsl:script bloki za pomocą skryptu
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: fde6f43f-c594-486f-abcb-2211197fae20
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 23961caa7b307df46b20b3811d0883d4c702a357
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="script-blocks-using-msxslscript"></a>Msxsl:script bloki za pomocą skryptu
<xref:System.Xml.Xsl.XslCompiledTransform> Klasa obsługuje osadzonych skryptów przy użyciu `msxsl:script` elementu. Po załadowaniu arkusza stylów żadnych określonych funkcji są kompilowane na język pośredni firmy Microsoft (MSIL) przez kod Document Object Model (CodeDOM) i są wykonywane w czasie wykonywania. Zestaw wygenerowane z bloku osadzony skrypt jest oddzielony niż zestaw wygenerowany dla arkusza stylów.  
  
## <a name="enable-xslt-script"></a>Włącz skryptów XSLT  
 Obsługa osadzonych skryptów jest ustawienie opcjonalne XSLT na <xref:System.Xml.Xsl.XslCompiledTransform> klasy. Obsługa skryptów jest domyślnie wyłączona. Aby włączyć obsługę skryptów, należy utworzyć <xref:System.Xml.Xsl.XsltSettings> obiekt z <xref:System.Xml.Xsl.XsltSettings.EnableScript%2A> ustawioną właściwość `true` i przekaż obiekt do <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> metody.  
  
> [!NOTE]
>  Powinna być włączona obsługa skryptów XSLT, tylko wtedy, gdy wymagana jest obsługa skryptów, podczas pracy w pełni zaufanym środowisku.  
  
## <a name="msxslscript-element-definition"></a>msxsl:Script definicji elementu  
 `msxsl:script` Element to rozszerzenie Microsoft zalecenie XSLT 1.0 i ma następujące definicje:  
  
```xml  
<msxsl:script language = "language-name" implements-prefix = "prefix of user namespace"> </msxsl:script>  
```  
  
 `msxsl` Prefiks jest powiązany `urn:schemas-microsoft-com:xslt` identyfikator URI przestrzeni nazw. Arkusz stylów musi zawierać `xmlns:msxsl=urn:schemas-microsoft-com:xslt` deklaracji przestrzeni nazw.  
  
 `language` Atrybutu jest opcjonalny. Jego wartość wynosi języka kodu bloku osadzonego kodu. Język jest mapowany na odpowiednią CodeDOM kompilatora za pomocą <xref:System.CodeDom.Compiler.CodeDomProvider.CreateProvider%2A?displayProperty=nameWithType> metody. <xref:System.Xml.Xsl.XslCompiledTransform> Klasa może obsługiwać żadnego języka Microsoft .NET, przy założeniu odpowiedniego dostawcę jest zainstalowany na maszynie i jest zarejestrowany w sekcji system.codedom w pliku machine.config. Jeśli `language` atrybut nie jest określony, domyślnie języka JScript. Nazwa języka nie jest rozróżniana wielkość liter, więc "JavaScript" i "javascript" są równoważne.  
  
 `implements-prefix` Atrybut jest obowiązkowy. Ten atrybut służy do zadeklarować przestrzeni nazw i powiązać ją z bloku skryptu. Wartość tego atrybutu jest prefiks, który reprezentuje obszar nazw. Ten prefiks można zdefiniować gdzieś w arkuszu stylów.  
  
> [!NOTE]
>  Korzystając z `msxsl:script` elementu, zdecydowanie zaleca się umieszczanie skryptu, niezależnie od języka, wewnątrz sekcji CDATA. Skrypt może zawierać operatorów, identyfikatory lub ograniczniki dla danego języka, jeśli nie znajduje się w sekcji CDATA, ma możliwość potencjalnego jest nieprawidłowo interpretowane jako XML. Następujący kod XML zawiera szablon sekcji CDATA rozmieszczenia kodu.  
  
```xml  
<msxsl:script implements-prefix='your-prefix' language='CSharp'>  
<![CDATA[  
// Code block.  
]]>  
</msxsl:script>  
```  
  
## <a name="script-functions"></a>Funkcje skryptu  
 Funkcje mogą być deklarowane w `msxsl:script` elementu. Funkcja została zadeklarowana, jest zawarty w bloku skryptu. Arkusze stylów może zawierać wiele bloków skryptu, każdy działające niezależnie od innych. Oznacza to, że jeśli wykonujesz kompilację w bloku skryptu nie można wywołać funkcję zdefiniowaną w innego bloku skryptu, chyba że jest on zadeklarowany jako do tego samego obszaru nazw i tego samego języka skryptów. Ponieważ każdy blok skryptu może znajdować się w jego własnej języka i analizowania bloku zgodnie z regułami gramatyki tego analizatora składni języka zalecane jest użycie prawidłowa składnia języka w użyciu. Na przykład jeśli w bloku skryptu języka Microsoft C#, należy użyć składni komentarz C#.  
  
 Podanych argumentów i wartości zwracane funkcji mogą być dowolnego typu. Ponieważ typy W3C XPath są podzbiorem popularnych typów języka wspólnego (CLR), konwersja typu odbywa się na typy, które nie są uznawane za typ XPath. W poniższej tabeli przedstawiono odpowiednie typy W3C i odpowiednik typu CLR.  
  
|Typ W3C|Typ CLR|  
|--------------|--------------|  
|`String`|<xref:System.String>|  
|`Boolean`|<xref:System.Boolean>|  
|`Number`|<xref:System.Double>|  
|`Result Tree Fragment`|<xref:System.Xml.XPath.XPathNavigator>|  
|`Node Set`|<xref:System.Xml.XPath.XPathNodeIterator>|  
  
 Numeryczne typy CLR są konwertowane na <xref:System.Double>. <xref:System.DateTime> Typu jest konwertowana na <xref:System.String>. <xref:System.Xml.XPath.IXPathNavigable> typy są konwertowane na <xref:System.Xml.XPath.XPathNavigator>. **Element XPathNavigator []** jest konwertowana na <xref:System.Xml.XPath.XPathNodeIterator>.  
  
 Wszystkie inne typy Zgłoś błąd.  
  
### <a name="importing-namespaces-and-assemblies"></a>Importowanie obszary nazw i zestawów  
 <xref:System.Xml.Xsl.XslCompiledTransform> Klasy powoduje wstępne definiowanie zestaw zestawy i przestrzenie nazw, które są obsługiwane przez domyślnie `msxsl:script` elementu. Można jednak użyć klas i członków należące do przestrzeni nazw, która nie znajduje się na liście wstępnie zdefiniowanych przez zaimportowanie zestawu i przestrzeni nazw w `msxsl:script` bloku.  
  
#### <a name="assemblies"></a>Zestawy  
 Domyślnie odwołują się następujące dwa zestawy:  
  
-   PLik System.dll  
  
-   System.Xml.dll  
  
-   Pliku Microsoft.VisualBasic.dll (po język skryptu VB)  
  
 Można zaimportować następującej liczby dodatkowych zestawów przy użyciu `msxsl:assembly` elementu. Gdy arkusz stylów jest kompilowany w tym zestawie. `msxsl:assembly` Element ma następującą definicję:  
  
```xml  
<msxsl:script>  
  <msxsl:assembly name="system.assemblyName" />  
  <msxsl:assembly href="path-name" />  
    <![CDATA[  
    // User code  
    ]]>  
</msxsl:script>  
```  
  
 `name` Atrybut zawiera nazwę zestawu i `href` atrybutu zawiera ścieżkę do zestawu. Nazwa zestawu może być pełną nazwą, taką jak "dane systemowe, wersja = 2.0.3600.0, Culture = neutral, PublicKeyToken = b77a5c561934e089", lub krótkiej nazwy, takie jak "System.Web".  
  
#### <a name="namespaces"></a>Namespaces  
 Domyślnie są dołączone następujących przestrzeni nazw:  
  
-   System  
  
-   System.Collection  
  
-   System.Text  
  
-   System.Text.RegularExpressions  
  
-   System.Xml  
  
-   System.Xml.Xsl  
  
-   System.Xml.XPath  
  
-   Microsoft.VisualBasic (po język skryptu VB)  
  
 Można dodać obsługę dodatkowe przestrzenie nazw przy użyciu `namespace` atrybutu. Wartość atrybutu jest nazwą przestrzeni nazw.  
  
```xml  
<msxsl:script>  
  <msxsl:using namespace="system.namespaceName" />  
    <![CDATA[  
    // User code  
    ]]>  
</msxsl:script>  
```  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto osadzony skrypt, aby obliczyć obwód koła podane jego radius.  
  
 [!code-csharp[XSLT_Script#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XSLT_Script/CS/xslt_script.cs#1)]
 [!code-vb[XSLT_Script#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XSLT_Script/VB/xslt_script.vb#1)]  
  
#### <a name="numberxml"></a>number.xml  
 [!code-xml[XSLT_Script#2](../../../../samples/snippets/xml/VS_Snippets_Data/XSLT_Script/XML/number.xml#2)]  
  
#### <a name="calcxsl"></a>calc.xsl  
 [!code-xml[XSLT_Script#3](../../../../samples/snippets/xml/VS_Snippets_Data/XSLT_Script/XML/calc.xsl#3)]  
  
### <a name="output"></a>Dane wyjściowe  
  
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
 [Przekształcenia XSLT](../../../../docs/standard/data/xml/xslt-transformations.md)  
 [Dynamiczne generowanie i kompilacja kodu źródłowego](../../../../docs/framework/reflection-and-codedom/dynamic-source-code-generation-and-compilation.md)
