---
title: 'Instrukcje: Ustaw bezpieczne dla wątków wywołania formantów Windows Forms'
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
ms.openlocfilehash: 78ad7b16d5220972a61848c0c80cd884afa842d9
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70928614"
---
# <a name="how-to-make-thread-safe-calls-to-windows-forms-controls"></a>Instrukcje: Ustaw bezpieczne dla wątków wywołania formantów Windows Forms

Wielowątkowość może zwiększyć wydajność aplikacji Windows Forms, ale dostęp do kontrolek Windows Forms nie jest ze względu bezpieczny wątkowo. Wielowątkowość może uwidaczniać kod do bardzo poważnych i złożonych błędów. Co najmniej dwa wątki manipulowania kontrolką mogą wymusić niespójność kontroli i prowadzić do warunków wyścigu, zakleszczeniów i zawieszania się lub zawieszenia. W przypadku zaimplementowania wielowątkowości w aplikacji należy zadbać o to, aby w sposób bezpieczny wątkowo wywoływać kontrolki międzywątkowe. Aby uzyskać więcej informacji, zobacz temat [zarządzane wątki z najlepszymi rozwiązaniami](../../../standard/threading/managed-threading-best-practices.md). 

Istnieją dwa sposoby bezpiecznego wywołania formantu Windows Forms z wątku, który nie utworzył tego formantu. Można użyć <xref:System.Windows.Forms.Control.Invoke%2A?displayProperty=fullName> metody do wywołania delegata utworzonego w wątku głównym, który z kolei wywołuje formant. Lub, można zaimplementować a <xref:System.ComponentModel.BackgroundWorker?displayProperty=nameWithType>, który używa modelu sterowanego zdarzeniami, do rozdzielenia pracy wykonanej w wątku w tle z raportowaniem wyników. 

## <a name="unsafe-cross-thread-calls"></a>Niebezpieczne wywołania między wątkami

Wywołanie formantu bezpośrednio z wątku, który nie został utworzony, jest niebezpieczne. Poniższy fragment kodu ilustruje niebezpieczne wywołanie do <xref:System.Windows.Forms.TextBox?displayProperty=nameWithType> kontrolki. Program obsługi `WriteTextUnsafe` zdarzeń tworzy nowy wątek, który <xref:System.Windows.Forms.TextBox.Text%2A?displayProperty=nameWithType> ustawia właściwość wątku głównego bezpośrednio. `Button1_Click` 

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

Debuger programu Visual Studio wykrywa te niebezpieczne wywołania wątku, wywołując <xref:System.InvalidOperationException> komunikat, **że operacja między wątkami jest nieprawidłowa. Kontrolka "", do której uzyskano dostęp z wątku innego niż wątek, w którym został utworzony.** <xref:System.InvalidOperationException> Zawsze występuje dla niebezpiecznych wywołań wielowątkowych podczas debugowania programu Visual Studio i może wystąpić w czasie wykonywania aplikacji. Należy rozwiązać ten problem, ale można wyłączyć wyjątek, ustawiając <xref:System.Windows.Forms.Control.CheckForIllegalCrossThreadCalls%2A?displayProperty=nameWithType> właściwość na. `false`

## <a name="safe-cross-thread-calls"></a>Bezpieczne wywołania między wątkami 

Poniższe przykłady kodu przedstawiają dwa sposoby bezpiecznego wywołania formantu Windows Forms z wątku, który go nie utworzył: 

1. <xref:System.Windows.Forms.Control.Invoke%2A?displayProperty=fullName> Metoda, która wywołuje delegata z wątku głównego, aby wywołać formant. 
2. <xref:System.ComponentModel.BackgroundWorker?displayProperty=nameWithType> Składnik, który oferuje model oparty na zdarzeniach. 

W obu przykładach wątek w tle uśpienie dla jednej sekundy w celu symulowania pracy wykonywanej w tym wątku. 

Możesz tworzyć i uruchamiać te przykłady jako aplikacje .NET Framework z poziomu wiersza C# polecenia lub Visual Basic. Aby uzyskać więcej informacji, zobacz [wiersza polecenia kompilowanego za pomocą pliku CSC. exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md) lub [Kompiluj z wiersza polecenia (Visual Basic)](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md). 

Począwszy od platformy .NET Core 3,0, można również kompilować i uruchamiać przykłady jako aplikacje platformy Windows .NET Core z folderu, który ma  *\<nazwę folderu* programu .NET Core Windows Forms > pliku projektu. csproj. 

## <a name="example-use-the-invoke-method-with-a-delegate"></a>Przykład: Używanie metody Invoke z delegatem

