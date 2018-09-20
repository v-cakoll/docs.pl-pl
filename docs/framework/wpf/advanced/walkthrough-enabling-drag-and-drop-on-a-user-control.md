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
ms.openlocfilehash: e151eb7f428fecb330970210fd7addb1603a211f
ms.sourcegitcommit: 3ab9254890a52a50762995fa6d7d77a00348db7e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46326624"
---
# <a name="walkthrough-enabling-drag-and-drop-on-a-user-control"></a><span data-ttu-id="99da4-102">Wskazówki: włączanie przeciągania i upuszczania w kontrolce użytkownika</span><span class="sxs-lookup"><span data-stu-id="99da4-102">Walkthrough: Enabling Drag and Drop on a User Control</span></span>
<span data-ttu-id="99da4-103">W tym instruktażu pokazano, jak utworzyć formant użytkownika niestandardowego, które mogą uczestniczyć w transferu danych przeciągnij i upuść [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)].</span><span class="sxs-lookup"><span data-stu-id="99da4-103">This walkthrough demonstrates how to create a custom user control that can participate in drag-and-drop data transfer in [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)].</span></span>  
  
 <span data-ttu-id="99da4-104">W tym przewodniku utworzysz niestandardowego WPF <xref:System.Windows.Controls.UserControl> reprezentujący okrągłe.</span><span class="sxs-lookup"><span data-stu-id="99da4-104">In this walkthrough, you will create a custom WPF <xref:System.Windows.Controls.UserControl> that represents a circle shape.</span></span> <span data-ttu-id="99da4-105">Funkcje zostaną zaimplementowane w kontrolce umożliwia transfer danych za pomocą przeciągania i upuszczania.</span><span class="sxs-lookup"><span data-stu-id="99da4-105">You will implement functionality on the control to enable data transfer through drag-and-drop.</span></span> <span data-ttu-id="99da4-106">Na przykład jeśli przeciągniesz z jednego formantu okrąg do innego, dane koloru wypełnienia zostanie skopiowana ze źródła okrąg do obiektu docelowego.</span><span class="sxs-lookup"><span data-stu-id="99da4-106">For example, if you drag from one Circle control to another, the Fill color data is copied from the source Circle to the target.</span></span> <span data-ttu-id="99da4-107">Jeśli przeciągniesz w kontrolce okrąg do <xref:System.Windows.Controls.TextBox>, reprezentacja ciągu koloru wypełnienia jest kopiowany do <xref:System.Windows.Controls.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="99da4-107">If you drag from a Circle control to a <xref:System.Windows.Controls.TextBox>, the string representation of the Fill color is copied to the <xref:System.Windows.Controls.TextBox>.</span></span> <span data-ttu-id="99da4-108">Mała aplikacja, która zawiera dwie kontrolki panel zostanie również utworzony i <xref:System.Windows.Controls.TextBox> do testowania funkcji przeciągania i upuszczania.</span><span class="sxs-lookup"><span data-stu-id="99da4-108">You will also create a small application that contains two panel controls and a <xref:System.Windows.Controls.TextBox> to test the drag-and-drop functionality.</span></span> <span data-ttu-id="99da4-109">Trzeba napisać kod, który umożliwia paneli do przetwarzania danych porzuconych koła, która umożliwia przenoszenie lub kopiowanie okręgów z kolekcji elementów podrzędnych panelu jednego do drugiego.</span><span class="sxs-lookup"><span data-stu-id="99da4-109">You will write code that enables the panels to process dropped Circle data, which will enable you to move or copy Circles from the Children collection of one panel to the other.</span></span>  
  
 <span data-ttu-id="99da4-110">W instruktażu przedstawiono następujące zagadnienia:</span><span class="sxs-lookup"><span data-stu-id="99da4-110">This walkthrough illustrates the following tasks:</span></span>  
  
-   <span data-ttu-id="99da4-111">Tworzenie niestandardowej kontrolki użytkownika.</span><span class="sxs-lookup"><span data-stu-id="99da4-111">Create a custom user control.</span></span>  
  
-   <span data-ttu-id="99da4-112">Włącz do źródła przeciągnij formant użytkownika.</span><span class="sxs-lookup"><span data-stu-id="99da4-112">Enable the user control to be a drag source.</span></span>  
  
-   <span data-ttu-id="99da4-113">Włącz kontrolkę użytkownika do miejsca docelowego.</span><span class="sxs-lookup"><span data-stu-id="99da4-113">Enable the user control to be a drop target.</span></span>  
  
-   <span data-ttu-id="99da4-114">Włączanie panelu na odbieranie danych z kontrolki użytkownika.</span><span class="sxs-lookup"><span data-stu-id="99da4-114">Enable a panel to receive data dropped from the user control.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="99da4-115">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="99da4-115">Prerequisites</span></span>  
 <span data-ttu-id="99da4-116">Następujące składniki są wymagane do przeprowadzenia tego instruktażu:</span><span class="sxs-lookup"><span data-stu-id="99da4-116">You need the following components to complete this walkthrough:</span></span>  
  
-   <span data-ttu-id="99da4-117">Visual Studio 2010</span><span class="sxs-lookup"><span data-stu-id="99da4-117">Visual Studio 2010</span></span>  
  
## <a name="creating-the-application-project"></a><span data-ttu-id="99da4-118">Tworzenie projektu aplikacji</span><span class="sxs-lookup"><span data-stu-id="99da4-118">Creating the Application Project</span></span>  
 <span data-ttu-id="99da4-119">W tej sekcji utworzysz infrastruktury aplikacji, która zawiera strona główna z dwa panele i <xref:System.Windows.Controls.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="99da4-119">In this section, you will create the application infrastructure, which includes a main page with two panels and a <xref:System.Windows.Controls.TextBox>.</span></span>  
  
### <a name="to-create-the-project"></a><span data-ttu-id="99da4-120">Aby utworzyć projekt</span><span class="sxs-lookup"><span data-stu-id="99da4-120">To create the project</span></span>  
  
1.  <span data-ttu-id="99da4-121">Utwórz nowy projekt aplikacji WPF w języku Visual Basic lub Visual C# o nazwie `DragDropExample`.</span><span class="sxs-lookup"><span data-stu-id="99da4-121">Create a new WPF Application project in Visual Basic or Visual C# named `DragDropExample`.</span></span> <span data-ttu-id="99da4-122">Aby uzyskać więcej informacji, zobacz [porady: Tworzenie nowego projektu aplikacji WPF](https://msdn.microsoft.com/library/1f6aea7a-33e1-4d3f-8555-1daa42e95d82).</span><span class="sxs-lookup"><span data-stu-id="99da4-122">For more information, see [How to: Create a New WPF Application Project](https://msdn.microsoft.com/library/1f6aea7a-33e1-4d3f-8555-1daa42e95d82).</span></span>  
  
2.  <span data-ttu-id="99da4-123">Open MainWindow.xaml.</span><span class="sxs-lookup"><span data-stu-id="99da4-123">Open MainWindow.xaml.</span></span>  
  
