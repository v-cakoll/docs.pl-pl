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
ms.openlocfilehash: 1807170b2f5df2333ec3b271a11f9b929c1e7993
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59087186"
---
# <a name="controls-with-built-in-owner-drawing-support"></a>Formanty z wbudowaną obsługą rysowania przez właściciela
Rysowanie w formularzach Windows, który jest znany także jako rysowanie niestandardowe, przez właściciela to technika zmiany wyglądu niektórych kontrolek.  
  
> [!NOTE]
>  Słowo "control", w tym temacie stosuje się do określenia klasy, które wynikają z poziomu <xref:System.Windows.Forms.Control> lub <xref:System.ComponentModel.Component>.  
  
 Zazwyczaj Windows obsługuje malowania automatycznie przy użyciu ustawień właściwości, takie jak <xref:System.Windows.Forms.Control.BackColor%2A> w celu określenia wyglądu formantu. Za pomocą Rysowanie przez właściciela możesz przejąć proces rysowania zmiana elementami wyglądu, które nie są dostępne za pomocą właściwości. Na przykład wiele kontrolek umożliwiają ustawianie koloru tekstu, która jest wyświetlana, ale są ograniczone do pojedynczego koloru. Rysowanie przez właściciela umożliwia wykonywanie takich czynności, jak wyświetlić część tekstu w czarny i części w kolorze czerwonym.  
  
 W praktyce Rysowanie przez właściciela jest podobny do rysowania grafiki w formularzu. Na przykład można użyć metod graficznych w obsłudze w formularzu <xref:System.Windows.Forms.Control.Paint> zdarzenie, aby emulować `ListBox` kontroli, ale musi napisać własny kod do obsługi wszystkich interakcji z użytkownikiem. Za pomocą Rysowanie przez właściciela formant używa kodu, aby narysować jego zawartość, ale w przeciwnym razie zachowuje wszystkie jego funkcje wewnętrzne. Narysuj każdy element w kontrolce lub dostosować niektóre aspekty każdego elementu, a domyślny wygląd innych aspektów każdego elementu, można użyć metody grafiki.  
  
## <a name="owner-drawing-in-windows-forms-controls"></a>Rysowanie właściciela w Windows Forms kontrolek  
 Aby wykonać właściciela rysowania formantów, które go obsługują, będzie zwykle ustawić jedną właściwość i obsługę zdarzeń co najmniej jeden.  
  
 Większość formanty Rysowanie przez właściciela tej pomocy technicznej mają `OwnerDraw` lub `DrawMode` właściwość, która wskazuje, czy kontrolka zgłosi jego zdarzenia związane z rysowaniem lub zdarzenia podczas jego samego do malowania.  
  
 Formanty, które nie mają `OwnerDraw` lub `DrawMode` właściwość zawierać `DataGridView` formant, który udostępnia zdarzenia rysowania, które automatycznie są wykonywane, i `ToolStrip` formant, który jest rysowany przy użyciu klasy renderowania zewnętrznego, który ma swój własny zdarzenia związane z rysowaniem.  
  
 Istnieją różne rodzaje zdarzenia rysowania, ale występuje typowych zdarzeń rysowania, aby narysować pojedynczy element w kontrolce. Program obsługi zdarzeń odbierze `EventArgs` obiekt, który zawiera informacje na temat elementu, rysowania i narzędzi można użyć do rysowania. Na przykład, ten obiekt zawiera zazwyczaj numer indeksu elementu w obrębie swojej kolekcji nadrzędnej <xref:System.Drawing.Rectangle> oznacza, że dla wybranego elementu wyświetlone granice, a <xref:System.Drawing.Graphics> obiekt do wywoływania metod malowania. Niektóre zdarzenia `EventArgs` obiekt zawiera dodatkowe informacje na temat elementu a metody wywołujące do malowania niektóre aspekty elementu domyślnie, np. tło lub prostokąt fokusu.  
  
 Aby utworzyć formant wielokrotnego użytku, który zawiera dostosowania rysowanych przez właściciela, Utwórz nową klasę pochodzącą od klasy kontrolki, która obsługuje Rysowanie przez właściciela. Zamiast obsługi zdarzenia rysowania, należy uwzględnić swój kod rysowania przez właściciela odpowiednie zastąpienia `On` *EventName* metodę lub metody w nowej klasie. Upewnij się, że wywołanie klasy bazowej `On` *EventName* metodę lub metody w tym przypadku tak, aby użytkownicy kontrolki można obsługiwać zdarzenia rysowania przez właściciela i zapewnia dodatkowe możliwości dostosowania.  
  
 Następujące formy Windows kontrolki Rysowanie we wszystkich wersjach programu .NET Framework przez właściciela pomocy technicznej:  
  
