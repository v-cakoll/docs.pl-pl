---
title: Tworzenie pierwszej aplikacji WPF w programie Visual Studio 2019 — .NET Framework
titleSuffix: ''
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
ms.openlocfilehash: 65b6fe31e86380162e90820c2cf118a9d1b96b4a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186584"
---
# <a name="tutorial-create-your-first-wpf-application-in-visual-studio-2019"></a><span data-ttu-id="52b1c-102">Samouczek: Tworzenie pierwszej aplikacji WPF w programie Visual Studio 2019</span><span class="sxs-lookup"><span data-stu-id="52b1c-102">Tutorial: Create your first WPF application in Visual Studio 2019</span></span>

<span data-ttu-id="52b1c-103">W tym artykule pokazano, jak opracować aplikację klasyczną Windows Presentation Foundation (WPF), która zawiera elementy, które są wspólne dla większości aplikacji WPF: Extensible Application Markup Language (XAML) znaczników, code-behind, definicje aplikacji, formantów, układu, powiązania danych i stylów.</span><span class="sxs-lookup"><span data-stu-id="52b1c-103">This article shows you how to develop a Windows Presentation Foundation (WPF) desktop application that includes the elements that are common to most WPF applications: Extensible Application Markup Language (XAML) markup, code-behind, application definitions, controls, layout, data binding, and styles.</span></span> <span data-ttu-id="52b1c-104">Aby opracować aplikację, użyjesz programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="52b1c-104">To develop the application, you'll use Visual Studio.</span></span>

<span data-ttu-id="52b1c-105">Niniejszy samouczek zawiera informacje na temat wykonywania następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="52b1c-105">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="52b1c-106">Tworzenie projektu WPF.</span><span class="sxs-lookup"><span data-stu-id="52b1c-106">Create a WPF project.</span></span>
> - <span data-ttu-id="52b1c-107">Użyj XAML, aby zaprojektować wygląd interfejsu użytkownika aplikacji.Use XAML to design the appearance of the application's user interface (UI).</span><span class="sxs-lookup"><span data-stu-id="52b1c-107">Use XAML to design the appearance of the application's user interface (UI).</span></span>
> - <span data-ttu-id="52b1c-108">Napisz kod, aby utworzyć zachowanie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="52b1c-108">Write code to build the application's behavior.</span></span>
> - <span data-ttu-id="52b1c-109">Utwórz definicję aplikacji, aby zarządzać aplikacją.</span><span class="sxs-lookup"><span data-stu-id="52b1c-109">Create an application definition to manage the application.</span></span>
> - <span data-ttu-id="52b1c-110">Dodaj formanty i utwórz układ, aby skomponować interfejs użytkownika aplikacji.</span><span class="sxs-lookup"><span data-stu-id="52b1c-110">Add controls and create the layout to compose the application UI.</span></span>
> - <span data-ttu-id="52b1c-111">Tworzenie stylów dla spójnego wyglądu w interfejsie użytkownika aplikacji.</span><span class="sxs-lookup"><span data-stu-id="52b1c-111">Create styles for a consistent appearance throughout the application's UI.</span></span>
> - <span data-ttu-id="52b1c-112">Powiąż interfejs użytkownika z danymi, zarówno w celu wypełnienia interfejsu użytkownika z danych, jak i do synchronizacji danych i interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="52b1c-112">Bind the UI to data, both to populate the UI from data and to keep the data and UI synchronized.</span></span>

<span data-ttu-id="52b1c-113">Pod koniec samouczka zostanie zbudowana autonomiczna aplikacja systemu Windows, która umożliwia użytkownikom wyświetlanie raportów wydatków dla wybranych osób.</span><span class="sxs-lookup"><span data-stu-id="52b1c-113">By the end of the tutorial, you'll have built a standalone Windows application that allows users to view expense reports for selected people.</span></span> <span data-ttu-id="52b1c-114">Aplikacja składa się z kilku stron WPF, które są hostowane w oknie stylu przeglądarki.</span><span class="sxs-lookup"><span data-stu-id="52b1c-114">The application is composed of several WPF pages that are hosted in a browser-style window.</span></span>

> [!TIP]
> <span data-ttu-id="52b1c-115">Przykładowy kod, który jest używany w tym samouczku jest dostępny zarówno dla języka Visual Basic i C# w [samouczku WPF App Sample Code](https://github.com/Microsoft/WPF-Samples/tree/master/Getting%20Started/WalkthroughFirstWPFApp).</span><span class="sxs-lookup"><span data-stu-id="52b1c-115">The sample code that is used in this tutorial is available for both Visual Basic and C# at [Tutorial WPF App Sample Code](https://github.com/Microsoft/WPF-Samples/tree/master/Getting%20Started/WalkthroughFirstWPFApp).</span></span>
>
> <span data-ttu-id="52b1c-116">Można przełączyć język kodu przykładowego kodu między C# i Visual Basic przy użyciu selektora języka na górze tej strony.</span><span class="sxs-lookup"><span data-stu-id="52b1c-116">You can toggle the code language of the sample code between C# and Visual Basic by using the language selector on top of this page.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="52b1c-117">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="52b1c-117">Prerequisites</span></span>

