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
ms.openlocfilehash: 5650298da99f8bc9a25c7d7ceea11a8a5bf968fb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="troubleshooting-reading-from-and-writing-to-text-files-visual-basic"></a><span data-ttu-id="7347b-102">Rozwiązywanie problemów: odczytywanie z oraz zapisywanie w plikach tekstowych (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7347b-102">Troubleshooting: reading from and writing to text files (Visual Basic)</span></span>
<span data-ttu-id="7347b-103">W tym temacie omówiono typowe problemy występujące podczas pracy z tekstem pliki, a także sugeruje podejście do każdego.</span><span class="sxs-lookup"><span data-stu-id="7347b-103">This topic discusses common problems encountered when working with text files and suggests an approach to each.</span></span>  
  
## <a name="common-problems"></a><span data-ttu-id="7347b-104">Typowe problemy</span><span class="sxs-lookup"><span data-stu-id="7347b-104">Common problems</span></span>  
 <span data-ttu-id="7347b-105">Najczęściej występujących problemów podczas pracy z plikami tekstowymi zawierać wyjątki zabezpieczeń, kodowania pliku lub nieprawidłowa ścieżki.</span><span class="sxs-lookup"><span data-stu-id="7347b-105">The most common issues encountered when working with text files include security exceptions, file encodings, or invalid paths.</span></span>  
  
### <a name="security-exceptions"></a><span data-ttu-id="7347b-106">Wyjątki zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="7347b-106">Security exceptions</span></span>  
 <span data-ttu-id="7347b-107">A <xref:System.Security.SecurityException> jest generowany, gdy wystąpi błąd zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="7347b-107">A <xref:System.Security.SecurityException> is thrown when a security error occurs.</span></span> <span data-ttu-id="7347b-108">Często jest to wynik użytkownika, których nie ma wystarczających uprawnień, które mogą zostać rozwiązane przez dodanie uprawnień lub Praca z plikami w magazynie izolowanym.</span><span class="sxs-lookup"><span data-stu-id="7347b-108">This is often a result of the user lacking necessary permissions, which may be solved by adding permissions or working with files in isolated storage.</span></span>  
  
### <a name="file-encodings"></a><span data-ttu-id="7347b-109">Kodowanie pliku</span><span class="sxs-lookup"><span data-stu-id="7347b-109">File encodings</span></span>  
 <span data-ttu-id="7347b-110">Kodowanie pliku, znanej także jako kodowanie znaków, określ sposób wyświetlania znaków podczas przetwarzania tekstu.</span><span class="sxs-lookup"><span data-stu-id="7347b-110">File encodings, also known as character encodings, specify how to represent characters when text processing.</span></span> <span data-ttu-id="7347b-111">Nieoczekiwane znaki w pliku tekstowym może spowodować niepoprawne kodowania.</span><span class="sxs-lookup"><span data-stu-id="7347b-111">Unexpected characters in a text file may result from incorrect encoding.</span></span> <span data-ttu-id="7347b-112">Dla większości plików kodowań może być preferowane zamiast innego pod względem znaków języków, które mogą lub nie może obsłużyć, mimo że Unicode jest zwykle preferowany.</span><span class="sxs-lookup"><span data-stu-id="7347b-112">For most files, one encoding may be preferable over another in terms of which language characters it can or cannot handle, although Unicode is usually preferred.</span></span> <span data-ttu-id="7347b-113">Aby uzyskać więcej informacji, zobacz [kodowanie pliku](../../../../visual-basic/developing-apps/programming/drives-directories-files/file-encodings.md) i <xref:System.Text.Encoding>.</span><span class="sxs-lookup"><span data-stu-id="7347b-113">For more information, see [File Encodings](../../../../visual-basic/developing-apps/programming/drives-directories-files/file-encodings.md) and <xref:System.Text.Encoding>.</span></span>  
  
### <a name="incorrect-paths"></a><span data-ttu-id="7347b-114">Nieprawidłowe ścieżki</span><span class="sxs-lookup"><span data-stu-id="7347b-114">Incorrect paths</span></span>  
 <span data-ttu-id="7347b-115">Podczas analizowania ścieżki plików, szczególnie względnych ścieżek, jest bardzo proste dostarczają nieprawidłowe dane.</span><span class="sxs-lookup"><span data-stu-id="7347b-115">When parsing file paths, particularly relative paths, it is easy to supply the wrong data.</span></span> <span data-ttu-id="7347b-116">Wiele problemów można usunąć, upewniając się, że są podając prawidłową ścieżkę.</span><span class="sxs-lookup"><span data-stu-id="7347b-116">Many problems can be corrected by making sure you are supplying the correct path.</span></span> <span data-ttu-id="7347b-117">Aby uzyskać więcej informacji, zobacz [porady: przeanalizować ścieżki plików](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-parse-file-paths.md).</span><span class="sxs-lookup"><span data-stu-id="7347b-117">For more information, see [How to: Parse File Paths](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-parse-file-paths.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7347b-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7347b-118">See also</span></span>  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem>  
 [<span data-ttu-id="7347b-119">Odczyt z plików</span><span class="sxs-lookup"><span data-stu-id="7347b-119">Reading from Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/reading-from-files.md)  
 [<span data-ttu-id="7347b-120">Zapisywanie w plikach</span><span class="sxs-lookup"><span data-stu-id="7347b-120">Writing to Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/writing-to-files.md)  
 [<span data-ttu-id="7347b-121">Analizowanie plików tekstowych za pomocą obiektu TextFieldParser</span><span class="sxs-lookup"><span data-stu-id="7347b-121">Parsing Text Files with the TextFieldParser Object</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/parsing-text-files-with-the-textfieldparser-object.md)
