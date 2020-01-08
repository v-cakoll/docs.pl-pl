---
title: Wykonywanie skryptów arkusza stylów XSLT przy użyciu elementu <msxsl:script>
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 60e2541b-0cea-4b2e-a4fa-85f4c50f1bef
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 32695d3bc29693ab4cf1e2f9d721d35598ecfb86
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/25/2019
ms.locfileid: "75344716"
---
# <a name="xslt-stylesheet-scripting-using-msxslscript"></a><span data-ttu-id="7de7f-102">Obsługa skryptów arkusza stylów XSLT przy użyciu \<msxsl: skrypt ></span><span class="sxs-lookup"><span data-stu-id="7de7f-102">XSLT Stylesheet Scripting Using \<msxsl:script></span></span>
<span data-ttu-id="7de7f-103">Klasa <xref:System.Xml.Xsl.XslTransform> obsługuje osadzone skrypty przy użyciu elementu `script`.</span><span class="sxs-lookup"><span data-stu-id="7de7f-103">The <xref:System.Xml.Xsl.XslTransform> class supports embedded scripting using the `script` element.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7de7f-104">Klasa <xref:System.Xml.Xsl.XslTransform> jest przestarzała w .NET Framework 2,0.</span><span class="sxs-lookup"><span data-stu-id="7de7f-104">The <xref:System.Xml.Xsl.XslTransform> class is obsolete in the .NET Framework 2.0.</span></span> <span data-ttu-id="7de7f-105">Można wykonywać przekształcenia Extensible Stylesheet Language for Transformations (XSLT) przy użyciu klasy <xref:System.Xml.Xsl.XslCompiledTransform>.</span><span class="sxs-lookup"><span data-stu-id="7de7f-105">You can perform Extensible Stylesheet Language for Transformations (XSLT) transformations using the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span> <span data-ttu-id="7de7f-106">Aby uzyskać więcej informacji, zobacz [Używanie klasy XslCompiledTransform](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) i [Migrowanie z klasy XslTransform](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md) .</span><span class="sxs-lookup"><span data-stu-id="7de7f-106">See [Using the XslCompiledTransform Class](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) and [Migrating From the XslTransform Class](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md) for more information.</span></span>  
  
 <span data-ttu-id="7de7f-107">Klasa <xref:System.Xml.Xsl.XslTransform> obsługuje osadzone skrypty przy użyciu elementu `script`.</span><span class="sxs-lookup"><span data-stu-id="7de7f-107">The <xref:System.Xml.Xsl.XslTransform> class supports embedded scripting using the `script` element.</span></span> <span data-ttu-id="7de7f-108">Po załadowaniu arkusza stylów wszystkie zdefiniowane funkcje są kompilowane do języka pośredniego firmy Microsoft (MSIL) przez zawinięte w definicji klasy i nie mają utraty wydajności w wyniku.</span><span class="sxs-lookup"><span data-stu-id="7de7f-108">When the style sheet is loaded, any defined functions are compiled to Microsoft intermediate language (MSIL) by being wrapped in a class definition and have no performance loss as a result.</span></span>  
  
 <span data-ttu-id="7de7f-109">Element `<msxsl:script>` jest zdefiniowany poniżej:</span><span class="sxs-lookup"><span data-stu-id="7de7f-109">The `<msxsl:script>` element is defined below:</span></span>  
  
