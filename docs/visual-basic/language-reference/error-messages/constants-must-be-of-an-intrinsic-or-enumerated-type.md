---
title: Stałe muszą być typu wewnętrznego lub wyliczeniowego, a nie typu klasy, struktury, parametru typu lub tablicy
ms.date: 07/20/2015
f1_keywords:
- vbc30424
- bc30424
helpviewer_keywords:
- BC30424
ms.assetid: 2d402c2f-27ad-428b-b699-d45cd62f7196
ms.openlocfilehash: 4d635d289ed99aed48c296c278bc546971af51da
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2018
ms.locfileid: "44083925"
---
# <a name="constants-must-be-of-an-intrinsic-or-enumerated-type-not-a-class-structure-type-parameter-or-array-type"></a><span data-ttu-id="e9530-102">Stałe muszą być typu wewnętrznego lub wyliczeniowego, a nie typu klasy, struktury, parametru typu lub tablicy</span><span class="sxs-lookup"><span data-stu-id="e9530-102">Constants must be of an intrinsic or enumerated type, not a class, structure, type parameter, or array type</span></span>
<span data-ttu-id="e9530-103">Podjęto próbę deklarowanie stałej jako klasy, struktury lub typ tablicy lub jako parametr typu zdefiniowane przez zawierającego typu ogólnego.</span><span class="sxs-lookup"><span data-stu-id="e9530-103">You have attempted to declare a constant as a class, structure, or array type, or as a type parameter defined by a containing generic type.</span></span>  
  
 <span data-ttu-id="e9530-104">Stałe muszą być typu wewnętrznego (`Boolean`, `Byte`, `Date`, `Decimal`, `Double`, `Integer`, `Long`, `Object`, `SByte`, `Short`, `Single`, `String`, `UInteger`, `ULong`, lub `UShort`), lub `Enum` typu na podstawie jednego z typów całkowitych.</span><span class="sxs-lookup"><span data-stu-id="e9530-104">Constants must be of an intrinsic type (`Boolean`, `Byte`, `Date`, `Decimal`, `Double`, `Integer`, `Long`, `Object`, `SByte`, `Short`, `Single`, `String`, `UInteger`, `ULong`, or `UShort`), or an `Enum` type based on one of the integral types.</span></span>  
  
 <span data-ttu-id="e9530-105">**Identyfikator błędu:** BC30424</span><span class="sxs-lookup"><span data-stu-id="e9530-105">**Error ID:** BC30424</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="e9530-106">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="e9530-106">To correct this error</span></span>  
  
1.  <span data-ttu-id="e9530-107">Deklarowanie stałej jako funkcja wewnętrzna lub `Enum` typu.</span><span class="sxs-lookup"><span data-stu-id="e9530-107">Declare the constant as an intrinsic or `Enum` type.</span></span>  
  
2.  <span data-ttu-id="e9530-108">Stała może być również specjalna wartość takich jak `True`, `False`, lub `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="e9530-108">A constant can also be a special value such as `True`, `False`, or `Nothing`.</span></span> <span data-ttu-id="e9530-109">Kompilator traktuje te wstępnie zdefiniowane wartości jako odpowiedniego typu wewnętrznego.</span><span class="sxs-lookup"><span data-stu-id="e9530-109">The compiler considers these predefined values to be of the appropriate intrinsic type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e9530-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e9530-110">See Also</span></span>  
 [<span data-ttu-id="e9530-111">Stałe i wyliczenia</span><span class="sxs-lookup"><span data-stu-id="e9530-111">Constants and Enumerations</span></span>](../../../visual-basic/language-reference/constants-and-enumerations.md)  
 [<span data-ttu-id="e9530-112">Typy danych</span><span class="sxs-lookup"><span data-stu-id="e9530-112">Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/index.md)  
 [<span data-ttu-id="e9530-113">Typy danych</span><span class="sxs-lookup"><span data-stu-id="e9530-113">Data Types</span></span>](../../../visual-basic/language-reference/data-types/index.md)
