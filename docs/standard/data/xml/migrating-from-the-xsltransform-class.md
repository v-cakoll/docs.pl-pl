---
title: Migrowanie z klasy XslTransform
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 9404d758-679f-4ffb-995d-3d07d817659e
ms.openlocfilehash: d18cf72f0629d347fb5f55ad7332e6046614c01b
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84282392"
---
# <a name="migrating-from-the-xsltransform-class"></a><span data-ttu-id="c4849-102">Migrowanie z klasy XslTransform</span><span class="sxs-lookup"><span data-stu-id="c4849-102">Migrating From the XslTransform Class</span></span>

<span data-ttu-id="c4849-103">Architektura XSLT została przeprojektowana w wersji programu Visual Studio 2005.</span><span class="sxs-lookup"><span data-stu-id="c4849-103">The XSLT architecture was redesigned in the Visual Studio 2005 release.</span></span> <span data-ttu-id="c4849-104"><xref:System.Xml.Xsl.XslTransform>Klasa została zastąpiona przez <xref:System.Xml.Xsl.XslCompiledTransform> klasę.</span><span class="sxs-lookup"><span data-stu-id="c4849-104">The <xref:System.Xml.Xsl.XslTransform> class was replaced by the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span>

<span data-ttu-id="c4849-105">W poniższych sekcjach opisano niektóre główne różnice między <xref:System.Xml.Xsl.XslCompiledTransform> <xref:System.Xml.Xsl.XslTransform> klasami i.</span><span class="sxs-lookup"><span data-stu-id="c4849-105">The following sections describe some of the main differences between the <xref:System.Xml.Xsl.XslCompiledTransform> and the <xref:System.Xml.Xsl.XslTransform> classes.</span></span>

## <a name="performance"></a><span data-ttu-id="c4849-106">Wydajność</span><span class="sxs-lookup"><span data-stu-id="c4849-106">Performance</span></span>

<span data-ttu-id="c4849-107"><xref:System.Xml.Xsl.XslCompiledTransform>Klasa zawiera wiele ulepszeń wydajności.</span><span class="sxs-lookup"><span data-stu-id="c4849-107">The <xref:System.Xml.Xsl.XslCompiledTransform> class includes many performance improvements.</span></span> <span data-ttu-id="c4849-108">Nowy procesor XSLT kompiluje arkusz stylów XSLT w dół do wspólnego formatu pośredniego, podobnie jak środowisko uruchomieniowe języka wspólnego (CLR) dla innych języków programowania.</span><span class="sxs-lookup"><span data-stu-id="c4849-108">The new XSLT processor compiles the XSLT style sheet down to a common intermediate format, similar to what the common language runtime (CLR) does for other programming languages.</span></span> <span data-ttu-id="c4849-109">Po skompilowaniu arkusza stylów można go buforować i ponownie używać.</span><span class="sxs-lookup"><span data-stu-id="c4849-109">Once the style sheet is compiled, it can be cached and reused.</span></span>

<span data-ttu-id="c4849-110"><xref:System.Xml.Xsl.XslCompiledTransform>Klasa zawiera również inne optymalizacje, które znacznie przyspieszają od <xref:System.Xml.Xsl.XslTransform> klasy.</span><span class="sxs-lookup"><span data-stu-id="c4849-110">The <xref:System.Xml.Xsl.XslCompiledTransform> class also includes other optimizations that make it much faster than the <xref:System.Xml.Xsl.XslTransform> class.</span></span>

