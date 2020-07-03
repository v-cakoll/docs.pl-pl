---
title: Tworzenie pierwszej aplikacji WPF w programie Visual Studio 2019 — .NET Framework
titleSuffix: ''
description: Opracowywanie aplikacji klasycznych Windows Presentation Foundation (WPF), która zawiera elementy wspólne dla większości aplikacji WPF.
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
ms.openlocfilehash: c9af988bcf291325b11df4fd22827b47090c0b48
ms.sourcegitcommit: b6a1869f97a37f11a68c90afde1a520a6887dcbc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/02/2020
ms.locfileid: "85853885"
---
# <a name="tutorial-create-your-first-wpf-application-in-visual-studio-2019"></a><span data-ttu-id="dee0a-103">Samouczek: Tworzenie pierwszej aplikacji WPF w programie Visual Studio 2019</span><span class="sxs-lookup"><span data-stu-id="dee0a-103">Tutorial: Create your first WPF application in Visual Studio 2019</span></span>

<span data-ttu-id="dee0a-104">W tym artykule przedstawiono sposób tworzenia aplikacji klasycznych Windows Presentation Foundation (WPF), która zawiera elementy, które są wspólne dla większości aplikacji WPF: znaczniki Extensible Application Markup Language (XAML), powiązane z kodem, definicje aplikacji, formanty, układ, powiązanie danych i style.</span><span class="sxs-lookup"><span data-stu-id="dee0a-104">This article shows you how to develop a Windows Presentation Foundation (WPF) desktop application that includes the elements that are common to most WPF applications: Extensible Application Markup Language (XAML) markup, code-behind, application definitions, controls, layout, data binding, and styles.</span></span> <span data-ttu-id="dee0a-105">Aby opracować aplikację, użyjesz programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="dee0a-105">To develop the application, you'll use Visual Studio.</span></span>

<span data-ttu-id="dee0a-106">Ten samouczek zawiera informacje na temat wykonywania następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="dee0a-106">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="dee0a-107">Utwórz projekt WPF.</span><span class="sxs-lookup"><span data-stu-id="dee0a-107">Create a WPF project.</span></span>
> - <span data-ttu-id="dee0a-108">Użyj języka XAML, aby zaprojektować wygląd interfejsu użytkownika aplikacji.</span><span class="sxs-lookup"><span data-stu-id="dee0a-108">Use XAML to design the appearance of the application's user interface (UI).</span></span>
> - <span data-ttu-id="dee0a-109">Napisz kod, aby skompilować zachowanie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="dee0a-109">Write code to build the application's behavior.</span></span>
> - <span data-ttu-id="dee0a-110">Utwórz definicję aplikacji w celu zarządzania aplikacją.</span><span class="sxs-lookup"><span data-stu-id="dee0a-110">Create an application definition to manage the application.</span></span>
> - <span data-ttu-id="dee0a-111">Dodaj kontrolki i Utwórz układ, aby utworzyć interfejs użytkownika aplikacji.</span><span class="sxs-lookup"><span data-stu-id="dee0a-111">Add controls and create the layout to compose the application UI.</span></span>
> - <span data-ttu-id="dee0a-112">Tworzenie stylów dla spójnego wyglądu w całym interfejsie użytkownika aplikacji.</span><span class="sxs-lookup"><span data-stu-id="dee0a-112">Create styles for a consistent appearance throughout the application's UI.</span></span>
> - <span data-ttu-id="dee0a-113">Powiąż interfejs użytkownika z danymi, zarówno w celu wypełnienia interfejsu użytkownika z danych, jak i zachowania synchronizacji danych i interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="dee0a-113">Bind the UI to data, both to populate the UI from data and to keep the data and UI synchronized.</span></span>

<span data-ttu-id="dee0a-114">Na końcu samouczka utworzysz autonomiczną aplikację systemu Windows, która umożliwia użytkownikom wyświetlanie raportów wydatków dla wybranych osób.</span><span class="sxs-lookup"><span data-stu-id="dee0a-114">By the end of the tutorial, you'll have built a standalone Windows application that allows users to view expense reports for selected people.</span></span> <span data-ttu-id="dee0a-115">Aplikacja składa się z kilku stron WPF, które są hostowane w oknie stylu przeglądarki.</span><span class="sxs-lookup"><span data-stu-id="dee0a-115">The application is composed of several WPF pages that are hosted in a browser-style window.</span></span>

> [!TIP]
> <span data-ttu-id="dee0a-116">Przykładowy kod, który jest używany w tym samouczku, jest dostępny dla Visual Basic i C# w [samouczku przykładowy kod aplikacji WPF](https://github.com/Microsoft/WPF-Samples/tree/master/Getting%20Started/WalkthroughFirstWPFApp).</span><span class="sxs-lookup"><span data-stu-id="dee0a-116">The sample code that is used in this tutorial is available for both Visual Basic and C# at [Tutorial WPF App Sample Code](https://github.com/Microsoft/WPF-Samples/tree/master/Getting%20Started/WalkthroughFirstWPFApp).</span></span>
>
> <span data-ttu-id="dee0a-117">Można przełączać język kodu przykładowego kodu między C# i Visual Basic przy użyciu selektora języka znajdującego się w górnej części tej strony.</span><span class="sxs-lookup"><span data-stu-id="dee0a-117">You can toggle the code language of the sample code between C# and Visual Basic by using the language selector on top of this page.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="dee0a-118">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="dee0a-118">Prerequisites</span></span>

