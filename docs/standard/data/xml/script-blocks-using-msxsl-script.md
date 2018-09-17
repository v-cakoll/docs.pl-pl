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
ms.openlocfilehash: c4d7dee9ebaed20970f715026661c29aae701289
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/16/2018
ms.locfileid: "45686092"
---
# <a name="script-blocks-using-msxslscript"></a><span data-ttu-id="d5f2e-102">Skrypt bloki msxsl: Script</span><span class="sxs-lookup"><span data-stu-id="d5f2e-102">Script Blocks Using msxsl:script</span></span>
<span data-ttu-id="d5f2e-103"><xref:System.Xml.Xsl.XslCompiledTransform> Klasa obsługuje osadzonych skryptów przy użyciu `msxsl:script` elementu.</span><span class="sxs-lookup"><span data-stu-id="d5f2e-103">The <xref:System.Xml.Xsl.XslCompiledTransform> class supports embedded scripts using the `msxsl:script` element.</span></span> <span data-ttu-id="d5f2e-104">Gdy arkusz stylów jest ładowany, wszystkie funkcje zdefiniowane są kompilowane do języka Microsoft intermediate language (MSIL) przez kod Document Object Model (CodeDOM) i są wykonywane w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="d5f2e-104">When the style sheet is loaded, any defined functions are compiled to Microsoft intermediate language (MSIL) by the Code Document Object Model (CodeDOM) and are executed during run time.</span></span> <span data-ttu-id="d5f2e-105">Zestaw wygenerowany na podstawie bloku osadzonych skryptów jest oddzielony niż zestaw wygenerowany dla arkusza stylów.</span><span class="sxs-lookup"><span data-stu-id="d5f2e-105">The assembly generated from the embedded script block is separate than the assembly generated for the style sheet.</span></span>  
  
## <a name="enable-xslt-script"></a><span data-ttu-id="d5f2e-106">Włącz skryptu XSLT</span><span class="sxs-lookup"><span data-stu-id="d5f2e-106">Enable XSLT Script</span></span>  
 <span data-ttu-id="d5f2e-107">Obsługa osadzonego skryptów jest ustawienie opcjonalne XSLT na <xref:System.Xml.Xsl.XslCompiledTransform> klasy.</span><span class="sxs-lookup"><span data-stu-id="d5f2e-107">Support for embedded scripts is an optional XSLT setting on the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span> <span data-ttu-id="d5f2e-108">Obsługa skryptów jest domyślnie wyłączona.</span><span class="sxs-lookup"><span data-stu-id="d5f2e-108">Script support is disabled by default.</span></span> <span data-ttu-id="d5f2e-109">Aby włączyć obsługę skryptów, należy utworzyć <xref:System.Xml.Xsl.XsltSettings> obiekt z <xref:System.Xml.Xsl.XsltSettings.EnableScript%2A> właściwością `true` i przekazać obiekt do <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="d5f2e-109">To enable script support, create an <xref:System.Xml.Xsl.XsltSettings> object with the <xref:System.Xml.Xsl.XsltSettings.EnableScript%2A> property set to `true` and pass the object to the <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> method.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d5f2e-110">Powinna być włączona obsługa skryptów XSLT, tylko wtedy, gdy wymagana jest obsługa skryptów i pracy w pełni zaufanym środowisku.</span><span class="sxs-lookup"><span data-stu-id="d5f2e-110">XSLT scripting should be enabled only if you require script support and you are working in a fully trusted environment.</span></span>  
  
## <a name="msxslscript-element-definition"></a><span data-ttu-id="d5f2e-111">msxsl: Script definicji elementu</span><span class="sxs-lookup"><span data-stu-id="d5f2e-111">msxsl:script Element Definition</span></span>  
 <span data-ttu-id="d5f2e-112">`msxsl:script` Element jest rozszerzeniem firmy Microsoft do specyfikacji XSLT 1.0 zalecenia i ma następującą definicję:</span><span class="sxs-lookup"><span data-stu-id="d5f2e-112">The `msxsl:script` element is a Microsoft extension to the XSLT 1.0 recommendation and has the following definition:</span></span>  
  
