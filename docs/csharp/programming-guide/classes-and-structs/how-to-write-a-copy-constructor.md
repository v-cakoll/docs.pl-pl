---
title: 'Porady: zapisywanie konstruktora kopiującego (Przewodnik programowania w języku C#)'
ms.date: 07/20/2015
helpviewer_keywords:
- C# Language, copy constructor
- copy constructor [C#]
ms.assetid: fba899b5-fc41-428e-a745-3ebdbf37990a
ms.openlocfilehash: 8a7cc85d40272918f4839d13fcccb79b558eeac7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-write-a-copy-constructor-c-programming-guide"></a><span data-ttu-id="79c59-102">Porady: zapisywanie konstruktora kopiującego (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="79c59-102">How to: Write a Copy Constructor (C# Programming Guide)</span></span>
<span data-ttu-id="79c59-103">C# nie zapewnia Konstruktor kopiujący dla obiektów, ale można wpisać własny.</span><span class="sxs-lookup"><span data-stu-id="79c59-103">C# doesn't provide a copy constructor for objects, but you can write one yourself.</span></span>  
  
## <a name="example"></a><span data-ttu-id="79c59-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="79c59-104">Example</span></span>  
 <span data-ttu-id="79c59-105">W poniższym przykładzie `Person` [klasy](../../../csharp/language-reference/keywords/class.md) definiuje konstruktora kopiującego, który przyjmuje, jako jej argument wystąpienia `Person`.</span><span class="sxs-lookup"><span data-stu-id="79c59-105">In the following example, the `Person`[class](../../../csharp/language-reference/keywords/class.md) defines a copy constructor that takes, as its argument, an instance of `Person`.</span></span> <span data-ttu-id="79c59-106">Wartości właściwości argumentu są przypisane do właściwości nowe wystąpienie klasy `Person`.</span><span class="sxs-lookup"><span data-stu-id="79c59-106">The values of the properties of the argument are assigned to the properties of the new instance of `Person`.</span></span> <span data-ttu-id="79c59-107">Kod zawiera Konstruktor kopiujący alternatywnych, która wysyła `Name` i `Age` właściwości wystąpienia, który ma zostać skopiowany do konstruktora wystąpienia klasy.</span><span class="sxs-lookup"><span data-stu-id="79c59-107">The code contains an alternative copy constructor that sends the `Name` and `Age` properties of the instance that you want to copy to the instance constructor of the class.</span></span>  
  
 [!code-csharp[csProgGuideObjects#16](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-write-a-copy-constructor_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="79c59-108">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="79c59-108">See Also</span></span>  
 <xref:System.ICloneable>  
 [<span data-ttu-id="79c59-109">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="79c59-109">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="79c59-110">Klasy i struktury</span><span class="sxs-lookup"><span data-stu-id="79c59-110">Classes and Structs</span></span>](../../../csharp/programming-guide/classes-and-structs/index.md)  
 [<span data-ttu-id="79c59-111">Konstruktory</span><span class="sxs-lookup"><span data-stu-id="79c59-111">Constructors</span></span>](../../../csharp/programming-guide/classes-and-structs/constructors.md)  
 [<span data-ttu-id="79c59-112">Finalizatory</span><span class="sxs-lookup"><span data-stu-id="79c59-112">Finalizers</span></span>](../../../csharp/programming-guide/classes-and-structs/destructors.md)
