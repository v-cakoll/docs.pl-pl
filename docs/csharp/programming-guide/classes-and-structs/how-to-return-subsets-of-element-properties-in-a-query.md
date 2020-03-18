---
title: Jak zwrócić podzestawy właściwości elementu w kwerendzie — Przewodnik programowania C#
ms.date: 07/20/2015
helpviewer_keywords:
- anonymous types [C#], for subsets of element properties
ms.assetid: fabdf349-f443-4e3f-8368-6c471be1dd7b
ms.openlocfilehash: 27a2626fc46307a7195040adf746d8d8757d2f82
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75714857"
---
# <a name="how-to-return-subsets-of-element-properties-in-a-query-c-programming-guide"></a><span data-ttu-id="d2800-102">Jak zwrócić podzestawy właściwości elementu w kwerendzie (Przewodnik programowania C#)</span><span class="sxs-lookup"><span data-stu-id="d2800-102">How to return subsets of element properties in a query (C# Programming Guide)</span></span>
<span data-ttu-id="d2800-103">Użyj typu anonimowego w wyrażeniu kwerendy, gdy obowiązują oba te warunki:</span><span class="sxs-lookup"><span data-stu-id="d2800-103">Use an anonymous type in a query expression when both of these conditions apply:</span></span>  
  
- <span data-ttu-id="d2800-104">Chcesz zwrócić tylko niektóre właściwości każdego elementu źródłowego.</span><span class="sxs-lookup"><span data-stu-id="d2800-104">You want to return only some of the properties of each source element.</span></span>  
  
- <span data-ttu-id="d2800-105">Nie trzeba przechowywać wyniki kwerendy poza zakresem metody, w którym kwerenda jest wykonywana.</span><span class="sxs-lookup"><span data-stu-id="d2800-105">You do not have to store the query results outside the scope of the method in which the query is executed.</span></span>  
  
 <span data-ttu-id="d2800-106">Jeśli chcesz zwrócić tylko jedną właściwość lub pole z każdego elementu źródłowego, `select` można po prostu użyć operatora kropki w klauzuli.</span><span class="sxs-lookup"><span data-stu-id="d2800-106">If you only want to return one property or field from each source element, then you can just use the dot operator in the `select` clause.</span></span> <span data-ttu-id="d2800-107">Na przykład, aby `ID` zwrócić `student`tylko z `select` każdego , należy napisać klauzulę w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="d2800-107">For example, to return only the `ID` of each `student`, write the `select` clause as follows:</span></span>  
  
```csharp  
select student.ID;  
```  
  
## <a name="example"></a><span data-ttu-id="d2800-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="d2800-108">Example</span></span>  
 <span data-ttu-id="d2800-109">W poniższym przykładzie pokazano, jak użyć typu anonimowego, aby zwrócić tylko podzbiór właściwości każdego elementu źródłowego, który pasuje do określonego warunku.</span><span class="sxs-lookup"><span data-stu-id="d2800-109">The following example shows how to use an anonymous type to return only a subset of the properties of each source element that matches the specified condition.</span></span>  
  
 [!code-csharp[csProgGuideLINQ#31](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csRef30LangFeatures_2.cs#31)]  
  
 <span data-ttu-id="d2800-110">Należy zauważyć, że typ anonimowy używa nazwy elementu źródłowego dla jego właściwości, jeśli nie określono nazwy.</span><span class="sxs-lookup"><span data-stu-id="d2800-110">Note that the anonymous type uses the source element's names for its properties if no names are specified.</span></span> <span data-ttu-id="d2800-111">Aby nadać nowe nazwy właściwościom typu anonimowego, należy napisać instrukcję w `select` następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="d2800-111">To give new names to the properties in the anonymous type, write the `select` statement as follows:</span></span>  
  
```csharp  
select new { First = student.FirstName, Last = student.LastName };  
```  
  
 <span data-ttu-id="d2800-112">Jeśli spróbujesz tego w `Console.WriteLine` poprzednim przykładzie, instrukcja musi również ulec zmianie:</span><span class="sxs-lookup"><span data-stu-id="d2800-112">If you try this in the previous example, then the `Console.WriteLine` statement must also change:</span></span>  
  
```csharp  
Console.WriteLine(student.First + " " + student.Last);  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="d2800-113">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="d2800-113">Compiling the Code</span></span>  
  
<span data-ttu-id="d2800-114">Aby uruchomić ten kod, skopiuj i wklej `using` klasę do aplikacji konsoli C# z dyrektywą dla System.Linq.</span><span class="sxs-lookup"><span data-stu-id="d2800-114">To run this code, copy and paste the class into a C# console application  with a `using` directive for System.Linq.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="d2800-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d2800-115">See also</span></span>

- [<span data-ttu-id="d2800-116">Przewodnik programowania języka C#</span><span class="sxs-lookup"><span data-stu-id="d2800-116">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="d2800-117">Typy anonimowe</span><span class="sxs-lookup"><span data-stu-id="d2800-117">Anonymous Types</span></span>](./anonymous-types.md)
- [<span data-ttu-id="d2800-118">LINQ w C#</span><span class="sxs-lookup"><span data-stu-id="d2800-118">LINQ in C#</span></span>](../../linq/index.md)
