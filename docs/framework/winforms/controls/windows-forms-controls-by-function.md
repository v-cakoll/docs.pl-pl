---
title: Formanty formularzy systemu Windows według funkcji
ms.date: 03/30/2017
helpviewer_keywords:
- controls [Windows Forms], by function
- Windows Forms, controls by function
- Windows Forms controls, list of
ms.assetid: 5e65a6c3-5d6f-480d-beb8-b28f865f07e3
ms.openlocfilehash: 058a18878b89991bd8124bd69e18476d4f1479d6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="windows-forms-controls-by-function"></a>Formanty formularzy systemu Windows według funkcji
Formularze systemu Windows oferuje kontrolek i składników, które wykonują wiele funkcji. W poniższej tabeli wymieniono formanty formularzy systemu Windows i składniki według funkcji ogólne. Ponadto w przypadku, gdy wiele istnieją środki zapobiegawcze, które pełnią taką samą funkcję, zalecane formant znajduje się uwagi dotyczące kontroli, którą on zastąpiony. W osobnej tabeli kolejnych formantów zastąpione są wyświetlane z ich zalecane zamiany.  
  
> [!NOTE]
>  W poniższych tabelach przedstawiono nie, co formant lub składnik, który można używać w formularzach systemu Windows; Aby bardziej pełną listę, zobacz [formanty do użycia w formularzach systemu Windows](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)  
  
## <a name="recommended-controls-and-components-by-function"></a>Zalecane formanty i składniki według funkcji  
  
