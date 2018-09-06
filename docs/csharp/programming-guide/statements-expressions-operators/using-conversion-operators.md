---
title: Używanie operatorów konwersji (Przewodnik programowania w języku C#)
ms.date: 07/20/2015
helpviewer_keywords:
- conversions [C#], operators
- conversion operators [C#]
- operators [C#], conversion
- user-defined conversions [C#]
- implicit conversion operators [C#]
- explicit conversion operators [C#]
ms.assetid: caf36e89-c6c0-4b87-9f9e-85780a45c9a4
ms.openlocfilehash: 17a722f7160ae9cd03caa2dff9c4436fcf0f9d9e
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43784461"
---
# <a name="using-conversion-operators-c-programming-guide"></a><span data-ttu-id="af465-102">Używanie operatorów konwersji (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="af465-102">Using Conversion Operators (C# Programming Guide)</span></span>
<span data-ttu-id="af465-103">Możesz użyć `implicit` operatorów konwersji, które są łatwiejsze w obsłudze, lub `explicit` operatorów konwersji, które wyraźnie wskazać dla każdego, kto kodu czy podczas konwertowania typu.</span><span class="sxs-lookup"><span data-stu-id="af465-103">You can use `implicit` conversion operators, which are easier to use, or `explicit` conversion operators, which clearly indicate to anyone reading the code that you're converting a type.</span></span> <span data-ttu-id="af465-104">W tym temacie przedstawiono oba rodzaje operatora konwersji.</span><span class="sxs-lookup"><span data-stu-id="af465-104">This topic demonstrates both types of conversion operator.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="af465-105">Uzyskać informacji dotyczących konwersji typu prostego, zobacz [porady: konwertowanie ciągu na liczbę](../../../csharp/programming-guide/types/how-to-convert-a-string-to-a-number.md), [porady: Konwertowanie tablicy typu byte na liczbę całkowitą](../../../csharp/programming-guide/types/how-to-convert-a-byte-array-to-an-int.md), [jak: konwersji między ciągów szesnastkowych, które i numeryczne Typy](../../../csharp/programming-guide/types/how-to-convert-between-hexadecimal-strings-and-numeric-types.md), lub <xref:System.Convert>.</span><span class="sxs-lookup"><span data-stu-id="af465-105">For information about simple type conversions, see [How to: Convert a String to a Number](../../../csharp/programming-guide/types/how-to-convert-a-string-to-a-number.md), [How to: Convert a byte Array to an int](../../../csharp/programming-guide/types/how-to-convert-a-byte-array-to-an-int.md), [How to: Convert Between Hexadecimal Strings and Numeric Types](../../../csharp/programming-guide/types/how-to-convert-between-hexadecimal-strings-and-numeric-types.md), or <xref:System.Convert>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="af465-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="af465-106">Example</span></span>  
 <span data-ttu-id="af465-107">Jest to przykład operator jawnej konwersji.</span><span class="sxs-lookup"><span data-stu-id="af465-107">This is an example of an explicit conversion operator.</span></span> <span data-ttu-id="af465-108">Ten operator konwertuje typ <xref:System.Byte> do typu wartości o nazwie `Digit`.</span><span class="sxs-lookup"><span data-stu-id="af465-108">This operator converts from the type <xref:System.Byte> to a value type called `Digit`.</span></span> <span data-ttu-id="af465-109">Ponieważ nie wszystkie wartości bajtowe mogą być konwertowane na cyfrę, konwersja jest jawne oznacza, że należy użyć rzutowania, jak pokazano na `Main` metody.</span><span class="sxs-lookup"><span data-stu-id="af465-109">Because not all bytes can be converted to a digit, the conversion is explicit, meaning that a cast must be used, as shown in the `Main` method.</span></span>  
  
 [!code-csharp[csProgGuideStatements#11](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-conversion-operators_1.cs)]  
  
## <a name="example"></a><span data-ttu-id="af465-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="af465-110">Example</span></span>  
 <span data-ttu-id="af465-111">W tym przykładzie przedstawiono operator niejawnej konwersji przez definiowanie operatora konwersji, która cofa w poprzednim przykładzie została: konwertuje wartość klasę o nazwie `Digit` do całkowitych <xref:System.Byte> typu.</span><span class="sxs-lookup"><span data-stu-id="af465-111">This example demonstrates an implicit conversion operator by defining a conversion operator that undoes what the previous example did: it converts from a value class called `Digit` to the integral <xref:System.Byte> type.</span></span> <span data-ttu-id="af465-112">Ponieważ dowolną cyfrę mogą być konwertowane na <xref:System.Byte>, nie ma potrzeby zmusić użytkowników, aby była niejawna konwersja informacje.</span><span class="sxs-lookup"><span data-stu-id="af465-112">Because any digit can be converted to a <xref:System.Byte>, there's no need to force users to be explicit about the conversion.</span></span>  
  
 [!code-csharp[csProgGuideStatements#12](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-conversion-operators_2.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="af465-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="af465-113">See Also</span></span>

- [<span data-ttu-id="af465-114">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="af465-114">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="af465-115">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="af465-115">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="af465-116">Operatory konwersji</span><span class="sxs-lookup"><span data-stu-id="af465-116">Conversion Operators</span></span>](../../../csharp/programming-guide/statements-expressions-operators/conversion-operators.md)  
- [<span data-ttu-id="af465-117">is</span><span class="sxs-lookup"><span data-stu-id="af465-117">is</span></span>](../../../csharp/language-reference/keywords/is.md)
