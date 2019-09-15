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
ms.openlocfilehash: e4c1de17b131ee68c6e6fce0035b703eb5b489a0
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/14/2019
ms.locfileid: "70991884"
---
# <a name="walkthrough-hosting-a-windows-forms-composite-control-in-wpf"></a><span data-ttu-id="713b3-102">Przewodnik: hostowanie kontrolki złożonej Windows Forms w WPF</span><span class="sxs-lookup"><span data-stu-id="713b3-102">Walkthrough: Hosting a Windows Forms Composite Control in WPF</span></span>
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]<span data-ttu-id="713b3-103">oferuje bogate środowisko do tworzenia aplikacji.</span><span class="sxs-lookup"><span data-stu-id="713b3-103">provides a rich environment for creating applications.</span></span> <span data-ttu-id="713b3-104">Jeśli jednak masz znaczną inwestycję w [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] kod, może być bardziej efektywne ponowne użycie co najmniej jednego kodu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] w aplikacji, a nie zapisanie go od podstaw.</span><span class="sxs-lookup"><span data-stu-id="713b3-104">However, when you have a substantial investment in [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] code, it can be more effective to reuse at least some of that code in your [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application rather than to rewrite it from scratch.</span></span> <span data-ttu-id="713b3-105">Najczęstszym scenariuszem jest to, że masz istniejące kontrolki Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="713b3-105">The most common scenario is when you have existing Windows Forms controls.</span></span> <span data-ttu-id="713b3-106">W niektórych przypadkach może nie mieć nawet dostępu do kodu źródłowego dla tych formantów.</span><span class="sxs-lookup"><span data-stu-id="713b3-106">In some cases, you might not even have access to the source code for these controls.</span></span> [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<span data-ttu-id="713b3-107">zapewnia prostą procedurę hostingu takich kontrolek w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacji.</span><span class="sxs-lookup"><span data-stu-id="713b3-107">provides a straightforward procedure for hosting such controls in a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application.</span></span> <span data-ttu-id="713b3-108">Na przykład można użyć [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] dla większości programowania, jednocześnie udostępniając wyspecjalizowane <xref:System.Windows.Forms.DataGridView> kontrolki.</span><span class="sxs-lookup"><span data-stu-id="713b3-108">For example, you can use [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] for most of your programming while hosting your specialized <xref:System.Windows.Forms.DataGridView> controls.</span></span>  
  
 <span data-ttu-id="713b3-109">Ten Instruktaż zawiera instrukcje dotyczące aplikacji, która hostuje Windows Forms formant złożony do wprowadzania danych w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacji.</span><span class="sxs-lookup"><span data-stu-id="713b3-109">This walkthrough steps you through an application that hosts a Windows Forms composite control to perform data entry in a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application.</span></span> <span data-ttu-id="713b3-110">Formant złożony jest spakowany w bibliotece DLL.</span><span class="sxs-lookup"><span data-stu-id="713b3-110">The composite control is packaged in a DLL.</span></span> <span data-ttu-id="713b3-111">Ta ogólna procedura może zostać rozszerzona na bardziej złożone aplikacje i kontrolki.</span><span class="sxs-lookup"><span data-stu-id="713b3-111">This general procedure can be extended to more complex applications and controls.</span></span> <span data-ttu-id="713b3-112">Ten przewodnik został zaprojektowany tak, aby był niemal identyczny w wyglądzie i funkcji w celu [instruktażu: Hostowanie złożonego formantu WPF w](walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="713b3-112">This walkthrough is designed to be nearly identical in appearance and functionality to [Walkthrough: Hosting a WPF Composite Control in Windows Forms](walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md).</span></span> <span data-ttu-id="713b3-113">Podstawowa różnica polega na tym, że scenariusz hostingu jest odwrócony.</span><span class="sxs-lookup"><span data-stu-id="713b3-113">The primary difference is that the hosting scenario is reversed.</span></span>  
  
 <span data-ttu-id="713b3-114">Przewodnik jest podzielony na dwie sekcje.</span><span class="sxs-lookup"><span data-stu-id="713b3-114">The walkthrough is divided into two sections.</span></span> <span data-ttu-id="713b3-115">W pierwszej sekcji krótko opisano implementację Windows Formsego formantu złożonego.</span><span class="sxs-lookup"><span data-stu-id="713b3-115">The first section briefly describes the implementation of the Windows Forms composite control.</span></span> <span data-ttu-id="713b3-116">W drugiej sekcji omówiono szczegółowo, jak hostować formant złożony w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacji, odbierać zdarzenia z kontrolki i uzyskiwać dostęp do niektórych właściwości kontrolki.</span><span class="sxs-lookup"><span data-stu-id="713b3-116">The second section discusses in detail how to host the composite control in a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application, receive events from the control, and access some of the control's properties.</span></span>  
  
 <span data-ttu-id="713b3-117">Zadania przedstawione w tym instruktażu obejmują:</span><span class="sxs-lookup"><span data-stu-id="713b3-117">Tasks illustrated in this walkthrough include:</span></span>  
  
- <span data-ttu-id="713b3-118">Implementowanie Windows Formsgo formantu złożonego.</span><span class="sxs-lookup"><span data-stu-id="713b3-118">Implementing the Windows Forms composite control.</span></span>  
  
- <span data-ttu-id="713b3-119">Implementowanie aplikacji hosta WPF.</span><span class="sxs-lookup"><span data-stu-id="713b3-119">Implementing the WPF host application.</span></span>  
  
 <span data-ttu-id="713b3-120">Aby uzyskać pełną listę kodów zadań przedstawionych w tym instruktażu, zobacz [hostowanie złożonego formantu Windows Forms w przykładzie WPF](https://go.microsoft.com/fwlink/?LinkID=159999).</span><span class="sxs-lookup"><span data-stu-id="713b3-120">For a complete code listing of the tasks illustrated in this walkthrough, see [Hosting a Windows Forms Composite Control in WPF Sample](https://go.microsoft.com/fwlink/?LinkID=159999).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="713b3-121">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="713b3-121">Prerequisites</span></span>  

<span data-ttu-id="713b3-122">Aby ukończyć ten przewodnik, potrzebujesz programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="713b3-122">You need Visual Studio to complete this walkthrough.</span></span>
  
## <a name="implementing-the-windows-forms-composite-control"></a><span data-ttu-id="713b3-123">Implementowanie Windows Formsgo formantu złożonego</span><span class="sxs-lookup"><span data-stu-id="713b3-123">Implementing the Windows Forms Composite Control</span></span>  
 <span data-ttu-id="713b3-124">Formant złożony Windows Forms używany w tym przykładzie jest prostym formularzem wprowadzania danych.</span><span class="sxs-lookup"><span data-stu-id="713b3-124">The Windows Forms composite control used in this example is a simple data-entry form.</span></span> <span data-ttu-id="713b3-125">Ten formularz przyjmuje nazwę i adres użytkownika, a następnie używa zdarzenia niestandardowego, aby zwrócić te informacje do hosta.</span><span class="sxs-lookup"><span data-stu-id="713b3-125">This form takes the user's name and address and then uses a custom event to return that information to the host.</span></span> <span data-ttu-id="713b3-126">Poniższa ilustracja przedstawia renderowany formant.</span><span class="sxs-lookup"><span data-stu-id="713b3-126">The following illustration shows the rendered control.</span></span>  

 <span data-ttu-id="713b3-127">Na poniższej ilustracji przedstawiono Windows Forms formant złożony:</span><span class="sxs-lookup"><span data-stu-id="713b3-127">The following image shows a Windows Forms composite control:</span></span>  

 ![Zrzut ekranu, który pokazuje prosty formant Windows Forms.](./media/walkthrough-hosting-a-windows-forms-composite-control-in-wpf/windows-forms-control.gif)  
  
### <a name="creating-the-project"></a><span data-ttu-id="713b3-129">Tworzenie projektu</span><span class="sxs-lookup"><span data-stu-id="713b3-129">Creating the Project</span></span>  
 <span data-ttu-id="713b3-130">Aby rozpocząć projekt:</span><span class="sxs-lookup"><span data-stu-id="713b3-130">To start the project:</span></span>  
  
1. <span data-ttu-id="713b3-131">Uruchom [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)]i Otwórz okno dialogowe **Nowy projekt** .</span><span class="sxs-lookup"><span data-stu-id="713b3-131">Launch [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)], and open the **New Project** dialog box.</span></span>  
  
2. <span data-ttu-id="713b3-132">W kategorii okna wybierz szablon **Biblioteka formantów Windows Forms** .</span><span class="sxs-lookup"><span data-stu-id="713b3-132">In the Window category, select the **Windows Forms Control Library** template.</span></span>  
  
3. <span data-ttu-id="713b3-133">Nadaj nazwę nowemu projektowi `MyControls`.</span><span class="sxs-lookup"><span data-stu-id="713b3-133">Name the new project `MyControls`.</span></span>  
  
4. <span data-ttu-id="713b3-134">W polu Lokalizacja Określ wygodną nazwę folderu najwyższego poziomu, na przykład `WpfHostingWindowsFormsControl`.</span><span class="sxs-lookup"><span data-stu-id="713b3-134">For the location, specify a conveniently named top-level folder, such as `WpfHostingWindowsFormsControl`.</span></span> <span data-ttu-id="713b3-135">Później aplikacja hosta zostanie umieszczona w tym folderze.</span><span class="sxs-lookup"><span data-stu-id="713b3-135">Later, you will put the host application in this folder.</span></span>  
  
5. <span data-ttu-id="713b3-136">Kliknij przycisk **OK** , aby utworzyć projekt.</span><span class="sxs-lookup"><span data-stu-id="713b3-136">Click **OK** to create the project.</span></span> <span data-ttu-id="713b3-137">Domyślny projekt zawiera pojedynczy formant o nazwie `UserControl1`.</span><span class="sxs-lookup"><span data-stu-id="713b3-137">The default project contains a single control named `UserControl1`.</span></span>  
  
6. <span data-ttu-id="713b3-138">W Eksplorator rozwiązań Zmień nazwę `UserControl1` na `MyControl1`.</span><span class="sxs-lookup"><span data-stu-id="713b3-138">In Solution Explorer, rename `UserControl1` to `MyControl1`.</span></span>  
  
 <span data-ttu-id="713b3-139">Projekt powinien zawierać odwołania do następujących bibliotek DLL systemu.</span><span class="sxs-lookup"><span data-stu-id="713b3-139">Your project should have references to the following system DLLs.</span></span> <span data-ttu-id="713b3-140">Jeśli dowolna z tych bibliotek DLL nie jest domyślnie dołączona, należy dodać je do projektu.</span><span class="sxs-lookup"><span data-stu-id="713b3-140">If any of these DLLs are not included by default, add them to the project.</span></span>  
  
- <span data-ttu-id="713b3-141">System</span><span class="sxs-lookup"><span data-stu-id="713b3-141">System</span></span>  
  
- <span data-ttu-id="713b3-142">System.Data</span><span class="sxs-lookup"><span data-stu-id="713b3-142">System.Data</span></span>  
  
- <span data-ttu-id="713b3-143">System.Drawing</span><span class="sxs-lookup"><span data-stu-id="713b3-143">System.Drawing</span></span>  
  
- <span data-ttu-id="713b3-144">System.Windows.Forms</span><span class="sxs-lookup"><span data-stu-id="713b3-144">System.Windows.Forms</span></span>  
  
- <span data-ttu-id="713b3-145">System.Xml</span><span class="sxs-lookup"><span data-stu-id="713b3-145">System.Xml</span></span>  
  
### <a name="adding-controls-to-the-form"></a><span data-ttu-id="713b3-146">Dodawanie kontrolek do formularza</span><span class="sxs-lookup"><span data-stu-id="713b3-146">Adding Controls to the Form</span></span>  
 <span data-ttu-id="713b3-147">Aby dodać kontrolki do formularza:</span><span class="sxs-lookup"><span data-stu-id="713b3-147">To add controls to the form:</span></span>  
  
- <span data-ttu-id="713b3-148">Otwórz `MyControl1` w projektancie.</span><span class="sxs-lookup"><span data-stu-id="713b3-148">Open `MyControl1` in the designer.</span></span>  
  
 <span data-ttu-id="713b3-149">Dodaj pięć <xref:System.Windows.Forms.Label> formantów i ich odpowiadające im <xref:System.Windows.Forms.TextBox> kontrolki, rozmiar i uporządkowany, tak jak na poprzedniej ilustracji, w formularzu.</span><span class="sxs-lookup"><span data-stu-id="713b3-149">Add five <xref:System.Windows.Forms.Label> controls and their corresponding <xref:System.Windows.Forms.TextBox> controls, sized and arranged as they are in the preceding illustration, on the form.</span></span> <span data-ttu-id="713b3-150">W przykładzie <xref:System.Windows.Forms.TextBox> kontrolki są nazwane:</span><span class="sxs-lookup"><span data-stu-id="713b3-150">In the example, the <xref:System.Windows.Forms.TextBox> controls are named:</span></span>  
  
- `txtName`  
  
- `txtAddress`  
  
- `txtCity`  
  
- `txtState`  
  
- `txtZip`  
  
 <span data-ttu-id="713b3-151">Dodaj dwie <xref:System.Windows.Forms.Button> kontrolki z etykietą **OK** i **Anuluj**.</span><span class="sxs-lookup"><span data-stu-id="713b3-151">Add two <xref:System.Windows.Forms.Button> controls labeled **OK** and **Cancel**.</span></span> <span data-ttu-id="713b3-152">W tym przykładzie nazwy przycisków są `btnOK` odpowiednio i. `btnCancel`</span><span class="sxs-lookup"><span data-stu-id="713b3-152">In the example, the button names are `btnOK` and `btnCancel`, respectively.</span></span>  
  
### <a name="implementing-the-supporting-code"></a><span data-ttu-id="713b3-153">Implementowanie kodu pomocniczego</span><span class="sxs-lookup"><span data-stu-id="713b3-153">Implementing the Supporting Code</span></span>  
 <span data-ttu-id="713b3-154">Otwórz formularz w widoku kodu.</span><span class="sxs-lookup"><span data-stu-id="713b3-154">Open the form in code view.</span></span> <span data-ttu-id="713b3-155">Kontrolka zwraca zebrane dane do hosta przez podnoszenie poziomu zdarzenia niestandardowego `OnButtonClick` .</span><span class="sxs-lookup"><span data-stu-id="713b3-155">The control returns the collected data to its host by raising the custom `OnButtonClick` event.</span></span> <span data-ttu-id="713b3-156">Dane są zawarte w obiekcie argumentu zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="713b3-156">The data is contained in the event argument object.</span></span> <span data-ttu-id="713b3-157">Poniższy kod przedstawia deklarację zdarzenia i delegata.</span><span class="sxs-lookup"><span data-stu-id="713b3-157">The following code shows the event and delegate declaration.</span></span>  
  
 <span data-ttu-id="713b3-158">Dodaj następujący kod do `MyControl1` klasy.</span><span class="sxs-lookup"><span data-stu-id="713b3-158">Add the following code to the `MyControl1` class.</span></span>  
  
 [!code-csharp[WpfHostingWindowsFormsControl#2](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/MyControls/MyControl1.cs#2)]
 [!code-vb[WpfHostingWindowsFormsControl#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/VisualBasic/MyControls/MyControl1.vb#2)]

 <span data-ttu-id="713b3-159">`MyControlEventArgs` Klasa zawiera informacje, które mają zostać zwrócone do hosta.</span><span class="sxs-lookup"><span data-stu-id="713b3-159">The `MyControlEventArgs` class contains the information to be returned to the host.</span></span>

 <span data-ttu-id="713b3-160">Dodaj następującą klasę do formularza.</span><span class="sxs-lookup"><span data-stu-id="713b3-160">Add the following class to the form.</span></span>

 [!code-csharp[WpfHostingWindowsFormsControl#3](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/MyControls/MyControl1.cs#3)]
 [!code-vb[WpfHostingWindowsFormsControl#3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/VisualBasic/MyControls/MyControl1.vb#3)]

 <span data-ttu-id="713b3-161">Gdy użytkownik kliknie <xref:System.Windows.Forms.Control.Click> przycisk **OK** lub **Anuluj** , programy obsługi zdarzeń tworzą `MyControlEventArgs` obiekt, który zawiera dane i zgłasza `OnButtonClick` zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="713b3-161">When the user clicks the **OK** or **Cancel** button, the <xref:System.Windows.Forms.Control.Click> event handlers create a `MyControlEventArgs` object that contains the data and raises the `OnButtonClick` event.</span></span> <span data-ttu-id="713b3-162">Jedyną różnicą między dwoma uchwytami jest `IsOK` właściwość argumentu zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="713b3-162">The only difference between the two handlers is the event argument's `IsOK` property.</span></span> <span data-ttu-id="713b3-163">Ta właściwość umożliwia hostowi określenie, który przycisk został kliknięty.</span><span class="sxs-lookup"><span data-stu-id="713b3-163">This property enables the host to determine which button was clicked.</span></span> <span data-ttu-id="713b3-164">Jest ona ustawiona `true` na przycisk **OK** , a `false` dla przycisku **Anuluj** .</span><span class="sxs-lookup"><span data-stu-id="713b3-164">It is set to `true` for the **OK** button, and `false` for the **Cancel** button.</span></span> <span data-ttu-id="713b3-165">Poniższy kod przedstawia dwa programy obsługi przycisków.</span><span class="sxs-lookup"><span data-stu-id="713b3-165">The following code shows the two button handlers.</span></span>

 <span data-ttu-id="713b3-166">Dodaj następujący kod do `MyControl1` klasy.</span><span class="sxs-lookup"><span data-stu-id="713b3-166">Add the following code to the `MyControl1` class.</span></span>

 [!code-csharp[WpfHostingWindowsFormsControl#4](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/MyControls/MyControl1.cs#4)]
 [!code-vb[WpfHostingWindowsFormsControl#4](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/VisualBasic/MyControls/MyControl1.vb#4)]

### <a name="giving-the-assembly-a-strong-name-and-building-the-assembly"></a><span data-ttu-id="713b3-167">Nadawanie zestawowi silnej nazwy i kompilowania zestawu</span><span class="sxs-lookup"><span data-stu-id="713b3-167">Giving the Assembly a Strong Name and Building the Assembly</span></span>
 <span data-ttu-id="713b3-168">Aby ten zestaw odwołuje [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] się do aplikacji, musi mieć silną nazwę.</span><span class="sxs-lookup"><span data-stu-id="713b3-168">For this assembly to be referenced by a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application, it must have a strong name.</span></span> <span data-ttu-id="713b3-169">Aby utworzyć silną nazwę, Utwórz plik klucza z SN. exe i dodaj go do projektu.</span><span class="sxs-lookup"><span data-stu-id="713b3-169">To create a strong name, create a key file with Sn.exe and add it to your project.</span></span>

1. <span data-ttu-id="713b3-170">Otwórz wiersz [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)] polecenia.</span><span class="sxs-lookup"><span data-stu-id="713b3-170">Open a [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)] command prompt.</span></span> <span data-ttu-id="713b3-171">Aby to zrobić, kliknij menu **Start** , a następnie wybierz pozycję **wszystkie programy/Microsoft Visual Studio 2010/Visual Studio Tools/wiersz polecenia programu Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="713b3-171">To do so, click the **Start** menu, and then select **All Programs/Microsoft Visual Studio 2010/Visual Studio Tools/Visual Studio Command Prompt**.</span></span> <span data-ttu-id="713b3-172">Spowoduje to uruchomienie okna konsoli z dostosowanymi zmiennymi środowiskowymi.</span><span class="sxs-lookup"><span data-stu-id="713b3-172">This launches a console window with customized environment variables.</span></span>

2. <span data-ttu-id="713b3-173">W wierszu polecenia Użyj `cd` polecenia, aby przejść do folderu projektu.</span><span class="sxs-lookup"><span data-stu-id="713b3-173">At the command prompt, use the `cd` command to go to your project folder.</span></span>

3. <span data-ttu-id="713b3-174">Wygeneruj plik klucza o nazwie SNK, uruchamiając następujące polecenie.</span><span class="sxs-lookup"><span data-stu-id="713b3-174">Generate a key file named MyControls.snk by running the following command.</span></span>

    ```console
    Sn.exe -k MyControls.snk
    ```

4. <span data-ttu-id="713b3-175">Aby dołączyć plik klucza w projekcie, kliknij prawym przyciskiem myszy nazwę projektu w Eksplorator rozwiązań a następnie kliknij pozycję **Właściwości**.</span><span class="sxs-lookup"><span data-stu-id="713b3-175">To include the key file in your project, right-click the project name in Solution Explorer and then click **Properties**.</span></span> <span data-ttu-id="713b3-176">W projektancie projektu kliknij kartę **podpisywanie** , zaznacz pole wyboru **podpisz zestaw** , a następnie przejdź do pliku klucza.</span><span class="sxs-lookup"><span data-stu-id="713b3-176">In the Project Designer, click the **Signing** tab, select the **Sign the assembly** check box and then browse to your key file.</span></span>

5. <span data-ttu-id="713b3-177">Skompiluj rozwiązanie.</span><span class="sxs-lookup"><span data-stu-id="713b3-177">Build the solution.</span></span> <span data-ttu-id="713b3-178">Kompilacja spowoduje utworzenie biblioteki DLL o nazwie WebControls. dll.</span><span class="sxs-lookup"><span data-stu-id="713b3-178">The build will produce a DLL named MyControls.dll.</span></span>

## <a name="implementing-the-wpf-host-application"></a><span data-ttu-id="713b3-179">Implementowanie aplikacji hosta WPF</span><span class="sxs-lookup"><span data-stu-id="713b3-179">Implementing the WPF Host Application</span></span>
 <span data-ttu-id="713b3-180">Aplikacja hosta używa kontrolki do hostowania `MyControl1`. <xref:System.Windows.Forms.Integration.WindowsFormsHost> [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]</span><span class="sxs-lookup"><span data-stu-id="713b3-180">The [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] host application uses the <xref:System.Windows.Forms.Integration.WindowsFormsHost> control to host `MyControl1`.</span></span> <span data-ttu-id="713b3-181">Aplikacja obsługuje zdarzenie, `OnButtonClick` aby otrzymywać dane z formantu.</span><span class="sxs-lookup"><span data-stu-id="713b3-181">The application handles the `OnButtonClick` event to receive the data from the control.</span></span> <span data-ttu-id="713b3-182">Zawiera również zbiór przycisków opcji, które umożliwiają zmianę niektórych właściwości kontrolki z [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacji.</span><span class="sxs-lookup"><span data-stu-id="713b3-182">It also has a collection of option buttons that enable you to change some of the control's properties from the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application.</span></span> <span data-ttu-id="713b3-183">Na poniższej ilustracji przedstawiono ukończoną aplikację.</span><span class="sxs-lookup"><span data-stu-id="713b3-183">The following illustration shows the finished application.</span></span>

<span data-ttu-id="713b3-184">Na poniższej ilustracji przedstawiono kompletną aplikację, w tym kontrolkę osadzoną w aplikacji WPF:</span><span class="sxs-lookup"><span data-stu-id="713b3-184">The following image shows the complete application, including the control embedded in the WPF application:</span></span>

 ![Zrzut ekranu, który pokazuje kontrolkę osadzoną na stronie WPF.](./media/walkthrough-hosting-a-windows-forms-composite-control-in-wpf/windows-presentation-foundation-page-control.gif)

### <a name="creating-the-project"></a><span data-ttu-id="713b3-186">Tworzenie projektu</span><span class="sxs-lookup"><span data-stu-id="713b3-186">Creating the Project</span></span>
 <span data-ttu-id="713b3-187">Aby rozpocząć projekt:</span><span class="sxs-lookup"><span data-stu-id="713b3-187">To start the project:</span></span>

1. <span data-ttu-id="713b3-188">Otwórz [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)]i wybierz pozycję **Nowy projekt**.</span><span class="sxs-lookup"><span data-stu-id="713b3-188">Open [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)], and select **New Project**.</span></span>

2. <span data-ttu-id="713b3-189">W kategorii okno Wybierz szablon **Aplikacja WPF** .</span><span class="sxs-lookup"><span data-stu-id="713b3-189">In the Window category, select the **WPF Application** template.</span></span>

3. <span data-ttu-id="713b3-190">Nadaj nazwę nowemu projektowi `WpfHost`.</span><span class="sxs-lookup"><span data-stu-id="713b3-190">Name the new project `WpfHost`.</span></span>

4. <span data-ttu-id="713b3-191">Dla lokalizacji Określ ten sam folder najwyższego poziomu, który zawiera projekt kontrolek.</span><span class="sxs-lookup"><span data-stu-id="713b3-191">For the location, specify the same top-level folder that contains the MyControls project.</span></span>

5. <span data-ttu-id="713b3-192">Kliknij przycisk **OK** , aby utworzyć projekt.</span><span class="sxs-lookup"><span data-stu-id="713b3-192">Click **OK** to create the project.</span></span>

 <span data-ttu-id="713b3-193">Należy również dodać odwołania do biblioteki DLL, która zawiera `MyControl1` i inne zestawy.</span><span class="sxs-lookup"><span data-stu-id="713b3-193">You also need to add references to the DLL that contains `MyControl1` and other assemblies.</span></span>

1. <span data-ttu-id="713b3-194">Kliknij prawym przyciskiem myszy nazwę projektu w Eksplorator rozwiązań i wybierz polecenie **Dodaj odwołanie**.</span><span class="sxs-lookup"><span data-stu-id="713b3-194">Right-click the project name in Solution Explorer and select **Add Reference**.</span></span>

2. <span data-ttu-id="713b3-195">Kliknij kartę **Przeglądaj** i przejdź do folderu, który zawiera plik. dll.</span><span class="sxs-lookup"><span data-stu-id="713b3-195">Click the **Browse** tab, and browse to the folder that contains MyControls.dll.</span></span> <span data-ttu-id="713b3-196">W tym instruktażu ten folder jest MyControls\bin\Debug.</span><span class="sxs-lookup"><span data-stu-id="713b3-196">For this walkthrough, this folder is MyControls\bin\Debug.</span></span>

3. <span data-ttu-id="713b3-197">Wybierz pozycję Moja Controls. dll, a następnie kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="713b3-197">Select MyControls.dll, and then click **OK**.</span></span>

4. <span data-ttu-id="713b3-198">Dodaj odwołanie do zestawu WindowsFormsIntegration o nazwie WindowsFormsIntegration. dll.</span><span class="sxs-lookup"><span data-stu-id="713b3-198">Add a reference to the WindowsFormsIntegration assembly, which is named WindowsFormsIntegration.dll.</span></span>

### <a name="implementing-the-basic-layout"></a><span data-ttu-id="713b3-199">Implementowanie układu podstawowego</span><span class="sxs-lookup"><span data-stu-id="713b3-199">Implementing the Basic Layout</span></span>
 <span data-ttu-id="713b3-200">[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] Aplikacja hosta jest zaimplementowana w MainWindow. XAML.</span><span class="sxs-lookup"><span data-stu-id="713b3-200">The [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] of the host application is implemented in MainWindow.xaml.</span></span> <span data-ttu-id="713b3-201">Ten plik zawiera [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] znacznik, który definiuje układ i hostuje kontrolkę Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="713b3-201">This file contains [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] markup that defines the layout, and hosts the Windows Forms control.</span></span> <span data-ttu-id="713b3-202">Aplikacja została podzielona na trzy regiony:</span><span class="sxs-lookup"><span data-stu-id="713b3-202">The application is divided into three regions:</span></span>

- <span data-ttu-id="713b3-203">Panel **właściwości kontrolki** , który zawiera kolekcję przycisków opcji, których można użyć do modyfikacji różnych właściwości kontrolki hostowanej.</span><span class="sxs-lookup"><span data-stu-id="713b3-203">The **Control Properties** panel, which contains a collection of option buttons that you can use to modify various properties of the hosted control.</span></span>

- <span data-ttu-id="713b3-204">**Dane z panelu sterowania** , które zawiera kilka <xref:System.Windows.Controls.TextBlock> elementów, które wyświetlają dane zwrócone przez kontrolkę hostowaną.</span><span class="sxs-lookup"><span data-stu-id="713b3-204">The **Data from Control** panel, which contains several <xref:System.Windows.Controls.TextBlock> elements that display the data returned from the hosted control.</span></span>

- <span data-ttu-id="713b3-205">Kontrolka hostowana.</span><span class="sxs-lookup"><span data-stu-id="713b3-205">The hosted control itself.</span></span>

 <span data-ttu-id="713b3-206">Podstawowy układ jest przedstawiony w poniższym kodzie XAML.</span><span class="sxs-lookup"><span data-stu-id="713b3-206">The basic layout is shown in the following XAML.</span></span> <span data-ttu-id="713b3-207">Znaczniki, które są potrzebne do hostowania `MyControl1` , są pomijane w tym przykładzie, ale zostaną omówione później.</span><span class="sxs-lookup"><span data-stu-id="713b3-207">The markup that is needed to host `MyControl1` is omitted from this example, but will be discussed later.</span></span>

 <span data-ttu-id="713b3-208">Zamień kod XAML w MainWindow. XAML na następujący.</span><span class="sxs-lookup"><span data-stu-id="713b3-208">Replace the XAML in MainWindow.xaml with the following.</span></span> <span data-ttu-id="713b3-209">Jeśli używasz Visual Basic, Zmień klasę na `x:Class="MainWindow"`.</span><span class="sxs-lookup"><span data-stu-id="713b3-209">If you are using Visual Basic, change the class to `x:Class="MainWindow"`.</span></span>

 [!code-xaml[WpfHostingWindowsFormsControl#100](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/WpfHost/Page1.xaml#100)]

 <span data-ttu-id="713b3-210">Pierwszy <xref:System.Windows.Controls.StackPanel> element zawiera kilka <xref:System.Windows.Controls.RadioButton> zestawów kontrolek, które umożliwiają modyfikowanie różnych domyślnych właściwości kontrolki hostowanej.</span><span class="sxs-lookup"><span data-stu-id="713b3-210">The first <xref:System.Windows.Controls.StackPanel> element contains several sets of <xref:System.Windows.Controls.RadioButton> controls that enable you to modify various default properties of the hosted control.</span></span> <span data-ttu-id="713b3-211">Po którym następuje <xref:System.Windows.Forms.Integration.WindowsFormsHost> element, który hostuje `MyControl1`.</span><span class="sxs-lookup"><span data-stu-id="713b3-211">That is followed by a <xref:System.Windows.Forms.Integration.WindowsFormsHost> element, which hosts `MyControl1`.</span></span> <span data-ttu-id="713b3-212">Końcowy <xref:System.Windows.Controls.StackPanel> element zawiera kilka <xref:System.Windows.Controls.TextBlock> elementów, które wyświetlają dane zwracane przez hostowaną kontrolkę.</span><span class="sxs-lookup"><span data-stu-id="713b3-212">The final <xref:System.Windows.Controls.StackPanel> element contains several <xref:System.Windows.Controls.TextBlock> elements that display the data that is returned by the hosted control.</span></span> <span data-ttu-id="713b3-213">Porządkowanie elementów i <xref:System.Windows.Controls.DockPanel.Dock%2A> ustawień atrybutów i <xref:System.Windows.FrameworkElement.Height%2A> osadza formant hostowany w oknie bez przerw ani zniekształceń.</span><span class="sxs-lookup"><span data-stu-id="713b3-213">The ordering of the elements and the <xref:System.Windows.Controls.DockPanel.Dock%2A> and <xref:System.Windows.FrameworkElement.Height%2A> attribute settings embed the hosted control into the window with no gaps or distortion.</span></span>

#### <a name="hosting-the-control"></a><span data-ttu-id="713b3-214">Hostowanie kontrolki</span><span class="sxs-lookup"><span data-stu-id="713b3-214">Hosting the Control</span></span>
 <span data-ttu-id="713b3-215">Następująca edytowana wersja poprzedniego języka XAML koncentruje się na elementach, które są konieczne `MyControl1`do hostowania.</span><span class="sxs-lookup"><span data-stu-id="713b3-215">The following edited version of the previous XAML focuses on the elements that are needed to host `MyControl1`.</span></span>

 [!code-xaml[WpfHostingWindowsFormsControl#101](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/WpfHost/Page1.xaml#101)]
[!code-xaml[WpfHostingWindowsFormsControl#102](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/WpfHost/Page1.xaml#102)]

 <span data-ttu-id="713b3-216">`MyControls` Atrybut mapowanie `xmlns` przestrzeni nazw tworzy odwołanie do przestrzeni nazw, która zawiera hostowaną kontrolkę.</span><span class="sxs-lookup"><span data-stu-id="713b3-216">The `xmlns` namespace mapping attribute creates a reference to the `MyControls` namespace that contains the hosted control.</span></span> <span data-ttu-id="713b3-217">To mapowanie umożliwia reprezentowanie `MyControl1` w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] jako `<mcl:MyControl1>`.</span><span class="sxs-lookup"><span data-stu-id="713b3-217">This mapping enables you to represent `MyControl1` in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] as `<mcl:MyControl1>`.</span></span>

 <span data-ttu-id="713b3-218">Dwa elementy w kodzie XAML obsługują hosting:</span><span class="sxs-lookup"><span data-stu-id="713b3-218">Two elements in the XAML handle the hosting:</span></span>

- <span data-ttu-id="713b3-219">`WindowsFormsHost`reprezentuje element, który umożliwia hostowanie Windows Formsej kontrolki [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] w aplikacji. <xref:System.Windows.Forms.Integration.WindowsFormsHost></span><span class="sxs-lookup"><span data-stu-id="713b3-219">`WindowsFormsHost` represents the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element that enables you to host a Windows Forms control in a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application.</span></span>

- <span data-ttu-id="713b3-220">`mcl:MyControl1`, który reprezentuje `MyControl1`, jest dodawany <xref:System.Windows.Forms.Integration.WindowsFormsHost> do kolekcji podrzędnej elementu.</span><span class="sxs-lookup"><span data-stu-id="713b3-220">`mcl:MyControl1`, which represents `MyControl1`, is added to the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element's child collection.</span></span> <span data-ttu-id="713b3-221">W efekcie ten formant Windows Forms jest renderowany jako część [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] okna i można komunikować się z formantem z poziomu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="713b3-221">As a result, this Windows Forms control is rendered as part of the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] window, and you can communicate with the control from the application.</span></span>

### <a name="implementing-the-code-behind-file"></a><span data-ttu-id="713b3-222">Implementowanie pliku związanego z kodem</span><span class="sxs-lookup"><span data-stu-id="713b3-222">Implementing the Code-Behind File</span></span>
 <span data-ttu-id="713b3-223">Plik związany z kodem, MainWindow. XAML. vb lub MainWindow.XAML.cs, zawiera kod proceduralny implementujący funkcje [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] omówione w poprzedniej sekcji.</span><span class="sxs-lookup"><span data-stu-id="713b3-223">The code-behind file, MainWindow.xaml.vb or MainWindow.xaml.cs, contains the procedural code that implements the functionality of the [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] discussed in the preceding section.</span></span> <span data-ttu-id="713b3-224">Zadania podstawowe są następujące:</span><span class="sxs-lookup"><span data-stu-id="713b3-224">The primary tasks are:</span></span>

- <span data-ttu-id="713b3-225">Dołączanie obsługi zdarzeń `MyControl1`do `OnButtonClick` zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="713b3-225">Attaching an event handler to `MyControl1`'s `OnButtonClick` event.</span></span>

- <span data-ttu-id="713b3-226">Modyfikowanie różnych właściwości `MyControl1`w zależności od sposobu ustawiania kolekcji przycisków opcji.</span><span class="sxs-lookup"><span data-stu-id="713b3-226">Modifying various properties of `MyControl1`, based on how the collection of option buttons are set.</span></span>

- <span data-ttu-id="713b3-227">Wyświetlanie danych zebranych przez formant.</span><span class="sxs-lookup"><span data-stu-id="713b3-227">Displaying the data collected by the control.</span></span>

#### <a name="initializing-the-application"></a><span data-ttu-id="713b3-228">Inicjowanie aplikacji</span><span class="sxs-lookup"><span data-stu-id="713b3-228">Initializing the Application</span></span>
 <span data-ttu-id="713b3-229">Kod inicjalizacji jest zawarty w procedurze obsługi zdarzeń dla <xref:System.Windows.FrameworkElement.Loaded> zdarzenia okna i dołącza procedurę obsługi zdarzeń do `OnButtonClick` zdarzenia kontrolki.</span><span class="sxs-lookup"><span data-stu-id="713b3-229">The initialization code is contained in an event handler for the window's <xref:System.Windows.FrameworkElement.Loaded> event and attaches an event handler to the control's `OnButtonClick` event.</span></span>

 <span data-ttu-id="713b3-230">W MainWindow. XAML. vb lub MainWindow.XAML.cs Dodaj następujący kod do `MainWindow` klasy.</span><span class="sxs-lookup"><span data-stu-id="713b3-230">In MainWindow.xaml.vb or MainWindow.xaml.cs, add the following code to the `MainWindow` class.</span></span>

 [!code-csharp[WpfHostingWindowsFormsControl#11](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/WpfHost/Page1.xaml.cs#11)]
 [!code-vb[WpfHostingWindowsFormsControl#11](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/VisualBasic/WpfHost/Page1.xaml.vb#11)]

 <span data-ttu-id="713b3-231">[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] Ponieważ omówione `MyControl1` wcześniej `MyControl1` elementypodrzędne<xref:System.Windows.Forms.Integration.WindowsFormsHost> kolekcji elementów, można rzutować elementu, Abyuzyskaćodwołaniedo.<xref:System.Windows.Forms.Integration.WindowsFormsHost.Child%2A> <xref:System.Windows.Forms.Integration.WindowsFormsHost></span><span class="sxs-lookup"><span data-stu-id="713b3-231">Because the [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] discussed previously added `MyControl1` to the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element's child element collection, you can cast the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element's <xref:System.Windows.Forms.Integration.WindowsFormsHost.Child%2A> to get the reference to `MyControl1`.</span></span> <span data-ttu-id="713b3-232">Następnie można użyć tego odwołania, aby dołączyć procedurę obsługi zdarzeń do `OnButtonClick`programu.</span><span class="sxs-lookup"><span data-stu-id="713b3-232">You can then use that reference to attach an event handler to `OnButtonClick`.</span></span>

 <span data-ttu-id="713b3-233">Oprócz podawania odniesienia do samego formantu, program <xref:System.Windows.Forms.Integration.WindowsFormsHost> ujawnia szereg właściwości kontrolki, które można manipulować z poziomu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="713b3-233">In addition to providing a reference to the control itself, <xref:System.Windows.Forms.Integration.WindowsFormsHost> exposes a number of the control's properties, which you can manipulate from the application.</span></span> <span data-ttu-id="713b3-234">Kod inicjalizacji przypisuje te wartości do prywatnych zmiennych globalnych do późniejszego użycia w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="713b3-234">The initialization code assigns those values to private global variables for later use in the application.</span></span>

 <span data-ttu-id="713b3-235">Dzięki temu można łatwo uzyskać dostęp do typów w `MyControls` bibliotece DLL, Dodaj następującą `Imports` instrukcję lub `using` na początku pliku.</span><span class="sxs-lookup"><span data-stu-id="713b3-235">So that you can easily access the types in the `MyControls` DLL, add the following `Imports` or `using` statement to the top of the file.</span></span>

```vb
Imports MyControls
```

```csharp
using MyControls;
```

#### <a name="handling-the-onbuttonclick-event"></a><span data-ttu-id="713b3-236">Obsługa zdarzenia OnButtonClick</span><span class="sxs-lookup"><span data-stu-id="713b3-236">Handling the OnButtonClick Event</span></span>
 <span data-ttu-id="713b3-237">`MyControl1`Podnosi zdarzenie `OnButtonClick` , gdy użytkownik kliknie jeden z przycisków kontrolki.</span><span class="sxs-lookup"><span data-stu-id="713b3-237">`MyControl1` raises the `OnButtonClick` event when the user clicks either of the control's buttons.</span></span>

 <span data-ttu-id="713b3-238">Dodaj następujący kod do `MainWindow` klasy.</span><span class="sxs-lookup"><span data-stu-id="713b3-238">Add the following code to the `MainWindow` class.</span></span>

 [!code-csharp[WpfHostingWindowsFormsControl#12](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/WpfHost/Page1.xaml.cs#12)]
 [!code-vb[WpfHostingWindowsFormsControl#12](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/VisualBasic/WpfHost/Page1.xaml.vb#12)]

 <span data-ttu-id="713b3-239">Dane w polach tekstowych są pakowane do `MyControlEventArgs` obiektu.</span><span class="sxs-lookup"><span data-stu-id="713b3-239">The data in the text boxes is packed into the `MyControlEventArgs` object.</span></span> <span data-ttu-id="713b3-240">Jeśli użytkownik kliknie przycisk **OK** , program obsługi zdarzeń wyodrębni dane i wyświetli je w panelu poniżej `MyControl1`.</span><span class="sxs-lookup"><span data-stu-id="713b3-240">If the user clicks the **OK** button, the event handler extracts the data and displays it in the panel below `MyControl1`.</span></span>

#### <a name="modifying-the-controls-properties"></a><span data-ttu-id="713b3-241">Modyfikowanie właściwości kontrolki</span><span class="sxs-lookup"><span data-stu-id="713b3-241">Modifying the Control’s Properties</span></span>
 <span data-ttu-id="713b3-242"><xref:System.Windows.Forms.Integration.WindowsFormsHost> Element uwidacznia kilka domyślnych właściwości kontrolki hostowanej.</span><span class="sxs-lookup"><span data-stu-id="713b3-242">The <xref:System.Windows.Forms.Integration.WindowsFormsHost> element exposes several of the hosted control's default properties.</span></span> <span data-ttu-id="713b3-243">W związku z tym można zmienić wygląd formantu tak, aby pasował do stylu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="713b3-243">As a result, you can change the appearance of the control to match the style of your application more closely.</span></span> <span data-ttu-id="713b3-244">Zestawy przycisków opcji w lewym panelu umożliwiają użytkownikowi modyfikowanie kilku właściwości koloru i czcionki.</span><span class="sxs-lookup"><span data-stu-id="713b3-244">The sets of option buttons in the left panel enable the user to modify several color and font properties.</span></span> <span data-ttu-id="713b3-245">Każdy zestaw przycisków ma procedurę obsługi dla <xref:System.Windows.Controls.Primitives.ButtonBase.Click> zdarzenia, które wykrywa wybór przycisku opcji użytkownika i zmienia odpowiednią właściwość w kontrolce.</span><span class="sxs-lookup"><span data-stu-id="713b3-245">Each set of buttons has a handler for the <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event, which detects the user's option button selections and changes the corresponding property on the control.</span></span>

 <span data-ttu-id="713b3-246">Dodaj następujący kod do `MainWindow` klasy.</span><span class="sxs-lookup"><span data-stu-id="713b3-246">Add the following code to the `MainWindow` class.</span></span>

 [!code-csharp[WpfHostingWindowsFormsControl#13](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/WpfHost/Page1.xaml.cs#13)]
 [!code-vb[WpfHostingWindowsFormsControl#13](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/VisualBasic/WpfHost/Page1.xaml.vb#13)]  
  
 <span data-ttu-id="713b3-247">Skompiluj i uruchom aplikację.</span><span class="sxs-lookup"><span data-stu-id="713b3-247">Build and run the application.</span></span> <span data-ttu-id="713b3-248">Dodaj tekst do kontrolki złożonej Windows Forms, a następnie kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="713b3-248">Add some text in the Windows Forms composite control and then click **OK**.</span></span> <span data-ttu-id="713b3-249">Tekst zostanie wyświetlony w etykietach.</span><span class="sxs-lookup"><span data-stu-id="713b3-249">The text appears in the labels.</span></span> <span data-ttu-id="713b3-250">Kliknij różne przyciski radiowe, aby zobaczyć efekt na kontrolce.</span><span class="sxs-lookup"><span data-stu-id="713b3-250">Click the different radio buttons to see the effect on the control.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="713b3-251">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="713b3-251">See also</span></span>

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [<span data-ttu-id="713b3-252">Projektowanie XAML w programie Visual Studio</span><span class="sxs-lookup"><span data-stu-id="713b3-252">Design XAML in Visual Studio</span></span>](/visualstudio/designers/designing-xaml-in-visual-studio)
- [<span data-ttu-id="713b3-253">Przewodnik: Hostowanie formantu Windows Forms w WPF</span><span class="sxs-lookup"><span data-stu-id="713b3-253">Walkthrough: Hosting a Windows Forms Control in WPF</span></span>](walkthrough-hosting-a-windows-forms-control-in-wpf.md)
- [<span data-ttu-id="713b3-254">Przewodnik: Hostowanie złożonego formantu WPF w Windows Forms</span><span class="sxs-lookup"><span data-stu-id="713b3-254">Walkthrough: Hosting a WPF Composite Control in Windows Forms</span></span>](walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
