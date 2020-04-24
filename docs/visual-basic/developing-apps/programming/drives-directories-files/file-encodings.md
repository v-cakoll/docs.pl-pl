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
# <a name="file-encodings-visual-basic"></a><span data-ttu-id="00c3c-102">Kodowanie pliku (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="00c3c-102">File Encodings (Visual Basic)</span></span>

<span data-ttu-id="00c3c-103">Kodowanie plików, znane także jako kodowania znaków, określają sposób reprezentowania znaków podczas przetwarzania tekstu.</span><span class="sxs-lookup"><span data-stu-id="00c3c-103">File encodings, also known as character encodings, specify how to represent characters when text processing.</span></span> <span data-ttu-id="00c3c-104">Jedno kodowanie może być preferowane przez inne warunki języka, które może lub nie może obsłużyć, chociaż standard Unicode jest zazwyczaj preferowany.</span><span class="sxs-lookup"><span data-stu-id="00c3c-104">One encoding may be preferable over another in terms of which language characters it can or cannot handle, although Unicode is usually preferred.</span></span>

<span data-ttu-id="00c3c-105">Podczas odczytywania z plików lub zapisywania do nich niewłaściwie dopasowane kodowania plików mogą spowodować wyjątki lub nieprawidłowe wyniki.</span><span class="sxs-lookup"><span data-stu-id="00c3c-105">When reading from or writing to files, improperly matching file encodings may result in exceptions or incorrect results.</span></span>

## <a name="types-of-encodings"></a><span data-ttu-id="00c3c-106">Typy kodowań</span><span class="sxs-lookup"><span data-stu-id="00c3c-106">Types of Encodings</span></span>

<span data-ttu-id="00c3c-107">Unicode jest preferowanym kodowaniem podczas pracy z plikami.</span><span class="sxs-lookup"><span data-stu-id="00c3c-107">Unicode is the preferred encoding when working with files.</span></span> <span data-ttu-id="00c3c-108">Unicode to ogólnoświatowy standard kodowania znaków, który używa wartości 16-bitowych kodu do reprezentowania wszystkich znaków używanych w nowoczesnych obliczeniach, w tym symboli technicznych i znaków specjalnych używanych do publikowania.</span><span class="sxs-lookup"><span data-stu-id="00c3c-108">Unicode is a worldwide character-encoding standard that uses 16-bit code values to represent all the characters used in modern computing, including technical symbols and special characters used in publishing.</span></span>

<span data-ttu-id="00c3c-109">Poprzednie standardy kodowania znaków składają się z tradycyjnych zestawów znaków, takich jak zestaw znaków ANSI systemu Windows, który używa wartości 8-bitowych lub kombinacji wartości 8-bitowych, aby reprezentować znaki używane w konkretnym języku lub regionie geograficznym.</span><span class="sxs-lookup"><span data-stu-id="00c3c-109">Previous character-encoding standards consisted of traditional character sets, such as the Windows ANSI character set that uses 8-bit code values, or combinations of 8-bit values, to represent the characters used in a specific language or geographical region.</span></span>

## <a name="encoding-class"></a><span data-ttu-id="00c3c-110">Klasa kodowania</span><span class="sxs-lookup"><span data-stu-id="00c3c-110">Encoding Class</span></span>

<span data-ttu-id="00c3c-111"><xref:System.Text.Encoding> Klasa reprezentuje kodowanie znaków.</span><span class="sxs-lookup"><span data-stu-id="00c3c-111">The <xref:System.Text.Encoding> class represents a character encoding.</span></span> <span data-ttu-id="00c3c-112">W tej tabeli przedstawiono typ dostępnych kodowań i opisano poszczególne z nich.</span><span class="sxs-lookup"><span data-stu-id="00c3c-112">This table lists the type of encodings available and describes each.</span></span>

|<span data-ttu-id="00c3c-113">Nazwa</span><span class="sxs-lookup"><span data-stu-id="00c3c-113">Name</span></span>|<span data-ttu-id="00c3c-114">Opis</span><span class="sxs-lookup"><span data-stu-id="00c3c-114">Description</span></span>|
|---|---|
|<xref:System.Text.ASCIIEncoding>|<span data-ttu-id="00c3c-115">Reprezentuje kodowanie znaków ASCII znaków Unicode.</span><span class="sxs-lookup"><span data-stu-id="00c3c-115">Represents an ASCII character encoding of Unicode characters.</span></span>|
|<xref:System.Text.UnicodeEncoding>|<span data-ttu-id="00c3c-116">Reprezentuje kodowanie UTF-16 znaków Unicode.</span><span class="sxs-lookup"><span data-stu-id="00c3c-116">Represents a UTF-16 encoding of Unicode characters.</span></span>|
|<xref:System.Text.UTF32Encoding>|<span data-ttu-id="00c3c-117">Reprezentuje kodowanie UTF-32 znaków Unicode.</span><span class="sxs-lookup"><span data-stu-id="00c3c-117">Represents a UTF-32 encoding of Unicode characters.</span></span>|
|<xref:System.Text.UTF7Encoding>|<span data-ttu-id="00c3c-118">Reprezentuje kodowanie UTF-7 znaków Unicode.</span><span class="sxs-lookup"><span data-stu-id="00c3c-118">Represents a UTF-7 encoding of Unicode characters.</span></span>|
|<xref:System.Text.UTF8Encoding>|<span data-ttu-id="00c3c-119">Reprezentuje kodowanie UTF-8 znaków Unicode.</span><span class="sxs-lookup"><span data-stu-id="00c3c-119">Represents a UTF-8 encoding of Unicode characters.</span></span>|

## <a name="see-also"></a><span data-ttu-id="00c3c-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="00c3c-120">See also</span></span>

- [<span data-ttu-id="00c3c-121">Odczyt z plików</span><span class="sxs-lookup"><span data-stu-id="00c3c-121">Reading from Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/reading-from-files.md)
- [<span data-ttu-id="00c3c-122">Zapisywanie w plikach</span><span class="sxs-lookup"><span data-stu-id="00c3c-122">Writing to Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/writing-to-files.md)
