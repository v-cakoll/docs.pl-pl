---
title: 'Porady: wpisywanie tekstu do pliku'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
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
caps.latest.revision: "29"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: ea0ff0d79762ba47214217a261a325aad9f5eaf6
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="how-to-write-text-to-a-file"></a><span data-ttu-id="48e7e-102">Porady: wpisywanie tekstu do pliku</span><span class="sxs-lookup"><span data-stu-id="48e7e-102">How to: Write Text to a File</span></span>
<span data-ttu-id="48e7e-103">Ten temat przedstawia różne sposoby tekst może zapisywać do pliku dla aplikacji .NET Framework lub [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikacji.</span><span class="sxs-lookup"><span data-stu-id="48e7e-103">This topic shows different ways you can write text to a file for .NET Framework applications or [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] apps.</span></span> <span data-ttu-id="48e7e-104">Następujące klasy i metody są zwykle używane do zapisywanie tekstu do pliku:</span><span class="sxs-lookup"><span data-stu-id="48e7e-104">The following classes and methods are typically used to write text to a file:</span></span>  
  
-   <span data-ttu-id="48e7e-105"><xref:System.IO.StreamWriter>-zawiera metody do zapisu w pliku synchronicznie (<xref:System.IO.StreamWriter.Write%2A> lub <xref:System.IO.TextWriter.WriteLine%2A>) lub asynchronicznie (<xref:System.IO.StreamWriter.WriteAsync%2A> i <xref:System.IO.StreamWriter.WriteLineAsync%2A>).</span><span class="sxs-lookup"><span data-stu-id="48e7e-105"><xref:System.IO.StreamWriter> - it contains methods to write to a file synchronously (<xref:System.IO.StreamWriter.Write%2A> or <xref:System.IO.TextWriter.WriteLine%2A>) or asynchronously (<xref:System.IO.StreamWriter.WriteAsync%2A> and <xref:System.IO.StreamWriter.WriteLineAsync%2A>).</span></span>  
  
-   <span data-ttu-id="48e7e-106"><xref:System.IO.File>— do użycia z aplikacji .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="48e7e-106"><xref:System.IO.File> – to be used with .NET Framework applications.</span></span> <span data-ttu-id="48e7e-107">Zapewnia metody statyczne do zapisywanie tekstu do pliku, takich jak <xref:System.IO.File.WriteAllLines%2A> i <xref:System.IO.File.WriteAllText%2A>, lub Dołącz tekstu do pliku (<xref:System.IO.File.AppendAllLines%2A>, <xref:System.IO.File.AppendAllText%2A> lub <xref:System.IO.File.AppendText%2A>).</span><span class="sxs-lookup"><span data-stu-id="48e7e-107">It provides static methods to write text to a file such as <xref:System.IO.File.WriteAllLines%2A> and <xref:System.IO.File.WriteAllText%2A>, or to append text to a file (<xref:System.IO.File.AppendAllLines%2A>, <xref:System.IO.File.AppendAllText%2A> or <xref:System.IO.File.AppendText%2A>).</span></span>  
  
-   <span data-ttu-id="48e7e-108">[FileIO](https://msdn.microsoft.com/library/windows/apps/windows.storage.fileio.aspx) — do użycia z [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikacji.</span><span class="sxs-lookup"><span data-stu-id="48e7e-108">[FileIO](https://msdn.microsoft.com/library/windows/apps/windows.storage.fileio.aspx) - to be used with [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] apps.</span></span> <span data-ttu-id="48e7e-109">Zawiera on metod asynchronicznych próbę zapisania tekstu do pliku ([WriteLinesAsync](https://msdn.microsoft.com/library/windows/apps/windows.storage.fileio.writelinesasync.aspx) lub [WriteTextAsync](https://msdn.microsoft.com/library/windows/apps/windows.storage.fileio.writetextasync.aspx)) lub Dołącz tekstu do pliku ([AppendLinesAsync](https://msdn.microsoft.com/library/windows/apps/windows.storage.fileio.appendlinesasync.aspx) lub [ AppendTextAsync](https://msdn.microsoft.com/library/windows/apps/windows.storage.fileio.appendtextasync.aspx)).</span><span class="sxs-lookup"><span data-stu-id="48e7e-109">It contains asynchronous methods to write text to a file ([WriteLinesAsync](https://msdn.microsoft.com/library/windows/apps/windows.storage.fileio.writelinesasync.aspx) or [WriteTextAsync](https://msdn.microsoft.com/library/windows/apps/windows.storage.fileio.writetextasync.aspx)) or to append text to a file ([AppendLinesAsync](https://msdn.microsoft.com/library/windows/apps/windows.storage.fileio.appendlinesasync.aspx) or [AppendTextAsync](https://msdn.microsoft.com/library/windows/apps/windows.storage.fileio.appendtextasync.aspx)).</span></span>  
  
 <span data-ttu-id="48e7e-110">Przykłady te zostały uproszczone aby skupić się na zadanie wykonywane.</span><span class="sxs-lookup"><span data-stu-id="48e7e-110">The samples have been kept simple in order to focus on the task being performed.</span></span> <span data-ttu-id="48e7e-111">Z tego powodu próbki wykonać sprawdzanie błędów minimalnego i obsługa wyjątków, jeśli wszystkie.</span><span class="sxs-lookup"><span data-stu-id="48e7e-111">For this reason, the samples perform minimal error checking and exception handling, if any.</span></span> <span data-ttu-id="48e7e-112">Rzeczywistych aplikacji zwykle zapewnia bardziej niezawodne sprawdzanie błędów i wyjątków.</span><span class="sxs-lookup"><span data-stu-id="48e7e-112">A real-world application generally provides more robust error checking and exception handling.</span></span>  
  
## <a name="example"></a><span data-ttu-id="48e7e-113">Przykład</span><span class="sxs-lookup"><span data-stu-id="48e7e-113">Example</span></span>  
 <span data-ttu-id="48e7e-114">Poniższy przykład przedstawia sposób synchronicznie zapisywanie tekstu do nowego pliku za pomocą <xref:System.IO.StreamWriter> klasy jeden wiersz jednocześnie.</span><span class="sxs-lookup"><span data-stu-id="48e7e-114">The following example shows how to synchronously write text to a new file using the <xref:System.IO.StreamWriter> class, one line at a time.</span></span> <span data-ttu-id="48e7e-115">Nowy plik tekstowy zostanie zapisana w folderze Moje dokumenty użytkownika.</span><span class="sxs-lookup"><span data-stu-id="48e7e-115">The new text file is saved to the user's My Documents folder.</span></span> <span data-ttu-id="48e7e-116">Ponieważ <xref:System.IO.StreamWriter> obiekt został zadeklarowany i w `using` instrukcji <xref:System.IO.StreamWriter.Dispose%2A> wywoływana jest metoda, która automatycznie opróżnia i zamknięcie strumienia.</span><span class="sxs-lookup"><span data-stu-id="48e7e-116">Because the <xref:System.IO.StreamWriter> object is declared and instantiated in a `using` statement, the <xref:System.IO.StreamWriter.Dispose%2A> method is invoked which automatically flushes and closes the stream.</span></span>  
  
 [!code-csharp[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/source.cs#writeline)] 
 [!code-vb[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/source.vb#writeline)]  
  
## <a name="example"></a><span data-ttu-id="48e7e-117">Przykład</span><span class="sxs-lookup"><span data-stu-id="48e7e-117">Example</span></span>  
 <span data-ttu-id="48e7e-118">Poniższy przykład pokazuje, jak dołączyć tekst do istniejącego pliku przy użyciu <xref:System.IO.StreamWriter> klasy.</span><span class="sxs-lookup"><span data-stu-id="48e7e-118">The following example shows how to append text to an existing file using the <xref:System.IO.StreamWriter> class.</span></span> <span data-ttu-id="48e7e-119">Używa tego samego pliku tekstowego z poprzedniego przykładu.</span><span class="sxs-lookup"><span data-stu-id="48e7e-119">It uses the same text file from the previous example.</span></span>  
  
 [!code-csharp[Conceptual.BasicIO.TextFiles#AppendText](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/source.cs#appendtext)] 
 [!code-vb[Conceptual.BasicIO.TextFiles#AppendText](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/source.vb#appendtext)]     
  
## <a name="example"></a><span data-ttu-id="48e7e-120">Przykład</span><span class="sxs-lookup"><span data-stu-id="48e7e-120">Example</span></span>  
 <span data-ttu-id="48e7e-121">Poniższy przykład przedstawia sposób asynchronicznie zapisywanie tekstu do nowego pliku za pomocą <xref:System.IO.StreamWriter> klasy.</span><span class="sxs-lookup"><span data-stu-id="48e7e-121">The following example shows how to asynchronously write text to a new file using the <xref:System.IO.StreamWriter> class.</span></span> <span data-ttu-id="48e7e-122">Aby można było wywołać <xref:System.IO.StreamWriter.WriteAsync%2A> metody, wywołanie metody musi występować w `async` metody.</span><span class="sxs-lookup"><span data-stu-id="48e7e-122">In order to invoke the <xref:System.IO.StreamWriter.WriteAsync%2A> method, the method call needs to be within an `async` method.</span></span> <span data-ttu-id="48e7e-123">Nowy plik tekstowy zostanie zapisana w folderze Moje dokumenty użytkownika.</span><span class="sxs-lookup"><span data-stu-id="48e7e-123">The new text file is saved to the user's My Documents folder.</span></span>  
  
 [!code-csharp[Conceptual.BasicIO.TextFiles#WriteAsync](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/source.cs#writeasync)] 
 [!code-vb[Conceptual.BasicIO.TextFiles#WriteAsync](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/source.vb#writeasync)]  
  
## <a name="example"></a><span data-ttu-id="48e7e-124">Przykład</span><span class="sxs-lookup"><span data-stu-id="48e7e-124">Example</span></span>  
 <span data-ttu-id="48e7e-125">Poniższy przykład przedstawia sposób zapisywanie tekstu do pliku i dołączyć nowe wiersze tekstu do tego samego pliku przy użyciu <xref:System.IO.File> klasy.</span><span class="sxs-lookup"><span data-stu-id="48e7e-125">The following example shows how to write text to a new file and append new lines of text to the same file using the <xref:System.IO.File> class.</span></span> <span data-ttu-id="48e7e-126"><xref:System.IO.File.WriteAllText%2A> i <xref:System.IO.File.AppendAllLines%2A> metod otwierających i zamykających plik w automatycznie.</span><span class="sxs-lookup"><span data-stu-id="48e7e-126">The <xref:System.IO.File.WriteAllText%2A> and <xref:System.IO.File.AppendAllLines%2A> methods open and close the file automatically.</span></span> <span data-ttu-id="48e7e-127">Jeśli ścieżka osobie <xref:System.IO.File.WriteAllText%2A> metody już istnieje, plik zostanie zastąpiony.</span><span class="sxs-lookup"><span data-stu-id="48e7e-127">If the path you provide to the <xref:System.IO.File.WriteAllText%2A> method already exists, the file will be overwritten.</span></span>  
  
 [!code-csharp[Conceptual.BasicIO.TextFiles#WriteFile](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/source.cs#writefile)] 
 [!code-vb[Conceptual.BasicIO.TextFiles#WriteFile](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/source.vb#writefile)]  
  
## <a name="example"></a><span data-ttu-id="48e7e-128">Przykład</span><span class="sxs-lookup"><span data-stu-id="48e7e-128">Example</span></span>  
 <span data-ttu-id="48e7e-129">Poniższy przykład przedstawia sposób asynchronicznego zapisu danych wejściowych użytkownika do pliku tekstowego w [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikacji.</span><span class="sxs-lookup"><span data-stu-id="48e7e-129">The following example shows how to asynchronously write user input to a text file in a [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] app.</span></span> <span data-ttu-id="48e7e-130">Ze względów bezpieczeństwa otwarcie pliku z [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikacji zwykle wymaga użycia [FileOpenPicker](http://msdn.microsoft.com/library/windows/apps/windows.storage.pickers.fileopenpicker.aspx) formantu.</span><span class="sxs-lookup"><span data-stu-id="48e7e-130">Because of security considerations, opening a file from a [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] app typically requires the use of a [FileOpenPicker](http://msdn.microsoft.com/library/windows/apps/windows.storage.pickers.fileopenpicker.aspx) control.</span></span> <span data-ttu-id="48e7e-131">W tym przykładzie `FileOpenPicker` jest filtrowana w celu wyświetlania plików tekstowych.</span><span class="sxs-lookup"><span data-stu-id="48e7e-131">In this example, the `FileOpenPicker` is filtered to show text files.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="48e7e-132">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="48e7e-132">See Also</span></span>  
 <xref:System.IO.StreamWriter>  
 <xref:System.IO.File.CreateText%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="48e7e-133">Instrukcje: wyliczanie katalogów i plików</span><span class="sxs-lookup"><span data-stu-id="48e7e-133">How to: Enumerate Directories and Files</span></span>](../../../docs/standard/io/how-to-enumerate-directories-and-files.md)  
 [<span data-ttu-id="48e7e-134">Instrukcje: odczyt i zapis we właśnie utworzonym pliku danych</span><span class="sxs-lookup"><span data-stu-id="48e7e-134">How to: Read and Write to a Newly Created Data File</span></span>](../../../docs/standard/io/how-to-read-and-write-to-a-newly-created-data-file.md)  
 [<span data-ttu-id="48e7e-135">Instrukcje: otwieranie pliku dziennika i dołączanie do niego</span><span class="sxs-lookup"><span data-stu-id="48e7e-135">How to: Open and Append to a Log File</span></span>](../../../docs/standard/io/how-to-open-and-append-to-a-log-file.md)  
 [<span data-ttu-id="48e7e-136">Instrukcje: odczytywanie tekstu z pliku</span><span class="sxs-lookup"><span data-stu-id="48e7e-136">How to: Read Text from a File</span></span>](../../../docs/standard/io/how-to-read-text-from-a-file.md)  
 [<span data-ttu-id="48e7e-137">Plik i strumienia I-O</span><span class="sxs-lookup"><span data-stu-id="48e7e-137">File and Stream I-O</span></span>](../../../docs/standard/io/index.md)
