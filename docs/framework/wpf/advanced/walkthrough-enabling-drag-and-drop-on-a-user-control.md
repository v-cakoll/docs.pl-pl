---
title: 'Przewodnik: włączanie przeciągania i upuszczania w kontrolce użytkownika'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- walkthrough [WPF], drag-and-drop
- drag-and-drop [WPF], walkthrough
ms.assetid: cc844419-1a77-4906-95d9-060d79107fc7
ms.openlocfilehash: 172e49c2c255db4d24d2180f919b1305326b5e82
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/14/2019
ms.locfileid: "70991807"
---
# <a name="walkthrough-enabling-drag-and-drop-on-a-user-control"></a><span data-ttu-id="c7700-102">Przewodnik: włączanie przeciągania i upuszczania w kontrolce użytkownika</span><span class="sxs-lookup"><span data-stu-id="c7700-102">Walkthrough: Enabling Drag and Drop on a User Control</span></span>

<span data-ttu-id="c7700-103">W tym instruktażu pokazano, jak utworzyć niestandardową kontrolkę użytkownika, która może uczestniczyć w transferze danych [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]metodą "przeciągnij i upuść" w temacie.</span><span class="sxs-lookup"><span data-stu-id="c7700-103">This walkthrough demonstrates how to create a custom user control that can participate in drag-and-drop data transfer in [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)].</span></span>

<span data-ttu-id="c7700-104">W tym instruktażu utworzysz niestandardową WPF <xref:System.Windows.Controls.UserControl> , która reprezentuje kształt okręgu.</span><span class="sxs-lookup"><span data-stu-id="c7700-104">In this walkthrough, you will create a custom WPF <xref:System.Windows.Controls.UserControl> that represents a circle shape.</span></span> <span data-ttu-id="c7700-105">W celu umożliwienia przesyłania danych przez przeciąganie i upuszczanie zostanie wdrożona funkcja na formancie.</span><span class="sxs-lookup"><span data-stu-id="c7700-105">You will implement functionality on the control to enable data transfer through drag-and-drop.</span></span> <span data-ttu-id="c7700-106">Na przykład, jeśli przeciągniesz jeden z formantów okręgu do innego, dane koloru wypełnienia są kopiowane z okręgu źródłowego do obiektu docelowego.</span><span class="sxs-lookup"><span data-stu-id="c7700-106">For example, if you drag from one Circle control to another, the Fill color data is copied from the source Circle to the target.</span></span> <span data-ttu-id="c7700-107">Jeśli przeciągniesz z kontrolki Circle do <xref:System.Windows.Controls.TextBox>, ciąg reprezentujący kolor wypełnienia jest kopiowany <xref:System.Windows.Controls.TextBox>do.</span><span class="sxs-lookup"><span data-stu-id="c7700-107">If you drag from a Circle control to a <xref:System.Windows.Controls.TextBox>, the string representation of the Fill color is copied to the <xref:System.Windows.Controls.TextBox>.</span></span> <span data-ttu-id="c7700-108">Utworzysz również małą aplikację, która zawiera dwie kontrolki paneli i <xref:System.Windows.Controls.TextBox> do testowania funkcji przeciągania i upuszczania.</span><span class="sxs-lookup"><span data-stu-id="c7700-108">You will also create a small application that contains two panel controls and a <xref:System.Windows.Controls.TextBox> to test the drag-and-drop functionality.</span></span> <span data-ttu-id="c7700-109">Napiszesz kod, który umożliwi panelom przetwarzanie porzuconych danych o kółku, co umożliwi przenoszenie lub kopiowanie okręgów z kolekcji Children jednego panelu do drugiego.</span><span class="sxs-lookup"><span data-stu-id="c7700-109">You will write code that enables the panels to process dropped Circle data, which will enable you to move or copy Circles from the Children collection of one panel to the other.</span></span>

<span data-ttu-id="c7700-110">W instruktażu przedstawiono następujące zagadnienia:</span><span class="sxs-lookup"><span data-stu-id="c7700-110">This walkthrough illustrates the following tasks:</span></span>

- <span data-ttu-id="c7700-111">Utwórz niestandardową kontrolkę użytkownika.</span><span class="sxs-lookup"><span data-stu-id="c7700-111">Create a custom user control.</span></span>

- <span data-ttu-id="c7700-112">Włącz kontrolkę użytkownika jako źródło przeciągania.</span><span class="sxs-lookup"><span data-stu-id="c7700-112">Enable the user control to be a drag source.</span></span>

- <span data-ttu-id="c7700-113">Włącz kontrolkę użytkownika jako element docelowy upuszczania.</span><span class="sxs-lookup"><span data-stu-id="c7700-113">Enable the user control to be a drop target.</span></span>

- <span data-ttu-id="c7700-114">Włącz panel do odbierania danych porzuconych z kontrolki użytkownika.</span><span class="sxs-lookup"><span data-stu-id="c7700-114">Enable a panel to receive data dropped from the user control.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="c7700-115">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="c7700-115">Prerequisites</span></span>

<span data-ttu-id="c7700-116">Aby ukończyć ten przewodnik, potrzebujesz programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="c7700-116">You need Visual Studio to complete this walkthrough.</span></span>

## <a name="create-the-application-project"></a><span data-ttu-id="c7700-117">Tworzenie projektu aplikacji</span><span class="sxs-lookup"><span data-stu-id="c7700-117">Create the Application Project</span></span>
 <span data-ttu-id="c7700-118">W tej sekcji utworzysz infrastrukturę aplikacji, która obejmuje stronę główną z dwoma panelami i <xref:System.Windows.Controls.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="c7700-118">In this section, you will create the application infrastructure, which includes a main page with two panels and a <xref:System.Windows.Controls.TextBox>.</span></span>

1. <span data-ttu-id="c7700-119">Utwórz nowy projekt aplikacji WPF w Visual Basic lub wizualizacji C# o `DragDropExample`nazwie.</span><span class="sxs-lookup"><span data-stu-id="c7700-119">Create a new WPF Application project in Visual Basic or Visual C# named `DragDropExample`.</span></span> <span data-ttu-id="c7700-120">Aby uzyskać więcej informacji, [zobacz Przewodnik: Moja pierwsza aplikacja](../getting-started/walkthrough-my-first-wpf-desktop-application.md)klasyczna WPF.</span><span class="sxs-lookup"><span data-stu-id="c7700-120">For more information, see [Walkthrough: My first WPF desktop application](../getting-started/walkthrough-my-first-wpf-desktop-application.md).</span></span>

2. <span data-ttu-id="c7700-121">Open MainWindow.xaml.</span><span class="sxs-lookup"><span data-stu-id="c7700-121">Open MainWindow.xaml.</span></span>

