---
title: Jak napisać Konstruktor kopiujący — C# Przewodnik programistyczny
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- C# Language, copy constructor
- copy constructor [C#]
ms.assetid: fba899b5-fc41-428e-a745-3ebdbf37990a
ms.openlocfilehash: 4ac7ccb55775019eb86d5345797d2fd74d3b9527
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/12/2019
ms.locfileid: "73970390"
---
# <a name="how-to-write-a-copy-constructor-c-programming-guide"></a><span data-ttu-id="a84ba-102">Jak napisać Konstruktor kopiujący (C# Przewodnik programowania)</span><span class="sxs-lookup"><span data-stu-id="a84ba-102">How to write a copy constructor (C# Programming Guide)</span></span>
<span data-ttu-id="a84ba-103">C#nie udostępnia konstruktora kopiującego dla obiektów, ale możesz napisać siebie.</span><span class="sxs-lookup"><span data-stu-id="a84ba-103">C# doesn't provide a copy constructor for objects, but you can write one yourself.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a84ba-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="a84ba-104">Example</span></span>  
 <span data-ttu-id="a84ba-105">W poniższym przykładzie [klasa](../../language-reference/keywords/class.md) `Person`definiuje Konstruktor kopiujący, który przyjmuje, jako argument, wystąpienie `Person`.</span><span class="sxs-lookup"><span data-stu-id="a84ba-105">In the following example, the `Person`[class](../../language-reference/keywords/class.md) defines a copy constructor that takes, as its argument, an instance of `Person`.</span></span> <span data-ttu-id="a84ba-106">Wartości właściwości argumentu są przypisywane do właściwości nowego wystąpienia `Person`.</span><span class="sxs-lookup"><span data-stu-id="a84ba-106">The values of the properties of the argument are assigned to the properties of the new instance of `Person`.</span></span> <span data-ttu-id="a84ba-107">Kod zawiera alternatywny Konstruktor kopiujący, który wysyła `Name` i `Age` właściwości wystąpienia, które chcesz skopiować do konstruktora wystąpienia klasy.</span><span class="sxs-lookup"><span data-stu-id="a84ba-107">The code contains an alternative copy constructor that sends the `Name` and `Age` properties of the instance that you want to copy to the instance constructor of the class.</span></span>  
  
 [!code-csharp[csProgGuideObjects#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#16)]  
  
## <a name="see-also"></a><span data-ttu-id="a84ba-108">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a84ba-108">See also</span></span>

- <xref:System.ICloneable>
- [<span data-ttu-id="a84ba-109">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="a84ba-109">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="a84ba-110">Klasy i struktury</span><span class="sxs-lookup"><span data-stu-id="a84ba-110">Classes and Structs</span></span>](./index.md)
- [<span data-ttu-id="a84ba-111">Konstruktory</span><span class="sxs-lookup"><span data-stu-id="a84ba-111">Constructors</span></span>](./constructors.md)
- [<span data-ttu-id="a84ba-112">Finalizatory</span><span class="sxs-lookup"><span data-stu-id="a84ba-112">Finalizers</span></span>](./destructors.md)
