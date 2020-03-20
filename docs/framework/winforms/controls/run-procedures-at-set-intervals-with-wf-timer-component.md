---
title: Uruchamianie procedur w regularnych interwałach ze składnikiem czasomierza
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
ms.openlocfilehash: 52d68a8136551384f67ff6232799600af09f8b66
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182064"
---
# <a name="how-to-run-procedures-at-set-intervals-with-the-windows-forms-timer-component"></a>Porady: uruchamianie procedur w ustalonych odstępach czasu za pomocą składnika Timer formularzy systemu Windows
Czasami można utworzyć procedurę, która jest uruchamiana w określonych odstępach czasu, dopóki pętla nie zakończy się lub która jest uruchamiana po upływie ustawionego przedziału czasu. Składnik <xref:System.Windows.Forms.Timer> umożliwia taką procedurę.  
  
 Ten składnik jest przeznaczony dla środowiska Windows Forms. Jeśli potrzebujesz timera, który jest odpowiedni dla środowiska serwera, zobacz [Wprowadzenie do czasomierzy opartych na serwerze](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/tb9yt5e6(v=vs.90)).  
  
> [!NOTE]
> Istnieją pewne ograniczenia podczas <xref:System.Windows.Forms.Timer> korzystania ze składnika. Aby uzyskać więcej informacji, zobacz [Ograniczenia właściwości Interval składnika windows forms](limitations-of-the-timer-component-interval-property.md).  
  
## <a name="to-run-a-procedure-at-set-intervals-with-the-timer-component"></a>Aby uruchomić procedurę w ustalonych odstępach czasu za pomocą składnika Timer  
  
1. Dodaj <xref:System.Windows.Forms.Timer> a do formularza. Zobacz poniższą sekcję przykładu, aby dowiedzieć się, jak to zrobić programowo. Visual Studio ma również obsługę dodawania składników do formularza. Zobacz [też: Jak: Dodawanie formantów bez interfejsu użytkownika do formularzy systemu Windows](how-to-add-controls-without-a-user-interface-to-windows-forms.md).  
  
2. Ustaw <xref:System.Windows.Forms.Timer.Interval%2A> właściwość (w milisekundach) dla czasomierza. Ta właściwość określa, ile czasu minie, zanim procedura zostanie ponownie uruchomiony.  
  
    > [!NOTE]
    > Im częściej występuje zdarzenie czasomierza, tym więcej czasu procesora jest używane w odpowiedzi na zdarzenie. Może to spowolnić ogólną wydajność. Nie należy ustawiać mniejszego interwału niż jest to konieczne.  
  
3. Napisz odpowiedni kod <xref:System.Windows.Forms.Timer.Tick> w programie obsługi zdarzeń. Kod, który piszesz w tym zdarzeniu <xref:System.Windows.Forms.Timer.Interval%2A> będzie uruchamiany w interwale określonym we właściwości.  
  
4. Ustaw <xref:System.Windows.Forms.Timer.Enabled%2A> właściwość, aby `true` uruchomić czasomierz. Zdarzenie <xref:System.Windows.Forms.Timer.Tick> rozpocznie się, uruchomienie procedury w określonym przedziale czasu.  
  
5. W odpowiednim czasie ustaw <xref:System.Windows.Forms.Timer.Enabled%2A> właściwość, aby `false` zatrzymać procedurę ponownie uruchomione. Ustawienie interwału na `0` nie powoduje zatrzymania czasomierza.  
  
## <a name="example"></a>Przykład  
 Ten przykład pierwszego kodu śledzi porę dnia w przyrostach jednosekundowych. Używa , <xref:System.Windows.Forms.Button>a <xref:System.Windows.Forms.Label>, i <xref:System.Windows.Forms.Timer> składnika w formularzu. Właściwość jest ustawiona <xref:System.Windows.Forms.Timer.Interval%2A> na 1000 (równa jednej sekundzie). W <xref:System.Windows.Forms.Timer.Tick> przypadku, podpis etykiety jest ustawiona na bieżący czas. Po kliknięciu przycisku, <xref:System.Windows.Forms.Timer.Enabled%2A> właściwość `false`jest ustawiona na , zatrzymując czasomierz z aktualizowaniem podpisu etykiety. Poniższy przykład kodu wymaga, aby <xref:System.Windows.Forms.Button> masz `Button1`formularz <xref:System.Windows.Forms.Timer> z `Timer1`formantem <xref:System.Windows.Forms.Label> o `Label1`nazwie, formantem o nazwie i formantem o nazwie .  
  
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
 Ten przykład drugiego kodu uruchamia procedurę co 600 milisekund, dopóki nie zakończy się pętla. Poniższy przykład kodu wymaga, aby <xref:System.Windows.Forms.Button> masz `Button1`formularz <xref:System.Windows.Forms.Timer> z `Timer1`formantem <xref:System.Windows.Forms.Label> o `Label1`nazwie, formantem o nazwie i formantem o nazwie .  
  
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

- <xref:System.Windows.Forms.Timer>
- [Timer, składnik](timer-component-windows-forms.md)
- [Timer — Informacje o składniku](timer-component-overview-windows-forms.md)