- <span data-ttu-id="dee0a-119">[Program Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) z zainstalowanym obciążeniem **programowania programu .NET Desktop** .</span><span class="sxs-lookup"><span data-stu-id="dee0a-119">[Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) with the **.NET desktop development** workload installed.</span></span>

   <span data-ttu-id="dee0a-120">Aby uzyskać więcej informacji na temat instalowania najnowszej wersji programu Visual Studio, zobacz [Instalowanie programu Visual Studio](/visualstudio/install/install-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="dee0a-120">For more information about installing the latest version of Visual Studio, see [Install Visual Studio](/visualstudio/install/install-visual-studio).</span></span>

## <a name="create-the-application-project"></a><span data-ttu-id="dee0a-121">Tworzenie projektu aplikacji</span><span class="sxs-lookup"><span data-stu-id="dee0a-121">Create the application project</span></span>

<span data-ttu-id="dee0a-122">Pierwszym krokiem jest utworzenie infrastruktury aplikacji, która obejmuje definicję aplikacji, dwie strony i obraz.</span><span class="sxs-lookup"><span data-stu-id="dee0a-122">The first step is to create the application infrastructure, which includes an application definition, two pages, and an image.</span></span>

1. <span data-ttu-id="dee0a-123">Utwórz nowy projekt aplikacji WPF w Visual Basic lub Visual C# o nazwie **`ExpenseIt`** :</span><span class="sxs-lookup"><span data-stu-id="dee0a-123">Create a new WPF Application project in Visual Basic or Visual C# named **`ExpenseIt`**:</span></span>

   1. <span data-ttu-id="dee0a-124">Otwórz program Visual Studio i wybierz pozycję **Utwórz nowy projekt** w menu **wprowadzenie** .</span><span class="sxs-lookup"><span data-stu-id="dee0a-124">Open Visual Studio and select **Create a new project** under the **Get started** menu.</span></span>

      <span data-ttu-id="dee0a-125">Zostanie otwarte okno dialogowe **Tworzenie nowego projektu** .</span><span class="sxs-lookup"><span data-stu-id="dee0a-125">The **Create a new project** dialog opens.</span></span>

   2. <span data-ttu-id="dee0a-126">Z listy rozwijanej **Język** wybierz opcję **C#** lub **Visual Basic**.</span><span class="sxs-lookup"><span data-stu-id="dee0a-126">In the **Language** dropdown, select either **C#** or **Visual Basic**.</span></span>

   3. <span data-ttu-id="dee0a-127">Wybierz szablon **Aplikacja WPF (.NET Framework)** , a następnie wybierz przycisk **dalej**.</span><span class="sxs-lookup"><span data-stu-id="dee0a-127">Select the **WPF App (.NET Framework)** template and then select **Next**.</span></span>

      ![Okno dialogowe Tworzenie nowego projektu](./media/walkthrough-my-first-wpf-desktop-application/create-new-project-dialog.png)

      <span data-ttu-id="dee0a-129">Zostanie otwarte okno dialogowe **Konfigurowanie nowego projektu** .</span><span class="sxs-lookup"><span data-stu-id="dee0a-129">The **Configure your new project** dialog opens.</span></span>

   4. <span data-ttu-id="dee0a-130">Wprowadź nazwę projektu **`ExpenseIt`** , a następnie wybierz pozycję **Utwórz**.</span><span class="sxs-lookup"><span data-stu-id="dee0a-130">Enter the project name **`ExpenseIt`** and then select **Create**.</span></span>

      ![Okno dialogowe Konfigurowanie nowego projektu](./media/walkthrough-my-first-wpf-desktop-application/configure-new-project-dialog.png)

      <span data-ttu-id="dee0a-132">Program Visual Studio tworzy projekt i otwiera projektanta dla domyślnego okna aplikacji o nazwie **MainWindow. XAML**.</span><span class="sxs-lookup"><span data-stu-id="dee0a-132">Visual Studio creates the project and opens the designer for the default application window named **MainWindow.xaml**.</span></span>

2. <span data-ttu-id="dee0a-133">Otwórz *aplikację Application. XAML* (Visual Basic) lub *App. XAML* (C#).</span><span class="sxs-lookup"><span data-stu-id="dee0a-133">Open *Application.xaml* (Visual Basic) or *App.xaml* (C#).</span></span>

    <span data-ttu-id="dee0a-134">Ten plik XAML definiuje aplikację WPF i wszystkie zasoby aplikacji.</span><span class="sxs-lookup"><span data-stu-id="dee0a-134">This XAML file defines a WPF application and any application resources.</span></span> <span data-ttu-id="dee0a-135">Ten plik jest również używany do określenia interfejsu użytkownika (w tym przypadku *MainWindow. XAML*), który jest automatycznie wyświetlany podczas uruchamiania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="dee0a-135">You also use this file to specify the UI, in this case *MainWindow.xaml*, that automatically shows when the application starts.</span></span>

    <span data-ttu-id="dee0a-136">KOD XAML powinien wyglądać następująco w Visual Basic:</span><span class="sxs-lookup"><span data-stu-id="dee0a-136">Your XAML should look like the following in Visual Basic:</span></span>

    [!code-xaml[ExpenseIt#1_A](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/Application.xaml#1_a)]

    <span data-ttu-id="dee0a-137">I podobne do następujących w języku C#:</span><span class="sxs-lookup"><span data-stu-id="dee0a-137">And like the following in C#:</span></span>

    [!code-xaml[ExpenseIt#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/App.xaml#1)]

3. <span data-ttu-id="dee0a-138">Otwórz *MainWindow. XAML*.</span><span class="sxs-lookup"><span data-stu-id="dee0a-138">Open *MainWindow.xaml*.</span></span>

    <span data-ttu-id="dee0a-139">Ten plik XAML jest głównym oknem aplikacji i wyświetla zawartość utworzoną na stronach.</span><span class="sxs-lookup"><span data-stu-id="dee0a-139">This XAML file is the main window of your application and displays content created in pages.</span></span> <span data-ttu-id="dee0a-140"><xref:System.Windows.Window>Klasa definiuje właściwości okna, takie jak tytuł, rozmiar lub ikona, i obsługuje zdarzenia, takie jak zamykanie lub ukrywanie.</span><span class="sxs-lookup"><span data-stu-id="dee0a-140">The <xref:System.Windows.Window> class defines the properties of a window, such as its title, size, or icon, and handles events, such as closing or hiding.</span></span>

4. <span data-ttu-id="dee0a-141">Zmień <xref:System.Windows.Window> element na <xref:System.Windows.Navigation.NavigationWindow> , jak pokazano na poniższym kodzie XAML:</span><span class="sxs-lookup"><span data-stu-id="dee0a-141">Change the <xref:System.Windows.Window> element to a <xref:System.Windows.Navigation.NavigationWindow>, as shown in the following XAML:</span></span>

   ```xaml
   <NavigationWindow x:Class="ExpenseIt.MainWindow"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        ...
   </NavigationWindow>
   ```

   <span data-ttu-id="dee0a-142">Ta aplikacja nawiguje do innej zawartości w zależności od danych wprowadzonych przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="dee0a-142">This app navigates to different content depending on the user input.</span></span> <span data-ttu-id="dee0a-143">Jest to dlatego, że główny należy <xref:System.Windows.Window> zmienić na <xref:System.Windows.Navigation.NavigationWindow> .</span><span class="sxs-lookup"><span data-stu-id="dee0a-143">This is why the main <xref:System.Windows.Window> needs to be changed to a <xref:System.Windows.Navigation.NavigationWindow>.</span></span> <span data-ttu-id="dee0a-144"><xref:System.Windows.Navigation.NavigationWindow>dziedziczy wszystkie właściwości <xref:System.Windows.Window> .</span><span class="sxs-lookup"><span data-stu-id="dee0a-144"><xref:System.Windows.Navigation.NavigationWindow> inherits all the properties of <xref:System.Windows.Window>.</span></span> <span data-ttu-id="dee0a-145"><xref:System.Windows.Navigation.NavigationWindow>Element w pliku XAML tworzy wystąpienie <xref:System.Windows.Navigation.NavigationWindow> klasy.</span><span class="sxs-lookup"><span data-stu-id="dee0a-145">The <xref:System.Windows.Navigation.NavigationWindow> element in the XAML file creates an instance of the <xref:System.Windows.Navigation.NavigationWindow> class.</span></span> <span data-ttu-id="dee0a-146">Aby uzyskać więcej informacji, zobacz [Omówienie nawigacji](../app-development/navigation-overview.md).</span><span class="sxs-lookup"><span data-stu-id="dee0a-146">For more information, see [Navigation overview](../app-development/navigation-overview.md).</span></span>

5. <span data-ttu-id="dee0a-147">Usuń <xref:System.Windows.Controls.Grid> elementy z między <xref:System.Windows.Navigation.NavigationWindow> tagami.</span><span class="sxs-lookup"><span data-stu-id="dee0a-147">Remove the <xref:System.Windows.Controls.Grid> elements from between the <xref:System.Windows.Navigation.NavigationWindow> tags.</span></span>

6. <span data-ttu-id="dee0a-148">Zmień następujące właściwości w kodzie XAML dla <xref:System.Windows.Navigation.NavigationWindow> elementu:</span><span class="sxs-lookup"><span data-stu-id="dee0a-148">Change the following properties in the XAML code for the <xref:System.Windows.Navigation.NavigationWindow> element:</span></span>

    - <span data-ttu-id="dee0a-149">Ustaw <xref:System.Windows.Window.Title%2A> Właściwość na " `ExpenseIt` ".</span><span class="sxs-lookup"><span data-stu-id="dee0a-149">Set the <xref:System.Windows.Window.Title%2A> property to "`ExpenseIt`".</span></span>

    - <span data-ttu-id="dee0a-150">Ustaw <xref:System.Windows.FrameworkElement.Height%2A> Właściwość na 350 pikseli.</span><span class="sxs-lookup"><span data-stu-id="dee0a-150">Set the <xref:System.Windows.FrameworkElement.Height%2A> property to 350 pixels.</span></span>

    - <span data-ttu-id="dee0a-151">Ustaw <xref:System.Windows.FrameworkElement.Width%2A> Właściwość na 500 pikseli.</span><span class="sxs-lookup"><span data-stu-id="dee0a-151">Set the <xref:System.Windows.FrameworkElement.Width%2A> property to 500 pixels.</span></span>

    <span data-ttu-id="dee0a-152">KOD XAML powinien wyglądać podobnie do poniższego Visual Basic:</span><span class="sxs-lookup"><span data-stu-id="dee0a-152">Your XAML should look like the following for Visual Basic:</span></span>

    [!code-xaml[ExpenseIt#2_A](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt/MainWindow.xaml#2_a)]

    <span data-ttu-id="dee0a-153">I podobne do następujących dla języka C#:</span><span class="sxs-lookup"><span data-stu-id="dee0a-153">And like the following for C#:</span></span>

    [!code-xaml[ExpenseIt#2](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/MainWindow.xaml#2)]

7. <span data-ttu-id="dee0a-154">Otwórz *MainWindow. XAML. vb* lub *MainWindow.XAML.cs*.</span><span class="sxs-lookup"><span data-stu-id="dee0a-154">Open *MainWindow.xaml.vb* or *MainWindow.xaml.cs*.</span></span>

    <span data-ttu-id="dee0a-155">Ten plik jest plikiem związanym z kodem, który zawiera kod służący do obsługi zdarzeń zadeklarowanych w *MainWindow. XAML*.</span><span class="sxs-lookup"><span data-stu-id="dee0a-155">This file is a code-behind file that contains code to handle the events declared in *MainWindow.xaml*.</span></span> <span data-ttu-id="dee0a-156">Ten plik zawiera klasę częściową dla okna zdefiniowanego w języku XAML.</span><span class="sxs-lookup"><span data-stu-id="dee0a-156">This file contains a partial class for the window defined in XAML.</span></span>

8. <span data-ttu-id="dee0a-157">Jeśli używasz języka C#, Zmień klasę, `MainWindow` Aby dziedziczyć z <xref:System.Windows.Navigation.NavigationWindow> .</span><span class="sxs-lookup"><span data-stu-id="dee0a-157">If you're using C#, change the `MainWindow` class to derive from <xref:System.Windows.Navigation.NavigationWindow>.</span></span> <span data-ttu-id="dee0a-158">(W Visual Basic dzieje się to automatycznie po zmianie okna w języku XAML). Kod w języku C# powinien teraz wyglądać następująco:</span><span class="sxs-lookup"><span data-stu-id="dee0a-158">(In Visual Basic, this happens automatically when you change the window in XAML.) Your C# code should now look like this:</span></span>

   [!code-csharp[ExpenseIt#3](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/MainWindow.xaml.cs?highlight=21)]

## <a name="add-files-to-the-application"></a><span data-ttu-id="dee0a-159">Dodawanie plików do aplikacji</span><span class="sxs-lookup"><span data-stu-id="dee0a-159">Add files to the application</span></span>

<span data-ttu-id="dee0a-160">W tej sekcji dodasz dwie strony i obraz do aplikacji.</span><span class="sxs-lookup"><span data-stu-id="dee0a-160">In this section, you'll add two pages and an image to the application.</span></span>

1. <span data-ttu-id="dee0a-161">Dodaj nową stronę do projektu i nadaj jej nazwę *`ExpenseItHome.xaml`* :</span><span class="sxs-lookup"><span data-stu-id="dee0a-161">Add a new page to the project, and name it *`ExpenseItHome.xaml`*:</span></span>

   1. <span data-ttu-id="dee0a-162">W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy **`ExpenseIt`** węzeł projektu i wybierz polecenie **Dodaj**  >  **stronę**.</span><span class="sxs-lookup"><span data-stu-id="dee0a-162">In **Solution Explorer**, right-click on the **`ExpenseIt`** project node and choose **Add** > **Page**.</span></span>

   1. <span data-ttu-id="dee0a-163">W oknie dialogowym **Dodaj nowy element** szablon **Strona (WPF)** jest już zaznaczony.</span><span class="sxs-lookup"><span data-stu-id="dee0a-163">In the **Add New Item** dialog, the **Page (WPF)** template is already selected.</span></span> <span data-ttu-id="dee0a-164">Wprowadź nazwę **`ExpenseItHome`** , a następnie wybierz pozycję **Dodaj**.</span><span class="sxs-lookup"><span data-stu-id="dee0a-164">Enter the name **`ExpenseItHome`**, and then select **Add**.</span></span>

    <span data-ttu-id="dee0a-165">Ta strona to pierwsza strona wyświetlana podczas uruchamiania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="dee0a-165">This page is the first page that's displayed when the application is launched.</span></span> <span data-ttu-id="dee0a-166">Zostanie wyświetlona lista osób, spośród których można wybrać, aby wyświetlić raport wydatków dla programu.</span><span class="sxs-lookup"><span data-stu-id="dee0a-166">It will show a list of people to select from, to show an expense report for.</span></span>

1. <span data-ttu-id="dee0a-167">Otwórz *`ExpenseItHome.xaml`* .</span><span class="sxs-lookup"><span data-stu-id="dee0a-167">Open *`ExpenseItHome.xaml`*.</span></span>

1. <span data-ttu-id="dee0a-168">Ustaw wartość <xref:System.Windows.Controls.Page.Title%2A> na " `ExpenseIt - Home` ".</span><span class="sxs-lookup"><span data-stu-id="dee0a-168">Set the <xref:System.Windows.Controls.Page.Title%2A> to "`ExpenseIt - Home`".</span></span>

1. <span data-ttu-id="dee0a-169">Ustaw `DesignHeight` do 350 pikseli i `DesignWidth` do 500 pikseli.</span><span class="sxs-lookup"><span data-stu-id="dee0a-169">Set the `DesignHeight` to 350 pixels and the `DesignWidth` to 500 pixels.</span></span>

    <span data-ttu-id="dee0a-170">KOD XAML jest teraz wyświetlany w następujący sposób dla Visual Basic:</span><span class="sxs-lookup"><span data-stu-id="dee0a-170">The XAML now appears as follows for Visual Basic:</span></span>

    [!code-xaml[ExpenseIt#6_A](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseItHome.xaml#6_a)]

    <span data-ttu-id="dee0a-171">I podobne do następujących dla języka C#:</span><span class="sxs-lookup"><span data-stu-id="dee0a-171">And like the following for C#:</span></span>

    [!code-xaml[ExpenseIt#6](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt2/ExpenseItHome.xaml#6)]

1. <span data-ttu-id="dee0a-172">Otwórz *MainWindow. XAML*.</span><span class="sxs-lookup"><span data-stu-id="dee0a-172">Open *MainWindow.xaml*.</span></span>

1. <span data-ttu-id="dee0a-173">Dodaj <xref:System.Windows.Navigation.NavigationWindow.Source%2A> Właściwość do <xref:System.Windows.Navigation.NavigationWindow> elementu i ustaw ją na " `ExpenseItHome.xaml` ".</span><span class="sxs-lookup"><span data-stu-id="dee0a-173">Add a <xref:System.Windows.Navigation.NavigationWindow.Source%2A> property to the <xref:System.Windows.Navigation.NavigationWindow> element and set it to "`ExpenseItHome.xaml`".</span></span>

    <span data-ttu-id="dee0a-174">To ustawienie *`ExpenseItHome.xaml`* jest pierwszą stroną otwartą podczas uruchamiania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="dee0a-174">This sets *`ExpenseItHome.xaml`* to be the first page opened when the application starts.</span></span>

    <span data-ttu-id="dee0a-175">Przykładowy kod XAML w Visual Basic:</span><span class="sxs-lookup"><span data-stu-id="dee0a-175">Example XAML in Visual Basic:</span></span>

    [!code-xaml[ExpenseIt#7_A](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/MainWindow.xaml#7_a)]

    <span data-ttu-id="dee0a-176">I w języku C#:</span><span class="sxs-lookup"><span data-stu-id="dee0a-176">And in C#:</span></span>

    [!code-xaml[ExpenseIt#7](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt2/MainWindow.xaml#7)]

   > [!TIP]
   > <span data-ttu-id="dee0a-177">Możesz również ustawić właściwość **Source** w kategorii **różne** okna **Właściwości** .</span><span class="sxs-lookup"><span data-stu-id="dee0a-177">You can also set the **Source** property in the **Miscellaneous** category of the **Properties** window.</span></span>
   >
   > ![Właściwość Source w okno Właściwości](./media/properties-source.png)

1. <span data-ttu-id="dee0a-179">Dodaj kolejną nową stronę WPF do projektu i nadaj jej nazwę *ExpenseReportPage. XAML*::</span><span class="sxs-lookup"><span data-stu-id="dee0a-179">Add another new WPF page to the project, and name it *ExpenseReportPage.xaml*::</span></span>

   1. <span data-ttu-id="dee0a-180">W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy **`ExpenseIt`** węzeł projektu i wybierz polecenie **Dodaj**  >  **stronę**.</span><span class="sxs-lookup"><span data-stu-id="dee0a-180">In **Solution Explorer**, right-click on the **`ExpenseIt`** project node and choose **Add** > **Page**.</span></span>

   1. <span data-ttu-id="dee0a-181">W oknie dialogowym **Dodaj nowy element** wybierz szablon **Strona (WPF)** .</span><span class="sxs-lookup"><span data-stu-id="dee0a-181">In the **Add New Item** dialog, select the **Page (WPF)** template.</span></span> <span data-ttu-id="dee0a-182">Wprowadź nazwę **ExpenseReportPage**, a następnie wybierz pozycję **Dodaj**.</span><span class="sxs-lookup"><span data-stu-id="dee0a-182">Enter the name **ExpenseReportPage**, and then select **Add**.</span></span>

    <span data-ttu-id="dee0a-183">Na tej stronie zostanie wyświetlony raport wydatków dla osoby, która została wybrana na **`ExpenseItHome`** stronie.</span><span class="sxs-lookup"><span data-stu-id="dee0a-183">This page will show the expense report for the person that is selected on the **`ExpenseItHome`** page.</span></span>

1. <span data-ttu-id="dee0a-184">Otwórz *ExpenseReportPage. XAML*.</span><span class="sxs-lookup"><span data-stu-id="dee0a-184">Open *ExpenseReportPage.xaml*.</span></span>

1. <span data-ttu-id="dee0a-185">Ustaw wartość <xref:System.Windows.Controls.Page.Title%2A> na " `ExpenseIt - View Expense` ".</span><span class="sxs-lookup"><span data-stu-id="dee0a-185">Set the <xref:System.Windows.Controls.Page.Title%2A> to "`ExpenseIt - View Expense`".</span></span>

1. <span data-ttu-id="dee0a-186">Ustaw `DesignHeight` do 350 pikseli i `DesignWidth` do 500 pikseli.</span><span class="sxs-lookup"><span data-stu-id="dee0a-186">Set the `DesignHeight` to 350 pixels and the `DesignWidth` to 500 pixels.</span></span>

    <span data-ttu-id="dee0a-187">*ExpenseReportPage. XAML* wygląda teraz następująco w Visual Basic:</span><span class="sxs-lookup"><span data-stu-id="dee0a-187">*ExpenseReportPage.xaml* now looks like the following in Visual Basic:</span></span>

    [!code-xaml[ExpenseIt#4_A](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseReportPage.xaml#4_a)]

    <span data-ttu-id="dee0a-188">I podobne do następujących w języku C#:</span><span class="sxs-lookup"><span data-stu-id="dee0a-188">And like the following in C#:</span></span>

    [!code-xaml[ExpenseIt#4](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/ExpenseReportPage.xaml#4)]

1. <span data-ttu-id="dee0a-189">Otwórz *ExpenseItHome. XAML. vb* oraz *ExpenseReportPage. XAML. vb*lub *ExpenseItHome.XAML.cs* i *ExpenseReportPage.XAML.cs*.</span><span class="sxs-lookup"><span data-stu-id="dee0a-189">Open *ExpenseItHome.xaml.vb* and *ExpenseReportPage.xaml.vb*, or *ExpenseItHome.xaml.cs* and *ExpenseReportPage.xaml.cs*.</span></span>

    <span data-ttu-id="dee0a-190">Podczas tworzenia nowego pliku stronicowania program Visual Studio automatycznie tworzy swój plik *związany z kodem* .</span><span class="sxs-lookup"><span data-stu-id="dee0a-190">When you create a new Page file, Visual Studio automatically creates its *code-behind* file.</span></span> <span data-ttu-id="dee0a-191">Te pliki związane z kodem obsługują logikę w celu reagowania na dane wejściowe użytkownika.</span><span class="sxs-lookup"><span data-stu-id="dee0a-191">These code-behind files handle the logic for responding to user input.</span></span>

    <span data-ttu-id="dee0a-192">Kod powinien wyglądać następująco **`ExpenseItHome`** :</span><span class="sxs-lookup"><span data-stu-id="dee0a-192">Your code should look like the following for **`ExpenseItHome`**:</span></span>

    [!code-csharp[ExpenseIt#2_5](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt2/ExpenseItHome.xaml.cs#2_5)]

    [!code-vb[ExpenseIt#2_5](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseItHome.xaml.vb#2_5)]

    <span data-ttu-id="dee0a-193">I tak jak w przypadku **ExpenseReportPage**:</span><span class="sxs-lookup"><span data-stu-id="dee0a-193">And like the following for **ExpenseReportPage**:</span></span>

    [!code-csharp[ExpenseIt#5](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/ExpenseReportPage.xaml.cs#5)]

    [!code-vb[ExpenseIt#5](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseReportPage.xaml.vb#5)]

1. <span data-ttu-id="dee0a-194">Dodaj obraz o nazwie *watermark.png* do projektu.</span><span class="sxs-lookup"><span data-stu-id="dee0a-194">Add an image named *watermark.png* to the project.</span></span> <span data-ttu-id="dee0a-195">Możesz utworzyć własny obraz, skopiować plik z przykładowego kodu lub pobrać go z repozytorium GitHub [Microsoft/WPF-Samples](https://raw.githubusercontent.com/microsoft/WPF-Samples/master/Getting%20Started/WalkthroughFirstWPFApp/csharp/watermark.png) .</span><span class="sxs-lookup"><span data-stu-id="dee0a-195">You can create your own image, copy the file from the sample code, or get it from the [microsoft/WPF-Samples](https://raw.githubusercontent.com/microsoft/WPF-Samples/master/Getting%20Started/WalkthroughFirstWPFApp/csharp/watermark.png) GitHub repository.</span></span>

    1. <span data-ttu-id="dee0a-196">Kliknij prawym przyciskiem myszy węzeł projektu i wybierz polecenie **Dodaj**  >  **istniejący element**lub naciśnij klawisze **SHIFT** + **Alt** + **A**.</span><span class="sxs-lookup"><span data-stu-id="dee0a-196">Right-click on the project node and select **Add** > **Existing Item**, or press **Shift**+**Alt**+**A**.</span></span>

    2. <span data-ttu-id="dee0a-197">W oknie dialogowym **Dodaj istniejący element** Ustaw filtr pliku na **wszystkie pliki** lub **pliki obrazów**, przejdź do pliku obrazu, którego chcesz użyć, a następnie wybierz pozycję **Dodaj**.</span><span class="sxs-lookup"><span data-stu-id="dee0a-197">In the **Add Existing Item** dialog, set the file filter to either **All Files** or **Image Files**, browse to the image file you want to use, and then select **Add**.</span></span>

## <a name="build-and-run-the-application"></a><span data-ttu-id="dee0a-198">Kompilowanie i uruchamianie aplikacji</span><span class="sxs-lookup"><span data-stu-id="dee0a-198">Build and run the application</span></span>

1. <span data-ttu-id="dee0a-199">Aby skompilować i uruchomić aplikację, naciśnij klawisz **F5** lub wybierz pozycję **Rozpocznij debugowanie** z menu **debugowanie** .</span><span class="sxs-lookup"><span data-stu-id="dee0a-199">To build and run the application, press **F5** or select **Start Debugging** from the **Debug** menu.</span></span>

    <span data-ttu-id="dee0a-200">Na poniższej ilustracji przedstawiono aplikację z <xref:System.Windows.Navigation.NavigationWindow> przyciskami:</span><span class="sxs-lookup"><span data-stu-id="dee0a-200">The following illustration shows the application with the <xref:System.Windows.Navigation.NavigationWindow> buttons:</span></span>

    ![Po skompilowaniu i uruchomieniu aplikacji.](./media/walkthrough-my-first-wpf-desktop-application/build-run-application.png)

2. <span data-ttu-id="dee0a-202">Zamknij aplikację, aby powrócić do programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="dee0a-202">Close the application to return to Visual Studio.</span></span>

## <a name="create-the-layout"></a><span data-ttu-id="dee0a-203">Tworzenie układu</span><span class="sxs-lookup"><span data-stu-id="dee0a-203">Create the layout</span></span>

<span data-ttu-id="dee0a-204">Układ zapewnia uporządkowany sposób umieszczania elementów interfejsu użytkownika, a także zarządza rozmiarem i położeniem tych elementów w przypadku zmiany rozmiaru interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="dee0a-204">Layout provides an ordered way to place UI elements, and also manages the size and position of those elements when a UI is resized.</span></span> <span data-ttu-id="dee0a-205">Zazwyczaj tworzysz układ z jedną z następujących kontrolek układu:</span><span class="sxs-lookup"><span data-stu-id="dee0a-205">You typically create a layout with one of the following layout controls:</span></span>

- <span data-ttu-id="dee0a-206"><xref:System.Windows.Controls.Canvas>-Definiuje obszar, w którym można jawnie pozycjonować elementy podrzędne za pomocą współrzędnych względnych dla obszaru kanwy.</span><span class="sxs-lookup"><span data-stu-id="dee0a-206"><xref:System.Windows.Controls.Canvas> - Defines an area within which you can explicitly position child elements by using coordinates that are relative to the Canvas area.</span></span>
- <span data-ttu-id="dee0a-207"><xref:System.Windows.Controls.DockPanel>-Definiuje obszar, w którym można rozmieścić elementy podrzędne w poziomie lub w pionie względem siebie.</span><span class="sxs-lookup"><span data-stu-id="dee0a-207"><xref:System.Windows.Controls.DockPanel> - Defines an area where you can arrange child elements either horizontally or vertically, relative to each other.</span></span>
- <span data-ttu-id="dee0a-208"><xref:System.Windows.Controls.Grid>-Definiuje elastyczny obszar siatki składający się z kolumn i wierszy.</span><span class="sxs-lookup"><span data-stu-id="dee0a-208"><xref:System.Windows.Controls.Grid> - Defines a flexible grid area that consists of columns and rows.</span></span>
- <span data-ttu-id="dee0a-209"><xref:System.Windows.Controls.StackPanel>— Rozmieszcza elementy podrzędne w pojedynczym wierszu, który może być zorientowany w poziomie lub w pionie.</span><span class="sxs-lookup"><span data-stu-id="dee0a-209"><xref:System.Windows.Controls.StackPanel> - Arranges child elements into a single line that can be oriented horizontally or vertically.</span></span>
- <span data-ttu-id="dee0a-210"><xref:System.Windows.Controls.VirtualizingStackPanel>-Rozmieszcza i wirtualizacji zawartość w jednym wierszu, który ma orientację poziomą lub pionową.</span><span class="sxs-lookup"><span data-stu-id="dee0a-210"><xref:System.Windows.Controls.VirtualizingStackPanel> - Arranges and virtualizes content on a single line that is oriented either horizontally or vertically.</span></span>
- <span data-ttu-id="dee0a-211"><xref:System.Windows.Controls.WrapPanel>-Umieszcza elementy podrzędne w kolejności sekwencyjnej od lewej do prawej, dzieląc zawartość do następnego wiersza na krawędzi pola zawierającego.</span><span class="sxs-lookup"><span data-stu-id="dee0a-211"><xref:System.Windows.Controls.WrapPanel> - Positions child elements in sequential position from left to right, breaking content to the next line at the edge of the containing box.</span></span> <span data-ttu-id="dee0a-212">Kolejne porządkowanie odbywa się sekwencyjnie od góry do dołu lub od prawej do lewej, w zależności od wartości właściwości Orientation.</span><span class="sxs-lookup"><span data-stu-id="dee0a-212">Subsequent ordering happens sequentially from top to bottom or from right to left, depending on the value of the Orientation property.</span></span>

<span data-ttu-id="dee0a-213">Każda z tych kontrolek układu obsługuje określony typ układu dla jego elementów podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="dee0a-213">Each of these layout controls supports a particular type of layout for its child elements.</span></span> <span data-ttu-id="dee0a-214">`ExpenseIt`rozmiary stron mogą być zmieniane, a każda Strona zawiera elementy ułożone w poziomie i w pionie wraz z innymi elementami.</span><span class="sxs-lookup"><span data-stu-id="dee0a-214">`ExpenseIt` pages can be resized, and each page has elements that are arranged horizontally and vertically alongside other elements.</span></span> <span data-ttu-id="dee0a-215">W tym przykładzie <xref:System.Windows.Controls.Grid> jest używany jako element układu dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="dee0a-215">In this example, the <xref:System.Windows.Controls.Grid> is used as  layout element for the application.</span></span>

> [!TIP]
> <span data-ttu-id="dee0a-216">Aby uzyskać więcej informacji o <xref:System.Windows.Controls.Panel> elementach, zobacz [Omówienie paneli](../controls/panels-overview.md).</span><span class="sxs-lookup"><span data-stu-id="dee0a-216">For more information about <xref:System.Windows.Controls.Panel> elements, see [Panels overview](../controls/panels-overview.md).</span></span> <span data-ttu-id="dee0a-217">Aby uzyskać więcej informacji na temat układu, zobacz [Układ](../advanced/layout.md).</span><span class="sxs-lookup"><span data-stu-id="dee0a-217">For more information about layout, see [Layout](../advanced/layout.md).</span></span>

<span data-ttu-id="dee0a-218">W tej sekcji utworzysz jednokolumnową tabelę z trzema wierszami i marginesem 10 pikseli, dodając definicje kolumn i wierszy do elementu <xref:System.Windows.Controls.Grid> w *`ExpenseItHome.xaml`* .</span><span class="sxs-lookup"><span data-stu-id="dee0a-218">In this section, you create a single-column table with three rows and a 10-pixel margin by adding column and row definitions to the <xref:System.Windows.Controls.Grid> in *`ExpenseItHome.xaml`*.</span></span>

1. <span data-ttu-id="dee0a-219">W *`ExpenseItHome.xaml`* , ustaw <xref:System.Windows.FrameworkElement.Margin%2A> właściwość elementu na wartość <xref:System.Windows.Controls.Grid> "10, 0, 10, 10", która odnosi się do lewego, górnego, prawego i dolnego marginesu:</span><span class="sxs-lookup"><span data-stu-id="dee0a-219">In *`ExpenseItHome.xaml`*, set the <xref:System.Windows.FrameworkElement.Margin%2A> property on the <xref:System.Windows.Controls.Grid> element to "10,0,10,10", which corresponds to left, top, right and bottom margins:</span></span>

   ```xaml
   <Grid Margin="10,0,10,10">
   ```

   > [!TIP]
   > <span data-ttu-id="dee0a-220">Możesz również ustawić wartości **marginesu** w oknie **Właściwości** , w obszarze Kategoria **układu** :</span><span class="sxs-lookup"><span data-stu-id="dee0a-220">You can also set the **Margin** values in the **Properties** window, under the **Layout** category:</span></span>
   >
   > ![Wartości marginesów w okno Właściwości](./media/properties-margin.png)

2. <span data-ttu-id="dee0a-222">Dodaj następujący kod XAML między <xref:System.Windows.Controls.Grid> tagami, aby utworzyć definicje wierszy i kolumn:</span><span class="sxs-lookup"><span data-stu-id="dee0a-222">Add the following XAML between the <xref:System.Windows.Controls.Grid> tags to create the row and column definitions:</span></span>

    [!code-xaml[ExpenseIt#8](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt3/ExpenseItHome.xaml#8)]

    <span data-ttu-id="dee0a-223"><xref:System.Windows.Controls.RowDefinition.Height%2A>Dwa wiersze są ustawione na <xref:System.Windows.GridLength.Auto%2A> , co oznacza, że rozmiar wierszy jest określany na podstawie zawartości w wierszach.</span><span class="sxs-lookup"><span data-stu-id="dee0a-223">The <xref:System.Windows.Controls.RowDefinition.Height%2A> of two rows is set to <xref:System.Windows.GridLength.Auto%2A>, which means that the rows are sized based on the content in the rows.</span></span> <span data-ttu-id="dee0a-224">Wartość domyślna <xref:System.Windows.Controls.RowDefinition.Height%2A> to <xref:System.Windows.GridUnitType.Star> rozmiar, co oznacza, że wysokość wiersza jest ważoną ilością dostępnego miejsca.</span><span class="sxs-lookup"><span data-stu-id="dee0a-224">The default <xref:System.Windows.Controls.RowDefinition.Height%2A> is <xref:System.Windows.GridUnitType.Star> sizing, which means that the row height is a weighted proportion of the available space.</span></span> <span data-ttu-id="dee0a-225">Na przykład jeśli dwa wiersze mają wartość <xref:System.Windows.Controls.RowDefinition.Height%2A> "\*", każdy z nich ma wysokość połowę dostępnego miejsca.</span><span class="sxs-lookup"><span data-stu-id="dee0a-225">For example if two rows each have a <xref:System.Windows.Controls.RowDefinition.Height%2A> of "\*", they each have a height that is half of the available space.</span></span>

    <span data-ttu-id="dee0a-226"><xref:System.Windows.Controls.Grid>Powinien teraz zawierać następujący kod XAML:</span><span class="sxs-lookup"><span data-stu-id="dee0a-226">Your <xref:System.Windows.Controls.Grid> should now contain the following XAML:</span></span>

    [!code-xaml[ExpenseIt#9](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt3/ExpenseItHome.xaml#9)]

## <a name="add-controls"></a><span data-ttu-id="dee0a-227">Dodawanie kontrolek</span><span class="sxs-lookup"><span data-stu-id="dee0a-227">Add controls</span></span>

<span data-ttu-id="dee0a-228">W tej sekcji opisano aktualizowanie interfejsu użytkownika strony głównej w celu wyświetlenia listy osób, w których można wybrać jedną osobę, aby wyświetlić raport z wydatków.</span><span class="sxs-lookup"><span data-stu-id="dee0a-228">In this section, you'll update the home page UI to show a list of people, where you select one person to display their expense report.</span></span> <span data-ttu-id="dee0a-229">Formanty to obiekty UI, które umożliwiają użytkownikom współpracującie z Twoją aplikacją.</span><span class="sxs-lookup"><span data-stu-id="dee0a-229">Controls are UI objects that allow users to interact with your application.</span></span> <span data-ttu-id="dee0a-230">Aby uzyskać więcej informacji, zobacz [Controls](../controls/index.md).</span><span class="sxs-lookup"><span data-stu-id="dee0a-230">For more information, see [Controls](../controls/index.md).</span></span>

<span data-ttu-id="dee0a-231">Aby utworzyć ten interfejs użytkownika, Dodaj następujące elementy *`ExpenseItHome.xaml`* :</span><span class="sxs-lookup"><span data-stu-id="dee0a-231">To create this UI, you'll add the following elements to *`ExpenseItHome.xaml`*:</span></span>

- <span data-ttu-id="dee0a-232">A <xref:System.Windows.Controls.ListBox> (dla listy osób).</span><span class="sxs-lookup"><span data-stu-id="dee0a-232">A <xref:System.Windows.Controls.ListBox> (for the list of people).</span></span>
- <span data-ttu-id="dee0a-233">A <xref:System.Windows.Controls.Label> (dla nagłówka listy).</span><span class="sxs-lookup"><span data-stu-id="dee0a-233">A <xref:System.Windows.Controls.Label> (for the list header).</span></span>
- <span data-ttu-id="dee0a-234">A <xref:System.Windows.Controls.Button> (kliknij, aby wyświetlić raport wydatków dla osoby, która została wybrana na liście).</span><span class="sxs-lookup"><span data-stu-id="dee0a-234">A <xref:System.Windows.Controls.Button> (to click to view the expense report for the person that is selected in the list).</span></span>

<span data-ttu-id="dee0a-235">Każda kontrolka jest umieszczana w wierszu obiektu <xref:System.Windows.Controls.Grid> przez ustawienie <xref:System.Windows.Controls.Grid.Row%2A?displayProperty=nameWithType> dołączonej właściwości.</span><span class="sxs-lookup"><span data-stu-id="dee0a-235">Each control is placed in a row of the <xref:System.Windows.Controls.Grid> by setting the <xref:System.Windows.Controls.Grid.Row%2A?displayProperty=nameWithType> attached property.</span></span> <span data-ttu-id="dee0a-236">Aby uzyskać więcej informacji o dołączanych właściwościach, zobacz temat [dołączone właściwości przegląd](../advanced/attached-properties-overview.md).</span><span class="sxs-lookup"><span data-stu-id="dee0a-236">For more information about attached properties, see [Attached Properties Overview](../advanced/attached-properties-overview.md).</span></span>

1. <span data-ttu-id="dee0a-237">W programie *`ExpenseItHome.xaml`* Dodaj następujący kod XAML gdzieś między <xref:System.Windows.Controls.Grid> tagami:</span><span class="sxs-lookup"><span data-stu-id="dee0a-237">In *`ExpenseItHome.xaml`*, add the following XAML somewhere between the <xref:System.Windows.Controls.Grid> tags:</span></span>

   [!code-xaml[ExpenseIt#10](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt4/ExpenseItHome.xaml#10)]

   > [!TIP]
   > <span data-ttu-id="dee0a-238">Możesz również utworzyć kontrolki, przeciągając je z okna **przybornika** do okna projektowania, a następnie ustawiając ich właściwości w oknie **Właściwości** .</span><span class="sxs-lookup"><span data-stu-id="dee0a-238">You can also create the controls by dragging them from the **Toolbox** window onto the design window, and then setting their properties in the **Properties** window.</span></span>

2. <span data-ttu-id="dee0a-239">Skompiluj i uruchom aplikację.</span><span class="sxs-lookup"><span data-stu-id="dee0a-239">Build and run the application.</span></span>

    <span data-ttu-id="dee0a-240">Na poniższej ilustracji przedstawiono utworzone przez Ciebie formanty:</span><span class="sxs-lookup"><span data-stu-id="dee0a-240">The following illustration shows the controls you created:</span></span>

![Przykładowy zrzut ekranu ExpenseIt z listą nazw](./media/walkthrough-my-first-wpf-desktop-application/add-application-controls.png)

## <a name="add-an-image-and-a-title"></a><span data-ttu-id="dee0a-242">Dodawanie obrazu i tytułu</span><span class="sxs-lookup"><span data-stu-id="dee0a-242">Add an image and a title</span></span>

<span data-ttu-id="dee0a-243">W tej sekcji zaktualizujesz interfejs użytkownika strony głównej za pomocą obrazu i tytułu strony.</span><span class="sxs-lookup"><span data-stu-id="dee0a-243">In this section, you'll update the home page UI with an image and a page title.</span></span>

1. <span data-ttu-id="dee0a-244">W programie *`ExpenseItHome.xaml`* Dodaj kolejną kolumnę z <xref:System.Windows.Controls.Grid.ColumnDefinitions%2A> ustaloną <xref:System.Windows.Controls.ColumnDefinition.Width%2A> 230 pikseli:</span><span class="sxs-lookup"><span data-stu-id="dee0a-244">In *`ExpenseItHome.xaml`*, add another column to the <xref:System.Windows.Controls.Grid.ColumnDefinitions%2A> with a fixed <xref:System.Windows.Controls.ColumnDefinition.Width%2A> of 230 pixels:</span></span>

    [!code-xaml[ExpenseIt#11](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseItHome.xaml?highlight=2#NewColumn)]

2. <span data-ttu-id="dee0a-245">Dodaj kolejny wiersz do <xref:System.Windows.Controls.Grid.RowDefinitions%2A> , aby uzyskać łącznie cztery wiersze:</span><span class="sxs-lookup"><span data-stu-id="dee0a-245">Add another row to the <xref:System.Windows.Controls.Grid.RowDefinitions%2A>, for a total of four rows:</span></span>

    [!code-xaml[ExpenseIt#11b](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseItHome.xaml?highlight=2#NewRows)]

3. <span data-ttu-id="dee0a-246">Przenieś kontrolki do drugiej kolumny, ustawiając <xref:System.Windows.Controls.Grid.Column%2A?displayProperty=nameWithType> Właściwość na 1 w każdej z trzech kontrolek (obramowanie, ListBox i Button).</span><span class="sxs-lookup"><span data-stu-id="dee0a-246">Move the controls to the second column by setting the <xref:System.Windows.Controls.Grid.Column%2A?displayProperty=nameWithType> property to 1 in each of the three controls (Border, ListBox, and Button).</span></span>

4. <span data-ttu-id="dee0a-247">Przenieś każdy formant w dół, zwiększając jego <xref:System.Windows.Controls.Grid.Row%2A?displayProperty=nameWithType> wartość o 1 dla każdej z trzech kontrolek (obramowanie, ListBox i Button) oraz dla elementu Border.</span><span class="sxs-lookup"><span data-stu-id="dee0a-247">Move each control down a row by incrementing its <xref:System.Windows.Controls.Grid.Row%2A?displayProperty=nameWithType> value by 1 for each of the three controls (Border, ListBox, and Button) and for the Border element.</span></span>

   <span data-ttu-id="dee0a-248">KOD XAML dla trzech kontrolek wygląda teraz następująco:</span><span class="sxs-lookup"><span data-stu-id="dee0a-248">The XAML for the three controls now looks like the following:</span></span>

    [!code-xaml[ExpenseIt#12](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#12)]

5. <span data-ttu-id="dee0a-249">Ustaw <xref:System.Windows.Controls.Panel.Background%2A?displayProperty=nameWithType> Właściwość na *watermark.png* pliku obrazu, DODAJĄC następujący kod XAML gdziekolwiek między `<Grid>` `</Grid>` tagami i:</span><span class="sxs-lookup"><span data-stu-id="dee0a-249">Set the <xref:System.Windows.Controls.Panel.Background%2A?displayProperty=nameWithType> property to the *watermark.png* image file, by adding the following XAML anywhere between the `<Grid>` and `</Grid>` tags:</span></span>

    [!code-xaml[ExpenseIt#14](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#14)]

6. <span data-ttu-id="dee0a-250">Przed <xref:System.Windows.Controls.Border> elementem Dodaj element <xref:System.Windows.Controls.Label> z zawartością "Wyświetl raport wydatków".</span><span class="sxs-lookup"><span data-stu-id="dee0a-250">Before the <xref:System.Windows.Controls.Border> element, add a <xref:System.Windows.Controls.Label> with the content "View Expense Report".</span></span> <span data-ttu-id="dee0a-251">Ta etykieta jest tytułem strony.</span><span class="sxs-lookup"><span data-stu-id="dee0a-251">This label is the title of the page.</span></span>

    [!code-xaml[ExpenseIt#13](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#13)]

7. <span data-ttu-id="dee0a-252">Skompiluj i uruchom aplikację.</span><span class="sxs-lookup"><span data-stu-id="dee0a-252">Build and run the application.</span></span>

<span data-ttu-id="dee0a-253">Na poniższej ilustracji przedstawiono wyniki, które właśnie Dodano:</span><span class="sxs-lookup"><span data-stu-id="dee0a-253">The following illustration shows the results of what you just added:</span></span>

![Przykładowy zrzut ekranu ExpenseIt pokazujący nowe tło obrazu i tytuł strony](./media/walkthrough-my-first-wpf-desktop-application/add-application-image-title.png)

## <a name="add-code-to-handle-events"></a><span data-ttu-id="dee0a-255">Dodawanie kodu do obsługi zdarzeń</span><span class="sxs-lookup"><span data-stu-id="dee0a-255">Add code to handle events</span></span>

1. <span data-ttu-id="dee0a-256">W programie *`ExpenseItHome.xaml`* Dodaj <xref:System.Windows.Controls.Primitives.ButtonBase.Click> do elementu procedurę obsługi zdarzeń <xref:System.Windows.Controls.Button> .</span><span class="sxs-lookup"><span data-stu-id="dee0a-256">In *`ExpenseItHome.xaml`*, add a <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event handler to the <xref:System.Windows.Controls.Button> element.</span></span> <span data-ttu-id="dee0a-257">Aby uzyskać więcej informacji, zobacz [jak: Tworzenie prostego programu obsługi zdarzeń](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/bb675300(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="dee0a-257">For more information, see [How to: Create a simple event handler](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/bb675300(v=vs.100)).</span></span>

    [!code-xaml[ExpenseIt#15](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt6/ExpenseItHome.xaml#15)]

2. <span data-ttu-id="dee0a-258">Otwórz *`ExpenseItHome.xaml.vb`* lub *`ExpenseItHome.xaml.cs`* .</span><span class="sxs-lookup"><span data-stu-id="dee0a-258">Open *`ExpenseItHome.xaml.vb`* or *`ExpenseItHome.xaml.cs`*.</span></span>

3. <span data-ttu-id="dee0a-259">Dodaj następujący kod do klasy, `ExpenseItHome` Aby dodać przycisk procedury obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="dee0a-259">Add the following code to the `ExpenseItHome` class to add a button click event handler.</span></span> <span data-ttu-id="dee0a-260">Procedura obsługi zdarzeń otwiera stronę **ExpenseReportPage** .</span><span class="sxs-lookup"><span data-stu-id="dee0a-260">The event handler opens the **ExpenseReportPage** page.</span></span>

    [!code-csharp[ExpenseIt#16](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt6/ExpenseItHome.xaml.cs#16)]
    [!code-vb[ExpenseIt#16](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt6/ExpenseItHome.xaml.vb#16)]

## <a name="create-the-ui-for-expensereportpage"></a><span data-ttu-id="dee0a-261">Tworzenie interfejsu użytkownika dla ExpenseReportPage</span><span class="sxs-lookup"><span data-stu-id="dee0a-261">Create the UI for ExpenseReportPage</span></span>

<span data-ttu-id="dee0a-262">*ExpenseReportPage. XAML* wyświetla raport wydatków dla osoby, która została wybrana na **`ExpenseItHome`** stronie.</span><span class="sxs-lookup"><span data-stu-id="dee0a-262">*ExpenseReportPage.xaml* displays the expense report for the person that's selected on the **`ExpenseItHome`** page.</span></span> <span data-ttu-id="dee0a-263">W tej sekcji utworzysz interfejs użytkownika dla **ExpenseReportPage**.</span><span class="sxs-lookup"><span data-stu-id="dee0a-263">In this section, you'll create the UI for **ExpenseReportPage**.</span></span> <span data-ttu-id="dee0a-264">Możesz również dodać kolory tła i wypełnienia do różnych elementów interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="dee0a-264">You'll also add background and fill colors to the various UI elements.</span></span>

1. <span data-ttu-id="dee0a-265">Otwórz *ExpenseReportPage. XAML*.</span><span class="sxs-lookup"><span data-stu-id="dee0a-265">Open *ExpenseReportPage.xaml*.</span></span>

2. <span data-ttu-id="dee0a-266">Dodaj następujący kod XAML między <xref:System.Windows.Controls.Grid> tagami:</span><span class="sxs-lookup"><span data-stu-id="dee0a-266">Add the following XAML between the <xref:System.Windows.Controls.Grid> tags:</span></span>

    [!code-xaml[ExpenseIt#17](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt6/ExpenseReportPage.xaml#17)]

    <span data-ttu-id="dee0a-267">Ten interfejs użytkownika jest podobny do *`ExpenseItHome.xaml`* , z wyjątkiem tego, że dane raportu są wyświetlane w <xref:System.Windows.Controls.DataGrid> .</span><span class="sxs-lookup"><span data-stu-id="dee0a-267">This UI is similar to *`ExpenseItHome.xaml`*, except the report data is displayed in a <xref:System.Windows.Controls.DataGrid>.</span></span>

3. <span data-ttu-id="dee0a-268">Skompiluj i uruchom aplikację.</span><span class="sxs-lookup"><span data-stu-id="dee0a-268">Build and run the application.</span></span>

4. <span data-ttu-id="dee0a-269">Wybierz przycisk **Wyświetl** .</span><span class="sxs-lookup"><span data-stu-id="dee0a-269">Select the **View** button.</span></span>

    <span data-ttu-id="dee0a-270">Zostanie wyświetlona strona raport o wydatkach.</span><span class="sxs-lookup"><span data-stu-id="dee0a-270">The expense report page appears.</span></span> <span data-ttu-id="dee0a-271">Zauważ również, że przycisk nawigacji wstecznej jest włączony.</span><span class="sxs-lookup"><span data-stu-id="dee0a-271">Also notice that the back navigation button is enabled.</span></span>

<span data-ttu-id="dee0a-272">Na poniższej ilustracji przedstawiono elementy interfejsu użytkownika dodane do *ExpenseReportPage. XAML*.</span><span class="sxs-lookup"><span data-stu-id="dee0a-272">The following illustration shows the UI elements added to *ExpenseReportPage.xaml*.</span></span>

![Przykładowy zrzut ekranu ExpenseIt przedstawiający interfejs użytkownika, który został właśnie utworzony dla ExpenseReportPage.](./media/walkthrough-my-first-wpf-desktop-application/create-application-ui.png)

## <a name="style-controls"></a><span data-ttu-id="dee0a-274">Kontrolki stylu</span><span class="sxs-lookup"><span data-stu-id="dee0a-274">Style controls</span></span>

<span data-ttu-id="dee0a-275">Wygląd różnych elementów jest często taki sam dla wszystkich elementów tego samego typu w interfejsie użytkownika.</span><span class="sxs-lookup"><span data-stu-id="dee0a-275">The appearance of various elements is often the same for all elements of the same type in a UI.</span></span> <span data-ttu-id="dee0a-276">Interfejs użytkownika używa [stylów](../../../desktop-wpf/fundamentals/styles-templates-overview.md) , aby można było używać ich w wielu elementach.</span><span class="sxs-lookup"><span data-stu-id="dee0a-276">UI uses [styles](../../../desktop-wpf/fundamentals/styles-templates-overview.md) to make appearances reusable across multiple elements.</span></span> <span data-ttu-id="dee0a-277">Możliwość ponownego wykorzystania stylów ułatwia tworzenie i zarządzanie XAML.</span><span class="sxs-lookup"><span data-stu-id="dee0a-277">The reusability of styles helps to simplify XAML creation and management.</span></span> <span data-ttu-id="dee0a-278">Ta sekcja zastępuje atrybuty dla elementu, które zostały zdefiniowane w poprzednich krokach ze stylami.</span><span class="sxs-lookup"><span data-stu-id="dee0a-278">This section replaces the per-element attributes that were defined in previous steps with styles.</span></span>

1. <span data-ttu-id="dee0a-279">Otwórz *aplikację Application. XAML* lub *App. XAML*.</span><span class="sxs-lookup"><span data-stu-id="dee0a-279">Open *Application.xaml* or *App.xaml*.</span></span>

2. <span data-ttu-id="dee0a-280">Dodaj następujący kod XAML między <xref:System.Windows.Application.Resources%2A?displayProperty=nameWithType> tagami:</span><span class="sxs-lookup"><span data-stu-id="dee0a-280">Add the following XAML between the <xref:System.Windows.Application.Resources%2A?displayProperty=nameWithType> tags:</span></span>

    [!code-xaml[ExpenseIt#18](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt7/App.xaml#18)]

    <span data-ttu-id="dee0a-281">Ten kod XAML dodaje następujące style:</span><span class="sxs-lookup"><span data-stu-id="dee0a-281">This XAML adds the following styles:</span></span>

    - <span data-ttu-id="dee0a-282">`headerTextStyle`: Aby sformatować tytuł strony <xref:System.Windows.Controls.Label> .</span><span class="sxs-lookup"><span data-stu-id="dee0a-282">`headerTextStyle`: To format the page title <xref:System.Windows.Controls.Label>.</span></span>

    - <span data-ttu-id="dee0a-283">`labelStyle`: Aby sformatować <xref:System.Windows.Controls.Label> kontrolki.</span><span class="sxs-lookup"><span data-stu-id="dee0a-283">`labelStyle`: To format the <xref:System.Windows.Controls.Label> controls.</span></span>

    - <span data-ttu-id="dee0a-284">`columnHeaderStyle`: Aby sformatować <xref:System.Windows.Controls.Primitives.DataGridColumnHeader> .</span><span class="sxs-lookup"><span data-stu-id="dee0a-284">`columnHeaderStyle`: To format the <xref:System.Windows.Controls.Primitives.DataGridColumnHeader>.</span></span>

    - <span data-ttu-id="dee0a-285">`listHeaderStyle`: Aby sformatować <xref:System.Windows.Controls.Border> kontrolki nagłówka listy.</span><span class="sxs-lookup"><span data-stu-id="dee0a-285">`listHeaderStyle`: To format the list header <xref:System.Windows.Controls.Border> controls.</span></span>

    - <span data-ttu-id="dee0a-286">`listHeaderTextStyle`: Aby sformatować nagłówek listy <xref:System.Windows.Controls.Label> .</span><span class="sxs-lookup"><span data-stu-id="dee0a-286">`listHeaderTextStyle`: To format the list header <xref:System.Windows.Controls.Label>.</span></span>

    - <span data-ttu-id="dee0a-287">`buttonStyle`: Aby sformatować <xref:System.Windows.Controls.Button> `ExpenseItHome.xaml` .</span><span class="sxs-lookup"><span data-stu-id="dee0a-287">`buttonStyle`: To format the <xref:System.Windows.Controls.Button> on `ExpenseItHome.xaml`.</span></span>

    <span data-ttu-id="dee0a-288">Należy zauważyć, że style są zasobami i elementami podrzędnymi <xref:System.Windows.Application.Resources%2A?displayProperty=nameWithType> elementu właściwości.</span><span class="sxs-lookup"><span data-stu-id="dee0a-288">Notice that the styles are resources and children of the <xref:System.Windows.Application.Resources%2A?displayProperty=nameWithType> property element.</span></span> <span data-ttu-id="dee0a-289">W tej lokalizacji style są stosowane do wszystkich elementów w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="dee0a-289">In this location, the styles are applied to all the elements in an application.</span></span> <span data-ttu-id="dee0a-290">Aby zapoznać się z przykładem użycia zasobów w aplikacji .NET, zobacz [Korzystanie z zasobów aplikacji](../advanced/how-to-use-application-resources.md).</span><span class="sxs-lookup"><span data-stu-id="dee0a-290">For an example of using resources in a .NET app, see [Use Application Resources](../advanced/how-to-use-application-resources.md).</span></span>

3. <span data-ttu-id="dee0a-291">W programie *`ExpenseItHome.xaml`* Zamień wszystkie elementy między <xref:System.Windows.Controls.Grid> elementami o następującym języku XAML:</span><span class="sxs-lookup"><span data-stu-id="dee0a-291">In *`ExpenseItHome.xaml`*, replace everything between the <xref:System.Windows.Controls.Grid> elements with the following XAML:</span></span>

    [!code-xaml[ExpenseIt#19](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt7/ExpenseItHome.xaml#19)]

    <span data-ttu-id="dee0a-292">Właściwości, takie jak <xref:System.Windows.VerticalAlignment> i definiujące <xref:System.Windows.Media.FontFamily> wygląd poszczególnych kontrolek, są usuwane i zastępowane przez zastosowanie stylów.</span><span class="sxs-lookup"><span data-stu-id="dee0a-292">The properties such as <xref:System.Windows.VerticalAlignment> and <xref:System.Windows.Media.FontFamily> that define the look of each control are removed and replaced by applying the styles.</span></span> <span data-ttu-id="dee0a-293">Na przykład, `headerTextStyle` jest stosowana do "Wyświetl raport wydatków" <xref:System.Windows.Controls.Label> .</span><span class="sxs-lookup"><span data-stu-id="dee0a-293">For example, the `headerTextStyle` is applied to the "View Expense Report" <xref:System.Windows.Controls.Label>.</span></span>

4. <span data-ttu-id="dee0a-294">Otwórz *ExpenseReportPage. XAML*.</span><span class="sxs-lookup"><span data-stu-id="dee0a-294">Open *ExpenseReportPage.xaml*.</span></span>

5. <span data-ttu-id="dee0a-295">Zastąp wszystkie <xref:System.Windows.Controls.Grid> elementy następującym XAML:</span><span class="sxs-lookup"><span data-stu-id="dee0a-295">Replace everything between the <xref:System.Windows.Controls.Grid> elements with the following XAML:</span></span>

    [!code-xaml[ExpenseIt#20](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt7/ExpenseReportPage.xaml#20)]

    <span data-ttu-id="dee0a-296">Ten kod XAML dodaje style do <xref:System.Windows.Controls.Label> <xref:System.Windows.Controls.Border> elementów i.</span><span class="sxs-lookup"><span data-stu-id="dee0a-296">This XAML adds styles to the <xref:System.Windows.Controls.Label> and <xref:System.Windows.Controls.Border> elements.</span></span>

6. <span data-ttu-id="dee0a-297">Skompiluj i uruchom aplikację.</span><span class="sxs-lookup"><span data-stu-id="dee0a-297">Build and run the application.</span></span> <span data-ttu-id="dee0a-298">Wygląd okna jest taki sam jak poprzednio.</span><span class="sxs-lookup"><span data-stu-id="dee0a-298">The window appearance is the same as previously.</span></span>

    ![ExpenseIt Przykładowy zrzut ekranu z tym samym wyglądem, jak w ostatniej sekcji.](./media/walkthrough-my-first-wpf-desktop-application/create-application-ui.png)

7. <span data-ttu-id="dee0a-300">Zamknij aplikację, aby powrócić do programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="dee0a-300">Close the application to return to Visual Studio.</span></span>

## <a name="bind-data-to-a-control"></a><span data-ttu-id="dee0a-301">Powiąż dane z kontrolką</span><span class="sxs-lookup"><span data-stu-id="dee0a-301">Bind data to a control</span></span>

<span data-ttu-id="dee0a-302">W tej sekcji utworzysz dane XML powiązane z różnymi kontrolkami.</span><span class="sxs-lookup"><span data-stu-id="dee0a-302">In this section, you'll create the XML data that is bound to various controls.</span></span>

1. <span data-ttu-id="dee0a-303">W programie *`ExpenseItHome.xaml`* po otwarciu <xref:System.Windows.Controls.Grid> elementu Dodaj następujący kod XAML, aby utworzyć <xref:System.Windows.Data.XmlDataProvider> zawierający dane dla każdej osoby:</span><span class="sxs-lookup"><span data-stu-id="dee0a-303">In *`ExpenseItHome.xaml`*, after the opening <xref:System.Windows.Controls.Grid> element, add the following XAML to create an <xref:System.Windows.Data.XmlDataProvider> that contains the data for each person:</span></span>

    [!code-xaml[ExpenseIt#23](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml?range=13,16-40,49)]

    <span data-ttu-id="dee0a-304">Dane są tworzone jako <xref:System.Windows.Controls.Grid> zasób.</span><span class="sxs-lookup"><span data-stu-id="dee0a-304">The data is created as a <xref:System.Windows.Controls.Grid> resource.</span></span> <span data-ttu-id="dee0a-305">Zwykle te dane zostałyby załadowane jako plik, ale dla uproszczenia dane są dodawane wewnętrznie.</span><span class="sxs-lookup"><span data-stu-id="dee0a-305">Normally this data would be loaded as a file, but for simplicity the data is added inline.</span></span>

2. <span data-ttu-id="dee0a-306">W `<Grid.Resources>` elemencie Dodaj następujący `<xref:System.Windows.DataTemplate>` element, który definiuje sposób wyświetlania danych w <xref:System.Windows.Controls.ListBox> , po `<XmlDataProvider>` elemencie:</span><span class="sxs-lookup"><span data-stu-id="dee0a-306">Within the `<Grid.Resources>` element, add the following `<xref:System.Windows.DataTemplate>` element, which defines how to display the data in the <xref:System.Windows.Controls.ListBox>, after the `<XmlDataProvider>` element:</span></span>

    [!code-xaml[ExpenseIt#24](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml?range=13,43-46,49)]

    <span data-ttu-id="dee0a-307">Aby uzyskać więcej informacji na temat szablonów danych, zobacz [tworzenia szablonów danych — omówienie](../data/data-templating-overview.md).</span><span class="sxs-lookup"><span data-stu-id="dee0a-307">For more information about data templates, see [Data templating overview](../data/data-templating-overview.md).</span></span>

3. <span data-ttu-id="dee0a-308">Zastąp istniejące <xref:System.Windows.Controls.ListBox> następującym XAML:</span><span class="sxs-lookup"><span data-stu-id="dee0a-308">Replace the existing <xref:System.Windows.Controls.ListBox> with the following XAML:</span></span>

    [!code-xaml[ExpenseIt#25](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml#25)]

    <span data-ttu-id="dee0a-309">Ten kod XAML wiąże <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> Właściwość ze <xref:System.Windows.Controls.ListBox> źródłem danych i stosuje szablon danych jako <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> .</span><span class="sxs-lookup"><span data-stu-id="dee0a-309">This XAML binds the <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> property of the <xref:System.Windows.Controls.ListBox> to the data source and applies the data template as the <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A>.</span></span>

## <a name="connect-data-to-controls"></a><span data-ttu-id="dee0a-310">Łączenie danych z kontrolkami</span><span class="sxs-lookup"><span data-stu-id="dee0a-310">Connect data to controls</span></span>

<span data-ttu-id="dee0a-311">Następnie dodasz kod w celu pobrania nazwy wybranej na **`ExpenseItHome`** stronie i przekazania jej do konstruktora **ExpenseReportPage**.</span><span class="sxs-lookup"><span data-stu-id="dee0a-311">Next, you'll add code to retrieve the name that's selected on the **`ExpenseItHome`** page and pass it to the constructor of **ExpenseReportPage**.</span></span> <span data-ttu-id="dee0a-312">**ExpenseReportPage** ustawia swój kontekst danych z elementem zakończonym, co oznacza, że kontrolki zdefiniowane w *ExpenseReportPage. XAML* są powiązane z.</span><span class="sxs-lookup"><span data-stu-id="dee0a-312">**ExpenseReportPage** sets its data context with the passed item, which is what the controls defined in *ExpenseReportPage.xaml* bind to.</span></span>

1. <span data-ttu-id="dee0a-313">Otwórz *ExpenseReportPage. XAML. vb* lub *ExpenseReportPage.XAML.cs*.</span><span class="sxs-lookup"><span data-stu-id="dee0a-313">Open *ExpenseReportPage.xaml.vb* or *ExpenseReportPage.xaml.cs*.</span></span>

2. <span data-ttu-id="dee0a-314">Dodaj Konstruktor, który pobiera obiekt, aby można było przekazać dane raportu wydatków wybranej osoby.</span><span class="sxs-lookup"><span data-stu-id="dee0a-314">Add a constructor that takes an object so you can pass the expense report data of the selected person.</span></span>

    [!code-csharp[ExpenseIt#26](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseReportPage.xaml.cs#26)]
    [!code-vb[ExpenseIt#26](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt8/ExpenseReportPage.xaml.vb#26)]

3. <span data-ttu-id="dee0a-315">Otwórz *`ExpenseItHome.xaml.vb`* lub *`ExpenseItHome.xaml.cs`* .</span><span class="sxs-lookup"><span data-stu-id="dee0a-315">Open *`ExpenseItHome.xaml.vb`* or *`ExpenseItHome.xaml.cs`*.</span></span>

4. <span data-ttu-id="dee0a-316">Zmień <xref:System.Windows.Controls.Primitives.ButtonBase.Click> procedurę obsługi zdarzeń, aby wywoływać nowego konstruktora przekazującego dane raportu wydatków wybranej osoby.</span><span class="sxs-lookup"><span data-stu-id="dee0a-316">Change the <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event handler to call the new constructor passing the expense report data of the selected person.</span></span>

    [!code-csharp[ExpenseIt#27](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml.cs#27)]
    [!code-vb[ExpenseIt#27](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt8/ExpenseItHome.xaml.vb#27)]

## <a name="style-data-with-data-templates"></a><span data-ttu-id="dee0a-317">Dane stylu z szablonami danych</span><span class="sxs-lookup"><span data-stu-id="dee0a-317">Style data with data templates</span></span>

<span data-ttu-id="dee0a-318">W tej sekcji należy zaktualizować interfejs użytkownika dla każdego elementu na listach powiązanych z danymi przy użyciu szablonów danych.</span><span class="sxs-lookup"><span data-stu-id="dee0a-318">In this section, you'll update the UI for each item in the data-bound lists by using data templates.</span></span>

1. <span data-ttu-id="dee0a-319">Otwórz *ExpenseReportPage. XAML*.</span><span class="sxs-lookup"><span data-stu-id="dee0a-319">Open *ExpenseReportPage.xaml*.</span></span>

2. <span data-ttu-id="dee0a-320">Powiąż zawartość elementów "name" i "Department" <xref:System.Windows.Controls.Label> z odpowiednią właściwością źródła danych.</span><span class="sxs-lookup"><span data-stu-id="dee0a-320">Bind the content of the "Name" and "Department" <xref:System.Windows.Controls.Label> elements to the appropriate data source property.</span></span> <span data-ttu-id="dee0a-321">Aby uzyskać więcej informacji na temat powiązania danych, zobacz temat [powiązanie danych — omówienie](../../../desktop-wpf/data/data-binding-overview.md).</span><span class="sxs-lookup"><span data-stu-id="dee0a-321">For more information about data binding, see [Data binding overview](../../../desktop-wpf/data/data-binding-overview.md).</span></span>

    [!code-xaml[ExpenseIt#31](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseReportPage.xaml#31)]

3. <span data-ttu-id="dee0a-322">Po otwarciu <xref:System.Windows.Controls.Grid> elementu Dodaj następujące szablony danych, które definiują sposób wyświetlania danych raportu wydatków:</span><span class="sxs-lookup"><span data-stu-id="dee0a-322">After the opening <xref:System.Windows.Controls.Grid> element, add the following data templates, which define how to display the expense report data:</span></span>

    [!code-xaml[ExpenseIt#30](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseReportPage.xaml#30)]

4. <span data-ttu-id="dee0a-323">Zamień <xref:System.Windows.Controls.DataGridTextColumn> elementy na <xref:System.Windows.Controls.DataGridTemplateColumn> <xref:System.Windows.Controls.DataGrid> element i Zastosuj do nich szablony.</span><span class="sxs-lookup"><span data-stu-id="dee0a-323">Replace the <xref:System.Windows.Controls.DataGridTextColumn> elements with <xref:System.Windows.Controls.DataGridTemplateColumn> under the <xref:System.Windows.Controls.DataGrid> element and apply the templates to them.</span></span>

    [!code-xaml[ExpenseIt#32](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseReportPage.xaml#32)]

5. <span data-ttu-id="dee0a-324">Skompiluj i uruchom aplikację.</span><span class="sxs-lookup"><span data-stu-id="dee0a-324">Build and run the application.</span></span>

6. <span data-ttu-id="dee0a-325">Wybierz osobę, a następnie wybierz przycisk **Wyświetl** .</span><span class="sxs-lookup"><span data-stu-id="dee0a-325">Select a person and then select the **View** button.</span></span>

<span data-ttu-id="dee0a-326">Na poniższej ilustracji przedstawiono obie strony `ExpenseIt` aplikacji z kontrolkami, układem, stylem, powiązaniem danych i szablonami danych, które zostały zastosowane:</span><span class="sxs-lookup"><span data-stu-id="dee0a-326">The following illustration shows both pages of the `ExpenseIt` application with controls, layout, styles, data binding, and data templates applied:</span></span>

![Obie strony aplikacji pokazują listę nazw i raport wydatków.](./media/walkthrough-my-first-wpf-desktop-application/application-data-templates.png)

> [!NOTE]
> <span data-ttu-id="dee0a-328">Ten przykład pokazuje konkretną funkcję WPF i nie jest zgodny ze wszystkimi najlepszymi rozwiązaniami dotyczącymi takich elementów, jak zabezpieczenia, lokalizacja i ułatwienia dostępu.</span><span class="sxs-lookup"><span data-stu-id="dee0a-328">This sample demonstrates a specific feature of WPF and doesn't follow all best practices for things like security, localization, and accessibility.</span></span> <span data-ttu-id="dee0a-329">Aby uzyskać kompleksową obsługę WPF i najlepszych rozwiązań programistycznych dotyczących projektowania aplikacji .NET, zobacz następujące tematy:</span><span class="sxs-lookup"><span data-stu-id="dee0a-329">For comprehensive coverage of WPF and the .NET app development best practices, see the following topics:</span></span>
>
> - [<span data-ttu-id="dee0a-330">Ułatwienia dostępu</span><span class="sxs-lookup"><span data-stu-id="dee0a-330">Accessibility</span></span>](../../ui-automation/accessibility-best-practices.md)
> - [<span data-ttu-id="dee0a-331">Bezpieczeństwo</span><span class="sxs-lookup"><span data-stu-id="dee0a-331">Security</span></span>](../security-wpf.md)
> - [<span data-ttu-id="dee0a-332">Globalizacja i lokalizacja WPF</span><span class="sxs-lookup"><span data-stu-id="dee0a-332">WPF globalization and localization</span></span>](../advanced/wpf-globalization-and-localization-overview.md)
> - [<span data-ttu-id="dee0a-333">Wydajność WPF</span><span class="sxs-lookup"><span data-stu-id="dee0a-333">WPF performance</span></span>](../advanced/optimizing-wpf-application-performance.md)

## <a name="next-steps"></a><span data-ttu-id="dee0a-334">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="dee0a-334">Next steps</span></span>

<span data-ttu-id="dee0a-335">W tym instruktażu przedstawiono kilka technik tworzenia interfejsu użytkownika przy użyciu Windows Presentation Foundation (WPF).</span><span class="sxs-lookup"><span data-stu-id="dee0a-335">In this walkthrough you learned a number of techniques for creating a UI using Windows Presentation Foundation (WPF).</span></span> <span data-ttu-id="dee0a-336">Należy teraz dysponować podstawową wiedzą na temat bloków konstrukcyjnych aplikacji .NET powiązanych z danymi.</span><span class="sxs-lookup"><span data-stu-id="dee0a-336">You should now have a basic understanding of the building blocks of a data-bound .NET app.</span></span> <span data-ttu-id="dee0a-337">Aby uzyskać więcej informacji na temat architektury WPF i modeli programowania, zobacz następujące tematy:</span><span class="sxs-lookup"><span data-stu-id="dee0a-337">For more information about the WPF architecture and programming models, see the following topics:</span></span>

- [<span data-ttu-id="dee0a-338">Architektura WPF</span><span class="sxs-lookup"><span data-stu-id="dee0a-338">WPF architecture</span></span>](../advanced/wpf-architecture.md)
- [<span data-ttu-id="dee0a-339">Przegląd XAML (WPF)</span><span class="sxs-lookup"><span data-stu-id="dee0a-339">XAML overview (WPF)</span></span>](../../../desktop-wpf/fundamentals/xaml.md)
- [<span data-ttu-id="dee0a-340">Przegląd właściwości zależności</span><span class="sxs-lookup"><span data-stu-id="dee0a-340">Dependency properties overview</span></span>](../advanced/dependency-properties-overview.md)
- [<span data-ttu-id="dee0a-341">Layout</span><span class="sxs-lookup"><span data-stu-id="dee0a-341">Layout</span></span>](../advanced/layout.md)

<span data-ttu-id="dee0a-342">Aby uzyskać więcej informacji na temat tworzenia aplikacji, zobacz następujące tematy:</span><span class="sxs-lookup"><span data-stu-id="dee0a-342">For more information about creating applications, see the following topics:</span></span>

- [<span data-ttu-id="dee0a-343">Opracowywanie aplikacji</span><span class="sxs-lookup"><span data-stu-id="dee0a-343">Application development</span></span>](../app-development/index.md)
- [<span data-ttu-id="dee0a-344">Formanty</span><span class="sxs-lookup"><span data-stu-id="dee0a-344">Controls</span></span>](../controls/index.md)
- [<span data-ttu-id="dee0a-345">Omówienie powiązań danych</span><span class="sxs-lookup"><span data-stu-id="dee0a-345">Data binding overview</span></span>](../../../desktop-wpf/data/data-binding-overview.md)
- [<span data-ttu-id="dee0a-346">Grafika i multimedia</span><span class="sxs-lookup"><span data-stu-id="dee0a-346">Graphics and multimedia</span></span>](../graphics-multimedia/index.md)
- [<span data-ttu-id="dee0a-347">Dokumenty w WPF</span><span class="sxs-lookup"><span data-stu-id="dee0a-347">Documents in WPF</span></span>](../advanced/documents-in-wpf.md)

## <a name="see-also"></a><span data-ttu-id="dee0a-348">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="dee0a-348">See also</span></span>

- [<span data-ttu-id="dee0a-349">Panele — Omówienie</span><span class="sxs-lookup"><span data-stu-id="dee0a-349">Panels overview</span></span>](../controls/panels-overview.md)
- [<span data-ttu-id="dee0a-350">Tworzenia szablonów danych — omówienie</span><span class="sxs-lookup"><span data-stu-id="dee0a-350">Data templating overview</span></span>](../data/data-templating-overview.md)
- [<span data-ttu-id="dee0a-351">Tworzenie aplikacji WPF</span><span class="sxs-lookup"><span data-stu-id="dee0a-351">Build a WPF application</span></span>](../app-development/building-a-wpf-application-wpf.md)
- [<span data-ttu-id="dee0a-352">Style i szablony</span><span class="sxs-lookup"><span data-stu-id="dee0a-352">Styles and templates</span></span>](../controls/styles-and-templates.md)
