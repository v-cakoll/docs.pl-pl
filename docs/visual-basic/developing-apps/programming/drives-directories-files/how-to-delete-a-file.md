---
title: 'Porady: usuwanie pliku'
ms.date: 07/20/2015
helpviewer_keywords:
- Delete method [Visual Basic]
- files [Visual Basic], deleting
- files [Visual Basic], manipulating
- File object
ms.assetid: 4b721769-3e45-4be7-b7fe-b08dc4141b44
ms.openlocfilehash: 57182f1a1d92b7fe954fd26b32c5e4b1107823ee
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "74348777"
---
# <a name="how-to-delete-a-file-in-visual-basic"></a><span data-ttu-id="9a71c-102">Porady: usuwanie pliku w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="9a71c-102">How to: Delete a File in Visual Basic</span></span>

<span data-ttu-id="9a71c-103">Metoda `DeleteFile` `My.Computer.FileSystem` obiektu umożliwia usunięcie pliku.</span><span class="sxs-lookup"><span data-stu-id="9a71c-103">The `DeleteFile` method of the `My.Computer.FileSystem` object allows you to delete a file.</span></span> <span data-ttu-id="9a71c-104">Wśród opcji, które oferuje to: czy wysłać usunięty plik do **Kosza**, czy poprosić użytkownika o potwierdzenie, że plik powinien zostać usunięty, i co zrobić, gdy użytkownik anuluje operację.</span><span class="sxs-lookup"><span data-stu-id="9a71c-104">Among the options it offers are: whether to send the deleted file to the **Recycle Bin**, whether to ask the user to confirm that the file should be deleted, and what to do when the user cancels the operation.</span></span>  
  
### <a name="to-delete-a-text-file"></a><span data-ttu-id="9a71c-105">Aby usunąć plik tekstowy</span><span class="sxs-lookup"><span data-stu-id="9a71c-105">To delete a text file</span></span>  
  
- <span data-ttu-id="9a71c-106">Użyj `DeleteFile` metody, aby usunąć plik.</span><span class="sxs-lookup"><span data-stu-id="9a71c-106">Use the `DeleteFile` method to delete the file.</span></span> <span data-ttu-id="9a71c-107">Poniższy kod pokazuje, jak usunąć `test.txt`plik o nazwie .</span><span class="sxs-lookup"><span data-stu-id="9a71c-107">The following code demonstrates how to delete the file named `test.txt`.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#22)]  
  
### <a name="to-delete-a-text-file-and-ask-the-user-to-confirm-that-the-file-should-be-deleted"></a><span data-ttu-id="9a71c-108">Aby usunąć plik tekstowy i poprosić użytkownika o potwierdzenie, że plik powinien zostać usunięty</span><span class="sxs-lookup"><span data-stu-id="9a71c-108">To delete a text file and ask the user to confirm that the file should be deleted</span></span>  
  
