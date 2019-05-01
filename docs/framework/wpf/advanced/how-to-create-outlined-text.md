---
title: 'Instrukcje: Tworzenie tekstu z konturem'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- typography [WPF], linear gradient brush
- outlined text [WPF]
- gradient brush [WPF]
- linear gradient brush [WPF]
- typography [WPF], outline effects
ms.assetid: 4aa3cf6e-1953-4f26-8230-7c1409e5f28d
ms.openlocfilehash: 237bdc097cd2a3fbfff6dd79bce401c2d091e211
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61776771"
---
# <a name="how-to-create-outlined-text"></a><span data-ttu-id="91423-102">Instrukcje: Tworzenie tekstu z konturem</span><span class="sxs-lookup"><span data-stu-id="91423-102">How to: Create Outlined Text</span></span>
<span data-ttu-id="91423-103">W większości przypadków, gdy dodajesz ornamentacji do ciągów tekstowych w swojej [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] aplikacji, w przypadku używania tekstu pod kątem zbiór znaków discrete lub symbole.</span><span class="sxs-lookup"><span data-stu-id="91423-103">In most cases, when you are adding ornamentation to text strings in your [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] application, you are using text in terms of a collection of discrete characters, or glyphs.</span></span> <span data-ttu-id="91423-104">Na przykład można utworzyć pędzel gradientów liniowych i zastosować je do <xref:System.Windows.Controls.Control.Foreground%2A> właściwość <xref:System.Windows.Controls.TextBox> obiektu.</span><span class="sxs-lookup"><span data-stu-id="91423-104">For example, you could create a linear gradient brush and apply it to the <xref:System.Windows.Controls.Control.Foreground%2A> property of a <xref:System.Windows.Controls.TextBox> object.</span></span> <span data-ttu-id="91423-105">Podczas wyświetlania lub edytowania pola tekstowego, Pędzel gradientów liniowych jest automatycznie stosowany do bieżącego zestawu znaków w ciągu tekstowym.</span><span class="sxs-lookup"><span data-stu-id="91423-105">When you display or edit the text box, the linear gradient brush is automatically applied to the current set of characters in the text string.</span></span>  
  
 ![Tekst wyświetlany za pomocą pędzel gradientów liniowych](./media/how-to-create-outlined-text/text-linear-gradient.jpg)    
  
 <span data-ttu-id="91423-107">Jednakże można także przekonwertować tekst do <xref:System.Windows.Media.Geometry> obiektów, co pozwala na tworzenie innych rodzajów wizualnie RTF.</span><span class="sxs-lookup"><span data-stu-id="91423-107">However, you can also convert text into <xref:System.Windows.Media.Geometry> objects, allowing you to create other types of visually rich text.</span></span> <span data-ttu-id="91423-108">Na przykład można utworzyć <xref:System.Windows.Media.Geometry> obiektu oparte na konspekt ciąg tekstowy.</span><span class="sxs-lookup"><span data-stu-id="91423-108">For example, you could create a <xref:System.Windows.Media.Geometry> object based on the outline of a text string.</span></span>  
  
 ![Kontur tekstu przy użyciu pędzel gradientów liniowych](./media/how-to-create-outlined-text/text-outline-linear-gradient.jpg)  
  
 <span data-ttu-id="91423-110">Jeśli tekst jest konwertowany na <xref:System.Windows.Media.Geometry> obiektu nie jest już zbioru znaków — nie można zmodyfikować znaków w ciągu tekstowym.</span><span class="sxs-lookup"><span data-stu-id="91423-110">When text is converted to a <xref:System.Windows.Media.Geometry> object, it is no longer a collection of characters—you cannot modify the characters in the text string.</span></span> <span data-ttu-id="91423-111">Jednak może wpłynąć na wygląd tekstu przekonwertowany, modyfikując jej obrysu i wypełnienie właściwości.</span><span class="sxs-lookup"><span data-stu-id="91423-111">However, you can affect the appearance of the converted text by modifying its stroke and fill properties.</span></span> <span data-ttu-id="91423-112">Stroke odwołuje się do konturu tekst skonwertowany; Wypełnienie odnosi się do obszaru w konturze tekst skonwertowany.</span><span class="sxs-lookup"><span data-stu-id="91423-112">The stroke refers to the outline of the converted text; the fill refers to the area inside the outline of the converted text.</span></span>  
  
 <span data-ttu-id="91423-113">Poniższe przykłady ilustrują kilka sposobów tworzenia efektów wizualnych, modyfikując obrysu i wypełnienia tekst skonwertowany.</span><span class="sxs-lookup"><span data-stu-id="91423-113">The following examples illustrate several ways of creating visual effects by modifying the stroke and fill of converted text.</span></span>  
  
 ![Tekst w różnych kolorach wypełnienia i pociągnięcia](./media/how-to-create-outlined-text/fill-stroke-text-effect.jpg)  
  
 ![Tekst z ImageBrush dotyczą pociągnięcia](./media/how-to-create-outlined-text/image-brush-application.jpg)
  
 <span data-ttu-id="91423-116">Istnieje również możliwość modyfikowania otaczający prostokąta pola lub wyróżnienie przekonwertowanego tekstu.</span><span class="sxs-lookup"><span data-stu-id="91423-116">It is also possible to modify the bounding box rectangle, or highlight, of the converted text.</span></span> <span data-ttu-id="91423-117">Poniższy przykład ilustruje sposób tworzenia efektów wizualnych, modyfikując obrysu i wyróżnienie tekst skonwertowany.</span><span class="sxs-lookup"><span data-stu-id="91423-117">The following example illustrates a way to creating visual effects by modifying the stroke and highlight of converted text.</span></span>  
  
 ![Tekst z ImageBrush stosowane do obrysu i wyróżnienia](./media/how-to-create-outlined-text/image-brush-text-application.jpg)

