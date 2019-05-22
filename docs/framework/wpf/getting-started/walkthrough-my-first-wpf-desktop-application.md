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
ms.openlocfilehash: c3440ddf6cdae6b24bcf1059ab2c76d8fb957263
ms.sourcegitcommit: 11deacc8ec9f229ab8ee3cd537515d4c2826515f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/22/2019
ms.locfileid: "66003865"
---
# <a name="walkthrough-my-first-wpf-desktop-application"></a><span data-ttu-id="d74dd-102">Przewodnik: Moja pierwsza aplikacja klasyczna WPF</span><span class="sxs-lookup"><span data-stu-id="d74dd-102">Walkthrough: My first WPF desktop application</span></span>

<span data-ttu-id="d74dd-103">W tym artykule przedstawiono sposób tworzenia aplikacji klasycznych Windows Presentation Foundation (WPF), która zawiera elementy, które są wspólne dla większości aplikacji WPF: Extensible Application Markup Language (XAML) znaczników, związane z kodem, definicji aplikacji, formanty, układ, powiązanie danych i stylów.</span><span class="sxs-lookup"><span data-stu-id="d74dd-103">This article shows you how to develop a Windows Presentation Foundation (WPF) desktop application that includes the elements that are common to most WPF applications: Extensible Application Markup Language (XAML) markup, code-behind, application definitions, controls, layout, data binding, and styles.</span></span> <span data-ttu-id="d74dd-104">Aby opracować aplikację, użyjesz programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="d74dd-104">To develop the application, you'll use Visual Studio.</span></span> 

<span data-ttu-id="d74dd-105">Ten instruktaż obejmuje następujące kroki:</span><span class="sxs-lookup"><span data-stu-id="d74dd-105">This walkthrough includes the following steps:</span></span>

- <span data-ttu-id="d74dd-106">Projektowanie wyglądu aplikacji interfejsu użytkownika (UI), należy użyć XAML.</span><span class="sxs-lookup"><span data-stu-id="d74dd-106">Use XAML to design the appearance of the application's user interface (UI).</span></span>

- <span data-ttu-id="d74dd-107">Pisanie kodu w celu tworzenia zachowaniu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="d74dd-107">Write code to build the application's behavior.</span></span>

- <span data-ttu-id="d74dd-108">Tworzenie definicji aplikacji do zarządzania aplikacją.</span><span class="sxs-lookup"><span data-stu-id="d74dd-108">Create an application definition to manage the application.</span></span>

- <span data-ttu-id="d74dd-109">Dodawanie formantów i Utwórz układ do tworzenia interfejsu użytkownika aplikacji.</span><span class="sxs-lookup"><span data-stu-id="d74dd-109">Add controls and create the layout to compose the application UI.</span></span>

- <span data-ttu-id="d74dd-110">Tworzenie stylów dla spójny wygląd interfejsu użytkownika aplikacji.</span><span class="sxs-lookup"><span data-stu-id="d74dd-110">Create styles for a consistent appearance throughout the application's UI.</span></span>

- <span data-ttu-id="d74dd-111">Powiąż interfejsu użytkownika do danych, aby wypełnić interfejsu użytkownika z danych i przechowywania danych, a następnie synchronizowane interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="d74dd-111">Bind the UI to data, both to populate the UI from data and to keep the data and UI synchronized.</span></span>

<span data-ttu-id="d74dd-112">Przed zakończeniem tego przewodnika będziesz wbudowane autonomicznej aplikacji Windows, która pozwala użytkownikom na wyświetlanie raportów wydatków dla wybranych osób.</span><span class="sxs-lookup"><span data-stu-id="d74dd-112">By the end of the walkthrough, you'll have built a standalone Windows application that allows users to view expense reports for selected people.</span></span> <span data-ttu-id="d74dd-113">Aplikacja składa się z kilku stron WPF, które znajdują się w oknie myszą.</span><span class="sxs-lookup"><span data-stu-id="d74dd-113">The application is composed of several WPF pages that are hosted in a browser-style window.</span></span>

> [!TIP]
> <span data-ttu-id="d74dd-114">Przykładowy kod, który jest używany do tworzenia tego przewodnika jest dostępny dla obu języka Visual Basic i C# na [kodu przykładowej aplikacji WPF wskazówki](https://github.com/Microsoft/WPF-Samples/tree/master/Getting%20Started/WalkthroughFirstWPFApp).</span><span class="sxs-lookup"><span data-stu-id="d74dd-114">The sample code that is used to build this walkthrough is available for both Visual Basic and C# at [Walkthrough WPF App Sample Code](https://github.com/Microsoft/WPF-Samples/tree/master/Getting%20Started/WalkthroughFirstWPFApp).</span></span>
>
> <span data-ttu-id="d74dd-115">Można przełączać język kodu przykładowego kodu między C# i Visual Basic przy użyciu **\< />** listy rozwijanej w prawej górnej części tego artykułu.</span><span class="sxs-lookup"><span data-stu-id="d74dd-115">You can toggle the code language of the sample code between C# and Visual Basic by using the **\</>** drop-down on the upper right side of this article.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="d74dd-116">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="d74dd-116">Prerequisites</span></span>

