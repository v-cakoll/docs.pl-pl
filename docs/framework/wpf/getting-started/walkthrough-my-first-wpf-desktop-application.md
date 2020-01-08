---
title: 'Samouczek: Tworzenie pierwszej aplikacji WPF w programie Visual Studio 2019 — .NET Framework'
ms.date: 09/06/2019
dev_langs:
- csharp
- vb
helpviewer_keywords:
- getting started [WPF], WPF
- WPF [WPF], getting started
ms.assetid: b96bed40-8946-4285-8fe4-88045ab854ed
ms.topic: tutorial
ms.custom: mvc,vs-dotnet
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7b5f74448ffce448740937c06a476a29c8659879
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/25/2019
ms.locfileid: "75336806"
---
# <a name="tutorial-create-your-first-wpf-application-in-visual-studio-2019"></a><span data-ttu-id="6cea1-102">Samouczek: Tworzenie pierwszej aplikacji WPF w programie Visual Studio 2019</span><span class="sxs-lookup"><span data-stu-id="6cea1-102">Tutorial: Create your first WPF application in Visual Studio 2019</span></span>

<span data-ttu-id="6cea1-103">W tym artykule przedstawiono sposób tworzenia aplikacji klasycznych Windows Presentation Foundation (WPF), która zawiera elementy wspólne dla większości aplikacji WPF: znaczniki Extensible Application Markup Language (XAML), powiązane z kodem, definicje aplikacji, kontrolki, układ, powiązanie danych i style.</span><span class="sxs-lookup"><span data-stu-id="6cea1-103">This article shows you how to develop a Windows Presentation Foundation (WPF) desktop application that includes the elements that are common to most WPF applications: Extensible Application Markup Language (XAML) markup, code-behind, application definitions, controls, layout, data binding, and styles.</span></span> <span data-ttu-id="6cea1-104">Aby opracować aplikację, użyjesz programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="6cea1-104">To develop the application, you'll use Visual Studio.</span></span> 

<span data-ttu-id="6cea1-105">Z tego samouczka dowiesz się, jak wykonywać następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="6cea1-105">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="6cea1-106">Utwórz projekt WPF.</span><span class="sxs-lookup"><span data-stu-id="6cea1-106">Create a WPF project.</span></span>
> - <span data-ttu-id="6cea1-107">Użyj języka XAML, aby zaprojektować wygląd interfejsu użytkownika aplikacji.</span><span class="sxs-lookup"><span data-stu-id="6cea1-107">Use XAML to design the appearance of the application's user interface (UI).</span></span>
> - <span data-ttu-id="6cea1-108">Napisz kod, aby skompilować zachowanie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="6cea1-108">Write code to build the application's behavior.</span></span>
> - <span data-ttu-id="6cea1-109">Utwórz definicję aplikacji w celu zarządzania aplikacją.</span><span class="sxs-lookup"><span data-stu-id="6cea1-109">Create an application definition to manage the application.</span></span>
> - <span data-ttu-id="6cea1-110">Dodaj kontrolki i Utwórz układ, aby utworzyć interfejs użytkownika aplikacji.</span><span class="sxs-lookup"><span data-stu-id="6cea1-110">Add controls and create the layout to compose the application UI.</span></span>
> - <span data-ttu-id="6cea1-111">Tworzenie stylów dla spójnego wyglądu w całym interfejsie użytkownika aplikacji.</span><span class="sxs-lookup"><span data-stu-id="6cea1-111">Create styles for a consistent appearance throughout the application's UI.</span></span>
> - <span data-ttu-id="6cea1-112">Powiąż interfejs użytkownika z danymi, zarówno w celu wypełnienia interfejsu użytkownika z danych, jak i zachowania synchronizacji danych i interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="6cea1-112">Bind the UI to data, both to populate the UI from data and to keep the data and UI synchronized.</span></span>

<span data-ttu-id="6cea1-113">Na końcu samouczka utworzysz autonomiczną aplikację systemu Windows, która umożliwia użytkownikom wyświetlanie raportów wydatków dla wybranych osób.</span><span class="sxs-lookup"><span data-stu-id="6cea1-113">By the end of the tutorial, you'll have built a standalone Windows application that allows users to view expense reports for selected people.</span></span> <span data-ttu-id="6cea1-114">Aplikacja składa się z kilku stron WPF, które są hostowane w oknie stylu przeglądarki.</span><span class="sxs-lookup"><span data-stu-id="6cea1-114">The application is composed of several WPF pages that are hosted in a browser-style window.</span></span>

> [!TIP]
> <span data-ttu-id="6cea1-115">Przykładowy kod używany w tym samouczku jest dostępny zarówno w Visual Basic, jak i C# w [samouczku przykładowy kod aplikacji WPF](https://github.com/Microsoft/WPF-Samples/tree/master/Getting%20Started/WalkthroughFirstWPFApp).</span><span class="sxs-lookup"><span data-stu-id="6cea1-115">The sample code that is used in this tutorial is available for both Visual Basic and C# at [Tutorial WPF App Sample Code](https://github.com/Microsoft/WPF-Samples/tree/master/Getting%20Started/WalkthroughFirstWPFApp).</span></span>
>
> <span data-ttu-id="6cea1-116">Można przełączać język kodu przykładowego kodu między C# i Visual Basic przy użyciu selektora języka znajdującego się na tej stronie.</span><span class="sxs-lookup"><span data-stu-id="6cea1-116">You can toggle the code language of the sample code between C# and Visual Basic by using the language selector on top of this page.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="6cea1-117">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="6cea1-117">Prerequisites</span></span>

