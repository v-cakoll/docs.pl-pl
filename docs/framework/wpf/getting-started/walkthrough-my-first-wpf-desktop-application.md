---
title: "Wskazówki: Pierwszy WPF pulpitu aplikację"
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
- getting started [WPF], WPF
- WPF [WPF], getting started
ms.assetid: b96bed40-8946-4285-8fe4-88045ab854ed
caps.latest.revision: "71"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: f9818231a68f5c2ac2a6852f27e4876baa9728e7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="walkthrough-my-first-wpf-desktop-application"></a><span data-ttu-id="9cd99-102">Wskazówki: Pierwszy WPF pulpitu aplikację</span><span class="sxs-lookup"><span data-stu-id="9cd99-102">Walkthrough: My first WPF desktop application</span></span>
<span data-ttu-id="9cd99-103">Ten przewodnik zawiera wprowadzenie do rozwoju [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] aplikacji, która zawiera elementy, które są wspólne dla większości [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] aplikacji: [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] znaczników, związane z kodem, definicji aplikacji, kontrolki, układ Powiązanie danych i style.</span><span class="sxs-lookup"><span data-stu-id="9cd99-103">This walkthrough provides an introduction to the development of a [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] application that includes the elements that are common to most [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] applications: [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] markup, code-behind, application definitions, controls, layout, data binding, and styles.</span></span> 
  
 <span data-ttu-id="9cd99-104">Ten przewodnik zawiera informacje rozwoju prostą [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] aplikacji, wykonując następujące kroki.</span><span class="sxs-lookup"><span data-stu-id="9cd99-104">This walkthrough guides you through the development of a simple [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] application using the following steps.</span></span> 
  
-   <span data-ttu-id="9cd99-105">Definiowanie [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] do projektowania wyglądu aplikacji [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)].</span><span class="sxs-lookup"><span data-stu-id="9cd99-105">Defining [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] to design the appearance of the application's [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)].</span></span> 
  
-   <span data-ttu-id="9cd99-106">Pisanie kodu do kompilacji zachowania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="9cd99-106">Writing code to build the application's behavior.</span></span> 
  
-   <span data-ttu-id="9cd99-107">Tworzenie definicji aplikacji, aby zarządzać aplikacją.</span><span class="sxs-lookup"><span data-stu-id="9cd99-107">Creating an application definition to manage the application.</span></span> 
  
-   <span data-ttu-id="9cd99-108">Dodawanie formantów i tworzenie układu utworzenie aplikacji [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)].</span><span class="sxs-lookup"><span data-stu-id="9cd99-108">Adding controls and creating the layout to compose the application [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)].</span></span> 
  
-   <span data-ttu-id="9cd99-109">Tworzenie stylów, aby utworzyć spójny wygląd aplikacji [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)].</span><span class="sxs-lookup"><span data-stu-id="9cd99-109">Creating styles to create a consistent appearance throughout an application's [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)].</span></span> 
  