## <a name="example"></a><span data-ttu-id="91423-119">Przykład</span><span class="sxs-lookup"><span data-stu-id="91423-119">Example</span></span>  
 <span data-ttu-id="91423-120">Kluczem do konwertowania tekstu do <xref:System.Windows.Media.Geometry> obiektu jest użycie <xref:System.Windows.Media.FormattedText> obiektu.</span><span class="sxs-lookup"><span data-stu-id="91423-120">The key to converting text to a <xref:System.Windows.Media.Geometry> object is to use the <xref:System.Windows.Media.FormattedText> object.</span></span> <span data-ttu-id="91423-121">Po utworzeniu tego obiektu można użyć <xref:System.Windows.Media.FormattedText.BuildGeometry%2A> i <xref:System.Windows.Media.FormattedText.BuildHighlightGeometry%2A> metod do konwertowania tekstu na <xref:System.Windows.Media.Geometry> obiektów.</span><span class="sxs-lookup"><span data-stu-id="91423-121">Once you have created this object, you can use the <xref:System.Windows.Media.FormattedText.BuildGeometry%2A> and <xref:System.Windows.Media.FormattedText.BuildHighlightGeometry%2A> methods to convert the text to <xref:System.Windows.Media.Geometry> objects.</span></span> <span data-ttu-id="91423-122">Pierwsza metoda zwraca geometrii tekstu sformatowanego. Druga metoda zwraca obwiedni geometrii tekstu sformatowanego.</span><span class="sxs-lookup"><span data-stu-id="91423-122">The first method returns the geometry of the formatted text; the second method returns the geometry of the formatted text's bounding box.</span></span> <span data-ttu-id="91423-123">Poniższy przykład kodu pokazuje sposób tworzenia <xref:System.Windows.Media.FormattedText> obiektu i pobrać geometrii tekstu sformatowanego i jego obwiedni.</span><span class="sxs-lookup"><span data-stu-id="91423-123">The following code example shows how to create a <xref:System.Windows.Media.FormattedText> object and to retrieve the geometries of the formatted text and its bounding box.</span></span>  
  
 [!code-csharp[OutlineTextControlViewer#CreateText](~/samples/snippets/csharp/VS_Snippets_Wpf/OutlineTextControlViewer/CSharp/OutlineTextControl.cs#createtext)]
 [!code-vb[OutlineTextControlViewer#CreateText](~/samples/snippets/visualbasic/VS_Snippets_Wpf/OutlineTextControlViewer/visualbasic/outlinetextcontrol.vb#createtext)]  
  
 <span data-ttu-id="91423-124">Aby wyświetlić pobrany <xref:System.Windows.Media.Geometry> obiektów i potrzebny jest dostęp do <xref:System.Windows.Media.DrawingContext> obiektu, na którym jest wyświetlany tekst skonwertowany.</span><span class="sxs-lookup"><span data-stu-id="91423-124">In order to display the retrieved the <xref:System.Windows.Media.Geometry> objects, you need to access the <xref:System.Windows.Media.DrawingContext> of the object that is displaying the converted text.</span></span> <span data-ttu-id="91423-125">W tych przykładach kodu odbywa się przez utworzenie obiektu kontrolki niestandardowej, która jest pochodną klasę, która obsługuje renderowanie zdefiniowanych przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="91423-125">In these code examples, this is done by creating a custom control object that is derived from a class that supports user-defined rendering.</span></span>  
  
 <span data-ttu-id="91423-126">Aby wyświetlić <xref:System.Windows.Media.Geometry> obiekty w formancie niestandardowym dostarczają zastąpienie <xref:System.Windows.UIElement.OnRender%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="91423-126">To display <xref:System.Windows.Media.Geometry> objects in the custom control, provide an override for the <xref:System.Windows.UIElement.OnRender%2A> method.</span></span> <span data-ttu-id="91423-127">Metoda zgodnym z przesłoniętą należy używać <xref:System.Windows.Media.DrawingContext.DrawGeometry%2A> metodę, aby narysować <xref:System.Windows.Media.Geometry> obiektów.</span><span class="sxs-lookup"><span data-stu-id="91423-127">Your overridden method should use the <xref:System.Windows.Media.DrawingContext.DrawGeometry%2A> method to draw the <xref:System.Windows.Media.Geometry> objects.</span></span>  
  
 [!code-csharp[OutlineTextControlViewer#OnRender](~/samples/snippets/csharp/VS_Snippets_Wpf/OutlineTextControlViewer/CSharp/OutlineTextControl.cs#onrender)]
 [!code-vb[OutlineTextControlViewer#OnRender](~/samples/snippets/visualbasic/VS_Snippets_Wpf/OutlineTextControlViewer/visualbasic/outlinetextcontrol.vb#onrender)]  
  
  <span data-ttu-id="91423-128">Dla źródła obiektu przykładowego użytkownika niestandardowego formantu, zobacz [OutlineTextControl.cs dla C# ](https://github.com/dotnet/samples/blob/master/snippets/csharp/VS_Snippets_Wpf/OutlineTextControlViewer/CSharp/OutlineTextControl.cs) i [OutlineTextControl.vb dla języka Visual Basic](https://github.com/dotnet/samples/blob/master/snippets/visualbasic/VS_Snippets_Wpf/OutlineTextControlViewer/visualbasic/outlinetextcontrol.vb).</span><span class="sxs-lookup"><span data-stu-id="91423-128">For the source of the example custom user control object, see [OutlineTextControl.cs for C#](https://github.com/dotnet/samples/blob/master/snippets/csharp/VS_Snippets_Wpf/OutlineTextControlViewer/CSharp/OutlineTextControl.cs) and [OutlineTextControl.vb for Visual Basic](https://github.com/dotnet/samples/blob/master/snippets/visualbasic/VS_Snippets_Wpf/OutlineTextControlViewer/visualbasic/outlinetextcontrol.vb).</span></span> 
  
## <a name="see-also"></a><span data-ttu-id="91423-129">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="91423-129">See also</span></span>

- [<span data-ttu-id="91423-130">Rysowanie formatowanego tekstu</span><span class="sxs-lookup"><span data-stu-id="91423-130">Drawing Formatted Text</span></span>](drawing-formatted-text.md)
