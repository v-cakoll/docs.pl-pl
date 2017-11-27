---
title: "Porady: odczyt z plików binarnych w Visual Basic"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- binary files [Visual Basic], reading from
- I/O [Visual Basic], reading from binary files
- ReadAllBytes method [Visual Basic], reading from binary files
- My.Computer.FileSystem object, reading from binary files
ms.assetid: d2b1269e-24b6-42e0-9414-ae708db282d8
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: ea6056f7d33b1137abb19b24246ce6874ff4d008
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-read-from-binary-files-in-visual-basic"></a><span data-ttu-id="9c834-102">Porady: odczyt z plików binarnych w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="9c834-102">How to: Read From Binary Files in Visual Basic</span></span>
<span data-ttu-id="9c834-103">`My.Computer.FileSystem` Zawiera obiekt `ReadAllBytes` metodę odczyt z plików binarnych.</span><span class="sxs-lookup"><span data-stu-id="9c834-103">The `My.Computer.FileSystem` object provides the `ReadAllBytes` method for reading from binary files.</span></span>  
  
### <a name="to-read-from-a-binary-file"></a><span data-ttu-id="9c834-104">Można odczytać z pliku binarnego</span><span class="sxs-lookup"><span data-stu-id="9c834-104">To read from a binary file</span></span>  
  
-   <span data-ttu-id="9c834-105">Użyj `ReadAllBytes` metodę, która zwraca zawartość pliku w postaci tablicy bajtów.</span><span class="sxs-lookup"><span data-stu-id="9c834-105">Use the `ReadAllBytes` method, which returns the contents of a file as a byte array.</span></span> <span data-ttu-id="9c834-106">Ten przykład odczytuje z pliku `C:/Documents and Settings/selfportrait.jpg`.</span><span class="sxs-lookup"><span data-stu-id="9c834-106">This example reads from the file `C:/Documents and Settings/selfportrait.jpg`.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#78](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-from-binary-files_1.vb)]  
  
-   <span data-ttu-id="9c834-107">W przypadku dużych plików binarnych, można użyć <xref:System.IO.FileStream.Read%2A> metody <xref:System.IO.FileStream> obiektu do odczytu z pliku z określoną ilością naraz.</span><span class="sxs-lookup"><span data-stu-id="9c834-107">For large binary files, you can use the <xref:System.IO.FileStream.Read%2A> method of the <xref:System.IO.FileStream> object to read from the file only a specified amount at a time.</span></span> <span data-ttu-id="9c834-108">Następnie można ograniczyć, jaka część pliku jest ładowany do pamięci dla każdej operacji odczytu.</span><span class="sxs-lookup"><span data-stu-id="9c834-108">You can then limit how much of the file is loaded into memory for each read operation.</span></span> <span data-ttu-id="9c834-109">Poniższy przykładowy kod kopiuje plik i umożliwia obiekt wywołujący, aby określić, ile pliku jest do odczytu do pamięci dla operacji odczytu.</span><span class="sxs-lookup"><span data-stu-id="9c834-109">The following code example copies a file and allows the caller to specify how much of the file is read into memory per read operation.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#91](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-from-binary-files_2.vb)]  
  
## <a name="robust-programming"></a><span data-ttu-id="9c834-110">Niezawodne programowanie</span><span class="sxs-lookup"><span data-stu-id="9c834-110">Robust Programming</span></span>  
 <span data-ttu-id="9c834-111">Poniższe warunki mogą spowodować wyjątków:</span><span class="sxs-lookup"><span data-stu-id="9c834-111">The following conditions may cause an exception to be thrown:</span></span>  
  
