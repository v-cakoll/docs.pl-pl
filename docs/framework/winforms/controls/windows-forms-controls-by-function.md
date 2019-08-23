---
title: Formanty formularzy systemu Windows według funkcji
ms.date: 03/30/2017
helpviewer_keywords:
- controls [Windows Forms], by function
- Windows Forms, controls by function
- Windows Forms controls, list of
ms.assetid: 5e65a6c3-5d6f-480d-beb8-b28f865f07e3
ms.openlocfilehash: 366b7412a61cac9d3706500adaee34fa8659fba2
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69922716"
---
# <a name="windows-forms-controls-by-function"></a>Formanty formularzy systemu Windows według funkcji
Windows Forms oferuje kontrolki i składniki, które wykonują szereg funkcji. Poniższa tabela zawiera listę formantów Windows Forms i składników zgodnie z ogólną funkcją. Ponadto, gdy istnieje wiele kontrolek, które obsługują tę samą funkcję, zalecana kontrolka jest wyświetlana z adnotacją dotyczącą formantu, który został zastąpiony. W oddzielnej tabeli zastąpione kontrolki są wyświetlane z ich zalecanymi zamiennikami.  
  
> [!NOTE]
> W poniższych tabelach nie wymieniono wszystkich formantów lub składników, których można użyć w Windows Forms; Aby uzyskać bardziej kompleksową listę, zobacz [kontrolki do użycia na Windows Forms](controls-to-use-on-windows-forms.md)  
  
## <a name="recommended-controls-and-components-by-function"></a>Zalecane formanty i składniki według funkcji  
  
