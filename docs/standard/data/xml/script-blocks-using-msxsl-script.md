---
title: 'Skrypt bloki msxsl: Script'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: fde6f43f-c594-486f-abcb-2211197fae20
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b45b8ebe048a5917019349ea3a6a357b7e90a9c0
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54565647"
---
# <a name="script-blocks-using-msxslscript"></a>Skrypt bloki msxsl: Script
<xref:System.Xml.Xsl.XslCompiledTransform> Klasa obsługuje osadzonych skryptów przy użyciu `msxsl:script` elementu. Gdy arkusz stylów jest ładowany, wszystkie funkcje zdefiniowane są kompilowane do języka Microsoft intermediate language (MSIL) przez kod Document Object Model (CodeDOM) i są wykonywane w czasie wykonywania. Zestaw wygenerowany na podstawie bloku osadzonych skryptów jest oddzielony niż zestaw wygenerowany dla arkusza stylów.  
  
## <a name="enable-xslt-script"></a>Włącz skryptu XSLT  
 Obsługa osadzonego skryptów jest ustawienie opcjonalne XSLT na <xref:System.Xml.Xsl.XslCompiledTransform> klasy. Obsługa skryptów jest domyślnie wyłączona. Aby włączyć obsługę skryptów, należy utworzyć <xref:System.Xml.Xsl.XsltSettings> obiekt z <xref:System.Xml.Xsl.XsltSettings.EnableScript%2A> właściwością `true` i przekazać obiekt do <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> metody.  
  
> [!NOTE]
>  Powinna być włączona obsługa skryptów XSLT, tylko wtedy, gdy wymagana jest obsługa skryptów i pracy w pełni zaufanym środowisku.  
  
## <a name="msxslscript-element-definition"></a>msxsl:script Element Definition  
 `msxsl:script` Element jest rozszerzeniem firmy Microsoft do specyfikacji XSLT 1.0 zalecenia i ma następującą definicję:  
  
```xml  
<msxsl:script language = "language-name" implements-prefix = "prefix of user namespace"> </msxsl:script>  
```  
  
 `msxsl` Prefiks jest powiązany z `urn:schemas-microsoft-com:xslt` identyfikator URI przestrzeni nazw. Arkusz stylów musi zawierać `xmlns:msxsl=urn:schemas-microsoft-com:xslt` deklarację przestrzeni nazw.  
  
 `language` Atrybut jest opcjonalny. Jego wartość jest język kodu w bloku osadzony kod. Język jest mapowany do odpowiedniego CodeDOM kompilatora przy użyciu <xref:System.CodeDom.Compiler.CodeDomProvider.CreateProvider%2A?displayProperty=nameWithType> metody. <xref:System.Xml.Xsl.XslCompiledTransform> Klasy może obsługiwać dowolny język programu Microsoft .NET, zakładając, że odpowiednie dostawca jest zainstalowany na komputerze i jest zarejestrowany w sekcji system.codedom pliku machine.config. Jeśli `language` atrybut nie zostanie określony, domyślnie języka JScript. Nazwa języka nie jest rozróżniana wielkość liter, więc "JavaScript" i "javascript" są równoważne.  
  
 `implements-prefix` Atrybut jest wymagany. Ten atrybut służy do deklarację przestrzeni nazw i skojarzyć go z bloku skryptu. Wartość tego atrybutu jest prefiks, który reprezentuje obszar nazw. Ten prefiks można zdefiniować gdzieś w arkuszu stylów.  
  
> [!NOTE]
>  Korzystając z `msxsl:script` elementu, zdecydowanie zaleca się że skryptu, niezależnie od języka, można umieścić w sekcji CDATA. Skrypt może zawierać operatorów, identyfikatory lub ograniczniki dla danego języka, jeśli nie znajduje się w sekcji CDATA, ma potencjał jest błędnie zinterpretowana jako XML. Następujący kody XML pokazuje szablon sekcja CDATA, gdzie można umieścić kod.  
  
```xml  
<msxsl:script implements-prefix='your-prefix' language='CSharp'>  
<![CDATA[  
// Code block.  
]]>  
</msxsl:script>  
```  
  
