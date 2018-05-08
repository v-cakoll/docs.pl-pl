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
ms.openlocfilehash: 4b2d968aff157ac83b21823d546c052e140607a2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="walkthrough-updating-status-bar-information-at-run-time"></a>Wskazówki: aktualizowanie informacji na pasku stanu w czasie wykonywania
> [!IMPORTANT]
>  <xref:System.Windows.Forms.StatusStrip> i <xref:System.Windows.Forms.ToolStripStatusLabel> formanty Zastąp oraz dodawać funkcje do <xref:System.Windows.Forms.StatusBar> i <xref:System.Windows.Forms.StatusBarPanel> steruje; jednak <xref:System.Windows.Forms.StatusBar> i <xref:System.Windows.Forms.StatusBarPanel> formanty są zachowywane dla zgodności z poprzednimi wersjami i użycia w przyszłości, jeśli możesz Wybierz.  
  
 Często program wywoła można zaktualizować zawartość paneli paska stanu dynamicznie w czasie wykonywania na podstawie zmian w stan aplikacji lub innych interakcji z użytkownikiem. Jest to często stosowana metoda sygnału użytkowników włączenia klucze, takie jak włączony klawisz CAPS LOCK, NUM LOCK lub blokady PRZEWIJANIA lub podaj datę lub zegara jako odwołanie wygodne.  
  
 W poniższym przykładzie użyje wystąpienia <xref:System.Windows.Forms.StatusBarPanel> klasy do obsługi zegara.  
  
### <a name="to-get-the-status-bar-ready-for-updating"></a>W celu przygotowania do aktualizacji paska stanu  
  
1.  Tworzenie nowego formularza systemu Windows.  
  
2.  Dodaj <xref:System.Windows.Forms.StatusBar> sterowania do formularza. Aby uzyskać więcej informacji, zobacz [porady: dodawanie formantów do formularzy systemu Windows](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).  
  
3.  Dodaj panelu paska stanu, aby Twoje <xref:System.Windows.Forms.StatusBar> formantu. Aby uzyskać więcej informacji, zobacz [porady: dodawanie paneli do formantu StatusBar](../../../../docs/framework/winforms/controls/how-to-add-panels-to-a-statusbar-control.md).  
  
4.  Aby uzyskać <xref:System.Windows.Forms.StatusBar> formant został dodany do formularza, ustaw <xref:System.Windows.Forms.StatusBar.ShowPanels%2A> właściwości `true`.  
  
5.  Dodawanie do formularzy systemu Windows <xref:System.Windows.Forms.Timer> składnika w formularzu.  
  
    > [!NOTE]
    >  Formularze systemu Windows <xref:System.Windows.Forms.Timer?displayProperty=nameWithType> składnika jest przeznaczony dla środowiska Windows Forms. Jeśli potrzebujesz czasomierza, które jest odpowiednie dla środowiska serwera, zobacz [wprowadzenie do serwerowych czasomierze](http://msdn.microsoft.com/library/adc0bc0a-a519-4812-bafc-fb9d1a5801fc).  
  
6.  Ustaw <xref:System.Windows.Forms.Timer.Enabled%2A> właściwości `true`.  
  
7.  Ustaw <xref:System.Windows.Forms.Timer.Interval%2A> właściwość <xref:System.Windows.Forms.Timer> na 30000.  
  
    > [!NOTE]
    >  <xref:System.Windows.Forms.Timer.Interval%2A> Właściwość <xref:System.Windows.Forms.Timer> składnika jest ustawiony na 30 sekund (30 000 w milisekundach), aby odzwierciedlane w czasie wyświetlane dokładnego czasu.  
  
### <a name="to-implement-the-timer-to-update-the-status-bar"></a>Aby zaimplementować czasomierza do aktualizacji paska stanu  
  
1.  Wstaw następujący kod do obsługi zdarzeń <xref:System.Windows.Forms.Timer> składnik do aktualizacji na panelu <xref:System.Windows.Forms.StatusBar> formantu.  
  
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
  
     W tym momencie można przystąpić do uruchamiania aplikacji i obserwować zegara działa w panelu paska stanu.  
  
### <a name="to-test-the-application"></a>Aby przetestować aplikację  
  
1.  Debugowanie aplikacji, a następnie naciśnij klawisz F5, aby uruchomić go. Aby uzyskać więcej informacji o debugowaniu, zobacz [debugowania w programie Visual Studio](/visualstudio/debugger/debugging-in-visual-studio).  
  
    > [!NOTE]
    >  Potrwa około 30 sekund na zegarze pojawią się w pasku stanu. To jest uzyskanie możliwe najdokładniejszych czasu. Z drugiej strony, aby zegara pojawić się wcześniej, można zmniejszyć wartość <xref:System.Windows.Forms.Timer.Interval%2A> właściwości można ustawić w kroku 7 w poprzedniej procedurze.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.StatusBar>  
 <xref:System.Windows.Forms.ToolStripStatusLabel>  
 [Instrukcje: dodawanie paneli do kontrolki StatusBar](../../../../docs/framework/winforms/controls/how-to-add-panels-to-a-statusbar-control.md)  
 [Instrukcje: ustalanie, który panel został kliknięty w kontrolce StatusBar formularzy Windows Forms](../../../../docs/framework/winforms/controls/determine-which-panel-wf-statusbar-control-was-clicked.md)  
 [StatusBar, kontrolka — omówienie](../../../../docs/framework/winforms/controls/statusbar-control-overview-windows-forms.md)
