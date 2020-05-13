---
title: Lokalizowanie aplikacji
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- localization [WPF], applications
- LocBaml tool [WPF]
- applications [WPF], localizing
ms.assetid: 5001227e-9326-48a4-9dcd-ba1b89ee6653
ms.openlocfilehash: dc7d8f4f56b26fffbd883e1e1d6e420026e1f94f
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/12/2020
ms.locfileid: "83209685"
---
# <a name="how-to-localize-an-application"></a><span data-ttu-id="16808-102">Instrukcje: lokalizowanie aplikacji</span><span class="sxs-lookup"><span data-stu-id="16808-102">How to: Localize an application</span></span>

<span data-ttu-id="16808-103">W tym samouczku wyjaśniono, jak utworzyć zlokalizowaną aplikację przy użyciu narzędzia LocBaml.</span><span class="sxs-lookup"><span data-stu-id="16808-103">This tutorial explains how to create a localized application by using the LocBaml tool.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="16808-104">Narzędzie LocBaml nie jest aplikacją przygotowaną do produkcji.</span><span class="sxs-lookup"><span data-stu-id="16808-104">The LocBaml tool is not a production-ready application.</span></span> <span data-ttu-id="16808-105">Jest on prezentowany jako przykład, który używa niektórych interfejsów API lokalizacji i ilustruje sposób pisania narzędzia lokalizacji.</span><span class="sxs-lookup"><span data-stu-id="16808-105">It is presented as a sample that uses some of the localization APIs and illustrates how you might write a localization tool.</span></span>  
  
## <a name="overview"></a><span data-ttu-id="16808-106">Omówienie</span><span class="sxs-lookup"><span data-stu-id="16808-106">Overview</span></span>

<span data-ttu-id="16808-107">Ten artykuł zawiera podejście krok po kroku dotyczące lokalizowania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="16808-107">This article gives you a step-by-step approach to localizing an application.</span></span> <span data-ttu-id="16808-108">Najpierw należy przygotować aplikację tak, aby tekst, który zostanie przetłumaczony, mógł zostać wyodrębniony.</span><span class="sxs-lookup"><span data-stu-id="16808-108">First, you prepare your application so that the text that will be translated can be extracted.</span></span> <span data-ttu-id="16808-109">Po przetłumaczeniu tekstu przetłumaczy przetłumaczony tekst na nową kopię oryginalnej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="16808-109">After the text is translated, you merge the translated text into a new copy of the original application.</span></span>
  
## <a name="create-a-sample-application"></a><span data-ttu-id="16808-110">Tworzenie przykładowej aplikacji</span><span class="sxs-lookup"><span data-stu-id="16808-110">Create a sample application</span></span>

