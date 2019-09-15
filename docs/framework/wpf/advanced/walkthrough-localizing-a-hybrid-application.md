---
title: 'Przewodnik: lokalizowanie aplikacji hybrydowej'
ms.date: 08/18/2018
helpviewer_keywords:
- localization [WPF interoperability]
- hybrid applications [WPF interoperability]
ms.assetid: fbc0c54e-930a-4c13-8e9c-27b83665010a
ms.openlocfilehash: b98bf7b3f0aa4e7698a5c0ca7c8ae16051ce6300
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/14/2019
ms.locfileid: "70991774"
---
# <a name="walkthrough-localizing-a-hybrid-application"></a><span data-ttu-id="6ba46-102">Przewodnik: lokalizowanie aplikacji hybrydowej</span><span class="sxs-lookup"><span data-stu-id="6ba46-102">Walkthrough: Localizing a Hybrid Application</span></span>

<span data-ttu-id="6ba46-103">W tym instruktażu pokazano, jak lokalizować [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] elementy w aplikacjihybrydowejopartejnabazie.[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6ba46-103">This walkthrough shows you how to localize [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] elements in a [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]-based hybrid application.</span></span>

<span data-ttu-id="6ba46-104">Zadania przedstawione w tym instruktażu obejmują:</span><span class="sxs-lookup"><span data-stu-id="6ba46-104">Tasks illustrated in this walkthrough include:</span></span>

- <span data-ttu-id="6ba46-105">Tworzenie projektu [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] hosta.</span><span class="sxs-lookup"><span data-stu-id="6ba46-105">Creating the [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] host project.</span></span>

- <span data-ttu-id="6ba46-106">Dodawanie lokalizowalnej zawartości.</span><span class="sxs-lookup"><span data-stu-id="6ba46-106">Adding localizable content.</span></span>

- <span data-ttu-id="6ba46-107">Włączanie lokalizacji.</span><span class="sxs-lookup"><span data-stu-id="6ba46-107">Enabling localization.</span></span>

- <span data-ttu-id="6ba46-108">Przypisywanie identyfikatorów zasobów.</span><span class="sxs-lookup"><span data-stu-id="6ba46-108">Assigning resource identifiers.</span></span>

- <span data-ttu-id="6ba46-109">Używanie narzędzia LocBaml do tworzenia zestawu satelickiego.</span><span class="sxs-lookup"><span data-stu-id="6ba46-109">Using the LocBaml tool to produce a satellite assembly.</span></span>

<span data-ttu-id="6ba46-110">Aby uzyskać pełną listę kodu zadań przedstawionych w tym przewodniku, zobacz [lokalizowanie przykładowej aplikacji hybrydowej](https://go.microsoft.com/fwlink/?LinkID=160015).</span><span class="sxs-lookup"><span data-stu-id="6ba46-110">For a complete code listing of the tasks illustrated in this walkthrough, see [Localizing a Hybrid Application Sample](https://go.microsoft.com/fwlink/?LinkID=160015).</span></span>

<span data-ttu-id="6ba46-111">Po zakończeniu będziesz mieć zlokalizowaną aplikację hybrydową.</span><span class="sxs-lookup"><span data-stu-id="6ba46-111">When you are finished, you will have a localized hybrid application.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="6ba46-112">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="6ba46-112">Prerequisites</span></span>

<span data-ttu-id="6ba46-113">Następujące składniki są wymagane do przeprowadzenia tego instruktażu:</span><span class="sxs-lookup"><span data-stu-id="6ba46-113">You need the following components to complete this walkthrough:</span></span>

- <span data-ttu-id="6ba46-114">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="6ba46-114">Visual Studio 2017</span></span>

## <a name="creating-the-windows-forms-host-project"></a><span data-ttu-id="6ba46-115">Tworzenie projektu hosta Windows Forms</span><span class="sxs-lookup"><span data-stu-id="6ba46-115">Creating the Windows Forms Host Project</span></span>

<span data-ttu-id="6ba46-116">Pierwszym krokiem jest utworzenie [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] projektu aplikacji i [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] dodanie elementu z zawartością, która zostanie zlokalizowana.</span><span class="sxs-lookup"><span data-stu-id="6ba46-116">The first step is to create the [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] application project and add a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] element with content that you will localize.</span></span>

### <a name="to-create-the-host-project"></a><span data-ttu-id="6ba46-117">Aby utworzyć projekt hosta</span><span class="sxs-lookup"><span data-stu-id="6ba46-117">To create the host project</span></span>

1. <span data-ttu-id="6ba46-118">Utwórz projekt **aplikacji WPF** o nazwie `LocalizingWpfInWf`.</span><span class="sxs-lookup"><span data-stu-id="6ba46-118">Create a **WPF App** project named `LocalizingWpfInWf`.</span></span>  <span data-ttu-id="6ba46-119">(**Plik** > **Nowy** **projekt Visual C#**  Visual Basic**klasyczna** **Aplikacja WPF**Desktop) > . >  >  > </span><span class="sxs-lookup"><span data-stu-id="6ba46-119">(**File** > **New** > **Project** > **Visual C#** or **Visual Basic** > **Classic Desktop** > **WPF Application**).</span></span>

2. <span data-ttu-id="6ba46-120">Dodaj element o nazwie`SimpleControl` do projektu. <xref:System.Windows.Controls.UserControl> [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6ba46-120">Add a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<xref:System.Windows.Controls.UserControl> element called `SimpleControl` to the project.</span></span>

3. <span data-ttu-id="6ba46-121">Użyj kontrolki, <xref:System.Windows.Forms.Integration.ElementHost> aby `SimpleControl` umieścić element w formularzu.</span><span class="sxs-lookup"><span data-stu-id="6ba46-121">Use the <xref:System.Windows.Forms.Integration.ElementHost> control to place a `SimpleControl` element on the form.</span></span> <span data-ttu-id="6ba46-122">Aby uzyskać więcej informacji, [zobacz Przewodnik: Hostowanie złożonej kontrolki WPF 3D w Windows Forms](walkthrough-hosting-a-3-d-wpf-composite-control-in-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="6ba46-122">For more information, see [Walkthrough: Hosting a 3-D WPF Composite Control in Windows Forms](walkthrough-hosting-a-3-d-wpf-composite-control-in-windows-forms.md).</span></span>

## <a name="adding-localizable-content"></a><span data-ttu-id="6ba46-123">Dodawanie lokalizowalnej zawartości</span><span class="sxs-lookup"><span data-stu-id="6ba46-123">Adding Localizable Content</span></span>

<span data-ttu-id="6ba46-124">Następnie dodasz kontrolkę [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]etykietai ustawisz zawartość elementu na Lokalizowalny ciąg. [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6ba46-124">Next, you will add a [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] label control and set the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] element's content to a localizable string.</span></span>

### <a name="to-add-localizable-content"></a><span data-ttu-id="6ba46-125">Aby dodać lokalizowalną zawartość</span><span class="sxs-lookup"><span data-stu-id="6ba46-125">To add localizable content</span></span>

1. <span data-ttu-id="6ba46-126">W **Eksplorator rozwiązań**kliknij dwukrotnie [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)]plik **SimpleControl. XAML** , aby otworzyć go w.</span><span class="sxs-lookup"><span data-stu-id="6ba46-126">In **Solution Explorer**, double-click **SimpleControl.xaml** to open it in the [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)].</span></span>

2. <span data-ttu-id="6ba46-127">Ustaw zawartość <xref:System.Windows.Controls.Button> formantu przy użyciu następującego kodu.</span><span class="sxs-lookup"><span data-stu-id="6ba46-127">Set the content of the <xref:System.Windows.Controls.Button> control using the following code.</span></span>

     [!code-xaml[LocalizingWpfInWf#10](~/samples/snippets/csharp/VS_Snippets_Wpf/LocalizingWpfInWf/CSharp/SimpleControl0.xaml#10)]

3. <span data-ttu-id="6ba46-128">W **Eksplorator rozwiązań**kliknij dwukrotnie przycisk **Form1** , aby otworzyć go w Projektant formularzy systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="6ba46-128">In **Solution Explorer**, double-click **Form1** to open it in the Windows Forms Designer.</span></span>

4. <span data-ttu-id="6ba46-129">Otwórz **Przybornik** i kliknij dwukrotnie **etykietę** , aby dodać kontrolkę etykieta do formularza.</span><span class="sxs-lookup"><span data-stu-id="6ba46-129">Open the **Toolbox** and double-click **Label** to add a label control to the form.</span></span> <span data-ttu-id="6ba46-130">Ustaw wartość <xref:System.Windows.Forms.Control.Text%2A> właściwości na `"Hello"`.</span><span class="sxs-lookup"><span data-stu-id="6ba46-130">Set the value of its <xref:System.Windows.Forms.Control.Text%2A> property to `"Hello"`.</span></span>

5. <span data-ttu-id="6ba46-131">Naciśnij klawisz **F5** , aby skompilować i uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="6ba46-131">Press **F5** to build and run the application.</span></span>

     <span data-ttu-id="6ba46-132">Zarówno element, jak i kontrolka etykieta wyświetlają tekst **"Hello".** `SimpleControl`</span><span class="sxs-lookup"><span data-stu-id="6ba46-132">Both the `SimpleControl` element and the label control display the text **"Hello"**.</span></span>

## <a name="enabling-localization"></a><span data-ttu-id="6ba46-133">Włączanie lokalizacji</span><span class="sxs-lookup"><span data-stu-id="6ba46-133">Enabling Localization</span></span>

<span data-ttu-id="6ba46-134">Projektant formularzy systemu Windows zawiera ustawienia umożliwiające włączenie lokalizacji w zestawie satelickim.</span><span class="sxs-lookup"><span data-stu-id="6ba46-134">The Windows Forms Designer provides settings for enabling localization in a satellite assembly.</span></span>

### <a name="to-enable-localization"></a><span data-ttu-id="6ba46-135">Aby włączyć lokalizację</span><span class="sxs-lookup"><span data-stu-id="6ba46-135">To enable localization</span></span>

1. <span data-ttu-id="6ba46-136">W **Eksplorator rozwiązań**kliknij dwukrotnie pozycję **Form1.cs** , aby otworzyć ją w Projektant formularzy systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="6ba46-136">In **Solution Explorer**, double-click **Form1.cs** to open it in the Windows Forms Designer.</span></span>

2. <span data-ttu-id="6ba46-137">W oknie **Właściwości** ustaw wartość właściwości **Lokalizowalny** formularza na `true`.</span><span class="sxs-lookup"><span data-stu-id="6ba46-137">In the **Properties** window, set the value of the form's **Localizable** property to `true`.</span></span>

3. <span data-ttu-id="6ba46-138">W oknie **Właściwości** ustaw wartość właściwości **Language** na **hiszpański (Hiszpania)** .</span><span class="sxs-lookup"><span data-stu-id="6ba46-138">In the **Properties** window, set the value of the **Language** property to **Spanish (Spain)**.</span></span>

4. <span data-ttu-id="6ba46-139">W Projektant formularzy systemu Windows wybierz kontrolkę etykieta.</span><span class="sxs-lookup"><span data-stu-id="6ba46-139">In the Windows Forms Designer, select the label control.</span></span>

5. <span data-ttu-id="6ba46-140">W oknie **Właściwości** ustaw wartość <xref:System.Windows.Forms.Control.Text%2A> właściwości na `"Hola"`.</span><span class="sxs-lookup"><span data-stu-id="6ba46-140">In the **Properties** window, set the value of the <xref:System.Windows.Forms.Control.Text%2A> property to `"Hola"`.</span></span>

     <span data-ttu-id="6ba46-141">Nowy plik zasobów o nazwie Form1.es-ES. resx zostanie dodany do projektu.</span><span class="sxs-lookup"><span data-stu-id="6ba46-141">A new resource file named Form1.es-ES.resx is added to the project.</span></span>

6. <span data-ttu-id="6ba46-142">W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy pozycję **Form1.cs** , a następnie kliknij pozycję **Wyświetl kod** , aby otworzyć ją w edytorze kodu.</span><span class="sxs-lookup"><span data-stu-id="6ba46-142">In **Solution Explorer**, right-click **Form1.cs** and click **View Code** to open it in the Code Editor.</span></span>

7. <span data-ttu-id="6ba46-143">Skopiuj następujący kod do `Form1` konstruktora, poprzedzając `InitializeComponent`wywołanie metody.</span><span class="sxs-lookup"><span data-stu-id="6ba46-143">Copy the following code into the `Form1` constructor, preceding the call to `InitializeComponent`.</span></span>

     [!code-csharp[LocalizingWpfInWf#2](~/samples/snippets/csharp/VS_Snippets_Wpf/LocalizingWpfInWf/CSharp/Form1.cs#2)]

8. <span data-ttu-id="6ba46-144">W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy pozycję **LocalizingWpfInWf** , a następnie kliknij pozycję **Zwolnij projekt**.</span><span class="sxs-lookup"><span data-stu-id="6ba46-144">In **Solution Explorer**, right-click **LocalizingWpfInWf** and click **Unload Project**.</span></span>

     <span data-ttu-id="6ba46-145">Nazwa projektu ma etykietę **(niedostępna)** .</span><span class="sxs-lookup"><span data-stu-id="6ba46-145">The project name is labeled **(unavailable)**.</span></span>

9. <span data-ttu-id="6ba46-146">Kliknij prawym przyciskiem myszy pozycję **LocalizingWpfInWf**, a następnie kliknij pozycję **Edytuj LocalizingWpfInWf. csproj**.</span><span class="sxs-lookup"><span data-stu-id="6ba46-146">Right-click **LocalizingWpfInWf**, and click **Edit LocalizingWpfInWf.csproj**.</span></span>

     <span data-ttu-id="6ba46-147">Plik projektu zostanie otwarty w edytorze kodu.</span><span class="sxs-lookup"><span data-stu-id="6ba46-147">The project file opens in the Code Editor.</span></span>

10. <span data-ttu-id="6ba46-148">Skopiuj poniższy wiersz do pierwszego `PropertyGroup` w pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="6ba46-148">Copy the following line into the first `PropertyGroup` in the project file.</span></span>

    ```xml
    <UICulture>en-US</UICulture>
    ```

11. <span data-ttu-id="6ba46-149">Zapisz plik projektu i zamknij go.</span><span class="sxs-lookup"><span data-stu-id="6ba46-149">Save the project file and close it.</span></span>

12. <span data-ttu-id="6ba46-150">W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy pozycję **LocalizingWpfInWf** , a następnie kliknij pozycję **Załaduj ponownie projekt**.</span><span class="sxs-lookup"><span data-stu-id="6ba46-150">In **Solution Explorer**, right-click **LocalizingWpfInWf** and click **Reload Project**.</span></span>

## <a name="assigning-resource-identifiers"></a><span data-ttu-id="6ba46-151">Przypisywanie identyfikatorów zasobów</span><span class="sxs-lookup"><span data-stu-id="6ba46-151">Assigning Resource Identifiers</span></span>

<span data-ttu-id="6ba46-152">Można zmapować lokalizowalną zawartość na zestawy zasobów przy użyciu identyfikatorów zasobów.</span><span class="sxs-lookup"><span data-stu-id="6ba46-152">You can map your localizable content to resource assemblies by using resource identifiers.</span></span> <span data-ttu-id="6ba46-153">Aplikacja MsBuild. exe automatycznie przypisuje identyfikatory zasobów podczas określania `updateuid` opcji.</span><span class="sxs-lookup"><span data-stu-id="6ba46-153">The MsBuild.exe application automatically assigns resource identifiers when you specify the `updateuid` option.</span></span>

### <a name="to-assign-resource-identifiers"></a><span data-ttu-id="6ba46-154">Aby przypisać identyfikatory zasobów</span><span class="sxs-lookup"><span data-stu-id="6ba46-154">To assign resource identifiers</span></span>

1. <span data-ttu-id="6ba46-155">Z menu Start Otwórz wiersz polecenia dla deweloperów dla programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="6ba46-155">From the Start Menu, open the Developer Command Prompt for Visual Studio.</span></span>

2. <span data-ttu-id="6ba46-156">Użyj następującego polecenia, aby przypisać identyfikatory zasobów do lokalizowalnej zawartości.</span><span class="sxs-lookup"><span data-stu-id="6ba46-156">Use the following command to assign resource identifiers to your localizable content.</span></span>

    ```console
    msbuild -t:updateuid LocalizingWpfInWf.csproj
    ```

3. <span data-ttu-id="6ba46-157">W **Eksplorator rozwiązań**kliknij dwukrotnie plik **SimpleControl. XAML** , aby otworzyć go w edytorze kodu.</span><span class="sxs-lookup"><span data-stu-id="6ba46-157">In **Solution Explorer**, double-click **SimpleControl.xaml** to open it in the Code Editor.</span></span> <span data-ttu-id="6ba46-158">Zobaczysz, że `msbuild` polecenie `Uid` dodało atrybut do wszystkich elementów.</span><span class="sxs-lookup"><span data-stu-id="6ba46-158">You will see that the `msbuild` command has added the `Uid` attribute to all the elements.</span></span> <span data-ttu-id="6ba46-159">Ułatwia to lokalizowanie identyfikatorów zasobów.</span><span class="sxs-lookup"><span data-stu-id="6ba46-159">This facilitates localization through the assignment of resource identifiers.</span></span>

     [!code-xaml[LocalizingWpfInWf#20](~/samples/snippets/csharp/VS_Snippets_Wpf/LocalizingWpfInWf/CSharp/SimpleControl.xaml#20)]

4. <span data-ttu-id="6ba46-160">Naciśnij klawisz **F6** , aby skompilować rozwiązanie.</span><span class="sxs-lookup"><span data-stu-id="6ba46-160">Press **F6** to build the solution.</span></span>

## <a name="using-locbaml-to-produce-a-satellite-assembly"></a><span data-ttu-id="6ba46-161">Tworzenie zestawu satelickiego za pomocą LocBaml</span><span class="sxs-lookup"><span data-stu-id="6ba46-161">Using LocBaml to Produce a Satellite Assembly</span></span>

<span data-ttu-id="6ba46-162">Zlokalizowana zawartość jest przechowywana w *zestawie satelickim*obsługującym tylko zasoby.</span><span class="sxs-lookup"><span data-stu-id="6ba46-162">Your localized content is stored in a resource-only *satellite assembly*.</span></span> <span data-ttu-id="6ba46-163">Użyj narzędzia wiersza polecenia LocBaml. exe, aby utworzyć zlokalizowany zestaw [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawartości.</span><span class="sxs-lookup"><span data-stu-id="6ba46-163">Use the command-line tool LocBaml.exe to produce a localized assembly for your [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] content.</span></span>

### <a name="to-produce-a-satellite-assembly"></a><span data-ttu-id="6ba46-164">Aby utworzyć zestaw satelicki</span><span class="sxs-lookup"><span data-stu-id="6ba46-164">To produce a satellite assembly</span></span>

1. <span data-ttu-id="6ba46-165">Skopiuj plik LocBaml. exe do folderu obj\Debug projektu.</span><span class="sxs-lookup"><span data-stu-id="6ba46-165">Copy LocBaml.exe to your project's obj\Debug folder.</span></span> <span data-ttu-id="6ba46-166">Aby uzyskać więcej informacji, zobacz [lokalizowanie aplikacji](how-to-localize-an-application.md).</span><span class="sxs-lookup"><span data-stu-id="6ba46-166">For more information, see [Localize an Application](how-to-localize-an-application.md).</span></span>

2. <span data-ttu-id="6ba46-167">W oknie wiersza polecenia Użyj następującego polecenia, aby wyodrębnić ciągi zasobów do pliku tymczasowego.</span><span class="sxs-lookup"><span data-stu-id="6ba46-167">In the Command Prompt window, use the following command to extract resource strings into a temporary file.</span></span>

    ```console
    LocBaml /parse LocalizingWpfInWf.g.en-US.resources /out:temp.csv
    ```

3. <span data-ttu-id="6ba46-168">Otwórz plik temp. CSV z programem Visual Studio lub innym edytorem tekstu.</span><span class="sxs-lookup"><span data-stu-id="6ba46-168">Open the temp.csv file with Visual Studio or another text editor.</span></span> <span data-ttu-id="6ba46-169">Zastąp ciąg `"Hello"` wyrażeniem hiszpańskim `"Hola"`.</span><span class="sxs-lookup"><span data-stu-id="6ba46-169">Replace the string `"Hello"` with its Spanish translation, `"Hola"`.</span></span>

4. <span data-ttu-id="6ba46-170">Zapisz plik temp. csv.</span><span class="sxs-lookup"><span data-stu-id="6ba46-170">Save the temp.csv file.</span></span>

5. <span data-ttu-id="6ba46-171">Użyj następującego polecenia, aby wygenerować zlokalizowany plik zasobów.</span><span class="sxs-lookup"><span data-stu-id="6ba46-171">Use the following command to generate the localized resource file.</span></span>

    ```console
    LocBaml /generate /trans:temp.csv LocalizingWpfInWf.g.en-US.resources /out:. /cul:es-ES
    ```

     <span data-ttu-id="6ba46-172">Plik LocalizingWpfInWf.g.es-ES. Resources jest tworzony w folderze obj\Debug.</span><span class="sxs-lookup"><span data-stu-id="6ba46-172">The LocalizingWpfInWf.g.es-ES.resources file is created in the obj\Debug folder.</span></span>

6. <span data-ttu-id="6ba46-173">Użyj następującego polecenia, aby skompilować zlokalizowany zestaw satelicki.</span><span class="sxs-lookup"><span data-stu-id="6ba46-173">Use the following command to build the localized satellite assembly.</span></span>

    ```console
    Al.exe /out:LocalizingWpfInWf.resources.dll /culture:es-ES /embed:LocalizingWpfInWf.Form1.es-ES.resources /embed:LocalizingWpfInWf.g.es-ES.resources
    ```

     <span data-ttu-id="6ba46-174">Plik LocalizingWpfInWf. resources. dll jest tworzony w folderze obj\Debug.</span><span class="sxs-lookup"><span data-stu-id="6ba46-174">The LocalizingWpfInWf.resources.dll file is created in the obj\Debug folder.</span></span>

7. <span data-ttu-id="6ba46-175">Skopiuj plik LocalizingWpfInWf. resources. dll do folderu bin\Debug\es-ES projektu.</span><span class="sxs-lookup"><span data-stu-id="6ba46-175">Copy the LocalizingWpfInWf.resources.dll file to the project's bin\Debug\es-ES folder.</span></span> <span data-ttu-id="6ba46-176">Zastąp istniejący plik.</span><span class="sxs-lookup"><span data-stu-id="6ba46-176">Replace the existing file.</span></span>

8. <span data-ttu-id="6ba46-177">Uruchom program LocalizingWpfInWf. exe, który znajduje się w folderze bin\Debug projektu.</span><span class="sxs-lookup"><span data-stu-id="6ba46-177">Run LocalizingWpfInWf.exe, which is located in your project's bin\Debug folder.</span></span> <span data-ttu-id="6ba46-178">Nie Kompiluj ponownie aplikacji lub zestaw satelicki zostanie nadpisany.</span><span class="sxs-lookup"><span data-stu-id="6ba46-178">Do not rebuild the application or the satellite assembly will be overwritten.</span></span>

     <span data-ttu-id="6ba46-179">Aplikacja pokazuje zlokalizowane ciągi zamiast ciągów w języku angielskim.</span><span class="sxs-lookup"><span data-stu-id="6ba46-179">The application shows the localized strings instead of the English strings.</span></span>

## <a name="see-also"></a><span data-ttu-id="6ba46-180">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6ba46-180">See also</span></span>

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [<span data-ttu-id="6ba46-181">Lokalizowanie aplikacji</span><span class="sxs-lookup"><span data-stu-id="6ba46-181">Localize an Application</span></span>](how-to-localize-an-application.md)
- <span data-ttu-id="6ba46-182">[Przewodnik: Lokalizowanie Windows Forms](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/y99d1cd3(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="6ba46-182">[Walkthrough: Localizing Windows Forms](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/y99d1cd3(v=vs.100))</span></span>
- [<span data-ttu-id="6ba46-183">Projektowanie XAML w programie Visual Studio</span><span class="sxs-lookup"><span data-stu-id="6ba46-183">Design XAML in Visual Studio</span></span>](/visualstudio/designers/designing-xaml-in-visual-studio)
