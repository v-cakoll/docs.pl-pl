---
title: 'Instrukcje: Implementowanie zdefiniowanych przez użytkownika konwersji struktur — C# przewodnik programowania'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- user-defined conversions [C#]
ms.assetid: 97839aef-8fbc-40d5-9769-6b569bc2710b
ms.openlocfilehash: bc792562b4849d402e03328e50dedac030520011
ms.sourcegitcommit: 41c0637e894fbcd0713d46d6ef1866f08dc321a2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/01/2019
ms.locfileid: "57201147"
---
# <a name="how-to-implement-user-defined-conversions-between-structs-c-programming-guide"></a><span data-ttu-id="08dbd-102">Instrukcje: Implementowanie zdefiniowanych przez użytkownika konwersji struktur (C# Programming Guide)</span><span class="sxs-lookup"><span data-stu-id="08dbd-102">How to: Implement User-Defined Conversions Between Structs (C# Programming Guide)</span></span>
<span data-ttu-id="08dbd-103">Ten przykład definiuje dwie struktury `RomanNumeral` i `BinaryNumeral`i przedstawiono konwersje między nimi.</span><span class="sxs-lookup"><span data-stu-id="08dbd-103">This example defines two structs, `RomanNumeral` and `BinaryNumeral`, and demonstrates conversions between them.</span></span>  
  
## <a name="example"></a><span data-ttu-id="08dbd-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="08dbd-104">Example</span></span>  
 [!code-csharp[csProgGuideStatements#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStatements/CS/Statements.cs#13)]  
  
## <a name="robust-programming"></a><span data-ttu-id="08dbd-105">Niezawodne programowanie</span><span class="sxs-lookup"><span data-stu-id="08dbd-105">Robust Programming</span></span>  
  
-   <span data-ttu-id="08dbd-106">W poprzednim przykładzie instrukcji:</span><span class="sxs-lookup"><span data-stu-id="08dbd-106">In the previous example, the statement:</span></span>  
  
     [!code-csharp[csProgGuideStatements#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStatements/CS/Statements.cs#14)]  
  
     <span data-ttu-id="08dbd-107">wykonuje konwersję z `RomanNumeral` do `BinaryNumeral`.</span><span class="sxs-lookup"><span data-stu-id="08dbd-107">performs a conversion from a `RomanNumeral` to a `BinaryNumeral`.</span></span> <span data-ttu-id="08dbd-108">Ponieważ nie istnieje żadne bezpośrednie konwersja `RomanNumeral` do `BinaryNumeral`, używane jest rzutowanie do konwersji z `RomanNumeral` do `int`i innym rzutowanie do konwersji z `int` do `BinaryNumeral`.</span><span class="sxs-lookup"><span data-stu-id="08dbd-108">Because there is no direct conversion from `RomanNumeral` to `BinaryNumeral`, a cast is used to convert from a `RomanNumeral` to an `int`, and another cast to convert from an `int` to a `BinaryNumeral`.</span></span>  
  
-   <span data-ttu-id="08dbd-109">Również — instrukcja</span><span class="sxs-lookup"><span data-stu-id="08dbd-109">Also the statement</span></span>  
  
     [!code-csharp[csProgGuideStatements#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStatements/CS/Statements.cs#15)]  
  
     <span data-ttu-id="08dbd-110">wykonuje konwersję z `BinaryNumeral` do `RomanNumeral`.</span><span class="sxs-lookup"><span data-stu-id="08dbd-110">performs a conversion from a `BinaryNumeral` to a `RomanNumeral`.</span></span> <span data-ttu-id="08dbd-111">Ponieważ `RomanNumeral` definiuje niejawna konwersja z `BinaryNumeral`, rzutowanie nie jest wymagana.</span><span class="sxs-lookup"><span data-stu-id="08dbd-111">Because `RomanNumeral` defines an implicit conversion from `BinaryNumeral`, no cast is required.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="08dbd-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="08dbd-112">See also</span></span>

- [<span data-ttu-id="08dbd-113">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="08dbd-113">C# Reference</span></span>](../../../csharp/language-reference/index.md)
- [<span data-ttu-id="08dbd-114">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="08dbd-114">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="08dbd-115">Operatory konwersji</span><span class="sxs-lookup"><span data-stu-id="08dbd-115">Conversion Operators</span></span>](../../../csharp/programming-guide/statements-expressions-operators/conversion-operators.md)