3. <span data-ttu-id="c7700-122">Dodaj następujące znaczniki między tagiem otwierającym i zamykającym <xref:System.Windows.Controls.Grid> .</span><span class="sxs-lookup"><span data-stu-id="c7700-122">Add the following markup between the opening and closing <xref:System.Windows.Controls.Grid> tags.</span></span>

     <span data-ttu-id="c7700-123">Ten znacznik tworzy interfejs użytkownika dla aplikacji testowej.</span><span class="sxs-lookup"><span data-stu-id="c7700-123">This markup creates the user interface for the test application.</span></span>

     [!code-xaml[DragDropWalkthrough#PanelsStep1XAML](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/SnippetWindow.xaml#panelsstep1xaml)]

## <a name="add-a-new-user-control-to-the-project"></a><span data-ttu-id="c7700-124">Dodaj nową kontrolkę użytkownika do projektu</span><span class="sxs-lookup"><span data-stu-id="c7700-124">Add a New User Control to the Project</span></span>
 <span data-ttu-id="c7700-125">W tej sekcji dodasz nową kontrolkę użytkownika do projektu.</span><span class="sxs-lookup"><span data-stu-id="c7700-125">In this section, you will add a new user control to the project.</span></span>

1. <span data-ttu-id="c7700-126">W menu Projekt wybierz polecenie **Dodaj kontrolkę użytkownika**.</span><span class="sxs-lookup"><span data-stu-id="c7700-126">On the Project menu, select **Add User Control**.</span></span>

2. <span data-ttu-id="c7700-127">W oknie dialogowym **Dodaj nowy element** Zmień nazwę na `Circle.xaml`, a następnie kliknij przycisk **Dodaj**.</span><span class="sxs-lookup"><span data-stu-id="c7700-127">In the **Add New Item** dialog box, change the name to `Circle.xaml`, and click **Add**.</span></span>

     <span data-ttu-id="c7700-128">W projekcie zostanie dodany okrąg. XAML i jego kod.</span><span class="sxs-lookup"><span data-stu-id="c7700-128">Circle.xaml and its code-behind is added to the project.</span></span>

3. <span data-ttu-id="c7700-129">Open Circle.xaml.</span><span class="sxs-lookup"><span data-stu-id="c7700-129">Open Circle.xaml.</span></span>

     <span data-ttu-id="c7700-130">Ten plik będzie zawierać elementy interfejsu użytkownika kontrolki użytkownika.</span><span class="sxs-lookup"><span data-stu-id="c7700-130">This file will contain the user interface elements of the user control.</span></span>

4. <span data-ttu-id="c7700-131">Dodaj następujący znacznik do katalogu głównego <xref:System.Windows.Controls.Grid> , aby utworzyć prostą kontrolkę użytkownika, która ma niebieski okrąg jako interfejs użytkownika.</span><span class="sxs-lookup"><span data-stu-id="c7700-131">Add the following markup to the root <xref:System.Windows.Controls.Grid> to create a simple user control that has a blue circle as its UI.</span></span>

     [!code-xaml[DragDropWalkthrough#EllipseXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml#ellipsexaml)]

5. <span data-ttu-id="c7700-132">Otwórz Circle.xaml.cs lub Circle. XAML. vb.</span><span class="sxs-lookup"><span data-stu-id="c7700-132">Open Circle.xaml.cs or Circle.xaml.vb.</span></span>

6. <span data-ttu-id="c7700-133">W C#programie Dodaj następujący kod po konstruktorze bez parametrów, aby utworzyć Konstruktor kopiujący.</span><span class="sxs-lookup"><span data-stu-id="c7700-133">In C#, add the following code after the parameterless constructor to create a copy constructor.</span></span> <span data-ttu-id="c7700-134">W Visual Basic Dodaj następujący kod, aby utworzyć zarówno konstruktora bez parametrów, jak i konstruktora kopiującego.</span><span class="sxs-lookup"><span data-stu-id="c7700-134">In Visual Basic, add the following code to create both a parameterless constructor and a copy constructor.</span></span>

     <span data-ttu-id="c7700-135">Aby umożliwić skopiowanie kontrolki użytkownika, należy dodać metodę kopiowania konstruktora w pliku związanym z kodem.</span><span class="sxs-lookup"><span data-stu-id="c7700-135">In order to allow the user control to be copied, you add a copy constructor method in the code-behind file.</span></span> <span data-ttu-id="c7700-136">W uproszczonej kontrolce użytkownika kółka będziesz kopiować tylko wypełnienie i rozmiar kontrolki użytkownika.</span><span class="sxs-lookup"><span data-stu-id="c7700-136">In the simplified Circle user control, you will only copy the Fill and the size of the of the user control.</span></span>

     [!code-csharp[DragDropWalkthrough#CopyCtor](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#copyctor)]
     [!code-vb[DragDropWalkthrough#CopyCtor](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#copyctor)]

## <a name="add-the-user-control-to-the-main-window"></a><span data-ttu-id="c7700-137">Dodaj kontrolkę użytkownika do okna głównego</span><span class="sxs-lookup"><span data-stu-id="c7700-137">Add the user control to the main window</span></span>

1. <span data-ttu-id="c7700-138">Open MainWindow.xaml.</span><span class="sxs-lookup"><span data-stu-id="c7700-138">Open MainWindow.xaml.</span></span>

2. <span data-ttu-id="c7700-139">Dodaj następujący kod XAML do tagu otwierającego <xref:System.Windows.Window> , aby utworzyć odwołanie do przestrzeni nazw XML dla bieżącej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="c7700-139">Add the following XAML to the opening <xref:System.Windows.Window> tag to create an XML namespace reference to the current application.</span></span>

    ```xaml
    xmlns:local="clr-namespace:DragDropExample"
    ```

3. <span data-ttu-id="c7700-140">W pierwszej kolejności <xref:System.Windows.Controls.StackPanel>Dodaj następujący kod XAML, aby utworzyć dwa wystąpienia kontrolki użytkownika Circle na pierwszym panelu.</span><span class="sxs-lookup"><span data-stu-id="c7700-140">In the first <xref:System.Windows.Controls.StackPanel>, add the following XAML to create two instances of the Circle user control in the first panel.</span></span>

     [!code-xaml[DragDropWalkthrough#CirclesXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/SnippetWindow.xaml#circlesxaml)]

     <span data-ttu-id="c7700-141">Pełny kod XAML dla panelu wygląda podobnie do poniższego.</span><span class="sxs-lookup"><span data-stu-id="c7700-141">The full XAML for the panel looks like the following.</span></span>

     [!code-xaml[DragDropWalkthrough#PanelsStep2XAML](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/SnippetWindow.xaml#panelsstep2xaml)]

## <a name="implement-drag-source-events-in-the-user-control"></a><span data-ttu-id="c7700-142">Implementowanie zdarzeń przeciągania źródła w kontrolce użytkownika</span><span class="sxs-lookup"><span data-stu-id="c7700-142">Implement Drag Source Events in the User Control</span></span>
 <span data-ttu-id="c7700-143">W tej sekcji zastąpisz <xref:System.Windows.UIElement.OnMouseMove%2A> metodę i zainicjujesz operację przeciągania i upuszczania.</span><span class="sxs-lookup"><span data-stu-id="c7700-143">In this section, you will override the <xref:System.Windows.UIElement.OnMouseMove%2A> method and initiate the drag-and-drop operation.</span></span>

 <span data-ttu-id="c7700-144">Po rozpoczęciu przeciągania (przycisk myszy jest wciśnięty, a mysz jest przenoszona), dane zostaną spakowane w celu przeniesienia do programu <xref:System.Windows.DataObject>.</span><span class="sxs-lookup"><span data-stu-id="c7700-144">If a drag is started (a mouse button is pressed and the mouse is moved), you will package the data to be transferred into a <xref:System.Windows.DataObject>.</span></span> <span data-ttu-id="c7700-145">W takim przypadku formant Circle spowoduje spakowanie trzech elementów danych; ciąg reprezentujący kolor wypełnienia, podwójną reprezentację wysokości i kopię siebie.</span><span class="sxs-lookup"><span data-stu-id="c7700-145">In this case, the Circle control will package three data items; a string representation of its Fill color, a double representation of its height, and a copy of itself.</span></span>

### <a name="to-initiate-a-drag-and-drop-operation"></a><span data-ttu-id="c7700-146">Aby zainicjować operację przeciągania i upuszczania</span><span class="sxs-lookup"><span data-stu-id="c7700-146">To initiate a drag-and-drop operation</span></span>

1. <span data-ttu-id="c7700-147">Otwórz Circle.xaml.cs lub Circle. XAML. vb.</span><span class="sxs-lookup"><span data-stu-id="c7700-147">Open Circle.xaml.cs or Circle.xaml.vb.</span></span>

2. <span data-ttu-id="c7700-148">Dodaj następujące <xref:System.Windows.UIElement.OnMouseMove%2A> zastąpienie, aby zapewnić obsługę klasy <xref:System.Windows.UIElement.MouseMove> dla zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="c7700-148">Add the following <xref:System.Windows.UIElement.OnMouseMove%2A> override to provide class handling for the <xref:System.Windows.UIElement.MouseMove> event.</span></span>

     [!code-csharp[DragDropWalkthrough#OnMouseMove](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#onmousemove)]
     [!code-vb[DragDropWalkthrough#OnMouseMove](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#onmousemove)]

     <span data-ttu-id="c7700-149">To <xref:System.Windows.UIElement.OnMouseMove%2A> przesłonięcie wykonuje następujące zadania:</span><span class="sxs-lookup"><span data-stu-id="c7700-149">This <xref:System.Windows.UIElement.OnMouseMove%2A> override performs the following tasks:</span></span>

    - <span data-ttu-id="c7700-150">Sprawdza, czy lewy przycisk myszy jest wciśnięty podczas przesuwania myszy.</span><span class="sxs-lookup"><span data-stu-id="c7700-150">Checks whether the left mouse button is pressed while the mouse is moving.</span></span>

    - <span data-ttu-id="c7700-151">Pakuje dane okręgu do <xref:System.Windows.DataObject>.</span><span class="sxs-lookup"><span data-stu-id="c7700-151">Packages the Circle data into a <xref:System.Windows.DataObject>.</span></span> <span data-ttu-id="c7700-152">W takim przypadku Kierownica ma trzy elementy danych; ciąg reprezentujący kolor wypełnienia, podwójną reprezentację wysokości i kopię siebie.</span><span class="sxs-lookup"><span data-stu-id="c7700-152">In this case, the Circle control packages three data items; a string representation of its Fill color, a double representation of its height, and a copy of itself.</span></span>

    - <span data-ttu-id="c7700-153">Wywołuje metodę statyczną <xref:System.Windows.DragDrop.DoDragDrop%2A?displayProperty=nameWithType> w celu zainicjowania operacji przeciągania i upuszczania.</span><span class="sxs-lookup"><span data-stu-id="c7700-153">Calls the static <xref:System.Windows.DragDrop.DoDragDrop%2A?displayProperty=nameWithType> method to initiate the drag-and-drop operation.</span></span> <span data-ttu-id="c7700-154">Do <xref:System.Windows.DragDrop.DoDragDrop%2A> metody przekazywane są następujące trzy parametry:</span><span class="sxs-lookup"><span data-stu-id="c7700-154">You pass the following three parameters to the <xref:System.Windows.DragDrop.DoDragDrop%2A> method:</span></span>

        - <span data-ttu-id="c7700-155">`dragSource`— Odwołanie do tego formantu.</span><span class="sxs-lookup"><span data-stu-id="c7700-155">`dragSource` – A reference to this control.</span></span>

        - <span data-ttu-id="c7700-156">`data`<xref:System.Windows.DataObject> — Utworzono w poprzednim kodzie.</span><span class="sxs-lookup"><span data-stu-id="c7700-156">`data` – The <xref:System.Windows.DataObject> created in the previous code.</span></span>

        - <span data-ttu-id="c7700-157">`allowedEffects`— Dozwolone operacje przeciągania i upuszczania, które są <xref:System.Windows.DragDropEffects.Copy> lub. <xref:System.Windows.DragDropEffects.Move></span><span class="sxs-lookup"><span data-stu-id="c7700-157">`allowedEffects` – The allowed drag-and-drop operations, which are <xref:System.Windows.DragDropEffects.Copy> or <xref:System.Windows.DragDropEffects.Move>.</span></span>

3. <span data-ttu-id="c7700-158">Naciśnij klawisz **F5** , aby skompilować i uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="c7700-158">Press **F5** to build and run the application.</span></span>

4. <span data-ttu-id="c7700-159">Kliknij jedną z kontrolek okręgu i przeciągnij ją nad panele, drugi okrąg i <xref:System.Windows.Controls.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="c7700-159">Click one of the Circle controls and drag it over the panels, the other Circle, and the <xref:System.Windows.Controls.TextBox>.</span></span> <span data-ttu-id="c7700-160">Podczas przeciągania nad <xref:System.Windows.Controls.TextBox>kursor zmieni się, aby wskazać przeniesienie.</span><span class="sxs-lookup"><span data-stu-id="c7700-160">When dragging over the <xref:System.Windows.Controls.TextBox>, the cursor changes to indicate a move.</span></span>

5. <span data-ttu-id="c7700-161">Przeciągając okrąg <xref:System.Windows.Controls.TextBox>na, naciśnij klawisz **Ctrl** .</span><span class="sxs-lookup"><span data-stu-id="c7700-161">While dragging a Circle over the <xref:System.Windows.Controls.TextBox>, press the **Ctrl** key.</span></span> <span data-ttu-id="c7700-162">Zauważ, że kursor zmieni się, aby wskazać kopię.</span><span class="sxs-lookup"><span data-stu-id="c7700-162">Notice how the cursor changes to indicate a copy.</span></span>

6. <span data-ttu-id="c7700-163">Przeciągnij i upuść okrąg na <xref:System.Windows.Controls.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="c7700-163">Drag and drop a Circle onto the <xref:System.Windows.Controls.TextBox>.</span></span> <span data-ttu-id="c7700-164">Ciąg reprezentujący kolor wypełnienia okręgu jest dołączany do <xref:System.Windows.Controls.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="c7700-164">The string representation of the Circle’s fill color is appended to the <xref:System.Windows.Controls.TextBox>.</span></span>

     <span data-ttu-id="c7700-165">![Ciąg reprezentujący kolor wypełnienia okręgu](./media/dragdrop-colorstring.png "DragDrop_ColorString")</span><span class="sxs-lookup"><span data-stu-id="c7700-165">![String representation of Circle's fill color](./media/dragdrop-colorstring.png "DragDrop_ColorString")</span></span>

<span data-ttu-id="c7700-166">Domyślnie kursor zmieni się w trakcie operacji przeciągania i upuszczania, aby wskazać, jaki efekt spowoduje porzucenie danych.</span><span class="sxs-lookup"><span data-stu-id="c7700-166">By default, the cursor will change during a drag-and-drop operation to indicate what effect dropping the data will have.</span></span> <span data-ttu-id="c7700-167">Możesz dostosować opinię podaną użytkownikowi przez obsługę <xref:System.Windows.UIElement.GiveFeedback> zdarzenia i ustawienie innego kursora.</span><span class="sxs-lookup"><span data-stu-id="c7700-167">You can customize the feedback given to the user by handling the <xref:System.Windows.UIElement.GiveFeedback> event and setting a different cursor.</span></span>

## <a name="give-feedback-to-the-user"></a><span data-ttu-id="c7700-168">Przekaż opinię użytkownikowi</span><span class="sxs-lookup"><span data-stu-id="c7700-168">Give feedback to the user</span></span>

1. <span data-ttu-id="c7700-169">Otwórz Circle.xaml.cs lub Circle. XAML. vb.</span><span class="sxs-lookup"><span data-stu-id="c7700-169">Open Circle.xaml.cs or Circle.xaml.vb.</span></span>

2. <span data-ttu-id="c7700-170">Dodaj następujące <xref:System.Windows.UIElement.OnGiveFeedback%2A> zastąpienie, aby zapewnić obsługę klasy <xref:System.Windows.UIElement.GiveFeedback> dla zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="c7700-170">Add the following <xref:System.Windows.UIElement.OnGiveFeedback%2A> override to provide class handling for the <xref:System.Windows.UIElement.GiveFeedback> event.</span></span>

     [!code-csharp[DragDropWalkthrough#OnGiveFeedback](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#ongivefeedback)]
     [!code-vb[DragDropWalkthrough#OnGiveFeedback](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#ongivefeedback)]

     <span data-ttu-id="c7700-171">To <xref:System.Windows.UIElement.OnGiveFeedback%2A> przesłonięcie wykonuje następujące zadania:</span><span class="sxs-lookup"><span data-stu-id="c7700-171">This <xref:System.Windows.UIElement.OnGiveFeedback%2A> override performs the following tasks:</span></span>

    - <span data-ttu-id="c7700-172">Sprawdza wartości, które są ustawione w programie obsługi <xref:System.Windows.UIElement.DragOver> zdarzeń upuszczania docelowej. <xref:System.Windows.GiveFeedbackEventArgs.Effects%2A></span><span class="sxs-lookup"><span data-stu-id="c7700-172">Checks the <xref:System.Windows.GiveFeedbackEventArgs.Effects%2A> values that are set in the drop target's <xref:System.Windows.UIElement.DragOver> event handler.</span></span>

    - <span data-ttu-id="c7700-173">Ustawia niestandardowy kursor na podstawie <xref:System.Windows.GiveFeedbackEventArgs.Effects%2A> wartości.</span><span class="sxs-lookup"><span data-stu-id="c7700-173">Sets a custom cursor based on the <xref:System.Windows.GiveFeedbackEventArgs.Effects%2A> value.</span></span> <span data-ttu-id="c7700-174">Kursor ma na celu umożliwienie wizualnej opinii użytkownika o tym, jaki wpływ na dane zostaną porzucane.</span><span class="sxs-lookup"><span data-stu-id="c7700-174">The cursor is intended to give visual feedback to the user about what effect dropping the data will have.</span></span>

3. <span data-ttu-id="c7700-175">Naciśnij klawisz **F5** , aby skompilować i uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="c7700-175">Press **F5** to build and run the application.</span></span>

4. <span data-ttu-id="c7700-176">Przeciągnij jedną z kontrolek okręgu na panele, drugi okrąg i <xref:System.Windows.Controls.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="c7700-176">Drag one of the Circle controls over the panels, the other Circle, and the <xref:System.Windows.Controls.TextBox>.</span></span> <span data-ttu-id="c7700-177">Zauważ, że kursory są teraz kursorami niestandardowymi, które <xref:System.Windows.UIElement.OnGiveFeedback%2A> zostały określone w przesłonięciu.</span><span class="sxs-lookup"><span data-stu-id="c7700-177">Notice that the cursors are now the custom cursors that you specified in the <xref:System.Windows.UIElement.OnGiveFeedback%2A> override.</span></span>

     <span data-ttu-id="c7700-178">![Przeciąganie i upuszczanie za pomocą niestandardowych kursorów](./media/dragdrop-customcursor.png "DragDrop_CustomCursor")</span><span class="sxs-lookup"><span data-stu-id="c7700-178">![Drag and drop with custom cursors](./media/dragdrop-customcursor.png "DragDrop_CustomCursor")</span></span>

5. <span data-ttu-id="c7700-179">Wybierz tekst `green` <xref:System.Windows.Controls.TextBox>z.</span><span class="sxs-lookup"><span data-stu-id="c7700-179">Select the text `green` from the <xref:System.Windows.Controls.TextBox>.</span></span>

6. <span data-ttu-id="c7700-180">`green` Przeciągnij tekst do kontrolki okręgu.</span><span class="sxs-lookup"><span data-stu-id="c7700-180">Drag the `green` text to a Circle control.</span></span> <span data-ttu-id="c7700-181">Zauważ, że domyślne kursory są wyświetlane, aby wskazać efekty operacji przeciągania i upuszczania.</span><span class="sxs-lookup"><span data-stu-id="c7700-181">Notice that the default cursors are shown to indicate the effects of the drag-and-drop operation.</span></span> <span data-ttu-id="c7700-182">Kursor opinii jest zawsze ustawiany przez źródło przeciągania.</span><span class="sxs-lookup"><span data-stu-id="c7700-182">The feedback cursor is always set by the drag source.</span></span>

## <a name="implement-drop-target-events-in-the-user-control"></a><span data-ttu-id="c7700-183">Implementowanie docelowych zdarzeń upuszczania w kontrolce użytkownika</span><span class="sxs-lookup"><span data-stu-id="c7700-183">Implement Drop Target Events in the User Control</span></span>
 <span data-ttu-id="c7700-184">W tej sekcji określisz, że formant użytkownika jest obiektem docelowym upuszczania, Zastąp metody, które umożliwiają kontrolowanie użytkownika jako element docelowy upuszczania, i przetwarzanie danych, które zostały przez niego usunięte.</span><span class="sxs-lookup"><span data-stu-id="c7700-184">In this section, you will specify that the user control is a drop target, override the methods that enable the user control to be a drop target, and process the data that is dropped on it.</span></span>

### <a name="to-enable-the-user-control-to-be-a-drop-target"></a><span data-ttu-id="c7700-185">Aby włączyć kontrolkę użytkownika jako element docelowy upuszczania</span><span class="sxs-lookup"><span data-stu-id="c7700-185">To enable the user control to be a drop target</span></span>

1. <span data-ttu-id="c7700-186">Open Circle.xaml.</span><span class="sxs-lookup"><span data-stu-id="c7700-186">Open Circle.xaml.</span></span>

2. <span data-ttu-id="c7700-187">W tagu otwierającym <xref:System.Windows.Controls.UserControl> <xref:System.Windows.UIElement.AllowDrop%2A> Dodaj właściwość i ustaw ją na `true`.</span><span class="sxs-lookup"><span data-stu-id="c7700-187">In the opening <xref:System.Windows.Controls.UserControl> tag, add the <xref:System.Windows.UIElement.AllowDrop%2A> property and set it to `true`.</span></span>

     [!code-xaml[DragDropWalkthrough#UCTagXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml#uctagxaml)]

<span data-ttu-id="c7700-188">Metoda jest wywoływana, <xref:System.Windows.UIElement.AllowDrop%2A> gdy właściwość jest ustawiona na `true` , a dane ze źródła przeciągania są porzucane w kontrolce użytkownika koła. <xref:System.Windows.UIElement.OnDrop%2A></span><span class="sxs-lookup"><span data-stu-id="c7700-188">The <xref:System.Windows.UIElement.OnDrop%2A> method is called when the <xref:System.Windows.UIElement.AllowDrop%2A> property is set to `true` and data from the drag source is dropped on the Circle user control.</span></span> <span data-ttu-id="c7700-189">W tej metodzie przetwarzasz dane, które zostały porzucone i stosują dane do okręgu.</span><span class="sxs-lookup"><span data-stu-id="c7700-189">In this method, you will process the data that was dropped and apply the data to the Circle.</span></span>

### <a name="to-process-the-dropped-data"></a><span data-ttu-id="c7700-190">Aby przetworzyć opuszczone dane</span><span class="sxs-lookup"><span data-stu-id="c7700-190">To process the dropped data</span></span>

1. <span data-ttu-id="c7700-191">Otwórz Circle.xaml.cs lub Circle. XAML. vb.</span><span class="sxs-lookup"><span data-stu-id="c7700-191">Open Circle.xaml.cs or Circle.xaml.vb.</span></span>

2. <span data-ttu-id="c7700-192">Dodaj następujące <xref:System.Windows.UIElement.OnDrop%2A> zastąpienie, aby zapewnić obsługę klasy <xref:System.Windows.UIElement.Drop> dla zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="c7700-192">Add the following <xref:System.Windows.UIElement.OnDrop%2A> override to provide class handling for the <xref:System.Windows.UIElement.Drop> event.</span></span>

     [!code-csharp[DragDropWalkthrough#OnDrop](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#ondrop)]
     [!code-vb[DragDropWalkthrough#OnDrop](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#ondrop)]

     <span data-ttu-id="c7700-193">To <xref:System.Windows.UIElement.OnDrop%2A> przesłonięcie wykonuje następujące zadania:</span><span class="sxs-lookup"><span data-stu-id="c7700-193">This <xref:System.Windows.UIElement.OnDrop%2A> override performs the following tasks:</span></span>

    - <span data-ttu-id="c7700-194"><xref:System.Windows.DataObject.GetDataPresent%2A> Używa metody do sprawdzenia, czy przeciągane dane zawierają obiekt ciągu.</span><span class="sxs-lookup"><span data-stu-id="c7700-194">Uses the <xref:System.Windows.DataObject.GetDataPresent%2A> method to check if the dragged data contains a string object.</span></span>

    - <span data-ttu-id="c7700-195"><xref:System.Windows.DataObject.GetData%2A> Używa metody do wyodrębnienia danych ciągu, jeśli są obecne.</span><span class="sxs-lookup"><span data-stu-id="c7700-195">Uses the <xref:System.Windows.DataObject.GetData%2A> method to extract the string data if it is present.</span></span>

    - <span data-ttu-id="c7700-196">Używa do próby przekonwertowania ciągu <xref:System.Windows.Media.Brush>na. <xref:System.Windows.Media.BrushConverter></span><span class="sxs-lookup"><span data-stu-id="c7700-196">Uses a <xref:System.Windows.Media.BrushConverter> to try to convert the string to a <xref:System.Windows.Media.Brush>.</span></span>

    - <span data-ttu-id="c7700-197">Jeśli konwersja zakończy się pomyślnie, program zastosuje pędzel <xref:System.Windows.Shapes.Shape.Fill%2A> do <xref:System.Windows.Shapes.Ellipse> elementu, który zapewnia interfejs użytkownika kontrolki Circle.</span><span class="sxs-lookup"><span data-stu-id="c7700-197">If the conversion is successful, applies the brush to the <xref:System.Windows.Shapes.Shape.Fill%2A> of the <xref:System.Windows.Shapes.Ellipse> that provides the UI of the Circle control.</span></span>

    - <span data-ttu-id="c7700-198"><xref:System.Windows.UIElement.Drop> Oznacza zdarzenie jako obsłużone.</span><span class="sxs-lookup"><span data-stu-id="c7700-198">Marks the <xref:System.Windows.UIElement.Drop> event as handled.</span></span> <span data-ttu-id="c7700-199">Należy oznaczyć zdarzenie upuszczania jako obsłużone, tak aby inne elementy, które odbierają to zdarzenie, wiedziały, że kontrolka użytkownika kółka ją obsłuży.</span><span class="sxs-lookup"><span data-stu-id="c7700-199">You should mark the drop event as handled so that other elements that receive this event know that the Circle user control handled it.</span></span>

3. <span data-ttu-id="c7700-200">Naciśnij klawisz **F5** , aby skompilować i uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="c7700-200">Press **F5** to build and run the application.</span></span>

4. <span data-ttu-id="c7700-201">Zaznacz tekst `green` <xref:System.Windows.Controls.TextBox>w.</span><span class="sxs-lookup"><span data-stu-id="c7700-201">Select the text `green` in the <xref:System.Windows.Controls.TextBox>.</span></span>

5. <span data-ttu-id="c7700-202">Przeciągnij tekst do kontrolki Circle i upuść ją.</span><span class="sxs-lookup"><span data-stu-id="c7700-202">Drag the text to a Circle control and drop it.</span></span> <span data-ttu-id="c7700-203">Okrąg zmieni się z niebieski na zielony.</span><span class="sxs-lookup"><span data-stu-id="c7700-203">The Circle changes from blue to green.</span></span>

     <span data-ttu-id="c7700-204">![Konwertuj ciąg na pędzel](./media/dragdrop-dropgreentext.png "DragDrop_DropGreenText")</span><span class="sxs-lookup"><span data-stu-id="c7700-204">![Convert a string to a brush](./media/dragdrop-dropgreentext.png "DragDrop_DropGreenText")</span></span>

6. <span data-ttu-id="c7700-205">Wpisz tekst `green` <xref:System.Windows.Controls.TextBox>w.</span><span class="sxs-lookup"><span data-stu-id="c7700-205">Type the text `green` in the <xref:System.Windows.Controls.TextBox>.</span></span>

7. <span data-ttu-id="c7700-206">Zaznacz tekst `gre` <xref:System.Windows.Controls.TextBox>w.</span><span class="sxs-lookup"><span data-stu-id="c7700-206">Select the text `gre` in the <xref:System.Windows.Controls.TextBox>.</span></span>

8. <span data-ttu-id="c7700-207">Przeciągnij go do kontrolki okręgu i upuść.</span><span class="sxs-lookup"><span data-stu-id="c7700-207">Drag it to a Circle control and drop it.</span></span> <span data-ttu-id="c7700-208">Zauważ, że kursor zmieni się, aby wskazać, że porzucanie jest dozwolone, ale kolor koła nie zmienia się `gre` , ponieważ nie jest prawidłowym kolorem.</span><span class="sxs-lookup"><span data-stu-id="c7700-208">Notice that the cursor changes to indicate that the drop is allowed, but the color of the Circle does not change because `gre` is not a valid color.</span></span>

9. <span data-ttu-id="c7700-209">Przeciągnij wskaźnik myszy z zielonego kółka i upuść go w kontrolce niebieskiego okręgu.</span><span class="sxs-lookup"><span data-stu-id="c7700-209">Drag from the green Circle control and drop on the blue Circle control.</span></span> <span data-ttu-id="c7700-210">Okrąg zmieni się z niebieski na zielony.</span><span class="sxs-lookup"><span data-stu-id="c7700-210">The Circle changes from blue to green.</span></span> <span data-ttu-id="c7700-211">Zauważ, że kursor jest pokazywany, zależy od tego <xref:System.Windows.Controls.TextBox> , czy okrąg jest źródłem przeciągania.</span><span class="sxs-lookup"><span data-stu-id="c7700-211">Notice that which cursor is shown depends on whether the <xref:System.Windows.Controls.TextBox> or the Circle is the drag source.</span></span>

<span data-ttu-id="c7700-212">Ustawienie właściwości na `true` i przetwarzanie porzuconych danych jest wymagane do włączenia elementu jako miejsca docelowego upuszczania. <xref:System.Windows.UIElement.AllowDrop%2A></span><span class="sxs-lookup"><span data-stu-id="c7700-212">Setting the <xref:System.Windows.UIElement.AllowDrop%2A> property to `true` and processing the dropped data is all that is required to enable an element to be a drop target.</span></span> <span data-ttu-id="c7700-213">Aby jednak zapewnić lepsze środowisko użytkownika, należy również obsłużyć <xref:System.Windows.UIElement.DragEnter>zdarzenia, <xref:System.Windows.UIElement.DragLeave>i <xref:System.Windows.UIElement.DragOver> .</span><span class="sxs-lookup"><span data-stu-id="c7700-213">However, to provide a better user experience, you should also handle the <xref:System.Windows.UIElement.DragEnter>, <xref:System.Windows.UIElement.DragLeave>, and <xref:System.Windows.UIElement.DragOver> events.</span></span> <span data-ttu-id="c7700-214">W tych zdarzeniach można wykonać testy i przekazać użytkownikowi dodatkowe opinie przed usunięciem danych.</span><span class="sxs-lookup"><span data-stu-id="c7700-214">In these events, you can perform checks and provide additional feedback to the user before the data is dropped.</span></span>

<span data-ttu-id="c7700-215">Gdy dane są przeciągane za pomocą okrągłej kontrolki użytkownika, formant powinien poinformować Źródło przeciągania, czy może przetwarzać dane, które są przeciągane.</span><span class="sxs-lookup"><span data-stu-id="c7700-215">When data is dragged over the Circle user control, the control should notify the drag source whether it can process the data that is being dragged.</span></span> <span data-ttu-id="c7700-216">Jeśli formant nie wie, jak przetwarzać dane, powinna odmówić usunięcia.</span><span class="sxs-lookup"><span data-stu-id="c7700-216">If the control does not know how to process the data, it should refuse the drop.</span></span> <span data-ttu-id="c7700-217">W tym celu należy obsłużyć <xref:System.Windows.UIElement.DragOver> zdarzenie i <xref:System.Windows.DragEventArgs.Effects%2A> ustawić właściwość.</span><span class="sxs-lookup"><span data-stu-id="c7700-217">To do this, you will handle the <xref:System.Windows.UIElement.DragOver> event and set the <xref:System.Windows.DragEventArgs.Effects%2A> property.</span></span>

### <a name="to-verify-that-the-data-drop-is-allowed"></a><span data-ttu-id="c7700-218">Aby sprawdzić, czy usuwanie danych jest dozwolone</span><span class="sxs-lookup"><span data-stu-id="c7700-218">To verify that the data drop is allowed</span></span>

1. <span data-ttu-id="c7700-219">Otwórz Circle.xaml.cs lub Circle. XAML. vb.</span><span class="sxs-lookup"><span data-stu-id="c7700-219">Open Circle.xaml.cs or Circle.xaml.vb.</span></span>

2. <span data-ttu-id="c7700-220">Dodaj następujące <xref:System.Windows.UIElement.OnDragOver%2A> zastąpienie, aby zapewnić obsługę klasy <xref:System.Windows.UIElement.DragOver> dla zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="c7700-220">Add the following <xref:System.Windows.UIElement.OnDragOver%2A> override to provide class handling for the <xref:System.Windows.UIElement.DragOver> event.</span></span>

     [!code-csharp[DragDropWalkthrough#OnDragOver](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#ondragover)]
     [!code-vb[DragDropWalkthrough#OnDragOver](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#ondragover)]

     <span data-ttu-id="c7700-221">To <xref:System.Windows.UIElement.OnDragOver%2A> przesłonięcie wykonuje następujące zadania:</span><span class="sxs-lookup"><span data-stu-id="c7700-221">This <xref:System.Windows.UIElement.OnDragOver%2A> override performs the following tasks:</span></span>

    - <span data-ttu-id="c7700-222">Ustawia właściwość na <xref:System.Windows.DragDropEffects.None>. <xref:System.Windows.DragEventArgs.Effects%2A></span><span class="sxs-lookup"><span data-stu-id="c7700-222">Sets the <xref:System.Windows.DragEventArgs.Effects%2A> property to <xref:System.Windows.DragDropEffects.None>.</span></span>

    - <span data-ttu-id="c7700-223">Wykonuje te same kontrole, które są wykonywane w <xref:System.Windows.UIElement.OnDrop%2A> metodzie, aby określić, czy formant użytkownika kółka może przetwarzać przeciągnięte dane.</span><span class="sxs-lookup"><span data-stu-id="c7700-223">Performs the same checks that are performed in the <xref:System.Windows.UIElement.OnDrop%2A> method to determine whether the Circle user control can process the dragged data.</span></span>

    - <span data-ttu-id="c7700-224">Jeśli kontrolka użytkownika może przetwarzać dane, ustawia <xref:System.Windows.DragEventArgs.Effects%2A> właściwość na <xref:System.Windows.DragDropEffects.Copy> lub <xref:System.Windows.DragDropEffects.Move>.</span><span class="sxs-lookup"><span data-stu-id="c7700-224">If the user control can process the data, sets the <xref:System.Windows.DragEventArgs.Effects%2A> property to <xref:System.Windows.DragDropEffects.Copy> or <xref:System.Windows.DragDropEffects.Move>.</span></span>

3. <span data-ttu-id="c7700-225">Naciśnij klawisz **F5** , aby skompilować i uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="c7700-225">Press **F5** to build and run the application.</span></span>

4. <span data-ttu-id="c7700-226">Zaznacz tekst `gre` <xref:System.Windows.Controls.TextBox>w.</span><span class="sxs-lookup"><span data-stu-id="c7700-226">Select the text `gre` in the <xref:System.Windows.Controls.TextBox>.</span></span>

5. <span data-ttu-id="c7700-227">Przeciągnij tekst do kontrolki okręgu.</span><span class="sxs-lookup"><span data-stu-id="c7700-227">Drag the text to a Circle control.</span></span> <span data-ttu-id="c7700-228">Zauważ, że kursor teraz zmienia się, aby wskazać, że upuszczenie nie jest `gre` dozwolone, ponieważ nie jest prawidłowym kolorem.</span><span class="sxs-lookup"><span data-stu-id="c7700-228">Notice that the cursor now changes to indicate that the drop is not allowed because `gre` is not a valid color.</span></span>

 <span data-ttu-id="c7700-229">Możesz bardziej usprawnić środowisko użytkownika, stosując podgląd operacji usuwania.</span><span class="sxs-lookup"><span data-stu-id="c7700-229">You can further enhance the user experience by applying a preview of the drop operation.</span></span> <span data-ttu-id="c7700-230">W przypadku kontrolki użytkownika Circle można zastąpić <xref:System.Windows.UIElement.OnDragEnter%2A> metody i. <xref:System.Windows.UIElement.OnDragLeave%2A></span><span class="sxs-lookup"><span data-stu-id="c7700-230">For the Circle user control, you will override the <xref:System.Windows.UIElement.OnDragEnter%2A> and <xref:System.Windows.UIElement.OnDragLeave%2A> methods.</span></span> <span data-ttu-id="c7700-231">Gdy dane są przeciągane nad formantem, bieżące tło <xref:System.Windows.Shapes.Shape.Fill%2A> jest zapisywane w zmiennej zastępczej.</span><span class="sxs-lookup"><span data-stu-id="c7700-231">When the data is dragged over the control, the current background <xref:System.Windows.Shapes.Shape.Fill%2A> is saved in a placeholder variable.</span></span> <span data-ttu-id="c7700-232">Ciąg jest następnie konwertowany na pędzel i zastosowany do <xref:System.Windows.Shapes.Ellipse> , który zapewnia interfejs użytkownika koła.</span><span class="sxs-lookup"><span data-stu-id="c7700-232">The string is then converted to a brush and applied to the <xref:System.Windows.Shapes.Ellipse> that provides the Circle's UI.</span></span> <span data-ttu-id="c7700-233">Jeśli dane są przeciągane z okręgu bez porzucenia, oryginalna <xref:System.Windows.Shapes.Shape.Fill%2A> wartość zostanie ponownie zastosowana do okręgu.</span><span class="sxs-lookup"><span data-stu-id="c7700-233">If the data is dragged out of the Circle without being dropped, the original <xref:System.Windows.Shapes.Shape.Fill%2A> value is re-applied to the Circle.</span></span>

### <a name="to-preview-the-effects-of-the-drag-and-drop-operation"></a><span data-ttu-id="c7700-234">Aby wyświetlić podgląd efektów operacji przeciągania i upuszczania</span><span class="sxs-lookup"><span data-stu-id="c7700-234">To preview the effects of the drag-and-drop operation</span></span>

1. <span data-ttu-id="c7700-235">Otwórz Circle.xaml.cs lub Circle. XAML. vb.</span><span class="sxs-lookup"><span data-stu-id="c7700-235">Open Circle.xaml.cs or Circle.xaml.vb.</span></span>

2. <span data-ttu-id="c7700-236">W klasie Circle Zadeklaruj zmienną prywatną <xref:System.Windows.Media.Brush> o nazwie `_previousFill` i zainicjuj ją `null`w.</span><span class="sxs-lookup"><span data-stu-id="c7700-236">In the Circle class, declare a private <xref:System.Windows.Media.Brush> variable named `_previousFill` and initialize it to `null`.</span></span>

     [!code-csharp[DragDropWalkthrough#Brush](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#brush)]
     [!code-vb[DragDropWalkthrough#Brush](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#brush)]

3. <span data-ttu-id="c7700-237">Dodaj następujące <xref:System.Windows.UIElement.OnDragEnter%2A> zastąpienie, aby zapewnić obsługę klasy <xref:System.Windows.UIElement.DragEnter> dla zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="c7700-237">Add the following <xref:System.Windows.UIElement.OnDragEnter%2A> override to provide class handling for the <xref:System.Windows.UIElement.DragEnter> event.</span></span>

     [!code-csharp[DragDropWalkthrough#OnDragEnter](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#ondragenter)]
     [!code-vb[DragDropWalkthrough#OnDragEnter](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#ondragenter)]

     <span data-ttu-id="c7700-238">To <xref:System.Windows.UIElement.OnDragEnter%2A> przesłonięcie wykonuje następujące zadania:</span><span class="sxs-lookup"><span data-stu-id="c7700-238">This <xref:System.Windows.UIElement.OnDragEnter%2A> override performs the following tasks:</span></span>

    - <span data-ttu-id="c7700-239"><xref:System.Windows.Shapes.Shape.Fill%2A> Zapisuje Właściwość <xref:System.Windows.Shapes.Ellipse> w zmiennej.`_previousFill`</span><span class="sxs-lookup"><span data-stu-id="c7700-239">Saves the <xref:System.Windows.Shapes.Shape.Fill%2A> property of the <xref:System.Windows.Shapes.Ellipse> in the `_previousFill` variable.</span></span>

    - <span data-ttu-id="c7700-240">Wykonuje te same kontrole, które są wykonywane w <xref:System.Windows.UIElement.OnDrop%2A> metodzie, aby określić, czy dane mogą być konwertowane <xref:System.Windows.Media.Brush>na.</span><span class="sxs-lookup"><span data-stu-id="c7700-240">Performs the same checks that are performed in the <xref:System.Windows.UIElement.OnDrop%2A> method to determine whether the data can be converted to a <xref:System.Windows.Media.Brush>.</span></span>

    - <span data-ttu-id="c7700-241">Jeśli dane są konwertowane na prawidłowe <xref:System.Windows.Media.Brush>, stosuje je <xref:System.Windows.Shapes.Shape.Fill%2A> do <xref:System.Windows.Shapes.Ellipse>.</span><span class="sxs-lookup"><span data-stu-id="c7700-241">If the data is converted to a valid <xref:System.Windows.Media.Brush>, applies it to the <xref:System.Windows.Shapes.Shape.Fill%2A> of the <xref:System.Windows.Shapes.Ellipse>.</span></span>

4. <span data-ttu-id="c7700-242">Dodaj następujące <xref:System.Windows.UIElement.OnDragLeave%2A> zastąpienie, aby zapewnić obsługę klasy <xref:System.Windows.UIElement.DragLeave> dla zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="c7700-242">Add the following <xref:System.Windows.UIElement.OnDragLeave%2A> override to provide class handling for the <xref:System.Windows.UIElement.DragLeave> event.</span></span>

     [!code-csharp[DragDropWalkthrough#OnDragLeave](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#ondragleave)]
     [!code-vb[DragDropWalkthrough#OnDragLeave](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#ondragleave)]

     <span data-ttu-id="c7700-243">To <xref:System.Windows.UIElement.OnDragLeave%2A> przesłonięcie wykonuje następujące zadania:</span><span class="sxs-lookup"><span data-stu-id="c7700-243">This <xref:System.Windows.UIElement.OnDragLeave%2A> override performs the following tasks:</span></span>

    - <span data-ttu-id="c7700-244">Stosuje zapisany w `_previousFill` zmiennejdo<xref:System.Windows.Shapes.Shape.Fill%2A> elementu ,któryzapewniainterfejsużytkownikadlakontrolkiużytkownikkółka.<xref:System.Windows.Shapes.Ellipse> <xref:System.Windows.Media.Brush></span><span class="sxs-lookup"><span data-stu-id="c7700-244">Applies the <xref:System.Windows.Media.Brush> saved in the `_previousFill` variable to the <xref:System.Windows.Shapes.Shape.Fill%2A> of the <xref:System.Windows.Shapes.Ellipse> that provides the UI of the Circle user control.</span></span>

5. <span data-ttu-id="c7700-245">Naciśnij klawisz **F5** , aby skompilować i uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="c7700-245">Press **F5** to build and run the application.</span></span>

6. <span data-ttu-id="c7700-246">Zaznacz tekst `green` <xref:System.Windows.Controls.TextBox>w.</span><span class="sxs-lookup"><span data-stu-id="c7700-246">Select the text `green` in the <xref:System.Windows.Controls.TextBox>.</span></span>

7. <span data-ttu-id="c7700-247">Przeciągnij tekst nad kontrolką okręgu bez porzucania go.</span><span class="sxs-lookup"><span data-stu-id="c7700-247">Drag the text over a Circle control without dropping it.</span></span> <span data-ttu-id="c7700-248">Okrąg zmieni się z niebieski na zielony.</span><span class="sxs-lookup"><span data-stu-id="c7700-248">The Circle changes from blue to green.</span></span>

     <span data-ttu-id="c7700-249">![Podgląd efektów operacji przeciągania&#45;i upuszczania&#45;](./media/dragdrop-previeweffects.png "DragDrop_PreviewEffects")</span><span class="sxs-lookup"><span data-stu-id="c7700-249">![Preview the effects of a drag&#45;and&#45;drop operation](./media/dragdrop-previeweffects.png "DragDrop_PreviewEffects")</span></span>

8. <span data-ttu-id="c7700-250">Przeciągnij tekst poza formant okręgu.</span><span class="sxs-lookup"><span data-stu-id="c7700-250">Drag the text away from the Circle control.</span></span> <span data-ttu-id="c7700-251">Okrąg zmieni się z zielonej z powrotem na niebieską.</span><span class="sxs-lookup"><span data-stu-id="c7700-251">The Circle changes from green back to blue.</span></span>

## <a name="enable-a-panel-to-receive-dropped-data"></a><span data-ttu-id="c7700-252">Włącz panel do odbierania porzuconych danych</span><span class="sxs-lookup"><span data-stu-id="c7700-252">Enable a Panel to Receive Dropped Data</span></span>

<span data-ttu-id="c7700-253">W tej sekcji włączasz panele obsługujące kontrolki użytkownika kółka, aby pełnić rolę obiektów docelowych dla przeciąganych danych.</span><span class="sxs-lookup"><span data-stu-id="c7700-253">In this section, you enable the panels that host the Circle user controls to act as drop targets for dragged Circle data.</span></span> <span data-ttu-id="c7700-254">Zaimplementowano kod, który umożliwia przesuwanie okręgu z jednego panelu do drugiego lub tworzenie kopii kontrolki okręgu przez przytrzymanie klawisza **Ctrl** podczas przeciągania i upuszczania okręgu.</span><span class="sxs-lookup"><span data-stu-id="c7700-254">You will implement code that enables you to move a Circle from one panel to another, or to make a copy of a Circle control by holding down the **Ctrl** key while dragging and dropping a Circle.</span></span>

1. <span data-ttu-id="c7700-255">Open MainWindow.xaml.</span><span class="sxs-lookup"><span data-stu-id="c7700-255">Open MainWindow.xaml.</span></span>

2. <span data-ttu-id="c7700-256">Jak pokazano w poniższym kodzie XAML, w każdej <xref:System.Windows.Controls.StackPanel> kontrolce Dodaj programy obsługi <xref:System.Windows.UIElement.DragOver> dla zdarzeń i <xref:System.Windows.UIElement.Drop> .</span><span class="sxs-lookup"><span data-stu-id="c7700-256">As shown in the following XAML, in each of the <xref:System.Windows.Controls.StackPanel> controls, add handlers for the <xref:System.Windows.UIElement.DragOver> and <xref:System.Windows.UIElement.Drop> events.</span></span> <span data-ttu-id="c7700-257">Nazwij program obsługi <xref:System.Windows.UIElement.Drop> `panel_DragOver` <xref:System.Windows.UIElement.DragOver> zdarzeń, a następnie `panel_Drop`Nazwij procedurę obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="c7700-257">Name the <xref:System.Windows.UIElement.DragOver> event handler, `panel_DragOver`, and name the <xref:System.Windows.UIElement.Drop> event handler, `panel_Drop`.</span></span>

     [!code-xaml[DragDropWalkthrough#PanelsXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/MainWindow.xaml#panelsxaml)]

3. <span data-ttu-id="c7700-258">Otwórz MainWindows.xaml.cs lub MainWindow. XAML. vb.</span><span class="sxs-lookup"><span data-stu-id="c7700-258">Open MainWindows.xaml.cs or MainWindow.xaml.vb.</span></span>

4. <span data-ttu-id="c7700-259">Dodaj następujący kod dla <xref:System.Windows.UIElement.DragOver> programu obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="c7700-259">Add the following code for the <xref:System.Windows.UIElement.DragOver> event handler.</span></span>

     [!code-csharp[DragDropWalkthrough#PanelDragOver](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/MainWindow.xaml.cs#paneldragover)]
     [!code-vb[DragDropWalkthrough#PanelDragOver](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/MainWindow.xaml.vb#paneldragover)]

     <span data-ttu-id="c7700-260">Ten <xref:System.Windows.UIElement.DragOver> program obsługi zdarzeń wykonuje następujące zadania:</span><span class="sxs-lookup"><span data-stu-id="c7700-260">This <xref:System.Windows.UIElement.DragOver> event handler performs the following tasks:</span></span>

    - <span data-ttu-id="c7700-261">Sprawdza, czy przeciągane dane zawierają dane "obiekt", które zostały spakowane w <xref:System.Windows.DataObject> przez okrągłą kontrolkę użytkownika i przechodzą w <xref:System.Windows.DragDrop.DoDragDrop%2A>wywołaniu.</span><span class="sxs-lookup"><span data-stu-id="c7700-261">Checks that the dragged data contains the "Object" data that was packaged in the <xref:System.Windows.DataObject> by the Circle user control and passed in the call to <xref:System.Windows.DragDrop.DoDragDrop%2A>.</span></span>

    - <span data-ttu-id="c7700-262">Jeśli istnieją dane "Object", sprawdź, czy klawisz **Ctrl** został naciśnięty.</span><span class="sxs-lookup"><span data-stu-id="c7700-262">If the "Object" data is present, checks whether the **Ctrl** key is pressed.</span></span>

    - <span data-ttu-id="c7700-263">Po naciśnięciu klawisza **Ctrl** ustawia <xref:System.Windows.DragEventArgs.Effects%2A> właściwość na <xref:System.Windows.DragDropEffects.Copy>.</span><span class="sxs-lookup"><span data-stu-id="c7700-263">If the **Ctrl** key is pressed, sets the <xref:System.Windows.DragEventArgs.Effects%2A> property to <xref:System.Windows.DragDropEffects.Copy>.</span></span> <span data-ttu-id="c7700-264">W przeciwnym razie ustaw <xref:System.Windows.DragEventArgs.Effects%2A> właściwość na <xref:System.Windows.DragDropEffects.Move>.</span><span class="sxs-lookup"><span data-stu-id="c7700-264">Otherwise, set the <xref:System.Windows.DragEventArgs.Effects%2A> property to <xref:System.Windows.DragDropEffects.Move>.</span></span>

5. <span data-ttu-id="c7700-265">Dodaj następujący kod dla <xref:System.Windows.UIElement.Drop> programu obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="c7700-265">Add the following code for the <xref:System.Windows.UIElement.Drop> event handler.</span></span>

     [!code-csharp[DragDropWalkthrough#PanelDrop](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/MainWindow.xaml.cs#paneldrop)]
     [!code-vb[DragDropWalkthrough#PanelDrop](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/MainWindow.xaml.vb#paneldrop)]

     <span data-ttu-id="c7700-266">Ten <xref:System.Windows.UIElement.Drop> program obsługi zdarzeń wykonuje następujące zadania:</span><span class="sxs-lookup"><span data-stu-id="c7700-266">This <xref:System.Windows.UIElement.Drop> event handler performs the following tasks:</span></span>

    - <span data-ttu-id="c7700-267">Sprawdza, <xref:System.Windows.UIElement.Drop> czy zdarzenie zostało już obsłużone.</span><span class="sxs-lookup"><span data-stu-id="c7700-267">Checks whether the <xref:System.Windows.UIElement.Drop> event has already been handled.</span></span> <span data-ttu-id="c7700-268">Na przykład, jeśli okrąg zostanie porzucony w innym okręgu, który <xref:System.Windows.UIElement.Drop> obsługuje zdarzenie, nie chcesz, aby panel, który zawiera okrąg, również go obsłużyć.</span><span class="sxs-lookup"><span data-stu-id="c7700-268">For instance, if a Circle is dropped on another Circle which handles the <xref:System.Windows.UIElement.Drop> event, you do not want the panel that contains the Circle to also handle it.</span></span>

    - <span data-ttu-id="c7700-269">Jeśli zdarzenie nie jest obsługiwane, sprawdza, czy klawisz Ctrl został naciśnięty. <xref:System.Windows.UIElement.Drop></span><span class="sxs-lookup"><span data-stu-id="c7700-269">If the <xref:System.Windows.UIElement.Drop> event is not handled, checks whether the **Ctrl** key is pressed.</span></span>

    - <span data-ttu-id="c7700-270">Jeśli klawisz **Ctrl** zostanie wciśnięty <xref:System.Windows.UIElement.Drop> , program tworzy kopię kontrolki Circle i <xref:System.Windows.Controls.Panel.Children%2A> dodaje ją do kolekcji <xref:System.Windows.Controls.StackPanel>.</span><span class="sxs-lookup"><span data-stu-id="c7700-270">If the **Ctrl** key is pressed when the <xref:System.Windows.UIElement.Drop> happens, makes a copy of the Circle control and add it to the <xref:System.Windows.Controls.Panel.Children%2A> collection of the <xref:System.Windows.Controls.StackPanel>.</span></span>

    - <span data-ttu-id="c7700-271">Jeśli klawisz **Ctrl** nie zostanie wciśnięty, przenosi okrąg z <xref:System.Windows.Controls.Panel.Children%2A> kolekcji jego panelu <xref:System.Windows.Controls.Panel.Children%2A> nadrzędnego do kolekcji panelu, w którym została porzucona.</span><span class="sxs-lookup"><span data-stu-id="c7700-271">If the **Ctrl** key is not pressed, moves the Circle from the <xref:System.Windows.Controls.Panel.Children%2A> collection of its parent panel to the <xref:System.Windows.Controls.Panel.Children%2A> collection of the panel that it was dropped on.</span></span>

    - <span data-ttu-id="c7700-272">Ustawia właściwość w taki sposób, <xref:System.Windows.DragDrop.DoDragDrop%2A> aby powiadamiał metodę o tym, czy operacja przenoszenia lub kopiowania została wykonana. <xref:System.Windows.DragEventArgs.Effects%2A></span><span class="sxs-lookup"><span data-stu-id="c7700-272">Sets the <xref:System.Windows.DragEventArgs.Effects%2A> property to notify the <xref:System.Windows.DragDrop.DoDragDrop%2A> method whether a move or copy operation was performed.</span></span>

6. <span data-ttu-id="c7700-273">Naciśnij klawisz **F5** , aby skompilować i uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="c7700-273">Press **F5** to build and run the application.</span></span>

7. <span data-ttu-id="c7700-274">Wybierz tekst `green` <xref:System.Windows.Controls.TextBox>z.</span><span class="sxs-lookup"><span data-stu-id="c7700-274">Select the text `green` from the <xref:System.Windows.Controls.TextBox>.</span></span>

8. <span data-ttu-id="c7700-275">Przeciągnij tekst nad kontrolką okręgu i upuść go.</span><span class="sxs-lookup"><span data-stu-id="c7700-275">Drag the text over a Circle control and drop it.</span></span>

9. <span data-ttu-id="c7700-276">Przeciągnij kontrolkę Circle z lewego panelu do prawego panelu i upuść ją.</span><span class="sxs-lookup"><span data-stu-id="c7700-276">Drag a Circle control from the left panel to the right panel and drop it.</span></span> <span data-ttu-id="c7700-277">Okrąg zostanie usunięty z <xref:System.Windows.Controls.Panel.Children%2A> kolekcji lewego panelu i dodany do kolekcji Children panelu po prawej stronie.</span><span class="sxs-lookup"><span data-stu-id="c7700-277">The Circle is removed from the <xref:System.Windows.Controls.Panel.Children%2A> collection of the left panel and added to the Children collection of the right panel.</span></span>

10. <span data-ttu-id="c7700-278">Przeciągnij kontrolkę Circle z panelu do drugiego panelu i upuść ją podczas naciskania klawisza **Ctrl** .</span><span class="sxs-lookup"><span data-stu-id="c7700-278">Drag a Circle control from the panel it is in to the other panel and drop it while pressing the **Ctrl** key.</span></span> <span data-ttu-id="c7700-279">Okrąg jest kopiowany, a kopia zostanie dodana do <xref:System.Windows.Controls.Panel.Children%2A> kolekcji panelu odbiorczego.</span><span class="sxs-lookup"><span data-stu-id="c7700-279">The Circle is copied and the copy is added to the <xref:System.Windows.Controls.Panel.Children%2A> collection of the receiving panel.</span></span>

     <span data-ttu-id="c7700-280">![Przeciąganie okręgu podczas naciskania klawisza Ctrl](./media/dragdrop-paneldrop.png "DragDrop_PanelDrop")</span><span class="sxs-lookup"><span data-stu-id="c7700-280">![Dragging a Circle while pressing the CTRL key](./media/dragdrop-paneldrop.png "DragDrop_PanelDrop")</span></span>

## <a name="see-also"></a><span data-ttu-id="c7700-281">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c7700-281">See also</span></span>

- [<span data-ttu-id="c7700-282">Przegląd przeciągania i upuszczania</span><span class="sxs-lookup"><span data-stu-id="c7700-282">Drag and Drop Overview</span></span>](drag-and-drop-overview.md)
