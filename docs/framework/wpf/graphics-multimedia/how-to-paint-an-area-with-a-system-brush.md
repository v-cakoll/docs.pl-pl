---
title: 'Instrukcje: Maluj obszar pędzlem systemowym'
ms.date: 03/30/2017
helpviewer_keywords:
- system brushes [WPF], painting with
- painting [WPF], with system brushes
- brushes [WPF], painting with system brushes [WPF]
ms.assetid: 5141a763-9235-42cb-a6bb-afc75513eac7
ms.openlocfilehash: 6977410a596a943a23c3841e80edf4cfed1bf6b5
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54644940"
---
# <a name="how-to-paint-an-area-with-a-system-brush"></a><span data-ttu-id="1e9de-102">Instrukcje: Maluj obszar pędzlem systemowym</span><span class="sxs-lookup"><span data-stu-id="1e9de-102">How to: Paint an Area with a System Brush</span></span>
<span data-ttu-id="1e9de-103"><xref:System.Windows.SystemColors> Klasy zapewnia dostęp do pędzli systemowych i kolorów, takich jak <xref:System.Windows.SystemColors.ControlBrush%2A>, <xref:System.Windows.SystemColors.ControlBrushKey%2A>, i <xref:System.Windows.SystemColors.DesktopBrush%2A>.</span><span class="sxs-lookup"><span data-stu-id="1e9de-103">The <xref:System.Windows.SystemColors> class provides access to system brushes and colors, such as <xref:System.Windows.SystemColors.ControlBrush%2A>, <xref:System.Windows.SystemColors.ControlBrushKey%2A>, and <xref:System.Windows.SystemColors.DesktopBrush%2A>.</span></span> <span data-ttu-id="1e9de-104">Pędzel system <xref:System.Windows.Media.SolidColorBrush> obiekt, który umożliwia malowanie obszaru za pomocą kolorów określonego systemu.</span><span class="sxs-lookup"><span data-stu-id="1e9de-104">A system brush is a <xref:System.Windows.Media.SolidColorBrush> object that paints an area with the specified system color.</span></span> <span data-ttu-id="1e9de-105">Pędzel systemu zawsze daje wypełnienia kryjącego; Nie można utworzyć gradientu.</span><span class="sxs-lookup"><span data-stu-id="1e9de-105">A system brush always produces a solid fill; it can't be used to create a gradient.</span></span>  
  
 <span data-ttu-id="1e9de-106">Pędzle systemowe służy jako statyczna lub dynamiczna zasobów.</span><span class="sxs-lookup"><span data-stu-id="1e9de-106">You can use system brushes as either a static or a dynamic resource.</span></span> <span data-ttu-id="1e9de-107">Użyj dynamicznych zasobów, jeśli chcesz, aby pędzla do automatycznej aktualizacji, jeśli użytkownik zmieni pędzla systemu, ponieważ aplikacja jest uruchomiona; w przeciwnym razie użyj zasób statyczny.</span><span class="sxs-lookup"><span data-stu-id="1e9de-107">Use a dynamic resource if you want the brush to update automatically if the user changes the system brush as the application is running; otherwise, use a static resource.</span></span> <span data-ttu-id="1e9de-108">Klasa SystemColors zawiera szereg statycznej właściwości, które postępuj zgodnie z ograniczeniami konwencji nazewnictwa:</span><span class="sxs-lookup"><span data-stu-id="1e9de-108">The SystemColors class contains a variety of static properties that follow a strict naming convention:</span></span>  
  
-   <span data-ttu-id="1e9de-109">*\<SystemColor>* Brush</span><span class="sxs-lookup"><span data-stu-id="1e9de-109">*\<SystemColor>* Brush</span></span>  
  
     <span data-ttu-id="1e9de-110">Pobiera odwołanie statyczne do <xref:System.Windows.Media.SolidColorBrush> koloru określonego systemu.</span><span class="sxs-lookup"><span data-stu-id="1e9de-110">Gets a static reference to a <xref:System.Windows.Media.SolidColorBrush> of the specified system color.</span></span>  
  
-   <span data-ttu-id="1e9de-111">*\<SystemColor>* BrushKey</span><span class="sxs-lookup"><span data-stu-id="1e9de-111">*\<SystemColor>* BrushKey</span></span>  
  
     <span data-ttu-id="1e9de-112">Pobiera dynamiczny odwołanie do <xref:System.Windows.Media.SolidColorBrush> koloru określonego systemu.</span><span class="sxs-lookup"><span data-stu-id="1e9de-112">Gets a dynamic reference to a <xref:System.Windows.Media.SolidColorBrush> of the specified system color.</span></span>  
  
