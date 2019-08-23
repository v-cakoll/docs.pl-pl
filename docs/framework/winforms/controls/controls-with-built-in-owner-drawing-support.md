---
title: Formanty z wbudowaną obsługą rysowania przez właściciela
ms.date: 03/30/2017
helpviewer_keywords:
- drawing [Windows Forms], owner
- drawing [Windows Forms], custom
- controls [Windows Forms], changing appearance
- custom drawing
- owner drawing
ms.assetid: 3823d01e-9610-43e6-864d-99f9b7c2b351
ms.openlocfilehash: f0d4b99f9ee0134fc7334a941dd5ef4fd7ba3df3
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69930193"
---
# <a name="controls-with-built-in-owner-drawing-support"></a>Formanty z wbudowaną obsługą rysowania przez właściciela
Rysowanie przez właściciela w Windows Forms, który jest również znany jako rysunek niestandardowy, jest techniką zmiany wyglądu wizualizacji niektórych kontrolek.  
  
> [!NOTE]
> Słowo "Control" w tym temacie służy do oznaczania klas, które pochodzą z albo <xref:System.Windows.Forms.Control> lub <xref:System.ComponentModel.Component>.  
  
 Zwykle system Windows automatycznie obsługuje malowanie przy użyciu ustawień właściwości, <xref:System.Windows.Forms.Control.BackColor%2A> takich jak w celu określenia wyglądu kontrolki. Przy użyciu rysowania przez właściciela można przetworzyć proces malowania, zmieniając elementy wyglądu, które nie są dostępne za pomocą właściwości. Na przykład wiele kontrolek pozwala ustawić kolor wyświetlanego tekstu, ale jest ograniczony do jednego koloru. Rysowanie przez właściciela umożliwia wykonywanie takich czynności jak wyświetlanie części tekstu w kolorze czarnym i w kolorze czerwonym.  
  
 W tym temacie rysowanie właściciela jest podobne do rysowania grafiki w formularzu. Na przykład można użyć metod graficznych w programie obsługi dla <xref:System.Windows.Forms.Control.Paint> zdarzenia formularza do emulowania `ListBox` kontrolki, ale trzeba napisać własny kod, aby obsłużyć wszystkie interakcje z użytkownikiem. Przy użyciu rysowania przez właściciela formant używa kodu do rysowania jego zawartości, ale w przeciwnym razie zachowuje wszystkie jego funkcje wewnętrzne. Możesz użyć metod graficznych, aby narysować każdy element w kontrolce lub dostosować niektóre aspekty każdego elementu przy użyciu domyślnego wyglądu dla innych aspektów każdego elementu.  
  
## <a name="owner-drawing-in-windows-forms-controls"></a>Rysowanie przez właściciela w kontrolkach Windows Forms  
 Aby wykonać rysowanie przez właściciela w kontrolkach, które go obsługują, zwykle ustawiana jest jedna właściwość i obsłużą jedno lub więcej zdarzeń.  
  
 Większość formantów, które obsługują rysowanie właściciela, `OwnerDraw` ma `DrawMode` właściwość lub, która wskazuje, czy kontrolka będzie zgłaszać zdarzenia związane z rysunkiem, czy zdarzenia, gdy malują się one w sobie.  
  
 Kontrolki, które nie mają `OwnerDraw` właściwości `DrawMode` lub zawierają `DataGridView` kontrolkę, która umożliwia `ToolStrip` rysowanie zdarzeń, które są wykonywane automatycznie, i kontrolki, która jest rysowana przy użyciu zewnętrznej klasy renderowania, która ma własne zdarzenia związane ze rysowaniem.  
  
 Istnieje wiele różnych rodzajów zdarzeń rysowania, ale w celu narysowania pojedynczego elementu wewnątrz kontrolki występuje typowe zdarzenie rysowania. Program obsługi zdarzeń odbiera `EventArgs` obiekt, który zawiera informacje o rysowanym elemencie i narzędziach, których można użyć do narysowania. Na przykład ten obiekt zwykle zawiera numer indeksu elementu w obrębie jego kolekcji nadrzędnej, <xref:System.Drawing.Rectangle> który wskazuje granice wyświetlania elementu <xref:System.Drawing.Graphics> i obiekt do wywoływania metod malowania. W przypadku niektórych zdarzeń `EventArgs` obiekt zawiera dodatkowe informacje na temat elementu i metod, które można wywołać w celu malowania niektórych aspektów elementu domyślnie, takich jak tło lub prostokąt fokusu.  
  
 Aby utworzyć kontrolkę wielokrotnego użytku, która zawiera dostosowania rysowane przez właściciela, Utwórz nową klasę pochodzącą z klasy kontrolki obsługującej rysowanie przez właściciela. Zamiast obsłużyć zdarzenia rysowania, Uwzględnij swój kod rysowania przez właściciela w zastąpieniach `On`dla odpowiedniej metody lub metod *EventName* w nowej klasie. Upewnij się, że w tym przypadku wywoływana `On`jest metoda lub metody klasy bazowej, tak aby użytkownicy Twojej kontrolki mogli obsłużyć zdarzenia rysowania przez właściciela i zapewnić dodatkowe dostosowanie.  
  
 Następujące kontrolki Windows Forms obsługują rysowanie właściciela we wszystkich wersjach .NET Framework:  
  
