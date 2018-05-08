---
title: 'Porady: uruchamianie procedur w ustalonych odstępach czasu za pomocą składnika Timer formularzy systemu Windows'
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
ms.openlocfilehash: 58ad0578f478b5cbc1d2a263fdf6b14b4555a339
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-run-procedures-at-set-intervals-with-the-windows-forms-timer-component"></a>Porady: uruchamianie procedur w ustalonych odstępach czasu za pomocą składnika Timer formularzy systemu Windows
Czasami można utworzyć procedury, która działa w określonych odstępach czasu, aż do pętli zostało zakończone lub uruchamiany po upłynięciu interwału czasu zestawu. <xref:System.Windows.Forms.Timer> Składnika umożliwia takiej procedury.  
  
 Ten składnik jest przeznaczony dla środowiska Windows Forms. Jeśli potrzebujesz czasomierza, które jest odpowiednie dla środowiska serwera, zobacz [wprowadzenie do serwerowych czasomierze](http://msdn.microsoft.com/library/adc0bc0a-a519-4812-bafc-fb9d1a5801fc).  
  
> [!NOTE]
>  Istnieją pewne ograniczenia w przypadku korzystania z <xref:System.Windows.Forms.Timer> składnika. Aby uzyskać więcej informacji, zobacz [ograniczenia właściwości Interval składnika Timer formularzy systemu Windows](../../../../docs/framework/winforms/controls/limitations-of-the-timer-component-interval-property.md).  
  
### <a name="to-run-a-procedure-at-set-intervals-with-the-timer-component"></a>Aby uruchomić procedurę w ustalonych odstępach czasu za pomocą składnika czasomierza  
  
1.  Dodaj <xref:System.Windows.Forms.Timer> do formularza. Zobacz następującą sekcję przykład ilustrację jak to zrobić programowo. Visual Studio ma również obsługę dodawania składników do formularza. Zobacz też [porady: dodawanie formantów bez interfejsu użytkownika do formularzy systemu Windows](http://msdn.microsoft.com/library/becyw7bz\(v=vs.110\)).  
  
2.  Ustaw <xref:System.Windows.Forms.Timer.Interval%2A> właściwości (w milisekundach) dla czasomierza. Ta właściwość określa czas, jaki upłynie procedura jest uruchamiana ponownie.  
  
    > [!NOTE]
    >  Im bardziej często występuje zdarzenie czasomierza, więcej czasu procesora jest używany w odpowiedzi na zdarzenia. Może to spowolnić ogólną wydajność. Nie ustawiaj przedział mniejsze niż to konieczne.  
  
3.  Zapisywanie odpowiedni kod w <xref:System.Windows.Forms.Timer.Tick> obsługi zdarzeń. Kod zapisu w takim przypadku zostanie uruchomiony w interwale określonym w <xref:System.Windows.Forms.Timer.Interval%2A> właściwości.  
  
4.  Ustaw <xref:System.Windows.Forms.Timer.Enabled%2A> właściwości `true` uruchomić czasomierza. <xref:System.Windows.Forms.Timer.Tick> Zdarzenia będą uruchamiane było, procedura w określonych interwałach.  
  
5.  W odpowiednim czasie, należy ustawić <xref:System.Windows.Forms.Timer.Enabled%2A> właściwości `false` przestanie procedury z ponownym uruchomieniem. Ustawienie interwału `0` nie powoduje czasomierza zatrzymać.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie pierwsze kodu śledzi porę dnia, w przyrostach sekundę. Używa <xref:System.Windows.Forms.Button>, <xref:System.Windows.Forms.Label>, a <xref:System.Windows.Forms.Timer> składnika w formularzu. <xref:System.Windows.Forms.Timer.Interval%2A> Właściwości ustawiono wartość 1000 (równą jednej sekundzie). W <xref:System.Windows.Forms.Timer.Tick> zdarzenia podpis etykiety ustawiono bieżący czas. Po kliknięciu przycisku <xref:System.Windows.Forms.Timer.Enabled%2A> właściwość jest ustawiona na `false`, zatrzymanie czasomierza aktualizuje podpis etykiety. Poniższy przykład kodu wymaga formularza z <xref:System.Windows.Forms.Button> formantu o nazwie `Button1`, <xref:System.Windows.Forms.Timer> formantu o nazwie `Timer1`, a <xref:System.Windows.Forms.Label> formantu o nazwie `Label1`.  
  
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
 Ta druga przykładowy kod uruchamia procedurę co 600 milisekund do momentu zakończenia pętli. Poniższy przykład kodu wymaga formularza z <xref:System.Windows.Forms.Button> formantu o nazwie `Button1`, <xref:System.Windows.Forms.Timer> formantu o nazwie `Timer1`, a <xref:System.Windows.Forms.Label> formantu o nazwie `Label1`.  
  
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
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.Timer>  
 [Timer, składnik](../../../../docs/framework/winforms/controls/timer-component-windows-forms.md)  
 [Timer, składnik — omówienie](../../../../docs/framework/winforms/controls/timer-component-overview-windows-forms.md)