```xml  
<msxsl:script language = "language-name" implements-prefix = "prefix of user namespace"> </msxsl:script>  
```  
  
 <span data-ttu-id="d5f2e-113">`msxsl` Prefiks jest powiązany z `urn:schemas-microsoft-com:xslt` identyfikator URI przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="d5f2e-113">The `msxsl` prefix is bound to the `urn:schemas-microsoft-com:xslt` namespace URI.</span></span> <span data-ttu-id="d5f2e-114">Arkusz stylów musi zawierać `xmlns:msxsl=urn:schemas-microsoft-com:xslt` deklarację przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="d5f2e-114">The style sheet must include the `xmlns:msxsl=urn:schemas-microsoft-com:xslt` namespace declaration.</span></span>  
  
 <span data-ttu-id="d5f2e-115">`language` Atrybut jest opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="d5f2e-115">The `language` attribute is optional.</span></span> <span data-ttu-id="d5f2e-116">Jego wartość jest język kodu w bloku osadzony kod.</span><span class="sxs-lookup"><span data-stu-id="d5f2e-116">Its value is the code language of the embedded code block.</span></span> <span data-ttu-id="d5f2e-117">Język jest mapowany do odpowiedniego CodeDOM kompilatora przy użyciu <xref:System.CodeDom.Compiler.CodeDomProvider.CreateProvider%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="d5f2e-117">The language is mapped to the appropriate CodeDOM compiler using the <xref:System.CodeDom.Compiler.CodeDomProvider.CreateProvider%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="d5f2e-118"><xref:System.Xml.Xsl.XslCompiledTransform> Klasy może obsługiwać dowolny język programu Microsoft .NET, zakładając, że odpowiednie dostawca jest zainstalowany na komputerze i jest zarejestrowany w sekcji system.codedom pliku machine.config.</span><span class="sxs-lookup"><span data-stu-id="d5f2e-118">The <xref:System.Xml.Xsl.XslCompiledTransform> class can support any Microsoft .NET language, assuming the appropriate provider is installed on the machine and is registered in the system.codedom section of the machine.config file.</span></span> <span data-ttu-id="d5f2e-119">Jeśli `language` atrybut nie zostanie określony, domyślnie języka JScript.</span><span class="sxs-lookup"><span data-stu-id="d5f2e-119">If a `language` attribute is not specified, the language defaults to JScript.</span></span> <span data-ttu-id="d5f2e-120">Nazwa języka nie jest rozróżniana wielkość liter, więc "JavaScript" i "javascript" są równoważne.</span><span class="sxs-lookup"><span data-stu-id="d5f2e-120">The language name is not case-sensitive so 'JavaScript' and 'javascript' are equivalent.</span></span>  
  
 <span data-ttu-id="d5f2e-121">`implements-prefix` Atrybut jest wymagany.</span><span class="sxs-lookup"><span data-stu-id="d5f2e-121">The `implements-prefix` attribute is mandatory.</span></span> <span data-ttu-id="d5f2e-122">Ten atrybut służy do deklarację przestrzeni nazw i skojarzyć go z bloku skryptu.</span><span class="sxs-lookup"><span data-stu-id="d5f2e-122">This attribute is used to declare a namespace and associate it with the script block.</span></span> <span data-ttu-id="d5f2e-123">Wartość tego atrybutu jest prefiks, który reprezentuje obszar nazw.</span><span class="sxs-lookup"><span data-stu-id="d5f2e-123">The value of this attribute is the prefix that represents the namespace.</span></span> <span data-ttu-id="d5f2e-124">Ten prefiks można zdefiniować gdzieś w arkuszu stylów.</span><span class="sxs-lookup"><span data-stu-id="d5f2e-124">This prefix can be defined somewhere in a style sheet.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d5f2e-125">Korzystając z `msxsl:script` elementu, zdecydowanie zaleca się że skryptu, niezależnie od języka, można umieścić w sekcji CDATA.</span><span class="sxs-lookup"><span data-stu-id="d5f2e-125">When using the `msxsl:script` element, we strongly recommend that the script, regardless of language, be placed inside a CDATA section.</span></span> <span data-ttu-id="d5f2e-126">Skrypt może zawierać operatorów, identyfikatory lub ograniczniki dla danego języka, jeśli nie znajduje się w sekcji CDATA, ma potencjał jest błędnie zinterpretowana jako XML.</span><span class="sxs-lookup"><span data-stu-id="d5f2e-126">Because the script can contain operators, identifiers, or delimiters for a given language, if it is not contained within a CDATA section, it has the potential of being misinterpreted as XML.</span></span> <span data-ttu-id="d5f2e-127">Następujący kody XML pokazuje szablon sekcja CDATA, gdzie można umieścić kod.</span><span class="sxs-lookup"><span data-stu-id="d5f2e-127">The following XML shows a template of the CDATA section where code can be placed.</span></span>  
  
