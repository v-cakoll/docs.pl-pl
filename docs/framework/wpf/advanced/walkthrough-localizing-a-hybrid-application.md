---
title: 'Wskazówki: lokalizacja aplikacji hybrydowej'
ms.date: 08/18/2018
helpviewer_keywords:
- localization [WPF interoperability]
- hybrid applications [WPF interoperability]
ms.assetid: fbc0c54e-930a-4c13-8e9c-27b83665010a
ms.openlocfilehash: 69aa5ae145ffe378b7a4547e5a33826965bf7894
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/21/2020
ms.locfileid: "80111117"
---
# <a name="walkthrough-localizing-a-hybrid-application"></a><span data-ttu-id="e6040-102">Wskazówki: lokalizacja aplikacji hybrydowej</span><span class="sxs-lookup"><span data-stu-id="e6040-102">Walkthrough: Localizing a Hybrid Application</span></span>

<span data-ttu-id="e6040-103">W tym przewodniku pokazano, jak [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zlokalizować elementy w aplikacji hybrydowej opartej na formularzach systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="e6040-103">This walkthrough shows you how to localize [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] elements in a Windows Forms-based hybrid application.</span></span>

<span data-ttu-id="e6040-104">Zadania zilustrowane w tym przewodniku obejmują:</span><span class="sxs-lookup"><span data-stu-id="e6040-104">Tasks illustrated in this walkthrough include:</span></span>

- <span data-ttu-id="e6040-105">Tworzenie projektu hosta formularzy systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="e6040-105">Creating the Windows Forms host project.</span></span>

- <span data-ttu-id="e6040-106">Dodawanie zawartości zlokalizowanej.</span><span class="sxs-lookup"><span data-stu-id="e6040-106">Adding localizable content.</span></span>

- <span data-ttu-id="e6040-107">Włączanie lokalizacji.</span><span class="sxs-lookup"><span data-stu-id="e6040-107">Enabling localization.</span></span>

- <span data-ttu-id="e6040-108">Przypisywanie identyfikatorów zasobów.</span><span class="sxs-lookup"><span data-stu-id="e6040-108">Assigning resource identifiers.</span></span>

- <span data-ttu-id="e6040-109">Za pomocą narzędzia LocBaml do produkcji zestawu satelickiego.</span><span class="sxs-lookup"><span data-stu-id="e6040-109">Using the LocBaml tool to produce a satellite assembly.</span></span>

<span data-ttu-id="e6040-110">Aby uzyskać pełną listę kod zadań zilustrowanych w tym instruktażu, zobacz [Lokalizowanie przykładu aplikacji hybrydowej](https://go.microsoft.com/fwlink/?LinkID=160015).</span><span class="sxs-lookup"><span data-stu-id="e6040-110">For a complete code listing of the tasks illustrated in this walkthrough, see [Localizing a Hybrid Application Sample](https://go.microsoft.com/fwlink/?LinkID=160015).</span></span>

<span data-ttu-id="e6040-111">Po zakończeniu będziesz mieć zlokalizowaną aplikację hybrydową.</span><span class="sxs-lookup"><span data-stu-id="e6040-111">When you are finished, you will have a localized hybrid application.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="e6040-112">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="e6040-112">Prerequisites</span></span>

<span data-ttu-id="e6040-113">Następujące składniki są wymagane do przeprowadzenia tego instruktażu:</span><span class="sxs-lookup"><span data-stu-id="e6040-113">You need the following components to complete this walkthrough:</span></span>

- <span data-ttu-id="e6040-114">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="e6040-114">Visual Studio 2017</span></span>

## <a name="creating-the-windows-forms-host-project"></a><span data-ttu-id="e6040-115">Tworzenie projektu hosta formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="e6040-115">Creating the Windows Forms Host Project</span></span>

<span data-ttu-id="e6040-116">Pierwszym krokiem jest utworzenie projektu aplikacji Formularze systemu Windows i dodanie elementu z zawartością, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] która będzie się ulaszować.</span><span class="sxs-lookup"><span data-stu-id="e6040-116">The first step is to create the Windows Forms application project and add a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] element with content that you will localize.</span></span>

