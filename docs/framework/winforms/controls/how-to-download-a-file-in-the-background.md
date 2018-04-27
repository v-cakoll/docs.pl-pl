---
title: 'Porady: pobieranie pliku w tle'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: ''
ms.topic: article
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
caps.latest.revision: 10
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: bdc587fb42722108466361500816a6598c8515e9
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-download-a-file-in-the-background"></a>Porady: pobieranie pliku w tle
Pobieranie pliku jest typowych zadań i często jest przydatne do przeprowadzenia tej operacji potencjalnie czasochłonne w oddzielnym wątku. Użyj <xref:System.ComponentModel.BackgroundWorker> składnika, aby wykonać to zadanie wymaga bardzo mało kodu.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu pokazuje sposób użycia <xref:System.ComponentModel.BackgroundWorker> składnika można załadować pliku XML z adresu URL. Po kliknięciu przez użytkownika **Pobierz** przycisku <xref:System.Windows.Forms.Control.Click> wywołań obsługi zdarzeń <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> metody <xref:System.ComponentModel.BackgroundWorker> składnik, aby uruchomić operację pobierania. Przycisk jest wyłączone na czas trwania pobierania, a następnie włączona po ukończeniu pobierania. A <xref:System.Windows.Forms.MessageBox> Wyświetla zawartość pliku.  
  
 [!code-csharp[System.ComponentModel.BackgroundWorker.IsBusy#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.IsBusy/CS/Form1.cs#1)]
 [!code-vb[System.ComponentModel.BackgroundWorker.IsBusy#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.IsBusy/VB/Form1.vb#1)]  
  
 **Trwa pobieranie pliku**  
  
 Plik jest pobierany na <xref:System.ComponentModel.BackgroundWorker> wątku roboczego składnika, w którym jest uruchomiona <xref:System.ComponentModel.BackgroundWorker.DoWork> obsługi zdarzeń. Ten wątek rozpoczyna się, gdy kod wywołuje <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> metody.  
  
 [!code-csharp[System.ComponentModel.BackgroundWorker.IsBusy#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.IsBusy/CS/Form1.cs#3)]
 [!code-vb[System.ComponentModel.BackgroundWorker.IsBusy#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.IsBusy/VB/Form1.vb#3)]  
  
 **Oczekiwanie na BackgroundWorker do zakończenia**  
  
 `downloadButton_Click` Obsługi zdarzeń pokazuje, jak oczekiwania <xref:System.ComponentModel.BackgroundWorker> składnika na zakończenie swojego zadania asynchronicznego.  
  
 Jeśli tylko aplikacja ma odpowiadanie na zdarzenia i nie chcesz wykonać pracę w głównym wątku podczas oczekiwania na zakończenie wątku tła, po prostu Wyjdź. program obsługi.  
  
 Jeśli chcesz kontynuować pracę w głównym wątku, użyj <xref:System.ComponentModel.BackgroundWorker.IsBusy%2A> umożliwia określenie, czy <xref:System.ComponentModel.BackgroundWorker> wątku jest nadal uruchomiona. W tym przykładzie paska postępu jest aktualizowany podczas przetwarzania pobierania. Pamiętaj wywołać <xref:System.Windows.Forms.Application.DoEvents%2A?displayProperty=nameWithType> Metoda aktualizowania reakcji interfejsu użytkownika.  
  
 [!code-csharp[System.ComponentModel.BackgroundWorker.IsBusy#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.IsBusy/CS/Form1.cs#2)]
 [!code-vb[System.ComponentModel.BackgroundWorker.IsBusy#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.IsBusy/VB/Form1.vb#2)]  
  
 **Wyświetlanie wyników**  
  
 `backgroundWorker1_RunWorkerCompleted` Dojścia metody <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> zdarzeń i jest wywoływana po wykonaniu operacji w tle. Ta metoda sprawdza najpierw <xref:System.ComponentModel.AsyncCompletedEventArgs.Error%2A?displayProperty=nameWithType> właściwości. Jeśli <xref:System.ComponentModel.AsyncCompletedEventArgs.Error%2A?displayProperty=nameWithType> jest `null`, a następnie ta metoda Wyświetla zawartość pliku. Następnie włącza przycisk pobierania, który został wyłączony w momencie rozpoczęcia pobierania, oraz resetuje pasek postępu.  
  
 [!code-csharp[System.ComponentModel.BackgroundWorker.IsBusy#4](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.IsBusy/CS/Form1.cs#4)]
 [!code-vb[System.ComponentModel.BackgroundWorker.IsBusy#4](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.IsBusy/VB/Form1.vb#4)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ten przykład wymaga:  
  
-   Odwołania do zestawów System.Xml, System.Drawing i System.Windows.Forms.  
  
 Uzyskać informacje o kompilowaniu w tym przykładzie z wiersza polecenia dla programu visual Basic lub Visual C#, zobacz [tworzenie z wiersza polecenia](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) lub [kompilowania z wiersza polecenia csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Można także utworzyć tym przykładzie [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] przez wklejenie kodu do nowego projektu.  Zobacz też [porady: kompilowanie i uruchamianie pełną Windows formularze kodu przykład za pomocą programu Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).  
  
## <a name="robust-programming"></a>Niezawodne programowanie  
 Zawsze sprawdzaj <xref:System.ComponentModel.AsyncCompletedEventArgs.Error%2A?displayProperty=nameWithType> właściwości w Twojej <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> obsługi zdarzeń przed podjęciem próby uzyskania dostępu <xref:System.ComponentModel.RunWorkerCompletedEventArgs.Result%2A?displayProperty=nameWithType> właściwości lub inny obiekt, który może mieć wpływ <xref:System.ComponentModel.BackgroundWorker.DoWork> obsługi zdarzeń.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ComponentModel.BackgroundWorker>  
 [Instrukcje: uruchamianie operacji w tle](../../../../docs/framework/winforms/controls/how-to-run-an-operation-in-the-background.md)  
 [Instrukcje: implementowanie formularza korzystającego z operacji w tle](../../../../docs/framework/winforms/controls/how-to-implement-a-form-that-uses-a-background-operation.md)
