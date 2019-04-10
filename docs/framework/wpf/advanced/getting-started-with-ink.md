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
ms.openlocfilehash: 4309b1108b2ea96eb298ff3bb876a0f63b80dc32
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59343600"
---
# <a name="get-started-with-ink-in-wpf"></a><span data-ttu-id="f7a14-102">Rozpoczynanie pracy z usługą pisma odręcznego na platformie WPF</span><span class="sxs-lookup"><span data-stu-id="f7a14-102">Get Started with Ink in WPF</span></span>

<span data-ttu-id="f7a14-103">Windows Presentation Foundation (WPF) zawiera funkcję pisma odręcznego, ułatwiająca włączenie cyfrowy atrament w swojej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f7a14-103">Windows Presentation Foundation (WPF) has an ink feature that makes it easy to incorporate digital ink into your app.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="f7a14-104">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="f7a14-104">Prerequisites</span></span>

<span data-ttu-id="f7a14-105">Aby użyć poniższych przykładów, należy najpierw zainstalować [programu Microsoft Visual Studio](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019).</span><span class="sxs-lookup"><span data-stu-id="f7a14-105">To use the following examples, first install [Microsoft Visual Studio](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019).</span></span> <span data-ttu-id="f7a14-106">Pomaga również wiedzieć, jak napisać podstawowych aplikacji WPF.</span><span class="sxs-lookup"><span data-stu-id="f7a14-106">It also helps to know how to write basic WPF apps.</span></span> <span data-ttu-id="f7a14-107">Aby uzyskać pomoc, wprowadzenie do WPF, zobacz [instruktażu: Mój pierwszy aplikacji klasycznej WPF](../getting-started/walkthrough-my-first-wpf-desktop-application.md).</span><span class="sxs-lookup"><span data-stu-id="f7a14-107">For help getting started with WPF, see [Walkthrough: My first WPF desktop application](../getting-started/walkthrough-my-first-wpf-desktop-application.md).</span></span>

## <a name="quick-start"></a><span data-ttu-id="f7a14-108">Przewodnik Szybki Start</span><span class="sxs-lookup"><span data-stu-id="f7a14-108">Quick Start</span></span>

<span data-ttu-id="f7a14-109">Ta sekcja ułatwia pisanie prostą aplikację WPF, która gromadzi pisma odręcznego.</span><span class="sxs-lookup"><span data-stu-id="f7a14-109">This section helps you write a simple WPF application that collects ink.</span></span>

### <a name="got-ink"></a><span data-ttu-id="f7a14-110">Masz pisma odręcznego?</span><span class="sxs-lookup"><span data-stu-id="f7a14-110">Got Ink?</span></span>

<span data-ttu-id="f7a14-111">Aby utworzyć aplikację WPF, która obsługuje pisma odręcznego:</span><span class="sxs-lookup"><span data-stu-id="f7a14-111">To create a WPF app that supports ink:</span></span>

1. <span data-ttu-id="f7a14-112">Otwórz program Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="f7a14-112">Open Visual Studio.</span></span>

2. <span data-ttu-id="f7a14-113">Utwórz nową **aplikacja WPF**.</span><span class="sxs-lookup"><span data-stu-id="f7a14-113">Create a new **WPF App**.</span></span>

   <span data-ttu-id="f7a14-114">W **nowy projekt** okna dialogowego, rozwiń węzeł **zainstalowane** > **Visual C#** lub **języka Visual Basic**  >   **Windows Desktop** kategorii.</span><span class="sxs-lookup"><span data-stu-id="f7a14-114">In the **New Project** dialog, expand the **Installed** > **Visual C#** or **Visual Basic** > **Windows Desktop** category.</span></span> <span data-ttu-id="f7a14-115">Następnie wybierz **aplikacja WPF (.NET Framework)** szablonu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f7a14-115">Then, select the **WPF App (.NET Framework)** app template.</span></span> <span data-ttu-id="f7a14-116">Wprowadź nazwę, a następnie wybierz **OK**.</span><span class="sxs-lookup"><span data-stu-id="f7a14-116">Enter a name, and then select **OK**.</span></span>

   <span data-ttu-id="f7a14-117">Program Visual Studio tworzy projekt, a *MainWindow.xaml* zostanie otwarty w projektancie.</span><span class="sxs-lookup"><span data-stu-id="f7a14-117">Visual Studio creates the project, and *MainWindow.xaml* opens in the designer.</span></span>

3. <span data-ttu-id="f7a14-118">Typ `<InkCanvas/>` między `<Grid>` tagów.</span><span class="sxs-lookup"><span data-stu-id="f7a14-118">Type `<InkCanvas/>` between the `<Grid>` tags.</span></span>

   ![Projektant XAML z tagiem InkCanvas](./media/getting-started-with-ink/inkcanvas-xaml.png)

