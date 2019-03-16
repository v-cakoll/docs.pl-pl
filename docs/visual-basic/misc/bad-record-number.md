---
title: Nieprawidłowy numer rekordu
ms.date: 07/20/2015
f1_keywords:
- vbrID63
ms.assetid: 1fcc33f8-822a-4de9-a6e3-228ddb5824a6
ms.openlocfilehash: c71d523406f3ffa420c36125847ab6d35a8f741c
ms.sourcegitcommit: 5c1abeec15fbddcc7dbaa729fabc1f1f29f12045
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2019
ms.locfileid: "58037107"
---
# <a name="bad-record-number"></a><span data-ttu-id="836de-102">Nieprawidłowy numer rekordu</span><span class="sxs-lookup"><span data-stu-id="836de-102">Bad record number</span></span>
<span data-ttu-id="836de-103">Numer rekordu w `a FileGet`, `FilePut`, `FileGetObject`, lub `FilePutObject` instrukcja jest mniejsza niż zero.</span><span class="sxs-lookup"><span data-stu-id="836de-103">The record number in `a FileGet`, `FilePut`, `FileGetObject`, or `FilePutObject` statement is less than or equal to zero.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="836de-104">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="836de-104">To correct this error</span></span>  
  
1.  <span data-ttu-id="836de-105">Sprawdź obliczenia używane do generowania numer rekordu.</span><span class="sxs-lookup"><span data-stu-id="836de-105">Check the calculations used in generating the record number.</span></span> <span data-ttu-id="836de-106">Sprawdź pisownię zmienne zawierającego numer rekordu lub używane podczas obliczania liczby rekordów.</span><span class="sxs-lookup"><span data-stu-id="836de-106">Verify spelling of the variables containing the record number or used in calculating record numbers.</span></span> <span data-ttu-id="836de-107">Nieprawidłowo zapisana nazwa zmiennej jest niejawnie zadeklarowana i inicjowane na wartość 0, o ile nie użyto `Option Explicit On` w module.</span><span class="sxs-lookup"><span data-stu-id="836de-107">A misspelled variable name is implicitly declared and initialized to zero, unless you used `Option Explicit On` in the module.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="836de-108">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="836de-108">See also</span></span>

- [<span data-ttu-id="836de-109">Option Explicit, instrukcja</span><span class="sxs-lookup"><span data-stu-id="836de-109">Option Explicit Statement</span></span>](../../visual-basic/language-reference/statements/option-explicit-statement.md)
