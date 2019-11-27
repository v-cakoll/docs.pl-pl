---
title: 'Porady: zapis w plikach binarnych'
ms.date: 07/20/2015
helpviewer_keywords:
- files [Visual Basic], binary access
- WriteAllBytes method [Visual Basic]
- binary files [Visual Basic], writing in Visual Basic
ms.assetid: 59fae125-de5b-4c96-883c-209f4a55112c
ms.openlocfilehash: 72d019f5f49868bd84d0507535e8ebc547b50e25
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74334428"
---
# <a name="how-to-write-to-binary-files-in-visual-basic"></a><span data-ttu-id="87df2-102">Porady: zapis w plikach binarnych w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="87df2-102">How to: Write to Binary Files in Visual Basic</span></span>

<span data-ttu-id="87df2-103">Metoda <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllBytes%2A> zapisuje dane do pliku binarnego.</span><span class="sxs-lookup"><span data-stu-id="87df2-103">The <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllBytes%2A> method writes data to a binary file.</span></span> <span data-ttu-id="87df2-104">Jeśli parametr `append` jest `True`, spowoduje to dołączenie danych do pliku; w przeciwnym razie dane w pliku są zastępowane.</span><span class="sxs-lookup"><span data-stu-id="87df2-104">If the `append` parameter is `True`, it will append the data to the file; otherwise data in the file is overwritten.</span></span>

<span data-ttu-id="87df2-105">Jeśli określona ścieżka wykluczająca nazwę pliku jest nieprawidłowa, zostanie zgłoszony wyjątek <xref:System.IO.DirectoryNotFoundException>.</span><span class="sxs-lookup"><span data-stu-id="87df2-105">If the specified path excluding the file name is not valid, a <xref:System.IO.DirectoryNotFoundException> exception will be thrown.</span></span> <span data-ttu-id="87df2-106">Jeśli ścieżka jest prawidłowa, ale plik nie istnieje, plik zostanie utworzony.</span><span class="sxs-lookup"><span data-stu-id="87df2-106">If the path is valid but the file does not exist, the file will be created.</span></span>

## <a name="to-write-to-a-binary-file"></a><span data-ttu-id="87df2-107">Aby zapisać w pliku binarnym</span><span class="sxs-lookup"><span data-stu-id="87df2-107">To write to a binary file</span></span>

<span data-ttu-id="87df2-108">Użyj metody `WriteAllBytes`, podając ścieżkę i nazwę pliku oraz liczbę bajtów do zapisania.</span><span class="sxs-lookup"><span data-stu-id="87df2-108">Use the `WriteAllBytes` method, supplying the file path and name and the bytes to be written.</span></span> <span data-ttu-id="87df2-109">Ten przykład dołącza tablicę danych `CustomerData` do pliku o nazwie `CollectedData.dat`.</span><span class="sxs-lookup"><span data-stu-id="87df2-109">This example appends the data array `CustomerData` to the file named `CollectedData.dat`.</span></span>

[!code-vb[VbVbcnMyFileSystem#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#27)]

## <a name="robust-programming"></a><span data-ttu-id="87df2-110">Skuteczne programowanie</span><span class="sxs-lookup"><span data-stu-id="87df2-110">Robust Programming</span></span>

<span data-ttu-id="87df2-111">Następujące warunki mogą utworzyć wyjątek:</span><span class="sxs-lookup"><span data-stu-id="87df2-111">The following conditions may create an exception:</span></span>

- <span data-ttu-id="87df2-112">Ścieżka jest nieprawidłowa z jednego z następujących powodów: jest to ciąg o zerowej długości; zawiera tylko białe znaki; lub zawiera nieprawidłowe znaki.</span><span class="sxs-lookup"><span data-stu-id="87df2-112">The path is not valid for one of the following reasons: it is a zero-length string; it contains only white space; or it contains invalid characters.</span></span> <span data-ttu-id="87df2-113">(<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="87df2-113">(<xref:System.ArgumentException>).</span></span>

- <span data-ttu-id="87df2-114">Ścieżka jest nieprawidłowa, ponieważ jest `Nothing` (<xref:System.ArgumentNullException>).</span><span class="sxs-lookup"><span data-stu-id="87df2-114">The path is not valid because it is `Nothing` (<xref:System.ArgumentNullException>).</span></span>

- <span data-ttu-id="87df2-115">`File` wskazuje ścieżkę, która nie istnieje (<xref:System.IO.FileNotFoundException> lub <xref:System.IO.DirectoryNotFoundException>).</span><span class="sxs-lookup"><span data-stu-id="87df2-115">`File` points to a path that does not exist (<xref:System.IO.FileNotFoundException> or <xref:System.IO.DirectoryNotFoundException>).</span></span>

- <span data-ttu-id="87df2-116">Plik jest używany przez inny proces lub wystąpił błąd we/wy (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="87df2-116">The file is in use by another process, or an I/O error occurs (<xref:System.IO.IOException>).</span></span>

- <span data-ttu-id="87df2-117">Ścieżka przekracza maksymalną długość zdefiniowaną przez system (<xref:System.IO.PathTooLongException>).</span><span class="sxs-lookup"><span data-stu-id="87df2-117">The path exceeds the system-defined maximum length (<xref:System.IO.PathTooLongException>).</span></span>

- <span data-ttu-id="87df2-118">Nazwa pliku lub katalogu w ścieżce zawiera dwukropek (:) lub ma nieprawidłowy format (<xref:System.NotSupportedException>).</span><span class="sxs-lookup"><span data-stu-id="87df2-118">A file or directory name in the path contains a colon (:) or is in an invalid format (<xref:System.NotSupportedException>).</span></span>

- <span data-ttu-id="87df2-119">Użytkownik nie ma wystarczających uprawnień do wyświetlania ścieżki (<xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="87df2-119">The user lacks necessary permissions to view the path (<xref:System.Security.SecurityException>).</span></span>

## <a name="see-also"></a><span data-ttu-id="87df2-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="87df2-120">See also</span></span>

- <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllBytes%2A>
- [<span data-ttu-id="87df2-121">Instrukcje: zapisywanie tekstu w plikach</span><span class="sxs-lookup"><span data-stu-id="87df2-121">How to: Write Text to Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-write-text-to-files.md)
