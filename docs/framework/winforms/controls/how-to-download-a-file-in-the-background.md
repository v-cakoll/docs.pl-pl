---
title: 'Porady: pobieranie pliku w tle'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- BackgroundWorker component
- background tasks
- Asynchronous Pattern
- forms [Windows Forms], multithreading
- components [Windows Forms], asynchronous
- forms [Windows Forms], background operations
- threading [Windows Forms], background operations
- background operations
ms.assetid: 9b7bc5ae-051c-4904-9720-18f6667388bd
ms.openlocfilehash: 2396516a0e6c9aeb9b2d64a0bf6e3974d64a5cc5
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/14/2018
ms.locfileid: "45594870"
---
# <a name="how-to-download-a-file-in-the-background"></a>Porady: pobieranie pliku w tle
Pobieranie pliku jest typowym zadaniem i jest często przydatne do wykonania tej operacji potencjalnie czasochłonne w oddzielnym wątku. Użyj <xref:System.ComponentModel.BackgroundWorker> składnika, aby wykonać to zadanie za pomocą bardzo niewielkiej ilości kodu.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu demonstruje sposób używania <xref:System.ComponentModel.BackgroundWorker> składnika można załadować pliku XML z adresu URL. Kiedy użytkownik kliknie **Pobierz** przycisku <xref:System.Windows.Forms.Control.Click> wywołań obsługi zdarzeń <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> metody <xref:System.ComponentModel.BackgroundWorker> składnika, aby uruchomić operację pobierania. Ten przycisk jest wyłączone na czas trwania pobierania i włączone po zakończeniu pobierania. A <xref:System.Windows.Forms.MessageBox> Wyświetla zawartość pliku.  
  
 [!code-csharp[System.ComponentModel.BackgroundWorker.IsBusy#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.IsBusy/CS/Form1.cs#1)]
 [!code-vb[System.ComponentModel.BackgroundWorker.IsBusy#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.IsBusy/VB/Form1.vb#1)]  
  
 **Pobieranie pliku**  
  
 Plik jest pobierany na <xref:System.ComponentModel.BackgroundWorker> wątku roboczego składnika, który jest uruchamiany <xref:System.ComponentModel.BackgroundWorker.DoWork> programu obsługi zdarzeń. Ten wątek rozpoczyna się, gdy kod wywołuje <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> metody.  
  
 [!code-csharp[System.ComponentModel.BackgroundWorker.IsBusy#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.IsBusy/CS/Form1.cs#3)]
 [!code-vb[System.ComponentModel.BackgroundWorker.IsBusy#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.IsBusy/VB/Form1.vb#3)]  
  
 **BackgroundWorker zakończyć oczekiwanie**  
  
 `downloadButton_Click` Programu obsługi zdarzeń pokazuje, jak czekać na <xref:System.ComponentModel.BackgroundWorker> składnika, aby zakończyć jego zadanie asynchroniczne.  
  
 Jeśli tylko aplikacja ma reagować na zdarzenia, a nie chcesz wykonać pracę w wątku głównym, podczas oczekiwania na ukończenie wątku tła, po prostu zamknąć program obsługi.  
  
 Jeśli chcesz to kontynuować pracę w wątku głównym, użyj <xref:System.ComponentModel.BackgroundWorker.IsBusy%2A> właściwości, aby określić, czy <xref:System.ComponentModel.BackgroundWorker> wątek jest nadal uruchomiona. W tym przykładzie paska postępu jest aktualizowana podczas przetwarzania pliki do pobrania. Pamiętaj wywołać <xref:System.Windows.Forms.Application.DoEvents%2A?displayProperty=nameWithType> metodę, aby zachować dynamicznego interfejsu użytkownika.  
  
 [!code-csharp[System.ComponentModel.BackgroundWorker.IsBusy#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.IsBusy/CS/Form1.cs#2)]
 [!code-vb[System.ComponentModel.BackgroundWorker.IsBusy#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.IsBusy/VB/Form1.vb#2)]  
  
 **Wyświetlanie wyników**  
  
 `backgroundWorker1_RunWorkerCompleted` Metodę uchwytów <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> zdarzenie i jest wywoływana po zakończeniu operacji w tle. Metoda ta najpierw sprawdza <xref:System.ComponentModel.AsyncCompletedEventArgs.Error%2A?displayProperty=nameWithType> właściwości. Jeśli <xref:System.ComponentModel.AsyncCompletedEventArgs.Error%2A?displayProperty=nameWithType> jest `null`, wówczas ta metoda Wy Wyświetla zawartość pliku. Umożliwia ona następnie przycisk pobierania, który został wyłączony w momencie rozpoczęcia pobierania, i resetuje pasek postępu.  
  
 [!code-csharp[System.ComponentModel.BackgroundWorker.IsBusy#4](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.IsBusy/CS/Form1.cs#4)]
 [!code-vb[System.ComponentModel.BackgroundWorker.IsBusy#4](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.IsBusy/VB/Form1.vb#4)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ten przykład wymaga:  
  
-   Odwołania do zestawów System.Xml, System.Drawing i przestrzeń nazw System.Windows.Forms.  
  
 Aby uzyskać informacje o tworzeniu tego przykładu z wiersza polecenia dla programu visual Basic lub Visual C#, zobacz [tworzenie z wiersza polecenia](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) lub [wiersza polecenia tworzenia przy użyciu csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Można także utworzyć tego przykładu w programie Visual Studio, wklejając kod do nowego projektu.  Zobacz też [porady: kompilowanie i uruchamianie pełną Windows Forms kodu przykładzie przy użyciu programu Visual Studio](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).  
  
## <a name="robust-programming"></a>Niezawodne programowanie  
 Zawsze sprawdzaj <xref:System.ComponentModel.AsyncCompletedEventArgs.Error%2A?displayProperty=nameWithType> właściwości w swojej <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> programu obsługi zdarzeń przed podjęciem próby uzyskania dostępu <xref:System.ComponentModel.RunWorkerCompletedEventArgs.Result%2A?displayProperty=nameWithType> właściwości lub inny obiekt, który może mieć wpływ <xref:System.ComponentModel.BackgroundWorker.DoWork> programu obsługi zdarzeń.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ComponentModel.BackgroundWorker>  
 [Instrukcje: uruchamianie operacji w tle](../../../../docs/framework/winforms/controls/how-to-run-an-operation-in-the-background.md)  
 [Instrukcje: implementowanie formularza korzystającego z operacji w tle](../../../../docs/framework/winforms/controls/how-to-implement-a-form-that-uses-a-background-operation.md)