-   <xref:System.Windows.Forms.ListBox>  
  
-   <xref:System.Windows.Forms.ComboBox>  
  
-   <xref:System.Windows.Forms.MenuItem> (używane przez <xref:System.Windows.Forms.MainMenu> i <xref:System.Windows.Forms.ContextMenu>)  
  
-   <xref:System.Windows.Forms.TabControl>  
  
 Następujące elementy sterujące obsługuje tylko Rysowanie przez właściciela [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)]:  
  
-   <xref:System.Windows.Forms.ToolTip>  
  
-   <xref:System.Windows.Forms.ListView>  
  
-   <xref:System.Windows.Forms.TreeView>  
  
 Następujące elementy sterujące obsługuje Rysowanie przez właściciela i są nowe w [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)]:  
  
-   <xref:System.Windows.Forms.DataGridView>  
  
-   <xref:System.Windows.Forms.ToolStrip>  
  
 Poniższe sekcje zawierają dodatkowe szczegóły dla każdego z tych kontrolek.  
  
### <a name="listbox-and-combobox-controls"></a>Pola listy i kontrolki ComboBox  
 <xref:System.Windows.Forms.ListBox> i <xref:System.Windows.Forms.ComboBox> formanty umożliwiają narysuj poszczególnych elementów w kontrolce, wszystko w jedno rozwiązanie lub w różnych rozmiarach.  
  
> [!NOTE]
>  Mimo że <xref:System.Windows.Forms.CheckedListBox> kontroli jest tworzony na podstawie <xref:System.Windows.Forms.ListBox> control, nie obsługuje ona Rysowanie przez właściciela.  
  
 Aby narysować każdego elementu w taki sam rozmiar, ustaw `DrawMode` właściwości <xref:System.Windows.Forms.DrawMode.OwnerDrawFixed> i obsługiwać `DrawItem` zdarzeń.  
  
 Aby narysować każdego elementu przy użyciu innego rozmiaru, należy ustawić `DrawMode` właściwości <xref:System.Windows.Forms.DrawMode.OwnerDrawVariable> i obsługiwać oba modele `MeasureItem` i `DrawItem` zdarzenia. `MeasureItem` Zdarzeń umożliwia wskazanie rozmiaru elementu przed `DrawItem` wystąpi zdarzenie dla tego elementu.  
  
 Aby uzyskać więcej informacji, wraz z przykładami kodu zobacz następujące tematy:  
  
-   <xref:System.Windows.Forms.ListBox.DrawMode%2A?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.ListBox.MeasureItem?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.ListBox.DrawItem?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.ComboBox.DrawMode%2A?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.ComboBox.MeasureItem?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.ComboBox.DrawItem?displayProperty=nameWithType>  
  
-   [Instrukcje: Tworzenie tekstu o zmiennym rozmiarze w formancie ComboBox](how-to-create-variable-sized-text-in-a-combobox-control.md)  
  
### <a name="menuitem-component"></a>Składnik element MenuItem  
 <xref:System.Windows.Forms.MenuItem> Składnika reprezentuje pojedynczy element menu w <xref:System.Windows.Forms.MainMenu> lub <xref:System.Windows.Forms.ContextMenu> składnika.  
  
 Aby narysować <xref:System.Windows.Forms.MenuItem>ustaw jego `OwnerDraw` właściwości `true` i obsługiwać jego `DrawItem` zdarzeń. Aby dostosować rozmiar elementu menu przed `DrawItem` wystąpi zdarzenie obsługi elementu `MeasureItem` zdarzeń.  
  
 Aby uzyskać więcej informacji, wraz z przykładami kodu zobacz następujące tematy odniesienia:  
  
