---
title: 'Rozwiązywanie problemów: odczytywanie z oraz zapisywanie w plikach tekstowych (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- troubleshooting file I/O
- writing text to files [Visual Basic], troubleshooting
- troubleshooting Visual Basic, text files
- I/O [Visual Basic], troubleshooting text files
- writing to files [Visual Basic], troubleshooting
- reading text files [Visual Basic], troubleshooting
ms.assetid: a8e9b44d-facb-4718-8c0f-466537171182
ms.openlocfilehash: 90a04d9de2ac77c28a92d99e1fe118a1f8ecf448
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "58831790"
---
# <a name="troubleshooting-reading-from-and-writing-to-text-files-visual-basic"></a><span data-ttu-id="e35a5-102">Rozwiązywanie problemów: odczytywanie z oraz zapisywanie w plikach tekstowych (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e35a5-102">Troubleshooting: reading from and writing to text files (Visual Basic)</span></span>
<span data-ttu-id="e35a5-103">W tym temacie omówiono typowe problemy występujące podczas pracy z tekstem pliki i sugeruje podejścia do każdego.</span><span class="sxs-lookup"><span data-stu-id="e35a5-103">This topic discusses common problems encountered when working with text files and suggests an approach to each.</span></span>  
  
## <a name="common-problems"></a><span data-ttu-id="e35a5-104">Typowe problemy</span><span class="sxs-lookup"><span data-stu-id="e35a5-104">Common problems</span></span>  
 <span data-ttu-id="e35a5-105">Typowe problemy występujące podczas pracy z plikami tekstowymi obejmują wyjątki zabezpieczeń, kodowanie pliku lub nieprawidłowe ścieżki.</span><span class="sxs-lookup"><span data-stu-id="e35a5-105">The most common issues encountered when working with text files include security exceptions, file encodings, or invalid paths.</span></span>  
  
### <a name="security-exceptions"></a><span data-ttu-id="e35a5-106">Wyjątki zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="e35a5-106">Security exceptions</span></span>  
 <span data-ttu-id="e35a5-107">Element <xref:System.Security.SecurityException> jest zgłaszany, gdy wystąpi błąd zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="e35a5-107">A <xref:System.Security.SecurityException> is thrown when a security error occurs.</span></span> <span data-ttu-id="e35a5-108">Często jest to wynik użytkownika, których nie ma wymaganych uprawnień, które mogą zostać rozwiązane przez dodanie uprawnień lub Praca z plikami w wydzielonej pamięci masowej.</span><span class="sxs-lookup"><span data-stu-id="e35a5-108">This is often a result of the user lacking necessary permissions, which may be solved by adding permissions or working with files in isolated storage.</span></span>  
  
### <a name="file-encodings"></a><span data-ttu-id="e35a5-109">Kodowanie pliku</span><span class="sxs-lookup"><span data-stu-id="e35a5-109">File encodings</span></span>  
 <span data-ttu-id="e35a5-110">Określ kodowanie pliku, znany także jako kodowanie znaków do reprezentowania znaków, kiedy przetwarzanie tekstu.</span><span class="sxs-lookup"><span data-stu-id="e35a5-110">File encodings, also known as character encodings, specify how to represent characters when text processing.</span></span> <span data-ttu-id="e35a5-111">Nieoczekiwane znaki w pliku tekstowym mogą wynikać z Nieprawidłowe kodowanie.</span><span class="sxs-lookup"><span data-stu-id="e35a5-111">Unexpected characters in a text file may result from incorrect encoding.</span></span> <span data-ttu-id="e35a5-112">Dla większości plików jednego formatu kodowania może być preferowane zamiast innego pod względem znaki języków, które mogą lub nie może obsłużyć, chociaż Unicode jest zwykle preferowany.</span><span class="sxs-lookup"><span data-stu-id="e35a5-112">For most files, one encoding may be preferable over another in terms of which language characters it can or cannot handle, although Unicode is usually preferred.</span></span> <span data-ttu-id="e35a5-113">Aby uzyskać więcej informacji, zobacz [kodowanie pliku](../../../../visual-basic/developing-apps/programming/drives-directories-files/file-encodings.md) i <xref:System.Text.Encoding>.</span><span class="sxs-lookup"><span data-stu-id="e35a5-113">For more information, see [File Encodings](../../../../visual-basic/developing-apps/programming/drives-directories-files/file-encodings.md) and <xref:System.Text.Encoding>.</span></span>  
  
### <a name="incorrect-paths"></a><span data-ttu-id="e35a5-114">Nieprawidłowe ścieżki</span><span class="sxs-lookup"><span data-stu-id="e35a5-114">Incorrect paths</span></span>  
 <span data-ttu-id="e35a5-115">Podczas analizowania ścieżki plików, szczególnie względnej ścieżki jest łatwe przekazywanie niewłaściwej danych.</span><span class="sxs-lookup"><span data-stu-id="e35a5-115">When parsing file paths, particularly relative paths, it is easy to supply the wrong data.</span></span> <span data-ttu-id="e35a5-116">Można rozwiązać wiele problemów, upewniając się, że są podawania poprawnej ścieżki.</span><span class="sxs-lookup"><span data-stu-id="e35a5-116">Many problems can be corrected by making sure you are supplying the correct path.</span></span> <span data-ttu-id="e35a5-117">Aby uzyskać więcej informacji, zobacz [jak: Analizowanie ścieżek pliku](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-parse-file-paths.md).</span><span class="sxs-lookup"><span data-stu-id="e35a5-117">For more information, see [How to: Parse File Paths](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-parse-file-paths.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e35a5-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e35a5-118">See also</span></span>

- <xref:Microsoft.VisualBasic.FileIO.FileSystem>
- [<span data-ttu-id="e35a5-119">Odczyt z plików</span><span class="sxs-lookup"><span data-stu-id="e35a5-119">Reading from Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/reading-from-files.md)
- [<span data-ttu-id="e35a5-120">Zapisywanie w plikach</span><span class="sxs-lookup"><span data-stu-id="e35a5-120">Writing to Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/writing-to-files.md)
- [<span data-ttu-id="e35a5-121">Analizowanie plików tekstowych za pomocą obiektu TextFieldParser</span><span class="sxs-lookup"><span data-stu-id="e35a5-121">Parsing Text Files with the TextFieldParser Object</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/parsing-text-files-with-the-textfieldparser-object.md)
