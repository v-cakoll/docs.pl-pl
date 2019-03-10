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
ms.openlocfilehash: f494d3176d72563a82b50fd5e077917e46045b91
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/09/2019
ms.locfileid: "57712292"
---
# <a name="bi-directional-support-for-windows-forms-applications"></a>Dwukierunkowa obsługa aplikacji Windows Forms
Visual Studio umożliwia tworzenie aplikacji z systemem Windows, które obsługują dwukierunkowej języków (od prawej do lewej), takich jak arabski i hebrajski. W tym standardowych formularzy, okna dialogowe, formularze MDI i wszystkich kontrolek, można pracować w nich — oznacza to, że wszystkie obiekty w <xref:System.Windows.Forms.Control> przestrzeni nazw.  
  
## <a name="culture-support"></a>Obsługa kultury  
 Kultura i ustawienia kultury interfejsu użytkownika można określić za pomocą daty, godziny, waluty i inne informacje, jak działa aplikacja. Obsługa kultury i kultury UI, jest taka sama dla języków dwukierunkowych, podobnie jak w przypadku innych języków. Aby uzyskać więcej informacji, zobacz [klasy, specyficzne dla kultury dla globalnych formularzy Windows i formularzy sieci web](/visualstudio/ide/culture-specific-classes-for-global-windows-forms-and-web-forms).  
  
## <a name="righttoleft-and-righttoleftlayout-properties"></a>RightToLeft i właściwości RightToLeftLayout zostanie zmieniona  
 Podstawa <xref:System.Windows.Forms.Control> zawiera klasy, z którego pochodzi formularzy, <xref:System.Windows.Forms.Control.RightToLeft%2A> właściwości, które można ustawić, aby zmienić kolejność czytania formularza i jej kontrolek. Jeśli ustawisz formularza <xref:System.Windows.Forms.Control.RightToLeft%2A> właściwości domyślne kontrolki na formularzu dziedziczą ustawienie. Jednak możesz również ustawić <xref:System.Windows.Forms.Control.RightToLeft%2A> właściwość indywidualnie dla większości kontrolek. Zobacz też [jak: Wyświetlanie tekstu od prawej do lewej w formularzach Windows Forms dla globalizacji](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/7d3337xw(v=vs.100)).  
  
 Efekt <xref:System.Windows.Forms.Control.RightToLeft%2A> właściwości może się różnić z jednego formantu do drugiego. W niektórych kontrolek właściwość określa tylko kolejność odczytu, podobnie jak w <xref:System.Windows.Forms.Button>, <xref:System.Windows.Forms.TreeView> i <xref:System.Windows.Forms.ToolTip> kontrolki. W innych formantów <xref:System.Windows.Forms.Control.RightToLeft%2A> właściwość zmienia kolejność czytania i układ. Obejmuje to <xref:System.Windows.Forms.RadioButton>, <xref:System.Windows.Forms.ComboBox> i <xref:System.Windows.Forms.CheckBox> kontrolki. Inne formanty wymagającą <xref:System.Windows.Forms.Form.RightToLeftLayout%2A> właściwości można zastosować do utworzenia duplikatów jej układ od prawej do lewej. Poniższa tabela zawiera szczegółowe informacje dotyczące sposobu <xref:System.Windows.Forms.Control.RightToLeft%2A> i <xref:System.Windows.Forms.Form.RightToLeftLayout%2A> właściwości na poszczególnych kontrolek Windows Forms.  
  