- <span data-ttu-id="52b1c-118">[Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) z zainstalowanym obciążeniem **dewelopera.NET desktop development** workload installed.</span><span class="sxs-lookup"><span data-stu-id="52b1c-118">[Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) with the **.NET desktop development** workload installed.</span></span>

   <span data-ttu-id="52b1c-119">Aby uzyskać więcej informacji na temat instalowania najnowszej wersji programu Visual Studio, zobacz [Instalowanie programu Visual Studio](/visualstudio/install/install-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="52b1c-119">For more information about installing the latest version of Visual Studio, see [Install Visual Studio](/visualstudio/install/install-visual-studio).</span></span>

## <a name="create-the-application-project"></a><span data-ttu-id="52b1c-120">Tworzenie projektu aplikacji</span><span class="sxs-lookup"><span data-stu-id="52b1c-120">Create the application project</span></span>

<span data-ttu-id="52b1c-121">Pierwszym krokiem jest utworzenie infrastruktury aplikacji, która zawiera definicję aplikacji, dwie strony i obraz.</span><span class="sxs-lookup"><span data-stu-id="52b1c-121">The first step is to create the application infrastructure, which includes an application definition, two pages, and an image.</span></span>

1. <span data-ttu-id="52b1c-122">Utwórz nowy projekt aplikacji WPF w języku **`ExpenseIt`** Visual Basic lub Visual C# o nazwie:</span><span class="sxs-lookup"><span data-stu-id="52b1c-122">Create a new WPF Application project in Visual Basic or Visual C# named **`ExpenseIt`**:</span></span>

   1. <span data-ttu-id="52b1c-123">Otwórz program Visual Studio i wybierz pozycję **Utwórz nowy projekt** w menu **Wprowadzenie.**</span><span class="sxs-lookup"><span data-stu-id="52b1c-123">Open Visual Studio and select **Create a new project** under the **Get started** menu.</span></span>

      <span data-ttu-id="52b1c-124">Zostanie otwarte okno dialogowe **Tworzenie nowego projektu.**</span><span class="sxs-lookup"><span data-stu-id="52b1c-124">The **Create a new project** dialog opens.</span></span>

   2. <span data-ttu-id="52b1c-125">W **menu rozwijanym Język** wybierz opcję **C#** lub **Visual Basic**.</span><span class="sxs-lookup"><span data-stu-id="52b1c-125">In the **Language** dropdown, select either **C#** or **Visual Basic**.</span></span>

   3. <span data-ttu-id="52b1c-126">Wybierz szablon **aplikacji WPF (.NET Framework),** a następnie wybierz pozycję **Dalej**.</span><span class="sxs-lookup"><span data-stu-id="52b1c-126">Select the **WPF App (.NET Framework)** template and then select **Next**.</span></span>

      ![Tworzenie nowego okna dialogowego projektu](./media/walkthrough-my-first-wpf-desktop-application/create-new-project-dialog.png)

      <span data-ttu-id="52b1c-128">Zostanie otwarte okno dialogowe **Konfigurowanie nowego projektu.**</span><span class="sxs-lookup"><span data-stu-id="52b1c-128">The **Configure your new project** dialog opens.</span></span>

   4. <span data-ttu-id="52b1c-129">Wprowadź nazwę **`ExpenseIt`** projektu, a następnie wybierz pozycję **Utwórz**.</span><span class="sxs-lookup"><span data-stu-id="52b1c-129">Enter the project name **`ExpenseIt`** and then select **Create**.</span></span>

      ![Konfigurowanie nowego okna dialogowego projektu](./media/walkthrough-my-first-wpf-desktop-application/configure-new-project-dialog.png)

      <span data-ttu-id="52b1c-131">Program Visual Studio tworzy projekt i otwiera projektanta domyślnego okna aplikacji o nazwie **MainWindow.xaml**.</span><span class="sxs-lookup"><span data-stu-id="52b1c-131">Visual Studio creates the project and opens the designer for the default application window named **MainWindow.xaml**.</span></span>

2. <span data-ttu-id="52b1c-132">Otwórz *plik Application.xaml* (Visual Basic) lub *App.xaml* (C#).</span><span class="sxs-lookup"><span data-stu-id="52b1c-132">Open *Application.xaml* (Visual Basic) or *App.xaml* (C#).</span></span>

    <span data-ttu-id="52b1c-133">Ten plik XAML definiuje aplikację WPF i wszelkie zasoby aplikacji.</span><span class="sxs-lookup"><span data-stu-id="52b1c-133">This XAML file defines a WPF application and any application resources.</span></span> <span data-ttu-id="52b1c-134">Ten plik służy również do określenia interfejsu użytkownika, w tym przypadku *MainWindow.xaml*, który automatycznie pokazuje, gdy aplikacja jest uruchamiana.</span><span class="sxs-lookup"><span data-stu-id="52b1c-134">You also use this file to specify the UI, in this case *MainWindow.xaml*, that automatically shows when the application starts.</span></span>

    <span data-ttu-id="52b1c-135">Kod XAML powinien wyglądać następująco w języku Visual Basic:</span><span class="sxs-lookup"><span data-stu-id="52b1c-135">Your XAML should look like the following in Visual Basic:</span></span>

    [!code-xaml[ExpenseIt#1_A](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/Application.xaml#1_a)]

    <span data-ttu-id="52b1c-136">I podobnie jak w języku C#:</span><span class="sxs-lookup"><span data-stu-id="52b1c-136">And like the following in C#:</span></span>

    [!code-xaml[ExpenseIt#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/App.xaml#1)]

3. <span data-ttu-id="52b1c-137">Otwórz *plik MainWindow.xaml*.</span><span class="sxs-lookup"><span data-stu-id="52b1c-137">Open *MainWindow.xaml*.</span></span>

    <span data-ttu-id="52b1c-138">Ten plik XAML jest głównym oknem aplikacji i wyświetla zawartość utworzoną na stronach.</span><span class="sxs-lookup"><span data-stu-id="52b1c-138">This XAML file is the main window of your application and displays content created in pages.</span></span> <span data-ttu-id="52b1c-139">Klasa <xref:System.Windows.Window> definiuje właściwości okna, takie jak jego tytuł, rozmiar lub ikona, i obsługuje zdarzenia, takie jak zamykanie lub ukrywanie.</span><span class="sxs-lookup"><span data-stu-id="52b1c-139">The <xref:System.Windows.Window> class defines the properties of a window, such as its title, size, or icon, and handles events, such as closing or hiding.</span></span>

4. <span data-ttu-id="52b1c-140">Zmień <xref:System.Windows.Window> element na <xref:System.Windows.Navigation.NavigationWindow>, jak pokazano w następującym XAML:</span><span class="sxs-lookup"><span data-stu-id="52b1c-140">Change the <xref:System.Windows.Window> element to a <xref:System.Windows.Navigation.NavigationWindow>, as shown in the following XAML:</span></span>

   ```xaml
   <NavigationWindow x:Class="ExpenseIt.MainWindow"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        ...
   </NavigationWindow>
   ```

   <span data-ttu-id="52b1c-141">Ta aplikacja przechodzi do różnych treści w zależności od danych wejściowych użytkownika.</span><span class="sxs-lookup"><span data-stu-id="52b1c-141">This app navigates to different content depending on the user input.</span></span> <span data-ttu-id="52b1c-142">Dlatego głównym <xref:System.Windows.Window> należy zmienić na <xref:System.Windows.Navigation.NavigationWindow>.</span><span class="sxs-lookup"><span data-stu-id="52b1c-142">This is why the main <xref:System.Windows.Window> needs to be changed to a <xref:System.Windows.Navigation.NavigationWindow>.</span></span> <span data-ttu-id="52b1c-143"><xref:System.Windows.Navigation.NavigationWindow>dziedziczy wszystkie właściwości <xref:System.Windows.Window>pliku .</span><span class="sxs-lookup"><span data-stu-id="52b1c-143"><xref:System.Windows.Navigation.NavigationWindow> inherits all the properties of <xref:System.Windows.Window>.</span></span> <span data-ttu-id="52b1c-144">Element <xref:System.Windows.Navigation.NavigationWindow> w pliku XAML tworzy wystąpienie <xref:System.Windows.Navigation.NavigationWindow> klasy.</span><span class="sxs-lookup"><span data-stu-id="52b1c-144">The <xref:System.Windows.Navigation.NavigationWindow> element in the XAML file creates an instance of the <xref:System.Windows.Navigation.NavigationWindow> class.</span></span> <span data-ttu-id="52b1c-145">Aby uzyskać więcej informacji, zobacz [Omówienie nawigacji](../app-development/navigation-overview.md).</span><span class="sxs-lookup"><span data-stu-id="52b1c-145">For more information, see [Navigation overview](../app-development/navigation-overview.md).</span></span>

5. <span data-ttu-id="52b1c-146">Usuń <xref:System.Windows.Controls.Grid> elementy z <xref:System.Windows.Navigation.NavigationWindow> między znacznikami.</span><span class="sxs-lookup"><span data-stu-id="52b1c-146">Remove the <xref:System.Windows.Controls.Grid> elements from between the <xref:System.Windows.Navigation.NavigationWindow> tags.</span></span>

6. <span data-ttu-id="52b1c-147">Zmień następujące właściwości w kodzie XAML dla <xref:System.Windows.Navigation.NavigationWindow> elementu:</span><span class="sxs-lookup"><span data-stu-id="52b1c-147">Change the following properties in the XAML code for the <xref:System.Windows.Navigation.NavigationWindow> element:</span></span>

    - <span data-ttu-id="52b1c-148">Ustaw <xref:System.Windows.Window.Title%2A> właściwość`ExpenseIt`na " ".</span><span class="sxs-lookup"><span data-stu-id="52b1c-148">Set the <xref:System.Windows.Window.Title%2A> property to "`ExpenseIt`".</span></span>

    - <span data-ttu-id="52b1c-149">Ustaw <xref:System.Windows.FrameworkElement.Height%2A> właściwość na 350 pikseli.</span><span class="sxs-lookup"><span data-stu-id="52b1c-149">Set the <xref:System.Windows.FrameworkElement.Height%2A> property to 350 pixels.</span></span>

    - <span data-ttu-id="52b1c-150">Ustaw <xref:System.Windows.FrameworkElement.Width%2A> właściwość na 500 pikseli.</span><span class="sxs-lookup"><span data-stu-id="52b1c-150">Set the <xref:System.Windows.FrameworkElement.Width%2A> property to 500 pixels.</span></span>

    <span data-ttu-id="52b1c-151">Kod XAML powinien wyglądać następująco w przypadku języka Visual Basic:</span><span class="sxs-lookup"><span data-stu-id="52b1c-151">Your XAML should look like the following for Visual Basic:</span></span>

    [!code-xaml[ExpenseIt#2_A](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt/MainWindow.xaml#2_a)]

    <span data-ttu-id="52b1c-152">I podobnie jak następujące dla Języka C#:</span><span class="sxs-lookup"><span data-stu-id="52b1c-152">And like the following for C#:</span></span>

    [!code-xaml[ExpenseIt#2](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/MainWindow.xaml#2)]

7. <span data-ttu-id="52b1c-153">Otwórz *plik MainWindow.xaml.vb* lub *MainWindow.xaml.cs*.</span><span class="sxs-lookup"><span data-stu-id="52b1c-153">Open *MainWindow.xaml.vb* or *MainWindow.xaml.cs*.</span></span>

    <span data-ttu-id="52b1c-154">Ten plik jest plikiem związanym z kodem, który zawiera kod do obsługi zdarzeń zadeklarowanych w *pliku MainWindow.xaml*.</span><span class="sxs-lookup"><span data-stu-id="52b1c-154">This file is a code-behind file that contains code to handle the events declared in *MainWindow.xaml*.</span></span> <span data-ttu-id="52b1c-155">Ten plik zawiera klasę częściową dla okna zdefiniowanego w języku XAML.</span><span class="sxs-lookup"><span data-stu-id="52b1c-155">This file contains a partial class for the window defined in XAML.</span></span>

8. <span data-ttu-id="52b1c-156">Jeśli używasz języka C#, `MainWindow` zmień klasę, <xref:System.Windows.Navigation.NavigationWindow>z której ma pochodzić .</span><span class="sxs-lookup"><span data-stu-id="52b1c-156">If you're using C#, change the `MainWindow` class to derive from <xref:System.Windows.Navigation.NavigationWindow>.</span></span> <span data-ttu-id="52b1c-157">(W języku Visual Basic dzieje się to automatycznie po zmianie okna w języku XAML). Twój kod języka C# powinien teraz wyglądać następująco:</span><span class="sxs-lookup"><span data-stu-id="52b1c-157">(In Visual Basic, this happens automatically when you change the window in XAML.) Your C# code should now look like this:</span></span>

   [!code-csharp[ExpenseIt#3](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/MainWindow.xaml.cs?highlight=21)]

## <a name="add-files-to-the-application"></a><span data-ttu-id="52b1c-158">Dodawanie plików do aplikacji</span><span class="sxs-lookup"><span data-stu-id="52b1c-158">Add files to the application</span></span>

<span data-ttu-id="52b1c-159">W tej sekcji dodasz dwie strony i obraz do aplikacji.</span><span class="sxs-lookup"><span data-stu-id="52b1c-159">In this section, you'll add two pages and an image to the application.</span></span>

1. <span data-ttu-id="52b1c-160">Dodaj nową stronę do projektu i *`ExpenseItHome.xaml`* nazwij ją:</span><span class="sxs-lookup"><span data-stu-id="52b1c-160">Add a new page to the project, and name it *`ExpenseItHome.xaml`*:</span></span>

   1. <span data-ttu-id="52b1c-161">W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy węzeł **`ExpenseIt`** projektu i wybierz polecenie **Dodaj** > **stronę**.</span><span class="sxs-lookup"><span data-stu-id="52b1c-161">In **Solution Explorer**, right-click on the **`ExpenseIt`** project node and choose **Add** > **Page**.</span></span>

   1. <span data-ttu-id="52b1c-162">W oknie dialogowym **Dodawanie nowego elementu** szablon Strony **(WPF)** jest już zaznaczony.</span><span class="sxs-lookup"><span data-stu-id="52b1c-162">In the **Add New Item** dialog, the **Page (WPF)** template is already selected.</span></span> <span data-ttu-id="52b1c-163">Wprowadź nazwę **`ExpenseItHome`**, a następnie wybierz pozycję **Dodaj**.</span><span class="sxs-lookup"><span data-stu-id="52b1c-163">Enter the name **`ExpenseItHome`**, and then select **Add**.</span></span>

    <span data-ttu-id="52b1c-164">Ta strona jest pierwszą stroną wyświetlaną po uruchomieniu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="52b1c-164">This page is the first page that's displayed when the application is launched.</span></span> <span data-ttu-id="52b1c-165">Wyświetli listę osób do wyboru, aby wyświetlić raport z wydatków.</span><span class="sxs-lookup"><span data-stu-id="52b1c-165">It will show a list of people to select from, to show an expense report for.</span></span>

1. <span data-ttu-id="52b1c-166">Otwórz *`ExpenseItHome.xaml`*.</span><span class="sxs-lookup"><span data-stu-id="52b1c-166">Open *`ExpenseItHome.xaml`*.</span></span>

1. <span data-ttu-id="52b1c-167">Ustaw <xref:System.Windows.Controls.Page.Title%2A> na`ExpenseIt - Home`" ".</span><span class="sxs-lookup"><span data-stu-id="52b1c-167">Set the <xref:System.Windows.Controls.Page.Title%2A> to "`ExpenseIt - Home`".</span></span>

1. <span data-ttu-id="52b1c-168">Ustaw `DesignHeight` na 350 pikseli `DesignWidth` i na 500 pikseli.</span><span class="sxs-lookup"><span data-stu-id="52b1c-168">Set the `DesignHeight` to 350 pixels and the `DesignWidth` to 500 pixels.</span></span>

    <span data-ttu-id="52b1c-169">Kod XAML jest teraz wyświetlany w następujący sposób dla języka Visual Basic:</span><span class="sxs-lookup"><span data-stu-id="52b1c-169">The XAML now appears as follows for Visual Basic:</span></span>

    [!code-xaml[ExpenseIt#6_A](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseItHome.xaml#6_a)]

    <span data-ttu-id="52b1c-170">I podobnie jak następujące dla Języka C#:</span><span class="sxs-lookup"><span data-stu-id="52b1c-170">And like the following for C#:</span></span>

    [!code-xaml[ExpenseIt#6](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt2/ExpenseItHome.xaml#6)]

1. <span data-ttu-id="52b1c-171">Otwórz *plik MainWindow.xaml*.</span><span class="sxs-lookup"><span data-stu-id="52b1c-171">Open *MainWindow.xaml*.</span></span>

1. <span data-ttu-id="52b1c-172">Dodaj <xref:System.Windows.Navigation.NavigationWindow.Source%2A> właściwość <xref:System.Windows.Navigation.NavigationWindow> do elementu i`ExpenseItHome.xaml`ustaw ją na " ".</span><span class="sxs-lookup"><span data-stu-id="52b1c-172">Add a <xref:System.Windows.Navigation.NavigationWindow.Source%2A> property to the <xref:System.Windows.Navigation.NavigationWindow> element and set it to "`ExpenseItHome.xaml`".</span></span>

    <span data-ttu-id="52b1c-173">Spowoduje *`ExpenseItHome.xaml`* to ustawienie pierwszej strony otwartej po uruchomieniu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="52b1c-173">This sets *`ExpenseItHome.xaml`* to be the first page opened when the application starts.</span></span>

    <span data-ttu-id="52b1c-174">Przykładowy kod XAML w języku Visual Basic:</span><span class="sxs-lookup"><span data-stu-id="52b1c-174">Example XAML in Visual Basic:</span></span>

    [!code-xaml[ExpenseIt#7_A](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/MainWindow.xaml#7_a)]

    <span data-ttu-id="52b1c-175">A w języku C#:</span><span class="sxs-lookup"><span data-stu-id="52b1c-175">And in C#:</span></span>

    [!code-xaml[ExpenseIt#7](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt2/MainWindow.xaml#7)]

   > [!TIP]
   > <span data-ttu-id="52b1c-176">Można również ustawić **Source** właściwość w **kategorii Różne** **właściwości** okna.</span><span class="sxs-lookup"><span data-stu-id="52b1c-176">You can also set the **Source** property in the **Miscellaneous** category of the **Properties** window.</span></span>
   >
   > ![Właściwość źródłowych w oknie Właściwości](./media/properties-source.png)

1. <span data-ttu-id="52b1c-178">Dodaj kolejną nową stronę WPF do projektu i nadaj jej *nazwę ExpenseReportPage.xaml*::</span><span class="sxs-lookup"><span data-stu-id="52b1c-178">Add another new WPF page to the project, and name it *ExpenseReportPage.xaml*::</span></span>

   1. <span data-ttu-id="52b1c-179">W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy węzeł **`ExpenseIt`** projektu i wybierz polecenie **Dodaj** > **stronę**.</span><span class="sxs-lookup"><span data-stu-id="52b1c-179">In **Solution Explorer**, right-click on the **`ExpenseIt`** project node and choose **Add** > **Page**.</span></span>

   1. <span data-ttu-id="52b1c-180">W oknie dialogowym **Dodawanie nowego elementu** wybierz szablon Strona **(WPF).**</span><span class="sxs-lookup"><span data-stu-id="52b1c-180">In the **Add New Item** dialog, select the **Page (WPF)** template.</span></span> <span data-ttu-id="52b1c-181">Wprowadź nazwę **ExpenseReportPage**, a następnie wybierz pozycję **Dodaj**.</span><span class="sxs-lookup"><span data-stu-id="52b1c-181">Enter the name **ExpenseReportPage**, and then select **Add**.</span></span>

    <span data-ttu-id="52b1c-182">Na tej stronie zostanie wyświetlona raport z **`ExpenseItHome`** wydatków dla osoby wybranej na stronie.</span><span class="sxs-lookup"><span data-stu-id="52b1c-182">This page will show the expense report for the person that is selected on the **`ExpenseItHome`** page.</span></span>

1. <span data-ttu-id="52b1c-183">Otwórz *plik ExpenseReportPage.xaml*.</span><span class="sxs-lookup"><span data-stu-id="52b1c-183">Open *ExpenseReportPage.xaml*.</span></span>

1. <span data-ttu-id="52b1c-184">Ustaw <xref:System.Windows.Controls.Page.Title%2A> na`ExpenseIt - View Expense`" ".</span><span class="sxs-lookup"><span data-stu-id="52b1c-184">Set the <xref:System.Windows.Controls.Page.Title%2A> to "`ExpenseIt - View Expense`".</span></span>

1. <span data-ttu-id="52b1c-185">Ustaw `DesignHeight` na 350 pikseli `DesignWidth` i na 500 pikseli.</span><span class="sxs-lookup"><span data-stu-id="52b1c-185">Set the `DesignHeight` to 350 pixels and the `DesignWidth` to 500 pixels.</span></span>

    <span data-ttu-id="52b1c-186">*ExpenseReportPage.xaml* wygląda teraz następująco w języku Visual Basic:</span><span class="sxs-lookup"><span data-stu-id="52b1c-186">*ExpenseReportPage.xaml* now looks like the following in Visual Basic:</span></span>

    [!code-xaml[ExpenseIt#4_A](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseReportPage.xaml#4_a)]

    <span data-ttu-id="52b1c-187">I podobnie jak w języku C#:</span><span class="sxs-lookup"><span data-stu-id="52b1c-187">And like the following in C#:</span></span>

    [!code-xaml[ExpenseIt#4](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/ExpenseReportPage.xaml#4)]

1. <span data-ttu-id="52b1c-188">Otwórz *expenseItHome.xaml.vb* i *ExpenseReportPage.xaml.vb*lub *ExpenseItHome.xaml.cs* i *ExpenseReportPage.xaml.cs*.</span><span class="sxs-lookup"><span data-stu-id="52b1c-188">Open *ExpenseItHome.xaml.vb* and *ExpenseReportPage.xaml.vb*, or *ExpenseItHome.xaml.cs* and *ExpenseReportPage.xaml.cs*.</span></span>

    <span data-ttu-id="52b1c-189">Podczas tworzenia nowego pliku strony program Visual Studio automatycznie tworzy plik *związany z kodem.*</span><span class="sxs-lookup"><span data-stu-id="52b1c-189">When you create a new Page file, Visual Studio automatically creates its *code-behind* file.</span></span> <span data-ttu-id="52b1c-190">Te pliki związane z kodem obsługują logikę odpowiadania na dane wejściowe użytkownika.</span><span class="sxs-lookup"><span data-stu-id="52b1c-190">These code-behind files handle the logic for responding to user input.</span></span>

    <span data-ttu-id="52b1c-191">Kod powinien wyglądać następująco **`ExpenseItHome`** dla:</span><span class="sxs-lookup"><span data-stu-id="52b1c-191">Your code should look like the following for **`ExpenseItHome`**:</span></span>

    [!code-csharp[ExpenseIt#2_5](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt2/ExpenseItHome.xaml.cs#2_5)]

    [!code-vb[ExpenseIt#2_5](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseItHome.xaml.vb#2_5)]

    <span data-ttu-id="52b1c-192">I podobnie jak następujące dla **ExpenseReportPage:**</span><span class="sxs-lookup"><span data-stu-id="52b1c-192">And like the following for **ExpenseReportPage**:</span></span>

    [!code-csharp[ExpenseIt#5](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/ExpenseReportPage.xaml.cs#5)]

    [!code-vb[ExpenseIt#5](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseReportPage.xaml.vb#5)]

1. <span data-ttu-id="52b1c-193">Dodaj do projektu obraz o nazwie *watermark.png.*</span><span class="sxs-lookup"><span data-stu-id="52b1c-193">Add an image named *watermark.png* to the project.</span></span> <span data-ttu-id="52b1c-194">Można utworzyć własny obraz, skopiować plik z przykładowego kodu lub pobrać go z repozytorium GitHub [microsoft/WPF-Samples.](https://raw.githubusercontent.com/microsoft/WPF-Samples/master/Getting%20Started/WalkthroughFirstWPFApp/csharp/watermark.png)</span><span class="sxs-lookup"><span data-stu-id="52b1c-194">You can create your own image, copy the file from the sample code, or get it from the [microsoft/WPF-Samples](https://raw.githubusercontent.com/microsoft/WPF-Samples/master/Getting%20Started/WalkthroughFirstWPFApp/csharp/watermark.png) GitHub repository.</span></span>

    1. <span data-ttu-id="52b1c-195">Kliknij prawym przyciskiem myszy węzeł projektu i wybierz polecenie **Dodaj** > **istniejący element**lub naciśnij klawisz **Shift**+**Alt**+**A**.</span><span class="sxs-lookup"><span data-stu-id="52b1c-195">Right-click on the project node and select **Add** > **Existing Item**, or press **Shift**+**Alt**+**A**.</span></span>

    2. <span data-ttu-id="52b1c-196">W oknie dialogowym **Dodawanie istniejącego elementu** ustaw filtr plików na **Wszystkie pliki** lub Pliki **obrazów,** przejdź do pliku obrazu, którego chcesz użyć, a następnie wybierz pozycję **Dodaj**.</span><span class="sxs-lookup"><span data-stu-id="52b1c-196">In the **Add Existing Item** dialog, set the file filter to either **All Files** or **Image Files**, browse to the image file you want to use, and then select **Add**.</span></span>

## <a name="build-and-run-the-application"></a><span data-ttu-id="52b1c-197">Kompilowanie i uruchamianie aplikacji</span><span class="sxs-lookup"><span data-stu-id="52b1c-197">Build and run the application</span></span>

1. <span data-ttu-id="52b1c-198">Aby utworzyć i uruchomić aplikację, naciśnij **klawisz F5** lub wybierz **polecenie Rozpocznij debugowanie** z menu **Debugowania.**</span><span class="sxs-lookup"><span data-stu-id="52b1c-198">To build and run the application, press **F5** or select **Start Debugging** from the **Debug** menu.</span></span>

    <span data-ttu-id="52b1c-199">Na poniższej ilustracji <xref:System.Windows.Navigation.NavigationWindow> przedstawiono aplikację za pomocą przycisków:</span><span class="sxs-lookup"><span data-stu-id="52b1c-199">The following illustration shows the application with the <xref:System.Windows.Navigation.NavigationWindow> buttons:</span></span>

    ![Aplikacja po utworzeniu i uruchomieniu go.](./media/walkthrough-my-first-wpf-desktop-application/build-run-application.png)

2. <span data-ttu-id="52b1c-201">Zamknij aplikację, aby powrócić do programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="52b1c-201">Close the application to return to Visual Studio.</span></span>

## <a name="create-the-layout"></a><span data-ttu-id="52b1c-202">Tworzenie układu</span><span class="sxs-lookup"><span data-stu-id="52b1c-202">Create the layout</span></span>

<span data-ttu-id="52b1c-203">Układ zapewnia uporządkowany sposób umieszczania elementów interfejsu użytkownika, a także zarządza rozmiarem i położeniem tych elementów po przesiąknięciu rozmiaru interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="52b1c-203">Layout provides an ordered way to place UI elements, and also manages the size and position of those elements when a UI is resized.</span></span> <span data-ttu-id="52b1c-204">Zazwyczaj tworzy się układ z jednym z następujących formantów układu:</span><span class="sxs-lookup"><span data-stu-id="52b1c-204">You typically create a layout with one of the following layout controls:</span></span>

- <span data-ttu-id="52b1c-205"><xref:System.Windows.Controls.Canvas>- Definiuje obszar, w którym można jawnie umieszczać elementy podrzędne przy użyciu współrzędnych, które są względem obszaru Kanwy.</span><span class="sxs-lookup"><span data-stu-id="52b1c-205"><xref:System.Windows.Controls.Canvas> - Defines an area within which you can explicitly position child elements by using coordinates that are relative to the Canvas area.</span></span>
- <span data-ttu-id="52b1c-206"><xref:System.Windows.Controls.DockPanel>- Definiuje obszar, w którym można rozmieścić elementy podrzędne poziomo lub pionowo, względem siebie.</span><span class="sxs-lookup"><span data-stu-id="52b1c-206"><xref:System.Windows.Controls.DockPanel> - Defines an area where you can arrange child elements either horizontally or vertically, relative to each other.</span></span>
- <span data-ttu-id="52b1c-207"><xref:System.Windows.Controls.Grid>- Definiuje elastyczny obszar siatki, który składa się z kolumn i wierszy.</span><span class="sxs-lookup"><span data-stu-id="52b1c-207"><xref:System.Windows.Controls.Grid> - Defines a flexible grid area that consists of columns and rows.</span></span>
- <span data-ttu-id="52b1c-208"><xref:System.Windows.Controls.StackPanel>- Rozmieszcza elementy podrzędne w jednej linii, która może być zorientowana poziomo lub pionowo.</span><span class="sxs-lookup"><span data-stu-id="52b1c-208"><xref:System.Windows.Controls.StackPanel> - Arranges child elements into a single line that can be oriented horizontally or vertically.</span></span>
- <span data-ttu-id="52b1c-209"><xref:System.Windows.Controls.VirtualizingStackPanel>- Rozmieszcza i wirtualizuje zawartość w jednym wierszu, który jest zorientowany poziomo lub pionowo.</span><span class="sxs-lookup"><span data-stu-id="52b1c-209"><xref:System.Windows.Controls.VirtualizingStackPanel> - Arranges and virtualizes content on a single line that is oriented either horizontally or vertically.</span></span>
- <span data-ttu-id="52b1c-210"><xref:System.Windows.Controls.WrapPanel>- Umieszcza elementy podrzędne w pozycji sekwencyjnej od lewej do prawej, przebijając zawartość do następnego wiersza na krawędzi pola zawierającego.</span><span class="sxs-lookup"><span data-stu-id="52b1c-210"><xref:System.Windows.Controls.WrapPanel> - Positions child elements in sequential position from left to right, breaking content to the next line at the edge of the containing box.</span></span> <span data-ttu-id="52b1c-211">Kolejne porządkowanie odbywa się sekwencyjnie od góry do dołu lub od prawej do lewej, w zależności od wartości Orientation właściwości.</span><span class="sxs-lookup"><span data-stu-id="52b1c-211">Subsequent ordering happens sequentially from top to bottom or from right to left, depending on the value of the Orientation property.</span></span>

<span data-ttu-id="52b1c-212">Każdy z tych formantów układu obsługuje określonego typu układu dla jego elementów podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="52b1c-212">Each of these layout controls supports a particular type of layout for its child elements.</span></span> <span data-ttu-id="52b1c-213">`ExpenseIt`można zwymiarować strony, a każda strona ma elementy rozmieszczone poziomo i pionowo obok innych elementów.</span><span class="sxs-lookup"><span data-stu-id="52b1c-213">`ExpenseIt` pages can be resized, and each page has elements that are arranged horizontally and vertically alongside other elements.</span></span> <span data-ttu-id="52b1c-214">W tym przykładzie <xref:System.Windows.Controls.Grid> jest używany jako element układu dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="52b1c-214">In this example, the <xref:System.Windows.Controls.Grid> is used as  layout element for the application.</span></span>

> [!TIP]
> <span data-ttu-id="52b1c-215">Aby uzyskać <xref:System.Windows.Controls.Panel> więcej informacji o elementach, zobacz [Omówienie paneli](../controls/panels-overview.md).</span><span class="sxs-lookup"><span data-stu-id="52b1c-215">For more information about <xref:System.Windows.Controls.Panel> elements, see [Panels overview](../controls/panels-overview.md).</span></span> <span data-ttu-id="52b1c-216">Aby uzyskać więcej informacji o układzie, zobacz [Układ](../advanced/layout.md).</span><span class="sxs-lookup"><span data-stu-id="52b1c-216">For more information about layout, see [Layout](../advanced/layout.md).</span></span>

<span data-ttu-id="52b1c-217">W tej sekcji utworzysz tabelę jednokolumnową z trzema wierszami i marginesem <xref:System.Windows.Controls.Grid> 10 pikseli, dodając definicje kolumn i wierszy do w *`ExpenseItHome.xaml`*.</span><span class="sxs-lookup"><span data-stu-id="52b1c-217">In this section, you create a single-column table with three rows and a 10-pixel margin by adding column and row definitions to the <xref:System.Windows.Controls.Grid> in *`ExpenseItHome.xaml`*.</span></span>

1. <span data-ttu-id="52b1c-218">W *`ExpenseItHome.xaml`*, <xref:System.Windows.FrameworkElement.Margin%2A> ustaw właściwość na elemencie <xref:System.Windows.Controls.Grid> na "10,0,10,10", co odpowiada marginesom lewym, górnym, prawym i dolnym marginesem:</span><span class="sxs-lookup"><span data-stu-id="52b1c-218">In *`ExpenseItHome.xaml`*, set the <xref:System.Windows.FrameworkElement.Margin%2A> property on the <xref:System.Windows.Controls.Grid> element to "10,0,10,10", which corresponds to left, top, right and bottom margins:</span></span>

   ```xaml
   <Grid Margin="10,0,10,10">
   ```

   > [!TIP]
   > <span data-ttu-id="52b1c-219">Można również ustawić wartości **marginesu** w oknie **Właściwości** w kategorii **Układ:**</span><span class="sxs-lookup"><span data-stu-id="52b1c-219">You can also set the **Margin** values in the **Properties** window, under the **Layout** category:</span></span>
   >
   > ![Wartości marginesu w oknie Właściwości](./media/properties-margin.png)

2. <span data-ttu-id="52b1c-221">Dodaj następujący kod XAML między znacznikami, <xref:System.Windows.Controls.Grid> aby utworzyć definicje wierszy i kolumn:</span><span class="sxs-lookup"><span data-stu-id="52b1c-221">Add the following XAML between the <xref:System.Windows.Controls.Grid> tags to create the row and column definitions:</span></span>

    [!code-xaml[ExpenseIt#8](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt3/ExpenseItHome.xaml#8)]

    <span data-ttu-id="52b1c-222">Dwa <xref:System.Windows.Controls.RowDefinition.Height%2A> wiersze jest ustawiona na <xref:System.Windows.GridLength.Auto%2A>, co oznacza, że wiersze są wielkości na podstawie zawartości w wierszach.</span><span class="sxs-lookup"><span data-stu-id="52b1c-222">The <xref:System.Windows.Controls.RowDefinition.Height%2A> of two rows is set to <xref:System.Windows.GridLength.Auto%2A>, which means that the rows are sized based on the content in the rows.</span></span> <span data-ttu-id="52b1c-223">Wartością <xref:System.Windows.Controls.RowDefinition.Height%2A> <xref:System.Windows.GridUnitType.Star> domyślną jest zmiana rozmiaru, co oznacza, że wysokość wiersza jest ważoną proporcją dostępnego miejsca.</span><span class="sxs-lookup"><span data-stu-id="52b1c-223">The default <xref:System.Windows.Controls.RowDefinition.Height%2A> is <xref:System.Windows.GridUnitType.Star> sizing, which means that the row height is a weighted proportion of the available space.</span></span> <span data-ttu-id="52b1c-224">Na przykład, jeśli dwa <xref:System.Windows.Controls.RowDefinition.Height%2A> wiersze mają a "\*", każdy z nich ma wysokość, która stanowi połowę dostępnego miejsca.</span><span class="sxs-lookup"><span data-stu-id="52b1c-224">For example if two rows each have a <xref:System.Windows.Controls.RowDefinition.Height%2A> of "\*", they each have a height that is half of the available space.</span></span>

    <span data-ttu-id="52b1c-225">Teraz <xref:System.Windows.Controls.Grid> powinien zawierać następujący kod XAML:</span><span class="sxs-lookup"><span data-stu-id="52b1c-225">Your <xref:System.Windows.Controls.Grid> should now contain the following XAML:</span></span>

    [!code-xaml[ExpenseIt#9](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt3/ExpenseItHome.xaml#9)]

## <a name="add-controls"></a><span data-ttu-id="52b1c-226">Dodawanie kontrolek</span><span class="sxs-lookup"><span data-stu-id="52b1c-226">Add controls</span></span>

<span data-ttu-id="52b1c-227">W tej sekcji zaktualizujesz interfejs użytkownika strony głównej, aby wyświetlić listę osób, w której wybierzesz jedną osobę do wyświetlenia raportu z wydatków.</span><span class="sxs-lookup"><span data-stu-id="52b1c-227">In this section, you'll update the home page UI to show a list of people, where you select one person to display their expense report.</span></span> <span data-ttu-id="52b1c-228">Formanty są obiekty interfejsu użytkownika, które umożliwiają użytkownikom interakcję z aplikacją.</span><span class="sxs-lookup"><span data-stu-id="52b1c-228">Controls are UI objects that allow users to interact with your application.</span></span> <span data-ttu-id="52b1c-229">Aby uzyskać więcej informacji, zobacz [Formanty](../controls/index.md).</span><span class="sxs-lookup"><span data-stu-id="52b1c-229">For more information, see [Controls](../controls/index.md).</span></span>

<span data-ttu-id="52b1c-230">Aby utworzyć ten interfejs użytkownika, do: *`ExpenseItHome.xaml`*</span><span class="sxs-lookup"><span data-stu-id="52b1c-230">To create this UI, you'll add the following elements to *`ExpenseItHome.xaml`*:</span></span>

- <span data-ttu-id="52b1c-231">A <xref:System.Windows.Controls.ListBox> (dla listy osób).</span><span class="sxs-lookup"><span data-stu-id="52b1c-231">A <xref:System.Windows.Controls.ListBox> (for the list of people).</span></span>
- <span data-ttu-id="52b1c-232">A <xref:System.Windows.Controls.Label> (dla nagłówka listy).</span><span class="sxs-lookup"><span data-stu-id="52b1c-232">A <xref:System.Windows.Controls.Label> (for the list header).</span></span>
- <span data-ttu-id="52b1c-233">A <xref:System.Windows.Controls.Button> (aby kliknąć, aby wyświetlić raport z wydatków dla osoby wybranej na liście).</span><span class="sxs-lookup"><span data-stu-id="52b1c-233">A <xref:System.Windows.Controls.Button> (to click to view the expense report for the person that is selected in the list).</span></span>

<span data-ttu-id="52b1c-234">Każdy formant jest umieszczany <xref:System.Windows.Controls.Grid> w <xref:System.Windows.Controls.Grid.Row%2A?displayProperty=nameWithType> wierszu, ustawiając dołączoną właściwość.</span><span class="sxs-lookup"><span data-stu-id="52b1c-234">Each control is placed in a row of the <xref:System.Windows.Controls.Grid> by setting the <xref:System.Windows.Controls.Grid.Row%2A?displayProperty=nameWithType> attached property.</span></span> <span data-ttu-id="52b1c-235">Aby uzyskać więcej informacji na temat dołączonych właściwości, zobacz [Omówienie dołączonych właściwości](../advanced/attached-properties-overview.md).</span><span class="sxs-lookup"><span data-stu-id="52b1c-235">For more information about attached properties, see [Attached Properties Overview](../advanced/attached-properties-overview.md).</span></span>

1. <span data-ttu-id="52b1c-236">W *`ExpenseItHome.xaml`*, dodaj następujący kod XAML gdzieś między <xref:System.Windows.Controls.Grid> znacznikami:</span><span class="sxs-lookup"><span data-stu-id="52b1c-236">In *`ExpenseItHome.xaml`*, add the following XAML somewhere between the <xref:System.Windows.Controls.Grid> tags:</span></span>

   [!code-xaml[ExpenseIt#10](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt4/ExpenseItHome.xaml#10)]

   > [!TIP]
   > <span data-ttu-id="52b1c-237">Formanty można również utworzyć, przeciągając je z okna **Przybornika** do okna projektu, a następnie ustawiając ich właściwości w oknie **Właściwości.**</span><span class="sxs-lookup"><span data-stu-id="52b1c-237">You can also create the controls by dragging them from the **Toolbox** window onto the design window, and then setting their properties in the **Properties** window.</span></span>

2. <span data-ttu-id="52b1c-238">Skompiluj i uruchom aplikację.</span><span class="sxs-lookup"><span data-stu-id="52b1c-238">Build and run the application.</span></span>

    <span data-ttu-id="52b1c-239">Na poniższej ilustracji przedstawiono utworzone kontrolki:</span><span class="sxs-lookup"><span data-stu-id="52b1c-239">The following illustration shows the controls you created:</span></span>

![ExpenseIt przykładowy zrzut ekranu przedstawiający listę nazw](./media/walkthrough-my-first-wpf-desktop-application/add-application-controls.png)

## <a name="add-an-image-and-a-title"></a><span data-ttu-id="52b1c-241">Dodawanie obrazu i tytułu</span><span class="sxs-lookup"><span data-stu-id="52b1c-241">Add an image and a title</span></span>

<span data-ttu-id="52b1c-242">W tej sekcji zaktualizujesz interfejs użytkownika strony głównej o obraz i tytuł strony.</span><span class="sxs-lookup"><span data-stu-id="52b1c-242">In this section, you'll update the home page UI with an image and a page title.</span></span>

1. <span data-ttu-id="52b1c-243">W *`ExpenseItHome.xaml`* obszarze dodaj kolejną kolumnę <xref:System.Windows.Controls.Grid.ColumnDefinitions%2A> do kolumny o stałej liczbie <xref:System.Windows.Controls.ColumnDefinition.Width%2A> 230 pikseli:</span><span class="sxs-lookup"><span data-stu-id="52b1c-243">In *`ExpenseItHome.xaml`*, add another column to the <xref:System.Windows.Controls.Grid.ColumnDefinitions%2A> with a fixed <xref:System.Windows.Controls.ColumnDefinition.Width%2A> of 230 pixels:</span></span>

    [!code-xaml[ExpenseIt#11](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseItHome.xaml?highlight=52-55)]

2. <span data-ttu-id="52b1c-244">Dodaj kolejny wiersz <xref:System.Windows.Controls.Grid.RowDefinitions%2A>do , w sumie cztery wiersze:</span><span class="sxs-lookup"><span data-stu-id="52b1c-244">Add another row to the <xref:System.Windows.Controls.Grid.RowDefinitions%2A>, for a total of four rows:</span></span>

    [!code-xaml[ExpenseIt#11b](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseItHome.xaml?highlight=57-62)]

3. <span data-ttu-id="52b1c-245">Przenieś formanty do drugiej <xref:System.Windows.Controls.Grid.Column%2A?displayProperty=nameWithType> kolumny, ustawiając właściwość na 1 w każdym z trzech formantów (Border, ListBox i Button).</span><span class="sxs-lookup"><span data-stu-id="52b1c-245">Move the controls to the second column by setting the <xref:System.Windows.Controls.Grid.Column%2A?displayProperty=nameWithType> property to 1 in each of the three controls (Border, ListBox, and Button).</span></span>

4. <span data-ttu-id="52b1c-246">Przenieś każdy formant w dół wiersza, zwiększając jego <xref:System.Windows.Controls.Grid.Row%2A?displayProperty=nameWithType> wartość o 1 dla każdego z trzech formantów (Border, ListBox i Button) i dla Border element.</span><span class="sxs-lookup"><span data-stu-id="52b1c-246">Move each control down a row by incrementing its <xref:System.Windows.Controls.Grid.Row%2A?displayProperty=nameWithType> value by 1 for each of the three controls (Border, ListBox, and Button) and for the Border element.</span></span>

   <span data-ttu-id="52b1c-247">Kod XAML dla trzech formantów wygląda teraz następująco:</span><span class="sxs-lookup"><span data-stu-id="52b1c-247">The XAML for the three controls now looks like the following:</span></span>

    [!code-xaml[ExpenseIt#12](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#12)]

5. <span data-ttu-id="52b1c-248">Ustaw <xref:System.Windows.Controls.Panel.Background%2A?displayProperty=nameWithType> właściwość na plik obrazu *watermark.png,* dodając następujący kod `<Grid>` `</Grid>` XAML w dowolnym miejscu między tagami i:</span><span class="sxs-lookup"><span data-stu-id="52b1c-248">Set the <xref:System.Windows.Controls.Panel.Background%2A?displayProperty=nameWithType> property to the *watermark.png* image file, by adding the following XAML anywhere between the `<Grid>` and `</Grid>` tags:</span></span>

    [!code-xaml[ExpenseIt#14](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#14)]

6. <span data-ttu-id="52b1c-249">Przed <xref:System.Windows.Controls.Border> elementem dodaj <xref:System.Windows.Controls.Label> a z zawartością "Wyświetl raport z wydatków".</span><span class="sxs-lookup"><span data-stu-id="52b1c-249">Before the <xref:System.Windows.Controls.Border> element, add a <xref:System.Windows.Controls.Label> with the content "View Expense Report".</span></span> <span data-ttu-id="52b1c-250">Ta etykieta jest tytułem strony.</span><span class="sxs-lookup"><span data-stu-id="52b1c-250">This label is the title of the page.</span></span>

    [!code-xaml[ExpenseIt#13](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#13)]

7. <span data-ttu-id="52b1c-251">Skompiluj i uruchom aplikację.</span><span class="sxs-lookup"><span data-stu-id="52b1c-251">Build and run the application.</span></span>

<span data-ttu-id="52b1c-252">Na poniższej ilustracji przedstawiono wyniki tego, co właśnie dodano:</span><span class="sxs-lookup"><span data-stu-id="52b1c-252">The following illustration shows the results of what you just added:</span></span>

![ExpenseIt przykładowy zrzut ekranu przedstawiający nowe tło obrazu i tytuł strony](./media/walkthrough-my-first-wpf-desktop-application/add-application-image-title.png)

## <a name="add-code-to-handle-events"></a><span data-ttu-id="52b1c-254">Dodawanie kodu do obsługi zdarzeń</span><span class="sxs-lookup"><span data-stu-id="52b1c-254">Add code to handle events</span></span>

1. <span data-ttu-id="52b1c-255">W *`ExpenseItHome.xaml`* programie <xref:System.Windows.Controls.Primitives.ButtonBase.Click> dodaj program <xref:System.Windows.Controls.Button> obsługi zdarzeń do elementu.</span><span class="sxs-lookup"><span data-stu-id="52b1c-255">In *`ExpenseItHome.xaml`*, add a <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event handler to the <xref:System.Windows.Controls.Button> element.</span></span> <span data-ttu-id="52b1c-256">Aby uzyskać więcej informacji, zobacz [Jak: Tworzenie prostego programu obsługi zdarzeń](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/bb675300(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="52b1c-256">For more information, see [How to: Create a simple event handler](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/bb675300(v=vs.100)).</span></span>

    [!code-xaml[ExpenseIt#15](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt6/ExpenseItHome.xaml#15)]

2. <span data-ttu-id="52b1c-257">Otwórz *`ExpenseItHome.xaml.vb`* *`ExpenseItHome.xaml.cs`* lub .</span><span class="sxs-lookup"><span data-stu-id="52b1c-257">Open *`ExpenseItHome.xaml.vb`* or *`ExpenseItHome.xaml.cs`*.</span></span>

3. <span data-ttu-id="52b1c-258">Dodaj następujący kod `ExpenseItHome` do klasy, aby dodać program obsługi zdarzeń kliknięcia przycisku.</span><span class="sxs-lookup"><span data-stu-id="52b1c-258">Add the following code to the `ExpenseItHome` class to add a button click event handler.</span></span> <span data-ttu-id="52b1c-259">Program obsługi zdarzeń otwiera stronę **ExpenseReportPage.**</span><span class="sxs-lookup"><span data-stu-id="52b1c-259">The event handler opens the **ExpenseReportPage** page.</span></span>

    [!code-csharp[ExpenseIt#16](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt6/ExpenseItHome.xaml.cs#16)]
    [!code-vb[ExpenseIt#16](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt6/ExpenseItHome.xaml.vb#16)]

## <a name="create-the-ui-for-expensereportpage"></a><span data-ttu-id="52b1c-260">Tworzenie interfejsu użytkownika dla raportu o wydatkach</span><span class="sxs-lookup"><span data-stu-id="52b1c-260">Create the UI for ExpenseReportPage</span></span>

<span data-ttu-id="52b1c-261">*ExpenseReportPage.xaml* wyświetla raport z wydatków dla osoby **`ExpenseItHome`** wybranej na stronie.</span><span class="sxs-lookup"><span data-stu-id="52b1c-261">*ExpenseReportPage.xaml* displays the expense report for the person that's selected on the **`ExpenseItHome`** page.</span></span> <span data-ttu-id="52b1c-262">W tej sekcji utworzysz interfejs użytkownika dla **ExpenseReportPage**.</span><span class="sxs-lookup"><span data-stu-id="52b1c-262">In this section, you'll create the UI for **ExpenseReportPage**.</span></span> <span data-ttu-id="52b1c-263">Do różnych elementów interfejsu użytkownika dodasz również kolory tła i wypełnienia.</span><span class="sxs-lookup"><span data-stu-id="52b1c-263">You'll also add background and fill colors to the various UI elements.</span></span>

1. <span data-ttu-id="52b1c-264">Otwórz *plik ExpenseReportPage.xaml*.</span><span class="sxs-lookup"><span data-stu-id="52b1c-264">Open *ExpenseReportPage.xaml*.</span></span>

2. <span data-ttu-id="52b1c-265">Dodaj następujący kod XAML między <xref:System.Windows.Controls.Grid> znacznikami:</span><span class="sxs-lookup"><span data-stu-id="52b1c-265">Add the following XAML between the <xref:System.Windows.Controls.Grid> tags:</span></span>

    [!code-xaml[ExpenseIt#17](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt6/ExpenseReportPage.xaml#17)]

    <span data-ttu-id="52b1c-266">Ten interfejs użytkownika *`ExpenseItHome.xaml`* jest podobny do , z <xref:System.Windows.Controls.DataGrid>wyjątkiem danych raportu jest wyświetlany w .</span><span class="sxs-lookup"><span data-stu-id="52b1c-266">This UI is similar to *`ExpenseItHome.xaml`*, except the report data is displayed in a <xref:System.Windows.Controls.DataGrid>.</span></span>

3. <span data-ttu-id="52b1c-267">Skompiluj i uruchom aplikację.</span><span class="sxs-lookup"><span data-stu-id="52b1c-267">Build and run the application.</span></span>

4. <span data-ttu-id="52b1c-268">Wybierz przycisk **Widok.**</span><span class="sxs-lookup"><span data-stu-id="52b1c-268">Select the **View** button.</span></span>

    <span data-ttu-id="52b1c-269">Zostanie wyświetlona strona raportu z wydatków.</span><span class="sxs-lookup"><span data-stu-id="52b1c-269">The expense report page appears.</span></span> <span data-ttu-id="52b1c-270">Należy również zauważyć, że przycisk nawigacji wstecz jest włączony.</span><span class="sxs-lookup"><span data-stu-id="52b1c-270">Also notice that the back navigation button is enabled.</span></span>

<span data-ttu-id="52b1c-271">Na poniższej ilustracji przedstawiono elementy interfejsu użytkownika dodane do *pliku ExpenseReportPage.xaml*.</span><span class="sxs-lookup"><span data-stu-id="52b1c-271">The following illustration shows the UI elements added to *ExpenseReportPage.xaml*.</span></span>

![ExpenseIt przykładowy zrzut ekranu przedstawiający interfejs użytkownika utworzony właśnie dla ExpenseReportPage.](./media/walkthrough-my-first-wpf-desktop-application/create-application-ui.png)

## <a name="style-controls"></a><span data-ttu-id="52b1c-273">Kontrolki stylu</span><span class="sxs-lookup"><span data-stu-id="52b1c-273">Style controls</span></span>

<span data-ttu-id="52b1c-274">Wygląd różnych elementów jest często taka sama dla wszystkich elementów tego samego typu w interfejsie użytkownika.</span><span class="sxs-lookup"><span data-stu-id="52b1c-274">The appearance of various elements is often the same for all elements of the same type in a UI.</span></span> <span data-ttu-id="52b1c-275">Interfejs użytkownika używa [stylów,](../controls/styling-and-templating.md) aby występy były wielokrotnego użytku w wielu elementach.</span><span class="sxs-lookup"><span data-stu-id="52b1c-275">UI uses [styles](../controls/styling-and-templating.md) to make appearances reusable across multiple elements.</span></span> <span data-ttu-id="52b1c-276">Możliwość ponownego użycia stylów pomaga uprościć tworzenie xaml i zarządzanie.</span><span class="sxs-lookup"><span data-stu-id="52b1c-276">The reusability of styles helps to simplify XAML creation and management.</span></span> <span data-ttu-id="52b1c-277">Ta sekcja zastępuje atrybuty dla elementu, które zostały zdefiniowane w poprzednich krokach stylami.</span><span class="sxs-lookup"><span data-stu-id="52b1c-277">This section replaces the per-element attributes that were defined in previous steps with styles.</span></span>

1. <span data-ttu-id="52b1c-278">Otwórz *plik Application.xaml* lub *App.xaml*.</span><span class="sxs-lookup"><span data-stu-id="52b1c-278">Open *Application.xaml* or *App.xaml*.</span></span>

2. <span data-ttu-id="52b1c-279">Dodaj następujący kod XAML między <xref:System.Windows.Application.Resources%2A?displayProperty=nameWithType> znacznikami:</span><span class="sxs-lookup"><span data-stu-id="52b1c-279">Add the following XAML between the <xref:System.Windows.Application.Resources%2A?displayProperty=nameWithType> tags:</span></span>

    [!code-xaml[ExpenseIt#18](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt7/App.xaml#18)]

    <span data-ttu-id="52b1c-280">Ten kod XAML dodaje następujące style:</span><span class="sxs-lookup"><span data-stu-id="52b1c-280">This XAML adds the following styles:</span></span>

    - <span data-ttu-id="52b1c-281">`headerTextStyle`: Aby sformatować tytuł <xref:System.Windows.Controls.Label>strony .</span><span class="sxs-lookup"><span data-stu-id="52b1c-281">`headerTextStyle`: To format the page title <xref:System.Windows.Controls.Label>.</span></span>

    - <span data-ttu-id="52b1c-282">`labelStyle`: Aby <xref:System.Windows.Controls.Label> sformatować formanty.</span><span class="sxs-lookup"><span data-stu-id="52b1c-282">`labelStyle`: To format the <xref:System.Windows.Controls.Label> controls.</span></span>

    - <span data-ttu-id="52b1c-283">`columnHeaderStyle`: Aby <xref:System.Windows.Controls.Primitives.DataGridColumnHeader>sformatować plik .</span><span class="sxs-lookup"><span data-stu-id="52b1c-283">`columnHeaderStyle`: To format the <xref:System.Windows.Controls.Primitives.DataGridColumnHeader>.</span></span>

    - <span data-ttu-id="52b1c-284">`listHeaderStyle`: Aby sformatować kontrolki nagłówka <xref:System.Windows.Controls.Border> listy.</span><span class="sxs-lookup"><span data-stu-id="52b1c-284">`listHeaderStyle`: To format the list header <xref:System.Windows.Controls.Border> controls.</span></span>

    - <span data-ttu-id="52b1c-285">`listHeaderTextStyle`: Aby sformatować nagłówek <xref:System.Windows.Controls.Label>listy .</span><span class="sxs-lookup"><span data-stu-id="52b1c-285">`listHeaderTextStyle`: To format the list header <xref:System.Windows.Controls.Label>.</span></span>

    - <span data-ttu-id="52b1c-286">`buttonStyle`: Aby <xref:System.Windows.Controls.Button> sformatować on `ExpenseItHome.xaml`.</span><span class="sxs-lookup"><span data-stu-id="52b1c-286">`buttonStyle`: To format the <xref:System.Windows.Controls.Button> on `ExpenseItHome.xaml`.</span></span>

    <span data-ttu-id="52b1c-287">Należy zauważyć, że style są <xref:System.Windows.Application.Resources%2A?displayProperty=nameWithType> zasoby i elementy podrzędne elementu właściwości.</span><span class="sxs-lookup"><span data-stu-id="52b1c-287">Notice that the styles are resources and children of the <xref:System.Windows.Application.Resources%2A?displayProperty=nameWithType> property element.</span></span> <span data-ttu-id="52b1c-288">W tej lokalizacji style są stosowane do wszystkich elementów w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="52b1c-288">In this location, the styles are applied to all the elements in an application.</span></span> <span data-ttu-id="52b1c-289">Na przykład użycia zasobów w aplikacji .NET zobacz [Korzystanie z zasobów aplikacji](../advanced/how-to-use-application-resources.md).</span><span class="sxs-lookup"><span data-stu-id="52b1c-289">For an example of using resources in a .NET app, see [Use Application Resources](../advanced/how-to-use-application-resources.md).</span></span>

3. <span data-ttu-id="52b1c-290">W *`ExpenseItHome.xaml`*, zastąp wszystko między <xref:System.Windows.Controls.Grid> elementami następującym kodem XAML:</span><span class="sxs-lookup"><span data-stu-id="52b1c-290">In *`ExpenseItHome.xaml`*, replace everything between the <xref:System.Windows.Controls.Grid> elements with the following XAML:</span></span>

    [!code-xaml[ExpenseIt#19](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt7/ExpenseItHome.xaml#19)]

    <span data-ttu-id="52b1c-291">Właściwości, takie <xref:System.Windows.VerticalAlignment> jak <xref:System.Windows.Media.FontFamily> i definiujące wygląd każdego formantu są usuwane i zastępowane przez zastosowanie stylów.</span><span class="sxs-lookup"><span data-stu-id="52b1c-291">The properties such as <xref:System.Windows.VerticalAlignment> and <xref:System.Windows.Media.FontFamily> that define the look of each control are removed and replaced by applying the styles.</span></span> <span data-ttu-id="52b1c-292">Na przykład `headerTextStyle` jest stosowany do "Wyświetl raport <xref:System.Windows.Controls.Label>z wydatków" .</span><span class="sxs-lookup"><span data-stu-id="52b1c-292">For example, the `headerTextStyle` is applied to the "View Expense Report" <xref:System.Windows.Controls.Label>.</span></span>

4. <span data-ttu-id="52b1c-293">Otwórz *plik ExpenseReportPage.xaml*.</span><span class="sxs-lookup"><span data-stu-id="52b1c-293">Open *ExpenseReportPage.xaml*.</span></span>

5. <span data-ttu-id="52b1c-294">Zastąp <xref:System.Windows.Controls.Grid> wszystko między elementami następującym kodem XAML:</span><span class="sxs-lookup"><span data-stu-id="52b1c-294">Replace everything between the <xref:System.Windows.Controls.Grid> elements with the following XAML:</span></span>

    [!code-xaml[ExpenseIt#20](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt7/ExpenseReportPage.xaml#20)]

    <span data-ttu-id="52b1c-295">Ten kod XAML <xref:System.Windows.Controls.Label> dodaje <xref:System.Windows.Controls.Border> style do elementów i.</span><span class="sxs-lookup"><span data-stu-id="52b1c-295">This XAML adds styles to the <xref:System.Windows.Controls.Label> and <xref:System.Windows.Controls.Border> elements.</span></span>

6. <span data-ttu-id="52b1c-296">Skompiluj i uruchom aplikację.</span><span class="sxs-lookup"><span data-stu-id="52b1c-296">Build and run the application.</span></span> <span data-ttu-id="52b1c-297">Wygląd okna jest taki sam jak poprzednio.</span><span class="sxs-lookup"><span data-stu-id="52b1c-297">The window appearance is the same as previously.</span></span>

    ![ExpenseIt przykładowy zrzut ekranu o takim samym wyglądzie jak w ostatniej sekcji.](./media/walkthrough-my-first-wpf-desktop-application/create-application-ui.png)

7. <span data-ttu-id="52b1c-299">Zamknij aplikację, aby powrócić do programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="52b1c-299">Close the application to return to Visual Studio.</span></span>

## <a name="bind-data-to-a-control"></a><span data-ttu-id="52b1c-300">Powiąż dane z formantem</span><span class="sxs-lookup"><span data-stu-id="52b1c-300">Bind data to a control</span></span>

<span data-ttu-id="52b1c-301">W tej sekcji utworzysz dane XML, który jest powiązany z różnymi formantami.</span><span class="sxs-lookup"><span data-stu-id="52b1c-301">In this section, you'll create the XML data that is bound to various controls.</span></span>

1. <span data-ttu-id="52b1c-302">W *`ExpenseItHome.xaml`*, po <xref:System.Windows.Controls.Grid> elemencie otwierającym, dodaj <xref:System.Windows.Data.XmlDataProvider> następujący kod XAML, aby utworzyć dane zawierające dane dla każdej osoby:</span><span class="sxs-lookup"><span data-stu-id="52b1c-302">In *`ExpenseItHome.xaml`*, after the opening <xref:System.Windows.Controls.Grid> element, add the following XAML to create an <xref:System.Windows.Data.XmlDataProvider> that contains the data for each person:</span></span>

    [!code-xaml[ExpenseIt#23](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml?range=13,16-40,49)]

    <span data-ttu-id="52b1c-303">Dane są tworzone <xref:System.Windows.Controls.Grid> jako zasób.</span><span class="sxs-lookup"><span data-stu-id="52b1c-303">The data is created as a <xref:System.Windows.Controls.Grid> resource.</span></span> <span data-ttu-id="52b1c-304">Zwykle te dane będą ładowane jako plik, ale dla uproszczenia dane są dodawane w linii.</span><span class="sxs-lookup"><span data-stu-id="52b1c-304">Normally this data would be loaded as a file, but for simplicity the data is added inline.</span></span>

2. <span data-ttu-id="52b1c-305">W `<Grid.Resources>` elemencie `<xref:System.Windows.DataTemplate>` dodaj następujący element, który definiuje sposób <xref:System.Windows.Controls.ListBox>wyświetlania `<XmlDataProvider>` danych w , po elemencie:</span><span class="sxs-lookup"><span data-stu-id="52b1c-305">Within the `<Grid.Resources>` element, add the following `<xref:System.Windows.DataTemplate>` element, which defines how to display the data in the <xref:System.Windows.Controls.ListBox>, after the `<XmlDataProvider>` element:</span></span>

    [!code-xaml[ExpenseIt#24](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml?range=13,43-46,49)]

    <span data-ttu-id="52b1c-306">Aby uzyskać więcej informacji na temat szablonów danych, zobacz [Omówienie tworzenia szablonów danych](../data/data-templating-overview.md).</span><span class="sxs-lookup"><span data-stu-id="52b1c-306">For more information about data templates, see [Data templating overview](../data/data-templating-overview.md).</span></span>

3. <span data-ttu-id="52b1c-307">Zastąp istniejące <xref:System.Windows.Controls.ListBox> na następujący kod XAML:</span><span class="sxs-lookup"><span data-stu-id="52b1c-307">Replace the existing <xref:System.Windows.Controls.ListBox> with the following XAML:</span></span>

    [!code-xaml[ExpenseIt#25](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml#25)]

    <span data-ttu-id="52b1c-308">Ten kod XAML <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> wiąże <xref:System.Windows.Controls.ListBox> właściwość źródła danych i stosuje szablon <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A>danych jako plik .</span><span class="sxs-lookup"><span data-stu-id="52b1c-308">This XAML binds the <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> property of the <xref:System.Windows.Controls.ListBox> to the data source and applies the data template as the <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A>.</span></span>

## <a name="connect-data-to-controls"></a><span data-ttu-id="52b1c-309">Łączenie danych z formantami</span><span class="sxs-lookup"><span data-stu-id="52b1c-309">Connect data to controls</span></span>

<span data-ttu-id="52b1c-310">Następnie dodasz kod, aby pobrać nazwę, która jest **`ExpenseItHome`** zaznaczona na stronie i przekazać go do konstruktora **ExpenseReportPage**.</span><span class="sxs-lookup"><span data-stu-id="52b1c-310">Next, you'll add code to retrieve the name that's selected on the **`ExpenseItHome`** page and pass it to the constructor of **ExpenseReportPage**.</span></span> <span data-ttu-id="52b1c-311">**ExpenseReportPage** ustawia kontekst danych z przekazanym elementem, czyli z formantami zdefiniowanymi w *pliku ExpenseReportPage.xaml.*</span><span class="sxs-lookup"><span data-stu-id="52b1c-311">**ExpenseReportPage** sets its data context with the passed item, which is what the controls defined in *ExpenseReportPage.xaml* bind to.</span></span>

1. <span data-ttu-id="52b1c-312">Otwórz *expenseReportPage.xaml.vb* lub *ExpenseReportPage.xaml.cs*.</span><span class="sxs-lookup"><span data-stu-id="52b1c-312">Open *ExpenseReportPage.xaml.vb* or *ExpenseReportPage.xaml.cs*.</span></span>

2. <span data-ttu-id="52b1c-313">Dodaj konstruktora, który przyjmuje obiekt, dzięki czemu można przekazać dane raportu z wydatków wybranej osoby.</span><span class="sxs-lookup"><span data-stu-id="52b1c-313">Add a constructor that takes an object so you can pass the expense report data of the selected person.</span></span>

    [!code-csharp[ExpenseIt#26](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseReportPage.xaml.cs#26)]
    [!code-vb[ExpenseIt#26](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt8/ExpenseReportPage.xaml.vb#26)]

3. <span data-ttu-id="52b1c-314">Otwórz *`ExpenseItHome.xaml.vb`* *`ExpenseItHome.xaml.cs`* lub .</span><span class="sxs-lookup"><span data-stu-id="52b1c-314">Open *`ExpenseItHome.xaml.vb`* or *`ExpenseItHome.xaml.cs`*.</span></span>

4. <span data-ttu-id="52b1c-315">Zmień <xref:System.Windows.Controls.Primitives.ButtonBase.Click> program obsługi zdarzeń, aby wywołać nowy konstruktor przekazując dane raportu z wydatków wybranej osoby.</span><span class="sxs-lookup"><span data-stu-id="52b1c-315">Change the <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event handler to call the new constructor passing the expense report data of the selected person.</span></span>

    [!code-csharp[ExpenseIt#27](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml.cs#27)]
    [!code-vb[ExpenseIt#27](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt8/ExpenseItHome.xaml.vb#27)]

## <a name="style-data-with-data-templates"></a><span data-ttu-id="52b1c-316">Stylizowania danych za pomocą szablonów danych</span><span class="sxs-lookup"><span data-stu-id="52b1c-316">Style data with data templates</span></span>

<span data-ttu-id="52b1c-317">W tej sekcji zaktualizujesz interfejs użytkownika dla każdego elementu na listach związanych z danymi przy użyciu szablonów danych.</span><span class="sxs-lookup"><span data-stu-id="52b1c-317">In this section, you'll update the UI for each item in the data-bound lists by using data templates.</span></span>

1. <span data-ttu-id="52b1c-318">Otwórz *plik ExpenseReportPage.xaml*.</span><span class="sxs-lookup"><span data-stu-id="52b1c-318">Open *ExpenseReportPage.xaml*.</span></span>

2. <span data-ttu-id="52b1c-319">Powiąż zawartość elementów "Nazwa" i "Dział" <xref:System.Windows.Controls.Label> z właściwość odpowiedniego źródła danych.</span><span class="sxs-lookup"><span data-stu-id="52b1c-319">Bind the content of the "Name" and "Department" <xref:System.Windows.Controls.Label> elements to the appropriate data source property.</span></span> <span data-ttu-id="52b1c-320">Aby uzyskać więcej informacji na temat powiązania danych, zobacz [Omówienie powiązania danych](../../../desktop-wpf/data/data-binding-overview.md).</span><span class="sxs-lookup"><span data-stu-id="52b1c-320">For more information about data binding, see [Data binding overview](../../../desktop-wpf/data/data-binding-overview.md).</span></span>

    [!code-xaml[ExpenseIt#31](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseReportPage.xaml#31)]

3. <span data-ttu-id="52b1c-321">Po elemencie otwierającym <xref:System.Windows.Controls.Grid> dodaj następujące szablony danych, które definiują sposób wyświetlania danych raportu z wydatków:</span><span class="sxs-lookup"><span data-stu-id="52b1c-321">After the opening <xref:System.Windows.Controls.Grid> element, add the following data templates, which define how to display the expense report data:</span></span>

    [!code-xaml[ExpenseIt#30](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseReportPage.xaml#30)]

4. <span data-ttu-id="52b1c-322"><xref:System.Windows.Controls.DataGridTextColumn> Zastąp <xref:System.Windows.Controls.DataGridTemplateColumn> elementy <xref:System.Windows.Controls.DataGrid> pod elementem i zastosuj do nich szablony.</span><span class="sxs-lookup"><span data-stu-id="52b1c-322">Replace the <xref:System.Windows.Controls.DataGridTextColumn> elements with <xref:System.Windows.Controls.DataGridTemplateColumn> under the <xref:System.Windows.Controls.DataGrid> element and apply the templates to them.</span></span>

    [!code-xaml[ExpenseIt#32](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseReportPage.xaml#32)]

5. <span data-ttu-id="52b1c-323">Skompiluj i uruchom aplikację.</span><span class="sxs-lookup"><span data-stu-id="52b1c-323">Build and run the application.</span></span>

6. <span data-ttu-id="52b1c-324">Wybierz osobę, a następnie wybierz przycisk **Widok.**</span><span class="sxs-lookup"><span data-stu-id="52b1c-324">Select a person and then select the **View** button.</span></span>

<span data-ttu-id="52b1c-325">Na poniższej ilustracji `ExpenseIt` przedstawiono obie strony aplikacji z formantami, układem, stylami, powiązaniem danych i zastosowanymi szablonami danych:</span><span class="sxs-lookup"><span data-stu-id="52b1c-325">The following illustration shows both pages of the `ExpenseIt` application with controls, layout, styles, data binding, and data templates applied:</span></span>

![Obie strony aplikacji z listą nazwisk i raportem z wydatków.](./media/walkthrough-my-first-wpf-desktop-application/application-data-templates.png)

> [!NOTE]
> <span data-ttu-id="52b1c-327">W tym przykładzie przedstawiono określoną funkcję WPF WPF i nie jest zgodne ze wszystkimi najlepszymi rozwiązaniami dotyczącymi elementów, takich jak zabezpieczenia, lokalizacja i ułatwienia dostępu.</span><span class="sxs-lookup"><span data-stu-id="52b1c-327">This sample demonstrates a specific feature of WPF and doesn't follow all best practices for things like security, localization, and accessibility.</span></span> <span data-ttu-id="52b1c-328">Aby uzyskać kompleksowe pokrycie WPF WPF i .NET najlepsze rozwiązania dotyczące tworzenia aplikacji, zobacz następujące tematy:</span><span class="sxs-lookup"><span data-stu-id="52b1c-328">For comprehensive coverage of WPF and the .NET app development best practices, see the following topics:</span></span>
>
> - [<span data-ttu-id="52b1c-329">Ułatwienia dostępu</span><span class="sxs-lookup"><span data-stu-id="52b1c-329">Accessibility</span></span>](../../ui-automation/accessibility-best-practices.md)
> - [<span data-ttu-id="52b1c-330">Zabezpieczenia</span><span class="sxs-lookup"><span data-stu-id="52b1c-330">Security</span></span>](../security-wpf.md)
> - [<span data-ttu-id="52b1c-331">Globalizacja i lokalizacja WPF</span><span class="sxs-lookup"><span data-stu-id="52b1c-331">WPF globalization and localization</span></span>](../advanced/wpf-globalization-and-localization-overview.md)
> - [<span data-ttu-id="52b1c-332">Wydajność WPF</span><span class="sxs-lookup"><span data-stu-id="52b1c-332">WPF performance</span></span>](../advanced/optimizing-wpf-application-performance.md)

## <a name="next-steps"></a><span data-ttu-id="52b1c-333">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="52b1c-333">Next steps</span></span>

<span data-ttu-id="52b1c-334">W tym instruktażu można dowiedzieć się wiele technik tworzenia interfejsu użytkownika przy użyciu programu Windows Presentation Foundation (WPF).</span><span class="sxs-lookup"><span data-stu-id="52b1c-334">In this walkthrough you learned a number of techniques for creating a UI using Windows Presentation Foundation (WPF).</span></span> <span data-ttu-id="52b1c-335">Teraz powinieneś mieć podstawową wiedzę o blokach konstrukcyjnych aplikacji .NET powiązanej z danymi.</span><span class="sxs-lookup"><span data-stu-id="52b1c-335">You should now have a basic understanding of the building blocks of a data-bound .NET app.</span></span> <span data-ttu-id="52b1c-336">Aby uzyskać więcej informacji na temat architektury WPF i modeli programowania, zobacz następujące tematy:</span><span class="sxs-lookup"><span data-stu-id="52b1c-336">For more information about the WPF architecture and programming models, see the following topics:</span></span>

- [<span data-ttu-id="52b1c-337">Architektura WPF</span><span class="sxs-lookup"><span data-stu-id="52b1c-337">WPF architecture</span></span>](../advanced/wpf-architecture.md)
- [<span data-ttu-id="52b1c-338">Omówienie XAML (WPF)</span><span class="sxs-lookup"><span data-stu-id="52b1c-338">XAML overview (WPF)</span></span>](../advanced/xaml-overview-wpf.md)
- [<span data-ttu-id="52b1c-339">Omówienie właściwości zależności</span><span class="sxs-lookup"><span data-stu-id="52b1c-339">Dependency properties overview</span></span>](../advanced/dependency-properties-overview.md)
- [<span data-ttu-id="52b1c-340">Układ</span><span class="sxs-lookup"><span data-stu-id="52b1c-340">Layout</span></span>](../advanced/layout.md)

<span data-ttu-id="52b1c-341">Aby uzyskać więcej informacji na temat tworzenia aplikacji, zobacz następujące tematy:</span><span class="sxs-lookup"><span data-stu-id="52b1c-341">For more information about creating applications, see the following topics:</span></span>

- [<span data-ttu-id="52b1c-342">Tworzenie aplikacji</span><span class="sxs-lookup"><span data-stu-id="52b1c-342">Application development</span></span>](../app-development/index.md)
- [<span data-ttu-id="52b1c-343">Kontrolki</span><span class="sxs-lookup"><span data-stu-id="52b1c-343">Controls</span></span>](../controls/index.md)
- [<span data-ttu-id="52b1c-344">Omówienie powiązania danych</span><span class="sxs-lookup"><span data-stu-id="52b1c-344">Data binding overview</span></span>](../../../desktop-wpf/data/data-binding-overview.md)
- [<span data-ttu-id="52b1c-345">Grafika i multimedia</span><span class="sxs-lookup"><span data-stu-id="52b1c-345">Graphics and multimedia</span></span>](../graphics-multimedia/index.md)
- [<span data-ttu-id="52b1c-346">Dokumenty w WPF</span><span class="sxs-lookup"><span data-stu-id="52b1c-346">Documents in WPF</span></span>](../advanced/documents-in-wpf.md)

## <a name="see-also"></a><span data-ttu-id="52b1c-347">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="52b1c-347">See also</span></span>

- [<span data-ttu-id="52b1c-348">Omówienie paneli</span><span class="sxs-lookup"><span data-stu-id="52b1c-348">Panels overview</span></span>](../controls/panels-overview.md)
- [<span data-ttu-id="52b1c-349">Omówienie tworzenia szablonów danych</span><span class="sxs-lookup"><span data-stu-id="52b1c-349">Data templating overview</span></span>](../data/data-templating-overview.md)
- [<span data-ttu-id="52b1c-350">Tworzenie aplikacji WPF</span><span class="sxs-lookup"><span data-stu-id="52b1c-350">Build a WPF application</span></span>](../app-development/building-a-wpf-application-wpf.md)
- [<span data-ttu-id="52b1c-351">Style i szablony</span><span class="sxs-lookup"><span data-stu-id="52b1c-351">Styles and templates</span></span>](../controls/styles-and-templates.md)
