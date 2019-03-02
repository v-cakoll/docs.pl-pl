---
title: 'Instrukcje: Jawne Implementowanie elementów interfejsu - C# przewodnik programowania'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- interfaces [C#], explicitly implementing
ms.assetid: 514cde76-f981-474e-8b40-9493619f899c
ms.openlocfilehash: d5630065ae1fbfceca9ce3b5180664bba3a104a6
ms.sourcegitcommit: 41c0637e894fbcd0713d46d6ef1866f08dc321a2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/01/2019
ms.locfileid: "57201875"
---
# <a name="how-to-explicitly-implement-interface-members-c-programming-guide"></a><span data-ttu-id="cd8f4-102">Instrukcje: Jawne Implementowanie elementów interfejsu (C# Programming Guide)</span><span class="sxs-lookup"><span data-stu-id="cd8f4-102">How to: Explicitly Implement Interface Members (C# Programming Guide)</span></span>
<span data-ttu-id="cd8f4-103">W tym przykładzie deklaruje [interfejsu](../../../csharp/language-reference/keywords/interface.md), `IDimensions`i klasę, `Box`, który implementuje jawnie składowe interfejsu `getLength` i `getWidth`.</span><span class="sxs-lookup"><span data-stu-id="cd8f4-103">This example declares an [interface](../../../csharp/language-reference/keywords/interface.md), `IDimensions`, and a class, `Box`, which explicitly implements the interface members `getLength` and `getWidth`.</span></span> <span data-ttu-id="cd8f4-104">Elementy członkowskie są dostępne za pośrednictwem wystąpienia interfejsu `dimensions`.</span><span class="sxs-lookup"><span data-stu-id="cd8f4-104">The members are accessed through the interface instance `dimensions`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cd8f4-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="cd8f4-105">Example</span></span>  
 [!code-csharp[csProgGuideInheritance#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#8)]  
  
## <a name="robust-programming"></a><span data-ttu-id="cd8f4-106">Niezawodne programowanie</span><span class="sxs-lookup"><span data-stu-id="cd8f4-106">Robust Programming</span></span>  
  
-   <span data-ttu-id="cd8f4-107">Należy zauważyć, że następujące wiersze w `Main` metody są oznaczone jako komentarz, ponieważ ich dałby w efekcie błędy kompilacji.</span><span class="sxs-lookup"><span data-stu-id="cd8f4-107">Notice that the following lines, in the `Main` method, are commented out because they would produce compilation errors.</span></span> <span data-ttu-id="cd8f4-108">Nie można uzyskać dostępu do składowej interfejsu, który jest jawnie implementowane z [klasy](../../../csharp/language-reference/keywords/class.md) wystąpienie:</span><span class="sxs-lookup"><span data-stu-id="cd8f4-108">An interface member that is explicitly implemented cannot be accessed from a [class](../../../csharp/language-reference/keywords/class.md) instance:</span></span>  
  
     [!code-csharp[csProgGuideInheritance#45](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#45)]  
  
-   <span data-ttu-id="cd8f4-109">Zauważ również, że następujące wiersze w `Main` metoda pomyślnie drukowania wymiary pola, ponieważ z wystąpienia interfejsu wywoływane są metody:</span><span class="sxs-lookup"><span data-stu-id="cd8f4-109">Notice also that the following lines, in the `Main` method, successfully print out the dimensions of the box because the methods are being called from an instance of the interface:</span></span>  
  
     [!code-csharp[csProgGuideInheritance#46](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#46)]  
  
## <a name="see-also"></a><span data-ttu-id="cd8f4-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="cd8f4-110">See also</span></span>

- [<span data-ttu-id="cd8f4-111">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="cd8f4-111">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="cd8f4-112">Klasy i struktury</span><span class="sxs-lookup"><span data-stu-id="cd8f4-112">Classes and Structs</span></span>](../../../csharp/programming-guide/classes-and-structs/index.md)
- [<span data-ttu-id="cd8f4-113">Interfejsy</span><span class="sxs-lookup"><span data-stu-id="cd8f4-113">Interfaces</span></span>](../../../csharp/programming-guide/interfaces/index.md)
- [<span data-ttu-id="cd8f4-114">Instrukcje: Jawne Implementowanie elementów dwóch interfejsów</span><span class="sxs-lookup"><span data-stu-id="cd8f4-114">How to: Explicitly Implement Members of Two Interfaces</span></span>](../../../csharp/programming-guide/interfaces/how-to-explicitly-implement-members-of-two-interfaces.md)
