---
title: Wykonywanie połączeń z elementami sterującymi bezpiecznymi wątkami
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
ms.openlocfilehash: 365b1acb693b9ff2be603a3e659ed8d846a7696a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79142007"
---
# <a name="how-to-make-thread-safe-calls-to-windows-forms-controls"></a>Jak: Wykonywanie elementów sterujących formularzy windows bezpiecznych dla wątków

Wielowątkowość może poprawić wydajność aplikacji Windows Forms, ale dostęp do formantów formularzy systemu Windows nie jest z natury bezpieczny dla wątków. Wielowątkową może uwidocznić kod na bardzo poważne i złożone błędy. Dwa lub więcej wątków manipulowania formantem może wymusić formant w niespójnym stanie i prowadzić do warunków wyścigu, zakleszczenia i zawiesza się lub zawiesza. Jeśli zaimplementujesz wielowątkową w aplikacji, należy wywołać formanty między wątkami w sposób bezpieczny dla wątków. Aby uzyskać więcej informacji, zobacz [Najważniejsze wskazówki dotyczące zarządzanych wątków](../../../standard/threading/managed-threading-best-practices.md).

Istnieją dwa sposoby bezpiecznego wywoływania formantu Windows Forms z wątku, który nie utworzył tego formantu. Można użyć <xref:System.Windows.Forms.Control.Invoke%2A?displayProperty=fullName> metody wywołać delegata utworzonego w wątku głównym, który z kolei wywołuje formant. Lub można zaimplementować <xref:System.ComponentModel.BackgroundWorker?displayProperty=nameWithType>program , który używa modelu opartego na zdarzeniach, aby oddzielić pracę wykonaną w wątku w tle od raportowania wyników.

## <a name="unsafe-cross-thread-calls"></a>Niebezpieczne wywołania między wątkami

Jest niebezpieczne, aby wywołać formant bezpośrednio z wątku, który go nie utworzył. Poniższy fragment kodu ilustruje niebezpieczne wywołanie formantu. <xref:System.Windows.Forms.TextBox?displayProperty=nameWithType> Program `Button1_Click` obsługi zdarzeń `WriteTextUnsafe` tworzy nowy wątek, <xref:System.Windows.Forms.TextBox.Text%2A?displayProperty=nameWithType> który ustawia właściwość głównego wątku bezpośrednio.

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

Debuger programu Visual Studio wykrywa te niebezpieczne <xref:System.InvalidOperationException> wywołania wątku przez wywołanie z komunikatem, **operacja między wątkami nieprawidłowa. Kontrola "" dostęp z wątku innego niż wątek został utworzony na.** Zawsze <xref:System.InvalidOperationException> występuje dla niebezpiecznych wywołań między wątkami podczas debugowania programu Visual Studio i może wystąpić w czasie wykonywania aplikacji. Należy rozwiązać ten problem, ale wyjątek można <xref:System.Windows.Forms.Control.CheckForIllegalCrossThreadCalls%2A?displayProperty=nameWithType> wyłączyć, ustawiając właściwość na `false`.

## <a name="safe-cross-thread-calls"></a>Bezpieczne połączenia między wątkami

Poniższe przykłady kodu pokazują dwa sposoby bezpiecznego wywoływania formantu Windows Forms z wątku, który go nie utworzył:

1. Metoda, <xref:System.Windows.Forms.Control.Invoke%2A?displayProperty=fullName> która wywołuje delegata z wątku głównego do wywołania formantu.
2. Składnik, <xref:System.ComponentModel.BackgroundWorker?displayProperty=nameWithType> który oferuje model oparty na zdarzeniach.

W obu przykładach wątek w tle uśpia przez jedną sekundę, aby symulować pracę wykonaną w tym wątku.

Można skompilować i uruchomić te przykłady jako aplikacje .NET Framework z wiersza polecenia C# lub Visual Basic. Aby uzyskać więcej informacji, zobacz [Tworzenie wiersza polecenia za pomocą pliku csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md) lub [Kompilacja z wiersza polecenia (Visual Basic).](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md)

Począwszy od programu .NET Core 3.0, można również tworzyć i uruchamiać przykłady jako aplikacje windows .NET Core z folderu o nazwie folderu .NET Core Windows Forms * \<>.csproj* pliku projektu.

## <a name="example-use-the-invoke-method-with-a-delegate"></a>Przykład: Użyj metody Invoke z pełnomocnikiem

