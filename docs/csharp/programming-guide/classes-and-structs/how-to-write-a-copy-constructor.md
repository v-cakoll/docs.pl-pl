---
title: 'Instrukcje: Zapisywanie konstruktora kopiującego - C# przewodnik programowania'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- C# Language, copy constructor
- copy constructor [C#]
ms.assetid: fba899b5-fc41-428e-a745-3ebdbf37990a
ms.openlocfilehash: daf0683060d7df5dc5e644b4b84aac3dcdea939f
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/11/2018
ms.locfileid: "53240687"
---
# <a name="how-to-write-a-copy-constructor-c-programming-guide"></a><span data-ttu-id="f5ed9-102">Instrukcje: Zapisywanie konstruktora kopiującego (C# Programming Guide)</span><span class="sxs-lookup"><span data-stu-id="f5ed9-102">How to: Write a Copy Constructor (C# Programming Guide)</span></span>
<span data-ttu-id="f5ed9-103">C# nie zapewnia konstruktorowi kopii dla obiektów, ale możesz napisać ją sam.</span><span class="sxs-lookup"><span data-stu-id="f5ed9-103">C# doesn't provide a copy constructor for objects, but you can write one yourself.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f5ed9-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="f5ed9-104">Example</span></span>  
 <span data-ttu-id="f5ed9-105">W poniższym przykładzie `Person` [klasy](../../../csharp/language-reference/keywords/class.md) definiuje konstruktora kopiującego, który przyjmuje, jako argument, wystąpienie `Person`.</span><span class="sxs-lookup"><span data-stu-id="f5ed9-105">In the following example, the `Person`[class](../../../csharp/language-reference/keywords/class.md) defines a copy constructor that takes, as its argument, an instance of `Person`.</span></span> <span data-ttu-id="f5ed9-106">Wartości właściwości argumentu są przypisywane właściwościom nowego wystąpienia programu `Person`.</span><span class="sxs-lookup"><span data-stu-id="f5ed9-106">The values of the properties of the argument are assigned to the properties of the new instance of `Person`.</span></span> <span data-ttu-id="f5ed9-107">Kod zawiera alternatywny Konstruktor kopiujący wysyłający `Name` i `Age` właściwości wystąpienia, które chcesz skopiować do konstruktora wystąpienia klasy.</span><span class="sxs-lookup"><span data-stu-id="f5ed9-107">The code contains an alternative copy constructor that sends the `Name` and `Age` properties of the instance that you want to copy to the instance constructor of the class.</span></span>  
  
 [!code-csharp[csProgGuideObjects#16](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-write-a-copy-constructor_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="f5ed9-108">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f5ed9-108">See Also</span></span>

- <xref:System.ICloneable>  
- [<span data-ttu-id="f5ed9-109">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="f5ed9-109">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="f5ed9-110">Klasy i struktury</span><span class="sxs-lookup"><span data-stu-id="f5ed9-110">Classes and Structs</span></span>](../../../csharp/programming-guide/classes-and-structs/index.md)  
- [<span data-ttu-id="f5ed9-111">Konstruktory</span><span class="sxs-lookup"><span data-stu-id="f5ed9-111">Constructors</span></span>](../../../csharp/programming-guide/classes-and-structs/constructors.md)  
- [<span data-ttu-id="f5ed9-112">Finalizatory</span><span class="sxs-lookup"><span data-stu-id="f5ed9-112">Finalizers</span></span>](../../../csharp/programming-guide/classes-and-structs/destructors.md)
