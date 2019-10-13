---
title: Korzystanie z automatycznego układu — Omówienie
ms.date: 03/30/2017
helpviewer_keywords:
- layout [WPF], automatic
- automatic layout [WPF]
ms.assetid: 6fed9264-18bb-4d05-8867-1fe356c6f687
ms.openlocfilehash: 2fe473da3eeabef3852e3003e61b3b9604332855
ms.sourcegitcommit: 9c3a4f2d3babca8919a1e490a159c1500ba7a844
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/12/2019
ms.locfileid: "72291271"
---
# <a name="use-automatic-layout-overview"></a>Korzystanie z automatycznego układu — Omówienie

W tym temacie przedstawiono wskazówki dla deweloperów dotyczące pisania aplikacji [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] z lokalizowalnymi interfejsami użytkownika (interfejsów użytkownika). W przeszłości lokalizacja interfejsu użytkownika była czasochłonna. Każdy język, który został dostosowany przez interfejs użytkownika, musi być dopasowany piksel po piksel. Obecnie w przypadku właściwych standardów kodowania i odpowiednich wzorów interfejsów użytkownika można skonstruować, tak aby lokalizatory miały mniejszą zmianę rozmiarów i zmiany położenia. Podejście do pisania aplikacji, które mogą być łatwiejsze w zmianie rozmiaru i zmiany położenia, jest nazywane automatycznym układem i można je osiągnąć przy użyciu projektu aplikacji [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].

<a name="advantages_of_autolayout"></a>

## <a name="advantages-of-using-automatic-layout"></a>Zalety korzystania z automatycznego układu

Ponieważ system prezentacji [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] jest zaawansowany i elastyczny, zapewnia możliwość układu elementów w aplikacji, które można dostosować w celu dopasowania do wymagań różnych języków. Na poniższej liście przedstawiono niektóre zalety automatycznego układu.

- Interfejs użytkownika wyświetla się w dowolnym języku.

- Zmniejsza konieczność ponownego dopasowania pozycji i rozmiaru kontrolek po przetłumaczeniu tekstu.

- Zmniejsza konieczność ponownego dopasowania rozmiaru okna.

- Układ interfejsu użytkownika jest renderowany prawidłowo w dowolnym języku.

- Lokalizację można zmniejszyć do momentu, w którym jest nieco więcej niż tłumaczenie ciągu.

<a name="autolayout_controls"></a>

## <a name="automatic-layout-and-controls"></a>Automatyczny układ i kontrolki

Automatyczny układ umożliwia aplikacji dopasowanie rozmiaru formantu automatycznie. Na przykład kontrolka może zmienić, aby pomieścić długość ciągu. Ta funkcja umożliwia lokalizatorom nazw tłumaczenie ciągu; nie trzeba już zmieniać rozmiaru formantu, aby dopasować go do przetłumaczonego tekstu. Poniższy przykład tworzy przycisk z zawartością w języku angielskim.

