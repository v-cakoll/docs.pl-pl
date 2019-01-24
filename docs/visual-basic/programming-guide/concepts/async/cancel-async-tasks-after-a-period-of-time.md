---
title: Anulowanie zadań asynchronicznych po upływie określonego czasu (Visual Basic)
ms.date: 07/20/2015
ms.assetid: a48045a3-6a99-42af-b824-af340f0b9a5d
ms.openlocfilehash: a01ab79a2895bd9c5a8ae4782db06eb9dd5664a9
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54580554"
---
# <a name="cancel-async-tasks-after-a-period-of-time-visual-basic"></a>Anulowanie zadań asynchronicznych po upływie określonego czasu (Visual Basic)
Możesz anulować operację asynchroniczną po upływie pewnego czasu za pomocą <xref:System.Threading.CancellationTokenSource.CancelAfter%2A?displayProperty=nameWithType> metody, jeśli nie chcesz czekać na zakończenie operacji. Ta metoda planuje anulowanie skojarzonych zadań, które nie są ukończone przed upływem czasu, który jest wyznaczone przez `CancelAfter` wyrażenia.  
  
 Ten przykład dodaje do kodu utworzonego w [anulowanie zadania asynchronicznego lub listy zadań (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/cancel-an-async-task-or-a-list-of-tasks.md) można pobrać listy witryn sieci Web i wyświetlającym długość zawartości każdej z nich.  
  
> [!NOTE]
>  Aby uruchomić przykłady, jest posiadanie programu Visual Studio 2012 lub nowszy i program .NET Framework 4.5 lub nowszy jest zainstalowany na tym komputerze.  
  
## <a name="downloading-the-example"></a>Pobieranie przykładu  
 Można pobrać pełny projekt Windows Presentation Foundation (WPF) z [próbka asynchroniczna: Poprawnie Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) a następnie wykonaj poniższe kroki.  
  
1.  Dekompresuje plik który został pobrany, a następnie uruchom program Visual Studio.  
  
2.  Na pasku menu wybierz **pliku**, **Otwórz**, **projekt/rozwiązanie**.  
  
3.  W **Otwórz projekt** okno dialogowe, otwórz folder, który zawiera przykładowy kod, który został zdekompresowany, a następnie otwórz plik rozwiązania (.sln) dla AsyncFineTuningVB.  
  
4.  W **Eksploratora rozwiązań**, otwórz menu skrótów dla **CancelAfterTime** projektu, a następnie wybierz **Ustaw jako projekt startowy**.  
  
5.  Wybierz klawisz F5, aby uruchomić projekt.  
  
     Wybierz klawisze Ctrl + F5, aby uruchomić projekt bez debugowania go.  
  
6.  Uruchom program kilka razy, aby sprawdzić, czy dane wyjściowe są pokazywane dla wszystkich witryn sieci Web, witryn sieci Web lub niektórych witryn sieci web.  
  
 Jeśli nie chcesz wczytać projekt, można przejrzeć plik MainWindow.xaml.vb na końcu tego tematu.  
  
## <a name="building-the-example"></a>Budowanie przykładu  
 W przykładzie w tym temacie dodaje do projektu utworzonego w [anulowanie zadania asynchronicznego lub listy zadań (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/cancel-an-async-task-or-a-list-of-tasks.md) umożliwiający anulowanie listy zadań. W przykładzie użyto tego samego interfejsu użytkownika, mimo że **anulować** przycisk nie jest używany jawnie.  
  
 Aby zbudować przykład samodzielnie, krok po kroku, postępuj zgodnie z instrukcjami w sekcji "Pobieranie przykładu", ale wybierając **CancelAListOfTasks** jako **projekt startowy**. Dodaj zmiany w tym temacie do tego projektu.  
  
 Aby określić maksymalny czas, zanim zadania są oznaczane jako anulowane, należy dodać wywołanie `CancelAfter` do `startButton_Click`, jak pokazano w poniższym przykładzie. Dodatek jest oznaczony gwiazdkami.  
  
```vb  
Private Async Sub startButton_Click(sender As Object, e As RoutedEventArgs)  
  
    ' Instantiate the CancellationTokenSource.  
    cts = New CancellationTokenSource()  
  
    resultsTextBox.Clear()  
  
    Try  
        ' ***Set up the CancellationTokenSource to cancel after 2.5 seconds. (You   
        ' can adjust the time.)  
        cts.CancelAfter(2500)  
  
        Await AccessTheWebAsync(cts.Token)  
        resultsTextBox.Text &= vbCrLf & "Downloads complete."  
  
    Catch ex As OperationCanceledException  
        resultsTextBox.Text &= vbCrLf & "Downloads canceled." & vbCrLf  
  
    Catch ex As Exception  
        resultsTextBox.Text &= vbCrLf & "Downloads failed." & vbCrLf  
    End Try  
  
    ' Set the CancellationTokenSource to Nothing when the download is complete.  
    cts = Nothing  
End Sub  
```  
  
 Uruchom program kilka razy, aby sprawdzić, czy dane wyjściowe są pokazywane dla wszystkich witryn sieci Web, witryn sieci Web lub niektórych witryn sieci web. Poniższe dane wyjściowe są przykładowe.  
  
```  
Length of the downloaded string: 35990.  
  
Length of the downloaded string: 407399.  
  
Length of the downloaded string: 226091.  
  
Downloads canceled.  
```  
  
## <a name="complete-example"></a>Kompletny przykład  
 Poniższy kod jest pełnym tekstem pliku MainWindow.xaml.vb dla przykładu. Gwiazdki oznaczają elementy, które zostały dodane w tym przykładzie.  
  
 Należy zauważyć, że musisz dodać odwołanie do <xref:System.Net.Http>.  
  
 Można ściągnąć projekt z [próbka asynchroniczna: Dostrajania aplikacji](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea).  
  
```vb  
' Add an Imports directive and a reference for System.Net.Http.  
Imports System.Net.Http  
  
' Add the following Imports directive for System.Threading.  
Imports System.Threading  
  
Class MainWindow  
  
    ' Declare a System.Threading.CancellationTokenSource.  
    Dim cts As CancellationTokenSource  
  
    Private Async Sub startButton_Click(sender As Object, e As RoutedEventArgs)  
  
        ' Instantiate the CancellationTokenSource.  
        cts = New CancellationTokenSource()  
  
        resultsTextBox.Clear()  
  
        Try  
            ' ***Set up the CancellationTokenSource to cancel after 2.5 seconds. (You   
            ' can adjust the time.)  
            cts.CancelAfter(2500)  
  
            Await AccessTheWebAsync(cts.Token)  
            resultsTextBox.Text &= vbCrLf & "Downloads complete."  
  
        Catch ex As OperationCanceledException  
            resultsTextBox.Text &= vbCrLf & "Downloads canceled." & vbCrLf  
  
        Catch ex As Exception  
            resultsTextBox.Text &= vbCrLf & "Downloads failed." & vbCrLf  
        End Try  
  
        ' Set the CancellationTokenSource to Nothing when the download is complete.  
        cts = Nothing  
    End Sub  
  
    ' You can still include a Cancel button if you want to.  
    Private Sub cancelButton_Click(sender As Object, e As RoutedEventArgs)  
  
        If cts IsNot Nothing Then  
            cts.Cancel()  
        End If  
    End Sub  
  
    ' Provide a parameter for the CancellationToken.  
    ' Change the return type to Task because the method has no return statement.  
    Async Function AccessTheWebAsync(ct As CancellationToken) As Task  
  
        Dim client As HttpClient = New HttpClient()  
  
        ' Call SetUpURLList to make a list of web addresses.  
        Dim urlList As List(Of String) = SetUpURLList()  
  
        ' Process each element in the list of web addresses.  
        For Each url In urlList  
            ' GetAsync returns a Task(Of HttpResponseMessage).   
            ' Argument ct carries the message if the Cancel button is chosen.   
            ' Note that the Cancel button can cancel all remaining downloads.  
            Dim response As HttpResponseMessage = Await client.GetAsync(url, ct)  
  
            ' Retrieve the website contents from the HttpResponseMessage.  
            Dim urlContents As Byte() = Await response.Content.ReadAsByteArrayAsync()  
  
            resultsTextBox.Text &=  
                String.Format(vbCrLf & "Length of the downloaded string: {0}." & vbCrLf, urlContents.Length)  
        Next  
    End Function  
  
    ' Add a method that creates a list of web addresses.  
    Private Function SetUpURLList() As List(Of String)  
  
        Dim urls = New List(Of String) From  
            {  
                "https://msdn.microsoft.com",  
                "https://msdn.microsoft.com/library/hh290138.aspx",  
                "https://msdn.microsoft.com/library/hh290140.aspx",  
                "https://msdn.microsoft.com/library/dd470362.aspx",  
                "https://msdn.microsoft.com/library/aa578028.aspx",  
                "https://msdn.microsoft.com/library/ms404677.aspx",  
                "https://msdn.microsoft.com/library/ff730837.aspx"  
            }  
        Return urls  
    End Function  
  
End Class  
  
' Sample output:  
  
' Length of the downloaded string: 35990.  
  
' Length of the downloaded string: 407399.  
  
' Length of the downloaded string: 226091.  
  
' Downloads canceled.  
```  
  
## <a name="see-also"></a>Zobacz także
- [Programowanie asynchroniczne z Async i Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md)
- [Przewodnik: Uzyskiwanie dostępu do sieci Web za pomocą Async i Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)
- [Anulowanie zadania asynchronicznego lub listy zadań (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/cancel-an-async-task-or-a-list-of-tasks.md)
- [Dostrajanie aplikacji Async (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/fine-tuning-your-async-application.md)
- [Próbka asynchroniczna: Dostrajanie aplikacji](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea)
