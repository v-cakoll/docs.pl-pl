---
title: Stałe muszą być typu wewnętrznego lub wyliczeniowego, a nie typu klasy, struktury, parametru typu lub tablicy
ms.date: 07/20/2015
f1_keywords:
- vbc30424
- bc30424
helpviewer_keywords:
- BC30424
ms.assetid: 2d402c2f-27ad-428b-b699-d45cd62f7196
ms.openlocfilehash: 0f4cb04558bf9768de22f432a1c59203643aba6a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54595845"
---
# <a name="constants-must-be-of-an-intrinsic-or-enumerated-type-not-a-class-structure-type-parameter-or-array-type"></a><span data-ttu-id="68946-102">Stałe muszą być typu wewnętrznego lub wyliczeniowego, a nie typu klasy, struktury, parametru typu lub tablicy</span><span class="sxs-lookup"><span data-stu-id="68946-102">Constants must be of an intrinsic or enumerated type, not a class, structure, type parameter, or array type</span></span>
<span data-ttu-id="68946-103">Podjęto próbę deklarowanie stałej jako klasy, struktury lub typ tablicy lub jako parametr typu zdefiniowane przez zawierającego typu ogólnego.</span><span class="sxs-lookup"><span data-stu-id="68946-103">You have attempted to declare a constant as a class, structure, or array type, or as a type parameter defined by a containing generic type.</span></span>  
  
 <span data-ttu-id="68946-104">Stałe muszą być typu wewnętrznego (`Boolean`, `Byte`, `Date`, `Decimal`, `Double`, `Integer`, `Long`, `Object`, `SByte`, `Short`, `Single`, `String`, `UInteger`, `ULong`, lub `UShort`), lub `Enum` typu na podstawie jednego z typów całkowitych.</span><span class="sxs-lookup"><span data-stu-id="68946-104">Constants must be of an intrinsic type (`Boolean`, `Byte`, `Date`, `Decimal`, `Double`, `Integer`, `Long`, `Object`, `SByte`, `Short`, `Single`, `String`, `UInteger`, `ULong`, or `UShort`), or an `Enum` type based on one of the integral types.</span></span>  
  
 <span data-ttu-id="68946-105">**Identyfikator błędu:** BC30424</span><span class="sxs-lookup"><span data-stu-id="68946-105">**Error ID:** BC30424</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="68946-106">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="68946-106">To correct this error</span></span>  
  
1.  <span data-ttu-id="68946-107">Deklarowanie stałej jako funkcja wewnętrzna lub `Enum` typu.</span><span class="sxs-lookup"><span data-stu-id="68946-107">Declare the constant as an intrinsic or `Enum` type.</span></span>  
  
2.  <span data-ttu-id="68946-108">Stała może być również specjalna wartość takich jak `True`, `False`, lub `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="68946-108">A constant can also be a special value such as `True`, `False`, or `Nothing`.</span></span> <span data-ttu-id="68946-109">Kompilator traktuje te wstępnie zdefiniowane wartości jako odpowiedniego typu wewnętrznego.</span><span class="sxs-lookup"><span data-stu-id="68946-109">The compiler considers these predefined values to be of the appropriate intrinsic type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="68946-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="68946-110">See also</span></span>
- [<span data-ttu-id="68946-111">Stałe i wyliczenia</span><span class="sxs-lookup"><span data-stu-id="68946-111">Constants and Enumerations</span></span>](../../../visual-basic/language-reference/constants-and-enumerations.md)
- [<span data-ttu-id="68946-112">Typy danych</span><span class="sxs-lookup"><span data-stu-id="68946-112">Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/index.md)
- [<span data-ttu-id="68946-113">Typy danych</span><span class="sxs-lookup"><span data-stu-id="68946-113">Data Types</span></span>](../../../visual-basic/language-reference/data-types/index.md)
