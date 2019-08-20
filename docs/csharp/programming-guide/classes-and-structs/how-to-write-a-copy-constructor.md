---
title: 'Instrukcje: Napisz Konstruktor kopiujący — C# Przewodnik programistyczny'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- C# Language, copy constructor
- copy constructor [C#]
ms.assetid: fba899b5-fc41-428e-a745-3ebdbf37990a
ms.openlocfilehash: bdc352566052f4cec1686176131e9b1e1b768794
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69596608"
---
# <a name="how-to-write-a-copy-constructor-c-programming-guide"></a><span data-ttu-id="13b86-102">Instrukcje: Napisz Konstruktor kopiujący (C# Przewodnik programowania)</span><span class="sxs-lookup"><span data-stu-id="13b86-102">How to: Write a Copy Constructor (C# Programming Guide)</span></span>
<span data-ttu-id="13b86-103">C#nie udostępnia konstruktora kopiującego dla obiektów, ale możesz napisać siebie.</span><span class="sxs-lookup"><span data-stu-id="13b86-103">C# doesn't provide a copy constructor for objects, but you can write one yourself.</span></span>  
  
## <a name="example"></a><span data-ttu-id="13b86-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="13b86-104">Example</span></span>  
 <span data-ttu-id="13b86-105">W poniższym przykładzie `Person` [Klasa](../../language-reference/keywords/class.md) definiuje Konstruktor kopiujący, który przyjmuje, jako argument `Person`, wystąpienie.</span><span class="sxs-lookup"><span data-stu-id="13b86-105">In the following example, the `Person`[class](../../language-reference/keywords/class.md) defines a copy constructor that takes, as its argument, an instance of `Person`.</span></span> <span data-ttu-id="13b86-106">Wartości właściwości argumentu są przypisywane do właściwości nowego wystąpienia `Person`.</span><span class="sxs-lookup"><span data-stu-id="13b86-106">The values of the properties of the argument are assigned to the properties of the new instance of `Person`.</span></span> <span data-ttu-id="13b86-107">Kod zawiera alternatywny Konstruktor kopiujący, który wysyła `Name` właściwości `Age` i wystąpienia, które chcesz skopiować do konstruktora wystąpienia klasy.</span><span class="sxs-lookup"><span data-stu-id="13b86-107">The code contains an alternative copy constructor that sends the `Name` and `Age` properties of the instance that you want to copy to the instance constructor of the class.</span></span>  
  
 [!code-csharp[csProgGuideObjects#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#16)]  
  
## <a name="see-also"></a><span data-ttu-id="13b86-108">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="13b86-108">See also</span></span>

- <xref:System.ICloneable>
- [<span data-ttu-id="13b86-109">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="13b86-109">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="13b86-110">Klasy i struktury</span><span class="sxs-lookup"><span data-stu-id="13b86-110">Classes and Structs</span></span>](./index.md)
- [<span data-ttu-id="13b86-111">Konstruktory</span><span class="sxs-lookup"><span data-stu-id="13b86-111">Constructors</span></span>](./constructors.md)
- [<span data-ttu-id="13b86-112">Finalizatory</span><span class="sxs-lookup"><span data-stu-id="13b86-112">Finalizers</span></span>](./destructors.md)
