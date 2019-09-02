---
title: 'Instrukcje: Zwróć podzbiory właściwości elementu w przewodniku C# programowania zapytań'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- anonymous types [C#], for subsets of element properties
ms.assetid: fabdf349-f443-4e3f-8368-6c471be1dd7b
ms.openlocfilehash: 2c9fea2189819058187020c2e67b8826659fbed4
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/31/2019
ms.locfileid: "70205446"
---
# <a name="how-to-return-subsets-of-element-properties-in-a-query-c-programming-guide"></a><span data-ttu-id="5cffe-102">Instrukcje: Zwracanie podzbiorów właściwości elementu w zapytaniu (C# Przewodnik programowania)</span><span class="sxs-lookup"><span data-stu-id="5cffe-102">How to: Return Subsets of Element Properties in a Query (C# Programming Guide)</span></span>
<span data-ttu-id="5cffe-103">Użyj typu anonimowego w wyrażeniu zapytania, jeśli są spełnione oba te warunki:</span><span class="sxs-lookup"><span data-stu-id="5cffe-103">Use an anonymous type in a query expression when both of these conditions apply:</span></span>  
  
- <span data-ttu-id="5cffe-104">Chcesz zwrócić tylko niektóre właściwości każdego elementu źródłowego.</span><span class="sxs-lookup"><span data-stu-id="5cffe-104">You want to return only some of the properties of each source element.</span></span>  
  
- <span data-ttu-id="5cffe-105">Nie jest konieczne przechowywanie wyników zapytania poza zakresem metody, w której jest wykonywane zapytanie.</span><span class="sxs-lookup"><span data-stu-id="5cffe-105">You do not have to store the query results outside the scope of the method in which the query is executed.</span></span>  
  
 <span data-ttu-id="5cffe-106">Jeśli chcesz zwrócić tylko jedną właściwość lub pole z każdego elementu źródłowego, możesz po prostu użyć operatora kropki w `select` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="5cffe-106">If you only want to return one property or field from each source element, then you can just use the dot operator in the `select` clause.</span></span> <span data-ttu-id="5cffe-107">Aby na przykład zwrócić tylko te dane `ID` `student`, należy napisać `select` klauzulę w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="5cffe-107">For example, to return only the `ID` of each `student`, write the `select` clause as follows:</span></span>  
  
```csharp  
select student.ID;  
```  
  
## <a name="example"></a><span data-ttu-id="5cffe-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="5cffe-108">Example</span></span>  
 <span data-ttu-id="5cffe-109">Poniższy przykład pokazuje, jak używać typu anonimowego, aby zwrócić tylko podzestaw właściwości każdego elementu źródłowego, który jest zgodny z określonym warunkiem.</span><span class="sxs-lookup"><span data-stu-id="5cffe-109">The following example shows how to use an anonymous type to return only a subset of the properties of each source element that matches the specified condition.</span></span>  
  
 [!code-csharp[csProgGuideLINQ#31](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csRef30LangFeatures_2.cs#31)]  
  
 <span data-ttu-id="5cffe-110">Należy pamiętać, że typ anonimowy używa nazw elementów źródłowych dla jego właściwości, jeśli nie określono żadnych nazw.</span><span class="sxs-lookup"><span data-stu-id="5cffe-110">Note that the anonymous type uses the source element's names for its properties if no names are specified.</span></span> <span data-ttu-id="5cffe-111">Aby nadać nowym nazw właściwościom typu anonimowego, należy napisać `select` instrukcję w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="5cffe-111">To give new names to the properties in the anonymous type, write the `select` statement as follows:</span></span>  
  
```csharp  
select new { First = student.FirstName, Last = student.LastName };  
```  
  
 <span data-ttu-id="5cffe-112">Jeśli spróbujesz użyć tego w poprzednim przykładzie, `Console.WriteLine` należy również zmienić instrukcję:</span><span class="sxs-lookup"><span data-stu-id="5cffe-112">If you try this in the previous example, then the `Console.WriteLine` statement must also change:</span></span>  
  
```csharp  
Console.WriteLine(student.First + " " + student.Last);  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="5cffe-113">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="5cffe-113">Compiling the Code</span></span>  
  
<span data-ttu-id="5cffe-114">Aby uruchomić ten kod, skopiuj i wklej klasę do aplikacji C# konsolowej z `using` dyrektywą dla System. LINQ.</span><span class="sxs-lookup"><span data-stu-id="5cffe-114">To run this code, copy and paste the class into a C# console application  with a `using` directive for System.Linq.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="5cffe-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5cffe-115">See also</span></span>

- [<span data-ttu-id="5cffe-116">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="5cffe-116">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="5cffe-117">Typy anonimowe</span><span class="sxs-lookup"><span data-stu-id="5cffe-117">Anonymous Types</span></span>](./anonymous-types.md)
- [<span data-ttu-id="5cffe-118">Wyrażenia zapytania LINQ</span><span class="sxs-lookup"><span data-stu-id="5cffe-118">LINQ Query Expressions</span></span>](../linq-query-expressions/index.md)