> [!NOTE]
> <span data-ttu-id="c4849-111">Chociaż ogólna wydajność <xref:System.Xml.Xsl.XslCompiledTransform> klasy jest lepsza niż <xref:System.Xml.Xsl.XslTransform> Klasa, <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> Metoda <xref:System.Xml.Xsl.XslCompiledTransform> klasy może działać wolniej niż <xref:System.Xml.Xsl.XslTransform.Load%2A> Metoda <xref:System.Xml.Xsl.XslTransform> klasy, gdy jest wywoływana po raz pierwszy.</span><span class="sxs-lookup"><span data-stu-id="c4849-111">Although the overall performance of the <xref:System.Xml.Xsl.XslCompiledTransform> class is better than the <xref:System.Xml.Xsl.XslTransform> class, the <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> method of the <xref:System.Xml.Xsl.XslCompiledTransform> class might perform more slowly than the <xref:System.Xml.Xsl.XslTransform.Load%2A> method of the <xref:System.Xml.Xsl.XslTransform> class the first time it is called on a transformation.</span></span> <span data-ttu-id="c4849-112">Jest to spowodowane tym, że plik XSLT musi być skompilowany przed załadowaniem.</span><span class="sxs-lookup"><span data-stu-id="c4849-112">This is because the XSLT file must be compiled before it is loaded.</span></span> <span data-ttu-id="c4849-113">Aby uzyskać więcej informacji, zobacz następujący wpis w blogu: [XslCompiledTransform wolniej niż XslTransform?](https://docs.microsoft.com/archive/blogs/antosha/xslcompiledtransform-slower-than-xsltransform)</span><span class="sxs-lookup"><span data-stu-id="c4849-113">For more information, see the following blog post: [XslCompiledTransform Slower than XslTransform?](https://docs.microsoft.com/archive/blogs/antosha/xslcompiledtransform-slower-than-xsltransform)</span></span>

## <a name="security"></a><span data-ttu-id="c4849-114">Zabezpieczenia</span><span class="sxs-lookup"><span data-stu-id="c4849-114">Security</span></span>

<span data-ttu-id="c4849-115">Domyślnie <xref:System.Xml.Xsl.XslCompiledTransform> Klasa wyłącza obsługę `document()` funkcji XSLT i skryptów osadzonych.</span><span class="sxs-lookup"><span data-stu-id="c4849-115">By default, the <xref:System.Xml.Xsl.XslCompiledTransform> class disables support for the XSLT `document()` function and embedded scripting.</span></span> <span data-ttu-id="c4849-116">Te funkcje można włączyć, tworząc <xref:System.Xml.Xsl.XsltSettings> obiekt z włączonymi funkcjami i przekazując go do <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="c4849-116">These features can be enabled by creating an <xref:System.Xml.Xsl.XsltSettings> object that has the features enabled and passing it to the <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> method.</span></span> <span data-ttu-id="c4849-117">Poniższy przykład pokazuje, jak włączyć obsługę skryptów i przeprowadzić transformację XSLT.</span><span class="sxs-lookup"><span data-stu-id="c4849-117">The following example shows how to enable scripting and perform an XSLT transformation.</span></span>

[!code-csharp[XML_Migration#16](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#16)]
[!code-vb[XML_Migration#16](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#16)]

<span data-ttu-id="c4849-118">Aby uzyskać więcej informacji, zobacz [zagadnienia dotyczące zabezpieczeń XSLT](xslt-security-considerations.md).</span><span class="sxs-lookup"><span data-stu-id="c4849-118">For more information, see [XSLT Security Considerations](xslt-security-considerations.md).</span></span>

## <a name="new-features"></a><span data-ttu-id="c4849-119">Nowe funkcje</span><span class="sxs-lookup"><span data-stu-id="c4849-119">New Features</span></span>

### <a name="temporary-files"></a><span data-ttu-id="c4849-120">Pliki tymczasowe</span><span class="sxs-lookup"><span data-stu-id="c4849-120">Temporary Files</span></span>

<span data-ttu-id="c4849-121">Pliki tymczasowe są czasami generowane podczas przetwarzania XSLT.</span><span class="sxs-lookup"><span data-stu-id="c4849-121">Temporary files are sometimes generated during XSLT processing.</span></span> <span data-ttu-id="c4849-122">Jeśli arkusz stylów zawiera bloki skryptów lub jeśli zostanie skompilowany z ustawieniem Debuguj ustawionym na true, pliki tymczasowe można utworzyć w folderze% TEMP%.</span><span class="sxs-lookup"><span data-stu-id="c4849-122">If a style sheet contains script blocks, or if it is compiled with the debug setting set to true, temporary files may be created in the %TEMP% folder.</span></span> <span data-ttu-id="c4849-123">Mogą występować wystąpienia, gdy niektóre pliki tymczasowe nie zostaną usunięte ze względu na problemy z chronometrażem.</span><span class="sxs-lookup"><span data-stu-id="c4849-123">There may be instances when some temporary files are not deleted due to timing issues.</span></span> <span data-ttu-id="c4849-124">Na przykład jeśli pliki są używane przez bieżącą domenę aplikacji lub przez debuger, finalizator <xref:System.CodeDom.Compiler.TempFileCollection> obiektu nie będzie mógł go usunąć.</span><span class="sxs-lookup"><span data-stu-id="c4849-124">For example, if the files are in use by the current AppDomain or by the debugger, the finalizer of the <xref:System.CodeDom.Compiler.TempFileCollection> object will not be able to remove them.</span></span>

<span data-ttu-id="c4849-125"><xref:System.Xml.Xsl.XslCompiledTransform.TemporaryFiles%2A>Właściwość może służyć do dodatkowego oczyszczania, aby upewnić się, że wszystkie pliki tymczasowe są usuwane z klienta programu.</span><span class="sxs-lookup"><span data-stu-id="c4849-125">The <xref:System.Xml.Xsl.XslCompiledTransform.TemporaryFiles%2A> property can be used for additional cleanup to make sure that all temporary files are removed from the client.</span></span>

### <a name="support-for-the-xsloutput-element-and-xmlwriter"></a><span data-ttu-id="c4849-126">Obsługa elementu xsl: Output i XmlWriter</span><span class="sxs-lookup"><span data-stu-id="c4849-126">Support for the xsl:output Element and XmlWriter</span></span>

<span data-ttu-id="c4849-127"><xref:System.Xml.Xsl.XslTransform>Klasa zignorował `xsl:output` Ustawienia, gdy dane wyjściowe transformacji zostały wysłane do <xref:System.Xml.XmlWriter> obiektu.</span><span class="sxs-lookup"><span data-stu-id="c4849-127">The <xref:System.Xml.Xsl.XslTransform> class ignored `xsl:output` settings when the transform output was sent to an <xref:System.Xml.XmlWriter> object.</span></span> <span data-ttu-id="c4849-128"><xref:System.Xml.Xsl.XslCompiledTransform>Klasa ma <xref:System.Xml.Xsl.XslCompiledTransform.OutputSettings%2A> Właściwość, która zwraca <xref:System.Xml.XmlWriterSettings> obiekt zawierający informacje wyjściowe pochodzące z `xsl:output` elementu arkusza stylów.</span><span class="sxs-lookup"><span data-stu-id="c4849-128">The <xref:System.Xml.Xsl.XslCompiledTransform> class has an <xref:System.Xml.Xsl.XslCompiledTransform.OutputSettings%2A> property that returns an <xref:System.Xml.XmlWriterSettings> object containing the output information derived from the `xsl:output` element of the style sheet.</span></span> <span data-ttu-id="c4849-129"><xref:System.Xml.XmlWriterSettings>Obiekt jest używany do tworzenia <xref:System.Xml.XmlWriter> obiektu z prawidłowymi ustawieniami, które mogą być przesyłane do <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="c4849-129">The <xref:System.Xml.XmlWriterSettings> object is used to create an <xref:System.Xml.XmlWriter> object with the correct settings that can be passed to the <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> method.</span></span> <span data-ttu-id="c4849-130">Poniższy kod w języku C# ilustruje to zachowanie:</span><span class="sxs-lookup"><span data-stu-id="c4849-130">The following C# code illustrates this behavior:</span></span>

```csharp
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

### <a name="debug-option"></a><span data-ttu-id="c4849-131">Opcja debugowania</span><span class="sxs-lookup"><span data-stu-id="c4849-131">Debug Option</span></span>

<span data-ttu-id="c4849-132"><xref:System.Xml.Xsl.XslCompiledTransform>Klasa może generować informacje debugowania, które umożliwiają debugowanie arkusza stylów za pomocą debugera Microsoft Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="c4849-132">The <xref:System.Xml.Xsl.XslCompiledTransform> class can generate debug information, which enables you to debug the style sheet with the Microsoft Visual Studio Debugger.</span></span> <span data-ttu-id="c4849-133">Aby uzyskać więcej informacji, zobacz <xref:System.Xml.Xsl.XslCompiledTransform.%23ctor%28System.Boolean%29>.</span><span class="sxs-lookup"><span data-stu-id="c4849-133">See <xref:System.Xml.Xsl.XslCompiledTransform.%23ctor%28System.Boolean%29> for more information.</span></span>

## <a name="behavioral-differences"></a><span data-ttu-id="c4849-134">Różnice w zachowaniu</span><span class="sxs-lookup"><span data-stu-id="c4849-134">Behavioral Differences</span></span>

### <a name="transforming-to-an-xmlreader"></a><span data-ttu-id="c4849-135">Przekształcanie do elementu XmlReader</span><span class="sxs-lookup"><span data-stu-id="c4849-135">Transforming to an XmlReader</span></span>

<span data-ttu-id="c4849-136"><xref:System.Xml.Xsl.XslTransform>Klasa ma kilka przeciążenia transformacji, które zwracają wyniki transformacji jako <xref:System.Xml.XmlReader> obiekt.</span><span class="sxs-lookup"><span data-stu-id="c4849-136">The <xref:System.Xml.Xsl.XslTransform> class has several Transform overloads that return transformation results as an <xref:System.Xml.XmlReader> object.</span></span> <span data-ttu-id="c4849-137">Te przeciążenia mogą służyć do załadowania wyników transformacji do reprezentacji w pamięci (takiej jak <xref:System.Xml.XmlDocument> lub) bez naliczania <xref:System.Xml.XPath.XPathDocument> obciążeń związanych z serializacji i deserializacji wynikowego drzewa XML.</span><span class="sxs-lookup"><span data-stu-id="c4849-137">These overloads can be used to load the transformation results into an in-memory representation (such as <xref:System.Xml.XmlDocument> or <xref:System.Xml.XPath.XPathDocument>) without incurring the overhead of serialization and deserialization of the resulting XML tree.</span></span> <span data-ttu-id="c4849-138">Poniższy kod w języku C# pokazuje, jak załadować wyniki transformacji do <xref:System.Xml.XmlDocument> obiektu.</span><span class="sxs-lookup"><span data-stu-id="c4849-138">The following C# code shows how to load the transformation results into an <xref:System.Xml.XmlDocument> object.</span></span>

```csharp
// Load the style sheet
XslTransform xslt = new XslTransform();
xslt.Load("MyStylesheet.xsl");

// Transform input document to XmlDocument for additional processing
XmlDocument doc = new XmlDocument();
doc.Load(xslt.Transform(input, (XsltArgumentList)null));
```

<span data-ttu-id="c4849-139"><xref:System.Xml.Xsl.XslCompiledTransform>Klasa nie obsługuje transformacji do <xref:System.Xml.XmlReader> obiektu.</span><span class="sxs-lookup"><span data-stu-id="c4849-139">The <xref:System.Xml.Xsl.XslCompiledTransform> class does not support transforming to an <xref:System.Xml.XmlReader> object.</span></span> <span data-ttu-id="c4849-140">Można jednak wykonać coś podobnego przy użyciu <xref:System.Xml.XPath.XPathNavigator.CreateNavigator%2A> metody do załadowania utworzonego drzewa XML bezpośrednio z obiektu <xref:System.Xml.XmlWriter> .</span><span class="sxs-lookup"><span data-stu-id="c4849-140">However, you can do something similar by using the <xref:System.Xml.XPath.XPathNavigator.CreateNavigator%2A> method to load the resulting XML tree directly from an <xref:System.Xml.XmlWriter>.</span></span> <span data-ttu-id="c4849-141">Poniższy kod w języku C# pokazuje, jak wykonać to samo zadanie przy użyciu polecenia <xref:System.Xml.Xsl.XslCompiledTransform> .</span><span class="sxs-lookup"><span data-stu-id="c4849-141">The following C# code shows how to accomplish the same task using <xref:System.Xml.Xsl.XslCompiledTransform>.</span></span>

```csharp
// Transform input document to XmlDocument for additional processing
XmlDocument doc = new XmlDocument();
using (XmlWriter writer = doc.CreateNavigator().AppendChild()) {
    xslt.Transform(input, (XsltArgumentList)null, writer);
}
```

### <a name="discretionary-behavior"></a><span data-ttu-id="c4849-142">Zachowanie uznaniowe</span><span class="sxs-lookup"><span data-stu-id="c4849-142">Discretionary Behavior</span></span>

<span data-ttu-id="c4849-143">Zalecenie dotyczące formatu W3C XSL Transformations (XSLT) w wersji 1,0 zawiera obszary, w których dostawca implementacji może zdecydować, jak obsługiwać sytuację.</span><span class="sxs-lookup"><span data-stu-id="c4849-143">The W3C XSL Transformations (XSLT) Version 1.0 Recommendation includes areas in which the implementation provider may decide how to handle a situation.</span></span> <span data-ttu-id="c4849-144">Te obszary są uważane za zachowanie uznaniowe.</span><span class="sxs-lookup"><span data-stu-id="c4849-144">These areas are considered to be discretionary behavior.</span></span> <span data-ttu-id="c4849-145">Istnieje kilka obszarów, w których <xref:System.Xml.Xsl.XslCompiledTransform> zachowanie różni się od <xref:System.Xml.Xsl.XslTransform> klasy.</span><span class="sxs-lookup"><span data-stu-id="c4849-145">There are several areas where the <xref:System.Xml.Xsl.XslCompiledTransform> behaves differently than the <xref:System.Xml.Xsl.XslTransform> class.</span></span> <span data-ttu-id="c4849-146">Aby uzyskać więcej informacji, zobacz [odzyskanie błędów XSLT](recoverable-xslt-errors.md).</span><span class="sxs-lookup"><span data-stu-id="c4849-146">For more information, see [Recoverable XSLT Errors](recoverable-xslt-errors.md).</span></span>

### <a name="extension-objects-and-script-functions"></a><span data-ttu-id="c4849-147">Obiekty rozszerzeń i funkcje skryptów</span><span class="sxs-lookup"><span data-stu-id="c4849-147">Extension Objects and Script Functions</span></span>

<span data-ttu-id="c4849-148"><xref:System.Xml.Xsl.XslCompiledTransform>wprowadza dwa nowe ograniczenia dotyczące używania funkcji skryptów:</span><span class="sxs-lookup"><span data-stu-id="c4849-148"><xref:System.Xml.Xsl.XslCompiledTransform> introduces two new restrictions on the use of script functions:</span></span>

- <span data-ttu-id="c4849-149">Tylko metody publiczne mogą być wywoływane z wyrażeń XPath.</span><span class="sxs-lookup"><span data-stu-id="c4849-149">Only public methods may be called from XPath expressions.</span></span>

- <span data-ttu-id="c4849-150">Przeciążenia są odróżniane od siebie w zależności od liczby argumentów.</span><span class="sxs-lookup"><span data-stu-id="c4849-150">Overloads are distinguishable from each other based on the number of arguments.</span></span> <span data-ttu-id="c4849-151">Jeśli więcej niż jedno Przeciążenie ma taką samą liczbę argumentów, zostanie zgłoszony wyjątek.</span><span class="sxs-lookup"><span data-stu-id="c4849-151">If more than one overload has the same number of arguments, an exception will be raised.</span></span>

<span data-ttu-id="c4849-152">W programie <xref:System.Xml.Xsl.XslCompiledTransform> powiązanie (wyszukiwanie nazw metod) z funkcjami skryptu występuje w czasie kompilacji, a arkusze stylów, które działały z XslTransform, mogą spowodować wyjątek podczas ładowania z <xref:System.Xml.Xsl.XslCompiledTransform> .</span><span class="sxs-lookup"><span data-stu-id="c4849-152">In <xref:System.Xml.Xsl.XslCompiledTransform>, a binding (method name lookup) to script functions occurs at compile time, and style sheets that worked with XslTransform may cause an exception when they are loaded with <xref:System.Xml.Xsl.XslCompiledTransform>.</span></span>

<span data-ttu-id="c4849-153"><xref:System.Xml.Xsl.XslCompiledTransform>obsługuje elementy mające `msxsl:using` i `msxsl:assembly` elementów podrzędnych w obrębie `msxsl:script` elementu.</span><span class="sxs-lookup"><span data-stu-id="c4849-153"><xref:System.Xml.Xsl.XslCompiledTransform> supports having `msxsl:using` and `msxsl:assembly` child elements within the `msxsl:script` element.</span></span> <span data-ttu-id="c4849-154">`msxsl:using`Elementy i `msxsl:assembly` są używane do deklarowania dodatkowych przestrzeni nazw i zestawów do użycia w bloku skryptu.</span><span class="sxs-lookup"><span data-stu-id="c4849-154">The `msxsl:using` and `msxsl:assembly` elements are used to declare additional namespaces and assemblies for use in the script block.</span></span> <span data-ttu-id="c4849-155">Aby uzyskać więcej informacji, zobacz [bloki skryptów przy użyciu msxsl: Script](script-blocks-using-msxsl-script.md) .</span><span class="sxs-lookup"><span data-stu-id="c4849-155">See [Script Blocks Using msxsl:script](script-blocks-using-msxsl-script.md) for more information.</span></span>

<span data-ttu-id="c4849-156"><xref:System.Xml.Xsl.XslCompiledTransform>zabrania obiektów rozszerzeń, które mają wiele przeciążeń z tą samą liczbą argumentów.</span><span class="sxs-lookup"><span data-stu-id="c4849-156"><xref:System.Xml.Xsl.XslCompiledTransform> prohibits extension objects that have multiple overloads with the same number of arguments.</span></span>

### <a name="msxml-functions"></a><span data-ttu-id="c4849-157">Funkcje programu MSXML</span><span class="sxs-lookup"><span data-stu-id="c4849-157">MSXML Functions</span></span>

<span data-ttu-id="c4849-158">Do klasy dodano obsługę dodatkowych funkcji MSXML <xref:System.Xml.Xsl.XslCompiledTransform> .</span><span class="sxs-lookup"><span data-stu-id="c4849-158">Support for additional MSXML functions have been added to the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span> <span data-ttu-id="c4849-159">Na poniższej liście opisano nowe lub udoskonalone funkcje:</span><span class="sxs-lookup"><span data-stu-id="c4849-159">The following list describes new or improved functionality:</span></span>

- <span data-ttu-id="c4849-160">msxsl: zestaw węzłów: <xref:System.Xml.Xsl.XslTransform> wymagany argument funkcji [funkcji zestawu węzłów](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms256197(v=vs.100)) musi być fragmentem drzewa wynikowego.</span><span class="sxs-lookup"><span data-stu-id="c4849-160">msxsl:node-set: <xref:System.Xml.Xsl.XslTransform> required the argument of the [node-set Function](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms256197(v=vs.100)) function to be a result tree fragment.</span></span> <span data-ttu-id="c4849-161"><xref:System.Xml.Xsl.XslCompiledTransform>Klasa nie ma tego wymagania.</span><span class="sxs-lookup"><span data-stu-id="c4849-161">The <xref:System.Xml.Xsl.XslCompiledTransform> class does not have this requirement.</span></span>

- <span data-ttu-id="c4849-162">msxsl: wersja: Ta funkcja jest obsługiwana w programie <xref:System.Xml.Xsl.XslCompiledTransform> .</span><span class="sxs-lookup"><span data-stu-id="c4849-162">msxsl:version: This function is supported in <xref:System.Xml.Xsl.XslCompiledTransform>.</span></span>

- <span data-ttu-id="c4849-163">Funkcje rozszerzenia XPath: [Funkcja MS: Compare — porównanie](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms256114(v=vs.100)), [MS: UTC funkcja](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms256474(v=vs.100)), [MS: Namespace-URI](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms256231(v=vs.100)), [MS: funkcja local-name](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms256055(v=vs.100)), [MS: Number](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms256155(v=vs.100)), funkcja [MS: format-Date](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms256099(v=vs.100))i MS: funkcje [funkcji Time w formacie godziny](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms256467(v=vs.100)) są teraz obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="c4849-163">XPath extension functions: The [ms:string-compare Function](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms256114(v=vs.100)), [ms:utc Function](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms256474(v=vs.100)), [ms:namespace-uri Function](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms256231(v=vs.100)), [ms:local-name Function](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms256055(v=vs.100)), [ms:number Function](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms256155(v=vs.100)), [ms:format-date Function](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms256099(v=vs.100)), and [ms:format-time Function](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms256467(v=vs.100)) functions are now supported.</span></span>

- <span data-ttu-id="c4849-164">Funkcje rozszerzenia XPath powiązane ze schematem: funkcje te nie są obsługiwane natywnie przez program <xref:System.Xml.Xsl.XslCompiledTransform> .</span><span class="sxs-lookup"><span data-stu-id="c4849-164">Schema-related XPath extension functions: These functions are not supported natively by <xref:System.Xml.Xsl.XslCompiledTransform>.</span></span> <span data-ttu-id="c4849-165">Można je jednak zaimplementować jako funkcje rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="c4849-165">However, they can be implemented as extension functions.</span></span>

## <a name="see-also"></a><span data-ttu-id="c4849-166">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c4849-166">See also</span></span>

- [<span data-ttu-id="c4849-167">Przekształcenia XSLT</span><span class="sxs-lookup"><span data-stu-id="c4849-167">XSLT Transformations</span></span>](xslt-transformations.md)
- [<span data-ttu-id="c4849-168">Używanie klasy XslCompiledTransform</span><span class="sxs-lookup"><span data-stu-id="c4849-168">Using the XslCompiledTransform Class</span></span>](using-the-xslcompiledtransform-class.md)
