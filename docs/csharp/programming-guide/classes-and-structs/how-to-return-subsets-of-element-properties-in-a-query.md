---
title: 'Instrukcje: Zwracanie podzbiorów właściwości elementu w zapytaniu — C# przewodnik programowania'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- anonymous types [C#], for subsets of element properties
ms.assetid: fabdf349-f443-4e3f-8368-6c471be1dd7b
ms.openlocfilehash: acff804d87d67bf8758b97ad04805359bb3f2e32
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/14/2019
ms.locfileid: "65586068"
---
# <a name="how-to-return-subsets-of-element-properties-in-a-query-c-programming-guide"></a><span data-ttu-id="cb727-102">Instrukcje: Zwracanie podzbiorów właściwości elementu w zapytaniu (C# Programming Guide)</span><span class="sxs-lookup"><span data-stu-id="cb727-102">How to: Return Subsets of Element Properties in a Query (C# Programming Guide)</span></span>
<span data-ttu-id="cb727-103">Użyj typu anonimowego w wyrażeniu zapytania, gdy oba te warunki zostaną spełnione:</span><span class="sxs-lookup"><span data-stu-id="cb727-103">Use an anonymous type in a query expression when both of these conditions apply:</span></span>  
  
- <span data-ttu-id="cb727-104">Należy zwrócić tylko niektóre właściwości każdego elementu źródłowego.</span><span class="sxs-lookup"><span data-stu-id="cb727-104">You want to return only some of the properties of each source element.</span></span>  
  
- <span data-ttu-id="cb727-105">Nie masz do przechowywania wyników zapytania poza zakresem metody wykonywania zapytania.</span><span class="sxs-lookup"><span data-stu-id="cb727-105">You do not have to store the query results outside the scope of the method in which the query is executed.</span></span>  
  
 <span data-ttu-id="cb727-106">Jeśli chcesz tylko do zwrócenia jedną właściwość lub pole z każdego elementu źródłowego, a następnie można użyć operatora z dot `select` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="cb727-106">If you only want to return one property or field from each source element, then you can just use the dot operator in the `select` clause.</span></span> <span data-ttu-id="cb727-107">Na przykład, aby zwrócić tylko `ID` każdego `student`, zapis `select` klauzuli w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="cb727-107">For example, to return only the `ID` of each `student`, write the `select` clause as follows:</span></span>  
  
```  
select student.ID;  
```  
  
## <a name="example"></a><span data-ttu-id="cb727-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="cb727-108">Example</span></span>  
 <span data-ttu-id="cb727-109">Poniższy przykład pokazuje, jak użyć typu anonimowego w celu zwracania tylko podzbiór właściwości każdego elementu źródłowego, który odpowiada określony warunek.</span><span class="sxs-lookup"><span data-stu-id="cb727-109">The following example shows how to use an anonymous type to return only a subset of the properties of each source element that matches the specified condition.</span></span>  
  
 [!code-csharp[csProgGuideLINQ#31](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csRef30LangFeatures_2.cs#31)]  
  
 <span data-ttu-id="cb727-110">Pamiętaj, że typ anonimowy używa nazwy elementu źródłowego dla jego właściwości, jeśli nie określono żadnych nazw.</span><span class="sxs-lookup"><span data-stu-id="cb727-110">Note that the anonymous type uses the source element's names for its properties if no names are specified.</span></span> <span data-ttu-id="cb727-111">Aby udostępnić nowe nazwy właściwości w typ anonimowy, należy napisać `select` instrukcji w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="cb727-111">To give new names to the properties in the anonymous type, write the `select` statement as follows:</span></span>  
  
```  
select new { First = student.FirstName, Last = student.LastName };  
```  
  
 <span data-ttu-id="cb727-112">Jeśli spróbujesz to w poprzednim przykładzie, a następnie `Console.WriteLine` instrukcji należy także zmienić:</span><span class="sxs-lookup"><span data-stu-id="cb727-112">If you try this in the previous example, then the `Console.WriteLine` statement must also change:</span></span>  
  
```csharp  
Console.WriteLine(student.First + " " + student.Last);  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="cb727-113">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="cb727-113">Compiling the Code</span></span>  
  
<span data-ttu-id="cb727-114">Aby uruchomić ten kod, skopiuj i Wklej klasy do C# aplikacji przy użyciu konsoli `using` dyrektywy dla System.Linq.</span><span class="sxs-lookup"><span data-stu-id="cb727-114">To run this code, copy and paste the class into a C# console application  with a `using` directive for System.Linq.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="cb727-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="cb727-115">See also</span></span>

- [<span data-ttu-id="cb727-116">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="cb727-116">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="cb727-117">Typy anonimowe</span><span class="sxs-lookup"><span data-stu-id="cb727-117">Anonymous Types</span></span>](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md)
- [<span data-ttu-id="cb727-118">Wyrażenia zapytań LINQ</span><span class="sxs-lookup"><span data-stu-id="cb727-118">LINQ Query Expressions</span></span>](../../../csharp/programming-guide/linq-query-expressions/index.md)
