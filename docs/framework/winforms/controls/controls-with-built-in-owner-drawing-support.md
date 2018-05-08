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
ms.openlocfilehash: a5cbdc733a2f1cda3e708ceaae8604297f8da58a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="controls-with-built-in-owner-drawing-support"></a>Formanty z wbudowaną obsługą rysowania przez właściciela
Rysowanie w formularzach systemu Windows, który jest również nazywany Rysowanie niestandardowe, przez właściciela jest technika Zmienianie wyglądu niektórych formantów.  
  
> [!NOTE]
>  Wyraz "control" w tym temacie służy oznacza klas pochodzących od albo <xref:System.Windows.Forms.Control> lub <xref:System.ComponentModel.Component>.  
  
 Zazwyczaj systemu Windows obsługuje rysowania automatycznie przy użyciu ustawień właściwości, takie jak <xref:System.Windows.Forms.Control.BackColor%2A> ustalenie wyglądu formantu. Bez Rysowanie przez właściciela należy wykonać nad procesem rysowania Zmienianie wyglądu elementów, które nie są dostępne za pomocą właściwości. Na przykład wiele formantów pozwalają na ustawienie kolor tekstu, która jest wyświetlana, ale jest ograniczone do pojedynczego koloru. Rysowanie przez właściciela umożliwia wykonywanie czynności, takich jak wyświetlanie część tekstu w czarne i częściowo w red.  
  
 W praktyce Rysowanie przez właściciela jest podobny do rysowania grafiki na formularzu. Na przykład można użyć metody grafiki w procedurze obsługi w formularzu <xref:System.Windows.Forms.Control.Paint> zdarzeń emulować `ListBox` sterowania, ale musi napisać własny kod do obsługi wszystkich interakcji z użytkownikiem. W przypadku Rysowanie przez właściciela formantu używa kodu do rysowania jego zawartość, ale w przeciwnym razie zachowuje jego możliwości wewnętrznej. Metody grafiki służą do rysowania każdego elementu w formancie lub dostosować niektórych aspektów każdego elementu podczas korzystania z domyślnego wyglądu innych aspektów każdego elementu.  
  
## <a name="owner-drawing-in-windows-forms-controls"></a>Formanty formularzy rysunku właściciela w systemie Windows  
 Aby wykonać właściciela rysowania formantów, które obsługują tę, będzie zwykle ustawić jedną właściwość i obsługi co najmniej jednego zdarzenia.  
  
 Większość formantów Rysowanie przez właściciela tego pomocy technicznej ma `OwnerDraw` lub `DrawMode` właściwość, która wskazuje, czy formant zgłosi jego związane z rysowaniem zdarzenie lub zdarzenia, gdy umożliwia malowanie, sama.  
  
 Formanty, które nie mają `OwnerDraw` lub `DrawMode` obejmują właściwości `DataGridView` kontroli, co zapewnia rysowania zdarzenia, które są wykonywane automatycznie, oraz `ToolStrip` formant, który jest rysowane przy użyciu klasy renderowania zewnętrznego, która ma własną zdarzenia związane z rysowaniem.  
  
 Istnieje wiele różnych rodzajów rysowania zdarzeń, ale występuje typowych zdarzeń rysowania, aby narysować pojedynczego elementu w formancie. Program obsługi zdarzeń odbiera `EventArgs` obiekt, który zawiera informacje o elemencie rysowania i narzędzi można użyć do rysowania. Na przykład ten obiekt zawiera zwykle numer indeksu elementu w obrębie swojej kolekcji nadrzędnej <xref:System.Drawing.Rectangle> który wskazuje element wyświetlany granice i <xref:System.Drawing.Graphics> obiektu do wywoływania metody malowania. W przypadku niektórych zdarzeń `EventArgs` obiektu zawiera dodatkowe informacje na temat elementu, a metody wywołujące namalować niektóre aspekty elementu domyślnie, np. tło lub prostokąt fokusu.  
  
 Aby utworzyć formant wielokrotnego użytku, który zawiera dostosowania rysowanych przez właściciela, Utwórz nową klasę pochodzącą z klasy formantu, który obsługuje Rysowanie przez właściciela. Zamiast Obsługa zdarzeń rysunku, należy uwzględnić swój kod rysowania przez właściciela w odpowiednie zastąpienia `On` *EventName* metod w nowej klasy. Upewnij się, że Wywołaj klasę bazową `On` *EventName* metod, w tym przypadku tak, aby użytkownicy formantu obsługi zdarzenia rysowania przez właściciela i zapewniają dodatkowe możliwości dostosowania.  
  
 Następujące formularzy systemu Windows formanty obsługi Rysowanie przez właściciela we wszystkich wersjach systemu .NET Framework:  
  
