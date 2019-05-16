---
title: Dokumentowanie kodu przy użyciu komentarzy XML
description: Dowiedz się, jak dokumentowanie kodu za pomocą komentarzy dokumentacji XML do generowania pliku dokumentacji XML w czasie kompilacji.
ms.date: 02/14/2017
ms.assetid: 8e75e317-4a55-45f2-a866-e76124171838
ms.openlocfilehash: 17a6beabf7e8a917c461dae4d92f1cfbb0d9de71
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65633739"
---
# <a name="documenting-your-code-with-xml-comments"></a><span data-ttu-id="b1abe-103">Dokumentowanie kodu przy użyciu komentarzy XML</span><span class="sxs-lookup"><span data-stu-id="b1abe-103">Documenting your code with XML comments</span></span>

<span data-ttu-id="b1abe-104">Komentarze dokumentacji XML są specjalnym rodzajem komentarz, dodanych wcześniej definicji typu zdefiniowanego przez użytkownika lub elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="b1abe-104">XML documentation comments are a special kind of comment, added above the definition of any user-defined type or member.</span></span>
<span data-ttu-id="b1abe-105">Są one specjalne, ponieważ mogą być przetwarzane przez kompilator do generowania pliku dokumentacji XML w czasie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="b1abe-105">They are special because they can be processed by the compiler to generate an XML documentation file at compile time.</span></span>
<span data-ttu-id="b1abe-106">Plik XML wygenerowanego przez kompilator mogą być dystrybuowane wraz z Twojego zestawu platformy .NET tak, aby program Visual Studio i innych środowisk IDE umożliwia IntelliSense Wyświetlanie skróconych informacji dotyczących typów ani elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="b1abe-106">The compiler generated XML file can be distributed alongside your .NET assembly so that Visual Studio and other IDEs can use IntelliSense to show quick information about types or members.</span></span> <span data-ttu-id="b1abe-107">Ponadto plik XML mogą być uruchamiane za pomocą takich narzędzi [DocFX](https://dotnet.github.io/docfx/) i [Sandcastle](https://github.com/EWSoftware/SHFB) do generowania dokumentacja interfejsu API witryn sieci Web.</span><span class="sxs-lookup"><span data-stu-id="b1abe-107">Additionally, the XML file can be run through tools like [DocFX](https://dotnet.github.io/docfx/) and [Sandcastle](https://github.com/EWSoftware/SHFB) to generate API reference websites.</span></span>

<span data-ttu-id="b1abe-108">Komentarze dokumentacji XML, podobnie jak wszystkie inne komentarze są ignorowane przez kompilator.</span><span class="sxs-lookup"><span data-stu-id="b1abe-108">XML documentation comments, like all other comments, are ignored by the compiler.</span></span>

<span data-ttu-id="b1abe-109">Aby wygenerować plik XML w czasie kompilacji, wykonując jedną z następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="b1abe-109">You can generate the XML file at compile time by doing one of the following:</span></span>

- <span data-ttu-id="b1abe-110">Jeśli tworzysz aplikację za pomocą programu .NET Core z poziomu wiersza polecenia, możesz dodać [elementu DocumentationFile](/visualstudio/msbuild/common-msbuild-project-properties) do `<PropertyGroup>` sekcji w pliku projektu csproj.</span><span class="sxs-lookup"><span data-stu-id="b1abe-110">If you are developing an application with .NET Core from the command line, you can add a [DocumentationFile element](/visualstudio/msbuild/common-msbuild-project-properties) to the `<PropertyGroup>` section of your .csproj project file.</span></span> <span data-ttu-id="b1abe-111">Poniższy przykład generuje plik XML w katalogu projektu o takiej samej nazwie głównego pliku zestawu:</span><span class="sxs-lookup"><span data-stu-id="b1abe-111">The following example generates an XML file in the project directory with the same root filename as the assembly:</span></span>

   ```xml
   <DocumentationFile>bin\$(Configuration)\$(TargetFramework)\$(AssemblyName).xml</DocumentationFile>
   ```

   <span data-ttu-id="b1abe-112">Można również określić dokładną bezwzględną lub względną ścieżkę i nazwę pliku XML.</span><span class="sxs-lookup"><span data-stu-id="b1abe-112">You can also specify the exact absolute or relative path and name of the XML file.</span></span> <span data-ttu-id="b1abe-113">Poniższy przykład generuje plik XML, w tym samym katalogu co wersja do debugowania aplikacji:</span><span class="sxs-lookup"><span data-stu-id="b1abe-113">The following example generates the XML file in the same directory as the debug version of an application:</span></span>

   ```xml
   <DocumentationFile>bin\Debug\netcoreapp2.1\App.xml</DocumentationFile>
   ```

- <span data-ttu-id="b1abe-114">Jeśli tworzysz aplikację przy użyciu programu Visual Studio kliknij prawym przyciskiem myszy projekt i wybierz pozycję **właściwości**.</span><span class="sxs-lookup"><span data-stu-id="b1abe-114">If you are developing an application using Visual Studio, right-click on the project and select **Properties**.</span></span> <span data-ttu-id="b1abe-115">W oknie dialogowym właściwości wybierz **kompilacji** kartę i sprawdź **pliku dokumentacji XML**.</span><span class="sxs-lookup"><span data-stu-id="b1abe-115">In the properties dialog, select the **Build** tab, and check **XML documentation file**.</span></span> <span data-ttu-id="b1abe-116">Można również zmienić lokalizację, do której kompilator zapisuje plik.</span><span class="sxs-lookup"><span data-stu-id="b1abe-116">You can also change the location to which the compiler writes the file.</span></span>

- <span data-ttu-id="b1abe-117">Jeśli kompilujesz aplikację .NET Framework z poziomu wiersza polecenia Dodaj [/doc — opcja kompilatora](language-reference/compiler-options/doc-compiler-option.md) podczas kompilowania kodu.</span><span class="sxs-lookup"><span data-stu-id="b1abe-117">If you are compiling a .NET Framework application from the command line, add the [/doc compiler option](language-reference/compiler-options/doc-compiler-option.md) when compiling.</span></span>  

<span data-ttu-id="b1abe-118">Komentarze dokumentacji XML używać Potrójna ukośników (`///`) i XML sformatowane treść komentarza.</span><span class="sxs-lookup"><span data-stu-id="b1abe-118">XML documentation comments use triple forward slashes (`///`) and an XML formatted comment body.</span></span> <span data-ttu-id="b1abe-119">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="b1abe-119">For example:</span></span>

[!code-csharp[XML Documentation Comment](../../samples/snippets/csharp/concepts/codedoc/xml-comment.cs)]

## <a name="walkthrough"></a><span data-ttu-id="b1abe-120">Przewodnik</span><span class="sxs-lookup"><span data-stu-id="b1abe-120">Walkthrough</span></span>

<span data-ttu-id="b1abe-121">Przejdźmy teraz przez dokumentowanie biblioteki matematyczne wykraczającego poza podstawowe ułatwia zrozumienie współtworzyć także nowych deweloperów i deweloperzy innych firm mogą korzystać.</span><span class="sxs-lookup"><span data-stu-id="b1abe-121">Let's walk through documenting a very basic math library to make it easy for new developers to understand/contribute and for third party developers to use.</span></span>

<span data-ttu-id="b1abe-122">Oto kod biblioteki matematyczne proste:</span><span class="sxs-lookup"><span data-stu-id="b1abe-122">Here's code for the simple math library:</span></span>

[!code-csharp[Sample Library](../../samples/snippets/csharp/concepts/codedoc/sample-library.cs)]

<span data-ttu-id="b1abe-123">Biblioteka przykładowe obsługuje cztery główne operacje arytmetyczne `add`, `subtract`, `multiply` i `divide` na `int` i `double` typy danych.</span><span class="sxs-lookup"><span data-stu-id="b1abe-123">The sample library supports four major arithmetic operations `add`, `subtract`, `multiply` and `divide` on `int` and `double` data types.</span></span>

<span data-ttu-id="b1abe-124">Teraz chcesz mieć możliwość tworzenia dokument referencyjny dotyczący interfejsu API z poziomu kodu dla deweloperów innych firm, którzy użyj biblioteki, ale nie masz dostępu do kodu źródłowego.</span><span class="sxs-lookup"><span data-stu-id="b1abe-124">Now you want to be able to create an API reference document from your code for third party developers who use your library but don't have access to the source code.</span></span>
<span data-ttu-id="b1abe-125">Jak wspomniano wcześniej tagów dokumentacji XML można to osiągnąć.</span><span class="sxs-lookup"><span data-stu-id="b1abe-125">As mentioned earlier XML documentation tags can be used to achieve this.</span></span> <span data-ttu-id="b1abe-126">Możesz teraz zostaną wprowadzone do standardowych tagów XML C# kompilator obsługuje.</span><span class="sxs-lookup"><span data-stu-id="b1abe-126">You will now be introduced to the standard XML tags the C# compiler supports.</span></span>

## <a name="summary"></a><span data-ttu-id="b1abe-127">\<Summary ></span><span class="sxs-lookup"><span data-stu-id="b1abe-127">\<summary></span></span>

<span data-ttu-id="b1abe-128">`<summary>` Znacznik dodaje krótki informacji na temat typu lub elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="b1abe-128">The `<summary>` tag adds brief information about a type or member.</span></span>
<span data-ttu-id="b1abe-129">Zademonstruję jego użycie przez dodanie jej do `Math` klasy definicji i pierwszy `Add` metody.</span><span class="sxs-lookup"><span data-stu-id="b1abe-129">I'll demonstrate its use by adding it to the `Math` class definition and the first `Add` method.</span></span> <span data-ttu-id="b1abe-130">Możesz zastosować je do pozostałej części kodu.</span><span class="sxs-lookup"><span data-stu-id="b1abe-130">Feel free to apply it to the rest of your code.</span></span>

[!code-csharp[Summary Tag](../../samples/snippets/csharp/concepts/codedoc/summary-tag.cs)]

<span data-ttu-id="b1abe-131">`<summary>` Tag jest bardzo ważna, a firma Microsoft zaleca, aby uwzględniać go, ponieważ jego zawartość jest podstawowym źródłem informacji typu lub elementu członkowskiego w technologii IntelliSense lub dokument referencyjny dotyczący interfejsu API.</span><span class="sxs-lookup"><span data-stu-id="b1abe-131">The `<summary>` tag is very important, and we recommend that you include it because its content is the primary source of type or member information in IntelliSense or an API reference document.</span></span>

## <a name="remarks"></a><span data-ttu-id="b1abe-132">\<Remarks ></span><span class="sxs-lookup"><span data-stu-id="b1abe-132">\<remarks></span></span>

<span data-ttu-id="b1abe-133">`<remarks>` Tag uzupełnia informacje dotyczące typów ani elementów członkowskich, `<summary>` zawiera tag.</span><span class="sxs-lookup"><span data-stu-id="b1abe-133">The `<remarks>` tag supplements the information about types or members that the `<summary>` tag provides.</span></span> <span data-ttu-id="b1abe-134">W tym przykładzie będzie po prostu dodaj go do klasy.</span><span class="sxs-lookup"><span data-stu-id="b1abe-134">In this example, you'll just add it to the class.</span></span>

[!code-csharp[Remarks Tag](../../samples/snippets/csharp/concepts/codedoc/remarks-tag.cs)]

## <a name="returns"></a><span data-ttu-id="b1abe-135">\<returns></span><span class="sxs-lookup"><span data-stu-id="b1abe-135">\<returns></span></span>

<span data-ttu-id="b1abe-136">`<returns>` Tagu w tym artykule opisano wartość zwracaną deklaracji metody.</span><span class="sxs-lookup"><span data-stu-id="b1abe-136">The `<returns>` tag describes the return value of a method declaration.</span></span>
<span data-ttu-id="b1abe-137">Jak poprzednio, w poniższym przykładzie pokazano `<returns>` tag pierwszego `Add` metody.</span><span class="sxs-lookup"><span data-stu-id="b1abe-137">As before, the following example illustrates the `<returns>` tag on the first `Add` method.</span></span> <span data-ttu-id="b1abe-138">Możesz tworzyć takie same, o innych metodach.</span><span class="sxs-lookup"><span data-stu-id="b1abe-138">You can do the same on other methods.</span></span>

[!code-csharp[Returns Tag](../../samples/snippets/csharp/concepts/codedoc/returns-tag.cs)]

## <a name="value"></a><span data-ttu-id="b1abe-139">\<value></span><span class="sxs-lookup"><span data-stu-id="b1abe-139">\<value></span></span>

<span data-ttu-id="b1abe-140">`<value>` Tag jest podobne do `<returns>` tagów, z tą różnicą, że zostanie on użyty do właściwości.</span><span class="sxs-lookup"><span data-stu-id="b1abe-140">The `<value>` tag is similar to the `<returns>` tag, except that you use it for properties.</span></span>
<span data-ttu-id="b1abe-141">Zakładając, że Twoje `Math` biblioteki miały statyczny właściwość o nazwie `PI`, poniżej przedstawiono, jak skorzystać z tego tagu:</span><span class="sxs-lookup"><span data-stu-id="b1abe-141">Assuming your `Math` library had a static property called `PI`, here's how you'd use this tag:</span></span>

[!code-csharp[Value Tag](../../samples/snippets/csharp/concepts/codedoc/value-tag.cs)]

## <a name="example"></a><span data-ttu-id="b1abe-142">\<przykład ></span><span class="sxs-lookup"><span data-stu-id="b1abe-142">\<example></span></span>

<span data-ttu-id="b1abe-143">Możesz użyć `<example>` tag, aby uwzględnić przykładem w dokumentacji XML.</span><span class="sxs-lookup"><span data-stu-id="b1abe-143">You use the `<example>` tag to include an example in your XML documentation.</span></span>
<span data-ttu-id="b1abe-144">Wiąże się to przy użyciu elementu podrzędnego `<code>` tagu.</span><span class="sxs-lookup"><span data-stu-id="b1abe-144">This involves using the child `<code>` tag.</span></span>

[!code-csharp[Example Tag](../../samples/snippets/csharp/concepts/codedoc/example-tag.cs)]

<span data-ttu-id="b1abe-145">`code` Tag zachowuje podziały wierszy i wcięć przykłady dłużej.</span><span class="sxs-lookup"><span data-stu-id="b1abe-145">The `code` tag preserves line breaks and indentation for longer examples.</span></span>

## <a name="para"></a><span data-ttu-id="b1abe-146">\<para></span><span class="sxs-lookup"><span data-stu-id="b1abe-146">\<para></span></span>

<span data-ttu-id="b1abe-147">Możesz użyć `<para>` tag, aby formatować takiej treści, w ramach jego tagu nadrzędnym.</span><span class="sxs-lookup"><span data-stu-id="b1abe-147">You use the `<para>` tag to format the content within its parent tag.</span></span> <span data-ttu-id="b1abe-148">`<para>` jest zazwyczaj używany wewnątrz znacznik, taki jak `<remarks>` lub `<returns>`, aby podzielić tekstu akapitów.</span><span class="sxs-lookup"><span data-stu-id="b1abe-148">`<para>` is usually used inside a tag, such as `<remarks>` or `<returns>`, to divide text into paragraphs.</span></span>
<span data-ttu-id="b1abe-149">Zawartość można formatować `<remarks>` tag dla swojej definicji klasy.</span><span class="sxs-lookup"><span data-stu-id="b1abe-149">You can format the contents of the `<remarks>` tag for your class definition.</span></span>

[!code-csharp[Para Tag](../../samples/snippets/csharp/concepts/codedoc/para-tag.cs)]

## <a name="c"></a><span data-ttu-id="b1abe-150">\<c></span><span class="sxs-lookup"><span data-stu-id="b1abe-150">\<c></span></span>

<span data-ttu-id="b1abe-151">Pracując nadal na temat formatowania, użyj `<c>` tag do oznaczania część tekstu jako kod.</span><span class="sxs-lookup"><span data-stu-id="b1abe-151">Still on the topic of formatting, you use the `<c>` tag for marking part of text as code.</span></span>
<span data-ttu-id="b1abe-152">Jest on podobny do `<code>` tagu, ale wbudowanego.</span><span class="sxs-lookup"><span data-stu-id="b1abe-152">It's like the `<code>` tag but inline.</span></span> <span data-ttu-id="b1abe-153">Może to być przydatne, gdy chcesz wyświetlić przykład szybki kod jako część zawartości tagu.</span><span class="sxs-lookup"><span data-stu-id="b1abe-153">It's useful when you want to show a quick code example as part of a tag's content.</span></span>
<span data-ttu-id="b1abe-154">Zaktualizujmy w dokumentacji dotyczącej `Math` klasy.</span><span class="sxs-lookup"><span data-stu-id="b1abe-154">Let's update the documentation for the `Math` class.</span></span>

[!code-csharp[C Tag](../../samples/snippets/csharp/concepts/codedoc/c-tag.cs)]

## <a name="exception"></a><span data-ttu-id="b1abe-155">\<wyjątku ></span><span class="sxs-lookup"><span data-stu-id="b1abe-155">\<exception></span></span>

<span data-ttu-id="b1abe-156">Za pomocą `<exception>` tagu, umożliwiają deweloperom wiedzieć, czy metoda może zgłosić określonych wyjątków.</span><span class="sxs-lookup"><span data-stu-id="b1abe-156">By using the `<exception>` tag, you let your developers know that a method can throw specific exceptions.</span></span>
<span data-ttu-id="b1abe-157">Spojrzenie na Twoje `Math` biblioteki, możesz zobaczyć, że oba `Add` metody zgłosić wyjątek, jeśli określony warunek jest spełniony.</span><span class="sxs-lookup"><span data-stu-id="b1abe-157">Looking at your `Math` library, you can see that both `Add` methods throw an exception if a certain condition is met.</span></span> <span data-ttu-id="b1abe-158">Nie jest tak oczywiste, że całkowitą `Divide` metoda generuje również Jeśli `b` parametr ma wartość zero.</span><span class="sxs-lookup"><span data-stu-id="b1abe-158">Not so obvious, though, is that integer `Divide` method throws as well if the `b` parameter is zero.</span></span> <span data-ttu-id="b1abe-159">Teraz należy dodać wyjątek dokumentacji do tej metody.</span><span class="sxs-lookup"><span data-stu-id="b1abe-159">Now add exception documentation to this method.</span></span>

[!code-csharp[Exception Tag](../../samples/snippets/csharp/concepts/codedoc/exception-tag.cs)]

<span data-ttu-id="b1abe-160">`cref` Atrybutu reprezentuje odwołanie do wyjątek, który jest dostępny w bieżącym środowisku kompilacji.</span><span class="sxs-lookup"><span data-stu-id="b1abe-160">The `cref` attribute represents a reference to an exception that is available from the current compilation environment.</span></span>
<span data-ttu-id="b1abe-161">Może to być dowolny typ zdefiniowany w projekcie lub przywoływanego zestawu.</span><span class="sxs-lookup"><span data-stu-id="b1abe-161">This can be any type defined in the project or a referenced assembly.</span></span> <span data-ttu-id="b1abe-162">Kompilator zgłosi ostrzeżenie, jeśli jego wartość nie jest możliwe.</span><span class="sxs-lookup"><span data-stu-id="b1abe-162">The compiler will issue a warning if its value cannot be resolved.</span></span>

## <a name="see"></a><span data-ttu-id="b1abe-163">\<see></span><span class="sxs-lookup"><span data-stu-id="b1abe-163">\<see></span></span>

<span data-ttu-id="b1abe-164">`<see>` Tagu umożliwia tworzenie łączem do strony dokumentacji dla innego elementu kodu.</span><span class="sxs-lookup"><span data-stu-id="b1abe-164">The `<see>` tag lets you create a clickable link to a documentation page for another code element.</span></span> <span data-ttu-id="b1abe-165">W naszym następnym przykładzie utworzymy łączem między tymi dwoma `Add` metody.</span><span class="sxs-lookup"><span data-stu-id="b1abe-165">In our next example, we'll create a clickable link between the two `Add` methods.</span></span>

[!code-csharp[See Tag](../../samples/snippets/csharp/concepts/codedoc/see-tag.cs)]

<span data-ttu-id="b1abe-166">`cref` Jest **wymagane** atrybut, który reprezentuje odwołanie do typu lub jego elementu członkowskiego, który jest dostępny w bieżącym środowisku kompilacji.</span><span class="sxs-lookup"><span data-stu-id="b1abe-166">The `cref` is a **required** attribute that represents a reference to a type or its member that is available from the current compilation environment.</span></span>
<span data-ttu-id="b1abe-167">Może to być dowolny typ zdefiniowany w projekcie lub przywoływanego zestawu.</span><span class="sxs-lookup"><span data-stu-id="b1abe-167">This can be any type defined in the project or a referenced assembly.</span></span>

## <a name="seealso"></a><span data-ttu-id="b1abe-168">\<seealso></span><span class="sxs-lookup"><span data-stu-id="b1abe-168">\<seealso></span></span>

<span data-ttu-id="b1abe-169">Możesz użyć `<seealso>` tagu w taki sam sposób jak `<see>` tagu.</span><span class="sxs-lookup"><span data-stu-id="b1abe-169">You use the `<seealso>` tag in the same way you do the `<see>` tag.</span></span> <span data-ttu-id="b1abe-170">Jedyna różnica polega na tym, że jego zawartość zwykle znajduje się w sekcji "Zobacz też".</span><span class="sxs-lookup"><span data-stu-id="b1abe-170">The only difference is that its content is typically placed in a "See Also" section.</span></span> <span data-ttu-id="b1abe-171">W tym miejscu dodamy `seealso` tagiem na liczbę całkowitą `Add` metodę, aby odwoływać się do innych metod w klasie, które akceptują parametry liczby całkowitej:</span><span class="sxs-lookup"><span data-stu-id="b1abe-171">Here we'll add a `seealso` tag on the integer `Add` method to reference other methods in the class that accept integer parameters:</span></span>

[!code-csharp[Seealso Tag](../../samples/snippets/csharp/concepts/codedoc/seealso-tag.cs)]

<span data-ttu-id="b1abe-172">`cref` Atrybutu reprezentuje odwołanie do typu lub jego elementu członkowskiego, który jest dostępny w bieżącym środowisku kompilacji.</span><span class="sxs-lookup"><span data-stu-id="b1abe-172">The `cref` attribute represents a reference to a type or its member that is available from the current compilation environment.</span></span>
<span data-ttu-id="b1abe-173">Może to być dowolny typ zdefiniowany w projekcie lub przywoływanego zestawu.</span><span class="sxs-lookup"><span data-stu-id="b1abe-173">This can be any type defined in the project or a referenced assembly.</span></span>

## <a name="param"></a><span data-ttu-id="b1abe-174">\<param></span><span class="sxs-lookup"><span data-stu-id="b1abe-174">\<param></span></span>

<span data-ttu-id="b1abe-175">Możesz użyć `<param>` tag do opisania parametrów metody.</span><span class="sxs-lookup"><span data-stu-id="b1abe-175">You use the `<param>` tag to describe a method's parameters.</span></span> <span data-ttu-id="b1abe-176">Poniżej przedstawiono przykład podwójnego `Add` metody: Opisuje tagu określono parametr w **wymagane** `name` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="b1abe-176">Here's an example on the double `Add` method: The parameter the tag describes is specified in the **required** `name` attribute.</span></span>

[!code-csharp[Param Tag](../../samples/snippets/csharp/concepts/codedoc/param-tag.cs)]

## <a name="typeparam"></a><span data-ttu-id="b1abe-177">\<typeparam></span><span class="sxs-lookup"><span data-stu-id="b1abe-177">\<typeparam></span></span>

<span data-ttu-id="b1abe-178">Możesz użyć `<typeparam>` tag, podobnie jak `<param>` tagu, ale dla ogólnego deklaracji typu lub metody do opisania parametr ogólny.</span><span class="sxs-lookup"><span data-stu-id="b1abe-178">You use `<typeparam>` tag just like the `<param>` tag but for generic type or method declarations to describe a generic parameter.</span></span>
<span data-ttu-id="b1abe-179">Szybkie metodę rodzajową, aby dodać swoje `Math` klasy, aby sprawdzić, czy jeden ilość jest większy niż inny.</span><span class="sxs-lookup"><span data-stu-id="b1abe-179">Add a quick generic method to your `Math` class to check if one quantity is greater than another.</span></span>

[!code-csharp[Typeparam Tag](../../samples/snippets/csharp/concepts/codedoc/typeparam-tag.cs)]

## <a name="paramref"></a><span data-ttu-id="b1abe-180">\<paramref></span><span class="sxs-lookup"><span data-stu-id="b1abe-180">\<paramref></span></span>

<span data-ttu-id="b1abe-181">Czasami może być w trakcie opisujące metoda wykonuje w jakie mogą być `<summary>` tagu, na które może chcieć odwołać się do parametru.</span><span class="sxs-lookup"><span data-stu-id="b1abe-181">Sometimes you might be in the middle of describing what a method does in what could be a `<summary>` tag, and you might want to make a reference to a parameter.</span></span> <span data-ttu-id="b1abe-182">`<paramref>` Tag jest doskonale sprawdza się właśnie to.</span><span class="sxs-lookup"><span data-stu-id="b1abe-182">The `<paramref>` tag is great for just this.</span></span> <span data-ttu-id="b1abe-183">Spróbujmy na podstawie aktualizacji podsumowania naszych double `Add` metody.</span><span class="sxs-lookup"><span data-stu-id="b1abe-183">Let's update the summary of our double based `Add` method.</span></span> <span data-ttu-id="b1abe-184">Podobnie jak `<param>` Nazwa parametru jest określona w tagu **wymagane** `name` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="b1abe-184">Like the `<param>` tag the parameter name is specified in the **required** `name` attribute.</span></span>

[!code-csharp[Paramref Tag](../../samples/snippets/csharp/concepts/codedoc/paramref-tag.cs)]

## <a name="typeparamref"></a><span data-ttu-id="b1abe-185">\<typeparamref></span><span class="sxs-lookup"><span data-stu-id="b1abe-185">\<typeparamref></span></span>

<span data-ttu-id="b1abe-186">Możesz użyć `<typeparamref>` tag, podobnie jak `<paramref>` tagu, ale dla ogólnego deklaracji typu lub metody do opisania parametr ogólny.</span><span class="sxs-lookup"><span data-stu-id="b1abe-186">You use `<typeparamref>` tag just like the `<paramref>` tag but for generic type or method declarations to describe a generic parameter.</span></span>
<span data-ttu-id="b1abe-187">Można użyć tej samej metody rodzajowej, utworzone wcześniej.</span><span class="sxs-lookup"><span data-stu-id="b1abe-187">You can use the same generic method you previously created.</span></span>

[!code-csharp[Typeparamref Tag](../../samples/snippets/csharp/concepts/codedoc/typeparamref-tag.cs)]

## <a name="list"></a><span data-ttu-id="b1abe-188">\<list></span><span class="sxs-lookup"><span data-stu-id="b1abe-188">\<list></span></span>

<span data-ttu-id="b1abe-189">Możesz użyć `<list>` tag o dokumentacji formatu listy uporządkowanej, listę nieuporządkowaną lub tabeli.</span><span class="sxs-lookup"><span data-stu-id="b1abe-189">You use the `<list>` tag to format documentation information as an ordered list, unordered list or table.</span></span>
<span data-ttu-id="b1abe-190">Wprowadź nieuporządkowaną listę każdej operacji matematycznych swoje `Math` biblioteka obsługuje.</span><span class="sxs-lookup"><span data-stu-id="b1abe-190">Make an unordered list of every math operation your `Math` library supports.</span></span>

[!code-csharp[List Tag](../../samples/snippets/csharp/concepts/codedoc/list-tag.cs)]

<span data-ttu-id="b1abe-191">Można wprowadzić uporządkowanej liście lub tabeli, zmieniając `type` atrybutu `number` lub `table`, odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="b1abe-191">You can make an ordered list or table by changing the `type` attribute to `number` or `table`, respectively.</span></span>

### <a name="putting-it-all-together"></a><span data-ttu-id="b1abe-192">Łączenie wszystkiego razem</span><span class="sxs-lookup"><span data-stu-id="b1abe-192">Putting it all together</span></span>

<span data-ttu-id="b1abe-193">Jeśli już a następnie w tym samouczku i zastosowano tagów w kodzie, gdy jest to konieczne, kodu powinien teraz wyglądać podobnie do poniższej:</span><span class="sxs-lookup"><span data-stu-id="b1abe-193">If you've followed this tutorial and applied the tags to your code where necessary, your code should now look similar to the following:</span></span>

[!code-csharp[Tagged Library](../../samples/snippets/csharp/concepts/codedoc/tagged-library.cs)]

<span data-ttu-id="b1abe-194">W kodzie można wygenerować szczegółową dokumentację witryny sieci Web z odsyłacze możesz klikać.</span><span class="sxs-lookup"><span data-stu-id="b1abe-194">From your code, you can generate a detailed documentation website complete with clickable cross-references.</span></span> <span data-ttu-id="b1abe-195">Ale one zmierzyła się z innym problemem: kod stał się trudny do odczytania.</span><span class="sxs-lookup"><span data-stu-id="b1abe-195">But you're faced with another problem: your code has become hard to read.</span></span>
<span data-ttu-id="b1abe-196">Istnieje wiele informacji do przesiania, że będzie to być okropnej dla każdego dewelopera, który chce przyczyniają się do tego kodu.</span><span class="sxs-lookup"><span data-stu-id="b1abe-196">There's so much information to sift through that this is going to be a nightmare for any developer who wants to contribute to this code.</span></span>
<span data-ttu-id="b1abe-197">Szczęście jest tag XML, które mogą ułatwić pracę z tym:</span><span class="sxs-lookup"><span data-stu-id="b1abe-197">Thankfully there's an XML tag that can help you deal with this:</span></span>

## <a name="include"></a><span data-ttu-id="b1abe-198">\<include></span><span class="sxs-lookup"><span data-stu-id="b1abe-198">\<include></span></span>

<span data-ttu-id="b1abe-199">`<include>` Znacznik umożliwia Zobacz komentarze w osobnym pliku XML, które opisują typy i elementy członkowskie w kodzie źródłowym, w przeciwieństwie do wprowadzania komentarzy dokumentacji bezpośrednio w pliku kodu źródłowego.</span><span class="sxs-lookup"><span data-stu-id="b1abe-199">The `<include>` tag lets you refer to comments in a separate XML file that describe the types and members in your source code, as opposed to placing documentation comments directly in your source code file.</span></span>

<span data-ttu-id="b1abe-200">Teraz możesz zacząć przenieść wszystkie tagi XML w osobnym pliku XML o nazwie `docs.xml`.</span><span class="sxs-lookup"><span data-stu-id="b1abe-200">Now you're going to move all your XML tags into a separate XML file named `docs.xml`.</span></span> <span data-ttu-id="b1abe-201">Swobodnie nazwę pliku, co tylko chcesz.</span><span class="sxs-lookup"><span data-stu-id="b1abe-201">Feel free to name the file whatever you want.</span></span>

[!code-xml[Sample XML](../../samples/snippets/csharp/concepts/codedoc/include.xml)]

<span data-ttu-id="b1abe-202">W powyższym kodzie XML komentarze dokumentacji każdego elementu członkowskiego są wyświetlane bezpośrednio wewnątrz tagu o nazwie po ich działania.</span><span class="sxs-lookup"><span data-stu-id="b1abe-202">In the above XML, each member's documentation comments appear directly inside a tag named after what they do.</span></span> <span data-ttu-id="b1abe-203">Możesz wybrać własne strategii.</span><span class="sxs-lookup"><span data-stu-id="b1abe-203">You can choose your own strategy.</span></span>
<span data-ttu-id="b1abe-204">Teraz, gdy komentarz XML w oddzielnym pliku, zobaczmy, jak Twój kod może się bardziej czytelny przy użyciu `<include>` tag:</span><span class="sxs-lookup"><span data-stu-id="b1abe-204">Now that you have your XML comments in a separate file, let's see how your code can be made more readable by using the `<include>` tag:</span></span>

[!code-csharp[Include Tag](../../samples/snippets/csharp/concepts/codedoc/include-tag.cs)]

<span data-ttu-id="b1abe-205">I są dostępne: naszego kodu jest do odczytu i utracono żadnych informacji o dokumentacji.</span><span class="sxs-lookup"><span data-stu-id="b1abe-205">And there you have it: our code is back to being readable, and no documentation information has been lost.</span></span>

<span data-ttu-id="b1abe-206">`file` Atrybut reprezentuje nazwę pliku XML zawierającego dokumentację.</span><span class="sxs-lookup"><span data-stu-id="b1abe-206">The `file` attribute represents the name of the XML file containing the documentation.</span></span>

<span data-ttu-id="b1abe-207">`path` Atrybutu reprezentuje [XPath](../standard/data/xml/xpath-queries-and-namespaces.md) zapytania `tag name` obecne w określonym `file`.</span><span class="sxs-lookup"><span data-stu-id="b1abe-207">The `path` attribute represents an [XPath](../standard/data/xml/xpath-queries-and-namespaces.md) query to the `tag name` present in the specified `file`.</span></span>

<span data-ttu-id="b1abe-208">`name` Atrybut reprezentuje określenie nazwy w tagu, który poprzedza komentarze.</span><span class="sxs-lookup"><span data-stu-id="b1abe-208">The `name` attribute represents the name specifier in the tag that precedes the comments.</span></span>

<span data-ttu-id="b1abe-209">`id` Atrybut, który może być używany zamiast `name` reprezentuje identyfikator tagu, który poprzedza komentarze.</span><span class="sxs-lookup"><span data-stu-id="b1abe-209">The `id` attribute which can be used in place of `name` represents the ID for the tag that precedes the comments.</span></span>

### <a name="user-defined-tags"></a><span data-ttu-id="b1abe-210">Tagi zdefiniowane przez użytkownika</span><span class="sxs-lookup"><span data-stu-id="b1abe-210">User Defined Tags</span></span>

<span data-ttu-id="b1abe-211">Wszystkie tagi opisanych powyżej reprezentują te, które są rozpoznawane przez kompilator języka C#.</span><span class="sxs-lookup"><span data-stu-id="b1abe-211">All the tags outlined above represent those that are recognized by the C# compiler.</span></span> <span data-ttu-id="b1abe-212">Jednak użytkownik będzie mógł zdefiniować własne tagi.</span><span class="sxs-lookup"><span data-stu-id="b1abe-212">However, a user is free to define their own tags.</span></span>
<span data-ttu-id="b1abe-213">Narzędzia, takie jak rozwiązania Sandcastle przenieść pomocy technicznej dla dodatkowego tagów, takich jak [ `<event>` ](https://ewsoftware.github.io/XMLCommentsGuide/html/81bf7ad3-45dc-452f-90d5-87ce2494a182.htm), [ `<note>` ](https://ewsoftware.github.io/XMLCommentsGuide/html/4302a60f-e4f4-4b8d-a451-5f453c4ebd46.htm) nawet pomocy technicznej i [dokumentowanie przestrzenie nazw](https://ewsoftware.github.io/XMLCommentsGuide/html/BD91FAD4-188D-4697-A654-7C07FD47EF31.htm).</span><span class="sxs-lookup"><span data-stu-id="b1abe-213">Tools like Sandcastle bring support for extra tags like [`<event>`](https://ewsoftware.github.io/XMLCommentsGuide/html/81bf7ad3-45dc-452f-90d5-87ce2494a182.htm), [`<note>`](https://ewsoftware.github.io/XMLCommentsGuide/html/4302a60f-e4f4-4b8d-a451-5f453c4ebd46.htm) and even support [documenting namespaces](https://ewsoftware.github.io/XMLCommentsGuide/html/BD91FAD4-188D-4697-A654-7C07FD47EF31.htm).</span></span>
<span data-ttu-id="b1abe-214">Niestandardowy lub narzędzia do generowania dokumentacji wewnętrznych można również za pomocą standardowych tagów i może być obsługiwanych wiele formatów danych wyjściowych z kodu HTML na format PDF.</span><span class="sxs-lookup"><span data-stu-id="b1abe-214">Custom or in-house documentation generation tools can also be used with the standard tags and multiple output formats from HTML to PDF can be supported.</span></span>

## <a name="recommendations"></a><span data-ttu-id="b1abe-215">Zalecenia</span><span class="sxs-lookup"><span data-stu-id="b1abe-215">Recommendations</span></span>

<span data-ttu-id="b1abe-216">Dokumentowanie kodu jest zalecane w przypadku wielu powodów.</span><span class="sxs-lookup"><span data-stu-id="b1abe-216">Documenting code is recommended for many reasons.</span></span> <span data-ttu-id="b1abe-217">Poniżej przedstawiono kilka najlepszych zasad, ogólnych scenariuszy przypadków użycia, rzeczy, które przydatnych podczas korzystając z dokumentacji XML tagów w kodzie języka C#.</span><span class="sxs-lookup"><span data-stu-id="b1abe-217">What follows are some best practices, general use case scenarios, and things that you should know when using XML documentation tags in your C# code.</span></span>

* <span data-ttu-id="b1abe-218">Dla spójności wszystkie publicznie widoczne typy i składowe powinny być udokumentowane.</span><span class="sxs-lookup"><span data-stu-id="b1abe-218">For the sake of consistency, all publicly visible types and their members should be documented.</span></span> <span data-ttu-id="b1abe-219">Jeśli musisz to zrobić, wykonaj to wszystko.</span><span class="sxs-lookup"><span data-stu-id="b1abe-219">If you must do it, do it all.</span></span>
* <span data-ttu-id="b1abe-220">Prywatne elementy członkowskie można również opisane, przy użyciu komentarzy XML.</span><span class="sxs-lookup"><span data-stu-id="b1abe-220">Private members can also be documented using XML comments.</span></span> <span data-ttu-id="b1abe-221">Jednak to uwidacznia przebiega (potencjalnie poufnych) biblioteki.</span><span class="sxs-lookup"><span data-stu-id="b1abe-221">However, this exposes the inner (potentially confidential) workings of your library.</span></span>
* <span data-ttu-id="b1abe-222">W ramach absolutnego minimum, typy i składowe powinny mieć `<summary>` tag, ponieważ jego zawartość jest wymagane dla funkcji IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="b1abe-222">At a bare minimum, types and their members should have a `<summary>` tag because its content is needed for IntelliSense.</span></span>
* <span data-ttu-id="b1abe-223">Tekst dokumentacji zapisywane są postaci kompletnych zdań, kończąc na stopnie.</span><span class="sxs-lookup"><span data-stu-id="b1abe-223">Documentation text should be written using complete sentences ending with full stops.</span></span>
* <span data-ttu-id="b1abe-224">Klasy częściowe są w pełni obsługiwane, a informacje o dokumentacji, będą połączone w pojedynczy wpis dla danego typu.</span><span class="sxs-lookup"><span data-stu-id="b1abe-224">Partial classes are fully supported, and documentation information will be concatenated into a single entry for that type.</span></span>
* <span data-ttu-id="b1abe-225">Kompilator sprawdza składnię `<exception>`, `<include>`, `<param>`, `<see>`, `<seealso>` i `<typeparam>` tagów.</span><span class="sxs-lookup"><span data-stu-id="b1abe-225">The compiler verifies the syntax of the `<exception>`, `<include>`, `<param>`, `<see>`, `<seealso>` and `<typeparam>` tags.</span></span>
- <span data-ttu-id="b1abe-226">Kompilator sprawdza poprawność parametrów, które zawierają ścieżki do plików i odwołań pozwalającą na inne części kodu.</span><span class="sxs-lookup"><span data-stu-id="b1abe-226">The compiler validates the parameters that contain file paths and references to other parts of the code.</span></span>

## <a name="see-also"></a><span data-ttu-id="b1abe-227">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b1abe-227">See also</span></span>

- [<span data-ttu-id="b1abe-228">Komentarze dokumentacji XML (C# Programming Guide)</span><span class="sxs-lookup"><span data-stu-id="b1abe-228">XML Documentation Comments (C# Programming Guide)</span></span>](programming-guide/xmldoc/index.md)
- [<span data-ttu-id="b1abe-229">Tagi zalecane dla komentarzy do dokumentacji (C# Programming Guide)</span><span class="sxs-lookup"><span data-stu-id="b1abe-229">Recommended Tags for Documentation Comments (C# Programming Guide)</span></span>](programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)
