---
title: 'Instrukcje: Łączenie się plikami tekstowymi w Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- I/O [Visual Basic], appending to files
- I/O [Visual Basic], My.Computer.FileSystem.WriteAllText method
- I/O [Visual Basic], WriteAllText method
ms.assetid: bbbd7fb5-f169-41a9-b53f-520ea9613913
ms.openlocfilehash: d7518493cca62018ccda9659e977333184888ea7
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2019
ms.locfileid: "56968689"
---
# <a name="how-to-append-to-text-files-in-visual-basic"></a><span data-ttu-id="31362-102">Instrukcje: Łączenie się plikami tekstowymi w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="31362-102">How to: Append to Text Files in Visual Basic</span></span>
<span data-ttu-id="31362-103"><xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A> Metoda może służyć do dołączenia do pliku tekstowego, określając, który `append` parametr ma wartość `True`.</span><span class="sxs-lookup"><span data-stu-id="31362-103">The <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A> method can be used to append to a text file by specifying that the `append` parameter is set to `True`.</span></span>  
  
### <a name="to-append-to-a-text-file"></a><span data-ttu-id="31362-104">Aby dołączyć do pliku tekstowego</span><span class="sxs-lookup"><span data-stu-id="31362-104">To append to a text file</span></span>  
  
-   <span data-ttu-id="31362-105">Użyj `WriteAllText` metody, określając pliku docelowego i ciąg do dołączenia i ustawienie `append` parametr `True`.</span><span class="sxs-lookup"><span data-stu-id="31362-105">Use the `WriteAllText` method, specifying the target file and string to be appended and setting the `append` parameter to `True`.</span></span>  
  
     <span data-ttu-id="31362-106">Ten przykład Przepisuje ciąg `"This is a test string."` pliku o nazwie `Testfile.txt`.</span><span class="sxs-lookup"><span data-stu-id="31362-106">This example writes the string `"This is a test string."` to the file named `Testfile.txt`.</span></span>  
  
     [!code-vb[VbFileIOWrite#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOWrite/VB/Class1.vb#6)]  
  
## <a name="robust-programming"></a><span data-ttu-id="31362-107">Niezawodne programowanie</span><span class="sxs-lookup"><span data-stu-id="31362-107">Robust Programming</span></span>  
 <span data-ttu-id="31362-108">Następujące warunki mogą spowodować wyjątek:</span><span class="sxs-lookup"><span data-stu-id="31362-108">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="31362-109">Ścieżka nie jest prawidłowa dla jednego z następujących przyczyn: jest to ciąg o zerowej długości, zawiera tylko znak odstępu, zawiera nieprawidłowe znaki lub jest ścieżką do urządzenia (rozpoczyna się od \\ \\.\\) (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="31362-109">The path is not valid for one of the following reasons: it is a zero-length string, it contains only white space, it contains invalid characters, or it is a device path (starts with \\\\.\\) (<xref:System.ArgumentException>).</span></span>  
  
-   <span data-ttu-id="31362-110">Ścieżka jest nieprawidłowa, ponieważ jest on `Nothing` (<xref:System.ArgumentNullException>).</span><span class="sxs-lookup"><span data-stu-id="31362-110">The path is not valid because it is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
-   <span data-ttu-id="31362-111">`File` Wskazuje ścieżkę, która nie istnieje (<xref:System.IO.FileNotFoundException> lub <xref:System.IO.DirectoryNotFoundException>).</span><span class="sxs-lookup"><span data-stu-id="31362-111">`File` points to a path that does not exist (<xref:System.IO.FileNotFoundException> or <xref:System.IO.DirectoryNotFoundException>).</span></span>  
  
-   <span data-ttu-id="31362-112">Plik jest używany przez inny proces lub wystąpi błąd We/Wy (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="31362-112">The file is in use by another process, or an I/O error occurs (<xref:System.IO.IOException>).</span></span>  
  
-   <span data-ttu-id="31362-113">Ścieżka przekracza maksymalną długość zdefiniowaną przez system (<xref:System.IO.PathTooLongException>).</span><span class="sxs-lookup"><span data-stu-id="31362-113">The path exceeds the system-defined maximum length (<xref:System.IO.PathTooLongException>).</span></span>  
  
-   <span data-ttu-id="31362-114">Nazwa pliku lub katalogu w ścieżce zawiera dwukropek (:) lub jest w nieprawidłowym formacie (<xref:System.NotSupportedException>).</span><span class="sxs-lookup"><span data-stu-id="31362-114">A file or directory name in the path contains a colon (:) or is in an invalid format (<xref:System.NotSupportedException>).</span></span>  
  
-   <span data-ttu-id="31362-115">Użytkownik nie ma wystarczających uprawnień do wyświetlania ścieżki (<xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="31362-115">The user lacks necessary permissions to view the path (<xref:System.Security.SecurityException>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="31362-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="31362-116">See also</span></span>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem>
- [<span data-ttu-id="31362-117">Zapisywanie w plikach</span><span class="sxs-lookup"><span data-stu-id="31362-117">Writing to Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/writing-to-files.md)
