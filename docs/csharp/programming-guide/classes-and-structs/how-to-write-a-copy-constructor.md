---
title: 'Instrukcje: Zapisywanie konstruktora kopiującego - C# przewodnik programowania'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- C# Language, copy constructor
- copy constructor [C#]
ms.assetid: fba899b5-fc41-428e-a745-3ebdbf37990a
ms.openlocfilehash: 252e66229b75c545c85aa175267ea267c138a087
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54573127"
---
# <a name="how-to-write-a-copy-constructor-c-programming-guide"></a><span data-ttu-id="83219-102">Instrukcje: Zapisywanie konstruktora kopiującego (C# Programming Guide)</span><span class="sxs-lookup"><span data-stu-id="83219-102">How to: Write a Copy Constructor (C# Programming Guide)</span></span>
<span data-ttu-id="83219-103">C# nie zapewnia konstruktorowi kopii dla obiektów, ale możesz napisać ją sam.</span><span class="sxs-lookup"><span data-stu-id="83219-103">C# doesn't provide a copy constructor for objects, but you can write one yourself.</span></span>  
  
## <a name="example"></a><span data-ttu-id="83219-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="83219-104">Example</span></span>  
 <span data-ttu-id="83219-105">W poniższym przykładzie `Person` [klasy](../../../csharp/language-reference/keywords/class.md) definiuje konstruktora kopiującego, który przyjmuje, jako argument, wystąpienie `Person`.</span><span class="sxs-lookup"><span data-stu-id="83219-105">In the following example, the `Person`[class](../../../csharp/language-reference/keywords/class.md) defines a copy constructor that takes, as its argument, an instance of `Person`.</span></span> <span data-ttu-id="83219-106">Wartości właściwości argumentu są przypisywane właściwościom nowego wystąpienia programu `Person`.</span><span class="sxs-lookup"><span data-stu-id="83219-106">The values of the properties of the argument are assigned to the properties of the new instance of `Person`.</span></span> <span data-ttu-id="83219-107">Kod zawiera alternatywny Konstruktor kopiujący wysyłający `Name` i `Age` właściwości wystąpienia, które chcesz skopiować do konstruktora wystąpienia klasy.</span><span class="sxs-lookup"><span data-stu-id="83219-107">The code contains an alternative copy constructor that sends the `Name` and `Age` properties of the instance that you want to copy to the instance constructor of the class.</span></span>  
  
 [!code-csharp[csProgGuideObjects#16](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-write-a-copy-constructor_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="83219-108">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="83219-108">See also</span></span>

- <xref:System.ICloneable>
- [<span data-ttu-id="83219-109">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="83219-109">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="83219-110">Klasy i struktury</span><span class="sxs-lookup"><span data-stu-id="83219-110">Classes and Structs</span></span>](../../../csharp/programming-guide/classes-and-structs/index.md)
- [<span data-ttu-id="83219-111">Konstruktory</span><span class="sxs-lookup"><span data-stu-id="83219-111">Constructors</span></span>](../../../csharp/programming-guide/classes-and-structs/constructors.md)
- [<span data-ttu-id="83219-112">Finalizatory</span><span class="sxs-lookup"><span data-stu-id="83219-112">Finalizers</span></span>](../../../csharp/programming-guide/classes-and-structs/destructors.md)
