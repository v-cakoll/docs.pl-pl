---
title: Dwukierunkowa obsługa aplikacji Windows Forms
ms.date: 09/30/2017
helpviewer_keywords:
- globalization [Windows Forms], bi-directional support in Windows
- Windows Forms, international
- localization [Windows Forms], bi-directional support in Windows
- bi-directional language support [Windows Forms], Windows applications
- Windows Forms, bi-directional support
ms.openlocfilehash: 3bf90636bf1fc4b20b23c61fdd90033b3da35ddd
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73141198"
---
# <a name="bi-directional-support-for-windows-forms-applications"></a>Dwukierunkowa obsługa aplikacji Windows Forms
Program Visual Studio umożliwia tworzenie aplikacji opartych na systemie Windows, które obsługują dwukierunkowe języki (od prawej do lewej), takie jak arabski i hebrajski. Obejmuje to standardowe formularze, okna dialogowe, formularze MDI i wszystkie kontrolki, z którymi można korzystać w tych formularzach — czyli wszystkie obiekty w przestrzeni nazw <xref:System.Windows.Forms.Control>.

## <a name="culture-support"></a>Obsługa kultur
 Ustawienia kultur i kultury interfejsu użytkownika określają, jak działa aplikacja z datami, godzinami, walutą i innymi informacjami. Obsługa kultur i kultury interfejsu użytkownika jest taka sama dla dwukierunkowych języków, jak w przypadku innych języków. Aby uzyskać więcej informacji, zobacz [klasy specyficzne dla kultury dla globalnych formularzy systemu Windows i formularzy sieci Web](/visualstudio/ide/culture-specific-classes-for-global-windows-forms-and-web-forms).

## <a name="righttoleft-and-righttoleftlayout-properties"></a>Właściwości RightToLeft i RightToLeftLayout
 Klasa bazowa <xref:System.Windows.Forms.Control>, z której pochodzą formularze, zawiera właściwość <xref:System.Windows.Forms.Control.RightToLeft%2A>, którą można ustawić, aby zmienić kolejność odczytywania formularza i jego kontrolek. Jeśli ustawisz właściwość <xref:System.Windows.Forms.Control.RightToLeft%2A> formularza, domyślnie kontrolki w formularzu dziedziczą to ustawienie. Jednak Właściwość <xref:System.Windows.Forms.Control.RightToLeft%2A> można również ustawić indywidualnie dla większości formantów. Zobacz również [instrukcje: wyświetlanie tekstu od prawej do lewej w Windows Forms na potrzeby globalizacji](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/7d3337xw(v=vs.100)).

 Efekt właściwości <xref:System.Windows.Forms.Control.RightToLeft%2A> może się różnić od jednej kontrolki do innej. W niektórych kontrolkach Właściwość ustawia tylko kolejność odczytywania, jak w <xref:System.Windows.Forms.Button>, <xref:System.Windows.Forms.TreeView> i <xref:System.Windows.Forms.ToolTip>. W innych kontrolkach Właściwość <xref:System.Windows.Forms.Control.RightToLeft%2A> zmienia kolejność odczytywania i układ. Obejmuje kontrolki <xref:System.Windows.Forms.RadioButton>, <xref:System.Windows.Forms.ComboBox> i <xref:System.Windows.Forms.CheckBox>. Inne kontrolki wymagają, aby Właściwość <xref:System.Windows.Forms.Form.RightToLeftLayout%2A> była stosowana do dublowania układu od prawej do lewej. Poniższa tabela zawiera szczegółowe informacje na temat tego, jak właściwości <xref:System.Windows.Forms.Control.RightToLeft%2A> i <xref:System.Windows.Forms.Form.RightToLeftLayout%2A> wpływają na poszczególne kontrolki Windows Forms.

