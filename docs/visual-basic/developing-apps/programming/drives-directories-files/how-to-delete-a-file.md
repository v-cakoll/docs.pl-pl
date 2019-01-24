---
title: 'Instrukcje: Usuń plik w języku Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- Delete method [Visual Basic]
- files [Visual Basic], deleting
- files [Visual Basic], manipulating
- File object
ms.assetid: 4b721769-3e45-4be7-b7fe-b08dc4141b44
ms.openlocfilehash: 2222c06b71b3063c848495aec52fd4acf0674073
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54520623"
---
# <a name="how-to-delete-a-file-in-visual-basic"></a><span data-ttu-id="d01dd-102">Instrukcje: Usuń plik w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="d01dd-102">How to: Delete a File in Visual Basic</span></span>
<span data-ttu-id="d01dd-103">`DeleteFile` Metody `My.Computer.FileSystem` obiektu umożliwia usunięcie pliku.</span><span class="sxs-lookup"><span data-stu-id="d01dd-103">The `DeleteFile` method of the `My.Computer.FileSystem` object allows you to delete a file.</span></span> <span data-ttu-id="d01dd-104">Spośród opcji oferuje: czy usunięty plik, aby wysłać **Kosza**, czy należy poprosić użytkownika, aby upewnić się, że należy usunąć plik i co należy zrobić, gdy użytkownik anuluje operację.</span><span class="sxs-lookup"><span data-stu-id="d01dd-104">Among the options it offers are: whether to send the deleted file to the **Recycle Bin**, whether to ask the user to confirm that the file should be deleted, and what to do when the user cancels the operation.</span></span>  
  
### <a name="to-delete-a-text-file"></a><span data-ttu-id="d01dd-105">Aby usunąć plik tekstowy</span><span class="sxs-lookup"><span data-stu-id="d01dd-105">To delete a text file</span></span>  
  
-   <span data-ttu-id="d01dd-106">Użyj `DeleteFile` metodę, aby usunąć ten plik.</span><span class="sxs-lookup"><span data-stu-id="d01dd-106">Use the `DeleteFile` method to delete the file.</span></span> <span data-ttu-id="d01dd-107">Poniższy kod ilustruje sposób usunąć plik o nazwie `test.txt`.</span><span class="sxs-lookup"><span data-stu-id="d01dd-107">The following code demonstrates how to delete the file named `test.txt`.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#22](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-delete-a-file_1.vb)]  
  
### <a name="to-delete-a-text-file-and-ask-the-user-to-confirm-that-the-file-should-be-deleted"></a><span data-ttu-id="d01dd-108">Aby usunąć plik tekstowy i poprosić użytkownika, aby upewnić się, że należy usunąć plik</span><span class="sxs-lookup"><span data-stu-id="d01dd-108">To delete a text file and ask the user to confirm that the file should be deleted</span></span>  
  
