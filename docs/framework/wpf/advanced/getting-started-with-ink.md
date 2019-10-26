---
title: Tworzenie InkCanvas w aplikacji WPF w programie Visual Studio
ms.date: 08/15/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- procedural code in lieu of XAML [WPF]
- XAML [WPF], procedural code in lieu of
- InkCanvas (WPF)
ms.assetid: 760332dd-594a-475d-865b-01659db8cab7
ms.openlocfilehash: ebbf25037921e7802b2bfcb6ffa562d16a849ffa
ms.sourcegitcommit: 82f94a44ad5c64a399df2a03fa842db308185a76
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/25/2019
ms.locfileid: "72920248"
---
# <a name="get-started-with-ink-in-wpf"></a><span data-ttu-id="1728d-102">Wprowadzenie do pisma odręcznego w WPF</span><span class="sxs-lookup"><span data-stu-id="1728d-102">Get Started with Ink in WPF</span></span>

<span data-ttu-id="1728d-103">Windows Presentation Foundation (WPF) zawiera funkcję atramentu, która ułatwia włączenie cyfrowego atramentu do aplikacji.</span><span class="sxs-lookup"><span data-stu-id="1728d-103">Windows Presentation Foundation (WPF) has an ink feature that makes it easy to incorporate digital ink into your app.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="1728d-104">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="1728d-104">Prerequisites</span></span>

<span data-ttu-id="1728d-105">Aby skorzystać z poniższych przykładów, należy najpierw zainstalować [program Visual Studio](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019).</span><span class="sxs-lookup"><span data-stu-id="1728d-105">To use the following examples, first install [Visual Studio](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019).</span></span> <span data-ttu-id="1728d-106">Pomaga również dowiedzieć się, jak napisać podstawowe aplikacje WPF.</span><span class="sxs-lookup"><span data-stu-id="1728d-106">It also helps to know how to write basic WPF apps.</span></span> <span data-ttu-id="1728d-107">Aby uzyskać pomoc dotyczącą rozpoczynania pracy z programem WPF, zobacz [Przewodnik: moja pierwsza aplikacja klasyczna WPF](../getting-started/walkthrough-my-first-wpf-desktop-application.md).</span><span class="sxs-lookup"><span data-stu-id="1728d-107">For help getting started with WPF, see [Walkthrough: My first WPF desktop application](../getting-started/walkthrough-my-first-wpf-desktop-application.md).</span></span>

## <a name="quick-start"></a><span data-ttu-id="1728d-108">Szybki start</span><span class="sxs-lookup"><span data-stu-id="1728d-108">Quick Start</span></span>

<span data-ttu-id="1728d-109">Ta sekcja ułatwia pisanie prostej aplikacji WPF, która zbiera pismo odręczne.</span><span class="sxs-lookup"><span data-stu-id="1728d-109">This section helps you write a simple WPF application that collects ink.</span></span>

### <a name="got-ink"></a><span data-ttu-id="1728d-110">Masz atrament?</span><span class="sxs-lookup"><span data-stu-id="1728d-110">Got Ink?</span></span>

<span data-ttu-id="1728d-111">Aby utworzyć aplikację WPF, która obsługuje pismo odręczne:</span><span class="sxs-lookup"><span data-stu-id="1728d-111">To create a WPF app that supports ink:</span></span>

1. <span data-ttu-id="1728d-112">Otwórz program Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="1728d-112">Open Visual Studio.</span></span>

2. <span data-ttu-id="1728d-113">Utwórz nową **aplikację WPF**.</span><span class="sxs-lookup"><span data-stu-id="1728d-113">Create a new **WPF App**.</span></span>

   <span data-ttu-id="1728d-114">W oknie dialogowym **Nowy projekt** rozwiń węzeł **zainstalowana** > **Wizualizacja C#**  lub **Visual Basic** > kategorii **pulpitu systemu Windows** .</span><span class="sxs-lookup"><span data-stu-id="1728d-114">In the **New Project** dialog, expand the **Installed** > **Visual C#** or **Visual Basic** > **Windows Desktop** category.</span></span> <span data-ttu-id="1728d-115">Następnie wybierz szablon aplikacji **Aplikacja WPF (.NET Framework)** .</span><span class="sxs-lookup"><span data-stu-id="1728d-115">Then, select the **WPF App (.NET Framework)** app template.</span></span> <span data-ttu-id="1728d-116">Wprowadź nazwę, a następnie wybierz przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="1728d-116">Enter a name, and then select **OK**.</span></span>

   <span data-ttu-id="1728d-117">Program Visual Studio tworzy projekt, a *MainWindow. XAML* zostanie otwarty w projektancie.</span><span class="sxs-lookup"><span data-stu-id="1728d-117">Visual Studio creates the project, and *MainWindow.xaml* opens in the designer.</span></span>

3. <span data-ttu-id="1728d-118">Wpisz `<InkCanvas/>` między tagami `<Grid>`.</span><span class="sxs-lookup"><span data-stu-id="1728d-118">Type `<InkCanvas/>` between the `<Grid>` tags.</span></span>

   ![Projektant XAML z tagiem InkCanvas](./media/getting-started-with-ink/inkcanvas-xaml.png)

