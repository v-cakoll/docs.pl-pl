---
title: Dwukierunkowa obsługa aplikacji Windows Forms
ms.date: 09/30/2017
helpviewer_keywords:
- globalization [Windows Forms], bi-directional support in Windows
- Windows Forms, international
- localization [Windows Forms], bi-directional support in Windows
- bi-directional language support [Windows Forms], Windows applications
- Windows Forms, bi-directional support
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5615ec6125cf622d4d6cd72d219d13be4bd5b096
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69040395"
---
# <a name="bi-directional-support-for-windows-forms-applications"></a>Dwukierunkowa obsługa aplikacji Windows Forms
Program Visual Studio umożliwia tworzenie aplikacji opartych na systemie Windows, które obsługują dwukierunkowe języki (od prawej do lewej), takie jak arabski i hebrajski. Obejmuje to standardowe formularze, okna dialogowe, formularze MDI i wszystkie kontrolki, z którymi można korzystać w tych formularzach — czyli wszystkie obiekty w <xref:System.Windows.Forms.Control> przestrzeni nazw.

## <a name="culture-support"></a>Obsługa kultur
 Ustawienia kultur i kultury interfejsu użytkownika określają, jak działa aplikacja z datami, godzinami, walutą i innymi informacjami. Obsługa kultur i kultury interfejsu użytkownika jest taka sama dla dwukierunkowych języków, jak w przypadku innych języków. Aby uzyskać więcej informacji, zobacz [klasy specyficzne dla kultury dla globalnych formularzy systemu Windows i formularzy sieci Web](/visualstudio/ide/culture-specific-classes-for-global-windows-forms-and-web-forms).

## <a name="righttoleft-and-righttoleftlayout-properties"></a>Właściwości RightToLeft i RightToLeftLayout
 Klasa bazowa <xref:System.Windows.Forms.Control> , z której pochodzą formularze, <xref:System.Windows.Forms.Control.RightToLeft%2A> zawiera właściwość, którą można ustawić, aby zmienić kolejność odczytywania formularza i jego kontrolek. Jeśli ustawisz <xref:System.Windows.Forms.Control.RightToLeft%2A> właściwość formularza, domyślnie kontrolki w formularzu dziedziczą to ustawienie. Można jednak ustawić <xref:System.Windows.Forms.Control.RightToLeft%2A> Właściwość pojedynczo dla większości formantów. Zapoznaj [się również z tematem: Wyświetlanie tekstu od prawej do lewej w Windows Forms na potrzeby globalizacji](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/7d3337xw(v=vs.100)).

 Efekt <xref:System.Windows.Forms.Control.RightToLeft%2A> właściwości może się różnić od jednej kontrolki do innej. W niektórych kontrolkach Właściwość ustawia tylko kolejność odczytywania, jak w <xref:System.Windows.Forms.Button>, <xref:System.Windows.Forms.TreeView> i <xref:System.Windows.Forms.ToolTip> formantów. W innych kontrolkach <xref:System.Windows.Forms.Control.RightToLeft%2A> właściwość zmienia kolejność odczytu i układ. Obejmuje <xref:System.Windows.Forms.RadioButton> to<xref:System.Windows.Forms.ComboBox> i formanty<xref:System.Windows.Forms.CheckBox> . Inne kontrolki wymagają, <xref:System.Windows.Forms.Form.RightToLeftLayout%2A> aby właściwość została zastosowana w celu dublowania jej układu od prawej do lewej. Poniższa tabela zawiera szczegółowe informacje o tym <xref:System.Windows.Forms.Control.RightToLeft%2A> , <xref:System.Windows.Forms.Form.RightToLeftLayout%2A> jak właściwości i wpływają na poszczególne kontrolki Windows Forms.

