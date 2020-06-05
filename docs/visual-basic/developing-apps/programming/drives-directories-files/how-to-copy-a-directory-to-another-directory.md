---
title: 'Instrukcje: Kopiowanie katalogu do innego katalogu'
ms.date: 07/20/2015
helpviewer_keywords:
- I/O [Visual Basic], copying directories
- I/O [Visual Basic], copying folders
- folders [Visual Basic], copying
- directories [Visual Basic], copying
ms.assetid: 2a370bd7-10ba-4219-afc4-4519d031eb6c
ms.openlocfilehash: e28f50f6a812188ac7af801cea691818488bd6cd
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84401722"
---
# <a name="how-to-copy-a-directory-to-another-directory-in-visual-basic"></a><span data-ttu-id="8210e-102">Porady: kopiowanie katalogu do innego katalogu w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="8210e-102">How to: Copy a Directory to Another Directory in Visual Basic</span></span>

<span data-ttu-id="8210e-103">Użyj <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyDirectory%2A> metody, aby skopiować katalog do innego katalogu.</span><span class="sxs-lookup"><span data-stu-id="8210e-103">Use the <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyDirectory%2A> method to copy a directory to another directory.</span></span> <span data-ttu-id="8210e-104">Ta metoda kopiuje zawartość katalogu oraz sam katalog.</span><span class="sxs-lookup"><span data-stu-id="8210e-104">This method copies the contents of the directory as well as the directory itself.</span></span> <span data-ttu-id="8210e-105">Jeśli katalog docelowy nie istnieje, zostanie utworzony.</span><span class="sxs-lookup"><span data-stu-id="8210e-105">If the target directory does not exist, it will be created.</span></span> <span data-ttu-id="8210e-106">Jeśli katalog o tej samej nazwie istnieje w lokalizacji docelowej i `overwrite` ma ustawioną wartość `False` , zawartość tych dwóch katalogów zostanie scalona.</span><span class="sxs-lookup"><span data-stu-id="8210e-106">If a directory with the same name exists in the target location and `overwrite` is set to `False`, the contents of the two directories will be merged.</span></span> <span data-ttu-id="8210e-107">Podczas operacji można określić nową nazwę katalogu.</span><span class="sxs-lookup"><span data-stu-id="8210e-107">You can specify a new name for the directory during the operation.</span></span>

<span data-ttu-id="8210e-108">Podczas kopiowania plików w katalogu mogą zostać zgłoszone wyjątki, które są spowodowane przez określony plik, taki jak plik istniejący podczas scalania, gdy `overwrite` jest ustawiony na `False` .</span><span class="sxs-lookup"><span data-stu-id="8210e-108">When copying files within a directory, exceptions may be thrown that are caused by specific file, such as a file existing during a merge while `overwrite` is set to `False`.</span></span> <span data-ttu-id="8210e-109">Gdy takie wyjątki są zgłaszane, są one konsolidowane w jednym wyjątku, którego `Data` Właściwość zawiera wpisy, w których plik lub ścieżka katalogu jest kluczem, a określony komunikat wyjątku jest zawarty w odpowiedniej wartości.</span><span class="sxs-lookup"><span data-stu-id="8210e-109">When such exceptions are thrown, they are consolidated into a single exception, whose `Data` property holds entries in which the file or directory path is the key and the specific exception message is contained in the corresponding value.</span></span>

## <a name="to-copy-a-directory-to-another-directory"></a><span data-ttu-id="8210e-110">Aby skopiować katalog do innego katalogu</span><span class="sxs-lookup"><span data-stu-id="8210e-110">To copy a directory to another directory</span></span>

