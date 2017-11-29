---
title: "Używanie operatorów konwersji (Przewodnik programowania w języku C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- conversions [C#], operators
- conversion operators [C#]
- operators [C#], conversion
- user-defined conversions [C#]
- implicit conversion operators [C#]
- explicit conversion operators [C#]
ms.assetid: caf36e89-c6c0-4b87-9f9e-85780a45c9a4
caps.latest.revision: "20"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 5a43332df795d853c3060a604360adeaea5e3fd4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="using-conversion-operators-c-programming-guide"></a><span data-ttu-id="6db66-102">Używanie operatorów konwersji (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="6db66-102">Using Conversion Operators (C# Programming Guide)</span></span>
<span data-ttu-id="6db66-103">Można użyć `implicit` operatory konwersji, które są łatwiejsze do użycia, lub `explicit` operatory konwersji, wskazujące wyraźnie innym osobom odczytywanie kod czy podczas konwertowania typu.</span><span class="sxs-lookup"><span data-stu-id="6db66-103">You can use `implicit` conversion operators, which are easier to use, or `explicit` conversion operators, which clearly indicate to anyone reading the code that you're converting a type.</span></span> <span data-ttu-id="6db66-104">W tym temacie przedstawiono oba rodzaje operatora konwersji.</span><span class="sxs-lookup"><span data-stu-id="6db66-104">This topic demonstrates both types of conversion operator.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6db66-105">Aby uzyskać informacje o konwersji typu prostego, zobacz [jak: konwertowanie ciągu na liczbę](../../../csharp/programming-guide/types/how-to-convert-a-string-to-a-number.md), [porady: Konwertowanie tablicy typu byte na liczbę całkowitą](../../../csharp/programming-guide/types/how-to-convert-a-byte-array-to-an-int.md), [jak: konwertowanie między ciągów szesnastkowych i numeryczne Typy](../../../csharp/programming-guide/types/how-to-convert-between-hexadecimal-strings-and-numeric-types.md), lub <xref:System.Convert>.</span><span class="sxs-lookup"><span data-stu-id="6db66-105">For information about simple type conversions, see [How to: Convert a String to a Number](../../../csharp/programming-guide/types/how-to-convert-a-string-to-a-number.md), [How to: Convert a byte Array to an int](../../../csharp/programming-guide/types/how-to-convert-a-byte-array-to-an-int.md), [How to: Convert Between Hexadecimal Strings and Numeric Types](../../../csharp/programming-guide/types/how-to-convert-between-hexadecimal-strings-and-numeric-types.md), or <xref:System.Convert>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6db66-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="6db66-106">Example</span></span>  
 <span data-ttu-id="6db66-107">To jest przykład operator jawnej konwersji.</span><span class="sxs-lookup"><span data-stu-id="6db66-107">This is an example of an explicit conversion operator.</span></span> <span data-ttu-id="6db66-108">Ten operator konwertuje z typu <xref:System.Byte> wartość typu o nazwie `Digit`.</span><span class="sxs-lookup"><span data-stu-id="6db66-108">This operator converts from the type <xref:System.Byte> to a value type called `Digit`.</span></span> <span data-ttu-id="6db66-109">Ponieważ nie wszystkie bajty można przekonwertować na cyfrę, konwersja jest jawne, co oznacza że musi być używane rzutowanie, jak pokazano w `Main` metody.</span><span class="sxs-lookup"><span data-stu-id="6db66-109">Because not all bytes can be converted to a digit, the conversion is explicit, meaning that a cast must be used, as shown in the `Main` method.</span></span>  
  
 [!code-csharp[csProgGuideStatements#11](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-conversion-operators_1.cs)]  
  
## <a name="example"></a><span data-ttu-id="6db66-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="6db66-110">Example</span></span>  
 <span data-ttu-id="6db66-111">W przykładzie pokazano operator niejawnej konwersji przez definiowanie operatora konwersji, która cofa w poprzednim przykładzie został: konwertuje z klasy wartości o nazwie `Digit` na typy całkowite <xref:System.Byte> typu.</span><span class="sxs-lookup"><span data-stu-id="6db66-111">This example demonstrates an implicit conversion operator by defining a conversion operator that undoes what the previous example did: it converts from a value class called `Digit` to the integral <xref:System.Byte> type.</span></span> <span data-ttu-id="6db66-112">Ponieważ dowolną cyfrę może zostać przekonwertowany na <xref:System.Byte>, nie istnieje potrzeba aby wymusić użytkowników jako jawne o konwersji.</span><span class="sxs-lookup"><span data-stu-id="6db66-112">Because any digit can be converted to a <xref:System.Byte>, there's no need to force users to be explicit about the conversion.</span></span>  
  
 [!code-csharp[csProgGuideStatements#12](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-conversion-operators_2.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="6db66-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6db66-113">See Also</span></span>  
 [<span data-ttu-id="6db66-114">Odwołanie w C#</span><span class="sxs-lookup"><span data-stu-id="6db66-114">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="6db66-115">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="6db66-115">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="6db66-116">Operatory konwersji</span><span class="sxs-lookup"><span data-stu-id="6db66-116">Conversion Operators</span></span>](../../../csharp/programming-guide/statements-expressions-operators/conversion-operators.md)  
 [<span data-ttu-id="6db66-117">jest</span><span class="sxs-lookup"><span data-stu-id="6db66-117">is</span></span>](../../../csharp/language-reference/keywords/is.md)
