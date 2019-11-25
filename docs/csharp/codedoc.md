---
title: Dokumentowanie kodu za pomocą komentarzy XML
description: Dowiedz się, jak udokumentować kod za pomocą komentarzy dokumentacji XML i generować plik dokumentacji XML w czasie kompilacji.
ms.date: 02/14/2017
ms.technology: csharp-fundamentals
ms.assetid: 8e75e317-4a55-45f2-a866-e76124171838
ms.openlocfilehash: c858a92309710a0ac6b68e9194f2d7ef4c9577a0
ms.sourcegitcommit: fbb8a593a511ce667992502a3ce6d8f65c594edf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2019
ms.locfileid: "74140665"
---
# <a name="documenting-your-code-with-xml-comments"></a><span data-ttu-id="bfbea-103">Dokumentowanie kodu za pomocą komentarzy XML</span><span class="sxs-lookup"><span data-stu-id="bfbea-103">Documenting your code with XML comments</span></span>

<span data-ttu-id="bfbea-104">Komentarze dokumentacji XML są specjalnym rodzajem komentarza, który został dodany powyżej definicji dowolnego typu lub elementu członkowskiego zdefiniowanego przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="bfbea-104">XML documentation comments are a special kind of comment, added above the definition of any user-defined type or member.</span></span>
<span data-ttu-id="bfbea-105">Są one specyficzne, ponieważ mogą być przetwarzane przez kompilator w celu wygenerowania pliku dokumentacji XML w czasie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="bfbea-105">They are special because they can be processed by the compiler to generate an XML documentation file at compile time.</span></span>
<span data-ttu-id="bfbea-106">Plik XML wygenerowany przez kompilator może być dystrybuowany wraz z zestawem .NET, dzięki czemu program Visual Studio i inne środowisk IDE mogą używać funkcji IntelliSense do wyświetlania szybkich informacji o typach lub elementach członkowskich.</span><span class="sxs-lookup"><span data-stu-id="bfbea-106">The compiler generated XML file can be distributed alongside your .NET assembly so that Visual Studio and other IDEs can use IntelliSense to show quick information about types or members.</span></span> <span data-ttu-id="bfbea-107">Ponadto plik XML można uruchomić za pomocą narzędzi, takich jak [DocFX](https://dotnet.github.io/docfx/) i [Sandcastle](https://github.com/EWSoftware/SHFB) , aby generować witryny sieci Web dokumentacji interfejsu API.</span><span class="sxs-lookup"><span data-stu-id="bfbea-107">Additionally, the XML file can be run through tools like [DocFX](https://dotnet.github.io/docfx/) and [Sandcastle](https://github.com/EWSoftware/SHFB) to generate API reference websites.</span></span>

<span data-ttu-id="bfbea-108">Komentarze dokumentacji XML, podobnie jak wszystkie inne komentarze, są ignorowane przez kompilator.</span><span class="sxs-lookup"><span data-stu-id="bfbea-108">XML documentation comments, like all other comments, are ignored by the compiler.</span></span>

<span data-ttu-id="bfbea-109">Plik XML można wygenerować w czasie kompilacji, wykonując jedną z następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="bfbea-109">You can generate the XML file at compile time by doing one of the following:</span></span>

- <span data-ttu-id="bfbea-110">Jeśli tworzysz aplikację przy użyciu platformy .NET Core z wiersza polecenia, możesz dodać element `GenerateDocumentationFile` do sekcji `<PropertyGroup>` pliku projektu. csproj.</span><span class="sxs-lookup"><span data-stu-id="bfbea-110">If you are developing an application with .NET Core from the command line, you can add a `GenerateDocumentationFile` element to the `<PropertyGroup>` section of your .csproj project file.</span></span> <span data-ttu-id="bfbea-111">Możesz również określić ścieżkę do pliku dokumentacji bezpośrednio przy użyciu [elementu`DocumentationFile`](/visualstudio/msbuild/common-msbuild-project-properties).</span><span class="sxs-lookup"><span data-stu-id="bfbea-111">You can also specify the path to the documentation file directly using [`DocumentationFile` element](/visualstudio/msbuild/common-msbuild-project-properties).</span></span> <span data-ttu-id="bfbea-112">Poniższy przykład generuje plik XML w katalogu projektu z tą samą nazwą pliku głównego co zestaw:</span><span class="sxs-lookup"><span data-stu-id="bfbea-112">The following example generates an XML file in the project directory with the same root filename as the assembly:</span></span>

   ```xml
   <GenerateDocumentationFile>true</GenerateDocumentationFile>
   ```
   
   <span data-ttu-id="bfbea-113">Jest to równoważne z następującymi:</span><span class="sxs-lookup"><span data-stu-id="bfbea-113">This is equivalent to the following:</span></span>
   
   ```xml
   <DocumentationFile>bin\$(Configuration)\$(TargetFramework)\$(AssemblyName).xml</DocumentationFile>
   ```

- <span data-ttu-id="bfbea-114">Jeśli tworzysz aplikację przy użyciu programu Visual Studio, kliknij prawym przyciskiem myszy projekt i wybierz polecenie **Właściwości**.</span><span class="sxs-lookup"><span data-stu-id="bfbea-114">If you are developing an application using Visual Studio, right-click on the project and select **Properties**.</span></span> <span data-ttu-id="bfbea-115">W oknie dialogowym właściwości wybierz kartę **kompilacja** i sprawdź **plik dokumentacji XML**.</span><span class="sxs-lookup"><span data-stu-id="bfbea-115">In the properties dialog, select the **Build** tab, and check **XML documentation file**.</span></span> <span data-ttu-id="bfbea-116">Możesz również zmienić lokalizację, w której kompilator zapisuje plik.</span><span class="sxs-lookup"><span data-stu-id="bfbea-116">You can also change the location to which the compiler writes the file.</span></span>

- <span data-ttu-id="bfbea-117">Jeśli kompilujesz aplikację .NET Framework z wiersza polecenia, Dodaj [opcję kompilatora-doc](language-reference/compiler-options/doc-compiler-option.md) podczas kompilowania.</span><span class="sxs-lookup"><span data-stu-id="bfbea-117">If you are compiling a .NET Framework application from the command line, add the [-doc compiler option](language-reference/compiler-options/doc-compiler-option.md) when compiling.</span></span>  

<span data-ttu-id="bfbea-118">Komentarze dokumentacji XML używają potrójnych ukośników (`///`) i treści komentarza w formacie XML.</span><span class="sxs-lookup"><span data-stu-id="bfbea-118">XML documentation comments use triple forward slashes (`///`) and an XML formatted comment body.</span></span> <span data-ttu-id="bfbea-119">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="bfbea-119">For example:</span></span>

[!code-csharp[XML Documentation Comment](../../samples/snippets/csharp/concepts/codedoc/xml-comment.cs)]

## <a name="walkthrough"></a><span data-ttu-id="bfbea-120">Instruktaż</span><span class="sxs-lookup"><span data-stu-id="bfbea-120">Walkthrough</span></span>

<span data-ttu-id="bfbea-121">Zapoznaj się z dokumentem bardzo podstawową bibliotekę matematyczną, aby ułatwić nowym deweloperom zrozumienie/współtworzenie i współdziałanie z innymi programistami.</span><span class="sxs-lookup"><span data-stu-id="bfbea-121">Let's walk through documenting a very basic math library to make it easy for new developers to understand/contribute and for third party developers to use.</span></span>

<span data-ttu-id="bfbea-122">Oto kod dla prostej biblioteki matematycznej:</span><span class="sxs-lookup"><span data-stu-id="bfbea-122">Here's code for the simple math library:</span></span>

[!code-csharp[Sample Library](../../samples/snippets/csharp/concepts/codedoc/sample-library.cs)]

<span data-ttu-id="bfbea-123">Biblioteka Przykładowa obsługuje cztery główne operacje arytmetyczne `add`, `subtract`, `multiply` i `divide` na `int` i `double` typy danych.</span><span class="sxs-lookup"><span data-stu-id="bfbea-123">The sample library supports four major arithmetic operations `add`, `subtract`, `multiply` and `divide` on `int` and `double` data types.</span></span>

<span data-ttu-id="bfbea-124">Teraz chcesz mieć możliwość utworzenia dokumentu referencyjnego interfejsu API na podstawie kodu dla deweloperów innych firm, którzy korzystają z biblioteki, ale nie mają dostępu do kodu źródłowego.</span><span class="sxs-lookup"><span data-stu-id="bfbea-124">Now you want to be able to create an API reference document from your code for third party developers who use your library but don't have access to the source code.</span></span>
<span data-ttu-id="bfbea-125">Jak wspomniano wcześniej Tagi dokumentacji XML, można użyć w tym celu.</span><span class="sxs-lookup"><span data-stu-id="bfbea-125">As mentioned earlier XML documentation tags can be used to achieve this.</span></span> <span data-ttu-id="bfbea-126">Teraz będziesz wprowadzać do standardowych tagów XML obsługiwanych przez C# kompilator.</span><span class="sxs-lookup"><span data-stu-id="bfbea-126">You will now be introduced to the standard XML tags the C# compiler supports.</span></span>

## <a name="summary"></a><span data-ttu-id="bfbea-127">\<summary></span><span class="sxs-lookup"><span data-stu-id="bfbea-127">\<summary></span></span>

<span data-ttu-id="bfbea-128">Tag `<summary>` dodaje krótkie informacje dotyczące typu lub składowej.</span><span class="sxs-lookup"><span data-stu-id="bfbea-128">The `<summary>` tag adds brief information about a type or member.</span></span>
<span data-ttu-id="bfbea-129">Pokażę swoje użycie przez dodanie go do definicji klasy `Math` i pierwszej metody `Add`.</span><span class="sxs-lookup"><span data-stu-id="bfbea-129">I'll demonstrate its use by adding it to the `Math` class definition and the first `Add` method.</span></span> <span data-ttu-id="bfbea-130">Śmiało, aby zastosować go do pozostałej części kodu.</span><span class="sxs-lookup"><span data-stu-id="bfbea-130">Feel free to apply it to the rest of your code.</span></span>

[!code-csharp[Summary Tag](../../samples/snippets/csharp/concepts/codedoc/summary-tag.cs)]

<span data-ttu-id="bfbea-131">Tag `<summary>` jest bardzo istotny i zalecamy dołączenie go, ponieważ jego zawartość jest podstawowym źródłem informacji o typie lub elemencie członkowskim w technologii IntelliSense lub dokumentacji interfejsu API.</span><span class="sxs-lookup"><span data-stu-id="bfbea-131">The `<summary>` tag is very important, and we recommend that you include it because its content is the primary source of type or member information in IntelliSense or an API reference document.</span></span>

## <a name="remarks"></a><span data-ttu-id="bfbea-132">\<remarks ></span><span class="sxs-lookup"><span data-stu-id="bfbea-132">\<remarks></span></span>

<span data-ttu-id="bfbea-133">Tag `<remarks>` uzupełnia informacje o typach lub elementach członkowskich udostępnianych przez tag `<summary>`.</span><span class="sxs-lookup"><span data-stu-id="bfbea-133">The `<remarks>` tag supplements the information about types or members that the `<summary>` tag provides.</span></span> <span data-ttu-id="bfbea-134">W tym przykładzie wystarczy dodać go do klasy.</span><span class="sxs-lookup"><span data-stu-id="bfbea-134">In this example, you'll just add it to the class.</span></span>

[!code-csharp[Remarks Tag](../../samples/snippets/csharp/concepts/codedoc/remarks-tag.cs)]

## <a name="returns"></a><span data-ttu-id="bfbea-135">\<returns></span><span class="sxs-lookup"><span data-stu-id="bfbea-135">\<returns></span></span>

<span data-ttu-id="bfbea-136">Tag `<returns>` opisuje wartość zwracaną deklaracji metody.</span><span class="sxs-lookup"><span data-stu-id="bfbea-136">The `<returns>` tag describes the return value of a method declaration.</span></span>
<span data-ttu-id="bfbea-137">Tak jak wcześniej Poniższy przykład ilustruje tag `<returns>` na pierwszej `Add` metodzie.</span><span class="sxs-lookup"><span data-stu-id="bfbea-137">As before, the following example illustrates the `<returns>` tag on the first `Add` method.</span></span> <span data-ttu-id="bfbea-138">Można to zrobić w innych metodach.</span><span class="sxs-lookup"><span data-stu-id="bfbea-138">You can do the same on other methods.</span></span>

[!code-csharp[Returns Tag](../../samples/snippets/csharp/concepts/codedoc/returns-tag.cs)]

## <a name="value"></a><span data-ttu-id="bfbea-139">\<value></span><span class="sxs-lookup"><span data-stu-id="bfbea-139">\<value></span></span>

<span data-ttu-id="bfbea-140">Tag `<value>` jest podobny do tagu `<returns>`, z tą różnicą, że jest używany do właściwości.</span><span class="sxs-lookup"><span data-stu-id="bfbea-140">The `<value>` tag is similar to the `<returns>` tag, except that you use it for properties.</span></span>
<span data-ttu-id="bfbea-141">Zakładając, że biblioteka `Math` ma właściwość statyczną o nazwie `PI`, poniżej przedstawiono sposób użycia tego tagu:</span><span class="sxs-lookup"><span data-stu-id="bfbea-141">Assuming your `Math` library had a static property called `PI`, here's how you'd use this tag:</span></span>

[!code-csharp[Value Tag](../../samples/snippets/csharp/concepts/codedoc/value-tag.cs)]

## <a name="example"></a><span data-ttu-id="bfbea-142">\<example ></span><span class="sxs-lookup"><span data-stu-id="bfbea-142">\<example></span></span>

<span data-ttu-id="bfbea-143">Używasz znacznika `<example>`, aby dołączyć przykład do dokumentacji XML.</span><span class="sxs-lookup"><span data-stu-id="bfbea-143">You use the `<example>` tag to include an example in your XML documentation.</span></span>
<span data-ttu-id="bfbea-144">Obejmuje to użycie znacznika `<code>` podrzędnego.</span><span class="sxs-lookup"><span data-stu-id="bfbea-144">This involves using the child `<code>` tag.</span></span>

[!code-csharp[Example Tag](../../samples/snippets/csharp/concepts/codedoc/example-tag.cs)]

<span data-ttu-id="bfbea-145">Tag `code` zachowuje podziały wierszy i wcięcia dla dłuższych przykładów.</span><span class="sxs-lookup"><span data-stu-id="bfbea-145">The `code` tag preserves line breaks and indentation for longer examples.</span></span>

## <a name="para"></a><span data-ttu-id="bfbea-146">\<para ></span><span class="sxs-lookup"><span data-stu-id="bfbea-146">\<para></span></span>

<span data-ttu-id="bfbea-147">Aby sformatować zawartość w tagu nadrzędnym, Użyj znacznika `<para>`.</span><span class="sxs-lookup"><span data-stu-id="bfbea-147">You use the `<para>` tag to format the content within its parent tag.</span></span> <span data-ttu-id="bfbea-148">`<para>` jest zwykle używany wewnątrz tagu, takiego jak `<remarks>` lub `<returns>`, aby podzielić tekst na akapity.</span><span class="sxs-lookup"><span data-stu-id="bfbea-148">`<para>` is usually used inside a tag, such as `<remarks>` or `<returns>`, to divide text into paragraphs.</span></span>
<span data-ttu-id="bfbea-149">Można sformatować zawartość tagu `<remarks>` w definicji klasy.</span><span class="sxs-lookup"><span data-stu-id="bfbea-149">You can format the contents of the `<remarks>` tag for your class definition.</span></span>

[!code-csharp[Para Tag](../../samples/snippets/csharp/concepts/codedoc/para-tag.cs)]

## <a name="c"></a><span data-ttu-id="bfbea-150">\<c ></span><span class="sxs-lookup"><span data-stu-id="bfbea-150">\<c></span></span>

<span data-ttu-id="bfbea-151">Nadal w temacie formatowania, używasz znacznika `<c>` do oznaczania części tekstu jako kodu.</span><span class="sxs-lookup"><span data-stu-id="bfbea-151">Still on the topic of formatting, you use the `<c>` tag for marking part of text as code.</span></span>
<span data-ttu-id="bfbea-152">Przypomina znacznik `<code>`, ale wbudowany.</span><span class="sxs-lookup"><span data-stu-id="bfbea-152">It's like the `<code>` tag but inline.</span></span> <span data-ttu-id="bfbea-153">Jest to przydatne, gdy chcesz pokazać przykładowy kod jako część zawartości znacznika.</span><span class="sxs-lookup"><span data-stu-id="bfbea-153">It's useful when you want to show a quick code example as part of a tag's content.</span></span>
<span data-ttu-id="bfbea-154">Zaktualizujmy dokumentację klasy `Math`.</span><span class="sxs-lookup"><span data-stu-id="bfbea-154">Let's update the documentation for the `Math` class.</span></span>

[!code-csharp[C Tag](../../samples/snippets/csharp/concepts/codedoc/c-tag.cs)]

## <a name="exception"></a><span data-ttu-id="bfbea-155">\<exception ></span><span class="sxs-lookup"><span data-stu-id="bfbea-155">\<exception></span></span>

<span data-ttu-id="bfbea-156">Przy użyciu znacznika `<exception>` pozwalasz deweloperom znać, że metoda może zgłosić określone wyjątki.</span><span class="sxs-lookup"><span data-stu-id="bfbea-156">By using the `<exception>` tag, you let your developers know that a method can throw specific exceptions.</span></span>
<span data-ttu-id="bfbea-157">Przeglądając bibliotekę `Math`, można zobaczyć, że obie metody `Add` zgłaszają wyjątek, jeśli spełniony jest określony warunek.</span><span class="sxs-lookup"><span data-stu-id="bfbea-157">Looking at your `Math` library, you can see that both `Add` methods throw an exception if a certain condition is met.</span></span> <span data-ttu-id="bfbea-158">Chociaż nie jest to oczywiste, jest to, że metoda `Divide` Integer zwraca również, jeśli parametr `b` ma wartość zero.</span><span class="sxs-lookup"><span data-stu-id="bfbea-158">Not so obvious, though, is that integer `Divide` method throws as well if the `b` parameter is zero.</span></span> <span data-ttu-id="bfbea-159">Teraz Dodaj dokumentację wyjątku do tej metody.</span><span class="sxs-lookup"><span data-stu-id="bfbea-159">Now add exception documentation to this method.</span></span>

[!code-csharp[Exception Tag](../../samples/snippets/csharp/concepts/codedoc/exception-tag.cs)]

<span data-ttu-id="bfbea-160">Atrybut `cref` reprezentuje odwołanie do wyjątku, który jest dostępny w bieżącym środowisku kompilacji.</span><span class="sxs-lookup"><span data-stu-id="bfbea-160">The `cref` attribute represents a reference to an exception that is available from the current compilation environment.</span></span>
<span data-ttu-id="bfbea-161">Może to być dowolny typ zdefiniowany w projekcie lub przywoływanym zestawie.</span><span class="sxs-lookup"><span data-stu-id="bfbea-161">This can be any type defined in the project or a referenced assembly.</span></span> <span data-ttu-id="bfbea-162">Kompilator wyświetli ostrzeżenie, jeśli nie można rozpoznać jego wartości.</span><span class="sxs-lookup"><span data-stu-id="bfbea-162">The compiler will issue a warning if its value cannot be resolved.</span></span>

## <a name="see"></a><span data-ttu-id="bfbea-163">\<see ></span><span class="sxs-lookup"><span data-stu-id="bfbea-163">\<see></span></span>

<span data-ttu-id="bfbea-164">Tag `<see>` umożliwia utworzenie linku kliknięcia do strony dokumentacji dla innego elementu kodu.</span><span class="sxs-lookup"><span data-stu-id="bfbea-164">The `<see>` tag lets you create a clickable link to a documentation page for another code element.</span></span> <span data-ttu-id="bfbea-165">W następnym przykładzie utworzysz link do kliknięcia między dwoma `Add` metodami.</span><span class="sxs-lookup"><span data-stu-id="bfbea-165">In our next example, we'll create a clickable link between the two `Add` methods.</span></span>

[!code-csharp[See Tag](../../samples/snippets/csharp/concepts/codedoc/see-tag.cs)]

<span data-ttu-id="bfbea-166">`cref` jest **wymaganym** atrybutem, który reprezentuje odwołanie do typu lub jego elementu członkowskiego, który jest dostępny w bieżącym środowisku kompilacji.</span><span class="sxs-lookup"><span data-stu-id="bfbea-166">The `cref` is a **required** attribute that represents a reference to a type or its member that is available from the current compilation environment.</span></span>
<span data-ttu-id="bfbea-167">Może to być dowolny typ zdefiniowany w projekcie lub przywoływanym zestawie.</span><span class="sxs-lookup"><span data-stu-id="bfbea-167">This can be any type defined in the project or a referenced assembly.</span></span>

## <a name="seealso"></a><span data-ttu-id="bfbea-168">\<seealso ></span><span class="sxs-lookup"><span data-stu-id="bfbea-168">\<seealso></span></span>

<span data-ttu-id="bfbea-169">Używasz znacznika `<seealso>` w taki sam sposób jak tag `<see>`.</span><span class="sxs-lookup"><span data-stu-id="bfbea-169">You use the `<seealso>` tag in the same way you do the `<see>` tag.</span></span> <span data-ttu-id="bfbea-170">Jedyną różnicą jest to, że jej zawartość jest zwykle umieszczana w sekcji "Zobacz też".</span><span class="sxs-lookup"><span data-stu-id="bfbea-170">The only difference is that its content is typically placed in a "See Also" section.</span></span> <span data-ttu-id="bfbea-171">Tutaj dodamy znacznik `seealso` w metodzie `Add` Integer, aby odwołać się do innych metod w klasie, która akceptuje parametry całkowite:</span><span class="sxs-lookup"><span data-stu-id="bfbea-171">Here we'll add a `seealso` tag on the integer `Add` method to reference other methods in the class that accept integer parameters:</span></span>

[!code-csharp[Seealso Tag](../../samples/snippets/csharp/concepts/codedoc/seealso-tag.cs)]

<span data-ttu-id="bfbea-172">Atrybut `cref` reprezentuje odwołanie do typu lub jego elementu członkowskiego, który jest dostępny w bieżącym środowisku kompilacji.</span><span class="sxs-lookup"><span data-stu-id="bfbea-172">The `cref` attribute represents a reference to a type or its member that is available from the current compilation environment.</span></span>
<span data-ttu-id="bfbea-173">Może to być dowolny typ zdefiniowany w projekcie lub przywoływanym zestawie.</span><span class="sxs-lookup"><span data-stu-id="bfbea-173">This can be any type defined in the project or a referenced assembly.</span></span>

## <a name="param"></a><span data-ttu-id="bfbea-174">\<param></span><span class="sxs-lookup"><span data-stu-id="bfbea-174">\<param></span></span>

<span data-ttu-id="bfbea-175">Za pomocą tagu `<param>` można opisać parametry metody.</span><span class="sxs-lookup"><span data-stu-id="bfbea-175">You use the `<param>` tag to describe a method's parameters.</span></span> <span data-ttu-id="bfbea-176">Oto przykład dotyczący metody Double `Add`: parametr opisany w opisie jest określony w **wymaganym** atrybucie `name`.</span><span class="sxs-lookup"><span data-stu-id="bfbea-176">Here's an example on the double `Add` method: The parameter the tag describes is specified in the **required** `name` attribute.</span></span>

[!code-csharp[Param Tag](../../samples/snippets/csharp/concepts/codedoc/param-tag.cs)]

## <a name="typeparam"></a><span data-ttu-id="bfbea-177">\<typeparam ></span><span class="sxs-lookup"><span data-stu-id="bfbea-177">\<typeparam></span></span>

<span data-ttu-id="bfbea-178">Używasz tagu `<typeparam>`, podobnie jak tag `<param>`, ale dla deklaracji typu ogólnego lub metody, aby opisać parametr generyczny.</span><span class="sxs-lookup"><span data-stu-id="bfbea-178">You use `<typeparam>` tag just like the `<param>` tag but for generic type or method declarations to describe a generic parameter.</span></span>
<span data-ttu-id="bfbea-179">Dodaj szybką metodę rodzajową do klasy `Math`, aby sprawdzić, czy jedna ilość jest większa niż inna.</span><span class="sxs-lookup"><span data-stu-id="bfbea-179">Add a quick generic method to your `Math` class to check if one quantity is greater than another.</span></span>

[!code-csharp[Typeparam Tag](../../samples/snippets/csharp/concepts/codedoc/typeparam-tag.cs)]

## <a name="paramref"></a><span data-ttu-id="bfbea-180">\<paramref ></span><span class="sxs-lookup"><span data-stu-id="bfbea-180">\<paramref></span></span>

<span data-ttu-id="bfbea-181">Czasami może być w środku opisującym opisywanie metody w tym, co może być tagiem `<summary>` i można utworzyć odwołanie do parametru.</span><span class="sxs-lookup"><span data-stu-id="bfbea-181">Sometimes you might be in the middle of describing what a method does in what could be a `<summary>` tag, and you might want to make a reference to a parameter.</span></span> <span data-ttu-id="bfbea-182">Tag `<paramref>` jest świetny dla samego siebie.</span><span class="sxs-lookup"><span data-stu-id="bfbea-182">The `<paramref>` tag is great for just this.</span></span> <span data-ttu-id="bfbea-183">Zaktualizujmy podsumowanie naszej metody `Add` opartej na podwójnej precyzji.</span><span class="sxs-lookup"><span data-stu-id="bfbea-183">Let's update the summary of our double based `Add` method.</span></span> <span data-ttu-id="bfbea-184">Podobnie jak w przypadku znacznika `<param>` Nazwa parametru jest określona w **wymaganym** atrybucie `name`.</span><span class="sxs-lookup"><span data-stu-id="bfbea-184">Like the `<param>` tag the parameter name is specified in the **required** `name` attribute.</span></span>

[!code-csharp[Paramref Tag](../../samples/snippets/csharp/concepts/codedoc/paramref-tag.cs)]

## <a name="typeparamref"></a><span data-ttu-id="bfbea-185">\<typeparamref ></span><span class="sxs-lookup"><span data-stu-id="bfbea-185">\<typeparamref></span></span>

<span data-ttu-id="bfbea-186">Używasz tagu `<typeparamref>`, podobnie jak tag `<paramref>`, ale dla deklaracji typu ogólnego lub metody, aby opisać parametr generyczny.</span><span class="sxs-lookup"><span data-stu-id="bfbea-186">You use `<typeparamref>` tag just like the `<paramref>` tag but for generic type or method declarations to describe a generic parameter.</span></span>
<span data-ttu-id="bfbea-187">Możesz użyć tej samej metody generycznej, która została wcześniej utworzona.</span><span class="sxs-lookup"><span data-stu-id="bfbea-187">You can use the same generic method you previously created.</span></span>

[!code-csharp[Typeparamref Tag](../../samples/snippets/csharp/concepts/codedoc/typeparamref-tag.cs)]

## <a name="list"></a><span data-ttu-id="bfbea-188">\<list ></span><span class="sxs-lookup"><span data-stu-id="bfbea-188">\<list></span></span>

<span data-ttu-id="bfbea-189">Tag `<list>` służy do formatowania informacji dokumentacji jako listy uporządkowanej, nieuporządkowanej listy lub tabeli.</span><span class="sxs-lookup"><span data-stu-id="bfbea-189">You use the `<list>` tag to format documentation information as an ordered list, unordered list or table.</span></span>
<span data-ttu-id="bfbea-190">Utwórz nieuporządkowaną listę każdej operacji matematycznej obsługiwanej przez bibliotekę `Math`.</span><span class="sxs-lookup"><span data-stu-id="bfbea-190">Make an unordered list of every math operation your `Math` library supports.</span></span>

[!code-csharp[List Tag](../../samples/snippets/csharp/concepts/codedoc/list-tag.cs)]

<span data-ttu-id="bfbea-191">Można utworzyć uporządkowaną listę lub tabelę, zmieniając atrybut `type` na odpowiednio `number` lub `table`.</span><span class="sxs-lookup"><span data-stu-id="bfbea-191">You can make an ordered list or table by changing the `type` attribute to `number` or `table`, respectively.</span></span>

### <a name="putting-it-all-together"></a><span data-ttu-id="bfbea-192">Umieszczanie wszystkich razem</span><span class="sxs-lookup"><span data-stu-id="bfbea-192">Putting it all together</span></span>

<span data-ttu-id="bfbea-193">Jeśli wykonano ten samouczek i zastosowano znaczniki do kodu w razie potrzeby, kod powinien teraz wyglądać podobnie do poniższego:</span><span class="sxs-lookup"><span data-stu-id="bfbea-193">If you've followed this tutorial and applied the tags to your code where necessary, your code should now look similar to the following:</span></span>

[!code-csharp[Tagged Library](../../samples/snippets/csharp/concepts/codedoc/tagged-library.cs)]

<span data-ttu-id="bfbea-194">Z poziomu kodu można wygenerować szczegółową witrynę sieci Web, która została ukończona z kliknięciami odwołania krzyżowego.</span><span class="sxs-lookup"><span data-stu-id="bfbea-194">From your code, you can generate a detailed documentation website complete with clickable cross-references.</span></span> <span data-ttu-id="bfbea-195">Ale nastąpiło inne zagadnienie: Twój kod stał się trudno odczytać.</span><span class="sxs-lookup"><span data-stu-id="bfbea-195">But you're faced with another problem: your code has become hard to read.</span></span>
<span data-ttu-id="bfbea-196">Istnieje dużo informacji do przesiania przez to, że jest to okropnej dla każdego dewelopera, który chce współtworzyć ten kod.</span><span class="sxs-lookup"><span data-stu-id="bfbea-196">There's so much information to sift through that this is going to be a nightmare for any developer who wants to contribute to this code.</span></span>
<span data-ttu-id="bfbea-197">Thankfully istnieje tag XML, który może pomóc Ci w poradzić sobie z:</span><span class="sxs-lookup"><span data-stu-id="bfbea-197">Thankfully there's an XML tag that can help you deal with this:</span></span>

## <a name="include"></a><span data-ttu-id="bfbea-198">\<include ></span><span class="sxs-lookup"><span data-stu-id="bfbea-198">\<include></span></span>

<span data-ttu-id="bfbea-199">Tag `<include>` umożliwia odwoływanie się do komentarzy w osobnym pliku XML, który opisuje typy i elementy członkowskie w kodzie źródłowym, zamiast umieszczania komentarzy do dokumentacji bezpośrednio w pliku kodu źródłowego.</span><span class="sxs-lookup"><span data-stu-id="bfbea-199">The `<include>` tag lets you refer to comments in a separate XML file that describe the types and members in your source code, as opposed to placing documentation comments directly in your source code file.</span></span>

<span data-ttu-id="bfbea-200">Teraz można przenieść wszystkie tagi XML do oddzielnego pliku XML o nazwie `docs.xml`.</span><span class="sxs-lookup"><span data-stu-id="bfbea-200">Now you're going to move all your XML tags into a separate XML file named `docs.xml`.</span></span> <span data-ttu-id="bfbea-201">Możesz nawiązać dowolną nazwę pliku.</span><span class="sxs-lookup"><span data-stu-id="bfbea-201">Feel free to name the file whatever you want.</span></span>

[!code-xml[Sample XML](../../samples/snippets/csharp/concepts/codedoc/include.xml)]

<span data-ttu-id="bfbea-202">W powyższym kodzie XML komentarze dokumentacji każdego członka są wyświetlane bezpośrednio wewnątrz tagu o nazwie po tym, co robią.</span><span class="sxs-lookup"><span data-stu-id="bfbea-202">In the above XML, each member's documentation comments appear directly inside a tag named after what they do.</span></span> <span data-ttu-id="bfbea-203">Możesz wybrać własną strategię.</span><span class="sxs-lookup"><span data-stu-id="bfbea-203">You can choose your own strategy.</span></span>
<span data-ttu-id="bfbea-204">Teraz, gdy masz Komentarze XML w osobnym pliku, zobaczmy, jak kod może być bardziej czytelny przy użyciu tagu `<include>`:</span><span class="sxs-lookup"><span data-stu-id="bfbea-204">Now that you have your XML comments in a separate file, let's see how your code can be made more readable by using the `<include>` tag:</span></span>

[!code-csharp[Include Tag](../../samples/snippets/csharp/concepts/codedoc/include-tag.cs)]

<span data-ttu-id="bfbea-205">Jest to możliwe: kod jest z powrotem odczytywany, a informacje o dokumentacji nie zostały utracone.</span><span class="sxs-lookup"><span data-stu-id="bfbea-205">And there you have it: our code is back to being readable, and no documentation information has been lost.</span></span>

<span data-ttu-id="bfbea-206">Atrybut `file` reprezentuje nazwę pliku XML zawierającego dokumentację.</span><span class="sxs-lookup"><span data-stu-id="bfbea-206">The `file` attribute represents the name of the XML file containing the documentation.</span></span>

<span data-ttu-id="bfbea-207">Atrybut `path` reprezentuje zapytanie [XPath](../standard/data/xml/xpath-queries-and-namespaces.md) do `tag name` obecne w określonym `file`.</span><span class="sxs-lookup"><span data-stu-id="bfbea-207">The `path` attribute represents an [XPath](../standard/data/xml/xpath-queries-and-namespaces.md) query to the `tag name` present in the specified `file`.</span></span>

<span data-ttu-id="bfbea-208">Atrybut `name` reprezentuje specyfikator Name w tagu, który poprzedza Komentarze.</span><span class="sxs-lookup"><span data-stu-id="bfbea-208">The `name` attribute represents the name specifier in the tag that precedes the comments.</span></span>

<span data-ttu-id="bfbea-209">Atrybut `id`, który może być użyty zamiast `name` reprezentuje identyfikator tagu, który poprzedza Komentarze.</span><span class="sxs-lookup"><span data-stu-id="bfbea-209">The `id` attribute which can be used in place of `name` represents the ID for the tag that precedes the comments.</span></span>

### <a name="user-defined-tags"></a><span data-ttu-id="bfbea-210">Tagi zdefiniowane przez użytkownika</span><span class="sxs-lookup"><span data-stu-id="bfbea-210">User Defined Tags</span></span>

<span data-ttu-id="bfbea-211">Wszystkie Tagi podane powyżej reprezentują te, które są rozpoznawane przez C# kompilator.</span><span class="sxs-lookup"><span data-stu-id="bfbea-211">All the tags outlined above represent those that are recognized by the C# compiler.</span></span> <span data-ttu-id="bfbea-212">Jednak użytkownik może definiować własne znaczniki.</span><span class="sxs-lookup"><span data-stu-id="bfbea-212">However, a user is free to define their own tags.</span></span>
<span data-ttu-id="bfbea-213">Narzędzia takie jak Sandcastle zapewniają obsługę dodatkowych tagów, takich jak [`<event>`](https://ewsoftware.github.io/XMLCommentsGuide/html/81bf7ad3-45dc-452f-90d5-87ce2494a182.htm), [`<note>`](https://ewsoftware.github.io/XMLCommentsGuide/html/4302a60f-e4f4-4b8d-a451-5f453c4ebd46.htm) i nawet obsługują [dokumenty przestrzeni nazw](https://ewsoftware.github.io/XMLCommentsGuide/html/BD91FAD4-188D-4697-A654-7C07FD47EF31.htm).</span><span class="sxs-lookup"><span data-stu-id="bfbea-213">Tools like Sandcastle bring support for extra tags like [`<event>`](https://ewsoftware.github.io/XMLCommentsGuide/html/81bf7ad3-45dc-452f-90d5-87ce2494a182.htm), [`<note>`](https://ewsoftware.github.io/XMLCommentsGuide/html/4302a60f-e4f4-4b8d-a451-5f453c4ebd46.htm) and even support [documenting namespaces](https://ewsoftware.github.io/XMLCommentsGuide/html/BD91FAD4-188D-4697-A654-7C07FD47EF31.htm).</span></span>
<span data-ttu-id="bfbea-214">Niestandardowe i wewnętrzne narzędzia do generowania dokumentacji mogą również być używane ze znacznikami standardowymi i można obsługiwać wiele formatów wyjściowych z formatu HTML do pliku PDF.</span><span class="sxs-lookup"><span data-stu-id="bfbea-214">Custom or in-house documentation generation tools can also be used with the standard tags and multiple output formats from HTML to PDF can be supported.</span></span>

## <a name="recommendations"></a><span data-ttu-id="bfbea-215">Mając</span><span class="sxs-lookup"><span data-stu-id="bfbea-215">Recommendations</span></span>

<span data-ttu-id="bfbea-216">Dokumentowanie kodu jest zalecane z wielu powodów.</span><span class="sxs-lookup"><span data-stu-id="bfbea-216">Documenting code is recommended for many reasons.</span></span> <span data-ttu-id="bfbea-217">Poniżej przedstawiono niektóre najlepsze rozwiązania, ogólne scenariusze przypadków użycia i informacje, które należy znać w przypadku używania tagów dokumentacji XML w C# kodzie.</span><span class="sxs-lookup"><span data-stu-id="bfbea-217">What follows are some best practices, general use case scenarios, and things that you should know when using XML documentation tags in your C# code.</span></span>

- <span data-ttu-id="bfbea-218">Ze względu na spójność wszystkich publicznie widocznych typów i ich członków należy udokumentować.</span><span class="sxs-lookup"><span data-stu-id="bfbea-218">For the sake of consistency, all publicly visible types and their members should be documented.</span></span> <span data-ttu-id="bfbea-219">Jeśli to konieczne, zrób wszystko.</span><span class="sxs-lookup"><span data-stu-id="bfbea-219">If you must do it, do it all.</span></span>
- <span data-ttu-id="bfbea-220">Prywatne elementy członkowskie mogą być również udokumentowane przy użyciu komentarzy XML.</span><span class="sxs-lookup"><span data-stu-id="bfbea-220">Private members can also be documented using XML comments.</span></span> <span data-ttu-id="bfbea-221">Jednak spowoduje to uwidocznienie wewnętrznej (potencjalnie poufnej) pracy biblioteki.</span><span class="sxs-lookup"><span data-stu-id="bfbea-221">However, this exposes the inner (potentially confidential) workings of your library.</span></span>
- <span data-ttu-id="bfbea-222">W przypadku braku systemu operacyjnego typy i ich elementy członkowskie powinny mieć tag `<summary>`, ponieważ jego zawartość jest wymagana przez funkcję IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="bfbea-222">At a bare minimum, types and their members should have a `<summary>` tag because its content is needed for IntelliSense.</span></span>
- <span data-ttu-id="bfbea-223">Tekst dokumentacji należy napisać przy użyciu kompletnych zdań kończących się pełnym zatrzymywaniem.</span><span class="sxs-lookup"><span data-stu-id="bfbea-223">Documentation text should be written using complete sentences ending with full stops.</span></span>
- <span data-ttu-id="bfbea-224">Klasy częściowe są w pełni obsługiwane, a informacje o dokumentacji są łączone w jeden wpis dla tego typu.</span><span class="sxs-lookup"><span data-stu-id="bfbea-224">Partial classes are fully supported, and documentation information will be concatenated into a single entry for that type.</span></span>
- <span data-ttu-id="bfbea-225">Kompilator weryfikuje składnię `<exception>`, `<include>`, `<param>`, `<see>`, `<seealso>` i `<typeparam>`.</span><span class="sxs-lookup"><span data-stu-id="bfbea-225">The compiler verifies the syntax of the `<exception>`, `<include>`, `<param>`, `<see>`, `<seealso>` and `<typeparam>` tags.</span></span>
- <span data-ttu-id="bfbea-226">Kompilator sprawdza poprawność parametrów zawierających ścieżki plików i odwołania do innych części kodu.</span><span class="sxs-lookup"><span data-stu-id="bfbea-226">The compiler validates the parameters that contain file paths and references to other parts of the code.</span></span>

## <a name="see-also"></a><span data-ttu-id="bfbea-227">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="bfbea-227">See also</span></span>

- [<span data-ttu-id="bfbea-228">Komentarze dokumentacji XML (C# Przewodnik programowania)</span><span class="sxs-lookup"><span data-stu-id="bfbea-228">XML Documentation Comments (C# Programming Guide)</span></span>](programming-guide/xmldoc/index.md)
- [<span data-ttu-id="bfbea-229">Zalecane Tagi dla komentarzy do dokumentacjiC# (Przewodnik programowania)</span><span class="sxs-lookup"><span data-stu-id="bfbea-229">Recommended Tags for Documentation Comments (C# Programming Guide)</span></span>](programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)