- <span data-ttu-id="8210e-111">Użyj `CopyDirectory` metody, określając źródłową i docelową nazwę katalogu.</span><span class="sxs-lookup"><span data-stu-id="8210e-111">Use the `CopyDirectory` method, specifying source and destination directory names.</span></span> <span data-ttu-id="8210e-112">Poniższy przykład kopiuje katalog o nazwie `TestDirectory1` do `TestDirectory2` , zastępując istniejące pliki.</span><span class="sxs-lookup"><span data-stu-id="8210e-112">The following example copies the directory named `TestDirectory1` into `TestDirectory2`, overwriting existing files.</span></span>

    [!code-vb[VbVbcnMyFileSystem#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#16)]

    <span data-ttu-id="8210e-113">Ten przykład kodu jest również dostępny jako fragment kodu IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="8210e-113">This code example is also available as an IntelliSense code snippet.</span></span> <span data-ttu-id="8210e-114">W selektorze fragmentów kodu znajduje się w **systemie plików — dyski, foldery i pliki**.</span><span class="sxs-lookup"><span data-stu-id="8210e-114">In the code snippet picker, it is located in **File system - Processing Drives, Folders, and Files**.</span></span> <span data-ttu-id="8210e-115">Aby uzyskać więcej informacji, zobacz [fragmenty kodu](/visualstudio/ide/code-snippets).</span><span class="sxs-lookup"><span data-stu-id="8210e-115">For more information, see [Code Snippets](/visualstudio/ide/code-snippets).</span></span>

## <a name="robust-programming"></a><span data-ttu-id="8210e-116">Niezawodne programowanie</span><span class="sxs-lookup"><span data-stu-id="8210e-116">Robust Programming</span></span>

<span data-ttu-id="8210e-117">Następujące warunki mogą spowodować wyjątek:</span><span class="sxs-lookup"><span data-stu-id="8210e-117">The following conditions may cause an exception:</span></span>

- <span data-ttu-id="8210e-118">Nowa nazwa określona dla katalogu zawiera dwukropek (:) lub ukośnik (\ lub/) ( <xref:System.ArgumentException> ).</span><span class="sxs-lookup"><span data-stu-id="8210e-118">The new name specified for the directory contains a colon (:) or slash (\ or /) (<xref:System.ArgumentException>).</span></span>

- <span data-ttu-id="8210e-119">Ścieżka jest nieprawidłowa z jednego z następujących powodów: jest ciągiem o zerowej długości, zawiera tylko biały znak, zawiera nieprawidłowe znaki lub jest ścieżką urządzenia (zaczyna się od \\ \\ . \\ ) (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="8210e-119">The path is not valid for one of the following reasons: it is a zero-length string, it contains only white space, it contains invalid characters, or it is a device path (starts with \\\\.\\) (<xref:System.ArgumentException>).</span></span>

- <span data-ttu-id="8210e-120">Ścieżka jest nieprawidłowa, ponieważ jest `Nothing` ( <xref:System.ArgumentNullException> ).</span><span class="sxs-lookup"><span data-stu-id="8210e-120">The path is not valid because it is `Nothing` (<xref:System.ArgumentNullException>).</span></span>

- <span data-ttu-id="8210e-121">`destinationDirectoryName`jest `Nothing` lub ciągiem pustym ( <xref:System.ArgumentNullException> )</span><span class="sxs-lookup"><span data-stu-id="8210e-121">`destinationDirectoryName` is `Nothing` or an empty string (<xref:System.ArgumentNullException>)</span></span>

- <span data-ttu-id="8210e-122">Katalog źródłowy nie istnieje ( <xref:System.IO.DirectoryNotFoundException> ).</span><span class="sxs-lookup"><span data-stu-id="8210e-122">The source directory does not exist (<xref:System.IO.DirectoryNotFoundException>).</span></span>

- <span data-ttu-id="8210e-123">Katalog źródłowy jest katalogiem głównym ( <xref:System.IO.IOException> ).</span><span class="sxs-lookup"><span data-stu-id="8210e-123">The source directory is a root directory (<xref:System.IO.IOException>).</span></span>

- <span data-ttu-id="8210e-124">Połączona ścieżka wskazuje istniejący plik ( <xref:System.IO.IOException> ).</span><span class="sxs-lookup"><span data-stu-id="8210e-124">The combined path points to an existing file (<xref:System.IO.IOException>).</span></span>

- <span data-ttu-id="8210e-125">Ścieżka źródłowa i ścieżka docelowa są takie same ( <xref:System.IO.IOException> ).</span><span class="sxs-lookup"><span data-stu-id="8210e-125">The source path and target path are the same (<xref:System.IO.IOException>).</span></span>

- <span data-ttu-id="8210e-126">`ShowUI`jest ustawiona na, `UIOption.AllDialogs` a użytkownik anuluje operację lub nie można skopiować co najmniej jednego pliku w katalogu ( <xref:System.OperationCanceledException> ).</span><span class="sxs-lookup"><span data-stu-id="8210e-126">`ShowUI` is set to `UIOption.AllDialogs` and the user cancels the operation, or one or more files in the directory cannot be copied (<xref:System.OperationCanceledException>).</span></span>

- <span data-ttu-id="8210e-127">Operacja jest cykliczna ( <xref:System.InvalidOperationException> ).</span><span class="sxs-lookup"><span data-stu-id="8210e-127">The operation is cyclic (<xref:System.InvalidOperationException>).</span></span>

- <span data-ttu-id="8210e-128">Ścieżka zawiera dwukropek (:) (<xref:System.NotSupportedException>).</span><span class="sxs-lookup"><span data-stu-id="8210e-128">The path contains a colon (:) (<xref:System.NotSupportedException>).</span></span>

- <span data-ttu-id="8210e-129">Ścieżka przekracza maksymalną długość zdefiniowaną przez system ( <xref:System.IO.PathTooLongException> ).</span><span class="sxs-lookup"><span data-stu-id="8210e-129">The path exceeds the system-defined maximum length (<xref:System.IO.PathTooLongException>).</span></span>

- <span data-ttu-id="8210e-130">Nazwa pliku lub folderu w ścieżce zawiera dwukropek (:) lub ma nieprawidłowy format ( <xref:System.NotSupportedException> ).</span><span class="sxs-lookup"><span data-stu-id="8210e-130">A file or folder name in the path contains a colon (:) or is in an invalid format (<xref:System.NotSupportedException>).</span></span>

- <span data-ttu-id="8210e-131">Użytkownik nie ma wystarczających uprawnień do wyświetlania ścieżki ( <xref:System.Security.SecurityException> ).</span><span class="sxs-lookup"><span data-stu-id="8210e-131">The user lacks necessary permissions to view the path (<xref:System.Security.SecurityException>).</span></span>

- <span data-ttu-id="8210e-132">Plik docelowy istnieje, ale nie można uzyskać do niego dostępu ( <xref:System.UnauthorizedAccessException> ).</span><span class="sxs-lookup"><span data-stu-id="8210e-132">A destination file exists but cannot be accessed (<xref:System.UnauthorizedAccessException>).</span></span>

## <a name="see-also"></a><span data-ttu-id="8210e-133">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8210e-133">See also</span></span>

- <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyDirectory%2A>
- [<span data-ttu-id="8210e-134">Instrukcje: Znajdowanie podkatalogów z określonym wzorcem</span><span class="sxs-lookup"><span data-stu-id="8210e-134">How to: Find Subdirectories with a Specific Pattern</span></span>](how-to-find-subdirectories-with-a-specific-pattern.md)
- [<span data-ttu-id="8210e-135">Instrukcje: Pobieranie kolekcji plików z katalogu</span><span class="sxs-lookup"><span data-stu-id="8210e-135">How to: Get the Collection of Files in a Directory</span></span>](how-to-get-the-collection-of-files-in-a-directory.md)
