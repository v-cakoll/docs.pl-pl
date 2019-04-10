---
title: Formanty formularzy systemu Windows według funkcji
ms.date: 03/30/2017
helpviewer_keywords:
- controls [Windows Forms], by function
- Windows Forms, controls by function
- Windows Forms controls, list of
ms.assetid: 5e65a6c3-5d6f-480d-beb8-b28f865f07e3
ms.openlocfilehash: 3a82642c985b7ec1cee885cdda7b054adbe3dfee
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59115482"
---
# <a name="windows-forms-controls-by-function"></a>Formanty formularzy systemu Windows według funkcji
Formularze Windows oferuje formanty i składniki, które wykonują wiele funkcji. W poniższej tabeli wymieniono kontrolek formularzy Windows Forms i składników, zgodnie z ogólnych funkcji. Ponadto w przypadku wielu formantów, które obsługują tę samą funkcję, zalecane kontroli znajduje się notatki dotyczące formant, który on zastąpiony. W osobnej tabeli kolejnych zastąpione formanty są wyświetlane z ich zalecane zamienniki.  
  
> [!NOTE]
>  W poniższej tabeli nie wymieniono każdy formant lub składnika, których można używać w formularzach Windows Forms; Aby bardziej pełną listę, zobacz [kontrolki do użycia w formularzach Windows Forms](controls-to-use-on-windows-forms.md)  
  
## <a name="recommended-controls-and-components-by-function"></a>Zalecane kontrolek i składników, funkcja  
  
