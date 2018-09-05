---
title: 'Porady: jawne implementowanie elementów interfejsu (Przewodnik programowania w języku C#)'
ms.date: 07/20/2015
helpviewer_keywords:
- interfaces [C#], explicitly implementing
ms.assetid: 514cde76-f981-474e-8b40-9493619f899c
ms.openlocfilehash: 30ea58b7ef3edd757c450b9fca1cc810ff9d17c1
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43558610"
---
# <a name="how-to-explicitly-implement-interface-members-c-programming-guide"></a><span data-ttu-id="3270d-102">Porady: jawne implementowanie elementów interfejsu (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="3270d-102">How to: Explicitly Implement Interface Members (C# Programming Guide)</span></span>
<span data-ttu-id="3270d-103">W tym przykładzie deklaruje [interfejsu](../../../csharp/language-reference/keywords/interface.md), `IDimensions`i klasę, `Box`, który implementuje jawnie składowe interfejsu `getLength` i `getWidth`.</span><span class="sxs-lookup"><span data-stu-id="3270d-103">This example declares an [interface](../../../csharp/language-reference/keywords/interface.md), `IDimensions`, and a class, `Box`, which explicitly implements the interface members `getLength` and `getWidth`.</span></span> <span data-ttu-id="3270d-104">Elementy członkowskie są dostępne za pośrednictwem wystąpienia interfejsu `dimensions`.</span><span class="sxs-lookup"><span data-stu-id="3270d-104">The members are accessed through the interface instance `dimensions`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3270d-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="3270d-105">Example</span></span>  
 [!code-csharp[csProgGuideInheritance#8](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-explicitly-implement-interface-members_1.cs)]  
  
## <a name="robust-programming"></a><span data-ttu-id="3270d-106">Niezawodne programowanie</span><span class="sxs-lookup"><span data-stu-id="3270d-106">Robust Programming</span></span>  
  
-   <span data-ttu-id="3270d-107">Należy zauważyć, że następujące wiersze w `Main` metody są oznaczone jako komentarz, ponieważ ich dałby w efekcie błędy kompilacji.</span><span class="sxs-lookup"><span data-stu-id="3270d-107">Notice that the following lines, in the `Main` method, are commented out because they would produce compilation errors.</span></span> <span data-ttu-id="3270d-108">Nie można uzyskać dostępu do składowej interfejsu, który jest jawnie implementowane z [klasy](../../../csharp/language-reference/keywords/class.md) wystąpienie:</span><span class="sxs-lookup"><span data-stu-id="3270d-108">An interface member that is explicitly implemented cannot be accessed from a [class](../../../csharp/language-reference/keywords/class.md) instance:</span></span>  
  
     [!code-csharp[csProgGuideInheritance#45](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-explicitly-implement-interface-members_2.cs)]  
  
-   <span data-ttu-id="3270d-109">Zauważ również, że następujące wiersze w `Main` metoda pomyślnie drukowania wymiary pola, ponieważ z wystąpienia interfejsu wywoływane są metody:</span><span class="sxs-lookup"><span data-stu-id="3270d-109">Notice also that the following lines, in the `Main` method, successfully print out the dimensions of the box because the methods are being called from an instance of the interface:</span></span>  
  
     [!code-csharp[csProgGuideInheritance#46](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-explicitly-implement-interface-members_3.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="3270d-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3270d-110">See Also</span></span>

- [<span data-ttu-id="3270d-111">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="3270d-111">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="3270d-112">Klasy i struktury</span><span class="sxs-lookup"><span data-stu-id="3270d-112">Classes and Structs</span></span>](../../../csharp/programming-guide/classes-and-structs/index.md)  
- [<span data-ttu-id="3270d-113">Interfejsy</span><span class="sxs-lookup"><span data-stu-id="3270d-113">Interfaces</span></span>](../../../csharp/programming-guide/interfaces/index.md)  
- [<span data-ttu-id="3270d-114">Instrukcje: jawne implementowanie elementów dwóch interfejsów</span><span class="sxs-lookup"><span data-stu-id="3270d-114">How to: Explicitly Implement Members of Two Interfaces</span></span>](../../../csharp/programming-guide/interfaces/how-to-explicitly-implement-members-of-two-interfaces.md)