|Kontrolka/składnika|Efekt RightToLeft właściwość|Efekt właściwości RightToLeftLayout zostanie zmieniona|Wymaga dublowania?|  
|------------------------|------------------------------------|------------------------------------------|-------------------------|  
|<xref:System.Windows.Forms.Button>|Ustawia RTL kolejność odczytu. Odwraca <xref:System.Windows.Forms.ButtonBase.TextAlign%2A>, <xref:System.Windows.Forms.ButtonBase.ImageAlign%2A>, i <xref:System.Windows.Forms.ButtonBase.TextImageRelation%2A>|Nie wpływu|Nie|  
|<xref:System.Windows.Forms.CheckBox>|Pole wyboru jest wyświetlane po prawej stronie tekstu|Nie wpływu|Nie|  
|<xref:System.Windows.Forms.CheckedListBox>|Wszystkie pola wyboru są wyświetlane po prawej stronie tekstu|Nie wpływu|Nie|  
|<xref:System.Windows.Forms.ColorDialog>|Nie wpływa na; w zależności od języka systemu operacyjnego|Nie wpływu|Nie|  
|<xref:System.Windows.Forms.ComboBox>|Elementy w kontrolce pola kombi są wyrównane do prawej|Nie wpływu|Nie|  
|<xref:System.Windows.Forms.ContextMenu>|Zostanie wyświetlony wyrównany do prawej od prawej do lewej kolejność odczytu|Nie wpływu|Nie|  
|<xref:System.Windows.Forms.DataGrid>|Zostanie wyświetlony wyrównany do prawej od prawej do lewej kolejność odczytu|Nie wpływu|Nie|  
|<xref:System.Windows.Forms.DataGridView>|Dotyczy zarówno od prawej do lewej kolejności i kontrolowania układu do czytania|Nie wpływu|Nie|  
|<xref:System.Windows.Forms.DateTimePicker>|Nie wpływa na; w zależności od języka systemu operacyjnego|Odzwierciedla kontrolki|Tak|  
|<xref:System.Windows.Forms.DomainUpDown>|Lewy wyrównuje w górę i w dół przycisków|Nie wpływu|Nie|  
|<xref:System.Windows.Forms.ErrorProvider>|Nieobsługiwane|Nie wpływu|Nie|  
|<xref:System.Windows.Forms.FontDialog>|W zależności od języka systemu operacyjnego|Nie wpływu|Nie|  
|<xref:System.Windows.Forms.Form>|Ustawia kolejność czytania RTL i odwraca paski przewijania|Formularz odzwierciedla|Tak|  
|<xref:System.Windows.Forms.GroupBox>|Podpis jest wyświetlany, wyrównanie do prawej. Formanty podrzędne mogą dziedziczyć tej właściwości.|Użyj <xref:System.Windows.Forms.TableLayoutPanel> w kontrolce dublowanie od prawej do lewej pomocy technicznej|Nie|  
|<xref:System.Windows.Forms.HScrollBar>|Rozpoczyna się od pola przewijania (thumb) wyrównany do prawej|Nie wpływu|Nie|  
|<xref:System.Windows.Forms.ImageList>|Nie jest wymagane|Nie wpływu|Nie|  
|<xref:System.Windows.Forms.Label>|Wyświetlane wyrównany do prawej. Odwraca <xref:System.Windows.Forms.Label.TextAlign%2A> i <xref:System.Windows.Forms.Label.ImageAlign%2A>|Nie wpływu|Nie|  
|<xref:System.Windows.Forms.LinkLabel>|Wyświetlane wyrównany do prawej. Odwraca <xref:System.Windows.Forms.Label.TextAlign%2A> i <xref:System.Windows.Forms.Label.ImageAlign%2A>|Nie wpływu|Nie|  
|<xref:System.Windows.Forms.ListBox>|Elementy są wyrównane do prawej|Nie wpływu|Nie|  
|<xref:System.Windows.Forms.ListView>|Ustawia kolejność czytania od prawej do lewej; elementy pozostają wyrównane do lewej|Odzwierciedla kontrolki|Tak|  
|<xref:System.Windows.Forms.MainMenu>|Wyświetlana wyrównany do prawej od prawej do lewej kolejność odczytu w czasie wykonywania (nie w czasie projektowania)|Nie wpływu|Nie|  
|<xref:System.Windows.Forms.MaskedTextBox>|Wyświetla tekst od prawej do lewej.|Nie wpływu|Nie|  
|<xref:System.Windows.Forms.MonthCalendar>|Nie wpływa na; w zależności od języka systemu operacyjnego|Odzwierciedla kontrolki|Tak|  
|<xref:System.Windows.Forms.NotifyIcon>|Nieobsługiwane|Nieobsługiwane|Nie|  
|<xref:System.Windows.Forms.NumericUpDown>|Przyciski w górę i w dół są wyrównane do lewej|Nie wpływu|Nie|  
|<xref:System.Windows.Forms.OpenFileDialog>|W systemach operacyjnych od prawej do lewej, ustawienie zawierający formularz <xref:System.Windows.Forms.Control.RightToLeft> właściwość <xref:System.Windows.Forms.RightToLeft.Yes?displayProperty=nameWithType> lokalizuje okna dialogowego |Nie wpływu|Nie|  
|<xref:System.Windows.Forms.PageSetupDialog>|Nie wpływa na; w zależności od języka systemu operacyjnego|Nie wpływu|Nie|  
|<xref:System.Windows.Forms.Panel>|Formanty podrzędne mogą dziedziczyć tę właściwość|Użyj <xref:System.Windows.Forms.TableLayoutPanel> znajdujących się pod kontrolą w prawo do działu pomocy technicznej po lewej stronie|Tak|  
|<xref:System.Windows.Forms.PictureBox>|Nieobsługiwane|Nie wpływu|Nie|  
|<xref:System.Windows.Forms.PrintDialog>|Nie wpływa na; w zależności od języka systemu operacyjnego|Nie wpływu|Nie|  
|<xref:System.Drawing.Printing.PrintDocument>|Stają się wyrównane do lewej pasek przewijania pionowego i poziomego paska przewijania rozpoczyna się od lewej strony|Nie wpływu|Nie|  
|<xref:System.Windows.Forms.PrintPreviewDialog>|Nieobsługiwane|Nieobsługiwane|Nie|  
|<xref:System.Windows.Forms.ProgressBar>|Nie ma wpływu na przez tę właściwość|Odzwierciedla kontrolki|Tak|  
|<xref:System.Windows.Forms.RadioButton>|Przycisk radiowy jest wyświetlany po prawej stronie tekstu|Nie wpływu|Nie|  
|<xref:System.Windows.Forms.RichTextBox>|Elementy kontrolki, które zawierają tekst są wyświetlane od prawej do lewej kolejność czytania od prawej do lewej|Nie wpływu|Nie|  
|<xref:System.Windows.Forms.SaveFileDialog>|Nie wpływa na; w zależności od języka systemu operacyjnego|Nie wpływu|Nie|  
|<xref:System.Windows.Forms.SplitContainer>|Układ panelu została odwrócona; pionowy pasek przewijania jest wyświetlany po lewej stronie; poziomy pasek przewijania rozpoczyna się od prawej strony|Użyj <xref:System.Windows.Forms.TableLayoutPanel> kolejności dublowanie formantów podrzędnych|Nie|  
|<xref:System.Windows.Forms.Splitter>|Nieobsługiwane|Nie wpływu|Nie|  
|<xref:System.Windows.Forms.StatusBar>|Nieobsługiwane. Użyj <xref:System.Windows.Forms.StatusStrip> zamiast tego|Żadnego wpływu; Użyj <xref:System.Windows.Forms.StatusStrip> zamiast tego|Nie|  
|<xref:System.Windows.Forms.TabControl>|Nie dotyczy tej właściwości|Odzwierciedla kontrolki|Tak|  
|<xref:System.Windows.Forms.TextBox>|Wyświetla tekst od prawej do lewej od prawej do lewej kolejność odczytu|Nie wpływu|Nie|  
|<xref:System.Windows.Forms.Timer>|Nie jest wymagane|Nie jest wymagane|Nie|  
|<xref:System.Windows.Forms.ToolBar>|Nie dotyczy tej właściwości; Użyj <xref:System.Windows.Forms.ToolStrip> zamiast tego|Żadnego wpływu; Użyj <xref:System.Windows.Forms.ToolStrip> zamiast tego|Tak|  
|<xref:System.Windows.Forms.ToolTip>|Ustawia RTL kolejność odczytu|Nie wpływu|Nie|  
|<xref:System.Windows.Forms.TrackBar>|Przewijania lub śledzenie rozpoczyna się od prawej; gdy <xref:System.Windows.Forms.TrackBar.Orientation%2A> , jest pionowa impulsów wystąpić z prawej strony|Nie wpływu|Nie|  
|<xref:System.Windows.Forms.TreeView>|Ustawia RTL tylko kolejność odczytu|Odzwierciedla kontrolki|Tak|  
|<xref:System.Windows.Forms.UserControl>|Pionowy pasek przewijania jest wyświetlany po lewej stronie; poziomy pasek przewijania jest thumb po prawej stronie|Brak bezpośredniej obsługi; Użyj <xref:System.Windows.Forms.TableLayoutPanel>|Nie|  
|<xref:System.Windows.Forms.VScrollBar>|Wyświetlane po lewej stronie zamiast po prawej stronie kontrolki przewijany|Nie wpływu|Nie|  
  