-   <xref:System.Windows.Forms.MenuItem.OwnerDraw%2A?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.MenuItem.DrawItem?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.MenuItem.MeasureItem?displayProperty=nameWithType>  
  
### <a name="tabcontrol-control"></a>TabControl — Formant  
 <xref:System.Windows.Forms.TabControl> Control umożliwia rysowanie poszczególnych kart w formancie. Rysowanie przez właściciela ma wpływ na kartach. <xref:System.Windows.Forms.TabPage> nie wpływają na zawartość.  
  
 Aby narysować każda karta w <xref:System.Windows.Forms.TabControl>ustaw `DrawMode` właściwości <xref:System.Windows.Forms.TabDrawMode.OwnerDrawFixed> i obsługiwać `DrawItem` zdarzeń. To zdarzenie występuje jeden raz dla każdej karty, tylko wtedy, gdy karta jest widoczny w kontrolce.  
  
 Aby uzyskać więcej informacji, wraz z przykładami kodu zobacz następujące tematy odniesienia:  
  
-   <xref:System.Windows.Forms.TabControl.DrawMode%2A?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.TabControl.DrawItem?displayProperty=nameWithType>  
  
### <a name="tooltip-component"></a>ToolTip — Składnik  
 <xref:System.Windows.Forms.ToolTip> Składnika umożliwia rysowania całego etykietki narzędzia, gdy jest on wyświetlany.  
  
 Aby narysować <xref:System.Windows.Forms.ToolTip>ustaw jego `OwnerDraw` właściwości `true` i obsługiwać jego `Draw` zdarzeń. Aby dostosować rozmiar <xref:System.Windows.Forms.ToolTip> przed `Draw` wystąpi zdarzenie, obsługi `Popup` zdarzeń i ustaw <xref:System.Windows.Forms.PopupEventArgs.ToolTipSize%2A> właściwość w obsłudze zdarzeń.  
  
 Aby uzyskać więcej informacji, wraz z przykładami kodu zobacz następujące tematy odniesienia:  
  
-   <xref:System.Windows.Forms.ToolTip.OwnerDraw%2A?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.ToolTip.Draw?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.ToolTip.Popup?displayProperty=nameWithType>  
  
### <a name="listview-control"></a>ListView — Formant  
 <xref:System.Windows.Forms.ListView> Control umożliwia rysowanie pojedynczych elementów podrzędnych i nagłówków kolumn w formancie.  
  
 Aby włączyć Rysowanie w kontrolce przez właściciela, ustaw `OwnerDraw` właściwość `true`.  
  
 Aby narysować każdy element w kontrolce, obsługi `DrawItem` zdarzeń.  
  
 Aby narysować każdej podpozycji lub nagłówek kolumny w kontrolce po <xref:System.Windows.Forms.ListView.View%2A> właściwość jest ustawiona na <xref:System.Windows.Forms.View.Details>, obsługi `DrawSubItem` i `DrawColumnHeader` zdarzenia.  
  
 Aby uzyskać więcej informacji, wraz z przykładami kodu zobacz następujące tematy odniesienia:  
  
-   <xref:System.Windows.Forms.ListView.OwnerDraw%2A?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.ListView.DrawItem?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.ListView.DrawSubItem?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.ListView.DrawColumnHeader?displayProperty=nameWithType>  
  
### <a name="treeview-control"></a>TreeView — Formant  
 <xref:System.Windows.Forms.TreeView> Control umożliwia rysowanie poszczególnych węzłów w formancie.  
  
 Aby narysować tylko tekstu wyświetlanego w każdym węźle, należy ustawić `DrawMode` właściwości <xref:System.Windows.Forms.TreeViewDrawMode.OwnerDrawText> i obsługiwać `DrawNode` zdarzenie ma zostać narysowany tekst.  
  
 Aby narysować wszystkie elementy w każdym węźle, należy ustawić `DrawMode` właściwości <xref:System.Windows.Forms.TreeViewDrawMode.OwnerDrawAll> i obsługiwać `DrawNode` zdarzenie, aby rysować elementy, niezależnie od tego potrzebujesz, takie jak tekst, ikony, pola wyboru, plus lub minus znaków i linie, łączenie węzłów.  
  
 Aby uzyskać więcej informacji, wraz z przykładami kodu zobacz następujące tematy odniesienia:  
  
