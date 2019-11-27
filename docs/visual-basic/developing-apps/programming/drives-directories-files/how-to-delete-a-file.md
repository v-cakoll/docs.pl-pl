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
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348777"
---
# <a name="how-to-delete-a-file-in-visual-basic"></a><span data-ttu-id="0422c-102">Porady: usuwanie pliku w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="0422c-102">How to: Delete a File in Visual Basic</span></span>

<span data-ttu-id="0422c-103">Metoda `DeleteFile` obiektu `My.Computer.FileSystem` umożliwia usunięcie pliku.</span><span class="sxs-lookup"><span data-stu-id="0422c-103">The `DeleteFile` method of the `My.Computer.FileSystem` object allows you to delete a file.</span></span> <span data-ttu-id="0422c-104">Wśród opcji, które oferuje: czy wysłać usunięty plik do **kosza**, czy należy polecić użytkownikowi potwierdzenie, że plik powinien zostać usunięty, i co należy zrobić, gdy użytkownik anuluje operację.</span><span class="sxs-lookup"><span data-stu-id="0422c-104">Among the options it offers are: whether to send the deleted file to the **Recycle Bin**, whether to ask the user to confirm that the file should be deleted, and what to do when the user cancels the operation.</span></span>  
  
### <a name="to-delete-a-text-file"></a><span data-ttu-id="0422c-105">Aby usunąć plik tekstowy</span><span class="sxs-lookup"><span data-stu-id="0422c-105">To delete a text file</span></span>  
  
- <span data-ttu-id="0422c-106">Użyj metody `DeleteFile`, aby usunąć plik.</span><span class="sxs-lookup"><span data-stu-id="0422c-106">Use the `DeleteFile` method to delete the file.</span></span> <span data-ttu-id="0422c-107">Poniższy kod ilustruje sposób usuwania pliku o nazwie `test.txt`.</span><span class="sxs-lookup"><span data-stu-id="0422c-107">The following code demonstrates how to delete the file named `test.txt`.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#22)]  
  
### <a name="to-delete-a-text-file-and-ask-the-user-to-confirm-that-the-file-should-be-deleted"></a><span data-ttu-id="0422c-108">Aby usunąć plik tekstowy i polecić użytkownikowi potwierdzenie, że plik powinien zostać usunięty</span><span class="sxs-lookup"><span data-stu-id="0422c-108">To delete a text file and ask the user to confirm that the file should be deleted</span></span>  
  
