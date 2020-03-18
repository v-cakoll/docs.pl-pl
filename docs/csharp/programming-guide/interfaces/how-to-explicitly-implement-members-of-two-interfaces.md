---
title: Jak jawnie implementować członków dwóch interfejsów - Przewodnik programowania C#
ms.date: 07/20/2015
helpviewer_keywords:
- inheritance [C#], explicitly implementing interface members
- interfaces [C#], explicitly implementing with inheritance
ms.assetid: 8b402ddc-dff9-4869-89cb-d718c764e68e
ms.openlocfilehash: c7adc08f62a7f8a14b8e10f8b5ecdd6e37db811d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75701241"
---
# <a name="how-to-explicitly-implement-members-of-two-interfaces-c-programming-guide"></a><span data-ttu-id="81a30-102">Jak jawnie implementować członków dwóch interfejsów (C# Programming Guide)</span><span class="sxs-lookup"><span data-stu-id="81a30-102">How to explicitly implement members of two interfaces (C# Programming Guide)</span></span>
<span data-ttu-id="81a30-103">Implementacja [interfejsu](../../language-reference/keywords/interface.md) jawnego umożliwia również programisty zaimplementować dwa interfejsy, które mają te same nazwy elementów członkowskich i nadać każdemu członkowi interfejsu oddzielną implementację.</span><span class="sxs-lookup"><span data-stu-id="81a30-103">Explicit [interface](../../language-reference/keywords/interface.md) implementation also allows the programmer to implement two interfaces that have the same member names and give each interface member a separate implementation.</span></span> <span data-ttu-id="81a30-104">W tym przykładzie są wyświetlane wymiary pola zarówno w jednostkach metrycznych, jak i angielskich.</span><span class="sxs-lookup"><span data-stu-id="81a30-104">This example displays the dimensions of a box in both metric and English units.</span></span> <span data-ttu-id="81a30-105">[Klasa](../../language-reference/keywords/class.md) Box implementuje dwa interfejsy IEnglishDimensions i IMetricDimensions, które reprezentują różne systemy pomiarowe.</span><span class="sxs-lookup"><span data-stu-id="81a30-105">The Box [class](../../language-reference/keywords/class.md) implements two interfaces IEnglishDimensions and IMetricDimensions, which represent the different measurement systems.</span></span> <span data-ttu-id="81a30-106">Oba interfejsy mają identyczne nazwy elementów członkowskich, Długość i Szerokość.</span><span class="sxs-lookup"><span data-stu-id="81a30-106">Both interfaces have identical member names, Length and Width.</span></span>  
  
## <a name="example"></a><span data-ttu-id="81a30-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="81a30-107">Example</span></span>  
 [!code-csharp[csProgGuideInheritance#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#9)]  
  
## <a name="robust-programming"></a><span data-ttu-id="81a30-108">Niezawodne programowanie</span><span class="sxs-lookup"><span data-stu-id="81a30-108">Robust Programming</span></span>  
 <span data-ttu-id="81a30-109">Jeśli chcesz wprowadzić domyślne pomiary w jednostkach angielskich, należy zaimplementować metody Długość i szerokość normalnie i jawnie zaimplementować length and width metody z iMetricDimensions interfejsu:</span><span class="sxs-lookup"><span data-stu-id="81a30-109">If you want to make the default measurements in English units, implement the methods Length and Width normally, and explicitly implement the Length and Width methods from the IMetricDimensions interface:</span></span>  
  
 [!code-csharp[csProgGuideInheritance#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#10)]  
  
 <span data-ttu-id="81a30-110">W takim przypadku można uzyskać dostęp do jednostek angielskich z wystąpienia klasy i uzyskać dostęp do jednostek metryk z wystąpienia interfejsu:</span><span class="sxs-lookup"><span data-stu-id="81a30-110">In this case, you can access the English units from the class instance and access the metric units from the interface instance:</span></span>  
  
 [!code-csharp[csProgGuideInheritance#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#11)]  
  
## <a name="see-also"></a><span data-ttu-id="81a30-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="81a30-111">See also</span></span>

- [<span data-ttu-id="81a30-112">Przewodnik programowania języka C#</span><span class="sxs-lookup"><span data-stu-id="81a30-112">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="81a30-113">Klasy i struktury</span><span class="sxs-lookup"><span data-stu-id="81a30-113">Classes and Structs</span></span>](../classes-and-structs/index.md)
- [<span data-ttu-id="81a30-114">Interfejsy</span><span class="sxs-lookup"><span data-stu-id="81a30-114">Interfaces</span></span>](./index.md)
- [<span data-ttu-id="81a30-115">Jawne implementowanie elementów interfejsu</span><span class="sxs-lookup"><span data-stu-id="81a30-115">How to explicitly implement interface members</span></span>](./how-to-explicitly-implement-interface-members.md)
