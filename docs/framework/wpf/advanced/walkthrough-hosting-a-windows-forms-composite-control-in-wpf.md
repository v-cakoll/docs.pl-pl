---
title: Hostowanie złożonego formantu Windows Forms w WPF
titleSuffix: ''
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hosting Windows Forms control in WPF [WPF]
- composite controls [WPF], hosting in WPF
ms.assetid: 96fcd78d-1c77-4206-8928-3a0579476ef4
ms.openlocfilehash: 16c09b4bb393fa830412385b4b405dd1fae9878b
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744995"
---
# <a name="walkthrough-hosting-a-windows-forms-composite-control-in-wpf"></a><span data-ttu-id="42ffd-102">Wskazówki: hosting złożonego formantu Windows Forms w WPF</span><span class="sxs-lookup"><span data-stu-id="42ffd-102">Walkthrough: Hosting a Windows Forms Composite Control in WPF</span></span>
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] <span data-ttu-id="42ffd-103">zapewnia rozbudowane środowisko do tworzenia aplikacji.</span><span class="sxs-lookup"><span data-stu-id="42ffd-103">provides a rich environment for creating applications.</span></span> <span data-ttu-id="42ffd-104">Jeśli jednak masz znaczną inwestycję w kod [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)], może być bardziej efektywne ponowne użycie co najmniej jednego kodu w aplikacji [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], a nie zapisanie go od podstaw.</span><span class="sxs-lookup"><span data-stu-id="42ffd-104">However, when you have a substantial investment in [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] code, it can be more effective to reuse at least some of that code in your [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application rather than to rewrite it from scratch.</span></span> <span data-ttu-id="42ffd-105">Najczęstszym scenariuszem jest to, że masz istniejące kontrolki Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="42ffd-105">The most common scenario is when you have existing Windows Forms controls.</span></span> <span data-ttu-id="42ffd-106">W niektórych przypadkach może nie mieć nawet dostępu do kodu źródłowego dla tych formantów.</span><span class="sxs-lookup"><span data-stu-id="42ffd-106">In some cases, you might not even have access to the source code for these controls.</span></span> [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <span data-ttu-id="42ffd-107">zapewnia prostą procedurę hostingu takich kontrolek w aplikacji [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].</span><span class="sxs-lookup"><span data-stu-id="42ffd-107">provides a straightforward procedure for hosting such controls in a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application.</span></span> <span data-ttu-id="42ffd-108">Na przykład można użyć [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] w większości programowania, jednocześnie udostępniając wyspecjalizowane kontrolki <xref:System.Windows.Forms.DataGridView>.</span><span class="sxs-lookup"><span data-stu-id="42ffd-108">For example, you can use [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] for most of your programming while hosting your specialized <xref:System.Windows.Forms.DataGridView> controls.</span></span>  
  
 <span data-ttu-id="42ffd-109">Ten Instruktaż przeprowadzi Cię przez aplikację, która hostuje Windows Forms formant złożony do wprowadzania danych w aplikacji [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].</span><span class="sxs-lookup"><span data-stu-id="42ffd-109">This walkthrough steps you through an application that hosts a Windows Forms composite control to perform data entry in a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application.</span></span> <span data-ttu-id="42ffd-110">Formant złożony jest spakowany w bibliotece DLL.</span><span class="sxs-lookup"><span data-stu-id="42ffd-110">The composite control is packaged in a DLL.</span></span> <span data-ttu-id="42ffd-111">Ta ogólna procedura może zostać rozszerzona na bardziej złożone aplikacje i kontrolki.</span><span class="sxs-lookup"><span data-stu-id="42ffd-111">This general procedure can be extended to more complex applications and controls.</span></span> <span data-ttu-id="42ffd-112">Ten przewodnik został zaprojektowany tak, aby był niemal identyczny w wyglądzie i funkcjach do [przewodnika: hosting złożonego formantu WPF w Windows Forms](walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="42ffd-112">This walkthrough is designed to be nearly identical in appearance and functionality to [Walkthrough: Hosting a WPF Composite Control in Windows Forms](walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md).</span></span> <span data-ttu-id="42ffd-113">Podstawowa różnica polega na tym, że scenariusz hostingu jest odwrócony.</span><span class="sxs-lookup"><span data-stu-id="42ffd-113">The primary difference is that the hosting scenario is reversed.</span></span>  
  
 <span data-ttu-id="42ffd-114">Przewodnik jest podzielony na dwie sekcje.</span><span class="sxs-lookup"><span data-stu-id="42ffd-114">The walkthrough is divided into two sections.</span></span> <span data-ttu-id="42ffd-115">W pierwszej sekcji krótko opisano implementację Windows Formsego formantu złożonego.</span><span class="sxs-lookup"><span data-stu-id="42ffd-115">The first section briefly describes the implementation of the Windows Forms composite control.</span></span> <span data-ttu-id="42ffd-116">W drugiej sekcji omówiono szczegółowo, jak hostować formant złożony w aplikacji [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], odbierać zdarzenia z kontrolki i uzyskiwać dostęp do niektórych właściwości kontrolki.</span><span class="sxs-lookup"><span data-stu-id="42ffd-116">The second section discusses in detail how to host the composite control in a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application, receive events from the control, and access some of the control's properties.</span></span>  
  
 <span data-ttu-id="42ffd-117">Zadania przedstawione w tym instruktażu obejmują:</span><span class="sxs-lookup"><span data-stu-id="42ffd-117">Tasks illustrated in this walkthrough include:</span></span>  
  
- <span data-ttu-id="42ffd-118">Implementowanie Windows Formsgo formantu złożonego.</span><span class="sxs-lookup"><span data-stu-id="42ffd-118">Implementing the Windows Forms composite control.</span></span>  
  
- <span data-ttu-id="42ffd-119">Implementowanie aplikacji hosta WPF.</span><span class="sxs-lookup"><span data-stu-id="42ffd-119">Implementing the WPF host application.</span></span>  
  
 <span data-ttu-id="42ffd-120">Aby uzyskać pełną listę kodów zadań przedstawionych w tym instruktażu, zobacz [hostowanie złożonego formantu Windows Forms w przykładzie WPF](https://go.microsoft.com/fwlink/?LinkID=159999).</span><span class="sxs-lookup"><span data-stu-id="42ffd-120">For a complete code listing of the tasks illustrated in this walkthrough, see [Hosting a Windows Forms Composite Control in WPF Sample](https://go.microsoft.com/fwlink/?LinkID=159999).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="42ffd-121">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="42ffd-121">Prerequisites</span></span>  

<span data-ttu-id="42ffd-122">Aby ukończyć ten przewodnik, potrzebujesz programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="42ffd-122">You need Visual Studio to complete this walkthrough.</span></span>
  
## <a name="implementing-the-windows-forms-composite-control"></a><span data-ttu-id="42ffd-123">Implementowanie Windows Formsgo formantu złożonego</span><span class="sxs-lookup"><span data-stu-id="42ffd-123">Implementing the Windows Forms Composite Control</span></span>  
 <span data-ttu-id="42ffd-124">Formant złożony Windows Forms używany w tym przykładzie jest prostym formularzem wprowadzania danych.</span><span class="sxs-lookup"><span data-stu-id="42ffd-124">The Windows Forms composite control used in this example is a simple data-entry form.</span></span> <span data-ttu-id="42ffd-125">Ten formularz przyjmuje nazwę i adres użytkownika, a następnie używa zdarzenia niestandardowego, aby zwrócić te informacje do hosta.</span><span class="sxs-lookup"><span data-stu-id="42ffd-125">This form takes the user's name and address and then uses a custom event to return that information to the host.</span></span> <span data-ttu-id="42ffd-126">Poniższa ilustracja przedstawia renderowany formant.</span><span class="sxs-lookup"><span data-stu-id="42ffd-126">The following illustration shows the rendered control.</span></span>  

 <span data-ttu-id="42ffd-127">Na poniższej ilustracji przedstawiono Windows Forms formant złożony:</span><span class="sxs-lookup"><span data-stu-id="42ffd-127">The following image shows a Windows Forms composite control:</span></span>  

 ![Zrzut ekranu, który pokazuje prosty formant Windows Forms.](./media/walkthrough-hosting-a-windows-forms-composite-control-in-wpf/windows-forms-control.gif)  
  
### <a name="creating-the-project"></a><span data-ttu-id="42ffd-129">Tworzenie projektu</span><span class="sxs-lookup"><span data-stu-id="42ffd-129">Creating the Project</span></span>  
 <span data-ttu-id="42ffd-130">Aby rozpocząć projekt:</span><span class="sxs-lookup"><span data-stu-id="42ffd-130">To start the project:</span></span>  
  
1. <span data-ttu-id="42ffd-131">Uruchom program Visual Studio i Otwórz okno dialogowe **Nowy projekt** .</span><span class="sxs-lookup"><span data-stu-id="42ffd-131">Launch Visual Studio, and open the **New Project** dialog box.</span></span>  
  
2. <span data-ttu-id="42ffd-132">W kategorii okna wybierz szablon **Biblioteka formantów Windows Forms** .</span><span class="sxs-lookup"><span data-stu-id="42ffd-132">In the Window category, select the **Windows Forms Control Library** template.</span></span>  
  
3. <span data-ttu-id="42ffd-133">Nadaj nazwę nowemu projektowi `MyControls`.</span><span class="sxs-lookup"><span data-stu-id="42ffd-133">Name the new project `MyControls`.</span></span>  
  
4. <span data-ttu-id="42ffd-134">W polu Lokalizacja Określ wygodną nazwę folderu najwyższego poziomu, na przykład `WpfHostingWindowsFormsControl`.</span><span class="sxs-lookup"><span data-stu-id="42ffd-134">For the location, specify a conveniently named top-level folder, such as `WpfHostingWindowsFormsControl`.</span></span> <span data-ttu-id="42ffd-135">Później aplikacja hosta zostanie umieszczona w tym folderze.</span><span class="sxs-lookup"><span data-stu-id="42ffd-135">Later, you will put the host application in this folder.</span></span>  
  
5. <span data-ttu-id="42ffd-136">Kliknij przycisk **OK** , aby utworzyć projekt.</span><span class="sxs-lookup"><span data-stu-id="42ffd-136">Click **OK** to create the project.</span></span> <span data-ttu-id="42ffd-137">Domyślny projekt zawiera pojedynczy formant o nazwie `UserControl1`.</span><span class="sxs-lookup"><span data-stu-id="42ffd-137">The default project contains a single control named `UserControl1`.</span></span>  
  
6. <span data-ttu-id="42ffd-138">W Eksplorator rozwiązań Zmień nazwę `UserControl1` na `MyControl1`.</span><span class="sxs-lookup"><span data-stu-id="42ffd-138">In Solution Explorer, rename `UserControl1` to `MyControl1`.</span></span>  
  
 <span data-ttu-id="42ffd-139">Projekt powinien zawierać odwołania do następujących bibliotek DLL systemu.</span><span class="sxs-lookup"><span data-stu-id="42ffd-139">Your project should have references to the following system DLLs.</span></span> <span data-ttu-id="42ffd-140">Jeśli dowolna z tych bibliotek DLL nie jest domyślnie dołączona, należy dodać je do projektu.</span><span class="sxs-lookup"><span data-stu-id="42ffd-140">If any of these DLLs are not included by default, add them to the project.</span></span>  
  
- <span data-ttu-id="42ffd-141">System</span><span class="sxs-lookup"><span data-stu-id="42ffd-141">System</span></span>  
  
- <span data-ttu-id="42ffd-142">System.Data</span><span class="sxs-lookup"><span data-stu-id="42ffd-142">System.Data</span></span>  
  
- <span data-ttu-id="42ffd-143">System.Drawing</span><span class="sxs-lookup"><span data-stu-id="42ffd-143">System.Drawing</span></span>  
  
- <span data-ttu-id="42ffd-144">System.Windows.Forms</span><span class="sxs-lookup"><span data-stu-id="42ffd-144">System.Windows.Forms</span></span>  
  
- <span data-ttu-id="42ffd-145">System.Xml</span><span class="sxs-lookup"><span data-stu-id="42ffd-145">System.Xml</span></span>  
  
### <a name="adding-controls-to-the-form"></a><span data-ttu-id="42ffd-146">Dodawanie kontrolek do formularza</span><span class="sxs-lookup"><span data-stu-id="42ffd-146">Adding Controls to the Form</span></span>  
 <span data-ttu-id="42ffd-147">Aby dodać kontrolki do formularza:</span><span class="sxs-lookup"><span data-stu-id="42ffd-147">To add controls to the form:</span></span>  
  
- <span data-ttu-id="42ffd-148">Otwórz `MyControl1` w projektancie.</span><span class="sxs-lookup"><span data-stu-id="42ffd-148">Open `MyControl1` in the designer.</span></span>  
  
 <span data-ttu-id="42ffd-149">Dodaj pięć <xref:System.Windows.Forms.Label> kontrolek i odpowiadające im kontrolki <xref:System.Windows.Forms.TextBox>, rozmiar i ułożone w taki sposób, jak na poprzedniej ilustracji, w formularzu.</span><span class="sxs-lookup"><span data-stu-id="42ffd-149">Add five <xref:System.Windows.Forms.Label> controls and their corresponding <xref:System.Windows.Forms.TextBox> controls, sized and arranged as they are in the preceding illustration, on the form.</span></span> <span data-ttu-id="42ffd-150">W przykładzie kontrolki <xref:System.Windows.Forms.TextBox> są nazwane:</span><span class="sxs-lookup"><span data-stu-id="42ffd-150">In the example, the <xref:System.Windows.Forms.TextBox> controls are named:</span></span>  
  
- `txtName`  
  
- `txtAddress`  
  
- `txtCity`  
  
- `txtState`  
  
- `txtZip`  
  
 <span data-ttu-id="42ffd-151">Dodaj dwie kontrolki <xref:System.Windows.Forms.Button> oznaczone jako **OK** i **Anuluj**.</span><span class="sxs-lookup"><span data-stu-id="42ffd-151">Add two <xref:System.Windows.Forms.Button> controls labeled **OK** and **Cancel**.</span></span> <span data-ttu-id="42ffd-152">W tym przykładzie nazwy przycisków są odpowiednio `btnOK` i `btnCancel`.</span><span class="sxs-lookup"><span data-stu-id="42ffd-152">In the example, the button names are `btnOK` and `btnCancel`, respectively.</span></span>  
  
### <a name="implementing-the-supporting-code"></a><span data-ttu-id="42ffd-153">Implementowanie kodu pomocniczego</span><span class="sxs-lookup"><span data-stu-id="42ffd-153">Implementing the Supporting Code</span></span>  
 <span data-ttu-id="42ffd-154">Otwórz formularz w widoku kodu.</span><span class="sxs-lookup"><span data-stu-id="42ffd-154">Open the form in code view.</span></span> <span data-ttu-id="42ffd-155">Kontrolka zwraca zebrane dane do hosta przez podnoszenie niestandardowego zdarzenia `OnButtonClick`.</span><span class="sxs-lookup"><span data-stu-id="42ffd-155">The control returns the collected data to its host by raising the custom `OnButtonClick` event.</span></span> <span data-ttu-id="42ffd-156">Dane są zawarte w obiekcie argumentu zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="42ffd-156">The data is contained in the event argument object.</span></span> <span data-ttu-id="42ffd-157">Poniższy kod przedstawia deklarację zdarzenia i delegata.</span><span class="sxs-lookup"><span data-stu-id="42ffd-157">The following code shows the event and delegate declaration.</span></span>  
  
 <span data-ttu-id="42ffd-158">Dodaj następujący kod do klasy `MyControl1`.</span><span class="sxs-lookup"><span data-stu-id="42ffd-158">Add the following code to the `MyControl1` class.</span></span>  
  
 [!code-csharp[WpfHostingWindowsFormsControl#2](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/MyControls/MyControl1.cs#2)]
 [!code-vb[WpfHostingWindowsFormsControl#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/VisualBasic/MyControls/MyControl1.vb#2)]

 <span data-ttu-id="42ffd-159">Klasa `MyControlEventArgs` zawiera informacje, które mają zostać zwrócone do hosta.</span><span class="sxs-lookup"><span data-stu-id="42ffd-159">The `MyControlEventArgs` class contains the information to be returned to the host.</span></span>

 <span data-ttu-id="42ffd-160">Dodaj następującą klasę do formularza.</span><span class="sxs-lookup"><span data-stu-id="42ffd-160">Add the following class to the form.</span></span>

 [!code-csharp[WpfHostingWindowsFormsControl#3](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/MyControls/MyControl1.cs#3)]
 [!code-vb[WpfHostingWindowsFormsControl#3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/VisualBasic/MyControls/MyControl1.vb#3)]

 <span data-ttu-id="42ffd-161">Gdy użytkownik kliknie przycisk **OK** lub **Anuluj** , programy obsługi zdarzeń <xref:System.Windows.Forms.Control.Click> tworzą obiekt `MyControlEventArgs` zawierający dane i zgłasza zdarzenie `OnButtonClick`.</span><span class="sxs-lookup"><span data-stu-id="42ffd-161">When the user clicks the **OK** or **Cancel** button, the <xref:System.Windows.Forms.Control.Click> event handlers create a `MyControlEventArgs` object that contains the data and raises the `OnButtonClick` event.</span></span> <span data-ttu-id="42ffd-162">Jedyną różnicą między dwoma uchwytami jest właściwość `IsOK` argumentu zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="42ffd-162">The only difference between the two handlers is the event argument's `IsOK` property.</span></span> <span data-ttu-id="42ffd-163">Ta właściwość umożliwia hostowi określenie, który przycisk został kliknięty.</span><span class="sxs-lookup"><span data-stu-id="42ffd-163">This property enables the host to determine which button was clicked.</span></span> <span data-ttu-id="42ffd-164">Dla przycisku **OK** jest ustawiona wartość `true` i `false` przycisku **Anuluj** .</span><span class="sxs-lookup"><span data-stu-id="42ffd-164">It is set to `true` for the **OK** button, and `false` for the **Cancel** button.</span></span> <span data-ttu-id="42ffd-165">Poniższy kod przedstawia dwa programy obsługi przycisków.</span><span class="sxs-lookup"><span data-stu-id="42ffd-165">The following code shows the two button handlers.</span></span>

 <span data-ttu-id="42ffd-166">Dodaj następujący kod do klasy `MyControl1`.</span><span class="sxs-lookup"><span data-stu-id="42ffd-166">Add the following code to the `MyControl1` class.</span></span>

 [!code-csharp[WpfHostingWindowsFormsControl#4](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/MyControls/MyControl1.cs#4)]
 [!code-vb[WpfHostingWindowsFormsControl#4](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/VisualBasic/MyControls/MyControl1.vb#4)]

### <a name="giving-the-assembly-a-strong-name-and-building-the-assembly"></a><span data-ttu-id="42ffd-167">Nadawanie zestawowi silnej nazwy i kompilowania zestawu</span><span class="sxs-lookup"><span data-stu-id="42ffd-167">Giving the Assembly a Strong Name and Building the Assembly</span></span>
 <span data-ttu-id="42ffd-168">Dla tego zestawu, do którego odwołuje się aplikacja [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], musi mieć silną nazwę.</span><span class="sxs-lookup"><span data-stu-id="42ffd-168">For this assembly to be referenced by a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application, it must have a strong name.</span></span> <span data-ttu-id="42ffd-169">Aby utworzyć silną nazwę, Utwórz plik klucza z SN. exe i dodaj go do projektu.</span><span class="sxs-lookup"><span data-stu-id="42ffd-169">To create a strong name, create a key file with Sn.exe and add it to your project.</span></span>

1. <span data-ttu-id="42ffd-170">Otwórz wiersz polecenia programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="42ffd-170">Open a Visual Studio command prompt.</span></span> <span data-ttu-id="42ffd-171">Aby to zrobić, kliknij menu **Start** , a następnie wybierz pozycję **wszystkie programy/Microsoft Visual Studio 2010/Visual Studio Tools/wiersz polecenia programu Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="42ffd-171">To do so, click the **Start** menu, and then select **All Programs/Microsoft Visual Studio 2010/Visual Studio Tools/Visual Studio Command Prompt**.</span></span> <span data-ttu-id="42ffd-172">Spowoduje to uruchomienie okna konsoli z dostosowanymi zmiennymi środowiskowymi.</span><span class="sxs-lookup"><span data-stu-id="42ffd-172">This launches a console window with customized environment variables.</span></span>

2. <span data-ttu-id="42ffd-173">W wierszu polecenia Użyj polecenia `cd`, aby przejść do folderu projektu.</span><span class="sxs-lookup"><span data-stu-id="42ffd-173">At the command prompt, use the `cd` command to go to your project folder.</span></span>

3. <span data-ttu-id="42ffd-174">Wygeneruj plik klucza o nazwie SNK, uruchamiając następujące polecenie.</span><span class="sxs-lookup"><span data-stu-id="42ffd-174">Generate a key file named MyControls.snk by running the following command.</span></span>

    ```console
    Sn.exe -k MyControls.snk
    ```

4. <span data-ttu-id="42ffd-175">Aby dołączyć plik klucza w projekcie, kliknij prawym przyciskiem myszy nazwę projektu w Eksplorator rozwiązań a następnie kliknij pozycję **Właściwości**.</span><span class="sxs-lookup"><span data-stu-id="42ffd-175">To include the key file in your project, right-click the project name in Solution Explorer and then click **Properties**.</span></span> <span data-ttu-id="42ffd-176">W projektancie projektu kliknij kartę **podpisywanie** , zaznacz pole wyboru **podpisz zestaw** , a następnie przejdź do pliku klucza.</span><span class="sxs-lookup"><span data-stu-id="42ffd-176">In the Project Designer, click the **Signing** tab, select the **Sign the assembly** check box and then browse to your key file.</span></span>

5. <span data-ttu-id="42ffd-177">Skompiluj rozwiązanie.</span><span class="sxs-lookup"><span data-stu-id="42ffd-177">Build the solution.</span></span> <span data-ttu-id="42ffd-178">Kompilacja spowoduje utworzenie biblioteki DLL o nazwie WebControls. dll.</span><span class="sxs-lookup"><span data-stu-id="42ffd-178">The build will produce a DLL named MyControls.dll.</span></span>

## <a name="implementing-the-wpf-host-application"></a><span data-ttu-id="42ffd-179">Implementowanie aplikacji hosta WPF</span><span class="sxs-lookup"><span data-stu-id="42ffd-179">Implementing the WPF Host Application</span></span>
 <span data-ttu-id="42ffd-180">Aplikacja hosta [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] używa kontrolki <xref:System.Windows.Forms.Integration.WindowsFormsHost> do hostowania `MyControl1`.</span><span class="sxs-lookup"><span data-stu-id="42ffd-180">The [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] host application uses the <xref:System.Windows.Forms.Integration.WindowsFormsHost> control to host `MyControl1`.</span></span> <span data-ttu-id="42ffd-181">Aplikacja obsługuje zdarzenie `OnButtonClick`, aby otrzymywać dane z formantu.</span><span class="sxs-lookup"><span data-stu-id="42ffd-181">The application handles the `OnButtonClick` event to receive the data from the control.</span></span> <span data-ttu-id="42ffd-182">Zawiera również zbiór przycisków opcji, które umożliwiają zmianę niektórych właściwości kontrolki z aplikacji [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].</span><span class="sxs-lookup"><span data-stu-id="42ffd-182">It also has a collection of option buttons that enable you to change some of the control's properties from the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application.</span></span> <span data-ttu-id="42ffd-183">Na poniższej ilustracji przedstawiono ukończoną aplikację.</span><span class="sxs-lookup"><span data-stu-id="42ffd-183">The following illustration shows the finished application.</span></span>

<span data-ttu-id="42ffd-184">Na poniższej ilustracji przedstawiono kompletną aplikację, w tym kontrolkę osadzoną w aplikacji WPF:</span><span class="sxs-lookup"><span data-stu-id="42ffd-184">The following image shows the complete application, including the control embedded in the WPF application:</span></span>

 ![Zrzut ekranu, który pokazuje kontrolkę osadzoną na stronie WPF.](./media/walkthrough-hosting-a-windows-forms-composite-control-in-wpf/windows-presentation-foundation-page-control.gif)

### <a name="creating-the-project"></a><span data-ttu-id="42ffd-186">Tworzenie projektu</span><span class="sxs-lookup"><span data-stu-id="42ffd-186">Creating the Project</span></span>
 <span data-ttu-id="42ffd-187">Aby rozpocząć projekt:</span><span class="sxs-lookup"><span data-stu-id="42ffd-187">To start the project:</span></span>

1. <span data-ttu-id="42ffd-188">Otwórz program Visual Studio i wybierz pozycję **Nowy projekt**.</span><span class="sxs-lookup"><span data-stu-id="42ffd-188">Open Visual Studio, and select **New Project**.</span></span>

2. <span data-ttu-id="42ffd-189">W kategorii okno Wybierz szablon **Aplikacja WPF** .</span><span class="sxs-lookup"><span data-stu-id="42ffd-189">In the Window category, select the **WPF Application** template.</span></span>

3. <span data-ttu-id="42ffd-190">Nadaj nazwę nowemu projektowi `WpfHost`.</span><span class="sxs-lookup"><span data-stu-id="42ffd-190">Name the new project `WpfHost`.</span></span>

4. <span data-ttu-id="42ffd-191">Dla lokalizacji Określ ten sam folder najwyższego poziomu, który zawiera projekt kontrolek.</span><span class="sxs-lookup"><span data-stu-id="42ffd-191">For the location, specify the same top-level folder that contains the MyControls project.</span></span>

5. <span data-ttu-id="42ffd-192">Kliknij przycisk **OK** , aby utworzyć projekt.</span><span class="sxs-lookup"><span data-stu-id="42ffd-192">Click **OK** to create the project.</span></span>

 <span data-ttu-id="42ffd-193">Należy również dodać odwołania do biblioteki DLL, która zawiera `MyControl1` i inne zestawy.</span><span class="sxs-lookup"><span data-stu-id="42ffd-193">You also need to add references to the DLL that contains `MyControl1` and other assemblies.</span></span>

1. <span data-ttu-id="42ffd-194">Kliknij prawym przyciskiem myszy nazwę projektu w Eksplorator rozwiązań i wybierz polecenie **Dodaj odwołanie**.</span><span class="sxs-lookup"><span data-stu-id="42ffd-194">Right-click the project name in Solution Explorer and select **Add Reference**.</span></span>

2. <span data-ttu-id="42ffd-195">Kliknij kartę **Przeglądaj** i przejdź do folderu, który zawiera plik. dll.</span><span class="sxs-lookup"><span data-stu-id="42ffd-195">Click the **Browse** tab, and browse to the folder that contains MyControls.dll.</span></span> <span data-ttu-id="42ffd-196">W tym instruktażu ten folder jest MyControls\bin\Debug.</span><span class="sxs-lookup"><span data-stu-id="42ffd-196">For this walkthrough, this folder is MyControls\bin\Debug.</span></span>

3. <span data-ttu-id="42ffd-197">Wybierz pozycję Moja Controls. dll, a następnie kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="42ffd-197">Select MyControls.dll, and then click **OK**.</span></span>

4. <span data-ttu-id="42ffd-198">Dodaj odwołanie do zestawu WindowsFormsIntegration o nazwie WindowsFormsIntegration. dll.</span><span class="sxs-lookup"><span data-stu-id="42ffd-198">Add a reference to the WindowsFormsIntegration assembly, which is named WindowsFormsIntegration.dll.</span></span>

### <a name="implementing-the-basic-layout"></a><span data-ttu-id="42ffd-199">Implementowanie układu podstawowego</span><span class="sxs-lookup"><span data-stu-id="42ffd-199">Implementing the Basic Layout</span></span>
 <span data-ttu-id="42ffd-200">[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] aplikacji hosta jest zaimplementowana w MainWindow. XAML.</span><span class="sxs-lookup"><span data-stu-id="42ffd-200">The [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] of the host application is implemented in MainWindow.xaml.</span></span> <span data-ttu-id="42ffd-201">Ten plik zawiera [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] znacznik, który definiuje układ i hostuje kontrolkę Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="42ffd-201">This file contains [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] markup that defines the layout, and hosts the Windows Forms control.</span></span> <span data-ttu-id="42ffd-202">Aplikacja została podzielona na trzy regiony:</span><span class="sxs-lookup"><span data-stu-id="42ffd-202">The application is divided into three regions:</span></span>

- <span data-ttu-id="42ffd-203">Panel **właściwości kontrolki** , który zawiera kolekcję przycisków opcji, których można użyć do modyfikacji różnych właściwości kontrolki hostowanej.</span><span class="sxs-lookup"><span data-stu-id="42ffd-203">The **Control Properties** panel, which contains a collection of option buttons that you can use to modify various properties of the hosted control.</span></span>

- <span data-ttu-id="42ffd-204">**Dane z panelu sterowania** , które zawierają kilka <xref:System.Windows.Controls.TextBlock> elementów, które wyświetlają dane zwrócone przez obsługiwaną kontrolę.</span><span class="sxs-lookup"><span data-stu-id="42ffd-204">The **Data from Control** panel, which contains several <xref:System.Windows.Controls.TextBlock> elements that display the data returned from the hosted control.</span></span>

- <span data-ttu-id="42ffd-205">Kontrolka hostowana.</span><span class="sxs-lookup"><span data-stu-id="42ffd-205">The hosted control itself.</span></span>

 <span data-ttu-id="42ffd-206">Podstawowy układ jest przedstawiony w poniższym kodzie XAML.</span><span class="sxs-lookup"><span data-stu-id="42ffd-206">The basic layout is shown in the following XAML.</span></span> <span data-ttu-id="42ffd-207">Znaczniki, które są potrzebne do hostowania `MyControl1`, są pomijane w tym przykładzie, ale zostaną omówione później.</span><span class="sxs-lookup"><span data-stu-id="42ffd-207">The markup that is needed to host `MyControl1` is omitted from this example, but will be discussed later.</span></span>

 <span data-ttu-id="42ffd-208">Zamień kod XAML w MainWindow. XAML na następujący.</span><span class="sxs-lookup"><span data-stu-id="42ffd-208">Replace the XAML in MainWindow.xaml with the following.</span></span> <span data-ttu-id="42ffd-209">Jeśli używasz Visual Basic, Zmień klasę na `x:Class="MainWindow"`.</span><span class="sxs-lookup"><span data-stu-id="42ffd-209">If you are using Visual Basic, change the class to `x:Class="MainWindow"`.</span></span>

 [!code-xaml[WpfHostingWindowsFormsControl#100](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/WpfHost/Page1.xaml#100)]

 <span data-ttu-id="42ffd-210">Pierwszy <xref:System.Windows.Controls.StackPanel> element zawiera kilka zestawów formantów <xref:System.Windows.Controls.RadioButton>, które umożliwiają modyfikowanie różnych domyślnych właściwości kontrolki hostowanej.</span><span class="sxs-lookup"><span data-stu-id="42ffd-210">The first <xref:System.Windows.Controls.StackPanel> element contains several sets of <xref:System.Windows.Controls.RadioButton> controls that enable you to modify various default properties of the hosted control.</span></span> <span data-ttu-id="42ffd-211">Następuje <xref:System.Windows.Forms.Integration.WindowsFormsHost> element, który hostuje `MyControl1`.</span><span class="sxs-lookup"><span data-stu-id="42ffd-211">That is followed by a <xref:System.Windows.Forms.Integration.WindowsFormsHost> element, which hosts `MyControl1`.</span></span> <span data-ttu-id="42ffd-212">Końcowy element <xref:System.Windows.Controls.StackPanel> zawiera kilka elementów <xref:System.Windows.Controls.TextBlock>, które wyświetlają dane zwracane przez hostowaną kontrolkę.</span><span class="sxs-lookup"><span data-stu-id="42ffd-212">The final <xref:System.Windows.Controls.StackPanel> element contains several <xref:System.Windows.Controls.TextBlock> elements that display the data that is returned by the hosted control.</span></span> <span data-ttu-id="42ffd-213">Kolejność elementów oraz ustawienia atrybutów <xref:System.Windows.Controls.DockPanel.Dock%2A> i <xref:System.Windows.FrameworkElement.Height%2A> Osadź formant hostowany w oknie bez przerw ani zniekształceń.</span><span class="sxs-lookup"><span data-stu-id="42ffd-213">The ordering of the elements and the <xref:System.Windows.Controls.DockPanel.Dock%2A> and <xref:System.Windows.FrameworkElement.Height%2A> attribute settings embed the hosted control into the window with no gaps or distortion.</span></span>

#### <a name="hosting-the-control"></a><span data-ttu-id="42ffd-214">Hostowanie kontrolki</span><span class="sxs-lookup"><span data-stu-id="42ffd-214">Hosting the Control</span></span>
 <span data-ttu-id="42ffd-215">Następująca edytowana wersja poprzedniego języka XAML koncentruje się na elementach, które są konieczne do hostowania `MyControl1`.</span><span class="sxs-lookup"><span data-stu-id="42ffd-215">The following edited version of the previous XAML focuses on the elements that are needed to host `MyControl1`.</span></span>

 [!code-xaml[WpfHostingWindowsFormsControl#101](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/WpfHost/Page1.xaml#101)]
[!code-xaml[WpfHostingWindowsFormsControl#102](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/WpfHost/Page1.xaml#102)]

 <span data-ttu-id="42ffd-216">Atrybut mapowania przestrzeni nazw `xmlns` tworzy odwołanie do przestrzeni nazw `MyControls`, która zawiera hostowaną kontrolkę.</span><span class="sxs-lookup"><span data-stu-id="42ffd-216">The `xmlns` namespace mapping attribute creates a reference to the `MyControls` namespace that contains the hosted control.</span></span> <span data-ttu-id="42ffd-217">To mapowanie umożliwia reprezentowanie `MyControl1` w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] jako `<mcl:MyControl1>`.</span><span class="sxs-lookup"><span data-stu-id="42ffd-217">This mapping enables you to represent `MyControl1` in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] as `<mcl:MyControl1>`.</span></span>

 <span data-ttu-id="42ffd-218">Dwa elementy w kodzie XAML obsługują hosting:</span><span class="sxs-lookup"><span data-stu-id="42ffd-218">Two elements in the XAML handle the hosting:</span></span>

- <span data-ttu-id="42ffd-219">`WindowsFormsHost` reprezentuje element <xref:System.Windows.Forms.Integration.WindowsFormsHost>, który umożliwia hostowanie kontrolki Windows Forms w aplikacji [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].</span><span class="sxs-lookup"><span data-stu-id="42ffd-219">`WindowsFormsHost` represents the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element that enables you to host a Windows Forms control in a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application.</span></span>

- <span data-ttu-id="42ffd-220">`mcl:MyControl1`, która reprezentuje `MyControl1`, jest dodawany do kolekcji podrzędnej <xref:System.Windows.Forms.Integration.WindowsFormsHost> elementu.</span><span class="sxs-lookup"><span data-stu-id="42ffd-220">`mcl:MyControl1`, which represents `MyControl1`, is added to the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element's child collection.</span></span> <span data-ttu-id="42ffd-221">W efekcie ten formant Windows Forms jest renderowany jako część okna [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] i można komunikować się z kontrolką z poziomu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="42ffd-221">As a result, this Windows Forms control is rendered as part of the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] window, and you can communicate with the control from the application.</span></span>

### <a name="implementing-the-code-behind-file"></a><span data-ttu-id="42ffd-222">Implementowanie pliku związanego z kodem</span><span class="sxs-lookup"><span data-stu-id="42ffd-222">Implementing the Code-Behind File</span></span>
 <span data-ttu-id="42ffd-223">Plik związany z kodem, MainWindow. XAML. vb lub MainWindow.xaml.cs, zawiera kod proceduralny implementujący funkcje [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] omówione w poprzedniej sekcji.</span><span class="sxs-lookup"><span data-stu-id="42ffd-223">The code-behind file, MainWindow.xaml.vb or MainWindow.xaml.cs, contains the procedural code that implements the functionality of the [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] discussed in the preceding section.</span></span> <span data-ttu-id="42ffd-224">Zadania podstawowe są następujące:</span><span class="sxs-lookup"><span data-stu-id="42ffd-224">The primary tasks are:</span></span>

- <span data-ttu-id="42ffd-225">Dołączanie programu obsługi zdarzeń do zdarzenia `OnButtonClick` `MyControl1`.</span><span class="sxs-lookup"><span data-stu-id="42ffd-225">Attaching an event handler to `MyControl1`'s `OnButtonClick` event.</span></span>

- <span data-ttu-id="42ffd-226">Modyfikowanie różnych właściwości `MyControl1`w zależności od tego, jak kolekcja przycisków opcji jest ustawiona.</span><span class="sxs-lookup"><span data-stu-id="42ffd-226">Modifying various properties of `MyControl1`, based on how the collection of option buttons are set.</span></span>

- <span data-ttu-id="42ffd-227">Wyświetlanie danych zebranych przez formant.</span><span class="sxs-lookup"><span data-stu-id="42ffd-227">Displaying the data collected by the control.</span></span>

#### <a name="initializing-the-application"></a><span data-ttu-id="42ffd-228">Inicjowanie aplikacji</span><span class="sxs-lookup"><span data-stu-id="42ffd-228">Initializing the Application</span></span>
 <span data-ttu-id="42ffd-229">Kod inicjalizacji jest zawarty w obsłudze zdarzeń dla zdarzenia <xref:System.Windows.FrameworkElement.Loaded> okna i dołącza procedurę obsługi zdarzeń do zdarzenia `OnButtonClick` formantu.</span><span class="sxs-lookup"><span data-stu-id="42ffd-229">The initialization code is contained in an event handler for the window's <xref:System.Windows.FrameworkElement.Loaded> event and attaches an event handler to the control's `OnButtonClick` event.</span></span>

 <span data-ttu-id="42ffd-230">W MainWindow. XAML. vb lub MainWindow.xaml.cs Dodaj następujący kod do klasy `MainWindow`.</span><span class="sxs-lookup"><span data-stu-id="42ffd-230">In MainWindow.xaml.vb or MainWindow.xaml.cs, add the following code to the `MainWindow` class.</span></span>

 [!code-csharp[WpfHostingWindowsFormsControl#11](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/WpfHost/Page1.xaml.cs#11)]
 [!code-vb[WpfHostingWindowsFormsControl#11](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/VisualBasic/WpfHost/Page1.xaml.vb#11)]

 <span data-ttu-id="42ffd-231">Ponieważ [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] omówione wcześniej `MyControl1` do kolekcji elementów podrzędnych <xref:System.Windows.Forms.Integration.WindowsFormsHost> elementu, można rzutować <xref:System.Windows.Forms.Integration.WindowsFormsHost.Child%2A> elementu <xref:System.Windows.Forms.Integration.WindowsFormsHost>, aby uzyskać odwołanie do `MyControl1`.</span><span class="sxs-lookup"><span data-stu-id="42ffd-231">Because the [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] discussed previously added `MyControl1` to the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element's child element collection, you can cast the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element's <xref:System.Windows.Forms.Integration.WindowsFormsHost.Child%2A> to get the reference to `MyControl1`.</span></span> <span data-ttu-id="42ffd-232">Następnie można użyć tego odwołania, aby dołączyć procedurę obsługi zdarzeń do `OnButtonClick`.</span><span class="sxs-lookup"><span data-stu-id="42ffd-232">You can then use that reference to attach an event handler to `OnButtonClick`.</span></span>

 <span data-ttu-id="42ffd-233">Oprócz podawania odniesienia do samego formantu, <xref:System.Windows.Forms.Integration.WindowsFormsHost> uwidacznia szereg właściwości kontrolki, które można manipulować z poziomu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="42ffd-233">In addition to providing a reference to the control itself, <xref:System.Windows.Forms.Integration.WindowsFormsHost> exposes a number of the control's properties, which you can manipulate from the application.</span></span> <span data-ttu-id="42ffd-234">Kod inicjalizacji przypisuje te wartości do prywatnych zmiennych globalnych do późniejszego użycia w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="42ffd-234">The initialization code assigns those values to private global variables for later use in the application.</span></span>

 <span data-ttu-id="42ffd-235">Dzięki temu można łatwo uzyskać dostęp do typów w `MyControls` DLL, Dodaj następującą instrukcję `Imports` lub `using` na początku pliku.</span><span class="sxs-lookup"><span data-stu-id="42ffd-235">So that you can easily access the types in the `MyControls` DLL, add the following `Imports` or `using` statement to the top of the file.</span></span>

```vb
Imports MyControls
```

```csharp
using MyControls;
```

#### <a name="handling-the-onbuttonclick-event"></a><span data-ttu-id="42ffd-236">Obsługa zdarzenia OnButtonClick</span><span class="sxs-lookup"><span data-stu-id="42ffd-236">Handling the OnButtonClick Event</span></span>
 <span data-ttu-id="42ffd-237">`MyControl1` wywołuje zdarzenie `OnButtonClick`, gdy użytkownik kliknie jeden z przycisków kontrolki.</span><span class="sxs-lookup"><span data-stu-id="42ffd-237">`MyControl1` raises the `OnButtonClick` event when the user clicks either of the control's buttons.</span></span>

 <span data-ttu-id="42ffd-238">Dodaj następujący kod do klasy `MainWindow`.</span><span class="sxs-lookup"><span data-stu-id="42ffd-238">Add the following code to the `MainWindow` class.</span></span>

 [!code-csharp[WpfHostingWindowsFormsControl#12](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/WpfHost/Page1.xaml.cs#12)]
 [!code-vb[WpfHostingWindowsFormsControl#12](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/VisualBasic/WpfHost/Page1.xaml.vb#12)]

 <span data-ttu-id="42ffd-239">Dane w polach tekstowych są pakowane do obiektu `MyControlEventArgs`.</span><span class="sxs-lookup"><span data-stu-id="42ffd-239">The data in the text boxes is packed into the `MyControlEventArgs` object.</span></span> <span data-ttu-id="42ffd-240">Jeśli użytkownik kliknie przycisk **OK** , program obsługi zdarzeń wyodrębni dane i wyświetli je w panelu poniżej `MyControl1`.</span><span class="sxs-lookup"><span data-stu-id="42ffd-240">If the user clicks the **OK** button, the event handler extracts the data and displays it in the panel below `MyControl1`.</span></span>

#### <a name="modifying-the-controls-properties"></a><span data-ttu-id="42ffd-241">Modyfikowanie właściwości kontrolki</span><span class="sxs-lookup"><span data-stu-id="42ffd-241">Modifying the Control’s Properties</span></span>
 <span data-ttu-id="42ffd-242">Element <xref:System.Windows.Forms.Integration.WindowsFormsHost> uwidacznia kilka właściwości domyślnych kontrolki hostowanej.</span><span class="sxs-lookup"><span data-stu-id="42ffd-242">The <xref:System.Windows.Forms.Integration.WindowsFormsHost> element exposes several of the hosted control's default properties.</span></span> <span data-ttu-id="42ffd-243">W związku z tym można zmienić wygląd formantu tak, aby pasował do stylu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="42ffd-243">As a result, you can change the appearance of the control to match the style of your application more closely.</span></span> <span data-ttu-id="42ffd-244">Zestawy przycisków opcji w lewym panelu umożliwiają użytkownikowi modyfikowanie kilku właściwości koloru i czcionki.</span><span class="sxs-lookup"><span data-stu-id="42ffd-244">The sets of option buttons in the left panel enable the user to modify several color and font properties.</span></span> <span data-ttu-id="42ffd-245">Każdy zestaw przycisków ma procedurę obsługi dla zdarzenia <xref:System.Windows.Controls.Primitives.ButtonBase.Click>, które wykrywa wybór przycisku opcji użytkownika i zmienia odpowiednią właściwość w formancie.</span><span class="sxs-lookup"><span data-stu-id="42ffd-245">Each set of buttons has a handler for the <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event, which detects the user's option button selections and changes the corresponding property on the control.</span></span>

 <span data-ttu-id="42ffd-246">Dodaj następujący kod do klasy `MainWindow`.</span><span class="sxs-lookup"><span data-stu-id="42ffd-246">Add the following code to the `MainWindow` class.</span></span>

 [!code-csharp[WpfHostingWindowsFormsControl#13](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/WpfHost/Page1.xaml.cs#13)]
 [!code-vb[WpfHostingWindowsFormsControl#13](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/VisualBasic/WpfHost/Page1.xaml.vb#13)]  
  
 <span data-ttu-id="42ffd-247">Skompiluj i uruchom aplikację.</span><span class="sxs-lookup"><span data-stu-id="42ffd-247">Build and run the application.</span></span> <span data-ttu-id="42ffd-248">Dodaj tekst do kontrolki złożonej Windows Forms, a następnie kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="42ffd-248">Add some text in the Windows Forms composite control and then click **OK**.</span></span> <span data-ttu-id="42ffd-249">Tekst zostanie wyświetlony w etykietach.</span><span class="sxs-lookup"><span data-stu-id="42ffd-249">The text appears in the labels.</span></span> <span data-ttu-id="42ffd-250">Kliknij różne przyciski radiowe, aby zobaczyć efekt na kontrolce.</span><span class="sxs-lookup"><span data-stu-id="42ffd-250">Click the different radio buttons to see the effect on the control.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="42ffd-251">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="42ffd-251">See also</span></span>

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [<span data-ttu-id="42ffd-252">Projektowanie XAML w programie Visual Studio</span><span class="sxs-lookup"><span data-stu-id="42ffd-252">Design XAML in Visual Studio</span></span>](/visualstudio/xaml-tools/designing-xaml-in-visual-studio)
- [<span data-ttu-id="42ffd-253">Przewodnik: hosting kontrolki Windows Forms w WPF</span><span class="sxs-lookup"><span data-stu-id="42ffd-253">Walkthrough: Hosting a Windows Forms Control in WPF</span></span>](walkthrough-hosting-a-windows-forms-control-in-wpf.md)
- [<span data-ttu-id="42ffd-254">Przewodnik: hosting złożonej kontrolki WPF w Windows Forms</span><span class="sxs-lookup"><span data-stu-id="42ffd-254">Walkthrough: Hosting a WPF Composite Control in Windows Forms</span></span>](walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