-   <span data-ttu-id="9c834-112">Ścieżka nie jest prawidłowy dla jednego z następujących powodów: jest to ciąg o zerowej długości, zawiera tylko biały znak, zawiera nieprawidłowe znaki lub jest ścieżką urządzenia (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="9c834-112">The path is not valid for one of the following reasons: it is a zero-length string, it contains only white space, it contains invalid characters, or it is a device path (<xref:System.ArgumentException>).</span></span>  
  
-   <span data-ttu-id="9c834-113">Ścieżka jest nieprawidłowa, ponieważ jest on `Nothing` (<xref:System.ArgumentNullException>).</span><span class="sxs-lookup"><span data-stu-id="9c834-113">The path is not valid because it is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
-   <span data-ttu-id="9c834-114">Plik nie istnieje (<xref:System.IO.FileNotFoundException>).</span><span class="sxs-lookup"><span data-stu-id="9c834-114">The file does not exist (<xref:System.IO.FileNotFoundException>).</span></span>  
  
-   <span data-ttu-id="9c834-115">Plik jest używany przez inny proces lub błąd We/Wy (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="9c834-115">The file is in use by another process, or an I/O error occurs (<xref:System.IO.IOException>).</span></span>  
  
-   <span data-ttu-id="9c834-116">Ścieżka przekracza maksymalną długość zdefiniowana w systemie (<xref:System.IO.PathTooLongException>).</span><span class="sxs-lookup"><span data-stu-id="9c834-116">The path exceeds the system-defined maximum length (<xref:System.IO.PathTooLongException>).</span></span>  
  
-   <span data-ttu-id="9c834-117">Nazwę pliku lub katalogu w ścieżce zawiera dwukropek (:) lub jest w nieprawidłowym formacie (<xref:System.NotSupportedException>).</span><span class="sxs-lookup"><span data-stu-id="9c834-117">A file or directory name in the path contains a colon (:) or is in an invalid format (<xref:System.NotSupportedException>).</span></span>  
  
-   <span data-ttu-id="9c834-118">Nie ma wystarczającej ilości pamięci do zapisania ciągu do buforu (<xref:System.OutOfMemoryException>).</span><span class="sxs-lookup"><span data-stu-id="9c834-118">There is not enough memory to write the string to buffer (<xref:System.OutOfMemoryException>).</span></span>  
  
-   <span data-ttu-id="9c834-119">Użytkownik nie ma wystarczających uprawnień, aby wyświetlić ścieżkę (<xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="9c834-119">The user lacks necessary permissions to view the path (<xref:System.Security.SecurityException>).</span></span>  
  
 <span data-ttu-id="9c834-120">Nie należy podejmować decyzji dotyczących zawartości pliku na podstawie rozszerzenia nazwy pliku.</span><span class="sxs-lookup"><span data-stu-id="9c834-120">Do not make decisions about the contents of the file based on the name of the file.</span></span> <span data-ttu-id="9c834-121">Na przykład plik Form1.vb nie może być plik źródłowy języka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="9c834-121">For example, the file Form1.vb may not be a Visual Basic source file.</span></span>  
  
 <span data-ttu-id="9c834-122">Sprawdź wszystkie dane wejściowe, zanim użyjesz danych w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="9c834-122">Verify all inputs before using the data in your application.</span></span> <span data-ttu-id="9c834-123">Zawartość pliku może się różnić od oczekiwanej i metody odczytu z pliku nie zadziałają.</span><span class="sxs-lookup"><span data-stu-id="9c834-123">The contents of the file may not be what is expected, and methods to read from the file may fail.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9c834-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9c834-124">See Also</span></span>  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.ReadAllBytes%2A>  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllBytes%2A>  
 [<span data-ttu-id="9c834-125">Odczyt z plików</span><span class="sxs-lookup"><span data-stu-id="9c834-125">Reading from Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/reading-from-files.md)  
 [<span data-ttu-id="9c834-126">Porady: Odczyt z plików tekstowych w wielu formatach</span><span class="sxs-lookup"><span data-stu-id="9c834-126">How to: Read From Text Files with Multiple Formats</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-text-files-with-multiple-formats.md)  
 [<span data-ttu-id="9c834-127">Zapisywanie danych i odczytywania ze Schowka</span><span class="sxs-lookup"><span data-stu-id="9c834-127">Storing Data to and Reading from the Clipboard</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/storing-data-to-and-reading-from-the-clipboard.md)