|Funkcja|formant|Opis|  
|--------------|-------------|-----------------|  
|Wyświetlanie danych|<xref:System.Windows.Forms.DataGridView>kontroli|<xref:System.Windows.Forms.DataGridView> Formant zawiera dostosowywalną tabelę do wyświetlania danych. <xref:System.Windows.Forms.DataGridView> Klasa umożliwia dostosowanie komórek, wierszy, kolumn i obramowań. **Uwaga:**  Formant zawiera wiele podstawowych i zaawansowanych funkcji, których brakuje <xref:System.Windows.Forms.DataGrid> w formancie. <xref:System.Windows.Forms.DataGridView> Aby uzyskać więcej informacji, zobacz [różnice między kontrolkami DataGridView i DataGrid Windows Forms](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md)|  
|Powiązanie danych i nawigacja|<xref:System.Windows.Forms.BindingSource> cm6long|Upraszcza kontrolki wiązania w formularzu do danych, zapewniając zarządzanie walutą, powiadomienia o zmianach i inne usługi.|  
||<xref:System.Windows.Forms.BindingNavigator>kontroli|Udostępnia interfejs typu Toolbar, który umożliwia nawigowanie i manipulowanie danymi w formularzu.|  
|Edytowanie tekstu|<xref:System.Windows.Forms.TextBox>kontroli|Wyświetla tekst wprowadzony w czasie projektowania, który może być edytowany przez użytkowników w czasie wykonywania lub zmieniany programowo.|  
||<xref:System.Windows.Forms.RichTextBox>kontroli|Umożliwia wyświetlanie tekstu z formatowaniem w formacie zwykłego tekstu lub tekstu sformatowanego (RTF).|  
||<xref:System.Windows.Forms.MaskedTextBox>kontroli|Ogranicza format danych wejściowych użytkownika|  
|Wyświetlanie informacji (tylko do odczytu)|<xref:System.Windows.Forms.Label>kontroli|Wyświetla tekst, który użytkownicy nie mogą edytować bezpośrednio.|  
||<xref:System.Windows.Forms.LinkLabel>kontroli|Wyświetla tekst jako łącze w stylu sieci Web i wyzwala zdarzenie po kliknięciu specjalnego tekstu przez użytkownika. Zazwyczaj tekst jest łączem do innego okna lub witryny sieci Web.|  
||<xref:System.Windows.Forms.StatusStrip>kontroli|Wyświetla informacje o bieżącym stanie aplikacji przy użyciu obszaru Framed, zwykle w dolnej części formularza nadrzędnego.|  
||<xref:System.Windows.Forms.ProgressBar>kontroli|Wyświetla bieżący postęp operacji dla użytkownika.|  
|Wyświetlanie strony sieci Web|<xref:System.Windows.Forms.WebBrowser>kontroli|Umożliwia użytkownikowi nawigowanie po stronach sieci Web wewnątrz formularza.|  
|Wybór z listy|<xref:System.Windows.Forms.CheckedListBox>kontroli|Wyświetla listę elementów przewijalnych, z których każde towarzyszy pole wyboru.|  
||<xref:System.Windows.Forms.ComboBox>kontroli|Wyświetla listę rozwijaną elementów.|  
||<xref:System.Windows.Forms.DomainUpDown>kontroli|Wyświetla listę elementów tekstowych, które użytkownicy mogą przewijać przy użyciu przycisków w górę i w dół.|  
||<xref:System.Windows.Forms.ListBox>kontroli|Wyświetla listę elementów tekstowych i graficznych (ikon).|  
||<xref:System.Windows.Forms.ListView>kontroli|Wyświetla elementy w jednym z czterech różnych widoków. Widoki obejmują tylko tekst, tekst z małymi ikonami, tekst z dużymi ikonami i widok szczegółów.|  
||<xref:System.Windows.Forms.NumericUpDown>kontroli|Wyświetla listę cyfr, które użytkownicy mogą przewijać przy użyciu przycisków w górę i w dół.|  
||<xref:System.Windows.Forms.TreeView>kontroli|Wyświetla hierarchiczną kolekcję obiektów węzła, która może składać się z tekstu z opcjonalnymi polami wyboru lub ikonami.|  
|Wyświetlanie grafiki|<xref:System.Windows.Forms.PictureBox>kontroli|Wyświetla pliki graficzne, takie jak mapy bitowe i ikony, w ramce.|  
|Magazyn grafiki|<xref:System.Windows.Forms.ImageList>kontroli|Służy jako repozytorium obrazów. <xref:System.Windows.Forms.ImageList>kontrolki i zawarte w nich obrazy mogą być ponownie używane z jednej aplikacji do następnej.|  
|Ustawienie wartości|<xref:System.Windows.Forms.CheckBox>kontroli|Wyświetla pole wyboru i etykietę dla tekstu. Zwykle używane do ustawiania opcji.|  
||<xref:System.Windows.Forms.CheckedListBox>kontroli|Wyświetla listę elementów przewijalnych, z których każde towarzyszy pole wyboru.|  
||<xref:System.Windows.Forms.RadioButton>kontroli|Wyświetla przycisk, który można włączyć lub wyłączyć.|  
||<xref:System.Windows.Forms.TrackBar>kontroli|Umożliwia użytkownikom ustawianie wartości w skali przez przeniesienie "kciuka" wzdłuż skali.|  
|Ustawienie daty|<xref:System.Windows.Forms.DateTimePicker>kontroli|Wyświetla graficzny kalendarz, aby umożliwić użytkownikom wybranie daty lub godziny.|  
||<xref:System.Windows.Forms.MonthCalendar>kontroli|Wyświetla graficzny kalendarz, aby umożliwić użytkownikom wybranie zakresu dat.|  
|Okna dialogowe|<xref:System.Windows.Forms.ColorDialog>kontroli|Wyświetla okno dialogowe selektora kolorów, które umożliwia użytkownikom ustawianie koloru elementu interfejsu.|  
||<xref:System.Windows.Forms.FontDialog>kontroli|Wyświetla okno dialogowe, które umożliwia użytkownikom ustawianie czcionki i jej atrybutów.|  
||<xref:System.Windows.Forms.OpenFileDialog>kontroli|Wyświetla okno dialogowe, które umożliwia użytkownikom nawigowanie do i wybieranie pliku.|  
||<xref:System.Windows.Forms.PrintDialog>kontroli|Wyświetla okno dialogowe, które umożliwia użytkownikom wybranie drukarki i ustawienie jej atrybutów.|  
||<xref:System.Windows.Forms.PrintPreviewDialog>kontroli|Wyświetla okno dialogowe, w którym jest wyświetlany sposób <xref:System.Drawing.Printing.PrintDocument> wyświetlania składnika formantu po wydrukowaniu.|  
||<xref:System.Windows.Forms.FolderBrowserDialog>kontroli|Wyświetla okno dialogowe, które umożliwia użytkownikom przeglądanie, tworzenie i ostatecznie Wybieranie folderu|  
||<xref:System.Windows.Forms.SaveFileDialog>kontroli|Wyświetla okno dialogowe, które umożliwia użytkownikom zapisywanie pliku.|  
|Kontrolki menu|<xref:System.Windows.Forms.MenuStrip>kontroli|Tworzy menu niestandardowe. **Uwaga:**  Zaprojektowano, <xref:System.Windows.Forms.MenuStrip> aby <xref:System.Windows.Forms.MainMenu> zastąpić formant.|  
||<xref:System.Windows.Forms.ContextMenuStrip>kontroli|Tworzy niestandardowe menu kontekstowe. **Uwaga:**  Zaprojektowano, <xref:System.Windows.Forms.ContextMenuStrip> aby <xref:System.Windows.Forms.ContextMenu> zastąpić formant.|  
|Polecenia|<xref:System.Windows.Forms.Button>kontroli|Uruchamia, kończy lub przerywa proces.|  
||<xref:System.Windows.Forms.LinkLabel>kontroli|Wyświetla tekst jako łącze w stylu sieci Web i wyzwala zdarzenie po kliknięciu specjalnego tekstu przez użytkownika. Zazwyczaj tekst jest łączem do innego okna lub witryny sieci Web.|  
||<xref:System.Windows.Forms.NotifyIcon>kontroli|Wyświetla ikonę w obszarze powiadomień o stanie paska zadań, który reprezentuje aplikację działającą w tle.|  
||<xref:System.Windows.Forms.ToolStrip>kontroli|Tworzy paski narzędzi, które mogą mieć system Microsoft Windows XP, Microsoft Office, program Microsoft Internet Explorer lub niestandardowy wygląd i działanie, z lub bez motywów oraz z obsługą przepełnienia i zmiany kolejności elementów w czasie wykonywania. **Uwaga:**  Kontrolka jest zaprojektowana tak <xref:System.Windows.Forms.ToolBar> , aby zamienić formant. <xref:System.Windows.Forms.ToolStrip>|  
|Pomoc użytkownika|<xref:System.Windows.Forms.HelpProvider> cm6long|Udostępnia okna podręczne lub pomoc online dla kontrolek.|  
||<xref:System.Windows.Forms.ToolTip> cm6long|Udostępnia okno podręczne, które wyświetla Krótki opis przeznaczenie kontrolki, gdy użytkownik umieści wskaźnik na kontrolce.|  
|Grupowanie innych kontrolek|<xref:System.Windows.Forms.Panel>kontroli|Grupuje zestaw kontrolek w ramce bez etykiet.|  
||<xref:System.Windows.Forms.GroupBox>kontroli|Grupuje zestaw kontrolek (takich jak przyciski radiowe) w ramce z etykietą nieprzewijalną.|  
||<xref:System.Windows.Forms.TabControl>kontroli|Udostępnia stronę z kartami do wydajnego organizowania i uzyskiwania dostępu do zgrupowanych obiektów.|  
||<xref:System.Windows.Forms.SplitContainer>kontroli|Program udostępnia dwa panele rozdzielone przez ruchomy pasek. **Uwaga:**  Kontrolka jest zaprojektowana tak <xref:System.Windows.Forms.Splitter> , aby zamienić formant. <xref:System.Windows.Forms.SplitContainer>|  
||<xref:System.Windows.Forms.TableLayoutPanel>kontroli|Reprezentuje Panel, który dynamicznie ustala zawartość w siatce składającej się z wierszy i kolumn.|  
||<xref:System.Windows.Forms.FlowLayoutPanel>kontroli|Reprezentuje Panel, który dynamicznie określa zawartość w poziomie lub w pionie.|  
|Dźwięk|<xref:System.Media.SoundPlayer>kontroli|Odtwarza pliki dźwiękowe w formacie wav. Dźwięki można ładować lub odtwarzać asynchronicznie.|  
  