|Formant/składnik|Efekt właściwości RightToLeft|Efekt właściwości RightToLeftLayout|Wymaga dublowania?|
|------------------------|------------------------------------|------------------------------------------|-------------------------|
|<xref:System.Windows.Forms.Button>|Ustawia kolejność odczytywania od prawej do lewej. Odwraca <xref:System.Windows.Forms.ButtonBase.TextAlign%2A>, <xref:System.Windows.Forms.ButtonBase.ImageAlign%2A>i <xref:System.Windows.Forms.ButtonBase.TextImageRelation%2A>|Brak efektu|Nie|
|<xref:System.Windows.Forms.CheckBox>|To pole wyboru jest wyświetlane po prawej stronie tekstu|Brak efektu|Nie|
|<xref:System.Windows.Forms.CheckedListBox>|Wszystkie pola wyboru są wyświetlane po prawej stronie tekstu.|Brak efektu|Nie|
|<xref:System.Windows.Forms.ColorDialog>|Nie dotyczy; zależy od języka systemu operacyjnego|Brak efektu|Nie|
|<xref:System.Windows.Forms.ComboBox>|Elementy w kontrolce pole kombi są wyrównane do prawej|Brak efektu|Nie|
|<xref:System.Windows.Forms.ContextMenu>|Pojawia się wyrównane do prawej z kolejnością czytania od lewej|Brak efektu|Nie|
|<xref:System.Windows.Forms.DataGrid>|Pojawia się wyrównane do prawej z kolejnością czytania od lewej|Brak efektu|Nie|
|<xref:System.Windows.Forms.DataGridView>|Wpływa na kolejność odczytywania od prawej do lewej i układ kontroli|Brak efektu|Nie|
|<xref:System.Windows.Forms.DateTimePicker>|Nie dotyczy; zależy od języka systemu operacyjnego|Odzwierciedla kontrolkę|Tak|
|<xref:System.Windows.Forms.DomainUpDown>|Lewy i Wyrównaj przyciski w górę i w dół|Brak efektu|Nie|
|<xref:System.Windows.Forms.ErrorProvider>|Nieobsługiwane|Brak efektu|Nie|
|<xref:System.Windows.Forms.FontDialog>|Zależy od języka systemu operacyjnego|Brak efektu|Nie|
|<xref:System.Windows.Forms.Form>|Ustawia kolejność odczytywania od prawej i odwraca paski przewijania|Odzwierciedla formularz|Tak|
|<xref:System.Windows.Forms.GroupBox>|Zostanie wyświetlony napis wyrównany do prawej. Formanty podrzędne mogą dziedziczyć tę właściwość.|Używanie <xref:System.Windows.Forms.TableLayoutPanel> w formancie do obsługi dublowania od prawej do lewej|Nie|
|<xref:System.Windows.Forms.HScrollBar>|Rozpoczyna się od prawej strony pola przewijania (kciuka)|Brak efektu|Nie|
|<xref:System.Windows.Forms.ImageList>|Niewymagane|Brak efektu|Nie|
|<xref:System.Windows.Forms.Label>|Wyświetlane wyrównane do prawej. Odwraca <xref:System.Windows.Forms.Label.TextAlign%2A> i <xref:System.Windows.Forms.Label.ImageAlign%2A>|Brak efektu|Nie|
|<xref:System.Windows.Forms.LinkLabel>|Wyświetlane wyrównane do prawej. Odwraca <xref:System.Windows.Forms.Label.TextAlign%2A> i <xref:System.Windows.Forms.Label.ImageAlign%2A>|Brak efektu|Nie|
|<xref:System.Windows.Forms.ListBox>|Elementy są wyrównane do prawej|Brak efektu|Nie|
|<xref:System.Windows.Forms.ListView>|Ustawia kolejność odczytu na RTL; elementy pozostają wyrównane do lewej|Odzwierciedla kontrolkę|Tak|
|<xref:System.Windows.Forms.MainMenu>|Wyświetlane wyrównane do prawej kolejność odczytu w czasie wykonywania (nie w czasie projektowania)|Brak efektu|Nie|
|<xref:System.Windows.Forms.MaskedTextBox>|Wyświetla tekst od prawej do lewej.|Brak efektu|Nie|
|<xref:System.Windows.Forms.MonthCalendar>|Nie dotyczy; zależy od języka systemu operacyjnego|Odzwierciedla kontrolkę|Tak|
|<xref:System.Windows.Forms.NotifyIcon>|Nieobsługiwane|Nieobsługiwane|Nie|
|<xref:System.Windows.Forms.NumericUpDown>|Przyciski w górę i w dół są wyrównane do lewej|Brak efektu|Nie|
|<xref:System.Windows.Forms.OpenFileDialog>|W systemach operacyjnych pisanych od prawej do lewej, ustawienie właściwości <xref:System.Windows.Forms.Control.RightToLeft> formularza zawierającej <xref:System.Windows.Forms.RightToLeft.Yes?displayProperty=nameWithType> lokalizuje okno dialogowe |Brak efektu|Nie|
|<xref:System.Windows.Forms.PageSetupDialog>|Nie dotyczy; zależy od języka systemu operacyjnego|Brak efektu|Nie|
|<xref:System.Windows.Forms.Panel>|Formanty podrzędne mogą dziedziczyć tę właściwość|Używanie <xref:System.Windows.Forms.TableLayoutPanel> w formancie do obsługi od prawej do lewej|Tak|
|<xref:System.Windows.Forms.PictureBox>|Nieobsługiwane|Brak efektu|Nie|
|<xref:System.Windows.Forms.PrintDialog>|Nie dotyczy; zależy od języka systemu operacyjnego|Brak efektu|Nie|
|<xref:System.Drawing.Printing.PrintDocument>|Pionowy pasek przewijania staje się wyrównany do lewej, a poziomy pasek przewijania zaczyna się od lewej|Brak efektu|Nie|
|<xref:System.Windows.Forms.PrintPreviewDialog>|Nieobsługiwane|Nieobsługiwane|Nie|
|<xref:System.Windows.Forms.ProgressBar>|Nie dotyczy tej właściwości|Odzwierciedla kontrolkę|Tak|
|<xref:System.Windows.Forms.RadioButton>|Przycisk radiowy jest wyświetlany po prawej stronie tekstu|Brak efektu|Nie|
|<xref:System.Windows.Forms.RichTextBox>|Elementy kontrolne, które zawierają tekst, są wyświetlane od prawej do lewej z kolejnością czytania RTL|Brak efektu|Nie|
|<xref:System.Windows.Forms.SaveFileDialog>|Nie dotyczy; zależy od języka systemu operacyjnego|Brak efektu|Nie|
|<xref:System.Windows.Forms.SplitContainer>|Układ panelu jest odwrócony; pionowy pasek przewijania pojawia się po lewej stronie; poziomy pasek przewijania zaczyna się z prawej strony|Używanie <xref:System.Windows.Forms.TableLayoutPanel> do dublowania kolejności formantów podrzędnych|Nie|
|<xref:System.Windows.Forms.Splitter>|Nieobsługiwane|Brak efektu|Nie|
|<xref:System.Windows.Forms.StatusBar>|Nieobsługiwane; Zamiast tego użyj <xref:System.Windows.Forms.StatusStrip>|Brak efektu; Zamiast tego użyj <xref:System.Windows.Forms.StatusStrip>|Nie|
|<xref:System.Windows.Forms.TabControl>|Nie dotyczy tej właściwości|Odzwierciedla kontrolkę|Tak|
|<xref:System.Windows.Forms.TextBox>|Wyświetla tekst od prawej do lewej z kolejnością czytania RTL|Brak efektu|Nie|
|<xref:System.Windows.Forms.Timer>|Niewymagane|Niewymagane|Nie|
|<xref:System.Windows.Forms.ToolBar>|Nie ma to wpływ na tę właściwość; Zamiast tego użyj <xref:System.Windows.Forms.ToolStrip>|Brak efektu; Zamiast tego użyj <xref:System.Windows.Forms.ToolStrip>|Tak|
|<xref:System.Windows.Forms.ToolTip>|Ustawia kolejność odczytywania od prawej do lewej|Brak efektu|Nie|
|<xref:System.Windows.Forms.TrackBar>|Przewijanie lub śledzenie zaczyna się od prawej strony; gdy <xref:System.Windows.Forms.TrackBar.Orientation%2A> jest pionowy, Takty występują po prawej stronie|Brak efektu|Nie|
|<xref:System.Windows.Forms.TreeView>|Ustawia tylko kolejność odczytu RTL|Odzwierciedla kontrolkę|Tak|
|<xref:System.Windows.Forms.UserControl>|Pionowy pasek przewijania pojawia się po lewej stronie; pasek przewijania w poziomie po prawej stronie|Brak bezpośredniej pomocy technicznej; Użyj <xref:System.Windows.Forms.TableLayoutPanel>|Nie|
|<xref:System.Windows.Forms.VScrollBar>|Wyświetlane po lewej stronie zamiast po prawej stronie formantów przewijalnych|Brak efektu|Nie|

