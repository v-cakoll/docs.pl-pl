---
title: Ustaw bezpieczne dla wątków wywołania formantów
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
ms.openlocfilehash: 101457ab2a02b8de49d06c354ca307e07b690ba2
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76736166"
---
# <a name="how-to-make-thread-safe-calls-to-windows-forms-controls"></a>Instrukcje: wykonywanie bezpiecznych dla wątków wywołań formantów Windows Forms

Wielowątkowość może zwiększyć wydajność aplikacji Windows Forms, ale dostęp do kontrolek Windows Forms nie jest ze względu bezpieczny wątkowo. Wielowątkowość może uwidaczniać kod do bardzo poważnych i złożonych błędów. Co najmniej dwa wątki manipulowania kontrolką mogą wymusić niespójność kontroli i prowadzić do warunków wyścigu, zakleszczeniów i zawieszania się lub zawieszenia. W przypadku zaimplementowania wielowątkowości w aplikacji należy zadbać o to, aby w sposób bezpieczny wątkowo wywoływać kontrolki międzywątkowe. Aby uzyskać więcej informacji, zobacz temat [zarządzane wątki z najlepszymi rozwiązaniami](../../../standard/threading/managed-threading-best-practices.md). 

Istnieją dwa sposoby bezpiecznego wywołania formantu Windows Forms z wątku, który nie utworzył tego formantu. Metodę <xref:System.Windows.Forms.Control.Invoke%2A?displayProperty=fullName> można użyć do wywołania delegata utworzonego w wątku głównym, który z kolei wywołuje formant. Można też zaimplementować <xref:System.ComponentModel.BackgroundWorker?displayProperty=nameWithType>, która używa modelu opartego na zdarzeniach, do rozdzielenia pracy wykonanej w wątku w tle z raportowaniem wyników. 

## <a name="unsafe-cross-thread-calls"></a>Niebezpieczne wywołania między wątkami

Wywołanie formantu bezpośrednio z wątku, który nie został utworzony, jest niebezpieczne. Poniższy fragment kodu ilustruje niebezpieczne wywołanie kontrolki <xref:System.Windows.Forms.TextBox?displayProperty=nameWithType>. Program obsługi zdarzeń `Button1_Click` tworzy nowy wątek `WriteTextUnsafe`, który bezpośrednio ustawia właściwość <xref:System.Windows.Forms.TextBox.Text%2A?displayProperty=nameWithType> wątku głównego. 

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

Debuger programu Visual Studio wykrywa te niebezpieczne wywołania wątku, wywołując <xref:System.InvalidOperationException> z komunikatem, **operacja między wątkami jest nieprawidłowa. Kontrolka "", do której uzyskano dostęp z wątku innego niż wątek, w którym został utworzony.** <xref:System.InvalidOperationException> zawsze występuje w przypadku niebezpiecznych wywołań między wątkami podczas debugowania programu Visual Studio i może wystąpić w czasie wykonywania aplikacji. Należy rozwiązać ten problem, ale można wyłączyć wyjątek, ustawiając właściwość <xref:System.Windows.Forms.Control.CheckForIllegalCrossThreadCalls%2A?displayProperty=nameWithType> na `false`.

## <a name="safe-cross-thread-calls"></a>Bezpieczne wywołania między wątkami 

Poniższe przykłady kodu przedstawiają dwa sposoby bezpiecznego wywołania formantu Windows Forms z wątku, który go nie utworzył: 

1. Metoda <xref:System.Windows.Forms.Control.Invoke%2A?displayProperty=fullName>, która wywołuje delegata z wątku głównego, aby wywołać formant. 
2. Składnik <xref:System.ComponentModel.BackgroundWorker?displayProperty=nameWithType>, który oferuje model oparty na zdarzeniach. 

W obu przykładach wątek w tle uśpienie dla jednej sekundy w celu symulowania pracy wykonywanej w tym wątku. 

Możesz tworzyć i uruchamiać te przykłady jako aplikacje .NET Framework z poziomu wiersza C# polecenia lub Visual Basic. Aby uzyskać więcej informacji, zobacz [wiersza polecenia kompilowanego za pomocą pliku CSC. exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md) lub [Kompiluj z wiersza polecenia (Visual Basic)](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md). 

Począwszy od platformy .NET Core 3,0, można również kompilować i uruchamiać przykłady jako aplikacje Windows .NET Core z folderu, który ma Windows Forms .NET Core *\<nazwa folderu >. csproj* . 

## <a name="example-use-the-invoke-method-with-a-delegate"></a>Przykład: Użyj metody Invoke z delegatem

