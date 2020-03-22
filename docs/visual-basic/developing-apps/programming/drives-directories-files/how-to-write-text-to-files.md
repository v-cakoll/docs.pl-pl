---
title: 'Porady: zapisywanie tekstu do plików'
ms.date: 07/20/2015
helpviewer_keywords:
- files [Visual Basic], writing to
- text, writing to files
- writing to files [Visual Basic]
- examples [Visual Basic], text files
ms.assetid: 304956eb-530d-4df7-b48f-9b4d1f2581a0
ms.openlocfilehash: ce1ee59ba71af6bb13e05a5bce37a2f7eee37712
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "74334472"
---
# <a name="how-to-write-text-to-files-in-visual-basic"></a><span data-ttu-id="5819c-102">Porady: zapisywanie tekstu do plików w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="5819c-102">How to: Write Text to Files in Visual Basic</span></span>

<span data-ttu-id="5819c-103">Metoda <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A> może służyć do pisania tekstu do plików.</span><span class="sxs-lookup"><span data-stu-id="5819c-103">The <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A> method can be used to write text to files.</span></span> <span data-ttu-id="5819c-104">Jeśli określony plik nie istnieje, jest tworzony.</span><span class="sxs-lookup"><span data-stu-id="5819c-104">If the specified file does not exist, it is created.</span></span>  
  
## <a name="procedure"></a><span data-ttu-id="5819c-105">Procedura</span><span class="sxs-lookup"><span data-stu-id="5819c-105">Procedure</span></span>  
  
#### <a name="to-write-text-to-a-file"></a><span data-ttu-id="5819c-106">Aby napisać tekst do pliku</span><span class="sxs-lookup"><span data-stu-id="5819c-106">To write text to a file</span></span>  
  