- <span data-ttu-id="0422c-109">Użyj metody `DeleteFile`, aby usunąć plik, lub ustaw `showUI` do `AllDialogs`.</span><span class="sxs-lookup"><span data-stu-id="0422c-109">Use the `DeleteFile` method to delete the file, setting `showUI` to `AllDialogs`.</span></span> <span data-ttu-id="0422c-110">Poniższy kod ilustruje sposób usuwania pliku o nazwie `test.txt` i zezwala użytkownikowi na potwierdzenie, że plik powinien zostać usunięty.</span><span class="sxs-lookup"><span data-stu-id="0422c-110">The following code demonstrates how to delete the file named `test.txt` and allow the user to confirm that the file should be deleted.</span></span>  
  
     [!code-vb[VbFileIOMisc#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOMisc/VB/Class1.vb#9)]  
  
### <a name="to-delete-a-text-file-and-send-it-to-the-recycle-bin"></a><span data-ttu-id="0422c-111">Aby usunąć plik tekstowy i wysłać go do kosza</span><span class="sxs-lookup"><span data-stu-id="0422c-111">To delete a text file and send it to the Recycle Bin</span></span>  
  
- <span data-ttu-id="0422c-112">Użyj metody `DeleteFile`, aby usunąć plik, określając `SendToRecycleBin` parametru `recycle`.</span><span class="sxs-lookup"><span data-stu-id="0422c-112">Use the `DeleteFile` method to delete the file, specifying `SendToRecycleBin` for the `recycle` parameter.</span></span> <span data-ttu-id="0422c-113">Poniższy kod ilustruje sposób usuwania pliku o nazwie `test.txt` i wysyłania go do **kosza**.</span><span class="sxs-lookup"><span data-stu-id="0422c-113">The following code demonstrates how to delete the file named `test.txt` and send it to the **Recycle Bin**.</span></span>  
  
     [!code-vb[VbFileIOMisc#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOMisc/VB/Class1.vb#10)]  
  
## <a name="robust-programming"></a><span data-ttu-id="0422c-114">Skuteczne programowanie</span><span class="sxs-lookup"><span data-stu-id="0422c-114">Robust Programming</span></span>  

 <span data-ttu-id="0422c-115">Następujące warunki mogą spowodować wyjątek:</span><span class="sxs-lookup"><span data-stu-id="0422c-115">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="0422c-116">Ścieżka jest nieprawidłowa z jednego z następujących powodów: jest ciągiem o zerowej długości, zawiera tylko biały znak, zawiera nieprawidłowe znaki lub jest ścieżką urządzenia (rozpoczyna się od \\\\.\\) (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="0422c-116">The path is not valid for one of the following reasons: it is a zero-length string, it contains only white space, it contains invalid characters, or it is a device path (starts with \\\\.\\) (<xref:System.ArgumentException>).</span></span>  
  
- <span data-ttu-id="0422c-117">Ścieżka jest nieprawidłowa, ponieważ jest `Nothing` (<xref:System.ArgumentNullException>).</span><span class="sxs-lookup"><span data-stu-id="0422c-117">The path is not valid because it is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
- <span data-ttu-id="0422c-118">Ścieżka przekracza maksymalną długość zdefiniowaną przez system (<xref:System.IO.PathTooLongException>).</span><span class="sxs-lookup"><span data-stu-id="0422c-118">The path exceeds the system-defined maximum length (<xref:System.IO.PathTooLongException>).</span></span>  
  
- <span data-ttu-id="0422c-119">Nazwa pliku lub folderu w ścieżce zawiera dwukropek (:) lub ma nieprawidłowy format (<xref:System.NotSupportedException>).</span><span class="sxs-lookup"><span data-stu-id="0422c-119">A file or folder name in the path contains a colon (:) or is in an invalid format (<xref:System.NotSupportedException>).</span></span>  
  
- <span data-ttu-id="0422c-120">Plik jest używany (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="0422c-120">The file is in use (<xref:System.IO.IOException>).</span></span>  
  
- <span data-ttu-id="0422c-121">Użytkownik nie ma wystarczających uprawnień do wyświetlania ścieżki (<xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="0422c-121">The user lacks necessary permissions to view the path (<xref:System.Security.SecurityException>).</span></span>  
  
- <span data-ttu-id="0422c-122">Plik nie istnieje (<xref:System.IO.FileNotFoundException>).</span><span class="sxs-lookup"><span data-stu-id="0422c-122">The file does not exist (<xref:System.IO.FileNotFoundException>).</span></span>  
  
- <span data-ttu-id="0422c-123">Użytkownik nie ma uprawnień do usunięcia pliku lub plik jest tylko do odczytu (<xref:System.UnauthorizedAccessException>).</span><span class="sxs-lookup"><span data-stu-id="0422c-123">The user does not have permission to delete the file, or the file is read-only (<xref:System.UnauthorizedAccessException>).</span></span>  
  
- <span data-ttu-id="0422c-124">Istnieje sytuacja częściowej relacji zaufania, w której użytkownik nie ma wystarczających uprawnień (<xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="0422c-124">A partial-trust situation exists in which the user does not have sufficient permissions (<xref:System.Security.SecurityException>).</span></span>  
  
- <span data-ttu-id="0422c-125">Użytkownik anulował operację, a `onUserCancel` jest ustawiona na `ThrowException` (<xref:System.OperationCanceledException>).</span><span class="sxs-lookup"><span data-stu-id="0422c-125">The user cancelled the operation and `onUserCancel` is set to `ThrowException` (<xref:System.OperationCanceledException>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0422c-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0422c-126">See also</span></span>

- <xref:Microsoft.VisualBasic.FileIO.UICancelOption>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem>
- <xref:Microsoft.VisualBasic.FileIO.UIOption>
- <xref:Microsoft.VisualBasic.FileIO.RecycleOption>
- [<span data-ttu-id="0422c-127">Instrukcje: pobieranie kolekcji plików z katalogu</span><span class="sxs-lookup"><span data-stu-id="0422c-127">How to: Get the Collection of Files in a Directory</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-get-the-collection-of-files-in-a-directory.md)