-   <span data-ttu-id="1e9de-113">*\<SystemColor>* Color</span><span class="sxs-lookup"><span data-stu-id="1e9de-113">*\<SystemColor>* Color</span></span>  
  
     <span data-ttu-id="1e9de-114">Pobiera odwołanie statyczne do <xref:System.Windows.Media.Color> struktury kolorów określonego systemu.</span><span class="sxs-lookup"><span data-stu-id="1e9de-114">Gets a static reference to a <xref:System.Windows.Media.Color> structure of the specified system color.</span></span>  
  
-   <span data-ttu-id="1e9de-115">*\<SystemColor>* ColorKey</span><span class="sxs-lookup"><span data-stu-id="1e9de-115">*\<SystemColor>* ColorKey</span></span>  
  
     <span data-ttu-id="1e9de-116">Pobiera dynamiczny odwołanie do <xref:System.Windows.Media.Color> struktury kolorów określonego systemu.</span><span class="sxs-lookup"><span data-stu-id="1e9de-116">Gets a dynamic reference to the <xref:System.Windows.Media.Color> structure of the specified system color.</span></span>  
  
 <span data-ttu-id="1e9de-117">Kolor systemu jest <xref:System.Windows.Media.Color> strukturę, która może służyć do konfigurowania pędzla.</span><span class="sxs-lookup"><span data-stu-id="1e9de-117">A system color is a <xref:System.Windows.Media.Color> structure that can be used to configure a brush.</span></span> <span data-ttu-id="1e9de-118">Na przykład można utworzyć przy użyciu kolorów systemowych, ustawiając gradientu <xref:System.Windows.Media.GradientStop.Color%2A> właściwości <xref:System.Windows.Media.LinearGradientBrush> ograniczniki gradientu obiektu za pomocą kolorów systemowych.</span><span class="sxs-lookup"><span data-stu-id="1e9de-118">For example, you can create a gradient using system colors by setting the <xref:System.Windows.Media.GradientStop.Color%2A> properties of a <xref:System.Windows.Media.LinearGradientBrush> object's gradient stops with system colors.</span></span> <span data-ttu-id="1e9de-119">Aby uzyskać przykład, zobacz [Użyj kolorów systemowych w gradiencie](../../../../docs/framework/wpf/graphics-multimedia/how-to-use-system-colors-in-a-gradient.md).</span><span class="sxs-lookup"><span data-stu-id="1e9de-119">For an example, see [Use System Colors in a Gradient](../../../../docs/framework/wpf/graphics-multimedia/how-to-use-system-colors-in-a-gradient.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="1e9de-120">Przykład</span><span class="sxs-lookup"><span data-stu-id="1e9de-120">Example</span></span>  
 <span data-ttu-id="1e9de-121">W poniższym przykładzie użyto dynamicznego systemu odwołanie pędzla do Ustawianie tła przycisku.</span><span class="sxs-lookup"><span data-stu-id="1e9de-121">The following example uses a dynamic system brush reference to set the Background of a button.</span></span>  
  
 [!code-xaml[brushsamples_snip#GraphicsMMDynamicSystemColorDesktopBrushKeyExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/DynamicSystemBrushExample.xaml#graphicsmmdynamicsystemcolordesktopbrushkeyexamplewholepage)]  
  
 <span data-ttu-id="1e9de-122">W następnym przykładzie użyto systemu statycznego odwołanie pędzla do Ustawianie tła przycisku.</span><span class="sxs-lookup"><span data-stu-id="1e9de-122">The next example uses a static system brush reference to set the Background of a button.</span></span>  
  
 [!code-xaml[brushsamples_snip#GraphicsMMStaticSystemColorDesktopBrushExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/StaticSystemBrushExample.xaml#graphicsmmstaticsystemcolordesktopbrushexamplewholepage)]  
  
 <span data-ttu-id="1e9de-123">Na przykład przedstawiający sposób użycia kolorów systemowych w gradiencie zobacz [Użyj kolorów systemowych w gradiencie](../../../../docs/framework/wpf/graphics-multimedia/how-to-use-system-colors-in-a-gradient.md).</span><span class="sxs-lookup"><span data-stu-id="1e9de-123">For an example showing how to use a system color in a gradient, see [Use System Colors in a Gradient](../../../../docs/framework/wpf/graphics-multimedia/how-to-use-system-colors-in-a-gradient.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1e9de-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1e9de-124">See also</span></span>
- [<span data-ttu-id="1e9de-125">Używanie kolorów systemowych w gradiencie</span><span class="sxs-lookup"><span data-stu-id="1e9de-125">Use System Colors in a Gradient</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-use-system-colors-in-a-gradient.md)
- [<span data-ttu-id="1e9de-126">Malowanie jednolitymi kolorami i gradientami — przegląd</span><span class="sxs-lookup"><span data-stu-id="1e9de-126">Painting with Solid Colors and Gradients Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md)
