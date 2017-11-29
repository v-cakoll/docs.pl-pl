---
title: "Porady: zapisywanie konstruktora kopiującego (Przewodnik programowania w języku C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- C# Language, copy constructor
- copy constructor [C#]
ms.assetid: fba899b5-fc41-428e-a745-3ebdbf37990a
caps.latest.revision: "20"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: f15d8fabc49cbff5515b78a7d2fb6f9e49d0704e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-write-a-copy-constructor-c-programming-guide"></a><span data-ttu-id="44541-102">Porady: zapisywanie konstruktora kopiującego (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="44541-102">How to: Write a Copy Constructor (C# Programming Guide)</span></span>
<span data-ttu-id="44541-103">C# nie zapewnia Konstruktor kopiujący dla obiektów, ale można wpisać własny.</span><span class="sxs-lookup"><span data-stu-id="44541-103">C# doesn't provide a copy constructor for objects, but you can write one yourself.</span></span>  
  
## <a name="example"></a><span data-ttu-id="44541-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="44541-104">Example</span></span>  
 <span data-ttu-id="44541-105">W poniższym przykładzie `Person` [klasy](../../../csharp/language-reference/keywords/class.md) definiuje konstruktora kopiującego, który przyjmuje, jako jej argument wystąpienia `Person`.</span><span class="sxs-lookup"><span data-stu-id="44541-105">In the following example, the `Person`[class](../../../csharp/language-reference/keywords/class.md) defines a copy constructor that takes, as its argument, an instance of `Person`.</span></span> <span data-ttu-id="44541-106">Wartości właściwości argumentu są przypisane do właściwości nowe wystąpienie klasy `Person`.</span><span class="sxs-lookup"><span data-stu-id="44541-106">The values of the properties of the argument are assigned to the properties of the new instance of `Person`.</span></span> <span data-ttu-id="44541-107">Kod zawiera Konstruktor kopiujący alternatywnych, która wysyła `Name` i `Age` właściwości wystąpienia, który ma zostać skopiowany do konstruktora wystąpienia klasy.</span><span class="sxs-lookup"><span data-stu-id="44541-107">The code contains an alternative copy constructor that sends the `Name` and `Age` properties of the instance that you want to copy to the instance constructor of the class.</span></span>  
  
 [!code-csharp[csProgGuideObjects#16](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-write-a-copy-constructor_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="44541-108">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="44541-108">See Also</span></span>  
 <xref:System.ICloneable>  
 [<span data-ttu-id="44541-109">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="44541-109">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="44541-110">Klasy i struktury</span><span class="sxs-lookup"><span data-stu-id="44541-110">Classes and Structs</span></span>](../../../csharp/programming-guide/classes-and-structs/index.md)  
 [<span data-ttu-id="44541-111">Konstruktory</span><span class="sxs-lookup"><span data-stu-id="44541-111">Constructors</span></span>](../../../csharp/programming-guide/classes-and-structs/constructors.md)  
 [<span data-ttu-id="44541-112">Finalizatory</span><span class="sxs-lookup"><span data-stu-id="44541-112">Finalizers</span></span>](../../../csharp/programming-guide/classes-and-structs/destructors.md)