- <span data-ttu-id="9a71c-109">Użyj `DeleteFile` metody, aby usunąć `showUI` plik, ustawiając na `AllDialogs`.</span><span class="sxs-lookup"><span data-stu-id="9a71c-109">Use the `DeleteFile` method to delete the file, setting `showUI` to `AllDialogs`.</span></span> <span data-ttu-id="9a71c-110">Poniższy kod pokazuje, jak usunąć `test.txt` plik o nazwie i umożliwić użytkownikowi potwierdzenie, że plik powinien zostać usunięty.</span><span class="sxs-lookup"><span data-stu-id="9a71c-110">The following code demonstrates how to delete the file named `test.txt` and allow the user to confirm that the file should be deleted.</span></span>  
  
     [!code-vb[VbFileIOMisc#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOMisc/VB/Class1.vb#9)]  
  
### <a name="to-delete-a-text-file-and-send-it-to-the-recycle-bin"></a><span data-ttu-id="9a71c-111">Aby usunąć plik tekstowy i wysłać go do Kosza</span><span class="sxs-lookup"><span data-stu-id="9a71c-111">To delete a text file and send it to the Recycle Bin</span></span>  
  
- <span data-ttu-id="9a71c-112">Użyj `DeleteFile` metody, aby usunąć plik, określając `SendToRecycleBin` dla parametru. `recycle`</span><span class="sxs-lookup"><span data-stu-id="9a71c-112">Use the `DeleteFile` method to delete the file, specifying `SendToRecycleBin` for the `recycle` parameter.</span></span> <span data-ttu-id="9a71c-113">Poniższy kod pokazuje, jak usunąć `test.txt` nazwany plik i wysłać go do **Kosza**.</span><span class="sxs-lookup"><span data-stu-id="9a71c-113">The following code demonstrates how to delete the file named `test.txt` and send it to the **Recycle Bin**.</span></span>  
  
     [!code-vb[VbFileIOMisc#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOMisc/VB/Class1.vb#10)]  
  
## <a name="robust-programming"></a><span data-ttu-id="9a71c-114">Niezawodne programowanie</span><span class="sxs-lookup"><span data-stu-id="9a71c-114">Robust Programming</span></span>  

 <span data-ttu-id="9a71c-115">Następujące warunki mogą spowodować wyjątek:</span><span class="sxs-lookup"><span data-stu-id="9a71c-115">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="9a71c-116">Ścieżka nie jest prawidłowa z jednego z następujących powodów: jest ciągiem o zerowej długości, zawiera tylko biały znak, \\ \\\\zawiera nieprawidłowe znaki lub jest ścieżką urządzenia (zaczyna się od . ) (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="9a71c-116">The path is not valid for one of the following reasons: it is a zero-length string, it contains only white space, it contains invalid characters, or it is a device path (starts with \\\\.\\) (<xref:System.ArgumentException>).</span></span>  
  
- <span data-ttu-id="9a71c-117">Ścieżka jest nieprawidłowa, `Nothing` ponieważ<xref:System.ArgumentNullException>jest ( ).</span><span class="sxs-lookup"><span data-stu-id="9a71c-117">The path is not valid because it is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
- <span data-ttu-id="9a71c-118">Ścieżka przekracza zdefiniowaną przez system<xref:System.IO.PathTooLongException>maksymalną długość ( ).</span><span class="sxs-lookup"><span data-stu-id="9a71c-118">The path exceeds the system-defined maximum length (<xref:System.IO.PathTooLongException>).</span></span>  
  
- <span data-ttu-id="9a71c-119">Nazwa pliku lub folderu w ścieżce zawiera dwukropek (:) lub jest w nieprawidłowym formacie (<xref:System.NotSupportedException>).</span><span class="sxs-lookup"><span data-stu-id="9a71c-119">A file or folder name in the path contains a colon (:) or is in an invalid format (<xref:System.NotSupportedException>).</span></span>  
  
- <span data-ttu-id="9a71c-120">Plik jest używany<xref:System.IO.IOException>( ).</span><span class="sxs-lookup"><span data-stu-id="9a71c-120">The file is in use (<xref:System.IO.IOException>).</span></span>  
  
- <span data-ttu-id="9a71c-121">Użytkownik nie ma niezbędnych uprawnień do<xref:System.Security.SecurityException>wyświetlania ścieżki ( ).</span><span class="sxs-lookup"><span data-stu-id="9a71c-121">The user lacks necessary permissions to view the path (<xref:System.Security.SecurityException>).</span></span>  
  
- <span data-ttu-id="9a71c-122">Plik nie istnieje<xref:System.IO.FileNotFoundException>( ).</span><span class="sxs-lookup"><span data-stu-id="9a71c-122">The file does not exist (<xref:System.IO.FileNotFoundException>).</span></span>  
  
- <span data-ttu-id="9a71c-123">Użytkownik nie ma uprawnień do usunięcia pliku lub plik<xref:System.UnauthorizedAccessException>jest tylko do odczytu ( ).</span><span class="sxs-lookup"><span data-stu-id="9a71c-123">The user does not have permission to delete the file, or the file is read-only (<xref:System.UnauthorizedAccessException>).</span></span>  
  
- <span data-ttu-id="9a71c-124">Istnieje sytuacja częściowego zaufania, w której użytkownik nie<xref:System.Security.SecurityException>ma wystarczających uprawnień ( ).</span><span class="sxs-lookup"><span data-stu-id="9a71c-124">A partial-trust situation exists in which the user does not have sufficient permissions (<xref:System.Security.SecurityException>).</span></span>  
  
- <span data-ttu-id="9a71c-125">Użytkownik anulował operację `onUserCancel` i jest `ThrowException` <xref:System.OperationCanceledException>ustawiony na ( ).</span><span class="sxs-lookup"><span data-stu-id="9a71c-125">The user cancelled the operation and `onUserCancel` is set to `ThrowException` (<xref:System.OperationCanceledException>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9a71c-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9a71c-126">See also</span></span>

- <xref:Microsoft.VisualBasic.FileIO.UICancelOption>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem>
- <xref:Microsoft.VisualBasic.FileIO.UIOption>
- <xref:Microsoft.VisualBasic.FileIO.RecycleOption>
- [<span data-ttu-id="9a71c-127">Porady: pobieranie kolekcji plików z katalogu w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="9a71c-127">How to: Get the Collection of Files in a Directory</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-get-the-collection-of-files-in-a-directory.md)
