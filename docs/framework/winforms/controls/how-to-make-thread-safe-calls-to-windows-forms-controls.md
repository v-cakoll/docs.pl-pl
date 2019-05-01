---
title: 'Instrukcje: Bezpieczne wątkowo wywołania kontrolek formularzy Windows Forms'
ms.date: 02/19/2019
dev_langs:
- csharp
- vb
f1_keywords:
- EHInvalidOperation.WinForms.IllegalCrossThreadCall
helpviewer_keywords:
- thread safety [Windows Forms], calling controls [Windows Forms]
- calling controls [Windows Forms], thread safety [Windows Forms]
- CheckForIllegalCrossThreadCalls property [Windows Forms]
- Windows Forms controls [Windows Forms], multithreading
- BackgroundWorker class [Windows Forms], examples
- threading [Windows Forms], cross-thread calls
- controls [Windows Forms], multithreading
ms.assetid: 138f38b6-1099-4fd5-910c-390b41cbad35
ms.openlocfilehash: 3211df1f0e585780039471b80b5b913613ad9bbd
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61913799"
---
# <a name="how-to-make-thread-safe-calls-to-windows-forms-controls"></a>Instrukcje: Bezpieczne wątkowo wywołania kontrolek formularzy Windows Forms

Wielowątkowość może poprawić wydajność aplikacji Windows Forms, ale dostęp do kontrolek formularzy Windows Forms jest natury metodą o bezpiecznych wątkach. Wielowątkowość udostępnić swój kod, aby bardzo poważne i złożone usterek. Dwa lub więcej wątków operowanie formantem można wymusić kontrolki w niespójnym stanie i prowadzić do Sytuacje wyścigu, zakleszczenia i zawiesza się lub zawiesza się. W przypadku zaimplementowania wielowątkowości w swojej aplikacji, należy koniecznie wywołania międzywątkowe formanty w sposób wątkowo. Aby uzyskać więcej informacji, zobacz [zarządzana wątkowość — najlepsze rozwiązania](../../../standard/threading/managed-threading-best-practices.md). 

Istnieją dwa sposoby, aby bezpiecznie wywołać formantu Windows Forms z wątku, który nie został utworzony tej kontrolki. Możesz użyć <xref:System.Windows.Forms.Control.Invoke%2A?displayProperty=fullName> metodę do wywołania delegata utworzone w wątku głównym, który z kolei wywołuje formantu. Lub możesz zaimplementować <xref:System.ComponentModel.BackgroundWorker?displayProperty=nameWithType>, który używa modelu oparte na zdarzeniach do rozdzielania pracy wykonanej w wątku w tle z raportowania na wyniki. 

## <a name="unsafe-cross-thread-calls"></a>Niebezpieczne wywołania międzywątkowe

Nie jest bezpieczne wywołanie formantu bezpośrednio z wątku, który nie jest utworzona. Poniższy fragment kodu ilustruje niebezpieczne wywołanie <xref:System.Windows.Forms.TextBox?displayProperty=nameWithType> kontroli. `Button1_Click` Programu obsługi zdarzeń tworzy nową `WriteTextUnsafe` wątku, który ustawia wątku głównego <xref:System.Windows.Forms.TextBox.Text%2A?displayProperty=nameWithType> właściwość bezpośrednio. 

```csharp
private void Button1_Click(object sender, EventArgs e)
{
    thread2 = new Thread(new ThreadStart(WriteTextUnsafe));
    thread2.Start();
}
private void WriteTextUnsafe()
{
    textBox1.Text = "This text was set unsafely.";
}
```

```vb
Private Sub Button1_Click(ByVal sender As Object, e As EventArgs) Handles Button1.Click
    Thread2 = New Thread(New ThreadStart(AddressOf WriteTextUnsafe))
    Thread2.Start()
End Sub

Private Sub WriteTextUnsafe()
    TextBox1.Text = "This text was set unsafely."
End Sub
```

Debuger programu Visual Studio wykryje te wywołania wątku niebezpieczne, tworząc <xref:System.InvalidOperationException> z wiadomością **międzywątkowe operacja jest nieprawidłowa. Kontrolka "" dostępne z wątku innego niż wątek został utworzony na.** <xref:System.InvalidOperationException> Zawsze występuje na niebezpieczny wywołania międzywątkowe podczas debugowania programu Visual Studio i może wystąpić w czasie wykonywania aplikacji. Należy rozwiązać ten problem, ale w przypadku wyłączenia wyjątku, ustawiając <xref:System.Windows.Forms.Control.CheckForIllegalCrossThreadCalls%2A?displayProperty=nameWithType> właściwość `false`.

## <a name="safe-cross-thread-calls"></a>Bezpieczne wywołania międzywątkowe 

Poniższe przykłady kodu ilustrują bezpiecznie wywołać formantu Windows Forms z wątku, który nie jest utworzona na dwa sposoby: 
1. <xref:System.Windows.Forms.Control.Invoke%2A?displayProperty=fullName> Metody, która wywołuje delegata z wątku głównego, aby wywołać formantu. 
2. A <xref:System.ComponentModel.BackgroundWorker?displayProperty=nameWithType> składnik, który oferuje model oparte na zdarzeniach. 

