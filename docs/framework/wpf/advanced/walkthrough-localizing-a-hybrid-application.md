---
title: 'Wskazówki: lokalizacja aplikacji hybrydowej'
ms.date: 08/18/2018
helpviewer_keywords:
- localization [WPF interoperability]
- hybrid applications [WPF interoperability]
ms.assetid: fbc0c54e-930a-4c13-8e9c-27b83665010a
ms.openlocfilehash: e1d06085b4edb5c1e102eaab766ec7636194b991
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/22/2018
ms.locfileid: "46697961"
---
# <a name="walkthrough-localizing-a-hybrid-application"></a><span data-ttu-id="0da9b-102">Wskazówki: lokalizacja aplikacji hybrydowej</span><span class="sxs-lookup"><span data-stu-id="0da9b-102">Walkthrough: Localizing a Hybrid Application</span></span>

<span data-ttu-id="0da9b-103">W tym instruktażu pokazano, jak zlokalizować [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] elementów w [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]— na podstawie aplikacji hybrydowych.</span><span class="sxs-lookup"><span data-stu-id="0da9b-103">This walkthrough shows you how to localize [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] elements in a [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]-based hybrid application.</span></span>

<span data-ttu-id="0da9b-104">Zadania zilustrowane w tym przewodniku obejmują:</span><span class="sxs-lookup"><span data-stu-id="0da9b-104">Tasks illustrated in this walkthrough include:</span></span>

-   <span data-ttu-id="0da9b-105">Tworzenie [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] projektu hosta.</span><span class="sxs-lookup"><span data-stu-id="0da9b-105">Creating the [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] host project.</span></span>

-   <span data-ttu-id="0da9b-106">Dodawanie możliwych do zlokalizowania zawartości.</span><span class="sxs-lookup"><span data-stu-id="0da9b-106">Adding localizable content.</span></span>

-   <span data-ttu-id="0da9b-107">Włączanie lokalizacji.</span><span class="sxs-lookup"><span data-stu-id="0da9b-107">Enabling localization.</span></span>

-   <span data-ttu-id="0da9b-108">Przypisywanie identyfikatorów zasobów.</span><span class="sxs-lookup"><span data-stu-id="0da9b-108">Assigning resource identifiers.</span></span>

-   <span data-ttu-id="0da9b-109">Przy użyciu locbaml — narzędzie do tworzenia zestawu satelickiego.</span><span class="sxs-lookup"><span data-stu-id="0da9b-109">Using the LocBaml tool to produce a satellite assembly.</span></span>

<span data-ttu-id="0da9b-110">Lista zadań przedstawione w niniejszym przewodniku kompletny kod znajduje się [lokalizowanie przykładowej aplikacji hybrydowych](https://go.microsoft.com/fwlink/?LinkID=160015).</span><span class="sxs-lookup"><span data-stu-id="0da9b-110">For a complete code listing of the tasks illustrated in this walkthrough, see [Localizing a Hybrid Application Sample](https://go.microsoft.com/fwlink/?LinkID=160015).</span></span>

<span data-ttu-id="0da9b-111">Po zakończeniu masz hybrydowej zlokalizowanych aplikacji.</span><span class="sxs-lookup"><span data-stu-id="0da9b-111">When you are finished, you will have a localized hybrid application.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="0da9b-112">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="0da9b-112">Prerequisites</span></span>

<span data-ttu-id="0da9b-113">Następujące składniki są wymagane do przeprowadzenia tego instruktażu:</span><span class="sxs-lookup"><span data-stu-id="0da9b-113">You need the following components to complete this walkthrough:</span></span>

-   <span data-ttu-id="0da9b-114">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="0da9b-114">Visual Studio 2017</span></span>

## <a name="creating-the-windows-forms-host-project"></a><span data-ttu-id="0da9b-115">Tworząc projekt hosta Windows Forms</span><span class="sxs-lookup"><span data-stu-id="0da9b-115">Creating the Windows Forms Host Project</span></span>

<span data-ttu-id="0da9b-116">Pierwszym krokiem jest utworzenie [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] aplikacji projektu i dodawanie [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] elementu z zawartością, która będzie lokalizowany.</span><span class="sxs-lookup"><span data-stu-id="0da9b-116">The first step is to create the [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] application project and add a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] element with content that you will localize.</span></span>