|Funkcja|formant|Opis|  
|--------------|-------------|-----------------|  
|Wyświetlanie danych|<xref:System.Windows.Forms.DataGridView>  — formant|<xref:System.Windows.Forms.DataGridView> Kontroli zawiera tabelę można dostosować do wyświetlania danych. <xref:System.Windows.Forms.DataGridView> Klasa umożliwia dostosowanie komórek, wierszy, kolumny i obramowania. **Uwaga:**  <xref:System.Windows.Forms.DataGridView> Control oferuje wiele podstawowych i zaawansowanych funkcji, których brakuje w <xref:System.Windows.Forms.DataGrid> kontroli. Aby uzyskać więcej informacji, zobacz [różnice między Windows Forms formantami DataGridView i DataGrid](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md)|  
|Powiązanie danych oraz nawigacji|<xref:System.Windows.Forms.BindingSource> składnik|Ułatwia powiązanie kontrolek w formularzu z danymi, zapewniając zarządzania waluty, powiadomienia o zmianie i innych usług.|  
||<xref:System.Windows.Forms.BindingNavigator>  — formant|Udostępnia interfejs typu toolbar do nawigowania i manipulowanie danymi w formularzu.|  
|Edytowanie tekstu|<xref:System.Windows.Forms.TextBox>  — formant|Wyświetla tekst wprowadzony w czasie projektowania, które mogą być edytowane przez użytkowników w czasie wykonywania lub programowo zmienić.|  
||<xref:System.Windows.Forms.RichTextBox>  — formant|Umożliwia tekst do wyświetlenia za pomocą formatowania w postaci zwykłego tekstu lub w formacie tekstu sformatowanego (RTF).|  
||<xref:System.Windows.Forms.MaskedTextBox>  — formant|Ogranicza formatu danych wejściowych użytkownika|  
|Wyświetlane informacje (tylko do odczytu)|<xref:System.Windows.Forms.Label>  — formant|Wyświetla tekst, który użytkownicy nie mogą bezpośrednio edytować.|  
||<xref:System.Windows.Forms.LinkLabel>  — formant|Tekst jest wyświetlany jako łączy stylu sieci Web i wyzwala zdarzenie, kiedy użytkownik kliknie specjalne tekstu. Zazwyczaj tekst jest linkiem do innego okna lub witryny sieci Web.|  
||<xref:System.Windows.Forms.StatusStrip>  — formant|Wyświetla informacje dotyczące bieżącego stanu aplikacji przy użyciu obszaru ramce, zazwyczaj w dolnej części formularza nadrzędnego.|  
||<xref:System.Windows.Forms.ProgressBar>  — formant|Wyświetla bieżący postęp operacji dla użytkownika.|  
|Wyświetlanie strony sieci Web|<xref:System.Windows.Forms.WebBrowser>  — formant|Umożliwia użytkownikowi nawigację stron sieci Web wewnątrz formularza.|  
|Wybór z listy|<xref:System.Windows.Forms.CheckedListBox>  — formant|Zawiera listę elementów, każdy wraz z polem wyboru.|  
||<xref:System.Windows.Forms.ComboBox>  — formant|Wyświetla listę rozwijaną listę elementów.|  
||<xref:System.Windows.Forms.DomainUpDown>  — formant|Wyświetla listę elementów tekstowych, które użytkownicy będą mogli przewijać za pośrednictwem przy użyciu przycisków w górę i w dół.|  
||<xref:System.Windows.Forms.ListBox>  — formant|Wyświetla listę tekstu i elementów graficznych (ikony).|  
||<xref:System.Windows.Forms.ListView>  — formant|Wyświetla elementy w jednej z czterech różnych widoków. Widoki zawierać tylko tekst, tekst przy użyciu małych ikon, tekst przy użyciu dużych ikon i widoku szczegółów.|  
||<xref:System.Windows.Forms.NumericUpDown>  — formant|Wyświetla listę liczb, które użytkownicy będą mogli przewijać za pośrednictwem przy użyciu przycisków w górę i w dół.|  
||<xref:System.Windows.Forms.TreeView>  — formant|Przedstawia kolekcję hierarchiczną obiektów węzła, które może składać się z tekstem opcjonalne pola wyboru lub ikony.|  
|Wyświetlanie grafiki|<xref:System.Windows.Forms.PictureBox>  — formant|Wyświetla graficzny pliki, takie jak mapy bitowe i ikony w ramce.|  
|Magazyn grafiki|<xref:System.Windows.Forms.ImageList>  — formant|Służy jako repozytorium obrazów. <xref:System.Windows.Forms.ImageList> kontrolki i obrazów, które zawierają może zostać ponownie użyte z jednej aplikacji do następnego.|  
|Ustawienie wartości|<xref:System.Windows.Forms.CheckBox>  — formant|Wyświetla pole wyboru i etykiety tekstu. Zazwyczaj używane do ustawiania opcji.|  
||<xref:System.Windows.Forms.CheckedListBox>  — formant|Zawiera listę elementów, każdy wraz z polem wyboru.|  
||<xref:System.Windows.Forms.RadioButton>  — formant|Wyświetla przycisk, który może być włączony lub wyłączony.|  
||<xref:System.Windows.Forms.TrackBar>  — formant|Umożliwia użytkownikom ustawienie wartości w skali, przenosząc "mówi" wzdłuż skali.|  
|Ustawienie daty|<xref:System.Windows.Forms.DateTimePicker>  — formant|Wyświetla graficzny kalendarz, aby zezwolić użytkownikom na wybór daty lub godziny.|  
||<xref:System.Windows.Forms.MonthCalendar>  — formant|Wyświetla graficzny kalendarz, aby zezwolić użytkownikom na wybór zakresu dat.|  
|Okna dialogowe|<xref:System.Windows.Forms.ColorDialog>  — formant|Wyświetla okno dialogowe próbnika kolorów, który umożliwia użytkownikom ustawić kolor elementu interfejsu.|  
||<xref:System.Windows.Forms.FontDialog>  — formant|Wyświetlane jest okno dialogowe, która umożliwia użytkownikom ustawić czcionkę i jego atrybuty.|  
||<xref:System.Windows.Forms.OpenFileDialog>  — formant|Wyświetlane jest okno dialogowe, który umożliwia użytkownikom przejdź do, a następnie wybierz plik.|  
||<xref:System.Windows.Forms.PrintDialog>  — formant|Wyświetlane jest okno dialogowe, która umożliwia użytkownikom wybranie drukarki i ustaw jego atrybuty.|  
||<xref:System.Windows.Forms.PrintPreviewDialog>  — formant|Wyświetla okno dialogowe wyświetla, w jaki sposób kontrolki <xref:System.Drawing.Printing.PrintDocument> składnika pojawi się po wydrukowaniu.|  
||<xref:System.Windows.Forms.FolderBrowserDialog>  — formant|Wyświetla okno dialogowe, które umożliwia użytkownikom przeglądanie, tworzenie i ostatecznie wybierz folder|  
||<xref:System.Windows.Forms.SaveFileDialog>  — formant|Wyświetla okno dialogowe, które umożliwia użytkownikom zapisać plik.|  
|Formanty menu|<xref:System.Windows.Forms.MenuStrip>  — formant|Tworzy niestandardowe menu. **Uwaga:**  <xref:System.Windows.Forms.MenuStrip> Zaprojektowano w celu zastąpienia <xref:System.Windows.Forms.MainMenu> kontroli.|  
||<xref:System.Windows.Forms.ContextMenuStrip>  — formant|Tworzy niestandardowego menu kontekstowego. **Uwaga:**  <xref:System.Windows.Forms.ContextMenuStrip> Zaprojektowano w celu zastąpienia <xref:System.Windows.Forms.ContextMenu> kontroli.|  
|Polecenia|<xref:System.Windows.Forms.Button>  — formant|Uruchamia, zatrzymuje się lub przerwanie procesu.|  
||<xref:System.Windows.Forms.LinkLabel>  — formant|Tekst jest wyświetlany jako łączy stylu sieci Web i wyzwala zdarzenie, kiedy użytkownik kliknie specjalne tekstu. Zazwyczaj tekst jest linkiem do innego okna lub witryny sieci Web.|  
||<xref:System.Windows.Forms.NotifyIcon>  — formant|Wyświetla ikonę w obszarze stanu powiadomień na pasku zadań, która reprezentuje aplikację działającą w tle.|  
||<xref:System.Windows.Forms.ToolStrip>  — formant|Tworzy pasków narzędzi, które mogą mieć systemu Microsoft Windows XP, Microsoft Office, programu Microsoft Internet Explorer lub niestandardowy wygląd i działanie, z lub bez motywy i obsługę przepełnienie i zmiany kolejności elementów w czasie wykonywania. **Uwaga:**  <xref:System.Windows.Forms.ToolStrip> Kontroli zaprojektowano w celu zastąpienia <xref:System.Windows.Forms.ToolBar> kontroli.|  
|Pomoc dla użytkowników|<xref:System.Windows.Forms.HelpProvider> składnik|Udostępnia pomoc menu podręczne lub kontrolek.|  
||<xref:System.Windows.Forms.ToolTip> składnik|Udostępnia okno podręczne, które wyświetla krótki opis przeznaczenia kontrolki, gdy użytkownik zatrzyma wskaźnik myszy na kontrolce.|  
|Grupowanie innych formantów|<xref:System.Windows.Forms.Panel>  — formant|Grupuje zestaw formantów na bez etykiety, którą można przewijać w ramce.|  
||<xref:System.Windows.Forms.GroupBox>  — formant|Grupuje zestaw formantów (na przykład przycisków radiowych) dla etykietą, ramki nonscrollable.|  
||<xref:System.Windows.Forms.TabControl>  — formant|Zawiera strony organizowanie i uzyskiwania dostępu do sieci z kartami obiekty zgrupowane efektywnie.|  
||<xref:System.Windows.Forms.SplitContainer>  — formant|Udostępnia dwa panele rozdzielone ruchome paska. **Uwaga:**  <xref:System.Windows.Forms.SplitContainer> Kontroli zaprojektowano w celu zastąpienia <xref:System.Windows.Forms.Splitter> kontroli.|  
||<xref:System.Windows.Forms.TableLayoutPanel>  — formant|Reprezentuje panel, który dynamicznie wychodzi poza swoją zawartość w siatce, składa się z wierszy i kolumn.|  
||<xref:System.Windows.Forms.FlowLayoutPanel>  — formant|Reprezentuje panel, który dynamicznie wychodzi poza swoją zawartość w poziomie lub pionie.|  
|Dźwięk|<xref:System.Media.SoundPlayer>  — formant|Odtwarza dźwięk pliki w formacie .wav. Dźwięki można załadować lub odtwarzane asynchronicznie.|  
  
