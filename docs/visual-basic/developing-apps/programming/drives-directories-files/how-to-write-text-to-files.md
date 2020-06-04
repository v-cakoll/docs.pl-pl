---
title: 'Instrukcje: Zapisywanie tekstu w plikach'
ms.date: 07/20/2015
helpviewer_keywords:
- files [Visual Basic], writing to
- text, writing to files
- writing to files [Visual Basic]
- examples [Visual Basic], text files
ms.assetid: 304956eb-530d-4df7-b48f-9b4d1f2581a0
ms.openlocfilehash: f95a0c4df4a2eab0069a6dab0d4c3fa338d1d8ef
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84411541"
---
# <a name="how-to-write-text-to-files-in-visual-basic"></a><span data-ttu-id="cfefc-102">Porady: zapisywanie tekstu do plików w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="cfefc-102">How to: Write Text to Files in Visual Basic</span></span>

<span data-ttu-id="cfefc-103"><xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A>Metoda może służyć do zapisywania tekstu do plików.</span><span class="sxs-lookup"><span data-stu-id="cfefc-103">The <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A> method can be used to write text to files.</span></span> <span data-ttu-id="cfefc-104">Jeśli określony plik nie istnieje, zostanie utworzony.</span><span class="sxs-lookup"><span data-stu-id="cfefc-104">If the specified file does not exist, it is created.</span></span>  
  
## <a name="procedure"></a><span data-ttu-id="cfefc-105">Procedura</span><span class="sxs-lookup"><span data-stu-id="cfefc-105">Procedure</span></span>  
  
#### <a name="to-write-text-to-a-file"></a><span data-ttu-id="cfefc-106">Aby zapisać tekst do pliku</span><span class="sxs-lookup"><span data-stu-id="cfefc-106">To write text to a file</span></span>  
  