```xml  
<msxsl:script implements-prefix='your-prefix' language='CSharp'>  
<![CDATA[  
// Code block.  
]]>  
</msxsl:script>  
```  
  
## <a name="script-functions"></a><span data-ttu-id="d5f2e-128">Funkcje skryptu</span><span class="sxs-lookup"><span data-stu-id="d5f2e-128">Script Functions</span></span>  
 <span data-ttu-id="d5f2e-129">Funkcje mogą być zadeklarowane w obrębie `msxsl:script` elementu.</span><span class="sxs-lookup"><span data-stu-id="d5f2e-129">Functions can be declared within the `msxsl:script` element.</span></span> <span data-ttu-id="d5f2e-130">Gdy funkcja jest zadeklarowana, znajduje się w bloku skryptu.</span><span class="sxs-lookup"><span data-stu-id="d5f2e-130">When a function is declared, it is contained in a script block.</span></span> <span data-ttu-id="d5f2e-131">Arkusze stylów może zawierać wiele Bloki skryptu, każdy niezależnego innych.</span><span class="sxs-lookup"><span data-stu-id="d5f2e-131">Style sheets can contain multiple script blocks, each operating independent of the other.</span></span> <span data-ttu-id="d5f2e-132">Oznacza to, że jeśli wykonujesz wewnątrz bloku skryptu, nie można wywołać funkcję zdefiniowaną w innego bloku skryptu, o ile nie jest zadeklarowany ma ten sam język skryptów i tej samej przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="d5f2e-132">That means that if you are executing inside a script block, you cannot call a function that you defined in another script block unless it is declared to have the same namespace and the same scripting language.</span></span> <span data-ttu-id="d5f2e-133">Ponieważ każdy blok skryptu może znajdować się w jego własnej języka i bloku jest analizowany zgodnie z regułami gramatyki tego analizatora języka zaleca się, że używasz poprawnej składni język używany w.</span><span class="sxs-lookup"><span data-stu-id="d5f2e-133">Because each script block can be in its own language, and the block is parsed according to the grammar rules of that language parser we recommend that you use the correct syntax for the language in use.</span></span> <span data-ttu-id="d5f2e-134">Na przykład jeśli jesteś w bloku skryptu Microsoft C#, należy użyć składni komentarza języka C#.</span><span class="sxs-lookup"><span data-stu-id="d5f2e-134">For example, if you are in a Microsoft C# script block, use the C# comment syntax.</span></span>  
  
 <span data-ttu-id="d5f2e-135">Podanych argumentów i wartości zwracane funkcji mogą być dowolnego typu.</span><span class="sxs-lookup"><span data-stu-id="d5f2e-135">The supplied arguments and return values to the function can be of any type.</span></span> <span data-ttu-id="d5f2e-136">Ponieważ typy W3C XPath są podzbiorem popularnych typów języka wspólnego (CLR), konwersja typu odbywa się na typy, które nie są traktowane jako typu wyrażenie XPath.</span><span class="sxs-lookup"><span data-stu-id="d5f2e-136">Because the W3C XPath types are a subset of the common language runtime (CLR) types, type conversion takes place on types that are not considered to be an XPath type.</span></span> <span data-ttu-id="d5f2e-137">W poniższej tabeli przedstawiono odpowiednie typy W3C i równoważne typu CLR.</span><span class="sxs-lookup"><span data-stu-id="d5f2e-137">The following table shows the corresponding W3C types and the equivalent CLR type.</span></span>  
  
