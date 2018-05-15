---
title: 'Wskazówki: włączanie przeciągania i upuszczania w kontrolce użytkownika'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- walkthrough [WPF], drag-and-drop
- drag-and-drop [WPF], walkthrough
ms.assetid: cc844419-1a77-4906-95d9-060d79107fc7
ms.openlocfilehash: e4dba856b973f1210f2d088de3ed8ae5df2c6988
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="walkthrough-enabling-drag-and-drop-on-a-user-control"></a><span data-ttu-id="fcea6-102">Wskazówki: włączanie przeciągania i upuszczania w kontrolce użytkownika</span><span class="sxs-lookup"><span data-stu-id="fcea6-102">Walkthrough: Enabling Drag and Drop on a User Control</span></span>
<span data-ttu-id="fcea6-103">Ten przewodnik przedstawia sposób tworzenia formant użytkownika niestandardowego, który mogą uczestniczyć w transferu danych przeciągania i upuszczania [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)].</span><span class="sxs-lookup"><span data-stu-id="fcea6-103">This walkthrough demonstrates how to create a custom user control that can participate in drag-and-drop data transfer in [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)].</span></span>  
  
 <span data-ttu-id="fcea6-104">W tym przewodniku spowoduje utworzenie niestandardowych WPF <xref:System.Windows.Controls.UserControl> reprezentujący okrągłego kształtu.</span><span class="sxs-lookup"><span data-stu-id="fcea6-104">In this walkthrough, you will create a custom WPF <xref:System.Windows.Controls.UserControl> that represents a circle shape.</span></span> <span data-ttu-id="fcea6-105">Funkcje zostaną zaimplementowane w formancie umożliwia transfer danych za pośrednictwem przeciągania i upuszczania.</span><span class="sxs-lookup"><span data-stu-id="fcea6-105">You will implement functionality on the control to enable data transfer through drag-and-drop.</span></span> <span data-ttu-id="fcea6-106">Na przykład jeśli przeciąganie z jednego formantu okrąg na inny dane koloru wypełnienia zostanie skopiowana ze źródła koło z obiektem docelowym.</span><span class="sxs-lookup"><span data-stu-id="fcea6-106">For example, if you drag from one Circle control to another, the Fill color data is copied from the source Circle to the target.</span></span> <span data-ttu-id="fcea6-107">Jeśli zostanie przeciągnięty za pomocą formantu okręgu do <xref:System.Windows.Controls.TextBox>, reprezentację ciągu kolor wypełnienia jest kopiowany do <xref:System.Windows.Controls.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="fcea6-107">If you drag from a Circle control to a <xref:System.Windows.Controls.TextBox>, the string representation of the Fill color is copied to the <xref:System.Windows.Controls.TextBox>.</span></span> <span data-ttu-id="fcea6-108">Zostanie również utworzona mała aplikacji, która zawiera dwa formanty panelu i <xref:System.Windows.Controls.TextBox> Aby przetestować funkcje przeciągania i upuszczania.</span><span class="sxs-lookup"><span data-stu-id="fcea6-108">You will also create a small application that contains two panel controls and a <xref:System.Windows.Controls.TextBox> to test the drag-and-drop functionality.</span></span> <span data-ttu-id="fcea6-109">Napiszesz kod, który umożliwia paneli do przetworzenia porzuconych danych koło, co umożliwi przenosić i kopiować okręgi z kolekcji Children elementu panel jednego do drugiego.</span><span class="sxs-lookup"><span data-stu-id="fcea6-109">You will write code that enables the panels to process dropped Circle data, which will enable you to move or copy Circles from the Children collection of one panel to the other.</span></span>  
  
 <span data-ttu-id="fcea6-110">W instruktażu przedstawiono następujące zagadnienia:</span><span class="sxs-lookup"><span data-stu-id="fcea6-110">This walkthrough illustrates the following tasks:</span></span>  
  
-   <span data-ttu-id="fcea6-111">Tworzenie formantu użytkownika niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="fcea6-111">Create a custom user control.</span></span>  
  
-   <span data-ttu-id="fcea6-112">Kontrola użytkownika jako źródła przeciągania.</span><span class="sxs-lookup"><span data-stu-id="fcea6-112">Enable the user control to be a drag source.</span></span>  
  
-   <span data-ttu-id="fcea6-113">Kontrola użytkownika jako miejsca docelowego.</span><span class="sxs-lookup"><span data-stu-id="fcea6-113">Enable the user control to be a drop target.</span></span>  
  
-   <span data-ttu-id="fcea6-114">Włącz panelu na odbieranie danych z kontrolki użytkownika.</span><span class="sxs-lookup"><span data-stu-id="fcea6-114">Enable a panel to receive data dropped from the user control.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="fcea6-115">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="fcea6-115">Prerequisites</span></span>  
 <span data-ttu-id="fcea6-116">Następujące składniki są wymagane do przeprowadzenia tego instruktażu:</span><span class="sxs-lookup"><span data-stu-id="fcea6-116">You need the following components to complete this walkthrough:</span></span>  
  
-   <span data-ttu-id="fcea6-117">Visual Studio 2010</span><span class="sxs-lookup"><span data-stu-id="fcea6-117">Visual Studio 2010</span></span>  
  
## <a name="creating-the-application-project"></a><span data-ttu-id="fcea6-118">Tworzenie projektu aplikacji</span><span class="sxs-lookup"><span data-stu-id="fcea6-118">Creating the Application Project</span></span>  
 <span data-ttu-id="fcea6-119">W tej sekcji utworzysz infrastruktury aplikacji, w tym strony głównej z dwa panele i <xref:System.Windows.Controls.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="fcea6-119">In this section, you will create the application infrastructure, which includes a main page with two panels and a <xref:System.Windows.Controls.TextBox>.</span></span>  
  
### <a name="to-create-the-project"></a><span data-ttu-id="fcea6-120">Aby utworzyć projekt</span><span class="sxs-lookup"><span data-stu-id="fcea6-120">To create the project</span></span>  
  
1.  <span data-ttu-id="fcea6-121">Utwórz nowy projekt aplikacji WPF w języku Visual Basic lub Visual C# o nazwie `DragDropExample`.</span><span class="sxs-lookup"><span data-stu-id="fcea6-121">Create a new WPF Application project in Visual Basic or Visual C# named `DragDropExample`.</span></span> <span data-ttu-id="fcea6-122">Aby uzyskać więcej informacji, zobacz [porady: Tworzenie nowego projektu aplikacji WPF](http://msdn.microsoft.com/library/1f6aea7a-33e1-4d3f-8555-1daa42e95d82).</span><span class="sxs-lookup"><span data-stu-id="fcea6-122">For more information, see [How to: Create a New WPF Application Project](http://msdn.microsoft.com/library/1f6aea7a-33e1-4d3f-8555-1daa42e95d82).</span></span>  
  
2.  <span data-ttu-id="fcea6-123">Open MainWindow.xaml.</span><span class="sxs-lookup"><span data-stu-id="fcea6-123">Open MainWindow.xaml.</span></span>  
  
