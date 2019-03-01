---
title: 'Instrukcje: Zapis w plikach binarnych w Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- files [Visual Basic], binary access
- WriteAllBytes method [Visual Basic]
- binary files [Visual Basic], writing in Visual Basic
ms.assetid: 59fae125-de5b-4c96-883c-209f4a55112c
ms.openlocfilehash: 9e83029b7b5fd635ff08e608760b6c64c7945da0
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2019
ms.locfileid: "56965933"
---
# <a name="how-to-write-to-binary-files-in-visual-basic"></a><span data-ttu-id="05bcf-102">Instrukcje: Zapis w plikach binarnych w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="05bcf-102">How to: Write to Binary Files in Visual Basic</span></span>
<span data-ttu-id="05bcf-103"><xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllBytes%2A> Metoda zapisuje dane w pliku binarnym.</span><span class="sxs-lookup"><span data-stu-id="05bcf-103">The <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllBytes%2A> method writes data to a binary file.</span></span> <span data-ttu-id="05bcf-104">Jeśli `append` parametr jest `True`, dołączy je do pliku; w przeciwnym razie zostanie zastąpiony dane w pliku.</span><span class="sxs-lookup"><span data-stu-id="05bcf-104">If the `append` parameter is `True`, it will append the data to the file; otherwise data in the file is overwritten.</span></span>  
  
 <span data-ttu-id="05bcf-105">Jeśli określona ścieżka, z wyjątkiem nazwy pliku nie jest prawidłowy, <xref:System.IO.DirectoryNotFoundException> zostanie zgłoszony wyjątek.</span><span class="sxs-lookup"><span data-stu-id="05bcf-105">If the specified path excluding the file name is not valid, a <xref:System.IO.DirectoryNotFoundException> exception will be thrown.</span></span> <span data-ttu-id="05bcf-106">Jeśli ścieżka jest prawidłowa, ale plik nie istnieje, zostanie utworzony plik.</span><span class="sxs-lookup"><span data-stu-id="05bcf-106">If the path is valid but the file does not exist, the file will be created.</span></span>  
  
### <a name="to-write-to-a-binary-file"></a><span data-ttu-id="05bcf-107">Można zapisać do pliku binarnego</span><span class="sxs-lookup"><span data-stu-id="05bcf-107">To write to a binary file</span></span>  
  
-   <span data-ttu-id="05bcf-108">Użyj `WriteAllBytes` metody, podając ścieżkę i nazwę i bajtów do zapisania.</span><span class="sxs-lookup"><span data-stu-id="05bcf-108">Use the `WriteAllBytes` method, supplying the file path and name and the bytes to be written.</span></span> <span data-ttu-id="05bcf-109">W tym przykładzie dołącza tablicy danych `CustomerData` pliku o nazwie `CollectedData.dat`.</span><span class="sxs-lookup"><span data-stu-id="05bcf-109">This example appends the data array `CustomerData` to the file named `CollectedData.dat`.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#27)]  
  
## <a name="robust-programming"></a><span data-ttu-id="05bcf-110">Niezawodne programowanie</span><span class="sxs-lookup"><span data-stu-id="05bcf-110">Robust Programming</span></span>  
 <span data-ttu-id="05bcf-111">Następujące warunki mogą utworzyć wyjątek:</span><span class="sxs-lookup"><span data-stu-id="05bcf-111">The following conditions may create an exception:</span></span>  
  
-   <span data-ttu-id="05bcf-112">Ścieżka nie jest prawidłowa dla jednego z następujących przyczyn: jest to ciąg o zerowej długości; zawiera tylko znak odstępu; lub zawiera nieprawidłowe znaki.</span><span class="sxs-lookup"><span data-stu-id="05bcf-112">The path is not valid for one of the following reasons: it is a zero-length string; it contains only white space; or it contains invalid characters.</span></span> <span data-ttu-id="05bcf-113">(<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="05bcf-113">(<xref:System.ArgumentException>).</span></span>  
  
-   <span data-ttu-id="05bcf-114">Ścieżka jest nieprawidłowa, ponieważ jest on `Nothing` (<xref:System.ArgumentNullException>).</span><span class="sxs-lookup"><span data-stu-id="05bcf-114">The path is not valid because it is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
-   <span data-ttu-id="05bcf-115">`File` Wskazuje ścieżkę, która nie istnieje (<xref:System.IO.FileNotFoundException> lub <xref:System.IO.DirectoryNotFoundException>).</span><span class="sxs-lookup"><span data-stu-id="05bcf-115">`File` points to a path that does not exist (<xref:System.IO.FileNotFoundException> or <xref:System.IO.DirectoryNotFoundException>).</span></span>  
  
-   <span data-ttu-id="05bcf-116">Plik jest używany przez inny proces lub wystąpi błąd We/Wy (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="05bcf-116">The file is in use by another process, or an I/O error occurs (<xref:System.IO.IOException>).</span></span>  
  
-   <span data-ttu-id="05bcf-117">Ścieżka przekracza maksymalną długość zdefiniowaną przez system (<xref:System.IO.PathTooLongException>).</span><span class="sxs-lookup"><span data-stu-id="05bcf-117">The path exceeds the system-defined maximum length (<xref:System.IO.PathTooLongException>).</span></span>  
  
-   <span data-ttu-id="05bcf-118">Nazwa pliku lub katalogu w ścieżce zawiera dwukropek (:) lub jest w nieprawidłowym formacie (<xref:System.NotSupportedException>).</span><span class="sxs-lookup"><span data-stu-id="05bcf-118">A file or directory name in the path contains a colon (:) or is in an invalid format (<xref:System.NotSupportedException>).</span></span>  
  
-   <span data-ttu-id="05bcf-119">Użytkownik nie ma wystarczających uprawnień do wyświetlania ścieżki (<xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="05bcf-119">The user lacks necessary permissions to view the path (<xref:System.Security.SecurityException>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="05bcf-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="05bcf-120">See also</span></span>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllBytes%2A>
- [<span data-ttu-id="05bcf-121">Instrukcje: Zapisywanie tekstu do plików</span><span class="sxs-lookup"><span data-stu-id="05bcf-121">How to: Write Text to Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-write-text-to-files.md)