## <a name="encoding"></a>Kodowanie  
 Formularze Windows obsługują standardu Unicode, dzięki czemu może zawierać dowolny znak, po utworzeniu aplikacji dwukierunkowej. Jednak nie wszystkie formanty Windows Forms obsługują znaki Unicode na wszystkich platformach. Aby uzyskać więcej informacji, zobacz [kodowanie i globalizacja formularzy Windows](encoding-and-windows-forms-globalization.md).  
  
## <a name="gdi"></a>GDI+  
 Możesz użyć [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] Rysowanie tekstu za pomocą kolejność czytania od prawej do lewej. <xref:System.Drawing.Graphics.DrawString%2A> Obsługuje metodę, która służy do rysowania tekstu, `StringFormat` parametr, który można ustawić <xref:System.Drawing.StringFormatFlags.DirectionRightToLeft> członkiem <xref:System.Drawing.StringFormatFlags> wyliczenie, aby można było odwrócić punkt początkowy dla tekstu.  
  
## <a name="common-dialog-boxes"></a>Wspólne okna dialogowe  
 Narzędzia systemowe, takie jak okno dialogowe Otwieranie pliku będące pod kontrolą systemu Windows. Dziedziczą one elementy języka systemu operacyjnego. Korzystania z wersji systemu Windows przy użyciu ustawień języka tych okien dialogowych za pomocą języków dwukierunkowych będzie działać poprawnie.  
  
 Podobnie komunikatów przechodzą przez system operacyjny i obsługuje tekstu dwukierunkowego. Napisy na przyciskach okno komunikatu opierają się na bieżącym ustawieniem języka. Domyślnie okien komunikatów nie należy używać kolejność czytania od prawej do lewej, ale można określić parametr, aby zmienić kolejność czytania, po wyświetleniu okna komunikatu.  
  
