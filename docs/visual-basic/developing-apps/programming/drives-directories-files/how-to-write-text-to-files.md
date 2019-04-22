---
title: 'Instrukcje: Zapisywanie tekstu do plików w języku Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- files [Visual Basic], writing to
- text, writing to files
- writing to files [Visual Basic]
- examples [Visual Basic], text files
ms.assetid: 304956eb-530d-4df7-b48f-9b4d1f2581a0
ms.openlocfilehash: f4d6c3ef5ba6d8aa286e1ae2bd8a944aacdad096
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "58828228"
---
# <a name="how-to-write-text-to-files-in-visual-basic"></a><span data-ttu-id="6e117-102">Instrukcje: Zapisywanie tekstu do plików w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="6e117-102">How to: Write Text to Files in Visual Basic</span></span>
<span data-ttu-id="6e117-103"><xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A> Metoda może służyć do zapisywanie tekstu do plików.</span><span class="sxs-lookup"><span data-stu-id="6e117-103">The <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A> method can be used to write text to files.</span></span> <span data-ttu-id="6e117-104">Jeśli określony plik nie istnieje, zostanie utworzony.</span><span class="sxs-lookup"><span data-stu-id="6e117-104">If the specified file does not exist, it is created.</span></span>  
  
## <a name="procedure"></a><span data-ttu-id="6e117-105">Procedura</span><span class="sxs-lookup"><span data-stu-id="6e117-105">Procedure</span></span>  
  
#### <a name="to-write-text-to-a-file"></a><span data-ttu-id="6e117-106">Aby wpisać tekst w pliku</span><span class="sxs-lookup"><span data-stu-id="6e117-106">To write text to a file</span></span>  
  
