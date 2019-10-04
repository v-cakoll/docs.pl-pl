---
title: Korzystanie z automatycznego układu — Omówienie
ms.date: 03/30/2017
helpviewer_keywords:
- layout [WPF], automatic
- automatic layout [WPF]
ms.assetid: 6fed9264-18bb-4d05-8867-1fe356c6f687
ms.openlocfilehash: 0253c57f080705b648d9f416368d0fe974ac83ab
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/03/2019
ms.locfileid: "71834670"
---
# <a name="use-automatic-layout-overview"></a><span data-ttu-id="c41da-102">Korzystanie z automatycznego układu — Omówienie</span><span class="sxs-lookup"><span data-stu-id="c41da-102">Use Automatic Layout Overview</span></span>

<span data-ttu-id="c41da-103">W tym temacie przedstawiono wskazówki dla deweloperów dotyczące pisania aplikacji [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] z lokalizowalną [!INCLUDE[TLA#tla_ui#plural](../../../../includes/tlasharptla-uisharpplural-md.md)].</span><span class="sxs-lookup"><span data-stu-id="c41da-103">This topic introduces guidelines for developers on how to write [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] applications with localizable [!INCLUDE[TLA#tla_ui#plural](../../../../includes/tlasharptla-uisharpplural-md.md)].</span></span> <span data-ttu-id="c41da-104">W przeszłości lokalizacja interfejsu użytkownika była czasochłonna.</span><span class="sxs-lookup"><span data-stu-id="c41da-104">In the past, localization of a UI was a time consuming process.</span></span> <span data-ttu-id="c41da-105">Każdy język, który został dostosowany przez interfejs użytkownika, musi być dopasowany piksel po piksel.</span><span class="sxs-lookup"><span data-stu-id="c41da-105">Each language that the UI was adapted for required a pixel by pixel adjustment.</span></span> <span data-ttu-id="c41da-106">Obecnie w przypadku właściwych standardów kodowania i odpowiednich wzorów można utworzyć [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)], tak aby lokalizatory miały mniejszą zmianę rozmiarów i zmiany położenia.</span><span class="sxs-lookup"><span data-stu-id="c41da-106">Today with the right design and right coding standards, [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)] can be constructed so that localizers have less resizing and repositioning to do.</span></span> <span data-ttu-id="c41da-107">Podejście do pisania aplikacji, które mogą być łatwiejsze w zmianie rozmiaru i zmiany położenia, jest nazywane automatycznym układem i można je osiągnąć przy użyciu projektu aplikacji [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].</span><span class="sxs-lookup"><span data-stu-id="c41da-107">The approach to writing applications that can be more easily resized and repositioned is called automatic layout, and can be achieved by using [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application design.</span></span>

<a name="advantages_of_autolayout"></a>

## <a name="advantages-of-using-automatic-layout"></a><span data-ttu-id="c41da-108">Zalety korzystania z automatycznego układu</span><span class="sxs-lookup"><span data-stu-id="c41da-108">Advantages of Using Automatic Layout</span></span>

<span data-ttu-id="c41da-109">Ponieważ system prezentacji [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] jest zaawansowany i elastyczny, zapewnia możliwość układu elementów w aplikacji, które można dostosować w celu dopasowania do wymagań różnych języków.</span><span class="sxs-lookup"><span data-stu-id="c41da-109">Because the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] presentation system is powerful and flexible, it provides the ability to layout elements in an application that can be adjusted to fit the requirements of different languages.</span></span> <span data-ttu-id="c41da-110">Na poniższej liście przedstawiono niektóre zalety automatycznego układu.</span><span class="sxs-lookup"><span data-stu-id="c41da-110">The following list points out some of the advantages of automatic layout.</span></span>

- <span data-ttu-id="c41da-111">Interfejs użytkownika wyświetla się w dowolnym języku.</span><span class="sxs-lookup"><span data-stu-id="c41da-111">UI displays well  in any language.</span></span>

- <span data-ttu-id="c41da-112">Zmniejsza konieczność ponownego dopasowania pozycji i rozmiaru kontrolek po przetłumaczeniu tekstu.</span><span class="sxs-lookup"><span data-stu-id="c41da-112">Reduces the need to readjust position and size of controls after text is translated.</span></span>

- <span data-ttu-id="c41da-113">Zmniejsza konieczność ponownego dopasowania rozmiaru okna.</span><span class="sxs-lookup"><span data-stu-id="c41da-113">Reduces the need to readjust window size.</span></span>

- <span data-ttu-id="c41da-114">Układ interfejsu użytkownika jest renderowany prawidłowo w dowolnym języku.</span><span class="sxs-lookup"><span data-stu-id="c41da-114">UI layout renders properly in any language.</span></span>

- <span data-ttu-id="c41da-115">Lokalizację można zmniejszyć do momentu, w którym jest nieco więcej niż tłumaczenie ciągu.</span><span class="sxs-lookup"><span data-stu-id="c41da-115">Localization can be reduced to the point that it is little more than string translation.</span></span>

<a name="autolayout_controls"></a>

## <a name="automatic-layout-and-controls"></a><span data-ttu-id="c41da-116">Automatyczny układ i kontrolki</span><span class="sxs-lookup"><span data-stu-id="c41da-116">Automatic Layout and Controls</span></span>

<span data-ttu-id="c41da-117">Automatyczny układ umożliwia aplikacji dopasowanie rozmiaru formantu automatycznie.</span><span class="sxs-lookup"><span data-stu-id="c41da-117">Automatic layout enables an application to adjust the size of a control automatically.</span></span> <span data-ttu-id="c41da-118">Na przykład kontrolka może zmienić, aby pomieścić długość ciągu.</span><span class="sxs-lookup"><span data-stu-id="c41da-118">For example, a control can change to accommodate the length of a string.</span></span> <span data-ttu-id="c41da-119">Ta funkcja umożliwia lokalizatorom nazw tłumaczenie ciągu; nie trzeba już zmieniać rozmiaru formantu, aby dopasować go do przetłumaczonego tekstu.</span><span class="sxs-lookup"><span data-stu-id="c41da-119">This capability enables  localizers to translate the string; they no longer need to resize the control to fit the translated text.</span></span> <span data-ttu-id="c41da-120">Poniższy przykład tworzy przycisk z zawartością w języku angielskim.</span><span class="sxs-lookup"><span data-stu-id="c41da-120">The following example creates a button with English content.</span></span>

[!code-xaml[LocalizationBtn_snip#1](~/samples/snippets/csharp/VS_Snippets_Wpf/LocalizationBtn_snip/CS/Pane1.xaml#1)]

<span data-ttu-id="c41da-121">W tym przykładzie wszystkie czynności, które należy wykonać, aby można było zmienić tekst przycisku hiszpańskiego.</span><span class="sxs-lookup"><span data-stu-id="c41da-121">In the example, all you have to do to make a Spanish button is change the text.</span></span> <span data-ttu-id="c41da-122">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="c41da-122">For example,</span></span>

[!code-xaml[LocalizationBtn#1](~/samples/snippets/csharp/VS_Snippets_Wpf/LocalizationBtn/CS/Pane1.xaml#1)]

<span data-ttu-id="c41da-123">Na poniższej ilustracji przedstawiono dane wyjściowe przykładów kodu:</span><span class="sxs-lookup"><span data-stu-id="c41da-123">The following graphic shows the output of the code samples:</span></span>

![Ten sam przycisk z tekstem w różnych językach](./media/use-automatic-layout-overview/auto-resizable-button.png)

<a name="autolayout_coding"></a>

## <a name="automatic-layout-and-coding-standards"></a><span data-ttu-id="c41da-125">Automatyczne układ i standardy kodowania</span><span class="sxs-lookup"><span data-stu-id="c41da-125">Automatic Layout and Coding Standards</span></span>

<span data-ttu-id="c41da-126">Zastosowanie podejścia automatycznego do układu wymaga zestawu wzorców i standardów projektowania i reguł, aby utworzyć w pełni Lokalizowalny interfejs użytkownika.</span><span class="sxs-lookup"><span data-stu-id="c41da-126">Using the automatic layout approach requires a set of coding and design standards and rules to produce a fully localizable UI.</span></span> <span data-ttu-id="c41da-127">Poniższe wskazówki ułatwią automatyczne kodowanie układu.</span><span class="sxs-lookup"><span data-stu-id="c41da-127">The following guidelines will aid your automatic layout coding.</span></span>

<span data-ttu-id="c41da-128">**Nie używaj pozycji bezwzględnych**</span><span class="sxs-lookup"><span data-stu-id="c41da-128">**Do not use absolute positions**</span></span>

- <span data-ttu-id="c41da-129">Nie należy używać <xref:System.Windows.Controls.Canvas>, ponieważ umieszcza elementy w absolutnie.</span><span class="sxs-lookup"><span data-stu-id="c41da-129">Do not use <xref:System.Windows.Controls.Canvas> because it positions elements absolutely.</span></span>

- <span data-ttu-id="c41da-130">Użyj <xref:System.Windows.Controls.DockPanel>, <xref:System.Windows.Controls.StackPanel> i <xref:System.Windows.Controls.Grid> do położenia kontrolek.</span><span class="sxs-lookup"><span data-stu-id="c41da-130">Use <xref:System.Windows.Controls.DockPanel>, <xref:System.Windows.Controls.StackPanel>, and <xref:System.Windows.Controls.Grid> to position controls.</span></span>

<span data-ttu-id="c41da-131">Aby uzyskać informacje na temat dyskusji na temat różnych typów paneli, zobacz [Omówienie paneli](../controls/panels-overview.md).</span><span class="sxs-lookup"><span data-stu-id="c41da-131">For a discussion about various types of panels, see [Panels Overview](../controls/panels-overview.md).</span></span>

<span data-ttu-id="c41da-132">**Nie ustawiaj stałego rozmiaru okna**</span><span class="sxs-lookup"><span data-stu-id="c41da-132">**Do not set a fixed size for a window**</span></span>

- <span data-ttu-id="c41da-133">Użyj <xref:System.Windows.Window.SizeToContent%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="c41da-133">Use <xref:System.Windows.Window.SizeToContent%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="c41da-134">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="c41da-134">For example:</span></span>

  [!code-xaml[LocalizationGrid#2](~/samples/snippets/csharp/VS_Snippets_Wpf/LocalizationGrid/CS/Pane1.xaml#2)]

<span data-ttu-id="c41da-135">**Dodaj <xref:System.Windows.FrameworkElement.FlowDirection%2A>**</span><span class="sxs-lookup"><span data-stu-id="c41da-135">**Add a <xref:System.Windows.FrameworkElement.FlowDirection%2A>**</span></span>

- <span data-ttu-id="c41da-136">Dodaj <xref:System.Windows.FrameworkElement.FlowDirection%2A> do elementu głównego aplikacji.</span><span class="sxs-lookup"><span data-stu-id="c41da-136">Add a <xref:System.Windows.FrameworkElement.FlowDirection%2A> to the root element of your application.</span></span>

  <span data-ttu-id="c41da-137">WPF zapewnia wygodny sposób obsługi układów poziomych, dwukierunkowych i pionowych.</span><span class="sxs-lookup"><span data-stu-id="c41da-137">WPF provides a convenient way to support horizontal, bidirectional, and vertical layouts.</span></span> <span data-ttu-id="c41da-138">W środowisku prezentacji Właściwość <xref:System.Windows.FrameworkElement.FlowDirection%2A> może służyć do definiowania układu.</span><span class="sxs-lookup"><span data-stu-id="c41da-138">In presentation framework, the <xref:System.Windows.FrameworkElement.FlowDirection%2A> property can be used to define layout.</span></span> <span data-ttu-id="c41da-139">Wzorce kierunku przepływu są następujące:</span><span class="sxs-lookup"><span data-stu-id="c41da-139">The flow-direction patterns are:</span></span>

  - <span data-ttu-id="c41da-140"><xref:System.Windows.FlowDirection.LeftToRight?displayProperty=nameWithType> (LrTb) — układ poziomy dla języków łacińskich, wschodnioazjatyckich i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="c41da-140"><xref:System.Windows.FlowDirection.LeftToRight?displayProperty=nameWithType> (LrTb) — horizontal layout for Latin, East Asian, and so forth.</span></span>

  - <span data-ttu-id="c41da-141"><xref:System.Windows.FlowDirection.RightToLeft?displayProperty=nameWithType> (RlTb) — dwukierunkowy dla języka arabskiego, hebrajskiego i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="c41da-141"><xref:System.Windows.FlowDirection.RightToLeft?displayProperty=nameWithType> (RlTb) — bidirectional for Arabic, Hebrew, and so forth.</span></span>

<span data-ttu-id="c41da-142">**Używaj czcionek złożonych zamiast czcionek fizycznych**</span><span class="sxs-lookup"><span data-stu-id="c41da-142">**Use composite fonts instead of physical fonts**</span></span>

- <span data-ttu-id="c41da-143">W przypadku czcionek złożonych nie ma potrzeby zlokalizowania właściwości <xref:System.Windows.Controls.Control.FontFamily%2A>.</span><span class="sxs-lookup"><span data-stu-id="c41da-143">With composite fonts, the <xref:System.Windows.Controls.Control.FontFamily%2A> property does not need to be localized.</span></span>

- <span data-ttu-id="c41da-144">Deweloperzy mogą korzystać z jednej z następujących czcionek lub tworzyć własne.</span><span class="sxs-lookup"><span data-stu-id="c41da-144">Developers can use one of the following fonts or create their own.</span></span>

  - <span data-ttu-id="c41da-145">Globalny interfejs użytkownika</span><span class="sxs-lookup"><span data-stu-id="c41da-145">Global User Interface</span></span>
  - <span data-ttu-id="c41da-146">Globalna szeryfowa sieć San</span><span class="sxs-lookup"><span data-stu-id="c41da-146">Global San Serif</span></span>
  - <span data-ttu-id="c41da-147">Szeryfy globalne</span><span class="sxs-lookup"><span data-stu-id="c41da-147">Global Serif</span></span>

<span data-ttu-id="c41da-148">**Dodaj plik XML: lang**</span><span class="sxs-lookup"><span data-stu-id="c41da-148">**Add xml:lang**</span></span>

- <span data-ttu-id="c41da-149">Dodaj atrybut `xml:lang` w głównym elemencie interfejsu użytkownika, na przykład `xml:lang="en-US"` dla aplikacji w języku angielskim.</span><span class="sxs-lookup"><span data-stu-id="c41da-149">Add the `xml:lang` attribute in the root element of your UI, such as `xml:lang="en-US"` for an English application.</span></span>

- <span data-ttu-id="c41da-150">Ponieważ czcionki złożone używają `xml:lang` w celu określenia używanej czcionki, należy ustawić tę właściwość, aby obsługiwała scenariusze wielojęzyczne.</span><span class="sxs-lookup"><span data-stu-id="c41da-150">Because composite fonts use `xml:lang` to determine what font to use, set this property to support multilingual scenarios.</span></span>

<a name="autolay_grids"></a>

## <a name="automatic-layout-and-grids"></a><span data-ttu-id="c41da-151">Automatyczny układ i siatki</span><span class="sxs-lookup"><span data-stu-id="c41da-151">Automatic Layout and Grids</span></span>

<span data-ttu-id="c41da-152">Element <xref:System.Windows.Controls.Grid> jest przydatny do automatycznego układu, ponieważ umożliwia deweloperowi Pozycjonowanie elementów.</span><span class="sxs-lookup"><span data-stu-id="c41da-152">The <xref:System.Windows.Controls.Grid> element, is useful for automatic layout because it enables a developer to position elements.</span></span> <span data-ttu-id="c41da-153">Kontrolka <xref:System.Windows.Controls.Grid> umożliwia dystrybuowanie dostępnego miejsca między elementami podrzędnymi przy użyciu układu kolumn i wierszy.</span><span class="sxs-lookup"><span data-stu-id="c41da-153">A <xref:System.Windows.Controls.Grid> control is capable of distributing the available space among its child elements, using a column and row arrangement.</span></span> <span data-ttu-id="c41da-154">Elementy interfejsu użytkownika mogą obejmować wiele komórek i można mieć siatki w obrębie siatki.</span><span class="sxs-lookup"><span data-stu-id="c41da-154">The UI elements can span multiple cells, and it is possible to have grids within grids.</span></span> <span data-ttu-id="c41da-155">Siatki są przydatne, ponieważ umożliwiają utworzenie i umieszczenie złożonego interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="c41da-155">Grids are useful because they enable you to create and position complex UI.</span></span> <span data-ttu-id="c41da-156">Poniższy przykład ilustruje użycie siatki do umieszczenia niektórych przycisków i tekstu.</span><span class="sxs-lookup"><span data-stu-id="c41da-156">The following example demonstrates using a grid to position some buttons and text.</span></span> <span data-ttu-id="c41da-157">Zauważ, że wysokość i szerokość komórek są ustawione na <xref:System.Windows.GridUnitType.Auto>; w związku z tym komórka, która zawiera przycisk z obrazem, dopasowuje się do obrazu.</span><span class="sxs-lookup"><span data-stu-id="c41da-157">Notice that the height and width of the cells are set to <xref:System.Windows.GridUnitType.Auto>; therefore, the cell that contains the button with an image adjusts to fit the image.</span></span>

[!code-xaml[LocalizationGrid#1](~/samples/snippets/csharp/VS_Snippets_Wpf/LocalizationGrid/CS/Pane1.xaml#1)]

<span data-ttu-id="c41da-158">Na poniższej ilustracji przedstawiono siatkę wyprodukowanych przez poprzedni kod.</span><span class="sxs-lookup"><span data-stu-id="c41da-158">The following graphic shows the grid produced by the previous code.</span></span>

<span data-ttu-id="c41da-159">![Przykład siatki](./media/glob-grid.png "glob_grid") siatki</span><span class="sxs-lookup"><span data-stu-id="c41da-159">![Grid example](./media/glob-grid.png "glob_grid") Grid</span></span>

<a name="autolay_grids_issharedsizescope"></a>

## <a name="automatic-layout-and-grids-using-the-issharedsizescope-property"></a><span data-ttu-id="c41da-160">Automatyczne układ i siatki przy użyciu właściwości IsSharedSizeScope</span><span class="sxs-lookup"><span data-stu-id="c41da-160">Automatic Layout and Grids Using the IsSharedSizeScope Property</span></span>

<span data-ttu-id="c41da-161">Element <xref:System.Windows.Controls.Grid> jest przydatny w aplikacjach lokalizowalnych do tworzenia formantów, które dostosowują się do zawartości.</span><span class="sxs-lookup"><span data-stu-id="c41da-161">A <xref:System.Windows.Controls.Grid> element is useful in localizable applications to create controls that adjust to fit content.</span></span> <span data-ttu-id="c41da-162">Jednak w przypadku, gdy kontrolki mają obsługiwać określony rozmiar, niezależnie od zawartości.</span><span class="sxs-lookup"><span data-stu-id="c41da-162">However, at times you want controls to maintain a particular size regardless of content.</span></span> <span data-ttu-id="c41da-163">Na przykład jeśli masz przyciski "OK", "Anuluj" i "Przeglądaj", prawdopodobnie nie chcesz, aby rozmiar przycisków był dopasowany do zawartości.</span><span class="sxs-lookup"><span data-stu-id="c41da-163">For example, if you have "OK", "Cancel" and "Browse" buttons you probably do not want the buttons sized to fit the content.</span></span> <span data-ttu-id="c41da-164">W takim przypadku dołączona <xref:System.Windows.Controls.Grid.IsSharedSizeScope%2A?displayProperty=nameWithType> właściwość jest przydatna do udostępniania tego samego zmiany rozmiarów między wieloma elementami siatki.</span><span class="sxs-lookup"><span data-stu-id="c41da-164">In this case the <xref:System.Windows.Controls.Grid.IsSharedSizeScope%2A?displayProperty=nameWithType> attached property is useful for sharing the same sizing among multiple grid elements.</span></span> <span data-ttu-id="c41da-165">Poniższy przykład ilustruje sposób udostępniania danych o wymiarach kolumn i wierszy między wieloma elementami <xref:System.Windows.Controls.Grid>.</span><span class="sxs-lookup"><span data-stu-id="c41da-165">The following example demonstrates how to share column and row sizing data between multiple <xref:System.Windows.Controls.Grid> elements.</span></span>

[!code-xaml[gridIssharedsizescopeProp#2](~/samples/snippets/csharp/VS_Snippets_Wpf/gridIssharedsizescopeProp/CSharp/Window1.xaml#2)]

> [!NOTE]
> <span data-ttu-id="c41da-166">Aby uzyskać pełny przykład kodu, zobacz [udostępnianie właściwości zmiany rozmiarów między siatkami](../controls/how-to-share-sizing-properties-between-grids.md).</span><span class="sxs-lookup"><span data-stu-id="c41da-166">For the complete code sample, see [Share Sizing Properties Between Grids](../controls/how-to-share-sizing-properties-between-grids.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="c41da-167">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c41da-167">See also</span></span>

- [<span data-ttu-id="c41da-168">Globalizacja dla WPF</span><span class="sxs-lookup"><span data-stu-id="c41da-168">Globalization for WPF</span></span>](globalization-for-wpf.md)
- [<span data-ttu-id="c41da-169">Tworzenie przycisku przy użyciu automatycznego układu</span><span class="sxs-lookup"><span data-stu-id="c41da-169">Use Automatic Layout to Create a Button</span></span>](how-to-use-automatic-layout-to-create-a-button.md)
- [<span data-ttu-id="c41da-170">Użyj siatki do automatycznego układu</span><span class="sxs-lookup"><span data-stu-id="c41da-170">Use a Grid for Automatic Layout</span></span>](how-to-use-a-grid-for-automatic-layout.md)
