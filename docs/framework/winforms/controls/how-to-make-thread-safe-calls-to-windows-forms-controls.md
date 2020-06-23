---
title: Ustaw bezpieczne dla wątków wywołania formantów
ms.date: 02/19/2019
description: Dowiedz się, jak zaimplementować wielowątkowość w aplikacji przez wywoływanie kontrolek między wątkami w sposób bezpieczny dla wątków.
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
ms.openlocfilehash: b5f4de7bd3d8d89de98dbe27e2dbf360763670d0
ms.sourcegitcommit: 3824ff187947572b274b9715b60c11269335c181
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/17/2020
ms.locfileid: "84904185"
---
# <a name="how-to-make-thread-safe-calls-to-windows-forms-controls"></a>Instrukcje: wykonywanie bezpiecznych dla wątków wywołań formantów Windows Forms

Wielowątkowość może zwiększyć wydajność aplikacji Windows Forms, ale dostęp do kontrolek Windows Forms nie jest ze względu bezpieczny wątkowo. Wielowątkowość może uwidaczniać kod do bardzo poważnych i złożonych błędów. Co najmniej dwa wątki manipulowania kontrolką mogą wymusić niespójność kontroli i prowadzić do warunków wyścigu, zakleszczeniów i zawieszania się lub zawieszenia. W przypadku zaimplementowania wielowątkowości w aplikacji należy zadbać o to, aby w sposób bezpieczny wątkowo wywoływać kontrolki międzywątkowe. Aby uzyskać więcej informacji, zobacz temat [zarządzane wątki z najlepszymi rozwiązaniami](../../../standard/threading/managed-threading-best-practices.md).

Istnieją dwa sposoby bezpiecznego wywołania formantu Windows Forms z wątku, który nie utworzył tego formantu. Można użyć <xref:System.Windows.Forms.Control.Invoke%2A?displayProperty=fullName> metody do wywołania delegata utworzonego w wątku głównym, który z kolei wywołuje formant. Lub, można zaimplementować a <xref:System.ComponentModel.BackgroundWorker?displayProperty=nameWithType> , który używa modelu sterowanego zdarzeniami, do rozdzielenia pracy wykonanej w wątku w tle z raportowaniem wyników.

## <a name="unsafe-cross-thread-calls"></a>Niebezpieczne wywołania między wątkami

Wywołanie formantu bezpośrednio z wątku, który nie został utworzony, jest niebezpieczne. Poniższy fragment kodu ilustruje niebezpieczne wywołanie do <xref:System.Windows.Forms.TextBox?displayProperty=nameWithType> kontrolki. `Button1_Click`Program obsługi zdarzeń tworzy nowy `WriteTextUnsafe` wątek, który ustawia właściwość wątku głównego <xref:System.Windows.Forms.TextBox.Text%2A?displayProperty=nameWithType> bezpośrednio.

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

Debuger programu Visual Studio wykrywa te niebezpieczne wywołania wątku <xref:System.InvalidOperationException> , wywołując komunikat, że **operacja między wątkami jest nieprawidłowa. Kontrolka "", do której uzyskano dostęp z wątku innego niż wątek, w którym został utworzony.** <xref:System.InvalidOperationException>Zawsze występuje dla niebezpiecznych wywołań wielowątkowych podczas debugowania programu Visual Studio i może wystąpić w czasie wykonywania aplikacji. Należy rozwiązać ten problem, ale można wyłączyć wyjątek, ustawiając <xref:System.Windows.Forms.Control.CheckForIllegalCrossThreadCalls%2A?displayProperty=nameWithType> Właściwość na `false` .

## <a name="safe-cross-thread-calls"></a>Bezpieczne wywołania między wątkami

Poniższe przykłady kodu przedstawiają dwa sposoby bezpiecznego wywołania formantu Windows Forms z wątku, który go nie utworzył:

1. <xref:System.Windows.Forms.Control.Invoke%2A?displayProperty=fullName>Metoda, która wywołuje delegata z wątku głównego, aby wywołać formant.
2. <xref:System.ComponentModel.BackgroundWorker?displayProperty=nameWithType>Składnik, który oferuje model oparty na zdarzeniach.

W obu przykładach wątek w tle uśpienie dla jednej sekundy w celu symulowania pracy wykonywanej w tym wątku.

Możesz tworzyć i uruchamiać te przykłady jako .NET Framework aplikacje z poziomu wiersza polecenia C# lub Visual Basic. Aby uzyskać więcej informacji, zobacz [wiersza polecenia kompilowania przy użyciu csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md) lub [kompilowania z wiersza polecenia (Visual Basic)](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md).

Począwszy od platformy .NET Core 3,0, można również kompilować i uruchamiać przykłady jako aplikacje platformy Windows .NET Core z folderu, który ma plik projektu programu .NET Core Windows Forms * \<folder name> . csproj* .