|Formant/składnik|Efekt właściwości RightToLeft|Efekt właściwości RightToLeftLayout|Wymaga dublowania?|
|------------------------|------------------------------------|------------------------------------------|-------------------------|
|<xref:System.Windows.Forms.Button>|Ustawia kolejność odczytywania od prawej do lewej. <xref:System.Windows.Forms.ButtonBase.TextAlign%2A>Odwraca, i<xref:System.Windows.Forms.ButtonBase.ImageAlign%2A><xref:System.Windows.Forms.ButtonBase.TextImageRelation%2A>|Brak efektu|Nie|
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
|<xref:System.Windows.Forms.GroupBox>|Zostanie wyświetlony napis wyrównany do prawej. Formanty podrzędne mogą dziedziczyć tę właściwość.|<xref:System.Windows.Forms.TableLayoutPanel> Używanie kontrolki do obsługi dublowania od prawej do lewej|Nie|
|<xref:System.Windows.Forms.HScrollBar>|Rozpoczyna się od prawej strony pola przewijania (kciuka)|Brak efektu|Nie|
|<xref:System.Windows.Forms.ImageList>|Niewymagane|Brak efektu|Nie|
|<xref:System.Windows.Forms.Label>|Wyświetlane wyrównane do prawej. <xref:System.Windows.Forms.Label.TextAlign%2A> Odwraca i<xref:System.Windows.Forms.Label.ImageAlign%2A>|Brak efektu|Nie|
|<xref:System.Windows.Forms.LinkLabel>|Wyświetlane wyrównane do prawej. <xref:System.Windows.Forms.Label.TextAlign%2A> Odwraca i<xref:System.Windows.Forms.Label.ImageAlign%2A>|Brak efektu|Nie|
|<xref:System.Windows.Forms.ListBox>|Elementy są wyrównane do prawej|Brak efektu|Nie|
|<xref:System.Windows.Forms.ListView>|Ustawia kolejność odczytu na RTL; elementy pozostają wyrównane do lewej|Odzwierciedla kontrolkę|Tak|
|<xref:System.Windows.Forms.MainMenu>|Wyświetlane wyrównane do prawej kolejność odczytu w czasie wykonywania (nie w czasie projektowania)|Brak efektu|Nie|
|<xref:System.Windows.Forms.MaskedTextBox>|Wyświetla tekst od prawej do lewej.|Brak efektu|Nie|
|<xref:System.Windows.Forms.MonthCalendar>|Nie dotyczy; zależy od języka systemu operacyjnego|Odzwierciedla kontrolkę|Tak|
|<xref:System.Windows.Forms.NotifyIcon>|Nieobsługiwane|Nieobsługiwane|Nie|
|<xref:System.Windows.Forms.NumericUpDown>|Przyciski w górę i w dół są wyrównane do lewej|Brak efektu|Nie|
|<xref:System.Windows.Forms.OpenFileDialog>|W systemach operacyjnych pisanych od prawej do lewej, ustawienie <xref:System.Windows.Forms.Control.RightToLeft> właściwości zawierającej formularz w celu <xref:System.Windows.Forms.RightToLeft.Yes?displayProperty=nameWithType> zlokalizowania okna dialogowego |Brak efektu|Nie|
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
|<xref:System.Windows.Forms.SplitContainer>|Układ panelu jest odwrócony; pionowy pasek przewijania pojawia się po lewej stronie; poziomy pasek przewijania zaczyna się z prawej strony|<xref:System.Windows.Forms.TableLayoutPanel> Użyj do dublowania kolejności formantów podrzędnych|Nie|
|<xref:System.Windows.Forms.Splitter>|Nieobsługiwane|Brak efektu|Nie|
|<xref:System.Windows.Forms.StatusBar>|Nieobsługiwane; Użyj <xref:System.Windows.Forms.StatusStrip> zamiast tego|Brak efektu; Użyj <xref:System.Windows.Forms.StatusStrip> zamiast tego|Nie|
|<xref:System.Windows.Forms.TabControl>|Nie dotyczy tej właściwości|Odzwierciedla kontrolkę|Tak|
|<xref:System.Windows.Forms.TextBox>|Wyświetla tekst od prawej do lewej z kolejnością czytania RTL|Brak efektu|Nie|
|<xref:System.Windows.Forms.Timer>|Niewymagane|Niewymagane|Nie|
|<xref:System.Windows.Forms.ToolBar>|Nie ma to wpływ na tę właściwość; Użyj <xref:System.Windows.Forms.ToolStrip> zamiast tego|Brak efektu; Użyj <xref:System.Windows.Forms.ToolStrip> zamiast tego|Tak|
|<xref:System.Windows.Forms.ToolTip>|Ustawia kolejność odczytywania od prawej do lewej|Brak efektu|Nie|
|<xref:System.Windows.Forms.TrackBar>|Przewijanie lub śledzenie zaczyna się od prawej strony; gdy <xref:System.Windows.Forms.TrackBar.Orientation%2A> jest pionowy, Takty występują od prawej|Brak efektu|Nie|
|<xref:System.Windows.Forms.TreeView>|Ustawia tylko kolejność odczytu RTL|Odzwierciedla kontrolkę|Tak|
|<xref:System.Windows.Forms.UserControl>|Pionowy pasek przewijania pojawia się po lewej stronie; pasek przewijania w poziomie po prawej stronie|Brak bezpośredniej pomocy technicznej; Użyj<xref:System.Windows.Forms.TableLayoutPanel>|Nie|
|<xref:System.Windows.Forms.VScrollBar>|Wyświetlane po lewej stronie zamiast po prawej stronie formantów przewijalnych|Brak efektu|Nie|