## <a name="superseded-controls-and-components-by-function"></a>Zastąpione kontrolek i składników, funkcja  
  
|Funkcja|Zastąpione kontroli|Zalecane zastąpienia|  
|--------------|------------------------|-----------------------------|  
|Wyświetlanie danych|<xref:System.Windows.Forms.DataGrid>|<xref:System.Windows.Forms.DataGridView>|  
|Wyświetlane informacje (formantów tylko do odczytu)|<xref:System.Windows.Forms.StatusBar>|<xref:System.Windows.Forms.StatusStrip>|  
|Formanty menu|<xref:System.Windows.Forms.ContextMenu>|<xref:System.Windows.Forms.ContextMenuStrip>|  
||<xref:System.Windows.Forms.MainMenu>|<xref:System.Windows.Forms.MenuStrip>|  
|Polecenia|<xref:System.Windows.Forms.ToolBar>|<xref:System.Windows.Forms.ToolStrip>|  
||<xref:System.Windows.Forms.StatusBar>|<xref:System.Windows.Forms.StatusStrip>|  
|Układ formularza|<xref:System.Windows.Forms.Splitter>|<xref:System.Windows.Forms.SplitContainer>|  
  
## <a name="see-also"></a>Zobacz także

- [Formanty do użycia w formularzach systemu Windows](controls-to-use-on-windows-forms.md)
- [Opracowywanie niestandardowych formantów formularzy systemu Windows za pomocą programu .NET Framework](developing-custom-windows-forms-controls.md)
