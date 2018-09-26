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
ms.openlocfilehash: 1190fb739e7c1873532e96b50399ac0deb6bb51c
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/25/2018
ms.locfileid: "47080003"
---
# <a name="how-to-localize-an-application"></a><span data-ttu-id="26398-102">Jak lokalizować aplikację</span><span class="sxs-lookup"><span data-stu-id="26398-102">How to: Localize an Application</span></span>
<span data-ttu-id="26398-103">W tym samouczku opisano sposób tworzenia zlokalizowanych aplikacji przy użyciu locbaml — narzędzie.</span><span class="sxs-lookup"><span data-stu-id="26398-103">This tutorial explains how to create a localized application by using the LocBaml tool.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="26398-104">Locbaml — narzędzie nie jest aplikacją gotowe do produkcji.</span><span class="sxs-lookup"><span data-stu-id="26398-104">The LocBaml tool is not a production-ready application.</span></span> <span data-ttu-id="26398-105">Jest on przedstawiony jako przykład używana część lokalizacji interfejsów API, który ilustruje, w jaki sposób można napisać narzędziem do lokalizacji.</span><span class="sxs-lookup"><span data-stu-id="26398-105">It is presented as a sample that uses some of the localization APIs and illustrates how you might write a localization tool.</span></span>  
  
<a name="Introduction"></a>   
## <a name="overview"></a><span data-ttu-id="26398-106">Omówienie</span><span class="sxs-lookup"><span data-stu-id="26398-106">Overview</span></span>  
 <span data-ttu-id="26398-107">Tej dyskusji zapewnia szczegółowe podejście do lokalizowania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="26398-107">This discussion gives you a step-by-step approach to localizing an application.</span></span> <span data-ttu-id="26398-108">Najpierw zostanie przygotowany aplikacji, dzięki czemu można wyodrębnić tekst, który zostanie zamieniona.</span><span class="sxs-lookup"><span data-stu-id="26398-108">First, you will prepare your application so that the text that will be translated can be extracted.</span></span> <span data-ttu-id="26398-109">Po tekst jest tłumaczony, zostaną scalone przetłumaczonego tekstu do nowej kopii oryginalnej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="26398-109">After the text is translated, you will merge the translated text into a new copy of the original application.</span></span>  
  