## <a name="encoding"></a>Kody
 Windows Forms obsługiwać kod Unicode, dlatego można uwzględnić dowolny zestaw znaków podczas tworzenia aplikacji dwukierunkowych. Jednak nie wszystkie formanty Windows Forms obsługują standard Unicode na wszystkich platformach.

## <a name="gdi"></a>GDI+
 Można użyć GDI+ do rysowania tekstu z kolejnością czytania od prawej do lewej. Metoda <xref:System.Drawing.Graphics.DrawString%2A>, która jest używana do rysowania tekstu, obsługuje parametr `StringFormat`, który można ustawić dla <xref:System.Drawing.StringFormatFlags.DirectionRightToLeft> elementu członkowskiego wyliczenia <xref:System.Drawing.StringFormatFlags>, aby odwrócić punkt początkowy dla tekstu.

## <a name="common-dialog-boxes"></a>Wspólne okna dialogowe
 Narzędzia systemowe, takie jak okno dialogowe Otwórz plik, są pod kontrolą systemu Windows. Dziedziczą one elementy języka z systemu operacyjnego. W przypadku korzystania z wersji systemu Windows z prawidłowymi ustawieniami języka te okna dialogowe będą działały prawidłowo w językach dwukierunkowych.

 Podobnie pola komunikatów przechodzą przez system operacyjny i obsługują tekst dwukierunkowy. Podpisy na przyciskach okna komunikatu są zależne od bieżącego ustawienia języka. Domyślnie okna komunikatów nie używają kolejności odczytywania od prawej do lewej, ale można określić parametr, aby zmienić kolejność odczytywania, gdy wyświetlane są okna komunikatów.

