---
title: 'Przewodnik: Aktualizowanie informacji na pasku stanu w czasie wykonywania'
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
ms.openlocfilehash: 3de554d4c8c3963948159bc6b8c2196f9ebc10ad
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54745886"
---
# <a name="walkthrough-updating-status-bar-information-at-run-time"></a>Przewodnik: Aktualizowanie informacji na pasku stanu w czasie wykonywania
> [!IMPORTANT]
>  <xref:System.Windows.Forms.StatusStrip> i <xref:System.Windows.Forms.ToolStripStatusLabel> kontrolki Zastąp i dodawania funkcjonalności do <xref:System.Windows.Forms.StatusBar> i <xref:System.Windows.Forms.StatusBarPanel> kontroluje; jednak <xref:System.Windows.Forms.StatusBar> i <xref:System.Windows.Forms.StatusBarPanel> kontrolek zostaną zachowane dla zgodności z poprzednimi wersjami i użycia w przyszłości, jeśli możesz Wybierz.  
  
 Często program będzie wywoływać parametr dla aktualizacji zawartości paneli paska stanu dynamicznie w czasie wykonywania, na podstawie zmian do stanu aplikacji lub innych interakcji z użytkownikiem. Jest to często stosowaną metodą sygnał użytkownikom włączenie kluczy, takie jak włączony klawisz CAPS LOCK, NUM LOCK lub SCROLL LOCK lub podaj datę lub zegara jako odwołanie wygodne.  
  
 W poniższym przykładzie użyjesz wystąpienie <xref:System.Windows.Forms.StatusBarPanel> klasy do hostowania zegara.  
  
### <a name="to-get-the-status-bar-ready-for-updating"></a>Aby uzyskać gotowe do aktualizacji paska stanu  
  
1.  Tworzenie nowego formularza Windows.  
  
2.  Dodaj <xref:System.Windows.Forms.StatusBar> formantu do formularza. Aby uzyskać więcej informacji, zobacz [jak: Dodawanie formantów do formularzy Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).  
  
3.  Dodawanie panelu pasek stanu, aby Twoje <xref:System.Windows.Forms.StatusBar> kontroli. Aby uzyskać więcej informacji, zobacz [jak: Dodawanie paneli do kontrolki StatusBar](../../../../docs/framework/winforms/controls/how-to-add-panels-to-a-statusbar-control.md).  
  
4.  Aby uzyskać <xref:System.Windows.Forms.StatusBar> formant został dodany do formularza, ustaw <xref:System.Windows.Forms.StatusBar.ShowPanels%2A> właściwość `true`.  
  
5.  Dodawanie formularzy Windows <xref:System.Windows.Forms.Timer> składnika do formularza.  
  
    > [!NOTE]
    >  Formularze Windows <xref:System.Windows.Forms.Timer?displayProperty=nameWithType> składnik jest przeznaczony dla środowiska Windows Forms. Jeśli potrzebujesz czasomierza, która jest odpowiednia w środowisku serwera, zobacz [wprowadzenie do serwerowych czasomierzy](https://msdn.microsoft.com/library/adc0bc0a-a519-4812-bafc-fb9d1a5801fc).  
  
6.  Ustaw <xref:System.Windows.Forms.Timer.Enabled%2A> właściwość `true`.  
  
7.  Ustaw <xref:System.Windows.Forms.Timer.Interval%2A> właściwość <xref:System.Windows.Forms.Timer> na 30000.  
  
    > [!NOTE]
    >  <xref:System.Windows.Forms.Timer.Interval%2A> Właściwość <xref:System.Windows.Forms.Timer> składnika jest ustawiony na 30 sekund (30 000 milisekund), aby upewnić się, że dokładnego czasu jest odzwierciedlana w czasie wyświetlane.  
  
### <a name="to-implement-the-timer-to-update-the-status-bar"></a>Aby zaimplementować czasomierza do aktualizacji paska stanu  
  
1.  Wstaw następujący kod do programu obsługi zdarzeń z <xref:System.Windows.Forms.Timer> składnik do aktualizacji na panelu <xref:System.Windows.Forms.StatusBar> kontroli.  
  
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
  
     W tym momencie można przystąpić do uruchomienia aplikacji i obserwuj zegara działa w panelu pasek stanu.  
  
### <a name="to-test-the-application"></a>Aby przetestować aplikację  
  
1.  Debugowanie aplikacji, a następnie naciśnij klawisz F5, aby go uruchomić. Aby uzyskać szczegółowe informacje o debugowaniu, zobacz [debugowania w programie Visual Studio](/visualstudio/debugger/debugging-in-visual-studio).  
  
    > [!NOTE]
    >  Potrwa około 30 sekund w przypadku zegara pojawią się w pasku stanu. To jest uzyskanie czas najdokładniejszych możliwe. Z drugiej strony, aby zegar pojawić się wcześniej, można zmniejszyć wartość <xref:System.Windows.Forms.Timer.Interval%2A> właściwości ustawionej w kroku 7 w poprzedniej procedurze.  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Windows.Forms.StatusBar>
- <xref:System.Windows.Forms.ToolStripStatusLabel>
- [Instrukcje: Dodawanie paneli do formantu StatusBar](../../../../docs/framework/winforms/controls/how-to-add-panels-to-a-statusbar-control.md)
- [Instrukcje: Określanie, które panelu w formancie StatusBar formularzy Windows został kliknięty](../../../../docs/framework/winforms/controls/determine-which-panel-wf-statusbar-control-was-clicked.md)
- [StatusBar, kontrolka — omówienie](../../../../docs/framework/winforms/controls/statusbar-control-overview-windows-forms.md)
