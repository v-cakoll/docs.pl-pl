---
title: 'Instrukcje: uruchamianie procedur w ustalonych odstępach czasu za pomocą składnika Timer formularzy systemu Windows'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- examples [Windows Forms], timers
- timers [Windows Forms], event intervals
- initialization [Windows Forms], Timer components
- timers [Windows Forms], Windows-based
- Timer component [Windows Forms], initializing
- procedures [Windows Forms], specific time intervals
ms.assetid: 8025247a-2de4-4d86-b8ab-a8cb8aeab2ea
ms.openlocfilehash: 9900b96bf04668805b841c842f7c625b86e76d39
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69960550"
---
# <a name="how-to-run-procedures-at-set-intervals-with-the-windows-forms-timer-component"></a>Instrukcje: uruchamianie procedur w ustalonych odstępach czasu za pomocą składnika Timer formularzy systemu Windows
Czasami warto utworzyć procedurę, która jest uruchamiana w określonych przedziałach czasowych, dopóki pętla nie zostanie zakończona lub uruchomiona, gdy upłynie ustawiony interwał czasu. Składnik <xref:System.Windows.Forms.Timer> ten wykonuje taką procedurę.  
  
 Ten składnik jest przeznaczony dla środowiska Windows Formsowego. Jeśli potrzebujesz czasomierza odpowiedniego dla środowiska serwera, zobacz [wprowadzenie do czasomierzy oparte na serwerze](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/tb9yt5e6(v=vs.90)).  
  
> [!NOTE]
> Korzystanie z <xref:System.Windows.Forms.Timer> składnika ma pewne ograniczenia. Aby uzyskać więcej informacji, zobacz [ograniczenia właściwości Interval składnika czasomierza Windows Forms](limitations-of-the-timer-component-interval-property.md).  
  
## <a name="to-run-a-procedure-at-set-intervals-with-the-timer-component"></a>Aby uruchomić procedurę w ustalonych odstępach czasu za pomocą składnika Timer  
  
1. <xref:System.Windows.Forms.Timer> Dodaj do formularza. Zapoznaj się z poniższą sekcją przykładową, aby zapoznać się z tym, jak to zrobić programowo. Program Visual Studio obsługuje także dodawanie składników do formularza. Zapoznaj [się również z tematem: Dodaj kontrolki bez interfejsu użytkownika do Windows Forms](how-to-add-controls-without-a-user-interface-to-windows-forms.md).  
  
2. <xref:System.Windows.Forms.Timer.Interval%2A> Ustaw właściwość (w milisekundach) dla czasomierza. Ta właściwość określa, ile czasu będzie upłynąć przed ponownym uruchomieniem procedury.  
  
    > [!NOTE]
    > Im częściej występuje zdarzenie czasomierza, tym więcej czasu procesora jest używany w odpowiedzi na zdarzenie. Może to spowolnić ogólną wydajność. Nie ustawiaj interwału krótszego niż jest to potrzebne.  
  
3. Zapisz odpowiedni kod w programie <xref:System.Windows.Forms.Timer.Tick> obsługi zdarzeń. Kod napisany w tym zdarzeniu będzie uruchamiany z interwałem określonym we <xref:System.Windows.Forms.Timer.Interval%2A> właściwości.  
  
4. Ustaw właściwość na `true` , aby uruchomić czasomierz. <xref:System.Windows.Forms.Timer.Enabled%2A> <xref:System.Windows.Forms.Timer.Tick> Zdarzenie rozpocznie się, uruchamiając procedurę w określonym interwale.  
  
5. W odpowiednim momencie Ustaw <xref:System.Windows.Forms.Timer.Enabled%2A> właściwość na `false` , aby zatrzymać procedurę od nowa. Ustawienie interwału `0` nie powoduje zatrzymania czasomierza.  
  
## <a name="example"></a>Przykład  
 Ten pierwszy przykład kodu śledzi godzinę pierwszego przyrostu. Używa <xref:System.Windows.Forms.Button>elementu <xref:System.Windows.Forms.Timer> , a i składnika w formularzu. <xref:System.Windows.Forms.Label> <xref:System.Windows.Forms.Timer.Interval%2A> Właściwość jest ustawiona na 1000 (równa 1 sekunda). W takim <xref:System.Windows.Forms.Timer.Tick> przypadku podpis etykiety jest ustawiany na bieżącą godzinę. Gdy przycisk zostanie kliknięty, <xref:System.Windows.Forms.Timer.Enabled%2A> właściwość jest ustawiona na, zatrzymywanie czasomierza w celu `false`zaktualizowania napisu etykiety. Poniższy przykład kodu wymaga <xref:System.Windows.Forms.Button> formularza z kontrolką o nazwie `Button1`, <xref:System.Windows.Forms.Timer> kontrolce o nazwie `Timer1`i <xref:System.Windows.Forms.Label> kontrolki o nazwie `Label1`.  
  
```vb  
Private Sub InitializeTimer()  
   ' Run this procedure in an appropriate event.  
   ' Set to 1 second.  
   Timer1.Interval = 1000  
   ' Enable timer.  
   Timer1.Enabled = True  
   Button1.Text = "Enabled"  
End Sub  
x  
Private Sub Timer1_Tick(ByVal Sender As Object, ByVal e As EventArgs) Handles Timer1.Tick  
' Set the caption to the current time.  
   Label1.Text = DateTime.Now  
End Sub  
  
Private Sub Button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Button1.Click  
      If Button1.Text = "Stop" Then  
         Button1.Text = "Start"  
         Timer1.Enabled = False  
      Else  
         Button1.Text = "Stop"  
         Timer1.Enabled = True  
      End If  
End Sub  
```  
  
