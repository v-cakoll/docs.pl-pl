---
title: "Dokumentowanie kodu za pomocą komentarze XML"
description: "Dowiedz się, jak dokumentowanie kodu za pomocą komentarze dokumentacji XML i generowania pliku dokumentacji XML w czasie kompilacji."
keywords: .NET, .NET core
author: BillWagner
ms.author: wiwagn
ms.date: 02/14/2017
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 8e75e317-4a55-45f2-a866-e76124171838
ms.openlocfilehash: 709ef2ba2202e69ba35834789ad6e743a0f6b719
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="documenting-your-code-with-xml-comments"></a><span data-ttu-id="daad0-104">Dokumentowanie kodu za pomocą komentarze XML</span><span class="sxs-lookup"><span data-stu-id="daad0-104">Documenting your code with XML comments</span></span>

<span data-ttu-id="daad0-105">Komentarze dokumentacji XML to specjalny rodzaj, dodano komentarz powyżej definicji typu zdefiniowanego przez użytkownika lub elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="daad0-105">XML documentation comments are a special kind of comment, added above the definition of any user-defined type or member.</span></span> <span data-ttu-id="daad0-106">Są one specjalne, ponieważ mogą być przetwarzane przez kompilator do generowania pliku dokumentacji XML w czasie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="daad0-106">They are special because they can be processed by the compiler to generate an XML documentation file at compile time.</span></span>
<span data-ttu-id="daad0-107">Plik XML wygenerowanego przez kompilator mogą być dystrybuowane wraz z zestawu .NET, dzięki czemu program Visual Studio i innych IDEs może używać IntelliSense do wyświetlenia szybkie informacji na temat typów albo elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="daad0-107">The compiler generated XML file can be distributed alongside your .NET assembly so that Visual Studio and other IDEs can use IntelliSense to show quick information about types or members.</span></span> <span data-ttu-id="daad0-108">Ponadto można uruchomić plik XML za pomocą takich narzędzi jak [DocFX](https://dotnet.github.io/docfx/) i [Sandcastle](https://github.com/EWSoftware/SHFB) można wygenerować odwołania API witryn sieci Web.</span><span class="sxs-lookup"><span data-stu-id="daad0-108">Additionally, the XML file can be run through tools like [DocFX](https://dotnet.github.io/docfx/) and [Sandcastle](https://github.com/EWSoftware/SHFB) to generate API reference websites.</span></span>

<span data-ttu-id="daad0-109">Komentarze dokumentacji XML, podobnie jak wszystkie inne komentarze są ignorowane przez kompilator.</span><span class="sxs-lookup"><span data-stu-id="daad0-109">XML documentation comments, like all other comments, are ignored by the compiler.</span></span>

<span data-ttu-id="daad0-110">W czasie kompilacji można wygenerować plik XML, wykonując jedną z następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="daad0-110">You can generate the XML file at compile time by doing one of the following:</span></span>

- <span data-ttu-id="daad0-111">Jeśli tworzysz aplikację z platformą .NET Core w wierszu polecenia, można dodać [elementu DocumentationFile](http://docs.microsoft.com/visualstudio/msbuild/common-msbuild-project-properties) do `<PropertyGroup>` sekcji pliku .csproj projektu.</span><span class="sxs-lookup"><span data-stu-id="daad0-111">If you are developing an application with .NET Core from the command line, you can add a [DocumentationFile element](http://docs.microsoft.com/visualstudio/msbuild/common-msbuild-project-properties) to the `<PropertyGroup>` section of your .csproj project file.</span></span> <span data-ttu-id="daad0-112">Poniższy przykład generuje plik XML w katalogu projektu o takiej samej nazwie głównego pliku zestawu:</span><span class="sxs-lookup"><span data-stu-id="daad0-112">The following example generates an XML file in the project directory with the same root filename as the assembly:</span></span>

   ```xml
   <DocumentationFile>bin\$(Configuration)\$(TargetFramework)\$(AssemblyName).xml</DocumentationFile>
   ```

   <span data-ttu-id="daad0-113">Można również określić dokładną bezwzględną ani względną ścieżkę i nazwę pliku XML.</span><span class="sxs-lookup"><span data-stu-id="daad0-113">You can also specify the exact absolute or relative path and name of the XML file.</span></span> <span data-ttu-id="daad0-114">Poniższy przykład generuje plik XML w tym samym katalogu co wersja do debugowania aplikacji:</span><span class="sxs-lookup"><span data-stu-id="daad0-114">The following example generates the XML file in the same directory as the debug version of an application:</span></span>

    ```xml
   <DocumentationFile>bin\Debug\netcoreapp1.0\App.xml</DocumentationFile>
   ```

- <span data-ttu-id="daad0-115">Jeśli tworzysz aplikację przy użyciu programu Visual Studio, kliknij prawym przyciskiem myszy projekt i wybierz **właściwości**.</span><span class="sxs-lookup"><span data-stu-id="daad0-115">If you are developing an application using Visual Studio, right-click on the project and select **Properties**.</span></span> <span data-ttu-id="daad0-116">W oknie dialogowym właściwości wybierz **kompilacji** i sprawdź **pliku dokumentacji XML**.</span><span class="sxs-lookup"><span data-stu-id="daad0-116">In the properties dialog, select the **Build** tab, and check **XML documentation file**.</span></span> <span data-ttu-id="daad0-117">Możesz również zmienić lokalizację, do której kompilator zapisuje plik.</span><span class="sxs-lookup"><span data-stu-id="daad0-117">You can also change the location to which the compiler writes the file.</span></span> 

- <span data-ttu-id="daad0-118">Jeśli kompilacja aplikacji .NET Framework, w wierszu polecenia, należy dodać [/doc — opcja kompilatora](language-reference/compiler-options/doc-compiler-option.md) podczas kompilowania.</span><span class="sxs-lookup"><span data-stu-id="daad0-118">If you are compiling a .NET Framework application from the command line, add the [/doc compiler option](language-reference/compiler-options/doc-compiler-option.md) when compiling.</span></span>  

<span data-ttu-id="daad0-119">Potrójna kreska ułamkowa Użyj komentarze dokumentacji XML (`///`) i treść komentarza sformatowany XML.</span><span class="sxs-lookup"><span data-stu-id="daad0-119">XML documentation comments use triple forward slashes (`///`) and an XML formatted comment body.</span></span> <span data-ttu-id="daad0-120">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="daad0-120">For example:</span></span>

[!code-csharp[XML Documentation Comment](../../samples/snippets/csharp/concepts/codedoc/xml-comment.cs)]

## <a name="walkthrough"></a><span data-ttu-id="daad0-121">Wskazówki</span><span class="sxs-lookup"><span data-stu-id="daad0-121">Walkthrough</span></span>

<span data-ttu-id="daad0-122">Przejdźmy, dokumentowanie biblioteki matematyczne bardzo podstawowe ułatwia nowe deweloperom zrozumieć współtworzenia i deweloperom użycie innych firm.</span><span class="sxs-lookup"><span data-stu-id="daad0-122">Let's walk through documenting a very basic math library to make it easy for new developers to understand/contribute and for third party developers to use.</span></span>

<span data-ttu-id="daad0-123">Oto kod biblioteki matematyczne prosty:</span><span class="sxs-lookup"><span data-stu-id="daad0-123">Here's code for the simple math library:</span></span>

[!code-csharp[Sample Library](../../samples/snippets/csharp/concepts/codedoc/sample-library.cs)]

<span data-ttu-id="daad0-124">Biblioteka próbki obsługuje cztery główne operacje arytmetyczne `add`, `subtract`, `multiply` i `divide` na `int` i `double` typy danych.</span><span class="sxs-lookup"><span data-stu-id="daad0-124">The sample library supports four major arithmetic operations `add`, `subtract`, `multiply` and `divide` on `int` and `double` data types.</span></span>

<span data-ttu-id="daad0-125">Teraz chcesz mieć możliwość utworzenia dokument dokumentacja interfejsu API w kodzie dla deweloperów innych firm, którzy używają biblioteki, ale nie mają dostępu do kodu źródłowego.</span><span class="sxs-lookup"><span data-stu-id="daad0-125">Now you want to be able to create an API reference document from your code for third party developers who use your library but don't have access to the source code.</span></span>
<span data-ttu-id="daad0-126">Jak wspomniano wcześniej tagów dokumentacji XML może być użyty można to osiągnąć, możesz teraz zostaną wprowadzone do standardowych obsługuje kompilatora tagi C# XML.</span><span class="sxs-lookup"><span data-stu-id="daad0-126">As mentioned earlier XML documentation tags can be used to achieve this, You will now be introduced to the standard XML tags the C# compiler supports.</span></span>

### <a name="ltsummarygt"></a><span data-ttu-id="daad0-127">&lt;Podsumowanie&gt;</span><span class="sxs-lookup"><span data-stu-id="daad0-127">&lt;summary&gt;</span></span>

<span data-ttu-id="daad0-128">`<summary>` Tagów dodaje krótki informacji na temat typu lub elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="daad0-128">The `<summary>` tag adds brief information about a type or member.</span></span>
<span data-ttu-id="daad0-129">I będzie pokazują jego użycie przez dodanie go do `Math` klasy definicji i pierwszy `Add` metody.</span><span class="sxs-lookup"><span data-stu-id="daad0-129">I'll demonstrate its use by adding it to the `Math` class definition and the first `Add` method.</span></span> <span data-ttu-id="daad0-130">Możesz także zastosować je do pozostałej części kodu.</span><span class="sxs-lookup"><span data-stu-id="daad0-130">Feel free to apply it to the rest of your code.</span></span>

[!code-csharp[Summary Tag](../../samples/snippets/csharp/concepts/codedoc/summary-tag.cs)]

<span data-ttu-id="daad0-131">`<summary>` Tag jest bardzo ważne i zalecane jest uwzględniania go, ponieważ jego zawartość jest podstawowym źródłem informacji typu lub elementu członkowskiego w IntelliSense lub dokument dokumentacja interfejsu API.</span><span class="sxs-lookup"><span data-stu-id="daad0-131">The `<summary>` tag is very important, and we recommend that you include it because its content is the primary source of type or member information in IntelliSense or an API reference document.</span></span>

### <a name="ltremarksgt"></a><span data-ttu-id="daad0-132">&lt;Uwagi&gt;</span><span class="sxs-lookup"><span data-stu-id="daad0-132">&lt;remarks&gt;</span></span>

<span data-ttu-id="daad0-133">`<remarks>` Tag przedstawiono dodatkowe informacje dotyczące typów albo elementów członkowskich który `<summary>` zawiera tag.</span><span class="sxs-lookup"><span data-stu-id="daad0-133">The `<remarks>` tag supplements the information about types or members that the `<summary>` tag provides.</span></span> <span data-ttu-id="daad0-134">W tym przykładzie będzie po prostu dodaj ją do klasy.</span><span class="sxs-lookup"><span data-stu-id="daad0-134">In this example, you'll just add it to the class.</span></span>

[!code-csharp[Remarks Tag](../../samples/snippets/csharp/concepts/codedoc/remarks-tag.cs)]

### <a name="ltreturnsgt"></a><span data-ttu-id="daad0-135">&lt;Zwraca&gt;</span><span class="sxs-lookup"><span data-stu-id="daad0-135">&lt;returns&gt;</span></span>

<span data-ttu-id="daad0-136">`<returns>` Tag opisuje wartość zwracana w deklaracji metody.</span><span class="sxs-lookup"><span data-stu-id="daad0-136">The `<returns>` tag describes the return value of a method declaration.</span></span>
<span data-ttu-id="daad0-137">Jak wcześniej, poniższy przykład przedstawia `<returns>` tag pierwszego `Add` metody.</span><span class="sxs-lookup"><span data-stu-id="daad0-137">As before, the following example illustrates the `<returns>` tag on the first `Add` method.</span></span> <span data-ttu-id="daad0-138">Możesz to zrobić na innych metod.</span><span class="sxs-lookup"><span data-stu-id="daad0-138">You can do the same on other methods.</span></span>

[!code-csharp[Returns Tag](../../samples/snippets/csharp/concepts/codedoc/returns-tag.cs)]

### <a name="ltvaluegt"></a><span data-ttu-id="daad0-139">&lt;wartość&gt;</span><span class="sxs-lookup"><span data-stu-id="daad0-139">&lt;value&gt;</span></span>

<span data-ttu-id="daad0-140">`<value>` Tag jest podobny do `<returns>` tagów, z wyjątkiem tego, że używasz dla właściwości.</span><span class="sxs-lookup"><span data-stu-id="daad0-140">The `<value>` tag is similar to the `<returns>` tag, except that you use it for properties.</span></span>
<span data-ttu-id="daad0-141">Zakładając, że Twoje `Math` biblioteka ma właściwości statycznej o nazwie `PI`, Oto jak użyje tego tagu:</span><span class="sxs-lookup"><span data-stu-id="daad0-141">Assuming your `Math` library had a static property called `PI`, here's how you'd use this tag:</span></span>

[!code-csharp[Value Tag](../../samples/snippets/csharp/concepts/codedoc/value-tag.cs)]

### <a name="ltexamplegt"></a><span data-ttu-id="daad0-142">&lt;przykład&gt;</span><span class="sxs-lookup"><span data-stu-id="daad0-142">&lt;example&gt;</span></span>

<span data-ttu-id="daad0-143">Możesz użyć `<example>` znacznik w celu uwzględnienia przykładem w dokumentacji XML.</span><span class="sxs-lookup"><span data-stu-id="daad0-143">You use the `<example>` tag to include an example in your XML documentation.</span></span>
<span data-ttu-id="daad0-144">Obejmuje to przy użyciu elementu podrzędnego `<code>` tagu.</span><span class="sxs-lookup"><span data-stu-id="daad0-144">This involves using the child `<code>` tag.</span></span>

[!code-csharp[Example Tag](../../samples/snippets/csharp/concepts/codedoc/example-tag.cs)]

<span data-ttu-id="daad0-145">`code` Tag zachowuje podziały wiersza i wcięcia dłuższego przykłady.</span><span class="sxs-lookup"><span data-stu-id="daad0-145">The `code` tag preserves line breaks and indentation for longer examples.</span></span>

### <a name="ltparagt"></a><span data-ttu-id="daad0-146">&lt;para&gt;</span><span class="sxs-lookup"><span data-stu-id="daad0-146">&lt;para&gt;</span></span>

<span data-ttu-id="daad0-147">Możesz użyć `<para>` znacznik w celu formatowania zawartości w tagu nadrzędnym.</span><span class="sxs-lookup"><span data-stu-id="daad0-147">You use the `<para>` tag to format the content within its parent tag.</span></span> <span data-ttu-id="daad0-148">`<para>`jest zwykle używany wewnątrz tagu, takich jak `<remarks>` lub `<returns>`, aby podzielić tekst na akapitów.</span><span class="sxs-lookup"><span data-stu-id="daad0-148">`<para>` is usually used inside a tag, such as `<remarks>` or `<returns>`, to divide text into paragraphs.</span></span>
<span data-ttu-id="daad0-149">Zawartość można sformatować `<remarks>` tag definicji klasy.</span><span class="sxs-lookup"><span data-stu-id="daad0-149">You can format the contents of the `<remarks>` tag for your class definition.</span></span>

[!code-csharp[Para Tag](../../samples/snippets/csharp/concepts/codedoc/para-tag.cs)]

### <a name="ltcgt"></a><span data-ttu-id="daad0-150">&lt;c&gt;</span><span class="sxs-lookup"><span data-stu-id="daad0-150">&lt;c&gt;</span></span>

<span data-ttu-id="daad0-151">Pracując nadal na temat formatowania, użyj `<c>` tag znakowania część tekstu jako tekstu zawierającego kod.</span><span class="sxs-lookup"><span data-stu-id="daad0-151">Still on the topic of formatting, you use the `<c>` tag for marking part of text as code.</span></span>
<span data-ttu-id="daad0-152">Przypomina to `<code>` , ale wbudowany tag.</span><span class="sxs-lookup"><span data-stu-id="daad0-152">It's like the `<code>` tag but inline.</span></span> <span data-ttu-id="daad0-153">Jest przydatne, gdy chcesz pokazać przykładowego kodu szybkie jako część zawartości tagu.</span><span class="sxs-lookup"><span data-stu-id="daad0-153">It's useful when you want to show a quick code example as part of a tag's content.</span></span>
<span data-ttu-id="daad0-154">Ta funkcja pozwala zaktualizować dokumentację dla `Math` klasy.</span><span class="sxs-lookup"><span data-stu-id="daad0-154">Let's update the documentation for the `Math` class.</span></span>

[!code-csharp[C Tag](../../samples/snippets/csharp/concepts/codedoc/c-tag.cs)]

### <a name="ltexceptiongt"></a><span data-ttu-id="daad0-155">&lt;wyjątek&gt;</span><span class="sxs-lookup"><span data-stu-id="daad0-155">&lt;exception&gt;</span></span>

<span data-ttu-id="daad0-156">Za pomocą `<exception>` tagu let deweloperów wiedzieć, że metoda może zgłosić określonych wyjątków.</span><span class="sxs-lookup"><span data-stu-id="daad0-156">By using the `<exception>` tag, you let your developers know that a method can throw specific exceptions.</span></span>
<span data-ttu-id="daad0-157">Spojrzenie na Twojej `Math` biblioteki, można stwierdzić, że oba `Add` metody zgłosić wyjątek, jeśli określony warunek jest spełniony.</span><span class="sxs-lookup"><span data-stu-id="daad0-157">Looking at your `Math` library, you can see that both `Add` methods throw an exception if a certain condition is met.</span></span> <span data-ttu-id="daad0-158">Nie jest tak oczywiste, że liczba całkowita `Divide` metoda zgłasza, a także jeśli `b` parametru wynosi zero.</span><span class="sxs-lookup"><span data-stu-id="daad0-158">Not so obvious, though, is that integer `Divide` method throws as well if the `b` parameter is zero.</span></span> <span data-ttu-id="daad0-159">Teraz należy dodać wyjątek dokumentacji do tej metody.</span><span class="sxs-lookup"><span data-stu-id="daad0-159">Now add exception documentation to this method.</span></span>

[!code-csharp[Exception Tag](../../samples/snippets/csharp/concepts/codedoc/exception-tag.cs)]

<span data-ttu-id="daad0-160">`cref` Atrybut reprezentuje odwołanie do wyjątek, który jest dostępny w bieżącym środowisku kompilacji.</span><span class="sxs-lookup"><span data-stu-id="daad0-160">The `cref` attribute represents a reference to an exception that is available from the current compilation environment.</span></span>
<span data-ttu-id="daad0-161">Może to być dowolny typ zdefiniowany w projekcie lub przywoływanego zestawu.</span><span class="sxs-lookup"><span data-stu-id="daad0-161">This can be any type defined in the project or a referenced assembly.</span></span> <span data-ttu-id="daad0-162">Kompilator będzie ostrzeżenie, jeśli nie można rozpoznać jego wartość.</span><span class="sxs-lookup"><span data-stu-id="daad0-162">The compiler will issue a warning if its value cannot be resolved.</span></span>

### <a name="ltseegt"></a><span data-ttu-id="daad0-163">&lt;Zobacz&gt;</span><span class="sxs-lookup"><span data-stu-id="daad0-163">&lt;see&gt;</span></span>

<span data-ttu-id="daad0-164">`<see>` Tagu umożliwia tworzenie łączem do strony dokumentacji dla innego elementu kodu.</span><span class="sxs-lookup"><span data-stu-id="daad0-164">The `<see>` tag lets you create a clickable link to a documentation page for another code element.</span></span> <span data-ttu-id="daad0-165">W naszym przykładzie dalej, utworzymy łączem między tymi dwoma `Add` metody.</span><span class="sxs-lookup"><span data-stu-id="daad0-165">In our next example, we'll create a clickable link between the two `Add` methods.</span></span>

[!code-csharp[See Tag](../../samples/snippets/csharp/concepts/codedoc/see-tag.cs)]

<span data-ttu-id="daad0-166">`cref` Jest **wymagane** atrybut, który reprezentuje odwołanie do typu lub jego element członkowski, który jest dostępny w bieżącym środowisku kompilacji.</span><span class="sxs-lookup"><span data-stu-id="daad0-166">The `cref` is a **required** attribute that represents a reference to a type or its member that is available from the current compilation environment.</span></span> <span data-ttu-id="daad0-167">Może to być dowolny typ zdefiniowany w projekcie lub przywoływanego zestawu.</span><span class="sxs-lookup"><span data-stu-id="daad0-167">This can be any type defined in the project or a referenced assembly.</span></span>

### <a name="ltseealsogt"></a><span data-ttu-id="daad0-168">&lt;SeeAlso&gt;</span><span class="sxs-lookup"><span data-stu-id="daad0-168">&lt;seealso&gt;</span></span>

<span data-ttu-id="daad0-169">Możesz użyć `<seealso>` tag w taki sam sposób jak `<see>` tagu.</span><span class="sxs-lookup"><span data-stu-id="daad0-169">You use the `<seealso>` tag in the same way you do the `<see>` tag.</span></span> <span data-ttu-id="daad0-170">Jedyna różnica polega na tym, że jego zawartość jest zwykle umieszczane w sekcji "Zobacz też".</span><span class="sxs-lookup"><span data-stu-id="daad0-170">The only difference is that its content is typically placed in a "See Also" section.</span></span> <span data-ttu-id="daad0-171">W tym miejscu dodamy `seealso` tagu na liczbę całkowitą `Add` metodę, aby odwoływać się inne metody w klasie, które akceptują parametrów całkowitą:</span><span class="sxs-lookup"><span data-stu-id="daad0-171">Here we'll add a `seealso` tag on the integer `Add` method to reference other methods in the class that accept integer parameters:</span></span>

[!code-csharp[Seealso Tag](../../samples/snippets/csharp/concepts/codedoc/seealso-tag.cs)]

<span data-ttu-id="daad0-172">`cref` Atrybut reprezentuje odwołanie do typu lub jego element członkowski, który jest dostępny w bieżącym środowisku kompilacji.</span><span class="sxs-lookup"><span data-stu-id="daad0-172">The `cref` attribute represents a reference to a type or its member that is available from the current compilation environment.</span></span>
<span data-ttu-id="daad0-173">Może to być dowolny typ zdefiniowany w projekcie lub przywoływanego zestawu.</span><span class="sxs-lookup"><span data-stu-id="daad0-173">This can be any type defined in the project or a referenced assembly.</span></span>

### <a name="ltparamgt"></a><span data-ttu-id="daad0-174">&lt;param&gt;</span><span class="sxs-lookup"><span data-stu-id="daad0-174">&lt;param&gt;</span></span>

<span data-ttu-id="daad0-175">Możesz użyć `<param>` tag do opisywania parametry metody.</span><span class="sxs-lookup"><span data-stu-id="daad0-175">You use the `<param>` tag to describe a method's parameters.</span></span> <span data-ttu-id="daad0-176">Oto przykład na podwójnego `Add` — metoda: określono parametr tag opisano w **wymagane** `name` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="daad0-176">Here's an example on the double `Add` method: The parameter the tag describes is specified in the **required** `name` attribute.</span></span>

[!code-csharp[Param Tag](../../samples/snippets/csharp/concepts/codedoc/param-tag.cs)]

### <a name="lttypeparamgt"></a><span data-ttu-id="daad0-177">&lt;typeparam&gt;</span><span class="sxs-lookup"><span data-stu-id="daad0-177">&lt;typeparam&gt;</span></span>

<span data-ttu-id="daad0-178">Możesz użyć `<typeparam>` znacznik, podobnie jak `<param>` tag, ale ogólnym typie lub metodzie deklaracje do opisywania parametru ogólnego.</span><span class="sxs-lookup"><span data-stu-id="daad0-178">You use `<typeparam>` tag just like the `<param>` tag but for generic type or method declarations to describe a generic parameter.</span></span>
<span data-ttu-id="daad0-179">Dodaj szybka metoda ogólna do Twojej `Math` klasę, aby sprawdzić, czy ilości jest większa od innego.</span><span class="sxs-lookup"><span data-stu-id="daad0-179">Add a quick generic method to your `Math` class to check if one quantity is greater than another.</span></span>

[!code-csharp[Typeparam Tag](../../samples/snippets/csharp/concepts/codedoc/typeparam-tag.cs)]

### <a name="ltparamrefgt"></a><span data-ttu-id="daad0-180">&lt;paramref&gt;</span><span class="sxs-lookup"><span data-stu-id="daad0-180">&lt;paramref&gt;</span></span>

<span data-ttu-id="daad0-181">Czasami może być środku opisujące, w jakie mogą być czego metody `<summary>` tag, a może chcesz odwołać się do parametru.</span><span class="sxs-lookup"><span data-stu-id="daad0-181">Sometimes you might be in the middle of describing what a method does in what could be a `<summary>` tag, and you might want to make a reference to a parameter.</span></span> <span data-ttu-id="daad0-182">`<paramref>` Tag jest doskonałym rozwiązaniem dla tego właśnie.</span><span class="sxs-lookup"><span data-stu-id="daad0-182">The `<paramref>` tag is great for just this.</span></span> <span data-ttu-id="daad0-183">Załóżmy na podstawie aktualizacji podsumowanie naszych o podwójnej precyzji `Add` metody.</span><span class="sxs-lookup"><span data-stu-id="daad0-183">Let's update the summary of our double based `Add` method.</span></span> <span data-ttu-id="daad0-184">Podobnie jak `<param>` określono nazwę parametru w tagu **wymagane** `name` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="daad0-184">Like the `<param>` tag the parameter name is specified in the **required** `name` attribute.</span></span>

[!code-csharp[Paramref Tag](../../samples/snippets/csharp/concepts/codedoc/paramref-tag.cs)]

### <a name="lttypeparamrefgt"></a><span data-ttu-id="daad0-185">&lt;typeparamref&gt;</span><span class="sxs-lookup"><span data-stu-id="daad0-185">&lt;typeparamref&gt;</span></span>

<span data-ttu-id="daad0-186">Możesz użyć `<typeparamref>` znacznik, podobnie jak `<paramref>` tag, ale ogólnym typie lub metodzie deklaracje do opisywania parametru ogólnego.</span><span class="sxs-lookup"><span data-stu-id="daad0-186">You use `<typeparamref>` tag just like the `<paramref>` tag but for generic type or method declarations to describe a generic parameter.</span></span>
<span data-ttu-id="daad0-187">Można użyć tej samej metody ogólnej utworzonych wcześniej.</span><span class="sxs-lookup"><span data-stu-id="daad0-187">You can use the same generic method you previously created.</span></span>

[!code-csharp[Typeparamref Tag](../../samples/snippets/csharp/concepts/codedoc/typeparamref-tag.cs)]

### <a name="ltlistgt"></a><span data-ttu-id="daad0-188">&lt;Lista&gt;</span><span class="sxs-lookup"><span data-stu-id="daad0-188">&lt;list&gt;</span></span>

<span data-ttu-id="daad0-189">Możesz użyć `<list>` tag do dokumentacji informacji o formacie listy uporządkowanej, Lista nieuporządkowana lub tabeli.</span><span class="sxs-lookup"><span data-stu-id="daad0-189">You use the `<list>` tag to format documentation information as an ordered list, unordered list or table.</span></span>
<span data-ttu-id="daad0-190">Wprowadź nieuporządkowaną listę każdej operacji matematycznych Twojej `Math` obsługuje biblioteki.</span><span class="sxs-lookup"><span data-stu-id="daad0-190">Make an unordered list of every math operation your `Math` library supports.</span></span>

[!code-csharp[List Tag](../../samples/snippets/csharp/concepts/codedoc/list-tag.cs)]

<span data-ttu-id="daad0-191">Można wprowadzić listy uporządkowanej lub tabeli, zmieniając `type` atrybutu `number` lub `table`odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="daad0-191">You can make an ordered list or table by changing the `type` attribute to `number` or `table`, respectively.</span></span>

### <a name="putting-it-all-together"></a><span data-ttu-id="daad0-192">Składanie wszystkiego razem</span><span class="sxs-lookup"><span data-stu-id="daad0-192">Putting it all together</span></span>

<span data-ttu-id="daad0-193">Jeśli już zostały wykonane w tym samouczku i zastosować znaczniki w kodzie, w miarę potrzeby, kodu powinna wyglądać podobnie do poniższej:</span><span class="sxs-lookup"><span data-stu-id="daad0-193">If you've followed this tutorial and applied the tags to your code where necessary, your code should now look similar to the following:</span></span>

[!code-csharp[Tagged Library](../../samples/snippets/csharp/concepts/codedoc/tagged-library.cs)]

<span data-ttu-id="daad0-194">W kodzie można wygenerować szczegółowa dokumentacja witryny sieci Web z odsyłacze aktywne.</span><span class="sxs-lookup"><span data-stu-id="daad0-194">From your code, you can generate a detailed documentation website complete with clickable cross-references.</span></span> <span data-ttu-id="daad0-195">Ale jest skierowany w innym problemów z: kod stał się trudny do odczytania.</span><span class="sxs-lookup"><span data-stu-id="daad0-195">But you're faced with another problem: your code has become hard to read.</span></span>
<span data-ttu-id="daad0-196">Ma tak dużej ilości informacji do przesiania, to ma być nightmare dla Każdy deweloper, który chce przyczyniają się do tego kodu.</span><span class="sxs-lookup"><span data-stu-id="daad0-196">There's so much information to sift through that this is going to be a nightmare for any developer who wants to contribute to this code.</span></span> <span data-ttu-id="daad0-197">Brak thankfully tagu XML, które mogą pomóc biznesowych w radzeniu sobie z tym:</span><span class="sxs-lookup"><span data-stu-id="daad0-197">Thankfully there's an XML tag that can help you deal with this:</span></span>

### <a name="ltincludegt"></a><span data-ttu-id="daad0-198">&lt;obejmują&gt;</span><span class="sxs-lookup"><span data-stu-id="daad0-198">&lt;include&gt;</span></span>

<span data-ttu-id="daad0-199">`<include>` Należy odwoływać się do komentarzy w osobnym pliku XML, które opisują typy i elementy członkowskie w kodzie źródłowym, w przeciwieństwie do wprowadzania komentarzy do dokumentacji bezpośrednio w pliku kodu źródłowego.</span><span class="sxs-lookup"><span data-stu-id="daad0-199">The `<include>` tag lets you refer to comments in a separate XML file that describe the types and members in your source code, as opposed to placing documentation comments directly in your source code file.</span></span>

<span data-ttu-id="daad0-200">Teraz możesz zacząć Przenieś wszystkie tagi XML do oddzielnego pliku XML o nazwie `docs.xml`.</span><span class="sxs-lookup"><span data-stu-id="daad0-200">Now you're going to move all your XML tags into a separate XML file named `docs.xml`.</span></span> <span data-ttu-id="daad0-201">Możesz także nazwę pliku dowolne.</span><span class="sxs-lookup"><span data-stu-id="daad0-201">Feel free to name the file whatever you want.</span></span>

[!code-xml[Sample XML](../../samples/snippets/csharp/concepts/codedoc/include.xml)]

<span data-ttu-id="daad0-202">W powyższym kodzie XML każdy element członkowski komentarzy dokumentacji są wyświetlane bezpośrednio wewnątrz tagu o nazwie po ich działania.</span><span class="sxs-lookup"><span data-stu-id="daad0-202">In the above XML, each member's documentation comments appear directly inside a tag named after what they do.</span></span> <span data-ttu-id="daad0-203">Możesz wybrać własne strategii.</span><span class="sxs-lookup"><span data-stu-id="daad0-203">You can choose your own strategy.</span></span> <span data-ttu-id="daad0-204">Teraz, gdy masz komentarz XML w osobnym pliku Zobaczmy, jak kod może się bardziej czytelny przy użyciu `<include>` tagu:</span><span class="sxs-lookup"><span data-stu-id="daad0-204">Now that you have your XML comments in a separate file, let's see how your code can be made more readable by using the `<include>` tag:</span></span>

[!code-csharp[Include Tag](../../samples/snippets/csharp/concepts/codedoc/include-tag.cs)]

<span data-ttu-id="daad0-205">I mają: naszego kodu jest do jest do odczytu i utracono żadnych informacji w dokumentacji.</span><span class="sxs-lookup"><span data-stu-id="daad0-205">And there you have it: our code is back to being readable, and no documentation information has been lost.</span></span> 

<span data-ttu-id="daad0-206">`filename` Atrybut reprezentuje nazwę pliku XML zawierającego w dokumentacji.</span><span class="sxs-lookup"><span data-stu-id="daad0-206">The `filename` attribute represents the name of the XML file containing the documentation.</span></span>

<span data-ttu-id="daad0-207">`path` Atrybutu reprezentuje [XPath](https://msdn.microsoft.com/library/ms256115.aspx) kwerendę `tag name` w określonym `filename`.</span><span class="sxs-lookup"><span data-stu-id="daad0-207">The `path` attribute represents an [XPath](https://msdn.microsoft.com/library/ms256115.aspx) query to the `tag name` present in the specified `filename`.</span></span>

<span data-ttu-id="daad0-208">`name` Atrybut reprezentuje określenie nazwy w tagu poprzedzający komentarze.</span><span class="sxs-lookup"><span data-stu-id="daad0-208">The `name` attribute represents the name specifier in the tag that precedes the comments.</span></span>

<span data-ttu-id="daad0-209">`id` Atrybut, którego można użyć zamiast `name` reprezentuje identyfikator tagu poprzedzający komentarze.</span><span class="sxs-lookup"><span data-stu-id="daad0-209">The `id` attribute which can be used in place of `name` represents the ID for the tag that precedes the comments.</span></span>

### <a name="user-defined-tags"></a><span data-ttu-id="daad0-210">Tagi zdefiniowane przez użytkownika</span><span class="sxs-lookup"><span data-stu-id="daad0-210">User Defined Tags</span></span>

<span data-ttu-id="daad0-211">Wszystkie znaczniki opisanych powyżej reprezentują te, które są rozpoznawane przez kompilator języka C#.</span><span class="sxs-lookup"><span data-stu-id="daad0-211">All the tags outlined above represent those that are recognized by the C# compiler.</span></span> <span data-ttu-id="daad0-212">Jednak użytkownik jest bezpłatna do zdefiniowania własnych tagów.</span><span class="sxs-lookup"><span data-stu-id="daad0-212">However, a user is free to define their own tags.</span></span>
<span data-ttu-id="daad0-213">Narzędzia, takie jak Sandcastle Przełącz pomocy technicznej dla dodatkowych tagów, takich jak [ `<event>` ](http://ewsoftware.github.io/XMLCommentsGuide/html/81bf7ad3-45dc-452f-90d5-87ce2494a182.htm), [ `<note>` ](http://ewsoftware.github.io/XMLCommentsGuide/html/4302a60f-e4f4-4b8d-a451-5f453c4ebd46.htm) i obsługa nawet [dokumentowanie przestrzenie nazw](http://ewsoftware.github.io/XMLCommentsGuide/html/BD91FAD4-188D-4697-A654-7C07FD47EF31.htm).</span><span class="sxs-lookup"><span data-stu-id="daad0-213">Tools like Sandcastle bring support for extra tags like [`<event>`](http://ewsoftware.github.io/XMLCommentsGuide/html/81bf7ad3-45dc-452f-90d5-87ce2494a182.htm), [`<note>`](http://ewsoftware.github.io/XMLCommentsGuide/html/4302a60f-e4f4-4b8d-a451-5f453c4ebd46.htm) and even support [documenting namespaces](http://ewsoftware.github.io/XMLCommentsGuide/html/BD91FAD4-188D-4697-A654-7C07FD47EF31.htm).</span></span>
<span data-ttu-id="daad0-214">Niestandardowe lub narzędzia generowania dokumentacji wewnętrznych można również używać razem standardowych znaczników i mogą być obsługiwane wielu danych wyjściowych w formacie HTML do pliku PDF.</span><span class="sxs-lookup"><span data-stu-id="daad0-214">Custom or in-house documentation generation tools can also be used with the standard tags and multiple output formats from HTML to PDF can be supported.</span></span>

## <a name="recommendations"></a><span data-ttu-id="daad0-215">Zalecenia</span><span class="sxs-lookup"><span data-stu-id="daad0-215">Recommendations</span></span>

<span data-ttu-id="daad0-216">Dokumentowanie kodu jest zalecane z wielu powodów.</span><span class="sxs-lookup"><span data-stu-id="daad0-216">Documenting code is recommended for many reasons.</span></span> <span data-ttu-id="daad0-217">Jakie następujące przedstawiono najlepsze rozwiązania, ogólne Użyj scenariuszy przypadków i rzeczy, które należy poznać po użyciu dokumentacji XML tagów w kodzie C#.</span><span class="sxs-lookup"><span data-stu-id="daad0-217">What follows are some best practices, general use case scenarios, and things that you should know when using XML documentation tags in your C# code.</span></span>

* <span data-ttu-id="daad0-218">Dla spójności wszystkie typy widocznego publicznie i ich elementy Członkowskie powinny być udokumentowane.</span><span class="sxs-lookup"><span data-stu-id="daad0-218">For the sake of consistency, all publicly visible types and their members should be documented.</span></span> <span data-ttu-id="daad0-219">Jeśli musisz to zrobić, wykonaj wszystkie.</span><span class="sxs-lookup"><span data-stu-id="daad0-219">If you must do it, do it all.</span></span>
* <span data-ttu-id="daad0-220">Prywatne elementy Członkowskie mogą również opisane przy użyciu komentarze XML.</span><span class="sxs-lookup"><span data-stu-id="daad0-220">Private members can also be documented using XML comments.</span></span> <span data-ttu-id="daad0-221">Jednak ten opisuje przebiega (potencjalnie poufnych) biblioteki.</span><span class="sxs-lookup"><span data-stu-id="daad0-221">However, this exposes the inner (potentially confidential) workings of your library.</span></span>
* <span data-ttu-id="daad0-222">Co najmniej systemu od zera, typy i ich elementy Członkowskie powinny mieć `<summary>` tagu, ponieważ jego zawartość jest wymagane przez funkcję IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="daad0-222">At a bare minimum, types and their members should have a `<summary>` tag because its content is needed for IntelliSense.</span></span>
* <span data-ttu-id="daad0-223">Tekst dokumentacji powinna być zapisana przy użyciu pełnych zdań kończąc stopnie.</span><span class="sxs-lookup"><span data-stu-id="daad0-223">Documentation text should be written using complete sentences ending with full stops.</span></span>
* <span data-ttu-id="daad0-224">Klasy częściowe są w pełni obsługiwane, a dokumentacji informacji zostanie łączone w pojedynczy wpis dla tego typu.</span><span class="sxs-lookup"><span data-stu-id="daad0-224">Partial classes are fully supported, and documentation information will be concatenated into a single entry for that type.</span></span>
* <span data-ttu-id="daad0-225">Kompilator sprawdza składnię `<exception>`, `<include>`, `<param>`, `<see>`, `<seealso>` i `<typeparam>` tagów.</span><span class="sxs-lookup"><span data-stu-id="daad0-225">The compiler verifies the syntax of the `<exception>`, `<include>`, `<param>`, `<see>`, `<seealso>` and `<typeparam>` tags.</span></span>
- <span data-ttu-id="daad0-226">Kompilator sprawdza poprawność parametrów, które zawierają ścieżki pliku i odwołania do innych części kodu.</span><span class="sxs-lookup"><span data-stu-id="daad0-226">The compiler validates the parameters that contain file paths and references to other parts of the code.</span></span>

## <a name="see-also"></a><span data-ttu-id="daad0-227">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="daad0-227">See also</span></span>
[<span data-ttu-id="daad0-228">Komentarze dokumentacji XML (C# przewodnik programowania w języku)</span><span class="sxs-lookup"><span data-stu-id="daad0-228">XML Documentation Comments (C# Programming Guide)</span></span>](programming-guide/xmldoc/xml-documentation-comments.md)

[<span data-ttu-id="daad0-229">Tagi zalecane dla komentarzy do dokumentacji (C# przewodnik programowania w języku)</span><span class="sxs-lookup"><span data-stu-id="daad0-229">Recommended Tags for Documentation Comments (C# Programming Guide)</span></span>](programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)