-   <xref:System.Windows.Forms.ListBox>  
  
-   <xref:System.Windows.Forms.ComboBox>  
  
-   <xref:System.Windows.Forms.MenuItem> (używane przez <xref:System.Windows.Forms.MainMenu> i <xref:System.Windows.Forms.ContextMenu>)  
  
-   <xref:System.Windows.Forms.TabControl>  
  
 Następujące formanty obsługuje tylko w Rysowanie przez właściciela [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)]:  
  
-   <xref:System.Windows.Forms.ToolTip>  
  
-   <xref:System.Windows.Forms.ListView>  
  
-   <xref:System.Windows.Forms.TreeView>  
  
 Następujące sterowniki obsługują rysowanie przez właściciela i są nowe w [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)]:  
  
-   <xref:System.Windows.Forms.DataGridView>  
  
-   <xref:System.Windows.Forms.ToolStrip>  
  
 Poniższe sekcje zawierają dodatkowe szczegóły dla każdego z tych kontrolek.  
  
### <a name="listbox-and-combobox-controls"></a>Pole listy i formantów ComboBox  
 <xref:System.Windows.Forms.ListBox> i <xref:System.Windows.Forms.ComboBox> formanty umożliwiają rysowanie poszczególnych elementów w formancie wszystko w jednym rozmiaru lub w różnych rozmiarach.  
  
> [!NOTE]
>  Mimo że <xref:System.Windows.Forms.CheckedListBox> kontroli jest pochodną <xref:System.Windows.Forms.ListBox> kontroli, nie obsługuje Rysowanie przez właściciela.  
  
 Aby narysować każdego elementu ten sam rozmiar, ustaw `DrawMode` właściwości <xref:System.Windows.Forms.DrawMode.OwnerDrawFixed> i obsługiwać `DrawItem` zdarzeń.  
  
 Aby narysować każdego elementu przy użyciu innego rozmiaru, ustaw `DrawMode` właściwości <xref:System.Windows.Forms.DrawMode.OwnerDrawVariable> i obsługiwać oba `MeasureItem` i `DrawItem` zdarzenia. `MeasureItem` Zdarzeń umożliwia wskazanie rozmiar elementu przed `DrawItem` zdarzenie dla tego elementu.  
  
 Aby uzyskać więcej informacji, wraz z przykładami kodu zobacz następujące tematy:  
  
-   <xref:System.Windows.Forms.ListBox.DrawMode%2A?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.ListBox.MeasureItem?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.ListBox.DrawItem?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.ComboBox.DrawMode%2A?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.ComboBox.MeasureItem?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.ComboBox.DrawItem?displayProperty=nameWithType>  
  
-   [Instrukcje: tworzenie tekstu o zmiennym rozmiarze w kontrolce ComboBox](../../../../docs/framework/winforms/controls/how-to-create-variable-sized-text-in-a-combobox-control.md)  
  
### <a name="menuitem-component"></a>Składnik MenuItem  
 <xref:System.Windows.Forms.MenuItem> Składnik reprezentuje pojedynczy element menu w <xref:System.Windows.Forms.MainMenu> lub <xref:System.Windows.Forms.ContextMenu> składnika.  
  
 Rysowanie <xref:System.Windows.Forms.MenuItem>, ustaw jej `OwnerDraw` właściwości `true` i obsługiwać jego `DrawItem` zdarzeń. Aby dostosować rozmiar elementu menu przed `DrawItem` wystąpi zdarzenie, obsługi elementu `MeasureItem` zdarzeń.  
  
 Aby uzyskać więcej informacji, wraz z przykładami kodu zobacz następujące tematy odwołania:  
  
