---
title: 'Instrukcje: Lokalizowanie aplikacji'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- localization [WPF], applications
- LocBaml tool [WPF]
- applications [WPF], localizing
ms.assetid: 5001227e-9326-48a4-9dcd-ba1b89ee6653
ms.openlocfilehash: 749ba2dd9318976289d9d4140cfadd711e0548d4
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/30/2019
ms.locfileid: "68629871"
---
# <a name="how-to-localize-an-application"></a><span data-ttu-id="c90d6-102">Instrukcje: Lokalizowanie aplikacji</span><span class="sxs-lookup"><span data-stu-id="c90d6-102">How to: Localize an Application</span></span>
<span data-ttu-id="c90d6-103">W tym samouczku wyjaśniono, jak utworzyć zlokalizowaną aplikację przy użyciu narzędzia LocBaml.</span><span class="sxs-lookup"><span data-stu-id="c90d6-103">This tutorial explains how to create a localized application by using the LocBaml tool.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c90d6-104">Narzędzie LocBaml nie jest aplikacją przygotowaną do produkcji.</span><span class="sxs-lookup"><span data-stu-id="c90d6-104">The LocBaml tool is not a production-ready application.</span></span> <span data-ttu-id="c90d6-105">Jest on prezentowany jako przykład, który używa niektórych interfejsów API lokalizacji i ilustruje sposób pisania narzędzia lokalizacji.</span><span class="sxs-lookup"><span data-stu-id="c90d6-105">It is presented as a sample that uses some of the localization APIs and illustrates how you might write a localization tool.</span></span>  
  
<a name="Introduction"></a>   
## <a name="overview"></a><span data-ttu-id="c90d6-106">Omówienie</span><span class="sxs-lookup"><span data-stu-id="c90d6-106">Overview</span></span>  
 <span data-ttu-id="c90d6-107">Ta dyskusja zawiera podejście krok po kroku dotyczące lokalizowania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="c90d6-107">This discussion gives you a step-by-step approach to localizing an application.</span></span> <span data-ttu-id="c90d6-108">Najpierw przygotujesz aplikację, tak aby tekst, który zostanie przetłumaczony, mógł zostać wyodrębniony.</span><span class="sxs-lookup"><span data-stu-id="c90d6-108">First, you will prepare your application so that the text that will be translated can be extracted.</span></span> <span data-ttu-id="c90d6-109">Po przetłumaczeniu tekstu zostanie scalony przetłumaczony tekst na nową kopię oryginalnej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="c90d6-109">After the text is translated, you will merge the translated text into a new copy of the original application.</span></span>  
  
