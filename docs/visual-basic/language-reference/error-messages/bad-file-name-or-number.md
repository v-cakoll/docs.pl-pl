---
title: Zła nazwa lub numer pliku
ms.date: 07/20/2015
f1_keywords:
- vbrID52
ms.assetid: d0e96aea-7621-48f6-a78b-5d37d18aaa4e
ms.openlocfilehash: b6da1031b60a4cd73c53588cf18992797c3fddab
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2019
ms.locfileid: "58839070"
---
# <a name="bad-file-name-or-number"></a><span data-ttu-id="6842d-102">Zła nazwa lub numer pliku</span><span class="sxs-lookup"><span data-stu-id="6842d-102">Bad file name or number</span></span>
<span data-ttu-id="6842d-103">Wystąpił błąd podczas próby uzyskania dostępu do określonego pliku.</span><span class="sxs-lookup"><span data-stu-id="6842d-103">An error occurred while trying to access the specified file.</span></span> <span data-ttu-id="6842d-104">Wśród możliwych przyczyn tego błędu są:</span><span class="sxs-lookup"><span data-stu-id="6842d-104">Among the possible causes for this error are:</span></span>  
  
-   <span data-ttu-id="6842d-105">Oświadczenie odnosi się do pliku przy użyciu nazwy pliku lub numeru, który nie został określony w `FileOpen` instrukcji lub która została określona w `FileOpen` instrukcji, jednak podano wartość następnie zamknięty.</span><span class="sxs-lookup"><span data-stu-id="6842d-105">A statement refers to a file with a file name or number that was not specified in the `FileOpen` statement or that was specified in a `FileOpen` statement but was subsequently closed.</span></span>  
  
-   <span data-ttu-id="6842d-106">Oświadczenie odnosi się do pliku z numerem, który znajduje się poza zakresem numerów plików.</span><span class="sxs-lookup"><span data-stu-id="6842d-106">A statement refers to a file with a number that is out of the range of file numbers.</span></span>  
  
-   <span data-ttu-id="6842d-107">Oświadczenie odnosi się do nazwy pliku lub numer, który jest nieprawidłowy.</span><span class="sxs-lookup"><span data-stu-id="6842d-107">A statement refers to a file name or number that is not valid.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="6842d-108">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="6842d-108">To correct this error</span></span>  
  
1.  <span data-ttu-id="6842d-109">Upewnij się, że nazwa pliku jest określona w `FileOpen` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="6842d-109">Make sure the file name is specified in a `FileOpen` statement.</span></span> <span data-ttu-id="6842d-110">Należy pamiętać, że po wywołaniu `FileClose` instrukcji bez argumentów, może przypadkowo zamknięto wszystkie otwarte pliki.</span><span class="sxs-lookup"><span data-stu-id="6842d-110">Note that if you invoked the `FileClose` statement without arguments, you may have inadvertently closed all open files.</span></span>  
  
2.  <span data-ttu-id="6842d-111">Jeśli Twój kod generuje algorithmically liczby plików, upewnij się, że cyfry są prawidłowe.</span><span class="sxs-lookup"><span data-stu-id="6842d-111">If your code is generating file numbers algorithmically, make sure the numbers are valid.</span></span>  
  
3.  <span data-ttu-id="6842d-112">Sprawdź nazwy pliku, aby upewnić się, że są one zgodne z konwencjami systemu operacyjnego.</span><span class="sxs-lookup"><span data-stu-id="6842d-112">Check the file names to make sure they conform to operating system conventions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6842d-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6842d-113">See also</span></span>

- <xref:Microsoft.VisualBasic.FileSystem.FileOpen%2A>
- [<span data-ttu-id="6842d-114">Visual Basic — konwencje nazewnictwa</span><span class="sxs-lookup"><span data-stu-id="6842d-114">Visual Basic Naming Conventions</span></span>](../../../visual-basic/programming-guide/program-structure/naming-conventions.md)
