---
title: Tworzenie aplikacji WPF w programie Visual Studio
ms.date: 10/26/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- getting started [WPF], WPF
- WPF [WPF], getting started
ms.assetid: b96bed40-8946-4285-8fe4-88045ab854ed
author: mairaw
ms.author: mairaw
ms.custom: vs-dotnet
ms.openlocfilehash: bfbe1bb413e0d9f46fe587d7a412af5303685b7a
ms.sourcegitcommit: 8f95d3a37e591963ebbb9af6e90686fd5f3b8707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2019
ms.locfileid: "56748378"
---
# <a name="walkthrough-my-first-wpf-desktop-application"></a><span data-ttu-id="3d484-102">Przewodnik: Mój pierwszy aplikacji klasycznej WPF</span><span class="sxs-lookup"><span data-stu-id="3d484-102">Walkthrough: My first WPF desktop application</span></span>

<span data-ttu-id="3d484-103">W tym artykule przedstawiono sposób tworzenia prostej aplikacji Windows Presentation Foundation (WPF), który zawiera elementy, które są wspólne dla większości aplikacji WPF: Extensible Application Markup Language (XAML) znaczników, związane z kodem, definicji aplikacji, formanty, układ, powiązanie danych i stylów.</span><span class="sxs-lookup"><span data-stu-id="3d484-103">This article shows you how to develop a simple Windows Presentation Foundation (WPF) application that includes the elements that are common to most WPF applications: Extensible Application Markup Language (XAML) markup, code-behind, application definitions, controls, layout, data binding, and styles.</span></span>

<span data-ttu-id="3d484-104">Ten instruktaż obejmuje następujące kroki:</span><span class="sxs-lookup"><span data-stu-id="3d484-104">This walkthrough includes the following steps:</span></span>

- <span data-ttu-id="3d484-105">Projektowanie wyglądu aplikacji interfejsu użytkownika (UI), należy użyć XAML.</span><span class="sxs-lookup"><span data-stu-id="3d484-105">Use XAML to design the appearance of the application's user interface (UI).</span></span>

- <span data-ttu-id="3d484-106">Pisanie kodu w celu tworzenia zachowaniu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="3d484-106">Write code to build the application's behavior.</span></span>

- <span data-ttu-id="3d484-107">Tworzenie definicji aplikacji do zarządzania aplikacją.</span><span class="sxs-lookup"><span data-stu-id="3d484-107">Create an application definition to manage the application.</span></span>

- <span data-ttu-id="3d484-108">Dodawanie formantów i Utwórz układ do tworzenia interfejsu użytkownika aplikacji.</span><span class="sxs-lookup"><span data-stu-id="3d484-108">Add controls and create the layout to compose the application UI.</span></span>

- <span data-ttu-id="3d484-109">Tworzenie stylów dla spójny wygląd interfejsu użytkownika aplikacji.</span><span class="sxs-lookup"><span data-stu-id="3d484-109">Create styles for a consistent appearance throughout an application's UI.</span></span>

- <span data-ttu-id="3d484-110">Interfejs użytkownika należy powiązać dane, aby wypełnić interfejsu użytkownika z danych, a także zapewnić danych i interfejsu użytkownika synchronizowane.</span><span class="sxs-lookup"><span data-stu-id="3d484-110">Bind the UI to data to both populate the UI from data and keep the data and UI synchronized.</span></span>

<span data-ttu-id="3d484-111">Przed zakończeniem tego przewodnika będziesz wbudowane autonomicznej aplikacji Windows, która pozwala użytkownikom na wyświetlanie raportów wydatków dla wybranych osób.</span><span class="sxs-lookup"><span data-stu-id="3d484-111">By the end of the walkthrough, you'll have built a standalone Windows application that allows users to view expense reports for selected people.</span></span> <span data-ttu-id="3d484-112">Aplikacja składa się z kilku stron WPF, które znajdują się w oknie myszą.</span><span class="sxs-lookup"><span data-stu-id="3d484-112">The application is composed of several WPF pages that are hosted in a browser-style window.</span></span>

> [!TIP]
> <span data-ttu-id="3d484-113">Przykładowy kod, który jest używany do tworzenia tego przewodnika jest dostępna zarówno dla języka Visual Basic i C# w [wprowadzenie do kompilowania aplikacji WPF](https://go.microsoft.com/fwlink/?LinkID=160008).</span><span class="sxs-lookup"><span data-stu-id="3d484-113">The sample code that is used to build this walkthrough is available for both Visual Basic and C# at [Introduction to Building WPF Applications](https://go.microsoft.com/fwlink/?LinkID=160008).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="3d484-114">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="3d484-114">Prerequisites</span></span>

