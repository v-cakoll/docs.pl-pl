---
title: 'Porady: usuwanie pliku w Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- Delete method [Visual Basic]
- files [Visual Basic], deleting
- files [Visual Basic], manipulating
- File object
ms.assetid: 4b721769-3e45-4be7-b7fe-b08dc4141b44
ms.openlocfilehash: 2918b756d5f37de2489042a9eabfe7312841af81
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-delete-a-file-in-visual-basic"></a><span data-ttu-id="d57a2-102">Porady: usuwanie pliku w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="d57a2-102">How to: Delete a File in Visual Basic</span></span>
<span data-ttu-id="d57a2-103">`DeleteFile` Metody `My.Computer.FileSystem` obiektu służy do usuwania pliku.</span><span class="sxs-lookup"><span data-stu-id="d57a2-103">The `DeleteFile` method of the `My.Computer.FileSystem` object allows you to delete a file.</span></span> <span data-ttu-id="d57a2-104">Opcje oferuje należą: czy wysyłać usuniętego pliku do **Kosza**, czy poprosić użytkownika o potwierdzenie, że plik powinien zostać usunięty i co należy zrobić, gdy użytkownik anuluje operację.</span><span class="sxs-lookup"><span data-stu-id="d57a2-104">Among the options it offers are: whether to send the deleted file to the **Recycle Bin**, whether to ask the user to confirm that the file should be deleted, and what to do when the user cancels the operation.</span></span>  
  
### <a name="to-delete-a-text-file"></a><span data-ttu-id="d57a2-105">Aby usunąć plik tekstowy</span><span class="sxs-lookup"><span data-stu-id="d57a2-105">To delete a text file</span></span>  
  
-   <span data-ttu-id="d57a2-106">Użyj `DeleteFile` metodę, aby usunąć plik.</span><span class="sxs-lookup"><span data-stu-id="d57a2-106">Use the `DeleteFile` method to delete the file.</span></span> <span data-ttu-id="d57a2-107">Poniższy kod ilustruje sposób usuwania pliku o nazwie `test.txt`.</span><span class="sxs-lookup"><span data-stu-id="d57a2-107">The following code demonstrates how to delete the file named `test.txt`.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#22](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-delete-a-file_1.vb)]  
  
### <a name="to-delete-a-text-file-and-ask-the-user-to-confirm-that-the-file-should-be-deleted"></a><span data-ttu-id="d57a2-108">Aby usunąć plik tekstowy i monitowanie użytkownika o potwierdzenie, że plik powinien zostać usunięty.</span><span class="sxs-lookup"><span data-stu-id="d57a2-108">To delete a text file and ask the user to confirm that the file should be deleted</span></span>  
  