- <span data-ttu-id="5819c-107">Użyj `WriteAllText` metody do pisania tekstu do pliku, określając plik i tekst do zapisania.</span><span class="sxs-lookup"><span data-stu-id="5819c-107">Use the `WriteAllText` method to write text to a file, specifying the file and text to be written.</span></span> <span data-ttu-id="5819c-108">W tym przykładzie `"This is new text."` zapisuje `test.txt`wiersz do pliku o nazwie , dołączając tekst do dowolnego istniejącego tekstu w pliku.</span><span class="sxs-lookup"><span data-stu-id="5819c-108">This example writes the line `"This is new text."` to the file named `test.txt`, appending the text to any existing text in the file.</span></span>  
  
     [!code-vb[VbFileIOWrite#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOWrite/VB/Class1.vb#3)]  
  
#### <a name="to-write-a-series-of-strings-to-a-file"></a><span data-ttu-id="5819c-109">Aby napisać serię ciągów do pliku</span><span class="sxs-lookup"><span data-stu-id="5819c-109">To write a series of strings to a file</span></span>  
  
- <span data-ttu-id="5819c-110">Pętla za pośrednictwem kolekcji ciągów.</span><span class="sxs-lookup"><span data-stu-id="5819c-110">Loop through the string collection.</span></span> <span data-ttu-id="5819c-111">Użyj `WriteAllText` metody do pisania tekstu do pliku, określając plik docelowy `append` i `True`ciąg do dodania i ustawienie .</span><span class="sxs-lookup"><span data-stu-id="5819c-111">Use the `WriteAllText` method to write text to a file, specifying the target file and string to be added and setting `append` to `True`.</span></span>  
  
     <span data-ttu-id="5819c-112">W tym przykładzie zapisuje nazwy `Documents and Settings` plików `FileList.txt`w katalogu do , wstawiając powrót karetki między każdym dla lepszej czytelności.</span><span class="sxs-lookup"><span data-stu-id="5819c-112">This example writes the names of the files in the `Documents and Settings` directory to `FileList.txt`, inserting a carriage return between each for better readability.</span></span>  
  
     [!code-vb[VbFileIOWrite#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOWrite/VB/Class1.vb#4)]  
  
## <a name="robust-programming"></a><span data-ttu-id="5819c-113">Niezawodne programowanie</span><span class="sxs-lookup"><span data-stu-id="5819c-113">Robust Programming</span></span>  

 <span data-ttu-id="5819c-114">Następujące warunki mogą spowodować wyjątek:</span><span class="sxs-lookup"><span data-stu-id="5819c-114">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="5819c-115">Ścieżka nie jest prawidłowa z jednego z następujących powodów: jest ciągiem o zerowej długości, zawiera tylko biały znak, \\ \\\\zawiera nieprawidłowe znaki lub jest ścieżką urządzenia (zaczyna się od . ) (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="5819c-115">The path is not valid for one of the following reasons: it is a zero-length string, it contains only white space, it contains invalid characters, or it is a device path (starts with \\\\.\\) (<xref:System.ArgumentException>).</span></span>  
  
- <span data-ttu-id="5819c-116">Ścieżka jest nieprawidłowa, `Nothing` ponieważ<xref:System.ArgumentNullException>jest ( ).</span><span class="sxs-lookup"><span data-stu-id="5819c-116">The path is not valid because it is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
- <span data-ttu-id="5819c-117">`File`wskazuje ścieżkę, która nie<xref:System.IO.FileNotFoundException> <xref:System.IO.DirectoryNotFoundException>istnieje ( lub ).</span><span class="sxs-lookup"><span data-stu-id="5819c-117">`File` points to a path that does not exist (<xref:System.IO.FileNotFoundException> or <xref:System.IO.DirectoryNotFoundException>).</span></span>  
  
- <span data-ttu-id="5819c-118">Plik jest używany przez inny proces lub występuje błąd<xref:System.IO.IOException>we/wy ( ).</span><span class="sxs-lookup"><span data-stu-id="5819c-118">The file is in use by another process, or an I/O error occurs (<xref:System.IO.IOException>).</span></span>  
  
- <span data-ttu-id="5819c-119">Ścieżka przekracza zdefiniowaną przez system<xref:System.IO.PathTooLongException>maksymalną długość ( ).</span><span class="sxs-lookup"><span data-stu-id="5819c-119">The path exceeds the system-defined maximum length (<xref:System.IO.PathTooLongException>).</span></span>  
  
- <span data-ttu-id="5819c-120">Nazwa pliku lub katalogu w ścieżce zawiera dwukropek (:) lub jest w nieprawidłowym formacie (<xref:System.NotSupportedException>).</span><span class="sxs-lookup"><span data-stu-id="5819c-120">A file or directory name in the path contains a colon (:) or is in an invalid format (<xref:System.NotSupportedException>).</span></span>  
  
- <span data-ttu-id="5819c-121">Użytkownik nie ma niezbędnych uprawnień do<xref:System.Security.SecurityException>wyświetlania ścieżki ( ).</span><span class="sxs-lookup"><span data-stu-id="5819c-121">The user lacks necessary permissions to view the path (<xref:System.Security.SecurityException>).</span></span>  
  
- <span data-ttu-id="5819c-122">Dysk jest zapełniony, `WriteAllText` a<xref:System.IO.IOException>wywołanie nie powiedzie się ( ).</span><span class="sxs-lookup"><span data-stu-id="5819c-122">The disk is full, and the call to `WriteAllText` fails (<xref:System.IO.IOException>).</span></span>  
  
 <span data-ttu-id="5819c-123">Jeśli używasz w kontekście częściowego zaufania, kod może zgłosić wyjątek z powodu niewystarczających uprawnień.</span><span class="sxs-lookup"><span data-stu-id="5819c-123">If you are running in a partial-trust context, the code might throw an exception due to insufficient privileges.</span></span> <span data-ttu-id="5819c-124">Aby uzyskać więcej informacji, zobacz [Podstawy zabezpieczeń dostępu do kodu](../../../../framework/misc/code-access-security-basics.md).</span><span class="sxs-lookup"><span data-stu-id="5819c-124">For more information, see [Code Access Security Basics](../../../../framework/misc/code-access-security-basics.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5819c-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5819c-125">See also</span></span>

- <xref:Microsoft.VisualBasic.FileIO.FileSystem>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A>
- [<span data-ttu-id="5819c-126">Jak: Odczyt z plików tekstowych</span><span class="sxs-lookup"><span data-stu-id="5819c-126">How to: Read from Text Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-text-files.md)
