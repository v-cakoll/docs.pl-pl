---
title: Dokumentowanie kodu za pomocą komentarzy XML
description: Dowiedz się, jak udokumentować kod za pomocą komentarzy do dokumentacji XML i wygenerować plik dokumentacji XML w czasie kompilacji.
ms.date: 01/21/2020
ms.technology: csharp-fundamentals
ms.assetid: 8e75e317-4a55-45f2-a866-e76124171838
ms.openlocfilehash: 1ed39c4733c36b3932fcb85bf50d4f4c0e53aa6f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79146320"
---
# <a name="document-your-code-with-xml-comments"></a><span data-ttu-id="d85e5-103">Dokumentowanie kodu za pomocą komentarzy XML</span><span class="sxs-lookup"><span data-stu-id="d85e5-103">Document your code with XML comments</span></span>

<span data-ttu-id="d85e5-104">Komentarze do dokumentacji XML są specjalnym rodzajem komentarza, dodanego powyżej definicji dowolnego typu zdefiniowanego przez użytkownika lub elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="d85e5-104">XML documentation comments are a special kind of comment, added above the definition of any user-defined type or member.</span></span>
<span data-ttu-id="d85e5-105">Są one specjalne, ponieważ mogą być przetwarzane przez kompilator do generowania pliku dokumentacji XML w czasie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="d85e5-105">They are special because they can be processed by the compiler to generate an XML documentation file at compile time.</span></span>
<span data-ttu-id="d85e5-106">Plik XML wygenerowany przez kompilator może być rozpowszechniany wraz z zestawem .NET, dzięki czemu visual studio i inne identyfikatory mogą używać intelliSense do pokazywania szybkich informacji o typach lub członkach.</span><span class="sxs-lookup"><span data-stu-id="d85e5-106">The compiler-generated XML file can be distributed alongside your .NET assembly so that Visual Studio and other IDEs can use IntelliSense to show quick information about types or members.</span></span> <span data-ttu-id="d85e5-107">Ponadto plik XML można uruchomić za pomocą narzędzi, takich jak [DocFX](https://dotnet.github.io/docfx/) i [Sandcastle,](https://github.com/EWSoftware/SHFB) aby wygenerować witryny referencyjne API.</span><span class="sxs-lookup"><span data-stu-id="d85e5-107">Additionally, the XML file can be run through tools like [DocFX](https://dotnet.github.io/docfx/) and [Sandcastle](https://github.com/EWSoftware/SHFB) to generate API reference websites.</span></span>

<span data-ttu-id="d85e5-108">Komentarze dokumentacji XML, podobnie jak wszystkie inne komentarze, są ignorowane przez kompilator.</span><span class="sxs-lookup"><span data-stu-id="d85e5-108">XML documentation comments, like all other comments, are ignored by the compiler.</span></span>

<span data-ttu-id="d85e5-109">Plik XML można wygenerować w czasie kompilacji, wykonując jedną z następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="d85e5-109">You can generate the XML file at compile time by doing one of the following:</span></span>

- <span data-ttu-id="d85e5-110">Jeśli tworzysz aplikację z .NET Core z wiersza `GenerateDocumentationFile` polecenia, `<PropertyGroup>` możesz dodać element do sekcji pliku projektu csproj.</span><span class="sxs-lookup"><span data-stu-id="d85e5-110">If you are developing an application with .NET Core from the command line, you can add a `GenerateDocumentationFile` element to the `<PropertyGroup>` section of your .csproj project file.</span></span> <span data-ttu-id="d85e5-111">Ścieżkę do pliku dokumentacji można [ `DocumentationFile` ](/visualstudio/msbuild/common-msbuild-project-properties)również określić bezpośrednio za pomocą elementu .</span><span class="sxs-lookup"><span data-stu-id="d85e5-111">You can also specify the path to the documentation file directly using [`DocumentationFile` element](/visualstudio/msbuild/common-msbuild-project-properties).</span></span> <span data-ttu-id="d85e5-112">Poniższy przykład generuje plik XML w katalogu projektu o tej samej głównej nazwie pliku co zestaw:</span><span class="sxs-lookup"><span data-stu-id="d85e5-112">The following example generates an XML file in the project directory with the same root filename as the assembly:</span></span>

   ```xml
   <GenerateDocumentationFile>true</GenerateDocumentationFile>
   ```

   <span data-ttu-id="d85e5-113">Jest to równoważne z następującymi kwestiami:</span><span class="sxs-lookup"><span data-stu-id="d85e5-113">This is equivalent to the following:</span></span>

   ```xml
   <DocumentationFile>bin\$(Configuration)\$(TargetFramework)\$(AssemblyName).xml</DocumentationFile>
   ```

- <span data-ttu-id="d85e5-114">Jeśli tworzysz aplikację za pomocą programu Visual Studio, kliknij prawym przyciskiem myszy projekt i wybierz **polecenie Właściwości**.</span><span class="sxs-lookup"><span data-stu-id="d85e5-114">If you are developing an application using Visual Studio, right-click on the project and select **Properties**.</span></span> <span data-ttu-id="d85e5-115">W oknie dialogowym właściwości wybierz kartę **Kompilacja** i sprawdź **plik dokumentacji XML**.</span><span class="sxs-lookup"><span data-stu-id="d85e5-115">In the properties dialog, select the **Build** tab, and check **XML documentation file**.</span></span> <span data-ttu-id="d85e5-116">Można również zmienić lokalizację, do której kompilator zapisuje plik.</span><span class="sxs-lookup"><span data-stu-id="d85e5-116">You can also change the location to which the compiler writes the file.</span></span>

- <span data-ttu-id="d85e5-117">Jeśli kompilacja aplikacji .NET Framework z wiersza polecenia, dodaj [opcję kompilatora -doc](language-reference/compiler-options/doc-compiler-option.md) podczas kompilowania.</span><span class="sxs-lookup"><span data-stu-id="d85e5-117">If you are compiling a .NET Framework application from the command line, add the [-doc compiler option](language-reference/compiler-options/doc-compiler-option.md) when compiling.</span></span>  

<span data-ttu-id="d85e5-118">Komentarze do dokumentacji XML`///`używają potrójnych ukośników do przodu ( ) i treści komentarzy w formacie XML.</span><span class="sxs-lookup"><span data-stu-id="d85e5-118">XML documentation comments use triple forward slashes (`///`) and an XML formatted comment body.</span></span> <span data-ttu-id="d85e5-119">Przykład:</span><span class="sxs-lookup"><span data-stu-id="d85e5-119">For example:</span></span>

[!code-csharp[XML Documentation Comment](../../samples/snippets/csharp/concepts/codedoc/xml-comment.cs)]

## <a name="walkthrough"></a><span data-ttu-id="d85e5-120">Przewodnik</span><span class="sxs-lookup"><span data-stu-id="d85e5-120">Walkthrough</span></span>

<span data-ttu-id="d85e5-121">Przejdźmy przez dokumentowanie bardzo podstawowej biblioteki matematycznej, aby ułatwić nowym deweloperom zrozumienie/przyczynienie się i korzystanie z niej przez programistów innych firm.</span><span class="sxs-lookup"><span data-stu-id="d85e5-121">Let's walk through documenting a very basic math library to make it easy for new developers to understand/contribute and for third-party developers to use.</span></span>

<span data-ttu-id="d85e5-122">Oto kod prostej biblioteki matematycznej:</span><span class="sxs-lookup"><span data-stu-id="d85e5-122">Here's code for the simple math library:</span></span>

[!code-csharp[Sample Library](../../samples/snippets/csharp/concepts/codedoc/sample-library.cs)]

<span data-ttu-id="d85e5-123">Przykładowa biblioteka obsługuje cztery główne operacje `subtract` `multiply`arytmetyczne `int` ( `double` `add`, , i `divide`) i typy danych.</span><span class="sxs-lookup"><span data-stu-id="d85e5-123">The sample library supports four major arithmetic operations (`add`, `subtract`, `multiply`, and `divide`) on `int` and `double` data types.</span></span>

<span data-ttu-id="d85e5-124">Teraz chcesz mieć możliwość tworzenia dokumentu referencyjnego interfejsu API z kodu dla innych deweloperów, którzy korzystają z biblioteki, ale nie mają dostępu do kodu źródłowego.</span><span class="sxs-lookup"><span data-stu-id="d85e5-124">Now you want to be able to create an API reference document from your code for third-party developers who use your library but don't have access to the source code.</span></span>
<span data-ttu-id="d85e5-125">Jak wspomniano wcześniej tagów dokumentacji XML można użyć do osiągnięcia tego celu.</span><span class="sxs-lookup"><span data-stu-id="d85e5-125">As mentioned earlier XML documentation tags can be used to achieve this.</span></span> <span data-ttu-id="d85e5-126">Teraz zostaniewprowadzony do standardowych tagów XML kompilator C# obsługuje.</span><span class="sxs-lookup"><span data-stu-id="d85e5-126">You will now be introduced to the standard XML tags the C# compiler supports.</span></span>

## <a name="summary"></a><span data-ttu-id="d85e5-127">\<summary></span><span class="sxs-lookup"><span data-stu-id="d85e5-127">\<summary></span></span>

<span data-ttu-id="d85e5-128">Tag `<summary>` dodaje krótkie informacje o typie lub elecie członkowskim.</span><span class="sxs-lookup"><span data-stu-id="d85e5-128">The `<summary>` tag adds brief information about a type or member.</span></span>
<span data-ttu-id="d85e5-129">Zademonstruję jego użycie, dodając `Math` go do `Add` definicji klasy i pierwszej metody.</span><span class="sxs-lookup"><span data-stu-id="d85e5-129">I'll demonstrate its use by adding it to the `Math` class definition and the first `Add` method.</span></span> <span data-ttu-id="d85e5-130">Możesz zastosować go do reszty kodu.</span><span class="sxs-lookup"><span data-stu-id="d85e5-130">Feel free to apply it to the rest of your code.</span></span>

[!code-csharp[Summary Tag](~/samples/snippets/csharp/concepts/codedoc/summary-tag.cs)]

<span data-ttu-id="d85e5-131">Tag `<summary>` jest ważny i zaleca się dołączenie go, ponieważ jego zawartość jest podstawowym źródłem informacji o typie lub członka w intelliSense lub dokumencie referencyjnym interfejsu API.</span><span class="sxs-lookup"><span data-stu-id="d85e5-131">The `<summary>` tag is important, and we recommend that you include it because its content is the primary source of type or member information in IntelliSense or an API reference document.</span></span>

## <a name="remarks"></a><span data-ttu-id="d85e5-132">\<uwagi></span><span class="sxs-lookup"><span data-stu-id="d85e5-132">\<remarks></span></span>

<span data-ttu-id="d85e5-133">Tag `<remarks>` uzupełnia informacje o typach `<summary>` lub członkach, które zapewnia tag.</span><span class="sxs-lookup"><span data-stu-id="d85e5-133">The `<remarks>` tag supplements the information about types or members that the `<summary>` tag provides.</span></span> <span data-ttu-id="d85e5-134">W tym przykładzie po prostu dodasz go do klasy.</span><span class="sxs-lookup"><span data-stu-id="d85e5-134">In this example, you'll just add it to the class.</span></span>

[!code-csharp[Remarks Tag](~/samples/snippets/csharp/concepts/codedoc/remarks-tag.cs)]

## <a name="returns"></a><span data-ttu-id="d85e5-135">\<returns></span><span class="sxs-lookup"><span data-stu-id="d85e5-135">\<returns></span></span>

<span data-ttu-id="d85e5-136">Tag `<returns>` opisuje wartość zwracaną deklaracji metody.</span><span class="sxs-lookup"><span data-stu-id="d85e5-136">The `<returns>` tag describes the return value of a method declaration.</span></span>
<span data-ttu-id="d85e5-137">Podobnie jak poprzednio, w `<returns>` poniższym `Add` przykładzie przedstawiono tag na pierwszej metody.</span><span class="sxs-lookup"><span data-stu-id="d85e5-137">As before, the following example illustrates the `<returns>` tag on the first `Add` method.</span></span> <span data-ttu-id="d85e5-138">Możesz zrobić to samo na innych metodach.</span><span class="sxs-lookup"><span data-stu-id="d85e5-138">You can do the same on other methods.</span></span>

[!code-csharp[Returns Tag](~/samples/snippets/csharp/concepts/codedoc/returns-tag.cs)]

## <a name="value"></a><span data-ttu-id="d85e5-139">\<value></span><span class="sxs-lookup"><span data-stu-id="d85e5-139">\<value></span></span>

<span data-ttu-id="d85e5-140">Tag `<value>` jest podobny `<returns>` do znacznika, z tą różnicą, że używasz go do właściwości.</span><span class="sxs-lookup"><span data-stu-id="d85e5-140">The `<value>` tag is similar to the `<returns>` tag, except that you use it for properties.</span></span>
<span data-ttu-id="d85e5-141">Zakładając, `Math` że biblioteka ma `PI`statyczną właściwość o nazwie , oto jak użyć tego tagu:</span><span class="sxs-lookup"><span data-stu-id="d85e5-141">Assuming your `Math` library had a static property called `PI`, here's how you'd use this tag:</span></span>

[!code-csharp[Value Tag](~/samples/snippets/csharp/concepts/codedoc/value-tag.cs)]

## <a name="example"></a><span data-ttu-id="d85e5-142">\<przykład></span><span class="sxs-lookup"><span data-stu-id="d85e5-142">\<example></span></span>

<span data-ttu-id="d85e5-143">Tag służy `<example>` do dołączania przykładu do dokumentacji XML.</span><span class="sxs-lookup"><span data-stu-id="d85e5-143">You use the `<example>` tag to include an example in your XML documentation.</span></span>
<span data-ttu-id="d85e5-144">Wiąże się to `<code>` z użyciem tagu podrzędnego.</span><span class="sxs-lookup"><span data-stu-id="d85e5-144">This involves using the child `<code>` tag.</span></span>

[!code-csharp[Example Tag](~/samples/snippets/csharp/concepts/codedoc/example-tag.cs)]

<span data-ttu-id="d85e5-145">Znacznik `code` zachowuje podziały wierszy i wcięcia dla dłuższych przykładów.</span><span class="sxs-lookup"><span data-stu-id="d85e5-145">The `code` tag preserves line breaks and indentation for longer examples.</span></span>

## <a name="para"></a><span data-ttu-id="d85e5-146">\<para></span><span class="sxs-lookup"><span data-stu-id="d85e5-146">\<para></span></span>

<span data-ttu-id="d85e5-147">Tag służy `<para>` do formatowania zawartości w tagu nadrzędnym.</span><span class="sxs-lookup"><span data-stu-id="d85e5-147">You use the `<para>` tag to format the content within its parent tag.</span></span> <span data-ttu-id="d85e5-148">`<para>`jest zwykle używany wewnątrz znacznika, na przykład `<remarks>` lub `<returns>`, do dzielenia tekstu na akapity.</span><span class="sxs-lookup"><span data-stu-id="d85e5-148">`<para>` is usually used inside a tag, such as `<remarks>` or `<returns>`, to divide text into paragraphs.</span></span>
<span data-ttu-id="d85e5-149">Zawartość tagu `<remarks>` dla definicji klasy można sformatować.</span><span class="sxs-lookup"><span data-stu-id="d85e5-149">You can format the contents of the `<remarks>` tag for your class definition.</span></span>

[!code-csharp[Para Tag](~/samples/snippets/csharp/concepts/codedoc/para-tag.cs)]

## <a name="c"></a><span data-ttu-id="d85e5-150">\<c></span><span class="sxs-lookup"><span data-stu-id="d85e5-150">\<c></span></span>

<span data-ttu-id="d85e5-151">Nadal na temat formatowania, używasz `<c>` znacznika do oznaczania części tekstu jako kod.</span><span class="sxs-lookup"><span data-stu-id="d85e5-151">Still on the topic of formatting, you use the `<c>` tag for marking part of text as code.</span></span>
<span data-ttu-id="d85e5-152">To jak tag, `<code>` ale wbudowany.</span><span class="sxs-lookup"><span data-stu-id="d85e5-152">It's like the `<code>` tag but inline.</span></span> <span data-ttu-id="d85e5-153">Jest to przydatne, gdy chcesz pokazać przykład szybkiego kodu jako część zawartości tagu.</span><span class="sxs-lookup"><span data-stu-id="d85e5-153">It's useful when you want to show a quick code example as part of a tag's content.</span></span>
<span data-ttu-id="d85e5-154">Zaktualizujmy dokumentację `Math` dla klasy.</span><span class="sxs-lookup"><span data-stu-id="d85e5-154">Let's update the documentation for the `Math` class.</span></span>

[!code-csharp[C Tag](~/samples/snippets/csharp/concepts/codedoc/c-tag.cs)]

## <a name="exception"></a><span data-ttu-id="d85e5-155">\<> wyjątek</span><span class="sxs-lookup"><span data-stu-id="d85e5-155">\<exception></span></span>

<span data-ttu-id="d85e5-156">Za pomocą `<exception>` tagu, poinformować deweloperów, że metoda może zgłaszać określone wyjątki.</span><span class="sxs-lookup"><span data-stu-id="d85e5-156">By using the `<exception>` tag, you let your developers know that a method can throw specific exceptions.</span></span>
<span data-ttu-id="d85e5-157">Patrząc na `Math` bibliotekę, można `Add` zobaczyć, że obie metody zgłosić wyjątek, jeśli określony warunek jest spełniony.</span><span class="sxs-lookup"><span data-stu-id="d85e5-157">Looking at your `Math` library, you can see that both `Add` methods throw an exception if a certain condition is met.</span></span> <span data-ttu-id="d85e5-158">Nie jest to jednak tak oczywiste, że metoda całkowita `Divide` również zgłasza, jeśli `b` parametr wynosi zero.</span><span class="sxs-lookup"><span data-stu-id="d85e5-158">Not so obvious, though, is that integer `Divide` method throws as well if the `b` parameter is zero.</span></span> <span data-ttu-id="d85e5-159">Teraz dodaj dokumentację wyjątku do tej metody.</span><span class="sxs-lookup"><span data-stu-id="d85e5-159">Now add exception documentation to this method.</span></span>

[!code-csharp[Exception Tag](~/samples/snippets/csharp/concepts/codedoc/exception-tag.cs)]

<span data-ttu-id="d85e5-160">Atrybut `cref` reprezentuje odwołanie do wyjątku, który jest dostępny z bieżącego środowiska kompilacji.</span><span class="sxs-lookup"><span data-stu-id="d85e5-160">The `cref` attribute represents a reference to an exception that is available from the current compilation environment.</span></span>
<span data-ttu-id="d85e5-161">Może to być dowolny typ zdefiniowany w projekcie lub zestaw, do którego istnieje odwołanie.</span><span class="sxs-lookup"><span data-stu-id="d85e5-161">This can be any type defined in the project or a referenced assembly.</span></span> <span data-ttu-id="d85e5-162">Kompilator wyda ostrzeżenie, jeśli jego wartość nie można rozwiązać.</span><span class="sxs-lookup"><span data-stu-id="d85e5-162">The compiler will issue a warning if its value cannot be resolved.</span></span>

## <a name="see"></a><span data-ttu-id="d85e5-163">\<zobacz></span><span class="sxs-lookup"><span data-stu-id="d85e5-163">\<see></span></span>

<span data-ttu-id="d85e5-164">Tag `<see>` umożliwia utworzenie klikalnego łącza do strony dokumentacji dla innego elementu kodu.</span><span class="sxs-lookup"><span data-stu-id="d85e5-164">The `<see>` tag lets you create a clickable link to a documentation page for another code element.</span></span> <span data-ttu-id="d85e5-165">W następnym przykładzie utworzymy klikalne łącze `Add` między tymi dwiema metodami.</span><span class="sxs-lookup"><span data-stu-id="d85e5-165">In our next example, we'll create a clickable link between the two `Add` methods.</span></span>

[!code-csharp[See Tag](~/samples/snippets/csharp/concepts/codedoc/see-tag.cs)]

<span data-ttu-id="d85e5-166">Jest `cref` **to wymagany** atrybut, który reprezentuje odwołanie do typu lub jego element członkowski, który jest dostępny z bieżącego środowiska kompilacji.</span><span class="sxs-lookup"><span data-stu-id="d85e5-166">The `cref` is a **required** attribute that represents a reference to a type or its member that is available from the current compilation environment.</span></span>
<span data-ttu-id="d85e5-167">Może to być dowolny typ zdefiniowany w projekcie lub zestaw, do którego istnieje odwołanie.</span><span class="sxs-lookup"><span data-stu-id="d85e5-167">This can be any type defined in the project or a referenced assembly.</span></span>

## <a name="seealso"></a><span data-ttu-id="d85e5-168">\<></span><span class="sxs-lookup"><span data-stu-id="d85e5-168">\<seealso></span></span>

<span data-ttu-id="d85e5-169">Tag użyje go `<seealso>` w taki `<see>` sam sposób, jak tag.</span><span class="sxs-lookup"><span data-stu-id="d85e5-169">You use the `<seealso>` tag in the same way you do the `<see>` tag.</span></span> <span data-ttu-id="d85e5-170">Jedyną różnicą jest to, że jego zawartość jest zazwyczaj umieszczana w sekcji "Zobacz też".</span><span class="sxs-lookup"><span data-stu-id="d85e5-170">The only difference is that its content is typically placed in a "See Also" section.</span></span> <span data-ttu-id="d85e5-171">W tym miejscu `seealso` dodamy znacznik metody `Add` całkowitej, aby odwołać się do innych metod w klasie, które akceptują parametry całkowite:</span><span class="sxs-lookup"><span data-stu-id="d85e5-171">Here we'll add a `seealso` tag on the integer `Add` method to reference other methods in the class that accept integer parameters:</span></span>

[!code-csharp[Seealso Tag](~/samples/snippets/csharp/concepts/codedoc/seealso-tag.cs)]

<span data-ttu-id="d85e5-172">Atrybut `cref` reprezentuje odwołanie do typu lub jego element członkowski, który jest dostępny z bieżącego środowiska kompilacji.</span><span class="sxs-lookup"><span data-stu-id="d85e5-172">The `cref` attribute represents a reference to a type or its member that is available from the current compilation environment.</span></span>
<span data-ttu-id="d85e5-173">Może to być dowolny typ zdefiniowany w projekcie lub zestaw, do którego istnieje odwołanie.</span><span class="sxs-lookup"><span data-stu-id="d85e5-173">This can be any type defined in the project or a referenced assembly.</span></span>

## <a name="param"></a><span data-ttu-id="d85e5-174">\<param></span><span class="sxs-lookup"><span data-stu-id="d85e5-174">\<param></span></span>

<span data-ttu-id="d85e5-175">Tag służy `<param>` do opisywania parametrów metody.</span><span class="sxs-lookup"><span data-stu-id="d85e5-175">You use the `<param>` tag to describe a method's parameters.</span></span> <span data-ttu-id="d85e5-176">Oto przykład na double `Add` metody: Parametr tag opisuje jest określony w **wymaganym** `name` atrybutem.</span><span class="sxs-lookup"><span data-stu-id="d85e5-176">Here's an example on the double `Add` method: The parameter the tag describes is specified in the **required** `name` attribute.</span></span>

[!code-csharp[Param Tag](~/samples/snippets/csharp/concepts/codedoc/param-tag.cs)]

## <a name="typeparam"></a><span data-ttu-id="d85e5-177">\<> typeparam</span><span class="sxs-lookup"><span data-stu-id="d85e5-177">\<typeparam></span></span>

<span data-ttu-id="d85e5-178">Tag `<typeparam>` jest używany `<param>` tak jak tag, ale dla deklaracji typu ogólnego lub metody do opisania parametru ogólnego.</span><span class="sxs-lookup"><span data-stu-id="d85e5-178">You use `<typeparam>` tag just like the `<param>` tag but for generic type or method declarations to describe a generic parameter.</span></span>
<span data-ttu-id="d85e5-179">Dodaj szybką metodę `Math` rodzajową do klasy, aby sprawdzić, czy jedna ilość jest większa niż inna.</span><span class="sxs-lookup"><span data-stu-id="d85e5-179">Add a quick generic method to your `Math` class to check if one quantity is greater than another.</span></span>

[!code-csharp[Typeparam Tag](~/samples/snippets/csharp/concepts/codedoc/typeparam-tag.cs)]

## <a name="paramref"></a><span data-ttu-id="d85e5-180">\<paramref></span><span class="sxs-lookup"><span data-stu-id="d85e5-180">\<paramref></span></span>

<span data-ttu-id="d85e5-181">Czasami może być w środku opisujące, co metoda `<summary>` robi w co może być tag i może chcesz odwołać się do parametru.</span><span class="sxs-lookup"><span data-stu-id="d85e5-181">Sometimes you might be in the middle of describing what a method does in what could be a `<summary>` tag, and you might want to make a reference to a parameter.</span></span> <span data-ttu-id="d85e5-182">Tag `<paramref>` jest świetny tylko do tego.</span><span class="sxs-lookup"><span data-stu-id="d85e5-182">The `<paramref>` tag is great for just this.</span></span> <span data-ttu-id="d85e5-183">Zaktualizujmy podsumowanie naszej metody `Add` podwójnej.</span><span class="sxs-lookup"><span data-stu-id="d85e5-183">Let's update the summary of our double based `Add` method.</span></span> <span data-ttu-id="d85e5-184">Podobnie `<param>` jak tag, nazwa parametru jest określona w **wymaganym** `name` atrybucie.</span><span class="sxs-lookup"><span data-stu-id="d85e5-184">Like the `<param>` tag, the parameter name is specified in the **required** `name` attribute.</span></span>

[!code-csharp[Paramref Tag](~/samples/snippets/csharp/concepts/codedoc/paramref-tag.cs)]

## <a name="typeparamref"></a><span data-ttu-id="d85e5-185">\<typparamref></span><span class="sxs-lookup"><span data-stu-id="d85e5-185">\<typeparamref></span></span>

<span data-ttu-id="d85e5-186">Tag `<typeparamref>` jest używany `<paramref>` tak jak tag, ale dla deklaracji typu ogólnego lub metody do opisania parametru ogólnego.</span><span class="sxs-lookup"><span data-stu-id="d85e5-186">You use `<typeparamref>` tag just like the `<paramref>` tag but for generic type or method declarations to describe a generic parameter.</span></span>
<span data-ttu-id="d85e5-187">Można użyć tej samej metody ogólnej, która została utworzona wcześniej.</span><span class="sxs-lookup"><span data-stu-id="d85e5-187">You can use the same generic method you previously created.</span></span>

[!code-csharp[Typeparamref Tag](~/samples/snippets/csharp/concepts/codedoc/typeparamref-tag.cs)]

## <a name="list"></a><span data-ttu-id="d85e5-188">\<> listy</span><span class="sxs-lookup"><span data-stu-id="d85e5-188">\<list></span></span>

<span data-ttu-id="d85e5-189">Tag służy `<list>` do formatowania informacji o dokumentacji jako uporządkowanej listy, nieuporządkowanej listy lub tabeli.</span><span class="sxs-lookup"><span data-stu-id="d85e5-189">You use the `<list>` tag to format documentation information as an ordered list, unordered list, or table.</span></span> <span data-ttu-id="d85e5-190">Zrób nieuporządkowaną listę wszystkich operacji `Math` matematycznych, które obsługuje biblioteka.</span><span class="sxs-lookup"><span data-stu-id="d85e5-190">Make an unordered list of every math operation your `Math` library supports.</span></span>

[!code-csharp[List Tag](~/samples/snippets/csharp/concepts/codedoc/list-tag.cs)]

<span data-ttu-id="d85e5-191">Można spoinować listę lub tabelę, zmieniając `type` atrybut odpowiednio na `number` lub `table`, .</span><span class="sxs-lookup"><span data-stu-id="d85e5-191">You can make an ordered list or table by changing the `type` attribute to `number` or `table`, respectively.</span></span>

## <a name="inheritdoc"></a><span data-ttu-id="d85e5-192">\<> dziedziczenia</span><span class="sxs-lookup"><span data-stu-id="d85e5-192">\<inheritdoc></span></span>

<span data-ttu-id="d85e5-193">Tag służy `<inheritdoc>` do dziedziczenia komentarzy XML z klas podstawowych, interfejsów i podobnych metod.</span><span class="sxs-lookup"><span data-stu-id="d85e5-193">You can use the `<inheritdoc>` tag to inherit XML comments from base classes, interfaces, and similar methods.</span></span> <span data-ttu-id="d85e5-194">Eliminuje to niepożądane kopiowanie i wklejanie zduplikowanych komentarzy XML i automatycznie synchronizuje komentarze XML.</span><span class="sxs-lookup"><span data-stu-id="d85e5-194">This eliminates unwanted copying and pasting of duplicate XML comments and automatically keeps XML comments synchronized.</span></span>

[!code-csharp-interactive[InheritDoc Tag](~/samples/snippets/csharp/concepts/codedoc/inheritdoc-tag.cs)]

### <a name="put-it-all-together"></a><span data-ttu-id="d85e5-195">Zebranie wszystkich elementów</span><span class="sxs-lookup"><span data-stu-id="d85e5-195">Put it all together</span></span>

<span data-ttu-id="d85e5-196">Jeśli w razie potrzeby zastosowano ten samouczek i zastosowano tagi do kodu, kod powinien teraz wyglądać podobnie do następującego:</span><span class="sxs-lookup"><span data-stu-id="d85e5-196">If you've followed this tutorial and applied the tags to your code where necessary, your code should now look similar to the following:</span></span>

[!code-csharp[Tagged Library](~/samples/snippets/csharp/concepts/codedoc/tagged-library.cs)]

<span data-ttu-id="d85e5-197">Z kodu można wygenerować szczegółową stronę internetową dokumentacji wraz z klikalnymi odsyłaczem.</span><span class="sxs-lookup"><span data-stu-id="d85e5-197">From your code, you can generate a detailed documentation website complete with clickable cross-references.</span></span> <span data-ttu-id="d85e5-198">Ale masz do czynienia z innym problemem: twój kod stał się trudny do odczytania.</span><span class="sxs-lookup"><span data-stu-id="d85e5-198">But you're faced with another problem: your code has become hard to read.</span></span>
<span data-ttu-id="d85e5-199">Jest tak wiele informacji, aby przesiać przez to, że to będzie koszmar dla każdego dewelopera, który chce przyczynić się do tego kodu.</span><span class="sxs-lookup"><span data-stu-id="d85e5-199">There's so much information to sift through that this is going to be a nightmare for any developer who wants to contribute to this code.</span></span>
<span data-ttu-id="d85e5-200">Na szczęście istnieje tag XML, który może pomóc ci poradzić sobie z tym:</span><span class="sxs-lookup"><span data-stu-id="d85e5-200">Thankfully there's an XML tag that can help you deal with this:</span></span>

## <a name="include"></a><span data-ttu-id="d85e5-201">\<obejmują></span><span class="sxs-lookup"><span data-stu-id="d85e5-201">\<include></span></span>

<span data-ttu-id="d85e5-202">Tag `<include>` umożliwia odwoływanie się do komentarzy w oddzielnym pliku XML, które opisują typy i elementy członkowskie w kodzie źródłowym, w przeciwieństwie do umieszczania komentarzy dokumentacji bezpośrednio w pliku kodu źródłowego.</span><span class="sxs-lookup"><span data-stu-id="d85e5-202">The `<include>` tag lets you refer to comments in a separate XML file that describe the types and members in your source code, as opposed to placing documentation comments directly in your source code file.</span></span>

<span data-ttu-id="d85e5-203">Teraz przeniesiesz wszystkie znaczniki XML do oddzielnego `docs.xml`pliku XML o nazwie .</span><span class="sxs-lookup"><span data-stu-id="d85e5-203">Now you're going to move all your XML tags into a separate XML file named `docs.xml`.</span></span> <span data-ttu-id="d85e5-204">Możesz nazwać plik, co chcesz.</span><span class="sxs-lookup"><span data-stu-id="d85e5-204">Feel free to name the file whatever you want.</span></span>

[!code-xml[Sample XML](~/samples/snippets/csharp/concepts/codedoc/include.xml)]

<span data-ttu-id="d85e5-205">W powyższym pliku XML komentarze dokumentacji każdego członka są wyświetlane bezpośrednio wewnątrz tagu o nazwie po tym, co robią.</span><span class="sxs-lookup"><span data-stu-id="d85e5-205">In the above XML, each member's documentation comments appear directly inside a tag named after what they do.</span></span> <span data-ttu-id="d85e5-206">Możesz wybrać własną strategię.</span><span class="sxs-lookup"><span data-stu-id="d85e5-206">You can choose your own strategy.</span></span>
<span data-ttu-id="d85e5-207">Teraz, gdy masz komentarze XML w osobnym pliku, zobaczmy, jak kod `<include>` może być bardziej czytelny za pomocą tagu:</span><span class="sxs-lookup"><span data-stu-id="d85e5-207">Now that you have your XML comments in a separate file, let's see how your code can be made more readable by using the `<include>` tag:</span></span>

[!code-csharp[Include Tag](~/samples/snippets/csharp/concepts/codedoc/include-tag.cs)]

<span data-ttu-id="d85e5-208">I masz to: nasz kod powraca do czytelni i żadne informacje o dokumentacji nie zostały utracone.</span><span class="sxs-lookup"><span data-stu-id="d85e5-208">And there you have it: our code is back to being readable, and no documentation information has been lost.</span></span>

<span data-ttu-id="d85e5-209">Atrybut `file` reprezentuje nazwę pliku XML zawierającego dokumentację.</span><span class="sxs-lookup"><span data-stu-id="d85e5-209">The `file` attribute represents the name of the XML file containing the documentation.</span></span>

<span data-ttu-id="d85e5-210">Atrybut `path` reprezentuje kwerendę [XPath](../standard/data/xml/xpath-queries-and-namespaces.md) `tag name` do teraźniejszości w `file`określonym .</span><span class="sxs-lookup"><span data-stu-id="d85e5-210">The `path` attribute represents an [XPath](../standard/data/xml/xpath-queries-and-namespaces.md) query to the `tag name` present in the specified `file`.</span></span>

<span data-ttu-id="d85e5-211">Atrybut `name` reprezentuje specyfikator nazw w tagu, który poprzedza komentarze.</span><span class="sxs-lookup"><span data-stu-id="d85e5-211">The `name` attribute represents the name specifier in the tag that precedes the comments.</span></span>

<span data-ttu-id="d85e5-212">Atrybut, `id` który może być używany `name`w miejsce , reprezentuje identyfikator tagu, który poprzedza komentarze.</span><span class="sxs-lookup"><span data-stu-id="d85e5-212">The `id` attribute, which can be used in place of `name`, represents the ID for the tag that precedes the comments.</span></span>

### <a name="user-defined-tags"></a><span data-ttu-id="d85e5-213">Tagi zdefiniowane przez użytkownika</span><span class="sxs-lookup"><span data-stu-id="d85e5-213">User-defined tags</span></span>

<span data-ttu-id="d85e5-214">Wszystkie znaczniki opisane powyżej reprezentują te, które są rozpoznawane przez kompilator C#.</span><span class="sxs-lookup"><span data-stu-id="d85e5-214">All the tags outlined above represent those that are recognized by the C# compiler.</span></span> <span data-ttu-id="d85e5-215">Jednak użytkownik może swobodnie definiować własne tagi.</span><span class="sxs-lookup"><span data-stu-id="d85e5-215">However, a user is free to define their own tags.</span></span>
<span data-ttu-id="d85e5-216">Narzędzia takie jak Sandcastle przynieść wsparcie dla dodatkowych tagów, takich jak [ \<>zdarzeń](https://ewsoftware.github.io/XMLCommentsGuide/html/81bf7ad3-45dc-452f-90d5-87ce2494a182.htm) i [ \<>pamiętać, ](https://ewsoftware.github.io/XMLCommentsGuide/html/4302a60f-e4f4-4b8d-a451-5f453c4ebd46.htm)a nawet wsparcie [dokumentowania przestrzeni nazw](https://ewsoftware.github.io/XMLCommentsGuide/html/BD91FAD4-188D-4697-A654-7C07FD47EF31.htm).</span><span class="sxs-lookup"><span data-stu-id="d85e5-216">Tools like Sandcastle bring support for extra tags like [\<event>](https://ewsoftware.github.io/XMLCommentsGuide/html/81bf7ad3-45dc-452f-90d5-87ce2494a182.htm) and [\<note>](https://ewsoftware.github.io/XMLCommentsGuide/html/4302a60f-e4f4-4b8d-a451-5f453c4ebd46.htm), and even support [documenting namespaces](https://ewsoftware.github.io/XMLCommentsGuide/html/BD91FAD4-188D-4697-A654-7C07FD47EF31.htm).</span></span>
<span data-ttu-id="d85e5-217">Niestandardowe lub w domu narzędzia do generowania dokumentacji mogą być również używane ze standardowymi tagami i wiele formatów wyjściowych od HTML do PDF mogą być obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="d85e5-217">Custom or in-house documentation generation tools can also be used with the standard tags and multiple output formats from HTML to PDF can be supported.</span></span>

## <a name="recommendations"></a><span data-ttu-id="d85e5-218">Zalecenia</span><span class="sxs-lookup"><span data-stu-id="d85e5-218">Recommendations</span></span>

<span data-ttu-id="d85e5-219">Dokumentowanie kodu jest zalecane z wielu powodów.</span><span class="sxs-lookup"><span data-stu-id="d85e5-219">Documenting code is recommended for many reasons.</span></span> <span data-ttu-id="d85e5-220">Oto niektóre najlepsze rozwiązania, scenariusze przypadków użycia ogólnego i rzeczy, które należy wiedzieć podczas używania tagów dokumentacji XML w kodzie Języka C#.</span><span class="sxs-lookup"><span data-stu-id="d85e5-220">What follows are some best practices, general use case scenarios, and things that you should know when using XML documentation tags in your C# code.</span></span>

- <span data-ttu-id="d85e5-221">W celu zachowania spójności należy udokumentować wszystkie publicznie widoczne typy i ich elementy członkowskie.</span><span class="sxs-lookup"><span data-stu-id="d85e5-221">For the sake of consistency, all publicly visible types and their members should be documented.</span></span> <span data-ttu-id="d85e5-222">Jeśli musisz to zrobić, zrób to wszystko.</span><span class="sxs-lookup"><span data-stu-id="d85e5-222">If you must do it, do it all.</span></span>
- <span data-ttu-id="d85e5-223">Członkowie prywatni mogą być również dokumentowane za pomocą komentarzy XML.</span><span class="sxs-lookup"><span data-stu-id="d85e5-223">Private members can also be documented using XML comments.</span></span> <span data-ttu-id="d85e5-224">Jednak to naraża wewnętrzne (potencjalnie poufne) funkcjonowanie biblioteki.</span><span class="sxs-lookup"><span data-stu-id="d85e5-224">However, this exposes the inner (potentially confidential) workings of your library.</span></span>
- <span data-ttu-id="d85e5-225">Co najmniej, typy i ich członkowie `<summary>` powinni mieć tag, ponieważ jego zawartość jest potrzebna dla IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="d85e5-225">At a bare minimum, types and their members should have a `<summary>` tag because its content is needed for IntelliSense.</span></span>
- <span data-ttu-id="d85e5-226">Tekst dokumentacji powinien być napisany przy użyciu pełnych zdań kończących się pełnymi zatrzymaniami.</span><span class="sxs-lookup"><span data-stu-id="d85e5-226">Documentation text should be written using complete sentences ending with full stops.</span></span>
- <span data-ttu-id="d85e5-227">Klasy częściowe są w pełni obsługiwane, a informacje o dokumentacji zostaną połączone w jeden wpis dla tego typu.</span><span class="sxs-lookup"><span data-stu-id="d85e5-227">Partial classes are fully supported, and documentation information will be concatenated into a single entry for that type.</span></span>
- <span data-ttu-id="d85e5-228">Kompilator weryfikuje `<exception>`składnię `<param>`, `<seealso>` `<include>`, `<typeparam>` , `<see>`, i tagów.</span><span class="sxs-lookup"><span data-stu-id="d85e5-228">The compiler verifies the syntax of the `<exception>`, `<include>`, `<param>`, `<see>`, `<seealso>`, and `<typeparam>` tags.</span></span>
- <span data-ttu-id="d85e5-229">Kompilator sprawdza poprawność parametrów, które zawierają ścieżki plików i odwołania do innych części kodu.</span><span class="sxs-lookup"><span data-stu-id="d85e5-229">The compiler validates the parameters that contain file paths and references to other parts of the code.</span></span>

## <a name="see-also"></a><span data-ttu-id="d85e5-230">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d85e5-230">See also</span></span>

- [<span data-ttu-id="d85e5-231">Komentarze dokumentacji XML (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="d85e5-231">XML Documentation Comments (C# Programming Guide)</span></span>](programming-guide/xmldoc/index.md)
- [<span data-ttu-id="d85e5-232">Znaczniki zalecane dla komentarzy do dokumentacji (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="d85e5-232">Recommended Tags for Documentation Comments (C# Programming Guide)</span></span>](programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)