-   <span data-ttu-id="6e117-107">Użyj `WriteAllText` metodę, aby wpisać tekst do pliku, określając pliku i tekst do wyświetlenia.</span><span class="sxs-lookup"><span data-stu-id="6e117-107">Use the `WriteAllText` method to write text to a file, specifying the file and text to be written.</span></span> <span data-ttu-id="6e117-108">Ten przykład zapisuje linię `"This is new text."` pliku o nazwie `test.txt`, dodając tekst na wszelki istniejący tekst w pliku.</span><span class="sxs-lookup"><span data-stu-id="6e117-108">This example writes the line `"This is new text."` to the file named `test.txt`, appending the text to any existing text in the file.</span></span>  
  
     [!code-vb[VbFileIOWrite#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOWrite/VB/Class1.vb#3)]  
  
#### <a name="to-write-a-series-of-strings-to-a-file"></a><span data-ttu-id="6e117-109">Do zapisu serii ciągów w pliku</span><span class="sxs-lookup"><span data-stu-id="6e117-109">To write a series of strings to a file</span></span>  
  
-   <span data-ttu-id="6e117-110">W pętli poprzez kolekcji ciągów.</span><span class="sxs-lookup"><span data-stu-id="6e117-110">Loop through the string collection.</span></span> <span data-ttu-id="6e117-111">Użyj `WriteAllText` metodę, aby wpisać tekst w pliku, określając pliku docelowego i parametry, które mają zostać dodane i ustawienie `append` do `True`.</span><span class="sxs-lookup"><span data-stu-id="6e117-111">Use the `WriteAllText` method to write text to a file, specifying the target file and string to be added and setting `append` to `True`.</span></span>  
  
     <span data-ttu-id="6e117-112">Ten przykład Przepisuje nazwy plików w `Documents and Settings` do katalogu `FileList.txt`, wstawianie karetki zwracają między nimi w celu zwiększenia czytelności.</span><span class="sxs-lookup"><span data-stu-id="6e117-112">This example writes the names of the files in the `Documents and Settings` directory to `FileList.txt`, inserting a carriage return between each for better readability.</span></span>  
  
     [!code-vb[VbFileIOWrite#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOWrite/VB/Class1.vb#4)]  
  
## <a name="robust-programming"></a><span data-ttu-id="6e117-113">Niezawodne programowanie</span><span class="sxs-lookup"><span data-stu-id="6e117-113">Robust Programming</span></span>  
 <span data-ttu-id="6e117-114">Następujące warunki mogą spowodować wyjątek:</span><span class="sxs-lookup"><span data-stu-id="6e117-114">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="6e117-115">Ścieżka nie jest prawidłowa dla jednego z następujących przyczyn: jest to ciąg o zerowej długości, zawiera tylko znak odstępu, zawiera nieprawidłowe znaki lub jest ścieżką do urządzenia (rozpoczyna się od \\ \\.\\) (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="6e117-115">The path is not valid for one of the following reasons: it is a zero-length string, it contains only white space, it contains invalid characters, or it is a device path (starts with \\\\.\\) (<xref:System.ArgumentException>).</span></span>  
  
-   <span data-ttu-id="6e117-116">Ścieżka jest nieprawidłowa, ponieważ jest on `Nothing` (<xref:System.ArgumentNullException>).</span><span class="sxs-lookup"><span data-stu-id="6e117-116">The path is not valid because it is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
-   <span data-ttu-id="6e117-117">`File` Wskazuje ścieżkę, która nie istnieje (<xref:System.IO.FileNotFoundException> lub <xref:System.IO.DirectoryNotFoundException>).</span><span class="sxs-lookup"><span data-stu-id="6e117-117">`File` points to a path that does not exist (<xref:System.IO.FileNotFoundException> or <xref:System.IO.DirectoryNotFoundException>).</span></span>  
  
-   <span data-ttu-id="6e117-118">Plik jest używany przez inny proces lub wystąpi błąd We/Wy (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="6e117-118">The file is in use by another process, or an I/O error occurs (<xref:System.IO.IOException>).</span></span>  
  
-   <span data-ttu-id="6e117-119">Ścieżka przekracza maksymalną długość zdefiniowaną przez system (<xref:System.IO.PathTooLongException>).</span><span class="sxs-lookup"><span data-stu-id="6e117-119">The path exceeds the system-defined maximum length (<xref:System.IO.PathTooLongException>).</span></span>  
  
-   <span data-ttu-id="6e117-120">Nazwa pliku lub katalogu w ścieżce zawiera dwukropek (:) lub jest w nieprawidłowym formacie (<xref:System.NotSupportedException>).</span><span class="sxs-lookup"><span data-stu-id="6e117-120">A file or directory name in the path contains a colon (:) or is in an invalid format (<xref:System.NotSupportedException>).</span></span>  
  
-   <span data-ttu-id="6e117-121">Użytkownik nie ma wystarczających uprawnień do wyświetlania ścieżki (<xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="6e117-121">The user lacks necessary permissions to view the path (<xref:System.Security.SecurityException>).</span></span>  
  
-   <span data-ttu-id="6e117-122">Dysk jest pełny i wywołanie `WriteAllText` zakończy się niepowodzeniem (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="6e117-122">The disk is full, and the call to `WriteAllText` fails (<xref:System.IO.IOException>).</span></span>  
  
 <span data-ttu-id="6e117-123">Jeśli używasz w kontekście częściowego zaufania, kod może zgłosić wyjątek ze względu na niewystarczające uprawnienia.</span><span class="sxs-lookup"><span data-stu-id="6e117-123">If you are running in a partial-trust context, the code might throw an exception due to insufficient privileges.</span></span> <span data-ttu-id="6e117-124">Aby uzyskać więcej informacji, zobacz [podstawy zabezpieczeń dostępu kodu](../../../../framework/misc/code-access-security-basics.md).</span><span class="sxs-lookup"><span data-stu-id="6e117-124">For more information, see [Code Access Security Basics](../../../../framework/misc/code-access-security-basics.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6e117-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6e117-125">See also</span></span>

- <xref:Microsoft.VisualBasic.FileIO.FileSystem>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A>
- [<span data-ttu-id="6e117-126">Instrukcje: Odczyt z plików tekstowych</span><span class="sxs-lookup"><span data-stu-id="6e117-126">How to: Read from Text Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-text-files.md)