## <a name="superseded-controls-and-components-by-function"></a>Zastąpione kontrolki i składniki według funkcji  
  
|Funkcja|Zastępujący formant|Zalecane zastąpienie|  
|--------------|------------------------|-----------------------------|  
|Wyświetlanie danych|<xref:System.Windows.Forms.DataGrid>|<xref:System.Windows.Forms.DataGridView>|  
|Wyświetlanie informacji (kontrolki tylko do odczytu)|<xref:System.Windows.Forms.StatusBar>|<xref:System.Windows.Forms.StatusStrip>|  
|Kontrolki menu|<xref:System.Windows.Forms.ContextMenu>|<xref:System.Windows.Forms.ContextMenuStrip>|  
||<xref:System.Windows.Forms.MainMenu>|<xref:System.Windows.Forms.MenuStrip>|  
|Polecenia|<xref:System.Windows.Forms.ToolBar>|<xref:System.Windows.Forms.ToolStrip>|  
||<xref:System.Windows.Forms.StatusBar>|<xref:System.Windows.Forms.StatusStrip>|  
|Układ formularza|<xref:System.Windows.Forms.Splitter>|<xref:System.Windows.Forms.SplitContainer>|  
  
## <a name="see-also"></a>Zobacz także

- [Kontrolki do użycia w formularzach Windows Forms](controls-to-use-on-windows-forms.md)
- [Opracowywanie niestandardowych kontrolek formularzy Windows Forms za pomocą programu .NET Framework](developing-custom-windows-forms-controls.md)