Poniższy przykład ilustruje wzorzec w celu zapewnienia bezpiecznego wątkowo wywołań kontrolki Windows Forms. Wysyła zapytanie do właściwości <xref:System.Windows.Forms.Control.InvokeRequired%2A?displayProperty=fullName>, co porównuje identyfikator wątku tworzenia kontrolki z IDENTYFIKATORem wątku wywołującego. Jeśli identyfikatory wątku są takie same, wywołuje formant bezpośrednio. Jeśli identyfikatory wątku są różne, wywołuje metodę <xref:System.Windows.Forms.Control.Invoke%2A?displayProperty=nameWithType> z delegatem z głównego wątku, co sprawia, że rzeczywiste wywołanie do kontrolki.

`SafeCallDelegate` umożliwia ustawienie właściwości <xref:System.Windows.Forms.TextBox.Text%2A> kontrolki <xref:System.Windows.Forms.TextBox>. Metoda `WriteTextSafe` wykonuje zapytania <xref:System.Windows.Forms.Control.InvokeRequired%2A>. Jeśli <xref:System.Windows.Forms.Control.InvokeRequired%2A> zwraca `true`, `WriteTextSafe` przekazuje `SafeCallDelegate` do metody <xref:System.Windows.Forms.Control.Invoke%2A>, aby wykonać rzeczywiste wywołanie do kontrolki. Jeśli <xref:System.Windows.Forms.Control.InvokeRequired%2A> zwraca `false`, `WriteTextSafe` ustawia <xref:System.Windows.Forms.TextBox.Text%2A?displayProperty=nameWithType> bezpośrednio. Program obsługi zdarzeń `Button1_Click` tworzy nowy wątek i uruchamia metodę `WriteTextSafe`. 

 [!code-csharp[ThreadSafeCalls#1](~/samples/snippets/winforms/thread-safe/example1/cs/Form1.cs)]
 [!code-vb[ThreadSafeCalls#1](~/samples/snippets/winforms/thread-safe/example1/vb/Form1.vb)]  

## <a name="example-use-a-backgroundworker-event-handler"></a>Przykład: Użyj procedury obsługi zdarzeń BackgroundWorker

Łatwy sposób implementacji wielowątkowości polega na składniku <xref:System.ComponentModel.BackgroundWorker?displayProperty=nameWithType>, który używa modelu opartego na zdarzeniach. Wątek w tle uruchamia zdarzenie <xref:System.ComponentModel.BackgroundWorker.DoWork?displayProperty=nameWithType>, które nie współdziała z głównym wątkiem. Wątek główny uruchamia programy obsługi zdarzeń <xref:System.ComponentModel.BackgroundWorker.ProgressChanged?displayProperty=nameWithType> i <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted?displayProperty=nameWithType>, które mogą wywołać kontrolki wątku głównego.

Aby wykonać wywołanie bezpieczne dla wątków przy użyciu <xref:System.ComponentModel.BackgroundWorker>, Utwórz metodę w wątku w tle w celu wykonania pracy i powiąż ją ze zdarzeniem <xref:System.ComponentModel.BackgroundWorker.DoWork>. Utwórz kolejną metodę w wątku głównym, aby zgłosić wyniki pracy w tle i powiązać ją ze zdarzeniem <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> lub <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted>. Aby uruchomić wątek w tle, wywołaj <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A?displayProperty=nameWithType>. 

W przykładzie zastosowano procedurę obsługi zdarzeń <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted>, aby ustawić właściwość <xref:System.Windows.Forms.TextBox.Text%2A> kontrolki <xref:System.Windows.Forms.TextBox>. Przykład użycia zdarzenia <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> można znaleźć w temacie <xref:System.ComponentModel.BackgroundWorker>. 

 [!code-csharp[ThreadSafeCalls#2](~/samples/snippets/winforms/thread-safe/example2/cs/Form1.cs)]
 [!code-vb[ThreadSafeCalls#2](~/samples/snippets/winforms/thread-safe/example2/vb/Form1.vb)]  

## <a name="see-also"></a>Zobacz także

- <xref:System.ComponentModel.BackgroundWorker>
- [Instrukcje: uruchamianie operacji w tle](how-to-run-an-operation-in-the-background.md)
- [Instrukcje: Implementowanie formularza korzystającego z operacji w tle](how-to-implement-a-form-that-uses-a-background-operation.md)
- [Tworzenie niestandardowych kontrolek Windows Forms przy użyciu .NET Framework](developing-custom-windows-forms-controls.md)
