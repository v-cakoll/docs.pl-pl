---
title: Tworzenie aplikacji WPF w programie Visual Studio
ms.date: 03/20/2019
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
ms.openlocfilehash: 4919424339df1f8d2c68465bd9f9af42f344fe37
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70254073"
---
# <a name="walkthrough-my-first-wpf-desktop-application"></a><span data-ttu-id="5167d-102">Przewodnik: Moja pierwsza aplikacja klasyczna WPF</span><span class="sxs-lookup"><span data-stu-id="5167d-102">Walkthrough: My first WPF desktop application</span></span>

<span data-ttu-id="5167d-103">W tym artykule przedstawiono sposób tworzenia aplikacji klasycznych Windows Presentation Foundation (WPF), która zawiera elementy wspólne dla większości aplikacji WPF: Znaczniki Extensible Application Markup Language (XAML), powiązane z kodem, definicje aplikacji, formanty, układ, powiązanie danych i style.</span><span class="sxs-lookup"><span data-stu-id="5167d-103">This article shows you how to develop a Windows Presentation Foundation (WPF) desktop application that includes the elements that are common to most WPF applications: Extensible Application Markup Language (XAML) markup, code-behind, application definitions, controls, layout, data binding, and styles.</span></span> <span data-ttu-id="5167d-104">Aby opracować aplikację, użyjesz programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="5167d-104">To develop the application, you'll use Visual Studio.</span></span> 

<span data-ttu-id="5167d-105">Ten przewodnik obejmuje następujące kroki:</span><span class="sxs-lookup"><span data-stu-id="5167d-105">This walkthrough includes the following steps:</span></span>

- <span data-ttu-id="5167d-106">Użyj języka XAML, aby zaprojektować wygląd interfejsu użytkownika aplikacji.</span><span class="sxs-lookup"><span data-stu-id="5167d-106">Use XAML to design the appearance of the application's user interface (UI).</span></span>

- <span data-ttu-id="5167d-107">Napisz kod, aby skompilować zachowanie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="5167d-107">Write code to build the application's behavior.</span></span>

- <span data-ttu-id="5167d-108">Utwórz definicję aplikacji w celu zarządzania aplikacją.</span><span class="sxs-lookup"><span data-stu-id="5167d-108">Create an application definition to manage the application.</span></span>

- <span data-ttu-id="5167d-109">Dodaj kontrolki i Utwórz układ, aby utworzyć interfejs użytkownika aplikacji.</span><span class="sxs-lookup"><span data-stu-id="5167d-109">Add controls and create the layout to compose the application UI.</span></span>

- <span data-ttu-id="5167d-110">Tworzenie stylów dla spójnego wyglądu w całym interfejsie użytkownika aplikacji.</span><span class="sxs-lookup"><span data-stu-id="5167d-110">Create styles for a consistent appearance throughout the application's UI.</span></span>

- <span data-ttu-id="5167d-111">Powiąż interfejs użytkownika z danymi, zarówno w celu wypełnienia interfejsu użytkownika z danych, jak i zachowania synchronizacji danych i interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="5167d-111">Bind the UI to data, both to populate the UI from data and to keep the data and UI synchronized.</span></span>

<span data-ttu-id="5167d-112">Na koniec przewodnika utworzysz autonomiczną aplikację systemu Windows, która umożliwia użytkownikom wyświetlanie raportów wydatków dla wybranych osób.</span><span class="sxs-lookup"><span data-stu-id="5167d-112">By the end of the walkthrough, you'll have built a standalone Windows application that allows users to view expense reports for selected people.</span></span> <span data-ttu-id="5167d-113">Aplikacja składa się z kilku stron WPF, które są hostowane w oknie stylu przeglądarki.</span><span class="sxs-lookup"><span data-stu-id="5167d-113">The application is composed of several WPF pages that are hosted in a browser-style window.</span></span>

> [!TIP]
> <span data-ttu-id="5167d-114">Przykładowy kod, który jest używany do kompilowania tego instruktażu, jest dostępny zarówno C# w Visual Basic, jak i w [instruktażu przykładowego kodu aplikacji WPF](https://github.com/Microsoft/WPF-Samples/tree/master/Getting%20Started/WalkthroughFirstWPFApp).</span><span class="sxs-lookup"><span data-stu-id="5167d-114">The sample code that is used to build this walkthrough is available for both Visual Basic and C# at [Walkthrough WPF App Sample Code](https://github.com/Microsoft/WPF-Samples/tree/master/Getting%20Started/WalkthroughFirstWPFApp).</span></span>
>
> <span data-ttu-id="5167d-115">Można przełączać język kodu przykładowego kodu między C# i Visual Basic przy użyciu **\< />** listy rozwijanej w prawym górnym rogu tego artykułu.</span><span class="sxs-lookup"><span data-stu-id="5167d-115">You can toggle the code language of the sample code between C# and Visual Basic by using the **\</>** drop-down on the upper right side of this article.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="5167d-116">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="5167d-116">Prerequisites</span></span>

