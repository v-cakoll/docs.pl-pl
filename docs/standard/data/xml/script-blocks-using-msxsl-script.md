---
title: Bloki skryptów i element msxsl:script
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: fde6f43f-c594-486f-abcb-2211197fae20
ms.openlocfilehash: a63452df16e452a90eff3977ac8726cc0a5ac439
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75710196"
---
# <a name="script-blocks-using-msxslscript"></a>Bloki skryptów i element msxsl:script
Klasa <xref:System.Xml.Xsl.XslCompiledTransform> obsługuje osadzone skrypty przy użyciu elementu `msxsl:script`. Po załadowaniu arkusza stylów wszystkie zdefiniowane funkcje są kompilowane do języka pośredniego firmy Microsoft (MSIL) przez Code Document Object Model (CodeDOM) i są wykonywane w czasie wykonywania. Zestaw wygenerowany z osadzonego bloku skryptu jest oddzielony od zestawu wygenerowanego dla arkusza stylów.  
  
## <a name="enable-xslt-script"></a>Włącz skrypt XSLT  
 Obsługa skryptów osadzonych jest opcjonalnym ustawieniem XSLT dla klasy <xref:System.Xml.Xsl.XslCompiledTransform>. Obsługa skryptów jest domyślnie wyłączona. Aby włączyć obsługę skryptów, Utwórz obiekt <xref:System.Xml.Xsl.XsltSettings> z właściwością <xref:System.Xml.Xsl.XsltSettings.EnableScript%2A> ustawioną na `true` i przekaż obiekt do metody <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A>.  
  
> [!NOTE]
> Obsługa skryptów XSLT powinna być włączona tylko wtedy, gdy wymagana jest obsługa skryptów i Pracujesz w w pełni zaufanym środowisku.  
  
## <a name="msxslscript-element-definition"></a>msxsl: definicja elementu skryptu  
 Element `msxsl:script` to rozszerzenie Microsoft do zalecenia XSLT 1,0 i ma następującą definicję:  
  
```xml  
<msxsl:script language = "language-name" implements-prefix = "prefix of user namespace"> </msxsl:script>  
```  
  
 Prefiks `msxsl` jest powiązany z identyfikatorem URI `urn:schemas-microsoft-com:xslt` przestrzeni nazw. Arkusz stylów musi zawierać deklarację przestrzeni nazw `xmlns:msxsl=urn:schemas-microsoft-com:xslt`.  
  
 Atrybut `language` jest opcjonalny. Jego wartością jest język kodu osadzonego bloku kodu. Język jest mapowany do odpowiedniego kompilatora CodeDOM przy użyciu metody <xref:System.CodeDom.Compiler.CodeDomProvider.CreateProvider%2A?displayProperty=nameWithType>. Klasa <xref:System.Xml.Xsl.XslCompiledTransform> może obsługiwać dowolny język Microsoft .NET, przy założeniu, że odpowiedni Dostawca jest zainstalowany na komputerze i jest zarejestrowany w sekcji System. CodeDom pliku Machine. config. Jeśli atrybut `language` nie zostanie określony, język jest wartością domyślną języka JScript. W nazwie języka nie jest rozróżniana wielkość liter, dlatego "JavaScript" i "JavaScript" są równoważne.  
  
 Atrybut `implements-prefix` jest obowiązkowy. Ten atrybut służy do deklarowania przestrzeni nazw i kojarzenia jej z blokiem skryptu. Wartość tego atrybutu jest prefiks, który reprezentuje obszar nazw. Ten prefiks można zdefiniować w arkuszu stylów.  
  
> [!NOTE]
> W przypadku używania elementu `msxsl:script` zdecydowanie zaleca się, aby skrypt niezależnie od języka został umieszczony wewnątrz sekcji CDATA. Ze względu na to, że skrypt może zawierać operatory, identyfikatory lub ograniczniki dla danego języka, jeśli nie jest zawarty w sekcji CDATA, ma możliwość błędnego interpretowania kodu XML. W poniższym kodzie XML przedstawiono szablon sekcji CDATA, w której można umieścić kod.  
  
```xml  
<msxsl:script implements-prefix='your-prefix' language='CSharp'>  
<![CDATA[  
// Code block.  
]]>  
</msxsl:script>  
```  
  