```xml  
<msxsl:script language = "language-name" implements-prefix = "prefix of user namespace"> </msxsl:script>  
```  
  
 <span data-ttu-id="7de7f-110">gdzie `msxsl` jest prefiksem powiązanym z przestrzenią nazw `urn:schemas-microsoft-com:xslt`.</span><span class="sxs-lookup"><span data-stu-id="7de7f-110">where `msxsl` is a prefix bound to the namespace `urn:schemas-microsoft-com:xslt`.</span></span>  
  
 <span data-ttu-id="7de7f-111">Atrybut `language` nie jest obowiązkowy, ale jeśli jest określony, jego wartość musi być jedną z następujących: `C#`, `VB`, `JScript`, `JavaScript`, `VisualBasic`lub `CSharp`.</span><span class="sxs-lookup"><span data-stu-id="7de7f-111">The `language` attribute is not mandatory, but if specified, its value must be one of the following: `C#`, `VB`, `JScript`, `JavaScript`, `VisualBasic`, or `CSharp`.</span></span> <span data-ttu-id="7de7f-112">Jeśli nie zostanie określony, język jest wartością domyślną języka JScript.</span><span class="sxs-lookup"><span data-stu-id="7de7f-112">If not specified, the language defaults to JScript.</span></span> <span data-ttu-id="7de7f-113">W `language-name` nie jest rozróżniana wielkość liter, dlatego "JavaScript" i "JavaScript" są równoważne.</span><span class="sxs-lookup"><span data-stu-id="7de7f-113">The `language-name` is not case-sensitive, so 'JavaScript' and 'javascript' are equivalent.</span></span>  
  
 <span data-ttu-id="7de7f-114">Atrybut `implements-prefix` jest obowiązkowy.</span><span class="sxs-lookup"><span data-stu-id="7de7f-114">The `implements-prefix` attribute is mandatory.</span></span> <span data-ttu-id="7de7f-115">Ten atrybut służy do deklarowania przestrzeni nazw i kojarzenia jej z blokiem skryptu.</span><span class="sxs-lookup"><span data-stu-id="7de7f-115">This attribute is used to declare a namespace and associate it with the script block.</span></span> <span data-ttu-id="7de7f-116">Wartość tego atrybutu jest prefiks, który reprezentuje obszar nazw.</span><span class="sxs-lookup"><span data-stu-id="7de7f-116">The value of this attribute is the prefix that represents the namespace.</span></span> <span data-ttu-id="7de7f-117">Ta przestrzeń nazw może być zdefiniowana gdzieś w arkuszu stylów.</span><span class="sxs-lookup"><span data-stu-id="7de7f-117">This namespace can be defined somewhere in a style sheet.</span></span>  
  
 <span data-ttu-id="7de7f-118">Ponieważ element `msxsl:script` należy do `urn:schemas-microsoft-com:xslt`przestrzeni nazw, arkusz stylów musi zawierać deklarację przestrzeni nazw `xmlns:msxsl=urn:schemas-microsoft-com:xslt`.</span><span class="sxs-lookup"><span data-stu-id="7de7f-118">Because the `msxsl:script` element belongs to the namespace `urn:schemas-microsoft-com:xslt`, the style sheet must include the namespace declaration `xmlns:msxsl=urn:schemas-microsoft-com:xslt`.</span></span>  
  
 <span data-ttu-id="7de7f-119">Jeśli obiekt wywołujący skryptu nie ma uprawnienia dostępu <xref:System.Security.Permissions.SecurityPermissionFlag>, skrypt w arkuszu stylów nigdy nie zostanie skompilowany i wywołanie <xref:System.Xml.Xsl.XslTransform.Load%2A> zakończy się niepowodzeniem.</span><span class="sxs-lookup"><span data-stu-id="7de7f-119">If the caller of the script does not have <xref:System.Security.Permissions.SecurityPermissionFlag> access permission, then the script in a style sheet will never compile and the call to <xref:System.Xml.Xsl.XslTransform.Load%2A> will fail.</span></span>  
  
 <span data-ttu-id="7de7f-120">Jeśli obiekt wywołujący ma uprawnienia `UnmanagedCode`, skrypt kompiluje, ale operacje, które są dozwolone, są zależne od dowodów dostarczonych w czasie ładowania.</span><span class="sxs-lookup"><span data-stu-id="7de7f-120">If the caller has `UnmanagedCode` permission, the script compiles, but the operations that are allowed are dependent on the evidence that is supplied at load time.</span></span>  
  
 <span data-ttu-id="7de7f-121">Jeśli używasz jednej z <xref:System.Xml.Xsl.XslTransform.Load%2A> metod, które przyjmują <xref:System.Xml.XmlReader> lub <xref:System.Xml.XPath.XPathNavigator> do załadowania arkusza stylów, musisz użyć przeciążenia <xref:System.Xml.Xsl.XslTransform.Load%2A>, które przyjmuje parametr <xref:System.Security.Policy.Evidence> jako jeden z argumentów.</span><span class="sxs-lookup"><span data-stu-id="7de7f-121">If you are using one of the <xref:System.Xml.Xsl.XslTransform.Load%2A> methods that take an <xref:System.Xml.XmlReader> or <xref:System.Xml.XPath.XPathNavigator> to load the style sheet, you need to use the <xref:System.Xml.Xsl.XslTransform.Load%2A> overload that takes an <xref:System.Security.Policy.Evidence> parameter as one of its arguments.</span></span> <span data-ttu-id="7de7f-122">Aby zapewnić dowód, obiekt wywołujący musi mieć uprawnienie <xref:System.Security.Permissions.SecurityPermissionFlag>, aby dostarczyć `Evidence` do zestawu skryptu.</span><span class="sxs-lookup"><span data-stu-id="7de7f-122">To provide evidence, the caller must have <xref:System.Security.Permissions.SecurityPermissionFlag> permission to supply `Evidence` for the script assembly.</span></span> <span data-ttu-id="7de7f-123">Jeśli obiekt wywołujący nie ma tego uprawnienia, można ustawić parametr `Evidence`, aby `null`.</span><span class="sxs-lookup"><span data-stu-id="7de7f-123">If the caller does not have this permission, then they can set the `Evidence` parameter to `null`.</span></span> <span data-ttu-id="7de7f-124">Powoduje to, że funkcja <xref:System.Xml.Xsl.XslTransform.Load%2A> nie powiedzie się, jeśli znajdzie skrypt.</span><span class="sxs-lookup"><span data-stu-id="7de7f-124">This causes the <xref:System.Xml.Xsl.XslTransform.Load%2A> function to fail if it finds script.</span></span> <span data-ttu-id="7de7f-125">Uprawnienia `ControlEvidence` są uznawane za bardzo zaawansowane uprawnienia, które powinny być przyznawane tylko do wysoce zaufanego kodu.</span><span class="sxs-lookup"><span data-stu-id="7de7f-125">The `ControlEvidence` permission is considered a very powerful permission that should only be granted to highly trusted code.</span></span>  
  
 <span data-ttu-id="7de7f-126">Aby uzyskać dowody z Twojego zestawu, użyj `this.GetType().Assembly.Evidence`.</span><span class="sxs-lookup"><span data-stu-id="7de7f-126">To get the evidence from your assembly, use `this.GetType().Assembly.Evidence`.</span></span> <span data-ttu-id="7de7f-127">Aby uzyskać dowód z Uniform Resource Identifier (URI), użyj `Evidence e = XmlSecureResolver.CreateEvidenceForUrl(stylesheetURI)`.</span><span class="sxs-lookup"><span data-stu-id="7de7f-127">To get the evidence from a Uniform Resource Identifier (URI), use `Evidence e = XmlSecureResolver.CreateEvidenceForUrl(stylesheetURI)`.</span></span>  
  
 <span data-ttu-id="7de7f-128">W przypadku korzystania z <xref:System.Xml.Xsl.XslTransform.Load%2A> metod, które przyjmują <xref:System.Xml.XmlResolver>, ale nie `Evidence`, Strefa zabezpieczeń dla zestawu domyślnie ma wartość pełne zaufanie.</span><span class="sxs-lookup"><span data-stu-id="7de7f-128">If you use <xref:System.Xml.Xsl.XslTransform.Load%2A> methods that take an <xref:System.Xml.XmlResolver> but no `Evidence`, the security zone for the assembly defaults to Full Trust.</span></span> <span data-ttu-id="7de7f-129">Aby uzyskać więcej informacji, zobacz <xref:System.Security.SecurityZone> i [nazwane zestawy uprawnień](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/4652tyx7(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="7de7f-129">For more information, see <xref:System.Security.SecurityZone> and [Named Permission Sets](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/4652tyx7(v=vs.100)).</span></span>  
  
 <span data-ttu-id="7de7f-130">Funkcje mogą być deklarowane w obrębie elementu `msxsl:script`.</span><span class="sxs-lookup"><span data-stu-id="7de7f-130">Functions can be declared within the `msxsl:script` element.</span></span> <span data-ttu-id="7de7f-131">W poniższej tabeli przedstawiono przestrzenie nazw, które są obsługiwane domyślnie.</span><span class="sxs-lookup"><span data-stu-id="7de7f-131">The following table shows the namespaces that are supported by default.</span></span> <span data-ttu-id="7de7f-132">Można używać klas poza wymienionymi obszarami nazw.</span><span class="sxs-lookup"><span data-stu-id="7de7f-132">You can use classes outside the listed namespaces.</span></span> <span data-ttu-id="7de7f-133">Jednak te klasy muszą być w pełni kwalifikowane.</span><span class="sxs-lookup"><span data-stu-id="7de7f-133">However, these classes must be fully qualified.</span></span>  
  
|<span data-ttu-id="7de7f-134">Domyślne przestrzenie nazw</span><span class="sxs-lookup"><span data-stu-id="7de7f-134">Default Namespaces</span></span>|<span data-ttu-id="7de7f-135">Opis</span><span class="sxs-lookup"><span data-stu-id="7de7f-135">Description</span></span>|  
|------------------------|-----------------|  
|<span data-ttu-id="7de7f-136">System</span><span class="sxs-lookup"><span data-stu-id="7de7f-136">System</span></span>|<span data-ttu-id="7de7f-137">Klasy systemowej.</span><span class="sxs-lookup"><span data-stu-id="7de7f-137">System class.</span></span>|  
|<span data-ttu-id="7de7f-138">System.Collection</span><span class="sxs-lookup"><span data-stu-id="7de7f-138">System.Collection</span></span>|<span data-ttu-id="7de7f-139">Klasy kolekcji.</span><span class="sxs-lookup"><span data-stu-id="7de7f-139">Collection classes.</span></span>|  
|<span data-ttu-id="7de7f-140">System.Text</span><span class="sxs-lookup"><span data-stu-id="7de7f-140">System.Text</span></span>|<span data-ttu-id="7de7f-141">Klasy tekstowe.</span><span class="sxs-lookup"><span data-stu-id="7de7f-141">Text classes.</span></span>|  
|<span data-ttu-id="7de7f-142">System.Text.RegularExpressions</span><span class="sxs-lookup"><span data-stu-id="7de7f-142">System.Text.RegularExpressions</span></span>|<span data-ttu-id="7de7f-143">Klasy wyrażeń regularnych.</span><span class="sxs-lookup"><span data-stu-id="7de7f-143">Regular expression classes.</span></span>|  
|<span data-ttu-id="7de7f-144">System.Xml</span><span class="sxs-lookup"><span data-stu-id="7de7f-144">System.Xml</span></span>|<span data-ttu-id="7de7f-145">Podstawowe klasy XML.</span><span class="sxs-lookup"><span data-stu-id="7de7f-145">Core XML classes.</span></span>|  
|<span data-ttu-id="7de7f-146">System.Xml.Xsl</span><span class="sxs-lookup"><span data-stu-id="7de7f-146">System.Xml.Xsl</span></span>|<span data-ttu-id="7de7f-147">Klasy XSLT.</span><span class="sxs-lookup"><span data-stu-id="7de7f-147">XSLT classes.</span></span>|  
|<span data-ttu-id="7de7f-148">System.Xml.XPath</span><span class="sxs-lookup"><span data-stu-id="7de7f-148">System.Xml.XPath</span></span>|<span data-ttu-id="7de7f-149">Klasy języka XML Path Language (XPath).</span><span class="sxs-lookup"><span data-stu-id="7de7f-149">XML Path Language (XPath) classes.</span></span>|  
|<span data-ttu-id="7de7f-150">Microsoft.VisualBasic</span><span class="sxs-lookup"><span data-stu-id="7de7f-150">Microsoft.VisualBasic</span></span>|<span data-ttu-id="7de7f-151">Klasy dla skryptów Visual Basic firmy Microsoft.</span><span class="sxs-lookup"><span data-stu-id="7de7f-151">Classes for Microsoft Visual Basic scripts.</span></span>|  
  
 <span data-ttu-id="7de7f-152">Gdy funkcja jest zadeklarowana, jest zawarta w bloku skryptu.</span><span class="sxs-lookup"><span data-stu-id="7de7f-152">When a function is declared, it is contained in a script block.</span></span> <span data-ttu-id="7de7f-153">Arkusze stylów mogą zawierać wiele bloków skryptu, z których każda działa niezależnie od siebie.</span><span class="sxs-lookup"><span data-stu-id="7de7f-153">Style sheets can contain multiple script blocks, each operating independent of the other.</span></span> <span data-ttu-id="7de7f-154">Oznacza to, że jeśli wykonujesz wewnątrz bloku skryptu, nie można wywołać funkcji, która została zdefiniowana w innym bloku skryptu, chyba że jest zadeklarowana jako ma tę samą przestrzeń nazw i ten sam język skryptowy.</span><span class="sxs-lookup"><span data-stu-id="7de7f-154">That means that if you are executing inside a script block, you cannot call a function that you defined in another script block unless it is declared to have the same namespace and the same scripting language.</span></span> <span data-ttu-id="7de7f-155">Ponieważ każdy blok skryptu może znajdować się w własnym języku, a blok jest analizowany zgodnie z regułami gramatyki tego parsera języka, należy użyć poprawnej składni dla używanego języka.</span><span class="sxs-lookup"><span data-stu-id="7de7f-155">Because each script block can be in its own language, and the block is parsed according to the grammar rules of that language parser, you must use the correct syntax for the language in use.</span></span> <span data-ttu-id="7de7f-156">Na przykład, jeśli jesteś w bloku C# skryptu, jest to błąd, aby użyć węzła komentarza XML `<!-- an XML comment -->` w bloku.</span><span class="sxs-lookup"><span data-stu-id="7de7f-156">For example, if you are in a C# script block, then it is an error to use an XML comment node `<!-- an XML comment -->` in the block.</span></span>  
  
 <span data-ttu-id="7de7f-157">Podane argumenty i zwracane wartości zdefiniowane przez funkcje skryptów muszą być jednym z typów XPath lub XSLT organizacja World Wide Web Consortium (W3C).</span><span class="sxs-lookup"><span data-stu-id="7de7f-157">The supplied arguments and return values defined by the script functions must be one of the World Wide Web Consortium (W3C) XPath or XSLT types.</span></span> <span data-ttu-id="7de7f-158">W poniższej tabeli przedstawiono odpowiednie typy W3C, równoważne klasy .NET Framework (typ) i określające, czy typ W3C jest typem XPath czy XSLT.</span><span class="sxs-lookup"><span data-stu-id="7de7f-158">The following table shows the corresponding W3C types, the equivalent .NET Framework classes (Type), and whether the W3C type is an XPath type or XSLT type.</span></span>  
  
|<span data-ttu-id="7de7f-159">Typ</span><span class="sxs-lookup"><span data-stu-id="7de7f-159">Type</span></span>|<span data-ttu-id="7de7f-160">Równoważna Klasa .NET Framework (typ)</span><span class="sxs-lookup"><span data-stu-id="7de7f-160">Equivalent .NET Framework Class (Type)</span></span>|<span data-ttu-id="7de7f-161">Typ XPath lub typ XSLT</span><span class="sxs-lookup"><span data-stu-id="7de7f-161">XPath type or XSLT type</span></span>|  
|----------|----------------------------------------------|-----------------------------|  
|<span data-ttu-id="7de7f-162">String</span><span class="sxs-lookup"><span data-stu-id="7de7f-162">String</span></span>|<span data-ttu-id="7de7f-163">System.String</span><span class="sxs-lookup"><span data-stu-id="7de7f-163">System.String</span></span>|<span data-ttu-id="7de7f-164">{1&gt;XPath&lt;1}</span><span class="sxs-lookup"><span data-stu-id="7de7f-164">XPath</span></span>|  
|<span data-ttu-id="7de7f-165">Boolean</span><span class="sxs-lookup"><span data-stu-id="7de7f-165">Boolean</span></span>|<span data-ttu-id="7de7f-166">System.Boolean</span><span class="sxs-lookup"><span data-stu-id="7de7f-166">System.Boolean</span></span>|<span data-ttu-id="7de7f-167">{1&gt;XPath&lt;1}</span><span class="sxs-lookup"><span data-stu-id="7de7f-167">XPath</span></span>|  
|<span data-ttu-id="7de7f-168">Wartość liczbowa</span><span class="sxs-lookup"><span data-stu-id="7de7f-168">Number</span></span>|<span data-ttu-id="7de7f-169">System.Double</span><span class="sxs-lookup"><span data-stu-id="7de7f-169">System.Double</span></span>|<span data-ttu-id="7de7f-170">{1&gt;XPath&lt;1}</span><span class="sxs-lookup"><span data-stu-id="7de7f-170">XPath</span></span>|  
|<span data-ttu-id="7de7f-171">Fragment drzewa wyników</span><span class="sxs-lookup"><span data-stu-id="7de7f-171">Result Tree Fragment</span></span>|<span data-ttu-id="7de7f-172">System.Xml.XPath.XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="7de7f-172">System.Xml.XPath.XPathNavigator</span></span>|<span data-ttu-id="7de7f-173">XSLT</span><span class="sxs-lookup"><span data-stu-id="7de7f-173">XSLT</span></span>|  
|<span data-ttu-id="7de7f-174">Zestaw węzłów</span><span class="sxs-lookup"><span data-stu-id="7de7f-174">Node Set</span></span>|<span data-ttu-id="7de7f-175">System.Xml.XPath.XPathNodeIterator</span><span class="sxs-lookup"><span data-stu-id="7de7f-175">System.Xml.XPath.XPathNodeIterator</span></span>|<span data-ttu-id="7de7f-176">{1&gt;XPath&lt;1}</span><span class="sxs-lookup"><span data-stu-id="7de7f-176">XPath</span></span>|  
  
 <span data-ttu-id="7de7f-177">Jeśli funkcja skryptu używa jednego z następujących typów liczbowych: Int16, UInt16, Int32, UInt32, Int64, UInt64, Single lub decimal, są one wymuszane jako podwójne, które mapuje do typu W3C XPath.</span><span class="sxs-lookup"><span data-stu-id="7de7f-177">If the script function utilizes one of the following numeric types: Int16, UInt16, Int32, UInt32, Int64, UInt64, Single, or Decimal, they are forced to Double, which maps to the W3C XPath type number.</span></span> <span data-ttu-id="7de7f-178">Wszystkie inne typy są wymuszane jako ciąg wywołujący metodę `ToString`.</span><span class="sxs-lookup"><span data-stu-id="7de7f-178">All other types are forced to a string by calling the `ToString` method.</span></span>  
  
 <span data-ttu-id="7de7f-179">Jeśli funkcja skryptu używa typu innego niż wymienione powyżej, lub jeśli funkcja nie kompiluje się, gdy arkusz stylów jest ładowany do obiektu <xref:System.Xml.Xsl.XslTransform>, zgłaszany jest wyjątek.</span><span class="sxs-lookup"><span data-stu-id="7de7f-179">If the script function utilizes a type other than the ones mentioned above, or if the function does not compile when the style sheet is loaded into the <xref:System.Xml.Xsl.XslTransform> object, an exception is thrown.</span></span>  
  
 <span data-ttu-id="7de7f-180">W przypadku używania elementu `msxsl:script` zdecydowanie zaleca się, aby skrypt niezależnie od języka został umieszczony wewnątrz sekcji CDATA.</span><span class="sxs-lookup"><span data-stu-id="7de7f-180">When using the `msxsl:script` element, it is highly recommended that the script, regardless of language, be placed inside a CDATA section.</span></span> <span data-ttu-id="7de7f-181">Na przykład, poniższy kod XML pokazuje szablon sekcji CDATA, w której umieszczony jest swój plik.</span><span class="sxs-lookup"><span data-stu-id="7de7f-181">For example, the following XML shows the template of the CDATA section where your code is placed.</span></span>  
  
```xml  
<msxsl:script implements-prefix='yourprefix' language='CSharp'>  
    <![CDATA[  
    ... your code here ...  
    ]]>  
</msxsl:script>  
```  
  
 <span data-ttu-id="7de7f-182">Zdecydowanie zaleca się, aby cała zawartość skryptu była umieszczana w sekcji CDATA, ponieważ operatory, identyfikatory lub ograniczniki danego języka mają potencjalną interpretację jako XML.</span><span class="sxs-lookup"><span data-stu-id="7de7f-182">It is highly recommended that all script content be placed in a CDATA section, because operators, identifiers, or delimiters for a given language have the potential of being misinterpreted as XML.</span></span> <span data-ttu-id="7de7f-183">W poniższym przykładzie pokazano użycie operatora logicznego AND w skrypcie.</span><span class="sxs-lookup"><span data-stu-id="7de7f-183">The following example shows the use of the logical AND operator in script.</span></span>  
  
```xml  
<msxsl:script implements-prefix='yourprefix' language='CSharp'>  
    public string book(string abc, string xyz)  
    {  
        if ((abc == bar) && (abc == xyz)) return bar + xyz;  
        else return null;  
    }  
</msxsl:script>  
```  
  
 <span data-ttu-id="7de7f-184">Zgłasza wyjątek, ponieważ znaki handlowe nie są wyprowadzane.</span><span class="sxs-lookup"><span data-stu-id="7de7f-184">This throws an exception because the ampersands are not escaped.</span></span> <span data-ttu-id="7de7f-185">Dokument jest ładowany jako XML i nie jest stosowane żadne specjalne traktowanie do tekstu między tagami elementu `msxsl:script`.</span><span class="sxs-lookup"><span data-stu-id="7de7f-185">The document is loaded as XML, and no special treatment is applied to the text between the `msxsl:script` element tags.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7de7f-186">Przykład</span><span class="sxs-lookup"><span data-stu-id="7de7f-186">Example</span></span>  
 <span data-ttu-id="7de7f-187">W poniższym przykładzie zastosowano osadzony skrypt do obliczenia obwodu okręgu, który ma swój promień.</span><span class="sxs-lookup"><span data-stu-id="7de7f-187">The following example uses an embedded script to calculate the circumference of a circle given its radius.</span></span>  
  
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
  
## <a name="input"></a><span data-ttu-id="7de7f-188">Dane wejściowe</span><span class="sxs-lookup"><span data-stu-id="7de7f-188">Input</span></span>  
 <span data-ttu-id="7de7f-189">number.xml</span><span class="sxs-lookup"><span data-stu-id="7de7f-189">number.xml</span></span>  
  
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
  
 <span data-ttu-id="7de7f-190">calc.xsl</span><span class="sxs-lookup"><span data-stu-id="7de7f-190">calc.xsl</span></span>  
  
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
  
## <a name="output"></a><span data-ttu-id="7de7f-191">Dane wyjściowe</span><span class="sxs-lookup"><span data-stu-id="7de7f-191">Output</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="7de7f-192">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7de7f-192">See also</span></span>

- [<span data-ttu-id="7de7f-193">Implementowanie procesora XSLT przy użyciu klasy XslTransform</span><span class="sxs-lookup"><span data-stu-id="7de7f-193">XslTransform Class Implements the XSLT Processor</span></span>](../../../../docs/standard/data/xml/xsltransform-class-implements-the-xslt-processor.md)
