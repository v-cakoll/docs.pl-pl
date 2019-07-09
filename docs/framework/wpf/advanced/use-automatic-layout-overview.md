---
title: Przegląd Użyj automatycznego układu
ms.date: 03/30/2017
helpviewer_keywords:
- layout [WPF], automatic
- automatic layout [WPF]
ms.assetid: 6fed9264-18bb-4d05-8867-1fe356c6f687
ms.openlocfilehash: d4a0fd819d08fdd936dd1ef35e8cd8c00947f9e0
ms.sourcegitcommit: d6e27023aeaffc4b5a3cb4b88685018d6284ada4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/09/2019
ms.locfileid: "67662684"
---
# <a name="use-automatic-layout-overview"></a><span data-ttu-id="77e98-102">Przegląd Użyj automatycznego układu</span><span class="sxs-lookup"><span data-stu-id="77e98-102">Use Automatic Layout Overview</span></span>

<span data-ttu-id="77e98-103">W tym temacie przedstawiono wskazówki dla deweloperów dotyczące programowania [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] aplikacji przy użyciu możliwych do zlokalizowania [!INCLUDE[TLA#tla_ui#plural](../../../../includes/tlasharptla-uisharpplural-md.md)].</span><span class="sxs-lookup"><span data-stu-id="77e98-103">This topic introduces guidelines for developers on how to write [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] applications with localizable [!INCLUDE[TLA#tla_ui#plural](../../../../includes/tlasharptla-uisharpplural-md.md)].</span></span> <span data-ttu-id="77e98-104">W przeszłości lokalizacja interfejs użytkownika był czasochłonny proces.</span><span class="sxs-lookup"><span data-stu-id="77e98-104">In the past, localization of a UI was a time consuming process.</span></span> <span data-ttu-id="77e98-105">Każdego z języków interfejsu użytkownika została dostosowana do wymagana korekta poszczególne piksele.</span><span class="sxs-lookup"><span data-stu-id="77e98-105">Each language that the UI was adapted for required a pixel by pixel adjustment.</span></span> <span data-ttu-id="77e98-106">Dzisiaj z właściwy projekt i po prawej stronie standardy, kodowania [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)] można skonstruować tak, aby lokalizatorzy mają mniejsza Zmienianie rozmiaru i położenia celu.</span><span class="sxs-lookup"><span data-stu-id="77e98-106">Today with the right design and right coding standards, [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)] can be constructed so that localizers have less resizing and repositioning to do.</span></span> <span data-ttu-id="77e98-107">Podejścia do pisania aplikacji, które można łatwiej o zmienionym rozmiarze i zmienionym nosi nazwę automatycznego układu oraz można osiągnąć za pomocą [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] projektowania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="77e98-107">The approach to writing applications that can be more easily resized and repositioned is called automatic layout, and can be achieved by using [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application design.</span></span>

<a name="advantages_of_autolayout"></a>

## <a name="advantages-of-using-automatic-layout"></a><span data-ttu-id="77e98-108">Korzyści wynikające z używania automatycznego układu</span><span class="sxs-lookup"><span data-stu-id="77e98-108">Advantages of Using Automatic Layout</span></span>

<span data-ttu-id="77e98-109">Ponieważ [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] system prezentacji jest wydajny i elastyczny, daje możliwość elementów układu w aplikacji, którą można dostosować zgodnie z wymaganiami w różnych językach.</span><span class="sxs-lookup"><span data-stu-id="77e98-109">Because the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] presentation system is powerful and flexible, it provides the ability to layout elements in an application that can be adjusted to fit the requirements of different languages.</span></span> <span data-ttu-id="77e98-110">Poniższa lista wskazuje niektóre korzyści wynikające z układem automatycznym.</span><span class="sxs-lookup"><span data-stu-id="77e98-110">The following list points out some of the advantages of automatic layout.</span></span>

- <span data-ttu-id="77e98-111">Interfejs użytkownika wyświetla się także w dowolnym języku.</span><span class="sxs-lookup"><span data-stu-id="77e98-111">UI displays well  in any language.</span></span>

- <span data-ttu-id="77e98-112">Ogranicza potrzebę ponownie dopasować położenie i rozmiar kontrolki po jest przetłumaczony tekst.</span><span class="sxs-lookup"><span data-stu-id="77e98-112">Reduces the need to readjust position and size of controls after text is translated.</span></span>

- <span data-ttu-id="77e98-113">Ogranicza potrzebę Dopasuj rozmiar okna.</span><span class="sxs-lookup"><span data-stu-id="77e98-113">Reduces the need to readjust window size.</span></span>

- <span data-ttu-id="77e98-114">Układ interfejsu użytkownika poprawnie renderowany w dowolnym języku.</span><span class="sxs-lookup"><span data-stu-id="77e98-114">UI layout renders properly in any language.</span></span>

- <span data-ttu-id="77e98-115">Lokalizacja można zmniejszyć do punktu, jest on nieco więcej niż ciąg tłumaczenia.</span><span class="sxs-lookup"><span data-stu-id="77e98-115">Localization can be reduced to the point that it is little more than string translation.</span></span>

<a name="autolayout_controls"></a>

## <a name="automatic-layout-and-controls"></a><span data-ttu-id="77e98-116">Automatyczny układ i kontrolek</span><span class="sxs-lookup"><span data-stu-id="77e98-116">Automatic Layout and Controls</span></span>

<span data-ttu-id="77e98-117">Układ automatyczny umożliwia aplikacji automatyczne dopasowanie rozmiaru formantu.</span><span class="sxs-lookup"><span data-stu-id="77e98-117">Automatic layout enables an application to adjust the size of a control automatically.</span></span> <span data-ttu-id="77e98-118">Na przykład kontrolki można zmienić celu uwzględnienia długość ciągu.</span><span class="sxs-lookup"><span data-stu-id="77e98-118">For example, a control can change to accommodate the length of a string.</span></span> <span data-ttu-id="77e98-119">Ta funkcja umożliwia lokalizatorzy do tłumaczenia ciągów; muszą już nie zmienia rozmiar formantu w celu dopasowania do przetłumaczonego tekstu.</span><span class="sxs-lookup"><span data-stu-id="77e98-119">This capability enables  localizers to translate the string; they no longer need to resize the control to fit the translated text.</span></span> <span data-ttu-id="77e98-120">Poniższy przykład tworzy przycisk z zawartości w języku angielskim.</span><span class="sxs-lookup"><span data-stu-id="77e98-120">The following example creates a button with English content.</span></span>

[!code-xaml[LocalizationBtn_snip#1](~/samples/snippets/csharp/VS_Snippets_Wpf/LocalizationBtn_snip/CS/Pane1.xaml#1)]

<span data-ttu-id="77e98-121">W tym przykładzie jest wszystko, co trzeba zrobić, aby przycisk hiszpańskim, zmienianie tekstu.</span><span class="sxs-lookup"><span data-stu-id="77e98-121">In the example, all you have to do to make a Spanish button is change the text.</span></span> <span data-ttu-id="77e98-122">Na przykład</span><span class="sxs-lookup"><span data-stu-id="77e98-122">For example,</span></span>

[!code-xaml[LocalizationBtn#1](~/samples/snippets/csharp/VS_Snippets_Wpf/LocalizationBtn/CS/Pane1.xaml#1)]

<span data-ttu-id="77e98-123">Na poniższym rysunku przedstawiono dane wyjściowe przykłady kodu:</span><span class="sxs-lookup"><span data-stu-id="77e98-123">The following graphic shows the output of the code samples:</span></span>

![Ten sam przycisk z tekstem w różnych językach](./media/use-automatic-layout-overview/auto-resizable-button.png)

<a name="autolayout_coding"></a>

## <a name="automatic-layout-and-coding-standards"></a><span data-ttu-id="77e98-125">Automatyczny układ i standardy kodowania</span><span class="sxs-lookup"><span data-stu-id="77e98-125">Automatic Layout and Coding Standards</span></span>

<span data-ttu-id="77e98-126">Przy użyciu metody automatycznego układu wymaga zestawu kodowania i projektowania standardów i zasad do produkcji w pełni Lokalizowalny interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="77e98-126">Using the automatic layout approach requires a set of coding and design standards and rules to produce a fully localizable UI.</span></span> <span data-ttu-id="77e98-127">Poniższe wskazówki będą pomocy kodowania automatycznego układu.</span><span class="sxs-lookup"><span data-stu-id="77e98-127">The following guidelines will aid your automatic layout coding.</span></span>

<span data-ttu-id="77e98-128">**Nie używaj położenia bezwzględne**</span><span class="sxs-lookup"><span data-stu-id="77e98-128">**Do not use absolute positions**</span></span>

- <span data-ttu-id="77e98-129">Nie używaj <xref:System.Windows.Controls.Canvas> ponieważ umieszcza elementy absolutnie.</span><span class="sxs-lookup"><span data-stu-id="77e98-129">Do not use <xref:System.Windows.Controls.Canvas> because it positions elements absolutely.</span></span>

- <span data-ttu-id="77e98-130">Użyj <xref:System.Windows.Controls.DockPanel>, <xref:System.Windows.Controls.StackPanel>, i <xref:System.Windows.Controls.Grid> położenie kontrolki.</span><span class="sxs-lookup"><span data-stu-id="77e98-130">Use <xref:System.Windows.Controls.DockPanel>, <xref:System.Windows.Controls.StackPanel>, and <xref:System.Windows.Controls.Grid> to position controls.</span></span>

<span data-ttu-id="77e98-131">Aby uzyskać informacje o różnych typach paneli, zobacz [Przegląd panele](../controls/panels-overview.md).</span><span class="sxs-lookup"><span data-stu-id="77e98-131">For a discussion about various types of panels, see [Panels Overview](../controls/panels-overview.md).</span></span>

<span data-ttu-id="77e98-132">**Nie należy ustawiać o stałym rozmiarze okna**</span><span class="sxs-lookup"><span data-stu-id="77e98-132">**Do not set a fixed size for a window**</span></span>

- <span data-ttu-id="77e98-133">Użyj <xref:System.Windows.Window.SizeToContent%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="77e98-133">Use <xref:System.Windows.Window.SizeToContent%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="77e98-134">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="77e98-134">For example:</span></span>

  [!code-xaml[LocalizationGrid#2](~/samples/snippets/csharp/VS_Snippets_Wpf/LocalizationGrid/CS/Pane1.xaml#2)]

<span data-ttu-id="77e98-135">**Dodaj <xref:System.Windows.FrameworkElement.FlowDirection%2A>**</span><span class="sxs-lookup"><span data-stu-id="77e98-135">**Add a <xref:System.Windows.FrameworkElement.FlowDirection%2A>**</span></span>

- <span data-ttu-id="77e98-136">Dodaj <xref:System.Windows.FrameworkElement.FlowDirection%2A> do elementu głównego aplikacji.</span><span class="sxs-lookup"><span data-stu-id="77e98-136">Add a <xref:System.Windows.FrameworkElement.FlowDirection%2A> to the root element of your application.</span></span>

  <span data-ttu-id="77e98-137">WPF zapewnia wygodny sposób obsługi poziomej, dwukierunkowe i układów w pionie.</span><span class="sxs-lookup"><span data-stu-id="77e98-137">WPF provides a convenient way to support horizontal, bidirectional, and vertical layouts.</span></span> <span data-ttu-id="77e98-138">W ramach prezentacji <xref:System.Windows.FrameworkElement.FlowDirection%2A> właściwość może służyć do definiowania układu.</span><span class="sxs-lookup"><span data-stu-id="77e98-138">In presentation framework, the <xref:System.Windows.FrameworkElement.FlowDirection%2A> property can be used to define layout.</span></span> <span data-ttu-id="77e98-139">Wzorce kierunek przepływu są:</span><span class="sxs-lookup"><span data-stu-id="77e98-139">The flow-direction patterns are:</span></span>

  - <span data-ttu-id="77e98-140"><xref:System.Windows.FlowDirection.LeftToRight?displayProperty=nameWithType> (LrTb) — układ poziomy łaciński, Azja Wschodnia i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="77e98-140"><xref:System.Windows.FlowDirection.LeftToRight?displayProperty=nameWithType> (LrTb) — horizontal layout for Latin, East Asian, and so forth.</span></span>

  - <span data-ttu-id="77e98-141"><xref:System.Windows.FlowDirection.RightToLeft?displayProperty=nameWithType> (RlTb) — dwukierunkowych dla arabskiego, hebrajskiego i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="77e98-141"><xref:System.Windows.FlowDirection.RightToLeft?displayProperty=nameWithType> (RlTb) — bidirectional for Arabic, Hebrew, and so forth.</span></span>

<span data-ttu-id="77e98-142">**Użyj czcionki zamiast fizycznych czcionek**</span><span class="sxs-lookup"><span data-stu-id="77e98-142">**Use composite fonts instead of physical fonts**</span></span>

- <span data-ttu-id="77e98-143">W przypadku złożonych czcionek <xref:System.Windows.Controls.Control.FontFamily%2A> właściwości nie musi być lokalizowany.</span><span class="sxs-lookup"><span data-stu-id="77e98-143">With composite fonts, the <xref:System.Windows.Controls.Control.FontFamily%2A> property does not need to be localized.</span></span>

- <span data-ttu-id="77e98-144">Deweloperzy można użyć jednej z następujących czcionek lub utworzyć własne.</span><span class="sxs-lookup"><span data-stu-id="77e98-144">Developers can use one of the following fonts or create their own.</span></span>

  - <span data-ttu-id="77e98-145">Globalny interfejs użytkownika</span><span class="sxs-lookup"><span data-stu-id="77e98-145">Global User Interface</span></span>
  - <span data-ttu-id="77e98-146">Serif globalne sieci San</span><span class="sxs-lookup"><span data-stu-id="77e98-146">Global San Serif</span></span>
  - <span data-ttu-id="77e98-147">Globalne Serif</span><span class="sxs-lookup"><span data-stu-id="77e98-147">Global Serif</span></span>

<span data-ttu-id="77e98-148">**Dodaj XML: lang**</span><span class="sxs-lookup"><span data-stu-id="77e98-148">**Add xml:lang**</span></span>

- <span data-ttu-id="77e98-149">Dodaj `xml:lang` atrybutu w elemencie głównym interfejsu użytkownika, takie jak `xml:lang="en-US"` dla aplikacji w języku angielskim.</span><span class="sxs-lookup"><span data-stu-id="77e98-149">Add the `xml:lang` attribute in the root element of your UI, such as `xml:lang="en-US"` for an English application.</span></span>

- <span data-ttu-id="77e98-150">Ponieważ używają czcionki `xml:lang` Aby ustalić, jakie czcionki do użycia, należy ustawić tę właściwość, do obsługi wielu języków scenariuszy.</span><span class="sxs-lookup"><span data-stu-id="77e98-150">Because composite fonts use `xml:lang` to determine what font to use, set this property to support multilingual scenarios.</span></span>

<a name="autolay_grids"></a>

## <a name="automatic-layout-and-grids"></a><span data-ttu-id="77e98-151">Automatyczny układ i siatki</span><span class="sxs-lookup"><span data-stu-id="77e98-151">Automatic Layout and Grids</span></span>

<span data-ttu-id="77e98-152"><xref:System.Windows.Controls.Grid> Elementu, jest przydatne w przypadku automatycznego układu, ponieważ umożliwia deweloperom położenie elementów.</span><span class="sxs-lookup"><span data-stu-id="77e98-152">The <xref:System.Windows.Controls.Grid> element, is useful for automatic layout because it enables a developer to position elements.</span></span> <span data-ttu-id="77e98-153">A <xref:System.Windows.Controls.Grid> kontrolka jest w stanie dystrybucji dostępna ilość miejsca między jego elementów podrzędnych, za pomocą w układzie wierszy i kolumn.</span><span class="sxs-lookup"><span data-stu-id="77e98-153">A <xref:System.Windows.Controls.Grid> control is capable of distributing the available space among its child elements, using a column and row arrangement.</span></span> <span data-ttu-id="77e98-154">Elementy interfejsu użytkownika może obejmować wiele komórek. Ponadto istnieje możliwość mają siatki w obrębie siatki.</span><span class="sxs-lookup"><span data-stu-id="77e98-154">The UI elements can span multiple cells, and it is possible to have grids within grids.</span></span> <span data-ttu-id="77e98-155">Siatki są przydatne, ponieważ umożliwiają one tworzenie i umieść złożonego interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="77e98-155">Grids are useful because they enable you to create and position complex UI.</span></span> <span data-ttu-id="77e98-156">Poniższy przykład demonstruje użycie siatki do pozycji niektóre przyciski i tekst.</span><span class="sxs-lookup"><span data-stu-id="77e98-156">The following example demonstrates using a grid to position some buttons and text.</span></span> <span data-ttu-id="77e98-157">Należy zauważyć, że wysokość i szerokość komórek są ustawione na <xref:System.Windows.GridUnitType.Auto>; dlatego komórkę, która zawiera przycisk za pomocą obrazu jest dopasowywany obrazu.</span><span class="sxs-lookup"><span data-stu-id="77e98-157">Notice that the height and width of the cells are set to <xref:System.Windows.GridUnitType.Auto>; therefore, the cell that contains the button with an image adjusts to fit the image.</span></span>

[!code-xaml[LocalizationGrid#1](~/samples/snippets/csharp/VS_Snippets_Wpf/LocalizationGrid/CS/Pane1.xaml#1)]

<span data-ttu-id="77e98-158">Na poniższym rysunku przedstawiono siatki produkowane przez poprzedniego kodu.</span><span class="sxs-lookup"><span data-stu-id="77e98-158">The following graphic shows the grid produced by the previous code.</span></span>

<span data-ttu-id="77e98-159">![Przykład Grid](./media/glob-grid.png "glob_grid") siatki</span><span class="sxs-lookup"><span data-stu-id="77e98-159">![Grid example](./media/glob-grid.png "glob_grid") Grid</span></span>

<a name="autolay_grids_issharedsizescope"></a>

## <a name="automatic-layout-and-grids-using-the-issharedsizescope-property"></a><span data-ttu-id="77e98-160">Automatyczny układ i siatki, przy użyciu właściwości IsSharedSizeScope</span><span class="sxs-lookup"><span data-stu-id="77e98-160">Automatic Layout and Grids Using the IsSharedSizeScope Property</span></span>

<span data-ttu-id="77e98-161">A <xref:System.Windows.Controls.Grid> element jest przydatne w zlokalizowanych aplikacjach w celu tworzenia formantów, które Dopasuj do zawartości.</span><span class="sxs-lookup"><span data-stu-id="77e98-161">A <xref:System.Windows.Controls.Grid> element is useful in localizable applications to create controls that adjust to fit content.</span></span> <span data-ttu-id="77e98-162">Jednak czasami chcesz służy do obsługi określonego rozmiaru, niezależnie od zawartości.</span><span class="sxs-lookup"><span data-stu-id="77e98-162">However, at times you want controls to maintain a particular size regardless of content.</span></span> <span data-ttu-id="77e98-163">Na przykład jeśli masz "OK", "Anuluj" i "Przeglądaj" przyciski, prawdopodobnie nie ma przyciski dopasowana zawartości.</span><span class="sxs-lookup"><span data-stu-id="77e98-163">For example, if you have "OK", "Cancel" and "Browse" buttons you probably do not want the buttons sized to fit the content.</span></span> <span data-ttu-id="77e98-164">W tym przypadku <xref:System.Windows.Controls.Grid.IsSharedSizeScope%2A?displayProperty=nameWithType> dołączoną właściwość przydaje się do udostępniania tego samego rozmiaru między wiele elementów siatki.</span><span class="sxs-lookup"><span data-stu-id="77e98-164">In this case the <xref:System.Windows.Controls.Grid.IsSharedSizeScope%2A?displayProperty=nameWithType> attached property is useful for sharing the same sizing among multiple grid elements.</span></span> <span data-ttu-id="77e98-165">W poniższym przykładzie pokazano sposób udostępniania danych między wieloma rozmiaru wierszy i kolumn <xref:System.Windows.Controls.Grid> elementów.</span><span class="sxs-lookup"><span data-stu-id="77e98-165">The following example demonstrates how to share column and row sizing data between multiple <xref:System.Windows.Controls.Grid> elements.</span></span>

[!code-xaml[gridIssharedsizescopeProp#2](~/samples/snippets/csharp/VS_Snippets_Wpf/gridIssharedsizescopeProp/CSharp/Window1.xaml#2)]

> [!NOTE]
> <span data-ttu-id="77e98-166">Aby uzyskać cały przykładowy kod, zobacz [udziału właściwości ustalania rozmiaru między siatkami](../controls/how-to-share-sizing-properties-between-grids.md)</span><span class="sxs-lookup"><span data-stu-id="77e98-166">For the complete code sample, see [Share Sizing Properties Between Grids](../controls/how-to-share-sizing-properties-between-grids.md)</span></span>

## <a name="see-also"></a><span data-ttu-id="77e98-167">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="77e98-167">See also</span></span>

- [<span data-ttu-id="77e98-168">Globalizacja dla WPF</span><span class="sxs-lookup"><span data-stu-id="77e98-168">Globalization for WPF</span></span>](globalization-for-wpf.md)
- [<span data-ttu-id="77e98-169">Używanie automatycznego układu do utworzenia przycisku</span><span class="sxs-lookup"><span data-stu-id="77e98-169">Use Automatic Layout to Create a Button</span></span>](how-to-use-automatic-layout-to-create-a-button.md)
- [<span data-ttu-id="77e98-170">Używanie siatki do automatycznego układu</span><span class="sxs-lookup"><span data-stu-id="77e98-170">Use a Grid for Automatic Layout</span></span>](how-to-use-a-grid-for-automatic-layout.md)
