---
title: 'Porady: zapis w plikach binarnych w Visual Basic'
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- files [Visual Basic], binary access
- WriteAllBytes method [Visual Basic]
- binary files [Visual Basic], writing in Visual Basic
ms.assetid: 59fae125-de5b-4c96-883c-209f4a55112c
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 4d8f908822dbcb865f427bee082b8bc4e22ca7fe
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-write-to-binary-files-in-visual-basic"></a><span data-ttu-id="edcac-102">Porady: zapis w plikach binarnych w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="edcac-102">How to: Write to Binary Files in Visual Basic</span></span>
<span data-ttu-id="edcac-103"><xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllBytes%2A> Metody zapisuje dane w pliku binarnym.</span><span class="sxs-lookup"><span data-stu-id="edcac-103">The <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllBytes%2A> method writes data to a binary file.</span></span> <span data-ttu-id="edcac-104">Jeśli `append` parametr jest `True`, dołączy danych do pliku; w przeciwnym razie dane w pliku są zastępowane.</span><span class="sxs-lookup"><span data-stu-id="edcac-104">If the `append` parameter is `True`, it will append the data to the file; otherwise data in the file is overwritten.</span></span>  
  
 <span data-ttu-id="edcac-105">Jeśli określona ścieżka, z wyłączeniem nazwa pliku nie jest prawidłowy, <xref:System.IO.DirectoryNotFoundException> zostanie wygenerowany wyjątek.</span><span class="sxs-lookup"><span data-stu-id="edcac-105">If the specified path excluding the file name is not valid, a <xref:System.IO.DirectoryNotFoundException> exception will be thrown.</span></span> <span data-ttu-id="edcac-106">Jeśli ścieżka jest prawidłowa, ale plik nie istnieje, zostanie utworzony plik.</span><span class="sxs-lookup"><span data-stu-id="edcac-106">If the path is valid but the file does not exist, the file will be created.</span></span>  
  
### <a name="to-write-to-a-binary-file"></a><span data-ttu-id="edcac-107">Można zapisać do pliku binarnego</span><span class="sxs-lookup"><span data-stu-id="edcac-107">To write to a binary file</span></span>  
  
-   <span data-ttu-id="edcac-108">Użyj `WriteAllBytes` metody, podając ścieżkę pliku i nazwa i liczba bajtów do zapisania.</span><span class="sxs-lookup"><span data-stu-id="edcac-108">Use the `WriteAllBytes` method, supplying the file path and name and the bytes to be written.</span></span> <span data-ttu-id="edcac-109">W tym przykładzie dołącza tablicy danych `CustomerData` pliku o nazwie `CollectedData.dat`.</span><span class="sxs-lookup"><span data-stu-id="edcac-109">This example appends the data array `CustomerData` to the file named `CollectedData.dat`.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#27](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-write-to-binary-files_1.vb)]  
  
## <a name="robust-programming"></a><span data-ttu-id="edcac-110">Niezawodne programowanie</span><span class="sxs-lookup"><span data-stu-id="edcac-110">Robust Programming</span></span>  
 <span data-ttu-id="edcac-111">Poniższe warunki mogą utworzyć wyjątek:</span><span class="sxs-lookup"><span data-stu-id="edcac-111">The following conditions may create an exception:</span></span>  
  
-   <span data-ttu-id="edcac-112">Ścieżka nie jest prawidłowy dla jednego z następujących powodów: jest ciąg o zerowej długości. zawiera tylko biały znak lub zawiera nieprawidłowe znaki.</span><span class="sxs-lookup"><span data-stu-id="edcac-112">The path is not valid for one of the following reasons: it is a zero-length string; it contains only white space; or it contains invalid characters.</span></span> <span data-ttu-id="edcac-113">(<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="edcac-113">(<xref:System.ArgumentException>).</span></span>  
  
-   <span data-ttu-id="edcac-114">Ścieżka jest nieprawidłowa, ponieważ jest on `Nothing` (<xref:System.ArgumentNullException>).</span><span class="sxs-lookup"><span data-stu-id="edcac-114">The path is not valid because it is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
-   <span data-ttu-id="edcac-115">`File`wskazuje na ścieżkę, która nie istnieje (<xref:System.IO.FileNotFoundException> lub <xref:System.IO.DirectoryNotFoundException>).</span><span class="sxs-lookup"><span data-stu-id="edcac-115">`File` points to a path that does not exist (<xref:System.IO.FileNotFoundException> or <xref:System.IO.DirectoryNotFoundException>).</span></span>  
  
-   <span data-ttu-id="edcac-116">Plik jest używany przez inny proces lub błąd We/Wy (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="edcac-116">The file is in use by another process, or an I/O error occurs (<xref:System.IO.IOException>).</span></span>  
  
-   <span data-ttu-id="edcac-117">Ścieżka przekracza maksymalną długość zdefiniowana w systemie (<xref:System.IO.PathTooLongException>).</span><span class="sxs-lookup"><span data-stu-id="edcac-117">The path exceeds the system-defined maximum length (<xref:System.IO.PathTooLongException>).</span></span>  
  
-   <span data-ttu-id="edcac-118">Nazwę pliku lub katalogu w ścieżce zawiera dwukropek (:) lub jest w nieprawidłowym formacie (<xref:System.NotSupportedException>).</span><span class="sxs-lookup"><span data-stu-id="edcac-118">A file or directory name in the path contains a colon (:) or is in an invalid format (<xref:System.NotSupportedException>).</span></span>  
  
-   <span data-ttu-id="edcac-119">Użytkownik nie ma wystarczających uprawnień, aby wyświetlić ścieżkę (<xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="edcac-119">The user lacks necessary permissions to view the path (<xref:System.Security.SecurityException>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="edcac-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="edcac-120">See Also</span></span>  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllBytes%2A>  
 [<span data-ttu-id="edcac-121">Porady: zapisywanie tekstu do plików</span><span class="sxs-lookup"><span data-stu-id="edcac-121">How to: Write Text to Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-write-text-to-files.md)