- <span data-ttu-id="6cea1-118">[Program Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) z zainstalowanym obciążeniem **programowania programu .NET Desktop** .</span><span class="sxs-lookup"><span data-stu-id="6cea1-118">[Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) with the **.NET desktop development** workload installed.</span></span>

   <span data-ttu-id="6cea1-119">Aby uzyskać więcej informacji na temat instalowania najnowszej wersji programu Visual Studio, zobacz [Instalowanie programu Visual Studio](/visualstudio/install/install-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="6cea1-119">For more information about installing the latest version of Visual Studio, see [Install Visual Studio](/visualstudio/install/install-visual-studio).</span></span>

## <a name="create-the-application-project"></a><span data-ttu-id="6cea1-120">Tworzenie projektu aplikacji</span><span class="sxs-lookup"><span data-stu-id="6cea1-120">Create the application project</span></span>

<span data-ttu-id="6cea1-121">Pierwszym krokiem jest utworzenie infrastruktury aplikacji, która obejmuje definicję aplikacji, dwie strony i obraz.</span><span class="sxs-lookup"><span data-stu-id="6cea1-121">The first step is to create the application infrastructure, which includes an application definition, two pages, and an image.</span></span>

1. <span data-ttu-id="6cea1-122">Utwórz nowy projekt aplikacji WPF w Visual Basic lub wizualizacji C# o nazwie **`ExpenseIt`** :</span><span class="sxs-lookup"><span data-stu-id="6cea1-122">Create a new WPF Application project in Visual Basic or Visual C# named **`ExpenseIt`**:</span></span>

   1. <span data-ttu-id="6cea1-123">Otwórz program Visual Studio i wybierz pozycję **Utwórz nowy projekt** w menu **wprowadzenie** .</span><span class="sxs-lookup"><span data-stu-id="6cea1-123">Open Visual Studio and select **Create a new project** under the **Get started** menu.</span></span>

      <span data-ttu-id="6cea1-124">Zostanie otwarte okno dialogowe **Tworzenie nowego projektu** .</span><span class="sxs-lookup"><span data-stu-id="6cea1-124">The **Create a new project** dialog opens.</span></span>

   2. <span data-ttu-id="6cea1-125">Z listy rozwijanej **Język** wybierz opcję **C#** lub **Visual Basic**.</span><span class="sxs-lookup"><span data-stu-id="6cea1-125">In the **Language** dropdown, select either **C#** or **Visual Basic**.</span></span>
      
   3. <span data-ttu-id="6cea1-126">Wybierz szablon **Aplikacja WPF (.NET Framework)** , a następnie wybierz przycisk **dalej**.</span><span class="sxs-lookup"><span data-stu-id="6cea1-126">Select the **WPF App (.NET Framework)** template and then select **Next**.</span></span> 
     
      ![Okno dialogowe Tworzenie nowego projektu](./media/walkthrough-my-first-wpf-desktop-application/create-new-project-dialog.png)
    
      <span data-ttu-id="6cea1-128">Zostanie otwarte okno dialogowe **Konfigurowanie nowego projektu** .</span><span class="sxs-lookup"><span data-stu-id="6cea1-128">The **Configure your new project** dialog opens.</span></span>

   4. <span data-ttu-id="6cea1-129">Wprowadź nazwę projektu **`ExpenseIt`** a następnie wybierz pozycję **Utwórz**.</span><span class="sxs-lookup"><span data-stu-id="6cea1-129">Enter the project name **`ExpenseIt`** and then select **Create**.</span></span>

      ![Okno dialogowe Konfigurowanie nowego projektu](./media/walkthrough-my-first-wpf-desktop-application/configure-new-project-dialog.png)

      <span data-ttu-id="6cea1-131">Program Visual Studio tworzy projekt i otwiera projektanta dla domyślnego okna aplikacji o nazwie **MainWindow. XAML**.</span><span class="sxs-lookup"><span data-stu-id="6cea1-131">Visual Studio creates the project and opens the designer for the default application window named **MainWindow.xaml**.</span></span>

2. <span data-ttu-id="6cea1-132">Otwórz *aplikację Application. XAML* (Visual Basic) lub *App. XAML* (C#).</span><span class="sxs-lookup"><span data-stu-id="6cea1-132">Open *Application.xaml* (Visual Basic) or *App.xaml* (C#).</span></span>

    <span data-ttu-id="6cea1-133">Ten plik XAML definiuje aplikację WPF i wszystkie zasoby aplikacji.</span><span class="sxs-lookup"><span data-stu-id="6cea1-133">This XAML file defines a WPF application and any application resources.</span></span> <span data-ttu-id="6cea1-134">Ten plik jest również używany do określenia interfejsu użytkownika (w tym przypadku *MainWindow. XAML*), który jest automatycznie wyświetlany podczas uruchamiania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="6cea1-134">You also use this file to specify the UI, in this case *MainWindow.xaml*, that automatically shows when the application starts.</span></span>

    <span data-ttu-id="6cea1-135">KOD XAML powinien wyglądać następująco w Visual Basic:</span><span class="sxs-lookup"><span data-stu-id="6cea1-135">Your XAML should look like the following in Visual Basic:</span></span>

    [!code-xaml[ExpenseIt#1_A](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/Application.xaml#1_a)]

    <span data-ttu-id="6cea1-136">I podobne do następujących w C#programie:</span><span class="sxs-lookup"><span data-stu-id="6cea1-136">And like the following in C#:</span></span>

    [!code-xaml[ExpenseIt#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/App.xaml#1)]

3. <span data-ttu-id="6cea1-137">Otwórz *MainWindow. XAML*.</span><span class="sxs-lookup"><span data-stu-id="6cea1-137">Open *MainWindow.xaml*.</span></span>

    <span data-ttu-id="6cea1-138">Ten plik XAML jest głównym oknem aplikacji i wyświetla zawartość utworzoną na stronach.</span><span class="sxs-lookup"><span data-stu-id="6cea1-138">This XAML file is the main window of your application and displays content created in pages.</span></span> <span data-ttu-id="6cea1-139">Klasa <xref:System.Windows.Window> definiuje właściwości okna, takie jak tytuł, rozmiar lub ikona i obsługuje zdarzenia, takie jak zamykanie lub ukrywanie.</span><span class="sxs-lookup"><span data-stu-id="6cea1-139">The <xref:System.Windows.Window> class defines the properties of a window, such as its title, size, or icon, and handles events, such as closing or hiding.</span></span>

4. <span data-ttu-id="6cea1-140">Zmień element <xref:System.Windows.Window> na <xref:System.Windows.Navigation.NavigationWindow>, jak pokazano na poniższym kodzie XAML:</span><span class="sxs-lookup"><span data-stu-id="6cea1-140">Change the <xref:System.Windows.Window> element to a <xref:System.Windows.Navigation.NavigationWindow>, as shown in the following XAML:</span></span>

   ```xaml
   <NavigationWindow x:Class="ExpenseIt.MainWindow"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        ...
   </NavigationWindow>
   ```

   <span data-ttu-id="6cea1-141">Ta aplikacja nawiguje do innej zawartości w zależności od danych wprowadzonych przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="6cea1-141">This app navigates to different content depending on the user input.</span></span> <span data-ttu-id="6cea1-142">Dlatego głównym <xref:System.Windows.Window> należy zmienić na <xref:System.Windows.Navigation.NavigationWindow>.</span><span class="sxs-lookup"><span data-stu-id="6cea1-142">This is why the main <xref:System.Windows.Window> needs to be changed to a <xref:System.Windows.Navigation.NavigationWindow>.</span></span> <span data-ttu-id="6cea1-143"><xref:System.Windows.Navigation.NavigationWindow> dziedziczy wszystkie właściwości <xref:System.Windows.Window>.</span><span class="sxs-lookup"><span data-stu-id="6cea1-143"><xref:System.Windows.Navigation.NavigationWindow> inherits all the properties of <xref:System.Windows.Window>.</span></span> <span data-ttu-id="6cea1-144">Element <xref:System.Windows.Navigation.NavigationWindow> w pliku XAML tworzy wystąpienie klasy <xref:System.Windows.Navigation.NavigationWindow>.</span><span class="sxs-lookup"><span data-stu-id="6cea1-144">The <xref:System.Windows.Navigation.NavigationWindow> element in the XAML file creates an instance of the <xref:System.Windows.Navigation.NavigationWindow> class.</span></span> <span data-ttu-id="6cea1-145">Aby uzyskać więcej informacji, zobacz [Omówienie nawigacji](../app-development/navigation-overview.md).</span><span class="sxs-lookup"><span data-stu-id="6cea1-145">For more information, see [Navigation overview](../app-development/navigation-overview.md).</span></span>

5. <span data-ttu-id="6cea1-146">Usuń <xref:System.Windows.Controls.Grid> elementy z między tagami <xref:System.Windows.Navigation.NavigationWindow>.</span><span class="sxs-lookup"><span data-stu-id="6cea1-146">Remove the <xref:System.Windows.Controls.Grid> elements from between the <xref:System.Windows.Navigation.NavigationWindow> tags.</span></span>

6. <span data-ttu-id="6cea1-147">Zmień następujące właściwości w kodzie XAML dla elementu <xref:System.Windows.Navigation.NavigationWindow>:</span><span class="sxs-lookup"><span data-stu-id="6cea1-147">Change the following properties in the XAML code for the <xref:System.Windows.Navigation.NavigationWindow> element:</span></span>

    - <span data-ttu-id="6cea1-148">Ustaw właściwość <xref:System.Windows.Window.Title%2A> na "`ExpenseIt`".</span><span class="sxs-lookup"><span data-stu-id="6cea1-148">Set the <xref:System.Windows.Window.Title%2A> property to "`ExpenseIt`".</span></span>

    - <span data-ttu-id="6cea1-149">Ustaw właściwość <xref:System.Windows.FrameworkElement.Height%2A> na 350 pikseli.</span><span class="sxs-lookup"><span data-stu-id="6cea1-149">Set the <xref:System.Windows.FrameworkElement.Height%2A> property to 350 pixels.</span></span>

    - <span data-ttu-id="6cea1-150">Ustaw właściwość <xref:System.Windows.FrameworkElement.Width%2A> na 500 pikseli.</span><span class="sxs-lookup"><span data-stu-id="6cea1-150">Set the <xref:System.Windows.FrameworkElement.Width%2A> property to 500 pixels.</span></span>

    <span data-ttu-id="6cea1-151">KOD XAML powinien wyglądać podobnie do poniższego Visual Basic:</span><span class="sxs-lookup"><span data-stu-id="6cea1-151">Your XAML should look like the following for Visual Basic:</span></span>

    [!code-xaml[ExpenseIt#2_A](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt/MainWindow.xaml#2_a)]

    <span data-ttu-id="6cea1-152">I podobne do C#następujących:</span><span class="sxs-lookup"><span data-stu-id="6cea1-152">And like the following for C#:</span></span>

    [!code-xaml[ExpenseIt#2](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/MainWindow.xaml#2)]

7. <span data-ttu-id="6cea1-153">Otwórz *MainWindow. XAML. vb* lub *MainWindow.XAML.cs*.</span><span class="sxs-lookup"><span data-stu-id="6cea1-153">Open *MainWindow.xaml.vb* or *MainWindow.xaml.cs*.</span></span>

    <span data-ttu-id="6cea1-154">Ten plik jest plikiem związanym z kodem, który zawiera kod służący do obsługi zdarzeń zadeklarowanych w *MainWindow. XAML*.</span><span class="sxs-lookup"><span data-stu-id="6cea1-154">This file is a code-behind file that contains code to handle the events declared in *MainWindow.xaml*.</span></span> <span data-ttu-id="6cea1-155">Ten plik zawiera klasę częściową dla okna zdefiniowanego w języku XAML.</span><span class="sxs-lookup"><span data-stu-id="6cea1-155">This file contains a partial class for the window defined in XAML.</span></span>

8. <span data-ttu-id="6cea1-156">Jeśli używasz programu C#, zmień klasę `MainWindow`, aby dziedziczyć z <xref:System.Windows.Navigation.NavigationWindow>.</span><span class="sxs-lookup"><span data-stu-id="6cea1-156">If you're using C#, change the `MainWindow` class to derive from <xref:System.Windows.Navigation.NavigationWindow>.</span></span> <span data-ttu-id="6cea1-157">(W Visual Basic dzieje się to automatycznie po zmianie okna w języku XAML). C# Kod powinien teraz wyglądać następująco:</span><span class="sxs-lookup"><span data-stu-id="6cea1-157">(In Visual Basic, this happens automatically when you change the window in XAML.) Your C# code should now look like this:</span></span>

   [!code-csharp[ExpenseIt#3](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/MainWindow.xaml.cs?highlight=21)]

## <a name="add-files-to-the-application"></a><span data-ttu-id="6cea1-158">Dodawanie plików do aplikacji</span><span class="sxs-lookup"><span data-stu-id="6cea1-158">Add files to the application</span></span>

<span data-ttu-id="6cea1-159">W tej sekcji dodasz dwie strony i obraz do aplikacji.</span><span class="sxs-lookup"><span data-stu-id="6cea1-159">In this section, you'll add two pages and an image to the application.</span></span>

1. <span data-ttu-id="6cea1-160">Dodaj nową stronę do projektu i nadaj jej nazwę *`ExpenseItHome.xaml`* :</span><span class="sxs-lookup"><span data-stu-id="6cea1-160">Add a new page to the project, and name it *`ExpenseItHome.xaml`*:</span></span>

   1. <span data-ttu-id="6cea1-161">W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy węzeł projektu **`ExpenseIt`** i wybierz polecenie **Dodaj** > **stronę**.</span><span class="sxs-lookup"><span data-stu-id="6cea1-161">In **Solution Explorer**, right-click on the **`ExpenseIt`** project node and choose **Add** > **Page**.</span></span>

   1. <span data-ttu-id="6cea1-162">W oknie dialogowym **Dodaj nowy element** szablon **Strona (WPF)** jest już zaznaczony.</span><span class="sxs-lookup"><span data-stu-id="6cea1-162">In the **Add New Item** dialog, the **Page (WPF)** template is already selected.</span></span> <span data-ttu-id="6cea1-163">Wprowadź nazwę **`ExpenseItHome`** a następnie wybierz pozycję **Dodaj**.</span><span class="sxs-lookup"><span data-stu-id="6cea1-163">Enter the name **`ExpenseItHome`**, and then select **Add**.</span></span>

    <span data-ttu-id="6cea1-164">Ta strona to pierwsza strona wyświetlana podczas uruchamiania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="6cea1-164">This page is the first page that's displayed when the application is launched.</span></span> <span data-ttu-id="6cea1-165">Zostanie wyświetlona lista osób, spośród których można wybrać, aby wyświetlić raport wydatków dla programu.</span><span class="sxs-lookup"><span data-stu-id="6cea1-165">It will show a list of people to select from, to show an expense report for.</span></span>

1. <span data-ttu-id="6cea1-166">Otwórz *`ExpenseItHome.xaml`* .</span><span class="sxs-lookup"><span data-stu-id="6cea1-166">Open *`ExpenseItHome.xaml`*.</span></span>

1. <span data-ttu-id="6cea1-167">Ustaw <xref:System.Windows.Controls.Page.Title%2A> na "`ExpenseIt - Home`".</span><span class="sxs-lookup"><span data-stu-id="6cea1-167">Set the <xref:System.Windows.Controls.Page.Title%2A> to "`ExpenseIt - Home`".</span></span>

1. <span data-ttu-id="6cea1-168">Ustaw `DesignHeight` na 350 pikseli i `DesignWidth` na 500 pikseli.</span><span class="sxs-lookup"><span data-stu-id="6cea1-168">Set the `DesignHeight` to 350 pixels and the `DesignWidth` to 500 pixels.</span></span>

    <span data-ttu-id="6cea1-169">KOD XAML jest teraz wyświetlany w następujący sposób dla Visual Basic:</span><span class="sxs-lookup"><span data-stu-id="6cea1-169">The XAML now appears as follows for Visual Basic:</span></span>

    [!code-xaml[ExpenseIt#6_A](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseItHome.xaml#6_a)]

    <span data-ttu-id="6cea1-170">I podobne do C#następujących:</span><span class="sxs-lookup"><span data-stu-id="6cea1-170">And like the following for C#:</span></span>

    [!code-xaml[ExpenseIt#6](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt2/ExpenseItHome.xaml#6)]

1. <span data-ttu-id="6cea1-171">Otwórz *MainWindow. XAML*.</span><span class="sxs-lookup"><span data-stu-id="6cea1-171">Open *MainWindow.xaml*.</span></span>

1. <span data-ttu-id="6cea1-172">Dodaj właściwość <xref:System.Windows.Navigation.NavigationWindow.Source%2A> do elementu <xref:System.Windows.Navigation.NavigationWindow> i ustaw ją na "`ExpenseItHome.xaml`".</span><span class="sxs-lookup"><span data-stu-id="6cea1-172">Add a <xref:System.Windows.Navigation.NavigationWindow.Source%2A> property to the <xref:System.Windows.Navigation.NavigationWindow> element and set it to "`ExpenseItHome.xaml`".</span></span>

    <span data-ttu-id="6cea1-173">To ustawienie *`ExpenseItHome.xaml`* być pierwszą stroną otwartą podczas uruchamiania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="6cea1-173">This sets *`ExpenseItHome.xaml`* to be the first page opened when the application starts.</span></span> 

    <span data-ttu-id="6cea1-174">Przykładowy kod XAML w Visual Basic:</span><span class="sxs-lookup"><span data-stu-id="6cea1-174">Example XAML in Visual Basic:</span></span>

    [!code-xaml[ExpenseIt#7_A](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/MainWindow.xaml#7_a)]

    <span data-ttu-id="6cea1-175">W języku C#:</span><span class="sxs-lookup"><span data-stu-id="6cea1-175">And in C#:</span></span>

    [!code-xaml[ExpenseIt#7](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt2/MainWindow.xaml#7)]

   > [!TIP]
   > <span data-ttu-id="6cea1-176">Możesz również ustawić właściwość **Source** w kategorii **różne** okna **Właściwości** .</span><span class="sxs-lookup"><span data-stu-id="6cea1-176">You can also set the **Source** property in the **Miscellaneous** category of the **Properties** window.</span></span>
   >
   > ![Właściwość Source w okno Właściwości](./media/properties-source.png)

1. <span data-ttu-id="6cea1-178">Dodaj kolejną nową stronę WPF do projektu i nadaj jej nazwę *ExpenseReportPage. XAML*::</span><span class="sxs-lookup"><span data-stu-id="6cea1-178">Add another new WPF page to the project, and name it *ExpenseReportPage.xaml*::</span></span>

   1. <span data-ttu-id="6cea1-179">W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy węzeł projektu **`ExpenseIt`** i wybierz polecenie **Dodaj** > **stronę**.</span><span class="sxs-lookup"><span data-stu-id="6cea1-179">In **Solution Explorer**, right-click on the **`ExpenseIt`** project node and choose **Add** > **Page**.</span></span>

   1. <span data-ttu-id="6cea1-180">W oknie dialogowym **Dodaj nowy element** wybierz szablon **Strona (WPF)** .</span><span class="sxs-lookup"><span data-stu-id="6cea1-180">In the **Add New Item** dialog, select the **Page (WPF)** template.</span></span> <span data-ttu-id="6cea1-181">Wprowadź nazwę **ExpenseReportPage**, a następnie wybierz pozycję **Dodaj**.</span><span class="sxs-lookup"><span data-stu-id="6cea1-181">Enter the name **ExpenseReportPage**, and then select **Add**.</span></span>

    <span data-ttu-id="6cea1-182">Na tej stronie zostanie wyświetlony raport wydatków dla osoby, która została wybrana na stronie **`ExpenseItHome`** .</span><span class="sxs-lookup"><span data-stu-id="6cea1-182">This page will show the expense report for the person that is selected on the **`ExpenseItHome`** page.</span></span>

1. <span data-ttu-id="6cea1-183">Otwórz *ExpenseReportPage. XAML*.</span><span class="sxs-lookup"><span data-stu-id="6cea1-183">Open *ExpenseReportPage.xaml*.</span></span>

1. <span data-ttu-id="6cea1-184">Ustaw <xref:System.Windows.Controls.Page.Title%2A> na "`ExpenseIt - View Expense`".</span><span class="sxs-lookup"><span data-stu-id="6cea1-184">Set the <xref:System.Windows.Controls.Page.Title%2A> to "`ExpenseIt - View Expense`".</span></span>

1. <span data-ttu-id="6cea1-185">Ustaw `DesignHeight` na 350 pikseli i `DesignWidth` na 500 pikseli.</span><span class="sxs-lookup"><span data-stu-id="6cea1-185">Set the `DesignHeight` to 350 pixels and the `DesignWidth` to 500 pixels.</span></span> 

    <span data-ttu-id="6cea1-186">*ExpenseReportPage. XAML* wygląda teraz następująco w Visual Basic:</span><span class="sxs-lookup"><span data-stu-id="6cea1-186">*ExpenseReportPage.xaml* now looks like the following in Visual Basic:</span></span>

    [!code-xaml[ExpenseIt#4_A](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseReportPage.xaml#4_a)]

    <span data-ttu-id="6cea1-187">I podobne do następujących w C#programie:</span><span class="sxs-lookup"><span data-stu-id="6cea1-187">And like the following in C#:</span></span>

    [!code-xaml[ExpenseIt#4](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/ExpenseReportPage.xaml#4)]

1. <span data-ttu-id="6cea1-188">Otwórz *ExpenseItHome. XAML. vb* oraz *ExpenseReportPage. XAML. vb*lub *ExpenseItHome.XAML.cs* i *ExpenseReportPage.XAML.cs*.</span><span class="sxs-lookup"><span data-stu-id="6cea1-188">Open *ExpenseItHome.xaml.vb* and *ExpenseReportPage.xaml.vb*, or *ExpenseItHome.xaml.cs* and *ExpenseReportPage.xaml.cs*.</span></span>

    <span data-ttu-id="6cea1-189">Podczas tworzenia nowego pliku stronicowania program Visual Studio automatycznie tworzy swój plik *związany z kodem* .</span><span class="sxs-lookup"><span data-stu-id="6cea1-189">When you create a new Page file, Visual Studio automatically creates its *code-behind* file.</span></span> <span data-ttu-id="6cea1-190">Te pliki związane z kodem obsługują logikę w celu reagowania na dane wejściowe użytkownika.</span><span class="sxs-lookup"><span data-stu-id="6cea1-190">These code-behind files handle the logic for responding to user input.</span></span>

    <span data-ttu-id="6cea1-191">Kod powinien wyglądać podobnie do poniższego **`ExpenseItHome`** :</span><span class="sxs-lookup"><span data-stu-id="6cea1-191">Your code should look like the following for **`ExpenseItHome`**:</span></span>

    [!code-csharp[ExpenseIt#2_5](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt2/ExpenseItHome.xaml.cs#2_5)]

    [!code-vb[ExpenseIt#2_5](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseItHome.xaml.vb#2_5)]

    <span data-ttu-id="6cea1-192">I tak jak w przypadku **ExpenseReportPage**:</span><span class="sxs-lookup"><span data-stu-id="6cea1-192">And like the following for **ExpenseReportPage**:</span></span>

    [!code-csharp[ExpenseIt#5](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/ExpenseReportPage.xaml.cs#5)]

    [!code-vb[ExpenseIt#5](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseReportPage.xaml.vb#5)]

1. <span data-ttu-id="6cea1-193">Dodaj obraz o nazwie *znak wodny. png* do projektu.</span><span class="sxs-lookup"><span data-stu-id="6cea1-193">Add an image named *watermark.png* to the project.</span></span> <span data-ttu-id="6cea1-194">Możesz utworzyć własny obraz, skopiować plik z przykładowego kodu lub pobrać go z repozytorium GitHub [Microsoft/WPF-Samples](https://raw.githubusercontent.com/microsoft/WPF-Samples/master/Getting%20Started/WalkthroughFirstWPFApp/csharp/watermark.png) .</span><span class="sxs-lookup"><span data-stu-id="6cea1-194">You can create your own image, copy the file from the sample code, or get it from the [microsoft/WPF-Samples](https://raw.githubusercontent.com/microsoft/WPF-Samples/master/Getting%20Started/WalkthroughFirstWPFApp/csharp/watermark.png) GitHub repository.</span></span>

    1. <span data-ttu-id="6cea1-195">Kliknij prawym przyciskiem myszy węzeł projektu i wybierz polecenie **dodaj** > **istniejący element**lub naciśnij klawisz **SHIFT**+**Alt**+**A**.</span><span class="sxs-lookup"><span data-stu-id="6cea1-195">Right-click on the project node and select **Add** > **Existing Item**, or press **Shift**+**Alt**+**A**.</span></span>

    2. <span data-ttu-id="6cea1-196">W oknie dialogowym **Dodaj istniejący element** Ustaw filtr pliku na **wszystkie pliki** lub **pliki obrazów**, przejdź do pliku obrazu, którego chcesz użyć, a następnie wybierz pozycję **Dodaj**.</span><span class="sxs-lookup"><span data-stu-id="6cea1-196">In the **Add Existing Item** dialog, set the file filter to either **All Files** or **Image Files**, browse to the image file you want to use, and then select **Add**.</span></span>

## <a name="build-and-run-the-application"></a><span data-ttu-id="6cea1-197">Kompilowanie i uruchamianie aplikacji</span><span class="sxs-lookup"><span data-stu-id="6cea1-197">Build and run the application</span></span>

1. <span data-ttu-id="6cea1-198">Aby skompilować i uruchomić aplikację, naciśnij klawisz **F5** lub wybierz pozycję **Rozpocznij debugowanie** z menu **debugowanie** .</span><span class="sxs-lookup"><span data-stu-id="6cea1-198">To build and run the application, press **F5** or select **Start Debugging** from the **Debug** menu.</span></span>

    <span data-ttu-id="6cea1-199">Na poniższej ilustracji przedstawiono aplikację z przyciskami <xref:System.Windows.Navigation.NavigationWindow>:</span><span class="sxs-lookup"><span data-stu-id="6cea1-199">The following illustration shows the application with the <xref:System.Windows.Navigation.NavigationWindow> buttons:</span></span>

    ![Po skompilowaniu i uruchomieniu aplikacji.](./media/walkthrough-my-first-wpf-desktop-application/build-run-application.png)

2. <span data-ttu-id="6cea1-201">Zamknij aplikację, aby powrócić do programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="6cea1-201">Close the application to return to Visual Studio.</span></span>

## <a name="create-the-layout"></a><span data-ttu-id="6cea1-202">Tworzenie układu</span><span class="sxs-lookup"><span data-stu-id="6cea1-202">Create the layout</span></span>

<span data-ttu-id="6cea1-203">Układ zapewnia uporządkowany sposób umieszczania elementów interfejsu użytkownika, a także zarządza rozmiarem i położeniem tych elementów w przypadku zmiany rozmiaru interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="6cea1-203">Layout provides an ordered way to place UI elements, and also manages the size and position of those elements when a UI is resized.</span></span> <span data-ttu-id="6cea1-204">Zazwyczaj tworzysz układ z jedną z następujących kontrolek układu:</span><span class="sxs-lookup"><span data-stu-id="6cea1-204">You typically create a layout with one of the following layout controls:</span></span>

- <span data-ttu-id="6cea1-205"><xref:System.Windows.Controls.Canvas> — definiuje obszar, w którym można jawnie pozycjonować elementy podrzędne za pomocą współrzędnych względnych dla obszaru kanwy.</span><span class="sxs-lookup"><span data-stu-id="6cea1-205"><xref:System.Windows.Controls.Canvas> - Defines an area within which you can explicitly position child elements by using coordinates that are relative to the Canvas area.</span></span>
- <span data-ttu-id="6cea1-206"><xref:System.Windows.Controls.DockPanel> — definiuje obszar, w którym można rozmieścić elementy podrzędne w poziomie lub w pionie względem siebie.</span><span class="sxs-lookup"><span data-stu-id="6cea1-206"><xref:System.Windows.Controls.DockPanel> - Defines an area where you can arrange child elements either horizontally or vertically, relative to each other.</span></span>
- <span data-ttu-id="6cea1-207"><xref:System.Windows.Controls.Grid> — definiuje elastyczny obszar siatki składający się z kolumn i wierszy.</span><span class="sxs-lookup"><span data-stu-id="6cea1-207"><xref:System.Windows.Controls.Grid> - Defines a flexible grid area that consists of columns and rows.</span></span>
- <span data-ttu-id="6cea1-208"><xref:System.Windows.Controls.StackPanel> — rozmieszcza elementy podrzędne w pojedynczym wierszu, który może być zorientowany w poziomie lub w pionie.</span><span class="sxs-lookup"><span data-stu-id="6cea1-208"><xref:System.Windows.Controls.StackPanel> - Arranges child elements into a single line that can be oriented horizontally or vertically.</span></span>
- <span data-ttu-id="6cea1-209"><xref:System.Windows.Controls.VirtualizingStackPanel> — rozmieszcza i wirtualizację zawartości w jednym wierszu, który ma orientację poziomą lub pionową.</span><span class="sxs-lookup"><span data-stu-id="6cea1-209"><xref:System.Windows.Controls.VirtualizingStackPanel> - Arranges and virtualizes content on a single line that is oriented either horizontally or vertically.</span></span>
- <span data-ttu-id="6cea1-210"><xref:System.Windows.Controls.WrapPanel> — elementy podrzędne w kolejności sekwencyjnej od lewej do prawej, Podziel zawartość do następnego wiersza na krawędzi pola zawierającego.</span><span class="sxs-lookup"><span data-stu-id="6cea1-210"><xref:System.Windows.Controls.WrapPanel> - Positions child elements in sequential position from left to right, breaking content to the next line at the edge of the containing box.</span></span> <span data-ttu-id="6cea1-211">Kolejne porządkowanie odbywa się sekwencyjnie od góry do dołu lub od prawej do lewej, w zależności od wartości właściwości Orientation.</span><span class="sxs-lookup"><span data-stu-id="6cea1-211">Subsequent ordering happens sequentially from top to bottom or from right to left, depending on the value of the Orientation property.</span></span>

<span data-ttu-id="6cea1-212">Każda z tych kontrolek układu obsługuje określony typ układu dla jego elementów podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="6cea1-212">Each of these layout controls supports a particular type of layout for its child elements.</span></span> <span data-ttu-id="6cea1-213">można zmienić rozmiar stron `ExpenseIt`, a każda Strona zawiera elementy ułożone w poziomie i w pionie wraz z innymi elementami.</span><span class="sxs-lookup"><span data-stu-id="6cea1-213">`ExpenseIt` pages can be resized, and each page has elements that are arranged horizontally and vertically alongside other elements.</span></span> <span data-ttu-id="6cea1-214">W tym przykładzie <xref:System.Windows.Controls.Grid> jest używany jako element układu dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="6cea1-214">In this example, the <xref:System.Windows.Controls.Grid> is used as  layout element for the application.</span></span>

> [!TIP]
> <span data-ttu-id="6cea1-215">Aby uzyskać więcej informacji na temat elementów <xref:System.Windows.Controls.Panel>, zobacz [Omówienie paneli](../controls/panels-overview.md).</span><span class="sxs-lookup"><span data-stu-id="6cea1-215">For more information about <xref:System.Windows.Controls.Panel> elements, see [Panels overview](../controls/panels-overview.md).</span></span> <span data-ttu-id="6cea1-216">Aby uzyskać więcej informacji na temat układu, zobacz [Układ](../advanced/layout.md).</span><span class="sxs-lookup"><span data-stu-id="6cea1-216">For more information about layout, see [Layout](../advanced/layout.md).</span></span>

<span data-ttu-id="6cea1-217">W tej sekcji utworzysz jednokolumnową tabelę z trzema wierszami i marginesem 10 pikseli, dodając definicje kolumn i wierszy do <xref:System.Windows.Controls.Grid> w *`ExpenseItHome.xaml`* .</span><span class="sxs-lookup"><span data-stu-id="6cea1-217">In this section, you create a single-column table with three rows and a 10-pixel margin by adding column and row definitions to the <xref:System.Windows.Controls.Grid> in *`ExpenseItHome.xaml`*.</span></span>

1. <span data-ttu-id="6cea1-218">W *`ExpenseItHome.xaml`* ustaw właściwość <xref:System.Windows.FrameworkElement.Margin%2A> dla elementu <xref:System.Windows.Controls.Grid> na wartość "10, 0, 10, 10", która odnosi się do lewego, górnego, prawego i dolnego marginesu:</span><span class="sxs-lookup"><span data-stu-id="6cea1-218">In *`ExpenseItHome.xaml`*, set the <xref:System.Windows.FrameworkElement.Margin%2A> property on the <xref:System.Windows.Controls.Grid> element to "10,0,10,10", which corresponds to left, top, right and bottom margins:</span></span>

   ```xaml
   <Grid Margin="10,0,10,10">
   ```

   > [!TIP]
   > <span data-ttu-id="6cea1-219">Możesz również ustawić wartości **marginesu** w oknie **Właściwości** , w obszarze Kategoria **układu** :</span><span class="sxs-lookup"><span data-stu-id="6cea1-219">You can also set the **Margin** values in the **Properties** window, under the **Layout** category:</span></span>
   >
   > ![Wartości marginesów w okno Właściwości](./media/properties-margin.png)

2. <span data-ttu-id="6cea1-221">Dodaj następujący kod XAML między tagami <xref:System.Windows.Controls.Grid>, aby utworzyć definicje wierszy i kolumn:</span><span class="sxs-lookup"><span data-stu-id="6cea1-221">Add the following XAML between the <xref:System.Windows.Controls.Grid> tags to create the row and column definitions:</span></span>

    [!code-xaml[ExpenseIt#8](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt3/ExpenseItHome.xaml#8)]

    <span data-ttu-id="6cea1-222"><xref:System.Windows.Controls.RowDefinition.Height%2A> dwóch wierszy jest ustawiona na <xref:System.Windows.GridLength.Auto%2A>, co oznacza, że rozmiar wierszy jest określany na podstawie zawartości w wierszach.</span><span class="sxs-lookup"><span data-stu-id="6cea1-222">The <xref:System.Windows.Controls.RowDefinition.Height%2A> of two rows is set to <xref:System.Windows.GridLength.Auto%2A>, which means that the rows are sized based on the content in the rows.</span></span> <span data-ttu-id="6cea1-223">Domyślny <xref:System.Windows.Controls.RowDefinition.Height%2A> jest <xref:System.Windows.GridUnitType.Star> rozmiar, co oznacza, że wysokość wiersza jest ważoną ilością dostępnego miejsca.</span><span class="sxs-lookup"><span data-stu-id="6cea1-223">The default <xref:System.Windows.Controls.RowDefinition.Height%2A> is <xref:System.Windows.GridUnitType.Star> sizing, which means that the row height is a weighted proportion of the available space.</span></span> <span data-ttu-id="6cea1-224">Na przykład jeśli dwa wiersze mają <xref:System.Windows.Controls.RowDefinition.Height%2A> "\*", każda z nich ma wysokość połowę dostępnego miejsca.</span><span class="sxs-lookup"><span data-stu-id="6cea1-224">For example if two rows each have a <xref:System.Windows.Controls.RowDefinition.Height%2A> of "\*", they each have a height that is half of the available space.</span></span>

    <span data-ttu-id="6cea1-225"><xref:System.Windows.Controls.Grid> powinien teraz zawierać następujący kod XAML:</span><span class="sxs-lookup"><span data-stu-id="6cea1-225">Your <xref:System.Windows.Controls.Grid> should now contain the following XAML:</span></span>

    [!code-xaml[ExpenseIt#9](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt3/ExpenseItHome.xaml#9)]

## <a name="add-controls"></a><span data-ttu-id="6cea1-226">Dodawanie kontrolek</span><span class="sxs-lookup"><span data-stu-id="6cea1-226">Add controls</span></span>

<span data-ttu-id="6cea1-227">W tej sekcji opisano aktualizowanie interfejsu użytkownika strony głównej w celu wyświetlenia listy osób, w których można wybrać jedną osobę, aby wyświetlić raport z wydatków.</span><span class="sxs-lookup"><span data-stu-id="6cea1-227">In this section, you'll update the home page UI to show a list of people, where you select one person to display their expense report.</span></span> <span data-ttu-id="6cea1-228">Formanty to obiekty UI, które umożliwiają użytkownikom współpracującie z Twoją aplikacją.</span><span class="sxs-lookup"><span data-stu-id="6cea1-228">Controls are UI objects that allow users to interact with your application.</span></span> <span data-ttu-id="6cea1-229">Aby uzyskać więcej informacji, zobacz [Controls](../controls/index.md).</span><span class="sxs-lookup"><span data-stu-id="6cea1-229">For more information, see [Controls](../controls/index.md).</span></span>

<span data-ttu-id="6cea1-230">Aby utworzyć ten interfejs użytkownika, Dodaj następujące elementy do *`ExpenseItHome.xaml`* :</span><span class="sxs-lookup"><span data-stu-id="6cea1-230">To create this UI, you'll add the following elements to *`ExpenseItHome.xaml`*:</span></span>

- <span data-ttu-id="6cea1-231"><xref:System.Windows.Controls.ListBox> (dla listy osób).</span><span class="sxs-lookup"><span data-stu-id="6cea1-231">A <xref:System.Windows.Controls.ListBox> (for the list of people).</span></span>
- <span data-ttu-id="6cea1-232"><xref:System.Windows.Controls.Label> (dla nagłówka listy).</span><span class="sxs-lookup"><span data-stu-id="6cea1-232">A <xref:System.Windows.Controls.Label> (for the list header).</span></span>
- <span data-ttu-id="6cea1-233"><xref:System.Windows.Controls.Button> (kliknij, aby wyświetlić raport wydatków dla osoby, która została wybrana na liście).</span><span class="sxs-lookup"><span data-stu-id="6cea1-233">A <xref:System.Windows.Controls.Button> (to click to view the expense report for the person that is selected in the list).</span></span>

<span data-ttu-id="6cea1-234">Każda kontrolka jest umieszczana w wierszu <xref:System.Windows.Controls.Grid> przez ustawienie <xref:System.Windows.Controls.Grid.Row%2A?displayProperty=nameWithType> dołączonej właściwości.</span><span class="sxs-lookup"><span data-stu-id="6cea1-234">Each control is placed in a row of the <xref:System.Windows.Controls.Grid> by setting the <xref:System.Windows.Controls.Grid.Row%2A?displayProperty=nameWithType> attached property.</span></span> <span data-ttu-id="6cea1-235">Aby uzyskać więcej informacji o dołączanych właściwościach, zobacz temat [dołączone właściwości przegląd](../advanced/attached-properties-overview.md).</span><span class="sxs-lookup"><span data-stu-id="6cea1-235">For more information about attached properties, see [Attached Properties Overview](../advanced/attached-properties-overview.md).</span></span>

1. <span data-ttu-id="6cea1-236">W *`ExpenseItHome.xaml`* Dodaj następujący kod XAML gdzieś między tagami <xref:System.Windows.Controls.Grid>:</span><span class="sxs-lookup"><span data-stu-id="6cea1-236">In *`ExpenseItHome.xaml`*, add the following XAML somewhere between the <xref:System.Windows.Controls.Grid> tags:</span></span>

   [!code-xaml[ExpenseIt#10](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt4/ExpenseItHome.xaml#10)]

   > [!TIP]
   > <span data-ttu-id="6cea1-237">Możesz również utworzyć kontrolki, przeciągając je z okna **przybornika** do okna projektowania, a następnie ustawiając ich właściwości w oknie **Właściwości** .</span><span class="sxs-lookup"><span data-stu-id="6cea1-237">You can also create the controls by dragging them from the **Toolbox** window onto the design window, and then setting their properties in the **Properties** window.</span></span>

2. <span data-ttu-id="6cea1-238">Skompiluj i uruchom aplikację.</span><span class="sxs-lookup"><span data-stu-id="6cea1-238">Build and run the application.</span></span>

    <span data-ttu-id="6cea1-239">Na poniższej ilustracji przedstawiono utworzone przez Ciebie formanty:</span><span class="sxs-lookup"><span data-stu-id="6cea1-239">The following illustration shows the controls you created:</span></span>

![Przykładowy zrzut ekranu ExpenseIt z listą nazw](./media/walkthrough-my-first-wpf-desktop-application/add-application-controls.png)

## <a name="add-an-image-and-a-title"></a><span data-ttu-id="6cea1-241">Dodawanie obrazu i tytułu</span><span class="sxs-lookup"><span data-stu-id="6cea1-241">Add an image and a title</span></span>

<span data-ttu-id="6cea1-242">W tej sekcji zaktualizujesz interfejs użytkownika strony głównej za pomocą obrazu i tytułu strony.</span><span class="sxs-lookup"><span data-stu-id="6cea1-242">In this section, you'll update the home page UI with an image and a page title.</span></span>

1. <span data-ttu-id="6cea1-243">W *`ExpenseItHome.xaml`* Dodaj kolejną kolumnę do <xref:System.Windows.Controls.Grid.ColumnDefinitions%2A> o stałym <xref:System.Windows.Controls.ColumnDefinition.Width%2A> 230 pikseli:</span><span class="sxs-lookup"><span data-stu-id="6cea1-243">In *`ExpenseItHome.xaml`*, add another column to the <xref:System.Windows.Controls.Grid.ColumnDefinitions%2A> with a fixed <xref:System.Windows.Controls.ColumnDefinition.Width%2A> of 230 pixels:</span></span>

    [!code-xaml[ExpenseIt#11](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseItHome.xaml?highlight=52-55)]

2. <span data-ttu-id="6cea1-244">Dodaj kolejny wiersz do <xref:System.Windows.Controls.Grid.RowDefinitions%2A>, aby uzyskać łącznie cztery wiersze:</span><span class="sxs-lookup"><span data-stu-id="6cea1-244">Add another row to the <xref:System.Windows.Controls.Grid.RowDefinitions%2A>, for a total of four rows:</span></span>

    [!code-xaml[ExpenseIt#11b](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseItHome.xaml?highlight=57-62)]

3. <span data-ttu-id="6cea1-245">Przenieś kontrolki do drugiej kolumny, ustawiając właściwość <xref:System.Windows.Controls.Grid.Column%2A?displayProperty=nameWithType> na 1 w każdej z trzech kontrolek (obramowanie, ListBox i Button).</span><span class="sxs-lookup"><span data-stu-id="6cea1-245">Move the controls to the second column by setting the <xref:System.Windows.Controls.Grid.Column%2A?displayProperty=nameWithType> property to 1 in each of the three controls (Border, ListBox, and Button).</span></span>

4. <span data-ttu-id="6cea1-246">Przenieś każdy formant w dół, zwiększając jego wartość <xref:System.Windows.Controls.Grid.Row%2A?displayProperty=nameWithType> o 1 dla każdej z trzech kontrolek (obramowanie, ListBox i Button) oraz dla elementu Border.</span><span class="sxs-lookup"><span data-stu-id="6cea1-246">Move each control down a row by incrementing its <xref:System.Windows.Controls.Grid.Row%2A?displayProperty=nameWithType> value by 1 for each of the three controls (Border, ListBox, and Button) and for the Border element.</span></span>

   <span data-ttu-id="6cea1-247">KOD XAML dla trzech kontrolek wygląda teraz następująco:</span><span class="sxs-lookup"><span data-stu-id="6cea1-247">The XAML for the three controls now looks like the following:</span></span>

    [!code-xaml[ExpenseIt#12](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#12)]

5. <span data-ttu-id="6cea1-248">Ustaw właściwość <xref:System.Windows.Controls.Panel.Background%2A?displayProperty=nameWithType> na plik obrazu *znaku wodnego* , dodając Poniższy kod XAML między tagami `<Grid>` i `</Grid>`:</span><span class="sxs-lookup"><span data-stu-id="6cea1-248">Set the <xref:System.Windows.Controls.Panel.Background%2A?displayProperty=nameWithType> property to the *watermark.png* image file, by adding the following XAML anywhere between the `<Grid>` and `</Grid>` tags:</span></span>

    [!code-xaml[ExpenseIt#14](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#14)]

6. <span data-ttu-id="6cea1-249">Przed elementem <xref:System.Windows.Controls.Border> Dodaj <xref:System.Windows.Controls.Label> z zawartością "Wyświetl raport wydatków".</span><span class="sxs-lookup"><span data-stu-id="6cea1-249">Before the <xref:System.Windows.Controls.Border> element, add a <xref:System.Windows.Controls.Label> with the content "View Expense Report".</span></span> <span data-ttu-id="6cea1-250">Ta etykieta jest tytułem strony.</span><span class="sxs-lookup"><span data-stu-id="6cea1-250">This label is the title of the page.</span></span>

    [!code-xaml[ExpenseIt#13](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#13)]

7. <span data-ttu-id="6cea1-251">Skompiluj i uruchom aplikację.</span><span class="sxs-lookup"><span data-stu-id="6cea1-251">Build and run the application.</span></span>

<span data-ttu-id="6cea1-252">Na poniższej ilustracji przedstawiono wyniki, które właśnie Dodano:</span><span class="sxs-lookup"><span data-stu-id="6cea1-252">The following illustration shows the results of what you just added:</span></span>

![Przykładowy zrzut ekranu ExpenseIt pokazujący nowe tło obrazu i tytuł strony](./media/walkthrough-my-first-wpf-desktop-application/add-application-image-title.png)

## <a name="add-code-to-handle-events"></a><span data-ttu-id="6cea1-254">Dodawanie kodu do obsługi zdarzeń</span><span class="sxs-lookup"><span data-stu-id="6cea1-254">Add code to handle events</span></span>

1. <span data-ttu-id="6cea1-255">W *`ExpenseItHome.xaml`* Dodaj procedurę obsługi zdarzeń <xref:System.Windows.Controls.Primitives.ButtonBase.Click> do elementu <xref:System.Windows.Controls.Button>.</span><span class="sxs-lookup"><span data-stu-id="6cea1-255">In *`ExpenseItHome.xaml`*, add a <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event handler to the <xref:System.Windows.Controls.Button> element.</span></span> <span data-ttu-id="6cea1-256">Aby uzyskać więcej informacji, zobacz [jak: Tworzenie prostego programu obsługi zdarzeń](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/bb675300(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="6cea1-256">For more information, see [How to: Create a simple event handler](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/bb675300(v=vs.100)).</span></span>

    [!code-xaml[ExpenseIt#15](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt6/ExpenseItHome.xaml#15)]

2. <span data-ttu-id="6cea1-257">Otwórz *`ExpenseItHome.xaml.vb`* lub *`ExpenseItHome.xaml.cs`* .</span><span class="sxs-lookup"><span data-stu-id="6cea1-257">Open *`ExpenseItHome.xaml.vb`* or *`ExpenseItHome.xaml.cs`*.</span></span>

3. <span data-ttu-id="6cea1-258">Dodaj następujący kod do klasy `ExpenseItHome`, aby dodać przycisk procedury obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="6cea1-258">Add the following code to the `ExpenseItHome` class to add a button click event handler.</span></span> <span data-ttu-id="6cea1-259">Procedura obsługi zdarzeń otwiera stronę **ExpenseReportPage** .</span><span class="sxs-lookup"><span data-stu-id="6cea1-259">The event handler opens the **ExpenseReportPage** page.</span></span>

    [!code-csharp[ExpenseIt#16](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt6/ExpenseItHome.xaml.cs#16)]
    [!code-vb[ExpenseIt#16](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt6/ExpenseItHome.xaml.vb#16)]

## <a name="create-the-ui-for-expensereportpage"></a><span data-ttu-id="6cea1-260">Tworzenie interfejsu użytkownika dla ExpenseReportPage</span><span class="sxs-lookup"><span data-stu-id="6cea1-260">Create the UI for ExpenseReportPage</span></span>

<span data-ttu-id="6cea1-261">*ExpenseReportPage. XAML* wyświetla raport wydatków dla osoby, która została wybrana na stronie **`ExpenseItHome`** .</span><span class="sxs-lookup"><span data-stu-id="6cea1-261">*ExpenseReportPage.xaml* displays the expense report for the person that's selected on the **`ExpenseItHome`** page.</span></span> <span data-ttu-id="6cea1-262">W tej sekcji utworzysz interfejs użytkownika dla **ExpenseReportPage**.</span><span class="sxs-lookup"><span data-stu-id="6cea1-262">In this section, you'll create the UI for **ExpenseReportPage**.</span></span> <span data-ttu-id="6cea1-263">Możesz również dodać kolory tła i wypełnienia do różnych elementów interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="6cea1-263">You'll also add background and fill colors to the various UI elements.</span></span>

1. <span data-ttu-id="6cea1-264">Otwórz *ExpenseReportPage. XAML*.</span><span class="sxs-lookup"><span data-stu-id="6cea1-264">Open *ExpenseReportPage.xaml*.</span></span>

2. <span data-ttu-id="6cea1-265">Dodaj następujący kod XAML między tagami <xref:System.Windows.Controls.Grid>:</span><span class="sxs-lookup"><span data-stu-id="6cea1-265">Add the following XAML between the <xref:System.Windows.Controls.Grid> tags:</span></span>

    [!code-xaml[ExpenseIt#17](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt6/ExpenseReportPage.xaml#17)]

    <span data-ttu-id="6cea1-266">Ten interfejs użytkownika jest podobny do *`ExpenseItHome.xaml`* , z wyjątkiem tego, że dane raportu są wyświetlane w <xref:System.Windows.Controls.DataGrid>.</span><span class="sxs-lookup"><span data-stu-id="6cea1-266">This UI is similar to *`ExpenseItHome.xaml`*, except the report data is displayed in a <xref:System.Windows.Controls.DataGrid>.</span></span>

3. <span data-ttu-id="6cea1-267">Skompiluj i uruchom aplikację.</span><span class="sxs-lookup"><span data-stu-id="6cea1-267">Build and run the application.</span></span>

4. <span data-ttu-id="6cea1-268">Wybierz przycisk **Wyświetl** .</span><span class="sxs-lookup"><span data-stu-id="6cea1-268">Select the **View** button.</span></span>

    <span data-ttu-id="6cea1-269">Zostanie wyświetlona strona raport o wydatkach.</span><span class="sxs-lookup"><span data-stu-id="6cea1-269">The expense report page appears.</span></span> <span data-ttu-id="6cea1-270">Zauważ również, że przycisk nawigacji wstecznej jest włączony.</span><span class="sxs-lookup"><span data-stu-id="6cea1-270">Also notice that the back navigation button is enabled.</span></span>

<span data-ttu-id="6cea1-271">Na poniższej ilustracji przedstawiono elementy interfejsu użytkownika dodane do *ExpenseReportPage. XAML*.</span><span class="sxs-lookup"><span data-stu-id="6cea1-271">The following illustration shows the UI elements added to *ExpenseReportPage.xaml*.</span></span>

![Przykładowy zrzut ekranu ExpenseIt przedstawiający interfejs użytkownika, który został właśnie utworzony dla ExpenseReportPage.](./media/walkthrough-my-first-wpf-desktop-application/create-application-ui.png)

## <a name="style-controls"></a><span data-ttu-id="6cea1-273">Kontrolki stylu</span><span class="sxs-lookup"><span data-stu-id="6cea1-273">Style controls</span></span>

<span data-ttu-id="6cea1-274">Wygląd różnych elementów jest często taki sam dla wszystkich elementów tego samego typu w interfejsie użytkownika.</span><span class="sxs-lookup"><span data-stu-id="6cea1-274">The appearance of various elements is often the same for all elements of the same type in a UI.</span></span> <span data-ttu-id="6cea1-275">Interfejs użytkownika używa [stylów](../controls/styling-and-templating.md) , aby można było używać ich w wielu elementach.</span><span class="sxs-lookup"><span data-stu-id="6cea1-275">UI uses [styles](../controls/styling-and-templating.md) to make appearances reusable across multiple elements.</span></span> <span data-ttu-id="6cea1-276">Możliwość ponownego wykorzystania stylów ułatwia tworzenie i zarządzanie XAML.</span><span class="sxs-lookup"><span data-stu-id="6cea1-276">The reusability of styles helps to simplify XAML creation and management.</span></span> <span data-ttu-id="6cea1-277">Ta sekcja zastępuje atrybuty dla elementu, które zostały zdefiniowane w poprzednich krokach ze stylami.</span><span class="sxs-lookup"><span data-stu-id="6cea1-277">This section replaces the per-element attributes that were defined in previous steps with styles.</span></span>

1. <span data-ttu-id="6cea1-278">Otwórz *aplikację Application. XAML* lub *App. XAML*.</span><span class="sxs-lookup"><span data-stu-id="6cea1-278">Open *Application.xaml* or *App.xaml*.</span></span>

2. <span data-ttu-id="6cea1-279">Dodaj następujący kod XAML między tagami <xref:System.Windows.Application.Resources%2A?displayProperty=nameWithType>:</span><span class="sxs-lookup"><span data-stu-id="6cea1-279">Add the following XAML between the <xref:System.Windows.Application.Resources%2A?displayProperty=nameWithType> tags:</span></span>

    [!code-xaml[ExpenseIt#18](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt7/App.xaml#18)]

    <span data-ttu-id="6cea1-280">Ten kod XAML dodaje następujące style:</span><span class="sxs-lookup"><span data-stu-id="6cea1-280">This XAML adds the following styles:</span></span>

    - <span data-ttu-id="6cea1-281">`headerTextStyle`: Formatowanie tytułu strony <xref:System.Windows.Controls.Label>.</span><span class="sxs-lookup"><span data-stu-id="6cea1-281">`headerTextStyle`: To format the page title <xref:System.Windows.Controls.Label>.</span></span>

    - <span data-ttu-id="6cea1-282">`labelStyle`: Aby sformatować kontrolki <xref:System.Windows.Controls.Label>.</span><span class="sxs-lookup"><span data-stu-id="6cea1-282">`labelStyle`: To format the <xref:System.Windows.Controls.Label> controls.</span></span>

    - <span data-ttu-id="6cea1-283">`columnHeaderStyle`: Aby sformatować <xref:System.Windows.Controls.Primitives.DataGridColumnHeader>.</span><span class="sxs-lookup"><span data-stu-id="6cea1-283">`columnHeaderStyle`: To format the <xref:System.Windows.Controls.Primitives.DataGridColumnHeader>.</span></span>

    - <span data-ttu-id="6cea1-284">`listHeaderStyle`: Aby sformatować kontrolki nagłówka listy <xref:System.Windows.Controls.Border>.</span><span class="sxs-lookup"><span data-stu-id="6cea1-284">`listHeaderStyle`: To format the list header <xref:System.Windows.Controls.Border> controls.</span></span>

    - <span data-ttu-id="6cea1-285">`listHeaderTextStyle`: Aby sformatować nagłówek listy <xref:System.Windows.Controls.Label>.</span><span class="sxs-lookup"><span data-stu-id="6cea1-285">`listHeaderTextStyle`: To format the list header <xref:System.Windows.Controls.Label>.</span></span>

    - <span data-ttu-id="6cea1-286">`buttonStyle`: Aby sformatować <xref:System.Windows.Controls.Button> w `ExpenseItHome.xaml`.</span><span class="sxs-lookup"><span data-stu-id="6cea1-286">`buttonStyle`: To format the <xref:System.Windows.Controls.Button> on `ExpenseItHome.xaml`.</span></span>

    <span data-ttu-id="6cea1-287">Należy zauważyć, że style są zasobami i elementami podrzędnymi elementu właściwości <xref:System.Windows.Application.Resources%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="6cea1-287">Notice that the styles are resources and children of the <xref:System.Windows.Application.Resources%2A?displayProperty=nameWithType> property element.</span></span> <span data-ttu-id="6cea1-288">W tej lokalizacji style są stosowane do wszystkich elementów w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="6cea1-288">In this location, the styles are applied to all the elements in an application.</span></span> <span data-ttu-id="6cea1-289">Aby zapoznać się z przykładem użycia zasobów w aplikacji .NET, zobacz [Korzystanie z zasobów aplikacji](../advanced/how-to-use-application-resources.md).</span><span class="sxs-lookup"><span data-stu-id="6cea1-289">For an example of using resources in a .NET app, see [Use Application Resources](../advanced/how-to-use-application-resources.md).</span></span>

3. <span data-ttu-id="6cea1-290">W *`ExpenseItHome.xaml`* Zastąp wszystkie elementy <xref:System.Windows.Controls.Grid> następującym XAML:</span><span class="sxs-lookup"><span data-stu-id="6cea1-290">In *`ExpenseItHome.xaml`*, replace everything between the <xref:System.Windows.Controls.Grid> elements with the following XAML:</span></span>

    [!code-xaml[ExpenseIt#19](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt7/ExpenseItHome.xaml#19)]

    <span data-ttu-id="6cea1-291">Właściwości, takie jak <xref:System.Windows.VerticalAlignment> i <xref:System.Windows.Media.FontFamily> definiujące wygląd poszczególnych kontrolek, są usuwane i zastępowane przez zastosowanie stylów.</span><span class="sxs-lookup"><span data-stu-id="6cea1-291">The properties such as <xref:System.Windows.VerticalAlignment> and <xref:System.Windows.Media.FontFamily> that define the look of each control are removed and replaced by applying the styles.</span></span> <span data-ttu-id="6cea1-292">Na przykład `headerTextStyle` jest zastosowana do <xref:System.Windows.Controls.Label>"Wyświetl raport wydatków".</span><span class="sxs-lookup"><span data-stu-id="6cea1-292">For example, the `headerTextStyle` is applied to the "View Expense Report" <xref:System.Windows.Controls.Label>.</span></span>

4. <span data-ttu-id="6cea1-293">Otwórz *ExpenseReportPage. XAML*.</span><span class="sxs-lookup"><span data-stu-id="6cea1-293">Open *ExpenseReportPage.xaml*.</span></span>

5. <span data-ttu-id="6cea1-294">Zastąp wszystkie elementy <xref:System.Windows.Controls.Grid> następującym XAML:</span><span class="sxs-lookup"><span data-stu-id="6cea1-294">Replace everything between the <xref:System.Windows.Controls.Grid> elements with the following XAML:</span></span>

    [!code-xaml[ExpenseIt#20](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt7/ExpenseReportPage.xaml#20)]

    <span data-ttu-id="6cea1-295">Ten kod XAML dodaje style do <xref:System.Windows.Controls.Label> i <xref:System.Windows.Controls.Border> elementów.</span><span class="sxs-lookup"><span data-stu-id="6cea1-295">This XAML adds styles to the <xref:System.Windows.Controls.Label> and <xref:System.Windows.Controls.Border> elements.</span></span>

6. <span data-ttu-id="6cea1-296">Skompiluj i uruchom aplikację.</span><span class="sxs-lookup"><span data-stu-id="6cea1-296">Build and run the application.</span></span> <span data-ttu-id="6cea1-297">Wygląd okna jest taki sam jak poprzednio.</span><span class="sxs-lookup"><span data-stu-id="6cea1-297">The window appearance is the same as previously.</span></span>

    ![ExpenseIt Przykładowy zrzut ekranu z tym samym wyglądem, jak w ostatniej sekcji.](./media/walkthrough-my-first-wpf-desktop-application/create-application-ui.png)

7. <span data-ttu-id="6cea1-299">Zamknij aplikację, aby powrócić do programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="6cea1-299">Close the application to return to Visual Studio.</span></span>

## <a name="bind-data-to-a-control"></a><span data-ttu-id="6cea1-300">Powiąż dane z kontrolką</span><span class="sxs-lookup"><span data-stu-id="6cea1-300">Bind data to a control</span></span>

<span data-ttu-id="6cea1-301">W tej sekcji utworzysz dane XML powiązane z różnymi kontrolkami.</span><span class="sxs-lookup"><span data-stu-id="6cea1-301">In this section, you'll create the XML data that is bound to various controls.</span></span>

1. <span data-ttu-id="6cea1-302">W *`ExpenseItHome.xaml`* po otwarciu elementu <xref:System.Windows.Controls.Grid> Dodaj następujący kod XAML, aby utworzyć <xref:System.Windows.Data.XmlDataProvider> zawierający dane dla każdej osoby:</span><span class="sxs-lookup"><span data-stu-id="6cea1-302">In *`ExpenseItHome.xaml`*, after the opening <xref:System.Windows.Controls.Grid> element, add the following XAML to create an <xref:System.Windows.Data.XmlDataProvider> that contains the data for each person:</span></span>

    [!code-xaml[ExpenseIt#23](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml?range=13,16-40,49)]

    <span data-ttu-id="6cea1-303">Dane są tworzone jako zasób <xref:System.Windows.Controls.Grid>.</span><span class="sxs-lookup"><span data-stu-id="6cea1-303">The data is created as a <xref:System.Windows.Controls.Grid> resource.</span></span> <span data-ttu-id="6cea1-304">Zwykle te dane zostałyby załadowane jako plik, ale dla uproszczenia dane są dodawane wewnętrznie.</span><span class="sxs-lookup"><span data-stu-id="6cea1-304">Normally this data would be loaded as a file, but for simplicity the data is added inline.</span></span>

2. <span data-ttu-id="6cea1-305">W `<Grid.Resources>` elementu Dodaj następujący element `<xref:System.Windows.DataTemplate>`, który definiuje sposób wyświetlania danych w <xref:System.Windows.Controls.ListBox>, po elemencie `<XmlDataProvider>`:</span><span class="sxs-lookup"><span data-stu-id="6cea1-305">Within the `<Grid.Resources>` element, add the following `<xref:System.Windows.DataTemplate>` element, which defines how to display the data in the <xref:System.Windows.Controls.ListBox>, after the `<XmlDataProvider>` element:</span></span>

    [!code-xaml[ExpenseIt#24](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml?range=13,43-46,49)]

    <span data-ttu-id="6cea1-306">Aby uzyskać więcej informacji na temat szablonów danych, zobacz [tworzenia szablonów danych — omówienie](../data/data-templating-overview.md).</span><span class="sxs-lookup"><span data-stu-id="6cea1-306">For more information about data templates, see [Data templating overview](../data/data-templating-overview.md).</span></span>

3. <span data-ttu-id="6cea1-307">Zastąp istniejące <xref:System.Windows.Controls.ListBox> następującym XAML:</span><span class="sxs-lookup"><span data-stu-id="6cea1-307">Replace the existing <xref:System.Windows.Controls.ListBox> with the following XAML:</span></span>

    [!code-xaml[ExpenseIt#25](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml#25)]

    <span data-ttu-id="6cea1-308">Ten kod XAML wiąże <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> Właściwość <xref:System.Windows.Controls.ListBox> ze źródłem danych i stosuje szablon danych jako <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A>.</span><span class="sxs-lookup"><span data-stu-id="6cea1-308">This XAML binds the <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> property of the <xref:System.Windows.Controls.ListBox> to the data source and applies the data template as the <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A>.</span></span>

## <a name="connect-data-to-controls"></a><span data-ttu-id="6cea1-309">Łączenie danych z kontrolkami</span><span class="sxs-lookup"><span data-stu-id="6cea1-309">Connect data to controls</span></span>

<span data-ttu-id="6cea1-310">Następnie dodasz kod w celu pobrania nazwy wybranej na stronie **`ExpenseItHome`** i przekazania jej do konstruktora **ExpenseReportPage**.</span><span class="sxs-lookup"><span data-stu-id="6cea1-310">Next, you'll add code to retrieve the name that's selected on the **`ExpenseItHome`** page and pass it to the constructor of **ExpenseReportPage**.</span></span> <span data-ttu-id="6cea1-311">**ExpenseReportPage** ustawia swój kontekst danych z elementem zakończonym, co oznacza, że kontrolki zdefiniowane w *ExpenseReportPage. XAML* są powiązane z.</span><span class="sxs-lookup"><span data-stu-id="6cea1-311">**ExpenseReportPage** sets its data context with the passed item, which is what the controls defined in *ExpenseReportPage.xaml* bind to.</span></span>

1. <span data-ttu-id="6cea1-312">Otwórz *ExpenseReportPage. XAML. vb* lub *ExpenseReportPage.XAML.cs*.</span><span class="sxs-lookup"><span data-stu-id="6cea1-312">Open *ExpenseReportPage.xaml.vb* or *ExpenseReportPage.xaml.cs*.</span></span>

2. <span data-ttu-id="6cea1-313">Dodaj Konstruktor, który pobiera obiekt, aby można było przekazać dane raportu wydatków wybranej osoby.</span><span class="sxs-lookup"><span data-stu-id="6cea1-313">Add a constructor that takes an object so you can pass the expense report data of the selected person.</span></span>

    [!code-csharp[ExpenseIt#26](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseReportPage.xaml.cs#26)]
    [!code-vb[ExpenseIt#26](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt8/ExpenseReportPage.xaml.vb#26)]

3. <span data-ttu-id="6cea1-314">Otwórz *`ExpenseItHome.xaml.vb`* lub *`ExpenseItHome.xaml.cs`* .</span><span class="sxs-lookup"><span data-stu-id="6cea1-314">Open *`ExpenseItHome.xaml.vb`* or *`ExpenseItHome.xaml.cs`*.</span></span>

4. <span data-ttu-id="6cea1-315">Zmień procedurę obsługi zdarzeń <xref:System.Windows.Controls.Primitives.ButtonBase.Click>, aby wywoływać nowego konstruktora przekazującego dane raportu wydatków wybranej osoby.</span><span class="sxs-lookup"><span data-stu-id="6cea1-315">Change the <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event handler to call the new constructor passing the expense report data of the selected person.</span></span>

    [!code-csharp[ExpenseIt#27](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml.cs#27)]
    [!code-vb[ExpenseIt#27](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt8/ExpenseItHome.xaml.vb#27)]

## <a name="style-data-with-data-templates"></a><span data-ttu-id="6cea1-316">Dane stylu z szablonami danych</span><span class="sxs-lookup"><span data-stu-id="6cea1-316">Style data with data templates</span></span>

<span data-ttu-id="6cea1-317">W tej sekcji należy zaktualizować interfejs użytkownika dla każdego elementu na listach powiązanych z danymi przy użyciu szablonów danych.</span><span class="sxs-lookup"><span data-stu-id="6cea1-317">In this section, you'll update the UI for each item in the data-bound lists by using data templates.</span></span>

1. <span data-ttu-id="6cea1-318">Otwórz *ExpenseReportPage. XAML*.</span><span class="sxs-lookup"><span data-stu-id="6cea1-318">Open *ExpenseReportPage.xaml*.</span></span>

2. <span data-ttu-id="6cea1-319">Powiąż zawartość <xref:System.Windows.Controls.Label> elementów "name" i "Department" z odpowiednią właściwością źródła danych.</span><span class="sxs-lookup"><span data-stu-id="6cea1-319">Bind the content of the "Name" and "Department" <xref:System.Windows.Controls.Label> elements to the appropriate data source property.</span></span> <span data-ttu-id="6cea1-320">Aby uzyskać więcej informacji na temat powiązania danych, zobacz temat [powiązanie danych — omówienie](../../../desktop-wpf/data/data-binding-overview.md).</span><span class="sxs-lookup"><span data-stu-id="6cea1-320">For more information about data binding, see [Data binding overview](../../../desktop-wpf/data/data-binding-overview.md).</span></span>

    [!code-xaml[ExpenseIt#31](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseReportPage.xaml#31)]

3. <span data-ttu-id="6cea1-321">Po otwarciu elementu <xref:System.Windows.Controls.Grid> należy dodać następujące szablony danych, które definiują sposób wyświetlania danych raportu wydatków:</span><span class="sxs-lookup"><span data-stu-id="6cea1-321">After the opening <xref:System.Windows.Controls.Grid> element, add the following data templates, which define how to display the expense report data:</span></span>

    [!code-xaml[ExpenseIt#30](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseReportPage.xaml#30)]

4. <span data-ttu-id="6cea1-322">Zastąp <xref:System.Windows.Controls.DataGridTextColumn> elementami <xref:System.Windows.Controls.DataGridTemplateColumn> pod elementem <xref:System.Windows.Controls.DataGrid> i Zastosuj do nich szablony.</span><span class="sxs-lookup"><span data-stu-id="6cea1-322">Replace the <xref:System.Windows.Controls.DataGridTextColumn> elements with <xref:System.Windows.Controls.DataGridTemplateColumn> under the <xref:System.Windows.Controls.DataGrid> element and apply the templates to them.</span></span>

    [!code-xaml[ExpenseIt#32](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseReportPage.xaml#32)]

5. <span data-ttu-id="6cea1-323">Skompiluj i uruchom aplikację.</span><span class="sxs-lookup"><span data-stu-id="6cea1-323">Build and run the application.</span></span>

6. <span data-ttu-id="6cea1-324">Wybierz osobę, a następnie wybierz przycisk **Wyświetl** .</span><span class="sxs-lookup"><span data-stu-id="6cea1-324">Select a person and then select the **View** button.</span></span>

<span data-ttu-id="6cea1-325">Na poniższej ilustracji przedstawiono obie strony aplikacji `ExpenseIt` z kontrolkami, układem, stylami, powiązaniem danych i szablonami danych:</span><span class="sxs-lookup"><span data-stu-id="6cea1-325">The following illustration shows both pages of the `ExpenseIt` application with controls, layout, styles, data binding, and data templates applied:</span></span>

![Obie strony aplikacji pokazują listę nazw i raport wydatków.](./media/walkthrough-my-first-wpf-desktop-application/application-data-templates.png)

> [!NOTE]
> <span data-ttu-id="6cea1-327">Ten przykład pokazuje konkretną funkcję WPF i nie jest zgodny ze wszystkimi najlepszymi rozwiązaniami dotyczącymi takich elementów, jak zabezpieczenia, lokalizacja i ułatwienia dostępu.</span><span class="sxs-lookup"><span data-stu-id="6cea1-327">This sample demonstrates a specific feature of WPF and doesn't follow all best practices for things like security, localization, and accessibility.</span></span> <span data-ttu-id="6cea1-328">Aby uzyskać kompleksową obsługę WPF i najlepszych rozwiązań programistycznych dotyczących projektowania aplikacji .NET, zobacz następujące tematy:</span><span class="sxs-lookup"><span data-stu-id="6cea1-328">For comprehensive coverage of WPF and the .NET app development best practices, see the following topics:</span></span>
>
> - [<span data-ttu-id="6cea1-329">Ułatwienia dostępu</span><span class="sxs-lookup"><span data-stu-id="6cea1-329">Accessibility</span></span>](../../ui-automation/accessibility-best-practices.md)
> - [<span data-ttu-id="6cea1-330">Zabezpieczenia</span><span class="sxs-lookup"><span data-stu-id="6cea1-330">Security</span></span>](../security-wpf.md)
> - [<span data-ttu-id="6cea1-331">Globalizacja i lokalizacja WPF</span><span class="sxs-lookup"><span data-stu-id="6cea1-331">WPF globalization and localization</span></span>](../advanced/wpf-globalization-and-localization-overview.md)
> - [<span data-ttu-id="6cea1-332">Wydajność WPF</span><span class="sxs-lookup"><span data-stu-id="6cea1-332">WPF performance</span></span>](../advanced/optimizing-wpf-application-performance.md)

## <a name="next-steps"></a><span data-ttu-id="6cea1-333">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="6cea1-333">Next steps</span></span>

<span data-ttu-id="6cea1-334">W tym instruktażu przedstawiono kilka technik tworzenia interfejsu użytkownika przy użyciu Windows Presentation Foundation (WPF).</span><span class="sxs-lookup"><span data-stu-id="6cea1-334">In this walkthrough you learned a number of techniques for creating a UI using Windows Presentation Foundation (WPF).</span></span> <span data-ttu-id="6cea1-335">Należy teraz dysponować podstawową wiedzą na temat bloków konstrukcyjnych aplikacji .NET powiązanych z danymi.</span><span class="sxs-lookup"><span data-stu-id="6cea1-335">You should now have a basic understanding of the building blocks of a data-bound .NET app.</span></span> <span data-ttu-id="6cea1-336">Aby uzyskać więcej informacji na temat architektury WPF i modeli programowania, zobacz następujące tematy:</span><span class="sxs-lookup"><span data-stu-id="6cea1-336">For more information about the WPF architecture and programming models, see the following topics:</span></span>

- [<span data-ttu-id="6cea1-337">Architektura WPF</span><span class="sxs-lookup"><span data-stu-id="6cea1-337">WPF architecture</span></span>](../advanced/wpf-architecture.md)
- [<span data-ttu-id="6cea1-338">Przegląd XAML (WPF)</span><span class="sxs-lookup"><span data-stu-id="6cea1-338">XAML overview (WPF)</span></span>](../advanced/xaml-overview-wpf.md)
- [<span data-ttu-id="6cea1-339">Przegląd właściwości zależności</span><span class="sxs-lookup"><span data-stu-id="6cea1-339">Dependency properties overview</span></span>](../advanced/dependency-properties-overview.md)
- [<span data-ttu-id="6cea1-340">Układ</span><span class="sxs-lookup"><span data-stu-id="6cea1-340">Layout</span></span>](../advanced/layout.md)

<span data-ttu-id="6cea1-341">Aby uzyskać więcej informacji na temat tworzenia aplikacji, zobacz następujące tematy:</span><span class="sxs-lookup"><span data-stu-id="6cea1-341">For more information about creating applications, see the following topics:</span></span>

- [<span data-ttu-id="6cea1-342">Opracowywanie aplikacji</span><span class="sxs-lookup"><span data-stu-id="6cea1-342">Application development</span></span>](../app-development/index.md)
- [<span data-ttu-id="6cea1-343">Kontrolki</span><span class="sxs-lookup"><span data-stu-id="6cea1-343">Controls</span></span>](../controls/index.md)
- [<span data-ttu-id="6cea1-344">Przegląd powiązań danych</span><span class="sxs-lookup"><span data-stu-id="6cea1-344">Data binding overview</span></span>](../../../desktop-wpf/data/data-binding-overview.md)
- [<span data-ttu-id="6cea1-345">Grafika i multimedia</span><span class="sxs-lookup"><span data-stu-id="6cea1-345">Graphics and multimedia</span></span>](../graphics-multimedia/index.md)
- [<span data-ttu-id="6cea1-346">Dokumenty w WPF</span><span class="sxs-lookup"><span data-stu-id="6cea1-346">Documents in WPF</span></span>](../advanced/documents-in-wpf.md)

## <a name="see-also"></a><span data-ttu-id="6cea1-347">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6cea1-347">See also</span></span>

- [<span data-ttu-id="6cea1-348">Panele — Omówienie</span><span class="sxs-lookup"><span data-stu-id="6cea1-348">Panels overview</span></span>](../controls/panels-overview.md)
- [<span data-ttu-id="6cea1-349">Tworzenia szablonów danych — omówienie</span><span class="sxs-lookup"><span data-stu-id="6cea1-349">Data templating overview</span></span>](../data/data-templating-overview.md)
- [<span data-ttu-id="6cea1-350">Tworzenie aplikacji WPF</span><span class="sxs-lookup"><span data-stu-id="6cea1-350">Build a WPF application</span></span>](../app-development/building-a-wpf-application-wpf.md)
- [<span data-ttu-id="6cea1-351">Style i szablony</span><span class="sxs-lookup"><span data-stu-id="6cea1-351">Styles and templates</span></span>](../controls/styles-and-templates.md)
