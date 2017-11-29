---
title: "Wskazówki: hosting złożonego formantu Windows Forms w WPF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hosting Windows Forms control in WPF [WPF]
- composite controls [WPF], hosting in WPF
ms.assetid: 96fcd78d-1c77-4206-8928-3a0579476ef4
caps.latest.revision: "33"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: f9fc708d3fff3dfca29f46da8d345aeb243df38c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="walkthrough-hosting-a-windows-forms-composite-control-in-wpf"></a><span data-ttu-id="a2956-102">Wskazówki: hosting złożonego formantu Windows Forms w WPF</span><span class="sxs-lookup"><span data-stu-id="a2956-102">Walkthrough: Hosting a Windows Forms Composite Control in WPF</span></span>
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]<span data-ttu-id="a2956-103">udostępnia bogate środowisko do tworzenia aplikacji.</span><span class="sxs-lookup"><span data-stu-id="a2956-103"> provides a rich environment for creating applications.</span></span> <span data-ttu-id="a2956-104">Jeśli masz znaczących inwestycji [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] kodu, może być bardziej skuteczne ponownie użyć co najmniej części kodu w Twojej [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacji zamiast ponownego wpisywania go od początku.</span><span class="sxs-lookup"><span data-stu-id="a2956-104">However, when you have a substantial investment in [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] code, it can be more effective to reuse at least some of that code in your [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application rather than to rewrite it from scratch.</span></span> <span data-ttu-id="a2956-105">Najbardziej typowym scenariuszem jest w przypadku istniejących [!INCLUDE[TLA2#tla_winforms](../../../../includes/tla2sharptla-winforms-md.md)] kontrolki.</span><span class="sxs-lookup"><span data-stu-id="a2956-105">The most common scenario is when you have existing [!INCLUDE[TLA2#tla_winforms](../../../../includes/tla2sharptla-winforms-md.md)] controls.</span></span> <span data-ttu-id="a2956-106">W niektórych przypadkach nie jeszcze masz dostęp do kodu źródłowego dla tych kontrolek.</span><span class="sxs-lookup"><span data-stu-id="a2956-106">In some cases, you might not even have access to the source code for these controls.</span></span> [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<span data-ttu-id="a2956-107">zawiera proste procedury obsługi tych kontrolek w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacji.</span><span class="sxs-lookup"><span data-stu-id="a2956-107"> provides a straightforward procedure for hosting such controls in a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application.</span></span> <span data-ttu-id="a2956-108">Na przykład można użyć [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] dla większości sieci programowania podczas hosting sieci specjalne <xref:System.Windows.Forms.DataGridView> kontrolki.</span><span class="sxs-lookup"><span data-stu-id="a2956-108">For example, you can use [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] for most of your programming while hosting your specialized <xref:System.Windows.Forms.DataGridView> controls.</span></span>  
  
 <span data-ttu-id="a2956-109">Ten przewodnik zawiera kroki aplikacji obsługującego [!INCLUDE[TLA2#tla_winforms](../../../../includes/tla2sharptla-winforms-md.md)] złożonych kontrolek do wykonania wprowadzania danych w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacji.</span><span class="sxs-lookup"><span data-stu-id="a2956-109">This walkthrough steps you through an application that hosts a [!INCLUDE[TLA2#tla_winforms](../../../../includes/tla2sharptla-winforms-md.md)] composite control to perform data entry in a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application.</span></span> <span data-ttu-id="a2956-110">Formantu złożonego jest dostarczana w bibliotece DLL.</span><span class="sxs-lookup"><span data-stu-id="a2956-110">The composite control is packaged in a DLL.</span></span> <span data-ttu-id="a2956-111">Ta procedura ogólne można rozszerzyć do bardziej złożonych aplikacji i formanty.</span><span class="sxs-lookup"><span data-stu-id="a2956-111">This general procedure can be extended to more complex applications and controls.</span></span> <span data-ttu-id="a2956-112">W tym przewodniku została zaprojektowana jako niemal identyczny jak w wyglądu i działania [wskazówki: hostowanie formantu złożonego WPF w formularzach systemu Windows](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="a2956-112">This walkthrough is designed to be nearly identical in appearance and functionality to [Walkthrough: Hosting a WPF Composite Control in Windows Forms](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md).</span></span> <span data-ttu-id="a2956-113">Podstawowa różnica polega na tym, czy została odwrócona scenariuszu obsługi.</span><span class="sxs-lookup"><span data-stu-id="a2956-113">The primary difference is that the hosting scenario is reversed.</span></span>  
  
 <span data-ttu-id="a2956-114">Instruktaż jest podzielona na dwie sekcje.</span><span class="sxs-lookup"><span data-stu-id="a2956-114">The walkthrough is divided into two sections.</span></span> <span data-ttu-id="a2956-115">Pierwsza sekcja krótko opisano wykonania [!INCLUDE[TLA2#tla_winforms](../../../../includes/tla2sharptla-winforms-md.md)] formantu złożonego.</span><span class="sxs-lookup"><span data-stu-id="a2956-115">The first section briefly describes the implementation of the [!INCLUDE[TLA2#tla_winforms](../../../../includes/tla2sharptla-winforms-md.md)] composite control.</span></span> <span data-ttu-id="a2956-116">Druga sekcja omówiono szczegółowo do obsługi złożonych kontrolek w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacji, odbieranie zdarzeń z formantu i uzyskiwać dostęp do niektórych właściwości formantu.</span><span class="sxs-lookup"><span data-stu-id="a2956-116">The second section discusses in detail how to host the composite control in a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application, receive events from the control, and access some of the control's properties.</span></span>  
  
 <span data-ttu-id="a2956-117">Zadania przedstawione w tym przewodniku obejmują:</span><span class="sxs-lookup"><span data-stu-id="a2956-117">Tasks illustrated in this walkthrough include:</span></span>  
  
-   <span data-ttu-id="a2956-118">Wdrażanie złożonych kontrolek formularzy systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="a2956-118">Implementing the Windows Forms composite control.</span></span>  
  
-   <span data-ttu-id="a2956-119">Wdrażanie aplikacji hosta WPF.</span><span class="sxs-lookup"><span data-stu-id="a2956-119">Implementing the WPF host application.</span></span>  
  
 <span data-ttu-id="a2956-120">Kompletny kod lista zadań przedstawione w tym przewodniku, zobacz [Hosting formantu złożonego formularzy systemu Windows w przykładowym WPF](http://go.microsoft.com/fwlink/?LinkID=159999).</span><span class="sxs-lookup"><span data-stu-id="a2956-120">For a complete code listing of the tasks illustrated in this walkthrough, see [Hosting a Windows Forms Composite Control in WPF Sample](http://go.microsoft.com/fwlink/?LinkID=159999).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="a2956-121">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="a2956-121">Prerequisites</span></span>  
 <span data-ttu-id="a2956-122">Następujące składniki są wymagane do przeprowadzenia tego instruktażu:</span><span class="sxs-lookup"><span data-stu-id="a2956-122">You need the following components to complete this walkthrough:</span></span>  
  
-   [!INCLUDE[vs_dev10_long](../../../../includes/vs-dev10-long-md.md)]<span data-ttu-id="a2956-123">.</span><span class="sxs-lookup"><span data-stu-id="a2956-123">.</span></span>  
  
## <a name="implementing-the-windows-forms-composite-control"></a><span data-ttu-id="a2956-124">Implementowanie złożonego formantu formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="a2956-124">Implementing the Windows Forms Composite Control</span></span>  
 <span data-ttu-id="a2956-125">[!INCLUDE[TLA2#tla_winforms](../../../../includes/tla2sharptla-winforms-md.md)] Formantu złożonego używana w tym przykładzie jest proste wprowadzania danych formularza.</span><span class="sxs-lookup"><span data-stu-id="a2956-125">The [!INCLUDE[TLA2#tla_winforms](../../../../includes/tla2sharptla-winforms-md.md)] composite control used in this example is a simple data-entry form.</span></span> <span data-ttu-id="a2956-126">Ten formularz przyjmuje nazwę użytkownika i adres, a następnie używa niestandardowych zdarzeń do zwracania informacji do hosta.</span><span class="sxs-lookup"><span data-stu-id="a2956-126">This form takes the user's name and address and then uses a custom event to return that information to the host.</span></span> <span data-ttu-id="a2956-127">Na poniższej ilustracji przedstawiono renderowanych formantu.</span><span class="sxs-lookup"><span data-stu-id="a2956-127">The following illustration shows the rendered control.</span></span>  
  
 <span data-ttu-id="a2956-128">![Formant formularzy systemu Windows proste](../../../../docs/framework/wpf/advanced/media/wfcontrol.gif "WFControl")</span><span class="sxs-lookup"><span data-stu-id="a2956-128">![Simple Windows Forms control](../../../../docs/framework/wpf/advanced/media/wfcontrol.gif "WFControl")</span></span>  
<span data-ttu-id="a2956-129">Złożonego formantu formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="a2956-129">Windows Forms composite control</span></span>  
  
### <a name="creating-the-project"></a><span data-ttu-id="a2956-130">Tworzenie projektu</span><span class="sxs-lookup"><span data-stu-id="a2956-130">Creating the Project</span></span>  
 <span data-ttu-id="a2956-131">Aby uruchomić projekt:</span><span class="sxs-lookup"><span data-stu-id="a2956-131">To start the project:</span></span>  
  
1.  <span data-ttu-id="a2956-132">Uruchom [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)], a następnie otwórz **nowy projekt** okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="a2956-132">Launch [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)], and open the **New Project** dialog box.</span></span>  
  
2.  <span data-ttu-id="a2956-133">W oknie kategorii, wybierz **Biblioteka formantów formularzy systemu Windows** szablonu.</span><span class="sxs-lookup"><span data-stu-id="a2956-133">In the Window category, select the **Windows Forms Control Library** template.</span></span>  
  
3.  <span data-ttu-id="a2956-134">Nazwa nowego projektu `MyControls`.</span><span class="sxs-lookup"><span data-stu-id="a2956-134">Name the new project `MyControls`.</span></span>  
  
4.  <span data-ttu-id="a2956-135">Do lokalizacji, określ wygodnie nazwanego folder najwyższego poziomu, takich jak `WpfHostingWindowsFormsControl`.</span><span class="sxs-lookup"><span data-stu-id="a2956-135">For the location, specify a conveniently named top-level folder, such as `WpfHostingWindowsFormsControl`.</span></span> <span data-ttu-id="a2956-136">Później należy umieścić w folderze aplikacji hosta.</span><span class="sxs-lookup"><span data-stu-id="a2956-136">Later, you will put the host application in this folder.</span></span>  
  
5.  <span data-ttu-id="a2956-137">Kliknij przycisk **OK** Aby utworzyć projekt.</span><span class="sxs-lookup"><span data-stu-id="a2956-137">Click **OK** to create the project.</span></span> <span data-ttu-id="a2956-138">Domyślny projekt zawiera jeden formant o nazwie `UserControl1`.</span><span class="sxs-lookup"><span data-stu-id="a2956-138">The default project contains a single control named `UserControl1`.</span></span>  
  
6.  <span data-ttu-id="a2956-139">W Eksploratorze rozwiązań, Zmień nazwę `UserControl1` do `MyControl1`.</span><span class="sxs-lookup"><span data-stu-id="a2956-139">In Solution Explorer, rename `UserControl1` to `MyControl1`.</span></span>  
  
 <span data-ttu-id="a2956-140">Projekt powinien mieć odwołania do następującego systemowej biblioteki dll.</span><span class="sxs-lookup"><span data-stu-id="a2956-140">Your project should have references to the following system DLLs.</span></span> <span data-ttu-id="a2956-141">Jeśli dowolne te biblioteki DLL nie są włączone domyślnie, dodaj je do projektu.</span><span class="sxs-lookup"><span data-stu-id="a2956-141">If any of these DLLs are not included by default, add them to the project.</span></span>  
  
-   <span data-ttu-id="a2956-142">System</span><span class="sxs-lookup"><span data-stu-id="a2956-142">System</span></span>  
  
-   <span data-ttu-id="a2956-143">Dane systemowe</span><span class="sxs-lookup"><span data-stu-id="a2956-143">System.Data</span></span>  
  
-   <span data-ttu-id="a2956-144">System.Drawing</span><span class="sxs-lookup"><span data-stu-id="a2956-144">System.Drawing</span></span>  
  
-   <span data-ttu-id="a2956-145">System.Windows.Forms</span><span class="sxs-lookup"><span data-stu-id="a2956-145">System.Windows.Forms</span></span>  
  
-   <span data-ttu-id="a2956-146">System.Xml</span><span class="sxs-lookup"><span data-stu-id="a2956-146">System.Xml</span></span>  
  
### <a name="adding-controls-to-the-form"></a><span data-ttu-id="a2956-147">Dodawanie formantów do formularza</span><span class="sxs-lookup"><span data-stu-id="a2956-147">Adding Controls to the Form</span></span>  
 <span data-ttu-id="a2956-148">Do dodawania formantów do formularza:</span><span class="sxs-lookup"><span data-stu-id="a2956-148">To add controls to the form:</span></span>  
  
-   <span data-ttu-id="a2956-149">Otwórz `MyControl1` w projektancie.</span><span class="sxs-lookup"><span data-stu-id="a2956-149">Open `MyControl1` in the designer.</span></span>  
  
 <span data-ttu-id="a2956-150">Dodaj pięć <xref:System.Windows.Forms.Label> kontrolek i odpowiednie <xref:System.Windows.Forms.TextBox> formantów, wielkości i tak jak znajdują się na poprzedniej ilustracji w formularzu.</span><span class="sxs-lookup"><span data-stu-id="a2956-150">Add five <xref:System.Windows.Forms.Label> controls and their corresponding <xref:System.Windows.Forms.TextBox> controls, sized and arranged as they are in the preceding illustration, on the form.</span></span> <span data-ttu-id="a2956-151">W tym przykładzie <xref:System.Windows.Forms.TextBox> formanty są o nazwie:</span><span class="sxs-lookup"><span data-stu-id="a2956-151">In the example, the <xref:System.Windows.Forms.TextBox> controls are named:</span></span>  
  
-   `txtName`  
  
-   `txtAddress`  
  
-   `txtCity`  
  
-   `txtState`  
  
-   `txtZip`  
  
 <span data-ttu-id="a2956-152">Dodaj dwa <xref:System.Windows.Forms.Button> formantów z etykietą **OK** i **anulować**.</span><span class="sxs-lookup"><span data-stu-id="a2956-152">Add two <xref:System.Windows.Forms.Button> controls labeled **OK** and **Cancel**.</span></span> <span data-ttu-id="a2956-153">W tym przykładzie są nazwy przycisków `btnOK` i `btnCancel`odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="a2956-153">In the example, the button names are `btnOK` and `btnCancel`, respectively.</span></span>  
  
### <a name="implementing-the-supporting-code"></a><span data-ttu-id="a2956-154">Implementowanie obsługi kodu</span><span class="sxs-lookup"><span data-stu-id="a2956-154">Implementing the Supporting Code</span></span>  
 <span data-ttu-id="a2956-155">Otwórz formularz w widoku kodu.</span><span class="sxs-lookup"><span data-stu-id="a2956-155">Open the form in code view.</span></span> <span data-ttu-id="a2956-156">Formant zwraca zebranych danych do jej hosta podnosząc niestandardowego `OnButtonClick` zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="a2956-156">The control returns the collected data to its host by raising the custom `OnButtonClick` event.</span></span> <span data-ttu-id="a2956-157">Dane są zawarte w obiekt argument zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="a2956-157">The data is contained in the event argument object.</span></span> <span data-ttu-id="a2956-158">Poniższy kod przedstawia deklaracja zdarzenia a obiektem delegowanym.</span><span class="sxs-lookup"><span data-stu-id="a2956-158">The following code shows the event and delegate declaration.</span></span>  
  
 <span data-ttu-id="a2956-159">Dodaj następujący kod do `MyControl1` klasy.</span><span class="sxs-lookup"><span data-stu-id="a2956-159">Add the following code to the `MyControl1` class.</span></span>  
  
 [!code-csharp[WpfHostingWindowsFormsControl#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/MyControls/MyControl1.cs#2)]
 [!code-vb[WpfHostingWindowsFormsControl#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/VisualBasic/MyControls/MyControl1.vb#2)]  
  
 <span data-ttu-id="a2956-160">`MyControlEventArgs` Klasa zawiera informacje, które ma zostać zwrócona do hosta.</span><span class="sxs-lookup"><span data-stu-id="a2956-160">The `MyControlEventArgs` class contains the information to be returned to the host.</span></span>  
  
 <span data-ttu-id="a2956-161">Dodaj następujące klasy w formularzu.</span><span class="sxs-lookup"><span data-stu-id="a2956-161">Add the following class to the form.</span></span>  
  
 [!code-csharp[WpfHostingWindowsFormsControl#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/MyControls/MyControl1.cs#3)]
 [!code-vb[WpfHostingWindowsFormsControl#3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/VisualBasic/MyControls/MyControl1.vb#3)]  
  
 <span data-ttu-id="a2956-162">Po kliknięciu przez użytkownika **OK** lub **anulować** przycisku <xref:System.Windows.Forms.Control.Click> tworzenie obsługi zdarzeń `MyControlEventArgs` obiekt, który zawiera dane i zgłasza `OnButtonClick` zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="a2956-162">When the user clicks the **OK** or **Cancel** button, the <xref:System.Windows.Forms.Control.Click> event handlers create a `MyControlEventArgs` object that contains the data and raises the `OnButtonClick` event.</span></span> <span data-ttu-id="a2956-163">Argument zdarzenia jest jedyną różnicą między dwóch metod obsługi `IsOK` właściwości.</span><span class="sxs-lookup"><span data-stu-id="a2956-163">The only difference between the two handlers is the event argument's `IsOK` property.</span></span> <span data-ttu-id="a2956-164">Ta właściwość umożliwia hosta określić, który przycisk został kliknięty.</span><span class="sxs-lookup"><span data-stu-id="a2956-164">This property enables the host to determine which button was clicked.</span></span> <span data-ttu-id="a2956-165">Ma ustawioną wartość `true` dla **OK** przycisk, a `false` dla **anulować** przycisku.</span><span class="sxs-lookup"><span data-stu-id="a2956-165">It is set to `true` for the **OK** button, and `false` for the **Cancel** button.</span></span> <span data-ttu-id="a2956-166">Poniższy kod przedstawia programy obsługi dwóch przycisków.</span><span class="sxs-lookup"><span data-stu-id="a2956-166">The following code shows the two button handlers.</span></span>  
  
 <span data-ttu-id="a2956-167">Dodaj następujący kod do `MyControl1` klasy.</span><span class="sxs-lookup"><span data-stu-id="a2956-167">Add the following code to the `MyControl1` class.</span></span>  
  
 [!code-csharp[WpfHostingWindowsFormsControl#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/MyControls/MyControl1.cs#4)]
 [!code-vb[WpfHostingWindowsFormsControl#4](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/VisualBasic/MyControls/MyControl1.vb#4)]  
  
### <a name="giving-the-assembly-a-strong-name-and-building-the-assembly"></a><span data-ttu-id="a2956-168">Nadanie silnej nazwy zestawu i kompilowania zestawu</span><span class="sxs-lookup"><span data-stu-id="a2956-168">Giving the Assembly a Strong Name and Building the Assembly</span></span>  
 <span data-ttu-id="a2956-169">Dla tego zestawu można odwoływać się [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacji, musi mieć silnej nazwy.</span><span class="sxs-lookup"><span data-stu-id="a2956-169">For this assembly to be referenced by a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application, it must have a strong name.</span></span> <span data-ttu-id="a2956-170">Aby utworzyć silnej nazwy, Utwórz plik klucza o Sn.exe i dodaj go do projektu.</span><span class="sxs-lookup"><span data-stu-id="a2956-170">To create a strong name, create a key file with Sn.exe and add it to your project.</span></span>  
  
1.  <span data-ttu-id="a2956-171">Otwórz [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)] wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="a2956-171">Open a [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)] command prompt.</span></span> <span data-ttu-id="a2956-172">Aby to zrobić, kliknij przycisk **Start** menu, a następnie wybierz **wszystkie programy/Microsoft Studio 2010/Visual Studio Tools/Visual Studio wiersz polecenia programu Visual**.</span><span class="sxs-lookup"><span data-stu-id="a2956-172">To do so, click the **Start** menu, and then select **All Programs/Microsoft Visual Studio 2010/Visual Studio Tools/Visual Studio Command Prompt**.</span></span> <span data-ttu-id="a2956-173">Spowoduje to uruchomienie ze zmiennymi dostosowane środowisko okna konsoli.</span><span class="sxs-lookup"><span data-stu-id="a2956-173">This launches a console window with customized environment variables.</span></span>  
  
2.  <span data-ttu-id="a2956-174">W wierszu polecenia, użyj `cd` polecenie, aby przejść do folderu projektu.</span><span class="sxs-lookup"><span data-stu-id="a2956-174">At the command prompt, use the `cd` command to go to your project folder.</span></span>  
  
3.  <span data-ttu-id="a2956-175">Generuj plik klucza o nazwie MyControls.snk, uruchamiając następujące polecenie.</span><span class="sxs-lookup"><span data-stu-id="a2956-175">Generate a key file named MyControls.snk by running the following command.</span></span>  
  
    ```  
    Sn.exe -k MyControls.snk  
    ```  
  
4.  <span data-ttu-id="a2956-176">Aby dołączyć plik klucza do projektu, kliknij prawym przyciskiem myszy nazwę projektu w Eksploratorze rozwiązań, a następnie kliknij przycisk **właściwości**.</span><span class="sxs-lookup"><span data-stu-id="a2956-176">To include the key file in your project, right-click the project name in Solution Explorer and then click **Properties**.</span></span> <span data-ttu-id="a2956-177">W Projektancie projektu kliknij **podpisywanie** wybierz opcję **Podpisz zestaw** zaznacz pole wyboru, a następnie przejdź do pliku klucza.</span><span class="sxs-lookup"><span data-stu-id="a2956-177">In the Project Designer, click the **Signing** tab, select the **Sign the assembly** check box and then browse to your key file.</span></span>  
  
5.  <span data-ttu-id="a2956-178">Skompiluj rozwiązanie.</span><span class="sxs-lookup"><span data-stu-id="a2956-178">Build the solution.</span></span> <span data-ttu-id="a2956-179">Kompilacja utworzy o nazwie MyControls.dll biblioteki DLL.</span><span class="sxs-lookup"><span data-stu-id="a2956-179">The build will produce a DLL named MyControls.dll.</span></span>  
  
## <a name="implementing-the-wpf-host-application"></a><span data-ttu-id="a2956-180">Wdrażanie aplikacji hosta WPF</span><span class="sxs-lookup"><span data-stu-id="a2956-180">Implementing the WPF Host Application</span></span>  
 <span data-ttu-id="a2956-181">[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Hosta aplikacja używa <xref:System.Windows.Forms.Integration.WindowsFormsHost> formantu do hosta `MyControl1`.</span><span class="sxs-lookup"><span data-stu-id="a2956-181">The [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] host application uses the <xref:System.Windows.Forms.Integration.WindowsFormsHost> control to host `MyControl1`.</span></span> <span data-ttu-id="a2956-182">Uchwyty aplikacji `OnButtonClick` zdarzeń do odbierania danych z formantu.</span><span class="sxs-lookup"><span data-stu-id="a2956-182">The application handles the `OnButtonClick` event to receive the data from the control.</span></span> <span data-ttu-id="a2956-183">Ma również zbiór przycisków opcji, które umożliwiają zmianę niektórych właściwości formantu z [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacji.</span><span class="sxs-lookup"><span data-stu-id="a2956-183">It also has a collection of option buttons that enable you to change some of the control's properties from the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application.</span></span> <span data-ttu-id="a2956-184">Na poniższej ilustracji przedstawiono Zakończono aplikacji.</span><span class="sxs-lookup"><span data-stu-id="a2956-184">The following illustration shows the finished application.</span></span>  
  
 <span data-ttu-id="a2956-185">![Formantu osadzonego w stronie WPF](../../../../docs/framework/wpf/advanced/media/avalonhost.gif "AvalonHost")</span><span class="sxs-lookup"><span data-stu-id="a2956-185">![A control embedded in a WPF page](../../../../docs/framework/wpf/advanced/media/avalonhost.gif "AvalonHost")</span></span>  
<span data-ttu-id="a2956-186">Kompletna aplikacja przedstawiający formantu osadzonego w aplikacji WPF</span><span class="sxs-lookup"><span data-stu-id="a2956-186">The complete application, showing the control embedded in the WPF application</span></span>  
  
### <a name="creating-the-project"></a><span data-ttu-id="a2956-187">Tworzenie projektu</span><span class="sxs-lookup"><span data-stu-id="a2956-187">Creating the Project</span></span>  
 <span data-ttu-id="a2956-188">Aby uruchomić projekt:</span><span class="sxs-lookup"><span data-stu-id="a2956-188">To start the project:</span></span>  
  
1.  <span data-ttu-id="a2956-189">Otwórz [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)]i wybierz **nowy projekt**.</span><span class="sxs-lookup"><span data-stu-id="a2956-189">Open [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)], and select **New Project**.</span></span>  
  
2.  <span data-ttu-id="a2956-190">W oknie kategorii, wybierz **aplikacji WPF** szablonu.</span><span class="sxs-lookup"><span data-stu-id="a2956-190">In the Window category, select the **WPF Application** template.</span></span>
  
3.  <span data-ttu-id="a2956-191">Nazwa nowego projektu `WpfHost`.</span><span class="sxs-lookup"><span data-stu-id="a2956-191">Name the new project `WpfHost`.</span></span>  
  
4.  <span data-ttu-id="a2956-192">W przypadku lokalizacji określ tego samego folderu najwyższego poziomu, który zawiera MyControls projektu.</span><span class="sxs-lookup"><span data-stu-id="a2956-192">For the location, specify the same top-level folder that contains the MyControls project.</span></span>  
  
5.  <span data-ttu-id="a2956-193">Kliknij przycisk **OK** Aby utworzyć projekt.</span><span class="sxs-lookup"><span data-stu-id="a2956-193">Click **OK** to create the project.</span></span>  
  
 <span data-ttu-id="a2956-194">Należy również dodać odwołania do biblioteki DLL zawierającej `MyControl1` i innych zestawów.</span><span class="sxs-lookup"><span data-stu-id="a2956-194">You also need to add references to the DLL that contains `MyControl1` and other assemblies.</span></span>  
  
1.  <span data-ttu-id="a2956-195">Kliknij prawym przyciskiem myszy nazwę projektu w Eksploratorze rozwiązań i wybierz **Dodaj odwołanie**.</span><span class="sxs-lookup"><span data-stu-id="a2956-195">Right-click the project name in Solution Explorer and select **Add Reference**.</span></span>  
  
2.  <span data-ttu-id="a2956-196">Kliknij przycisk **Przeglądaj** karcie i przejdź do folderu, który zawiera MyControls.dll.</span><span class="sxs-lookup"><span data-stu-id="a2956-196">Click the **Browse** tab, and browse to the folder that contains MyControls.dll.</span></span> <span data-ttu-id="a2956-197">W ramach tego przewodnika ten folder jest MyControls\bin\Debug.</span><span class="sxs-lookup"><span data-stu-id="a2956-197">For this walkthrough, this folder is MyControls\bin\Debug.</span></span>  
  
3.  <span data-ttu-id="a2956-198">Wybierz MyControls.dll, a następnie kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="a2956-198">Select MyControls.dll, and then click **OK**.</span></span>  
  
4.  <span data-ttu-id="a2956-199">Dodaj odwołanie do zestawu WindowsFormsIntegration, o nazwie WindowsFormsIntegration.dll.</span><span class="sxs-lookup"><span data-stu-id="a2956-199">Add a reference to the WindowsFormsIntegration assembly, which is named WindowsFormsIntegration.dll.</span></span>  
  
### <a name="implementing-the-basic-layout"></a><span data-ttu-id="a2956-200">Podstawowe układu Implementowanie</span><span class="sxs-lookup"><span data-stu-id="a2956-200">Implementing the Basic Layout</span></span>  
 <span data-ttu-id="a2956-201">[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] Hosta aplikacji jest zaimplementowana w MainWindow.xaml.</span><span class="sxs-lookup"><span data-stu-id="a2956-201">The [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] of the host application is implemented in MainWindow.xaml.</span></span> <span data-ttu-id="a2956-202">Ten plik zawiera [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] kod znaczników, który definiuje układ i obsługuje [!INCLUDE[TLA2#tla_winforms](../../../../includes/tla2sharptla-winforms-md.md)] formantu.</span><span class="sxs-lookup"><span data-stu-id="a2956-202">This file contains [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] markup that defines the layout, and hosts the [!INCLUDE[TLA2#tla_winforms](../../../../includes/tla2sharptla-winforms-md.md)] control.</span></span> <span data-ttu-id="a2956-203">Aplikacja jest podzielona na trzy obszary:</span><span class="sxs-lookup"><span data-stu-id="a2956-203">The application is divided into three regions:</span></span>  
  
-   <span data-ttu-id="a2956-204">**Właściwości formantu** panelu, które zawiera kolekcję przycisków opcji, które służy do modyfikowania różnych właściwości obsługiwanego formantu.</span><span class="sxs-lookup"><span data-stu-id="a2956-204">The **Control Properties** panel, which contains a collection of option buttons that you can use to modify various properties of the hosted control.</span></span>  
  
-   <span data-ttu-id="a2956-205">**Danych z formantu** panelu, które zawiera kilka <xref:System.Windows.Controls.TextBlock> elementów, które przedstawiają dane zwrócone z obsługiwanego formantu.</span><span class="sxs-lookup"><span data-stu-id="a2956-205">The **Data from Control** panel, which contains several <xref:System.Windows.Controls.TextBlock> elements that display the data returned from the hosted control.</span></span>  
  
-   <span data-ttu-id="a2956-206">Hostowanej samego formantu.</span><span class="sxs-lookup"><span data-stu-id="a2956-206">The hosted control itself.</span></span>  
  
 <span data-ttu-id="a2956-207">Podstawowy układ przedstawiono w następujących XAML.</span><span class="sxs-lookup"><span data-stu-id="a2956-207">The basic layout is shown in the following XAML.</span></span> <span data-ttu-id="a2956-208">Kod znaczników, który jest wymagany do hosta `MyControl1` pominięto w tym przykładzie, ale zostanie dokładnie omówione później.</span><span class="sxs-lookup"><span data-stu-id="a2956-208">The markup that is needed to host `MyControl1` is omitted from this example, but will be discussed later.</span></span>  
  
 <span data-ttu-id="a2956-209">Zamień XAML w MainWindow.xaml poniżej.</span><span class="sxs-lookup"><span data-stu-id="a2956-209">Replace the XAML in MainWindow.xaml with the following.</span></span> <span data-ttu-id="a2956-210">Jeśli używasz programu Visual Basic, Zmień klasę, aby `x:Class="MainWindow"`.</span><span class="sxs-lookup"><span data-stu-id="a2956-210">If you are using Visual Basic, change the class to `x:Class="MainWindow"`.</span></span>  
  
 [!code-xaml[WpfHostingWindowsFormsControl#100](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/WpfHost/Page1.xaml#100)]  
  
 <span data-ttu-id="a2956-211">Pierwszy <xref:System.Windows.Controls.StackPanel> element zawiera kilka zestawów <xref:System.Windows.Controls.RadioButton> formantów, które umożliwiają modyfikowanie różnych właściwości domyślne obsługiwanego formantu.</span><span class="sxs-lookup"><span data-stu-id="a2956-211">The first <xref:System.Windows.Controls.StackPanel> element contains several sets of <xref:System.Windows.Controls.RadioButton> controls that enable you to modify various default properties of the hosted control.</span></span> <span data-ttu-id="a2956-212">Którym następuje <xref:System.Windows.Forms.Integration.WindowsFormsHost> elementów, których hostów `MyControl1`.</span><span class="sxs-lookup"><span data-stu-id="a2956-212">That is followed by a <xref:System.Windows.Forms.Integration.WindowsFormsHost> element, which hosts `MyControl1`.</span></span> <span data-ttu-id="a2956-213">Ostatni <xref:System.Windows.Controls.StackPanel> element zawiera kilka <xref:System.Windows.Controls.TextBlock> elementów, które przedstawiają dane zwracane przez obsługiwanego formantu.</span><span class="sxs-lookup"><span data-stu-id="a2956-213">The final <xref:System.Windows.Controls.StackPanel> element contains several <xref:System.Windows.Controls.TextBlock> elements that display the data that is returned by the hosted control.</span></span> <span data-ttu-id="a2956-214">Kolejność elementów i <xref:System.Windows.Controls.DockPanel.Dock%2A> i <xref:System.Windows.FrameworkElement.Height%2A> ustawienia atrybutu osadzić obsługiwanego formantu do okna bez przerw i zakłóceń.</span><span class="sxs-lookup"><span data-stu-id="a2956-214">The ordering of the elements and the <xref:System.Windows.Controls.DockPanel.Dock%2A> and <xref:System.Windows.FrameworkElement.Height%2A> attribute settings embed the hosted control into the window with no gaps or distortion.</span></span>  
  
#### <a name="hosting-the-control"></a><span data-ttu-id="a2956-215">Hosting kontrolki</span><span class="sxs-lookup"><span data-stu-id="a2956-215">Hosting the Control</span></span>  
 <span data-ttu-id="a2956-216">Następująca wersja edytowanego poprzednie XAML skupia się wokół elementów, które są wymagane do hosta `MyControl1`.</span><span class="sxs-lookup"><span data-stu-id="a2956-216">The following edited version of the previous XAML focuses on the elements that are needed to host `MyControl1`.</span></span>  
  
 [!code-xaml[WpfHostingWindowsFormsControl#101](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/WpfHost/Page1.xaml#101)]  
[!code-xaml[WpfHostingWindowsFormsControl#102](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/WpfHost/Page1.xaml#102)]  
  
 <span data-ttu-id="a2956-217">`xmlns` Atrybutu mapowania przestrzeni nazw tworzy odwołanie do `MyControls` przestrzeni nazw, która zawiera obsługiwanego formantu.</span><span class="sxs-lookup"><span data-stu-id="a2956-217">The `xmlns` namespace mapping attribute creates a reference to the `MyControls` namespace that contains the hosted control.</span></span> <span data-ttu-id="a2956-218">To mapowanie umożliwia reprezentują `MyControl1` w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] jako `<mcl:MyControl1>`.</span><span class="sxs-lookup"><span data-stu-id="a2956-218">This mapping enables you to represent `MyControl1` in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] as `<mcl:MyControl1>`.</span></span>  
  
 <span data-ttu-id="a2956-219">Dwa elementy w kodzie XAML obsługi hostingu:</span><span class="sxs-lookup"><span data-stu-id="a2956-219">Two elements in the XAML handle the hosting:</span></span>  
  
-   <span data-ttu-id="a2956-220">`WindowsFormsHost`reprezentuje <xref:System.Windows.Forms.Integration.WindowsFormsHost> element, który pozwala na hoście [!INCLUDE[TLA2#tla_winforms](../../../../includes/tla2sharptla-winforms-md.md)] kontroli w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacji.</span><span class="sxs-lookup"><span data-stu-id="a2956-220">`WindowsFormsHost` represents the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element that enables you to host a [!INCLUDE[TLA2#tla_winforms](../../../../includes/tla2sharptla-winforms-md.md)] control in a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application.</span></span>  
  
-   <span data-ttu-id="a2956-221">`mcl:MyControl1`, która reprezentuje `MyControl1`, jest dodawany do <xref:System.Windows.Forms.Integration.WindowsFormsHost> elementu podrzędnej kolekcji.</span><span class="sxs-lookup"><span data-stu-id="a2956-221">`mcl:MyControl1`, which represents `MyControl1`, is added to the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element's child collection.</span></span> <span data-ttu-id="a2956-222">W związku z tym to [!INCLUDE[TLA2#tla_winforms](../../../../includes/tla2sharptla-winforms-md.md)] renderowania formantu jako część [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] , a następnie może komunikować się z urządzeniem za pomocą aplikacji.</span><span class="sxs-lookup"><span data-stu-id="a2956-222">As a result, this [!INCLUDE[TLA2#tla_winforms](../../../../includes/tla2sharptla-winforms-md.md)] control is rendered as part of the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] window, and you can communicate with the control from the application.</span></span>  
  
### <a name="implementing-the-code-behind-file"></a><span data-ttu-id="a2956-223">Implementacja pliku CodeBehind</span><span class="sxs-lookup"><span data-stu-id="a2956-223">Implementing the Code-Behind File</span></span>  
 <span data-ttu-id="a2956-224">Plik CodeBehind, MainWindow.xaml.vb lub MainWindow.xaml.cs, zawiera kod procedury, która implementuje funkcje [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] omówione w poprzedniej sekcji.</span><span class="sxs-lookup"><span data-stu-id="a2956-224">The code-behind file, MainWindow.xaml.vb or MainWindow.xaml.cs, contains the procedural code that implements the functionality of the [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] discussed in the preceding section.</span></span> <span data-ttu-id="a2956-225">Podstawowe zadania są:</span><span class="sxs-lookup"><span data-stu-id="a2956-225">The primary tasks are:</span></span>  
  
-   <span data-ttu-id="a2956-226">Dołączanie do obsługi zdarzeń `MyControl1`w `OnButtonClick` zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="a2956-226">Attaching an event handler to `MyControl1`'s `OnButtonClick` event.</span></span>  
  
-   <span data-ttu-id="a2956-227">Modyfikowanie właściwości różnych `MyControl1`, zależności od konfiguracji kolekcji przycisków opcji.</span><span class="sxs-lookup"><span data-stu-id="a2956-227">Modifying various properties of `MyControl1`, based on how the collection of option buttons are set.</span></span>  
  
-   <span data-ttu-id="a2956-228">Wyświetlanie danych zebranych przez formant.</span><span class="sxs-lookup"><span data-stu-id="a2956-228">Displaying the data collected by the control.</span></span>  
  
#### <a name="initializing-the-application"></a><span data-ttu-id="a2956-229">Inicjowanie aplikacji</span><span class="sxs-lookup"><span data-stu-id="a2956-229">Initializing the Application</span></span>  
 <span data-ttu-id="a2956-230">Kod inicjujący znajduje się w obsłudze zdarzeń w oknie <xref:System.Windows.FrameworkElement.Loaded> zdarzeń i dołącza program obsługi zdarzeń do formantu `OnButtonClick` zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="a2956-230">The initialization code is contained in an event handler for the window's <xref:System.Windows.FrameworkElement.Loaded> event and attaches an event handler to the control's `OnButtonClick` event.</span></span>  
  
 <span data-ttu-id="a2956-231">W MainWindow.xaml.vb lub MainWindow.xaml.cs, Dodaj następujący kod, aby `MainWindow` klasy.</span><span class="sxs-lookup"><span data-stu-id="a2956-231">In MainWindow.xaml.vb or MainWindow.xaml.cs, add the following code to the `MainWindow` class.</span></span>  
  
 [!code-csharp[WpfHostingWindowsFormsControl#11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/WpfHost/Page1.xaml.cs#11)]
 [!code-vb[WpfHostingWindowsFormsControl#11](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/VisualBasic/WpfHost/Page1.xaml.vb#11)]  
  
 <span data-ttu-id="a2956-232">Ponieważ [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] omówione uprzednio dodanych `MyControl1` do <xref:System.Windows.Forms.Integration.WindowsFormsHost> kolekcji elementów podrzędnych elementu, można rzutować <xref:System.Windows.Forms.Integration.WindowsFormsHost> elementu <xref:System.Windows.Forms.Integration.WindowsFormsHost.Child%2A> można pobrać odwołania do `MyControl1`.</span><span class="sxs-lookup"><span data-stu-id="a2956-232">Because the [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] discussed previously added `MyControl1` to the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element's child element collection, you can cast the <xref:System.Windows.Forms.Integration.WindowsFormsHost> element's <xref:System.Windows.Forms.Integration.WindowsFormsHost.Child%2A> to get the reference to `MyControl1`.</span></span> <span data-ttu-id="a2956-233">Następnie służy odwołujące się do dołączenia do obsługi zdarzeń `OnButtonClick`.</span><span class="sxs-lookup"><span data-stu-id="a2956-233">You can then use that reference to attach an event handler to `OnButtonClick`.</span></span>  
  
 <span data-ttu-id="a2956-234">Oprócz zapewnienia odwołanie do samej kontrolce, <xref:System.Windows.Forms.Integration.WindowsFormsHost> przedstawia liczbę właściwości formantu, które można manipulować, korzystając z aplikacji.</span><span class="sxs-lookup"><span data-stu-id="a2956-234">In addition to providing a reference to the control itself, <xref:System.Windows.Forms.Integration.WindowsFormsHost> exposes a number of the control's properties, which you can manipulate from the application.</span></span> <span data-ttu-id="a2956-235">Kod inicjujący przypisuje tych wartości do prywatnego zmienne globalne do późniejszego użytku w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="a2956-235">The initialization code assigns those values to private global variables for later use in the application.</span></span>  
  
 <span data-ttu-id="a2956-236">Tak, aby mogli łatwo uzyskiwać dostęp typu `MyControls` biblioteki DLL, Dodaj następujący `Imports` lub `using` instrukcji na początku pliku.</span><span class="sxs-lookup"><span data-stu-id="a2956-236">So that you can easily access the types in the `MyControls` DLL, add the following `Imports` or `using` statement to the top of the file.</span></span>  
  
```vb  
Imports MyControls  
```  
  
```csharp  
using MyControls;  
```  
  
#### <a name="handling-the-onbuttonclick-event"></a><span data-ttu-id="a2956-237">Obsługa zdarzeń OnButtonClick</span><span class="sxs-lookup"><span data-stu-id="a2956-237">Handling the OnButtonClick Event</span></span>  
 <span data-ttu-id="a2956-238">`MyControl1`zgłasza `OnButtonClick` zdarzenie, gdy użytkownik kliknie jeden z przycisków kontrolki.</span><span class="sxs-lookup"><span data-stu-id="a2956-238">`MyControl1` raises the `OnButtonClick` event when the user clicks either of the control's buttons.</span></span>  
  
 <span data-ttu-id="a2956-239">Dodaj następujący kod do `MainWindow` klasy.</span><span class="sxs-lookup"><span data-stu-id="a2956-239">Add the following code to the `MainWindow` class.</span></span>  
  
 [!code-csharp[WpfHostingWindowsFormsControl#12](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/WpfHost/Page1.xaml.cs#12)]
 [!code-vb[WpfHostingWindowsFormsControl#12](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/VisualBasic/WpfHost/Page1.xaml.vb#12)]  
  
 <span data-ttu-id="a2956-240">Spakowane dane w polach tekstowych w `MyControlEventArgs` obiektu.</span><span class="sxs-lookup"><span data-stu-id="a2956-240">The data in the text boxes is packed into the `MyControlEventArgs` object.</span></span> <span data-ttu-id="a2956-241">Gdy użytkownik kliknie **OK** przycisku, program obsługi zdarzeń wyodrębnia dane i wyświetla je w panelu poniżej `MyControl1`.</span><span class="sxs-lookup"><span data-stu-id="a2956-241">If the user clicks the **OK** button, the event handler extracts the data and displays it in the panel below `MyControl1`.</span></span>  
  
#### <a name="modifying-the-controls-properties"></a><span data-ttu-id="a2956-242">Modyfikowanie właściwości formantu</span><span class="sxs-lookup"><span data-stu-id="a2956-242">Modifying the Control’s Properties</span></span>  
 <span data-ttu-id="a2956-243"><xref:System.Windows.Forms.Integration.WindowsFormsHost> Element udostępnia kilka właściwości domyślne obsługiwanego formantu.</span><span class="sxs-lookup"><span data-stu-id="a2956-243">The <xref:System.Windows.Forms.Integration.WindowsFormsHost> element exposes several of the hosted control's default properties.</span></span> <span data-ttu-id="a2956-244">W związku z tym można zmienić wygląd formantu, aby lepiej pasuje styl aplikacji.</span><span class="sxs-lookup"><span data-stu-id="a2956-244">As a result, you can change the appearance of the control to match the style of your application more closely.</span></span> <span data-ttu-id="a2956-245">Zestawy przycisków opcji znajdujących się w lewym panelu zezwolić użytkownikowi na modyfikowanie kilka właściwości kolorów i czcionek.</span><span class="sxs-lookup"><span data-stu-id="a2956-245">The sets of option buttons in the left panel enable the user to modify several color and font properties.</span></span> <span data-ttu-id="a2956-246">Każdy zestaw przycisków ma obsługi dla <xref:System.Windows.Controls.Primitives.ButtonBase.Click> zdarzenie, które wykrywa przycisk Opcje użytkownika i zmienia odpowiadających im właściwości w formancie.</span><span class="sxs-lookup"><span data-stu-id="a2956-246">Each set of buttons has a handler for the <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event, which detects the user's option button selections and changes the corresponding property on the control.</span></span>  
  
 <span data-ttu-id="a2956-247">Dodaj następujący kod do `MainWindow` klasy.</span><span class="sxs-lookup"><span data-stu-id="a2956-247">Add the following code to the `MainWindow` class.</span></span>  
  
 [!code-csharp[WpfHostingWindowsFormsControl#13](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/CSharp/WpfHost/Page1.xaml.cs#13)]
 [!code-vb[WpfHostingWindowsFormsControl#13](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WpfHostingWindowsFormsControl/VisualBasic/WpfHost/Page1.xaml.vb#13)]  
  
 <span data-ttu-id="a2956-248">Skompiluj i uruchom aplikację.</span><span class="sxs-lookup"><span data-stu-id="a2956-248">Build and run the application.</span></span> <span data-ttu-id="a2956-249">Dodaj część tekstu w złożonych kontrolek formularzy systemu Windows, a następnie kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="a2956-249">Add some text in the Windows Forms composite control and then click **OK**.</span></span> <span data-ttu-id="a2956-250">Tekst jest wyświetlany w etykiecie.</span><span class="sxs-lookup"><span data-stu-id="a2956-250">The text appears in the labels.</span></span> <span data-ttu-id="a2956-251">Kliknij przyciski różnych opcji, aby zobaczyć efekt w formancie.</span><span class="sxs-lookup"><span data-stu-id="a2956-251">Click the different radio buttons to see the effect on the control.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a2956-252">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a2956-252">See Also</span></span>  
 <xref:System.Windows.Forms.Integration.ElementHost>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [<span data-ttu-id="a2956-253">Projektant WPF</span><span class="sxs-lookup"><span data-stu-id="a2956-253">WPF Designer</span></span>](http://msdn.microsoft.com/en-us/c6c65214-8411-4e16-b254-163ed4099c26)  
 [<span data-ttu-id="a2956-254">Wskazówki: Hostowanie kontrolki formularza systemu Windows na platformie WPF</span><span class="sxs-lookup"><span data-stu-id="a2956-254">Walkthrough: Hosting a Windows Forms Control in WPF</span></span>](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-control-in-wpf.md)  
 [<span data-ttu-id="a2956-255">Wskazówki: Hostowanie formantu złożonego WPF w formularzach systemu Windows</span><span class="sxs-lookup"><span data-stu-id="a2956-255">Walkthrough: Hosting a WPF Composite Control in Windows Forms</span></span>](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