-   <span data-ttu-id="d01dd-109">Użyj `DeleteFile` metodę, aby usunąć plik, ustawienie `showUI` do `AllDialogs`.</span><span class="sxs-lookup"><span data-stu-id="d01dd-109">Use the `DeleteFile` method to delete the file, setting `showUI` to `AllDialogs`.</span></span> <span data-ttu-id="d01dd-110">Poniższy kod ilustruje sposób usunąć plik o nazwie `test.txt` i umożliwić użytkownikowi upewnij się, że należy usunąć plik.</span><span class="sxs-lookup"><span data-stu-id="d01dd-110">The following code demonstrates how to delete the file named `test.txt` and allow the user to confirm that the file should be deleted.</span></span>  
  
     [!code-vb[VbFileIOMisc#9](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-delete-a-file_2.vb)]  
  
### <a name="to-delete-a-text-file-and-send-it-to-the-recycle-bin"></a><span data-ttu-id="d01dd-111">Aby usunąć plik tekstowy i wysyłać je do Kosza</span><span class="sxs-lookup"><span data-stu-id="d01dd-111">To delete a text file and send it to the Recycle Bin</span></span>  
  
-   <span data-ttu-id="d01dd-112">Użyj `DeleteFile` metodę, aby usunąć plik, określając `SendToRecycleBin` dla `recycle` parametru.</span><span class="sxs-lookup"><span data-stu-id="d01dd-112">Use the `DeleteFile` method to delete the file, specifying `SendToRecycleBin` for the `recycle` parameter.</span></span> <span data-ttu-id="d01dd-113">Poniższy kod ilustruje sposób usunąć plik o nazwie `test.txt` oraz wysyłać je do **Kosza**.</span><span class="sxs-lookup"><span data-stu-id="d01dd-113">The following code demonstrates how to delete the file named `test.txt` and send it to the **Recycle Bin**.</span></span>  
  
     [!code-vb[VbFileIOMisc#10](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-delete-a-file_3.vb)]  
  
## <a name="robust-programming"></a><span data-ttu-id="d01dd-114">Niezawodne programowanie</span><span class="sxs-lookup"><span data-stu-id="d01dd-114">Robust Programming</span></span>  
 <span data-ttu-id="d01dd-115">Następujące warunki mogą spowodować wyjątek:</span><span class="sxs-lookup"><span data-stu-id="d01dd-115">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="d01dd-116">Ścieżka nie jest prawidłowa dla jednego z następujących przyczyn: jest to ciąg o zerowej długości, zawiera tylko znak odstępu, zawiera nieprawidłowe znaki lub jest ścieżką do urządzenia (rozpoczyna się od \\ \\.\\) (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="d01dd-116">The path is not valid for one of the following reasons: it is a zero-length string, it contains only white space, it contains invalid characters, or it is a device path (starts with \\\\.\\) (<xref:System.ArgumentException>).</span></span>  
  
-   <span data-ttu-id="d01dd-117">Ścieżka jest nieprawidłowa, ponieważ jest on `Nothing` (<xref:System.ArgumentNullException>).</span><span class="sxs-lookup"><span data-stu-id="d01dd-117">The path is not valid because it is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
-   <span data-ttu-id="d01dd-118">Ścieżka przekracza maksymalną długość zdefiniowaną przez system (<xref:System.IO.PathTooLongException>).</span><span class="sxs-lookup"><span data-stu-id="d01dd-118">The path exceeds the system-defined maximum length (<xref:System.IO.PathTooLongException>).</span></span>  
  
-   <span data-ttu-id="d01dd-119">Nazwa pliku lub folderu w ścieżce zawiera dwukropek (:) lub jest w nieprawidłowym formacie (<xref:System.NotSupportedException>).</span><span class="sxs-lookup"><span data-stu-id="d01dd-119">A file or folder name in the path contains a colon (:) or is in an invalid format (<xref:System.NotSupportedException>).</span></span>  
  
-   <span data-ttu-id="d01dd-120">Plik jest w użyciu (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="d01dd-120">The file is in use (<xref:System.IO.IOException>).</span></span>  
  
-   <span data-ttu-id="d01dd-121">Użytkownik nie ma wystarczających uprawnień do wyświetlania ścieżki (<xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="d01dd-121">The user lacks necessary permissions to view the path (<xref:System.Security.SecurityException>).</span></span>  
  
-   <span data-ttu-id="d01dd-122">Plik nie istnieje (<xref:System.IO.FileNotFoundException>).</span><span class="sxs-lookup"><span data-stu-id="d01dd-122">The file does not exist (<xref:System.IO.FileNotFoundException>).</span></span>  
  
-   <span data-ttu-id="d01dd-123">Użytkownik nie ma uprawnień do usunięcia pliku lub plik jest tylko do odczytu (<xref:System.UnauthorizedAccessException>).</span><span class="sxs-lookup"><span data-stu-id="d01dd-123">The user does not have permission to delete the file, or the file is read-only (<xref:System.UnauthorizedAccessException>).</span></span>  
  
-   <span data-ttu-id="d01dd-124">Sytuacja częściowego zaufania istnieje, w którym użytkownik nie ma wystarczających uprawnień (<xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="d01dd-124">A partial-trust situation exists in which the user does not have sufficient permissions (<xref:System.Security.SecurityException>).</span></span>  
  
-   <span data-ttu-id="d01dd-125">Użytkownik anulował operację i `onUserCancel` ustawiono `ThrowException` (<xref:System.OperationCanceledException>).</span><span class="sxs-lookup"><span data-stu-id="d01dd-125">The user cancelled the operation and `onUserCancel` is set to `ThrowException` (<xref:System.OperationCanceledException>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d01dd-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d01dd-126">See also</span></span>
- <xref:Microsoft.VisualBasic.FileIO.UICancelOption>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem>
- <xref:Microsoft.VisualBasic.FileIO.UIOption>
- <xref:Microsoft.VisualBasic.FileIO.RecycleOption>
- [<span data-ttu-id="d01dd-127">Instrukcje: Pobieranie kolekcji plików w katalogu</span><span class="sxs-lookup"><span data-stu-id="d01dd-127">How to: Get the Collection of Files in a Directory</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-get-the-collection-of-files-in-a-directory.md)
