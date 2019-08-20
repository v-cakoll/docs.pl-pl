---
title: 'Instrukcje: Jawne implementowanie elementów członkowskich C# interfejsu — Przewodnik programowania'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- interfaces [C#], explicitly implementing
ms.assetid: 514cde76-f981-474e-8b40-9493619f899c
ms.openlocfilehash: 5ef8b42fe5ca07548d52b88720ea4845d2408bb1
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69589208"
---
# <a name="how-to-explicitly-implement-interface-members-c-programming-guide"></a><span data-ttu-id="a1146-102">Instrukcje: Jawnie Implementuj elementy członkowskie interfejsuC# (Przewodnik programowania)</span><span class="sxs-lookup"><span data-stu-id="a1146-102">How to: Explicitly Implement Interface Members (C# Programming Guide)</span></span>
<span data-ttu-id="a1146-103">Ten przykład deklaruje [interfejs](../../language-reference/keywords/interface.md), `IDimensions`i klasę, `Box`, która jawnie implementuje elementy członkowskie `getLength` interfejsu i `getWidth`.</span><span class="sxs-lookup"><span data-stu-id="a1146-103">This example declares an [interface](../../language-reference/keywords/interface.md), `IDimensions`, and a class, `Box`, which explicitly implements the interface members `getLength` and `getWidth`.</span></span> <span data-ttu-id="a1146-104">Dostęp do członków uzyskuje się za pomocą `dimensions`wystąpienia interfejsu.</span><span class="sxs-lookup"><span data-stu-id="a1146-104">The members are accessed through the interface instance `dimensions`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a1146-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="a1146-105">Example</span></span>  
 [!code-csharp[csProgGuideInheritance#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#8)]  
  
## <a name="robust-programming"></a><span data-ttu-id="a1146-106">Niezawodne programowanie</span><span class="sxs-lookup"><span data-stu-id="a1146-106">Robust Programming</span></span>  
  
- <span data-ttu-id="a1146-107">Zwróć uwagę, że następujące wiersze w metodzie są oznaczone jako `Main` komentarze, ponieważ spowodują błędy kompilacji.</span><span class="sxs-lookup"><span data-stu-id="a1146-107">Notice that the following lines, in the `Main` method, are commented out because they would produce compilation errors.</span></span> <span data-ttu-id="a1146-108">Nie można uzyskać dostępu do elementu członkowskiego interfejsu, który jest jawnie zaimplementowany z wystąpienia [klasy](../../language-reference/keywords/class.md) :</span><span class="sxs-lookup"><span data-stu-id="a1146-108">An interface member that is explicitly implemented cannot be accessed from a [class](../../language-reference/keywords/class.md) instance:</span></span>  
  
     [!code-csharp[csProgGuideInheritance#45](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#45)]  
  
- <span data-ttu-id="a1146-109">Zwróć również uwagę, że w `Main` metodzie pomyślnie Wydrukowano Wymiary pola, ponieważ metody są wywoływane z wystąpienia interfejsu:</span><span class="sxs-lookup"><span data-stu-id="a1146-109">Notice also that the following lines, in the `Main` method, successfully print out the dimensions of the box because the methods are being called from an instance of the interface:</span></span>  
  
     [!code-csharp[csProgGuideInheritance#46](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#46)]  
  
## <a name="see-also"></a><span data-ttu-id="a1146-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a1146-110">See also</span></span>

- [<span data-ttu-id="a1146-111">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="a1146-111">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="a1146-112">Klasy i struktury</span><span class="sxs-lookup"><span data-stu-id="a1146-112">Classes and Structs</span></span>](../classes-and-structs/index.md)
- [<span data-ttu-id="a1146-113">Interfejsy</span><span class="sxs-lookup"><span data-stu-id="a1146-113">Interfaces</span></span>](./index.md)
- [<span data-ttu-id="a1146-114">Instrukcje: Jawne implementowanie elementów członkowskich dwóch interfejsów</span><span class="sxs-lookup"><span data-stu-id="a1146-114">How to: Explicitly Implement Members of Two Interfaces</span></span>](./how-to-explicitly-implement-members-of-two-interfaces.md)
