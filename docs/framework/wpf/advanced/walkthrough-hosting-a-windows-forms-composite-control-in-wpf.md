---
title: 'Przewodnik: hostowanie kontrolki złożonej Windows Forms w WPF'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hosting Windows Forms control in WPF [WPF]
- composite controls [WPF], hosting in WPF
ms.assetid: 96fcd78d-1c77-4206-8928-3a0579476ef4
ms.openlocfilehash: 90d0e2f3c6ebab070809a4813c87da3539fd14f1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62032191"
---
# <a name="walkthrough-hosting-a-windows-forms-composite-control-in-wpf"></a><span data-ttu-id="16e40-102">Przewodnik: hostowanie kontrolki złożonej Windows Forms w WPF</span><span class="sxs-lookup"><span data-stu-id="16e40-102">Walkthrough: Hosting a Windows Forms Composite Control in WPF</span></span>
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] <span data-ttu-id="16e40-103">oferuje rozbudowane środowisko do tworzenia aplikacji.</span><span class="sxs-lookup"><span data-stu-id="16e40-103">provides a rich environment for creating applications.</span></span> <span data-ttu-id="16e40-104">Jednak jeśli masz znaczne inwestycje [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] kodu, może być bardziej efektywne ponownie użyć co najmniej część tego kodu w swojej [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacji, a nie do jego przepisania od podstaw.</span><span class="sxs-lookup"><span data-stu-id="16e40-104">However, when you have a substantial investment in [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] code, it can be more effective to reuse at least some of that code in your [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application rather than to rewrite it from scratch.</span></span> <span data-ttu-id="16e40-105">Najbardziej typowym scenariuszem jest w przypadku istniejących kontrolek Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="16e40-105">The most common scenario is when you have existing Windows Forms controls.</span></span> <span data-ttu-id="16e40-106">W niektórych przypadkach możesz nawet utracić dostęp do kodu źródłowego dla tych formantów.</span><span class="sxs-lookup"><span data-stu-id="16e40-106">In some cases, you might not even have access to the source code for these controls.</span></span> [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <span data-ttu-id="16e40-107">zawiera procedury prostym do hostowania te kontrolki w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacji.</span><span class="sxs-lookup"><span data-stu-id="16e40-107">provides a straightforward procedure for hosting such controls in a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application.</span></span> <span data-ttu-id="16e40-108">Na przykład, można użyć [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] dla większości programowania w hostujący usługi specjalistyczne <xref:System.Windows.Forms.DataGridView> kontrolki.</span><span class="sxs-lookup"><span data-stu-id="16e40-108">For example, you can use [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] for most of your programming while hosting your specialized <xref:System.Windows.Forms.DataGridView> controls.</span></span>  
  
 <span data-ttu-id="16e40-109">Ten przewodnik przeprowadzi Cię przez aplikację, która obsługuje złożone kontrolkę Windows Forms do wykonywania wprowadzania danych w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacji.</span><span class="sxs-lookup"><span data-stu-id="16e40-109">This walkthrough steps you through an application that hosts a Windows Forms composite control to perform data entry in a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application.</span></span> <span data-ttu-id="16e40-110">Złożonej kontrolki jest dostarczana w bibliotece DLL.</span><span class="sxs-lookup"><span data-stu-id="16e40-110">The composite control is packaged in a DLL.</span></span> <span data-ttu-id="16e40-111">Ta procedura ogólne można rozszerzyć do bardziej złożonych aplikacji i formantów.</span><span class="sxs-lookup"><span data-stu-id="16e40-111">This general procedure can be extended to more complex applications and controls.</span></span> <span data-ttu-id="16e40-112">Ten przewodnik jest przeznaczony do niemal identyczne w wyglądu i działania [instruktażu: Hosting złożonego formantu WPF w formularzach Windows Forms](walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="16e40-112">This walkthrough is designed to be nearly identical in appearance and functionality to [Walkthrough: Hosting a WPF Composite Control in Windows Forms](walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md).</span></span> <span data-ttu-id="16e40-113">Podstawowa różnica polega na tym, że scenariusza hostingu została odwrócona.</span><span class="sxs-lookup"><span data-stu-id="16e40-113">The primary difference is that the hosting scenario is reversed.</span></span>  
  
 <span data-ttu-id="16e40-114">Ekran instruktażu jest podzielony na dwie sekcje.</span><span class="sxs-lookup"><span data-stu-id="16e40-114">The walkthrough is divided into two sections.</span></span> <span data-ttu-id="16e40-115">Pierwsza sekcja krótko opisano wykonania złożonego formantu Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="16e40-115">The first section briefly describes the implementation of the Windows Forms composite control.</span></span> <span data-ttu-id="16e40-116">Druga sekcja w tym artykule omówiono szczegółowo sposobu hostowania złożonej kontrolki w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacji, odbieranie zdarzeń z kontrolki i uzyskiwać dostęp do niektórych właściwości formantu.</span><span class="sxs-lookup"><span data-stu-id="16e40-116">The second section discusses in detail how to host the composite control in a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application, receive events from the control, and access some of the control's properties.</span></span>  
  
 <span data-ttu-id="16e40-117">Zadania zilustrowane w tym przewodniku obejmują:</span><span class="sxs-lookup"><span data-stu-id="16e40-117">Tasks illustrated in this walkthrough include:</span></span>  
  
- <span data-ttu-id="16e40-118">Implementowanie złożonego formantu Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="16e40-118">Implementing the Windows Forms composite control.</span></span>  
  
- <span data-ttu-id="16e40-119">Implementowanie aplikacja hosta WPF.</span><span class="sxs-lookup"><span data-stu-id="16e40-119">Implementing the WPF host application.</span></span>  
  
 <span data-ttu-id="16e40-120">Lista zadań przedstawione w niniejszym przewodniku kompletny kod znajduje się [Hosting kontrolki złożonej formularzy Windows w przykładzie WPF](https://go.microsoft.com/fwlink/?LinkID=159999).</span><span class="sxs-lookup"><span data-stu-id="16e40-120">For a complete code listing of the tasks illustrated in this walkthrough, see [Hosting a Windows Forms Composite Control in WPF Sample](https://go.microsoft.com/fwlink/?LinkID=159999).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="16e40-121">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="16e40-121">Prerequisites</span></span>  

<span data-ttu-id="16e40-122">Potrzebujesz programu Visual Studio w celu przeprowadzenia tego instruktażu.</span><span class="sxs-lookup"><span data-stu-id="16e40-122">You need Visual Studio to complete this walkthrough.</span></span>
  
## <a name="implementing-the-windows-forms-composite-control"></a><span data-ttu-id="16e40-123">Implementowanie formantu złożonego programu Windows Forms</span><span class="sxs-lookup"><span data-stu-id="16e40-123">Implementing the Windows Forms Composite Control</span></span>  
 <span data-ttu-id="16e40-124">Kontrolek złożonych Windows Forms używane w tym przykładzie jest formą proste wprowadzanie danych.</span><span class="sxs-lookup"><span data-stu-id="16e40-124">The Windows Forms composite control used in this example is a simple data-entry form.</span></span> <span data-ttu-id="16e40-125">Ten formularz przyjmuje nazwę użytkownika i adres, a następnie używa niestandardowego zdarzenia w celu zwracania tych informacji do hosta.</span><span class="sxs-lookup"><span data-stu-id="16e40-125">This form takes the user's name and address and then uses a custom event to return that information to the host.</span></span> <span data-ttu-id="16e40-126">Poniższa ilustracja przedstawia renderowanych kontroli.</span><span class="sxs-lookup"><span data-stu-id="16e40-126">The following illustration shows the rendered control.</span></span>  

 <span data-ttu-id="16e40-127">Na poniższej ilustracji przedstawiono złożonego formantu Windows Forms:</span><span class="sxs-lookup"><span data-stu-id="16e40-127">The following image shows a Windows Forms composite control:</span></span>  

 ![Zrzut ekranu, który pokazuje prosty formant Windows Forms.](./media/walkthrough-hosting-a-windows-forms-composite-control-in-wpf/windows-forms-control.gif)  
  
### <a name="creating-the-project"></a><span data-ttu-id="16e40-129">Tworzenie projektu</span><span class="sxs-lookup"><span data-stu-id="16e40-129">Creating the Project</span></span>  
 <span data-ttu-id="16e40-130">Aby uruchomić projekt:</span><span class="sxs-lookup"><span data-stu-id="16e40-130">To start the project:</span></span>  
  
1. <span data-ttu-id="16e40-131">Uruchom [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)], a następnie otwórz **nowy projekt** okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="16e40-131">Launch [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)], and open the **New Project** dialog box.</span></span>  
  
2. <span data-ttu-id="16e40-132">W kategorii oknie Wybierz **Biblioteka kontrolek formularzy Windows** szablonu.</span><span class="sxs-lookup"><span data-stu-id="16e40-132">In the Window category, select the **Windows Forms Control Library** template.</span></span>  
  
3. <span data-ttu-id="16e40-133">Nazwa nowego projektu `MyControls`.</span><span class="sxs-lookup"><span data-stu-id="16e40-133">Name the new project `MyControls`.</span></span>  
  
4. <span data-ttu-id="16e40-134">Dla lokalizacji, określ wygodnie nazwane folder najwyższego poziomu, takie jak `WpfHostingWindowsFormsControl`.</span><span class="sxs-lookup"><span data-stu-id="16e40-134">For the location, specify a conveniently named top-level folder, such as `WpfHostingWindowsFormsControl`.</span></span> <span data-ttu-id="16e40-135">Później należy umieścić aplikacji hosta w tym folderze.</span><span class="sxs-lookup"><span data-stu-id="16e40-135">Later, you will put the host application in this folder.</span></span>  
  
5. <span data-ttu-id="16e40-136">Kliknij przycisk **OK** do tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="16e40-136">Click **OK** to create the project.</span></span> <span data-ttu-id="16e40-137">Domyślny projekt zawiera jeden formant o nazwie `UserControl1`.</span><span class="sxs-lookup"><span data-stu-id="16e40-137">The default project contains a single control named `UserControl1`.</span></span>  
  
6. <span data-ttu-id="16e40-138">W Eksploratorze rozwiązań, zmienianie nazwy `UserControl1` do `MyControl1`.</span><span class="sxs-lookup"><span data-stu-id="16e40-138">In Solution Explorer, rename `UserControl1` to `MyControl1`.</span></span>  
  
 <span data-ttu-id="16e40-139">Projekt powinien mieć odwołania do następujących systemowych bibliotek DLL.</span><span class="sxs-lookup"><span data-stu-id="16e40-139">Your project should have references to the following system DLLs.</span></span> <span data-ttu-id="16e40-140">Jeśli dowolny z tych bibliotek DLL nie są włączone domyślnie, należy je dodać do projektu.</span><span class="sxs-lookup"><span data-stu-id="16e40-140">If any of these DLLs are not included by default, add them to the project.</span></span>  
  
- <span data-ttu-id="16e40-141">System</span><span class="sxs-lookup"><span data-stu-id="16e40-141">System</span></span>  
  
- <span data-ttu-id="16e40-142">System.Data</span><span class="sxs-lookup"><span data-stu-id="16e40-142">System.Data</span></span>  
  
- <span data-ttu-id="16e40-143">System.Drawing</span><span class="sxs-lookup"><span data-stu-id="16e40-143">System.Drawing</span></span>  
  
- <span data-ttu-id="16e40-144">System.Windows.Forms</span><span class="sxs-lookup"><span data-stu-id="16e40-144">System.Windows.Forms</span></span>  
  
- <span data-ttu-id="16e40-145">System.Xml</span><span class="sxs-lookup"><span data-stu-id="16e40-145">System.Xml</span></span>  
  
### <a name="adding-controls-to-the-form"></a><span data-ttu-id="16e40-146">Dodawanie formantów do formularza</span><span class="sxs-lookup"><span data-stu-id="16e40-146">Adding Controls to the Form</span></span>  
 <span data-ttu-id="16e40-147">Aby dodać formanty do formularza:</span><span class="sxs-lookup"><span data-stu-id="16e40-147">To add controls to the form:</span></span>  
  
- <span data-ttu-id="16e40-148">Otwórz `MyControl1` w projektancie.</span><span class="sxs-lookup"><span data-stu-id="16e40-148">Open `MyControl1` in the designer.</span></span>  
  
 <span data-ttu-id="16e40-149">Dodaj 5 <xref:System.Windows.Forms.Label> kontrolek i odpowiadające im <xref:System.Windows.Forms.TextBox> formantów, rozmiar i tak jak są one na poprzedniej ilustracji, na formularzu.</span><span class="sxs-lookup"><span data-stu-id="16e40-149">Add five <xref:System.Windows.Forms.Label> controls and their corresponding <xref:System.Windows.Forms.TextBox> controls, sized and arranged as they are in the preceding illustration, on the form.</span></span> <span data-ttu-id="16e40-150">W tym przykładzie <xref:System.Windows.Forms.TextBox> formantów są nazywane:</span><span class="sxs-lookup"><span data-stu-id="16e40-150">In the example, the <xref:System.Windows.Forms.TextBox> controls are named:</span></span>  
  
- `txtName`  
  
- `txtAddress`  
  
- `txtCity`  
  
- `txtState`  
  
- `txtZip`  
  
 <span data-ttu-id="16e40-151">Dodaj dwie <xref:System.Windows.Forms.Button> przycisk kontrolek oznaczonych **OK** i **anulować**.</span><span class="sxs-lookup"><span data-stu-id="16e40-151">Add two <xref:System.Windows.Forms.Button> controls labeled **OK** and **Cancel**.</span></span> <span data-ttu-id="16e40-152">W tym przykładzie są nazwy przycisków `btnOK` i `btnCancel`, odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="16e40-152">In the example, the button names are `btnOK` and `btnCancel`, respectively.</span></span>  
  
### <a name="implementing-the-supporting-code"></a><span data-ttu-id="16e40-153">Implementowanie obsługi kodu</span><span class="sxs-lookup"><span data-stu-id="16e40-153">Implementing the Supporting Code</span></span>  
 <span data-ttu-id="16e40-154">Otwórz formularz w widoku kodu.</span><span class="sxs-lookup"><span data-stu-id="16e40-154">Open the form in code view.</span></span> <span data-ttu-id="16e40-155">Formant powraca zebranych danych do jej hosta, tworząc niestandardowy `OnButtonClick` zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="16e40-155">The control returns the collected data to its host by raising the custom `OnButtonClick` event.</span></span> <span data-ttu-id="16e40-156">Dane są zawarte w obiekcie argumentu zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="16e40-156">The data is contained in the event argument object.</span></span> <span data-ttu-id="16e40-157">Poniższy kod przedstawia deklaracji zdarzeń i delegata.</span><span class="sxs-lookup"><span data-stu-id="16e40-157">The following code shows the event and delegate declaration.</span></span>  
  
 <span data-ttu-id="16e40-158">Dodaj następujący kod do `MyControl1` klasy.</span><span class="sxs-lookup"><span data-stu-id="16e40-158">Add the following code to the `MyControl1` class.</span></span>  
  
 [!code-csharp[WpfHostingWindowsFormsControl#2](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/MyControls/MyControl1.cs#2)]
 [!code-vb[WpfHostingWindowsFormsControl#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/VisualBasic/MyControls/MyControl1.vb#2)]

 <span data-ttu-id="16e40-159">`MyControlEventArgs` Klasa zawiera informacje, które mają zostać zwrócona do hosta.</span><span class="sxs-lookup"><span data-stu-id="16e40-159">The `MyControlEventArgs` class contains the information to be returned to the host.</span></span>

 <span data-ttu-id="16e40-160">Dodaj poniższą klasę do formularza.</span><span class="sxs-lookup"><span data-stu-id="16e40-160">Add the following class to the form.</span></span>

 [!code-csharp[WpfHostingWindowsFormsControl#3](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/MyControls/MyControl1.cs#3)]
 [!code-vb[WpfHostingWindowsFormsControl#3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/VisualBasic/MyControls/MyControl1.vb#3)]

 <span data-ttu-id="16e40-161">Po kliknięciu przez użytkownika **OK** lub **anulować** przycisku <xref:System.Windows.Forms.Control.Click> utworzyć procedury obsługi zdarzeń `MyControlEventArgs` obiekt, który zawiera dane i zgłasza `OnButtonClick` zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="16e40-161">When the user clicks the **OK** or **Cancel** button, the <xref:System.Windows.Forms.Control.Click> event handlers create a `MyControlEventArgs` object that contains the data and raises the `OnButtonClick` event.</span></span> <span data-ttu-id="16e40-162">Jedyną różnicą między dwoma obsługi jest argumentu zdarzenia `IsOK` właściwości.</span><span class="sxs-lookup"><span data-stu-id="16e40-162">The only difference between the two handlers is the event argument's `IsOK` property.</span></span> <span data-ttu-id="16e40-163">Ta właściwość umożliwia hostowi na określenie, której przycisk został kliknięty.</span><span class="sxs-lookup"><span data-stu-id="16e40-163">This property enables the host to determine which button was clicked.</span></span> <span data-ttu-id="16e40-164">Jest równa `true` dla **OK** przycisku i `false` dla **anulować** przycisku.</span><span class="sxs-lookup"><span data-stu-id="16e40-164">It is set to `true` for the **OK** button, and `false` for the **Cancel** button.</span></span> <span data-ttu-id="16e40-165">Poniższy kod przedstawia programy obsługi dwóch przycisków.</span><span class="sxs-lookup"><span data-stu-id="16e40-165">The following code shows the two button handlers.</span></span>

 <span data-ttu-id="16e40-166">Dodaj następujący kod do `MyControl1` klasy.</span><span class="sxs-lookup"><span data-stu-id="16e40-166">Add the following code to the `MyControl1` class.</span></span>

 [!code-csharp[WpfHostingWindowsFormsControl#4](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/MyControls/MyControl1.cs#4)]
 [!code-vb[WpfHostingWindowsFormsControl#4](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/VisualBasic/MyControls/MyControl1.vb#4)]

### <a name="giving-the-assembly-a-strong-name-and-building-the-assembly"></a><span data-ttu-id="16e40-167">Zapewniając zestawu z silną nazwą i tworzenia zestawu</span><span class="sxs-lookup"><span data-stu-id="16e40-167">Giving the Assembly a Strong Name and Building the Assembly</span></span>
 <span data-ttu-id="16e40-168">Dla tego zestawu odwoływać się [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacji musi mieć silną nazwę.</span><span class="sxs-lookup"><span data-stu-id="16e40-168">For this assembly to be referenced by a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application, it must have a strong name.</span></span> <span data-ttu-id="16e40-169">Aby utworzyć silnej nazwy, Utwórz plik klucza o Sn.exe i dodaj go do projektu.</span><span class="sxs-lookup"><span data-stu-id="16e40-169">To create a strong name, create a key file with Sn.exe and add it to your project.</span></span>

1. <span data-ttu-id="16e40-170">Otwórz [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)] wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="16e40-170">Open a [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)] command prompt.</span></span> <span data-ttu-id="16e40-171">Aby to zrobić, kliknij przycisk **Start** menu, a następnie wybierz pozycję **wszystkie programy/Microsoft Visual Studio 2010/Visual Studio narzędzia/Visual Studio Command Prompt**.</span><span class="sxs-lookup"><span data-stu-id="16e40-171">To do so, click the **Start** menu, and then select **All Programs/Microsoft Visual Studio 2010/Visual Studio Tools/Visual Studio Command Prompt**.</span></span> <span data-ttu-id="16e40-172">Spowoduje to uruchomienie okna konsoli za pomocą zmiennych środowiskowych dostosowane.</span><span class="sxs-lookup"><span data-stu-id="16e40-172">This launches a console window with customized environment variables.</span></span>

2. <span data-ttu-id="16e40-173">W wierszu polecenia użyj `cd` polecenie, aby przejść do folderu projektu.</span><span class="sxs-lookup"><span data-stu-id="16e40-173">At the command prompt, use the `cd` command to go to your project folder.</span></span>

3. <span data-ttu-id="16e40-174">Wygeneruj plik klucza o nazwie MyControls.snk, uruchamiając następujące polecenie.</span><span class="sxs-lookup"><span data-stu-id="16e40-174">Generate a key file named MyControls.snk by running the following command.</span></span>

    ```
    Sn.exe -k MyControls.snk
    ```

4. <span data-ttu-id="16e40-175">Aby dołączyć plik klucza w projekcie, kliknij prawym przyciskiem myszy nazwę projektu w Eksploratorze rozwiązań, a następnie kliknij przycisk **właściwości**.</span><span class="sxs-lookup"><span data-stu-id="16e40-175">To include the key file in your project, right-click the project name in Solution Explorer and then click **Properties**.</span></span> <span data-ttu-id="16e40-176">W Projektancie projektu kliknij **podpisywanie** zaznacz **Podpisz zestaw** zaznacz pole wyboru, a następnie przejdź do Twojego pliku klucza.</span><span class="sxs-lookup"><span data-stu-id="16e40-176">In the Project Designer, click the **Signing** tab, select the **Sign the assembly** check box and then browse to your key file.</span></span>

5. <span data-ttu-id="16e40-177">Skompiluj rozwiązanie.</span><span class="sxs-lookup"><span data-stu-id="16e40-177">Build the solution.</span></span> <span data-ttu-id="16e40-178">Kompilacja generuje biblioteki DLL o nazwie MyControls.dll.</span><span class="sxs-lookup"><span data-stu-id="16e40-178">The build will produce a DLL named MyControls.dll.</span></span>

## <a name="implementing-the-wpf-host-application"></a><span data-ttu-id="16e40-179">Implementowanie aplikacja hosta WPF</span><span class="sxs-lookup"><span data-stu-id="16e40-179">Implementing the WPF Host Application</span></span>
 <span data-ttu-id="16e40-180">[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Hostowanie aplikacji używa <xref:System.Windows.Forms.Integration.WindowsFormsHost> kontrolki hosta `MyControl1`.</span><span class="sxs-lookup"><span data-stu-id="16e40-180">The [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] host application uses the <xref:System.Windows.Forms.Integration.WindowsFormsHost> control to host `MyControl1`.</span></span> <span data-ttu-id="16e40-181">Uchwyty aplikacji `OnButtonClick` zdarzenia w celu odbierania danych z formantu.</span><span class="sxs-lookup"><span data-stu-id="16e40-181">The application handles the `OnButtonClick` event to receive the data from the control.</span></span> <span data-ttu-id="16e40-182">Ma również zbiór przycisków opcji, które umożliwiają zmianę niektórych właściwości formantu z [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacji.</span><span class="sxs-lookup"><span data-stu-id="16e40-182">It also has a collection of option buttons that enable you to change some of the control's properties from the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application.</span></span> <span data-ttu-id="16e40-183">Na poniższej ilustracji przedstawiono ukończonej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="16e40-183">The following illustration shows the finished application.</span></span>

<span data-ttu-id="16e40-184">Na poniższej ilustracji przedstawiono kompletnej aplikacji, w tym formantu osadzonego w aplikacji WPF:</span><span class="sxs-lookup"><span data-stu-id="16e40-184">The following image shows the complete application, including the control embedded in the WPF application:</span></span>

 ![Zrzut ekranu pokazujący kontrolki osadzony na stronie programu WPF.](./media/walkthrough-hosting-a-windows-forms-composite-control-in-wpf/windows-presentation-foundation-page-control.gif)

### <a name="creating-the-project"></a><span data-ttu-id="16e40-186">Tworzenie projektu</span><span class="sxs-lookup"><span data-stu-id="16e40-186">Creating the Project</span></span>
 <span data-ttu-id="16e40-187">Aby uruchomić projekt:</span><span class="sxs-lookup"><span data-stu-id="16e40-187">To start the project:</span></span>

1. <span data-ttu-id="16e40-188">Otwórz [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)]i wybierz **nowy projekt**.</span><span class="sxs-lookup"><span data-stu-id="16e40-188">Open [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)], and select **New Project**.</span></span>

2. <span data-ttu-id="16e40-189">W kategorii oknie Wybierz **aplikacji WPF** szablonu.</span><span class="sxs-lookup"><span data-stu-id="16e40-189">In the Window category, select the **WPF Application** template.</span></span>

3. <span data-ttu-id="16e40-190">Nazwa nowego projektu `WpfHost`.</span><span class="sxs-lookup"><span data-stu-id="16e40-190">Name the new project `WpfHost`.</span></span>

4. <span data-ttu-id="16e40-191">Dla lokalizacji należy określić ten sam folder najwyższego poziomu, który zawiera projekt MyControls.</span><span class="sxs-lookup"><span data-stu-id="16e40-191">For the location, specify the same top-level folder that contains the MyControls project.</span></span>

5. <span data-ttu-id="16e40-192">Kliknij przycisk **OK** do tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="16e40-192">Click **OK** to create the project.</span></span>

 <span data-ttu-id="16e40-193">Należy również dodać odwołania do biblioteki DLL, która zawiera `MyControl1` i innych zestawów.</span><span class="sxs-lookup"><span data-stu-id="16e40-193">You also need to add references to the DLL that contains `MyControl1` and other assemblies.</span></span>

1. <span data-ttu-id="16e40-194">Kliknij prawym przyciskiem myszy nazwę projektu w Eksploratorze rozwiązań i wybierz **Dodaj odwołanie**.</span><span class="sxs-lookup"><span data-stu-id="16e40-194">Right-click the project name in Solution Explorer and select **Add Reference**.</span></span>

2. <span data-ttu-id="16e40-195">Kliknij przycisk **Przeglądaj** , a następnie przejdź do folderu, który zawiera MyControls.dll.</span><span class="sxs-lookup"><span data-stu-id="16e40-195">Click the **Browse** tab, and browse to the folder that contains MyControls.dll.</span></span> <span data-ttu-id="16e40-196">W tym przewodniku ten folder jest MyControls\bin\Debug.</span><span class="sxs-lookup"><span data-stu-id="16e40-196">For this walkthrough, this folder is MyControls\bin\Debug.</span></span>

3. <span data-ttu-id="16e40-197">Wybierz MyControls.dll, a następnie kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="16e40-197">Select MyControls.dll, and then click **OK**.</span></span>

4. <span data-ttu-id="16e40-198">Dodaj odwołanie do zestawu WindowsFormsIntegration, która nosi nazwę WindowsFormsIntegration.dll.</span><span class="sxs-lookup"><span data-stu-id="16e40-198">Add a reference to the WindowsFormsIntegration assembly, which is named WindowsFormsIntegration.dll.</span></span>

### <a name="implementing-the-basic-layout"></a><span data-ttu-id="16e40-199">Implementowanie podstawowy układ</span><span class="sxs-lookup"><span data-stu-id="16e40-199">Implementing the Basic Layout</span></span>
 <span data-ttu-id="16e40-200">[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] Hosta aplikacji jest zaimplementowana w pliku MainWindow.xaml.</span><span class="sxs-lookup"><span data-stu-id="16e40-200">The [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] of the host application is implemented in MainWindow.xaml.</span></span> <span data-ttu-id="16e40-201">Ten plik zawiera [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] znaczników, który definiuje układ i udostępnia kontrolki Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="16e40-201">This file contains [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] markup that defines the layout, and hosts the Windows Forms control.</span></span> <span data-ttu-id="16e40-202">Aplikacja jest podzielony na trzy regiony:</span><span class="sxs-lookup"><span data-stu-id="16e40-202">The application is divided into three regions:</span></span>

- <span data-ttu-id="16e40-203">**Właściwości kontrolki** panel, który zawiera kolekcję przycisków opcji, które służy do modyfikowania różnych właściwości obiektu obsługiwanego formantu.</span><span class="sxs-lookup"><span data-stu-id="16e40-203">The **Control Properties** panel, which contains a collection of option buttons that you can use to modify various properties of the hosted control.</span></span>

- <span data-ttu-id="16e40-204">**Danych z formantu** panel, który zawiera kilka <xref:System.Windows.Controls.TextBlock> elementy, które wyświetlają dane zwrócone w wyniku obsługiwanego formantu.</span><span class="sxs-lookup"><span data-stu-id="16e40-204">The **Data from Control** panel, which contains several <xref:System.Windows.Controls.TextBlock> elements that display the data returned from the hosted control.</span></span>

- <span data-ttu-id="16e40-205">Hostowanej sama kontrolka.</span><span class="sxs-lookup"><span data-stu-id="16e40-205">The hosted control itself.</span></span>

 <span data-ttu-id="16e40-206">Układ podstawowy jest wyświetlany w następujących XAML.</span><span class="sxs-lookup"><span data-stu-id="16e40-206">The basic layout is shown in the following XAML.</span></span> <span data-ttu-id="16e40-207">Kod znaczników, który jest potrzebny do hosta `MyControl1` pominięto w tym przykładzie, ale zostanie dokładnie omówione później.</span><span class="sxs-lookup"><span data-stu-id="16e40-207">The markup that is needed to host `MyControl1` is omitted from this example, but will be discussed later.</span></span>

 <span data-ttu-id="16e40-208">Zamień na XAML w pliku MainWindow.xaml poniżej.</span><span class="sxs-lookup"><span data-stu-id="16e40-208">Replace the XAML in MainWindow.xaml with the following.</span></span> <span data-ttu-id="16e40-209">Jeśli używasz języka Visual Basic, zmień klasy, która ma `x:Class="MainWindow"`.</span><span class="sxs-lookup"><span data-stu-id="16e40-209">If you are using Visual Basic, change the class to `x:Class="MainWindow"`.</span></span>

 [!code-xaml[WpfHostingWindowsFormsControl#100](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/WpfHost/Page1.xaml#100)]

 <span data-ttu-id="16e40-210">Pierwszy <xref:System.Windows.Controls.StackPanel> element zawiera kilka zestawów <xref:System.Windows.Controls.RadioButton> formantów, które umożliwiają modyfikowanie różne właściwości domyślne obsługiwanego formantu.</span><span class="sxs-lookup"><span data-stu-id="16e40-210">The first <xref:System.Windows.Controls.StackPanel> element contains several sets of <xref:System.Windows.Controls.RadioButton> controls that enable you to modify various default properties of the hosted control.</span></span> <span data-ttu-id="16e40-211">Które następuje <xref:System.Windows.Forms.Integration.WindowsFormsHost> elementu, która hostuje `MyControl1`.</span><span class="sxs-lookup"><span data-stu-id="16e40-211">That is followed by a <xref:System.Windows.Forms.Integration.WindowsFormsHost> element, which hosts `MyControl1`.</span></span> <span data-ttu-id="16e40-212">Końcowe <xref:System.Windows.Controls.StackPanel> element zawiera kilka <xref:System.Windows.Controls.TextBlock> elementy, które wyświetlają dane, który jest zwracany przez kontrolę hostowanej.</span><span class="sxs-lookup"><span data-stu-id="16e40-212">The final <xref:System.Windows.Controls.StackPanel> element contains several <xref:System.Windows.Controls.TextBlock> elements that display the data that is returned by the hosted control.</span></span> <span data-ttu-id="16e40-213">Kolejność elementów i <xref:System.Windows.Controls.DockPanel.Dock%2A> i <xref:System.Windows.FrameworkElement.Height%2A> ustawień atrybutów osadzanie obsługiwanego formantu w oknie bez przerw i zakłóceń.</span><span class="sxs-lookup"><span data-stu-id="16e40-213">The ordering of the elements and the <xref:System.Windows.Controls.DockPanel.Dock%2A> and <xref:System.Windows.FrameworkElement.Height%2A> attribute settings embed the hosted control into the window with no gaps or distortion.</span></span>

#### <a name="hosting-the-control"></a><span data-ttu-id="16e40-214">Hostowanie kontrolki</span><span class="sxs-lookup"><span data-stu-id="16e40-214">Hosting the Control</span></span>
 <span data-ttu-id="16e40-215">Następująca wersja edytowanych poprzedniego XAML koncentruje się na elementy, które są potrzebne do hosta `MyControl1`.</span><span class="sxs-lookup"><span data-stu-id="16e40-215">The following edited version of the previous XAML focuses on the elements that are needed to host `MyControl1`.</span></span>

 [!code-xaml[WpfHostingWindowsFormsControl#101](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/WpfHost/Page1.xaml#101)]
[!code-xaml[WpfHostingWindowsFormsControl#102](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/WpfHost/Page1.xaml#102)]

 <span data-ttu-id="16e40-216">`xmlns` Atrybutu mapowania przestrzeni nazw tworzy odwołanie do `MyControls` przestrzeni nazw, który zawiera formant hostowanej.</span><span class="sxs-lookup"><span data-stu-id="16e40-216">The `xmlns` namespace mapping attribute creates a reference to the `MyControls` namespace that contains the hosted control.</span></span> <span data-ttu-id="16e40-217">To mapowanie umożliwia reprezentują `MyControl1` w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] jako `<mcl:MyControl1>`.</span><span class="sxs-lookup"><span data-stu-id="16e40-217">This mapping enables you to represent `MyControl1` in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] as `<mcl:MyControl1>`.</span></span>

 <span data-ttu-id="16e40-218">Dwa elementy w XAML obsługi hostingu:</span><span class="sxs-lookup"><span data-stu-id="16e40-218">Two elements in the XAML handle the hosting:</span></span>

- <span data-ttu-id="16e40-219">`WindowsFormsHost` reprezentuje <xref:System.Windows.Forms.Integration.WindowsFormsHost> element, który pozwala na hostowanie kontrolki Windows Forms w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacji.</span><span class="sxs-lookup"><span data-stu-id="16e40-219">`WindowsFormsHost` represents the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element that enables you to host a Windows Forms control in a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application.</span></span>

- <span data-ttu-id="16e40-220">`mcl:MyControl1`, który reprezentuje `MyControl1`, jest dodawany do <xref:System.Windows.Forms.Integration.WindowsFormsHost> elementu kolekcji podrzędnej.</span><span class="sxs-lookup"><span data-stu-id="16e40-220">`mcl:MyControl1`, which represents `MyControl1`, is added to the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element's child collection.</span></span> <span data-ttu-id="16e40-221">W wyniku tego formantu Windows Forms jest renderowana jako część [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] , a następnie może komunikować się z urządzeniem za pomocą aplikacji.</span><span class="sxs-lookup"><span data-stu-id="16e40-221">As a result, this Windows Forms control is rendered as part of the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] window, and you can communicate with the control from the application.</span></span>

### <a name="implementing-the-code-behind-file"></a><span data-ttu-id="16e40-222">Wdrażanie pliku związanego z kodem</span><span class="sxs-lookup"><span data-stu-id="16e40-222">Implementing the Code-Behind File</span></span>
 <span data-ttu-id="16e40-223">Plik związany z kodem, MainWindow.xaml.vb lub MainWindow.xaml.cs, zawiera kod proceduralny, która implementuje funkcje [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] omówione w poprzedniej sekcji.</span><span class="sxs-lookup"><span data-stu-id="16e40-223">The code-behind file, MainWindow.xaml.vb or MainWindow.xaml.cs, contains the procedural code that implements the functionality of the [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] discussed in the preceding section.</span></span> <span data-ttu-id="16e40-224">Dostępne są następujące podstawowe zadania:</span><span class="sxs-lookup"><span data-stu-id="16e40-224">The primary tasks are:</span></span>

- <span data-ttu-id="16e40-225">Program obsługi zdarzeń do dołączania `MyControl1`firmy `OnButtonClick` zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="16e40-225">Attaching an event handler to `MyControl1`'s `OnButtonClick` event.</span></span>

- <span data-ttu-id="16e40-226">Modyfikowanie właściwości różnych `MyControl1`, zależnie od konfiguracji kolekcję przycisków opcji.</span><span class="sxs-lookup"><span data-stu-id="16e40-226">Modifying various properties of `MyControl1`, based on how the collection of option buttons are set.</span></span>

- <span data-ttu-id="16e40-227">Wyświetlanie danych zebranych przez kontrolkę.</span><span class="sxs-lookup"><span data-stu-id="16e40-227">Displaying the data collected by the control.</span></span>

#### <a name="initializing-the-application"></a><span data-ttu-id="16e40-228">Inicjowanie aplikacji</span><span class="sxs-lookup"><span data-stu-id="16e40-228">Initializing the Application</span></span>
 <span data-ttu-id="16e40-229">Kod inicjowania znajduje się w obsłudze zdarzeń dla okna <xref:System.Windows.FrameworkElement.Loaded> zdarzeń i dołącza program obsługi zdarzeń do formantu `OnButtonClick` zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="16e40-229">The initialization code is contained in an event handler for the window's <xref:System.Windows.FrameworkElement.Loaded> event and attaches an event handler to the control's `OnButtonClick` event.</span></span>

 <span data-ttu-id="16e40-230">W pliku MainWindow.xaml.vb lub MainWindow.xaml.cs Dodaj następujący kod, aby `MainWindow` klasy.</span><span class="sxs-lookup"><span data-stu-id="16e40-230">In MainWindow.xaml.vb or MainWindow.xaml.cs, add the following code to the `MainWindow` class.</span></span>

 [!code-csharp[WpfHostingWindowsFormsControl#11](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/WpfHost/Page1.xaml.cs#11)]
 [!code-vb[WpfHostingWindowsFormsControl#11](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/VisualBasic/WpfHost/Page1.xaml.vb#11)]

 <span data-ttu-id="16e40-231">Ponieważ [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] omówionych wcześniej dodano `MyControl1` do <xref:System.Windows.Forms.Integration.WindowsFormsHost> kolekcji elementów podrzędnych elementu, można rzutować <xref:System.Windows.Forms.Integration.WindowsFormsHost> elementu <xref:System.Windows.Forms.Integration.WindowsFormsHost.Child%2A> można pobrać odwołania do `MyControl1`.</span><span class="sxs-lookup"><span data-stu-id="16e40-231">Because the [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] discussed previously added `MyControl1` to the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element's child element collection, you can cast the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element's <xref:System.Windows.Forms.Integration.WindowsFormsHost.Child%2A> to get the reference to `MyControl1`.</span></span> <span data-ttu-id="16e40-232">Następnie można użyć tego odwołania, można dołączyć program obsługi zdarzeń do `OnButtonClick`.</span><span class="sxs-lookup"><span data-stu-id="16e40-232">You can then use that reference to attach an event handler to `OnButtonClick`.</span></span>

 <span data-ttu-id="16e40-233">Ponadto, aby zapewnić odwołanie do samej kontrolce, <xref:System.Windows.Forms.Integration.WindowsFormsHost> eksponuje pewną liczbę właściwości kontrolki, które można manipulować z aplikacji.</span><span class="sxs-lookup"><span data-stu-id="16e40-233">In addition to providing a reference to the control itself, <xref:System.Windows.Forms.Integration.WindowsFormsHost> exposes a number of the control's properties, which you can manipulate from the application.</span></span> <span data-ttu-id="16e40-234">Kod inicjowania przypisuje te wartości do prywatnej zmienne globalne do późniejszego użycia w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="16e40-234">The initialization code assigns those values to private global variables for later use in the application.</span></span>

 <span data-ttu-id="16e40-235">Tak, aby mogli łatwo uzyskiwać dostęp z typami w `MyControls` biblioteki DLL, Dodaj następujący kod `Imports` lub `using` instrukcji na górze pliku.</span><span class="sxs-lookup"><span data-stu-id="16e40-235">So that you can easily access the types in the `MyControls` DLL, add the following `Imports` or `using` statement to the top of the file.</span></span>

```vb
Imports MyControls
```

```csharp
using MyControls;
```

#### <a name="handling-the-onbuttonclick-event"></a><span data-ttu-id="16e40-236">Obsługa zdarzeń OnButtonClick</span><span class="sxs-lookup"><span data-stu-id="16e40-236">Handling the OnButtonClick Event</span></span>
 <span data-ttu-id="16e40-237">`MyControl1` wywołuje `OnButtonClick` zdarzenie, kiedy użytkownik kliknie jeden z przycisków kontrolki.</span><span class="sxs-lookup"><span data-stu-id="16e40-237">`MyControl1` raises the `OnButtonClick` event when the user clicks either of the control's buttons.</span></span>

 <span data-ttu-id="16e40-238">Dodaj następujący kod do `MainWindow` klasy.</span><span class="sxs-lookup"><span data-stu-id="16e40-238">Add the following code to the `MainWindow` class.</span></span>

 [!code-csharp[WpfHostingWindowsFormsControl#12](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/WpfHost/Page1.xaml.cs#12)]
 [!code-vb[WpfHostingWindowsFormsControl#12](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/VisualBasic/WpfHost/Page1.xaml.vb#12)]

 <span data-ttu-id="16e40-239">Dane w polach tekstowych są pakowane w `MyControlEventArgs` obiektu.</span><span class="sxs-lookup"><span data-stu-id="16e40-239">The data in the text boxes is packed into the `MyControlEventArgs` object.</span></span> <span data-ttu-id="16e40-240">Jeśli użytkownik kliknie **OK** przycisk, program obsługi zdarzeń wyodrębnia dane i wyświetla go w panelu poniżej `MyControl1`.</span><span class="sxs-lookup"><span data-stu-id="16e40-240">If the user clicks the **OK** button, the event handler extracts the data and displays it in the panel below `MyControl1`.</span></span>

#### <a name="modifying-the-controls-properties"></a><span data-ttu-id="16e40-241">Modyfikowanie właściwości kontrolki</span><span class="sxs-lookup"><span data-stu-id="16e40-241">Modifying the Control’s Properties</span></span>
 <span data-ttu-id="16e40-242"><xref:System.Windows.Forms.Integration.WindowsFormsHost> Elementu udostępnia kilka właściwości domyślnych obsługiwanego formantu.</span><span class="sxs-lookup"><span data-stu-id="16e40-242">The <xref:System.Windows.Forms.Integration.WindowsFormsHost> element exposes several of the hosted control's default properties.</span></span> <span data-ttu-id="16e40-243">Co w efekcie można zmienić wygląd formantu większe zbliżenie style aplikacji.</span><span class="sxs-lookup"><span data-stu-id="16e40-243">As a result, you can change the appearance of the control to match the style of your application more closely.</span></span> <span data-ttu-id="16e40-244">Zestawy przycisków opcji znajdujących się w lewym panelu zezwolić użytkownikom na modyfikowanie kilka właściwości kolorów i czcionek.</span><span class="sxs-lookup"><span data-stu-id="16e40-244">The sets of option buttons in the left panel enable the user to modify several color and font properties.</span></span> <span data-ttu-id="16e40-245">Każdy zestaw przycisków ma program obsługi dla <xref:System.Windows.Controls.Primitives.ButtonBase.Click> zdarzenie, które wykrywa przycisk Opcje użytkownika i zmienia odpowiedniej właściwości w formancie.</span><span class="sxs-lookup"><span data-stu-id="16e40-245">Each set of buttons has a handler for the <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event, which detects the user's option button selections and changes the corresponding property on the control.</span></span>

 <span data-ttu-id="16e40-246">Dodaj następujący kod do `MainWindow` klasy.</span><span class="sxs-lookup"><span data-stu-id="16e40-246">Add the following code to the `MainWindow` class.</span></span>

 [!code-csharp[WpfHostingWindowsFormsControl#13](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/WpfHost/Page1.xaml.cs#13)]
 [!code-vb[WpfHostingWindowsFormsControl#13](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/VisualBasic/WpfHost/Page1.xaml.vb#13)]  
  
 <span data-ttu-id="16e40-247">Skompiluj i uruchom aplikację.</span><span class="sxs-lookup"><span data-stu-id="16e40-247">Build and run the application.</span></span> <span data-ttu-id="16e40-248">Dodaj tekst w złożonego formantu Windows Forms, a następnie kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="16e40-248">Add some text in the Windows Forms composite control and then click **OK**.</span></span> <span data-ttu-id="16e40-249">Tekst jest wyświetlany w etykietach.</span><span class="sxs-lookup"><span data-stu-id="16e40-249">The text appears in the labels.</span></span> <span data-ttu-id="16e40-250">Kliknij przyciski radiowe różnych, aby zobaczyć efekt na formancie.</span><span class="sxs-lookup"><span data-stu-id="16e40-250">Click the different radio buttons to see the effect on the control.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="16e40-251">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="16e40-251">See also</span></span>

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [<span data-ttu-id="16e40-252">Projektowanie XAML w programie Visual Studio</span><span class="sxs-lookup"><span data-stu-id="16e40-252">Design XAML in Visual Studio</span></span>](/visualstudio/designers/designing-xaml-in-visual-studio)
- [<span data-ttu-id="16e40-253">Przewodnik: Hosting kontrolki Windows Forms w WPF</span><span class="sxs-lookup"><span data-stu-id="16e40-253">Walkthrough: Hosting a Windows Forms Control in WPF</span></span>](walkthrough-hosting-a-windows-forms-control-in-wpf.md)
- [<span data-ttu-id="16e40-254">Przewodnik: Hosting złożonego formantu WPF w formularzach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="16e40-254">Walkthrough: Hosting a WPF Composite Control in Windows Forms</span></span>](walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