- <span data-ttu-id="5167d-117">Visual Studio 2017 lub nowszy (w tym artykule jest wykorzystywany program Visual Studio 2019)</span><span class="sxs-lookup"><span data-stu-id="5167d-117">Visual Studio 2017 or later (this article uses Visual Studio 2019)</span></span>

   <span data-ttu-id="5167d-118">Aby uzyskać więcej informacji na temat instalowania najnowszej wersji programu Visual Studio, zobacz [Instalowanie programu Visual Studio](/visualstudio/install/install-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="5167d-118">For more information about installing the latest version of Visual Studio, see [Install Visual Studio](/visualstudio/install/install-visual-studio).</span></span>

## <a name="create-the-application-project"></a><span data-ttu-id="5167d-119">Tworzenie projektu aplikacji</span><span class="sxs-lookup"><span data-stu-id="5167d-119">Create the application project</span></span>

<span data-ttu-id="5167d-120">Pierwszym krokiem jest utworzenie infrastruktury aplikacji, która obejmuje definicję aplikacji, dwie strony i obraz.</span><span class="sxs-lookup"><span data-stu-id="5167d-120">The first step is to create the application infrastructure, which includes an application definition, two pages, and an image.</span></span>

1. <span data-ttu-id="5167d-121">Utwórz nowy projekt aplikacji WPF w Visual Basic lub wizualizacji C# o **`ExpenseIt`** nazwie:</span><span class="sxs-lookup"><span data-stu-id="5167d-121">Create a new WPF Application project in Visual Basic or Visual C# named **`ExpenseIt`**:</span></span>

   1. <span data-ttu-id="5167d-122">Otwórz program Visual Studio i wybierz pozycję **Utwórz nowy projekt** w menu **wprowadzenie** .</span><span class="sxs-lookup"><span data-stu-id="5167d-122">Open Visual Studio and select **Create a new project** under the **Get started** menu.</span></span>

      <span data-ttu-id="5167d-123">Zostanie otwarte okno dialogowe **Tworzenie nowego projektu** .</span><span class="sxs-lookup"><span data-stu-id="5167d-123">The **Create a new project** dialog opens.</span></span>

   2. <span data-ttu-id="5167d-124">Z listy rozwijanej **Język** wybierz opcję **C#** lub **Visual Basic**.</span><span class="sxs-lookup"><span data-stu-id="5167d-124">In the **Language** dropdown, select either **C#** or **Visual Basic**.</span></span>
      
   3. <span data-ttu-id="5167d-125">Wybierz szablon **Aplikacja WPF (.NET Framework)** , a następnie wybierz przycisk **dalej**.</span><span class="sxs-lookup"><span data-stu-id="5167d-125">Select the **WPF App (.NET Framework)** template and then select **Next**.</span></span> 
     
      ![Okno dialogowe Tworzenie nowego projektu](./media/walkthrough-my-first-wpf-desktop-application/create-new-project-dialog.png)
    
      <span data-ttu-id="5167d-127">Zostanie otwarte okno dialogowe **Konfigurowanie nowego projektu** .</span><span class="sxs-lookup"><span data-stu-id="5167d-127">The **Configure your new project** dialog opens.</span></span>

   4. <span data-ttu-id="5167d-128">Wprowadź nazwę **`ExpenseIt`** projektu, a następnie wybierz pozycję **Utwórz**.</span><span class="sxs-lookup"><span data-stu-id="5167d-128">Enter the project name **`ExpenseIt`** and then select **Create**.</span></span>

      ![Okno dialogowe Konfigurowanie nowego projektu](./media/walkthrough-my-first-wpf-desktop-application/configure-new-project-dialog.png)

      <span data-ttu-id="5167d-130">Program Visual Studio tworzy projekt i otwiera projektanta dla domyślnego okna aplikacji o nazwie **MainWindow. XAML**.</span><span class="sxs-lookup"><span data-stu-id="5167d-130">Visual Studio creates the project and opens the designer for the default application window named **MainWindow.xaml**.</span></span>

2. <span data-ttu-id="5167d-131">Otwórz *aplikację Application. XAML* (Visual Basic) lub *App. XAML* (C#).</span><span class="sxs-lookup"><span data-stu-id="5167d-131">Open *Application.xaml* (Visual Basic) or *App.xaml* (C#).</span></span>

    <span data-ttu-id="5167d-132">Ten plik XAML definiuje aplikację WPF i wszystkie zasoby aplikacji.</span><span class="sxs-lookup"><span data-stu-id="5167d-132">This XAML file defines a WPF application and any application resources.</span></span> <span data-ttu-id="5167d-133">Ten plik jest również używany do określenia interfejsu użytkownika (w tym przypadku *MainWindow. XAML*), który jest automatycznie wyświetlany podczas uruchamiania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="5167d-133">You also use this file to specify the UI, in this case *MainWindow.xaml*, that automatically shows when the application starts.</span></span>

    <span data-ttu-id="5167d-134">KOD XAML powinien wyglądać następująco w Visual Basic:</span><span class="sxs-lookup"><span data-stu-id="5167d-134">Your XAML should look like the following in Visual Basic:</span></span>

    [!code-xaml[ExpenseIt#1_A](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/Application.xaml#1_a)]

    <span data-ttu-id="5167d-135">I podobne do następujących w C#programie:</span><span class="sxs-lookup"><span data-stu-id="5167d-135">And like the following in C#:</span></span>

    [!code-xaml[ExpenseIt#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/App.xaml#1)]

3. <span data-ttu-id="5167d-136">Otwórz *MainWindow. XAML*.</span><span class="sxs-lookup"><span data-stu-id="5167d-136">Open *MainWindow.xaml*.</span></span>

    <span data-ttu-id="5167d-137">Ten plik XAML jest głównym oknem aplikacji i wyświetla zawartość utworzoną na stronach.</span><span class="sxs-lookup"><span data-stu-id="5167d-137">This XAML file is the main window of your application and displays content created in pages.</span></span> <span data-ttu-id="5167d-138"><xref:System.Windows.Window> Klasa definiuje właściwości okna, takie jak tytuł, rozmiar lub ikona, i obsługuje zdarzenia, takie jak zamykanie lub ukrywanie.</span><span class="sxs-lookup"><span data-stu-id="5167d-138">The <xref:System.Windows.Window> class defines the properties of a window, such as its title, size, or icon, and handles events, such as closing or hiding.</span></span>

4. <span data-ttu-id="5167d-139"><xref:System.Windows.Window> Zmień element<xref:System.Windows.Navigation.NavigationWindow>na, jak pokazano na poniższym kodzie XAML:</span><span class="sxs-lookup"><span data-stu-id="5167d-139">Change the <xref:System.Windows.Window> element to a <xref:System.Windows.Navigation.NavigationWindow>, as shown in the following XAML:</span></span>

   ```xaml
   <NavigationWindow x:Class="ExpenseIt.MainWindow"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        ...
   </NavigationWindow>
   ```

   <span data-ttu-id="5167d-140">Ta aplikacja nawiguje do innej zawartości w zależności od danych wprowadzonych przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="5167d-140">This app navigates to different content depending on the user input.</span></span> <span data-ttu-id="5167d-141">Jest to dlatego, że <xref:System.Windows.Window> główny należy zmienić <xref:System.Windows.Navigation.NavigationWindow>na.</span><span class="sxs-lookup"><span data-stu-id="5167d-141">This is why the main <xref:System.Windows.Window> needs to be changed to a <xref:System.Windows.Navigation.NavigationWindow>.</span></span> <span data-ttu-id="5167d-142"><xref:System.Windows.Navigation.NavigationWindow>dziedziczy wszystkie właściwości <xref:System.Windows.Window>.</span><span class="sxs-lookup"><span data-stu-id="5167d-142"><xref:System.Windows.Navigation.NavigationWindow> inherits all the properties of <xref:System.Windows.Window>.</span></span> <span data-ttu-id="5167d-143">Element w pliku XAML tworzy wystąpienie <xref:System.Windows.Navigation.NavigationWindow> klasy. <xref:System.Windows.Navigation.NavigationWindow></span><span class="sxs-lookup"><span data-stu-id="5167d-143">The <xref:System.Windows.Navigation.NavigationWindow> element in the XAML file creates an instance of the <xref:System.Windows.Navigation.NavigationWindow> class.</span></span> <span data-ttu-id="5167d-144">Aby uzyskać więcej informacji, zobacz [Omówienie nawigacji](../app-development/navigation-overview.md).</span><span class="sxs-lookup"><span data-stu-id="5167d-144">For more information, see [Navigation overview](../app-development/navigation-overview.md).</span></span>

5. <span data-ttu-id="5167d-145">Usuń elementy z między <xref:System.Windows.Navigation.NavigationWindow>tagami. <xref:System.Windows.Controls.Grid></span><span class="sxs-lookup"><span data-stu-id="5167d-145">Remove the <xref:System.Windows.Controls.Grid> elements from between the <xref:System.Windows.Navigation.NavigationWindow> tags.</span></span>

6. <span data-ttu-id="5167d-146">Zmień następujące właściwości w kodzie XAML dla <xref:System.Windows.Navigation.NavigationWindow> elementu:</span><span class="sxs-lookup"><span data-stu-id="5167d-146">Change the following properties in the XAML code for the <xref:System.Windows.Navigation.NavigationWindow> element:</span></span>

    - <span data-ttu-id="5167d-147">Ustaw właściwość na "`ExpenseIt`". <xref:System.Windows.Window.Title%2A></span><span class="sxs-lookup"><span data-stu-id="5167d-147">Set the <xref:System.Windows.Window.Title%2A> property to "`ExpenseIt`".</span></span>

    - <span data-ttu-id="5167d-148"><xref:System.Windows.FrameworkElement.Height%2A> Ustaw właściwość na 350 pikseli.</span><span class="sxs-lookup"><span data-stu-id="5167d-148">Set the <xref:System.Windows.FrameworkElement.Height%2A> property to 350 pixels.</span></span>

    - <span data-ttu-id="5167d-149"><xref:System.Windows.FrameworkElement.Width%2A> Ustaw właściwość na 500 pikseli.</span><span class="sxs-lookup"><span data-stu-id="5167d-149">Set the <xref:System.Windows.FrameworkElement.Width%2A> property to 500 pixels.</span></span>

    <span data-ttu-id="5167d-150">KOD XAML powinien wyglądać podobnie do poniższego Visual Basic:</span><span class="sxs-lookup"><span data-stu-id="5167d-150">Your XAML should look like the following for Visual Basic:</span></span>

    [!code-xaml[ExpenseIt#2_A](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt/MainWindow.xaml#2_a)]

    <span data-ttu-id="5167d-151">I podobne do C#następujących:</span><span class="sxs-lookup"><span data-stu-id="5167d-151">And like the following for C#:</span></span>

    [!code-xaml[ExpenseIt#2](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/MainWindow.xaml#2)]

7. <span data-ttu-id="5167d-152">Otwórz *MainWindow. XAML. vb* lub *MainWindow.XAML.cs*.</span><span class="sxs-lookup"><span data-stu-id="5167d-152">Open *MainWindow.xaml.vb* or *MainWindow.xaml.cs*.</span></span>

    <span data-ttu-id="5167d-153">Ten plik jest plikiem związanym z kodem, który zawiera kod służący do obsługi zdarzeń zadeklarowanych w *MainWindow. XAML*.</span><span class="sxs-lookup"><span data-stu-id="5167d-153">This file is a code-behind file that contains code to handle the events declared in *MainWindow.xaml*.</span></span> <span data-ttu-id="5167d-154">Ten plik zawiera klasę częściową dla okna zdefiniowanego w języku XAML.</span><span class="sxs-lookup"><span data-stu-id="5167d-154">This file contains a partial class for the window defined in XAML.</span></span>

8. <span data-ttu-id="5167d-155">Jeśli używasz programu C#, Zmień `MainWindow` klasę, aby dziedziczyć z <xref:System.Windows.Navigation.NavigationWindow>.</span><span class="sxs-lookup"><span data-stu-id="5167d-155">If you're using C#, change the `MainWindow` class to derive from <xref:System.Windows.Navigation.NavigationWindow>.</span></span> <span data-ttu-id="5167d-156">(W Visual Basic dzieje się to automatycznie po zmianie okna w języku XAML). C# Kod powinien teraz wyglądać następująco:</span><span class="sxs-lookup"><span data-stu-id="5167d-156">(In Visual Basic, this happens automatically when you change the window in XAML.) Your C# code should now look like this:</span></span>

   [!code-csharp[ExpenseIt#3](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/MainWindow.xaml.cs?highlight=21)]

## <a name="add-files-to-the-application"></a><span data-ttu-id="5167d-157">Dodawanie plików do aplikacji</span><span class="sxs-lookup"><span data-stu-id="5167d-157">Add files to the application</span></span>

<span data-ttu-id="5167d-158">W tej sekcji dodasz dwie strony i obraz do aplikacji.</span><span class="sxs-lookup"><span data-stu-id="5167d-158">In this section, you'll add two pages and an image to the application.</span></span>

1. <span data-ttu-id="5167d-159">Dodaj nową stronę do projektu i nadaj jej *`ExpenseItHome.xaml`* nazwę:</span><span class="sxs-lookup"><span data-stu-id="5167d-159">Add a new page to the project, and name it *`ExpenseItHome.xaml`*:</span></span>

   1. <span data-ttu-id="5167d-160">W **Eksplorator rozwiązań**kliknij **`ExpenseIt`** prawym przyciskiem myszy węzeł projektu i wybierz polecenie **Dodaj** > **stronę**.</span><span class="sxs-lookup"><span data-stu-id="5167d-160">In **Solution Explorer**, right-click on the **`ExpenseIt`** project node and choose **Add** > **Page**.</span></span>

   1. <span data-ttu-id="5167d-161">W oknie dialogowym **Dodaj nowy element** szablon **Strona (WPF)** jest już zaznaczony.</span><span class="sxs-lookup"><span data-stu-id="5167d-161">In the **Add New Item** dialog, the **Page (WPF)** template is already selected.</span></span> <span data-ttu-id="5167d-162">Wprowadź nazwę **`ExpenseItHome`** , a następnie wybierz pozycję **Dodaj**.</span><span class="sxs-lookup"><span data-stu-id="5167d-162">Enter the name **`ExpenseItHome`**, and then select **Add**.</span></span>

    <span data-ttu-id="5167d-163">Ta strona to pierwsza strona wyświetlana podczas uruchamiania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="5167d-163">This page is the first page that's displayed when the application is launched.</span></span> <span data-ttu-id="5167d-164">Zostanie wyświetlona lista osób, spośród których można wybrać, aby wyświetlić raport wydatków dla programu.</span><span class="sxs-lookup"><span data-stu-id="5167d-164">It will show a list of people to select from, to show an expense report for.</span></span>

1. <span data-ttu-id="5167d-165">Otwórz *`ExpenseItHome.xaml`* .</span><span class="sxs-lookup"><span data-stu-id="5167d-165">Open *`ExpenseItHome.xaml`*.</span></span>

1. <span data-ttu-id="5167d-166">Ustaw wartość`ExpenseIt - Home`na "". <xref:System.Windows.Controls.Page.Title%2A></span><span class="sxs-lookup"><span data-stu-id="5167d-166">Set the <xref:System.Windows.Controls.Page.Title%2A> to "`ExpenseIt - Home`".</span></span>

1. <span data-ttu-id="5167d-167">Ustaw do 350 pikseli `DesignWidth` i do 500 pikseli. `DesignHeight`</span><span class="sxs-lookup"><span data-stu-id="5167d-167">Set the `DesignHeight` to 350 pixels and the `DesignWidth` to 500 pixels.</span></span>

    <span data-ttu-id="5167d-168">KOD XAML jest teraz wyświetlany w następujący sposób dla Visual Basic:</span><span class="sxs-lookup"><span data-stu-id="5167d-168">The XAML now appears as follows for Visual Basic:</span></span>

    [!code-xaml[ExpenseIt#6_A](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseItHome.xaml#6_a)]

    <span data-ttu-id="5167d-169">I podobne do C#następujących:</span><span class="sxs-lookup"><span data-stu-id="5167d-169">And like the following for C#:</span></span>

    [!code-xaml[ExpenseIt#6](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt2/ExpenseItHome.xaml#6)]

1. <span data-ttu-id="5167d-170">Otwórz *MainWindow. XAML*.</span><span class="sxs-lookup"><span data-stu-id="5167d-170">Open *MainWindow.xaml*.</span></span>

1. <span data-ttu-id="5167d-171">Dodaj właściwość do elementu i ustaw ją na "`ExpenseItHome.xaml`". <xref:System.Windows.Navigation.NavigationWindow> <xref:System.Windows.Navigation.NavigationWindow.Source%2A></span><span class="sxs-lookup"><span data-stu-id="5167d-171">Add a <xref:System.Windows.Navigation.NavigationWindow.Source%2A> property to the <xref:System.Windows.Navigation.NavigationWindow> element and set it to "`ExpenseItHome.xaml`".</span></span>

    <span data-ttu-id="5167d-172">To ustawienie *`ExpenseItHome.xaml`* jest pierwszą stroną otwartą podczas uruchamiania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="5167d-172">This sets *`ExpenseItHome.xaml`* to be the first page opened when the application starts.</span></span> 

    <span data-ttu-id="5167d-173">Przykładowy kod XAML w Visual Basic:</span><span class="sxs-lookup"><span data-stu-id="5167d-173">Example XAML in Visual Basic:</span></span>

    [!code-xaml[ExpenseIt#7_A](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/MainWindow.xaml#7_a)]

    <span data-ttu-id="5167d-174">W języku C#:</span><span class="sxs-lookup"><span data-stu-id="5167d-174">And in C#:</span></span>

    [!code-xaml[ExpenseIt#7](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt2/MainWindow.xaml#7)]

   > [!TIP]
   > <span data-ttu-id="5167d-175">Możesz również ustawić właściwość **Source** w kategorii **różne** okna **Właściwości** .</span><span class="sxs-lookup"><span data-stu-id="5167d-175">You can also set the **Source** property in the **Miscellaneous** category of the **Properties** window.</span></span>
   >
   > ![Właściwość Source w okno Właściwości](./media/properties-source.png)

1. <span data-ttu-id="5167d-177">Dodaj kolejną nową stronę WPF do projektu i nadaj jej nazwę *ExpenseReportPage. XAML*::</span><span class="sxs-lookup"><span data-stu-id="5167d-177">Add another new WPF page to the project, and name it *ExpenseReportPage.xaml*::</span></span>

   1. <span data-ttu-id="5167d-178">W **Eksplorator rozwiązań**kliknij **`ExpenseIt`** prawym przyciskiem myszy węzeł projektu i wybierz polecenie **Dodaj** > **stronę**.</span><span class="sxs-lookup"><span data-stu-id="5167d-178">In **Solution Explorer**, right-click on the **`ExpenseIt`** project node and choose **Add** > **Page**.</span></span>

   1. <span data-ttu-id="5167d-179">W oknie dialogowym **Dodaj nowy element** wybierz szablon **Strona (WPF)** .</span><span class="sxs-lookup"><span data-stu-id="5167d-179">In the **Add New Item** dialog, select the **Page (WPF)** template.</span></span> <span data-ttu-id="5167d-180">Wprowadź nazwę **ExpenseReportPage**, a następnie wybierz pozycję **Dodaj**.</span><span class="sxs-lookup"><span data-stu-id="5167d-180">Enter the name **ExpenseReportPage**, and then select **Add**.</span></span>

    <span data-ttu-id="5167d-181">Na tej stronie zostanie wyświetlony raport wydatków dla osoby, która została wybrana na **`ExpenseItHome`** stronie.</span><span class="sxs-lookup"><span data-stu-id="5167d-181">This page will show the expense report for the person that is selected on the **`ExpenseItHome`** page.</span></span>

1. <span data-ttu-id="5167d-182">Otwórz *ExpenseReportPage. XAML*.</span><span class="sxs-lookup"><span data-stu-id="5167d-182">Open *ExpenseReportPage.xaml*.</span></span>

1. <span data-ttu-id="5167d-183">Ustaw wartość`ExpenseIt - View Expense`na "". <xref:System.Windows.Controls.Page.Title%2A></span><span class="sxs-lookup"><span data-stu-id="5167d-183">Set the <xref:System.Windows.Controls.Page.Title%2A> to "`ExpenseIt - View Expense`".</span></span>

1. <span data-ttu-id="5167d-184">Ustaw do 350 pikseli `DesignWidth` i do 500 pikseli. `DesignHeight`</span><span class="sxs-lookup"><span data-stu-id="5167d-184">Set the `DesignHeight` to 350 pixels and the `DesignWidth` to 500 pixels.</span></span> 

    <span data-ttu-id="5167d-185">*ExpenseReportPage. XAML* wygląda teraz następująco w Visual Basic:</span><span class="sxs-lookup"><span data-stu-id="5167d-185">*ExpenseReportPage.xaml* now looks like the following in Visual Basic:</span></span>

    [!code-xaml[ExpenseIt#4_A](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseReportPage.xaml#4_a)]

    <span data-ttu-id="5167d-186">I podobne do następujących w C#programie:</span><span class="sxs-lookup"><span data-stu-id="5167d-186">And like the following in C#:</span></span>

    [!code-xaml[ExpenseIt#4](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/ExpenseReportPage.xaml#4)]

1. <span data-ttu-id="5167d-187">Otwórz *ExpenseItHome. XAML. vb* oraz *ExpenseReportPage. XAML. vb*lub *ExpenseItHome.XAML.cs* i *ExpenseReportPage.XAML.cs*.</span><span class="sxs-lookup"><span data-stu-id="5167d-187">Open *ExpenseItHome.xaml.vb* and *ExpenseReportPage.xaml.vb*, or *ExpenseItHome.xaml.cs* and *ExpenseReportPage.xaml.cs*.</span></span>

    <span data-ttu-id="5167d-188">Podczas tworzenia nowego pliku stronicowania program Visual Studio automatycznie tworzy swój plik *związany z kodem* .</span><span class="sxs-lookup"><span data-stu-id="5167d-188">When you create a new Page file, Visual Studio automatically creates its *code-behind* file.</span></span> <span data-ttu-id="5167d-189">Te pliki związane z kodem obsługują logikę w celu reagowania na dane wejściowe użytkownika.</span><span class="sxs-lookup"><span data-stu-id="5167d-189">These code-behind files handle the logic for responding to user input.</span></span>

    <span data-ttu-id="5167d-190">Kod powinien wyglądać **`ExpenseItHome`** następująco:</span><span class="sxs-lookup"><span data-stu-id="5167d-190">Your code should look like the following for **`ExpenseItHome`**:</span></span>

    [!code-csharp[ExpenseIt#2_5](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt2/ExpenseItHome.xaml.cs#2_5)]

    [!code-vb[ExpenseIt#2_5](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseItHome.xaml.vb#2_5)]

    <span data-ttu-id="5167d-191">I tak jak w przypadku **ExpenseReportPage**:</span><span class="sxs-lookup"><span data-stu-id="5167d-191">And like the following for **ExpenseReportPage**:</span></span>

    [!code-csharp[ExpenseIt#5](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/ExpenseReportPage.xaml.cs#5)]

    [!code-vb[ExpenseIt#5](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseReportPage.xaml.vb#5)]

1. <span data-ttu-id="5167d-192">Dodaj obraz o nazwie *znak wodny. png* do projektu.</span><span class="sxs-lookup"><span data-stu-id="5167d-192">Add an image named *watermark.png* to the project.</span></span> <span data-ttu-id="5167d-193">Możesz utworzyć własny obraz, skopiować plik z przykładowego kodu lub pobrać go [tutaj](https://raw.githubusercontent.com/microsoft/WPF-Samples/master/Getting%20Started/WalkthroughFirstWPFApp/csharp/watermark.png).</span><span class="sxs-lookup"><span data-stu-id="5167d-193">You can create your own image, copy the file from the sample code, or get it [here](https://raw.githubusercontent.com/microsoft/WPF-Samples/master/Getting%20Started/WalkthroughFirstWPFApp/csharp/watermark.png).</span></span>

    1. <span data-ttu-id="5167d-194">Kliknij prawym przyciskiem myszy węzeł projektu i wybierz polecenie **Dodaj** > **istniejący element**lub naciśnij klawisze **SHIFT**+**Alt**+**A**.</span><span class="sxs-lookup"><span data-stu-id="5167d-194">Right-click on the project node and select **Add** > **Existing Item**, or press **Shift**+**Alt**+**A**.</span></span>

    2. <span data-ttu-id="5167d-195">W oknie dialogowym **Dodaj istniejący element** Ustaw filtr pliku na **wszystkie pliki** lub **pliki obrazów**, przejdź do pliku obrazu, którego chcesz użyć, a następnie wybierz pozycję **Dodaj**.</span><span class="sxs-lookup"><span data-stu-id="5167d-195">In the **Add Existing Item** dialog, set the file filter to either **All Files** or **Image Files**, browse to the image file you want to use, and then select **Add**.</span></span>

## <a name="build-and-run-the-application"></a><span data-ttu-id="5167d-196">Kompilowanie i uruchamianie aplikacji</span><span class="sxs-lookup"><span data-stu-id="5167d-196">Build and run the application</span></span>

1. <span data-ttu-id="5167d-197">Aby skompilować i uruchomić aplikację, naciśnij klawisz **F5** lub wybierz pozycję **Rozpocznij debugowanie** z menu **debugowanie** .</span><span class="sxs-lookup"><span data-stu-id="5167d-197">To build and run the application, press **F5** or select **Start Debugging** from the **Debug** menu.</span></span>

    <span data-ttu-id="5167d-198">Na poniższej ilustracji przedstawiono aplikację z <xref:System.Windows.Navigation.NavigationWindow> przyciskami:</span><span class="sxs-lookup"><span data-stu-id="5167d-198">The following illustration shows the application with the <xref:System.Windows.Navigation.NavigationWindow> buttons:</span></span>

    ![Po skompilowaniu i uruchomieniu aplikacji.](./media/walkthrough-my-first-wpf-desktop-application/build-run-application.png)

2. <span data-ttu-id="5167d-200">Zamknij aplikację, aby powrócić do programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="5167d-200">Close the application to return to Visual Studio.</span></span>

## <a name="create-the-layout"></a><span data-ttu-id="5167d-201">Tworzenie układu</span><span class="sxs-lookup"><span data-stu-id="5167d-201">Create the layout</span></span>

<span data-ttu-id="5167d-202">Układ zapewnia uporządkowany sposób umieszczania elementów interfejsu użytkownika, a także zarządza rozmiarem i położeniem tych elementów w przypadku zmiany rozmiaru interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="5167d-202">Layout provides an ordered way to place UI elements, and also manages the size and position of those elements when a UI is resized.</span></span> <span data-ttu-id="5167d-203">Zazwyczaj tworzysz układ z jedną z następujących kontrolek układu:</span><span class="sxs-lookup"><span data-stu-id="5167d-203">You typically create a layout with one of the following layout controls:</span></span>

- <span data-ttu-id="5167d-204"><xref:System.Windows.Controls.Canvas>-Definiuje obszar, w którym można jawnie pozycjonować elementy podrzędne za pomocą współrzędnych względnych dla obszaru kanwy.</span><span class="sxs-lookup"><span data-stu-id="5167d-204"><xref:System.Windows.Controls.Canvas> - Defines an area within which you can explicitly position child elements by using coordinates that are relative to the Canvas area.</span></span>
- <span data-ttu-id="5167d-205"><xref:System.Windows.Controls.DockPanel>-Definiuje obszar, w którym można rozmieścić elementy podrzędne w poziomie lub w pionie względem siebie.</span><span class="sxs-lookup"><span data-stu-id="5167d-205"><xref:System.Windows.Controls.DockPanel> - Defines an area where you can arrange child elements either horizontally or vertically, relative to each other.</span></span>
- <span data-ttu-id="5167d-206"><xref:System.Windows.Controls.Grid>-Definiuje elastyczny obszar siatki składający się z kolumn i wierszy.</span><span class="sxs-lookup"><span data-stu-id="5167d-206"><xref:System.Windows.Controls.Grid> - Defines a flexible grid area that consists of columns and rows.</span></span>
- <span data-ttu-id="5167d-207"><xref:System.Windows.Controls.StackPanel>— Rozmieszcza elementy podrzędne w pojedynczym wierszu, który może być zorientowany w poziomie lub w pionie.</span><span class="sxs-lookup"><span data-stu-id="5167d-207"><xref:System.Windows.Controls.StackPanel> - Arranges child elements into a single line that can be oriented horizontally or vertically.</span></span>
- <span data-ttu-id="5167d-208"><xref:System.Windows.Controls.VirtualizingStackPanel>-Rozmieszcza i wirtualizacji zawartość w jednym wierszu, który ma orientację poziomą lub pionową.</span><span class="sxs-lookup"><span data-stu-id="5167d-208"><xref:System.Windows.Controls.VirtualizingStackPanel> - Arranges and virtualizes content on a single line that is oriented either horizontally or vertically.</span></span>
- <span data-ttu-id="5167d-209"><xref:System.Windows.Controls.WrapPanel>-Umieszcza elementy podrzędne w kolejności sekwencyjnej od lewej do prawej, dzieląc zawartość do następnego wiersza na krawędzi pola zawierającego.</span><span class="sxs-lookup"><span data-stu-id="5167d-209"><xref:System.Windows.Controls.WrapPanel> - Positions child elements in sequential position from left to right, breaking content to the next line at the edge of the containing box.</span></span> <span data-ttu-id="5167d-210">Kolejne porządkowanie odbywa się sekwencyjnie od góry do dołu lub od prawej do lewej, w zależności od wartości właściwości Orientation.</span><span class="sxs-lookup"><span data-stu-id="5167d-210">Subsequent ordering happens sequentially from top to bottom or from right to left, depending on the value of the Orientation property.</span></span>

<span data-ttu-id="5167d-211">Każda z tych kontrolek układu obsługuje określony typ układu dla jego elementów podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="5167d-211">Each of these layout controls supports a particular type of layout for its child elements.</span></span> <span data-ttu-id="5167d-212">`ExpenseIt`rozmiary stron mogą być zmieniane, a każda Strona zawiera elementy ułożone w poziomie i w pionie wraz z innymi elementami.</span><span class="sxs-lookup"><span data-stu-id="5167d-212">`ExpenseIt` pages can be resized, and each page has elements that are arranged horizontally and vertically alongside other elements.</span></span> <span data-ttu-id="5167d-213">W tym przykładzie <xref:System.Windows.Controls.Grid> jest używany jako element układu dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="5167d-213">In this example, the <xref:System.Windows.Controls.Grid> is used as  layout element for the application.</span></span>

> [!TIP]
> <span data-ttu-id="5167d-214">Aby uzyskać więcej informacji <xref:System.Windows.Controls.Panel> o elementach, zobacz [Omówienie paneli](../controls/panels-overview.md).</span><span class="sxs-lookup"><span data-stu-id="5167d-214">For more information about <xref:System.Windows.Controls.Panel> elements, see [Panels overview](../controls/panels-overview.md).</span></span> <span data-ttu-id="5167d-215">Aby uzyskać więcej informacji na temat układu, zobacz [Układ](../advanced/layout.md).</span><span class="sxs-lookup"><span data-stu-id="5167d-215">For more information about layout, see [Layout](../advanced/layout.md).</span></span>

<span data-ttu-id="5167d-216">W tej sekcji utworzysz jednokolumnową tabelę z trzema wierszami i marginesem 10 pikseli, dodając definicje kolumn i wierszy do <xref:System.Windows.Controls.Grid> elementu w. *`ExpenseItHome.xaml`*</span><span class="sxs-lookup"><span data-stu-id="5167d-216">In this section, you create a single-column table with three rows and a 10-pixel margin by adding column and row definitions to the <xref:System.Windows.Controls.Grid> in *`ExpenseItHome.xaml`*.</span></span>

1. <span data-ttu-id="5167d-217">W *`ExpenseItHome.xaml`* , <xref:System.Windows.Controls.Grid> ustaw właściwość elementu na wartość "10, 0, 10, 10", która odnosi się do lewego, górnego, prawego i dolnego marginesu: <xref:System.Windows.FrameworkElement.Margin%2A></span><span class="sxs-lookup"><span data-stu-id="5167d-217">In *`ExpenseItHome.xaml`*, set the <xref:System.Windows.FrameworkElement.Margin%2A> property on the <xref:System.Windows.Controls.Grid> element to "10,0,10,10", which corresponds to left, top, right and bottom margins:</span></span>

   ```xaml
   <Grid Margin="10,0,10,10">
   ```

   > [!TIP]
   > <span data-ttu-id="5167d-218">Możesz również ustawić wartości **marginesu** w oknie **Właściwości** , w obszarze Kategoria **układu** :</span><span class="sxs-lookup"><span data-stu-id="5167d-218">You can also set the **Margin** values in the **Properties** window, under the **Layout** category:</span></span>
   >
   > ![Wartości marginesów w okno Właściwości](./media/properties-margin.png)

2. <span data-ttu-id="5167d-220">Dodaj następujący kod XAML między tagami <xref:System.Windows.Controls.Grid> , aby utworzyć definicje wierszy i kolumn:</span><span class="sxs-lookup"><span data-stu-id="5167d-220">Add the following XAML between the <xref:System.Windows.Controls.Grid> tags to create the row and column definitions:</span></span>

    [!code-xaml[ExpenseIt#8](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt3/ExpenseItHome.xaml#8)]

    <span data-ttu-id="5167d-221">Dwa wiersze są ustawione na <xref:System.Windows.GridLength.Auto%2A>, co oznacza, że rozmiar wierszy jest określany na podstawie zawartości w wierszach. <xref:System.Windows.Controls.RowDefinition.Height%2A></span><span class="sxs-lookup"><span data-stu-id="5167d-221">The <xref:System.Windows.Controls.RowDefinition.Height%2A> of two rows is set to <xref:System.Windows.GridLength.Auto%2A>, which means that the rows are sized based on the content in the rows.</span></span> <span data-ttu-id="5167d-222">Wartość domyślna <xref:System.Windows.Controls.RowDefinition.Height%2A> to <xref:System.Windows.GridUnitType.Star> rozmiar, co oznacza, że wysokość wiersza jest ważoną ilością dostępnego miejsca.</span><span class="sxs-lookup"><span data-stu-id="5167d-222">The default <xref:System.Windows.Controls.RowDefinition.Height%2A> is <xref:System.Windows.GridUnitType.Star> sizing, which means that the row height is a weighted proportion of the available space.</span></span> <span data-ttu-id="5167d-223">Na przykład jeśli dwa wiersze mają wartość <xref:System.Windows.Controls.RowDefinition.Height%2A> "\*", każdy z nich ma wysokość połowę dostępnego miejsca.</span><span class="sxs-lookup"><span data-stu-id="5167d-223">For example if two rows each have a <xref:System.Windows.Controls.RowDefinition.Height%2A> of "\*", they each have a height that is half of the available space.</span></span>

    <span data-ttu-id="5167d-224"><xref:System.Windows.Controls.Grid> Powinien teraz zawierać następujący kod XAML:</span><span class="sxs-lookup"><span data-stu-id="5167d-224">Your <xref:System.Windows.Controls.Grid> should now contain the following XAML:</span></span>

    [!code-xaml[ExpenseIt#9](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt3/ExpenseItHome.xaml#9)]

## <a name="add-controls"></a><span data-ttu-id="5167d-225">Dodawanie kontrolek</span><span class="sxs-lookup"><span data-stu-id="5167d-225">Add controls</span></span>

<span data-ttu-id="5167d-226">W tej sekcji opisano aktualizowanie interfejsu użytkownika strony głównej w celu wyświetlenia listy osób, w których można wybrać jedną osobę, aby wyświetlić raport z wydatków.</span><span class="sxs-lookup"><span data-stu-id="5167d-226">In this section, you'll update the home page UI to show a list of people, where you select one person to display their expense report.</span></span> <span data-ttu-id="5167d-227">Formanty to obiekty UI, które umożliwiają użytkownikom współpracującie z Twoją aplikacją.</span><span class="sxs-lookup"><span data-stu-id="5167d-227">Controls are UI objects that allow users to interact with your application.</span></span> <span data-ttu-id="5167d-228">Aby uzyskać więcej informacji, zobacz [Controls](../controls/index.md).</span><span class="sxs-lookup"><span data-stu-id="5167d-228">For more information, see [Controls](../controls/index.md).</span></span>

<span data-ttu-id="5167d-229">Aby utworzyć ten interfejs użytkownika, Dodaj następujące elementy *`ExpenseItHome.xaml`* :</span><span class="sxs-lookup"><span data-stu-id="5167d-229">To create this UI, you'll add the following elements to *`ExpenseItHome.xaml`*:</span></span>

- <span data-ttu-id="5167d-230">A <xref:System.Windows.Controls.ListBox> (dla listy osób).</span><span class="sxs-lookup"><span data-stu-id="5167d-230">A <xref:System.Windows.Controls.ListBox> (for the list of people).</span></span>
- <span data-ttu-id="5167d-231">A <xref:System.Windows.Controls.Label> (dla nagłówka listy).</span><span class="sxs-lookup"><span data-stu-id="5167d-231">A <xref:System.Windows.Controls.Label> (for the list header).</span></span>
- <span data-ttu-id="5167d-232">A <xref:System.Windows.Controls.Button> (kliknij, aby wyświetlić raport wydatków dla osoby, która została wybrana na liście).</span><span class="sxs-lookup"><span data-stu-id="5167d-232">A <xref:System.Windows.Controls.Button> (to click to view the expense report for the person that is selected in the list).</span></span>

<span data-ttu-id="5167d-233">Każda kontrolka jest umieszczana w wierszu <xref:System.Windows.Controls.Grid> obiektu przez <xref:System.Windows.Controls.Grid.Row%2A?displayProperty=nameWithType> ustawienie dołączonej właściwości.</span><span class="sxs-lookup"><span data-stu-id="5167d-233">Each control is placed in a row of the <xref:System.Windows.Controls.Grid> by setting the <xref:System.Windows.Controls.Grid.Row%2A?displayProperty=nameWithType> attached property.</span></span> <span data-ttu-id="5167d-234">Aby uzyskać więcej informacji o dołączanych właściwościach, zobacz temat [dołączone właściwości przegląd](../advanced/attached-properties-overview.md).</span><span class="sxs-lookup"><span data-stu-id="5167d-234">For more information about attached properties, see [Attached Properties Overview](../advanced/attached-properties-overview.md).</span></span>

1. <span data-ttu-id="5167d-235">W *`ExpenseItHome.xaml`* programie Dodaj następujący kod XAML gdzieś <xref:System.Windows.Controls.Grid> między tagami:</span><span class="sxs-lookup"><span data-stu-id="5167d-235">In *`ExpenseItHome.xaml`*, add the following XAML somewhere between the <xref:System.Windows.Controls.Grid> tags:</span></span>

   [!code-xaml[ExpenseIt#10](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt4/ExpenseItHome.xaml#10)]

   > [!TIP]
   > <span data-ttu-id="5167d-236">Możesz również utworzyć kontrolki, przeciągając je z okna **przybornika** do okna projektowania, a następnie ustawiając ich właściwości w oknie **Właściwości** .</span><span class="sxs-lookup"><span data-stu-id="5167d-236">You can also create the controls by dragging them from the **Toolbox** window onto the design window, and then setting their properties in the **Properties** window.</span></span>

2. <span data-ttu-id="5167d-237">Skompiluj i uruchom aplikację.</span><span class="sxs-lookup"><span data-stu-id="5167d-237">Build and run the application.</span></span>

    <span data-ttu-id="5167d-238">Na poniższej ilustracji przedstawiono utworzone przez Ciebie formanty:</span><span class="sxs-lookup"><span data-stu-id="5167d-238">The following illustration shows the controls you created:</span></span>

![Przykładowy zrzut ekranu ExpenseIt z listą nazw](./media/walkthrough-my-first-wpf-desktop-application/add-application-controls.png)

## <a name="add-an-image-and-a-title"></a><span data-ttu-id="5167d-240">Dodawanie obrazu i tytułu</span><span class="sxs-lookup"><span data-stu-id="5167d-240">Add an image and a title</span></span>

<span data-ttu-id="5167d-241">W tej sekcji zaktualizujesz interfejs użytkownika strony głównej za pomocą obrazu i tytułu strony.</span><span class="sxs-lookup"><span data-stu-id="5167d-241">In this section, you'll update the home page UI with an image and a page title.</span></span>

1. <span data-ttu-id="5167d-242">W *`ExpenseItHome.xaml`* programie Dodaj kolejną kolumnę <xref:System.Windows.Controls.Grid.ColumnDefinitions%2A> z ustaloną <xref:System.Windows.Controls.ColumnDefinition.Width%2A> 230 pikseli:</span><span class="sxs-lookup"><span data-stu-id="5167d-242">In *`ExpenseItHome.xaml`*, add another column to the <xref:System.Windows.Controls.Grid.ColumnDefinitions%2A> with a fixed <xref:System.Windows.Controls.ColumnDefinition.Width%2A> of 230 pixels:</span></span>

    [!code-xaml[ExpenseIt#11](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseItHome.xaml?highlight=52-55)]

2. <span data-ttu-id="5167d-243">Dodaj kolejny wiersz do <xref:System.Windows.Controls.Grid.RowDefinitions%2A>, aby uzyskać łącznie cztery wiersze:</span><span class="sxs-lookup"><span data-stu-id="5167d-243">Add another row to the <xref:System.Windows.Controls.Grid.RowDefinitions%2A>, for a total of four rows:</span></span>

    [!code-xaml[ExpenseIt#11b](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseItHome.xaml?highlight=57-62)]

3. <span data-ttu-id="5167d-244">Przenieś kontrolki do drugiej kolumny, ustawiając <xref:System.Windows.Controls.Grid.Column%2A?displayProperty=nameWithType> właściwość na 1 w każdej z trzech kontrolek (obramowanie, ListBox i Button).</span><span class="sxs-lookup"><span data-stu-id="5167d-244">Move the controls to the second column by setting the <xref:System.Windows.Controls.Grid.Column%2A?displayProperty=nameWithType> property to 1 in each of the three controls (Border, ListBox, and Button).</span></span>

4. <span data-ttu-id="5167d-245">Przenieś każdy formant w dół, zwiększając jego <xref:System.Windows.Controls.Grid.Row%2A?displayProperty=nameWithType> wartość o 1 dla każdej z trzech kontrolek (obramowanie, ListBox i Button) oraz dla elementu Border.</span><span class="sxs-lookup"><span data-stu-id="5167d-245">Move each control down a row by incrementing its <xref:System.Windows.Controls.Grid.Row%2A?displayProperty=nameWithType> value by 1 for each of the three controls (Border, ListBox, and Button) and for the Border element.</span></span>

   <span data-ttu-id="5167d-246">KOD XAML dla trzech kontrolek wygląda teraz następująco:</span><span class="sxs-lookup"><span data-stu-id="5167d-246">The XAML for the three controls now looks like the following:</span></span>

    [!code-xaml[ExpenseIt#12](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#12)]

5. <span data-ttu-id="5167d-247">Ustaw właściwość na plik obrazu *znaku wodnego. png* , dodając następujący `<Grid>` kod XAML gdziekolwiek między tagami i `</Grid>`: <xref:System.Windows.Controls.Panel.Background%2A?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="5167d-247">Set the <xref:System.Windows.Controls.Panel.Background%2A?displayProperty=nameWithType> property to the *watermark.png* image file, by adding the following XAML anywhere between the `<Grid>` and `</Grid>` tags:</span></span>

    [!code-xaml[ExpenseIt#14](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#14)]

6. <span data-ttu-id="5167d-248"><xref:System.Windows.Controls.Border> Przed elementem <xref:System.Windows.Controls.Label> Dodaj element z zawartością "Wyświetl raport wydatków".</span><span class="sxs-lookup"><span data-stu-id="5167d-248">Before the <xref:System.Windows.Controls.Border> element, add a <xref:System.Windows.Controls.Label> with the content "View Expense Report".</span></span> <span data-ttu-id="5167d-249">Ta etykieta jest tytułem strony.</span><span class="sxs-lookup"><span data-stu-id="5167d-249">This label is the title of the page.</span></span>

    [!code-xaml[ExpenseIt#13](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#13)]

7. <span data-ttu-id="5167d-250">Skompiluj i uruchom aplikację.</span><span class="sxs-lookup"><span data-stu-id="5167d-250">Build and run the application.</span></span>

<span data-ttu-id="5167d-251">Na poniższej ilustracji przedstawiono wyniki, które właśnie Dodano:</span><span class="sxs-lookup"><span data-stu-id="5167d-251">The following illustration shows the results of what you just added:</span></span>

![Przykładowy zrzut ekranu ExpenseIt pokazujący nowe tło obrazu i tytuł strony](./media/walkthrough-my-first-wpf-desktop-application/add-application-image-title.png)

## <a name="add-code-to-handle-events"></a><span data-ttu-id="5167d-253">Dodawanie kodu do obsługi zdarzeń</span><span class="sxs-lookup"><span data-stu-id="5167d-253">Add code to handle events</span></span>

1. <span data-ttu-id="5167d-254">W *`ExpenseItHome.xaml`* programie Dodajdo<xref:System.Windows.Controls.Button> elementu procedurę obsługi zdarzeń.<xref:System.Windows.Controls.Primitives.ButtonBase.Click></span><span class="sxs-lookup"><span data-stu-id="5167d-254">In *`ExpenseItHome.xaml`*, add a <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event handler to the <xref:System.Windows.Controls.Button> element.</span></span> <span data-ttu-id="5167d-255">Aby uzyskać więcej informacji, zobacz [jak: Utwórz prostą procedurę obsługi](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/bb675300(v=vs.100))zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="5167d-255">For more information, see [How to: Create a simple event handler](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/bb675300(v=vs.100)).</span></span>

    [!code-xaml[ExpenseIt#15](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt6/ExpenseItHome.xaml#15)]

2. <span data-ttu-id="5167d-256">Otwórz *`ExpenseItHome.xaml.vb`* lub *`ExpenseItHome.xaml.cs`* .</span><span class="sxs-lookup"><span data-stu-id="5167d-256">Open *`ExpenseItHome.xaml.vb`* or *`ExpenseItHome.xaml.cs`*.</span></span>

3. <span data-ttu-id="5167d-257">Dodaj następujący kod do klasy, `ExpenseItHome` aby dodać przycisk procedury obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="5167d-257">Add the following code to the `ExpenseItHome` class to add a button click event handler.</span></span> <span data-ttu-id="5167d-258">Procedura obsługi zdarzeń otwiera stronę **ExpenseReportPage** .</span><span class="sxs-lookup"><span data-stu-id="5167d-258">The event handler opens the **ExpenseReportPage** page.</span></span>

    [!code-csharp[ExpenseIt#16](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt6/ExpenseItHome.xaml.cs#16)]
    [!code-vb[ExpenseIt#16](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt6/ExpenseItHome.xaml.vb#16)]

## <a name="create-the-ui-for-expensereportpage"></a><span data-ttu-id="5167d-259">Tworzenie interfejsu użytkownika dla ExpenseReportPage</span><span class="sxs-lookup"><span data-stu-id="5167d-259">Create the UI for ExpenseReportPage</span></span>

<span data-ttu-id="5167d-260">*ExpenseReportPage. XAML* wyświetla raport wydatków dla osoby, która została wybrana na **`ExpenseItHome`** stronie.</span><span class="sxs-lookup"><span data-stu-id="5167d-260">*ExpenseReportPage.xaml* displays the expense report for the person that's selected on the **`ExpenseItHome`** page.</span></span> <span data-ttu-id="5167d-261">W tej sekcji utworzysz interfejs użytkownika dla **ExpenseReportPage**.</span><span class="sxs-lookup"><span data-stu-id="5167d-261">In this section, you'll create the UI for **ExpenseReportPage**.</span></span> <span data-ttu-id="5167d-262">Możesz również dodać kolory tła i wypełnienia do różnych elementów interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="5167d-262">You'll also add background and fill colors to the various UI elements.</span></span>

1. <span data-ttu-id="5167d-263">Otwórz *ExpenseReportPage. XAML*.</span><span class="sxs-lookup"><span data-stu-id="5167d-263">Open *ExpenseReportPage.xaml*.</span></span>

2. <span data-ttu-id="5167d-264">Dodaj następujący kod XAML między <xref:System.Windows.Controls.Grid> tagami:</span><span class="sxs-lookup"><span data-stu-id="5167d-264">Add the following XAML between the <xref:System.Windows.Controls.Grid> tags:</span></span>

    [!code-xaml[ExpenseIt#17](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt6/ExpenseReportPage.xaml#17)]

    <span data-ttu-id="5167d-265">Ten interfejs użytkownika jest podobny *`ExpenseItHome.xaml`* do, z wyjątkiem tego, że dane raportu <xref:System.Windows.Controls.DataGrid>są wyświetlane w.</span><span class="sxs-lookup"><span data-stu-id="5167d-265">This UI is similar to *`ExpenseItHome.xaml`*, except the report data is displayed in a <xref:System.Windows.Controls.DataGrid>.</span></span>

3. <span data-ttu-id="5167d-266">Skompiluj i uruchom aplikację.</span><span class="sxs-lookup"><span data-stu-id="5167d-266">Build and run the application.</span></span>

4. <span data-ttu-id="5167d-267">Wybierz przycisk **Wyświetl** .</span><span class="sxs-lookup"><span data-stu-id="5167d-267">Select the **View** button.</span></span>

    <span data-ttu-id="5167d-268">Zostanie wyświetlona strona raport o wydatkach.</span><span class="sxs-lookup"><span data-stu-id="5167d-268">The expense report page appears.</span></span> <span data-ttu-id="5167d-269">Zauważ również, że przycisk nawigacji wstecznej jest włączony.</span><span class="sxs-lookup"><span data-stu-id="5167d-269">Also notice that the back navigation button is enabled.</span></span>

<span data-ttu-id="5167d-270">Na poniższej ilustracji przedstawiono elementy interfejsu użytkownika dodane do *ExpenseReportPage. XAML*.</span><span class="sxs-lookup"><span data-stu-id="5167d-270">The following illustration shows the UI elements added to *ExpenseReportPage.xaml*.</span></span>

![Przykładowy zrzut ekranu ExpenseIt przedstawiający interfejs użytkownika, który został właśnie utworzony dla ExpenseReportPage.](./media/walkthrough-my-first-wpf-desktop-application/create-application-ui.png)

## <a name="style-controls"></a><span data-ttu-id="5167d-272">Kontrolki stylu</span><span class="sxs-lookup"><span data-stu-id="5167d-272">Style controls</span></span>

<span data-ttu-id="5167d-273">Wygląd różnych elementów jest często taki sam dla wszystkich elementów tego samego typu w interfejsie użytkownika.</span><span class="sxs-lookup"><span data-stu-id="5167d-273">The appearance of various elements is often the same for all elements of the same type in a UI.</span></span> <span data-ttu-id="5167d-274">Interfejs użytkownika używa [stylów](../controls/styling-and-templating.md) , aby można było używać ich w wielu elementach.</span><span class="sxs-lookup"><span data-stu-id="5167d-274">UI uses [styles](../controls/styling-and-templating.md) to make appearances reusable across multiple elements.</span></span> <span data-ttu-id="5167d-275">Możliwość ponownego wykorzystania stylów ułatwia tworzenie i zarządzanie XAML.</span><span class="sxs-lookup"><span data-stu-id="5167d-275">The reusability of styles helps to simplify XAML creation and management.</span></span> <span data-ttu-id="5167d-276">Ta sekcja zastępuje atrybuty dla elementu, które zostały zdefiniowane w poprzednich krokach ze stylami.</span><span class="sxs-lookup"><span data-stu-id="5167d-276">This section replaces the per-element attributes that were defined in previous steps with styles.</span></span>

1. <span data-ttu-id="5167d-277">Otwórz *aplikację Application. XAML* lub *App. XAML*.</span><span class="sxs-lookup"><span data-stu-id="5167d-277">Open *Application.xaml* or *App.xaml*.</span></span>

2. <span data-ttu-id="5167d-278">Dodaj następujący kod XAML między <xref:System.Windows.Application.Resources%2A?displayProperty=nameWithType> tagami:</span><span class="sxs-lookup"><span data-stu-id="5167d-278">Add the following XAML between the <xref:System.Windows.Application.Resources%2A?displayProperty=nameWithType> tags:</span></span>

    [!code-xaml[ExpenseIt#18](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt7/App.xaml#18)]

    <span data-ttu-id="5167d-279">Ten kod XAML dodaje następujące style:</span><span class="sxs-lookup"><span data-stu-id="5167d-279">This XAML adds the following styles:</span></span>

    - <span data-ttu-id="5167d-280">`headerTextStyle`: Aby sformatować tytuł <xref:System.Windows.Controls.Label>strony.</span><span class="sxs-lookup"><span data-stu-id="5167d-280">`headerTextStyle`: To format the page title <xref:System.Windows.Controls.Label>.</span></span>

    - <span data-ttu-id="5167d-281">`labelStyle`: Do formatowania <xref:System.Windows.Controls.Label> kontrolek.</span><span class="sxs-lookup"><span data-stu-id="5167d-281">`labelStyle`: To format the <xref:System.Windows.Controls.Label> controls.</span></span>

    - <span data-ttu-id="5167d-282">`columnHeaderStyle`: Aby sformatować <xref:System.Windows.Controls.Primitives.DataGridColumnHeader>.</span><span class="sxs-lookup"><span data-stu-id="5167d-282">`columnHeaderStyle`: To format the <xref:System.Windows.Controls.Primitives.DataGridColumnHeader>.</span></span>

    - <span data-ttu-id="5167d-283">`listHeaderStyle`: Aby sformatować kontrolki <xref:System.Windows.Controls.Border> nagłówka listy.</span><span class="sxs-lookup"><span data-stu-id="5167d-283">`listHeaderStyle`: To format the list header <xref:System.Windows.Controls.Border> controls.</span></span>

    - <span data-ttu-id="5167d-284">`listHeaderTextStyle`: Aby sformatować nagłówek <xref:System.Windows.Controls.Label>listy.</span><span class="sxs-lookup"><span data-stu-id="5167d-284">`listHeaderTextStyle`: To format the list header <xref:System.Windows.Controls.Label>.</span></span>

    - <span data-ttu-id="5167d-285">`buttonStyle`: Aby sformatować <xref:System.Windows.Controls.Button> `ExpenseItHome.xaml`.</span><span class="sxs-lookup"><span data-stu-id="5167d-285">`buttonStyle`: To format the <xref:System.Windows.Controls.Button> on `ExpenseItHome.xaml`.</span></span>

    <span data-ttu-id="5167d-286">Należy zauważyć, że style są zasobami i elementami podrzędnymi <xref:System.Windows.Application.Resources%2A?displayProperty=nameWithType> elementu właściwości.</span><span class="sxs-lookup"><span data-stu-id="5167d-286">Notice that the styles are resources and children of the <xref:System.Windows.Application.Resources%2A?displayProperty=nameWithType> property element.</span></span> <span data-ttu-id="5167d-287">W tej lokalizacji style są stosowane do wszystkich elementów w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="5167d-287">In this location, the styles are applied to all the elements in an application.</span></span> <span data-ttu-id="5167d-288">Aby zapoznać się z przykładem użycia zasobów w aplikacji .NET, zobacz [Korzystanie z zasobów aplikacji](../advanced/how-to-use-application-resources.md).</span><span class="sxs-lookup"><span data-stu-id="5167d-288">For an example of using resources in a .NET app, see [Use Application Resources](../advanced/how-to-use-application-resources.md).</span></span>

3. <span data-ttu-id="5167d-289">W *`ExpenseItHome.xaml`* programie Zamień wszystkie <xref:System.Windows.Controls.Grid> elementy między elementami o następującym języku XAML:</span><span class="sxs-lookup"><span data-stu-id="5167d-289">In *`ExpenseItHome.xaml`*, replace everything between the <xref:System.Windows.Controls.Grid> elements with the following XAML:</span></span>

    [!code-xaml[ExpenseIt#19](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt7/ExpenseItHome.xaml#19)]

    <span data-ttu-id="5167d-290">Właściwości, takie jak <xref:System.Windows.VerticalAlignment> i <xref:System.Windows.Media.FontFamily> definiujące wygląd poszczególnych kontrolek, są usuwane i zastępowane przez zastosowanie stylów.</span><span class="sxs-lookup"><span data-stu-id="5167d-290">The properties such as <xref:System.Windows.VerticalAlignment> and <xref:System.Windows.Media.FontFamily> that define the look of each control are removed and replaced by applying the styles.</span></span> <span data-ttu-id="5167d-291">Na przykład, `headerTextStyle` jest stosowana do "Wyświetl raport wydatków" <xref:System.Windows.Controls.Label>.</span><span class="sxs-lookup"><span data-stu-id="5167d-291">For example, the `headerTextStyle` is applied to the "View Expense Report" <xref:System.Windows.Controls.Label>.</span></span>

4. <span data-ttu-id="5167d-292">Otwórz *ExpenseReportPage. XAML*.</span><span class="sxs-lookup"><span data-stu-id="5167d-292">Open *ExpenseReportPage.xaml*.</span></span>

5. <span data-ttu-id="5167d-293">Zastąp wszystkie <xref:System.Windows.Controls.Grid> elementy następującym XAML:</span><span class="sxs-lookup"><span data-stu-id="5167d-293">Replace everything between the <xref:System.Windows.Controls.Grid> elements with the following XAML:</span></span>

    [!code-xaml[ExpenseIt#20](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt7/ExpenseReportPage.xaml#20)]

    <span data-ttu-id="5167d-294">Ten kod XAML dodaje style do <xref:System.Windows.Controls.Label> elementów <xref:System.Windows.Controls.Border> i.</span><span class="sxs-lookup"><span data-stu-id="5167d-294">This XAML adds styles to the <xref:System.Windows.Controls.Label> and <xref:System.Windows.Controls.Border> elements.</span></span>

6. <span data-ttu-id="5167d-295">Skompiluj i uruchom aplikację.</span><span class="sxs-lookup"><span data-stu-id="5167d-295">Build and run the application.</span></span> <span data-ttu-id="5167d-296">Wygląd okna jest taki sam jak poprzednio.</span><span class="sxs-lookup"><span data-stu-id="5167d-296">The window appearance is the same as previously.</span></span>

    ![ExpenseIt Przykładowy zrzut ekranu z tym samym wyglądem, jak w ostatniej sekcji.](./media/walkthrough-my-first-wpf-desktop-application/create-application-ui.png)

7. <span data-ttu-id="5167d-298">Zamknij aplikację, aby powrócić do programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="5167d-298">Close the application to return to Visual Studio.</span></span>

## <a name="bind-data-to-a-control"></a><span data-ttu-id="5167d-299">Powiąż dane z kontrolką</span><span class="sxs-lookup"><span data-stu-id="5167d-299">Bind data to a control</span></span>

<span data-ttu-id="5167d-300">W tej sekcji utworzysz dane XML powiązane z różnymi kontrolkami.</span><span class="sxs-lookup"><span data-stu-id="5167d-300">In this section, you'll create the XML data that is bound to various controls.</span></span>

1. <span data-ttu-id="5167d-301">W *`ExpenseItHome.xaml`* programie po otwarciu <xref:System.Windows.Controls.Grid> elementu Dodaj <xref:System.Windows.Data.XmlDataProvider> następujący kod XAML, aby utworzyć zawierający dane dla każdej osoby:</span><span class="sxs-lookup"><span data-stu-id="5167d-301">In *`ExpenseItHome.xaml`*, after the opening <xref:System.Windows.Controls.Grid> element, add the following XAML to create an <xref:System.Windows.Data.XmlDataProvider> that contains the data for each person:</span></span>

    [!code-xaml[ExpenseIt#23](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml?range=13,16-40,49)]

    <span data-ttu-id="5167d-302">Dane są tworzone jako <xref:System.Windows.Controls.Grid> zasób.</span><span class="sxs-lookup"><span data-stu-id="5167d-302">The data is created as a <xref:System.Windows.Controls.Grid> resource.</span></span> <span data-ttu-id="5167d-303">Zwykle te dane zostałyby załadowane jako plik, ale dla uproszczenia dane są dodawane wewnętrznie.</span><span class="sxs-lookup"><span data-stu-id="5167d-303">Normally this data would be loaded as a file, but for simplicity the data is added inline.</span></span>

2. <span data-ttu-id="5167d-304">W elemencie Dodaj następujący `<xref:System.Windows.DataTemplate>` element, który definiuje sposób <xref:System.Windows.Controls.ListBox>wyświetlania danych `<XmlDataProvider>` w, po elemencie: `<Grid.Resources>`</span><span class="sxs-lookup"><span data-stu-id="5167d-304">Within the `<Grid.Resources>` element, add the following `<xref:System.Windows.DataTemplate>` element, which defines how to display the data in the <xref:System.Windows.Controls.ListBox>, after the `<XmlDataProvider>` element:</span></span>

    [!code-xaml[ExpenseIt#24](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml?range=13,43-46,49)]

    <span data-ttu-id="5167d-305">Aby uzyskać więcej informacji na temat szablonów danych, zobacz [tworzenia szablonów danych — omówienie](../data/data-templating-overview.md).</span><span class="sxs-lookup"><span data-stu-id="5167d-305">For more information about data templates, see [Data templating overview](../data/data-templating-overview.md).</span></span>

3. <span data-ttu-id="5167d-306">Zastąp istniejące <xref:System.Windows.Controls.ListBox> następującym XAML:</span><span class="sxs-lookup"><span data-stu-id="5167d-306">Replace the existing <xref:System.Windows.Controls.ListBox> with the following XAML:</span></span>

    [!code-xaml[ExpenseIt#25](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml#25)]

    <span data-ttu-id="5167d-307">Ten kod XAML wiąże <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> Właściwość <xref:System.Windows.Controls.ListBox> ze źródłem danych i stosuje szablon danych jako <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A>.</span><span class="sxs-lookup"><span data-stu-id="5167d-307">This XAML binds the <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> property of the <xref:System.Windows.Controls.ListBox> to the data source and applies the data template as the <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A>.</span></span>

## <a name="connect-data-to-controls"></a><span data-ttu-id="5167d-308">Łączenie danych z kontrolkami</span><span class="sxs-lookup"><span data-stu-id="5167d-308">Connect data to controls</span></span>

<span data-ttu-id="5167d-309">Następnie dodasz kod w celu pobrania nazwy wybranej na **`ExpenseItHome`** stronie i przekazania jej do konstruktora **ExpenseReportPage**.</span><span class="sxs-lookup"><span data-stu-id="5167d-309">Next, you'll add code to retrieve the name that's selected on the **`ExpenseItHome`** page and pass it to the constructor of **ExpenseReportPage**.</span></span> <span data-ttu-id="5167d-310">**ExpenseReportPage** ustawia swój kontekst danych z elementem zakończonym, co oznacza, że kontrolki zdefiniowane w *ExpenseReportPage. XAML* są powiązane z.</span><span class="sxs-lookup"><span data-stu-id="5167d-310">**ExpenseReportPage** sets its data context with the passed item, which is what the controls defined in *ExpenseReportPage.xaml* bind to.</span></span>

1. <span data-ttu-id="5167d-311">Otwórz *ExpenseReportPage. XAML. vb* lub *ExpenseReportPage.XAML.cs*.</span><span class="sxs-lookup"><span data-stu-id="5167d-311">Open *ExpenseReportPage.xaml.vb* or *ExpenseReportPage.xaml.cs*.</span></span>

2. <span data-ttu-id="5167d-312">Dodaj Konstruktor, który pobiera obiekt, aby można było przekazać dane raportu wydatków wybranej osoby.</span><span class="sxs-lookup"><span data-stu-id="5167d-312">Add a constructor that takes an object so you can pass the expense report data of the selected person.</span></span>

    [!code-csharp[ExpenseIt#26](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseReportPage.xaml.cs#26)]
    [!code-vb[ExpenseIt#26](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt8/ExpenseReportPage.xaml.vb#26)]

3. <span data-ttu-id="5167d-313">Otwórz *`ExpenseItHome.xaml.vb`* lub *`ExpenseItHome.xaml.cs`* .</span><span class="sxs-lookup"><span data-stu-id="5167d-313">Open *`ExpenseItHome.xaml.vb`* or *`ExpenseItHome.xaml.cs`*.</span></span>

4. <span data-ttu-id="5167d-314">Zmień procedurę obsługi zdarzeń, aby wywoływać nowego konstruktora przekazującego dane raportu wydatków wybranej osoby. <xref:System.Windows.Controls.Primitives.ButtonBase.Click></span><span class="sxs-lookup"><span data-stu-id="5167d-314">Change the <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event handler to call the new constructor passing the expense report data of the selected person.</span></span>

    [!code-csharp[ExpenseIt#27](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml.cs#27)]
    [!code-vb[ExpenseIt#27](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt8/ExpenseItHome.xaml.vb#27)]

## <a name="style-data-with-data-templates"></a><span data-ttu-id="5167d-315">Dane stylu z szablonami danych</span><span class="sxs-lookup"><span data-stu-id="5167d-315">Style data with data templates</span></span>

<span data-ttu-id="5167d-316">W tej sekcji należy zaktualizować interfejs użytkownika dla każdego elementu na listach powiązanych z danymi przy użyciu szablonów danych.</span><span class="sxs-lookup"><span data-stu-id="5167d-316">In this section, you'll update the UI for each item in the data-bound lists by using data templates.</span></span>

1. <span data-ttu-id="5167d-317">Otwórz *ExpenseReportPage. XAML*.</span><span class="sxs-lookup"><span data-stu-id="5167d-317">Open *ExpenseReportPage.xaml*.</span></span>

2. <span data-ttu-id="5167d-318">Powiąż zawartość elementów "name" i "Department" <xref:System.Windows.Controls.Label> z odpowiednią właściwością źródła danych.</span><span class="sxs-lookup"><span data-stu-id="5167d-318">Bind the content of the "Name" and "Department" <xref:System.Windows.Controls.Label> elements to the appropriate data source property.</span></span> <span data-ttu-id="5167d-319">Aby uzyskać więcej informacji na temat powiązania danych, zobacz temat [powiązanie danych — omówienie](../data/data-binding-overview.md).</span><span class="sxs-lookup"><span data-stu-id="5167d-319">For more information about data binding, see [Data binding overview](../data/data-binding-overview.md).</span></span>

    [!code-xaml[ExpenseIt#31](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseReportPage.xaml#31)]

3. <span data-ttu-id="5167d-320">Po otwarciu <xref:System.Windows.Controls.Grid> elementu Dodaj następujące szablony danych, które definiują sposób wyświetlania danych raportu wydatków:</span><span class="sxs-lookup"><span data-stu-id="5167d-320">After the opening <xref:System.Windows.Controls.Grid> element, add the following data templates, which define how to display the expense report data:</span></span>

    [!code-xaml[ExpenseIt#30](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseReportPage.xaml#30)]

4. <span data-ttu-id="5167d-321"><xref:System.Windows.Controls.DataGridTextColumn> Zamień elementy<xref:System.Windows.Controls.DataGridTemplateColumn> naelementiZastosuj<xref:System.Windows.Controls.DataGrid> do nich szablony.</span><span class="sxs-lookup"><span data-stu-id="5167d-321">Replace the <xref:System.Windows.Controls.DataGridTextColumn> elements with <xref:System.Windows.Controls.DataGridTemplateColumn> under the <xref:System.Windows.Controls.DataGrid> element and apply the templates to them.</span></span>

    [!code-xaml[ExpenseIt#32](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseReportPage.xaml#32)]

5. <span data-ttu-id="5167d-322">Skompiluj i uruchom aplikację.</span><span class="sxs-lookup"><span data-stu-id="5167d-322">Build and run the application.</span></span>

6. <span data-ttu-id="5167d-323">Wybierz osobę, a następnie wybierz przycisk **Wyświetl** .</span><span class="sxs-lookup"><span data-stu-id="5167d-323">Select a person and then select the **View** button.</span></span>

<span data-ttu-id="5167d-324">Na poniższej ilustracji przedstawiono obie strony `ExpenseIt` aplikacji z kontrolkami, układem, stylem, powiązaniem danych i szablonami danych, które zostały zastosowane:</span><span class="sxs-lookup"><span data-stu-id="5167d-324">The following illustration shows both pages of the `ExpenseIt` application with controls, layout, styles, data binding, and data templates applied:</span></span>

![Obie strony aplikacji pokazują listę nazw i raport wydatków.](./media/walkthrough-my-first-wpf-desktop-application/application-data-templates.png)

> [!NOTE]
> <span data-ttu-id="5167d-326">Ten przykład pokazuje konkretną funkcję WPF i nie jest zgodny ze wszystkimi najlepszymi rozwiązaniami dotyczącymi takich elementów, jak zabezpieczenia, lokalizacja i ułatwienia dostępu.</span><span class="sxs-lookup"><span data-stu-id="5167d-326">This sample demonstrates a specific feature of WPF and doesn't follow all best practices for things like security, localization, and accessibility.</span></span> <span data-ttu-id="5167d-327">Aby uzyskać kompleksową obsługę WPF i najlepszych rozwiązań programistycznych dotyczących projektowania aplikacji .NET, zobacz następujące tematy:</span><span class="sxs-lookup"><span data-stu-id="5167d-327">For comprehensive coverage of WPF and the .NET app development best practices, see the following topics:</span></span>
>
> - [<span data-ttu-id="5167d-328">Ułatwienia dostępu</span><span class="sxs-lookup"><span data-stu-id="5167d-328">Accessibility</span></span>](../../ui-automation/accessibility-best-practices.md)
>
> - [<span data-ttu-id="5167d-329">Zabezpieczenia</span><span class="sxs-lookup"><span data-stu-id="5167d-329">Security</span></span>](../security-wpf.md)
>
> - [<span data-ttu-id="5167d-330">Globalizacja i lokalizacja WPF</span><span class="sxs-lookup"><span data-stu-id="5167d-330">WPF globalization and localization</span></span>](../advanced/wpf-globalization-and-localization-overview.md)
>
> - [<span data-ttu-id="5167d-331">Wydajność WPF</span><span class="sxs-lookup"><span data-stu-id="5167d-331">WPF performance</span></span>](../advanced/optimizing-wpf-application-performance.md)

## <a name="next-steps"></a><span data-ttu-id="5167d-332">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="5167d-332">Next steps</span></span>

<span data-ttu-id="5167d-333">W tym instruktażu przedstawiono kilka technik tworzenia interfejsu użytkownika przy użyciu Windows Presentation Foundation (WPF).</span><span class="sxs-lookup"><span data-stu-id="5167d-333">In this walkthrough you learned a number of techniques for creating a UI using Windows Presentation Foundation (WPF).</span></span> <span data-ttu-id="5167d-334">Należy teraz dysponować podstawową wiedzą na temat bloków konstrukcyjnych aplikacji .NET powiązanych z danymi.</span><span class="sxs-lookup"><span data-stu-id="5167d-334">You should now have a basic understanding of the building blocks of a data-bound .NET app.</span></span> <span data-ttu-id="5167d-335">Aby uzyskać więcej informacji na temat architektury WPF i modeli programowania, zobacz następujące tematy:</span><span class="sxs-lookup"><span data-stu-id="5167d-335">For more information about the WPF architecture and programming models, see the following topics:</span></span>

- [<span data-ttu-id="5167d-336">Architektura WPF</span><span class="sxs-lookup"><span data-stu-id="5167d-336">WPF architecture</span></span>](../advanced/wpf-architecture.md)
- [<span data-ttu-id="5167d-337">Przegląd XAML (WPF)</span><span class="sxs-lookup"><span data-stu-id="5167d-337">XAML overview (WPF)</span></span>](../advanced/xaml-overview-wpf.md)
- [<span data-ttu-id="5167d-338">Przegląd właściwości zależności</span><span class="sxs-lookup"><span data-stu-id="5167d-338">Dependency properties overview</span></span>](../advanced/dependency-properties-overview.md)
- [<span data-ttu-id="5167d-339">Układ</span><span class="sxs-lookup"><span data-stu-id="5167d-339">Layout</span></span>](../advanced/layout.md)

<span data-ttu-id="5167d-340">Aby uzyskać więcej informacji na temat tworzenia aplikacji, zobacz następujące tematy:</span><span class="sxs-lookup"><span data-stu-id="5167d-340">For more information about creating applications, see the following topics:</span></span>

- [<span data-ttu-id="5167d-341">Opracowywanie aplikacji</span><span class="sxs-lookup"><span data-stu-id="5167d-341">Application development</span></span>](../app-development/index.md)
- [<span data-ttu-id="5167d-342">Kontrolki</span><span class="sxs-lookup"><span data-stu-id="5167d-342">Controls</span></span>](../controls/index.md)
- [<span data-ttu-id="5167d-343">Przegląd powiązań danych</span><span class="sxs-lookup"><span data-stu-id="5167d-343">Data binding overview</span></span>](../data/data-binding-overview.md)
- [<span data-ttu-id="5167d-344">Grafika i multimedia</span><span class="sxs-lookup"><span data-stu-id="5167d-344">Graphics and multimedia</span></span>](../graphics-multimedia/index.md)
- [<span data-ttu-id="5167d-345">Dokumenty w WPF</span><span class="sxs-lookup"><span data-stu-id="5167d-345">Documents in WPF</span></span>](../advanced/documents-in-wpf.md)

## <a name="see-also"></a><span data-ttu-id="5167d-346">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5167d-346">See also</span></span>

- [<span data-ttu-id="5167d-347">Panele — Omówienie</span><span class="sxs-lookup"><span data-stu-id="5167d-347">Panels overview</span></span>](../controls/panels-overview.md)
- [<span data-ttu-id="5167d-348">Tworzenia szablonów danych — omówienie</span><span class="sxs-lookup"><span data-stu-id="5167d-348">Data templating overview</span></span>](../data/data-templating-overview.md)
- [<span data-ttu-id="5167d-349">Tworzenie aplikacji WPF</span><span class="sxs-lookup"><span data-stu-id="5167d-349">Build a WPF application</span></span>](../app-development/building-a-wpf-application-wpf.md)
- [<span data-ttu-id="5167d-350">Style i szablony</span><span class="sxs-lookup"><span data-stu-id="5167d-350">Styles and templates</span></span>](../controls/styles-and-templates.md)