3.  <span data-ttu-id="fcea6-124">Dodaj następujący kod między otwarcia i zamknięcia <xref:System.Windows.Controls.Grid> tagów.</span><span class="sxs-lookup"><span data-stu-id="fcea6-124">Add the following markup between the opening and closing <xref:System.Windows.Controls.Grid> tags.</span></span>  
  
     <span data-ttu-id="fcea6-125">Ten kod znaczników tworzy interfejsu użytkownika dla aplikacji testu.</span><span class="sxs-lookup"><span data-stu-id="fcea6-125">This markup creates the user interface for the test application.</span></span>  
  
     [!code-xaml[DragDropWalkthrough#PanelsStep1XAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/SnippetWindow.xaml#panelsstep1xaml)]  
  
## <a name="adding-a-new-user-control-to-the-project"></a><span data-ttu-id="fcea6-126">Dodawanie nowej kontrolki użytkownika do projektu</span><span class="sxs-lookup"><span data-stu-id="fcea6-126">Adding a New User Control to the Project</span></span>  
 <span data-ttu-id="fcea6-127">W tej sekcji nową kontrolkę użytkownika zostaną dodane do projektu.</span><span class="sxs-lookup"><span data-stu-id="fcea6-127">In this section, you will add a new user control to the project.</span></span>  
  
### <a name="to-add-a-new-user-control"></a><span data-ttu-id="fcea6-128">Aby dodać nową kontrolkę użytkownika</span><span class="sxs-lookup"><span data-stu-id="fcea6-128">To add a new user control</span></span>  
  
1.  <span data-ttu-id="fcea6-129">W menu Projekt wybierz **Dodaj kontrolkę użytkownika**.</span><span class="sxs-lookup"><span data-stu-id="fcea6-129">On the Project menu, select **Add User Control**.</span></span>  
  
2.  <span data-ttu-id="fcea6-130">W oknie dialogowym Dodawanie nowego elementu, Zmień nazwę, aby `Circle.xaml`i kliknij przycisk **Dodaj**.</span><span class="sxs-lookup"><span data-stu-id="fcea6-130">In the Add New Item dialog box, change the name to `Circle.xaml`, and click **Add**.</span></span>  
  
     <span data-ttu-id="fcea6-131">Circle.XAML i jej kodem jest dodane do projektu.</span><span class="sxs-lookup"><span data-stu-id="fcea6-131">Circle.xaml and its code-behind is added to the project.</span></span>  
  
3.  <span data-ttu-id="fcea6-132">Open Circle.xaml.</span><span class="sxs-lookup"><span data-stu-id="fcea6-132">Open Circle.xaml.</span></span>  
  
     <span data-ttu-id="fcea6-133">Ten plik zawiera elementy interfejsu użytkownika kontrolki użytkownika.</span><span class="sxs-lookup"><span data-stu-id="fcea6-133">This file will contain the user interface elements of the user control.</span></span>  
  
4.  <span data-ttu-id="fcea6-134">Dodaj następujący kod do katalogu głównego <xref:System.Windows.Controls.Grid> można utworzyć formantu proste użytkownika, który ma niebieskie koło jako jego interfejsie użytkownika.</span><span class="sxs-lookup"><span data-stu-id="fcea6-134">Add the following markup to the root <xref:System.Windows.Controls.Grid> to create a simple user control that has a blue circle as its UI.</span></span>  
  
     [!code-xaml[DragDropWalkthrough#EllipseXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml#ellipsexaml)]  
  
5.  <span data-ttu-id="fcea6-135">Otwórz Circle.xaml.cs lub Circle.xaml.vb.</span><span class="sxs-lookup"><span data-stu-id="fcea6-135">Open Circle.xaml.cs or Circle.xaml.vb.</span></span>  
  
6.  <span data-ttu-id="fcea6-136">W języku C# Dodaj następujący kod po można utworzyć konstruktora kopiującego konstruktora domyślnego.</span><span class="sxs-lookup"><span data-stu-id="fcea6-136">In C#, add the following code after the default constructor to create a copy constructor.</span></span> <span data-ttu-id="fcea6-137">W języku Visual Basic Dodaj następujący kod do utworzenia zarówno konstruktora domyślnego i Konstruktor kopiujący.</span><span class="sxs-lookup"><span data-stu-id="fcea6-137">In Visual Basic, add the following code to create both a default constructor and a copy constructor.</span></span>  
  
     <span data-ttu-id="fcea6-138">Aby umożliwić kontrolki użytkownika do skopiowania, należy dodać metody konstruktora kopiowania pliku CodeBehind.</span><span class="sxs-lookup"><span data-stu-id="fcea6-138">In order to allow the user control to be copied, you add a copy constructor method in the code-behind file.</span></span> <span data-ttu-id="fcea6-139">W formancie użytkownika koło uproszczony spowoduje tylko skopiowanie wypełnienia i rozmiar kontrolki użytkownika.</span><span class="sxs-lookup"><span data-stu-id="fcea6-139">In the simplified Circle user control, you will only copy the Fill and the size of the of the user control.</span></span>  
  
     [!code-csharp[DragDropWalkthrough#CopyCtor](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#copyctor)]
     [!code-vb[DragDropWalkthrough#CopyCtor](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#copyctor)]  
  
### <a name="to-add-the-user-control-to-the-main-window"></a><span data-ttu-id="fcea6-140">Aby dodać kontrolkę użytkownika do głównego okna</span><span class="sxs-lookup"><span data-stu-id="fcea6-140">To add the user control to the main window</span></span>  
  
1.  <span data-ttu-id="fcea6-141">Open MainWindow.xaml.</span><span class="sxs-lookup"><span data-stu-id="fcea6-141">Open MainWindow.xaml.</span></span>  
  
2.  <span data-ttu-id="fcea6-142">Dodaj następujące XAML do otwarcia <xref:System.Windows.Window> tag, aby utworzyć odwołanie do przestrzeni nazw XML dla bieżącej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="fcea6-142">Add the following XAML to the opening <xref:System.Windows.Window> tag to create an XML namespace reference to the current application.</span></span>  
  
    ```  
    xmlns:local="clr-namespace:DragDropExample"  
    ```  
  
3.  <span data-ttu-id="fcea6-143">W pierwszym <xref:System.Windows.Controls.StackPanel>, Dodaj następujące XAML, aby utworzyć dwa wystąpienia kontrolki użytkownika koło w pierwszym panelu.</span><span class="sxs-lookup"><span data-stu-id="fcea6-143">In the first <xref:System.Windows.Controls.StackPanel>, add the following XAML to create two instances of the Circle user control in the first panel.</span></span>  
  
     [!code-xaml[DragDropWalkthrough#CirclesXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/SnippetWindow.xaml#circlesxaml)]  
  
     <span data-ttu-id="fcea6-144">Pełna XAML panelu wygląda następująco.</span><span class="sxs-lookup"><span data-stu-id="fcea6-144">The full XAML for the panel looks like the following.</span></span>  
  
     [!code-xaml[DragDropWalkthrough#PanelsStep2XAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/SnippetWindow.xaml#panelsstep2xaml)]  
  
## <a name="implementing-drag-source-events-in-the-user-control"></a><span data-ttu-id="fcea6-145">Implementowanie zdarzeń źródła przeciągania w formancie użytkownika</span><span class="sxs-lookup"><span data-stu-id="fcea6-145">Implementing Drag Source Events in the User Control</span></span>  
 <span data-ttu-id="fcea6-146">W tej sekcji zostanie zastąpione <xref:System.Windows.UIElement.OnMouseMove%2A> — metoda i Inicjowanie operacji przeciągania i upuszczania.</span><span class="sxs-lookup"><span data-stu-id="fcea6-146">In this section, you will override the <xref:System.Windows.UIElement.OnMouseMove%2A> method and initiate the drag-and-drop operation.</span></span>  
  
 <span data-ttu-id="fcea6-147">Po uruchomieniu przeciągnij (przycisk myszy jest wciśnięty i wskaźnik myszy zostanie przesunięty), będzie pakiet danych ma zostać przesłany do <xref:System.Windows.DataObject>.</span><span class="sxs-lookup"><span data-stu-id="fcea6-147">If a drag is started (a mouse button is pressed and the mouse is moved), you will package the data to be transferred into a <xref:System.Windows.DataObject>.</span></span> <span data-ttu-id="fcea6-148">W takim przypadku sterowania koło będzie pakietu trzy elementy danych; Reprezentacja ciągu jego kolor wypełnienia, podwójnej reprezentacji wysokości i swoją kopię.</span><span class="sxs-lookup"><span data-stu-id="fcea6-148">In this case, the Circle control will package three data items; a string representation of its Fill color, a double representation of its height, and a copy of itself.</span></span>  
  
### <a name="to-initiate-a-drag-and-drop-operation"></a><span data-ttu-id="fcea6-149">Aby zainicjować operacji przeciągania i upuszczania</span><span class="sxs-lookup"><span data-stu-id="fcea6-149">To initiate a drag-and-drop operation</span></span>  
  
1.  <span data-ttu-id="fcea6-150">Otwórz Circle.xaml.cs lub Circle.xaml.vb.</span><span class="sxs-lookup"><span data-stu-id="fcea6-150">Open Circle.xaml.cs or Circle.xaml.vb.</span></span>  
  
2.  <span data-ttu-id="fcea6-151">Dodaj następujące <xref:System.Windows.UIElement.OnMouseMove%2A> zastąpienie w celu zapewnienia obsługi dla klasy <xref:System.Windows.UIElement.MouseMove> zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="fcea6-151">Add the following <xref:System.Windows.UIElement.OnMouseMove%2A> override to provide class handling for the <xref:System.Windows.UIElement.MouseMove> event.</span></span>  
  
     [!code-csharp[DragDropWalkthrough#OnMouseMove](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#onmousemove)]
     [!code-vb[DragDropWalkthrough#OnMouseMove](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#onmousemove)]  
  
     <span data-ttu-id="fcea6-152">To <xref:System.Windows.UIElement.OnMouseMove%2A> zastąpienie wykonuje następujące zadania:</span><span class="sxs-lookup"><span data-stu-id="fcea6-152">This <xref:System.Windows.UIElement.OnMouseMove%2A> override performs the following tasks:</span></span>  
  
    -   <span data-ttu-id="fcea6-153">Sprawdza, czy naciśnięciu lewego przycisku myszy, gdy wskaźnik myszy porusza się.</span><span class="sxs-lookup"><span data-stu-id="fcea6-153">Checks whether the left mouse button is pressed while the mouse is moving.</span></span>  
  
    -   <span data-ttu-id="fcea6-154">Pakiety danych okręgu do <xref:System.Windows.DataObject>.</span><span class="sxs-lookup"><span data-stu-id="fcea6-154">Packages the Circle data into a <xref:System.Windows.DataObject>.</span></span> <span data-ttu-id="fcea6-155">W takim przypadku sterowania koło pakietów trzy elementy danych; Reprezentacja ciągu jego kolor wypełnienia, podwójnej reprezentacji wysokości i swoją kopię.</span><span class="sxs-lookup"><span data-stu-id="fcea6-155">In this case, the Circle control packages three data items; a string representation of its Fill color, a double representation of its height, and a copy of itself.</span></span>  
  
    -   <span data-ttu-id="fcea6-156">Wywołuje statycznych <xref:System.Windows.DragDrop.DoDragDrop%2A?displayProperty=nameWithType> metodę, aby zainicjować operację przeciągania i upuszczania.</span><span class="sxs-lookup"><span data-stu-id="fcea6-156">Calls the static <xref:System.Windows.DragDrop.DoDragDrop%2A?displayProperty=nameWithType> method to initiate the drag-and-drop operation.</span></span> <span data-ttu-id="fcea6-157">Następujące trzy parametry do przekazania <xref:System.Windows.DragDrop.DoDragDrop%2A> metody:</span><span class="sxs-lookup"><span data-stu-id="fcea6-157">You pass the following three parameters to the <xref:System.Windows.DragDrop.DoDragDrop%2A> method:</span></span>  
  
        -   <span data-ttu-id="fcea6-158">`dragSource` — Odwołanie do tego formantu.</span><span class="sxs-lookup"><span data-stu-id="fcea6-158">`dragSource` – A reference to this control.</span></span>  
  
        -   <span data-ttu-id="fcea6-159">`data` — <xref:System.Windows.DataObject> Utworzony w poprzednim kodzie.</span><span class="sxs-lookup"><span data-stu-id="fcea6-159">`data` – The <xref:System.Windows.DataObject> created in the previous code.</span></span>  
  
        -   <span data-ttu-id="fcea6-160">`allowedEffects` Dozwolonych operacji przeciągania i upuszczania, które są <xref:System.Windows.DragDropEffects.Copy> lub <xref:System.Windows.DragDropEffects.Move>.</span><span class="sxs-lookup"><span data-stu-id="fcea6-160">`allowedEffects` – The allowed drag-and-drop operations, which are <xref:System.Windows.DragDropEffects.Copy> or <xref:System.Windows.DragDropEffects.Move>.</span></span>  
  
3.  <span data-ttu-id="fcea6-161">Naciśnij klawisz F5, aby skompilować i uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="fcea6-161">Press F5 to build and run the application.</span></span>  
  
4.  <span data-ttu-id="fcea6-162">Formantów koło kliknij i przeciągnij go za pośrednictwem panele innych okręgu i <xref:System.Windows.Controls.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="fcea6-162">Click one of the Circle controls and drag it over the panels, the other Circle, and the <xref:System.Windows.Controls.TextBox>.</span></span> <span data-ttu-id="fcea6-163">Podczas przeciągania za pośrednictwem <xref:System.Windows.Controls.TextBox>, oznaczać przenoszenie zmiany kursora.</span><span class="sxs-lookup"><span data-stu-id="fcea6-163">When dragging over the <xref:System.Windows.Controls.TextBox>, the cursor changes to indicate a move.</span></span>  
  
5.  <span data-ttu-id="fcea6-164">Podczas przeciągania koło za pośrednictwem <xref:System.Windows.Controls.TextBox>, naciśnij klawisz CTRL.</span><span class="sxs-lookup"><span data-stu-id="fcea6-164">While dragging a Circle over the <xref:System.Windows.Controls.TextBox>, press the CTRL key.</span></span> <span data-ttu-id="fcea6-165">Zwróć uwagę, jak kursor zmienia się na wskazać kopię.</span><span class="sxs-lookup"><span data-stu-id="fcea6-165">Notice how the cursor changes to indicate a copy.</span></span>  
  
6.  <span data-ttu-id="fcea6-166">Przeciągnij i upuść okrąg na <xref:System.Windows.Controls.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="fcea6-166">Drag and drop a Circle onto the <xref:System.Windows.Controls.TextBox>.</span></span> <span data-ttu-id="fcea6-167">Kolor wypełnienia koła reprezentację ciągu jest dołączany do <xref:System.Windows.Controls.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="fcea6-167">The string representation of the Circle’s fill color is appended to the <xref:System.Windows.Controls.TextBox>.</span></span>  
  
     <span data-ttu-id="fcea6-168">![Ciąg reprezentację kolor wypełnienia okręgu](../../../../docs/framework/wpf/advanced/media/dragdrop-colorstring.png "DragDrop_ColorString")</span><span class="sxs-lookup"><span data-stu-id="fcea6-168">![String representation of Circle's fill color](../../../../docs/framework/wpf/advanced/media/dragdrop-colorstring.png "DragDrop_ColorString")</span></span>  
  
 <span data-ttu-id="fcea6-169">Domyślnie gdy kursor zmieni się podczas operacji przeciągania i upuszczania, aby wskazać, będą miały wpływ, jaki usunięcie danych.</span><span class="sxs-lookup"><span data-stu-id="fcea6-169">By default, the cursor will change during a drag-and-drop operation to indicate what effect dropping the data will have.</span></span> <span data-ttu-id="fcea6-170">Można dostosować zwrotnych użytkownikowi Obsługa <xref:System.Windows.UIElement.GiveFeedback> zdarzeń i ustawienie różnych kursora.</span><span class="sxs-lookup"><span data-stu-id="fcea6-170">You can customize the feedback given to the user by handling the <xref:System.Windows.UIElement.GiveFeedback> event and setting a different cursor.</span></span>  
  
### <a name="to-give-feedback-to-the-user"></a><span data-ttu-id="fcea6-171">Aby przekazać opinię do użytkownika</span><span class="sxs-lookup"><span data-stu-id="fcea6-171">To give feedback to the user</span></span>  
  
1.  <span data-ttu-id="fcea6-172">Otwórz Circle.xaml.cs lub Circle.xaml.vb.</span><span class="sxs-lookup"><span data-stu-id="fcea6-172">Open Circle.xaml.cs or Circle.xaml.vb.</span></span>  
  
2.  <span data-ttu-id="fcea6-173">Dodaj następujące <xref:System.Windows.UIElement.OnGiveFeedback%2A> zastąpienie w celu zapewnienia obsługi dla klasy <xref:System.Windows.UIElement.GiveFeedback> zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="fcea6-173">Add the following <xref:System.Windows.UIElement.OnGiveFeedback%2A> override to provide class handling for the <xref:System.Windows.UIElement.GiveFeedback> event.</span></span>  
  
     [!code-csharp[DragDropWalkthrough#OnGiveFeedback](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#ongivefeedback)]
     [!code-vb[DragDropWalkthrough#OnGiveFeedback](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#ongivefeedback)]  
  
     <span data-ttu-id="fcea6-174">To <xref:System.Windows.UIElement.OnGiveFeedback%2A> zastąpienie wykonuje następujące zadania:</span><span class="sxs-lookup"><span data-stu-id="fcea6-174">This <xref:System.Windows.UIElement.OnGiveFeedback%2A> override performs the following tasks:</span></span>  
  
    -   <span data-ttu-id="fcea6-175">Sprawdza <xref:System.Windows.GiveFeedbackEventArgs.Effects%2A> wartości, które są ustawiane w celu upuszczania <xref:System.Windows.UIElement.DragOver> obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="fcea6-175">Checks the <xref:System.Windows.GiveFeedbackEventArgs.Effects%2A> values that are set in the drop target's <xref:System.Windows.UIElement.DragOver> event handler.</span></span>  
  
    -   <span data-ttu-id="fcea6-176">Ustawia kursor niestandardowych, na podstawie <xref:System.Windows.GiveFeedbackEventArgs.Effects%2A> wartości.</span><span class="sxs-lookup"><span data-stu-id="fcea6-176">Sets a custom cursor based on the <xref:System.Windows.GiveFeedbackEventArgs.Effects%2A> value.</span></span> <span data-ttu-id="fcea6-177">Kursor ma umożliwić wizualne dla użytkownika o będą miały wpływ, jaki usunięcie danych.</span><span class="sxs-lookup"><span data-stu-id="fcea6-177">The cursor is intended to give visual feedback to the user about what effect dropping the data will have.</span></span>  
  
3.  <span data-ttu-id="fcea6-178">Naciśnij klawisz F5, aby skompilować i uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="fcea6-178">Press F5 to build and run the application.</span></span>  
  
4.  <span data-ttu-id="fcea6-179">Przeciągnij jeden okręgu kontroluje za pośrednictwem panele innych okręgu i <xref:System.Windows.Controls.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="fcea6-179">Drag one of the Circle controls over the panels, the other Circle, and the <xref:System.Windows.Controls.TextBox>.</span></span> <span data-ttu-id="fcea6-180">Kursory są teraz niestandardowych kursorów, które zostały określone w <xref:System.Windows.UIElement.OnGiveFeedback%2A> zastąpienia.</span><span class="sxs-lookup"><span data-stu-id="fcea6-180">Notice that the cursors are now the custom cursors that you specified in the <xref:System.Windows.UIElement.OnGiveFeedback%2A> override.</span></span>  
  
     <span data-ttu-id="fcea6-181">![Przeciągnij i upuść z niestandardowych kursorów](../../../../docs/framework/wpf/advanced/media/dragdrop-customcursor.png "DragDrop_CustomCursor")</span><span class="sxs-lookup"><span data-stu-id="fcea6-181">![Drag and drop with custom cursors](../../../../docs/framework/wpf/advanced/media/dragdrop-customcursor.png "DragDrop_CustomCursor")</span></span>  
  
5.  <span data-ttu-id="fcea6-182">Zaznacz tekst `green` z <xref:System.Windows.Controls.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="fcea6-182">Select the text `green` from the <xref:System.Windows.Controls.TextBox>.</span></span>  
  
6.  <span data-ttu-id="fcea6-183">Przeciągnij `green` tekst formantu okręgu.</span><span class="sxs-lookup"><span data-stu-id="fcea6-183">Drag the `green` text to a Circle control.</span></span> <span data-ttu-id="fcea6-184">Należy zauważyć, że kursory domyślne są wyświetlane, aby wskazać skutków operacji przeciągania i upuszczania.</span><span class="sxs-lookup"><span data-stu-id="fcea6-184">Notice that the default cursors are shown to indicate the effects of the drag-and-drop operation.</span></span> <span data-ttu-id="fcea6-185">Kursor opinii ma zawsze wartość źródła przeciągania.</span><span class="sxs-lookup"><span data-stu-id="fcea6-185">The feedback cursor is always set by the drag source.</span></span>  
  
## <a name="implementing-drop-target-events-in-the-user-control"></a><span data-ttu-id="fcea6-186">Implementowanie docelowego upuszczania w formancie użytkownika</span><span class="sxs-lookup"><span data-stu-id="fcea6-186">Implementing Drop Target Events in the User Control</span></span>  
 <span data-ttu-id="fcea6-187">W tej sekcji zostanie Określ, czy kontrolka użytkownika jest element docelowy upuszczania zastąpienie metody, które umożliwiają użytkownikowi do miejsca docelowego można kontrolować i przetwarzania danych, które są przenoszone na nim.</span><span class="sxs-lookup"><span data-stu-id="fcea6-187">In this section, you will specify that the user control is a drop target, override the methods that enable the user control to be a drop target, and process the data that is dropped on it.</span></span>  
  
### <a name="to-enable-the-user-control-to-be-a-drop-target"></a><span data-ttu-id="fcea6-188">Aby włączyć kontrolę użytkownika jako miejsca docelowego</span><span class="sxs-lookup"><span data-stu-id="fcea6-188">To enable the user control to be a drop target</span></span>  
  
1.  <span data-ttu-id="fcea6-189">Open Circle.xaml.</span><span class="sxs-lookup"><span data-stu-id="fcea6-189">Open Circle.xaml.</span></span>  
  
2.  <span data-ttu-id="fcea6-190">W otwarcia <xref:System.Windows.Controls.UserControl> tagów, Dodaj <xref:System.Windows.UIElement.AllowDrop%2A> właściwości i wartości `true`.</span><span class="sxs-lookup"><span data-stu-id="fcea6-190">In the opening <xref:System.Windows.Controls.UserControl> tag, add the <xref:System.Windows.UIElement.AllowDrop%2A> property and set it to `true`.</span></span>  
  
     [!code-xaml[DragDropWalkthrough#UCTagXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml#uctagxaml)]  
  
 <span data-ttu-id="fcea6-191"><xref:System.Windows.UIElement.OnDrop%2A> Metoda jest wywoływana, gdy <xref:System.Windows.UIElement.AllowDrop%2A> właściwość jest ustawiona na `true` i kontrola użytkownika koło jest upuszczony danych ze źródła przeciągania.</span><span class="sxs-lookup"><span data-stu-id="fcea6-191">The <xref:System.Windows.UIElement.OnDrop%2A> method is called when the <xref:System.Windows.UIElement.AllowDrop%2A> property is set to `true` and data from the drag source is dropped on the Circle user control.</span></span> <span data-ttu-id="fcea6-192">W przypadku tej metody możesz przetwarzania danych, która została usunięta i dotyczą danych okręgu.</span><span class="sxs-lookup"><span data-stu-id="fcea6-192">In this method, you will process the data that was dropped and apply the data to the Circle.</span></span>  
  
### <a name="to-process-the-dropped-data"></a><span data-ttu-id="fcea6-193">Do przetwarzania danych porzuconych</span><span class="sxs-lookup"><span data-stu-id="fcea6-193">To process the dropped data</span></span>  
  
1.  <span data-ttu-id="fcea6-194">Otwórz Circle.xaml.cs lub Circle.xaml.vb.</span><span class="sxs-lookup"><span data-stu-id="fcea6-194">Open Circle.xaml.cs or Circle.xaml.vb.</span></span>  
  
2.  <span data-ttu-id="fcea6-195">Dodaj następujące <xref:System.Windows.UIElement.OnDrop%2A> zastąpienie w celu zapewnienia obsługi dla klasy <xref:System.Windows.UIElement.Drop> zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="fcea6-195">Add the following <xref:System.Windows.UIElement.OnDrop%2A> override to provide class handling for the <xref:System.Windows.UIElement.Drop> event.</span></span>  
  
     [!code-csharp[DragDropWalkthrough#OnDrop](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#ondrop)]
     [!code-vb[DragDropWalkthrough#OnDrop](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#ondrop)]  
  
     <span data-ttu-id="fcea6-196">To <xref:System.Windows.UIElement.OnDrop%2A> zastąpienie wykonuje następujące zadania:</span><span class="sxs-lookup"><span data-stu-id="fcea6-196">This <xref:System.Windows.UIElement.OnDrop%2A> override performs the following tasks:</span></span>  
  
    -   <span data-ttu-id="fcea6-197">Używa <xref:System.Windows.DataObject.GetDataPresent%2A> metodę sprawdzania, czy dane przeciągane zawiera obiekt ciągu.</span><span class="sxs-lookup"><span data-stu-id="fcea6-197">Uses the <xref:System.Windows.DataObject.GetDataPresent%2A> method to check if the dragged data contains a string object.</span></span>  
  
    -   <span data-ttu-id="fcea6-198">Używa <xref:System.Windows.DataObject.GetData%2A> metodę, aby wyodrębnić dane ciągu, jeśli jest obecny.</span><span class="sxs-lookup"><span data-stu-id="fcea6-198">Uses the <xref:System.Windows.DataObject.GetData%2A> method to extract the string data if it is present.</span></span>  
  
    -   <span data-ttu-id="fcea6-199">Używa <xref:System.Windows.Media.BrushConverter> spróbuj przekonwertować ciągu do <xref:System.Windows.Media.Brush>.</span><span class="sxs-lookup"><span data-stu-id="fcea6-199">Uses a <xref:System.Windows.Media.BrushConverter> to try to convert the string to a <xref:System.Windows.Media.Brush>.</span></span>  
  
    -   <span data-ttu-id="fcea6-200">Jeśli konwersja zakończy się pomyślnie, stosuje pędzla do <xref:System.Windows.Shapes.Shape.Fill%2A> z <xref:System.Windows.Shapes.Ellipse> zapewnia koło formantu interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="fcea6-200">If the conversion is successful, applies the brush to the <xref:System.Windows.Shapes.Shape.Fill%2A> of the <xref:System.Windows.Shapes.Ellipse> that provides the UI of the Circle control.</span></span>  
  
    -   <span data-ttu-id="fcea6-201">Znaczniki <xref:System.Windows.UIElement.Drop> zdarzenie, ponieważ obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="fcea6-201">Marks the <xref:System.Windows.UIElement.Drop> event as handled.</span></span> <span data-ttu-id="fcea6-202">Zdarzenie upuszczania powinny zostać oznaczone jako obsługi, aby poinformować inne elementy, które odbierają to zdarzenie kontrolki użytkownika koło obsługiwane go.</span><span class="sxs-lookup"><span data-stu-id="fcea6-202">You should mark the drop event as handled so that other elements that receive this event know that the Circle user control handled it.</span></span>  
  
3.  <span data-ttu-id="fcea6-203">Naciśnij klawisz F5, aby skompilować i uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="fcea6-203">Press F5 to build and run the application.</span></span>  
  
4.  <span data-ttu-id="fcea6-204">Zaznacz tekst `green` w <xref:System.Windows.Controls.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="fcea6-204">Select the text `green` in the <xref:System.Windows.Controls.TextBox>.</span></span>  
  
5.  <span data-ttu-id="fcea6-205">Przeciągnij tekst do formantu koło i upuść go.</span><span class="sxs-lookup"><span data-stu-id="fcea6-205">Drag the text to a Circle control and drop it.</span></span> <span data-ttu-id="fcea6-206">Zmiany koło z blue zielony.</span><span class="sxs-lookup"><span data-stu-id="fcea6-206">The Circle changes from blue to green.</span></span>  
  
     <span data-ttu-id="fcea6-207">![Konwertowanie ciągu pędzel](../../../../docs/framework/wpf/advanced/media/dragdrop-dropgreentext.png "DragDrop_DropGreenText")</span><span class="sxs-lookup"><span data-stu-id="fcea6-207">![Convert a string to a brush](../../../../docs/framework/wpf/advanced/media/dragdrop-dropgreentext.png "DragDrop_DropGreenText")</span></span>  
  
6.  <span data-ttu-id="fcea6-208">Wpisz tekst `green` w <xref:System.Windows.Controls.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="fcea6-208">Type the text `green` in the <xref:System.Windows.Controls.TextBox>.</span></span>  
  
7.  <span data-ttu-id="fcea6-209">Zaznacz tekst `gre` w <xref:System.Windows.Controls.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="fcea6-209">Select the text `gre` in the <xref:System.Windows.Controls.TextBox>.</span></span>  
  
8.  <span data-ttu-id="fcea6-210">Przeciągnij go do kontroli koło i upuść go.</span><span class="sxs-lookup"><span data-stu-id="fcea6-210">Drag it to a Circle control and drop it.</span></span> <span data-ttu-id="fcea6-211">Należy zauważyć, że kursor zmienia się na wskazują, że listy jest dozwolone, ale nie zmienia kolor okręgu, ponieważ `gre` nie jest prawidłowy kolor.</span><span class="sxs-lookup"><span data-stu-id="fcea6-211">Notice that the cursor changes to indicate that the drop is allowed, but the color of the Circle does not change because `gre` is not a valid color.</span></span>  
  
9. <span data-ttu-id="fcea6-212">Przeciągnij z formantu zielone koło i usunąć niebieskie formantu koło.</span><span class="sxs-lookup"><span data-stu-id="fcea6-212">Drag from the green Circle control and drop on the blue Circle control.</span></span> <span data-ttu-id="fcea6-213">Zmiany koło z blue zielony.</span><span class="sxs-lookup"><span data-stu-id="fcea6-213">The Circle changes from blue to green.</span></span> <span data-ttu-id="fcea6-214">Należy zauważyć, że jest wyświetlany kursor, który jest zależny od tego, czy <xref:System.Windows.Controls.TextBox> lub okręgu jest elementem źródłowym przeciągania.</span><span class="sxs-lookup"><span data-stu-id="fcea6-214">Notice that which cursor is shown depends on whether the <xref:System.Windows.Controls.TextBox> or the Circle is the drag source.</span></span>  
  
 <span data-ttu-id="fcea6-215">Ustawienie <xref:System.Windows.UIElement.AllowDrop%2A> właściwości `true` i przetwarzania danych porzuconych jest wszystko, co jest wymagane w celu włączenia element jako element docelowy upuszczania.</span><span class="sxs-lookup"><span data-stu-id="fcea6-215">Setting the <xref:System.Windows.UIElement.AllowDrop%2A> property to `true` and processing the dropped data is all that is required to enable an element to be a drop target.</span></span> <span data-ttu-id="fcea6-216">Jednak aby zapewnić lepsze środowisko użytkownika, możesz również obsługi <xref:System.Windows.UIElement.DragEnter>, <xref:System.Windows.UIElement.DragLeave>, i <xref:System.Windows.UIElement.DragOver> zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="fcea6-216">However, to provide a better user experience, you should also handle the <xref:System.Windows.UIElement.DragEnter>, <xref:System.Windows.UIElement.DragLeave>, and <xref:System.Windows.UIElement.DragOver> events.</span></span> <span data-ttu-id="fcea6-217">W tych zdarzeń można wykonać kontroli i wyrazić swoją opinię dodatkowe do użytkownika, zanim danych zostanie porzucony.</span><span class="sxs-lookup"><span data-stu-id="fcea6-217">In these events, you can perform checks and provide additional feedback to the user before the data is dropped.</span></span>  
  
 <span data-ttu-id="fcea6-218">Gdy danych zostanie przeciągnięty nad formantem użytkownika koło, formantu powiadamiać źródła przeciągania, czy może przetwarzać dane, które przeciągania.</span><span class="sxs-lookup"><span data-stu-id="fcea6-218">When data is dragged over the Circle user control, the control should notify the drag source whether it can process the data that is being dragged.</span></span> <span data-ttu-id="fcea6-219">Jeśli formant nie może określić sposób przetwarzania danych, należy go odmówić listy.</span><span class="sxs-lookup"><span data-stu-id="fcea6-219">If the control does not know how to process the data, it should refuse the drop.</span></span> <span data-ttu-id="fcea6-220">Aby to zrobić, będzie obsługiwać <xref:System.Windows.UIElement.DragOver> zdarzeń i zestaw <xref:System.Windows.DragEventArgs.Effects%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="fcea6-220">To do this, you will handle the <xref:System.Windows.UIElement.DragOver> event and set the <xref:System.Windows.DragEventArgs.Effects%2A> property.</span></span>  
  
### <a name="to-verify-that-the-data-drop-is-allowed"></a><span data-ttu-id="fcea6-221">Aby sprawdzić, czy jest dozwolone porzucenia danych</span><span class="sxs-lookup"><span data-stu-id="fcea6-221">To verify that the data drop is allowed</span></span>  
  
1.  <span data-ttu-id="fcea6-222">Otwórz Circle.xaml.cs lub Circle.xaml.vb.</span><span class="sxs-lookup"><span data-stu-id="fcea6-222">Open Circle.xaml.cs or Circle.xaml.vb.</span></span>  
  
2.  <span data-ttu-id="fcea6-223">Dodaj następujące <xref:System.Windows.UIElement.OnDragOver%2A> zastąpienie w celu zapewnienia obsługi dla klasy <xref:System.Windows.UIElement.DragOver> zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="fcea6-223">Add the following <xref:System.Windows.UIElement.OnDragOver%2A> override to provide class handling for the <xref:System.Windows.UIElement.DragOver> event.</span></span>  
  
     [!code-csharp[DragDropWalkthrough#OnDragOver](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#ondragover)]
     [!code-vb[DragDropWalkthrough#OnDragOver](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#ondragover)]  
  
     <span data-ttu-id="fcea6-224">To <xref:System.Windows.UIElement.OnDragOver%2A> zastąpienie wykonuje następujące zadania:</span><span class="sxs-lookup"><span data-stu-id="fcea6-224">This <xref:System.Windows.UIElement.OnDragOver%2A> override performs the following tasks:</span></span>  
  
    -   <span data-ttu-id="fcea6-225">Ustawia <xref:System.Windows.DragEventArgs.Effects%2A> właściwości <xref:System.Windows.DragDropEffects.None>.</span><span class="sxs-lookup"><span data-stu-id="fcea6-225">Sets the <xref:System.Windows.DragEventArgs.Effects%2A> property to <xref:System.Windows.DragDropEffects.None>.</span></span>  
  
    -   <span data-ttu-id="fcea6-226">Wykonuje tej samej testy, które są wykonywane w <xref:System.Windows.UIElement.OnDrop%2A> metodę, aby określić, czy formant użytkownika koło może przetwarzać przeciąganego danych.</span><span class="sxs-lookup"><span data-stu-id="fcea6-226">Performs the same checks that are performed in the <xref:System.Windows.UIElement.OnDrop%2A> method to determine whether the Circle user control can process the dragged data.</span></span>  
  
    -   <span data-ttu-id="fcea6-227">Jeśli formant użytkownika może przetwarzać danych, ustawia <xref:System.Windows.DragEventArgs.Effects%2A> właściwości <xref:System.Windows.DragDropEffects.Copy> lub <xref:System.Windows.DragDropEffects.Move>.</span><span class="sxs-lookup"><span data-stu-id="fcea6-227">If the user control can process the data, sets the <xref:System.Windows.DragEventArgs.Effects%2A> property to <xref:System.Windows.DragDropEffects.Copy> or <xref:System.Windows.DragDropEffects.Move>.</span></span>  
  
3.  <span data-ttu-id="fcea6-228">Naciśnij klawisz F5, aby skompilować i uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="fcea6-228">Press F5 to build and run the application.</span></span>  
  
4.  <span data-ttu-id="fcea6-229">Zaznacz tekst `gre` w <xref:System.Windows.Controls.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="fcea6-229">Select the text `gre` in the <xref:System.Windows.Controls.TextBox>.</span></span>  
  
5.  <span data-ttu-id="fcea6-230">Przeciągnij tekst formantu okręgu.</span><span class="sxs-lookup"><span data-stu-id="fcea6-230">Drag the text to a Circle control.</span></span> <span data-ttu-id="fcea6-231">Należy zauważyć, że kursor zmienia się teraz na wskazują, że listy jest niedozwolona, ponieważ `gre` nie jest prawidłowy kolor.</span><span class="sxs-lookup"><span data-stu-id="fcea6-231">Notice that the cursor now changes to indicate that the drop is not allowed because `gre` is not a valid color.</span></span>  
  
 <span data-ttu-id="fcea6-232">Może dodatkowo ulepszyć środowisko użytkownika, stosując Podgląd operacji usuwania.</span><span class="sxs-lookup"><span data-stu-id="fcea6-232">You can further enhance the user experience by applying a preview of the drop operation.</span></span> <span data-ttu-id="fcea6-233">Kontrolki użytkownika koło, spowoduje zastąpienie <xref:System.Windows.UIElement.OnDragEnter%2A> i <xref:System.Windows.UIElement.OnDragLeave%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="fcea6-233">For the Circle user control, you will override the <xref:System.Windows.UIElement.OnDragEnter%2A> and <xref:System.Windows.UIElement.OnDragLeave%2A> methods.</span></span> <span data-ttu-id="fcea6-234">Po danych zostanie przeciągnięty nad formantem bieżące tło <xref:System.Windows.Shapes.Shape.Fill%2A> jest zapisywany w zmiennej symbolu zastępczego.</span><span class="sxs-lookup"><span data-stu-id="fcea6-234">When the data is dragged over the control, the current background <xref:System.Windows.Shapes.Shape.Fill%2A> is saved in a placeholder variable.</span></span> <span data-ttu-id="fcea6-235">Ciąg jest następnie konwertowana pędzla i stosowane do <xref:System.Windows.Shapes.Ellipse> zapewnia okręgu interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="fcea6-235">The string is then converted to a brush and applied to the <xref:System.Windows.Shapes.Ellipse> that provides the Circle's UI.</span></span> <span data-ttu-id="fcea6-236">Jeśli dane zostanie przeciągnięty poza okręgu bez usuwane oryginalnej <xref:System.Windows.Shapes.Shape.Fill%2A> wartość jest ponownie stosowana do okręgu.</span><span class="sxs-lookup"><span data-stu-id="fcea6-236">If the data is dragged out of the Circle without being dropped, the original <xref:System.Windows.Shapes.Shape.Fill%2A> value is re-applied to the Circle.</span></span>  
  
### <a name="to-preview-the-effects-of-the-drag-and-drop-operation"></a><span data-ttu-id="fcea6-237">Aby wyświetlić podgląd skutków operacji przeciągania i upuszczania</span><span class="sxs-lookup"><span data-stu-id="fcea6-237">To preview the effects of the drag-and-drop operation</span></span>  
  
1.  <span data-ttu-id="fcea6-238">Otwórz Circle.xaml.cs lub Circle.xaml.vb.</span><span class="sxs-lookup"><span data-stu-id="fcea6-238">Open Circle.xaml.cs or Circle.xaml.vb.</span></span>  
  
2.  <span data-ttu-id="fcea6-239">W klasie koło zadeklarować prywatnej <xref:System.Windows.Media.Brush> zmiennej o nazwie `_previousFill` i zainicjować go do `null`.</span><span class="sxs-lookup"><span data-stu-id="fcea6-239">In the Circle class, declare a private <xref:System.Windows.Media.Brush> variable named `_previousFill` and initialize it to `null`.</span></span>  
  
     [!code-csharp[DragDropWalkthrough#Brush](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#brush)]
     [!code-vb[DragDropWalkthrough#Brush](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#brush)]  
  
3.  <span data-ttu-id="fcea6-240">Dodaj następujące <xref:System.Windows.UIElement.OnDragEnter%2A> zastąpienie w celu zapewnienia obsługi dla klasy <xref:System.Windows.UIElement.DragEnter> zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="fcea6-240">Add the following <xref:System.Windows.UIElement.OnDragEnter%2A> override to provide class handling for the <xref:System.Windows.UIElement.DragEnter> event.</span></span>  
  
     [!code-csharp[DragDropWalkthrough#OnDragEnter](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#ondragenter)]
     [!code-vb[DragDropWalkthrough#OnDragEnter](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#ondragenter)]  
  
     <span data-ttu-id="fcea6-241">To <xref:System.Windows.UIElement.OnDragEnter%2A> zastąpienie wykonuje następujące zadania:</span><span class="sxs-lookup"><span data-stu-id="fcea6-241">This <xref:System.Windows.UIElement.OnDragEnter%2A> override performs the following tasks:</span></span>  
  
    -   <span data-ttu-id="fcea6-242">Zapisuje <xref:System.Windows.Shapes.Shape.Fill%2A> właściwość <xref:System.Windows.Shapes.Ellipse> w `_previousFill` zmiennej.</span><span class="sxs-lookup"><span data-stu-id="fcea6-242">Saves the <xref:System.Windows.Shapes.Shape.Fill%2A> property of the <xref:System.Windows.Shapes.Ellipse> in the `_previousFill` variable.</span></span>  
  
    -   <span data-ttu-id="fcea6-243">Wykonuje tej samej testy, które są wykonywane w <xref:System.Windows.UIElement.OnDrop%2A> metodę, aby określić, czy dane mogą być konwertowane na <xref:System.Windows.Media.Brush>.</span><span class="sxs-lookup"><span data-stu-id="fcea6-243">Performs the same checks that are performed in the <xref:System.Windows.UIElement.OnDrop%2A> method to determine whether the data can be converted to a <xref:System.Windows.Media.Brush>.</span></span>  
  
    -   <span data-ttu-id="fcea6-244">Jeśli dane są konwertowane na prawidłową <xref:System.Windows.Media.Brush>, stosuje je do <xref:System.Windows.Shapes.Shape.Fill%2A> z <xref:System.Windows.Shapes.Ellipse>.</span><span class="sxs-lookup"><span data-stu-id="fcea6-244">If the data is converted to a valid <xref:System.Windows.Media.Brush>, applies it to the <xref:System.Windows.Shapes.Shape.Fill%2A> of the <xref:System.Windows.Shapes.Ellipse>.</span></span>  
  
4.  <span data-ttu-id="fcea6-245">Dodaj następujące <xref:System.Windows.UIElement.OnDragLeave%2A> zastąpienie w celu zapewnienia obsługi dla klasy <xref:System.Windows.UIElement.DragLeave> zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="fcea6-245">Add the following <xref:System.Windows.UIElement.OnDragLeave%2A> override to provide class handling for the <xref:System.Windows.UIElement.DragLeave> event.</span></span>  
  
     [!code-csharp[DragDropWalkthrough#OnDragLeave](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#ondragleave)]
     [!code-vb[DragDropWalkthrough#OnDragLeave](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#ondragleave)]  
  
     <span data-ttu-id="fcea6-246">To <xref:System.Windows.UIElement.OnDragLeave%2A> zastąpienie wykonuje następujące zadania:</span><span class="sxs-lookup"><span data-stu-id="fcea6-246">This <xref:System.Windows.UIElement.OnDragLeave%2A> override performs the following tasks:</span></span>  
  
    -   <span data-ttu-id="fcea6-247">Stosuje <xref:System.Windows.Media.Brush> zapisane w `_previousFill` zmienną <xref:System.Windows.Shapes.Shape.Fill%2A> z <xref:System.Windows.Shapes.Ellipse> zapewnia interfejsu użytkownika koło kontrolki użytkownika.</span><span class="sxs-lookup"><span data-stu-id="fcea6-247">Applies the <xref:System.Windows.Media.Brush> saved in the `_previousFill` variable to the <xref:System.Windows.Shapes.Shape.Fill%2A> of the <xref:System.Windows.Shapes.Ellipse> that provides the UI of the Circle user control.</span></span>  
  
5.  <span data-ttu-id="fcea6-248">Naciśnij klawisz F5, aby skompilować i uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="fcea6-248">Press F5 to build and run the application.</span></span>  
  
6.  <span data-ttu-id="fcea6-249">Zaznacz tekst `green` w <xref:System.Windows.Controls.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="fcea6-249">Select the text `green` in the <xref:System.Windows.Controls.TextBox>.</span></span>  
  
7.  <span data-ttu-id="fcea6-250">Przeciągnij tekst nad formantem okręgu bez porzuceniem jej.</span><span class="sxs-lookup"><span data-stu-id="fcea6-250">Drag the text over a Circle control without dropping it.</span></span> <span data-ttu-id="fcea6-251">Zmiany koło z blue zielony.</span><span class="sxs-lookup"><span data-stu-id="fcea6-251">The Circle changes from blue to green.</span></span>  
  
     <span data-ttu-id="fcea6-252">![Efekty przeciągnij&#45;i&#45;porzucić operacji](../../../../docs/framework/wpf/advanced/media/dragdrop-previeweffects.png "DragDrop_PreviewEffects")</span><span class="sxs-lookup"><span data-stu-id="fcea6-252">![Preview the effects of a drag&#45;and&#45;drop operation](../../../../docs/framework/wpf/advanced/media/dragdrop-previeweffects.png "DragDrop_PreviewEffects")</span></span>  
  
8.  <span data-ttu-id="fcea6-253">Przeciągnij tekst od kontroli okręgu.</span><span class="sxs-lookup"><span data-stu-id="fcea6-253">Drag the text away from the Circle control.</span></span> <span data-ttu-id="fcea6-254">Zmiany koło z zielonym kopii na niebieski.</span><span class="sxs-lookup"><span data-stu-id="fcea6-254">The Circle changes from green back to blue.</span></span>  
  
## <a name="enabling-a-panel-to-receive-dropped-data"></a><span data-ttu-id="fcea6-255">Włączanie panelu do odbierania porzucony danych</span><span class="sxs-lookup"><span data-stu-id="fcea6-255">Enabling a Panel to Receive Dropped Data</span></span>  
 <span data-ttu-id="fcea6-256">W tej sekcji zostaną włączone zespoły obsługujące kontrolek użytkownika okrąg na działanie jako miejsc docelowych przeciąganego danych okręgu.</span><span class="sxs-lookup"><span data-stu-id="fcea6-256">In this section, you will enable the panels that host the Circle user controls to act as drop targets for dragged Circle data.</span></span> <span data-ttu-id="fcea6-257">Kod, który umożliwia przenieść koło z jednego panelu lub utworzyć kopię formantu koło, przytrzymując klawisz CTRL podczas przeciągania i upuszczania koło zostaną zaimplementowane.</span><span class="sxs-lookup"><span data-stu-id="fcea6-257">You will implement code that enables you to move a Circle from one panel to another, or to make a copy of a Circle control by holding down the CTRL key while dragging and dropping a Circle.</span></span>  
  
### <a name="to-enable-the-panel-to-be-a-drop-target"></a><span data-ttu-id="fcea6-258">Aby włączyć panelu jako miejsca docelowego</span><span class="sxs-lookup"><span data-stu-id="fcea6-258">To enable the panel to be a drop target</span></span>  
  
1.  <span data-ttu-id="fcea6-259">Open MainWindow.xaml.</span><span class="sxs-lookup"><span data-stu-id="fcea6-259">Open MainWindow.xaml.</span></span>  
  
2.  <span data-ttu-id="fcea6-260">Jak pokazano w poniższych XAML, w każdym <xref:System.Windows.Controls.StackPanel> formantów, Dodaj obsługę <xref:System.Windows.UIElement.DragOver> i <xref:System.Windows.UIElement.Drop> zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="fcea6-260">As shown in the following XAML, in each of the <xref:System.Windows.Controls.StackPanel> controls, add handlers for the <xref:System.Windows.UIElement.DragOver> and <xref:System.Windows.UIElement.Drop> events.</span></span> <span data-ttu-id="fcea6-261">Nazwa <xref:System.Windows.UIElement.DragOver> program obsługi zdarzeń, `panel_DragOver`i nazwij <xref:System.Windows.UIElement.Drop> program obsługi zdarzeń, `panel_Drop`.</span><span class="sxs-lookup"><span data-stu-id="fcea6-261">Name the <xref:System.Windows.UIElement.DragOver> event handler, `panel_DragOver`, and name the <xref:System.Windows.UIElement.Drop> event handler, `panel_Drop`.</span></span>  
  
     [!code-xaml[DragDropWalkthrough#PanelsXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/MainWindow.xaml#panelsxaml)]  
  
3.  <span data-ttu-id="fcea6-262">Otwórz MainWindows.xaml.cs lub MainWindow.xaml.vb.</span><span class="sxs-lookup"><span data-stu-id="fcea6-262">Open MainWindows.xaml.cs or MainWindow.xaml.vb.</span></span>  
  
4.  <span data-ttu-id="fcea6-263">Dodaj następujący kod do <xref:System.Windows.UIElement.DragOver> obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="fcea6-263">Add the following code for the <xref:System.Windows.UIElement.DragOver> event handler.</span></span>  
  
     [!code-csharp[DragDropWalkthrough#PanelDragOver](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/MainWindow.xaml.cs#paneldragover)]
     [!code-vb[DragDropWalkthrough#PanelDragOver](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/MainWindow.xaml.vb#paneldragover)]  
  
     <span data-ttu-id="fcea6-264">To <xref:System.Windows.UIElement.DragOver> obsługi zdarzeń wykonuje następujące zadania:</span><span class="sxs-lookup"><span data-stu-id="fcea6-264">This <xref:System.Windows.UIElement.DragOver> event handler performs the following tasks:</span></span>  
  
    -   <span data-ttu-id="fcea6-265">Sprawdza, czy dane przeciągane zawiera dane "Obiektu", które zostało umieszczone w <xref:System.Windows.DataObject> przez formant użytkownika koło i przekazywane w wywołaniu <xref:System.Windows.DragDrop.DoDragDrop%2A>.</span><span class="sxs-lookup"><span data-stu-id="fcea6-265">Checks that the dragged data contains the "Object" data that was packaged in the <xref:System.Windows.DataObject> by the Circle user control and passed in the call to <xref:System.Windows.DragDrop.DoDragDrop%2A>.</span></span>  
  
    -   <span data-ttu-id="fcea6-266">Jeśli dane "Obiektu" jest obecny, sprawdza, czy zostanie naciśnięty klawisz CTRL.</span><span class="sxs-lookup"><span data-stu-id="fcea6-266">If the "Object" data is present, checks whether the CTRL key is pressed.</span></span>  
  
    -   <span data-ttu-id="fcea6-267">Jeśli zostanie naciśnięty klawisz CTRL, ustawia <xref:System.Windows.DragEventArgs.Effects%2A> właściwości <xref:System.Windows.DragDropEffects.Copy>.</span><span class="sxs-lookup"><span data-stu-id="fcea6-267">If the CTRL key is pressed, sets the <xref:System.Windows.DragEventArgs.Effects%2A> property to <xref:System.Windows.DragDropEffects.Copy>.</span></span> <span data-ttu-id="fcea6-268">W przeciwnym razie wartość <xref:System.Windows.DragEventArgs.Effects%2A> właściwości <xref:System.Windows.DragDropEffects.Move>.</span><span class="sxs-lookup"><span data-stu-id="fcea6-268">Otherwise, set the <xref:System.Windows.DragEventArgs.Effects%2A> property to <xref:System.Windows.DragDropEffects.Move>.</span></span>  
  
5.  <span data-ttu-id="fcea6-269">Dodaj następujący kod do <xref:System.Windows.UIElement.Drop> obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="fcea6-269">Add the following code for the <xref:System.Windows.UIElement.Drop> event handler.</span></span>  
  
     [!code-csharp[DragDropWalkthrough#PanelDrop](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/MainWindow.xaml.cs#paneldrop)]
     [!code-vb[DragDropWalkthrough#PanelDrop](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/MainWindow.xaml.vb#paneldrop)]  
  
     <span data-ttu-id="fcea6-270">To <xref:System.Windows.UIElement.Drop> obsługi zdarzeń wykonuje następujące zadania:</span><span class="sxs-lookup"><span data-stu-id="fcea6-270">This <xref:System.Windows.UIElement.Drop> event handler performs the following tasks:</span></span>  
  
    -   <span data-ttu-id="fcea6-271">Sprawdza, czy <xref:System.Windows.UIElement.Drop> zdarzenie jest już obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="fcea6-271">Checks whether the <xref:System.Windows.UIElement.Drop> event has already been handled.</span></span> <span data-ttu-id="fcea6-272">Na przykład po przerwaniu okrąg na innym koło, które uchwytów <xref:System.Windows.UIElement.Drop> zdarzeń, nie ma panelu, zawierający kółko, aby również je obsłużyć.</span><span class="sxs-lookup"><span data-stu-id="fcea6-272">For instance, if a Circle is dropped on another Circle which handles the <xref:System.Windows.UIElement.Drop> event, you do not want the panel that contains the Circle to also handle it.</span></span>  
  
    -   <span data-ttu-id="fcea6-273">Jeśli <xref:System.Windows.UIElement.Drop> zdarzeń nie jest obsługiwana, sprawdza czy zostanie naciśnięty klawisz CTRL.</span><span class="sxs-lookup"><span data-stu-id="fcea6-273">If the <xref:System.Windows.UIElement.Drop> event is not handled, checks whether the CTRL key is pressed.</span></span>  
  
    -   <span data-ttu-id="fcea6-274">Jeśli po naciśnięciu klawisza CTRL <xref:System.Windows.UIElement.Drop> następuje, sprawia, że kopia okręgu kontroli i dodać go do <xref:System.Windows.Controls.Panel.Children%2A> kolekcji <xref:System.Windows.Controls.StackPanel>.</span><span class="sxs-lookup"><span data-stu-id="fcea6-274">If the CTRL key is pressed when the <xref:System.Windows.UIElement.Drop> happens, makes a copy of the Circle control and add it to the <xref:System.Windows.Controls.Panel.Children%2A> collection of the <xref:System.Windows.Controls.StackPanel>.</span></span>  
  
    -   <span data-ttu-id="fcea6-275">Jeśli nie zostanie naciśnięty klawisz CTRL, przenosi koło z <xref:System.Windows.Controls.Panel.Children%2A> kolekcji nadrzędnej panel do <xref:System.Windows.Controls.Panel.Children%2A> kolekcji panelu, który został porzucony na.</span><span class="sxs-lookup"><span data-stu-id="fcea6-275">If the CTRL key is not pressed, moves the Circle from the <xref:System.Windows.Controls.Panel.Children%2A> collection of its parent panel to the <xref:System.Windows.Controls.Panel.Children%2A> collection of the panel that it was dropped on.</span></span>  
  
    -   <span data-ttu-id="fcea6-276">Ustawia <xref:System.Windows.DragEventArgs.Effects%2A> właściwości powiadomiono <xref:System.Windows.DragDrop.DoDragDrop%2A> metody czy zostało przeprowadzone operacji przenoszenia lub kopiowania.</span><span class="sxs-lookup"><span data-stu-id="fcea6-276">Sets the <xref:System.Windows.DragEventArgs.Effects%2A> property to notify the <xref:System.Windows.DragDrop.DoDragDrop%2A> method whether a move or copy operation was performed.</span></span>  
  
6.  <span data-ttu-id="fcea6-277">Naciśnij klawisz F5, aby skompilować i uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="fcea6-277">Press F5 to build and run the application.</span></span>  
  
7.  <span data-ttu-id="fcea6-278">Zaznacz tekst `green` z <xref:System.Windows.Controls.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="fcea6-278">Select the text `green` from the <xref:System.Windows.Controls.TextBox>.</span></span>  
  
8.  <span data-ttu-id="fcea6-279">Przeciągnij tekst nad formantem koło i upuść go.</span><span class="sxs-lookup"><span data-stu-id="fcea6-279">Drag the text over a Circle control and drop it.</span></span>  
  
9. <span data-ttu-id="fcea6-280">Przeciągnij formant koło z lewego panelu na prawym panelu i upuść go.</span><span class="sxs-lookup"><span data-stu-id="fcea6-280">Drag a Circle control from the left panel to the right panel and drop it.</span></span> <span data-ttu-id="fcea6-281">Okręgu zostanie usunięty z <xref:System.Windows.Controls.Panel.Children%2A> kolekcji lewego panelu i dodany do kolekcji elementów podrzędnych w prawym panelu.</span><span class="sxs-lookup"><span data-stu-id="fcea6-281">The Circle is removed from the <xref:System.Windows.Controls.Panel.Children%2A> collection of the left panel and added to the Children collection of the right panel.</span></span>  
  
10. <span data-ttu-id="fcea6-282">Przeciągnij formant koło z panelu, w którym się do innych panelu i upuść naciskaj klawisz CTRL.</span><span class="sxs-lookup"><span data-stu-id="fcea6-282">Drag a Circle control from the panel it is in to the other panel and drop it while pressing the CTRL key.</span></span> <span data-ttu-id="fcea6-283">Okręgu jest kopiowany i dodawane do kopii <xref:System.Windows.Controls.Panel.Children%2A> kolekcji panelu docelowego.</span><span class="sxs-lookup"><span data-stu-id="fcea6-283">The Circle is copied and the copy is added to the <xref:System.Windows.Controls.Panel.Children%2A> collection of the receiving panel.</span></span>  
  
     <span data-ttu-id="fcea6-284">![Przeciąganie koło naciskaj klawisz CTRL](../../../../docs/framework/wpf/advanced/media/dragdrop-paneldrop.png "DragDrop_PanelDrop")</span><span class="sxs-lookup"><span data-stu-id="fcea6-284">![Dragging a Circle while pressing the CTRL key](../../../../docs/framework/wpf/advanced/media/dragdrop-paneldrop.png "DragDrop_PanelDrop")</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fcea6-285">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="fcea6-285">See Also</span></span>  
 [<span data-ttu-id="fcea6-286">Przegląd przeciągania i upuszczania</span><span class="sxs-lookup"><span data-stu-id="fcea6-286">Drag and Drop Overview</span></span>](../../../../docs/framework/wpf/advanced/drag-and-drop-overview.md)