- <span data-ttu-id="cfefc-107">Użyj `WriteAllText` metody, aby zapisać tekst do pliku, określając plik i tekst do zapisania.</span><span class="sxs-lookup"><span data-stu-id="cfefc-107">Use the `WriteAllText` method to write text to a file, specifying the file and text to be written.</span></span> <span data-ttu-id="cfefc-108">Ten przykład zapisuje wiersz `"This is new text."` do pliku o nazwie `test.txt` , dołączając tekst do dowolnego istniejącego tekstu w pliku.</span><span class="sxs-lookup"><span data-stu-id="cfefc-108">This example writes the line `"This is new text."` to the file named `test.txt`, appending the text to any existing text in the file.</span></span>  
  
     [!code-vb[VbFileIOWrite#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOWrite/VB/Class1.vb#3)]  
  
#### <a name="to-write-a-series-of-strings-to-a-file"></a><span data-ttu-id="cfefc-109">Aby napisać serię ciągów do pliku</span><span class="sxs-lookup"><span data-stu-id="cfefc-109">To write a series of strings to a file</span></span>  
  
- <span data-ttu-id="cfefc-110">Pętla w kolekcji ciągów.</span><span class="sxs-lookup"><span data-stu-id="cfefc-110">Loop through the string collection.</span></span> <span data-ttu-id="cfefc-111">Użyj `WriteAllText` metody, aby zapisać tekst do pliku, określając docelowy plik i ciąg, który ma zostać dodany i ustawienie `append` `True` .</span><span class="sxs-lookup"><span data-stu-id="cfefc-111">Use the `WriteAllText` method to write text to a file, specifying the target file and string to be added and setting `append` to `True`.</span></span>  
  
     <span data-ttu-id="cfefc-112">Ten przykład zapisuje nazwy plików w `Documents and Settings` katalogu do `FileList.txt` , wstawiając znak powrotu karetki między nimi w celu zwiększenia czytelności.</span><span class="sxs-lookup"><span data-stu-id="cfefc-112">This example writes the names of the files in the `Documents and Settings` directory to `FileList.txt`, inserting a carriage return between each for better readability.</span></span>  
  
     [!code-vb[VbFileIOWrite#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOWrite/VB/Class1.vb#4)]  
  
## <a name="robust-programming"></a><span data-ttu-id="cfefc-113">Niezawodne programowanie</span><span class="sxs-lookup"><span data-stu-id="cfefc-113">Robust Programming</span></span>  

 <span data-ttu-id="cfefc-114">Następujące warunki mogą spowodować wyjątek:</span><span class="sxs-lookup"><span data-stu-id="cfefc-114">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="cfefc-115">Ścieżka jest nieprawidłowa z jednego z następujących powodów: jest ciągiem o zerowej długości, zawiera tylko biały znak, zawiera nieprawidłowe znaki lub jest ścieżką urządzenia (zaczyna się od \\ \\ . \\ ) (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="cfefc-115">The path is not valid for one of the following reasons: it is a zero-length string, it contains only white space, it contains invalid characters, or it is a device path (starts with \\\\.\\) (<xref:System.ArgumentException>).</span></span>  
  
- <span data-ttu-id="cfefc-116">Ścieżka jest nieprawidłowa, ponieważ jest `Nothing` ( <xref:System.ArgumentNullException> ).</span><span class="sxs-lookup"><span data-stu-id="cfefc-116">The path is not valid because it is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
- <span data-ttu-id="cfefc-117">`File`wskazuje ścieżkę, która nie istnieje ( <xref:System.IO.FileNotFoundException> lub <xref:System.IO.DirectoryNotFoundException> ).</span><span class="sxs-lookup"><span data-stu-id="cfefc-117">`File` points to a path that does not exist (<xref:System.IO.FileNotFoundException> or <xref:System.IO.DirectoryNotFoundException>).</span></span>  
  
- <span data-ttu-id="cfefc-118">Plik jest używany przez inny proces lub wystąpił błąd we/wy ( <xref:System.IO.IOException> ).</span><span class="sxs-lookup"><span data-stu-id="cfefc-118">The file is in use by another process, or an I/O error occurs (<xref:System.IO.IOException>).</span></span>  
  
- <span data-ttu-id="cfefc-119">Ścieżka przekracza maksymalną długość zdefiniowaną przez system ( <xref:System.IO.PathTooLongException> ).</span><span class="sxs-lookup"><span data-stu-id="cfefc-119">The path exceeds the system-defined maximum length (<xref:System.IO.PathTooLongException>).</span></span>  
  
- <span data-ttu-id="cfefc-120">Nazwa pliku lub katalogu w ścieżce zawiera dwukropek (:) lub ma nieprawidłowy format ( <xref:System.NotSupportedException> ).</span><span class="sxs-lookup"><span data-stu-id="cfefc-120">A file or directory name in the path contains a colon (:) or is in an invalid format (<xref:System.NotSupportedException>).</span></span>  
  
- <span data-ttu-id="cfefc-121">Użytkownik nie ma wystarczających uprawnień do wyświetlania ścieżki ( <xref:System.Security.SecurityException> ).</span><span class="sxs-lookup"><span data-stu-id="cfefc-121">The user lacks necessary permissions to view the path (<xref:System.Security.SecurityException>).</span></span>  
  
- <span data-ttu-id="cfefc-122">Dysk jest zapełniony i wywołanie metody `WriteAllText` nie powiodło się ( <xref:System.IO.IOException> ).</span><span class="sxs-lookup"><span data-stu-id="cfefc-122">The disk is full, and the call to `WriteAllText` fails (<xref:System.IO.IOException>).</span></span>  
  
 <span data-ttu-id="cfefc-123">Jeśli używasz w kontekście częściowego zaufania, kod może zgłosić wyjątek z powodu niewystarczających uprawnień.</span><span class="sxs-lookup"><span data-stu-id="cfefc-123">If you are running in a partial-trust context, the code might throw an exception due to insufficient privileges.</span></span> <span data-ttu-id="cfefc-124">Aby uzyskać więcej informacji, zobacz podstawowe informacje o [zabezpieczeniach dostępu kodu](../../../../framework/misc/code-access-security-basics.md).</span><span class="sxs-lookup"><span data-stu-id="cfefc-124">For more information, see [Code Access Security Basics](../../../../framework/misc/code-access-security-basics.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cfefc-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="cfefc-125">See also</span></span>

- <xref:Microsoft.VisualBasic.FileIO.FileSystem>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A>
- [<span data-ttu-id="cfefc-126">Instrukcje: odczyt z plików tekstowych</span><span class="sxs-lookup"><span data-stu-id="cfefc-126">How to: Read from Text Files</span></span>](how-to-read-from-text-files.md)
