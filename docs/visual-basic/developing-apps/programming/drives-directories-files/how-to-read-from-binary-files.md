---
title: 'Instrukcje: Odczyt z plików binarnych'
ms.date: 07/20/2015
helpviewer_keywords:
- binary files [Visual Basic], reading from
- I/O [Visual Basic], reading from binary files
- ReadAllBytes method [Visual Basic], reading from binary files
- My.Computer.FileSystem object, reading from binary files
ms.assetid: d2b1269e-24b6-42e0-9414-ae708db282d8
ms.openlocfilehash: 3b4108034b86d99143fff6943e68ca0077ebd21b
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84359932"
---
# <a name="how-to-read-from-binary-files-in-visual-basic"></a><span data-ttu-id="fef5f-102">Porady: odczyt z plików binarnych w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="fef5f-102">How to: Read From Binary Files in Visual Basic</span></span>

<span data-ttu-id="fef5f-103">`My.Computer.FileSystem`Obiekt udostępnia `ReadAllBytes` metodę odczytu z plików binarnych.</span><span class="sxs-lookup"><span data-stu-id="fef5f-103">The `My.Computer.FileSystem` object provides the `ReadAllBytes` method for reading from binary files.</span></span>  
  
### <a name="to-read-from-a-binary-file"></a><span data-ttu-id="fef5f-104">Aby odczytywać dane z pliku binarnego</span><span class="sxs-lookup"><span data-stu-id="fef5f-104">To read from a binary file</span></span>  
  
- <span data-ttu-id="fef5f-105">Użyj `ReadAllBytes` metody, która zwraca zawartość pliku jako tablicę bajtów.</span><span class="sxs-lookup"><span data-stu-id="fef5f-105">Use the `ReadAllBytes` method, which returns the contents of a file as a byte array.</span></span> <span data-ttu-id="fef5f-106">Ten przykład odczytuje z pliku `C:/Documents and Settings/selfportrait.jpg` .</span><span class="sxs-lookup"><span data-stu-id="fef5f-106">This example reads from the file `C:/Documents and Settings/selfportrait.jpg`.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#78](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#78)]  
  
- <span data-ttu-id="fef5f-107">W przypadku dużych plików binarnych można użyć <xref:System.IO.FileStream.Read%2A> metody <xref:System.IO.FileStream> obiektu do odczytu z pliku tylko określonej wartości w danym momencie.</span><span class="sxs-lookup"><span data-stu-id="fef5f-107">For large binary files, you can use the <xref:System.IO.FileStream.Read%2A> method of the <xref:System.IO.FileStream> object to read from the file only a specified amount at a time.</span></span> <span data-ttu-id="fef5f-108">Następnie można ograniczyć ilość pliku do załadowania do pamięci dla każdej operacji odczytu.</span><span class="sxs-lookup"><span data-stu-id="fef5f-108">You can then limit how much of the file is loaded into memory for each read operation.</span></span> <span data-ttu-id="fef5f-109">Poniższy przykład kodu kopiuje plik i umożliwia obiektowi wywołującemu określenie, jaka część pliku jest odczytywana do pamięci na potrzeby operacji odczytu.</span><span class="sxs-lookup"><span data-stu-id="fef5f-109">The following code example copies a file and allows the caller to specify how much of the file is read into memory per read operation.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#91](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#91)]  
  
## <a name="robust-programming"></a><span data-ttu-id="fef5f-110">Niezawodne programowanie</span><span class="sxs-lookup"><span data-stu-id="fef5f-110">Robust Programming</span></span>  

 <span data-ttu-id="fef5f-111">Następujące warunki mogą spowodować zgłoszenie wyjątku:</span><span class="sxs-lookup"><span data-stu-id="fef5f-111">The following conditions may cause an exception to be thrown:</span></span>  
  
- <span data-ttu-id="fef5f-112">Ścieżka jest nieprawidłowa z jednego z następujących powodów: jest ciągiem o zerowej długości, zawiera tylko biały znak, zawiera nieprawidłowe znaki lub jest ścieżką urządzenia ( <xref:System.ArgumentException> ).</span><span class="sxs-lookup"><span data-stu-id="fef5f-112">The path is not valid for one of the following reasons: it is a zero-length string, it contains only white space, it contains invalid characters, or it is a device path (<xref:System.ArgumentException>).</span></span>  
  
