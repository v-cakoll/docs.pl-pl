---
title: 'XSLT skryptów przy użyciu arkusza stylów &lt;msxsl: Script&gt;'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 60e2541b-0cea-4b2e-a4fa-85f4c50f1bef
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 68c98b3b4effbe7cea1a3c4443d2222e6bbcd43c
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2018
ms.locfileid: "44036135"
---
# <a name="xslt-stylesheet-scripting-using-ltmsxslscriptgt"></a><span data-ttu-id="04332-102">XSLT skryptów przy użyciu arkusza stylów &lt;msxsl: Script&gt;</span><span class="sxs-lookup"><span data-stu-id="04332-102">XSLT Stylesheet Scripting Using &lt;msxsl:script&gt;</span></span>
<span data-ttu-id="04332-103"><xref:System.Xml.Xsl.XslTransform> Klasa obsługuje osadzonych skryptów przy użyciu `script` elementu.</span><span class="sxs-lookup"><span data-stu-id="04332-103">The <xref:System.Xml.Xsl.XslTransform> class supports embedded scripting using the `script` element.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="04332-104"><xref:System.Xml.Xsl.XslTransform> Klasy jest przestarzała w [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)].</span><span class="sxs-lookup"><span data-stu-id="04332-104">The <xref:System.Xml.Xsl.XslTransform> class is obsolete in the [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)].</span></span> <span data-ttu-id="04332-105">Można przeprowadzić rozszerzalny język arkusza stylów dla przekształceń przekształcenia (XSLT) przy użyciu <xref:System.Xml.Xsl.XslCompiledTransform> klasy.</span><span class="sxs-lookup"><span data-stu-id="04332-105">You can perform Extensible Stylesheet Language for Transformations (XSLT) transformations using the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span> <span data-ttu-id="04332-106">Zobacz [używanie klasy XslCompiledTransform](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) i [Migrowanie z klasy XslTransform](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md) Aby uzyskać więcej informacji.</span><span class="sxs-lookup"><span data-stu-id="04332-106">See [Using the XslCompiledTransform Class](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) and [Migrating From the XslTransform Class](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md) for more information.</span></span>  
  
 <span data-ttu-id="04332-107"><xref:System.Xml.Xsl.XslTransform> Klasa obsługuje osadzonych skryptów przy użyciu `script` elementu.</span><span class="sxs-lookup"><span data-stu-id="04332-107">The <xref:System.Xml.Xsl.XslTransform> class supports embedded scripting using the `script` element.</span></span> <span data-ttu-id="04332-108">Po załadowaniu arkusza stylów, wszystkie funkcje zdefiniowane są kompilowane do języka Microsoft intermediate language (MSIL), są opakowane w definicji klasy i w wyniku mają bez utraty wydajności.</span><span class="sxs-lookup"><span data-stu-id="04332-108">When the style sheet is loaded, any defined functions are compiled to Microsoft intermediate language (MSIL) by being wrapped in a class definition and have no performance loss as a result.</span></span>  
  
 <span data-ttu-id="04332-109">`<msxsl:script>` Jest zdefiniowany element poniżej:</span><span class="sxs-lookup"><span data-stu-id="04332-109">The `<msxsl:script>` element is defined below:</span></span>  
  