4. <span data-ttu-id="f7a14-120">Naciśnij klawisz **F5** do uruchomienia aplikacji w debugerze.</span><span class="sxs-lookup"><span data-stu-id="f7a14-120">Press **F5** to launch your application in the debugger.</span></span>

5. <span data-ttu-id="f7a14-121">Za pomocą pióra lub mysz, zapis **Witaj, świecie** w oknie.</span><span class="sxs-lookup"><span data-stu-id="f7a14-121">Using a stylus or mouse, write **hello world** in the window.</span></span>

<span data-ttu-id="f7a14-122">Napisanych pisma odręcznego wielokrotność aplikację "hello world" przy użyciu tylko 12 naciśnięć klawiszy!</span><span class="sxs-lookup"><span data-stu-id="f7a14-122">You've written the ink equivalent of a "hello world" application with only 12 keystrokes!</span></span>

### <a name="spice-up-your-app"></a><span data-ttu-id="f7a14-123">Popraw aplikacji w górę</span><span class="sxs-lookup"><span data-stu-id="f7a14-123">Spice Up Your App</span></span>

<span data-ttu-id="f7a14-124">Przyjrzyjmy się korzystać z niektórych funkcji WPF.</span><span class="sxs-lookup"><span data-stu-id="f7a14-124">Let’s take advantage of some features of the WPF.</span></span> <span data-ttu-id="f7a14-125">Zastąp wszystkie między otwierającym i zamykającym \<okna > Znaczniki następującym kodem:</span><span class="sxs-lookup"><span data-stu-id="f7a14-125">Replace everything between the opening and closing \<Window> tags with the following markup:</span></span>

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

<span data-ttu-id="f7a14-126">Ta XAML tworzy pędzla gradientu tła powierzchni pisma odręcznego.</span><span class="sxs-lookup"><span data-stu-id="f7a14-126">This XAML creates a gradient brush background on your inking surface.</span></span>

![Gradient kolorów na pisma odręcznego narażonego na ataki w aplikacji WPF](./media/getting-started-with-ink/gradient-colors.png)

### <a name="add-some-code-behind-the-xaml"></a><span data-ttu-id="f7a14-128">Dodawanie kodu za XAML</span><span class="sxs-lookup"><span data-stu-id="f7a14-128">Add Some Code Behind the XAML</span></span>

<span data-ttu-id="f7a14-129">Gdy XAML sprawia, że można łatwo projektować interfejs użytkownika, dowolnej aplikacji w rzeczywistych warunkach musi dodać kod do obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="f7a14-129">While XAML makes it very easy to design the user interface, any real-world application needs to add code to handle events.</span></span> <span data-ttu-id="f7a14-130">Poniżej przedstawiono prosty przykład, który powiększa pisma odręcznego w odpowiedzi kliknij prawym przyciskiem myszy z myszy.</span><span class="sxs-lookup"><span data-stu-id="f7a14-130">Here is a simple example that zooms in on the ink in response to a right-click from a mouse.</span></span>

