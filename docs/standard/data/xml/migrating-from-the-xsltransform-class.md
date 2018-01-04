---
title: Migrowanie z klasy XslTransform
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
ms.assetid: 9404d758-679f-4ffb-995d-3d07d817659e
caps.latest.revision: "3"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 1fe2848deadd8de4494f485d792604663515686e
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="migrating-from-the-xsltransform-class"></a><span data-ttu-id="f7e5a-102">Migrowanie z klasy XslTransform</span><span class="sxs-lookup"><span data-stu-id="f7e5a-102">Migrating From the XslTransform Class</span></span>
<span data-ttu-id="f7e5a-103">Architektura XSLT został przeprojektowany w [!INCLUDE[vsprvslong](../../../../includes/vsprvslong-md.md)] wersji.</span><span class="sxs-lookup"><span data-stu-id="f7e5a-103">The XSLT architecture was redesigned in the [!INCLUDE[vsprvslong](../../../../includes/vsprvslong-md.md)] release.</span></span> <span data-ttu-id="f7e5a-104"><xref:System.Xml.Xsl.XslTransform> Klasa została zastąpiona przez <xref:System.Xml.Xsl.XslCompiledTransform> klasy.</span><span class="sxs-lookup"><span data-stu-id="f7e5a-104">The <xref:System.Xml.Xsl.XslTransform> class has been replaced by the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span>  
  
 <span data-ttu-id="f7e5a-105">W poniższych sekcjach opisano niektóre główne różnice między <xref:System.Xml.Xsl.XslCompiledTransform> i <xref:System.Xml.Xsl.XslTransform> klasy.</span><span class="sxs-lookup"><span data-stu-id="f7e5a-105">The following sections describe some of the main differences between the <xref:System.Xml.Xsl.XslCompiledTransform> and the <xref:System.Xml.Xsl.XslTransform> classes.</span></span>  
  
## <a name="performance"></a><span data-ttu-id="f7e5a-106">Wydajność</span><span class="sxs-lookup"><span data-stu-id="f7e5a-106">Performance</span></span>  
 <span data-ttu-id="f7e5a-107"><xref:System.Xml.Xsl.XslCompiledTransform> Klasa zawiera wiele ulepszeń wydajności.</span><span class="sxs-lookup"><span data-stu-id="f7e5a-107">The <xref:System.Xml.Xsl.XslCompiledTransform> class includes many performance improvements.</span></span> <span data-ttu-id="f7e5a-108">Nowe procesorze XSLT kompiluje arkusz stylów XSLT do wspólnego formatu pośredniego, podobnie jak w przypadku języków programowania czego środowisko uruchomieniowe języka wspólnego (CLR).</span><span class="sxs-lookup"><span data-stu-id="f7e5a-108">The new XSLT processor compiles the XSLT style sheet down to a common intermediate format, similar to what the common language runtime (CLR) does for other programming languages.</span></span> <span data-ttu-id="f7e5a-109">Gdy arkusz stylów jest kompilowana, można w pamięci podręcznej i ponownie.</span><span class="sxs-lookup"><span data-stu-id="f7e5a-109">Once the style sheet is compiled, it can be cached and reused.</span></span>  
  
 <span data-ttu-id="f7e5a-110"><xref:System.Xml.Xsl.XslCompiledTransform> Klasa zawiera również inne funkcje optymalizacji, które ułatwiają znacznie szybsze niż <xref:System.Xml.Xsl.XslTransform> klasy.</span><span class="sxs-lookup"><span data-stu-id="f7e5a-110">The <xref:System.Xml.Xsl.XslCompiledTransform> class also includes other optimizations that make it much faster than the <xref:System.Xml.Xsl.XslTransform> class.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f7e5a-111">Mimo że ogólną wydajność <xref:System.Xml.Xsl.XslCompiledTransform> klasy jest lepszym rozwiązaniem niż <xref:System.Xml.Xsl.XslTransform> klasy, <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> metody <xref:System.Xml.Xsl.XslCompiledTransform> klasy może zapewnić więcej wolniej niż <xref:System.Xml.Xsl.XslTransform.Load%2A> metody <xref:System.Xml.Xsl.XslTransform> klasy pierwszy czasu wywoływana jest transformację.</span><span class="sxs-lookup"><span data-stu-id="f7e5a-111">Although the overall performance of the <xref:System.Xml.Xsl.XslCompiledTransform> class is better than the <xref:System.Xml.Xsl.XslTransform> class, the <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> method of the <xref:System.Xml.Xsl.XslCompiledTransform> class might perform more slowly than the <xref:System.Xml.Xsl.XslTransform.Load%2A> method of the <xref:System.Xml.Xsl.XslTransform> class the first time it is called on a transformation.</span></span> <span data-ttu-id="f7e5a-112">Jest to spowodowane musi zostać skompilowany plik XSLT, przed jego załadowaniem.</span><span class="sxs-lookup"><span data-stu-id="f7e5a-112">This is because the XSLT file must be compiled before it is loaded.</span></span> <span data-ttu-id="f7e5a-113">Aby uzyskać więcej informacji, zobacz następującym wpisie w blogu: [XslCompiledTransform wolniej niż XslTransform?](http://go.microsoft.com/fwlink/?LinkId=130590)</span><span class="sxs-lookup"><span data-stu-id="f7e5a-113">For more information, see the following blog post: [XslCompiledTransform Slower than XslTransform?](http://go.microsoft.com/fwlink/?LinkId=130590)</span></span>  
  
