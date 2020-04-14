---
title: Jak utworzyć schemat tekstu
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
ms.openlocfilehash: 86bfa396a2aa44eb511c014687501d60e170a396
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81278928"
---
# <a name="how-to-create-outlined-text"></a><span data-ttu-id="3f300-102">Jak: Tworzenie tekstu konspektów</span><span class="sxs-lookup"><span data-stu-id="3f300-102">How to: Create outlined text</span></span>

<span data-ttu-id="3f300-103">W większości przypadków podczas dodawania ornamentacji do ciągów tekstowych w [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] aplikacji, używasz tekstu pod względem kolekcji znaków dyskretnych lub glifów.</span><span class="sxs-lookup"><span data-stu-id="3f300-103">In most cases, when you're adding ornamentation to text strings in your [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] application, you are using text in terms of a collection of discrete characters, or glyphs.</span></span> <span data-ttu-id="3f300-104">Na przykład można utworzyć pędzel gradientu liniowego <xref:System.Windows.Controls.Control.Foreground%2A> i <xref:System.Windows.Controls.TextBox> zastosować go do właściwości obiektu.</span><span class="sxs-lookup"><span data-stu-id="3f300-104">For example, you could create a linear gradient brush and apply it to the <xref:System.Windows.Controls.Control.Foreground%2A> property of a <xref:System.Windows.Controls.TextBox> object.</span></span> <span data-ttu-id="3f300-105">Podczas wyświetlania lub edytowania pola tekstowego liniowy pędzel gradientowy jest automatycznie stosowany do bieżącego zestawu znaków w ciągu tekstowym.</span><span class="sxs-lookup"><span data-stu-id="3f300-105">When you display or edit the text box, the linear gradient brush is automatically applied to the current set of characters in the text string.</span></span>  
  
 ![Tekst wyświetlany za pomocą liniowego pędzla gradientowego](./media/how-to-create-outlined-text/text-linear-gradient.jpg)
  
 <span data-ttu-id="3f300-107">Można jednak również konwertować tekst na <xref:System.Windows.Media.Geometry> obiekty, co pozwala na tworzenie innych typów wizualnie tekstu sformatowany.</span><span class="sxs-lookup"><span data-stu-id="3f300-107">However, you can also convert text into <xref:System.Windows.Media.Geometry> objects, allowing you to create other types of visually rich text.</span></span> <span data-ttu-id="3f300-108">Na przykład można utworzyć <xref:System.Windows.Media.Geometry> obiekt na podstawie konturu ciągu tekstowego.</span><span class="sxs-lookup"><span data-stu-id="3f300-108">For example, you could create a <xref:System.Windows.Media.Geometry> object based on the outline of a text string.</span></span>  
  
 ![Kontur tekstu przy użyciu pędzla gradientu liniowego](./media/how-to-create-outlined-text/text-outline-linear-gradient.jpg)  
  
 <span data-ttu-id="3f300-110">Gdy tekst jest konwertowany na <xref:System.Windows.Media.Geometry> obiekt, nie jest już kolekcją znaków — nie można modyfikować znaków w ciągu tekstowym.</span><span class="sxs-lookup"><span data-stu-id="3f300-110">When text is converted to a <xref:System.Windows.Media.Geometry> object, it is no longer a collection of characters—you cannot modify the characters in the text string.</span></span> <span data-ttu-id="3f300-111">Można jednak wpłynąć na wygląd przekonwertowanego tekstu, modyfikując jego właściwości obrysu i wypełnienia.</span><span class="sxs-lookup"><span data-stu-id="3f300-111">However, you can affect the appearance of the converted text by modifying its stroke and fill properties.</span></span> <span data-ttu-id="3f300-112">Obrys odnosi się do konturu przekonwertowanego tekstu; wypełnienie odnosi się do obszaru wewnątrz konturu przekonwertowanego tekstu.</span><span class="sxs-lookup"><span data-stu-id="3f300-112">The stroke refers to the outline of the converted text; the fill refers to the area inside the outline of the converted text.</span></span>  
  
 <span data-ttu-id="3f300-113">Poniższe przykłady ilustrują kilka sposobów tworzenia efektów wizualnych przez modyfikowanie obrysu i wypełnienia przekonwertowanego tekstu.</span><span class="sxs-lookup"><span data-stu-id="3f300-113">The following examples illustrate several ways of creating visual effects by modifying the stroke and fill of converted text.</span></span>  
  
 ![Tekst o różnych kolorach wypełnienia i obrysu](./media/how-to-create-outlined-text/fill-stroke-text-effect.jpg)  
  
 ![Tekst z pędzlem obrazu zastosowanym do obrysu](./media/how-to-create-outlined-text/image-brush-application.jpg)
  
 <span data-ttu-id="3f300-116">Możliwe jest również zmodyfikowanie prostokąta obwiedni lub podświetlenia przekonwertowanego tekstu.</span><span class="sxs-lookup"><span data-stu-id="3f300-116">It is also possible to modify the bounding box rectangle, or highlight, of the converted text.</span></span> <span data-ttu-id="3f300-117">Poniższy przykład ilustruje sposób tworzenia efektów wizualnych przez modyfikowanie obrysu i wyróżnienia przekonwertowanego tekstu.</span><span class="sxs-lookup"><span data-stu-id="3f300-117">The following example illustrates a way to create visual effects by modifying the stroke and highlight of converted text.</span></span>  
  
 ![Tekst z pędzlem obrazu zastosowanym do obrysu i podświetlenia](./media/how-to-create-outlined-text/image-brush-text-application.jpg)