4. <span data-ttu-id="1728d-120">Naciśnij klawisz **F5** , aby uruchomić aplikację w debugerze.</span><span class="sxs-lookup"><span data-stu-id="1728d-120">Press **F5** to launch your application in the debugger.</span></span>

5. <span data-ttu-id="1728d-121">Za pomocą pióra lub myszy Napisz **Hello World** w oknie.</span><span class="sxs-lookup"><span data-stu-id="1728d-121">Using a stylus or mouse, write **hello world** in the window.</span></span>

<span data-ttu-id="1728d-122">Napisano odpowiednik atramentu aplikacji "Hello World" tylko przez 12 naciśnięć klawiszy.</span><span class="sxs-lookup"><span data-stu-id="1728d-122">You've written the ink equivalent of a "hello world" application with only 12 keystrokes!</span></span>

### <a name="spice-up-your-app"></a><span data-ttu-id="1728d-123">Przyprawa do aplikacji</span><span class="sxs-lookup"><span data-stu-id="1728d-123">Spice Up Your App</span></span>

<span data-ttu-id="1728d-124">Skorzystajmy z niektórych funkcji WPF.</span><span class="sxs-lookup"><span data-stu-id="1728d-124">Let’s take advantage of some features of the WPF.</span></span> <span data-ttu-id="1728d-125">Zastąp wszystko między tagiem otwierającym i zamykającym \<> tagów z następującą adiustacją:</span><span class="sxs-lookup"><span data-stu-id="1728d-125">Replace everything between the opening and closing \<Window> tags with the following markup:</span></span>

```xaml
<Page>
  <InkCanvas Name="myInkCanvas" MouseRightButtonUp="RightMouseUpHandler">
    <InkCanvas.Background>
      <LinearGradientBrush>
        <GradientStop Color="Yellow" Offset="0.0" />
          <GradientStop Color="Blue" Offset="0.5" />
            <GradientStop Color="HotPink" Offset="1.0" />
              </LinearGradientBrush>
    </InkCanvas.Background>
  </InkCanvas>
</Page>
```

<span data-ttu-id="1728d-126">Ten kod XAML tworzy tło pędzla gradientu na powierzchni odręcznej.</span><span class="sxs-lookup"><span data-stu-id="1728d-126">This XAML creates a gradient brush background on your inking surface.</span></span>

![Kolory gradientowe na powierzchni odręcznej w aplikacji WPF](./media/getting-started-with-ink/gradient-colors.png)

### <a name="add-some-code-behind-the-xaml"></a><span data-ttu-id="1728d-128">Dodaj kod za kodem XAML</span><span class="sxs-lookup"><span data-stu-id="1728d-128">Add Some Code Behind the XAML</span></span>

<span data-ttu-id="1728d-129">Chociaż XAML ułatwia projektowanie interfejsu użytkownika, dowolna aplikacja rzeczywista musi dodać kod do obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="1728d-129">While XAML makes it very easy to design the user interface, any real-world application needs to add code to handle events.</span></span> <span data-ttu-id="1728d-130">Oto prosty przykład, który powiększa się w odniesieniu do atramentu w odpowiedzi na kliknięcie prawym przyciskiem myszy.</span><span class="sxs-lookup"><span data-stu-id="1728d-130">Here is a simple example that zooms in on the ink in response to a right-click from a mouse.</span></span>

