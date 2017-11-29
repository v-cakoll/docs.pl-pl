---
title: 'Porady: usuwanie pliku w Visual Basic'
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- Delete method [Visual Basic]
- files [Visual Basic], deleting
- files [Visual Basic], manipulating
- File object
ms.assetid: 4b721769-3e45-4be7-b7fe-b08dc4141b44
caps.latest.revision: "24"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 536c10070ef51044b801fc6a5805741896586dff
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-delete-a-file-in-visual-basic"></a><span data-ttu-id="02d8e-102">Porady: usuwanie pliku w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="02d8e-102">How to: Delete a File in Visual Basic</span></span>
<span data-ttu-id="02d8e-103">`DeleteFile` Metody `My.Computer.FileSystem` obiektu służy do usuwania pliku.</span><span class="sxs-lookup"><span data-stu-id="02d8e-103">The `DeleteFile` method of the `My.Computer.FileSystem` object allows you to delete a file.</span></span> <span data-ttu-id="02d8e-104">Opcje oferuje należą: czy wysyłać usuniętego pliku do **Kosza**, czy poprosić użytkownika o potwierdzenie, że plik powinien zostać usunięty i co należy zrobić, gdy użytkownik anuluje operację.</span><span class="sxs-lookup"><span data-stu-id="02d8e-104">Among the options it offers are: whether to send the deleted file to the **Recycle Bin**, whether to ask the user to confirm that the file should be deleted, and what to do when the user cancels the operation.</span></span>  
  
### <a name="to-delete-a-text-file"></a><span data-ttu-id="02d8e-105">Aby usunąć plik tekstowy</span><span class="sxs-lookup"><span data-stu-id="02d8e-105">To delete a text file</span></span>  
  
-   <span data-ttu-id="02d8e-106">Użyj `DeleteFile` metodę, aby usunąć plik.</span><span class="sxs-lookup"><span data-stu-id="02d8e-106">Use the `DeleteFile` method to delete the file.</span></span> <span data-ttu-id="02d8e-107">Poniższy kod ilustruje sposób usuwania pliku o nazwie `test.txt`.</span><span class="sxs-lookup"><span data-stu-id="02d8e-107">The following code demonstrates how to delete the file named `test.txt`.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#22](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-delete-a-file_1.vb)]  
  
### <a name="to-delete-a-text-file-and-ask-the-user-to-confirm-that-the-file-should-be-deleted"></a><span data-ttu-id="02d8e-108">Aby usunąć plik tekstowy i monitowanie użytkownika o potwierdzenie, że plik powinien zostać usunięty.</span><span class="sxs-lookup"><span data-stu-id="02d8e-108">To delete a text file and ask the user to confirm that the file should be deleted</span></span>  
  
