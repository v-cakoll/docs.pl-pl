---
title: Jak lokalizować aplikację
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- localization [WPF], applications
- LocBaml tool [WPF]
- applications [WPF], localizing
ms.assetid: 5001227e-9326-48a4-9dcd-ba1b89ee6653
ms.openlocfilehash: f2e7e5e8879e89806cfd457a1af80f51b91871cb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174215"
---
# <a name="how-to-localize-an-application"></a><span data-ttu-id="3495a-102">Jak lokalizować aplikację</span><span class="sxs-lookup"><span data-stu-id="3495a-102">How to: Localize an Application</span></span>
<span data-ttu-id="3495a-103">W tym samouczku wyjaśniono, jak utworzyć zlokalizowaną aplikację przy użyciu narzędzia LocBaml.</span><span class="sxs-lookup"><span data-stu-id="3495a-103">This tutorial explains how to create a localized application by using the LocBaml tool.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3495a-104">Narzędzie LocBaml nie jest aplikacją gotową do produkcji.</span><span class="sxs-lookup"><span data-stu-id="3495a-104">The LocBaml tool is not a production-ready application.</span></span> <span data-ttu-id="3495a-105">Jest on przedstawiony jako przykład, który używa niektórych interfejsów API lokalizacji i ilustruje, jak można napisać narzędzie lokalizacji.</span><span class="sxs-lookup"><span data-stu-id="3495a-105">It is presented as a sample that uses some of the localization APIs and illustrates how you might write a localization tool.</span></span>  
  
<a name="Introduction"></a>
## <a name="overview"></a><span data-ttu-id="3495a-106">Omówienie</span><span class="sxs-lookup"><span data-stu-id="3495a-106">Overview</span></span>  
 <span data-ttu-id="3495a-107">Ta dyskusja zawiera podejście krok po kroku do lokalizowania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="3495a-107">This discussion gives you a step-by-step approach to localizing an application.</span></span> <span data-ttu-id="3495a-108">Najpierw przygotujesz aplikację, aby można było wyodrębnić tekst, który zostanie przetłumaczony.</span><span class="sxs-lookup"><span data-stu-id="3495a-108">First, you will prepare your application so that the text that will be translated can be extracted.</span></span> <span data-ttu-id="3495a-109">Po przetłumaczeniu tekstu zostanie scalić przetłumaczony tekst na nową kopię oryginalnej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="3495a-109">After the text is translated, you will merge the translated text into a new copy of the original application.</span></span>  
  
<a name="Requirements"></a>
## <a name="requirements"></a><span data-ttu-id="3495a-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="3495a-110">Requirements</span></span>  
 <span data-ttu-id="3495a-111">W trakcie tej dyskusji użyjesz aparatu kompilacji firmy Microsoft (MSBuild), który jest kompilatorem uruchamianym z wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="3495a-111">Over the course of this discussion, you will use Microsoft build engine (MSBuild), which is a compiler that runs from the command line.</span></span>  
  
 <span data-ttu-id="3495a-112">Ponadto zostaniesz poinstruowany, aby użyć pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="3495a-112">Also, you will be instructed to use a project file.</span></span> <span data-ttu-id="3495a-113">Aby uzyskać instrukcje dotyczące używania plików MSBuild i projektu, zobacz [Tworzenie i wdrażanie](../app-development/building-and-deploying-wpf-applications.md).</span><span class="sxs-lookup"><span data-stu-id="3495a-113">For instructions on how to use MSBuild and project files, see [Build and Deploy](../app-development/building-and-deploying-wpf-applications.md).</span></span>  
  
 <span data-ttu-id="3495a-114">Wszystkie przykłady w tej dyskusji używają en-US (English-US) jako kultury.</span><span class="sxs-lookup"><span data-stu-id="3495a-114">All the examples in this discussion use en-US (English-US) as the culture.</span></span> <span data-ttu-id="3495a-115">Dzięki temu można pracować przez kroki przykładów bez instalowania innego języka.</span><span class="sxs-lookup"><span data-stu-id="3495a-115">This enables you to work through the steps of the examples without installing a different language.</span></span>  
  
