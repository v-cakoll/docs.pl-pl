---
title: Kodowanie pliku (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- character encodings
- files [Visual Basic], encoding
- Unicode, file encoding
- file encoding
ms.assetid: ea2c5f5f-bbb1-4150-9928-b9951fa6bc57
ms.openlocfilehash: c22e8046a8b88890f25bc6b671825eb6d68ec6b8
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2019
ms.locfileid: "58814006"
---
# <a name="file-encodings-visual-basic"></a><span data-ttu-id="3d311-102">Kodowanie pliku (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3d311-102">File Encodings (Visual Basic)</span></span>
<span data-ttu-id="3d311-103">Określ kodowanie pliku, znany także jako kodowanie znaków do reprezentowania znaków, kiedy przetwarzanie tekstu.</span><span class="sxs-lookup"><span data-stu-id="3d311-103">File encodings, also known as character encodings, specify how to represent characters when text processing.</span></span> <span data-ttu-id="3d311-104">Jednego formatu kodowania może być preferowane zamiast innego pod względem znaki języków, które mogą lub nie może obsłużyć, mimo że Unicode jest zwykle preferowany.</span><span class="sxs-lookup"><span data-stu-id="3d311-104">One encoding may be preferable over another in terms of which language characters it can or cannot handle, although Unicode is usually preferred.</span></span>  
  
 <span data-ttu-id="3d311-105">Gdy odczytujemy ze zmiennej czy zapisywanie w plikach, nieprawidłowo dopasowania kodowanie pliku może spowodować wyjątków lub niepoprawne wyniki.</span><span class="sxs-lookup"><span data-stu-id="3d311-105">When reading from or writing to files, improperly matching file encodings may result in exceptions or incorrect results.</span></span>  
  
## <a name="types-of-encodings"></a><span data-ttu-id="3d311-106">Typy kodowania</span><span class="sxs-lookup"><span data-stu-id="3d311-106">Types of Encodings</span></span>  
 <span data-ttu-id="3d311-107">Unicode jest preferowaną metodę kodowania, podczas pracy z plikami.</span><span class="sxs-lookup"><span data-stu-id="3d311-107">Unicode is the preferred encoding when working with files.</span></span> <span data-ttu-id="3d311-108">Unicode jest na całym świecie standard kodowania znaków, który używa wartości 16-bitowego kodu, który reprezentuje wszystkie znaki, które są stosowane w nowoczesnych obliczeń, w tym techniczne symboli i znaków specjalnych, używane podczas publikowania w.</span><span class="sxs-lookup"><span data-stu-id="3d311-108">Unicode is a worldwide character-encoding standard that uses 16-bit code values to represent all the characters used in modern computing, including technical symbols and special characters used in publishing.</span></span>  
  
 <span data-ttu-id="3d311-109">Wcześniejsze standardy kodowania znaków składa się z zestawów znaków tradycyjnych, takich jak zestawu znaków Windows ANSI, który używa wartości 8-bitowego kodu lub kombinacji wartości 8-bitowych, który reprezentuje znaki używane w określonym języku lub regionu geograficznego.</span><span class="sxs-lookup"><span data-stu-id="3d311-109">Previous character-encoding standards consisted of traditional character sets, such as the Windows ANSI character set that uses 8-bit code values, or combinations of 8-bit values, to represent the characters used in a specific language or geographical region.</span></span>  
  
## <a name="encoding-class"></a><span data-ttu-id="3d311-110">Klasa kodowania</span><span class="sxs-lookup"><span data-stu-id="3d311-110">Encoding Class</span></span>  
 <span data-ttu-id="3d311-111"><xref:System.Text.Encoding> Klasa reprezentuje kodowania znaków.</span><span class="sxs-lookup"><span data-stu-id="3d311-111">The <xref:System.Text.Encoding> class represents a character encoding.</span></span> <span data-ttu-id="3d311-112">Ta tabela zawiera typ kodowania dostępne i zawiera opis każdego.</span><span class="sxs-lookup"><span data-stu-id="3d311-112">This table lists the type of encodings available and describes each.</span></span>  
  
|<span data-ttu-id="3d311-113">Nazwa</span><span class="sxs-lookup"><span data-stu-id="3d311-113">Name</span></span>|<span data-ttu-id="3d311-114">Opis</span><span class="sxs-lookup"><span data-stu-id="3d311-114">Description</span></span>|
|---|---|    
|<xref:System.Text.ASCIIEncoding>|<span data-ttu-id="3d311-115">Reprezentuje kodowania znaków ASCII znaków Unicode.</span><span class="sxs-lookup"><span data-stu-id="3d311-115">Represents an ASCII character encoding of Unicode characters.</span></span>|  
|<xref:System.Text.UnicodeEncoding>|<span data-ttu-id="3d311-116">Reprezentuje kodowanie UTF-16 znaków Unicode.</span><span class="sxs-lookup"><span data-stu-id="3d311-116">Represents a UTF-16 encoding of Unicode characters.</span></span>|  
|<xref:System.Text.UTF32Encoding>|<span data-ttu-id="3d311-117">Reprezentuje kodowania UTF-32 znaków Unicode.</span><span class="sxs-lookup"><span data-stu-id="3d311-117">Represents a UTF-32 encoding of Unicode characters.</span></span>|  
|<xref:System.Text.UTF7Encoding>|<span data-ttu-id="3d311-118">Reprezentuje kodowania UTF-7 znaków Unicode.</span><span class="sxs-lookup"><span data-stu-id="3d311-118">Represents a UTF-7 encoding of Unicode characters.</span></span>|  
|<xref:System.Text.UTF8Encoding>|<span data-ttu-id="3d311-119">Reprezentuje kodowania UTF-8 znaków Unicode.</span><span class="sxs-lookup"><span data-stu-id="3d311-119">Represents a UTF-8 encoding of Unicode characters.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="3d311-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3d311-120">See also</span></span>

- [<span data-ttu-id="3d311-121">Odczyt z plików</span><span class="sxs-lookup"><span data-stu-id="3d311-121">Reading from Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/reading-from-files.md)
- [<span data-ttu-id="3d311-122">Zapisywanie w plikach</span><span class="sxs-lookup"><span data-stu-id="3d311-122">Writing to Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/writing-to-files.md)