-   <span data-ttu-id="02d8e-109">Użyj `DeleteFile` do usunięcia pliku z ustawieniami `showUI` do `AllDialogs`.</span><span class="sxs-lookup"><span data-stu-id="02d8e-109">Use the `DeleteFile` method to delete the file, setting `showUI` to `AllDialogs`.</span></span> <span data-ttu-id="02d8e-110">Poniższy kod ilustruje sposób usuwania pliku o nazwie `test.txt` i Zezwalaj użytkownikowi na upewnij się, że plik powinien zostać usunięty.</span><span class="sxs-lookup"><span data-stu-id="02d8e-110">The following code demonstrates how to delete the file named `test.txt` and allow the user to confirm that the file should be deleted.</span></span>  
  
     [!code-vb[VbFileIOMisc#9](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-delete-a-file_2.vb)]  
  
### <a name="to-delete-a-text-file-and-send-it-to-the-recycle-bin"></a><span data-ttu-id="02d8e-111">Aby usunąć plik tekstowy i wysyłania go do Kosza</span><span class="sxs-lookup"><span data-stu-id="02d8e-111">To delete a text file and send it to the Recycle Bin</span></span>  
  
-   <span data-ttu-id="02d8e-112">Użyj `DeleteFile` metodę, aby usunąć plik, określając `SendToRecycleBin` dla `recycle` parametru.</span><span class="sxs-lookup"><span data-stu-id="02d8e-112">Use the `DeleteFile` method to delete the file, specifying `SendToRecycleBin` for the `recycle` parameter.</span></span> <span data-ttu-id="02d8e-113">Poniższy kod ilustruje sposób usuwania pliku o nazwie `test.txt` i wysyłania go do **Kosza**.</span><span class="sxs-lookup"><span data-stu-id="02d8e-113">The following code demonstrates how to delete the file named `test.txt` and send it to the **Recycle Bin**.</span></span>  
  
     [!code-vb[VbFileIOMisc#10](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-delete-a-file_3.vb)]  
  
## <a name="robust-programming"></a><span data-ttu-id="02d8e-114">Niezawodne programowanie</span><span class="sxs-lookup"><span data-stu-id="02d8e-114">Robust Programming</span></span>  
 <span data-ttu-id="02d8e-115">Następujące warunki mogą spowodować wyjątek:</span><span class="sxs-lookup"><span data-stu-id="02d8e-115">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="02d8e-116">Ścieżka nie jest prawidłowy dla jednego z następujących powodów: jest to ciąg o zerowej długości, zawiera tylko biały znak, zawiera nieprawidłowe znaki lub jest ścieżką urządzenia (rozpoczyna się od \\ \\.\\) (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="02d8e-116">The path is not valid for one of the following reasons: it is a zero-length string, it contains only white space, it contains invalid characters, or it is a device path (starts with \\\\.\\) (<xref:System.ArgumentException>).</span></span>  
  
-   <span data-ttu-id="02d8e-117">Ścieżka jest nieprawidłowa, ponieważ jest on `Nothing` (<xref:System.ArgumentNullException>).</span><span class="sxs-lookup"><span data-stu-id="02d8e-117">The path is not valid because it is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
-   <span data-ttu-id="02d8e-118">Ścieżka przekracza maksymalną długość zdefiniowana w systemie (<xref:System.IO.PathTooLongException>).</span><span class="sxs-lookup"><span data-stu-id="02d8e-118">The path exceeds the system-defined maximum length (<xref:System.IO.PathTooLongException>).</span></span>  
  
-   <span data-ttu-id="02d8e-119">Nazwę pliku lub folderu w ścieżce zawiera dwukropek (:) lub jest w nieprawidłowym formacie (<xref:System.NotSupportedException>).</span><span class="sxs-lookup"><span data-stu-id="02d8e-119">A file or folder name in the path contains a colon (:) or is in an invalid format (<xref:System.NotSupportedException>).</span></span>  
  
-   <span data-ttu-id="02d8e-120">Plik jest w użyciu (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="02d8e-120">The file is in use (<xref:System.IO.IOException>).</span></span>  
  
-   <span data-ttu-id="02d8e-121">Użytkownik nie ma wystarczających uprawnień, aby wyświetlić ścieżkę (<xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="02d8e-121">The user lacks necessary permissions to view the path (<xref:System.Security.SecurityException>).</span></span>  
  
-   <span data-ttu-id="02d8e-122">Plik nie istnieje (<xref:System.IO.FileNotFoundException>).</span><span class="sxs-lookup"><span data-stu-id="02d8e-122">The file does not exist (<xref:System.IO.FileNotFoundException>).</span></span>  
  
-   <span data-ttu-id="02d8e-123">Użytkownik nie ma uprawnień do usuwania pliku lub plik jest tylko do odczytu (<xref:System.UnauthorizedAccessException>).</span><span class="sxs-lookup"><span data-stu-id="02d8e-123">The user does not have permission to delete the file, or the file is read-only (<xref:System.UnauthorizedAccessException>).</span></span>  
  
-   <span data-ttu-id="02d8e-124">Istnieje sytuacji częściowego zaufania, użytkownik nie ma wystarczających uprawnień (<xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="02d8e-124">A partial-trust situation exists in which the user does not have sufficient permissions (<xref:System.Security.SecurityException>).</span></span>  
  
-   <span data-ttu-id="02d8e-125">Użytkownik anulował operację i `onUserCancel` ustawiono `ThrowException` (<xref:System.OperationCanceledException>).</span><span class="sxs-lookup"><span data-stu-id="02d8e-125">The user cancelled the operation and `onUserCancel` is set to `ThrowException` (<xref:System.OperationCanceledException>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="02d8e-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="02d8e-126">See Also</span></span>  
 <xref:Microsoft.VisualBasic.FileIO.UICancelOption>  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem>  
 <xref:Microsoft.VisualBasic.FileIO.UIOption>  
 <xref:Microsoft.VisualBasic.FileIO.RecycleOption>  
 [<span data-ttu-id="02d8e-127">Porady: pobieranie kolekcji plików z katalogu</span><span class="sxs-lookup"><span data-stu-id="02d8e-127">How to: Get the Collection of Files in a Directory</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-get-the-collection-of-files-in-a-directory.md)