### <a name="to-create-the-host-project"></a><span data-ttu-id="e6040-117">Aby utworzyć projekt hosta</span><span class="sxs-lookup"><span data-stu-id="e6040-117">To create the host project</span></span>

1. <span data-ttu-id="e6040-118">Utwórz projekt aplikacji `LocalizingWpfInWf` **WPF** o nazwie .</span><span class="sxs-lookup"><span data-stu-id="e6040-118">Create a **WPF App** project named `LocalizingWpfInWf`.</span></span>  <span data-ttu-id="e6040-119">(Plik**File** > **Nowy** > **projekt Visual** > **C#** lub **Visual Basic** > **Classic Desktop** > **WPF Aplikacji**).</span><span class="sxs-lookup"><span data-stu-id="e6040-119">(**File** > **New** > **Project** > **Visual C#** or **Visual Basic** > **Classic Desktop** > **WPF Application**).</span></span>

2. <span data-ttu-id="e6040-120">[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.UserControl> Dodaj element `SimpleControl` wywoływany do projektu.</span><span class="sxs-lookup"><span data-stu-id="e6040-120">Add a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<xref:System.Windows.Controls.UserControl> element called `SimpleControl` to the project.</span></span>

3. <span data-ttu-id="e6040-121">Użyj <xref:System.Windows.Forms.Integration.ElementHost> formantu, `SimpleControl` aby umieścić element w formularzu.</span><span class="sxs-lookup"><span data-stu-id="e6040-121">Use the <xref:System.Windows.Forms.Integration.ElementHost> control to place a `SimpleControl` element on the form.</span></span> <span data-ttu-id="e6040-122">Aby uzyskać więcej informacji, zobacz [Przewodnik: Hostowanie kontrolki złożonej 3D WPF w formularzach systemu Windows](walkthrough-hosting-a-3-d-wpf-composite-control-in-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="e6040-122">For more information, see [Walkthrough: Hosting a 3D WPF Composite Control in Windows Forms](walkthrough-hosting-a-3-d-wpf-composite-control-in-windows-forms.md).</span></span>

## <a name="adding-localizable-content"></a><span data-ttu-id="e6040-123">Dodawanie zawartości zlokalizowanej</span><span class="sxs-lookup"><span data-stu-id="e6040-123">Adding Localizable Content</span></span>

<span data-ttu-id="e6040-124">Następnie należy dodać formant etykiety windows [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] forms i ustawić zawartość elementu na ciąg lokalizowalny.</span><span class="sxs-lookup"><span data-stu-id="e6040-124">Next, you will add a Windows Forms label control and set the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] element's content to a localizable string.</span></span>

### <a name="to-add-localizable-content"></a><span data-ttu-id="e6040-125">Aby dodać zawartość konfigurowalną</span><span class="sxs-lookup"><span data-stu-id="e6040-125">To add localizable content</span></span>

1. <span data-ttu-id="e6040-126">W **Eksploratorze rozwiązań**kliknij dwukrotnie **simplecontrol.xaml,** aby otworzyć go w Projektancie WPF.</span><span class="sxs-lookup"><span data-stu-id="e6040-126">In **Solution Explorer**, double-click **SimpleControl.xaml** to open it in the WPF Designer.</span></span>

2. <span data-ttu-id="e6040-127">Ustaw zawartość formantu przy <xref:System.Windows.Controls.Button> użyciu następującego kodu.</span><span class="sxs-lookup"><span data-stu-id="e6040-127">Set the content of the <xref:System.Windows.Controls.Button> control using the following code.</span></span>

     [!code-xaml[LocalizingWpfInWf#10](~/samples/snippets/csharp/VS_Snippets_Wpf/LocalizingWpfInWf/CSharp/SimpleControl0.xaml#10)]

3. <span data-ttu-id="e6040-128">W **Eksploratorze rozwiązań**kliknij dwukrotnie **pozycję Form1,** aby otworzyć go w Projektancie formularzy systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="e6040-128">In **Solution Explorer**, double-click **Form1** to open it in the Windows Forms Designer.</span></span>

4. <span data-ttu-id="e6040-129">Otwórz **przybornik** i kliknij dwukrotnie **pozycję Etykieta,** aby dodać formant etykiety do formularza.</span><span class="sxs-lookup"><span data-stu-id="e6040-129">Open the **Toolbox** and double-click **Label** to add a label control to the form.</span></span> <span data-ttu-id="e6040-130">Ustaw wartość jego <xref:System.Windows.Forms.Control.Text%2A> właściwości `"Hello"`na .</span><span class="sxs-lookup"><span data-stu-id="e6040-130">Set the value of its <xref:System.Windows.Forms.Control.Text%2A> property to `"Hello"`.</span></span>

5. <span data-ttu-id="e6040-131">Naciśnij **klawisz F5,** aby utworzyć i uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="e6040-131">Press **F5** to build and run the application.</span></span>

     <span data-ttu-id="e6040-132">Zarówno `SimpleControl` element, jak i formant etykiety wyświetlają tekst **"Hello"**.</span><span class="sxs-lookup"><span data-stu-id="e6040-132">Both the `SimpleControl` element and the label control display the text **"Hello"**.</span></span>

## <a name="enabling-localization"></a><span data-ttu-id="e6040-133">Włączanie lokalizacji</span><span class="sxs-lookup"><span data-stu-id="e6040-133">Enabling Localization</span></span>

<span data-ttu-id="e6040-134">Projektant formularzy systemu Windows udostępnia ustawienia umożliwiające lokalizację w zestawie satelicie.</span><span class="sxs-lookup"><span data-stu-id="e6040-134">The Windows Forms Designer provides settings for enabling localization in a satellite assembly.</span></span>

### <a name="to-enable-localization"></a><span data-ttu-id="e6040-135">Aby włączyć lokalizację</span><span class="sxs-lookup"><span data-stu-id="e6040-135">To enable localization</span></span>

1. <span data-ttu-id="e6040-136">W **Eksploratorze rozwiązań**kliknij dwukrotnie **Form1.cs,** aby otworzyć go w Projektancie formularzy systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="e6040-136">In **Solution Explorer**, double-click **Form1.cs** to open it in the Windows Forms Designer.</span></span>

2. <span data-ttu-id="e6040-137">W oknie **Właściwości** ustaw wartość właściwości **Localizable** formularza na `true`.</span><span class="sxs-lookup"><span data-stu-id="e6040-137">In the **Properties** window, set the value of the form's **Localizable** property to `true`.</span></span>

3. <span data-ttu-id="e6040-138">W oknie **Właściwości** ustaw wartość właściwości **Language** na **hiszpański (Hiszpania)**.</span><span class="sxs-lookup"><span data-stu-id="e6040-138">In the **Properties** window, set the value of the **Language** property to **Spanish (Spain)**.</span></span>

4. <span data-ttu-id="e6040-139">W projektancie formularzy systemu Windows wybierz kontrolkę etykiety.</span><span class="sxs-lookup"><span data-stu-id="e6040-139">In the Windows Forms Designer, select the label control.</span></span>

5. <span data-ttu-id="e6040-140">W oknie **Właściwości** ustaw wartość właściwości <xref:System.Windows.Forms.Control.Text%2A> na `"Hola"`.</span><span class="sxs-lookup"><span data-stu-id="e6040-140">In the **Properties** window, set the value of the <xref:System.Windows.Forms.Control.Text%2A> property to `"Hola"`.</span></span>

     <span data-ttu-id="e6040-141">Nowy plik zasobów o nazwie Form1.es-ES.resx zostanie dodany do projektu.</span><span class="sxs-lookup"><span data-stu-id="e6040-141">A new resource file named Form1.es-ES.resx is added to the project.</span></span>

6. <span data-ttu-id="e6040-142">W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy **Form1.cs** i kliknij polecenie **Wyświetl kod,** aby otworzyć go w Edytorze kodów.</span><span class="sxs-lookup"><span data-stu-id="e6040-142">In **Solution Explorer**, right-click **Form1.cs** and click **View Code** to open it in the Code Editor.</span></span>

7. <span data-ttu-id="e6040-143">Skopiuj `Form1` następujący kod do konstruktora, poprzedzając wywołanie do `InitializeComponent`.</span><span class="sxs-lookup"><span data-stu-id="e6040-143">Copy the following code into the `Form1` constructor, preceding the call to `InitializeComponent`.</span></span>

     [!code-csharp[LocalizingWpfInWf#2](~/samples/snippets/csharp/VS_Snippets_Wpf/LocalizingWpfInWf/CSharp/Form1.cs#2)]

8. <span data-ttu-id="e6040-144">W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy **pozycję LocalizingWpfInWf** i kliknij polecenie **Zwolnij projekt**.</span><span class="sxs-lookup"><span data-stu-id="e6040-144">In **Solution Explorer**, right-click **LocalizingWpfInWf** and click **Unload Project**.</span></span>

     <span data-ttu-id="e6040-145">Nazwa projektu jest oznaczona etykietą **(niedostępna).**</span><span class="sxs-lookup"><span data-stu-id="e6040-145">The project name is labeled **(unavailable)**.</span></span>

9. <span data-ttu-id="e6040-146">Kliknij prawym przyciskiem myszy **pozycję LocalizingWpfInWf**, a następnie kliknij polecenie **Edytuj lokalizowanieWpfInWf.csproj**.</span><span class="sxs-lookup"><span data-stu-id="e6040-146">Right-click **LocalizingWpfInWf**, and click **Edit LocalizingWpfInWf.csproj**.</span></span>

     <span data-ttu-id="e6040-147">Plik projektu zostanie otwarty w Edytorze kodu.</span><span class="sxs-lookup"><span data-stu-id="e6040-147">The project file opens in the Code Editor.</span></span>

10. <span data-ttu-id="e6040-148">Skopiuj następujący `PropertyGroup` wiersz do pierwszego w pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="e6040-148">Copy the following line into the first `PropertyGroup` in the project file.</span></span>

    ```xml
    <UICulture>en-US</UICulture>
    ```

11. <span data-ttu-id="e6040-149">Zapisz plik projektu i zamknij go.</span><span class="sxs-lookup"><span data-stu-id="e6040-149">Save the project file and close it.</span></span>

12. <span data-ttu-id="e6040-150">W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy **pozycję LocalizingWpfInWf** i kliknij polecenie **Załaduj ponownie projekt**.</span><span class="sxs-lookup"><span data-stu-id="e6040-150">In **Solution Explorer**, right-click **LocalizingWpfInWf** and click **Reload Project**.</span></span>

## <a name="assigning-resource-identifiers"></a><span data-ttu-id="e6040-151">Przypisywanie identyfikatorów zasobów</span><span class="sxs-lookup"><span data-stu-id="e6040-151">Assigning Resource Identifiers</span></span>

<span data-ttu-id="e6040-152">Zawartość konfigurowalną można mapować na zestawy zasobów przy użyciu identyfikatorów zasobów.</span><span class="sxs-lookup"><span data-stu-id="e6040-152">You can map your localizable content to resource assemblies by using resource identifiers.</span></span> <span data-ttu-id="e6040-153">Aplikacja MsBuild.exe automatycznie przypisuje identyfikatory zasobów po `updateuid` określeniu tej opcji.</span><span class="sxs-lookup"><span data-stu-id="e6040-153">The MsBuild.exe application automatically assigns resource identifiers when you specify the `updateuid` option.</span></span>

### <a name="to-assign-resource-identifiers"></a><span data-ttu-id="e6040-154">Aby przypisać identyfikatory zasobów</span><span class="sxs-lookup"><span data-stu-id="e6040-154">To assign resource identifiers</span></span>

1. <span data-ttu-id="e6040-155">W menu Start otwórz wiersz polecenia dewelopera dla programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="e6040-155">From the Start Menu, open the Developer Command Prompt for Visual Studio.</span></span>

2. <span data-ttu-id="e6040-156">Użyj następującego polecenia, aby przypisać identyfikatory zasobów do zawartości możliwej do zlokalizowania.</span><span class="sxs-lookup"><span data-stu-id="e6040-156">Use the following command to assign resource identifiers to your localizable content.</span></span>

    ```console
    msbuild -t:updateuid LocalizingWpfInWf.csproj
    ```

3. <span data-ttu-id="e6040-157">W **Eksploratorze rozwiązań**kliknij dwukrotnie **simplecontrol.xaml,** aby otworzyć go w Edytorze kodu.</span><span class="sxs-lookup"><span data-stu-id="e6040-157">In **Solution Explorer**, double-click **SimpleControl.xaml** to open it in the Code Editor.</span></span> <span data-ttu-id="e6040-158">Zobaczysz, że `msbuild` polecenie `Uid` dodało atrybut do wszystkich elementów.</span><span class="sxs-lookup"><span data-stu-id="e6040-158">You will see that the `msbuild` command has added the `Uid` attribute to all the elements.</span></span> <span data-ttu-id="e6040-159">Ułatwia to lokalizację poprzez przypisanie identyfikatorów zasobów.</span><span class="sxs-lookup"><span data-stu-id="e6040-159">This facilitates localization through the assignment of resource identifiers.</span></span>

     [!code-xaml[LocalizingWpfInWf#20](~/samples/snippets/csharp/VS_Snippets_Wpf/LocalizingWpfInWf/CSharp/SimpleControl.xaml#20)]

4. <span data-ttu-id="e6040-160">Naciśnij **klawisz F6,** aby zbudować rozwiązanie.</span><span class="sxs-lookup"><span data-stu-id="e6040-160">Press **F6** to build the solution.</span></span>

## <a name="using-locbaml-to-produce-a-satellite-assembly"></a><span data-ttu-id="e6040-161">Tworzenie zestawu satelitarnego za pomocą LocBaml</span><span class="sxs-lookup"><span data-stu-id="e6040-161">Using LocBaml to Produce a Satellite Assembly</span></span>

<span data-ttu-id="e6040-162">Zlokalizowana zawartość jest przechowywana w *zestawie satelicie*tylko za zasoby.</span><span class="sxs-lookup"><span data-stu-id="e6040-162">Your localized content is stored in a resource-only *satellite assembly*.</span></span> <span data-ttu-id="e6040-163">Użyj narzędzia wiersza polecenia LocBaml.exe, aby utworzyć [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zlokalizowany zestaw dla zawartości.</span><span class="sxs-lookup"><span data-stu-id="e6040-163">Use the command-line tool LocBaml.exe to produce a localized assembly for your [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] content.</span></span>

### <a name="to-produce-a-satellite-assembly"></a><span data-ttu-id="e6040-164">Aby wyprodukować zespół satelity</span><span class="sxs-lookup"><span data-stu-id="e6040-164">To produce a satellite assembly</span></span>

1. <span data-ttu-id="e6040-165">Skopiuj program LocBaml.exe do folderu obj\Debug projektu.</span><span class="sxs-lookup"><span data-stu-id="e6040-165">Copy LocBaml.exe to your project's obj\Debug folder.</span></span> <span data-ttu-id="e6040-166">Aby uzyskać więcej informacji, zobacz [Lokalizowanie aplikacji](how-to-localize-an-application.md).</span><span class="sxs-lookup"><span data-stu-id="e6040-166">For more information, see [Localize an Application](how-to-localize-an-application.md).</span></span>

2. <span data-ttu-id="e6040-167">W oknie Wiersz polecenia użyj następującego polecenia, aby wyodrębnić ciągi zasobów do pliku tymczasowego.</span><span class="sxs-lookup"><span data-stu-id="e6040-167">In the Command Prompt window, use the following command to extract resource strings into a temporary file.</span></span>

    ```console
    LocBaml /parse LocalizingWpfInWf.g.en-US.resources /out:temp.csv
    ```

3. <span data-ttu-id="e6040-168">Otwórz plik temp.csv za pomocą programu Visual Studio lub innego edytora tekstu.</span><span class="sxs-lookup"><span data-stu-id="e6040-168">Open the temp.csv file with Visual Studio or another text editor.</span></span> <span data-ttu-id="e6040-169">Zastąp ciąg `"Hello"` jego `"Hola"`tłumaczeniem na język hiszpański, .</span><span class="sxs-lookup"><span data-stu-id="e6040-169">Replace the string `"Hello"` with its Spanish translation, `"Hola"`.</span></span>

4. <span data-ttu-id="e6040-170">Zapisz plik temp.csv.</span><span class="sxs-lookup"><span data-stu-id="e6040-170">Save the temp.csv file.</span></span>

5. <span data-ttu-id="e6040-171">Użyj następującego polecenia, aby wygenerować zlokalizowany plik zasobów.</span><span class="sxs-lookup"><span data-stu-id="e6040-171">Use the following command to generate the localized resource file.</span></span>

    ```console
    LocBaml /generate /trans:temp.csv LocalizingWpfInWf.g.en-US.resources /out:. /cul:es-ES
    ```

     <span data-ttu-id="e6040-172">Plik LocalizingWpfInWf.g.es-ES.resources jest tworzony w folderze obj\Debug.</span><span class="sxs-lookup"><span data-stu-id="e6040-172">The LocalizingWpfInWf.g.es-ES.resources file is created in the obj\Debug folder.</span></span>

6. <span data-ttu-id="e6040-173">Użyj następującego polecenia, aby zbudować zlokalizowany zestaw satelickiego.</span><span class="sxs-lookup"><span data-stu-id="e6040-173">Use the following command to build the localized satellite assembly.</span></span>

    ```console
    Al.exe /out:LocalizingWpfInWf.resources.dll /culture:es-ES /embed:LocalizingWpfInWf.Form1.es-ES.resources /embed:LocalizingWpfInWf.g.es-ES.resources
    ```

     <span data-ttu-id="e6040-174">Plik LocalizingWpfInWf.resources.dll jest tworzony w folderze obj\Debug.</span><span class="sxs-lookup"><span data-stu-id="e6040-174">The LocalizingWpfInWf.resources.dll file is created in the obj\Debug folder.</span></span>

7. <span data-ttu-id="e6040-175">Skopiuj plik LocalizingWpfInWf.resources.dll do folderu bin\Debug\es projektu.</span><span class="sxs-lookup"><span data-stu-id="e6040-175">Copy the LocalizingWpfInWf.resources.dll file to the project's bin\Debug\es-ES folder.</span></span> <span data-ttu-id="e6040-176">Zastąp istniejący plik.</span><span class="sxs-lookup"><span data-stu-id="e6040-176">Replace the existing file.</span></span>

8. <span data-ttu-id="e6040-177">Uruchom localizingWpfInWf.exe, który znajduje się w folderze bin\Debug projektu projektu.</span><span class="sxs-lookup"><span data-stu-id="e6040-177">Run LocalizingWpfInWf.exe, which is located in your project's bin\Debug folder.</span></span> <span data-ttu-id="e6040-178">Nie należy przebudowywać aplikacji lub zestaw satelicie zostanie zastąpiony.</span><span class="sxs-lookup"><span data-stu-id="e6040-178">Do not rebuild the application or the satellite assembly will be overwritten.</span></span>

     <span data-ttu-id="e6040-179">Aplikacja pokazuje zlokalizowane ciągi zamiast ciągów w języku angielskim.</span><span class="sxs-lookup"><span data-stu-id="e6040-179">The application shows the localized strings instead of the English strings.</span></span>

## <a name="see-also"></a><span data-ttu-id="e6040-180">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e6040-180">See also</span></span>

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [<span data-ttu-id="e6040-181">Lokalizowanie aplikacji</span><span class="sxs-lookup"><span data-stu-id="e6040-181">Localize an Application</span></span>](how-to-localize-an-application.md)
- <span data-ttu-id="e6040-182">[Przewodnik: Lokalizowanie formularzy systemu Windows](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/y99d1cd3(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="e6040-182">[Walkthrough: Localizing Windows Forms](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/y99d1cd3(v=vs.100))</span></span>
- [<span data-ttu-id="e6040-183">Projektowanie XAML w programie Visual Studio</span><span class="sxs-lookup"><span data-stu-id="e6040-183">Design XAML in Visual Studio</span></span>](/visualstudio/xaml-tools/designing-xaml-in-visual-studio)