|<span data-ttu-id="d5f2e-138">Typ W3C</span><span class="sxs-lookup"><span data-stu-id="d5f2e-138">W3C type</span></span>|<span data-ttu-id="d5f2e-139">Typ CLR</span><span class="sxs-lookup"><span data-stu-id="d5f2e-139">CLR type</span></span>|  
|--------------|--------------|  
|`String`|<xref:System.String>|  
|`Boolean`|<xref:System.Boolean>|  
|`Number`|<xref:System.Double>|  
|`Result Tree Fragment`|<xref:System.Xml.XPath.XPathNavigator>|  
|`Node Set`|<xref:System.Xml.XPath.XPathNodeIterator>|  
  
 <span data-ttu-id="d5f2e-140">CLR, typy liczbowe są konwertowane na <xref:System.Double>.</span><span class="sxs-lookup"><span data-stu-id="d5f2e-140">CLR numeric types are converted to <xref:System.Double>.</span></span> <span data-ttu-id="d5f2e-141"><xref:System.DateTime> Typu jest konwertowany na <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="d5f2e-141">The <xref:System.DateTime> type is converted to <xref:System.String>.</span></span> <span data-ttu-id="d5f2e-142"><xref:System.Xml.XPath.IXPathNavigable> typy są konwertowane na <xref:System.Xml.XPath.XPathNavigator>.</span><span class="sxs-lookup"><span data-stu-id="d5f2e-142"><xref:System.Xml.XPath.IXPathNavigable> types are converted to <xref:System.Xml.XPath.XPathNavigator>.</span></span> <span data-ttu-id="d5f2e-143">**[] Klasy XPathNavigator** jest konwertowana na <xref:System.Xml.XPath.XPathNodeIterator>.</span><span class="sxs-lookup"><span data-stu-id="d5f2e-143">**XPathNavigator[]** is converted to <xref:System.Xml.XPath.XPathNodeIterator>.</span></span>  
  
 <span data-ttu-id="d5f2e-144">Wszystkie pozostałe typy zgłosić błąd.</span><span class="sxs-lookup"><span data-stu-id="d5f2e-144">All other types throw an error.</span></span>  
  
### <a name="importing-namespaces-and-assemblies"></a><span data-ttu-id="d5f2e-145">Importowanie przestrzeni nazw i zestawów</span><span class="sxs-lookup"><span data-stu-id="d5f2e-145">Importing Namespaces and Assemblies</span></span>  
 <span data-ttu-id="d5f2e-146"><xref:System.Xml.Xsl.XslCompiledTransform> Klasy powoduje wstępne definiowanie zestawu zestawy i przestrzenie nazw, które są obsługiwane domyślnie `msxsl:script` elementu.</span><span class="sxs-lookup"><span data-stu-id="d5f2e-146">The <xref:System.Xml.Xsl.XslCompiledTransform> class predefines a set of assemblies and namespaces that are supported by default by the `msxsl:script` element.</span></span> <span data-ttu-id="d5f2e-147">Jednak można użyć klas i składowych należące do przestrzeni nazw, która nie znajduje się na liście wstępnie zdefiniowane przez zaimportowanie zestawu i przestrzeni nazw w `msxsl:script` bloku.</span><span class="sxs-lookup"><span data-stu-id="d5f2e-147">However, you can use classes and members belonging to a namespace that is not on the predefined list by importing the assembly and namespace in `msxsl:script` block.</span></span>  
  
