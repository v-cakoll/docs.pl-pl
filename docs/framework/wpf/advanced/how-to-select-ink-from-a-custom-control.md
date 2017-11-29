---
title: "Porady: wybrać atrament w niestandardowej kontrolce"
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
- controls [WPF], ink selection
- ink [WPF], selecting from custom control
- custom controls [WPF], ink selection
ms.assetid: 5f3a45c6-6d40-4017-9b47-933f134ceba3
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: dd9693209cc35ecd3c0473133b7c21639a239ff5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-select-ink-from-a-custom-control"></a><span data-ttu-id="a2f7c-102">Porady: wybrać atrament w niestandardowej kontrolce</span><span class="sxs-lookup"><span data-stu-id="a2f7c-102">How to: Select Ink from a Custom Control</span></span>
<span data-ttu-id="a2f7c-103">Dodając <xref:System.Windows.Ink.IncrementalLassoHitTester> do formantu niestandardowego można włączyć formantu, dzięki czemu użytkownik może wybrać odręczne za pomocą narzędzia lasso, podobnie jak <xref:System.Windows.Controls.InkCanvas> wybiera z pewnymi lasso.</span><span class="sxs-lookup"><span data-stu-id="a2f7c-103">By adding an <xref:System.Windows.Ink.IncrementalLassoHitTester> to your custom control, you can enable your control so that a user can select ink with a lasso tool, similar to the way the <xref:System.Windows.Controls.InkCanvas> selects ink with a lasso.</span></span>  
  
 <span data-ttu-id="a2f7c-104">W tym przykładzie przyjęto założenie, że znasz tworzenia włączone odręczne kontrolek niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="a2f7c-104">This example assumes you are familiar with creating an ink-enabled custom control.</span></span>  <span data-ttu-id="a2f7c-105">Aby utworzyć niestandardowego formantu, który akceptuje odręczne, zobacz [tworzenia kontrolki wprowadzania odręcznego](../../../../docs/framework/wpf/advanced/creating-an-ink-input-control.md).</span><span class="sxs-lookup"><span data-stu-id="a2f7c-105">To create a custom control that accepts ink input, see [Creating an Ink Input Control](../../../../docs/framework/wpf/advanced/creating-an-ink-input-control.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="a2f7c-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="a2f7c-106">Example</span></span>  
 <span data-ttu-id="a2f7c-107">Gdy użytkownik wprowadzi lasso <xref:System.Windows.Ink.IncrementalLassoHitTester> prognozuje linie, które będą w granicach ścieżki lasso po podaniu polu.</span><span class="sxs-lookup"><span data-stu-id="a2f7c-107">When the user draws a lasso, the <xref:System.Windows.Ink.IncrementalLassoHitTester> predicts which strokes will be within the lasso path's boundaries after the user completes the lasso.</span></span>  <span data-ttu-id="a2f7c-108">Kreślone okażą się w granicach ścieżki lasso można traktować jako zaznaczony.</span><span class="sxs-lookup"><span data-stu-id="a2f7c-108">Strokes that are determined to be within the lasso path's boundaries can be thought of as being selected.</span></span>  <span data-ttu-id="a2f7c-109">Wybranych pociągnięć może również zostać usunięte.</span><span class="sxs-lookup"><span data-stu-id="a2f7c-109">Selected strokes can also become unselected.</span></span>  <span data-ttu-id="a2f7c-110">Na przykład, jeśli użytkownik zmieni kierunek podczas rysowania lasso <xref:System.Windows.Ink.IncrementalLassoHitTester> może usunąć zaznaczenie niektórych pociągnięć.</span><span class="sxs-lookup"><span data-stu-id="a2f7c-110">For example, if the user reverses direction while drawing the lasso, the <xref:System.Windows.Ink.IncrementalLassoHitTester> may unselect some strokes.</span></span>  
  
 <span data-ttu-id="a2f7c-111"><xref:System.Windows.Ink.IncrementalLassoHitTester> Zgłasza <xref:System.Windows.Ink.IncrementalLassoHitTester.SelectionChanged> zdarzeń, dzięki czemu formantu niestandardowego podczas rysowania polu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="a2f7c-111">The <xref:System.Windows.Ink.IncrementalLassoHitTester> raises the <xref:System.Windows.Ink.IncrementalLassoHitTester.SelectionChanged> event, which enables your custom control to respond while the user is drawing the lasso.</span></span>  <span data-ttu-id="a2f7c-112">Na przykład można zmienić wygląd pociągnięć, ponieważ użytkownik wybiera i usuwa je.</span><span class="sxs-lookup"><span data-stu-id="a2f7c-112">For example, you can change the appearance of strokes as the user selects and unselects them.</span></span>  
  
## <a name="managing-the-ink-mode"></a><span data-ttu-id="a2f7c-113">Zarządzanie trybie odręcznego</span><span class="sxs-lookup"><span data-stu-id="a2f7c-113">Managing the Ink Mode</span></span>  
 <span data-ttu-id="a2f7c-114">Jest przydatne do użytkownika, jeśli polu pojawia się inaczej niż pismo odręczne na formantu.</span><span class="sxs-lookup"><span data-stu-id="a2f7c-114">It is helpful to the user if the lasso appears differently than the ink on your control.</span></span> <span data-ttu-id="a2f7c-115">W tym celu formantu niestandardowego należy zachować informacje o czy zapisywania lub wybranie odręczne użytkownika.</span><span class="sxs-lookup"><span data-stu-id="a2f7c-115">To accomplish this, your custom control must keep track of whether the user is writing or selecting ink.</span></span> <span data-ttu-id="a2f7c-116">W tym celu najłatwiej zadeklarować wyliczenie z dwóch wartości: jedna, aby wskazać zapisuje użytkownika i odręcznego jedna, aby wskazać, że użytkownik wybiera odręczne.</span><span class="sxs-lookup"><span data-stu-id="a2f7c-116">The easiest way to do this is to declare an enumeration with two values: one to indicate that the user is writing ink and one to indicate that the user is selecting ink.</span></span>  
  
 [!code-csharp[HowToSelectInk#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToSelectInk/CSharp/InkSelector.cs#2)]
 [!code-vb[HowToSelectInk#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HowToSelectInk/VisualBasic/InkSelector.vb#2)]  
  
 <span data-ttu-id="a2f7c-117">Następnie dodaj dwie <xref:System.Windows.Ink.DrawingAttributes> do klasy: należy użyć, gdy użytkownik zapisuje odręczne, należy użyć, gdy użytkownik wybierze odręczne.</span><span class="sxs-lookup"><span data-stu-id="a2f7c-117">Next, add two <xref:System.Windows.Ink.DrawingAttributes> to the class: one to use when the user writes ink, one to use when the user selects ink.</span></span>  <span data-ttu-id="a2f7c-118">W Konstruktorze zainicjować <xref:System.Windows.Ink.DrawingAttributes> i Dołącz zarówno <xref:System.Windows.Ink.DrawingAttributes.AttributeChanged> zdarzenia do tej procedury obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="a2f7c-118">In the constructor, initialize the <xref:System.Windows.Ink.DrawingAttributes> and attach both <xref:System.Windows.Ink.DrawingAttributes.AttributeChanged> events to the same event handler.</span></span> <span data-ttu-id="a2f7c-119">Następnie ustaw <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer.DrawingAttributes%2A> właściwość <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> do pisma odręcznego <xref:System.Windows.Ink.DrawingAttributes>.</span><span class="sxs-lookup"><span data-stu-id="a2f7c-119">Then set the <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer.DrawingAttributes%2A> property of the <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> to the ink <xref:System.Windows.Ink.DrawingAttributes>.</span></span>  
  
 [!code-csharp[HowToSelectInk#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToSelectInk/CSharp/InkSelector.cs#3)]
 [!code-vb[HowToSelectInk#3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HowToSelectInk/VisualBasic/InkSelector.vb#3)]  
[!code-csharp[HowToSelectInk#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToSelectInk/CSharp/InkSelector.cs#4)]
[!code-vb[HowToSelectInk#4](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HowToSelectInk/VisualBasic/InkSelector.vb#4)]  
  
 <span data-ttu-id="a2f7c-120">Dodaj właściwości, która udostępnia tryb zaznaczania.</span><span class="sxs-lookup"><span data-stu-id="a2f7c-120">Add a property that exposes the selection mode.</span></span> <span data-ttu-id="a2f7c-121">Gdy użytkownik zmieni tryb zaznaczania, ustaw <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer.DrawingAttributes%2A> właściwość <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> do odpowiedniego <xref:System.Windows.Ink.DrawingAttributes> obiekt, a następnie ponownie dołączyć <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer.RootVisual%2A> właściwości <xref:System.Windows.Controls.InkPresenter>.</span><span class="sxs-lookup"><span data-stu-id="a2f7c-121">When the user changes the selection mode, set the <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer.DrawingAttributes%2A> property of the <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> to the appropriate <xref:System.Windows.Ink.DrawingAttributes> object and then reattach the <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer.RootVisual%2A> Property to the <xref:System.Windows.Controls.InkPresenter>.</span></span>  
  
 [!code-csharp[HowToSelectInk#5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToSelectInk/CSharp/InkSelector.cs#5)]
 [!code-vb[HowToSelectInk#5](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HowToSelectInk/VisualBasic/InkSelector.vb#5)]  
  
 <span data-ttu-id="a2f7c-122">Udostępnianie <xref:System.Windows.Ink.DrawingAttributes> jako właściwości, dzięki czemu aplikacje można określić wygląd pociągnięć i wyboru pociągnięć.</span><span class="sxs-lookup"><span data-stu-id="a2f7c-122">Expose the <xref:System.Windows.Ink.DrawingAttributes> as properties so applications can determine the appearance of the ink strokes and selection strokes.</span></span>  
  
 [!code-csharp[HowToSelectInk#6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToSelectInk/CSharp/InkSelector.cs#6)]
 [!code-vb[HowToSelectInk#6](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HowToSelectInk/VisualBasic/InkSelector.vb#6)]  
  
 <span data-ttu-id="a2f7c-123">Gdy właściwość <xref:System.Windows.Ink.DrawingAttributes> obiekt zmian, <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer.RootVisual%2A> musi zostać ponownie nałożona do <xref:System.Windows.Controls.InkPresenter>.</span><span class="sxs-lookup"><span data-stu-id="a2f7c-123">When a property of a <xref:System.Windows.Ink.DrawingAttributes> object changes, the <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer.RootVisual%2A> must be reattached to the <xref:System.Windows.Controls.InkPresenter>.</span></span>  <span data-ttu-id="a2f7c-124">W obsłudze zdarzeń dla <xref:System.Windows.Ink.DrawingAttributes.AttributeChanged> zdarzeń, podłącz <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer.RootVisual%2A> do <xref:System.Windows.Controls.InkPresenter>.</span><span class="sxs-lookup"><span data-stu-id="a2f7c-124">In the event handler for the <xref:System.Windows.Ink.DrawingAttributes.AttributeChanged> event, reattach the <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer.RootVisual%2A> to the <xref:System.Windows.Controls.InkPresenter>.</span></span>  
  
 [!code-csharp[HowToSelectInk#7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToSelectInk/CSharp/InkSelector.cs#7)]
 [!code-vb[HowToSelectInk#7](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HowToSelectInk/VisualBasic/InkSelector.vb#7)]  
  
## <a name="using-the-incrementallassohittester"></a><span data-ttu-id="a2f7c-125">Przy użyciu IncrementalLassoHitTester</span><span class="sxs-lookup"><span data-stu-id="a2f7c-125">Using the IncrementalLassoHitTester</span></span>  
 <span data-ttu-id="a2f7c-126">Utwórz i zainicjuj <xref:System.Windows.Ink.StrokeCollection> zawierający wybranych pociągnięć.</span><span class="sxs-lookup"><span data-stu-id="a2f7c-126">Create and initialize a <xref:System.Windows.Ink.StrokeCollection> that contains the selected strokes.</span></span>  
  
 [!code-csharp[HowToSelectInk#8](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToSelectInk/CSharp/InkSelector.cs#8)]
 [!code-vb[HowToSelectInk#8](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HowToSelectInk/VisualBasic/InkSelector.vb#8)]  
  
 <span data-ttu-id="a2f7c-127">Uruchomienia użytkownika do rysowania pociągnięcia odręczne lub lasso, usuń zaznaczenie żadnych wybranych pociągnięć.</span><span class="sxs-lookup"><span data-stu-id="a2f7c-127">When the user starts to draw a stroke, either ink or the lasso, unselect any selected strokes.</span></span> <span data-ttu-id="a2f7c-128">Następnie, jeśli użytkownik jest rysowania lasso, Utwórz <xref:System.Windows.Ink.IncrementalLassoHitTester> przez wywołanie metody <xref:System.Windows.Ink.StrokeCollection.GetIncrementalLassoHitTester%2A>, subskrybować <xref:System.Windows.Ink.IncrementalLassoHitTester.SelectionChanged> zdarzeń i wywołania <xref:System.Windows.Ink.IncrementalHitTester.AddPoints%2A>.</span><span class="sxs-lookup"><span data-stu-id="a2f7c-128">Then, if the user is drawing a lasso, create an <xref:System.Windows.Ink.IncrementalLassoHitTester> by calling <xref:System.Windows.Ink.StrokeCollection.GetIncrementalLassoHitTester%2A>, subscribe to the <xref:System.Windows.Ink.IncrementalLassoHitTester.SelectionChanged> event, and call <xref:System.Windows.Ink.IncrementalHitTester.AddPoints%2A>.</span></span> <span data-ttu-id="a2f7c-129">Ten kod może być metodą oddzielne i wywoływać z <xref:System.Windows.UIElement.OnStylusDown%2A> i <xref:System.Windows.UIElement.OnMouseDown%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="a2f7c-129">This code can be a separate method and called from the <xref:System.Windows.UIElement.OnStylusDown%2A> and <xref:System.Windows.UIElement.OnMouseDown%2A> methods.</span></span>  
  
 [!code-csharp[HowToSelectInk#9](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToSelectInk/CSharp/InkSelector.cs#9)]
 [!code-vb[HowToSelectInk#9](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HowToSelectInk/VisualBasic/InkSelector.vb#9)]  
  
 <span data-ttu-id="a2f7c-130">Dodawanie punktów Pióro do <xref:System.Windows.Ink.IncrementalLassoHitTester> podczas, gdy użytkownik wprowadzi polu.</span><span class="sxs-lookup"><span data-stu-id="a2f7c-130">Add the stylus points to the <xref:System.Windows.Ink.IncrementalLassoHitTester> while the user draws the lasso.</span></span>  <span data-ttu-id="a2f7c-131">Wywołanie następującej metody z <xref:System.Windows.UIElement.OnStylusMove%2A>, <xref:System.Windows.UIElement.OnStylusUp%2A>, <xref:System.Windows.UIElement.OnMouseMove%2A>, i <xref:System.Windows.UIElement.OnMouseLeftButtonUp%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="a2f7c-131">Call the following method from the <xref:System.Windows.UIElement.OnStylusMove%2A>, <xref:System.Windows.UIElement.OnStylusUp%2A>, <xref:System.Windows.UIElement.OnMouseMove%2A>, and <xref:System.Windows.UIElement.OnMouseLeftButtonUp%2A> methods.</span></span>  
  
 [!code-csharp[HowToSelectInk#10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToSelectInk/CSharp/InkSelector.cs#10)]
 [!code-vb[HowToSelectInk#10](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HowToSelectInk/VisualBasic/InkSelector.vb#10)]  
  
 <span data-ttu-id="a2f7c-132">Obsługa <xref:System.Windows.Ink.IncrementalLassoHitTester.SelectionChanged?displayProperty=nameWithType> zdarzeń odpowiadać, gdy użytkownik wybiera i usuwa pociągnięć.</span><span class="sxs-lookup"><span data-stu-id="a2f7c-132">Handle the <xref:System.Windows.Ink.IncrementalLassoHitTester.SelectionChanged?displayProperty=nameWithType> event to respond when the user selects and unselects strokes.</span></span>  <span data-ttu-id="a2f7c-133"><xref:System.Windows.Ink.LassoSelectionChangedEventArgs> Klasa ma <xref:System.Windows.Ink.LassoSelectionChangedEventArgs.SelectedStrokes%2A> i <xref:System.Windows.Ink.LassoSelectionChangedEventArgs.DeselectedStrokes%2A> właściwości, które pobierają pociągnięć, które zostały zaznaczony i niezaznaczony, odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="a2f7c-133">The <xref:System.Windows.Ink.LassoSelectionChangedEventArgs> class has the <xref:System.Windows.Ink.LassoSelectionChangedEventArgs.SelectedStrokes%2A> and <xref:System.Windows.Ink.LassoSelectionChangedEventArgs.DeselectedStrokes%2A> properties that get the strokes that were selected and unselected, respectively.</span></span>  
  
 [!code-csharp[HowToSelectInk#11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToSelectInk/CSharp/InkSelector.cs#11)]
 [!code-vb[HowToSelectInk#11](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HowToSelectInk/VisualBasic/InkSelector.vb#11)]  
  
 <span data-ttu-id="a2f7c-134">Gdy użytkownik zakończy rysowania w polu, subskrypcję <xref:System.Windows.Ink.IncrementalLassoHitTester.SelectionChanged> zdarzeń i wywołania <xref:System.Windows.Ink.IncrementalHitTester.EndHitTesting%2A>.</span><span class="sxs-lookup"><span data-stu-id="a2f7c-134">When the user finishes drawing the lasso, unsubscribe from the <xref:System.Windows.Ink.IncrementalLassoHitTester.SelectionChanged> event and call <xref:System.Windows.Ink.IncrementalHitTester.EndHitTesting%2A>.</span></span>  
  
 [!code-csharp[HowToSelectInk#12](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToSelectInk/CSharp/InkSelector.cs#12)]
 [!code-vb[HowToSelectInk#12](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HowToSelectInk/VisualBasic/InkSelector.vb#12)]  
  
## <a name="putting-it-all-together"></a><span data-ttu-id="a2f7c-135">Wprowadzanie wszystkich ze sobą.</span><span class="sxs-lookup"><span data-stu-id="a2f7c-135">Putting it All Together.</span></span>  
 <span data-ttu-id="a2f7c-136">Poniższy przykład jest kontrolki niestandardowej, która umożliwia użytkownikowi wybranie z pewnymi lasso.</span><span class="sxs-lookup"><span data-stu-id="a2f7c-136">The following example is a custom control that enables a user to select ink with a lasso.</span></span>  
  
 [!code-csharp[HowToSelectInk#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToSelectInk/CSharp/InkSelector.cs#1)]
 [!code-vb[HowToSelectInk#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HowToSelectInk/VisualBasic/InkSelector.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="a2f7c-137">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a2f7c-137">See Also</span></span>  
 <xref:System.Windows.Ink.IncrementalLassoHitTester>  
 <xref:System.Windows.Ink.StrokeCollection>  
 <xref:System.Windows.Input.StylusPointCollection>  
 [<span data-ttu-id="a2f7c-138">Tworzenie formantu wprowadzania odręcznego</span><span class="sxs-lookup"><span data-stu-id="a2f7c-138">Creating an Ink Input Control</span></span>](../../../../docs/framework/wpf/advanced/creating-an-ink-input-control.md)
