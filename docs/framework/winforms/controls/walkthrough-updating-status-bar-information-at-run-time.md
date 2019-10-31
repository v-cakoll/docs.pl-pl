---
title: 'Wskazówki: aktualizowanie informacji na pasku stanu w czasie wykonywania'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- status bars [Windows Forms], updating at run time
- status bars [Windows Forms], refreshing panels
- StatusBar control [Windows Forms], refreshing panels
- panels [Windows Forms], refreshing status bar
ms.assetid: cc2abb06-c082-49f7-a5a3-2fd1bbcb58d1
ms.openlocfilehash: f1d22079dfa3a6452efb74ef57530bb43e059a4a
ms.sourcegitcommit: 5a28f8eb071fcc09b045b0c4ae4b96898673192e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2019
ms.locfileid: "73197103"
---
# <a name="walkthrough-updating-status-bar-information-at-run-time"></a>Wskazówki: aktualizowanie informacji na pasku stanu w czasie wykonywania
> [!IMPORTANT]
> Kontrolki <xref:System.Windows.Forms.StatusStrip> i <xref:System.Windows.Forms.ToolStripStatusLabel> zastępują i dodają funkcje do kontrolek <xref:System.Windows.Forms.StatusBar> i <xref:System.Windows.Forms.StatusBarPanel>; jednak kontrolki <xref:System.Windows.Forms.StatusBar> i <xref:System.Windows.Forms.StatusBarPanel> są zachowywane w celu zapewnienia zgodności z poprzednimi wersjami i w przyszłości, jeśli wybierzesz opcję.  
  
 Często program będzie wywoływał, aby zaktualizować zawartość paneli paska stanu dynamicznie w czasie wykonywania, na podstawie zmian stanu aplikacji lub innej interakcji z użytkownikiem. Jest to typowy sposób, aby sygnalizować użytkownikom, że klucze takie jak Caps Lock, NUM LOCK lub SCROLL LOCK są włączone, lub podać datę lub zegar jako wygodne odwołanie.  
  
 W poniższym przykładzie zostanie użyte wystąpienie klasy <xref:System.Windows.Forms.StatusBarPanel> do hostowania zegara.  
  
### <a name="to-get-the-status-bar-ready-for-updating"></a>Aby wyświetlić pasek stanu gotowy do aktualizacji  
  
1. Utwórz nowy formularz systemu Windows.  
  
2. Dodaj kontrolkę <xref:System.Windows.Forms.StatusBar> do formularza. Aby uzyskać szczegółowe informacje, zobacz [How to: Add Controls to Windows Forms](how-to-add-controls-to-windows-forms.md).  
  
3. Dodaj panel paska stanu do kontrolki <xref:System.Windows.Forms.StatusBar>. Aby uzyskać szczegółowe informacje, zobacz [jak: dodać panele do kontrolki StatusBar](how-to-add-panels-to-a-statusbar-control.md).  
  
4. Dla kontrolki <xref:System.Windows.Forms.StatusBar> dodanej do formularza ustaw właściwość <xref:System.Windows.Forms.StatusBar.ShowPanels%2A> na `true`.  
  
5. Dodaj składnik <xref:System.Windows.Forms.Timer> Windows Forms do formularza.  
  
    > [!NOTE]
    > Składnik <xref:System.Windows.Forms.Timer?displayProperty=nameWithType> Windows Forms jest przeznaczony dla środowiska Windows Forms. Jeśli potrzebujesz czasomierza odpowiedniego dla środowiska serwera, zobacz [wprowadzenie do czasomierzy oparte na serwerze](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/tb9yt5e6(v=vs.90)).  
  
6. Ustaw właściwość <xref:System.Windows.Forms.Timer.Enabled%2A> na `true`.  
  
7. Dla właściwości <xref:System.Windows.Forms.Timer.Interval%2A> <xref:System.Windows.Forms.Timer> ustaw wartość 30000.  
  
    > [!NOTE]
    > Właściwość <xref:System.Windows.Forms.Timer.Interval%2A> składnika <xref:System.Windows.Forms.Timer> jest ustawiona na 30 sekund (30 000 milisekund), aby mieć pewność, że dokładny czas zostanie odzwierciedlony w wyświetlonym czasie.  
  
### <a name="to-implement-the-timer-to-update-the-status-bar"></a>Aby zaimplementować czasomierz w celu zaktualizowania paska stanu  
  
1. Wstaw następujący kod do procedury obsługi zdarzeń składnika <xref:System.Windows.Forms.Timer>, aby zaktualizować panel kontrolki <xref:System.Windows.Forms.StatusBar>.  
  
    ```vb  
    Private Sub Timer1_Tick(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Timer1.Tick  
       StatusBar1.Panels(0).Text = Now.ToShortTimeString  
    End Sub  
    ```  
  
    ```csharp  
    private void timer1_Tick(object sender, System.EventArgs e)  
    {  
       statusBar1.Panels[0].Text = DateTime.Now.ToShortTimeString();  
    }  
    ```  
  
    ```cpp  
    private:  
      System::Void timer1_Tick(System::Object ^ sender,  
        System::EventArgs ^ e)  
      {  
        statusBar1->Panels[0]->Text =  
          DateTime::Now.ToShortTimeString();  
      }  
    ```  
  
     W tym momencie można przystąpić do uruchamiania aplikacji i obserwować zegar uruchomiony w panelu pasek stanu.  
  
### <a name="to-test-the-application"></a>Aby przetestować aplikację  
  
1. Debuguj aplikację i naciśnij klawisz F5, aby ją uruchomić. Aby uzyskać szczegółowe informacje o debugowaniu, zobacz [debugowanie w programie Visual Studio](/visualstudio/debugger/debugger-feature-tour).  
  
    > [!NOTE]
    > Zegar będzie wyświetlany na pasku stanu przez około 30 sekund. Jest to najlepszy możliwy czas. Z drugiej strony, aby zegar pojawił się wcześniej, można zmniejszyć wartość właściwości <xref:System.Windows.Forms.Timer.Interval%2A> ustawionej w kroku 7 w poprzedniej procedurze.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.StatusBar>
- <xref:System.Windows.Forms.ToolStripStatusLabel>
- [Instrukcje: dodawanie paneli do kontrolki StatusBar](how-to-add-panels-to-a-statusbar-control.md)
- [Instrukcje: ustalanie, który panel został kliknięty w kontrolce StatusBar formularzy Windows Forms](determine-which-panel-wf-statusbar-control-was-clicked.md)
- [StatusBar, kontrolka — omówienie](statusbar-control-overview-windows-forms.md)