#### <a name="assemblies"></a><span data-ttu-id="d5f2e-148">Zestawy</span><span class="sxs-lookup"><span data-stu-id="d5f2e-148">Assemblies</span></span>  
 <span data-ttu-id="d5f2e-149">Następujące dwa zestawy są określone przez domyślny:</span><span class="sxs-lookup"><span data-stu-id="d5f2e-149">The following two assemblies are referenced by default:</span></span>  
  
-   <span data-ttu-id="d5f2e-150">PLik System.dll</span><span class="sxs-lookup"><span data-stu-id="d5f2e-150">System.dll</span></span>  
  
-   <span data-ttu-id="d5f2e-151">System.Xml.dll</span><span class="sxs-lookup"><span data-stu-id="d5f2e-151">System.Xml.dll</span></span>  
  
-   <span data-ttu-id="d5f2e-152">Pliku Microsoft.VisualBasic.dll (jeśli jest to język skryptów jest VB)</span><span class="sxs-lookup"><span data-stu-id="d5f2e-152">Microsoft.VisualBasic.dll (when the script language is VB)</span></span>  
  
 <span data-ttu-id="d5f2e-153">Możesz zaimportować dodatkowe zestawy za pomocą `msxsl:assembly` elementu.</span><span class="sxs-lookup"><span data-stu-id="d5f2e-153">You can import the additional assemblies using the `msxsl:assembly` element.</span></span> <span data-ttu-id="d5f2e-154">W tym zestawie podczas kompilowania arkusza stylów.</span><span class="sxs-lookup"><span data-stu-id="d5f2e-154">This includes the assembly when the style sheet is compiled.</span></span> <span data-ttu-id="d5f2e-155">`msxsl:assembly` Element ma następującą definicję:</span><span class="sxs-lookup"><span data-stu-id="d5f2e-155">The `msxsl:assembly` element has the following definition:</span></span>  
  
```xml  
<msxsl:script>  
  <msxsl:assembly name="system.assemblyName" />  
  <msxsl:assembly href="path-name" />  
    <![CDATA[  
    // User code  
    ]]>  
</msxsl:script>  
```  
  
 <span data-ttu-id="d5f2e-156">`name` Atrybut zawiera nazwę zestawu i `href` atrybutu zawiera ścieżkę do zestawu.</span><span class="sxs-lookup"><span data-stu-id="d5f2e-156">The `name` attribute contains the name of the assembly and the `href` attribute contains the path to the assembly.</span></span> <span data-ttu-id="d5f2e-157">Nazwa zestawu może być pełną nazwą, taką jak "System.Data, Version = 2.0.3600.0, Culture = neutral, PublicKeyToken = b77a5c561934e089", lub krótkiej nazwy, takie jak "System.Web".</span><span class="sxs-lookup"><span data-stu-id="d5f2e-157">The assembly name can be a full name, such as "System.Data, Version=2.0.3600.0, Culture=neutral, PublicKeyToken=b77a5c561934e089", or a short name, such as "System.Web".</span></span>  
  
#### <a name="namespaces"></a><span data-ttu-id="d5f2e-158">Namespaces</span><span class="sxs-lookup"><span data-stu-id="d5f2e-158">Namespaces</span></span>  
 <span data-ttu-id="d5f2e-159">Następujące przestrzenie nazw są domyślnie dołączone:</span><span class="sxs-lookup"><span data-stu-id="d5f2e-159">The following namespaces are included by default:</span></span>  
  
-   <span data-ttu-id="d5f2e-160">System</span><span class="sxs-lookup"><span data-stu-id="d5f2e-160">System</span></span>  
  
-   <span data-ttu-id="d5f2e-161">System.Collection</span><span class="sxs-lookup"><span data-stu-id="d5f2e-161">System.Collection</span></span>  
  
-   <span data-ttu-id="d5f2e-162">System.Text</span><span class="sxs-lookup"><span data-stu-id="d5f2e-162">System.Text</span></span>  
  
