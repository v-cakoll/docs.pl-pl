---
title: 'Porady: implementowanie zdefiniowanych przez użytkownika konwersji struktur (Przewodnik programowania w języku C#)'
ms.date: 07/20/2015
helpviewer_keywords:
- user-defined conversions [C#]
ms.assetid: 97839aef-8fbc-40d5-9769-6b569bc2710b
ms.openlocfilehash: cff85d60c1b59f4d1ca028f8fc02fee5728fa3d6
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43746707"
---
# <a name="how-to-implement-user-defined-conversions-between-structs-c-programming-guide"></a><span data-ttu-id="60d9c-102">Porady: implementowanie zdefiniowanych przez użytkownika konwersji struktur (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="60d9c-102">How to: Implement User-Defined Conversions Between Structs (C# Programming Guide)</span></span>
<span data-ttu-id="60d9c-103">Ten przykład definiuje dwie struktury `RomanNumeral` i `BinaryNumeral`i przedstawiono konwersje między nimi.</span><span class="sxs-lookup"><span data-stu-id="60d9c-103">This example defines two structs, `RomanNumeral` and `BinaryNumeral`, and demonstrates conversions between them.</span></span>  
  
## <a name="example"></a><span data-ttu-id="60d9c-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="60d9c-104">Example</span></span>  
 [!code-csharp[csProgGuideStatements#13](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-implement-user-defined-conversions-between-structs_1.cs)]  
  
## <a name="robust-programming"></a><span data-ttu-id="60d9c-105">Niezawodne programowanie</span><span class="sxs-lookup"><span data-stu-id="60d9c-105">Robust Programming</span></span>  
  
-   <span data-ttu-id="60d9c-106">W poprzednim przykładzie instrukcji:</span><span class="sxs-lookup"><span data-stu-id="60d9c-106">In the previous example, the statement:</span></span>  
  
     [!code-csharp[csProgGuideStatements#14](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-implement-user-defined-conversions-between-structs_2.cs)]  
  
     <span data-ttu-id="60d9c-107">wykonuje konwersję z `RomanNumeral` do `BinaryNumeral`.</span><span class="sxs-lookup"><span data-stu-id="60d9c-107">performs a conversion from a `RomanNumeral` to a `BinaryNumeral`.</span></span> <span data-ttu-id="60d9c-108">Ponieważ nie istnieje żadne bezpośrednie konwersja `RomanNumeral` do `BinaryNumeral`, używane jest rzutowanie do konwersji z `RomanNumeral` do `int`i innym rzutowanie do konwersji z `int` do `BinaryNumeral`.</span><span class="sxs-lookup"><span data-stu-id="60d9c-108">Because there is no direct conversion from `RomanNumeral` to `BinaryNumeral`, a cast is used to convert from a `RomanNumeral` to an `int`, and another cast to convert from an `int` to a `BinaryNumeral`.</span></span>  
  
-   <span data-ttu-id="60d9c-109">Również — instrukcja</span><span class="sxs-lookup"><span data-stu-id="60d9c-109">Also the statement</span></span>  
  
     [!code-csharp[csProgGuideStatements#15](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-implement-user-defined-conversions-between-structs_3.cs)]  
  
     <span data-ttu-id="60d9c-110">wykonuje konwersję z `BinaryNumeral` do `RomanNumeral`.</span><span class="sxs-lookup"><span data-stu-id="60d9c-110">performs a conversion from a `BinaryNumeral` to a `RomanNumeral`.</span></span> <span data-ttu-id="60d9c-111">Ponieważ `RomanNumeral` definiuje niejawna konwersja z `BinaryNumeral`, rzutowanie nie jest wymagana.</span><span class="sxs-lookup"><span data-stu-id="60d9c-111">Because `RomanNumeral` defines an implicit conversion from `BinaryNumeral`, no cast is required.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="60d9c-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="60d9c-112">See Also</span></span>

- [<span data-ttu-id="60d9c-113">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="60d9c-113">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="60d9c-114">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="60d9c-114">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="60d9c-115">Operatory konwersji</span><span class="sxs-lookup"><span data-stu-id="60d9c-115">Conversion Operators</span></span>](../../../csharp/programming-guide/statements-expressions-operators/conversion-operators.md)