<span data-ttu-id="16808-111">W tym kroku przygotowasz aplikację do lokalizacji.</span><span class="sxs-lookup"><span data-stu-id="16808-111">In this step, you prepare your app for localization.</span></span> <span data-ttu-id="16808-112">W przykładach Windows Presentation Foundation (WPF) dostarcza się próbkę HelloApp, która będzie używana w przykładach kodu w tej dyskusji.</span><span class="sxs-lookup"><span data-stu-id="16808-112">In the Windows Presentation Foundation (WPF) samples, a HelloApp sample is supplied that will be used for the code examples in this discussion.</span></span> <span data-ttu-id="16808-113">Jeśli chcesz użyć tego przykładu, Pobierz pliki Extensible Application Markup Language (XAML) z [przykładu narzędzia LocBaml](https://github.com/microsoft/WPF-Samples/tree/master/Tools/LocBaml).</span><span class="sxs-lookup"><span data-stu-id="16808-113">If you would like to use this sample, download the Extensible Application Markup Language (XAML) files from the [LocBaml Tool Sample](https://github.com/microsoft/WPF-Samples/tree/master/Tools/LocBaml).</span></span>  
  
1. <span data-ttu-id="16808-114">Utwórz aplikację w punkcie, w którym chcesz rozpocząć lokalizację.</span><span class="sxs-lookup"><span data-stu-id="16808-114">Develop your application to the point where you want to start localization.</span></span>  
  
2. <span data-ttu-id="16808-115">Określ język programistyczny w pliku projektu, tak aby MSBuild generował zestaw główny i zestaw satelicki (plik z rozszerzeniem. resources. dll) zawierający zasoby języka neutralnego.</span><span class="sxs-lookup"><span data-stu-id="16808-115">Specify the development language in the project file so that MSBuild generates a main assembly and a satellite assembly (a file with the .resources.dll extension) to contain the neutral language resources.</span></span> <span data-ttu-id="16808-116">Plik projektu w przykładzie HelloApp jest HelloApp. csproj.</span><span class="sxs-lookup"><span data-stu-id="16808-116">The project file in the HelloApp sample is HelloApp.csproj.</span></span> <span data-ttu-id="16808-117">W tym pliku znajdziesz następujący język programowania:</span><span class="sxs-lookup"><span data-stu-id="16808-117">In that file, you will find the development language identified as follows:</span></span>  
  
   `<UICulture>en-US</UICulture>`  
  
3. <span data-ttu-id="16808-118">Dodaj UID do plików XAML.</span><span class="sxs-lookup"><span data-stu-id="16808-118">Add Uids to your XAML files.</span></span> <span data-ttu-id="16808-119">Identyfikatory UID są używane do śledzenia zmian w plikach i identyfikowania elementów, które muszą być przetłumaczone.</span><span class="sxs-lookup"><span data-stu-id="16808-119">Uids are used to keep track of changes to files and to identify items that must be translated.</span></span> <span data-ttu-id="16808-120">Aby dodać UID do plików, uruchom polecenie `updateuid` w pliku projektu:</span><span class="sxs-lookup"><span data-stu-id="16808-120">To add Uids to your files, run `updateuid` on your project file:</span></span>  

   `msbuild -t:updateuid helloapp.csproj`

   <span data-ttu-id="16808-121">Aby sprawdzić, czy nie ma żadnych lub zduplikowanych identyfikatorów UID, uruchom polecenie `checkuid` :</span><span class="sxs-lookup"><span data-stu-id="16808-121">To verify that you have no missing or duplicate Uids, run `checkuid`:</span></span>  

   `msbuild -t:checkuid helloapp.csproj`

   <span data-ttu-id="16808-122">Po uruchomieniu `updateuid` pliki powinny zawierać identyfikatory UID.</span><span class="sxs-lookup"><span data-stu-id="16808-122">After running `updateuid`, your files should contain Uids.</span></span> <span data-ttu-id="16808-123">Na przykład w pliku *Pane1. XAML* HelloApp należy znaleźć następujące informacje:</span><span class="sxs-lookup"><span data-stu-id="16808-123">For example, in the *Pane1.xaml* file of HelloApp, you should find the following:</span></span>  

   ```xaml
   <StackPanel x:Uid="StackPanel_1">
     <TextBlock x:Uid="TextBlock_1">Hello World</TextBlock>
     <TextBlock x:Uid="TextBlock_2">Goodbye World</TextBlock>
   </StackPanel>
   ```

## <a name="create-the-neutral-language-resources-satellite-assembly"></a><span data-ttu-id="16808-124">Tworzenie zestawu satelickiego dla zasobów języka neutralnego</span><span class="sxs-lookup"><span data-stu-id="16808-124">Create the neutral-language resources satellite assembly</span></span>

<span data-ttu-id="16808-125">Po skonfigurowaniu aplikacji do generowania zestawu satelickiego dla zasobów języka neutralnego należy skompilować aplikację.</span><span class="sxs-lookup"><span data-stu-id="16808-125">After the application is configured to generate a neutral-language resources satellite assembly, you build the application.</span></span> <span data-ttu-id="16808-126">Spowoduje to wygenerowanie głównego zestawu aplikacji oraz zestawu satelickiego dla zasobów języka neutralnego, który jest wymagany przez LocBaml do lokalizacji.</span><span class="sxs-lookup"><span data-stu-id="16808-126">This generates the main application assembly as well as the neutral-language resources satellite assembly that's required by LocBaml for localization.</span></span>

<span data-ttu-id="16808-127">Aby skompilować aplikację:</span><span class="sxs-lookup"><span data-stu-id="16808-127">To build the application:</span></span>  
  
1. <span data-ttu-id="16808-128">Kompiluj HelloApp do tworzenia biblioteki dołączanej dynamicznie (DLL):</span><span class="sxs-lookup"><span data-stu-id="16808-128">Compile HelloApp to create a dynamic-link library (DLL):</span></span>  
  
   `msbuild helloapp.csproj`
  
2. <span data-ttu-id="16808-129">Nowo utworzony zestaw aplikacji głównej (HelloApp. exe) jest tworzony w następującym folderze: *C:\HelloApp\Bin\Debug*</span><span class="sxs-lookup"><span data-stu-id="16808-129">The newly created main application assembly, HelloApp.exe, is created in the following folder: *C:\HelloApp\Bin\Debug*</span></span>
  
3. <span data-ttu-id="16808-130">Nowo utworzony zestaw satelicki dla zasobów języka neutralnego, HelloApp. resources. dll, został utworzony w następującym folderze: *C:\HelloApp\Bin\Debug\en-US*</span><span class="sxs-lookup"><span data-stu-id="16808-130">The newly created neutral-language resources satellite assembly, HelloApp.resources.dll, is created in the following folder: *C:\HelloApp\Bin\Debug\en-US*</span></span>
  
## <a name="build-the-locbaml-tool"></a><span data-ttu-id="16808-131">Tworzenie narzędzia LocBaml</span><span class="sxs-lookup"><span data-stu-id="16808-131">Build the LocBaml tool</span></span>  
  
1. <span data-ttu-id="16808-132">Wszystkie pliki niezbędne do kompilowania LocBaml znajdują się w przykładach WPF.</span><span class="sxs-lookup"><span data-stu-id="16808-132">All the files necessary to build LocBaml are located in the WPF samples.</span></span> <span data-ttu-id="16808-133">Pobierz pliki C# z [przykładu narzędzia LocBaml](https://github.com/microsoft/WPF-Samples/tree/master/Tools/LocBaml).</span><span class="sxs-lookup"><span data-stu-id="16808-133">Download the C# files from the [LocBaml Tool Sample](https://github.com/microsoft/WPF-Samples/tree/master/Tools/LocBaml).</span></span>  
  
2. <span data-ttu-id="16808-134">W wierszu polecenia Uruchom plik projektu (LocBaml. csproj) w celu skompilowania narzędzia:</span><span class="sxs-lookup"><span data-stu-id="16808-134">From the command line, run the project file (locbaml.csproj) to build the tool:</span></span>  

   `msbuild locbaml.csproj`
  
3. <span data-ttu-id="16808-135">Przejdź do katalogu *bin\Release* , aby znaleźć nowo utworzony plik wykonywalny (LocBaml. exe).</span><span class="sxs-lookup"><span data-stu-id="16808-135">Go to the *Bin\Release* directory to find the newly created executable file (locbaml.exe).</span></span> <span data-ttu-id="16808-136">Przykład: *C:\LocBaml\Bin\Release\locbaml.exe*</span><span class="sxs-lookup"><span data-stu-id="16808-136">Example: *C:\LocBaml\Bin\Release\locbaml.exe*</span></span>
  
4. <span data-ttu-id="16808-137">Opcje, które można określić, gdy uruchamiasz LocBaml są następujące.</span><span class="sxs-lookup"><span data-stu-id="16808-137">The options that you can specify when you run LocBaml are as follows.</span></span>

   | <span data-ttu-id="16808-138">Opcja</span><span class="sxs-lookup"><span data-stu-id="16808-138">Option</span></span> | <span data-ttu-id="16808-139">Opis</span><span class="sxs-lookup"><span data-stu-id="16808-139">Description</span></span>|
   | - | - |
   | <span data-ttu-id="16808-140">`parse` lub `-p`</span><span class="sxs-lookup"><span data-stu-id="16808-140">`parse` or `-p`</span></span> | <span data-ttu-id="16808-141">Analizuje pliki BAML, zasoby lub biblioteki DLL w celu wygenerowania pliku CSV lub txt.</span><span class="sxs-lookup"><span data-stu-id="16808-141">Parses Baml, resources, or DLL files to generate a .csv or .txt file.</span></span> |
   | <span data-ttu-id="16808-142">`generate` lub `-g`</span><span class="sxs-lookup"><span data-stu-id="16808-142">`generate` or `-g`</span></span> | <span data-ttu-id="16808-143">Generuje zlokalizowany plik binarny przy użyciu przetłumaczonego pliku.</span><span class="sxs-lookup"><span data-stu-id="16808-143">Generates a localized binary file by using a translated file.</span></span> |
   | <span data-ttu-id="16808-144">`out`lub `-o` {*FileDirectory*]</span><span class="sxs-lookup"><span data-stu-id="16808-144">`out` or `-o` {*filedirectory*]</span></span> | <span data-ttu-id="16808-145">Nazwa pliku wyjściowego.</span><span class="sxs-lookup"><span data-stu-id="16808-145">Output file name.</span></span> |
   | <span data-ttu-id="16808-146">`culture`lub `-cul` {*Culture*]</span><span class="sxs-lookup"><span data-stu-id="16808-146">`culture` or `-cul` {*culture*]</span></span> | <span data-ttu-id="16808-147">Ustawienia regionalne zestawów wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="16808-147">Locale of output assemblies.</span></span> |
   | <span data-ttu-id="16808-148">`translation`lub `-trans` {*Translation. csv*]</span><span class="sxs-lookup"><span data-stu-id="16808-148">`translation` or `-trans` {*translation.csv*]</span></span> | <span data-ttu-id="16808-149">Przetłumaczony lub zlokalizowany plik.</span><span class="sxs-lookup"><span data-stu-id="16808-149">Translated or localized file.</span></span> |
   | <span data-ttu-id="16808-150">`asmpath`lub `-asmpath` {*FileDirectory*]</span><span class="sxs-lookup"><span data-stu-id="16808-150">`asmpath` or `-asmpath` {*filedirectory*]</span></span> | <span data-ttu-id="16808-151">Jeśli kod XAML zawiera niestandardowe kontrolki, należy podać `asmpath` do niestandardowego zestawu kontrolek.</span><span class="sxs-lookup"><span data-stu-id="16808-151">If your XAML code contains custom controls, you must supply the `asmpath` to the custom control assembly.</span></span> |
   | `nologo` | <span data-ttu-id="16808-152">Nie wyświetla logo ani informacji o prawach autorskich.</span><span class="sxs-lookup"><span data-stu-id="16808-152">Displays no logo or copyright information.</span></span> |
   | `verbose` | <span data-ttu-id="16808-153">Wyświetla informacje o trybie informacji pełnej.</span><span class="sxs-lookup"><span data-stu-id="16808-153">Displays verbose mode information.</span></span> |
  
   > [!NOTE]
   > <span data-ttu-id="16808-154">Jeśli potrzebujesz listy opcji, gdy korzystasz z narzędzia, wpisz `LocBaml.exe` i naciśnij klawisz **Enter**.</span><span class="sxs-lookup"><span data-stu-id="16808-154">If you need a list of the options when you are running the tool, enter `LocBaml.exe` and then press **Enter**.</span></span>
  
## <a name="use-locbaml-to-parse-a-file"></a><span data-ttu-id="16808-155">Analizowanie pliku przy użyciu LocBaml</span><span class="sxs-lookup"><span data-stu-id="16808-155">Use LocBaml to parse a file</span></span>

<span data-ttu-id="16808-156">Po utworzeniu narzędzia LocBaml można go użyć do przeanalizowania HelloApp. resources. dll w celu wyodrębnienia zawartości tekstowej, która ma zostać zlokalizowana.</span><span class="sxs-lookup"><span data-stu-id="16808-156">Now that you have created the LocBaml tool, you are ready to use it to parse HelloApp.resources.dll to extract the text content that will be localized.</span></span>  
  
1. <span data-ttu-id="16808-157">Skopiuj plik LocBaml. exe do folderu bin\Debug aplikacji, w którym został utworzony zestaw aplikacji głównej.</span><span class="sxs-lookup"><span data-stu-id="16808-157">Copy LocBaml.exe to your application's bin\debug folder, where the main application assembly was created.</span></span>  
  
2. <span data-ttu-id="16808-158">Aby przeanalizować plik zestawu satelickiego i zapisać dane wyjściowe jako plik CSV, użyj następującego polecenia:</span><span class="sxs-lookup"><span data-stu-id="16808-158">To parse the satellite assembly file and store the output as a .csv file, use the following command:</span></span>  
  
   `LocBaml.exe /parse HelloApp.resources.dll /out:Hello.csv`
  
   > [!NOTE]
   > <span data-ttu-id="16808-159">Jeśli plik wejściowy HelloApp. resources. dll nie znajduje się w tym samym katalogu, co LocBaml. exe Przenieś jeden z tych plików, tak aby oba pliki były w tym samym katalogu.</span><span class="sxs-lookup"><span data-stu-id="16808-159">If the input file, HelloApp.resources.dll, is not in the same directory as LocBaml.exe move one of the files so that both files are in the same directory.</span></span>  
  
3. <span data-ttu-id="16808-160">Po uruchomieniu LocBaml do analizowania plików dane wyjściowe składają się z siedmiu pól rozdzielonych przecinkami (pliki CSV) lub tabulatorami (pliki. txt).</span><span class="sxs-lookup"><span data-stu-id="16808-160">When you run LocBaml to parse files, the output consists of seven fields delimited by commas (.csv files) or tabs (.txt files).</span></span> <span data-ttu-id="16808-161">Poniżej przedstawiono przeanalizowany plik CSV dla HelloApp. resources. dll:</span><span class="sxs-lookup"><span data-stu-id="16808-161">The following shows the parsed .csv file for the HelloApp.resources.dll:</span></span>

   | |
   |-|
   |<span data-ttu-id="16808-162">HelloApp. g. pl-US. Resources: window1. BAML, Stack1: System. Windows. Controls. StackPanel. $Content, IGNORE, FALSE, FALSE,, #Text1; #Text2;</span><span class="sxs-lookup"><span data-stu-id="16808-162">HelloApp.g.en-US.resources:window1.baml,Stack1:System.Windows.Controls.StackPanel.$Content,Ignore,FALSE, FALSE,,#Text1;#Text2;</span></span>|
   |<span data-ttu-id="16808-163">HelloApp. g. pl-US. Resources: window1. BAML, Tekst1: System. Windows. Controls. TextBlock. $Content, None, TRUE, TRUE,, Hello world</span><span class="sxs-lookup"><span data-stu-id="16808-163">HelloApp.g.en-US.resources:window1.baml,Text1:System.Windows.Controls.TextBlock.$Content,None,TRUE, TRUE,,Hello World</span></span>|
   |<span data-ttu-id="16808-164">HelloApp. g. pl-US. Resources: window1. BAML, Tekst2: System. Windows. Controls. TextBlock. $Content, None, TRUE, TRUE,, pożegnanie świata</span><span class="sxs-lookup"><span data-stu-id="16808-164">HelloApp.g.en-US.resources:window1.baml,Text2:System.Windows.Controls.TextBlock.$Content,None,TRUE, TRUE,,Goodbye World</span></span>|

   <span data-ttu-id="16808-165">Siedem pól są następujące:</span><span class="sxs-lookup"><span data-stu-id="16808-165">The seven fields are:</span></span>  
  
   - <span data-ttu-id="16808-166">**Nazwa BAML**.</span><span class="sxs-lookup"><span data-stu-id="16808-166">**BAML Name**.</span></span> <span data-ttu-id="16808-167">Nazwa zasobu BAML w odniesieniu do zestawu satelickiego dla języka źródłowego.</span><span class="sxs-lookup"><span data-stu-id="16808-167">The name of the BAML resource with respect to the source language satellite assembly.</span></span>  
  
   - <span data-ttu-id="16808-168">**Klucz zasobu**.</span><span class="sxs-lookup"><span data-stu-id="16808-168">**Resource Key**.</span></span> <span data-ttu-id="16808-169">Zlokalizowany identyfikator zasobu.</span><span class="sxs-lookup"><span data-stu-id="16808-169">The localized resource identifier.</span></span>  
  
   - <span data-ttu-id="16808-170">**Kategoria**.</span><span class="sxs-lookup"><span data-stu-id="16808-170">**Category**.</span></span> <span data-ttu-id="16808-171">Typ wartości.</span><span class="sxs-lookup"><span data-stu-id="16808-171">The value type.</span></span> <span data-ttu-id="16808-172">Zobacz [atrybuty lokalizacji i komentarze](localization-attributes-and-comments.md).</span><span class="sxs-lookup"><span data-stu-id="16808-172">See [Localization Attributes and Comments](localization-attributes-and-comments.md).</span></span>  
  
   - <span data-ttu-id="16808-173">**Czytelność**.</span><span class="sxs-lookup"><span data-stu-id="16808-173">**Readability**.</span></span> <span data-ttu-id="16808-174">Określa, czy wartość może być odczytywana przez lokalizatora.</span><span class="sxs-lookup"><span data-stu-id="16808-174">Whether the value can be read by a localizer.</span></span> <span data-ttu-id="16808-175">Zobacz [atrybuty lokalizacji i komentarze](localization-attributes-and-comments.md).</span><span class="sxs-lookup"><span data-stu-id="16808-175">See [Localization Attributes and Comments](localization-attributes-and-comments.md).</span></span>  
  
   - <span data-ttu-id="16808-176">**Modifiability**.</span><span class="sxs-lookup"><span data-stu-id="16808-176">**Modifiability**.</span></span> <span data-ttu-id="16808-177">Czy wartość może być modyfikowana przez lokalizatora.</span><span class="sxs-lookup"><span data-stu-id="16808-177">Whether the value can be modified by a localizer.</span></span> <span data-ttu-id="16808-178">Zobacz [atrybuty lokalizacji i komentarze](localization-attributes-and-comments.md).</span><span class="sxs-lookup"><span data-stu-id="16808-178">See [Localization Attributes and Comments](localization-attributes-and-comments.md).</span></span>  
  
   - <span data-ttu-id="16808-179">**Komentarze**.</span><span class="sxs-lookup"><span data-stu-id="16808-179">**Comments**.</span></span> <span data-ttu-id="16808-180">Dodatkowy opis wartości, aby pomóc w ustaleniu, jak jest lokalizowana wartość.</span><span class="sxs-lookup"><span data-stu-id="16808-180">Additional description of the value to help determine how a value is localized.</span></span> <span data-ttu-id="16808-181">Zobacz [atrybuty lokalizacji i komentarze](localization-attributes-and-comments.md).</span><span class="sxs-lookup"><span data-stu-id="16808-181">See [Localization Attributes and Comments](localization-attributes-and-comments.md).</span></span>  
  
   - <span data-ttu-id="16808-182">**Wartość**.</span><span class="sxs-lookup"><span data-stu-id="16808-182">**Value**.</span></span> <span data-ttu-id="16808-183">Wartość tekstowa do przetłumaczenia na pożądaną kulturę.</span><span class="sxs-lookup"><span data-stu-id="16808-183">The text value to translate to the desired culture.</span></span>  
  
   <span data-ttu-id="16808-184">W poniższej tabeli przedstawiono, w jaki sposób te pola są mapowane na wartości rozdzielane pliku CSV:</span><span class="sxs-lookup"><span data-stu-id="16808-184">The following table shows how these fields map to the delimited values of the .csv file:</span></span>  
  
   |<span data-ttu-id="16808-185">Nazwa BAML</span><span class="sxs-lookup"><span data-stu-id="16808-185">BAML name</span></span>|<span data-ttu-id="16808-186">Klucz zasobu</span><span class="sxs-lookup"><span data-stu-id="16808-186">Resource key</span></span>|<span data-ttu-id="16808-187">Kategoria</span><span class="sxs-lookup"><span data-stu-id="16808-187">Category</span></span>|<span data-ttu-id="16808-188">Czytelność</span><span class="sxs-lookup"><span data-stu-id="16808-188">Readability</span></span>|<span data-ttu-id="16808-189">Modifiability</span><span class="sxs-lookup"><span data-stu-id="16808-189">Modifiability</span></span>|<span data-ttu-id="16808-190">Komentarze</span><span class="sxs-lookup"><span data-stu-id="16808-190">Comments</span></span>|<span data-ttu-id="16808-191">Wartość</span><span class="sxs-lookup"><span data-stu-id="16808-191">Value</span></span>|  
   |---------------|------------------|--------------|-----------------|-------------------|--------------|-----------|
   |<span data-ttu-id="16808-192">HelloApp. g. pl-US. Resources: window1. BAML</span><span class="sxs-lookup"><span data-stu-id="16808-192">HelloApp.g.en-US.resources:window1.baml</span></span>|<span data-ttu-id="16808-193">Stack1: System. Windows. Controls. StackPanel. $Content</span><span class="sxs-lookup"><span data-stu-id="16808-193">Stack1:System.Windows.Controls.StackPanel.$Content</span></span>|<span data-ttu-id="16808-194">Zignoruj</span><span class="sxs-lookup"><span data-stu-id="16808-194">Ignore</span></span>|<span data-ttu-id="16808-195">FALSE</span><span class="sxs-lookup"><span data-stu-id="16808-195">FALSE</span></span>|<span data-ttu-id="16808-196">FALSE</span><span class="sxs-lookup"><span data-stu-id="16808-196">FALSE</span></span>||<span data-ttu-id="16808-197">#Text1; #Text2</span><span class="sxs-lookup"><span data-stu-id="16808-197">#Text1;#Text2</span></span>|
   |<span data-ttu-id="16808-198">HelloApp. g. pl-US. Resources: window1. BAML</span><span class="sxs-lookup"><span data-stu-id="16808-198">HelloApp.g.en-US.resources:window1.baml</span></span>|<span data-ttu-id="16808-199">Tekst1: System. Windows. Controls. TextBlock. $Content</span><span class="sxs-lookup"><span data-stu-id="16808-199">Text1:System.Windows.Controls.TextBlock.$Content</span></span>|<span data-ttu-id="16808-200">Brak</span><span class="sxs-lookup"><span data-stu-id="16808-200">None</span></span>|<span data-ttu-id="16808-201">TRUE</span><span class="sxs-lookup"><span data-stu-id="16808-201">TRUE</span></span>|<span data-ttu-id="16808-202">TRUE</span><span class="sxs-lookup"><span data-stu-id="16808-202">TRUE</span></span>||<span data-ttu-id="16808-203">Witaj, świecie</span><span class="sxs-lookup"><span data-stu-id="16808-203">Hello World</span></span>|
   |<span data-ttu-id="16808-204">HelloApp. g. pl-US. Resources: window1. BAML</span><span class="sxs-lookup"><span data-stu-id="16808-204">HelloApp.g.en-US.resources:window1.baml</span></span>|<span data-ttu-id="16808-205">Tekst2: System. Windows. Controls. TextBlock. $Content</span><span class="sxs-lookup"><span data-stu-id="16808-205">Text2:System.Windows.Controls.TextBlock.$Content</span></span>|<span data-ttu-id="16808-206">Brak</span><span class="sxs-lookup"><span data-stu-id="16808-206">None</span></span>|<span data-ttu-id="16808-207">TRUE</span><span class="sxs-lookup"><span data-stu-id="16808-207">TRUE</span></span>|<span data-ttu-id="16808-208">TRUE</span><span class="sxs-lookup"><span data-stu-id="16808-208">TRUE</span></span>||<span data-ttu-id="16808-209">Na świecie</span><span class="sxs-lookup"><span data-stu-id="16808-209">Goodbye World</span></span>|
  
   <span data-ttu-id="16808-210">Zwróć uwagę, że wszystkie wartości pola **Komentarze** nie zawierają wartości; Jeśli pole nie ma wartości, jest puste.</span><span class="sxs-lookup"><span data-stu-id="16808-210">Notice that all the values for the **Comments** field contain no values; if a field doesn't have a value, it is empty.</span></span> <span data-ttu-id="16808-211">Zauważ również, że element w pierwszym wierszu nie jest możliwy do odczytania ani do zmodyfikowania, a jego wartość **kategorii** jest ignorowana, a wszystko wskazuje, że wartość nie jest lokalizowalna.</span><span class="sxs-lookup"><span data-stu-id="16808-211">Also notice that the item in the first row is neither readable nor modifiable, and has "Ignore" as its **Category** value, all of which indicates that the value is not localizable.</span></span>  
  
4. <span data-ttu-id="16808-212">Aby ułatwić odnajdywanie lokalizowalnych elementów w przeanalizowanych plikach, szczególnie w dużych plikach, można sortować lub filtrować elementy według **kategorii**, **czytelności**i **modifiability**.</span><span class="sxs-lookup"><span data-stu-id="16808-212">To facilitate discovery of localizable items in parsed files, particularly in large files, you can sort or filter the items by **Category**, **Readability**, and **Modifiability**.</span></span> <span data-ttu-id="16808-213">Na przykład można odfiltrować niemodyfikowalne i niemodyfikowane wartości.</span><span class="sxs-lookup"><span data-stu-id="16808-213">For example, you can filter out unreadable and unmodifiable values.</span></span>  
  
## <a name="translate-the-localizable-content"></a><span data-ttu-id="16808-214">Tłumaczenie lokalizowalnej zawartości</span><span class="sxs-lookup"><span data-stu-id="16808-214">Translate the localizable content</span></span>

<span data-ttu-id="16808-215">Użyj dowolnego dostępnego narzędzia, aby przetłumaczyć wyodrębnioną zawartość.</span><span class="sxs-lookup"><span data-stu-id="16808-215">Use any tool that you have available to translate the extracted content.</span></span> <span data-ttu-id="16808-216">Dobrym sposobem jest zapisanie zasobów do pliku CSV i wyświetlenie ich w programie Microsoft Excel, co spowoduje zmianę tłumaczenia na ostatnią kolumnę (wartość).</span><span class="sxs-lookup"><span data-stu-id="16808-216">A good way to do this is to write the resources to a .csv file and view them in Microsoft Excel, making translation changes to the last column (value).</span></span>  
  
## <a name="use-locbaml-to-generate-a-new-resourcesdll-file"></a><span data-ttu-id="16808-217">Użyj LocBaml, aby wygenerować nowy plik resources. dll</span><span class="sxs-lookup"><span data-stu-id="16808-217">Use LocBaml to generate a new .resources.dll file</span></span>

<span data-ttu-id="16808-218">Zawartość zidentyfikowana przez analizowanie HelloApp. resources. dll z LocBaml została przetłumaczona i należy ją scalić z powrotem do oryginalnej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="16808-218">The content that was identified by parsing HelloApp.resources.dll with LocBaml has been translated and must be merged back into the original application.</span></span> <span data-ttu-id="16808-219">Użyj `generate` opcji lub, `-g` Aby wygenerować nowy plik resources. dll.</span><span class="sxs-lookup"><span data-stu-id="16808-219">Use the `generate` or `-g` option to generate a new .resources.dll file.</span></span>  
  
1. <span data-ttu-id="16808-220">Użyj następującej składni, aby wygenerować nowy plik HelloApp. resources. dll.</span><span class="sxs-lookup"><span data-stu-id="16808-220">Use the following syntax to generate a new HelloApp.resources.dll file.</span></span> <span data-ttu-id="16808-221">Oznacz kulturę jako en-US (/CUL: en-US).</span><span class="sxs-lookup"><span data-stu-id="16808-221">Mark the culture as en-US (/cul:en-US).</span></span>  
  
   `LocBaml.exe /generate HelloApp.resources.dll /trans:Hello.csv /out:c:\ /cul:en-US`  

   > [!NOTE]
   > <span data-ttu-id="16808-222">Jeśli plik wejściowy, Hello. csv, nie znajduje się w tym samym katalogu co plik wykonywalny, LocBaml. exe, Przenieś jeden z tych plików, tak aby oba pliki były w tym samym katalogu.</span><span class="sxs-lookup"><span data-stu-id="16808-222">If the input file, Hello.csv, is not in the same directory as the executable, LocBaml.exe, move one of the files so that both files are in the same directory.</span></span>  
  
2. <span data-ttu-id="16808-223">Zastąp stary plik *HelloApp. resources. dll* w katalogu *C:\HelloApp\Bin\Debug\en-US\HelloApp.resources.dll* nowo utworzonym plikiem *HelloApp. resources. dll* .</span><span class="sxs-lookup"><span data-stu-id="16808-223">Replace the old *HelloApp.resources.dll* file in the *C:\HelloApp\Bin\Debug\en-US\HelloApp.resources.dll* directory with your newly created *HelloApp.resources.dll* file.</span></span>  
  
3. <span data-ttu-id="16808-224">"Hello world" i "Pożegnanie świata" powinny teraz zostać przetłumaczone w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="16808-224">"Hello World" and "Goodbye World" should now be translated in your application.</span></span>  
  
4. <span data-ttu-id="16808-225">Aby przetłumaczyć na inną kulturę, należy użyć kultury języka, do którego jest przeprowadzana translacja.</span><span class="sxs-lookup"><span data-stu-id="16808-225">To translate to a different culture, use the culture of the language that you are translating to.</span></span> <span data-ttu-id="16808-226">Poniższy przykład pokazuje, jak przetłumaczyć na francuski — kanadyjski:</span><span class="sxs-lookup"><span data-stu-id="16808-226">The following example shows how to translate to French-Canadian:</span></span>  
  
   `LocBaml.exe /generate HelloApp.resources.dll /trans:Hellofr-CA.csv /out:c:\ /cul:fr-CA`  
  
5. <span data-ttu-id="16808-227">W tym samym zestawie, w którym znajduje się główny zestaw aplikacji, Utwórz nowy folder specyficzny dla kultury, który ma być nowym zestawem satelickim.</span><span class="sxs-lookup"><span data-stu-id="16808-227">In the same assembly as the main application assembly, create a new culture-specific folder to house the new satellite assembly.</span></span> <span data-ttu-id="16808-228">W języku francuskim — kanadyjskim folderem będzie fr-CA.</span><span class="sxs-lookup"><span data-stu-id="16808-228">For French-Canadian, the folder would be fr-CA.</span></span>  
  
6. <span data-ttu-id="16808-229">Skopiuj wygenerowany zestaw satelicki do nowego folderu.</span><span class="sxs-lookup"><span data-stu-id="16808-229">Copy the generated satellite assembly to the new folder.</span></span>  
  
7. <span data-ttu-id="16808-230">Aby przetestować nowy zestaw satelicki, należy zmienić kulturę, w której zostanie uruchomiona aplikacja.</span><span class="sxs-lookup"><span data-stu-id="16808-230">To test the new satellite assembly, you need to change the culture under which your application will run.</span></span> <span data-ttu-id="16808-231">Można to zrobić na jeden z dwóch sposobów:</span><span class="sxs-lookup"><span data-stu-id="16808-231">You can do this in one of two ways:</span></span>  
  
   - <span data-ttu-id="16808-232">Zmień ustawienia regionalne systemu operacyjnego.</span><span class="sxs-lookup"><span data-stu-id="16808-232">Change your operating system's regional settings.</span></span>
  
   - <span data-ttu-id="16808-233">W aplikacji Dodaj następujący kod do App.xaml.cs:</span><span class="sxs-lookup"><span data-stu-id="16808-233">In your application, add the following code to App.xaml.cs:</span></span>  
  
     [!code-xaml[LocBamlChangeCultureSnippets#LocBamlChangeCultureMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/LocBamlChangeCultureSnippets/CSharp/App.xaml#locbamlchangeculturemarkup)]
     [!code-csharp[LocBamlChangeCultureSnippets#LocBamlChangeCultureCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/LocBamlChangeCultureSnippets/CSharp/App.xaml.cs#locbamlchangeculturecodebehind)]
     [!code-vb[LocBamlChangeCultureSnippets#LocBamlChangeCultureCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/LocBamlChangeCultureSnippets/VisualBasic/Application.xaml.vb#locbamlchangeculturecodebehind)]  
  
## <a name="tips-for-using-locbaml"></a><span data-ttu-id="16808-234">Wskazówki dotyczące używania LocBaml</span><span class="sxs-lookup"><span data-stu-id="16808-234">Tips for Using LocBaml</span></span>  
  
- <span data-ttu-id="16808-235">Wszystkie zestawy zależne, które definiują niestandardowe kontrolki, muszą zostać skopiowane do katalogu lokalnego LocBaml lub zainstalowane w pamięci podręcznej GAC.</span><span class="sxs-lookup"><span data-stu-id="16808-235">All dependent assemblies that define custom controls must be copied into the local directory of LocBaml or installed into the GAC.</span></span> <span data-ttu-id="16808-236">Jest to konieczne, ponieważ interfejs API lokalizacji musi mieć dostęp do zestawów zależnych, gdy odczytuje plik binarny XAML (BAML).</span><span class="sxs-lookup"><span data-stu-id="16808-236">This is necessary because the localization API must have access to the dependent assemblies when it reads the binary XAML (BAML).</span></span>  
  
- <span data-ttu-id="16808-237">Jeśli główny zestaw jest podpisany, wygenerowana Biblioteka DLL zasobów musi być również podpisana, aby można było ją załadować.</span><span class="sxs-lookup"><span data-stu-id="16808-237">If the main assembly is signed, the generated resource DLL must also be signed in order for it to be loaded.</span></span>  
  
- <span data-ttu-id="16808-238">Wersja zlokalizowanej biblioteki DLL zasobów musi być synchronizowana z zestawem głównym.</span><span class="sxs-lookup"><span data-stu-id="16808-238">The version of the localized resource DLL needs to be synchronized with the main assembly.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="16808-239">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="16808-239">See also</span></span>

- [<span data-ttu-id="16808-240">Globalizacja dla WPF</span><span class="sxs-lookup"><span data-stu-id="16808-240">Globalization for WPF</span></span>](globalization-for-wpf.md)
- [<span data-ttu-id="16808-241">Przegląd Użyj automatycznego układu</span><span class="sxs-lookup"><span data-stu-id="16808-241">Use Automatic Layout Overview</span></span>](use-automatic-layout-overview.md)
