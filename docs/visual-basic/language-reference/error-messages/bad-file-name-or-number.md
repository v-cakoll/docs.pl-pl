---
title: Zła nazwa lub numer pliku
ms.date: 07/20/2015
f1_keywords:
- vbrID52
ms.assetid: d0e96aea-7621-48f6-a78b-5d37d18aaa4e
ms.openlocfilehash: 11e866d9a8da7ad1ecc5f788fc31f6ac96d32f2c
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409832"
---
# <a name="bad-file-name-or-number"></a><span data-ttu-id="d5629-102">Zła nazwa lub numer pliku</span><span class="sxs-lookup"><span data-stu-id="d5629-102">Bad file name or number</span></span>
<span data-ttu-id="d5629-103">Wystąpił błąd podczas próby uzyskania dostępu do określonego pliku.</span><span class="sxs-lookup"><span data-stu-id="d5629-103">An error occurred while trying to access the specified file.</span></span> <span data-ttu-id="d5629-104">Wśród możliwych przyczyn tego błędu są:</span><span class="sxs-lookup"><span data-stu-id="d5629-104">Among the possible causes for this error are:</span></span>  
  
- <span data-ttu-id="d5629-105">Instrukcja odwołuje się do pliku z nazwą lub numerem pliku, który nie został określony w `FileOpen` instrukcji lub który został określony w instrukcji, `FileOpen` ale został zamknięty.</span><span class="sxs-lookup"><span data-stu-id="d5629-105">A statement refers to a file with a file name or number that was not specified in the `FileOpen` statement or that was specified in a `FileOpen` statement but was subsequently closed.</span></span>  
  
- <span data-ttu-id="d5629-106">Instrukcja odwołuje się do pliku o liczbie poza zakresem numerów plików.</span><span class="sxs-lookup"><span data-stu-id="d5629-106">A statement refers to a file with a number that is out of the range of file numbers.</span></span>  
  
- <span data-ttu-id="d5629-107">Instrukcja odwołuje się do nieprawidłowej nazwy lub liczby plików.</span><span class="sxs-lookup"><span data-stu-id="d5629-107">A statement refers to a file name or number that is not valid.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="d5629-108">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="d5629-108">To correct this error</span></span>  
  
1. <span data-ttu-id="d5629-109">Upewnij się, że nazwa pliku jest określona w `FileOpen` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="d5629-109">Make sure the file name is specified in a `FileOpen` statement.</span></span> <span data-ttu-id="d5629-110">Należy pamiętać, że jeśli wywołano `FileClose` instrukcję bez argumentów, być może przypadkowo zamknięto wszystkie otwarte pliki.</span><span class="sxs-lookup"><span data-stu-id="d5629-110">Note that if you invoked the `FileClose` statement without arguments, you may have inadvertently closed all open files.</span></span>  
  
2. <span data-ttu-id="d5629-111">Jeśli kod generuje numery plików algorithmically, upewnij się, że liczby są prawidłowe.</span><span class="sxs-lookup"><span data-stu-id="d5629-111">If your code is generating file numbers algorithmically, make sure the numbers are valid.</span></span>  
  
3. <span data-ttu-id="d5629-112">Sprawdź nazwy plików, aby upewnić się, że są one zgodne z konwencjami systemu operacyjnego.</span><span class="sxs-lookup"><span data-stu-id="d5629-112">Check the file names to make sure they conform to operating system conventions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d5629-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d5629-113">See also</span></span>

- <xref:Microsoft.VisualBasic.FileSystem.FileOpen%2A>
- [<span data-ttu-id="d5629-114">Visual Basic — Konwencje nazewnictwa</span><span class="sxs-lookup"><span data-stu-id="d5629-114">Visual Basic Naming Conventions</span></span>](../../programming-guide/program-structure/naming-conventions.md)