```csharp  
private void InitializeTimer()  
{  
    // Call this procedure when the application starts.  
    // Set to 1 second.  
    Timer1.Interval = 1000;  
    Timer1.Tick += new EventHandler(Timer1_Tick);  
  
    // Enable timer.  
    Timer1.Enabled = true;  
  
    Button1.Text = "Stop";  
    Button1.Click += new EventHandler(Button1_Click);  
}  
  
private void Timer1_Tick(object Sender, EventArgs e)     
{  
   // Set the caption to the current time.  
   Label1.Text = DateTime.Now.ToString();  
}  
  
private void Button1_Click(object sender, EventArgs e)  
{  
  if ( Button1.Text == "Stop" )  
  {  
    Button1.Text = "Start";  
    Timer1.Enabled = false;  
  }  
  else  
  {  
    Button1.Text = "Stop";  
    Timer1.Enabled = true;  
  }  
}  
```  
  
```cpp  
private:  
   void InitializeTimer()  
   {  
      // Run this procedure in an appropriate event.  
      // Set to 1 second.  
      timer1->Interval = 1000;  
      // Enable timer.  
      timer1->Enabled = true;  
      this->timer1->Tick += gcnew System::EventHandler(this,    
                               &Form1::timer1_Tick);  
  
      button1->Text = S"Stop";  
      this->button1->Click += gcnew System::EventHandler(this,   
                               &Form1::button1_Click);  
   }  
  
   void timer1_Tick(System::Object ^ sender,  
      System::EventArgs ^ e)  
   {  
      // Set the caption to the current time.  
      label1->Text = DateTime::Now.ToString();  
   }  
  
   void button1_Click(System::Object ^ sender,  
      System::EventArgs ^ e)  
   {  
      if ( button1->Text == "Stop" )  
      {  
         button1->Text = "Start";  
         timer1->Enabled = false;  
      }  
      else  
      {  
         button1->Text = "Stop";  
         timer1->Enabled = true;  
      }  
   }  
```  
  
## <a name="example"></a>Przykład  
 Ten drugi przykład kodu uruchamia procedurę co 600 milisekund do momentu zakończenia pętli. Poniższy przykład kodu wymaga <xref:System.Windows.Forms.Button> formularza z kontrolką o nazwie `Button1`, <xref:System.Windows.Forms.Timer> kontrolce o nazwie `Timer1`i <xref:System.Windows.Forms.Label> kontrolki o nazwie `Label1`.  
  
```vb  
' This variable will be the loop counter.  
Private counter As Integer  
  
Private Sub InitializeTimer()  
   ' Run this procedure in an appropriate event.  
   counter = 0  
   Timer1.Interval = 600  
   Timer1.Enabled = True  
End Sub  
  
Private Sub Timer1_Tick(ByVal sender As Object, ByVal e As System.EventArgs) Handles Timer1.Tick  
   If counter => 10 Then  
      ' Exit loop code.  
      Timer1.Enabled = False  
      counter = 0  
   Else  
      ' Run your procedure here.  
      ' Increment counter.  
      counter = counter + 1  
      Label1.Text = "Procedures Run: " & counter.ToString  
   End If  
End Sub  
```  
  
```csharp  
// This variable will be the loop counter.  
private int counter;  
  
private void InitializeTimer()  
{  
   // Run this procedure in an appropriate event.  
   counter = 0;  
   timer1.Interval = 600;  
   timer1.Enabled = true;  
   // Hook up timer's tick event handler.  
   this.timer1.Tick += new System.EventHandler(this.timer1_Tick);  
}  
  
private void timer1_Tick(object sender, System.EventArgs e)     
{  
   if (counter >= 10)   
   {  
      // Exit loop code.  
      timer1.Enabled = false;  
      counter = 0;  
   }  
   else  
   {  
      // Run your procedure here.  
      // Increment counter.  
      counter = counter + 1;  
      label1.Text = "Procedures Run: " + counter.ToString();  
      }  
}  
```  
  
```cpp  
private:  
   int counter;  
  
   void InitializeTimer()  
   {  
      // Run this procedure in an appropriate event.  
      counter = 0;  
      timer1->Interval = 600;  
      timer1->Enabled = true;  
      // Hook up timer's tick event handler.  
      this->timer1->Tick += gcnew System::EventHandler(this, &Form1::timer1_Tick);  
   }  
  
   void timer1_Tick(System::Object ^ sender,  
      System::EventArgs ^ e)  
   {  
      if (counter >= 10)   
      {  
         // Exit loop code.  
         timer1->Enabled = false;  
         counter = 0;  
      }  
      else  
      {  
         // Run your procedure here.  
         // Increment counter.  
         counter = counter + 1;  
         label1->Text = String::Concat("Procedures Run: ",  
            counter.ToString());  
      }  
   }  
```  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.Timer>
- [Timer, składnik](timer-component-windows-forms.md)
- [Timer, składnik — omówienie](timer-component-overview-windows-forms.md)