### <a name="to-create-the-host-project"></a><span data-ttu-id="0da9b-117">Aby utworzyć projekt hosta</span><span class="sxs-lookup"><span data-stu-id="0da9b-117">To create the host project</span></span>

1.  <span data-ttu-id="0da9b-118">Tworzenie **aplikacja WPF** projektu o nazwie `LocalizingWpfInWf`.</span><span class="sxs-lookup"><span data-stu-id="0da9b-118">Create a **WPF App** project named `LocalizingWpfInWf`.</span></span>  <span data-ttu-id="0da9b-119">(**Pliku** > **nowe** > **projektu** > **Visual C#** lub **języka Visual Basic**   >  **Classic Desktop** > **aplikacji WPF**).</span><span class="sxs-lookup"><span data-stu-id="0da9b-119">(**File** > **New** > **Project** > **Visual C#** or **Visual Basic** > **Classic Desktop** > **WPF Application**).</span></span>

2.  <span data-ttu-id="0da9b-120">Dodaj [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.UserControl> element o nazwie `SimpleControl` do projektu.</span><span class="sxs-lookup"><span data-stu-id="0da9b-120">Add a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<xref:System.Windows.Controls.UserControl> element called `SimpleControl` to the project.</span></span>

3.  <span data-ttu-id="0da9b-121">Użyj <xref:System.Windows.Forms.Integration.ElementHost> formantu, aby umieścić `SimpleControl` elementu w formularzu.</span><span class="sxs-lookup"><span data-stu-id="0da9b-121">Use the <xref:System.Windows.Forms.Integration.ElementHost> control to place a `SimpleControl` element on the form.</span></span> <span data-ttu-id="0da9b-122">Aby uzyskać więcej informacji, zobacz [wskazówki: Hosting 3-złożonego formantu WPF w formularzach Windows Forms](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-3-d-wpf-composite-control-in-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="0da9b-122">For more information, see [Walkthrough: Hosting a 3-D WPF Composite Control in Windows Forms](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-3-d-wpf-composite-control-in-windows-forms.md).</span></span>

## <a name="adding-localizable-content"></a><span data-ttu-id="0da9b-123">Dodawanie możliwych do zlokalizowania zawartości</span><span class="sxs-lookup"><span data-stu-id="0da9b-123">Adding Localizable Content</span></span>

<span data-ttu-id="0da9b-124">Następnie dodasz [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] kontrolka etykiety i ustaw [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawartości elementu do zlokalizowania ciągu.</span><span class="sxs-lookup"><span data-stu-id="0da9b-124">Next, you will add a [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] label control and set the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] element's content to a localizable string.</span></span>

### <a name="to-add-localizable-content"></a><span data-ttu-id="0da9b-125">Aby dodać możliwych do zlokalizowania zawartości</span><span class="sxs-lookup"><span data-stu-id="0da9b-125">To add localizable content</span></span>

1.  <span data-ttu-id="0da9b-126">W **Eksploratora rozwiązań**, kliknij dwukrotnie **SimpleControl.xaml** aby otworzyć go w [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="0da9b-126">In **Solution Explorer**, double-click **SimpleControl.xaml** to open it in the [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)].</span></span>

2.  <span data-ttu-id="0da9b-127">Ustaw zawartość <xref:System.Windows.Controls.Button> kontrolować, używając następującego kodu.</span><span class="sxs-lookup"><span data-stu-id="0da9b-127">Set the content of the <xref:System.Windows.Controls.Button> control using the following code.</span></span>

     [!code-xaml[LocalizingWpfInWf#10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LocalizingWpfInWf/CSharp/SimpleControl0.xaml#10)]

3.  <span data-ttu-id="0da9b-128">W **Eksploratora rozwiązań**, kliknij dwukrotnie **Form1** aby go otworzyć w programie Windows Forms Designer.</span><span class="sxs-lookup"><span data-stu-id="0da9b-128">In **Solution Explorer**, double-click **Form1** to open it in the Windows Forms Designer.</span></span>

4.  <span data-ttu-id="0da9b-129">Otwórz **przybornika** i kliknij dwukrotnie **etykiety** można dodać kontrolkę typu etykieta do formularza.</span><span class="sxs-lookup"><span data-stu-id="0da9b-129">Open the **Toolbox** and double-click **Label** to add a label control to the form.</span></span> <span data-ttu-id="0da9b-130">Ustaw wartość jego <xref:System.Windows.Forms.Control.Text%2A> właściwość `"Hello"`.</span><span class="sxs-lookup"><span data-stu-id="0da9b-130">Set the value of its <xref:System.Windows.Forms.Control.Text%2A> property to `"Hello"`.</span></span>

5.  <span data-ttu-id="0da9b-131">Naciśnij klawisz **F5** Aby skompilować i uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="0da9b-131">Press **F5** to build and run the application.</span></span>

     <span data-ttu-id="0da9b-132">Zarówno `SimpleControl` elementu i formant etykiety wyświetlić tekst **"Hello"**.</span><span class="sxs-lookup"><span data-stu-id="0da9b-132">Both the `SimpleControl` element and the label control display the text **"Hello"**.</span></span>

## <a name="enabling-localization"></a><span data-ttu-id="0da9b-133">Włączanie lokalizacji</span><span class="sxs-lookup"><span data-stu-id="0da9b-133">Enabling Localization</span></span>

<span data-ttu-id="0da9b-134">Windows Forms Designer udostępnia ustawienia umożliwiające włączanie lokalizacji w zestawie satelickim.</span><span class="sxs-lookup"><span data-stu-id="0da9b-134">The Windows Forms Designer provides settings for enabling localization in a satellite assembly.</span></span>

### <a name="to-enable-localization"></a><span data-ttu-id="0da9b-135">Można włączyć lokalizacji</span><span class="sxs-lookup"><span data-stu-id="0da9b-135">To enable localization</span></span>

1.  <span data-ttu-id="0da9b-136">W **Eksploratora rozwiązań**, kliknij dwukrotnie **Form1.cs** aby go otworzyć w programie Windows Forms Designer.</span><span class="sxs-lookup"><span data-stu-id="0da9b-136">In **Solution Explorer**, double-click **Form1.cs** to open it in the Windows Forms Designer.</span></span>

2.  <span data-ttu-id="0da9b-137">W **właściwości** okna, ustaw wartość w postaci **Lokalizowalny** właściwość `true`.</span><span class="sxs-lookup"><span data-stu-id="0da9b-137">In the **Properties** window, set the value of the form's **Localizable** property to `true`.</span></span>

3.  <span data-ttu-id="0da9b-138">W **właściwości** okna, ustaw wartość **języka** właściwości **hiszpański (Hiszpania)**.</span><span class="sxs-lookup"><span data-stu-id="0da9b-138">In the **Properties** window, set the value of the **Language** property to **Spanish (Spain)**.</span></span>

4.  <span data-ttu-id="0da9b-139">W programie Windows Forms Designer wybierz formant etykiety.</span><span class="sxs-lookup"><span data-stu-id="0da9b-139">In the Windows Forms Designer, select the label control.</span></span>

5.  <span data-ttu-id="0da9b-140">W **właściwości** okna, ustaw wartość <xref:System.Windows.Forms.Control.Text%2A> właściwość `"Hola"`.</span><span class="sxs-lookup"><span data-stu-id="0da9b-140">In the **Properties** window, set the value of the <xref:System.Windows.Forms.Control.Text%2A> property to `"Hola"`.</span></span>

     <span data-ttu-id="0da9b-141">Plik zasobów o nazwie Form1.es ES.resx zostanie dodany do projektu.</span><span class="sxs-lookup"><span data-stu-id="0da9b-141">A new resource file named Form1.es-ES.resx is added to the project.</span></span>

6.  <span data-ttu-id="0da9b-142">W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **Form1.cs** i kliknij przycisk **Wyświetl kod** aby go otworzyć w edytorze kodu.</span><span class="sxs-lookup"><span data-stu-id="0da9b-142">In **Solution Explorer**, right-click **Form1.cs** and click **View Code** to open it in the Code Editor.</span></span>

7.  <span data-ttu-id="0da9b-143">Skopiuj następujący kod do `Form1` konstruktora, poprzedzającym wywołanie `InitializeComponent`.</span><span class="sxs-lookup"><span data-stu-id="0da9b-143">Copy the following code into the `Form1` constructor, preceding the call to `InitializeComponent`.</span></span>

     [!code-csharp[LocalizingWpfInWf#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LocalizingWpfInWf/CSharp/Form1.cs#2)]

8.  <span data-ttu-id="0da9b-144">W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **LocalizingWpfInWf** i kliknij przycisk **Zwolnij projekt**.</span><span class="sxs-lookup"><span data-stu-id="0da9b-144">In **Solution Explorer**, right-click **LocalizingWpfInWf** and click **Unload Project**.</span></span>

     <span data-ttu-id="0da9b-145">Nazwa projektu jest oznaczona etykietą **(niedostępna)**.</span><span class="sxs-lookup"><span data-stu-id="0da9b-145">The project name is labeled **(unavailable)**.</span></span>

9. <span data-ttu-id="0da9b-146">Kliknij prawym przyciskiem myszy **LocalizingWpfInWf**i kliknij przycisk **Edytuj LocalizingWpfInWf.csproj**.</span><span class="sxs-lookup"><span data-stu-id="0da9b-146">Right-click **LocalizingWpfInWf**, and click **Edit LocalizingWpfInWf.csproj**.</span></span>

     <span data-ttu-id="0da9b-147">Plik projektu zostanie otwarty w edytorze kodu.</span><span class="sxs-lookup"><span data-stu-id="0da9b-147">The project file opens in the Code Editor.</span></span>

10. <span data-ttu-id="0da9b-148">Skopiuj następujący wiersz do pierwszego `PropertyGroup` w pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="0da9b-148">Copy the following line into the first `PropertyGroup` in the project file.</span></span>

    ```xml
    <UICulture>en-US</UICulture>
    ```

11. <span data-ttu-id="0da9b-149">Zapisz plik projektu i zamknij go.</span><span class="sxs-lookup"><span data-stu-id="0da9b-149">Save the project file and close it.</span></span>

12. <span data-ttu-id="0da9b-150">W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **LocalizingWpfInWf** i kliknij przycisk **Załaduj ponownie projekt**.</span><span class="sxs-lookup"><span data-stu-id="0da9b-150">In **Solution Explorer**, right-click **LocalizingWpfInWf** and click **Reload Project**.</span></span>

## <a name="assigning-resource-identifiers"></a><span data-ttu-id="0da9b-151">Przypisywanie identyfikatory zasobów</span><span class="sxs-lookup"><span data-stu-id="0da9b-151">Assigning Resource Identifiers</span></span>

<span data-ttu-id="0da9b-152">Możliwych do zlokalizowania zawartości można mapować do zestawów zasobów przy użyciu identyfikatorów zasobów.</span><span class="sxs-lookup"><span data-stu-id="0da9b-152">You can map your localizable content to resource assemblies by using resource identifiers.</span></span> <span data-ttu-id="0da9b-153">Po określeniu aplikacji MsBuild.exe automatycznie przypisuje identyfikatory zasobów `updateuid` opcji.</span><span class="sxs-lookup"><span data-stu-id="0da9b-153">The MsBuild.exe application automatically assigns resource identifiers when you specify the `updateuid` option.</span></span>

### <a name="to-assign-resource-identifiers"></a><span data-ttu-id="0da9b-154">Aby przypisać identyfikatory zasobów</span><span class="sxs-lookup"><span data-stu-id="0da9b-154">To assign resource identifiers</span></span>

1.  <span data-ttu-id="0da9b-155">Z Menu Start otwórz wiersz polecenia programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="0da9b-155">From the Start Menu, open the Visual Studio Command Prompt.</span></span>

2.  <span data-ttu-id="0da9b-156">Użyj następującego polecenia, aby przypisać identyfikatory zasobów do zlokalizowania zawartości.</span><span class="sxs-lookup"><span data-stu-id="0da9b-156">Use the following command to assign resource identifiers to your localizable content.</span></span>

    ```
    msbuild -t:updateuid LocalizingWpfInWf.csproj
    ```

3.  <span data-ttu-id="0da9b-157">W **Eksploratora rozwiązań**, kliknij dwukrotnie **SimpleControl.xaml** aby go otworzyć w edytorze kodu.</span><span class="sxs-lookup"><span data-stu-id="0da9b-157">In **Solution Explorer**, double-click **SimpleControl.xaml** to open it in the Code Editor.</span></span> <span data-ttu-id="0da9b-158">Zostanie wyświetlony `msbuild` polecenia został dodany `Uid` atrybutu do wszystkich elementów.</span><span class="sxs-lookup"><span data-stu-id="0da9b-158">You will see that the `msbuild` command has added the `Uid` attribute to all the elements.</span></span> <span data-ttu-id="0da9b-159">To ułatwia lokalizacji poprzez przypisywanie identyfikatorów zasobów.</span><span class="sxs-lookup"><span data-stu-id="0da9b-159">This facilitates localization through the assignment of resource identifiers.</span></span>

     [!code-xaml[LocalizingWpfInWf#20](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LocalizingWpfInWf/CSharp/SimpleControl.xaml#20)]

4.  <span data-ttu-id="0da9b-160">Naciśnij klawisz **F6** do skompilowania rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="0da9b-160">Press **F6** to build the solution.</span></span>

## <a name="using-locbaml-to-produce-a-satellite-assembly"></a><span data-ttu-id="0da9b-161">Przy użyciu locbaml — w celu utworzenia zestawu satelickiego</span><span class="sxs-lookup"><span data-stu-id="0da9b-161">Using LocBaml to Produce a Satellite Assembly</span></span>

<span data-ttu-id="0da9b-162">Zlokalizowane zawartość jest przechowywana w tylko do zasobów *zestawie satelickim*.</span><span class="sxs-lookup"><span data-stu-id="0da9b-162">Your localized content is stored in a resource-only *satellite assembly*.</span></span> <span data-ttu-id="0da9b-163">Narzędzie wiersza polecenia LocBaml.exe do utworzenia zlokalizowanej zestawu dla Twojego [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawartości.</span><span class="sxs-lookup"><span data-stu-id="0da9b-163">Use the command-line tool LocBaml.exe to produce a localized assembly for your [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] content.</span></span>

### <a name="to-produce-a-satellite-assembly"></a><span data-ttu-id="0da9b-164">Aby wygenerować zestawu satelickiego</span><span class="sxs-lookup"><span data-stu-id="0da9b-164">To produce a satellite assembly</span></span>

1.  <span data-ttu-id="0da9b-165">Skopiuj LocBaml.exe folder obj\Debug tego projektu.</span><span class="sxs-lookup"><span data-stu-id="0da9b-165">Copy LocBaml.exe to your project's obj\Debug folder.</span></span> <span data-ttu-id="0da9b-166">Aby uzyskać więcej informacji, zobacz [lokalizowanie aplikacji](../../../../docs/framework/wpf/advanced/how-to-localize-an-application.md).</span><span class="sxs-lookup"><span data-stu-id="0da9b-166">For more information, see [Localize an Application](../../../../docs/framework/wpf/advanced/how-to-localize-an-application.md).</span></span>

2.  <span data-ttu-id="0da9b-167">W oknie wiersza polecenia użyj następującego polecenia, aby wyodrębnić ciągów zasobów do pliku tymczasowego.</span><span class="sxs-lookup"><span data-stu-id="0da9b-167">In the Command Prompt window, use the following command to extract resource strings into a temporary file.</span></span>

    ```
    LocBaml /parse LocalizingWpfInWf.g.en-US.resources /out:temp.csv
    ```

3.  <span data-ttu-id="0da9b-168">Otwórz plik temp.csv za pomocą programu Visual Studio lub innego edytora tekstu.</span><span class="sxs-lookup"><span data-stu-id="0da9b-168">Open the temp.csv file with Visual Studio or another text editor.</span></span> <span data-ttu-id="0da9b-169">Zastąp ciąg `"Hello"` z tłumaczeniem hiszpańskim `"Hola"`.</span><span class="sxs-lookup"><span data-stu-id="0da9b-169">Replace the string `"Hello"` with its Spanish translation, `"Hola"`.</span></span>

4.  <span data-ttu-id="0da9b-170">Zapisz plik temp.csv.</span><span class="sxs-lookup"><span data-stu-id="0da9b-170">Save the temp.csv file.</span></span>

5.  <span data-ttu-id="0da9b-171">Użyj następującego polecenia, aby wygenerować plik zlokalizowanych zasobów.</span><span class="sxs-lookup"><span data-stu-id="0da9b-171">Use the following command to generate the localized resource file.</span></span>

    ```
    LocBaml /generate /trans:temp.csv LocalizingWpfInWf.g.en-US.resources /out:. /cul:es-ES
    ```

     <span data-ttu-id="0da9b-172">Plik LocalizingWpfInWf.g.es ES.resources jest tworzony w folderze obj\Debug.</span><span class="sxs-lookup"><span data-stu-id="0da9b-172">The LocalizingWpfInWf.g.es-ES.resources file is created in the obj\Debug folder.</span></span>

6.  <span data-ttu-id="0da9b-173">Użyj następującego polecenia do tworzenia zestawu satelickiego zlokalizowane.</span><span class="sxs-lookup"><span data-stu-id="0da9b-173">Use the following command to build the localized satellite assembly.</span></span>

    ```
    Al.exe /out:LocalizingWpfInWf.resources.dll /culture:es-ES /embed:LocalizingWpfInWf.Form1.es-ES.resources /embed:LocalizingWpfInWf.g.es-ES.resources
    ```

     <span data-ttu-id="0da9b-174">Plik LocalizingWpfInWf.resources.dll jest tworzony w folderze obj\Debug.</span><span class="sxs-lookup"><span data-stu-id="0da9b-174">The LocalizingWpfInWf.resources.dll file is created in the obj\Debug folder.</span></span>

7.  <span data-ttu-id="0da9b-175">Skopiuj plik LocalizingWpfInWf.resources.dll do folderu bin\Debug\es ES projektu.</span><span class="sxs-lookup"><span data-stu-id="0da9b-175">Copy the LocalizingWpfInWf.resources.dll file to the project's bin\Debug\es-ES folder.</span></span> <span data-ttu-id="0da9b-176">Zastąp istniejący plik.</span><span class="sxs-lookup"><span data-stu-id="0da9b-176">Replace the existing file.</span></span>

8.  <span data-ttu-id="0da9b-177">Uruchom LocalizingWpfInWf.exe, który znajduje się w folderze bin\Debug Twojego projektu.</span><span class="sxs-lookup"><span data-stu-id="0da9b-177">Run LocalizingWpfInWf.exe, which is located in your project's bin\Debug folder.</span></span> <span data-ttu-id="0da9b-178">Nie ponownie skompiluj aplikację lub zestawie satelickim zostaną zastąpione.</span><span class="sxs-lookup"><span data-stu-id="0da9b-178">Do not rebuild the application or the satellite assembly will be overwritten.</span></span>

     <span data-ttu-id="0da9b-179">Aplikacja zawiera zlokalizowane ciągi zamiast ciągi w języku polskim.</span><span class="sxs-lookup"><span data-stu-id="0da9b-179">The application shows the localized strings instead of the English strings.</span></span>

## <a name="see-also"></a><span data-ttu-id="0da9b-180">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0da9b-180">See Also</span></span>

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [<span data-ttu-id="0da9b-181">Lokalizowanie aplikacji</span><span class="sxs-lookup"><span data-stu-id="0da9b-181">Localize an Application</span></span>](../../../../docs/framework/wpf/advanced/how-to-localize-an-application.md)
- [<span data-ttu-id="0da9b-182">Wskazówki: Lokalizowanie interfejsów Windows Forms</span><span class="sxs-lookup"><span data-stu-id="0da9b-182">Walkthrough: Localizing Windows Forms</span></span>](https://msdn.microsoft.com/library/9a96220d-a19b-4de0-9f48-01e5d82679e5)
- [<span data-ttu-id="0da9b-183">Projektowanie XAML w programie Visual Studio</span><span class="sxs-lookup"><span data-stu-id="0da9b-183">Design XAML in Visual Studio</span></span>](/visualstudio/designers/designing-xaml-in-visual-studio)