Poniższy przykład ilustruje wzorzec w celu zapewnienia bezpiecznego wątkowo wywołań kontrolki Windows Forms. Wysyła zapytanie do <xref:System.Windows.Forms.Control.InvokeRequired%2A?displayProperty=fullName> właściwości, co porównuje identyfikator wątku tworzenia kontrolki z identyfikatorem wątku wywołującego. Jeśli identyfikatory wątku są takie same, wywołuje formant bezpośrednio. Jeśli identyfikatory wątku są różne, wywołuje <xref:System.Windows.Forms.Control.Invoke%2A?displayProperty=nameWithType> metodę z delegatem z głównego wątku, co sprawia, że rzeczywiste wywołanie do kontrolki.

`SafeCallDelegate` Włącza <xref:System.Windows.Forms.TextBox.Text%2A> ustawienie właściwości <xref:System.Windows.Forms.TextBox> kontrolki. Metoda wykonuje zapytania <xref:System.Windows.Forms.Control.InvokeRequired%2A>. `WriteTextSafe` Jeśli <xref:System.Windows.Forms.Control.InvokeRequired%2A> zwraca `true` ,`WriteTextSafe` przekazuje metodędometody,abywykonaćrzeczywistewywołaniedokontrolki.`SafeCallDelegate` <xref:System.Windows.Forms.Control.Invoke%2A> Jeśli <xref:System.Windows.Forms.Control.InvokeRequired%2A> zwraca `false`, `WriteTextSafe` ustawia bezpośrednio.<xref:System.Windows.Forms.TextBox.Text%2A?displayProperty=nameWithType> Program obsługi `WriteTextSafe` zdarzeń tworzy nowy wątek i uruchamia metodę. `Button1_Click` 

 [!code-csharp[ThreadSafeCalls#1](~/samples/snippets/winforms/thread-safe/example1/cs/Form1.cs)]
 [!code-vb[ThreadSafeCalls#1](~/samples/snippets/winforms/thread-safe/example1/vb/Form1.vb)]  

## <a name="example-use-a-backgroundworker-event-handler"></a>Przykład: Korzystanie z programu obsługi zdarzeń BackgroundWorker

Łatwym sposobem implementacji wielowątkowości jest <xref:System.ComponentModel.BackgroundWorker?displayProperty=nameWithType> składnik, który używa modelu opartego na zdarzeniach. Wątek w tle uruchamia <xref:System.ComponentModel.BackgroundWorker.DoWork?displayProperty=nameWithType> zdarzenie, które nie współdziała z głównym wątkiem. Wątek główny uruchamia <xref:System.ComponentModel.BackgroundWorker.ProgressChanged?displayProperty=nameWithType> programy obsługi zdarzeń <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted?displayProperty=nameWithType> i, które mogą wywołać kontrolki wątku głównego.

Aby wykonać wywołanie bezpieczne dla wątków przy użyciu <xref:System.ComponentModel.BackgroundWorker>programu, należy utworzyć metodę w wątku w tle w celu wykonania pracy i powiązać ją <xref:System.ComponentModel.BackgroundWorker.DoWork> ze zdarzeniem. Utwórz kolejną metodę w wątku głównym, aby zgłosić wyniki pracy w tle i powiązać ją ze <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> zdarzeniem or. <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> Aby uruchomić wątek w tle, wywołaj <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A?displayProperty=nameWithType>polecenie. 

W przykładzie zastosowano <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> procedurę obsługi zdarzeń, aby <xref:System.Windows.Forms.TextBox> ustawić <xref:System.Windows.Forms.TextBox.Text%2A> właściwość kontrolki. Przykład użycia <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> zdarzenia znajduje się w temacie <xref:System.ComponentModel.BackgroundWorker>. 

 [!code-csharp[ThreadSafeCalls#2](~/samples/snippets/winforms/thread-safe/example2/cs/Form1.cs)]
 [!code-vb[ThreadSafeCalls#2](~/samples/snippets/winforms/thread-safe/example2/vb/Form1.vb)]  

## <a name="see-also"></a>Zobacz także

- <xref:System.ComponentModel.BackgroundWorker>
- [Instrukcje: Uruchamianie operacji w tle](how-to-run-an-operation-in-the-background.md)
- [Instrukcje: Implementowanie formularza korzystającego z operacji w tle](how-to-implement-a-form-that-uses-a-background-operation.md)
- [Tworzenie niestandardowych kontrolek Windows Forms przy użyciu .NET Framework](developing-custom-windows-forms-controls.md)