[!code-xaml[LocalizationBtn_snip#1](~/samples/snippets/csharp/VS_Snippets_Wpf/LocalizationBtn_snip/CS/Pane1.xaml#1)]

W tym przykładzie wszystkie czynności, które należy wykonać, aby można było zmienić tekst przycisku hiszpańskiego. Na przykład:

[!code-xaml[LocalizationBtn#1](~/samples/snippets/csharp/VS_Snippets_Wpf/LocalizationBtn/CS/Pane1.xaml#1)]

Na poniższej ilustracji przedstawiono dane wyjściowe przykładów kodu:

![Ten sam przycisk z tekstem w różnych językach](./media/use-automatic-layout-overview/auto-resizable-button.png)

<a name="autolayout_coding"></a>

## <a name="automatic-layout-and-coding-standards"></a>Automatyczne układ i standardy kodowania

Zastosowanie podejścia automatycznego do układu wymaga zestawu wzorców i standardów projektowania i reguł, aby utworzyć w pełni Lokalizowalny interfejs użytkownika. Poniższe wskazówki ułatwią automatyczne kodowanie układu.

**Nie używaj pozycji bezwzględnych**

- Nie należy używać <xref:System.Windows.Controls.Canvas>, ponieważ umieszcza elementy w absolutnie.

- Użyj <xref:System.Windows.Controls.DockPanel>, <xref:System.Windows.Controls.StackPanel> i <xref:System.Windows.Controls.Grid> do położenia kontrolek.

Aby uzyskać informacje na temat dyskusji na temat różnych typów paneli, zobacz [Omówienie paneli](../controls/panels-overview.md).

**Nie ustawiaj stałego rozmiaru okna**

- Użyj <xref:System.Windows.Window.SizeToContent%2A?displayProperty=nameWithType>. Na przykład:

  [!code-xaml[LocalizationGrid#2](~/samples/snippets/csharp/VS_Snippets_Wpf/LocalizationGrid/CS/Pane1.xaml#2)]

**Dodaj <xref:System.Windows.FrameworkElement.FlowDirection%2A>**

- Dodaj <xref:System.Windows.FrameworkElement.FlowDirection%2A> do elementu głównego aplikacji.

  WPF zapewnia wygodny sposób obsługi układów poziomych, dwukierunkowych i pionowych. W środowisku prezentacji Właściwość <xref:System.Windows.FrameworkElement.FlowDirection%2A> może służyć do definiowania układu. Wzorce kierunku przepływu są następujące:

  - <xref:System.Windows.FlowDirection.LeftToRight?displayProperty=nameWithType> (LrTb) — układ poziomy dla języków łacińskich, wschodnioazjatyckich i tak dalej.

  - <xref:System.Windows.FlowDirection.RightToLeft?displayProperty=nameWithType> (RlTb) — dwukierunkowy dla języka arabskiego, hebrajskiego i tak dalej.

**Używaj czcionek złożonych zamiast czcionek fizycznych**

- W przypadku czcionek złożonych nie ma potrzeby zlokalizowania właściwości <xref:System.Windows.Controls.Control.FontFamily%2A>.

- Deweloperzy mogą korzystać z jednej z następujących czcionek lub tworzyć własne.

  - Globalny interfejs użytkownika
  - Globalna szeryfowa sieć San
  - Szeryfy globalne

**Dodaj plik XML: lang**

- Dodaj atrybut `xml:lang` w głównym elemencie interfejsu użytkownika, na przykład `xml:lang="en-US"` dla aplikacji w języku angielskim.

- Ponieważ czcionki złożone używają `xml:lang` w celu określenia używanej czcionki, należy ustawić tę właściwość, aby obsługiwała scenariusze wielojęzyczne.

<a name="autolay_grids"></a>

## <a name="automatic-layout-and-grids"></a>Automatyczny układ i siatki

Element <xref:System.Windows.Controls.Grid> jest przydatny do automatycznego układu, ponieważ umożliwia deweloperowi Pozycjonowanie elementów. Kontrolka <xref:System.Windows.Controls.Grid> umożliwia dystrybuowanie dostępnego miejsca między elementami podrzędnymi przy użyciu układu kolumn i wierszy. Elementy interfejsu użytkownika mogą obejmować wiele komórek i można mieć siatki w obrębie siatki. Siatki są przydatne, ponieważ umożliwiają utworzenie i umieszczenie złożonego interfejsu użytkownika. Poniższy przykład ilustruje użycie siatki do umieszczenia niektórych przycisków i tekstu. Zauważ, że wysokość i szerokość komórek są ustawione na <xref:System.Windows.GridUnitType.Auto>; w związku z tym komórka, która zawiera przycisk z obrazem, dopasowuje się do obrazu.

[!code-xaml[LocalizationGrid#1](~/samples/snippets/csharp/VS_Snippets_Wpf/LocalizationGrid/CS/Pane1.xaml#1)]

Na poniższej ilustracji przedstawiono siatkę wyprodukowanych przez poprzedni kod.

![Przykład siatki](./media/glob-grid.png "glob_grid") siatki

<a name="autolay_grids_issharedsizescope"></a>

## <a name="automatic-layout-and-grids-using-the-issharedsizescope-property"></a>Automatyczne układ i siatki przy użyciu właściwości IsSharedSizeScope

Element <xref:System.Windows.Controls.Grid> jest przydatny w aplikacjach lokalizowalnych do tworzenia formantów, które dostosowują się do zawartości. Jednak w przypadku, gdy kontrolki mają obsługiwać określony rozmiar, niezależnie od zawartości. Na przykład jeśli masz przyciski "OK", "Anuluj" i "Przeglądaj", prawdopodobnie nie chcesz, aby rozmiar przycisków był dopasowany do zawartości. W takim przypadku dołączona <xref:System.Windows.Controls.Grid.IsSharedSizeScope%2A?displayProperty=nameWithType> właściwość jest przydatna do udostępniania tego samego zmiany rozmiarów między wieloma elementami siatki. Poniższy przykład ilustruje sposób udostępniania danych o wymiarach kolumn i wierszy między wieloma elementami <xref:System.Windows.Controls.Grid>.

[!code-xaml[gridIssharedsizescopeProp#2](~/samples/snippets/csharp/VS_Snippets_Wpf/gridIssharedsizescopeProp/CSharp/Window1.xaml#2)]

> [!NOTE]
> Aby uzyskać pełny przykład kodu, zobacz [udostępnianie właściwości zmiany rozmiarów między siatkami](../controls/how-to-share-sizing-properties-between-grids.md).

## <a name="see-also"></a>Zobacz także

- [Globalizacja dla WPF](globalization-for-wpf.md)
- [Tworzenie przycisku przy użyciu automatycznego układu](how-to-use-automatic-layout-to-create-a-button.md)
- [Użyj siatki do automatycznego układu](how-to-use-a-grid-for-automatic-layout.md)
