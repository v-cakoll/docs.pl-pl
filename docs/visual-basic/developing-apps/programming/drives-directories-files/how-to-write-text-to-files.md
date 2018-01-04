---
title: "Porady: zapisywanie tekstu do plików w Visual Basic"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- files [Visual Basic], writing to
- text, writing to files
- writing to files [Visual Basic]
- examples [Visual Basic], text files
ms.assetid: 304956eb-530d-4df7-b48f-9b4d1f2581a0
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 4fbbe0ec007911460dc2bda8c681775da9a6cb91
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-write-text-to-files-in-visual-basic"></a><span data-ttu-id="5ffc0-102">Porady: zapisywanie tekstu do plików w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="5ffc0-102">How to: Write Text to Files in Visual Basic</span></span>
<span data-ttu-id="5ffc0-103"><xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A> Metody umożliwia zapisywanie tekstu do plików.</span><span class="sxs-lookup"><span data-stu-id="5ffc0-103">The <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A> method can be used to write text to files.</span></span> <span data-ttu-id="5ffc0-104">Jeśli określony plik nie istnieje, jest tworzony.</span><span class="sxs-lookup"><span data-stu-id="5ffc0-104">If the specified file does not exist, it is created.</span></span>  
  
## <a name="procedure"></a><span data-ttu-id="5ffc0-105">Procedura</span><span class="sxs-lookup"><span data-stu-id="5ffc0-105">Procedure</span></span>  
  
#### <a name="to-write-text-to-a-file"></a><span data-ttu-id="5ffc0-106">Pisanie do pliku</span><span class="sxs-lookup"><span data-stu-id="5ffc0-106">To write text to a file</span></span>  
  