-   <span data-ttu-id="d5f2e-163">System.Text.RegularExpressions</span><span class="sxs-lookup"><span data-stu-id="d5f2e-163">System.Text.RegularExpressions</span></span>  
  
-   <span data-ttu-id="d5f2e-164">System.Xml</span><span class="sxs-lookup"><span data-stu-id="d5f2e-164">System.Xml</span></span>  
  
-   <span data-ttu-id="d5f2e-165">System.Xml.Xsl</span><span class="sxs-lookup"><span data-stu-id="d5f2e-165">System.Xml.Xsl</span></span>  
  
-   <span data-ttu-id="d5f2e-166">System.Xml.XPath</span><span class="sxs-lookup"><span data-stu-id="d5f2e-166">System.Xml.XPath</span></span>  
  
-   <span data-ttu-id="d5f2e-167">Microsoft.VisualBasic (jeśli jest to język skryptów jest VB)</span><span class="sxs-lookup"><span data-stu-id="d5f2e-167">Microsoft.VisualBasic (when the script language is VB)</span></span>  
  
 <span data-ttu-id="d5f2e-168">Można dodać obsługę dodatkowe przestrzenie nazw `namespace` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="d5f2e-168">You can add support for additional namespaces using the `namespace` attribute.</span></span> <span data-ttu-id="d5f2e-169">Wartość atrybutu jest nazwa przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="d5f2e-169">The attribute value is the name of the namespace.</span></span>  
  
```xml  
<msxsl:script>  
  <msxsl:using namespace="system.namespaceName" />  
    <![CDATA[  
    // User code  
    ]]>  
</msxsl:script>  
```  
  
## <a name="example"></a><span data-ttu-id="d5f2e-170">Przykład</span><span class="sxs-lookup"><span data-stu-id="d5f2e-170">Example</span></span>  
 <span data-ttu-id="d5f2e-171">W poniższym przykładzie użyto osadzonych skryptów do obliczania obwód koła, biorąc pod uwagę jego usługi radius.</span><span class="sxs-lookup"><span data-stu-id="d5f2e-171">The following example uses an embedded script to calculate the circumference of a circle given its radius.</span></span>  
  
 [!code-csharp[XSLT_Script#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XSLT_Script/CS/xslt_script.cs#1)]
 [!code-vb[XSLT_Script#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XSLT_Script/VB/xslt_script.vb#1)]  
  
#### <a name="numberxml"></a><span data-ttu-id="d5f2e-172">number.xml</span><span class="sxs-lookup"><span data-stu-id="d5f2e-172">number.xml</span></span>  
 [!code-xml[XSLT_Script#2](../../../../samples/snippets/xml/VS_Snippets_Data/XSLT_Script/XML/number.xml#2)]  
  
#### <a name="calcxsl"></a><span data-ttu-id="d5f2e-173">calc.xsl</span><span class="sxs-lookup"><span data-stu-id="d5f2e-173">calc.xsl</span></span>  
 [!code-xml[XSLT_Script#3](../../../../samples/snippets/xml/VS_Snippets_Data/XSLT_Script/XML/calc.xsl#3)]  
  
### <a name="output"></a><span data-ttu-id="d5f2e-174">Dane wyjściowe</span><span class="sxs-lookup"><span data-stu-id="d5f2e-174">Output</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="d5f2e-175">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d5f2e-175">See also</span></span>

- [<span data-ttu-id="d5f2e-176">Przekształcenia XSLT</span><span class="sxs-lookup"><span data-stu-id="d5f2e-176">XSLT Transformations</span></span>](../../../../docs/standard/data/xml/xslt-transformations.md)  
- [<span data-ttu-id="d5f2e-177">Dynamiczne generowanie i kompilacja kodu źródłowego</span><span class="sxs-lookup"><span data-stu-id="d5f2e-177">Dynamic Source Code Generation and Compilation</span></span>](../../../../docs/framework/reflection-and-codedom/dynamic-source-code-generation-and-compilation.md)