|Funkcja|Formant|Opis|  
|--------------|-------------|-----------------|  
|Wyświetlanie danych|<xref:System.Windows.Forms.DataGridView> Formant|<xref:System.Windows.Forms.DataGridView> Formant zawiera tabelę można dostosować do wyświetlania danych. <xref:System.Windows.Forms.DataGridView> Klasa umożliwia dostosowywanie komórek, wierszy, kolumny i obramowania. **Uwaga:** <xref:System.Windows.Forms.DataGridView> kontrola zapewnia wiele podstawowych i zaawansowanych funkcji, które nie występują w <xref:System.Windows.Forms.DataGrid> formantu. Aby uzyskać więcej informacji, zobacz [różnice między Windows Forms formantami DataGridView i DataGrid](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md)|  
|Powiązanie danych i nawigacji|<xref:System.Windows.Forms.BindingSource> Składnik|Ułatwia powiązanie formantów w formularzu do danych, zapewniając zarządzania waluty, powiadomienia o zmianie i innych usług.|  
||<xref:System.Windows.Forms.BindingNavigator> Formant|Udostępnia interfejs typ paska narzędzi do nawigacji i manipulacji danymi na formularzu.|  
|Edytowanie tekstu|<xref:System.Windows.Forms.TextBox> Formant|Wyświetla tekst wprowadzony w czasie projektowania, który można edytowane przez użytkowników w czasie wykonywania, lub programistycznej zmiany.|  
||<xref:System.Windows.Forms.RichTextBox> Formant|Umożliwia tekst, który ma być wyświetlane z formatowaniem w postaci zwykłego tekstu lub format tekstu sformatowanego (RTF).|  
||<xref:System.Windows.Forms.MaskedTextBox> Formant|Ogranicza format danych wejściowych użytkownika|  
|Wyświetlane informacje (tylko do odczytu)|<xref:System.Windows.Forms.Label> Formant|Wyświetlany tekst, który użytkownicy nie mogą bezpośrednio edytować.|  
||<xref:System.Windows.Forms.LinkLabel> Formant|Tekst jest wyświetlany jako łącze stylu sieci Web i wyzwala zdarzenie, gdy użytkownik kliknie specjalne tekstu. Tekst jest zwykle łącza do innego okna lub witryny sieci Web.|  
||<xref:System.Windows.Forms.StatusStrip> Formant|Wyświetla informacje o bieżącym stanie aplikacji przy użyciu obszaru ramce, zazwyczaj w dolnej części formularza nadrzędnego.|  
||<xref:System.Windows.Forms.ProgressBar> Formant|Wyświetla bieżący postęp operacji dla użytkownika.|  
|Wyświetlanie strony sieci Web|<xref:System.Windows.Forms.WebBrowser> Formant|Umożliwia użytkownikowi nawigację strony sieci Web wewnątrz formularza.|  
|Wybór z listy|<xref:System.Windows.Forms.CheckedListBox> Formant|Zawiera listę elementów, każdy wraz z polem wyboru.|  
||<xref:System.Windows.Forms.ComboBox> Formant|Wyświetla listę elementów listy rozwijanej.|  
||<xref:System.Windows.Forms.DomainUpDown> Formant|Wyświetla listę elementów tekstowych, które użytkownicy mogą przewijać z przycisków w górę i w dół.|  
||<xref:System.Windows.Forms.ListBox> Formant|Wyświetla listę tekstu i elementów graficznych (ikony).|  
||<xref:System.Windows.Forms.ListView> Formant|Wyświetla elementy w jednej z czterech różnych widoków. Widoki obejmują tylko tekst, tekst na małe ikony tekstu w dużych ikon i widoku szczegółów.|  
||<xref:System.Windows.Forms.NumericUpDown> Formant|Wyświetla listę liczb, które użytkownicy mogą przewijać z przycisków w górę i w dół.|  
||<xref:System.Windows.Forms.TreeView> Formant|Wyświetla użytkownikowi hierarchiczną kolekcję obiektów węzła, które może składać się z pomocą opcjonalne pola wyboru lub ikony.|  
|Wyświetlanie grafiki|<xref:System.Windows.Forms.PictureBox> Formant|Wyświetla graficzny plików, takich jak mapy bitowe i ikony w ramce.|  
|Magazyn grafiki|<xref:System.Windows.Forms.ImageList> Formant|Służy jako repozytorium obrazów. <xref:System.Windows.Forms.ImageList> Formanty i obrazów, które zawierają mogą być ponownie używane z jednej aplikacji do następnego.|  
|Ustawienie wartości|<xref:System.Windows.Forms.CheckBox> Formant|Wyświetla pole wyboru i etykietę dla tekstu. Zazwyczaj używany do ustawiania opcji.|  
||<xref:System.Windows.Forms.CheckedListBox> Formant|Zawiera listę elementów, każdy wraz z polem wyboru.|  
||<xref:System.Windows.Forms.RadioButton> Formant|Wyświetla przycisku, który może być włączony lub wyłączony.|  
||<xref:System.Windows.Forms.TrackBar> Formant|Umożliwia użytkownikom ustawianie wartości w skali, przenosząc "thumb" wzdłuż skali.|  
|Ustawienie daty|<xref:System.Windows.Forms.DateTimePicker> Formant|Wyświetla graficzny kalendarz, aby zezwolić użytkownikom na wybranie daty lub godziny.|  
||<xref:System.Windows.Forms.MonthCalendar> Formant|Wyświetla graficzny kalendarz, aby użytkownicy mogli wybrać zakres dat.|  
|Okna dialogowe|<xref:System.Windows.Forms.ColorDialog> Formant|Wyświetla okno dialogowe selektora kolorów, który umożliwia użytkownikom ustawianie koloru elementu interfejsu.|  
||<xref:System.Windows.Forms.FontDialog> Formant|Wyświetla okno dialogowe, który umożliwia użytkownikom Ustaw czcionkę i jego atrybuty.|  
||<xref:System.Windows.Forms.OpenFileDialog> Formant|Wyświetla okno dialogowe, które umożliwia użytkownikom przechodzenie do i wybierz plik.|  
||<xref:System.Windows.Forms.PrintDialog> Formant|Wyświetla okno dialogowe, które pozwala użytkownikom na wybranie drukarki i ustaw jego atrybuty.|  
||<xref:System.Windows.Forms.PrintPreviewDialog> Formant|Wyświetla okno dialogowe wyświetla jak formantu <xref:System.Drawing.Printing.PrintDocument> składnika pojawi się po wydrukowaniu.|  
||<xref:System.Windows.Forms.FolderBrowserDialog> Formant|Wyświetla okno dialogowe, którego użytkownicy mogą przeglądać, tworzyć i ostatecznie wybierz folder|  
||<xref:System.Windows.Forms.SaveFileDialog> Formant|Wyświetla okno dialogowe, które umożliwia użytkownikom zapisać plik.|  
|Formanty menu|<xref:System.Windows.Forms.MenuStrip> Formant|Tworzy niestandardowe menu. **Uwaga:** <xref:System.Windows.Forms.MenuStrip> zaprojektowano w celu zastąpienia <xref:System.Windows.Forms.MainMenu> formantu.|  
||<xref:System.Windows.Forms.ContextMenuStrip> Formant|Tworzy menu kontekstowe niestandardowych. **Uwaga:** <xref:System.Windows.Forms.ContextMenuStrip> zaprojektowano w celu zastąpienia <xref:System.Windows.Forms.ContextMenu> formantu.|  
|Polecenia|<xref:System.Windows.Forms.Button> Formant|Uruchamia, zatrzymuje lub przerwania procesu.|  
||<xref:System.Windows.Forms.LinkLabel> Formant|Tekst jest wyświetlany jako łącze stylu sieci Web i wyzwala zdarzenie, gdy użytkownik kliknie specjalne tekstu. Tekst jest zwykle łącza do innego okna lub witryny sieci Web.|  
||<xref:System.Windows.Forms.NotifyIcon> Formant|Wyświetla ikonę w obszarze powiadomień stanu na pasku zadań, reprezentujący aplikacji uruchomionej w tle.|  
||<xref:System.Windows.Forms.ToolStrip> Formant|Utworzenie pasków narzędzi, które mogą zostać systemu Microsoft Windows XP, Microsoft Office, Microsoft Internet Explorer lub niestandardowy wygląd i działanie z lub bez kompozycje i obsługę przepełnienie i zmianę kolejności elementów czasu wykonywania. **Uwaga:** <xref:System.Windows.Forms.ToolStrip> kontroli zaprojektowano w celu zastąpienia <xref:System.Windows.Forms.ToolBar> formantu.|  
|Pomoc dla użytkowników|<xref:System.Windows.Forms.HelpProvider> Składnik|Udostępnia menu podręczne lub pomoc dla formantów.|  
||<xref:System.Windows.Forms.ToolTip> Składnik|Udostępnia okno podręczne, które wyświetla krótki opis przeznaczenia formantu, gdy użytkownik zatrzyma wskaźnik myszy na kontrolce.|  
|Grupowanie formantów innych|<xref:System.Windows.Forms.Panel> Formant|Grupuje zestaw kontrolek na bez etykiety, którą można przewijać w ramce.|  
||<xref:System.Windows.Forms.GroupBox> Formant|Grupuje zestawu (takie jak przyciski radiowe) na ramce etykietą, nonscrollable.|  
||<xref:System.Windows.Forms.TabControl> Formant|Zapewnia wydajne obiekty zgrupowane strony organizowanie i uzyskiwania dostępu do sieci z kartami.|  
||<xref:System.Windows.Forms.SplitContainer> Formant|Udostępnia dwa panele oddzielone ruchomy paska. **Uwaga:** <xref:System.Windows.Forms.SplitContainer> kontroli zaprojektowano w celu zastąpienia <xref:System.Windows.Forms.Splitter> formantu.|  
||<xref:System.Windows.Forms.TableLayoutPanel> Formant|Reprezentuje panelu, który dynamicznie wychodzi poza swoją zawartość w siatce składa się z wierszy i kolumn.|  
||<xref:System.Windows.Forms.FlowLayoutPanel> Formant|Reprezentuje panelu, który dynamicznie wychodzi poza swoją zawartość w poziomie lub pionie.|  
|audio|<xref:System.Media.SoundPlayer> Formant|Odtwarza dźwięk pliki w formacie .wav. Dźwięki można załadować lub odtwarzane asynchronicznie.|  
  