## <a name="righttoleft-scrollbars-and-scrollablecontrol"></a>RightToLeft, paski przewijania i elementu ScrollableControl  
 Obecnie jest to ograniczenie w formularzach Windows, który uniemożliwia wszystkie klasy pochodne od <xref:System.Windows.Forms.ScrollableControl> z działają prawidłowo po obu <xref:System.Windows.Forms.Control.RightToLeft%2A> jest włączona i <xref:System.Windows.Forms.ScrollableControl.AutoScroll%2A> jest ustawiona na <xref:System.Windows.Forms.RightToLeft.Yes>. Na przykład, załóżmy, że takie jak umieścić formant <xref:System.Windows.Forms.Panel>— lub pochodną klasy kontenera <xref:System.Windows.Forms.Panel> (takie jak <xref:System.Windows.Forms.FlowLayoutPanel> lub <xref:System.Windows.Forms.TableLayoutPanel>) — w formularzu. Jeśli ustawisz <xref:System.Windows.Forms.ScrollableControl.AutoScroll%2A> kontenera do <xref:System.Windows.Forms.RightToLeft.Yes> , a następnie ustaw <xref:System.Windows.Forms.Control.Anchor%2A> właściwości jednego lub kilku kontrolek wewnątrz kontenera, na <xref:System.Windows.Forms.AnchorStyles.Right>, a następnie Brak paska przewijania kiedykolwiek pojawia się. Klasa jest pochodną <xref:System.Windows.Forms.ScrollableControl> działa tak, jakby <xref:System.Windows.Forms.ScrollableControl.AutoScroll%2A> ustawiono <xref:System.Windows.Forms.RightToLeft.No>.  
  
 Obecnie jedynym obejściem jest aby zagnieździć <xref:System.Windows.Forms.ScrollableControl> wewnątrz innego <xref:System.Windows.Forms.ScrollableControl>. Na przykład jeśli potrzebujesz <xref:System.Windows.Forms.TableLayoutPanel> pracę w sytuacji, można umieścić go w <xref:System.Windows.Forms.Panel> i ustaw <xref:System.Windows.Forms.ScrollableControl.AutoScroll%2A> na <xref:System.Windows.Forms.Panel> do <xref:System.Windows.Forms.RightToLeft.Yes>.  
  
