---
title: Błąd ładowania biblioteki DLL (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vbrID48
ms.assetid: 4226cd1f-028c-477d-88a5-cb57f7e0cdc8
ms.openlocfilehash: 5a26443a49b0b853f2f2188fb58d7ed907d671b4
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64659625"
---
# <a name="error-in-loading-dll-visual-basic"></a><span data-ttu-id="d53fb-102">Błąd ładowania biblioteki DLL (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d53fb-102">Error in loading DLL (Visual Basic)</span></span>
<span data-ttu-id="d53fb-103">Biblioteki dołączanej (dynamicznie DLL) jest biblioteką, określone w `Lib` klauzuli `Declare` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="d53fb-103">A dynamic-link library (DLL) is a library specified in the `Lib` clause of a `Declare` statement.</span></span> <span data-ttu-id="d53fb-104">Możliwe przyczyny tego błędu to:</span><span class="sxs-lookup"><span data-stu-id="d53fb-104">Possible causes for this error include:</span></span>  
  
- <span data-ttu-id="d53fb-105">Plik nie jest wykonywalny biblioteki DLL.</span><span class="sxs-lookup"><span data-stu-id="d53fb-105">The file is not DLL executable.</span></span>  
  
- <span data-ttu-id="d53fb-106">Plik nie jest biblioteką DLL Windows firmy Microsoft.</span><span class="sxs-lookup"><span data-stu-id="d53fb-106">The file is not a Microsoft Windows DLL.</span></span>  
  
- <span data-ttu-id="d53fb-107">Biblioteka DLL odwołuje się do innej biblioteki DLL, która nie jest obecny.</span><span class="sxs-lookup"><span data-stu-id="d53fb-107">The DLL references another DLL that is not present.</span></span>  
  
- <span data-ttu-id="d53fb-108">Plik DLL lub biblioteki DLL do którego istnieje odwołanie nie jest w katalogu określonego w ścieżce.</span><span class="sxs-lookup"><span data-stu-id="d53fb-108">The DLL or referenced DLL is not in a directory specified in the path.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="d53fb-109">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="d53fb-109">To correct this error</span></span>  
  
- <span data-ttu-id="d53fb-110">Jeśli plik znajduje się tekst źródłowy plik, a w związku z tym nie plik wykonywalny biblioteki DLL, musi być skompilowane i połączone do postaci pliku wykonywalnego biblioteki DLL.</span><span class="sxs-lookup"><span data-stu-id="d53fb-110">If the file is a source-text file and therefore not DLL executable, it must be compiled and linked to a DLL-executable form.</span></span>  
  
- <span data-ttu-id="d53fb-111">Jeśli plik nie jest biblioteką DLL Windows firmy Microsoft, należy uzyskać równoważne Windows firmy Microsoft.</span><span class="sxs-lookup"><span data-stu-id="d53fb-111">If the file is not a Microsoft Windows DLL, obtain the Microsoft Windows equivalent.</span></span>  
  
- <span data-ttu-id="d53fb-112">Jeśli biblioteka DLL odwołuje się do innej biblioteki DLL, która nie jest obecny, Uzyskaj DLL do którego istnieje odwołanie i udostępnić go.</span><span class="sxs-lookup"><span data-stu-id="d53fb-112">If the DLL references another DLL that is not present, obtain the referenced DLL and make it available.</span></span>  
  
- <span data-ttu-id="d53fb-113">Jeśli biblioteka DLL lub biblioteki DLL do którego istnieje odwołanie nie jest w katalogu określony przez ścieżkę, Przenieś bibliotekę DLL do katalogu, do którego istnieje odwołanie.</span><span class="sxs-lookup"><span data-stu-id="d53fb-113">If the DLL or referenced DLL is not in a directory specified by the path, move the DLL to a referenced directory.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d53fb-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d53fb-114">See also</span></span>

- [<span data-ttu-id="d53fb-115">Declare, instrukcja</span><span class="sxs-lookup"><span data-stu-id="d53fb-115">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)