1. <span data-ttu-id="1728d-131">Ustaw procedurę obsługi `MouseRightButtonUp` w kodzie XAML:</span><span class="sxs-lookup"><span data-stu-id="1728d-131">Set the `MouseRightButtonUp` handler in your XAML:</span></span>

   [!code-xaml[DigitalInkTopics#3](~/samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window2.xaml#3)]

1. <span data-ttu-id="1728d-132">W **Eksplorator rozwiązań**rozwiń węzeł MainWindow. XAML i Otwórz plik związany z kodem (MainWindow.XAML.cs lub MainWindow. XAML. vb).</span><span class="sxs-lookup"><span data-stu-id="1728d-132">In **Solution Explorer**, expand MainWindow.xaml and open the code-behind file (MainWindow.xaml.cs or MainWindow.xaml.vb).</span></span> <span data-ttu-id="1728d-133">Dodaj następujący kod procedury obsługi zdarzeń:</span><span class="sxs-lookup"><span data-stu-id="1728d-133">Add the following event handler code:</span></span>

   [!code-csharp[DigitalInkTopics#4](~/samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window2.xaml.cs#4)]
   [!code-vb[DigitalInkTopics#4](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DigitalInkTopics/VisualBasic/Window2.xaml.vb#4)]

1. <span data-ttu-id="1728d-134">Uruchom aplikację.</span><span class="sxs-lookup"><span data-stu-id="1728d-134">Run the application.</span></span> <span data-ttu-id="1728d-135">Dodaj pismo odręczne, a następnie kliknij prawym przyciskiem myszy myszą lub naciśnij odpowiednik pióra.</span><span class="sxs-lookup"><span data-stu-id="1728d-135">Add some ink, and then right-click with the mouse or perform a press-and-hold equivalent with a stylus.</span></span>

   <span data-ttu-id="1728d-136">Widok zostanie powiększony za każdym razem, gdy klikniesz prawym przyciskiem myszy.</span><span class="sxs-lookup"><span data-stu-id="1728d-136">The display zooms in each time you click with the right mouse button.</span></span>

### <a name="use-procedural-code-instead-of-xaml"></a><span data-ttu-id="1728d-137">Użyj kodu proceduralnego zamiast języka XAML</span><span class="sxs-lookup"><span data-stu-id="1728d-137">Use Procedural Code Instead of XAML</span></span>

<span data-ttu-id="1728d-138">Dostęp do wszystkich funkcji WPF można uzyskać z kodu proceduralnego.</span><span class="sxs-lookup"><span data-stu-id="1728d-138">You can access all WPF features from procedural code.</span></span> <span data-ttu-id="1728d-139">Wykonaj następujące kroki, aby utworzyć aplikację "Hello Ink World" dla platformy WPF, która nie korzysta ze wszystkich języków XAML.</span><span class="sxs-lookup"><span data-stu-id="1728d-139">Follow these steps to create a "Hello Ink World" application for WPF that doesn’t use any XAML at all.</span></span>

1. <span data-ttu-id="1728d-140">Utwórz nowy projekt aplikacji konsolowej w programie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="1728d-140">Create a new console application project in Visual Studio.</span></span>

   <span data-ttu-id="1728d-141">W oknie dialogowym **Nowy projekt** rozwiń węzeł **zainstalowana** > **Wizualizacja C#**  lub **Visual Basic** > kategorii **pulpitu systemu Windows** .</span><span class="sxs-lookup"><span data-stu-id="1728d-141">In the **New Project** dialog, expand the **Installed** > **Visual C#** or **Visual Basic** > **Windows Desktop** category.</span></span> <span data-ttu-id="1728d-142">Następnie wybierz szablon aplikacji **Aplikacja konsolowa (.NET Framework)** .</span><span class="sxs-lookup"><span data-stu-id="1728d-142">Then, select the **Console App (.NET Framework)** app template.</span></span> <span data-ttu-id="1728d-143">Wprowadź nazwę, a następnie wybierz przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="1728d-143">Enter a name, and then select **OK**.</span></span>

1. <span data-ttu-id="1728d-144">Wklej następujący kod do pliku Program.cs lub program. vb:</span><span class="sxs-lookup"><span data-stu-id="1728d-144">Paste the following code into the Program.cs or Program.vb file:</span></span>

   [!code-csharp[InkCanvasConsoleApp#1](~/samples/snippets/csharp/VS_Snippets_Wpf/InkCanvasConsoleApp/CSharp/Program.cs#1)]
   [!code-vb[InkCanvasConsoleApp#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/InkCanvasConsoleApp/VisualBasic/Module1.vb#1)]

1. <span data-ttu-id="1728d-145">Dodaj odwołania do zestawów 'Presentationcore, platformie docelowej i 'Windowsbase, klikając prawym przyciskiem myszy pozycję **odwołania** w **Eksplorator rozwiązań** i wybierając pozycję **Dodaj odwołanie**.</span><span class="sxs-lookup"><span data-stu-id="1728d-145">Add references to the PresentationCore, PresentationFramework, and WindowsBase assemblies by right-clicking on **References** in **Solution Explorer** and choosing **Add Reference**.</span></span>

   ![Menedżer odwołań przedstawiający 'Presentationcore i platformie docelowej](./media/getting-started-with-ink/reference-manager-presentationcore-presentationframework.png)

1. <span data-ttu-id="1728d-147">Skompiluj aplikację, naciskając klawisz **F5**.</span><span class="sxs-lookup"><span data-stu-id="1728d-147">Build the application by pressing **F5**.</span></span>

## <a name="see-also"></a><span data-ttu-id="1728d-148">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1728d-148">See also</span></span>

- [<span data-ttu-id="1728d-149">Cyfrowy atrament</span><span class="sxs-lookup"><span data-stu-id="1728d-149">Digital Ink</span></span>](digital-ink.md)
- [<span data-ttu-id="1728d-150">Zbieranie atramentu</span><span class="sxs-lookup"><span data-stu-id="1728d-150">Collecting Ink</span></span>](collecting-ink.md)
- [<span data-ttu-id="1728d-151">Rozpoznawanie pisma odręcznego</span><span class="sxs-lookup"><span data-stu-id="1728d-151">Handwriting Recognition</span></span>](handwriting-recognition.md)
- [<span data-ttu-id="1728d-152">Przechowywanie pisma odręcznego</span><span class="sxs-lookup"><span data-stu-id="1728d-152">Storing Ink</span></span>](storing-ink.md)