- <span data-ttu-id="3d484-115">Program Visual Studio 2017 lub nowszego</span><span class="sxs-lookup"><span data-stu-id="3d484-115">Visual Studio 2017 or later</span></span>

   <span data-ttu-id="3d484-116">Aby uzyskać więcej informacji na temat instalowania najnowszej wersji programu Visual Studio, zobacz [Zainstaluj program Visual Studio](/visualstudio/install/install-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="3d484-116">For more information about installing the latest version of Visual Studio, see [Install Visual Studio](/visualstudio/install/install-visual-studio).</span></span>

## <a name="create-the-application-project"></a><span data-ttu-id="3d484-117">Utwórz projekt aplikacji</span><span class="sxs-lookup"><span data-stu-id="3d484-117">Create the application project</span></span>

<span data-ttu-id="3d484-118">Pierwszym krokiem jest do utworzenia infrastruktury aplikacji, który zawiera definicję aplikacji, dwie strony i obraz.</span><span class="sxs-lookup"><span data-stu-id="3d484-118">The first step is to create the application infrastructure, which includes an application definition, two pages, and an image.</span></span>

1. <span data-ttu-id="3d484-119">Utwórz nowy projekt aplikacji WPF w języku Visual Basic lub Visual C# o nazwie **`ExpenseIt`**:</span><span class="sxs-lookup"><span data-stu-id="3d484-119">Create a new WPF Application project in Visual Basic or Visual C# named **`ExpenseIt`**:</span></span>

   1. <span data-ttu-id="3d484-120">Otwórz program Visual Studio i wybierz **pliku** > **New** > **projektu**.</span><span class="sxs-lookup"><span data-stu-id="3d484-120">Open Visual Studio and select **File** > **New** > **Project**.</span></span>

      <span data-ttu-id="3d484-121">**Nowy projekt** zostanie otwarte okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="3d484-121">The **New Project** dialog opens.</span></span>

   2. <span data-ttu-id="3d484-122">W obszarze **zainstalowane** kategorii, rozwiń węzeł **Visual C#**  lub **języka Visual Basic** węzeł, a następnie wybierz **pulpitu Windows**.</span><span class="sxs-lookup"><span data-stu-id="3d484-122">Under the **Installed** category, expand either the **Visual C#** or **Visual Basic** node, and then select **Windows Desktop**.</span></span>

   3. <span data-ttu-id="3d484-123">Wybierz **aplikacja WPF (.NET Framework)** szablonu.</span><span class="sxs-lookup"><span data-stu-id="3d484-123">Select the **WPF App (.NET Framework)** template.</span></span> <span data-ttu-id="3d484-124">Wprowadź nazwę **`ExpenseIt`** , a następnie wybierz **OK**.</span><span class="sxs-lookup"><span data-stu-id="3d484-124">Enter the name **`ExpenseIt`** and then select **OK**.</span></span>

      ![Okno dialogowe nowego projektu za pomocą wybrano aplikacji WPF](media/new-project-dialog.png)

      <span data-ttu-id="3d484-126">Visual Studio tworzy projekt i zostanie otwarty projektant domyślny okna aplikacji o nazwie **MainWindow.xaml**.</span><span class="sxs-lookup"><span data-stu-id="3d484-126">Visual Studio creates the project and opens the designer for the default application window named **MainWindow.xaml**.</span></span>

   > [!NOTE]
   > <span data-ttu-id="3d484-127">W tym instruktażu wykorzystano <xref:System.Windows.Controls.DataGrid> formant, który jest dostępny w programie .NET Framework 4 i nowszych wersjach.</span><span class="sxs-lookup"><span data-stu-id="3d484-127">This walkthrough uses the <xref:System.Windows.Controls.DataGrid> control that is available in the .NET Framework 4 and later.</span></span> <span data-ttu-id="3d484-128">Należy się upewnić, że projekt jest ukierunkowany na .NET Framework 4 lub nowszej.</span><span class="sxs-lookup"><span data-stu-id="3d484-128">Be sure that your project targets the .NET Framework 4 or later.</span></span> <span data-ttu-id="3d484-129">Aby uzyskać więcej informacji, zobacz [jak: Docelowa wersja systemu .NET Framework](/visualstudio/ide/how-to-target-a-version-of-the-dotnet-framework).</span><span class="sxs-lookup"><span data-stu-id="3d484-129">For more information, see [How to: Target a Version of the .NET Framework](/visualstudio/ide/how-to-target-a-version-of-the-dotnet-framework).</span></span>

2. <span data-ttu-id="3d484-130">Otwórz *Application.xaml* (Visual Basic) lub *App.xaml* (C#).</span><span class="sxs-lookup"><span data-stu-id="3d484-130">Open *Application.xaml* (Visual Basic) or *App.xaml* (C#).</span></span>

    <span data-ttu-id="3d484-131">Ten plik XAML definiuje aplikacji WPF i wszystkich zasobów aplikacji.</span><span class="sxs-lookup"><span data-stu-id="3d484-131">This XAML file defines a WPF application and any application resources.</span></span> <span data-ttu-id="3d484-132">Ten plik również użyć do określenia interfejs użytkownika, który jest automatycznie wyświetlana podczas uruchamiania aplikacji; w tym przypadku *MainWindow.xaml*.</span><span class="sxs-lookup"><span data-stu-id="3d484-132">You also use this file to specify the UI that automatically shows when the application starts; in this case, *MainWindow.xaml*.</span></span>

    <span data-ttu-id="3d484-133">Usługi XAML powinien wyglądać następująco w języku Visual Basic:</span><span class="sxs-lookup"><span data-stu-id="3d484-133">Your XAML should look like this in Visual Basic:</span></span>

    [!code-xaml[ExpenseIt#1_A](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/Application.xaml#1_a)]

    <span data-ttu-id="3d484-134">Lub tak jak poniżej w języku C#:</span><span class="sxs-lookup"><span data-stu-id="3d484-134">Or like this in C#:</span></span>

    [!code-xaml[ExpenseIt#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/App.xaml#1)]

3. <span data-ttu-id="3d484-135">Otwórz *MainWindow.xaml*.</span><span class="sxs-lookup"><span data-stu-id="3d484-135">Open *MainWindow.xaml*.</span></span>

    <span data-ttu-id="3d484-136">Ten plik XAML okno główne aplikacji i wyświetla zawartość utworzona na stronach.</span><span class="sxs-lookup"><span data-stu-id="3d484-136">This XAML file is the main window of your application and displays content created in pages.</span></span> <span data-ttu-id="3d484-137"><xref:System.Windows.Window> Klasy definiuje właściwości okna, takie jak jego tytuł, rozmiar lub ikonę i obsługuje zdarzenia, takie jak zamknąć lub ukrywanie.</span><span class="sxs-lookup"><span data-stu-id="3d484-137">The <xref:System.Windows.Window> class defines the properties of a window, such as its title, size, or icon, and handles events, such as closing or hiding.</span></span>

4. <span data-ttu-id="3d484-138">Zmiana <xref:System.Windows.Window> elementu <xref:System.Windows.Navigation.NavigationWindow>, jak pokazano na poniższym XAML:</span><span class="sxs-lookup"><span data-stu-id="3d484-138">Change the <xref:System.Windows.Window> element to a <xref:System.Windows.Navigation.NavigationWindow>, as shown in the following XAML:</span></span>

   ```xaml
   <NavigationWindow x:Class="ExpenseIt.MainWindow"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        ...
   </NavigationWindow>
   ```

   <span data-ttu-id="3d484-139">Ta aplikacja powoduje przejście do innej zawartości, w zależności od danych wejściowych użytkownika.</span><span class="sxs-lookup"><span data-stu-id="3d484-139">This app navigates to different content depending on the user input.</span></span> <span data-ttu-id="3d484-140">Dlatego głównym <xref:System.Windows.Window> musi zostać zmienione w celu <xref:System.Windows.Navigation.NavigationWindow>.</span><span class="sxs-lookup"><span data-stu-id="3d484-140">This is why the main <xref:System.Windows.Window> needs to be changed to a <xref:System.Windows.Navigation.NavigationWindow>.</span></span> <span data-ttu-id="3d484-141"><xref:System.Windows.Navigation.NavigationWindow> dziedziczy wszystkie właściwości <xref:System.Windows.Window>.</span><span class="sxs-lookup"><span data-stu-id="3d484-141"><xref:System.Windows.Navigation.NavigationWindow> inherits all the properties of <xref:System.Windows.Window>.</span></span> <span data-ttu-id="3d484-142"><xref:System.Windows.Navigation.NavigationWindow> Elementu w pliku XAML tworzy wystąpienie <xref:System.Windows.Navigation.NavigationWindow> klasy.</span><span class="sxs-lookup"><span data-stu-id="3d484-142">The <xref:System.Windows.Navigation.NavigationWindow> element in the XAML file creates an instance of the <xref:System.Windows.Navigation.NavigationWindow> class.</span></span> <span data-ttu-id="3d484-143">Aby uzyskać więcej informacji, zobacz [Nawigacja — omówienie](../../../../docs/framework/wpf/app-development/navigation-overview.md).</span><span class="sxs-lookup"><span data-stu-id="3d484-143">For more information, see [Navigation overview](../../../../docs/framework/wpf/app-development/navigation-overview.md).</span></span>

5. <span data-ttu-id="3d484-144">Zmień następujące właściwości na <xref:System.Windows.Navigation.NavigationWindow> elementu:</span><span class="sxs-lookup"><span data-stu-id="3d484-144">Change the following properties on the <xref:System.Windows.Navigation.NavigationWindow> element:</span></span>

    - <span data-ttu-id="3d484-145">Ustaw <xref:System.Windows.Window.Title%2A> właściwość "`ExpenseIt`".</span><span class="sxs-lookup"><span data-stu-id="3d484-145">Set the <xref:System.Windows.Window.Title%2A> property to "`ExpenseIt`".</span></span>

    - <span data-ttu-id="3d484-146">Ustaw <xref:System.Windows.FrameworkElement.Width%2A> właściwości na 500 pikseli.</span><span class="sxs-lookup"><span data-stu-id="3d484-146">Set the <xref:System.Windows.FrameworkElement.Width%2A> property to 500 pixels.</span></span>

    - <span data-ttu-id="3d484-147">Ustaw <xref:System.Windows.FrameworkElement.Height%2A> właściwość 350 pikseli.</span><span class="sxs-lookup"><span data-stu-id="3d484-147">Set the <xref:System.Windows.FrameworkElement.Height%2A> property to 350 pixels.</span></span>

    - <span data-ttu-id="3d484-148">Usuń <xref:System.Windows.Controls.Grid> elementy między <xref:System.Windows.Navigation.NavigationWindow> tagów.</span><span class="sxs-lookup"><span data-stu-id="3d484-148">Remove the <xref:System.Windows.Controls.Grid> elements between the <xref:System.Windows.Navigation.NavigationWindow> tags.</span></span>

    <span data-ttu-id="3d484-149">Usługi XAML powinien wyglądać następująco w języku Visual Basic:</span><span class="sxs-lookup"><span data-stu-id="3d484-149">Your XAML should look like this in Visual Basic:</span></span>

    [!code-xaml[ExpenseIt#2_A](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt/MainWindow.xaml#2_a)]

    <span data-ttu-id="3d484-150">Lub tak jak poniżej w języku C#:</span><span class="sxs-lookup"><span data-stu-id="3d484-150">Or like this in C#:</span></span>

    [!code-xaml[ExpenseIt#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/MainWindow.xaml#2)]

6. <span data-ttu-id="3d484-151">Otwórz *MainWindow.xaml.vb* lub *MainWindow.xaml.cs*.</span><span class="sxs-lookup"><span data-stu-id="3d484-151">Open *MainWindow.xaml.vb* or *MainWindow.xaml.cs*.</span></span>

    <span data-ttu-id="3d484-152">Ten plik jest plik związany z kodem, który zawiera kod służący do obsługi zdarzeń zadeklarowanych w *MainWindow.xaml*.</span><span class="sxs-lookup"><span data-stu-id="3d484-152">This file is a code-behind file that contains code to handle the events declared in *MainWindow.xaml*.</span></span> <span data-ttu-id="3d484-153">Ten plik zawiera klasę częściową dla okna zdefiniowane w XAML.</span><span class="sxs-lookup"><span data-stu-id="3d484-153">This file contains a partial class for the window defined in XAML.</span></span>

7. <span data-ttu-id="3d484-154">Jeśli używasz języka C#, zmień `MainWindow` pochodzi od klasy <xref:System.Windows.Navigation.NavigationWindow>.</span><span class="sxs-lookup"><span data-stu-id="3d484-154">If you are using C#, change the `MainWindow` class to derive from <xref:System.Windows.Navigation.NavigationWindow>.</span></span> <span data-ttu-id="3d484-155">(W języku Visual Basic to wykonywane automatycznie po zmianie okna XAML).</span><span class="sxs-lookup"><span data-stu-id="3d484-155">(In Visual Basic, this happens automatically when you change the window in XAML.)</span></span>

   <span data-ttu-id="3d484-156">Kod powinien wyglądać następująco:</span><span class="sxs-lookup"><span data-stu-id="3d484-156">Your code should look like this:</span></span>

   [!code-csharp[ExpenseIt#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/MainWindow.xaml.cs#3)]
   [!code-vb[ExpenseIt#3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/MainWindow.xaml.vb#3)]

   > [!TIP]
   > <span data-ttu-id="3d484-157">Można przełączać język kodu przykładowego kodu między C# i Visual Basic w **języka** listy rozwijanej w prawej górnej części tego artykułu.</span><span class="sxs-lookup"><span data-stu-id="3d484-157">You can toggle the code language of the sample code between C# and Visual Basic in the **Language** drop-down on the upper right side of this article.</span></span>

## <a name="add-files-to-the-application"></a><span data-ttu-id="3d484-158">Dodaj pliki do aplikacji</span><span class="sxs-lookup"><span data-stu-id="3d484-158">Add files to the application</span></span>

<span data-ttu-id="3d484-159">W tej sekcji należy dodać dwie strony i obrazu do aplikacji.</span><span class="sxs-lookup"><span data-stu-id="3d484-159">In this section, you'll add two pages and an image to the application.</span></span>

1. <span data-ttu-id="3d484-160">Dodaj nową stronę WPF do projektu i nadaj mu nazwę *`ExpenseItHome.xaml`*:</span><span class="sxs-lookup"><span data-stu-id="3d484-160">Add a new WPF page to the project, and name it *`ExpenseItHome.xaml`*:</span></span>

   1. <span data-ttu-id="3d484-161">W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **`ExpenseIt`** węzeł projektu i wybierz polecenie **Dodaj** > **strony**.</span><span class="sxs-lookup"><span data-stu-id="3d484-161">In **Solution Explorer**, right-click on the **`ExpenseIt`** project node and choose **Add** > **Page**.</span></span>

   1. <span data-ttu-id="3d484-162">W **Dodaj nowy element** okno dialogowe, **strony (WPF)** już zaznaczony jest szablon.</span><span class="sxs-lookup"><span data-stu-id="3d484-162">In the **Add New Item** dialog, the **Page (WPF)** template is already selected.</span></span> <span data-ttu-id="3d484-163">Wprowadź nazwę **`ExpenseItHome`**, a następnie wybierz pozycję **Dodaj**.</span><span class="sxs-lookup"><span data-stu-id="3d484-163">Enter the name **`ExpenseItHome`**, and then select **Add**.</span></span>

    <span data-ttu-id="3d484-164">Ta strona jest pierwsza strona, która jest wyświetlana, gdy aplikacja zostanie uruchomiona.</span><span class="sxs-lookup"><span data-stu-id="3d484-164">This page is the first page that's displayed when the application is launched.</span></span> <span data-ttu-id="3d484-165">Widoczna będzie lista osób, które można wybierać, aby wyświetlić raport wydatków dla.</span><span class="sxs-lookup"><span data-stu-id="3d484-165">It will show a list of people to select from, to show an expense report for.</span></span>

2. <span data-ttu-id="3d484-166">Otwórz *`ExpenseItHome.xaml`*.</span><span class="sxs-lookup"><span data-stu-id="3d484-166">Open *`ExpenseItHome.xaml`*.</span></span>

3. <span data-ttu-id="3d484-167">Ustaw <xref:System.Windows.Controls.Page.Title%2A> do "`ExpenseIt - Home`".</span><span class="sxs-lookup"><span data-stu-id="3d484-167">Set the <xref:System.Windows.Controls.Page.Title%2A> to "`ExpenseIt - Home`".</span></span>

    <span data-ttu-id="3d484-168">Usługi XAML powinien wyglądać następująco w języku Visual Basic:</span><span class="sxs-lookup"><span data-stu-id="3d484-168">Your XAML should look like this in Visual Basic:</span></span>

    [!code-xaml[ExpenseIt#6_A](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseItHome.xaml#6_a)]

    <span data-ttu-id="3d484-169">Bądź w języku C#:</span><span class="sxs-lookup"><span data-stu-id="3d484-169">Or this in C#:</span></span>

    [!code-xaml[ExpenseIt#6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt2/ExpenseItHome.xaml#6)]

4. <span data-ttu-id="3d484-170">Otwórz *MainWindow.xaml*.</span><span class="sxs-lookup"><span data-stu-id="3d484-170">Open *MainWindow.xaml*.</span></span>

5. <span data-ttu-id="3d484-171">Ustaw <xref:System.Windows.Navigation.NavigationWindow.Source%2A> właściwość <xref:System.Windows.Navigation.NavigationWindow> do "`ExpenseItHome.xaml`".</span><span class="sxs-lookup"><span data-stu-id="3d484-171">Set the <xref:System.Windows.Navigation.NavigationWindow.Source%2A> property on the <xref:System.Windows.Navigation.NavigationWindow> to "`ExpenseItHome.xaml`".</span></span>

    <span data-ttu-id="3d484-172">To ustawienie *`ExpenseItHome.xaml`* jako pierwsza strona otwarty podczas uruchamiania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="3d484-172">This sets *`ExpenseItHome.xaml`* to be the first page opened when the application starts.</span></span> <span data-ttu-id="3d484-173">Usługi XAML powinien wyglądać następująco w języku Visual Basic:</span><span class="sxs-lookup"><span data-stu-id="3d484-173">Your XAML should look like this in Visual Basic:</span></span>

    [!code-xaml[ExpenseIt#7_A](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/MainWindow.xaml#7_a)]

    <span data-ttu-id="3d484-174">Bądź w języku C#:</span><span class="sxs-lookup"><span data-stu-id="3d484-174">Or this in C#:</span></span>

    [!code-xaml[ExpenseIt#7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt2/MainWindow.xaml#7)]

   > [!TIP]
   > <span data-ttu-id="3d484-175">Można również ustawić **źródła** właściwość **różne** kategorii **właściwości** okna.</span><span class="sxs-lookup"><span data-stu-id="3d484-175">You can also set the **Source** property in the **Miscellaneous** category of the **Properties** window.</span></span>
   >
   > ![Source — właściwość w oknie właściwości](media/properties-source.png)

6. <span data-ttu-id="3d484-177">Dodaj inną nową stronę WPF do projektu i nadaj mu nazwę *ExpenseReportPage.xaml*::</span><span class="sxs-lookup"><span data-stu-id="3d484-177">Add another new WPF page to the project, and name it *ExpenseReportPage.xaml*::</span></span>

   1. <span data-ttu-id="3d484-178">W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **`ExpenseIt`** węzeł projektu i wybierz polecenie **Dodaj** > **strony**.</span><span class="sxs-lookup"><span data-stu-id="3d484-178">In **Solution Explorer**, right-click on the **`ExpenseIt`** project node and choose **Add** > **Page**.</span></span>

   1. <span data-ttu-id="3d484-179">W **Dodaj nowy element** okno dialogowe, **strony (WPF)** już zaznaczony jest szablon.</span><span class="sxs-lookup"><span data-stu-id="3d484-179">In the **Add New Item** dialog, the **Page (WPF)** template is already selected.</span></span> <span data-ttu-id="3d484-180">Wprowadź nazwę **ExpenseReportPage**, a następnie wybierz pozycję **Dodaj**.</span><span class="sxs-lookup"><span data-stu-id="3d484-180">Enter the name **ExpenseReportPage**, and then select **Add**.</span></span>

    <span data-ttu-id="3d484-181">Tej strony wyświetli raportu wydatków dla osób, które wybrano na **`ExpenseItHome`** strony.</span><span class="sxs-lookup"><span data-stu-id="3d484-181">This page will show the expense report for the person that is selected on the **`ExpenseItHome`** page.</span></span>

7. <span data-ttu-id="3d484-182">Otwórz *ExpenseReportPage.xaml*.</span><span class="sxs-lookup"><span data-stu-id="3d484-182">Open *ExpenseReportPage.xaml*.</span></span>

8. <span data-ttu-id="3d484-183">Ustaw <xref:System.Windows.Controls.Page.Title%2A> do "`ExpenseIt - View Expense`".</span><span class="sxs-lookup"><span data-stu-id="3d484-183">Set the <xref:System.Windows.Controls.Page.Title%2A> to "`ExpenseIt - View Expense`".</span></span>

    <span data-ttu-id="3d484-184">Usługi XAML powinien wyglądać następująco w języku Visual Basic:</span><span class="sxs-lookup"><span data-stu-id="3d484-184">Your XAML should look like this in Visual Basic:</span></span>

    [!code-xaml[ExpenseIt#4_A](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseReportPage.xaml#4_a)]

    <span data-ttu-id="3d484-185">Bądź w języku C#:</span><span class="sxs-lookup"><span data-stu-id="3d484-185">Or this in C#:</span></span>

    [!code-xaml[ExpenseIt#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/ExpenseReportPage.xaml#4)]

9. <span data-ttu-id="3d484-186">Otwórz *ExpenseItHome.xaml.vb* i *ExpenseReportPage.xaml.vb*, lub *ExpenseItHome.xaml.cs* i *ExpenseReportPage.xaml.cs*.</span><span class="sxs-lookup"><span data-stu-id="3d484-186">Open *ExpenseItHome.xaml.vb* and *ExpenseReportPage.xaml.vb*, or *ExpenseItHome.xaml.cs* and *ExpenseReportPage.xaml.cs*.</span></span>

    <span data-ttu-id="3d484-187">Podczas tworzenia nowego pliku strony Visual Studio automatycznie tworzy *związanym z kodem* pliku.</span><span class="sxs-lookup"><span data-stu-id="3d484-187">When you create a new Page file, Visual Studio automatically creates a *code-behind* file.</span></span> <span data-ttu-id="3d484-188">Te pliki związane z kodem obsługi logiki w odpowiedzi na dane wejściowe użytkownika.</span><span class="sxs-lookup"><span data-stu-id="3d484-188">These code-behind files handle the logic for responding to user input.</span></span>

    <span data-ttu-id="3d484-189">Kod powinien wyglądać następująco dla **`ExpenseItHome`**:</span><span class="sxs-lookup"><span data-stu-id="3d484-189">Your code should look like this for **`ExpenseItHome`**:</span></span>

    [!code-csharp[ExpenseIt#2_5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt2/ExpenseItHome.xaml.cs#2_5)]
    [!code-vb[ExpenseIt#2_5](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseItHome.xaml.vb#2_5)]

    <span data-ttu-id="3d484-190">I tak dla **ExpenseReportPage**:</span><span class="sxs-lookup"><span data-stu-id="3d484-190">And like this for **ExpenseReportPage**:</span></span>

    [!code-csharp[ExpenseIt#5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/ExpenseReportPage.xaml.cs#5)]
    [!code-vb[ExpenseIt#5](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseReportPage.xaml.vb#5)]

10. <span data-ttu-id="3d484-191">Dodawanie obrazu o nazwie *watermark.png* do projektu.</span><span class="sxs-lookup"><span data-stu-id="3d484-191">Add an image named *watermark.png* to the project.</span></span> <span data-ttu-id="3d484-192">Tworzenie własnego obrazu, skopiuj plik z przykładowego kodu lub jego [tutaj](https://github.com/dotnet/docs/blob/master/docs/framework/wpf/getting-started/media/watermark.png).</span><span class="sxs-lookup"><span data-stu-id="3d484-192">You can create your own image, copy the file from the sample code, or get it [here](https://github.com/dotnet/docs/blob/master/docs/framework/wpf/getting-started/media/watermark.png).</span></span>

   1. <span data-ttu-id="3d484-193">Kliknij prawym przyciskiem myszy węzeł projektu i wybierz **Dodaj** > **istniejący element**, lub naciśnij **Shift**+**Alt** + **A**.</span><span class="sxs-lookup"><span data-stu-id="3d484-193">Right-click on the project node and select **Add** > **Existing Item**, or press **Shift**+**Alt**+**A**.</span></span>

   2. <span data-ttu-id="3d484-194">W **Dodaj istniejący element** okno dialogowe, przejdź do pliku obrazu, który chcesz użyć, a następnie wybierz **Dodaj**.</span><span class="sxs-lookup"><span data-stu-id="3d484-194">In the **Add Existing Item** dialog, browse to the image file you want to use, and then select **Add**.</span></span>

## <a name="build-and-run-the-application"></a><span data-ttu-id="3d484-195">Kompilowanie i uruchamianie aplikacji</span><span class="sxs-lookup"><span data-stu-id="3d484-195">Build and run the application</span></span>

1. <span data-ttu-id="3d484-196">Aby skompilować i uruchomić aplikację, naciśnij klawisz **F5** lub wybierz **Rozpocznij debugowanie** z **debugowania** menu.</span><span class="sxs-lookup"><span data-stu-id="3d484-196">To build and run the application, press **F5** or select **Start Debugging** from the **Debug** menu.</span></span>

    <span data-ttu-id="3d484-197">Na poniższej ilustracji przedstawiono aplikację za pomocą <xref:System.Windows.Navigation.NavigationWindow> przyciski:</span><span class="sxs-lookup"><span data-stu-id="3d484-197">The following illustration shows the application with the <xref:System.Windows.Navigation.NavigationWindow> buttons:</span></span>

    ![Zrzut ekranu przedstawiający programu ExpenseIt](../../../../docs/framework/wpf/getting-started/media/gettingstartedfigure1.png)

2. <span data-ttu-id="3d484-199">Zamknij aplikację, aby powrócić do programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="3d484-199">Close the application to return to Visual Studio.</span></span>

## <a name="create-the-layout"></a><span data-ttu-id="3d484-200">Utwórz układ</span><span class="sxs-lookup"><span data-stu-id="3d484-200">Create the layout</span></span>

<span data-ttu-id="3d484-201">Układ zapewnia uporządkowany sposób umieszczania elementów interfejsu użytkownika i zarządza także rozmiar i położenie tych elementów przy zmianie rozmiaru interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="3d484-201">Layout provides an ordered way to place UI elements, and also manages the size and position of those elements when a UI is resized.</span></span> <span data-ttu-id="3d484-202">Układ jest zwykle tworzysz przy użyciu jednego z następujących formantów układu:</span><span class="sxs-lookup"><span data-stu-id="3d484-202">You typically create a layout with one of the following layout controls:</span></span>

- <xref:System.Windows.Controls.Canvas>
- <xref:System.Windows.Controls.DockPanel>
- <xref:System.Windows.Controls.Grid>
- <xref:System.Windows.Controls.StackPanel>
- <xref:System.Windows.Controls.VirtualizingStackPanel>
- <xref:System.Windows.Controls.WrapPanel>

<span data-ttu-id="3d484-203">Każda z tych kontrolek układ obsługuje specjalny rodzaj układu dla jego elementów podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="3d484-203">Each of these layout controls supports a special type of layout for its child elements.</span></span> <span data-ttu-id="3d484-204">`ExpenseIt` można zmienić rozmiar strony, a każda strona ma elementy, które są ułożone poziomo i pionowo wraz z innymi elementami.</span><span class="sxs-lookup"><span data-stu-id="3d484-204">`ExpenseIt` pages can be resized, and each page has elements that are arranged horizontally and vertically alongside other elements.</span></span> <span data-ttu-id="3d484-205">W związku z tym <xref:System.Windows.Controls.Grid> jest elementem układu idealne dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="3d484-205">Consequently, the <xref:System.Windows.Controls.Grid> is the ideal layout element for the application.</span></span>

> [!TIP]
> <span data-ttu-id="3d484-206">Aby uzyskać więcej informacji na temat <xref:System.Windows.Controls.Panel> elementów, zobacz [Przegląd panele](../../../../docs/framework/wpf/controls/panels-overview.md).</span><span class="sxs-lookup"><span data-stu-id="3d484-206">For more information about <xref:System.Windows.Controls.Panel> elements, see [Panels overview](../../../../docs/framework/wpf/controls/panels-overview.md).</span></span> <span data-ttu-id="3d484-207">Aby uzyskać więcej informacji na temat układu, zobacz [układ](../../../../docs/framework/wpf/advanced/layout.md).</span><span class="sxs-lookup"><span data-stu-id="3d484-207">For more information about layout, see [Layout](../../../../docs/framework/wpf/advanced/layout.md).</span></span>

<span data-ttu-id="3d484-208">W sekcji utworzysz tabelą z jedną kolumną z trzema wierszami i margines 10 pikseli, dodając definicje kolumn i wierszy <xref:System.Windows.Controls.Grid> w *`ExpenseItHome.xaml`*.</span><span class="sxs-lookup"><span data-stu-id="3d484-208">In the section, you create a single-column table with three rows and a 10-pixel margin by adding column and row definitions to the <xref:System.Windows.Controls.Grid> in *`ExpenseItHome.xaml`*.</span></span>

1. <span data-ttu-id="3d484-209">Otwórz *`ExpenseItHome.xaml`*.</span><span class="sxs-lookup"><span data-stu-id="3d484-209">Open *`ExpenseItHome.xaml`*.</span></span>

2. <span data-ttu-id="3d484-210">Ustaw <xref:System.Windows.FrameworkElement.Margin%2A> właściwość <xref:System.Windows.Controls.Grid> elementu "10,0,10,10", która odnosi się do lewej, górnej, prawej strony i dolnego marginesu:</span><span class="sxs-lookup"><span data-stu-id="3d484-210">Set the <xref:System.Windows.FrameworkElement.Margin%2A> property on the <xref:System.Windows.Controls.Grid> element to "10,0,10,10", which corresponds to left, top, right and bottom margins:</span></span>

   ```xaml
   <Grid Margin="10,0,10,10">
   ```

   > [!TIP]
   > <span data-ttu-id="3d484-211">Można również ustawić **margines** wartości w **właściwości** okna, w obszarze **układ** kategorii:</span><span class="sxs-lookup"><span data-stu-id="3d484-211">You can also set the **Margin** values in the **Properties** window, under the **Layout** category:</span></span>
   >
   > ![Wartości marginesów w oknie właściwości](media/properties-margin.png)

3. <span data-ttu-id="3d484-213">Dodaj następujące XAML między <xref:System.Windows.Controls.Grid> znaczników do utworzenia definicji wierszy i kolumn:</span><span class="sxs-lookup"><span data-stu-id="3d484-213">Add the following XAML between the <xref:System.Windows.Controls.Grid> tags to create the row and column definitions:</span></span>

    [!code-xaml[ExpenseIt#8](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt3/ExpenseItHome.xaml#8)]

    <span data-ttu-id="3d484-214"><xref:System.Windows.Controls.RowDefinition.Height%2A> Dwóch wierszy jest równa <xref:System.Windows.GridLength.Auto%2A>, co oznacza, że wiersze mają rozmiar na podstawie zawartości w wierszach.</span><span class="sxs-lookup"><span data-stu-id="3d484-214">The <xref:System.Windows.Controls.RowDefinition.Height%2A> of two rows is set to <xref:System.Windows.GridLength.Auto%2A>, which means that the rows are sized based on the content in the rows.</span></span> <span data-ttu-id="3d484-215">Wartość domyślna <xref:System.Windows.Controls.RowDefinition.Height%2A> jest <xref:System.Windows.GridUnitType.Star> zmiany rozmiaru, co oznacza, że wiersze o nierównej wysokości ważona część dostępnego miejsca.</span><span class="sxs-lookup"><span data-stu-id="3d484-215">The default <xref:System.Windows.Controls.RowDefinition.Height%2A> is <xref:System.Windows.GridUnitType.Star> sizing, which means that the row height is a weighted proportion of the available space.</span></span> <span data-ttu-id="3d484-216">Na przykład jeśli masz dwa wiersze <xref:System.Windows.Controls.RowDefinition.Height%2A> elementu "\*", każdy z nich ma wysokości połowę dostępnego miejsca.</span><span class="sxs-lookup"><span data-stu-id="3d484-216">For example if two rows each have a <xref:System.Windows.Controls.RowDefinition.Height%2A> of "\*", they each have a height that is half of the available space.</span></span>

    <span data-ttu-id="3d484-217">Twoje <xref:System.Windows.Controls.Grid> powinno teraz wyglądać podobnie do poniższej XAML:</span><span class="sxs-lookup"><span data-stu-id="3d484-217">Your <xref:System.Windows.Controls.Grid> should now look like the following XAML:</span></span>

    [!code-xaml[ExpenseIt#9](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt3/ExpenseItHome.xaml#9)]

## <a name="add-controls"></a><span data-ttu-id="3d484-218">Dodawanie formantów</span><span class="sxs-lookup"><span data-stu-id="3d484-218">Add controls</span></span>

<span data-ttu-id="3d484-219">W tej sekcji zostaną zaktualizowane interfejsu użytkownika, aby wyświetlić listę osób, które użytkownik może wybrać z, aby wyświetlić raport wydatków dla strony głównej.</span><span class="sxs-lookup"><span data-stu-id="3d484-219">In this section, you'll update the home page UI to show a list of people that a user can select from to show the expense report for.</span></span> <span data-ttu-id="3d484-220">Formanty są obiektów interfejsu użytkownika, które umożliwiają użytkownikom na interakcję z aplikacją.</span><span class="sxs-lookup"><span data-stu-id="3d484-220">Controls are UI objects that allow users to interact with your application.</span></span> <span data-ttu-id="3d484-221">Aby uzyskać więcej informacji, zobacz [formantów](../../../../docs/framework/wpf/controls/index.md).</span><span class="sxs-lookup"><span data-stu-id="3d484-221">For more information, see [Controls](../../../../docs/framework/wpf/controls/index.md).</span></span>

<span data-ttu-id="3d484-222">Aby utworzyć tego interfejsu użytkownika, należy dodać następujące elementy do *`ExpenseItHome.xaml`*:</span><span class="sxs-lookup"><span data-stu-id="3d484-222">To create this UI, you'll add the following elements to *`ExpenseItHome.xaml`*:</span></span>

- <span data-ttu-id="3d484-223"><xref:System.Windows.Controls.ListBox> (Aby uzyskać listę osób).</span><span class="sxs-lookup"><span data-stu-id="3d484-223"><xref:System.Windows.Controls.ListBox> (for the list of people).</span></span>
- <span data-ttu-id="3d484-224"><xref:System.Windows.Controls.Label> (w przypadku nagłówek listy).</span><span class="sxs-lookup"><span data-stu-id="3d484-224"><xref:System.Windows.Controls.Label> (for the list header).</span></span>
- <span data-ttu-id="3d484-225"><xref:System.Windows.Controls.Button> (aby kliknij, aby wyświetlić raport wydatków dla osoby, która jest zaznaczony na liście).</span><span class="sxs-lookup"><span data-stu-id="3d484-225"><xref:System.Windows.Controls.Button> (to click to view the expense report for the person that is selected in the list).</span></span>

<span data-ttu-id="3d484-226">Każda kontrolka znajduje się w wierszu <xref:System.Windows.Controls.Grid> , ustawiając <xref:System.Windows.Controls.Grid.Row%2A?displayProperty=nameWithType> dołączona właściwość.</span><span class="sxs-lookup"><span data-stu-id="3d484-226">Each control is placed in a row of the <xref:System.Windows.Controls.Grid> by setting the <xref:System.Windows.Controls.Grid.Row%2A?displayProperty=nameWithType> attached property.</span></span> <span data-ttu-id="3d484-227">Aby uzyskać więcej informacji na temat właściwości dołączone zobacz [Przegląd właściwości dołączonych](../../../../docs/framework/wpf/advanced/attached-properties-overview.md).</span><span class="sxs-lookup"><span data-stu-id="3d484-227">For more information about attached properties, see [Attached Properties Overview](../../../../docs/framework/wpf/advanced/attached-properties-overview.md).</span></span>

1. <span data-ttu-id="3d484-228">Otwórz *`ExpenseItHome.xaml`*.</span><span class="sxs-lookup"><span data-stu-id="3d484-228">Open *`ExpenseItHome.xaml`*.</span></span>

2. <span data-ttu-id="3d484-229">Dodaj następujące XAML gdzieś między <xref:System.Windows.Controls.Grid> tagi:</span><span class="sxs-lookup"><span data-stu-id="3d484-229">Add the following XAML somewhere between the <xref:System.Windows.Controls.Grid> tags:</span></span>

   [!code-xaml[ExpenseIt#10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt4/ExpenseItHome.xaml#10)]

   > [!TIP]
   > <span data-ttu-id="3d484-230">Można również utworzyć formanty przeciągając je z **przybornika** okna na oknie projektu, a następnie ustawiając ich właściwości **właściwości** okna.</span><span class="sxs-lookup"><span data-stu-id="3d484-230">You can also create the controls by dragging them from the **Toolbox** window onto the design window, and then setting their properties in the **Properties** window.</span></span>

3. <span data-ttu-id="3d484-231">Skompiluj i uruchom aplikację.</span><span class="sxs-lookup"><span data-stu-id="3d484-231">Build and run the application.</span></span>

<span data-ttu-id="3d484-232">Na poniższej ilustracji zawiera kontrolki, które zostały utworzone:</span><span class="sxs-lookup"><span data-stu-id="3d484-232">The following illustration shows the controls you just created:</span></span>

![Zrzut ekranu przedstawiający programu ExpenseIt](../../../../docs/framework/wpf/getting-started/media/gettingstartedfigure2.png)

## <a name="add-an-image-and-a-title"></a><span data-ttu-id="3d484-234">Dodaj obraz i tytuł</span><span class="sxs-lookup"><span data-stu-id="3d484-234">Add an image and a title</span></span>

<span data-ttu-id="3d484-235">W tej sekcji zostaną zaktualizowane interfejsie użytkownika strony głównej przy użyciu obrazu i tytuł strony.</span><span class="sxs-lookup"><span data-stu-id="3d484-235">In this section, you'll update the home page UI with an image and a page title.</span></span>

1. <span data-ttu-id="3d484-236">Otwórz *`ExpenseItHome.xaml`*.</span><span class="sxs-lookup"><span data-stu-id="3d484-236">Open *`ExpenseItHome.xaml`*.</span></span>

2. <span data-ttu-id="3d484-237">Dodaj kolejną kolumnę do <xref:System.Windows.Controls.Grid.ColumnDefinitions%2A> o stałym <xref:System.Windows.Controls.ColumnDefinition.Width%2A> 230 pikseli:</span><span class="sxs-lookup"><span data-stu-id="3d484-237">Add another column to the <xref:System.Windows.Controls.Grid.ColumnDefinitions%2A> with a fixed <xref:System.Windows.Controls.ColumnDefinition.Width%2A> of 230 pixels:</span></span>

    [!code-xaml[ExpenseIt#11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#11)]

3. <span data-ttu-id="3d484-238">Dodaj kolejny wiersz do <xref:System.Windows.Controls.Grid.RowDefinitions%2A>, łącznie cztery wiersze:</span><span class="sxs-lookup"><span data-stu-id="3d484-238">Add another row to the <xref:System.Windows.Controls.Grid.RowDefinitions%2A>, for a total of four rows:</span></span>

    [!code-xaml[ExpenseIt#11b](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#11b)]

4. <span data-ttu-id="3d484-239">Przenieś kontrolki do drugiej kolumny, ustawiając <xref:System.Windows.Controls.Grid.Column%2A?displayProperty=nameWithType> właściwości na wartość 1 w każdym z trzech kontrolek (obramowanie, ListBox i przycisk).</span><span class="sxs-lookup"><span data-stu-id="3d484-239">Move the controls to the second column by setting the <xref:System.Windows.Controls.Grid.Column%2A?displayProperty=nameWithType> property to 1 in each of the three controls (Border, ListBox, and Button).</span></span>

5. <span data-ttu-id="3d484-240">Przenieś każdy formant w dół wiersz, przez zwiększenie jego <xref:System.Windows.Controls.Grid.Row%2A?displayProperty=nameWithType> wartość o 1.</span><span class="sxs-lookup"><span data-stu-id="3d484-240">Move each control down a row, by incrementing its <xref:System.Windows.Controls.Grid.Row%2A?displayProperty=nameWithType> value by 1.</span></span>

   <span data-ttu-id="3d484-241">XAML dla trzech kontrolek wygląda teraz następująco:</span><span class="sxs-lookup"><span data-stu-id="3d484-241">The XAML for the three controls now looks like this:</span></span>

    [!code-xaml[ExpenseIt#12](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#12)]

6. <span data-ttu-id="3d484-242">Ustaw <xref:System.Windows.Controls.Panel.Background%2A> z <xref:System.Windows.Controls.Grid> jako *watermark.png* plik obrazu, dodając następujące XAML gdzieś między `<Grid>` i `</Grid>` tagi:</span><span class="sxs-lookup"><span data-stu-id="3d484-242">Set the <xref:System.Windows.Controls.Panel.Background%2A> of the <xref:System.Windows.Controls.Grid> to be the *watermark.png* image file, by adding the following XAML somewhere between the `<Grid>` and `</Grid>` tags:</span></span>

    [!code-xaml[ExpenseIt#14](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#14)]

7. <span data-ttu-id="3d484-243">Przed <xref:System.Windows.Controls.Border> elementu Dodawanie <xref:System.Windows.Controls.Label> z zawartością "Wyświetl raport wydatków".</span><span class="sxs-lookup"><span data-stu-id="3d484-243">Before the <xref:System.Windows.Controls.Border> element, add a <xref:System.Windows.Controls.Label> with the content "View Expense Report".</span></span> <span data-ttu-id="3d484-244">Jest to tytuł strony.</span><span class="sxs-lookup"><span data-stu-id="3d484-244">This is the title of the page.</span></span>

    [!code-xaml[ExpenseIt#13](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#13)]

8. <span data-ttu-id="3d484-245">Skompiluj i uruchom aplikację.</span><span class="sxs-lookup"><span data-stu-id="3d484-245">Build and run the application.</span></span>

<span data-ttu-id="3d484-246">Poniższa ilustracja przedstawia wyniki co właśnie został dodany:</span><span class="sxs-lookup"><span data-stu-id="3d484-246">The following illustration shows the results of what you just added:</span></span>

![Zrzut ekranu przedstawiający programu ExpenseIt](../../../../docs/framework/wpf/getting-started/media/gettingstartedfigure3.png)

## <a name="add-code-to-handle-events"></a><span data-ttu-id="3d484-248">Dodaj kod do obsługi zdarzeń</span><span class="sxs-lookup"><span data-stu-id="3d484-248">Add code to handle events</span></span>

1. <span data-ttu-id="3d484-249">Otwórz *`ExpenseItHome.xaml`*.</span><span class="sxs-lookup"><span data-stu-id="3d484-249">Open *`ExpenseItHome.xaml`*.</span></span>

2. <span data-ttu-id="3d484-250">Dodaj <xref:System.Windows.Controls.Primitives.ButtonBase.Click> procedurę obsługi zdarzeń do <xref:System.Windows.Controls.Button> elementu.</span><span class="sxs-lookup"><span data-stu-id="3d484-250">Add a <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event handler to the <xref:System.Windows.Controls.Button> element.</span></span> <span data-ttu-id="3d484-251">Aby uzyskać więcej informacji, zobacz [jak: Utwórz procedurę obsługi zdarzenia prostego](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/bb675300(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="3d484-251">For more information, see [How to: Create a simple event handler](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/bb675300(v=vs.100)).</span></span>

    [!code-xaml[ExpenseIt#15](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt6/ExpenseItHome.xaml#15)]

3. <span data-ttu-id="3d484-252">Otwórz *`ExpenseItHome.xaml.vb`* lub *`ExpenseItHome.xaml.cs`*.</span><span class="sxs-lookup"><span data-stu-id="3d484-252">Open *`ExpenseItHome.xaml.vb`* or *`ExpenseItHome.xaml.cs`*.</span></span>

4. <span data-ttu-id="3d484-253">Dodaj następujący kod do `ExpenseItHome` klasy, aby dodać przycisk, program obsługi zdarzeń kliknięcia.</span><span class="sxs-lookup"><span data-stu-id="3d484-253">Add the following code to the `ExpenseItHome` class to add a button click event handler.</span></span> <span data-ttu-id="3d484-254">Zostanie otwarty program obsługi zdarzeń **ExpenseReportPage** strony.</span><span class="sxs-lookup"><span data-stu-id="3d484-254">The event handler opens the **ExpenseReportPage** page.</span></span>

    [!code-csharp[ExpenseIt#16](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt6/ExpenseItHome.xaml.cs#16)]
    [!code-vb[ExpenseIt#16](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt6/ExpenseItHome.xaml.vb#16)]

## <a name="create-the-ui-for-expensereportpage"></a><span data-ttu-id="3d484-255">Tworzenie interfejsu użytkownika dla ExpenseReportPage</span><span class="sxs-lookup"><span data-stu-id="3d484-255">Create the UI for ExpenseReportPage</span></span>

<span data-ttu-id="3d484-256">*ExpenseReportPage.xaml* wyświetla raport wydatków dla osób, które wybrano na **`ExpenseItHome`** strony.</span><span class="sxs-lookup"><span data-stu-id="3d484-256">*ExpenseReportPage.xaml* displays the expense report for the person that's selected on the **`ExpenseItHome`** page.</span></span> <span data-ttu-id="3d484-257">W tej sekcji utworzysz interfejs użytkownika dla **ExpenseReportPage**.</span><span class="sxs-lookup"><span data-stu-id="3d484-257">In this section, you'll create the UI for **ExpenseReportPage**.</span></span> <span data-ttu-id="3d484-258">Dodasz również tła i wypełnij kolorów do różnych elementów interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="3d484-258">You'll also add background and fill colors to the various UI elements.</span></span>

1. <span data-ttu-id="3d484-259">Otwórz *ExpenseReportPage.xaml*.</span><span class="sxs-lookup"><span data-stu-id="3d484-259">Open *ExpenseReportPage.xaml*.</span></span>

2. <span data-ttu-id="3d484-260">Dodaj następujące XAML między <xref:System.Windows.Controls.Grid> tagi:</span><span class="sxs-lookup"><span data-stu-id="3d484-260">Add the following XAML between the <xref:System.Windows.Controls.Grid> tags:</span></span>

    [!code-xaml[ExpenseIt#17](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt6/ExpenseReportPage.xaml#17)]

    <span data-ttu-id="3d484-261">Ten interfejs jest podobny do *`ExpenseItHome.xaml`*, z wyjątkiem dane raportu są wyświetlane w <xref:System.Windows.Controls.DataGrid>.</span><span class="sxs-lookup"><span data-stu-id="3d484-261">This UI is similar to *`ExpenseItHome.xaml`*, except the report data is displayed in a <xref:System.Windows.Controls.DataGrid>.</span></span>

3. <span data-ttu-id="3d484-262">Skompiluj i uruchom aplikację.</span><span class="sxs-lookup"><span data-stu-id="3d484-262">Build and run the application.</span></span>

    > [!NOTE]
    > <span data-ttu-id="3d484-263">Jeśli wystąpi błąd, który <xref:System.Windows.Controls.DataGrid> nie został znaleziony lub nie istnieje, upewnij się, że projekt jest przeznaczony dla .NET Framework 4 lub nowszej.</span><span class="sxs-lookup"><span data-stu-id="3d484-263">If you get an error that the <xref:System.Windows.Controls.DataGrid> was not found or does not exist, make sure that your project targets the .NET Framework 4 or later.</span></span> <span data-ttu-id="3d484-264">Aby uzyskać więcej informacji, zobacz [jak: Docelowa wersja systemu .NET Framework](/visualstudio/ide/how-to-target-a-version-of-the-dotnet-framework).</span><span class="sxs-lookup"><span data-stu-id="3d484-264">For more information, see [How to: Target a Version of the .NET Framework](/visualstudio/ide/how-to-target-a-version-of-the-dotnet-framework).</span></span>

4. <span data-ttu-id="3d484-265">Wybierz **widoku** przycisku.</span><span class="sxs-lookup"><span data-stu-id="3d484-265">Select the **View** button.</span></span>

    <span data-ttu-id="3d484-266">Zostanie wyświetlona strona raportu wydatków.</span><span class="sxs-lookup"><span data-stu-id="3d484-266">The expense report page appears.</span></span> <span data-ttu-id="3d484-267">Zwróć również uwagę, że zostanie włączony przycisk przeglądania do tyłu.</span><span class="sxs-lookup"><span data-stu-id="3d484-267">Also notice that the back navigation button is enabled.</span></span>

<span data-ttu-id="3d484-268">Na poniższej ilustracji przedstawiono elementy interfejsu użytkownika dodano do *ExpenseReportPage.xaml*.</span><span class="sxs-lookup"><span data-stu-id="3d484-268">The following illustration shows the UI elements added to *ExpenseReportPage.xaml*.</span></span>

![Zrzut ekranu przedstawiający programu ExpenseIt](../../../../docs/framework/wpf/getting-started/media/gettingstartedfigure4.png)

## <a name="style-controls"></a><span data-ttu-id="3d484-270">Kontrolki stylu</span><span class="sxs-lookup"><span data-stu-id="3d484-270">Style controls</span></span>

<span data-ttu-id="3d484-271">Wygląd elementów różnych często jest taka sama dla wszystkich elementów tego samego typu w interfejsie użytkownika.</span><span class="sxs-lookup"><span data-stu-id="3d484-271">The appearance of various elements is often the same for all elements of the same type in a UI.</span></span> <span data-ttu-id="3d484-272">Korzysta z interfejsu użytkownika [style](../../../../docs/framework/wpf/controls/styling-and-templating.md) się wygląd wielokrotnego użytku dla wielu elementów.</span><span class="sxs-lookup"><span data-stu-id="3d484-272">UI uses [styles](../../../../docs/framework/wpf/controls/styling-and-templating.md) to make appearances reusable across multiple elements.</span></span> <span data-ttu-id="3d484-273">Możliwość ponownego wykorzystania stylów pomaga uprościć tworzenie XAML i zarządzanie nimi.</span><span class="sxs-lookup"><span data-stu-id="3d484-273">The reusability of styles helps to simplify XAML creation and management.</span></span> <span data-ttu-id="3d484-274">W tej sekcji zastępuje atrybuty-elementowej, które zostały zdefiniowane w poprzednich krokach przy użyciu stylów.</span><span class="sxs-lookup"><span data-stu-id="3d484-274">This section replaces the per-element attributes that were defined in previous steps with styles.</span></span>

1. <span data-ttu-id="3d484-275">Otwórz *Application.xaml* lub *App.xaml*.</span><span class="sxs-lookup"><span data-stu-id="3d484-275">Open *Application.xaml* or *App.xaml*.</span></span>

2. <span data-ttu-id="3d484-276">Dodaj następujące XAML między <xref:System.Windows.Application.Resources%2A?displayProperty=nameWithType> tagi:</span><span class="sxs-lookup"><span data-stu-id="3d484-276">Add the following XAML between the <xref:System.Windows.Application.Resources%2A?displayProperty=nameWithType> tags:</span></span>

    [!code-xaml[ExpenseIt#18](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt7/App.xaml#18)]

    <span data-ttu-id="3d484-277">Ta XAML dodaje następujące style:</span><span class="sxs-lookup"><span data-stu-id="3d484-277">This XAML adds the following styles:</span></span>

    - <span data-ttu-id="3d484-278">`headerTextStyle`: Aby sformatować tytuł strony <xref:System.Windows.Controls.Label>.</span><span class="sxs-lookup"><span data-stu-id="3d484-278">`headerTextStyle`: To format the page title <xref:System.Windows.Controls.Label>.</span></span>

    - <span data-ttu-id="3d484-279">`labelStyle`: Aby sformatować <xref:System.Windows.Controls.Label> kontrolki.</span><span class="sxs-lookup"><span data-stu-id="3d484-279">`labelStyle`: To format the <xref:System.Windows.Controls.Label> controls.</span></span>

    - <span data-ttu-id="3d484-280">`columnHeaderStyle`: Aby sformatować <xref:System.Windows.Controls.Primitives.DataGridColumnHeader>.</span><span class="sxs-lookup"><span data-stu-id="3d484-280">`columnHeaderStyle`: To format the <xref:System.Windows.Controls.Primitives.DataGridColumnHeader>.</span></span>

    - <span data-ttu-id="3d484-281">`listHeaderStyle`: Aby sformatować nagłówek listy <xref:System.Windows.Controls.Border> kontrolki.</span><span class="sxs-lookup"><span data-stu-id="3d484-281">`listHeaderStyle`: To format the list header <xref:System.Windows.Controls.Border> controls.</span></span>

    - <span data-ttu-id="3d484-282">`listHeaderTextStyle`: Aby sformatować nagłówek listy <xref:System.Windows.Controls.Label>.</span><span class="sxs-lookup"><span data-stu-id="3d484-282">`listHeaderTextStyle`: To format the list header <xref:System.Windows.Controls.Label>.</span></span>

    - <span data-ttu-id="3d484-283">`buttonStyle`: Aby sformatować <xref:System.Windows.Controls.Button> na `ExpenseItHome.xaml`.</span><span class="sxs-lookup"><span data-stu-id="3d484-283">`buttonStyle`: To format the <xref:System.Windows.Controls.Button> on `ExpenseItHome.xaml`.</span></span>

    <span data-ttu-id="3d484-284">Zauważ, że style są zasobami i elementy podrzędne <xref:System.Windows.Application.Resources%2A?displayProperty=nameWithType> elementu właściwości.</span><span class="sxs-lookup"><span data-stu-id="3d484-284">Notice that the styles are resources and children of the <xref:System.Windows.Application.Resources%2A?displayProperty=nameWithType> property element.</span></span> <span data-ttu-id="3d484-285">W tej lokalizacji stylów są stosowane do wszystkich elementów w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="3d484-285">In this location, the styles are applied to all the elements in an application.</span></span> <span data-ttu-id="3d484-286">Na przykład korzystania z zasobów w aplikacji .NET Framework, zobacz [wykorzystania zasobów aplikacji](../../../../docs/framework/wpf/advanced/how-to-use-application-resources.md).</span><span class="sxs-lookup"><span data-stu-id="3d484-286">For an example of using resources in a .NET Framework application, see [Use Application Resources](../../../../docs/framework/wpf/advanced/how-to-use-application-resources.md).</span></span>

3. <span data-ttu-id="3d484-287">Otwórz *`ExpenseItHome.xaml`*.</span><span class="sxs-lookup"><span data-stu-id="3d484-287">Open *`ExpenseItHome.xaml`*.</span></span>

4. <span data-ttu-id="3d484-288">Zamień wszystko pomiędzy <xref:System.Windows.Controls.Grid> elementów za pomocą następujących XAML:</span><span class="sxs-lookup"><span data-stu-id="3d484-288">Replace everything between the <xref:System.Windows.Controls.Grid> elements with the following XAML:</span></span>

    [!code-xaml[ExpenseIt#19](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt7/ExpenseItHome.xaml#19)]

    <span data-ttu-id="3d484-289">Właściwości, takie jak <xref:System.Windows.VerticalAlignment> i <xref:System.Windows.Media.FontFamily> definiują wygląd każdego formantu usunięty i zastąpiony, stosując style.</span><span class="sxs-lookup"><span data-stu-id="3d484-289">The properties such as <xref:System.Windows.VerticalAlignment> and <xref:System.Windows.Media.FontFamily> that define the look of each control are removed and replaced by applying the styles.</span></span> <span data-ttu-id="3d484-290">Na przykład `headerTextStyle` jest stosowany do "Wyświetl raport wydatków" <xref:System.Windows.Controls.Label>.</span><span class="sxs-lookup"><span data-stu-id="3d484-290">For example, the `headerTextStyle` is applied to the "View Expense Report" <xref:System.Windows.Controls.Label>.</span></span>

5. <span data-ttu-id="3d484-291">Otwórz *ExpenseReportPage.xaml*.</span><span class="sxs-lookup"><span data-stu-id="3d484-291">Open *ExpenseReportPage.xaml*.</span></span>

6. <span data-ttu-id="3d484-292">Zamień wszystko pomiędzy <xref:System.Windows.Controls.Grid> elementów za pomocą następujących XAML:</span><span class="sxs-lookup"><span data-stu-id="3d484-292">Replace everything between the <xref:System.Windows.Controls.Grid> elements with the following XAML:</span></span>

    [!code-xaml[ExpenseIt#20](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt7/ExpenseReportPage.xaml#20)]

    <span data-ttu-id="3d484-293">Spowoduje to dodanie stylów <xref:System.Windows.Controls.Label> i <xref:System.Windows.Controls.Border> elementów.</span><span class="sxs-lookup"><span data-stu-id="3d484-293">This adds styles to the <xref:System.Windows.Controls.Label> and <xref:System.Windows.Controls.Border> elements.</span></span>

## <a name="bind-data-to-a-control"></a><span data-ttu-id="3d484-294">Powiązanie danych kontrolki</span><span class="sxs-lookup"><span data-stu-id="3d484-294">Bind data to a control</span></span>

<span data-ttu-id="3d484-295">W tej sekcji utworzysz dane XML, który jest powiązany z różnych formantów.</span><span class="sxs-lookup"><span data-stu-id="3d484-295">In this section, you'll create the XML data that is bound to various controls.</span></span>

1. <span data-ttu-id="3d484-296">Otwórz *`ExpenseItHome.xaml`*.</span><span class="sxs-lookup"><span data-stu-id="3d484-296">Open *`ExpenseItHome.xaml`*.</span></span>

2. <span data-ttu-id="3d484-297">Po otwarciu <xref:System.Windows.Controls.Grid> elementu, Dodaj następujące XAML do tworzenia <xref:System.Windows.Data.XmlDataProvider> dla każdej osoby, która zawiera dane:</span><span class="sxs-lookup"><span data-stu-id="3d484-297">After the opening <xref:System.Windows.Controls.Grid> element, add the following XAML to create an <xref:System.Windows.Data.XmlDataProvider> that contains the data for each person:</span></span>

    [!code-xaml[ExpenseIt#21](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml#21)]
    [!code-xaml[ExpenseIt#23](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml#23)]
    [!code-xaml[ExpenseIt#22](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml#22)]

    <span data-ttu-id="3d484-298">Dane są tworzone jako <xref:System.Windows.Controls.Grid> zasobów.</span><span class="sxs-lookup"><span data-stu-id="3d484-298">The data is created as a <xref:System.Windows.Controls.Grid> resource.</span></span> <span data-ttu-id="3d484-299">Zwykle to będą ładowane jako plik, ale dla uproszczenia dane są dodawane na tekście.</span><span class="sxs-lookup"><span data-stu-id="3d484-299">Normally this would be loaded as a file, but for simplicity the data is added inline.</span></span>

3. <span data-ttu-id="3d484-300">W ramach `<Grid.Resources>` elementu, Dodaj następujący kod <xref:System.Windows.DataTemplate>, który definiuje sposób wyświetlania danych w <xref:System.Windows.Controls.ListBox>:</span><span class="sxs-lookup"><span data-stu-id="3d484-300">Within the `<Grid.Resources>` element, add the following <xref:System.Windows.DataTemplate>, which defines how to display the data in the <xref:System.Windows.Controls.ListBox>:</span></span>

    [!code-xaml[ExpenseIt#21](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml#21)]
    [!code-xaml[ExpenseIt#24](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml#24)]
    [!code-xaml[ExpenseIt#22](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml#22)]

    <span data-ttu-id="3d484-301">Aby uzyskać więcej informacji na temat szablonów danych zobacz [Przegląd szablonowanie danych](../../../../docs/framework/wpf/data/data-templating-overview.md).</span><span class="sxs-lookup"><span data-stu-id="3d484-301">For more information about data templates, see [Data templating overview](../../../../docs/framework/wpf/data/data-templating-overview.md).</span></span>

4. <span data-ttu-id="3d484-302">Zastąp istniejące <xref:System.Windows.Controls.ListBox> za pomocą następujących XAML:</span><span class="sxs-lookup"><span data-stu-id="3d484-302">Replace the existing <xref:System.Windows.Controls.ListBox> with the following XAML:</span></span>

    [!code-xaml[ExpenseIt#25](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml#25)]

    <span data-ttu-id="3d484-303">Wiąże się to XAML <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> właściwość <xref:System.Windows.Controls.ListBox> ze źródłem danych i stosuje szablon danych jako <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A>.</span><span class="sxs-lookup"><span data-stu-id="3d484-303">This XAML binds the <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> property of the <xref:System.Windows.Controls.ListBox> to the data source and applies the data template as the <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A>.</span></span>

## <a name="connect-data-to-controls"></a><span data-ttu-id="3d484-304">Łączenie danych z kontrolkami</span><span class="sxs-lookup"><span data-stu-id="3d484-304">Connect data to controls</span></span>

<span data-ttu-id="3d484-305">Następnie dodasz kod, aby pobrać nazwy, która została wybrana na **`ExpenseItHome`** strony, a następnie przekazać go do konstruktora obiektu **ExpenseReportPage**.</span><span class="sxs-lookup"><span data-stu-id="3d484-305">Next, you'll add code to retrieve the name that's selected on the **`ExpenseItHome`** page and pass it to the constructor of **ExpenseReportPage**.</span></span> <span data-ttu-id="3d484-306">**ExpenseReportPage** ustawia kontekst danych przy użyciu przekazanych elementu, który jest zdefiniowany kontrolek w *ExpenseReportPage.xaml* powiązać.</span><span class="sxs-lookup"><span data-stu-id="3d484-306">**ExpenseReportPage** sets its data context with the passed item, which is what the controls defined in *ExpenseReportPage.xaml* bind to.</span></span>

1. <span data-ttu-id="3d484-307">Otwórz *ExpenseReportPage.xaml.vb* lub *ExpenseReportPage.xaml.cs*.</span><span class="sxs-lookup"><span data-stu-id="3d484-307">Open *ExpenseReportPage.xaml.vb* or *ExpenseReportPage.xaml.cs*.</span></span>

2. <span data-ttu-id="3d484-308">Dodaj konstruktora przyjmującego obiekt, dzięki czemu można przekazać dane raportu wydatków wybrane osoby.</span><span class="sxs-lookup"><span data-stu-id="3d484-308">Add a constructor that takes an object so you can pass the expense report data of the selected person.</span></span>

    [!code-csharp[ExpenseIt#26](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseReportPage.xaml.cs#26)]
    [!code-vb[ExpenseIt#26](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt8/ExpenseReportPage.xaml.vb#26)]

3. <span data-ttu-id="3d484-309">Otwórz *`ExpenseItHome.xaml.vb`* lub *`ExpenseItHome.xaml.cs`*.</span><span class="sxs-lookup"><span data-stu-id="3d484-309">Open *`ExpenseItHome.xaml.vb`* or *`ExpenseItHome.xaml.cs`*.</span></span>

4. <span data-ttu-id="3d484-310">Zmiana <xref:System.Windows.Controls.Primitives.ButtonBase.Click> program obsługi zdarzeń, aby wywołać nowego konstruktora, przekazując dane raportu wydatków wybrane osoby.</span><span class="sxs-lookup"><span data-stu-id="3d484-310">Change the <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event handler to call the new constructor passing the expense report data of the selected person.</span></span>

    [!code-csharp[ExpenseIt#27](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml.cs#27)]
    [!code-vb[ExpenseIt#27](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt8/ExpenseItHome.xaml.vb#27)]

## <a name="style-data-with-data-templates"></a><span data-ttu-id="3d484-311">Styl danych za pomocą szablonów danych</span><span class="sxs-lookup"><span data-stu-id="3d484-311">Style data with data templates</span></span>

<span data-ttu-id="3d484-312">W tej sekcji zostaną zaktualizowane w interfejsie użytkownika dla każdego elementu na listach powiązanych z danymi przy użyciu szablonów danych.</span><span class="sxs-lookup"><span data-stu-id="3d484-312">In this section, you'll update the UI for each item in the data-bound lists by using data templates.</span></span>

1. <span data-ttu-id="3d484-313">Otwórz *ExpenseReportPage.xaml*.</span><span class="sxs-lookup"><span data-stu-id="3d484-313">Open *ExpenseReportPage.xaml*.</span></span>

2. <span data-ttu-id="3d484-314">Powiąż z zawartością "Name" i "Dział" <xref:System.Windows.Controls.Label> elementy do odpowiednich danych źródła właściwości.</span><span class="sxs-lookup"><span data-stu-id="3d484-314">Bind the content of the "Name" and "Department" <xref:System.Windows.Controls.Label> elements to the appropriate data source property.</span></span> <span data-ttu-id="3d484-315">Aby uzyskać więcej informacji na temat tworzenia powiązań danych, zobacz [Przegląd wiązanie danych](../../../../docs/framework/wpf/data/data-binding-overview.md).</span><span class="sxs-lookup"><span data-stu-id="3d484-315">For more information about data binding, see [Data binding overview](../../../../docs/framework/wpf/data/data-binding-overview.md).</span></span>

    [!code-xaml[ExpenseIt#31](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseReportPage.xaml#31)]

3. <span data-ttu-id="3d484-316">Po otwarciu <xref:System.Windows.Controls.Grid> elementu, Dodaj następujące szablony danych, które określają sposób wyświetlania danych raportu wydatków:</span><span class="sxs-lookup"><span data-stu-id="3d484-316">After the opening <xref:System.Windows.Controls.Grid> element, add the following data templates, which define how to display the expense report data:</span></span>

    [!code-xaml[ExpenseIt#30](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseReportPage.xaml#30)]

4. <span data-ttu-id="3d484-317">Zastąp <xref:System.Windows.Controls.DataGridTextColumn> elementów za pomocą <xref:System.Windows.Controls.DataGridTemplateColumn> w obszarze <xref:System.Windows.Controls.DataGrid> elementu i stosować szablony do nich.</span><span class="sxs-lookup"><span data-stu-id="3d484-317">Replace the <xref:System.Windows.Controls.DataGridTextColumn> elements with <xref:System.Windows.Controls.DataGridTemplateColumn> under the <xref:System.Windows.Controls.DataGrid> element and apply the templates to them.</span></span>

    [!code-xaml[ExpenseIt#32](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseReportPage.xaml#32)]

5. <span data-ttu-id="3d484-318">Skompiluj i uruchom aplikację.</span><span class="sxs-lookup"><span data-stu-id="3d484-318">Build and run the application.</span></span>

6. <span data-ttu-id="3d484-319">Wybierz osobę, a następnie wybierz pozycję **widoku** przycisku.</span><span class="sxs-lookup"><span data-stu-id="3d484-319">Select a person and then select the **View** button.</span></span>

<span data-ttu-id="3d484-320">Na poniższej ilustracji przedstawiono obie strony `ExpenseIt` aplikacji za pomocą formantów, układ, style, powiązań danych i zastosowanych szablonów danych:</span><span class="sxs-lookup"><span data-stu-id="3d484-320">The following illustration shows both pages of the `ExpenseIt` application with controls, layout, styles, data binding, and data templates applied:</span></span>

![Przykładowe zrzuty ekranu programu ExpenseIt](../../../../docs/framework/wpf/getting-started/media/gettingstartedfigure5.png)

> [!NOTE]
> <span data-ttu-id="3d484-322">Ten przykład demonstruje określonych funkcji, WPF i nie należy wykonać wszystkie najlepsze rozwiązania w zakresie elementów, takich jak bezpieczeństwo, lokalizacja i ułatwienia dostępu.</span><span class="sxs-lookup"><span data-stu-id="3d484-322">This sample demonstrates a specific feature of WPF and doesn't follow all best practices for things like security, localization, and accessibility.</span></span> <span data-ttu-id="3d484-323">Aby uzyskać kompleksowe informacje na temat WPF i najlepszych rozwiązań projektowania aplikacji .NET Framework Zobacz następujące tematy:</span><span class="sxs-lookup"><span data-stu-id="3d484-323">For comprehensive coverage of WPF and the .NET Framework application development best practices, see the following topics:</span></span>
>
> - [<span data-ttu-id="3d484-324">Ułatwienia dostępu</span><span class="sxs-lookup"><span data-stu-id="3d484-324">Accessibility</span></span>](../../../../docs/framework/ui-automation/accessibility-best-practices.md)
>
> - [<span data-ttu-id="3d484-325">Zabezpieczenia</span><span class="sxs-lookup"><span data-stu-id="3d484-325">Security</span></span>](../../../../docs/framework/wpf/security-wpf.md)
>
> - [<span data-ttu-id="3d484-326">Lokalizacja i globalizacja WPF</span><span class="sxs-lookup"><span data-stu-id="3d484-326">WPF globalization and localization</span></span>](../../../../docs/framework/wpf/advanced/wpf-globalization-and-localization-overview.md)
>
> - [<span data-ttu-id="3d484-327">Wydajności WPF</span><span class="sxs-lookup"><span data-stu-id="3d484-327">WPF performance</span></span>](../../../../docs/framework/wpf/advanced/optimizing-wpf-application-performance.md)

## <a name="next-steps"></a><span data-ttu-id="3d484-328">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="3d484-328">Next steps</span></span>

<span data-ttu-id="3d484-329">W tym instruktażu przedstawiono kilka technik tworzenia interfejsu użytkownika przy użyciu Windows Presentation Foundation (WPF).</span><span class="sxs-lookup"><span data-stu-id="3d484-329">In this walkthrough you learned a number of techniques for creating a UI using Windows Presentation Foundation (WPF).</span></span> <span data-ttu-id="3d484-330">Powinna już podstawową wiedzę na temat bloki konstrukcyjne aplikacji powiązanych z danymi, .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="3d484-330">You should now have a basic understanding of the building blocks of a data-bound, .NET Framework application.</span></span> <span data-ttu-id="3d484-331">Aby uzyskać więcej informacji o modelach programowania i architektura WPF zobacz następujące tematy:</span><span class="sxs-lookup"><span data-stu-id="3d484-331">For more information about the WPF architecture and programming models, see the following topics:</span></span>

- [<span data-ttu-id="3d484-332">Architektura WPF</span><span class="sxs-lookup"><span data-stu-id="3d484-332">WPF architecture</span></span>](../../../../docs/framework/wpf/advanced/wpf-architecture.md)
- [<span data-ttu-id="3d484-333">Przegląd XAML (WPF)</span><span class="sxs-lookup"><span data-stu-id="3d484-333">XAML overview (WPF)</span></span>](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)
- [<span data-ttu-id="3d484-334">Przegląd właściwości zależności</span><span class="sxs-lookup"><span data-stu-id="3d484-334">Dependency properties overview</span></span>](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)
- [<span data-ttu-id="3d484-335">Układ</span><span class="sxs-lookup"><span data-stu-id="3d484-335">Layout</span></span>](../../../../docs/framework/wpf/advanced/layout.md)

<span data-ttu-id="3d484-336">Aby uzyskać więcej informacji na temat tworzenia aplikacji zobacz następujące tematy:</span><span class="sxs-lookup"><span data-stu-id="3d484-336">For more information about creating applications, see the following topics:</span></span>

- [<span data-ttu-id="3d484-337">Tworzenie aplikacji</span><span class="sxs-lookup"><span data-stu-id="3d484-337">Application development</span></span>](../../../../docs/framework/wpf/app-development/index.md)
- [<span data-ttu-id="3d484-338">Kontrolki</span><span class="sxs-lookup"><span data-stu-id="3d484-338">Controls</span></span>](../../../../docs/framework/wpf/controls/index.md)
- [<span data-ttu-id="3d484-339">Przegląd wiązanie danych</span><span class="sxs-lookup"><span data-stu-id="3d484-339">Data binding overview</span></span>](../../../../docs/framework/wpf/data/data-binding-overview.md)
- [<span data-ttu-id="3d484-340">Grafika i multimedia</span><span class="sxs-lookup"><span data-stu-id="3d484-340">Graphics and multimedia</span></span>](../../../../docs/framework/wpf/graphics-multimedia/index.md)
- [<span data-ttu-id="3d484-341">Dokumenty w WPF</span><span class="sxs-lookup"><span data-stu-id="3d484-341">Documents in WPF</span></span>](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)

## <a name="see-also"></a><span data-ttu-id="3d484-342">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3d484-342">See also</span></span>

- [<span data-ttu-id="3d484-343">Panele — omówienie</span><span class="sxs-lookup"><span data-stu-id="3d484-343">Panels overview</span></span>](../../../../docs/framework/wpf/controls/panels-overview.md)
- [<span data-ttu-id="3d484-344">Przegląd szablonowanie danych</span><span class="sxs-lookup"><span data-stu-id="3d484-344">Data templating overview</span></span>](../../../../docs/framework/wpf/data/data-templating-overview.md)
- [<span data-ttu-id="3d484-345">Tworzenie aplikacji WPF</span><span class="sxs-lookup"><span data-stu-id="3d484-345">Build a WPF application</span></span>](../../../../docs/framework/wpf/app-development/building-a-wpf-application-wpf.md)
- [<span data-ttu-id="3d484-346">Style i szablony</span><span class="sxs-lookup"><span data-stu-id="3d484-346">Styles and templates</span></span>](../../../../docs/framework/wpf/controls/styles-and-templates.md)