- <xref:System.Windows.Forms.ListBox>  
  
- <xref:System.Windows.Forms.ComboBox>  
  
- <xref:System.Windows.Forms.MenuItem>(używane przez <xref:System.Windows.Forms.MainMenu> i <xref:System.Windows.Forms.ContextMenu>)  
  
- <xref:System.Windows.Forms.TabControl>  
  
 Poniższe kontrolki obsługują rysowanie właściciela tylko w .NET Framework 2,0:  
  
- <xref:System.Windows.Forms.ToolTip>  
  
- <xref:System.Windows.Forms.ListView>  
  
- <xref:System.Windows.Forms.TreeView>  
  
 Poniższe kontrolki obsługują rysowanie właściciela i są nowe w .NET Framework 2,0:  
  
- <xref:System.Windows.Forms.DataGridView>  
  
- <xref:System.Windows.Forms.ToolStrip>  
  
 Poniższe sekcje zawierają dodatkowe szczegóły dla każdej z tych kontrolek.  
  
### <a name="listbox-and-combobox-controls"></a>ListBox i ComboBox — formanty  
 Formanty <xref:System.Windows.Forms.ListBox> i<xref:System.Windows.Forms.ComboBox> umożliwiają rysowanie poszczególnych elementów w formancie albo w jednym rozmiarze, albo w różnych rozmiarach.  
  
> [!NOTE]
> Chociaż formant pochodzi <xref:System.Windows.Forms.ListBox> od kontrolki, nie obsługuje rysowania przez właściciela. <xref:System.Windows.Forms.CheckedListBox>  
  
 Aby narysować każdy element o takim samym rozmiarze, `DrawMode` należy ustawić <xref:System.Windows.Forms.DrawMode.OwnerDrawFixed> właściwość na i `DrawItem` obsłużyć zdarzenie.  
  
 Aby narysować każdy element przy użyciu innego rozmiaru, należy `DrawMode` ustawić właściwość <xref:System.Windows.Forms.DrawMode.OwnerDrawVariable> na `DrawItem` i obsłużyć zarówno `MeasureItem` zdarzenie, jak i. Zdarzenie umożliwia wskazanie rozmiaru elementu `DrawItem` przed wystąpieniem zdarzenia dla tego elementu. `MeasureItem`  
  
 Aby uzyskać więcej informacji, w tym przykłady kodu, zobacz następujące tematy:  
  
- <xref:System.Windows.Forms.ListBox.DrawMode%2A?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.ListBox.MeasureItem?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.ListBox.DrawItem?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.ComboBox.DrawMode%2A?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.ComboBox.MeasureItem?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.ComboBox.DrawItem?displayProperty=nameWithType>  
  
- [Instrukcje: Tworzenie tekstu o zmiennym rozmiarze w kontrolce ComboBox](how-to-create-variable-sized-text-in-a-combobox-control.md)  
  