## <a name="encoding"></a>Kodowanie
 Windows Forms obsługiwać kod Unicode, dlatego można uwzględnić dowolny zestaw znaków podczas tworzenia aplikacji dwukierunkowych. Jednak nie wszystkie formanty Windows Forms obsługują standard Unicode na wszystkich platformach. Aby uzyskać więcej informacji, zobacz [kodowania i Windows Forms globalizacji](encoding-and-windows-forms-globalization.md).

## <a name="gdi"></a>GDI+
 Można użyć GDI+ do rysowania tekstu z kolejnością czytania od prawej do lewej. Metoda, która jest używana do rysowania tekstu, `StringFormat` obsługuje parametr, który można ustawić <xref:System.Drawing.StringFormatFlags> dla <xref:System.Drawing.StringFormatFlags.DirectionRightToLeft> elementu członkowskiego wyliczenia w celu odwrócenia punktu pochodzenia dla tekstu. <xref:System.Drawing.Graphics.DrawString%2A>

## <a name="common-dialog-boxes"></a>Wspólne okna dialogowe
 Narzędzia systemowe, takie jak okno dialogowe Otwórz plik, są pod kontrolą systemu Windows. Dziedziczą one elementy języka z systemu operacyjnego. W przypadku korzystania z wersji systemu Windows z prawidłowymi ustawieniami języka te okna dialogowe będą działały prawidłowo w językach dwukierunkowych.

 Podobnie pola komunikatów przechodzą przez system operacyjny i obsługują tekst dwukierunkowy. Podpisy na przyciskach okna komunikatu są zależne od bieżącego ustawienia języka. Domyślnie okna komunikatów nie używają kolejności odczytywania od prawej do lewej, ale można określić parametr, aby zmienić kolejność odczytywania, gdy wyświetlane są okna komunikatów.

