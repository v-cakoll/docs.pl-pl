---
title: "Porady: uzyskiwanie dostępu do klasy kolekcji za pomocą instrukcji foreach (Przewodnik programowania w języku C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- collection classes [C#], foreach statement
ms.assetid: a6b9cf5c-6c8d-4223-b12c-288949434493
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 0cf827e958d4dc3b951d17b53effd155356c0ca5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-access-a-collection-class-with-foreach-c-programming-guide"></a><span data-ttu-id="9f3fc-102">Porady: uzyskiwanie dostępu do klasy kolekcji za pomocą instrukcji foreach (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="9f3fc-102">How to: Access a Collection Class with foreach (C# Programming Guide)</span></span>
<span data-ttu-id="9f3fc-103">Poniższy przykładowy kod przedstawia sposób zapisania kolekcja nierodzajową klasę, która może być używany z [foreach](../../../csharp/language-reference/keywords/foreach-in.md).</span><span class="sxs-lookup"><span data-stu-id="9f3fc-103">The following code example illustrates how to write a non-generic collection class that can be used with [foreach](../../../csharp/language-reference/keywords/foreach-in.md).</span></span> <span data-ttu-id="9f3fc-104">W przykładzie zdefiniowano klasę tokenizatora ciągu.</span><span class="sxs-lookup"><span data-stu-id="9f3fc-104">The example defines a string tokenizer class.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9f3fc-105">W tym przykładzie reprezentuje zalecaną praktyką tylko wtedy, gdy nie można użyć klasy rodzajowej kolekcji.</span><span class="sxs-lookup"><span data-stu-id="9f3fc-105">This example represents recommended practice only when you cannot use a generic collection class.</span></span> <span data-ttu-id="9f3fc-106">Na przykład implementowania bezpiecznej kolekcji ogólnej klasy, która obsługuje <xref:System.Collections.Generic.IEnumerable%601>, zobacz [Iteratory](http://msdn.microsoft.com/library/f45331db-d595-46ec-9142-551d3d1eb1a7).</span><span class="sxs-lookup"><span data-stu-id="9f3fc-106">For an example of how to implement a type-safe generic collection class that supports <xref:System.Collections.Generic.IEnumerable%601>, see [Iterators](http://msdn.microsoft.com/library/f45331db-d595-46ec-9142-551d3d1eb1a7).</span></span>  
  
 <span data-ttu-id="9f3fc-107">W tym przykładzie poniższy kod używa segmentu `Tokens` klasę, aby przerwać zdania "Jest przykładowe zdania".</span><span class="sxs-lookup"><span data-stu-id="9f3fc-107">In the example, the following code segment uses the `Tokens` class to break the sentence "This is a sample sentence."</span></span> <span data-ttu-id="9f3fc-108">w tokenach przy użyciu "" i "-" jako separatora.</span><span class="sxs-lookup"><span data-stu-id="9f3fc-108">into tokens by using ' ' and '-' as separators.</span></span> <span data-ttu-id="9f3fc-109">Następnie kod wyświetla te tokeny przy użyciu `foreach` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="9f3fc-109">The code then displays those tokens by using a `foreach` statement.</span></span>  
  
 [!code-csharp[csProgGuideCollections#3](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-access-a-collection-class-with-foreach_1.cs)]  
  
## <a name="example"></a><span data-ttu-id="9f3fc-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="9f3fc-110">Example</span></span>  
 <span data-ttu-id="9f3fc-111">Wewnętrznie `Tokens` klasy używa tablicy do przechowywania tokenów.</span><span class="sxs-lookup"><span data-stu-id="9f3fc-111">Internally, the `Tokens` class uses an array to store the tokens.</span></span> <span data-ttu-id="9f3fc-112">Ponieważ implementuje tablice <xref:System.Collections.IEnumerator> i <xref:System.Collections.IEnumerable>, przykładów kodu można użyć metody wyliczania tablicy (<xref:System.Collections.IEnumerable.GetEnumerator%2A>, <xref:System.Collections.IEnumerator.MoveNext%2A>, <xref:System.Collections.IEnumerator.Reset%2A>, i <xref:System.Collections.IEnumerator.Current%2A>) zamiast definiując je w `Tokens` klasy.</span><span class="sxs-lookup"><span data-stu-id="9f3fc-112">Because arrays implement <xref:System.Collections.IEnumerator> and <xref:System.Collections.IEnumerable>, the code example could have used the array's enumeration methods (<xref:System.Collections.IEnumerable.GetEnumerator%2A>, <xref:System.Collections.IEnumerator.MoveNext%2A>, <xref:System.Collections.IEnumerator.Reset%2A>, and <xref:System.Collections.IEnumerator.Current%2A>) instead of defining them in the `Tokens` class.</span></span> <span data-ttu-id="9f3fc-113">Definicjami metod znajdują się w tym przykładzie wyjaśnienie, jak są definiowane i co działają.</span><span class="sxs-lookup"><span data-stu-id="9f3fc-113">The method definitions are included in the example to clarify how they are defined and what each does.</span></span>  
  
 [!code-csharp[csProgGuideCollections#2](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-access-a-collection-class-with-foreach_2.cs)]  
  
 <span data-ttu-id="9f3fc-114">W języku C# nie jest niezbędna dla klasy kolekcji <xref:System.Collections.IEnumerable> i <xref:System.Collections.IEnumerator> aby był zgodny z `foreach`.</span><span class="sxs-lookup"><span data-stu-id="9f3fc-114">In C#, it is not necessary for a collection class to implement <xref:System.Collections.IEnumerable> and <xref:System.Collections.IEnumerator> to be compatible with `foreach`.</span></span> <span data-ttu-id="9f3fc-115">Jeśli klasa ma wymagany <xref:System.Collections.IEnumerable.GetEnumerator%2A>, <xref:System.Collections.IEnumerator.MoveNext%2A>, <xref:System.Collections.IEnumerator.Reset%2A>, i <xref:System.Collections.IEnumerator.Current%2A> elementów członkowskich, będzie działać z `foreach`.</span><span class="sxs-lookup"><span data-stu-id="9f3fc-115">If the class has the required <xref:System.Collections.IEnumerable.GetEnumerator%2A>, <xref:System.Collections.IEnumerator.MoveNext%2A>, <xref:System.Collections.IEnumerator.Reset%2A>, and <xref:System.Collections.IEnumerator.Current%2A> members, it will work with `foreach`.</span></span> <span data-ttu-id="9f3fc-116">Pominięcie interfejsy zaletą dzięki któremu można określić typ zwracany dla `Current` jest określony więcej niż <xref:System.Object>.</span><span class="sxs-lookup"><span data-stu-id="9f3fc-116">Omitting the interfaces has the advantage of enabling you to define a return type for `Current` that is more specific than <xref:System.Object>.</span></span> <span data-ttu-id="9f3fc-117">Zapewnia to bezpieczeństwo typów.</span><span class="sxs-lookup"><span data-stu-id="9f3fc-117">This provides type safety.</span></span>  
  
 <span data-ttu-id="9f3fc-118">Na przykład Zmień następujące wiersze w poprzednim przykładzie.</span><span class="sxs-lookup"><span data-stu-id="9f3fc-118">For example, change the following lines in the previous example.</span></span>  
  
```csharp  
// Change the Tokens class so that it no longer implements IEnumerable.  
public class Tokens  
{  
    // . . .  
  
    // Change the return type for the GetEnumerator method.  
    public TokenEnumerator GetEnumerator()  
    {   }  
  
    // Change TokenEnumerator so that it no longer implements IEnumerator.  
    public class TokenEnumerator  
    {  
        // . . .  
  
        // Change the return type of method Current to string.  
        public string Current  
        {   }  
    }  
 }  
```  
  
 <span data-ttu-id="9f3fc-119">Ponieważ `Current` zwraca wartość typu ciąg, kompilator może wykryć stosowania niezgodny typ `foreach` instrukcji, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="9f3fc-119">Because `Current` returns a string, the compiler can detect when an incompatible type is used in a `foreach` statement, as shown in the following code.</span></span>  
  
```csharp  
// Error: Cannot convert type string to int.  
foreach (int item in f)    
```  
  
 <span data-ttu-id="9f3fc-120">Wadą pominięcie <xref:System.Collections.IEnumerable> i <xref:System.Collections.IEnumerator> jest, że klasa kolekcji nie jest już współdziałać z `foreach` instrukcji lub równoważne instrukcje języków środowiska uruchomieniowego języka wspólnego.</span><span class="sxs-lookup"><span data-stu-id="9f3fc-120">The disadvantage of omitting <xref:System.Collections.IEnumerable> and <xref:System.Collections.IEnumerator> is that the collection class is no longer interoperable with the `foreach` statements, or equivalent statements, of other common language runtime languages.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9f3fc-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9f3fc-121">See Also</span></span>  
 <xref:System.Collections.Generic>  
 [<span data-ttu-id="9f3fc-122">Odwołanie w C#</span><span class="sxs-lookup"><span data-stu-id="9f3fc-122">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="9f3fc-123">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="9f3fc-123">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="9f3fc-124">Tablice</span><span class="sxs-lookup"><span data-stu-id="9f3fc-124">Arrays</span></span>](../../../csharp/programming-guide/arrays/index.md)  
 [<span data-ttu-id="9f3fc-125">Kolekcje</span><span class="sxs-lookup"><span data-stu-id="9f3fc-125">Collections</span></span>](http://msdn.microsoft.com/library/e76533a9-5033-4a0b-b003-9c2be60d185b)