### <a name="menuitem-component"></a>MenuItem, składnik  
 Składnik reprezentuje pojedynczy element menu <xref:System.Windows.Forms.MainMenu> w składniku lub <xref:System.Windows.Forms.ContextMenu>. <xref:System.Windows.Forms.MenuItem>  
  
 Aby narysować <xref:System.Windows.Forms.MenuItem>, ustaw jej `OwnerDraw` właściwość na `true` i obsługuj jej `DrawItem` zdarzenie. Aby dostosować rozmiar elementu menu przed `DrawItem` wystąpieniem zdarzenia, należy obsłużyć `MeasureItem` zdarzenie elementu.  
  
 Aby uzyskać więcej informacji, w tym przykłady kodu, zobacz następujące tematy dotyczące odwołań:  
  
- <xref:System.Windows.Forms.MenuItem.OwnerDraw%2A?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.MenuItem.DrawItem?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.MenuItem.MeasureItem?displayProperty=nameWithType>  
  
### <a name="tabcontrol-control"></a>TabControl — Formant  
 <xref:System.Windows.Forms.TabControl> Kontrolka umożliwia rysowanie poszczególnych kart w formancie. Rysowanie właściciela dotyczy tylko kart; <xref:System.Windows.Forms.TabPage> zawartość nie jest modyfikowana.  
  
 Aby narysować każdą kartę w <xref:System.Windows.Forms.TabControl>, należy `DrawMode` ustawić `DrawItem` właściwość na <xref:System.Windows.Forms.TabDrawMode.OwnerDrawFixed> i obsłużyć zdarzenie. To zdarzenie występuje raz dla każdej karty tylko wtedy, gdy karta jest widoczna w formancie.  
  
 Aby uzyskać więcej informacji, w tym przykłady kodu, zobacz następujące tematy dotyczące odwołań:  
  
- <xref:System.Windows.Forms.TabControl.DrawMode%2A?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.TabControl.DrawItem?displayProperty=nameWithType>  
  
### <a name="tooltip-component"></a>ToolTip — Składnik  
 <xref:System.Windows.Forms.ToolTip> Składnik umożliwia narysowanie całej etykietki narzędzia, gdy zostanie ona wyświetlona.  
  
 Aby narysować <xref:System.Windows.Forms.ToolTip>, ustaw jej `OwnerDraw` właściwość na `true` i obsługuj jej `Draw` zdarzenie. Aby <xref:System.Windows.Forms.ToolTip> dostosować rozmiar `Draw` przed wystąpieniem `Popup` zdarzenia, należy obsłużyć zdarzenie i ustawić <xref:System.Windows.Forms.PopupEventArgs.ToolTipSize%2A> właściwość w programie obsługi zdarzeń.  
  
 Aby uzyskać więcej informacji, w tym przykłady kodu, zobacz następujące tematy dotyczące odwołań:  
  
- <xref:System.Windows.Forms.ToolTip.OwnerDraw%2A?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.ToolTip.Draw?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.ToolTip.Popup?displayProperty=nameWithType>  
  
### <a name="listview-control"></a>ListView — Formant  
 <xref:System.Windows.Forms.ListView> Kontrolka umożliwia rysowanie poszczególnych elementów, podelementów i nagłówków kolumn w kontrolce.  
  
 Aby włączyć rysowanie właściciela w kontrolce, ustaw `OwnerDraw` właściwość na. `true`  
  
 Aby narysować każdy element w kontrolce, obsłużyć `DrawItem` zdarzenie.  
  
 Aby narysować każdy nagłówek podelementu lub kolumny w kontrolce, gdy <xref:System.Windows.Forms.ListView.View%2A> właściwość jest ustawiona na `DrawSubItem` <xref:System.Windows.Forms.View.Details>, `DrawColumnHeader` obsłużyć zdarzenia i.  
  
 Aby uzyskać więcej informacji, w tym przykłady kodu, zobacz następujące tematy dotyczące odwołań:  
  
- <xref:System.Windows.Forms.ListView.OwnerDraw%2A?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.ListView.DrawItem?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.ListView.DrawSubItem?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.ListView.DrawColumnHeader?displayProperty=nameWithType>  
  
