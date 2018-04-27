---
title: 'Porady: odczyt z plików testowych w Visual Basic'
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- extended characters [Visual Basic], reading
- reading text files [Visual Basic]
- reading data, text files
- examples [Visual Basic], reading text files
- text files [Visual Basic], reading
ms.assetid: 735fe9d7-0f7a-4185-ba02-f35e580ec4b8
caps.latest.revision: 27
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: e39b08fcee382674fcf6af07f9da7439eb1bea69
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-read-from-text-files-in-visual-basic"></a><span data-ttu-id="93276-102">Porady: odczyt z plików testowych w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="93276-102">How to: Read From Text Files in Visual Basic</span></span>
<span data-ttu-id="93276-103"><xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.ReadAllText%2A> Metody `My.Computer.FileSystem` obiektu służy do odczytu z pliku tekstowego.</span><span class="sxs-lookup"><span data-stu-id="93276-103">The <xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.ReadAllText%2A> method of the `My.Computer.FileSystem` object allows you to read from a text file.</span></span> <span data-ttu-id="93276-104">Kodowanie pliku może być określone, jeśli zawartość pliku używa kodowania, takiego jak ASCII lub UTF-8.</span><span class="sxs-lookup"><span data-stu-id="93276-104">The file encoding can be specified if the contents of the file use an encoding such as ASCII or UTF-8.</span></span>  
  
 <span data-ttu-id="93276-105">Podczas odczytu z pliku używającego znaków rozszerzonych, trzeba będzie określić kodowanie pliku.</span><span class="sxs-lookup"><span data-stu-id="93276-105">If you are reading from a file with extended characters, you will need to specify the file encoding.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="93276-106">Aby odczytać plik pojedynczy wiersz tekstu w czasie, należy użyć <xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.OpenTextFileReader%2A> metody `My.Computer.FileSystem` obiektu.</span><span class="sxs-lookup"><span data-stu-id="93276-106">To read a file a single line of text at a time, use the <xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.OpenTextFileReader%2A> method of the `My.Computer.FileSystem` object.</span></span> <span data-ttu-id="93276-107">`OpenTextFileReader` Metoda zwraca <xref:System.IO.StreamReader> obiektu.</span><span class="sxs-lookup"><span data-stu-id="93276-107">The `OpenTextFileReader` method returns a <xref:System.IO.StreamReader> object.</span></span> <span data-ttu-id="93276-108">Można użyć <xref:System.IO.StreamReader.ReadLine%2A> metody `StreamReader` obiektu do odczytania jeden wiersz pliku naraz.</span><span class="sxs-lookup"><span data-stu-id="93276-108">You can use the <xref:System.IO.StreamReader.ReadLine%2A> method of the `StreamReader` object to read a file one line at a time.</span></span> <span data-ttu-id="93276-109">Możesz przetestować końca pliku przy użyciu <xref:System.IO.StreamReader.EndOfStream%2A> metody `StreamReader` obiektu.</span><span class="sxs-lookup"><span data-stu-id="93276-109">You can test for the end of the file using the <xref:System.IO.StreamReader.EndOfStream%2A> method of the `StreamReader` object.</span></span>  
  
### <a name="to-read-from-a-text-file"></a><span data-ttu-id="93276-110">Aby odczytać z pliku tekstowego</span><span class="sxs-lookup"><span data-stu-id="93276-110">To read from a text file</span></span>  
  