-   <span data-ttu-id="5ffc0-107">Użyj `WriteAllText` metodę zapisywanie tekstu do pliku, określając plików i tekst, który ma zostać zapisany.</span><span class="sxs-lookup"><span data-stu-id="5ffc0-107">Use the `WriteAllText` method to write text to a file, specifying the file and text to be written.</span></span> <span data-ttu-id="5ffc0-108">W tym przykładzie zapisuje linię `"This is new text."` pliku o nazwie `test.txt`, dodanie go do istniejącego tekstu w pliku.</span><span class="sxs-lookup"><span data-stu-id="5ffc0-108">This example writes the line `"This is new text."` to the file named `test.txt`, appending the text to any existing text in the file.</span></span>  
  
     [!code-vb[VbFileIOWrite#3](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-write-text-to-files_1.vb)]  
  
#### <a name="to-write-a-series-of-strings-to-a-file"></a><span data-ttu-id="5ffc0-109">Do zapisu w pliku serii ciągów</span><span class="sxs-lookup"><span data-stu-id="5ffc0-109">To write a series of strings to a file</span></span>  
  
-   <span data-ttu-id="5ffc0-110">Pętli kolekcji ciągów.</span><span class="sxs-lookup"><span data-stu-id="5ffc0-110">Loop through the string collection.</span></span> <span data-ttu-id="5ffc0-111">Użyj `WriteAllText` metoda próbę zapisania tekstu do pliku, określając pliku docelowego i ciąg do dodania i ustawienie `append` do `True`.</span><span class="sxs-lookup"><span data-stu-id="5ffc0-111">Use the `WriteAllText` method to write text to a file, specifying the target file and string to be added and setting `append` to `True`.</span></span>  
  
     <span data-ttu-id="5ffc0-112">W tym przykładzie zapisuje nazwy plików w `Documents and Settings` do katalogu `FileList.txt`, wstawianie karetki zwracać między nimi w celu zwiększenia czytelności.</span><span class="sxs-lookup"><span data-stu-id="5ffc0-112">This example writes the names of the files in the `Documents and Settings` directory to `FileList.txt`, inserting a carriage return between each for better readability.</span></span>  
  
     [!code-vb[VbFileIOWrite#4](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-write-text-to-files_2.vb)]  
  
## <a name="robust-programming"></a><span data-ttu-id="5ffc0-113">Niezawodne programowanie</span><span class="sxs-lookup"><span data-stu-id="5ffc0-113">Robust Programming</span></span>  
 <span data-ttu-id="5ffc0-114">Następujące warunki mogą spowodować wyjątek:</span><span class="sxs-lookup"><span data-stu-id="5ffc0-114">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="5ffc0-115">Ścieżka nie jest prawidłowy dla jednego z następujących powodów: jest to ciąg o zerowej długości, zawiera tylko biały znak, zawiera nieprawidłowe znaki lub jest ścieżką urządzenia (rozpoczyna się od \\ \\.\\) (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="5ffc0-115">The path is not valid for one of the following reasons: it is a zero-length string, it contains only white space, it contains invalid characters, or it is a device path (starts with \\\\.\\) (<xref:System.ArgumentException>).</span></span>  
  
-   <span data-ttu-id="5ffc0-116">Ścieżka jest nieprawidłowa, ponieważ jest on `Nothing` (<xref:System.ArgumentNullException>).</span><span class="sxs-lookup"><span data-stu-id="5ffc0-116">The path is not valid because it is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
-   <span data-ttu-id="5ffc0-117">`File`wskazuje na ścieżkę, która nie istnieje (<xref:System.IO.FileNotFoundException> lub <xref:System.IO.DirectoryNotFoundException>).</span><span class="sxs-lookup"><span data-stu-id="5ffc0-117">`File` points to a path that does not exist (<xref:System.IO.FileNotFoundException> or <xref:System.IO.DirectoryNotFoundException>).</span></span>  
  
-   <span data-ttu-id="5ffc0-118">Plik jest używany przez inny proces lub błąd We/Wy (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="5ffc0-118">The file is in use by another process, or an I/O error occurs (<xref:System.IO.IOException>).</span></span>  
  
-   <span data-ttu-id="5ffc0-119">Ścieżka przekracza maksymalną długość zdefiniowana w systemie (<xref:System.IO.PathTooLongException>).</span><span class="sxs-lookup"><span data-stu-id="5ffc0-119">The path exceeds the system-defined maximum length (<xref:System.IO.PathTooLongException>).</span></span>  
  
-   <span data-ttu-id="5ffc0-120">Nazwę pliku lub katalogu w ścieżce zawiera dwukropek (:) lub jest w nieprawidłowym formacie (<xref:System.NotSupportedException>).</span><span class="sxs-lookup"><span data-stu-id="5ffc0-120">A file or directory name in the path contains a colon (:) or is in an invalid format (<xref:System.NotSupportedException>).</span></span>  
  
-   <span data-ttu-id="5ffc0-121">Użytkownik nie ma wystarczających uprawnień, aby wyświetlić ścieżkę (<xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="5ffc0-121">The user lacks necessary permissions to view the path (<xref:System.Security.SecurityException>).</span></span>  
  
-   <span data-ttu-id="5ffc0-122">Dysk jest pełny i wywołanie `WriteAllText` nie powiedzie się (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="5ffc0-122">The disk is full, and the call to `WriteAllText` fails (<xref:System.IO.IOException>).</span></span>  
  
 <span data-ttu-id="5ffc0-123">Jeśli używasz w kontekście częściowego zaufania, kod może zgłosić wyjątek, ze względu na niewystarczające uprawnienia.</span><span class="sxs-lookup"><span data-stu-id="5ffc0-123">If you are running in a partial-trust context, the code might throw an exception due to insufficient privileges.</span></span> <span data-ttu-id="5ffc0-124">Aby uzyskać więcej informacji, zobacz [podstawy zabezpieczeń dostępu kodu](../../../../framework/misc/code-access-security-basics.md).</span><span class="sxs-lookup"><span data-stu-id="5ffc0-124">For more information, see [Code Access Security Basics](../../../../framework/misc/code-access-security-basics.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5ffc0-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5ffc0-125">See Also</span></span>  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem>  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A>  
 [<span data-ttu-id="5ffc0-126">Porady: Odczyt z plików tekstowych</span><span class="sxs-lookup"><span data-stu-id="5ffc0-126">How to: Read from Text Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-text-files.md)