## <a name="example-use-the-invoke-method-with-a-delegate"></a>Przykład: Użyj metody Invoke z delegatem

Poniższy przykład ilustruje wzorzec w celu zapewnienia bezpiecznego wątkowo wywołań kontrolki Windows Forms. Wysyła zapytanie do <xref:System.Windows.Forms.Control.InvokeRequired%2A?displayProperty=fullName> właściwości, co porównuje identyfikator wątku tworzenia kontrolki z identyfikatorem wątku wywołującego. Jeśli identyfikatory wątku są takie same, wywołuje formant bezpośrednio. Jeśli identyfikatory wątku są różne, wywołuje <xref:System.Windows.Forms.Control.Invoke%2A?displayProperty=nameWithType> metodę z delegatem z głównego wątku, co sprawia, że rzeczywiste wywołanie do kontrolki.

`SafeCallDelegate`Włącza ustawienie <xref:System.Windows.Forms.TextBox> właściwości kontrolki <xref:System.Windows.Forms.TextBox.Text%2A> . `WriteTextSafe`Metoda wykonuje zapytania <xref:System.Windows.Forms.Control.InvokeRequired%2A> . Jeśli <xref:System.Windows.Forms.Control.InvokeRequired%2A> zwraca `true` , `WriteTextSafe` przekazuje `SafeCallDelegate` metodę do <xref:System.Windows.Forms.Control.Invoke%2A> metody, aby wykonać rzeczywiste wywołanie do kontrolki. Jeśli <xref:System.Windows.Forms.Control.InvokeRequired%2A> zwraca `false` , `WriteTextSafe` ustawia <xref:System.Windows.Forms.TextBox.Text%2A?displayProperty=nameWithType> bezpośrednio. `Button1_Click`Program obsługi zdarzeń tworzy nowy wątek i uruchamia `WriteTextSafe` metodę.

 [!code-csharp[ThreadSafeCalls#1](~/samples/snippets/winforms/thread-safe/example1/cs/Form1.cs)]
 [!code-vb[ThreadSafeCalls#1](~/samples/snippets/winforms/thread-safe/example1/vb/Form1.vb)]  

## <a name="example-use-a-backgroundworker-event-handler"></a>Przykład: Użyj procedury obsługi zdarzeń BackgroundWorker

Łatwym sposobem implementacji wielowątkowości jest <xref:System.ComponentModel.BackgroundWorker?displayProperty=nameWithType> składnik, który używa modelu opartego na zdarzeniach. Wątek w tle uruchamia <xref:System.ComponentModel.BackgroundWorker.DoWork?displayProperty=nameWithType> zdarzenie, które nie współdziała z głównym wątkiem. Wątek główny uruchamia <xref:System.ComponentModel.BackgroundWorker.ProgressChanged?displayProperty=nameWithType> <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted?displayProperty=nameWithType> programy obsługi zdarzeń i, które mogą wywołać kontrolki wątku głównego.

Aby wykonać wywołanie bezpieczne dla wątków przy użyciu programu <xref:System.ComponentModel.BackgroundWorker> , należy utworzyć metodę w wątku w tle w celu wykonania pracy i powiązać ją ze <xref:System.ComponentModel.BackgroundWorker.DoWork> zdarzeniem. Utwórz kolejną metodę w wątku głównym, aby zgłosić wyniki pracy w tle i powiązać ją ze <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> zdarzeniem or. Aby uruchomić wątek w tle, wywołaj polecenie <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A?displayProperty=nameWithType> .

W przykładzie zastosowano <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> procedurę obsługi zdarzeń, aby ustawić <xref:System.Windows.Forms.TextBox> Właściwość kontrolki <xref:System.Windows.Forms.TextBox.Text%2A> . Przykład użycia <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> zdarzenia znajduje się w temacie <xref:System.ComponentModel.BackgroundWorker> .

 [!code-csharp[ThreadSafeCalls#2](~/samples/snippets/winforms/thread-safe/example2/cs/Form1.cs)]
 [!code-vb[ThreadSafeCalls#2](~/samples/snippets/winforms/thread-safe/example2/vb/Form1.vb)]  

## <a name="see-also"></a>Zobacz też

- <xref:System.ComponentModel.BackgroundWorker>
- [Instrukcje: uruchamianie operacji w tle](how-to-run-an-operation-in-the-background.md)
- [Instrukcje: Implementowanie formularza korzystającego z operacji w tle](how-to-implement-a-form-that-uses-a-background-operation.md)
- [Tworzenie niestandardowych kontrolek Windows Forms przy użyciu .NET Framework](developing-custom-windows-forms-controls.md)
