---
title: 'Porady: implementowanie zdefiniowanych przez użytkownika konwersji struktur (Przewodnik programowania w języku C#)'
ms.date: 07/20/2015
helpviewer_keywords:
- user-defined conversions [C#]
ms.assetid: 97839aef-8fbc-40d5-9769-6b569bc2710b
ms.openlocfilehash: 178d9e2f92c5c1989253a16d866052a1fc42c10e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33339933"
---
# <a name="how-to-implement-user-defined-conversions-between-structs-c-programming-guide"></a><span data-ttu-id="d9e12-102">Porady: implementowanie zdefiniowanych przez użytkownika konwersji struktur (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="d9e12-102">How to: Implement User-Defined Conversions Between Structs (C# Programming Guide)</span></span>
<span data-ttu-id="d9e12-103">W tym przykładzie definiuje dwie struktury `RomanNumeral` i `BinaryNumeral`i pokazuje konwersji między nimi.</span><span class="sxs-lookup"><span data-stu-id="d9e12-103">This example defines two structs, `RomanNumeral` and `BinaryNumeral`, and demonstrates conversions between them.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d9e12-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="d9e12-104">Example</span></span>  
 [!code-csharp[csProgGuideStatements#13](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-implement-user-defined-conversions-between-structs_1.cs)]  
  
## <a name="robust-programming"></a><span data-ttu-id="d9e12-105">Niezawodne programowanie</span><span class="sxs-lookup"><span data-stu-id="d9e12-105">Robust Programming</span></span>  
  
-   <span data-ttu-id="d9e12-106">W poprzednim przykładzie instrukcji:</span><span class="sxs-lookup"><span data-stu-id="d9e12-106">In the previous example, the statement:</span></span>  
  
     [!code-csharp[csProgGuideStatements#14](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-implement-user-defined-conversions-between-structs_2.cs)]  
  
     <span data-ttu-id="d9e12-107">wykonuje konwersję z `RomanNumeral` do `BinaryNumeral`.</span><span class="sxs-lookup"><span data-stu-id="d9e12-107">performs a conversion from a `RomanNumeral` to a `BinaryNumeral`.</span></span> <span data-ttu-id="d9e12-108">Ponieważ nie jest bezpośrednio konwersja z `RomanNumeral` do `BinaryNumeral`, rzutowanie służy do konwertowania z `RomanNumeral` do `int`i innym rzutowanie do przekonwertowania z `int` do `BinaryNumeral`.</span><span class="sxs-lookup"><span data-stu-id="d9e12-108">Because there is no direct conversion from `RomanNumeral` to `BinaryNumeral`, a cast is used to convert from a `RomanNumeral` to an `int`, and another cast to convert from an `int` to a `BinaryNumeral`.</span></span>  
  
-   <span data-ttu-id="d9e12-109">Również — instrukcja</span><span class="sxs-lookup"><span data-stu-id="d9e12-109">Also the statement</span></span>  
  
     [!code-csharp[csProgGuideStatements#15](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-implement-user-defined-conversions-between-structs_3.cs)]  
  
     <span data-ttu-id="d9e12-110">wykonuje konwersję z `BinaryNumeral` do `RomanNumeral`.</span><span class="sxs-lookup"><span data-stu-id="d9e12-110">performs a conversion from a `BinaryNumeral` to a `RomanNumeral`.</span></span> <span data-ttu-id="d9e12-111">Ponieważ `RomanNumeral` definiuje niejawna konwersja z `BinaryNumeral`, rzutowanie nie jest wymagane.</span><span class="sxs-lookup"><span data-stu-id="d9e12-111">Because `RomanNumeral` defines an implicit conversion from `BinaryNumeral`, no cast is required.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d9e12-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d9e12-112">See Also</span></span>  
 [<span data-ttu-id="d9e12-113">Odwołanie w C#</span><span class="sxs-lookup"><span data-stu-id="d9e12-113">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="d9e12-114">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="d9e12-114">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="d9e12-115">Operatory konwersji</span><span class="sxs-lookup"><span data-stu-id="d9e12-115">Conversion Operators</span></span>](../../../csharp/programming-guide/statements-expressions-operators/conversion-operators.md)