## <a name="righttoleft-scrollbars-and-scrollablecontrol"></a>RightToLeft, ScrollBars i elementu ScrollableControl
 Obecnie istnieje ograniczenie dotyczące Windows Forms, które uniemożliwiają prawidłowe działanie wszystkich klas <xref:System.Windows.Forms.ScrollableControl> pochodnych od momentu, <xref:System.Windows.Forms.Control.RightToLeft%2A> gdy oba są <xref:System.Windows.Forms.ScrollableControl.AutoScroll%2A> włączone i są <xref:System.Windows.Forms.RightToLeft.Yes>ustawione na. Załóżmy na <xref:System.Windows.Forms.Panel>przykład, że umieszczasz kontrolkę taką jak — lub klasę kontenera <xref:System.Windows.Forms.Panel> pochodną (taką jak <xref:System.Windows.Forms.FlowLayoutPanel> lub <xref:System.Windows.Forms.TableLayoutPanel>) — w formularzu. Jeśli ustawisz <xref:System.Windows.Forms.ScrollableControl.AutoScroll%2A> <xref:System.Windows.Forms.RightToLeft.Yes> kontener na, a następnie ustawisz <xref:System.Windows.Forms.Control.Anchor%2A> właściwość na co najmniej jednej kontrolce wewnątrz kontenera do <xref:System.Windows.Forms.AnchorStyles.Right>, nie pojawi się pasek przewijania. Klasa pochodna <xref:System.Windows.Forms.ScrollableControl> w przypadku, gdy <xref:System.Windows.Forms.ScrollableControl.AutoScroll%2A> zostały ustawione na <xref:System.Windows.Forms.RightToLeft.No>.

 Obecnie jedynym obejściem jest zazagnieżdżanie <xref:System.Windows.Forms.ScrollableControl> wewnątrz innego. <xref:System.Windows.Forms.ScrollableControl> Na przykład, jeśli <xref:System.Windows.Forms.TableLayoutPanel> konieczne jest działanie w tej sytuacji, można umieścić ją wewnątrz <xref:System.Windows.Forms.Panel> <xref:System.Windows.Forms.Panel> kontrolki <xref:System.Windows.Forms.RightToLeft.Yes>i ustawić <xref:System.Windows.Forms.ScrollableControl.AutoScroll%2A> na.

## <a name="mirroring"></a>Tworzenie
 *Dublowanie* odnosi się do odwrócenia układu elementów interfejsu użytkownika, dzięki czemu są one przepływem od prawej do lewej. Na przykład w duplikacie formularza systemu Windows przyciski Minimalizuj, Maksymalizuj i Zamknij są wyświetlane z lewej strony na pasku tytułu, a nie od prawej.

 Ustawienie <xref:System.Windows.Forms.Control.RightToLeft%2A> właściwości formularza lub kontrolki w celu `true` odwrócenia kolejności odczytu elementów w formularzu, ale to ustawienie nie powoduje odwrócenia układu do poziomu od prawej do lewej — nie jest to możliwe. Na przykład ustawienie tej właściwości nie powoduje przeniesienia przycisków **Minimalizuj**, **Maksymalizuj**i **Zamknij** na pasku tytułu formularza do lewej strony formularza. Analogicznie, niektóre kontrolki, takie <xref:System.Windows.Forms.TreeView> jak kontrolka, wymagają dublowania, aby zmiana ich wyświetlania była odpowiednia dla arabskiej lub hebrajskiej. Można dublować te kontrolki przez ustawienie <xref:System.Windows.Forms.Form.RightToLeftLayout%2A> właściwości.

 Można tworzyć zdublowane wersje następujących kontrolek:

- <xref:System.Windows.Forms.ColumnHeader.ListView%2A>

- <xref:System.Windows.Forms.Panel>

- <xref:System.Windows.Forms.StatusBar>

- <xref:System.Windows.Forms.TabControl>

- <xref:System.Windows.Forms.TabPage>

- <xref:System.Windows.Forms.ToolBar>

- <xref:System.Windows.Forms.TreeView>

 Niektóre kontrolki są zapieczętowane. W związku z tym nie można utworzyć z nich nowej kontrolki. Obejmują <xref:System.Windows.Forms.ImageList> one kontrolki <xref:System.Windows.Forms.ProgressBar> i.

## <a name="see-also"></a>Zobacz także

- [Obsługa dwukierunkowych aplikacji sieci Web ASP.NET](https://docs.microsoft.com/previous-versions/aspnet/6eedwbtt(v=vs.100))
- [Globalizacja Windows Forms aplikacji](globalizing-windows-forms.md)
