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
ms.openlocfilehash: fe1a15477e858a77ee7829f1d4a9d052457cd30f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="bi-directional-support-for-windows-forms-applications"></a>Dwukierunkowa obsługa aplikacji Windows Forms
Visual Studio służy do tworzenia aplikacji opartych na systemie Windows, które obsługują dwukierunkowego (od prawej do lewej) języków, takich jak arabski i hebrajski. Obejmuje to standardowych formularzy, okien dialogowych, formularze MDI i wszystkie formanty można pracować w nich — to znaczy, że wszystkie obiekty w <xref:System.Windows.Forms.Control> przestrzeni nazw.  
  
## <a name="culture-support"></a>Obsługa kultury  
 Culture i ustawienia kultury interfejsu użytkownika należy ustalić, jak aplikacja działa z daty, godziny, waluty i inne informacje. Obsługa kultury i kultury interfejsu użytkownika jest taka sama dla języków dwukierunkowych, podobnie jak w przypadku innych języków.   Zobacz też [klasy specyficzne dla kultury dla globalnych formularzy systemu Windows i formularzy sieci Web](http://msdn.microsoft.com/library/94ye9x8c\(v=vs.110\)) lub [klasy specyficzne dla kultury dla globalnych formularzy systemu Windows i formularzy sieci Web](http://msdn.microsoft.com/library/94ye9x8c\(v=vs.120\))  
  
## <a name="righttoleft-and-righttoleftlayout-properties"></a>RightToLeft i właściwości RightToLeftLayout zostanie zmieniona  
 Podstawowym <xref:System.Windows.Forms.Control> zawiera klasy, z którego pochodzi formularzy, <xref:System.Windows.Forms.Control.RightToLeft%2A> właściwości, które można ustawić, aby zmienić kolejność odczytu formularza i jego formantów. Jeśli ustawisz formularza <xref:System.Windows.Forms.Control.RightToLeft%2A> właściwość przez domyślny kontrolek w formularzu dziedziczy to ustawienie. Jednak można również ustawić <xref:System.Windows.Forms.Control.RightToLeft%2A> właściwości indywidualnie dla większości kontrolek. Zobacz też [porady: Tekst wyświetlania od prawej do lewej w formularzach systemu Windows dla globalizacji](http://msdn.microsoft.com/library/7d3337xw\(v=vs.110\)).  
  
 Efekt <xref:System.Windows.Forms.Control.RightToLeft%2A> właściwości może się różnić od jeden formant do innego. W niektórych formantów właściwość określa tylko kolejność czytania, podobnie jak w <xref:System.Windows.Forms.Button>, <xref:System.Windows.Forms.TreeView> i <xref:System.Windows.Forms.ToolTip> kontrolki. W innych kontrolek <xref:System.Windows.Forms.Control.RightToLeft%2A> zarówno kolejność czytania, jak i układ zmiany właściwości. Obejmuje to <xref:System.Windows.Forms.RadioButton>, <xref:System.Windows.Forms.ComboBox> i <xref:System.Windows.Forms.CheckBox> kontrolki. Inne formanty wymagają, aby <xref:System.Windows.Forms.Form.RightToLeftLayout%2A> właściwości można zastosować do duplikatów jego układ od prawej do lewej. W poniższej tabeli przedstawiono szczegółowe informacje, w jaki sposób <xref:System.Windows.Forms.Control.RightToLeft%2A> i <xref:System.Windows.Forms.Form.RightToLeftLayout%2A> właściwości na pojedynczych formantów formularzy systemu Windows.  
  
|Formant/składnika|Efekt właściwość RightToLeft|Efekt właściwości RightToLeftLayout zostanie zmieniona|Wymaga dublowania?|  
|------------------------|------------------------------------|------------------------------------------|-------------------------|  
|<xref:System.Windows.Forms.Button>|Ustawia RTL kolejność odczytu. Odwraca <xref:System.Windows.Forms.ButtonBase.TextAlign%2A>, <xref:System.Windows.Forms.ButtonBase.ImageAlign%2A>, i <xref:System.Windows.Forms.ButtonBase.TextImageRelation%2A>|Nie działa|Nie|  
|<xref:System.Windows.Forms.CheckBox>|Pole wyboru jest wyświetlane po prawej stronie tekstu|Nie działa|Nie|  
|<xref:System.Windows.Forms.CheckedListBox>|Wszystkie pola wyboru są wyświetlane po prawej stronie tekstu|Nie działa|Nie|  
|<xref:System.Windows.Forms.ColorDialog>|Nie dotyczy to; zależy od języka systemu operacyjnego|Nie działa|Nie|  
|<xref:System.Windows.Forms.ComboBox>|Elementy kontrolki pola kombi są wyrównane do lewej|Nie działa|Nie|  
|<xref:System.Windows.Forms.ContextMenu>|Zostanie wyświetlone wyrównany z RTL kolejność czytania|Nie działa|Nie|  
|<xref:System.Windows.Forms.DataGrid>|Zostanie wyświetlone wyrównany z RTL kolejność czytania|Nie działa|Nie|  
|<xref:System.Windows.Forms.DataGridView>|Dotyczy zarówno od prawej do lewej układ kolejności i kontroli do czytania|Nie działa|Nie|  
|<xref:System.Windows.Forms.DateTimePicker>|Nie dotyczy to; zależy od języka systemu operacyjnego|Odzwierciedla formantu|Tak|  
|<xref:System.Windows.Forms.DomainUpDown>|Po lewej Wyrównuje górę i w dół przycisków|Nie działa|Nie|  
|<xref:System.Windows.Forms.ErrorProvider>|Nieobsługiwane|Nie działa|Nie|  
|<xref:System.Windows.Forms.FontDialog>|Zależy od języka systemu operacyjnego|Nie działa|Nie|  
|<xref:System.Windows.Forms.Form>|Ustawia kolejność czytania RTL i odwraca paski przewijania|Odzwierciedla formularza|Tak|  
|<xref:System.Windows.Forms.GroupBox>|Podpis jest wyświetlany w prawej. Formanty podrzędne mogą dziedziczyć tej właściwości.|Użyj <xref:System.Windows.Forms.TableLayoutPanel> w formancie dublowania od prawej do lewej obsługuje|Nie|  
|<xref:System.Windows.Forms.HScrollBar>|Rozpoczyna się wyrównany do prawej strony pola przewijania (przenośny)|Nie działa|Nie|  
|<xref:System.Windows.Forms.ImageList>|Niewymagane|Nie działa|Nie|  
|<xref:System.Windows.Forms.Label>|Wyświetlane wyrównany do prawej. Odwraca <xref:System.Windows.Forms.Label.TextAlign%2A> i <xref:System.Windows.Forms.Label.ImageAlign%2A>|Nie działa|Nie|  
|<xref:System.Windows.Forms.LinkLabel>|Wyświetlane wyrównany do prawej. Odwraca <xref:System.Windows.Forms.Label.TextAlign%2A> i <xref:System.Windows.Forms.Label.ImageAlign%2A>|Nie działa|Nie|  
|<xref:System.Windows.Forms.ListBox>|Elementy są wyrównane do lewej|Nie działa|Nie|  
|<xref:System.Windows.Forms.ListView>|Ustawia kolejność czytania od prawej do lewej; elementy pozostają wyrównane do lewej|Odzwierciedla formantu|Tak|  
|<xref:System.Windows.Forms.MainMenu>|Wyświetlane wyrównany z RTL kolejność czytania w czasie wykonywania (nie w czasie projektowania)|Nie działa|Nie|  
|<xref:System.Windows.Forms.MaskedTextBox>|Wyświetla tekst od prawej do lewej.|Nie działa|Nie|  
|<xref:System.Windows.Forms.MonthCalendar>|Nie dotyczy to; zależy od języka systemu operacyjnego|Odzwierciedla formantu|Tak|  
|<xref:System.Windows.Forms.NotifyIcon>|Nieobsługiwane|Nieobsługiwane|Nie|  
|<xref:System.Windows.Forms.NumericUpDown>|Przyciski w górę i w dół są wyrównane do lewej|Nie działa|Nie|  
|<xref:System.Windows.Forms.OpenFileDialog>|W systemach operacyjnych od prawej do lewej, ustawienie zawierający formularz <xref:System.Windows.Forms.Control.RightToLeft> właściwości <xref:System.Windows.Forms.RightToLeft.Yes?displayProperty=nameWithType> lokalizuje okna dialogowego |Nie działa|Nie|  
|<xref:System.Windows.Forms.PageSetupDialog>|Nie dotyczy to; zależy od języka systemu operacyjnego|Nie działa|Nie|  
|<xref:System.Windows.Forms.Panel>|Formanty podrzędne mogą dziedziczyć tej właściwości|Użyj <xref:System.Windows.Forms.TableLayoutPanel> wewnątrz formantu dla prawej do lewej pomocy technicznej|Tak|  
|<xref:System.Windows.Forms.PictureBox>|Nieobsługiwane|Nie działa|Nie|  
|<xref:System.Windows.Forms.PrintDialog>|Nie dotyczy to; zależy od języka systemu operacyjnego|Nie działa|Nie|  
|<xref:System.Drawing.Printing.PrintDocument>|Pionowy pasek przewijania stają się wyrównane do lewej i poziomy pasek przewijania rozpoczyna się od lewej|Nie działa|Nie|  
|<xref:System.Windows.Forms.PrintPreviewDialog>|Nieobsługiwane|Nieobsługiwane|Nie|  
|<xref:System.Windows.Forms.ProgressBar>|Nie ma wpływu na przez tę właściwość|Odzwierciedla formantu|Tak|  
|<xref:System.Windows.Forms.RadioButton>|Przycisk radiowy jest wyświetlana po prawej stronie tekstu|Nie działa|Nie|  
|<xref:System.Windows.Forms.RichTextBox>|Elementy kontroli, które zawierają tekst są wyświetlane od prawej do lewej kolejność czytania od prawej do lewej|Nie działa|Nie|  
|<xref:System.Windows.Forms.SaveFileDialog>|Nie dotyczy to; zależy od języka systemu operacyjnego|Nie działa|Nie|  
|<xref:System.Windows.Forms.SplitContainer>|Układ panelu została odwrócona; pionowy pasek przewijania pojawia się po lewej stronie; poziomy pasek przewijania rozpoczyna się od prawej strony|Użyj <xref:System.Windows.Forms.TableLayoutPanel> w kolejności formanty podrzędne dublowania|Nie|  
|<xref:System.Windows.Forms.Splitter>|Nieobsługiwane|Nie działa|Nie|  
|<xref:System.Windows.Forms.StatusBar>|Nieobsługiwane. Użyj <xref:System.Windows.Forms.StatusStrip> zamiast niego|Żadnego wpływu; Użyj <xref:System.Windows.Forms.StatusStrip> zamiast niego|Nie|  
|<xref:System.Windows.Forms.TabControl>|Nie dotyczy tej właściwości|Odzwierciedla formantu|Tak|  
|<xref:System.Windows.Forms.TextBox>|Wyświetla tekst od prawej do lewej z RTL kolejność czytania|Nie działa|Nie|  
|<xref:System.Windows.Forms.Timer>|Niewymagane|Niewymagane|Nie|  
|<xref:System.Windows.Forms.ToolBar>|Nie dotyczy tej właściwości; Użyj <xref:System.Windows.Forms.ToolStrip> zamiast niego|Żadnego wpływu; Użyj <xref:System.Windows.Forms.ToolStrip> zamiast niego|Tak|  
|<xref:System.Windows.Forms.ToolTip>|Ustawia RTL kolejność czytania|Nie działa|Nie|  
|<xref:System.Windows.Forms.TrackBar>|Przewijania lub ścieżkę rozpoczyna się od prawej; gdy <xref:System.Windows.Forms.TrackBar.Orientation%2A> jest pionowy, wystąpić znaczniki osi po prawej stronie|Nie działa|Nie|  
|<xref:System.Windows.Forms.TreeView>|Ustawia RTL tylko kolejność czytania|Odzwierciedla formantu|Tak|  
|<xref:System.Windows.Forms.UserControl>|Pionowy pasek przewijania pojawia się po lewej stronie; poziomy pasek przewijania ma przycisku przewijania w prawo|Nie obsługuje bezpośredniego; Użyj <xref:System.Windows.Forms.TableLayoutPanel>|Nie|  
|<xref:System.Windows.Forms.VScrollBar>|Wyświetlane po lewej stronie zamiast po prawej stronie przewijanego formantów|Nie działa|Nie|  
  
## <a name="encoding"></a>Kodowanie  
 Formularze systemu Windows obsługują standardu Unicode, więc może zawierać znaków po utworzeniu aplikacji dwukierunkowych. Jednak nie wszystkie formanty formularzy systemu Windows obsługują standardu Unicode na wszystkich platformach. Aby uzyskać więcej informacji, zobacz [kodowanie i globalizacja formularzy systemu Windows](../../../../docs/framework/winforms/advanced/encoding-and-windows-forms-globalization.md).  
  
## <a name="gdi"></a>GDI+  
 Można użyć [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] Rysowanie tekstu w kolejności odczytywania od prawej do lewej. <xref:System.Drawing.Graphics.DrawString%2A> Obsługuje metodę, która jest używany do rysowania tekstu, `StringFormat` parametr, który można ustawić <xref:System.Drawing.StringFormatFlags.DirectionRightToLeft> członkiem <xref:System.Drawing.StringFormatFlags> wyliczenia, aby odwrócić punkt początkowy dla tekstu.  
  
## <a name="common-dialog-boxes"></a>Wspólne okna dialogowe  
 Narzędzia systemowe, takie jak okno dialogowe Otwieranie pliku są pod kontrolą systemu Windows. Elementy języka dziedziczą z systemu operacyjnego. Jeśli używasz wersji systemu Windows przy użyciu ustawień języka, tych okien dialogowych będzie działać poprawnie w językach dwukierunkowych.  
  
 Podobnie komunikatów przejść przez system operacyjny i obsługuje tekstu dwukierunkowego. Podpisy na przyciskach pola wiadomości są oparte na bieżącym ustawieniem języka. Domyślnie pola wiadomości nie używaj kolejność czytania od prawej do lewej, ale można określić parametr, aby zmienić kolejność czytania, gdy są wyświetlane pola wiadomości.  
  
## <a name="righttoleft-scrollbars-and-scrollablecontrol"></a>RightToLeft pasków przewijania i elementu ScrollableControl  
 Obecnie jest to ograniczenie w formularzach systemu Windows, który uniemożliwia wszystkie klasy wywodzące się z <xref:System.Windows.Forms.ScrollableControl> z działa prawidłowo po obu <xref:System.Windows.Forms.Control.RightToLeft%2A> jest włączona i <xref:System.Windows.Forms.ScrollableControl.AutoScroll%2A> ma ustawioną wartość <xref:System.Windows.Forms.RightToLeft.Yes>. Na przykład, załóżmy, że takie jak Umieść formant <xref:System.Windows.Forms.Panel>— lub kontener klasą pochodną <xref:System.Windows.Forms.Panel> (takich jak <xref:System.Windows.Forms.FlowLayoutPanel> lub <xref:System.Windows.Forms.TableLayoutPanel>) — w formularzu. Jeśli ustawisz <xref:System.Windows.Forms.ScrollableControl.AutoScroll%2A> w kontenerze na <xref:System.Windows.Forms.RightToLeft.Yes> , a następnie ustaw <xref:System.Windows.Forms.Control.Anchor%2A> właściwości na co najmniej jedna z kontrolek w kontenerze na <xref:System.Windows.Forms.AnchorStyles.Right>, następnie kiedykolwiek pojawia się nie pasek przewijania. Klasy pochodne <xref:System.Windows.Forms.ScrollableControl> zachowuje się tak, jakby <xref:System.Windows.Forms.ScrollableControl.AutoScroll%2A> ustawiono <xref:System.Windows.Forms.RightToLeft.No>.  
  
 Obecnie jest tylko obejście Aby zagnieździć <xref:System.Windows.Forms.ScrollableControl> wewnątrz innego <xref:System.Windows.Forms.ScrollableControl>. Na przykład jeśli potrzebujesz <xref:System.Windows.Forms.TableLayoutPanel> do pracy w takiej sytuacji należy umieścić go w <xref:System.Windows.Forms.Panel> kontroli oraz ustawić <xref:System.Windows.Forms.ScrollableControl.AutoScroll%2A> na <xref:System.Windows.Forms.Panel> do <xref:System.Windows.Forms.RightToLeft.Yes>.  
  
## <a name="mirroring"></a>Funkcja dublowania  
 *Dublowanie* odwołuje się do cofania układ elementów interfejsu użytkownika, tak aby ich przepływać od prawej do lewej. W dublowanych formularza systemu Windows na przykład Minimalizuj, Maksymalizuj i zamknij przyciski wyświetlane lewej na pasku tytułu nie prawej krawędzi.  
  
 Ustawienie formularza lub kontrolki <xref:System.Windows.Forms.Control.RightToLeft%2A> właściwości `true` Odwraca kolejność czytania elementów na formularzu, ale ustawienie to nie wstecznego układu się od prawej do lewej — to znaczy, że nie spowoduje to dublowania. Na przykład ustawienie dla tej właściwości nie przenosi **Minimalizuj**, **Maksymalizuj**, i **Zamknij** przycisków na pasku tytułu formularza po lewej stronie formularza. Podobnie, niektóre formanty, takie jak <xref:System.Windows.Forms.TreeView> kontrolować, wymagają dublowania, aby zmienić sposób ich wyświetlania odpowiednio dla arabskiego lub hebrajski. Formanty te ustawienia mogą być dublowane <xref:System.Windows.Forms.Form.RightToLeftLayout%2A> właściwości.  
  
 Można tworzyć dublowanego wersje następujące sterowniki:  
  
-   <xref:System.Windows.Forms.ColumnHeader.ListView%2A>  
  
-   <xref:System.Windows.Forms.Panel>  
  
-   <xref:System.Windows.Forms.StatusBar>  
  
-   <xref:System.Windows.Forms.TabControl>  
  
-   <xref:System.Windows.Forms.TabPage>  
  
-   <xref:System.Windows.Forms.ToolBar>  
  
-   <xref:System.Windows.Forms.TreeView>  
  
 Niektóre kontrolki są zapieczętowane. W związku z tym nie może pochodzić nową kontrolkę z nich. Obejmują one <xref:System.Windows.Forms.ImageList> i <xref:System.Windows.Forms.ProgressBar> kontrolki.  
  
## <a name="see-also"></a>Zobacz też  
 [Dwukierunkowa obsługa aplikacji sieci Web ASP.NET](http://msdn.microsoft.com/library/5576f9b1-9b86-41ef-8354-092d366bcd03)  
 [Globalizacja formularzy Windows Forms](../../../../docs/framework/winforms/advanced/globalizing-windows-forms.md)
