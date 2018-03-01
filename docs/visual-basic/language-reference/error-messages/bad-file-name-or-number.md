---
title: "Zła nazwa lub numer pliku"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbrID52
ms.assetid: d0e96aea-7621-48f6-a78b-5d37d18aaa4e
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 3d7c8bae3df0e75a1c4f9afacdff681a553503d2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="bad-file-name-or-number"></a><span data-ttu-id="1e3f0-102">Zła nazwa lub numer pliku</span><span class="sxs-lookup"><span data-stu-id="1e3f0-102">Bad file name or number</span></span>
<span data-ttu-id="1e3f0-103">Wystąpił błąd podczas próby uzyskania dostępu do określonego pliku.</span><span class="sxs-lookup"><span data-stu-id="1e3f0-103">An error occurred while trying to access the specified file.</span></span> <span data-ttu-id="1e3f0-104">Wśród możliwych przyczyn tego błędu są:</span><span class="sxs-lookup"><span data-stu-id="1e3f0-104">Among the possible causes for this error are:</span></span>  
  
-   <span data-ttu-id="1e3f0-105">Oświadczenie odnosi się do pliku za pomocą nazwy pliku i numer, który nie został określony w `FileOpen` instrukcji lub która została określona w `FileOpen` instrukcji, jednak podano następnie zamknięte.</span><span class="sxs-lookup"><span data-stu-id="1e3f0-105">A statement refers to a file with a file name or number that was not specified in the `FileOpen` statement or that was specified in a `FileOpen` statement but was subsequently closed.</span></span>  
  
-   <span data-ttu-id="1e3f0-106">Oświadczenie odnosi się do pliku z numerem, który znajduje się poza zakresem numerów plików.</span><span class="sxs-lookup"><span data-stu-id="1e3f0-106">A statement refers to a file with a number that is out of the range of file numbers.</span></span>  
  
-   <span data-ttu-id="1e3f0-107">Oświadczenie odnosi się do nazwy pliku lub liczba, która jest nieprawidłowa.</span><span class="sxs-lookup"><span data-stu-id="1e3f0-107">A statement refers to a file name or number that is not valid.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="1e3f0-108">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="1e3f0-108">To correct this error</span></span>  
  
1.  <span data-ttu-id="1e3f0-109">Upewnij się, że nazwa pliku jest określona w `FileOpen` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="1e3f0-109">Make sure the file name is specified in a `FileOpen` statement.</span></span> <span data-ttu-id="1e3f0-110">Należy pamiętać, że jeśli zostanie wywołany `FileClose` instrukcji bez argumentów, może spowodować niezamierzoną zamknięciu wszystkich otwartych plików.</span><span class="sxs-lookup"><span data-stu-id="1e3f0-110">Note that if you invoked the `FileClose` statement without arguments, you may have inadvertently closed all open files.</span></span>  
  
2.  <span data-ttu-id="1e3f0-111">Jeśli kod jest generowany numerów plików algorithmically, upewnij się, że numery są prawidłowe.</span><span class="sxs-lookup"><span data-stu-id="1e3f0-111">If your code is generating file numbers algorithmically, make sure the numbers are valid.</span></span>  
  
3.  <span data-ttu-id="1e3f0-112">Sprawdź nazwy pliku, aby upewnić się, że są one zgodne z konwencjami systemu operacyjnego.</span><span class="sxs-lookup"><span data-stu-id="1e3f0-112">Check the file names to make sure they conform to operating system conventions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1e3f0-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1e3f0-113">See Also</span></span>  
 <xref:Microsoft.VisualBasic.FileSystem.FileOpen%2A>  
 [<span data-ttu-id="1e3f0-114">Visual Basic — konwencje nazewnictwa</span><span class="sxs-lookup"><span data-stu-id="1e3f0-114">Visual Basic Naming Conventions</span></span>](../../../visual-basic/programming-guide/program-structure/naming-conventions.md)