1. <span data-ttu-id="f7a14-131">Ustaw `MouseRightButtonUp` obsługi w swojej XAML:</span><span class="sxs-lookup"><span data-stu-id="f7a14-131">Set the `MouseRightButtonUp` handler in your XAML:</span></span>

   [!code-xaml[DigitalInkTopics#3](~/samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window2.xaml#3)]

1. <span data-ttu-id="f7a14-132">W **Eksploratora rozwiązań**, rozwiń węzeł MainWindow.xaml i Otwórz plik związany z kodem (MainWindow.xaml.cs lub MainWindow.xaml.vb).</span><span class="sxs-lookup"><span data-stu-id="f7a14-132">In **Solution Explorer**, expand MainWindow.xaml and open the code-behind file (MainWindow.xaml.cs or MainWindow.xaml.vb).</span></span> <span data-ttu-id="f7a14-133">Dodaj następujący kod procedury obsługi zdarzeń:</span><span class="sxs-lookup"><span data-stu-id="f7a14-133">Add the following event handler code:</span></span>

   [!code-csharp[DigitalInkTopics#4](~/samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window2.xaml.cs#4)]
   [!code-vb[DigitalInkTopics#4](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DigitalInkTopics/VisualBasic/Window2.xaml.vb#4)]

1. <span data-ttu-id="f7a14-134">Uruchom aplikację.</span><span class="sxs-lookup"><span data-stu-id="f7a14-134">Run the application.</span></span> <span data-ttu-id="f7a14-135">Dodaj część pisma odręcznego, a następnie kliknij prawym przyciskiem myszy, za pomocą myszy lub wykonać odpowiednik naciśnięcie i przytrzymanie za pomocą pióra.</span><span class="sxs-lookup"><span data-stu-id="f7a14-135">Add some ink, and then right-click with the mouse or perform a press-and-hold equivalent with a stylus.</span></span>

   <span data-ttu-id="f7a14-136">Wyświetlanie powiększa za każdym razem, który kliknięto prawym przyciskiem myszy.</span><span class="sxs-lookup"><span data-stu-id="f7a14-136">The display zooms in each time you click with the right mouse button.</span></span>

### <a name="use-procedural-code-instead-of-xaml"></a><span data-ttu-id="f7a14-137">Zamiast kod proceduralny XAML</span><span class="sxs-lookup"><span data-stu-id="f7a14-137">Use Procedural Code Instead of XAML</span></span>

<span data-ttu-id="f7a14-138">Można uzyskać dostęp do wszystkich funkcji środowiska WPF z kodu proceduralnego.</span><span class="sxs-lookup"><span data-stu-id="f7a14-138">You can access all WPF features from procedural code.</span></span> <span data-ttu-id="f7a14-139">Wykonaj następujące kroki, aby utworzyć aplikację "Hello pisma odręcznego World" dla WPF, który nie używa żadnych XAML w ogóle.</span><span class="sxs-lookup"><span data-stu-id="f7a14-139">Follow these steps to create a "Hello Ink World" application for WPF that doesn’t use any XAML at all.</span></span>

1. <span data-ttu-id="f7a14-140">Utwórz nowy projekt aplikacji konsoli w programie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="f7a14-140">Create a new console application project in Visual Studio.</span></span>

   <span data-ttu-id="f7a14-141">W **nowy projekt** okna dialogowego, rozwiń węzeł **zainstalowane** > **Visual C#** lub **języka Visual Basic**  >   **Windows Desktop** kategorii.</span><span class="sxs-lookup"><span data-stu-id="f7a14-141">In the **New Project** dialog, expand the **Installed** > **Visual C#** or **Visual Basic** > **Windows Desktop** category.</span></span> <span data-ttu-id="f7a14-142">Następnie wybierz **Aplikacja konsoli (.NET Framework)** szablonu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f7a14-142">Then, select the **Console App (.NET Framework)** app template.</span></span> <span data-ttu-id="f7a14-143">Wprowadź nazwę, a następnie wybierz **OK**.</span><span class="sxs-lookup"><span data-stu-id="f7a14-143">Enter a name, and then select **OK**.</span></span>

1. <span data-ttu-id="f7a14-144">Wklej następujący kod do pliku Program.cs lub Program.vb:</span><span class="sxs-lookup"><span data-stu-id="f7a14-144">Paste the following code into the Program.cs or Program.vb file:</span></span>

   [!code-csharp[InkCanvasConsoleApp#1](~/samples/snippets/csharp/VS_Snippets_Wpf/InkCanvasConsoleApp/CSharp/Program.cs#1)]
   [!code-vb[InkCanvasConsoleApp#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/InkCanvasConsoleApp/VisualBasic/Module1.vb#1)]

1. <span data-ttu-id="f7a14-145">Dodaj odwołania do zestawów PresentationCore PresentationFramework i WindowsBase, klikając prawym przyciskiem myszy **odwołania** w **Eksploratora rozwiązań** i wybierając pozycję **Dodaj odwołanie**.</span><span class="sxs-lookup"><span data-stu-id="f7a14-145">Add references to the PresentationCore, PresentationFramework, and WindowsBase assemblies by right-clicking on **References** in **Solution Explorer** and choosing **Add Reference**.</span></span>

   ![Menadżer odwołań PresentationCore i PresentationFramework](./media/getting-started-with-ink/references.png)

1. <span data-ttu-id="f7a14-147">Kompiluj aplikację, naciskając klawisz **F5**.</span><span class="sxs-lookup"><span data-stu-id="f7a14-147">Build the application by pressing **F5**.</span></span>

## <a name="see-also"></a><span data-ttu-id="f7a14-148">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f7a14-148">See also</span></span>

- [<span data-ttu-id="f7a14-149">Cyfrowy atrament</span><span class="sxs-lookup"><span data-stu-id="f7a14-149">Digital Ink</span></span>](digital-ink.md)
- [<span data-ttu-id="f7a14-150">Zbieranie atramentu</span><span class="sxs-lookup"><span data-stu-id="f7a14-150">Collecting Ink</span></span>](collecting-ink.md)
- [<span data-ttu-id="f7a14-151">Rozpoznawanie pisma</span><span class="sxs-lookup"><span data-stu-id="f7a14-151">Handwriting Recognition</span></span>](handwriting-recognition.md)
- [<span data-ttu-id="f7a14-152">Przechowywanie atramentu</span><span class="sxs-lookup"><span data-stu-id="f7a14-152">Storing Ink</span></span>](storing-ink.md)