<a name="Requirements"></a>   
## <a name="requirements"></a><span data-ttu-id="c90d6-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c90d6-110">Requirements</span></span>  
 <span data-ttu-id="c90d6-111">W trakcie tej dyskusji zostanie użyty [!INCLUDE[TLA#tla_msbuild](../../../../includes/tlasharptla-msbuild-md.md)], który jest kompilatorem uruchamianym z wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="c90d6-111">Over the course of this discussion, you will use [!INCLUDE[TLA#tla_msbuild](../../../../includes/tlasharptla-msbuild-md.md)], which is a compiler that runs from the command line.</span></span>  
  
 <span data-ttu-id="c90d6-112">Ponadto zostanie nadana instrukcja użycia pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="c90d6-112">Also, you will be instructed to use a project file.</span></span> <span data-ttu-id="c90d6-113">Aby uzyskać instrukcje dotyczące używania [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] i plików projektu, zobacz Kompilowanie [i wdrażanie](../app-development/building-and-deploying-wpf-applications.md).</span><span class="sxs-lookup"><span data-stu-id="c90d6-113">For instructions on how to use [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] and project files, see [Build and Deploy](../app-development/building-and-deploying-wpf-applications.md).</span></span>  
  
 <span data-ttu-id="c90d6-114">We wszystkich przykładach w tym omówieniu użyto języka en-US (angielski-US) jako kultury.</span><span class="sxs-lookup"><span data-stu-id="c90d6-114">All the examples in this discussion use en-US (English-US) as the culture.</span></span> <span data-ttu-id="c90d6-115">Dzięki temu można wykonać kroki przykładów bez instalowania innego języka.</span><span class="sxs-lookup"><span data-stu-id="c90d6-115">This enables you to work through the steps of the examples without installing a different language.</span></span>  
  
<a name="create_sample_app"></a>   
## <a name="create-a-sample-application"></a><span data-ttu-id="c90d6-116">Tworzenie przykładowej aplikacji</span><span class="sxs-lookup"><span data-stu-id="c90d6-116">Create a Sample Application</span></span>  
 <span data-ttu-id="c90d6-117">W tym kroku zostanie przygotowana aplikacja do lokalizacji.</span><span class="sxs-lookup"><span data-stu-id="c90d6-117">In this step, you will prepare your application for localization.</span></span> <span data-ttu-id="c90d6-118">[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] W przykładach jest dostarczany przykład HelloApp, który będzie używany w przykładach kodu w tej dyskusji.</span><span class="sxs-lookup"><span data-stu-id="c90d6-118">In the [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] samples, a HelloApp sample is supplied that will be used for the code examples in this discussion.</span></span> <span data-ttu-id="c90d6-119">Jeśli chcesz użyć tego przykładu, Pobierz [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] pliki z przykładu [Narzędzia LocBaml](https://go.microsoft.com/fwlink/?LinkID=160016).</span><span class="sxs-lookup"><span data-stu-id="c90d6-119">If you would like to use this sample, download the [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] files from the [LocBaml Tool Sample](https://go.microsoft.com/fwlink/?LinkID=160016).</span></span>  
  
1. <span data-ttu-id="c90d6-120">Utwórz aplikację w punkcie, w którym chcesz rozpocząć lokalizację.</span><span class="sxs-lookup"><span data-stu-id="c90d6-120">Develop your application to the point where you want to start localization.</span></span>  
  
2. <span data-ttu-id="c90d6-121">Określ język programistyczny w pliku projektu, tak [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] aby generował główny zestaw i zestaw satelicki (plik z rozszerzeniem. resources. dll) zawierający zasoby języka neutralnego.</span><span class="sxs-lookup"><span data-stu-id="c90d6-121">Specify the development language in the project file so that [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] generates a main assembly and a satellite assembly (a file with the .resources.dll extension) to contain the neutral language resources.</span></span> <span data-ttu-id="c90d6-122">Plik projektu w przykładzie HelloApp jest HelloApp. csproj.</span><span class="sxs-lookup"><span data-stu-id="c90d6-122">The project file in the HelloApp sample is HelloApp.csproj.</span></span> <span data-ttu-id="c90d6-123">W tym pliku znajdziesz następujący język programowania:</span><span class="sxs-lookup"><span data-stu-id="c90d6-123">In that file, you will find the development language identified as follows:</span></span>  
  
     `<UICulture>en-US</UICulture>`  
  
3. <span data-ttu-id="c90d6-124">Dodawanie identyfikatorów UID do [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] plików.</span><span class="sxs-lookup"><span data-stu-id="c90d6-124">Add Uids to your [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] files.</span></span> <span data-ttu-id="c90d6-125">Identyfikatory UID są używane do śledzenia zmian w plikach i identyfikowania elementów, które muszą być przetłumaczone.</span><span class="sxs-lookup"><span data-stu-id="c90d6-125">Uids are used to keep track of changes to files and to identify items that must be translated.</span></span> <span data-ttu-id="c90d6-126">Aby dodać UID do plików, uruchom **updateuid** w pliku projektu:</span><span class="sxs-lookup"><span data-stu-id="c90d6-126">To add Uids to your files, run **updateuid** on your project file:</span></span>  
  
     <span data-ttu-id="c90d6-127">**MSBuild-t:updateuid helloapp. csproj**</span><span class="sxs-lookup"><span data-stu-id="c90d6-127">**msbuild -t:updateuid helloapp.csproj**</span></span>  
  
     <span data-ttu-id="c90d6-128">Aby sprawdzić, czy nie ma żadnych lub zduplikowanych identyfikatorów UID, uruchom **checkuid**:</span><span class="sxs-lookup"><span data-stu-id="c90d6-128">To verify that you have no missing or duplicate Uids, run **checkuid**:</span></span>  
  
     <span data-ttu-id="c90d6-129">**MSBuild-t:checkuid helloapp. csproj**</span><span class="sxs-lookup"><span data-stu-id="c90d6-129">**msbuild -t:checkuid helloapp.csproj**</span></span>  
  
     <span data-ttu-id="c90d6-130">Po uruchomieniu **updateuid**pliki powinny zawierać identyfikatory UID.</span><span class="sxs-lookup"><span data-stu-id="c90d6-130">After running **updateuid**, your files should contain Uids.</span></span> <span data-ttu-id="c90d6-131">Na przykład w pliku Pane1. XAML HelloApp należy znaleźć następujące informacje:</span><span class="sxs-lookup"><span data-stu-id="c90d6-131">For example, in the Pane1.xaml file of HelloApp, you should find the following:</span></span>  
  
     `<StackPanel x:Uid="StackPanel_1">`  
  
     `<TextBlock x:Uid="TextBlock_1">Hello World</TextBlock>`  
  
     `<TextBlock x:Uid="TextBlock_2">Goodbye World</TextBlock>`  
  
     `</StackPanel>`  
  
<a name="create_dll"></a>   
## <a name="create-the-neutral-language-resources-satellite-assembly"></a><span data-ttu-id="c90d6-132">Tworzenie zestawu satelickiego dla zasobów języka neutralnego</span><span class="sxs-lookup"><span data-stu-id="c90d6-132">Create the Neutral Language Resources Satellite Assembly</span></span>  
 <span data-ttu-id="c90d6-133">Po skonfigurowaniu aplikacji do generowania zestawu satelickiego dla neutralnych zasobów języka należy skompilować aplikację.</span><span class="sxs-lookup"><span data-stu-id="c90d6-133">After the application is configured to generate a neutral language resources satellite assembly, you build the application.</span></span> <span data-ttu-id="c90d6-134">Spowoduje to wygenerowanie głównego zestawu aplikacji oraz zestawu satelickiego dla zasobów języka neutralnego, który jest wymagany przez LocBaml do lokalizacji.</span><span class="sxs-lookup"><span data-stu-id="c90d6-134">This generates the main application assembly, as well as the neutral language resources satellite assembly that is required by LocBaml for localization.</span></span> <span data-ttu-id="c90d6-135">Aby skompilować aplikację:</span><span class="sxs-lookup"><span data-stu-id="c90d6-135">To build the application:</span></span>  
  
1. <span data-ttu-id="c90d6-136">Kompiluj HelloApp do tworzenia biblioteki dołączanej dynamicznie (DLL):</span><span class="sxs-lookup"><span data-stu-id="c90d6-136">Compile HelloApp to create a dynamic-link library (DLL):</span></span>  
  
     <span data-ttu-id="c90d6-137">**MSBuild helloapp. csproj**</span><span class="sxs-lookup"><span data-stu-id="c90d6-137">**msbuild helloapp.csproj**</span></span>  
  
2. <span data-ttu-id="c90d6-138">Nowo utworzony zestaw aplikacji głównej (HelloApp. exe) jest tworzony w następującym folderze:</span><span class="sxs-lookup"><span data-stu-id="c90d6-138">The newly created main application assembly, HelloApp.exe, is created in the following folder:</span></span>  
  
     `C:\HelloApp\Bin\Debug\`  
  
3. <span data-ttu-id="c90d6-139">Nowo utworzony zestaw satelicki dla zasobów języka neutralnego, HelloApp. resources. dll, został utworzony w następującym folderze:</span><span class="sxs-lookup"><span data-stu-id="c90d6-139">The newly created neutral language resources satellite assembly, HelloApp.resources.dll, is created in the following folder:</span></span>  
  
     `C:\HelloApp\Bin\Debug\en-US\`  
  
<a name="build_locbaml"></a>   
## <a name="build-the-locbaml-tool"></a><span data-ttu-id="c90d6-140">Tworzenie narzędzia LocBaml</span><span class="sxs-lookup"><span data-stu-id="c90d6-140">Build the LocBaml Tool</span></span>  
  
1. <span data-ttu-id="c90d6-141">Wszystkie pliki niezbędne do kompilowania LocBaml znajdują się w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] przykładach.</span><span class="sxs-lookup"><span data-stu-id="c90d6-141">All the files necessary to build LocBaml are located in the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] samples.</span></span> <span data-ttu-id="c90d6-142">Pobierz C# pliki z przykładu [Narzędzia LocBaml](https://go.microsoft.com/fwlink/?LinkID=160016).</span><span class="sxs-lookup"><span data-stu-id="c90d6-142">Download the C# files from the [LocBaml Tool Sample](https://go.microsoft.com/fwlink/?LinkID=160016).</span></span>  
  
2. <span data-ttu-id="c90d6-143">W wierszu polecenia Uruchom plik projektu (LocBaml. csproj) w celu skompilowania narzędzia:</span><span class="sxs-lookup"><span data-stu-id="c90d6-143">From the command line, run the project file (locbaml.csproj) to build the tool:</span></span>  
  
     <span data-ttu-id="c90d6-144">**msbuild locbaml.csproj**</span><span class="sxs-lookup"><span data-stu-id="c90d6-144">**msbuild locbaml.csproj**</span></span>  
  
3. <span data-ttu-id="c90d6-145">Przejdź do katalogu Bin\Release, aby znaleźć nowo utworzony plik wykonywalny (LocBaml. exe).</span><span class="sxs-lookup"><span data-stu-id="c90d6-145">Go to the Bin\Release directory to find the newly created executable file (locbaml.exe).</span></span> <span data-ttu-id="c90d6-146">Przykład: C: \LocBaml\Bin\Release\locbaml.exe.</span><span class="sxs-lookup"><span data-stu-id="c90d6-146">Example:C:\LocBaml\Bin\Release\locbaml.exe.</span></span>  
  
4. <span data-ttu-id="c90d6-147">Opcje, które można określić, gdy uruchamiasz LocBaml są następujące:</span><span class="sxs-lookup"><span data-stu-id="c90d6-147">The options that you can specify when you run LocBaml are as follows:</span></span>  
  
    - <span data-ttu-id="c90d6-148">**Analizuj** lub **-p:** Analizuje pliki BAML, zasoby lub biblioteki DLL w celu wygenerowania pliku CSV lub txt.</span><span class="sxs-lookup"><span data-stu-id="c90d6-148">**parse** or **-p:** Parses Baml, resources, or DLL files to generate a .csv or .txt file.</span></span>  
  
    - <span data-ttu-id="c90d6-149">**Generuj** lub **-g:** Generuje zlokalizowany plik binarny przy użyciu przetłumaczonego pliku.</span><span class="sxs-lookup"><span data-stu-id="c90d6-149">**generate** or **-g:** Generates a localized binary file by using a translated file.</span></span>  
  
    - <span data-ttu-id="c90d6-150">**out** lub **-o** {*FileDirectory*] **:** Nazwa pliku wyjściowego.</span><span class="sxs-lookup"><span data-stu-id="c90d6-150">**out** or **-o** {*filedirectory*] **:** Output file name.</span></span>  
  
    - <span data-ttu-id="c90d6-151">**kultura** lub **-CUL** {*Culture*] **:** Ustawienia regionalne zestawów wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="c90d6-151">**culture** or **-cul** {*culture*] **:** Locale of output assemblies.</span></span>  
  
    - <span data-ttu-id="c90d6-152">**tłumaczenie** lub **Trans** {*Translation. csv*] **:** Przetłumaczony lub zlokalizowany plik.</span><span class="sxs-lookup"><span data-stu-id="c90d6-152">**translation** or **-trans** {*translation.csv*] **:** Translated or localized file.</span></span>  
  
    - <span data-ttu-id="c90d6-153">**asmpath** lub **-asmpath:** {*FileDirectory*] **:** Jeśli kod zawiera niestandardowe kontrolki, należy podać asmpath do niestandardowego zestawu kontrolek. [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c90d6-153">**asmpath** or **-asmpath:** {*filedirectory*] **:** If your [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] code contains custom controls, you must supply the **asmpath** to the custom control assembly.</span></span>  
  
    - <span data-ttu-id="c90d6-154">**nologo** Nie wyświetla logo ani informacji o prawach autorskich.</span><span class="sxs-lookup"><span data-stu-id="c90d6-154">**nologo:** Displays no logo or copyright information.</span></span>  
  
    - <span data-ttu-id="c90d6-155">**pełne** Wyświetla informacje o trybie informacji pełnej.</span><span class="sxs-lookup"><span data-stu-id="c90d6-155">**verbose:** Displays verbose mode information.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="c90d6-156">Jeśli potrzebujesz listy opcji podczas uruchamiania narzędzia, wpisz **LocBaml. exe** i naciśnij klawisz ENTER.</span><span class="sxs-lookup"><span data-stu-id="c90d6-156">If you need a list of the options when you are running the tool, type     **LocBaml.exe** and press ENTER.</span></span>  
  
<a name="parse_dll"></a>   
## <a name="use-locbaml-to-parse-a-file"></a><span data-ttu-id="c90d6-157">Analizowanie pliku przy użyciu LocBaml</span><span class="sxs-lookup"><span data-stu-id="c90d6-157">Use LocBaml to Parse a File</span></span>  
 <span data-ttu-id="c90d6-158">Po utworzeniu narzędzia LocBaml można go użyć do przeanalizowania HelloApp. resources. dll w celu wyodrębnienia zawartości tekstowej, która ma zostać zlokalizowana.</span><span class="sxs-lookup"><span data-stu-id="c90d6-158">Now that you have created the LocBaml tool, you are ready to use it to parse HelloApp.resources.dll to extract the text content that will be localized.</span></span>  
  
1. <span data-ttu-id="c90d6-159">Skopiuj plik LocBaml. exe do folderu bin\Debug aplikacji, w którym został utworzony zestaw aplikacji głównej.</span><span class="sxs-lookup"><span data-stu-id="c90d6-159">Copy LocBaml.exe to your application's bin\debug folder, where the main application assembly was created.</span></span>  
  
2. <span data-ttu-id="c90d6-160">Aby przeanalizować plik zestawu satelickiego i zapisać dane wyjściowe jako plik CSV, użyj następującego polecenia:</span><span class="sxs-lookup"><span data-stu-id="c90d6-160">To parse the satellite assembly file and store the output as a .csv file, use the following command:</span></span>  
  
     <span data-ttu-id="c90d6-161">**LocBaml.exe /parse HelloApp.resources.dll /out:Hello.csv**</span><span class="sxs-lookup"><span data-stu-id="c90d6-161">**LocBaml.exe /parse HelloApp.resources.dll /out:Hello.csv**</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="c90d6-162">Jeśli plik wejściowy HelloApp. resources. dll nie znajduje się w tym samym katalogu, co LocBaml. exe Przenieś jeden z tych plików, tak aby oba pliki były w tym samym katalogu.</span><span class="sxs-lookup"><span data-stu-id="c90d6-162">If the input file, HelloApp.resources.dll, is not in the same directory as LocBaml.exe move one of the files so that both files are in the same directory.</span></span>  
  
3. <span data-ttu-id="c90d6-163">Po uruchomieniu LocBaml do analizowania plików dane wyjściowe składają się z siedmiu pól rozdzielonych przecinkami (pliki CSV) lub tabulatorami (pliki. txt).</span><span class="sxs-lookup"><span data-stu-id="c90d6-163">When you run LocBaml to parse files, the output consists of seven fields delimited by commas (.csv files) or tabs (.txt files).</span></span> <span data-ttu-id="c90d6-164">Poniżej przedstawiono przeanalizowany plik CSV dla HelloApp. resources. dll:</span><span class="sxs-lookup"><span data-stu-id="c90d6-164">The following shows the parsed .csv file for the HelloApp.resources.dll:</span></span>

   | |
   |-|
   |<span data-ttu-id="c90d6-165">HelloApp. g. pl-US. Resources: window1. BAML, Stack1: System. Windows. Controls. StackPanel. $Content, IGNORE, FALSE, FALSE,, #Text1; #Text2;</span><span class="sxs-lookup"><span data-stu-id="c90d6-165">HelloApp.g.en-US.resources:window1.baml,Stack1:System.Windows.Controls.StackPanel.$Content,Ignore,FALSE, FALSE,,#Text1;#Text2;</span></span>|
   |<span data-ttu-id="c90d6-166">HelloApp.g.en-US.resources:window1.baml,Text1:System.Windows.Controls.TextBlock.$Content,None,TRUE, TRUE,,Hello World</span><span class="sxs-lookup"><span data-stu-id="c90d6-166">HelloApp.g.en-US.resources:window1.baml,Text1:System.Windows.Controls.TextBlock.$Content,None,TRUE, TRUE,,Hello World</span></span>|
   |<span data-ttu-id="c90d6-167">HelloApp.g.en-US.resources:window1.baml,Text2:System.Windows.Controls.TextBlock.$Content,None,TRUE, TRUE,,Goodbye World</span><span class="sxs-lookup"><span data-stu-id="c90d6-167">HelloApp.g.en-US.resources:window1.baml,Text2:System.Windows.Controls.TextBlock.$Content,None,TRUE, TRUE,,Goodbye World</span></span>|

   <span data-ttu-id="c90d6-168">Siedem pól są następujące:</span><span class="sxs-lookup"><span data-stu-id="c90d6-168">The seven fields are:</span></span>  
  
   1. <span data-ttu-id="c90d6-169">**Nazwa BAML**.</span><span class="sxs-lookup"><span data-stu-id="c90d6-169">**BAML Name**.</span></span> <span data-ttu-id="c90d6-170">Nazwa zasobu BAML w odniesieniu do zestawu satelickiego dla języka źródłowego.</span><span class="sxs-lookup"><span data-stu-id="c90d6-170">The name of the BAML resource with respect to the source language satellite assembly.</span></span>  
  
   2. <span data-ttu-id="c90d6-171">**Klucz zasobu**.</span><span class="sxs-lookup"><span data-stu-id="c90d6-171">**Resource Key**.</span></span> <span data-ttu-id="c90d6-172">Zlokalizowany identyfikator zasobu.</span><span class="sxs-lookup"><span data-stu-id="c90d6-172">The localized resource identifier.</span></span>  
  
   3. <span data-ttu-id="c90d6-173">**Kategoria**.</span><span class="sxs-lookup"><span data-stu-id="c90d6-173">**Category**.</span></span> <span data-ttu-id="c90d6-174">Typ wartości.</span><span class="sxs-lookup"><span data-stu-id="c90d6-174">The value type.</span></span> <span data-ttu-id="c90d6-175">Zobacz [atrybuty lokalizacji i komentarze](localization-attributes-and-comments.md).</span><span class="sxs-lookup"><span data-stu-id="c90d6-175">See [Localization Attributes and Comments](localization-attributes-and-comments.md).</span></span>  
  
   4. <span data-ttu-id="c90d6-176">**Czytelność**.</span><span class="sxs-lookup"><span data-stu-id="c90d6-176">**Readability**.</span></span> <span data-ttu-id="c90d6-177">Określa, czy wartość może być odczytywana przez lokalizatora.</span><span class="sxs-lookup"><span data-stu-id="c90d6-177">Whether the value can be read by a localizer.</span></span> <span data-ttu-id="c90d6-178">Zobacz [atrybuty lokalizacji i komentarze](localization-attributes-and-comments.md).</span><span class="sxs-lookup"><span data-stu-id="c90d6-178">See [Localization Attributes and Comments](localization-attributes-and-comments.md).</span></span>  
  
   5. <span data-ttu-id="c90d6-179">**Modifiability**.</span><span class="sxs-lookup"><span data-stu-id="c90d6-179">**Modifiability**.</span></span> <span data-ttu-id="c90d6-180">Czy wartość może być modyfikowana przez lokalizatora.</span><span class="sxs-lookup"><span data-stu-id="c90d6-180">Whether the value can be modified by a localizer.</span></span> <span data-ttu-id="c90d6-181">Zobacz [atrybuty lokalizacji i komentarze](localization-attributes-and-comments.md).</span><span class="sxs-lookup"><span data-stu-id="c90d6-181">See [Localization Attributes and Comments](localization-attributes-and-comments.md).</span></span>  
  
   6. <span data-ttu-id="c90d6-182">**Komentarze**.</span><span class="sxs-lookup"><span data-stu-id="c90d6-182">**Comments**.</span></span> <span data-ttu-id="c90d6-183">Dodatkowy opis wartości, aby pomóc w ustaleniu, jak jest lokalizowana wartość.</span><span class="sxs-lookup"><span data-stu-id="c90d6-183">Additional description of the value to help determine how a value is localized.</span></span> <span data-ttu-id="c90d6-184">Zobacz [atrybuty lokalizacji i komentarze](localization-attributes-and-comments.md).</span><span class="sxs-lookup"><span data-stu-id="c90d6-184">See [Localization Attributes and Comments](localization-attributes-and-comments.md).</span></span>  
  
   7. <span data-ttu-id="c90d6-185">**Wartość**.</span><span class="sxs-lookup"><span data-stu-id="c90d6-185">**Value**.</span></span> <span data-ttu-id="c90d6-186">Wartość tekstowa do przetłumaczenia na pożądaną kulturę.</span><span class="sxs-lookup"><span data-stu-id="c90d6-186">The text value to translate to the desired culture.</span></span>  
  
   <span data-ttu-id="c90d6-187">W poniższej tabeli przedstawiono, w jaki sposób te pola są mapowane na wartości rozdzielane pliku CSV:</span><span class="sxs-lookup"><span data-stu-id="c90d6-187">The following table shows how these fields map to the delimited values of the .csv file:</span></span>  
  
   |<span data-ttu-id="c90d6-188">Nazwa BAML</span><span class="sxs-lookup"><span data-stu-id="c90d6-188">BAML name</span></span>|<span data-ttu-id="c90d6-189">Klucz zasobu</span><span class="sxs-lookup"><span data-stu-id="c90d6-189">Resource key</span></span>|<span data-ttu-id="c90d6-190">Kategoria</span><span class="sxs-lookup"><span data-stu-id="c90d6-190">Category</span></span>|<span data-ttu-id="c90d6-191">Czytelność</span><span class="sxs-lookup"><span data-stu-id="c90d6-191">Readability</span></span>|<span data-ttu-id="c90d6-192">Modifiability</span><span class="sxs-lookup"><span data-stu-id="c90d6-192">Modifiability</span></span>|<span data-ttu-id="c90d6-193">Komentarze</span><span class="sxs-lookup"><span data-stu-id="c90d6-193">Comments</span></span>|<span data-ttu-id="c90d6-194">Wartość</span><span class="sxs-lookup"><span data-stu-id="c90d6-194">Value</span></span>|  
   |---------------|------------------|--------------|-----------------|-------------------|--------------|-----------|
   |<span data-ttu-id="c90d6-195">HelloApp.g.en-US.resources:window1.baml</span><span class="sxs-lookup"><span data-stu-id="c90d6-195">HelloApp.g.en-US.resources:window1.baml</span></span>|<span data-ttu-id="c90d6-196">Stack1:System.Windows.Controls.StackPanel.$Content</span><span class="sxs-lookup"><span data-stu-id="c90d6-196">Stack1:System.Windows.Controls.StackPanel.$Content</span></span>|<span data-ttu-id="c90d6-197">Zignoruj</span><span class="sxs-lookup"><span data-stu-id="c90d6-197">Ignore</span></span>|<span data-ttu-id="c90d6-198">FAŁSZ</span><span class="sxs-lookup"><span data-stu-id="c90d6-198">FALSE</span></span>|<span data-ttu-id="c90d6-199">FAŁSZ</span><span class="sxs-lookup"><span data-stu-id="c90d6-199">FALSE</span></span>||<span data-ttu-id="c90d6-200">#Text1;#Text2</span><span class="sxs-lookup"><span data-stu-id="c90d6-200">#Text1;#Text2</span></span>|
   |<span data-ttu-id="c90d6-201">HelloApp.g.en-US.resources:window1.baml</span><span class="sxs-lookup"><span data-stu-id="c90d6-201">HelloApp.g.en-US.resources:window1.baml</span></span>|<span data-ttu-id="c90d6-202">Text1:System.Windows.Controls.TextBlock.$Content</span><span class="sxs-lookup"><span data-stu-id="c90d6-202">Text1:System.Windows.Controls.TextBlock.$Content</span></span>|<span data-ttu-id="c90d6-203">Brak</span><span class="sxs-lookup"><span data-stu-id="c90d6-203">None</span></span>|<span data-ttu-id="c90d6-204">OZNACZA</span><span class="sxs-lookup"><span data-stu-id="c90d6-204">TRUE</span></span>|<span data-ttu-id="c90d6-205">OZNACZA</span><span class="sxs-lookup"><span data-stu-id="c90d6-205">TRUE</span></span>||<span data-ttu-id="c90d6-206">Witaj Świecie</span><span class="sxs-lookup"><span data-stu-id="c90d6-206">Hello World</span></span>|
   |<span data-ttu-id="c90d6-207">HelloApp.g.en-US.resources:window1.baml</span><span class="sxs-lookup"><span data-stu-id="c90d6-207">HelloApp.g.en-US.resources:window1.baml</span></span>|<span data-ttu-id="c90d6-208">Text2:System.Windows.Controls.TextBlock.$Content</span><span class="sxs-lookup"><span data-stu-id="c90d6-208">Text2:System.Windows.Controls.TextBlock.$Content</span></span>|<span data-ttu-id="c90d6-209">Brak</span><span class="sxs-lookup"><span data-stu-id="c90d6-209">None</span></span>|<span data-ttu-id="c90d6-210">OZNACZA</span><span class="sxs-lookup"><span data-stu-id="c90d6-210">TRUE</span></span>|<span data-ttu-id="c90d6-211">OZNACZA</span><span class="sxs-lookup"><span data-stu-id="c90d6-211">TRUE</span></span>||<span data-ttu-id="c90d6-212">Na świecie</span><span class="sxs-lookup"><span data-stu-id="c90d6-212">Goodbye World</span></span>|
  
   <span data-ttu-id="c90d6-213">Zwróć uwagę, że wszystkie wartości pola **Komentarze** nie zawierają wartości; Jeśli pole nie ma wartości, jest puste.</span><span class="sxs-lookup"><span data-stu-id="c90d6-213">Notice that all the values for the **Comments** field contain no values; if a field doesn't have a value, it is empty.</span></span> <span data-ttu-id="c90d6-214">Zauważ również, że element w pierwszym wierszu nie jest możliwy do odczytania ani do zmodyfikowania, a jego wartość **kategorii** jest ignorowana, a wszystko wskazuje, że wartość nie jest lokalizowalna.</span><span class="sxs-lookup"><span data-stu-id="c90d6-214">Also notice that the item in the first row is neither readable nor modifiable, and has "Ignore" as its **Category** value, all of which indicates that the value is not localizable.</span></span>  
  
4. <span data-ttu-id="c90d6-215">Aby ułatwić odnajdywanie lokalizowalnych elementów w przeanalizowanych plikach, szczególnie w dużych plikach, można sortować lub filtrować elementy według **kategorii**, **czytelności**i **modifiability**.</span><span class="sxs-lookup"><span data-stu-id="c90d6-215">To facilitate discovery of localizable items in parsed files, particularly in large files, you can sort or filter the items by **Category**, **Readability**, and **Modifiability**.</span></span> <span data-ttu-id="c90d6-216">Na przykład można odfiltrować niemodyfikowalne i niemodyfikowane wartości.</span><span class="sxs-lookup"><span data-stu-id="c90d6-216">For example, you can filter out unreadable and unmodifiable values.</span></span>  
  
<a name="translate_loc_content"></a>   
## <a name="translate-the-localizable-content"></a><span data-ttu-id="c90d6-217">Tłumaczenie lokalizowalnej zawartości</span><span class="sxs-lookup"><span data-stu-id="c90d6-217">Translate the Localizable Content</span></span>  
 <span data-ttu-id="c90d6-218">Użyj dowolnego dostępnego narzędzia, aby przetłumaczyć wyodrębnioną zawartość.</span><span class="sxs-lookup"><span data-stu-id="c90d6-218">Use any tool that you have available to translate the extracted content.</span></span> <span data-ttu-id="c90d6-219">Dobrym sposobem jest zapisanie zasobów do pliku CSV i wyświetlenie ich w programie w [!INCLUDE[TLA#tla_xl](../../../../includes/tlasharptla-xl-md.md)]celu dokonania zmiany tłumaczenia na ostatnią kolumnę (wartość).</span><span class="sxs-lookup"><span data-stu-id="c90d6-219">A good way to do this is to write the resources to a .csv file and view them in [!INCLUDE[TLA#tla_xl](../../../../includes/tlasharptla-xl-md.md)], making translation changes to the last column (value).</span></span>  
  
<a name="merge_translations"></a>   
## <a name="use-locbaml-to-generate-a-new-resourcesdll-file"></a><span data-ttu-id="c90d6-220">Użyj LocBaml, aby wygenerować nowy plik resources. dll</span><span class="sxs-lookup"><span data-stu-id="c90d6-220">Use LocBaml to Generate a New .resources.dll File</span></span>  
 <span data-ttu-id="c90d6-221">Zawartość zidentyfikowana przez analizowanie HelloApp. resources. dll z LocBaml została przetłumaczona i należy ją scalić z powrotem do oryginalnej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="c90d6-221">The content that was identified by parsing HelloApp.resources.dll with LocBaml has been translated and must be merged back into the original application.</span></span> <span data-ttu-id="c90d6-222">Użyj opcji **Generuj** lub **-g** , aby wygenerować nowy plik resources. dll.</span><span class="sxs-lookup"><span data-stu-id="c90d6-222">Use the **generate** or **-g** option to generate a new .resources.dll file.</span></span>  
  
1. <span data-ttu-id="c90d6-223">Użyj następującej składni, aby wygenerować nowy plik HelloApp. resources. dll.</span><span class="sxs-lookup"><span data-stu-id="c90d6-223">Use the following syntax to generate a new HelloApp.resources.dll file.</span></span> <span data-ttu-id="c90d6-224">Oznacz kulturę jako en-US (/CUL: en-US).</span><span class="sxs-lookup"><span data-stu-id="c90d6-224">Mark the culture as en-US (/cul:en-US).</span></span>  
  
     <span data-ttu-id="c90d6-225">**LocBaml.exe /generate HelloApp.resources.dll /trans:Hello.csv /out:c:\ /cul:en-US**</span><span class="sxs-lookup"><span data-stu-id="c90d6-225">**LocBaml.exe /generate HelloApp.resources.dll /trans:Hello.csv /out:c:\ /cul:en-US**</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="c90d6-226">Jeśli plik wejściowy, Hello. csv, nie znajduje się w tym samym katalogu co plik wykonywalny, LocBaml. exe, Przenieś jeden z tych plików, tak aby oba pliki były w tym samym katalogu.</span><span class="sxs-lookup"><span data-stu-id="c90d6-226">If the input file, Hello.csv, is not in the same directory as the executable, LocBaml.exe, move one of the files so that both files are in the same directory.</span></span>  
  
2. <span data-ttu-id="c90d6-227">Zastąp stary plik HelloApp. resources. dll w katalogu C:\HelloApp\Bin\Debug\en-US\HelloApp.resources.dll nowo utworzonym plikiem HelloApp. resources. dll.</span><span class="sxs-lookup"><span data-stu-id="c90d6-227">Replace the old HelloApp.resources.dll file in the C:\HelloApp\Bin\Debug\en-US\HelloApp.resources.dll directory with your newly created HelloApp.resources.dll file.</span></span>  
  
3. <span data-ttu-id="c90d6-228">"Hello world" i "Pożegnanie świata" powinny teraz zostać przetłumaczone w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="c90d6-228">"Hello World" and "Goodbye World" should now be translated in your application.</span></span>  
  
4. <span data-ttu-id="c90d6-229">Aby przetłumaczyć na inną kulturę, należy użyć kultury języka, do którego jest przeprowadzana translacja.</span><span class="sxs-lookup"><span data-stu-id="c90d6-229">To translate to a different culture, use the culture of the language that you are translating to.</span></span> <span data-ttu-id="c90d6-230">Poniższy przykład pokazuje, jak przetłumaczyć na francuski — kanadyjski:</span><span class="sxs-lookup"><span data-stu-id="c90d6-230">The following example shows how to translate to French-Canadian:</span></span>  
  
     <span data-ttu-id="c90d6-231">**LocBaml. exe/Generate HelloApp. resources. dll/Trans: Hellofr-CA. csv/out: c:\/CUL: fr-CA**</span><span class="sxs-lookup"><span data-stu-id="c90d6-231">**LocBaml.exe /generate HelloApp.resources.dll /trans:Hellofr-CA.csv /out:c:\ /cul:fr-CA**</span></span>  
  
5. <span data-ttu-id="c90d6-232">W tym samym zestawie, w którym znajduje się główny zestaw aplikacji, Utwórz nowy folder specyficzny dla kultury, który ma być nowym zestawem satelickim.</span><span class="sxs-lookup"><span data-stu-id="c90d6-232">In the same assembly as the main application assembly, create a new culture-specific folder to house the new satellite assembly.</span></span> <span data-ttu-id="c90d6-233">W języku francuskim — kanadyjskim folderem będzie fr-CA.</span><span class="sxs-lookup"><span data-stu-id="c90d6-233">For French-Canadian, the folder would be fr-CA.</span></span>  
  
6. <span data-ttu-id="c90d6-234">Skopiuj wygenerowany zestaw satelicki do nowego folderu.</span><span class="sxs-lookup"><span data-stu-id="c90d6-234">Copy the generated satellite assembly to the new folder.</span></span>  
  
7. <span data-ttu-id="c90d6-235">Aby przetestować nowy zestaw satelicki, należy zmienić kulturę, w której zostanie uruchomiona aplikacja.</span><span class="sxs-lookup"><span data-stu-id="c90d6-235">To test the new satellite assembly, you need to change the culture under which your application will run.</span></span> <span data-ttu-id="c90d6-236">Można to zrobić na jeden z dwóch sposobów:</span><span class="sxs-lookup"><span data-stu-id="c90d6-236">You can do this in one of two ways:</span></span>  
  
    - <span data-ttu-id="c90d6-237">Zmień ustawienia regionalne systemu operacyjnego (**Uruchom** &#124; **panel** &#124; sterowania **Opcje regionalne i językowe**).</span><span class="sxs-lookup"><span data-stu-id="c90d6-237">Change your operating system's regional settings (**Start** &#124; **Control Panel** &#124; **Regional and Language Options**).</span></span>  
  
    - <span data-ttu-id="c90d6-238">W aplikacji Dodaj następujący kod do App.xaml.cs:</span><span class="sxs-lookup"><span data-stu-id="c90d6-238">In your application, add the following code to App.xaml.cs:</span></span>  
  
   [!code-xaml[LocBamlChangeCultureSnippets#LocBamlChangeCultureMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/LocBamlChangeCultureSnippets/CSharp/App.xaml#locbamlchangeculturemarkup)]
   [!code-csharp[LocBamlChangeCultureSnippets#LocBamlChangeCultureCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/LocBamlChangeCultureSnippets/CSharp/App.xaml.cs#locbamlchangeculturecodebehind)]
   [!code-vb[LocBamlChangeCultureSnippets#LocBamlChangeCultureCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/LocBamlChangeCultureSnippets/VisualBasic/Application.xaml.vb#locbamlchangeculturecodebehind)]  
  
<a name="Some_Tips_for_Using_LocBaml"></a>   
## <a name="some-tips-for-using-locbaml"></a><span data-ttu-id="c90d6-239">Niektóre wskazówki dotyczące używania LocBaml</span><span class="sxs-lookup"><span data-stu-id="c90d6-239">Some Tips for Using LocBaml</span></span>  
  
- <span data-ttu-id="c90d6-240">Wszystkie zestawy zależne, które definiują niestandardowe kontrolki, muszą zostać skopiowane do katalogu lokalnego LocBaml lub zainstalowane w pamięci podręcznej GAC.</span><span class="sxs-lookup"><span data-stu-id="c90d6-240">All dependent assemblies that define custom controls must be copied into the local directory of LocBaml or installed into the GAC.</span></span> <span data-ttu-id="c90d6-241">Jest to konieczne, ponieważ interfejs API lokalizacji musi mieć dostęp do zestawów zależnych, gdy odczytuje plik binarny XAML (BAML).</span><span class="sxs-lookup"><span data-stu-id="c90d6-241">This is necessary because the localization API must have access to the dependent assemblies when it reads the binary XAML (BAML).</span></span>  
  
- <span data-ttu-id="c90d6-242">Jeśli główny zestaw jest podpisany, wygenerowana Biblioteka DLL zasobów musi być również podpisana, aby można było ją załadować.</span><span class="sxs-lookup"><span data-stu-id="c90d6-242">If the main assembly is signed, the generated resource DLL must also be signed in order for it to be loaded.</span></span>  
  
- <span data-ttu-id="c90d6-243">Wersja zlokalizowanej biblioteki DLL zasobów musi być synchronizowana z zestawem głównym.</span><span class="sxs-lookup"><span data-stu-id="c90d6-243">The version of the localized resource DLL needs to be synchronized with the main assembly.</span></span>  
  
<a name="Whats_Next"></a>   
## <a name="whats-next"></a><span data-ttu-id="c90d6-244">Co dalej</span><span class="sxs-lookup"><span data-stu-id="c90d6-244">What's Next</span></span>  
 <span data-ttu-id="c90d6-245">Teraz należy uzyskać podstawową wiedzę na temat sposobu korzystania z narzędzia LocBaml.</span><span class="sxs-lookup"><span data-stu-id="c90d6-245">You should now have a basic understanding of how to use the LocBaml tool.</span></span>  <span data-ttu-id="c90d6-246">Powinno być możliwe tworzenie pliku, który zawiera identyfikatory UID.</span><span class="sxs-lookup"><span data-stu-id="c90d6-246">You should be able to make a file that contains Uids.</span></span> <span data-ttu-id="c90d6-247">Za pomocą narzędzia LocBaml, powinno być możliwe przeanalizowanie pliku w celu wyodrębnienia zawartości lokalizowalnej i po przetłumaczeniu zawartości, powinno być możliwe wygenerowanie pliku. resources. dll, który scala przetłumaczoną zawartość.</span><span class="sxs-lookup"><span data-stu-id="c90d6-247">By using the LocBaml tool, you should be able to parse a file to extract the localizable content, and after the content is translated, you should be able to generate a .resources.dll file that merges the translated content.</span></span> <span data-ttu-id="c90d6-248">Ten temat nie zawiera wszystkich szczegółów, ale teraz masz wiedzę niezbędną do lokalizowania aplikacji za pomocą LocBaml.</span><span class="sxs-lookup"><span data-stu-id="c90d6-248">This topic does not include every possible detail, but you now have the knowledge necessary to use LocBaml for localizing your applications.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c90d6-249">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c90d6-249">See also</span></span>

- [<span data-ttu-id="c90d6-250">Globalizacja dla WPF</span><span class="sxs-lookup"><span data-stu-id="c90d6-250">Globalization for WPF</span></span>](globalization-for-wpf.md)
- [<span data-ttu-id="c90d6-251">Przegląd używania automatycznego układu</span><span class="sxs-lookup"><span data-stu-id="c90d6-251">Use Automatic Layout Overview</span></span>](use-automatic-layout-overview.md)