-   <xref:System.Windows.Forms.MenuItem.OwnerDraw%2A?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.MenuItem.DrawItem?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.MenuItem.MeasureItem?displayProperty=nameWithType>  
  
### <a name="tabcontrol-control"></a>TabControl — Formant  
 <xref:System.Windows.Forms.TabControl> Kontroli umożliwia rysowanie poszczególnych kart w formancie. Rysowanie przez właściciela dotyczy tylko karty; <xref:System.Windows.Forms.TabPage> nie ma wpływu na zawartość.  
  
 Rysowanie każdej karcie <xref:System.Windows.Forms.TabControl>ustaw `DrawMode` właściwości <xref:System.Windows.Forms.TabDrawMode.OwnerDrawFixed> i obsługiwać `DrawItem` zdarzeń. To zdarzenie wystąpi jeden raz dla każdej karty tylko wtedy, gdy karta jest widoczna w formancie.  
  
 Aby uzyskać więcej informacji, wraz z przykładami kodu zobacz następujące tematy odwołania:  
  
-   <xref:System.Windows.Forms.TabControl.DrawMode%2A?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.TabControl.DrawItem?displayProperty=nameWithType>  
  
### <a name="tooltip-component"></a>ToolTip — Składnik  
 <xref:System.Windows.Forms.ToolTip> Składnika pozwala na pobieranie całego etykietka narzędzia, gdy pojawi się.  
  
 Rysowanie <xref:System.Windows.Forms.ToolTip>, ustaw jej `OwnerDraw` właściwości `true` i obsługiwać jego `Draw` zdarzeń. Aby dostosować rozmiar <xref:System.Windows.Forms.ToolTip> przed `Draw` wystąpi zdarzenie, obsługi `Popup` zdarzeń i zestaw <xref:System.Windows.Forms.PopupEventArgs.ToolTipSize%2A> właściwości w obsłudze zdarzeń.  
  
 Aby uzyskać więcej informacji, wraz z przykładami kodu zobacz następujące tematy odwołania:  
  
-   <xref:System.Windows.Forms.ToolTip.OwnerDraw%2A?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.ToolTip.Draw?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.ToolTip.Popup?displayProperty=nameWithType>  
  
### <a name="listview-control"></a>ListView — Formant  
 <xref:System.Windows.Forms.ListView> Kontroli umożliwia rysowanie poszczególnych elementów podrzędnych i nagłówków kolumn w formancie.  
  
 Aby włączyć Rysowanie w formancie przez właściciela, należy ustawić `OwnerDraw` właściwości `true`.  
  
 Do rysowania każdego elementu w formancie, obsługi `DrawItem` zdarzeń.  
  
 Do rysowania każdego podelementu lub nagłówek kolumny w formancie podczas <xref:System.Windows.Forms.ListView.View%2A> właściwość jest ustawiona na <xref:System.Windows.Forms.View.Details>, obsługi `DrawSubItem` i `DrawColumnHeader` zdarzenia.  
  
 Aby uzyskać więcej informacji, wraz z przykładami kodu zobacz następujące tematy odwołania:  
  
-   <xref:System.Windows.Forms.ListView.OwnerDraw%2A?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.ListView.DrawItem?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.ListView.DrawSubItem?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.ListView.DrawColumnHeader?displayProperty=nameWithType>  
  
### <a name="treeview-control"></a>TreeView — Kontrolka  
 <xref:System.Windows.Forms.TreeView> Kontroli umożliwia rysowanie poszczególne węzły w formancie.  
  
 Aby narysować tylko tekst wyświetlany w każdym węźle, ustaw `DrawMode` właściwości <xref:System.Windows.Forms.TreeViewDrawMode.OwnerDrawText> i obsługiwać `DrawNode` zdarzeń pisania tekstu.  
  
 Aby narysować wszystkie elementy w każdym węźle, ustaw `DrawMode` właściwości <xref:System.Windows.Forms.TreeViewDrawMode.OwnerDrawAll> i obsługiwać `DrawNode` zdarzeń do rysowania niezależnie od elementy wymagane, takie jak tekstu, ikony, pola wyboru, plus lub minus znaków i linie łączące węzły.  
  
 Aby uzyskać więcej informacji, wraz z przykładami kodu zobacz następujące tematy odwołania:  
  
