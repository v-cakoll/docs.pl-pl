---
title: 'Porady: wpisywanie tekstu do pliku'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- writing text to files
- I/O [.NET Framework], writing text to files
- streams, writing text to files
- data streams, writing text to files
ms.assetid: 060cbe06-2adf-4337-9e7b-961a5c840208
author: mairaw
ms.author: mairaw
ms.openlocfilehash: bc8082175047271c92f9a9a17a49534ffc9546a9
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/08/2018
ms.locfileid: "44180634"
---
# <a name="how-to-write-text-to-a-file"></a>Porady: wpisywanie tekstu do pliku
Ten temat przedstawia różne sposoby można wpisać tekst w pliku dla aplikacji .NET Framework lub [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikacji. Następujące klasy i metody są zwykle używane do zapisywanie tekstu do pliku:  
  
-   <xref:System.IO.StreamWriter> — zawiera metody służące do zapisu do pliku synchronicznie (<xref:System.IO.StreamWriter.Write%2A> lub <xref:System.IO.TextWriter.WriteLine%2A>) lub asynchronicznie (<xref:System.IO.StreamWriter.WriteAsync%2A> i <xref:System.IO.StreamWriter.WriteLineAsync%2A>).  
  
-   <xref:System.IO.File> — do użycia w aplikacjach .NET Framework. Zapewnia metody statyczne próbę zapisania tekstu do pliku, taką jak <xref:System.IO.File.WriteAllLines%2A> i <xref:System.IO.File.WriteAllText%2A>, lub dołączyć tekst do pliku (<xref:System.IO.File.AppendAllLines%2A>, <xref:System.IO.File.AppendAllText%2A> lub <xref:System.IO.File.AppendText%2A>).  
  
-   [FileIO](https://msdn.microsoft.com/library/windows/apps/windows.storage.fileio.aspx) — do użycia z [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikacji. Zawiera on metod asynchronicznych próbę zapisania tekstu do pliku ([WriteLinesAsync](https://msdn.microsoft.com/library/windows/apps/windows.storage.fileio.writelinesasync.aspx) lub [WriteTextAsync](https://msdn.microsoft.com/library/windows/apps/windows.storage.fileio.writetextasync.aspx)) lub dołączyć tekst do pliku ([AppendLinesAsync](https://msdn.microsoft.com/library/windows/apps/windows.storage.fileio.appendlinesasync.aspx) lub [ AppendTextAsync](https://msdn.microsoft.com/library/windows/apps/windows.storage.fileio.appendtextasync.aspx)).  

- <xref:System.IO.Path> — do użycia na ciągi, które zawierają informacje o ścieżce pliku lub katalogu. Zawiera on <xref:System.IO.Path.Combine%2A> metody, która umożliwia łączenie ciągów, aby zbudować ścieżki pliku lub katalogu.


 Przykłady te zostały uproszczone celu skupiania się na zadanie wykonywane. Z tego powodu przykłady wykonać sprawdzanie błędów minimalny i obsługę wyjątków, jeśli istnieje. Aplikacji rzeczywistych zwykle zapewnia bardziej niezawodne sprawdzanie błędów i wyjątków.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak synchronicznie zapisywanie tekstu do nowego pliku przy użyciu <xref:System.IO.StreamWriter> klasy jeden wiersz w danym momencie. Nowy plik tekstowy są zapisywane w folderze Moje dokumenty użytkownika. Ponieważ <xref:System.IO.StreamWriter> obiektu jest zadeklarowana i tworzone w `using` instrukcji <xref:System.IO.StreamWriter.Dispose%2A> wywoływana jest metoda, która automatycznie opróżnia i zamyka strumienia.  
  
 [!code-csharp[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/source.cs#writeline)] 
 [!code-vb[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/source.vb#writeline)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak dołączyć tekst do istniejącego pliku przy użyciu <xref:System.IO.StreamWriter> klasy. Używa tego samego pliku tekstowego z poprzedniego przykładu.  
  
 [!code-csharp[Conceptual.BasicIO.TextFiles#AppendText](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/source.cs#appendtext)] 
 [!code-vb[Conceptual.BasicIO.TextFiles#AppendText](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/source.vb#appendtext)]     
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak asynchronicznie zapisywanie tekstu do nowego pliku przy użyciu <xref:System.IO.StreamWriter> klasy. Aby można było wywołać <xref:System.IO.StreamWriter.WriteAsync%2A> metoda, wywołanie metody musi mieścić się w `async` metody. Nowy plik tekstowy są zapisywane w folderze Moje dokumenty użytkownika.  
  
 [!code-csharp[Conceptual.BasicIO.TextFiles#WriteAsync](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/source.cs#writeasync)] 
 [!code-vb[Conceptual.BasicIO.TextFiles#WriteAsync](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/source.vb#writeasync)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak zapisywanie tekstu do nowego pliku i dołączyć nowe wiersze tekstu do tego samego pliku przy użyciu <xref:System.IO.File> klasy. <xref:System.IO.File.WriteAllText%2A> i <xref:System.IO.File.AppendAllLines%2A> metod Otwórz i zamknij plik automatycznie. Jeśli ścieżka uzyskiwanie <xref:System.IO.File.WriteAllText%2A> metody już istnieje, plik zostanie zastąpiony.  
  
 [!code-csharp[Conceptual.BasicIO.TextFiles#WriteFile](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/source.cs#writefile)] 
 [!code-vb[Conceptual.BasicIO.TextFiles#WriteFile](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/source.vb#writefile)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak asynchronicznego zapisu danych wejściowych użytkownika do pliku tekstowego w [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikacji. Ze względów bezpieczeństwa, otwierając plik z [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikacji zwykle wymaga użycia [FileOpenPicker](https://msdn.microsoft.com/library/windows/apps/windows.storage.pickers.fileopenpicker.aspx) kontroli. W tym przykładzie `FileOpenPicker` jest filtrowany w celu wyświetlania plików tekstowych.  
  
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
  
## <a name="see-also"></a>Zobacz także

- <xref:System.IO.StreamWriter>  
- <xref:System.IO.Path>  
- <xref:System.IO.File.CreateText%2A?displayProperty=nameWithType>  
- [Instrukcje: wyliczanie katalogów i plików](../../../docs/standard/io/how-to-enumerate-directories-and-files.md)  
- [Instrukcje: odczyt i zapis we właśnie utworzonym pliku danych](../../../docs/standard/io/how-to-read-and-write-to-a-newly-created-data-file.md)  
- [Instrukcje: otwieranie pliku dziennika i dołączanie do niego](../../../docs/standard/io/how-to-open-and-append-to-a-log-file.md)  
- [Instrukcje: odczytywanie tekstu z pliku](../../../docs/standard/io/how-to-read-text-from-a-file.md)  
- [We/Wy plików i strumieni](../../../docs/standard/io/index.md)
