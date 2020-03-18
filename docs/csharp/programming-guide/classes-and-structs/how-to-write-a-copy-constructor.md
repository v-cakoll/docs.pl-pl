---
title: Jak napisać konstruktora kopii - C# Programming Guide
ms.date: 07/20/2015
helpviewer_keywords:
- C# Language, copy constructor
- copy constructor [C#]
ms.assetid: fba899b5-fc41-428e-a745-3ebdbf37990a
ms.openlocfilehash: aa6feb1b07f491a90a78684e254910d387b9bccd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75714853"
---
# <a name="how-to-write-a-copy-constructor-c-programming-guide"></a><span data-ttu-id="84e42-102">Jak napisać konstruktora kopii (C# Programming Guide)</span><span class="sxs-lookup"><span data-stu-id="84e42-102">How to write a copy constructor (C# Programming Guide)</span></span>
<span data-ttu-id="84e42-103">C# nie udostępnia konstruktora kopiowania dla obiektów, ale można napisać samodzielnie.</span><span class="sxs-lookup"><span data-stu-id="84e42-103">C# doesn't provide a copy constructor for objects, but you can write one yourself.</span></span>  
  
## <a name="example"></a><span data-ttu-id="84e42-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="84e42-104">Example</span></span>  
 <span data-ttu-id="84e42-105">W poniższym `Person`przykładzie [klasa](../../language-reference/keywords/class.md) definiuje konstruktora kopiowania, który `Person`przyjmuje, jako jego argument, wystąpienie .</span><span class="sxs-lookup"><span data-stu-id="84e42-105">In the following example, the `Person`[class](../../language-reference/keywords/class.md) defines a copy constructor that takes, as its argument, an instance of `Person`.</span></span> <span data-ttu-id="84e42-106">Wartości właściwości argumentu są przypisane do właściwości nowego wystąpienia . `Person`</span><span class="sxs-lookup"><span data-stu-id="84e42-106">The values of the properties of the argument are assigned to the properties of the new instance of `Person`.</span></span> <span data-ttu-id="84e42-107">Kod zawiera konstruktora kopiowania alternatywnego, który wysyła `Name` i `Age` właściwości wystąpienia, które chcesz skopiować do konstruktora wystąpienia klasy.</span><span class="sxs-lookup"><span data-stu-id="84e42-107">The code contains an alternative copy constructor that sends the `Name` and `Age` properties of the instance that you want to copy to the instance constructor of the class.</span></span>  
  
 [!code-csharp[csProgGuideObjects#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#16)]  
  
## <a name="see-also"></a><span data-ttu-id="84e42-108">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="84e42-108">See also</span></span>

- <xref:System.ICloneable>
- [<span data-ttu-id="84e42-109">Przewodnik programowania języka C#</span><span class="sxs-lookup"><span data-stu-id="84e42-109">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="84e42-110">Klasy i struktury</span><span class="sxs-lookup"><span data-stu-id="84e42-110">Classes and Structs</span></span>](./index.md)
- [<span data-ttu-id="84e42-111">Konstruktory</span><span class="sxs-lookup"><span data-stu-id="84e42-111">Constructors</span></span>](./constructors.md)
- [<span data-ttu-id="84e42-112">Finalizatory</span><span class="sxs-lookup"><span data-stu-id="84e42-112">Finalizers</span></span>](./destructors.md)