-   <span data-ttu-id="d57a2-109">Użyj `DeleteFile` do usunięcia pliku z ustawieniami `showUI` do `AllDialogs`.</span><span class="sxs-lookup"><span data-stu-id="d57a2-109">Use the `DeleteFile` method to delete the file, setting `showUI` to `AllDialogs`.</span></span> <span data-ttu-id="d57a2-110">Poniższy kod ilustruje sposób usuwania pliku o nazwie `test.txt` i Zezwalaj użytkownikowi na upewnij się, że plik powinien zostać usunięty.</span><span class="sxs-lookup"><span data-stu-id="d57a2-110">The following code demonstrates how to delete the file named `test.txt` and allow the user to confirm that the file should be deleted.</span></span>  
  
     [!code-vb[VbFileIOMisc#9](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-delete-a-file_2.vb)]  
  
### <a name="to-delete-a-text-file-and-send-it-to-the-recycle-bin"></a><span data-ttu-id="d57a2-111">Aby usunąć plik tekstowy i wysyłania go do Kosza</span><span class="sxs-lookup"><span data-stu-id="d57a2-111">To delete a text file and send it to the Recycle Bin</span></span>  
  
-   <span data-ttu-id="d57a2-112">Użyj `DeleteFile` metodę, aby usunąć plik, określając `SendToRecycleBin` dla `recycle` parametru.</span><span class="sxs-lookup"><span data-stu-id="d57a2-112">Use the `DeleteFile` method to delete the file, specifying `SendToRecycleBin` for the `recycle` parameter.</span></span> <span data-ttu-id="d57a2-113">Poniższy kod ilustruje sposób usuwania pliku o nazwie `test.txt` i wysyłania go do **Kosza**.</span><span class="sxs-lookup"><span data-stu-id="d57a2-113">The following code demonstrates how to delete the file named `test.txt` and send it to the **Recycle Bin**.</span></span>  
  
     [!code-vb[VbFileIOMisc#10](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-delete-a-file_3.vb)]  
  
## <a name="robust-programming"></a><span data-ttu-id="d57a2-114">Niezawodne programowanie</span><span class="sxs-lookup"><span data-stu-id="d57a2-114">Robust Programming</span></span>  
 <span data-ttu-id="d57a2-115">Następujące warunki mogą spowodować wyjątek:</span><span class="sxs-lookup"><span data-stu-id="d57a2-115">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="d57a2-116">Ścieżka nie jest prawidłowy dla jednego z następujących powodów: jest to ciąg o zerowej długości, zawiera tylko biały znak, zawiera nieprawidłowe znaki lub jest ścieżką urządzenia (rozpoczyna się od \\ \\.\\) (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="d57a2-116">The path is not valid for one of the following reasons: it is a zero-length string, it contains only white space, it contains invalid characters, or it is a device path (starts with \\\\.\\) (<xref:System.ArgumentException>).</span></span>  
  
-   <span data-ttu-id="d57a2-117">Ścieżka jest nieprawidłowa, ponieważ jest on `Nothing` (<xref:System.ArgumentNullException>).</span><span class="sxs-lookup"><span data-stu-id="d57a2-117">The path is not valid because it is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
-   <span data-ttu-id="d57a2-118">Ścieżka przekracza maksymalną długość zdefiniowana w systemie (<xref:System.IO.PathTooLongException>).</span><span class="sxs-lookup"><span data-stu-id="d57a2-118">The path exceeds the system-defined maximum length (<xref:System.IO.PathTooLongException>).</span></span>  
  
-   <span data-ttu-id="d57a2-119">Nazwę pliku lub folderu w ścieżce zawiera dwukropek (:) lub jest w nieprawidłowym formacie (<xref:System.NotSupportedException>).</span><span class="sxs-lookup"><span data-stu-id="d57a2-119">A file or folder name in the path contains a colon (:) or is in an invalid format (<xref:System.NotSupportedException>).</span></span>  
  
-   <span data-ttu-id="d57a2-120">Plik jest w użyciu (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="d57a2-120">The file is in use (<xref:System.IO.IOException>).</span></span>  
  
-   <span data-ttu-id="d57a2-121">Użytkownik nie ma wystarczających uprawnień, aby wyświetlić ścieżkę (<xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="d57a2-121">The user lacks necessary permissions to view the path (<xref:System.Security.SecurityException>).</span></span>  
  
-   <span data-ttu-id="d57a2-122">Plik nie istnieje (<xref:System.IO.FileNotFoundException>).</span><span class="sxs-lookup"><span data-stu-id="d57a2-122">The file does not exist (<xref:System.IO.FileNotFoundException>).</span></span>  
  
-   <span data-ttu-id="d57a2-123">Użytkownik nie ma uprawnień do usuwania pliku lub plik jest tylko do odczytu (<xref:System.UnauthorizedAccessException>).</span><span class="sxs-lookup"><span data-stu-id="d57a2-123">The user does not have permission to delete the file, or the file is read-only (<xref:System.UnauthorizedAccessException>).</span></span>  
  
-   <span data-ttu-id="d57a2-124">Istnieje sytuacji częściowego zaufania, użytkownik nie ma wystarczających uprawnień (<xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="d57a2-124">A partial-trust situation exists in which the user does not have sufficient permissions (<xref:System.Security.SecurityException>).</span></span>  
  
-   <span data-ttu-id="d57a2-125">Użytkownik anulował operację i `onUserCancel` ustawiono `ThrowException` (<xref:System.OperationCanceledException>).</span><span class="sxs-lookup"><span data-stu-id="d57a2-125">The user cancelled the operation and `onUserCancel` is set to `ThrowException` (<xref:System.OperationCanceledException>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d57a2-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d57a2-126">See Also</span></span>  
 <xref:Microsoft.VisualBasic.FileIO.UICancelOption>  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem>  
 <xref:Microsoft.VisualBasic.FileIO.UIOption>  
 <xref:Microsoft.VisualBasic.FileIO.RecycleOption>  
 [<span data-ttu-id="d57a2-127">Instrukcje: pobieranie kolekcji plików z katalogu</span><span class="sxs-lookup"><span data-stu-id="d57a2-127">How to: Get the Collection of Files in a Directory</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-get-the-collection-of-files-in-a-directory.md)
