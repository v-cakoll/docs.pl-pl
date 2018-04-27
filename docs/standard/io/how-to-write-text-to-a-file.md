---
title: 'Porady: wpisywanie tekstu do pliku'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology: dotnet-standard
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- writing text to files
- I/O [.NET Framework], writing text to files
- streams, writing text to files
- data streams, writing text to files
ms.assetid: 060cbe06-2adf-4337-9e7b-961a5c840208
caps.latest.revision: 29
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 926dfe1ea254fdb6460c835f58721f54609ddc90
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-write-text-to-a-file"></a>Porady: wpisywanie tekstu do pliku
Ten temat przedstawia różne sposoby tekst może zapisywać do pliku dla aplikacji .NET Framework lub [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikacji. Następujące klasy i metody są zwykle używane do zapisywanie tekstu do pliku:  
  
-   <xref:System.IO.StreamWriter> -zawiera metody do zapisu w pliku synchronicznie (<xref:System.IO.StreamWriter.Write%2A> lub <xref:System.IO.TextWriter.WriteLine%2A>) lub asynchronicznie (<xref:System.IO.StreamWriter.WriteAsync%2A> i <xref:System.IO.StreamWriter.WriteLineAsync%2A>).  
  
-   <xref:System.IO.File> — do użycia z aplikacji .NET Framework. Zapewnia metody statyczne do zapisywanie tekstu do pliku, takich jak <xref:System.IO.File.WriteAllLines%2A> i <xref:System.IO.File.WriteAllText%2A>, lub Dołącz tekstu do pliku (<xref:System.IO.File.AppendAllLines%2A>, <xref:System.IO.File.AppendAllText%2A> lub <xref:System.IO.File.AppendText%2A>).  
  
-   [FileIO](https://msdn.microsoft.com/library/windows/apps/windows.storage.fileio.aspx) — do użycia z [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikacji. Zawiera on metod asynchronicznych próbę zapisania tekstu do pliku ([WriteLinesAsync](https://msdn.microsoft.com/library/windows/apps/windows.storage.fileio.writelinesasync.aspx) lub [WriteTextAsync](https://msdn.microsoft.com/library/windows/apps/windows.storage.fileio.writetextasync.aspx)) lub Dołącz tekstu do pliku ([AppendLinesAsync](https://msdn.microsoft.com/library/windows/apps/windows.storage.fileio.appendlinesasync.aspx) lub [ AppendTextAsync](https://msdn.microsoft.com/library/windows/apps/windows.storage.fileio.appendtextasync.aspx)).  

- <xref:System.IO.Path> -ma być używany dla ciągów, które zawierają informacje o ścieżce pliku lub katalogu. Zawiera on <xref:System.IO.Path.Combine%2A> metodę, która umożliwia łączenie ciągów zbudować ścieżki pliku lub katalogu.


 Przykłady te zostały uproszczone aby skupić się na zadanie wykonywane. Z tego powodu próbki wykonać sprawdzanie błędów minimalnego i obsługa wyjątków, jeśli wszystkie. Rzeczywistych aplikacji zwykle zapewnia bardziej niezawodne sprawdzanie błędów i wyjątków.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia sposób synchronicznie zapisywanie tekstu do nowego pliku za pomocą <xref:System.IO.StreamWriter> klasy jeden wiersz jednocześnie. Nowy plik tekstowy zostanie zapisana w folderze Moje dokumenty użytkownika. Ponieważ <xref:System.IO.StreamWriter> obiekt został zadeklarowany i w `using` instrukcji <xref:System.IO.StreamWriter.Dispose%2A> wywoływana jest metoda, która automatycznie opróżnia i zamknięcie strumienia.  
  
 [!code-csharp[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/source.cs#writeline)] 
 [!code-vb[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/source.vb#writeline)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak dołączyć tekst do istniejącego pliku przy użyciu <xref:System.IO.StreamWriter> klasy. Używa tego samego pliku tekstowego z poprzedniego przykładu.  
  
 [!code-csharp[Conceptual.BasicIO.TextFiles#AppendText](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/source.cs#appendtext)] 
 [!code-vb[Conceptual.BasicIO.TextFiles#AppendText](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/source.vb#appendtext)]     
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia sposób asynchronicznie zapisywanie tekstu do nowego pliku za pomocą <xref:System.IO.StreamWriter> klasy. Aby można było wywołać <xref:System.IO.StreamWriter.WriteAsync%2A> metody, wywołanie metody musi występować w `async` metody. Nowy plik tekstowy zostanie zapisana w folderze Moje dokumenty użytkownika.  
  
 [!code-csharp[Conceptual.BasicIO.TextFiles#WriteAsync](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/source.cs#writeasync)] 
 [!code-vb[Conceptual.BasicIO.TextFiles#WriteAsync](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/source.vb#writeasync)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia sposób zapisywanie tekstu do pliku i dołączyć nowe wiersze tekstu do tego samego pliku przy użyciu <xref:System.IO.File> klasy. <xref:System.IO.File.WriteAllText%2A> i <xref:System.IO.File.AppendAllLines%2A> metod otwierających i zamykających plik w automatycznie. Jeśli ścieżka osobie <xref:System.IO.File.WriteAllText%2A> metody już istnieje, plik zostanie zastąpiony.  
  
 [!code-csharp[Conceptual.BasicIO.TextFiles#WriteFile](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/source.cs#writefile)] 
 [!code-vb[Conceptual.BasicIO.TextFiles#WriteFile](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/source.vb#writefile)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia sposób asynchronicznego zapisu danych wejściowych użytkownika do pliku tekstowego w [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikacji. Ze względów bezpieczeństwa otwarcie pliku z [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikacji zwykle wymaga użycia [FileOpenPicker](http://msdn.microsoft.com/library/windows/apps/windows.storage.pickers.fileopenpicker.aspx) formantu. W tym przykładzie `FileOpenPicker` jest filtrowana w celu wyświetlania plików tekstowych.  
  
```xaml  
<Page  
    x:Class="OpenFileWindowsStore.MainPage"  
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
    xmlns:local="using:OpenFileWindowsStore"  
    xmlns:d="http://schemas.microsoft.com/expression/blend/2008"  
    xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"  
    mc:Ignorable="d">  
  
    <Grid Background="{ThemeResource ApplicationPageBackgroundThemeBrush}">  
        <Button Content="save text to a file" HorizontalAlignment="Left" Margin="103,417,0,0" VerticalAlignment="Top"   
                Width="329" Height="86" FontSize="35" Click="Button_Click"/>  
        <TextBox Name="UserInputTextBox"  FontSize="18" HorizontalAlignment="Left" Margin="106,146,0,0"   
                 TextWrapping="Wrap" Text="Write some text here, and select a file to write it to." VerticalAlignment="Top"   
                 Height="201" Width="558" AcceptsReturn="True"/>  
        <TextBlock Name="StatusTextBox" HorizontalAlignment="Left" Margin="106,570,0,147" TextWrapping="Wrap" Text="Status:"   
                   VerticalAlignment="Center" Height="51" Width="1074" FontSize="18" />  
    </Grid>  
</Page>  
```  
  
 [!code-csharp[OpenFileWindowsStore#Code](../../../samples/snippets/csharp/VS_Snippets_CLR/openfilewindowsstore/cs/mainpage.xaml.cs#code)]
 [!code-vb[OpenFileWindowsStore#Code](../../../samples/snippets/visualbasic/VS_Snippets_CLR/openfilewindowsstore/vb/mainpage.xaml.vb#code)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.IO.StreamWriter>  
 <xref:System.IO.Path>  
 <xref:System.IO.File.CreateText%2A?displayProperty=nameWithType>  
 [Instrukcje: wyliczanie katalogów i plików](../../../docs/standard/io/how-to-enumerate-directories-and-files.md)  
 [Instrukcje: odczyt i zapis we właśnie utworzonym pliku danych](../../../docs/standard/io/how-to-read-and-write-to-a-newly-created-data-file.md)  
 [Instrukcje: otwieranie pliku dziennika i dołączanie do niego](../../../docs/standard/io/how-to-open-and-append-to-a-log-file.md)  
 [Instrukcje: odczytywanie tekstu z pliku](../../../docs/standard/io/how-to-read-text-from-a-file.md)  
 [Plik i strumienia I-O](../../../docs/standard/io/index.md)