<a name="Requirements"></a>   
## <a name="requirements"></a><span data-ttu-id="26398-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="26398-110">Requirements</span></span>  
 <span data-ttu-id="26398-111">W trakcie tej dyskusji, której użyjesz [!INCLUDE[TLA#tla_msbuild](../../../../includes/tlasharptla-msbuild-md.md)], czyli kompilatora, które jest uruchamiane z wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="26398-111">Over the course of this discussion, you will use [!INCLUDE[TLA#tla_msbuild](../../../../includes/tlasharptla-msbuild-md.md)], which is a compiler that runs from the command line.</span></span>  
  
 <span data-ttu-id="26398-112">Ponadto pojawi się instrukcja przy użyciu pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="26398-112">Also, you will be instructed to use a project file.</span></span> <span data-ttu-id="26398-113">Aby uzyskać instrukcje dotyczące sposobu używania [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] i pliki projektu, zobacz [tworzenie i wdrażanie](../../../../docs/framework/wpf/app-development/building-and-deploying-wpf-applications.md).</span><span class="sxs-lookup"><span data-stu-id="26398-113">For instructions on how to use [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] and project files, see [Build and Deploy](../../../../docs/framework/wpf/app-development/building-and-deploying-wpf-applications.md).</span></span>  
  
 <span data-ttu-id="26398-114">Wszystkie przykłady w tej dyskusji pełnić kultury en US (Angielski-Stany Zjednoczone).</span><span class="sxs-lookup"><span data-stu-id="26398-114">All the examples in this discussion use en-US (English-US) as the culture.</span></span> <span data-ttu-id="26398-115">Dzięki temu można pracować kroki przykłady bez konieczności instalowania na inny język.</span><span class="sxs-lookup"><span data-stu-id="26398-115">This enables you to work through the steps of the examples without installing a different language.</span></span>  
  
<a name="create_sample_app"></a>   
## <a name="create-a-sample-application"></a><span data-ttu-id="26398-116">Tworzenie przykładowej aplikacji</span><span class="sxs-lookup"><span data-stu-id="26398-116">Create a Sample Application</span></span>  
 <span data-ttu-id="26398-117">W tym kroku przygotujesz się do lokalizacji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="26398-117">In this step, you will prepare your application for localization.</span></span> <span data-ttu-id="26398-118">W [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] przykłady HelloApp podano przykładowe, który będzie używany dla przykładów kodu w tej dyskusji.</span><span class="sxs-lookup"><span data-stu-id="26398-118">In the [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] samples, a HelloApp sample is supplied that will be used for the code examples in this discussion.</span></span> <span data-ttu-id="26398-119">Jeśli chcesz korzystać z tej próbki, Pobierz [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] plików ze [locbaml — narzędzie przykładowe](https://go.microsoft.com/fwlink/?LinkID=160016).</span><span class="sxs-lookup"><span data-stu-id="26398-119">If you would like to use this sample, download the [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] files from the [LocBaml Tool Sample](https://go.microsoft.com/fwlink/?LinkID=160016).</span></span>  
  
1.  <span data-ttu-id="26398-120">Tworzenie aplikacji do punktu, w którym chcesz uruchomić lokalizacji.</span><span class="sxs-lookup"><span data-stu-id="26398-120">Develop your application to the point where you want to start localization.</span></span>  
  
2.  <span data-ttu-id="26398-121">Wybierz język programowania w pliku projektu, aby [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] generuje głównym zestawie i zestawem satelickim (plik o. resources.dll rozszerzenia) zawierać neutralny język zasobów.</span><span class="sxs-lookup"><span data-stu-id="26398-121">Specify the development language in the project file so that [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] generates a main assembly and a satellite assembly (a file with the .resources.dll extension) to contain the neutral language resources.</span></span> <span data-ttu-id="26398-122">Plik projektu w przykładzie HelloApp jest HelloApp.csproj.</span><span class="sxs-lookup"><span data-stu-id="26398-122">The project file in the HelloApp sample is HelloApp.csproj.</span></span> <span data-ttu-id="26398-123">W tym pliku znajdziesz języka programowania, określone w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="26398-123">In that file, you will find the development language identified as follows:</span></span>  
  
     `<UICulture>en-US</UICulture>`  
  
3.  <span data-ttu-id="26398-124">UID, aby dodać swoje [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] plików.</span><span class="sxs-lookup"><span data-stu-id="26398-124">Add Uids to your [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] files.</span></span> <span data-ttu-id="26398-125">UID są używane do śledzenia zmian w plikach i zidentyfikować elementy, które musi podlegać translacji.</span><span class="sxs-lookup"><span data-stu-id="26398-125">Uids are used to keep track of changes to files and to identify items that must be translated.</span></span> <span data-ttu-id="26398-126">Aby dodać UID do plików, uruchom **updateuid** w pliku projektu:</span><span class="sxs-lookup"><span data-stu-id="26398-126">To add Uids to your files, run **updateuid** on your project file:</span></span>  
  
     <span data-ttu-id="26398-127">**Program MSBuild - t: updateuid helloapp.csproj**</span><span class="sxs-lookup"><span data-stu-id="26398-127">**msbuild -t:updateuid helloapp.csproj**</span></span>  
  
     <span data-ttu-id="26398-128">Aby sprawdzić, czy nie brakuje lub zduplikowane UID, uruchom **checkuid**:</span><span class="sxs-lookup"><span data-stu-id="26398-128">To verify that you have no missing or duplicate Uids, run **checkuid**:</span></span>  
  
     <span data-ttu-id="26398-129">**Program MSBuild - t: checkuid helloapp.csproj**</span><span class="sxs-lookup"><span data-stu-id="26398-129">**msbuild -t:checkuid helloapp.csproj**</span></span>  
  
     <span data-ttu-id="26398-130">Po uruchomieniu **updateuid**, pliki może zawierać UID.</span><span class="sxs-lookup"><span data-stu-id="26398-130">After running **updateuid**, your files should contain Uids.</span></span> <span data-ttu-id="26398-131">Na przykład w pliku Pane1.xaml HelloApp, powinien znajdować się następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="26398-131">For example, in the Pane1.xaml file of HelloApp, you should find the following:</span></span>  
  
     `<StackPanel x:Uid="StackPanel_1">`  
  
     `<TextBlock x:Uid="TextBlock_1">Hello World</TextBlock>`  
  
     `<TextBlock x:Uid="TextBlock_2">Goodbye World</TextBlock>`  
  
     `</StackPanel>`  
  
<a name="create_dll"></a>   
## <a name="create-the-neutral-language-resources-satellite-assembly"></a><span data-ttu-id="26398-132">Tworzenie zestawu satelickiego neutralny język zasobów</span><span class="sxs-lookup"><span data-stu-id="26398-132">Create the Neutral Language Resources Satellite Assembly</span></span>  
 <span data-ttu-id="26398-133">Po skonfigurowaniu aplikacji do generowania zestawu satelickiego neutralny język zasobów kompilacji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="26398-133">After the application is configured to generate a neutral language resources satellite assembly, you build the application.</span></span> <span data-ttu-id="26398-134">Spowoduje to wygenerowanie zestawie aplikacji głównej, a także zestawu satelickiego neutralny język zasobów, wymaganego przez locbaml — dla lokalizacji.</span><span class="sxs-lookup"><span data-stu-id="26398-134">This generates the main application assembly, as well as the neutral language resources satellite assembly that is required by LocBaml for localization.</span></span> <span data-ttu-id="26398-135">Aby skompilować aplikację:</span><span class="sxs-lookup"><span data-stu-id="26398-135">To build the application:</span></span>  
  
1.  <span data-ttu-id="26398-136">Skompilować HelloApp, aby utworzyć [!INCLUDE[TLA#tla_dll](../../../../includes/tlasharptla-dll-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="26398-136">Compile HelloApp to create a [!INCLUDE[TLA#tla_dll](../../../../includes/tlasharptla-dll-md.md)]:</span></span>  
  
     <span data-ttu-id="26398-137">**MSBUILD helloapp.csproj**</span><span class="sxs-lookup"><span data-stu-id="26398-137">**msbuild helloapp.csproj**</span></span>  
  
2.  <span data-ttu-id="26398-138">Nowo utworzony głównym zestawem aplikacji, HelloApp.exe, jest tworzony w następującym folderze:</span><span class="sxs-lookup"><span data-stu-id="26398-138">The newly created main application assembly, HelloApp.exe, is created in the following folder:</span></span>  
  
     `C:\HelloApp\Bin\Debug\`  
  
3.  <span data-ttu-id="26398-139">Zestawu satelickiego zasobów nowo utworzony neutralnym językiem, HelloApp.resources.dll, jest tworzony w następującym folderze:</span><span class="sxs-lookup"><span data-stu-id="26398-139">The newly created neutral language resources satellite assembly, HelloApp.resources.dll, is created in the following folder:</span></span>  
  
     `C:\HelloApp\Bin\Debug\en-US\`  
  
<a name="build_locbaml"></a>   
## <a name="build-the-locbaml-tool"></a><span data-ttu-id="26398-140">Tworzenie locbaml — narzędzie</span><span class="sxs-lookup"><span data-stu-id="26398-140">Build the LocBaml Tool</span></span>  
  
1.  <span data-ttu-id="26398-141">Wszystkie pliki niezbędne do utworzenia locbaml — znajdują się w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] przykładów.</span><span class="sxs-lookup"><span data-stu-id="26398-141">All the files necessary to build LocBaml are located in the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] samples.</span></span> <span data-ttu-id="26398-142">Pobierz pliki C# z [locbaml — narzędzie przykładowe](https://go.microsoft.com/fwlink/?LinkID=160016).</span><span class="sxs-lookup"><span data-stu-id="26398-142">Download the C# files from the [LocBaml Tool Sample](https://go.microsoft.com/fwlink/?LinkID=160016).</span></span>  
  
2.  <span data-ttu-id="26398-143">Uruchom plik projektu (locbaml.csproj) do skompilowania narzędzie z wiersza polecenia:</span><span class="sxs-lookup"><span data-stu-id="26398-143">From the command line, run the project file (locbaml.csproj) to build the tool:</span></span>  
  
     <span data-ttu-id="26398-144">**MSBUILD locbaml.csproj**</span><span class="sxs-lookup"><span data-stu-id="26398-144">**msbuild locbaml.csproj**</span></span>  
  
3.  <span data-ttu-id="26398-145">Przejdź do katalogu Bin\Release, aby znaleźć nowo utworzony plik wykonywalny (locbaml.exe).</span><span class="sxs-lookup"><span data-stu-id="26398-145">Go to the Bin\Release directory to find the newly created executable file (locbaml.exe).</span></span> <span data-ttu-id="26398-146">Example:C:\LocBaml\Bin\Release\locbaml.exe.</span><span class="sxs-lookup"><span data-stu-id="26398-146">Example:C:\LocBaml\Bin\Release\locbaml.exe.</span></span>  
  
4.  <span data-ttu-id="26398-147">Dostępne są następujące opcje, które można określić po uruchomieniu locbaml —:</span><span class="sxs-lookup"><span data-stu-id="26398-147">The options that you can specify when you run LocBaml are as follows:</span></span>  
  
    -   <span data-ttu-id="26398-148">**analizowanie** lub **-p:** analizuje Baml zasobów, lub [!INCLUDE[TLA2#tla_dll](../../../../includes/tla2sharptla-dll-md.md)] plików, aby wygenerować plik CSV lub txt.</span><span class="sxs-lookup"><span data-stu-id="26398-148">**parse** or **-p:** Parses Baml, resources, or [!INCLUDE[TLA2#tla_dll](../../../../includes/tla2sharptla-dll-md.md)] files to generate a .csv or .txt file.</span></span>  
  
    -   <span data-ttu-id="26398-149">**Generowanie** lub **-g:** generuje zlokalizowany plik binarny, używając przetłumaczonego pliku.</span><span class="sxs-lookup"><span data-stu-id="26398-149">**generate** or **-g:** Generates a localized binary file by using a translated file.</span></span>  
  
    -   <span data-ttu-id="26398-150">**limit** lub **-o** {*filedirectory*] **:** nazwa pliku wyjściowego.</span><span class="sxs-lookup"><span data-stu-id="26398-150">**out** or **-o** {*filedirectory*] **:** Output file name.</span></span>  
  
    -   <span data-ttu-id="26398-151">**kultura** lub **- cul** {*kultury*] **:** ustawień regionalnych, zestawów danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="26398-151">**culture** or **-cul** {*culture*] **:** Locale of output assemblies.</span></span>  
  
    -   <span data-ttu-id="26398-152">**Tłumaczenie** lub **- trans** {*translation.csv*] **:** przetłumaczona lub zlokalizowanego pliku.</span><span class="sxs-lookup"><span data-stu-id="26398-152">**translation** or **-trans** {*translation.csv*] **:** Translated or localized file.</span></span>  
  
    -   <span data-ttu-id="26398-153">**asmpath** lub **- asmpath:** {*filedirectory*] **:** Jeśli Twoje [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] kod zawiera kontrolki niestandardowe, należy podać  **asmpath** do zestawu kontrolki niestandardowej.</span><span class="sxs-lookup"><span data-stu-id="26398-153">**asmpath** or **-asmpath:** {*filedirectory*] **:** If your [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] code contains custom controls, you must supply the **asmpath** to the custom control assembly.</span></span>  
  
    -   <span data-ttu-id="26398-154">**nologo:** wyświetlane żadne informacje logo lub praw autorskich.</span><span class="sxs-lookup"><span data-stu-id="26398-154">**nologo:** Displays no logo or copyright information.</span></span>  
  
    -   <span data-ttu-id="26398-155">**verbose:** Wyświetla informacje o trybie informacji pełnej.</span><span class="sxs-lookup"><span data-stu-id="26398-155">**verbose:** Displays verbose mode information.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="26398-156">Jeśli potrzebujesz listę opcji, gdy uruchamiasz narzędzie, należy wpisać **LocBaml.exe** i naciśnij klawisz ENTER.</span><span class="sxs-lookup"><span data-stu-id="26398-156">If you need a list of the options when you are running the tool, type     **LocBaml.exe** and press ENTER.</span></span>  
  
<a name="parse_dll"></a>   
## <a name="use-locbaml-to-parse-a-file"></a><span data-ttu-id="26398-157">Locbaml — Użyj, aby analizować plik</span><span class="sxs-lookup"><span data-stu-id="26398-157">Use LocBaml to Parse a File</span></span>  
 <span data-ttu-id="26398-158">Teraz, po utworzeniu locbaml — narzędzie, jesteś gotowy na potrzeby analizowania HelloApp.resources.dll, aby wyodrębnić zawartość tekstu, który zostanie zlokalizowany.</span><span class="sxs-lookup"><span data-stu-id="26398-158">Now that you have created the LocBaml tool, you are ready to use it to parse HelloApp.resources.dll to extract the text content that will be localized.</span></span>  
  
1.  <span data-ttu-id="26398-159">Skopiuj LocBaml.exe do folderu bin\debug aplikacji, w której utworzono zestawu głównej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="26398-159">Copy LocBaml.exe to your application's bin\debug folder, where the main application assembly was created.</span></span>  
  
2.  <span data-ttu-id="26398-160">Aby przeanalizować plik zestawu satelickiego i przechowywanie danych wyjściowych w formacie pliku CSV, użyj następującego polecenia:</span><span class="sxs-lookup"><span data-stu-id="26398-160">To parse the satellite assembly file and store the output as a .csv file, use the following command:</span></span>  
  
     <span data-ttu-id="26398-161">**/Parse LocBaml.exe HelloApp.resources.dll /out:Hello.csv**</span><span class="sxs-lookup"><span data-stu-id="26398-161">**LocBaml.exe /parse HelloApp.resources.dll /out:Hello.csv**</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="26398-162">Jeśli plik wejściowy HelloApp.resources.dll, nie znajduje się w tym samym katalogu co LocBaml.exe przenieść jeden z plików, tak aby oba pliki znajdują się w tym samym katalogu.</span><span class="sxs-lookup"><span data-stu-id="26398-162">If the input file, HelloApp.resources.dll, is not in the same directory as LocBaml.exe move one of the files so that both files are in the same directory.</span></span>  
  
3.  <span data-ttu-id="26398-163">Po uruchomieniu locbaml — można przeanalizować pliki, dane wyjściowe składa się z siedmiu pól rozdzielonych przecinkami (.csv pliki) lub kart (txt).</span><span class="sxs-lookup"><span data-stu-id="26398-163">When you run LocBaml to parse files, the output consists of seven fields delimited by commas (.csv files) or tabs (.txt files).</span></span> <span data-ttu-id="26398-164">Poniżej przedstawiono plik CSV przeanalizowany HelloApp.resources.dll:</span><span class="sxs-lookup"><span data-stu-id="26398-164">The following shows the parsed .csv file for the HelloApp.resources.dll:</span></span>

   | |
   |-|
   |<span data-ttu-id="26398-165">HelloApp.g.en US.resources:window1.baml, Stack1:System.Windows.Controls.StackPanel. $Content, zignorować, FALSE, FALSE,, #Text1; # Tekst2;</span><span class="sxs-lookup"><span data-stu-id="26398-165">HelloApp.g.en-US.resources:window1.baml,Stack1:System.Windows.Controls.StackPanel.$Content,Ignore,FALSE, FALSE,,#Text1;#Text2;</span></span>|
   |<span data-ttu-id="26398-166">HelloApp.g.en US.resources:window1.baml, Text1:System.Windows.Controls.TextBlock. $Content, None, wartość TRUE, TRUE,, Hello World</span><span class="sxs-lookup"><span data-stu-id="26398-166">HelloApp.g.en-US.resources:window1.baml,Text1:System.Windows.Controls.TextBlock.$Content,None,TRUE, TRUE,,Hello World</span></span>|
   |<span data-ttu-id="26398-167">HelloApp.g.en US.resources:window1.baml, Text2:System.Windows.Controls.TextBlock. $Content, None, wartość TRUE, TRUE,, Goodbye świata</span><span class="sxs-lookup"><span data-stu-id="26398-167">HelloApp.g.en-US.resources:window1.baml,Text2:System.Windows.Controls.TextBlock.$Content,None,TRUE, TRUE,,Goodbye World</span></span>|

   <span data-ttu-id="26398-168">Siedem pola są:</span><span class="sxs-lookup"><span data-stu-id="26398-168">The seven fields are:</span></span>  
  
   1.  <span data-ttu-id="26398-169">**Nazwa BAML**.</span><span class="sxs-lookup"><span data-stu-id="26398-169">**BAML Name**.</span></span> <span data-ttu-id="26398-170">Nazwa zasobu BAML w odniesieniu do zestawu satelickiego języka źródłowego.</span><span class="sxs-lookup"><span data-stu-id="26398-170">The name of the BAML resource with respect to the source language satellite assembly.</span></span>  
  
   2.  <span data-ttu-id="26398-171">**Klucz zasobu**.</span><span class="sxs-lookup"><span data-stu-id="26398-171">**Resource Key**.</span></span> <span data-ttu-id="26398-172">Identyfikator zlokalizowanych zasobów.</span><span class="sxs-lookup"><span data-stu-id="26398-172">The localized resource identifier.</span></span>  
  
   3.  <span data-ttu-id="26398-173">**Kategoria**.</span><span class="sxs-lookup"><span data-stu-id="26398-173">**Category**.</span></span> <span data-ttu-id="26398-174">Typ wartości.</span><span class="sxs-lookup"><span data-stu-id="26398-174">The value type.</span></span> <span data-ttu-id="26398-175">Zobacz [lokalizacja atrybutów i komentarzy](../../../../docs/framework/wpf/advanced/localization-attributes-and-comments.md).</span><span class="sxs-lookup"><span data-stu-id="26398-175">See [Localization Attributes and Comments](../../../../docs/framework/wpf/advanced/localization-attributes-and-comments.md).</span></span>  
  
   4.  <span data-ttu-id="26398-176">**Czytelność**.</span><span class="sxs-lookup"><span data-stu-id="26398-176">**Readability**.</span></span> <span data-ttu-id="26398-177">Czy można odczytać wartości przez lokalizatorowi.</span><span class="sxs-lookup"><span data-stu-id="26398-177">Whether the value can be read by a localizer.</span></span> <span data-ttu-id="26398-178">Zobacz [lokalizacja atrybutów i komentarzy](../../../../docs/framework/wpf/advanced/localization-attributes-and-comments.md).</span><span class="sxs-lookup"><span data-stu-id="26398-178">See [Localization Attributes and Comments](../../../../docs/framework/wpf/advanced/localization-attributes-and-comments.md).</span></span>  
  
   5.  <span data-ttu-id="26398-179">**Modifiability**.</span><span class="sxs-lookup"><span data-stu-id="26398-179">**Modifiability**.</span></span> <span data-ttu-id="26398-180">Czy wartość może być modyfikowany przez lokalizatorowi.</span><span class="sxs-lookup"><span data-stu-id="26398-180">Whether the value can be modified by a localizer.</span></span> <span data-ttu-id="26398-181">Zobacz [lokalizacja atrybutów i komentarzy](../../../../docs/framework/wpf/advanced/localization-attributes-and-comments.md).</span><span class="sxs-lookup"><span data-stu-id="26398-181">See [Localization Attributes and Comments](../../../../docs/framework/wpf/advanced/localization-attributes-and-comments.md).</span></span>  
  
   6.  <span data-ttu-id="26398-182">**Komentarze**.</span><span class="sxs-lookup"><span data-stu-id="26398-182">**Comments**.</span></span> <span data-ttu-id="26398-183">Dodatkowy opis wartości w celu określenia, jak wartość jest zlokalizowana.</span><span class="sxs-lookup"><span data-stu-id="26398-183">Additional description of the value to help determine how a value is localized.</span></span> <span data-ttu-id="26398-184">Zobacz [lokalizacja atrybutów i komentarzy](../../../../docs/framework/wpf/advanced/localization-attributes-and-comments.md).</span><span class="sxs-lookup"><span data-stu-id="26398-184">See [Localization Attributes and Comments](../../../../docs/framework/wpf/advanced/localization-attributes-and-comments.md).</span></span>  
  
   7.  <span data-ttu-id="26398-185">**Wartość**.</span><span class="sxs-lookup"><span data-stu-id="26398-185">**Value**.</span></span> <span data-ttu-id="26398-186">Wartość tekstowa do translacji na żądaną kulturę.</span><span class="sxs-lookup"><span data-stu-id="26398-186">The text value to translate to the desired culture.</span></span>  
  
   <span data-ttu-id="26398-187">W poniższej tabeli przedstawiono sposób mapowania tych pól do wartości rozdzielanego pliku CSV:</span><span class="sxs-lookup"><span data-stu-id="26398-187">The following table shows how these fields map to the delimited values of the .csv file:</span></span>  
  
   |<span data-ttu-id="26398-188">Nazwa BAML</span><span class="sxs-lookup"><span data-stu-id="26398-188">BAML name</span></span>|<span data-ttu-id="26398-189">Klucz zasobu</span><span class="sxs-lookup"><span data-stu-id="26398-189">Resource key</span></span>|<span data-ttu-id="26398-190">Kategoria</span><span class="sxs-lookup"><span data-stu-id="26398-190">Category</span></span>|<span data-ttu-id="26398-191">Czytelność</span><span class="sxs-lookup"><span data-stu-id="26398-191">Readability</span></span>|<span data-ttu-id="26398-192">Modifiability</span><span class="sxs-lookup"><span data-stu-id="26398-192">Modifiability</span></span>|<span data-ttu-id="26398-193">Komentarze</span><span class="sxs-lookup"><span data-stu-id="26398-193">Comments</span></span>|<span data-ttu-id="26398-194">Wartość</span><span class="sxs-lookup"><span data-stu-id="26398-194">Value</span></span>|  
   |---------------|------------------|--------------|-----------------|-------------------|--------------|-----------|
   |<span data-ttu-id="26398-195">HelloApp.g.en US.resources:window1.baml</span><span class="sxs-lookup"><span data-stu-id="26398-195">HelloApp.g.en-US.resources:window1.baml</span></span>|<span data-ttu-id="26398-196">Stack1:system.Windows.Controls.StackPanel.$Content</span><span class="sxs-lookup"><span data-stu-id="26398-196">Stack1:System.Windows.Controls.StackPanel.$Content</span></span>|<span data-ttu-id="26398-197">Ignoruj</span><span class="sxs-lookup"><span data-stu-id="26398-197">Ignore</span></span>|<span data-ttu-id="26398-198">FAŁSZ</span><span class="sxs-lookup"><span data-stu-id="26398-198">FALSE</span></span>|<span data-ttu-id="26398-199">FAŁSZ</span><span class="sxs-lookup"><span data-stu-id="26398-199">FALSE</span></span>||<span data-ttu-id="26398-200">#Text1; # Tekst2</span><span class="sxs-lookup"><span data-stu-id="26398-200">#Text1;#Text2</span></span>|
   |<span data-ttu-id="26398-201">HelloApp.g.en US.resources:window1.baml</span><span class="sxs-lookup"><span data-stu-id="26398-201">HelloApp.g.en-US.resources:window1.baml</span></span>|<span data-ttu-id="26398-202">Text1:system.Windows.Controls.TextBlock.$Content</span><span class="sxs-lookup"><span data-stu-id="26398-202">Text1:System.Windows.Controls.TextBlock.$Content</span></span>|<span data-ttu-id="26398-203">Brak</span><span class="sxs-lookup"><span data-stu-id="26398-203">None</span></span>|<span data-ttu-id="26398-204">WARTOŚĆ TRUE</span><span class="sxs-lookup"><span data-stu-id="26398-204">TRUE</span></span>|<span data-ttu-id="26398-205">WARTOŚĆ TRUE</span><span class="sxs-lookup"><span data-stu-id="26398-205">TRUE</span></span>||<span data-ttu-id="26398-206">Witaj Świecie</span><span class="sxs-lookup"><span data-stu-id="26398-206">Hello World</span></span>|
   |<span data-ttu-id="26398-207">HelloApp.g.en US.resources:window1.baml</span><span class="sxs-lookup"><span data-stu-id="26398-207">HelloApp.g.en-US.resources:window1.baml</span></span>|<span data-ttu-id="26398-208">Text2:system.Windows.Controls.TextBlock.$Content</span><span class="sxs-lookup"><span data-stu-id="26398-208">Text2:System.Windows.Controls.TextBlock.$Content</span></span>|<span data-ttu-id="26398-209">Brak</span><span class="sxs-lookup"><span data-stu-id="26398-209">None</span></span>|<span data-ttu-id="26398-210">WARTOŚĆ TRUE</span><span class="sxs-lookup"><span data-stu-id="26398-210">TRUE</span></span>|<span data-ttu-id="26398-211">WARTOŚĆ TRUE</span><span class="sxs-lookup"><span data-stu-id="26398-211">TRUE</span></span>||<span data-ttu-id="26398-212">Goodbye świata</span><span class="sxs-lookup"><span data-stu-id="26398-212">Goodbye World</span></span>|
  
   <span data-ttu-id="26398-213">Należy zauważyć, że wszystkie wartości dla **komentarze** pola nie zawierają wartości; Jeśli pola nie ma wartości, jest pusty.</span><span class="sxs-lookup"><span data-stu-id="26398-213">Notice that all the values for the **Comments** field contain no values; if a field doesn't have a value, it is empty.</span></span> <span data-ttu-id="26398-214">Także zauważyć, że elementu w pierwszym wierszu nie można odczytać ani można modyfikować oraz "Ignorowania" jako jego **kategorii** wartości, które wskazuje, że wartość jest możliwych do zlokalizowania.</span><span class="sxs-lookup"><span data-stu-id="26398-214">Also notice that the item in the first row is neither readable nor modifiable, and has "Ignore" as its **Category** value, all of which indicates that the value is not localizable.</span></span>  
  
4.  <span data-ttu-id="26398-215">Ułatwiają odnajdowanie elementów możliwych do zlokalizowania w plikach przeanalizowany, szczególnie w dużych plików, można sortować i filtrować elementy według **kategorii**, **czytelność**, i **Modifiability**.</span><span class="sxs-lookup"><span data-stu-id="26398-215">To facilitate discovery of localizable items in parsed files, particularly in large files, you can sort or filter the items by **Category**, **Readability**, and **Modifiability**.</span></span> <span data-ttu-id="26398-216">Na przykład można odfiltrować wartości nie można go odczytać i niemodyfikowalnych.</span><span class="sxs-lookup"><span data-stu-id="26398-216">For example, you can filter out unreadable and unmodifiable values.</span></span>  
  
<a name="translate_loc_content"></a>   
## <a name="translate-the-localizable-content"></a><span data-ttu-id="26398-217">Tłumaczenie możliwych do zlokalizowania zawartości</span><span class="sxs-lookup"><span data-stu-id="26398-217">Translate the Localizable Content</span></span>  
 <span data-ttu-id="26398-218">Za pomocą dowolnego narzędzia dostępne do translacji wyodrębnionej zawartości.</span><span class="sxs-lookup"><span data-stu-id="26398-218">Use any tool that you have available to translate the extracted content.</span></span> <span data-ttu-id="26398-219">Dobrym sposobem na to jest napisanie pliku zasobów do pliku CSV i wyświetlić je w [!INCLUDE[TLA#tla_xl](../../../../includes/tlasharptla-xl-md.md)], co tłumaczenia ostatnio zmiany kolumny (wartość).</span><span class="sxs-lookup"><span data-stu-id="26398-219">A good way to do this is to write the resources to a .csv file and view them in [!INCLUDE[TLA#tla_xl](../../../../includes/tlasharptla-xl-md.md)], making translation changes to the last column (value).</span></span>  
  
<a name="merge_translations"></a>   
## <a name="use-locbaml-to-generate-a-new-resourcesdll-file"></a><span data-ttu-id="26398-220">Użyj locbaml —, aby wygenerować nowy. resources.dll pliku</span><span class="sxs-lookup"><span data-stu-id="26398-220">Use LocBaml to Generate a New .resources.dll File</span></span>  
 <span data-ttu-id="26398-221">Zawartość, który został zidentyfikowany przez analizowanie HelloApp.resources.dll z locbaml — został przetłumaczony i musi być scalone oryginalnej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="26398-221">The content that was identified by parsing HelloApp.resources.dll with LocBaml has been translated and must be merged back into the original application.</span></span> <span data-ttu-id="26398-222">Użyj **Generowanie** lub **-g** opcję, aby wygenerować nowy. resources.dll pliku.</span><span class="sxs-lookup"><span data-stu-id="26398-222">Use the **generate** or **-g** option to generate a new .resources.dll file.</span></span>  
  
1.  <span data-ttu-id="26398-223">Użyj następującej składni, aby wygenerować nowy plik HelloApp.resources.dll.</span><span class="sxs-lookup"><span data-stu-id="26398-223">Use the following syntax to generate a new HelloApp.resources.dll file.</span></span> <span data-ttu-id="26398-224">Oznacz kulturę, co en US (/ cul:en — Stany Zjednoczone).</span><span class="sxs-lookup"><span data-stu-id="26398-224">Mark the culture as en-US (/cul:en-US).</span></span>  
  
     <span data-ttu-id="26398-225">**LocBaml.exe / Generowanie HelloApp.resources.dll /trans:Hello.csv /out:c: \ /cul:en — Stany Zjednoczone**</span><span class="sxs-lookup"><span data-stu-id="26398-225">**LocBaml.exe /generate HelloApp.resources.dll /trans:Hello.csv /out:c:\ /cul:en-US**</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="26398-226">Jeśli plik wejściowy Hello.csv, nie jest w tym samym katalogu co plik wykonywalny LocBaml.exe, należy przenieść jeden z plików tak, aby oba pliki znajdują się w tym samym katalogu.</span><span class="sxs-lookup"><span data-stu-id="26398-226">If the input file, Hello.csv, is not in the same directory as the executable, LocBaml.exe, move one of the files so that both files are in the same directory.</span></span>  
  
2.  <span data-ttu-id="26398-227">Zastąp starego pliku HelloApp.resources.dll w katalogu C:\HelloApp\Bin\Debug\en-US\HelloApp.resources.dll nowo utworzony plik HelloApp.resources.dll.</span><span class="sxs-lookup"><span data-stu-id="26398-227">Replace the old HelloApp.resources.dll file in the C:\HelloApp\Bin\Debug\en-US\HelloApp.resources.dll directory with your newly created HelloApp.resources.dll file.</span></span>  
  
3.  <span data-ttu-id="26398-228">"Hello World" i "Goodbye World" powinien teraz przetłumaczony na aplikację.</span><span class="sxs-lookup"><span data-stu-id="26398-228">"Hello World" and "Goodbye World" should now be translated in your application.</span></span>  
  
4.  <span data-ttu-id="26398-229">Do tłumaczenia, aby określić inną kulturę, używają kultury języka, który tłumaczy do.</span><span class="sxs-lookup"><span data-stu-id="26398-229">To translate to a different culture, use the culture of the language that you are translating to.</span></span> <span data-ttu-id="26398-230">Poniższy przykład pokazuje, jak przełożyć na French-Canadian:</span><span class="sxs-lookup"><span data-stu-id="26398-230">The following example shows how to translate to French-Canadian:</span></span>  
  
     <span data-ttu-id="26398-231">**LocBaml.exe / Generowanie HelloApp.resources.dll /trans:Hellofr-CA.csv /out:c: \ /cul:fr-urzędu certyfikacji**</span><span class="sxs-lookup"><span data-stu-id="26398-231">**LocBaml.exe /generate HelloApp.resources.dll /trans:Hellofr-CA.csv /out:c:\ /cul:fr-CA**</span></span>  
  
5.  <span data-ttu-id="26398-232">Z tego samego zestawu jako zestawu głównej aplikacji Utwórz nowy folder specyficzne dla kultury do przechowywania nowego zestawu satelickiego.</span><span class="sxs-lookup"><span data-stu-id="26398-232">In the same assembly as the main application assembly, create a new culture-specific folder to house the new satellite assembly.</span></span> <span data-ttu-id="26398-233">French-Canadian folder będzie fr-CA.</span><span class="sxs-lookup"><span data-stu-id="26398-233">For French-Canadian, the folder would be fr-CA.</span></span>  
  
6.  <span data-ttu-id="26398-234">Skopiuj wygenerowany satelicki do nowego folderu.</span><span class="sxs-lookup"><span data-stu-id="26398-234">Copy the generated satellite assembly to the new folder.</span></span>  
  
7.  <span data-ttu-id="26398-235">Aby przetestować nowego zestawu satelickiego, musisz zmienić kulturę, w którym aplikacja jest uruchamiana.</span><span class="sxs-lookup"><span data-stu-id="26398-235">To test the new satellite assembly, you need to change the culture under which your application will run.</span></span> <span data-ttu-id="26398-236">Można to zrobić na jeden z dwóch sposobów:</span><span class="sxs-lookup"><span data-stu-id="26398-236">You can do this in one of two ways:</span></span>  
  
    -   <span data-ttu-id="26398-237">Zmień ustawienia regionalne systemu operacyjnego (**Start** &#124; **Panelu sterowania** &#124; **Opcje regionalne i językowe**).</span><span class="sxs-lookup"><span data-stu-id="26398-237">Change your operating system's regional settings (**Start** &#124; **Control Panel** &#124; **Regional and Language Options**).</span></span>  
  
    -   <span data-ttu-id="26398-238">W aplikacji Dodaj następujący kod do pliku App.xaml.cs:</span><span class="sxs-lookup"><span data-stu-id="26398-238">In your application, add the following code to App.xaml.cs:</span></span>  
  
   [!code-xaml[LocBamlChangeCultureSnippets#LocBamlChangeCultureMARKUP](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LocBamlChangeCultureSnippets/CSharp/App.xaml#locbamlchangeculturemarkup)]
   [!code-csharp[LocBamlChangeCultureSnippets#LocBamlChangeCultureCODEBEHIND](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LocBamlChangeCultureSnippets/CSharp/App.xaml.cs#locbamlchangeculturecodebehind)]
   [!code-vb[LocBamlChangeCultureSnippets#LocBamlChangeCultureCODEBEHIND](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/LocBamlChangeCultureSnippets/VisualBasic/Application.xaml.vb#locbamlchangeculturecodebehind)]  
  
<a name="Some_Tips_for_Using_LocBaml"></a>   
## <a name="some-tips-for-using-locbaml"></a><span data-ttu-id="26398-239">Wskazówki dotyczące korzystania z locbaml —</span><span class="sxs-lookup"><span data-stu-id="26398-239">Some Tips for Using LocBaml</span></span>  
  
-   <span data-ttu-id="26398-240">Wszystkie zależne zestawy, które definiują niestandardowe formanty, musi być skopiowany do katalogu lokalnego locbaml — lub zainstalowane w GAC.</span><span class="sxs-lookup"><span data-stu-id="26398-240">All dependent assemblies that define custom controls must be copied into the local directory of LocBaml or installed into the GAC.</span></span> <span data-ttu-id="26398-241">Jest to konieczne, ponieważ lokalizacja interfejsu API musi mieć dostęp do zestawów zależnych, gdy odczytuje [!INCLUDE[TLA#tla_baml](../../../../includes/tlasharptla-baml-md.md)].</span><span class="sxs-lookup"><span data-stu-id="26398-241">This is necessary because the localization API must have access to the dependent assemblies when it reads the [!INCLUDE[TLA#tla_baml](../../../../includes/tlasharptla-baml-md.md)].</span></span>  
  
-   <span data-ttu-id="26398-242">Jeśli główny zestaw jest podpisany, wygenerowany Biblioteka DLL zasobu, również muszą być podpisane w celu użycia go do załadowania.</span><span class="sxs-lookup"><span data-stu-id="26398-242">If the main assembly is signed, the generated resource DLL must also be signed in order for it to be loaded.</span></span>  
  
-   <span data-ttu-id="26398-243">Wersja zlokalizowanych zasobów biblioteki DLL muszą być zsynchronizowane z zestawu głównego.</span><span class="sxs-lookup"><span data-stu-id="26398-243">The version of the localized resource DLL needs to be synchronized with the main assembly.</span></span>  
  
<a name="Whats_Next"></a>   
## <a name="whats-next"></a><span data-ttu-id="26398-244">Jaka jest przyszłość</span><span class="sxs-lookup"><span data-stu-id="26398-244">What's Next</span></span>  
 <span data-ttu-id="26398-245">Teraz powinien mieć podstawową wiedzę na temat sposobu użycia locbaml — narzędzie.</span><span class="sxs-lookup"><span data-stu-id="26398-245">You should now have a basic understanding of how to use the LocBaml tool.</span></span>  <span data-ttu-id="26398-246">Powinien móc plik, który zawiera UID.</span><span class="sxs-lookup"><span data-stu-id="26398-246">You should be able to make a file that contains Uids.</span></span> <span data-ttu-id="26398-247">Za pomocą locbaml — narzędzie, można przeanalizować pliku można wyodrębnić możliwych do zlokalizowania zawartości, a po zawartość jest tłumaczona, powinno być możliwe wygenerowanie. resources.dll zawierający scala tłumaczonej zawartości.</span><span class="sxs-lookup"><span data-stu-id="26398-247">By using the LocBaml tool, you should be able to parse a file to extract the localizable content, and after the content is translated, you should be able to generate a .resources.dll file that merges the translated content.</span></span> <span data-ttu-id="26398-248">W tym temacie nie ma możliwości szczegóły każdego zdarzenia, ale masz teraz wiedzy koniecznych do używania locbaml — do lokalizowania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="26398-248">This topic does not include every possible detail, but you now have the knowledge necessary to use LocBaml for localizing your applications.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="26398-249">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="26398-249">See Also</span></span>  
 [<span data-ttu-id="26398-250">Globalizacja dla WPF</span><span class="sxs-lookup"><span data-stu-id="26398-250">Globalization for WPF</span></span>](../../../../docs/framework/wpf/advanced/globalization-for-wpf.md)  
 [<span data-ttu-id="26398-251">Przegląd używania automatycznego układu</span><span class="sxs-lookup"><span data-stu-id="26398-251">Use Automatic Layout Overview</span></span>](../../../../docs/framework/wpf/advanced/use-automatic-layout-overview.md)
