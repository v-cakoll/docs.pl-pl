---
title: Jak jawnie zaimplementować członków interfejsu — C# Przewodnik programowania
ms.date: 07/20/2015
helpviewer_keywords:
- interfaces [C#], explicitly implementing
ms.assetid: 514cde76-f981-474e-8b40-9493619f899c
ms.openlocfilehash: d006db2a7501a3273f5cd11e82bc589b21e1ce9f
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75712094"
---
# <a name="how-to-explicitly-implement-interface-members-c-programming-guide"></a><span data-ttu-id="900c6-102">Jak jawnie zaimplementować członków interfejsu (C# Przewodnik programowania)</span><span class="sxs-lookup"><span data-stu-id="900c6-102">How to explicitly implement interface members (C# Programming Guide)</span></span>
<span data-ttu-id="900c6-103">Ten przykład deklaruje [interfejs](../../language-reference/keywords/interface.md), `IDimensions`i klasę `Box`, która jawnie implementuje elementy członkowskie interfejsu `getLength` i `getWidth`.</span><span class="sxs-lookup"><span data-stu-id="900c6-103">This example declares an [interface](../../language-reference/keywords/interface.md), `IDimensions`, and a class, `Box`, which explicitly implements the interface members `getLength` and `getWidth`.</span></span> <span data-ttu-id="900c6-104">Dostęp do członków uzyskuje się za pomocą wystąpienia interfejsu `dimensions`.</span><span class="sxs-lookup"><span data-stu-id="900c6-104">The members are accessed through the interface instance `dimensions`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="900c6-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="900c6-105">Example</span></span>  
 [!code-csharp[csProgGuideInheritance#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#8)]  
  
## <a name="robust-programming"></a><span data-ttu-id="900c6-106">Skuteczne programowanie</span><span class="sxs-lookup"><span data-stu-id="900c6-106">Robust Programming</span></span>  
  
- <span data-ttu-id="900c6-107">Zwróć uwagę, że następujące wiersze w metodzie `Main` są oznaczane jako komentarze, ponieważ spowodują błędy kompilacji.</span><span class="sxs-lookup"><span data-stu-id="900c6-107">Notice that the following lines, in the `Main` method, are commented out because they would produce compilation errors.</span></span> <span data-ttu-id="900c6-108">Nie można uzyskać dostępu do elementu członkowskiego interfejsu, który jest jawnie zaimplementowany z wystąpienia [klasy](../../language-reference/keywords/class.md) :</span><span class="sxs-lookup"><span data-stu-id="900c6-108">An interface member that is explicitly implemented cannot be accessed from a [class](../../language-reference/keywords/class.md) instance:</span></span>  
  
     [!code-csharp[csProgGuideInheritance#45](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#45)]  
  
- <span data-ttu-id="900c6-109">Zwróć również uwagę, że następujące wiersze w metodzie `Main` pomyślnie wydrukowały Wymiary pola, ponieważ metody są wywoływane z wystąpienia interfejsu:</span><span class="sxs-lookup"><span data-stu-id="900c6-109">Notice also that the following lines, in the `Main` method, successfully print out the dimensions of the box because the methods are being called from an instance of the interface:</span></span>  
  
     [!code-csharp[csProgGuideInheritance#46](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#46)]  
  
## <a name="see-also"></a><span data-ttu-id="900c6-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="900c6-110">See also</span></span>

- [<span data-ttu-id="900c6-111">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="900c6-111">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="900c6-112">Klasy i struktury</span><span class="sxs-lookup"><span data-stu-id="900c6-112">Classes and Structs</span></span>](../classes-and-structs/index.md)
- [<span data-ttu-id="900c6-113">Interfejsy</span><span class="sxs-lookup"><span data-stu-id="900c6-113">Interfaces</span></span>](./index.md)
- [<span data-ttu-id="900c6-114">Jak jawnie zaimplementować członków dwóch interfejsów</span><span class="sxs-lookup"><span data-stu-id="900c6-114">How to explicitly implement members of two interfaces</span></span>](./how-to-explicitly-implement-members-of-two-interfaces.md)