- <span data-ttu-id="d74dd-117">Program Visual Studio 2017 lub nowszym (w tym artykule korzysta z programu Visual Studio 2019 r.)</span><span class="sxs-lookup"><span data-stu-id="d74dd-117">Visual Studio 2017 or later (this article uses Visual Studio 2019)</span></span>

   <span data-ttu-id="d74dd-118">Aby uzyskać więcej informacji na temat instalowania najnowszej wersji programu Visual Studio, zobacz [Zainstaluj program Visual Studio](/visualstudio/install/install-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="d74dd-118">For more information about installing the latest version of Visual Studio, see [Install Visual Studio](/visualstudio/install/install-visual-studio).</span></span>

## <a name="create-the-application-project"></a><span data-ttu-id="d74dd-119">Utwórz projekt aplikacji</span><span class="sxs-lookup"><span data-stu-id="d74dd-119">Create the application project</span></span>

<span data-ttu-id="d74dd-120">Pierwszym krokiem jest do utworzenia infrastruktury aplikacji, który zawiera definicję aplikacji, dwie strony i obraz.</span><span class="sxs-lookup"><span data-stu-id="d74dd-120">The first step is to create the application infrastructure, which includes an application definition, two pages, and an image.</span></span>

1. <span data-ttu-id="d74dd-121">Utwórz nowy projekt aplikacji WPF w języku Visual Basic lub Visual C# o nazwie **`ExpenseIt`**:</span><span class="sxs-lookup"><span data-stu-id="d74dd-121">Create a new WPF Application project in Visual Basic or Visual C# named **`ExpenseIt`**:</span></span>

   1. <span data-ttu-id="d74dd-122">Otwórz program Visual Studio i wybierz **Utwórz nowy projekt** w obszarze **wprowadzenie** menu.</span><span class="sxs-lookup"><span data-stu-id="d74dd-122">Open Visual Studio and select **Create a new project** under the **Get started** menu.</span></span>

      <span data-ttu-id="d74dd-123">**Utwórz nowy projekt** zostanie otwarte okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="d74dd-123">The **Create a new project** dialog opens.</span></span>

   2. <span data-ttu-id="d74dd-124">W **języka** listy rozwijanej wybierz opcję **C#** lub **języka Visual Basic**.</span><span class="sxs-lookup"><span data-stu-id="d74dd-124">In the **Language** dropdown, select either **C#** or **Visual Basic**.</span></span>
      
   3. <span data-ttu-id="d74dd-125">Wybierz **aplikacja WPF (.NET Framework)** szablonu, a następnie wybierz **dalej**.</span><span class="sxs-lookup"><span data-stu-id="d74dd-125">Select the **WPF App (.NET Framework)** template and then select **Next**.</span></span> 
     
      ![Tworzenie okna dialogowego Nowy projekt](./media/walkthrough-my-first-wpf-desktop-application/create-new-project-dialog.png)
    
      <span data-ttu-id="d74dd-127">**Konfigurowania nowego projektu** zostanie otwarte okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="d74dd-127">The **Configure your new project** dialog opens.</span></span>

   4. <span data-ttu-id="d74dd-128">Wprowadź nazwę projektu **`ExpenseIt`** , a następnie wybierz **Utwórz**.</span><span class="sxs-lookup"><span data-stu-id="d74dd-128">Enter the project name **`ExpenseIt`** and then select **Create**.</span></span>

      ![Konfigurowanie okna dialogowego Nowy projekt](./media/walkthrough-my-first-wpf-desktop-application/configure-new-project-dialog.png)

      <span data-ttu-id="d74dd-130">Visual Studio tworzy projekt i zostanie otwarty projektant domyślny okna aplikacji o nazwie **MainWindow.xaml**.</span><span class="sxs-lookup"><span data-stu-id="d74dd-130">Visual Studio creates the project and opens the designer for the default application window named **MainWindow.xaml**.</span></span>

2. <span data-ttu-id="d74dd-131">Otwórz *Application.xaml* (Visual Basic) lub *App.xaml* (C#).</span><span class="sxs-lookup"><span data-stu-id="d74dd-131">Open *Application.xaml* (Visual Basic) or *App.xaml* (C#).</span></span>

    <span data-ttu-id="d74dd-132">Ten plik XAML definiuje aplikacji WPF i wszystkich zasobów aplikacji.</span><span class="sxs-lookup"><span data-stu-id="d74dd-132">This XAML file defines a WPF application and any application resources.</span></span> <span data-ttu-id="d74dd-133">Ten plik również użyć do określenia interfejsu użytkownika, w tym przypadku *MainWindow.xaml*, automatycznie pokazuje podczas uruchamiania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="d74dd-133">You also use this file to specify the UI, in this case *MainWindow.xaml*, that automatically shows when the application starts.</span></span>

    <span data-ttu-id="d74dd-134">Usługi XAML powinien wyglądać podobnie do poniższego w języku Visual Basic:</span><span class="sxs-lookup"><span data-stu-id="d74dd-134">Your XAML should look like the following in Visual Basic:</span></span>

    [!code-xaml[ExpenseIt#1_A](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/Application.xaml#1_a)]

    <span data-ttu-id="d74dd-135">I podobnie do poniższego w C#:</span><span class="sxs-lookup"><span data-stu-id="d74dd-135">And like the following in C#:</span></span>

    [!code-xaml[ExpenseIt#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/App.xaml#1)]

3. <span data-ttu-id="d74dd-136">Otwórz *MainWindow.xaml*.</span><span class="sxs-lookup"><span data-stu-id="d74dd-136">Open *MainWindow.xaml*.</span></span>

    <span data-ttu-id="d74dd-137">Ten plik XAML okno główne aplikacji i wyświetla zawartość utworzona na stronach.</span><span class="sxs-lookup"><span data-stu-id="d74dd-137">This XAML file is the main window of your application and displays content created in pages.</span></span> <span data-ttu-id="d74dd-138"><xref:System.Windows.Window> Klasy definiuje właściwości okna, takie jak jego tytuł, rozmiar lub ikonę i obsługuje zdarzenia, takie jak zamknąć lub ukrywanie.</span><span class="sxs-lookup"><span data-stu-id="d74dd-138">The <xref:System.Windows.Window> class defines the properties of a window, such as its title, size, or icon, and handles events, such as closing or hiding.</span></span>

4. <span data-ttu-id="d74dd-139">Zmiana <xref:System.Windows.Window> elementu <xref:System.Windows.Navigation.NavigationWindow>, jak pokazano na poniższym XAML:</span><span class="sxs-lookup"><span data-stu-id="d74dd-139">Change the <xref:System.Windows.Window> element to a <xref:System.Windows.Navigation.NavigationWindow>, as shown in the following XAML:</span></span>

   ```xaml
   <NavigationWindow x:Class="ExpenseIt.MainWindow"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        ...
   </NavigationWindow>
   ```

   <span data-ttu-id="d74dd-140">Ta aplikacja powoduje przejście do innej zawartości, w zależności od danych wejściowych użytkownika.</span><span class="sxs-lookup"><span data-stu-id="d74dd-140">This app navigates to different content depending on the user input.</span></span> <span data-ttu-id="d74dd-141">Dlatego głównym <xref:System.Windows.Window> musi zostać zmienione w celu <xref:System.Windows.Navigation.NavigationWindow>.</span><span class="sxs-lookup"><span data-stu-id="d74dd-141">This is why the main <xref:System.Windows.Window> needs to be changed to a <xref:System.Windows.Navigation.NavigationWindow>.</span></span> <span data-ttu-id="d74dd-142"><xref:System.Windows.Navigation.NavigationWindow> dziedziczy wszystkie właściwości <xref:System.Windows.Window>.</span><span class="sxs-lookup"><span data-stu-id="d74dd-142"><xref:System.Windows.Navigation.NavigationWindow> inherits all the properties of <xref:System.Windows.Window>.</span></span> <span data-ttu-id="d74dd-143"><xref:System.Windows.Navigation.NavigationWindow> Elementu w pliku XAML tworzy wystąpienie <xref:System.Windows.Navigation.NavigationWindow> klasy.</span><span class="sxs-lookup"><span data-stu-id="d74dd-143">The <xref:System.Windows.Navigation.NavigationWindow> element in the XAML file creates an instance of the <xref:System.Windows.Navigation.NavigationWindow> class.</span></span> <span data-ttu-id="d74dd-144">Aby uzyskać więcej informacji, zobacz [Nawigacja — omówienie](../app-development/navigation-overview.md).</span><span class="sxs-lookup"><span data-stu-id="d74dd-144">For more information, see [Navigation overview](../app-development/navigation-overview.md).</span></span>

5. <span data-ttu-id="d74dd-145">Usuń <xref:System.Windows.Controls.Grid> elementów między <xref:System.Windows.Navigation.NavigationWindow> tagów.</span><span class="sxs-lookup"><span data-stu-id="d74dd-145">Remove the <xref:System.Windows.Controls.Grid> elements from between the <xref:System.Windows.Navigation.NavigationWindow> tags.</span></span>

6. <span data-ttu-id="d74dd-146">Zmień następujące właściwości w kodzie XAML dla <xref:System.Windows.Navigation.NavigationWindow> elementu:</span><span class="sxs-lookup"><span data-stu-id="d74dd-146">Change the following properties in the XAML code for the <xref:System.Windows.Navigation.NavigationWindow> element:</span></span>

    - <span data-ttu-id="d74dd-147">Ustaw <xref:System.Windows.Window.Title%2A> właściwość "`ExpenseIt`".</span><span class="sxs-lookup"><span data-stu-id="d74dd-147">Set the <xref:System.Windows.Window.Title%2A> property to "`ExpenseIt`".</span></span>

    - <span data-ttu-id="d74dd-148">Ustaw <xref:System.Windows.FrameworkElement.Height%2A> właściwość 350 pikseli.</span><span class="sxs-lookup"><span data-stu-id="d74dd-148">Set the <xref:System.Windows.FrameworkElement.Height%2A> property to 350 pixels.</span></span>

    - <span data-ttu-id="d74dd-149">Ustaw <xref:System.Windows.FrameworkElement.Width%2A> właściwości na 500 pikseli.</span><span class="sxs-lookup"><span data-stu-id="d74dd-149">Set the <xref:System.Windows.FrameworkElement.Width%2A> property to 500 pixels.</span></span>

    <span data-ttu-id="d74dd-150">Usługi XAML powinien wyglądać podobnie do poniższego dla języka Visual Basic:</span><span class="sxs-lookup"><span data-stu-id="d74dd-150">Your XAML should look like the following for Visual Basic:</span></span>

    [!code-xaml[ExpenseIt#2_A](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt/MainWindow.xaml#2_a)]

    <span data-ttu-id="d74dd-151">I podobnie do poniższego dla C#:</span><span class="sxs-lookup"><span data-stu-id="d74dd-151">And like the following for C#:</span></span>

    [!code-xaml[ExpenseIt#2](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/MainWindow.xaml#2)]

7. <span data-ttu-id="d74dd-152">Otwórz *MainWindow.xaml.vb* lub *MainWindow.xaml.cs*.</span><span class="sxs-lookup"><span data-stu-id="d74dd-152">Open *MainWindow.xaml.vb* or *MainWindow.xaml.cs*.</span></span>

    <span data-ttu-id="d74dd-153">Ten plik jest plik związany z kodem, który zawiera kod służący do obsługi zdarzeń zadeklarowanych w *MainWindow.xaml*.</span><span class="sxs-lookup"><span data-stu-id="d74dd-153">This file is a code-behind file that contains code to handle the events declared in *MainWindow.xaml*.</span></span> <span data-ttu-id="d74dd-154">Ten plik zawiera klasę częściową dla okna zdefiniowane w XAML.</span><span class="sxs-lookup"><span data-stu-id="d74dd-154">This file contains a partial class for the window defined in XAML.</span></span>

8. <span data-ttu-id="d74dd-155">Jeśli używasz C#, zmień `MainWindow` pochodzi od klasy <xref:System.Windows.Navigation.NavigationWindow>.</span><span class="sxs-lookup"><span data-stu-id="d74dd-155">If you're using C#, change the `MainWindow` class to derive from <xref:System.Windows.Navigation.NavigationWindow>.</span></span> <span data-ttu-id="d74dd-156">(W języku Visual Basic to wykonywane automatycznie po zmianie okna XAML). Twoje C# kod powinien teraz wyglądać następująco:</span><span class="sxs-lookup"><span data-stu-id="d74dd-156">(In Visual Basic, this happens automatically when you change the window in XAML.) Your C# code should now look like this:</span></span>

   [!code-csharp[ExpenseIt#3](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/MainWindow.xaml.cs?highlight=21)]

## <a name="add-files-to-the-application"></a><span data-ttu-id="d74dd-157">Dodaj pliki do aplikacji</span><span class="sxs-lookup"><span data-stu-id="d74dd-157">Add files to the application</span></span>

<span data-ttu-id="d74dd-158">W tej sekcji należy dodać dwie strony i obrazu do aplikacji.</span><span class="sxs-lookup"><span data-stu-id="d74dd-158">In this section, you'll add two pages and an image to the application.</span></span>

1. <span data-ttu-id="d74dd-159">Dodaj nową stronę do projektu i nadaj mu nazwę *`ExpenseItHome.xaml`*:</span><span class="sxs-lookup"><span data-stu-id="d74dd-159">Add a new page to the project, and name it *`ExpenseItHome.xaml`*:</span></span>

   1. <span data-ttu-id="d74dd-160">W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **`ExpenseIt`** węzeł projektu i wybierz polecenie **Dodaj** > **strony**.</span><span class="sxs-lookup"><span data-stu-id="d74dd-160">In **Solution Explorer**, right-click on the **`ExpenseIt`** project node and choose **Add** > **Page**.</span></span>

   1. <span data-ttu-id="d74dd-161">W **Dodaj nowy element** okno dialogowe, **strony (WPF)** już zaznaczony jest szablon.</span><span class="sxs-lookup"><span data-stu-id="d74dd-161">In the **Add New Item** dialog, the **Page (WPF)** template is already selected.</span></span> <span data-ttu-id="d74dd-162">Wprowadź nazwę **`ExpenseItHome`**, a następnie wybierz pozycję **Dodaj**.</span><span class="sxs-lookup"><span data-stu-id="d74dd-162">Enter the name **`ExpenseItHome`**, and then select **Add**.</span></span>

    <span data-ttu-id="d74dd-163">Ta strona jest pierwsza strona, która jest wyświetlana, gdy aplikacja zostanie uruchomiona.</span><span class="sxs-lookup"><span data-stu-id="d74dd-163">This page is the first page that's displayed when the application is launched.</span></span> <span data-ttu-id="d74dd-164">Widoczna będzie lista osób, które można wybierać, aby wyświetlić raport wydatków dla.</span><span class="sxs-lookup"><span data-stu-id="d74dd-164">It will show a list of people to select from, to show an expense report for.</span></span>

1. <span data-ttu-id="d74dd-165">Otwórz *`ExpenseItHome.xaml`*.</span><span class="sxs-lookup"><span data-stu-id="d74dd-165">Open *`ExpenseItHome.xaml`*.</span></span>

1. <span data-ttu-id="d74dd-166">Ustaw <xref:System.Windows.Controls.Page.Title%2A> do "`ExpenseIt - Home`".</span><span class="sxs-lookup"><span data-stu-id="d74dd-166">Set the <xref:System.Windows.Controls.Page.Title%2A> to "`ExpenseIt - Home`".</span></span>

1. <span data-ttu-id="d74dd-167">Ustaw `DesignHeight` i `DesignWidth` element wartości do 300 pikseli.</span><span class="sxs-lookup"><span data-stu-id="d74dd-167">Set the `DesignHeight` and `DesignWidth` element values to 300 pixels.</span></span>

    <span data-ttu-id="d74dd-168">Dla języka Visual Basic z XAML teraz wygląda następująco:</span><span class="sxs-lookup"><span data-stu-id="d74dd-168">The XAML now appears as follows for Visual Basic:</span></span>

    [!code-xaml[ExpenseIt#6_A](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseItHome.xaml#6_a)]

    <span data-ttu-id="d74dd-169">I podobnie do poniższego dla C#:</span><span class="sxs-lookup"><span data-stu-id="d74dd-169">And like the following for C#:</span></span>

    [!code-xaml[ExpenseIt#6](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt2/ExpenseItHome.xaml#6)]

1. <span data-ttu-id="d74dd-170">Otwórz *MainWindow.xaml*.</span><span class="sxs-lookup"><span data-stu-id="d74dd-170">Open *MainWindow.xaml*.</span></span>

1. <span data-ttu-id="d74dd-171">Dodaj <xref:System.Windows.Navigation.NavigationWindow.Source%2A> właściwości <xref:System.Windows.Navigation.NavigationWindow> element i wybierz opcję "`ExpenseItHome.xaml`".</span><span class="sxs-lookup"><span data-stu-id="d74dd-171">Add a <xref:System.Windows.Navigation.NavigationWindow.Source%2A> property to the <xref:System.Windows.Navigation.NavigationWindow> element and set it to "`ExpenseItHome.xaml`".</span></span>

    <span data-ttu-id="d74dd-172">To ustawienie *`ExpenseItHome.xaml`* jako pierwsza strona otwarty podczas uruchamiania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="d74dd-172">This sets *`ExpenseItHome.xaml`* to be the first page opened when the application starts.</span></span> 

    <span data-ttu-id="d74dd-173">Przykład XAML w Visual Basic:</span><span class="sxs-lookup"><span data-stu-id="d74dd-173">Example XAML in Visual Basic:</span></span>

    [!code-xaml[ExpenseIt#7_A](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/MainWindow.xaml#7_a)]

    <span data-ttu-id="d74dd-174">W języku C#:</span><span class="sxs-lookup"><span data-stu-id="d74dd-174">And in C#:</span></span>

    [!code-xaml[ExpenseIt#7](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt2/MainWindow.xaml#7)]

   > [!TIP]
   > <span data-ttu-id="d74dd-175">Można również ustawić **źródła** właściwość **różne** kategorii **właściwości** okna.</span><span class="sxs-lookup"><span data-stu-id="d74dd-175">You can also set the **Source** property in the **Miscellaneous** category of the **Properties** window.</span></span>
   >
   > ![Source — właściwość w oknie właściwości](./media/properties-source.png)

1. <span data-ttu-id="d74dd-177">Dodaj inną nową stronę WPF do projektu i nadaj mu nazwę *ExpenseReportPage.xaml*::</span><span class="sxs-lookup"><span data-stu-id="d74dd-177">Add another new WPF page to the project, and name it *ExpenseReportPage.xaml*::</span></span>

   1. <span data-ttu-id="d74dd-178">W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **`ExpenseIt`** węzeł projektu i wybierz polecenie **Dodaj** > **strony**.</span><span class="sxs-lookup"><span data-stu-id="d74dd-178">In **Solution Explorer**, right-click on the **`ExpenseIt`** project node and choose **Add** > **Page**.</span></span>

   1. <span data-ttu-id="d74dd-179">W **Dodaj nowy element** okno dialogowe, wybierz opcję **strony (WPF)** szablonu.</span><span class="sxs-lookup"><span data-stu-id="d74dd-179">In the **Add New Item** dialog, select the **Page (WPF)** template.</span></span> <span data-ttu-id="d74dd-180">Wprowadź nazwę **ExpenseReportPage**, a następnie wybierz pozycję **Dodaj**.</span><span class="sxs-lookup"><span data-stu-id="d74dd-180">Enter the name **ExpenseReportPage**, and then select **Add**.</span></span>

    <span data-ttu-id="d74dd-181">Tej strony wyświetli raportu wydatków dla osób, które wybrano na **`ExpenseItHome`** strony.</span><span class="sxs-lookup"><span data-stu-id="d74dd-181">This page will show the expense report for the person that is selected on the **`ExpenseItHome`** page.</span></span>

1. <span data-ttu-id="d74dd-182">Otwórz *ExpenseReportPage.xaml*.</span><span class="sxs-lookup"><span data-stu-id="d74dd-182">Open *ExpenseReportPage.xaml*.</span></span>

1. <span data-ttu-id="d74dd-183">Ustaw <xref:System.Windows.Controls.Page.Title%2A> do "`ExpenseIt - View Expense`".</span><span class="sxs-lookup"><span data-stu-id="d74dd-183">Set the <xref:System.Windows.Controls.Page.Title%2A> to "`ExpenseIt - View Expense`".</span></span>

1. <span data-ttu-id="d74dd-184">Ustaw `DesignHeight` i `DesignWidth` element wartości do 300 pikseli.</span><span class="sxs-lookup"><span data-stu-id="d74dd-184">Set the `DesignHeight` and `DesignWidth` element values to 300 pixels.</span></span>

    <span data-ttu-id="d74dd-185">*ExpenseReportPage.xaml* teraz wygląda jak poniżej w języku Visual Basic:</span><span class="sxs-lookup"><span data-stu-id="d74dd-185">*ExpenseReportPage.xaml* now looks like the following in Visual Basic:</span></span>

    [!code-xaml[ExpenseIt#4_A](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseReportPage.xaml#4_a)]

    <span data-ttu-id="d74dd-186">I podobnie do poniższego w C#:</span><span class="sxs-lookup"><span data-stu-id="d74dd-186">And like the following in C#:</span></span>

    [!code-xaml[ExpenseIt#4](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/ExpenseReportPage.xaml#4)]

1. <span data-ttu-id="d74dd-187">Otwórz *ExpenseItHome.xaml.vb* i *ExpenseReportPage.xaml.vb*, lub *ExpenseItHome.xaml.cs* i *ExpenseReportPage.xaml.cs*.</span><span class="sxs-lookup"><span data-stu-id="d74dd-187">Open *ExpenseItHome.xaml.vb* and *ExpenseReportPage.xaml.vb*, or *ExpenseItHome.xaml.cs* and *ExpenseReportPage.xaml.cs*.</span></span>

    <span data-ttu-id="d74dd-188">Podczas tworzenia nowego pliku strony Visual Studio automatycznie tworzy jego *związanym z kodem* pliku.</span><span class="sxs-lookup"><span data-stu-id="d74dd-188">When you create a new Page file, Visual Studio automatically creates its *code-behind* file.</span></span> <span data-ttu-id="d74dd-189">Te pliki związane z kodem obsługi logiki w odpowiedzi na dane wejściowe użytkownika.</span><span class="sxs-lookup"><span data-stu-id="d74dd-189">These code-behind files handle the logic for responding to user input.</span></span>

    <span data-ttu-id="d74dd-190">Kod powinien wyglądać podobnie do poniższego dla **`ExpenseItHome`**:</span><span class="sxs-lookup"><span data-stu-id="d74dd-190">Your code should look like the following for **`ExpenseItHome`**:</span></span>

    [!code-csharp[ExpenseIt#2_5](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt2/ExpenseItHome.xaml.cs#2_5)]

    [!code-vb[ExpenseIt#2_5](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseItHome.xaml.vb#2_5)]

    <span data-ttu-id="d74dd-191">I podobnie do poniższego dla **ExpenseReportPage**:</span><span class="sxs-lookup"><span data-stu-id="d74dd-191">And like the following for **ExpenseReportPage**:</span></span>

    [!code-csharp[ExpenseIt#5](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt/ExpenseReportPage.xaml.cs#5)]

    [!code-vb[ExpenseIt#5](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt1_A/ExpenseReportPage.xaml.vb#5)]

1. <span data-ttu-id="d74dd-192">Dodawanie obrazu o nazwie *watermark.png* do projektu.</span><span class="sxs-lookup"><span data-stu-id="d74dd-192">Add an image named *watermark.png* to the project.</span></span> <span data-ttu-id="d74dd-193">Tworzenie własnego obrazu, skopiuj plik z przykładowego kodu lub jego [tutaj](https://github.com/Microsoft/WPF-Samples/tree/master/Getting%20Started/WalkthroughFirstWPFApp).</span><span class="sxs-lookup"><span data-stu-id="d74dd-193">You can create your own image, copy the file from the sample code, or get it [here](https://github.com/Microsoft/WPF-Samples/tree/master/Getting%20Started/WalkthroughFirstWPFApp).</span></span>

    1. <span data-ttu-id="d74dd-194">Kliknij prawym przyciskiem myszy węzeł projektu i wybierz **Dodaj** > **istniejący element**, lub naciśnij **Shift**+**Alt** + **A**.</span><span class="sxs-lookup"><span data-stu-id="d74dd-194">Right-click on the project node and select **Add** > **Existing Item**, or press **Shift**+**Alt**+**A**.</span></span>

    2. <span data-ttu-id="d74dd-195">W **Dodaj istniejący element** okna dialogowego, ustaw filtr pliku albo **wszystkie pliki** lub **pliki obrazów**, przejdź do pliku obrazu, które chcesz użyć, a następnie wybierz **Dodaj** .</span><span class="sxs-lookup"><span data-stu-id="d74dd-195">In the **Add Existing Item** dialog, set the file filter to either **All Files** or **Image Files**, browse to the image file you want to use, and then select **Add**.</span></span>

## <a name="build-and-run-the-application"></a><span data-ttu-id="d74dd-196">Kompilowanie i uruchamianie aplikacji</span><span class="sxs-lookup"><span data-stu-id="d74dd-196">Build and run the application</span></span>

1. <span data-ttu-id="d74dd-197">Aby skompilować i uruchomić aplikację, naciśnij klawisz **F5** lub wybierz **Rozpocznij debugowanie** z **debugowania** menu.</span><span class="sxs-lookup"><span data-stu-id="d74dd-197">To build and run the application, press **F5** or select **Start Debugging** from the **Debug** menu.</span></span>

    <span data-ttu-id="d74dd-198">Na poniższej ilustracji przedstawiono aplikację za pomocą <xref:System.Windows.Navigation.NavigationWindow> przyciski:</span><span class="sxs-lookup"><span data-stu-id="d74dd-198">The following illustration shows the application with the <xref:System.Windows.Navigation.NavigationWindow> buttons:</span></span>

    ![Aplikacja po Kompiluj i uruchom go.](./media/walkthrough-my-first-wpf-desktop-application/build-run-application.png)

2. <span data-ttu-id="d74dd-200">Zamknij aplikację, aby powrócić do programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="d74dd-200">Close the application to return to Visual Studio.</span></span>

## <a name="create-the-layout"></a><span data-ttu-id="d74dd-201">Utwórz układ</span><span class="sxs-lookup"><span data-stu-id="d74dd-201">Create the layout</span></span>

<span data-ttu-id="d74dd-202">Układ zapewnia uporządkowany sposób umieszczania elementów interfejsu użytkownika i zarządza także rozmiar i położenie tych elementów przy zmianie rozmiaru interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="d74dd-202">Layout provides an ordered way to place UI elements, and also manages the size and position of those elements when a UI is resized.</span></span> <span data-ttu-id="d74dd-203">Układ jest zwykle tworzysz przy użyciu jednego z następujących formantów układu:</span><span class="sxs-lookup"><span data-stu-id="d74dd-203">You typically create a layout with one of the following layout controls:</span></span>

- <span data-ttu-id="d74dd-204"><xref:System.Windows.Controls.Canvas> -Definiuje obszar, w którym możesz jawnie pozycjonować elementy podrzędne przy użyciu współrzędnych względnych w stosunku do obszaru kanwy.</span><span class="sxs-lookup"><span data-stu-id="d74dd-204"><xref:System.Windows.Controls.Canvas> - Defines an area within which you can explicitly position child elements by using coordinates that are relative to the Canvas area.</span></span>
- <span data-ttu-id="d74dd-205"><xref:System.Windows.Controls.DockPanel> -Definiuje obszar, w którym można rozmieścić elementy podrzędne w poziomie lub pionie, względem siebie.</span><span class="sxs-lookup"><span data-stu-id="d74dd-205"><xref:System.Windows.Controls.DockPanel> - Defines an area where you can arrange child elements either horizontally or vertically, relative to each other.</span></span>
- <span data-ttu-id="d74dd-206"><xref:System.Windows.Controls.Grid> -Definiuje elastyczny obszar siatki złożony z kolumn i wierszy.</span><span class="sxs-lookup"><span data-stu-id="d74dd-206"><xref:System.Windows.Controls.Grid> - Defines a flexible grid area that consists of columns and rows.</span></span>
- <span data-ttu-id="d74dd-207"><xref:System.Windows.Controls.StackPanel> -Rozmieszcza elementy podrzędne w jednej linii, która może być zorientowana poziomo czy pionowo.</span><span class="sxs-lookup"><span data-stu-id="d74dd-207"><xref:System.Windows.Controls.StackPanel> - Arranges child elements into a single line that can be oriented horizontally or vertically.</span></span>
- <span data-ttu-id="d74dd-208"><xref:System.Windows.Controls.VirtualizingStackPanel> -Rozmieszcza i Wirtualizuje zawartość w jednym wierszu, który jest ustawiony w poziomie lub pionie.</span><span class="sxs-lookup"><span data-stu-id="d74dd-208"><xref:System.Windows.Controls.VirtualizingStackPanel> - Arranges and virtualizes content on a single line that is oriented either horizontally or vertically.</span></span>
- <span data-ttu-id="d74dd-209"><xref:System.Windows.Controls.WrapPanel> -Ustawia elementy podrzędne na kolejnych pozycjach od od lewej do prawej, istotne zawartości do następnego wiersza na krawędzi zawierającego pole.</span><span class="sxs-lookup"><span data-stu-id="d74dd-209"><xref:System.Windows.Controls.WrapPanel> - Positions child elements in sequential position from left to right, breaking content to the next line at the edge of the containing box.</span></span> <span data-ttu-id="d74dd-210">Kolejne porządkowanie odbywa się sekwencyjnie od góry do dołu lub od prawej do lewej w zależności od wartości właściwości Orientation.</span><span class="sxs-lookup"><span data-stu-id="d74dd-210">Subsequent ordering happens sequentially from top to bottom or from right to left, depending on the value of the Orientation property.</span></span>

<span data-ttu-id="d74dd-211">Każda z tych kontrolek układu obsługuje określonego typu, układu dla jego elementów podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="d74dd-211">Each of these layout controls supports a particular type of layout for its child elements.</span></span> <span data-ttu-id="d74dd-212">`ExpenseIt` można zmienić rozmiar strony, a każda strona ma elementy, które są ułożone poziomo i pionowo wraz z innymi elementami.</span><span class="sxs-lookup"><span data-stu-id="d74dd-212">`ExpenseIt` pages can be resized, and each page has elements that are arranged horizontally and vertically alongside other elements.</span></span> <span data-ttu-id="d74dd-213">W tym przykładzie <xref:System.Windows.Controls.Grid> jest używany jako element układu dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="d74dd-213">In this example, the <xref:System.Windows.Controls.Grid> is used as  layout element for the application.</span></span>

> [!TIP]
> <span data-ttu-id="d74dd-214">Aby uzyskać więcej informacji na temat <xref:System.Windows.Controls.Panel> elementów, zobacz [Przegląd panele](../controls/panels-overview.md).</span><span class="sxs-lookup"><span data-stu-id="d74dd-214">For more information about <xref:System.Windows.Controls.Panel> elements, see [Panels overview](../controls/panels-overview.md).</span></span> <span data-ttu-id="d74dd-215">Aby uzyskać więcej informacji na temat układu, zobacz [układ](../advanced/layout.md).</span><span class="sxs-lookup"><span data-stu-id="d74dd-215">For more information about layout, see [Layout](../advanced/layout.md).</span></span>

<span data-ttu-id="d74dd-216">W tej sekcji utworzysz tabelą z jedną kolumną z trzema wierszami i margines 10 pikseli, dodając definicje kolumn i wierszy <xref:System.Windows.Controls.Grid> w *`ExpenseItHome.xaml`*.</span><span class="sxs-lookup"><span data-stu-id="d74dd-216">In this section, you create a single-column table with three rows and a 10-pixel margin by adding column and row definitions to the <xref:System.Windows.Controls.Grid> in *`ExpenseItHome.xaml`*.</span></span>

1. <span data-ttu-id="d74dd-217">W *`ExpenseItHome.xaml`* ustaw <xref:System.Windows.FrameworkElement.Margin%2A> właściwość <xref:System.Windows.Controls.Grid> elementu "10,0,10,10", która odnosi się do lewej, górnej, prawej strony i dolnego marginesu:</span><span class="sxs-lookup"><span data-stu-id="d74dd-217">In *`ExpenseItHome.xaml`*, set the <xref:System.Windows.FrameworkElement.Margin%2A> property on the <xref:System.Windows.Controls.Grid> element to "10,0,10,10", which corresponds to left, top, right and bottom margins:</span></span>

   ```xaml
   <Grid Margin="10,0,10,10">
   ```

   > [!TIP]
   > <span data-ttu-id="d74dd-218">Można również ustawić **margines** wartości w **właściwości** okna, w obszarze **układ** kategorii:</span><span class="sxs-lookup"><span data-stu-id="d74dd-218">You can also set the **Margin** values in the **Properties** window, under the **Layout** category:</span></span>
   >
   > ![Wartości marginesów w oknie właściwości](./media/properties-margin.png)

2. <span data-ttu-id="d74dd-220">Dodaj następujące XAML między <xref:System.Windows.Controls.Grid> znaczników do utworzenia definicji wierszy i kolumn:</span><span class="sxs-lookup"><span data-stu-id="d74dd-220">Add the following XAML between the <xref:System.Windows.Controls.Grid> tags to create the row and column definitions:</span></span>

    [!code-xaml[ExpenseIt#8](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt3/ExpenseItHome.xaml#8)]

    <span data-ttu-id="d74dd-221"><xref:System.Windows.Controls.RowDefinition.Height%2A> Dwóch wierszy jest równa <xref:System.Windows.GridLength.Auto%2A>, co oznacza, że wiersze mają rozmiar na podstawie zawartości w wierszach.</span><span class="sxs-lookup"><span data-stu-id="d74dd-221">The <xref:System.Windows.Controls.RowDefinition.Height%2A> of two rows is set to <xref:System.Windows.GridLength.Auto%2A>, which means that the rows are sized based on the content in the rows.</span></span> <span data-ttu-id="d74dd-222">Wartość domyślna <xref:System.Windows.Controls.RowDefinition.Height%2A> jest <xref:System.Windows.GridUnitType.Star> zmiany rozmiaru, co oznacza, że wiersze o nierównej wysokości ważona część dostępnego miejsca.</span><span class="sxs-lookup"><span data-stu-id="d74dd-222">The default <xref:System.Windows.Controls.RowDefinition.Height%2A> is <xref:System.Windows.GridUnitType.Star> sizing, which means that the row height is a weighted proportion of the available space.</span></span> <span data-ttu-id="d74dd-223">Na przykład jeśli masz dwa wiersze <xref:System.Windows.Controls.RowDefinition.Height%2A> elementu "\*", każdy z nich ma wysokości połowę dostępnego miejsca.</span><span class="sxs-lookup"><span data-stu-id="d74dd-223">For example if two rows each have a <xref:System.Windows.Controls.RowDefinition.Height%2A> of "\*", they each have a height that is half of the available space.</span></span>

    <span data-ttu-id="d74dd-224">Twoje <xref:System.Windows.Controls.Grid> nie powinien zawierać następujące XAML:</span><span class="sxs-lookup"><span data-stu-id="d74dd-224">Your <xref:System.Windows.Controls.Grid> should now contain the following XAML:</span></span>

    [!code-xaml[ExpenseIt#9](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt3/ExpenseItHome.xaml#9)]

## <a name="add-controls"></a><span data-ttu-id="d74dd-225">Dodawanie formantów</span><span class="sxs-lookup"><span data-stu-id="d74dd-225">Add controls</span></span>

<span data-ttu-id="d74dd-226">W tej sekcji zostaną zaktualizowane na stronie głównej interfejsu użytkownika, aby wyświetlić listę osób, wybierania jednej osoby do wyświetlania raportu wydatków.</span><span class="sxs-lookup"><span data-stu-id="d74dd-226">In this section, you'll update the home page UI to show a list of people, where you select one person to display their expense report.</span></span> <span data-ttu-id="d74dd-227">Formanty są obiektów interfejsu użytkownika, które umożliwiają użytkownikom na interakcję z aplikacją.</span><span class="sxs-lookup"><span data-stu-id="d74dd-227">Controls are UI objects that allow users to interact with your application.</span></span> <span data-ttu-id="d74dd-228">Aby uzyskać więcej informacji, zobacz [formantów](../controls/index.md).</span><span class="sxs-lookup"><span data-stu-id="d74dd-228">For more information, see [Controls](../controls/index.md).</span></span>

<span data-ttu-id="d74dd-229">Aby utworzyć tego interfejsu użytkownika, należy dodać następujące elementy do *`ExpenseItHome.xaml`*:</span><span class="sxs-lookup"><span data-stu-id="d74dd-229">To create this UI, you'll add the following elements to *`ExpenseItHome.xaml`*:</span></span>

- <span data-ttu-id="d74dd-230">Element <xref:System.Windows.Controls.ListBox> (Aby uzyskać listę osób).</span><span class="sxs-lookup"><span data-stu-id="d74dd-230">A <xref:System.Windows.Controls.ListBox> (for the list of people).</span></span>
- <span data-ttu-id="d74dd-231">Element <xref:System.Windows.Controls.Label> (dla nagłówka listy).</span><span class="sxs-lookup"><span data-stu-id="d74dd-231">A <xref:System.Windows.Controls.Label> (for the list header).</span></span>
- <span data-ttu-id="d74dd-232">Element <xref:System.Windows.Controls.Button> (aby kliknij, aby wyświetlić raport wydatków dla osoby, która jest zaznaczony na liście).</span><span class="sxs-lookup"><span data-stu-id="d74dd-232">A <xref:System.Windows.Controls.Button> (to click to view the expense report for the person that is selected in the list).</span></span>

<span data-ttu-id="d74dd-233">Każda kontrolka znajduje się w wierszu <xref:System.Windows.Controls.Grid> , ustawiając <xref:System.Windows.Controls.Grid.Row%2A?displayProperty=nameWithType> dołączona właściwość.</span><span class="sxs-lookup"><span data-stu-id="d74dd-233">Each control is placed in a row of the <xref:System.Windows.Controls.Grid> by setting the <xref:System.Windows.Controls.Grid.Row%2A?displayProperty=nameWithType> attached property.</span></span> <span data-ttu-id="d74dd-234">Aby uzyskać więcej informacji na temat właściwości dołączone zobacz [Przegląd właściwości dołączonych](../advanced/attached-properties-overview.md).</span><span class="sxs-lookup"><span data-stu-id="d74dd-234">For more information about attached properties, see [Attached Properties Overview](../advanced/attached-properties-overview.md).</span></span>

1. <span data-ttu-id="d74dd-235">W *`ExpenseItHome.xaml`*, Dodaj następujące XAML gdzieś między <xref:System.Windows.Controls.Grid> tagi:</span><span class="sxs-lookup"><span data-stu-id="d74dd-235">In *`ExpenseItHome.xaml`*, add the following XAML somewhere between the <xref:System.Windows.Controls.Grid> tags:</span></span>

   [!code-xaml[ExpenseIt#10](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt4/ExpenseItHome.xaml#10)]

   > [!TIP]
   > <span data-ttu-id="d74dd-236">Można również utworzyć formanty przeciągając je z **przybornika** okna na oknie projektu, a następnie ustawiając ich właściwości **właściwości** okna.</span><span class="sxs-lookup"><span data-stu-id="d74dd-236">You can also create the controls by dragging them from the **Toolbox** window onto the design window, and then setting their properties in the **Properties** window.</span></span>

2. <span data-ttu-id="d74dd-237">Skompiluj i uruchom aplikację.</span><span class="sxs-lookup"><span data-stu-id="d74dd-237">Build and run the application.</span></span>

    <span data-ttu-id="d74dd-238">Poniższa ilustracja zawiera kontrolki, które zostały utworzone:</span><span class="sxs-lookup"><span data-stu-id="d74dd-238">The following illustration shows the controls you created:</span></span>

![Zrzut ekranu przykładu programu ExpenseIt wyświetlanie listy nazw](./media/walkthrough-my-first-wpf-desktop-application/add-application-controls.png)

## <a name="add-an-image-and-a-title"></a><span data-ttu-id="d74dd-240">Dodaj obraz i tytuł</span><span class="sxs-lookup"><span data-stu-id="d74dd-240">Add an image and a title</span></span>

<span data-ttu-id="d74dd-241">W tej sekcji zostaną zaktualizowane interfejsie użytkownika strony głównej przy użyciu obrazu i tytuł strony.</span><span class="sxs-lookup"><span data-stu-id="d74dd-241">In this section, you'll update the home page UI with an image and a page title.</span></span>

1. <span data-ttu-id="d74dd-242">W *`ExpenseItHome.xaml`*, Dodaj kolejną kolumnę do <xref:System.Windows.Controls.Grid.ColumnDefinitions%2A> o stałym <xref:System.Windows.Controls.ColumnDefinition.Width%2A> 230 pikseli:</span><span class="sxs-lookup"><span data-stu-id="d74dd-242">In *`ExpenseItHome.xaml`*, add another column to the <xref:System.Windows.Controls.Grid.ColumnDefinitions%2A> with a fixed <xref:System.Windows.Controls.ColumnDefinition.Width%2A> of 230 pixels:</span></span>

    [!code-xaml[ExpenseIt#11](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseItHome.xaml?highlight=52-55)]

2. <span data-ttu-id="d74dd-243">Dodaj kolejny wiersz do <xref:System.Windows.Controls.Grid.RowDefinitions%2A>, łącznie cztery wiersze:</span><span class="sxs-lookup"><span data-stu-id="d74dd-243">Add another row to the <xref:System.Windows.Controls.Grid.RowDefinitions%2A>, for a total of four rows:</span></span>

    [!code-xaml[ExpenseIt#11b](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseItHome.xaml?highlight=57-62)]

3. <span data-ttu-id="d74dd-244">Przenieś kontrolki do drugiej kolumny, ustawiając <xref:System.Windows.Controls.Grid.Column%2A?displayProperty=nameWithType> właściwości na wartość 1 w każdym z trzech kontrolek (obramowanie, ListBox i przycisk).</span><span class="sxs-lookup"><span data-stu-id="d74dd-244">Move the controls to the second column by setting the <xref:System.Windows.Controls.Grid.Column%2A?displayProperty=nameWithType> property to 1 in each of the three controls (Border, ListBox, and Button).</span></span>

4. <span data-ttu-id="d74dd-245">Przenieś każdy formant w dół wiersz przez zwiększenie jego <xref:System.Windows.Controls.Grid.Row%2A?displayProperty=nameWithType> wartość 1 dla każdego z trzech kontrolek (obramowanie, ListBox i przycisku) i obramowania elementu.</span><span class="sxs-lookup"><span data-stu-id="d74dd-245">Move each control down a row by incrementing its <xref:System.Windows.Controls.Grid.Row%2A?displayProperty=nameWithType> value by 1 for each of the three controls (Border, ListBox, and Button) and for the Border element.</span></span>

   <span data-ttu-id="d74dd-246">XAML dla trzech kontrolek wygląda teraz następująco:</span><span class="sxs-lookup"><span data-stu-id="d74dd-246">The XAML for the three controls now looks like the following:</span></span>

    [!code-xaml[ExpenseIt#12](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#12)]

5. <span data-ttu-id="d74dd-247">Ustaw <xref:System.Windows.Controls.Panel.Background%2A?displayProperty=nameWithType> właściwości *watermark.png* plik obrazu, dodając następujące XAML dowolne miejsce między `<Grid>` i `</Grid>` tagi:</span><span class="sxs-lookup"><span data-stu-id="d74dd-247">Set the <xref:System.Windows.Controls.Panel.Background%2A?displayProperty=nameWithType> property to the *watermark.png* image file, by adding the following XAML anywhere between the `<Grid>` and `</Grid>` tags:</span></span>

    [!code-xaml[ExpenseIt#14](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#14)]

6. <span data-ttu-id="d74dd-248">Przed <xref:System.Windows.Controls.Border> elementu Dodawanie <xref:System.Windows.Controls.Label> z zawartością "Wyświetl raport wydatków".</span><span class="sxs-lookup"><span data-stu-id="d74dd-248">Before the <xref:System.Windows.Controls.Border> element, add a <xref:System.Windows.Controls.Label> with the content "View Expense Report".</span></span> <span data-ttu-id="d74dd-249">Ta etykieta jest tytuł strony.</span><span class="sxs-lookup"><span data-stu-id="d74dd-249">This label is the title of the page.</span></span>

    [!code-xaml[ExpenseIt#13](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt5/ExpenseItHome.xaml#13)]

7. <span data-ttu-id="d74dd-250">Skompiluj i uruchom aplikację.</span><span class="sxs-lookup"><span data-stu-id="d74dd-250">Build and run the application.</span></span>

<span data-ttu-id="d74dd-251">Poniższa ilustracja przedstawia wyniki co właśnie został dodany:</span><span class="sxs-lookup"><span data-stu-id="d74dd-251">The following illustration shows the results of what you just added:</span></span>

![Programu ExpenseIt Przykładowy zrzut ekranu nowego obrazu tła i tytuł strony](./media/walkthrough-my-first-wpf-desktop-application/add-application-image-title.png)

## <a name="add-code-to-handle-events"></a><span data-ttu-id="d74dd-253">Dodaj kod do obsługi zdarzeń</span><span class="sxs-lookup"><span data-stu-id="d74dd-253">Add code to handle events</span></span>

1. <span data-ttu-id="d74dd-254">W *`ExpenseItHome.xaml`*, Dodaj <xref:System.Windows.Controls.Primitives.ButtonBase.Click> procedurę obsługi zdarzeń do <xref:System.Windows.Controls.Button> elementu.</span><span class="sxs-lookup"><span data-stu-id="d74dd-254">In *`ExpenseItHome.xaml`*, add a <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event handler to the <xref:System.Windows.Controls.Button> element.</span></span> <span data-ttu-id="d74dd-255">Aby uzyskać więcej informacji, zobacz [jak: Utwórz procedurę obsługi zdarzenia prostego](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/bb675300(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="d74dd-255">For more information, see [How to: Create a simple event handler](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/bb675300(v=vs.100)).</span></span>

    [!code-xaml[ExpenseIt#15](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt6/ExpenseItHome.xaml#15)]

2. <span data-ttu-id="d74dd-256">Otwórz *`ExpenseItHome.xaml.vb`* lub *`ExpenseItHome.xaml.cs`*.</span><span class="sxs-lookup"><span data-stu-id="d74dd-256">Open *`ExpenseItHome.xaml.vb`* or *`ExpenseItHome.xaml.cs`*.</span></span>

3. <span data-ttu-id="d74dd-257">Dodaj następujący kod do `ExpenseItHome` klasy, aby dodać przycisk, program obsługi zdarzeń kliknięcia.</span><span class="sxs-lookup"><span data-stu-id="d74dd-257">Add the following code to the `ExpenseItHome` class to add a button click event handler.</span></span> <span data-ttu-id="d74dd-258">Zostanie otwarty program obsługi zdarzeń **ExpenseReportPage** strony.</span><span class="sxs-lookup"><span data-stu-id="d74dd-258">The event handler opens the **ExpenseReportPage** page.</span></span>

    [!code-csharp[ExpenseIt#16](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt6/ExpenseItHome.xaml.cs#16)]
    [!code-vb[ExpenseIt#16](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt6/ExpenseItHome.xaml.vb#16)]

## <a name="create-the-ui-for-expensereportpage"></a><span data-ttu-id="d74dd-259">Tworzenie interfejsu użytkownika dla ExpenseReportPage</span><span class="sxs-lookup"><span data-stu-id="d74dd-259">Create the UI for ExpenseReportPage</span></span>

<span data-ttu-id="d74dd-260">*ExpenseReportPage.xaml* wyświetla raport wydatków dla osób, które wybrano na **`ExpenseItHome`** strony.</span><span class="sxs-lookup"><span data-stu-id="d74dd-260">*ExpenseReportPage.xaml* displays the expense report for the person that's selected on the **`ExpenseItHome`** page.</span></span> <span data-ttu-id="d74dd-261">W tej sekcji utworzysz interfejs użytkownika dla **ExpenseReportPage**.</span><span class="sxs-lookup"><span data-stu-id="d74dd-261">In this section, you'll create the UI for **ExpenseReportPage**.</span></span> <span data-ttu-id="d74dd-262">Dodasz również tła i wypełnij kolorów do różnych elementów interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="d74dd-262">You'll also add background and fill colors to the various UI elements.</span></span>

1. <span data-ttu-id="d74dd-263">Otwórz *ExpenseReportPage.xaml*.</span><span class="sxs-lookup"><span data-stu-id="d74dd-263">Open *ExpenseReportPage.xaml*.</span></span>

2. <span data-ttu-id="d74dd-264">Dodaj następujące XAML między <xref:System.Windows.Controls.Grid> tagi:</span><span class="sxs-lookup"><span data-stu-id="d74dd-264">Add the following XAML between the <xref:System.Windows.Controls.Grid> tags:</span></span>

    [!code-xaml[ExpenseIt#17](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt6/ExpenseReportPage.xaml#17)]

    <span data-ttu-id="d74dd-265">Ten interfejs jest podobny do *`ExpenseItHome.xaml`*, z wyjątkiem dane raportu są wyświetlane w <xref:System.Windows.Controls.DataGrid>.</span><span class="sxs-lookup"><span data-stu-id="d74dd-265">This UI is similar to *`ExpenseItHome.xaml`*, except the report data is displayed in a <xref:System.Windows.Controls.DataGrid>.</span></span>

3. <span data-ttu-id="d74dd-266">Skompiluj i uruchom aplikację.</span><span class="sxs-lookup"><span data-stu-id="d74dd-266">Build and run the application.</span></span>

4. <span data-ttu-id="d74dd-267">Wybierz **widoku** przycisku.</span><span class="sxs-lookup"><span data-stu-id="d74dd-267">Select the **View** button.</span></span>

    <span data-ttu-id="d74dd-268">Zostanie wyświetlona strona raportu wydatków.</span><span class="sxs-lookup"><span data-stu-id="d74dd-268">The expense report page appears.</span></span> <span data-ttu-id="d74dd-269">Zwróć również uwagę, że zostanie włączony przycisk przeglądania do tyłu.</span><span class="sxs-lookup"><span data-stu-id="d74dd-269">Also notice that the back navigation button is enabled.</span></span>

<span data-ttu-id="d74dd-270">Na poniższej ilustracji przedstawiono elementy interfejsu użytkownika dodano do *ExpenseReportPage.xaml*.</span><span class="sxs-lookup"><span data-stu-id="d74dd-270">The following illustration shows the UI elements added to *ExpenseReportPage.xaml*.</span></span>

![Programu ExpenseIt Przykładowy zrzut ekranu interfejsu użytkownika, utworzony przez ExpenseReportPage.](./media/walkthrough-my-first-wpf-desktop-application/create-application-ui.png)

## <a name="style-controls"></a><span data-ttu-id="d74dd-272">Kontrolki stylu</span><span class="sxs-lookup"><span data-stu-id="d74dd-272">Style controls</span></span>

<span data-ttu-id="d74dd-273">Wygląd elementów różnych często jest taka sama dla wszystkich elementów tego samego typu w interfejsie użytkownika.</span><span class="sxs-lookup"><span data-stu-id="d74dd-273">The appearance of various elements is often the same for all elements of the same type in a UI.</span></span> <span data-ttu-id="d74dd-274">Korzysta z interfejsu użytkownika [style](../controls/styling-and-templating.md) się wygląd wielokrotnego użytku dla wielu elementów.</span><span class="sxs-lookup"><span data-stu-id="d74dd-274">UI uses [styles](../controls/styling-and-templating.md) to make appearances reusable across multiple elements.</span></span> <span data-ttu-id="d74dd-275">Możliwość ponownego wykorzystania stylów pomaga uprościć tworzenie XAML i zarządzanie nimi.</span><span class="sxs-lookup"><span data-stu-id="d74dd-275">The reusability of styles helps to simplify XAML creation and management.</span></span> <span data-ttu-id="d74dd-276">W tej sekcji zastępuje atrybuty-elementowej, które zostały zdefiniowane w poprzednich krokach przy użyciu stylów.</span><span class="sxs-lookup"><span data-stu-id="d74dd-276">This section replaces the per-element attributes that were defined in previous steps with styles.</span></span>

1. <span data-ttu-id="d74dd-277">Otwórz *Application.xaml* lub *App.xaml*.</span><span class="sxs-lookup"><span data-stu-id="d74dd-277">Open *Application.xaml* or *App.xaml*.</span></span>

2. <span data-ttu-id="d74dd-278">Dodaj następujące XAML między <xref:System.Windows.Application.Resources%2A?displayProperty=nameWithType> tagi:</span><span class="sxs-lookup"><span data-stu-id="d74dd-278">Add the following XAML between the <xref:System.Windows.Application.Resources%2A?displayProperty=nameWithType> tags:</span></span>

    [!code-xaml[ExpenseIt#18](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt7/App.xaml#18)]

    <span data-ttu-id="d74dd-279">Ta XAML dodaje następujące style:</span><span class="sxs-lookup"><span data-stu-id="d74dd-279">This XAML adds the following styles:</span></span>

    - <span data-ttu-id="d74dd-280">`headerTextStyle`: Aby sformatować tytuł strony <xref:System.Windows.Controls.Label>.</span><span class="sxs-lookup"><span data-stu-id="d74dd-280">`headerTextStyle`: To format the page title <xref:System.Windows.Controls.Label>.</span></span>

    - <span data-ttu-id="d74dd-281">`labelStyle`: Aby sformatować <xref:System.Windows.Controls.Label> kontrolki.</span><span class="sxs-lookup"><span data-stu-id="d74dd-281">`labelStyle`: To format the <xref:System.Windows.Controls.Label> controls.</span></span>

    - <span data-ttu-id="d74dd-282">`columnHeaderStyle`: Aby sformatować <xref:System.Windows.Controls.Primitives.DataGridColumnHeader>.</span><span class="sxs-lookup"><span data-stu-id="d74dd-282">`columnHeaderStyle`: To format the <xref:System.Windows.Controls.Primitives.DataGridColumnHeader>.</span></span>

    - <span data-ttu-id="d74dd-283">`listHeaderStyle`: Aby sformatować nagłówek listy <xref:System.Windows.Controls.Border> kontrolki.</span><span class="sxs-lookup"><span data-stu-id="d74dd-283">`listHeaderStyle`: To format the list header <xref:System.Windows.Controls.Border> controls.</span></span>

    - <span data-ttu-id="d74dd-284">`listHeaderTextStyle`: Aby sformatować nagłówek listy <xref:System.Windows.Controls.Label>.</span><span class="sxs-lookup"><span data-stu-id="d74dd-284">`listHeaderTextStyle`: To format the list header <xref:System.Windows.Controls.Label>.</span></span>

    - <span data-ttu-id="d74dd-285">`buttonStyle`: Aby sformatować <xref:System.Windows.Controls.Button> na `ExpenseItHome.xaml`.</span><span class="sxs-lookup"><span data-stu-id="d74dd-285">`buttonStyle`: To format the <xref:System.Windows.Controls.Button> on `ExpenseItHome.xaml`.</span></span>

    <span data-ttu-id="d74dd-286">Zauważ, że style są zasobami i elementy podrzędne <xref:System.Windows.Application.Resources%2A?displayProperty=nameWithType> elementu właściwości.</span><span class="sxs-lookup"><span data-stu-id="d74dd-286">Notice that the styles are resources and children of the <xref:System.Windows.Application.Resources%2A?displayProperty=nameWithType> property element.</span></span> <span data-ttu-id="d74dd-287">W tej lokalizacji stylów są stosowane do wszystkich elementów w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="d74dd-287">In this location, the styles are applied to all the elements in an application.</span></span> <span data-ttu-id="d74dd-288">Na przykład korzystania z zasobów w aplikacji platformy .NET, zobacz [wykorzystania zasobów aplikacji](../advanced/how-to-use-application-resources.md).</span><span class="sxs-lookup"><span data-stu-id="d74dd-288">For an example of using resources in a .NET app, see [Use Application Resources](../advanced/how-to-use-application-resources.md).</span></span>

3. <span data-ttu-id="d74dd-289">W *`ExpenseItHome.xaml`*, Zamień wszystko pomiędzy <xref:System.Windows.Controls.Grid> elementów za pomocą następujących XAML:</span><span class="sxs-lookup"><span data-stu-id="d74dd-289">In *`ExpenseItHome.xaml`*, replace everything between the <xref:System.Windows.Controls.Grid> elements with the following XAML:</span></span>

    [!code-xaml[ExpenseIt#19](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt7/ExpenseItHome.xaml#19)]

    <span data-ttu-id="d74dd-290">Właściwości, takie jak <xref:System.Windows.VerticalAlignment> i <xref:System.Windows.Media.FontFamily> definiują wygląd każdego formantu usunięty i zastąpiony, stosując style.</span><span class="sxs-lookup"><span data-stu-id="d74dd-290">The properties such as <xref:System.Windows.VerticalAlignment> and <xref:System.Windows.Media.FontFamily> that define the look of each control are removed and replaced by applying the styles.</span></span> <span data-ttu-id="d74dd-291">Na przykład `headerTextStyle` jest stosowany do "Wyświetl raport wydatków" <xref:System.Windows.Controls.Label>.</span><span class="sxs-lookup"><span data-stu-id="d74dd-291">For example, the `headerTextStyle` is applied to the "View Expense Report" <xref:System.Windows.Controls.Label>.</span></span>

4. <span data-ttu-id="d74dd-292">Otwórz *ExpenseReportPage.xaml*.</span><span class="sxs-lookup"><span data-stu-id="d74dd-292">Open *ExpenseReportPage.xaml*.</span></span>

5. <span data-ttu-id="d74dd-293">Zamień wszystko pomiędzy <xref:System.Windows.Controls.Grid> elementów za pomocą następujących XAML:</span><span class="sxs-lookup"><span data-stu-id="d74dd-293">Replace everything between the <xref:System.Windows.Controls.Grid> elements with the following XAML:</span></span>

    [!code-xaml[ExpenseIt#20](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt7/ExpenseReportPage.xaml#20)]

    <span data-ttu-id="d74dd-294">Ta XAML dodaje style, które mają <xref:System.Windows.Controls.Label> i <xref:System.Windows.Controls.Border> elementów.</span><span class="sxs-lookup"><span data-stu-id="d74dd-294">This XAML adds styles to the <xref:System.Windows.Controls.Label> and <xref:System.Windows.Controls.Border> elements.</span></span>

6. <span data-ttu-id="d74dd-295">Skompiluj i uruchom aplikację.</span><span class="sxs-lookup"><span data-stu-id="d74dd-295">Build and run the application.</span></span> <span data-ttu-id="d74dd-296">Wygląd okna jest taka sama jak wcześniej.</span><span class="sxs-lookup"><span data-stu-id="d74dd-296">The window appearance is the same as previously.</span></span>

    ![Zrzut ekranu przykładu programu ExpenseIt przy użyciu tego samego wygląd, tak jak w ostatniej sekcji.](./media/walkthrough-my-first-wpf-desktop-application/create-application-ui.png)

7. <span data-ttu-id="d74dd-298">Zamknij aplikację, aby powrócić do programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="d74dd-298">Close the application to return to Visual Studio.</span></span>

## <a name="bind-data-to-a-control"></a><span data-ttu-id="d74dd-299">Powiązanie danych kontrolki</span><span class="sxs-lookup"><span data-stu-id="d74dd-299">Bind data to a control</span></span>

<span data-ttu-id="d74dd-300">W tej sekcji utworzysz dane XML, który jest powiązany z różnych formantów.</span><span class="sxs-lookup"><span data-stu-id="d74dd-300">In this section, you'll create the XML data that is bound to various controls.</span></span>

1. <span data-ttu-id="d74dd-301">W *`ExpenseItHome.xaml`*, po otwarciu <xref:System.Windows.Controls.Grid> elementu, Dodaj następujące XAML do tworzenia <xref:System.Windows.Data.XmlDataProvider> dla każdej osoby, która zawiera dane:</span><span class="sxs-lookup"><span data-stu-id="d74dd-301">In *`ExpenseItHome.xaml`*, after the opening <xref:System.Windows.Controls.Grid> element, add the following XAML to create an <xref:System.Windows.Data.XmlDataProvider> that contains the data for each person:</span></span>

    [!code-xaml[ExpenseIt#23](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml?range=13,16-40,49)]

    <span data-ttu-id="d74dd-302">Dane są tworzone jako <xref:System.Windows.Controls.Grid> zasobów.</span><span class="sxs-lookup"><span data-stu-id="d74dd-302">The data is created as a <xref:System.Windows.Controls.Grid> resource.</span></span> <span data-ttu-id="d74dd-303">Zazwyczaj te dane będą ładowane jako plik, ale dla uproszczenia dane są dodawane na tekście.</span><span class="sxs-lookup"><span data-stu-id="d74dd-303">Normally this data would be loaded as a file, but for simplicity the data is added inline.</span></span>

2. <span data-ttu-id="d74dd-304">W ramach `<Grid.Resources>` elementu, Dodaj następujący kod `<xref:System.Windows.DataTemplate>` element, który definiuje sposób wyświetlania danych w <xref:System.Windows.Controls.ListBox>po `<XmlDataProvider>` elementu:</span><span class="sxs-lookup"><span data-stu-id="d74dd-304">Within the `<Grid.Resources>` element, add the following `<xref:System.Windows.DataTemplate>` element, which defines how to display the data in the <xref:System.Windows.Controls.ListBox>, after the `<XmlDataProvider>` element:</span></span>

    [!code-xaml[ExpenseIt#24](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml?range=13,43-46,49)]

    <span data-ttu-id="d74dd-305">Aby uzyskać więcej informacji na temat szablonów danych zobacz [Przegląd szablonowanie danych](../data/data-templating-overview.md).</span><span class="sxs-lookup"><span data-stu-id="d74dd-305">For more information about data templates, see [Data templating overview](../data/data-templating-overview.md).</span></span>

3. <span data-ttu-id="d74dd-306">Zastąp istniejące <xref:System.Windows.Controls.ListBox> za pomocą następujących XAML:</span><span class="sxs-lookup"><span data-stu-id="d74dd-306">Replace the existing <xref:System.Windows.Controls.ListBox> with the following XAML:</span></span>

    [!code-xaml[ExpenseIt#25](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml#25)]

    <span data-ttu-id="d74dd-307">Wiąże się to XAML <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> właściwość <xref:System.Windows.Controls.ListBox> ze źródłem danych i stosuje szablon danych jako <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A>.</span><span class="sxs-lookup"><span data-stu-id="d74dd-307">This XAML binds the <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> property of the <xref:System.Windows.Controls.ListBox> to the data source and applies the data template as the <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A>.</span></span>

## <a name="connect-data-to-controls"></a><span data-ttu-id="d74dd-308">Łączenie danych z kontrolkami</span><span class="sxs-lookup"><span data-stu-id="d74dd-308">Connect data to controls</span></span>

<span data-ttu-id="d74dd-309">Następnie dodasz kod, aby pobrać nazwy, która została wybrana na **`ExpenseItHome`** strony, a następnie przekazać go do konstruktora obiektu **ExpenseReportPage**.</span><span class="sxs-lookup"><span data-stu-id="d74dd-309">Next, you'll add code to retrieve the name that's selected on the **`ExpenseItHome`** page and pass it to the constructor of **ExpenseReportPage**.</span></span> <span data-ttu-id="d74dd-310">**ExpenseReportPage** ustawia kontekst danych przy użyciu przekazanych elementu, który jest zdefiniowany kontrolek w *ExpenseReportPage.xaml* powiązać.</span><span class="sxs-lookup"><span data-stu-id="d74dd-310">**ExpenseReportPage** sets its data context with the passed item, which is what the controls defined in *ExpenseReportPage.xaml* bind to.</span></span>

1. <span data-ttu-id="d74dd-311">Otwórz *ExpenseReportPage.xaml.vb* lub *ExpenseReportPage.xaml.cs*.</span><span class="sxs-lookup"><span data-stu-id="d74dd-311">Open *ExpenseReportPage.xaml.vb* or *ExpenseReportPage.xaml.cs*.</span></span>

2. <span data-ttu-id="d74dd-312">Dodaj konstruktora przyjmującego obiekt, dzięki czemu można przekazać dane raportu wydatków wybrane osoby.</span><span class="sxs-lookup"><span data-stu-id="d74dd-312">Add a constructor that takes an object so you can pass the expense report data of the selected person.</span></span>

    [!code-csharp[ExpenseIt#26](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseReportPage.xaml.cs#26)]
    [!code-vb[ExpenseIt#26](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt8/ExpenseReportPage.xaml.vb#26)]

3. <span data-ttu-id="d74dd-313">Otwórz *`ExpenseItHome.xaml.vb`* lub *`ExpenseItHome.xaml.cs`*.</span><span class="sxs-lookup"><span data-stu-id="d74dd-313">Open *`ExpenseItHome.xaml.vb`* or *`ExpenseItHome.xaml.cs`*.</span></span>

4. <span data-ttu-id="d74dd-314">Zmiana <xref:System.Windows.Controls.Primitives.ButtonBase.Click> program obsługi zdarzeń, aby wywołać nowego konstruktora, przekazując dane raportu wydatków wybrane osoby.</span><span class="sxs-lookup"><span data-stu-id="d74dd-314">Change the <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event handler to call the new constructor passing the expense report data of the selected person.</span></span>

    [!code-csharp[ExpenseIt#27](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt8/ExpenseItHome.xaml.cs#27)]
    [!code-vb[ExpenseIt#27](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpenseIt/VB/ExpenseIt8/ExpenseItHome.xaml.vb#27)]

## <a name="style-data-with-data-templates"></a><span data-ttu-id="d74dd-315">Styl danych za pomocą szablonów danych</span><span class="sxs-lookup"><span data-stu-id="d74dd-315">Style data with data templates</span></span>

<span data-ttu-id="d74dd-316">W tej sekcji zostaną zaktualizowane w interfejsie użytkownika dla każdego elementu na listach powiązanych z danymi przy użyciu szablonów danych.</span><span class="sxs-lookup"><span data-stu-id="d74dd-316">In this section, you'll update the UI for each item in the data-bound lists by using data templates.</span></span>

1. <span data-ttu-id="d74dd-317">Otwórz *ExpenseReportPage.xaml*.</span><span class="sxs-lookup"><span data-stu-id="d74dd-317">Open *ExpenseReportPage.xaml*.</span></span>

2. <span data-ttu-id="d74dd-318">Powiąż z zawartością "Name" i "Dział" <xref:System.Windows.Controls.Label> elementy do odpowiednich danych źródła właściwości.</span><span class="sxs-lookup"><span data-stu-id="d74dd-318">Bind the content of the "Name" and "Department" <xref:System.Windows.Controls.Label> elements to the appropriate data source property.</span></span> <span data-ttu-id="d74dd-319">Aby uzyskać więcej informacji na temat tworzenia powiązań danych, zobacz [Przegląd wiązanie danych](../data/data-binding-overview.md).</span><span class="sxs-lookup"><span data-stu-id="d74dd-319">For more information about data binding, see [Data binding overview](../data/data-binding-overview.md).</span></span>

    [!code-xaml[ExpenseIt#31](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseReportPage.xaml#31)]

3. <span data-ttu-id="d74dd-320">Po otwarciu <xref:System.Windows.Controls.Grid> elementu, Dodaj następujące szablony danych, które określają sposób wyświetlania danych raportu wydatków:</span><span class="sxs-lookup"><span data-stu-id="d74dd-320">After the opening <xref:System.Windows.Controls.Grid> element, add the following data templates, which define how to display the expense report data:</span></span>

    [!code-xaml[ExpenseIt#30](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseReportPage.xaml#30)]

4. <span data-ttu-id="d74dd-321">Zastąp <xref:System.Windows.Controls.DataGridTextColumn> elementów za pomocą <xref:System.Windows.Controls.DataGridTemplateColumn> w obszarze <xref:System.Windows.Controls.DataGrid> elementu i stosować szablony do nich.</span><span class="sxs-lookup"><span data-stu-id="d74dd-321">Replace the <xref:System.Windows.Controls.DataGridTextColumn> elements with <xref:System.Windows.Controls.DataGridTemplateColumn> under the <xref:System.Windows.Controls.DataGrid> element and apply the templates to them.</span></span>

    [!code-xaml[ExpenseIt#32](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpenseIt/CSharp/ExpenseIt9/ExpenseReportPage.xaml#32)]

5. <span data-ttu-id="d74dd-322">Skompiluj i uruchom aplikację.</span><span class="sxs-lookup"><span data-stu-id="d74dd-322">Build and run the application.</span></span>

6. <span data-ttu-id="d74dd-323">Wybierz osobę, a następnie wybierz pozycję **widoku** przycisku.</span><span class="sxs-lookup"><span data-stu-id="d74dd-323">Select a person and then select the **View** button.</span></span>

<span data-ttu-id="d74dd-324">Na poniższej ilustracji przedstawiono obie strony `ExpenseIt` aplikacji za pomocą formantów, układ, style, powiązań danych i zastosowanych szablonów danych:</span><span class="sxs-lookup"><span data-stu-id="d74dd-324">The following illustration shows both pages of the `ExpenseIt` application with controls, layout, styles, data binding, and data templates applied:</span></span>

![Obie strony aplikacji, wyświetlanie listy nazw i raportu wydatków.](./media/walkthrough-my-first-wpf-desktop-application/application-data-templates.png)

> [!NOTE]
> <span data-ttu-id="d74dd-326">Ten przykład demonstruje określonych funkcji, WPF i nie należy wykonać wszystkie najlepsze rozwiązania w zakresie elementów, takich jak bezpieczeństwo, lokalizacja i ułatwienia dostępu.</span><span class="sxs-lookup"><span data-stu-id="d74dd-326">This sample demonstrates a specific feature of WPF and doesn't follow all best practices for things like security, localization, and accessibility.</span></span> <span data-ttu-id="d74dd-327">Aby uzyskać kompleksowe informacje na temat WPF i najlepszych rozwiązań projektowania aplikacji platformy .NET zobacz następujące tematy:</span><span class="sxs-lookup"><span data-stu-id="d74dd-327">For comprehensive coverage of WPF and the .NET app development best practices, see the following topics:</span></span>
>
> - [<span data-ttu-id="d74dd-328">Ułatwienia dostępu</span><span class="sxs-lookup"><span data-stu-id="d74dd-328">Accessibility</span></span>](../../ui-automation/accessibility-best-practices.md)
>
> - [<span data-ttu-id="d74dd-329">Zabezpieczenia</span><span class="sxs-lookup"><span data-stu-id="d74dd-329">Security</span></span>](../security-wpf.md)
>
> - [<span data-ttu-id="d74dd-330">Lokalizacja i globalizacja WPF</span><span class="sxs-lookup"><span data-stu-id="d74dd-330">WPF globalization and localization</span></span>](../advanced/wpf-globalization-and-localization-overview.md)
>
> - [<span data-ttu-id="d74dd-331">Wydajności WPF</span><span class="sxs-lookup"><span data-stu-id="d74dd-331">WPF performance</span></span>](../advanced/optimizing-wpf-application-performance.md)

## <a name="next-steps"></a><span data-ttu-id="d74dd-332">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="d74dd-332">Next steps</span></span>

<span data-ttu-id="d74dd-333">W tym instruktażu przedstawiono kilka technik tworzenia interfejsu użytkownika przy użyciu Windows Presentation Foundation (WPF).</span><span class="sxs-lookup"><span data-stu-id="d74dd-333">In this walkthrough you learned a number of techniques for creating a UI using Windows Presentation Foundation (WPF).</span></span> <span data-ttu-id="d74dd-334">Powinna już podstawową wiedzę na temat bloków konstrukcyjnych związanych z danymi aplikacji .NET.</span><span class="sxs-lookup"><span data-stu-id="d74dd-334">You should now have a basic understanding of the building blocks of a data-bound .NET app.</span></span> <span data-ttu-id="d74dd-335">Aby uzyskać więcej informacji o modelach programowania i architektura WPF zobacz następujące tematy:</span><span class="sxs-lookup"><span data-stu-id="d74dd-335">For more information about the WPF architecture and programming models, see the following topics:</span></span>

- [<span data-ttu-id="d74dd-336">Architektura WPF</span><span class="sxs-lookup"><span data-stu-id="d74dd-336">WPF architecture</span></span>](../advanced/wpf-architecture.md)
- [<span data-ttu-id="d74dd-337">Przegląd XAML (WPF)</span><span class="sxs-lookup"><span data-stu-id="d74dd-337">XAML overview (WPF)</span></span>](../advanced/xaml-overview-wpf.md)
- [<span data-ttu-id="d74dd-338">Przegląd właściwości zależności</span><span class="sxs-lookup"><span data-stu-id="d74dd-338">Dependency properties overview</span></span>](../advanced/dependency-properties-overview.md)
- [<span data-ttu-id="d74dd-339">Układ</span><span class="sxs-lookup"><span data-stu-id="d74dd-339">Layout</span></span>](../advanced/layout.md)

<span data-ttu-id="d74dd-340">Aby uzyskać więcej informacji na temat tworzenia aplikacji zobacz następujące tematy:</span><span class="sxs-lookup"><span data-stu-id="d74dd-340">For more information about creating applications, see the following topics:</span></span>

- [<span data-ttu-id="d74dd-341">Tworzenie aplikacji</span><span class="sxs-lookup"><span data-stu-id="d74dd-341">Application development</span></span>](../app-development/index.md)
- [<span data-ttu-id="d74dd-342">Kontrolki</span><span class="sxs-lookup"><span data-stu-id="d74dd-342">Controls</span></span>](../controls/index.md)
- [<span data-ttu-id="d74dd-343">Przegląd wiązanie danych</span><span class="sxs-lookup"><span data-stu-id="d74dd-343">Data binding overview</span></span>](../data/data-binding-overview.md)
- [<span data-ttu-id="d74dd-344">Grafika i multimedia</span><span class="sxs-lookup"><span data-stu-id="d74dd-344">Graphics and multimedia</span></span>](../graphics-multimedia/index.md)
- [<span data-ttu-id="d74dd-345">Dokumenty w WPF</span><span class="sxs-lookup"><span data-stu-id="d74dd-345">Documents in WPF</span></span>](../advanced/documents-in-wpf.md)

## <a name="see-also"></a><span data-ttu-id="d74dd-346">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d74dd-346">See also</span></span>

- [<span data-ttu-id="d74dd-347">Panele — omówienie</span><span class="sxs-lookup"><span data-stu-id="d74dd-347">Panels overview</span></span>](../controls/panels-overview.md)
- [<span data-ttu-id="d74dd-348">Przegląd szablonowanie danych</span><span class="sxs-lookup"><span data-stu-id="d74dd-348">Data templating overview</span></span>](../data/data-templating-overview.md)
- [<span data-ttu-id="d74dd-349">Tworzenie aplikacji WPF</span><span class="sxs-lookup"><span data-stu-id="d74dd-349">Build a WPF application</span></span>](../app-development/building-a-wpf-application-wpf.md)
- [<span data-ttu-id="d74dd-350">Style i szablony</span><span class="sxs-lookup"><span data-stu-id="d74dd-350">Styles and templates</span></span>](../controls/styles-and-templates.md)