W obu przykładach sen wątku tła na sekundę do symulacji praca wykonywana w tym wątku. 

Można skompilować i uruchomić te przykłady jako aplikacji .NET Framework z C# lub wiersza polecenia programu Visual Basic. Aby uzyskać więcej informacji, zobacz [za pomocą wiersza polecenia przy użyciu csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md) lub [kompilacji z wiersza polecenia (Visual Basic)](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md). 

Począwszy od programu .NET Core 3.0 można również skompilować i uruchomić przykłady jako Windows aplikacje platformy .NET Core z folderu, który ma .NET Core Windows form  *\<nazwę folderu > .csproj* pliku projektu. 

## <a name="example-use-the-invoke-method-with-a-delegate"></a>Przykład: Metody Invoke za pomocą delegata

W poniższym przykładzie pokazano wzorzec zapewniających wątkowo wywołania do formantu Windows Forms. Wykonuje kwerendę <xref:System.Windows.Forms.Control.InvokeRequired%2A?displayProperty=fullName> właściwość, która porównuje kontrolki przez tworzenie identyfikator wątku do wywoływania identyfikator wątku. Jeśli identyfikatory wątku są takie same, wywołuje metodę formantu bezpośrednio. Jeśli identyfikatory wątku są różne, wywołuje metodę <xref:System.Windows.Forms.Control.Invoke%2A?displayProperty=nameWithType> metody delegata w wątku głównym, co sprawia, że to rzeczywiste wywołanie do formantu.

`SafeCallDelegate` Umożliwia ustawienie <xref:System.Windows.Forms.TextBox> kontrolki <xref:System.Windows.Forms.TextBox.Text%2A> właściwości. `WriteTextSafe` Zapytania metody <xref:System.Windows.Forms.Control.InvokeRequired%2A>. Jeśli <xref:System.Windows.Forms.Control.InvokeRequired%2A> zwraca `true`, `WriteTextSafe` przekazuje `SafeCallDelegate` do <xref:System.Windows.Forms.Control.Invoke%2A> metody to rzeczywiste wywołanie do formantu. Jeśli <xref:System.Windows.Forms.Control.InvokeRequired%2A> zwraca `false`, `WriteTextSafe` ustawia <xref:System.Windows.Forms.TextBox.Text%2A?displayProperty=nameWithType> bezpośrednio. `Button1_Click` Programu obsługi zdarzeń tworzy nowy wątek i uruchamia `WriteTextSafe` metody. 

 [!code-csharp[ThreadSafeCalls#1](~/samples/snippets/winforms/thread-safe/example1/cs/Form1.cs)]
 [!code-vb[ThreadSafeCalls#1](~/samples/snippets/winforms/thread-safe/example1/vb/Form1.vb)]  

## <a name="example-use-a-backgroundworker-event-handler"></a>Przykład: Użyj obsługi zdarzeń BackgroundWorker

Łatwe Implementowanie wielowątkowości jest <xref:System.ComponentModel.BackgroundWorker?displayProperty=nameWithType> składnik, który używa modelu oparte na zdarzeniach. Jest uruchamiane w wątku w tle <xref:System.ComponentModel.BackgroundWorker.DoWork?displayProperty=nameWithType> zdarzenie, które nie wchodzi w interakcje z wątku głównego. Główny wątek uruchamia <xref:System.ComponentModel.BackgroundWorker.ProgressChanged?displayProperty=nameWithType> i <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted?displayProperty=nameWithType> uchwytów zdarzeń, które można wywołać formantów wątku głównego.

Aby wywołać wątków przy użyciu <xref:System.ComponentModel.BackgroundWorker>, utworzyć metodę w wątku tła, które wykonają tę pracę i powiązać <xref:System.ComponentModel.BackgroundWorker.DoWork> zdarzeń. Tworzenie innej metody w wątku głównym, aby raportuje o wynikach pracę w tle i powiązać <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> lub <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> zdarzeń. Aby uruchomić wątku w tle, należy wywołać <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A?displayProperty=nameWithType>. 

W przykładzie użyto <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> programu obsługi zdarzeń, aby ustawić <xref:System.Windows.Forms.TextBox> kontrolki <xref:System.Windows.Forms.TextBox.Text%2A> właściwości. Aby uzyskać przykłady dotyczące używania <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> zdarzeń, zobacz <xref:System.ComponentModel.BackgroundWorker>. 

 [!code-csharp[ThreadSafeCalls#2](~/samples/snippets/winforms/thread-safe/example2/cs/Form1.cs)]
 [!code-vb[ThreadSafeCalls#2](~/samples/snippets/winforms/thread-safe/example2/vb/Form1.vb)]  

## <a name="see-also"></a>Zobacz także

- <xref:System.ComponentModel.BackgroundWorker>
- [Instrukcje: Uruchamianie operacji w tle](how-to-run-an-operation-in-the-background.md)
- [Instrukcje: Implementowanie formularza korzystającego z operacji w tle](how-to-implement-a-form-that-uses-a-background-operation.md)
- [Tworzenie niestandardowych formantów Windows Forms za pomocą programu .NET Framework](developing-custom-windows-forms-controls.md)