## <a name="example"></a><span data-ttu-id="3f300-119">Przykład</span><span class="sxs-lookup"><span data-stu-id="3f300-119">Example</span></span>  
 <span data-ttu-id="3f300-120">Kluczem do konwersji <xref:System.Windows.Media.Geometry> tekstu do obiektu <xref:System.Windows.Media.FormattedText> jest użycie obiektu.</span><span class="sxs-lookup"><span data-stu-id="3f300-120">The key to converting text to a <xref:System.Windows.Media.Geometry> object is to use the <xref:System.Windows.Media.FormattedText> object.</span></span> <span data-ttu-id="3f300-121">Po utworzeniu tego obiektu można <xref:System.Windows.Media.FormattedText.BuildGeometry%2A> użyć <xref:System.Windows.Media.FormattedText.BuildHighlightGeometry%2A> metody i metody, aby przekonwertować tekst na <xref:System.Windows.Media.Geometry> obiekty.</span><span class="sxs-lookup"><span data-stu-id="3f300-121">Once you have created this object, you can use the <xref:System.Windows.Media.FormattedText.BuildGeometry%2A> and <xref:System.Windows.Media.FormattedText.BuildHighlightGeometry%2A> methods to convert the text to <xref:System.Windows.Media.Geometry> objects.</span></span> <span data-ttu-id="3f300-122">Pierwsza metoda zwraca geometrię sformatowanego tekstu; druga metoda zwraca geometrię obwiedni sformatowanego tekstu.</span><span class="sxs-lookup"><span data-stu-id="3f300-122">The first method returns the geometry of the formatted text; the second method returns the geometry of the formatted text's bounding box.</span></span> <span data-ttu-id="3f300-123">Poniższy przykład kodu pokazuje, <xref:System.Windows.Media.FormattedText> jak utworzyć obiekt i pobrać geometrie sformatowanego tekstu i jego obwiedni.</span><span class="sxs-lookup"><span data-stu-id="3f300-123">The following code example shows how to create a <xref:System.Windows.Media.FormattedText> object and to retrieve the geometries of the formatted text and its bounding box.</span></span>  
  
 [!code-csharp[OutlineTextControlViewer#CreateText](~/samples/snippets/csharp/VS_Snippets_Wpf/OutlineTextControlViewer/CSharp/OutlineTextControl.cs#createtext)]
 [!code-vb[OutlineTextControlViewer#CreateText](~/samples/snippets/visualbasic/VS_Snippets_Wpf/OutlineTextControlViewer/visualbasic/outlinetextcontrol.vb#createtext)]  
  
 <span data-ttu-id="3f300-124">Aby wyświetlić pobrane <xref:System.Windows.Media.Geometry> obiekty, należy uzyskać <xref:System.Windows.Media.DrawingContext> dostęp do obiektu, który wyświetla przekonwertowany tekst.</span><span class="sxs-lookup"><span data-stu-id="3f300-124">In order to display the retrieved the <xref:System.Windows.Media.Geometry> objects, you need to access the <xref:System.Windows.Media.DrawingContext> of the object that's displaying the converted text.</span></span> <span data-ttu-id="3f300-125">W tych przykładach kodu ten dostęp uzyskuje się przez utworzenie niestandardowego obiektu kontrolnego, który jest pochodną klasy, która obsługuje renderowanie zdefiniowane przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="3f300-125">In these code examples, this access is achieved by creating a custom control object that's derived from a class that supports user-defined rendering.</span></span>  
  
 <span data-ttu-id="3f300-126">Aby <xref:System.Windows.Media.Geometry> wyświetlić obiekty w formancie niestandardowym, podaj zastąpienie <xref:System.Windows.UIElement.OnRender%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="3f300-126">To display <xref:System.Windows.Media.Geometry> objects in the custom control, provide an override for the <xref:System.Windows.UIElement.OnRender%2A> method.</span></span> <span data-ttu-id="3f300-127">Nadpisana metoda powinna <xref:System.Windows.Media.DrawingContext.DrawGeometry%2A> używać metody <xref:System.Windows.Media.Geometry> do rysowania obiektów.</span><span class="sxs-lookup"><span data-stu-id="3f300-127">Your overridden method should use the <xref:System.Windows.Media.DrawingContext.DrawGeometry%2A> method to draw the <xref:System.Windows.Media.Geometry> objects.</span></span>  
  
 [!code-csharp[OutlineTextControlViewer#OnRender](~/samples/snippets/csharp/VS_Snippets_Wpf/OutlineTextControlViewer/CSharp/OutlineTextControl.cs#onrender)]
 [!code-vb[OutlineTextControlViewer#OnRender](~/samples/snippets/visualbasic/VS_Snippets_Wpf/OutlineTextControlViewer/visualbasic/outlinetextcontrol.vb#onrender)]  
  
  <span data-ttu-id="3f300-128">Źródło przykładowego obiektu sterującego użytkownika niestandardowego można znaleźć [w OutlineTextControl.cs dla języka C#](https://github.com/dotnet/docs/tree/master/samples/snippets/csharp/VS_Snippets_Wpf/OutlineTextControlViewer/CSharp/OutlineTextControl.cs) i [OutlineTextControl.vb dla języka Visual Basic](https://github.com/dotnet/docs/blob/master/samples/snippets/visualbasic/VS_Snippets_Wpf/OutlineTextControlViewer/visualbasic/outlinetextcontrol.vb).</span><span class="sxs-lookup"><span data-stu-id="3f300-128">For the source of the example custom user control object, see [OutlineTextControl.cs for C#](https://github.com/dotnet/docs/tree/master/samples/snippets/csharp/VS_Snippets_Wpf/OutlineTextControlViewer/CSharp/OutlineTextControl.cs) and [OutlineTextControl.vb for Visual Basic](https://github.com/dotnet/docs/blob/master/samples/snippets/visualbasic/VS_Snippets_Wpf/OutlineTextControlViewer/visualbasic/outlinetextcontrol.vb).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="3f300-129">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3f300-129">See also</span></span>

- [<span data-ttu-id="3f300-130">Rysowanie formatowanego tekstu</span><span class="sxs-lookup"><span data-stu-id="3f300-130">Drawing Formatted Text</span></span>](drawing-formatted-text.md)
