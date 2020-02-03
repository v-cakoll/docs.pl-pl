---
title: Kontrolki według funkcji
ms.date: 03/30/2017
helpviewer_keywords:
- controls [Windows Forms], by function
- Windows Forms, controls by function
- Windows Forms controls, list of
ms.assetid: 5e65a6c3-5d6f-480d-beb8-b28f865f07e3
ms.openlocfilehash: f2341d49513b418c244ee7ab93c0858899502487
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76741578"
---
# <a name="windows-forms-controls-by-function"></a>Formanty formularzy systemu Windows według funkcji
Windows Forms oferuje kontrolki i składniki, które wykonują szereg funkcji. Poniższa tabela zawiera listę formantów Windows Forms i składników zgodnie z ogólną funkcją. Ponadto, gdy istnieje wiele kontrolek, które obsługują tę samą funkcję, zalecana kontrolka jest wyświetlana z adnotacją dotyczącą formantu, który został zastąpiony. W oddzielnej tabeli zastąpione kontrolki są wyświetlane z ich zalecanymi zamiennikami.  
  
> [!NOTE]
> W poniższych tabelach nie wymieniono wszystkich formantów lub składników, których można użyć w Windows Forms; Aby uzyskać bardziej kompleksową listę, zobacz [kontrolki do użycia na Windows Forms](controls-to-use-on-windows-forms.md)  
  
## <a name="recommended-controls-and-components-by-function"></a>Zalecane formanty i składniki według funkcji  
  
