---
title: "Wprowadzenie do użycia atramentu"
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
- procedural code in lieu of XAML [WPF]
- gradient brush [WPF], animating colors of
- XAML [WPF], procedural code in lieu of
- animation [WPF], gradient brush colors
- brushes [WPF], animating colors of
ms.assetid: 760332dd-594a-475d-865b-01659db8cab7
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: dc8ffe9ad68060d9dfbcafe99133a736237a2bb3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="getting-started-with-ink"></a><span data-ttu-id="a9d9a-102">Wprowadzenie do użycia atramentu</span><span class="sxs-lookup"><span data-stu-id="a9d9a-102">Getting Started with Ink</span></span>
<span data-ttu-id="a9d9a-103">Włączenie elektroniczne pismo odręczne aplikacji jest łatwiejsze niż kiedykolwiek.</span><span class="sxs-lookup"><span data-stu-id="a9d9a-103">Incorporating digital ink into your applications is easier than ever.</span></span> <span data-ttu-id="a9d9a-104">Odręczne powstał z jest następstwem COM i formularze systemu Windows metody programowania do osiągnięcia Pełna integracja [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].</span><span class="sxs-lookup"><span data-stu-id="a9d9a-104">Ink has evolved from being a corollary to the COM and Windows Forms method of programming to achieving full integration into the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].</span></span> <span data-ttu-id="a9d9a-105">Nie trzeba zainstalować oddzielne zestawy SDK lub bibliotek środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="a9d9a-105">You do not need to install separate SDKs or runtime libraries.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="a9d9a-106">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="a9d9a-106">Prerequisites</span></span>  
 <span data-ttu-id="a9d9a-107">Aby użyć w poniższych przykładach, należy najpierw zainstalować program Microsoft Visual Studio 2005 i [!INCLUDE[TLA2#tla_winfxsdk](../../../../includes/tla2sharptla-winfxsdk-md.md)].</span><span class="sxs-lookup"><span data-stu-id="a9d9a-107">To use the following examples, you must first install Microsoft Visual Studio 2005 and the [!INCLUDE[TLA2#tla_winfxsdk](../../../../includes/tla2sharptla-winfxsdk-md.md)].</span></span> <span data-ttu-id="a9d9a-108">Należy także zrozumienie sposobu pisania aplikacji dla [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].</span><span class="sxs-lookup"><span data-stu-id="a9d9a-108">You should also understand how to write applications for the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].</span></span> <span data-ttu-id="a9d9a-109">Aby uzyskać więcej informacji na temat rozpoczynania pracy z [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], zobacz [wskazówki: Moje pierwszą aplikację pulpitu WPF](../../../../docs/framework/wpf/getting-started/walkthrough-my-first-wpf-desktop-application.md).</span><span class="sxs-lookup"><span data-stu-id="a9d9a-109">For more information about getting started with the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], see [Walkthrough: My first WPF desktop application](../../../../docs/framework/wpf/getting-started/walkthrough-my-first-wpf-desktop-application.md).</span></span>  
  
## <a name="quick-start"></a><span data-ttu-id="a9d9a-110">Szybki Start</span><span class="sxs-lookup"><span data-stu-id="a9d9a-110">Quick Start</span></span>  
 <span data-ttu-id="a9d9a-111">Ta sekcja pomoże Ci napisać prosty [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacji, która gromadzi odręczne.</span><span class="sxs-lookup"><span data-stu-id="a9d9a-111">This section helps you write a simple [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application that collects ink.</span></span>  
  
 <span data-ttu-id="a9d9a-112">Jeśli jeszcze tego nie zrobiono, zainstaluj program Microsoft Visual Studio 2005 i [!INCLUDE[TLA#tla_winfxsdk](../../../../includes/tlasharptla-winfxsdk-md.md)].</span><span class="sxs-lookup"><span data-stu-id="a9d9a-112">If you haven't already done so, install Microsoft Visual Studio 2005 and the [!INCLUDE[TLA#tla_winfxsdk](../../../../includes/tlasharptla-winfxsdk-md.md)].</span></span> [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<span data-ttu-id="a9d9a-113">aplikacje zazwyczaj muszą być skompilowane zanim będzie możliwe wyświetlenie ich, nawet jeśli ich składać się wyłącznie z [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].</span><span class="sxs-lookup"><span data-stu-id="a9d9a-113"> applications usually must be compiled before you can view them, even if they consist entirely of [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].</span></span> <span data-ttu-id="a9d9a-114">Jednak [!INCLUDE[TLA#tla_winfxsdk](../../../../includes/tlasharptla-winfxsdk-md.md)] obejmuje aplikacji edytor XamlPad, zaprojektowane, aby przyspieszyć proces wdrażania [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]— na podstawie interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="a9d9a-114">However, the [!INCLUDE[TLA#tla_winfxsdk](../../../../includes/tlasharptla-winfxsdk-md.md)] includes an application, XamlPad, designed to speed up the process of implementing a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]-based UI.</span></span> <span data-ttu-id="a9d9a-115">Aby wyświetlić i tinker z pierwszego kilka przykładów w tym dokumencie, można użyć tej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="a9d9a-115">You can use that application to view and tinker with the first few samples in this document.</span></span> <span data-ttu-id="a9d9a-116">Proces tworzenia skompilowanych aplikacji z [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] jest uwzględnione w dalszej części tego dokumentu.</span><span class="sxs-lookup"><span data-stu-id="a9d9a-116">The process of creating compiled applications from [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] is covered later in this document.</span></span>  
  
 <span data-ttu-id="a9d9a-117">Aby uruchomić Edytor XAMLPad, kliknij przycisk **Start** menu wskaż **wszystkie programy**, wskaż polecenie **Microsoft Winndows SDK**, wskaż polecenie **narzędzia**i kliknij przycisk **Edytor XAMLPad**.</span><span class="sxs-lookup"><span data-stu-id="a9d9a-117">To launch XAMLPad, click the **Start** menu, point to **All Programs**, point to **Microsoft Winndows SDK**, point to **Tools**, and click **XAMLPad**.</span></span> <span data-ttu-id="a9d9a-118">W okienku renderowania Edytor XAMLPad renderuje kod XAML, napisany w okienku kodu.</span><span class="sxs-lookup"><span data-stu-id="a9d9a-118">In the rendering pane, XAMLPad renders the XAML code written in the code pane.</span></span> <span data-ttu-id="a9d9a-119">Można edytować kodu XAML, a zmiany są natychmiast widoczne w okienku renderowania.</span><span class="sxs-lookup"><span data-stu-id="a9d9a-119">You can edit the XAML code, and the changes immediately appear in the rendering pane.</span></span>  
  
#### <a name="got-ink"></a><span data-ttu-id="a9d9a-120">Otrzymano odręczne?</span><span class="sxs-lookup"><span data-stu-id="a9d9a-120">Got Ink?</span></span>  
 <span data-ttu-id="a9d9a-121">Aby uruchomić pierwszego [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacji, która obsługuje odręczne:</span><span class="sxs-lookup"><span data-stu-id="a9d9a-121">To start your first [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application that supports ink:</span></span>  
  
1.  <span data-ttu-id="a9d9a-122">Otwórz program Microsoft Visual Studio 2005</span><span class="sxs-lookup"><span data-stu-id="a9d9a-122">Open Microsoft Visual Studio 2005</span></span>  
  
2.  <span data-ttu-id="a9d9a-123">Utwórz nową **aplikacji systemu Windows (WPF)**</span><span class="sxs-lookup"><span data-stu-id="a9d9a-123">Create a new **Windows Application (WPF)**</span></span>  
  
3.  <span data-ttu-id="a9d9a-124">Typ `<InkCanvas/>` między `<Grid>` tagów</span><span class="sxs-lookup"><span data-stu-id="a9d9a-124">Type `<InkCanvas/>` between the `<Grid>` tags</span></span>  
  
4.  <span data-ttu-id="a9d9a-125">Naciśnij klawisz **F5** do uruchamiania aplikacji w debugerze</span><span class="sxs-lookup"><span data-stu-id="a9d9a-125">Press **F5** to launch your application in the debugger</span></span>  
  
5.  <span data-ttu-id="a9d9a-126">Przy użyciu pióro lub mysz, zapisać **Witaj świecie** w oknie</span><span class="sxs-lookup"><span data-stu-id="a9d9a-126">Using a stylus or mouse, write **hello world** in the window</span></span>  
  
 <span data-ttu-id="a9d9a-127">Napisanych odpowiednikiem odręczne aplikacja "hello world" o tylko 12 naciśnięcia klawiszy!</span><span class="sxs-lookup"><span data-stu-id="a9d9a-127">You've written the ink equivalent of a "hello world" application with only 12 keystrokes!</span></span>  
  
#### <a name="spice-up-your-application"></a><span data-ttu-id="a9d9a-128">Przypraw się na aplikację</span><span class="sxs-lookup"><span data-stu-id="a9d9a-128">Spice Up Your Application</span></span>  
 <span data-ttu-id="a9d9a-129">Teraz korzystać z niektórych funkcji [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].</span><span class="sxs-lookup"><span data-stu-id="a9d9a-129">Let’s take advantage of some features of the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].</span></span>  <span data-ttu-id="a9d9a-130">Zastąp wszystko pomiędzy otwierającym \<okna > i zamykanie \</Window > tagów z następujący kod, aby uzyskać pędzla gradientu tła powierzchni pisma odręcznego.</span><span class="sxs-lookup"><span data-stu-id="a9d9a-130">Replace everything between the opening \<Window> and closing \</Window> tags with the following markup to get a gradient brush background on your inking surface.</span></span>  
  
 [!code-xaml[DigitalInkTopics#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window1.xaml#1)]  
[!code-xaml[DigitalInkTopics#1a](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window1.xaml#1a)]  
  
#### <a name="using-animation"></a><span data-ttu-id="a9d9a-131">Przy użyciu animacji</span><span class="sxs-lookup"><span data-stu-id="a9d9a-131">Using Animation</span></span>  
 <span data-ttu-id="a9d9a-132">Dla zabawy umożliwia animować kolory pędzla gradientu.</span><span class="sxs-lookup"><span data-stu-id="a9d9a-132">For fun, let's animate the colors of the gradient brush.</span></span> <span data-ttu-id="a9d9a-133">Dodaj następujące [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] po upływie `</InkCanvas>` tag, ale przed zamknięciem `</Page>` tagu.</span><span class="sxs-lookup"><span data-stu-id="a9d9a-133">Add the following [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] after the closing `</InkCanvas>` tag but before the closing `</Page>` tag.</span></span>  
  
 [!code-xaml[DigitalInkTopics#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window1.xaml#2)]  
  
#### <a name="adding-some-code-behind-the-xaml"></a><span data-ttu-id="a9d9a-134">Dodanie niektórych kodzie XAML</span><span class="sxs-lookup"><span data-stu-id="a9d9a-134">Adding Some Code Behind the XAML</span></span>  
 <span data-ttu-id="a9d9a-135">Gdy XAML ułatwia bardzo Projektowanie interfejsu użytkownika, dowolnej aplikacji rzeczywistych musi Dodaj kod obsługi zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="a9d9a-135">While XAML makes it very easy to design the user interface, any real-world application needs to add code to handle events.</span></span> <span data-ttu-id="a9d9a-136">Poniżej przedstawiono prosty przykład, który powiększa pismo odręczne w odpowiedzi kliknij prawym przyciskiem myszy:</span><span class="sxs-lookup"><span data-stu-id="a9d9a-136">Here is a simple example that zooms in on the ink in response to a right-click from a mouse:</span></span>  
  
 <span data-ttu-id="a9d9a-137">Ustaw `MouseRightButtonUp` obsługi w Twojej [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="a9d9a-137">Set the `MouseRightButtonUp` handler in your [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]:</span></span>  
  
 [!code-xaml[DigitalInkTopics#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window2.xaml#3)]  
  
 <span data-ttu-id="a9d9a-138">W Eksploratorze rozwiązań programu Visual Studio rozwiń Windows1.xaml i Otwórz plik CodeBehind Window1.xaml.cs lub Window1.xaml.vb, jeśli używasz programu Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="a9d9a-138">In Visual Studio’s Solution Explorer, expand Windows1.xaml and open the code-behind file, Window1.xaml.cs or Window1.xaml.vb if you are using Visual Basic.</span></span> <span data-ttu-id="a9d9a-139">Dodaj następujący kod obsługi zdarzenia:</span><span class="sxs-lookup"><span data-stu-id="a9d9a-139">Add the following event handler code:</span></span>  
  
 [!code-csharp[DigitalInkTopics#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window2.xaml.cs#4)]
 [!code-vb[DigitalInkTopics#4](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DigitalInkTopics/VisualBasic/Window2.xaml.vb#4)]  
  
 <span data-ttu-id="a9d9a-140">Teraz uruchom aplikację.</span><span class="sxs-lookup"><span data-stu-id="a9d9a-140">Now, run your application.</span></span> <span data-ttu-id="a9d9a-141">Dodaj część pisma odręcznego, a następnie prawym przyciskiem myszy lub wykonaj odpowiednika naciśnij i przytrzymaj za pomocą pióra.</span><span class="sxs-lookup"><span data-stu-id="a9d9a-141">Add some ink and then right-click with the mouse or perform a press-and-hold equivalent with a stylus.</span></span>  
  
#### <a name="using-procedural-code-instead-of-xaml"></a><span data-ttu-id="a9d9a-142">Przy użyciu kodu procedurach zamiast XAML</span><span class="sxs-lookup"><span data-stu-id="a9d9a-142">Using Procedural Code Instead of XAML</span></span>  
 <span data-ttu-id="a9d9a-143">Dostęp do wszystkich [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] funkcji z kodu procedurach.</span><span class="sxs-lookup"><span data-stu-id="a9d9a-143">You can access all [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] features from procedural code.</span></span> <span data-ttu-id="a9d9a-144">Oto "odręczne aplikacji Hello World" dla [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] który nie używa żadnego [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] wcale.</span><span class="sxs-lookup"><span data-stu-id="a9d9a-144">Here is a "Hello Ink World" application for [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] that doesn’t use any [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] at all.</span></span> <span data-ttu-id="a9d9a-145">Wklej poniższy kod do pustej aplikacji konsoli w programie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="a9d9a-145">Paste the code below into an empty Console Application in Visual Studio.</span></span> <span data-ttu-id="a9d9a-146">Dodaj odwołania do zestawów PresentationCore, PresentationFramework i WindowsBase i skompilować aplikację, naciskając klawisz **F5**:</span><span class="sxs-lookup"><span data-stu-id="a9d9a-146">Add references to the PresentationCore, PresentationFramework, and WindowsBase assemblies, and build the application by pressing **F5**:</span></span>  
  
 [!code-csharp[InkCanvasConsoleApp#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/InkCanvasConsoleApp/CSharp/Program.cs#1)]
 [!code-vb[InkCanvasConsoleApp#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/InkCanvasConsoleApp/VisualBasic/Module1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="a9d9a-147">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a9d9a-147">See Also</span></span>  
 [<span data-ttu-id="a9d9a-148">Elektroniczne pismo odręczne</span><span class="sxs-lookup"><span data-stu-id="a9d9a-148">Digital Ink</span></span>](../../../../docs/framework/wpf/advanced/digital-ink.md)  
 [<span data-ttu-id="a9d9a-149">Zbieranie pisma odręcznego</span><span class="sxs-lookup"><span data-stu-id="a9d9a-149">Collecting Ink</span></span>](../../../../docs/framework/wpf/advanced/collecting-ink.md)  
 [<span data-ttu-id="a9d9a-150">Rozpoznawania pisma ręcznego</span><span class="sxs-lookup"><span data-stu-id="a9d9a-150">Handwriting Recognition</span></span>](../../../../docs/framework/wpf/advanced/handwriting-recognition.md)  
 [<span data-ttu-id="a9d9a-151">Przechowywanie odręcznego</span><span class="sxs-lookup"><span data-stu-id="a9d9a-151">Storing Ink</span></span>](../../../../docs/framework/wpf/advanced/storing-ink.md)