W poniższym przykładzie pokazano wzorzec dla zapewnienia wywołania bezpieczne dla wątków do formantu Windows Forms. Wysyła kwerendy <xref:System.Windows.Forms.Control.InvokeRequired%2A?displayProperty=fullName> właściwości, która porównuje formant tworzenia identyfikator wątku do identyfikatora wątku wywołującego. Jeśli identyfikatory wątku są takie same, wywołuje formant bezpośrednio. Jeśli identyfikatory wątku są różne, <xref:System.Windows.Forms.Control.Invoke%2A?displayProperty=nameWithType> wywołuje metodę z delegatem z wątku głównego, co sprawia, że rzeczywiste wywołanie formantu.

Włącza `SafeCallDelegate` ustawienie <xref:System.Windows.Forms.TextBox> <xref:System.Windows.Forms.TextBox.Text%2A> właściwości formantu. Metoda `WriteTextSafe` wysyła <xref:System.Windows.Forms.Control.InvokeRequired%2A>kwerendy . Jeśli <xref:System.Windows.Forms.Control.InvokeRequired%2A> `true`zwraca `WriteTextSafe` , `SafeCallDelegate` przekazuje <xref:System.Windows.Forms.Control.Invoke%2A> do metody, aby rzeczywiste wywołanie formantu. Jeśli <xref:System.Windows.Forms.Control.InvokeRequired%2A> `false`zwraca `WriteTextSafe` , <xref:System.Windows.Forms.TextBox.Text%2A?displayProperty=nameWithType> ustawia bezpośrednio. Program `Button1_Click` obsługi zdarzeń tworzy nowy `WriteTextSafe` wątek i uruchamia metodę.

 [!code-csharp[ThreadSafeCalls#1](~/samples/snippets/winforms/thread-safe/example1/cs/Form1.cs)]
 [!code-vb[ThreadSafeCalls#1](~/samples/snippets/winforms/thread-safe/example1/vb/Form1.vb)]  

## <a name="example-use-a-backgroundworker-event-handler"></a>Przykład: Użyj programu obsługi zdarzeń BackgroundWorker

Łatwym sposobem zaimplementowania wielowątkowego jest <xref:System.ComponentModel.BackgroundWorker?displayProperty=nameWithType> składnik, który używa modelu opartego na zdarzeniach. Wątek w <xref:System.ComponentModel.BackgroundWorker.DoWork?displayProperty=nameWithType> tle uruchamia zdarzenie, które nie wchodzi w interakcję z wątku głównego. Główny wątek <xref:System.ComponentModel.BackgroundWorker.ProgressChanged?displayProperty=nameWithType> <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted?displayProperty=nameWithType> uruchamia i obsługi zdarzeń, które można wywołać formanty wątku głównego.

Aby wykonać wywołanie bezpieczne <xref:System.ComponentModel.BackgroundWorker>dla wątków przy użyciu , utwórz metodę w <xref:System.ComponentModel.BackgroundWorker.DoWork> wątku tła, aby wykonać pracę, i powiązać ją ze zdarzeniem. Utwórz inną metodę w wątku głównym, aby zgłosić wyniki <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> pracy w tle i powiązać ją z zdarzeniem lub. Aby uruchomić wątek <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A?displayProperty=nameWithType>tła, zadzwoń do pliku .

W przykładzie <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> użyto programu <xref:System.Windows.Forms.TextBox> obsługi zdarzeń, aby ustawić <xref:System.Windows.Forms.TextBox.Text%2A> właściwość formantu. Na przykład przy <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> użyciu <xref:System.ComponentModel.BackgroundWorker>zdarzenia, zobacz .

 [!code-csharp[ThreadSafeCalls#2](~/samples/snippets/winforms/thread-safe/example2/cs/Form1.cs)]
 [!code-vb[ThreadSafeCalls#2](~/samples/snippets/winforms/thread-safe/example2/vb/Form1.vb)]  

## <a name="see-also"></a>Zobacz też

- <xref:System.ComponentModel.BackgroundWorker>
- [Jak: Uruchamianie operacji w tle](how-to-run-an-operation-in-the-background.md)
- [Jak: Implementowanie formularza, który używa operacji w tle](how-to-implement-a-form-that-uses-a-background-operation.md)
- [Tworzenie niestandardowych formantów formularzy systemu Windows za pomocą programu .NET Framework](developing-custom-windows-forms-controls.md)
