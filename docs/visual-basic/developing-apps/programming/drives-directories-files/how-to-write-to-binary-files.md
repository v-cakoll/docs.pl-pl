---
title: 'Instrukcje: Zapisz w plikach binarnych w Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- files [Visual Basic], binary access
- WriteAllBytes method [Visual Basic]
- binary files [Visual Basic], writing in Visual Basic
ms.assetid: 59fae125-de5b-4c96-883c-209f4a55112c
ms.openlocfilehash: ab42fa50aaf39397ac51db8a4cc3a3b00f6ce878
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71039413"
---
# <a name="how-to-write-to-binary-files-in-visual-basic"></a><span data-ttu-id="41bfe-102">Instrukcje: Zapisz w plikach binarnych w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="41bfe-102">How to: Write to Binary Files in Visual Basic</span></span>

<span data-ttu-id="41bfe-103"><xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllBytes%2A> Metoda zapisuje dane do pliku binarnego.</span><span class="sxs-lookup"><span data-stu-id="41bfe-103">The <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllBytes%2A> method writes data to a binary file.</span></span> <span data-ttu-id="41bfe-104">Jeśli parametr ma `True`wartość, dołączy dane do pliku; w przeciwnym razie dane w pliku są zastępowane. `append`</span><span class="sxs-lookup"><span data-stu-id="41bfe-104">If the `append` parameter is `True`, it will append the data to the file; otherwise data in the file is overwritten.</span></span>

<span data-ttu-id="41bfe-105">Jeśli określona ścieżka wykluczająca nazwę pliku jest nieprawidłowa, <xref:System.IO.DirectoryNotFoundException> zostanie zgłoszony wyjątek.</span><span class="sxs-lookup"><span data-stu-id="41bfe-105">If the specified path excluding the file name is not valid, a <xref:System.IO.DirectoryNotFoundException> exception will be thrown.</span></span> <span data-ttu-id="41bfe-106">Jeśli ścieżka jest prawidłowa, ale plik nie istnieje, plik zostanie utworzony.</span><span class="sxs-lookup"><span data-stu-id="41bfe-106">If the path is valid but the file does not exist, the file will be created.</span></span>

## <a name="to-write-to-a-binary-file"></a><span data-ttu-id="41bfe-107">Aby zapisać w pliku binarnym</span><span class="sxs-lookup"><span data-stu-id="41bfe-107">To write to a binary file</span></span>

<span data-ttu-id="41bfe-108">`WriteAllBytes` Użyj metody, podając ścieżkę i nazwę pliku oraz liczbę bajtów do zapisania.</span><span class="sxs-lookup"><span data-stu-id="41bfe-108">Use the `WriteAllBytes` method, supplying the file path and name and the bytes to be written.</span></span> <span data-ttu-id="41bfe-109">Ten przykład dołącza tablicę `CustomerData` danych do pliku o nazwie. `CollectedData.dat`</span><span class="sxs-lookup"><span data-stu-id="41bfe-109">This example appends the data array `CustomerData` to the file named `CollectedData.dat`.</span></span>

[!code-vb[VbVbcnMyFileSystem#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#27)]

## <a name="robust-programming"></a><span data-ttu-id="41bfe-110">Niezawodne programowanie</span><span class="sxs-lookup"><span data-stu-id="41bfe-110">Robust Programming</span></span>

<span data-ttu-id="41bfe-111">Następujące warunki mogą utworzyć wyjątek:</span><span class="sxs-lookup"><span data-stu-id="41bfe-111">The following conditions may create an exception:</span></span>

- <span data-ttu-id="41bfe-112">Ścieżka jest nieprawidłowa z jednego z następujących powodów: jest to ciąg o zerowej długości; zawiera tylko białe znaki; lub zawiera nieprawidłowe znaki.</span><span class="sxs-lookup"><span data-stu-id="41bfe-112">The path is not valid for one of the following reasons: it is a zero-length string; it contains only white space; or it contains invalid characters.</span></span> <span data-ttu-id="41bfe-113">(<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="41bfe-113">(<xref:System.ArgumentException>).</span></span>

- <span data-ttu-id="41bfe-114">Ścieżka jest nieprawidłowa, ponieważ jest `Nothing` (<xref:System.ArgumentNullException>).</span><span class="sxs-lookup"><span data-stu-id="41bfe-114">The path is not valid because it is `Nothing` (<xref:System.ArgumentNullException>).</span></span>

- <span data-ttu-id="41bfe-115">`File`wskazuje ścieżkę, która nie istnieje (<xref:System.IO.FileNotFoundException> lub <xref:System.IO.DirectoryNotFoundException>).</span><span class="sxs-lookup"><span data-stu-id="41bfe-115">`File` points to a path that does not exist (<xref:System.IO.FileNotFoundException> or <xref:System.IO.DirectoryNotFoundException>).</span></span>

- <span data-ttu-id="41bfe-116">Plik jest używany przez inny proces lub wystąpił błąd we/wy (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="41bfe-116">The file is in use by another process, or an I/O error occurs (<xref:System.IO.IOException>).</span></span>

- <span data-ttu-id="41bfe-117">Ścieżka przekracza maksymalną długość zdefiniowaną przez system (<xref:System.IO.PathTooLongException>).</span><span class="sxs-lookup"><span data-stu-id="41bfe-117">The path exceeds the system-defined maximum length (<xref:System.IO.PathTooLongException>).</span></span>

- <span data-ttu-id="41bfe-118">Nazwa pliku lub katalogu w ścieżce zawiera dwukropek (:) lub ma nieprawidłowy format (<xref:System.NotSupportedException>).</span><span class="sxs-lookup"><span data-stu-id="41bfe-118">A file or directory name in the path contains a colon (:) or is in an invalid format (<xref:System.NotSupportedException>).</span></span>

- <span data-ttu-id="41bfe-119">Użytkownik nie ma wystarczających uprawnień do wyświetlania ścieżki (<xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="41bfe-119">The user lacks necessary permissions to view the path (<xref:System.Security.SecurityException>).</span></span>

## <a name="see-also"></a><span data-ttu-id="41bfe-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="41bfe-120">See also</span></span>

- <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllBytes%2A>
- [<span data-ttu-id="41bfe-121">Instrukcje: Zapisz tekst do plików</span><span class="sxs-lookup"><span data-stu-id="41bfe-121">How to: Write Text to Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-write-text-to-files.md)
