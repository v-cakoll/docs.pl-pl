---
title: 'Rozwiązywanie problemów: odczytywanie z plików tekstowych i zapisywanie do nich'
ms.date: 07/20/2015
helpviewer_keywords:
- troubleshooting file I/O
- writing text to files [Visual Basic], troubleshooting
- troubleshooting Visual Basic, text files
- I/O [Visual Basic], troubleshooting text files
- writing to files [Visual Basic], troubleshooting
- reading text files [Visual Basic], troubleshooting
ms.assetid: a8e9b44d-facb-4718-8c0f-466537171182
ms.openlocfilehash: dbc53ca3cc9ae9b2d14b925f891d0409b2b7debd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "74333797"
---
# <a name="troubleshooting-reading-from-and-writing-to-text-files-visual-basic"></a><span data-ttu-id="f2934-102">Rozwiązywanie problemów: odczytywanie z plików tekstowych i zapisywanie do nich (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f2934-102">Troubleshooting: reading from and writing to text files (Visual Basic)</span></span>

<span data-ttu-id="f2934-103">W tym temacie omówiono typowe problemy występujące podczas pracy z plikami tekstowymi i sugerujemy podejście do każdego z nich.</span><span class="sxs-lookup"><span data-stu-id="f2934-103">This topic discusses common problems encountered when working with text files and suggests an approach to each.</span></span>  
  
## <a name="common-problems"></a><span data-ttu-id="f2934-104">Typowe problemy</span><span class="sxs-lookup"><span data-stu-id="f2934-104">Common problems</span></span>  

 <span data-ttu-id="f2934-105">Najczęstsze problemy występujące podczas pracy z plikami tekstowymi obejmują wyjątki zabezpieczeń, kodowanie plików lub nieprawidłowe ścieżki.</span><span class="sxs-lookup"><span data-stu-id="f2934-105">The most common issues encountered when working with text files include security exceptions, file encodings, or invalid paths.</span></span>  
  
### <a name="security-exceptions"></a><span data-ttu-id="f2934-106">Wyjątki zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="f2934-106">Security exceptions</span></span>  

 <span data-ttu-id="f2934-107">Występuje <xref:System.Security.SecurityException> , gdy wystąpi błąd zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="f2934-107">A <xref:System.Security.SecurityException> is thrown when a security error occurs.</span></span> <span data-ttu-id="f2934-108">Jest to często wynikiem braku potrzebnych uprawnień przez użytkownika, które mogą zostać rozwiązane przez dodanie uprawnień lub praca z plikami w izolowanym magazynie.</span><span class="sxs-lookup"><span data-stu-id="f2934-108">This is often a result of the user lacking necessary permissions, which may be solved by adding permissions or working with files in isolated storage.</span></span>  
  
### <a name="file-encodings"></a><span data-ttu-id="f2934-109">Kodowanie plików</span><span class="sxs-lookup"><span data-stu-id="f2934-109">File encodings</span></span>  

 <span data-ttu-id="f2934-110">Kodowanie plików, znane także jako kodowania znaków, określają sposób reprezentowania znaków podczas przetwarzania tekstu.</span><span class="sxs-lookup"><span data-stu-id="f2934-110">File encodings, also known as character encodings, specify how to represent characters when text processing.</span></span> <span data-ttu-id="f2934-111">Nieoczekiwane znaki w pliku tekstowym mogą wynikać z nieprawidłowego kodowania.</span><span class="sxs-lookup"><span data-stu-id="f2934-111">Unexpected characters in a text file may result from incorrect encoding.</span></span> <span data-ttu-id="f2934-112">W przypadku większości plików jedno kodowanie może być preferowane przez inne warunki języka, które może lub nie może obsłużyć, chociaż standard Unicode jest zazwyczaj preferowany.</span><span class="sxs-lookup"><span data-stu-id="f2934-112">For most files, one encoding may be preferable over another in terms of which language characters it can or cannot handle, although Unicode is usually preferred.</span></span> <span data-ttu-id="f2934-113">Aby uzyskać więcej informacji, zobacz [kodowanie plików](../../../../visual-basic/developing-apps/programming/drives-directories-files/file-encodings.md) i <xref:System.Text.Encoding>.</span><span class="sxs-lookup"><span data-stu-id="f2934-113">For more information, see [File Encodings](../../../../visual-basic/developing-apps/programming/drives-directories-files/file-encodings.md) and <xref:System.Text.Encoding>.</span></span>  
  
### <a name="incorrect-paths"></a><span data-ttu-id="f2934-114">Nieprawidłowe ścieżki</span><span class="sxs-lookup"><span data-stu-id="f2934-114">Incorrect paths</span></span>  

 <span data-ttu-id="f2934-115">Podczas analizowania ścieżek plików, szczególnie ścieżek względnych, można łatwo dostarczać błędne dane.</span><span class="sxs-lookup"><span data-stu-id="f2934-115">When parsing file paths, particularly relative paths, it is easy to supply the wrong data.</span></span> <span data-ttu-id="f2934-116">Wiele problemów można poprawić, upewniając się, że jest dostarczana poprawna ścieżka.</span><span class="sxs-lookup"><span data-stu-id="f2934-116">Many problems can be corrected by making sure you are supplying the correct path.</span></span> <span data-ttu-id="f2934-117">Aby uzyskać więcej informacji, zobacz [How to: Parse File Paths](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-parse-file-paths.md).</span><span class="sxs-lookup"><span data-stu-id="f2934-117">For more information, see [How to: Parse File Paths](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-parse-file-paths.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f2934-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f2934-118">See also</span></span>

- <xref:Microsoft.VisualBasic.FileIO.FileSystem>
- [<span data-ttu-id="f2934-119">Odczyt z plików</span><span class="sxs-lookup"><span data-stu-id="f2934-119">Reading from Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/reading-from-files.md)
- [<span data-ttu-id="f2934-120">Zapisywanie w plikach</span><span class="sxs-lookup"><span data-stu-id="f2934-120">Writing to Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/writing-to-files.md)
- [<span data-ttu-id="f2934-121">Analizowanie plików tekstowych za pomocą obiektu TextFieldParser</span><span class="sxs-lookup"><span data-stu-id="f2934-121">Parsing Text Files with the TextFieldParser Object</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/parsing-text-files-with-the-textfieldparser-object.md)
