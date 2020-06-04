---
title: Typ „<typename>” nie ma konstruktorów
ms.date: 07/20/2015
f1_keywords:
- bc30251
- vbc30251
helpviewer_keywords:
- BC30251
ms.assetid: aff3e1df-abe6-4bc0-9abc-a1e70514c561
ms.openlocfilehash: de0d825c7eec603f3ad1e43b1e4aaa0cc78fd1db
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84408513"
---
# <a name="type-typename-has-no-constructors"></a><span data-ttu-id="02015-102">Typ „\<typename>” nie ma konstruktorów</span><span class="sxs-lookup"><span data-stu-id="02015-102">Type '\<typename>' has no constructors</span></span>
<span data-ttu-id="02015-103">Typ nie obsługuje wywołania do `Sub New()` .</span><span class="sxs-lookup"><span data-stu-id="02015-103">A type does not support a call to `Sub New()`.</span></span> <span data-ttu-id="02015-104">Jedną z możliwych przyczyn jest uszkodzony kompilator lub plik binarny.</span><span class="sxs-lookup"><span data-stu-id="02015-104">One possible cause is a corrupted compiler or binary file.</span></span>  
  
 <span data-ttu-id="02015-105">**Identyfikator błędu:** BC30251</span><span class="sxs-lookup"><span data-stu-id="02015-105">**Error ID:** BC30251</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="02015-106">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="02015-106">To correct this error</span></span>  
  
1. <span data-ttu-id="02015-107">Jeśli typ znajduje się w innym projekcie lub w pliku, do którego istnieje odwołanie, zainstaluj ponownie projekt lub plik.</span><span class="sxs-lookup"><span data-stu-id="02015-107">If the type is in a different project or in a referenced file, reinstall the project or file.</span></span>  
  
2. <span data-ttu-id="02015-108">Jeśli typ znajduje się w tym samym projekcie, Skompiluj ponownie zestaw zawierający typ.</span><span class="sxs-lookup"><span data-stu-id="02015-108">If the type is in the same project, recompile the assembly containing the type.</span></span>  
  
3. <span data-ttu-id="02015-109">Jeśli błąd powtarza się, zainstaluj ponownie kompilator Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="02015-109">If the error recurs, reinstall the Visual Basic compiler.</span></span>  
  
4. <span data-ttu-id="02015-110">Jeśli błąd będzie się powtarzać, Zbierz informacje o okolicznościach i powiadom usługi pomocy technicznej firmy Microsoft.</span><span class="sxs-lookup"><span data-stu-id="02015-110">If the error persists, gather information about the circumstances and notify Microsoft Product Support Services.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="02015-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="02015-111">See also</span></span>

- [<span data-ttu-id="02015-112">Obiekty i klasy</span><span class="sxs-lookup"><span data-stu-id="02015-112">Objects and Classes</span></span>](../../programming-guide/language-features/objects-and-classes/index.md)
- [<span data-ttu-id="02015-113">Porozmawiaj z nami</span><span class="sxs-lookup"><span data-stu-id="02015-113">Talk to Us</span></span>](/visualstudio/ide/feedback-options)