## <a name="righttoleft-scrollbars-and-scrollablecontrol"></a>RightToLeft, ScrollBars i elementu ScrollableControl
 Obecnie istnieje ograniczenie Windows Forms, które uniemożliwiają prawidłowe działanie wszystkich klas pochodzących od <xref:System.Windows.Forms.ScrollableControl>, gdy jest włączona opcja obydwu <xref:System.Windows.Forms.Control.RightToLeft%2A> i <xref:System.Windows.Forms.ScrollableControl.AutoScroll%2A> jest ustawiona na <xref:System.Windows.Forms.RightToLeft.Yes>. Załóżmy na przykład, że umieszczasz kontrolkę taką jak <xref:System.Windows.Forms.Panel>— lub klasę kontenera pochodną od <xref:System.Windows.Forms.Panel> (na przykład <xref:System.Windows.Forms.FlowLayoutPanel> lub <xref:System.Windows.Forms.TableLayoutPanel>) — w formularzu. Jeśli ustawisz <xref:System.Windows.Forms.ScrollableControl.AutoScroll%2A> w kontenerze do <xref:System.Windows.Forms.RightToLeft.Yes> a następnie ustawisz właściwość <xref:System.Windows.Forms.Control.Anchor%2A> dla co najmniej jednej kontrolki wewnątrz kontenera do <xref:System.Windows.Forms.AnchorStyles.Right>, nie pojawi się pasek przewijania. Klasa pochodna <xref:System.Windows.Forms.ScrollableControl> działa tak, jakby <xref:System.Windows.Forms.ScrollableControl.AutoScroll%2A> zostały ustawione na <xref:System.Windows.Forms.RightToLeft.No>.

 Obecnie jedynym obejściem jest zagnieżdżanie <xref:System.Windows.Forms.ScrollableControl> wewnątrz innego <xref:System.Windows.Forms.ScrollableControl>. Na przykład jeśli potrzebujesz <xref:System.Windows.Forms.TableLayoutPanel> do pracy w tej sytuacji, możesz umieścić ją wewnątrz kontrolki <xref:System.Windows.Forms.Panel> i ustawić <xref:System.Windows.Forms.ScrollableControl.AutoScroll%2A> na <xref:System.Windows.Forms.Panel>, aby <xref:System.Windows.Forms.RightToLeft.Yes>.

## <a name="mirroring"></a>Tworzenie
 *Dublowanie* odnosi się do odwrócenia układu elementów interfejsu użytkownika, dzięki czemu są one przepływem od prawej do lewej. Na przykład w duplikacie formularza systemu Windows przyciski Minimalizuj, Maksymalizuj i Zamknij są wyświetlane z lewej strony na pasku tytułu, a nie od prawej.

 Ustawienie właściwości <xref:System.Windows.Forms.Control.RightToLeft%2A> formularza lub kontrolki w taki sposób, aby `true` odwrócić kolejność odczytywania elementów w formularzu, ale to ustawienie nie powoduje odwrócenia układu do wartości "od prawej do lewej", co oznacza, że nie spowoduje to dublowania. Na przykład ustawienie tej właściwości nie powoduje przeniesienia przycisków **Minimalizuj**, **Maksymalizuj**i **Zamknij** na pasku tytułu formularza do lewej strony formularza. Analogicznie, niektóre kontrolki, takie jak kontrolka <xref:System.Windows.Forms.TreeView>, wymagają dublowania, aby zmiany ich wyświetlania były odpowiednie dla języka arabskiego lub hebrajskiego. Można dublować te kontrolki, ustawiając właściwość <xref:System.Windows.Forms.Form.RightToLeftLayout%2A>.

 Można tworzyć zdublowane wersje następujących kontrolek:

- <xref:System.Windows.Forms.ColumnHeader.ListView%2A>

- <xref:System.Windows.Forms.Panel>

- <xref:System.Windows.Forms.StatusBar>

- <xref:System.Windows.Forms.TabControl>

- <xref:System.Windows.Forms.TabPage>

- <xref:System.Windows.Forms.ToolBar>

- <xref:System.Windows.Forms.TreeView>

 Niektóre kontrolki są zapieczętowane. W związku z tym nie można utworzyć z nich nowej kontrolki. Obejmują one kontrolki <xref:System.Windows.Forms.ImageList> i <xref:System.Windows.Forms.ProgressBar>.

## <a name="see-also"></a>Zobacz także

- [Obsługa dwukierunkowych aplikacji sieci Web ASP.NET](https://docs.microsoft.com/previous-versions/aspnet/6eedwbtt(v=vs.100))
