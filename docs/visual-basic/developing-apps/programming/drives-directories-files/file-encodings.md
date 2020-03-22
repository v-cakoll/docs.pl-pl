---
title: Kodowanie pliku
ms.date: 07/20/2015
helpviewer_keywords:
- character encodings
- files [Visual Basic], encoding
- Unicode, file encoding
- file encoding
ms.assetid: ea2c5f5f-bbb1-4150-9928-b9951fa6bc57
ms.openlocfilehash: 52770187568d0ba0f54ec36ee2c3d754a9b4d9a8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "74348890"
---
# <a name="file-encodings-visual-basic"></a><span data-ttu-id="266f3-102">Kodowanie pliku (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="266f3-102">File Encodings (Visual Basic)</span></span>

<span data-ttu-id="266f3-103">Kodowanie plików, znane również jako kodowanie znaków, określa sposób reprezentowania znaków podczas przetwarzania tekstu.</span><span class="sxs-lookup"><span data-stu-id="266f3-103">File encodings, also known as character encodings, specify how to represent characters when text processing.</span></span> <span data-ttu-id="266f3-104">Jedno kodowanie może być korzystne w stosunku do innego pod względem znaków języka, które może lub nie może obsłużyć, chociaż Unicode jest zwykle preferowane.</span><span class="sxs-lookup"><span data-stu-id="266f3-104">One encoding may be preferable over another in terms of which language characters it can or cannot handle, although Unicode is usually preferred.</span></span>

<span data-ttu-id="266f3-105">Podczas odczytywania lub zapisywania do plików nieprawidłowo pasujące kodowania plików może spowodować wyjątki lub nieprawidłowe wyniki.</span><span class="sxs-lookup"><span data-stu-id="266f3-105">When reading from or writing to files, improperly matching file encodings may result in exceptions or incorrect results.</span></span>

## <a name="types-of-encodings"></a><span data-ttu-id="266f3-106">Typy kodowania</span><span class="sxs-lookup"><span data-stu-id="266f3-106">Types of Encodings</span></span>

<span data-ttu-id="266f3-107">Unicode jest preferowanym kodowaniem podczas pracy z plikami.</span><span class="sxs-lookup"><span data-stu-id="266f3-107">Unicode is the preferred encoding when working with files.</span></span> <span data-ttu-id="266f3-108">Unicode to światowy standard kodowania znaków, który używa 16-bitowych wartości kodu do reprezentowania wszystkich znaków używanych w nowoczesnych komputerach, w tym symboli technicznych i znaków specjalnych używanych w publikowaniu.</span><span class="sxs-lookup"><span data-stu-id="266f3-108">Unicode is a worldwide character-encoding standard that uses 16-bit code values to represent all the characters used in modern computing, including technical symbols and special characters used in publishing.</span></span>

<span data-ttu-id="266f3-109">Poprzednie standardy kodowania znaków składały się z tradycyjnych zestawów znaków, takich jak zestaw znaków ANSI systemu Windows, który używa 8-bitowych wartości kodu lub kombinacji wartości 8-bitowych do reprezentowania znaków używanych w określonym języku lub regionie geograficznym.</span><span class="sxs-lookup"><span data-stu-id="266f3-109">Previous character-encoding standards consisted of traditional character sets, such as the Windows ANSI character set that uses 8-bit code values, or combinations of 8-bit values, to represent the characters used in a specific language or geographical region.</span></span>

## <a name="encoding-class"></a><span data-ttu-id="266f3-110">Klasa kodowania</span><span class="sxs-lookup"><span data-stu-id="266f3-110">Encoding Class</span></span>

<span data-ttu-id="266f3-111">Klasa <xref:System.Text.Encoding> reprezentuje kodowanie znaków.</span><span class="sxs-lookup"><span data-stu-id="266f3-111">The <xref:System.Text.Encoding> class represents a character encoding.</span></span> <span data-ttu-id="266f3-112">W tej tabeli wymieniono typ dostępnych kodowania i opisano każdy z nich.</span><span class="sxs-lookup"><span data-stu-id="266f3-112">This table lists the type of encodings available and describes each.</span></span>

|<span data-ttu-id="266f3-113">Nazwa</span><span class="sxs-lookup"><span data-stu-id="266f3-113">Name</span></span>|<span data-ttu-id="266f3-114">Opis</span><span class="sxs-lookup"><span data-stu-id="266f3-114">Description</span></span>|
|---|---|
|<xref:System.Text.ASCIIEncoding>|<span data-ttu-id="266f3-115">Reprezentuje kodowanie znaków ASCII znaków Unicode.</span><span class="sxs-lookup"><span data-stu-id="266f3-115">Represents an ASCII character encoding of Unicode characters.</span></span>|
|<xref:System.Text.UnicodeEncoding>|<span data-ttu-id="266f3-116">Reprezentuje kodowanie UTF-16 znaków Unicode.</span><span class="sxs-lookup"><span data-stu-id="266f3-116">Represents a UTF-16 encoding of Unicode characters.</span></span>|
|<xref:System.Text.UTF32Encoding>|<span data-ttu-id="266f3-117">Reprezentuje kodowanie UTF-32 znaków Unicode.</span><span class="sxs-lookup"><span data-stu-id="266f3-117">Represents a UTF-32 encoding of Unicode characters.</span></span>|
|<xref:System.Text.UTF7Encoding>|<span data-ttu-id="266f3-118">Reprezentuje kodowanie ZNAKÓW Unicode w u. UTF-7.</span><span class="sxs-lookup"><span data-stu-id="266f3-118">Represents a UTF-7 encoding of Unicode characters.</span></span>|
|<xref:System.Text.UTF8Encoding>|<span data-ttu-id="266f3-119">Reprezentuje kodowanie ZNAKÓW Unicode w u. UTF-8.</span><span class="sxs-lookup"><span data-stu-id="266f3-119">Represents a UTF-8 encoding of Unicode characters.</span></span>|

## <a name="see-also"></a><span data-ttu-id="266f3-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="266f3-120">See also</span></span>

- [<span data-ttu-id="266f3-121">Odczyt z plików</span><span class="sxs-lookup"><span data-stu-id="266f3-121">Reading from Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/reading-from-files.md)
- [<span data-ttu-id="266f3-122">Zapisywanie w plikach</span><span class="sxs-lookup"><span data-stu-id="266f3-122">Writing to Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/writing-to-files.md)