## <a name="superseded-controls-and-components-by-function"></a>Zastąpione formanty i składniki według funkcji  
  
|Funkcja|Formant zastąpione|Zastąpienie zalecane|  
|--------------|------------------------|-----------------------------|  
|Wyświetlanie danych|<xref:System.Windows.Forms.DataGrid>|<xref:System.Windows.Forms.DataGridView>|  
|Wyświetlane informacje (służy tylko do odczytu)|<xref:System.Windows.Forms.StatusBar>|<xref:System.Windows.Forms.StatusStrip>|  
|Formanty menu|<xref:System.Windows.Forms.ContextMenu>|<xref:System.Windows.Forms.ContextMenuStrip>|  
||<xref:System.Windows.Forms.MainMenu>|<xref:System.Windows.Forms.MenuStrip>|  
|Polecenia|<xref:System.Windows.Forms.ToolBar>|<xref:System.Windows.Forms.ToolStrip>|  
||<xref:System.Windows.Forms.StatusBar>|<xref:System.Windows.Forms.StatusStrip>|  
|Układu formularza|<xref:System.Windows.Forms.Splitter>|<xref:System.Windows.Forms.SplitContainer>|  
  
## <a name="see-also"></a>Zobacz też  
 [Kontrolki do użycia w formularzach Windows Forms](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)  
 [Opracowywanie niestandardowych kontrolek formularzy Windows Forms za pomocą programu .NET Framework](../../../../docs/framework/winforms/controls/developing-custom-windows-forms-controls.md)
