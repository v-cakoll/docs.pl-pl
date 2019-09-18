---
title: 'Instrukcje: Odczyt z plików tekstowych w Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- extended characters [Visual Basic], reading
- reading text files [Visual Basic]
- reading data, text files
- examples [Visual Basic], reading text files
- text files [Visual Basic], reading
ms.assetid: 735fe9d7-0f7a-4185-ba02-f35e580ec4b8
ms.openlocfilehash: 26e6d8f9cc64f0f1238afaaf6aaf85d69f6c32ce
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71039431"
---
# <a name="how-to-read-from-text-files-in-visual-basic"></a><span data-ttu-id="9af2c-102">Instrukcje: Odczyt z plików tekstowych w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="9af2c-102">How to: Read From Text Files in Visual Basic</span></span>

<span data-ttu-id="9af2c-103"><xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.ReadAllText%2A> Metoda`My.Computer.FileSystem` obiektu umożliwia odczytywanie z pliku tekstowego.</span><span class="sxs-lookup"><span data-stu-id="9af2c-103">The <xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.ReadAllText%2A> method of the `My.Computer.FileSystem` object allows you to read from a text file.</span></span> <span data-ttu-id="9af2c-104">Kodowanie pliku może być określone, jeśli zawartość pliku używa kodowania, takiego jak ASCII lub UTF-8.</span><span class="sxs-lookup"><span data-stu-id="9af2c-104">The file encoding can be specified if the contents of the file use an encoding such as ASCII or UTF-8.</span></span>

<span data-ttu-id="9af2c-105">Podczas odczytu z pliku używającego znaków rozszerzonych, trzeba będzie określić kodowanie pliku.</span><span class="sxs-lookup"><span data-stu-id="9af2c-105">If you are reading from a file with extended characters, you will need to specify the file encoding.</span></span>

> [!NOTE]
> <span data-ttu-id="9af2c-106">Aby odczytać plik pojedynczy wiersz tekstu, użyj <xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.OpenTextFileReader%2A> metody `My.Computer.FileSystem` obiektu.</span><span class="sxs-lookup"><span data-stu-id="9af2c-106">To read a file a single line of text at a time, use the <xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.OpenTextFileReader%2A> method of the `My.Computer.FileSystem` object.</span></span> <span data-ttu-id="9af2c-107">`OpenTextFileReader` Metoda<xref:System.IO.StreamReader> zwraca obiekt.</span><span class="sxs-lookup"><span data-stu-id="9af2c-107">The `OpenTextFileReader` method returns a <xref:System.IO.StreamReader> object.</span></span> <span data-ttu-id="9af2c-108">Można użyć <xref:System.IO.StreamReader.ReadLine%2A> metody `StreamReader` obiektu, aby odczytać plik jeden wiersz jednocześnie.</span><span class="sxs-lookup"><span data-stu-id="9af2c-108">You can use the <xref:System.IO.StreamReader.ReadLine%2A> method of the `StreamReader` object to read a file one line at a time.</span></span> <span data-ttu-id="9af2c-109">Można testować pod kątem końca pliku przy użyciu <xref:System.IO.StreamReader.EndOfStream%2A> metody `StreamReader` obiektu.</span><span class="sxs-lookup"><span data-stu-id="9af2c-109">You can test for the end of the file using the <xref:System.IO.StreamReader.EndOfStream%2A> method of the `StreamReader` object.</span></span>

## <a name="to-read-from-a-text-file"></a><span data-ttu-id="9af2c-110">Aby odczytać z pliku tekstowego</span><span class="sxs-lookup"><span data-stu-id="9af2c-110">To read from a text file</span></span>

