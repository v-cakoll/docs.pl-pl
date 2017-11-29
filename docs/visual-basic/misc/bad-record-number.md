---
title: "Nieprawidłowy numer rekordu"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vbrID63
ms.assetid: 1fcc33f8-822a-4de9-a6e3-228ddb5824a6
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: be04987353498775ec7dcef50b6acc1e6b4ec149
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="bad-record-number"></a><span data-ttu-id="05d86-102">Nieprawidłowy numer rekordu</span><span class="sxs-lookup"><span data-stu-id="05d86-102">Bad record number</span></span>
<span data-ttu-id="05d86-103">Liczba rekordów w `a FileGet`, `FilePut`, `FileGetObject`, lub `FilePutObject` instrukcja jest mniejsza niż lub równa zero.</span><span class="sxs-lookup"><span data-stu-id="05d86-103">The record number in `a FileGet`, `FilePut`, `FileGetObject`, or `FilePutObject` statement is less than or equal to zero.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="05d86-104">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="05d86-104">To correct this error</span></span>  
  
1.  <span data-ttu-id="05d86-105">Sprawdź obliczeń używane do generowania numer.</span><span class="sxs-lookup"><span data-stu-id="05d86-105">Check the calculations used in generating the record number.</span></span> <span data-ttu-id="05d86-106">Sprawdź pisownię zmiennych, zawierającą numer rekordu lub używana do obliczania liczby rekordów.</span><span class="sxs-lookup"><span data-stu-id="05d86-106">Verify spelling of the variables containing the record number or used in calculating record numbers.</span></span> <span data-ttu-id="05d86-107">Nieprawidłowo zapisana nazwa zmiennej jest niejawnie zadeklarowany i zainicjowana na wartość 0, chyba że użyto `Option Explicit On` w module.</span><span class="sxs-lookup"><span data-stu-id="05d86-107">A misspelled variable name is implicitly declared and initialized to zero, unless you used `Option Explicit On` in the module.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="05d86-108">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="05d86-108">See Also</span></span>  
 [<span data-ttu-id="05d86-109">Option Explicit — instrukcja</span><span class="sxs-lookup"><span data-stu-id="05d86-109">Option Explicit Statement</span></span>](../../visual-basic/language-reference/statements/option-explicit-statement.md)