-   <xref:System.Windows.Forms.TreeView.DrawMode%2A?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.TreeView.DrawNode?displayProperty=nameWithType>  
  
### <a name="datagridview-control"></a>DataGridView — Formant  
 <xref:System.Windows.Forms.DataGridView> Control umożliwia rysowanie pojedynczych komórek i wierszy w formancie.  
  
 Aby narysować pojedyncze komórki, obsługi `CellPainting` zdarzeń.  
  
 Aby narysować poszczególne wiersze lub elementy wierszy, obsługiwać jeden lub oba `RowPrePaint` i `RowPostPaint` zdarzenia. `RowPrePaint` Wystąpi zdarzenie przed komórki w wierszu są rysowane i `RowPostPaint` zdarzenie występuje po komórki są rysowane. Może obsługiwać obu zdarzeń i `CellPainting` zdarzenia rysowania tła wiersza, pojedyncze komórki i pierwszego planu wiersz oddzielnie, lub może zapewnić specjalnego dostosowania, w którym ich potrzebują i użyj domyślnego wyświetlania innych elementów wiersza.  
  
 Aby uzyskać więcej informacji, wraz z przykładami kodu zobacz następujące tematy:  
  
-   <xref:System.Windows.Forms.DataGridView.CellPainting>  
  
-   <xref:System.Windows.Forms.DataGridView.RowPrePaint>  
  
-   <xref:System.Windows.Forms.DataGridView.RowPostPaint>  
  
-   [Instrukcje: Dostosowywanie wyglądu komórek w kontrolce DataGridView formularzy Windows Forms](customize-the-appearance-of-cells-in-the-datagrid.md)  
  
-   [Instrukcje: Dostosowywanie wyglądu wierszy w kontrolce DataGridView formularzy Windows Forms](customize-the-appearance-of-rows-in-the-datagrid.md)  
  
### <a name="toolstrip-control"></a>ToolStrip — Formant  
 <xref:System.Windows.Forms.ToolStrip> i formanty pochodne umożliwiają dostosowanie każdego aspektu wyglądu ich.  
  
 Zapewnienie niestandardowe renderowanie <xref:System.Windows.Forms.ToolStrip> formanty, ustawić `Renderer` właściwość <xref:System.Windows.Forms.ToolStrip>, <xref:System.Windows.Forms.ToolStripManager>, <xref:System.Windows.Forms.ToolStripPanel>, lub <xref:System.Windows.Forms.ToolStripContentPanel> do `ToolStripRenderer` obiektu i obsługi co najmniej jeden z wielu zdarzeń rysowania, dostarczone przez `ToolStripRenderer` klasy. Także ustawić `Renderer` właściwości wystąpienia klasy własną pochodną `ToolStripRenderer`, <xref:System.Windows.Forms.ToolStripProfessionalRenderer>, lub <xref:System.Windows.Forms.ToolStripSystemRenderer> , który implementuje lub przesłania określonych `On` *EventName* metody.  
  
 Aby uzyskać więcej informacji, wraz z przykładami kodu zobacz następujące tematy:  
  
-   <xref:System.Windows.Forms.ToolStripRenderer>  
  
-   [Instrukcje: Tworzenie i ustawienie niestandardowego modułu renderowania dla formantu ToolStrip w formularzach Windows Forms](create-and-set-a-custom-renderer-for-the-toolstrip-control-in-wf.md)  
  
-   [Instrukcje: Rysowanie niestandardowego formantu ToolStrip](how-to-custom-draw-a-toolstrip-control.md)  
  
## <a name="see-also"></a>Zobacz także

- [Kontrolki do użycia w formularzach Windows Forms](controls-to-use-on-windows-forms.md)