<a name="create_sample_app"></a>
## <a name="create-a-sample-application"></a><span data-ttu-id="3495a-116">Tworzenie przykładowej aplikacji</span><span class="sxs-lookup"><span data-stu-id="3495a-116">Create a Sample Application</span></span>  
 <span data-ttu-id="3495a-117">W tym kroku przygotujesz aplikację do lokalizacji.</span><span class="sxs-lookup"><span data-stu-id="3495a-117">In this step, you will prepare your application for localization.</span></span> <span data-ttu-id="3495a-118">W [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] przykładach podano przykład HelloApp, który będzie używany dla przykładów kodu w tej dyskusji.</span><span class="sxs-lookup"><span data-stu-id="3495a-118">In the [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] samples, a HelloApp sample is supplied that will be used for the code examples in this discussion.</span></span> <span data-ttu-id="3495a-119">Jeśli chcesz użyć tego przykładu, [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] pobierz pliki z [przykładu narzędzia LocBaml](https://github.com/microsoft/WPF-Samples/tree/master/Tools/LocBaml).</span><span class="sxs-lookup"><span data-stu-id="3495a-119">If you would like to use this sample, download the [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] files from the [LocBaml Tool Sample](https://github.com/microsoft/WPF-Samples/tree/master/Tools/LocBaml).</span></span>  
  
1. <span data-ttu-id="3495a-120">Tworzenie aplikacji do punktu, w którym chcesz rozpocząć lokalizację.</span><span class="sxs-lookup"><span data-stu-id="3495a-120">Develop your application to the point where you want to start localization.</span></span>  
  
2. <span data-ttu-id="3495a-121">Określ język rozwoju w pliku projektu, tak aby MSBuild wygenerował główny zestaw i zestaw satelicki (plik z rozszerzeniem .resources.dll) zawierający zasoby języka neutralnego.</span><span class="sxs-lookup"><span data-stu-id="3495a-121">Specify the development language in the project file so that MSBuild generates a main assembly and a satellite assembly (a file with the .resources.dll extension) to contain the neutral language resources.</span></span> <span data-ttu-id="3495a-122">Plik projektu w przykładzie HelloApp jest HelloApp.csproj.</span><span class="sxs-lookup"><span data-stu-id="3495a-122">The project file in the HelloApp sample is HelloApp.csproj.</span></span> <span data-ttu-id="3495a-123">W tym pliku znajdziesz język programowania zidentyfikowany w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="3495a-123">In that file, you will find the development language identified as follows:</span></span>  
  
     `<UICulture>en-US</UICulture>`  
  
3. <span data-ttu-id="3495a-124">Dodaj Uids [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] do plików.</span><span class="sxs-lookup"><span data-stu-id="3495a-124">Add Uids to your [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] files.</span></span> <span data-ttu-id="3495a-125">Uids są używane do śledzenia zmian w plikach i do identyfikowania elementów, które muszą być przetłumaczone.</span><span class="sxs-lookup"><span data-stu-id="3495a-125">Uids are used to keep track of changes to files and to identify items that must be translated.</span></span> <span data-ttu-id="3495a-126">Aby dodać Uids do plików, uruchom **updateuid** w pliku projektu:</span><span class="sxs-lookup"><span data-stu-id="3495a-126">To add Uids to your files, run **updateuid** on your project file:</span></span>  
  
     <span data-ttu-id="3495a-127">**msbuild -t:updateuid helloapp.csproj**</span><span class="sxs-lookup"><span data-stu-id="3495a-127">**msbuild -t:updateuid helloapp.csproj**</span></span>  
  
     <span data-ttu-id="3495a-128">Aby sprawdzić, czy nie brakuje lub duplikuje Uids, uruchom **checkuid:**</span><span class="sxs-lookup"><span data-stu-id="3495a-128">To verify that you have no missing or duplicate Uids, run **checkuid**:</span></span>  
  
     <span data-ttu-id="3495a-129">**msbuild -t:checkuid helloapp.csproj**</span><span class="sxs-lookup"><span data-stu-id="3495a-129">**msbuild -t:checkuid helloapp.csproj**</span></span>  
  
     <span data-ttu-id="3495a-130">Po uruchomieniu **updateuid,** pliki powinny zawierać Uids.</span><span class="sxs-lookup"><span data-stu-id="3495a-130">After running **updateuid**, your files should contain Uids.</span></span> <span data-ttu-id="3495a-131">Na przykład w pliku Pane1.xaml helloapp, należy znaleźć następujące:</span><span class="sxs-lookup"><span data-stu-id="3495a-131">For example, in the Pane1.xaml file of HelloApp, you should find the following:</span></span>  
  
     `<StackPanel x:Uid="StackPanel_1">`  
  
     `<TextBlock x:Uid="TextBlock_1">Hello World</TextBlock>`  
  
     `<TextBlock x:Uid="TextBlock_2">Goodbye World</TextBlock>`  
  
     `</StackPanel>`  
  
<a name="create_dll"></a>
## <a name="create-the-neutral-language-resources-satellite-assembly"></a><span data-ttu-id="3495a-132">Tworzenie zestawu satelitarnego zasobów języka neutralnego</span><span class="sxs-lookup"><span data-stu-id="3495a-132">Create the Neutral Language Resources Satellite Assembly</span></span>  
 <span data-ttu-id="3495a-133">Po skonfigurowaniu aplikacji do generowania zestawu satelitów zasobów języka neutralnego, należy utworzyć aplikację.</span><span class="sxs-lookup"><span data-stu-id="3495a-133">After the application is configured to generate a neutral language resources satellite assembly, you build the application.</span></span> <span data-ttu-id="3495a-134">Generuje to główny zestaw aplikacji, a także zestaw satelicki zasobów języka neutralnego, który jest wymagany przez LocBaml do lokalizacji.</span><span class="sxs-lookup"><span data-stu-id="3495a-134">This generates the main application assembly, as well as the neutral language resources satellite assembly that is required by LocBaml for localization.</span></span> <span data-ttu-id="3495a-135">Aby skompilować aplikację:</span><span class="sxs-lookup"><span data-stu-id="3495a-135">To build the application:</span></span>  
  
1. <span data-ttu-id="3495a-136">Skompiluj HelloApp, aby utworzyć bibliotekę dynamicznego łącza (DLL):</span><span class="sxs-lookup"><span data-stu-id="3495a-136">Compile HelloApp to create a dynamic-link library (DLL):</span></span>  
  
     <span data-ttu-id="3495a-137">**msbuild helloapp.csproj**</span><span class="sxs-lookup"><span data-stu-id="3495a-137">**msbuild helloapp.csproj**</span></span>  
  
2. <span data-ttu-id="3495a-138">Nowo utworzony główny zestaw aplikacji, HelloApp.exe, jest tworzony w następującym folderze:</span><span class="sxs-lookup"><span data-stu-id="3495a-138">The newly created main application assembly, HelloApp.exe, is created in the following folder:</span></span>  
  
     `C:\HelloApp\Bin\Debug\`  
  
3. <span data-ttu-id="3495a-139">Nowo utworzony zestaw satelicki zasobów języka neutralnego, HelloApp.resources.dll, jest tworzony w następującym folderze:</span><span class="sxs-lookup"><span data-stu-id="3495a-139">The newly created neutral language resources satellite assembly, HelloApp.resources.dll, is created in the following folder:</span></span>  
  
     `C:\HelloApp\Bin\Debug\en-US\`  
  
<a name="build_locbaml"></a>
## <a name="build-the-locbaml-tool"></a><span data-ttu-id="3495a-140">Tworzenie narzędzia LocBaml</span><span class="sxs-lookup"><span data-stu-id="3495a-140">Build the LocBaml Tool</span></span>  
  
1. <span data-ttu-id="3495a-141">Wszystkie pliki niezbędne do zbudowania LocBaml znajdują się w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] przykładach.</span><span class="sxs-lookup"><span data-stu-id="3495a-141">All the files necessary to build LocBaml are located in the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] samples.</span></span> <span data-ttu-id="3495a-142">Pobierz pliki języka C# z [przykładowego narzędzia LocBaml](https://github.com/microsoft/WPF-Samples/tree/master/Tools/LocBaml).</span><span class="sxs-lookup"><span data-stu-id="3495a-142">Download the C# files from the [LocBaml Tool Sample](https://github.com/microsoft/WPF-Samples/tree/master/Tools/LocBaml).</span></span>  
  
2. <span data-ttu-id="3495a-143">W wierszu polecenia uruchom plik projektu (locbaml.csproj), aby utworzyć narzędzie:</span><span class="sxs-lookup"><span data-stu-id="3495a-143">From the command line, run the project file (locbaml.csproj) to build the tool:</span></span>  
  
     <span data-ttu-id="3495a-144">**msbuild locbaml.csproj**</span><span class="sxs-lookup"><span data-stu-id="3495a-144">**msbuild locbaml.csproj**</span></span>  
  
3. <span data-ttu-id="3495a-145">Przejdź do katalogu Bin\Release, aby znaleźć nowo utworzony plik wykonywalny (locbaml.exe).</span><span class="sxs-lookup"><span data-stu-id="3495a-145">Go to the Bin\Release directory to find the newly created executable file (locbaml.exe).</span></span> <span data-ttu-id="3495a-146">Przykład:C:\LocBaml\Bin\Release\locbaml.exe.</span><span class="sxs-lookup"><span data-stu-id="3495a-146">Example:C:\LocBaml\Bin\Release\locbaml.exe.</span></span>  
  
4. <span data-ttu-id="3495a-147">Opcje, które można określić po uruchomieniu LocBaml są następujące:</span><span class="sxs-lookup"><span data-stu-id="3495a-147">The options that you can specify when you run LocBaml are as follows:</span></span>  
  
    - <span data-ttu-id="3495a-148">**analizuj** lub **-p:** analizuje pliki Baml, zasoby lub biblioteki DLL w celu wygenerowania pliku csv lub txt.</span><span class="sxs-lookup"><span data-stu-id="3495a-148">**parse** or **-p:** Parses Baml, resources, or DLL files to generate a .csv or .txt file.</span></span>  
  
    - <span data-ttu-id="3495a-149">**generate** or **-g:** Generuje zlokalizowany plik binarny przy użyciu przetłumaczonego pliku.</span><span class="sxs-lookup"><span data-stu-id="3495a-149">**generate** or **-g:** Generates a localized binary file by using a translated file.</span></span>  
  
    - <span data-ttu-id="3495a-150">**out** lub **-o** {*filedirector*] **:** Nazwa pliku wyjściowego.</span><span class="sxs-lookup"><span data-stu-id="3495a-150">**out** or **-o** {*filedirectory*] **:** Output file name.</span></span>  
  
    - <span data-ttu-id="3495a-151">**culture** or **-cul** {*culture*] **:** Ustawienia regionalne zestawów wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="3495a-151">**culture** or **-cul** {*culture*] **:** Locale of output assemblies.</span></span>  
  
    - <span data-ttu-id="3495a-152">**translation** or **-trans** {*translation.csv*] **:** Przetłumaczony lub zlokalizowany plik.</span><span class="sxs-lookup"><span data-stu-id="3495a-152">**translation** or **-trans** {*translation.csv*] **:** Translated or localized file.</span></span>  
  
    - <span data-ttu-id="3495a-153">**asmpath** lub **-asmpath:** {*filedirector*] **:** Jeśli [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] kod zawiera formanty niestandardowe, należy podać **asmpath** do zestawu formantu niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="3495a-153">**asmpath** or **-asmpath:** {*filedirectory*] **:** If your [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] code contains custom controls, you must supply the **asmpath** to the custom control assembly.</span></span>  
  
    - <span data-ttu-id="3495a-154">**nologo:** Nie wyświetla żadnych informacji o logo ani prawach autorskich.</span><span class="sxs-lookup"><span data-stu-id="3495a-154">**nologo:** Displays no logo or copyright information.</span></span>  
  
    - <span data-ttu-id="3495a-155">**pełne:** Wyświetla pełne informacje o trybie.</span><span class="sxs-lookup"><span data-stu-id="3495a-155">**verbose:** Displays verbose mode information.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="3495a-156">Jeśli potrzebujesz listy opcji podczas uruchamiania narzędzia, wpisz **LocBaml.exe** i naciśnij klawisz ENTER.</span><span class="sxs-lookup"><span data-stu-id="3495a-156">If you need a list of the options when you are running the tool, type     **LocBaml.exe** and press ENTER.</span></span>  
  
<a name="parse_dll"></a>
## <a name="use-locbaml-to-parse-a-file"></a><span data-ttu-id="3495a-157">Analizowanie pliku za pomocąlocBaml</span><span class="sxs-lookup"><span data-stu-id="3495a-157">Use LocBaml to Parse a File</span></span>  
 <span data-ttu-id="3495a-158">Po utworzeniu narzędzia LocBaml można go użyć do przeanalizowania pliku HelloApp.resources.dll w celu wyodrębnienia zawartości tekstowej, która będzie zlokalizowana.</span><span class="sxs-lookup"><span data-stu-id="3495a-158">Now that you have created the LocBaml tool, you are ready to use it to parse HelloApp.resources.dll to extract the text content that will be localized.</span></span>  
  
1. <span data-ttu-id="3495a-159">Skopiuj program LocBaml.exe do folderu bin\debug aplikacji aplikacji, w którym utworzono główny zestaw aplikacji.</span><span class="sxs-lookup"><span data-stu-id="3495a-159">Copy LocBaml.exe to your application's bin\debug folder, where the main application assembly was created.</span></span>  
  
2. <span data-ttu-id="3495a-160">Aby przeanalizować plik zestawu satelickiego i zapisać dane wyjściowe jako plik csv, użyj następującego polecenia:</span><span class="sxs-lookup"><span data-stu-id="3495a-160">To parse the satellite assembly file and store the output as a .csv file, use the following command:</span></span>  
  
     <span data-ttu-id="3495a-161">**LocBaml.exe /parse HelloApp.resources.dll /out:Hello.csv**</span><span class="sxs-lookup"><span data-stu-id="3495a-161">**LocBaml.exe /parse HelloApp.resources.dll /out:Hello.csv**</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="3495a-162">Jeśli plik wejściowy HelloApp.resources.dll nie znajduje się w tym samym katalogu co LocBaml.exe przenieść jeden z plików, tak aby oba pliki znajdują się w tym samym katalogu.</span><span class="sxs-lookup"><span data-stu-id="3495a-162">If the input file, HelloApp.resources.dll, is not in the same directory as LocBaml.exe move one of the files so that both files are in the same directory.</span></span>  
  
3. <span data-ttu-id="3495a-163">Po uruchomieniu locBaml do analizowania plików dane wyjściowe składają się z siedmiu pól rozdzielonych przecinkami (pliki csv) lub kart (pliki.txt).</span><span class="sxs-lookup"><span data-stu-id="3495a-163">When you run LocBaml to parse files, the output consists of seven fields delimited by commas (.csv files) or tabs (.txt files).</span></span> <span data-ttu-id="3495a-164">Poniżej przedstawiono przeanalizowany plik csv dla pliku HelloApp.resources.dll:</span><span class="sxs-lookup"><span data-stu-id="3495a-164">The following shows the parsed .csv file for the HelloApp.resources.dll:</span></span>

   | |
   |-|
   |<span data-ttu-id="3495a-165">HelloApp.g.en-US.resources:window1.baml,Stack1:System.Windows.Controls.StackPanel.$Content,Ignore,FALSE, FALSE,,#Text1;#Text2;</span><span class="sxs-lookup"><span data-stu-id="3495a-165">HelloApp.g.en-US.resources:window1.baml,Stack1:System.Windows.Controls.StackPanel.$Content,Ignore,FALSE, FALSE,,#Text1;#Text2;</span></span>|
   |<span data-ttu-id="3495a-166">HelloApp.g.en-US.resources:window1.baml,Text1:System.Windows.Controls.TextBlock.$Content,None,TRUE, TRUE,,Hello World</span><span class="sxs-lookup"><span data-stu-id="3495a-166">HelloApp.g.en-US.resources:window1.baml,Text1:System.Windows.Controls.TextBlock.$Content,None,TRUE, TRUE,,Hello World</span></span>|
   |<span data-ttu-id="3495a-167">HelloApp.g.en-US.resources:window1.baml,Text2:System.Windows.Controls.TextBlock.$Content,None,TRUE, TRUE,,Goodbye World</span><span class="sxs-lookup"><span data-stu-id="3495a-167">HelloApp.g.en-US.resources:window1.baml,Text2:System.Windows.Controls.TextBlock.$Content,None,TRUE, TRUE,,Goodbye World</span></span>|

   <span data-ttu-id="3495a-168">Siedem pól to:</span><span class="sxs-lookup"><span data-stu-id="3495a-168">The seven fields are:</span></span>  
  
   1. <span data-ttu-id="3495a-169">**Nazwa BAML**.</span><span class="sxs-lookup"><span data-stu-id="3495a-169">**BAML Name**.</span></span> <span data-ttu-id="3495a-170">Nazwa zasobu BAML w odniesieniu do zestawu satelickiego języka źródłowego.</span><span class="sxs-lookup"><span data-stu-id="3495a-170">The name of the BAML resource with respect to the source language satellite assembly.</span></span>  
  
   2. <span data-ttu-id="3495a-171">**Klucz zasobu**.</span><span class="sxs-lookup"><span data-stu-id="3495a-171">**Resource Key**.</span></span> <span data-ttu-id="3495a-172">Zlokalizowany identyfikator zasobu.</span><span class="sxs-lookup"><span data-stu-id="3495a-172">The localized resource identifier.</span></span>  
  
   3. <span data-ttu-id="3495a-173">**Kategoria**.</span><span class="sxs-lookup"><span data-stu-id="3495a-173">**Category**.</span></span> <span data-ttu-id="3495a-174">Typ wartości.</span><span class="sxs-lookup"><span data-stu-id="3495a-174">The value type.</span></span> <span data-ttu-id="3495a-175">Zobacz [Atrybuty lokalizacji i komentarze](localization-attributes-and-comments.md).</span><span class="sxs-lookup"><span data-stu-id="3495a-175">See [Localization Attributes and Comments](localization-attributes-and-comments.md).</span></span>  
  
   4. <span data-ttu-id="3495a-176">**Czytelność**.</span><span class="sxs-lookup"><span data-stu-id="3495a-176">**Readability**.</span></span> <span data-ttu-id="3495a-177">Czy wartość może być odczytywana przez localizer.</span><span class="sxs-lookup"><span data-stu-id="3495a-177">Whether the value can be read by a localizer.</span></span> <span data-ttu-id="3495a-178">Zobacz [Atrybuty lokalizacji i komentarze](localization-attributes-and-comments.md).</span><span class="sxs-lookup"><span data-stu-id="3495a-178">See [Localization Attributes and Comments](localization-attributes-and-comments.md).</span></span>  
  
   5. <span data-ttu-id="3495a-179">**Możliwość modyfikacji**.</span><span class="sxs-lookup"><span data-stu-id="3495a-179">**Modifiability**.</span></span> <span data-ttu-id="3495a-180">Czy wartość może być modyfikowana przez localizer.</span><span class="sxs-lookup"><span data-stu-id="3495a-180">Whether the value can be modified by a localizer.</span></span> <span data-ttu-id="3495a-181">Zobacz [Atrybuty lokalizacji i komentarze](localization-attributes-and-comments.md).</span><span class="sxs-lookup"><span data-stu-id="3495a-181">See [Localization Attributes and Comments](localization-attributes-and-comments.md).</span></span>  
  
   6. <span data-ttu-id="3495a-182">**Komentarze**.</span><span class="sxs-lookup"><span data-stu-id="3495a-182">**Comments**.</span></span> <span data-ttu-id="3495a-183">Dodatkowy opis wartości, aby określić, jak wartość jest zlokalizowana.</span><span class="sxs-lookup"><span data-stu-id="3495a-183">Additional description of the value to help determine how a value is localized.</span></span> <span data-ttu-id="3495a-184">Zobacz [Atrybuty lokalizacji i komentarze](localization-attributes-and-comments.md).</span><span class="sxs-lookup"><span data-stu-id="3495a-184">See [Localization Attributes and Comments](localization-attributes-and-comments.md).</span></span>  
  
   7. <span data-ttu-id="3495a-185">**Wartość**.</span><span class="sxs-lookup"><span data-stu-id="3495a-185">**Value**.</span></span> <span data-ttu-id="3495a-186">Wartość tekstu do przetłumaczenia na żądaną kulturę.</span><span class="sxs-lookup"><span data-stu-id="3495a-186">The text value to translate to the desired culture.</span></span>  
  
   <span data-ttu-id="3495a-187">W poniższej tabeli pokazano, jak te pola są mapowane na rozdzielone wartości pliku csv:</span><span class="sxs-lookup"><span data-stu-id="3495a-187">The following table shows how these fields map to the delimited values of the .csv file:</span></span>  
  
   |<span data-ttu-id="3495a-188">Nazwa BAML</span><span class="sxs-lookup"><span data-stu-id="3495a-188">BAML name</span></span>|<span data-ttu-id="3495a-189">Klucz zasobu</span><span class="sxs-lookup"><span data-stu-id="3495a-189">Resource key</span></span>|<span data-ttu-id="3495a-190">Kategoria</span><span class="sxs-lookup"><span data-stu-id="3495a-190">Category</span></span>|<span data-ttu-id="3495a-191">Czytelność</span><span class="sxs-lookup"><span data-stu-id="3495a-191">Readability</span></span>|<span data-ttu-id="3495a-192">Modifiability</span><span class="sxs-lookup"><span data-stu-id="3495a-192">Modifiability</span></span>|<span data-ttu-id="3495a-193">Komentarze</span><span class="sxs-lookup"><span data-stu-id="3495a-193">Comments</span></span>|<span data-ttu-id="3495a-194">Wartość</span><span class="sxs-lookup"><span data-stu-id="3495a-194">Value</span></span>|  
   |---------------|------------------|--------------|-----------------|-------------------|--------------|-----------|
   |<span data-ttu-id="3495a-195">HelloApp.g.en-US.resources:window1.baml</span><span class="sxs-lookup"><span data-stu-id="3495a-195">HelloApp.g.en-US.resources:window1.baml</span></span>|<span data-ttu-id="3495a-196">Stack1:System.Windows.Controls.StackPanel.$Content</span><span class="sxs-lookup"><span data-stu-id="3495a-196">Stack1:System.Windows.Controls.StackPanel.$Content</span></span>|<span data-ttu-id="3495a-197">Zignoruj</span><span class="sxs-lookup"><span data-stu-id="3495a-197">Ignore</span></span>|<span data-ttu-id="3495a-198">FAŁSZ</span><span class="sxs-lookup"><span data-stu-id="3495a-198">FALSE</span></span>|<span data-ttu-id="3495a-199">FAŁSZ</span><span class="sxs-lookup"><span data-stu-id="3495a-199">FALSE</span></span>||<span data-ttu-id="3495a-200">#Text1;#Text2</span><span class="sxs-lookup"><span data-stu-id="3495a-200">#Text1;#Text2</span></span>|
   |<span data-ttu-id="3495a-201">HelloApp.g.en-US.resources:window1.baml</span><span class="sxs-lookup"><span data-stu-id="3495a-201">HelloApp.g.en-US.resources:window1.baml</span></span>|<span data-ttu-id="3495a-202">Tekst1:System.Windows.Controls.TextBlock.$Content</span><span class="sxs-lookup"><span data-stu-id="3495a-202">Text1:System.Windows.Controls.TextBlock.$Content</span></span>|<span data-ttu-id="3495a-203">Brak</span><span class="sxs-lookup"><span data-stu-id="3495a-203">None</span></span>|<span data-ttu-id="3495a-204">Prawda</span><span class="sxs-lookup"><span data-stu-id="3495a-204">TRUE</span></span>|<span data-ttu-id="3495a-205">Prawda</span><span class="sxs-lookup"><span data-stu-id="3495a-205">TRUE</span></span>||<span data-ttu-id="3495a-206">Witaj, świecie</span><span class="sxs-lookup"><span data-stu-id="3495a-206">Hello World</span></span>|
   |<span data-ttu-id="3495a-207">HelloApp.g.en-US.resources:window1.baml</span><span class="sxs-lookup"><span data-stu-id="3495a-207">HelloApp.g.en-US.resources:window1.baml</span></span>|<span data-ttu-id="3495a-208">Tekst2:System.Windows.Controls.TextBlock.$Content</span><span class="sxs-lookup"><span data-stu-id="3495a-208">Text2:System.Windows.Controls.TextBlock.$Content</span></span>|<span data-ttu-id="3495a-209">Brak</span><span class="sxs-lookup"><span data-stu-id="3495a-209">None</span></span>|<span data-ttu-id="3495a-210">Prawda</span><span class="sxs-lookup"><span data-stu-id="3495a-210">TRUE</span></span>|<span data-ttu-id="3495a-211">Prawda</span><span class="sxs-lookup"><span data-stu-id="3495a-211">TRUE</span></span>||<span data-ttu-id="3495a-212">Żegnaj Świat</span><span class="sxs-lookup"><span data-stu-id="3495a-212">Goodbye World</span></span>|
  
   <span data-ttu-id="3495a-213">Należy zauważyć, że wszystkie wartości dla **pola Komentarze** nie zawierają żadnych wartości; jeśli pole nie ma wartości, jest puste.</span><span class="sxs-lookup"><span data-stu-id="3495a-213">Notice that all the values for the **Comments** field contain no values; if a field doesn't have a value, it is empty.</span></span> <span data-ttu-id="3495a-214">Należy również zauważyć, że element w pierwszym wierszu nie jest czytelny ani modyfikowalny i ma "Ignore" jako wartość **kategorii,** z których wszystkie wskazują, że wartość nie jest zlokalizowana.</span><span class="sxs-lookup"><span data-stu-id="3495a-214">Also notice that the item in the first row is neither readable nor modifiable, and has "Ignore" as its **Category** value, all of which indicates that the value is not localizable.</span></span>  
  
4. <span data-ttu-id="3495a-215">Aby ułatwić wykrywanie elementów zlokalizowanych w analizowanych plikach, szczególnie w dużych plikach, można sortować lub filtrować elementy według **kategorii,** **czytelności**i **modyfikowalności**.</span><span class="sxs-lookup"><span data-stu-id="3495a-215">To facilitate discovery of localizable items in parsed files, particularly in large files, you can sort or filter the items by **Category**, **Readability**, and **Modifiability**.</span></span> <span data-ttu-id="3495a-216">Na przykład można odfiltrować nieczytelne i niemodyfikowalne wartości.</span><span class="sxs-lookup"><span data-stu-id="3495a-216">For example, you can filter out unreadable and unmodifiable values.</span></span>  
  
<a name="translate_loc_content"></a>
## <a name="translate-the-localizable-content"></a><span data-ttu-id="3495a-217">Tłumaczenie zawartości lokalizowalnej</span><span class="sxs-lookup"><span data-stu-id="3495a-217">Translate the Localizable Content</span></span>  
 <span data-ttu-id="3495a-218">Użyj dowolnego dostępnego narzędzia do tłumaczenia wyodrębnionych treści.</span><span class="sxs-lookup"><span data-stu-id="3495a-218">Use any tool that you have available to translate the extracted content.</span></span> <span data-ttu-id="3495a-219">Dobrym sposobem jest zapisanie zasobów w pliku csv i wyświetlenie ich w programie Microsoft Excel, wprowadzenie zmian w tłumaczeniu do ostatniej kolumny (wartości).</span><span class="sxs-lookup"><span data-stu-id="3495a-219">A good way to do this is to write the resources to a .csv file and view them in Microsoft Excel, making translation changes to the last column (value).</span></span>  
  
<a name="merge_translations"></a>
## <a name="use-locbaml-to-generate-a-new-resourcesdll-file"></a><span data-ttu-id="3495a-220">Generowanie nowego pliku .resources.dll za pomocą funkcji LocBaml</span><span class="sxs-lookup"><span data-stu-id="3495a-220">Use LocBaml to Generate a New .resources.dll File</span></span>  
 <span data-ttu-id="3495a-221">Zawartość, która została zidentyfikowana przez analizowanie HelloApp.resources.dll z LocBaml został przetłumaczony i muszą być scalone z powrotem do oryginalnej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="3495a-221">The content that was identified by parsing HelloApp.resources.dll with LocBaml has been translated and must be merged back into the original application.</span></span> <span data-ttu-id="3495a-222">Użyj opcji **generuj** lub **-g,** aby wygenerować nowy plik .resources.dll.</span><span class="sxs-lookup"><span data-stu-id="3495a-222">Use the **generate** or **-g** option to generate a new .resources.dll file.</span></span>  
  
1. <span data-ttu-id="3495a-223">Użyj następującej składni, aby wygenerować nowy plik HelloApp.resources.dll.</span><span class="sxs-lookup"><span data-stu-id="3495a-223">Use the following syntax to generate a new HelloApp.resources.dll file.</span></span> <span data-ttu-id="3495a-224">Oznacz kulturę jako en-US (/cul:en-US).</span><span class="sxs-lookup"><span data-stu-id="3495a-224">Mark the culture as en-US (/cul:en-US).</span></span>  
  
     <span data-ttu-id="3495a-225">**LocBaml.exe /generate HelloApp.resources.dll /trans:Hello.csv /out:c:\ /cul:en-US**</span><span class="sxs-lookup"><span data-stu-id="3495a-225">**LocBaml.exe /generate HelloApp.resources.dll /trans:Hello.csv /out:c:\ /cul:en-US**</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="3495a-226">Jeśli plik wejściowy Hello.csv nie znajduje się w tym samym katalogu co plik wykonywalny LocBaml.exe, przenieś jeden z plików, aby oba pliki były w tym samym katalogu.</span><span class="sxs-lookup"><span data-stu-id="3495a-226">If the input file, Hello.csv, is not in the same directory as the executable, LocBaml.exe, move one of the files so that both files are in the same directory.</span></span>  
  
2. <span data-ttu-id="3495a-227">Zastąp stary plik HelloApp.resources.dll w katalogu C:\HelloApp\Bin\Debug\en-US\HelloApp.resources.dll nowo utworzonym plikiem HelloApp.resources.dll.</span><span class="sxs-lookup"><span data-stu-id="3495a-227">Replace the old HelloApp.resources.dll file in the C:\HelloApp\Bin\Debug\en-US\HelloApp.resources.dll directory with your newly created HelloApp.resources.dll file.</span></span>  
  
3. <span data-ttu-id="3495a-228">"Hello World" i "Goodbye World" powinny być teraz tłumaczone w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="3495a-228">"Hello World" and "Goodbye World" should now be translated in your application.</span></span>  
  
4. <span data-ttu-id="3495a-229">Aby przetłumaczyć na inną kulturę, użyj kultury języka, na który tłumaczysz.</span><span class="sxs-lookup"><span data-stu-id="3495a-229">To translate to a different culture, use the culture of the language that you are translating to.</span></span> <span data-ttu-id="3495a-230">W poniższym przykładzie pokazano, jak przetłumaczyć na francusko-kanadyjskie:</span><span class="sxs-lookup"><span data-stu-id="3495a-230">The following example shows how to translate to French-Canadian:</span></span>  
  
     <span data-ttu-id="3495a-231">**LocBaml.exe /generate HelloApp.resources.dll /trans:Hellofr-CA.csv /out:c:\ /cul:fr-CA**</span><span class="sxs-lookup"><span data-stu-id="3495a-231">**LocBaml.exe /generate HelloApp.resources.dll /trans:Hellofr-CA.csv /out:c:\ /cul:fr-CA**</span></span>  
  
5. <span data-ttu-id="3495a-232">W tym samym zestawie co główny zestaw aplikacji utwórz nowy folder specyficzny dla kultury, aby pomieścić nowy zestaw satelickiego.</span><span class="sxs-lookup"><span data-stu-id="3495a-232">In the same assembly as the main application assembly, create a new culture-specific folder to house the new satellite assembly.</span></span> <span data-ttu-id="3495a-233">W przypadku języka francusko-kanadyjskiego folder będzie fr-CA.</span><span class="sxs-lookup"><span data-stu-id="3495a-233">For French-Canadian, the folder would be fr-CA.</span></span>  
  
6. <span data-ttu-id="3495a-234">Skopiuj wygenerowany zestaw satelitowy do nowego folderu.</span><span class="sxs-lookup"><span data-stu-id="3495a-234">Copy the generated satellite assembly to the new folder.</span></span>  
  
7. <span data-ttu-id="3495a-235">Aby przetestować nowy zestaw satelickiego, należy zmienić kulturę, w ramach której zostanie uruchomiony aplikacji.</span><span class="sxs-lookup"><span data-stu-id="3495a-235">To test the new satellite assembly, you need to change the culture under which your application will run.</span></span> <span data-ttu-id="3495a-236">Można to zrobić na jeden z dwóch sposobów:</span><span class="sxs-lookup"><span data-stu-id="3495a-236">You can do this in one of two ways:</span></span>  
  
    - <span data-ttu-id="3495a-237">Zmienianie ustawień regionalnych systemu operacyjnego **(Start** &#124; **Panel sterowania** &#124; **opcje regionalne i językowe).**</span><span class="sxs-lookup"><span data-stu-id="3495a-237">Change your operating system's regional settings (**Start** &#124; **Control Panel** &#124; **Regional and Language Options**).</span></span>  
  
    - <span data-ttu-id="3495a-238">W aplikacji dodaj następujący kod do App.xaml.cs:</span><span class="sxs-lookup"><span data-stu-id="3495a-238">In your application, add the following code to App.xaml.cs:</span></span>  
  
   [!code-xaml[LocBamlChangeCultureSnippets#LocBamlChangeCultureMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/LocBamlChangeCultureSnippets/CSharp/App.xaml#locbamlchangeculturemarkup)]
   [!code-csharp[LocBamlChangeCultureSnippets#LocBamlChangeCultureCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/LocBamlChangeCultureSnippets/CSharp/App.xaml.cs#locbamlchangeculturecodebehind)]
   [!code-vb[LocBamlChangeCultureSnippets#LocBamlChangeCultureCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/LocBamlChangeCultureSnippets/VisualBasic/Application.xaml.vb#locbamlchangeculturecodebehind)]  
  
<a name="Some_Tips_for_Using_LocBaml"></a>
## <a name="some-tips-for-using-locbaml"></a><span data-ttu-id="3495a-239">Kilka wskazówek dotyczących korzystania z LocBaml</span><span class="sxs-lookup"><span data-stu-id="3495a-239">Some Tips for Using LocBaml</span></span>  
  
- <span data-ttu-id="3495a-240">Wszystkie zestawy zależne, które definiują formanty niestandardowe, muszą zostać skopiowane do lokalnego katalogu LocBaml lub zainstalowane w pliku GAC.</span><span class="sxs-lookup"><span data-stu-id="3495a-240">All dependent assemblies that define custom controls must be copied into the local directory of LocBaml or installed into the GAC.</span></span> <span data-ttu-id="3495a-241">Jest to konieczne, ponieważ interfejs API lokalizacji musi mieć dostęp do zestawów zależnych podczas odczytywania binarnego XAML (BAML).</span><span class="sxs-lookup"><span data-stu-id="3495a-241">This is necessary because the localization API must have access to the dependent assemblies when it reads the binary XAML (BAML).</span></span>  
  
- <span data-ttu-id="3495a-242">Jeśli zestaw główny jest podpisany, wygenerowany rekord DLL zasobów musi być również podpisany w celu załadowania.</span><span class="sxs-lookup"><span data-stu-id="3495a-242">If the main assembly is signed, the generated resource DLL must also be signed in order for it to be loaded.</span></span>  
  
- <span data-ttu-id="3495a-243">Wersja biblioteki DLL zlokalizowanego zasobu musi być zsynchronizowana z zestawem głównym.</span><span class="sxs-lookup"><span data-stu-id="3495a-243">The version of the localized resource DLL needs to be synchronized with the main assembly.</span></span>  
  
<a name="Whats_Next"></a>
## <a name="whats-next"></a><span data-ttu-id="3495a-244">Co dalej</span><span class="sxs-lookup"><span data-stu-id="3495a-244">What's Next</span></span>  
 <span data-ttu-id="3495a-245">Teraz powinieneś mieć podstawową wiedzę na temat korzystania z narzędzia LocBaml.</span><span class="sxs-lookup"><span data-stu-id="3495a-245">You should now have a basic understanding of how to use the LocBaml tool.</span></span>  <span data-ttu-id="3495a-246">Powinieneś być w stanie zrobić plik, który zawiera Uids.</span><span class="sxs-lookup"><span data-stu-id="3495a-246">You should be able to make a file that contains Uids.</span></span> <span data-ttu-id="3495a-247">Za pomocą narzędzia LocBaml, należy mieć możliwość przeanalizowania pliku, aby wyodrębnić zawartość zlokalizowaną, a po przetłumaczeniu zawartości, powinien być w stanie wygenerować plik .resources.dll, który łączy przetłumaczoną zawartość.</span><span class="sxs-lookup"><span data-stu-id="3495a-247">By using the LocBaml tool, you should be able to parse a file to extract the localizable content, and after the content is translated, you should be able to generate a .resources.dll file that merges the translated content.</span></span> <span data-ttu-id="3495a-248">Ten temat nie zawiera wszystkich możliwych szczegółów, ale masz teraz wiedzę niezbędną do używania LocBaml do lokalizowania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="3495a-248">This topic does not include every possible detail, but you now have the knowledge necessary to use LocBaml for localizing your applications.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3495a-249">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3495a-249">See also</span></span>

- [<span data-ttu-id="3495a-250">Globalizacja dla WPF</span><span class="sxs-lookup"><span data-stu-id="3495a-250">Globalization for WPF</span></span>](globalization-for-wpf.md)
- [<span data-ttu-id="3495a-251">Przegląd używania automatycznego układu</span><span class="sxs-lookup"><span data-stu-id="3495a-251">Use Automatic Layout Overview</span></span>](use-automatic-layout-overview.md)
