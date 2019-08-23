---
title: 'Przewodnik: aktualizowanie informacji na pasku stanu w czasie wykonywania'
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
ms.openlocfilehash: 670746a1b964a85bc5136d976d831c6848466797
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69930985"
---
# <a name="walkthrough-updating-status-bar-information-at-run-time"></a>Przewodnik: aktualizowanie informacji na pasku stanu w czasie wykonywania
> [!IMPORTANT]
> <xref:System.Windows.Forms.StatusBarPanel> <xref:System.Windows.Forms.StatusBarPanel> <xref:System.Windows.Forms.StatusBar> <xref:System.Windows.Forms.StatusBar> Formanty i zastępują i dodają funkcje do kontrolek i, natomiast kontrolki i są zachowywane w celu zapewnienia zgodności z poprzednimi wersjami i w przyszłości. <xref:System.Windows.Forms.StatusStrip> <xref:System.Windows.Forms.ToolStripStatusLabel> następnie.  
  
 Często program będzie wywoływał, aby zaktualizować zawartość paneli paska stanu dynamicznie w czasie wykonywania, na podstawie zmian stanu aplikacji lub innej interakcji z użytkownikiem. Jest to typowy sposób, aby sygnalizować użytkownikom, że klucze takie jak Caps Lock, NUM LOCK lub SCROLL LOCK są włączone, lub podać datę lub zegar jako wygodne odwołanie.  
  
 W poniższym przykładzie zostanie użyte wystąpienie <xref:System.Windows.Forms.StatusBarPanel> klasy do hostowania zegara.  
  
### <a name="to-get-the-status-bar-ready-for-updating"></a>Aby wyświetlić pasek stanu gotowy do aktualizacji  
  
1. Utwórz nowy formularz systemu Windows.  
  
2. <xref:System.Windows.Forms.StatusBar> Dodaj kontrolkę do formularza. Aby uzyskać szczegółowe informacje [, zobacz How to: Dodaj formanty do Windows Forms](how-to-add-controls-to-windows-forms.md).  
  
3. Dodaj panel paska stanu do <xref:System.Windows.Forms.StatusBar> kontrolki. Aby uzyskać szczegółowe informacje [, zobacz How to: Dodaj panele do kontrolki](how-to-add-panels-to-a-statusbar-control.md)StatusBar.  
  
4. Dla kontrolki dodanej do formularza <xref:System.Windows.Forms.StatusBar.ShowPanels%2A> ustaw właściwość na `true`. <xref:System.Windows.Forms.StatusBar>  
  
5. Dodaj składnik Windows Forms <xref:System.Windows.Forms.Timer> do formularza.  
  
    > [!NOTE]
    > Składnik Windows Forms <xref:System.Windows.Forms.Timer?displayProperty=nameWithType> jest przeznaczony dla środowiska Windows Forms. Jeśli potrzebujesz czasomierza odpowiedniego dla środowiska serwera, zobacz [wprowadzenie do czasomierzy oparte na serwerze](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/tb9yt5e6(v=vs.90)).  
  
6. Ustaw <xref:System.Windows.Forms.Timer.Enabled%2A> właściwość `true`.  
  
7. <xref:System.Windows.Forms.Timer.Interval%2A> Ustaw właściwość <xref:System.Windows.Forms.Timer> na 30000.  
  
    > [!NOTE]
    > <xref:System.Windows.Forms.Timer.Interval%2A> Właściwość<xref:System.Windows.Forms.Timer> składnika jest ustawiana na 30 sekund (30 000 milisekund), aby mieć pewność, że dokładny czas zostanie odzwierciedlony w wyświetlonym czasie.  
  
### <a name="to-implement-the-timer-to-update-the-status-bar"></a>Aby zaimplementować czasomierz w celu zaktualizowania paska stanu  
  
1. Wstaw następujący kod do procedury obsługi <xref:System.Windows.Forms.Timer> zdarzeń składnika, aby zaktualizować panel <xref:System.Windows.Forms.StatusBar> kontrolki.  
  
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
  
1. Debuguj aplikację i naciśnij klawisz F5, aby ją uruchomić. Aby uzyskać szczegółowe informacje o debugowaniu, zobacz [debugowanie w programie Visual Studio](/visualstudio/debugger/debugging-in-visual-studio).  
  
    > [!NOTE]
    > Zegar będzie wyświetlany na pasku stanu przez około 30 sekund. Jest to najlepszy możliwy czas. Z drugiej strony, aby zegar pojawił się wcześniej, można zmniejszyć wartość <xref:System.Windows.Forms.Timer.Interval%2A> właściwości ustawionej w kroku 7 w poprzedniej procedurze.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.StatusBar>
- <xref:System.Windows.Forms.ToolStripStatusLabel>
- [Instrukcje: Dodawanie paneli do kontrolki StatusBar](how-to-add-panels-to-a-statusbar-control.md)
- [Instrukcje: Określ, który panel w Windows Forms kontrolce StatusBar został kliknięty](determine-which-panel-wf-statusbar-control-was-clicked.md)
- [StatusBar, kontrolka — omówienie](statusbar-control-overview-windows-forms.md)