3.  <span data-ttu-id="99da4-124">Dodaj następujący kod między otwierającym i zamykającym <xref:System.Windows.Controls.Grid> tagów.</span><span class="sxs-lookup"><span data-stu-id="99da4-124">Add the following markup between the opening and closing <xref:System.Windows.Controls.Grid> tags.</span></span>  
  
     <span data-ttu-id="99da4-125">Ten kod znaczników tworzy interfejs użytkownika dla aplikacji testowej.</span><span class="sxs-lookup"><span data-stu-id="99da4-125">This markup creates the user interface for the test application.</span></span>  
  
     [!code-xaml[DragDropWalkthrough#PanelsStep1XAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/SnippetWindow.xaml#panelsstep1xaml)]  
  
## <a name="adding-a-new-user-control-to-the-project"></a><span data-ttu-id="99da4-126">Dodawanie nowej kontrolki użytkownika do projektu</span><span class="sxs-lookup"><span data-stu-id="99da4-126">Adding a New User Control to the Project</span></span>  
 <span data-ttu-id="99da4-127">W tej sekcji dodasz nowy formant użytkownika do projektu.</span><span class="sxs-lookup"><span data-stu-id="99da4-127">In this section, you will add a new user control to the project.</span></span>  
  
### <a name="to-add-a-new-user-control"></a><span data-ttu-id="99da4-128">Aby dodać nową kontrolkę użytkownika</span><span class="sxs-lookup"><span data-stu-id="99da4-128">To add a new user control</span></span>  
  
1.  <span data-ttu-id="99da4-129">Z menu projektu wybierz **Dodaj kontrolkę użytkownika**.</span><span class="sxs-lookup"><span data-stu-id="99da4-129">On the Project menu, select **Add User Control**.</span></span>  
  
2.  <span data-ttu-id="99da4-130">W oknie dialogowym Dodaj nowy element, Zmień nazwę na `Circle.xaml`i kliknij przycisk **Dodaj**.</span><span class="sxs-lookup"><span data-stu-id="99da4-130">In the Add New Item dialog box, change the name to `Circle.xaml`, and click **Add**.</span></span>  
  
     <span data-ttu-id="99da4-131">Circle.XAML i jego związanym z kodem są dodawane do projektu.</span><span class="sxs-lookup"><span data-stu-id="99da4-131">Circle.xaml and its code-behind is added to the project.</span></span>  
  
3.  <span data-ttu-id="99da4-132">Open Circle.xaml.</span><span class="sxs-lookup"><span data-stu-id="99da4-132">Open Circle.xaml.</span></span>  
  
     <span data-ttu-id="99da4-133">Ten plik zawiera elementy interfejsu użytkownika formantu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="99da4-133">This file will contain the user interface elements of the user control.</span></span>  
  
4.  <span data-ttu-id="99da4-134">Dodaj następujący kod do katalogu głównego <xref:System.Windows.Controls.Grid> utworzyć kontrolkę użytkownika proste jasnoniebieski okrąg jako jego interfejsie użytkownika.</span><span class="sxs-lookup"><span data-stu-id="99da4-134">Add the following markup to the root <xref:System.Windows.Controls.Grid> to create a simple user control that has a blue circle as its UI.</span></span>  
  
     [!code-xaml[DragDropWalkthrough#EllipseXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml#ellipsexaml)]  
  
5.  <span data-ttu-id="99da4-135">Otwórz Circle.xaml.cs lub Circle.xaml.vb.</span><span class="sxs-lookup"><span data-stu-id="99da4-135">Open Circle.xaml.cs or Circle.xaml.vb.</span></span>  
  
6.  <span data-ttu-id="99da4-136">W języku C# Dodaj następujący kod po konstruktora domyślnego, aby utworzyć Konstruktor kopiujący.</span><span class="sxs-lookup"><span data-stu-id="99da4-136">In C#, add the following code after the default constructor to create a copy constructor.</span></span> <span data-ttu-id="99da4-137">W języku Visual Basic Dodaj następujący kod, aby utworzyć domyślny konstruktor i Konstruktor kopiujący.</span><span class="sxs-lookup"><span data-stu-id="99da4-137">In Visual Basic, add the following code to create both a default constructor and a copy constructor.</span></span>  
  
     <span data-ttu-id="99da4-138">Aby umożliwić kontrolki użytkownika, który ma być kopiowany, dodajesz metodę konstruktora kopiowania w pliku związanym z kodem.</span><span class="sxs-lookup"><span data-stu-id="99da4-138">In order to allow the user control to be copied, you add a copy constructor method in the code-behind file.</span></span> <span data-ttu-id="99da4-139">W kontrolce użytkownika uproszczone okrąg możesz zostaną skopiowane tylko wypełnienia i rozmiar kontrolki użytkownika.</span><span class="sxs-lookup"><span data-stu-id="99da4-139">In the simplified Circle user control, you will only copy the Fill and the size of the of the user control.</span></span>  
  
     [!code-csharp[DragDropWalkthrough#CopyCtor](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#copyctor)]
     [!code-vb[DragDropWalkthrough#CopyCtor](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#copyctor)]  
  
### <a name="to-add-the-user-control-to-the-main-window"></a><span data-ttu-id="99da4-140">Aby dodać formant użytkownika do okna głównego</span><span class="sxs-lookup"><span data-stu-id="99da4-140">To add the user control to the main window</span></span>  
  
1.  <span data-ttu-id="99da4-141">Open MainWindow.xaml.</span><span class="sxs-lookup"><span data-stu-id="99da4-141">Open MainWindow.xaml.</span></span>  
  
2.  <span data-ttu-id="99da4-142">Dodaj następujące XAML do otwarcia <xref:System.Windows.Window> tagu, można utworzyć odwołania do przestrzeni nazw XML dla bieżącej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="99da4-142">Add the following XAML to the opening <xref:System.Windows.Window> tag to create an XML namespace reference to the current application.</span></span>  
  
    ```  
    xmlns:local="clr-namespace:DragDropExample"  
    ```  
  
3.  <span data-ttu-id="99da4-143">W pierwszym <xref:System.Windows.Controls.StackPanel>, Dodaj następujące XAML, aby utworzyć dwa wystąpienia kontrolki użytkownika okrąg w pierwszym panelu.</span><span class="sxs-lookup"><span data-stu-id="99da4-143">In the first <xref:System.Windows.Controls.StackPanel>, add the following XAML to create two instances of the Circle user control in the first panel.</span></span>  
  
     [!code-xaml[DragDropWalkthrough#CirclesXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/SnippetWindow.xaml#circlesxaml)]  
  
     <span data-ttu-id="99da4-144">Pełne XAML panelu wygląda podobnie do poniższego.</span><span class="sxs-lookup"><span data-stu-id="99da4-144">The full XAML for the panel looks like the following.</span></span>  
  
     [!code-xaml[DragDropWalkthrough#PanelsStep2XAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/SnippetWindow.xaml#panelsstep2xaml)]  
  
## <a name="implementing-drag-source-events-in-the-user-control"></a><span data-ttu-id="99da4-145">Implementowanie zdarzenia źródła przeciągania w kontrolce użytkownika</span><span class="sxs-lookup"><span data-stu-id="99da4-145">Implementing Drag Source Events in the User Control</span></span>  
 <span data-ttu-id="99da4-146">W tej sekcji spowoduje przesłonięcie <xref:System.Windows.UIElement.OnMouseMove%2A> metody i zainicjuj operację przeciągania i upuszczania.</span><span class="sxs-lookup"><span data-stu-id="99da4-146">In this section, you will override the <xref:System.Windows.UIElement.OnMouseMove%2A> method and initiate the drag-and-drop operation.</span></span>  
  
 <span data-ttu-id="99da4-147">Po uruchomieniu przeciągnij przycisk myszy jest wciśnięty i wskaźnik myszy zostanie przeniesiony, będzie spakować dane do przesłania do <xref:System.Windows.DataObject>.</span><span class="sxs-lookup"><span data-stu-id="99da4-147">If a drag is started (a mouse button is pressed and the mouse is moved), you will package the data to be transferred into a <xref:System.Windows.DataObject>.</span></span> <span data-ttu-id="99da4-148">W takim przypadku kontrolka okrąg będzie pakietu trzy elementy danych; ciąg reprezentujący jego kolor wypełnienia, Podwójna reprezentacja jego wysokości i swoją kopię.</span><span class="sxs-lookup"><span data-stu-id="99da4-148">In this case, the Circle control will package three data items; a string representation of its Fill color, a double representation of its height, and a copy of itself.</span></span>  
  
### <a name="to-initiate-a-drag-and-drop-operation"></a><span data-ttu-id="99da4-149">Aby zainicjować operacji przeciągania i upuszczania</span><span class="sxs-lookup"><span data-stu-id="99da4-149">To initiate a drag-and-drop operation</span></span>  
  
1.  <span data-ttu-id="99da4-150">Otwórz Circle.xaml.cs lub Circle.xaml.vb.</span><span class="sxs-lookup"><span data-stu-id="99da4-150">Open Circle.xaml.cs or Circle.xaml.vb.</span></span>  
  
2.  <span data-ttu-id="99da4-151">Dodaj następujący kod <xref:System.Windows.UIElement.OnMouseMove%2A> należy przesłonić, aby zapewnić obsługę klasy dla <xref:System.Windows.UIElement.MouseMove> zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="99da4-151">Add the following <xref:System.Windows.UIElement.OnMouseMove%2A> override to provide class handling for the <xref:System.Windows.UIElement.MouseMove> event.</span></span>  
  
     [!code-csharp[DragDropWalkthrough#OnMouseMove](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#onmousemove)]
     [!code-vb[DragDropWalkthrough#OnMouseMove](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#onmousemove)]  
  
     <span data-ttu-id="99da4-152">To <xref:System.Windows.UIElement.OnMouseMove%2A> zastąpienie wykonuje następujące zadania:</span><span class="sxs-lookup"><span data-stu-id="99da4-152">This <xref:System.Windows.UIElement.OnMouseMove%2A> override performs the following tasks:</span></span>  
  
    -   <span data-ttu-id="99da4-153">Sprawdza, czy naciśnięciu lewego przycisku myszy, gdy wskaźnik myszy porusza się.</span><span class="sxs-lookup"><span data-stu-id="99da4-153">Checks whether the left mouse button is pressed while the mouse is moving.</span></span>  
  
    -   <span data-ttu-id="99da4-154">Pakiety danych okrąg do <xref:System.Windows.DataObject>.</span><span class="sxs-lookup"><span data-stu-id="99da4-154">Packages the Circle data into a <xref:System.Windows.DataObject>.</span></span> <span data-ttu-id="99da4-155">W takim przypadku kontrolka okrąg pakietów trzy elementy danych; ciąg reprezentujący jego kolor wypełnienia, Podwójna reprezentacja jego wysokości i swoją kopię.</span><span class="sxs-lookup"><span data-stu-id="99da4-155">In this case, the Circle control packages three data items; a string representation of its Fill color, a double representation of its height, and a copy of itself.</span></span>  
  
    -   <span data-ttu-id="99da4-156">Wywołuje statyczną <xref:System.Windows.DragDrop.DoDragDrop%2A?displayProperty=nameWithType> metodę, aby zainicjować operację przeciągania i upuszczania.</span><span class="sxs-lookup"><span data-stu-id="99da4-156">Calls the static <xref:System.Windows.DragDrop.DoDragDrop%2A?displayProperty=nameWithType> method to initiate the drag-and-drop operation.</span></span> <span data-ttu-id="99da4-157">Przekaż następujące trzy parametry, aby <xref:System.Windows.DragDrop.DoDragDrop%2A> metody:</span><span class="sxs-lookup"><span data-stu-id="99da4-157">You pass the following three parameters to the <xref:System.Windows.DragDrop.DoDragDrop%2A> method:</span></span>  
  
        -   <span data-ttu-id="99da4-158">`dragSource` — Odwołanie do tego formantu.</span><span class="sxs-lookup"><span data-stu-id="99da4-158">`dragSource` – A reference to this control.</span></span>  
  
        -   <span data-ttu-id="99da4-159">`data` — <xref:System.Windows.DataObject> Utworzony w poprzednim kodzie.</span><span class="sxs-lookup"><span data-stu-id="99da4-159">`data` – The <xref:System.Windows.DataObject> created in the previous code.</span></span>  
  
        -   <span data-ttu-id="99da4-160">`allowedEffects` Dozwolone operacje przeciągania i upuszczania, które są <xref:System.Windows.DragDropEffects.Copy> lub <xref:System.Windows.DragDropEffects.Move>.</span><span class="sxs-lookup"><span data-stu-id="99da4-160">`allowedEffects` – The allowed drag-and-drop operations, which are <xref:System.Windows.DragDropEffects.Copy> or <xref:System.Windows.DragDropEffects.Move>.</span></span>  
  
3.  <span data-ttu-id="99da4-161">Naciśnij klawisz F5, aby skompilować i uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="99da4-161">Press F5 to build and run the application.</span></span>  
  
4.  <span data-ttu-id="99da4-162">Kliknij jeden z formantów okrąg i przeciągnij go za pośrednictwem paneli, okrąg, a <xref:System.Windows.Controls.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="99da4-162">Click one of the Circle controls and drag it over the panels, the other Circle, and the <xref:System.Windows.Controls.TextBox>.</span></span> <span data-ttu-id="99da4-163">Podczas przeciągania przez <xref:System.Windows.Controls.TextBox>, zmiany kursor do wskazania przejście.</span><span class="sxs-lookup"><span data-stu-id="99da4-163">When dragging over the <xref:System.Windows.Controls.TextBox>, the cursor changes to indicate a move.</span></span>  
  
5.  <span data-ttu-id="99da4-164">Podczas przeciągania okręgu za pośrednictwem <xref:System.Windows.Controls.TextBox>, naciśnij klawisz CTRL.</span><span class="sxs-lookup"><span data-stu-id="99da4-164">While dragging a Circle over the <xref:System.Windows.Controls.TextBox>, press the CTRL key.</span></span> <span data-ttu-id="99da4-165">Zwróć uwagę, jak kursor zmienia się do wskazania kopię.</span><span class="sxs-lookup"><span data-stu-id="99da4-165">Notice how the cursor changes to indicate a copy.</span></span>  
  
6.  <span data-ttu-id="99da4-166">Przeciąganie i upuszczanie koła na <xref:System.Windows.Controls.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="99da4-166">Drag and drop a Circle onto the <xref:System.Windows.Controls.TextBox>.</span></span> <span data-ttu-id="99da4-167">Kolor wypełnienia koła reprezentację ciągu jest dołączany do <xref:System.Windows.Controls.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="99da4-167">The string representation of the Circle’s fill color is appended to the <xref:System.Windows.Controls.TextBox>.</span></span>  
  
     <span data-ttu-id="99da4-168">![Ciąg reprezentujący kolor wypełnienia koła](../../../../docs/framework/wpf/advanced/media/dragdrop-colorstring.png "DragDrop_ColorString")</span><span class="sxs-lookup"><span data-stu-id="99da4-168">![String representation of Circle's fill color](../../../../docs/framework/wpf/advanced/media/dragdrop-colorstring.png "DragDrop_ColorString")</span></span>  
  
 <span data-ttu-id="99da4-169">Domyślnie kursor zmieni się podczas operacji przeciągania i upuszczania, aby wskazać, będzie miał wpływ, jaki usunięcie danych.</span><span class="sxs-lookup"><span data-stu-id="99da4-169">By default, the cursor will change during a drag-and-drop operation to indicate what effect dropping the data will have.</span></span> <span data-ttu-id="99da4-170">Można dostosować zwrotnych użytkownikowi obsługi <xref:System.Windows.UIElement.GiveFeedback> zdarzeń i ustawianie różnych kursora.</span><span class="sxs-lookup"><span data-stu-id="99da4-170">You can customize the feedback given to the user by handling the <xref:System.Windows.UIElement.GiveFeedback> event and setting a different cursor.</span></span>  
  
### <a name="to-give-feedback-to-the-user"></a><span data-ttu-id="99da4-171">Aby przesłać opinię dla użytkownika</span><span class="sxs-lookup"><span data-stu-id="99da4-171">To give feedback to the user</span></span>  
  
1.  <span data-ttu-id="99da4-172">Otwórz Circle.xaml.cs lub Circle.xaml.vb.</span><span class="sxs-lookup"><span data-stu-id="99da4-172">Open Circle.xaml.cs or Circle.xaml.vb.</span></span>  
  
2.  <span data-ttu-id="99da4-173">Dodaj następujący kod <xref:System.Windows.UIElement.OnGiveFeedback%2A> należy przesłonić, aby zapewnić obsługę klasy dla <xref:System.Windows.UIElement.GiveFeedback> zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="99da4-173">Add the following <xref:System.Windows.UIElement.OnGiveFeedback%2A> override to provide class handling for the <xref:System.Windows.UIElement.GiveFeedback> event.</span></span>  
  
     [!code-csharp[DragDropWalkthrough#OnGiveFeedback](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#ongivefeedback)]
     [!code-vb[DragDropWalkthrough#OnGiveFeedback](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#ongivefeedback)]  
  
     <span data-ttu-id="99da4-174">To <xref:System.Windows.UIElement.OnGiveFeedback%2A> zastąpienie wykonuje następujące zadania:</span><span class="sxs-lookup"><span data-stu-id="99da4-174">This <xref:System.Windows.UIElement.OnGiveFeedback%2A> override performs the following tasks:</span></span>  
  
    -   <span data-ttu-id="99da4-175">Sprawdza, czy <xref:System.Windows.GiveFeedbackEventArgs.Effects%2A> wartości, które są ustawiane w element docelowy upuszczania <xref:System.Windows.UIElement.DragOver> programu obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="99da4-175">Checks the <xref:System.Windows.GiveFeedbackEventArgs.Effects%2A> values that are set in the drop target's <xref:System.Windows.UIElement.DragOver> event handler.</span></span>  
  
    -   <span data-ttu-id="99da4-176">Ustawia kursor niestandardowych, na podstawie <xref:System.Windows.GiveFeedbackEventArgs.Effects%2A> wartości.</span><span class="sxs-lookup"><span data-stu-id="99da4-176">Sets a custom cursor based on the <xref:System.Windows.GiveFeedbackEventArgs.Effects%2A> value.</span></span> <span data-ttu-id="99da4-177">Kursor jest przeznaczona do przekazać wizualną opinię użytkownikowi o będzie mieć wpływ, jaki usunięcie danych.</span><span class="sxs-lookup"><span data-stu-id="99da4-177">The cursor is intended to give visual feedback to the user about what effect dropping the data will have.</span></span>  
  
3.  <span data-ttu-id="99da4-178">Naciśnij klawisz F5, aby skompilować i uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="99da4-178">Press F5 to build and run the application.</span></span>  
  
4.  <span data-ttu-id="99da4-179">Przeciągnij jeden z okręgów kontroluje za pośrednictwem paneli, okrąg, a <xref:System.Windows.Controls.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="99da4-179">Drag one of the Circle controls over the panels, the other Circle, and the <xref:System.Windows.Controls.TextBox>.</span></span> <span data-ttu-id="99da4-180">Zauważ, że kursory są teraz kursorów niestandardowych, które określiłeś w <xref:System.Windows.UIElement.OnGiveFeedback%2A> zastąpienia.</span><span class="sxs-lookup"><span data-stu-id="99da4-180">Notice that the cursors are now the custom cursors that you specified in the <xref:System.Windows.UIElement.OnGiveFeedback%2A> override.</span></span>  
  
     <span data-ttu-id="99da4-181">![Przeciąganie i upuszczanie za pomocą niestandardowych kursorów](../../../../docs/framework/wpf/advanced/media/dragdrop-customcursor.png "DragDrop_CustomCursor")</span><span class="sxs-lookup"><span data-stu-id="99da4-181">![Drag and drop with custom cursors](../../../../docs/framework/wpf/advanced/media/dragdrop-customcursor.png "DragDrop_CustomCursor")</span></span>  
  
5.  <span data-ttu-id="99da4-182">Zaznacz tekst `green` z <xref:System.Windows.Controls.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="99da4-182">Select the text `green` from the <xref:System.Windows.Controls.TextBox>.</span></span>  
  
6.  <span data-ttu-id="99da4-183">Przeciągnij `green` tekst do kontrolki okrąg.</span><span class="sxs-lookup"><span data-stu-id="99da4-183">Drag the `green` text to a Circle control.</span></span> <span data-ttu-id="99da4-184">Zauważ, że kursory domyślny są wyświetlane w celu wskazania skutków operacji przeciągania i upuszczania.</span><span class="sxs-lookup"><span data-stu-id="99da4-184">Notice that the default cursors are shown to indicate the effects of the drag-and-drop operation.</span></span> <span data-ttu-id="99da4-185">Kursor opinie zawsze jest ustawiany przez elementem źródłowym przeciągania.</span><span class="sxs-lookup"><span data-stu-id="99da4-185">The feedback cursor is always set by the drag source.</span></span>  
  
## <a name="implementing-drop-target-events-in-the-user-control"></a><span data-ttu-id="99da4-186">Implementowanie docelowego upuszczania w kontrolce użytkownika</span><span class="sxs-lookup"><span data-stu-id="99da4-186">Implementing Drop Target Events in the User Control</span></span>  
 <span data-ttu-id="99da4-187">W tej sekcji określisz, że kontrolka użytkownika znajduje się miejsca docelowego, zastąpienie metody, które umożliwia użytkownikowi kontrolowanie jako miejsca docelowego i przetwarzania danych, który został upuszczony na nim.</span><span class="sxs-lookup"><span data-stu-id="99da4-187">In this section, you will specify that the user control is a drop target, override the methods that enable the user control to be a drop target, and process the data that is dropped on it.</span></span>  
  
### <a name="to-enable-the-user-control-to-be-a-drop-target"></a><span data-ttu-id="99da4-188">Aby włączyć funkcję Kontrola użytkownika jako miejsca docelowego</span><span class="sxs-lookup"><span data-stu-id="99da4-188">To enable the user control to be a drop target</span></span>  
  
1.  <span data-ttu-id="99da4-189">Open Circle.xaml.</span><span class="sxs-lookup"><span data-stu-id="99da4-189">Open Circle.xaml.</span></span>  
  
2.  <span data-ttu-id="99da4-190">W przypadku otwarcia <xref:System.Windows.Controls.UserControl> tagów, należy dodać <xref:System.Windows.UIElement.AllowDrop%2A> właściwości i ustaw ją na `true`.</span><span class="sxs-lookup"><span data-stu-id="99da4-190">In the opening <xref:System.Windows.Controls.UserControl> tag, add the <xref:System.Windows.UIElement.AllowDrop%2A> property and set it to `true`.</span></span>  
  
     [!code-xaml[DragDropWalkthrough#UCTagXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml#uctagxaml)]  
  
 <span data-ttu-id="99da4-191"><xref:System.Windows.UIElement.OnDrop%2A> Metoda jest wywoływana, gdy <xref:System.Windows.UIElement.AllowDrop%2A> właściwość jest ustawiona na `true` i dane ze źródła przeciągania został upuszczony na formant użytkownika okrąg.</span><span class="sxs-lookup"><span data-stu-id="99da4-191">The <xref:System.Windows.UIElement.OnDrop%2A> method is called when the <xref:System.Windows.UIElement.AllowDrop%2A> property is set to `true` and data from the drag source is dropped on the Circle user control.</span></span> <span data-ttu-id="99da4-192">W przypadku tej metody spowoduje przetwarzania danych, który został upuszczony i zastosować je do koła.</span><span class="sxs-lookup"><span data-stu-id="99da4-192">In this method, you will process the data that was dropped and apply the data to the Circle.</span></span>  
  
### <a name="to-process-the-dropped-data"></a><span data-ttu-id="99da4-193">Do przetwarzania elementów usuniętych danych</span><span class="sxs-lookup"><span data-stu-id="99da4-193">To process the dropped data</span></span>  
  
1.  <span data-ttu-id="99da4-194">Otwórz Circle.xaml.cs lub Circle.xaml.vb.</span><span class="sxs-lookup"><span data-stu-id="99da4-194">Open Circle.xaml.cs or Circle.xaml.vb.</span></span>  
  
2.  <span data-ttu-id="99da4-195">Dodaj następujący kod <xref:System.Windows.UIElement.OnDrop%2A> należy przesłonić, aby zapewnić obsługę klasy dla <xref:System.Windows.UIElement.Drop> zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="99da4-195">Add the following <xref:System.Windows.UIElement.OnDrop%2A> override to provide class handling for the <xref:System.Windows.UIElement.Drop> event.</span></span>  
  
     [!code-csharp[DragDropWalkthrough#OnDrop](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#ondrop)]
     [!code-vb[DragDropWalkthrough#OnDrop](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#ondrop)]  
  
     <span data-ttu-id="99da4-196">To <xref:System.Windows.UIElement.OnDrop%2A> zastąpienie wykonuje następujące zadania:</span><span class="sxs-lookup"><span data-stu-id="99da4-196">This <xref:System.Windows.UIElement.OnDrop%2A> override performs the following tasks:</span></span>  
  
    -   <span data-ttu-id="99da4-197">Używa <xref:System.Windows.DataObject.GetDataPresent%2A> metodę sprawdzania, czy przeciąganego danych zawiera obiekt ciągu.</span><span class="sxs-lookup"><span data-stu-id="99da4-197">Uses the <xref:System.Windows.DataObject.GetDataPresent%2A> method to check if the dragged data contains a string object.</span></span>  
  
    -   <span data-ttu-id="99da4-198">Używa <xref:System.Windows.DataObject.GetData%2A> metodę, aby wyodrębnić dane ciągu, jeśli jest obecny.</span><span class="sxs-lookup"><span data-stu-id="99da4-198">Uses the <xref:System.Windows.DataObject.GetData%2A> method to extract the string data if it is present.</span></span>  
  
    -   <span data-ttu-id="99da4-199">Używa <xref:System.Windows.Media.BrushConverter> próbował przekonwertować ciąg do <xref:System.Windows.Media.Brush>.</span><span class="sxs-lookup"><span data-stu-id="99da4-199">Uses a <xref:System.Windows.Media.BrushConverter> to try to convert the string to a <xref:System.Windows.Media.Brush>.</span></span>  
  
    -   <span data-ttu-id="99da4-200">Jeśli konwersja się powiedzie, ma zastosowanie pędzla, który ma <xref:System.Windows.Shapes.Shape.Fill%2A> z <xref:System.Windows.Shapes.Ellipse> zapewniający interfejsu użytkownika formantu okrąg.</span><span class="sxs-lookup"><span data-stu-id="99da4-200">If the conversion is successful, applies the brush to the <xref:System.Windows.Shapes.Shape.Fill%2A> of the <xref:System.Windows.Shapes.Ellipse> that provides the UI of the Circle control.</span></span>  
  
    -   <span data-ttu-id="99da4-201">Znaczniki <xref:System.Windows.UIElement.Drop> zdarzeń jako obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="99da4-201">Marks the <xref:System.Windows.UIElement.Drop> event as handled.</span></span> <span data-ttu-id="99da4-202">Zdarzenie upuszczania należy oznaczyć jako obsłużony, dzięki czemu inne elementy, które odbierają to zdarzenie wiadomo, kontrolki użytkownika okrąg obsługiwania go.</span><span class="sxs-lookup"><span data-stu-id="99da4-202">You should mark the drop event as handled so that other elements that receive this event know that the Circle user control handled it.</span></span>  
  
3.  <span data-ttu-id="99da4-203">Naciśnij klawisz F5, aby skompilować i uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="99da4-203">Press F5 to build and run the application.</span></span>  
  
4.  <span data-ttu-id="99da4-204">Zaznacz tekst `green` w <xref:System.Windows.Controls.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="99da4-204">Select the text `green` in the <xref:System.Windows.Controls.TextBox>.</span></span>  
  
5.  <span data-ttu-id="99da4-205">Przeciągnij tekst do kontrolki okrąg i upuść go.</span><span class="sxs-lookup"><span data-stu-id="99da4-205">Drag the text to a Circle control and drop it.</span></span> <span data-ttu-id="99da4-206">Koło zmienia się od niebieskiego na zielony.</span><span class="sxs-lookup"><span data-stu-id="99da4-206">The Circle changes from blue to green.</span></span>  
  
     <span data-ttu-id="99da4-207">![Konwertowanie ciągu pędzel](../../../../docs/framework/wpf/advanced/media/dragdrop-dropgreentext.png "DragDrop_DropGreenText")</span><span class="sxs-lookup"><span data-stu-id="99da4-207">![Convert a string to a brush](../../../../docs/framework/wpf/advanced/media/dragdrop-dropgreentext.png "DragDrop_DropGreenText")</span></span>  
  
6.  <span data-ttu-id="99da4-208">Wpisz tekst `green` w <xref:System.Windows.Controls.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="99da4-208">Type the text `green` in the <xref:System.Windows.Controls.TextBox>.</span></span>  
  
7.  <span data-ttu-id="99da4-209">Zaznacz tekst `gre` w <xref:System.Windows.Controls.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="99da4-209">Select the text `gre` in the <xref:System.Windows.Controls.TextBox>.</span></span>  
  
8.  <span data-ttu-id="99da4-210">Przeciągnij go do kontroli okrąg i upuść go.</span><span class="sxs-lookup"><span data-stu-id="99da4-210">Drag it to a Circle control and drop it.</span></span> <span data-ttu-id="99da4-211">Należy zauważyć, że kursor zmienia się na wskazują, że listy jest dozwolone, ale nie zmienia kolor koła, ponieważ `gre` nie jest prawidłowym kolorem.</span><span class="sxs-lookup"><span data-stu-id="99da4-211">Notice that the cursor changes to indicate that the drop is allowed, but the color of the Circle does not change because `gre` is not a valid color.</span></span>  
  
9. <span data-ttu-id="99da4-212">Przeciągnij z zielonym kontroli okrąg i upuść na niebieski sterowania okrąg.</span><span class="sxs-lookup"><span data-stu-id="99da4-212">Drag from the green Circle control and drop on the blue Circle control.</span></span> <span data-ttu-id="99da4-213">Koło zmienia się od niebieskiego na zielony.</span><span class="sxs-lookup"><span data-stu-id="99da4-213">The Circle changes from blue to green.</span></span> <span data-ttu-id="99da4-214">Należy zauważyć, że jest wyświetlany kursor, który jest zależny od tego, czy <xref:System.Windows.Controls.TextBox> lub koła jest elementem źródłowym przeciągania.</span><span class="sxs-lookup"><span data-stu-id="99da4-214">Notice that which cursor is shown depends on whether the <xref:System.Windows.Controls.TextBox> or the Circle is the drag source.</span></span>  
  
 <span data-ttu-id="99da4-215">Ustawienie <xref:System.Windows.UIElement.AllowDrop%2A> właściwość `true` i przetwarzanie danych porzuconych wszystko, co jest wymagane do włączenia elementu do miejsca docelowego.</span><span class="sxs-lookup"><span data-stu-id="99da4-215">Setting the <xref:System.Windows.UIElement.AllowDrop%2A> property to `true` and processing the dropped data is all that is required to enable an element to be a drop target.</span></span> <span data-ttu-id="99da4-216">Jednakże, aby zapewnić lepsze środowisko użytkownika, należy również obsługiwać <xref:System.Windows.UIElement.DragEnter>, <xref:System.Windows.UIElement.DragLeave>, i <xref:System.Windows.UIElement.DragOver> zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="99da4-216">However, to provide a better user experience, you should also handle the <xref:System.Windows.UIElement.DragEnter>, <xref:System.Windows.UIElement.DragLeave>, and <xref:System.Windows.UIElement.DragOver> events.</span></span> <span data-ttu-id="99da4-217">W ramach tych zdarzeń można wykonać testy i Prześlij dodatkową opinię do użytkownika, zanim danych zostało porzucone.</span><span class="sxs-lookup"><span data-stu-id="99da4-217">In these events, you can perform checks and provide additional feedback to the user before the data is dropped.</span></span>  
  
 <span data-ttu-id="99da4-218">Po danych jest przeciągany nad kontrolki użytkownika koła, formant powinien Powiadom elementem źródłowym przeciągania czy może przetworzyć dane, które przeciągania.</span><span class="sxs-lookup"><span data-stu-id="99da4-218">When data is dragged over the Circle user control, the control should notify the drag source whether it can process the data that is being dragged.</span></span> <span data-ttu-id="99da4-219">Jeśli formant nie potrafi do przetwarzania danych, należy go odmówić listy.</span><span class="sxs-lookup"><span data-stu-id="99da4-219">If the control does not know how to process the data, it should refuse the drop.</span></span> <span data-ttu-id="99da4-220">Aby to zrobić, będziesz obsługiwać <xref:System.Windows.UIElement.DragOver> zdarzeń i ustaw <xref:System.Windows.DragEventArgs.Effects%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="99da4-220">To do this, you will handle the <xref:System.Windows.UIElement.DragOver> event and set the <xref:System.Windows.DragEventArgs.Effects%2A> property.</span></span>  
  
### <a name="to-verify-that-the-data-drop-is-allowed"></a><span data-ttu-id="99da4-221">Aby sprawdzić, czy listy danych jest dozwolone</span><span class="sxs-lookup"><span data-stu-id="99da4-221">To verify that the data drop is allowed</span></span>  
  
1.  <span data-ttu-id="99da4-222">Otwórz Circle.xaml.cs lub Circle.xaml.vb.</span><span class="sxs-lookup"><span data-stu-id="99da4-222">Open Circle.xaml.cs or Circle.xaml.vb.</span></span>  
  
2.  <span data-ttu-id="99da4-223">Dodaj następujący kod <xref:System.Windows.UIElement.OnDragOver%2A> należy przesłonić, aby zapewnić obsługę klasy dla <xref:System.Windows.UIElement.DragOver> zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="99da4-223">Add the following <xref:System.Windows.UIElement.OnDragOver%2A> override to provide class handling for the <xref:System.Windows.UIElement.DragOver> event.</span></span>  
  
     [!code-csharp[DragDropWalkthrough#OnDragOver](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#ondragover)]
     [!code-vb[DragDropWalkthrough#OnDragOver](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#ondragover)]  
  
     <span data-ttu-id="99da4-224">To <xref:System.Windows.UIElement.OnDragOver%2A> zastąpienie wykonuje następujące zadania:</span><span class="sxs-lookup"><span data-stu-id="99da4-224">This <xref:System.Windows.UIElement.OnDragOver%2A> override performs the following tasks:</span></span>  
  
    -   <span data-ttu-id="99da4-225">Zestawy <xref:System.Windows.DragEventArgs.Effects%2A> właściwość <xref:System.Windows.DragDropEffects.None>.</span><span class="sxs-lookup"><span data-stu-id="99da4-225">Sets the <xref:System.Windows.DragEventArgs.Effects%2A> property to <xref:System.Windows.DragDropEffects.None>.</span></span>  
  
    -   <span data-ttu-id="99da4-226">Wykonuje ten sam testów, które są wykonywane w ramach <xref:System.Windows.UIElement.OnDrop%2A> metodę pozwala ustalić, czy okrąg kontrolki użytkownika można przetwarzać dane przeciąganego.</span><span class="sxs-lookup"><span data-stu-id="99da4-226">Performs the same checks that are performed in the <xref:System.Windows.UIElement.OnDrop%2A> method to determine whether the Circle user control can process the dragged data.</span></span>  
  
    -   <span data-ttu-id="99da4-227">Jeśli kontrolka użytkownika może przetwarzać dane, ustawia <xref:System.Windows.DragEventArgs.Effects%2A> właściwości <xref:System.Windows.DragDropEffects.Copy> lub <xref:System.Windows.DragDropEffects.Move>.</span><span class="sxs-lookup"><span data-stu-id="99da4-227">If the user control can process the data, sets the <xref:System.Windows.DragEventArgs.Effects%2A> property to <xref:System.Windows.DragDropEffects.Copy> or <xref:System.Windows.DragDropEffects.Move>.</span></span>  
  
3.  <span data-ttu-id="99da4-228">Naciśnij klawisz F5, aby skompilować i uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="99da4-228">Press F5 to build and run the application.</span></span>  
  
4.  <span data-ttu-id="99da4-229">Zaznacz tekst `gre` w <xref:System.Windows.Controls.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="99da4-229">Select the text `gre` in the <xref:System.Windows.Controls.TextBox>.</span></span>  
  
5.  <span data-ttu-id="99da4-230">Przeciągnij tekst do kontrolki okrąg.</span><span class="sxs-lookup"><span data-stu-id="99da4-230">Drag the text to a Circle control.</span></span> <span data-ttu-id="99da4-231">Należy zauważyć, że kursor zmienia się teraz do wskazania, że listy jest niedozwolona, ponieważ `gre` nie jest prawidłowym kolorem.</span><span class="sxs-lookup"><span data-stu-id="99da4-231">Notice that the cursor now changes to indicate that the drop is not allowed because `gre` is not a valid color.</span></span>  
  
 <span data-ttu-id="99da4-232">Może dodatkowo ulepszyć środowisko użytkownika, stosując Podgląd wykonać operacji usuwania.</span><span class="sxs-lookup"><span data-stu-id="99da4-232">You can further enhance the user experience by applying a preview of the drop operation.</span></span> <span data-ttu-id="99da4-233">Kontrolki użytkownika koła, spowoduje to zastąpienie <xref:System.Windows.UIElement.OnDragEnter%2A> i <xref:System.Windows.UIElement.OnDragLeave%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="99da4-233">For the Circle user control, you will override the <xref:System.Windows.UIElement.OnDragEnter%2A> and <xref:System.Windows.UIElement.OnDragLeave%2A> methods.</span></span> <span data-ttu-id="99da4-234">Jeśli danych jest przeciągnięty ponad kontrolką, bieżące tło <xref:System.Windows.Shapes.Shape.Fill%2A> są zapisywane w zmiennej symbol zastępczy.</span><span class="sxs-lookup"><span data-stu-id="99da4-234">When the data is dragged over the control, the current background <xref:System.Windows.Shapes.Shape.Fill%2A> is saved in a placeholder variable.</span></span> <span data-ttu-id="99da4-235">Ciąg jest konwertowany na pędzel i zastosowane do <xref:System.Windows.Shapes.Ellipse> zapewniający koła interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="99da4-235">The string is then converted to a brush and applied to the <xref:System.Windows.Shapes.Ellipse> that provides the Circle's UI.</span></span> <span data-ttu-id="99da4-236">Jeśli danych jest przeciągnąć poza okręgu bez Trwa porzucanie, oryginalnym <xref:System.Windows.Shapes.Shape.Fill%2A> wartość jest ponownie zastosować koła.</span><span class="sxs-lookup"><span data-stu-id="99da4-236">If the data is dragged out of the Circle without being dropped, the original <xref:System.Windows.Shapes.Shape.Fill%2A> value is re-applied to the Circle.</span></span>  
  
### <a name="to-preview-the-effects-of-the-drag-and-drop-operation"></a><span data-ttu-id="99da4-237">Aby wyświetlić podgląd skutków operacji przeciągania i upuszczania</span><span class="sxs-lookup"><span data-stu-id="99da4-237">To preview the effects of the drag-and-drop operation</span></span>  
  
1.  <span data-ttu-id="99da4-238">Otwórz Circle.xaml.cs lub Circle.xaml.vb.</span><span class="sxs-lookup"><span data-stu-id="99da4-238">Open Circle.xaml.cs or Circle.xaml.vb.</span></span>  
  
2.  <span data-ttu-id="99da4-239">W klasie Circle zadeklarować prywatnej <xref:System.Windows.Media.Brush> zmiennej o nazwie `_previousFill` i zainicjować jej do `null`.</span><span class="sxs-lookup"><span data-stu-id="99da4-239">In the Circle class, declare a private <xref:System.Windows.Media.Brush> variable named `_previousFill` and initialize it to `null`.</span></span>  
  
     [!code-csharp[DragDropWalkthrough#Brush](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#brush)]
     [!code-vb[DragDropWalkthrough#Brush](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#brush)]  
  
3.  <span data-ttu-id="99da4-240">Dodaj następujący kod <xref:System.Windows.UIElement.OnDragEnter%2A> należy przesłonić, aby zapewnić obsługę klasy dla <xref:System.Windows.UIElement.DragEnter> zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="99da4-240">Add the following <xref:System.Windows.UIElement.OnDragEnter%2A> override to provide class handling for the <xref:System.Windows.UIElement.DragEnter> event.</span></span>  
  
     [!code-csharp[DragDropWalkthrough#OnDragEnter](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#ondragenter)]
     [!code-vb[DragDropWalkthrough#OnDragEnter](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#ondragenter)]  
  
     <span data-ttu-id="99da4-241">To <xref:System.Windows.UIElement.OnDragEnter%2A> zastąpienie wykonuje następujące zadania:</span><span class="sxs-lookup"><span data-stu-id="99da4-241">This <xref:System.Windows.UIElement.OnDragEnter%2A> override performs the following tasks:</span></span>  
  
    -   <span data-ttu-id="99da4-242">Zapisuje <xref:System.Windows.Shapes.Shape.Fill%2A> właściwość <xref:System.Windows.Shapes.Ellipse> w `_previousFill` zmiennej.</span><span class="sxs-lookup"><span data-stu-id="99da4-242">Saves the <xref:System.Windows.Shapes.Shape.Fill%2A> property of the <xref:System.Windows.Shapes.Ellipse> in the `_previousFill` variable.</span></span>  
  
    -   <span data-ttu-id="99da4-243">Wykonuje ten sam testów, które są wykonywane w ramach <xref:System.Windows.UIElement.OnDrop%2A> metodę pozwala ustalić, czy dane mogą być konwertowane na <xref:System.Windows.Media.Brush>.</span><span class="sxs-lookup"><span data-stu-id="99da4-243">Performs the same checks that are performed in the <xref:System.Windows.UIElement.OnDrop%2A> method to determine whether the data can be converted to a <xref:System.Windows.Media.Brush>.</span></span>  
  
    -   <span data-ttu-id="99da4-244">Jeśli danych jest konwertowany na prawidłowym <xref:System.Windows.Media.Brush>, stosuje ją do <xref:System.Windows.Shapes.Shape.Fill%2A> z <xref:System.Windows.Shapes.Ellipse>.</span><span class="sxs-lookup"><span data-stu-id="99da4-244">If the data is converted to a valid <xref:System.Windows.Media.Brush>, applies it to the <xref:System.Windows.Shapes.Shape.Fill%2A> of the <xref:System.Windows.Shapes.Ellipse>.</span></span>  
  
4.  <span data-ttu-id="99da4-245">Dodaj następujący kod <xref:System.Windows.UIElement.OnDragLeave%2A> należy przesłonić, aby zapewnić obsługę klasy dla <xref:System.Windows.UIElement.DragLeave> zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="99da4-245">Add the following <xref:System.Windows.UIElement.OnDragLeave%2A> override to provide class handling for the <xref:System.Windows.UIElement.DragLeave> event.</span></span>  
  
     [!code-csharp[DragDropWalkthrough#OnDragLeave](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#ondragleave)]
     [!code-vb[DragDropWalkthrough#OnDragLeave](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#ondragleave)]  
  
     <span data-ttu-id="99da4-246">To <xref:System.Windows.UIElement.OnDragLeave%2A> zastąpienie wykonuje następujące zadania:</span><span class="sxs-lookup"><span data-stu-id="99da4-246">This <xref:System.Windows.UIElement.OnDragLeave%2A> override performs the following tasks:</span></span>  
  
    -   <span data-ttu-id="99da4-247">Stosuje <xref:System.Windows.Media.Brush> zapisane w `_previousFill` zmienną <xref:System.Windows.Shapes.Shape.Fill%2A> z <xref:System.Windows.Shapes.Ellipse> zapewniający interfejsu użytkownika formantu użytkownika okrąg.</span><span class="sxs-lookup"><span data-stu-id="99da4-247">Applies the <xref:System.Windows.Media.Brush> saved in the `_previousFill` variable to the <xref:System.Windows.Shapes.Shape.Fill%2A> of the <xref:System.Windows.Shapes.Ellipse> that provides the UI of the Circle user control.</span></span>  
  
5.  <span data-ttu-id="99da4-248">Naciśnij klawisz F5, aby skompilować i uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="99da4-248">Press F5 to build and run the application.</span></span>  
  
6.  <span data-ttu-id="99da4-249">Zaznacz tekst `green` w <xref:System.Windows.Controls.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="99da4-249">Select the text `green` in the <xref:System.Windows.Controls.TextBox>.</span></span>  
  
7.  <span data-ttu-id="99da4-250">Przeciągnij tekst nad formantem koła, bez usuwania go.</span><span class="sxs-lookup"><span data-stu-id="99da4-250">Drag the text over a Circle control without dropping it.</span></span> <span data-ttu-id="99da4-251">Koło zmienia się od niebieskiego na zielony.</span><span class="sxs-lookup"><span data-stu-id="99da4-251">The Circle changes from blue to green.</span></span>  
  
     <span data-ttu-id="99da4-252">![Efekty przeciągnij&#45;i&#45;porzucić operacji](../../../../docs/framework/wpf/advanced/media/dragdrop-previeweffects.png "DragDrop_PreviewEffects")</span><span class="sxs-lookup"><span data-stu-id="99da4-252">![Preview the effects of a drag&#45;and&#45;drop operation](../../../../docs/framework/wpf/advanced/media/dragdrop-previeweffects.png "DragDrop_PreviewEffects")</span></span>  
  
8.  <span data-ttu-id="99da4-253">Przeciągnij tekst od kontroli okrąg.</span><span class="sxs-lookup"><span data-stu-id="99da4-253">Drag the text away from the Circle control.</span></span> <span data-ttu-id="99da4-254">Koło zmienia się z zielonym kopii na niebieski.</span><span class="sxs-lookup"><span data-stu-id="99da4-254">The Circle changes from green back to blue.</span></span>  
  
## <a name="enabling-a-panel-to-receive-dropped-data"></a><span data-ttu-id="99da4-255">Włączanie panelu otrzymać porzucony danych</span><span class="sxs-lookup"><span data-stu-id="99da4-255">Enabling a Panel to Receive Dropped Data</span></span>  
 <span data-ttu-id="99da4-256">W tej sekcji spowoduje włączenie paneli, które hostowanie kontrolki użytkownika koła, aby pełnić rolę miejsc docelowych dla przeciąganego danych okrąg.</span><span class="sxs-lookup"><span data-stu-id="99da4-256">In this section, you will enable the panels that host the Circle user controls to act as drop targets for dragged Circle data.</span></span> <span data-ttu-id="99da4-257">Wdroży kod, który umożliwia, aby przenieść jeden panel okrąg lub można utworzyć kopii kontrolki koła, przytrzymując klawisz CTRL podczas przeciągania i upuszczania okrąg.</span><span class="sxs-lookup"><span data-stu-id="99da4-257">You will implement code that enables you to move a Circle from one panel to another, or to make a copy of a Circle control by holding down the CTRL key while dragging and dropping a Circle.</span></span>  
  
### <a name="to-enable-the-panel-to-be-a-drop-target"></a><span data-ttu-id="99da4-258">Aby włączyć panelu jako miejsca docelowego</span><span class="sxs-lookup"><span data-stu-id="99da4-258">To enable the panel to be a drop target</span></span>  
  
1.  <span data-ttu-id="99da4-259">Open MainWindow.xaml.</span><span class="sxs-lookup"><span data-stu-id="99da4-259">Open MainWindow.xaml.</span></span>  
  
2.  <span data-ttu-id="99da4-260">Jak pokazano w poniższym XAML, we wszystkich <xref:System.Windows.Controls.StackPanel> formantów, Dodaj programy obsługi dla <xref:System.Windows.UIElement.DragOver> i <xref:System.Windows.UIElement.Drop> zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="99da4-260">As shown in the following XAML, in each of the <xref:System.Windows.Controls.StackPanel> controls, add handlers for the <xref:System.Windows.UIElement.DragOver> and <xref:System.Windows.UIElement.Drop> events.</span></span> <span data-ttu-id="99da4-261">Nazwa <xref:System.Windows.UIElement.DragOver> programu obsługi zdarzeń `panel_DragOver`i nadaj <xref:System.Windows.UIElement.Drop> programu obsługi zdarzeń `panel_Drop`.</span><span class="sxs-lookup"><span data-stu-id="99da4-261">Name the <xref:System.Windows.UIElement.DragOver> event handler, `panel_DragOver`, and name the <xref:System.Windows.UIElement.Drop> event handler, `panel_Drop`.</span></span>  
  
     [!code-xaml[DragDropWalkthrough#PanelsXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/MainWindow.xaml#panelsxaml)]  
  
3.  <span data-ttu-id="99da4-262">Otwórz MainWindows.xaml.cs lub MainWindow.xaml.vb.</span><span class="sxs-lookup"><span data-stu-id="99da4-262">Open MainWindows.xaml.cs or MainWindow.xaml.vb.</span></span>  
  
4.  <span data-ttu-id="99da4-263">Dodaj następujący kod do <xref:System.Windows.UIElement.DragOver> programu obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="99da4-263">Add the following code for the <xref:System.Windows.UIElement.DragOver> event handler.</span></span>  
  
     [!code-csharp[DragDropWalkthrough#PanelDragOver](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/MainWindow.xaml.cs#paneldragover)]
     [!code-vb[DragDropWalkthrough#PanelDragOver](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/MainWindow.xaml.vb#paneldragover)]  
  
     <span data-ttu-id="99da4-264">To <xref:System.Windows.UIElement.DragOver> program obsługi zdarzeń wykonuje następujące zadania:</span><span class="sxs-lookup"><span data-stu-id="99da4-264">This <xref:System.Windows.UIElement.DragOver> event handler performs the following tasks:</span></span>  
  
    -   <span data-ttu-id="99da4-265">Sprawdza, czy przeciąganego danych zawiera dane "Object", która została spakowana w <xref:System.Windows.DataObject> przez funkcję Kontrola użytkownika okrąg i przekazywane w wywołaniu <xref:System.Windows.DragDrop.DoDragDrop%2A>.</span><span class="sxs-lookup"><span data-stu-id="99da4-265">Checks that the dragged data contains the "Object" data that was packaged in the <xref:System.Windows.DataObject> by the Circle user control and passed in the call to <xref:System.Windows.DragDrop.DoDragDrop%2A>.</span></span>  
  
    -   <span data-ttu-id="99da4-266">Jeśli dane "Object" jest obecny, sprawdza, czy zostanie naciśnięty klawisz CTRL.</span><span class="sxs-lookup"><span data-stu-id="99da4-266">If the "Object" data is present, checks whether the CTRL key is pressed.</span></span>  
  
    -   <span data-ttu-id="99da4-267">Jeśli ta opcja zostanie naciśnięty klawisz CTRL, ustawia <xref:System.Windows.DragEventArgs.Effects%2A> właściwość <xref:System.Windows.DragDropEffects.Copy>.</span><span class="sxs-lookup"><span data-stu-id="99da4-267">If the CTRL key is pressed, sets the <xref:System.Windows.DragEventArgs.Effects%2A> property to <xref:System.Windows.DragDropEffects.Copy>.</span></span> <span data-ttu-id="99da4-268">W przeciwnym wypadku ustaw <xref:System.Windows.DragEventArgs.Effects%2A> właściwość <xref:System.Windows.DragDropEffects.Move>.</span><span class="sxs-lookup"><span data-stu-id="99da4-268">Otherwise, set the <xref:System.Windows.DragEventArgs.Effects%2A> property to <xref:System.Windows.DragDropEffects.Move>.</span></span>  
  
5.  <span data-ttu-id="99da4-269">Dodaj następujący kod do <xref:System.Windows.UIElement.Drop> programu obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="99da4-269">Add the following code for the <xref:System.Windows.UIElement.Drop> event handler.</span></span>  
  
     [!code-csharp[DragDropWalkthrough#PanelDrop](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/MainWindow.xaml.cs#paneldrop)]
     [!code-vb[DragDropWalkthrough#PanelDrop](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/MainWindow.xaml.vb#paneldrop)]  
  
     <span data-ttu-id="99da4-270">To <xref:System.Windows.UIElement.Drop> program obsługi zdarzeń wykonuje następujące zadania:</span><span class="sxs-lookup"><span data-stu-id="99da4-270">This <xref:System.Windows.UIElement.Drop> event handler performs the following tasks:</span></span>  
  
    -   <span data-ttu-id="99da4-271">Sprawdza, czy <xref:System.Windows.UIElement.Drop> zdarzenie jest już obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="99da4-271">Checks whether the <xref:System.Windows.UIElement.Drop> event has already been handled.</span></span> <span data-ttu-id="99da4-272">Na przykład po przerwaniu koła na innym koło, które obsługuje <xref:System.Windows.UIElement.Drop> zdarzenia mają być panel, który zawiera koła, również go obsłużyć.</span><span class="sxs-lookup"><span data-stu-id="99da4-272">For instance, if a Circle is dropped on another Circle which handles the <xref:System.Windows.UIElement.Drop> event, you do not want the panel that contains the Circle to also handle it.</span></span>  
  
    -   <span data-ttu-id="99da4-273">Jeśli <xref:System.Windows.UIElement.Drop> zdarzeń nie jest obsługiwany, sprawdza, czy zostanie naciśnięty klawisz CTRL.</span><span class="sxs-lookup"><span data-stu-id="99da4-273">If the <xref:System.Windows.UIElement.Drop> event is not handled, checks whether the CTRL key is pressed.</span></span>  
  
    -   <span data-ttu-id="99da4-274">Jeśli po naciśnięciu klawisza CTRL <xref:System.Windows.UIElement.Drop> się stanie, sprawia, że kopia okręgu kontroli i dodać go do <xref:System.Windows.Controls.Panel.Children%2A> zbiór <xref:System.Windows.Controls.StackPanel>.</span><span class="sxs-lookup"><span data-stu-id="99da4-274">If the CTRL key is pressed when the <xref:System.Windows.UIElement.Drop> happens, makes a copy of the Circle control and add it to the <xref:System.Windows.Controls.Panel.Children%2A> collection of the <xref:System.Windows.Controls.StackPanel>.</span></span>  
  
    -   <span data-ttu-id="99da4-275">Jeśli nie jest wciśnięty klawisz CTRL, przenosi koło z <xref:System.Windows.Controls.Panel.Children%2A> zbiór jego nadrzędnego panelu <xref:System.Windows.Controls.Panel.Children%2A> zbiór panel, który został upuszczony.</span><span class="sxs-lookup"><span data-stu-id="99da4-275">If the CTRL key is not pressed, moves the Circle from the <xref:System.Windows.Controls.Panel.Children%2A> collection of its parent panel to the <xref:System.Windows.Controls.Panel.Children%2A> collection of the panel that it was dropped on.</span></span>  
  
    -   <span data-ttu-id="99da4-276">Zestawy <xref:System.Windows.DragEventArgs.Effects%2A> właściwości, aby powiadomić <xref:System.Windows.DragDrop.DoDragDrop%2A> metoda czy wykonano operację przenoszenia lub kopiowania.</span><span class="sxs-lookup"><span data-stu-id="99da4-276">Sets the <xref:System.Windows.DragEventArgs.Effects%2A> property to notify the <xref:System.Windows.DragDrop.DoDragDrop%2A> method whether a move or copy operation was performed.</span></span>  
  
6.  <span data-ttu-id="99da4-277">Naciśnij klawisz F5, aby skompilować i uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="99da4-277">Press F5 to build and run the application.</span></span>  
  
7.  <span data-ttu-id="99da4-278">Zaznacz tekst `green` z <xref:System.Windows.Controls.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="99da4-278">Select the text `green` from the <xref:System.Windows.Controls.TextBox>.</span></span>  
  
8.  <span data-ttu-id="99da4-279">Przeciągnij tekst nad formantem okrąg i upuść go.</span><span class="sxs-lookup"><span data-stu-id="99da4-279">Drag the text over a Circle control and drop it.</span></span>  
  
9. <span data-ttu-id="99da4-280">Przeciągnij formant koło z lewego panelu na prawym panelu i upuść go.</span><span class="sxs-lookup"><span data-stu-id="99da4-280">Drag a Circle control from the left panel to the right panel and drop it.</span></span> <span data-ttu-id="99da4-281">Koło zostanie usunięty z <xref:System.Windows.Controls.Panel.Children%2A> zbiór panelu po lewej stronie i dodawane do kolekcji elementów podrzędnych w prawym panelu.</span><span class="sxs-lookup"><span data-stu-id="99da4-281">The Circle is removed from the <xref:System.Windows.Controls.Panel.Children%2A> collection of the left panel and added to the Children collection of the right panel.</span></span>  
  
10. <span data-ttu-id="99da4-282">Przeciągnij formant koło z panelu, w którym się do innego panelu i upuść je w trakcie naciskania klawisza CTRL.</span><span class="sxs-lookup"><span data-stu-id="99da4-282">Drag a Circle control from the panel it is in to the other panel and drop it while pressing the CTRL key.</span></span> <span data-ttu-id="99da4-283">Koło jest kopiowana, a kopia zostanie dodany do <xref:System.Windows.Controls.Panel.Children%2A> zbiór odbieranie panelu.</span><span class="sxs-lookup"><span data-stu-id="99da4-283">The Circle is copied and the copy is added to the <xref:System.Windows.Controls.Panel.Children%2A> collection of the receiving panel.</span></span>  
  
     <span data-ttu-id="99da4-284">![Przeciąganie okrąg w trakcie naciskania klawisza CTRL](../../../../docs/framework/wpf/advanced/media/dragdrop-paneldrop.png "DragDrop_PanelDrop")</span><span class="sxs-lookup"><span data-stu-id="99da4-284">![Dragging a Circle while pressing the CTRL key](../../../../docs/framework/wpf/advanced/media/dragdrop-paneldrop.png "DragDrop_PanelDrop")</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="99da4-285">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="99da4-285">See Also</span></span>  
 [<span data-ttu-id="99da4-286">Przegląd przeciągania i upuszczania</span><span class="sxs-lookup"><span data-stu-id="99da4-286">Drag and Drop Overview</span></span>](../../../../docs/framework/wpf/advanced/drag-and-drop-overview.md)