## <a name="script-functions"></a>Funkcje skryptu  
 Funkcje mogą być zadeklarowane w obrębie `msxsl:script` elementu. Gdy funkcja jest zadeklarowana, znajduje się w bloku skryptu. Arkusze stylów może zawierać wiele Bloki skryptu, każdy niezależnego innych. Oznacza to, że jeśli wykonujesz wewnątrz bloku skryptu, nie można wywołać funkcję zdefiniowaną w innego bloku skryptu, o ile nie jest zadeklarowany ma ten sam język skryptów i tej samej przestrzeni nazw. Ponieważ każdy blok skryptu może znajdować się w jego własnej języka i bloku jest analizowany zgodnie z regułami gramatyki tego analizatora języka zaleca się, że używasz poprawnej składni język używany w. Na przykład jeśli jesteś w bloku skryptu Microsoft C#, należy użyć składni komentarza języka C#.  
  
 Podanych argumentów i wartości zwracane funkcji mogą być dowolnego typu. Ponieważ typy W3C XPath są podzbiorem popularnych typów języka wspólnego (CLR), konwersja typu odbywa się na typy, które nie są traktowane jako typu wyrażenie XPath. W poniższej tabeli przedstawiono odpowiednie typy W3C i równoważne typu CLR.  
  
|Typ W3C|Typ CLR|  
|--------------|--------------|  
|`String`|<xref:System.String>|  
|`Boolean`|<xref:System.Boolean>|  
|`Number`|<xref:System.Double>|  
|`Result Tree Fragment`|<xref:System.Xml.XPath.XPathNavigator>|  
|`Node Set`|<xref:System.Xml.XPath.XPathNodeIterator>|  
  
 CLR, typy liczbowe są konwertowane na <xref:System.Double>. <xref:System.DateTime> Typu jest konwertowany na <xref:System.String>. <xref:System.Xml.XPath.IXPathNavigable> typy są konwertowane na <xref:System.Xml.XPath.XPathNavigator>. **[] Klasy XPathNavigator** jest konwertowana na <xref:System.Xml.XPath.XPathNodeIterator>.  
  
 Wszystkie pozostałe typy zgłosić błąd.  
  
### <a name="importing-namespaces-and-assemblies"></a>Importowanie przestrzeni nazw i zestawów  
 <xref:System.Xml.Xsl.XslCompiledTransform> Klasy powoduje wstępne definiowanie zestawu zestawy i przestrzenie nazw, które są obsługiwane domyślnie `msxsl:script` elementu. Jednak można użyć klas i składowych należące do przestrzeni nazw, która nie znajduje się na liście wstępnie zdefiniowane przez zaimportowanie zestawu i przestrzeni nazw w `msxsl:script` bloku.  
  
#### <a name="assemblies"></a>Zestawy  
 Następujące dwa zestawy są określone przez domyślny:  
  
-   PLik System.dll  
  
-   System.Xml.dll  
  
-   Pliku Microsoft.VisualBasic.dll (jeśli jest to język skryptów jest VB)  
  
 Możesz zaimportować dodatkowe zestawy za pomocą `msxsl:assembly` elementu. W tym zestawie podczas kompilowania arkusza stylów. `msxsl:assembly` Element ma następującą definicję:  
  
```xml  
<msxsl:script>  
  <msxsl:assembly name="system.assemblyName" />  
  <msxsl:assembly href="path-name" />  
    <![CDATA[  
    // User code  
    ]]>  
</msxsl:script>  
```  
  
 `name` Atrybut zawiera nazwę zestawu i `href` atrybutu zawiera ścieżkę do zestawu. Nazwa zestawu może być pełną nazwą, taką jak "System.Data, Version = 2.0.3600.0, Culture = neutral, PublicKeyToken = b77a5c561934e089", lub krótkiej nazwy, takie jak "System.Web".  
  
#### <a name="namespaces"></a>Namespaces  
 Następujące przestrzenie nazw są domyślnie dołączone:  
  
-   System  
  
-   System.Collection  
  
-   System.Text  
  
-   System.Text.RegularExpressions  
  
-   System.Xml  
  
-   System.Xml.Xsl  
  
-   System.Xml.XPath  
  
-   Microsoft.VisualBasic (jeśli jest to język skryptów jest VB)  
  
 Można dodać obsługę dodatkowe przestrzenie nazw `namespace` atrybutu. Wartość atrybutu jest nazwa przestrzeni nazw.  
  
```xml  
<msxsl:script>  
  <msxsl:using namespace="system.namespaceName" />  
    <![CDATA[  
    // User code  
    ]]>  
</msxsl:script>  
```  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto osadzonych skryptów do obliczania obwód koła, biorąc pod uwagę jego usługi radius.  
  
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
  
## <a name="see-also"></a>Zobacz także

- [Przekształcenia XSLT](../../../../docs/standard/data/xml/xslt-transformations.md)
- [Dynamiczne generowanie i kompilacja kodu źródłowego](../../../../docs/framework/reflection-and-codedom/dynamic-source-code-generation-and-compilation.md)