<span data-ttu-id="9af2c-111">`ReadAllText` Użyj metody `My.Computer.FileSystem` obiektu, aby odczytać zawartość pliku tekstowego w ciągu, dostarczając ścieżkę.</span><span class="sxs-lookup"><span data-stu-id="9af2c-111">Use the `ReadAllText` method of the `My.Computer.FileSystem` object to read the contents of a text file into a string, supplying the path.</span></span> <span data-ttu-id="9af2c-112">Poniższy przykład odczytuje zawartość test.txt jako ciąg i wyświetla go w oknie komunikatu.</span><span class="sxs-lookup"><span data-stu-id="9af2c-112">The following example reads the contents of test.txt into a string and then displays it in a message box.</span></span>

[!code-vb[VbFileIORead#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#2)]

### <a name="to-read-from-a-text-file-that-is-encoded"></a><span data-ttu-id="9af2c-113">Aby odczytać z pliku tekstowego, który jest kodowany</span><span class="sxs-lookup"><span data-stu-id="9af2c-113">To read from a text file that is encoded</span></span>

<span data-ttu-id="9af2c-114">`ReadAllText` Użyj metody `My.Computer.FileSystem` obiektu, aby odczytać zawartość pliku tekstowego w ciągu, podając ścieżkę i typ kodowania pliku.</span><span class="sxs-lookup"><span data-stu-id="9af2c-114">Use the `ReadAllText` method of the `My.Computer.FileSystem` object to read the contents of a text file into a string, supplying the path and file encoding type.</span></span> <span data-ttu-id="9af2c-115">Poniższy przykład odczytuje zawartość pliku z kodowaniem UTF32 test.txt jako ciąg i wyświetla go w oknie komunikatu.</span><span class="sxs-lookup"><span data-stu-id="9af2c-115">The following example reads the contents of the UTF32 file test.txt into a string and then displays it in a message box.</span></span>

[!code-vb[VbFileIORead#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#3)]

## <a name="robust-programming"></a><span data-ttu-id="9af2c-116">Niezawodne programowanie</span><span class="sxs-lookup"><span data-stu-id="9af2c-116">Robust Programming</span></span>

<span data-ttu-id="9af2c-117">Następujące warunki mogą spowodować wyjątek:</span><span class="sxs-lookup"><span data-stu-id="9af2c-117">The following conditions may cause an exception:</span></span>

- <span data-ttu-id="9af2c-118">Ścieżka jest nieprawidłowa z jednego z następujących powodów: jest ciągiem o zerowej długości, zawiera tylko biały znak, zawiera nieprawidłowe znaki lub jest ścieżką urządzenia (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="9af2c-118">The path is not valid for one of the following reasons: it is a zero-length string, it contains only white space, it contains invalid characters, or it is a device path (<xref:System.ArgumentException>).</span></span>

- <span data-ttu-id="9af2c-119">Ścieżka jest nieprawidłowa, ponieważ jest `Nothing` (<xref:System.ArgumentNullException>).</span><span class="sxs-lookup"><span data-stu-id="9af2c-119">The path is not valid because it is `Nothing` (<xref:System.ArgumentNullException>).</span></span>

- <span data-ttu-id="9af2c-120">Plik nie istnieje (<xref:System.IO.FileNotFoundException>).</span><span class="sxs-lookup"><span data-stu-id="9af2c-120">The file does not exist (<xref:System.IO.FileNotFoundException>).</span></span>

- <span data-ttu-id="9af2c-121">Plik jest używany przez inny proces lub wystąpił błąd we/wy (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="9af2c-121">The file is in use by another process or an I/O error occurs (<xref:System.IO.IOException>).</span></span>

- <span data-ttu-id="9af2c-122">Ścieżka przekracza maksymalną długość zdefiniowaną przez system (<xref:System.IO.PathTooLongException>).</span><span class="sxs-lookup"><span data-stu-id="9af2c-122">The path exceeds the system-defined maximum length (<xref:System.IO.PathTooLongException>).</span></span>

- <span data-ttu-id="9af2c-123">Nazwa pliku lub katalogu w ścieżce zawiera dwukropek (:) lub ma nieprawidłowy format (<xref:System.NotSupportedException>).</span><span class="sxs-lookup"><span data-stu-id="9af2c-123">A file or directory name in the path contains a colon (:) or is in an invalid format (<xref:System.NotSupportedException>).</span></span>

- <span data-ttu-id="9af2c-124">Za mało pamięci, aby zapisać ciąg do bufora (<xref:System.OutOfMemoryException>).</span><span class="sxs-lookup"><span data-stu-id="9af2c-124">There is not enough memory to write the string to buffer (<xref:System.OutOfMemoryException>).</span></span>

- <span data-ttu-id="9af2c-125">Użytkownik nie ma wystarczających uprawnień do wyświetlania ścieżki (<xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="9af2c-125">The user lacks necessary permissions to view the path (<xref:System.Security.SecurityException>).</span></span>

<span data-ttu-id="9af2c-126">Nie należy podejmować decyzji dotyczących zawartości pliku na podstawie rozszerzenia nazwy pliku.</span><span class="sxs-lookup"><span data-stu-id="9af2c-126">Do not make decisions about the contents of the file based on the name of the file.</span></span> <span data-ttu-id="9af2c-127">Na przykład plik Form1. vb nie może być plikiem źródłowym Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="9af2c-127">For example, the file Form1.vb may not be a Visual Basic source file.</span></span>

<span data-ttu-id="9af2c-128">Sprawdź wszystkie dane wejściowe, zanim użyjesz danych w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="9af2c-128">Verify all inputs before using the data in your application.</span></span> <span data-ttu-id="9af2c-129">Zawartość pliku może się różnić od oczekiwanej i metody odczytu z pliku nie zadziałają.</span><span class="sxs-lookup"><span data-stu-id="9af2c-129">The contents of the file may not be what is expected, and methods to read from the file may fail.</span></span>

## <a name="see-also"></a><span data-ttu-id="9af2c-130">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9af2c-130">See also</span></span>

- <xref:Microsoft.VisualBasic.FileIO.FileSystem>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.ReadAllText%2A>
- [<span data-ttu-id="9af2c-131">Odczyt z plików</span><span class="sxs-lookup"><span data-stu-id="9af2c-131">Reading from Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/reading-from-files.md)
- [<span data-ttu-id="9af2c-132">Instrukcje: Odczyt z rozdzielanych przecinkami plików tekstowych</span><span class="sxs-lookup"><span data-stu-id="9af2c-132">How to: Read From Comma-Delimited Text Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-comma-delimited-text-files.md)
- [<span data-ttu-id="9af2c-133">Instrukcje: Odczyt z plików tekstowych o stałej szerokości</span><span class="sxs-lookup"><span data-stu-id="9af2c-133">How to: Read From Fixed-width Text Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-fixed-width-text-files.md)
- [<span data-ttu-id="9af2c-134">Instrukcje: Odczyt z plików tekstowych z wieloma formatami</span><span class="sxs-lookup"><span data-stu-id="9af2c-134">How to: Read From Text Files with Multiple Formats</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-text-files-with-multiple-formats.md)
- [<span data-ttu-id="9af2c-135">Rozwiązywanie problemów: Odczytywanie z plików tekstowych i zapisywanie do nich</span><span class="sxs-lookup"><span data-stu-id="9af2c-135">Troubleshooting: Reading from and Writing to Text Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/troubleshooting-reading-from-and-writing-to-text-files.md)
- [<span data-ttu-id="9af2c-136">Przewodnik: Manipulowanie plikami i katalogami w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="9af2c-136">Walkthrough: Manipulating Files and Directories in Visual Basic</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/walkthrough-manipulating-files-and-directories.md)
- [<span data-ttu-id="9af2c-137">Kodowanie pliku</span><span class="sxs-lookup"><span data-stu-id="9af2c-137">File Encodings</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/file-encodings.md)