```xml  
<msxsl:script language = "language-name" implements-prefix = "prefix of user namespace"> </msxsl:script>  
```  
  
 <span data-ttu-id="04332-110">gdzie `msxsl` jest prefiks, który jest powiązany z przestrzeni nazw `urn:schemas-microsoft-com:xslt`.</span><span class="sxs-lookup"><span data-stu-id="04332-110">where `msxsl` is a prefix bound to the namespace `urn:schemas-microsoft-com:xslt`.</span></span>  
  
 <span data-ttu-id="04332-111">`language` Atrybut nie jest wymagany, ale jeśli zostanie określony, jego wartość musi być jedną z następujących czynności: C#, VB, JScript, JavaScript, języka Visual Basic lub języka CSharp.</span><span class="sxs-lookup"><span data-stu-id="04332-111">The `language` attribute is not mandatory, but if specified, its value must be one of the following: C#, VB, JScript, JavaScript, VisualBasic, or CSharp.</span></span> <span data-ttu-id="04332-112">Jeśli nie zostanie określona, język domyślnie JScript.</span><span class="sxs-lookup"><span data-stu-id="04332-112">If not specified, the language defaults to JScript.</span></span> <span data-ttu-id="04332-113">`language-name` Nie jest rozróżniana wielkość liter, więc "JavaScript" i "javascript" są równoważne.</span><span class="sxs-lookup"><span data-stu-id="04332-113">The `language-name` is not case-sensitive, so 'JavaScript' and 'javascript' are equivalent.</span></span>  
  
 <span data-ttu-id="04332-114">`implements-prefix` Atrybut jest wymagany.</span><span class="sxs-lookup"><span data-stu-id="04332-114">The `implements-prefix` attribute is mandatory.</span></span> <span data-ttu-id="04332-115">Ten atrybut służy do deklarację przestrzeni nazw i skojarzyć go z bloku skryptu.</span><span class="sxs-lookup"><span data-stu-id="04332-115">This attribute is used to declare a namespace and associate it with the script block.</span></span> <span data-ttu-id="04332-116">Wartość tego atrybutu jest prefiks, który reprezentuje obszar nazw.</span><span class="sxs-lookup"><span data-stu-id="04332-116">The value of this attribute is the prefix that represents the namespace.</span></span> <span data-ttu-id="04332-117">Ta przestrzeń nazw można zdefiniować gdzieś w arkuszu stylów.</span><span class="sxs-lookup"><span data-stu-id="04332-117">This namespace can be defined somewhere in a style sheet.</span></span>  
  
 <span data-ttu-id="04332-118">Ponieważ `msxsl:script` element należy do przestrzeni nazw `urn:schemas-microsoft-com:xslt`, arkusz stylów może zawierać deklaracji przestrzeni nazw `xmlns:msxsl=urn:schemas-microsoft-com:xslt`.</span><span class="sxs-lookup"><span data-stu-id="04332-118">Because the `msxsl:script` element belongs to the namespace `urn:schemas-microsoft-com:xslt`, the style sheet must include the namespace declaration `xmlns:msxsl=urn:schemas-microsoft-com:xslt`.</span></span>  
  
 <span data-ttu-id="04332-119">Jeśli obiekt wywołujący skryptu nie ma <xref:System.Security.Permissions.SecurityPermissionFlag> uprawnienie, dostępu, a następnie skrypt w arkuszu stylów nigdy nie zostanie skompilowany i wywołania <xref:System.Xml.Xsl.XslTransform.Load%2A> zakończy się niepowodzeniem.</span><span class="sxs-lookup"><span data-stu-id="04332-119">If the caller of the script does not have <xref:System.Security.Permissions.SecurityPermissionFlag> access permission, then the script in a style sheet will never compile and the call to <xref:System.Xml.Xsl.XslTransform.Load%2A> will fail.</span></span>  
  
 <span data-ttu-id="04332-120">Jeśli obiekt wywołujący ma `UnmanagedCode` kompiluje skrypt uprawnienia, ale operacje, które są dozwolone są zależne od dowodów, która jest dostarczana w czasie ładowania.</span><span class="sxs-lookup"><span data-stu-id="04332-120">If the caller has `UnmanagedCode` permission, the script compiles, but the operations that are allowed are dependent on the evidence that is supplied at load time.</span></span>  
  
 <span data-ttu-id="04332-121">Jeśli używasz jednego z <xref:System.Xml.Xsl.XslTransform.Load%2A> metod, które przyjmują <xref:System.Xml.XmlReader> lub <xref:System.Xml.XPath.XPathNavigator> można załadować arkusza stylów, należy użyć <xref:System.Xml.Xsl.XslTransform.Load%2A> przeciążenia przyjmującego <xref:System.Security.Policy.Evidence> parametru jako jeden z argumentów.</span><span class="sxs-lookup"><span data-stu-id="04332-121">If you are using one of the <xref:System.Xml.Xsl.XslTransform.Load%2A> methods that take an <xref:System.Xml.XmlReader> or <xref:System.Xml.XPath.XPathNavigator> to load the style sheet, you need to use the <xref:System.Xml.Xsl.XslTransform.Load%2A> overload that takes an <xref:System.Security.Policy.Evidence> parameter as one of its arguments.</span></span> <span data-ttu-id="04332-122">Aby przedstawić dowód na to, wywołujący musi mieć <xref:System.Security.Permissions.SecurityPermissionFlag> uprawnień, aby dostarczyć `Evidence` dla zestawu skryptów.</span><span class="sxs-lookup"><span data-stu-id="04332-122">To provide evidence, the caller must have <xref:System.Security.Permissions.SecurityPermissionFlag> permission to supply `Evidence` for the script assembly.</span></span> <span data-ttu-id="04332-123">Jeśli obiekt wywołujący nie ma tego uprawnienia, a następnie mogą oni ustawić `Evidence` parametr `null`.</span><span class="sxs-lookup"><span data-stu-id="04332-123">If the caller does not have this permission, then they can set the `Evidence` parameter to `null`.</span></span> <span data-ttu-id="04332-124">Powoduje to, że <xref:System.Xml.Xsl.XslTransform.Load%2A> funkcję, aby zakończyć się niepowodzeniem, jeśli znajdzie skryptu.</span><span class="sxs-lookup"><span data-stu-id="04332-124">This causes the <xref:System.Xml.Xsl.XslTransform.Load%2A> function to fail if it finds script.</span></span> <span data-ttu-id="04332-125">`ControlEvidence` Uprawnienie jest uznawany za bardzo zaawansowane uprawnienia, które powinny być przyznawane tylko do wysoce zaufanym kodem.</span><span class="sxs-lookup"><span data-stu-id="04332-125">The `ControlEvidence` permission is considered a very powerful permission that should only be granted to highly trusted code.</span></span>  
  
 <span data-ttu-id="04332-126">Aby uzyskać dowód z zestawu, należy użyć `this.GetType().Assembly.Evidence`.</span><span class="sxs-lookup"><span data-stu-id="04332-126">To get the evidence from your assembly, use `this.GetType().Assembly.Evidence`.</span></span> <span data-ttu-id="04332-127">Aby uzyskać dowód z jednolite zasobów identyfikator (URI), użyj `Evidence e = XmlSecureResolver.CreateEvidenceForUrl(stylesheetURI)`.</span><span class="sxs-lookup"><span data-stu-id="04332-127">To get the evidence from a Uniform Resource Identifier (URI), use `Evidence e = XmlSecureResolver.CreateEvidenceForUrl(stylesheetURI)`.</span></span>  
  
 <span data-ttu-id="04332-128">Jeśli używasz <xref:System.Xml.Xsl.XslTransform.Load%2A> metod, które przyjmują <xref:System.Xml.XmlResolver> , ale nie `Evidence`, wartością domyślną pełnego zaufania strefie zabezpieczeń dla zestawu.</span><span class="sxs-lookup"><span data-stu-id="04332-128">If you use <xref:System.Xml.Xsl.XslTransform.Load%2A> methods that take an <xref:System.Xml.XmlResolver> but no `Evidence`, the security zone for the assembly defaults to Full Trust.</span></span> <span data-ttu-id="04332-129">Aby uzyskać więcej informacji, zobacz <xref:System.Security.SecurityZone> i [nazwanych zestawów uprawnień](https://msdn.microsoft.com/library/08250d67-c99d-4ab0-8d2b-b0e12019f6e3).</span><span class="sxs-lookup"><span data-stu-id="04332-129">For more information, see <xref:System.Security.SecurityZone> and [Named Permission Sets](https://msdn.microsoft.com/library/08250d67-c99d-4ab0-8d2b-b0e12019f6e3).</span></span>  
  
 <span data-ttu-id="04332-130">Funkcje mogą być zadeklarowane w obrębie `msxsl:script` elementu.</span><span class="sxs-lookup"><span data-stu-id="04332-130">Functions can be declared within the `msxsl:script` element.</span></span> <span data-ttu-id="04332-131">W poniższej tabeli przedstawiono przestrzenie nazw, które są obsługiwane przez domyślny.</span><span class="sxs-lookup"><span data-stu-id="04332-131">The following table shows the namespaces that are supported by default.</span></span> <span data-ttu-id="04332-132">Można użyć klas spoza listy obszarów nazw.</span><span class="sxs-lookup"><span data-stu-id="04332-132">You can use classes outside the listed namespaces.</span></span> <span data-ttu-id="04332-133">Jednak te klasy musi być w pełni kwalifikowana.</span><span class="sxs-lookup"><span data-stu-id="04332-133">However, these classes must be fully qualified.</span></span>  
  
|<span data-ttu-id="04332-134">Domyślne obszary nazw</span><span class="sxs-lookup"><span data-stu-id="04332-134">Default Namespaces</span></span>|<span data-ttu-id="04332-135">Opis</span><span class="sxs-lookup"><span data-stu-id="04332-135">Description</span></span>|  
|------------------------|-----------------|  
|<span data-ttu-id="04332-136">System</span><span class="sxs-lookup"><span data-stu-id="04332-136">System</span></span>|<span data-ttu-id="04332-137">Klasa systemu.</span><span class="sxs-lookup"><span data-stu-id="04332-137">System class.</span></span>|  
|<span data-ttu-id="04332-138">System.Collection</span><span class="sxs-lookup"><span data-stu-id="04332-138">System.Collection</span></span>|<span data-ttu-id="04332-139">Klasy kolekcji.</span><span class="sxs-lookup"><span data-stu-id="04332-139">Collection classes.</span></span>|  
|<span data-ttu-id="04332-140">System.Text</span><span class="sxs-lookup"><span data-stu-id="04332-140">System.Text</span></span>|<span data-ttu-id="04332-141">Klasy tekstu.</span><span class="sxs-lookup"><span data-stu-id="04332-141">Text classes.</span></span>|  
|<span data-ttu-id="04332-142">System.Text.RegularExpressions</span><span class="sxs-lookup"><span data-stu-id="04332-142">System.Text.RegularExpressions</span></span>|<span data-ttu-id="04332-143">Klasy wyrażeń regularnych.</span><span class="sxs-lookup"><span data-stu-id="04332-143">Regular expression classes.</span></span>|  
|<span data-ttu-id="04332-144">System.Xml</span><span class="sxs-lookup"><span data-stu-id="04332-144">System.Xml</span></span>|<span data-ttu-id="04332-145">Podstawowe klasy XML.</span><span class="sxs-lookup"><span data-stu-id="04332-145">Core XML classes.</span></span>|  
|<span data-ttu-id="04332-146">System.Xml.Xsl</span><span class="sxs-lookup"><span data-stu-id="04332-146">System.Xml.Xsl</span></span>|<span data-ttu-id="04332-147">Klasy XSLT.</span><span class="sxs-lookup"><span data-stu-id="04332-147">XSLT classes.</span></span>|  
|<span data-ttu-id="04332-148">System.Xml.XPath</span><span class="sxs-lookup"><span data-stu-id="04332-148">System.Xml.XPath</span></span>|<span data-ttu-id="04332-149">Klasy XML Path Language (XPath).</span><span class="sxs-lookup"><span data-stu-id="04332-149">XML Path Language (XPath) classes.</span></span>|  
|<span data-ttu-id="04332-150">Microsoft.VisualBasic</span><span class="sxs-lookup"><span data-stu-id="04332-150">Microsoft.VisualBasic</span></span>|<span data-ttu-id="04332-151">Klasy dla skryptów programu Microsoft Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="04332-151">Classes for Microsoft Visual Basic scripts.</span></span>|  
  
 <span data-ttu-id="04332-152">Gdy funkcja jest zadeklarowana, znajduje się w bloku skryptu.</span><span class="sxs-lookup"><span data-stu-id="04332-152">When a function is declared, it is contained in a script block.</span></span> <span data-ttu-id="04332-153">Arkusze stylów może zawierać wiele Bloki skryptu, każdy niezależnego innych.</span><span class="sxs-lookup"><span data-stu-id="04332-153">Style sheets can contain multiple script blocks, each operating independent of the other.</span></span> <span data-ttu-id="04332-154">Oznacza to, że jeśli wykonujesz wewnątrz bloku skryptu, nie można wywołać funkcję zdefiniowaną w innego bloku skryptu, o ile nie jest zadeklarowany ma ten sam język skryptów i tej samej przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="04332-154">That means that if you are executing inside a script block, you cannot call a function that you defined in another script block unless it is declared to have the same namespace and the same scripting language.</span></span> <span data-ttu-id="04332-155">Ponieważ każdy blok skryptu może znajdować się w jego własnej języka i bloku jest analizowany zgodnie z regułami gramatyki tego analizatora języka, należy użyć składni poprawne dla języka w użyciu.</span><span class="sxs-lookup"><span data-stu-id="04332-155">Because each script block can be in its own language, and the block is parsed according to the grammar rules of that language parser, you must use the correct syntax for the language in use.</span></span> <span data-ttu-id="04332-156">Na przykład, jeśli jesteś w bloku skryptu C#, wówczas jest błąd za pomocą węzła komentarz XML `<!-- an XML comment -->` w bloku.</span><span class="sxs-lookup"><span data-stu-id="04332-156">For example, if you are in a C# script block, then it is an error to use an XML comment node `<!-- an XML comment -->` in the block.</span></span>  
  
 <span data-ttu-id="04332-157">Podanych argumentów i wartości zwracane definicją funkcji skryptu musi być jednym z typów XPath World Wide Web Consortium (W3C) lub XSLT.</span><span class="sxs-lookup"><span data-stu-id="04332-157">The supplied arguments and return values defined by the script functions must be one of the World Wide Web Consortium (W3C) XPath or XSLT types.</span></span> <span data-ttu-id="04332-158">W poniższej tabeli przedstawiono odpowiednie typy W3C równoważne .NET Framework klas (typ) i czy W3C, wpisz to wyrażenie XPath typu lub XSLT.</span><span class="sxs-lookup"><span data-stu-id="04332-158">The following table shows the corresponding W3C types, the equivalent .NET Framework classes (Type), and whether the W3C type is an XPath type or XSLT type.</span></span>  
  
|<span data-ttu-id="04332-159">Typ</span><span class="sxs-lookup"><span data-stu-id="04332-159">Type</span></span>|<span data-ttu-id="04332-160">Równoważne .NET Framework klasy (typ)</span><span class="sxs-lookup"><span data-stu-id="04332-160">Equivalent .NET Framework Class (Type)</span></span>|<span data-ttu-id="04332-161">Wyrażenie XPath typu lub XSLT</span><span class="sxs-lookup"><span data-stu-id="04332-161">XPath type or XSLT type</span></span>|  
|----------|----------------------------------------------|-----------------------------|  
|<span data-ttu-id="04332-162">String</span><span class="sxs-lookup"><span data-stu-id="04332-162">String</span></span>|<span data-ttu-id="04332-163">System.String</span><span class="sxs-lookup"><span data-stu-id="04332-163">System.String</span></span>|<span data-ttu-id="04332-164">XPath</span><span class="sxs-lookup"><span data-stu-id="04332-164">XPath</span></span>|  
|<span data-ttu-id="04332-165">Boolean</span><span class="sxs-lookup"><span data-stu-id="04332-165">Boolean</span></span>|<span data-ttu-id="04332-166">System.Boolean</span><span class="sxs-lookup"><span data-stu-id="04332-166">System.Boolean</span></span>|<span data-ttu-id="04332-167">XPath</span><span class="sxs-lookup"><span data-stu-id="04332-167">XPath</span></span>|  
|<span data-ttu-id="04332-168">Wartość liczbowa</span><span class="sxs-lookup"><span data-stu-id="04332-168">Number</span></span>|<span data-ttu-id="04332-169">System.Double</span><span class="sxs-lookup"><span data-stu-id="04332-169">System.Double</span></span>|<span data-ttu-id="04332-170">XPath</span><span class="sxs-lookup"><span data-stu-id="04332-170">XPath</span></span>|  
|<span data-ttu-id="04332-171">Wynikowego fragmentu drzewa</span><span class="sxs-lookup"><span data-stu-id="04332-171">Result Tree Fragment</span></span>|<span data-ttu-id="04332-172">System.Xml.XPath.XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="04332-172">System.Xml.XPath.XPathNavigator</span></span>|<span data-ttu-id="04332-173">XSLT</span><span class="sxs-lookup"><span data-stu-id="04332-173">XSLT</span></span>|  
|<span data-ttu-id="04332-174">Zestaw węzłów</span><span class="sxs-lookup"><span data-stu-id="04332-174">Node Set</span></span>|<span data-ttu-id="04332-175">System.Xml.XPath.XPathNodeIterator</span><span class="sxs-lookup"><span data-stu-id="04332-175">System.Xml.XPath.XPathNodeIterator</span></span>|<span data-ttu-id="04332-176">XPath</span><span class="sxs-lookup"><span data-stu-id="04332-176">XPath</span></span>|  
  
 <span data-ttu-id="04332-177">Jeśli funkcja skryptu korzysta z jednego z następujących typów liczbowych: Int16, UInt16, Int32, UInt32, Int64, UInt64, jednego lub dziesiętnej, jest zmuszony do dwukrotnie, która mapuje do typu number W3C XPath.</span><span class="sxs-lookup"><span data-stu-id="04332-177">If the script function utilizes one of the following numeric types: Int16, UInt16, Int32, UInt32, Int64, UInt64, Single, or Decimal, they are forced to Double, which maps to the W3C XPath type number.</span></span> <span data-ttu-id="04332-178">Wszystkie pozostałe typy będą obowiązkowo przenoszone na ciąg przez wywołanie metody `ToString` metody.</span><span class="sxs-lookup"><span data-stu-id="04332-178">All other types are forced to a string by calling the `ToString` method.</span></span>  
  
 <span data-ttu-id="04332-179">Jeśli funkcja skryptu korzysta z typu innego niż wymienione powyżej lub jeśli funkcja nie kompiluje się kiedy arkusza stylów jest ładowany do <xref:System.Xml.Xsl.XslTransform> obiektu, jest zgłaszany wyjątek.</span><span class="sxs-lookup"><span data-stu-id="04332-179">If the script function utilizes a type other than the ones mentioned above, or if the function does not compile when the style sheet is loaded into the <xref:System.Xml.Xsl.XslTransform> object, an exception is thrown.</span></span>  
  
 <span data-ttu-id="04332-180">Korzystając z `msxsl:script` elementu, zdecydowanie zaleca się że skryptu, niezależnie od języka, można umieścić w sekcji CDATA.</span><span class="sxs-lookup"><span data-stu-id="04332-180">When using the `msxsl:script` element, it is highly recommended that the script, regardless of language, be placed inside a CDATA section.</span></span> <span data-ttu-id="04332-181">Na przykład następujący kody XML pokazuje szablonu sekcji CDATA, w którym znajduje się kod.</span><span class="sxs-lookup"><span data-stu-id="04332-181">For example, the following XML shows the template of the CDATA section where your code is placed.</span></span>  
  
```xml  
<msxsl:script implements-prefix='yourprefix' language='CSharp'>  
    <![CDATA[  
    ... your code here ...  
    ]]>  
</msxsl:script>  
```  
  
 <span data-ttu-id="04332-182">Wysoce zalecane jest aby cała zawartość skryptu były umieszczane w sekcji CDATA, ponieważ operatory, identyfikatory lub ograniczniki dla danego języka ma potencjał jest błędnie zinterpretowana jako XML.</span><span class="sxs-lookup"><span data-stu-id="04332-182">It is highly recommended that all script content be placed in a CDATA section, because operators, identifiers, or delimiters for a given language have the potential of being misinterpreted as XML.</span></span> <span data-ttu-id="04332-183">Poniższy przykład pokazuje użycie operatora logicznego AND w skrypcie.</span><span class="sxs-lookup"><span data-stu-id="04332-183">The following example shows the use of the logical AND operator in script.</span></span>  
  
```xml  
<msxsl:script implements-prefix='yourprefix' language='CSharp>  
    public string book(string abc, string xyz)  
    {  if ((abc== abc)&&(abc== xyz)) return bar+xyz;  
        else return null;  
    }  
</msxsl:script>  
```  
  
 <span data-ttu-id="04332-184">Zgłasza wyjątek, ponieważ takie znaki nie będą miały zmienione znaczenie.</span><span class="sxs-lookup"><span data-stu-id="04332-184">This throws an exception because the ampersands are not escaped.</span></span> <span data-ttu-id="04332-185">Dokument jest ładowany w formacie XML, a nie szczególne traktowanie jest stosowany do tekstu między `msxsl:script` tagi elementów.</span><span class="sxs-lookup"><span data-stu-id="04332-185">The document is loaded as XML, and no special treatment is applied to the text between the `msxsl:script` element tags.</span></span>  
  
## <a name="example"></a><span data-ttu-id="04332-186">Przykład</span><span class="sxs-lookup"><span data-stu-id="04332-186">Example</span></span>  
 <span data-ttu-id="04332-187">W poniższym przykładzie użyto osadzonych skryptów do obliczania obwód koła, biorąc pod uwagę jego usługi radius.</span><span class="sxs-lookup"><span data-stu-id="04332-187">The following example uses an embedded script to calculate the circumference of a circle given its radius.</span></span>  
  
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
  
## <a name="input"></a><span data-ttu-id="04332-188">Dane wejściowe</span><span class="sxs-lookup"><span data-stu-id="04332-188">Input</span></span>  
 <span data-ttu-id="04332-189">number.xml</span><span class="sxs-lookup"><span data-stu-id="04332-189">number.xml</span></span>  
  
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
  
 <span data-ttu-id="04332-190">calc.xsl</span><span class="sxs-lookup"><span data-stu-id="04332-190">calc.xsl</span></span>  
  
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
  
## <a name="output"></a><span data-ttu-id="04332-191">Dane wyjściowe</span><span class="sxs-lookup"><span data-stu-id="04332-191">Output</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="04332-192">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="04332-192">See also</span></span>

- [<span data-ttu-id="04332-193">Implementowanie procesora XSLT przy użyciu klasy XslTransform</span><span class="sxs-lookup"><span data-stu-id="04332-193">XslTransform Class Implements the XSLT Processor</span></span>](../../../../docs/standard/data/xml/xsltransform-class-implements-the-xslt-processor.md)