|Funkcja|formant|Opis|  
|--------------|-------------|-----------------|  
|Wyświetlanie danych|Kontrolka <xref:System.Windows.Forms.DataGridView>|Formant <xref:System.Windows.Forms.DataGridView> zawiera dostosowywalną tabelę do wyświetlania danych. Klasa <xref:System.Windows.Forms.DataGridView> umożliwia dostosowanie komórek, wierszy, kolumn i obramowań. **Uwaga:**  Kontrolka <xref:System.Windows.Forms.DataGridView> udostępnia wiele podstawowych i zaawansowanych funkcji, których brakuje w kontrolce <xref:System.Windows.Forms.DataGrid>. Aby uzyskać więcej informacji, zobacz [różnice między kontrolkami DataGridView i DataGrid Windows Forms](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md)|  
|Powiązanie danych i nawigacja|<xref:System.Windows.Forms.BindingSource> cm6long|Upraszcza kontrolki wiązania w formularzu do danych, zapewniając zarządzanie walutą, powiadomienia o zmianach i inne usługi.|  
||Kontrolka <xref:System.Windows.Forms.BindingNavigator>|Udostępnia interfejs typu Toolbar, który umożliwia nawigowanie i manipulowanie danymi w formularzu.|  
|Edytowanie tekstu|Kontrolka <xref:System.Windows.Forms.TextBox>|Wyświetla tekst wprowadzony w czasie projektowania, który może być edytowany przez użytkowników w czasie wykonywania lub zmieniany programowo.|  
||Kontrolka <xref:System.Windows.Forms.RichTextBox>|Umożliwia wyświetlanie tekstu z formatowaniem w formacie zwykłego tekstu lub tekstu sformatowanego (RTF).|  
||Kontrolka <xref:System.Windows.Forms.MaskedTextBox>|Ogranicza format danych wejściowych użytkownika|  
|Wyświetlanie informacji (tylko do odczytu)|Kontrolka <xref:System.Windows.Forms.Label>|Wyświetla tekst, który użytkownicy nie mogą edytować bezpośrednio.|  
||Kontrolka <xref:System.Windows.Forms.LinkLabel>|Wyświetla tekst jako łącze w stylu sieci Web i wyzwala zdarzenie po kliknięciu specjalnego tekstu przez użytkownika. Zazwyczaj tekst jest łączem do innego okna lub witryny sieci Web.|  
||Kontrolka <xref:System.Windows.Forms.StatusStrip>|Wyświetla informacje o bieżącym stanie aplikacji przy użyciu obszaru Framed, zwykle w dolnej części formularza nadrzędnego.|  
||Kontrolka <xref:System.Windows.Forms.ProgressBar>|Wyświetla bieżący postęp operacji dla użytkownika.|  
|Wyświetlanie strony sieci Web|Kontrolka <xref:System.Windows.Forms.WebBrowser>|Umożliwia użytkownikowi nawigowanie po stronach sieci Web wewnątrz formularza.|  
|Wybór z listy|Kontrolka <xref:System.Windows.Forms.CheckedListBox>|Wyświetla listę elementów przewijalnych, z których każde towarzyszy pole wyboru.|  
||Kontrolka <xref:System.Windows.Forms.ComboBox>|Wyświetla listę rozwijaną elementów.|  
||Kontrolka <xref:System.Windows.Forms.DomainUpDown>|Wyświetla listę elementów tekstowych, które użytkownicy mogą przewijać przy użyciu przycisków w górę i w dół.|  
||Kontrolka <xref:System.Windows.Forms.ListBox>|Wyświetla listę elementów tekstowych i graficznych (ikon).|  
||Kontrolka <xref:System.Windows.Forms.ListView>|Wyświetla elementy w jednym z czterech różnych widoków. Widoki obejmują tylko tekst, tekst z małymi ikonami, tekst z dużymi ikonami i widok szczegółów.|  
||Kontrolka <xref:System.Windows.Forms.NumericUpDown>|Wyświetla listę cyfr, które użytkownicy mogą przewijać przy użyciu przycisków w górę i w dół.|  
||Kontrolka <xref:System.Windows.Forms.TreeView>|Wyświetla hierarchiczną kolekcję obiektów węzła, która może składać się z tekstu z opcjonalnymi polami wyboru lub ikonami.|  
|Wyświetlanie grafiki|Kontrolka <xref:System.Windows.Forms.PictureBox>|Wyświetla pliki graficzne, takie jak mapy bitowe i ikony, w ramce.|  
|Magazyn grafiki|Kontrolka <xref:System.Windows.Forms.ImageList>|Służy jako repozytorium obrazów. <xref:System.Windows.Forms.ImageList> kontrolki i zawarte w nich obrazy mogą być ponownie używane z jednej aplikacji do następnej.|  
|Ustawienie wartości|Kontrolka <xref:System.Windows.Forms.CheckBox>|Wyświetla pole wyboru i etykietę dla tekstu. Zwykle używane do ustawiania opcji.|  
||Kontrolka <xref:System.Windows.Forms.CheckedListBox>|Wyświetla listę elementów przewijalnych, z których każde towarzyszy pole wyboru.|  
||Kontrolka <xref:System.Windows.Forms.RadioButton>|Wyświetla przycisk, który można włączyć lub wyłączyć.|  
||Kontrolka <xref:System.Windows.Forms.TrackBar>|Umożliwia użytkownikom ustawianie wartości w skali przez przeniesienie "kciuka" wzdłuż skali.|  
|Ustawienie daty|Kontrolka <xref:System.Windows.Forms.DateTimePicker>|Wyświetla graficzny kalendarz, aby umożliwić użytkownikom wybranie daty lub godziny.|  
||Kontrolka <xref:System.Windows.Forms.MonthCalendar>|Wyświetla graficzny kalendarz, aby umożliwić użytkownikom wybranie zakresu dat.|  
|Okna dialogowe|Kontrolka <xref:System.Windows.Forms.ColorDialog>|Wyświetla okno dialogowe selektora kolorów, które umożliwia użytkownikom ustawianie koloru elementu interfejsu.|  
||Kontrolka <xref:System.Windows.Forms.FontDialog>|Wyświetla okno dialogowe, które umożliwia użytkownikom ustawianie czcionki i jej atrybutów.|  
||Kontrolka <xref:System.Windows.Forms.OpenFileDialog>|Wyświetla okno dialogowe, które umożliwia użytkownikom nawigowanie do i wybieranie pliku.|  
||Kontrolka <xref:System.Windows.Forms.PrintDialog>|Wyświetla okno dialogowe, które umożliwia użytkownikom wybranie drukarki i ustawienie jej atrybutów.|  
||Kontrolka <xref:System.Windows.Forms.PrintPreviewDialog>|Wyświetla okno dialogowe, w którym jest wyświetlany sposób wyświetlania składnika <xref:System.Drawing.Printing.PrintDocument> formantu po wydrukowaniu.|  
||Kontrolka <xref:System.Windows.Forms.FolderBrowserDialog>|Wyświetla okno dialogowe, które umożliwia użytkownikom przeglądanie, tworzenie i ostatecznie Wybieranie folderu|  
||Kontrolka <xref:System.Windows.Forms.SaveFileDialog>|Wyświetla okno dialogowe, które umożliwia użytkownikom zapisywanie pliku.|  
|Kontrolki menu|Kontrolka <xref:System.Windows.Forms.MenuStrip>|Tworzy menu niestandardowe. **Uwaga:**  <xref:System.Windows.Forms.MenuStrip> jest zaprojektowana tak, aby zastąpić formant <xref:System.Windows.Forms.MainMenu>.|  
||Kontrolka <xref:System.Windows.Forms.ContextMenuStrip>|Tworzy niestandardowe menu kontekstowe. **Uwaga:**  <xref:System.Windows.Forms.ContextMenuStrip> jest zaprojektowana tak, aby zastąpić formant <xref:System.Windows.Forms.ContextMenu>.|  
|Polecenia|Kontrolka <xref:System.Windows.Forms.Button>|Uruchamia, kończy lub przerywa proces.|  
||Kontrolka <xref:System.Windows.Forms.LinkLabel>|Wyświetla tekst jako łącze w stylu sieci Web i wyzwala zdarzenie po kliknięciu specjalnego tekstu przez użytkownika. Zazwyczaj tekst jest łączem do innego okna lub witryny sieci Web.|  
||Kontrolka <xref:System.Windows.Forms.NotifyIcon>|Wyświetla ikonę w obszarze powiadomień o stanie paska zadań, który reprezentuje aplikację działającą w tle.|  
||Kontrolka <xref:System.Windows.Forms.ToolStrip>|Tworzy paski narzędzi, które mogą mieć system Microsoft Windows XP, Microsoft Office, program Microsoft Internet Explorer lub niestandardowy wygląd i działanie, z lub bez motywów oraz z obsługą przepełnienia i zmiany kolejności elementów w czasie wykonywania. **Uwaga:**  Formant <xref:System.Windows.Forms.ToolStrip> zaprojektowano w celu zastąpienia kontrolki <xref:System.Windows.Forms.ToolBar>.|  
|Pomoc dla użytkowników|<xref:System.Windows.Forms.HelpProvider> cm6long|Udostępnia okna podręczne lub pomoc online dla kontrolek.|  
||<xref:System.Windows.Forms.ToolTip> cm6long|Udostępnia okno podręczne, które wyświetla Krótki opis przeznaczenie kontrolki, gdy użytkownik umieści wskaźnik na kontrolce.|  
|Grupowanie innych kontrolek|Kontrolka <xref:System.Windows.Forms.Panel>|Grupuje zestaw kontrolek w ramce bez etykiet.|  
||Kontrolka <xref:System.Windows.Forms.GroupBox>|Grupuje zestaw kontrolek (takich jak przyciski radiowe) w ramce z etykietą nieprzewijalną.|  
||Kontrolka <xref:System.Windows.Forms.TabControl>|Udostępnia stronę z kartami do wydajnego organizowania i uzyskiwania dostępu do zgrupowanych obiektów.|  
||Kontrolka <xref:System.Windows.Forms.SplitContainer>|Program udostępnia dwa panele rozdzielone przez ruchomy pasek. **Uwaga:**  Formant <xref:System.Windows.Forms.SplitContainer> zaprojektowano w celu zastąpienia kontrolki <xref:System.Windows.Forms.Splitter>.|  
||Kontrolka <xref:System.Windows.Forms.TableLayoutPanel>|Reprezentuje Panel, który dynamicznie ustala zawartość w siatce składającej się z wierszy i kolumn.|  
||Kontrolka <xref:System.Windows.Forms.FlowLayoutPanel>|Reprezentuje Panel, który dynamicznie określa zawartość w poziomie lub w pionie.|  
|Dźwięk|Kontrolka <xref:System.Media.SoundPlayer>|Odtwarza pliki dźwiękowe w formacie wav. Dźwięki można ładować lub odtwarzać asynchronicznie.|  
  
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