## <a name="security"></a><span data-ttu-id="f7e5a-114">Zabezpieczenia</span><span class="sxs-lookup"><span data-stu-id="f7e5a-114">Security</span></span>  
 <span data-ttu-id="f7e5a-115">Domyślnie <xref:System.Xml.Xsl.XslCompiledTransform> klasy wyłącza obsługę XSLT `document()` funkcji i osadzonych skryptów.</span><span class="sxs-lookup"><span data-stu-id="f7e5a-115">By default, the <xref:System.Xml.Xsl.XslCompiledTransform> class disables support for the XSLT `document()` function and embedded scripting.</span></span> <span data-ttu-id="f7e5a-116">Te funkcje można włączyć, tworząc <xref:System.Xml.Xsl.XsltSettings> obiektu, który ma funkcje włączone i nastąpiło przejście do <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="f7e5a-116">These features can be enabled by creating an <xref:System.Xml.Xsl.XsltSettings> object that has the features enabled and passing it to the <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> method.</span></span> <span data-ttu-id="f7e5a-117">Poniższy przykład pokazuje, jak włączyć obsługę skryptów i przekształcenie XSLT.</span><span class="sxs-lookup"><span data-stu-id="f7e5a-117">The following example shows how to enable scripting and perform an XSLT transformation.</span></span>  
  
 [!code-csharp[XML_Migration#16](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#16)]
 [!code-vb[XML_Migration#16](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#16)]  
  
 <span data-ttu-id="f7e5a-118">Aby uzyskać więcej informacji, zobacz [zagadnienia dotyczące zabezpieczeń XSLT](../../../../docs/standard/data/xml/xslt-security-considerations.md).</span><span class="sxs-lookup"><span data-stu-id="f7e5a-118">For more information, see [XSLT Security Considerations](../../../../docs/standard/data/xml/xslt-security-considerations.md).</span></span>  
  
## <a name="new-features"></a><span data-ttu-id="f7e5a-119">Nowe funkcje</span><span class="sxs-lookup"><span data-stu-id="f7e5a-119">New Features</span></span>  
  
### <a name="temporary-files"></a><span data-ttu-id="f7e5a-120">Pliki tymczasowe</span><span class="sxs-lookup"><span data-stu-id="f7e5a-120">Temporary Files</span></span>  
 <span data-ttu-id="f7e5a-121">Pliki tymczasowe czasami są generowane podczas XSLT przetwarzania.</span><span class="sxs-lookup"><span data-stu-id="f7e5a-121">Temporary files are sometimes generated during XSLT processing.</span></span> <span data-ttu-id="f7e5a-122">Jeśli arkusz stylów zawiera bloki skryptu lub jest on skompilowany z wartością ustawienia debugowania można tworzyć wartość true, tymczasowe pliki w folderze % TEMP %.</span><span class="sxs-lookup"><span data-stu-id="f7e5a-122">If a style sheet contains script blocks, or if it is compiled with the debug setting set to true, temporary files may be created in the %TEMP% folder.</span></span> <span data-ttu-id="f7e5a-123">Mogą wystąpić sytuacje, gdy niektóre pliki tymczasowe nie są usuwane ze względu na problemy dotyczące synchronizacji.</span><span class="sxs-lookup"><span data-stu-id="f7e5a-123">There may be instances when some temporary files are not deleted due to timing issues.</span></span> <span data-ttu-id="f7e5a-124">Na przykład, jeśli pliki znajdują się w używany w bieżącym elemencie AppDomain lub przez debuger finalizatora <xref:System.CodeDom.Compiler.TempFileCollection> obiektu nie będzie można je usunąć.</span><span class="sxs-lookup"><span data-stu-id="f7e5a-124">For example, if the files are in use by the current AppDomain or by the debugger, the finalizer of the <xref:System.CodeDom.Compiler.TempFileCollection> object will not be able to remove them.</span></span>  
  
 <span data-ttu-id="f7e5a-125"><xref:System.Xml.Xsl.XslCompiledTransform.TemporaryFiles%2A> Właściwości umożliwia dodatkowe oczyszczania upewnij się, że wszystkie pliki tymczasowe są usuwane z klienta.</span><span class="sxs-lookup"><span data-stu-id="f7e5a-125">The <xref:System.Xml.Xsl.XslCompiledTransform.TemporaryFiles%2A> property can be used for additional cleanup to make sure that all temporary files are removed from the client.</span></span>  
  
### <a name="support-for-the-xsloutput-element-and-xmlwriter"></a><span data-ttu-id="f7e5a-126">Obsługa elementu xsl: Output i XmlWriter</span><span class="sxs-lookup"><span data-stu-id="f7e5a-126">Support for the xsl:output Element and XmlWriter</span></span>  
 <span data-ttu-id="f7e5a-127"><xref:System.Xml.Xsl.XslTransform> Klasy ignorowane `xsl:output` ustawień, gdy przekształcenie dane wyjściowe zostały wysłane do <xref:System.Xml.XmlWriter> obiektu.</span><span class="sxs-lookup"><span data-stu-id="f7e5a-127">The <xref:System.Xml.Xsl.XslTransform> class ignored `xsl:output` settings when the transform output was sent to an <xref:System.Xml.XmlWriter> object.</span></span> <span data-ttu-id="f7e5a-128"><xref:System.Xml.Xsl.XslCompiledTransform> Klasa ma <xref:System.Xml.Xsl.XslCompiledTransform.OutputSettings%2A> właściwości, która zwraca <xref:System.Xml.XmlWriterSettings> obiekt zawierający dane wyjściowe pochodzące z `xsl:output` element arkusza stylów.</span><span class="sxs-lookup"><span data-stu-id="f7e5a-128">The <xref:System.Xml.Xsl.XslCompiledTransform> class has an <xref:System.Xml.Xsl.XslCompiledTransform.OutputSettings%2A> property that returns an <xref:System.Xml.XmlWriterSettings> object containing the output information derived from the `xsl:output` element of the style sheet.</span></span> <span data-ttu-id="f7e5a-129"><xref:System.Xml.XmlWriterSettings> Obiekt jest używany do tworzenia <xref:System.Xml.XmlWriter> obiektu o poprawne ustawienia, które mogą zostać przekazane do <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="f7e5a-129">The <xref:System.Xml.XmlWriterSettings> object is used to create an <xref:System.Xml.XmlWriter> object with the correct settings that can be passed to the <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> method.</span></span> <span data-ttu-id="f7e5a-130">Poniższy kod C# ilustruje tego zachowania:</span><span class="sxs-lookup"><span data-stu-id="f7e5a-130">The following C# code illustrates this behavior:</span></span>  
  
```  
// Create the XslTransform object and load the style sheet.  
XslCompiledTransform xslt = new XslCompiledTransform();  
xslt.Load(stylesheet);  
  
// Load the file to transform.  
XPathDocument doc = new XPathDocument(filename);  
  
// Create the writer.  
XmlWriter writer = XmlWriter.Create(Console.Out, xslt.OutputSettings);  
  
// Transform the file and send the output to the console.  
xslt.Transform(doc, writer);  
writer.Close();  
```  
  
### <a name="debug-option"></a><span data-ttu-id="f7e5a-131">Debug — opcja</span><span class="sxs-lookup"><span data-stu-id="f7e5a-131">Debug Option</span></span>  
 <span data-ttu-id="f7e5a-132"><xref:System.Xml.Xsl.XslCompiledTransform> Klasy mogą generować informacji o debugowaniu, dzięki czemu można debugować arkusz stylów z firmą Microsoft [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] debugera.</span><span class="sxs-lookup"><span data-stu-id="f7e5a-132">The <xref:System.Xml.Xsl.XslCompiledTransform> class can generate debug information, which enables you to debug the style sheet with the Microsoft [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] Debugger.</span></span> <span data-ttu-id="f7e5a-133">Aby uzyskać więcej informacji, zobacz <xref:System.Xml.Xsl.XslCompiledTransform.%23ctor%28System.Boolean%29>.</span><span class="sxs-lookup"><span data-stu-id="f7e5a-133">See <xref:System.Xml.Xsl.XslCompiledTransform.%23ctor%28System.Boolean%29> for more information.</span></span>  
  
## <a name="behavioral-differences"></a><span data-ttu-id="f7e5a-134">Różnice funkcjonalne</span><span class="sxs-lookup"><span data-stu-id="f7e5a-134">Behavioral Differences</span></span>  
  
### <a name="transforming-to-an-xmlreader"></a><span data-ttu-id="f7e5a-135">Przekształcanie na element XmlReader</span><span class="sxs-lookup"><span data-stu-id="f7e5a-135">Transforming to an XmlReader</span></span>  
 <span data-ttu-id="f7e5a-136"><xref:System.Xml.Xsl.XslTransform> Klasa ma kilka przeciążeń przekształcania, które zwracają wyniki w postaci przekształcania <xref:System.Xml.XmlReader> obiektu.</span><span class="sxs-lookup"><span data-stu-id="f7e5a-136">The <xref:System.Xml.Xsl.XslTransform> class has several Transform overloads that return transformation results as an <xref:System.Xml.XmlReader> object.</span></span> <span data-ttu-id="f7e5a-137">Te przeciążenia może służyć do ładowanie wyników transformacji do reprezentacji w pamięci (takie jak <xref:System.Xml.XmlDocument> lub <xref:System.Xml.XPath.XPathDocument>) bez ponoszenia obciążenie serializacji i deserializacji wynikowy kod XML drzewa.</span><span class="sxs-lookup"><span data-stu-id="f7e5a-137">These overloads can be used to load the transformation results into an in-memory representation (such as <xref:System.Xml.XmlDocument> or <xref:System.Xml.XPath.XPathDocument>) without incurring the overhead of serialization and deserialization of the resulting XML tree.</span></span> <span data-ttu-id="f7e5a-138">Poniższy kod C# pokazano, jak można załadować wyników transformacji do <xref:System.Xml.XmlDocument> obiektu.</span><span class="sxs-lookup"><span data-stu-id="f7e5a-138">The following C# code shows how to load the transformation results into an <xref:System.Xml.XmlDocument> object.</span></span>  
  
```  
// Load the style sheet  
XslTransform xslt = new XslTransform();  
xslt.Load("MyStylesheet.xsl");  
  
// Transform input document to XmlDocument for additional processing  
XmlDocument doc = new XmlDocument();  
doc.Load(xslt.Transform(input, (XsltArgumentList)null));  
```  
  
 <span data-ttu-id="f7e5a-139"><xref:System.Xml.Xsl.XslCompiledTransform> Klasa nie obsługuje transformacji do <xref:System.Xml.XmlReader> obiektu.</span><span class="sxs-lookup"><span data-stu-id="f7e5a-139">The <xref:System.Xml.Xsl.XslCompiledTransform> class does not support transforming to an <xref:System.Xml.XmlReader> object.</span></span> <span data-ttu-id="f7e5a-140">Jednak można zrobić coś podobnego przez przy użyciu <xref:System.Xml.XPath.XPathNavigator.CreateNavigator%2A> metodę, aby załadować wynikowy kod XML drzewa bezpośrednio z <xref:System.Xml.XmlWriter>.</span><span class="sxs-lookup"><span data-stu-id="f7e5a-140">However, you can do something similar by using the <xref:System.Xml.XPath.XPathNavigator.CreateNavigator%2A> method to load the resulting XML tree directly from an <xref:System.Xml.XmlWriter>.</span></span> <span data-ttu-id="f7e5a-141">Poniższy kod C# przedstawia sposób wykonania tego samego zadania przy użyciu <xref:System.Xml.Xsl.XslCompiledTransform>.</span><span class="sxs-lookup"><span data-stu-id="f7e5a-141">The following C# code shows how to accomplish the same task using <xref:System.Xml.Xsl.XslCompiledTransform>.</span></span>  
  
```  
// Transform input document to XmlDocument for additional processing  
XmlDocument doc = new XmlDocument();  
using (XmlWriter writer = doc.CreateNavigator().AppendChild()) {  
    xslt.Transform(input, (XsltArgumentList)null, writer);  
}  
```  
  
### <a name="discretionary-behavior"></a><span data-ttu-id="f7e5a-142">Zachowanie DACL</span><span class="sxs-lookup"><span data-stu-id="f7e5a-142">Discretionary Behavior</span></span>  
 <span data-ttu-id="f7e5a-143">Zalecenia w wersji 1.0 W3C transformacji XSL (XSLT) obejmuje obszary, w których implementacji dostawcy może decyzję dotyczącą sposobu obsługi sytuacji.</span><span class="sxs-lookup"><span data-stu-id="f7e5a-143">The W3C XSL Transformations (XSLT) Version 1.0 Recommendation includes areas in which the implementation provider may decide how to handle a situation.</span></span> <span data-ttu-id="f7e5a-144">Te obszary są uważane za DACL zachowanie.</span><span class="sxs-lookup"><span data-stu-id="f7e5a-144">These areas are considered to be discretionary behavior.</span></span> <span data-ttu-id="f7e5a-145">Istnieje kilka obszarów gdzie <xref:System.Xml.Xsl.XslCompiledTransform> zachowuje się inaczej niż <xref:System.Xml.Xsl.XslTransform> klasy.</span><span class="sxs-lookup"><span data-stu-id="f7e5a-145">There are several areas where the <xref:System.Xml.Xsl.XslCompiledTransform> behaves differently than the <xref:System.Xml.Xsl.XslTransform> class.</span></span> <span data-ttu-id="f7e5a-146">Aby uzyskać więcej informacji, zobacz [możliwych do odzyskania błędy XSLT](../../../../docs/standard/data/xml/recoverable-xslt-errors.md).</span><span class="sxs-lookup"><span data-stu-id="f7e5a-146">For more information, see [Recoverable XSLT Errors](../../../../docs/standard/data/xml/recoverable-xslt-errors.md).</span></span>  
  
### <a name="extension-objects-and-script-functions"></a><span data-ttu-id="f7e5a-147">Rozszerzenia obiektów i funkcji skryptu</span><span class="sxs-lookup"><span data-stu-id="f7e5a-147">Extension Objects and Script Functions</span></span>  
 <span data-ttu-id="f7e5a-148"><xref:System.Xml.Xsl.XslCompiledTransform>wprowadzono dwie nowe ograniczenia dotyczące stosowania funkcji skryptu:</span><span class="sxs-lookup"><span data-stu-id="f7e5a-148"><xref:System.Xml.Xsl.XslCompiledTransform> introduces two new restrictions on the use of script functions:</span></span>  
  
-   <span data-ttu-id="f7e5a-149">Może być wywoływana tylko metody publicznej z wyrażenia XPath.</span><span class="sxs-lookup"><span data-stu-id="f7e5a-149">Only public methods may be called from XPath expressions.</span></span>  
  
-   <span data-ttu-id="f7e5a-150">Przeciążenia różnią się od siebie na podstawie liczby argumentów.</span><span class="sxs-lookup"><span data-stu-id="f7e5a-150">Overloads are distinguishable from each other based on the number of arguments.</span></span> <span data-ttu-id="f7e5a-151">Jeśli więcej niż jednego przeciążenia ma taką samą liczbę argumentów, zostanie zgłoszony wyjątek.</span><span class="sxs-lookup"><span data-stu-id="f7e5a-151">If more than one overload has the same number of arguments, an exception will be raised.</span></span>  
  
 <span data-ttu-id="f7e5a-152">W <xref:System.Xml.Xsl.XslCompiledTransform>powiązania (wyszukiwanie nazwy metody) do skryptu funkcji występuje w czasie kompilacji i arkusze stylów, które działały z XslTranform może spowodować wyjątek, gdy są załadowane z <xref:System.Xml.Xsl.XslCompiledTransform>.</span><span class="sxs-lookup"><span data-stu-id="f7e5a-152">In <xref:System.Xml.Xsl.XslCompiledTransform>, a binding (method name lookup) to script functions occurs at compile time, and style sheets that worked with XslTranform may cause an exception when they are loaded with <xref:System.Xml.Xsl.XslCompiledTransform>.</span></span>  
  
 <span data-ttu-id="f7e5a-153"><xref:System.Xml.Xsl.XslCompiledTransform>obsługuje posiadanie `msxsl:using` i `msxsl:assembly` elementy podrzędne w `msxsl:script` elementu.</span><span class="sxs-lookup"><span data-stu-id="f7e5a-153"><xref:System.Xml.Xsl.XslCompiledTransform> supports having `msxsl:using` and `msxsl:assembly` child elements within the `msxsl:script` element.</span></span> <span data-ttu-id="f7e5a-154">`msxsl:using` i `msxsl:assembly` elementy są używane do deklarowania dodatkowe przestrzenie nazw i zestawów do użycia w bloku skryptu.</span><span class="sxs-lookup"><span data-stu-id="f7e5a-154">The `msxsl:using` and `msxsl:assembly` elements are used to declare additional namespaces and assemblies for use in the script block.</span></span> <span data-ttu-id="f7e5a-155">Zobacz [przy użyciu bloków skryptu msxsl:script](../../../../docs/standard/data/xml/script-blocks-using-msxsl-script.md) Aby uzyskać więcej informacji.</span><span class="sxs-lookup"><span data-stu-id="f7e5a-155">See [Script Blocks Using msxsl:script](../../../../docs/standard/data/xml/script-blocks-using-msxsl-script.md) for more information.</span></span>  
  
 <span data-ttu-id="f7e5a-156"><xref:System.Xml.Xsl.XslCompiledTransform>Zabrania używania obiektów rozszerzenia, które mają wielu przeładowań z tą samą liczbą argumentów.</span><span class="sxs-lookup"><span data-stu-id="f7e5a-156"><xref:System.Xml.Xsl.XslCompiledTransform> prohibits extension objects that have multiple overloads with the same number of arguments.</span></span>  
  
### <a name="msxml-functions"></a><span data-ttu-id="f7e5a-157">Funkcje programu MSXML</span><span class="sxs-lookup"><span data-stu-id="f7e5a-157">MSXML Functions</span></span>  
 <span data-ttu-id="f7e5a-158">Obsługa dodatkowych funkcji MSXML zostały dodane do <xref:System.Xml.Xsl.XslCompiledTransform> klasy.</span><span class="sxs-lookup"><span data-stu-id="f7e5a-158">Support for additional MSXML functions have been added to the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span> <span data-ttu-id="f7e5a-159">Na poniższej liście opisano nowe i ulepszone funkcje:</span><span class="sxs-lookup"><span data-stu-id="f7e5a-159">The following list describes new or improved functionality:</span></span>  
  
-   <span data-ttu-id="f7e5a-160">msxsl:node — ustawianie: <xref:System.Xml.Xsl.XslTransform> wymagany argument [zestaw węzłów funkcji](http://msdn.microsoft.com/en-us/87b6b3f4-16f4-4fa3-8103-d62a679ac2a7) funkcję, która ma być wynikowego fragmentu drzewa.</span><span class="sxs-lookup"><span data-stu-id="f7e5a-160">msxsl:node-set: <xref:System.Xml.Xsl.XslTransform> required the argument of the [node-set Function](http://msdn.microsoft.com/en-us/87b6b3f4-16f4-4fa3-8103-d62a679ac2a7) function to be a result tree fragment.</span></span> <span data-ttu-id="f7e5a-161"><xref:System.Xml.Xsl.XslCompiledTransform> Klasa nie ma tego wymogu.</span><span class="sxs-lookup"><span data-stu-id="f7e5a-161">The <xref:System.Xml.Xsl.XslCompiledTransform> class does not have this requirement.</span></span>  
  
-   <span data-ttu-id="f7e5a-162">msxsl:Version: Ta funkcja jest obsługiwana w <xref:System.Xml.Xsl.XslCompiledTransform>.</span><span class="sxs-lookup"><span data-stu-id="f7e5a-162">msxsl:version: This function is supported in <xref:System.Xml.Xsl.XslCompiledTransform>.</span></span>  
  
-   <span data-ttu-id="f7e5a-163">Funkcje rozszerzeń XPath: [ms:string — compare — funkcja](http://msdn.microsoft.com/en-us/20616b82-9e27-444c-b714-4f1e09b73aee), [ms:utc funkcji](http://msdn.microsoft.com/en-us/ef26fc88-84c6-4fb9-9c3b-f2f5264b864f), [ms:namespace — uri funkcji](http://msdn.microsoft.com/en-us/91f9cabf-ab93-4dbe-9c12-e6a75214f4c7), [ms:local — nazwy funkcji](http://msdn.microsoft.com/en-us/10ed60a1-17a9-4d74-8b98-7940ac97c0b5), [ms:number funkcja](http://msdn.microsoft.com/en-us/b94fc08e-1f31-4f48-b1a8-6d78c1b5d954), [ms:format-Data funkcja](http://msdn.microsoft.com/en-us/51f35609-89a9-4098-a166-88bf01300bf5), i [ms:format-czasu funkcji](http://msdn.microsoft.com/en-us/e5c2df2d-e8fb-4a8f-bfc0-db84ea12a5d5) funkcje są teraz obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="f7e5a-163">XPath extension functions: The [ms:string-compare Function](http://msdn.microsoft.com/en-us/20616b82-9e27-444c-b714-4f1e09b73aee), [ms:utc Function](http://msdn.microsoft.com/en-us/ef26fc88-84c6-4fb9-9c3b-f2f5264b864f), [ms:namespace-uri Function](http://msdn.microsoft.com/en-us/91f9cabf-ab93-4dbe-9c12-e6a75214f4c7), [ms:local-name Function](http://msdn.microsoft.com/en-us/10ed60a1-17a9-4d74-8b98-7940ac97c0b5), [ms:number Function](http://msdn.microsoft.com/en-us/b94fc08e-1f31-4f48-b1a8-6d78c1b5d954), [ms:format-date Function](http://msdn.microsoft.com/en-us/51f35609-89a9-4098-a166-88bf01300bf5), and [ms:format-time Function](http://msdn.microsoft.com/en-us/e5c2df2d-e8fb-4a8f-bfc0-db84ea12a5d5) functions are now supported.</span></span>  
  
-   <span data-ttu-id="f7e5a-164">Powiązane schematu funkcje rozszerzenia XPath: te funkcje nie są obsługiwane natywnie przez <xref:System.Xml.Xsl.XslCompiledTransform>.</span><span class="sxs-lookup"><span data-stu-id="f7e5a-164">Schema-related XPath extension functions: These functions are not supported natively by <xref:System.Xml.Xsl.XslCompiledTransform>.</span></span> <span data-ttu-id="f7e5a-165">Jednak może być zaimplementowany jako funkcje rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="f7e5a-165">However, they can be implemented as extension functions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f7e5a-166">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f7e5a-166">See Also</span></span>  
 [<span data-ttu-id="f7e5a-167">Przekształcenia XSLT</span><span class="sxs-lookup"><span data-stu-id="f7e5a-167">XSLT Transformations</span></span>](../../../../docs/standard/data/xml/xslt-transformations.md)  
 [<span data-ttu-id="f7e5a-168">Używanie klasy XslCompiledTransform</span><span class="sxs-lookup"><span data-stu-id="f7e5a-168">Using the XslCompiledTransform Class</span></span>](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md)