### <a name="treeview-control"></a>TreeView — Formant  
 <xref:System.Windows.Forms.TreeView> Kontrolka umożliwia rysowanie poszczególnych węzłów w formancie.  
  
 Aby narysować tylko tekst wyświetlany w każdym węźle, należy ustawić `DrawMode` właściwość na <xref:System.Windows.Forms.TreeViewDrawMode.OwnerDrawText> i obsłużyć `DrawNode` zdarzenie do narysowania tekstu.  
  
 Aby narysować wszystkie elementy każdego węzła, należy ustawić `DrawMode` właściwość na <xref:System.Windows.Forms.TreeViewDrawMode.OwnerDrawAll> i obsłużyć zdarzenie, aby rysować elementy, które są `DrawNode` potrzebne, takie jak tekst, ikony, pola wyboru, znaki plus i minus i linie łączące węzły.  
  
 Aby uzyskać więcej informacji, w tym przykłady kodu, zobacz następujące tematy dotyczące odwołań:  
  
- <xref:System.Windows.Forms.TreeView.DrawMode%2A?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.TreeView.DrawNode?displayProperty=nameWithType>  
  
### <a name="datagridview-control"></a>DataGridView — Formant  
 <xref:System.Windows.Forms.DataGridView> Kontrolka umożliwia rysowanie pojedynczych komórek i wierszy w formancie.  
  
 Aby narysować pojedyncze komórki, obsłuż `CellPainting` zdarzenie.  
  
 Aby narysować pojedyncze wiersze lub elementy wierszy, należy obsłużyć jedno lub `RowPrePaint` oba `RowPostPaint` zdarzenia i. Zdarzenie występuje przed narysowaniem komórek w wierszu, `RowPostPaint` a zdarzenie występuje po narysowaniu komórek. `RowPrePaint` Można obsługiwać zarówno zdarzenia, jak i `CellPainting` zdarzenia w celu oddzielenia tła wierszy, poszczególnych komórek i pierwszego planu wiersza, lub można podać konkretne dostosowania, gdy są potrzebne, i użyć domyślnego wyświetlania dla innych elementów wiersza.  
  
 Aby uzyskać więcej informacji, w tym przykłady kodu, zobacz następujące tematy:  
  
- <xref:System.Windows.Forms.DataGridView.CellPainting>  
  
- <xref:System.Windows.Forms.DataGridView.RowPrePaint>  
  
- <xref:System.Windows.Forms.DataGridView.RowPostPaint>  
  
- [Instrukcje: Dostosowywanie wyglądu komórek w kontrolce DataGridView Windows Forms](customize-the-appearance-of-cells-in-the-datagrid.md)  
  
- [Instrukcje: Dostosuj wygląd wierszy w kontrolce DataGridView Windows Forms](customize-the-appearance-of-rows-in-the-datagrid.md)  
  
### <a name="toolstrip-control"></a>ToolStrip — Formant  
 <xref:System.Windows.Forms.ToolStrip>formanty pochodne umożliwiają dostosowanie dowolnego aspektu ich wyglądu.  
  
 Aby zapewnić niestandardowe renderowanie <xref:System.Windows.Forms.ToolStrip> formantów, należy `Renderer` ustawić właściwość <xref:System.Windows.Forms.ToolStrip>, <xref:System.Windows.Forms.ToolStripManager>, <xref:System.Windows.Forms.ToolStripPanel>, lub <xref:System.Windows.Forms.ToolStripContentPanel> na `ToolStripRenderer` obiekt i obsłużyć co najmniej jedno z wielu zdarzeń rysowania dostarczonych przez `ToolStripRenderer` Klasa. Alternatywnie `Renderer` można ustawić właściwość na wystąpienie klasy pochodzącej od `ToolStripRenderer`, <xref:System.Windows.Forms.ToolStripProfessionalRenderer>lub <xref:System.Windows.Forms.ToolStripSystemRenderer> implementujące lub zastępujące określone `On`metody *EventName* .  
  
 Aby uzyskać więcej informacji, w tym przykłady kodu, zobacz następujące tematy:  
  
- <xref:System.Windows.Forms.ToolStripRenderer>  
  
- [Instrukcje: Tworzenie i Ustawianie niestandardowego modułu renderowania dla formantu ToolStrip w Windows Forms](create-and-set-a-custom-renderer-for-the-toolstrip-control-in-wf.md)  
  
- [Instrukcje: Niestandardowe Rysowanie kontrolki ToolStrip](how-to-custom-draw-a-toolstrip-control.md)  
  
## <a name="see-also"></a>Zobacz także

- [Kontrolki do użycia w formularzach Windows Forms](controls-to-use-on-windows-forms.md)
