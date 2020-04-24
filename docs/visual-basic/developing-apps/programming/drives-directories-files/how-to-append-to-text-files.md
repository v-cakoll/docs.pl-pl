---
title: 'Porady: łączenie się plikami tekstowymi'
ms.date: 07/20/2015
helpviewer_keywords:
- I/O [Visual Basic], appending to files
- I/O [Visual Basic], My.Computer.FileSystem.WriteAllText method
- I/O [Visual Basic], WriteAllText method
ms.assetid: bbbd7fb5-f169-41a9-b53f-520ea9613913
ms.openlocfilehash: 97bcb5c511452e418df010f12d4b63f04251d021
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "74348869"
---
# <a name="how-to-append-to-text-files-in-visual-basic"></a><span data-ttu-id="bc4ac-102">Porady: łączenie się plikami tekstowymi w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="bc4ac-102">How to: Append to Text Files in Visual Basic</span></span>

<span data-ttu-id="bc4ac-103"><xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A> Metoda może służyć do dołączania do pliku tekstowego przez określenie, że `append` parametr jest ustawiony na `True`.</span><span class="sxs-lookup"><span data-stu-id="bc4ac-103">The <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A> method can be used to append to a text file by specifying that the `append` parameter is set to `True`.</span></span>  
  
### <a name="to-append-to-a-text-file"></a><span data-ttu-id="bc4ac-104">Aby dołączyć do pliku tekstowego</span><span class="sxs-lookup"><span data-stu-id="bc4ac-104">To append to a text file</span></span>  
  
- <span data-ttu-id="bc4ac-105">Użyj `WriteAllText` metody, określając docelowy plik i ciąg do dołączenia, a następnie ustaw `append` parametr na. `True`</span><span class="sxs-lookup"><span data-stu-id="bc4ac-105">Use the `WriteAllText` method, specifying the target file and string to be appended and setting the `append` parameter to `True`.</span></span>  
  
     <span data-ttu-id="bc4ac-106">Ten przykład zapisuje ciąg `"This is a test string."` do pliku o nazwie. `Testfile.txt`</span><span class="sxs-lookup"><span data-stu-id="bc4ac-106">This example writes the string `"This is a test string."` to the file named `Testfile.txt`.</span></span>  
  
     [!code-vb[VbFileIOWrite#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOWrite/VB/Class1.vb#6)]  
  
## <a name="robust-programming"></a><span data-ttu-id="bc4ac-107">Niezawodne programowanie</span><span class="sxs-lookup"><span data-stu-id="bc4ac-107">Robust Programming</span></span>  

 <span data-ttu-id="bc4ac-108">Następujące warunki mogą spowodować wyjątek:</span><span class="sxs-lookup"><span data-stu-id="bc4ac-108">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="bc4ac-109">Ścieżka jest nieprawidłowa z jednego z następujących powodów: jest ciągiem o zerowej długości, zawiera tylko biały znak, zawiera nieprawidłowe znaki lub jest ścieżką urządzenia (zaczyna się od \\ \\.\\) (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="bc4ac-109">The path is not valid for one of the following reasons: it is a zero-length string, it contains only white space, it contains invalid characters, or it is a device path (starts with \\\\.\\) (<xref:System.ArgumentException>).</span></span>  
  
- <span data-ttu-id="bc4ac-110">Ścieżka jest nieprawidłowa, ponieważ jest `Nothing` (<xref:System.ArgumentNullException>).</span><span class="sxs-lookup"><span data-stu-id="bc4ac-110">The path is not valid because it is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
- <span data-ttu-id="bc4ac-111">`File`wskazuje ścieżkę, która nie istnieje (<xref:System.IO.FileNotFoundException> lub <xref:System.IO.DirectoryNotFoundException>).</span><span class="sxs-lookup"><span data-stu-id="bc4ac-111">`File` points to a path that does not exist (<xref:System.IO.FileNotFoundException> or <xref:System.IO.DirectoryNotFoundException>).</span></span>  
  
- <span data-ttu-id="bc4ac-112">Plik jest używany przez inny proces lub wystąpił błąd we/wy (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="bc4ac-112">The file is in use by another process, or an I/O error occurs (<xref:System.IO.IOException>).</span></span>  
  
- <span data-ttu-id="bc4ac-113">Ścieżka przekracza maksymalną długość zdefiniowaną przez system (<xref:System.IO.PathTooLongException>).</span><span class="sxs-lookup"><span data-stu-id="bc4ac-113">The path exceeds the system-defined maximum length (<xref:System.IO.PathTooLongException>).</span></span>  
  
- <span data-ttu-id="bc4ac-114">Nazwa pliku lub katalogu w ścieżce zawiera dwukropek (:) lub ma nieprawidłowy format (<xref:System.NotSupportedException>).</span><span class="sxs-lookup"><span data-stu-id="bc4ac-114">A file or directory name in the path contains a colon (:) or is in an invalid format (<xref:System.NotSupportedException>).</span></span>  
  
- <span data-ttu-id="bc4ac-115">Użytkownik nie ma wystarczających uprawnień do wyświetlania ścieżki (<xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="bc4ac-115">The user lacks necessary permissions to view the path (<xref:System.Security.SecurityException>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bc4ac-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="bc4ac-116">See also</span></span>

- <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem>
- [<span data-ttu-id="bc4ac-117">Zapisywanie w plikach</span><span class="sxs-lookup"><span data-stu-id="bc4ac-117">Writing to Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/writing-to-files.md)