## <a name="mirroring"></a>Funkcja dublowania  
 *Dublowanie* odwołuje się do cofania układu elementów interfejsu użytkownika, tak aby przepływały od prawej do lewej. W formularzu Windows dublowane dla przykładu, Minimalizuj, Maksymalizuj i zamknij pojawiają się skrajnie po lewej na pasku tytułu, a nie najdalej z prawej strony.  
  
 Ustawienie formularza lub formantu <xref:System.Windows.Forms.Control.RightToLeft%2A> właściwość `true` Odwraca kolejność czytania elementów na formularzu, ale ustawienie to zmieniają układ od prawej do lewej — oznacza to, że nie spowoduje to dublowania. Na przykład ustawienie tej właściwości nie przenosi **Minimalizuj**, **Maksymalizuj**, i **Zamknij** przycisków na pasku tytułu formularza do lewej części formularza. Podobnie, niektóre kontrolki, takie jak <xref:System.Windows.Forms.TreeView> sterowania, wymagają dublowania w celu zmiany ich wyświetlania, aby były odpowiednie dla arabski lub hebrajski. Można dublować tych kontrolek, za pomocą ustawień <xref:System.Windows.Forms.Form.RightToLeftLayout%2A> właściwości.  
  
 Można tworzyć wersje dublowany z następujących formantów:  
  
-   <xref:System.Windows.Forms.ColumnHeader.ListView%2A>  
  
-   <xref:System.Windows.Forms.Panel>  
  
-   <xref:System.Windows.Forms.StatusBar>  
  
-   <xref:System.Windows.Forms.TabControl>  
  
-   <xref:System.Windows.Forms.TabPage>  
  
-   <xref:System.Windows.Forms.ToolBar>  
  
-   <xref:System.Windows.Forms.TreeView>  
  
 Niektóre kontrolki są zamknięte. W związku z tym nie możesz wywodzić nowej kontrolki z nich. Obejmują one <xref:System.Windows.Forms.ImageList> i <xref:System.Windows.Forms.ProgressBar> kontrolki.  
  
## <a name="see-also"></a>Zobacz także

- [Dwukierunkowa obsługa aplikacji sieci Web ASP.NET](https://docs.microsoft.com/previous-versions/aspnet/6eedwbtt(v=vs.100))
- [Globalizowanie aplikacji Windows Forms](globalizing-windows-forms.md)