- <span data-ttu-id="fef5f-113">Ścieżka jest nieprawidłowa, ponieważ jest `Nothing` ( <xref:System.ArgumentNullException> ).</span><span class="sxs-lookup"><span data-stu-id="fef5f-113">The path is not valid because it is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
- <span data-ttu-id="fef5f-114">Plik nie istnieje ( <xref:System.IO.FileNotFoundException> ).</span><span class="sxs-lookup"><span data-stu-id="fef5f-114">The file does not exist (<xref:System.IO.FileNotFoundException>).</span></span>  
  
- <span data-ttu-id="fef5f-115">Plik jest używany przez inny proces lub wystąpił błąd we/wy ( <xref:System.IO.IOException> ).</span><span class="sxs-lookup"><span data-stu-id="fef5f-115">The file is in use by another process, or an I/O error occurs (<xref:System.IO.IOException>).</span></span>  
  
- <span data-ttu-id="fef5f-116">Ścieżka przekracza maksymalną długość zdefiniowaną przez system ( <xref:System.IO.PathTooLongException> ).</span><span class="sxs-lookup"><span data-stu-id="fef5f-116">The path exceeds the system-defined maximum length (<xref:System.IO.PathTooLongException>).</span></span>  
  
- <span data-ttu-id="fef5f-117">Nazwa pliku lub katalogu w ścieżce zawiera dwukropek (:) lub ma nieprawidłowy format ( <xref:System.NotSupportedException> ).</span><span class="sxs-lookup"><span data-stu-id="fef5f-117">A file or directory name in the path contains a colon (:) or is in an invalid format (<xref:System.NotSupportedException>).</span></span>  
  
- <span data-ttu-id="fef5f-118">Za mało pamięci, aby zapisać ciąg do bufora ( <xref:System.OutOfMemoryException> ).</span><span class="sxs-lookup"><span data-stu-id="fef5f-118">There is not enough memory to write the string to buffer (<xref:System.OutOfMemoryException>).</span></span>  
  
- <span data-ttu-id="fef5f-119">Użytkownik nie ma wystarczających uprawnień do wyświetlania ścieżki ( <xref:System.Security.SecurityException> ).</span><span class="sxs-lookup"><span data-stu-id="fef5f-119">The user lacks necessary permissions to view the path (<xref:System.Security.SecurityException>).</span></span>  
  
 <span data-ttu-id="fef5f-120">Nie należy podejmować decyzji dotyczących zawartości pliku na podstawie rozszerzenia nazwy pliku.</span><span class="sxs-lookup"><span data-stu-id="fef5f-120">Do not make decisions about the contents of the file based on the name of the file.</span></span> <span data-ttu-id="fef5f-121">Na przykład plik Form1. vb nie może być plikiem źródłowym Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="fef5f-121">For example, the file Form1.vb may not be a Visual Basic source file.</span></span>  
  
 <span data-ttu-id="fef5f-122">Sprawdź wszystkie dane wejściowe, zanim użyjesz danych w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="fef5f-122">Verify all inputs before using the data in your application.</span></span> <span data-ttu-id="fef5f-123">Zawartość pliku może się różnić od oczekiwanej i metody odczytu z pliku nie zadziałają.</span><span class="sxs-lookup"><span data-stu-id="fef5f-123">The contents of the file may not be what is expected, and methods to read from the file may fail.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fef5f-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="fef5f-124">See also</span></span>

- <xref:Microsoft.VisualBasic.FileIO.FileSystem.ReadAllBytes%2A>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllBytes%2A>
- [<span data-ttu-id="fef5f-125">Odczyt z plików</span><span class="sxs-lookup"><span data-stu-id="fef5f-125">Reading from Files</span></span>](reading-from-files.md)
- [<span data-ttu-id="fef5f-126">Instrukcje: Odczyt z plików tekstowych w wielu formatach</span><span class="sxs-lookup"><span data-stu-id="fef5f-126">How to: Read From Text Files with Multiple Formats</span></span>](how-to-read-from-text-files-with-multiple-formats.md)
- [<span data-ttu-id="fef5f-127">Zapisywanie danych w schowku i odczytywanie ich z niego</span><span class="sxs-lookup"><span data-stu-id="fef5f-127">Storing Data to and Reading from the Clipboard</span></span>](../computer-resources/storing-data-to-and-reading-from-the-clipboard.md)
