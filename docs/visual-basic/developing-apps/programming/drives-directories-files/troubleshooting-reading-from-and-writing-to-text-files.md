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
ms.openlocfilehash: 8af4160d09f39f2622a007aef793173d614a8b44
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84406628"
---
# <a name="troubleshooting-reading-from-and-writing-to-text-files-visual-basic"></a><span data-ttu-id="c8945-102">Rozwiązywanie problemów: odczytywanie z plików tekstowych i zapisywanie do nich (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c8945-102">Troubleshooting: reading from and writing to text files (Visual Basic)</span></span>

<span data-ttu-id="c8945-103">W tym temacie omówiono typowe problemy występujące podczas pracy z plikami tekstowymi i sugerujemy podejście do każdego z nich.</span><span class="sxs-lookup"><span data-stu-id="c8945-103">This topic discusses common problems encountered when working with text files and suggests an approach to each.</span></span>  
  
## <a name="common-problems"></a><span data-ttu-id="c8945-104">Typowe problemy</span><span class="sxs-lookup"><span data-stu-id="c8945-104">Common problems</span></span>  

 <span data-ttu-id="c8945-105">Najczęstsze problemy występujące podczas pracy z plikami tekstowymi obejmują wyjątki zabezpieczeń, kodowanie plików lub nieprawidłowe ścieżki.</span><span class="sxs-lookup"><span data-stu-id="c8945-105">The most common issues encountered when working with text files include security exceptions, file encodings, or invalid paths.</span></span>  
  
### <a name="security-exceptions"></a><span data-ttu-id="c8945-106">Wyjątki zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="c8945-106">Security exceptions</span></span>  

 <span data-ttu-id="c8945-107"><xref:System.Security.SecurityException>Występuje, gdy wystąpi błąd zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="c8945-107">A <xref:System.Security.SecurityException> is thrown when a security error occurs.</span></span> <span data-ttu-id="c8945-108">Jest to często wynikiem braku potrzebnych uprawnień przez użytkownika, które mogą zostać rozwiązane przez dodanie uprawnień lub praca z plikami w izolowanym magazynie.</span><span class="sxs-lookup"><span data-stu-id="c8945-108">This is often a result of the user lacking necessary permissions, which may be solved by adding permissions or working with files in isolated storage.</span></span>  
  
### <a name="file-encodings"></a><span data-ttu-id="c8945-109">Kodowanie plików</span><span class="sxs-lookup"><span data-stu-id="c8945-109">File encodings</span></span>  

 <span data-ttu-id="c8945-110">Kodowanie plików, znane także jako kodowania znaków, określają sposób reprezentowania znaków podczas przetwarzania tekstu.</span><span class="sxs-lookup"><span data-stu-id="c8945-110">File encodings, also known as character encodings, specify how to represent characters when text processing.</span></span> <span data-ttu-id="c8945-111">Nieoczekiwane znaki w pliku tekstowym mogą wynikać z nieprawidłowego kodowania.</span><span class="sxs-lookup"><span data-stu-id="c8945-111">Unexpected characters in a text file may result from incorrect encoding.</span></span> <span data-ttu-id="c8945-112">W przypadku większości plików jedno kodowanie może być preferowane przez inne warunki języka, które może lub nie może obsłużyć, chociaż standard Unicode jest zazwyczaj preferowany.</span><span class="sxs-lookup"><span data-stu-id="c8945-112">For most files, one encoding may be preferable over another in terms of which language characters it can or cannot handle, although Unicode is usually preferred.</span></span> <span data-ttu-id="c8945-113">Aby uzyskać więcej informacji, zobacz [kodowanie plików](file-encodings.md) i <xref:System.Text.Encoding> .</span><span class="sxs-lookup"><span data-stu-id="c8945-113">For more information, see [File Encodings](file-encodings.md) and <xref:System.Text.Encoding>.</span></span>  
  
### <a name="incorrect-paths"></a><span data-ttu-id="c8945-114">Nieprawidłowe ścieżki</span><span class="sxs-lookup"><span data-stu-id="c8945-114">Incorrect paths</span></span>  

 <span data-ttu-id="c8945-115">Podczas analizowania ścieżek plików, szczególnie ścieżek względnych, można łatwo dostarczać błędne dane.</span><span class="sxs-lookup"><span data-stu-id="c8945-115">When parsing file paths, particularly relative paths, it is easy to supply the wrong data.</span></span> <span data-ttu-id="c8945-116">Wiele problemów można poprawić, upewniając się, że jest dostarczana poprawna ścieżka.</span><span class="sxs-lookup"><span data-stu-id="c8945-116">Many problems can be corrected by making sure you are supplying the correct path.</span></span> <span data-ttu-id="c8945-117">Aby uzyskać więcej informacji, zobacz [How to: Parse File Paths](how-to-parse-file-paths.md).</span><span class="sxs-lookup"><span data-stu-id="c8945-117">For more information, see [How to: Parse File Paths](how-to-parse-file-paths.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c8945-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c8945-118">See also</span></span>

- <xref:Microsoft.VisualBasic.FileIO.FileSystem>
- [<span data-ttu-id="c8945-119">Odczyt z plików</span><span class="sxs-lookup"><span data-stu-id="c8945-119">Reading from Files</span></span>](reading-from-files.md)
- [<span data-ttu-id="c8945-120">Zapisywanie w plikach</span><span class="sxs-lookup"><span data-stu-id="c8945-120">Writing to Files</span></span>](writing-to-files.md)
- [<span data-ttu-id="c8945-121">Analizowanie plików tekstowych za pomocą obiektu TextFieldParser</span><span class="sxs-lookup"><span data-stu-id="c8945-121">Parsing Text Files with the TextFieldParser Object</span></span>](parsing-text-files-with-the-textfieldparser-object.md)
