---
title: 'Instrukcje: zwracanie podzbiorów właściwości elementu w przewodniku C# programowania zapytań'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- anonymous types [C#], for subsets of element properties
ms.assetid: fabdf349-f443-4e3f-8368-6c471be1dd7b
ms.openlocfilehash: 196383731507137bf4309d38d27b36f29b23a06c
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/01/2019
ms.locfileid: "73419304"
---
# <a name="how-to-return-subsets-of-element-properties-in-a-query-c-programming-guide"></a><span data-ttu-id="ceb81-102">Porady: zwracanie podzbiorów właściwości elementu w kwerendzie (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="ceb81-102">How to: Return Subsets of Element Properties in a Query (C# Programming Guide)</span></span>
<span data-ttu-id="ceb81-103">Użyj typu anonimowego w wyrażeniu zapytania, jeśli są spełnione oba te warunki:</span><span class="sxs-lookup"><span data-stu-id="ceb81-103">Use an anonymous type in a query expression when both of these conditions apply:</span></span>  
  
- <span data-ttu-id="ceb81-104">Chcesz zwrócić tylko niektóre właściwości każdego elementu źródłowego.</span><span class="sxs-lookup"><span data-stu-id="ceb81-104">You want to return only some of the properties of each source element.</span></span>  
  
- <span data-ttu-id="ceb81-105">Nie jest konieczne przechowywanie wyników zapytania poza zakresem metody, w której jest wykonywane zapytanie.</span><span class="sxs-lookup"><span data-stu-id="ceb81-105">You do not have to store the query results outside the scope of the method in which the query is executed.</span></span>  
  
 <span data-ttu-id="ceb81-106">Jeśli chcesz zwrócić tylko jedną właściwość lub pole z każdego elementu źródłowego, możesz po prostu użyć operatora kropki w klauzuli `select`.</span><span class="sxs-lookup"><span data-stu-id="ceb81-106">If you only want to return one property or field from each source element, then you can just use the dot operator in the `select` clause.</span></span> <span data-ttu-id="ceb81-107">Aby na przykład zwrócić tylko `ID` poszczególnych `student`, należy napisać klauzulę `select` w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="ceb81-107">For example, to return only the `ID` of each `student`, write the `select` clause as follows:</span></span>  
  
```csharp  
select student.ID;  
```  
  
## <a name="example"></a><span data-ttu-id="ceb81-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="ceb81-108">Example</span></span>  
 <span data-ttu-id="ceb81-109">Poniższy przykład pokazuje, jak używać typu anonimowego, aby zwrócić tylko podzestaw właściwości każdego elementu źródłowego, który jest zgodny z określonym warunkiem.</span><span class="sxs-lookup"><span data-stu-id="ceb81-109">The following example shows how to use an anonymous type to return only a subset of the properties of each source element that matches the specified condition.</span></span>  
  
 [!code-csharp[csProgGuideLINQ#31](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csRef30LangFeatures_2.cs#31)]  
  
 <span data-ttu-id="ceb81-110">Należy pamiętać, że typ anonimowy używa nazw elementów źródłowych dla jego właściwości, jeśli nie określono żadnych nazw.</span><span class="sxs-lookup"><span data-stu-id="ceb81-110">Note that the anonymous type uses the source element's names for its properties if no names are specified.</span></span> <span data-ttu-id="ceb81-111">Aby nadać nowym nazw właściwościom typu anonimowego, należy napisać instrukcję `select` w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="ceb81-111">To give new names to the properties in the anonymous type, write the `select` statement as follows:</span></span>  
  
```csharp  
select new { First = student.FirstName, Last = student.LastName };  
```  
  
 <span data-ttu-id="ceb81-112">Jeśli spróbujesz użyć tego w poprzednim przykładzie, należy również zmienić instrukcję `Console.WriteLine`:</span><span class="sxs-lookup"><span data-stu-id="ceb81-112">If you try this in the previous example, then the `Console.WriteLine` statement must also change:</span></span>  
  
```csharp  
Console.WriteLine(student.First + " " + student.Last);  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="ceb81-113">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="ceb81-113">Compiling the Code</span></span>  
  
<span data-ttu-id="ceb81-114">Aby uruchomić ten kod, skopiuj i wklej klasę do aplikacji C# konsolowej z `using` dyrektywie for System. LINQ.</span><span class="sxs-lookup"><span data-stu-id="ceb81-114">To run this code, copy and paste the class into a C# console application  with a `using` directive for System.Linq.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="ceb81-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ceb81-115">See also</span></span>

- [<span data-ttu-id="ceb81-116">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="ceb81-116">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="ceb81-117">Typy anonimowe</span><span class="sxs-lookup"><span data-stu-id="ceb81-117">Anonymous Types</span></span>](./anonymous-types.md)
- [<span data-ttu-id="ceb81-118">LINQ w C#</span><span class="sxs-lookup"><span data-stu-id="ceb81-118">LINQ in C#</span></span>](../../linq/index.md)