-   <span data-ttu-id="93276-111">Użyj `ReadAllText` metody `My.Computer.FileSystem` obiektu można odczytać zawartości pliku tekstowego na ciąg, podając ścieżkę.</span><span class="sxs-lookup"><span data-stu-id="93276-111">Use the `ReadAllText` method of the `My.Computer.FileSystem` object to read the contents of a text file into a string, supplying the path.</span></span> <span data-ttu-id="93276-112">Poniższy przykład odczytuje zawartość test.txt jako ciąg i wyświetla go w oknie komunikatu.</span><span class="sxs-lookup"><span data-stu-id="93276-112">The following example reads the contents of test.txt into a string and then displays it in a message box.</span></span>  
  
     [!code-vb[VbFileIORead#2](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-from-text-files_1.vb)]  
  
### <a name="to-read-from-a-text-file-that-is-encoded"></a><span data-ttu-id="93276-113">Aby odczytać z pliku tekstowego, który jest kodowany</span><span class="sxs-lookup"><span data-stu-id="93276-113">To read from a text file that is encoded</span></span>  
  
-   <span data-ttu-id="93276-114">Użyj `ReadAllText` metody `My.Computer.FileSystem` obiekt, aby przeczytać jego zawartość pliku tekstowego na ciąg, podając ścieżkę i typ kodowania pliku.</span><span class="sxs-lookup"><span data-stu-id="93276-114">Use the `ReadAllText` method of the `My.Computer.FileSystem` object to read the contents of a text file into a string, supplying the path and file encoding type.</span></span> <span data-ttu-id="93276-115">Poniższy przykład odczytuje zawartość pliku z kodowaniem UTF32 test.txt jako ciąg i wyświetla go w oknie komunikatu.</span><span class="sxs-lookup"><span data-stu-id="93276-115">The following example reads the contents of the UTF32 file test.txt into a string and then displays it in a message box.</span></span>  
  
     [!code-vb[VbFileIORead#3](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-from-text-files_2.vb)]  
  
## <a name="robust-programming"></a><span data-ttu-id="93276-116">Niezawodne programowanie</span><span class="sxs-lookup"><span data-stu-id="93276-116">Robust Programming</span></span>  
 <span data-ttu-id="93276-117">Następujące warunki mogą spowodować wyjątek:</span><span class="sxs-lookup"><span data-stu-id="93276-117">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="93276-118">Ścieżka nie jest prawidłowy dla jednego z następujących powodów: jest to ciąg o zerowej długości, zawiera tylko biały znak, zawiera nieprawidłowe znaki lub jest ścieżką urządzenia (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="93276-118">The path is not valid for one of the following reasons: it is a zero-length string, it contains only white space, it contains invalid characters, or it is a device path (<xref:System.ArgumentException>).</span></span>  
  
-   <span data-ttu-id="93276-119">Ścieżka jest nieprawidłowa, ponieważ jest on `Nothing` (<xref:System.ArgumentNullException>).</span><span class="sxs-lookup"><span data-stu-id="93276-119">The path is not valid because it is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
-   <span data-ttu-id="93276-120">Plik nie istnieje (<xref:System.IO.FileNotFoundException>).</span><span class="sxs-lookup"><span data-stu-id="93276-120">The file does not exist (<xref:System.IO.FileNotFoundException>).</span></span>  
  
-   <span data-ttu-id="93276-121">Plik jest używany przez inny proces lub błąd We/Wy (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="93276-121">The file is in use by another process or an I/O error occurs (<xref:System.IO.IOException>).</span></span>  
  
-   <span data-ttu-id="93276-122">Ścieżka przekracza maksymalną długość zdefiniowana w systemie (<xref:System.IO.PathTooLongException>).</span><span class="sxs-lookup"><span data-stu-id="93276-122">The path exceeds the system-defined maximum length (<xref:System.IO.PathTooLongException>).</span></span>  
  
-   <span data-ttu-id="93276-123">Nazwę pliku lub katalogu w ścieżce zawiera dwukropek (:) lub jest w nieprawidłowym formacie (<xref:System.NotSupportedException>).</span><span class="sxs-lookup"><span data-stu-id="93276-123">A file or directory name in the path contains a colon (:) or is in an invalid format (<xref:System.NotSupportedException>).</span></span>  
  
-   <span data-ttu-id="93276-124">Nie ma wystarczającej ilości pamięci do zapisania ciągu do buforu (<xref:System.OutOfMemoryException>).</span><span class="sxs-lookup"><span data-stu-id="93276-124">There is not enough memory to write the string to buffer (<xref:System.OutOfMemoryException>).</span></span>  
  
-   <span data-ttu-id="93276-125">Użytkownik nie ma wystarczających uprawnień, aby wyświetlić ścieżkę (<xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="93276-125">The user lacks necessary permissions to view the path (<xref:System.Security.SecurityException>).</span></span>  
  
 <span data-ttu-id="93276-126">Nie należy podejmować decyzji dotyczących zawartości pliku na podstawie rozszerzenia nazwy pliku.</span><span class="sxs-lookup"><span data-stu-id="93276-126">Do not make decisions about the contents of the file based on the name of the file.</span></span> <span data-ttu-id="93276-127">Na przykład plik Form1.vb nie może być plik źródłowy języka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="93276-127">For example, the file Form1.vb may not be a Visual Basic source file.</span></span>  
  
 <span data-ttu-id="93276-128">Sprawdź wszystkie dane wejściowe, zanim użyjesz danych w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="93276-128">Verify all inputs before using the data in your application.</span></span> <span data-ttu-id="93276-129">Zawartość pliku może się różnić od oczekiwanej i metody odczytu z pliku nie zadziałają.</span><span class="sxs-lookup"><span data-stu-id="93276-129">The contents of the file may not be what is expected, and methods to read from the file may fail.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="93276-130">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="93276-130">See Also</span></span>  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem>  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.ReadAllText%2A>  
 [<span data-ttu-id="93276-131">Odczyt z plików</span><span class="sxs-lookup"><span data-stu-id="93276-131">Reading from Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/reading-from-files.md)  
 [<span data-ttu-id="93276-132">Instrukcje: odczyt z rozdzielonych przecinkami plików testowych</span><span class="sxs-lookup"><span data-stu-id="93276-132">How to: Read From Comma-Delimited Text Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-comma-delimited-text-files.md)  
 [<span data-ttu-id="93276-133">Instrukcje: odczyt z plików testowych o stałej szerokości</span><span class="sxs-lookup"><span data-stu-id="93276-133">How to: Read From Fixed-width Text Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-fixed-width-text-files.md)  
 [<span data-ttu-id="93276-134">Instrukcje: odczyt z plików tekstowych w wielu formatach</span><span class="sxs-lookup"><span data-stu-id="93276-134">How to: Read From Text Files with Multiple Formats</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-text-files-with-multiple-formats.md)  
 [<span data-ttu-id="93276-135">Rozwiązywanie problemów: odczytywanie z plików tekstowych oraz zapisywanie w nich</span><span class="sxs-lookup"><span data-stu-id="93276-135">Troubleshooting: Reading from and Writing to Text Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/troubleshooting-reading-from-and-writing-to-text-files.md)  
 [<span data-ttu-id="93276-136">Wskazówki: Manipulowanie plikami i katalogami w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="93276-136">Walkthrough: Manipulating Files and Directories in Visual Basic</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/walkthrough-manipulating-files-and-directories.md)  
 [<span data-ttu-id="93276-137">Kodowanie pliku</span><span class="sxs-lookup"><span data-stu-id="93276-137">File Encodings</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/file-encodings.md)
