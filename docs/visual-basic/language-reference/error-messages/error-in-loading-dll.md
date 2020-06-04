---
title: Błąd ładowania biblioteki DLL
ms.date: 07/20/2015
f1_keywords:
- vbrID48
ms.assetid: 4226cd1f-028c-477d-88a5-cb57f7e0cdc8
ms.openlocfilehash: fd2e425f2dd3f4127cd777d4a1f7ab9809de9d45
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409633"
---
# <a name="error-in-loading-dll-visual-basic"></a><span data-ttu-id="83bc5-102">Błąd ładowania biblioteki DLL (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="83bc5-102">Error in loading DLL (Visual Basic)</span></span>
<span data-ttu-id="83bc5-103">Biblioteka dołączana dynamicznie (DLL) to biblioteka określona w `Lib` klauzuli `Declare` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="83bc5-103">A dynamic-link library (DLL) is a library specified in the `Lib` clause of a `Declare` statement.</span></span> <span data-ttu-id="83bc5-104">Możliwe przyczyny tego błędu to:</span><span class="sxs-lookup"><span data-stu-id="83bc5-104">Possible causes for this error include:</span></span>  
  
- <span data-ttu-id="83bc5-105">Plik nie jest plikiem wykonywalnym DLL.</span><span class="sxs-lookup"><span data-stu-id="83bc5-105">The file is not DLL executable.</span></span>  
  
- <span data-ttu-id="83bc5-106">Ten plik nie jest plikiem DLL systemu Microsoft Windows.</span><span class="sxs-lookup"><span data-stu-id="83bc5-106">The file is not a Microsoft Windows DLL.</span></span>  
  
- <span data-ttu-id="83bc5-107">Biblioteka DLL odwołuje się do innej nieobecnej biblioteki DLL.</span><span class="sxs-lookup"><span data-stu-id="83bc5-107">The DLL references another DLL that is not present.</span></span>  
  
- <span data-ttu-id="83bc5-108">Biblioteka DLL lub przywoływana Biblioteka DLL nie znajduje się w katalogu określonym w ścieżce.</span><span class="sxs-lookup"><span data-stu-id="83bc5-108">The DLL or referenced DLL is not in a directory specified in the path.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="83bc5-109">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="83bc5-109">To correct this error</span></span>  
  
- <span data-ttu-id="83bc5-110">Jeśli plik jest plikiem źródłowym i w związku z tym nie jest plikiem wykonywalnym DLL, musi być skompilowany i połączony z formularzem wykonywalnym biblioteki DLL.</span><span class="sxs-lookup"><span data-stu-id="83bc5-110">If the file is a source-text file and therefore not DLL executable, it must be compiled and linked to a DLL-executable form.</span></span>  
  
- <span data-ttu-id="83bc5-111">Jeśli plik nie jest plikiem DLL systemu Microsoft Windows, uzyskaj odpowiedniki systemu Microsoft Windows.</span><span class="sxs-lookup"><span data-stu-id="83bc5-111">If the file is not a Microsoft Windows DLL, obtain the Microsoft Windows equivalent.</span></span>  
  
- <span data-ttu-id="83bc5-112">Jeśli biblioteka DLL odwołuje się do innej nieobecnej biblioteki DLL, uzyskaj przywoływaną bibliotekę DLL i Udostępnij ją.</span><span class="sxs-lookup"><span data-stu-id="83bc5-112">If the DLL references another DLL that is not present, obtain the referenced DLL and make it available.</span></span>  
  
- <span data-ttu-id="83bc5-113">Jeśli biblioteka DLL lub przywoływana Biblioteka DLL nie znajduje się w katalogu określonym przez ścieżkę, Przenieś bibliotekę DLL do katalogu, do którego się odwołuje.</span><span class="sxs-lookup"><span data-stu-id="83bc5-113">If the DLL or referenced DLL is not in a directory specified by the path, move the DLL to a referenced directory.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="83bc5-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="83bc5-114">See also</span></span>

- [<span data-ttu-id="83bc5-115">Declare — Instrukcja</span><span class="sxs-lookup"><span data-stu-id="83bc5-115">Declare Statement</span></span>](../statements/declare-statement.md)
