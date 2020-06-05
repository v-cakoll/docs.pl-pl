---
title: Zły numer rekordu
ms.date: 07/20/2015
f1_keywords:
- vbrID63
ms.assetid: 1fcc33f8-822a-4de9-a6e3-228ddb5824a6
ms.openlocfilehash: 44a11d95d33041de9d637684f41cb003dcc36b97
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84367545"
---
# <a name="bad-record-number"></a><span data-ttu-id="94856-102">Zły numer rekordu</span><span class="sxs-lookup"><span data-stu-id="94856-102">Bad record number</span></span>
<span data-ttu-id="94856-103">Liczba rekordów w `a FileGet` , `FilePut` , `FileGetObject` , lub `FilePutObject` instrukcji jest mniejsza lub równa zero.</span><span class="sxs-lookup"><span data-stu-id="94856-103">The record number in `a FileGet`, `FilePut`, `FileGetObject`, or `FilePutObject` statement is less than or equal to zero.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="94856-104">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="94856-104">To correct this error</span></span>  
  
1. <span data-ttu-id="94856-105">Sprawdź obliczenia używane podczas generowania numeru rekordu.</span><span class="sxs-lookup"><span data-stu-id="94856-105">Check the calculations used in generating the record number.</span></span> <span data-ttu-id="94856-106">Sprawdź pisownię zmiennych zawierających numer rekordu lub używany w obliczaniu numerów rekordów.</span><span class="sxs-lookup"><span data-stu-id="94856-106">Verify spelling of the variables containing the record number or used in calculating record numbers.</span></span> <span data-ttu-id="94856-107">Błędnie wpisana nazwa zmiennej jest niejawnie zadeklarowana i została zainicjowana do zera, chyba że została użyta `Option Explicit On` w module.</span><span class="sxs-lookup"><span data-stu-id="94856-107">A misspelled variable name is implicitly declared and initialized to zero, unless you used `Option Explicit On` in the module.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="94856-108">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="94856-108">See also</span></span>

- [<span data-ttu-id="94856-109">Option Explicit, instrukcja</span><span class="sxs-lookup"><span data-stu-id="94856-109">Option Explicit Statement</span></span>](../language-reference/statements/option-explicit-statement.md)
