---
title: Kodowanie pliku (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- character encodings
- files [Visual Basic], encoding
- Unicode, file encoding
- file encoding
ms.assetid: ea2c5f5f-bbb1-4150-9928-b9951fa6bc57
ms.openlocfilehash: 30aba517b3b0fbb5fa5bea48134934b2c2d26e50
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33582289"
---
# <a name="file-encodings-visual-basic"></a><span data-ttu-id="c892e-102">Kodowanie pliku (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c892e-102">File Encodings (Visual Basic)</span></span>
<span data-ttu-id="c892e-103">Kodowanie pliku, znanej także jako kodowanie znaków, określ sposób wyświetlania znaków podczas przetwarzania tekstu.</span><span class="sxs-lookup"><span data-stu-id="c892e-103">File encodings, also known as character encodings, specify how to represent characters when text processing.</span></span> <span data-ttu-id="c892e-104">Kodowań może być preferowana zamiast innego pod względem znaków języków, które mogą lub nie może obsłużyć, mimo że Unicode jest zwykle preferowany.</span><span class="sxs-lookup"><span data-stu-id="c892e-104">One encoding may be preferable over another in terms of which language characters it can or cannot handle, although Unicode is usually preferred.</span></span>  
  
 <span data-ttu-id="c892e-105">Gdy odczyt lub zapis do plików, nieprawidłowo dopasowania kodowanie pliku może spowodować wyjątków lub niepoprawne wyniki.</span><span class="sxs-lookup"><span data-stu-id="c892e-105">When reading from or writing to files, improperly matching file encodings may result in exceptions or incorrect results.</span></span>  
  
## <a name="types-of-encodings"></a><span data-ttu-id="c892e-106">Typy kodowania</span><span class="sxs-lookup"><span data-stu-id="c892e-106">Types of Encodings</span></span>  
 <span data-ttu-id="c892e-107">Unicode jest preferowaną metodę kodowania, podczas pracy z plikami.</span><span class="sxs-lookup"><span data-stu-id="c892e-107">Unicode is the preferred encoding when working with files.</span></span> <span data-ttu-id="c892e-108">Unicode jest na całym świecie standard kodowania znaków, który używa wartości 16-bitowego kodu do reprezentowania wszystkich znaków używany w obliczeniu nowoczesnych tym techniczne symboli i znaków specjalnych w publikowania.</span><span class="sxs-lookup"><span data-stu-id="c892e-108">Unicode is a worldwide character-encoding standard that uses 16-bit code values to represent all the characters used in modern computing, including technical symbols and special characters used in publishing.</span></span>  
  
 <span data-ttu-id="c892e-109">Wcześniejsze standardy kodowania znaków obejmowały zestawów tradycyjnych znaków, takich jak zestaw znaków ANSI systemu Windows, który używa wartości 8-bitowego kodu lub kombinacji wartości 8-bitowych, do reprezentowania znaki używane w określonym języku lub regionu geograficznego.</span><span class="sxs-lookup"><span data-stu-id="c892e-109">Previous character-encoding standards consisted of traditional character sets, such as the Windows ANSI character set that uses 8-bit code values, or combinations of 8-bit values, to represent the characters used in a specific language or geographical region.</span></span>  
  
## <a name="encoding-class"></a><span data-ttu-id="c892e-110">Kodowanie — klasa</span><span class="sxs-lookup"><span data-stu-id="c892e-110">Encoding Class</span></span>  
 <span data-ttu-id="c892e-111"><xref:System.Text.Encoding> Klasa reprezentuje kodowania znaków.</span><span class="sxs-lookup"><span data-stu-id="c892e-111">The <xref:System.Text.Encoding> class represents a character encoding.</span></span> <span data-ttu-id="c892e-112">Ta tabela zawiera typ kodowania dostępny i zawiera opis każdego.</span><span class="sxs-lookup"><span data-stu-id="c892e-112">This table lists the type of encodings available and describes each.</span></span>  
  
|<span data-ttu-id="c892e-113">Nazwa</span><span class="sxs-lookup"><span data-stu-id="c892e-113">Name</span></span>|<span data-ttu-id="c892e-114">Opis</span><span class="sxs-lookup"><span data-stu-id="c892e-114">Description</span></span>|
|---|---|    
|<xref:System.Text.ASCIIEncoding>|<span data-ttu-id="c892e-115">Reprezentuje kodowania znaków ASCII znaków Unicode.</span><span class="sxs-lookup"><span data-stu-id="c892e-115">Represents an ASCII character encoding of Unicode characters.</span></span>|  
|<xref:System.Text.UnicodeEncoding>|<span data-ttu-id="c892e-116">Reprezentuje kodowania UTF-16 znaków Unicode.</span><span class="sxs-lookup"><span data-stu-id="c892e-116">Represents a UTF-16 encoding of Unicode characters.</span></span>|  
|<xref:System.Text.UTF32Encoding>|<span data-ttu-id="c892e-117">Reprezentuje kodowania UTF-32 znaków Unicode.</span><span class="sxs-lookup"><span data-stu-id="c892e-117">Represents a UTF-32 encoding of Unicode characters.</span></span>|  
|<xref:System.Text.UTF7Encoding>|<span data-ttu-id="c892e-118">Reprezentuje kodowania UTF-7 znaków Unicode.</span><span class="sxs-lookup"><span data-stu-id="c892e-118">Represents a UTF-7 encoding of Unicode characters.</span></span>|  
|<xref:System.Text.UTF8Encoding>|<span data-ttu-id="c892e-119">Reprezentuje kodowania UTF-8 znaków Unicode.</span><span class="sxs-lookup"><span data-stu-id="c892e-119">Represents a UTF-8 encoding of Unicode characters.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c892e-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c892e-120">See Also</span></span>  
 [<span data-ttu-id="c892e-121">Odczyt z plików</span><span class="sxs-lookup"><span data-stu-id="c892e-121">Reading from Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/reading-from-files.md)  
 [<span data-ttu-id="c892e-122">Zapisywanie w plikach</span><span class="sxs-lookup"><span data-stu-id="c892e-122">Writing to Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/writing-to-files.md)