## <a name="script-functions"></a>Funkcje skryptu  
 Funkcje mogą być deklarowane w obrębie elementu `msxsl:script`. Gdy funkcja jest zadeklarowana, jest zawarta w bloku skryptu. Arkusze stylów mogą zawierać wiele bloków skryptu, z których każda działa niezależnie od siebie. Oznacza to, że jeśli wykonujesz wewnątrz bloku skryptu, nie można wywołać funkcji, która została zdefiniowana w innym bloku skryptu, chyba że jest zadeklarowana jako ma tę samą przestrzeń nazw i ten sam język skryptowy. Ponieważ każdy blok skryptu może znajdować się w własnym języku, a blok jest analizowany zgodnie z regułami gramatyki tego analizatora języka, zalecamy użycie odpowiedniej składni dla używanego języka. Na przykład, jeśli jesteś w bloku skryptu firmy C# Microsoft, użyj składni C# komentarza.  
  
 Podane argumenty i zwracane wartości do funkcji mogą być dowolnego typu. Ponieważ typy W3C XPath są podzbiorem typów środowiska uruchomieniowego języka wspólnego (CLR), konwersja typu odbywa się na typach, które nie są uważane za typ XPath. W poniższej tabeli przedstawiono odpowiednie typy W3C i odpowiedni typ środowiska CLR.  
  
|Typ W3C|Typ CLR|  
|--------------|--------------|  
|`String`|<xref:System.String>|  
|`Boolean`|<xref:System.Boolean>|  
|`Number`|<xref:System.Double>|  
|`Result Tree Fragment`|<xref:System.Xml.XPath.XPathNavigator>|  
|`Node Set`|<xref:System.Xml.XPath.XPathNodeIterator>|  
  
 Typy liczbowe CLR są konwertowane na <xref:System.Double>. Typ <xref:System.DateTime> jest konwertowany na <xref:System.String>. typy <xref:System.Xml.XPath.IXPathNavigable> są konwertowane na <xref:System.Xml.XPath.XPathNavigator>. Element **XPathNavigator []** został przekonwertowany na <xref:System.Xml.XPath.XPathNodeIterator>.  
  
 Wszystkie inne typy zgłaszają błąd.  
  
### <a name="importing-namespaces-and-assemblies"></a>Importowanie przestrzeni nazw i zestawów  
 Klasa <xref:System.Xml.Xsl.XslCompiledTransform> wstępnie definiuje zestaw zestawów i przestrzeni nazw, które są obsługiwane domyślnie przez element `msxsl:script`. Można jednak użyć klas i elementów członkowskich należących do przestrzeni nazw, która nie znajduje się na wstępnie zdefiniowanej liście przez zaimportowanie zestawu i przestrzeni nazw w bloku `msxsl:script`.  
  
#### <a name="assemblies"></a>Zestawy  
 Następujące dwa zestawy są domyślnie przywoływane:  
  
- PLik System.dll  
  
- System.Xml.dll  
  
- Microsoft. VisualBasic. dll (gdy skrypt skryptów jest w języku VB)  
  
 Dodatkowe zestawy można zaimportować przy użyciu elementu `msxsl:assembly`. Obejmuje to zestaw, gdy arkusz stylów jest kompilowany. Element `msxsl:assembly` ma następującą definicję:  
  
```xml  
<msxsl:script>  
  <msxsl:assembly name="system.assemblyName" />  
  <msxsl:assembly href="path-name" />  
    <![CDATA[  
    // User code  
    ]]>  
</msxsl:script>  
```  
  
 Atrybut `name` zawiera nazwę zestawu, a atrybut `href` zawiera ścieżkę do zestawu. Nazwa zestawu może być pełną nazwą, taką jak "System. Data, Version = 2.0.3600.0, Culture = neutral, PublicKeyToken = b77a5c561934e089" lub krótką nazwą, taką jak "System. Web".  
  
#### <a name="namespaces"></a>{1&gt;Przestrzenie nazw&lt;1}  
 Domyślnie są uwzględniane następujące przestrzenie nazw:  
  
- System  
  
- System.Collection  
  
- System.Text  
  
- System.Text.RegularExpressions  
  
- System.Xml  
  
- System.Xml.Xsl  
  
- System.Xml.XPath  
  
- Microsoft. VisualBasic (gdy język skryptu to VB)  
  
 Można dodać obsługę dodatkowych przestrzeni nazw przy użyciu atrybutu `namespace`. Wartość atrybutu jest nazwą przestrzeni nazw.  
  
```xml  
<msxsl:script>  
  <msxsl:using namespace="system.namespaceName" />  
    <![CDATA[  
    // User code  
    ]]>  
</msxsl:script>  
```  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie zastosowano osadzony skrypt do obliczenia obwodu okręgu, który ma swój promień.  
  
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