-   <span data-ttu-id="9cd99-110">Powiązanie [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] danych zarówno wypełnić [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] z danych i Zachowaj dane i [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] zsynchronizowane.</span><span class="sxs-lookup"><span data-stu-id="9cd99-110">Binding the [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] to data to both populate the [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] from data and keep the data and [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] synchronized.</span></span> 
  
 <span data-ttu-id="9cd99-111">Do końca tego przewodnika, dlatego zostanie utworzone autonomiczny [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] aplikacji, która umożliwia użytkownikom wyświetlanie raportów wydatków dla wybranych użytkowników.</span><span class="sxs-lookup"><span data-stu-id="9cd99-111">By the end of the walkthrough, you will have built a standalone [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] application that allows users to view expense reports for selected people.</span></span> <span data-ttu-id="9cd99-112">Aplikacja będzie składać się z kilku [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] stron, które znajdują się w oknie stylu przeglądarki.</span><span class="sxs-lookup"><span data-stu-id="9cd99-112">The application will be composed of several [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] pages that are hosted in a browser-style window.</span></span> 
  
 <span data-ttu-id="9cd99-113">Przykładowy kod, który jest używany do tworzenia tego przewodnika jest dostępny dla obu [!INCLUDE[TLA#tla_visualb](../../../../includes/tlasharptla-visualb-md.md)] i [!INCLUDE[TLA#tla_cshrp](../../../../includes/tlasharptla-cshrp-md.md)] w [wprowadzenie do tworzenia aplikacji WPF](http://go.microsoft.com/fwlink/?LinkID=160008).</span><span class="sxs-lookup"><span data-stu-id="9cd99-113">The sample code that is used to build this walkthrough is available for both [!INCLUDE[TLA#tla_visualb](../../../../includes/tlasharptla-visualb-md.md)] and [!INCLUDE[TLA#tla_cshrp](../../../../includes/tlasharptla-cshrp-md.md)] at  [Introduction to Building WPF Applications](http://go.microsoft.com/fwlink/?LinkID=160008).</span></span> 

## <a name="prerequisites"></a><span data-ttu-id="9cd99-114">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="9cd99-114">Prerequisites</span></span>  

- [!INCLUDE[vs_dev11_long](../../../../includes/vs-dev11-long-md.md)]<span data-ttu-id="9cd99-115">lub nowszy</span><span class="sxs-lookup"><span data-stu-id="9cd99-115"> or later</span></span>

<span data-ttu-id="9cd99-116">Aby uzyskać więcej informacji na temat instalowania najnowszej wersji programu Visual Studio, zobacz [program Visual Studio](/visualstudio/install/install-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="9cd99-116">For more information about installing the latest version of Visual Studio, see [Install Visual Studio](/visualstudio/install/install-visual-studio).</span></span>
  
## <a name="creating-the-application-project"></a><span data-ttu-id="9cd99-117">Tworzenie projektu aplikacji</span><span class="sxs-lookup"><span data-stu-id="9cd99-117">Creating the application project</span></span>  
 <span data-ttu-id="9cd99-118">W tej sekcji utworzysz infrastruktury aplikacji, w tym definicji aplikacji, dwie strony i obrazu.</span><span class="sxs-lookup"><span data-stu-id="9cd99-118">In this section, you create the application infrastructure, which includes an application definition, two pages, and an image.</span></span> 
  
1. <span data-ttu-id="9cd99-119">Utwórz nowy projekt aplikacji WPF w języku Visual Basic lub Visual C# o nazwie `ExpenseIt`.</span><span class="sxs-lookup"><span data-stu-id="9cd99-119">Create a new WPF Application project in Visual Basic or Visual C# named `ExpenseIt`.</span></span> <span data-ttu-id="9cd99-120">Aby uzyskać więcej informacji, zobacz [porady: Tworzenie nowego projektu aplikacji WPF](http://msdn.microsoft.com/en-us/1f6aea7a-33e1-4d3f-8555-1daa42e95d82).</span><span class="sxs-lookup"><span data-stu-id="9cd99-120">For more information, see [How to: Create a New WPF Application Project](http://msdn.microsoft.com/en-us/1f6aea7a-33e1-4d3f-8555-1daa42e95d82).</span></span> 
  
    > [!NOTE]
    >  <span data-ttu-id="9cd99-121">W tym przewodniku zastosowano <xref:System.Windows.Controls.DataGrid> formant, który jest dostępny w .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="9cd99-121">This walkthrough uses the <xref:System.Windows.Controls.DataGrid> control that is available in the .NET Framework 4.</span></span> <span data-ttu-id="9cd99-122">Należy się upewnić, że projekt jest przeznaczony dla programu .NET Framework 4 lub nowszej.</span><span class="sxs-lookup"><span data-stu-id="9cd99-122">Be sure that your project targets the .NET Framework 4 or later.</span></span> <span data-ttu-id="9cd99-123">Aby uzyskać więcej informacji, zobacz[porady: wersja docelowa platformy .NET Framework](/visualstudio/ide/how-to-target-a-version-of-the-dotnet-framework).</span><span class="sxs-lookup"><span data-stu-id="9cd99-123">For more information, see[How to: Target a Version of the .NET Framework](/visualstudio/ide/how-to-target-a-version-of-the-dotnet-framework).</span></span> 
  
2. <span data-ttu-id="9cd99-124">Otwórz Application.xaml (Visual Basic) lub App.xaml (C#).</span><span class="sxs-lookup"><span data-stu-id="9cd99-124">Open Application.xaml (Visual Basic) or App.xaml (C#).</span></span> 
  
     <span data-ttu-id="9cd99-125">To [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] plik definiuje [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] aplikacji i wszystkie zasoby aplikacji.</span><span class="sxs-lookup"><span data-stu-id="9cd99-125">This [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] file defines a [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] application and any application resources.</span></span> <span data-ttu-id="9cd99-126">Ten plik możesz również użyć do określenia [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] które automatycznie pokazuje podczas uruchamiania aplikacji; w takim przypadku MainWindow.xaml.</span><span class="sxs-lookup"><span data-stu-id="9cd99-126">You also use this file to specify the [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] that automatically shows when the application starts; in this case, MainWindow.xaml.</span></span> 
  
     <span data-ttu-id="9cd99-127">Twoje [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] powinna wyglądać następująco w języku Visual Basic:</span><span class="sxs-lookup"><span data-stu-id="9cd99-127">Your [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] should look like this in Visual Basic:</span></span>  
  
    [!code-xaml[ExpenseIt#1_A](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/Application.xaml#1_a)]  
  
     <span data-ttu-id="9cd99-128">Lub podobny do tego w języku C#:</span><span class="sxs-lookup"><span data-stu-id="9cd99-128">Or like this in C#:</span></span>  
  
    [!code-xaml[ExpenseIt#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/App.xaml#1)]  
  
3. <span data-ttu-id="9cd99-129">Otwórz MainWindow.xaml.</span><span class="sxs-lookup"><span data-stu-id="9cd99-129">Open MainWindow.xaml.</span></span> 
  
     <span data-ttu-id="9cd99-130">To [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] plik jest w głównym oknie aplikacji i wyświetla zawartości dla strony.</span><span class="sxs-lookup"><span data-stu-id="9cd99-130">This [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] file is the main window of your application and displays content created in pages.</span></span> <span data-ttu-id="9cd99-131"><xref:System.Windows.Window> Klasa definiuje właściwości okna, takie jak jego tytuł, rozmiaru lub ikona i obsługuje zdarzenia, takie jak zamknięcie lub ukrywanie.</span><span class="sxs-lookup"><span data-stu-id="9cd99-131">The <xref:System.Windows.Window> class defines the properties of a window, such as its title, size, or icon, and handles events, such as closing or hiding.</span></span> 
  
4. <span data-ttu-id="9cd99-132">Zmień <xref:System.Windows.Window> elementu <xref:System.Windows.Navigation.NavigationWindow>.</span><span class="sxs-lookup"><span data-stu-id="9cd99-132">Change the <xref:System.Windows.Window> element to a <xref:System.Windows.Navigation.NavigationWindow>.</span></span> 
  
     <span data-ttu-id="9cd99-133">Ta aplikacja przejdzie do innej zawartości w zależności od interakcji z użytkownikiem.</span><span class="sxs-lookup"><span data-stu-id="9cd99-133">This application will navigate to different content depending on the user interaction.</span></span> <span data-ttu-id="9cd99-134">W związku z tym głównym <xref:System.Windows.Window> musi zostać zmienione w celu <xref:System.Windows.Navigation.NavigationWindow>.</span><span class="sxs-lookup"><span data-stu-id="9cd99-134">Therefore, the main <xref:System.Windows.Window> needs to be changed to a <xref:System.Windows.Navigation.NavigationWindow>.</span></span> <span data-ttu-id="9cd99-135"><xref:System.Windows.Navigation.NavigationWindow>dziedziczy wszystkie właściwości <xref:System.Windows.Window>.</span><span class="sxs-lookup"><span data-stu-id="9cd99-135"><xref:System.Windows.Navigation.NavigationWindow> inherits all the properties of <xref:System.Windows.Window>.</span></span> <span data-ttu-id="9cd99-136"><xref:System.Windows.Navigation.NavigationWindow> Elementu w pliku XAML tworzy wystąpienie <xref:System.Windows.Navigation.NavigationWindow> klasy.</span><span class="sxs-lookup"><span data-stu-id="9cd99-136">The <xref:System.Windows.Navigation.NavigationWindow> element in the XAML file creates an instance of the <xref:System.Windows.Navigation.NavigationWindow> class.</span></span> <span data-ttu-id="9cd99-137">Aby uzyskać więcej informacji, zobacz [omówienie nawigacji](../../../../docs/framework/wpf/app-development/navigation-overview.md).</span><span class="sxs-lookup"><span data-stu-id="9cd99-137">For more information, see [Navigation Overview](../../../../docs/framework/wpf/app-development/navigation-overview.md).</span></span> 
  
5. <span data-ttu-id="9cd99-138">Zmień następujące właściwości na <xref:System.Windows.Navigation.NavigationWindow> elementu:</span><span class="sxs-lookup"><span data-stu-id="9cd99-138">Change the following properties on the <xref:System.Windows.Navigation.NavigationWindow> element:</span></span>  
  
    -   <span data-ttu-id="9cd99-139">Ustaw <xref:System.Windows.Window.Title%2A> dla właściwości "Programu ExpenseIt".</span><span class="sxs-lookup"><span data-stu-id="9cd99-139">Set the <xref:System.Windows.Window.Title%2A> property to "ExpenseIt".</span></span> 
  
    -   <span data-ttu-id="9cd99-140">Ustaw <xref:System.Windows.FrameworkElement.Width%2A> właściwości do 500 pikseli.</span><span class="sxs-lookup"><span data-stu-id="9cd99-140">Set the <xref:System.Windows.FrameworkElement.Width%2A> property to 500 pixels.</span></span> 
  
    -   <span data-ttu-id="9cd99-141">Ustaw <xref:System.Windows.FrameworkElement.Height%2A> właściwości 350 pikseli.</span><span class="sxs-lookup"><span data-stu-id="9cd99-141">Set the <xref:System.Windows.FrameworkElement.Height%2A> property to 350 pixels.</span></span> 
  
    -   <span data-ttu-id="9cd99-142">Usuń <xref:System.Windows.Controls.Grid> elementy między <xref:System.Windows.Navigation.NavigationWindow> tagów.</span><span class="sxs-lookup"><span data-stu-id="9cd99-142">Remove the <xref:System.Windows.Controls.Grid> elements between the <xref:System.Windows.Navigation.NavigationWindow> tags.</span></span> 
  
     <span data-ttu-id="9cd99-143">Twoje [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] powinna wyglądać następująco w języku Visual Basic:</span><span class="sxs-lookup"><span data-stu-id="9cd99-143">Your [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] should look like this in Visual Basic:</span></span>  
  
    [!code-xaml[ExpenseIt#2_A](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt/MainWindow.xaml#2_a)]  
  
     <span data-ttu-id="9cd99-144">Lub podobny do tego w języku C#:</span><span class="sxs-lookup"><span data-stu-id="9cd99-144">Or like this in C#:</span></span>  
  
    [!code-xaml[ExpenseIt#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/MainWindow.xaml#2)]  
  
6. <span data-ttu-id="9cd99-145">Otwórz MainWindow.xaml.vb lub MainWindow.xaml.cs.</span><span class="sxs-lookup"><span data-stu-id="9cd99-145">Open MainWindow.xaml.vb or MainWindow.xaml.cs.</span></span> 
  
     <span data-ttu-id="9cd99-146">Ten plik jest plikiem CodeBehind, zawierającego kod obsługujący zdarzenia zadeklarowany w MainWindow.xaml.</span><span class="sxs-lookup"><span data-stu-id="9cd99-146">This file is a code-behind file that contains code to handle the events declared in MainWindow.xaml.</span></span> <span data-ttu-id="9cd99-147">Ten plik zawiera klasę częściową dla okna zdefiniowany w języku XAML.</span><span class="sxs-lookup"><span data-stu-id="9cd99-147">This file contains a partial class for the window defined in XAML.</span></span> 
  
7. <span data-ttu-id="9cd99-148">Jeśli używasz języka C#, zmień `MainWindow` pochodzi od klasy <xref:System.Windows.Navigation.NavigationWindow>.</span><span class="sxs-lookup"><span data-stu-id="9cd99-148">If you are using C#, change the `MainWindow` class to derive from <xref:System.Windows.Navigation.NavigationWindow>.</span></span> 
  
     <span data-ttu-id="9cd99-149">W języku Visual Basic odbywa się to automatycznie po zmianie okna w języku XAML.</span><span class="sxs-lookup"><span data-stu-id="9cd99-149">In Visual Basic, this happens automatically when you change the window in XAML.</span></span> 
  
     <span data-ttu-id="9cd99-150">Kod powinien wyglądać następująco.</span><span class="sxs-lookup"><span data-stu-id="9cd99-150">Your code should look like this.</span></span> 
  
    [!code-csharp[ExpenseIt#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/MainWindow.xaml.cs#3)]
    [!code-vb[ExpenseIt#3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/MainWindow.xaml.vb#3)]  
  
## <a name="adding-files-to-the-application"></a><span data-ttu-id="9cd99-151">Dodawanie plików do aplikacji</span><span class="sxs-lookup"><span data-stu-id="9cd99-151">Adding files to the application</span></span>  
 <span data-ttu-id="9cd99-152">W tej sekcji możesz dodać dwie strony i obraz do aplikacji.</span><span class="sxs-lookup"><span data-stu-id="9cd99-152">In this section, you add two pages and an image to the application.</span></span> 
  
1. <span data-ttu-id="9cd99-153">Dodawanie nowej strony (WPF) do projektu o nazwie `ExpenseItHome.xaml`.</span><span class="sxs-lookup"><span data-stu-id="9cd99-153">Add a new Page (WPF) to the project named `ExpenseItHome.xaml`.</span></span> <span data-ttu-id="9cd99-154">Aby uzyskać więcej informacji, zobacz [porady: dodawanie nowych elementów do projektu WPF](http://msdn.microsoft.com/en-us/17e6b238-fc32-4385-98ef-2f66ca09d9ad).</span><span class="sxs-lookup"><span data-stu-id="9cd99-154">For more information, see [How to: Add New Items to a WPF Project](http://msdn.microsoft.com/en-us/17e6b238-fc32-4385-98ef-2f66ca09d9ad).</span></span> 
  
     <span data-ttu-id="9cd99-155">Ta strona jest pierwszą stroną, która jest wyświetlana, gdy aplikacja jest uruchamiana.</span><span class="sxs-lookup"><span data-stu-id="9cd99-155">This page is the first page that is displayed when the application is launched.</span></span> <span data-ttu-id="9cd99-156">Pojawi się lista osób, z którego użytkownik może wybrać osobę, aby wyświetlić raport wydatków dla.</span><span class="sxs-lookup"><span data-stu-id="9cd99-156">It will show a list of people from which a user can select a person to show an expense report for.</span></span> 
  
2. <span data-ttu-id="9cd99-157">Otwórz ExpenseItHome.xaml.</span><span class="sxs-lookup"><span data-stu-id="9cd99-157">Open ExpenseItHome.xaml.</span></span> 
  
3. <span data-ttu-id="9cd99-158">Ustaw <xref:System.Windows.Controls.Page.Title%2A> do programu "ExpenseIt — strona główna".</span><span class="sxs-lookup"><span data-stu-id="9cd99-158">Set the <xref:System.Windows.Controls.Page.Title%2A> to "ExpenseIt - Home".</span></span> 
  
     <span data-ttu-id="9cd99-159">Twoje [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] powinna wyglądać następująco w języku Visual Basic:</span><span class="sxs-lookup"><span data-stu-id="9cd99-159">Your [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] should look like this in Visual Basic:</span></span>  
  
    [!code-xaml[ExpenseIt#6_A](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseItHome.xaml#6_a)]  
  
     <span data-ttu-id="9cd99-160">Lub to w języku C#:</span><span class="sxs-lookup"><span data-stu-id="9cd99-160">Or this in C#:</span></span>  
  
    [!code-xaml[ExpenseIt#6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt2/ExpenseItHome.xaml#6)]  
  
4. <span data-ttu-id="9cd99-161">Otwórz MainWindow.xaml.</span><span class="sxs-lookup"><span data-stu-id="9cd99-161">Open MainWindow.xaml.</span></span> 
  
5. <span data-ttu-id="9cd99-162">Ustaw <xref:System.Windows.Navigation.NavigationWindow.Source%2A> właściwość <xref:System.Windows.Navigation.NavigationWindow> do "ExpenseItHome.xaml".</span><span class="sxs-lookup"><span data-stu-id="9cd99-162">Set the <xref:System.Windows.Navigation.NavigationWindow.Source%2A> property on the <xref:System.Windows.Navigation.NavigationWindow> to "ExpenseItHome.xaml".</span></span> 
  
     <span data-ttu-id="9cd99-163">To ustawienie ExpenseItHome.xaml się na pierwszej stronie otwarty podczas uruchamiania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="9cd99-163">This sets ExpenseItHome.xaml to be the first page opened when the application starts.</span></span> <span data-ttu-id="9cd99-164">Twoje [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] powinna wyglądać następująco w języku Visual Basic:</span><span class="sxs-lookup"><span data-stu-id="9cd99-164">Your [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] should look like this in Visual Basic:</span></span>  
  
    [!code-xaml[ExpenseIt#7_A](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/MainWindow.xaml#7_a)]  
  
     <span data-ttu-id="9cd99-165">Lub to w języku C#:</span><span class="sxs-lookup"><span data-stu-id="9cd99-165">Or this in C#:</span></span>  
  
    [!code-xaml[ExpenseIt#7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt2/MainWindow.xaml#7)]  
  
6. <span data-ttu-id="9cd99-166">Dodawanie nowej strony (WPF) do projektu o nazwie `ExpenseReportPage.xaml`.</span><span class="sxs-lookup"><span data-stu-id="9cd99-166">Add a new Page (WPF) to the project named `ExpenseReportPage.xaml`.</span></span> 
  
     <span data-ttu-id="9cd99-167">Ta strona będzie przedstawiał raportu wydatków wybranego na ExpenseItHome.xaml osoby.</span><span class="sxs-lookup"><span data-stu-id="9cd99-167">This page will show the expense report for the person that is selected on ExpenseItHome.xaml.</span></span> 
  
7. <span data-ttu-id="9cd99-168">Otwórz ExpenseReportPage.xaml.</span><span class="sxs-lookup"><span data-stu-id="9cd99-168">Open ExpenseReportPage.xaml.</span></span> 
  
8. <span data-ttu-id="9cd99-169">Ustaw <xref:System.Windows.Controls.Page.Title%2A> do programu "ExpenseIt — widok wydatków".</span><span class="sxs-lookup"><span data-stu-id="9cd99-169">Set the <xref:System.Windows.Controls.Page.Title%2A> to "ExpenseIt - View Expense".</span></span> 
  
     <span data-ttu-id="9cd99-170">Twoje [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] powinna wyglądać następująco w języku Visual Basic:</span><span class="sxs-lookup"><span data-stu-id="9cd99-170">Your [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] should look like this in Visual Basic:</span></span>  
  
    [!code-xaml[ExpenseIt#4_A](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseReportPage.xaml#4_a)]  
  
     <span data-ttu-id="9cd99-171">Lub to w języku C#:</span><span class="sxs-lookup"><span data-stu-id="9cd99-171">Or this in C#:</span></span>  
  
    [!code-xaml[ExpenseIt#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/ExpenseReportPage.xaml#4)]  
  
9. <span data-ttu-id="9cd99-172">Otwórz ExpenseItHome.xaml.vb i ExpenseReportPage.xaml.vb, lub ExpenseItHome.xaml.cs i ExpenseReportPage.xaml.cs.</span><span class="sxs-lookup"><span data-stu-id="9cd99-172">Open ExpenseItHome.xaml.vb and ExpenseReportPage.xaml.vb, or ExpenseItHome.xaml.cs and ExpenseReportPage.xaml.cs.</span></span> 
  
     <span data-ttu-id="9cd99-173">Visual Studio automatycznie tworzy w kodzie pliku, podczas tworzenia nowego pliku strony.</span><span class="sxs-lookup"><span data-stu-id="9cd99-173">When you create a new Page file, Visual Studio automatically creates a code behind file.</span></span> <span data-ttu-id="9cd99-174">Te pliki związane z kodem obsługi logiki w odpowiedzi na dane wejściowe użytkownika.</span><span class="sxs-lookup"><span data-stu-id="9cd99-174">These code-behind files handle the logic for responding to user input.</span></span> 
  
     <span data-ttu-id="9cd99-175">Kod powinien wyglądać następująco.</span><span class="sxs-lookup"><span data-stu-id="9cd99-175">Your code should look like this.</span></span> 
  
    [!code-csharp[ExpenseIt#2_5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt2/ExpenseItHome.xaml.cs#2_5)]
    [!code-vb[ExpenseIt#2_5](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseItHome.xaml.vb#2_5)]  
  
    [!code-csharp[ExpenseIt#5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/ExpenseReportPage.xaml.cs#5)]
    [!code-vb[ExpenseIt#5](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseReportPage.xaml.vb#5)]  
  
10. <span data-ttu-id="9cd99-176">Dodaj obraz o nazwie watermark.png do projektu.</span><span class="sxs-lookup"><span data-stu-id="9cd99-176">Add an image named watermark.png to the project.</span></span> <span data-ttu-id="9cd99-177">Można utworzyć własny obraz lub skopiuj plik z przykładowym kodzie.</span><span class="sxs-lookup"><span data-stu-id="9cd99-177">You can either create your own image, or copy the file from the sample code.</span></span> <span data-ttu-id="9cd99-178">Aby uzyskać więcej informacji, zobacz [NIB: porady: Dodawanie istniejących elementów do projektu](http://msdn.microsoft.com/en-us/15f4cfb7-78ab-457f-9f14-099a25a6a2d3).</span><span class="sxs-lookup"><span data-stu-id="9cd99-178">For more information, see [NIB:How to: Add Existing Items to a Project](http://msdn.microsoft.com/en-us/15f4cfb7-78ab-457f-9f14-099a25a6a2d3).</span></span> 

## <a name="building-and-running-the-application"></a><span data-ttu-id="9cd99-179">Tworzenie i uruchamianie aplikacji</span><span class="sxs-lookup"><span data-stu-id="9cd99-179">Building and running the application</span></span>  
 <span data-ttu-id="9cd99-180">W tej sekcji możesz skompilować i uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="9cd99-180">In this section, you build and run the application.</span></span> 
  
1. <span data-ttu-id="9cd99-181">Tworzenie i uruchamianie aplikacji, naciskając klawisz F5 lub wybierz **Rozpocznij debugowanie** z **debugowania** menu.</span><span class="sxs-lookup"><span data-stu-id="9cd99-181">Build and run the application by pressing F5 or select **Start Debugging** from the **Debug** menu.</span></span> 
  
     <span data-ttu-id="9cd99-182">Na poniższej ilustracji przedstawiono aplikację z <xref:System.Windows.Navigation.NavigationWindow> przycisków.</span><span class="sxs-lookup"><span data-stu-id="9cd99-182">The following illustration shows the application with the <xref:System.Windows.Navigation.NavigationWindow> buttons.</span></span> 
  
     <span data-ttu-id="9cd99-183">![Zrzut ekranu przedstawiający przykładowy programu ExpenseIt](../../../../docs/framework/wpf/getting-started/media/gettingstartedfigure1.png "GettingStartedFigure1")</span><span class="sxs-lookup"><span data-stu-id="9cd99-183">![ExpenseIt sample screen shot](../../../../docs/framework/wpf/getting-started/media/gettingstartedfigure1.png "GettingStartedFigure1")</span></span>  
  
2. <span data-ttu-id="9cd99-184">Zamknij aplikację, aby powrócić do [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)].</span><span class="sxs-lookup"><span data-stu-id="9cd99-184">Close the application to return to [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)].</span></span> 
  
## <a name="creating-the-layout"></a><span data-ttu-id="9cd99-185">Tworzenie układu</span><span class="sxs-lookup"><span data-stu-id="9cd99-185">Creating the layout</span></span>  
 <span data-ttu-id="9cd99-186">Układ zapewnia uporządkowanej sposób umieść [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] elementów i zarządza także rozmiar i położenie tych elementów podczas [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] rozmiar jest zmieniany.</span><span class="sxs-lookup"><span data-stu-id="9cd99-186">Layout provides an ordered way to place [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] elements, and also manages the size and position of those elements when a [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] is resized.</span></span> <span data-ttu-id="9cd99-187">Jeden z poniższych formantów układu są zwykle Utwórz układ:</span><span class="sxs-lookup"><span data-stu-id="9cd99-187">You typically create a layout with one of the following layout controls:</span></span>  
  
-   <xref:System.Windows.Controls.Canvas>  
  
-   <xref:System.Windows.Controls.DockPanel>  
  
-   <xref:System.Windows.Controls.Grid>  
  
-   <xref:System.Windows.Controls.StackPanel>  
  
-   <xref:System.Windows.Controls.VirtualizingStackPanel>  
  
-   <xref:System.Windows.Controls.WrapPanel>  
  
 <span data-ttu-id="9cd99-188">Każdy z tych kontrolek układu obsługuje specjalny rodzaj układu jego elementów podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="9cd99-188">Each of these layout controls supports a special type of layout for its child elements.</span></span> <span data-ttu-id="9cd99-189">Można zmienić rozmiar strony programu ExpenseIt i każdego strona zawiera elementy, które są rozmieszczone w poziomie i w pionie równolegle z innymi elementami.</span><span class="sxs-lookup"><span data-stu-id="9cd99-189">ExpenseIt pages can be resized, and each page has elements that are arranged horizontally and vertically alongside other elements.</span></span> <span data-ttu-id="9cd99-190">W rezultacie <xref:System.Windows.Controls.Grid> jest elementem układu idealne dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="9cd99-190">Consequently, the <xref:System.Windows.Controls.Grid> is the ideal layout element for the application.</span></span> 
  
> [!NOTE]
>  <span data-ttu-id="9cd99-191">Aby uzyskać więcej informacji na temat <xref:System.Windows.Controls.Panel> elementów, zobacz [omówienie panele](../../../../docs/framework/wpf/controls/panels-overview.md).</span><span class="sxs-lookup"><span data-stu-id="9cd99-191">For more information about <xref:System.Windows.Controls.Panel> elements, see [Panels Overview](../../../../docs/framework/wpf/controls/panels-overview.md).</span></span> <span data-ttu-id="9cd99-192">Aby uzyskać więcej informacji o układzie, zobacz [układu](../../../../docs/framework/wpf/advanced/layout.md).</span><span class="sxs-lookup"><span data-stu-id="9cd99-192">For more information about layout, see [Layout](../../../../docs/framework/wpf/advanced/layout.md).</span></span> 
  
 <span data-ttu-id="9cd99-193">W sekcji tworzenia jednokolumnową tabelę z trzy wiersze i margines 10 pikseli, dodając definicje kolumn i wierszy do <xref:System.Windows.Controls.Grid> w ExpenseItHome.xaml.</span><span class="sxs-lookup"><span data-stu-id="9cd99-193">In the section, you create a single-column table with three rows and a 10-pixel margin by adding column and row definitions to the <xref:System.Windows.Controls.Grid> in ExpenseItHome.xaml.</span></span> 
  
1. <span data-ttu-id="9cd99-194">Otwórz ExpenseItHome.xaml.</span><span class="sxs-lookup"><span data-stu-id="9cd99-194">Open ExpenseItHome.xaml.</span></span> 
  
2. <span data-ttu-id="9cd99-195">Ustaw <xref:System.Windows.FrameworkElement.Margin%2A> właściwość <xref:System.Windows.Controls.Grid> elementu "10,0,10,10", co odpowiada po lewej, górnej, prawej i dolnego marginesu.</span><span class="sxs-lookup"><span data-stu-id="9cd99-195">Set the <xref:System.Windows.FrameworkElement.Margin%2A> property on the <xref:System.Windows.Controls.Grid> element to "10,0,10,10" which corresponds to left, top, right and bottom margins.</span></span> 
  
3. <span data-ttu-id="9cd99-196">Dodaj następujące [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] między <xref:System.Windows.Controls.Grid> tagi do tworzenia definicji wierszy i kolumn.</span><span class="sxs-lookup"><span data-stu-id="9cd99-196">Add the following [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] between the <xref:System.Windows.Controls.Grid> tags to create the row and column definitions.</span></span> 
  
    [!code-xaml[ExpenseIt#8](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt3/ExpenseItHome.xaml#8)]  
  
     <span data-ttu-id="9cd99-197"><xref:System.Windows.Controls.RowDefinition.Height%2A> Dwa wiersze jest ustawiony na wartość <xref:System.Windows.GridLength.Auto%2A> podstawowa co oznacza, że będzie ustalany wiersze w zawartości w wierszach.</span><span class="sxs-lookup"><span data-stu-id="9cd99-197">The <xref:System.Windows.Controls.RowDefinition.Height%2A> of two rows is set to <xref:System.Windows.GridLength.Auto%2A> which means that the rows will be sized base on the content in the rows.</span></span> <span data-ttu-id="9cd99-198">Wartość domyślna <xref:System.Windows.Controls.RowDefinition.Height%2A> jest <xref:System.Windows.GridUnitType.Star> zmiany rozmiaru, co oznacza, że wiersz będzie ważona część dostępnego miejsca.</span><span class="sxs-lookup"><span data-stu-id="9cd99-198">The default <xref:System.Windows.Controls.RowDefinition.Height%2A> is <xref:System.Windows.GridUnitType.Star> sizing, which means that the row will be a weighted proportion of the available space.</span></span> <span data-ttu-id="9cd99-199">Na przykład mieć dwa wiersze wysokość "*", miało wysokości połowy dostępnego miejsca.</span><span class="sxs-lookup"><span data-stu-id="9cd99-199">For example if two rows each have a height of "*", they will each have a height that is half of the available space.</span></span>  
  
     <span data-ttu-id="9cd99-200">Twoje <xref:System.Windows.Controls.Grid> powinna wyglądać tak jak XAML następujące:</span><span class="sxs-lookup"><span data-stu-id="9cd99-200">Your <xref:System.Windows.Controls.Grid> should now look like the following XAML:</span></span>  
  
    [!code-xaml[ExpenseIt#9](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt3/ExpenseItHome.xaml#9)]  
  
## <a name="adding-controls"></a><span data-ttu-id="9cd99-201">Dodawanie formantów</span><span class="sxs-lookup"><span data-stu-id="9cd99-201">Adding controls</span></span>  
 <span data-ttu-id="9cd99-202">W tej sekcji, strony głównej [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] jest aktualizowany, aby wyświetlić listę osób, że użytkownicy mogą wybierać z do wyświetlenia raportu z wydatków dla wybranej osoby.</span><span class="sxs-lookup"><span data-stu-id="9cd99-202">In this section, the home page [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] is updated to show a list of people that users can select from to show the expense report for a selected person.</span></span> <span data-ttu-id="9cd99-203">Formanty są obiektami interfejsu użytkownika, które zezwala użytkownikom na interakcję z aplikacją.</span><span class="sxs-lookup"><span data-stu-id="9cd99-203">Controls are UI objects that allow users to interact with your application.</span></span> <span data-ttu-id="9cd99-204">Aby uzyskać więcej informacji, zobacz [formanty](../../../../docs/framework/wpf/controls/index.md).</span><span class="sxs-lookup"><span data-stu-id="9cd99-204">For more information, see [Controls](../../../../docs/framework/wpf/controls/index.md).</span></span> 
  
 <span data-ttu-id="9cd99-205">Aby utworzyć ten [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], następujące elementy są dodawane do ExpenseItHome.xaml:</span><span class="sxs-lookup"><span data-stu-id="9cd99-205">To create this [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], the following elements are added to ExpenseItHome.xaml:</span></span>  
  
-   <span data-ttu-id="9cd99-206"><xref:System.Windows.Controls.ListBox>(Aby uzyskać listę osób).</span><span class="sxs-lookup"><span data-stu-id="9cd99-206"><xref:System.Windows.Controls.ListBox> (for the list of people).</span></span> 
  
-   <span data-ttu-id="9cd99-207"><xref:System.Windows.Controls.Label>(dla nagłówka listy).</span><span class="sxs-lookup"><span data-stu-id="9cd99-207"><xref:System.Windows.Controls.Label> (for the list header).</span></span> 
  
-   <span data-ttu-id="9cd99-208"><xref:System.Windows.Controls.Button>(aby kliknij, aby wyświetlić raport wydatków dla osoby, która jest zaznaczony na liście).</span><span class="sxs-lookup"><span data-stu-id="9cd99-208"><xref:System.Windows.Controls.Button> (to click to view the expense report for the person that is selected in the list).</span></span> 
  
 <span data-ttu-id="9cd99-209">Każdy formant znajduje się w wierszu <xref:System.Windows.Controls.Grid> przez ustawienie <xref:System.Windows.Controls.Grid.Row%2A?displayProperty=nameWithType> dołączona właściwość.</span><span class="sxs-lookup"><span data-stu-id="9cd99-209">Each control is placed in a row of the <xref:System.Windows.Controls.Grid> by setting the <xref:System.Windows.Controls.Grid.Row%2A?displayProperty=nameWithType> attached property.</span></span> <span data-ttu-id="9cd99-210">Aby uzyskać więcej informacji na temat dołączone właściwości, zobacz [dołączony Przegląd właściwości](../../../../docs/framework/wpf/advanced/attached-properties-overview.md).</span><span class="sxs-lookup"><span data-stu-id="9cd99-210">For more information about attached properties, see [Attached Properties Overview](../../../../docs/framework/wpf/advanced/attached-properties-overview.md).</span></span> 
  
1. <span data-ttu-id="9cd99-211">Otwórz ExpenseItHome.xaml.</span><span class="sxs-lookup"><span data-stu-id="9cd99-211">Open ExpenseItHome.xaml.</span></span> 
  
2. <span data-ttu-id="9cd99-212">Dodaj następujące [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] między <xref:System.Windows.Controls.Grid> tagów.</span><span class="sxs-lookup"><span data-stu-id="9cd99-212">Add the following [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] between the <xref:System.Windows.Controls.Grid> tags.</span></span> 
  
    [!code-xaml[ExpenseIt#10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt4/ExpenseItHome.xaml#10)]  
  
3. <span data-ttu-id="9cd99-213">Skompiluj i uruchom aplikację.</span><span class="sxs-lookup"><span data-stu-id="9cd99-213">Build and run the application.</span></span> 
  
 <span data-ttu-id="9cd99-214">Na poniższej ilustracji przedstawiono formantów, które zostały utworzone przy użyciu języka XAML w tej sekcji.</span><span class="sxs-lookup"><span data-stu-id="9cd99-214">The following illustration shows the controls that are created by the XAML in this section.</span></span> 
  
 <span data-ttu-id="9cd99-215">![Zrzut ekranu przedstawiający przykładowy programu ExpenseIt](../../../../docs/framework/wpf/getting-started/media/gettingstartedfigure2.png "GettingStartedFigure2")</span><span class="sxs-lookup"><span data-stu-id="9cd99-215">![ExpenseIt sample screen shot](../../../../docs/framework/wpf/getting-started/media/gettingstartedfigure2.png "GettingStartedFigure2")</span></span>  
  
## <a name="adding-an-image-and-a-title"></a><span data-ttu-id="9cd99-216">Dodawanie obrazu i tytuł</span><span class="sxs-lookup"><span data-stu-id="9cd99-216">Adding an image and a title</span></span>  
 <span data-ttu-id="9cd99-217">W tej sekcji, strony głównej [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] został zaktualizowany o obrazu i tytuł strony.</span><span class="sxs-lookup"><span data-stu-id="9cd99-217">In this section, the home page [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] is updated with an image and a page title.</span></span> 
  
1. <span data-ttu-id="9cd99-218">Otwórz ExpenseItHome.xaml.</span><span class="sxs-lookup"><span data-stu-id="9cd99-218">Open ExpenseItHome.xaml.</span></span> 
  
2. <span data-ttu-id="9cd99-219">Dodaj inną kolumnę do <xref:System.Windows.Controls.Grid.ColumnDefinitions%2A> ze stałym <xref:System.Windows.Controls.ColumnDefinition.Width%2A> 230 pikseli.</span><span class="sxs-lookup"><span data-stu-id="9cd99-219">Add another column to the <xref:System.Windows.Controls.Grid.ColumnDefinitions%2A> with a fixed <xref:System.Windows.Controls.ColumnDefinition.Width%2A> of 230 pixels.</span></span> 
  
    [!code-xaml[ExpenseIt#11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#11)]  
  
3. <span data-ttu-id="9cd99-220">Dodaj nowy wiersz do <xref:System.Windows.Controls.Grid.RowDefinitions%2A>.</span><span class="sxs-lookup"><span data-stu-id="9cd99-220">Add another row to the <xref:System.Windows.Controls.Grid.RowDefinitions%2A>.</span></span> 
  
    [!code-xaml[ExpenseIt#11b](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#11b)]  
  
4. <span data-ttu-id="9cd99-221">Przenieś formanty do drugiej kolumny przez ustawienie <xref:System.Windows.Controls.Grid.Column%2A?displayProperty=nameWithType> do 1.</span><span class="sxs-lookup"><span data-stu-id="9cd99-221">Move the controls to the second column by setting <xref:System.Windows.Controls.Grid.Column%2A?displayProperty=nameWithType> to 1.</span></span> <span data-ttu-id="9cd99-222">Przesuń kontrolkę każdy wiersz w dół przez odpowiednie zwiększenie <xref:System.Windows.Controls.Grid.Row%2A?displayProperty=nameWithType> o 1.</span><span class="sxs-lookup"><span data-stu-id="9cd99-222">Move each control down a row, by increasing the <xref:System.Windows.Controls.Grid.Row%2A?displayProperty=nameWithType> by 1.</span></span> 
  
    [!code-xaml[ExpenseIt#12](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#12)]  
  
5. <span data-ttu-id="9cd99-223">Ustaw <xref:System.Windows.Controls.Panel.Background%2A> z <xref:System.Windows.Controls.Grid> jako watermark.png pliku obrazu.</span><span class="sxs-lookup"><span data-stu-id="9cd99-223">Set the <xref:System.Windows.Controls.Panel.Background%2A> of the <xref:System.Windows.Controls.Grid> to be the watermark.png image file.</span></span> 
  
    [!code-xaml[ExpenseIt#14](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#14)]  
  
6. <span data-ttu-id="9cd99-224">Przed <xref:System.Windows.Controls.Border>, Dodaj <xref:System.Windows.Controls.Label> z zawartością "Wyświetl raport o wydatkach" jako tytuł strony.</span><span class="sxs-lookup"><span data-stu-id="9cd99-224">Before the <xref:System.Windows.Controls.Border>, add a <xref:System.Windows.Controls.Label> with the content "View Expense Report" to be the title of the page.</span></span> 
  
    [!code-xaml[ExpenseIt#13](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#13)]  
  
7. <span data-ttu-id="9cd99-225">Skompiluj i uruchom aplikację.</span><span class="sxs-lookup"><span data-stu-id="9cd99-225">Build and run the application.</span></span> 
  
 <span data-ttu-id="9cd99-226">Na poniższej ilustracji przedstawiono wyniki w tej sekcji.</span><span class="sxs-lookup"><span data-stu-id="9cd99-226">The following illustration shows the results of this section.</span></span> 
  
 <span data-ttu-id="9cd99-227">![Zrzut ekranu przedstawiający przykładowy programu ExpenseIt](../../../../docs/framework/wpf/getting-started/media/gettingstartedfigure3.png "GettingStartedFigure3")</span><span class="sxs-lookup"><span data-stu-id="9cd99-227">![ExpenseIt sample screen shot](../../../../docs/framework/wpf/getting-started/media/gettingstartedfigure3.png "GettingStartedFigure3")</span></span>  
  
## <a name="adding-code-to-handle-events"></a><span data-ttu-id="9cd99-228">Dodawanie kodu do obsługi zdarzeń</span><span class="sxs-lookup"><span data-stu-id="9cd99-228">Adding code to handle events</span></span>  
  
1. <span data-ttu-id="9cd99-229">Otwórz ExpenseItHome.xaml.</span><span class="sxs-lookup"><span data-stu-id="9cd99-229">Open ExpenseItHome.xaml.</span></span> 
  
2. <span data-ttu-id="9cd99-230">Dodaj <xref:System.Windows.Controls.Primitives.ButtonBase.Click> program obsługi zdarzeń do <xref:System.Windows.Controls.Button> elementu.</span><span class="sxs-lookup"><span data-stu-id="9cd99-230">Add a <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event handler to the <xref:System.Windows.Controls.Button> element.</span></span> <span data-ttu-id="9cd99-231">Aby uzyskać więcej informacji, zobacz [porady: Tworzenie prostego obsługi zdarzeń](http://msdn.microsoft.com/en-us/b1456e07-9dec-4354-99cf-18666b64f480).</span><span class="sxs-lookup"><span data-stu-id="9cd99-231">For more information, see [How to: Create a Simple Event Handler](http://msdn.microsoft.com/en-us/b1456e07-9dec-4354-99cf-18666b64f480).</span></span> 
  
    [!code-xaml[ExpenseIt#15](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt6/ExpenseItHome.xaml#15)]  
  
3. <span data-ttu-id="9cd99-232">Otwórz ExpenseItHome.xaml.vb lub ExpenseItHome.xaml.cs.</span><span class="sxs-lookup"><span data-stu-id="9cd99-232">Open ExpenseItHome.xaml.vb or ExpenseItHome.xaml.cs.</span></span> 
  
4. <span data-ttu-id="9cd99-233">Dodaj następujący kod do <xref:System.Windows.Controls.Primitives.ButtonBase.Click> program obsługi zdarzeń, co powoduje, że okno, aby przejść do pliku ExpenseReportPage.xaml.</span><span class="sxs-lookup"><span data-stu-id="9cd99-233">Add the following code to the <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event handler, which causes the window to navigate to the ExpenseReportPage.xaml file.</span></span> 
  
    [!code-csharp[ExpenseIt#16](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt6/ExpenseItHome.xaml.cs#16)]
    [!code-vb[ExpenseIt#16](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt6/ExpenseItHome.xaml.vb#16)]  
  
## <a name="creating-the-ui-for-expensereportpage"></a><span data-ttu-id="9cd99-234">Tworzenie interfejsu użytkownika dla ExpenseReportPage</span><span class="sxs-lookup"><span data-stu-id="9cd99-234">Creating the UI for ExpenseReportPage</span></span>  
 <span data-ttu-id="9cd99-235">ExpenseReportPage.xaml wyświetla raport wydatków dla osoby, która została wybrana na ExpenseItHome.xaml.</span><span class="sxs-lookup"><span data-stu-id="9cd99-235">ExpenseReportPage.xaml displays the expense report for the person that was selected on the ExpenseItHome.xaml.</span></span> <span data-ttu-id="9cd99-236">W tej sekcji dodaje formantów i tworzy [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] dla ExpenseReportPage.xaml.</span><span class="sxs-lookup"><span data-stu-id="9cd99-236">This section adds controls and creates the [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] for ExpenseReportPage.xaml.</span></span> <span data-ttu-id="9cd99-237">W tej sekcji dodaje również kolory tła i wypełnienia do różnych [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] elementów.</span><span class="sxs-lookup"><span data-stu-id="9cd99-237">This section also adds background and fill colors to the various [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] elements.</span></span> 
  
1. <span data-ttu-id="9cd99-238">Otwórz ExpenseReportPage.xaml.</span><span class="sxs-lookup"><span data-stu-id="9cd99-238">Open ExpenseReportPage.xaml.</span></span> 
  
2. <span data-ttu-id="9cd99-239">Dodaj następujące XAML między <xref:System.Windows.Controls.Grid> tagów.</span><span class="sxs-lookup"><span data-stu-id="9cd99-239">Add the following XAML between the <xref:System.Windows.Controls.Grid> tags.</span></span> 
  
     <span data-ttu-id="9cd99-240">Interfejs ten jest podobny do interfejsu użytkownika utworzone na ExpenseItHome.xaml, z wyjątkiem danych raportu jest wyświetlany w <xref:System.Windows.Controls.DataGrid>.</span><span class="sxs-lookup"><span data-stu-id="9cd99-240">This UI is similar to the UI created on ExpenseItHome.xaml except the report data is displayed in a <xref:System.Windows.Controls.DataGrid>.</span></span> 
  
    [!code-xaml[ExpenseIt#17](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt6/ExpenseReportPage.xaml#17)]  
  
3. <span data-ttu-id="9cd99-241">Skompiluj i uruchom aplikację.</span><span class="sxs-lookup"><span data-stu-id="9cd99-241">Build and run the application.</span></span> 
  
    > [!NOTE]
    >  <span data-ttu-id="9cd99-242">Jeśli występuje błąd <xref:System.Windows.Controls.DataGrid> nie został znaleziony lub nie istnieje, upewnij się, że projekt jest przeznaczony dla programu .NET Framework 4 lub nowszej.</span><span class="sxs-lookup"><span data-stu-id="9cd99-242">If you get an error that the <xref:System.Windows.Controls.DataGrid> was not found or does not exist, make sure that your project targets the .NET Framework 4 or later.</span></span> <span data-ttu-id="9cd99-243">Aby uzyskać więcej informacji, zobacz [porady: wersja docelowa platformy .NET Framework](/visualstudio/ide/how-to-target-a-version-of-the-dotnet-framework).</span><span class="sxs-lookup"><span data-stu-id="9cd99-243">For more information, see [How to: Target a Version of the .NET Framework](/visualstudio/ide/how-to-target-a-version-of-the-dotnet-framework).</span></span> 
  
4. <span data-ttu-id="9cd99-244">Kliknij przycisk **widoku** przycisku.</span><span class="sxs-lookup"><span data-stu-id="9cd99-244">Click the **View** button.</span></span> 
  
     <span data-ttu-id="9cd99-245">Zostanie wyświetlona strona raportu wydatków.</span><span class="sxs-lookup"><span data-stu-id="9cd99-245">The expense report page appears.</span></span> 
  
 <span data-ttu-id="9cd99-246">Na poniższej ilustracji pokazano [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] elementy dodane do ExpenseReportPage.xaml.</span><span class="sxs-lookup"><span data-stu-id="9cd99-246">The following illustration shows the [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] elements added to ExpenseReportPage.xaml.</span></span> <span data-ttu-id="9cd99-247">Zwróć uwagę, że jest włączony przycisk nawigacji Wstecz.</span><span class="sxs-lookup"><span data-stu-id="9cd99-247">Notice that the back navigation button is enabled.</span></span> 
  
 <span data-ttu-id="9cd99-248">![Zrzut ekranu przedstawiający przykładowy programu ExpenseIt](../../../../docs/framework/wpf/getting-started/media/gettingstartedfigure4.png "GettingStartedFigure4")</span><span class="sxs-lookup"><span data-stu-id="9cd99-248">![ExpenseIt sample screen shot](../../../../docs/framework/wpf/getting-started/media/gettingstartedfigure4.png "GettingStartedFigure4")</span></span>  
  
## <a name="styling-controls"></a><span data-ttu-id="9cd99-249">Style formantów</span><span class="sxs-lookup"><span data-stu-id="9cd99-249">Styling controls</span></span>  
 <span data-ttu-id="9cd99-250">Wygląd różnych elementów często może być taka sama dla wszystkich elementów tego samego typu w [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)].</span><span class="sxs-lookup"><span data-stu-id="9cd99-250">The appearance of various elements can often be the same for all elements of the same type in a [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)].</span></span> [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]<span data-ttu-id="9cd99-251">używa style aby wygląd wielokrotnego użytku przez wiele elementów.</span><span class="sxs-lookup"><span data-stu-id="9cd99-251"> uses styles to make appearances reusable across multiple elements.</span></span> <span data-ttu-id="9cd99-252">Możliwość ponownego wykorzystania stylów pozwala uprościć [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] tworzenie i zarządzanie nimi.</span><span class="sxs-lookup"><span data-stu-id="9cd99-252">The reusability of styles helps to simplify [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] creation and management.</span></span> <span data-ttu-id="9cd99-253">Aby uzyskać więcej informacji na temat stylów, zobacz [stylami i tworzenia szablonów](../../../../docs/framework/wpf/controls/styling-and-templating.md).</span><span class="sxs-lookup"><span data-stu-id="9cd99-253">For more information about styles, see [Styling and Templating](../../../../docs/framework/wpf/controls/styling-and-templating.md).</span></span> <span data-ttu-id="9cd99-254">W tej sekcji zastępuje atrybutów na elementów, które zostały zdefiniowane w poprzednich krokach przy użyciu stylów.</span><span class="sxs-lookup"><span data-stu-id="9cd99-254">This section replaces the per-element attributes that were defined in previous steps with styles.</span></span> 
  
1. <span data-ttu-id="9cd99-255">Otwórz Application.xaml lub pliku App.xaml.</span><span class="sxs-lookup"><span data-stu-id="9cd99-255">Open Application.xaml or App.xaml.</span></span> 
  
2. <span data-ttu-id="9cd99-256">Dodaj następujące XAML między <xref:System.Windows.Application.Resources%2A?displayProperty=nameWithType> tagów:</span><span class="sxs-lookup"><span data-stu-id="9cd99-256">Add the following XAML between the <xref:System.Windows.Application.Resources%2A?displayProperty=nameWithType> tags:</span></span>  
  
    [!code-xaml[ExpenseIt#18](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt7/App.xaml#18)]  
  
     <span data-ttu-id="9cd99-257">To [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] dodaje następujące style:</span><span class="sxs-lookup"><span data-stu-id="9cd99-257">This [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] adds the following styles:</span></span>  
  
    -  <span data-ttu-id="9cd99-258">`headerTextStyle`: Aby sformatować tytuł strony <xref:System.Windows.Controls.Label>.</span><span class="sxs-lookup"><span data-stu-id="9cd99-258">`headerTextStyle`: To format the page title <xref:System.Windows.Controls.Label>.</span></span> 
  
    -  <span data-ttu-id="9cd99-259">`labelStyle`: Do formatowania <xref:System.Windows.Controls.Label> kontrolki.</span><span class="sxs-lookup"><span data-stu-id="9cd99-259">`labelStyle`: To format the <xref:System.Windows.Controls.Label> controls.</span></span> 
  
    -  <span data-ttu-id="9cd99-260">`columnHeaderStyle`: Do formatowania <xref:System.Windows.Controls.Primitives.DataGridColumnHeader>.</span><span class="sxs-lookup"><span data-stu-id="9cd99-260">`columnHeaderStyle`: To format the <xref:System.Windows.Controls.Primitives.DataGridColumnHeader>.</span></span> 
  
    -  <span data-ttu-id="9cd99-261">`listHeaderStyle`: Do formatowania nagłówków <xref:System.Windows.Controls.Border> kontrolki.</span><span class="sxs-lookup"><span data-stu-id="9cd99-261">`listHeaderStyle`: To format the list header <xref:System.Windows.Controls.Border> controls.</span></span> 
  
    -  <span data-ttu-id="9cd99-262">`listHeaderTextStyle`: Do formatowania nagłówków <xref:System.Windows.Controls.Label>.</span><span class="sxs-lookup"><span data-stu-id="9cd99-262">`listHeaderTextStyle`: To format the list header <xref:System.Windows.Controls.Label>.</span></span> 
  
    -  <span data-ttu-id="9cd99-263">`buttonStyle`: Do formatowania <xref:System.Windows.Controls.Button> na ExpenseItHome.xaml.</span><span class="sxs-lookup"><span data-stu-id="9cd99-263">`buttonStyle`: To format the <xref:System.Windows.Controls.Button> on ExpenseItHome.xaml.</span></span> 
  
     <span data-ttu-id="9cd99-264">Style są zasobów i elementy podrzędne <xref:System.Windows.Application.Resources%2A?displayProperty=nameWithType> elementu właściwości.</span><span class="sxs-lookup"><span data-stu-id="9cd99-264">Notice that the styles are resources and children of the <xref:System.Windows.Application.Resources%2A?displayProperty=nameWithType> property element.</span></span> <span data-ttu-id="9cd99-265">W tej lokalizacji style są stosowane do wszystkich elementów w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="9cd99-265">In this location, the styles are applied to all the elements in an application.</span></span> <span data-ttu-id="9cd99-266">Przykład użycia zasobów w [!INCLUDE[TLA2#tla_winfx](../../../../includes/tla2sharptla-winfx-md.md)] aplikacji, zobacz [wykorzystania zasobów aplikacji](../../../../docs/framework/wpf/advanced/how-to-use-application-resources.md).</span><span class="sxs-lookup"><span data-stu-id="9cd99-266">For an example of using resources in a [!INCLUDE[TLA2#tla_winfx](../../../../includes/tla2sharptla-winfx-md.md)] application, see [Use Application Resources](../../../../docs/framework/wpf/advanced/how-to-use-application-resources.md).</span></span> 
  
3. <span data-ttu-id="9cd99-267">Otwórz ExpenseItHome.xaml.</span><span class="sxs-lookup"><span data-stu-id="9cd99-267">Open ExpenseItHome.xaml.</span></span> 
  
4. <span data-ttu-id="9cd99-268">Zastąp wszystko pomiędzy <xref:System.Windows.Controls.Grid> elementy o następujących XAML.</span><span class="sxs-lookup"><span data-stu-id="9cd99-268">Replace everything between the <xref:System.Windows.Controls.Grid> elements with the following XAML.</span></span> 
  
    [!code-xaml[ExpenseIt#19](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt7/ExpenseItHome.xaml#19)]  
  
     <span data-ttu-id="9cd99-269">Właściwości, takie jak <xref:System.Windows.VerticalAlignment> i <xref:System.Windows.Media.FontFamily> definiujących wygląd każdej kontrolki usunięty i zastąpiony, stosując style.</span><span class="sxs-lookup"><span data-stu-id="9cd99-269">The properties such as <xref:System.Windows.VerticalAlignment> and <xref:System.Windows.Media.FontFamily> that define the look of each control are removed and replaced by applying the styles.</span></span> <span data-ttu-id="9cd99-270">Na przykład `headerTextStyle` jest stosowany do "Wyświetl raport wydatków" <xref:System.Windows.Controls.Label>.</span><span class="sxs-lookup"><span data-stu-id="9cd99-270">For example, the `headerTextStyle` is applied to the "View Expense Report" <xref:System.Windows.Controls.Label>.</span></span> 
  
5. <span data-ttu-id="9cd99-271">Otwórz ExpenseReportPage.xaml.</span><span class="sxs-lookup"><span data-stu-id="9cd99-271">Open ExpenseReportPage.xaml.</span></span> 
  
6. <span data-ttu-id="9cd99-272">Zastąp wszystko pomiędzy <xref:System.Windows.Controls.Grid> elementy o następujących XAML.</span><span class="sxs-lookup"><span data-stu-id="9cd99-272">Replace everything between the <xref:System.Windows.Controls.Grid> elements with the following XAML.</span></span> 
  
    [!code-xaml[ExpenseIt#20](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt7/ExpenseReportPage.xaml#20)]  
  
     <span data-ttu-id="9cd99-273">Spowoduje to dodanie stylów <xref:System.Windows.Controls.Label> i <xref:System.Windows.Controls.Border> elementy.</span><span class="sxs-lookup"><span data-stu-id="9cd99-273">This adds styles to the <xref:System.Windows.Controls.Label> and <xref:System.Windows.Controls.Border> elements.</span></span> 
  
7. <span data-ttu-id="9cd99-274">Skompiluj i uruchom aplikację.</span><span class="sxs-lookup"><span data-stu-id="9cd99-274">Build and run the application.</span></span> 
  
     <span data-ttu-id="9cd99-275">Po dodaniu [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] w tej sekcji aplikacji wygląda tak samo jak przed aktualizowany przy użyciu stylów.</span><span class="sxs-lookup"><span data-stu-id="9cd99-275">After adding the [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] in this section, the application looks the same as it did before being updated with styles.</span></span> 
  
## <a name="binding-data-to-a-control"></a><span data-ttu-id="9cd99-276">Wiązanie danych do formantu</span><span class="sxs-lookup"><span data-stu-id="9cd99-276">Binding data to a control</span></span>  
 <span data-ttu-id="9cd99-277">W tej sekcji utworzysz [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)] danych, który jest powiązany z różnych formantów.</span><span class="sxs-lookup"><span data-stu-id="9cd99-277">In this section, you create the [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)] data that is bound to various controls.</span></span> 
  
1. <span data-ttu-id="9cd99-278">Otwórz ExpenseItHome.xaml.</span><span class="sxs-lookup"><span data-stu-id="9cd99-278">Open ExpenseItHome.xaml.</span></span> 
  
2. <span data-ttu-id="9cd99-279">Po otwarciu <xref:System.Windows.Controls.Grid> elementu, Dodaj następujący kod XAML, aby utworzyć <xref:System.Windows.Data.XmlDataProvider> dla każdej osoby, która zawiera dane.</span><span class="sxs-lookup"><span data-stu-id="9cd99-279">After the opening <xref:System.Windows.Controls.Grid> element, add the following XAML to create an <xref:System.Windows.Data.XmlDataProvider> that contains the data for each person.</span></span> 
  
     <span data-ttu-id="9cd99-280">Dane są tworzone jako <xref:System.Windows.Controls.Grid> zasobów.</span><span class="sxs-lookup"><span data-stu-id="9cd99-280">The data is created as a <xref:System.Windows.Controls.Grid> resource.</span></span> <span data-ttu-id="9cd99-281">Zwykle będzie to być ładowane jako plik, ale dla uproszczenia dane są dodawane wbudowanego.</span><span class="sxs-lookup"><span data-stu-id="9cd99-281">Normally this would be loaded as a file, but for simplicity the data is added inline.</span></span> 
  
    [!code-xaml[ExpenseIt#21](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml#21)]  
    [!code-xaml[ExpenseIt#23](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml#23)]  
    [!code-xaml[ExpenseIt#22](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml#22)]  
  
3. <span data-ttu-id="9cd99-282">W <xref:System.Windows.Controls.Grid> zasobów, Dodaj następujący <xref:System.Windows.DataTemplate>, który definiuje sposób wyświetlania danych w <xref:System.Windows.Controls.ListBox>.</span><span class="sxs-lookup"><span data-stu-id="9cd99-282">In the <xref:System.Windows.Controls.Grid> resource, add the following <xref:System.Windows.DataTemplate>, which defines how to display the data in the <xref:System.Windows.Controls.ListBox>.</span></span> <span data-ttu-id="9cd99-283">Aby uzyskać więcej informacji na temat szablonów danych, zobacz [omówienie tworzenia szablonów danych](../../../../docs/framework/wpf/data/data-templating-overview.md).</span><span class="sxs-lookup"><span data-stu-id="9cd99-283">For more information about data templates, see [Data Templating Overview](../../../../docs/framework/wpf/data/data-templating-overview.md).</span></span> 
  
    [!code-xaml[ExpenseIt#21](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml#21)]  
    [!code-xaml[ExpenseIt#24](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml#24)]  
    [!code-xaml[ExpenseIt#22](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml#22)]  
  
4. <span data-ttu-id="9cd99-284">Zastąp istniejące <xref:System.Windows.Controls.ListBox> z następujących XAML.</span><span class="sxs-lookup"><span data-stu-id="9cd99-284">Replace the existing <xref:System.Windows.Controls.ListBox> with the following XAML.</span></span> 
  
    [!code-xaml[ExpenseIt#25](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml#25)]  
  
     <span data-ttu-id="9cd99-285">Wiąże się to XAML <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> właściwość <xref:System.Windows.Controls.ListBox> ze źródłem danych i stosuje szablon danych jako <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A>.</span><span class="sxs-lookup"><span data-stu-id="9cd99-285">This XAML binds the <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> property of the <xref:System.Windows.Controls.ListBox> to the data source and applies the data template as the <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A>.</span></span> 
  
## <a name="connecting-data-to-controls"></a><span data-ttu-id="9cd99-286">Łączenie danych z formantami</span><span class="sxs-lookup"><span data-stu-id="9cd99-286">Connecting data to controls</span></span>  
 <span data-ttu-id="9cd99-287">W tej sekcji napisać kod, który pobiera bieżący element jest zaznaczony na liście osób na stronie ExpenseItHome.xaml i przekazuje jego odwołania do konstruktora obiektu `ExpenseReportPage` podczas tworzenia wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="9cd99-287">In this section, you write the code that retrieves the current item that is selected in the list of people on the ExpenseItHome.xaml page, and passes its reference to the constructor of `ExpenseReportPage` during instantiation.</span></span> <span data-ttu-id="9cd99-288">`ExpenseReportPage`Ustawia jego kontekst danych o elemencie przekazany jest formanty zdefiniowanych w ExpenseReportPage.xaml zostanie z nim powiązane.</span><span class="sxs-lookup"><span data-stu-id="9cd99-288">`ExpenseReportPage` sets its data context with the passed item, which is what the controls defined in ExpenseReportPage.xaml will bind to.</span></span> 
  
1. <span data-ttu-id="9cd99-289">Otwórz ExpenseReportPage.xaml.vb lub ExpenseReportPage.xaml.cs.</span><span class="sxs-lookup"><span data-stu-id="9cd99-289">Open ExpenseReportPage.xaml.vb or ExpenseReportPage.xaml.cs.</span></span> 
  
2. <span data-ttu-id="9cd99-290">Dodaj Konstruktor pobierający obiekt, więc można przekazać dane raportu wydatków wybranego użytkownika.</span><span class="sxs-lookup"><span data-stu-id="9cd99-290">Add a constructor that takes an object so you can pass the expense report data of the selected person.</span></span> 
  
    [!code-csharp[ExpenseIt#26](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseReportPage.xaml.cs#26)]
    [!code-vb[ExpenseIt#26](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt8/ExpenseReportPage.xaml.vb#26)]  
  
3. <span data-ttu-id="9cd99-291">Otwórz ExpenseItHome.xaml.vb lub ExpenseItHome.xaml.cs.</span><span class="sxs-lookup"><span data-stu-id="9cd99-291">Open ExpenseItHome.xaml.vb or ExpenseItHome.xaml.cs.</span></span> 
  
4. <span data-ttu-id="9cd99-292">Zmień <xref:System.Windows.Controls.Primitives.ButtonBase.Click> obsługi zdarzeń do wywołania konstruktora new przekazywanie danych raportu wydatków wybrane osoby.</span><span class="sxs-lookup"><span data-stu-id="9cd99-292">Change the <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event handler to call the new constructor passing the expense report data of the selected person.</span></span> 
  
    [!code-csharp[ExpenseIt#27](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml.cs#27)]
    [!code-vb[ExpenseIt#27](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt8/ExpenseItHome.xaml.vb#27)]  
  
## <a name="styling-data-with-data-templates"></a><span data-ttu-id="9cd99-293">Style danych za pomocą szablonów danych</span><span class="sxs-lookup"><span data-stu-id="9cd99-293">Styling data with data templates</span></span>  
 <span data-ttu-id="9cd99-294">W tej sekcji możesz zaktualizować [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] dla każdego elementu w danych powiązane listy przy użyciu szablonów danych.</span><span class="sxs-lookup"><span data-stu-id="9cd99-294">In this section, you update the [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] for each item in the data bound lists by using data templates.</span></span> 
  
1. <span data-ttu-id="9cd99-295">Otwórz ExpenseReportPage.xaml.</span><span class="sxs-lookup"><span data-stu-id="9cd99-295">Open ExpenseReportPage.xaml.</span></span> 
  
2. <span data-ttu-id="9cd99-296">Powiąż z zawartością "Name" i "Dział" <xref:System.Windows.Controls.Label> właściwość źródła elementy do odpowiednich danych.</span><span class="sxs-lookup"><span data-stu-id="9cd99-296">Bind the content of the "Name" and "Department" <xref:System.Windows.Controls.Label> elements to the appropriate data source property.</span></span> <span data-ttu-id="9cd99-297">Aby uzyskać więcej informacji na temat wiązania danych, zobacz [omówienie powiązania danych](../../../../docs/framework/wpf/data/data-binding-overview.md).</span><span class="sxs-lookup"><span data-stu-id="9cd99-297">For more information about data binding, see [Data Binding Overview](../../../../docs/framework/wpf/data/data-binding-overview.md).</span></span> 
  
    [!code-xaml[ExpenseIt#31](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseReportPage.xaml#31)]  
  
3. <span data-ttu-id="9cd99-298">Po otwarciu <xref:System.Windows.Controls.Grid> elementu, Dodaj następujące szablony danych, które określają sposób wyświetlania danych raportu wydatków.</span><span class="sxs-lookup"><span data-stu-id="9cd99-298">After the opening <xref:System.Windows.Controls.Grid> element, add the following data templates, which define how to display the expense report data.</span></span>  
    [!code-xaml[ExpenseIt#30](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseReportPage.xaml#30)]  
  
4. <span data-ttu-id="9cd99-299">Stosować szablony do <xref:System.Windows.Controls.DataGrid> kolumny wyświetlające wydatków danych raportu.</span><span class="sxs-lookup"><span data-stu-id="9cd99-299">Apply the templates to the <xref:System.Windows.Controls.DataGrid> columns that display the expense report data.</span></span> 
  
    [!code-xaml[ExpenseIt#32](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseReportPage.xaml#32)]  
  
5. <span data-ttu-id="9cd99-300">Skompiluj i uruchom aplikację.</span><span class="sxs-lookup"><span data-stu-id="9cd99-300">Build and run the application.</span></span> 
  
6. <span data-ttu-id="9cd99-301">Wybierz osoby, a następnie kliknij przycisk **widoku** przycisku.</span><span class="sxs-lookup"><span data-stu-id="9cd99-301">Select a person and click the **View** button.</span></span> 
  
 <span data-ttu-id="9cd99-302">Na poniższej ilustracji przedstawiono obie strony aplikacji programu ExpenseIt z formantami, układ, style, powiązania danych i zastosować szablony danych.</span><span class="sxs-lookup"><span data-stu-id="9cd99-302">The following illustration shows both pages of the ExpenseIt application with controls, layout, styles, data binding, and data templates applied.</span></span> 
  
 <span data-ttu-id="9cd99-303">![Zrzuty ekranu programu ExpenseIt](../../../../docs/framework/wpf/getting-started/media/gettingstartedfigure5.png "GettingStartedFigure5")</span><span class="sxs-lookup"><span data-stu-id="9cd99-303">![ExpenseIt sample screen shots](../../../../docs/framework/wpf/getting-started/media/gettingstartedfigure5.png "GettingStartedFigure5")</span></span>  
  
## <a name="best-practices"></a><span data-ttu-id="9cd99-304">Najlepsze praktyki</span><span class="sxs-lookup"><span data-stu-id="9cd99-304">Best practices</span></span>  
 <span data-ttu-id="9cd99-305">Ten przykład przedstawia określoną funkcję WPF i w związku z tym, nie jest zgodna z najlepszych rozwiązań tworzenia aplikacji.</span><span class="sxs-lookup"><span data-stu-id="9cd99-305">This sample demonstrates a specific feature of WPF and, consequently, does not follow application development best practices.</span></span> <span data-ttu-id="9cd99-306">Dla kompleksowym omówieniem [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] i [!INCLUDE[TLA2#tla_winfx](../../../../includes/tla2sharptla-winfx-md.md)] najlepszych rozwiązań tworzenia aplikacji, zgodnie z potrzebami, zobacz następujące tematy:</span><span class="sxs-lookup"><span data-stu-id="9cd99-306">For comprehensive coverage of [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] and the [!INCLUDE[TLA2#tla_winfx](../../../../includes/tla2sharptla-winfx-md.md)] application development best practices, see the following topics as appropriate:</span></span>  
  
-   <span data-ttu-id="9cd99-307">Dostępność — [najlepsze praktyki dotyczące ułatwień dostępu](../../../../docs/framework/ui-automation/accessibility-best-practices.md)</span><span class="sxs-lookup"><span data-stu-id="9cd99-307">Accessibility - [Accessibility Best Practices](../../../../docs/framework/ui-automation/accessibility-best-practices.md)</span></span>  
  
-   <span data-ttu-id="9cd99-308">Zabezpieczenia — [zabezpieczeń](../../../../docs/framework/wpf/security-wpf.md)</span><span class="sxs-lookup"><span data-stu-id="9cd99-308">Security - [Security](../../../../docs/framework/wpf/security-wpf.md)</span></span>  
  
-   <span data-ttu-id="9cd99-309">Lokalizacja — [omówienie lokalizacja i globalizacja WPF](../../../../docs/framework/wpf/advanced/wpf-globalization-and-localization-overview.md)</span><span class="sxs-lookup"><span data-stu-id="9cd99-309">Localization - [WPF Globalization and Localization Overview](../../../../docs/framework/wpf/advanced/wpf-globalization-and-localization-overview.md)</span></span>  
  
-   <span data-ttu-id="9cd99-310">Wydajność — [optymalizacji wydajności aplikacji WPF](../../../../docs/framework/wpf/advanced/optimizing-wpf-application-performance.md)</span><span class="sxs-lookup"><span data-stu-id="9cd99-310">Performance - [Optimizing WPF Application Performance](../../../../docs/framework/wpf/advanced/optimizing-wpf-application-performance.md)</span></span>  
  
## <a name="whats-next"></a><span data-ttu-id="9cd99-311">Co to jest dalej</span><span class="sxs-lookup"><span data-stu-id="9cd99-311">What's next</span></span>  
 <span data-ttu-id="9cd99-312">Masz teraz szereg technik dyspozycji użytkownika do tworzenia [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] przy użyciu [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)].</span><span class="sxs-lookup"><span data-stu-id="9cd99-312">You now have a number of techniques at your disposal for creating a [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] using [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)].</span></span> <span data-ttu-id="9cd99-313">Po wykonaniu pełnego zrozumienia podstawowe bloki konstrukcyjne z danymi [!INCLUDE[TLA2#tla_winfx](../../../../includes/tla2sharptla-winfx-md.md)] aplikacji.</span><span class="sxs-lookup"><span data-stu-id="9cd99-313">You should now have a broad understanding of the basic building blocks of a data-bound [!INCLUDE[TLA2#tla_winfx](../../../../includes/tla2sharptla-winfx-md.md)] application.</span></span> <span data-ttu-id="9cd99-314">W tym temacie w żadnym wypadku nie jest wyczerpująca, ale miejmy nadzieję, że użytkownik ma teraz również w pewnym sensie niektóre możliwości, które można wykryć samodzielnie poza technik w tym temacie.</span><span class="sxs-lookup"><span data-stu-id="9cd99-314">This topic is by no means exhaustive, but hopefully you also now have a sense of some of the possibilities you might discover on your own beyond the techniques in this topic.</span></span> 
  
 <span data-ttu-id="9cd99-315">Aby uzyskać więcej informacji o modelach programowanie i architektura WPF zobacz następujące tematy:</span><span class="sxs-lookup"><span data-stu-id="9cd99-315">For more information about the WPF architecture and programming models, see the following topics:</span></span>  
  
-   [<span data-ttu-id="9cd99-316">Architektura WPF</span><span class="sxs-lookup"><span data-stu-id="9cd99-316">WPF Architecture</span></span>](../../../../docs/framework/wpf/advanced/wpf-architecture.md)  
  
-   [<span data-ttu-id="9cd99-317">Omówienie XAML (WPF)</span><span class="sxs-lookup"><span data-stu-id="9cd99-317">XAML Overview (WPF)</span></span>](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)  
  
-   [<span data-ttu-id="9cd99-318">Przegląd właściwości zależności</span><span class="sxs-lookup"><span data-stu-id="9cd99-318">Dependency Properties Overview</span></span>](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)  
  
-   [<span data-ttu-id="9cd99-319">Układ</span><span class="sxs-lookup"><span data-stu-id="9cd99-319">Layout</span></span>](../../../../docs/framework/wpf/advanced/layout.md)  
  
 <span data-ttu-id="9cd99-320">Aby uzyskać więcej informacji o tworzeniu aplikacji zobacz następujące tematy:</span><span class="sxs-lookup"><span data-stu-id="9cd99-320">For more information about creating applications, see the following topics:</span></span>  
  
-   [<span data-ttu-id="9cd99-321">Projektowanie aplikacji</span><span class="sxs-lookup"><span data-stu-id="9cd99-321">Application Development</span></span>](../../../../docs/framework/wpf/app-development/index.md)  
  
-   [<span data-ttu-id="9cd99-322">Formanty</span><span class="sxs-lookup"><span data-stu-id="9cd99-322">Controls</span></span>](../../../../docs/framework/wpf/controls/index.md)  
  
-   [<span data-ttu-id="9cd99-323">Omówienie powiązania danych</span><span class="sxs-lookup"><span data-stu-id="9cd99-323">Data Binding Overview</span></span>](../../../../docs/framework/wpf/data/data-binding-overview.md)  
  
-   [<span data-ttu-id="9cd99-324">Grafika i Multimedia</span><span class="sxs-lookup"><span data-stu-id="9cd99-324">Graphics and Multimedia</span></span>](../../../../docs/framework/wpf/graphics-multimedia/index.md)  
  
-   [<span data-ttu-id="9cd99-325">Dokumentów na platformie WPF</span><span class="sxs-lookup"><span data-stu-id="9cd99-325">Documents in WPF</span></span>](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)  
  
## <a name="see-also"></a><span data-ttu-id="9cd99-326">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9cd99-326">See also</span></span>  
 [<span data-ttu-id="9cd99-327">Omówienie paneli</span><span class="sxs-lookup"><span data-stu-id="9cd99-327">Panels Overview</span></span>](../../../../docs/framework/wpf/controls/panels-overview.md)  
 [<span data-ttu-id="9cd99-328">Omówienie tworzenia szablonów danych</span><span class="sxs-lookup"><span data-stu-id="9cd99-328">Data Templating Overview</span></span>](../../../../docs/framework/wpf/data/data-templating-overview.md)  
 [<span data-ttu-id="9cd99-329">Tworzenie aplikacji WPF</span><span class="sxs-lookup"><span data-stu-id="9cd99-329">Building a WPF Application</span></span>](../../../../docs/framework/wpf/app-development/building-a-wpf-application-wpf.md)  
 [<span data-ttu-id="9cd99-330">Style i szablony</span><span class="sxs-lookup"><span data-stu-id="9cd99-330">Styles and Templates</span></span>](../../../../docs/framework/wpf/controls/styles-and-templates.md)