-   <xref:System.Windows.Forms.TreeView.DrawMode%2A?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.TreeView.DrawNode?displayProperty=nameWithType>  
  
### <a name="datagridview-control"></a>DataGridView — Formant  
 <xref:System.Windows.Forms.DataGridView> Kontroli umożliwia rysowanie pojedynczych komórek i wierszy w formancie.  
  
 Rysowanie pojedynczych komórek, obsługi `CellPainting` zdarzeń.  
  
 Rysowanie elementów wierszy lub poszczególnych wierszy, obsługiwać jeden lub oba `RowPrePaint` i `RowPostPaint` zdarzenia. `RowPrePaint` Zdarzenie przed komórek w wierszu są rysowane i `RowPostPaint` zdarzenie po komórki są rysowane. Może obsługiwać obu zdarzeń i `CellPainting` zdarzeń do rysowania tła wiersza, pojedynczych komórek i pierwszego wiersza oddzielnie, lub zapewniają specjalnego dostosowania, gdy potrzebne i użyć domyślnego wiersza innych elementów.  
  
 Aby uzyskać więcej informacji, wraz z przykładami kodu zobacz następujące tematy:  
  
-   <xref:System.Windows.Forms.DataGridView.CellPainting>  
  
-   <xref:System.Windows.Forms.DataGridView.RowPrePaint>  
  
-   <xref:System.Windows.Forms.DataGridView.RowPostPaint>  
  
-   [Instrukcje: dostosowywanie wyglądu komórek w kontrolce DataGridView formularzy Windows Forms](../../../../docs/framework/winforms/controls/customize-the-appearance-of-cells-in-the-datagrid.md)  
  
-   [Instrukcje: dostosowywanie wyglądu wierszy w kontrolce DataGridView formularzy Windows Forms](../../../../docs/framework/winforms/controls/customize-the-appearance-of-rows-in-the-datagrid.md)  
  
### <a name="toolstrip-control"></a>ToolStrip — Formant  
 <xref:System.Windows.Forms.ToolStrip> i formanty pochodne umożliwiają dostosowanie każdego aspektu wyglądu ich.  
  
 Zapewnienie niestandardowe renderowanie <xref:System.Windows.Forms.ToolStrip> formantów, ustaw `Renderer` właściwość <xref:System.Windows.Forms.ToolStrip>, <xref:System.Windows.Forms.ToolStripManager>, <xref:System.Windows.Forms.ToolStripPanel>, lub <xref:System.Windows.Forms.ToolStripContentPanel> do `ToolStripRenderer` obiektu i obsługi co najmniej jedną z wielu zdarzeń rysowania dostarczone przez `ToolStripRenderer` klasy. Możesz również ustawić `Renderer` dla właściwości wystąpienia własne klasy pochodzące z `ToolStripRenderer`, <xref:System.Windows.Forms.ToolStripProfessionalRenderer>, lub <xref:System.Windows.Forms.ToolStripSystemRenderer> implementuje lub przesłania określonych `On` *EventName* metody.  
  
 Aby uzyskać więcej informacji, wraz z przykładami kodu zobacz następujące tematy:  
  
-   <xref:System.Windows.Forms.ToolStripRenderer>  
  
-   [Instrukcje: tworzenie i ustawienie niestandardowego modułu renderowania dla kontrolki ToolStrip w formularzach Windows Forms](../../../../docs/framework/winforms/controls/create-and-set-a-custom-renderer-for-the-toolstrip-control-in-wf.md)  
  
-   [Instrukcje: niestandardowy rysunek kontrolki ToolStrip](../../../../docs/framework/winforms/controls/how-to-custom-draw-a-toolstrip-control.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Kontrolki do użycia w formularzach Windows Forms](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)
