---
title: Błąd ładowania biblioteki DLL (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vbrID48
ms.assetid: 4226cd1f-028c-477d-88a5-cb57f7e0cdc8
ms.openlocfilehash: ac21c4d52b248025ee26bac3e511bb5b0a0b668e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33584686"
---
# <a name="error-in-loading-dll-visual-basic"></a><span data-ttu-id="3fa8f-102">Błąd ładowania biblioteki DLL (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3fa8f-102">Error in loading DLL (Visual Basic)</span></span>
<span data-ttu-id="3fa8f-103">Biblioteki dołączanej (dynamicznie DLL) jest określona w bibliotece `Lib` klauzuli `Declare` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="3fa8f-103">A dynamic-link library (DLL) is a library specified in the `Lib` clause of a `Declare` statement.</span></span> <span data-ttu-id="3fa8f-104">Możliwe przyczyny tego błędu to:</span><span class="sxs-lookup"><span data-stu-id="3fa8f-104">Possible causes for this error include:</span></span>  
  
-   <span data-ttu-id="3fa8f-105">Plik nie jest wykonywalne biblioteki DLL.</span><span class="sxs-lookup"><span data-stu-id="3fa8f-105">The file is not DLL executable.</span></span>  
  
-   <span data-ttu-id="3fa8f-106">Plik nie jest biblioteką DLL systemu Windows firmy Microsoft.</span><span class="sxs-lookup"><span data-stu-id="3fa8f-106">The file is not a Microsoft Windows DLL.</span></span>  
  
-   <span data-ttu-id="3fa8f-107">Plik DLL, który odwołuje się do innej bibliotece DLL, która nie występuje.</span><span class="sxs-lookup"><span data-stu-id="3fa8f-107">The DLL references another DLL that is not present.</span></span>  
  
-   <span data-ttu-id="3fa8f-108">Biblioteki DLL lub pliku nie jest określona w ścieżce katalogu.</span><span class="sxs-lookup"><span data-stu-id="3fa8f-108">The DLL or referenced DLL is not in a directory specified in the path.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="3fa8f-109">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="3fa8f-109">To correct this error</span></span>  
  
-   <span data-ttu-id="3fa8f-110">Jeśli plik znajduje się plik tekst źródłowy i dlatego nie plik wykonywalny biblioteki DLL, musi być skompilowany i połączony z formularzem plik wykonywalny biblioteki DLL.</span><span class="sxs-lookup"><span data-stu-id="3fa8f-110">If the file is a source-text file and therefore not DLL executable, it must be compiled and linked to a DLL-executable form.</span></span>  
  
-   <span data-ttu-id="3fa8f-111">Jeśli plik nie jest biblioteką DLL systemu Windows firmy Microsoft, należy uzyskać równoważne Microsoft Windows.</span><span class="sxs-lookup"><span data-stu-id="3fa8f-111">If the file is not a Microsoft Windows DLL, obtain the Microsoft Windows equivalent.</span></span>  
  
-   <span data-ttu-id="3fa8f-112">Jeśli plik DLL, który odwołuje się do innej bibliotece DLL, która nie jest obecny, Uzyskaj przywoływanego biblioteki DLL i udostępni go.</span><span class="sxs-lookup"><span data-stu-id="3fa8f-112">If the DLL references another DLL that is not present, obtain the referenced DLL and make it available.</span></span>  
  
-   <span data-ttu-id="3fa8f-113">Jeśli plik DLL lub pliku nie jest określony przez ścieżkę katalogu, należy przenieść biblioteki DLL do katalogu, do którego istnieje odwołanie.</span><span class="sxs-lookup"><span data-stu-id="3fa8f-113">If the DLL or referenced DLL is not in a directory specified by the path, move the DLL to a referenced directory.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3fa8f-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3fa8f-114">See Also</span></span>  
 [<span data-ttu-id="3fa8f-115">Declare, instrukcja</span><span class="sxs-lookup"><span data-stu-id="3fa8f-115">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)
